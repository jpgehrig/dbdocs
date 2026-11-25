Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/INTERVALDS.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatumWithConnection.md)
- [Next Class](INTERVALYM.md)

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

## Class INTERVALDS

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.INTERVALDS

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class INTERVALDS
      extends Datum

  **INTERVALDS Class**

  The `INTERVALDS` class specifies a value to be used to measure time differences.

  The internal data for this object is stored as a 11 byte array in the super class' storage area. The bytes are arranged as follows:

            Byte       Represents
             0         High byte of day
             1         2nd high byte of day
             2         3rd high byte of day
             3         least byte of day
             4         hour val + 60
             5         min + 60
             6         sec + 60
             7         High byte of Fractional second
             8         2nd high byte of Fractional Second
             9         3rd high byte of Fractional Second
             10        least byte of Fractional Second


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

    | Constructor and Description                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `INTERVALDS``()`<br>Constructs a INTERVALDS object initialized with .                                                                                                                       |
    | `INTERVALDS``(byte[] intervalDS)`<br>Create an Oracle INTERVALDS object represented by the given intervalDS byte array                                                                      |
    | `INTERVALDS``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Create an Oracle INTERVALDS object represented by the given String |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if the object can be converted to a particular class |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `stringValue``()`<br>Returns String for this INTERVALDS object                                                                                                                              |
    | `byte[]`                                                                                                 | `toBytes``()`<br>Convert Oracle INTERVALDS object into a byte array                                                                                                                         |
    | `static byte[]`                                                                                          | `toBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert Java String to Oracle INTERVALDS.                             |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `toJdbc``()`<br>Returns the JDBC representation of the INTERVALDS object                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `toString``()`<br>Converts a INTERVALDS to a string                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``(byte[] inparray)`<br>Converts a INTERVALDS to a string                                                                                                                          |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### INTERVALDS

          public INTERVALDS()

      Constructs a INTERVALDS object initialized with .

    <!-- -->

    - #### INTERVALDS

          public INTERVALDS(byte[] intervalDS)

      Create an Oracle INTERVALDS object represented by the given intervalDS byte array
      Parameters:
      `intervalDS` - byte array

    <!-- -->

    - #### INTERVALDS

          public INTERVALDS(String str)

      Create an Oracle INTERVALDS object represented by the given String
      Parameters:
      `str` - Java String object

  <!-- -->

  - ### Method Detail

    - #### toBytes

          public byte[] toBytes()

      Convert Oracle INTERVALDS object into a byte array
      Returns:
      the byte array stored in the INTERVALDS object

    <!-- -->

    - #### toBytes

          public static byte[] toBytes(String str)

      Convert Java String to Oracle INTERVALDS.
      Parameters:
      `str` - java.lang.String object to be converted.

      Returns:
      the byte array representing the input string.

    <!-- -->

    - #### toString

          public static String toString(byte[] inparray)

      Converts a INTERVALDS to a string
      Parameters:
      `inparray` - a byte array representing the INTERVALDS object

      Returns:
      String representing the INTERVALDS object

    <!-- -->

    - #### toJdbc

          public Object toJdbc()

      Returns the JDBC representation of the INTERVALDS object
      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

    <!-- -->

    - #### stringValue

          public String stringValue()

      Returns String for this INTERVALDS object
      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      a Java String value

    <!-- -->

    - #### toString

          public String toString()

      Converts a INTERVALDS to a string
      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      String representing this INTERVALDS object

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

    - #### makeJdbcArray

          public Object makeJdbcArray(int arraySize)

      Returns a JDBC array representation of the datum
      Specified by:
      [`makeJdbcArray`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `arraySize` - size of the array

      Returns:
      an object containing the JDBC array value

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/INTERVALDS.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatumWithConnection.md)
- [Next Class](INTERVALYM.md)

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
