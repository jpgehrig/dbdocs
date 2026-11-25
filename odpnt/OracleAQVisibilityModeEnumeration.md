Table 12-38 lists all the `OracleAQVisibilityMode` enumeration values with a description of each enumerated value.

Table 12-38 OracleAQVisibilityMode Members

| Member Name | Description                                                                                                                                 |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `Immediate` | Indicates that the enqueue or dequeue operation is not part of the current transaction. The operation constitutes a transaction of its own. |
| `OnCommit`  | Indicates that the enqueue or dequeue operation is part of the current transaction. This is the default case.                               |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"
