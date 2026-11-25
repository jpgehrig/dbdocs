`OracleBlob` instance properties are listed in Table 13-17.

Table 13-17 OracleBlob Instance Properties

| Properties                                      | Description                                                                                                                      |
|:------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| [CanRead](BlobCanRead.md)                       | Indicates whether or not the LOB stream can be read                                                                              |
| [CanSeek](BlobCanSeek.md)                       | Indicates whether or not forward and backward seek operations be performed                                                       |
| [CanWrite](BlobCanWrite.md)                     | Indicates whether or not the LOB object supports writing                                                                         |
| [Connection](BlobConnection.md)                 | Indicates the `OracleConnection` that is used to retrieve and write `BLOB` data                                                  |
| [IsEmpty](BlobIsEmpty.md)                       | Indicates whether the `BLOB` is empty or not                                                                                     |
| [IsInChunkWriteMode](BlobIsInChunkWriteMode.md) | Indicates whether or not the `BLOB` has been opened to defer index updates                                                       |
| [IsNull](BlobIsNull.md)                         | Indicates whether or not the current instance has a null value                                                                   |
| [IsTemporary](BlobIsTemporary.md)               | Indicates whether or not the current instance is bound to a temporary `BLOB`                                                     |
| [Length](BlobLength.md)                         | Indicates the size of the `BLOB` data                                                                                            |
| [OptimumChunkSize](BlobOptimumChunkSize.md)     | Indicates the optimal data buffer length (or multiples thereof) that read and write operations should use to improve performance |
| [Position](BlobPosition.md)                     | Indicates the current read or write position in the LOB stream                                                                   |
| [Value](BlobValue.md)                           | Returns the data, starting from the first byte in `BLOB`, as a byte array                                                        |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
