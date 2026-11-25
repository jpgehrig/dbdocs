Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NUMBER.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NCLOB.md)
- [Next Class](OPAQUE.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.sql

## Class NUMBER

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.NUMBER

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.OracleNumber

  ------------------------------------------------------------------------



      public class NUMBER
      extends Datum
      implements oracle.jdbc.internal.OracleNumber

  **NUMBER Class**
  The NUMBER class provides converisons between the Oracle Number (lnxnum_t) data type and Java types byte\[\], byte, short, integer, long, float, double, String, BigInteger. and BigDecimal.

  The internal data for this object is stored as a byte array in the super class' storage area.

  Static methods are used for conversions.

  The LNX length included format is not supported. The byte array passed to or returned by any method is assumed to have the proper length accessible by the `byte[].length` instance variable.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                  |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NUMBER``()`<br>Constructs a NUMBER object initialized to zero.                                                                                                                                              |
    | `NUMBER``(`[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` BigDecNum)`<br>Constructs a NUMBER object initialized to the specified BigDecimal value. |
    | `NUMBER``(`[`BigInteger`](http://download.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` BigIntNum)`<br>Constructs a NUMBER object initialized to the specified BigInteger value. |
    | `NUMBER``(boolean boolNum)`<br>Constructs a Number object initialized to the specified boolean value.                                                                                                        |
    | `NUMBER``(byte byteNum)`<br>Constructs a Number object initialized to the specified byte value.                                                                                                              |
    | `NUMBER``(byte[] num)`<br>Constructs a NUMBER object initialized to the value specified by the byte array.                                                                                                   |
    | `NUMBER``(double doubleNum)`<br>Constructs a Number object initialized to the specified double value.                                                                                                        |
    | `NUMBER``(float floatNum)`<br>Constructs a Number object initialized to the specified float value.                                                                                                           |
    | `NUMBER``(int intNum)`<br>Constructs a Number object initialized to the specified integer value.                                                                                                             |
    | `NUMBER``(long longNum)`<br>Constructs a Number object initialized to the specified long value.                                                                                                              |
    | `NUMBER``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Constructs a NUMBER object initialized to the value specified by the object             |
    | `NUMBER``(short shortNum)`<br>Constructs a Number object initialized to the specified short value.                                                                                                           |
    | `NUMBER``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` StringNum, int scale)`<br>Constructs a NUMBER object initialized to the specified String value.  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                               |
    |------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NUMBER`                                                                                                         | `abs``()`<br>Returns a new NUMBER object initialized to the absolute value of NUMBER.                                                                                                                                                                                                                                                                                                                                |
    | `NUMBER`                                                                                                         | `acos``()`<br>Returns a new NUMBER object initialized to the arc cosine value of NUMBER.                                                                                                                                                                                                                                                                                                                             |
    | `NUMBER`                                                                                                         | `add``(NUMBER n)`<br>Returns a new NUMBER object initialized to the value of the addition of the NUMBER value and n.                                                                                                                                                                                                                                                                                                 |
    | `NUMBER`                                                                                                         | `asin``()`<br>Returns a new NUMBER object initialized to the arc sine value of NUMBER.                                                                                                                                                                                                                                                                                                                               |
    | `NUMBER`                                                                                                         | `atan``()`<br>Returns a new NUMBER object initialized to the arc tangent value of NUMBER.                                                                                                                                                                                                                                                                                                                            |
    | `NUMBER`                                                                                                         | `atan2``(NUMBER x)`<br>Returns a new NUMBER object initialized to the value of atan2(NUMBER/x).                                                                                                                                                                                                                                                                                                                      |
    | [`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)          | `bigDecimalValue``()`<br>Calls toBigDecimalto convert internal Oracle Number into a Java BigDecimal.                                                                                                                                                                                                                                                                                                                 |
    | [`BigInteger`](http://download.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)          | `bigIntegerValue``()`<br>Calls toBigInteger to convert internal Oracle Number to a Java BigInteger.                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                        | `booleanValue``()`<br>Calls toBoolean to convert internal Oracle Number to a Java boolean.                                                                                                                                                                                                                                                                                                                           |
    | `byte`                                                                                                           | `byteValue``()`<br>Calls toByte to convert internal Oracle Number to a Java byte.                                                                                                                                                                                                                                                                                                                                    |
    | `NUMBER`                                                                                                         | `ceil``()`<br>Returns a new NUMBER object initialized to the ceiling of NUMBER value.                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                            | `compareTo``(NUMBER n)`<br>Returns -1 if NUMBER is less than n, 0 if NUMBER and n are equal (==), 1 if NUMBER is greater than n.                                                                                                                                                                                                                                                                                     |
    | `NUMBER`                                                                                                         | `cos``()`<br>Returns a new NUMBER object initialized to the cosine value of NUMBER.                                                                                                                                                                                                                                                                                                                                  |
    | `NUMBER`                                                                                                         | `cosh``()`<br>Returns a new NUMBER object initialized to the hyperbolic cosine value of NUMBER.                                                                                                                                                                                                                                                                                                                      |
    | `NUMBER`                                                                                                         | `decrement``()`<br>Returns a new NUMBER object initialized to the NUMBER value decremented by 1.                                                                                                                                                                                                                                                                                                                     |
    | `NUMBER`                                                                                                         | `div``(NUMBER n)`<br>Returns a new NUMBER object initialized to the division of NUMBER value by n.                                                                                                                                                                                                                                                                                                                   |
    | `double`                                                                                                         | `doubleValue``()`<br>Calls toDouble to convert internal Oracle Number to a Java double.                                                                                                                                                                                                                                                                                                                              |
    | `static NUMBER`                                                                                                  | `e``()`<br>Returns a new NUMBER object initialized to the value of e.                                                                                                                                                                                                                                                                                                                                                |
    | `NUMBER`                                                                                                         | `exp``()`<br>Returns a new NUMBER object initialized to the value of e raised to NUMBER value.                                                                                                                                                                                                                                                                                                                       |
    | `NUMBER`                                                                                                         | `floatingPointRound``(int precision)`<br>Returns a new NUMBER object initialized to Number rounded to precision significant decimal digits.                                                                                                                                                                                                                                                                          |
    | `float`                                                                                                          | `floatValue``()`<br>Calls toFloat to convert internal Oracle Number to a Java float.                                                                                                                                                                                                                                                                                                                                 |
    | `NUMBER`                                                                                                         | `floor``()`<br>Returns a new NUMBER object initialized to the floor of NUMBER value.                                                                                                                                                                                                                                                                                                                                 |
    | `static NUMBER`                                                                                                  | `formattedTextToNumber``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` num, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` fmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns a NUMBER converted from Num controlled by the format fmt. |
    | `NUMBER`                                                                                                         | `increment``()`<br>Returns a new NUMBER object initialized to the NUMBER value incremented by 1.                                                                                                                                                                                                                                                                                                                     |
    | `int`                                                                                                            | `intValue``()`<br>Calls toInt to convert internal Oracle Number to a Java int.                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                        | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class                                                                                                                                                                                                                          |
    | `boolean`                                                                                                        | `isInf``()`<br>Returns true if NUMBER value is positive or negative infinity and a false otherwise.                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                        | `isInt``()`<br>Returns true if NUMBER value is finite and integral.                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                        | `isNegInf``()`<br>Returns returns true if NUMBER is negative infinity and false otherwise.                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                        | `isPosInf``()`<br>Returns true if NUMBER is positive infinity and false otherwise.                                                                                                                                                                                                                                                                                                                                   |
    | `static boolean`                                                                                                 | `isValid``(byte[] num)`<br>Checks if a given Oracle Number is valid                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                        | `isZero``()`<br>Returns true if NUMBER is zero.                                                                                                                                                                                                                                                                                                                                                                      |
    | `NUMBER`                                                                                                         | `ln``()`<br>Returns a new NUMBER object initialized to the natural logarithm of the NUMBER value.                                                                                                                                                                                                                                                                                                                    |
    | `static NUMBER`                                                                                                  | `ln10``()`<br>Returns a new NUMBER object initialized to the value of ln(10).                                                                                                                                                                                                                                                                                                                                        |
    | `NUMBER`                                                                                                         | `log``(NUMBER base)`<br>Returns a new NUMBER object initialized to the logarithm to the base base of the NUMBER value.                                                                                                                                                                                                                                                                                               |
    | `long`                                                                                                           | `longValue``()`<br>Calls toLong to convert internal Oracle Number to a Java long.                                                                                                                                                                                                                                                                                                                                    |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                  | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                                                                                                                                                                                 |
    | `NUMBER`                                                                                                         | `mod``(NUMBER n)`<br>Returns a new NUMBER object initialized to the remainder of the division of NUMBER/n.                                                                                                                                                                                                                                                                                                           |
    | `NUMBER`                                                                                                         | `mul``(NUMBER n)`<br>Returns a new NUMBER object initialized to product of NUMBER and n.                                                                                                                                                                                                                                                                                                                             |
    | `NUMBER`                                                                                                         | `negate``()`<br>Returns a new NUMBER object initialized to the negated NUMBER value.                                                                                                                                                                                                                                                                                                                                 |
    | `static NUMBER`                                                                                                  | `negInf``()`<br>Returns a new NUMBER object initialized to negative infinity.                                                                                                                                                                                                                                                                                                                                        |
    | `static NUMBER`                                                                                                  | `pi``()`<br>Returns a new NUMBER object initialized to the value of pi.                                                                                                                                                                                                                                                                                                                                              |
    | `static NUMBER`                                                                                                  | `posInf``()`<br>Returns a new NUMBER object initialized to positive infinity.                                                                                                                                                                                                                                                                                                                                        |
    | `NUMBER`                                                                                                         | `pow``(int exp)`<br>Returns a new NUMBER object initialized to NUMBER value raised to the exp power.                                                                                                                                                                                                                                                                                                                 |
    | `NUMBER`                                                                                                         | `pow``(NUMBER exp)`<br>Returns a new NUMBER object initialized to the value of NUMBER value raised to the exp power.                                                                                                                                                                                                                                                                                                 |
    | `NUMBER`                                                                                                         | `round``(int decimal_place)`<br>Returns a new NUMBER object initialized to the NUMBER value rounded to specified decimal place decimal_place.                                                                                                                                                                                                                                                                        |
    | `NUMBER`                                                                                                         | `scale``(int left, int right, boolean[] big)`<br>Returns a new NUMBER object initialized to the value determined by the rounding performed based on the right parameter below.                                                                                                                                                                                                                                       |
    | `NUMBER`                                                                                                         | `shift``(int digits)`<br>Returns a new NUMBER object initialized the NUMBER value shifted digits decimal places.                                                                                                                                                                                                                                                                                                     |
    | `short`                                                                                                          | `shortValue``()`<br>Calls toShort to convert internal Oracle Number to a Java short.                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                            | `sign``()`<br>Returns -1 if the sign of NUMBER is negative, 0 if NUMBER is 0, and \> 0 if NUMBER is positive.                                                                                                                                                                                                                                                                                                        |
    | `NUMBER`                                                                                                         | `sin``()`<br>Returns a new NUMBER object initialized to the sine of the NUMBER.                                                                                                                                                                                                                                                                                                                                      |
    | `NUMBER`                                                                                                         | `sinh``()`<br>Returns a new NUMBER object initialized to the hyperbolic sine of NUMBER.                                                                                                                                                                                                                                                                                                                              |
    | `NUMBER`                                                                                                         | `sqroot``()`<br>Returns a new NUMBER object initialized to the square root of NUMBER.                                                                                                                                                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `stringValue``()`<br>Calls toString to convert internal Oracle Number to a Java String.                                                                                                                                                                                                                                                                                                                              |
    | `NUMBER`                                                                                                         | `sub``(NUMBER n)`<br>Returns a new NUMBER object initialized to the difference of NUMBER and n.                                                                                                                                                                                                                                                                                                                      |
    | `NUMBER`                                                                                                         | `tan``()`<br>Returns a new NUMBER object initialized to the tangent of NUMBER.                                                                                                                                                                                                                                                                                                                                       |
    | `NUMBER`                                                                                                         | `tanh``()`<br>Returns a new NUMBER object initialized to the hyperbolic tangent of Number.                                                                                                                                                                                                                                                                                                                           |
    | `static NUMBER`                                                                                                  | `textToPrecisionNumber``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` num, boolean precflag, int preclen, boolean scaleflag, int scalelen, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns a NUMBER object initialized to the value in num as described below.                              |
    | `static `[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true) | `toBigDecimal``(byte[] num)`<br>Converts an Oracle Number into a Java BigDecimal.                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`BigInteger`](http://download.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true) | `toBigInteger``(byte[] num)`<br>Converts an Oracle Number into a Java BigInteger.                                                                                                                                                                                                                                                                                                                                    |
    | `static boolean`                                                                                                 | `toBoolean``(byte[] num)`<br>Convert an Oracle Number to a Java boolean.                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                                    | `toByte``(byte[] num)`<br>Converts an Oracle Number into a Java byte.                                                                                                                                                                                                                                                                                                                                                |
    | `byte[]`                                                                                                         | `toBytes``()`<br>Returns the internal Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte[]`                                                                                                  | `toBytes``(`[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` BigDecNum)`<br>Converts a Java BigDecimal to an Oracle Number byte array.                                                                                                                                                                                                                       |
    | `static byte[]`                                                                                                  | `toBytes``(`[`BigInteger`](http://download.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` BigIntNum)`<br>Converts a Java BigInteger to an Oracle Number byte array.                                                                                                                                                                                                                       |
    | `static byte[]`                                                                                                  | `toBytes``(boolean boolNum)`<br>Converts a Java boolean to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                              |
    | `static byte[]`                                                                                                  | `toBytes``(byte byteNum)`<br>Converts a Java byte to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                    |
    | `static byte[]`                                                                                                  | `toBytes``(double doubleNum)`<br>Converts a Java double to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                              |
    | `static byte[]`                                                                                                  | `toBytes``(float floatNum)`<br>Converts a Java float to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                 |
    | `static byte[]`                                                                                                  | `toBytes``(int intNum)`<br>Converts a Java int to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                       |
    | `static byte[]`                                                                                                  | `toBytes``(long longNum)`<br>Converts a Java long to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                    |
    | `static byte[]`                                                                                                  | `toBytes``(short shortNum)`<br>Converts a Java short to an Oracle Number byte array.                                                                                                                                                                                                                                                                                                                                 |
    | `static byte[]`                                                                                                  | `toBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` StringNum, int scale)`<br>Converts a Java String to an Oracle Number byte array.                                                                                                                                                                                                                        |
    | `static double`                                                                                                  | `toDouble``(byte[] num)`<br>Converts an Oracle Number into a Java double.                                                                                                                                                                                                                                                                                                                                            |
    | `static float`                                                                                                   | `toFloat``(byte[] num)`<br>Converts an Oracle Number into a Java float.                                                                                                                                                                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `toFormattedText``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` fmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns a new String based on the format specified in fmt and NUMBER.                                                                                                          |
    | `static int`                                                                                                     | `toInt``(byte[] num)`<br>Converts an Oracle Number into a Java int.                                                                                                                                                                                                                                                                                                                                                  |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                  | `toJdbc``()`<br>Returns the JDBC representation of the datum object                                                                                                                                                                                                                                                                                                                                                  |
    | `static long`                                                                                                    | `toLong``(byte[] num)`<br>Converts an Oracle Number into a Java long.                                                                                                                                                                                                                                                                                                                                                |
    | `static short`                                                                                                   | `toShort``(byte[] num)`<br>Converts an Oracle Number into a Java xemacs short.                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `toString``(byte[] num)`<br>Convert an Oracle Number to a Java String.                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `toText``(int outStringLength, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns a String with the unformatted representation of NUMBER.                                                                                                                                                                                                           |
    | `NUMBER`                                                                                                         | `truncate``(int decimal_place)`<br>Returns a new NUMBER object initialized to the NUMBER value truncated to specified decimal place decimal_place.                                                                                                                                                                                                                                                                   |
    | `static NUMBER`                                                                                                  | `zero``()`<br>Returns a new NUMBER object initialized to zero.                                                                                                                                                                                                                                                                                                                                                       |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`isNull`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleNumber

      `from, from`

<!-- -->

- - ### Constructor Detail

    - #### NUMBER

          public NUMBER()

      Constructs a NUMBER object initialized to zero.

    <!-- -->

    - #### NUMBER

          public NUMBER(byte[] num)

      Constructs a NUMBER object initialized to the value specified by the byte array. Assumes length separate format where `a.length` is the length of the Oracle Number in bytes.
      Parameters:
      `num` - Oracle Number in byte array format

    <!-- -->

    - #### NUMBER

          public NUMBER(byte byteNum)

      Constructs a Number object initialized to the specified byte value.
      Parameters:
      `byteNum` - The Java byte value

    <!-- -->

    - #### NUMBER

          public NUMBER(int intNum)

      Constructs a Number object initialized to the specified integer value.
      Parameters:
      `intNum` - The Java integer value

    <!-- -->

    - #### NUMBER

          public NUMBER(long longNum)

      Constructs a Number object initialized to the specified long value.
      Parameters:
      `longNum` - The Java long value

    <!-- -->

    - #### NUMBER

          public NUMBER(short shortNum)

      Constructs a Number object initialized to the specified short value.
      Parameters:
      `shortNum` - The Java short value

    <!-- -->

    - #### NUMBER

          public NUMBER(float floatNum)

      Constructs a Number object initialized to the specified float value.
      Parameters:
      `floatNum` - The Java float value

    <!-- -->

    - #### NUMBER

          public NUMBER(double doubleNum)
                 throws SQLException

      Constructs a Number object initialized to the specified double value.
      Parameters:
      `doubleNum` - The Java double value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### NUMBER

          public NUMBER(BigDecimal BigDecNum)
                 throws SQLException

      Constructs a NUMBER object initialized to the specified BigDecimal value. Throws a SQLException on over/underflow of the exponent and/or mantissa.
      Since there doesn't seem to be a way to represent +-inf using a BigDecimal this condition isn't considered.

      Notes:

      - This method *may not* preserve the scaling of the BigDecimal, since scaling information is not part of an Oracle number.
      - A BigDecimal distinguishes between 0 and -0. This method *will not* preserve the signedness of zero.
      - At present, this method does not round. If the BigDecimal has more digits than will fit into the mantissa of an Oracle number, an exception is thrown.

      Parameters:
      `BigDecNum` - The BigDecimal used to initialize NUMBER.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### NUMBER

          public NUMBER(BigInteger BigIntNum)
                 throws SQLException

      Constructs a NUMBER object initialized to the specified BigInteger value. Throws a SQLException on overflow of the exponent and/or mantissa.
      Parameters:
      `BigIntNum` - The Java BigInteger from which to construct the Oracle number.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on overflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### NUMBER

          public NUMBER(String StringNum,
                        int scale)
                 throws SQLException

      Constructs a NUMBER object initialized to the specified String value. Throws a SQLException on overflow of the exponent and/or mantissa.
      Parameters:
      `StringNum` - The Java String from which to construct the Oracle number.

      `scale` - scale to use

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### NUMBER

          public NUMBER(boolean boolNum)

      Constructs a Number object initialized to the specified boolean value.
      Parameters:
      `boolNum` - The Java boolean value

    <!-- -->

    - #### NUMBER

          public NUMBER(Object obj)
                 throws SQLException

      Constructs a NUMBER object initialized to the value specified by the object
      Parameters:
      `obj` - Object value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if initialization is not allowed

  <!-- -->

  - ### Method Detail

    - #### toDouble

          public static double toDouble(byte[] num)

      Converts an Oracle Number into a Java double. The resultant double will be rounded on loss of precision. Note that the exponent range of an IEEE double is greater than that of an Oracle number so an exponent over/underflow cannot occur.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java double value

    <!-- -->

    - #### toFloat

          public static float toFloat(byte[] num)

      Converts an Oracle Number into a Java float.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java float value

    <!-- -->

    - #### toLong

          public static long toLong(byte[] num)
                             throws SQLException

      Converts an Oracle Number into a Java long.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java long value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### toInt

          public static int toInt(byte[] num)
                           throws SQLException

      Converts an Oracle Number into a Java int.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java int value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### toShort

          public static short toShort(byte[] num)
                               throws SQLException

      Converts an Oracle Number into a Java xemacs short.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java short value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### toByte

          public static byte toByte(byte[] num)
                             throws SQLException

      Converts an Oracle Number into a Java byte.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java byte value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### toBigInteger

          public static BigInteger toBigInteger(byte[] num)
                                         throws SQLException

      Converts an Oracle Number into a Java BigInteger.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java BigInteger value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### toBigDecimal

          public static BigDecimal toBigDecimal(byte[] num)
                                         throws SQLException

      Converts an Oracle Number into a Java BigDecimal.
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java BigDecimal value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### toString

          public static String toString(byte[] num)

      Convert an Oracle Number to a Java String. Negative numbers are represented by a leading "-". No sign is added for positive numbers. The output will always be in fixed decimal format.
      Specified by:
      `toString` in interface `oracle.jdbc.internal.OracleNumber`

      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      fixed point decimal string

    <!-- -->

    - #### toBoolean

          public static boolean toBoolean(byte[] num)

      Convert an Oracle Number to a Java boolean. A zero value translates to `false` and non-zero values translate to `true`,
      Parameters:
      `num` - Oracle Number in byte array format

      Returns:
      a Java boolean value

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(double doubleNum)
                                throws SQLException

      Converts a Java double to an Oracle Number byte array.
      Parameters:
      `doubleNum` - Java double value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(float floatNum)

      Converts a Java float to an Oracle Number byte array.
      Parameters:
      `floatNum` - Java float value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(long longNum)

      Converts a Java long to an Oracle Number byte array.
      Parameters:
      `longNum` - Java long value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(int intNum)

      Converts a Java int to an Oracle Number byte array.
      Parameters:
      `intNum` - Java int value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(short shortNum)

      Converts a Java short to an Oracle Number byte array.
      Parameters:
      `shortNum` - Java short value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(byte byteNum)

      Converts a Java byte to an Oracle Number byte array.
      Parameters:
      `byteNum` - Java byte value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(BigInteger BigIntNum)
                                throws SQLException

      Converts a Java BigInteger to an Oracle Number byte array. Rounding will occur on loss of precision. Positive and Negative Infinity are not considered.
      Parameters:
      `BigIntNum` - Java BigInteger value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - will be thrown if the Oracle Number exponent or mantissa overflows.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(BigDecimal BigDecNum)
                                throws SQLException

      Converts a Java BigDecimal to an Oracle Number byte array.
      Parameters:
      `BigDecNum` - Java BigDecimal value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on overflow/underflow of the Oracle Number exponent or mantissa.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(String StringNum,
                                       int scale)
                                throws SQLException

      Converts a Java String to an Oracle Number byte array. Converts a fixed point number string. Negative numbers will begin with a - sign and numbers less than zero will begin with "0.".
      Notes:

      - This method *may not* preserve scale since scaling information is not part of an Oracle number.
      - This method *will not* preserve the signedness of zero.

      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleNumber`

      Parameters:
      `StringNum` - Java String value

      `scale` - scale to use

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(boolean boolNum)

      Converts a Java boolean to an Oracle Number byte array. A `true` value translates to 1 and a `false` value translates to 0.
      Parameters:
      `boolNum` - Java boolean value

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### toBytes

          public byte[] toBytes()

      Returns the internal Oracle Number byte array.
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleNumber`

      Returns:
      a Java byte array in Oracle Number length separate format. The `length` instance variable holds Oracle Number length in bytes.

    <!-- -->

    - #### doubleValue

          public double doubleValue()

      Calls toDouble to convert internal Oracle Number to a Java double.
      Overrides:
      [`doubleValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java double value

    <!-- -->

    - #### floatValue

          public float floatValue()

      Calls toFloat to convert internal Oracle Number to a Java float.
      Overrides:
      [`floatValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java float value

    <!-- -->

    - #### longValue

          public long longValue()
                         throws SQLException

      Calls toLong to convert internal Oracle Number to a Java long.
      Overrides:
      [`longValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java long value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### intValue

          public int intValue()
                       throws SQLException

      Calls toInt to convert internal Oracle Number to a Java int.
      Overrides:
      [`intValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java int value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### shortValue

          public short shortValue()
                           throws SQLException

      Calls toShort to convert internal Oracle Number to a Java short.
      Returns:
      a Java short value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### byteValue

          public byte byteValue()
                         throws SQLException

      Calls toByte to convert internal Oracle Number to a Java byte.
      Overrides:
      [`byteValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java byte value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### bigIntegerValue

          public BigInteger bigIntegerValue()
                                     throws SQLException

      Calls toBigInteger to convert internal Oracle Number to a Java BigInteger.
      Returns:
      a Java BigInteger value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the Oracle Number exponent is out of range.

    <!-- -->

    - #### bigDecimalValue

          public BigDecimal bigDecimalValue()
                                     throws SQLException

      Calls toBigDecimalto convert internal Oracle Number into a Java BigDecimal.
      Overrides:
      [`bigDecimalValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java BigDecimal value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - on over/underflow of the Oracle Number exponent and on overflow of the mantissa.

    <!-- -->

    - #### stringValue

          public String stringValue()

      Calls toString to convert internal Oracle Number to a Java String.
      Specified by:
      `stringValue` in interface `oracle.jdbc.internal.OracleNumber`

      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java String value

    <!-- -->

    - #### booleanValue

          public boolean booleanValue()

      Calls toBoolean to convert internal Oracle Number to a Java boolean.
      Overrides:
      [`booleanValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java boolean value

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Returns the JDBC representation of the datum object
      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### makeJdbcArray

          public Object makeJdbcArray(int arraySize)

      Returns a JDBC array representation of the datum
      Specified by:
      [`makeJdbcArray`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `arraySize` - size of the array

      Returns:
      an object containing the JDBC array value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC array representation results in an error

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class cls)

      Determines if the object can be converted to a particular class
      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `cls` - Class to convert to

      Returns:
      true, if conversion to cls is permitted false, if conversion to cls is not permitted

    <!-- -->

    - #### abs

          public NUMBER abs()
                     throws SQLException

      Returns a new NUMBER object initialized to the absolute value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### acos

          public NUMBER acos()
                      throws SQLException

      Returns a new NUMBER object initialized to the arc cosine value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### add

          public NUMBER add(NUMBER n)
                     throws SQLException

      Returns a new NUMBER object initialized to the value of the addition of the NUMBER value and n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### asin

          public NUMBER asin()
                      throws SQLException

      Returns a new NUMBER object initialized to the arc sine value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### atan

          public NUMBER atan()
                      throws SQLException

      Returns a new NUMBER object initialized to the arc tangent value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### atan2

          public NUMBER atan2(NUMBER x)
                       throws SQLException

      Returns a new NUMBER object initialized to the value of atan2(NUMBER/x).
      Parameters:
      `x` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### ceil

          public NUMBER ceil()
                      throws SQLException

      Returns a new NUMBER object initialized to the ceiling of NUMBER value.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### cos

          public NUMBER cos()
                     throws SQLException

      Returns a new NUMBER object initialized to the cosine value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### cosh

          public NUMBER cosh()
                      throws SQLException

      Returns a new NUMBER object initialized to the hyperbolic cosine value of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### decrement

          public NUMBER decrement()
                           throws SQLException

      Returns a new NUMBER object initialized to the NUMBER value decremented by 1. Assumption: the NUMBER value represents a positive integer
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### div

          public NUMBER div(NUMBER n)
                     throws SQLException

      Returns a new NUMBER object initialized to the division of NUMBER value by n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### exp

          public NUMBER exp()
                     throws SQLException

      Returns a new NUMBER object initialized to the value of e raised to NUMBER value.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### floatingPointRound

          public NUMBER floatingPointRound(int precision)
                                    throws SQLException

      Returns a new NUMBER object initialized to Number rounded to precision significant decimal digits.
      Parameters:
      `precision` - input precision

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### floor

          public NUMBER floor()
                       throws SQLException

      Returns a new NUMBER object initialized to the floor of NUMBER value.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### increment

          public NUMBER increment()
                           throws SQLException

      Returns a new NUMBER object initialized to the NUMBER value incremented by 1. Assumption: the NUMBER value represents a positive integer
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### ln

          public NUMBER ln()
                    throws SQLException

      Returns a new NUMBER object initialized to the natural logarithm of the NUMBER value.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### log

          public NUMBER log(NUMBER base)
                     throws SQLException

      Returns a new NUMBER object initialized to the logarithm to the base base of the NUMBER value.
      Parameters:
      `base` - Base for calculating logarithm

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### mod

          public NUMBER mod(NUMBER n)
                     throws SQLException

      Returns a new NUMBER object initialized to the remainder of the division of NUMBER/n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### mul

          public NUMBER mul(NUMBER n)
                     throws SQLException

      Returns a new NUMBER object initialized to product of NUMBER and n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### negate

          public NUMBER negate()
                        throws SQLException

      Returns a new NUMBER object initialized to the negated NUMBER value.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### pow

          public NUMBER pow(NUMBER exp)
                     throws SQLException

      Returns a new NUMBER object initialized to the value of NUMBER value raised to the exp power.
      Parameters:
      `exp` - input Oracle Number exponent

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### pow

          public NUMBER pow(int exp)
                     throws SQLException

      Returns a new NUMBER object initialized to NUMBER value raised to the exp power. exp is an integer value.
      Parameters:
      `exp` - input integral exponent

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### round

          public NUMBER round(int decimal_place)
                       throws SQLException

      Returns a new NUMBER object initialized to the NUMBER value rounded to specified decimal place decimal_place.
      Parameters:
      `decimal_place` - decimal place to round to

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### scale

          public NUMBER scale(int left,
                              int right,
                              boolean[] big)
                       throws SQLException

      Returns a new NUMBER object initialized to the value determined by the rounding performed based on the right parameter below.
      Parameters:
      `left` - maximum number of decimal digits to the left of the decimal point. It will not effect the number but big will return true if this value is exceeded.

      `right` - maximum number of decimal digits to the right of the decimal point. The number is rounded at this point. Negative values are allowed.

      `big` - set to true if the number of left-hand-side digits is exceeded and false otherwise. If big is null, it is left unset.

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### shift

          public NUMBER shift(int digits)
                       throws SQLException

      Returns a new NUMBER object initialized the NUMBER value shifted digits decimal places.
      Parameters:
      `digits` - number of decimal places to shift. Can be negative. Positive values shift the decimal place to the right and negative values to the left. For example, if NUMBER corresponds to 1234.5 and digits == -1, the new NUMBER object will correspond to 123.45.

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### sin

          public NUMBER sin()
                     throws SQLException

      Returns a new NUMBER object initialized to the sine of the NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### sinh

          public NUMBER sinh()
                      throws SQLException

      Returns a new NUMBER object initialized to the hyperbolic sine of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### sqroot

          public NUMBER sqroot()
                        throws SQLException

      Returns a new NUMBER object initialized to the square root of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### sub

          public NUMBER sub(NUMBER n)
                     throws SQLException

      Returns a new NUMBER object initialized to the difference of NUMBER and n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### tan

          public NUMBER tan()
                     throws SQLException

      Returns a new NUMBER object initialized to the tangent of NUMBER.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### tanh

          public NUMBER tanh()
                      throws SQLException

      Returns a new NUMBER object initialized to the hyperbolic tangent of Number.
      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### truncate

          public NUMBER truncate(int decimal_place)
                          throws SQLException

      Returns a new NUMBER object initialized to the NUMBER value truncated to specified decimal place decimal_place.
      Parameters:
      `decimal_place` - decimal place to truncate to

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### formattedTextToNumber

          public static NUMBER formattedTextToNumber(String num,
                                                     String fmt,
                                                     String lang)
                                              throws SQLException

      Returns a NUMBER converted from Num controlled by the format fmt.
      Parameters:
      `num` - input string representing a numeric value

      `fmt` - format string \[see "Oracle 8 Server Concepts Manual" or "CORE User's Guide Appendix D"\]

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a new NUMBER Object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### textToPrecisionNumber

          public static NUMBER textToPrecisionNumber(String num,
                                                     boolean precflag,
                                                     int preclen,
                                                     boolean scaleflag,
                                                     int scalelen,
                                                     String lang)
                                              throws SQLException

      Returns a NUMBER object initialized to the value in num as described below.
      Parameters:
      `num` - input string representing a numeric value

      `precflag` - if true, then a precision restriction should be applied

      `preclen` - the maximum number of the decimal digits the NUMBER may have, subject to the scale requirement. The number is NOT rounded if more than preclen decimal digits must be placed in the number to meet the scale requirement. ncp is set to 0 if the precision restriction is violated. preclen is ignored if precflag is false.

      `scaleflag` - if true then scale restriction should be applied

      `scalelen` - the maximum number of decimal digits to the right of the decimal point in the NUMBER Negative values are allowed. Any excess digits are rounded off, this is not reported. If enough digits are available in the input, the maximum digits will be written to the right of the decimal place even if the percussion restriction is violated. scalelen is ignored if scaleflag is false. if precision is specified but scale is not, the scale is assumed to be 0.

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a new NUMBER object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### toFormattedText

          public String toFormattedText(String fmt,
                                        String lang)
                                 throws SQLException

      Returns a new String based on the format specified in fmt and NUMBER.
      *For pure Java implementation only* Notes:

      - This method *does not* support NLS strings yet. Only ASCII.
      - Unimplemented exception is thrown for Hexadecimal & Roman Numbers

      Parameters:
      `fmt` - format string \[see "Oracle 8 Server Concepts Manual" or "CORE User's Guide Appendix D"\]

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a new String

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toText

          public String toText(int outStringLength,
                               String lang)
                        throws SQLException

      Returns a String with the unformatted representation of NUMBER.
      Parameters:
      `outStringLength` - \|outStringLength\| is the length of the result string. If outStringLength \< 0, the result string is in scientific notation.

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a new String

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### compareTo

          public int compareTo(NUMBER n)

      Returns -1 if NUMBER is less than n, 0 if NUMBER and n are equal (==), 1 if NUMBER is greater than n.
      Parameters:
      `n` - input Oracle Number

      Returns:
      integer result of comparison

    <!-- -->

    - #### isInf

          public boolean isInf()

      Returns true if NUMBER value is positive or negative infinity and a false otherwise.
      Returns:
      boolean

    <!-- -->

    - #### isNegInf

          public boolean isNegInf()

      Returns returns true if NUMBER is negative infinity and false otherwise.
      Returns:
      boolean

    <!-- -->

    - #### isPosInf

          public boolean isPosInf()

      Returns true if NUMBER is positive infinity and false otherwise.
      Returns:
      boolean

    <!-- -->

    - #### isInt

          public boolean isInt()

      Returns true if NUMBER value is finite and integral.
      Returns:
      boolean

    <!-- -->

    - #### isValid

          public static boolean isValid(byte[] num)

      Checks if a given Oracle Number is valid
      Parameters:
      `num` - input Oracle Number

      Returns:
      boolean

    <!-- -->

    - #### isZero

          public boolean isZero()

      Returns true if NUMBER is zero.
      Returns:
      boolean

    <!-- -->

    - #### e

          public static NUMBER e()

      Returns a new NUMBER object initialized to the value of e.
      Returns:
      a new NUMBER object

    <!-- -->

    - #### ln10

          public static NUMBER ln10()

      Returns a new NUMBER object initialized to the value of ln(10).
      Returns:
      a new NUMBER object

    <!-- -->

    - #### negInf

          public static NUMBER negInf()

      Returns a new NUMBER object initialized to negative infinity.
      Returns:
      a new NUMBER object

    <!-- -->

    - #### pi

          public static NUMBER pi()

      Returns a new NUMBER object initialized to the value of pi.
      Returns:
      a new NUMBER object

    <!-- -->

    - #### posInf

          public static NUMBER posInf()

      Returns a new NUMBER object initialized to positive infinity.
      Returns:
      a new NUMBER object

    <!-- -->

    - #### zero

          public static NUMBER zero()

      Returns a new NUMBER object initialized to zero.
      Returns:
      a new NUMBER object

    <!-- -->

    - #### sign

          public int sign()

      Returns -1 if the sign of NUMBER is negative, 0 if NUMBER is 0, and \> 0 if NUMBER is positive.
      Returns:
      int representing the sign

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NUMBER.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NCLOB.md)
- [Next Class](OPAQUE.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
