This instance property specifies the name of the queue that the message should be moved to if it cannot be processed successfully.

### Declaration

    // C#
    public string ExceptionQueue {get;set;}

### Property Value

The name of the queue that a message should be moved to if it cannot be processed successfully. The default value is `null`.

### Remarks

This property specifies the queue that a message should be moved to if the message has expired or if the number of unsuccessful dequeue attempts have exceeded the `max_retries `value for the queue.

If this property is not set or the specified exception queue name does not exist, then the default exception queue associated with the queue table is used.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
