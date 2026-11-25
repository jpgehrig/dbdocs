Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTranslatingConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTemporalField.md)
- [Next Class](OracleTranslatingConnection.SqlTranslationVersion.md)

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

## Interface OracleTranslatingConnection

- All Known Implementing Classes:
  [BabelfishConnection](babelfish/BabelfishConnection.md)

  ------------------------------------------------------------------------



      public interface OracleTranslatingConnection

  Declares convenience methods to get non translating Statements, PreparedStatements or CallableStatements from a SQL Translation enabled connection. All the methods defined here are counterparts to similar methods defined in java.sql.Connection, with an additional boolean flag. If the flag translation is true then the resulting Statement will have SQL Translation enabled just like you would get from a Translation enabled Connection. Else if the flag is false then the resulting Statment will not have translation enabled. Only a translation enabled connection can be handled with a reference to this interface.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                                                                              |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`OracleTranslatingConnection.SqlTranslationVersion`](OracleTranslatingConnection.SqlTranslationVersion.md)<br>Enumeration of various Translation versions of a query. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                                                                                                                                                                                            | Method and Description                                                                                                                                                                                                                                             |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                         | `createStatement``(boolean translation)`                                                                                                                                                                                                                           |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                         | `createStatement``(int resultSetType, int resultSetConcurrency, boolean translation)`                                                                                                                                                                              |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                         | `createStatement``(int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`                                                                                                                                                    |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | `getSqlTranslationVersions``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation.             |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                         | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean translation)`                                                                                                                        |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                         | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, boolean translation)`                                                                           |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                         | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`                                                 |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean translation)`                                                                                                                   |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int[] columnIndexes, boolean translation)`                                                                                              |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int autoGeneratedKeys, boolean translation)`                                                                                            |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, boolean translation)`                                                                      |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`                                            |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                         | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] columnNames, boolean translation)`  |

<!-- -->

- - ### Method Detail

    - #### createStatement

          Statement createStatement(boolean translation)
                             throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createStatement

          Statement createStatement(int resultSetType,
                                    int resultSetConcurrency,
                                    boolean translation)
                             throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createStatement

          Statement createStatement(int resultSetType,
                                    int resultSetConcurrency,
                                    int resultSetHoldability,
                                    boolean translation)
                             throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             int autoGeneratedKeys,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             int[] columnIndexes,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             String[] columnNames,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             int resultSetType,
                                             int resultSetConcurrency,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          PreparedStatement prepareStatement(String sql,
                                             int resultSetType,
                                             int resultSetConcurrency,
                                             int resultSetHoldability,
                                             boolean translation)
                                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          CallableStatement prepareCall(String sql,
                                        boolean translation)
                                 throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          CallableStatement prepareCall(String sql,
                                        int resultSetType,
                                        int resultSetConcurrency,
                                        boolean translation)
                                 throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          CallableStatement prepareCall(String sql,
                                        int resultSetType,
                                        int resultSetConcurrency,
                                        int resultSetHoldability,
                                        boolean translation)
                                 throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSqlTranslationVersions

          Map<OracleTranslatingConnection.SqlTranslationVersion,String> getSqlTranslationVersions(String sql,
                                                                                                  boolean suppressExceptions)
                                                                                           throws SQLException

      Returns a map of all the translation versions of the query during SQL Translation. See SqlTranslationVersion enum for more details about returning versions.
      Parameters:
      `sql` - vendor specific sql to be translated

      `suppressExceptions` - suppresses any exception raised during query translation and returns whatever is available. Useful to get JDBC_MARKER_CONVERTED version when the translation is throwing error.

      Returns:
      Map with all the translation versions of a query. In case of an Exception and if suppressExceptions is true then the TRANSLATED version in the map is null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there is a problem in query translation provided suppressExceptions is false.

      See Also:
      [`OracleTranslatingConnection.SqlTranslationVersion`](OracleTranslatingConnection.SqlTranslationVersion.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTranslatingConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTemporalField.md)
- [Next Class](OracleTranslatingConnection.SqlTranslationVersion.md)

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
