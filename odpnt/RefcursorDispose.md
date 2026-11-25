This instance method disposes of the resources allocated by the `OracleRefCursor` object.

### Declaration

    // C#
    public void Dispose();

### Implements

`IDisposable`

### Remarks

The object cannot be reused after being disposed.

Once `Dispose()` is called, the object of `OracleRefCursor` is in an uninitialized state. Although some properties can still be accessed, their values may not be accountable. Since resources are freed, method calls can lead to exceptions.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)

- [OracleRefCursor Members](RefCursorMembers.md)
