Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ArrayDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ARRAY.md)
- [Next Class](AttributeDescriptor.md)

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

## Class ArrayDescriptor

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.TypeDescriptor](TypeDescriptor.md)

  - - oracle.sql.ArrayDescriptor

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, [OracleData](../jdbc/OracleData.md), [OracleTypeMetaData](../jdbc/OracleTypeMetaData.md), [OracleTypeMetaData.Array](../jdbc/OracleTypeMetaData.Array.md), [ORAData](ORAData.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly.


      public class ArrayDescriptor
      extends TypeDescriptor
      implements oracle.jdbc.internal.OracleTypeMetaData.Array, Serializable

  Describes an array class. In Oracle 8 all arrays are named types.
  See Also:
  [`Connection.createArrayOf(java.lang.String, java.lang.Object[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createArrayOf_java_lang_String_java_lang_Object_A_), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.internal.OracleTypeMetaData

      `oracle.jdbc.internal.OracleTypeMetaData.Array, oracle.jdbc.internal.OracleTypeMetaData.Opaque, oracle.jdbc.internal.OracleTypeMetaData.Struct`

    <!-- -->

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTypeMetaData](../jdbc/OracleTypeMetaData.md)

      [`OracleTypeMetaData.ArrayStorage`](../jdbc/OracleTypeMetaData.ArrayStorage.md)`, `[`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                    |
    |-------------------|------------------------------------------|
    | `static int`      | `CACHE_ALL`<br>Deprecated. <br>          |
    | `static int`      | `CACHE_LAST`<br>Deprecated. <br>         |
    | `static int`      | `CACHE_NONE`<br>Deprecated. <br>         |
    | `static int`      | `TYPE_NESTED_TABLE`<br>Deprecated. <br>  |
    | `static int`      | `TYPE_VARRAY`<br>Deprecated. <br>        |

    - ### Fields inherited from class oracle.sql.[TypeDescriptor](TypeDescriptor.md)

      [`ANYDATASETTOID`](TypeDescriptor.md)`, `[`ANYDATATOID`](TypeDescriptor.md)`, `[`ANYTYPETOID`](TypeDescriptor.md)`, `[`DEBUG_SERIALIZATION`](TypeDescriptor.md)`, `[`RAWTOID`](TypeDescriptor.md)`, `[`TYPECODE_BDOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_BFILE`](TypeDescriptor.md)`, `[`TYPECODE_BFLOAT`](TypeDescriptor.md)`, `[`TYPECODE_BLOB`](TypeDescriptor.md)`, `[`TYPECODE_BOOLEAN`](TypeDescriptor.md)`, `[`TYPECODE_CFILE`](TypeDescriptor.md)`, `[`TYPECODE_CHAR`](TypeDescriptor.md)`, `[`TYPECODE_CLOB`](TypeDescriptor.md)`, `[`TYPECODE_DATE`](TypeDescriptor.md)`, `[`TYPECODE_DECIMAL`](TypeDescriptor.md)`, `[`TYPECODE_DOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_ERRHP`](TypeDescriptor.md)`, `[`TYPECODE_FLOAT`](TypeDescriptor.md)`, `[`TYPECODE_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_DS`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_YM`](TypeDescriptor.md)`, `[`TYPECODE_ITABLE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_ARRAY`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOBJECT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JSTRUCT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_REF`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_STRUCT`](TypeDescriptor.md)`, `[`TYPECODE_MLSLABEL`](TypeDescriptor.md)`, `[`TYPECODE_NAMEDCOLLECTION`](TypeDescriptor.md)`, `[`TYPECODE_NCHAR`](TypeDescriptor.md)`, `[`TYPECODE_NCLOB`](TypeDescriptor.md)`, `[`TYPECODE_NONE`](TypeDescriptor.md)`, `[`TYPECODE_NUMBER`](TypeDescriptor.md)`, `[`TYPECODE_NVARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_OBJECT`](TypeDescriptor.md)`, `[`TYPECODE_OCTET`](TypeDescriptor.md)`, `[`TYPECODE_OPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_OTMFIRST`](TypeDescriptor.md)`, `[`TYPECODE_OTMLAST`](TypeDescriptor.md)`, `[`TYPECODE_PLS_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_PTR`](TypeDescriptor.md)`, `[`TYPECODE_RAW`](TypeDescriptor.md)`, `[`TYPECODE_REAL`](TypeDescriptor.md)`, `[`TYPECODE_RECORD`](TypeDescriptor.md)`, `[`TYPECODE_REF`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_SMALLINT`](TypeDescriptor.md)`, `[`TYPECODE_SQLXML`](TypeDescriptor.md)`, `[`TYPECODE_SYSFIRST`](TypeDescriptor.md)`, `[`TYPECODE_SYSLAST`](TypeDescriptor.md)`, `[`TYPECODE_TABLE`](TypeDescriptor.md)`, `[`TYPECODE_TIME`](TypeDescriptor.md)`, `[`TYPECODE_TIME_TZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_LTZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_TZ`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_UROWID`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_VARRAY`](TypeDescriptor.md)`, `[`XMLTYPETOID`](TypeDescriptor.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                      |
    |------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static ArrayDescriptor`                                                                             | `createDescriptor``(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                                                                                                                                      |
    | `static ArrayDescriptor`                                                                             | `createDescriptor``(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated. <br>Descriptor factory.                                                                                                                      |
    | `static ArrayDescriptor`                                                                             | `createDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                                                          |
    | `static ArrayDescriptor`                                                                             | `createDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated. <br>Descriptor factory.                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `descType``()`<br>Deprecated. <br>Describe the collection type.                                                                                                                                                                                                                                                                                             |
    | [`OracleTypeMetaData.ArrayStorage`](../jdbc/OracleTypeMetaData.ArrayStorage.md)                      | `getArrayStorage``()`<br>Deprecated. <br>Return the database type of the array.                                                                                                                                                                                                                                                                             |
    | `int`                                                                                                | `getArrayType``()`<br>Deprecated. <br>Return the database type of the array.                                                                                                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)      | `getBaseName``()`<br>Deprecated. <br>In case the elements are named types the fully qualified name of their type.Otherwise, return type name used by the database                                                                                                                                                                                           |
    | `int`                                                                                                | `getBaseType``()`<br>Deprecated. <br>Return element's type code.                                                                                                                                                                                                                                                                                            |
    | [`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)                                      | `getKind``()`<br>Deprecated. <br>Return the kind of type.                                                                                                                                                                                                                                                                                                   |
    | `long`                                                                                               | `getMaxLength``()`<br>Deprecated. <br>Return the maximun number of elements this array object can hold.                                                                                                                                                                                                                                                     |
    | `int`                                                                                                | `getTypeCode``()`<br>Deprecated. <br>Returns type code.                                                                                                                                                                                                                                                                                                     |
    | `byte[]`                                                                                             | `toBytes``(oracle.jdbc.internal.OracleArray s, `[`Datum`](Datum.md)` sDatum, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                                                               |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`  | `toJavaArray``(oracle.jdbc.internal.OracleArray s, `[`Datum`](Datum.md)` sDatum, long beginIdx, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes, s.objectArray may be modified if 'keepLocalCopy' is true |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | `toNumericArray``(oracle.jdbc.internal.OracleArray array, `[`Datum`](Datum.md)` arrayDatum, long beginIdx, int count, int type, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                                                                                                 |
    | [`Datum`](Datum.md)`[]`                                                                              | `toOracleArray``(oracle.jdbc.internal.OracleArray s, `[`Datum`](Datum.md)` sDatum, long beginIdx, int count, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                               |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `toResultSet``(`[`ARRAY`](ARRAY.md)` array, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                                                             |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `toResultSet``(oracle.jdbc.internal.OracleArray array, `[`Datum`](Datum.md)` arrayDatum, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `toResultSetFromImage``(oracle.jdbc.internal.OracleArray array, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map)`<br>Deprecated. <br>                                                                                                                                                |

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

- - ### Field Detail

    - #### TYPE_VARRAY

          public static final int TYPE_VARRAY

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPE_NESTED_TABLE

          public static final int TYPE_NESTED_TABLE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CACHE_NONE

          public static final int CACHE_NONE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CACHE_ALL

          public static final int CACHE_ALL

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CACHE_LAST

          public static final int CACHE_LAST

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### createDescriptor

          public static ArrayDescriptor createDescriptor(String name,
                                                         Connection conn)
                                                  throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `connection` - a Connection to a database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the name does not name an array type.

    <!-- -->

    - #### createDescriptor

          public static ArrayDescriptor createDescriptor(String name,
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
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the name does not name an array type.

    <!-- -->

    - #### createDescriptor

          public static ArrayDescriptor createDescriptor(oracle.sql.SQLName sqlName,
                                                         Connection conn)
                                                  throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a SQLName with the name of the type.

      `connection` - a Connection to a database

      Returns:
      the descriptor created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the name does not name an array type.

    <!-- -->

    - #### createDescriptor

          public static ArrayDescriptor createDescriptor(oracle.sql.SQLName sqlName,
                                                         Connection conn,
                                                         boolean recurse,
                                                         boolean force)
                                                  throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a SQLName with the name of the type.

      `connection` - a Connection to a database

      `recurse` - a boolean to specify whether to create descriptors for component objects

      `force` - a boolean to specify whether to replace any cached descriptor.

      Returns:
      the descriptor created.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the name does not name an array type.

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
      the kind, ARRAY

    <!-- -->

    - #### getBaseType

          public int getBaseType()
                          throws SQLException

      Deprecated. 
      Return element's type code.
      Specified by:
      [`getBaseType`](../jdbc/OracleTypeMetaData.Array.md) in interface [`OracleTypeMetaData.Array`](../jdbc/OracleTypeMetaData.Array.md)

      Returns:
      the type code of elements of the array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBaseName

          public String getBaseName()
                             throws SQLException

      Deprecated. 
      In case the elements are named types the fully qualified name of their type.Otherwise, return type name used by the database
      Specified by:
      [`getBaseName`](../jdbc/OracleTypeMetaData.Array.md) in interface [`OracleTypeMetaData.Array`](../jdbc/OracleTypeMetaData.Array.md)

      Returns:
      the name of the base type.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the element's type is not named.

    <!-- -->

    - #### getArrayStorage

          public OracleTypeMetaData.ArrayStorage getArrayStorage()
                                                          throws SQLException

      Deprecated. 
      Return the database type of the array. The possible return values are OracleTypeMetaData.ArrayStorage. Either as a nested table or VARRAY.
      Specified by:
      [`getArrayStorage`](../jdbc/OracleTypeMetaData.Array.md) in interface [`OracleTypeMetaData.Array`](../jdbc/OracleTypeMetaData.Array.md)

      Returns:
      how the array is stored in the database.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getArrayType

          public int getArrayType()
                           throws SQLException

      Deprecated. 
      Return the database type of the array. The possible return values are ArrayDescriptor.TYPE_VARRAY and ArrayDescriptor.TYPE_NESTED_TABLE.
      Returns:
      database array type.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxLength

          public long getMaxLength()
                            throws SQLException

      Deprecated. 
      Return the maximun number of elements this array object can hold.
      Specified by:
      [`getMaxLength`](../jdbc/OracleTypeMetaData.Array.md) in interface [`OracleTypeMetaData.Array`](../jdbc/OracleTypeMetaData.Array.md)

      Returns:
      the maximum array size; return 0 if no limit.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### descType

          public String descType()
                          throws SQLException

      Deprecated. 
      Describe the collection type.
      Returns:
      the type information

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### toBytes

          public byte[] toBytes(oracle.jdbc.internal.OracleArray s,
                                Datum sDatum,
                                boolean keepLocalCopy)
                         throws SQLException

      Deprecated. 
      Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toOracleArray

          public Datum[] toOracleArray(oracle.jdbc.internal.OracleArray s,
                                       Datum sDatum,
                                       long beginIdx,
                                       int count,
                                       boolean keepLocalCopy)
                                throws SQLException

      Deprecated. 
      Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toJavaArray

          public Object[] toJavaArray(oracle.jdbc.internal.OracleArray s,
                                      Datum sDatum,
                                      long beginIdx,
                                      int count,
                                      Map map,
                                      boolean keepLocalCopy)
                               throws SQLException

      Deprecated. 
      Side Effect: array.datumArray, array.bytes, s.objectArray may be modified if 'keepLocalCopy' is true
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toResultSet

          public ResultSet toResultSet(ARRAY array,
                                       long index,
                                       int count,
                                       Map map,
                                       boolean saveLocalCopy)
                                throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toResultSet

          public ResultSet toResultSet(oracle.jdbc.internal.OracleArray array,
                                       Datum arrayDatum,
                                       long index,
                                       int count,
                                       Map map,
                                       boolean saveLocalCopy)
                                throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toResultSetFromImage

          public ResultSet toResultSetFromImage(oracle.jdbc.internal.OracleArray array,
                                                long index,
                                                int count,
                                                Map map)
                                         throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toNumericArray

          public Object toNumericArray(oracle.jdbc.internal.OracleArray array,
                                       Datum arrayDatum,
                                       long beginIdx,
                                       int count,
                                       int type,
                                       boolean saveLocalCopy)
                                throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

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

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ArrayDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ARRAY.md)
- [Next Class](AttributeDescriptor.md)

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
