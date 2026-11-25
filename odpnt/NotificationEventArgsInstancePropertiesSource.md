This property returns the database event source for the notification.

### Declaration

    // C#
    public OracleNotificationSource Source{get;}

### Property Value

The `OracleNotificationSource` value for the notification.

### Remarks

The `OracleNotificationSource` value is an enumeration type. If several event sources are received from the notification message, the `Source` property is set to one of the `OracleNotificationSource` enumeration values related to the database event source. For example, if a table has been altered (by the `ALTER` `TABLE` command) and a new row has been inserted into the same table, the `Source` property is set to either `OracleNotificationSource.Object` or `OracleNotificationSource.Data`.

For Continuous Query Notification:

- When the `Source` property is set to `OracleNotificationSource.Data`:

  - The `Info` property is set to one of the following:

    - `OracleNotificationInfo.Insert`

    - `OracleNotificationInfo.Delete`

    - `OracleNotificationInfo.Update`

  - The `ResourceNames` property is set, and the elements are set to the invalidated object names.

  - The `Details` property contains detailed information on the change of each invalidated table.

- When the `Source` property is set to `OracleNotificationSource.Database`:

  - The `Info` property is set to one of the following:

    - `OracleNotificationInfo.Startup`

    - `OracleNotificationInfo.Shutdown`

    - `OracleNotificationInfo.Shutdown_Any`

    - `OracleNotificationInfo.Dropped`

- When the `Source` property is set to `OracleNotificationSource.Object`:

  - The `Info` property is set to either `OracleNotificationInfo.Altered` or `OracleNotificationInfo.Dropped`.

  - The `ResourceNames` property is set, and the array elements of the `ResourceNames` property are set to the object names that have been altered or dropped.

  - The `Details` property contains detailed information on the changes of the object.

- When the `Source` property is set to `OracleNotificationSource.Subscription`:

  - The `Info` property is set to the following:

    - `OracleNotificationInfo.End`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)

- [OracleNotificationEventArgs Members](NotificationEventArgsMembers.md)

- "[OracleNotificationSource Enumeration](OracleNotificationSourceEnumeration.md)"
