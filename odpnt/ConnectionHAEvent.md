This event is triggered when an HA event occurs.

### Declaration

    // C#
    public static event OracleHAEventHandler HAEvent;

### Event Data

The event handler receives an `OracleHAEventArgs` object which exposes the following properties containing information about the event.

- `Source`

  Indicates the source of the event.

- `Status`

  Indicates the status of the event.

- `DatabaseName`

  Indicates the database name affected by this event.

- `DatabaseDomainName`

  Indicates the database domain name affected by this event.

- `HostName`

  Indicates the host name affected by this event.

- `InstanceName`

  Indicates the instance name affected by this event.

- `ServiceName`

  Indicates the service name affected by this event.

- `Time`

  Indicates the time of the event.

### Remarks

The `HAEvent` is static, which means that any HA Events that happen within the application domain can trigger this event. Note that in order to receive HA event notifications, `OracleConnection` objects that establish connections within the application domain must have `"ha events=true"` in the application. Otherwise, the application never receives any HA Events.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- "[OracleHAEventArgs Properties](HAEventArgsProperties.md)"

- "[OracleHAEventHandler Delegate](OracleHAEventHandlerDelegate.md)"
