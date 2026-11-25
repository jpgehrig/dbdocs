This method converts the current `OracleTimeStampLTZ` structure to an `OracleDate` structure.

### Declaration

    // C#
    public OracleDate ToOracleDate();

### Return Value

The returned `OracleDate` structure contains the date and time in the current instance.

### Remarks

The precision of the `OracleTimeStampLTZ` value can be lost during the conversion.

If the current instance has a null value, the value of the returned `OracleDate` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)
