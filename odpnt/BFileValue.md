This instance property returns the data, starting from the first byte in `BFILE`, as a byte array.

### Declaration

    // C#
    public byte[] Value{get;}

### Property Value

A byte array.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The length of data is bound by the maximum length of the byte array. The current value of the `Position` property is not used or changed.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
