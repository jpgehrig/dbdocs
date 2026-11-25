Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NoAvailableConnectionsException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionRetrievalInfo.md)
- [Next Class](TimeToLiveConnectionTimeoutCallback.md)

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

oracle.ucp

## Class NoAvailableConnectionsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [oracle.ucp.UniversalConnectionPoolException](UniversalConnectionPoolException.md)

      - - oracle.ucp.NoAvailableConnectionsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NoAvailableConnectionsException
      extends UniversalConnectionPoolException

  An exception indicating that there are no available connections in the connection pool.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.ucp.[UniversalConnectionPoolException](UniversalConnectionPoolException.md)

      [`errorCode`](UniversalConnectionPoolException.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NoAvailableConnectionsException``()`<br>Constructs a new exception with `null` as its detail message.                                                                                                                                                          |
    | `NoAvailableConnectionsException``(java.lang.String message)`<br>Constructs a new exception with the specified detail message.                                                                                                                                  |
    | `NoAvailableConnectionsException``(java.lang.String message, int errorCode)`<br>Constructs a new exception with the specified detail message and error code.                                                                                                    |
    | `NoAvailableConnectionsException``(java.lang.String message, java.lang.Throwable cause)`<br>Constructs a new exception with the specified detail message and cause.                                                                                             |
    | `NoAvailableConnectionsException``(java.lang.Throwable cause)`<br>Constructs a new exception with the specified cause and a detail message of `(cause==null ? null : cause.toString())`, which typically contains the class and detail message of the `cause`). |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.ucp.[UniversalConnectionPoolException](UniversalConnectionPoolException.md)

      [`getErrorCode`](UniversalConnectionPoolException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NoAvailableConnectionsException

          public NoAvailableConnectionsException()

      Constructs a new exception with `null` as its detail message. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.

    <!-- -->

    - #### NoAvailableConnectionsException

          public NoAvailableConnectionsException(java.lang.String message)

      Constructs a new exception with the specified detail message. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method.

    <!-- -->

    - #### NoAvailableConnectionsException

          public NoAvailableConnectionsException(java.lang.String message,
                                                 int errorCode)

      Constructs a new exception with the specified detail message and error code. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method.

      `errorCode` - the error code for this exception.

    <!-- -->

    - #### NoAvailableConnectionsException

          public NoAvailableConnectionsException(java.lang.String message,
                                                 java.lang.Throwable cause)

      Constructs a new exception with the specified detail message and cause.
      Note that the detail message associated with `cause` is *not* automatically incorporated in this exception's detail message.

      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method.

      `cause` - the cause. The cause is saved for later retrieval by the `Throwable.getCause()` method. A `null` value is permitted and indicates that the cause is nonexistent or unknown.

    <!-- -->

    - #### NoAvailableConnectionsException

          public NoAvailableConnectionsException(java.lang.Throwable cause)

      Constructs a new exception with the specified cause and a detail message of `(cause==null ? null : cause.toString())`, which typically contains the class and detail message of the `cause`). This constructor is useful for exceptions that are little more than wrappers for other throwables (for example, `PrivilegedActionException`).
      Parameters:
      `cause` - the cause. The cause is saved for later retrieval by the `Throwable.getCause()` method. A `null` value is permitted and indicates that the cause is nonexistent or unknown.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NoAvailableConnectionsException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionRetrievalInfo.md)
- [Next Class](TimeToLiveConnectionTimeoutCallback.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
