This instance property specifies whether the change notification registration is object-based or query-based.

### Declaration

    // C#
    public bool QueryBasedNotification{get; set;}

### Property Value

Specifies whether the change notification registration is object-based or not.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This property value will be ignored if it is set after the command execution that registers the command for change notification.

By default, this property is true.

ODP.NET developers can register their queries on the row level, not just the object level, beginning with Oracle Data Provider for .NET release 11.1 and Oracle Database 11g release 1 (11.1). The application only receives notification when the selected row or rows change. Query-based notifications provide developers more granularity for using client-side cached data, as they can be more specific about what changes the application needs to be notified of.

`OracleNotificationType` enumeration is set to `Query` for query-based notifications.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
