Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/Datum.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DATE.md)
- [Next Class](DatumWithConnection.md)

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

## Class Datum

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.Datum

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [BINARY_DOUBLE](BINARY_DOUBLE.md), [BINARY_FLOAT](BINARY_FLOAT.md), [CHAR](CHAR.md), [DATE](DATE.md), [DatumWithConnection](DatumWithConnection.md), [INTERVALDS](INTERVALDS.md), [INTERVALYM](INTERVALYM.md), [NUMBER](NUMBER.md), [RAW](RAW.md), [ROWID](ROWID.md), [TIMESTAMP](TIMESTAMP.md), [TIMESTAMPLTZ](TIMESTAMPLTZ.md), [TIMESTAMPTZ](TIMESTAMPTZ.md)

  ------------------------------------------------------------------------



      public abstract class Datum
      extends Object
      implements Serializable

  The root of Oracle native datatype hierarchy.
  Each subclass represents one of the native kernel datatypes.

  In order to allow for possible optimization of data copying between SQL and Java, instances of subclasses are immutable.

  Since:
  JDK1(Oracle)

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                          | Field and Description           |
    |------------------------------------------------------------|---------------------------------|
    | `protected oracle.jdbc.internal.OracleDatumWithConnection` | `ojiOracleDatumWithConnection`  |
    | `protected Datum`                                          | `targetDatum`                   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                  |
    |----------------------------------------------------------------------------------------------|
    | `Datum``()`<br>Creates an empty datum                                                        |
    | `Datum``(byte[] newData)`<br>Create a new datum with the given byte array as representation. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                          | Method and Description                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)    | `asciiStreamValue``()`<br>Convert to an ascii stream representation of the datum object                                                                                                                                                                      |
    | [`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)    | `bigDecimalValue``()`<br>Convert to a BigDecimal representation of the datum object                                                                                                                                                                          |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)    | `binaryStreamValue``()`<br>Convert to a binary stream representation of the datum object                                                                                                                                                                     |
    | `boolean`                                                                                                  | `booleanValue``()`<br>Convert to a boolean representation of the datum object                                                                                                                                                                                |
    | `protected boolean`                                                                                        | `bytesEqual``(Datum other)`                                                                                                                                                                                                                                  |
    | `int`                                                                                                      | `bytesHashCode``()`                                                                                                                                                                                                                                          |
    | `byte`                                                                                                     | `byteValue``()`<br>Convert to a byte representation of the datum object                                                                                                                                                                                      |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)              | `characterStreamValue``()`<br>Convert to a character stream representation of the datum object                                                                                                                                                               |
    | `static int`                                                                                               | `compareBytes``(byte[] m, byte[] n)`<br>Do an unsigned compare on byte arrays m and n                                                                                                                                                                        |
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)                 | `dateValue``()`<br>Convert to a Date representation of the datum object                                                                                                                                                                                      |
    | `double`                                                                                                   | `doubleValue``()`<br>Convert to a double representation of the datum object                                                                                                                                                                                  |
    | `boolean`                                                                                                  | `equals``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Test any object for equality with an Datum.                                                                                             |
    | `float`                                                                                                    | `floatValue``()`<br>Convert to a float representation of the datum object                                                                                                                                                                                    |
    | `byte[]`                                                                                                   | `getBytes``()`<br>Create a new Java byte array containing a copy of the RDBMS data.                                                                                                                                                                          |
    | `protected oracle.jdbc.internal.OracleConnection`                                                          | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                   |
    | `long`                                                                                                     | `getLength``()`<br>Retreive the length of a datum.                                                                                                                                                                                                           |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)    | `getStream``()`<br>Create an input stream so the raw data may be read.                                                                                                                                                                                       |
    | `int`                                                                                                      | `intValue``()`<br>Convert to a integer representation of the datum object                                                                                                                                                                                    |
    | `abstract boolean`                                                                                         | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` cls)`<br>Determines if datum object can be converted to a particular class                                                                |
    | `boolean`                                                                                                  | `isNull``()`<br>Test if this Datum is empty                                                                                                                                                                                                                  |
    | `long`                                                                                                     | `longValue``()`<br>Convert to a long representation of the datum object                                                                                                                                                                                      |
    | `abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `makeJdbcArray``(int arraySize)`<br>Returns a JDBC array representation of the datum                                                                                                                                                                         |
    | `void`                                                                                                     | `setBytes``(byte[] array)`<br>Sets datum value using a byte array.                                                                                                                                                                                           |
    | `void`                                                                                                     | `setShareBytes``(byte[] array)`<br>Sets datum value using a byte array.                                                                                                                                                                                      |
    | `byte[]`                                                                                                   | `shareBytes``()`<br>Retrieve the data bytes.                                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)            | `stringValue``()`<br>Convert to a String representation of the datum object                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)            | `stringValue``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Some Datum subclass such as TIMESTAMPTZ will override this default implementation which simply ignores the the connection. |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)       | `timestampValue``()`<br>Convert to a Timestamp representation of the datum object                                                                                                                                                                            |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)       | `timestampValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`                                                                                                                                |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                 | `timeValue``()`<br>Convert to a Time representation of the datum object                                                                                                                                                                                      |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)                 | `timeValue``(`[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`                                                                                                                                     |
    | `<T> T`                                                                                                    | `toClass``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<T> type)`<br>Convert this datum to an instance of the specified type if possible.                                                                 |
    | `abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `toJdbc``()`<br>Returns the JDBC representation of the datum object                                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### targetDatum

          protected Datum targetDatum

    <!-- -->

    - #### ojiOracleDatumWithConnection

          protected oracle.jdbc.internal.OracleDatumWithConnection ojiOracleDatumWithConnection

  <!-- -->

  - ### Constructor Detail

    - #### Datum

          public Datum()

      Creates an empty datum

    <!-- -->

    - #### Datum

          public Datum(byte[] newData)

      Create a new datum with the given byte array as representation. Subclasses use this to initialize the `data` array.
      Parameters:
      `newData` - byte array to be stored in the datum

  <!-- -->

  - ### Method Detail

    - #### equals

          public boolean equals(Object obj)

      Test any object for equality with an Datum. Datums are equal if they are of the same class and their bytes are the same.
      Overrides:
      [`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `obj` - object to compare `this` with

      Returns:
      true if the class of `this` is the same as the class of `obj` and the byte representation of `this` is the same as the byte representation of `obj`.

    <!-- -->

    - #### bytesHashCode

          public int bytesHashCode()

      Returns:
      hash code for the bytes data stored in this Datum object

    <!-- -->

    - #### shareBytes

          public byte[] shareBytes()

      Retrieve the data bytes.
      Used by java code in subclasses to access the data bytes. If the bytes are not yet a Java array, this may cause them to be copied into one.

      Returns:
      a shared pointer to the datum's data bytes.

    <!-- -->

    - #### getLength

          public long getLength()

      Retreive the length of a datum.
      Returns:
      The length of the datum in bytes.

    <!-- -->

    - #### setBytes

          public void setBytes(byte[] array)

      Sets datum value using a byte array. The byte array is copied.
      Parameters:
      `array` - byte array used to set the datum value

    <!-- -->

    - #### setShareBytes

          public void setShareBytes(byte[] array)

      Sets datum value using a byte array. The byte array is referenced.
      Parameters:
      `array` - byte array used to set the datum value

    <!-- -->

    - #### getBytes

          public byte[] getBytes()

      Create a new Java byte array containing a copy of the RDBMS data. No conversions of any kind are done.
      For now, the data array is simply copied. When we are using moss to go directly to the buffer cache, this implementation will be overridden by a native method which will cons an array and copy the bytes into it.

      Subclasses which handle very long datatypes which will not ordinarily be represented as Java array, should check for allocation failure and return nil if detected. They should however try to materialize the raw data no matter how long since users may actually need to materialize huge arrays.

      Returns:
      A new copy of the data bytes or nil if the data could not be materialized because it was too long.

    <!-- -->

    - #### isNull

          public boolean isNull()

      Test if this Datum is empty
      Returns:
      a boolean

    <!-- -->

    - #### getStream

          public InputStream getStream()

      Create an input stream so the raw data may be read.
      This is the normal way to access long datatypes.

      Returns:
      an input stream.

    <!-- -->

    - #### stringValue

          public String stringValue()
                             throws SQLException

      Convert to a String representation of the datum object
      Returns:
      String representation of the datum object

      Throws:
      `SQLException,` - if no String representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### stringValue

          public String stringValue(Connection conn)
                             throws SQLException

      Some Datum subclass such as TIMESTAMPTZ will override this default implementation which simply ignores the the connection.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### booleanValue

          public boolean booleanValue()
                               throws SQLException

      Convert to a boolean representation of the datum object
      Returns:
      boolean representation of the datum object

      Throws:
      `SQLException,` - if no boolean representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### intValue

          public int intValue()
                       throws SQLException

      Convert to a integer representation of the datum object
      Returns:
      integer representation of the datum object

      Throws:
      `SQLException,` - if no integer representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### longValue

          public long longValue()
                         throws SQLException

      Convert to a long representation of the datum object
      Returns:
      long representation of the datum object

      Throws:
      `SQLException,` - if no long representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### floatValue

          public float floatValue()
                           throws SQLException

      Convert to a float representation of the datum object
      Returns:
      float representation of the datum object

      Throws:
      `SQLException,` - if no float representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### doubleValue

          public double doubleValue()
                             throws SQLException

      Convert to a double representation of the datum object
      Returns:
      double representation of the datum object

      Throws:
      `SQLException,` - if no double representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### byteValue

          public byte byteValue()
                         throws SQLException

      Convert to a byte representation of the datum object
      Returns:
      byte representation of the datum object

      Throws:
      `SQLException,` - if no byte representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### bigDecimalValue

          public BigDecimal bigDecimalValue()
                                     throws SQLException

      Convert to a BigDecimal representation of the datum object
      Returns:
      java.math.BigDecimal representation of the datum object

      Throws:
      `SQLException,` - if no BigDecimal representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dateValue

          public Date dateValue()
                         throws SQLException

      Convert to a Date representation of the datum object
      Returns:
      java.sql.Date representation of the datum object

      Throws:
      `SQLException,` - if no Date representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue()
                         throws SQLException

      Convert to a Time representation of the datum object
      Returns:
      java.sql.Time representation of the datum object

      Throws:
      `SQLException,` - if no Time representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timeValue

          public Time timeValue(Calendar cal)
                         throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue()
                                   throws SQLException

      Convert to a Timestamp representation of the datum object
      Returns:
      java.sql.Timestamp representation of the datum object

      Throws:
      `SQLException,` - if no Timestamp representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue(Calendar cal)
                                   throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### characterStreamValue

          public Reader characterStreamValue()
                                      throws SQLException

      Convert to a character stream representation of the datum object
      Returns:
      character stream representation of the datum object

      Throws:
      `SQLException,` - if no character stream representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### asciiStreamValue

          public InputStream asciiStreamValue()
                                       throws SQLException

      Convert to an ascii stream representation of the datum object
      Returns:
      ascii stream representation of the datum object

      Throws:
      `SQLException,` - if no ascii stream representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### binaryStreamValue

          public InputStream binaryStreamValue()
                                        throws SQLException

      Convert to a binary stream representation of the datum object
      Returns:
      binary stream representation of the datum object

      Throws:
      `SQLException,` - if no binary stream representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isConvertibleTo

          public abstract boolean isConvertibleTo(Class cls)

      Determines if datum object can be converted to a particular class
      Parameters:
      `cls` - Class to convert to

      Returns:
      true, if conversion to cls is permitted false, if conversion to cls is not permitted

    <!-- -->

    - #### toClass

          public <T> T toClass(Class<T> type)
                        throws SQLException

      Convert this datum to an instance of the specified type if possible.
      Parameters:
      `type` - targetDatum class

      Returns:
      an instance of the targetDatum class corresponding to this datum.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the conversion is not possible.

    <!-- -->

    - #### toJdbc

          public abstract Object toJdbc()
                                 throws SQLException

      Returns the JDBC representation of the datum object
      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### makeJdbcArray

          public abstract Object makeJdbcArray(int arraySize)

      Returns a JDBC array representation of the datum
      Parameters:
      `arraySize` - size of the array

      Returns:
      an object containing the JDBC array value

    <!-- -->

    - #### compareBytes

          public static int compareBytes(byte[] m,
                                         byte[] n)

      Do an unsigned compare on byte arrays m and n
      Parameters:
      `m` - input byte array

      `n` - input byte array

      Returns:
      -1 if m \< n, 0 if equal, 1 if m \> n

    <!-- -->

    - #### bytesEqual

          protected boolean bytesEqual(Datum other)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/Datum.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DATE.md)
- [Next Class](DatumWithConnection.md)

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
