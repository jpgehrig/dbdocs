This static operator subtracts one `OracleIntervalDS` structure from another.

### Declaration

    // C#
    public static OracleIntervalDS operator - (OracleIntervalDS val1,
       OracleIntervalDS val2);

### Parameters

- `val1`

  The first `OracleIntervalDS`.

- `val2`

  The second `OracleIntervalDS`.

### Return Value

An `OracleIntervalDS` structure.

### Remarks

If either argument has a null value, the returned `OracleIntervalDS` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
