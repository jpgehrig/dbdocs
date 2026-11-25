This instance method compares the LOB data referenced by two `OracleClob`s.

### Declaration

    // C#
    public bool IsEqual(OracleClob obj);

### Parameters

- `obj`

  An `OracleClob` object.

### Return Value

Returns `true` if the current `OracleClob` and the provided `OracleClob` refer to the same LOB. Otherwise, returns `false`.

### Remarks

Note that this method can return `true` even if the two `OracleClob` objects returns `false` for == or `Equals()` because two different `OracleClob` instances can refer to the same LOB.

The provided object and the current instance must be using the same connection, that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
