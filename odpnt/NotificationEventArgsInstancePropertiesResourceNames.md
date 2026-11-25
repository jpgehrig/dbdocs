This property indicates the database resources related to the current notification.

### Declaration

    // C#
    public string[] ResourceNames{get;}

### Property Value

A string array that indicates the database resources related to the current notification.

### Remarks

For Continuous Query Notification, the `ResourceNames` property contains information about the invalidated object names in the format \<`schema_name`\>.\<`object` `_name`\>. To obtain more detailed information about the changes for invalidated objects, use the `Details` property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)

- [OracleNotificationEventArgs Members](NotificationEventArgsMembers.md)

- "[Details](NotificationEventArgsInstancePropertiesDetails.md)"
