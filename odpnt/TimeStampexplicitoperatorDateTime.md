This static type conversion operator converts an `OracleTimeStamp` value to a `DateTime` structure.

### Declaration

    // C#
    public static explicit operator DateTime(OracleTimeStamp value1);

### Parameters

- `value1`

  An `OracleTimeStamp` instance.

### Return Value

A `DateTime` containing the date and time in the current instance.

### Exceptions

`OracleNullValueException` - The `OracleTimeStamp` structure has a null value.

### Remarks

The precision of the `OracleTimeStamp` can be lost during the conversion.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
