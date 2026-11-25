This instance property returns an array of message identifiers.

### Declaration

    // C#
    public byte[][] MessageId{get;}

### Property Value

A `byte[][]` that specifies the message identifiers received as part of the notification.

### Remarks

This property specifies the message identifiers of the messages that raise the notification.

The size of the `MessageId` array is 1 for regular notifications. The size of the MessageId array is 1 for grouping notifications if the notification grouping type is `OracleAQNotificationGroupingType.Last`. This property is not relevant if the `NotificationType` is `OracleAQNotificationType.Timeout`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessageAvailableEventArgs Class](OracleAQMessageAvailableEventArgsClass.md)

- [OracleAQMessageAvailableEventArgs Members](AQMessageAvailableEventArgsMembers.md)
