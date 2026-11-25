This static method returns a new instance of an `OracleIntervalYM` with the specified year precision.

### Declaration

    // C#
    public static OracleIntervalYM SetPrecision(OracleIntervalYM value1,
       int yearPrecision);

### Parameters

- `value1`

  An `OracleIntervalYM` structure.

- `yearPrecision`

  The year precision provided. Range of year precision is (0 to 9).

### Return Value

An `OracleIntervalDS` instance.

### Exceptions

`ArgumentOutOfRangeException` - `yearPrecision` is out of the specified range.

### Remarks

Depending on the value specified in the supplied `yearPrecision`, `0` or more leading zeros are displayed in the string returned by `ToString()`.

### Example

An `OracleIntervalYM` with a value of "`1-2`" results in the string "`001-2`" when `SetPrecision()` is called with the year precision set to `3`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
