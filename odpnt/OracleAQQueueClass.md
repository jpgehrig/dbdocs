An `OracleAQQueue` object represents a queue.

### Class Inheritance

`System.Object`

`  OracleAQQueue`

### Declaration

    // C#
    public class OracleAQQueue : IDisposable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

A queue is a repository of messages and may either be a user queue, or an exception queue. A user queue is for normal message processing. A message is moved from a user queue to an exception queue if it cannot be retrieved and processed for some reason.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Members](AQQueueMembers.md)

- [OracleAQQueue Constructors](AQQueueConstructors.md)

- [OracleAQQueue Static Methods](AQQueueStaticMethods.md)

- [OracleAQQueue Properties](AQQueueProperties.md)

- [OracleAQQueue Public Methods](AQQueuePublicMethods.md)

- [OracleAQQueue Events](AQQueueEvents.md)
