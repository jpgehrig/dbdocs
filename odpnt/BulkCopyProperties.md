`OracleBulkCopy` properties are listed in Table 17-5.

Table 17-5 OracleBulkCopy Properties

| Property                                                        | Description                                                                                                     |
|:----------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| [BatchSize](BulkCopyBatchSize.md)                               | Specifies the number of rows to be sent as a batch to the database                                              |
| [BulkCopyOptions](BulkCopyBulkCopyOptions.md)                   | Specifies the `OracleBulkCopyOptions` enumeration value that determines the behavior of the bulk copy operation |
| [BulkCopyTimeout](BulkCopyBulkCopyTimeout.md)                   | Specifies the number of seconds allowed for the bulk copy operation to complete before it is aborted            |
| [ColumnMappings](BulkCopyColumnMappings.md)                     | Specifies the column mappings between the data source and destination table                                     |
| [Connection](BulkCopyConnection.md)                             | Specifies the `OracleConnection` object that the Oracle database uses to perform the bulk copy operation        |
| [DestinationPartitionName](BulkCopyDestinationPartitionName.md) | Specifies the database partition that the data is loaded into                                                   |
| [DestinationTableName](BulkCopyDestinationTableName.md)         | Specifies the database table that the data is loaded in                                                         |
| [NotifyAfter](BulkCopyNotifyAfter.md)                           | Defines the number of rows to be processed before a notification event is generated                             |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
