This static method returns a new instance of an `OracleIntervalDS` with the specified day precision and fractional second precision.

### Declaration

    // C#
    public static OracleIntervalDS SetPrecision(OracleIntervalDS value1,
        int dayPrecision, int fracSecPrecision);

### Parameters

- `value1`

  An `OracleIntervalDS` structure.

- `dayPrecision`

  The day precision provided. Range of day precision is (0 to 9).

- `fracSecPrecision`

  The fractional second precision provided. Range of fractional second precision is (0 to 9).

### Return Value

An `OracleIntervalDS` instance.

### Exceptions

`ArgumentOutOfRangeException` - An argument value is out of the specified range.

### Remarks

Depending on the value specified in the supplied `dayPrecision`, 0 or more leading zeros are displayed in the string returned by `ToString()`.

The value specified in the supplied `fracSecPrecision` is used to perform a rounding off operation on the supplied `OracleIntervalDS` value. Depending on this value, `0` or more trailing zeros are displayed in the string returned by `ToString()`.

### Example

The `OracleIntervalDS` with a value of "`1` `2:3:4.99`" results in the string "`001` `2:3:4.99000`" when `SetPrecision()` is called, with the day precision set to `3` and fractional second precision set to `5`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
