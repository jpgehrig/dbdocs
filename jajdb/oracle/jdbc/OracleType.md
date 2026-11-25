Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleType.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTranslatingConnection.SqlTranslationVersion.md)
- [Next Class](OracleTypeMetaData.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

oracle.jdbc

## Enum OracleType

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<OracleType\>

  - - oracle.jdbc.OracleType

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleType\>, [SQLType](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)

  ------------------------------------------------------------------------



      public enum OracleType
      extends Enum<OracleType>
      implements SQLType

  These are all the types documented in Oracle? Database SQL Language Reference 12c Release 1. The JDBC driver does not necessarily support every type.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `ANYDATA`                                                                                                                  |
    | `ANYDATASET`                                                                                                               |
    | `ANYTYPE`                                                                                                                  |
    | `BFILE`                                                                                                                    |
    | `BINARY_DOUBLE`                                                                                                            |
    | `BINARY_FLOAT`                                                                                                             |
    | `BLOB`                                                                                                                     |
    | `CHAR`                                                                                                                     |
    | `CLOB`                                                                                                                     |
    | `DATE`                                                                                                                     |
    | `DBURITYPE`                                                                                                                |
    | `FLOAT`                                                                                                                    |
    | `HTTPURITYPE`                                                                                                              |
    | `INTERVAL_DAY_TO_SECOND`                                                                                                   |
    | `INTERVAL_YEAR_TO_MONTH`                                                                                                   |
    | `LONG`                                                                                                                     |
    | `LONG_RAW`                                                                                                                 |
    | `NCHAR`                                                                                                                    |
    | `NCLOB`                                                                                                                    |
    | `NESTED_TABLE`                                                                                                             |
    | `NUMBER`                                                                                                                   |
    | `NVARCHAR`                                                                                                                 |
    | `OBJECT`                                                                                                                   |
    | `ORDAUDIO`                                                                                                                 |
    | `ORDDICOM`                                                                                                                 |
    | `ORDDOC`                                                                                                                   |
    | `ORDIMAGE`                                                                                                                 |
    | `ORDVIDEO`                                                                                                                 |
    | `PLSQL_BOOLEAN`<br>PLSQL_BOOLEAN binds BOOLEAN type for input/output parameters when executing a PLSQL function/procedure. |
    | `RAW`                                                                                                                      |
    | `REF`                                                                                                                      |
    | `ROWID`                                                                                                                    |
    | `SDO_GEOMETRY`                                                                                                             |
    | `SDO_GEORASTER`                                                                                                            |
    | `SDO_TOPO_GEOMETRY`                                                                                                        |
    | `SI_AVERAGE_COLOR`                                                                                                         |
    | `SI_COLOR`                                                                                                                 |
    | `SI_COLOR_HISTOGRAM`                                                                                                       |
    | `SI_FEATURE_LIST`                                                                                                          |
    | `SI_POSITIONAL_COLOR`                                                                                                      |
    | `SI_STILL_IMAGE`                                                                                                           |
    | `SI_TEXTURE`                                                                                                               |
    | `TIMESTAMP`                                                                                                                |
    | `TIMESTAMP_WITH_LOCAL_TIME_ZONE`                                                                                           |
    | `TIMESTAMP_WITH_TIME_ZONE`                                                                                                 |
    | `UROWID`                                                                                                                   |
    | `VARCHAR2`                                                                                                                 |
    | `VARRAY`                                                                                                                   |
    | `XDBURITYPE`                                                                                                               |
    | `XMLTYPE`                                                                                                                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                 | Method and Description                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `getName``()`                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)   | `getVendor``()`                                                                                                                                                                        |
    | [`Integer`](http://download.oracle.com/javase/8/docs/api/java/lang/Integer.html?is-external=true) | `getVendorTypeNumber``()`                                                                                                                                                              |
    | `boolean`                                                                                         | `isNationalCharacterSet``()`<br>Does this type use the national character set?                                                                                                         |
    | `boolean`                                                                                         | `isSupported``()`<br>Does this driver support this database type?                                                                                                                      |
    | `static OracleType`                                                                               | `toOracleType``(int oracleTypesConst)`<br>Returns the OracleType corresponding to the int constant defined in OracleTypes.                                                             |
    | `static OracleType`                                                                               | `toOracleType``(`[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` sqlType)`<br>Returns the OracleType corresponding to SQLType.       |
    | `static OracleType`                                                                               | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static OracleType[]`                                                                             | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### VARCHAR2

          public static final OracleType VARCHAR2

    <!-- -->

    - #### NVARCHAR

          public static final OracleType NVARCHAR

    <!-- -->

    - #### NUMBER

          public static final OracleType NUMBER

    <!-- -->

    - #### FLOAT

          public static final OracleType FLOAT

    <!-- -->

    - #### LONG

          public static final OracleType LONG

    <!-- -->

    - #### DATE

          public static final OracleType DATE

    <!-- -->

    - #### BINARY_FLOAT

          public static final OracleType BINARY_FLOAT

    <!-- -->

    - #### BINARY_DOUBLE

          public static final OracleType BINARY_DOUBLE

    <!-- -->

    - #### TIMESTAMP

          public static final OracleType TIMESTAMP

    <!-- -->

    - #### TIMESTAMP_WITH_TIME_ZONE

          public static final OracleType TIMESTAMP_WITH_TIME_ZONE

    <!-- -->

    - #### TIMESTAMP_WITH_LOCAL_TIME_ZONE

          public static final OracleType TIMESTAMP_WITH_LOCAL_TIME_ZONE

    <!-- -->

    - #### INTERVAL_YEAR_TO_MONTH

          public static final OracleType INTERVAL_YEAR_TO_MONTH

    <!-- -->

    - #### INTERVAL_DAY_TO_SECOND

          public static final OracleType INTERVAL_DAY_TO_SECOND

    <!-- -->

    - #### PLSQL_BOOLEAN

          public static final OracleType PLSQL_BOOLEAN

      PLSQL_BOOLEAN binds BOOLEAN type for input/output parameters when executing a PLSQL function/procedure. Only available for thin driver.
      Since:
      12.2

    <!-- -->

    - #### RAW

          public static final OracleType RAW

    <!-- -->

    - #### LONG_RAW

          public static final OracleType LONG_RAW

    <!-- -->

    - #### ROWID

          public static final OracleType ROWID

    <!-- -->

    - #### UROWID

          public static final OracleType UROWID

    <!-- -->

    - #### CHAR

          public static final OracleType CHAR

    <!-- -->

    - #### NCHAR

          public static final OracleType NCHAR

    <!-- -->

    - #### CLOB

          public static final OracleType CLOB

    <!-- -->

    - #### NCLOB

          public static final OracleType NCLOB

    <!-- -->

    - #### BLOB

          public static final OracleType BLOB

    <!-- -->

    - #### BFILE

          public static final OracleType BFILE

    <!-- -->

    - #### OBJECT

          public static final OracleType OBJECT

    <!-- -->

    - #### REF

          public static final OracleType REF

    <!-- -->

    - #### VARRAY

          public static final OracleType VARRAY

    <!-- -->

    - #### NESTED_TABLE

          public static final OracleType NESTED_TABLE

    <!-- -->

    - #### ANYTYPE

          public static final OracleType ANYTYPE

    <!-- -->

    - #### ANYDATA

          public static final OracleType ANYDATA

    <!-- -->

    - #### ANYDATASET

          public static final OracleType ANYDATASET

    <!-- -->

    - #### XMLTYPE

          public static final OracleType XMLTYPE

    <!-- -->

    - #### HTTPURITYPE

          public static final OracleType HTTPURITYPE

    <!-- -->

    - #### XDBURITYPE

          public static final OracleType XDBURITYPE

    <!-- -->

    - #### DBURITYPE

          public static final OracleType DBURITYPE

    <!-- -->

    - #### SDO_GEOMETRY

          public static final OracleType SDO_GEOMETRY

    <!-- -->

    - #### SDO_TOPO_GEOMETRY

          public static final OracleType SDO_TOPO_GEOMETRY

    <!-- -->

    - #### SDO_GEORASTER

          public static final OracleType SDO_GEORASTER

    <!-- -->

    - #### ORDAUDIO

          public static final OracleType ORDAUDIO

    <!-- -->

    - #### ORDDICOM

          public static final OracleType ORDDICOM

    <!-- -->

    - #### ORDDOC

          public static final OracleType ORDDOC

    <!-- -->

    - #### ORDIMAGE

          public static final OracleType ORDIMAGE

    <!-- -->

    - #### ORDVIDEO

          public static final OracleType ORDVIDEO

    <!-- -->

    - #### SI_AVERAGE_COLOR

          public static final OracleType SI_AVERAGE_COLOR

    <!-- -->

    - #### SI_COLOR

          public static final OracleType SI_COLOR

    <!-- -->

    - #### SI_COLOR_HISTOGRAM

          public static final OracleType SI_COLOR_HISTOGRAM

    <!-- -->

    - #### SI_FEATURE_LIST

          public static final OracleType SI_FEATURE_LIST

    <!-- -->

    - #### SI_POSITIONAL_COLOR

          public static final OracleType SI_POSITIONAL_COLOR

    <!-- -->

    - #### SI_STILL_IMAGE

          public static final OracleType SI_STILL_IMAGE

    <!-- -->

    - #### SI_TEXTURE

          public static final OracleType SI_TEXTURE

  <!-- -->

  - ### Method Detail

    - #### values

          public static OracleType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OracleType c : OracleType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OracleType valueOf(String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      [`IllegalArgumentException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if this enum type has no constant with the specified name

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if the argument is null

    <!-- -->

    - #### toOracleType

          public static OracleType toOracleType(SQLType sqlType)
                                         throws SQLException

      Returns the OracleType corresponding to SQLType.
      Parameters:
      `sqlType` -

      Returns:
      corresponding OracleType

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

    <!-- -->

    - #### toOracleType

          public static OracleType toOracleType(int oracleTypesConst)
                                         throws SQLException

      Returns the OracleType corresponding to the int constant defined in OracleTypes.
      Parameters:
      `oracleTypesConst` - an int value defined in OracleTypes.

      Returns:
      the corresponding OracleType.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is no corresponding OracleType.

    <!-- -->

    - #### getName

          public String getName()

      Specified by:
      [`getName`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true#getName__) in interface [`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)

    <!-- -->

    - #### getVendor

          public String getVendor()

      Specified by:
      [`getVendor`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true#getVendor__) in interface [`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)

    <!-- -->

    - #### getVendorTypeNumber

          public Integer getVendorTypeNumber()

      Specified by:
      [`getVendorTypeNumber`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true#getVendorTypeNumber__) in interface [`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)

    <!-- -->

    - #### isNationalCharacterSet

          public boolean isNationalCharacterSet()

      Does this type use the national character set?
      Returns:
      true iff this type uses the national character set

      Since:
      12.2

    <!-- -->

    - #### isSupported

          public boolean isSupported()

      Does this driver support this database type?
      Returns:
      true iff this driver supports this database type

      Since:
      12.2

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleType.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTranslatingConnection.SqlTranslationVersion.md)
- [Next Class](OracleTypeMetaData.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
