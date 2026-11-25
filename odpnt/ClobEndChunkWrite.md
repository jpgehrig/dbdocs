This instance method closes the `CLOB` referenced by the current `OracleClob` instance.

### Declaration

    // C#
    public void EndChunkWrite();

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

Index updates occur immediately if write operation(s) are deferred by the `BeginChunkWrite` method.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
