The `OracleParameterStatus` enumeration type indicates whether a `NULL` value is fetched from a column, or truncation has occurred during the fetch, or a `NULL` value is to be inserted into a database column.

Table 6-180 lists all the `OracleParameterStatus` enumeration values with a description of each enumerated value.

Table 6-180 OracleParameterStatus Members

| Member Name   | Description                                                                                                                                                                            |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Success`     | Indicates that (for input parameters) the input value has been assigned to the column. For output parameter, it indicates that the provider assigned an intact value to the parameter. |
| `NullFetched` | Indicates that a `NULL` value has been fetched from a column or an `OUT` parameter.                                                                                                    |
| `NullInsert`  | Indicates that a `NULL` value is to be inserted into a column.                                                                                                                         |
| `Truncation`  | Indicates that truncation has occurred when fetching the data from the column.                                                                                                         |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleParameter Class](OracleParameterClass.md)"

- `OracleParameter` "[ArrayBindStatus](ParameterArrayBindStatus.md)"

- `OracleParameter` "[Value](ParameterValue.md)"
