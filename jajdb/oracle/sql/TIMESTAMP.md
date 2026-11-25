Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMP.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](StructDescriptor.md)
- [Next Class](TIMESTAMPLTZ.md)

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

## Class TIMESTAMP

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.TIMESTAMP

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.OracleTimestamp

  ------------------------------------------------------------------------



      public class TIMESTAMP
      extends Datum
      implements Serializable, oracle.jdbc.internal.OracleTimestamp

  **TIMESTAMP Class**

  The `TIMESTAMP` class provides conversions between the Oracle Date (ldx_t) data type and Java classes `java.sql.Date`, `java.sql.Time`, `java.sql.Timestamp`

  The internal data for this object is stored as a eleven byte array in the super class' storage area. The bytes are arranged as follows:

            Byte       Represents
             0         Century (119 for 1990)
             1         Decade  (190 for 1990)
             2         Month
             3         Day
             4         Hour
             5         Minute
             6         Seconds
             7         Nanoseconds
             8         Nanoseconds
             9         Nanoseconds
             10        Nanoseconds


  Static methods are used for conversions.

  Since:
  release specific (what release of product did this appear in)

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description    |
    |-------------------|--------------------------|
    | `static int`      | `SIZE_DATE`              |
    | `static int`      | `SIZE_TIMESTAMP`         |
    | `static int`      | `SIZE_TIMESTAMP_NOFRAC`  |

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TIMESTAMP``()`<br>Constructs a TIMESTAMP object initialized to 1/1/1970.                                                                                                                                                                                                                                                      |
    | `TIMESTAMP``(byte[] timestamp)`<br>Create an Oracle TIMESTAMP object represented by the given Oracle Timestamp                                                                                                                                                                                                                 |
    | `TIMESTAMP``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Create an Oracle TIMESTAMP object represented by the Java Date                                                                                                                                             |
    | `TIMESTAMP``(`[`DATE`](DATE.md)` date)`<br>Create an Oracle TIMESTAMP object represented by the Oracle DATE                                                                                                                                                                                                                    |
    | `TIMESTAMP``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Create a TIMESTAMP object given a Java String object.                                                                                                                                                  |
    | `TIMESTAMP``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Create an Oracle TIMESTAMP object represented by the given Java Time                                                                                                                                       |
    | `TIMESTAMP``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Create an Oracle TIMESTAMP object represented by the Java Timestamp                                                                                                                         |
    | `TIMESTAMP``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Create an Oracle TIMESTAMP object represented by the Java Timestamp and Calendar |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                             | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
    |---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                    | `dateValue``()`<br>Calls toDate to convert internal Oracle TIMESTAMP to a Java Date.                                                                                                                                                                                                                                                                                                                                                       |
    | `static int`                                                                                                  | `getJavaYear``(int cent, int decade)`                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static int`                                                                                                  | `getOracleYear``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                     | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class                                                                                                                                                                                                                                                |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `stringValue``()`<br>Calls toString to convert internal Oracle TIMESTAMP to a Java String.                                                                                                                                                                                                                                                                                                                                                 |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``()`<br>Calls toTimestamp to convert internal Oracle TIMESTAMP to a Java Timestamp.                                                                                                                                                                                                                                                                                                                                        |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)          | `timestampValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Calls toTimestamp to convert internal Oracle TIMESTAMP and Calendar to a Java Timestamp.                                                                                                                                                                                                                  |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                    | `timeValue``()`<br>Calls toTime to convert internal Oracle Date to a Java Time.                                                                                                                                                                                                                                                                                                                                                            |
    | `static TIMESTAMP`                                                                                            | `TimeZoneConvert``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, TIMESTAMP tstamp, `[`TimeZone`](http://download.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz1, `[`TimeZone`](http://download.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz2)`<br>Converts the TIMESTAMP object from one timezone to the other |
    | `byte[]`                                                                                                      | `toBytes``()`<br>Convert Oracle TIMESTAMP object into a byte array                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte[]`                                                                                               | `toBytes``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` date)`<br>Convert Java Date to Oracle TIMESTAMP.                                                                                                                                                                                                                                                                                   |
    | `static byte[]`                                                                                               | `toBytes``(`[`DATE`](DATE.md)` date)`<br>Convert Oracle DATE to Oracle TIMESTAMP                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte[]`                                                                                               | `toBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert Java String to Oracle TIMESTAMP.                                                                                                                                                                                                                                                                             |
    | `static byte[]`                                                                                               | `toBytes``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` time)`<br>Convert Java Time to Oracle TIMESTAMP.                                                                                                                                                                                                                                                                                   |
    | `static byte[]`                                                                                               | `toBytes``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp)`<br>Convert Java Timestamp to Oracle TIMESTAMP                                                                                                                                                                                                                                                                |
    | `static byte[]`                                                                                               | `toBytes``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert Java Timestamp and Java Calendar to Oracle TIMESTAMP                                                                                                                                   |
    | `static `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)           | `toDate``(byte[] timestamp)`<br>Convert a byte array representing a TIMESTAMP object to a Java Date Object                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`DATE`](DATE.md)                                                                                    | `toDATE``(byte[] timestamp)`<br>Convert a byte array representing a TIMESTAMP object to a Oracle DATE Object                                                                                                                                                                                                                                                                                                                               |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)               | `toJdbc``()`<br>Returns the JDBC representation of the datum object                                                                                                                                                                                                                                                                                                                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `toString``()`                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `toString``(byte[] bytes)`<br>Converts a TIMESTAMP to a string                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)           | `toTime``(byte[] timestamp)`<br>Convert a byte array representing a TIMESTAMP object to a Java Time Object                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(byte[] timestamp)`<br>Convert a byte array representing a TIMESTAMP object to a Java Timestamp Object                                                                                                                                                                                                                                                                                                                       |
    | `static `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true) | `toTimestamp``(byte[] timestamp, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Convert a byte array representing a TIMESTAMP object to a Java Timestamp Object given Calendar object                                                                                                                                                                                      |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleTimestamp

      `from, from`

<!-- -->

- - ### Field Detail

    - #### SIZE_DATE

          public static final int SIZE_DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SIZE_TIMESTAMP

          public static final int SIZE_TIMESTAMP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SIZE_TIMESTAMP_NOFRAC

          public static final int SIZE_TIMESTAMP_NOFRAC

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### TIMESTAMP

          public TIMESTAMP()

      Constructs a TIMESTAMP object initialized to 1/1/1970.

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(byte[] timestamp)

      Create an Oracle TIMESTAMP object represented by the given Oracle Timestamp
      Parameters:
      `timestamp` - Oracle TIMESTAMP

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(Time time)

      Create an Oracle TIMESTAMP object represented by the given Java Time
      Parameters:
      `time` - Java Time object

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(Date date)

      Create an Oracle TIMESTAMP object represented by the Java Date
      Parameters:
      `date` - Java Date object

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(Timestamp timestamp)

      Create an Oracle TIMESTAMP object represented by the Java Timestamp
      Parameters:
      `timestamp` - Java Timestamp object

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(Timestamp timestamp,
                           Calendar cal)

      Create an Oracle TIMESTAMP object represented by the Java Timestamp and Calendar
      Parameters:
      `timestamp` - Java Timestamp object

      `cal` - Java Util Calendar object

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(DATE date)

      Create an Oracle TIMESTAMP object represented by the Oracle DATE
      Parameters:
      `date` - Oracle DATE object

    <!-- -->

    - #### TIMESTAMP

          public TIMESTAMP(String str)

      Create a TIMESTAMP object given a Java String object.
      Parameters:
      `str` - Java String object

  <!-- -->

  - ### Method Detail

    - #### toDate

          public static Date toDate(byte[] timestamp)
                             throws SQLException

      Convert a byte array representing a TIMESTAMP object to a Java Date Object
      Parameters:
      `timestamp` - Oracle TIMESTAMP object

      Returns:
      the Java date object represented by Oracle TIMESTAMP object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTime

          public static Time toTime(byte[] timestamp)
                             throws SQLException

      Convert a byte array representing a TIMESTAMP object to a Java Time Object
      Parameters:
      `timestamp` - Oracle TIMESTAMP object

      Returns:
      the java.sql.Time object represented by Oracle TIMESTAMP object. Only the hour, minute and seconds are contained in the java.sql.Time object that is returned and hence callers should not attempt to access the date component of the returned object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(byte[] timestamp)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMP object to a Java Timestamp Object
      Parameters:
      `timestamp` - Oracle TIMESTAMP object

      Returns:
      the Java timestamp object represented by Oracle TIMESTAMP object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toTimestamp

          public static Timestamp toTimestamp(byte[] timestamp,
                                              Calendar cal)
                                       throws SQLException

      Convert a byte array representing a TIMESTAMP object to a Java Timestamp Object given Calendar object
      Parameters:
      `timestamp` - Oracle TIMESTAMP object to be converted

      `cal` - java.utl.Calendar object

      Returns:
      the java.sql.Timestamp object represented by the Oracle TIMESTAMP object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toDATE

          public static DATE toDATE(byte[] timestamp)
                             throws SQLException

      Convert a byte array representing a TIMESTAMP object to a Oracle DATE Object
      Parameters:
      `timestamp` - Oracle TIMESTAMP object

      Returns:
      the oracle DATE object represented by Oracle TIMESTAMP object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue()
                                   throws SQLException

      Calls toTimestamp to convert internal Oracle TIMESTAMP to a Java Timestamp.
      Overrides:
      [`timestampValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Timestamp value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Calendar cal)
                                   throws SQLException

      Calls toTimestamp to convert internal Oracle TIMESTAMP and Calendar to a Java Timestamp.
      Overrides:
      [`timestampValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Timestamp value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toString

          public static String toString(byte[] bytes)

      Converts a TIMESTAMP to a string
      Specified by:
      `toString` in interface `oracle.jdbc.internal.OracleTimestamp`

      Parameters:
      `date` - a byte array

      Returns:
      String representing the date

    <!-- -->

    - #### toBytes

          public byte[] toBytes()

      Convert Oracle TIMESTAMP object into a byte array
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleTimestamp`

      Returns:
      the byte array stored in the TIMESTAMP object

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Time time)

      Convert Java Time to Oracle TIMESTAMP.
      Parameters:
      `time` - java.sql.Time object to be converted.

      Returns:
      the byte array representing the java Time.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Date date)

      Convert Java Date to Oracle TIMESTAMP.
      Parameters:
      `date` - java.sql.Date object to be converted.

      Returns:
      the byte array representing the java Date.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Timestamp timestamp)

      Convert Java Timestamp to Oracle TIMESTAMP
      Parameters:
      `Timestamp` - java.sql.Timestamp object to be converted.

      Returns:
      the byte array representing the java timestamp.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(Timestamp timestamp,
                                       Calendar cal)

      Convert Java Timestamp and Java Calendar to Oracle TIMESTAMP
      Parameters:
      `Timestamp` - java.sql.Timestamp object to be converted.

      `Calendar` - java.util.Calendar object to be converted.

      Returns:
      the byte array representing the java timestamp.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(DATE date)

      Convert Oracle DATE to Oracle TIMESTAMP
      Parameters:
      `date` - oracle.sql.Timestamp object to be converted.

      Returns:
      the byte array representing the oracle DATE.

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(String str)

      Convert Java String to Oracle TIMESTAMP.
      Specified by:
      `toBytes` in interface `oracle.jdbc.internal.OracleTimestamp`

      Parameters:
      `str` - java.lang.String object to be converted.

      Returns:
      the byte array representing the input string.

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

    - #### TimeZoneConvert

          public static TIMESTAMP TimeZoneConvert(Connection conn,
                                                  TIMESTAMP tstamp,
                                                  TimeZone tz1,
                                                  TimeZone tz2)
                                           throws SQLException

      Converts the TIMESTAMP object from one timezone to the other
      Parameters:
      `conn` - Java Connection object tstamp TIMESTAMP object to be converted tz1 Source timezone tz2 Destination timezone

      Returns:
      TIMESTAMP object in the destination timezone

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue()

      Calls toString to convert internal Oracle TIMESTAMP to a Java String.
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

    - #### getOracleYear

          public static int getOracleYear(Calendar cal)

    <!-- -->

    - #### dateValue

          public Date dateValue()
                         throws SQLException

      Calls toDate to convert internal Oracle TIMESTAMP to a Java Date.
      Overrides:
      [`dateValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Date Object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue()
                         throws SQLException

      Calls toTime to convert internal Oracle Date to a Java Time.
      Overrides:
      [`timeValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java Time value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getJavaYear

          public static int getJavaYear(int cent,
                                        int decade)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TIMESTAMP.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](StructDescriptor.md)
- [Next Class](TIMESTAMPLTZ.md)

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
