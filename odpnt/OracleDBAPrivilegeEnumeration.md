`OracleDBAPrivilege `enumerated values are used to explicitly specify the DBA Privilege required while creating the `OracleCredential` object.

[Table 6-172](OracleConnectionTypeEnumeration.md) lists all the `OracleDBAPrivilege` enumeration values with a description of each enumerated value.

Table 6-174 OracleDBAPrivilege Enumeration Values

| Member Name | Description                          |
|:------------|:-------------------------------------|
| `None`      | Default value, no DBA privilege set. |
| `SYSDBA`    | `SYSDBA` connection                  |
| `SYSOPER`   | `SYSOPER` connection                 |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCredential Class](OracleCredentialClass.md)

- [DBAPrivilege](CredentialDBAPrivilege.md)
