This method converts the current `OracleTimeStampTZ` structure to an `OracleDate` structure.

### Declaration

    // C#
    public OracleDate ToOracleDate();

### Return Value

The returned `OracleDate` contains the date and time in the current instance, but the time zone information in the current instance is truncated

### Remarks

The precision of the `OracleTimeStampTZ` value can be lost during the conversion, and the time zone information in the current instance is truncated.

If the current instance has a null value, the value of the returned `OracleDate` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
