This method converts the current `OracleTimeStamp` structure to an `OracleDate` structure.

### Declaration

    // C#
    public OracleDate ToOracleDate();

### Return Value

The returned `OracleDate` contains the date and time in the current instance.

### Remarks

The precision of the `OracleTimeStamp` value can be lost during the conversion.

If the value of the `OracleTimeStamp` has a null value, the value of the returned `OracleDate` structure has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
