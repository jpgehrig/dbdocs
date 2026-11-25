This method converts the current `OracleTimeStampLTZ` structure to an `OracleTimeStampTZ` structure.

### Declaration

    // C#
    public OracleTimeStampTZ ToOracleTimeStampTZ();

### Return Value

The returned `OracleTimeStampTZ` contains the date and time of the current instance, with the time zone set to the `OracleGlobalization.TimeZone` from the thread.

### Remarks

If the current instance has a null value, the value of the returned `OracleTimeStampTZ` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
