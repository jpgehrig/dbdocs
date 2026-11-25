Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishCallableStatement.md)
- [Next Class](BabelfishGenericProxy.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.jdbc.babelfish

## Class BabelfishConnection

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.babelfish.BabelfishGenericProxy](BabelfishGenericProxy.md)

  - - oracle.jdbc.babelfish.BabelfishConnection

<!-- -->

- All Implemented Interfaces:
  [OracleTranslatingConnection](../OracleTranslatingConnection.md)

  ------------------------------------------------------------------------



      public abstract class BabelfishConnection
      extends BabelfishGenericProxy
      implements OracleTranslatingConnection

  Proxy Superclass for java.sql.Connection interface. It is used by the Oracle JDBC proxy library to proxify java.sql.Connection objects to support the auto translation features.

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTranslatingConnection](../OracleTranslatingConnection.md)

      [`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `BabelfishConnection``()`   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                                                                                                                                                                                                                          | `close``()`<br>Releases this `Connection` object's database and JDBC resources immediately instead of waiting for them to be automatically released.                                                                                                                                                                                                                               |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``()`<br>Creates a `Statement` with translation features enabled                                                                                                                                                                                                                                                                                                   |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``(boolean translation)`<br>Similar to createStatement() but with an additional translation flag.                                                                                                                                                                                                                                                                  |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``(int resultSetType, int resultSetConcurrency)`<br>Returns a `Statement` with translation features enabled                                                                                                                                                                                                                                                        |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``(int resultSetType, int resultSetConcurrency, boolean translation)`<br>Similar to createStatement(int resultSetType, int resultSetConcurrency) but with an additional translation flag.                                                                                                                                                                          |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``(int resultSetType, int resultSetConcurrency, int resultSetHoldability)`<br>Returns a `Statement` with translation features enabled                                                                                                                                                                                                                              |
    | [`Statement`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)                                                                                                                                                                                                            | `createStatement``(int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`<br>Similar to createStatement(int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag.                                                                                                                      |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                                                                                                                                                                                            | `getCreator``()`                                                                                                                                                                                                                                                                                                                                                                   |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                                                                                                                                                                                            | `getDelegate``()`                                                                                                                                                                                                                                                                                                                                                                  |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | `getSqlTranslationVersions``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation.                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                                                                                                                                                                                                                 | `nativeSQL``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql)`<br>Converts the given foreign dialect SQL statement into the system's native SQL grammar.                                                                                                                                                                     |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                                                                                                                                                                                                     | `post_Methods``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` result)`<br>Post interceptor.                                                                                                                       |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql)`<br>Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String)                                                                                                                                                                  |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean translation)`<br>Similar to prepareCall(String sql) but with an additional translation flag.                                                                                                                                                         |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency)`<br>Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String, int, int)                                                                                                           |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, boolean translation)`<br>Similar to prepareCall(String sql, int resultSetType, int resultSetConcurrency) but with an additional translation flag.                                                               |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability)`<br>Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String, int, int, int)                                                                            |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)                                                                                                                                                                                            | `prepareCall``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`<br>Similar to prepareCall(String sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag.           |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String)                                                                                                                                                        |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean translation)`<br>Similar to prepareStatement(String sql) but with an additional translation flag.                                                                                                                                               |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int autoGeneratedKeys)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int)                                                                                                                            |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int[] columnIndexes)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int\[\])                                                                                                                          |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int[] columnIndexes, boolean translation)`<br>Similar to prepareStatement(String sql, int\[\] columnIndexes) but with an additional translation flag.                                                                                                   |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int autoGeneratedKeys, boolean translation)`<br>Similar to prepareStatement(String sql, int autoGeneratedKeys) but with an additional translation flag.                                                                                                 |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int, int)                                                                                                 |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, boolean translation)`<br>Similar to prepareStatement(String sql, int resultSetType, int resultSetConcurrency) but with an additional translation flag.                                                     |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int, int, int)                                                                  |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability, boolean translation)`<br>Similar to prepareStatement(String sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag. |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] columnNames)`<br>Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, java.lang.String\[\])                 |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)                                                                                                                                                                                            | `prepareStatement``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] columnNames, boolean translation)`<br>Similar to prepareStatement(String sql, String\[\] columnNames) but with an additional translation flag.      |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                                                                                                                                                                                            | `proxify``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` d, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` creator)`                                                                                                                                                        |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                                                                                                                                                                                                     | `translateError``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` ex)`<br>Interceptor for translation of errors.                                                                                         |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### BabelfishConnection

          public BabelfishConnection()

  <!-- -->

  - ### Method Detail

    - #### getCreator

          protected abstract Object getCreator()

      Specified by:

      [`getCreator`](BabelfishGenericProxy.md) in class [`BabelfishGenericProxy`](BabelfishGenericProxy.md)

      Returns:

    <!-- -->

    - #### getDelegate

          protected abstract Object getDelegate()

      Specified by:

      [`getDelegate`](BabelfishGenericProxy.md) in class [`BabelfishGenericProxy`](BabelfishGenericProxy.md)

      Returns:

    <!-- -->

    - #### proxify

          protected abstract Object proxify(Object d,
                                            Object creator)

    <!-- -->

    - #### translateError

          protected Object translateError(Method m,
                                          SQLException ex)
                                   throws SQLException

      Interceptor for translation of errors.
      Overrides:
      [`translateError`](BabelfishGenericProxy.md) in class [`BabelfishGenericProxy`](BabelfishGenericProxy.md)

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### post_Methods

          protected Object post_Methods(Method m,
                                        Object result)

      Post interceptor. sets up the translator in relevant objects required for handling error translation in those objects.
      Overrides:

      [`post_Methods`](BabelfishGenericProxy.md) in class [`BabelfishGenericProxy`](BabelfishGenericProxy.md)

      Returns:

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int autoGeneratedKeys)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int[] columnIndexes)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int\[\])
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String, int[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_A_)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    String[] columnNames)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, java.lang.String\[\])
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String, java.lang.String[])`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_java_lang_String_A_)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int resultSetType,
                                                    int resultSetConcurrency)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int, int)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_int_)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int resultSetType,
                                                    int resultSetConcurrency,
                                                    int resultSetHoldability)
                                             throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareStatement(java.lang.String, int, int, int)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareStatement(java.lang.String, int, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_int_int_)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql)
                                        throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareCall(java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql,
                                               int resultSetType,
                                               int resultSetConcurrency)
                                        throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String, int, int)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareCall(java.lang.String, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_int_int_)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql,
                                               int resultSetType,
                                               int resultSetConcurrency,
                                               int resultSetHoldability)
                                        throws SQLException

      Translation enabled implementation of java.sql.Connection#prepareCall(java.lang.String, int, int, int)
      Parameters:
      `sql` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.prepareCall(java.lang.String, int, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_int_int_int_)

    <!-- -->

    - #### nativeSQL

          public String nativeSQL(String sql)
                           throws SQLException

      Converts the given foreign dialect SQL statement into the system's native SQL grammar. A driver may convert the JDBC SQL grammar into its system's native SQL grammar prior to sending it. This method returns the native form of the statement that the driver would have sent.
      Parameters:
      `sql` - a foreign dialect SQL statement that may contain one or more '?' parameter placeholders

      Returns:
      the native form of this statement

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs or this method is called on a closed connection

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Releases this `Connection` object's database and JDBC resources immediately instead of waiting for them to be automatically released.
      Calling the method `close` on a `Connection` object that is already closed is a no-op.

      It is **strongly recommended** that an application explicitly commits or rolls back an active transaction prior to calling the `close` method. If the `close` method is called and there is an active transaction, the results are implementation-defined.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - SQLException if a database access error occurs

    <!-- -->

    - #### createStatement

          public Statement createStatement()
                                    throws SQLException

      Creates a `Statement` with translation features enabled
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.createStatement()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement__)

    <!-- -->

    - #### createStatement

          public Statement createStatement(boolean translation)
                                    throws SQLException

      Similar to createStatement() but with an additional translation flag. If the translation flag is true then the returning `Statement` will have translation enabled. If the flag is false then the returning `Statement` will be a normal `Statement` with no translation features.
      Specified by:
      [`createStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createStatement

          public Statement createStatement(int resultSetType,
                                           int resultSetConcurrency)
                                    throws SQLException

      Returns a `Statement` with translation features enabled
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.createStatement(int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement_int_int_)

    <!-- -->

    - #### createStatement

          public Statement createStatement(int resultSetType,
                                           int resultSetConcurrency,
                                           boolean translation)
                                    throws SQLException

      Similar to createStatement(int resultSetType, int resultSetConcurrency) but with an additional translation flag. If the translation flag is true then the returning `Statement` will have translation enabled. If the flag is false then the returning `Statement` will be a normal `Statement` with no translation features.
      Specified by:
      [`createStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### createStatement

          public Statement createStatement(int resultSetType,
                                           int resultSetConcurrency,
                                           int resultSetHoldability)
                                    throws SQLException

      Returns a `Statement` with translation features enabled
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection.createStatement(int, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement_int_int_int_)

    <!-- -->

    - #### createStatement

          public Statement createStatement(int resultSetType,
                                           int resultSetConcurrency,
                                           int resultSetHoldability,
                                           boolean translation)
                                    throws SQLException

      Similar to createStatement(int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag. If the translation flag is true then the returning `Statement` will have translation enabled. If the flag is false then the returning `Statement` will be a normal `Statement` with no translation features.
      Specified by:
      [`createStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int autoGeneratedKeys,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql, int autoGeneratedKeys) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int[] columnIndexes,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql, int\[\] columnIndexes) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    String[] columnNames,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql, String\[\] columnNames) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int resultSetType,
                                                    int resultSetConcurrency,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql, int resultSetType, int resultSetConcurrency) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatement

          public PreparedStatement prepareStatement(String sql,
                                                    int resultSetType,
                                                    int resultSetConcurrency,
                                                    int resultSetHoldability,
                                                    boolean translation)
                                             throws SQLException

      Similar to prepareStatement(String sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag. If the translation flag is true then the returning `PreparedStatement` will have translation enabled. If the flag is false then the returning `PreparedStatement` will be a normal `PreparedStatement` with no translation features.
      Specified by:
      [`prepareStatement`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql,
                                               boolean translation)
                                        throws SQLException

      Similar to prepareCall(String sql) but with an additional translation flag. If the translation flag is true then the returning `CallableStatement` will have translation enabled. If the flag is false then the returning `CallableStatement` will be a normal `CallableStatement` with no translation features.
      Specified by:
      [`prepareCall`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql,
                                               int resultSetType,
                                               int resultSetConcurrency,
                                               boolean translation)
                                        throws SQLException

      Similar to prepareCall(String sql, int resultSetType, int resultSetConcurrency) but with an additional translation flag. If the translation flag is true then the returning `CallableStatement` will have translation enabled. If the flag is false then the returning `CallableStatement` will be a normal `CallableStatement` with no translation features.
      Specified by:
      [`prepareCall`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareCall

          public CallableStatement prepareCall(String sql,
                                               int resultSetType,
                                               int resultSetConcurrency,
                                               int resultSetHoldability,
                                               boolean translation)
                                        throws SQLException

      Similar to prepareCall(String sql, int resultSetType, int resultSetConcurrency, int resultSetHoldability) but with an additional translation flag. If the translation flag is true then the returning `CallableStatement` will have translation enabled. If the flag is false then the returning `CallableStatement` will be a normal `CallableStatement` with no translation features.
      Specified by:
      [`prepareCall`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `translation` - boolean flag to enable or disable translation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSqlTranslationVersions

          public Map<OracleTranslatingConnection.SqlTranslationVersion,String> getSqlTranslationVersions(String sql,
                                                                                                         boolean suppressExceptions)
                                                                                                  throws SQLException

      Returns a map of all the translation versions of the query during SQL Translation. See the documentation of OracleTranslatingConnection.SqlTranslationVersion enum for more details about returning versions.
      Specified by:
      [`getSqlTranslationVersions`](../OracleTranslatingConnection.md) in interface [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

      Parameters:
      `sql` - vendor specific sql to be translated

      `suppressExceptions` - suppresses any exception raised during query translation and returns whatever is available. Useful to get JDBC_MARKER_CONVERTED version when the translation is throwing error.

      Returns:
      Map with all the translation versions of a query. In case of an Exception and suppressExceptions is true then the TRANSLATED version is null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there is a problem in query translation provided suppressExceptions is false.

      See Also:
      [`OracleTranslatingConnection`](../OracleTranslatingConnection.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishCallableStatement.md)
- [Next Class](BabelfishGenericProxy.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
