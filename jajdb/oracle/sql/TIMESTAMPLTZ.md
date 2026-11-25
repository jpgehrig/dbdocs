Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMPLTZ.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMP.md)
- [Next Class](TIMESTAMPTZ.md)

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

## Class TIMESTAMPLTZ

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.TIMESTAMPLTZ

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class TIMESTAMPLTZ
      extends Datum

  **TIMESTAMPLTZ Class**

  The `TIMESTAMPLTZ` class provides conversions between the Oracle Date (ldx_t) data type and Java classes `java.sql.Date`, `java.sql.Time`, `java.sql.Timestamp`

  The internal data for this object is stored as a eleven byte array in the super class' storage area. The bytes are arranged as follows:

            Byte       Represents
             0         Century (119 for 1990)
             1         Decade  (190 for 1990)
             2         Month
             3         Day
             4         Hour
             5         Minute
             6         Seconds
             7         Nanoseconds (Most Significant bit)
             8         Nanoseconds
             9         Nanoseconds
             10        Nanoseconds (Least Significant Bit)


  -We add 100 to the century and decade fields so that negative values will be positive and positive values will be higher than negative values -We add 1 to the month,hour,minute,second fields for the java objects since they start of from 0.
  Static methods are used for conversions.

  Since:
  release specific (what release of product did this appear in)

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TIMESTAMPLTZ``()`<br>Constructs a TIMESTAMPLTZ object initialized to 1/1/1970.                                                                                                                                                                                                                                                                                                                                                         |
    | `TIMESTAMPLTZ``(byte[] timestampltz)`<br>Create an Oracle TIMESTAMPLTZ object represented by the given Oracle Timestampltz                                                                                                                                                                                                                                                                                                              |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Java Date                     |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`DATE`](DATE.md)` date)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Oracle DATE                                                                                            |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Deprecated.                                                                       |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Create an Oracle TIMESTAMPLTZ object represented by the given Java Time               |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Java Timestamp |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Java Date                                                                                                                                 |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`DATE`](DATE.md)` date)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Oracle DATE                                                                                                                                                                                                        |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                           |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`DATE`](DATE.md)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                                                    |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Deprecated.                                                                                                                                                                                   |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                       |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Create an Oracle TIMESTAMPLTZ object represented by the given Java Time                                                                                                                           |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                           |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Create an Oracle TIMESTAMPLTZ object represented by the Java Timestamp                                                                                                             |
    | `TIMESTAMPLTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                             | Method and Description                                                                                                                                                                                                                                                                                                                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toDate(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java Date.                                                                                                                                                                               |
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toDate(Connection, byte\[\], Calendar) to convert internal Oracle TIMESTAMPLTZ to a Java Date.                                                          |
    | `boolean`                                                                                                     | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class                                                                                                                                                                                                              |
    | `java.time.LocalDateTime`                                                                                     | `localDateTimeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toLocalDateTime(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java LocalDateTime.                                                                                                                                                    |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                                                                                                                                                                     |
    | `java.time.OffsetDateTime`                                                                                    | `offsetDateTimeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toOffsetDateTime(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java OffsetDateTime.                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `stringValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toString(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java String.                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `stringValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toString(Connection, byte\[\], Calendar) to convert internal Oracle TIMESTAMPLTZ to a Java String.                                                    |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                                                                                                                                                                                                                                                                        |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Calls toTimestamp to convert internal Oracle TIMESTAMPLTZ to a Java Timestamp.                                                                          |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toTime to convert internal Oracle TIMESTAMPLTZ to a Java Time.                                                                                                                                                                                                     |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toTime to convert internal Oracle TIMESTAMPLTZ to a Java Time.                                                                                          |
    | `static void`                                                                                                 | `TimeZoneAdjust``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal1, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal2)`                                                |
    | `static long`                                                                                                 | `TimeZoneAdjustUTC``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal1)`                                                                                                                                                         |
    | `byte[]`                                                                                                      | `toBytes``()`<br>Convert Oracle TIMESTAMPLTZ object into a byte array                                                                                                                                                                                                                                                                                                                                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Convert Java Date to Oracle TIMESTAMPLTZ.                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal, `[`DATE`](DATE.md)` date)`<br>Convert Oracle DATE to Oracle TIMESTAMPLTZ                                                                                            |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` sess, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert Java String to Oracle TIMESTAMPLTZ.             |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Convert Java Time to Oracle TIMESTAMPLTZ.                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Convert Java Timestamp to Oracle TIMESTAMPLTZ |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                 |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`DATE`](DATE.md)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                          |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Convert Java String to Oracle TIMESTAMPLTZ.             |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                 |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                  |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Java Date Object                                                                                                                                                                          |
    | `static `[`DATE`](DATE.md)                                                                                    | `toDATE``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Oracle DATE Object                                                                                                                                                                        |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                                |
    | `static `[`DATE`](DATE.md)                                                                                    | `toDATE``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                                |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `toJdbc``()`<br>Returns the JDBC representation of the datum object                                                                                                                                                                                                                                                                                                                                      |
    | `static java.time.LocalDateTime`                                                                              | `toLocalDateTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Java LocalDateTime Object                                                                                                                                                        |
    | `static java.time.OffsetDateTime`                                                                             | `toOffsetDateTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Java OffsetDateTime Object                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Converts a TIMESTAMPLTZ to a string                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                              |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Java Time Object                                                                                                                                                                          |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                                |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Java Timestamp Object                                                                                                                                                                |
    | `static `[`TIMESTAMP`](TIMESTAMP.md)                                                                          | `toTIMESTAMP``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Oracle TIMESTAMP Object                                                                                                                                                              |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` dbtz)`<br>Deprecated.                                                                                                                           |
    | `static `[`TIMESTAMPTZ`](TIMESTAMPTZ.md)                                                                      | `toTIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestampltz)`<br>Convert a byte array representing a TIMESTAMPLTZ object to a Oracle TIMESTAMPTZ Object                                                                                                                                                          |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ()

      Constructs a TIMESTAMPLTZ object initialized to 1/1/1970.

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(byte[] timestampltz)

      Create an Oracle TIMESTAMPLTZ object represented by the given Oracle Timestampltz
      Parameters:
      `Connection` - conn

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Time time,
                              Calendar dbtz)
                       throws SQLException

      Deprecated. 
      Create an Oracle TIMESTAMPLTZ object represented by the given Java Time
      Parameters:
      `conn` - JDBC connection time Java Time object dbtz Calendar object containing Database Timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Date date,
                              Calendar dbtz)
                       throws SQLException

      Deprecated. 
      Create an Oracle TIMESTAMPLTZ object represented by the Java Date
      Parameters:
      `conn` - JDBC connection date Java Date object dbtz Calendar object containing Database Timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Timestamp timestamp,
                              Calendar dbtz)
                       throws SQLException

      Deprecated. 
      Create an Oracle TIMESTAMPLTZ object represented by the Java Timestamp
      Parameters:
      `conn` - Connection timestamp Java Timestamp object dbtz Calendar object containing Database Timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              DATE date,
                              Calendar dbtz)
                       throws SQLException

      Deprecated. 
      Create an Oracle TIMESTAMPLTZ object represented by the Oracle DATE
      Parameters:
      `conn` - JDBC connection date Oracle DATE object dbtz Calendar object containing Database Timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              String str,
                              Calendar dbtz)
                       throws SQLException

      Deprecated. 
      Create a TIMESTAMPLTZ object given a Java String object.
      Parameters:
      `conn` - JDBC connection str Java String object dbtz Calendar object containing Database Timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Calendar sess,
                              Time time)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the given Java Time
      Parameters:
      `conn` - JDBC connection sess Calendar object containing Session Timezone time Java Time object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Calendar sess,
                              Date date)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Java Date
      Parameters:
      `conn` - JDBC connection sess Calendar object containing Session Timezone date Java Date object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Calendar sess,
                              Timestamp timestamp)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Java Timestamp
      Parameters:
      `conn` - Connection sess Calendar object containing Session Timezone timestamp Java Timestamp object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Calendar sess,
                              DATE date)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Oracle DATE
      Parameters:
      `conn` - JDBC connection sess Calendar object containing Session Timezone date Oracle DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Calendar sess,
                              String str)
                       throws SQLException

      Deprecated. 
      Create a TIMESTAMPLTZ object given a Java String object.
      Parameters:
      `conn` - JDBC connection sess Calendar object containing Session Timezone str Java String object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Time time)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the given Java Time
      Parameters:
      `conn` - JDBC connection time Java Time object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Date date)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Java Date
      Parameters:
      `conn` - JDBC connection date Java Date object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              Timestamp timestamp)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Java Timestamp
      Parameters:
      `conn` - Connection timestamp Java Timestamp object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              DATE date)
                       throws SQLException

      Create an Oracle TIMESTAMPLTZ object represented by the Oracle DATE
      Parameters:
      `conn` - JDBC connection date Oracle DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPLTZ

          public TIMESTAMPLTZ(Connection conn,
                              String str)
                       throws SQLException

      Deprecated. 
      Create a TIMESTAMPLTZ object given a Java String object.
      Parameters:
      `conn` - JDBC connection str Java String object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### toDate

          public static Date toDate(Connection conn,
                                    byte[] timestampltz,
                                    Calendar dbtz)
                             throws SQLException

      Deprecated. 
      Convert a byte array representing a TIMESTAMPLTZ object to a Java Date Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object dbtz Database timezone

      Returns:
      the Java date object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTime

          public static Time toTime(Connection conn,
                                    byte[] timestampltz,
                                    Calendar dbtz)
                             throws SQLException

      Deprecated. 
      Convert a byte array representing a TIMESTAMPLTZ object to a Java Time Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object dbtz Database timezone

      Returns:
      the java.sql.Time object represented by Oracle TIMESTAMPLTZ object. Only the hour, minute and seconds are contained in the java.sql.Time object that is returned and hence callers should not attempt to access the date component of the returned object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(Connection conn,
                                              byte[] timestampltz,
                                              Calendar dbtz)
                                       throws SQLException

      Deprecated. 
      Convert a byte array representing a TIMESTAMPLTZ object to a Java Timestamp Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object dbtz Database timezone

      Returns:
      the Java timestamp object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDATE

          public static DATE toDATE(Connection conn,
                                    byte[] timestampltz,
                                    Calendar dbtz)
                             throws SQLException

      Deprecated. 
      Convert a byte array representing a TIMESTAMPLTZ object to a Oracle DATE Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object dbtz Database timezone

      Returns:
      the oracle DATE object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Connection conn,
                                          Calendar dbtz)
                                   throws SQLException

      Calls toTimestamp to convert internal Oracle TIMESTAMPLTZ to a Java Timestamp.
      Returns:
      a Java Timestamp value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Connection conn)
                                   throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toString

          public static String toString(Connection conn,
                                        byte[] timestampltz,
                                        Calendar dbtz)
                                 throws SQLException

      Deprecated. 
      Converts a TIMESTAMPLTZ to a String
      Parameters:
      `date` - a byte array

      Returns:
      String representing the date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public byte[] toBytes()

      Convert Oracle TIMESTAMPLTZ object into a byte array
      Returns:
      the byte array stored in the TIMESTAMPLTZ object

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Time time,
                                       Calendar dbtz)
                                throws SQLException

      Deprecated. 
      Convert Java Time to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC connection time java.sql.Time object to be converted. dbtz Database timezone

      Returns:
      the byte array representing the java Time.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Date date,
                                       Calendar dbtz)
                                throws SQLException

      Deprecated. 
      Convert Java Date to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC connection date java.sql.Date object to be converted. dbtz Database timezone

      Returns:
      the byte array representing the java Date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Timestamp timestamp,
                                       Calendar dbtz)
                                throws SQLException

      Deprecated. 
      Convert Java Timestamp to Oracle TIMESTAMPLTZ
      Parameters:
      `conn` - JDBC connection Timestamp java.sql.Timestamp object to be converted. dbtz database timezone

      Returns:
      the byte array representing the input date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       DATE date,
                                       Calendar dbtz)
                                throws SQLException

      Deprecated. 
      Convert Oracle DATE to Oracle TIMESTAMPLTZ
      Parameters:
      `conn` - JDBC connection date oracle.sql.DATE object to be converted. dbtz database timezone

      Returns:
      the byte array representing the Oracle DATE.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       String str,
                                       Calendar dbtz)
                                throws SQLException

      Convert Java String to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC Connection str java.lang.String object to be converted. dbtz database timezone

      Returns:
      the byte array representing the input string.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDate

          public static Date toDate(Connection conn,
                                    byte[] timestampltz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Java Date Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object

      Returns:
      the Java date object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toLocalDateTime

          public static java.time.LocalDateTime toLocalDateTime(Connection conn,
                                                                byte[] timestampltz)
                                                         throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Java LocalDateTime Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object

      Returns:
      the Java LocalDateTime object represented by the Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toOffsetDateTime

          public static java.time.OffsetDateTime toOffsetDateTime(Connection conn,
                                                                  byte[] timestampltz)
                                                           throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Java OffsetDateTime Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object

      Returns:
      the Java OffsetDateTime object represented by the Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTime

          public static Time toTime(Connection conn,
                                    byte[] timestampltz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Java Time Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object

      Returns:
      the Java time object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(Connection conn,
                                              byte[] timestampltz)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Java Timestamp Object
      Parameters:
      `conn` - JDBC connection timestamp Oracle TIMESTAMP object

      Returns:
      the Java timestamp object represented by Oracle TIMESTAMP object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDATE

          public static DATE toDATE(Connection conn,
                                    byte[] timestampltz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Oracle DATE Object
      Parameters:
      `conn` - JDBC connection timestampltz Oracle TIMESTAMPLTZ object

      Returns:
      the Oracle DATE object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTIMESTAMP

          public static TIMESTAMP toTIMESTAMP(Connection conn,
                                              byte[] timestampltz)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Oracle TIMESTAMP Object
      Parameters:
      `conn` - JDBC connection timestamp Oracle TIMESTAMPLTZ object

      Returns:
      the oracle TIMESTAMP object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTIMESTAMPTZ

          public static TIMESTAMPTZ toTIMESTAMPTZ(Connection conn,
                                                  byte[] timestampltz)
                                           throws SQLException

      Convert a byte array representing a TIMESTAMPLTZ object to a Oracle TIMESTAMPTZ Object
      Parameters:
      `conn` - JDBC connection timestamp Oracle TIMESTAMPLTZ object

      Returns:
      the oracle TIMESTAMPTZ object represented by Oracle TIMESTAMPLTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toString

          public static String toString(Connection conn,
                                        byte[] timestampltz)
                                 throws SQLException

      Converts a TIMESTAMPLTZ to a string
      Parameters:
      `date` - a byte array

      Returns:
      String representing the date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Calendar cal,
                                       Time time)
                                throws SQLException

      Convert Java Time to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC connection cal Session timezone time java.sql.Time object to be converted.

      Returns:
      the byte array representing the java Time.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Calendar cal,
                                       Date date)
                                throws SQLException

      Convert Java Date to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC connection cal Session timezone date java.sql.Date object to be converted.

      Returns:
      the byte array representing the java Date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Calendar cal,
                                       Timestamp timestamp)
                                throws SQLException

      Convert Java Timestamp to Oracle TIMESTAMPLTZ
      Parameters:
      `conn` - JDBC connection cal Session timezone Timestamp java.sql.Timestamp object to be converted.

      Returns:
      the byte array representing the input date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Calendar cal,
                                       DATE date)
                                throws SQLException

      Convert Oracle DATE to Oracle TIMESTAMPLTZ
      Parameters:
      `conn` - JDBC connection cal Session timezone date oracle.sql.DATE object to be converted.

      Returns:
      the byte array representing the Oracle DATE.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Calendar sess,
                                       String str)
                                throws SQLException

      Convert Java String to Oracle TIMESTAMPLTZ.
      Parameters:
      `conn` - JDBC Connection sess Calendar object containing Session Timezone str java.lang.String object to be converted.

      Returns:
      the byte array representing the input string.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue(Connection conn)
                             throws SQLException

      Calls toString(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java String.
      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `conn` - oracle.JDBC.OracleConnection object

      Returns:
      a Java String value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue(Connection conn,
                                    Calendar cal)
                             throws SQLException

      Calls toString(Connection, byte\[\], Calendar) to convert internal Oracle TIMESTAMPLTZ to a Java String.
      Parameters:
      `conn` - oracle.JDBC.OracleConnection object cal java.util.Calendar object

      Returns:
      a Java String value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dateValue

          public Date dateValue(Connection conn,
                                Calendar cal)
                         throws SQLException

      Calls toDate(Connection, byte\[\], Calendar) to convert internal Oracle TIMESTAMPLTZ to a Java Date.
      Parameters:
      `conn` - JDBC Connection object cal java.util.Calendar object

      Returns:
      a Java Date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dateValue

          public Date dateValue(Connection conn)
                         throws SQLException

      Calls toDate(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java Date.
      Parameters:
      `conn` - JDBC Connection object

      Returns:
      a Java Date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### localDateTimeValue

          public java.time.LocalDateTime localDateTimeValue(Connection conn)
                                                     throws SQLException

      Calls toLocalDateTime(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java LocalDateTime.
      Parameters:
      `conn` - JDBC Connection object

      Returns:
      a Java LocalDateTime

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### offsetDateTimeValue

          public java.time.OffsetDateTime offsetDateTimeValue(Connection conn)
                                                       throws SQLException

      Calls toOffsetDateTime(Connection, byte\[\]) to convert internal Oracle TIMESTAMPLTZ to a Java OffsetDateTime.
      Parameters:
      `conn` - JDBC Connection object

      Returns:
      a Java OffsetDateTime

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue(Connection conn)
                         throws SQLException

      Calls toTime to convert internal Oracle TIMESTAMPLTZ to a Java Time.
      Returns:
      a Java Time value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue(Connection conn,
                                Calendar cal)
                         throws SQLException

      Calls toTime to convert internal Oracle TIMESTAMPLTZ to a Java Time.
      Returns:
      a Java Time value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

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

    - #### TimeZoneAdjust

          public static void TimeZoneAdjust(Connection conn,
                                            Calendar cal1,
                                            Calendar cal2)
                                     throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TimeZoneAdjustUTC

          public static long TimeZoneAdjustUTC(Connection conn,
                                               Calendar cal1)
                                        throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMPLTZ.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMP.md)
- [Next Class](TIMESTAMPTZ.md)

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
