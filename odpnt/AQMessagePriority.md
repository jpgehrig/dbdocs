This instance property specifies the priority of the message.

### Declaration

    // C#
    public int Priority {get;set;}

### Property Value

An `integer` that specifies the priority of the message.

### Remarks

The default value is 0. In order to take effect, this property must be set prior to enqueuing the message.

Smaller values indicate higher priority for the message. Negative values may also be used.

The priority of an enqueued message is useful for priority-based dequeuing.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
