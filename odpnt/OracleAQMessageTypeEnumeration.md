The `OracleAQMessageType` enumeration type specifies the message payload type.

Table 12-34 lists all the `OracleAQMessageType` enumeration values with a description of each enumerated value.

Table 12-34 OracleAQMessageType Members

| Member Name | Description                                                                                                                                                                                                                                                                                        |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Raw`       | Indicates the Raw message type.<br>The data type of the payload must be either `OracleBinary` or `byte[]` to enqueue the message.                                                                                                                                                                  |
| `Udt`       | Indicates the Oracle UDT message type.<br>The ODP.NET AQ implementation currently does not support user defined types with LOB attributes. It also does not support other variants of user defined types such as VARRAY and nested tables, as Oracle Database AQ does not support them inherently. |
| `Xml`       | Indicates the XML message type.<br>The data type of the payload must be `OracleXmlType`, `XmlReader`, or `String` in order to enqueue the message. If the data type is `String`, it must be well-formed XML, else an exception is raised when enqueuing the message.                               |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleAQQueue Class](OracleAQQueueClass.md)"

- "[OracleAQQueue Constructors](AQQueueConstructors.md)"

- "[MessageType](AQQueueMessageType.md)"
