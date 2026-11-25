This method attempts to cancel a command that is currently executing on a particular connection.

### Declaration

    // C#
    public override void Cancel();

### Implements

`IDbCommand.Cancel`

### Remarks

If cancellation of the command succeeds, an exception is thrown. If cancellation is not successful, no exception is thrown. If there is no command being executed at the time of the `Cancel` invocation, `Cancel` does nothing. Invoking the `Cancel` method does not guarantee that the command executing at the time will always be cancelled. The execution may complete before it can be terminated. In such cases, no exception is thrown.

When multiple `OracleCommand` objects share the same connection, only one command can be executed on that connection at any one time. When it is invoked, the `Cancel` method attempts to cancel the statement currently running on the connection that the `OracleCommand` object is using to execute the command. However, when multiple `OracleCommand` objects execute statements on the same connection simultaneously, issuing a `Cancel` method invocation may cancel any of the issued commands. This is because the command designated for cancellation may complete before the `Cancel` invocation is effective. If this happens, a command executed by a different `OracleCommand` could be cancelled instead.

There are several ways to avoid this non-deterministic situation that the `Cancel` method can cause:

- The application can create just one `OracleCommand` object for each connection. Doing so assures that the `Cancel` invocation only cancels commands executed by the `OracleCommand` object using a particular connection.

- Command executions in the application are synchronized between `OracleCommand` objects that use the same connection.

These suggestions do not apply if `Cancel` is not used in the application.

Because the termination on the currently running execution is non-deterministic, it is recommended that any non-atomic SQL or PL/SQL execution be started within a transaction. When the command execution successfully terminates with an exception of `ORA-01013:` `user` `requested` `cancel` `of` `current` `operation`, the transaction can be rolled back for data integrity. Other possible exceptions thrown after a command cancellation occurs include `ORA-00936` and `ORA-00604.` Examples of non-atomic execution are collections of DML command executions that are executed one-by-one and multiple DML commands that are part of a PL/SQL stored procedure or function.

### Example

    // C#

    // This example shows how command executions can be cancelled in a
    // deterministic way even if multiple commands are executed on a single
    // connection.  This is accomplished by synchronizing threads through events.
    // Since the Cancel method terminates the currently running operation on the
    // connection, threads must be serialized if multiple threads are using the
    // same connection to execute server round-trip incurring operations.
    // Furthermore, the example shows how the execution and cancel threads should
    // be synchronized so that nth iteration of the command execution does not
    // inappropriately cancel the (n+1)th command executed by the same thread.

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using System.Threading;

    class CancelSample
    {
      private OracleCommand cmd;
      Thread t1, t2;
      // threads signal following events when assigned operations are completed

      private AutoResetEvent ExecuteEvent = new AutoResetEvent(false);
      private AutoResetEvent CancelEvent = new AutoResetEvent(false);
      private AutoResetEvent FinishedEvent = new AutoResetEvent(false);
      AutoResetEvent[] ExecuteAndCancel = new AutoResetEvent[2];

      // Default constructor
      CancelSample()
      {
        cmd = new OracleCommand("select * from all_objects",
          new OracleConnection("user id=scott;password=tiger;data source=oracle"));
        ExecuteAndCancel[0] = ExecuteEvent;
        ExecuteAndCancel[1] = CancelEvent;
      }

      // Constructor that takes a particular command and connection
      CancelSample(string command, OracleConnection con)
      {
        cmd = new OracleCommand(command, con);
        ExecuteAndCancel[0] = ExecuteEvent;
        ExecuteAndCancel[1] = CancelEvent;
      }

      // Execution of the command
      public void Execute()
      {
        OracleDataReader reader = null;
        try
        {
          Console.WriteLine("Execute.");
          reader = cmd.ExecuteReader();
          Console.WriteLine("Execute Done.");
          reader.Close();
        }
        catch(Exception e)
        {
          Console.WriteLine("The command has been cancelled.", e.Message);
        }
        Console.WriteLine("ExecuteEvent.Set()");
        ExecuteEvent.Set();
      }

      // Canceling of the command
      public void Cancel()
      {
        try
        {
          // cancel query if it takes longer than 100 ms to finish execution
          System.Threading.Thread.Sleep(100);
          Console.WriteLine("Cancel.");
          cmd.Cancel();
        }
        catch (Exception e)
        {
          Console.WriteLine(e.ToString());
        }
        Console.WriteLine("Cancel done.");
        Console.WriteLine("CancelEvent.Set()");
        CancelEvent.Set();
      }

      // Execution of the command with a potential of cancelling
      public void ExecuteWithinLimitedTime()
      {
        for (int i = 0; i < 5; i++)
        {
          Monitor.Enter(typeof(CancelSample));
          try
          {
            Console.WriteLine("Executing " + this.cmd.CommandText);
            ExecuteEvent.Reset();
            CancelEvent.Reset();
            t1 = new Thread(new ThreadStart(this.Execute));
            t2 = new Thread(new ThreadStart(this.Cancel));
            t1.Start();
            t2.Start();
          }
          finally
          {
            WaitHandle.WaitAll(ExecuteAndCancel);
            Monitor.Exit(typeof(CancelSample));
          }
        }
        FinishedEvent.Set();
      }
      [MTAThread]
      static void Main()
      {
        try
        {
          AutoResetEvent[] ExecutionCompleteEvents = new AutoResetEvent[3];

          // Create the connection that is to be used by three commands
          OracleConnection con = new OracleConnection("user id=scott;" +
            "password=tiger;data source=oracle");
          con.Open();

          // Create instances of CancelSample class
          CancelSample test1 = new CancelSample("select * from all_objects", con);
          CancelSample test2 = new CancelSample("select * from all_objects, emp",
                                                con);
          CancelSample test3 = new CancelSample("select * from all_objects, dept",
                                                con);

          // Create threads for each CancelSample object instance
          Thread t1 = new Thread(new ThreadStart(test1.ExecuteWithinLimitedTime));
          Thread t2 = new Thread(new ThreadStart(test2.ExecuteWithinLimitedTime));
          Thread t3 = new Thread(new ThreadStart(test3.ExecuteWithinLimitedTime));

          // Obtain a handle to an event from each object
          ExecutionCompleteEvents[0] = test1.FinishedEvent;
          ExecutionCompleteEvents[1] = test2.FinishedEvent;
          ExecutionCompleteEvents[2] = test3.FinishedEvent;

          // Start all threads to execute three commands using a single connection
          t1.Start();
          t2.Start();
          t3.Start();

          // Wait for all three commands to finish executing/canceling before
          //closing the connection
          WaitHandle.WaitAll(ExecutionCompleteEvents);
          con.Close();
        }
        catch (Exception e)
        {
          Console.WriteLine(e.ToString());
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- [`http://msdn.microsoft.com/library`](http://msdn.microsoft.com/library) for detailed information about this Microsoft .NET Framework feature
