This constructor creates an instance of the `OracleDependency` class and binds it to the specified `OracleCommand` instance, while specifying whether or not a registration is to be removed upon notification, the timeout value of the notification registration, and the persistence of the notification.

### Declaration

    // C#
    public OracleDependency (OracleCommand cmd, bool isNotifiedOnce, long timeout,
      bool isPersistent)

### Parameters

- `cmd`

  The command associated with the Continuous Query Notification request.

- `isNotifiedOnce`

  An indicator that specifies whether or not the registration is removed automatically once the notification occurs.

- `timeout`

  The amount of time, in seconds, that the registration stays active. When `timeout` is set to `0`, the registration never expires. The valid values for `timeout` are between `0` and `4294967295`.

- `isPersistent`

  Indicates whether or not the invalidation message should be queued persistently in the database before delivery. If the `isPersistent` parameter is set to `True`, the message is queued persistently in the database and cannot be lost upon database failures or shutdowns. If the `isPersistent` property is set to `False`, the message is stored in an in-memory queue before delivery and might be lost.

  Database performance is faster if the message is stored in an in-memory queue rather than in the database queue.

### Exceptions

`ArgumentNullException` - The `cmd` parameter is null.

`ArgumentOutOfRangeException` - The specified `timeout` is invalid.

`InvalidOperationException` - The specified `OracleCommand` instance already contains a notification request.

### Remarks

When this `OracleDependency` constructor binds the `OracleCommand` instance to an `OracleDependency` instance, it causes the creation of an `OracleNotificationRequest` instance and then sets that `OracleNotificationRequest` instance to the `OracleCommand.``Notification` property.

The Continuous Query Notification is registered with the database, when the command is executed. Any of the command execution methods (for example, `ExecuteNonQuery`, `ExecuteReader`, and so on) will register the notification request. An `OracleDependency` may be bound to more than one `OracleCommand`. When one of these `OracleCommand` object statements is executed, the statement is registered with the associated `OracleCommand`. Although the registration happens on each `OracleCommand` separately, one `OracleDependency` can be responsible for detecting and sending notifications that occur for all `OracleCommand` objects that the `OracleDependency` is associated with. The `OnChangeEventArgs` that is passed to the application for the `OnChange` event provides information on what has changed in the database.

The `OracleNotificationRequest` instance that is created by this constructor has the following default property values:

- `IsNotifiedOnce` is set to the specified value.

- `Timeout` is set to the specified value.

- `IsPersistent` is set to the specified value.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
