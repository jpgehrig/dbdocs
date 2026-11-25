This static operator determines if two `OracleString` values are equal.

### Declaration

    // C#
    public static bool operator == (OracleString value1, OracleString value2);

### Parameters

- `value1`

  The first `OracleString`.

- `value2`

  The second `OracleString`.

### Return Value

Returns `true` if two `OracleString` values are equal; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleString` that has a value is greater than an `OracleString` that has a null value.

- Two `OracleString`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
