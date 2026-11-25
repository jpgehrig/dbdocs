This event is triggered when the connection state changes.

### Declaration

    // C#
    public override event StateChangeEventHandler StateChange;

### Event Data

The event handler receives a `StateChangeEventArgs` object which exposes the following properties containing information about the event.

- `CurrentState`

  The new state of the connection.

- `OriginalState`

  The original state of the connection.

### Remarks

The `StateChange` event is raised after a connection changes state, whenever an explicit call is made to `Open`, `Close` or `Dispose`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- Microsoft ADO.NET documentation for a description of `StateChangeEventHandler`
