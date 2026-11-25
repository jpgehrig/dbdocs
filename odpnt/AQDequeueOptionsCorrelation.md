This instance property specifies the correlation identifier of the message to be dequeued.

### Declaration

    // C#
    public string Correlation {get;set;}

### Property Value

A `string`.

### Remarks

This property specifies the identification of the message to be dequeued. Special pattern matching characters, such as the percent sign (`%`) and the underscore (`_`) can be used. If more than one message satisfies the pattern, then the order of dequeuing is undetermined.

The maximum length of `Correlation` is 128.

`MessageId` and `Correlation` are two independent identifiers. While `MessageId` is unique for a message, a group of messages can be assigned the same `Correlation`. Also, pattern matching is possible only with `Correlation`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
