This method creates a new instance of the `OracleIntervalYM` structure and sets its value using the supplied string.

### Declaration

    // C#
    public OracleIntervalYM (string intervalStr);

### Parameters

- `intervalStr`

  A string representing the Oracle `INTERVAL` `YEAR` `TO` `MONTH`.

### Remarks

The value specified in the supplied `intervalStr` must be in Year-Month format.

### Exceptions

`ArgumentException` - The `intervalStr` parameter is not in the valid format or `intervalStr` has an invalid value.

`ArgumentNullException` - The `intervalStr` parameter is null.

### Example

"1-2" means 1 year and 2 months.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
