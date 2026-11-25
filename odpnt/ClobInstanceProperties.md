`OracleClob` instance properties are listed in Table 13-26.

Table 13-26 OracleClob Instance Properties

| Properties                                      | Description                                                                                                  |
|:------------------------------------------------|:-------------------------------------------------------------------------------------------------------------|
| [CanRead](ClobCanRead.md)                       | Indicates whether or not the LOB stream can be read                                                          |
| [CanSeek](ClobCanSeek.md)                       | Indicates whether or not forward and backward seek operations can be performed                               |
| [CanWrite](ClobCanWrite.md)                     | Indicates whether or not the LOB stream can be written                                                       |
| [Connection](ClobConnection.md)                 | Indicates the `OracleConnection` that is used to retrieve and write `CLOB` data                              |
| [IsEmpty](ClobIsEmpty.md)                       | Indicates whether the `CLOB` is `empty` or not                                                               |
| [IsInChunkWriteMode](ClobIsInChunkWriteMode.md) | Indicates whether or not the `CLOB` has been opened                                                          |
| [IsNClob](ClobIsNClob.md)                       | Indicates whether or not the `OracleClob` object represents an `NCLOB`.                                      |
| [IsNull](ClobIsNull.md)                         | Indicates whether or not the current instance has a null value                                               |
| [IsTemporary](ClobIsTemporary.md)               | Indicates whether or not the current instance is bound to a temporary `CLOB`                                 |
| [Length](ClobLength.md)                         | Indicates the size of the `CLOB` data in bytes                                                               |
| [OptimumChunkSize](ClobOptimumChunkSize.md)     | Indicates the minimum number of bytes to retrieve or send from the database during a read or write operation |
| [Position](ClobPosition.md)                     | Indicates the current read or write position in the LOB stream in bytes                                      |
| [Value](ClobValue.md)                           | Returns the data, starting from the first character in the `CLOB` or `NCLOB`, as a string                    |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
