Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OPAQUE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NUMBER.md)
- [Next Class](OpaqueDescriptor.md)

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

## Class OPAQUE

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.OPAQUE

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleDatumWithConnection, [OracleOpaque](../jdbc/OracleOpaque.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use oracle.jdbc.OracleOpaque interface for declaration instead of using concrete class oracle.sql.OPAQUE.


      public class OPAQUE
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleOpaque

  A class for opaque data type. Use [`OracleOpaque`](../jdbc/OracleOpaque.md) interface for declaration instead of using concrete class oracle.sql.OPAQUE. oracle.jdbc.OracleOpaque has methods declared for all opertions.
  Obtaining an OracleOpaque from [`OracleResultSet`](../jdbc/OracleResultSet.md)

  `oracle.jdbc.OracleOpaque opaque = ((OracleResultSet)resultSet).getOPAQUE(...);`
  Since:
  8.2

  See Also:
  [`OracleOpaque`](../jdbc/OracleOpaque.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OPAQUE``(`[`OpaqueDescriptor`](OpaqueDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value)`<br>Deprecated. <br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                                                                           |
    |--------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `byte[]`                                                                                               | `getBytesValue``()`<br>Deprecated. <br>Return a byte array that represents the attributes into the format that is actually used in the database.                                                                 |
    | [`OpaqueDescriptor`](OpaqueDescriptor.md)                                                              | `getDescriptor``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                         |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                      |
    | [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)                                                  | `getOracleMetaData``()`<br>Deprecated. <br>Return the type data for this object                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getSQLTypeName``()`<br>Deprecated. <br>Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.                                    |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `getValue``()`<br>Deprecated. <br>Return the Opaque value.                                                                                                                                                       |
    | `boolean`                                                                                              | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Determines if datum object can be converted to a particular class |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `stringValue``()`<br>Deprecated. <br>Convert to a String representation of the datum object                                                                                                                      |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toJdbc``()`<br>Deprecated. <br>Returns the JDBC representation of the datum object                                                                                                                              |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Constructor Detail

    - #### OPAQUE

          public OPAQUE(OpaqueDescriptor type,
                        Connection conn,
                        Object value)
                 throws SQLException

      Deprecated. 
      Constructor. The raw bytes are computed at this time or a copy of attributes is made. In any event the caller is free to modify the array without affecting the values held in the OPAQUE.
      Parameters:
      `type` - the SQLStructType used to convert the type to

      `attributes` - the array specifying the attributes to be converted to raw bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `oracle.sql.SQLStructType`

  <!-- -->

  - ### Method Detail

    - #### getSQLTypeName

          public String getSQLTypeName()
                                throws SQLException

      Deprecated. 
      Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.
      Specified by:
      [`getSQLTypeName`](../jdbc/OracleOpaque.md) in interface [`OracleOpaque`](../jdbc/OracleOpaque.md)

      Returns:
      the fully-qualified type name of the SQL structured type for which this `Struct` object is the generic representation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### stringValue

          public String stringValue()
                             throws SQLException

      Deprecated. 
      Description copied from class: [`Datum`](Datum.md)
      Convert to a String representation of the datum object
      Specified by:
      `stringValue` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      String representation of the datum object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getOracleMetaData

          public OracleTypeMetaData getOracleMetaData()
                                               throws SQLException

      Deprecated. 
      Return the type data for this object
      Specified by:
      [`getOracleMetaData`](../jdbc/OracleOpaque.md) in interface [`OracleOpaque`](../jdbc/OracleOpaque.md)

      Returns:
      type metadata

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      11.2.0.3.0

    <!-- -->

    - #### getDescriptor

          public OpaqueDescriptor getDescriptor()
                                         throws SQLException

      Deprecated. 
      Oracle extension. Return the OpaqueDescriptor object that contains the type information.
      Returns:
      the type descriptor

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getValue

          public Object getValue()
                          throws SQLException

      Deprecated. 
      Return the Opaque value.
      Specified by:
      [`getValue`](../jdbc/OracleOpaque.md) in interface [`OracleOpaque`](../jdbc/OracleOpaque.md)

      Returns:
      a Java object that represents the opaque value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytesValue

          public byte[] getBytesValue()
                               throws SQLException

      Deprecated. 
      Return a byte array that represents the attributes into the format that is actually used in the database.
      Returns:
      a byte array that represents the opaque value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class jClass)

      Deprecated. 
      Determines if datum object can be converted to a particular class
      Specified by:
      `isConvertibleTo` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `cls` - Class to convert to

      Returns:
      true, if conversion to cls is permitted false, if conversion to cls is not permitted

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Returns the JDBC representation of the datum object
      Specified by:
      `toJdbc` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### getJavaSqlConnection

          public Connection getJavaSqlConnection()
                                          throws SQLException

      Deprecated. 
      Description copied from class: [`DatumWithConnection`](DatumWithConnection.md)
      Oracle extension Return the java.sql.Connection associated with the receiver. Since 9.0.0 not all Oracle JDBC connection objects are assignment compatible with oracle.jdbc.driver.OracleConnection. If the connection is wrapped, return the outermost wrapper.
      Specified by:
      `getJavaSqlConnection` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`getJavaSqlConnection`](DatumWithConnection.md) in class [`DatumWithConnection`](DatumWithConnection.md)

      Returns:
      the connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OPAQUE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](NUMBER.md)
- [Next Class](OpaqueDescriptor.md)

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
