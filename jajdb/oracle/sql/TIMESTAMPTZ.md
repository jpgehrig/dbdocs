Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMPTZ.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMPLTZ.md)
- [Next Class](TypeDescriptor.md)

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

## Class TIMESTAMPTZ

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.TIMESTAMPTZ

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.OracleTimestampWithTimeZone

  ------------------------------------------------------------------------



      public class TIMESTAMPTZ
      extends Datum
      implements oracle.jdbc.internal.OracleTimestampWithTimeZone

  **TIMESTAMPTZ Class**

  The `TIMESTAMPTZ` class provides conversions between the Oracle Date (ldx_t) data type and Java classes `java.sql.Date`, `java.sql.Time`, `java.sql.Timestamp`

  The internal data for this object is stored as a thirteen byte array in the super class' storage area. The bytes are arranged as follows:

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
             11,12     Region id or Timezone Hour/Minute


  The timezone information is stored as an offset in the RegionID format or in the HOUR/MINUTE format
  Static methods are used for conversions.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TIMESTAMPTZ``()`<br>Constructs a TIMESTAMPTZ object initialized to 1/1/1970.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `TIMESTAMPTZ``(byte[] timestamptz)`<br>Create an Oracle TIMESTAMPTZ object represented by the given Oracle Timestamptz                                                                                                                                                                                                                                                                                                                                            |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Create an Oracle TIMESTAMPTZ object represented by the Java Date                                                                                                                                                             |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`DATE`](DATE.md)` date)`<br>Create an Oracle TIMESTAMPTZ object represented by the Oracle DATE                                                                                                                                                                                                                                    |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create an Oracle TIMESTAMPTZ object represented by the Java Date and the Java Calendar object                     |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Create a TIMESTAMPTZ object given a Java String object.                                                                                                                                                                  |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create a TIMESTAMPTZ object given a Java String object.                                                       |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Create an Oracle TIMESTAMPTZ object represented by the given Java Time                                                                                                                                                       |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create an Oracle TIMESTAMPTZ object represented by the given Java Time and the Java Calendar object               |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp                                                                                                                                         |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp and the Java Calendar object |
    | `TIMESTAMPTZ``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, java.time.ZoneId tzid)`<br>Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp with the specified ZoneId.                                                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                             | Method and Description                                                                                                                                                                                                                                                                                                                                                                                  |
    |---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toDate to convert internal Oracle TIMESTAMPTZ to a Java Date.                                                                                                                                                                                                     |
    | [`TimeZone`](http://download.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)           | `getTimeZone``()`                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                     | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class                                                                                                                                                                                                             |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                                                                                                                                                                    |
    | `java.time.OffsetDateTime`                                                                                    | `offsetDateTimeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toOffsetDateTime to convert internal Oracle TIMESTAMPTZ to a Java OffsetDateTime.                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `stringValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toString to convert internal Oracle TIMESTAMPTZ to a Java String.                                                                                                                                                                                               |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toTimestamp to convert internal Oracle Date to a Java Timestamp.                                                                                                                                                                                             |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Calls toTime to convert internal Oracle Date to a Java Time.                                                                                                                                                                                                            |
    | `byte[]`                                                                                                      | `toBytes``()`<br>Convert Oracle Timestamptz object into a byte array                                                                                                                                                                                                                                                                                                                                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Convert Java Date to Oracle TIMESTAMPTZ.                                                                                                                               |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`DATE`](DATE.md)` date)`<br>Convert Oracle DATE to Oracle TIMESTAMPTZ                                                                                                                                                                                                       |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Date to Oracle TIMESTAMPTZ.                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert Java String to Oracle TIMESTAMPTZ.                                                                                                                         |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java String to Oracle TIMESTAMPTZ.              |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Convert Java Time to Oracle TIMESTAMPTZ.                                                                                                                               |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Time to Oracle TIMESTAMPTZ.                    |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Convert Java Timestamp to Oracle TIMESTAMPTZ                                                                                                            |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Timestamp to Oracle TIMESTAMPTZ |
    | `static byte[]`                                                                                               | `toBytes``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, java.time.ZoneId tzid)`<br>Convert Java Timestamp to Oracle TIMESTAMPTZ                                                                                     |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Java Date Object                                                                                                                                                                           |
    | `static `[`DATE`](DATE.md)                                                                                    | `toDATE``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Oracle DATE Object                                                                                                                                                                         |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate2``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Java Date Object in accordance with java.sql.Date specification.                                                                                                                          |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `toJdbc``()`<br>Returns the JDBC representation of the timestamptz object                                                                                                                                                                                                                                                                                                                               |
    | `static java.time.OffsetDateTime`                                                                             | `toOffsetDateTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Converts a TIMESTAMPTZ to an OffsetDateTime                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Converts a TIMESTAMPTZ to a string                                                                                                                                                                                                                   |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Java Time Object                                                                                                                                                                           |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMP WITH TIME ZONE object to a Java Timestamp Object                                                                                                                                                    |
    | `static `[`TIMESTAMP`](TIMESTAMP.md)                                                                          | `toTIMESTAMP``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Oracle TIMESTAMP Object                                                                                                                                                               |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp2``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, byte[] timestamptz)`<br>Convert a byte array representing a TIMESTAMPTZ object to a Java Timestamp Object                                                                                                                                                                |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleTimestampWithTimeZone

      `from, from`

<!-- -->

- - ### Constructor Detail

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ()

      Constructs a TIMESTAMPTZ object initialized to 1/1/1970.

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(byte[] timestamptz)

      Create an Oracle TIMESTAMPTZ object represented by the given Oracle Timestamptz
      Parameters:
      `timestamptz` - Oracle TIMESTAMPTZ

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Date date)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Java Date
      Parameters:
      `conn` - JDBC connection date Java Date object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Date date,
                             Calendar cal)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Java Date and the Java Calendar object
      Parameters:
      `conn` - JDBC connection date Java Date object cal java Calendar object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Time time)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the given Java Time
      Parameters:
      `conn` - JDBC connection time Java Time object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Time time,
                             Calendar cal)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the given Java Time and the Java Calendar object
      Parameters:
      `conn` - JDBC connection time Java Time object cal java Calendar object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Timestamp timestamp)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Timestamp timestamp,
                             Calendar cal)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp and the Java Calendar object
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object cal Java Calendar object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             Timestamp timestamp,
                             java.time.ZoneId tzid)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Java Timestamp with the specified ZoneId.
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object tzidstamp Java ZoneId object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             DATE date)
                      throws SQLException

      Create an Oracle TIMESTAMPTZ object represented by the Oracle DATE
      Parameters:
      `conn` - JDBC connection date Oracle DATE object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             String str)
                      throws SQLException

      Create a TIMESTAMPTZ object given a Java String object.
      Parameters:
      `conn` - JDBC connection str Java String object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TIMESTAMPTZ

          public TIMESTAMPTZ(Connection conn,
                             String str,
                             Calendar cal)
                      throws SQLException

      Create a TIMESTAMPTZ object given a Java String object.
      Parameters:
      `conn` - JDBC connection str Java String object cal Calendar object encapsulating the timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### toDate

          public static Date toDate(Connection conn,
                                    byte[] timestamptz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Java Date Object
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the Java Date object represented by Oracle TIMESTAMPTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDate2

          public static Date toDate2(Connection conn,
                                     byte[] timestamptz)
                              throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Java Date Object in accordance with java.sql.Date specification.
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object in byte array

      Returns:
      the Java Date object represented by Oracle TIMESTAMPTZ object as per java.sql.Date standards. i.e w.r.t GMT timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTime

          public static Time toTime(Connection conn,
                                    byte[] timestamptz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Java Time Object
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the java.sql.Time object represented by Oracle TIMESTAMPTZ object. Only the hour, minute and seconds are contained in the java.sql.Time object that is returned and hence callers should not attempt to access the date component of the returned object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDATE

          public static DATE toDATE(Connection conn,
                                    byte[] timestamptz)
                             throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Oracle DATE Object
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the oracle DATE object represented by Oracle TIMESTAMPTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTIMESTAMP

          public static TIMESTAMP toTIMESTAMP(Connection conn,
                                              byte[] timestamptz)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Oracle TIMESTAMP Object
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the Oracle TIMESTAMP object represented by Oracle TIMESTAMPTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(Connection conn,
                                              byte[] timestamptz)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMP WITH TIME ZONE object to a Java Timestamp Object
      Specified by:
      `toTimestamp` in interface `oracle.jdbc.internal.OracleTimestampWithTimeZone`

      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the Java Timestamp object represented by Oracle TIMESTAMPTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp2

          public static Timestamp toTimestamp2(Connection conn,
                                               byte[] timestamptz)
                                        throws SQLException

      Convert a byte array representing a TIMESTAMPTZ object to a Java Timestamp Object
      Parameters:
      `conn` - JDBC connection timestamptz Oracle TIMESTAMPTZ object

      Returns:
      the Java Timestamp object represented by Oracle TIMESTAMPTZ object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toString

          public static String toString(Connection conn,
                                        byte[] timestamptz)
                                 throws SQLException

      Converts a TIMESTAMPTZ to a string
      Specified by:
      `toString` in interface `oracle.jdbc.internal.OracleTimestampWithTimeZone`

      Parameters:
      `timestamptz` - a byte array

      Returns:
      String representing the TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toOffsetDateTime

          public static java.time.OffsetDateTime toOffsetDateTime(Connection conn,
                                                                  byte[] timestamptz)
                                                           throws SQLException

      Converts a TIMESTAMPTZ to an OffsetDateTime
      Parameters:
      `timestamptz` - a byte array

      Returns:
      OffsetDateTime representing the TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Connection conn)
                                   throws SQLException

      Calls toTimestamp to convert internal Oracle Date to a Java Timestamp.
      Returns:
      a Java Timestamp value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public byte[] toBytes()

      Convert Oracle Timestamptz object into a byte array
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleTimestampWithTimeZone`

      Returns:
      the byte array stored in the TIMESTAMPTZ object

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Date date)
                                throws SQLException

      Convert Java Date to Oracle TIMESTAMPTZ.
      Parameters:
      `conn` - JDBC connection date Java Date object

      Returns:
      the byte array representing the java Date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Date date,
                                       Calendar cal)
                                throws SQLException

      Convert Java Date to Oracle TIMESTAMPTZ.
      Parameters:
      `conn` - JDBC connection date Java Date object cal java Calendar object

      Returns:
      the byte array representing the java Date.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Time time)
                                throws SQLException

      Convert Java Time to Oracle TIMESTAMPTZ.
      Parameters:
      `conn` - JDBC connection time Java Time object

      Returns:
      the byte array representing the java Time.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Time time,
                                       Calendar cal)
                                throws SQLException

      Convert Java Time to Oracle TIMESTAMPTZ.
      Parameters:
      `conn` - JDBC connection time Java Time object cal java Calendar object

      Returns:
      the byte array representing the java Time.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Timestamp timestamp)
                                throws SQLException

      Convert Java Timestamp to Oracle TIMESTAMPTZ
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object

      Returns:
      the byte array representing the TIMESTAMPTZ object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Timestamp timestamp,
                                       Calendar cal)
                                throws SQLException

      Convert Java Timestamp to Oracle TIMESTAMPTZ
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object cal Java Calendar object

      Returns:
      the byte array representing the TIMESTAMPTZ object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       Timestamp timestamp,
                                       java.time.ZoneId tzid)
                                throws SQLException

      Convert Java Timestamp to Oracle TIMESTAMPTZ
      Parameters:
      `conn` - JDBC connection timestamp Java Timestamp object tzid Java ZoneId object

      Returns:
      the byte array representing the TIMESTAMPTZ object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       DATE date)
                                throws SQLException

      Convert Oracle DATE to Oracle TIMESTAMPTZ
      Parameters:
      `conn` - JDBC connection date Oracle DATE object

      Returns:
      the byte array representing the Oracle TIMESTAMPTZ.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       String str)
                                throws SQLException

      Convert Java String to Oracle TIMESTAMPTZ.
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleTimestampWithTimeZone`

      Parameters:
      `conn` - JDBC Connection str java.lang.String object to be converted.

      Returns:
      the byte array representing the input string.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Connection conn,
                                       String str,
                                       Calendar cal)
                                throws SQLException

      Convert Java String to Oracle TIMESTAMPTZ.
      Parameters:
      `conn` - JDBC Connection str java.lang.String object to be converted. cal Calendar object encapsulating the timezone

      Returns:
      the byte array representing the input string.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue(Connection conn)
                             throws SQLException

      Calls toString to convert internal Oracle TIMESTAMPTZ to a Java String.
      Specified by:
      `stringValue` in interface `oracle.jdbc.internal.OracleTimestampWithTimeZone`

      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `conn` - oracle.JDBC.OracleConnection object

      Returns:
      a Java String value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### offsetDateTimeValue

          public java.time.OffsetDateTime offsetDateTimeValue(Connection conn)
                                                       throws SQLException

      Calls toOffsetDateTime to convert internal Oracle TIMESTAMPTZ to a Java OffsetDateTime.
      Parameters:
      `a` - JDBC Connection object

      Returns:
      a Java OffsetDateTime

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dateValue

          public Date dateValue(Connection conn)
                         throws SQLException

      Calls toDate to convert internal Oracle TIMESTAMPTZ to a Java Date.
      Parameters:
      `a` - JDBC Connection object

      Returns:
      a Java Date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue(Connection conn)
                         throws SQLException

      Calls toTime to convert internal Oracle Date to a Java Time.
      Returns:
      a Java Time value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTimeZone

          public TimeZone getTimeZone()
                               throws SQLException

      Returns:
      the TimeZone of this value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Returns the JDBC representation of the timestamptz object
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

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMPTZ.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMPLTZ.md)
- [Next Class](TypeDescriptor.md)

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
