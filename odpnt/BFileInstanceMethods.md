`OracleBFile` instance methods are listed in Table 13-9.

Table 13-9 OracleBFile Instance Methods

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

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
