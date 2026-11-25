This method returns a `CodeAccessPermission` object that represents an `OraclePermission` object.

### Declaration

    // C#
    public override System.Security.CodeAccessPermission CreatePermission(
      System.Security.Permissions.PermissionState state);

### Parameter

- `state`

  A `PermissionState` object.

### Return Value

A `CodeAccessPermission` object that represents an `OraclePermission` object.

### Remarks

This method enables users, writing provider-independent code, to get a `CodeAccessPermission` instance that represents an `OraclePermission` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleClientFactory Class](OracleClientFactoryClass.md)

- [OracleClientFactory Members](OracleClientFactoryMembers.md)
