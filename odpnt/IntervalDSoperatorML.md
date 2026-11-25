This static operator multiplies an `OracleIntervalDS` value by a number.

### Declaration

    // C#
    public static OracleIntervalDS operator * (OracleIntervalDS val1,
       int multiplier);

### Parameters

- `val1`

  The first `OracleIntervalDS`.

- `multiplier`

  A multiplier.

### Return Value

A new `OracleIntervalDS` instance.

### Remarks

If the `OracleIntervalDS` structure has a null value, the returned `OracleIntervalDS` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
