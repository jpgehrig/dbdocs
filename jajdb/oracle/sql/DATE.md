Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DATE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CustomDatumFactory.md)
- [Next Class](Datum.md)

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

## Class DATE

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.DATE

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.OracleDate

  ------------------------------------------------------------------------



      public class DATE
      extends Datum
      implements oracle.jdbc.internal.OracleDate

  **DATE Class**

  The `DATE` class provides conversions between the Oracle Date (ldx_t) data type and Java classes `java.sql.Date`, `java.sql.Time`, `java.sql.Timestamp`

  The internal data for this object is stored as a seven byte array in the super class' storage area. The bytes are arranged as follows:

            Byte       Represents
             0         Century (19 for 1990)
             1         Decade  (90 for 1990)
             2         Month
             3         Day
             4         Hour
             5         Minute
             6         Seconds


  Static methods are used for conversions.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                     |
    |-------------------|-----------------------------------------------------------|
    | `static int`      | `BDA`<br>Bad day: above range                             |
    | `static int`      | `BDAL`<br>Bad day: below range                            |
    | `static int`      | `BDT`<br>Bad date format                                  |
    | `static int`      | `BHR`<br>Bad hour: above range                            |
    | `static int`      | `BHRL`<br>Bad hour: below range                           |
    | `static int`      | `BMN`<br>Bad minute: above range                          |
    | `static int`      | `BMNL`<br>Bad minute: below range                         |
    | `static int`      | `BMO`<br>Bad month: above range                           |
    | `static int`      | `BMOL`<br>Bad month: below range                          |
    | `static int`      | `BSC`<br>Bad second: above range                          |
    | `static int`      | `BSCL`<br>Bad second: below range                         |
    | `static int`      | `BYR`<br>Bad year: above range                            |
    | `static int`      | `BYRL`<br>Bad year: below range                           |
    | `static int`      | `HRZER0`<br>Zero valued hour                              |
    | `static int`      | `MIZERO`<br>Zero valued minute                            |
    | `static int`      | `MSD`<br>Day is one of those "missing" from the year 1582 |
    | `static int`      | `SEZERO`<br>Zero valued second                            |
    | `static int`      | `YR0`<br>Year zero does not exist                         |

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DATE``()`<br>Constructs a DATE object initialized to 1/1/1970.                                                                                                                                                                                                                                                        |
    | `DATE``(byte[] date)`<br>Create a DATE object represented by the given Oracle Date.                                                                                                                                                                                                                                    |
    | `DATE``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Create a DATE object given a Java Date object.                                                                                                                                                          |
    | `DATE``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create a DATE object given a Java Date object and a Calendar                                 |
    | `DATE``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Constructs a DATE object initialized to the value specified by the object                                                                                                                           |
    | `DATE``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Constructs a DATE object initialized to the value specified by the object and a Calendar |
    | `DATE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Create a DATE object given a Java String object.                                                                                                                                                    |
    | `DATE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, boolean lenient)`<br>Create a DATE object given a Java String object.                                                                                                                                   |
    | `DATE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create a DATE object given a Java String object and a Calendar                           |
    | `DATE``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Create a DATE object given a Java Time object.                                                                                                                                                          |
    | `DATE``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create a DATE object given a Java Time object and a Calendar                                 |
    | `DATE``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Create a DATE object given a Java Timestamp object                                                                                                                                       |
    | `DATE``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create a DATE object given a Java Timestamp object and a Calendar             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                             | Method and Description                                                                                                                                                                                                                                                                                                                                                       |
    |---------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DATE`                                                                                                        | `addJulianDays``(int julianDay, int julianSec)`<br>Add Julian days to a date.                                                                                                                                                                                                                                                                                                |
    | `DATE`                                                                                                        | `addMonths``(int months)`<br>Add months to a date.                                                                                                                                                                                                                                                                                                                           |
    | `static int`                                                                                                  | `checkValidity``(byte[] date)`<br>Checks the DATE passed in.                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                         | `compareTo``(DATE date)`<br>Returns -1 if DATE is less than date, 0 if DATE and date are equal (==), 1 if DATE is greater than date.                                                                                                                                                                                                                                         |
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``()`<br>Calls toDate to convert internal Oracle DATE to a Java Date.                                                                                                                                                                                                                                                                                              |
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toDate to convert internal Oracle DATE and Calendar to a Java Date.                                                                                                                                                                        |
    | `void`                                                                                                        | `diffInJulianDays``(DATE date, int[] julianDay, int[] julianSec)`<br>Calculates the difference between two dates in Julian days.                                                                                                                                                                                                                                             |
    | [`NUMBER`](NUMBER.md)                                                                                         | `diffInMonths``(DATE date)`<br>Calculates the difference between two dates in months.                                                                                                                                                                                                                                                                                        |
    | `static DATE`                                                                                                 | `fromJulianDays``(int julianDay, int julianSec)`<br>Convert given julian days and seconds to an Oracle Date.                                                                                                                                                                                                                                                                 |
    | `static DATE`                                                                                                 | `fromText``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` datestr, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` fmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Convert a string to a DATE object. |
    | `static DATE`                                                                                                 | `getCurrentDate``()`<br>Gets current date and time                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                     | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class                                                                                                                                                                                  |
    | `DATE`                                                                                                        | `lastDayOfMonth``()`<br>returns a DATE object intialized to the last day of the month .                                                                                                                                                                                                                                                                                      |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                                                                                                                                         |
    | `static void`                                                                                                 | `numberToJulianDays``(`[`NUMBER`](NUMBER.md)` num, int[] julianDay, int[] julianSec)`<br>Converts an Oracle NUMBER to Julian days and seconds                                                                                                                                                                                                                                |
    | `static byte[]`                                                                                               | `parseFormat``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` fmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Converts the fmt string into tokens for use by toText().                                                                                   |
    | `DATE`                                                                                                        | `round``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` prec)`<br>returns a DATE object with date rounded to specified precision                                                                                                                                                                                          |
    | `DATE`                                                                                                        | `setDayOfWeek``(int day)`<br>returns a DATE object initialized to date advanced to the week of the day specified.                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `stringValue``()`<br>Calls toString to convert internal Oracle DATE to a Java String.                                                                                                                                                                                                                                                                                        |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``()`<br>Calls toTimestamp to convert internal Oracle DATE to a Java Timestamp.                                                                                                                                                                                                                                                                               |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toTimestamp to convert internal Oracle DATE and Calendar to a Java Timestamp.                                                                                                                                                         |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``()`<br>Calls toTime to convert internal Oracle DATE to a Java Time.                                                                                                                                                                                                                                                                                              |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toTime to convert internal Oracle DATE and Calendar to a Java Time.                                                                                                                                                                        |
    | `byte[]`                                                                                                      | `toBytes``()`                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte[]`                                                                                               | `toBytes``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Convert Java Date to Oracle DATE.                                                                                                                                                                                                                          |
    | `static byte[]`                                                                                               | `toBytes``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Date and Calendar to Oracle DATE.                                                                                                  |
    | `static byte[]`                                                                                               | `toBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert Java String to Oracle DATE.                                                                                                                                                                                                                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java String to Oracle DATE.                                                                                                         |
    | `static byte[]`                                                                                               | `toBytes``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Convert Java Time to Oracle DATE.                                                                                                                                                                                                                          |
    | `static byte[]`                                                                                               | `toBytes``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Time and Calendar to Oracle DATE.                                                                                                  |
    | `static byte[]`                                                                                               | `toBytes``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Convert Java Timestamp to Oracle DATE.                                                                                                                                                                                                      |
    | `static byte[]`                                                                                               | `toBytes``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Timestamp and Calendar to Oracle DATE.                                                                              |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(byte[] date)`<br>Convert Oracle DATE to Java Date.                                                                                                                                                                                                                                                                                                                 |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(byte[] date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Oracle DATE and Calendar to Java Date.                                                                                                                                                                                         |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `toJdbc``()`<br>Returns the JDBC representation of the datum object                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                        | `toJulianDays``(int[] julianDay, int[] julianSec)`<br>Convert to Julian days and seconds from the given date.                                                                                                                                                                                                                                                                |
    | [`NUMBER`](NUMBER.md)                                                                                         | `toNumber``()`<br>Converts date to an Oracle Number.                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `toString``()`                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``(byte[] bytes)`<br>Converts a DATE to a string                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `toText``(byte[] pfmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Convert date to text as specified by fmt.                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `toText``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` fmt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Convert date to text as specified by fmt.                                                                                                       |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(byte[] date)`<br>Convert Oracle DATE to Java Time.                                                                                                                                                                                                                                                                                                                 |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(byte[] date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Oracle DATE and Calendar to Java Time.                                                                                                                                                                                         |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(byte[] date)`<br>Convert Oracle DATE to Java Timestamp.                                                                                                                                                                                                                                                                                                       |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(byte[] date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Oracle DATE and Calendar to Java Timestamp.                                                                                                                                                                               |
    | `DATE`                                                                                                        | `truncate``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` prec)`<br>returns a DATE object with date truncated to specified precision                                                                                                                                                                                     |
    | `DATE`                                                                                                        | `zeroTime``()`<br>Zero out the time from a DATE object.                                                                                                                                                                                                                                                                                                                      |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDate

      `from, from`

<!-- -->

- - ### Field Detail

    - #### BDA

          public static final int BDA

      Bad day: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BDAL

          public static final int BDAL

      Bad day: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BMO

          public static final int BMO

      Bad month: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BMOL

          public static final int BMOL

      Bad month: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BYR

          public static final int BYR

      Bad year: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BYRL

          public static final int BYRL

      Bad year: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BHR

          public static final int BHR

      Bad hour: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BHRL

          public static final int BHRL

      Bad hour: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BMN

          public static final int BMN

      Bad minute: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BMNL

          public static final int BMNL

      Bad minute: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BSC

          public static final int BSC

      Bad second: above range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BSCL

          public static final int BSCL

      Bad second: below range
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MSD

          public static final int MSD

      Day is one of those "missing" from the year 1582
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### YR0

          public static final int YR0

      Year zero does not exist
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BDT

          public static final int BDT

      Bad date format
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### HRZER0

          public static final int HRZER0

      Zero valued hour
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MIZERO

          public static final int MIZERO

      Zero valued minute
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SEZERO

          public static final int SEZERO

      Zero valued second
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### DATE

          public DATE()

      Constructs a DATE object initialized to 1/1/1970.

    <!-- -->

    - #### DATE

          public DATE(byte[] date)

      Create a DATE object represented by the given Oracle Date.
      Parameters:
      `date` - Oracle DATE

    <!-- -->

    - #### DATE

          public DATE(Date date)

      Create a DATE object given a Java Date object.
      Parameters:
      `date` - Java Date object

    <!-- -->

    - #### DATE

          public DATE(Time time)

      Create a DATE object given a Java Time object.
      Parameters:
      `time` - Java Time object

    <!-- -->

    - #### DATE

          public DATE(Timestamp timestamp)

      Create a DATE object given a Java Timestamp object
      Parameters:
      `timestamp` - Java Timestamp object

    <!-- -->

    - #### DATE

          public DATE(Date date,
                      Calendar cal)

      Create a DATE object given a Java Date object and a Calendar
      Parameters:
      `date` - Java Date object

      `cal` - Java Calendar object which encapsulates the timezone information of date

    <!-- -->

    - #### DATE

          public DATE(Time time,
                      Calendar cal)

      Create a DATE object given a Java Time object and a Calendar
      Parameters:
      `time` - Java Time object

      `cal` - Java Calendar object which encapsulates the timezone information of time

    <!-- -->

    - #### DATE

          public DATE(Timestamp timestamp,
                      Calendar cal)

      Create a DATE object given a Java Timestamp object and a Calendar
      Parameters:
      `timestamp` - Java Timestamp object

      `cal` - Java Calendar object which encapsulates the timezone information of timestamp

    <!-- -->

    - #### DATE

          public DATE(String str)

      Create a DATE object given a Java String object.
      Parameters:
      `str` - Java String object

    <!-- -->

    - #### DATE

          public DATE(String str,
                      boolean lenient)
               throws ParseException

      Create a DATE object given a Java String object.
      Parameters:
      `str` - Java String object

      `lenient` - Java Boolean variable

      Throws:
      [`ParseException`](http://download.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true)

    <!-- -->

    - #### DATE

          public DATE(String str,
                      Calendar cal)

      Create a DATE object given a Java String object and a Calendar
      Parameters:
      `str` - Java String object

      `cal` - Java Calendar object which encapsulates the timezone information for interpreting str

    <!-- -->

    - #### DATE

          public DATE(Object obj)
               throws SQLException

      Constructs a DATE object initialized to the value specified by the object
      Parameters:
      `obj` - Object value

      `obj` - Object value

      `obj` - Object value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if initialization is not allowed

    <!-- -->

    - #### DATE

          public DATE(Object obj,
                      Calendar cal)
               throws SQLException

      Constructs a DATE object initialized to the value specified by the object and a Calendar
      Parameters:
      `obj` - Object value

      `cal` - Calendar to use

      `obj` - Object value

      `obj` - Object value

      `cal` - Calendar which encapsulates the timezone information of obj

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if initialization is not allowed

  <!-- -->

  - ### Method Detail

    - #### toDate

          public static Date toDate(byte[] date)

      Convert Oracle DATE to Java Date.
      Parameters:
      `date` - Oracle DATE to be converted

      Returns:
      the java.sql.Date object represented by the Oracle DATE date.

    <!-- -->

    - #### toTime

          public static Time toTime(byte[] date)

      Convert Oracle DATE to Java Time.
      Parameters:
      `date` - Oracle DATE to be converted

      Returns:
      the java.sql.Time object represented by the Oracle DATE date.

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(byte[] date)

      Convert Oracle DATE to Java Timestamp.
      Parameters:
      `date` - Oracle DATE to be converted

      Returns:
      the java.sql.Timestamp object represented by the Oracle DATE date.

    <!-- -->

    - #### toDate

          public static Date toDate(byte[] date,
                                    Calendar cal)

      Convert Oracle DATE and Calendar to Java Date.
      Parameters:
      `date` - Oracle DATE to be converted

      `cal` - Calendar which encapsulates the timezone information to be used to create Date object

      Returns:
      the java.sql.Date object represented by the Oracle DATE date.

    <!-- -->

    - #### toTime

          public static Time toTime(byte[] date,
                                    Calendar cal)

      Convert Oracle DATE and Calendar to Java Time.
      Parameters:
      `date` - Oracle DATE to be converted

      `cal` - Calendar which encapsulates the timezone information to be used to create the Time object

      Returns:
      the java.sql.Time object represented by the Oracle DATE date.

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(byte[] date,
                                              Calendar cal)

      Convert Oracle DATE and Calendar to Java Timestamp.
      Parameters:
      `date` - Oracle DATE to be converted

      `cal` - Calendar which encapsulates the timezone information to be used to create the Timestamp object

      Returns:
      the java.sql.Timestamp object represented by the Oracle DATE date.

    <!-- -->

    - #### toString

          public static String toString(byte[] bytes)

      Converts a DATE to a string
      Specified by:
      `toString` in interface `oracle.jdbc.internal.OracleDate`

      Parameters:
      `date` - a byte array

      Returns:
      String representing the date

    <!-- -->

    - #### toBytes

          public byte[] toBytes()

      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleDate`

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Date date)

      Convert Java Date to Oracle DATE.
      Parameters:
      `date` - java.sql.Date object to be converted.

      Returns:
      the byte array representing the input date.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Time time)

      Convert Java Time to Oracle DATE.
      Parameters:
      `time` - java.sql.Time object to be converted.

      Returns:
      the byte array representing the input time.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Timestamp timestamp)

      Convert Java Timestamp to Oracle DATE.
      Parameters:
      `timestamp` - java.sql.Timestamp object to be converted.

      Returns:
      the byte array representing the input timestamp.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Date date,
                                       Calendar cal)

      Convert Java Date and Calendar to Oracle DATE.
      Parameters:
      `date` - java.sql.Date object to be converted.

      `cal` - java.util.Calendar object which encapsulates the timezone information of date

      Returns:
      the byte array representing the input date.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Time time,
                                       Calendar cal)

      Convert Java Time and Calendar to Oracle DATE.
      Parameters:
      `time` - java.sql.Time object to be converted.

      `cal` - java.util.Calendar object which encapsulates the timezone information of time

      Returns:
      the byte array representing the input time.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Timestamp timestamp,
                                       Calendar cal)

      Convert Java Timestamp and Calendar to Oracle DATE.
      Parameters:
      `timestamp` - java.sql.Timestamp object to be converted.

      `cal` - java.util.Calendar object which encapsulates the timezone information of date

      Returns:
      the byte array representing the input timestamp.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(String str)

      Convert Java String to Oracle DATE.
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleDate`

      Parameters:
      `str` - java.lang.String object to be converted.

      Returns:
      the byte array representing the input string.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(String str,
                                       Calendar cal)

      Convert Java String to Oracle DATE.
      Parameters:
      `str` - java.lang.String object to be converted.

      `cal` - java.util.Calendar object which encapsulates the timezone information for interpreting str

      Returns:
      the byte array representing the input string.

    <!-- -->

    - #### dateValue

          public Date dateValue()

      Calls toDate to convert internal Oracle DATE to a Java Date.
      Overrides:
      [`dateValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Date value

    <!-- -->

    - #### timeValue

          public Time timeValue()

      Calls toTime to convert internal Oracle DATE to a Java Time.
      Overrides:
      [`timeValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Time value

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue()

      Calls toTimestamp to convert internal Oracle DATE to a Java Timestamp.
      Overrides:
      [`timestampValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Timestamp value

    <!-- -->

    - #### dateValue

          public Date dateValue(Calendar cal)

      Calls toDate to convert internal Oracle DATE and Calendar to a Java Date.
      Parameters:
      `cal` - Calendar to use

      Returns:
      a Java Date value

    <!-- -->

    - #### timeValue

          public Time timeValue(Calendar cal)

      Calls toTime to convert internal Oracle DATE and Calendar to a Java Time.
      Overrides:
      [`timeValue`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `cal` - Calendar to use

      Returns:
      a Java Time value

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Calendar cal)

      Calls toTimestamp to convert internal Oracle DATE and Calendar to a Java Timestamp.
      Overrides:
      [`timestampValue`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `cal` - Calendar to use

      Returns:
      a Java Timestamp value

    <!-- -->

    - #### stringValue

          public String stringValue()

      Calls toString to convert internal Oracle DATE to a Java String.
      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java String value

    <!-- -->

    - #### toString

          public String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

    <!-- -->

    - #### toJdbc

          public Object toJdbc()

      Returns the JDBC representation of the datum object
      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

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

    - #### addJulianDays

          public DATE addJulianDays(int julianDay,
                                    int julianSec)
                             throws SQLException

      Add Julian days to a date.
      Parameters:
      `julianDay` - Number of Julian days to add to DATE

      `julianSec` - Number of seconds past midnight

      Returns:
      new DATE object initalized to the DATE values added to the Julian days.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### addMonths

          public DATE addMonths(int months)
                         throws SQLException

      Add months to a date.
      Parameters:
      `months` - integral months to add to date

      Returns:
      new DATE object initialized to the DATE value added to months. months can be negative to perform month subtraction.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### zeroTime

          public DATE zeroTime()
                        throws SQLException

      Zero out the time from a DATE object.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### diffInJulianDays

          public void diffInJulianDays(DATE date,
                                       int[] julianDay,
                                       int[] julianSec)
                                throws SQLException

      Calculates the difference between two dates in Julian days.
      Parameters:
      `date` - Date to be subtracted.

      `julianDay` - Number of Julian days

      `julianSec` - Number of seconds past midnight

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### diffInMonths

          public NUMBER diffInMonths(DATE date)
                              throws SQLException

      Calculates the difference between two dates in months.
      Parameters:
      `date` - Date to be subtracted.

      Returns:
      NUMBER difference in months as an Oracle Number.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### getCurrentDate

          public static DATE getCurrentDate()
                                     throws SQLException

      Gets current date and time
      Returns:
      DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### checkValidity

          public static int checkValidity(byte[] date)
                                   throws SQLException

      Checks the DATE passed in.
      Parameters:
      `date` - Date to be checked

      Returns:
      0 if the date is valid or the ORed representations in the following table:

      |        |                                                  |
      |--------|--------------------------------------------------|
      | BDA    | Bad day: above range                             |
      | BDAL   | Bad day: below range                             |
      | BMO    | Bad month: above range                           |
      | BMOL   | Bad month: below range                           |
      | BYR    | Bad year: above range                            |
      | BYRL   | Bad year: below range                            |
      | BHR    | Bad hour: above range                            |
      | BHRL   | Bad hour: below range                            |
      | BMN    | Bad minute: above range                          |
      | BMNL   | Bad minute: below range                          |
      | BSC    | Bad second: above range                          |
      | BSCL   | Bad second: below range                          |
      | MSD    | Day is one of those "missing" from the year 1582 |
      | YR0    | Year zero does not exist                         |
      | BDT    | Bad date format                                  |
      | HRZERO | Zero valued hour                                 |
      | MIZERO | Zero valued minute                               |
      | SEZERO | Zero valued second                               |

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### fromJulianDays

          public static DATE fromJulianDays(int julianDay,
                                            int julianSec)
                                     throws SQLException

      Convert given julian days and seconds to an Oracle Date.
      Parameters:
      `julianDay` - Number of Julian days

      `julianSec` - Number of seconds past midnight

      Returns:
      new DATE object initialized based on the number of Julian days.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### fromText

          public static DATE fromText(String datestr,
                                      String fmt,
                                      String lang)
                               throws SQLException

      Convert a string to a DATE object.
      Parameters:
      `datestr` - Input Date string

      `fmt` - Date Format

      `lang` - Input date language

      Returns:
      DATE object **Note:** Some of the extended Date Formats supported by the C Date libraries from CORE are not supported in this pure Java equivalent implementation. The Format strings supported are:

      | String        | Meaning                                                                                                                                                                                                 |
      |---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | a.d.          | B.C./A.D. indicator                                                                                                                                                                                     |
      | a.m.          | A.M./P.M. indicator                                                                                                                                                                                     |
      | ad            | BC/AD indicator                                                                                                                                                                                         |
      | am            | AM/PM indicator                                                                                                                                                                                         |
      | b.c.          | B.C./A.D. indicator                                                                                                                                                                                     |
      | bc            | BC/AD indicator                                                                                                                                                                                         |
      | d             | day of the week                                                                                                                                                                                         |
      | day           | name of the day, spelled out                                                                                                                                                                            |
      | dd            | day of the month                                                                                                                                                                                        |
      | ddd           | day of year                                                                                                                                                                                             |
      | dy            | name of weekday abbreviated                                                                                                                                                                             |
      | hh            | hour representation in 12 hour format                                                                                                                                                                   |
      | hh24          | hour representation in 24 hour format                                                                                                                                                                   |
      | mi            | minutes                                                                                                                                                                                                 |
      | mm            | two digit month representation                                                                                                                                                                          |
      | mon           | month abbreviation                                                                                                                                                                                      |
      | month         | name of the month, spelled out                                                                                                                                                                          |
      | p.m.          | A.M./P.M. indicator                                                                                                                                                                                     |
      | pm            | AM/PM indicator                                                                                                                                                                                         |
      | ss            | two digit second representation                                                                                                                                                                         |
      | Y             | last digit of the year                                                                                                                                                                                  |
      | YY            | last two digits of a year                                                                                                                                                                               |
      | YYY           | last three digits of a year                                                                                                                                                                             |
      | YYYY          | year                                                                                                                                                                                                    |
      | "\<literal\>" | all text in quotes is copied into the output string It is not possible to place a quote character into the output string. On input, literal text is a placeholder for another string of the same length |
      | /,%&@#..      | punctuation (non-alphanumeric characters) is treated exactly like a literal without the need for quotes.                                                                                                |

      The Date format string **not** supported versus the C library are:

      | String | Meaning                                                                                                                                                                                                                                   |
      |--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | E      | abbreviated era name                                                                                                                                                                                                                      |
      | EE     | full era name                                                                                                                                                                                                                             |
      | FX     | all date literals must be an exact match                                                                                                                                                                                                  |
      | j      | Julian day                                                                                                                                                                                                                                |
      | RM     | Roman numeral month (I-XII)                                                                                                                                                                                                               |
      | RR     | Round year with two digits (on input, rounds the century up one if the year is \<50 and the reference date is \>= 50, and down one century if the year is \>= 50 and the reference date is \<50)                                          |
      | RRRR   | Round year (on input, accepts either four digit input or, for two digit input, rounds the century up one if the year is \<50 and the reference date is \>= 50, and down one century if the year is \>= 50 and the reference date is \<50) |
      | sssss  | number of seconds past midnight                                                                                                                                                                                                           |
      | sy,yyy | signed year (BC dates have "-" in front)                                                                                                                                                                                                  |
      | syYYY  | signed year (BC dates have "-" in front)                                                                                                                                                                                                  |
      | Y,YYY  | year with comma                                                                                                                                                                                                                           |
      | YEAR   | year number spelled out                                                                                                                                                                                                                   |

      Also parsing is strict i.e. spaces and literals should match the format string exactly. (except for a.d./b.c. the string should be ad/bc)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### lastDayOfMonth

          public DATE lastDayOfMonth()
                              throws SQLException

      returns a DATE object intialized to the last day of the month .
      Returns:
      a DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### numberToJulianDays

          public static void numberToJulianDays(NUMBER num,
                                                int[] julianDay,
                                                int[] julianSec)
                                         throws SQLException

      Converts an Oracle NUMBER to Julian days and seconds
      Parameters:
      `num` - Oracle Number to convert

      `julianDay` - Number of Julian days

      `julianSec` - Number of seconds past midnight

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### round

          public DATE round(String prec)
                     throws SQLException

      returns a DATE object with date rounded to specified precision
      Parameters:
      `prec` - precision to use while rounding

      Returns:
      DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### setDayOfWeek

          public DATE setDayOfWeek(int day)
                            throws SQLException

      returns a DATE object initialized to date advanced to the week of the day specified.
      Parameters:
      `day` - day of the week the date needs to be advanced

      Returns:
      DATE object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### toJulianDays

          public void toJulianDays(int[] julianDay,
                                   int[] julianSec)
                            throws SQLException

      Convert to Julian days and seconds from the given date.
      Parameters:
      `julianDay` - Number of Julian days

      `julianSec` - Number of seconds past midnight

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### toNumber

          public NUMBER toNumber()
                          throws SQLException

      Converts date to an Oracle Number.
      Returns:
      an Oracle Number

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### toText

          public String toText(String fmt,
                               String lang)
                        throws SQLException

      Convert date to text as specified by fmt.
      Parameters:
      `fmt` - date format

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a String converted from date via format fmt.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available or an invalid format string is provided.

    <!-- -->

    - #### toText

          public String toText(byte[] pfmt,
                               String lang)
                        throws SQLException

      Convert date to text as specified by fmt.
      Parameters:
      `pfmt` - date format parsed by parseFormat

      `lang` - the NLS language the conversion is to be performed in, null indicates use default.

      Returns:
      a String converted from date via format fmt.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available or an invalid format string is provided.

    <!-- -->

    - #### parseFormat

          public static byte[] parseFormat(String fmt,
                                           String lang)
                                    throws SQLException

      Converts the fmt string into tokens for use by toText().
      Parameters:
      `fmt` - date format

      `lang` - A String containing NLS Language and/or Territory null indicates to use default.

      Returns:
      a byte array containing tokens from the parsed format

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the format string can not be parsed.

    <!-- -->

    - #### truncate

          public DATE truncate(String prec)
                        throws SQLException

      returns a DATE object with date truncated to specified precision
      Parameters:
      `prec` - precision to use while truncating

      Returns:
      DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Java implementation is not available

    <!-- -->

    - #### compareTo

          public int compareTo(DATE date)

      Returns -1 if DATE is less than date, 0 if DATE and date are equal (==), 1 if DATE is greater than date.
      Parameters:
      `date` - input Oracle Date

      Returns:
      integer result of comparison

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DATE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CustomDatumFactory.md)
- [Next Class](Datum.md)

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
