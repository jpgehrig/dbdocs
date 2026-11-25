This static method determines whether or not the first of two `OracleString` values is less than the second.

### Declaration

    // C#
    public static bool LessThan(OracleString str1, OracleString str2);

### Parameters

- `str1`

  The first `OracleString.`

- `str2`

  The second `OracleString.`

### Return Value

Returns `true` if the first is less than the second; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleString` that has a value is greater than an `OracleString` that has a null value.

- Two `OracleString`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
