The `OnChange` event is sent when a database notification associated with the dependency is received from the database. The information related to the notification is stored in the `OracleChangeNotificationEventArgs` class.

### Declaration

    // C#
    public event OnChangeEventHandler OnChange;

### Remarks

The `OnChange` event occurs if any result set associated with the dependency changes. For objects that are part of a Transaction, notifications will be received for each modified object. This event also occurs for other actions related to database or registration status, such as database shutdowns and startups, or registration timeouts.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
