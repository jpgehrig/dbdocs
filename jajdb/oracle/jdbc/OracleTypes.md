Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypes.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Struct.md)
- [Next Class](OracleXAConnectionBuilder.md)

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

oracle.jdbc

## Class OracleTypes

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.OracleTypes

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class OracleTypes
      extends Object

  Oracle types.
  This interface defines constants that are used to identify SQL types. The actual type constant values are equivalent to those in XOPEN.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                 |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ARRAY`                                                                                                                                               |
    | `static int`      | `BFILE`                                                                                                                                               |
    | `static int`      | `BIGINT`                                                                                                                                              |
    | `static int`      | `BINARY`                                                                                                                                              |
    | `static int`      | `BINARY_DOUBLE`                                                                                                                                       |
    | `static int`      | `BINARY_FLOAT`                                                                                                                                        |
    | `static int`      | `BIT`                                                                                                                                                 |
    | `static int`      | `BLOB`                                                                                                                                                |
    | `static int`      | `BOOLEAN`<br>The constant in the Java programming language, somtimes referred to as a type code, that identifies the generic SQL type `BOOLEAN`.      |
    | `static int`      | `CHAR`                                                                                                                                                |
    | `static int`      | `CLOB`                                                                                                                                                |
    | `static int`      | `CURSOR`                                                                                                                                              |
    | `static int`      | `DATALINK`<br>The constant in the Java programming language, somtimes referred to as a type code, that identifies the generic SQL type `DATALINK`.    |
    | `static int`      | `DATE`                                                                                                                                                |
    | `static int`      | `DECIMAL`                                                                                                                                             |
    | `static int`      | `DOUBLE`                                                                                                                                              |
    | `static int`      | `FIXED_CHAR`<br>Use this type when binding to a CHAR column in the where clause of a Select statement.                                                |
    | `static int`      | `FLOAT`                                                                                                                                               |
    | `static int`      | `INTEGER`                                                                                                                                             |
    | `static int`      | `INTERVALDS`                                                                                                                                          |
    | `static int`      | `INTERVALYM`                                                                                                                                          |
    | `static int`      | `JAVA_OBJECT`                                                                                                                                         |
    | `static int`      | `JAVA_STRUCT`                                                                                                                                         |
    | `static int`      | `LONGNVARCHAR`                                                                                                                                        |
    | `static int`      | `LONGVARBINARY`                                                                                                                                       |
    | `static int`      | `LONGVARCHAR`                                                                                                                                         |
    | `static int`      | `NCHAR`                                                                                                                                               |
    | `static int`      | `NCLOB`                                                                                                                                               |
    | `static int`      | `NULL`                                                                                                                                                |
    | `static int`      | `NUMBER`<br>NUMBER shares same value as NUMERIC as it is synonym defined for convenience when using the oracle.sql.NUMBER type.                       |
    | `static int`      | `NUMERIC`                                                                                                                                             |
    | `static int`      | `NVARCHAR`                                                                                                                                            |
    | `static int`      | `OPAQUE`                                                                                                                                              |
    | `static int`      | `OTHER`<br>OTHER indicates that the SQL type is database specific and gets mapped to a Java object which can be accessed via getObject and setObject. |
    | `static int`      | `PLSQL_BOOLEAN`<br>PLSQL_BOOLEAN binds BOOLEAN type for input/output parameters when executing a PLSQL function/procedure.                            |
    | `static int`      | `PLSQL_INDEX_TABLE`                                                                                                                                   |
    | `static int`      | `RAW`<br>RAW shares same value as BINARY as it is synonym defined for convenience when using the oracle.sql.RAW type.                                 |
    | `static int`      | `REAL`                                                                                                                                                |
    | `static int`      | `REF`                                                                                                                                                 |
    | `static int`      | `REF_CURSOR`                                                                                                                                          |
    | `static int`      | `ROWID`                                                                                                                                               |
    | `static int`      | `SMALLINT`                                                                                                                                            |
    | `static int`      | `SQLXML`                                                                                                                                              |
    | `static int`      | `STRUCT`                                                                                                                                              |
    | `static int`      | `TIME`                                                                                                                                                |
    | `static int`      | `TIMESTAMP`                                                                                                                                           |
    | `static int`      | `TIMESTAMPLTZ`                                                                                                                                        |
    | `static int`      | `TIMESTAMPNS`<br>Deprecated. <br>since 9.2.0. Use OracleTypes.TIMESTAMP instead.                                                                      |
    | `static int`      | `TIMESTAMPTZ`                                                                                                                                         |
    | `static int`      | `TINYINT`                                                                                                                                             |
    | `static int`      | `VARBINARY`                                                                                                                                           |
    | `static int`      | `VARCHAR`                                                                                                                                             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OracleTypes``()`           |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### BIT

          public static final int BIT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TINYINT

          public static final int TINYINT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SMALLINT

          public static final int SMALLINT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INTEGER

          public static final int INTEGER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BIGINT

          public static final int BIGINT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FLOAT

          public static final int FLOAT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REAL

          public static final int REAL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOUBLE

          public static final int DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NUMERIC

          public static final int NUMERIC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DECIMAL

          public static final int DECIMAL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CHAR

          public static final int CHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### VARCHAR

          public static final int VARCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONGVARCHAR

          public static final int LONGVARCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATE

          public static final int DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIME

          public static final int TIME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMP

          public static final int TIMESTAMP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PLSQL_BOOLEAN

          public static final int PLSQL_BOOLEAN

      PLSQL_BOOLEAN binds BOOLEAN type for input/output parameters when executing a PLSQL function/procedure. Only available for thin driver.
      Since:
      12.2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMPNS

          public static final int TIMESTAMPNS

      Deprecated. since 9.2.0. Use OracleTypes.TIMESTAMP instead.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMPTZ

          public static final int TIMESTAMPTZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMPLTZ

          public static final int TIMESTAMPLTZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INTERVALYM

          public static final int INTERVALYM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INTERVALDS

          public static final int INTERVALDS

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY

          public static final int BINARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### VARBINARY

          public static final int VARBINARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONGVARBINARY

          public static final int LONGVARBINARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ROWID

          public static final int ROWID

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CURSOR

          public static final int CURSOR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLOB

          public static final int BLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CLOB

          public static final int CLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BFILE

          public static final int BFILE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STRUCT

          public static final int STRUCT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ARRAY

          public static final int ARRAY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REF

          public static final int REF

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NCHAR

          public static final int NCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NCLOB

          public static final int NCLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NVARCHAR

          public static final int NVARCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONGNVARCHAR

          public static final int LONGNVARCHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SQLXML

          public static final int SQLXML

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REF_CURSOR

          public static final int REF_CURSOR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPAQUE

          public static final int OPAQUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JAVA_STRUCT

          public static final int JAVA_STRUCT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### JAVA_OBJECT

          public static final int JAVA_OBJECT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PLSQL_INDEX_TABLE

          public static final int PLSQL_INDEX_TABLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY_FLOAT

          public static final int BINARY_FLOAT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY_DOUBLE

          public static final int BINARY_DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NULL

          public static final int NULL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NUMBER

          public static final int NUMBER

      NUMBER shares same value as NUMERIC as it is synonym defined for convenience when using the oracle.sql.NUMBER type. Internally, code need only worry about NUMERIC.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RAW

          public static final int RAW

      RAW shares same value as BINARY as it is synonym defined for convenience when using the oracle.sql.RAW type. Internally, code need only worry about BINARY.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OTHER

          public static final int OTHER

      OTHER indicates that the SQL type is database specific and gets mapped to a Java object which can be accessed via getObject and setObject.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FIXED_CHAR

          public static final int FIXED_CHAR

      Use this type when binding to a CHAR column in the where clause of a Select statement. A non padded comparision will be done unlike in CHAR and VARCHAR case. Not particularly needed for an insert as the database will pad it. This type is used for bind only. It cannot be used for define and registerOutParameter.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATALINK

          public static final int DATALINK

      The constant in the Java programming language, somtimes referred to as a type code, that identifies the generic SQL type `DATALINK`.
      Since:
      9.0.2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BOOLEAN

          public static final int BOOLEAN

      The constant in the Java programming language, somtimes referred to as a type code, that identifies the generic SQL type `BOOLEAN`.
      Since:
      9.0.2

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleTypes

          public OracleTypes()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypes.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Struct.md)
- [Next Class](OracleXAConnectionBuilder.md)

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
