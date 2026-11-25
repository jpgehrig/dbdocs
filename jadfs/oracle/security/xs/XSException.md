Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](XSAuthenticationModule.md)
- [Next Class](XSPrincipalException.md)

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

oracle.security.xs

## Class XSException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.security.xs.XSException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [AccessDeniedException](AccessDeniedException.md), [InvalidSessionException](InvalidSessionException.md), [InvalidXSAttributeException](InvalidXSAttributeException.md), [InvalidXSNamespaceException](InvalidXSNamespaceException.md), [InvalidXSUserException](InvalidXSUserException.md), [NotAttachedException](NotAttachedException.md), [SessionNamespaceException](SessionNamespaceException.md), [XSPrincipalException](XSPrincipalException.md), [XSSessionException](XSSessionException.md), [XSSessionManagerException](XSSessionManagerException.md)

  ------------------------------------------------------------------------



      public class XSException
      extends java.lang.Exception

  Base exception class and a wrapper for server-side error. Exception thrown when an error occurs in most of the APIs. For example, this exception is thrown when an invalid or null parameter is passed to the Session API or an error from the server round-trip operations occurs.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSException``()`<br>Creates a new `XSException`.                                                                                                                                             |
    | `XSException``(java.lang.String message)`<br>Creates a new XSException with the specified exception message.                                                                                  |
    | `XSException``(java.lang.String errKey, java.lang.Object[] parameters)`<br>Creates a new XSException with the specified error key and parameters.                                             |
    | `XSException``(java.lang.String errKey, java.lang.Object[] parameters, java.lang.Throwable cause)`<br>Creates a new XSException with the specified error key, parameters, and cause of error. |
    | `XSException``(java.lang.String message, java.lang.Throwable cause)`<br>Creates a new XSException with the specified exception message and cause of exception.                                |
    | `XSException``(java.lang.Throwable cause)`<br>Creates a new XSException with the specified cause of the exception.                                                                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                          |
    |--------------------|-----------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getMessage``()`<br>Returns the detailed message of the exception.                                              |
    | `java.lang.String` | `getMessage``(java.util.Locale lc)`<br>Returns the detailed message of the exception in the specified `Locale`. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSException

          public XSException()

      Creates a new `XSException`.

    <!-- -->

    - #### XSException

          public XSException(java.lang.String message)

      Creates a new XSException with the specified exception message.
      Parameters:
      `message` - the exception message

    <!-- -->

    - #### XSException

          public XSException(java.lang.Throwable cause)

      Creates a new XSException with the specified cause of the exception.
      Parameters:
      `cause` - the cause of the exception

    <!-- -->

    - #### XSException

          public XSException(java.lang.String message,
                             java.lang.Throwable cause)

      Creates a new XSException with the specified exception message and cause of exception.
      Parameters:
      `message` - the exception message

      `cause` - the cause of the exception

    <!-- -->

    - #### XSException

          public XSException(java.lang.String errKey,
                             java.lang.Object[] parameters,
                             java.lang.Throwable cause)

      Creates a new XSException with the specified error key, parameters, and cause of error.
      Parameters:
      `errKey` - the error key

      `parameters` - the parameters

      `cause` - the cause of the error

    <!-- -->

    - #### XSException

          public XSException(java.lang.String errKey,
                             java.lang.Object[] parameters)

      Creates a new XSException with the specified error key and parameters.
      Parameters:
      `errKey` - the error key

      `parameters` - the parameters

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Returns the detailed message of the exception.
      Overrides:
      `getMessage` in class `java.lang.Throwable`

      Returns:
      the detail message string of this exception instance

    <!-- -->

    - #### getMessage

          public java.lang.String getMessage(java.util.Locale lc)

      Returns the detailed message of the exception in the specified `Locale`.
      Parameters:
      `lc` - `Locale`

      Returns:
      the detail message string of this exception instance in the specified `Locale`

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](XSAuthenticationModule.md)
- [Next Class](XSPrincipalException.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
