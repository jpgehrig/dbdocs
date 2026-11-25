`OracleBulkCopy` members are listed in the following tables.

### OracleBulkCopy Constructors

`OracleBulkCopy` constructors are listed in Table 17-1.

Table 17-1 OracleBulkCopy Constructors

| Constructor                                            | Description                                                                      |
|:-------------------------------------------------------|:---------------------------------------------------------------------------------|
| [OracleBulkCopy Constructors](BulkCopyConstructors.md) | `OracleBulkCopy` constructors create new instances of the `OracleBulkCopy` class |

### OracleBulkCopy Properties

`OracleBulkCopy` properties are listed in Table 17-2.

Table 17-2 OracleBulkCopy Properties

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

### OracleBulkCopy Public Methods

`OracleBulkCopy` public methods are listed in Table 17-3.

Table 17-3 OracleBulkCopy Public Methods

| Method                                             | Description                                              |
|:---------------------------------------------------|:---------------------------------------------------------|
| [Close](BulkCopyClose.md)                          | Closes the `OracleBulkCopy` instance                     |
| [Dispose](BulkCopyDispose.md)                      | Releases any resources or memory allocated by the object |
| [WriteToServer](BulkCopyWriteToServerOverloads.md) | Copies rows to a destination table                       |

### OracleBulkCopy Events

`OracleBulkCopy` events are listed in Table 17-4.

Table 17-4 OracleBulkCopy Events

| Event                                           | Description                                                                                                       |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| [OracleRowsCopied](BulkCopyOracleRowsCopied.md) | Triggered every time the number of rows specified by the `OracleBulkCopy.NotifyAfter` property has been processed |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)
