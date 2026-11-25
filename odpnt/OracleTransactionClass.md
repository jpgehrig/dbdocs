An `OracleTransaction` object represents a local transaction.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.Data.Common.DbTransaction`

`      Oracle.DataAccess.Client.OracleTransaction`

### Declaration

    // C#
    public sealed class OracleTransaction : DbTransaction

    // C#
    public sealed class OracleTransaction : MarshalByRefObject,
       IDbTransaction, IDisposable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

The application calls `BeginTransaction` on the `OracleConnection` object to create an `OracleTransaction` object. The `OracleTransaction` object can be created in Read Committed mode only. Any other mode results in an exception.

The execution of a [DDL](glossary.md) statement in the context of a transaction is not recommended since it results in an implicit commit that is not reflected in the state of the `OracleTransaction` object.

All operations related to [savepoint](glossary.md)s pertain to the current local transaction. Operations like commit and rollback performed on the transaction have no effect on data in any existing `DataSet`.

### Example

    // Database Setup, if you have not done so yet.
    /*
    connect scott/tiger@oracle
    DROP TABLE MyTable;
    CREATE TABLE MyTable (MyColumn NUMBER);
    --CREATE TABLE MyTable (MyColumn NUMBER PRIMARY KEY);

    */

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleTransactionSample
    {
      static void Main()
      {
        // Drop & Create MyTable as indicated Database Setup, at beginning

        // This sample starts a transaction and inserts two records with the same
        // value for MyColumn into MyTable.
        // If MyColumn is not a primary key, the transaction will commit.
        // If MyColumn is a primary key, the second insert will violate the
        // unique constraint and the transaction will rollback.


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

        try
        {
          // Insert the same row twice into MyTable
          cmd.CommandText = "INSERT INTO MyTable VALUES (1)";
          cmd.ExecuteNonQuery();
          cmd.ExecuteNonQuery(); // This may throw an exception
          txn.Commit();
        }
        catch (Exception e)
        {
          // Print the exception message
          Console.WriteLine("e.Message    =  " + e.Message);

          // Rollback the transaction
          txn.Rollback();
        }

        // Check the number of rows in MyTable after transaction
        cmd.CommandText = "SELECT COUNT(*) FROM MyTable";
        myTableCount = int.Parse(cmd.ExecuteScalar().ToString());

        // Prints the number of rows
        // If MyColumn is not a PRIMARY KEY, the value should increase by two.
        // If MyColumn is a PRIMARY KEY, the value should remain same.
        Console.WriteLine("myTableCount = " + myTableCount);

        txn.Dispose();
        cmd.Dispose();

        con.Close();
        con.Dispose();
      }
    }

Not supported in a .NET stored procedure

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Members](TransactionMembers.md)

- [OracleTransaction Static Methods](TransactionStaticMethods.md)

- [OracleTransaction Properties](TransactionProperties.md)
