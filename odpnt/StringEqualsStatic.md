Overloads `Object`

This static method determines whether or not the two `OracleString`s being compared are equal.

### Declaration

    // C#
    public static bool Equals(OracleString str1, OracleString str2);

### Parameters

- `str1`

  The first `OracleString.`

- `str2`

  The second `OracleString.`

### Return Value

Returns `true` if the two `OracleString`s being compared are equal; returns `false` otherwise.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleString` that has a value is greater than an `OracleString` that has a null value.

- Two `OracleString`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
