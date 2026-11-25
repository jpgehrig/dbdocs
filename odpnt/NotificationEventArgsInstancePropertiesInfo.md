This property indicates the database events for the notification.

### Declaration

    // C#
    public OracleNotificationInfo Info{get;}

### Property Value

An `OracleNotificationInfo` value that indicates the database event for the notification.

### Remarks

The `OracleNotificationInfo` value is an enumeration type. If several events are received from the invalidation message, the `Info` property is set to one of the `OracleNotificationInfo` enumeration values associated with the database events. For example, if a table has been altered and a new row has been inserted into another table, the `Info` property is set to either `OracleNotificationInfo.Alter`ed or `OracleNotificationInfo.Insert`.

To obtain more detailed information from the invalidation message, use the `Details` and the `ResourceNames` properties.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)

- [OracleNotificationEventArgs Members](NotificationEventArgsMembers.md)

- "[Details](NotificationEventArgsInstancePropertiesDetails.md)"

- "[ResourceNames](NotificationEventArgsInstancePropertiesResourceNames.md)"

- "[OracleNotificationInfo Enumeration](OracleNotificationInfoEnumeration.md)"
