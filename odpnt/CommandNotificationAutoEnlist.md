This instance property indicates whether or not to register for a continuous query notification with the database automatically when the command is executed.

### Declaration

    // C#
    public bool NotificationAutoEnlist {set; get;}

### Property Value

A `bool` value indicating whether or not to make a continuous query notification request automatically, when the command is executed. If `NotificationAutoEnlist` is set to `true`, and the `Notification` property is set appropriately, a continuous query notification request is registered automatically; otherwise, no continuous query notification registration is made.

Default value: `true`

### Remarks

A notification request can be used for multiple command executions using the same `OracleCommand` instance. In that case, set the `NotificationAutoEnlist` property to `true`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Continuous Query Notification Support](featChange.md)"

- [Continuous Query Notification Classes](Continuous-Query-Notification-Classes.md)
