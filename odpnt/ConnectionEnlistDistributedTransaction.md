This method enables applications to explicitly enlist in a specific distributed transaction after a connection has been opened.

### Declaration

    // C#
    public void EnlistDistributedTransaction(ITransaction transaction);

### Parameters

- `transaction`

  An `ITransaction` interface.

### Exceptions

`InvalidOperationException` - The connection is part of a local transaction or the connection is closed.

### Remarks

`EnlistDistributedTransaction` enables objects to enlist in a specific transaction that is passed to the method. The `ITransaction` interface can be obtained by applying an (`ITransaction`) cast to the `ContexUtil.Transaction` property within the component that started the distributed transaction.

The connection must be open before calling this method or an `InvalidOperationException` is thrown.

If a connection is part of a local transaction that was started implicitly or explicitly while attempting to enlist in a distributed transaction, the local transaction is rolled back and an exception is thrown.

By default, distributed transactions roll back, unless the method-level `AutoComplete` declaration is set.

Invoking the commit on the `ITranasction` raises an exception.

Invoking the rollback on the `ITransaction` method and calling `ContextUtil.SetComplete` on the same distributed transaction raises an exception.

### Remarks (.NET Stored Procedure)

Using this method causes a Not Supported exception.

### Example

Application:

    // C#

    /* This is the class that will utilize the Enterprise Services
       component.  This module needs to be built as an executable.

       The Enterprise Services Component DLL must be built first
       before building this module.
       In addition, the DLL needs to be referenced appropriately
       when building this application.
    */

    using System;
    using System.EnterpriseServices;
    using DistribTxnSample;

    class DistribTxnSample_App
    {
      static void Main()
      {
        DistribTxnSample_Comp comp = new DistribTxnSample_Comp();
        comp.DoWork();
      }
    }

Component:

    // C#

    /* This module needs to be
       1) built as a component DLL/Library
       2) built with a strong name

      This library must be built first before the application is built.
    */

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using System.EnterpriseServices;

    namespace DistribTxnSample
    {
      [Transaction(TransactionOption.RequiresNew)]
      public class DistribTxnSample_Comp : ServicedComponent
      {
        public void DoWork()
        {
          string constr =
            "User Id=scott;Password=tiger;Data Source=oracle;enlist=false";
          OracleConnection con = new OracleConnection(constr);
          con.Open();

          // Enlist in a distrubuted transaction
          con.EnlistDistributedTransaction((ITransaction)ContextUtil.Transaction);

          // Update EMP table
          OracleCommand cmd = con.CreateCommand();
          cmd.CommandText = "UPDATE emp set sal = sal + .01";
          cmd.ExecuteNonQuery();

          // Commit
          ContextUtil.SetComplete();

          // Dispose OracleConnection object
          con.Dispose();
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[EnlistTransaction](ConnectionEnlistTransaction.md)"

- [`http://msdn.microsoft.com/library`](http://msdn.microsoft.com/library) for detailed information about this Microsoft .NET Framework feature
