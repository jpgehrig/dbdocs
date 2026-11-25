This property specifies whether to group notifications together by time is enabled or not.

### Declaration

    // C#
    public bool GroupingNotificationEnabled {get; set}

### Property Value

A `true` value indicates that grouping notification is enabled. A `false` value indicates that grouping notification is disabled.

### Remarks

The default value is `false`.

Modifying this property after the completion of a successful registration has no effect.

If enabled, then ODP.NET will group notifications together that occur during the same time period.  The time period is defined by `OracleNotificationRequest.GroupingInterval`.

If disabled, then notifications will be generated immediately after the event that triggers them.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
