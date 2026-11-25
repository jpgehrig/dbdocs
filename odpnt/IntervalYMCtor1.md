This method creates a new instance of the `OracleIntervalYM` structure using the supplied total number of months for a period of time.

### Declaration

    // C#
    public OracleIntervalYM (long totalMonths);

### Parameters

- `totalMonths`

  The number of total months for a time interval. Range is -12,000,000,000 \< `totalMonths` \< 12,000,000,000.

### Exceptions

`ArgumentOutOfRangeException` - The `totalMonths` parameter is out of the specified range.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
