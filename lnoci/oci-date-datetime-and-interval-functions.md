Lists and describes the OCI date and interval functions.

Table 28-4 describes the OCI date and interval functions that are described in this section.

Table 28-4 Date Functions

| Function                       | Purpose                                                                                                             |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| OCIDateAddDays()               | Add or subtract days                                                                                                |
| OCIDateAddMonths()             | Add or subtract months                                                                                              |
| OCIDateAssign()                | Assign date                                                                                                         |
| OCIDateCheck()                 | Check if the given date is valid                                                                                    |
| OCIDateCompare()               | Compare dates                                                                                                       |
| OCIDateDaysBetween()           | Get number of days between two dates                                                                                |
| OCIDateFromText()              | Convert string to date                                                                                              |
| OCIDateGetDate()               | Get the date portion of a date                                                                                      |
| OCIDateGetTime()               | Get the time portion of a date                                                                                      |
| OCIDateLastDay()               | Get date of last day of month                                                                                       |
| OCIDateNextDay()               | Get date of next day                                                                                                |
| OCIDateSetDate()               | Set the date portion of a date                                                                                      |
| OCIDateSetTime()               | Set the time portion of a date                                                                                      |
| OCIDateSysDate()               | Get the current system date and time                                                                                |
| OCIDateTimeAssign()            | Perform a datetime assignment                                                                                       |
| OCIDateTimeCheck()             | Check if the given date is valid                                                                                    |
| OCIDateTimeCompare()           | Compare two datetime values                                                                                         |
| OCIDateTimeConstruct()         | Construct a datetime descriptor                                                                                     |
| OCIDateTimeConvert()           | Convert one datetime type to another                                                                                |
| OCIDateTimeFromArray()         | Convert an array of size `OCI_DT_ARRAYLEN` to an `OCIDateTime `descriptor                                           |
| OCIDateTimeFromText()          | Convert the given string to Oracle datetime type in the `OCIDateTime` descriptor, according to the specified format |
| OCIDateTimeGetDate()           | Get the date (year, month, day) portion of a datetime value                                                         |
| OCIDateTimeGetTime()           | Get the time (hour, min, second, fractional second) of a datetime value                                             |
| OCIDateTimeGetTimeZoneName()   | Get the time zone name portion of a datetime value                                                                  |
| OCIDateTimeGetTimeZoneOffset() | Get the time zone (hour, minute) portion of a datetime value                                                        |
| OCIDateTimeIntervalAdd()       | Add an interval to a datetime to produce a resulting datetime                                                       |
| OCIDateTimeIntervalSub()       | Subtract an interval from a datetime and store the result in a datetime                                             |
| OCIDateTimeSubtract()          | Take two datetimes as input and store their difference in an interval                                               |
| OCIDateTimeSysTimeStamp()      | Get the system current date and time as a time stamp with time zone                                                 |
| OCIDateTimeToArray()           | Convert an `OCIDateTime` descriptor to an array                                                                     |
| OCIDateTimeToText()            | Convert the given date to a string according to the specified format                                                |
| OCIDateToText()                | Convert date to string                                                                                              |
| OCIDateZoneToZone()            | Convert date from one time zone to another zone                                                                     |
| OCIIntervalAdd()               | Add two intervals to produce a resulting interval                                                                   |
| OCIIntervalAssign()            | Copy one interval to another                                                                                        |
| OCIIntervalCheck()             | Check the validity of an interval                                                                                   |
| OCIIntervalCompare()           | Compare two intervals                                                                                               |
| OCIIntervalDivide()            | Divide an interval by an Oracle `NUMBER` to produce an interval                                                     |
| OCIIntervalFromNumber()        | Convert an Oracle `NUMBER` to an interval                                                                           |
| OCIIntervalFromText()          | When given an interval string, return the interval represented by the string                                        |
| OCIIntervalFromTZ()            | Return an `OCI_DTYPE_INTERVAL_DS`                                                                                   |
| OCIIntervalGetDaySecond()      | Get values of day, hour, minute, and second from an interval                                                        |
| OCIIntervalGetYearMonth()      | Get year and month from an interval                                                                                 |
| OCIIntervalMultiply()          | Multiply an interval by an Oracle `NUMBER` to produce an interval                                                   |
| OCIIntervalSetDaySecond()      | Set day, hour, minute, and second in an interval                                                                    |
| OCIIntervalSetYearMonth()      | Set year and month in an interval                                                                                   |
| OCIIntervalSubtract()          | Subtract two intervals and stores the result in an interval                                                         |
| OCIIntervalToNumber()          | Convert an interval to an Oracle NUMBER                                                                             |
| OCIIntervalToText()            | When given an interval, produce a string representing the interval                                                  |

### 28.3.1 OCIDateAddDays()

Adds or subtracts days from a given date.

#### Purpose

Adds or subtracts days from a given date.

#### Syntax

    sword OCIDateAddDays ( OCIError          *err,
                           const OCIDate     *date,
                           sb4                num_days,
                           OCIDate           *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
he given date from which to add or subtract.

num_days (IN)
Number of days to be added or subtracted. A negative value is subtracted.

result (IN/OUT)
Result of adding days to, or subtracting days from, `date`.

#### Returns

This function returns an error if an invalid date is passed to it.

**Related Topics**

- OCIDateAddMonths()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.2 OCIDateAddMonths()

Adds or subtracts months from a given date.

#### Purpose

Adds or subtracts months from a given date.

#### Syntax

    sword OCIDateAddMonths ( OCIError            *err,
                             const OCIDate       *date,
                             sb4                  num_months,
                             OCIDate             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
The given date from which to add or subtract.

num_months (IN)
Number of months to be added or subtracted. A negative value is subtracted.

result (IN/OUT)
Result of adding days to, or subtracting days from, `date`.

#### Comments

If the input `date` is the last day of a month, then the appropriate adjustments are made to ensure that the output date is also the last day of the month. For example, Feb. 28 + 1 month = March 31, and November 30 – 3 months = August 31. Otherwise the `result` date has the same day component as `date`.

#### Returns

This function returns an error if an invalid date is passed to it.

**Related Topics**

- OCIDateAddDays()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.3 OCIDateAssign()

Performs a date assignment.

#### Purpose

Performs a date assignment.

#### Syntax

    sword OCIDateAssign ( OCIError         *err,
                          const OCIDate    *from,
                          OCIDate          *to );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

from (IN)
Date to be assigned.

to (OUT)
Target of assignment.

#### Comments

This function assigns a value from one `OCIDate` variable to another.

**Related Topics**

- OCIDateCheck()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.4 OCIDateCheck()

Checks if the given date is valid.

#### Purpose

Checks if the given date is valid.

#### Syntax

    sword OCIDateCheck ( OCIError          *err,
                         const OCIDate     *date,
                         uword             *valid );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
Date to be checked.

valid (OUT)
Returns zero for a valid date; otherwise, it returns the logical operator OR combination of all error bits specified in Table 28-5.

Table 28-5 Error Bits Returned by the valid Parameter for OCIDateCheck()

| Macro Name                       | Bit Number | Error                                 |
|:---------------------------------|:-----------|:--------------------------------------|
| `OCI_DATE_INVALID_DAY`           | 0x1        | Bad day                               |
| `OCI_DATE_DAY_BELOW_VALID`       | 0x2        | Bad day low/high bit (1=low)          |
| `OCI_DATE_INVALID_MONTH`         | 0x4        | Bad month                             |
| `OCI_DATE_MONTH_BELOW_VALID`     | 0x8        | Bad month low/high bit (1=low)        |
| `OCI_DATE_INVALID_YEAR`          | 0x10       | Bad year                              |
| `OCI_DATE_YEAR_BELOW_VALID`      | 0x20       | Bad year low/high bit (1=low)         |
| `OCI_DATE_INVALID_HOUR`          | 0x40       | Bad hour                              |
| `OCI_DATE_HOUR_BELOW_VALID`      | 0x80       | Bad hour low/high bit (1=low)         |
| `OCI_DATE_INVALID_MINUTE`        | 0x100      | Bad minute                            |
| `OCI_DATE_MINUTE_BELOW_VALID`    | 0x200      | Bad minute low/high bit (1=low)       |
| `OCI_DATE_INVALID_SECOND`        | 0x400      | Bad second                            |
| `OCI_DATE_SECOND_BELOW_VALID`    | 0x800      | Bad second low/high bit (1=low)       |
| `OCI_DATE_DAY_MISSING_FROM_1582` | 0x1000     | Day is one of those missing from 1582 |
| `OCI_DATE_YEAR_ZERO`             | 0x2000     | Year may not equal zero               |
| `OCI_DATE_INVALID_FORMAT`        | 0x8000     | Bad date format input                 |

For example, if the date passed in was 2/0/1990 25:61:10 in (month/day/year hours:minutes:seconds format), the error returned is:

    OCI_DATE_INVALID_DAY | OCI_DATE_DAY_BELOW_VALID | OCI_DATE_INVALID_HOUR |
       OCI_DATE_INVALID_MINUTE.

#### Returns

This function returns an error if `date` or `valid` pointer is `NULL`.

**Related Topics**

- OCIDateCompare()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.5 OCIDateCompare()

Compares two dates.

#### Purpose

Compares two dates.

#### Syntax

    sword OCIDateCompare ( OCIError           *err,
                           const OCIDate      *date1,
                           const OCIDate      *date2,
                           sword              *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date1, date2 (IN)
Dates to be compared.

result (OUT)
Comparison result as listed in Table 28-6.

Table 28-6 Comparison Results

| Comparison Result  | Output in result Parameter |
|:-------------------|:---------------------------|
| `date1` \<` date2` | -1                         |
| `date1` = `date2`  | 0                          |
| `date1` \> `date2` | 1                          |

#### Returns

This function returns an error if an invalid date is passed to it.

**Related Topics**

- OCIDateCheck()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.6 OCIDateDaysBetween()

Gets the number of days between two dates.

#### Purpose

Gets the number of days between two dates.

#### Syntax

    sword OCIDateDaysBetween ( OCIError            *err,
                               const OCIDate       *date1,
                               const OCIDate       *date2,
                               sb4                 *num_days );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date1 (IN)
Input date.

date2 (IN)
Input date.

num_days (OUT)
Number of days between `date1` and `date2`.

#### Comments

When the number of days between `date1` and `date2` is computed, the time is ignored.

#### Returns

This function returns an error if an invalid date is passed to it.

**Related Topics**

- OCIDateCheck()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.7 OCIDateFromText()

Converts a character string to a date type according to the specified format.

#### Purpose

Converts a character string to a date type according to the specified format.

#### Syntax

    sword OCIDateFromText ( OCIError           *err,
                            const OraText      *date_str,
                            ub4                 d_str_length,
                            const OraText      *fmt,
                            ub1                 fmt_length,
                            const OraText      *lang_name,
                            ub4                 lang_length,
                            OCIDate            *date );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date_str (IN)
Input string to be converted to Oracle date.

d_str_length (IN)
Size of the input string. If the length is –1, then `date_str` is treated as a `NULL`-terminated string.

fmt (IN)
Conversion format. If `fmt` is a `NULL` pointer, then the string is expected to be in "DD-MON-YY" format.

fmt_length (IN)
Length of the `fmt` parameter.

lang_name (IN)
Language in which the names and abbreviations of days and months are specified. If `lang_name` is a `NULL` string, `(text *)0`, then the default language of the session is used.

lang_length (IN)
Length of the `lang_name` parameter.

date (OUT)
Given string converted to date.

#### Comments

See the `TO_DATE` conversion function described in the [Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md)for a description of format and multilingual arguments.

#### Returns

This function returns an error if it receives an invalid format, language, or input string.

**Related Topics**

- OCIDateToText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.8 OCIDateGetDate()

Gets the year, month, and day stored in an Oracle date.

#### Purpose

Gets the year, month, and day stored in an Oracle date.

#### Syntax

    void OCIDateGetDate ( const OCIDate    *date,
                          sb2              *year,
                          ub1              *month,
                          ub1              *day );

#### Parameters

date (IN)
Oracle date whose year, month, day data is retrieved.

year (OUT)
Year value returned.

month (OUT)
Month value returned.

day (OUT)
Day value returned.

#### Comments

None.

**Related Topics**

- OCIDateSetDate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.9 OCIDateGetTime()

Gets the time stored in an Oracle date.

#### Purpose

Gets the time stored in an Oracle date.

#### Syntax

    void OCIDateGetTime ( const OCIDate    *date,
                          ub1              *hour,
                          ub1              *min,
                          ub1              *sec );

#### Parameters

date (IN)
Oracle date whose time data is retrieved.

hour (OUT)
Hour value returned.

min (OUT)
Minute value returned.

sec (OUT)
Second value returned.

#### Returns

Returns the time information in the form: hour, minute and seconds.

**Related Topics**

- OCIDateSetTime()
- OCIDateGetDate()

### 28.3.10 OCIDateLastDay()

Gets the date of the last day of the month in a specified date.

#### Purpose

Gets the date of the last day of the month in a specified date.

#### Syntax

    sword OCIDateLastDay ( OCIError            *err,
                           const OCIDate       *date,
                           OCIDate             *last_day );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
Input date.

last_day (OUT)
Last day of the month in `date`.

#### Returns

This function returns an error if an invalid date is passed to it.

**Related Topics**

- OCIDateGetDate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.11 OCIDateNextDay()

Gets the date of the next day of the week after a given date.

#### Purpose

Gets the date of the next day of the week after a given date.

#### Syntax

    sword OCIDateNextDay ( OCIError            *err,
                           const OCIDate       *date,
                           const OraText       *day,
                           ub4                  day_length,
                           OCIDate             *next_day );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
Returned date should be later than this date.

day (IN)
First day of the week named by this is returned.

day_length (IN)
Length in bytes of string `day`.

next_day (OUT)
First day of the week named by `day` that is later than `date`.

#### Returns

Returns the date of the first day of the week named by `day` that is later than `date`.

#### Example

The following code example shows how to get the date of the next Monday after April 18, 1996 (a Thursday).

Getting the Date for a Specific Day After a Specified Date

    OCIDate one_day, next_day;
    /* Add code here to set one_day to be '18-APR-96' */
    OCIDateNextDay(err, &one_day, "MONDAY", strlen("MONDAY"), &next_day);

`OCIDateNextDay()` returns "22-APR-96".

This function returns an error if an invalid date or day is passed to it.

**Related Topics**

- OCIDateGetDate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.12 OCIDateSetDate()

Set the values in an Oracle date.

#### Purpose

Set the values in an Oracle date.

#### Syntax

    void OCIDateSetDate ( OCIDate    *date,
                          sb2         year,
                          ub1         month,
                          ub1         day );

#### Parameters

date (OUT)
Oracle date whose time data is set.

year (IN)
Year value to be set.

month (IN)
Month value to be set.

day (IN)
Day value to be set.

#### Comments

None.

**Related Topics**

- OCIDateGetDate()

### 28.3.13 OCIDateSetTime()

Sets the time information in an Oracle date.

#### Purpose

Sets the time information in an Oracle date.

#### Syntax

    void OCIDateSetTime ( OCIDate    *date,
                          ub1         hour,
                          ub1         min,
                          ub1         sec );

#### Parameters

date (OUT)
Oracle date whose time data is set.

hour (IN)
Hour value to be set.

min (IN)
Minute value to be set.

sec (IN)
Second value to be set.

#### Comments

None.

**Related Topics**

- OCIDateGetTime()

### 28.3.14 OCIDateSysDate()

Gets the current system date and time of the client.

#### Purpose

Gets the current system date and time of the client.

#### Syntax

    sword OCIDateSysDate ( OCIError       *err,
                           OCIDate        *sys_date );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sys_date (OUT)
Current system date and time of the client.

#### Comments

None.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.15 OCIDateTimeAssign()

Performs a datetime assignment.

#### Purpose

Performs a datetime assignment.

#### Syntax

    sword OCIDateTimeAssign ( void                *hndl,
                              OCIError            *err,
                              const OCIDateTime   *from,
                              OCIDateTime         *to );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle. If a user session handle is passed, the conversion occurs in the session's `NLS_LANGUAGE` and the session's `NLS_CALENDAR`; otherwise, the default is used.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

from (IN)
Source, right-hand side (`rhs`) datetime to be assigned.

to (OUT)
Target, left-hand side (`lhs`) of assignment.

#### Comments

This function performs an assignment from the `from` datetime to the `to` datetime for any of the datetime types listed in the description of the `type` parameter.

The `type` of the output is the same as that of the input.

#### Returns

`OCI_SUCCESS`; or OCI_ERROR.

**Related Topics**

- OCIDateTimeCheck()
- OCIDateTimeConstruct()

### 28.3.16 OCIDateTimeCheck()

Checks if the given date is valid.

#### Purpose

Checks if the given date is valid.

#### Syntax

    sword OCIDateTimeCheck ( void                *hndl,
                             OCIError            *err,
                             const OCIDateTime   *date,
                             ub4                 *valid );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle. If a user session handle is passed, the conversion occurs in the session's `NLS_LANGUAGE` and the session's `NLS_CALENDAR`, otherwise, the default is used.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
The date to be checked.

valid (OUT)
Returns zero for a valid date; otherwise, it returns the logical operator OR combination of all the error bits specified in Table 28-7.

Table 28-7 Error Bits Returned by the valid Parameter for OCIDateTimeCheck()

| Macro Name                     | Bit Number | Error                                 |
|:-------------------------------|:-----------|:--------------------------------------|
| `OCI_DT_INVALID_DAY`           | 0x1        | Bad day                               |
| `OCI_DT_DAY_BELOW_VALID`       | 0x2        | Bad day low/high bit (1=low)          |
| `OCI_DT_INVALID_MONTH`         | 0x4        | Bad month                             |
| `OCI_DT_MONTH_BELOW_VALID`     | 0x8        | Bad month low/high bit (1=low)        |
| `OCI_DT_INVALID_YEAR`          | 0x10       | Bad year                              |
| `OCI_DT_YEAR_BELOW_VALID`      | 0x20       | Bad year low/high bit (1=low)         |
| `OCI_DT_INVALID_HOUR`          | 0x40       | Bad hour                              |
| `OCI_DT_HOUR_BELOW_VALID`      | 0x80       | Bad hour low/high bit (1=low)         |
| `OCI_DT_INVALID_MINUTE`        | 0x100      | Bad minute                            |
| `OCI_DT_MINUTE_BELOW_VALID`    | 0x200      | Bad minute low/high bit (1=low)       |
| `OCI_DT_INVALID_SECOND`        | 0x400      | Bad second                            |
| `OCI_DT_SECOND_BELOW_VALID`    | 0x800      | Bad second low/high bit (1=low)       |
| `OCI_DT_DAY_MISSING_FROM_1582` | 0x1000     | Day is one of those missing from 1582 |
| `OCI_DT_YEAR_ZERO`             | 0x2000     | Year may not equal zero               |
| `OCI_DT_INVALID_TIMEZONE`      | 0x4000     | Bad time zone                         |
| `OCI_DT_INVALID_FORMAT`        | 0x8000     | Bad date format input                 |

So, for example, if the date passed in was 2/0/1990 25:61:10 in (month/day/year hours:minutes:seconds format), the error returned is:

     OCI_DT_INVALID_DAY | OCI_DT_DAY_BELOW_VALID |
         OCI_DT_INVALID_HOUR | OCI_DT_INVALID_MINUTE.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if err is a `NULL` pointer; `OCI_ERROR`, if `date` or `valid` is a `NULL` pointer.

**Related Topics**

- OCIDateTimeAssign()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.17 OCIDateTimeCompare()

Compares two datetime values.

#### Purpose

Compares two datetime values.

#### Syntax

    sword OCIDateTimeCompare ( void               *hndl,
                               OCIError           *err,
                               const OCIDateTime  *date1,
                               const OCIDateTime  *date2,
                               sword              *result );

#### Parameters

hndl (IN/OUT)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date1, date2 (IN)
Dates to be compared.

result (OUT)
Comparison result as listed in Table 28-8.

Table 28-8 Comparison Results Returned by the result Parameter for OCIDateTimeCompare()

| Comparison Result  | Output in result Parameter |
|:-------------------|:---------------------------|
| `date1` \< `date2` | -1                         |
| `date1` = `date2`  | 0                          |
| `date1` \> `date2` | 1                          |

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if err is a `NULL` pointer; `OCI_ERROR`, if an invalid date is used or if the input date arguments are not of mutually comparable types.

**Related Topics**

- OCIDateTimeConstruct()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.18 OCIDateTimeConstruct()

Constructs a datetime descriptor.

#### Purpose

Constructs a datetime descriptor.

#### Syntax

    sword OCIDateTimeConstruct ( void          *hndl,
                                 OCIError      *err,
                                 OCIDateTime   *datetime,
                                 sb2            year,
                                 ub1            month,
                                 ub1            day,
                                 ub1            hour,
                                 ub1            min,
                                 ub1            sec,
                                 ub4            fsec,
                                 OraText       *timezone,
                                 size_t         timezone_length );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime `descriptor.

year (IN)
Year value.

month (IN)
Month value.

day (IN)
Day value.

hour (IN)
Hour value.

min (IN)
Minute value.

sec (IN)
Second value.

fsec (IN)
Fractional second value.

timezone (IN)
Time zone string. A string representation of time zone displacement is the difference (in hours and minutes) between local time and UTC (Coordinated Universal Time—formerly Greenwich Mean Time) in the format "\[+\|-\]\[HH:MM\]". For example, "-08:00".

timezone_length (IN)
Length of the time zone string.

#### Comments

The type of the datetime is the type of the `OCIDateTime` descriptor. Only the relevant fields based on the type are used. For types with a time zone, the date and time fields are assumed to be in the local time of the specified time zone.

If the time zone is not specified, then the session default time zone is assumed.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`, if datetime is not valid.

**Related Topics**

- OCIDateTimeAssign()
- OCIDateTimeConvert()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.19 OCIDateTimeConvert()

Converts one datetime type to another.

#### Purpose

Converts one datetime type to another.

#### Syntax

    sword OCIDateTimeConvert ( void         *hndl,
                               OCIError     *err,
                               OCIDateTime  *indate,
                               OCIDateTime  *outdate );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

indate (IN)
A pointer to the input date.

outdate (OUT)
A pointer to the output datetime.

#### Comments

This function converts one datetime type to another. The result type is the type of the `outdate` descriptor. The session default time zone (`ORA_SDTZ`) is used when converting a datetime without a time zone to one with a time zone.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE` if `err` is `NULL`; or `OCI_ERROR`, if the conversion is not possible with the given input values.

**Related Topics**

- OCIDateTimeCheck()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.20 OCIDateTimeFromArray()

Converts an array containing a date to an `OCIDateTime `descriptor.

#### Purpose

Converts an array containing a date to an `OCIDateTime `descriptor.

#### Syntax

    sword OCIDateTimeFromArray ( void               *hndl,
                                 OCIError           *err,
                                 const ub1          *inarray,
                                 ub4                *len
                                 ub1                 type,
                                 OCIDateTime        *datetime,
                                 const OCIInterval  *reftz,
                                 ub1                 fsprec );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inarray(IN)
Array of ub1, containing the date.

len (IN)
Length of `inarray`.

type (IN)
Type of the resulting datetime. The array is converted to the specific SQLT type.

datetime (OUT)
Pointer to an `OCIDateTime` descriptor.

reftz (IN)
Descriptor for `OCIInterval` used as a reference when converting a `SQLT_TIMESTAMP_LT``Z` type.

fsprec (IN)
Fractional second precision of the resulting datetime.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR` if `type` is invalid.

**Related Topics**

- OCIDateTimeFromText()
- OCIDateTimeToArray()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.21 OCIDateTimeFromText()

Converts the given string to an Oracle datetime type in the `OCIDateTime` descriptor, according to the specified format.

#### Purpose

Converts the given string to an Oracle datetime type in the `OCIDateTime` descriptor, according to the specified format.

#### Syntax

    sword OCIDateTimeFromText ( void               *hndl,
                                OCIError           *err,
                                const OraText      *date_str,
                                size_t              dstr_length,
                                const OraText      *fmt,
                                ub1                 fmt_length,
                                const OraText      *lang_name,
                                size_t              lang_length,
                                OCIDateTime        *datetime );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle. If a user session handle is passed, the conversion occurs in the session's NLS_LANGUAGE and the session's NLS_CALENDAR; otherwise, the default is used.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date_str (IN)
The input string to be converted to an Oracle datetime.

dstr_length (IN)
The size of the input string. If the length is –1, then `date_str` is treated as a `NULL`-terminated string.

fmt (IN)
The conversion format. If `fmt` is a `NULL` pointer, then the string is expected to be in the default format for the datetime type.

fmt_length (IN)
The length of the `fmt` parameter.

lang_name (IN)
Specifies the language in which the names and abbreviations of months and days are specified. The default language of the session is used if `lang_name` is `NULL` (`lang_name` = `(text *)0`).

lang_length (IN)
The length of the `lang_name` parameter.

datetime (OUT)
The given string converted to a date.

#### Comments

See the description of the `TO_DATE` conversion function in the [Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md) for a description of the format argument.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE` if `err` is `NULL`; or `OCI_ERROR`, if any of the following is true:

- An invalid format is used.

- An unknown language is used.

- An invalid input string is used.

**Related Topics**

- OCIDateTimeToText()
- OCIDateTimeFromArray()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.22 OCIDateTimeGetDate()

Gets the date (year, month, day) portion of a datetime value.

#### Purpose

Gets the date (year, month, day) portion of a datetime value.

#### Syntax

    sword OCIDateTimeGetDate ( void               *hndl,
                               OCIError           *err,
                               const OCIDateTime  *datetime,
                               sb2                *year,
                               ub1                *month,
                               ub1                *day );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime` descriptor from which date information is retrieved.

year (OUT)
month (OUT)
day (OUT)
The retrieved year, month, and day values.

#### Comments

This function gets the date (year, month, day) portion of a datetime value.

#### Returns

`OCI_SUCCESS` or `OCI_ERROR`.

**Related Topics**

- OCIDateTimeGetTime()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.23 OCIDateTimeGetTime()

Gets the time (hour, min, second, fractional second) of a datetime value.

#### Purpose

Gets the time (hour, min, second, fractional second) of a datetime value.

#### Syntax

    sword OCIDateTimeGetTime ( void          *hndl,
                               OCIError      *err,
                               OCIDateTime   *datetime,
                               ub1           *hour,
                               ub1           *min,
                               ub1           *sec,
                               ub4           *fsec );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime` descriptor from which time information is retrieved.

hour (OUT)
The retrieved hour value.

min (OUT)
The retrieved minute value.

sec (OUT)
The retrieved second value.

fsec (OUT)
The retrieved fractional second value.

#### Comments

This function gets the time portion (hour, min, second, fractional second) from a given datetime value.

This function returns an error if the given datetime does not contain time information.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`, if datetime does not contain time (`SQLT_DATE`).

**Related Topics**

- OCIDateTimeGetDate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.24 OCIDateTimeGetTimeZoneName()

Gets the time zone name portion of a datetime value.

#### Purpose

Gets the time zone name portion of a datetime value.

#### Syntax

    sword OCIDateTimeGetTimeZoneName ( void               *hndl,
                                       OCIError           *err,
                                       const OCIDateTime  *datetime,
                                       ub1                *buf,
                                       ub4                *buflen, );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime` descriptor.

buf (OUT)
Buffer to store the retrieved time zone name.

buflen (IN/OUT)
The size of the buffer (IN). The size of the name field (OUT)

#### Comments

This function gets the time portion (hour, min, second, fractional second) from a given datetime value.

This function returns an error if the given datetime does not contain time information.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`, if datetime does not contain a time zone (`SQLT_DATE`, `SQLT_TIMESTAMP`).

**Related Topics**

- OCIDateTimeGetDate()
- OCIDateTimeGetTimeZoneOffset()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.25 OCIDateTimeGetTimeZoneOffset()

Gets the time zone (hour, minute) portion of a datetime value.

#### Purpose

Gets the time zone (hour, minute) portion of a datetime value.

#### Syntax

    sword OCIDateTimeGetTimeZoneOffset ( void               *hndl,
                                         OCIError           *err,
                                         const OCIDateTime  *datetime,
                                         sb1                *hour,
                                         sb1                *min, );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime` descriptor.

hour (OUT)
The retrieved time zone hour value.

min (OUT)
The retrieved time zone minute value.

#### Comments

This function gets the time zone hour and the time zone minute portion from a given datetime value.

This function returns an error if the given datetime does not contain time information.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`, if datetime does not contain a time zone (`SQLT_DATE`, `SQLT_TIMESTAMP`).

**Related Topics**

- OCIDateTimeGetDate()
- OCIDateTimeGetTimeZoneName()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.26 OCIDateTimeIntervalAdd()

Adds an interval to a datetime to produce a resulting datetime.

#### Purpose

Adds an interval to a datetime to produce a resulting datetime.

#### Syntax

    sword OCIDateTimeIntervalAdd ( void         *hndl,
                                   OCIError     *err,
                                   OCIDateTime  *datetime,
                                   OCIInterval  *inter,
                                   OCIDateTime  *outdatetime );

#### Parameters

hndl (IN)
The user session or environment handle. If a session handle is passed, the addition occurs in the session default calendar.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to the input datetime.

inter (IN)
Pointer to the input interval.

outdatetime (OUT)
Pointer to the output datetime. The output datetime is of same type as the input datetime.

#### Returns

`OCI_SUCCESS`, if the function completes successfully; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if the resulting date is before Jan 1, -4713 or is after Dec 31, 9999.

**Related Topics**

- OCIDateTimeIntervalSub()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.27 OCIDateTimeIntervalSub()

Subtracts an interval from a datetime and stores the result in a datetime.

#### Purpose

Subtracts an interval from a datetime and stores the result in a datetime.

#### Syntax

    sword OCIDateTimeIntervalSub ( void         *hndl,
                                   OCIError     *err,
                                   OCIDateTime  *datetime,
                                   OCIInterval  *inter,
                                   OCIDateTime  *outdatetime );

#### Parameters

hndl (IN)
The user session or environment handle. If a session handle is passed, the subtraction occurs in the session default calendar. The interval is assumed to be in the session calendar.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to the input datetime value.

inter (IN)
Pointer to the input interval.

outdatetime (OUT)
Pointer to the output datetime. The output datetime is of same type as the input datetime.

#### Returns

`OCI_SUCCESS`, if the function completes successfully; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if the resulting date is before Jan 1, -4713 or is after Dec 31, 9999.

**Related Topics**

- OCIDateTimeIntervalAdd()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.28 OCIDateTimeSubtract()

Takes two datetimes as input and stores their difference in an interval.

#### Purpose

Takes two datetimes as input and stores their difference in an interval.

#### Syntax

    sword OCIDateTimeSubtract ( void         *hndl,
                                OCIError     *err,
                                OCIDateTime  *indate1,
                                OCIDateTime  *indate2,
                                OCIInterval  *inter );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

indate1 (IN)
Pointer to the subtrahend (number to be subtracted).

indate2 (IN)
Pointer to the minuend (number to be subtracted from).

inter (OUT)
Pointer to the output interval.

#### Returns

`OCI_SUCCESS`, if the function completes successfully; `OCI_INVALID_HANDLE` if `err` is `NULL` pointer; or `OCI_ERROR`, if the input datetimes are not of comparable types.

**Related Topics**

- OCIDateTimeCompare()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.29 OCIDateTimeSysTimeStamp()

Gets the system current date and time as a time stamp with time zone.

#### Purpose

Gets the system current date and time as a time stamp with time zone.

#### Syntax

    sword OCIDateTimeSysTimeStamp ( void           *hndl,
                                    OCIError       *err,
                                    OCIDateTime    *sys_date );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sys_date (OUT)
Pointer to the output time stamp.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIDateSysDate()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.30 OCIDateTimeToArray()

Converts an `OCIDateTime` descriptor to an array.

#### Purpose

Converts an `OCIDateTime` descriptor to an array.

#### Syntax

    sword OCIDateTimeToArray ( void               *hndl,
                               OCIError           *err,
                               const OCIDateTime  *datetime,
                               const OCIInterval  *reftz,
                               ub1                *outarray,
                               ub4                *len
                               ub1                 fsprec );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

datetime (IN)
Pointer to an `OCIDateTime` descriptor.

reftz (IN)
Descriptor for the `OCIInterval` used as a reference when converting the `SQL_TIMESTAMP_LTZ` type.

outarray(OUT)
Array of bytes containing the date.

len (OUT)
Length of `outarray`.

fsprec (IN)
Fractional second precision in the array.

#### Comments

The array is allocated by OCI and its length is returned.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`, if datetime is invalid.

**Related Topics**

- OCIDateTimeToText()
- OCIDateTimeFromArray()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.31 OCIDateTimeToText()

Converts the given date to a string according to the specified format.

#### Purpose

Converts the given date to a string according to the specified format.

#### Syntax

    sword OCIDateTimeToText ( void                *hndl,
                              OCIError            *err,
                              const OCIDateTime   *date,
                              const OraText       *fmt,
                              ub1                  fmt_length,
                              ub1                  fsprec,
                              const OraText       *lang_name,
                              size_t               lang_length,
                              ub4                 *buf_size,
                              OraText             *buf );

#### Parameters

hndl (IN)
The OCI user session handle or environment handle. If a user session handle is passed, the conversion occurs in the session's `NLS_LANGUAGE` and the session's `NLS_CALENDAR`; otherwise, the default is used.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
Oracle datetime value to be converted.

fmt (IN)
The conversion format. If it is a `NULL` string pointer, `(text*)0`, then the date is converted to a character string in the default format for that type.

fmt_length (IN)
The length of the `fmt` parameter.

fsprec (IN)
Specifies the precision in which the fractional seconds value is returned.

lang_name (IN)
Specifies the language in which the names and abbreviations of months and days are returned. The default language of the session is used if `lang_name` is `NULL` (`lang_name` = `(OraText *)0`).

lang_length (IN)
The length of the `lang_name` parameter.

buf_size (IN/OUT)
The size of the `buf` buffer (IN).

The size of the resulting string after the conversion (OUT).

buf (OUT)
The buffer into which the converted string is placed.

#### Comments

See the description of the `TO_DATE` conversion function in the [Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md) for a description of format and multilingual arguments. The converted NULL-terminated date string is stored in the buffer `buf`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is `NULL`; or `OCI_ERROR`, if any of the following statements is true:

- The buffer is too small.

- An invalid format is used.

- An unknown language is used.

- There is an overflow error.

**Related Topics**

- OCIDateTimeFromText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.32 OCIDateToText()

Converts a date type to a character string.

#### Purpose

Converts a date type to a character string.

#### Syntax

    sword OCIDateToText ( OCIError                  *err,
                          const OCIDate             *date,
                          const OraText             *fmt,
                          ub1                        fmt_length,
                          const OraText             *lang_name,
                          ub4                        lang_length,
                          ub4                       *buf_size,
                          OraText                   *buf );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date (IN)
Oracle date to be converted.

fmt (IN)
Conversion format. If `NULL`, `(text *)0`, then the date is converted to a character string in the default date format, DD-MON-YY.

fmt_length (IN)
Length of the `fmt` parameter.

lang_name (IN)
Specifies the language in which names and abbreviations of months and days are returned; the default language of the session is used if `lang_name` is `NULL` (`(text *)0`).

lang_length (IN)
Length of the `lang_name` parameter.

buf_size (IN/OUT)
Size of the buffer (IN). Size of the resulting string is returned with this parameter (OUT).

buf (OUT)
Buffer into which the converted string is placed.

#### Comments

Converts the given date to a string according to the specified format. The converted `NULL`-terminated date string is stored in `buf`.

See the `TO_DATE` conversion function described in the [Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md) for a description of format and multilingual arguments.

#### Returns

This function returns an error if the buffer is too small, or if the function is passed an invalid format or unknown language. Overflow also causes an error. For example, converting a value of 10 into format '9' causes an error.

**Related Topics**

- OCIDateFromText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.33 OCIDateZoneToZone()

Converts a date from one time zone to another.

#### Purpose

Converts a date from one time zone to another.

#### Syntax

    sword OCIDateZoneToZone ( OCIError           *err,
                              const OCIDate      *date1,
                              const OraText      *zon1,
                              ub4                 zon1_length,
                              const OraText      *zon2,
                              ub4                 zon2_length,
                              OCIDate            *date2 );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

date1 (IN)
Date to convert.

zon1 (IN)
Zone of the input date.

zon1_length (IN)
Length in bytes of `zon1`.

zon2 (IN)
Zone to be converted to.

zon2_length (IN)
Length in bytes of `zon2`.

date2 (OUT)
Converted date (in `zon2`).

#### Comments

Converts a given date `date1` in time zone `zon1` to a date `date2` in time zone `zon2`. Works only with North American time zones.

For a list of valid zone strings, see the description of the `NEW_TIME` function in the [Oracle Database SQL Language Reference](../sqlrf/NEW_TIME.md). Examples of valid zone strings include:

- AST, Atlantic Standard Time

- ADT, Atlantic Daylight Time

- BST, Bering Standard Time

- BDT, Bering Daylight Time

#### Returns

This function returns an error if an invalid date or time zone is passed to it.

**Related Topics**

- OCIDateCheck()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.34 OCIIntervalAdd()

Adds two intervals to produce a resulting interval.

#### Purpose

Adds two intervals to produce a resulting interval.

#### Syntax

    sword OCIIntervalAdd ( void         *hndl,
                           OCIError     *err,
                           OCIInterval  *addend1,
                           OCIInterval  *addend2,
                           OCIInterval  *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

addend1 (IN)
Interval to be added.

addend2 (IN)
Interval to be added.

result (OUT)
The resulting interval (`addend1` + `addend2`).

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if any of the following statements is true:

- The two input intervals are not mutually comparable.

- The resulting year is greater than `SB4MAXVAL`.

- The resulting year is less than `SB4MINVAL`.

**Related Topics**

- OCIIntervalSubtract()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.35 OCIIntervalAssign()

Copies one interval to another.

#### Purpose

Copies one interval to another.

#### Syntax

    void OCIIntervalAssign ( void              *hndl,
                             OCIError          *err,
                             const OCIInterval *inpinter,
                             OCIInterval       *outinter );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inpinter (IN)
Input interval.

outinter (OUT)
Output interval.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalCompare()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.36 OCIIntervalCheck()

Checks the validity of an interval.

#### Purpose

Checks the validity of an interval.

#### Syntax

    sword OCIIntervalCheck ( void               *hndl,
                            OCIError            *err,
                            const OCIInterval   *interval,
                            ub4                 *valid );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

interval (IN)
Interval to be checked.

valid (OUT)
Returns zero if the interval is valid; otherwise, it returns the logical operator OR combination of the codes specified in Table 28-9.

Table 28-9 Error Bits Returned by the valid Parameter for OCIIntervalCheck()

| Macro Name                      | Bit Number | Error                                      |
|:--------------------------------|:-----------|:-------------------------------------------|
| `OCI_INTER_INVALID_DAY`         | 0x1        | Bad day                                    |
| `OCI_INTER_DAY_BELOW_VALID`     | 0x2        | Bad day low/high bit (1=low)               |
| `OCI_INTER_INVALID_MONTH`       | 0x4        | Bad month                                  |
| `OCI_INTER_MONTH_BELOW_VALID`   | 0x8        | Bad month low/high bit (1=low)             |
| `OCI_INTER_INVALID_YEAR`        | 0x10       | Bad year                                   |
| `OCI_INTER_YEAR_BELOW_VALID`    | 0x20       | Bad year low/high bit (1=low)              |
| `OCI_INTER_INVALID_HOUR`        | 0x40       | Bad hour                                   |
| `OCI_INTER_HOUR_BELOW_VALID`    | 0x80       | Bad hour low/high bit (1=low)              |
| `OCI_INTER_INVALID_MINUTE`      | 0x100      | Bad minute                                 |
| `OCI_INTER_MINUTE_BELOW_VALID`  | 0x200      | Bad minute low/high bit (1=low)            |
| `OCI_INTER_INVALID_SECOND`      | 0x400      | Bad second                                 |
| `OCI_INTER_SECOND_BELOW_VALID`  | 0x800      | Bad second low/high bit (1=low)            |
| `OCI_INTER_INVALID_FRACSEC`     | 0x1000     | Bad fractional second                      |
| `OCI_INTER_FRACSEC_BELOW_VALID` | 0x2000     | Bad fractional second low/high bit (1=low) |

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, on error.

**Related Topics**

- OCIIntervalCompare()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.37 OCIIntervalCompare()

Compares two intervals.

#### Purpose

Compares two intervals.

#### Syntax

    sword OCIIntervalCompare (void          *hndl,
                              OCIError      *err,
                              OCIInterval   *inter1,
                              OCIInterval   *inter2,
                              sword         *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inter1 (IN)
Interval to be compared.

inter2 (IN)
Interval to be compared.

result (OUT)
Comparison result as specified in Table 28-10.

Table 28-10 Comparison Results Returned by the result Parameter for OCIIntervalCompare()

| Comparison Result    | Output in result Parameter |
|:---------------------|:---------------------------|
| `inter1` \< `inter2` | -1                         |
| `inter1` = `inter2`  | 0                          |
| `inter1` \> `inter2` | 1                          |

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if the input values are not mutually comparable.

**Related Topics**

- OCIIntervalAssign()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.38 OCIIntervalDivide()

Divides an interval by an Oracle `NUMBER` to produce an interval.

#### Purpose

Divides an interval by an Oracle `NUMBER` to produce an interval.

#### Syntax

    sword OCIIntervalDivide ( void         *hndl,
                              OCIError     *err,
                              OCIInterval  *dividend,
                              OCINumber    *divisor,
                              OCIInterval  *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

dividend (IN)
Interval to be divided.

divisor (IN)
Oracle `NUMBER` dividing `dividend`.

result (OUT)
The resulting interval ( `dividend` / `divisor`).

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalMultiply()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.39 OCIIntervalFromNumber()

Converts an Oracle `NUMBER` to an interval.

#### Purpose

Converts an Oracle `NUMBER` to an interval.

#### Syntax

    sword OCIIntervalFromNumber ( void               *hndl,
                                  OCIError           *err,
                                  OCIInterval        *interval,
                                  OCINumber          *number );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

interval (OUT)
Interval result.

number (IN)
Oracle `NUMBER` to be converted (in years for YEAR TO MONTH intervals and in days for DAY TO SECOND intervals).

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalToNumber()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.40 OCIIntervalFromText()

When given an interval string, returns the interval represented by the string. The type of the interval is the type of the `result` descriptor.

#### Purpose

When given an interval string, returns the interval represented by the string. The type of the interval is the type of the `result` descriptor.

#### Syntax

    sword OCIIntervalFromText ( void           *hndl,
                                OCIError       *err,
                                const OraText  *inpstring,
                                size_t          str_len,
                                OCIInterval    *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inpstring (IN)
Input string.

str_len (IN)
Length of the input string.

result (OUT)
Resultant interval.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if any of the following statements is true:

- There are too many fields in the literal string.

- The year is out of range (–4713 to 9999).

- The month is out of range (1 to 12).

- The day of month is out of range (1 to 28...31).

- The hour is out of range (0 to 23).

- The hour is out of range (0 to 11).

- The minutes are out of range (0 to 59).

- The seconds in the minute are out of range (0 to 59).

- The seconds in the day are out of range (0 to 86399).

- The interval is invalid.

**Related Topics**

- OCIIntervalToText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.41 OCIIntervalFromTZ()

Returns an `OCI_DTYPE_INTERVAL_DS` of data type `OCIInterval` with the region ID set (if the region is specified in the input string) and the current absolute offset, or an absolute offset with the region ID set to 0.

#### Purpose

Returns an `OCI_DTYPE_INTERVAL_DS` of data type `OCIInterval` with the region ID set (if the region is specified in the input string) and the current absolute offset, or an absolute offset with the region ID set to 0.

#### Syntax

    sword OCIIntervalFromTZ ( void           *hndl,
                              OCIError       *err,
                              const oratext  *inpstring,
                              size_t          str_len,
                              OCIInterval    *result ) ;

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inpstring (IN)
Pointer to the input string.

str_len (IN)
Length of `inpstring`.

result (OUT)
Output interval.

#### Returns

`OCI_SUCCESS`, on success; `OCI_INVALID_HANDLE`, if err is `NULL`; or `OCI_ERROR`, if there is a bad interval type or there are time zone errors.

#### Comments

The input string must be of the form \[+/-\]TZH:TZM or 'TZR \[TZD\]'

**Related Topics**

- OCIIntervalFromText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.42 OCIIntervalGetDaySecond()

Gets values of day, hour, minute, and second from an interval.

#### Purpose

Gets values of day, hour, minute, and second from an interval.

#### Syntax

    sword OCIIntervalGetDaySecond (void               *hndl,
                                   OCIError           *err,
                                   sb4                *dy,
                                   sb4                *hr,
                                   sb4                *mm,
                                   sb4                *ss,
                                   sb4                *fsec,
                                   const OCIInterval  *interval );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

dy (OUT)
Number of days.

hr (OUT)
Number of hours.

mm (OUT)
Number of minutes.

ss (OUT)
Number of seconds.

fsec (OUT)
Number of nano seconds.

interval (IN)
The input interval.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalSetDaySecond()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.43 OCIIntervalGetYearMonth()

Gets year and month from an interval.

#### Purpose

Gets year and month from an interval.

#### Syntax

    sword OCIIntervalGetYearMonth ( void               *hndl,
                                    OCIError           *err,
                                    sb4                *yr,
                                    sb4                *mnth,
                                    const OCIInterval  *interval );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

yr (OUT)
Year value.

mnth (OUT)
Month value.

interval (IN)
The input interval.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalSetYearMonth()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.44 OCIIntervalMultiply()

Multiplies an interval by an Oracle `NUMBER` to produce an interval.

#### Purpose

Multiplies an interval by an Oracle `NUMBER` to produce an interval.

#### Syntax

    sword OCIIntervalMultiply ( void               *hndl,
                                OCIError           *err,
                                const OCIInterval  *inter,
                                OCINumber          *nfactor,
                                OCIInterval        *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inter (IN)
Interval to be multiplied.

nfactor (IN)
Oracle `NUMBER` to be multiplied.

result (OUT)
The resulting interval (`inter` \* `nfactor`).

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if any of the following statements is true:

- The resulting year is greater than `SB4MAXVAL`.

- The resulting year is less than `SB4MINVAL`.

**Related Topics**

- OCIIntervalDivide()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.45 OCIIntervalSetDaySecond()

Sets day, hour, minute, and second in an interval.

#### Purpose

Sets day, hour, minute, and second in an interval.

#### Syntax

    sword OCIIntervalSetDaySecond ( void               *hndl,
                                    OCIError           *err,
                                    sb4                 dy,
                                    sb4                 hr,
                                    sb4                 mm,
                                    sb4                 ss,
                                    sb4                 fsec,
                                    OCIInterval        *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

dy (IN)
Number of days.

hr (IN)
Number of hours.

mm (IN)
Number of minutes.

ss (IN)
Number of seconds.

fsec (IN)
Number of nano seconds.

result (OUT)
The resulting interval.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalGetDaySecond()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.46 OCIIntervalSetYearMonth()

Sets year and month in an interval.

#### Purpose

Sets year and month in an interval.

#### Syntax

    sword OCIIntervalSetYearMonth ( void               *hndl,
                                    OCIError           *err,
                                    sb4                 yr,
                                    sb4                 mnth,
                                    OCIInterval        *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

yr (IN)
Year value.

mnth (IN)
Month value.

result (OUT)
The resulting interval.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if any of the following statements is true:

- The resulting year is greater than `SB4MAXVAL`.

- The resulting year is less than `SB4MINVAL`.

**Related Topics**

- OCIIntervalGetYearMonth()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.47 OCIIntervalSubtract()

Subtracts two intervals and stores the result in an interval.

#### Purpose

Subtracts two intervals and stores the result in an interval.

#### Syntax

    sword OCIIntervalSubtract ( void         *hndl,
                                OCIError     *err,
                                OCIInterval  *minuend,
                                OCIInterval  *subtrahend,
                                OCIInterval  *result );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

minuend (IN)
The interval to be subtracted from.

subtrahend (IN)
The interval subtracted from `minuend`.

result (OUT)
The resulting interval (`minuend` - `subtrahend`).

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if any of the following statements is true:

- The resulting year is greater than `SB4MAXVAL`.

- The resulting year is less than `SB4MINVAL`.

- The two input intervals are not mutually comparable.

**Related Topics**

- OCIIntervalAdd()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.48 OCIIntervalToNumber()

Converts an interval to an Oracle `NUMBER`.

#### Purpose

Converts an interval to an Oracle `NUMBER`.

#### Syntax

    sword OCIIntervalToNumber ( void               *hndl,
                                OCIError           *err,
                                OCIInterval        *interval,
                                OCINumber          *number );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

interval (IN)
Interval to be converted.

number (OUT)
Oracle `NUMBER` result (in years for `YEARMONTH` interval and in days for `DAYSECOND`).

#### Comments

Fractional portions of the date (for instance, minutes and seconds if the unit chosen is hours) are included in the Oracle `NUMBER` produced. Excess precision is truncated.

#### Returns

`OCI_SUCCESS`; or `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer.

**Related Topics**

- OCIIntervalFromNumber()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.3.49 OCIIntervalToText()

When given an interval, produces a string representing the interval.

#### Purpose

When given an interval, produces a string representing the interval.

#### Syntax

    sword OCIIntervalToText ( void               *hndl,
                              OCIError           *err,
                              const OCIInterval  *interval,
                              ub1                 lfprec,
                              ub1                 fsprec,
                              OraText            *buffer,
                              size_t              buflen,
                              size_t             *resultlen );

#### Parameters

hndl (IN)
The OCI user session handle or the environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

interval (IN)
Interval to be converted.

lfprec (IN)
Leading field precision. (The number of digits used to represent the leading field.)

fsprec (IN)
Fractional second precision of the interval (the number of digits used to represent the fractional seconds).

buffer (OUT)
Buffer to hold the result.

buflen (IN)
The length of `buffer`.

resultlen (OUT)
The length of the result placed into `buffer`.

#### Comments

The interval literal is output as 'year' or '\[year-\]month' for `INTERVAL YEAR TO MONTH` intervals and as 'seconds' or 'minutes\[:seconds\]' or 'hours\[:minutes\[:seconds\]\]' or 'days\[ hours\[:minutes\[:seconds\]\]\]' for `INTERVAL` `DAY` `TO` `SECOND` intervals (where optional fields are surrounded by brackets).

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`, if `err` is a `NULL` pointer; or `OCI_ERROR`, if the buffer is not large enough to hold the result.

**Related Topics**

- OCIIntervalFromText()
- [OCIErrorGet()](miscellaneous-functions.md)
