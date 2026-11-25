This instance property specifies the type of queue table associated with this queue.

### Declaration

    // C#
    public OracleAQMessageType MessageType {get; set;}

### Property Value

An `OracleAQMessageType` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The type value specified is invalid.

`ObjectDisposedException` - The object is already disposed.

### Remarks

The `MessageType` property also dictates the type of message payloads that are enqueued or dequeued from the queue. It is possible to enqueue a variety of payloads depending on the `MessageType`.

Table 12-27 lists the allowed payload types for various message types.

Table 12-27 Message Types and Payloads

| OracleAQQueue.MessageType | Allowed OracleAQMessage.Payload type to Enqueue                                    |
|:--------------------------|:-----------------------------------------------------------------------------------|
| `OracleAQMessageType.Raw` | `OracleBinary`, `byte[]`                                                           |
| `OracleAQMessageType.Xml` | `OracleXmlType`, `XmlReader`, `String` (well-formed XML, else exception is raised) |
| `OracleAQMessageType.UDT` | `UDT` Custom Object                                                                |

Table 12-28 lists the payload types for dequeued messages.

Table 12-28 Payload Types for Dequeued Messages

| OracleAQQueue.MessageType | DequeueOptions.ProviderSpecificType | OracleAQMessage.Payload of dequeued message |
|:--------------------------|:------------------------------------|:--------------------------------------------|
| `OracleAQMessageType.Xml` | `true`                              | `OracleXmlType`                             |
| `OracleAQMessageType.Xml` | `false`                             | `XmlReader`                                 |
| `OracleAQMessageType.Raw` | `true`                              | `OracleBinary`                              |
| `OracleAQMessageType.Raw` | `false`                             | `Byte[]`                                    |
| `OracleAQMessageType.UDT` | N.A.                                | `UDT` Custom Object                         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
