This method creates a new instance of the `OracleIntervalYM` structure and sets its value using the total number of years.

### Declaration

    // C#
    public OracleIntervalYM (double totalYears);

### Parameters

- `totalYears`

  Number of total years. Range is -1,000,000,000 \< `totalYears` \> 1,000,000,000.

### Exceptions

`ArgumentOutOfRangeException` - The `totalYears` parameter is out of the specified range.

`ArgumentException` - The `totalYears` parameter cannot be used to construct a valid `OracleIntervalYM`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
