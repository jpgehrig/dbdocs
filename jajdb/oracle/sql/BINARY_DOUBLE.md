Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BINARY_DOUBLE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BFILE.md)
- [Next Class](BINARY_FLOAT.md)

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

## Class BINARY_DOUBLE

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.BINARY_DOUBLE

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class BINARY_DOUBLE
      extends Datum

  The BINARY_DOUBLE class is a representation of the Oracle BINARY_DOUBLE datatype. It is intended to be immutable. The user should not try to change its contents once it is constructed.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BINARY_DOUBLE``(`[`Boolean`](http://download.oracle.com/javase/8/docs/api/java/lang/Boolean.html?is-external=true)` b)`<br>Construct a BINARY_DOUBLE from an instance of java.lang.Boolean. |
    | `BINARY_DOUBLE``(byte[] _bytes)`<br>Construct a BINARY_DOUBLE from a byte array.                                                                                                             |
    | `BINARY_DOUBLE``(double d)`<br>Construct a BINARY_DOUBLE from a primitive double.                                                                                                            |
    | `BINARY_DOUBLE``(`[`Double`](http://download.oracle.com/javase/8/docs/api/java/lang/Double.html?is-external=true)` d)`<br>Construct a BINARY_DOUBLE from an instance of java.lang.Double.    |
    | `BINARY_DOUBLE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`<br>Construct a BINARY_DOUBLE from an instance of java.lang.String.    |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true) | `bigDecimalValue``()`<br>Convert this to a BigDecimal type.                                                                                                                                                    |
    | `double`                                                                                                | `doubleValue``()`<br>Convert this to a double type.                                                                                                                                                            |
    | `boolean`                                                                                               | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Test whether this data object can be converted to the specified Java data type. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `stringValue``()`<br>Convert this data object into a String.                                                                                                                                                   |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `toJdbc``()`<br>Convert this data object into its default Java object type.                                                                                                                                    |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getConnectionDuringExceptionHandling`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### BINARY_DOUBLE

          public BINARY_DOUBLE(byte[] _bytes)

      Construct a BINARY_DOUBLE from a byte array.
      Parameters:
      `_bytes` - input data from which this class instance is constructed.

    <!-- -->

    - #### BINARY_DOUBLE

          public BINARY_DOUBLE(double d)

      Construct a BINARY_DOUBLE from a primitive double.
      Parameters:
      `d` - input data from which this class instance is constructed.

    <!-- -->

    - #### BINARY_DOUBLE

          public BINARY_DOUBLE(Double d)

      Construct a BINARY_DOUBLE from an instance of java.lang.Double.
      Parameters:
      `d` - input data from which this class instance is constructed.

    <!-- -->

    - #### BINARY_DOUBLE

          public BINARY_DOUBLE(String s)
                        throws SQLException

      Construct a BINARY_DOUBLE from an instance of java.lang.String.
      Parameters:
      `s` - input data from which this class instance is constructed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### BINARY_DOUBLE

          public BINARY_DOUBLE(Boolean b)

      Construct a BINARY_DOUBLE from an instance of java.lang.Boolean.
      Parameters:
      `b` - input data from which this class instance is constructed.

  <!-- -->

  - ### Method Detail

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Convert this data object into its default Java object type.
      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      the data value as a byte array.

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

    - #### doubleValue

          public double doubleValue()
                             throws SQLException

      Convert this to a double type.
      Overrides:
      [`doubleValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      The double value of this type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### bigDecimalValue

          public BigDecimal bigDecimalValue()
                                     throws SQLException

      Convert this to a BigDecimal type.
      Overrides:
      [`bigDecimalValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      The BigDecimal value of this type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BINARY_DOUBLE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BFILE.md)
- [Next Class](BINARY_FLOAT.md)

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
