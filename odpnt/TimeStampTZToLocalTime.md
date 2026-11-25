This method converts the current `OracleTimeStampTZ` instance to local time.

### Declaration

    // C#
    public OracleTimeStampLTZ ToLocalTime();

### Return Value

An `OracleTimeStampLTZ` that contains the date and time, which is normalized to the client local time zone, in the current instance.

### Remarks

If the current instance has a null value, the returned `OracleTimeStampLTZ` has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
