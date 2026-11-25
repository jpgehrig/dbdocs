This method creates a new instance of the `OracleIntervalYM` structure and sets its value using years and months.

### Declaration

    // C#
    public OracleIntervalYM (int years, int months);

### Parameters

- `years`

  Number of years. Range of year is (-999,999,999 to 999,999,999).

- `months`

  Number of months. Range of month is (-11 to 11).

### Remarks

The sign of all the arguments must be the same.

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleIntervalYM`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)

- [OracleIntervalYM Members](IntervalYMMembers.md)
