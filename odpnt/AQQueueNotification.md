This instance property specifies the various notification options for notifications that are registered using the `MessageAvailable` event.

### Declaration

    // C#
    public OracleNotificationRequest Notification {get;}

### Property Value

Specifies an `OracleNotificationRequest` object whose properties can be changed to alter the notification behavior.

### Remarks

This property can be used to change various notification options. The notification options must be changed before registering with the `MessageAvailable` event. This property can be modified again only after unregistering from the `MessageAvailable` event.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
