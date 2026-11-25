This instance property specifies the identification for the message.

### Declaration

    // C#
    public string Correlation {get;}

### Property Value

A `string` that specifies the identification for the message.

### Remarks

This property specifies the correlation of the message for which the notification is raised. The consumer can then use this identification to dequeue specific messages by setting the "[Correlation](AQDequeueOptionsCorrelation.md)" property of the `OracleAQDequeueOptions` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessageAvailableEventArgs Class](OracleAQMessageAvailableEventArgsClass.md)

- [OracleAQMessageAvailableEventArgs Members](AQMessageAvailableEventArgsMembers.md)

- "[Correlation](AQDequeueOptionsCorrelation.md)"
