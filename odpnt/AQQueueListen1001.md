This method listens for messages on the queue on behalf of `listenConsumers`.

### Declaration

    // C#
    public string Listen(string[] listenConsumers);

### Parameters

- `listenConsumers`

  An array of consumers to listen for on this queue. This parameter should be `null` in case of single consumer queues.

### Return Value

A `string`.

### Exceptions

`InvalidOperationException` - The connection is not open.

`ObjectDisposedException` - The object is already disposed.

### Remarks

This call blocks the calling thread until there is a message ready for consumption for a consumer in the `listenConsumers` array. It returns a `string` representing the consumer name for which the message is ready.

`Listen` is useful in situations that require waiting until a message is available in the queue for consumers whose names are specified in `listenConsumers`.

### Example

The following example demonstrates using the `Listen` method. The first part of the example performs the requisite database setup for the database user, `SCOTT`. The second part of the example demonstrates how a thread can listen and wait until a message is enqueued.

    -- Part I: Database setup required for this demo

    ------------------------------------------------------------------
    -- SQL to grant appropriate privilege to database user, SCOTT
    ------------------------------------------------------------------
    SQL> ALTER USER SCOTT ACCOUNT UNLOCK IDENTIFIED BY Pwd4Sct;
    User altered.
    GRANT ALL ON DBMS_AQADM TO scott;

    ------------------------------------------------------------------
    -- PLSQL to create queue-table and queue and start queue for SCOTT
    ------------------------------------------------------------------
    BEGIN
      DBMS_AQADM.CREATE_QUEUE_TABLE(
        queue_table=>'scott.test_q_tab',
        queue_payload_type=>'RAW',
        multiple_consumers=>FALSE);

      DBMS_AQADM.CREATE_QUEUE(
        queue_name=>'scott.test_q',
        queue_table=>'scott.test_q_tab');

      DBMS_AQADM.START_QUEUE(queue_name=>'scott.test_q');
    END;
    /

    ------------------------------------------------------------------
    -- PLSQL to stop queue and drop queue & queue-table from SCOTT
    ------------------------------------------------------------------
    BEGIN
      DBMS_AQADM.STOP_QUEUE('scott.test_q');

      DBMS_AQADM.DROP_QUEUE(
        queue_name => 'scott.test_q',
        auto_commit => TRUE);

      DBMS_AQADM.DROP_QUEUE_TABLE(
        queue_table => 'scott.test_q_tab',
        force => FALSE,
        auto_commit => TRUE);
    END;
    /
    -- End of Part I, database setup.

    //Part II: Demonstrates using the Listen method
    //C#
    using System;
    using System.Text;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;
    using System.Threading;

    namespace ODPSample
    {
      /// <summary>
      /// Demonstrates how a thread can listen and wait until a message is enqueued.
      /// Once a message is enqueued, the listening thread returns from the
      /// blocked Listen() method invocation and dequeues the message.
      /// </summary>
      class EnqueueDequeue
      {
        static bool s_bListenReturned = false;

        static void Main(string[] args)
        {
          // Create connection
          string constr = "user id=scott;password=Pwd4Sct;data source=oracle";
          OracleConnection con = new OracleConnection(constr);

          // Create queue
          OracleAQQueue queue = new OracleAQQueue("scott.test_q", con);

          try
          {
            // Open connection
            con.Open();

            // Set message type for the queue
            queue.MessageType = OracleAQMessageType.Raw;

            // Spawning a thread which will listen for a message
            ThreadStart ts = new ThreadStart(TestListen);
            Thread t = new Thread(ts);
            t.Start();

            System.Threading.Thread.Sleep(2000);

            // Begin transaction for enqueue
            OracleTransaction txn = con.BeginTransaction();

            // Prepare message and RAW payload
            OracleAQMessage enqMsg = new OracleAQMessage();
            byte[] bytePayload = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
            enqMsg.Payload = bytePayload;

            // Prepare to Enqueue
            queue.EnqueueOptions.Visibility = OracleAQVisibilityMode.OnCommit;

            Console.WriteLine("[Main Thread]   Enqueuing a message...");
            Console.WriteLine("[Main Thread]   Enqueued Message Payload      : "
              + ByteArrayToString(enqMsg.Payload as byte[]));
            Console.WriteLine();

            // Enqueue message
            queue.Enqueue(enqMsg);

            // Enqueue transaction commit
            txn.Commit();

            // Loop till Listen returns
            while (!s_bListenReturned)
              System.Threading.Thread.Sleep(1000);
          }
          catch (Exception e)
          {
            Console.WriteLine("Error: {0}", e.Message);
          }
          finally
          {
            // Close/Dispose objects
            queue.Dispose();
            con.Close();
            con.Dispose();
          }
        }

        static void TestListen()
        {
          // Create connection
          string constr = "user id=scott;password=Pwd4Sct;data source=oracle";
          OracleConnection conListen = new OracleConnection(constr);

          // Create queue
          OracleAQQueue queueListen = new OracleAQQueue("scott.test_q", conListen);

          try
          {
              // Open the connection for Listen thread.
              // Connection blocked on Listen thread can not be used for other DB
              // operations
              conListen.Open();

              // Set message type for the queue
              queueListen.MessageType = OracleAQMessageType.Raw;

            // Listen
            queueListen.Listen(null);

            Console.WriteLine("[Listen Thread] Listen returned... Dequeuing...");

            // Begin txn for Dequeue
            OracleTransaction txn = conListen.BeginTransaction();

            // Prepare to Dequeue
            queueListen.DequeueOptions.Visibility = OracleAQVisibilityMode.OnCommit;
            queueListen.DequeueOptions.Wait = 10;

            // Dequeue message
            OracleAQMessage deqMsg = queueListen.Dequeue();
            Console.WriteLine("[Listen Thread] Dequeued Message Payload      : "
              + ByteArrayToString(deqMsg.Payload as byte[]));

            // Dequeue txn commit
            txn.Commit();

            // Allow the main thread to exit
            s_bListenReturned = true;
          }
          catch (Exception e)
          {
            Console.WriteLine("Error: {0}", e.Message);
          }
          finally
          {
            // Close/Dispose objects
            queueListen.Dispose();
            conListen.Close();
            conListen.Dispose();
          }
        }

        // Function to convert byte[] to string
        static private string ByteArrayToString(byte[] byteArray)
        {
          StringBuilder sb = new StringBuilder();
          for (int n = 0; n < byteArray.Length; n++)
          {
            sb.Append((int.Parse(byteArray[n].ToString())).ToString("X"));
          }
          return sb.ToString();
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
