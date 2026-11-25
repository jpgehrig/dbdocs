An `OracleDataSourceCollection` supports adding and deleting network service name (i.e. TNS) entries for ODP.NET's use to connect to an Oracle database.

### Class Inheritance

`System.Object`

` Oracle.ManagedDataAccess.Client.OracleDataSourceCollection`

### Declaration

    // C#
    public sealed class OracleDataSourceCollection

### Requirements

| Provider       | ODP.NET Core                      |
|:---------------|:----------------------------------|
| Assembly       | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.6.1 or higher                   |
| .NET Core      | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

    using System;
    using Oracle.ManagedDataAccess.Client;

    namespace NetCoreApp
    {
      class DataSourcesExample
      {
        static void Main(string[] args)
        {
          // Example to configure Data Sources for the ODP.NET Core provider.

          // Add data source through Add method on OracleDataSourceCollection
          OracleConfiguration.OracleDataSources.Add("orcl1", "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host1)(PORT=1234))(CONNECT_DATA=(SERVICE_NAME=oracle)(SERVER=dedicated)))");

          // Add data source through indexer method on OracleDataSourceCollection
          OracleConfiguration.OracleDataSources["orcl2"] =
            "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host1)(PORT=1234))(CONNECT_DATA=(SERVICE_NAME=oracle)(SERVER=dedicated)))";

          // Get number of data sources configured
          int numDataSources = OracleConfiguration.OracleDataSources.Count;

          // Get OracleDataSourceCollection object
          OracleDataSourceCollection dsColl = OracleConfiguration.OracleDataSources;

          // Add server through Add method on OracleDataSourceCollection
          dsColl.Add("orcl3", "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host3)(PORT=1234))(CONNECT_DATA=(SERVICE_NAME=oracle)(SERVER=dedicated)))");

          // Add server through indexer method on OracleDataSourceCollection
          dsColl["orcl4"] = "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host4)(PORT=1234))(CONNECT_DATA=(SERVICE_NAME=oracle)(SERVER=dedicated)))";

          // Remove a data source
          OracleConfiguration.OracleDataSources.Remove("db2");

          // Get number of data sources configured
          numDataSources = OracleConfiguration.OracleDataSources.Count;

          // Get value corresponding to a data source.
          string dsVal = OracleConfiguration.OracleDataSources["db1"];

          OracleConnection orclCon = null;

          try
          {
            // Open a test connection
            orclCon = new OracleConnection("user id=scott; password=tiger; data source=orcl3");

            orclCon.Open();
            orclCon.Close();
          }
          catch (OracleException ex)
          {
            Console.WriteLine(ex);
          }
          finally
          {
            // Close the connection
            if (null != orclCon)
              orclCon.Close();
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataSourceCollection Members](OracleDataSourceCollectionMembers.md)

- [OracleDataSourceCollection Methods](DataSourceCollectionMethods.md)

- [OracleDataSourceCollection Properties](DataSourceCollectionProperties.md)
