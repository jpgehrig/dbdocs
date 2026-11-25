Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleSQLPermission.md)
- [Next Class](OracleStruct.md)

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

## Interface OracleStatement

- All Superinterfaces:
  [AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleCallableStatement](OracleCallableStatement.md), [OraclePreparedStatement](OraclePreparedStatement.md)

  ------------------------------------------------------------------------



      public interface OracleStatement
      extends Statement

  This interface defines the Oracle extensions to the standard JDBC interface `java.sql.Statement` and is the superinterface of the `OraclePreparedStatement` and `OracleCallableStatement` interfaces. You can use `java.sql.Statement` in your application where you do not make use of the Oracle extensions. However, when your application uses the Oracle extensions to `java.sql.Statement` you must cast your statement object to the type `oracle.jdbc.OracleStatement`. Although the type by which the java compiler will identify the statement object is changed, the object itself is unchanged.
  Extended functionality includes support for settings flags and options for Oracle performance extensions on a statement-by-statements basis, as opposed to the `OracleConnection` interface that sets these on a connection-wide basis.

  Since:
  8.1.7

  See Also:
  `Connection.createStatement`

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `EXPLICIT`            |
    | `static int`      | `IMPLICIT`            |
    | `static int`      | `NEW`                 |

    - ### Fields inherited from interface java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      [`CLOSE_ALL_RESULTS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_ALL_RESULTS)`, `[`CLOSE_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_CURRENT_RESULT)`, `[`EXECUTE_FAILED`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#EXECUTE_FAILED)`, `[`KEEP_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#KEEP_CURRENT_RESULT)`, `[`NO_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#NO_GENERATED_KEYS)`, `[`RETURN_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#RETURN_GENERATED_KEYS)`, `[`SUCCESS_NO_INFO`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#SUCCESS_NO_INFO)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Default Methods](javascript:show(16);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                         | Method and Description                                                                                                                                                                                                                                                                        |
    |-----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                    | `clearDefines``()`<br>Lets you clear previously defined types for the define-columns of this statement.                                                                                                                                                                                       |
    | `void`                                                                                                    | `closeOnCompletion``()`<br>Specifies that this Statement will be closed when all its dependent result sets are closed.                                                                                                                                                                        |
    | `void`                                                                                                    | `closeWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>The underlying cursor is not closed and the Statement handle is cached on the Key.                                                                                 |
    | `int`                                                                                                     | `creationState``()`<br>Deprecated.                                                                                                                                                                                                                                                            |
    | `void`                                                                                                    | `defineColumnType``(int columnIndex, int type)`<br>Defines the type you will use to retrieve data from a particular database table column.                                                                                                                                                    |
    | `void`                                                                                                    | `defineColumnType``(int columnIndex, int type, int lobPrefetchSize)`<br>Defines the type you will use to retrieve data from a particular database table column.                                                                                                                               |
    | `void`                                                                                                    | `defineColumnType``(int columnIndex, int type, int lobPrefetchSize, short formOfUse)`<br>Deprecated.                                                                                                                                                                                          |
    | `void`                                                                                                    | `defineColumnType``(int columnIndex, int typeCode, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Defines the type you will use to retrieve data from a particular database table column and specifies the column type name. |
    | `void`                                                                                                    | `defineColumnTypeBytes``(int columnIndex, int type, int lobPrefetchSize)`<br>Deprecated.                                                                                                                                                                                                      |
    | `void`                                                                                                    | `defineColumnTypeChars``(int columnIndex, int type, int lobPrefetchSize)`<br>Deprecated.                                                                                                                                                                                                      |
    | `default `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `enquoteIdentifier``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` identifier, boolean alwaysQuote)`<br>Returns a SQL identifier.                                                                                                         |
    | `default `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `enquoteLiteral``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` val)`<br>Returns a `String` enclosed in single quotes.                                                                                                                    |
    | `default `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `enquoteNCharLiteral``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` val)`<br>Returns a `String` enclosed in single quotes and prefixed with 'N'.                                                                                         |
    | `int`                                                                                                     | `getLobPrefetchSize``()`<br>Returns the LOB prefetch size.                                                                                                                                                                                                                                    |
    | `long`                                                                                                    | `getRegisteredQueryId``()`<br>Returns the id of the query that has been added in the registration (only for query change notification).                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`       | `getRegisteredTableNames``()`<br>Returns the name of the tables that have been added to the registration if any.                                                                                                                                                                              |
    | `int`                                                                                                     | `getRowPrefetch``()`<br>Retrieves the value or row prefetch for all result sets created from this statement.                                                                                                                                                                                  |
    | `boolean`                                                                                                 | `isNCHAR``(int index)`<br>isNCHAR (int)                                                                                                                                                                                                                                                       |
    | `default boolean`                                                                                         | `isSimpleIdentifier``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` identifier)`<br>Retrieves whether `identifier` is a simple SQL identifier.                                                                                            |
    | `void`                                                                                                    | `setDatabaseChangeRegistration``(`[`DatabaseChangeRegistration`](dcn/DatabaseChangeRegistration.md)` registration)`<br>Associate a Database Change Registration object with this statement.                                                                                                   |
    | `void`                                                                                                    | `setLobPrefetchSize``(int value)`<br>Overrides the LOB prefetch size for this statement.                                                                                                                                                                                                      |
    | `void`                                                                                                    | `setRowPrefetch``(int value)`<br>Sets the value of row prefetch for all result sets created from this statement.                                                                                                                                                                              |

    - ### Methods inherited from interface java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      [`addBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#addBatch_java_lang_String_)`, `[`cancel`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#cancel__)`, `[`clearBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#clearBatch__)`, `[`clearWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#clearWarnings__)`, `[`close`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#close__)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_int_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_int_A_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_java_lang_String_A_)`, `[`executeBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeBatch__)`, `[`executeLargeBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeBatch__)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_int_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_int_A_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_java_lang_String_A_)`, `[`executeQuery`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeQuery_java_lang_String_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_int_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_int_A_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_java_lang_String_A_)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getConnection__)`, `[`getFetchDirection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getFetchDirection__)`, `[`getFetchSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getFetchSize__)`, `[`getGeneratedKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getGeneratedKeys__)`, `[`getLargeMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getLargeMaxRows__)`, `[`getLargeUpdateCount`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getLargeUpdateCount__)`, `[`getMaxFieldSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMaxFieldSize__)`, `[`getMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMaxRows__)`, `[`getMoreResults`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMoreResults__)`, `[`getMoreResults`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMoreResults_int_)`, `[`getQueryTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getQueryTimeout__)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSet__)`, `[`getResultSetConcurrency`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetConcurrency__)`, `[`getResultSetHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetHoldability__)`, `[`getResultSetType`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetType__)`, `[`getUpdateCount`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getUpdateCount__)`, `[`getWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getWarnings__)`, `[`isClosed`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isClosed__)`, `[`isCloseOnCompletion`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isCloseOnCompletion__)`, `[`isPoolable`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isPoolable__)`, `[`setCursorName`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setCursorName_java_lang_String_)`, `[`setEscapeProcessing`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setEscapeProcessing_boolean_)`, `[`setFetchDirection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setFetchDirection_int_)`, `[`setFetchSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setFetchSize_int_)`, `[`setLargeMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setLargeMaxRows_long_)`, `[`setMaxFieldSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setMaxFieldSize_int_)`, `[`setMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setMaxRows_int_)`, `[`setPoolable`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setPoolable_boolean_)`, `[`setQueryTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setQueryTimeout_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Field Detail

    - #### NEW

          static final int NEW

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### IMPLICIT

          static final int IMPLICIT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EXPLICIT

          static final int EXPLICIT

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### clearDefines

          void clearDefines()
                     throws SQLException

      Lets you clear previously defined types for the define-columns of this statement. This is usefull if you want to reuse this statement for a different query.
      After calling `clearDefines`, you can either perform defines by calling `defineColumnType/defineColumnTypeChars` or let the driver use the default defines for the table.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

    <!-- -->

    - #### defineColumnType

          void defineColumnType(int columnIndex,
                                int type)
                         throws SQLException

      Defines the type you will use to retrieve data from a particular database table column.

      For the JDBC-OCI driver and the server-side internal driver, if you decide to use defineColumnType you must declare the types of exactly all columns in the query. For the thin driver, it is not required to define all the columns.

      See the JDBC Manual section on Data Interface for LOBs for a description of using defineColumnType to get LOB columns as streams. In some cases this is a large performance gain. The lob prefetch feature makes this less important, however. It is effective for basic lobs, but less so for SecureFile lobs.

      BFILE, BLOB, CLOB, or NCLOB data can be read using the same streaming mechanism as for LONG RAW and LONG data. Use defineColumnType(nn, Types.LONGVARBINARY) for BLOB or BFILE, defineColumnType(nn,Types.LONGVARCHAR) for CLOB, or defineColumnType(nn,Types.LONGNVARCHAR) for NCLOB. This produces a stream on the data as if it were a LONG RAW or LONG column. Use defineColumnType( nn, Types.VARBINARY) or defineColumnType(nn, Types.VARCHAR) returns the data as if it were a RAW or VARCHAR2 column with the size limits of those types.

      The following example illustrates the use of this feature in the PM sample schema:

              // Ask for the column as a character stream:
              ((OracleStatement)stmt).defineColumnType(1, Types.LONGVARCHAR);

              ResultSet rset = stmt.executeQuery("select PRODUCT_TEXT from ONLINE_MEDIA");
              while (rset.next() )
              System.out.println(rset.getString(1));


      All columns can be defined to their "natural" JDBC types; in most cases, they can be defined to the `Types.CHAR` or `Types.VARCHAR` typecode. You can also use the `OracleTypes` typecodes. The type can also be different from the native type of the column. Appropriate conversions will be done. A subsequent call to `getObject()` for this column will return the supplied type rather than the native type.

      Parameters:
      `columnIndex` - index of column (first is 1)

      `type` - type to be assigned to column

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `defineColumnType(int,int,int)`, `clearDefines`

    <!-- -->

    - #### defineColumnType

          void defineColumnType(int columnIndex,
                                int type,
                                int lobPrefetchSize)
                         throws SQLException

      Defines the type you will use to retrieve data from a particular database table column. See defineColumnType( int, int) for general information.

      In previous releases the third parameter was used to control the buffer sizes used with possible truncation of data. In the current release it is used only to control the LOB prefetch size at the column level. This setting overrides the default LOB prefetch size that is defined at the connection or statement level. The `lobPrefetchSize` argument represents in this case the number of bytes to prefetch for a BLOB and chars for a CLOB and the value must be \>= 0 and the type must be set to OracleTypes.CLOB for a CLOB column and OracleTypes.BLOB for a BLOB column.

      Parameters:
      `columnIndex` - index of column (first is 1)

      `type` - type to be assigned to column

      `lobPrefetchSize` - for lob column, size of prefetch buffer

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `#java.sql.Statement.setMaxFieldSize`

    <!-- -->

    - #### defineColumnType

          void defineColumnType(int columnIndex,
                                int type,
                                int lobPrefetchSize,
                                short formOfUse)
                         throws SQLException

      Deprecated. 
      Deprecated method, please use defineColumnType(int, int, int) with the type such as Types.NCHAR, Types.NVARCHAR, Types.NCLOB.

      See defineColumnType( int, int) for general information.

      The formOfUse parameter may take the value oracle.jdbc.OraclePreparedStatement.FORM_CHAR to specify that the data be in the database character set or oracle.jdbc.OraclePreparedStatement.FORM_NCHAR to specify that the data be in the national character set.

      Parameters:
      `columnIndex` - index of column (first is 1)

      `type` - type to be assigned to column

      `lobPrefetchSize` - for lob column, size of prefetch buffer

      `formOfUse` - flag to select character set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      10iR1

    <!-- -->

    - #### defineColumnTypeBytes

          void defineColumnTypeBytes(int columnIndex,
                                     int type,
                                     int lobPrefetchSize)
                              throws SQLException

      Deprecated. 
      Deprecated method, please use defineColumnType(int, int, int) which is used internally by this method.
      Parameters:
      `columnIndex` - index of column (first is 1)

      `type` - type to be assigned to column

      `lobPrefetchSize` - ignored except for lob columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `defineColumnType(int,int,int)`, `clearDefines`

    <!-- -->

    - #### defineColumnTypeChars

          void defineColumnTypeChars(int columnIndex,
                                     int type,
                                     int lobPrefetchSize)
                              throws SQLException

      Deprecated. 
      Deprecated method, please use defineColumnType(int, int, int) which is used internally by this method.
      Parameters:
      `columnIndex` - index of column (first is 1)

      `type` - type to be assigned to column

      `lobPrefetchSize` - ignored except for lob columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `defineColumnType(int,int,int)`, `clearDefines`

    <!-- -->

    - #### defineColumnType

          void defineColumnType(int columnIndex,
                                int typeCode,
                                String typeName)
                         throws SQLException

      Defines the type you will use to retrieve data from a particular database table column and specifies the column type name. This method should be used for structured object, object reference and array columns. See defineColumnType( int, int) for general information.

      Parameters:
      `columnIndex` - index of column (first is 1)

      `typeCode` - type code for this column.

      `typeName` - specifies the fully-qualified name of the type of the column

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `defineColumnType(int,int)`, `clearDefines`

    <!-- -->

    - #### getRowPrefetch

          int getRowPrefetch()

      Retrieves the value or row prefetch for all result sets created from this statement.
      The row-prefetching feature associates an integer row-prefetch setting with a given statement object. JDBC fetches that number of rows at a time from the database during the query. That is, JDBC will fetch N rows that match the query criteria and bring them all back to the client at once, where N is the prefetch setting. Then, once your `next` calls have run through those N rows, JDBC will go back to fetch the next N rows that match the criteria.

      You can set the number of rows to prefetch for this particular Oracle statement (any type of statement). You can also reset the default number of rows that will be prefetched for all statements in your connection with the `OracleConnection.setDefaultRowPrefetch` method.

      Returns:
      the row prefetch value

      See Also:
      `setRowPrefetch`, [`OracleConnection.setDefaultRowPrefetch`](OracleConnection.md)

    <!-- -->

    - #### setRowPrefetch

          void setRowPrefetch(int value)
                       throws SQLException

      Sets the value of row prefetch for all result sets created from this statement. It overrides the prefetch value set from the connection, for this particular statement.
      The row-prefetching feature associates an integer row-prefetch setting with a given statement object. JDBC fetches that number of rows at a time from the database during the query. That is, JDBC will fetch N rows that match the query criteria and bring them all back to the client at once, where N is the prefetch setting. Then, once your `next` calls have run through those N rows, JDBC will go back to fetch the next N rows that match the criteria.

      The row_prefetch will be turned back to 1 automatically by the driver if any of the select-column types is streaming (long data or long raw data). This is overrides any value the user might set. Also, this will be done regardless of wether the streaming columns are read or not.

      Notes :

      - If a column of a result set is of datatype LONG or LONG RAW (that is, the streaming types), JDBC changes the statement's row-prefetch setting to 1, even if you never actually read a value of either of those types.
      - Do not mix the JDBC 2.0 fetch size API and the Oracle row-prefetching API in your application. You can use one or the other, but not both.

      Parameters:
      `value` - the number of rows to prefetch

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the argument `value` is \<=0

      See Also:
      `getRowPrefetch`, [`OracleConnection.setDefaultRowPrefetch`](OracleConnection.md)

    <!-- -->

    - #### getLobPrefetchSize

          int getLobPrefetchSize()
                          throws SQLException

      Returns the LOB prefetch size. This value can be set at the connection level with the `oracle.jdbc.defaultLobPrefetchSize` connection property or at the statement level through the `setLobPrefetchSize(int)` method.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.2

      See Also:
      `setLobPrefetchSize`

    <!-- -->

    - #### setLobPrefetchSize

          void setLobPrefetchSize(int value)
                           throws SQLException

      Overrides the LOB prefetch size for this statement. With LOB prefetch, meta-data such as the lob length and the chunk size as well as the beginning of the LOB data are sent along with the locator during the regular fetch operation. This has a significant performance impact especially for small LOBs which can potentially be entirely prefetched. The data is then available to the user without having to go through the LOB protocol. Note that this is available only with the Oracle database starting in 11.1.
      LOB prefetch is enabled by default (see the `oracle.jdbc.defaultLobPrefetchSize` connection property which default value is 4k bytes for BLOBs and 4k chars for CLOBs). The LOB prefetch size can be set at the connection level through the property or at the statement level through this method. The statement level setting overrides the setting at the connection level. This setting can also be overriden at the column level through the `defineColumnType` method where the size represents the number of bytes (or chars for CLOB) to prefetch.

      Parameters:
      `value` - must be \>= -1. -1 disables the feature. 0 enables LOB prefetch of meta data only (lob length and chunk size). Any value \>=0 represents the number of bytes to be prefetched for BLOB and the number of chars for CLOB.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if `value < -1`

      Since:
      11.2

      See Also:
      `getLobPrefetchSize`, `OracleConnection.DEFAULT_LOB_PREFETCH_SIZE`

    <!-- -->

    - #### closeWithKey

          void closeWithKey(String key)
                     throws SQLException

      The underlying cursor is not closed and the Statement handle is cached on the Key. The Statement is cached as it is and the state, data, and meta-data is not cleared. The same statement can be retrieved with this Key later. Key cannot be null.
      Parameters:
      `key` - A key to tag to the statement to be retrieved later

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### creationState

          int creationState()

      Deprecated. 
      Returns:
      Creation Status flag

    <!-- -->

    - #### isNCHAR

          boolean isNCHAR(int index)
                   throws SQLException

      isNCHAR (int)
      Parameters:
      `index` - the column index

      Returns:
      true if the column is of type NCHAR/NVARCHAR/NCLOB false if the column is not of type NCHAR/NVARCHAR/NCLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setDatabaseChangeRegistration

          void setDatabaseChangeRegistration(DatabaseChangeRegistration registration)
                                      throws SQLException

      Associate a Database Change Registration object with this statement.
      Any subsequent queries executed with this statement will be part of the given registration.

      If you want this statement to no longer add queries to the registration, call this method again with a 'null' argument. Subsequent queries won't be part of the registration.

      Parameters:
      `registration` - can be either a valid registration or 'null'.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

      See Also:
      `getRegisteredQueryId()`

    <!-- -->

    - #### getRegisteredTableNames

          String[] getRegisteredTableNames()
                                    throws SQLException

      Returns the name of the tables that have been added to the registration if any.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### getRegisteredQueryId

          long getRegisteredQueryId()
                             throws SQLException

      Returns the id of the query that has been added in the registration (only for query change notification).
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

      See Also:
      `setDatabaseChangeRegistration(oracle.jdbc.dcn.DatabaseChangeRegistration)`

    <!-- -->

    - #### closeOnCompletion

          void closeOnCompletion()
                          throws SQLException

      Specifies that this Statement will be closed when all its dependent result sets are closed. If execution of the Statement does not produce any result sets, this method has no effect.
      Specified by:
      [`closeOnCompletion`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#closeOnCompletion__) in interface [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if this method is called on a closed Statement

      Since:
      1.7

    <!-- -->

    - #### enquoteLiteral

          default String enquoteLiteral(String val)
                                 throws SQLException

      Returns a `String` enclosed in single quotes. Any occurrence of a single quote within the string will be replaced by two single quotes.
      > **Examples of the conversion:**
      >
      > |  Value   |     Result     |
      > |:--------:|:--------------:|
      > |  Hello   |    'Hello'     |
      > |  G'Day   |    'G''Day'    |
      > | 'G''Day' | '''G''''Day''' |
      > |  I'''M   |   'I''''''M'   |

      Parameters:
      `val` - a character string

      Returns:
      A string enclosed by single quotes with every single quote converted to two single quotes

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if val is null

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if val cannot be transformed into a SQL literal

    <!-- -->

    - #### enquoteNCharLiteral

          default String enquoteNCharLiteral(String val)
                                      throws SQLException

      Returns a `String` enclosed in single quotes and prefixed with 'N'. Any occurrence of a single quote within the string will be replaced by two single quotes.
      > **Examples of the conversion:**
      >
      > |   Value   |     Result      |
      > |:---------:|:---------------:|
      > |   Hello   |    N'Hello'     |
      > |   G'Day   |    N'G''Day'    |
      > | N'G''Day' | N'''G''''Day''' |
      > |   I'''M   |   N'I''''''M'   |

      Parameters:
      `val` - a character string

      Returns:
      A string enclosed by single quotes with every single quote converted to two single quotes

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if val is null

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if val cannot be transformed into a SQL literal

    <!-- -->

    - #### isSimpleIdentifier

          default boolean isSimpleIdentifier(String identifier)
                                      throws SQLException

      Retrieves whether `identifier` is a simple SQL identifier.
      Parameters:
      `identifier` - a SQL identifier

      Returns:
      A simple SQL identifier or a delimited identifier

      Throws:
      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if identifier is null

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the driver cannot verify that identifier is a valid simple identifier or not

    <!-- -->

    - #### enquoteIdentifier

          default String enquoteIdentifier(String identifier,
                                           boolean alwaysQuote)
                                    throws SQLException

      Returns a SQL identifier. If `identifier` is a simple SQL identifier:
      - Return the original value if `alwaysQuote` is `false`
      - Return a delimited identifier if `alwaysQuote` is `true`

      If `identifier` is not a simple SQL identifier, `identifier` will be enclosed in double quotes if not already present. If the datasource does not support double quotes for delimited identifiers, the identifier should be enclosed by the string returned from `DatabaseMetaData#getIdentifierQuoteString`. If the datasource does not support delimited identifiers, a `SQLFeatureNotSupportedException` should be thrown.
      A `SQLException` will be thrown if `identifier` contains any characters invalid in a delimited identifier or the identifier length is invalid for the datasource.

      Parameters:
      `identifier` - a SQL identifier

      `alwaysQuote` - indicates if a simple SQL identifier should be returned as a quoted identifier

      Returns:
      A simple SQL identifier or a delimited identifier

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if identifier is not a valid identifier

      `SQLFeatureNotSupportedException` - if the datasource does not support delimited identifiers

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if identifier is null

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleSQLPermission.md)
- [Next Class](OracleStruct.md)

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
