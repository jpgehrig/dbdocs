This property specifies the `OracleBulkCopyOptions` enumeration value that determines the behavior of the bulk copy option.

### Declaration

    // C#
    public OracleBulkCopyOptions BulkCopyOptions {get; set;}

### Property Value

The `OracleBulkCopyOptions` enumeration object that defines the behavior of the bulk copy operation.

### Exceptions

`ArgumentNullException` - The bulk copy options set is null.

### Remarks

The default value of this property is `OracleBulkCopyOptions.Default` value. This property can be used to change the bulk copy options between the batches of a bulk copy operation.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
