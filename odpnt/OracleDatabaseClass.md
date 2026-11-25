An `OracleDatabase` object represents an Oracle Database instance.

### Class Inheritance

`System.Object`

`  Oracle.DataAccess.Client.OracleDatabase`

### Declaration

    // C#
    public sealed class OracleDatabase : IDisposable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    namespace Startup
    {
      class Test
      {
        static void Main()
        {
          OracleConnection con = null;
          OracleDatabase db = null;
          string constring = "dba privilege=sysdba;user id=scott;password=tiger;data source=oracle";

          try
          {
            // Open a connection to see if the DB is up
            con = new OracleConnection(constring);
            con.Open();

            Console.WriteLine("The Oracle database is already up.");
          }
          catch (OracleException ex)
          {
            // If the database is down, start up the DB
            if (ex.Number == 1034)
            {
              Console.WriteLine("The Oracle database is down.");

              // Create an instance of an OracleDatbase object
              db = new OracleDatabase(constring);

              // Start up the database
              db.Startup();

              Console.WriteLine("The Oracle database is now up.");

              // Executing Startup() is the same as the following:
              // db.Startup(OracleDBStartupMode.NoRestriction, null, true);
              // which is also the same as:
              // db.Startup(OracleDBStartupMode.NoRestriction, null, false);
              // db.ExecuteNonQuery("ALTER DATABASE MOUNT");
              // db.ExecuteNonQuery("ALTER DATABASE OPEN");

              // Dispose the OracleDatabase object
              db.Dispose();
            }
            else
            {
              Console.WriteLine("Error: " + ex.Message);
            }
          }
          finally
          {
            // Dispose the OracleConnetion object
            con.Dispose();
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Members](DatabaseMembers.md)

- [OracleDatabase Constructors](DatabaseCtor.md)

- [OracleDatabase Properties](DatabaseProperties.md)

- [OracleDatabase Public Methods](DatabasePublicMethods.md)
