An integer value indicating the maximum time period in seconds that ODP.NET waits for the service to drain connections from the database service from when the Fast Application Notification `SERVICE DOWN` event is received.

### Declaration

    // C#
    public int DrainTimeout {get;}

### Property Value

The number of seconds allowed for resource draining to be completed during a planned outage

### Remarks

When connecting to Oracle Data Guard in Oracle Database 12c Release 2 or later, database administrators can set their own timeout value, `drain_timeout`, to indicate the number of seconds allowed for resource draining to be completed during a planned outage. The `drain_timeout` value populates `OracleHAEventArgs.DrainTimeout.drain_timeout` can be used by the ODP.NET `ServiceRelocationConnectionTimeout` to wait for a service to be relocated before attempting new connections.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- [OracleHAEventArgs Members](HAEventArgsMembers.md)

- "[HAEvent](ConnectionHAEvent.md)"

- [`ServiceRelocationConnectionTimeout`](InstallManagedConfig.md)
