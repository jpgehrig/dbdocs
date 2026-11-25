This instance property indicates whether or not the `BFILE` specified by the `DirectoryName` and `FileName` exists.

### Declaration

    // C#
    public bool FileExists {get;}

### Property Value

`bool`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

Unless a connection, file name, and directory name are provided, this property is set to `false` by default.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
