`OracleDBShutdownMode `enumerated values specify the database shutdown options.

[Table 6-176](OracleDBStartupModeEnumeration.md) lists all the `OracleDBShutdownMode` enumeration values with a description of each enumerated value.

Table 6-175 OracleDBShutdownMode Enumeration Values

| Member Name          | Description                                                                                                                                                |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Default`            | Refuses new connections and waits for existing connections to end.                                                                                         |
| `Transactional`      | Refuses new connections and does not allow any new transactions. Waits for active transactions to commit.                                                  |
| `TransactionalLocal` | Refuses new connections and does not allow any new transactions. Waits for only local transactions to commit.                                              |
| `Immediate`          | Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and rolled back.         |
| `Final`              | Shuts down the database. Used in the second call for shutdown after the database has been closed and dismounted.                                           |
| `Abort`              | Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and are not rolled back. |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleConnection Class](OracleConnectionClass.md)"

- "[Shutdown](DatabaseShutdownOverloads.md)"
