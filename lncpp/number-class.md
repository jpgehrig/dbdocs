The `Number` class handles limited-precision signed base `10` numbers. A `Number` guarantees `38` decimal digits of precision. All positive numbers in the range displayed here can be represented to a full `38`-digit precision:

    10^-130

and

    9.99999999999999999999999999999999999999*10^125

The range of representable negative numbers is symmetrical.

The number zero can be represented exactly. Also, Oracle numbers have representations for positive and negative infinity. These are generally used to indicate overflow.

The internal storage type is opaque and private. Scale is not preserved when `Number` instances are created.

`Number` does not support the concept of NaN and is not IEEE-754-85 compliant. `Number` does support +Infinity and -Infinity.

Objects from the `Number` class can be used as standalone class objects in client side numeric computations. They can also be used to fetch from and set to the database.

Example 13-10 How to Retrieve and Use a Number Object

This example demonstrates a `Number` column value being retrieved from the database, a bind using a `Number` object, and a comparison using a standalone `Number` object.

    /* Create a connection */
    Environment *env = Environment::createEnvironment(Environment::DEFAULT);
    Connection *conn = Connection(user, passwd, db);

    /* Create a statement and associate a select clause with it */
    string sqlStmt = "SELECT department_id FROM DEPARTMENTS";
    Statement *stmt = conn->createStatement(sqlStmt);

    /* Run the statement to get a result set */
    ResultSet *rset = stmt->executeQuery();
    while(rset->next())
    {
       Number deptId = rset->getNumber(1);
       /* Display the department id with the format string 9,999 */
       cout << "Department Id" << deptId.toText(env, "9,999");

       /* Use the number obtained as a bind value in the following query */
       stmt->setSQL("SELECT * FROM EMPLOYEES WHERE department_id = :x");
       stmt->setNumber(1, deptId);
       ResultSet *rset2 = stmt->executeQuery();
       .
       .
    }
    /* Using a Number object as a standalone and the operations on them */

    /* Create a number to a double value */
    double value = 2345.123;
    Number nu1 (value);

    /* Some common Number methods */
    Number abs = nu1.abs();    /* absolute value */
    Number sqrt = nu1.squareroot();    /* square root */
    Environment *env = Environment::createEnvironment();

    //create a null year-month interval
    IntervalYM ym
    if(ym.isNull())
       cout << "\n ym is null";

    //assign a non null value to ym
    IntervalYM anotherYM(env, "10-30");
    ym = anotherYM;

    //now all operations are valid on ym
    int yr = ym.getYear();

Table 13-30 Summary of Number Methods

| Method                               | Summary                                                                                                                                        |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| Number()                             | `Number` class constructor.                                                                                                                    |
| abs()                                | Returns the absolute value of the number.                                                                                                      |
| arcCos()                             | Returns the arcCosine of the number.                                                                                                           |
| arcSin()                             | Returns the arcSine of the number.                                                                                                             |
| arcTan()                             | Returns the arcTangent of the number.                                                                                                          |
| arcTan2()                            | Returns the arcTangent2 of the input number `y` and this number `x`.                                                                           |
| ceil()                               | Returns the smallest integral value not less than the value of the number.                                                                     |
| cos()                                | Returns the cosine of the number.                                                                                                              |
| exp()                                | Returns the natural exponent of the number.                                                                                                    |
| floor()                              | Returns the largest integral value not greater than the value of the number.                                                                   |
| fromBytes()                          | Returns a Number derived from a `Bytes` object.                                                                                                |
| fromText()                           | Returns a Number from a given number string, format string and NLS parameters specified.                                                       |
| hypCos()                             | Returns the hyperbolic cosine of the number.                                                                                                   |
| hypSin()                             | Returns the hyperbolic sine of the number.                                                                                                     |
| hypTan()                             | Returns the hyperbolic tangent of the number.                                                                                                  |
| intPower()                           | Returns the number raised to the integer value specified.                                                                                      |
| isNull()                             | Checks if `Number` is `NULL`.                                                                                                                  |
| ln()                                 | Returns the natural logarithm of the number.                                                                                                   |
| log()                                | Returns the logarithm of the number to the base value specified.                                                                               |
| operator++()                         | Increments the `number`.                                                                                                                       |
| operator--()                         | Decrements the n`umber`.                                                                                                                       |
| operator\*()                         | Returns the product of two `Number`s.                                                                                                          |
| operator/()                          | Returns the quotient of two `Number`s.                                                                                                         |
| operator%()                          | Returns the modulo of two `Number`s.                                                                                                           |
| operator+()                          | Returns the sum of two `Number`s.                                                                                                              |
| operator-()                          | Returns the negated value of `Number.`                                                                                                         |
| operator-()                          | Returns the difference between two `Number`s.                                                                                                  |
| operator\<()                         | Checks if a number is less than an other number.                                                                                               |
| operator\<=()                        | Checks if a number is less than or equal to an other number.                                                                                   |
| operator\>()                         | Checks if a number is greater than an other number.                                                                                            |
| [operator\>=()](date-class.md)       | Checks if a number is greater than or equal to an other number.                                                                                |
| [operator=()](date-class.md)         | Assigns one number to another.                                                                                                                 |
| [operator==()](date-class.md)        | Checks if two numbers are equal.                                                                                                               |
| [operator!=()](date-class.md)        | Checks if two numbers are not equal.                                                                                                           |
| [operator\*=()](intervalds-class.md) | Multiplication assignment.                                                                                                                     |
| [operator/=()](intervalds-class.md)  | Division assignment.                                                                                                                           |
| operator%=()                         | Modulo assignment.                                                                                                                             |
| operator+=()                         | Addition assignment.                                                                                                                           |
| operator-=()                         | Subtraction assignment.                                                                                                                        |
| operator char()                      | Returns `Number` converted to native char.                                                                                                     |
| operator signed char()               | Returns `Number` converted to native signed char.                                                                                              |
| operator double()                    | Returns `Number` converted to a native double.                                                                                                 |
| operator float()                     | Returns `Number` converted to a native float.                                                                                                  |
| operator int()                       | Returns `Number` converted to native integer.                                                                                                  |
| operator long()                      | Returns `Number` converted to native long.                                                                                                     |
| operator long double()               | Returns `Number` converted to a native long double.                                                                                            |
| operator short()                     | Returns `Number` converted to native short integer.                                                                                            |
| operator unsigned char()             | Returns `Number` converted to an unsigned native char.                                                                                         |
| operator unsigned int()              | Returns `Number` converted to an unsigned native integer.                                                                                      |
| operator unsigned long()             | Returns `Number` converted to an unsigned native long.                                                                                         |
| operator unsigned short()            | Returns `Number` converted to an unsigned native short integer.                                                                                |
| power()                              | Returns `Number` raised to the power of another number specified.                                                                              |
| prec()                               | Returns `Number` rounded to digits of precision specified.                                                                                     |
| round()                              | Returns `Number` rounded to decimal place specified. Negative values are allowed.                                                              |
| setNull()                            | Sets `Number` to `NULL`.                                                                                                                       |
| shift()                              | Returns a `Number` that is equivalent to the passed value `* 10^n`, where `n` may be positive or negative.                                     |
| sign()                               | Returns the sign of the value of the passed value: -1 for the passed value \< 0, 0 for the passed value == 0, and 1 for the passed value \> 0. |
| sin()                                | Returns sine of the number.                                                                                                                    |
| squareroot()                         | Returns the square root of the number.                                                                                                         |
| tan()                                | Returns tangent of the number.                                                                                                                 |
| toBytes()                            | Returns a `Bytes` object representing the `Number`.                                                                                            |
| toText()                             | Returns the number as a string formatted based on the format and NLS parameters.                                                               |
| trunc()                              | Returns a `Number` with the value truncated at `n` decimal place(s). Negative values are allowed.                                              |

### 13.22.1 Number()

`Number` class constructor.

| Syntax                                   | Description                                                                                                                                |
|:-----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `Number();`                              | Default constructor.                                                                                                                       |
| `Number(`<br>`   const Number &srcNum);` | Creates a copy of a `Number`.                                                                                                              |
| `Number(`<br>`   long double &val);`     | Translates a native long double into a `Number`. The `Number` is created using the precision of the platform-specific constant `LDBL_DIG`. |
| `Number(`<br>`   double val);`           | Translates a native double into a `Number`. The `Number` is created using the precision of the platform-specific constant `DBL_DIG`.       |
| `Number(`<br>`   float val);`            | Translates a native float into a `Number`. The `Number` is created using the precision of the platform-specific constant `FLT_DIG`.        |
| `Number(`<br>`   long val);`             | Translates a native long into a `Number`.                                                                                                  |
| `Number(`<br>`   int val);`              | Translates a native int into a `Number`.                                                                                                   |
| `Number(`<br>`   shot val);`             | Translates a native short into a `Number`.                                                                                                 |
| `Number(`<br>`   char val);`             | Translates a native char into a `Number`.                                                                                                  |
| `Number(`<br>`   signed char val);`      | Translates a native signed char into a `Number`.                                                                                           |
| `Number(`<br>`   unsigned long val);`    | Translates an native unsigned long into a `Number`.                                                                                        |
| `Number(`<br>`   unsigned int val);`     | Translates a native unsigned int into a `Number`.                                                                                          |
| `Number(`<br>`   unsigned short val);`   | Translates a native unsigned short into a `Number`.                                                                                        |
| `Number(`<br>`   unsigned char val);`    | Translates the unsigned character array into a `Number`.                                                                                   |

| Parameter | Description                                              |
|:----------|:---------------------------------------------------------|
| `srcNum`  | The source `Number` copied into the new `Number` object. |
| `val`     | The value assigned to the `Number` object.               |

### 13.22.2 abs()

This method returns the absolute value of the `Number` object.

#### Syntax

    const Number abs() const;

### 13.22.3 arcCos()

This method returns the arccosine of the `Number` object.

#### Syntax

    const Number arcCos() const;

### 13.22.4 arcSin()

This method returns the arcsine of the `Number` object.

#### Syntax

    const Number arcSin() const;

### 13.22.5 arcTan()

This method returns the arctangent of the `Number` object.

#### Syntax

    const Number arcTan() const;

### 13.22.6 arcTan2()

This method returns the arctangent of the `Number` object with the parameter specified. It returns `atan2 (val, x)` where `val` is the parameter specified and `x` is the current number object.

#### Syntax

    const Number arcTan2(
       const Number &val) const;

| Parameter | Description                                                       |
|:----------|:------------------------------------------------------------------|
| `val`     | Number parameter `val` to the arcTangent function `atan2(val,x)`. |

### 13.22.7 ceil()

This method returns the smallest integer that is greater than or equal to the `Number` object.

#### Syntax

    const Number ceil() const;

### 13.22.8 cos()

This method returns the cosine of the `Number` object.

#### Syntax

    const Number cos() const;

### 13.22.9 exp()

This method returns the natural exponential of the `Number` object.

#### Syntax

    const Number exp() const;

### 13.22.10 floor()

This method returns the largest integer that is less than or equal to the `Number` object.

#### Syntax

    const Number floor() const;

### 13.22.11 fromBytes()

This method returns a `Number` object represented by the byte string specified.

#### Syntax

    void fromBytes(
       const Bytes &str);

| Parameter | Description    |
|:----------|:---------------|
| `str`     | A byte string. |

### 13.22.12 fromText()

Sets `Number` object to value represented by a `string` or `UString`.

The value is interpreted based on the `fmt` and `nlsParam` parameters. In cases where `nlsParam` is not passed, the Globalization Support settings of the `envp` parameter are used.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for information on [`TO_NUMBER`](../sqlrf/TO_NUMBER.md)

| Syntax                                                                                                                                           | Description                                               |
|:-------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------|
| `void fromText(`<br>`   const Environment *envp,`<br>`   const string &number,`<br>`   const string &fmt,`<br>`   const string &nlsParam = "");` | Sets `Number` object to value represented by a `string`.  |
| `void fromText(`<br>`   const Environment *envp,`<br>`   const UString &number,`<br>`   const UString &fmt,`<br>`   const UString &nlsParam);`   | Sets `Number` object to value represented by a `UString`. |

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `envp`     | The OCCI environment.                                                                                                                                                                                  |
| `number`   | The number string to be converted to a `Number` object.                                                                                                                                                |
| `fmt`      | The format string.                                                                                                                                                                                     |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.22.13 hypCos()

This method returns the hypercosine of the `Number` object.

#### Syntax

    const Number hypCos() const;

### 13.22.14 hypSin()

This method returns the hypersine of the `Number` object.

#### Syntax

    const Number hypSin() const;

### 13.22.15 hypTan()

This method returns the hypertangent of the `Number` object.

#### Syntax

    const Number hypTan() const;

### 13.22.16 intPower()

This method returns a `Number` whose value is the number object raised to the power of the value specified.

#### Syntax

    const Number intPower(
       int val) const;

| Parameter | Description                          |
|:----------|:-------------------------------------|
| `val`     | Power to which the number is raised. |

### 13.22.17 isNull()

This method tests whether the `Number` object is `NULL`. If the `Number` object is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.22.18 ln()

This method returns the natural logarithm of the `Number` object.

#### Syntax

    const Number ln() const;

### 13.22.19 log()

This method returns the logarithm of the `Number` object with the base provided by the parameter specified.

#### Syntax

    const Number log(
       const Number &val) const;

| Parameter | Description                                       |
|:----------|:--------------------------------------------------|
| `val`     | The base to be used in the logarithm calculation. |

### 13.22.20 operator++()

Unary `operator++()`. This is a postfix operator.

| Syntax                                        | Description                                                                   |
|:----------------------------------------------|:------------------------------------------------------------------------------|
| `Number& operator++();`                       | This method returns the `Number` object incremented by `1`.                   |
| `const Number operator++(`<br>`   int incr);` | This method returns the `Number` object incremented by the integer specified. |

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `incr`    | The number by which the `Number` object is incremented. |

### 13.22.21 operator`--`()

Unary `operator--()`. This is a prefix operator.

| Syntax                                        | Description                                                                   |
|:----------------------------------------------|:------------------------------------------------------------------------------|
| `Number& operator--();`                       | This method returns the `Number` object decremented by `1`.                   |
| `const Number operator--(`<br>`   int decr);` | This method returns the `Number` object decremented by the integer specified. |

| Parameter | Description                                           |
|:----------|:------------------------------------------------------|
| `decr`    | The number by which the Number object is decremented. |

### 13.22.22 operator\*()

This method returns the product of the parameters specified.

#### Syntax

    Number operator*(
       const Number &first,

       const Number &second);

| Parameter | Description          |
|:----------|:---------------------|
| `first`   | First multiplicand.  |
| `second`  | Second multiplicand. |

### 13.22.23 operator/()

This method returns the quotient of the parameters specified.

#### Syntax

    Number operator/(
       const Number &dividend,
       const Number &divisor);

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `dividend` | The number to be divided.      |
| `divisor`  | The number by which to divide. |

### 13.22.24 operator%()

This method returns the remainder of the division of the parameters specified.

#### Syntax

    Number operator%(
       const Number &dividend,
       const Number &divider);

| Parameter  | Description                    |
|:-----------|:-------------------------------|
| `dividend` | The number to be divided.      |
| `divizor`  | The number by which to divide. |

### 13.22.25 operator+()

This method returns the sum of the parameters specified.

#### Syntax

    Number operator+(
       const Number &first,
       const Number &second);

| Parameter | Description                |
|:----------|:---------------------------|
| `first`   | First number to be added.  |
| `second`  | Second number to be added. |

### 13.22.26 operator-()

Unary `operator-()`. This method returns the negated value of the `Number `object.

#### Syntax

    const Number operator-();

### 13.22.27 operator-()

This method returns the difference between the parameters specified.

#### Syntax

    Number operator-(
       const Number &subtrahend,
       const Number &subtractor);

| Parameter    | Description                  |
|:-------------|:-----------------------------|
| `subtrahend` | The number to be reduced.    |
| `subtractor` | The number to be subtracted. |

### 13.22.28 operator\<()

This method checks whether the first parameter specified is less than the second parameter specified. If the first parameter is less than the second parameter, then `TRUE` is returned; otherwise, `FALSE` is returned. If either parameter equals infinity, then `FALSE` is returned.

#### Syntax

    bool operator<(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.29 operator\<=()

This method checks whether the first parameter specified is less than or equal to the second parameter specified. If the first parameter is less than or equal to the second parameter, then `TRUE` is returned; otherwise, `FALSE` is returned. If either `parameter` equals infinity, then `FALSE` is returned.

#### Syntax

    bool operator<=(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.30 operator\>()

This method checks whether the first parameter specified is greater than the second parameter specified. If the first parameter is greater than the second parameter, then `TRUE` is returned; otherwise, `FALSE` is returned. If either parameter equals infinity, then `FALSE` is returned.

#### Syntax

    bool operator>(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.31 operator\>=()

This method checks whether the first parameter specified is greater than or equal to the second parameter specified. If the first parameter is greater than or equal to the second parameter, then `TRUE` is returned; otherwise, `FALSE` is returned. If either parameter equals infinity, then `FALSE` is returned.

#### Syntax

    bool operator>=(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.32 operator==()

This method checks whether the parameters specified are equal. If the parameters are equal, then `TRUE` is returned; otherwise, `FALSE` is returned. If either parameter equals +infinity or -infinity, then `FALSE` is returned.

#### Syntax

    bool operator==(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.33 operator!=()

This method checks whether the first parameter specified equals the second parameter specified. If the parameters are not equal, `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!=(
       const Number &first,
       const Number &second);

| Parameter | Description                   |
|:----------|:------------------------------|
| `first`   | First number to be compared.  |
| `second`  | Second number to be compared. |

### 13.22.34 operator=()

This method assigns the value of the parameter specified to the `Number` object.

#### Syntax

    Number& operator=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.35 operator\*=()

This method multiplies the `Number` object by the parameter specified, and assigns the product to the `Number` object.

#### Syntax

    Number& operator*=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.36 operator/=()

This method divides the `Number` object by the parameter specified, and assigns the quotient to the `Number` object.

#### Syntax

    Number& operator/=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.37 operator%=()

This method divides the `Number` object by the parameter specified, and assigns the remainder to the `Number` object.

#### Syntax

    Number& operator%=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.38 operator+=()

This method adds the Number object and the parameter specified, and assigns the sum to the `Number` object.

#### Syntax

    Number& operator+=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.39 operator`-=`()

This method subtracts the parameter specified from the `Number` object, and assigns the difference to the `Number` object.

#### Syntax

    Number& operator-=(
       const Number &num);

| Parameter | Description                   |
|:----------|:------------------------------|
| `num`     | A parameter of type `Number`. |

### 13.22.40 operator char()

This method returns the value of the Number object converted to a native `char`.

#### Syntax

    operator char() const;

### 13.22.41 operator signed char()

This method returns the value of the Number object converted to a native `signed char`.

#### Syntax

    operator signed char() const;

### 13.22.42 operator double()

This method returns the value of the `Number` object converted to a native `double`.

#### Syntax

    operator double() const;

### 13.22.43 operator float()

This method returns the value of the `Number` object converted to a native `float`.

#### Syntax

    operator float() const;

### 13.22.44 operator int()

This method returns the value of the `Number` object converted to a native` int`.

#### Syntax

    operator int() const;

### 13.22.45 operator long()

This method returns the value of the `Number` object converted to a native `long`.

#### Syntax

    operator long() const;

### 13.22.46 operator long double()

This method returns the value of the `Number` object converted to a native `long double`.

#### Syntax

    operator long double() const;

### 13.22.47 operator short()

This method returns the value of the `Number` object converted to a native `short` integer.

#### Syntax

    operator short() const;

### 13.22.48 operator unsigned char()

This method returns the value of the `Number` object converted to a native `unsigned char`.

#### Syntax

    operator unsigned char() const;

### 13.22.49 operator unsigned int()

This method returns the value of the `Number` object converted to a native `unsigned int`.

#### Syntax

    operator unsigned int() const;

### 13.22.50 operator unsigned long()

This method returns the value of the `Number` object converted to a native `unsigned long`.

#### Syntax

    operator unsigned long() const;

### 13.22.51 operator unsigned short()

This method returns the value of the `Number` object converted to a native `unsigned short` integer.

#### Syntax

    operator unsigned short() const;

### 13.22.52 power()

This method returns the value of the `Number` object raised to the power of the value provided by the parameter specified.

#### Syntax

    const Number power(
       const Number &val) const;

| Parameter | Description                                     |
|:----------|:------------------------------------------------|
| `val`     | The power to which the number has to be raised. |

### 13.22.53 prec()

This method returns the value of the `Number` object rounded to the digits of precision provided by the parameter specified.

#### Syntax

    const Number prec(
       int digits) const;

| Parameter | Description                        |
|:----------|:-----------------------------------|
| `digits`  | The number of digits of precision. |

### 13.22.54 round()

This method returns the value of the `Number` object rounded to the decimal place provided by the parameter specified.

#### Syntax

    const Number round(
       int decPlace) const;

| Parameter  | Description                                             |
|:-----------|:--------------------------------------------------------|
| `decPlace` | The number of digits to the right of the decimal point. |

### 13.22.55 setNull()

This method sets the value of the `Number` object to `NULL`.

#### Syntax

    void setNull();

### 13.22.56 shift()

This method returns the `Number` object multiplied by 10 to the power provided by the parameter specified.

#### Syntax

    const Number shift(
       int val) const;

| Parameter | Description       |
|:----------|:------------------|
| `val`     | An integer value. |

### 13.22.57 sign()

This method returns the sign of the value of the `Number` object. If the `Number` object is negative, then create a `Date` object using integer parameters is returned. If the `Number` object equals `0`, then create a `Date` object using integer parameters is returned. If the `Number` object is positive, then `1` is returned.

#### Syntax

    const int sign() const;

### 13.22.58 sin()

This method returns the sin of the `Number` object.

#### Syntax

    const Number sin() const;

### 13.22.59 squareroot()

This method returns the square root of the `Number` object.

#### Syntax

    const Number squareroot() const;

### 13.22.60 tan()

This method returns the tangent of the `Number` object.

#### Syntax

    const Number tan() const;

### 13.22.61 toBytes()

This method converts the `Number` object into a `Bytes` object. The bytes representation is assumed to be in length excluded format, that is, the `Byte.length()` method gives the length of valid bytes and the `0`th byte is the exponent byte.

#### Syntax

    Bytes toBytes() const;

### 13.22.62 toText()

Convert the `Number` object to a formatted `string` or `UString` based on the parameters specified.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md)for information on [`TO_NUMBER`](../sqlrf/TO_NUMBER.md)

| Syntax                                                                                                                   | Description                                                                            |
|:-------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------|
| `string toText(`<br>`   const Environment *envp,`<br>`   const string &fmt,`<br>`   const string &nlsParam = "") const;` | Convert the `Number` object to a formatted `string` based on the parameters specified. |
| `UString toText(`<br>`   const Environment *envp,`<br>`   const UString &fmt,`<br>`   const UString &nlsParam) const;`   | Convert the `Number` object to a `UString` based on the parameters specified.          |

| Parameter  | Description                                                                                                                                                                                            |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `envp`     | The OCCI environment.                                                                                                                                                                                  |
| `fmt`      | The format string.                                                                                                                                                                                     |
| `nlsParam` | The NLS parameters string. If `nlsParam` is specified, this determines the NLS parameters to be used for the conversion. If `nlsParam` is not specified, the NLS parameters are picked up from `envp`. |

### 13.22.63 trunc()

This method returns the `Number` object truncated at the number of decimal places provided by the parameter specified.

#### Syntax

    const Number trunc(
       int decPlace) const;

| Parameter  | Description                                                                                   |
|:-----------|:----------------------------------------------------------------------------------------------|
| `decPlace` | The number of places to the right of the decimal place at which the value is to be truncated. |
