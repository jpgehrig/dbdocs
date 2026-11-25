This method shuts down the database instance using the specified mode.

### Declaration

    //C#
    public void Shutdown(OracleDBShutdownMode shutdownMode, bool bCloseDismountAndFinalize);

### Parameters

- `shutdownMode`

  A `OracleDBShutdownMode` enumeration value.

- `bCloseDismountAndFinalize`

  A `boolean` signifying whether the database is to be closed, dismounted, and finalized.

### Exceptions

`OracleException` - The database shutdown request has failed.

### Remarks

This method shuts down a database instance in the specified mode. If the `bCloseDismountAndFinalize` parameter is `true`, then the method also closes the database, dismounts the database, and shuts down the instance using the `OracleDBShutdownMode.Final` mode.

If the `bCloseDismountAndFinalize` parameter is `true`, then this method does not throw exceptions for cases where the database has been already closed, dismounted, or shutdown appropriately. If other errors are encountered, then an exception is thrown.

If the `bCloseDismountAndFinalize` parameter is `false`, then the application needs to explicitly close and dismount the database. The application can then reinvoke the method using the `OracleDBShutdownMode.Final` mode to properly shut down the database. For example, if `db` is an instance of the `OracleDatabase` class, then the application invokes the following:

1.  `db.Shutdown(OracleDBShutdownMode.Default, false); `

2.  `db.ExecuteNonQuery("ALTER DATABASE CLOSE NORMAL");`

3.  `db.ExecuteNonQuery("ALTER DATABASE DISMOUNT");`

4.  `db.Shutdown(OracleDBShutdownMode.Final);`

**Note:**

- The `OracleDBShutdownMode.Final` enumeration value should not be used as the `shutdownMode` for the initial method invocation. The `OracleDBShutdownMode.Final` mode should be used only if the database is already closed and dismounted. Otherwise, the method might wait indefinitely.

- If the specified `shutdownMode` is `OracleDBShutdownMode.Final`, then the value of the `bCloseDismountAndFinalize` input parameter is ignored, as the database should have been closed and dismounted already.

If the specified `shutdownMode` is `OracleDBShutdownMode.Abort`, then the value of the `bCloseDismountAndFinalize` input parameter is ignored, as the `Abort` mode requires the database to be closed, dismounted, and finalized.

Invoking this method against an Oracle Real Application Clusters (Oracle RAC) database shuts down only that database instance to which the `OracleDatabase` object is connected.

### Example

    using System;
    using Oracle.DataAccess.Client;

    namespace Shutdown
    {
      class Test
      {
        static void Main()
        {
          OracleConnection con = null;
          OracleDatabase db = null;
          string constring = "user id=scott;password=tiger;data source=oracle;" +
            "pooling=false;dba privilege=sysdba";

          try
          {
            // Open a connection to see if the DB is up;
            con = new OracleConnection(constring);
            con.Open();

            Console.WriteLine("The Oracle database is currently up.");

            // If open succeeds, we know that the database is up.
            // We have to dispose the connection so that we can
            //   shutdown the database.
            con.Dispose();

            // Shutdown the database
            db = new OracleDatabase(constring);
            db.Shutdown();

            Console.WriteLine("The Oracle database is shut down.");

            // Executing Shutdown() above is the same as the following:
            // db.Shutdown(OracleDBShutdownMode.Default, false);
            // db.ExecuteNonQuery("ALTER DATABASE CLOSE NORMAL");
            // db.ExecuteNonQuery("ALTER DATABASE DISMOUNT");
            // db.Shutdown(OracleDBShutdownMode.Final);

            // Dispose the OracleDatabase object
            db.Dispose();
          }
          catch (OracleException ex)
          {
            Console.WriteLine("An error has occurred: {0}", ex.Message);
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)

- "[OracleDBShutdownMode Enumeration](OracleDBShutdownModeEnumeration.md)"
