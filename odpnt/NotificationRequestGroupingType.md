This property specifies the type of grouping notification, which can summarize all notifications during the time period or only the last notification.

### Declaration

    // C#
    public OracleAQNotificationGroupingType GroupingType {get; set}

### Property Value

An `OracleAQNotificationGroupingType` enum value. The possible enum values are `OracleAQNotificationGroupingType.Summary` and `OracleAQNotificationGroupingType.Last`.

### Remarks

The default value is `OracleAQNotificationGroupingType.Summary`.

Modifying this property after the completion of a successful registration has no effect.

`OracleAQNotificationGroupingType.Summary` : All notifications in the group are summarized into a single notification.

**Note:**

The single notification does not include `ROWID`s, even if `ROWID` information was requested to be returned.

`OracleAQNotificationGroupingType.Last` : Only the last notification in the group is published. The earlier ones discarded.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
