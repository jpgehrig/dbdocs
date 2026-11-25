With ADO.NET, data classes derive from the base classes defined in the `System.Data.Common` namespace. Developers can create provider-specific instances of these base classes using provider factory classes.

Provider factory classes allow generic data access code to access multiple data sources with a minimum of data source-specific code. This reduces much of the conditional logic currently used by applications accessing multiple data sources.

Using Oracle Data Provider for .NET, the `OracleClientFactory` class can be returned and instantiated, enabling an application to create instances of the following ODP.NET classes that inherit from the base classes:

Table 3-1 ODP.NET Classes that Inherit from ADO.NET 2.0 Base Classes

| ODP.NET Classes                 | Inherited from ADO.NET 2.0 Base Class |
|:--------------------------------|:--------------------------------------|
| `OracleClientFactory`           | `DbProviderFactory`                   |
| `OracleCommand`                 | `DbCommand`                           |
| `OracleCommandBuilder`          | `DbCommandBuilder`                    |
| `OracleConnection`              | `DbConnection`                        |
| `OracleConnectionStringBuilder` | `DbConnectionStringBuilder`           |
| `OracleDataAdapter`             | `DbDataAdapter`                       |
| `OracleDataReader`              | `DbDataReader`                        |
| `OracleDataSourceEnumerator`    | `DbDataSourceEnumerator`              |
| `OracleException`               | `DbException`                         |
| `OracleParameter`               | `DbParameter`                         |
| `OracleParameterCollection`     | `DbParameterCollection`               |
| `OracleTransaction`             | `DbTransaction`                       |

In general, applications still require Oracle-specific connection strings, SQL or stored procedure calls, and declare that a factory from ODP.NET is used.

**Note:**

ODP.NET Core does not support factory classes.

**See Also:**

[OracleClientFactory Class](OracleClientFactoryClass.md)
