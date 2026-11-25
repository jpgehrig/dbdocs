This property specifies the time zone region name or hour offset.

### Declaration

    // C#
    public string TimeZone {get; set;}

### Property Value

The string represents the time zone region name or the time zone offset.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the time zone region name of the local computer

`TimeZone` is only used when the thread constructs one of the `TimeStamp` structures. `TimeZone` has no effect on the session.

`TimeZone` can be either an hour offset, for example, 7:00, or a valid time zone region name that is provided in `V$TIMEZONE_NAMES`, such as US/Pacific. Time zone abbreviations are not supported.

**Note:**

PST is a time zone region name as well as a time zone abbreviation; therefore it is accepted by `OracleGlobalization`.

This property returns an empty string if the `OracleGlobalization` object is obtained using `GetSessionInfo()` or `GetSessionInfo(OracleGlobalization)`. Initially, by default, the time zone of the session is identical to the time zone of the thread. Therefore, given that the session time zone is not changed by invoking `ALTER` `SESSION` calls, the session time zone can be fetched from the client's globalization settings.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
