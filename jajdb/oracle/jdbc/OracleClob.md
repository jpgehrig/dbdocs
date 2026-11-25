Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleClob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleCallableStatement.md)
- [Next Class](OracleConnection.md)

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

## Interface OracleClob

- All Superinterfaces:
  [Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleNClob](OracleNClob.md)

  <!-- -->

  All Known Implementing Classes:
  [CLOB](../sql/CLOB.md), [NCLOB](../sql/NCLOB.md)

  ------------------------------------------------------------------------



      public interface OracleClob
      extends Clob

  This interface extends the standard JDBC interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true) and defines methods for Oracle specific Clob .
  Generally any new code should avoid the direct use of the class [`CLOB`](../sql/CLOB.md). For variable declarations use the interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true) or this interface as required. Instead of the static methods [`CLOB.createTemporary(java.sql.Connection, boolean, int)`](../sql/CLOB.md) and [`CLOB.empty_lob()`](../sql/CLOB.md) please use [`Connection.createClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createClob__) and [`CLOB.getEmptyCLOB()`](../sql/CLOB.md) respectively.

  Since:
  11.2.0.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                              | Method and Description                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                         | `close``()`<br>Close a previously opened CLOB.                                                                                                                                                                    |
    | `boolean`                                                                                      | `isEmptyLob``()`<br>Return true if this is a empty lob.                                                                                                                                                           |
    | `boolean`                                                                                      | `isOpen``()`<br>Check whether the CLOB is opened.                                                                                                                                                                 |
    | `boolean`                                                                                      | `isSecureFile``()`<br>Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).                                                  |
    | `boolean`                                                                                      | `isTemporary``()`<br>Return true if the lob locator points to a temporary clob.                                                                                                                                   |
    | `void`                                                                                         | `open``(`[`LargeObjectAccessMode`](LargeObjectAccessMode.md)` mode)`<br>Open a CLOB in the indicated mode.                                                                                                        |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true) | `toSQLXML``()`<br>Returns an object which impements java.sql.SQLXML with content take from this Clob.                                                                                                             |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true) | `toSQLXML``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaURL)`<br>Returns an object which impements java.sql.SQLXML with content taken from this Clob. |

    - ### Methods inherited from interface java.sql.[Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#free__)`, `[`getAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getAsciiStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream_long_long_)`, `[`getSubString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getSubString_long_int_)`, `[`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#length__)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_sql_Clob_long_)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_lang_String_long_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setAsciiStream_long_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setCharacterStream_long_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_int_int_)`, `[`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#truncate_long_)

<!-- -->

- - ### Method Detail

    - #### open

          void open(LargeObjectAccessMode mode)
             throws SQLException

      Open a CLOB in the indicated mode. Valid modes include MODE_READONLY, and MODE_READWRITE. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### close

          void close()
              throws SQLException

      Close a previously opened CLOB.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          boolean isOpen()
                  throws SQLException

      Check whether the CLOB is opened.
      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isTemporary

          boolean isTemporary()
                       throws SQLException

      Return true if the lob locator points to a temporary clob. False if it does not.
      Returns:
      true if the lob locator points to a temporary clob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isEmptyLob

          boolean isEmptyLob()
                      throws SQLException

      Return true if this is a empty lob.
      Returns:
      true if this is a empty lob.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `empty_lob`

    <!-- -->

    - #### isSecureFile

          boolean isSecureFile()
                        throws SQLException

      Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).
      Returns:
      `true` if this is a SecureFile and `false` otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### toSQLXML

          SQLXML toSQLXML()
                   throws SQLException

      Returns an object which impements java.sql.SQLXML with content take from this Clob.
      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

    <!-- -->

    - #### toSQLXML

          SQLXML toSQLXML(String schemaURL)
                   throws SQLException

      Returns an object which impements java.sql.SQLXML with content taken from this Clob.
      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleClob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleCallableStatement.md)
- [Next Class](OracleConnection.md)

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
