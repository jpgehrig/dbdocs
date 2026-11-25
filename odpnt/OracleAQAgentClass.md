The `OracleAQAgent` class represents agents that may be senders or recipients of a message.

### Class Inheritance

`System.Object`

`  OracleAQAgent`

### Declaration

    // C#
    public sealed class OracleAQAgent

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

An agent may be a consumer, another queue, or a consumer of another queue. The queue may be either local or remote. A remote queue is specified through a database link.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQAgent Members](AQAgentMembers.md)

- [OracleAQAgent Constructors](AQAgentConstructors.md)

- [OracleAQAgent Properties](AQAgentProperties.md)
