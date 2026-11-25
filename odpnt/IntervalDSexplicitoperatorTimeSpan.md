This type conversion operator converts an `OracleIntervalDS` structure to a `TimeSpan` structure.

### Declaration

    // C#
    public static explicit operator TimeSpan(OracleIntervalDS val);

### Parameters

- `val`

  An `OracleIntervalDS` instance.

### Return Value

A `TimeSpan` structure.

### Exceptions

`OracleNullValueException` - The `OracleIntervalDS` structure has a null value.

### Remarks

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
