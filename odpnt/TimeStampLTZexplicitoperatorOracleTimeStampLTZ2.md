This static type conversion operator converts an `OracleTimeStampTZ` value to an `OracleTimeStampLTZ` structure.

### Declaration

    // C#
    public static explicit operator OracleTimeStampLTZ
      (OracleTimeStampTZ value1);

### Parameters

- `value1`

  An `OracleTimeStampTZ` instance.

### Return Value

The `OracleTimeStampLTZ` structure contains the date and time in the `OracleTimeStampTZ` structure (which is normalized to the client local time zone).

### Remarks

If the `OracleTimeStampTZ` structure has a null value, the returned `OracleTimeStampLTZ` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
