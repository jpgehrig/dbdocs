This instance property specifies the consumer name for which to dequeue the message.

### Declaration

    // C#
    public string ConsumerName {get;set;}

### Property Value

A `string`.

### Remarks

The `ConsumerName` property only accesses those messages that match the consumer name. If a queue is not set up for multiple consumers, then this field should be set to `null`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
