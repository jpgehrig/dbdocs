`OracleBlob` members are listed in the following tables.

### OracleBlob Constructors

`OracleBlob` constructors are listed in Table 13-10.

Table 13-10 OracleBlob Constructors

| Constructor                             | Description                                                |
|:----------------------------------------|:-----------------------------------------------------------|
| [OracleBlob Constructors](BlobCtors.md) | Creates an instance of the `OracleBlob` class (Overloaded) |

### OracleBlob Static Fields

`OracleBlob` static fields are listed in Table 13-11.

Table 13-11 OracleBlob Static Fields

| Field                     | Description                                                                                  |
|:--------------------------|:---------------------------------------------------------------------------------------------|
| [MaxSize](BlobMaxSize.md) | Holds the maximum number of bytes a `BLOB` can hold, which is 4,294,967,295 (2^32 - 1) bytes |
| [Null](BlobNull.md)       | Represents a null value that can be assigned to the value of an `OracleBlob` instance        |

### OracleBlob Static Methods

`OracleBlob` static methods are listed in Table 13-12.

Table 13-12 OracleBlob Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleBlob Instance Properties

`OracleBlob` instance properties are listed in Table 13-13.

Table 13-13 OracleBlob Instance Properties

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

### OracleBlob Instance Methods

`OracleBlob` instance methods are listed in Table 13-14.

Table 13-14 OracleBlob Instance Methods

| Methods                                   | Description                                                                                     |
|:------------------------------------------|:------------------------------------------------------------------------------------------------|
| [Append](BlobAppendOverloads.md)          | Appends the supplied data to the current `OracleBlob` instance (Overloaded)                     |
| [BeginChunkWrite](BlobbeginChunkWrite.md) | Opens the `BLOB`                                                                                |
| `BeginRead`                               | Inherited from `System.IO.Stream`                                                               |
| `BeginWrite`                              | Inherited from `System.IO.Stream`                                                               |
| [Clone](BlobClone.md)                     | Creates a copy of an `OracleBlob` object                                                        |
| [Close](BlobClose.md)                     | Closes the current stream and releases any resources associated with it                         |
| [Compare](BlobCompare.md)                 | Compares data referenced by the current instance and that of the supplied object                |
| [CopyTo](BlobCopyToOverloads.md)          | Copies from the current `OracleBlob` instance to an `OracleBlob` object (Overloaded)            |
| `CreateObjRef`                            | Inherited from `System.MarshalByRefObject`                                                      |
| [Dispose](BlobDispose.md)                 | Releases resources allocated by this `object`                                                   |
| [EndChunkWrite](BlobEndChunkWrite.md)     | Closes the `BLOB` referenced by the current `OracleBlob` instance                               |
| `EndRead`                                 | Inherited from `System.IO.Stream`                                                               |
| `EndWrite`                                | Inherited from `System.IO.Stream`                                                               |
| `Equals`                                  | Inherited from `System.Object` (Overloaded)                                                     |
| [Erase](BlobEraseOverloads.md)            | Erases data (Overloaded)                                                                        |
| [Flush](BlobFlush.md)                     | Not supported                                                                                   |
| `GetHashCode`                             | Inherited from `System.Object`                                                                  |
| `GetLifetimeService `                     | Inherited from `System.MarshalByRefObject`                                                      |
| `GetType`                                 | Inherited from `System.Object`                                                                  |
| `InitializedLifetimeService`              | Inherited from `System.MarshalByRefObject`                                                      |
| [IsEqual](BlobIsEqual.md)                 | Compares the LOB data referenced by the two `OracleBlob`s                                       |
| [Read](BlobRead.md)                       | Reads a specified amount of bytes from the ODP.NET LOB Type instance and populates the `buffer` |
| `ReadByte`                                | Inherited from `System.IO.Stream`                                                               |
| [Search](BlobSearch.md)                   | Searches for a binary pattern in the current instance of an `OracleBlob`                        |
| [Seek](BlobSeek.md)                       | Sets the position in the current LOB stream                                                     |
| [SetLength](BlobSetLength.md)             | Trims or truncates the `BLOB` value to the specified length                                     |
| `ToString`                                | Inherited from `System.Object`                                                                  |
| [Write](BlobWrite.md)                     | Writes the supplied buffer into the `OracleBlob`                                                |
| `WriteByte`                               | Inherited from `System.IO.Stream`                                                               |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- OracleBlob Members
