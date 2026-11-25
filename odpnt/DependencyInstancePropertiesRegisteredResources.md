This property indicates the database resources that are registered in the notification registration.

### Declaration

    // C#
    public ArrayList RegisteredResources{get;}

### Property Value

The registered resources in the notification registration.

### Remarks

The `ArrayList` contains all the command statement or statements that are registered for notification through this `OracleDependency` object. It is appropriately updated when the Continuous Query Notification is registered by a command execution.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
