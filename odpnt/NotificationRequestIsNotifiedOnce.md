This property indicates whether or not the registration is to be removed upon notification.

### Declaration

    // C#
    public bool IsNotifiedOnce{get; set;}

### Property Value

A `bool` value that indicates whether or not the registration is to be removed upon notification.

### Remarks

The default value is `false` for AQ. This is different from change notification where the default value is `true`.

Modifying this property after the completion of a successful registration has no effect.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
