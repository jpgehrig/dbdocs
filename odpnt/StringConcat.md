This static method concatenates two `OracleString` instances and returns a new `OracleString` instance that represents the result.

### Declaration

    // C#
    public static OracleString Concat(OracleString str1, OracleString str2);

### Parameters

- `str1`

  The first `OracleString.`

- `str2`

  The second `OracleString`.

### Return Value

An `OracleString.`

### Remarks

If either argument has a null value, the returned `OracleString` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
