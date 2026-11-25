This static type conversion operator converts an `OracleTimeStampLTZ` value to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public static explicit operator OracleTimeStamp(OracleTimeStampLTZ value1);

### Parameters

- `value1`

  An `OracleTimeStampLTZ` instance.

### Return Value

The returned `OracleTimeStamp` contains the date and time of the `OracleTimeStampLTZ` structure.

### Remarks

If the `OracleTimeStampLTZ` structure has a null value, the returned `OracleTimeStamp` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
