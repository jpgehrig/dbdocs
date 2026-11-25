`OracleBlob` instance methods are listed in Table 13-18.

Table 13-18 OracleBlob Instance Methods

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

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
