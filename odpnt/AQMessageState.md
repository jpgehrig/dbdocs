This instance property specifies the state of the message at the time of dequeue.

### Declaration

    // C#
    public OracleAQMessageState State {get;}

### Property Value

An `OracleAQMessageState` enumerated value.

### Remarks

This property is available after the message is dequeued.

The state of buffered messages dequeued by specifying `Correlation` under dequeue options is always `OracleAQMessageState.Ready`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
