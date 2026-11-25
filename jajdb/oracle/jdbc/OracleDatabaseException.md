Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDatabaseException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleData.md)
- [Next Class](OracleDatabaseMetaData.md)

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

## Class OracleDatabaseException

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

  - - [java.lang.Exception](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)

    - - oracle.jdbc.OracleDatabaseException

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OracleDatabaseException
      extends Exception

  Provides additional information about the Oracle error. Any information which is specific to the Oracle error may go into this class. In case of any parsing error while executing sql in Oracle server, an instance of this class is set as cause of the SQLException thrown by executeXXX methods in oracle.jdbc.Statement and its subclasses. For example, the error position in the failed SQL can be obtained as below,
        try{
          myStatement.executeUpdate();
        }
        catch (SQLException sqlx) {
          if(sqlx.getCause() != null &&
              sqlx.getCause() instanceof OracleDatabaseException) {
            int sqlErrorPosition =
               ((OracleDatabaseException)sqlx.getCause()).getErrorPosition();
          }
        }


  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleDatabaseException``(int errorPosition, int oracleErrorNumber, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oracleErrorMessage, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` originalSql)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                |
    |-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                           | `getErrorPosition``()`<br>In case of a parsing error, this method returns the position of the error in the actual SQL which has failed in the server. |
    | `int`                                                                                           | `getOracleErrorNumber``()`<br>Returns the Oracle error number for this failure.                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getOriginalSql``()`<br>Returns the original SQL used to create the Statement.                                                                        |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getSql``()`<br>Returns the actual SQL which was sent to the server.                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`                                                                                                                                        |

    - ### Methods inherited from class java.lang.[Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

      [`addSuppressed`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#addSuppressed_java_lang_Throwable_)`, `[`fillInStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#fillInStackTrace__)`, `[`getCause`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getCause__)`, `[`getLocalizedMessage`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getLocalizedMessage__)`, `[`getMessage`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getMessage__)`, `[`getStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getStackTrace__)`, `[`getSuppressed`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getSuppressed__)`, `[`initCause`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#initCause_java_lang_Throwable_)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace__)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace_java_io_PrintStream_)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace_java_io_PrintWriter_)`, `[`setStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#setStackTrace_java_lang_StackTraceElement_A_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleDatabaseException

          public OracleDatabaseException(int errorPosition,
                                         int oracleErrorNumber,
                                         String oracleErrorMessage,
                                         String sql,
                                         String originalSql)

  <!-- -->

  - ### Method Detail

    - #### getErrorPosition

          public int getErrorPosition()

      In case of a parsing error, this method returns the position of the error in the actual SQL which has failed in the server. The position corresponds to the actual SQL sent to the server returned by `getSql()`. It may be different from the original SQL returned by `getOriginalSql()`.
      Returns:
      errorPosition

    <!-- -->

    - #### getOracleErrorNumber

          public int getOracleErrorNumber()

      Returns the Oracle error number for this failure.
      Returns:
      OracleErrorNumber

    <!-- -->

    - #### getSql

          public String getSql()

      Returns the actual SQL which was sent to the server.
      Returns:
      sql

    <!-- -->

    - #### getOriginalSql

          public String getOriginalSql()

      Returns the original SQL used to create the Statement. This SQL may have been modified before being sent to the database to be executed. The SQL sent to the database is returned by `getSql()`. The method `getErrorPosition()` returns the position of the error in the actual SQL sent to the database, not the original SQL returned by this method.
      Returns:
      originalSql

    <!-- -->

    - #### toString

          public String toString()

      Overrides:
      [`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#toString__) in class [`Throwable`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDatabaseException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleData.md)
- [Next Class](OracleDatabaseMetaData.md)

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
