This property indicates the database user name associated with the `OracleDependency` instance.

### Declaration

    // C#
    public string UserName{get;}

### Property Value

A string that indicates the database user name associated with the `OracleDependency` instance. This database user registers the Continuous Query Notification request with the database.

### Remarks

The `UserName` property is populated with the user name once the `OracleCommand` associated with the `OracleDependency` executes and registers for the notification successfully. Only the database user who creates the notification registration, or the database system administrator, can remove the registration.

The user specified by this property must have the `CHANGE` `NOTIFICATION` privilege to register successfully for the Continuous Query Notification with the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
