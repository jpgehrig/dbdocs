This static method returns a new instance of an `OracleTimeStamp` with the specified fractional second precision.

### Declaration

    // C#
    public static OracleTimeStamp SetPrecision(OracleTimeStamp value1,
        int fracSecPrecision);

### Parameters

- `value1`

  The provided `OracleTimeStamp` object.

- `fracSecPrecision`

  The fractional second precision provided. Range of fractional second precision is (0 to 9).

### Return Value

An `OracleTimeStamp` structure with the specified fractional second precision.

### Exceptions

`ArgumentOutOfRangeException` - `fracSecPrecision` is out of the specified range.

### Remarks

The value specified in the supplied `fracSecPrecision` is used to perform a rounding off operation on the supplied `OracleTimeStamp` value. Depending on this value, `0` or more trailing zeros are displayed in the string returned by `ToString()`.

### Example

The `OracleTimeStamp` with a value of "`December` `31,` `9999` `23:59:59.99`" results in the string "`December` `31,` `9999` `23:59:59.99000`" when `SetPrecision()` is called with the fractional second precision set to `5`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
