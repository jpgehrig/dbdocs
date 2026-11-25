This static type conversion operator converts an `OracleTimeStampLTZ` value to a `DateTime` structure.

### Declaration

    // C#
    public static explicit operator DateTime(OracleTimeStampLTZ value1);

### Parameters

- `value1`

  An `OracleTimeStampLTZ` instance.

### Return Value

A `DateTime` that contains the date and time in the current instance.

### Exceptions

`OracleNullValueException` - The `OracleTimeStampLTZ` structure has a null value.

### Remarks

The precision of the `OracleTimeStampLTZ` value can be lost during the conversion.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
