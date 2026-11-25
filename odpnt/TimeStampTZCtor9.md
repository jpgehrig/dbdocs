This constructor creates a new instance of the `OracleTimeStampTZ` structure and sets its value for date and time using year, month, day, hour, minute, second, millisecond, and time zone data.

### Declaration

    // C#
    public OracleTimeStampTZ(int year, int month, int day, int hour,
      int minute,   int second, double millisecond, string timeZone);

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

- `millisecond`

  The millisecond provided. Range of `millisecond` is (0 to 999.999999).

- `timeZone`

  The time zone data provided.

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleTimeStampTZ` (that is, the day is out of range for the month or the time zone is invalid).

### Remarks

`timeZone` can be either an hour offset, for example, 7:00, or a valid time zone region name that is provided in `V$TIMEZONE_NAMES`, such as US/Pacific. Time zone abbreviations are not supported.

If time zone is null, the `OracleGlobalization.TimeZone` of the thread is used.

**Note:**

PST is a time zone region name as well as a time zone abbreviation; therefore it is accepted by `OracleTimeStampTZ`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)
