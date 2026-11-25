An `OracleConnection` object represents a connection to an Oracle database.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.ComponentModel.Component`

`      System.Data.Common.DbConnection`

`        Oracle.DataAccess.Client.OracleConnection`

### Declaration

    // C#
    public sealed class OracleConnection : DbConnection, IDbConnection, ICloneable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleConnectionSample
    {
      static void Main()
      {
        // Connect
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Execute a SQL SELECT
        OracleCommand cmd = con.CreateCommand();
        cmd.CommandText = "select * from emp";
        OracleDataReader reader = cmd.ExecuteReader();

        // Print all employee numbers
        while (reader.Read())
          Console.WriteLine(reader.GetInt32(0));

        // Clean up
        reader.Dispose();
        cmd.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Members](ConnectionMembers.md)

- [OracleConnection Constructors](ConnectionCtors.md)

- [OracleConnection Static Properties](ConnectionStaticProperties.md)

- [OracleConnection Static Methods](ConnectionStaticMethods.md)

- [OracleConnection Properties](ConnectionProperties.md)

- [OracleConnection Public Methods](ConnectionPublicMethods.md)

- [OracleConnection Events](ConnectionEvents.md)
