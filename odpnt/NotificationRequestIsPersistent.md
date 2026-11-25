This property indicates whether or not the notification message should be queued persistently in the database until delivery.

### Declaration

    // C#
    public bool IsPersistent{get; set;}

### Property Value

A `bool` value that indicates whether or not the notifications should be stored persistently in the database until delivery.

When the `IsPersistent` property is set to `True`, the message is queued persistently in the database and cannot be lost upon database failures or shutdowns. When the `IsPersistent` property is set to `False`, the message is stored in an in-memory queue before delivery and could be lost.

This property does not apply to `NotificationRegistration` which is always persistent.

This property only applies to the notification message after it has been sent.

### Remarks

The default value is `false`.

The database performs faster if the message is stored in an in-memory queue rather than a database queue.

Modifying this property after the completion of a successful registration has no effect.

This property is ignored for grouping notifications.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
