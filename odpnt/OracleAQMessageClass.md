An `OracleAQMessage` object represents a message to be enqueued and dequeued.

### Class Inheritance

`System.Object`

`  OracleAQMessage`

### Declaration

    // C#
    public sealed class OracleAQMessage

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

An `OracleAQMessage` object consists of control information (metadata) and Payload (data). The control information is exposed by various properties on the `OracleAQMessage` object and is used by Oracle Database Advanced Queuing to manage messages. The payload is the information stored in the queue.

**Note:**

An instance of `OracleAQMessage` cannot be re-used across multiple operations of `OracleAQQueue` public method [Enqueue](AQQueueEnqueueOverloads.md)() or [EnqueueArray](AQQueueEnqueueArrayOverloads.md)(), if the payload is an `XmlReader`. This is a direct consequence of the forward-only semantics of the `XmlReader`, as an [Enqueue](AQQueueEnqueueOverloads.md)() or [EnqueueArray](AQQueueEnqueueArrayOverloads.md)() operation internally invokes a read operation on the `XmlReader` to extract the data to be enqueued.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Members](AQMessageMembers.md)

- [OracleAQMessage Constructors](AQMessageConstructors.md)

- [OracleAQMessage Properties](AQMessageProperties.md)
