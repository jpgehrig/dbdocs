This instance property specifies the position of the message that will be retrieved.

### Declaration

    // C#
    public OracleAQNavigationMode NavigationMode {get;set;}

### Property Value

An `OracleAQNavigationMode` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The specified `NavigationMode` value is invalid.

### Remarks

The default value is `OracleAQNavigationMode.NextMessage`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
