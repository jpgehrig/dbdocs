This constructor creates a new instance of the `OracleDate` structure and set its value for time using the supplied year, month, day, hour, minute, and second.

### Declaration

    // C#
    public OracleDate (int year, int month, int day, int hour, int minute, int second);

### Parameters

- `year`

  The supplied year. Range of `year` is (-4712 to 9999).

- `month`

  The supplied month. Range of `month` is (1 to 12).

- `day`

  The supplied day. Range of `day` is (1 to 31).

- `hour`

  The supplied hour. Range of `hour` is (0 to 23).

- `minute`

  The supplied minute. Range of `minute` is (0 to 59).

- `second`

  The supplied second. Range of `second` is (0 to 59).

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleDate` (that is, the day is out of range for the month).

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)
