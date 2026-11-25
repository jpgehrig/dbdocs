This static type conversion operator converts an `OracleTimeStampTZ` value to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public static explicit operator OracleTimeStamp(OracleTimeStampTZ value1);

### Parameters

- `value1`

  An `OracleTimeStampTZ` instance.

### Return Value

The returned `OracleTimeStamp` contains the date and time information from `value1`, but the time zone information from `value1` is truncated.

### Remarks

If the `OracleTimeStampTZ` structure has a null value, the returned `OracleTimeStamp` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
