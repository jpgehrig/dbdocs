This method creates a [savepoint](glossary.md) within the current transaction.

### Declaration

    // C#
    public void Save(string savepointName);

### Parameters

- `savepointName`

  The name of the savepoint being created in the current transaction.

### Exceptions

`InvalidOperationException` - The transaction has already been completed.

### Remarks

After creating a savepoint, the transaction does not enter a completed state and can be used for further operations.

The `savepointName` specified is created in the database in a case-insensitive manner. Calling the `Rollback` method rolls back to `savepointName`. This allows portions of a transaction to be rolled back, instead of the entire transaction.

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

    class SaveSample
    {
      static void Main()
      {
        // Drop & Create MyTable as indicated in Database Setup, at beginning

        // This sample starts a transaction and creates a savepoint after
        // inserting one record into MyTable.
        // After inserting the second record it rollsback to the savepoint
        // and commits the transaction. Only the first record will be inserted

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

        // Create a savepoint
        txn.Save("MySavePoint");

        // Insert another row into MyTable
        cmd.CommandText = "insert into mytable values (2)";
        cmd.ExecuteNonQuery();

        // Rollback to the savepoint
        txn.Rollback("MySavePoint");

        // Commit the transaction
        txn.Commit();

        // Check the number of rows in MyTable after transaction
        cmd.CommandText = "SELECT COUNT(*) FROM MyTable";
        myTableCount = int.Parse(cmd.ExecuteScalar().ToString());

        // Prints the number of rows, should have increased by 1
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
