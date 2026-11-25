This method rolls back a database transaction.

### Declaration

    // C#
    public override void Rollback();

### Implements

`IDbTransaction`

### Exceptions

`InvalidOperationException` - The transaction has already been completed successfully, has been rolled back, or the associated connection is closed.

### Remarks

After a `Rollback()`, the `OracleTransaction` object can no longer be used because the `Rollback` ends the transaction.

### Example

    // Database Setup, if you have not done so yet.
    /*
    connect scott/tiger@oracle
    DROP TABLE MyTable;
    CREATE TABLE MyTable (MyColumn NUMBER);

    */

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class RollbackSample
    {
      static void Main()
      {
        // Drop & Create MyTable as indicated previously in Database Setup

        // This sample starts a transaction and inserts one record into MyTable.
        // It then rollsback the transaction, the number of rows remains the same

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = con.CreateCommand();

        // Check the number of rows in MyTable before transaction
        cmd.CommandText = "SELECT COUNT(*) FROM MyTable";
        int myTableCount = int.Parse(cmd.ExecuteScalar().ToString());

        // Print the number of rows in MyTable
        Console.WriteLine("myTableCount = " + myTableCount);

        // Start a transaction
        OracleTransaction txn = con.BeginTransaction(
          IsolationLevel.ReadCommitted);

        // Insert a row into MyTable
        cmd.CommandText = "INSERT INTO MyTable VALUES (1)";
        cmd.ExecuteNonQuery();

        // Rollback the transaction
        txn.Rollback();

        // Check the number of rows in MyTable after transaction
        cmd.CommandText = "SELECT COUNT(*) FROM MyTable";
        myTableCount = int.Parse(cmd.ExecuteScalar().ToString());

        // Prints the number of rows, should remain the same
        Console.WriteLine("myTableCount = " + myTableCount);

        txn.Dispose();
        cmd.Dispose();

        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Class](OracleTransactionClass.md)

- [OracleTransaction Members](TransactionMembers.md)
