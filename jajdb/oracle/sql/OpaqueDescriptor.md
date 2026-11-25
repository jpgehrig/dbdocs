Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OpaqueDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OPAQUE.md)
- [Next Class](ORAData.md)

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

## Class OpaqueDescriptor

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.TypeDescriptor](TypeDescriptor.md)

  - - oracle.sql.OpaqueDescriptor

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, [OracleData](../jdbc/OracleData.md), [OracleTypeMetaData](../jdbc/OracleTypeMetaData.md), [OracleTypeMetaData.Opaque](../jdbc/OracleTypeMetaData.Opaque.md), [ORAData](ORAData.md)

  ------------------------------------------------------------------------

  Deprecated. 
  OPAQUE types cannot be created on the client side.


      public class OpaqueDescriptor
      extends TypeDescriptor
      implements oracle.jdbc.internal.OracleTypeMetaData.Opaque, Serializable

  Type descriptor of Opaque data type.
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

    - ### Fields inherited from class oracle.sql.[TypeDescriptor](TypeDescriptor.md)

      [`ANYDATASETTOID`](TypeDescriptor.md)`, `[`ANYDATATOID`](TypeDescriptor.md)`, `[`ANYTYPETOID`](TypeDescriptor.md)`, `[`DEBUG_SERIALIZATION`](TypeDescriptor.md)`, `[`RAWTOID`](TypeDescriptor.md)`, `[`TYPECODE_BDOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_BFILE`](TypeDescriptor.md)`, `[`TYPECODE_BFLOAT`](TypeDescriptor.md)`, `[`TYPECODE_BLOB`](TypeDescriptor.md)`, `[`TYPECODE_BOOLEAN`](TypeDescriptor.md)`, `[`TYPECODE_CFILE`](TypeDescriptor.md)`, `[`TYPECODE_CHAR`](TypeDescriptor.md)`, `[`TYPECODE_CLOB`](TypeDescriptor.md)`, `[`TYPECODE_DATE`](TypeDescriptor.md)`, `[`TYPECODE_DECIMAL`](TypeDescriptor.md)`, `[`TYPECODE_DOUBLE`](TypeDescriptor.md)`, `[`TYPECODE_ERRHP`](TypeDescriptor.md)`, `[`TYPECODE_FLOAT`](TypeDescriptor.md)`, `[`TYPECODE_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_DS`](TypeDescriptor.md)`, `[`TYPECODE_INTERVAL_YM`](TypeDescriptor.md)`, `[`TYPECODE_ITABLE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_ARRAY`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOBJECT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JOPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_JSTRUCT`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_REF`](TypeDescriptor.md)`, `[`TYPECODE_JDBC_STRUCT`](TypeDescriptor.md)`, `[`TYPECODE_MLSLABEL`](TypeDescriptor.md)`, `[`TYPECODE_NAMEDCOLLECTION`](TypeDescriptor.md)`, `[`TYPECODE_NCHAR`](TypeDescriptor.md)`, `[`TYPECODE_NCLOB`](TypeDescriptor.md)`, `[`TYPECODE_NONE`](TypeDescriptor.md)`, `[`TYPECODE_NUMBER`](TypeDescriptor.md)`, `[`TYPECODE_NVARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_OBJECT`](TypeDescriptor.md)`, `[`TYPECODE_OCTET`](TypeDescriptor.md)`, `[`TYPECODE_OPAQUE`](TypeDescriptor.md)`, `[`TYPECODE_OTMFIRST`](TypeDescriptor.md)`, `[`TYPECODE_OTMLAST`](TypeDescriptor.md)`, `[`TYPECODE_PLS_INTEGER`](TypeDescriptor.md)`, `[`TYPECODE_PTR`](TypeDescriptor.md)`, `[`TYPECODE_RAW`](TypeDescriptor.md)`, `[`TYPECODE_REAL`](TypeDescriptor.md)`, `[`TYPECODE_RECORD`](TypeDescriptor.md)`, `[`TYPECODE_REF`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_SIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_SMALLINT`](TypeDescriptor.md)`, `[`TYPECODE_SQLXML`](TypeDescriptor.md)`, `[`TYPECODE_SYSFIRST`](TypeDescriptor.md)`, `[`TYPECODE_SYSLAST`](TypeDescriptor.md)`, `[`TYPECODE_TABLE`](TypeDescriptor.md)`, `[`TYPECODE_TIME`](TypeDescriptor.md)`, `[`TYPECODE_TIME_TZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_LTZ`](TypeDescriptor.md)`, `[`TYPECODE_TIMESTAMP_TZ`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED16`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED32`](TypeDescriptor.md)`, `[`TYPECODE_UNSIGNED8`](TypeDescriptor.md)`, `[`TYPECODE_UROWID`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR`](TypeDescriptor.md)`, `[`TYPECODE_VARCHAR2`](TypeDescriptor.md)`, `[`TYPECODE_VARRAY`](TypeDescriptor.md)`, `[`XMLTYPETOID`](TypeDescriptor.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                                                             |
    |-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static OpaqueDescriptor`                                                                       | `createDescriptor``(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                                                             |
    | `static OpaqueDescriptor`                                                                       | `createDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `descType``()`<br>Deprecated. <br>Describe this type.                                                                                                                                                                                                                              |
    | [`OracleTypeMetaData.Kind`](../jdbc/OracleTypeMetaData.Kind.md)                                 | `getKind``()`<br>Deprecated. <br>Return the kind of type.                                                                                                                                                                                                                          |
    | `long`                                                                                          | `getMaxLength``()`<br>Deprecated. <br>Return the maximun number of bytes this opaque object can hold.                                                                                                                                                                              |
    | `int`                                                                                           | `getTypeCode``()`<br>Deprecated. <br>Return the type code: OracleTypes.SQLXML if type is SYS.XMLTYPE else return the OPAQUE type code OracleTypes.OPAQUE                                                                                                                           |
    | `boolean`                                                                                       | `hasFixedSize``()`<br>Deprecated. <br>Indicates whether the Opaque type has fixed size.                                                                                                                                                                                            |
    | `boolean`                                                                                       | `hasUnboundedSize``()`<br>Deprecated. <br>Indicates whether the Opaque type has unbounded size ().                                                                                                                                                                                 |
    | `boolean`                                                                                       | `isModeledInC``()`<br>Deprecated. <br>Indicates whether the Opaque type is modelled in C language.                                                                                                                                                                                 |
    | `boolean`                                                                                       | `isTrustedLibrary``()`<br>Deprecated. <br>Indicates whether the Trusted Library implementing Support functions are specified for the Opaque type.                                                                                                                                  |

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

          public static OpaqueDescriptor createDescriptor(String name,
                                                          Connection conn)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a String naming the type. (Not necessarily fully qualified)

      `conn` - a Connection to a database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createDescriptor

          public static OpaqueDescriptor createDescriptor(oracle.sql.SQLName sqlName,
                                                          Connection conn)
                                                   throws SQLException

      Deprecated. 
      Descriptor factory. Lookup the name in the database, and determine the characteristics of this array.
      Parameters:
      `name` - a SQLName

      `connection` - a Connection to a database

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
      the kind, OPAQUE

    <!-- -->

    - #### getTypeCode

          public int getTypeCode()
                          throws SQLException

      Deprecated. 
      Return the type code: OracleTypes.SQLXML if type is SYS.XMLTYPE else return the OPAQUE type code OracleTypes.OPAQUE
      Specified by:
      [`getTypeCode`](../jdbc/OracleTypeMetaData.md) in interface [`OracleTypeMetaData`](../jdbc/OracleTypeMetaData.md)

      Overrides:
      [`getTypeCode`](TypeDescriptor.md) in class [`TypeDescriptor`](TypeDescriptor.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxLength

          public long getMaxLength()
                            throws SQLException

      Deprecated. 
      Return the maximun number of bytes this opaque object can hold.
      Specified by:
      [`getMaxLength`](../jdbc/OracleTypeMetaData.Opaque.md) in interface [`OracleTypeMetaData.Opaque`](../jdbc/OracleTypeMetaData.Opaque.md)

      Returns:
      the maximum opaque size; return 0 if unbounded.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isTrustedLibrary

          public boolean isTrustedLibrary()
                                   throws SQLException

      Deprecated. 
      Indicates whether the Trusted Library implementing Support functions are specified for the Opaque type. This is the case for internal Opaque Types that are modeled in C.
      Specified by:
      [`isTrustedLibrary`](../jdbc/OracleTypeMetaData.Opaque.md) in interface [`OracleTypeMetaData.Opaque`](../jdbc/OracleTypeMetaData.Opaque.md)

      Returns:
      true if the Trusted Library implementing Support functions are specified; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isModeledInC

          public boolean isModeledInC()
                               throws SQLException

      Deprecated. 
      Indicates whether the Opaque type is modelled in C language.
      Specified by:
      [`isModeledInC`](../jdbc/OracleTypeMetaData.Opaque.md) in interface [`OracleTypeMetaData.Opaque`](../jdbc/OracleTypeMetaData.Opaque.md)

      Returns:
      true if the Opaque type is modelled in C language; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### hasUnboundedSize

          public boolean hasUnboundedSize()
                                   throws SQLException

      Deprecated. 
      Indicates whether the Opaque type has unbounded size ().
      Specified by:
      [`hasUnboundedSize`](../jdbc/OracleTypeMetaData.Opaque.md) in interface [`OracleTypeMetaData.Opaque`](../jdbc/OracleTypeMetaData.Opaque.md)

      Returns:
      true if the Opaque type hsa unbounded size; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### hasFixedSize

          public boolean hasFixedSize()
                               throws SQLException

      Deprecated. 
      Indicates whether the Opaque type has fixed size.
      Specified by:
      [`hasFixedSize`](../jdbc/OracleTypeMetaData.Opaque.md) in interface [`OracleTypeMetaData.Opaque`](../jdbc/OracleTypeMetaData.Opaque.md)

      Returns:
      true if the Opaque type has fixed size; false, otherwise.

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
- [Use](class-use/OpaqueDescriptor.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OPAQUE.md)
- [Next Class](ORAData.md)

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
