Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolAdapter.md)
- [Next Class](UniversalConnectionPoolLifeCycleState.md)

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

## Class UniversalConnectionPoolException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.ucp.UniversalConnectionPoolException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [NoAvailableConnectionsException](NoAvailableConnectionsException.md)

  ------------------------------------------------------------------------



      public class UniversalConnectionPoolException
      extends java.lang.Exception

  This exception is the base exception for Universal Connection Pool exceptions.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `protected int`   | `errorCode`           |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                      |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `UniversalConnectionPoolException``()`<br>Constructs a new exception with `null` as its detailed message.                                                                                                                                                        |
    | `UniversalConnectionPoolException``(java.lang.String message)`<br>Constructs a new exception with the specified detail message.                                                                                                                                  |
    | `UniversalConnectionPoolException``(java.lang.String message, int errorCode)`<br>Constructs a new exception with the specified detail message and error code.                                                                                                    |
    | `UniversalConnectionPoolException``(java.lang.String message, java.lang.Throwable cause)`<br>Constructs a new exception with the specified detail message and cause.                                                                                             |
    | `UniversalConnectionPoolException``(java.lang.Throwable cause)`<br>Constructs a new exception with the specified cause and a detail message of `(cause==null ? null : cause.toString())`, which typically contains the class and detail message of the `cause`). |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                    |
    |-------------------|---------------------------------------------------------------------------|
    | `int`             | `getErrorCode``()`<br>Gets the error code associated with this exception. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### errorCode

          protected int errorCode

  <!-- -->

  - ### Constructor Detail

    - #### UniversalConnectionPoolException

          public UniversalConnectionPoolException()

      Constructs a new exception with `null` as its detailed message. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.

    <!-- -->

    - #### UniversalConnectionPoolException

          public UniversalConnectionPoolException(java.lang.String message)

      Constructs a new exception with the specified detail message. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method.

    <!-- -->

    - #### UniversalConnectionPoolException

          public UniversalConnectionPoolException(java.lang.String message,
                                                  int errorCode)

      Constructs a new exception with the specified detail message and error code. The cause is not initialized and may subsequently be initialized by a call to `Throwable.initCause(java.lang.Throwable)`.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method.

      `errorCode` - the error code for this exception.

    <!-- -->

    - #### UniversalConnectionPoolException

          public UniversalConnectionPoolException(java.lang.String message,
                                                  java.lang.Throwable cause)

      Constructs a new exception with the specified detail message and cause.
      Note that the detail message associated with `cause` is *not* automatically incorporated in this exception's detail message.

      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `Throwable.getMessage()` method).

      `cause` - the cause. The cause is saved for later retrieval by the `Throwable.getCause()` method. A `null` value is permitted and indicates that the cause is nonexistent or unknown.

    <!-- -->

    - #### UniversalConnectionPoolException

          public UniversalConnectionPoolException(java.lang.Throwable cause)

      Constructs a new exception with the specified cause and a detail message of `(cause==null ? null : cause.toString())`, which typically contains the class and detail message of the `cause`). This constructor is useful for exceptions that are little more than wrappers for other throwables (for example, `PrivilegedActionException`).
      Parameters:
      `cause` - the cause. The cause is saved for later retrieval by the `Throwable.getCause()` method. A `null` value is permitted and indicates that the cause is nonexistent or unknown.

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public int getErrorCode()

      Gets the error code associated with this exception.
      Returns:
      the error code.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolException.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolAdapter.md)
- [Next Class](UniversalConnectionPoolLifeCycleState.md)

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
