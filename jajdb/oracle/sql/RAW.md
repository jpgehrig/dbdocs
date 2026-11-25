Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/RAW.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ORADataFactory.md)
- [Next Class](REF.md)

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

## Class RAW

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.RAW

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class RAW
      extends Datum

  The RAW class is a representation of the Oracle RAW datatype. It is intended to be immutable. The user should not try to change its contents once it is constructed.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `RAW``(byte[] raw_bytes)`<br>Construct a RAW from a byte array.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `RAW``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` val)`<br>Deprecated. <br>in 9.2. The behavior of this constructor when passed a String argument will be changed in the next major release after 9.2. There will be no change in the behavior when passed an argument of any other type. The static methods newRAW and oldRAW capture the new and old behavior. It is deprecated only to warn of the impending change in behavior. The deprecation will be removed in the next major release after 9.2. The constructor will remain and will be supported. See release notes for more info. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected oracle.jdbc.internal.OracleConnection`                                               | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                     |
    | `static byte[]`                                                                                 | `hexString2Bytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` hexString)`<br>Converts a String of hex digits into a byte array with the corresponding byte values.                      |
    | `boolean`                                                                                       | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Test whether this data object can be converted to the specified Java data type.                                 |
    | `static RAW`                                                                                    | `newRAW``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor beginning in 10i R1.                        |
    | `static RAW`                                                                                    | `oldRAW``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor in versions of Oracle JDBC 9.2 and earlier. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `stringValue``()`<br>Convert this data object into a String.                                                                                                                                                                                   |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `toJdbc``()`<br>Convert this data object into its default Java object type.                                                                                                                                                                    |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`bigDecimalValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### RAW

          public RAW(byte[] raw_bytes)

      Construct a RAW from a byte array.
      Parameters:
      `raw_bytes` - input data from which this class instance is constructed.

    <!-- -->

    - #### RAW

          public RAW(Object val)
              throws SQLException

      Deprecated. in 9.2. The behavior of this constructor when passed a String argument will be changed in the next major release after 9.2. There will be no change in the behavior when passed an argument of any other type. The static methods newRAW and oldRAW capture the new and old behavior. It is deprecated only to warn of the impending change in behavior. The deprecation will be removed in the next major release after 9.2. The constructor will remain and will be supported. See release notes for more info.
      Construct a RAW from a Java object. The possible object types are java.lang.String and byte\[\].
      Parameters:
      `val` - input data from which this class instance is constructed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `#newRAW(Object), #oldRAW(Object)`

  <!-- -->

  - ### Method Detail

    - #### hexString2Bytes

          public static byte[] hexString2Bytes(String hexString)
                                        throws SQLException

      Converts a String of hex digits into a byte array with the corresponding byte values.
      Parameters:
      `hexString` - A String of hex digits

      Returns:
      a byte array half the length of the argument with the value corresponding to the argument

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if one of the characters in the argument is not a hex digit

    <!-- -->

    - #### newRAW

          public static RAW newRAW(Object obj)
                            throws SQLException

      Creates a new RAW from an Object in the manner of the RAW(Object) constructor beginning in 10i R1. The only difference is if the argument is a String. This method assumes that the String consists of hex digits and returns a new RAW constructed from the bytes represented by those hex digits. If the argument is not a String then the behavior is the same as the RAW(Object) constructor.
      In Oracle JDBC versions beginning in 10i R1 this is identical to RAW(Object). In versions 9.2 and earlier, it provides the functionality that will be provided in versions beginning in 10i R1.

      **Note** that the behavior of RAW(Object) when passed a String argument changed in 10i R1.

      Parameters:
      `obj` - Object used to create the new RAW value

      Returns:
      a new RAW value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the argument is a String and one of the characters is not a hex digit

      See Also:
      `oldRAW`

    <!-- -->

    - #### oldRAW

          public static RAW oldRAW(Object obj)
                            throws SQLException

      Creates a new RAW from an Object in the manner of the RAW(Object) constructor in versions of Oracle JDBC 9.2 and earlier. The only difference is if the argument is a String. This method returns a new RAW containing the bytes of the ISO8859_1 representation of the String argument. If the argument is not a String then it is the same as the RAW(Object) constructor.
      In Oracle JDBC versions 9.2 and earlier this is identical to the RAW(Object) constructor. Beginning in 10i R1, it provides the functionality that previously was provided by that constructor.

      **Note** that the behavior of RAW(Object) when passed a String argument changed in 10i R1.

      Parameters:
      `obj` - Object used to create the RAW value

      Returns:
      a new RAW value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if something goes wrong

      See Also:
      `newRAW`

    <!-- -->

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

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Overrides:
      [`getConnectionDuringExceptionHandling`](Datum.md) in class [`Datum`](Datum.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/RAW.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ORADataFactory.md)
- [Next Class](REF.md)

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
