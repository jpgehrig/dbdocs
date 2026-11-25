This instance property specifies the expected delivery mode of the message being dequeued.

### Declaration

    // C#
    public OracleAQMessageDeliveryMode DeliveryMode {get;set;}

### Property Value

An `OracleAQMessageDeliveryMode` enumerated value.

### Remarks

This property specifies the type of messages to be dequeued. It can be set to dequeue either persistent or buffered messages, or both from a queue. The following values are valid:

- `OracleAQMessageDeliveryMode.Persistent`

- `OracleAQMessageDeliveryMode.Buffered`

- `OracleAQMessageDeliveryMode.PersistentOrBuffered`

The default value is `OracleAQMessageDeliveryMode.Persistent`.

Buffered messaging is supported in all queue tables created with a database compatibility level of 8.1 or higher.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
