This type conversion operator converts a `TimeSpan` structure to an `OracleIntervalDS` structure.

### Declaration

    // C#
    public static implicit operator OracleIntervalDS(TimeSpan val);

### Parameters

- `val`

  A `TimeSpan` instance.

### Return Value

An `OracleIntervalDS` structure.

### Remarks

The returned `OracleIntervalDS` structure contains the same days, hours, seconds, and milliseconds as the supplied `TimeSpan` `val`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
