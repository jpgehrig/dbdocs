This event is triggered when an Oracle failover occurs.

### Declaration

    // C#
    public event OracleFailoverEventHandler Failover;

### Event Data

The event handler receives an `OracleFailoverEventArgs` object which exposes the following properties containing information about the event.

- `FailoverType`

  Indicates the type of the failover.

- `FailoverEvent`

  Indicates the state of the failover.

### Remarks

The `Failover` event is raised when a connection to an Oracle instance is unexpectedly severed. The client should create an `OracleFailoverEventHandler` delegate to listen to this event.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[OracleFailoverEventArgs Properties](FailoverEventArgsProperties.md)"

- "[OracleFailoverEventHandler Delegate](OracleFailoverEventHandlerDelegate.md)"
