`OracleAQQueue` constructors create new instances of the `OracleAQQueue` class.

### Overload List:

- [OracleAQQueue(string)](AQQueueCtor1.md)

  This constructor takes a queue name to initialize a queue object.

- [OracleAQQueue(string, OracleConnection)](AQQueueCtor2.md)

  This constructor takes a queue name and connection to initialize a queue object. The connection does not need be open during the queue object construction.

- [OracleAQQueue(string, OracleConnection, OracleAQMessageType)](AQQueueCtor3.md)

  This constructor takes a queue name, connection, and message type enumeration to initialize a queue object.

- [OracleAQQueue(string, OracleConnection, OracleAQMessageType, string)](AQQueueCtor4.md)

  This constructor takes a queue name, connection, message type enumeration, and UDT type name to initialize a queue object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
