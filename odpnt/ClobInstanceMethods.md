The `OracleClob` instance methods are listed in Table 13-27.

Table 13-27 OracleClob Instance Methods

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

- [OracleClob Members](ClobMembers.md)
