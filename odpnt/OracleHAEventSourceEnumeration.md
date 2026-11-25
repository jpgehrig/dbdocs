The `OracleHAEventSource` enumeration indicates the source of the HA event.

Table 8-3 lists all the `OracleHAEventSource` enumeration values with a description of each enumerated value.

Table 8-3 OracleHAEventSource Enumeration Member Values

| Member Name     | Description                                     |
|:----------------|:------------------------------------------------|
| `Service`       | The source of the HA Event is a service.        |
| `ServiceMember` | The source of the HA Event is a service member. |
| `Database`      | The source of the HA Event is a database.       |
| `Host`          | The source of the HA Event is a host.           |
| `Instance`      | The source of the HA Event is an instance.      |
| `Node`          | The source of the HA Event is a node.           |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- "[Source](HAEventArgsSource.md)"
