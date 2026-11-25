`OracleNotificationSource` enumerated values specify the different sources that cause notification.

Table 9-29 lists all the `OracleNotificationSource` enumeration values with a description of each enumerated value.

Table 9-29 OracleNotificationSource Members

| Member Name    | Description                                                     |
|:---------------|:----------------------------------------------------------------|
| `Data`         | The data in a table has changed.                                |
| `Database`     | A database event such as a database startup or shutdown occurs. |
| `Object`       | A database object is altered or dropped.                        |
| `Subscription` | The subscription is changed.                                    |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

"[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"
