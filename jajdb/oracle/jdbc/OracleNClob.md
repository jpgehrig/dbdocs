Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleNClob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDriver.md)
- [Next Class](OracleOCIFailover.md)

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

## Interface OracleNClob

- All Superinterfaces:
  [Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true), [NClob](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true), [OracleClob](OracleClob.md)

  <!-- -->

  All Known Implementing Classes:
  [NCLOB](../sql/NCLOB.md)

  ------------------------------------------------------------------------



      public interface OracleNClob
      extends NClob, OracleClob

  This interface extends the standard JDBC interface [`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true) and defines methods for Oracle specific NClob .
  Generally any new code should avoid the direct use of the class [`NCLOB`](../sql/NCLOB.md). For variable declarations use the interface [`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true) or this interface as required.

  Creating temporary NClob using factory method, [`Connection.createNClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createNClob__)

  Since:
  11.2.0.3.0

<!-- -->

- - ### Method Summary

    - ### Methods inherited from interface oracle.jdbc.[OracleClob](OracleClob.md)

      [`close`](OracleClob.md)`, `[`isEmptyLob`](OracleClob.md)`, `[`isOpen`](OracleClob.md)`, `[`isSecureFile`](OracleClob.md)`, `[`isTemporary`](OracleClob.md)`, `[`open`](OracleClob.md)`, `[`toSQLXML`](OracleClob.md)`, `[`toSQLXML`](OracleClob.md)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#free__)`, `[`getAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getAsciiStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream_long_long_)`, `[`getSubString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getSubString_long_int_)`, `[`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#length__)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_sql_Clob_long_)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_lang_String_long_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setAsciiStream_long_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setCharacterStream_long_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_int_int_)`, `[`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#truncate_long_)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleNClob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDriver.md)
- [Next Class](OracleOCIFailover.md)

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
