`OracleBFile` instance properties are listed in Table 13-8.

Table 13-8 OracleBFile Instance Properties

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

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
