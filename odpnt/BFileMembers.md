`OracleBFile` members are listed in the following tables.

### OracleBFile Constructors

`OracleBFile` constructors are listed in Table 13-1.

Table 13-1 OracleBFile Constructors

| Constructor                               | Description                                                 |
|:------------------------------------------|:------------------------------------------------------------|
| [OracleBFile Constructors](BFileCtors.md) | Creates an instance of the `OracleBFile` class (Overloaded) |

### OracleBFile Static Fields

`OracleBFile` static fields are listed in Table 13-2.

Table 13-2 OracleBFile Static Fields

| Field                      | Description                                                                                                    |
|:---------------------------|:---------------------------------------------------------------------------------------------------------------|
| [MaxSize](BFileMaxSize.md) | The static field holds the maximum number of bytes a `BFILE` can hold, which is 4,294,967,295 (2^32 - 1) bytes |
| [Null](BFileNull.md)       | Represents a null value that can be assigned to the value of an `OracleBFile` instance                         |

### OracleBFile Static Methods

`OracleBFile` static methods are listed in Table 13-3.

Table 13-3 OracleBFile Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleBFile Instance Properties

`OracleBFile` instance properties are listed in Table 13-4.

Table 13-4 OracleBFile Instance Properties

| Properties                             | Description                                                                    |
|:---------------------------------------|:-------------------------------------------------------------------------------|
| [CanRead](BFileCanRead.md)             | Indicates whether or not the LOB stream can be read                            |
| [CanSeek](BFileCanSeek.md)             | Indicates whether or not forward and backward seek operations can be performed |
| [CanWrite](BFileCanWrite.md)           | Indicates whether or not the LOB object supports writing                       |
| [Connection](BFileConnection.md)       | Indicates the connection used to read from a `BFILE`                           |
| [DirectoryName](BFileDirectoryName.md) | Indicates the directory alias of the `BFILE`                                   |
| [FileExists](BFileFileExists.md)       | Indicates whether or not the specified `BFILE` exists                          |
| [FileName](BFileFileName.md)           | Indicates the name of the `BFILE`                                              |
| [IsEmpty](BFileIsEmpty.md)             | Indicates whether the `BFILE` is empty or not                                  |
| [IsNull](BFileIsNull.md)               | Indicates whether or not the current instance has a null value                 |
| [IsOpen](BFileIsOpen.md)               | Indicates whether the `BFILE` has been opened by this instance or not          |
| [Length](BFileLength.md)               | Indicates the size of the `BFILE` data in bytes                                |
| [Position](BFilePosition.md)           | Indicates the current read position in the LOB stream                          |
| [Value](BFileValue.md)                 | Returns the data, starting from the first byte in `BFILE`, as a byte array     |

### OracleBFile Instance Methods

`OracleBFile` instance methods are listed in Table 13-5.

Table 13-5 OracleBFile Instance Methods

| Methods                           | Description                                                                                  |
|:----------------------------------|:---------------------------------------------------------------------------------------------|
| `BeginRead`                       | Inherited from `System.IO.Stream`                                                            |
| `BeginWrite`                      | Not Supported                                                                                |
| [Clone](BFileClone.md)            | Creates a copy of an `OracleBFile` object                                                    |
| [Close](BFileClose.md)            | Closes the current stream and releases any resources associated with the stream              |
| [CloseFile](BFileCloseFile.md)    | Closes the `BFILE` referenced by the current `BFILE` instance                                |
| [Compare](BFileCompare.md)        | Compares data referenced by the two `OracleBFile`s                                           |
| `CreateObjRef`                    | Inherited from `System.MarshalByRefObject`                                                   |
| [CopyTo](BFileCopyToOverloads.md) | Copies data as specified (Overloaded)                                                        |
| [Dispose](BFileDispose.md)        | Releases resources allocated by this object                                                  |
| `EndRead`                         | Inherited from `System.IO.Stream`                                                            |
| `EndWrite`                        | Not Supported                                                                                |
| `Equals`                          | Inherited from `System.Object` (Overloaded)                                                  |
| [Flush](BFileFlush.md)            | Not Supported                                                                                |
| [FlushAsync](BFileFlushAsync.md)  | Not Supported                                                                                |
| `GetHashCode`                     | Inherited from `System.Object`                                                               |
| `GetLifetimeService `             | Inherited from `System.MarshalByRefObject`                                                   |
| `GetType`                         | Inherited from `System.Object`                                                               |
| `InitializeLifetimeService`       | Inherited from `System.MarshalByRefObject`                                                   |
| [IsEqual](BFileIsEqual.md)        | Compares the LOB references                                                                  |
| [OpenFile](BFileOpenFile.md)      | Opens the `BFILE` specified by the `FileName` and `DirectoryName`                            |
| [Read](BFileRead.md)              | Reads a specified amount of bytes from the `OracleBFile` instance and populates the `buffer` |
| `ReadByte`                        | Inherited from `System.IO.Stream`                                                            |
| [Search](BFileSearch.md)          | Searches for a binary pattern in the current instance of an `OracleBFile`                    |
| [Seek](BFileSeek.md)              | Sets the position on the current LOB stream                                                  |
| [SetLength](BFileSetLength.md)    | Not Supported                                                                                |
| `ToString`                        | Inherited from `System.Object`                                                               |
| [Write](BFileWrite.md)            | Not Supported                                                                                |
| `WriteByte`                       | Not Supported                                                                                |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- OracleBFile Members
