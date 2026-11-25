This class supports the SQL standard `TIMESTAMP WITH TIME ZONE` and `TIMESTAMP WITHOUT TIME ZONE` types, and works with all database `TIMESTAMP` types: `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, and `TIMESTAMP WITH LOCAL TIME ZONE`.

`Timestamp` time components, such as hour, minute, second and fractional section are in the time zone specified for the `Timestamp`. This is new behavior for the 10g release; previous versions supported GMT values of time components. Time components were only converted to the time zone specified by `Timestamp` when they were stored in the database. For example, the following Timestamp() call constructs a `Timestamp` value `13-Nov 2003 17:24:30.0` in timezone `+5:30`.

    Timestamp ts(env, 2003, 11, 13, 17, 24, 30, 0, 5, 30);

The behavior of this call in previous releases would interpret the timestamp components as GMT, resulting in a timestamp value of `13-Nov 2003 11:54:30.0` in timezone `+5:30`. Users were forced to convert the timestamps to GMT before invoking the constructor. Note that for GMT timezone, both hour and minute equal `0`.

This behavior change also applies to setDate() and setTime() methods.

The fields of `Timestamp` class and their legal ranges are provided in Table 13-49. An `SQLException` occurs if a parameter is out of range.

Table 13-49 Fields of Timestamp and Their Legal Ranges

| Field    | Type         | Minimum Value | Maximum value |
|:---------|:-------------|:--------------|:--------------|
| `year`   | int          | `-4713`       | `9999`        |
| `month`  | unsigned int | `1`           | `12`          |
| `day`    | unsigned int | `1`           | `31`          |
| `hour`   | unsigned int | `0`           | `23`          |
| `min`    | unsigned int | `0`           | `59`          |
| `sec`    | unsigned int | `0`           | `61`          |
| `tzhour` | int          | `-12`         | `14`          |
| `tzmin`  | int          | `-59`         | `59`          |

Table 13-50 Summary of Timestamp Methods

| Method              | Summary                                                                                 |
|:--------------------|:----------------------------------------------------------------------------------------|
| Timestamp()         | `Timestamp` class constructor.                                                          |
| fromText()          | Sets the time stamp from the values provided by the string.                             |
| getDate()           | Gets the date from the `Timestamp` object.                                              |
| getTime()           | Gets the time from the `TimeStamp` object.                                              |
| getTimeZoneOffset() | Returns the time zone hour and minute offset value.                                     |
| intervalAdd()       | Returns a `Timestamp` object with value (this + interval).                              |
| intervalSub()       | Returns a `Timestamp` object with value (this - interval).                              |
| isNull()            | Checks if `Timestamp` is `NULL`.                                                        |
| operator=()         | Simple assignment.                                                                      |
| operator==()        | Checks if a and b are equal.                                                            |
| operator!=()        | Checks if a and b are not equal.                                                        |
| operator\>()        | Checks if a is greater than b.                                                          |
| operator\>=()       | Checks if a is greater than or equal to b.                                              |
| operator\<()        | Checks if a is less than b.                                                             |
| operator\<=()       | Checks if a is less than or equal to b.                                                 |
| setDate()           | Sets the year, month, day components contained for this timestamp.                      |
| setNull()           | Sets the value of Timestamp to `NULL`                                                   |
| setTime()           | Sets the day, hour, minute, second and fractional second components for this timestamp. |
| setTimeZoneOffset() | Sets the hour and minute offset for time zone.                                          |
| subDS()             | Returns a `IntervalDS` representing this - `val`.                                       |
| subYM()             | Returns a `IntervalYM` representing this - `val`.                                       |
| toText()            | Returns a` string `representation for the timestamp in the format specified.            |

### 13.33.1 Timestamp()

`Timestamp` class constructor.

| Syntax                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                     |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Timestamp(`<br>`   const Environment *env,`<br>`   int year=1,`<br>`   unsigned int month=1,`<br>`   unsigned int day=1,`<br>`   unsigned int hour=0,`<br>`   unsigned int min=0,`<br>`   unsigned int sec=0,`<br>`   unsigned int fs=0,`<br>`   int tzhour=0,`<br>`   int tzmin=0);` | Returns a default `Timestamp` object. Time components are understood to be in the specified time zone.                                                                                                                                                                                          |
| `Timestamp();`                                                                                                                                                                                                                                                                         | Returns a `NULL Timestamp` object. A `NULL` timestamp can be initialized by assignment or calling the fromText() method. Methods that can be called on `NULL` timestamp objects are setNull(), [isNull()](bfile-class.md) and [operator=()](bfile-class.md).                                    |
| `Timestamp(`<br>`   const Environment *env,`<br>`   int year,`<br>`   unsigned int month,`<br>`   unsigned int day,`<br>`   unsigned int hour,`<br>`   unsigned int min,`<br>`   unsigned int sec,`<br>`   unsigned int fs,`<br>`   const string &timezone);`                          | Multibyte support. The timezone can be passed as region, "US/Eastern", or as an offset from GMT, "+05:30". If an empty string is passed, then the time is considered to be in the current session's time zone. Used for constructing values for `TIMESTAMP WITH LOCAL TIME ZONE` types.         |
| `Timestamp(`<br>`   const Environment *env,`<br>`   int year,`<br>`   unsigned int month,`<br>`   unsigned int day,`<br>`   unsigned int hour,`<br>`   unsigned int min,`<br>`   unsigned int sec,`<br>`   unsigned int fs,`<br>`   const UString &timezone);`                         | UTF16 (`UString`) support. The timezone can be passed as region, "US/Eastern", or as an offset from GMT, "+05:30". If an empty string is passed, then the time is considered to be in the current session's time zone. Used for constructing values for `TIMESTAMP WITH LOCAL TIME ZONE` types. |
| `Timestamp(`<br>`   const Timestamp &src);`                                                                                                                                                                                                                                            | Copy constructor.                                                                                                                                                                                                                                                                               |

| Parameter | Description                           |
|:----------|:--------------------------------------|
| `year`    | Year component.                       |
| `month`   | Month component.                      |
| `day`     | Day component.                        |
| `hour`    | Hour component.                       |
| `minute`  | Minute component.                     |
| `second`  | Second component.                     |
| `fs`      | Fractional second component.          |
| `tzhour`  | Time zone difference hour component.  |
| `tzmin`   | Timezone difference minute component. |
| `src`     | The original `Timezone`.              |

Example 13-11 Using Default Timestamp Constructor

This example demonstrates that the default constructor creates a `NULL` value, and how you can assign a non-`NULL` value to a `Timestamp` and perform operations on it:

    Environment *env = Environment::createEnvironment();

    //create a null timestamp
    Timestamp ts;
    if(ts.isNull())
       cout << "\n ts is Null";

    //assign a non null value to ts
    Timestamp notNullTs(env, 2000, 8, 17, 12, 0, 0, 0, 5, 30);
    ts = notNullTs;

    //now all operations are valid on ts
    int yr;
    unsigned int mth, day;
    ts.getDate(yr, mth, day);

Example 13-12 Using fromText() method to Initialize a NULL Timestamp Instance

The following code example demonstrates how to use the fromText() method to initialize a `NULL` timestamp:

    Environment *env = Environment::createEnvironment();

    Timestamp ts1;
    ts1.fromText("01:16:17.12 04/03/1825", "hh:mi:ssxff dd/mm/yyyy", "", env);

Example 13-13 Comparing Timestamps Stored in the Database

The following code example demonstrates how to get the timestamp column from a result set, check whether the timestamp is `NULL`, get the timestamp value in string format, and determine the difference between 2 timestamps:

    Timestamp reft(env, 2001, 1, 1);
    ResultSet *rs=stmt->executeQuery(
       "select order_date from orders where customer_id=1");
    rs->next();

    //retrieve the timestamp column from result set
    Timestamp ts=rs->getTimestamp(1);

    //check timestamp for null
    if(!ts.isNull())
    {
       string tsstr=ts.toText(           //get the timestamp value in string format
          "dd/mm/yyyy hh:mi:ss [tzh:tzm]",0);
       if(reft<ts                        //compare timestamps
          IntervalDS ds=reft.subDS(ts);  //get difference between timestamps
    }

### 13.33.2 fromText()

Sets the timestamp value from the string. The string is expected to be in the format specified. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from the environment which has been passed. In case environment is not passed, Globalization Support parameters are obtained from the environment associated with the instance, if any.

Sets `Timestamp` object to value represented by a `string` or `UString`.

The value is interpreted based on the `fmt` and `nlsParam` parameters. In cases where `nlsParam` is not passed, the Globalization Support settings of the `envp` parameter are used.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_DATE`](../sqlrf/TO_DATE.md)

| Syntax                                                                                                                                                      | Description                                                                         |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| `void fromText(`<br>`   const string &timestmpStr,`<br>`   const string &fmt,`<br>`   const string &nlsParam = "",`<br>`   const Environment *env = NULL);` | Sets `Timestamp` object to value represented by a `string`.                         |
| `void fromText(`<br>`   const UString &timestmpStr,`<br>`   const UString &fmt,`<br>`   const UString &nlsParam,`<br>`   const Environment *env = NULL);`   | Sets `Timestamp` object to value represented by a `UString`; globalization enabled. |

| Parameter     | Description                                                                                                                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `timestmpStr` | The timestamp `string` or `UString` to be converted to a `Timestamp` object.                                                                                                                                                                                                                            |
| `fmt`         | The format string.                                                                                                                                                                                                                                                                                      |
| `nlsParam`    | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`.                                                                                                  |
| `env`         | The OCCI environment. In globalization enabled version of the method, used to determine `NLS_CALENDAR` for interpreting `timestampStr`. If `env` is not passed, the environment associated with the object controls the setting. Should be a non-`NULL` value if called on a `NULL` `Timestamp` object. |

### 13.33.3 getDate()

Returns the year, month and day values of the `Timestamp`.

#### Syntax

    void getDate(
       int &year,
       unsigned int &month,
       unsigned int &day) const;

| Parameter | Description      |
|:----------|:-----------------|
| `year`    | Year component.  |
| `month`   | Month component. |
| `day`     | Day component.   |

### 13.33.4 getTime()

Returns the hour, minute, second, and fractional second components

#### Syntax

    void getTime(
       unsigned int &hour,
       unsigned int &minute,
       unsigned int &second,
       unsigned int &fs) const;

| Parameter | Description                  |
|:----------|:-----------------------------|
| `hour`    | Hour component.              |
| `minute`  | Minute component.            |
| `second`  | Second component.            |
| `fs`      | Fractional second component. |

### 13.33.5 getTimeZoneOffset()

Returns the time zone offset in hours and minutes.

#### Syntax

    void getTimeZoneOffset(
       int &hour,
       int &minute) const;

| Parameter | Description       |
|:----------|:------------------|
| `hour`    | Time zone hour.   |
| `minute`  | Time zone minute. |

### 13.33.6 intervalAdd()

Adds an interval to timestamp.

| Syntax                                                               | Description                                   |
|:---------------------------------------------------------------------|:----------------------------------------------|
| `const Timestamp intervalAdd(`<br>`   const IntervalDS& val) const;` | Adds an IntervalDS interval to the timestamp. |
| `const Timestamp intervalAdd(`<br>`   const IntervalYM& val) const;` | Adds an IntervalYM interval to the timestamp. |

| Parameter | Description           |
|:----------|:----------------------|
| `val`     | Interval to be added. |

### 13.33.7 intervalSub()

Subtracts an interval from a timestamp and returns the result as a timestamp. Returns a `Timestamp` with the value of this - `val`.

| Syntax                                                               | Description                                          |
|:---------------------------------------------------------------------|:-----------------------------------------------------|
| `const Timestamp intervalSub(`<br>`   const IntervalDS& val) const;` | Subtracts an `IntervalDS` interval to the timestamp. |
| `const Timestamp intervalsUB(`<br>`   const IntervalYM& val) const;` | Subtracts an `IntervalYM` interval to the timestamp. |

| Parameter | Description                |
|:----------|:---------------------------|
| `val`     | Interval to be subtracted. |

### 13.33.8 isNull()

Returns `TRUE` if `Timestamp` is `NULL` or `FALSE` otherwise.

#### Syntax

    bool isNull() const;

### 13.33.9 operator=()

Assigns a given timestamp object to this object.

#### Syntax

    Timestamp & operator=(
       const Timestamp &src);

| Parameter | Description           |
|:----------|:----------------------|
| `src`     | Value to be assigned. |

### 13.33.10 operator==()

Compares the timestamps specified. If the timestamps are equal, returns `TRUE`, `FALSE` otherwise. If either `a` or `b` is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator==(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.11 operator!=()

Compares the timestamps specified. If the timestamps are not equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either timestamp is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.12 operator\>()

Returns `TRUE` if `first` is greater than `second`, `FALSE` otherwise. If either is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator>(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.13 operator\>=()

Compares the timestamps specified. If the `first` timestamp is greater than or equal to the `second` timestamp then `TRUE` is returned; otherwise, `FALSE` is returned. If either timestamp is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator>=(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.14 operator\<()

Returns `TRUE` if `first` is less than `second`, `FALSE` otherwise. If either `a` or `b` is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator<(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.15 operator\<=()

Compares the timestamps specified. If the first timestamp is less than or equal to the second timestamp then `TRUE` is returned; otherwise, `FALSE` is returned. If either timestamp is `NULL` then `FALSE` is returned.

#### Syntax

    bool operator<=(
       const Timestamp &first,
       const Timestamp &second);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `first`   | First timestamp to be compared.  |
| `second`  | Second timestamp to be compared. |

### 13.33.16 setDate()

Sets the year, month, day components contained for this timestamp

#### Syntax

    void setDate(
       int year,
       unsigned int month,
       unsigned int day);

| Parameter | Description                                          |
|:----------|:-----------------------------------------------------|
| `year`    | Year component. Valid values are -4713 through 9999. |
| `month`   | Month component. Valid values are 1 through 12.      |
| `day`     | Day component. Valid values are 1 through 31.        |

### 13.33.17 setNull()

Sets the timestamp to `NULL`.

#### Syntax

    void setNull();

### 13.33.18 setTime()

Sets the day, hour, minute, second and fractional second components for this timestamp.

#### Syntax

    void setTime(
       unsigned int hour,
       unsigned int minute,
       unsigned int second,
       unsigned int fs);

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| hour      | Hour component. Valid values are 0 through 23.   |
| minute    | Minute component. Valid values are 0 through 59. |
| second    | Second component. Valid values are 0 through 59. |
| fs        | Fractional second component.                     |

### 13.33.19 setTimeZoneOffset()

Sets the hour and minute offset for time zone.

#### Syntax

    void setTimeZoneOffset(
       int hour,
       int minute);

| Parameter | Description                                        |
|:----------|:---------------------------------------------------|
| hour      | Time zone hour. Valid values are -12 through 12.   |
| minute    | Time zone minute. Valid values are -59 through 59. |

### 13.33.20 subDS()

Computes the difference between this timestamp and the specified timestamp and return the difference as an `IntervalDS`.

#### Syntax

    const IntervalDS subDS(
       const Timestamp& val) const;

| Parameter | Description                 |
|:----------|:----------------------------|
| val       | Timestamp to be subtracted. |

### 13.33.21 subYM()

Computes the difference between timestamp values and return the difference as an `IntervalYM`.

#### Syntax

    const IntervalYM subYM(
       const Timestamp& val) const;

| Parameter | Description                   |
|:----------|:------------------------------|
| `val`     | `Timestamp` to be subtracted. |

### 13.33.22 toText()

Returns a `string `or `UString` representation for the timestamp in the format specified.

If `nlsParam` is specified, this determines the NLS parameters used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from the environment associated with the instance, if any.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_DATE`](../sqlrf/TO_DATE.md)

| Syntax                                                                                                               | Description                                                                                          |
|:---------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| `string toText(`<br>`   const string &fmt,`<br>`   unsigned int fsprec,`<br>`   const string &nlsParam = "") const;` | Returns a `string `representation for the timestamp in the format specified.                         |
| `UString toText(`<br>`   const UString &fmt,`<br>`   unsigned int fsprec,`<br>`   const UString &nlsParam) const;`   | Returns a `UString` representation for the timestamp in the format specified; globalization enabled. |

| Parameter  | Description                                                                                                                                                                                                |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `fmt`      | The format string.                                                                                                                                                                                         |
| `fsprec`   | The precision for the fractional second component of `Timestamp`.                                                                                                                                          |
| `nlsParam` | The `NLS` parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the `NLS` parameters are picked up from `envp`. |
