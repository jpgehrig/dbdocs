`OracleRowidInfo` enumeration values specify whether `ROWID` information is included as part of the `ChangeNotificationEventArgs` or not.

[Table 9-28](OracleNotificationTypeEnumeration.md) lists all the `OracleRowidInfo`enumeration values with a description of each enumerated value.

Table 9-27 OracleRowidInfo Members

| Member Name | Description                                                                                                                                        |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `Default`   | `ROWID` information is included only if `OracleCommand.AddRowid` property is set to true or if `ROWID` column is explicitly included in the query. |
| `Include`   | `ROWID` information is included regardless of whether `ROWID` is included in the select-list of the query or not.                                  |
| `Exclude`   | `ROWID` information is not included regardless of whether `ROWID` is included in the select-list of the query or not.                              |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[RowidInfo](DependencyInstancePropertiesRowidInfo.md)"
