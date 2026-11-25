This instance property specifies the duration, in seconds, for which an enqueued message is available for dequeuing.

### Declaration

    // C#
    public int Expiration {get;set;}

### Property Value

An `integer` that specifies the number of seconds an enqueued message is available for dequeuing.

### Exceptions

`ArgumentException` - The value specified is less than -1.

### Remarks

The value specified is an offset from the value specified in the `Delay` property.

The following are valid values for the property:

- Positive integer - Indicates the expiration in seconds.

- `-1` - Indicates that the message never expires.

The default value is `-1`. When a message expires, the message moves from the `READY` state to the `EXPIRED` state.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
