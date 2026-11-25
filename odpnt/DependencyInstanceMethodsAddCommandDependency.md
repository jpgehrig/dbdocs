This instance method binds the `OracleDependency` instance to the specified `OracleCommand` instance.

### Declaration

    // C#
    Public void AddCommandDependency (OracleCommand cmd);

### Parameters

- `cmd`

  The command that is to be bound to the `OracleDependency` object.

### Exceptions

`ArgumentNullException` - The `cmd` parameter is null.

`InvalidOperationException` - The specified `OracleCommand` instance already contains a notification request.

### Remarks

An `OracleDependency` instance can bind to multiple `OracleCommand` instances.

While it binds an existing `OracleDependency` instance to an `OracleCommand` instance, the `AddCommandDependency` method creates an `OracleNotificationRequest` instance, and sets it to the specified `OracleCommand.Notification` property.

When this method creates an `OracleNotificationRequest` instance, the following `OracleNotificationRequest` properties are set:

- `IsNotifiedOnce` is set to the value `True`.

- `Timeout` is set to 50,000 seconds.

- `IsPersistent` is set to the value `False`, indicating that the invalidation message is stored in an in-memory queue before delivery.

With this method, multiple commands can be associated with a single Continuous Query Notification registration request. Furthermore, the `OracleNotificationRequest` attribute values assigned to the `OracleCommand` can be changed once the association between the `OracleCommand` and the `OracleDependency` is established.

However, when multiple `OracleCommand` objects are associated with a single `OracleDependency` object, the `OracleNotificationRequest` attributes (`Timeout`, `IsPersistent`, and `IsNotifiedOnce`) of the first executed `OracleCommand` object are used for registration, the attributes associated with subsequent `OracleCommand` executions will be ignored.

Furthermore, once a command associated with an `OracleDependency` is executed and registered, all other subsequent command executions and registration associated with the same `OracleDependency` must use a connection with the same `"User` `Id"` and `"Data` `Source"` connection string attribute value settings.

Otherwise, an exception will be thrown.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)

- "[OracleDependency(OracleCommand)](DependencyCtor2.md)" for `OracleNotificationRequest` property value
