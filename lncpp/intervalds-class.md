The IntervalDS class encapsulates time interval calculations in terms of days, hours, minutes, seconds, and fractional seconds. Leading field precision is determined by number of decimal digits in day input. Fraction second precision is determined by number of fraction digits on input.

Table 13-19 Fields of IntervalDS Class

| Field    | Type  | Description                                                                                                                                                                                                                                                        |
|:---------|:------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `day`    | `int` | Day component. Valid values are `-10^9` through `10^9`.                                                                                                                                                                                                            |
| `hour`   | `int` | Hour component. Valid values are `-23` through `23`.                                                                                                                                                                                                               |
| `minute` | `int` | Minute component. Valid values are `-59` through `59`.                                                                                                                                                                                                             |
| `second` | `int` | Second component. Valid values are `-59` through `59`.                                                                                                                                                                                                             |
| `fs`     | `int` | Fractional second component. Constructs a `NULL` `IntervalDS` object. A `NULL` `intervalDS` can be initialized by assignment or calling `fromText` method. Methods that can be called on `NULL` `intervalDS` objects are [setName()](bfile-class.md) and isNull(). |

Example 13-6 How to Use an Empty IntervalDS Object through Direct Assignment

This example demonstrates how the default constructor creates a `NULL` value, and how you can assign a non `NULL` value to a day-second interval and then perform operations on it.

    Environment *env = Environment::createEnvironment();

    // Create a NULL day-second interval
    IntervalDS ds;
    if(ds.isNull())
       cout << "\n ds is null";

    // Assign a non-NULL value to ds
    IntervalDS anotherDS(env, "10 20:14:10.2");
    ds = anotherDS;

    // Now all operations on IntervalDS are valid
    int DAY = ds.getDay();

Example 13-7 How to Use an Empty IntervalDS Object Through \*Text() Methods

This example demonstrates how to create a `NULL` day-second interval, initialize the day-second interval by using the `fromText()` method, add to the day-second interval by using the += operator, multiply by using the \* operator, compare 2 day-second intervals, and convert a day-second interval to a string by using the `toText` method:

    Environment *env = Environment::createEnvironment();

    // Create a null day-second interval
    IntervalDS ds1

    // Initialize a null day-second interval by using the fromText method
    ds1.fromText("20 10:20:30.9","",env);

    IntervalDS addWith(env,2,1);
    ds1 += addWith;    //call += operator

    IntervalDS mulDs1=ds1 * Number(env,10);
                       //call * operator
    if(ds1==mulDs1)    //call == operator
       .
       .
    string strds=ds1.toText(2,4);                       //2 is leading field precision
                       //4 is the fractional field precision

Table 13-20 Summary of IntervalDS Methods

| Method        | Summary                                                      |
|:--------------|:-------------------------------------------------------------|
| IntervalDS()  | `IntervalDS` class constructor.                              |
| fromText()    | Returns an `IntervalDS` converted from a `string`.           |
| fromUText()   | Returns an `IntervalDS` converted from a `UString`.          |
| getDay()      | Returns day interval values.                                 |
| getFracSec()  | Returns fractional second interval values.                   |
| getFracSec()  | Returns hour interval values.                                |
| getMinute()   | Returns minute interval values.                              |
| getSecond()   | Returns second interval values.                              |
| isNull()      | Returns `true` if `IntervalDS` is `NULL`, `false` otherwise. |
| operator\*()  | Returns the product of two `IntervalDS` values.              |
| operator\*=() | Multiplication assignment.                                   |
| operator=()   | Simple assignment.                                           |
| operator==()  | Checks if `a` and `b` are equal.                             |
| operator!=()  | Checks if `a` and `b` are not equal.                         |
| operator/()   | Returns an `IntervalDS` with value `(``a`` / ``b``)`.        |
| operator/=()  | Division assignment.                                         |
| operator\>()  | Checks if `a` is greater than `b`                            |
| operator\>=() | Checks if `a` is greater than or equal to `b`.               |
| operator\<()  | Checks if `a` is less than `b`.                              |
| operator\<=() | Checks if `a` is less than or equal to `b`.                  |
| operator-()   | Returns an `IntervalDS` with value (`a -`` ``b`).            |
| operator-=()  | Subtraction assignment.                                      |
| operator+()   | Returns the sum of two `IntervalDS` values.                  |
| operator+=()  | Addition assignment.                                         |
| set()         | Sets day-second interval.                                    |
| setNull()     | Sets day-second interval to `NULL`.                          |
| toText()      | Converts to a `string` representation for the interval.      |
| toUText()     | Converts to a `UString` representation for the interval.     |

### 13.15.1 IntervalDS()

`IntervalDS` class constructor.

| Syntax                                                                                                                                                        | Description                                                                                                                                                                                                                                             |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IntervalDS();`                                                                                                                                               | Constructs a `NULL` `IntervalDS` object. A `NULL` `IntervalDS `can be initialized by assignment or calling fromText() method. Methods that can be called on `NULL` `IntervalDS` objects are [setName()](bfile-class.md) and [isNull()](bfile-class.md). |
| `IntervalDS(`<br>`   const Environment *env,`<br>`   int day = 0,`<br>`   int hour = 0,`<br>`   int minute = 0,`<br>`   int second = 0,`<br>`   int fs = 0);` | Constructs an `IntervalDS` object within a specified `Environment`.                                                                                                                                                                                     |
| `IntervalDS(`<br>`   const IntervalDS &src);`                                                                                                                 | Constructs an` IntervalYM` object from `src`.                                                                                                                                                                                                           |

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `env`     | The `Environment`.                                      |
| `day`     | The `day` field of `IntervalDS`.                        |
| `hour`    | The `hour` field of `IntervalDS`.                       |
| `minute`  | The `minute` field of `IntervalDS`.                     |
| `second`  | The second field of `IntervalDS`.                       |
| `fs`      | The `fs` field of `IntervalDS`.                         |
| `src`     | The source that the `IntervalDS` object is copied from. |

### 13.15.2 fromText()

Creates the interval from the string specified. The string is converted using the `nls` parameters associated with the relevant environment. The `nls` parameters are picked up from `env`. If `env` is `NULL`, the `nls` parameters are picked up from the environment associated with the instance, if any.

#### Syntax

    void fromText(
       const string &inpstr,
       const string &nlsParam = "",
       const Environment *env = NULL);

| Parameter  | Description                                                                                                                                                                                             |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `inpstr`   | Input string representing a day second interval of the form 'days hours:minutes:seconds', for example, '10 20:14:10.2'                                                                                  |
| `nlsParam` | The `NLS` parameter string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |
| `env`      | Environment whose NLS parameters are used.                                                                                                                                                              |

### 13.15.3 fromUText()

Creates the interval from the `UString` specified.

#### Syntax

    void fromUText(
       const UString &inpstr,
       const Environment *env=NULL );

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `inpstr`  | Input `UString` representing a day second interval of the form 'days hours:minutes:seconds', for example, '10 20:14:10.2' |
| `env`     | The `Environment`.                                                                                                        |

### 13.15.4 getDay()

Returns the day component of the interval.

#### Syntax

    int getDay() const;

### 13.15.5 getFracSec()

Returns the fractional second component of the interval.

#### Syntax

    int getFracSec() const;

### 13.15.6 getHour()

Returns the hour component of the interval.

#### Syntax

    int getHour() const;

### 13.15.7 getMinute()

Returns the minute component of this interval.

#### Syntax

    int getMinute() const;

### 13.15.8 getSecond()

Returns the seconds component of this interval.

#### Syntax

    int getSecond() const;

### 13.15.9 isNull()

Tests whether the interval is `NULL`. If the interval is `NULL` then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.15.10 operator\*()

Multiplies an interval by a specified value and returns the result.

#### Syntax

    const IntervalDS operator*(
       const IntervalDS &interval,
       const Number &val);

| Parameter  | Description                                  |
|:-----------|:---------------------------------------------|
| `interval` | Interval to be multiplied.                   |
| `val`      | Value by which interval is to be multiplied. |

### 13.15.11 operator\*=()

Assigns the product of `IntervalDS` and `a` to `IntervalDS`.

#### Syntax

    IntervalDS& operator*=(
       const IntervalDS &factor);

| Parameter | Description            |
|:----------|:-----------------------|
| `factor`  | A day second interval. |

### 13.15.12 operator=()

Assigns the specified value to the interval.

#### Syntax

    IntervalDS& operator=(
       const IntervalDS &src);

| Parameter | Description           |
|:----------|:----------------------|
| `src`     | Value to be assigned. |

### 13.15.13 operator==()

Compares the intervals specified. If the intervals are equal, then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator==(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.14 operator!=()

Compares the intervals specified. If the intervals are not equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator!=(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.15 operator/()

Returns the result of dividing an interval by a constant value.

#### Syntax

    const IntervalDS operator/(
       const IntervalDS &dividend,
       const Number &factor);

| Parameter  | Description                               |
|:-----------|:------------------------------------------|
| `dividend` | The interval to be divided.               |
| `factor`   | Value by which interval is to be divided. |

### 13.15.16 operator/=()

Assigns the quotient of `IntervalDS` and `val` to `IntervalDS`.

#### Syntax

    IntervalDS& operator/=(
       const IntervalDS &factor);

| Parameter | Description            |
|:----------|:-----------------------|
| `factor`  | A day second interval. |

### 13.15.17 operator\>()

Compares the intervals specified. If the first interval is greater than the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator>(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.18 operator\>=()

Compares the intervals specified. If the first interval is greater than or equal to the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator>=(
       const IntervalDS &first,
       const IntervalDS &first);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.19 operator\<()

Compares the intervals specified. If the first interval is less than the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator<(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.20 operator\<=()

Compares the intervals specified. If the first interval is less than or equal to the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator<=(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.21 operator-()

Returns the difference between the intervals `first` and `second`.

#### Syntax

    const IntervalDS operator-(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.22 operator`-=`()

Assigns the difference between `IntervalDS` and `val` to `IntervalDS`.

#### Syntax

    IntervalDS& operator-=(
       const IntervalDS &val);

| Parameter | Description            |
|:----------|:-----------------------|
| `val`     | A day second interval. |

### 13.15.23 operator+()

Returns the sum of the intervals specified.

#### Syntax

    const IntervalDS operator+(
       const IntervalDS &first,
       const IntervalDS &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.15.24 operator+=()

Assigns the sum of `IntervalDS `and `val` to `IntervalDS`.

#### Syntax

    IntervalDS& operator+=(
       const IntervalDS &val);

| Parameter | Description            |
|:----------|:-----------------------|
| `val`     | A day second interval. |

### 13.15.25 set()

Sets the interval to the values specified.

#### Syntax

    void set(
       int day,
       int hour,
       int minute,
       int second,
       int fracsec);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `day`     | Day component.               |
| `hour`    | Hour component.              |
| `min`     | Minute component.            |
| `second`  | Second component.            |
| `fracsec` | Fractional second component. |

### 13.15.26 setNull()

Sets the `IntervalDS` to `NULL`.

#### Syntax

    void setNull();

### 13.15.27 toText()

Converts to a `string` representation for the interval.

#### Syntax

    string toText(
       unsigned int lfprec,
       unsigned int fsprec,
       const string &nlsParam = "") const;

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `lfprec`   | Leading field precision.                                                                                                                                                                               |
| `fsprec`   | Fractional second precision.                                                                                                                                                                           |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.15.28 toUText()

Converts to a `UString` representation for the interval.

#### Syntax

    UString toUText(
       unsigned int lfprec,
       unsigned int fsprec) cosnt;

| Parameter | Description                  |
|:----------|:-----------------------------|
| `lfprec`  | Leading field precision.     |
| `fsprec`  | Fractional second precision. |
