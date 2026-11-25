This instance property returns the data, starting from the first character in the `CLOB` or `NCLOB`, as a string.

### Declaration

    // C#
    public string Value{get;}

### Property Value

A string.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `Value` is less than `0`.

### Remarks

The value of `Position` is neither used nor changed by using this property.

The maximum string length that can be returned by this property is 2 GB.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
