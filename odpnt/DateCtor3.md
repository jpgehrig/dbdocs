This constructor creates a new instance of the `OracleDate` structure and set its value for date using the supplied year, month, and day.

### Declaration

    // C#
    public OracleDate (int year, int month, int day);

### Parameters

- `year`

  The supplied year. Range of `year` is (-4712 to 9999).

- `month`

  The supplied month. Range of `month` is (1 to 12).

- `day`

  The supplied day. Range of `day` is (1 to 31).

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleDate` (that is, the day is out of range for the month).

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
