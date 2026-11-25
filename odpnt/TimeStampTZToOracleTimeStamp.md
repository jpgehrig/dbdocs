This method converts the current `OracleTimeStampTZ` structure to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public OracleTimeStamp ToOracleTimeStamp();

### Return Value

The returned `OracleTimeStamp` contains the date and time in the current instance, but the time zone information is truncated.

### Remarks

If the value of the current instance has a null value, the value of the returned `OracleTimeStamp` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
