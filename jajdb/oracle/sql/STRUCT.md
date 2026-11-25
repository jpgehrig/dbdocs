Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/STRUCT.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ROWID.md)
- [Next Class](StructDescriptor.md)

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

## Class STRUCT

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.STRUCT

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Struct](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, [OracleStruct](../jdbc/OracleStruct.md)

  <!-- -->

  Direct Known Subclasses:
  [JAVA_STRUCT](JAVA_STRUCT.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT.


      public class STRUCT
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleStruct, oracle.jdbc.internal.OracleConcreteProxy

  This class has two roles.
  - It is the Oracle implementation class for the generic JDBC Struct interface.
  - It wraps the "raw bytes" of an Oracle Object Type.

  Like other classes in oracle.sql. it is a value class. That is, once it is constructed the user should not change its contents. Use [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true) interface for declaration instead of using concrete class oracle.sql.STRUCT. java.sql.Struct has methods declared for all opertions. For Oracle specific methods use the interface [`OracleStruct`](../jdbc/OracleStruct.md).
  Obtaining a Struct from the ResultSet

  `java.sql.Struct struct = resultSet.getStruct(...);`
  Creating a Struct using factory method [`Connection.createStruct(java.lang.String, java.lang.Object[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStruct_java_lang_String_java_lang_Object_A_)

  `java.sql.Struct struct = connection.createStruct(...);`
  See Also:
  [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true), [`OracleStruct`](../jdbc/OracleStruct.md), [`Connection.createStruct(java.lang.String, java.lang.Object[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStruct_java_lang_String_java_lang_Object_A_), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                           | Field and Description         |
    |---------------------------------------------|-------------------------------|
    | `protected oracle.jdbc.driver.OracleStruct` | `target`<br>Deprecated. <br>  |

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `STRUCT``(`[`StructDescriptor`](StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attrList)`<br>Deprecated. <br>                       |
    | `STRUCT``(`[`StructDescriptor`](StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[] attributes)`<br>Deprecated. <br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                                                                                                                                  |
    |--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `dump``()`<br>Deprecated. <br>Create a string which show the contents of this Object and of all its component parts.                                                                                                                                                    |
    | `static void`                                                                                          | `dump``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` o, `[`PrintStream`](http://download.oracle.com/javase/8/docs/api/java/io/PrintStream.html?is-external=true)` ps)`<br>Deprecated. <br>                         |
    | `static void`                                                                                          | `dump``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` o, `[`PrintWriter`](http://download.oracle.com/javase/8/docs/api/java/io/PrintWriter.html?is-external=true)` pw)`<br>Deprecated. <br>                         |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`    | `getAttributes``()`<br>Deprecated. <br>Implements the Struct interface function.                                                                                                                                                                                        |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`    | `getAttributes``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Implements the Struct interface function.                                                                                         |
    | `boolean`                                                                                              | `getAutoBuffering``()`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                                             |
    | [`Datum`](Datum.md)`[]`                                                                                | `getDatumArray``()`<br>Deprecated. <br>                                                                                                                                                                                                                                 |
    | [`StructDescriptor`](StructDescriptor.md)                                                              | `getDescriptor``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                                                                             |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`    | `getObjectArray``()`<br>Deprecated. <br>                                                                                                                                                                                                                                |
    | [`Datum`](Datum.md)`[]`                                                                                | `getOracleAttributes``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                          |
    | [`OracleDataFactory`](../jdbc/OracleDataFactory.md)                                                    | `getOracleDataFactory``(`[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)` map, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` classname)`<br>Deprecated. <br>  |
    | [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)                                                  | `getOracleMetaData``()`<br>Deprecated. <br>Return the type data for this object                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)        | `getSQLTypeName``()`<br>Deprecated. <br>Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.                                                                                           |
    | `oracle.jdbc.driver.OracleStruct`                                                                      | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                                                                     |
    | `boolean`                                                                                              | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Determines if datum object can be converted to a particular class                                                        |
    | `void`                                                                                                 | `setAutoBuffering``(boolean enable)`<br>Deprecated. <br>Performance hint.                                                                                                                                                                                               |
    | `void`                                                                                                 | `setNullDatumArray``()`<br>Deprecated. <br>Set the variable null.                                                                                                                                                                                                       |
    | `void`                                                                                                 | `setNullObjectArray``()`<br>Deprecated. <br>Set the variable null.                                                                                                                                                                                                      |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toJdbc``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                       |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)        | `toJdbc``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>Oracle extension.                                                                                                                        |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`asciiStreamValue`](Datum.md)`, `[`bigDecimalValue`](Datum.md)`, `[`binaryStreamValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`characterStreamValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setBytes`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Field Detail

    - #### target

          protected oracle.jdbc.driver.OracleStruct target

      Deprecated. 

  <!-- -->

  - ### Constructor Detail

    - #### STRUCT

          public STRUCT(StructDescriptor type,
                        Connection conn,
                        Object[] attributes)
                 throws SQLException

      Deprecated. 
      Constructor. The raw bytes are computed at this time or a copy of attributes is made. In any event the caller is free to modify the array without affecting the values held in the STRUCT. For inherited object types we must check that the descriptor indicates that the type is instantiable. That database does not check on e.g. insertion but only on PL/SQL object creation. So we have to check here, too. There is an argument to be made that there is a good use for the STRUCT instance to carry data around and that the error ought to be when an insertion or udpate is attempted. But this keeps the "not instantiable" rather than "not storable" notion. And is is much more simple.
      Parameters:
      `type` - the SQLStructType used to convert the type to

      `attributes` - the array specifying the attributes to be converted to raw bytes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `oracle.sql.SQLStructType`

    <!-- -->

    - #### STRUCT

          public STRUCT(StructDescriptor type,
                        Connection conn,
                        Map attrList)
                 throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleStruct getTarget()

      Deprecated. 

    <!-- -->

    - #### getSQLTypeName

          public String getSQLTypeName()
                                throws SQLException

      Deprecated. 
      Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.
      Specified by:
      [`getSQLTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getSQLTypeName__) in interface [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)

      Returns:
      the fully-qualified type name of the SQL structured type for which this `Struct` object is the generic representation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getAttributes

          public Object[] getAttributes()
                                 throws SQLException

      Deprecated. 
      Implements the Struct interface function. Produces the ordered values of the attributes of the SQL structure type that this `Struct` object represents. Each call returns a fresh array. This method uses the type map associated with the connection for customizations of the type mappings. If there is no entry in the connection's type map that matches the structured type that this `Struct` object represents, the driver uses the standard mapping.
      Conceptually, this method calls the method `getObject` on each attribute of the structured type and returns a Java array containing the result.

      Specified by:
      [`getAttributes`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getAttributes__) in interface [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)

      Returns:
      an array containing the ordered attribute values

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getAttributes

          public Object[] getAttributes(Map map)
                                 throws SQLException

      Deprecated. 
      Implements the Struct interface function. Produces the ordered values of the attributes of the SQL structurec type that this `Struct` object represents. Each call returns a fresh array. This method uses the given type map for customizations of the type mappings. If there is no entry in the given type map that matches the structured type that this `Struct` object represents, the driver uses the standard mapping.
      Conceptually, this method calls the method `getObject` on each attribute of the structured type and returns a Java array containing the result.

      Specified by:
      [`getAttributes`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getAttributes_java_util_Map_) in interface [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)

      Parameters:
      `map` - a mapping of SQL type names to Java classes

      Returns:
      an array containing the ordered attribute values

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getOracleMetaData

          public OracleTypeMetaData getOracleMetaData()
                                               throws SQLException

      Deprecated. 
      Return the type data for this object
      Specified by:
      [`getOracleMetaData`](../jdbc/OracleStruct.md) in interface [`OracleStruct`](../jdbc/OracleStruct.md)

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
      Oracle extension. Return the StructDescriptor object that contains the type information.
      Returns:
      the type descriptor

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getOracleAttributes

          public Datum[] getOracleAttributes()
                                      throws SQLException

      Deprecated. 
      Oracle extension. Retrun the array of Attributes as oracle.sql.XXX's. A fresh array is returned each time getOracleAttributes is called.
      Returns:
      Datum array that containing the ordered attribute values as oracle.sql.Datum objects.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDatumArray

          public Datum[] getDatumArray()

      Deprecated. 

    <!-- -->

    - #### setNullDatumArray

          public void setNullDatumArray()

      Deprecated. 
      Set the variable null. (INTERNAL)

    <!-- -->

    - #### getObjectArray

          public Object[] getObjectArray()

      Deprecated. 

    <!-- -->

    - #### setNullObjectArray

          public void setNullObjectArray()

      Deprecated. 
      Set the variable null. (INTERNAL)

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Oracle extension. Returns the JDBC representation of the datum object
      Specified by:
      `toJdbc` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      an object containing the JDBC value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if conversion to JDBC representation results in an error

    <!-- -->

    - #### toJdbc

          public Object toJdbc(Map map)
                        throws SQLException

      Deprecated. 
      Oracle extension. Consults the map to determine what class to convert to, and then uses toClass
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

    - #### setAutoBuffering

          public void setAutoBuffering(boolean enable)
                                throws SQLException

      Deprecated. 
      Performance hint. Sets this struct's auto-buffering mode. If a struct is in auto-buffering mode, then the struct will keep a local copy of all its attributes. Then the next access to the same attributes will return a cloned copy. Otherwise, type conversion for each element is required. By default, a STRUCT is NOT in auto-buffering mode.
      Parameters:
      `enable` - - true enables auto-buffering; false disables auto-buffering

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `getAutoBuffering()`

    <!-- -->

    - #### getAutoBuffering

          public boolean getAutoBuffering()
                                   throws SQLException

      Deprecated. 
      Performance hint. Get the current auto-buffering state.
      Returns:
      the current state of auto-buffering

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `setAutoBuffering(boolean)`

    <!-- -->

    - #### getOracleDataFactory

          public OracleDataFactory getOracleDataFactory(Hashtable map,
                                                        String classname)
                                                 throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

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

    <!-- -->

    - #### dump

          public String dump()
                      throws SQLException

      Deprecated. 
      Create a string which show the contents of this Object and of all its component parts.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dump

          public static void dump(Object o,
                                  PrintStream ps)
                           throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dump

          public static void dump(Object o,
                                  PrintWriter pw)
                           throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/STRUCT.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ROWID.md)
- [Next Class](StructDescriptor.md)

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
