Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TypeDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMPTZ.md)
- Next Class

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

## Class TypeDescriptor

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.TypeDescriptor

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, [OracleData](../jdbc/OracleData.md), [OracleTypeMetaData](../jdbc/OracleTypeMetaData.md), [ORAData](ORAData.md)

  <!-- -->

  Direct Known Subclasses:
  [ArrayDescriptor](ArrayDescriptor.md), [OpaqueDescriptor](OpaqueDescriptor.md), [StructDescriptor](StructDescriptor.md)

  ------------------------------------------------------------------------



      public class TypeDescriptor
      extends Object
      implements oracle.jdbc.internal.OracleTypeMetaData, Serializable, ORAData, OracleData

  The descriptor of pre-defined types.
  See Also:
  [Serialized Form](../../serialized-form.md)

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

    | Modifier and Type | Field and Description       |
    |-------------------|-----------------------------|
    | `static byte[]`   | `ANYDATASETTOID`            |
    | `static byte[]`   | `ANYDATATOID`               |
    | `static byte[]`   | `ANYTYPETOID`               |
    | `static boolean`  | `DEBUG_SERIALIZATION`       |
    | `static byte[]`   | `RAWTOID`                   |
    | `static short`    | `TYPECODE_BDOUBLE`          |
    | `static short`    | `TYPECODE_BFILE`            |
    | `static short`    | `TYPECODE_BFLOAT`           |
    | `static short`    | `TYPECODE_BLOB`             |
    | `static short`    | `TYPECODE_BOOLEAN`          |
    | `static short`    | `TYPECODE_CFILE`            |
    | `static short`    | `TYPECODE_CHAR`             |
    | `static short`    | `TYPECODE_CLOB`             |
    | `static short`    | `TYPECODE_DATE`             |
    | `static short`    | `TYPECODE_DECIMAL`          |
    | `static short`    | `TYPECODE_DOUBLE`           |
    | `static short`    | `TYPECODE_ERRHP`            |
    | `static short`    | `TYPECODE_FLOAT`            |
    | `static short`    | `TYPECODE_INTEGER`          |
    | `static short`    | `TYPECODE_INTERVAL_DS`      |
    | `static short`    | `TYPECODE_INTERVAL_YM`      |
    | `static short`    | `TYPECODE_ITABLE`           |
    | `static short`    | `TYPECODE_JDBC_ARRAY`       |
    | `static short`    | `TYPECODE_JDBC_JOBJECT`     |
    | `static short`    | `TYPECODE_JDBC_JOPAQUE`     |
    | `static short`    | `TYPECODE_JDBC_JSTRUCT`     |
    | `static short`    | `TYPECODE_JDBC_REF`         |
    | `static short`    | `TYPECODE_JDBC_STRUCT`      |
    | `static short`    | `TYPECODE_MLSLABEL`         |
    | `static short`    | `TYPECODE_NAMEDCOLLECTION`  |
    | `static short`    | `TYPECODE_NCHAR`            |
    | `static short`    | `TYPECODE_NCLOB`            |
    | `static short`    | `TYPECODE_NONE`             |
    | `static short`    | `TYPECODE_NUMBER`           |
    | `static short`    | `TYPECODE_NVARCHAR2`        |
    | `static short`    | `TYPECODE_OBJECT`           |
    | `static short`    | `TYPECODE_OCTET`            |
    | `static short`    | `TYPECODE_OPAQUE`           |
    | `static short`    | `TYPECODE_OTMFIRST`         |
    | `static short`    | `TYPECODE_OTMLAST`          |
    | `static short`    | `TYPECODE_PLS_INTEGER`      |
    | `static short`    | `TYPECODE_PTR`              |
    | `static short`    | `TYPECODE_RAW`              |
    | `static short`    | `TYPECODE_REAL`             |
    | `static short`    | `TYPECODE_RECORD`           |
    | `static short`    | `TYPECODE_REF`              |
    | `static short`    | `TYPECODE_SIGNED16`         |
    | `static short`    | `TYPECODE_SIGNED32`         |
    | `static short`    | `TYPECODE_SIGNED8`          |
    | `static short`    | `TYPECODE_SMALLINT`         |
    | `static short`    | `TYPECODE_SQLXML`           |
    | `static short`    | `TYPECODE_SYSFIRST`         |
    | `static short`    | `TYPECODE_SYSLAST`          |
    | `static short`    | `TYPECODE_TABLE`            |
    | `static short`    | `TYPECODE_TIME`             |
    | `static short`    | `TYPECODE_TIME_TZ`          |
    | `static short`    | `TYPECODE_TIMESTAMP`        |
    | `static short`    | `TYPECODE_TIMESTAMP_LTZ`    |
    | `static short`    | `TYPECODE_TIMESTAMP_TZ`     |
    | `static short`    | `TYPECODE_UNSIGNED16`       |
    | `static short`    | `TYPECODE_UNSIGNED32`       |
    | `static short`    | `TYPECODE_UNSIGNED8`        |
    | `static short`    | `TYPECODE_UROWID`           |
    | `static short`    | `TYPECODE_VARCHAR`          |
    | `static short`    | `TYPECODE_VARCHAR2`         |
    | `static short`    | `TYPECODE_VARRAY`           |
    | `static byte[]`   | `XMLTYPETOID`               |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                                                                                                                                                 |
    |-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `TypeDescriptor``(short _typeCode)`                                                                                                                                                                                                                         |
    | `protected` | `TypeDescriptor``(short _typeCode, oracle.jdbc.oracore.OracleTypeADT type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                                                                  |
    | `protected` | `TypeDescriptor``(short _typeCode, oracle.sql.SQLName name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                                                                                 |
    | `protected` | `TypeDescriptor``(short _typeCode, oracle.sql.SQLName name, oracle.jdbc.oracore.OracleTypeADT type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`                                         |
    | `protected` | `TypeDescriptor``(short _typeCode, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                   |
    |----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `convToUpperCase``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Convert the String to UpperCase character by character                                                     |
    | `protected oracle.jdbc.internal.OracleConnection`                                                        | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                               |
    | `short`                                                                                                  | `getInternalTypeCode``()`                                                                                                                                                                                                                |
    | [`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)                                          | `getKind``()`<br>Return the kind of type.                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `getName``()`<br>Return fully qualified type name.                                                                                                                                                                                       |
    | `long`                                                                                                   | `getPrecision``()`                                                                                                                                                                                                                       |
    | `byte`                                                                                                   | `getScale``()`                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getSubtypeName``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn, byte[] image, long offset)`                                                                                                                                  |
    | `int`                                                                                                    | `getTypeCode``()`<br>Returns type code.                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `getTypeCodeName``()`<br>Returns the type code name.                                                                                                                                                                                     |
    | `void`                                                                                                   | `initMetadataRecursively``()`                                                                                                                                                                                                            |
    | `void`                                                                                                   | `initNamesRecursively``()`                                                                                                                                                                                                               |
    | `boolean`                                                                                                | `isTransient``()`                                                                                                                                                                                                                        |
    | `static boolean`                                                                                         | `isV2available``(byte[] toid)`                                                                                                                                                                                                           |
    | `void`                                                                                                   | `printXML``(`[`PrintStream`](http://download.oracle.com/javase/8/docs/api/java/io/PrintStream.html?is-external=true)` s)`<br>Print an XML representation of this type and all OracleTypes within.                                        |
    | `void`                                                                                                   | `printXML``(`[`PrintStream`](http://download.oracle.com/javase/8/docs/api/java/io/PrintStream.html?is-external=true)` stream, boolean fetchAllMetaDataAsNeeded)`<br>Print an XML representation of this type and all OracleTypes within. |
    | `void`                                                                                                   | `setConnection``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` connection)`                                                                                                   |
    | `void`                                                                                                   | `setPrecision``(long _precision)`                                                                                                                                                                                                        |
    | `void`                                                                                                   | `setScale``(byte _scale)`                                                                                                                                                                                                                |
    | [`Datum`](Datum.md)                                                                                      | `toDatum``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract an oracle.sql.Datum object.                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `toJDBCObject``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract a jdbc Object.                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `toXMLString``()`<br>Creates a String which is an XML representation of this type and all OracleTypes within.                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)          | `toXMLString``(boolean fetchAllMetaDataAsNeeded)`<br>Creates a String which is an XML representation of this type and all OracleTypes within.                                                                                            |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### DEBUG_SERIALIZATION

          public static boolean DEBUG_SERIALIZATION

    <!-- -->

    - #### RAWTOID

          public static final byte[] RAWTOID

    <!-- -->

    - #### ANYTYPETOID

          public static final byte[] ANYTYPETOID

    <!-- -->

    - #### ANYDATATOID

          public static final byte[] ANYDATATOID

    <!-- -->

    - #### ANYDATASETTOID

          public static final byte[] ANYDATASETTOID

    <!-- -->

    - #### XMLTYPETOID

          public static final byte[] XMLTYPETOID

    <!-- -->

    - #### TYPECODE_REF

          public static final short TYPECODE_REF

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_DATE

          public static final short TYPECODE_DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SIGNED8

          public static final short TYPECODE_SIGNED8

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SIGNED16

          public static final short TYPECODE_SIGNED16

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SIGNED32

          public static final short TYPECODE_SIGNED32

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_REAL

          public static final short TYPECODE_REAL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_DOUBLE

          public static final short TYPECODE_DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_BFLOAT

          public static final short TYPECODE_BFLOAT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_BDOUBLE

          public static final short TYPECODE_BDOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_FLOAT

          public static final short TYPECODE_FLOAT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NUMBER

          public static final short TYPECODE_NUMBER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_DECIMAL

          public static final short TYPECODE_DECIMAL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_UNSIGNED8

          public static final short TYPECODE_UNSIGNED8

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_UNSIGNED16

          public static final short TYPECODE_UNSIGNED16

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_UNSIGNED32

          public static final short TYPECODE_UNSIGNED32

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_OCTET

          public static final short TYPECODE_OCTET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SMALLINT

          public static final short TYPECODE_SMALLINT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_INTEGER

          public static final short TYPECODE_INTEGER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_RAW

          public static final short TYPECODE_RAW

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_PTR

          public static final short TYPECODE_PTR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_VARCHAR2

          public static final short TYPECODE_VARCHAR2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_CHAR

          public static final short TYPECODE_CHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_VARCHAR

          public static final short TYPECODE_VARCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_MLSLABEL

          public static final short TYPECODE_MLSLABEL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_VARRAY

          public static final short TYPECODE_VARRAY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TABLE

          public static final short TYPECODE_TABLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_OBJECT

          public static final short TYPECODE_OBJECT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_OPAQUE

          public static final short TYPECODE_OPAQUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NAMEDCOLLECTION

          public static final short TYPECODE_NAMEDCOLLECTION

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_BLOB

          public static final short TYPECODE_BLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_BFILE

          public static final short TYPECODE_BFILE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_CLOB

          public static final short TYPECODE_CLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_CFILE

          public static final short TYPECODE_CFILE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TIME

          public static final short TYPECODE_TIME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TIME_TZ

          public static final short TYPECODE_TIME_TZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TIMESTAMP

          public static final short TYPECODE_TIMESTAMP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TIMESTAMP_TZ

          public static final short TYPECODE_TIMESTAMP_TZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_TIMESTAMP_LTZ

          public static final short TYPECODE_TIMESTAMP_LTZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_INTERVAL_YM

          public static final short TYPECODE_INTERVAL_YM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_INTERVAL_DS

          public static final short TYPECODE_INTERVAL_DS

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_UROWID

          public static final short TYPECODE_UROWID

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_OTMFIRST

          public static final short TYPECODE_OTMFIRST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_OTMLAST

          public static final short TYPECODE_OTMLAST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SYSFIRST

          public static final short TYPECODE_SYSFIRST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SYSLAST

          public static final short TYPECODE_SYSLAST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_PLS_INTEGER

          public static final short TYPECODE_PLS_INTEGER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_ITABLE

          public static final short TYPECODE_ITABLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_RECORD

          public static final short TYPECODE_RECORD

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_BOOLEAN

          public static final short TYPECODE_BOOLEAN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NCHAR

          public static final short TYPECODE_NCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NVARCHAR2

          public static final short TYPECODE_NVARCHAR2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NCLOB

          public static final short TYPECODE_NCLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_NONE

          public static final short TYPECODE_NONE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_ERRHP

          public static final short TYPECODE_ERRHP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_JOBJECT

          public static final short TYPECODE_JDBC_JOBJECT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_STRUCT

          public static final short TYPECODE_JDBC_STRUCT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_ARRAY

          public static final short TYPECODE_JDBC_ARRAY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_JOPAQUE

          public static final short TYPECODE_JDBC_JOPAQUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_REF

          public static final short TYPECODE_JDBC_REF

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_JDBC_JSTRUCT

          public static final short TYPECODE_JDBC_JSTRUCT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPECODE_SQLXML

          public static final short TYPECODE_SQLXML

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### TypeDescriptor

          protected TypeDescriptor(short _typeCode)

    <!-- -->

    - #### TypeDescriptor

          protected TypeDescriptor(short _typeCode,
                                   String name,
                                   Connection conn)
                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TypeDescriptor

          protected TypeDescriptor(short _typeCode,
                                   oracle.sql.SQLName name,
                                   Connection conn)
                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TypeDescriptor

          protected TypeDescriptor(short _typeCode,
                                   oracle.sql.SQLName name,
                                   oracle.jdbc.oracore.OracleTypeADT type,
                                   Connection conn)
                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### TypeDescriptor

          protected TypeDescriptor(short _typeCode,
                                   oracle.jdbc.oracore.OracleTypeADT type,
                                   Connection conn)
                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getKind

          public OracleTypeMetaData.Kind getKind()

      Description copied from interface: [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)
      Return the kind of type.
      Specified by:
      [`getKind`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Returns:
      the kind, TYPE

    <!-- -->

    - #### getName

          public String getName()
                         throws SQLException

      Return fully qualified type name.
      Specified by:
      [`getName`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeCode

          public int getTypeCode()
                          throws SQLException

      Returns type code.
      Specified by:
      [`getTypeCode`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeCodeName

          public String getTypeCodeName()
                                 throws SQLException

      Returns the type code name.
      Specified by:
      [`getTypeCodeName`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getInternalTypeCode

          public short getInternalTypeCode()
                                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isV2available

          public static boolean isV2available(byte[] toid)

    <!-- -->

    - #### toDatum

          public Datum toDatum(Connection c)
                        throws SQLException

      Description copied from interface: [`ORAData`](ORAData.md)
      Extract an oracle.sql.Datum object.
      This method is invoked by setORAData() to extract a Datum. The implementation of this method must return the correct type of Datum.

      Although most implementation will ignore the connection, it is occassionally needed. For example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Specified by:
      [`toDatum`](ORAData.md) in interface [`ORAData`](ORAData.md)

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a Datum contaning the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

    <!-- -->

    - #### toJDBCObject

          public Object toJDBCObject(Connection c)
                              throws SQLException

      Description copied from interface: [`OracleData`](../jdbc/OracleData.md)
      Extract a jdbc Object.
      This method is invoked by setObject() to extract the jdbc Object. The implementation must return the jdbc Object that correctly represents the underlying SQLType.

      Although most implementation will ignore the connection, it is ocassionally needed. for example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Specified by:
      [`toJDBCObject`](../jdbc/OracleData.md) in interface [`OracleData`](../jdbc/OracleData.md)

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a jdbc Object contianing the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

    <!-- -->

    - #### isTransient

          public boolean isTransient()

    <!-- -->

    - #### setPrecision

          public void setPrecision(long _precision)

    <!-- -->

    - #### getPrecision

          public long getPrecision()

    <!-- -->

    - #### setScale

          public void setScale(byte _scale)

    <!-- -->

    - #### getScale

          public byte getScale()

    <!-- -->

    - #### setConnection

          public void setConnection(Connection connection)
                             throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSubtypeName

          public static String getSubtypeName(OracleConnection conn,
                                              byte[] image,
                                              long offset)
                                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### initMetadataRecursively

          public void initMetadataRecursively()
                                       throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### initNamesRecursively

          public void initNamesRecursively()
                                    throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toXMLString

          public String toXMLString()
                             throws SQLException

      Creates a String which is an XML representation of this type and all OracleTypes within. Metadata for object types and collections is relatively expensive to get from the server. Not all of it is necessary depending on how the TypeDescriptor is used. In normal operation it is fetched as needed. This method will provide a representation of this type in its current state without fetching additional data
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toXMLString

          public String toXMLString(boolean fetchAllMetaDataAsNeeded)
                             throws SQLException

      Creates a String which is an XML representation of this type and all OracleTypes within. Optionally causes any metadata which has not been previously fetched from the server to be obtained so as to provide a complete representation. See toXMLString()
      Parameters:
      `fetchAllMetaDataAsNeeded` - if set to true and if necessary the driver will fetch the metadata from the server

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### printXML

          public void printXML(PrintStream s)
                        throws SQLException

      Print an XML representation of this type and all OracleTypes within.
      Parameters:
      `s` - a PrintStream upon which to write

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### printXML

          public void printXML(PrintStream stream,
                               boolean fetchAllMetaDataAsNeeded)
                        throws SQLException

      Print an XML representation of this type and all OracleTypes within.
      Parameters:
      `stream` - a PrintStream upon which to write

      `fetchAllMetaDataAsNeeded` - if set to true and if necessary the driver will fetch the metadata from the server

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### convToUpperCase

          public static String convToUpperCase(String str)

      Convert the String to UpperCase character by character
      Parameters:
      `String` -

      Returns:
      String converted to Uppercase

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TypeDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](TIMESTAMPTZ.md)
- Next Class

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
