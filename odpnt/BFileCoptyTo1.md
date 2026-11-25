This instance method copies data from the current instance to the provided `OracleBlob` object.

### Declaration

    // C#
    public Int64 CopyTo(OracleBlob obj);

### Parameters

- `obj`

  The `OracleBlob` object to which the data is copied.

### Return Value

The return value is the amount copied.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - This exception is thrown if any of the following conditions exist:

- The `OracleConnection` is not open or has been closed during the lifetime of the object.

- The LOB object parameter has a different connection than the object.

### Remarks

The provided object and the current instance must be using the same connection; that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
