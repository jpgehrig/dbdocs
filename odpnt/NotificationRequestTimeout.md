This property specifies the time, in seconds, that the registration remains alive.

### Declaration

    // C#
    public long Timeout{get; set}

### Property Value

A `long` value that specifies the time, in seconds, that the registration remains alive. The valid values for the `Timeout` property are between `0` and `4294967295`.

### Exceptions

`ArgumentOutOfRangeException` - The specified `Timeout` is invalid.

### Remarks

The default value is` 0` (infinite) for AQ and 50000 for change notification. If the `Timeout` property is set to `0`, then the registration does not expire.

If the registration is removed because the `Timeout` value has been reached, then the database sends a notification indicating the expiration.

Modifying this property after the completion of a successful registration has no effect.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
