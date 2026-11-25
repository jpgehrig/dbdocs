This method converts an `OracleTimeStamp` structure to an `OracleDate` structure.

### Declaration

    // C#
    public explicit operator OracleDate(OracleTimeStamp ts);

### Parameters

- `ts`

  `OracleTimeStamp`

### Return Value

The returned `OracleDate` structure contains the date and time in the `OracleTimeStamp` structure.

### Remarks

The precision of the `OracleTimeStamp` value can be lost during the conversion.

If the `OracleTimeStamp` structure has a null value, the returned `OracleDate` structure also has a null value.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
