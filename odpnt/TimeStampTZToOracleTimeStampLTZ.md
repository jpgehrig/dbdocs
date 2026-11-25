This method converts the current `OracleTimeStampTZ` structure to an `OracleTimeStampLTZ` structure.

### Declaration

    // C#
    public OracleTimeStampLTZ ToOracleTimeStampLTZ();

### Return Value

The returned `OracleTimeStampLTZ` structure contains the date and time, which is normalized to the client local time zone, in the current instance.

### Remarks

If the value of the current instance has a null value, the value of the returned `OracleTimeStampLTZ` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
