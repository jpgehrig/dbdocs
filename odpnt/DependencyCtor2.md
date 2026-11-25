This constructor creates an instance of the `OracleDependency` class and binds it to an `OracleCommand` instance.

### Declaration

    // C#
    public OracleDependency (OracleCommand cmd)

### Parameters

- `cmd`

  The command that the `OracleDependecy` object binds to.

### Exceptions

`ArgumentNullException` - The `cmd` parameter is null.

`InvalidOperationException` - The specified `OracleCommand` instance already contains a notification request.

### Remarks

When this `OracleDependency` constructor binds the `OracleCommand` instance to an `OracleDependency` instance, it causes the creation of an `OracleNotificationRequest` instance and then sets that `OracleNotificationRequest` instance to the `OracleCommand.``Notification` property.

The Continuous Query Notification is registered with the database, when the command is executed. Any of the command execution methods (for example, `ExecuteNonQuery`, `ExecuteReader`, and so on) will register the notification request. An `OracleDependency` may be bound to more than one `OracleCommand`. When one of these `OracleCommand` object statements is executed, the statement is registered with the associated `OracleCommand`. Although the registration happens on each `OracleCommand` separately, one `OracleDependency` can be responsible for detecting and sending notifications that occur for all `OracleCommand` objects that the `OracleDependency` is associated with. The `OnChangeEventArgs` that is passed to the application for the `OnChange` event provides information on what has changed in the database.

The `OracleNotificationRequest` instance that is created by this constructor has the following default property values:

- `IsNotifiedOnce` is set to the value `True`.

- `Timeout` is set to 50,000 seconds.

- `IsPersistent` is set to the value `False`, that is, the invalidation message is not persistent, but is stored in an in-memory queue before delivery.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
