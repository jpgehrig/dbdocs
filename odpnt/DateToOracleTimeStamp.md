This method converts the current `OracleDate` structure to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public OracleTimeStamp ToOracleTimeStamp();

### Return Value

An `OracleTimeStamp` structure.

### Remarks

The returned `OracleTimeStamp` structure has date and time in the current instance.

If the `OracleDate` instance has a null value, the returned `OracleTimeStamp` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
