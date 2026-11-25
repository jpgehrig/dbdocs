This instance property provides a list of `CHANGE_NOTIFICATION_QUERY_ID`s.

### Declaration

    // C#
    public ArrayList RegisteredQueryIDs {get;}

### Property Value

This property is an `ArrayList` of `CHANGE_NOTIFICATION_QUERY_ID`s.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This property provides a list of `CHANGE_NOTIFICATION_QUERY_ID`s that uniquely identify the query that has been registered for change notification. The notification returned from the database will also contain these IDs, allowing applications to determine the query that the notifications are for.

The `QueryId` at index n in `RegisteredQueryIDs` is for the statement at index n the `RegisteredResources` at index n.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
