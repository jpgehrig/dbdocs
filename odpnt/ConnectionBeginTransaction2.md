This method begins a local transaction with the specified isolation level.

### Declaration

    // C#
    public OracleTransaction BeginTransaction(IsolationLevel isolationLevel);

### Parameters

- `isolationLevel`

  The isolation level for the new transaction.

### Return Value

An `OracleTransaction` object representing the new transaction.

### Implements

`IDbConnection`

### Exceptions

`InvalidOperationException` - A transaction has already been started.

`ArgumentException` - The `isolationLevel` specified is invalid.

### Remarks

The following isolation levels are supported: `IsolationLevel.ReadCommitted` and `IsolationLevel.Serializable`.

Although the `BeginTransaction` method supports the `IsolationLevel.Serializable` isolation level, serializable transactions are not supported when using `System.Transactions` and `TransactionScope`.

Requesting other isolation levels causes an exception.

### Remarks (.NET Stored Procedure)

Using this method in a .NET stored procedure for context connection causes a Not Supported exception.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class BeginTransactionSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Create an OracleCommand object using the connection object
        OracleCommand cmd = con.CreateCommand();

        // Start a transaction
        OracleTransaction txn = con.BeginTransaction(IsolationLevel.ReadCommitted);

        // Update EMP table
        cmd.CommandText = "update emp set sal = sal + 100";
        cmd.ExecuteNonQuery();

        // Rollback transaction
        txn.Rollback();
        Console.WriteLine("Transaction rolledback");

        // Clean up
        txn.Dispose();
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
