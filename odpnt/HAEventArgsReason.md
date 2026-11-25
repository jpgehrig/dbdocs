This property specifies reason for which the HA event was sent by the server.

### Declaration

    // C#
    public string Reason {get;}

### Property Value

The reason the HA Event was triggered. Possible values include `Data_Guard_Failover`, `Failure`, `Dependency`, `User`, `Autostart`, and `Restart`.

The value `User` is indicative of a planned outage. All other values are indicative of an unplanned outage.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- [OracleHAEventArgs Members](HAEventArgsMembers.md)

- "[HAEvent](ConnectionHAEvent.md)"
