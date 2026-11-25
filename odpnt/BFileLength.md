Overrides `Stream`

This instance property indicates the size of the `BFILE` data in bytes.

### Declaration

    // C#
    public override Int64 Length {get;}

### Property Value

`Int64`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
