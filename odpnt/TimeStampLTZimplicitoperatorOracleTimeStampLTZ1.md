This static type conversion operator converts an `OracleDate` value to an `OracleTimeStampLTZ` structure.

### Declaration

    // C#
    public static implicit operator OracleTimeStampLTZ(OracleDate value1);

### Parameters

- `value1`

  An `OracleDate`.

### Return Value

The returned `OracleTimeStampLTZ` structure contains the date and time in the `OracleDate` structure.

### Remarks

If the `OracleDate` structure has a null value, the returned `OracleTimeStampLTZ` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
