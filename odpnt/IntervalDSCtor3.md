This constructor creates a new instance of the `OracleIntervalDS` structure and sets its value using the total number of days.

### Declaration

    // C#
    public OracleIntervalDS(double totalDays);

### Parameters

- `totalDays`

  The supplied total number of days for a time interval. Range of days is -1000,000,000 \< `totalDays` \< 1000,000,000.

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleIntervalDS`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
