This static field indicates the port number that the notification listener listens on, for database notifications.

### Declaration

    // C#
    public static int Port{get; set}

### Property Value

An `int` value that represents the number of the port that listens for the database notifications. If the port number is set to `-1`, a random port number is assigned for the listener when the listener is started. Otherwise, the specified port number is used to start the listener.

### Exceptions

`ArgumentOutOfRangeException` - The port number is set to a negative value.

`InvalidOperationException` - The port number is being changed after the listener has started.

### Remarks

The port number specified by the `OracleDependency.Port` static field is used by the notification listener that runs within the same application domain as ODP.NET. This port number receives Continuous Query Notifications from the database. One notification listener is capable of listening to all Continuous Query Notifications and therefore, only one notification listener is created for each application domain.

The notification listener is created when a command associated with an `OracleDependency` object is executed for the first time during the application domain lifetime. The port number specified for the `OracleDependency.Port` static field is used by the listener for its lifetime. The `OracleDependency.Port` static field can be changed after the creation of the notification listener, but doing so does not affect the actual port number that the notification listener listens on.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
