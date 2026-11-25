This property defines the number of rows to be processed before a notification event is generated.

### Declaration

    // C#
    public int NotifyAfter {get; set;}

### Property Value

An integer value that specifies the number of rows to be processed before the notification event is raised.

### Exceptions

`ArgumentOutOfRangeException` - The property value is set to a number less than zero.

### Remarks

The default value for this property is zero, to specify that no notifications events are to be generated.

This property can be retrieved in user interface components to display the progress of a bulk copy operation. The `NotifyAfter` property can be set at anytime, even during a bulk copy operation. The changes take effect for the next notification and any subsequent operations on the same instance.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
