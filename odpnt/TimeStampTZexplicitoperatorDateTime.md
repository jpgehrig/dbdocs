This static type conversion operator converts an `OracleTimeStampTZ` value to a `DateTime` structure and truncates the time zone information.

### Declaration

    // C#
    public static explicit operator DateTime(OracleTimeStampTZ value1);

### Parameters

- `value1`

  An `OracleTimeStampTZ`.

### Return Value

A `DateTime` containing the date and time in the current instance, but with the time zone information in the current instance truncated.

### Exceptions

`OracleNullValueException` - The `OracleTimeStampTZ` structure has a null value.

### Remarks

The precision of the `OracleTimeStampTZ` value can be lost during the conversion, and the time zone information in the current instance is truncated

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
