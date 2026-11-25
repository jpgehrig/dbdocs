`OracleNotificationInfo` enumerated values specify the database event that causes the notification.

Table 9-30 lists all the `OracleNotificationInfo` enumeration values with a description of each enumerated value.

Table 9-30 OracleNotificationInfo Members

| Member Name    | Description                                                                            |
|:---------------|:---------------------------------------------------------------------------------------|
| `Insert`       | A row is inserted.                                                                     |
| `Delete`       | A row is deleted.                                                                      |
| `Update`       | A row is updated.                                                                      |
| `Startup`      | A database starts.                                                                     |
| `Shutdown`     | A database shuts down.                                                                 |
| `Shutdown_any` | A database instance in a Real Application Cluster (Oracle RAC) environment shuts down. |
| `Alter`        | An object is altered.                                                                  |
| `Drop`         | An object or database is dropped.                                                      |
| `End`          | A registration is removed.                                                             |
| `Error`        | A notification error occurs.                                                           |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

"[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"
