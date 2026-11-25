This instance property specifies the message identifier of the message to be dequeued.

### Declaration

    // C#
    public byte[] MessageId {get;set;}

### Property Value

A `byte[ ].`

### Remarks

The dequeue operation succeeds only if the message ID of the message being dequeued matches with the message ID specified.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
