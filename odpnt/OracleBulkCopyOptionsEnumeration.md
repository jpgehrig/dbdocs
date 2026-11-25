The `OracleBulkCopyOptions` enumeration specifies the values that can be combined with an instance of the `OracleBulkCopy` class and used as options to determine its behavior and the behavior of the `WriteToServer` methods for that instance.

Table 17-17 lists all the `OracleBulkCopyOptions` enumeration values with a description of each enumerated value.

Table 17-17 OracleBulkCopyOptions Enumeration Members

| Member Name              | Description                                                                                                                                                                                                                                                                                                                                                          |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Default`                | Indicates that the default value for all options are to be used                                                                                                                                                                                                                                                                                                      |
| `UseInternalTransaction` | Indicates that each batch of the bulk copy operation occurs within a transaction. If the connection used to perform the bulk copy operation is already part of a transaction, an `InvalidOperationException` exception is raised.<br>If this member is not specified, `BatchSize` number of rows are sent to the database, without any transaction-related activity. |

**Note:**

All bulk copy operations are agnostic of any local or distributed transaction created by the application.

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- `OracleBulkCopy` "[BulkCopyOptions](BulkCopyBulkCopyOptions.md)"
