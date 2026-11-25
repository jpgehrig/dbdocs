Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAException.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](OracleXAResource.md)

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

oracle.jdbc.xa

## Class OracleXAException

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

  - - [java.lang.Exception](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)

    - - [javax.transaction.xa.XAException](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      - - oracle.jdbc.xa.OracleXAException

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OracleXAException
      extends XAException

  OracleXAException extends XAException to leverage Oracle SQL Error number corresponding to the XA Exception.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class javax.transaction.xa.[XAException](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

      [`errorCode`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#errorCode)`, `[`XA_HEURCOM`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_HEURCOM)`, `[`XA_HEURHAZ`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_HEURHAZ)`, `[`XA_HEURMIX`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_HEURMIX)`, `[`XA_HEURRB`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_HEURRB)`, `[`XA_NOMIGRATE`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_NOMIGRATE)`, `[`XA_RBBASE`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBBASE)`, `[`XA_RBCOMMFAIL`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBCOMMFAIL)`, `[`XA_RBDEADLOCK`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBDEADLOCK)`, `[`XA_RBEND`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBEND)`, `[`XA_RBINTEGRITY`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBINTEGRITY)`, `[`XA_RBOTHER`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBOTHER)`, `[`XA_RBPROTO`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBPROTO)`, `[`XA_RBROLLBACK`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBROLLBACK)`, `[`XA_RBTIMEOUT`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBTIMEOUT)`, `[`XA_RBTRANSIENT`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RBTRANSIENT)`, `[`XA_RDONLY`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RDONLY)`, `[`XA_RETRY`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XA_RETRY)`, `[`XAER_ASYNC`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_ASYNC)`, `[`XAER_DUPID`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_DUPID)`, `[`XAER_INVAL`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_INVAL)`, `[`XAER_NOTA`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_NOTA)`, `[`XAER_OUTSIDE`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_OUTSIDE)`, `[`XAER_PROTO`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_PROTO)`, `[`XAER_RMERR`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_RMERR)`, `[`XAER_RMFAIL`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true#XAER_RMFAIL)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXAException``()`<br>Default OracleXAException class.                                                                                              |
    | `OracleXAException``(int error)`<br>Default OracleXAException class that takes an error code which is a combination of Oracle Sql No.                    |
    | `OracleXAException``(int error, int _xaError)`                                                                                                           |
    | `OracleXAException``(`[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` sqlex, int _xaError)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                             | Method and Description                                                                                                                                                                                |
    |-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`                                                                                                                  | `errorConvert``(int err, int defaultErrorCode)`                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                               | `getMessage``()`                                                                                                                                                                                      |
    | `int`                                                                                                                         | `getOracleError``()`<br>getOracleError returns the Oracle Error code corresponding to this exception.                                                                                                 |
    | `int`                                                                                                                         | `getXAError``()`<br>getXAError returns the XA Error code corresponding to this exception.                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getXAErrorMessage``(int eCode)`                                                                                                                                                                      |
    | `static `[`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) | `newXAException``(oracle.jdbc.internal.OracleConnection conn, int error)`                                                                                                                             |
    | `static `[`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) | `newXAException``(oracle.jdbc.internal.OracleConnection conn, int error, int xaerror)`                                                                                                                |
    | `static `[`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) | `newXAException``(oracle.jdbc.internal.OracleConnection conn, int error, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` sqlException)`  |
    | `static `[`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) | `newXAException``(oracle.jdbc.internal.OracleConnection conn, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` sqlexc, int xaerror)`      |

    - ### Methods inherited from class java.lang.[Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

      [`addSuppressed`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#addSuppressed_java_lang_Throwable_)`, `[`fillInStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#fillInStackTrace__)`, `[`getCause`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getCause__)`, `[`getLocalizedMessage`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getLocalizedMessage__)`, `[`getStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getStackTrace__)`, `[`getSuppressed`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getSuppressed__)`, `[`initCause`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#initCause_java_lang_Throwable_)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace__)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace_java_io_PrintStream_)`, `[`printStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#printStackTrace_java_io_PrintWriter_)`, `[`setStackTrace`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#setStackTrace_java_lang_StackTraceElement_A_)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#toString__)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleXAException

          public OracleXAException()

      Default OracleXAException class.

    <!-- -->

    - #### OracleXAException

          public OracleXAException(int error)

      Default OracleXAException class that takes an error code which is a combination of Oracle Sql No. and XA Error No.
      Parameters:
      `error` - Oracle Error no.

    <!-- -->

    - #### OracleXAException

          public OracleXAException(int error,
                                   int _xaError)

    <!-- -->

    - #### OracleXAException

          public OracleXAException(SQLException sqlex,
                                   int _xaError)

  <!-- -->

  - ### Method Detail

    - #### newXAException

          public static XAException newXAException(oracle.jdbc.internal.OracleConnection conn,
                                                   int error)

    <!-- -->

    - #### newXAException

          public static XAException newXAException(oracle.jdbc.internal.OracleConnection conn,
                                                   int error,
                                                   SQLException sqlException)

    <!-- -->

    - #### newXAException

          public static XAException newXAException(oracle.jdbc.internal.OracleConnection conn,
                                                   int error,
                                                   int xaerror)

    <!-- -->

    - #### newXAException

          public static XAException newXAException(oracle.jdbc.internal.OracleConnection conn,
                                                   SQLException sqlexc,
                                                   int xaerror)

    <!-- -->

    - #### errorConvert

          public static int errorConvert(int err,
                                         int defaultErrorCode)

    <!-- -->

    - #### getXAError

          public int getXAError()

      getXAError returns the XA Error code corresponding to this exception. The error codes are the one defined in XAException class.
      Returns:
      int XA Error Code.

    <!-- -->

    - #### getOracleError

          public int getOracleError()

      getOracleError returns the Oracle Error code corresponding to this exception. Return values are the standard ORA errors. Returns zero when one doesn't exist.
      Returns:
      int Oracle Error Code.

    <!-- -->

    - #### getMessage

          public String getMessage()

      Overrides:
      [`getMessage`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true#getMessage__) in class [`Throwable`](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true)

    <!-- -->

    - #### getXAErrorMessage

          public static String getXAErrorMessage(int eCode)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAException.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](OracleXAResource.md)

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
