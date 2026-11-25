The OLAP row functions extend the syntax of the SQL row functions for use with dimensional objects. If you use the SQL row functions, then this syntax is familiar. You can use these functions on relational data when loading it into cubes and cube dimensions, and with the OLAP functions when creating calculated measures.

This chapter describes the row functions of the OLAP expression syntax. It contains these topics:

- Row Functions in Alphabetical Order

- Row Functions By Category

### 3.1 Row Functions in Alphabetical Order

A B C D E F G H I L M N O P R S T U V W

#### A

- ABS
- ACOS
- ADD_MONTHS
- ASCII
- ASCIISTR
- ASIN
- ATAN
- ATAN2

#### B

- BIN_TO_NUM
- BITAND

#### C

- CAST
- CEIL
- CHARTOROWID
- CHR
- COALESCE
- CONCAT
- COS
- COSH
- CURRENT_DATE
- CURRENT_TIMESTAMP

#### D

- DBTIMEZONE
- DECODE

#### E

- EXP
- EXTRACT (datetime)

#### F

- FLOOR
- FROM_TZ

#### G

- GREATEST

#### H

- HEXTORAW

#### I

- INITCAP
- INSTR

#### L

- LAST_DAY
- LEAST
- LENGTH
- LN
- LNNVL
- LOCALTIMESTAMP
- LOG
- LOWER
- LPAD
- LTRIM

#### M

- MOD
- MONTHS_BETWEEN

#### N

- NANVL
- NEW_TIME
- NEXT_DAY
- NLS_CHARSET_ID
- NLS_CHARSET_NAME
- NLS_INITCAP
- NLS_LOWER
- NLS_UPPER
- NLSSORT
- NULLIF
- NUMTODSINTERVAL
- NUMTOYMINTERVAL
- NVL
- NVL2

#### O

- ORA_HASH

#### P

- POWER

#### R

- RAWTOHEX
- REGEXP_COUNT
- REGEXP_INSTR
- REGEXP_REPLACE
- REGEXP_SUBSTR
- REMAINDER
- REPLACE
- ROUND (date)
- ROUND (number)
- ROWIDTOCHAR
- ROWIDTONCHAR
- RPAD
- RTRIM

#### S

- SESSIONTIMEZONE
- SIGN
- SIN
- SINH
- SOUNDEX
- SQRT
- SUBSTR
- SYS_CONTEXT
- SYSDATE
- SYSTIMESTAMP

#### T

- TAN
- TANH
- TO_BINARY_DOUBLE
- TO_BINARY_FLOAT
- TO_CHAR (character)
- TO_CHAR (datetime)
- TO_CHAR (number)
- TO_DATE
- TO_DSINTERVAL
- TO_NCHAR (character)
- TO_NCHAR (datetime)
- TO_NCHAR (number)
- TO_NUMBER
- TO_TIMESTAMP
- TO_TIMESTAMP_TZ
- TO_YMINTERVAL
- TRANSLATE
- TRANSLATE (USING)
- TRIM
- TRUNC (number)
- TZ_OFFSET

#### U

- UID
- UNISTR
- UPPER
- USER

#### V

- VSIZE

#### W

- WIDTH_BUCKET

### 3.2 Row Functions By Category

The row functions are grouped into the following categories:

- Numeric Functions

- Character Functions That Return Characters

- NLS Character Functions

- Character Functions That Return Numbers

- Datetime Functions

- General Comparison Functions

- Conversion Functions

- Encoding and Decoding Function

- Null-Related Functions

- Environment and Identifier Functions

#### 3.2.1 Numeric Functions

These functions accept numeric input and return numeric values:

- ABS
- ACOS
- ASIN
- ATAN
- ATAN2
- BITAND
- CEIL
- COS
- COSH
- EXP
- FLOOR
- LN
- LOG
- MOD
- NANVL
- POWER
- REMAINDER
- ROUND (number)
- SIGN
- SIN
- SINH
- SQRT
- TAN
- TANH
- TRUNC (number)
- WIDTH_BUCKET

#### 3.2.2 Character Functions That Return Characters

These functions accept character input and return character values:

- CHR
- CONCAT
- INITCAP
- LOWER
- LPAD
- LTRIM
- NLS_CHARSET_NAME
- NLS_INITCAP
- NLS_LOWER
- NLS_UPPER
- NLSSORT
- REGEXP_REPLACE
- REGEXP_SUBSTR
- REPLACE
- RPAD
- RTRIM
- SOUNDEX
- SUBSTR
- TRANSLATE
- TRIM
- UPPER

#### 3.2.3 NLS Character Functions

These functions return information about a character set:

- NLS_CHARSET_ID
- NLS_CHARSET_NAME

#### 3.2.4 Character Functions That Return Numbers

These functions accept character input and return numeric values:

- ASCII
- INSTR
- LENGTH
- REGEXP_COUNT
- REGEXP_INSTR

#### 3.2.5 Datetime Functions

These functions operate on date, timestamp, or interval values:

- ADD_MONTHS
- CURRENT_DATE
- CURRENT_TIMESTAMP
- DBTIMEZONE
- EXTRACT (datetime)
- FROM_TZ
- LAST_DAY
- LOCALTIMESTAMP
- MONTHS_BETWEEN
- NEW_TIME
- NEXT_DAY
- NUMTODSINTERVAL
- NUMTOYMINTERVAL
- ROUND (date)
- SESSIONTIMEZONE
- SYSDATE
- SYSTIMESTAMP
- TO_CHAR (datetime)
- TO_DSINTERVAL
- TO_TIMESTAMP
- TO_TIMESTAMP_TZ
- TO_YMINTERVAL
- TZ_OFFSET

#### 3.2.6 General Comparison Functions

These functions determine the greatest or least value in a set of values:

- GREATEST
- LEAST

#### 3.2.7 Conversion Functions

These functions change a value from one data type to another:

- ASCIISTR
- BIN_TO_NUM
- CAST
- CHARTOROWID
- HEXTORAW
- NUMTODSINTERVAL
- NUMTOYMINTERVAL
- RAWTOHEX
- ROWIDTOCHAR
- ROWIDTONCHAR
- TO_BINARY_DOUBLE
- TO_BINARY_FLOAT
- TO_CHAR (character)
- TO_CHAR (datetime)
- TO_CHAR (number)
- TO_DATE
- TO_DSINTERVAL
- TO_NCHAR (character)
- TO_NCHAR (datetime)
- TO_NCHAR (number)
- TO_NUMBER
- TO_TIMESTAMP
- TO_TIMESTAMP_TZ
- TO_YMINTERVAL
- TRANSLATE (USING)
- UNISTR

#### 3.2.8 Encoding and Decoding Function

These functions return a numeric value for each input value:

- DECODE
- ORA_HASH
- VSIZE

#### 3.2.9 Null-Related Functions

These functions facilitate null handling:

- COALESCE
- LNNVL
- NANVL
- NULLIF
- NVL
- NVL2

#### 3.2.10 Environment and Identifier Functions

These functions provide information about the instance and the session:

- SYS_CONTEXT
- UID
- USER

### 3.3 ABS

`ABS` returns the absolute value of a numeric expression.

#### Return Value

    NUMBER

#### Syntax

    ABS(n)

#### Arguments

`n` is any numeric expression.

#### Example

`ABS(-15)` returns the value `15`.

### 3.4 ACOS

`ACOS` calculates the angle value in radians of a specified cosine.

#### Return Value

    NUMBER

#### Syntax

    ACOS(n)

#### Arguments

`n` is a numeric expression for the cosine in the range of -1 to 1.

#### Example

`ACOS(.3)` returns the value `1.26610367`.

### 3.5 ADD_MONTHS

`ADD_MONTHS` returns a date that is a specified number of months after a specified date.

When the starting date is the last day of the month or when the returned month has fewer days, then `ADD_MONTHS` returns the last day of the month. Otherwise, the returned day is the starting day.

#### Return Value

    DATE

#### Syntax

    ADD_MONTHS(date, integer)

#### Arguments

`date` is the starting date.

`integer` is the number of months to be added to the starting date.

#### Example

`ADD_MONTHS('17-JUN-06', 1)` returns the value `17-JUL-06`.

### 3.6 ASCII

`ASCII` returns the decimal representation of the first character of an expression.

#### Return Value

    NUMBER

#### Syntax

    ASCII(char)

#### Arguments

`char` can be any text expression.

#### Example

`ASCII('Boston')` returns the value `66`, which is the ASCII equivalent of the letter B.

### 3.7 ASCIISTR

`ASCIISTR` converts a string in any character set to ASCII in the database character set. Non-ASCII characters are represented as `\`xxxx, where xxxx is a UTF-16 code unit.

#### Return Value

    VARCHAR2

#### Syntax

    ASCIISTR(char)

#### Arguments

`char` can be any character string.

#### Example

`ASCIISTR('Skåne')` returns the value `Sk\00E5ne`.

### 3.8 ASIN

`ASIN` calculates the angle value in radians of a specified sine.

#### Return Value

    NUMBER

#### Syntax

    ASIN(n)

#### Arguments

`n` is a numeric expression in the range of -1 to 1 that contains the decimal value of a sine.

#### Example

`ASIN(.3)` returns the value `0.304692654`.

### 3.9 ATAN

`ATAN` calculates the angle value in radians of a specified tangent.

Use `ATAN2` to retrieve a full-range (0 - 2 pi) numeric value indicating the arc tangent of a given ratio.

#### Return Value

    NUMBER

#### Syntax

    ATAN(n)

#### Arguments

`n` is a numeric expression that contains the decimal value of a tangent.

#### Example

`ATAN(.3)` returns the value `0.291456794`.

### 3.10 ATAN2

`ATAN2` returns a full-range (0 - 2 pi) numeric value of the arc tangent of a given ratio. The function returns values in the range of -pi to pi, depending on the signs of the arguments.

Use `ATAN` to calculate the angle value (in radians) of a specified tangent that is not a ratio.

#### Return Value

    NUMBER

#### Syntax

    ATAN2(n1, n2)

#### Arguments

`n1` and `n2` are numeric expressions for the components of the ratio.

#### Example

`ATAN2(.3, .2)` returns the value `0.982793723`.

### 3.11 BIN_TO_NUM

`BIN_TO_NUM` converts a bit vector to its equivalent number.

#### Return Value

    NUMBER

#### Syntax

    BIN_TO_NUM(expr [, expr ]... )

#### Arguments

`expr` is a numeric expression with a value of 0 or 1 for the value of a bit in the bit vector.

#### Example

`BIN_TO_NUM(1,0,1,0)` returns the value `10`.

### 3.12 BITAND

`BITAND` computes an `AND` operation on the bits of two nonnegative integers, and returns an integer. This function is commonly used with the `DECODE` function.

An `AND` operation compares two bit values. If both values are 1, the operator returns 1. If one or both values are 0, the operator returns 0.

#### Return Value

    NUMBER

#### Syntax

    BITAND(expr1, expr2)

#### Arguments

`expr1` and `expr2` are numeric expressions for nonnegative integers.

#### Example

`BITAND(7, 29)` returns the value `5`.

The binary value of `7` is `111` and of `29` is `11101`. A bit-by-bit comparison generates the binary value `101`, which is decimal `5`.

### 3.13 CAST

`CAST` converts values from one data type to another.

#### Return Value

The data type specified by `type_name`.

#### Syntax

    CAST(expr AS type_name)

#### Arguments

`expr` can be an expression in one of the data types.

`type_name` is one of the data types listed in [Table 1-2](basic-elements.md).

Table 3-1 shows which data types can be cast into which other built-in data types. `NUMBER` includes `NUMBER`, `DECIMAL`, and `INTEGER`. `DATETIME` includes `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIMEZONE`, and `TIMESTAMP WITH LOCAL TIMEZONE`. `INTERVAL` includes `INTERVAL DAY TO SECOND` and `INTERVAL YEAR TO MONTH`.

Table 3-1 Compatible Data Types

| From                        | To BINARY_FLOAT, BINARY_DOUBLE | To CHAR, VARCHAR2 | To NUMBER | To DATETIME, INTERVAL | To NCHAR, NVARCHAR2 |
|:----------------------------|:-------------------------------|:------------------|:----------|:----------------------|:--------------------|
| BINARY_FLOAT, BINARY_DOUBLE | yes                            | yes               | yes       | no                    | yes                 |
| CHAR, VARCHAR2              | yes                            | yes               | yes       | yes                   | no                  |
| NUMBER                      | yes                            | yes               | yes       | no                    | yes                 |
| DATETIME, INTERVAL          | no                             | yes               | no        | yes                   | yes                 |
| NCHAR, NVARCHAR2            | yes                            | no                | yes       | no                    | yes                 |

#### Example

`CAST('123.4567' AS NUMBER(10,2))` returns the value `123.46`.

### 3.14 CEIL

`CEIL` returns the smallest whole number greater than or equal to a specified number.

#### Return Value

    NUMBER

#### Syntax

    CEIL(n)

#### Arguments

`n` is a numeric expression.

#### Examples

`CEIL(3.1415927)` returns the value `4`.

`CEIL(-3.4)` returns the value `-3.00`.

### 3.15 CHARTOROWID

`CHARTOROWID` converts a value from a text data type to a `ROWID` data type.

For more information about the `ROWID` pseudocolumn, refer to the Oracle Database SQL Language Reference.

#### Return Value

    ROWID

#### Syntax

    CHARTOROWID(char)

#### Arguments

`char` is a text expression that forms a valid rowid.

#### Example

`chartorowid('AAAN6EAALAAAAAMAAB')` returns the text string `AAAN6EAALAAAAAMAAB` as a rowid.

### 3.16 CHR

`CHR` converts an integer to the character with its binary equivalent in either the database character set or the national character set.

For single-byte character sets, if `n` \> 256, then `CHR` converts the binary equivalent of `mod(n, 256)`.

For the Unicode national character sets and all multibyte character sets, `n` must resolve to one entire code point. Code points are not validated, and the result of specifying invalid code points is indeterminate.

#### Return Value

    VARCHAR2 | NVARCHAR2

#### Syntax

    CHR(n [ USING NCHAR_CS ])

#### Arguments

`n` is a numeric expression.

`USING NCHAR_CS` returns a character in the national character set. Otherwise, the return value is in the database character set. The OLAP engine uses the UTF8 national character set, so the return value may be different from the SQL `CHR` function, which uses the database UTF16 national character set.

#### Example

`CHR(67)`, `CHR(67 USING NCHAR_CS)`, and `CHR(323)` all return the letter `C` on an ASCII-based system with the WE8DEC database character set and the UTF8 national character set. `CHR(323)` is evaluated as `CHR(MOD(323, 256))`.

### 3.17 COALESCE

`COALESCE` returns the first non-null expression in a list of expressions, or `NULL` when all of the expressions evaluate to null.

#### Return Value

Data type of the first argument

#### Syntax

    COALESCE(expr [, expr ]...)

#### Arguments

`expr` can be any expression.

#### Examples

`COALESCE(5, 8, 3)` returns the value `5`.

`COALESCE(NULL, 8, 3)` returns the value `8`.

### 3.18 CONCAT

`CONCAT` joins two expressions as a single character string. The data type of the return value is the same as the expressions, or if they are mixed, the one that results in a lossless conversion.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    CONCAT(char1, char2)

#### Arguments

`char1` and `char2` are text expressions.

#### Example

`CONCAT('The current date is ', 'October 13, 2006')` returns the string `The current date is October 13, 2006`.

### 3.19 COS

`COS` calculates the cosine of an angle.

#### Return Value

    NUMBER

#### Syntax

    COS(n)

#### Arguments

`n` is a numeric expression for an angle represented in radians.

#### Example

`COS(180 * 3.1415927/180)` returns the cosine of 180 degrees as the value `-1`. The expression converts degrees to radians.

### 3.20 COSH

`COSH` calculates the cosine of a hyperbolic angle.

#### Return Value

    NUMBER

#### Syntax

    COSH(n)

#### Arguments

`n` is a numeric expression for a hyperbolic angle.

#### Example

`COSH(0)` returns the value `1`.

### 3.21 CURRENT_DATE

`CURRENT_DATE` returns the current date in the session time zone.

#### Return Value

    DATE

#### Syntax

    CURRENT_DATE

#### Example

`CURRENT_DATE` returns a value such as `12-AUG-08`.

### 3.22 CURRENT_TIMESTAMP

`CURRENT_TIMESTAMP` returns the current date and time in the session time zone. The time zone offset identifies the current local time of the session.

#### Return Value

    TIMESTAMP WITH TIME ZONE

#### Syntax

    CURRENT_TIMESTAMP [ (precision) ]

#### Arguments

`precision` specifies the fractional second precision of the returned time value. The default value is 6.

#### Examples

`CURRENT_TIMESTAMP` returns a value such as `08-AUG-06 11.18.31.082257 AM -08:00`.

`CURRENT_TIMESTAMP(2)` returns a value such as `08-AUG-06 11.18.31.08 AM -08:00`.

### 3.23 DBTIMEZONE

`DBTIMEZONE` returns the value of the database time zone as either a time zone offset from Coordinated Universal Time (UTC) or a time zone region name.

To obtain other time zone offsets, use `TZ_OFFSET`.

#### Return Value

    VARCHAR2

#### Syntax

    DBTIMEZONE

#### Example

`DBTIMEZONE` returns the offset `-08:00` for Mountain Standard Time.

### 3.24 DECODE

`DECODE` compares an expression to one or more search strings one by one.

If `expr` is `search`, then `DECODE` returns the corresponding `result`. If there is no match, then `DECODE` returns `default`. If you omit `default`, then `DECODE` returns `NULL`.

#### Return Value

Data type of the first `result` argument

#### Syntax

    DECODE(expr, search, result
              [, search, result ]...
              [, default ]
          )

#### Arguments

`expr` is an expression that is compared to one or more search strings.

`search` is a string that is searched for a match to `expr`.

`result` is the return value when `expr` matches the corresponding search string.

`default` is the return value when `expr` does not match any of the search strings. If `default` is omitted, then `DECODE` returns `NULL`.

The arguments can be any numeric or character type. Two nulls are equivalent. If `expr` is null, then `DECODE` returns the `result` of the first `search` that is also null.

The maximum number of components, including `expr`, `searches`, `results`, and `default`, is 255.

#### Example

`DECODE(sysdate, '21-JUN-06', 'Summer Solstice', '21-DEC-06', 'Winter Solstice', 'Have a nice day!')`

returns these values:

`Summer Solstice` on June 21, 2006

`Winter Solstice` on December 21, 2006

`Have a nice day!` on all other days

### 3.25 EXP

`EXP` returns `e` raised to the `n`th power, where `e` = 2.71828183. The function returns a value of the same type as the argument.

#### Return Value

    NUMBER

#### Syntax

    EXP(n)

#### Arguments

`n` is a numeric expression for the exponent.

#### Example

`EXP(4)` returns the value `54.59815`.

### 3.26 EXTRACT (datetime)

`EXTRACT` returns the value of a specified field from a datetime or interval expression.

#### Return Value

    NUMBER

#### Syntax

    EXTRACT( { { YEAR
               | MONTH
               | DAY
               | HOUR
               | MINUTE
               | SECOND
               }
             | { TIMEZONE_HOUR
               | TIMEZONE_MINUTE
               }
             | { TIMEZONE_REGION
               | TIMEZONE_ABBR
               }
             }
        FROM   { datetime_value_expression
               | interval_value_expression
               }
           )

#### Arguments

`datetime_value_expression` is an expression with a datetime data type.

`interval_value_expression` is an expression with an interval data type.

#### Example

`EXTRACT(MONTH FROM CURRENT_TIMESTAMP)` returns the value `8` for August when the current timestamp is `08-AUG-06 01.10.55.330120 PM -07:00`.

`EXTRACT(TIMEZONE_HOUR FROM CURRENT_TIMESTAMP)` returns the value `-7` from the same example.

### 3.27 FLOOR

`FLOOR` returns the largest integer equal to or less than a specified number.

#### Return Value

    NUMBER

#### Syntax

    FLOOR(n)

#### Arguments

`n` can be any numeric expression.

#### Examples

`FLOOR(15.7)` returns the value `15`.

`FLOOR(-15.7)` returns the value `-16`.

### 3.28 FROM_TZ

`FROM_TZ` converts a timestamp value and a time zone to a `TIMESTAMP WITH TIME ZONE` data type.

#### Return Value

    TIMESTAMP WITH TIME ZONE

#### Syntax

    FROM_TZ (timestamp_value, time_zone_value)

#### Arguments

`timestamp_value` is an expression with a `TIMESTAMP` data type.

`time_zone_value` is a text expression that returns a string in the format `TZH:TZM` or in `TZR` with optional `TZD` format.

#### Example

`FROM_TZ(TIMESTAMP '2008-03-26 08:00:00', '3:00')` returns the value `26-MAR-08 08.00.00.000000 AM +03:00`.

### 3.29 GREATEST

`GREATEST` returns the largest expression in a list of expressions. All expressions after the first are implicitly converted to the data type of the first expression before the comparison. Text expressions are compared character by character.

To retrieve the smallest expression in a list of expressions, use `LEAST`.

#### Return Value

The data type of the first expression

#### Syntax

    GREATEST(expr [, expr ]...)

#### Arguments

`expr` can be any expression.

#### Examples

`GREATEST('Harry','Harriot','Harold')` returns the value `Harry`.

`GREATEST(7, 19, 3)` returns the value `19`.

### 3.30 HEXTORAW

`HEXTORAW` converts a hexadecimal value to a raw value.

#### Return Value

    RAW

#### Syntax

    HEXTORAW (char)

#### Arguments

`char` is a hexadecimal value in the `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2` data type.

#### Example

`HEXTORAW('7D')` returns the `RAW` value `7D`.

### 3.31 INITCAP

`INITCAP` returns a specified text expression, with the first letter of each word in uppercase and all other letters in lowercase. Words are delimited by white space or non-alphanumeric characters. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    INITCAP(char)

#### Arguments

`char` can be any text expression.

#### Example

`INITCAP('top ten tunes')` and `INITCAP('TOP TEN TUNES')` both return the string `Top Ten Tunes`.

### 3.32 INSTR

The `INSTR` functions search `string` for `substring`. The function returns an integer indicating the position of the character in `string`, or a zero (0) if does not find a match.

- `INSTR` calculates strings using characters as defined by the input character set.

- `INSTRB` uses bytes instead of characters.

- `INSTRC` uses Unicode complete characters.

`REGEXP_INSTR` provides additional options.

#### Return Value

    NUMBER

#### Syntax

    { INSTR | INSTRB | INSTRC }
    (string , substring [, position [, occurrence ] ])

#### Arguments

`string` is the text expression to search.

`substring` is the text string to search for.

`position` is a nonzero integer indicating the character in `string` where the function begins the search. When position is negative, then `INSTR` counts and searches backward from the end of string. The default value of position is 1, which means that the function begins searching at the first character of string.

`occurrence` is an integer indicating which occurrence of string the function should search for. The value of occurrence must be positive. The default values of occurrence is 1, meaning the function searches for the first occurrence of `substring`.

#### Example

`INSTR('CORPORATE FLOOR','OR', 3, 2)` searches the string CORPORATE FLOOR beginning with the third character (R) for the second instance of the substring OR. It returns the value `14`, which is the position of the second O in FLOOR.

### 3.33 LAST_DAY

`LAST_DAY` returns the last day of the month in which a particular date falls.

#### Return Value

    DATE

#### Syntax

    LAST_DAY(date)

#### Arguments

`date` can be any datetime expression.

#### Example

`LAST_DAY('26-MAR-06')` returns the value `31-MAR-06`.

### 3.34 LEAST

`LEAST` returns the smallest expression in a list of expressions. All expressions after the first are implicitly converted to the data type of the first expression before the comparison. Text expressions are compared character by character.

To retrieve the largest expression in a list of expressions, use `GREATEST`.

#### Return Value

The data type of the first expression

#### Syntax

    LEAST(expr [, expr ]...)

#### Arguments

`expr` can be any expression.

#### Examples

`LEAST('Harry','Harriot','Harold')` returns the value `Harold`.

`LEAST(19, 3, 7)` returns the value `3`.

### 3.35 LENGTH

The `LENGTH` functions return the length of a text expression.

- `LENGTH` counts the number of characters.

- `LENGTHB` uses bytes instead of characters.

- `LENGTHC` uses Unicode complete characters.

#### Return Value

    NUMBER

#### Syntax

    { LENGTH | LENGTHB | LENGTHC }(char)

#### Arguments

`char` is any text expression.

#### Example

`LENGTH('CANDIDE')` returns the value `7`.

### 3.36 LN

`LN` returns the natural logarithm of a number greater than 0.

#### Return Value

    NUMBER

#### Syntax

    LN(n)

#### Arguments

`n` can be any numeric expression with a value greater than 0.

#### Example

`LN(95)` returns the value `4.55387689`.

### 3.37 LNNVL

`LNNVL` evaluates a condition when one or both operands of the condition may be null. `LNNVL` can be used anywhere a scalar expression can appear, even in contexts where the `IS [NOT] NULL`, `AND`, or `OR` conditions are not valid but would otherwise be required to account for potential nulls.

NOTE: This function returns `1` (true) if the condition is false or unknown, and `0` (false) if the condition is true.

#### Return Value

    NUMBER

#### Syntax

    LNNVL(condition)

#### Arguments

`condition` can be any expression containing scalar values.

#### Examples

`LNNVL(1 > 4)` returns `1` (true).

### 3.38 LOCALTIMESTAMP

`LOCALTIMESTAMP` returns the current date and time in the session time zone.

#### Return Value

    TIMESTAMP

#### Syntax

    LOCALTIMESTAMP [ (timestamp_precision) ]

#### Arguments

`timestamp_precision` specifies the fractional second precision of the time value returned.

#### Examples

`LOCALTIMESTAMP` returns a value such as `09-AUG-06 08.11.37.045186 AM`.

`LOCALTIMESTAMP(2)` returns a value such as `09-AUG-06 08.11.37.040000 AM`.

### 3.39 LOG

`LOG` computes the logarithm of an expression.

#### Return Value

    NUMBER

#### Syntax

    LOG(n2, n1)

#### Arguments

`n2` is the base by which to compute the logarithm.

`n1` is the value whose logarithm is calculated. It can be any numeric expression that is greater than zero. When the value is equal to or less than zero, `LOG` returns a null value.

#### Example

`LOG(10,100)` returns the value `2`.

### 3.40 LOWER

`LOWER` converts all alphabetic characters in a text expression to lowercase. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    LOWER(char)

#### Arguments

`char` can be any text expression.

#### Example

`LOWER('STOP SHOUTING')` returns the string `stop shouting`.

### 3.41 LPAD

`LPAD` adds characters to the left of an expression to a specified length. The data type of the return value is the same as the original text.

Use `RPAD` to add characters to the right.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    LPAD(expr1, n [, expr2 ])

#### Arguments

`expr1` is a text expression for the base string.

`n` is the total length of the returned expression. If `expr1` is longer than `n`, then this function truncates `expr1` to `n` characters.

`expr2` is a text expression for the padding characters. By default, it is a space.

#### Example

`LPAD('Page 1',15,'*.')` returns the value `*.*.*.*.*Page 1`.

`LPAD('Stay tuned', 4)` returns the value `Stay`.

### 3.42 LTRIM

`LTRIM` scans a text expression from left to right and removes all the characters that match the characters in the trim expression, until it finds an unmatched character. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    LTRIM(char [, set ])

#### Arguments

`char` is the text expression to be trimmed.

`set` is a text expression with the characters to remove. The default value of `set` is a single blank.

#### Examples

`LTRIM(' . . . .Last Word', ' .')` returns the value `Last Word`.

### 3.43 MOD

`MOD` returns the remainder after a number is divided by another, or the number if the divisor is 0 (zero).

#### Return Value

    NUMBER

#### Syntax

    MOD(n2, n1)

#### Arguments

`n2` is a numeric expression for the number to be divided.

`n1` is a numeric expression for the divisor.

#### Example

`MOD(13,7)` returns the value `6`.

### 3.44 MONTHS_BETWEEN

`MONTHS_BETWEEN` calculates the number of months between two dates. When the two dates have the same day component or are both the last day of the month, then the return value is a whole number. Otherwise, the return value includes a fraction that considers the difference in the days based on a 31-day month.

#### Return Value

    NUMBER

#### Syntax

    MONTHS_BETWEEN(date1, date2)

#### Arguments

`date1` and `date2` are datetime expressions. If `date1` is later than `date2`, then the result is positive. If `date1` is earlier than `date2`, then the result is negative.

#### Example

`MONTHS_BETWEEN('15-APR-06', '01-JAN-06')` returns the value `3.4516129`.

### 3.45 NANVL

`NANVL` checks if a value is a number. If it is, then `NANVL` returns that value. If not, it returns an alternate value. This function is typically used to convert a binary double or binary float NaN (Not a Number) value to zero or null.

#### Return Value

    datatype

#### Syntax

    NANVL (expression, alternate)

#### Arguments

`expression` can be any value.

`alternate` is the numeric value returned if `expression` is not a number.

### 3.46 NEW_TIME

`NEW_TIME` converts the date and time from one time zone to another. Before using this function, set the `NLS_DATE_FORMAT` parameter to display 24-hour time.

#### Return Value

    DATE

#### Syntax

    NEW_TIME(date, timezone1, timezone2)

#### Arguments

`date` is a datetime expression to be converted to a new time zone.

`timezone1` is the time zone of `date`.

`timezone2` is the new time zone.

The time zone arguments are limited to the values in Table 3-2. For other time zones, use `FROM_TZ`.

Table 3-2 Time Zones

| Time Zone                   | Abbreviation |
|:----------------------------|:-------------|
| Alaska-Hawaii Daylight Time | HDT          |
| Alaska-Hawaii Standard Time | HST          |
| Atlantic Daylight Time      | ADT          |
| Atlantic Standard Time      | AST          |
| Bering Daylight Time        | BDT          |
| Bering Standard Time        | BST          |
| Central Daylight Time       | CDT          |
| Central Standard Time       | CST          |
| Eastern Daylight Time       | EDT          |
| Eastern Standard Time       | EST          |
| Greenwich Mean Time         | GMT          |
| Mountain Daylight Time      | MDT          |
| Mountain Standard Time      | MST          |
| Newfoundland Standard Time  | NST          |
| Pacific Daylight Time       | PDT          |
| Pacific Standard Time       | PST          |
| Yukon Daylight Time         | YDT          |
| Yukon Standard Time         | YST          |

#### Example

`NEW_TIME(SYSDATE, 'PST', 'EST')` returns a value such as `18-JAN-07 04:38:07` in Eastern Standard Time when `SYSDATE` is `18-JAN-07 01:38:07` in Pacific Standard Time. For this example, `NLS_DATE_FORMAT` is set to `DD-MON-RR HH:MI:SS`.

### 3.47 NEXT_DAY

`NEXT_DAY` returns the date of the first instance of a particular day of the week that follows the specified date.

#### Return Value

    DATE

#### Syntax

    NEXT_DAY(date, char)

#### Arguments

`date` is a datetime expression.

`char` is a text expression that identifies a day of the week (for example, Monday) in the language of your session.

#### Example

`NEXT_DAY('11-SEP-01', 'Monday')` returns the value `17-SEP-01`.

### 3.48 NLS_CHARSET_ID

`NLS_CHARSET_ID` returns the identification number corresponding to a specified character set name.

#### Return Value

    NUMBER

#### Syntax

    NLS_CHARSET_ID  ( charset_name )

#### Arguments

`charset_name` is a VARCHAR2 expression that is a valid character set name.

#### Example

`NLS_CHARSET_ID('AL32UTF8')` returns the value `873`.

### 3.49 NLS_CHARSET_NAME

`NLS_CHARSET_NAME` returns the name corresponding to a specified character set number.

#### Return Value

    VARCHAR2

#### Syntax

    NLS_CHARSET_NAME (charset_id)

#### Arguments

`charset_id` is a valid character set number or one of these keywords:

- `CHAR_CS` represents the database character set.

- `NCHAR_CS` represents the national character set. The national character set for the database can be either UTF-8 or AL16UTF16 (default). However, the national character set for analytic workspaces is always UTF-8.

If the number does not correspond to a character set, then the function returns `NULL`.

#### Example

`NLS_CHARSET_NAME(2000)` returns the value `AL16UTF16`.

### 3.50 NLS_INITCAP

`NLS_INITCAP` returns a string in which each word begins with a capital followed by lower-case letters. White space and nonalphanumeric characters delimit the words.

#### Return Value

    VARCHAR2

#### Syntax

    NLS_INITCAP (char [, 'nlsparam' ])

#### Arguments

`char` can be any text string.

`nlsparam` can have the form `'NLS_SORT =``sort``'` where `sort` is either a linguistic sort sequence or `BINARY`. The linguistic sort sequence handles special linguistic requirements for case conversions. These requirements can result in a return value of a different length than `char`. If you omit `nlsparam`, then this function uses the default sort sequence for your session.

#### Example

`NLS_INITCAP('WALKING&THROUGH*A*winter wonderland')` returns the value `Walking#Through*A*Winter Wonderland`.

`NLS_INITCAP('ijsland')` returns the value `Ijsland`, but `NLS_INITCAP(NLS_INITCAP('ijsland', 'NLS_SORT = XDutch')` returns `IJsland`.

### 3.51 NLS_LOWER

`NLS_LOWER` converts all alphabetic characters in a text expression to lowercase. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    NLS_LOWER (char [, 'nlsparam' ])

#### Arguments

`char` can be any text expression.

`nlsparam` is a linguistic sort sequence in the form `NLS_SORT =``sort``[_ai |_ci]`, where `sort` is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort.

#### Example

`NLS_LOWER('STOP SHOUTING')` returns the string `stop shouting`.

### 3.52 NLS_UPPER

`NLS_UPPER` converts all alphabetic characters in a text expression to uppercase. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    NLS_UPPER (char [, 'nlsparam' ])

#### Arguments

`char` can be any text expression.

`nlsparam` is a linguistic sort sequence in the form `NLS_SORT =``sort``[_ai |_ci]`, where `sort` is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort.

#### Example

`NLS_UPPER('This is an emergency')` returns the string `THIS IS AN EMERGENCY`.

### 3.53 NLSSORT

`NLSSORT` returns the string of bytes used to sort a text string. You can use this function to specify sorting and comparison operations based on a linguistic sort sequence rather than on the binary value of a string.

Note: `NLSSORT` returns a `RAW` value, which you may pass to another function. To create a measure or a calculated measure for the values returned by `NLSSORT`, use the `RAWTOHEX` function.

For more information about linguistic sorting, refer to the Oracle Database Globalization Support Guide.

#### Return Value

    RAW

#### Syntax

    NLSSORT(char [, 'nlsparam' ])

#### Arguments

`char` is a text expression.

`nlsparam` is a linguistic sort sequence in the form `NLS_SORT =``sort``[_ai |_ci]`, where `sort` is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort.

#### Example

`NLSSORT('Rumpelstiltskin')` returns the value `52756D70656C7374696C74736B696E00` for a default linguistic sort, which in this case is American.

### 3.54 NULLIF

`NULLIF` compares one expression with another. It returns `NULL` when the expressions are equal, or the first expression when they are not.

#### Return Value

Data type of the first argument

#### Syntax

    NULLIF(expr1, expr2)

#### Arguments

`expr1` is the base expression. It cannot be a literal null.

`expr2` is the expression to compare with the base expression.

#### Example

`NULLIF('red', 'Red')` returns the value `red`.

### 3.55 NUMTODSINTERVAL

`NUMTODSINTERVAL` converts a number to an `INTERVAL DAY TO SECOND` data type.

#### Return Value

    INTERVAL DAY TO SECOND

#### Syntax

    NUMTODSINTERVAL(n, 'interval_unit')

#### Arguments

`n` can be any numeric expression.

`interval_unit` is a text expression that specifies the units. It must resolve to one of the following values:

- `DAY`

- `HOUR`

- `MINUTE`

- `SECOND`

These values are case insensitive.

#### Example

`NUMTODSINTERVAL(100, 'MINUTE')` returns the value +00 01:40:00.000000.

### 3.56 NUMTOYMINTERVAL

`NUMTOYMINTERVAL` converts a number to an `INTERVAL YEAR TO MONTH` data type.

#### Return Value

    INTERVAL YEAR TO MONTH

#### Syntax

    NUMTOYMINTERVAL(n, 'interval_unit')

#### Arguments

`n` can be any numeric expression.

`interval_unit` is a text expression that specifies the units. It must resolve to one of the following values:

- `YEAR`

- `MONTH`

These values are case insensitive.

#### Example

`NUMTOYMINTERVAL(18, 'MONTH')` returns the value `+01-06`.

### 3.57 NVL

`NVL` replaces a null with a string. `NVL` returns the replacement string when the base expression is null, and the value of the base expression when it is not null.

To replace an expression with one value if it is null and a different value if it is not, use `NVL2`.

#### Return Value

Data type of the first argument

#### Syntax

    NVL(expr1, expr2)

#### Arguments

`expr1` is the base expression that is evaluated.

`expr2` is the replacement string that is returned when `expr1` is null.

#### Examples

`NVL('First String', 'Second String')` returns the value `First String`.

`NVL(null, 'Second String')` returns the value `Second String`.

### 3.58 NVL2

`NVL2` returns one value when the value of a specified expression is not null, or another value when the value of the specified expression is null.

To replace a null value with a string, use `NVL`.

#### Return Value

Data type of the first argument

#### Syntax

    NVL2(expr1, expr2, expr3)

#### Arguments

`expr1` is the base expression whose value this function evaluates.

`expr2` is an expression whose value is returned when `expr1` is not null.

`expr3` is an expression whose value is returned when `expr1` is null.

#### Example

`NVL2('Which string?', 'First String', 'Second String')` returns the value `First String`.

### 3.59 ORA_HASH

`ORA_HASH` generates hash values for an expression. You can use it to randomly assign a set of values into several buckets for analysis, or to generate a set of random numbers.

#### Return Value

    NUMBER

#### Syntax

    ORA_HASH  (expr [, max_bucket [, seed_value ] ])

#### Arguments

`expr` can be any expression that provides the data for generating the hash values.

`max_bucket` is the maximum bucket number. For example, when `max_bucket` is set to 5, `ORA_HASH` returns values of 0 to 5, creating six buckets. Set this value from 0 to 4294967295 or 2^32-1 (default).

`seed_value` is a value used by `ORA_HASH` to generate the hash values. Enter a different `seed_value` for different results. Set this value from 0 (default) to 4294967295 or 2^32-1.

#### Example

`ORA_HASH(PRODUCT_CUBE.PRICES, 5)` returns a value in the range of 0 to 5 for each value of the Prices measure, as shown in the Hash 5 column. The rows are also sorted on the Hash 5 column.

`ORA_HASH(PRODUCT_CUBE.PRICES, 5, 13)` also returns values in the range of 0 to 5, but uses a different seed.

| Product      | Prices    | Hash 5 | Seed 13 |
|:-------------|:----------|:-------|:--------|
| ENVY STD     | 200539.83 | 0      | 4       |
| ENVY EXE     | 255029.31 | 0      | 5       |
| 1GB USB DRV  | 44645.65  | 1      | 2       |
| DLX MOUSE    | 1379.49   | 2      | 2       |
| 144MB DISK   | 3011.43   | 2      | 5       |
| 512 USB DRV  | 22139.99  | 2      | 2       |
| 19 SVGA      | 34837.16  | 3      | 0       |
| 56KPS MODEM  | 12478     | 3      | 2       |
| ENVY EXT KBD | 4312.22   | 3      | 5       |
| 17 SVGA      | 22605.55  | 4      | 1       |
| EXT CD ROM   | 17990.14  | 4      | 0       |
| ENVY ABM     | 205462.25 | 5      | 1       |

### 3.60 POWER

`POWER` raises a number to a power.

#### Return Value

    NUMBER

#### Syntax

    POWER(n2, n1)

#### Arguments

`n2` is any numeric expression that is raised to a power.

`n1` is the exponent.

#### Example

`POWER(3,2)` returns the value `9`.

### 3.61 RAWTOHEX

`RAWTOHEX` converts raw data to a character value containing its hexadecimal representation.

#### Return Value

    VARCHAR2

#### Syntax

    RAWTOHEX(raw)

#### Arguments

`raw` can be any scalar data type other than `LONG`, `LONG RAW`, `CLOB`, `BLOB`, or `BFILE`.

#### Example

`RAWTOHEX(NLSSORT('Rumpelstiltskin'))` converts the raw value returned by `NLSSORT` to the hexadecimal value `52756D70656C7374696C74736B696E00`.

### 3.62 REGEXP_COUNT

`REGEXP_COUNT` searches a string for a regular pattern and returns the number of times the pattern occurs. If no match is found, the function returns 0.

The function evaluates strings using characters as defined by the input character set.

#### Return Value

    NUMBER

#### Syntax

    REGEXP_COUNT (source_char, pattern
                  [, position
                     [, match_parameter ]
                  ]
                 )

#### Arguments

`source_char` is the text expression to search.

`pattern` is the string to search for. A period matches any character. For a list of operators, refer to the Oracle Database SQL Language Reference, Appendix D, "Oracle Regular Expression Support."

`position` is a nonzero integer indicating the character of `source_char` where the function begins the search. When `position` is negative, then the function counts and searches backward from the end of string. The default value of `position` is 1, which means that the function begins searching at the first character of `source_char`.

`match_parameter` is a text literal that lets you change the default matching behavior of the function. You can specify one or more of the following values:

- `c`: Case-sensitive matching.

- `i`: Case-insensitive matching.

- `m`: Treat the source string as multiple lines. The function interprets ` ^` and `$` as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line.

- `n`: New-line character is among the characters matched by a period (the wildcard character). By default, it is not.

- `x`: Ignore whitespace characters.

#### Example

`REGEXP_COUNT('Mississippi', 'i', 1)` searches the string `Mississippi` for the letter `i`, beginning the search at the first letter. It returns the value `4`.

### 3.63 REGEXP_REPLACE

`REGEXP_REPLACE` searches a string for a regular pattern and replaces it with another string. By default, the function returns `source_char` with every occurrence of the regular expression pattern replaced with `replace_string`.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    REGEXP_REPLACE(source_char, pattern
                   [, replace_string
                      [, position
                         [, occurrence
                            [, match_parameter ]
                         ]
                      ]
                   ]
                  )

#### Arguments

`source_char` is the text expression that is searched.

`pattern` is the text expression to search for. It is usually a text literal and can contain up to 512 bytes. For a list of operators, refer to the Oracle Database SQL Language Reference, Appendix D, "Oracle Regular Expression Support."

`replace_string` is the text that replaces `pattern` in `source_char`.

`position` is a nonzero integer indicating the character of `source_char` where the function begins the search. When `position` is negative, then the function counts and searches backward from the end of string. The default value of `position` is 1, which means that the function begins searching at the first character of `source_char`.

`occurrence` is an integer indicating which occurrence of `pattern` the function should search for. The value of `occurrence` must be positive. The default values of `occurrence` is 1, meaning the function searches for the first occurrence of `pattern`.

`match_parameter` is a text literal that lets you change the default matching behavior of the function. You can specify one or more of the following values:

- `c`: Case-sensitive matching.

- `i`: Case-insensitive matching.

- `m`: Treat the source string as multiple lines. The function interprets ` ^` and `$` as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line.

- `n`: New-line character is among the characters matched by a period (the wildcard character). By default, it is not.

- `x`: Ignore whitespace characters.

#### Example

`REGEXP_REPLACE('500 Oracle Parkway, Redwood Shores, CA', '( ){2,}', ' ')`

eliminates extra spaces and returns the string

`500 Oracle Parkway, Redwood Shores, CA`

### 3.64 REGEXP_INSTR

`REGEXP_INSTR` searches a string for a regular pattern. It can return an integer indicating either the beginning or the ending position of the matched substring. If no match is found, then the function returns 0.

The function evaluates strings using characters as defined by the input character set.

#### Return Value

    NUMBER

#### Syntax

    REGEXP_INSTR (source_char, pattern
                  [, position
                     [, occurrence
                        [, return_option
                           [, match_parameter ]
                        ]
                     ]
                  ]
                 )

#### Arguments

`source_char` is the text expression to search.

`pattern` is the string to search for. A period matches any character. For a list of operators, refer to the Oracle Database SQL Language Reference, Appendix D, Oracle Regular Expression Support.

`position` is a nonzero integer indicating the character of `source_char` where the function begins the search. When `position` is negative, then the function counts and searches backward from the end of string. The default value of `position` is 1, which means that the function begins searching at the first character of `source_char`.

`occurrence` is an integer indicating which occurrence of `pattern` the function should search for. The value of `occurrence` must be positive. The default values of `occurrence` is 1, meaning the function searches for the first occurrence of `pattern`.

`return_option` is either 0 to return the position of the match (default), or 1 to return the position of the character following the match.

`match_parameter` is a text literal that lets you change the default matching behavior of the function. You can specify one or more of the following values:

- `c`: Case-sensitive matching.

- `i`: Case-insensitive matching.

- `m`: Treat the source string as multiple lines. The function interprets ` ^` and `$` as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line.

- `n`: New-line character is among the characters matched by a period (the wildcard character). By default, it is not.

- `x`: Ignore whitespace characters.

#### Example

`REGEXP_INSTR('Mississippi', 'i', 1, 3)` searches the string `Mississippi` for the third instance of the letter `i`, beginning the search at the first letter. It returns the value `8`.

### 3.65 REGEXP_SUBSTR

`REGEXP_SUBSTR` searches a string for a pattern and returns the matching string.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR

#### Syntax

    REGEXP_SUBSTR(source_char, pattern
                  [, position
                     [, occurrence
                        [, match_parameter ]
                     ]
                  ]
                 )

#### Arguments

`source_char` is the text expression that is searched.

`pattern` is the text expression to search for. It is usually a text literal and can contain up to 512 bytes. For a list of operators, refer to the Oracle Database SQL Language Reference, Appendix D, "Oracle Regular Expression Support."

`position` is a nonzero integer indicating the character of `source_char` where the function begins the search. When `position` is negative, then the function counts and searches backward from the end of string. The default value of `position` is 1, which means that the function begins searching at the first character of `source_char`.

`occurrence` is an integer indicating which occurrence of `pattern` the function should search for. The value of `occurrence` must be positive. The default values of `occurrence` is 1, meaning the function searches for the first occurrence of `pattern`.

`match_parameter` is a text expression that lets you change the default matching behavior of the function. You can specify one or more of the following values:

- `c`: Case-sensitive matching.

- `i`: Case-insensitive matching.

- `m`: Treat the source string as multiple lines. The function interprets ` ^` and `$` as the start and end, respectively, of any line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the function treats the source string as a single line.

- `n`: New-line character is among the characters matched by a period (the wildcard character). By default, it is not.

- `x`: Ignore whitespace characters.

#### Examples

`REGEXP_SUBSTR('7 W 96th St, New York, NEW YORK', 'new york', 10, 2, 'i')` starts searching at the tenth character and matches `NEW YORK` in a case-insensitive match.

`REGEXP_SUBSTR('parsley, sage, rosemary, thyme', 's[^,]+e', 1, 2)` starts searching at the first character and matches the second substring consisting of the letter `s`, any number of characters that are not commas, and the letter `e`. In this example, the function returns the value `sage`.

### 3.66 REMAINDER

`REMAINDER` returns a rounded remainder when one number is divided by another using this equation:

`n2 - (n1 * N)`

where `N` is the integer nearest `n2/n1`.

#### Return Value

    NUMBER

#### Syntax

    REMAINDER(n2, n1)

#### Arguments

`n1` is a numeric expression for the divisor.

`n2` is a numeric expression for the dividend.

#### Example

`REMAINDER(18,7)` returns the value `-3`.

### 3.67 REPLACE

`REPLACE` searches a string for a regular pattern, replaces it with another string, and returns the modified string.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    REPLACE(char, search_string [, replacement_string ])

#### Arguments

`char` is the text expression that is searched.

`search_string` is the text expression to search for.

`replacement_string` is the text expression that replaces `search_string` in `char`.

#### Example

`REPLACE('Nick Nack', 'N', 'Cl')` returns the string `Click Clack`.

### 3.68 ROUND (date)

`ROUND` returns a date rounded to the unit specified by the date format.

#### Return Value

    DATE

#### Syntax

    ROUND(date [, fmt ])

#### Arguments

`date` is an expression that identifies a date and time.

`fmt` is a text literal with a date format, as described in the Oracle Database SQL Language Reference.

#### Examples

`ROUND(SYSDATE, 'YEAR')` returns the value `01-JAN-07` for any day in the last half of 2006.

`ROUND(TO_DATE('13-OCT-06'), 'MONTH')` returns the value `01-OCT-06`.

### 3.69 ROUND (number)

`ROUND` returns a number rounded to a specified number of places.

#### Return Value

    NUMBER

#### Syntax

    ROUND(n [, integer ])

#### Arguments

`n` is the number to round.

`integer` is the number of decimal places of the rounded number. A negative value rounds to the left of the decimal point. The default value is 0.

#### Examples

`ROUND(15.193)` returns the value `15`.

`ROUND(15.193,1)` returns the value `15.2`.

`ROUND(15.193,-1)` returns the value `20`.

### 3.70 ROWIDTOCHAR

`ROWIDTOCHAR` converts a row address from a `ROWID` data type to text.The return value is always 18 characters long in the database character set.

#### Return Value

    VARCHAR2

#### Syntax

    ROWIDTOCHAR(rowid)

#### Arguments

`rowid` is a row address to convert.

### 3.71 ROWIDTONCHAR

`ROWIDTONCHAR` converts a row address from the `ROWID` data type to text. The return value is always 18 characters in the national character set.

#### Return Value

    NVARCHAR2

#### Syntax

    ROWIDTONCHAR(rowid)

#### Arguments

`rowid` is a row address to convert.

### 3.72 RPAD

`RPAD` adds characters to the right of an expression to a specified length. The data type of the return value is the same as the original text.

Use `LPAD` to add characters to the left.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    RPAD(expr1 , n [, expr2 ])

#### Arguments

`expr1` is a text expression for the base string.

`n` is the total length of the returned expression. If `expr1` is longer than `n`, then this function truncates `expr1` to `n` characters.

`expr2` is a text expression for the padding characters. By default, it is a space.

#### Example

`RPAD('Stay tuned', 15, '. ')` returns the value `Stay tuned. . .`

`RPAD('Stay tuned', 4)` returns the value `Stay`.

### 3.73 RTRIM

`RTRIM` scans a text expression from right to left and removes all the characters that match the characters in the trim expression, until it finds an unmatched character. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    RTRIM(char [, set ])

#### Arguments

`char` is the text expression to be trimmed.

`set` is a text expression with the characters to remove. The default value of `set` is a single blank.

#### Examples

`RTRIM('You did that!?!?!?!', '?!')` returns the value `You did that`.

`RTRIM('3.14848', '84')` returns the text value `3.1`.

### 3.74 SESSIONTIMEZONE

`SESSIONTIMEZONE` returns the time zone of the current session. The return type is a time zone offset from Coordinated Universal Time (UTC) or a time zone region name.

#### Return Value

    VARCHAR2

#### Syntax

    SESSIONTIMEZONE

#### Example

`SESSIONTIMEZONE` returns the value `-05:00` for Eastern Standard Time.

### 3.75 SIGN

`SIGN` returns a value that indicates whether a specified number is less than, equal to, or greater than 0 (zero):

- `-1` if `n < 0`

- `0` if `n = 0`

- `1` if `n > 0`

#### Return Value

    NUMBER

#### Syntax

    SIGN(n)

#### Arguments

`n` is a numeric expression.

#### Example

`SIGN(-15)` returns the value `-1`.

### 3.76 SIN

`SIN` returns the sine of an angle.

#### Return Value

    NUMBER

#### Syntax

    SIN(n)

#### Arguments

`n` is a numeric expression for an angle in radians.

#### Example

`SIN(30 * 3.1415927/180)` calculates the sine of a 30 degrees angle as the value `0.500000007`. The numeric expression converts degrees to radians.

### 3.77 SINH

`SINH` returns the sine of a hyperbolic angle.

#### Return Value

    NUMBER

#### Syntax

    SINH(n)

#### Arguments

`n` is a numeric expression for a hyperbolic angle.

#### Example

`SINH(1)` returns the value `1.17520119`.

### 3.78 SOUNDEX

`SOUNDEX` returns a character string containing the phonetic representation of a text expression. This function lets you compare words that are spelled differently but sound alike.

The function is based on the algorithm described in Donald Knuth's The Art of Computer Programming. This algorithm was designed specifically for English. Its results for other languages other than English are unpredictable and typically unsatisfactory.

#### Return Value

    VARCHAR2

#### Syntax

    SOUNDEX (char)

#### Arguments

`char` can be any text expression.

#### Example

All of these examples return the value `D500`:

    soundex('Donna')

    soundex('Diane')

    soundex('Dana')

### 3.79 SQRT

`SQRT` returns the square root of a number.

#### Return Value

    NUMBER

#### Syntax

    SQRT(n)

#### Arguments

`n` is a numeric expression for a positive number.

#### Example

`SQRT(13)` returns the value `3.60555128`.

### 3.80 SUBSTR

`SUBSTR` returns a portion of string, beginning at a specified character position and extending a specified number of characters.

- `SUBSTR` calculates lengths using characters as defined by the input character set.

- `SUBSTRB` uses bytes instead of characters.

- `SUBSTRC` uses Unicode complete characters.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    { SUBSTR | SUBSTRB | SUBSTRC }(char, position [, substring_length ])

#### Arguments

`char` is a text expression that provides the base string from which the substring is derived.

`position` identifies the first character of the substring:

- When `position` is positive, then the function counts from the beginning of `char` to find the first character.

- When `position` is negative, then the function counts backward from the end of `char`.

- When `position` is 0 (zero), then the first character is the beginning of the substring.

`substring_length` is the number of characters in the returned string. By default, the function returns all characters to the end of the base string. If you specify a value less than 1, then the function returns a null.

#### Examples

`SUBSTR('firefly', 1, 4)` returns the substring `fire`.

`SUBSTR('firefly', -3, 3)` returns the substring `fly`.

### 3.81 SYS_CONTEXT

`SYS_CONTEXT` returns the value of an attribute of a named context. The context, attribute, and value must already be defined in the database. If the context is not defined, `SYS_CONTEXT` returns `NULL`.

#### Return Value

    VARCHAR2

#### Syntax

    SYS_CONTEXT ('namespace', 'parameter')

#### Arguments

`namespace` can be any named context in the database. `USERENV` is a built-in context that describes the current session.

`parameter` is a defined attribute of `namespace`. Table 3-3 describes the predefined attributes of `USERENV` that are most likely to have values. For a complete list, refer to the `SYS_CONTEXT` entry in the Oracle Database SQL Language Reference.

Table 3-3 USERENV Attributes

| USERENV Attribute        | Description                                                                                                                           |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `AUTHENTICATED_IDENTITY` | The identity used for authentication, such as database user name, schema name, or operating system login name.                        |
| `AUTHENTICATION_METHOD`  | The method of authentication, such as `PASSWORD`, `OS`, or `SSL`.                                                                     |
| `CURRENT_EDITION_ID`     | The session edition identifier, such as `100`.                                                                                        |
| `CURRENT_EDITION_NAME`   | The session edition name, such as `ORA$BASE`.                                                                                         |
| `CURRENT_SCHEMA`         | The name of the currently active default schema, such as `SH`.                                                                        |
| `CURRENT_SCHEMA_ID`      | The numeric identifier of the currently active default schema, such as `80`.                                                          |
| `CURRENT_USER`           | The name of the database user whose privileges are currently active, such as `SH`.                                                    |
| `CURRENT_USERID`         | The numeric identifier of the database user whose privileges are currently active, such as `80`.                                      |
| `DATABASE_ROLE`          | Data Guard role of the database: `PRIMARY`, `PHYSICAL STANDBY`, `LOGICAL STANDBY`, or `SNAPSHOT STANDBY`.                             |
| `DB_DOMAIN`              | The network domain of the database as specified by the `DB_DOMAIN` initialization parameter, such as `us.example.com`.                |
| `DB_NAME`                | The name of the database as specified by the `DB_NAME` initialization parameter.                                                      |
| `DB_UNIQUE_NAME`         | The unique name of the database within the domain as specified by the `DB_UNIQUE_NAME` initialization parameter.                      |
| `ENTERPRISE_IDENTITY`    | The enterprise-wide identity of the user, or `NULL` for local users, SYSDBA, and SYSOPER.                                             |
| `FG_JOB_ID`              | Job identifier of the current session if a client foreground process opened it; otherwise, `NULL`.                                    |
| `GLOBAL_CONTEXT_MEMORY`  | The number used in the System Global Area by the globally accessed context.                                                           |
| `GLOBAL_UID`             | The global user identification from Oracle Internet Directory for Enterprise User Security logins; otherwise, `NULL`.                 |
| `HOST`                   | The name of the client host computer.                                                                                                 |
| `IDENTIFICATION_TYPE`    | The way the user schema was created in the database: `LOCAL`, `EXTERNAL`, `GLOBAL SHARED`, or `GLOBAL PRIVATE`.                       |
| `INSTANCE`               | The identification number of the current instance, such as `1`.                                                                       |
| `INSTANCE_NAME`          | The name of the database instance.                                                                                                    |
| `IP_ADDRESS`             | The IP address of the client, such as `10.255.255.255`.                                                                               |
| `ISDBA`                  | `TRUE` if the user was authenticated with DBA privileges; otherwise, `FALSE`.                                                         |
| `LANG`                   | A short name for the session language, such as `US` for `AMERICAN`.                                                                   |
| `LANGUAGE`               | The language, territory, and database character set in the form `language_territory.characterset`, such as `AMERICA_AMERICAN.WE8DEC`. |
| `MODULE`                 | The application name set through the `DBMS_APPLICATION_INFO` package or OCI, such as `JDBC Thin Client` or `SQL Developer`.           |
| `NETWORK_PROTOCOL`       | The network protocol being used for communication, such as `TCP`.                                                                     |
| `NLS_CALENDAR`           | The session calendar, such as `GREGORIAN`.                                                                                            |
| `NLS_CURRENCY`           | The session currency mark, such as `$`.                                                                                               |
| `NLS_DATE_FORMAT`        | The session date format, such as `DD-MON-RR`.                                                                                         |
| `NLS_DATE_LANGUAGE`      | The session date language, such as `AMERICAN`.                                                                                        |
| `NLS_SORT`               | `BINARY` or a linguistic sort basis, such as `XSPANISH`.                                                                              |
| `NLS_TERRITORY`          | The session territory, such as `AMERICA`.                                                                                             |
| `OS_USER`                | The operating system user name of the client process that initiated the database session.                                             |
| `SERVER_HOST`            | The host name of the computer where the database instance is running.                                                                 |
| `SERVICE_NAME`           | The name of the service the session is connected to, such as `SYS$USERS`.                                                             |
| `SESSION_USER`           | The database user name or schema name that identified the user at login, such as `SH`.                                                |
| `SESSIONID`              | The session identifier, such as `120456`.                                                                                             |
| `SID`                    | The session number, such as `86`.                                                                                                     |

#### Example

`SYS_CONTEXT('USERENV','NLS_DATE_FORMAT')` returns a value such as `DD-MON-RR`.

### 3.82 SYSDATE

`SYSDATE` returns the current date and time of the operating system on which the database resides. The format of the value depends on the value of the `NLS_DATE_FORMAT` initialization parameter.

#### Return Value

    DATE

#### Syntax

    SYSDATE

#### Examples

`SYSDATE` returns a value such as `13-AUG-06` with `NLS_DATE_FORMAT` set to `DD-MON-RR`.

`TO_CHAR(SYSDATE, 'MM-DD-YYYY HH24:MI:SS')` returns a value such as `08-13-2006 17:20:47`. The date format provided in the call to `TO_CHAR` displays both the date and the time.

### 3.83 SYSTIMESTAMP

`SYSTIMESTAMP` returns the system date, including fractional seconds and time zone, of the system on which the database resides.

#### Return Value

    TIMESTAMP WITH TIME ZONE

#### Syntax

    SYSTIMESTAMP

#### Example

`SYSTIMESTAMP` returns a value such as

`13-AUG-06 05.28.10.385799 PM -08:00`.

### 3.84 TAN

`TAN` returns the tangent of an angle.

#### Return Value

    NUMBER

#### Syntax

    TAN(n)

#### Arguments

`n` is a numeric expression for an angle in radians.

#### Example

`TAN(135 * 3.1415927/180)` calculates the tangent of a 135 degree angle as the value `-0.99999993`. The expression converts degrees to radians.

### 3.85 TANH

`TANH` returns the tangent of a hyperbolic angle.

#### Return Value

    NUMBER

#### Syntax

    TANH(n)

#### Arguments

`n` is a numeric expression for a hyperbolic angle.

#### Example

`TANH(.5)` returns the value `0.462117157`.

### 3.86 TO_BINARY_DOUBLE

`TO_BINARY_DOUBLE` converts a text or numeric expression to a double-precision floating-point number.

#### Return Value

    BINARY_DOUBLE

#### Syntax

    TO_BINARY_DOUBLE (expr [, fmt [, 'nlsparam' ] ])

#### Arguments

`n` can be any text or numeric expression.

`fmt` is a text expression that identifies a number format model as described in the Oracle Database SQL Language Reference.

`nlsparam` specifies the characters used by these number format elements:

- Decimal character

- Group separator

- Local currency symbol

- International currency symbol

This argument has the format shown here:

    'NLS_NUMERIC_CHARACTERS = ''dg''
     NLS_CURRENCY = ''text''
     NLS_ISO_CURRENCY = territory '

The `d` is the decimal character, and the `g` is the group separator. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

If you omit this argument or any of the NLS parameters, then this function uses the default values for your session to interpret `expr`.

#### Example

All of these examples return the value `1.235E+003`:

    TO_BINARY_DOUBLE(1234.56)

    TO_BINARY_DOUBLE('$1,234.56', '$9,999.99')

    TO_BINARY_DOUBLE('1.234,56', '9G999D99', 'NLS_NUMERIC_CHARACTERS='',.''')

### 3.87 TO_BINARY_FLOAT

`TO_BINARY_FLOAT` converts a text or numeric expression to a single-precision floating-point number.

#### Return Value

    BINARY_FLOAT

#### Syntax

    TO_BINARY_FLOAT (expr [, fmt [, 'nlsparam' ] ])

#### Arguments

`n` can be any text or numeric expression.

`fmt` is a text expression that identifies a number format model as described in the Oracle Database SQL Language Reference.

`nlsparam` specifies the characters used by these number format elements:

- Decimal character

- Group separator

- Local currency symbol

- International currency symbol

This argument has the format shown here:

    'NLS_NUMERIC_CHARACTERS = ''dg''
     NLS_CURRENCY = ''text''
     NLS_ISO_CURRENCY = territory '

The `d` is the decimal character, and the `g` is the group separator. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

If you omit this argument or any of the NLS parameters, then this function uses the default values for your session to interpret `expr`.

#### Examples

All of these examples return the value `1.235E+003`:

    TO_BINARY_FLOAT(1234.56)

    TO_BINARY_FLOAT('$1,234.56', '$9,999.99')

    TO_BINARY_FLOAT('1.234,56', '9G999D99', 'NLS_NUMERIC_CHARACTERS='',.''')

### 3.88 TO_CHAR (character)

`TO_CHAR(character)` converts a text expression to the database character set.

#### Return Value

    VARCHAR2

#### Syntax

    TO_CHAR(exp)

#### Arguments

`char` is a text expression. If it contains characters that are not represented in the database character set, then the conversion results in a loss of data.

#### Examples

`TO_CHAR('¡Una qué sorpresa!')` returns the value `?Una qu? sorpresa!` Two letters are lost in the conversion (`¡`and `é`) because they are not in the database character set.

`TO_CHAR('David Ortiz')` returns the value `David Ortiz` in the database character set. No characters are lost in this conversion because all of them are in the database character set.

### 3.89 TO_CHAR (datetime)

`TO_CHAR(datetime)` converts a datetime or interval expression to a text string in a specified format.

#### Return Value

    VARCHAR2

#### Syntax

    TO_CHAR({ datetime | interval } [, fmt [, 'nlsparam' ] ])

#### Arguments

`datetime` is a datetime expression to be converted to text.

`interval` is an interval expression to be converted to text.

`fmt` is a datetime model format specifying the format of `char`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter or can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to the Oracle Database SQL Language Reference.

`nlsparam` specifies the language in which month and day names and abbreviations are returned. This argument can have this form:

    'NLS_DATE_LANGUAGE = language'

By default, the return value is in the session date language.

#### Examples

`TO_CHAR(SYSDATE)` returns a value such as `11-APR-08`.

`TO_CHAR(SYSDATE, 'Day: MONTH DD, YYYY')` returns a value such as `Friday : APRIL 11, 2008`.

`TO_CHAR(SYSDATE, 'Day: MONTH DD, YYYY', 'NLS_DATE_LANGUAGE = Spanish')` returns a value such as `Viernes : ABRIL 11, 2008`.

### 3.90 TO_CHAR (number)

`TO_CHAR(number)` converts a numeric expression to a text value in the database character set.

#### Return Value

    VARCHAR2

#### Syntax

    TO_CHAR(n [, fmt [, 'nlsparam' ] ])

#### Arguments

`n` is a numeric expression to be converted.

`fmt` is a text expression that identifies a number format model as described in the Oracle Database SQL Language Reference.

`nlsparam` specifies the characters that are returned by these number format elements:

- Decimal character

- Group separator

- Local currency symbol

- International currency symbol

This argument has the format shown here:

    'NLS_NUMERIC_CHARACTERS = ''dg''
     NLS_CURRENCY = ''text''
     NLS_ISO_CURRENCY = territory '

The characters `d` and `g` represent the decimal character and group separator, respectively. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

If you omit this argument or any of the NLS parameters, then this function uses the default values for your session.

#### Examples

`TO_CHAR(1234567, 'C9G999G999D99')` returns a text string such as `USD1,234,567.00`.

`TO_CHAR(1234567, 'C9G999G999D99', 'NLS_ISO_CURRENCY = SPAIN')` returns the text string `EUR1,234,567.00`.

### 3.91 TO_DATE

`TO_DATE` converts a text expression to a `DATE` data type.

#### Return Value

    DATE

#### Syntax

    TO_DATE(char [, fmt [, 'nlsparam' ] ])

#### Arguments

`char` is a text expression that represents a date.

`fmt` is a datetime model format specifying the format of `char`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter or can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to the Oracle Database SQL Language Reference.

`nlsparam` specifies the language of `char`. This argument can have this form:

    'NLS_DATE_LANGUAGE = language'

By default, `char` is in the session date language.

#### Examples

`TO_DATE('October 13, 2008', 'MONTH DD, YYYY')` returns the value `13-OCT-08`.

`TO_DATE('13 Octubre 2008', 'dd month yyyy', 'NLS_DATE_LANGUAGE=SPANISH')` also returns the value `13-OCT-08`

### 3.92 TO_DSINTERVAL

`TO_DSINTERVAL` converts a text expression to an `INTERVAL DAY TO SECOND` data type.

#### Return Value

    INTERVAL DAY TO SECOND

#### Syntax

    TO_DSINTERVAL(char)

#### Arguments

`char` is a text expression to be converted.

#### Example

`TO_DSINTERVAL('360 12:45:49')` returns the value `+360 12:45:49.000000`.

### 3.93 TO_NCHAR (character)

`TO_NCHAR(character)` converts a character string to the national character set.

#### Return Value

    NVARCHAR2

#### Syntax

    TO_NCHAR(exp)

#### Arguments

`exp` is a text expression. If it contains characters that are not represented in the national character set, then the conversion results in a loss of data.

#### Example

`TO_NCHAR('David Ortiz')` returns the value `David Ortiz` in the national character set.

### 3.94 TO_NCHAR (datetime)

`TO_NCHAR(datetime)` converts a datetime or interval value to the national character set.

#### Return Value

    NVARCHAR2

#### Syntax

    TO_NCHAR({ datetime | interval }
             [, fmt [, 'nlsparam' ] ]
            )

#### Arguments

`datetime` is a datetime expression to be converted to text.

`interval` is an interval expression to be converted to text.

`fmt` is a datetime model format specifying the format of `char`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter or can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to the Oracle Database SQL Language Reference.

`nlsparam` specifies the language in which month and day names and abbreviations are returned. This argument can have this form:

    'NLS_DATE_LANGUAGE = language'

By default, the return value is in the session date language.

#### Examples

`TO_NCHAR(SYSDATE)` returns a value such as `11-APR-08`.

`TO_NCHAR(SYSDATE, 'Day: MONTH DD, YYYY')` returns a value such as `Friday : APRIL 11, 2008`.

`TO_NCHAR(SYSDATE, 'Day: MONTH DD, YYYY', 'NLS_DATE_LANGUAGE = Spanish')` returns a value such as `Viernes : ABRIL 11, 2008`.

### 3.95 TO_NCHAR (number)

`TO_NCHAR(number)` converts a number to the national character set.

#### Return Value

    NVARCHAR2

#### Syntax

    TO_CHAR(n [, fmt [, 'nlsparam' ] ])

#### Arguments

`n` is a numeric expression to be converted.

`fmt` is a text expression that identifies a number format model as described in the Oracle Database SQL Language Reference.

`nlsparam` is a text expression that specifies the characters that are returned by these number format elements:

- Decimal character

- Group separator

- Local currency symbol

- International currency symbol

This argument has the format shown here:

    'NLS_NUMERIC_CHARACTERS = ''dg''
       NLS_CURRENCY = ''text''
       NLS_ISO_CURRENCY = territory '

The characters `d` and `g` represent the decimal character and group separator, respectively. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

If you omit this argument or any of the NLS parameters, then this function uses the default values for your session.

#### Examples

`TO_NCHAR(1234567, 'C9G999G999D99')` returns a text string such as `USD1,234,567.00`.

`TO_NCHAR(1234567, 'C9G999G999D99', 'NLS_ISO_CURRENCY = SPAIN')` returns the text string `EUR1,234,567.00`.

### 3.96 TO_NUMBER

`TO_NUMBER` converts a text expression containing a number to a value of `NUMBER` data type.

#### Return Value

    NUMBER

#### Syntax

    TO_NUMBER(expr [, fmt [, 'nlsparam' ] ])

#### Arguments

`expr` is an expression to be converted to a number.

`fmt` is a text expression that identifies a number format model as described in the Oracle Database SQL Language Reference.

`nlsparam` specifies the characters used by these number format elements:

- Decimal character

- Group separator

- Local currency symbol

- International currency symbol

This argument has the format shown here:

    'NLS_NUMERIC_CHARACTERS = ''dg''
     NLS_CURRENCY = ''text''
     NLS_ISO_CURRENCY = territory '

The `d` is the decimal character, and the `g` is the group separator. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

If you omit this argument or any of the NLS parameters, then this function uses the default values for your session to interpret `expr`.

#### Examples

`TO_NUMBER('$1,234,567.89', 'L999G999G999D99')` returns the value `1234567.89`.

`TO_NUMBER('EUR1,234,567.89', 'C999G999G999D99', 'NLS_ISO_CURRENCY=SPAIN')` also returns the value `1234567.89`.

### 3.97 TO_TIMESTAMP

`TO_TIMESTAMP` converts a text expression to a value of `TIMESTAMP`.

#### Return Value

    TIMESTAMP

#### Syntax

    TO_TIMESTAMP(char [, fmt [ 'nlsparam' ] ])

#### Arguments

`char` is a text expression to be converted.

`fmt` is a datetime model format specifying the format of `char`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter or can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to the Oracle Database SQL Language Reference.

`nlsparam` specifies the language in which month and day names and abbreviations given in `char`. This argument has this form:

    'NLS_DATE_LANGUAGE = language'

By default, `char` is in the session date language.

#### Examples

`TO_TIMESTAMP('10-SEP-0614:10:10.123000','DD-MON-RRHH24:MI:SS.FF')` returns the value `10-SEP-06 02.10.10.123000 PM`.

`TO_TIMESTAMP('10-AGOSTO-0714:10:10', 'DD-MON-RRHH24:MI:SS.FF', 'NLS_DATE_LANGUAGE=SPANISH')` returns the value `10-AUG-07 02.10.10.000000 PM`.

### 3.98 TO_TIMESTAMP_TZ

`TO_TIMESTAMP_TZ` converts a text expression to a value of `TIMESTAMP``WITH``TIME``ZONE` data type.

#### Return Value

    TIMESTAMP WITH TIME ZONE

#### Syntax

    TO_TIMESTAMP_TZ(char [, fmt [ 'nlsparam' ] ])

#### Arguments

`char` is a text expression to be converted.

`fmt` is a datetime model format specifying the format of `char`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter or can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to the Oracle Database SQL Language Reference.

`nlsparam` specifies the language in which month and day names and abbreviations given in `char`. This argument has this form:

    'NLS_DATE_LANGUAGE = language'

By default, `char` is in the session date language.

#### Examples

`TO_TIMESTAMP_TZ('2006-03-26 7:33:00 -4:00', 'YYYY-MM-DD HH:MI:SS TZH:TZM')` returns the value `26-MAR-06 07.33.00.000000 AM -04:00`.

`TO_TIMESTAMP_TZ('2006-AGOSTO-13 7:33:00 -4:00', 'YYYY-MONTH-DD HH:MI:SS TZH:TZM', 'NLS_DATE_LANGUAGE=SPANISH')` returns the value `13-AUG-06 07.33.00.000000 AM -04:00`.

### 3.99 TO_YMINTERVAL

`TO_YMINTERVAL` converts a text expression to an `INTERVAL YEAR TO MONTH` data type. The function accepts argument in one of the two formats:

- SQL interval format compatible with the SQL standard (ISO/IEC 9075:2003)

- ISO duration format compatible with the ISO 8601:2004 standard

#### Return Value

    INTERVAL YEAR TO MONTH

#### Syntax

    TO_YMINTERVAL  ( ' { sql_format | ym_iso_format } ' )

    sql_format::=
    [+|-] years - months

    ym_iso_format::=
    [-] P  [ years Y  ] [months M ] [days D ] [ T  [hours H ] [minutes M ] [seconds [. frac_secs] S  ] ]

#### Arguments

In SQL format:

`years` is an integer between 0 and 999999999

`months` is an integer between 0 and 11.

Additional blanks are allowed between format elements.

In ISO format:

`years` and `months` are integers between 0 and 999999999.

`days`, `hours`, `minutes`, `seconds`, and `frac_secs` are nonnegative integers and are ignored.

No blanks are allowed in the value.

#### Examples

`TO_YMINTERVAL('1-6')` and `TO_YMINTERVAL('P1Y6M')` return the value `+01-06` for 1 year and 6 months.

`SYSDATE + TO_YMINTERVAL('1-6')` adds one year and six months to the current date. When `SYSDATE` is `15-APR-08`, the value is `15-OCT-09`.

`SYSDATE + TO_YMINTERVAL('P1Y6M')` adds one year and six months to the current date using ISO format. When `SYSDATE` is `15-APR-08`, the value is `15-OCT-09`.

`SYSDATE + TO_YMINTERVAL('-1-2')` subtracts one year and two months from the current date. When `SYSDATE` is `15-APR-08`, the value is `15-FEB-07`.

### 3.100 TRANSLATE

`TRANSLATE` enables you to make several single-character, one-to-one substitutions in one operation. This expression returns an expression with all occurrences of each character in one string replaced by its corresponding character in a second string.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    TRANSLATE(expr, from_string, to_string)

#### Arguments

`expr` is a text expression to be modified.

`from_string` consists of one or more characters to be replaced in `expr`.

`to_string` consists of one or more characters that replace the corresponding characters in `from_string`. This string can be shorter than `from_string`, so that a null replaces the extra characters. However, `to_string` cannot be empty.

#### Example

`TRANSLATE('disk', 'dk', 'Dc')` returns the value `Disc`.

### 3.101 TRANSLATE (USING)

`TRANSLATE` converts a text string between the database character set and the national character set.

Note: The `TRANSLATE USING` function is supported primarily for ANSI compatibility. Oracle recommends that you use the `TO_CHAR` and `TO_NCHAR` functions for converting data to the database or national character sets. `TO_CHAR` and `TO_NCHAR` can take as arguments a greater variety of data types than `TRANSLATE USING`, which accepts only character data.

#### Return Value

    VARCHAR2 | NVARCHAR2

#### Syntax

    TRANSLATE (char USING { CHAR_CS | NCHAR_CS } )

#### Arguments

`char` is a text expression to be converted to the database character set (`USING CHAR_CS`) or the national character set (`USING NCHAR_CS`).

#### Example

`TRANSLATE('north by northwest' USING NCHAR_CS)` returns the value `north by northwest` in the national character set.

### 3.102 TRIM

`TRIM` removes leading or trailing characters (or both) from a character string.

#### Return Value

    VARCHAR2

#### Syntax

    TRIM([ { { LEADING | TRAILING | BOTH }[ trim_character ]
           | trim_character
           }
           FROM
         ]
         trim_source
        )

#### Arguments

`LEADING` removes matching characters from the beginning of the string.

`TRAILING` removes matching characters from the end of the string.

`BOTH` removes matching characters from both the beginning and the end of the string. (Default)

`trim_character` is a single character to be removed. By default, it is a space.

`trim_source` is the text expression to be trimmed.

#### Examples

`TRIM('0' FROM '00026501.6703000')` returns the value `26501.6703`.

`TRIM(LEADING '!' FROM '!!Help! Help!!')` returns the value `Help! Help!!`.

### 3.103 TRUNC (number)

`TRUNC` shortens a numeric expression to a specified number of decimal places.

#### Return Value

    NUMBER

#### Syntax

    TRUNC(n1 [, n2 ])

#### Arguments

`n1` is the numeric expression to be truncated.

`n2` is the number of decimal places. A positive number truncates digits to the right of the decimal point, and a negative number replaces digits to the left of the decimal point. The default value is zero (0).

#### Examples

`TRUNC(15.79)` returns the value `15`.

`TRUNC(15.79, 1)` returns the value `15.7`.

`TRUNC(15.79, -1)` returns the value `10`.

### 3.104 TZ_OFFSET

`TZ_OFFSET` returns the time zone offset from Coordinated Universal Time (UTC).

#### Return Value

    VARCHAR2

#### Syntax

    TZ_OFFSET({ 'time_zone_name' | '{ + | - } hh:mi'
              | SESSIONTIMEZONE | DBTMEZONE
              }
             )

#### Arguments

`time_zone_name` is the name of a time zone.

`hh:mm` are hours and minutes. This argument simply returns itself.

`SESSIONTIMEZONE` returns the session time zone.

`DBTIMEZONE` returns the database time zone.

#### Examples

`TZ_OFFSET('US/Eastern')` returns the offset `-04:00` during Daylight Savings Time.

`TZ_OFFSET('EST')` returns the offset `-05:00`.

`TZ_OFFSET(DBTIMEZONE)` returns the offset `-07:00` for Mountain Standard Time.

### 3.105 UID

`UID` returns a unique identifier (UID) for the session user (the user who logged on).

#### Return Value

    INTEGER

#### Syntax

    UID

#### Example

`UID` returns a value such as `76`.

### 3.106 UNISTR

`UNISTR` converts a text string to the national character set.

#### Return Value

    NVARCHAR2

#### Syntax

    UNISTR ( string )

#### Arguments

`string` can be any text expression. For portability, Oracle recommends using only ASCII characters and Unicode encoding values as text literals. A Unicode encoding value has the form \\xxxx where xxxx is the hexadecimal value of a character. Supplementary characters are encoded as two code units, the first from the high-surrogates range (U+D800 to U+DBFF), and the second from the low-surrogates range (U+DC00 to U+DFFF). To include a literal backslash in the string, precede it with another backslash (\\).

#### Example

`UNISTR('abc\00e5\00f1\00f6')` returns the value `abcåñö`.

### 3.107 UPPER

`UPPER` converts all alphabetic characters in a text expression to uppercase. The data type of the return value is the same as the original text.

#### Return Value

    CHAR | NCHAR | VARCHAR2 | NVARCHAR2

#### Syntax

    UPPER(char)

#### Arguments

`char` can be any text expression.

#### Example

`UPPER('This is an emergency')` returns the string `THIS IS AN EMERGENCY`.

### 3.108 USER

`USER` returns the name of the session user (the user who logged on).

#### Return Value

    VARCHAR2

#### Syntax

    USER

#### Example

`USER` returns a value such as `GLOBAL`.

### 3.109 VSIZE

`VSIZE` returns the number of bytes in the internal representation of an expression. It returns `NULL` for a null expression.

#### Return Value

    NUMBER

#### Syntax

    VSIZE (expr)

#### Arguments

`expr` can be an expression of any data type.

#### Example

`VSIZE('Sound of thunder')` returns the value `16`.

`VSIZE(CHANNEL.LONG_DESCRIPTION)` returns the following values:

| Channel      | VSIZE |
|:-------------|:------|
| Catalog      | 7     |
| Direct Sales | 12    |
| Internet     | 8     |

### 3.110 WIDTH_BUCKET

`WIDTH_BUCKET` enables you to construct a histogram range divided into intervals of identical size. The function returns the bucket number into which the value of an expression falls.

When needed, `WIDTH_BUCKET` creates an underflow bucket numbered 0 and an overflow bucket numbered `num_buckets`+1. These buckets handle values outside the specified range and are helpful in checking the reasonableness of the end points.

#### Return Value

    NUMBER

#### Syntax

    WIDTH_BUCKET
       (expr, min_value, max_value, num_buckets)

#### Arguments

`expr` is the expression for which the histogram is being created. This expression must evaluate to a numeric or datetime value or to a value. If `expr` evaluates to null, then the function returns `NULL`.

`min_value` and `max_value` are expressions for the end points of the acceptable range for `expr`. Both of these expressions must evaluate to numeric or datetime values, and neither can evaluate to null.

`num_buckets` is an expression for the number of buckets. This expression must evaluate to a positive integer.

#### Example

`WIDTH_BUCKET(13, 0, 20, 4)` returns the value `3`. It creates four buckets from 0 to 20 and sorts the value 13 into bucket 3.

`WIDTH_BUCKET(-5, 0, 20, 4)` returns the value `0`. The value `-5` is below the beginning of the range.
