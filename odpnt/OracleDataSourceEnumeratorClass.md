An `OracleDataSourceEnumerator` object allows applications to generically obtain a collection of data sources to connect to.

### Class Inheritance

`System.Object`

`  System.DbDataSourceEnumerator`

`    Oracle.DataAccess.Client.OracleDataSourceEnumerator`

### Declaration

    // C#
    public sealed class OracleDataSourceEnumerator : DbDataSourceEnumerator

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class DataSourceEnumSample
    {
      static void Main()
      {
        string ProviderName = "Oracle.DataAccess.Client";

        DbProviderFactory factory = DbProviderFactories.GetFactory(ProviderName);

        if (factory.CanCreateDataSourceEnumerator)
        {
          DbDataSourceEnumerator dsenum = factory.CreateDataSourceEnumerator();
          DataTable dt = dsenum.GetDataSources();

          // Print the first column/row entry in the DataTable
          Console.WriteLine(dt.Columns[0] + " : " + dt.Rows[0][0]);
          Console.WriteLine(dt.Columns[1] + " : " + dt.Rows[0][1]);
          Console.WriteLine(dt.Columns[2] + " : " + dt.Rows[0][2]);
          Console.WriteLine(dt.Columns[3] + " : " + dt.Rows[0][3]);
          Console.WriteLine(dt.Columns[4] + " : " + dt.Rows[0][4]);
        }
        else
          Console.Write("Data source enumeration is not supported by provider");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataSourceEnumerator Members](OracleDataSourceEnumeratorMembers.md)

- [OracleDataSourceEnumerator Constructor](DataSourceEnumeratorCtor.md)

- [OracleDataSourceEnumerator Public Methods](DataSourceEnumeratorPublicMethods.md)
