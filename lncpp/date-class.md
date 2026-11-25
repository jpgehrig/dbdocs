The Date class specifies the abstraction for a SQL `DATE` data item. The Date class also adds formatting and parsing operations to support the OCCI escape syntax for date values.

Since the SQL standard `DATE` is a subset of Oracle Date, this class can be used to support both.

Objects from the Date class can be used as standalone class objects in client side numeric computations and also used to fetch from, and set to, the database.

Example 13-5 How to Get a Date from Database and Use it in Standalone Calculations

This example demonstrates a Date column value being retrieved from the database, a bind using a Date object, and a computation using a standalone Date object.

    /* Create a connection */
    Environment *env = Environment::createEnvironment(Environment::DEFAULT);
    Connection *conn = Connection(user, passwd, db);

    /* Create a statement and associate a DML statement to it */
    string sqlStmt = "SELECT job-id, start_date from JOB_HISTORY
                                where end_date = :x";
    Statement *stmt = conn->createStatement(sqlStmt);

    /* Create a Date object and bind it to the statement */
    Date edate(env, 2000, 9, 3, 23, 30, 30);
    stmt->setDate(1, edate);
    ResultSet *rset = stmt->executeQuery();

    /* Fetch a date from the database */
    while(rset->next())
    {
       Date sd = rset->getDate(2);
       Date temp = sd;    /*assignment operator */
       /* Methods on Date */
       temp.getDate(year, month, day, hour, minute, second);
       temp.setMonths(2);
       IntervalDS inter = temp.daysBetween(sd);
       .
       .
    }

Table 13-16 Summary of Date Methods

| Method          | Summary                                                                              |
|:----------------|:-------------------------------------------------------------------------------------|
| Date()          | `Date` class constructor.                                                            |
| addDays()       | Returns a `Date` object with n days added.                                           |
| addMonths()     | Returns a `Date` object with n months added.                                         |
| daysBetween()   | Returns the number of days between the current `Date` object and the date specified. |
| fromBytes()     | Convert an external `Bytes` representation of a `Date` object to a `Date` object.    |
| fromText()      | Convert the date from a given input string with format and NLS parameters specified. |
| getDate()()     | Returns the date and time components of the `Date` object.                           |
| getSystemDate() | Returns a `Date` object containing the system date.                                  |
| isNull()        | Returns `TRUE` if `Date` is `NULL``; otherwise returns` `false`.                     |
| lastDay()       | Returns a `Date` that is the last day of the month.                                  |
| nextDay()       | Returns a `Date` that is the date of the next day of the week.                       |
| operator=()     | Assigns the values of a date to another.                                             |
| operator==()    | Returns `TRUE` if `a` and `b` are the same, `false` otherwise.                       |
| operator!=()    | Returns `TRUE` if `a` and `b` are unequal, `false` otherwise.                        |
| operator\>()    | Returns `TRUE` if `a` is past `b`, `false` otherwise.                                |
| operator\>=()   | Returns `TRUE` if `a` is past `b or equal to b`, `false` otherwise.                  |
| operator=()     | Returns `TRUE` if `a` is before `b`, `false` otherwise.                              |
| operator\>()    | Returns `TRUE` if `a` is before `b`, or equal to b, `false` otherwise.               |
| setDate()       | Sets the date from the date components input.                                        |
| setNull()       | Sets the object state to `NULL`.                                                     |
| toBytes()       | Converts the `Date` object into an external `Bytes` representation.                  |
| toText()        | Returns the `Date` object as a string.                                               |
| toZone()        | Returns a `Date` object converted from one time zone to another.                     |

### 13.13.1 Date()

`Date` class constructor.

| Syntax                                                                                                                                                                                                                          | Description                                       |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------|
| `Date();`                                                                                                                                                                                                                       | Creates a `NULL` `Date` object.                   |
| `Date(`<br>`   const Date &srcDate);`                                                                                                                                                                                           | Creates a copy of a `Date` object.                |
| `Date(`<br>`   const Environment *envp,`<br>`   int year = 1,`<br>`   unsigned int month = 1,`<br>`   unsigned int day = 1,`<br>`   unsigned int hour = 0,`<br>`   unsigned int minute = 0,`<br>`   unsigned int seconds = 0);` | Creates a `Date` object using integer parameters. |

| Parameter | Description             |
|:----------|:------------------------|
| year      | -4712 to 9999, except 0 |
| month     | 1 to 12                 |
| day       | 1 to 31                 |
| minutes   | 0 to 59                 |
| seconds   | 0 to 59                 |

### 13.13.2 addDays()

Adds a specified number of days to the `Date` object and returns the new date.

#### Syntax

    Date addDays(
       int val) const;

| Parameter | Description                                                  |
|:----------|:-------------------------------------------------------------|
| `val`     | The number of days to be added to the current `Date` object. |

### 13.13.3 addMonths()

Adds a specified number of months to the `Date` object and returns the new date.

#### Syntax

    Date addMonths(
       int val) const;

| Parameter | Description                                                    |
|:----------|:---------------------------------------------------------------|
| `val`     | The number of months to be added to the current `Date` object. |

### 13.13.4 daysBetween()

Returns the number of days between the current `Date` object and `the date specified`.

#### Syntax

    IntervalDS daysBetween(
       const Date &date) const;

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `date`    | The date to be used to compute the days between. |

### 13.13.5 fromBytes()

Converts a `Bytes` object to a `Date` object.

#### Syntax

    void fromBytes(
       const Bytes &byteStream,
       const Environment *envp = NULL);

| Parameter    | Description                                     |
|:-------------|:------------------------------------------------|
| `byteStream` | `Date` in external format in the form of Bytes. |
| `envp`       | The OCCI environment.                           |

### 13.13.6 fromText()

Sets `Date` object to value represented by a `string` or `UString`.

The value is interpreted based on the `fmt` and `nlsParam` parameters. In cases where `nlsParam` is not passed, the Globalization Support settings of the `envp` parameter are used.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_DATE`](../sqlrf/TO_DATE.md)

| Syntax                                                                                                                                                        | Description                                                                    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------|
| `void fromText(`<br>`   const string &datestr,`<br>`   const string &fmt = "",`<br>`   const string &nlsParam = "",`<br>`   const Environment *envp = NULL);` | Sets `Date` object to value represented by a `string`.                         |
| `void fromText(`<br>`   const UString &datestr,`<br>`   const UString &fmt,`<br>`   const UString &nlsParam,`<br>`   const Environment *envp = NULL);`        | Sets `Date` object to value represented by a `UString`; globalization enabled. |

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `envp`     | The OCCI environment.                                                                                                                                                                                  |
| `datestr`  | The date string to be converted to a `Date` object.                                                                                                                                                    |
| `fmt`      | The format string; default is `DD-MON-YY`.                                                                                                                                                             |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.13.7 getDate()

Returns the date in the form of the date components year, month, day, hour, minute, seconds.

#### Syntax

    void getDate(
       int &year,
       unsigned int &month,
       unsigned int &day,
       unsigned int &hour,
       unsigned int &min,
       unsigned int &seconds) const;

| Parameter | Description                        |
|:----------|:-----------------------------------|
| `year`    | The year component of the date.    |
| `month`   | The month component of the date.   |
| `day`     | The day component of the date.     |
| `hour`    | The hour component of the date.    |
| `min`     | The minutes component of the date. |
| `seconds` | The seconds component of the date. |

### 13.13.8 getSystemDate()

Returns the system date.

#### Syntax

    static Date getSystemDate(
       const Environment *envp);

| Parameter | Description                                           |
|:----------|:------------------------------------------------------|
| `envp `   | The environment in which the system date is returned. |

### 13.13.9 isNull()

Tests whether the `Date` is `NULL`. If the `Date` is `NULL`, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.13.10 lastDay()

Returns a date representing the last day of the current month.

#### Syntax

    Date lastDay() const;

### 13.13.11 nextDay()

Returns a date representing the day after the day of the week specified.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_DATE`](../sqlrf/TO_DATE.md)

| Syntax                                             | Description                                                                                                                                                                                                    |
|:---------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Date nextDay(`<br>`   const string &dow) const;`  | Returns a date representing the day after the day of the week specified.                                                                                                                                       |
| `Date nextDay(`<br>`   const UString &dow) const;` | Returns a date representing the day after the day of the week specified.; globalization enabled. The parameter should be in the character set associated with the environment from which the date was created. |

| Parameter | Description                                |
|:----------|:-------------------------------------------|
| `dow`     | A string representing the day of the week. |

### 13.13.12 operator=()

Assigns the date object on the right side of the equal (=) sign to the date object on the left side of the equal (=) sign.

#### Syntax

    Date& operator=(
       const Date &d);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `date`    | The date object that is assigned. |

### 13.13.13 operator==()

Compares the dates specified. If the dates are equal, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator==(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.14 operator!=()

Compares the dates specified. If the dates are not equal then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.15 operator\>()

Compares the dates specified. If the first date is in the future relative to the second date then `TRUE` is returned; otherwise, `FALSE` is returned. If either date is `NULL` then `FALSE` is returned. If the dates are of different type, then `FALSE` is returned.

#### Syntax

    bool operator>(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.16 operator\>=()

Compares the dates specified. If the first date is in the future relative to the second date or the dates are equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either date is `NULL` then `FALSE` is returned. If the dates are of a different type, then `FALSE` is returned.

#### Syntax

    bool operator>=(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.17 operator\<()

Compares the dates specified. If the first date precedes the second date, then `TRUE` is returned; otherwise, `FALSE` is returned. If either date is `NULL` then `FALSE` is returned. If the dates are of a different type, then `FALSE` is returned.

#### Syntax

    bool operator<(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.18 operator\<=()

Compares the dates specified. If the first date precedes the second date or the dates are equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either date is `NULL` then `FALSE` is returned. If the dates are of a different type, then `FALSE` is returned.

#### Syntax

    bool operator<=(
       const Date &first,
       const Date &second);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `first`   | The first date to be compared.  |
| `second`  | The second date to be compared. |

### 13.13.19 setDate()

Sets the date to the values specified.

#### Syntax

    void setDate(
       int year = 1,
       unsigned int month = 1,
       unsigned int day = 1,
       unsigned int hour = 0,
       unsigned int minute = 0,
       unsigned int seconds = 0);

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `year`    | The argument specifying the year value. Valid values are `-4713 `through `9999`. |
| `month`   | The argument specifying the month value. Valid values are `1` through `12`.      |
| `day`     | The argument specifying the day value. Valid values are 1 through 31.            |
| `hour`    | The argument specifying the hour value. Valid values are 0 through 23.           |
| `min`     | The argument specifying the minutes value. Valid values are 0 through 59.        |
| `seconds` | The argument specifying the seconds value. Valid values are 0 through 59.        |

### 13.13.20 setNull()

Sets the `Date` to atomically `NULL`.

#### Syntax

    void setNull();

### 13.13.21 toBytes()

Returns the date in `Bytes` representation.

#### Syntax

    Bytes toBytes() const;

### 13.13.22 toText()

Returns a `string` or `UString` with the value of this date formatted using `fmt` and `nlsParam`.

The value is interpreted based on the `fmt` and `nlsParam` parameters. In cases where `nlsParam` is not passed, the Globalization Support settings of the `envp` parameter are used.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_DATE`](../sqlrf/TO_DATE.md)

| Syntax                                                                                       | Description                                                                           |
|:---------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------|
| `string toText(`<br>`   const string &fmt = "",`<br>`   const string &nlsParam = "") const;` | Returns a `string` with the value of this date formatted using `fmt` and `nlsParam`.  |
| `UString toText(`<br>`   const UString &fmt,`<br>`   const UString &nlsParam) const;`        | Returns a `UString` with the value of this date formatted using `fmt` and `nlsParam`. |

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `fmt`      | The format string; default is `DD-MON-YY`.                                                                                                                                                             |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.13.23 toZone()

Returns `Date` value converted from one time zone to another.

#### Syntax

    Date toZone(
       const string &zone1,
       const string &zone2) const;

| Parameter | Description                                               |
|:----------|:----------------------------------------------------------|
| `zone1`   | A string representing the time zone to be converted from. |
| `zone2`   | A string representing the time zone to be converted to.   |

Valid time zone codes are:

| Zone code  | Value                                        |
|:-----------|:---------------------------------------------|
| `AST, ADT` | Atlantic Standard or Daylight Time           |
| `BST, BDT` | Bering Standard or Daylight Time             |
| `CST, CDT` | Central Standard or Daylight Time            |
| `EST, EDT` | Eastern Standard or Daylight Time            |
| `GMT`      | Greenwich Mean Time                          |
| `HST, HDT` | Alaska-Hawaii Standard Time or Daylight Time |
| `MST, MDT` | Mountain Standard or Daylight Time           |
| `NST`      | Newfoundland Standard Time                   |
| `PST, PDT` | Pacific Standard or Daylight Time            |
| `YST, YDT` | Yukon Standard or Daylight Time              |
