This instance property returns the message identifier.

### Declaration

    // C#
    public byte[] MessageId {get;}

### Property Value

A `byte[]` that specifies the message identifier.

### Remarks

This property is available after an enqueue or dequeue operation. Dequeued buffered messages have a `null` value for `MessageId`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
