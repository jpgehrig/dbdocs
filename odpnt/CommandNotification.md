This instance property indicates that there is a notification request for the command.

### Declaration

    // C#
    public OracleNotificationRequest  Notification {set; get;}

### Property Value

A notification request for the command.

### Remarks

When a changed notification is first registered, the client listener is started in order to receive any database notification. The listener uses the port number defined in the `OracleDependency.Port` static field. Subsequent change notification registrations use the same listener in the same client process and do not start another listener.

When `Notification` is set to an `OracleNotificationRequest` instance, a notification registration is created (if it has not already been created) when the command is executed. Once the registration is created, the properties of the `OracleNotificationRequest` instance cannot be modified. If the notification registration has already been created, the result set that is associated with the command is added to the existing registration.

When `Notification` is set to `null`, subsequent command executions do not require a notification request. If a notification request is not required, set the `Notification` property to `null`, or set the `NotificationAutoEnlist` property to `false`.

For Continuous Query Notification, a notification request can be used for multiple command executions. In that case, any query result set associated with different commands can be invalidated within the same registration.

When the `OracleDependency.OnChange` event is fired, if the `ROWID` column is explicitly included in the query (or `AddRowid` property is set to `true`), then the `Rowid` column contains `ROWID` values in the `DataTable` referenced by the `OracleNotificationEventArgs.Details` property. This behavior can be overridden by explicitly requesting for an inclusion and exclusion of `ROWID` values in the `OracleNotificationEventArgs` by setting the `OracleDependency.RowidInfo` to `OracleRowidInfo.Include` or `OracleRowidInfo.Exclude`, respectively.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Continuous Query Notification Support](featChange.md)"

- [Continuous Query Notification Classes](Continuous-Query-Notification-Classes.md)
