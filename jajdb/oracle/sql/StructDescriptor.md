Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/StructDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](STRUCT.md)
- [Next Class](TIMESTAMP.md)

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

## Class StructDescriptor

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.TypeDescriptor](TypeDescriptor.md)

  - - oracle.sql.StructDescriptor

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, [OracleData](../jdbc/OracleData.md), [OracleTypeMetaData](../jdbc/OracleTypeMetaData.md), [OracleTypeMetaData.Struct](../jdbc/OracleTypeMetaData.Struct.md), [ORAData](ORAData.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.


      public class StructDescriptor
      extends TypeDescriptor
      implements oracle.jdbc.internal.OracleTypeMetaData.Struct, Serializable

  Descriptor of a SQL structured object. (That is an SQL Object type). Its main responsibility is understanding how to convert between various representations of such a struct.
  There should be a method to return information about the fields (beyond their number. But there is no public representation for that.

  See Also:
  [`Connection.createStruct(java.lang.String, java.lang.Object[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStruct_java_lang_String_java_lang_Object_A_), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.internal.OracleTypeMetaData

      `oracle.jdbc.internal.OracleTypeMetaData.Array, oracle.jdbc.internal.OracleTypeMetaData.Opaque, oracle.jdbc.internal.OracleTypeMetaData.Struct`

    <!-- -->

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTypeMetaData](../jdbc/OracleTypeMetaData.md)

      [`OracleTypeMetaData.ArrayStorage`](../jdbc/OracleTypeMetaData.ArrayStorage.md)`, `[`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.sql.[TypeDescriptor](TypeDescriptor.md)

      [`ANYDATASETTOID`](TypeDescriptor.md)`, `[`ANYDATATOID`](TypeDescriptor.md)`, `[`ANYTYPETOID`](TypeDescriptor.md)`, `[`DEBUG_SERIALIZATION`](TypeDescriptor.md)`, `[`RAWTOID`](TypeDescriptor.md)`, `[`TYPECODE_BDOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_BFILE`](TypeDescriptor.md)`, `[`TYPECODE_BFLOAT`](TypeDescriptor.md)`, `[`TYPECODE_BLOB`](TypeDescriptor.md)`, `[`TYPECODE_BOOLEAN`](TypeDescriptor.md)`, `[`TYPECODE_CFILE`](TypeDescriptor.md)`, `[`TYPECODE_CHAR`](TypeDescriptor.md)`, `[`TYPECODE_CLOB`](TypeDescriptor.md)`, `[`TYPECODE_DATE`](TypeDescriptor.md)`, `[`TYPECODE_DECIMAL`](TypeDescriptor.md)`, `[`TYPECODE_DOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_ERRHP`](TypeDescriptor.md)`, `[`TYPECODE_FLOAT`](TypeDescriptor.md)`, `[`TYPECODE_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_DS`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_YM`](TypeDescriptor.md)`, `[`TYPECODE_ITABLE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_ARRAY`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOBJECT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JSTRUCT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_REF`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_STRUCT`](TypeDescriptor.md)`, `[`TYPECODE_MLSLABEL`](TypeDescriptor.md)`, `[`TYPECODE_NAMEDCOLLECTION`](TypeDescriptor.md)`, `[`TYPECODE_NCHAR`](TypeDescriptor.md)`, `[`TYPECODE_NCLOB`](TypeDescriptor.md)`, `[`TYPECODE_NONE`](TypeDescriptor.md)`, `[`TYPECODE_NUMBER`](TypeDescriptor.md)`, `[`TYPECODE_NVARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_OBJECT`](TypeDescriptor.md)`, `[`TYPECODE_OCTET`](TypeDescriptor.md)`, `[`TYPECODE_OPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_OTMFIRST`](TypeDescriptor.md)`, `[`TYPECODE_OTMLAST`](TypeDescriptor.md)`, `[`TYPECODE_PLS_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_PTR`](TypeDescriptor.md)`, `[`TYPECODE_RAW`](TypeDescriptor.md)`, `[`TYPECODE_REAL`](TypeDescriptor.md)`, `[`TYPECODE_RECORD`](TypeDescriptor.md)`, `[`TYPECODE_REF`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_SMALLINT`](TypeDescriptor.md)`, `[`TYPECODE_SQLXML`](TypeDescriptor.md)`, `[`TYPECODE_SYSFIRST`](TypeDescriptor.md)`, `[`TYPECODE_SYSLAST`](TypeDescriptor.md)`, `[`TYPECODE_TABLE`](TypeDescriptor.md)`, `[`TYPECODE_TIME`](TypeDescriptor.md)`, `[`TYPECODE_TIME_TZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_LTZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_TZ`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_UROWID`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_VARRAY`](TypeDescriptor.md)`, `[`XMLTYPETOID`](TypeDescriptor.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                             |
    |----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static StructDescriptor`                                                                                            | `createDescriptor``(oracle.sql.SQLName name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated.                                                                                                                                        |
    | `static StructDescriptor`                                                                                            | `createDescriptor``(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated.                                                                                                     |
    | `static StructDescriptor`                                                                                            | `createDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                 |
    | `static StructDescriptor`                                                                                            | `createDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated. <br>Descriptor factory. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `descType``()`<br>Deprecated. <br>Describe this type.                                                                                                                                                                                                                                                              |
    | [`AttributeDescriptor`](AttributeDescriptor.md)`[]`                                                                  | `getAttributesDescriptor``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getJavaClassName``()`<br>Deprecated. <br>Returns the external name of the JAVA_STRUCT type.                                                                                                                                                                                                                       |
    | [`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)                                                      | `getKind``()`<br>Deprecated. <br>Return the kind of type.                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getLanguage``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                                | `getLength``()`<br>Deprecated. <br>The number of fields in the Object Type.                                                                                                                                                                                                                                        |
    | `int`                                                                                                                | `getLocalAttributeCount``()`<br>Deprecated. <br>Returns the number of attributes defined in the subtype.                                                                                                                                                                                                           |
    | [`ResultSetMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true) | `getMetaData``()`<br>Deprecated. <br>Gets the metadata regarding this type.                                                                                                                                                                                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`                  | `getSubtypeNames``()`<br>Deprecated. <br>Returns the SQL type names of the direct subtypes.                                                                                                                                                                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getSupertypeName``()`<br>Deprecated. <br>Returns the SQL type name of the direct subtype.                                                                                                                                                                                                                         |
    | `int`                                                                                                                | `getTypeCode``()`<br>Deprecated. <br>Returns type code.                                                                                                                                                                                                                                                            |
    | `int`                                                                                                                | `getTypeVersion``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                            | `isFinalType``()`<br>Deprecated. <br>Indicates whether the object type is a final type.                                                                                                                                                                                                                            |
    | `boolean`                                                                                                            | `isInstantiable``()`<br>Deprecated. <br>Indicates whether the object type is instantiable.                                                                                                                                                                                                                         |
    | `boolean`                                                                                                            | `isJavaObject``()`<br>Deprecated. <br>Indicates whether the object type is a JAVA_STRUCT type or a STRUCT type.                                                                                                                                                                                                    |
    | `boolean`                                                                                                            | `isSubtype``()`<br>Deprecated. <br>Indicates whether the object type is a subtype.                                                                                                                                                                                                                                 |
    | [`Datum`](Datum.md)`[]`                                                                                              | `toOracleArray``(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attributes)`<br>Deprecated. <br>                                                                                                                                                                      |

    - ### Methods inherited from class oracle.sql.[TypeDescriptor](TypeDescriptor.md)

      [`convToUpperCase`](TypeDescriptor.md)`, `[`getConnectionDuringExceptionHandling`](TypeDescriptor.md)`, `[`getInternalTypeCode`](TypeDescriptor.md)`, `[`getName`](TypeDescriptor.md)`, `[`getPrecision`](TypeDescriptor.md)`, `[`getScale`](TypeDescriptor.md)`, `[`getSubtypeName`](TypeDescriptor.md)`, `[`getTypeCodeName`](TypeDescriptor.md)`, `[`initMetadataRecursively`](TypeDescriptor.md)`, `[`initNamesRecursively`](TypeDescriptor.md)`, `[`isTransient`](TypeDescriptor.md)`, `[`isV2available`](TypeDescriptor.md)`, `[`printXML`](TypeDescriptor.md)`, `[`printXML`](TypeDescriptor.md)`, `[`setConnection`](TypeDescriptor.md)`, `[`setPrecision`](TypeDescriptor.md)`, `[`setScale`](TypeDescriptor.md)`, `[`toDatum`](TypeDescriptor.md)`, `[`toJDBCObject`](TypeDescriptor.md)`, `[`toXMLString`](TypeDescriptor.md)`, `[`toXMLString`](TypeDescriptor.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.ACProxyable

      `getACProxy, setACProxy`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.[OracleTypeMetaData](../jdbc/OracleTypeMetaData.md)

      [`getName`](../jdbc/OracleTypeMetaData.md)`, `[`getSchemaName`](../jdbc/OracleTypeMetaData.md)`, `[`getSQLName`](../jdbc/OracleTypeMetaData.md)`, `[`getTypeCodeName`](../jdbc/OracleTypeMetaData.md)

<!-- -->

- - ### Method Detail

    - #### createDescriptor

          public static StructDescriptor createDescriptor(String name,
                                                          Connection conn)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `conn` - a Connection to a database

      Returns:
      the descriptor created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createDescriptor

          public static StructDescriptor createDescriptor(String name,
                                                          Connection conn,
                                                          boolean recurse,
                                                          boolean force)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `connection` - a Connection to a database

      `recurse` - a boolean to specify whether to create descriptors for component objects

      `force` - a boolean to specify whether to replace any cached descriptor.

      Returns:
      the descriptor created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createDescriptor

          public static StructDescriptor createDescriptor(oracle.sql.SQLName sqlName,
                                                          Connection conn,
                                                          boolean recurse,
                                                          boolean force)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `connection` - a Connection to a database

      `recurse` - a boolean to specify whether to create descriptors for component objects

      `force` - a boolean to specify whether to replace any cached descriptor.

      Returns:
      the descriptor created. **Use connection.createStruct intead**

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createDescriptor

          public static StructDescriptor createDescriptor(oracle.sql.SQLName name,
                                                          Connection conn)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `connection` - a Connection to a database

      Returns:
      the descriptor created. **Use connection.createStruct intead**

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getKind

          public OracleTypeMetaData.Kind getKind()

      Deprecated. 
      Description copied from interface: [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)
      Return the kind of type.
      Specified by:
      [`getKind`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Overrides:
      [`getKind`](TypeDescriptor.md) in class [`TypeDescriptor`](TypeDescriptor.md)

      Returns:
      the kind, STRUCT

    <!-- -->

    - #### getTypeCode

          public int getTypeCode()
                          throws SQLException

      Deprecated. 
      Description copied from class: [`TypeDescriptor`](TypeDescriptor.md)
      Returns type code.
      Specified by:
      [`getTypeCode`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Overrides:
      [`getTypeCode`](TypeDescriptor.md) in class [`TypeDescriptor`](TypeDescriptor.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeVersion

          public int getTypeVersion()
                             throws SQLException

      Deprecated. 
      Specified by:
      [`getTypeVersion`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAttributesDescriptor

          public AttributeDescriptor[] getAttributesDescriptor()

      Deprecated. 

    <!-- -->

    - #### getLength

          public int getLength()
                        throws SQLException

      Deprecated. 
      The number of fields in the Object Type.
      Specified by:
      [`getLength`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toOracleArray

          public Datum[] toOracleArray(Map attributes)
                                throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMetaData

          public ResultSetMetaData getMetaData()
                                        throws SQLException

      Deprecated. 
      Gets the metadata regarding this type. The return ResultSetMetaData contains the attribute name, attribute type id and attribute type precision information. The column index in ResultSetMetaData maps to the position of the attribute in a Struct (with the first attribute being at index 1).
      Specified by:
      [`getMetaData`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      a ResultSetMetaData object that contains the type info

      Throws:
      `if` - database access error occurs

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isFinalType

          public boolean isFinalType()
                              throws SQLException

      Deprecated. 
      Indicates whether the object type is a final type.
      Specified by:
      [`isFinalType`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      true if the object type is a final type and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isSubtype

          public boolean isSubtype()
                            throws SQLException

      Deprecated. 
      Indicates whether the object type is a subtype.
      Specified by:
      [`isSubtype`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      true if the object type is a subtype and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isInstantiable

          public boolean isInstantiable()
                                 throws SQLException

      Deprecated. 
      Indicates whether the object type is instantiable.
      Specified by:
      [`isInstantiable`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      true if the object type is instantiable and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isJavaObject

          public boolean isJavaObject()
                               throws SQLException

      Deprecated. 
      Indicates whether the object type is a JAVA_STRUCT type or a STRUCT type.
      Returns:
      true if the object type is a JAVA_STRUCT type and false if the object type is a STRUCT type.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getSupertypeName

          public String getSupertypeName()
                                  throws SQLException

      Deprecated. 
      Returns the SQL type name of the direct subtype.
      Specified by:
      [`getSupertypeName`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      the fully qualified name of the supertype. Returns null if the object type is not a subtype.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getLocalAttributeCount

          public int getLocalAttributeCount()
                                     throws SQLException

      Deprecated. 
      Returns the number of attributes defined in the subtype.
      Specified by:
      [`getLocalAttributeCount`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      number of subtype attributes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getSubtypeNames

          public String[] getSubtypeNames()
                                   throws SQLException

      Deprecated. 
      Returns the SQL type names of the direct subtypes.
      Specified by:
      [`getSubtypeNames`](../jdbc/OracleTypeMetaData.Struct.md) in interface [`OracleTypeMetaData.Struct`](../jdbc/OracleTypeMetaData.Struct.md)

      Returns:
      the fully qualifed name of the direct subtypes. Returns an empty String array if there is no subtypes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getJavaClassName

          public String getJavaClassName()
                                  throws SQLException

      Deprecated. 
      Returns the external name of the JAVA_STRUCT type.
      Returns:
      the JAVA_STRUCT's Java type name. Returns null if the object type is not a JAVA_STRUCT type.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getLanguage

          public String getLanguage()
                             throws SQLException

      Deprecated. 
      Returns:
      JAVA if this is a JAVA_STRUCT, SQL otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### descType

          public String descType()
                          throws SQLException

      Deprecated. 
      Describe this type.
      Returns:
      the type information.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/StructDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](STRUCT.md)
- [Next Class](TIMESTAMP.md)

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
