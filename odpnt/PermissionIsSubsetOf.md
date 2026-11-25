This method returns a boolean value that indicates whether or not the current permission is a subset of the target permission.

### Declaration

    // C#
    public override bool IsSubsetOf(IPermission target);

### Parameters

- `target`

  A permission that must be of type `OraclePermission`.

### Return Value

A `bool` value that indicates whether or not the current permission is a subset of the target permission.

### Exceptions

`ArgumentException` - The permission is not of the `OraclePermission` type.

### Remarks

The `AllowBlankPassword` property is ignored when evaluating whether or not the current permission is a subset of the target permission.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OraclePermission Class](OraclePermissionClass.md)

- [OraclePermission Members](PermissionMembers.md)
