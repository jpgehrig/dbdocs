Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- Prev Class
- [Next Class](ApplicationSessionService.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.security.xs.ee.session

## Class ApplicationSessionException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.security.xs.ee.session.ApplicationSessionException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [NamespaceNotFoundException](NamespaceNotFoundException.md)

  ------------------------------------------------------------------------



      public class ApplicationSessionException
      extends java.lang.Exception

  Exception thrown from RAS session service APIs. It is a wrapper of internal exception produeced by JDBC or XS APIs.
  See Also:
  [Serialized Form](../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ApplicationSessionException``()`<br>Default constructor.                                                                                        |
    | `ApplicationSessionException``(java.lang.String message)`<br>Constructor with the specified detail message.                                      |
    | `ApplicationSessionException``(java.lang.String message, java.lang.Throwable cause)`<br>Constructor with the specified detail message and cause. |
    | `ApplicationSessionException``(java.lang.Throwable cause)`<br>Constructor with the specified cause.                                              |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ApplicationSessionException

          public ApplicationSessionException(java.lang.Throwable cause)

      Constructor with the specified cause.
      Parameters:
      `cause` - internal exception being wrapped

    <!-- -->

    - #### ApplicationSessionException

          public ApplicationSessionException(java.lang.String message,
                                             java.lang.Throwable cause)

      Constructor with the specified detail message and cause.
      Parameters:
      `message` - detail exception message

      `cause` - internal exception being wrapped

    <!-- -->

    - #### ApplicationSessionException

          public ApplicationSessionException(java.lang.String message)

      Constructor with the specified detail message.
      Parameters:
      `message` - detail exception message

    <!-- -->

    - #### ApplicationSessionException

          public ApplicationSessionException()

      Default constructor.

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- Prev Class
- [Next Class](ApplicationSessionService.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
