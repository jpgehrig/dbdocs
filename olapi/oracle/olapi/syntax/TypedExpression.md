Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](TimeZoneExpression.md)
- [Next Class](UnaryOperatorExpression.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.syntax

## Class TypedExpression

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - oracle.olapi.syntax.TypedExpression

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  <!-- -->

  Direct Known Subclasses:
  [AggregationFunctionExpression](AggregationFunctionExpression.md), [ColumnExpression](ColumnExpression.md), [LiteralExpression](LiteralExpression.md), [OLAPDMLExpression](OLAPDMLExpression.md), [OLAPFunctionExpression](OLAPFunctionExpression.md), [PlaceholderExpression](PlaceholderExpression.md), [QDRExpression](QDRExpression.md), [RowExpression](RowExpression.md), [UnresolvedExpression](UnresolvedExpression.md)

  ------------------------------------------------------------------------



      public abstract class TypedExpression
      extends Expression

  An `Expression` that is a combination of one or more values, operators, and functions that evaluates to a value. A `TypedExpression` has an associated `DataType` that represents the data type of the value.
  Many of the `TypedExpression` methods return a `TypedExpression` that has the same syntax as the SQL function of the same name. When Oracle OLAP evaluates the `TypedExpression`, it returns the same value that the SQL function returns.

  In the examples of the methods of this class, the `mp` object is the `MdmMetadataProvider` for the session.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                                                                                                |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TypedExpression`           | `abs``()`<br>Calculates the absolute value of the numeric expression value of this `TypedExpression`.                                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `acos``()`<br>Calculates the angle value in radians of the cosine value of this `TypedExpression`.                                                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `addMonths``(int rhs)`<br>Creates a `TypedExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.                                                                                                                                                                                   |
    | `TypedExpression`           | `addMonths``(TypedExpression rhs)`<br>Creates a `TypedExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.                                                                                                                                                                       |
    | `TypedExpression`           | `ascii``()`<br>Creates a `TypedExpression` that evaluates to the ASCII decimal representation of the first character of the value of this `TypedExpression`.                                                                                                                                                                                                          |
    | `TypedExpression`           | `asciiStr``()`<br>Converts the value of this `TypedExpression` to ASCII.                                                                                                                                                                                                                                                                                              |
    | `TypedExpression`           | `asin``()`<br>Calculates the angle value in radians of the specified sine.                                                                                                                                                                                                                                                                                            |
    | `TypedExpression`           | `atan``()`<br>Calculates the angle value in radians of the specified tangent.                                                                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `atan2``(TypedExpression rhs)`<br>Calculates the full-range (0 - 2 *pi*) numeric value that indicates the arc tangent of the specified ratio.                                                                                                                                                                                                                         |
    | [`Condition`](Condition.md) | `between``(TypedExpression start, TypedExpression end, boolean negate)`<br>Indicates whether the value of this `TypedExpression` is in the specified range of values.                                                                                                                                                                                                 |
    | `static TypedExpression`    | `binToNum``(TypedExpression[] args)`<br>Converts an array of bits to the equivalent number.                                                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `bitAnd``(TypedExpression rhs)`<br>Computes a bitwise `AND` operation on the bits of two nonnegative integers.                                                                                                                                                                                                                                                        |
    | `TypedExpression`           | `cast``(java.lang.String datatype)`<br>Converts the data type of the value of this `TypedExpression` into another data type value.                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `ceil``()`<br>Calculates the smallest integer that is greater than or equal to the value of this `TypedExpression`.                                                                                                                                                                                                                                                   |
    | `TypedExpression`           | `charToROWID``()`<br>Converts the value of this `TypedExpression` from the `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2` data type to the `ROWID` data type.                                                                                                                                                                                                            |
    | `TypedExpression`           | `chr``()`<br>Converts the integer value of this `TypedExpression` to the character in the database character set with the binary equivalent of the integer.                                                                                                                                                                                                           |
    | `TypedExpression`           | `chr``(boolean usingNChar)`<br>Converts the integer value of this `TypedExpression` to the character in the national character set with the binary equivalent of the integer.                                                                                                                                                                                         |
    | `static TypedExpression`    | `coalesce``(TypedExpression[] args)`<br>Creates a `TypedExpression` that evaluates to the first non-null expression in a list of expressions, or to `null` when all of the expressions evaluate to `null`.                                                                                                                                                            |
    | `TypedExpression`           | `compose``()`<br>Converts the value of this `TypedExpression` to a Unicode string in the same character set as this expression.                                                                                                                                                                                                                                       |
    | `TypedExpression`           | `concat``(java.lang.String rhs)`<br>Concatentates two text expressions as a single character string.                                                                                                                                                                                                                                                                  |
    | `TypedExpression`           | `concat``(TypedExpression rhs)`<br>Concatenates two text expressions as a single character string.                                                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `convert``(TypedExpression destCharSet)`<br>Converts the character string value of this `TypedExpression` from one character set to the specified character set.                                                                                                                                                                                                      |
    | `TypedExpression`           | `convert``(TypedExpression destCharSet, TypedExpression sourceCharSet)`<br>Converts the character string value of this `TypedExpression` from the source character set to the destination character set.                                                                                                                                                              |
    | `TypedExpression`           | `cos``()`<br>Calculates the cosine of the value (interpreted as an angle value in radians) of this `TypedExpression`.                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `cosh``()`<br>Calculates the hyperbolic cosine of the value (interpreted as an angle value in radians) of this `TypedExpression`.                                                                                                                                                                                                                                     |
    | `static TypedExpression`    | `currentDate``()`<br>Creates a `TypedExpression` that evaluates to the current date in the session time zone.                                                                                                                                                                                                                                                         |
    | `static TypedExpression`    | `currentTime``(TypedExpression precision)`<br>Creates a `TypedExpression` that evaluates to the current date and time in the session time zone.                                                                                                                                                                                                                       |
    | `static TypedExpression`    | `dbTimeZone``()`<br>Creates a `TypedExpression` that evaluates to the value of the database time zone as either a time zone offset from Coordinated Universal Time (UTC) or a time zone region name.                                                                                                                                                                  |
    | `TypedExpression`           | `decode``(TypedExpression[] cases, TypedExpression defaultExpression)`<br>Compares the value of this `TypedExpression` to one or more search strings one by one.                                                                                                                                                                                                      |
    | `TypedExpression`           | `decompose``()`<br>Decomposes the Unicode character string value of this `TypedExpression` and returns a `TypedExpression` in the same character set.                                                                                                                                                                                                                 |
    | `TypedExpression`           | `deref``()`<br>Creates a `TypedExpression` that evaluates to the object reference of the value of this `TypedExpression`, which must evaluate to a `REF` to an object.                                                                                                                                                                                                |
    | `TypedExpression`           | `div``(double rhs)`<br>Divides the value of this `TypedExpression` by the specified `double` value.                                                                                                                                                                                                                                                                   |
    | `TypedExpression`           | `div``(float rhs)`<br>Divides the value of this `TypedExpression` by the specified `float` value.                                                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `div``(int rhs)`<br>Divides the value of this `TypedExpression` by the specified `int` value.                                                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `div``(short rhs)`<br>Divides the value of this `TypedExpression` by the specified `short` value.                                                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `div``(TypedExpression rhs)`<br>Divides the value of this `TypedExpression` by the value of the specified `TypedExpression`.                                                                                                                                                                                                                                          |
    | `TypedExpression`           | `dump``(TypedExpression returnFormat, TypedExpression startPosition, TypedExpression length)`<br>Creates a `TypedExpression` that evaluates to the data type code, length in bytes, and internal representation of the value of this `TypedExpression`.                                                                                                               |
    | [`Condition`](Condition.md) | `eq``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is equal to the specified `double` value.                                                                                                                                                                                                                                                 |
    | [`Condition`](Condition.md) | `eq``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is equal to the specified `float` value.                                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `eq``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is equal to the specified `int` value.                                                                                                                                                                                                                                                       |
    | [`Condition`](Condition.md) | `eq``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is equal to the specified `short` value.                                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `eq``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is equal to the value of the specified `TypedExpression`.                                                                                                                                                                                                                        |
    | `TypedExpression`           | `exp``()`<br>Calculates the value of 2.71828183 raised to the power of the value of this `TypedExpression`.                                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `extractDay``()`<br>Extracts the day from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                                   |
    | `TypedExpression`           | `extractHour``()`<br>Extracts the hour from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `extractMinute``()`<br>Extracts the minute from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `extractMonth``()`<br>Extracts the month from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `extractSecond``()`<br>Extracts the second from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `extractTimeZoneAbbr``()`<br>Extracts the name of the time zone abbreviation from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                           |
    | `TypedExpression`           | `extractTimeZoneHour``()`<br>Extracts the time zone hour from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `extractTimeZoneMinute``()`<br>Extracts the time zone minute from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `extractTimeZoneRegion``()`<br>Extracts the name of the time zone region from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                               |
    | `TypedExpression`           | `extractYear``()`<br>Extracts the year from the datetime or interval value of this `TypedExpression`.                                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `floor``()`<br>Calculates the largest integer that is equal to or less than the value of this `TypedExpression`.                                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `fromTZ``(TypedExpression timeZoneValue)`<br>Converts the timestamp value of this `TypedExpression` and the specified time zone to a `TIMESTAMP WITH TIME ZONE` data type.                                                                                                                                                                                            |
    | [`Condition`](Condition.md) | `ge``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `double` value.                                                                                                                                                                                                                                 |
    | [`Condition`](Condition.md) | `ge``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `float` value.                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `ge``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `int` value.                                                                                                                                                                                                                                       |
    | [`Condition`](Condition.md) | `ge``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `short` value.                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `ge``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than or equal to the value of the specified `TypedExpression`.                                                                                                                                                                                                        |
    | [`DataType`](DataType.md)   | `getDataType``()`<br>Gets the data type of this `TypedExpression`, which is represented by a `DataType` object.                                                                                                                                                                                                                                                       |
    | `static TypedExpression`    | `greatest``(TypedExpression[] args)`<br>Creates a `TypedExpression` that evaluates to the largest expression in a list of expressions.                                                                                                                                                                                                                                |
    | [`Condition`](Condition.md) | `gt``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than the specified `double` value.                                                                                                                                                                                                                                             |
    | [`Condition`](Condition.md) | `gt``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than the specified `float` value.                                                                                                                                                                                                                                               |
    | [`Condition`](Condition.md) | `gt``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than the specified `int` value.                                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `gt``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than the specified `short` value.                                                                                                                                                                                                                                               |
    | [`Condition`](Condition.md) | `gt``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is greater than the value of the specified `TypedExpression`.                                                                                                                                                                                                                    |
    | `TypedExpression`           | `hexToRAW``()`<br>Converts to a raw value the value of this `TypedExpression`, which contains hexadecimal digits in the `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2` character set.                                                                                                                                                                                    |
    | [`Condition`](Condition.md) | `in``(TypedExpression[] list)`<br>Indicates whether this `TypedExpression` occurs in the specified list of expressions.                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `initcap``()`<br>Converts the first letter of each word of this `TypedExpression` to uppercase and all other letters to lowercase.                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `instr``(TypedExpression substring, TypedExpression position, TypedExpression occurrence)`<br>Searches the value of this `TypedExpression` for the characters of the specified substring.                                                                                                                                                                             |
    | `TypedExpression`           | `instr2``(TypedExpression substring, TypedExpression position, TypedExpression occurrence)`<br>Searches the value of this `TypedExpression` for the UCS2 code points of the specified substring.                                                                                                                                                                      |
    | `TypedExpression`           | `instr4``(TypedExpression substring, TypedExpression position, TypedExpression occurrence)`<br>Searches the value of this `TypedExpression` for the UCS4 code points of the specified substring.                                                                                                                                                                      |
    | `TypedExpression`           | `instrB``(TypedExpression substring, TypedExpression position, TypedExpression occurrence)`<br>Searches the value of this `TypedExpression` for the bytes of the specified substring.                                                                                                                                                                                 |
    | `TypedExpression`           | `instrC``(TypedExpression substring, TypedExpression position, TypedExpression occurrence)`<br>Searches the value of this `TypedExpression` for the Unicode complete characters of the specified substring.                                                                                                                                                           |
    | [`Condition`](Condition.md) | `isInfinite``(boolean negate)`<br>Indicates whether the value of this `TypedExpression` is the special value `INFINITE`.                                                                                                                                                                                                                                              |
    | [`Condition`](Condition.md) | `isNAN``(boolean negate)`<br>Indicates whether the value of this `TypedExpression` is the special value `NAN` (not a number).                                                                                                                                                                                                                                         |
    | [`Condition`](Condition.md) | `isNotNull``()`<br>Creates a `Condition` that evaluates to `true` if the value of this `TypedExpression` is not `null`.                                                                                                                                                                                                                                               |
    | [`Condition`](Condition.md) | `isNull``()`<br>Creates a `Condition` that evaluates to `true` if the value of this `TypedExpression` is `null`.                                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `lastDay``()`<br>Creates a `TypedExpression` that evaluates to the last day of the month in which the date of the value of this `TypedExpression` falls.                                                                                                                                                                                                              |
    | [`Condition`](Condition.md) | `le``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is less than or equal to the specified `double` value.                                                                                                                                                                                                                                    |
    | [`Condition`](Condition.md) | `le``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is less than or equal to the specified `float` value.                                                                                                                                                                                                                                      |
    | [`Condition`](Condition.md) | `le``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is less than or equal to the specified `int` value.                                                                                                                                                                                                                                          |
    | [`Condition`](Condition.md) | `le``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is less than or equal to the specified `short` value.                                                                                                                                                                                                                                      |
    | [`Condition`](Condition.md) | `le``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is less than or equal to the value of the specified `TypedExpression`.                                                                                                                                                                                                           |
    | `static TypedExpression`    | `least``(TypedExpression[] args)`<br>Creates a `TypedExpression` that evaluates to the smallest expression in a list of expressions.                                                                                                                                                                                                                                  |
    | `TypedExpression`           | `length``()`<br>Counts the number of characters in the text expression of this `TypedExpression`.                                                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `length2``()`<br>Counts the number of UCS2 code points in the text expression of this `TypedExpression`.                                                                                                                                                                                                                                                              |
    | `TypedExpression`           | `length4``()`<br>Counts the number of UC42 code points in the text expression of this `TypedExpression`.                                                                                                                                                                                                                                                              |
    | `TypedExpression`           | `lengthB``()`<br>Counts the number of bytes in the text expression of this `TypedExpression`.                                                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `lengthC``()`<br>Counts the number of Unicode characters in the text expression of this `TypedExpression`.                                                                                                                                                                                                                                                            |
    | [`Condition`](Condition.md) | `like``(TypedExpression pattern)`<br>Indicates whether the specified text pattern occurs in the value of this `TypedExpression`.                                                                                                                                                                                                                                      |
    | [`Condition`](Condition.md) | `like``(TypedExpression pattern, TypedExpression escape, boolean negate)`<br>Indicates whether the specified text pattern occurs in the value of this `TypedExpression`.                                                                                                                                                                                              |
    | [`Condition`](Condition.md) | `like2``(TypedExpression pattern, TypedExpression escape, boolean negate)`<br>Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests UCS2 code points and treats a Unicode supplementary character as one character.                                                                                       |
    | [`Condition`](Condition.md) | `like4``(TypedExpression pattern, TypedExpression escape, boolean negate)`<br>Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests UCS4 code points and treats a composite character as one character.                                                                                                   |
    | [`Condition`](Condition.md) | `likeC``(TypedExpression pattern, TypedExpression escape, boolean negate)`<br>Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests Unicode complete characters and treats a Unicode supplementary character as two characters.                                                                           |
    | `TypedExpression`           | `ln``()`<br>Calculates the natural logarithm of the value of this `TypedExpression`.                                                                                                                                                                                                                                                                                  |
    | `static TypedExpression`    | `localTimestamp``(TypedExpression precision)`<br>Creates a `TypedExpression` that evaluates to the current date and time in the session time zone.                                                                                                                                                                                                                    |
    | `TypedExpression`           | `log``(TypedExpression n1)`<br>Calculates the logarithm of the value of the specified `TypedExpression` where the value of this `TypedExpression` is the base.                                                                                                                                                                                                        |
    | `TypedExpression`           | `lower``()`<br>Converts to lowercase all alphabetic characters in the value of this `TypedExpression`.                                                                                                                                                                                                                                                                |
    | `TypedExpression`           | `lpad``(TypedExpression n, TypedExpression expr2)`<br>Adds the specified number of characters to the left of the value of this `TypedExpression`.                                                                                                                                                                                                                     |
    | [`Condition`](Condition.md) | `lt``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is less than the specified `double` value.                                                                                                                                                                                                                                                |
    | [`Condition`](Condition.md) | `lt``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is less than the specified `float` value.                                                                                                                                                                                                                                                  |
    | [`Condition`](Condition.md) | `lt``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is less than the specified `int` value.                                                                                                                                                                                                                                                      |
    | [`Condition`](Condition.md) | `lt``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is less than the specified `short` value.                                                                                                                                                                                                                                                  |
    | [`Condition`](Condition.md) | `lt``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is less than the value of the specified `TypedExpression`.                                                                                                                                                                                                                       |
    | `TypedExpression`           | `ltrim``(TypedExpression set)`<br>Searches the value of this `TypedExpression`, starting from the left, and removes all of the characters that match the characters in the trim expression `set`, until an unmatched character occurs.                                                                                                                                |
    | `TypedExpression`           | `minus``()`<br>Negates the value of this `TypedExpression`.                                                                                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `minus``(double rhs)`<br>Subtracts the specified `double` value from the value of this `TypedExpression`.                                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `minus``(float rhs)`<br>Subtracts the specified `float` value from the value of this `TypedExpression`.                                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `minus``(int rhs)`<br>Subtracts the specified `int` value from the value of this `TypedExpression`.                                                                                                                                                                                                                                                                   |
    | `TypedExpression`           | `minus``(short rhs)`<br>Subtracts the specified `short` value from the value of this `TypedExpression`.                                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `minus``(TypedExpression rhs)`<br>Subtracts the value of the specified `TypedExpression` from the value of this `TypedExpression`.                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `mod``(TypedExpression n1)`<br>Calculates the remainder of the value of this `TypedExpression` divided by the value of the specified `TypedExpression`.                                                                                                                                                                                                               |
    | `TypedExpression`           | `monthsBetween``(TypedExpression date2)`<br>Calculates the number of months between the date value of this `TypedExpression` and the specified date.                                                                                                                                                                                                                  |
    | `TypedExpression`           | `nanvl``(TypedExpression n1)`<br>Replaces the value of this `TypedExpression` with the value of the specified `TypedExpression` if the value of this `TypedExpression` is the special value `NAN` (not a number).                                                                                                                                                     |
    | [`Condition`](Condition.md) | `ne``(double rhs)`<br>Indicates whether the value of this `TypedExpression` is not equal to the specified `double` value.                                                                                                                                                                                                                                             |
    | [`Condition`](Condition.md) | `ne``(float rhs)`<br>Indicates whether the value of this `TypedExpression` is not equal to the specified `float` value.                                                                                                                                                                                                                                               |
    | [`Condition`](Condition.md) | `ne``(int rhs)`<br>Indicates whether the value of this `TypedExpression` is not equal to the specified `int` value.                                                                                                                                                                                                                                                   |
    | [`Condition`](Condition.md) | `ne``(short rhs)`<br>Indicates whether the value of this `TypedExpression` is not equal to the specified `short` value.                                                                                                                                                                                                                                               |
    | [`Condition`](Condition.md) | `ne``(TypedExpression rhs)`<br>Indicates whether the value of this `TypedExpression` is not equal to the value of the specified `TypedExpression`.                                                                                                                                                                                                                    |
    | `TypedExpression`           | `newTime``(TypedExpression timeZone1, TypedExpression timeZone2)`<br>Converts the date and time value of this `TypedExpression` from one time zone to another.                                                                                                                                                                                                        |
    | `TypedExpression`           | `nextDay``(TypedExpression dayName)`<br>Creates a `TypedExpression` that evaluates to the first instance of the specified day of the week that follows the date value of this `TypedExpression`.                                                                                                                                                                      |
    | `TypedExpression`           | `nlsCharsetDeclLen``(TypedExpression charSetID)`<br>Creates a `TypedExpression` that evaluates to the declaration length (in number of characters) of the `NCHAR` column that this `TypedExpression` represents.                                                                                                                                                      |
    | `TypedExpression`           | `nlsCharsetID``()`<br>Creates a `TypedExpression` that evaluates to the character set ID number corresponding to character set name specified by this `TypedExpression`.                                                                                                                                                                                              |
    | `TypedExpression`           | `nlsCharsetName``()`<br>Creates a `TypedExpression` that evaluates to the name of the character set that corresponds to the ID number specified by the value of this `TypedExpression`.                                                                                                                                                                               |
    | `TypedExpression`           | `nlsInitcap``(TypedExpression nlsparam)`<br>Converts the first letter of each word of this `TypedExpression` to uppercase and all other letters to lowercase.                                                                                                                                                                                                         |
    | `TypedExpression`           | `nlsLower``(TypedExpression nlsparam)`<br>Converts to lowercase all alphabetic characters in the value of this `TypedExpression`.                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `nlsSort``(TypedExpression nlsparam)`<br>Creates a `TypedExpression` that evaluates to the string of bytes that Oracle OLAP uses to sort a text string.                                                                                                                                                                                                               |
    | `TypedExpression`           | `nlsUpper``(TypedExpression nlsparam)`<br>Converts to uppercase all alphabetic characters in the value of this `TypedExpression`.                                                                                                                                                                                                                                     |
    | [`Condition`](Condition.md) | `notIn``(TypedExpression[] list)`<br>Indicates whether this `TypedExpression` does not occur in the specified list of expressions.                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `nullIf``(TypedExpression expr2)`<br>Compares the value of this `TypedExpression` to the value of the `expr2` `TypedExpression`.                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `numToDSInterval``(TypedExpression intervalUnit)`<br>Converts the value of this `TypedExpression` to a `DS_INTERVAL` literal.                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `numToYMInterval``(TypedExpression intervalUnit)`<br>Converts the value of this `TypedExpression` to a `YM_INTERVAL` literal.                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `nvl``(TypedExpression expr2)`<br>Replaces the null value of this `TypedExpression` with the string specified by `expr2`.                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `nvl2``(TypedExpression expr2, TypedExpression expr3)`<br>Replaces the value of this `TypedExpression` with the expression specified by `expr2` or with the expression specified by `expr3` if the value of this `TypedExpression` is `null`.                                                                                                                         |
    | `TypedExpression`           | `oraHash``(TypedExpression maxBucket, TypedExpression seedValue)`<br>Computes the hash value of the value of this `TypedExpression`.                                                                                                                                                                                                                                  |
    | `TypedExpression`           | `plus``(double rhs)`<br>Adds the specified `double` value to the value of this `TypedExpression`.                                                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `plus``(float rhs)`<br>Adds the specified `float` value to the value of this `TypedExpression`.                                                                                                                                                                                                                                                                       |
    | `TypedExpression`           | `plus``(int rhs)`<br>Adds the specified `int` value to the value of this `TypedExpression`.                                                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `plus``(short rhs)`<br>Adds the specified `short` value to the value of this `TypedExpression`.                                                                                                                                                                                                                                                                       |
    | `TypedExpression`           | `plus``(TypedExpression rhs)`<br>Adds the value of the specified `TypedExpression` to the value of this `TypedExpression`.                                                                                                                                                                                                                                            |
    | `TypedExpression`           | `power``(TypedExpression rhs)`<br>Raises the value of this `TypedExpression` to the power of the value of the specified `TypedExpression`.                                                                                                                                                                                                                            |
    | `TypedExpression`           | `rawToHex``()`<br>Converts the raw value of this `TypedExpression`, to a character string value containing the hexadecimal representation of the raw value.                                                                                                                                                                                                           |
    | `TypedExpression`           | `rawToNHex``()`<br>Converts the raw value of this `TypedExpression`, to a character string value in the national character set; the value contains the hexadecimal representation of the raw value.                                                                                                                                                                   |
    | `TypedExpression`           | `regexpInstr``(TypedExpression pattern, TypedExpression position, TypedExpression occurrence, TypedExpression returnOption, TypedExpression matchParameter)`<br>Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression`.                                                                   |
    | `TypedExpression`           | `regexpReplace``(TypedExpression pattern, TypedExpression replaceString, TypedExpression position, TypedExpression occurrence, TypedExpression matchParameter)`<br>Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression` and the replacement of the matching string with another string. |
    | `TypedExpression`           | `regexpSubstr``(TypedExpression pattern, TypedExpression position, TypedExpression occurrence, TypedExpression matchParameter)`<br>Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression`.                                                                                                |
    | `TypedExpression`           | `remainder``(TypedExpression rhs)`<br>Divides the value of this `TypedExpression` by the value of the specified `TypedExpression` and calculates the rounded remainder.                                                                                                                                                                                               |
    | `TypedExpression`           | `replace``(TypedExpression searchString, TypedExpression replacementString)`<br>Searches a string for a pattern, replaces it with another string, and returns the modified string.                                                                                                                                                                                    |
    | `TypedExpression`           | `round``(TypedExpression precision)`<br>Rounds the value of this `TypedExpression` to the precision specified.                                                                                                                                                                                                                                                        |
    | `TypedExpression`           | `rowIDToChar``()`<br>Converts the `ROWID` value of this `TypedExpression` to the `VARCHAR2` data type.                                                                                                                                                                                                                                                                |
    | `TypedExpression`           | `rowIDToNChar``()`<br>Converts the `ROWID` value of this `TypedExpression` to the `NVARCHAR2` data type.                                                                                                                                                                                                                                                              |
    | `TypedExpression`           | `rpad``(TypedExpression n, TypedExpression expr2)`<br>Adds the specified number of characters to the right of the value of this `TypedExpression`.                                                                                                                                                                                                                    |
    | `TypedExpression`           | `rtrim``(TypedExpression set)`<br>Searches the value of this `TypedExpression`, starting from the right, and removes all of the characters that match the characters in the trim expression `set`, until an unmatched character occurs.                                                                                                                               |
    | `TypedExpression`           | `scnToTimestamp``()`<br>Creates a `TypedExpression` that evaluates to the approximate timestamp that is associated with the system change number (SCN) value of this `TypedExpression`.                                                                                                                                                                               |
    | `static TypedExpression`    | `sessionTimeZone``()`<br>Creates a `TypedExpression` that evaluates to the time zone of the current session.                                                                                                                                                                                                                                                          |
    | `TypedExpression`           | `sign``()`<br>Determines whether a number is less than, equal to, or greater than 0 (zero).                                                                                                                                                                                                                                                                           |
    | `TypedExpression`           | `sin``()`<br>Calculates the sine of an angle expressed in radians.                                                                                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `sinh``()`<br>Calculates the hyperbolic sine of the value of this `TypedExpression`.                                                                                                                                                                                                                                                                                  |
    | `TypedExpression`           | `soundex``()`<br>Creates a `TypedExpression` that evaluates to a character string that contains the phonetic representation of the character that is the value of this `TypedExpresson`.                                                                                                                                                                              |
    | `TypedExpression`           | `sqrt``()`<br>Calculates the square root of the value of this `TypedExpression`.                                                                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `substr``(TypedExpression position, TypedExpression substringLength)`<br>Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified character position and includes the specified number of characters.                                                                                            |
    | `TypedExpression`           | `substr2``(TypedExpression position, TypedExpression substringLength)`<br>Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified UCS2 code point position and extends the specified number of UCS2 code points.                                                                                |
    | `TypedExpression`           | `substr4``(TypedExpression position, TypedExpression substringLength)`<br>Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified UCS4 code point position and extends the specified number of UCS4 code points.                                                                                |
    | `TypedExpression`           | `substrB``(TypedExpression position, TypedExpression substringLength)`<br>Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified byte position and extends the specified number of bytes.                                                                                                      |
    | `TypedExpression`           | `substrC``(TypedExpression position, TypedExpression substringLength)`<br>Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified Unicode complete character position and extends the specified number of Unicode complete characters.                                                          |
    | `TypedExpression`           | `sysContext``(TypedExpression namespace, TypedExpression parameter, TypedExpression length)`<br>Creates a `TypedExpression` that evaluates to the value of `parameter` that is associated with the context `namespace`.                                                                                                                                               |
    | `static TypedExpression`    | `sysDate``()`<br>Creates a `TypedExpression` that evaluates to the current date and time of the operating system on which the database resides.                                                                                                                                                                                                                       |
    | `TypedExpression`           | `sysExtractUTC``()`<br>Extracts the UTC (Coordinated Universal Time, which was formerly Greenwich Mean Time) from the datetime value of this `TypedExpression` with time zone offset or time zone region name.                                                                                                                                                        |
    | `static TypedExpression`    | `sysGUID``()`<br>Creates a `TypedExpression` that evaluates to a globally unique identifier (RAW value) made up of 16 bytes.                                                                                                                                                                                                                                          |
    | `static TypedExpression`    | `sysTimestamp``()`<br>Creates a `TypedExpression` that evaluates to the system date, including fractional seconds and time zone, of the system on which the database resides.                                                                                                                                                                                         |
    | `TypedExpression`           | `sysTypeID``()`<br>Creates a `TypedExpression` that evaluates to the the typeid of the most specific type of the operand.                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `tan``()`<br>Calculates the tangent of an angle expressed in radians.                                                                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `tanh``()`<br>Calculates the hyperbolic tangent of the value of this `TypedExpression`.                                                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `times``(double rhs)`<br>Multiplies the value of this `TypedExpression` by the specified `double` value.                                                                                                                                                                                                                                                              |
    | `TypedExpression`           | `times``(float rhs)`<br>Multiplies the value of this `TypedExpression` by the specified `float` value.                                                                                                                                                                                                                                                                |
    | `TypedExpression`           | `times``(int rhs)`<br>Multiplies the value of this `TypedExpression` by the specified `int` value.                                                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `times``(short rhs)`<br>Multiplies the value of this `TypedExpression` by the specified `short` value.                                                                                                                                                                                                                                                                |
    | `TypedExpression`           | `times``(TypedExpression rhs)`<br>Multiplies the value of this `TypedExpression` by the value of the specified `TypedExpression`.                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `timestampToSCN``()`<br>Creates a `TypedExpression` that evaluates to the approximate system change number (SCN) that is associated with the timestamp value of this `TypedExpression`.                                                                                                                                                                               |
    | `TypedExpression`           | `toBinaryDouble``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts to a `BINARY_DOUBLE` the character string or a numeric value of type `NUMBER` or `BINARY_FLOAT` of this `TypedExpression`.                                                                                                                                                              |
    | `TypedExpression`           | `toBinaryFloat``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts to a `BINARY_FLOAT` the character string or a numeric value of type `NUMBER` or `BINARY_DOUBLE` of this `TypedExpression`.                                                                                                                                                               |
    | `TypedExpression`           | `toChar``()`<br>Converts the `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB` value of this `TypedExpression` to the database character set.                                                                                                                                                                                                                                  |
    | `TypedExpression`           | `toChar``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts the value of this `TypedExpression` to a value in the specified format and NLS parameters.                                                                                                                                                                                                      |
    | `TypedExpression`           | `toCLOB``()`<br>Converts to a `CLOB` value the `NCLOB` in a LOB column or other character string value of this `TypedExpression`.                                                                                                                                                                                                                                     |
    | `TypedExpression`           | `toDate``()`<br>Converts the data type of the value of this `TypedExpression` to the `DATE` data type.                                                                                                                                                                                                                                                                |
    | `TypedExpression`           | `toDate``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts the data type of the value of this `TypedExpression` to the `DATE` data type in the format specified by the date format `fmt` and the language specified by `nlsparam`.                                                                                                                         |
    | `TypedExpression`           | `toDSInterval``(TypedExpression nlsparam)`<br>Converts the text expression of this `TypedExpression` to a `DS_INTERVAL` data type.                                                                                                                                                                                                                                    |
    | `TypedExpression`           | `toLOB``()`<br>Converts the value of this `TypedExpression` to a `LOB`.                                                                                                                                                                                                                                                                                               |
    | `TypedExpression`           | `toMultiByte``()`<br>Converts the single-byte characters of the value of this `TypedExpression` to the corresponding multibyte characters.                                                                                                                                                                                                                            |
    | `TypedExpression`           | `toNChar``()`<br>Converts the `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB` value of this `TypedExpression` to the national character set.                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `toNChar``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts the datetime or interval value of this `TypedExpression` from the database character set to the national character set in the format specified by the date format `fmt` and the language specified by `nlsparam`.                                                                              |
    | `TypedExpression`           | `toNCLOB``()`<br>Converts to an `NCLOB` value the `CLOB` in a LOB column or other character string value of this `TypedExpression`.                                                                                                                                                                                                                                   |
    | `TypedExpression`           | `toNumber``()`<br>Converts the value of this `TypedExpression` to the `NUMBER` data type.                                                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `toNumber``(TypedExpression fmt)`<br>Converts the value of this `TypedExpression` to the `NUMBER` data type in the format model specified by `fmt`.                                                                                                                                                                                                                   |
    | `TypedExpression`           | `toNumber``(TypedExpression fmt, TypedExpression nlsParam)`<br>Converts the value of this `TypedExpression` to the `NUMBER` data type in the format model specified by `fmt`.                                                                                                                                                                                         |
    | `TypedExpression`           | `toSingleByte``()`<br>Converts the multibyte characters of the value of this `TypedExpression` to the corresponding single-byte characters.                                                                                                                                                                                                                           |
    | `TypedExpression`           | `toTimestamp``(TypedExpression fmt, TypedExpression nlsparam)`<br>Converts the text expression of this `TypedExpression` to a `TIMESTAMP` data type.                                                                                                                                                                                                                  |
    | `TypedExpression`           | `toTimestampTZ``(TypedExpression fmt, TypedExpression nlsparam)`<br>Converts the text expression of this `TypedExpression` to a `TIMESTAMP_WITH_TIME_ZONE` data type.                                                                                                                                                                                                 |
    | `TypedExpression`           | `toYMInterval``()`<br>Converts the text expression of this `TypedExpression` to a `YM_INTERVAL` data type.                                                                                                                                                                                                                                                            |
    | `TypedExpression`           | `translate``(TypedExpression fromString, TypedExpression toString)`<br>Creates a `TypedExpression` that evaluates to an expression in which all occurrences of the specified characters in the value of this `TypedExpression` are replaced by the corresponding character in the value of the `toString` parameter.                                                  |
    | `TypedExpression`           | `translateUsingCharCS``()`<br>Converts the character string value of this `TypedExpression` into the database character set.                                                                                                                                                                                                                                          |
    | `TypedExpression`           | `translateUsingNCharCS``()`<br>Converts the character string value of this `TypedExpression` into the national character set.                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `treat``(java.lang.String typeName, boolean isRefType)`<br>Creates a `TypedExpression` that has the value of this `TypedExpression` but that has the type specified by `typeName`.                                                                                                                                                                                    |
    | `TypedExpression`           | `trim``(TypedExpression trimCharacter)`<br>Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified leading or trailing characters.                                                                                                                                                                                         |
    | `TypedExpression`           | `trimLeading``(TypedExpression trimCharacter)`<br>Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified leading character.                                                                                                                                                                                               |
    | `TypedExpression`           | `trimTrailing``(TypedExpression trimCharacter)`<br>Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified trailing character.                                                                                                                                                                                             |
    | `TypedExpression`           | `trunc``(TypedExpression fmt)`<br>Truncates the value of this `TypedExpression`.                                                                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `tzOffset``()`<br>Creates a `TypedExpression` that evaluates to the time zone offset from Coordinated Universal Time (UTC).                                                                                                                                                                                                                                           |
    | `static TypedExpression`    | `UID``()`<br>Creates a `TypedExpression` that evaluates to an integer that uniquely identifies the session user.                                                                                                                                                                                                                                                      |
    | `TypedExpression`           | `unistr``()`<br>Converts the value of this `TypedExpression` into the national character set.                                                                                                                                                                                                                                                                         |
    | `TypedExpression`           | `upper``()`<br>Converts to uppercase all alphabetic characters in the value of this `TypedExpression`.                                                                                                                                                                                                                                                                |
    | `static TypedExpression`    | `USER``()`<br>Creates a `TypedExpression` that evaluates to the name of the session user.                                                                                                                                                                                                                                                                             |
    | `TypedExpression`           | `userEnv``()`<br>Creates a `TypedExpression` that evaluates to information about the current session.                                                                                                                                                                                                                                                                 |
    | `TypedExpression`           | `vsize``()`<br>Creates a `TypedExpression` that evaluates to the number of bytes in the internal representation of the value of this `TypedExpression`.                                                                                                                                                                                                               |
    | `TypedExpression`           | `widthBucket``(TypedExpression minValue, TypedExpression maxValue, TypedExpression numBuckets)`<br>Constructs a histogram range that is divided into intervals of identical size.                                                                                                                                                                                     |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getDataType

          public final DataType getDataType()

      Gets the data type of this `TypedExpression`, which is represented by a `DataType` object.
      Returns:
      A `DataType` that represents the data type of the value to which this `TypedExpression` evaluates.

    <!-- -->

    - #### isNull

          public final Condition isNull()

      Creates a `Condition` that evaluates to `true` if the value of this `TypedExpression` is `null`.
      Returns:
      An `IsCondition` that evaluates to `true` if the value of the `TypedExpression` is `null`.

    <!-- -->

    - #### isNotNull

          public final Condition isNotNull()

      Creates a `Condition` that evaluates to `true` if the value of this `TypedExpression` is not `null`.
      Returns:
      An `IsCondition` that evaluates to `true` if the value of this `TypedExpression` is not `null`.

    <!-- -->

    - #### isInfinite

          public final Condition isInfinite(boolean negate)

      Indicates whether the value of this `TypedExpression` is the special value `INFINITE`. The `Condition` evaluates to `true` if value of this `TypedExpression` is the special value `INFINITE` and if the `negate` parameter is `false`. If the `negate` parameter is `true`, then the `Condition` evaluates to `true` if the value of this `TypedExpression` is not `INFINITE`.
      Parameters:
      `negate` - A `boolean` that reverses the evaluation of the value of the `TypedExpression`. If this parameter is `false`, then the `Condition` returned by this method is `true` if the value is `INFINITE`. If this parameter is `true`, then the `Condition` is `true` if the value is not `INFINITE`.

      Returns:
      An `IsCondition` that indicates whether the value of the `TypedExpression` is `INFINITE` or not `INFINITE`.

    <!-- -->

    - #### isNAN

          public final Condition isNAN(boolean negate)

      Indicates whether the value of this `TypedExpression` is the special value `NAN` (not a number). The `Condition` evaluates to `true` if the value is `NAN` and if the `negate` parameter is `false`. If the `negate` parameter is `true`, then the `Condition` evaluates to `true` if the value of this `TypedExpression` is not `NAN`.
      Parameters:
      `negate` - A `boolean` that reverses the evaluation of the value of the `TypedExpression`. If this parameter is `false`, then the `Condition` is `true` if the value is `NAN`. If this parameter is `true`, then the `Condition` is `true` if the value is not `NAN`.

      Returns:
      An `IsCondition` that indicates whether the value of the `TypedExpression` is `NAN` or not `NAN`.

    <!-- -->

    - #### between

          public final Condition between(TypedExpression start,
                                         TypedExpression end,
                                         boolean negate)

      Indicates whether the value of this `TypedExpression` is in the specified range of values. The `Condition` evaluates to `true` if the value is greater than or equal to the start expression and is less than or equal to the end expression and if the `negate` parameter is `false`. If the `negate` parameter is `true`, then the `Condition` evaluates to `true` if the value of this `TypedExpression` is not in the range.
      Parameters:
      `start` - A `TypedExpression` that has the value that is the start of the range.

      `end` - A `TypedExpression` that has the value that is the end of the range.

      `negate` - A `boolean` that reverses the evaluation of the value of the `TypedExpression`. If this parameter is `false`, then the `Condition` is `true` if the expression is in the range. If this parameter is `true`, then the `Condition` is `true` if the expression is not in the range.

      Returns:
      A `BetweenCondition` that indicates whether the value of the `TypedExpression` is in the specified range of values or is not in the specified range of values.

    <!-- -->

    - #### like

          public final Condition like(TypedExpression pattern)

      Indicates whether the specified text pattern occurs in the value of this `TypedExpression`. The pattern can contain wildcard characters. See [`LikeCondition`](LikeCondition.md) for the valid wildcard characters.
      Parameters:
      `pattern` - A `TypedExpression` that specifies the pattern to search for.

      Returns:
      A `LikeCondition` that evaluates to `true` if the text pattern is present in the value of this `TypedExpression`.

    <!-- -->

    - #### like

          public final Condition like(TypedExpression pattern,
                                      TypedExpression escape,
                                      boolean negate)

      Indicates whether the specified text pattern occurs in the value of this `TypedExpression`. The pattern can contain wildcard characters. See [`LikeCondition`](LikeCondition.md) for the valid wildcard characters.
      Parameters:
      `pattern` - A `TypedExpression` that specifies the pattern to search for.

      `escape` - A `TypedExpression` that has the text expression to use as the escape character.

      `negate` - A `boolean` that if `true` adds `NOT` to the `LIKE` operator or if `false` does not add `NOT` to the operator.

      Returns:
      A `LikeCondition` that indicates whether the text pattern is present or is not present in the value of this `TypedExpression`.

    <!-- -->

    - #### like2

          public final Condition like2(TypedExpression pattern,
                                       TypedExpression escape,
                                       boolean negate)

      Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests UCS2 code points and treats a Unicode supplementary character as one character. The pattern can contain wildcard characters. See [`LikeCondition`](LikeCondition.md) for the valid wildcard characters.
      Parameters:
      `pattern` - A `TypedExpression` that specifies the pattern to search for. The pattern can contain wildcard characters.

      `escape` - A `TypedExpression` that has the text expression to use as the escape character.

      `negate` - A `boolean` that if `true` adds `NOT` to the `LIKE` operator or if `false` does not add `NOT` to the operator.

      Returns:
      A `LikeCondition` that indicates whether the text pattern is present or is not present in the value of this `TypedExpression`.

    <!-- -->

    - #### like4

          public final Condition like4(TypedExpression pattern,
                                       TypedExpression escape,
                                       boolean negate)

      Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests UCS4 code points and treats a composite character as one character. The pattern can contain wildcard characters. See [`LikeCondition`](LikeCondition.md) for the valid wildcard characters.
      Parameters:
      `pattern` - A `TypedExpression` that specifies the pattern to search for. The pattern can contain wildcard characters.

      `escape` - A `TypedExpression` that has the text expression to use as the escape character.

      `negate` - A `boolean` that if `true` adds `NOT` to the `LIKE` operator or if `false` does not add `NOT` to the operator.

      Returns:
      A `LikeCondition` that indicates whether the text pattern is present or is not present in the value of this `TypedExpression`.

    <!-- -->

    - #### likeC

          public final Condition likeC(TypedExpression pattern,
                                       TypedExpression escape,
                                       boolean negate)

      Indicates whether the specified text pattern occurs in the value of this `TypedExpression`; the `Condition` tests Unicode complete characters and treats a Unicode supplementary character as two characters. The pattern can contain wildcard characters. See [`LikeCondition`](LikeCondition.md) for the valid wildcard characters.
      Parameters:
      `pattern` - A `TypedExpression` that specifies the pattern to search for. The pattern can contain wildcard characters.

      `escape` - A `TypedExpression` that has the text expression to use as the escape character.

      `negate` - A `boolean` that if `true` adds `NOT` to the `LIKE` operator or if `false` does not add `NOT` to the operator.

      Returns:
      A `LikeCondition` that indicates whether the text pattern is present or is not present in the value of this `TypedExpression`.

    <!-- -->

    - #### in

          public final Condition in(TypedExpression[] list)

      Indicates whether this `TypedExpression` occurs in the specified list of expressions.
      Parameters:
      `list` - An array of `TypedExpression` objects.

      Returns:
      A `ListComparisonCondition` that indicates whether this `TypedExpression` occurs in the list of expressions.

    <!-- -->

    - #### notIn

          public final Condition notIn(TypedExpression[] list)

      Indicates whether this `TypedExpression` does not occur in the specified list of expressions.
      Parameters:
      `list` - An array of `TypedExpression` objects.

      Returns:
      A `ListComparisonCondition` that indicates whether this `TypedExpression` does not occur in the list of expressions.

    <!-- -->

    - #### eq

          public final Condition eq(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is equal to the value of the specified `TypedExpression`. The `Condition` evaluates to `true` if the value of this `TypedExpression` equals the value of the specified `TypedExpression` or `false` if it does not.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` equals the value of the specified `TypedExpression`, or `false` if it does not.

    <!-- -->

    - #### eq

          public final Condition eq(double rhs)

      Indicates whether the value of this `TypedExpression` is equal to the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` equals the `double` value or `false` if it does not.

    <!-- -->

    - #### eq

          public final Condition eq(float rhs)

      Indicates whether the value of this `TypedExpression` is equal to the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` equals the `float` value or `false` if it does not.

    <!-- -->

    - #### eq

          public final Condition eq(int rhs)

      Indicates whether the value of this `TypedExpression` is equal to the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` equals the `int` value or `false` if it does not.

    <!-- -->

    - #### eq

          public final Condition eq(short rhs)

      Indicates whether the value of this `TypedExpression` is equal to the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` equals the `short` value or `false` if it does not.

    <!-- -->

    - #### ge

          public final Condition ge(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is greater than or equal to the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than or equal to the value of the specified `TypedExpression`, or `false` if it is not.

    <!-- -->

    - #### ge

          public final Condition ge(double rhs)

      Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than or equal to the `double`, or `false` if it is not.

    <!-- -->

    - #### ge

          public final Condition ge(float rhs)

      Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than or equal to the `float`, or `false` if it is not.

    <!-- -->

    - #### ge

          public final Condition ge(int rhs)

      Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than or equal to the `int`, or `false` if it is not.

    <!-- -->

    - #### ge

          public final Condition ge(short rhs)

      Indicates whether the value of this `TypedExpression` is greater than or equal to the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than or equal to the `short`, or `false` if it is not.

    <!-- -->

    - #### gt

          public final Condition gt(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is greater than the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than the value of the specified `TypedExpression`, or `false` if it is not.

    <!-- -->

    - #### gt

          public final Condition gt(double rhs)

      Indicates whether the value of this `TypedExpression` is greater than the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than the `double`, or `false` if it is not.

    <!-- -->

    - #### gt

          public final Condition gt(float rhs)

      Indicates whether the value of this `TypedExpression` is greater than the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than the `float`, or `false` if it is not.

    <!-- -->

    - #### gt

          public final Condition gt(int rhs)

      Indicates whether the value of this `TypedExpression` is greater than the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than the `int`, or `false` if it is not.

    <!-- -->

    - #### gt

          public final Condition gt(short rhs)

      Indicates whether the value of this `TypedExpression` is greater than the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is greater than the `short`, or `false` if it is not.

    <!-- -->

    - #### le

          public final Condition le(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is less than or equal to the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than or equal to the value of the specified `TypedExpression`, or `false` if it is not.

    <!-- -->

    - #### le

          public final Condition le(double rhs)

      Indicates whether the value of this `TypedExpression` is less than or equal to the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than or equal to the `double`, or `false` if it is not.

    <!-- -->

    - #### le

          public final Condition le(float rhs)

      Indicates whether the value of this `TypedExpression` is less than or equal to the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than or equal to the `float`, or `false` if it is not.

    <!-- -->

    - #### le

          public final Condition le(int rhs)

      Indicates whether the value of this `TypedExpression` is less than or equal to the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than or equal to the `int`, or `false` if it is not.

    <!-- -->

    - #### le

          public final Condition le(short rhs)

      Indicates whether the value of this `TypedExpression` is less than or equal to the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than or equal to the `short`, or `false` if it is not.

    <!-- -->

    - #### lt

          public final Condition lt(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is less than the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than the value of the specified `TypedExpression`, or `false` if it is not.

    <!-- -->

    - #### lt

          public final Condition lt(double rhs)

      Indicates whether the value of this `TypedExpression` is less than the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than the `double`, or `false` if it is not.

    <!-- -->

    - #### lt

          public final Condition lt(float rhs)

      Indicates whether the value of this `TypedExpression` is less than the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than the `float`, or `false` if it is not.

    <!-- -->

    - #### lt

          public final Condition lt(int rhs)

      Indicates whether the value of this `TypedExpression` is less than the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than the `int`, or `false` if it is not.

    <!-- -->

    - #### lt

          public final Condition lt(short rhs)

      Indicates whether the value of this `TypedExpression` is less than the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is less than the `short`, or `false` if it is not.

    <!-- -->

    - #### ne

          public final Condition ne(TypedExpression rhs)

      Indicates whether the value of this `TypedExpression` is not equal to the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` to compare to this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is not equal to the value of the specified `TypedExpression`, or `false` if it is.

    <!-- -->

    - #### ne

          public final Condition ne(double rhs)

      Indicates whether the value of this `TypedExpression` is not equal to the specified `double` value.
      Parameters:
      `rhs` - The `double` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is not equal to the `double` value or `false` if it is.

    <!-- -->

    - #### ne

          public final Condition ne(float rhs)

      Indicates whether the value of this `TypedExpression` is not equal to the specified `float` value.
      Parameters:
      `rhs` - The `float` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is not equal to the `float` value or `false` if it is.

    <!-- -->

    - #### ne

          public final Condition ne(int rhs)

      Indicates whether the value of this `TypedExpression` is not equal to the specified `int` value.
      Parameters:
      `rhs` - The `int` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is not equal to the `int` value or `false` if it is.

    <!-- -->

    - #### ne

          public final Condition ne(short rhs)

      Indicates whether the value of this `TypedExpression` is not equal to the specified `short` value.
      Parameters:
      `rhs` - The `short` to compare to the value of this `TypedExpression`.

      Returns:
      A `ValueComparisonCondition` that evaluates to `true` if the value of this `TypedExpression` is not equal to the `short` value or `false` if it is.

    <!-- -->

    - #### div

          public final TypedExpression div(double rhs)

      Divides the value of this `TypedExpression` by the specified `double` value.
      Parameters:
      `rhs` - The `double` value to use as the divisor.

      Returns:
      A `BinaryOperatorExpressionTypedExpression` that evaluates to the result of the division.

    <!-- -->

    - #### div

          public final TypedExpression div(float rhs)

      Divides the value of this `TypedExpression` by the specified `float` value.
      Parameters:
      `rhs` - The `float` value to use as the divisor.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the division.

    <!-- -->

    - #### div

          public final TypedExpression div(int rhs)

      Divides the value of this `TypedExpression` by the specified `int` value.
      Parameters:
      `rhs` - The `int` value to use as the divisor.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the division.

    <!-- -->

    - #### div

          public final TypedExpression div(TypedExpression rhs)

      Divides the value of this `TypedExpression` by the value of the specified `TypedExpression`.
      Parameters:
      `rhs` - A `TypedExpression` to use as the divisor.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the division.

    <!-- -->

    - #### div

          public final TypedExpression div(short rhs)

      Divides the value of this `TypedExpression` by the specified `short` value.
      Parameters:
      `rhs` - The `short` value to use as the divisor.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the division.

    <!-- -->

    - #### minus

          public final TypedExpression minus(double rhs)

      Subtracts the specified `double` value from the value of this `TypedExpression`.
      Parameters:
      `rhs` - The `double` value to subtract from the value of this `TypedExpression`.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the subtraction.

    <!-- -->

    - #### minus

          public final TypedExpression minus(float rhs)

      Subtracts the specified `float` value from the value of this `TypedExpression`.
      Parameters:
      `rhs` - The `float` value to subtract from the value of this `TypedExpression`.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the subtraction.

    <!-- -->

    - #### minus

          public final TypedExpression minus(int rhs)

      Subtracts the specified `int` value from the value of this `TypedExpression`.
      Parameters:
      `rhs` - The `int` value to subtract from the value of this `TypedExpression`.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the subtraction.

    <!-- -->

    - #### minus

          public final TypedExpression minus(TypedExpression rhs)

      Subtracts the value of the specified `TypedExpression` from the value of this `TypedExpression`.
      Parameters:
      `rhs` - The `TypedExpression` with the value to subtract from the value of this `TypedExpression`.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the subtraction.

    <!-- -->

    - #### minus

          public final TypedExpression minus(short rhs)

      Subtracts the specified `short` value from the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand - operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `short` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the subtraction.

    <!-- -->

    - #### minus

          public final TypedExpression minus()

      Negates the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `- operand`, where this `TypedExpression` is the operand.
      **Example:**

      In the following code the `numExpr` object has the value `-6`.

           NumberExpression numExpr = (NumberExpression)
                                      SyntaxObject.fromSyntax("-6", mp);
           TypedExpression minusOp = numExpr.minus();
           System.out.println("The syntax of minusOp is " + minusOp.toSyntax());

      The code produces the following output.
           - -6

      Returns:
      A `UnaryOperatorExpression` that evaluates to the negation of the value of this `TypedExpression`.

    <!-- -->

    - #### plus

          public final TypedExpression plus(double rhs)

      Adds the specified `double` value to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand + operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `double` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the addition.

    <!-- -->

    - #### plus

          public final TypedExpression plus(float rhs)

      Adds the specified `float` value to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand + operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `float` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the addition.

    <!-- -->

    - #### plus

          public final TypedExpression plus(int rhs)

      Adds the specified `int` value to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand + operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `int` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the addition.

    <!-- -->

    - #### plus

          public final TypedExpression plus(TypedExpression rhs)

      Adds the value of the specified `TypedExpression` to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand + operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `TypedExpression` that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the addition.

    <!-- -->

    - #### plus

          public final TypedExpression plus(short rhs)

      Adds the specified `short` value to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand + operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `short` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the addition.

    <!-- -->

    - #### times

          public final TypedExpression times(double rhs)

      Multiplies the value of this `TypedExpression` by the specified `double` value. The syntax of the `TypedExpression` returned by this method is `operand * operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `double` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the multiplication.

    <!-- -->

    - #### times

          public final TypedExpression times(float rhs)

      Multiplies the value of this `TypedExpression` by the specified `float` value. The syntax of the `TypedExpression` returned by this method is `operand * operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `float` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the multiplication.

    <!-- -->

    - #### times

          public final TypedExpression times(int rhs)

      Multiplies the value of this `TypedExpression` by the specified `int` value. The syntax of the `TypedExpression` returned by this method is `operand * operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `int` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the multiplication.

    <!-- -->

    - #### times

          public final TypedExpression times(TypedExpression rhs)

      Multiplies the value of this `TypedExpression` by the value of the specified `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `operand * operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `TypedExpression` that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the multiplication.

    <!-- -->

    - #### times

          public final TypedExpression times(short rhs)

      Multiplies the value of this `TypedExpression` by the specified `short` value. The syntax of the `TypedExpression` returned by this method is `operand * operand`, where this `TypedExpression` is the left-hand-side operand and the `rhs` parameter is the right-hand-side operand.
      Parameters:
      `rhs` - The `short` value that is the right-hand-side operand.

      Returns:
      A `BinaryOperatorExpression` that evaluates to the result of the multiplication.

    <!-- -->

    - #### abs

          public final TypedExpression abs()

      Calculates the absolute value of the numeric expression value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `ABS(n)`, where this `TypedExpression` has the numeric value `n`.
      Returns:
      A `RowFunctionExpression` that evaluates to the absolute value of this `TypedExpression`.

    <!-- -->

    - #### acos

          public final TypedExpression acos()

      Calculates the angle value in radians of the cosine value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `ACOS(n)`, where this `TypedExpression` has the value `n`, which is a numeric expression for the cosine in the range of -1 to 1.
      Returns:
      A `RowFunctionExpression` that evaluates to the angle value of the cosine.

    <!-- -->

    - #### asin

          public final TypedExpression asin()

      Calculates the angle value in radians of the specified sine. The syntax of the `TypedExpression` returned by this method is `ASIN(n)`, where this `TypedExpression` has the value `n`, which is a numeric expression in the range of -1 to 1 that contains the decimal value of the sine
      Returns:
      A `RowFunctionExpression` that evaluates to the angle value of the sine.

    <!-- -->

    - #### atan

          public final TypedExpression atan()

      Calculates the angle value in radians of the specified tangent. The syntax of the `TypedExpression` returned by this method is `ATAN(n)`, where this `TypedExpression` has the value `n`, which is a numeric expression that contains the decimal value of the tangent.
      To retrieve a full-range (0 - 2 *pi*) numeric value that indicates the arc tangent of a ratio, use the `atan2` method.

      Returns:
      A `RowFunctionExpression` that evaluates to of angle value of the tangent.

    <!-- -->

    - #### atan2

          public final TypedExpression atan2(TypedExpression rhs)

      Calculates the full-range (0 - 2 *pi*) numeric value that indicates the arc tangent of the specified ratio. The syntax of the `TypedExpression` returned by this method is `ATAN2(n1, n2)`.
      This `TypedExpression` is `n1`, which is a numeric expression that contains left-hand-side component of the ratio. The `rhs` parameter specifies the right-hand-side component of the ratio.

      The SQL `ATAN2` function returns values in the range of -*pi* to *pi*, depending on the signs of the arguments. The values are expressed in radians. use the `atan` method.

      Returns:
      A `RowFunctionExpression` that evaluates to of the arc tangent of the ratio.

    <!-- -->

    - #### bitAnd

          public final TypedExpression bitAnd(TypedExpression rhs)

      Computes a bitwise `AND` operation on the bits of two nonnegative integers. The syntax of the `TypedExpression` returned by this method is `BITAND(expr1, expr2)`. This `TypedExpression` is `expr1` and the `rhs` parameter is `expr2`.
      This `TypedExpression` returned by this method is commonly used as a parameter to the `decode` method.

      Parameters:
      `rhs` - The `TypedExpression` that is the `expr2` argument for the `BITAND` operation.

      Returns:
      A `RowFunctionExpression` that evaluates to the result of a bitwise `AND` operation on the value of this `TypedExpression` and `rhs`.

    <!-- -->

    - #### ceil

          public final TypedExpression ceil()

      Calculates the smallest integer that is greater than or equal to the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `CEIL(n)`, where *n* is the value of this `TypedExpression`.
      **Example:**

      The following code produces the `TypedExpression` `ceilExpr`. The `numExpr` object has the value `3.14159265359`.

           NumberExpression numExpr = (NumberExpression)
                                      SyntaxObject.fromSyntax("3.14159265359", mp);
           TypedExpression ceilExpr = numExpr.ceil();
           System.out.println("The syntax of ceilExpr is " + ceilExpr.toSyntax());

      The code produces the following output.
           CEIL(3.1415927)

      The `ceilExpr` `TypedExpression` evaluates to `4`.
      Returns:
      A `RowFunctionExpression` that evaluates to the smallest integer that is greater than or equal to the value of this `TypedExpression`.

    <!-- -->

    - #### cos

          public final TypedExpression cos()

      Calculates the cosine of the value (interpreted as an angle value in radians) of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `COSH(n)`, where *n* is the value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the cosine of the value of this `TypedExpression`.

    <!-- -->

    - #### cosh

          public final TypedExpression cosh()

      Calculates the hyperbolic cosine of the value (interpreted as an angle value in radians) of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `COSH(n)`, where `n` is the value of of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to of the hyperbolic cosine of the value this `TypedExpression`.

    <!-- -->

    - #### exp

          public final TypedExpression exp()

      Calculates the value of 2.71828183 raised to the power of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `EXP(n)`, where *n* is the value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the exponential value of 2.71828183 with the value of this `TypedExpression` as the exponent.

    <!-- -->

    - #### floor

          public final TypedExpression floor()

      Calculates the largest integer that is equal to or less than the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `FLOOR(n)`, where *n* is the value of this `TypedExpression`.
      **Example:**

      The following code produces the `TypedExpression` `floorExpr`. The `numExpr` object has the value `15.7`.

           NumberExpression numExpr = (NumberExpression)
                                      SyntaxObject.fromSyntax("15.7", mp);
           TypedExpression floorExpr = numExpr.floor();
           System.out.println("The syntax of floorExpr is " + floorExpr.toSyntax());

      The code produces the following output.
           FLOOR(15.7)

      The `floorExpr` `TypedExpression` evaluates to `15`.
      Returns:
      A `RowFunctionExpression` that evaluates to the largest integer that is equal to or less than the value of this `TypedExpression`.

    <!-- -->

    - #### ln

          public final TypedExpression ln()

      Calculates the natural logarithm of the value of this `TypedExpression`. The value of this `TypedExpression` must be greater than 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `LN(n)`, where *n* is the value of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the natural logarithm of the value of this `TypedExpression`.

    <!-- -->

    - #### log

          public final TypedExpression log(TypedExpression n1)

      Calculates the logarithm of the value of the specified `TypedExpression` where the value of this `TypedExpression` is the base. The value of this `TypedExpression` can be any positive numeric value.
      The syntax of the `TypedExpression` returned by this method is `LOG(n2, n1)`, where *n2* is the value of this `TypedExpression` and *n1* is the value of the `n1` parameter.

      **Example:**

      The following code produces the `TypedExpression` `logExpr`.

           NumberExpression n1 = (NumberExpression) SyntaxObject.fromSyntax("100", mp);
           NumberExpression n2 = (NumberExpression) SyntaxObject.fromSyntax("10", mp);
           TypedExpression logExpr = n2.log(n1);
           System.out.println("The syntax of logExpr is " + logExpr.toSyntax());

      The code produces the following output.
           LOG(10, 100)

      The `logExpr` `TypedExpression` evaluates to `2`.
      Parameters:
      `n1` - A `TypedExpression` that has a positive numeric value other than 0 or 1.

      Returns:
      A `RowFunctionExpression` that evaluates to the logarithm base `n2` of `n1`.

    <!-- -->

    - #### mod

          public final TypedExpression mod(TypedExpression n1)

      Calculates the remainder of the value of this `TypedExpression` divided by the value of the specified `TypedExpression`. If the divisor is 0 (zero), then the `TypedExpression` returned by this method has the same value as this `TypedExpression`.
      The syntax of the `TypedExpression` is `MOD(n2, n1)`, where *n2* is the value of this `TypedExpression` and *n1* is the value of the `n1` parameter.

      Parameters:
      `n1` - A `TypedExpression` that has a numeric value that is the divisor.

      Returns:
      A `RowFunctionExpression` that evaluates to the remainder of the value of this `TypedExpression` divided by the value of `n1`.

    <!-- -->

    - #### nanvl

          public final TypedExpression nanvl(TypedExpression n1)

      Replaces the value of this `TypedExpression` with the value of the specified `TypedExpression` if the value of this `TypedExpression` is the special value `NAN` (not a number). If the value of this `TypedExpression` is not `NAN`, then the `TypedExpression` returned by this method has the same value as this `TypedExpression`. This method is useful for mapping `NAN` values to `null`.
      The syntax of the `TypedExpression` is `NANVL(n2, n1)`, where *n2* is the value of this `TypedExpression` and *n1* is the value of the `n1` parameter.

      Parameters:
      `n1` - A `TypedExpression` that has the value to substitute for the value of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of the `n1` `TypedExpression` or the value of this `TypedExpression`.

    <!-- -->

    - #### power

          public final TypedExpression power(TypedExpression rhs)

      Raises the value of this `TypedExpression` to the power of the value of the specified `TypedExpression`. The syntax of the `TypedExpression` is `POWER(n2, n1)`, where *n2* is the value of this `TypedExpression` and *n1* is the value of the `rhs` parameter.
      **Example:**

      The following code produces the `TypedExpression` `powerExpr`.

           NumberExpression n1 = (NumberExpression) SyntaxObject.fromSyntax("3", mp);
           NumberExpression rhs = (NumberExpression) SyntaxObject.fromSyntax("2", mp);
           TypedExpression powerExpr = n1.power(rhs);
           System.out.println("The syntax of powerExpr is " + powerExpr.toSyntax());

      The code produces the following output.
           POWER(3, 2)

      The `powerExpr` `TypedExpression` evaluates to `9`.
      Parameters:
      `rhs` - A `TypedExpression` that has a numeric value that is the power.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` raised to the power of the value of the `rhs` parameter.

    <!-- -->

    - #### remainder

          public final TypedExpression remainder(TypedExpression rhs)

      Divides the value of this `TypedExpression` by the value of the specified `TypedExpression` and calculates the rounded remainder. Oracle OLAP determines the remainder by using the formula `n2 - (n1 * N)`, where *N* is the integer nearest `n2/n1`.
      The syntax of the `TypedExpression` is `REMAINDER(n2, n1)`, where *n2* is the value of this `TypedExpression` and *n1* is the value of the `rhs` parameter.

      **Example:**

      The following code produces the `TypedExpression` `remainderExpr`.

           NumberExpression n1 = (NumberExpression) SyntaxObject.fromSyntax("18", mp);
           NumberExpression rhs = (NumberExpression) SyntaxObject.fromSyntax("7", mp);
           TypedExpression remainderExpr = n1.remainder(rhs);
           System.out.println("The syntax of remainderExpr is " + remainderExpr.toSyntax());

      The code produces the following output.
           REMAINDER(18, 7)

      The `remainderExpr` `TypedExpression` evaluates to `-3`.
      Parameters:
      `rhs` - A `TypedExpression` that has a numeric value that is the divisor.

      Returns:
      A `RowFunctionExpression` that evaluates to the rounded remainder of the division of the value of this `TypedExpression` by the value of the `rhs` parameter.

    <!-- -->

    - #### round

          public final TypedExpression round(TypedExpression precision)

      Rounds the value of this `TypedExpression` to the precision specified. The syntax of the `TypedExpression` returned by this method depends on the data type of this `TypedExpression`.
      If the data type of this `TypedExpression` is `NUMBER`, then the syntax is `ROUND(n, integer)`, where *n* is the value of this `TypedExpression` and *integer* is the value of the `precision` parameter. The `precision` parameter must be a `TypedExpression` with a numeric value. A positive number specifies rounding on the right side of the decimal point. A negative number specifies rounding on the left side of the decimal point.

      If the data type of this `TypedExpression` is `DATE`, then the syntax is `ROUND(exp, fmt)`, where *exp* is the value of this `TypedExpression` and *fmt* is the value of the `precision` parameter. The `precision` parameter must be a `TypedExpression` with a character value in a format model such as `'YYYY'` or `'MON'`. For a list of the valid format models, see [Formats for the Input Parameter for the round and trunc Methods](doc-files/rndtrncfmt.md).

      For examples of the `round` method, see [Examples for round](doc-files/rowfuncsyntax.md).

      Parameters:
      `precision` - For rounding a number, a `TypedExpression` that has an integer value. For rounding a date, a `TypedExpression` that has an character value that specifies a format model.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` rounded to the precision specified by the value of the `precision` parameter.

    <!-- -->

    - #### sign

          public final TypedExpression sign()

      Determines whether a number is less than, equal to, or greater than 0 (zero). The syntax of the `TypedExpression` is `SIGN(n)`, where *n* is the numeric value of this `TypedExpression`.
      The `TypedExpression` returned by this method evaluates to the following:

      - `-1` if *n* \< 0
      - ` 0` if *n* = 0
      - ` 1` if *n* \> 0

      **Example:**

           TypedExpression n = (TypedExpression) SyntaxObject.fromSyntax(-15);
           TypedExpression signExpr = n.sign();
           System.out.println("The syntax of signExpr is " + signExpr.toSyntax());

      The code produces the following output.
           The syntax of signExpr is SIGN(-15)

      The `signExpr` `TypedExpression` evaluates to `-1`.
      Returns:
      A `RowFunctionExpression` that indicates the sign of this `TypedExpression`.

    <!-- -->

    - #### sin

          public final TypedExpression sin()

      Calculates the sine of an angle expressed in radians. The syntax of the `TypedExpression` returned by this method is `SIN(n)`, where *n* is the numeric value, in radians, of this `TypedExpression`.
      **Example:**

      This example produces a `TypedExpression` that calculates the sine of a 30 degree angle.

           TypedExpression n = (TypedExpression)
                                 SyntaxObject.fromSyntax("30 * 3.14159265359/180", mp);
           // The syntax of n is an expression that converts 30 into radians.
           TypedExpression sinExpr = n.sin();
           System.out.println("The syntax of sinExpr is " + sinExpr.toSyntax());

      The code produces the following output.
           The syntax of sinExpr is SIN(30 * 3.1415927 / 180)

      The `sinExpr` `TypedExpression` evaluates to `.5`.
      Returns:
      A `RowFunctionExpression` that evaluates to the sine of this `TypedExpression`.

    <!-- -->

    - #### sinh

          public final TypedExpression sinh()

      Calculates the hyperbolic sine of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `SINH(n)`, where *n* is the numeric value of this `TypedExpression`.
      **Example:**

           TypedExpression n = (TypedExpression) SyntaxObject.fromSyntax("1", mp);
           TypedExpression sinhExpr = n.sinh();
           System.out.println("The syntax of sinhExpr is " + sinhExpr.toSyntax());

      The code produces the following output.
           The syntax of sinhExpr is SINH(1)

      The `sinhExpr` `TypedExpression` evaluates to `1.18`.
      Returns:
      A `RowFunctionExpression` that evaluates to the hyperbolic sine of this `TypedExpression`.

    <!-- -->

    - #### sqrt

          public final TypedExpression sqrt()

      Calculates the square root of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `SQRT(n)`, where *n* is the numeric value of this `TypedExpression`.
      **Example:**

           TypedExpression n = (TypedExpression) SyntaxObject.fromSyntax("13", mp);
           TypedExpression sqrtExpr = n.sqrt();
           System.out.println("The syntax of sqrtExpr is " + sqrtExpr.toSyntax());

      The code produces the following output.
           The syntax of sqrtExpr is SQRT(13)

      The `sqrtExpr` `TypedExpression` evaluates to `3.60555128`.
      Returns:
      A `RowFunctionExpression` that evaluates to the square root of this `TypedExpression`.

    <!-- -->

    - #### tan

          public final TypedExpression tan()

      Calculates the tangent of an angle expressed in radians. The syntax of the `TypedExpression` returned by this method is `TAN(n)`, where *n* is the numeric value, in radians, of this `TypedExpression`.
      **Example:**

      This example produces a `TypedExpression` that calculates the tangent of a 135 degree angle.

           TypedExpression n = (TypedExpression)
                                SyntaxObject.fromSyntax("135 * 3.14159265359/180", mp);
           // The syntax of n is an expression that converts 135 into radians.
           TypedExpression tanExpr = n.sin();
           System.out.println("The syntax of tanExpr is " + tanExpr.toSyntax());

      The code produces the following output.
           The syntax of sinExpr is TAN(135 * 3.1415927 / 180)

      The `tanExpr` `TypedExpression` evaluates to `-1`.
      Returns:
      A `RowFunctionExpression` that evaluates to the tangent of this `TypedExpression`.

    <!-- -->

    - #### tanh

          public final TypedExpression tanh()

      Calculates the hyperbolic tangent of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `TANH(n)`, where *n* is the numeric value of this `TypedExpression`.
      **Example:**

           TypedExpression n = (TypedExpression) SyntaxObject.fromSyntax(".5", mp);
           TypedExpression tanhExpr = n.tanh();
           System.out.println("The syntax of tanhExpr is " + tanhExpr.toSyntax());

      The code produces the following output.
           The syntax of tanhExpr is TANH(.5)

      The `tanhExpr` `TypedExpression` evaluates to `.46`.
      Returns:
      A `RowFunctionExpression` that evaluates to the hyperbolic tangent of this `TypedExpression`.

    <!-- -->

    - #### trunc

          public final TypedExpression trunc(TypedExpression fmt)

      Truncates the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `TRUNC(exp [, fmt])`, where *exp* is the numeric or date expression of this `TypedExpression` and *fmt* is an optional argument.
      Valid values for *fmt* depend on the data type of this `TypedExpression`. If the data type is `NUMBER`, then *fmt* must be a numeric expression that specifies the number of decimal places by which to truncate the value of this `TypedExpression`. A positive number specifies truncating on the right side of the decimal point. A negative number specifies truncating on the left side of the decimal point, which replaces numbers to the left of the decimal point with 0 (zero). If *fmt* is 0, then the result is truncated to 0 decimal places.

      If the data type is `DATE`, then *fmt* must be a a text expression in the date format model, such as `YYYY` or `MON`. For a list of the valid date format models, see [Formats for the Input Parameter for the round and trunc Methods](doc-files/rndtrncfmt.md).

      For examples of the `trunc` method, see [Example for trunc](doc-files/rowfuncsyntax.md).

      Parameters:
      `fmt` - For truncating a number, a `TypedExpression` that has an numeric value. For truncating a date, a `TypedExpression` that has a textual value that specifies a date format model.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` truncated as specified by the `fmt` parameter.

    <!-- -->

    - #### widthBucket

          public final TypedExpression widthBucket(TypedExpression minValue,
                                                   TypedExpression maxValue,
                                                   TypedExpression numBuckets)

      Constructs a histogram range that is divided into intervals of identical size. The `TypedExpression` returned by this method evaluates to the bucket number into which the value of this `TypedExpression` falls. The `TypedExpression` returned by this method has the syntax `WIDTH_BUCKET(expr, min_value, max_value, num_buckets)`, where *expr* is the numeric expression of this `TypedExpression` and the other arguments are the parameters of this method.
      The expression of this `TypedExpression` is the expression for which the histogram is being created. This expression must evaluate to a numeric or datetime value or to a value. If this `TypedExpression` evaluates to `null`, then the `TypedExpression` returned by this method evaluates to `null`.

      When needed, the `WIDTH_BUCKET` expression creates an underflow bucket numbered 0 and an overflow bucket numbered *num_buckets*+1. These buckets handle values outside the specified range and are helpful in checking the reasonableness of the end points.

      The `minValue` and `maxValue` parameters are `TypedExpression` objects that evaluate to the end points of the acceptable range for the value of this `TypedExpression`. Both of these expressions must evaluate to numeric or datetime values, and neither can evaluate to `null`.

      For an example of `widthBucket`, see [Example for widthBucket](doc-files/rowfuncsyntax.md).

      Parameters:
      `minValue` - A `TypedExpression` that evaluates to the beginning of the range for the value of this `TypedExpression`.

      `maxValue` - A `TypedExpression` that evaluates to the end of the range for the value of this `TypedExpression`.

      `numBuckets` - A `TypedExpression` that evaluates to the number of buckets. This expression must evaluate to a positive integer.

      Returns:
      A `RowFunctionExpression` that evaluates to the bucket number into which the value of this `TypedExpression` falls.

    <!-- -->

    - #### ascii

          public final TypedExpression ascii()

      Creates a `TypedExpression` that evaluates to the ASCII decimal representation of the first character of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `ASCII(char)` where *char* is this `TypedExpression`, which is a text expression of data type `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`.
      For an example of `ascii`, see [Example for ascii](doc-files/rowfuncsyntax.md).

      Returns:
      A `RowFunctionExpression` that evaluates to the ASCII decimal representation of the first character of the value of this `TypedExpression`.

    <!-- -->

    - #### chr

          public final TypedExpression chr()

      Converts the integer value of this `TypedExpression` to the character in the database character set with the binary equivalent of the integer. The syntax of the `TypedExpression` returned by this method is `CHR(n)` where *n* is the value of this `TypedExpression`.
      For single-byte character sets, if *n* is greater than 256, then the `TypedExpression` returned by this method evaluates to the binary equivalent of *n* divided by 256. For multibyte character sets, *n* must evaluate to one entire numeric code, also known as a code point. Oracle OLAP does not validate code points, and the result of specifying an invalid code point is indeterminate.

      For an example of `chr`, see [Example for chr](doc-files/rowfuncsyntax.md).

      Returns:
      A `RowFunctionExpression` that evaluates to the character with the binary equivalent of the integer value of this `TypedExpression`.

    <!-- -->

    - #### chr

          public final TypedExpression chr(boolean usingNChar)

      Converts the integer value of this `TypedExpression` to the character in the national character set with the binary equivalent of the integer. The syntax of the `TypedExpression` returned by this method is `CHR(n USING NCHAR_CS)` where *n* is the value of this `TypedExpression`.
      For single-byte character sets, if *n* is greater than 256, then the `TypedExpression` returned by this method evaluates to the binary equivalent of *n* divided by 256. For multibyte character sets, *n* must evaluate to one entire numeric code. Oracle OLAP does not validate the numeric code, and the result of specifying an invalid code is indeterminate.

      For an example of `chr`, see [Example for chr](doc-files/rowfuncsyntax.md).

      Parameters:
      `usingNChar` - A `boolean` that specifies whether to use the national character set.

      Returns:
      A `RowFunctionExpression` that evaluates to the character with the binary equivalent of the integer value of this `TypedExpression`.

    <!-- -->

    - #### concat

          public final TypedExpression concat(java.lang.String rhs)

      Concatentates two text expressions as a single character string. The syntax of the `TypedExpression` returned by this method is `CONCAT(char1, char2)` where *char1* is the value of this `TypedExpression` and *char2* is the value of the `rhs` parameter.
      The data types of the expressions of this `TypedExpression` and the `rhs` `TypedExpression` can be text expressions in any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB`.

      For examples of `concat`, see [Example for concat](doc-files/rowfuncsyntax.md).

      Parameters:
      `rhs` - A `String` that has the value to concatenate with this `TypedExpression`.

      Returns:
      A `StringExpression` that evaluates to text that contains the values of this `TypedExpression` and the `rhs` parameter.

    <!-- -->

    - #### concat

          public final TypedExpression concat(TypedExpression rhs)

      Concatenates two text expressions as a single character string. The syntax of the `TypedExpression` returned by this method is `CONCAT(char1, char2)` where *char1* is the value of this `TypedExpression` and *char2* is the value of the `rhs` parameter.
      The data types of the expressions of this `TypedExpression` and the `rhs` `TypedExpression` can be text expressions in any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB`.

      For examples of `concat`, see [Example for concat](doc-files/rowfuncsyntax.md).

      Parameters:
      `rhs` - A `TypedExpression` that has the value to concatenate with this `TypedExpression`.

      Returns:
      A `BinaryOperatorExpression` that evaluates to text that contains the values of this `TypedExpression` and the `rhs` parameter.

    <!-- -->

    - #### initcap

          public final TypedExpression initcap()

      Converts the first letter of each word of this `TypedExpression` to uppercase and all other letters to lowercase. Words are delimited by white space or non-alphanumeric characters.
      The syntax of the `TypedExpression` returned by this method is `INITCAP(char)` where *char* is the value of this `TypedExpression`. The data type of the value of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`.

      For an example of `initcap`, see [Example for initcap](doc-files/rowfuncsyntax.md).

      Returns:
      A `RowFunctionExpression` that evaluates to text that contains the text of this `TypedExpression` with the first letter of each word in uppercase and all other letters in lowercase.

    <!-- -->

    - #### instr

          public final TypedExpression instr(TypedExpression substring,
                                             TypedExpression position,
                                             TypedExpression occurrence)

      Searches the value of this `TypedExpression` for the characters of the specified substring. The `TypedExpression` returned by this method evaluates to an integer that indicates the position of the first character of the substring in the value of this `TypedExpression` that matches the specified substring. If no match occurs, then it evaluates to 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `INSTR(string, substring, position, occurrence)` where *string* is the value of this `TypedExpression` and the other arguments are the parameters of this method. The `INSTR` expression calculates strings using characters as defined by the input character set. The `INSTRB` expression uses bytes instead of characters. `INSTRC` uses Unicode complete characters. `INSTR2` uses UCS2 code points. `INSTR4` uses UCS4 code points. To create one of those expressions, use the `instrB`, `instrC`, `instr2`, or `instr4` method, respectively.

      Parameters:
      `substring` - A `TypedExpression` that has the string to match.

      `position` - A `TypedExpression` that has a nonzero integer indicating the position in the string of this `TypedExpression` at which to begin the search. A negative `position` value specifies a position count and search backward from the end of the string.

      `occurrence` - A `TypedExpression` that has a positive integer that indicates which occurrence of the substring to search for.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that indicates the position of the first character of this string that matches the specified substring or 0 (zero) if no match occurs.

      See Also:
      `regexpInstr`

    <!-- -->

    - #### instrB

          public final TypedExpression instrB(TypedExpression substring,
                                              TypedExpression position,
                                              TypedExpression occurrence)

      Searches the value of this `TypedExpression` for the bytes of the specified substring. The `TypedExpression` returned by this method evaluates to an integer that indicates the position of the first byte of the string in the value of this `TypedExpression` that matches the substring. If no match occurs, then it evaluates to 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `INSTRB(string, substring, position, occurrence)` where *string* is the value of this `TypedExpression` and the other arguments are the parameters of this method.

      Parameters:
      `substring` - A `TypedExpression` that has the string to match.

      `position` - A `TypedExpression` that has a nonzero integer indicating the position in the string of this `TypedExpression` at which to begin the search. A negative `position` value specifies a position count and search backward from the end of the string.

      `occurrence` - A `TypedExpression` that has a positive integer that indicates which occurrence of the substring to search for.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that indicates the position of the first byte of this string that matches the specified substring or 0 (zero) if no match occurs.

      See Also:
      `instr`

    <!-- -->

    - #### instrC

          public final TypedExpression instrC(TypedExpression substring,
                                              TypedExpression position,
                                              TypedExpression occurrence)

      Searches the value of this `TypedExpression` for the Unicode complete characters of the specified substring. The `TypedExpression` returned by this method evaluates to an integer that indicates the position of the first Unicode character in the string in the value of this `TypedExpression` that matches the substring. If no match occurs, then it evaluates to 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `INSTRC(string, substring, position, occurrence)` where *string* is the value of this `TypedExpression` and the other arguments are the parameters of this method.

      Parameters:
      `substring` - A `TypedExpression` that has the string to match.

      `position` - A `TypedExpression` that has a nonzero integer indicating the position in the string of this `TypedExpression` at which to begin the search. A negative `position` value specifies a position count and search backward from the end of the string.

      `occurrence` - A `TypedExpression` that has a positive integer that indicates which occurrence of the substring to search for.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that indicates the position of the first Unicode character of this string that matches the specified substring or 0 (zero) if no match occurs.

      See Also:
      `instr`

    <!-- -->

    - #### instr2

          public final TypedExpression instr2(TypedExpression substring,
                                              TypedExpression position,
                                              TypedExpression occurrence)

      Searches the value of this `TypedExpression` for the UCS2 code points of the specified substring. The `TypedExpression` returned by this method evaluates to an integer that indicates the position of the first UCS2 code point in the string in the value of this `TypedExpression` that matches the substring. If no match occurs, then it evaluates to 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `INSTR2(string, substring, position, occurrence)` where *string* is the value of this `TypedExpression` and the other arguments are the parameters of this method.

      Parameters:
      `substring` - A `TypedExpression` that has the string to match.

      `position` - A `TypedExpression` that has a nonzero integer indicating the position in the string of this `TypedExpression` at which to begin the search. A negative `position` value specifies a position count and search backward from the end of the string.

      `occurrence` - A `TypedExpression` that has a positive integer that indicates which occurrence of the substring to search for.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that indicates the position of the first UCS2 code point of this string that matches the specified substring or 0 (zero) if no match occurs.

      See Also:
      `instr`

    <!-- -->

    - #### instr4

          public final TypedExpression instr4(TypedExpression substring,
                                              TypedExpression position,
                                              TypedExpression occurrence)

      Searches the value of this `TypedExpression` for the UCS4 code points of the specified substring. The `TypedExpression` returned by this method evaluates to an integer that indicates the position of the first UCS4 code point in the string in the value of this `TypedExpression` that matches the substring. If no match occurs, then it evaluates to 0 (zero).
      The syntax of the `TypedExpression` returned by this method is `INSTR4(string, substring, position, occurrence)` where *string* is the value of this `TypedExpression` and the other arguments are the parameters of this method.

      Parameters:
      `substring` - A `TypedExpression` that has the string to match.

      `position` - A `TypedExpression` that has a nonzero integer indicating the position in the string of this `TypedExpression` at which to begin the search. A negative `position` value specifies a position count and search backward from the end of the string.

      `occurrence` - A `TypedExpression` that has a positive integer that indicates which occurrence of the substring to search for.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that indicates the position of the first UCS4 code point of this string that matches the specified substring or 0 (zero) if no match occurs.

      See Also:
      `instr`

    <!-- -->

    - #### length

          public final TypedExpression length()

      Counts the number of characters in the text expression of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LENGTH(char)` where *char* is the value of this `TypedExpression`.
      The `LENGTH` expression calculates characters as defined by the input character set. The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`. If the data type is `CHAR`, then the length includes all trailing blanks. If this expression is null, then the `TypedExpression` returned by this method evaluates to `null`.

      The `LENGTHB` expression uses bytes instead of characters. `LENGTHC` uses Unicode complete characters. `LENGTH2` uses UCS2 code points. `LENGTH4` uses UCS4 code points. To create one of those expressions, use the `lengthB`, `lengthC`, `length2`, or `length4` method, respectively.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that is the number of characters in this text expression.

    <!-- -->

    - #### lengthB

          public final TypedExpression lengthB()

      Counts the number of bytes in the text expression of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LENGTHB(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`. If the data type is `CHAR`, then the length includes all trailing blanks. If this expression is null, then the `TypedExpression` returned by this method evaluates to `null`.

      Use the `LENGTHB` expression only for single-byte LOBs. Do not use it with `CLOB` and `NCLOB` data in a multibyte character set.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that is the number of bytes in this text expression.

      See Also:
      `length`

    <!-- -->

    - #### lengthC

          public final TypedExpression lengthC()

      Counts the number of Unicode characters in the text expression of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LENGTHC(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`. If the data type is `CHAR`, then the length includes all trailing blanks. If this expression is null, then the `TypedExpression` returned by this method evaluates to `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that is the number of Unicode characters in this text expression.

      See Also:
      `length`

    <!-- -->

    - #### length2

          public final TypedExpression length2()

      Counts the number of UCS2 code points in the text expression of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LENGTH2(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`. If the data type is `CHAR`, then the length includes all trailing blanks. If this expression is null, then the `TypedExpression` returned by this method evaluates to `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that is the number of UCS2 code points in this text expression.

      See Also:
      `length`

    <!-- -->

    - #### length4

          public final TypedExpression length4()

      Counts the number of UC42 code points in the text expression of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LENGTH4(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`. If the data type is `CHAR`, then the length includes all trailing blanks. If this expression is null, then the `TypedExpression` returned by this method evaluates to `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to an integer that is the number of UCS4 code points in this text expression.

      See Also:
      `length`

    <!-- -->

    - #### lower

          public final TypedExpression lower()

      Converts to lowercase all alphabetic characters in the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LOWER(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which all alphabetic characters are lowercase.

    <!-- -->

    - #### lpad

          public final TypedExpression lpad(TypedExpression n,
                                            TypedExpression expr2)

      Adds the specified number of characters to the left of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `LPAD(expr1, n, expr2)` where *expr1* is the value of this `TypedExpression` and the other arguments are the parameters of this method.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Parameters:
      `n` - A `TypedExpression` that has a number that specifies the total length of value of the `TypedExpression` returned by this method. If the value of this `TypedExpression` is longer than `n`, then the `LPAD` expression truncates the value of the returned `TypedExpression` to `n` characters.

      `expr2` - A `TypedExpression` that has a text expression for the padding characters. By default, the padding character is a space.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which text expression of this `TypedExpression` is padded to the left with the specified number of padding characters.

    <!-- -->

    - #### ltrim

          public final TypedExpression ltrim(TypedExpression set)

      Searches the value of this `TypedExpression`, starting from the left, and removes all of the characters that match the characters in the trim expression `set`, until an unmatched character occurs. The syntax of the `TypedExpression` returned by this method is `LTRIM(char, set)` where *char* is the value of this `TypedExpression` and *set* is the `set` parameter.
      Parameters:
      `set` - A `TypedExpression` that has a text expression with the characters to remove. The default value of `set` is a single blank.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression with the specified characters trimmed from the left.

    <!-- -->

    - #### nlsInitcap

          public final TypedExpression nlsInitcap(TypedExpression nlsparam)

      Converts the first letter of each word of this `TypedExpression` to uppercase and all other letters to lowercase. Words are delimited by white space or non-alphanumeric characters.
      The syntax of the `TypedExpression` returned by this method is `NLS_INITCAP(char, nlsparam)` where *char* is the value of this `TypedExpression` and *nlsparam* is the `nlsparam` parameter. . The data type of the value of this `TypedExpression` and the `nlsparam` `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`.

      Parameters:
      `nlsparam` - A `TypedExpression` that has a linguistic sort sequence in the form `NLS_SORT = sort[_ai |_ci]`, where *sort* is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort. For more information about linguistic sorting, refer to *Oracle Database Globalization Support Guide*.

      Returns:
      A `RowFunctionExpression` that evaluates to text that contains the text of this `TypedExpression` with the first letter of each word in uppercase and all other letters in lowercase.

    <!-- -->

    - #### nlsLower

          public final TypedExpression nlsLower(TypedExpression nlsparam)

      Converts to lowercase all alphabetic characters in the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `NLS_LOWER(char, nlsparam)` where *char* is the value of this `TypedExpression` and *nlsparam* is the `nlsparam` parameter.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Parameters:
      `nlsparam` - A `TypedExpression` that has a linguistic sort sequence in the form `NLS_SORT = sort[_ai |_ci]`, where *sort* is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort. For more information about linguistic sorting, refer to *Oracle Database Globalization Support Guide*.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which all alphabetic characters are lowercase.

    <!-- -->

    - #### nlsSort

          public final TypedExpression nlsSort(TypedExpression nlsparam)

      Creates a `TypedExpression` that evaluates to the string of bytes that Oracle OLAP uses to sort a text string. You can use this method to specify sorting and comparison operations that are based on a linguistic sort sequence rather than on the binary value of a string. The syntax of the `TypedExpression` returned by this method is `NLSSORT(char, nlsparam)` where *char* is the value of this `TypedExpression` and *nlsparam* is the `nlsparam` parameter.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Parameters:
      `nlsparam` - A `TypedExpression` that has a linguistic sort sequence in the form `NLS_SORT = sort[_ai |_ci]`, where *sort* is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort. For more information about linguistic sorting, refer to *Oracle Database Globalization Support Guide*.

      Returns:
      A `RowFunctionExpression` that evaluates to a string of bytes that Oracle OLAP uses to sort a text string.

    <!-- -->

    - #### nlsUpper

          public final TypedExpression nlsUpper(TypedExpression nlsparam)

      Converts to uppercase all alphabetic characters in the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `NLS_UPPER(char, nlsparam)` where *char* is the value of this `TypedExpression` and *nlsparam* is the `nlsparam` parameter.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Parameters:
      `nlsparam` - A `TypedExpression` that has a linguistic sort sequence in the form `NLS_SORT = sort[_ai |_ci]`, where *sort* is an NLS language. You can add a suffix to the language to modify the sort: `_ai` for an accent-insensitive sort, or `_ci` for a case-insensitive sort. For more information about linguistic sorting, refer to *Oracle Database Globalization Support Guide*.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which all alphabetic characters are uppercase.

    <!-- -->

    - #### regexpInstr

          public final TypedExpression regexpInstr(TypedExpression pattern,
                                                   TypedExpression position,
                                                   TypedExpression occurrence,
                                                   TypedExpression returnOption,
                                                   TypedExpression matchParameter)

      Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression`. The `TypedExpression` that is returned by this method evaluates to an integer that indicates either the beginning or ending position of the matched substring. If no match occurs, the `TypedExpression` evaluates to 0.
      Parameters:
      `pattern` - A `TypedExpression` that represents the regular expression to search for. A period matches any character.

      `position` - A `TypedExpression` that represents a nonzero integer that indicates where to begin the search. If the value of the integer is negative, then the search begins at the end of string and counts backwards toward the beginning. The default value of the parameter is 1, which begins the search at the first character of string.

      `occurrence` - A `TypedExpression` that represents is an integer that indicates which occurrence of pattern to search for. The value of the integer must be positive. The default value of the integer is 1, which specifies a search for the first occurrence of pattern.

      `returnOption` - A `TypedExpression` that represents an integer that is is either 0, which specifies finding the position of the beginning of match, or 1, which specifies finding the position of the first character following the match. The default value of the integer is 0.

      `matchParameter` - A `TypedExpression` that represents a text literal that lets you change the default matching behavior of the function. You can specify one or more of the following values:

      | Parameter Value | Description                                                                                                                                                                                                                                                                                                   |
      |:---------------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |       `c`       | Case-sensitive matching.                                                                                                                                                                                                                                                                                      |
      |       `i`       | Case-insensitive matching.                                                                                                                                                                                                                                                                                    |
      |       `m`       | Treat the source string as multiple lines. The characters `^` and `$` indicate the start and end, respectively, of a line anywhere in the source string, rather than only at the start or end of the entire source string. By default, the `REGEXP_INSTR` function treats the source string as a single line. |
      |       `n`       | Include the newline character among the characters matched by a period (the wildcard character). By default, it is not included.                                                                                                                                                                              |
      |       `x`       | Ignore whitespace characters.                                                                                                                                                                                                                                                                                 |

      Returns:
      A `RowFunctionExpression` that represents a search for a regular expression.

    <!-- -->

    - #### regexpReplace

          public final TypedExpression regexpReplace(TypedExpression pattern,
                                                     TypedExpression replaceString,
                                                     TypedExpression position,
                                                     TypedExpression occurrence,
                                                     TypedExpression matchParameter)

      Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression` and the replacement of the matching string with another string.
      Parameters:
      `pattern` - A `TypedExpression` that represents the regular expression to search for. The expression is usually a text literal and can contain up to 512 bytes.

      `replaceString` - A `TypedExpression` that represents the text that replaces the searched for pattern in this `TypedExpression`.

      `position` - A `TypedExpression` that represents a nonzero integer that indicates where to begin the search. If the value of the integer is negative, then the search begins at the end of string and counts backwards toward the beginning. The default value of the parameter is 1, which begins the search at the first character of string.

      `occurrence` - A `TypedExpression` that represents is an integer that indicates which occurrence of pattern to search for. The value of the integer must be positive. The default value of the integer is 1, which specifies a search for the first occurrence of pattern.

      `matchParameter` - A `TypedExpression` that represents a text literal that lets you change the default matching behavior of the function. You can specify one or more of the values listed in the table in the `matchParameter` description in the `regexpInstr` method.

      Returns:
      A `RowFunctionExpression` that represents the replacement of a regular expression by another expression.

    <!-- -->

    - #### regexpSubstr

          public final TypedExpression regexpSubstr(TypedExpression pattern,
                                                    TypedExpression position,
                                                    TypedExpression occurrence,
                                                    TypedExpression matchParameter)

      Creates a `TypedExpression` that represents a search for a regular expression pattern in the string value of this `TypedExression`. The `TypedExpression` that is returned by this method evaluates to the matched expression.
      Parameters:
      `pattern` - A `TypedExpression` that represents the regular expression to search for. The expression is usually a text literal and can contain up to 512 bytes.

      `position` - A `TypedExpression` that represents a nonzero integer that indicates where to begin the search. If the value of the integer is negative, then the search begins at the end of string and counts backwards toward the beginning. The default value of the parameter is 1, which begins the search at the first character of string.

      `occurrence` - A `TypedExpression` that represents is an integer that indicates which occurrence of pattern to search for. The value of the integer must be positive. The default value of the integer is 1, which specifies a search for the first occurrence of pattern.

      `matchParameter` - A `TypedExpression` that represents a text literal that lets you change the default matching behavior of the function. You can specify one or more of the values listed in the table in the `matchParameter` description in the `regexpInstr` method.

      Returns:
      A `RowFunctionExpression` that evaluates to the string of this `TypedExpression` that matches the specified pattern.

    <!-- -->

    - #### replace

          public final TypedExpression replace(TypedExpression searchString,
                                               TypedExpression replacementString)

      Searches a string for a pattern, replaces it with another string, and returns the modified string.
      Parameters:
      `searchString` - A `TypedExpression` that represents the string to search for.

      `replacementString` - A `TypedExpression` that represents the text that replaces searched for string of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the string of this `TypedExpression` with the searched for string replaced by the replacement string.

    <!-- -->

    - #### rpad

          public final TypedExpression rpad(TypedExpression n,
                                            TypedExpression expr2)

      Adds the specified number of characters to the right of the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `RPAD(expr1, n, expr2)` where *expr1* is the value of this `TypedExpression` and the other arguments are the parameters of this method.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Parameters:
      `n` - A `TypedExpression` that has a number that specifies the total length of value of the `TypedExpression` returned by this method. If the value of this `TypedExpression` is longer than `n`, then the `RPAD` expression truncates the value of the returned `TypedExpression` to `n` characters.

      `expr2` - A `TypedExpression` that has a text expression for the padding characters. By default, the padding character is a space.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which text expression of this `TypedExpression` is padded to the right with the specified number of padding characters.

    <!-- -->

    - #### rtrim

          public final TypedExpression rtrim(TypedExpression set)

      Searches the value of this `TypedExpression`, starting from the right, and removes all of the characters that match the characters in the trim expression `set`, until an unmatched character occurs. The syntax of the `TypedExpression` returned by this method is `RTRIM(char, set)` where *char* is the value of this `TypedExpression` and *set* is the `set` parameter.
      Parameters:
      `set` - A `TypedExpression` that has a text expression with the characters to remove. The default value of `set` is a single blank.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression with the specified characters trimmed from the right.

    <!-- -->

    - #### soundex

          public final TypedExpression soundex()

      Creates a `TypedExpression` that evaluates to a character string that contains the phonetic representation of the character that is the value of this `TypedExpresson`. You can use this method to compare words that are spelled differently, but that sound alike in English.
      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is a phonetic representation of the value of this `TypedExpresson`.

    <!-- -->

    - #### substr

          public final TypedExpression substr(TypedExpression position,
                                              TypedExpression substringLength)

      Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified character position and includes the specified number of characters. The `TypedExpression` returned by this method calculates lengths using characters as defined by the input character set.
      Parameters:
      `position` - A `TypedExpression` that specifies the position at which to begin the substitution. If the value of this parameter is positive, then the count of positions starts at the beginning of the value of this `TypedExpression`. If the parameter value is negative, then the count begins at the end of this `TypedExpression` and procedes backward. If the parameter value is 0 (zero), then the first character of this `TypedExpression` is the beginning of the substring.

      `substringLength` - A `TypedExpression` that represents the number of characters to select. By default, the selection includes all of the characters of this `TypedExpression`. If you specify a value less than 1, then the value of the returned `TypedExpression` is `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is the specified substring of this `TypedExpresson`.

    <!-- -->

    - #### substrB

          public final TypedExpression substrB(TypedExpression position,
                                               TypedExpression substringLength)

      Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified byte position and extends the specified number of bytes. The `TypedExpression` returned by this method uses bytes to calculate lengths.
      Parameters:
      `position` - A `TypedExpression` that specifies the position at which to begin the substitution. If the value of this parameter is positive, then the count of positions starts at the beginning of the value of this `TypedExpression`. If the parameter value is negative, then the count begins at the end of this `TypedExpression` and procedes backward. If the parameter value is 0 (zero), then the first character of this `TypedExpression` is the beginning of the substring.

      `substringLength` - A `TypedExpression` that represents the number of bytes to select. By default, the selection includes all of the bytes of this `TypedExpression`. If you specify a value less than 1, then the value of the returned `TypedExpression` is `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is the specified substring of this `TypedExpresson`.

    <!-- -->

    - #### substrC

          public final TypedExpression substrC(TypedExpression position,
                                               TypedExpression substringLength)

      Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified Unicode complete character position and extends the specified number of Unicode complete characters. The `TypedExpression` returned by this method uses Unicode complete characters to calculate lengths.
      Parameters:
      `position` - A `TypedExpression` that specifies the position at which to begin the substitution. If the value of this parameter is positive, then the count of positions starts at the beginning of the value of this `TypedExpression`. If the parameter value is negative, then the count begins at the end of this `TypedExpression` and procedes backward. If the parameter value is 0 (zero), then the first character of this `TypedExpression` is the beginning of the substring.

      `substringLength` - A `TypedExpression` that represents the number of characters to select. By default, the selection includes all of the characters of this `TypedExpression`. If you specify a value less than 1, then the value of the returned `TypedExpression` is `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is the specified substring of this `TypedExpresson`.

    <!-- -->

    - #### substr2

          public final TypedExpression substr2(TypedExpression position,
                                               TypedExpression substringLength)

      Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified UCS2 code point position and extends the specified number of UCS2 code points. The `TypedExpression` returned by this method uses UCS2 code points to calculate lengths.
      Parameters:
      `position` - A `TypedExpression` that specifies the position at which to begin the substitution. If the value of this parameter is positive, then the count of positions starts at the beginning of the value of this `TypedExpression`. If the parameter value is negative, then the count begins at the end of this `TypedExpression` and procedes backward. If the parameter value is 0 (zero), then the first character of this `TypedExpression` is the beginning of the substring.

      `substringLength` - A `TypedExpression` that represents the number of characters to select. By default, the selection includes all of the characters of this `TypedExpression`. If you specify a value less than 1, then the value of the returned `TypedExpression` is `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is the specified substring of this `TypedExpresson`.

    <!-- -->

    - #### substr4

          public final TypedExpression substr4(TypedExpression position,
                                               TypedExpression substringLength)

      Creates a `TypedExpression` that evaluates to the portion of the value of this `TypedExpression` that begins at the specified UCS4 code point position and extends the specified number of UCS4 code points. The `TypedExpression` returned by this method uses UCS4 code points to calculate lengths.
      Parameters:
      `position` - A `TypedExpression` that specifies the position at which to begin the substitution. If the value of this parameter is positive, then the count of positions starts at the beginning of the value of this `TypedExpression`. If the parameter value is negative, then the count begins at the end of this `TypedExpression` and procedes backward. If the parameter value is 0 (zero), then the first character of this `TypedExpression` is the beginning of the substring.

      `substringLength` - A `TypedExpression` that represents the number of characters to select. By default, the selection includes all of the characters of this `TypedExpression`. If you specify a value less than 1, then the value of the returned `TypedExpression` is `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that is the specified substring of this `TypedExpresson`.

    <!-- -->

    - #### translate

          public final TypedExpression translate(TypedExpression fromString,
                                                 TypedExpression toString)

      Creates a `TypedExpression` that evaluates to an expression in which all occurrences of the specified characters in the value of this `TypedExpression` are replaced by the corresponding character in the value of the `toString` parameter. You can use this method to make several single-character, one-to-one substitutions in one operation.
      Parameters:
      `fromString` - A `TypedExpression` that represents one or more characters to replace.

      `toString` - A `TypedExpression` that represents one or more characters with which to replace the corresponding characters in `fromString`. The number of characters in `toString` can be fewer than the number in `fromString`. If so, then a `null` replaces the extra characters of `fromString`. However, the `toString` expression cannot be empty.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression that has the value of this `TypedExpresson` with the specified replacements.

    <!-- -->

    - #### treat

          public final TypedExpression treat(java.lang.String typeName,
                                             boolean isRefType)

      Creates a `TypedExpression` that has the value of this `TypedExpression` but that has the type specified by `typeName`.
      Parameters:
      `typeName` - A `String` that contains the type for the returned `TypedExpression`. The value of `typeName` must be some supertype or subtype of the type of this `TypedExpression`.

      `isRefType` - A `boolean` that indicates whether this `TypedExpression` has the type `REF`.

      Returns:
      A `RowFunctionExpression` that evaluates to this `TypedExpresson` with the type changed to the specified type.

    <!-- -->

    - #### trim

          public final TypedExpression trim(TypedExpression trimCharacter)

      Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified leading or trailing characters.
      Parameters:
      `trimCharacter` - A `TypedExpression` that evaluates to a character to remove.

      Returns:
      A `RowFunctionExpression` that has the value of this `TypedExpression` but with the specified leading or trailing character removed.

    <!-- -->

    - #### trimLeading

          public final TypedExpression trimLeading(TypedExpression trimCharacter)

      Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified leading character.
      Parameters:
      `trimCharacter` - A `TypedExpression` that evaluates to a character to remove.

      Returns:
      A `RowFunctionExpression` that has the value of this `TypedExpression` but with the specified leading character removed.

    <!-- -->

    - #### trimTrailing

          public final TypedExpression trimTrailing(TypedExpression trimCharacter)

      Creates a `TypedExpression` that has the value of this `TypedExpression` but without the specified trailing character.
      Parameters:
      `trimCharacter` - A `TypedExpression` that evaluates to a character to remove.

      Returns:
      A `RowFunctionExpression` that has the value of this `TypedExpression` but with the specified trailing character removed.

    <!-- -->

    - #### upper

          public final TypedExpression upper()

      Converts to uppercase all alphabetic characters in the value of this `TypedExpression`. The syntax of the `TypedExpression` returned by this method is `UPPER(char)` where *char* is the value of this `TypedExpression`.
      The data type of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB` or `NCLOB`.

      Returns:
      A `RowFunctionExpression` that evaluates to a text expression in which all alphabetic characters are uppercase.

    <!-- -->

    - #### nlsCharsetDeclLen

          public final TypedExpression nlsCharsetDeclLen(TypedExpression charSetID)

      Creates a `TypedExpression` that evaluates to the declaration length (in number of characters) of the `NCHAR` column that this `TypedExpression` represents.
      Parameters:
      `charSetID` - A `TypedExpression` that evaluates to the character set ID of the column.

      Returns:
      A `RowFunctionExpression` that evaluates to the the declared length of the column.

    <!-- -->

    - #### nlsCharsetID

          public final TypedExpression nlsCharsetID()

      Creates a `TypedExpression` that evaluates to the character set ID number corresponding to character set name specified by this `TypedExpression`. The value of `TypedExpression` must be a run-time `VARCHAR2` value. The string value `'CHAR_CS'` evaluates to the database character set ID number of the server. The string value `'NCHAR_CS'` evaluates to the national character set ID number of the server. An invalid character set name evaluates to `null`.
      Returns:
      A `RowFunctionExpression` that evaluates to the character set ID number corresponding to character set name specified by this `TypedExpression`.

    <!-- -->

    - #### nlsCharsetName

          public final TypedExpression nlsCharsetName()

      Creates a `TypedExpression` that evaluates to the name of the character set that corresponds to the ID number specified by the value of this `TypedExpression`. The character set name is a `VARCHAR2` value in the database character set.
      If the value of this `TypedExpression` is a valid character set ID, then the `TypedExpression` returned by this method evalutes to `null`.

      Returns:
      A `RowFunctionExpression` that evaluates to the name of the character set that corresponds to the ID number specified by the value of this `TypedExpression`.

    <!-- -->

    - #### addMonths

          public final TypedExpression addMonths(TypedExpression rhs)

      Creates a `TypedExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.
      Parameters:
      `rhs` - A `TypedExpression` that evaluates to an integer that specifies the number of months to add.

      Returns:
      A `RowFunctionExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.

    <!-- -->

    - #### addMonths

          public final TypedExpression addMonths(int rhs)

      Creates a `TypedExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.
      Parameters:
      `rhs` - An integer that specifies the number of months to add.

      Returns:
      A `RowFunctionExpression` that evaluates to the date that is the specified number of months after the date that is the value of this `TypedExpression`.

    <!-- -->

    - #### currentDate

          public static final TypedExpression currentDate()

      Creates a `TypedExpression` that evaluates to the current date in the session time zone.
      Returns:
      A `RowFunctionExpression` that evaluates to the current date.

    <!-- -->

    - #### currentTime

          public static final TypedExpression currentTime(TypedExpression precision)

      Creates a `TypedExpression` that evaluates to the current date and time in the session time zone.
      Parameters:
      `precision` - A `TypedExpression` that specifies a fractional second precision for the returned time value. The default value is 6.

      Returns:
      A `RowFunctionExpression` that evaluates to the current time.

    <!-- -->

    - #### dbTimeZone

          public static final TypedExpression dbTimeZone()

      Creates a `TypedExpression` that evaluates to the value of the database time zone as either a time zone offset from Coordinated Universal Time (UTC) or a time zone region name.
      Returns:
      A `RowFunctionExpression` that evaluates to the database time zone.

    <!-- -->

    - #### extractYear

          public final TypedExpression extractYear()

      Extracts the year from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a year.

    <!-- -->

    - #### extractMonth

          public final TypedExpression extractMonth()

      Extracts the month from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a month.

    <!-- -->

    - #### extractDay

          public final TypedExpression extractDay()

      Extracts the day from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a day.

    <!-- -->

    - #### extractHour

          public final TypedExpression extractHour()

      Extracts the hour from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to an hour.

    <!-- -->

    - #### extractMinute

          public final TypedExpression extractMinute()

      Extracts the minute from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a minute.

    <!-- -->

    - #### extractSecond

          public final TypedExpression extractSecond()

      Extracts the second from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a second.

    <!-- -->

    - #### extractTimeZoneHour

          public final TypedExpression extractTimeZoneHour()

      Extracts the time zone hour from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a time zone hour.

    <!-- -->

    - #### extractTimeZoneMinute

          public final TypedExpression extractTimeZoneMinute()

      Extracts the time zone minute from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to a time zone minute.

    <!-- -->

    - #### extractTimeZoneRegion

          public final TypedExpression extractTimeZoneRegion()

      Extracts the name of the time zone region from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the name of the time zone region.

    <!-- -->

    - #### extractTimeZoneAbbr

          public final TypedExpression extractTimeZoneAbbr()

      Extracts the name of the time zone abbreviation from the datetime or interval value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the name of the time zone abbreviation.

    <!-- -->

    - #### fromTZ

          public final TypedExpression fromTZ(TypedExpression timeZoneValue)

      Converts the timestamp value of this `TypedExpression` and the specified time zone to a `TIMESTAMP WITH TIME ZONE` data type.
      Parameters:
      `timeZoneValue` - A `TypedExpression` that evaluates to a string in the format `TZH:TZM` or in `TZR` with an optional `TZD` format.

      Returns:
      A `RowFunctionExpression` that evaluates to the timestamp and time zone in the data type.

    <!-- -->

    - #### lastDay

          public final TypedExpression lastDay()

      Creates a `TypedExpression` that evaluates to the last day of the month in which the date of the value of this `TypedExpression` falls.
      Returns:
      A `RowFunctionExpression` that evaluates to the last day of the month in which the date of the value of this `TypedExpression` falls.

    <!-- -->

    - #### localTimestamp

          public static final TypedExpression localTimestamp(TypedExpression precision)

      Creates a `TypedExpression` that evaluates to the current date and time in the session time zone.
      Parameters:
      `precision` - A `TypedExpression` that specifies a fractional second precision for the returned time value.

      Returns:
      A `RowFunctionExpression` that evaluates to the current date and time in the session time zone.

    <!-- -->

    - #### monthsBetween

          public final TypedExpression monthsBetween(TypedExpression date2)

      Calculates the number of months between the date value of this `TypedExpression` and the specified date. When the two dates have the same day component or are both the last day of the month, then the value of the `TypedExpression` returned of this method is a whole number. Otherwise, the value of the returned object includes a fraction that considers the difference in the days based on a 31-day month.
      Parameters:
      `date2` - A `TypedExpression` that evaluates to a date.

      Returns:
      A `RowFunctionExpression` that evaluates to the the number of months between the date value of this `TypedExpression` and the specified date.

    <!-- -->

    - #### newTime

          public final TypedExpression newTime(TypedExpression timeZone1,
                                               TypedExpression timeZone2)

      Converts the date and time value of this `TypedExpression` from one time zone to another. Before using the `TypedExpression` returned by this method, set the NLS_DATE_FORMAT parameter to display 24-hour time.
      The following table lists the valid values for the `timezone1` and `timezone2` parameters. For other timezones, use the `fromTZ` method.

      | Abbreviation | Time Zone                   |
      |--------------|-----------------------------|
      | ADT          | Atlantic Daylight Time      |
      | AST          | Atlantic Standard Time      |
      | BDT          | Bering Daylight Time        |
      | BST          | Bering Standard Time        |
      | CDT          | Central Daylight Time       |
      | CST          | Central Standard Time       |
      | EDT          | Eastern Daylight Time       |
      | EST          | Eastern Standard Time       |
      | GMT          | Greenwich Mean Time         |
      | HDT          | Alaska-Hawaii Daylight Time |
      | HST          | Alaska-Hawaii Standard Time |
      | MDT          | Mountain Daylight Time      |
      | MST          | Mountain Standard Time      |
      | NST          | Newfoundland Standard Time  |
      | PDT          | Pacific Daylight Time       |
      | PST          | Pacific Standard Time       |
      | YDT          | Yukon Daylight Time         |
      | YST          | Yukon Standard Time         |

      Parameters:
      `timeZone1` - A `TypedExpression` that evaluates to the time zone of the date and time value of this `TypedExpression`.

      `timeZone2` - A `TypedExpression` that evaluates to the new time zone.

      Returns:
      A `RowFunctionExpression` that evaluates to the the new time.

    <!-- -->

    - #### nextDay

          public final TypedExpression nextDay(TypedExpression dayName)

      Creates a `TypedExpression` that evaluates to the first instance of the specified day of the week that follows the date value of this `TypedExpression`.
      Parameters:
      `dayName` - A `TypedExpression` that evaluates to the a day of the week.

      Returns:
      A `RowFunctionExpression` that evaluates to the first instance of the specified day of the week that follows the date value of this `TypedExpression`.

    <!-- -->

    - #### sessionTimeZone

          public static final TypedExpression sessionTimeZone()

      Creates a `TypedExpression` that evaluates to the time zone of the current session. The `TypedExpression` returned by this method is a time zone offset from Coordinated Universal Time (UTC) or a time zone region name.
      Returns:
      A `RowFunctionExpression` that evaluates to the time zone of the current session.

    <!-- -->

    - #### sysExtractUTC

          public final TypedExpression sysExtractUTC()

      Extracts the UTC (Coordinated Universal Time, which was formerly Greenwich Mean Time) from the datetime value of this `TypedExpression` with time zone offset or time zone region name.
      Returns:
      A `RowFunctionExpression` that evaluates to the the UTC for the value of this `TypedExpression`.

    <!-- -->

    - #### sysDate

          public static final TypedExpression sysDate()

      Creates a `TypedExpression` that evaluates to the current date and time of the operating system on which the database resides. The format of the value depends on the value of the NLS_DATE_FORMAT initialization parameter.
      Returns:
      A `RowFunctionExpression` that evaluates to the current date and time of the operating system on which the database resides.

    <!-- -->

    - #### sysTimestamp

          public static final TypedExpression sysTimestamp()

      Creates a `TypedExpression` that evaluates to the system date, including fractional seconds and time zone, of the system on which the database resides.
      Returns:
      A `RowFunctionExpression` that evaluates to the system date of the system on which the database resides.

    <!-- -->

    - #### toDSInterval

          public final TypedExpression toDSInterval(TypedExpression nlsparam)

      Converts the text expression of this `TypedExpression` to a `DS_INTERVAL` data type.
      Parameters:
      `nlsparam` - A `TypedExpression` that evaluates to a setting for the `NLS_NUMERIC_CHARACTERS` parameter of the database. The value of the `nlsparam` `TypedExpression` can have the form
        `NLS_NUMERIC_CHARACTERS = "dg"`
      where `d` is the decimal character, and `g` is the group separator. Neither character can be a space.

      Returns:
      A `RowFunctionExpression` that evaluates to the the value of this `TypedExpression` converted to a `DS_INTERVAL` data type.

    <!-- -->

    - #### toTimestamp

          public final TypedExpression toTimestamp(TypedExpression fmt,
                                                   TypedExpression nlsparam)

      Converts the text expression of this `TypedExpression` to a `TIMESTAMP` data type.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a datetime model format that specifies the format of the value of this `TypedExpression`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter of the database or it can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to *Oracle Database SQL Language Reference*.

      `nlsparam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the the value of this `TypedExpression` converted to a `TIMESTAMP` data type.

    <!-- -->

    - #### toTimestampTZ

          public final TypedExpression toTimestampTZ(TypedExpression fmt,
                                                     TypedExpression nlsparam)

      Converts the text expression of this `TypedExpression` to a `TIMESTAMP_WITH_TIME_ZONE` data type.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a datetime model format that specifies the format of the value of this `TypedExpression`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter of the database or it can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, refer to *Oracle Database SQL Language Reference*.

      `nlsparam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the the value of this `TypedExpression` converted to a `TIMESTAMP_WITH_TIME_ZONE` data type.

    <!-- -->

    - #### toYMInterval

          public final TypedExpression toYMInterval()

      Converts the text expression of this `TypedExpression` to a `YM_INTERVAL` data type.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `YM_INTERVAL` data type.

    <!-- -->

    - #### tzOffset

          public final TypedExpression tzOffset()

      Creates a `TypedExpression` that evaluates to the time zone offset from Coordinated Universal Time (UTC).
      Returns:
      A `RowFunctionExpression` that evaluates to the time zone offset from Coordinated Universal Time (UTC).

    <!-- -->

    - #### greatest

          public static TypedExpression greatest(TypedExpression[] args)

      Creates a `TypedExpression` that evaluates to the largest expression in a list of expressions. Oracle OLAP implicitly converts all expressions after the first to the data type of the first expression before the comparison. It compares text expressions character by character.
      Parameters:
      `args` - An array of `TypedExpression` objects that have the values to compare.

      Returns:
      A `RowFunctionExpression` that evaluates to the largest expression in the list of expressions.

    <!-- -->

    - #### least

          public static TypedExpression least(TypedExpression[] args)

      Creates a `TypedExpression` that evaluates to the smallest expression in a list of expressions. Oracle OLAP implicitly converts all expressions after the first to the data type of the first expression before the comparison. It compares text expressions character by character.
      Parameters:
      `args` - An array of `TypedExpression` objects that have the values to compare.

      Returns:
      A `RowFunctionExpression` that evaluates to the smallest expression in the list of expressions.

    <!-- -->

    - #### asciiStr

          public final TypedExpression asciiStr()

      Converts the value of this `TypedExpression` to ASCII. The value of this `TypedExpression` can be a string, or an expression that evaluates to a string, in any character set. The `TypedExpression` returned by this method evaluates to an ASCII version of the string in the database character set. Oracle OLAP converts non-ASCII characters to the form `\xxxx`, where `xxxx` represents a UTF-16 code unit.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to ASCII.

    <!-- -->

    - #### binToNum

          public static TypedExpression binToNum(TypedExpression[] args)

      Converts an array of bits to the equivalent number. You can use the `TypedExpression` returned by this method for selecting groups of interest from a materialized view using grouping sets.
      Parameters:
      `args` - An array of `TypedExpression` objects that have the bit values to convert.

      Returns:
      A `RowFunctionExpression` that evaluates to the a number that is equivalent to the specified bit values.

    <!-- -->

    - #### cast

          public final TypedExpression cast(java.lang.String datatype)

      Converts the data type of the value of this `TypedExpression` into another data type value.
      Parameters:
      `datatype` - A `TypedExpression` that evaluates to a data type.

      Returns:
      A `RowFunctionExpression` that evaluates to the data type of the value of this `TypedExpression` converted to the specified data type.

    <!-- -->

    - #### charToROWID

          public final TypedExpression charToROWID()

      Converts the value of this `TypedExpression` from the `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2` data type to the `ROWID` data type.
      Returns:
      A `RowFunctionExpression` that evaluates to the the value of this `TypedExpression` converted to the `ROWID` data type.

    <!-- -->

    - #### compose

          public final TypedExpression compose()

      Converts the value of this `TypedExpression` to a Unicode string in the same character set as this expression. The value of this `TypedExpression` can be any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB`.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a Unicode string in the same character set.

    <!-- -->

    - #### convert

          public final TypedExpression convert(TypedExpression destCharSet)

      Converts the character string value of this `TypedExpression` from one character set to the specified character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the specified character set.

    <!-- -->

    - #### convert

          public final TypedExpression convert(TypedExpression destCharSet,
                                               TypedExpression sourceCharSet)

      Converts the character string value of this `TypedExpression` from the source character set to the destination character set.
      Parameters:
      `destCharSet` - A `TypedExpression` that evaluates to the destination character set.

      `sourceCharSet` - A `TypedExpression` that evaluates to the source character set.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted from the source character set to the destination character set.

    <!-- -->

    - #### decompose

          public final TypedExpression decompose()

      Decomposes the Unicode character string value of this `TypedExpression` and returns a `TypedExpression` in the same character set. For example, an o-umlaut code point in the value of this `TypedExpression` decomposes to an "o" code point followed by an umlaut code point in the returned expression.
      Returns:
      A `RowFunctionExpression` that evaluates to the the decomposed value of this `TypedExpression`.

    <!-- -->

    - #### hexToRAW

          public final TypedExpression hexToRAW()

      Converts to a raw value the value of this `TypedExpression`, which contains hexadecimal digits in the `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2` character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a raw value.

    <!-- -->

    - #### numToDSInterval

          public final TypedExpression numToDSInterval(TypedExpression intervalUnit)

      Converts the value of this `TypedExpression` to a `DS_INTERVAL` literal.
      Parameters:
      `intervalUnit` - A `TypedExpression` that evaluates to a text expression that specifies the units. The expression must resolve to `DAY`, `HOUR`, `MINUTE` or `SECOND`.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `DS_INTERVAL` literal value.

    <!-- -->

    - #### numToYMInterval

          public final TypedExpression numToYMInterval(TypedExpression intervalUnit)

      Converts the value of this `TypedExpression` to a `YM_INTERVAL` literal.
      Parameters:
      `intervalUnit` - A `TypedExpression` that evaluates to a text expression that specifies the units. The expression must resolve to `MONTH` or `YEAR`.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `YM_INTERVAL` literal value.

    <!-- -->

    - #### rawToHex

          public final TypedExpression rawToHex()

      Converts the raw value of this `TypedExpression`, to a character string value containing the hexadecimal representation of the raw value.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a hexadecimal value.

    <!-- -->

    - #### rawToNHex

          public final TypedExpression rawToNHex()

      Converts the raw value of this `TypedExpression`, to a character string value in the national character set; the value contains the hexadecimal representation of the raw value.
      Returns:
      A `RowFunctionExpression` that evaluates to a hexadecimal representation of the value of this `TypedExpression`.

    <!-- -->

    - #### rowIDToChar

          public final TypedExpression rowIDToChar()

      Converts the `ROWID` value of this `TypedExpression` to the `VARCHAR2` data type. The value of the `TypedExpression` returned by this method is always 18 characters long.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the `VARCHAR2` data type.

    <!-- -->

    - #### rowIDToNChar

          public final TypedExpression rowIDToNChar()

      Converts the `ROWID` value of this `TypedExpression` to the `NVARCHAR2` data type. The value of the `TypedExpression` returned by this method is always in the national character set and is 18 characters long.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the `NVARCHAR2` data type.

    <!-- -->

    - #### scnToTimestamp

          public final TypedExpression scnToTimestamp()

      Creates a `TypedExpression` that evaluates to the approximate timestamp that is associated with the system change number (SCN) value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the the approximate timestamp that is associated with the SCN value of this `TypedExpression`

    <!-- -->

    - #### timestampToSCN

          public final TypedExpression timestampToSCN()

      Creates a `TypedExpression` that evaluates to the approximate system change number (SCN) that is associated with the timestamp value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the the SCN that is associated with the timestamp value of this `TypedExpression`

    <!-- -->

    - #### toBinaryDouble

          public final TypedExpression toBinaryDouble(TypedExpression fmt,
                                                      TypedExpression nlsParam)

      Converts to a `BINARY_DOUBLE` the character string or a numeric value of type `NUMBER` or `BINARY_FLOAT` of this `TypedExpression`. The `fmt` and `nlsParam` parameters are valid only if the value of this `TypedExpression` is a character string.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a text expression that identifies a number format model as described in *Oracle Database SQL Language Reference*.

      `nlsParam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a double-precision floating-point number.

    <!-- -->

    - #### toBinaryFloat

          public final TypedExpression toBinaryFloat(TypedExpression fmt,
                                                     TypedExpression nlsParam)

      Converts to a `BINARY_FLOAT` the character string or a numeric value of type `NUMBER` or `BINARY_DOUBLE` of this `TypedExpression`.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a text expression that identifies a number format model as described in *Oracle Database SQL Language Reference*.

      `nlsParam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a single-precision floating-point number.

    <!-- -->

    - #### toChar

          public final TypedExpression toChar()

      Converts the `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB` value of this `TypedExpression` to the database character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the database character set.

    <!-- -->

    - #### toChar

          public final TypedExpression toChar(TypedExpression fmt,
                                              TypedExpression nlsParam)

      Converts the value of this `TypedExpression` to a value in the specified format and NLS parameters. The value of this `TypedExpression` can be a numeric expression or a datetime or interval expression.
      If the value of this `TypedExpression` is a numeric expression, then the `fmt` parameter is a `TypedExpression` that evaluates to a text expression that identifies a number format model as described in *Oracle Database SQL Language Reference*. For a numeric expression, the `nlsParam` parameter specifies the characters that are returned by the following number format elements:

      - Decimal character
      - Group separator
      - Local currency symbol
      - International currency symbol

      The `nlsParam` parameter values have the following formats:

           'NLS_NUMERIC_CHARACTERS = ''dg''
            NLS_CURRENCY = ''text''
            NLS_ISO_CURRENCY = territory '

      The characters `d` and `g` represent the decimal character and group separator, respectively. They must be different single-byte characters. Within the quoted string, use two single quotation marks around the parameter values. Ten characters are available for the currency symbol.

      If you omit this argument or any of the NLS parameters, then the values are the default values for your session.

      If the value of this `TypedExpression` is a datetime or interval expression, then the `fmt` parameter is a `TypedExpression` that evaluates to a datetime model format. The default date format is determined implicitly by the `NLS_TERRITORY` database initialization parameter or you can set it explicitly with the `NLS_DATE_FORMAT` database parameter. For data type formats, see *Oracle Database SQL Language Reference*.

      For a datetime or interval expression, the `nlsParam` parameter specifies the language in which month and day names and abbreviations of the converted value. The value of the `nlsParam` parameter has the following form:

           'NLS_DATE_LANGUAGE = language'

      By default, the converted value is in the session date language.

      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a text expression that identifies a number or datetime model format.

      `nlsParam` - A `TypedExpression` that evaluates to language parameters for the converted value.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a text string in the specified format and language parameters.

    <!-- -->

    - #### toCLOB

          public final TypedExpression toCLOB()

      Converts to a `CLOB` value the `NCLOB` in a LOB column or other character string value of this `TypedExpression`. The character string value of this `TypedExpression` can be any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB`.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `CLOB`.

    <!-- -->

    - #### toDate

          public final TypedExpression toDate()

      Converts the data type of the value of this `TypedExpression` to the `DATE` data type. The data type of the value of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `DATE`.

    <!-- -->

    - #### toDate

          public final TypedExpression toDate(TypedExpression fmt,
                                              TypedExpression nlsParam)

      Converts the data type of the value of this `TypedExpression` to the `DATE` data type in the format specified by the date format `fmt` and the language specified by `nlsparam`. The data type of the value of this `TypedExpression` can be `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a datetime model format that specifies the format of the value of this `TypedExpression`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter of the database or it can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, see *Oracle Database SQL Language Reference*.

      `nlsParam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `DATE`.

    <!-- -->

    - #### toLOB

          public final TypedExpression toLOB()

      Converts the value of this `TypedExpression` to a `LOB`. The value of this `TypedExpression` can be a `LONG` or `LONG` `RAW` in the column `long_column`. You can use this method only with a value from a `LONG` or `LONG` `RAW` column, and only in the select list of a subquery in an `INSERT` statement.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `LOB`.

    <!-- -->

    - #### toMultiByte

          public final TypedExpression toMultiByte()

      Converts the single-byte characters of the value of this `TypedExpression` to the corresponding multibyte characters.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to multibyte characters.

    <!-- -->

    - #### toNChar

          public final TypedExpression toNChar()

      Converts the `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB` value of this `TypedExpression` to the national character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the national character set.

    <!-- -->

    - #### toNChar

          public final TypedExpression toNChar(TypedExpression fmt,
                                               TypedExpression nlsParam)

      Converts the datetime or interval value of this `TypedExpression` from the database character set to the national character set in the format specified by the date format `fmt` and the language specified by `nlsparam`. The data type of the value of this `TypedExpression` can be `DATE`, `TIMESTAMP`, `TIMESTAMP_WITH_TIME_ZONE`, or `TIMESTAMP_WITH_LOCAL_TIME_ZONE` .
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a datetime model format that specifies the format of the value of this `TypedExpression`. The default date format is determined implicitly by the `NLS_TERRITORY` initialization parameter of the database or it can be set explicitly by the `NLS_DATE_FORMAT` parameter. For data type formats, see *Oracle Database SQL Language Reference*.

      `nlsParam` - A `TypedExpression` that evaluates to the language for the month and day names and abbreviations of the `TypedExpression` returned by this method. The value of the `nlsparam` `TypedExpression` can have the following form:
        `'NLS_DATE_LANGUAGE = language'`
      By default, the value of the `TypedExpression` returned by this method is in the session date language.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the national character set as specified by the parameters.

    <!-- -->

    - #### toNCLOB

          public final TypedExpression toNCLOB()

      Converts to an `NCLOB` value the `CLOB` in a LOB column or other character string value of this `TypedExpression`. The character string value of this `TypedExpression` can be any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, `NVARCHAR2`, `CLOB`, or `NCLOB`.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a `NCLOB`.

    <!-- -->

    - #### toNumber

          public final TypedExpression toNumber()

      Converts the value of this `TypedExpression` to the `NUMBER` data type.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a number.

    <!-- -->

    - #### toNumber

          public final TypedExpression toNumber(TypedExpression fmt)

      Converts the value of this `TypedExpression` to the `NUMBER` data type in the format model specified by `fmt`.
      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a text expression that identifies a number format model as described in *Oracle Database SQL Language Reference*.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a number in the specified format.

    <!-- -->

    - #### toNumber

          public final TypedExpression toNumber(TypedExpression fmt,
                                                TypedExpression nlsParam)

      Converts the value of this `TypedExpression` to the `NUMBER` data type in the format model specified by `fmt`. The `nlsParam` parameter specifies the characters that are returned by the following number format elements:
      - Decimal character
      - Group separator
      - Local currency symbol
      - International currency symbol

      The `nlsParam` parameter values have the following formats:

           'NLS_NUMERIC_CHARACTERS = ''dg''
            NLS_CURRENCY = ''text''
            NLS_ISO_CURRENCY = territory '

      Parameters:
      `fmt` - A `TypedExpression` that evaluates to a text expression that identifies a number format model as described in *Oracle Database SQL Language Reference*.

      `nlsParam` - A `TypedExpression` that evaluates to language parameters for the converted value.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a number as specified by the format and language parameters.

    <!-- -->

    - #### toSingleByte

          public final TypedExpression toSingleByte()

      Converts the multibyte characters of the value of this `TypedExpression` to the corresponding single-byte characters.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to a single-byte characters.

    <!-- -->

    - #### translateUsingCharCS

          public final TypedExpression translateUsingCharCS()

      Converts the character string value of this `TypedExpression` into the database character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the database character set.

    <!-- -->

    - #### translateUsingNCharCS

          public final TypedExpression translateUsingNCharCS()

      Converts the character string value of this `TypedExpression` into the national character set.
      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the national character set.

    <!-- -->

    - #### unistr

          public final TypedExpression unistr()

      Converts the value of this `TypedExpression` into the national character set. The national character set of the database can be either AL16UTF16 or UTF8. The value of this `TypedExpression` can include Unicode encoded character values. Unicode encoding is useful, for example, for inserting data into `NCHAR` columns.
      The Unicode encoding value has the form `'\xxxx'` where `'xxxx'` is the hexadecimal value of a character in UCS-2 encoding format. Supplementary characters are encoded as two code units, the first from the high-surrogates range (U+D800 to U+DBFF), and the second from the low-surrogates range (U+DC00 to U+DFFF). To include the backslash in the string itself, precede it with another backslash (\\).

      For portability and data preservation, Oracle recommends that in the value of this `TypedExpression` you specify only ASCII characters and the Unicode encoding values.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of this `TypedExpression` converted to the national character set.

    <!-- -->

    - #### decode

          public final TypedExpression decode(TypedExpression[] cases,
                                              TypedExpression defaultExpression)

      Compares the value of this `TypedExpression` to one or more search strings one by one. If the value of this `TypedExpression` is equal to a search string, then the `TypedExpression` returned by this method has the result that corresponds to the search string. If no match occurs, then the returned value is the specified default. If you omit a default value, then the returned value is `null`.
      Parameters:
      `cases` - An array of `TypedExpression` objects that evaluate to search strings and corresponding results.

      `defaultExpression` - A `TypedExpression`

      Returns:
      A `RowFunctionExpression` that evaluates to the the results returned by the searches.

    <!-- -->

    - #### oraHash

          public final TypedExpression oraHash(TypedExpression maxBucket,
                                               TypedExpression seedValue)

      Computes the hash value of the value of this `TypedExpression`. This expression returned by this method is useful for operations such as analyzing a subset of data and generating a random sample.
      The value of this `TypedExpression` commonly evaluates to a column name. The value can be any length but it cannot be a `LONG` or `LOB` type. It cannot be a user-defined object type unless it is a nested table type. The hash value for nested table types does not depend on the order of elements in the collection. All other datatypes are supported for the value.

      The `maxBucket` and `seedValue` parameters are optional.

      Parameters:
      `maxBucket` - A `TypedExpression` that evaluates to the maximum bucket value returned by the hash function. You can specify any value between 0 and 4294967295. The default is 4294967295.

      `seedValue` - A `TypedExpression` that evaluates to a value that enables Oracle OLAP to produce many different results for the same set of data. Oracle OLAP applies the hash function to the combination of the value of this `TypedExpression` and the the value of this parameter. You can specify any value between 0 and 4294967295. The default is 0.

      Returns:
      A `RowFunctionExpression` that evaluates to the the hash value of the value of this `TypedExpression`.

    <!-- -->

    - #### dump

          public final TypedExpression dump(TypedExpression returnFormat,
                                            TypedExpression startPosition,
                                            TypedExpression length)

      Creates a `TypedExpression` that evaluates to the data type code, length in bytes, and internal representation of the value of this `TypedExpression`. For the datatype corresponding to each code, see *Oracle Database SQL Language Reference*.
      The values of the `startPosition` and `length` parameters combine to determine which portion of the internal representation to return. The default is to return the entire internal representation in decimal notation.

      Parameters:
      `returnFormat` - A `TypedExpression` that evaluates to an expression that specifies the format of the return value. The expression can have any of the following values:

      - 8 returns result in octal notation.
      - 10 returns result in decimal notation.
      - 16 returns result in hexadecimal notation.
      - 17 returns result as single characters.

      By default, the return value contains no character set information. To retrieve the character set name of expr, add 1000 to any of the preceding format values. For example, a value of 1008 returns the result in octal and provides the character set name the value of this `TypedExpression`.

      `startPosition` - A `TypedExpression` that evaluates to the position in the internal representation at which to start the process.

      `length` - A `TypedExpression` that evaluates to the the amount of the internal representation to process.

      Returns:
      A `RowFunctionExpression` that evaluates to the the data type code, length in bytes, and internal representation of the value of this `TypedExpression`. The returned expression is always in the database character set.

    <!-- -->

    - #### deref

          public final TypedExpression deref()

      Creates a `TypedExpression` that evaluates to the object reference of the value of this `TypedExpression`, which must evaluate to a `REF` to an object.
      Returns:
      A `RowFunctionExpression` that evaluates to the to the object reference of the value of this `TypedExpression`.

    <!-- -->

    - #### vsize

          public final TypedExpression vsize()

      Creates a `TypedExpression` that evaluates to the number of bytes in the internal representation of the value of this `TypedExpression`.
      Returns:
      A `RowFunctionExpression` that evaluates to the number of bytes in the internal representation of the value of this `TypedExpression`.

    <!-- -->

    - #### coalesce

          public static TypedExpression coalesce(TypedExpression[] args)

      Creates a `TypedExpression` that evaluates to the first non-null expression in a list of expressions, or to `null` when all of the expressions evaluate to `null`.
      Parameters:
      `args` - An array of `TypedExpression` objects that evaluate to a list of expressions.

      Returns:
      A `RowFunctionExpression` that evaluates to the first non-null expression in the list of expressions, or to `null` when all of the expressions evaluate to `null`.

    <!-- -->

    - #### nullIf

          public final TypedExpression nullIf(TypedExpression expr2)

      Compares the value of this `TypedExpression` to the value of the `expr2` `TypedExpression`. The `TypedExpression` returned by this method evaluates to `null` when the expressions are equal or to the value of this `TypedExpression` when they are not.
      Parameters:
      `expr2` - A `TypedExpression` that evaluates to an expression to compare to the value of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the `null` when the Compared expressions are equal or to the value of this `TypedExpression` when they are not equal.

    <!-- -->

    - #### nvl

          public final TypedExpression nvl(TypedExpression expr2)

      Replaces the null value of this `TypedExpression` with the string specified by `expr2`. If the value of this `TypedExpression` is not null, then the returned `TypedExpression` has the same value as this `TypedExpression`.
      Parameters:
      `expr2` - A `TypedExpression` that has the string value with which to replace the null value of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the string specified by `expr2` or to the value of this `TypedExpression`.

    <!-- -->

    - #### nvl2

          public final TypedExpression nvl2(TypedExpression expr2,
                                            TypedExpression expr3)

      Replaces the value of this `TypedExpression` with the expression specified by `expr2` or with the expression specified by `expr3` if the value of this `TypedExpression` is `null`.
      To replace a null value with a string, use the `nvl` method.

      Parameters:
      `expr2` - A `TypedExpression` that has the expression with which to replace the non-null value of this `TypedExpression`.

      `expr3` - A `TypedExpression` that has the expression with which to replace the null value of this `TypedExpression`.

      Returns:
      A `RowFunctionExpression` that evaluates to the expression specified by `expr2` or by `expr3`.

    <!-- -->

    - #### sysContext

          public final TypedExpression sysContext(TypedExpression namespace,
                                                  TypedExpression parameter,
                                                  TypedExpression length)

      Creates a `TypedExpression` that evaluates to the value of `parameter` that is associated with the context `namespace`.
      Parameters:
      `namespace` - A `TypedExpression` that evaluates to a string that designates an existing namespace. The namespace value must be a valid SQL identifier.

      `parameter` - A `TypedExpression` that evaluates to a parameter associated with the namespace. The value of the parameter must have been set using the `DBMS_SESSION.set_context` procedure. The parameter name can be any string. It is not case sensitive, but it cannot exceed 30 bytes in length.

      `length` - A `TypedExpression` that evaluates to a length for the value of the `TypedExpression` returned by this method. The default maximum size of the return value is 256 bytes. You can override this default by specifying the optional length parameter, which must be a `NUMBER` or a value that can be implicitly converted to `NUMBER`. The valid range of values is 1 to 4000 bytes. If you specify an invalid value, then Oracle OLAP ignores it and uses the default.

      Returns:
      A `RowFunctionExpression` that evaluates to the value of `parameter` associated with the context `namespace`. The data type of the value of the `RowFunctionExpression` is `VARCHAR2`.

    <!-- -->

    - #### sysGUID

          public static TypedExpression sysGUID()

      Creates a `TypedExpression` that evaluates to a globally unique identifier (RAW value) made up of 16 bytes.
      Returns:
      A `RowFunctionExpression` that evaluates to the globally unique identifier.

    <!-- -->

    - #### UID

          public static TypedExpression UID()

      Creates a `TypedExpression` that evaluates to an integer that uniquely identifies the session user.
      Returns:
      A `RowFunctionExpression` that evaluates to an integer that uniquely identifies the session user.

    <!-- -->

    - #### USER

          public static TypedExpression USER()

      Creates a `TypedExpression` that evaluates to the name of the session user.
      Returns:
      A `RowFunctionExpression` that evaluates to the name of the session user.

    <!-- -->

    - #### sysTypeID

          public final TypedExpression sysTypeID()

      Creates a `TypedExpression` that evaluates to the the typeid of the most specific type of the operand.
      Returns:
      A `RowFunctionExpression` that evaluates to the the typeid of the most specific type of the operand.

    <!-- -->

    - #### userEnv

          public final TypedExpression userEnv()

      Creates a `TypedExpression` that evaluates to information about the current session.
      Returns:
      A `RowFunctionExpression` that evaluates to information about the current session.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](TimeZoneExpression.md)
- [Next Class](UnaryOperatorExpression.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
