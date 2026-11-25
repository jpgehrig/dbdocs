This instance property specifies the transaction group for the dequeued message.

### Declaration

    // C#
    public string TransactionGroup {get;}

### Property Value

A `string` that specifies the transaction group.

### Remarks

This property is set only after the call to `DequeueArray`. This property is supported only when using Oracle Database 10g database or higher.

Messages belonging to one queue can be grouped to form a set that can only be consumed by one user at a time. This requires that the queue be created in a queue table that is enabled for message grouping. All messages belonging to a group must be created in the same transaction. Also, all messages created in one transaction belong to the same group.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
