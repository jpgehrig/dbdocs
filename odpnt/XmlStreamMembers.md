`OracleXmlStream` members are listed in the following tables.

### OracleXmlStream Constructors

The `OracleXmlStream` constructors are listed in Table 7-12.

Table 7-12 OracleXmlStream Constructors

| Constructor                                      | Description                                                                                                                              |
|:-------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| [OracleXmlStream Constructor](XmlStreamCtors.md) | Creates an instance of an `OracleXmlStream` object which provides a `Stream` representation of the XML data stored in an `OracleXmlType` |

### OracleXmlStream Static Methods

The `OracleXmlStream` static methods are listed in Table 7-13.

Table 7-13 OracleXmlStream Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleXmlStream Instance Properties

The `OracleXmlStream` instance properties are listed in Table 7-14.

Table 7-14 OracleXmlStream Instance Properties

| Properties                           | Description                                                                       |
|:-------------------------------------|:----------------------------------------------------------------------------------|
| [CanRead](XmlStreamCanRead.md)       | Indicates whether or not the XML stream can be read                               |
| [CanSeek](XmlStreamCanSeek.md)       | Indicates whether or not forward and backward seek operation can be performed     |
| [CanWrite](XmlStreamCanWrite.md)     | `OracleXmlStream` is a sequential read only, forward only stream.                 |
| [Connection](XmlStreamConnection.md) | Indicates the `OracleConnection` that is used to retrieve the XML data            |
| [Length](XmlStreamLength.md)         | Indicates the number of bytes in the XML stream                                   |
| [Position](XmlStreamPosition.md)     | Gets or sets the byte position within the stream                                  |
| [Value](XmlStreamValue.md)           | Returns the XML data, starting from the first character in the stream as a string |

### OracleXmlStream Instance Methods

The `OracleXmlStream` instance methods are listed in Table 7-15.

Table 7-15 OracleXmlStream Instance Methods

| Methods                            | Description                                                                                           |
|:-----------------------------------|:------------------------------------------------------------------------------------------------------|
| `BeginRead`                        | Inherited from `System.IO.Stream`                                                                     |
| `BeginWrite`                       | Inherited from `System.IO.Stream`                                                                     |
| [Clone](XmlStreamClone.md)         | Creates a copy of an `OracleXmlStream` object                                                         |
| [Close](XmlStream.md)              | Closes the current stream and releases any resources associated with it                               |
| [Dispose](XmlStreamDispose.md)     | Releases resources allocated by this object                                                           |
| `EndRead`                          | Inherited from `System.IO.Stream`                                                                     |
| `EndWrite`                         | Inherited from `System.IO.Stream`                                                                     |
| `Equals`                           | Inherited from `System.Object`                                                                        |
| [Flush](XmlStreamFlush.md)         | Not Supported                                                                                         |
| `GetHashCode`                      | Inherited from `System.Object`                                                                        |
| `GetLifetimeService`               | Inherited from `System.MarshalByRefObject`                                                            |
| `GetType`                          | Inherited from `System.Object`                                                                        |
| `InitializeLifetimeService`        | Inherited from `System.MarshalByRefObject`                                                            |
| [Read](XmlStreamReadOverloads.md)  | Reads a specified amount from the current stream instance and populates the array buffer (Overloaded) |
| `ReadByte`                         | Inherited from `System.IO.Stream`                                                                     |
| [Seek](XmlStreamSeek.md)           | Sets the position within the current stream and returns the new position within the current stream    |
| [SetLength](XmlStreamSetLength.md) | Not Supported                                                                                         |
| `ToString`                         | Inherited from `System.Object`                                                                        |
| [Write](XmlStreamWrite.md)         | Not Supported                                                                                         |
| `WriteByte`                        | Not Supported                                                                                         |
| [WriteLine](XmlStreamWriteLine.md) | Not Supported                                                                                         |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)
