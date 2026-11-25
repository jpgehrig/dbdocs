This instance property returns the number of attempts that have been made to dequeue the message.

### Declaration

    // C#
    public int DequeueAttempts {get;}

### Property Value

An `integer` that indicates the number of dequeue attempts.

### Remarks

This property is available in an `OracleAQMessage` after the message has been dequeued from a queue.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
