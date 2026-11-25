This constructor creates a new instance of the `OracleIntervalDS` structure and sets its value using the supplied days, hours, minutes, seconds, and nanoseconds.

### Declaration

    // C#
    public OracleIntervalDS (int days, int hours, int minutes, int seconds,
       int nanoseconds);

### Parameters

- `days`

  The days provided. Range of day is (-999,999,999 to 999,999,999).

- `hours`

  The hours provided. Range of hour is (-23 to 23).

- `minutes`

  The minutes provided. Range of minute is (-59 to 59).

- `seconds`

  The seconds provided. Range of second is (-59 to 59).

- `nanoseconds`

  The nanoseconds provided. Range of nanosecond is (-999,999,999 to 999,999,999)

### Exceptions

`ArgumentOutOfRangeException` - The argument value for one or more of the parameters is out of the specified range.

`ArgumentException` - The argument values of the parameters cannot be used to construct a valid `OracleIntervalDS`.

### Remarks

The sign of all the arguments must be the same.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)

- [OracleIntervalDS Members](IntervalDSMembers.md)
