Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CHAR.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BLOB.md)
- [Next Class](CharacterBuffer.md)

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

## Class CHAR

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.CHAR

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class CHAR
      extends Datum

  The Oracle specific representation of characters. The class extends oracle.sql.Datum and interprets the bytes according to one of the Oracle supported character sets. Each object of type oracle.sql.CHAR contains an indication of what character set to use in interpreting the bytes so one class can be used for all the variations, such as National Character Set, Client, Database, etc.
  For conversions that are not supported directly by CHAR (e.g. "best effort" conversions from String), if the programer wants a "best attempt" even when the conversion looses information, the "withReplacement" methods of oracle.sql.CharacterSet can be used directly.

  See Also:
  [`CharacterSet`](CharacterSet.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                          | Field and Description |
    |--------------------------------------------|-----------------------|
    | `static `[`CharacterSet`](CharacterSet.md) | `DEFAULT_CHARSET`     |

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                                                                                      |
    |-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `CHAR``()`                                                                                                                                                                                       |
    | ` `         | `CHAR``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`CharacterSet`](CharacterSet.md)` charSet)`<br>Construct a CHAR from an Object. |
    | ` `         | `CHAR``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](CharacterSet.md)` charSet)`<br>Constructor for CHAR.            |
    | ` `         | `CHAR``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](CharacterSet.md)` charSet, int len)`<br>Constructor for CHAR.   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `asciiStreamValue``()`<br>Convert to an ascii stream representation of the datum object                                                                                                                        |
    | [`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true) | `bigDecimalValue``()`<br>Convert this data object into a BigDecimal.                                                                                                                                           |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `binaryStreamValue``()`<br>Convert to a binary stream representation of the datum object                                                                                                                       |
    | `boolean`                                                                                               | `booleanValue``()`<br>Convert to a boolean representation of the datum object                                                                                                                                  |
    | `byte`                                                                                                  | `byteValue``()`<br>Convert to a byte representation of the datum object                                                                                                                                        |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)           | `characterStreamValue``()`<br>Convert to a character stream representation of the datum object                                                                                                                 |
    | [`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)              | `dateValue``()`<br>Convert to a Date representation of the datum object                                                                                                                                        |
    | `double`                                                                                                | `doubleValue``()`<br>Convert to a double representation of the datum object                                                                                                                                    |
    | `float`                                                                                                 | `floatValue``()`<br>Convert to a float representation of the datum object                                                                                                                                      |
    | `protected oracle.jdbc.internal.OracleConnection`                                                       | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getString``()`<br>Converts the sequence of characters represented by this to a String.                                                                                                                        |
    | `int`                                                                                                   | `intValue``()`<br>Convert to a integer representation of the datum object                                                                                                                                      |
    | `boolean`                                                                                               | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Test whether this data object can be converted to the specified Java data type. |
    | `boolean`                                                                                               | `isVariableLength``()`<br>Determines if this instance represents a variable or fixed length character sequence.                                                                                                |
    | `long`                                                                                                  | `longValue``()`<br>Convert to a long representation of the datum object                                                                                                                                        |
    | `int`                                                                                                   | `oracleId``()`<br>The integer that identifies the character set.                                                                                                                                               |
    | `void`                                                                                                  | `setVariableLength``(boolean variableLength)`<br>Sets a flag to indicate if this instance represents a fixed or variable length character sequence.                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `stringValue``()`<br>Convert this data object into a String.                                                                                                                                                   |
    | [`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)    | `timestampValue``()`<br>Convert to a Timestamp representation of the datum object                                                                                                                              |
    | [`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)              | `timeValue``()`<br>Convert to a Time representation of the datum object                                                                                                                                        |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `toJdbc``()`<br>Convert this data object into its default Java object type.                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `toString``()`<br>Converts the characters to a String.                                                                                                                                                         |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`isNull`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### DEFAULT_CHARSET

          public static final CharacterSet DEFAULT_CHARSET

  <!-- -->

  - ### Constructor Detail

    - #### CHAR

          protected CHAR()

    <!-- -->

    - #### CHAR

          public CHAR(String str,
                      CharacterSet charSet,
                      int len)
               throws SQLException

      Constructor for CHAR.
      Similar to CHAR(String str, CharacterSet charSet) Added parameter len. This CHAR constructor will space pad the CHAR object up to the length specificed by len.
      Parameters:
      `str` - the sequence of characters (represented in Unicode).

      `charSet` - the CharacterSet to which the string should be converted.

      if charSet is null, default charset will be used. The default charset choose we8iso8859p1 as Oracle Utiliites charset.

      `len` - the length that the CHAR object will be space padded up to

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the attempt to convert str to charSet throws an exception.

    <!-- -->

    - #### CHAR

          public CHAR(String str,
                      CharacterSet charSet)
               throws SQLException

      Constructor for CHAR.
      The String is first converted to the indicated character set. No provision is made for loss if the CharacterSet cannot represent all Unicode characters. Although perhaps some time in the future it may throw an exception in that case.
      Parameters:
      `str` - the sequence of characters (represented in Unicode).

      `charSet` - the CharacterSet to which the string should be converted.

      if charSet is null, default charset will be used. The default charset choose we8iso8859p1 as Oracle Utiliites charset.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the attempt to convert str to charSet throws an exception.

    <!-- -->

    - #### CHAR

          public CHAR(Object obj,
                      CharacterSet charSet)
               throws SQLException

      Construct a CHAR from an Object.
      Parameters:
      `obj` - input data from which this class instance is constructed. This constructor calls obj.toString() to obtain the input string.

      `charSet` - character set of the CHAR to be created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the input argument 'obj' is an instance of an unsupported class, or if the input object cannot be converted into a CHAR.

  <!-- -->

  - ### Method Detail

    - #### oracleId

          public int oracleId()

      The integer that identifies the character set.
      Returns:
      Oracle character set ID

    <!-- -->

    - #### getString

          public String getString()
                           throws SQLException

      Converts the sequence of characters represented by this to a String.
      Returns:
      a String containing the Unicode characters represented in this.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion from this.oracleId to UTF is not supported

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the particular cannot characters cannot be converted without loss to Unicode.

    <!-- -->

    - #### toString

          public String toString()

      Converts the characters to a String. Attempts to use getString, but if that throws an exception presents a hex representation of the individual bytes.
      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Convert this data object into its default Java object type.
      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      the data value as a (fill in the blank) object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any of the lower layer code throws an exception.

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class jClass)

      Test whether this data object can be converted to the specified Java data type.
      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `jClass` - specifies the Java data type to test against.

      Returns:
      true if this data object is convertible to the specified Java class, and a corresponding xxxValue() method is available; otherwise, a false is returned.

    <!-- -->

    - #### stringValue

          public String stringValue()

      Convert this data object into a String.
      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      the data value in String representation.

    <!-- -->

    - #### booleanValue

          public boolean booleanValue()
                               throws SQLException

      Convert to a boolean representation of the datum object
      Overrides:
      [`booleanValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`intValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`longValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`floatValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`doubleValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`byteValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      byte representation of the datum object

      Throws:
      `SQLException,` - if no byte representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dateValue

          public Date dateValue()
                         throws SQLException

      Convert to a Date representation of the datum object
      Overrides:
      [`dateValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`timeValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      java.sql.Time representation of the datum object

      Throws:
      `SQLException,` - if no Time representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### timestampValue

          public Timestamp timestampValue()
                                   throws SQLException

      Convert to a Timestamp representation of the datum object
      Overrides:
      [`timestampValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      java.sql.Timestamp representation of the datum object

      Throws:
      `SQLException,` - if no Timestamp representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### bigDecimalValue

          public BigDecimal bigDecimalValue()
                                     throws SQLException

      Convert this data object into a BigDecimal.
      Overrides:
      [`bigDecimalValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      the data value in BigDecimal representation.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### characterStreamValue

          public Reader characterStreamValue()
                                      throws SQLException

      Convert to a character stream representation of the datum object
      Overrides:
      [`characterStreamValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`asciiStreamValue`](Datum.md) in class [`Datum`](Datum.md)

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
      Overrides:
      [`binaryStreamValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      binary stream representation of the datum object

      Throws:
      `SQLException,` - if no binary stream representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Overrides:
      [`getConnectionDuringExceptionHandling`](Datum.md) in class [`Datum`](Datum.md)

    <!-- -->

    - #### setVariableLength

          public void setVariableLength(boolean variableLength)

      Sets a flag to indicate if this instance represents a fixed or variable length character sequence.
      Parameters:
      `variableLength` - True for variable length or false for fixed length.

    <!-- -->

    - #### isVariableLength

          public boolean isVariableLength()

      Determines if this instance represents a variable or fixed length character sequence.
      Returns:
      True if variable length or false if fixed length.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CHAR.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BLOB.md)
- [Next Class](CharacterBuffer.md)

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
