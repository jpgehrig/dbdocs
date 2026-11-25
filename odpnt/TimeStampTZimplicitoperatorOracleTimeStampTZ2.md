This static type conversion operator converts a `DateTime` structure to an `OracleTimeStampTZ` structure.

### Declaration

    // C#
    public static implicit operator OracleTimeStampTZ (DateTime value1);

### Parameters

- `value1`

  A `DateTime` structure.

### Return Value

The returned `OracleTimeStampTZ` contains the date and time from the `DateTime` and the time zone from the `OracleGlobalization.TimeZone` of the thread.

### Remarks

The `OracleGlobalization.TimeZone` of the thread is used to convert from a `DateTime` to an Oracle `TimeStampTZ` structure.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
