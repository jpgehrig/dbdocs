This instance property specifies the duration, in seconds, after which an enqueued message is available for dequeuing.

### Declaration

    // C#
    public int Delay {get;set;}

### Property Value

An `integer` that indicates the number of seconds after which an enqueued message is available for dequeuing.

### Exceptions

`ArgumentException` - The value specified is less than 0.

### Remarks

This property delays the immediate consumption of an enqueued message. The following are valid values for this property:

- Positive integer - Indicates the delay in seconds.

- 0 - indicates that the message is immediately available for dequeuing.

The default value is 0. The `Delay` property is not supported with buffered messaging.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
