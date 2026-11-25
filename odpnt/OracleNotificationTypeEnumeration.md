`OracleNotificationType` enumerated values specify the different types that cause the notification.

Table 9-28 lists all the `OracleNotificationType` enumeration values with a description of each enumerated value.

Table 9-28 OracleNotificationType Members

| Member Name | Description                                  |
|:------------|:---------------------------------------------|
| `Change`    | A change occurs in the database.             |
| `Subscribe` | A change occurs in the subscription.         |
| `Query`     | A query-based change occurs in the database. |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

"[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"
