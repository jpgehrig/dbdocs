This static type conversion operator converts an `OracleTimeStamp` value to an `OracleTimeStampLTZ` structure.

### Declaration

    // C#
    public static explicit operator OracleTimeStampLTZ (OracleTimeStamp value1);

### Parameters

- `value1`

  An `OracleTimeStamp`.

### Return Value

The `OracleTimeStampLTZ` structure contains the date and time of the `OracleTimeStampTZ` structure.

### Remarks

If the `OracleTimeStamp` structure has a null value, the returned `OracleTimeStampLTZ` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
