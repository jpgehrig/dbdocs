Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatumWithConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](Datum.md)
- [Next Class](INTERVALDS.md)

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

## Class DatumWithConnection

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - oracle.sql.DatumWithConnection

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.OracleDatumWithConnection

  <!-- -->

  Direct Known Subclasses:
  [ARRAY](ARRAY.md), [BFILE](BFILE.md), [BLOB](BLOB.md), [CLOB](CLOB.md), [OPAQUE](OPAQUE.md), [REF](REF.md), [STRUCT](STRUCT.md)

  ------------------------------------------------------------------------



      public abstract class DatumWithConnection
      extends Datum
      implements oracle.jdbc.internal.OracleDatumWithConnection

  A supper class for some Oracle specific datatypes, such as BFILE, BLOB, etc.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type               | Field and Description        |
    |---------------------------------|------------------------------|
    | `protected DatumWithConnection` | `targetDatumWithConnection`  |

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description               |
    |-------------------------------------------|
    | `DatumWithConnection``()`                 |
    | `DatumWithConnection``(byte[] elements)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                 |
    |--------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                                                                          | `assertNotNull``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                       |
    | `static void`                                                                                          | `assertNotNull``(`[`TypeDescriptor`](TypeDescriptor.md)` desc)`                                                                                        |
    | `oracle.jdbc.driver.OracleConnection`                                                                  | `getConnection``()`<br>Deprecated. <br>since 9.0.0. Use `getJavaSqlConnection()` or `getInternalConnection()`, or Use `getOracleConnection()` instead. |
    | `protected oracle.jdbc.internal.OracleConnection`                                                      | `getConnectionDuringExceptionHandling``()`                                                                                                             |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getJavaSqlConnection``()`<br>Oracle extension Return the java.sql.Connection associated with the receiver.                                            |
    | [`OracleConnection`](../jdbc/OracleConnection.md)                                                      | `getOracleConnection``()`<br>Oracle extension.                                                                                                         |

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isConvertibleTo`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`makeJdbcArray`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)`, `[`toJdbc`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getInternalConnection, getLength, getStream, intValue, isConvertibleTo, longValue, makeJdbcArray, setBytes, setShareBytes, shareBytes, stringValue, stringValue, timestampValue, timestampValue, timeValue, timeValue, toJdbc`

<!-- -->

- - ### Field Detail

    - #### targetDatumWithConnection

          protected DatumWithConnection targetDatumWithConnection

  <!-- -->

  - ### Constructor Detail

    - #### DatumWithConnection

          public DatumWithConnection(byte[] elements)
                              throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### DatumWithConnection

          public DatumWithConnection()

  <!-- -->

  - ### Method Detail

    - #### assertNotNull

          public static void assertNotNull(Connection conn)
                                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### assertNotNull

          public static void assertNotNull(TypeDescriptor desc)
                                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getJavaSqlConnection

          public Connection getJavaSqlConnection()
                                          throws SQLException

      Oracle extension Return the java.sql.Connection associated with the receiver. Since 9.0.0 not all Oracle JDBC connection objects are assignment compatible with oracle.jdbc.driver.OracleConnection. If the connection is wrapped, return the outermost wrapper.
      Specified by:
      `getJavaSqlConnection` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Returns:
      the connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9iR2

    <!-- -->

    - #### getOracleConnection

          public OracleConnection getOracleConnection()
                                               throws SQLException

      Oracle extension. The OracleConnection object associated with the object. If the internal connection is wrapped return the wrapping instance.
      Specified by:
      `getOracleConnection` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Returns:
      the possibly wrapped connection for external use

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9.2

    <!-- -->

    - #### getConnection

          public oracle.jdbc.driver.OracleConnection getConnection()
                                                            throws SQLException

      Deprecated. since 9.0.0. Use `getJavaSqlConnection()` or `getInternalConnection()`, or Use `getOracleConnection()` instead.
      Oracle extension. Returns the oracle.jdbc.driver.OracleConnection object associated with the receiver. This is always a physical connection. Any logical connection or connection wrapper associated with the physical connection is ignored by this mehtod
      Specified by:
      `getConnection` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Returns:
      the connection if it is assignment compatible with oracle.jdbc.driver.OracleConnection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the connection is not assignment compatible

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

      Overrides:
      [`getConnectionDuringExceptionHandling`](Datum.md) in class [`Datum`](Datum.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatumWithConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](Datum.md)
- [Next Class](INTERVALDS.md)

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
