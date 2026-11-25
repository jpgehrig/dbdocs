This property returns the database event type for the notification.

### Declaration

    // C#
    public OracleNotificationType Type{get;}

### Property Value

An `OracleNotificationType` enumeration value that represents the type of the database event notification.

### Remarks

The `OracleNotificationType` value is an enumeration type. If several event types are received from the notification message, then the `Type` property is set to one of the `OracleNotificationType` enumeration values related to the database event type.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)

- [OracleNotificationEventArgs Members](NotificationEventArgsMembers.md)

- "[OracleNotificationType Enumeration](OracleNotificationTypeEnumeration.md)"
