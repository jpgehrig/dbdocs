This static field indicates the address that the notification listener listens on, for database notifications.

### Declaration

    // C#
    public static string Address{get; set}

### Property Value

A `string` value that represents the address that listens for the database notifications.

If the address is not set, then `OracleConfiguration.DBNotificationAddress` will be used if set. If `OracleDependency.Address` is explicitly set to `string.Empty` or `null`, then the hostname will be used.

### Remarks

This property allows specifying a particular IPv4 or IPv6 address to use, such as the case with a machine that contains multiple network cards. The address can be set to any valid hostname, IPv4, or IPv6 address, which is associated with the machine on which the ODP.NET application is running on, which will be listening for notifications.

The address specified by the `OracleDependency.Address` static field is used by the notification listener that runs within the same application domain as ODP.NET. This address receives Continuous Query Notifications from the database. One notification listener is capable of listening to all Continuous Query Notifications and therefore, only one notification listener is created for each application domain.

The notification listener is created when a command associated with an `OracleDependency` object is executed for the first time during the application domain lifetime. The address specified for the `OracleDependency.Address` static field is used by the listener for its lifetime. The `OracleDependency.Address` static field can be changed after the creation of the notification listener, but doing so does not affect the actual address that the notification listener listens on.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
