This static operator determines whether two `OracleIntervalYM` values are not equal.

### Declaration

    // C#
    public static bool operator != (OracleIntervalYM val1, OracleIntervalYM val2)

### Parameters

- `val1`

  The first `OracleIntervalYM`.

- `val2`

  The second `OracleIntervalYM`.

### Return Value

Returns `true` if two `OracleIntervalYM` values are not equal; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleIntervalYM` that has a value compares greater than an `OracleIntervalYM` that has a null value.

- Two `OracleIntervalYM`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
