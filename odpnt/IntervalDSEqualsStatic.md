This static method determines whether or not two `OracleIntervalDS` values are equal.

### Declaration

    // C#
    public static bool Equals(OracleIntervalDS val1, OracleIntervalDS val2);

### Parameters

- `val1`

  The first `OracleIntervalDS`.

- `val2`

  The second `OracleIntervalDS`.

### Return Value

If the two `OracleIntervalDS` structures represent the same time interval, returns `true`; otherwise, returns `false`.

### Remarks

The following rules apply to the behavior of this method.

- Any `OracleIntervalDS` that has a value compares greater than an `OracleIntervalDS` that has a null value.

- Two `OracleIntervalDS`s that contain a null value are equal.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
