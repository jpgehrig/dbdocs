This instance property specifies the number of messages that raised this notification.

### Declaration

    // C#
    public int AvailableMessages{get;}

### Property Value

An `integer` indicating the number of messages that raised this notification.

### Remarks

The property value is 1 for a regular notification type. The notification type can be specified using the `OracleAQQueue.Notification` property.

This property is not relevant if the `NotificationType` is `OracleAQNotificationType.Timeout`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessageAvailableEventArgs Class](OracleAQMessageAvailableEventArgsClass.md)

- [OracleAQMessageAvailableEventArgs Members](AQMessageAvailableEventArgsMembers.md)
