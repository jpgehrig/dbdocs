This property specifies the interval of grouping notification in seconds. The group notifications are delivered at intervals specified by this property.

### Declaration

    // C#
    public int GroupingInterval {get; set}

### Property Value

An `integer` specifying the grouping interval in seconds.

### Remarks

If this value is 900, then notifications generated in the same 15 minute interval are grouped together into a single notification. The default value is 600 seconds.

The range of `GroupingInterval` is from `1` to `Int32.MaxValue`.

Modifying this property after the completion of a successful registration has no effect.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Class](OracleNotificationRequestClass.md)
