`OracleDBStartupMode `enumerated values specify the database startup options.

Table 6-176 lists all the `OracleDBStartupMode` enumeration values with a description of each enumerated value.

Table 6-176 OracleDBStartupMode Enumeration Values

| Member Name     | Description                                                                                                                                                                                      |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NoRestriction` | Starts the database and allows access to all users.                                                                                                                                              |
| `Restrict`      | Starts the database and allows database access only to users having the `CREATE SESSION` and `RESTRICTED SESSION` privileges. These privileges are normally assigned to database administrators. |
| `Force`         | Shuts down a running instance in abort mode and starts a new instance.                                                                                                                           |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleConnection Class](OracleConnectionClass.md)"

- "[Startup](DatabaseStartupOverloads.md)"
