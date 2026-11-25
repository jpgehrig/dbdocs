This instance property specifies an identification for the message.

### Declaration

    // C#
    public string Correlation {get;set;}

### Property Value

A `string` that specifies the identification for the message.

### Remarks

The producer of a message can set this property at the time of enqueuing. The consumer can then use this identification to dequeue specific messages by setting the `Correlation` property of an `OracleAQDequeueOptions` object. For more information regarding dequeuing messages based on `Correlation`, refer to "[Correlation](AQDequeueOptionsCorrelation.md)" under the `OracleAQDequeueOptions` class.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)

- "[Correlation](AQDequeueOptionsCorrelation.md)"
