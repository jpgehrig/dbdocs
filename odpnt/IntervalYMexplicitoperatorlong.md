This type conversion operator converts an `OracleIntervalYM` to a number that represents the number of months in the time interval.

### Declaration

    // C#
    public static explicit operator long (OracleIntervalYM val);

### Parameters

- `val`

  An `OracleIntervalYM` structure.

### Return Value

A `long` number in months.

### Exceptions

`OracleNullValueException` - The `OracleIntervalYM` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
