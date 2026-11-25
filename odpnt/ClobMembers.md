`OracleClob` members are listed in the following tables.

### OracleClob Constructors

`OracleClob` constructors are listed in Table 13-19.

Table 13-19 OracleClob Constructors

| Constructor                             | Description                                                                            |
|:----------------------------------------|:---------------------------------------------------------------------------------------|
| [OracleClob Constructors](ClobCtors.md) | Creates an instance of the `OracleClob` class bound to a temporary `CLOB` (Overloaded) |

### OracleClob Static Fields

`OracleClob` static fields are listed in Table 13-20.

Table 13-20 OracleClob Static Fields

| Field                     | Description                                                                                  |
|:--------------------------|:---------------------------------------------------------------------------------------------|
| [MaxSize](ClobMaxSize.md) | Holds the maximum number of bytes a `CLOB` can hold, which is 4,294,967,295 (2^32 - 1) bytes |
| [Null](ClobNull.md)       | Represents a null value that can be assigned to the value of an `OracleClob` instance        |

### OracleClob Static Methods

`OracleClob` static methods are listed in Table 13-21.

Table 13-21 OracleClob Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleClob Instance Properties

`OracleClob` instance properties are listed in Table 13-22.

Table 13-22 OracleClob Instance Properties

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

### OracleClob Instance Methods

The `OracleClob` instance methods are listed in Table 13-23.

Table 13-23 OracleClob Instance Methods

| Methods                                   | Description                                                                           |
|:------------------------------------------|:--------------------------------------------------------------------------------------|
| [Append](ClobAppendOverloads.md)          | Appends data to the current `OracleClob` instance (Overloaded)                        |
| [BeginChunkWrite](ClobBeginChunkWrite.md) | Opens the `CLOB`                                                                      |
| `BeginRead`                               | Inherited from `System.IO.Stream`                                                     |
| `BeginWrite`                              | Inherited from `System.IO.Stream`                                                     |
| [Clone](ClobClone.md)                     | Creates a copy of an `OracleClob` object                                              |
| [Close](ClobClose.md)                     | Closes the current stream and releases resources associated with it                   |
| [Compare](ClobCompare.md)                 | Compares data referenced by the current instance to that of the supplied object       |
| [CopyTo](ClobCopyToOverloads.md)          | Copies the data to an `OracleClob` (Overloaded)                                       |
| `CreateObjRef`                            | Inherited from `System.MarshalByRefObject`                                            |
| [Dispose](ClobDispose.md)                 | Releases resources allocated by this object                                           |
| [EndChunkWrite](ClobEndChunkWrite.md)     | Closes the `CLOB` referenced by the current `OracleClob` instance                     |
| `EndRead`                                 | Inherited from `System.IO.Stream`                                                     |
| `EndWrite`                                | Inherited from `System.IO.Stream`                                                     |
| `Equals`                                  | Inherited from `System.Object` (Overloaded)                                           |
| [Erase](ClobEraseOverloads.md)            | Erases the specified `amount` of data (Overloaded)                                    |
| [Flush](ClobFlush.md)                     | Not supported                                                                         |
| [GetHashCode](ClobGetHashCode.md)         | Returns a hash code for the current instance                                          |
| `GetLifetimeService `                     | Inherited from `System.MarshalByRefObject`                                            |
| `GetType`                                 | Inherited from `System.Object`                                                        |
| `InitializeLifetimeService`               | Inherited from `System.MarshalByRefObject`                                            |
| [IsEqual](ClobIsEqual.md)                 | Compares the LOB data referenced by two `OracleClob`s                                 |
| [Read](ClobReadOverloads.md)              | Reads from the current instance (Overloaded)                                          |
| `ReadByte`                                | Inherited from `System.IO.Stream`                                                     |
| [Search](ClobSearchOverloads.md)          | Searches for a character pattern in the current instance of `OracleClob` (Overloaded) |
| [Seek](ClobSeek.md)                       | Sets the position in the current LOB stream                                           |
| [SetLength](ClobSetLength.md)             | Trims or truncates the `CLOB` value                                                   |
| `ToString`                                | Inherited from `System.Object`                                                        |
| [Write](ClobWriteOverloads.md)            | Writes the provided `buffer` into the `OracleClob` (Overloaded)                       |
| `WriteByte`                               | Inherited from `System.IO.Stream`                                                     |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)
