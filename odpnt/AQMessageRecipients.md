This instance property specifies the list of recipients that overrides the default queue subscribers.

### Declaration

    // C#
    public OracleAQAgent[] Recipients {get; set}

### Property Value

An `OracleAQAgent[]`.

### Remarks

This recipient list is valid only for messages being enqueued to multiconsumer queues. The list of recipients is not returned with the message at the time of dequeuing.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
