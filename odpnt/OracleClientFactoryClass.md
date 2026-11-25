An `OracleClientFactory` object allows applications to instantiate ODP.NET classes in a generic way.

### Class Inheritance

`System.Object`

`  System.Data.Common.DbProviderFactory`

`    Oracle.DataAccess.Client.OracleClientFactory`

### Declaration

    // C#
    public sealed class OracleClientFactory : DbProviderFactory

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           |
|:---------------|:---------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class FactorySample
    {
      static void Main()
      {
        string constr = "user id=scott;password=tiger;data source=oracle";

        DbProviderFactory factory =
                DbProviderFactories.GetFactory("Oracle.DataAccess.Client");

        DbConnection conn = factory.CreateConnection();

        try
        {
          conn.ConnectionString = constr;
          conn.Open();

          DbCommand cmd = factory.CreateCommand();
          cmd.Connection = conn;
          cmd.CommandText = "select * from emp";

          DbDataReader reader = cmd.ExecuteReader();
          while (reader.Read())
            Console.WriteLine(reader["EMPNO"] + " : " + reader["ENAME"]);
        }
        catch (Exception ex)
        {
          Console.WriteLine(ex.Message);
          Console.WriteLine(ex.StackTrace);
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleClientFactory Members](OracleClientFactoryMembers.md)

- [OracleClientFactory Field](ClientFactoryField.md)

- [OracleClientFactory Constructor](ClientFactoryConstructor.md)

- [OracleClientFactory Public Properties](ClientFactoryProperties.md)

- [OracleClientFactory Public Methods](ClientFactoryPublicMethods.md)
