This instance property indicates the directory alias of the `BFILE`.

### Declaration

    // C#
    public string DirectoryName {get;set;}

### Property Value

A `string`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The value of the `DirectoryName` changed while the `BFILE` is open.

### Remarks

The maximum length of a `DirectoryName` is 30 bytes.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
