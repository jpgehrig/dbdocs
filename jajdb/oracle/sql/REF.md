Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/REF.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](RAW.md)
- [Next Class](ROWID.md)

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

## Class REF

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.REF

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://download.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), [Ref](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, [OracleRef](../jdbc/OracleRef.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.Ref interface for declaration instead of using concrete class oracle.sql.REF.


      public class REF
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleRef, Serializable, Cloneable, oracle.jdbc.internal.OracleConcreteProxy

  The REF class is a representation of the Oracle REF datatype, and it implements the java.sql.Ref interface. Use [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true) interface for declaration instead of using concrete class oracle.sql.REF. java.sql.Ref has methods declared for all opertions. For Oracle specific methods use the interface [`OracleRef`](../jdbc/OracleRef.md).
  Obtaining java.sql.Ref from ResultSet

  `java.sql.Ref ref = resultSet.getRef(...);` There is no way to create [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true) on the client side.
  See Also:
  [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true), [`OracleRef`](../jdbc/OracleRef.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                        | Field and Description         |
    |------------------------------------------|-------------------------------|
    | `protected oracle.jdbc.driver.OracleRef` | `target`<br>Deprecated. <br>  |

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                                                                                                                                                                                               |
    |--------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `clone``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                              | `equals``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Deprecated. <br>Test any object for equality with an Datum.                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getBaseTypeName``()`<br>Deprecated. <br>Implements the Ref interface method.                                                                                                                                                                                                                                                        |
    | [`StructDescriptor`](StructDescriptor.md)                                                              | `getDescriptor``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                             |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                                                                                                                                          |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `getObject``()`<br>Deprecated. <br>JDBC 3.0 Retrieves the SQL structured type instance referenced by this `Ref` object.                                                                                                                                                                                                              |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `getObject``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>                                                                                                                                                                                                   |
    | [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)                                                  | `getOracleMetaData``()`<br>Deprecated. <br>Return the type data for this object                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getSQLTypeName``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                            |
    | [`STRUCT`](STRUCT.md)                                                                                  | `getSTRUCT``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                 |
    | `oracle.jdbc.driver.OracleRef`                                                                         | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                  |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `getValue``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                  |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `getValue``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                   |
    | `int`                                                                                                  | `hashCode``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                              | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Test whether this data object can be converted to the specified Java data type.                                                                                                       |
    | `void`                                                                                                 | `setObject``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value)`<br>Deprecated. <br>JDBC 3.0 Sets the structured type value that this `Ref` object references to the given instance of `Object`.                                                                               |
    | `void`                                                                                                 | `setValue``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toClass``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` clazz, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Returns the required object based on the class to which the SQL structured type is mapped to. |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toJdbc``()`<br>Deprecated. <br>Convert this data object into its default Java object type.                                                                                                                                                                                                                                          |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toJdbc``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Convert this data object into the Java object as defined in map if the data object type is not mapped to any class then its converted into default Java object type                                   |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Field Detail

    - #### target

          protected oracle.jdbc.driver.OracleRef target

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleRef getTarget()

      Deprecated. 

    <!-- -->

    - #### getBaseTypeName

          public String getBaseTypeName()
                                 throws SQLException

      Deprecated. 
      Implements the Ref interface method. Gets the fully-qualified SQL structured type name of the referenced item.
      Specified by:
      [`getBaseTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getBaseTypeName__) in interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

      Returns:
      fully-qualified SQL structured type name of the referenced item.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getValue

          public Object getValue(Map map)
                          throws SQLException

      Deprecated. 
      Oracle extension. Get referenced object. Use "map" for customized type mapping.
      Parameters:
      `map` - contains mapping of SQL type names to Java classes

      Returns:
      the referenced object which can be a STRUCT or any java object defined in type map.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getValue

          public Object getValue()
                          throws SQLException

      Deprecated. 
      Oracle extension. Get referenced object. Use the connection type map for customized type mapping.
      Returns:
      the referenced object which can be a STRUCT or any java object defined in type map.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSTRUCT

          public STRUCT getSTRUCT()
                           throws SQLException

      Deprecated. 
      Oracle extension. Get the referenced object as a STRUCT instance. Customized type mapping is ignored.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setValue

          public void setValue(Object value)
                        throws SQLException

      Deprecated. 
      Oracle extension. Set REF value. The method updated the underly object value in database.
      Parameters:
      `value` - the value to be set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getOracleMetaData

          public OracleTypeMetaData getOracleMetaData()
                                               throws SQLException

      Deprecated. 
      Return the type data for this object
      Specified by:
      [`getOracleMetaData`](../jdbc/OracleRef.md) in interface [`OracleRef`](../jdbc/OracleRef.md)

      Returns:
      type metadata

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      11.2.0.3.0

    <!-- -->

    - #### getDescriptor

          public StructDescriptor getDescriptor()
                                         throws SQLException

      Deprecated. 
      Oracle extension. Return the type descriptor of the ADT type that this REF object points to.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSQLTypeName

          public String getSQLTypeName()
                                throws SQLException

      Deprecated. 
      Oracle extension. Return the type name of the ADT type that this REF object points to.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getObject

          public Object getObject(Map map)
                           throws SQLException

      Deprecated. 
      Specified by:
      [`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getObject_java_util_Map_) in interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getObject

          public Object getObject()
                           throws SQLException

      Deprecated. 
      JDBC 3.0 Retrieves the SQL structured type instance referenced by this `Ref` object. If the connection's type map has an entry for the structured type, the instance will be custom mapped to the Java class indicated in the type map. Otherwise, the structured type instance will be mapped to a `Struct` object.
      Specified by:
      [`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getObject__) in interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

      Returns:
      a Java `Object` that is the mapping for the SQL structured type to which this `Ref` object refers

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      `setObject(java.lang.Object)`

    <!-- -->

    - #### setObject

          public void setObject(Object value)
                         throws SQLException

      Deprecated. 
      JDBC 3.0 Sets the structured type value that this `Ref` object references to the given instance of `Object`. The driver converts this to an SQL structured type when it sends it to the database.
      Specified by:
      [`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#setObject_java_lang_Object_) in interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

      Parameters:
      `value` - an `Object` representing the SQL structured type instance that this `Ref` object will reference

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10R1

      See Also:
      `getObject()`, `getObject(Map)`, [`PreparedStatement.setObject(int, Object)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_), `PreparedStatement#setObject(String, Object)`

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Convert this data object into its default Java object type.
      Specified by:
      `toJdbc` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      this object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any of the lower layer code throws an exception.

    <!-- -->

    - #### toJdbc

          public Object toJdbc(Map map)
                        throws SQLException

      Deprecated. 
      Convert this data object into the Java object as defined in map if the data object type is not mapped to any class then its converted into default Java object type
      Parameters:
      `map` - connection type map

      Returns:
      jdbcObject

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toClass

          public Object toClass(Class clazz,
                                Map map)
                         throws SQLException

      Deprecated. 
      Returns the required object based on the class to which the SQL structured type is mapped to.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class jClass)

      Deprecated. 
      Test whether this data object can be converted to the specified Java data type.
      Specified by:
      `isConvertibleTo` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `jClass` - specifies the Java data type to test against.

      Returns:
      true if this data object is convertible to the specified Java class, and a corresponding xxxValue() method is available; otherwise, a false is returned.

    <!-- -->

    - #### clone

          public Object clone()
                       throws CloneNotSupportedException

      Deprecated. 
      Overrides:
      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Throws:
      [`CloneNotSupportedException`](http://download.oracle.com/javase/8/docs/api/java/lang/CloneNotSupportedException.html?is-external=true)

    <!-- -->

    - #### equals

          public boolean equals(Object obj)

      Deprecated. 
      Description copied from class: [`Datum`](Datum.md)
      Test any object for equality with an Datum. Datums are equal if they are of the same class and their bytes are the same.
      Overrides:
      [`equals`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `obj` - object to compare `this` with

      Returns:
      true if the class of `this` is the same as the class of `obj` and the byte representation of `this` is the same as the byte representation of `obj`.

    <!-- -->

    - #### hashCode

          public int hashCode()

      Deprecated. 
      Overrides:
      [`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__) in class [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

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
- [Use](class-use/REF.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](RAW.md)
- [Next Class](ROWID.md)

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
