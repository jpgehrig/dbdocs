This static operator divides an `OracleIntervalDS` value by a number.

### Declaration

    // C#
    public static OracleIntervalDS operator / (OracleIntervalDS val1,
       int divisor);

### Parameters

- `val1`

  The first `OracleIntervalDS`.

- `divisor`

  A divisor.

### Return Value

An `OracleIntervalDS` structure.

### Remarks

If the `OracleIntervalDS` structure has a null value, the returned `OracleIntervalDS` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
