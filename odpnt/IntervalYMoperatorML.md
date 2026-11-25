This static operator multiplies an `OracleIntervalYM` value by a number.

### Declaration

    // C#
    public static OracleIntervalYM operator * (OracleIntervalYM val1, int multiplier);

### Parameters

- `val1`

  The first `OracleIntervalYM`.

- `multiplier`

  A multiplier.

### Return Value

An `OracleIntervalYM` structure.

### Remarks

If the supplied `OracleIntervalYM` structure has a null value, the returned `OracleIntervalYM` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
