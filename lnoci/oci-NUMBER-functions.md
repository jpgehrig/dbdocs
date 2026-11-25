Lists and describes the OCI `NUMBER` functions.

Table 28-11 describes the OCI `NUMBER` functions that are described in this section.

**See Also:**

[OCINumber Examples](object-relational-data-types-in-oci.md)

Table 28-11 NUMBER Functions

| Function               | Purpose                                                              |
|:-----------------------|:---------------------------------------------------------------------|
| OCINumberAbs()         | Compute the absolute value                                           |
| OCINumberAdd()         | Add a `NUMBER` to a `NUMBER`                                         |
| OCINumberArcCos()      | Compute the arc cosine                                               |
| OCINumberArcSin()      | Compute the arc sine                                                 |
| OCINumberArcTan()      | Compute the arc tangent                                              |
| OCINumberArcTan2()     | Compute the arc tangent given two arguments for `NUMBER`             |
| OCINumberAssign()      | Assign one `NUMBER` to another                                       |
| OCINumberCeil()        | Compute the ceiling of `NUMBER`                                      |
| OCINumberCmp()         | Compare one `NUMBER` with another `NUMBER`                           |
| OCINumberCos()         | Compute the cosine                                                   |
| OCINumberDec()         | Decrement a `NUMBER`                                                 |
| OCINumberDiv()         | Divide a `NUMBER` by a `NUMBER`                                      |
| OCINumberExp()         | Raise e to the specified Oracle `NUMBER` power                       |
| OCINumberFloor()       | Compute the floor value of a `NUMBER`                                |
| OCINumberFromInt()     | Convert an integer to an Oracle `NUMBER`                             |
| OCINumberFromReal()    | Convert a real type to an Oracle `NUMBER`                            |
| OCINumberFromText()    | Convert a string to an Oracle `NUMBER`                               |
| OCINumberHypCos()      | Compute the hyperbolic cosine                                        |
| OCINumberHypSin()      | Compute the hyperbolic sine                                          |
| OCINumberHypTan()      | Compute the hyperbolic tangent                                       |
| OCINumberInc()         | Increment an Oracle `NUMBER`                                         |
| OCINumberIntPower()    | Raise a given base to an integer power                               |
| OCINumberIsInt()       | Test if a `NUMBER` is an integer                                     |
| OCINumberIsZero()      | Test if a `NUMBER` is zero                                           |
| OCINumberLn()          | Compute the natural logarithm                                        |
| OCINumberLog()         | Compute the logarithm to an arbitrary base                           |
| OCINumberMod()         | Gets the modulus (remainder) of the division of two Oracle `NUMBER`s |
| OCINumberMul()         | Multiply one Oracle `NUMBER` by another Oracle `NUMBER`              |
| OCINumberNeg()         | Negates an Oracle `NUMBER`                                           |
| OCINumberPower()       | Raises a given base to a given exponent                              |
| OCINumberPrec()        | Round a `NUMBER` to a specified number of decimal places             |
| OCINumberRound()       | Round an Oracle `NUMBER` to a specified decimal place                |
| OCINumberSetPi()       | Initialize a `NUMBER` to pi                                          |
| OCINumberSetZero()     | Initialize a `NUMBER` to zero                                        |
| OCINumberShift()       | Multiply by 10, shifting a specified number of decimal places        |
| OCINumberSign()        | Obtain the sign of an Oracle `NUMBER`                                |
| OCINumberSin()         | Compute the sine                                                     |
| OCINumberSqrt()        | Compute the square root of a `NUMBER`                                |
| OCINumberSub()         | Subtract a `NUMBER` from a `NUMBER`                                  |
| OCINumberTan()         | Compute the tangent                                                  |
| OCINumberToInt()       | Convert an Oracle `NUMBER` to an integer                             |
| OCINumberToReal()      | Convert an Oracle `NUMBER` to a real type                            |
| OCINumberToRealArray() | Convert an array of `NUMBER` to a real array.                        |
| OCINumberToText()      | Convert an Oracle `NUMBER` to a string                               |
| OCINumberTrunc()       | Truncate an Oracle `NUMBER` at a specified decimal place             |

### 28.4.1 OCINumberAbs()

Computes the absolute value of an Oracle `NUMBER`.

#### Purpose

Computes the absolute value of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberAbs ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Input `NUMBER`.

result (OUT)
The absolute value of the input `NUMBER`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.2 OCINumberAdd()

Adds a `NUMBER` to another `NUMBER`.

#### Purpose

Adds a `NUMBER` to another `NUMBER`.

#### Syntax

    sword OCINumberAdd ( OCIError              *err,
                         const OCINumber       *number1,
                         const OCINumber       *number2,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1, number2 (IN)
The first `NUMBER` to be added to the second `NUMBER`.

result (OUT)
Result of adding `number1` to `number2`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberSub()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.3 OCINumberArcCos()

Takes the arc cosine in radians of an Oracle `NUMBER`.

#### Purpose

Takes the arc cosine in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberArcCos ( OCIError            *err,
                            const OCINumber     *number,
                            OCINumber           *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the arc cosine.

result (OUT)
Result of the arc cosine in radians.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`, if `number` is less than –1, or if `number` is greater than 1.

**Related Topics**

- OCINumberCos()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.4 OCINumberArcSin()

Takes the arc sine in radians of an Oracle `NUMBER`.

#### Purpose

Takes the arc sine in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberArcSin ( OCIError              *err,
                            const OCINumber       *number,
                            OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the arc sine.

result (OUT)
Result of the arc sine in radians.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`, if `number` is less than –1, or if `number` is greater than 1.

**Related Topics**

- OCINumberSin()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.5 OCINumberArcTan()

Takes the arc tangent in radians of an Oracle `NUMBER`.

#### Purpose

Takes the arc tangent in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberArcTan ( OCIError             *err,
                            const OCINumber      *number,
                            OCINumber            *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the arc tangent.

result (OUT)
Result of the arc tangent in radians.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberTan()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.6 OCINumberArcTan2()

Takes the arc tangent given two arguments for Oracle `NUMBER`.

#### Purpose

Takes the arc tangent given two arguments for Oracle `NUMBER`.

#### Syntax

    sword OCINumberArcTan2 ( OCIError              *err,
                             const OCINumber       *number1,
                             const OCINumber       *number2,
                             OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1 (IN)
Argument 1 of the arc tangent.

number2 (IN)
Argument 2 of the arc tangent.

result (OUT)
Result of the arc tangent in radians.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL` or if `number2` equals 0.

**Related Topics**

- OCINumberTan()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.7 OCINumberAssign()

Assigns one Oracle `NUMBER` to another Oracle `NUMBER`.

#### Purpose

Assigns one Oracle `NUMBER` to another Oracle `NUMBER`.

#### Syntax

    sword OCINumberAssign ( OCIError              *err,
                            const OCINumber       *from,
                            OCINumber             *to );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

from (IN)
`NUMBER` to be assigned.

to (OUT)
`NUMBER` copied into.

#### Comments

Assigns the `NUMBER` identified by `from` to the `NUMBER` identified by `to`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberCmp()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.8 OCINumberCeil()

Computes the ceiling value of an Oracle `NUMBER`.

#### Purpose

Computes the ceiling value of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberCeil ( OCIError              *err,
                          const OCINumber       *number,
                          OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Input `NUMBER`.

result (OUT)
Output that contains the ceiling value of the input `NUMBER`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberFloor()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.9 OCINumberCmp()

Compares one Oracle `NUMBER` with another Oracle `NUMBER`.

#### Purpose

Compares one Oracle `NUMBER` with another Oracle `NUMBER`.

#### Syntax

    sword OCINumberCmp ( OCIError            *err,
                         const OCINumber     *number1,
                         const OCINumber     *number2,
                         sword               *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1, number2 (IN)
The first `NUMBER` to compare with the second `NUMBER`.

result (OUT)
Comparison result as specified in Table 28-12.

Table 28-12 Comparison Results Returned by the result Parameter for OCINumberCmp()

| Comparison Result      | Output in result Parameter |
|:-----------------------|:---------------------------|
| `number1` \< `number2` | negative                   |
| `number1` = `number2`  | `0`                        |
| `number1` \> `number2` | positive                   |

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberAssign()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.10 OCINumberCos()

Computes the cosine in radians of an Oracle `NUMBER`.

#### Purpose

Computes the cosine in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberCos ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the cosine in radians.

result (OUT)
Result of the cosine.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberArcCos()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.11 OCINumberDec()

12.1.0.2, added a short description.

#### Purpose

Decrements an Oracle `NUMBER` in place.

#### Syntax

    sword OCINumberDec ( OCIError  *err,
                         OCINumber *number );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN/OUT)
A positive Oracle `NUMBER` to be decremented.

#### Comments

Decrements an Oracle `NUMBER` in place. It is assumed that the input is an integer between 0 and 100^21-2. If the input is too large, it is treated as 0; the result is an Oracle `NUMBER` 1. If the input is not a positive integer, the result is unpredictable.

#### Returns

This function returns an error if the input `NUMBER` is `NULL`.

**Related Topics**

- OCINumberInc()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.12 OCINumberDiv()

Divides one Oracle `NUMBER` by another Oracle `NUMBER`.

#### Purpose

Divides one Oracle `NUMBER` by another Oracle `NUMBER`.

#### Syntax

    sword OCINumberDiv ( OCIError               *err,
                         const OCINumber        *number1,
                         const OCINumber        *number2,
                         OCINumber              *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1 (IN)
Pointer to the numerator.

number2 (IN)
Pointer to the denominator.

result (OUT)
Division result.

#### Comments

Divides `number1` by `number2` and returns the result in `result`.

#### Returns

This function returns an error if any of the following statements is true:

- Any of the `NUMBER` arguments is `NULL`.

- There is an underflow error.

- There is a divide-by-zero error.

**Related Topics**

- OCINumberMul()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.13 OCINumberExp()

Raises e to the specified Oracle `NUMBER` power.

#### Purpose

Raises e to the specified Oracle `NUMBER` power.

#### Syntax

    sword OCINumberExp ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
This function raises e to this Oracle `NUMBER` power.

result (OUT)
Output of exponentiation.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberLn()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.14 OCINumberFloor()

Computes the floor (round down) value of an Oracle `NUMBER`.

#### Purpose

Computes the floor (round down) value of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberFloor ( OCIError              *err,
                           const OCINumber       *number,
                           OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Input `NUMBER`.

result (OUT)
The floor (round down) value of the input `NUMBER`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberCeil()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.15 OCINumberFromInt()

Converts an integer to an Oracle `NUMBER`.

#### Purpose

Converts an integer to an Oracle `NUMBER`.

#### Syntax

    sword OCINumberFromInt ( OCIError            *err,
                             const void          *inum,
                             uword                inum_length,
                             uword                inum_s_flag,
                             OCINumber           *number );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

inum (IN)
Pointer to the integer to convert.

inum_length (IN)
Size of the integer.

inum_s_flag (IN)
Flag that designates the sign of the integer, as follows:

- `OCI_NUMBER_UNSIGNED` - Unsigned values

- `OCI_NUMBER``_SIGNED` - Signed values

number (OUT)
Given integer converted to Oracle `NUMBER`.

#### Comments

This is a native type conversion function. It converts any Oracle standard system-native integer type, such as `ub4` or `sb2`, to an Oracle `NUMBER`.

#### Returns

This function returns an error if the number is too big to fit into an Oracle `NUMBER`, if `number` or `inum` is `NULL`, or if an invalid sign flag value is passed in `inum_s_flag`.

**Related Topics**

- OCINumberToInt()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.16 OCINumberFromReal()

Converts a real (floating-point) type to an Oracle `NUMBER`.

#### Purpose

Converts a real (floating-point) type to an Oracle `NUMBER`.

#### Syntax

    sword OCINumberFromReal ( OCIError           *err,
                              const void         *rnum,
                              uword               rnum_length,
                              OCINumber          *number );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rnum (IN)
Pointer to the floating-point number to convert.

rnum_length (IN)
The size of the desired result, which equals `sizeof`({`float` \| `double` \| `long double`}).

number (OUT)
Given float converted to Oracle `NUMBER`.

#### Comments

This is a native type conversion function. It converts a system-native floating-point type to an Oracle `NUMBER`.

#### Returns

This function returns an error if `number` or `rnum` is `NULL`, or if `rnum_length` equals zero.

**Related Topics**

- OCINumberFromText()

### 28.4.17 OCINumberFromText()

Converts a character string to an Oracle `NUMBER`.

#### Purpose

Converts a character string to an Oracle `NUMBER`.

#### Syntax

    sword OCINumberFromText ( OCIError           *err,
                              const OraText      *str,
                              ub4                 str_length,
                              const OraText      *fmt,
                              ub4                 fmt_length,
                              const OraText      *nls_params,
                              ub4                 nls_p_length,
                              OCINumber          *number );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

str (IN)
Input string to convert to Oracle `NUMBER`.

str_length (IN)
Size of the input string.

fmt (IN)
Conversion format.

fmt_length (IN)
Length of the `fmt` parameter.

nls_params (IN)
Globalization support format specification. If it is the `NULL` string (""), then the default parameters for the session are used.

nls_p_length (IN)
Length of the `nls_params` parameter.

number (OUT)
Given string converted to `NUMBER`.

#### Comments

Converts the given string to a `NUMBER` according to the specified format. See the `TO_NUMBER` conversion function described in the [Oracle Database SQL Language Reference](../sqlrf/TO_NUMBER.md) for a description of format and multilingual parameters.

#### Returns

This function returns an error if there is an invalid format, an invalid multibyte format, or an invalid input string, if `number` or `str` is `NULL`, or if `str_length` is zero.

### 28.4.18 OCINumberHypCos()

Computes the hyperbolic cosine of an Oracle `NUMBER`.

#### Purpose

Computes the hyperbolic cosine of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberHypCos ( OCIError              *err,
                            const OCINumber       *number,
                            OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the cosine hyperbolic.

result (OUT)
Result of the cosine hyperbolic.

#### Returns

This function returns an error if either of the `number` arguments is `NULL`.

**Note:**

An Oracle `NUMBER` overflow causes an unpredictable result value.

**Related Topics**

- OCINumberHypSin()
- OCINumberHypTan()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.19 OCINumberHypSin()

Computes the hyperbolic sine of an Oracle `NUMBER`.

#### Purpose

Computes the hyperbolic sine of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberHypSin ( OCIError              *err,
                            const OCINumber       *number,
                            OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the sine hyperbolic.

result (OUT)
Result of the sine hyperbolic.

#### Returns

This function returns an error if either of the `NUMBER` arguments is `NULL`.

**Note:**

An Oracle `NUMBER` overflow causes an unpredictable result value.

**Related Topics**

- OCINumberHypCos()
- OCINumberHypTan()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.20 OCINumberHypTan()

Computes the hyperbolic tangent of an Oracle `NUMBER`.

#### Purpose

Computes the hyperbolic tangent of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberHypTan ( OCIError              *err,
                            const OCINumber       *number,
                            OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the tangent hyperbolic.

result (OUT)
Result of the tangent hyperbolic.

#### Returns

This function returns an error if either of the `NUMBER` arguments is `NULL`.

**Note:**

An Oracle `NUMBER` overflow causes an unpredictable result value.

**Related Topics**

- OCINumberHypCos()
- OCINumberHypSin()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.21 OCINumberInc()

Increments an Oracle `NUMBER`.

#### Purpose

Increments an Oracle `NUMBER`.

#### Syntax

    sword OCINumberInc ( OCIError   *err,
                         OCINumber  *number );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN/OUT)
A positive Oracle `NUMBER` to be incremented.

#### Comments

Increments an Oracle `NUMBER` in place. It is assumed that the input is an integer between 0 and 100^21-2. If the input is too large, it is treated as 0 - the result is an Oracle `NUMBER` 1. If the input is not a positive integer, the result is unpredictable.

#### Returns

This function returns an error if the input `NUMBER` is `NULL`.

**Related Topics**

- OCINumberDec()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.22 OCINumberIntPower()

Raises a given base to a given integer power.

#### Purpose

Raises a given base to a given integer power.

#### Syntax

    sword OCINumberIntPower ( OCIError             *err,
                              const OCINumber      *base,
                              const sword           exp,
                              OCINumber            *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

base (IN)
Base of the exponentiation.

exp (IN)
Exponent to which the base is raised.

result (OUT)
Output of exponentiation.

#### Returns

This function returns an error if either of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberPower()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.23 OCINumberIsInt()

Tests if an OCINumber is an integer.

#### Purpose

Tests if an OCINumber is an integer.

#### Syntax

    sword OCINumberIsInt ( OCIError         *err,
                           const OCINumber  *number,
                           boolean          *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
`NUMBER` to be tested.

result (OUT)
Set to `TRUE` if integer value; otherwise, `FALSE`

#### Returns

This function returns an error if `number` or `result` is `NULL`.

**Related Topics**

- OCINumberRound()
- OCINumberTrunc()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.24 OCINumberIsZero()

Tests if the given `NUMBER` equals zero.

#### Purpose

Tests if the given `NUMBER` equals zero.

#### Syntax

    sword OCINumberIsZero ( OCIError            *err,
                            const OCINumber     *number,
                            boolean             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
`NUMBER` to compare.

result (OUT)
Set to `TRUE` if equal to zero; otherwise, set to `FALSE`.

#### Returns

This function returns an error if the `NUMBER` argument is `NULL`.

**Related Topics**

- OCINumberSetZero()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.25 OCINumberLn()

Takes the natural logarithm (base e) of an Oracle `NUMBER`.

#### Purpose

Takes the natural logarithm (base e) of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberLn ( OCIError              *err,
                        const OCINumber       *number,
                        OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Logarithm of this `NUMBER` is computed.

result (OUT)
Logarithm result.

#### Returns

This function returns an error if either of the `NUMBER` arguments is `NULL`, or if `number` is less than or equal to zero.

**Related Topics**

- OCINumberExp()
- OCINumberLog()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.26 OCINumberLog()

Takes the logarithm, to any base, of an Oracle `NUMBER`.

#### Purpose

Takes the logarithm, to any base, of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberLog ( OCIError              *err,
                         const OCINumber       *base,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

base (IN)
Base of the logarithm.

number (IN)
Operand.

result (OUT)
Logarithm result.

#### Returns

This function returns an error if:

- Any of the `NUMBER` arguments is `NULL`

- The value of `number` \<= 0

- The value of `base` \<= 0

**Related Topics**

- OCINumberLn()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.27 OCINumberMod()

Gets the modulus (remainder) of the division of two Oracle `NUMBER`s.

#### Purpose

Gets the modulus (remainder) of the division of two Oracle `NUMBER`s.

#### Syntax

    sword OCINumberMod ( OCIError              *err,
                         const OCINumber       *number1,
                         const OCINumber       *number2,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1 (IN)
Pointer to the numerator.

number2 (IN)
Pointer to the denominator.

result (OUT)
Remainder of the result.

#### Returns

This function returns an error if `number1` or `number2` is `NULL`, or if there is a divide-by-zero error.

**Related Topics**

- OCINumberDiv()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.28 OCINumberMul()

Multiplies one Oracle `NUMBER` by another Oracle `NUMBER`.

#### Purpose

Multiplies one Oracle `NUMBER` by another Oracle `NUMBER`.

#### Syntax

    sword OCINumberMul ( OCIError              *err,
                         const OCINumber       *number1,
                         const OCINumber       *number2,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1 (IN)
`NUMBER` to multiply.

number2 (IN)
`NUMBER` to multiply.

result (OUT)
Multiplication result.

#### Comments

Multiplies `number1` with `number2` and returns the result in `result`.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberDiv()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.29 OCINumberNeg()

Negates an Oracle `NUMBER`.

#### Purpose

Negates an Oracle `NUMBER`.

#### Syntax

    sword OCINumberNeg ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
`NUMBER` to negate.

result (OUT)
Contains negated value of `number`.

#### Returns

This function returns an error if either of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberAbs()
- OCINumberSign()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.30 OCINumberPower()

Raises a given base to a given exponent.

#### Purpose

Raises a given base to a given exponent.

#### Syntax

    sword OCINumberPower ( OCIError              *err,
                           const OCINumber       *base,
                           const OCINumber       *number,
                           OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

base (IN)
Base of the exponentiation.

number (IN)
Exponent to which the base is to be raised.

result (OUT)
Output of exponentiation.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberExp()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.31 OCINumberPrec()

Rounds an `OCINumber` to a specified number of decimal digits.

#### Purpose

Rounds an `OCINumber` to a specified number of decimal digits.

#### Syntax

    sword OCINumberPrec ( OCIError            *err,
                          const OCINumber     *number,
                          eword                nDigs,
                          OCINumber           *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
The number for which to set precision.

nDigs (IN)
The number of decimal digits desired in the result.

result (OUT)
The result.

#### Comments

Performs a floating-point round with respect to the number of digits.

#### Returns

This function returns an error any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberRound()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.32 OCINumberRound()

Rounds an Oracle `NUMBER` to a specified decimal place.

#### Purpose

Rounds an Oracle `NUMBER` to a specified decimal place.

#### Syntax

    sword OCINumberRound ( OCIError              *err,
                           const OCINumber       *number,
                           sword                  decplace,
                           OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
`NUMBER` to round.

decplace (IN)
Number of decimal digits to the right of the decimal point to round to. Negative values are allowed.

result (OUT)
Output of rounding.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberTrunc()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.33 OCINumberSetPi()

Sets an `OCINumber` to pi.

#### Purpose

Sets an `OCINumber` to pi.

#### Syntax

    void OCINumberSetPi ( OCIError *err,
                          OCINumber *num );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

num (OUT)
`NUMBER` set to the value of pi.

#### Comments

Initializes the given `NUMBER` to the value of pi.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.34 OCINumberSetZero()

Initializes an Oracle `NUMBER` to zero.

#### Purpose

Initializes an Oracle `NUMBER` to zero.

#### Syntax

    void OCINumberSetZero ( OCIError      *err
                            OCINumber     *num );

#### Parameters

err (IN)
A valid OCI error handle. This function does not check for errors because the function never produces an error.

num (IN/OUT)
Oracle `NUMBER` to initialize to zero value.

#### Comments

None.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.35 OCINumberShift()

Multiplies a `NUMBER` by a power of 10 by shifting it a specified number of decimal places.

#### Purpose

Multiplies a `NUMBER` by a power of 10 by shifting it a specified number of decimal places.

#### Syntax

    sword OCINumberShift ( OCIError         *err,
                           const OCINumber  *number,
                           const sword      nDig,
                           OCINumber        *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Oracle `NUMBER` to be shifted.

nDig (IN)
Number of decimal places to shift.

result (OUT)
Shift result.

#### Comments

Multiplies `number` by 10^`nDig` and sets `product` to the result.

#### Returns

This function returns an error if the input `number` is `NULL`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.36 OCINumberSign()

Gets sign of an Oracle `NUMBER`.

#### Purpose

Gets sign of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberSign ( OCIError             *err,
                          const OCINumber      *number,
                          sword                *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Oracle `NUMBER` whose sign is returned.

result (OUT)
Table 28-13 lists the possible return values.

Table 28-13 Values of result

| Value of number | Output in result Parameter |
|:----------------|:---------------------------|
| `number` \< 0   | -1                         |
| `number` == 0   | 0                          |
| `number` \> 0   | 1                          |

#### Returns

This function returns an error if `number` or `result` is `NULL`.

**Related Topics**

- OCINumberAbs()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.37 OCINumberSin()

Computes the sine in radians of an Oracle `NUMBER`.

#### Purpose

Computes the sine in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberSin ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the sine in radians.

result (OUT)
Result of the sine.

#### Returns

This function returns an error if either of the `number` arguments is `NULL`.

**Related Topics**

- OCINumberArcSin()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.38 OCINumberSqrt()

Computes the square root of an Oracle `NUMBER`.

#### Purpose

Computes the square root of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberSqrt ( OCIError           *err,
                         const OCINumber     *number,
                         OCINumber           *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Input `NUMBER`.

result (OUT)
Output that contains the square root of the input `NUMBER`.

#### Returns

This function returns an error if `number` is `NULL` or `number` is negative.

**Related Topics**

- OCINumberPower()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.39 OCINumberSub()

Subtracts one Oracle `NUMBER` from another Oracle `NUMBER`.

#### Purpose

Subtracts one Oracle `NUMBER` from another Oracle `NUMBER`.

#### Syntax

    sword OCINumberSub ( OCIError             *err,
                         const OCINumber      *number1,
                         const OCINumber      *number2,
                         OCINumber            *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number1, number2 (IN)
This function subtracts `number2` from `number1`.

result (OUT)
Subtraction result.

#### Comments

Subtracts `number2` from `number1` and returns the result in `result`.

#### Returns

This function returns an error if any of the `number` arguments is `NULL`.

**Related Topics**

- OCINumberAdd()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.40 OCINumberTan()

Computes the tangent in radians of an Oracle `NUMBER`.

#### Purpose

Computes the tangent in radians of an Oracle `NUMBER`.

#### Syntax

    sword OCINumberTan ( OCIError              *err,
                         const OCINumber       *number,
                         OCINumber             *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Argument of the tangent in radians.

result (OUT)
Result of the tangent.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberArcTan()
- OCINumberArcTan2()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.41 OCINumberToInt()

Converts an Oracle `NUMBER` type to integer.

#### Purpose

Converts an Oracle `NUMBER` type to integer.

#### Syntax

    sword OCINumberToInt ( OCIError              *err,
                           const OCINumber       *number,
                           uword                 rsl_length,
                           uword                 rsl_flag,
                           void                  *rsl );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Oracle `NUMBER` to convert.

rsl_length (IN)
Size of the desired result.

rsl_flag (IN)
Flag that designates the sign of the output, as follows:

- `OCI_NUMBER_UNSIGNED` - Unsigned values

- `OCI_NUMBER_SIGNED` - Signed values

rsl (OUT)
Pointer to space for the result.

#### Comments

This is a native type conversion function. It converts the given Oracle `NUMBER` into an integer of the form `xbn`, such as `ub2`, `ub4`, or `sb2`.

#### Returns

This function returns an error if `number` or `rsl` is `NULL`, if `number` is too big (overflow) or too small (underflow), or if an invalid sign flag value is passed in `rsl_flag`.

**Related Topics**

- OCINumberFromInt()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.42 OCINumberToReal()

Converts an Oracle `NUMBER` type to a real type.

#### Purpose

Converts an Oracle `NUMBER` type to a real type.

#### Syntax

    sword OCINumberToReal ( OCIError            *err,
                            const OCINumber     *number,
                            uword                rsl_length,
                            void                *rsl );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Oracle `NUMBER` to convert.

rsl_length (IN)
The size of the desired result, which equals `sizeof`({ `float` \| `double` \| `long double`}).

rsl (OUT)
Pointer to space for storing the result.

#### Comments

This is a native type conversion function. It converts an Oracle `NUMBER` into a system-native real type. This function only converts `NUMBER`s up to LDBL_DIG, DBL_DIG, or FLT_DIG digits of precision and removes trailing zeros. These constants are defined in `float.h`.

You must pass a valid `OCINumber` to this function. Otherwise, the result is undefined.

**Related Topics**

- OCINumberFromReal()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.43 OCINumberToRealArray()

Converts an array of `NUMBER` to an array of real type.

#### Purpose

Converts an array of `NUMBER` to an array of real type.

#### Syntax

    sword OCINumberToRealArray ( OCIError         *err,
                                 const OCINumber  **number,
                                 uword            elems,
                                 uword            rsl_length,
                                 void             *rsl );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Pointer to array of `NUMBER` to be converted.

elems (IN)
Maximum number of `NUMBER` pointers.

rsl_length (IN)
The size of the desired result, that is, `sizeof({ float | double | long double `}`)`.

rsl (OUT)
Pointer to array of space for storing the result.

#### Comments

Native type conversion function that converts an Oracle `NUMBER` into a system-native real type. This function only converts numbers up to` LDBL_DI``G`, `DBL_DIG`, or `FLT_DIG` digits of precision and removes trailing zeroes. The constants are defined in the `float.h` header file.

You must pass a valid `OCINumber` to this function. Otherwise, the result is undefined.

#### Returns

`OCI_SUCCESS`, if the function completes successfully; `OCI_INVALID_HANDLE`, if `err` is `NULL`; or `OCI_ERROR`, if `number` or `rsl` is `NULL` or `rsl_length` is 0.

**Related Topics**

- OCINumberToReal()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.44 OCINumberToText()

Converts an Oracle `NUMBER` to a character string according to a specified format.

#### Purpose

Converts an Oracle `NUMBER` to a character string according to a specified format.

#### Syntax

    sword OCINumberToText ( OCIError             *err,
                            const OCINumber      *number,
                            const OraText        *fmt,
                            ub4                   fmt_length,
                            const OraText        *nls_params,
                            ub4                   nls_p_length,
                            ub4                  *buf_size,
                            OraText              *buf );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Oracle `NUMBER` to convert.

fmt (IN)
Conversion format.

fmt_length (IN)
Length of the `fmt` parameter.

nls_params (IN)
Globalization support format specification. If it is a `NULL` string (`(text *)0` ), then the default parameters for the session is used.

nls_p_length (IN)
Length of the `nls_params` parameter.

buf_size (IN)
Size of the buffer.

buf (OUT)
Buffer into which the converted string is placed.

#### Comments

See the `TO_NUMBER` conversion function described in the [Oracle Database SQL Language Reference](../sqlrf/TO_NUMBER.md)for a description of format and globalization support parameters.

The converted number string is stored in `buf`, up to a maximum of `buf_size` bytes.

#### Returns

This function returns an error if:

- The value of `number` or `buf` is `NULL`

- The buffer is too small

- An invalid format or invalid multibyte format is passed

- A number to text translation for given format causes an overflow

**Related Topics**

- OCINumberFromText()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.4.45 OCINumberTrunc()

Truncates an Oracle `NUMBER` at a specified decimal place.

#### Purpose

Truncates an Oracle `NUMBER` at a specified decimal place.

#### Syntax

    sword OCINumberTrunc ( OCIError             *err,
                           const OCINumber      *number,
                           sword                 decplace,
                           OCINumber            *result );

#### Parameters

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

number (IN)
Input `NUMBER`.

decplace (IN)
Number of decimal digits to the right of the decimal point at which to truncate. Negative values are allowed.

result (OUT)
Output of truncation.

#### Returns

This function returns an error if any of the `NUMBER` arguments is `NULL`.

**Related Topics**

- OCINumberRound()
- [OCIErrorGet()](miscellaneous-functions.md)
