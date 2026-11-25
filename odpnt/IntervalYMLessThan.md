This static method determines whether or not the first of two `OracleIntervalYM` values is less than the second.

### Declaration

    // C#
    public static bool LessThan(OracleIntervalYM val1, OracleIntervalYM val2);

### Parameters

- `val1`

  The first `OracleIntervalYM`.

- `val2`

  The second `OracleIntervalYM`.

### Return Value

Returns `true` if the first of two `OracleIntervalYM` values is less than the second; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleIntervalYM` that has a value compares greater than an `OracleIntervalYM` that has a null value.

- Two `OracleIntervalYM`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
