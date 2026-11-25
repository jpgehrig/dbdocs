This static operator concatenates two `OracleString` values.

### Declaration

    // C#
    public static OracleString operator + (OracleString value1, OracleString value2);

### Parameters

- `value1`

  The first `OracleString`.

- `value2`

  The second `OracleString`.

### Return Value

An `OracleString.`

### Remarks

If either argument has a null value, the returned `OracleString` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
