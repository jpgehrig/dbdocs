This instance method appends the `CLOB` data referenced by the provided `OracleClob` object to the current `OracleClob` instance.

### Declaration

    // C#
    public void Append(OracleClob obj);

### Parameters

- `obj`

  An `OracleClob` object.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The parameter has a different connection than the object, `OracleConnection` is not opened, or `OracleConnection` has been reopened.

### Remarks

No character set conversions are made.

The provided object and the current instance must be using the same connection; that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
