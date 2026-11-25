This constructor creates a new instance of the `OracleTimeStamp` structure and sets its value for date and time using year, month, day, hour, minute, second, and millisecond.

### Declaration

    // C#
    public OracleTimeStamp(int year, int month, int day, int hour,
       int minute,  int second, double millisecond);


### Parameters

- `year`

  The year provided. Range of `year` is (-4712 to 9999).

- `month`

  The month provided. Range of `month` is (1 to 12).

- `day`

  The day provided. Range of `day` is (1 to 31).

- `hour`

  The hour provided. Range of `hour` is (0 to 23).

- `minute`

  The minute provided. Range of `minute` is (0 to 59).

- `second`

  The second provided. Range of `second` is (0 to 59).

- `milliSeconds`

  The milliseconds provided. Range of `millisecond` is (0 to 999.999999).

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleTimeStamp` (that is, the day is out of range for the month).

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)
