`IntervalYM` supports the SQL standard data type Year-Month Interval.

Leading field precision is determined by number of decimal digits on input.

Table 13-21 Fields of IntervalYM Class

| Field   | Type  | Description                                              |
|:--------|:------|:---------------------------------------------------------|
| `year`  | `int` | Year component. Valid values are `-10^9` through `10^9`. |
| `month` | `int` | Month component. Valid values are `-11` through `11`.    |

Example 13-8 How to Use an Empty IntervalYM Object Through Direct Assignment

This example demonstrates that the default constructor creates a `NULL` value, and how you can assign a non `NULL` value to a year-month interval and then perform operations on it:

    Environment *env = Environment::createEnvironment();

    // Create a NULL year-month interval
    IntervalYM ym
    if(ym.isNull())
       cout << "\n ym is null";

    // Assign a non-NULL value to ym
    IntervalYM anotherYM(env, "10-30");
    ym=anotherYM;

    // Now all operations on YM are valid
    int yr = ym.getYear();

Example 13-9 How to Use an IntervalYM Object Through ResultSet and toText() Method

This example demonstrates how to get the year-month interval column from a result set, add to the year-month interval by using the `+=` operator, multiply by using the `*` operator, compare 2 year-month intervals, and convert a year-month interval to a string by using the `toText()` method.

    //SELECT WARRANT_PERIOD from PRODUCT_INFORMATION
    //obtain result set
    resultset->next();

    //get interval value from resultset
    IntervalYM ym1 = resultset->getIntervalYM(1);

    IntervalYM addWith(env, 10, 1);
    ym1 += addWith;    //call += operator

    IntervalYM mulYm1 = ym1 * Number(env, 10);    //call * operator
    if(ym1<mulYm1)    //comparison
       .
       .
    string strym = ym1.toText(3);    //3 is the leading field precision

Table 13-22 Summary of IntervalYM Methods

| Method        | Summary                                                 |
|:--------------|:--------------------------------------------------------|
| IntervalYM()  | `IntervalYM` class constructor.                         |
| fromText()    | Converts a `string` into an `IntervalYM`.               |
| fromUText()   | Converts a `UString` into an `IntervalYM`.              |
| getMonth()    | Returns month interval value.                           |
| getYear()     | Returns year interval value.                            |
| isNull()      | Checks if the interval is `NULL`.                       |
| operator\*()  | Returns the product of two `IntervalYM` values.         |
| operator\*=() | Multiplication assignment.                              |
| operator=()   | Simple assignment.                                      |
| operator==()  | Checks if `a` and `b` are equal.                        |
| operator!=()  | Checks if `a` and `b` are not equal.                    |
| operator/()   | Returns an `interval` with value `(``a/b``)`.           |
| operator/=()  | Division assignment.                                    |
| operator\>()  | Checks if `a` is greater than `b`.                      |
| operator\>=() | Checks if `a` is greater than or equal to `b`.          |
| operator\<()  | Checks if `a` is less than `b`.                         |
| operator\<=() | Checks if `a` is less than or equal to `b`.             |
| operator-()   | Returns an `interval` with value `(``a - b``)`.         |
| operator-=()  | Subtraction assignment.                                 |
| operator+()   | Returns the sum of two `IntervalYM` values.             |
| operator+=()  | Addition assignment.                                    |
| set()         | Sets the interval to the values specified.              |
| setNull()     | Sets the interval to `NULL`.                            |
| toText()      | Converts to a `string` representation of the interval.  |
| toUText()     | Converts to a `UString` representation of the interval. |

### 13.16.1 IntervalYM()

IntervalYM class constructor.

| Syntax                                                                                       | Description                                                                                                                                                                                                                                                                      |
|:---------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IntervalYM();`                                                                              | Constructs a `NULL` `IntervalYM` object. A `NULL` `IntervalYM` can be initialized by assignment or calling [operator\*()](intervalds-class.md) method. Methods that can be called on `NULL` `IntervalYM` objects are [setName()](bfile-class.md) and [isNull()](bfile-class.md). |
| `IntervalYM(`<br>`   const Environment *env,`<br>`   int year  = 0,`<br>`   int month = 0);` | Creates an `IntervalYM` object within the specified `Environment`.                                                                                                                                                                                                               |
| `IntervalDS(`<br>`   const IntervalYM &src);`                                                | Copy constructor.                                                                                                                                                                                                                                                                |

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `env`     | The `Environment`.                                      |
| `year`    | The `year` field of the `IntervalYM` object.            |
| `month`   | The `month` field of the `IntervalYM` object.           |
| `src`     | The source that the `IntervalYM` object is copied from. |

### 13.16.2 fromText()

This method initializes the interval to the values in `inpstr`. The string is interpreted using the NLS parameters set in the environment.

The NLS parameters are picked up from `env`. If `env` is `NULL`, the NLS parameters are picked up from the environment associated with the instance, if any.

#### Syntax

    void fromText(
       const string &inpStr,
       const string &nlsParam = "",
       const Environment *env = NULL);

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `inpStr`   | Input string representing a year month interval of the form 'year-month'.                                                                                                                              |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |
| `env`      | Environment whose NLS parameters are used.                                                                                                                                                             |

### 13.16.3 fromUText()

Creates the interval from the `UString` specified.

#### Syntax

    void fromUText(
       const UString &inpStr,
       const Environment *env=NULL );

| Parameter | Description                                                                  |
|:----------|:-----------------------------------------------------------------------------|
| `inpStr`  | Input `UString` representing a year month interval of the form 'year-month'. |
| `env`     | The `Environment`.                                                           |

### 13.16.4 getMonth()

This method returns the month component of the interval.

#### Syntax

    int getMonth() const;

### 13.16.5 getYear()

This method returns the year component of the interval.

#### Syntax

    int getYear() const;

### 13.16.6 isNull()

This method tests whether the interval is `NULL`. If the interval is `NULL` then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.16.7 operator\*()

This method multiplies the interval by a factor and returns the result.

#### Syntax

    const IntervalYM operator*(
       const IntervalDS &interval
       const Number &val);

| Parameter  | Description                                  |
|:-----------|:---------------------------------------------|
| `interval` | Interval to be multiplied.                   |
| `val`      | Value by which interval is to be multiplied. |

### 13.16.8 operator\*=()

This method multiplies the interval by a specified value.

Syntax

    IntervalYM& operator*=(
       const Number &factor);

| Parameter | Description             |
|:----------|:------------------------|
| `factor`  | Value to be multiplied. |

### 13.16.9 operator=()

This method assigns the specified value to the interval.

#### Syntax

    IntervalYM& operator=(
       const IntervalYM &src);

| Parameter | Description           |
|:----------|:----------------------|
| `src`     | Value to be assigned. |

### 13.16.10 operator==()

This method compares the intervals specified. If the intervals are equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator==(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.11 operator!=()

This method compares the intervals specified. If the intervals are not equal then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator!=(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.12 operator/()

This method returns the result of dividing the interval by a factor.

#### Syntax

    const IntervalYM operator/(
       const IntervalYM &dividend,
       const Number &factor);

| Parameter  | Description                               |
|:-----------|:------------------------------------------|
| `dividend` | The interval to be divided.               |
| `factor`   | Value by which interval is to be divided. |

### 13.16.13 operator/=()

This method divides the interval by a factor.

#### Syntax

    IntervalYM& operator/=(
       const Number &factor);

| Parameter | Description            |
|:----------|:-----------------------|
| `factor`  | A day second interval. |

### 13.16.14 operator\>()

This method compares the intervals specified. If the first interval is greater than the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator>(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.15 operator\>=()

This method compares the intervals specified. If the first interval is greater than or equal to the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator>=(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.16 operator\<()

This method compares the intervals specified. If the first interval is less than the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown.

#### Syntax

    bool operator<(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.17 operator\<=()

This method compares the intervals specified. If the first interval is less than or equal to the second interval then `TRUE` is returned; otherwise, `FALSE` is returned. If either interval is `NULL` then SQLException is thrown

#### Syntax

    bool operator<=(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.18 operator-()

This method returns the difference between the intervals specified.

#### Syntax

    const IntervalYM operator-(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.19 operator`-=`()

This method computes the difference between itself and another interval.

#### Syntax

    IntervalYM& operator-=(
       const IntervalYM &val);

| Parameter | Description            |
|:----------|:-----------------------|
| `val`     | A day second interval. |

### 13.16.20 operator+()

This method returns the sum of the intervals specified.

#### Syntax

    const IntervalYM operator+(
       const IntervalYM &first,
       const IntervalYM &second);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `first`   | The first interval to be compared.  |
| `second`  | The second interval to be compared. |

### 13.16.21 operator+=()

This method assigns the sum of `IntervalYM `and `val` to `IntervalYM`.

#### Syntax

    IntervalYM& operator+=(
       const IntervalYM &val);

| Parameter | Description            |
|:----------|:-----------------------|
| `val`     | A day second interval. |

### 13.16.22 set()

This method sets the interval to the values specified.

#### Syntax

    void set(
       int year,
       int month);

| Parameter | Description                                              |
|:----------|:---------------------------------------------------------|
| `year`    | Year component. Valid values are `-10^9` through `10^9`. |
| `month`   | Month component. Valid values are `-11 `through `11`.    |

### 13.16.23 setNull()

This method sets the interval to `NULL`.

#### Syntax

    void setNull();

### 13.16.24 toText()

This method returns the string representation of the interval.

#### Syntax

    string toText(
       unsigned int lfprec,
       const string &nlsParam = "") const;

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `lfprec`   | Leading field precision.                                                                                                                                                                               |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.16.25 toUText()

Converts to a `UString` representation for the interval.

#### Syntax

    UString toUText(
       unsigned int lfprec) cosnt;

| Parameter | Description              |
|:----------|:-------------------------|
| `lfprec`  | Leading field precision. |
