Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](MergeException.md)**
- **[Next Class](NamespaceRegistry.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr**

## **Class NamespaceException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.jcr.RepositoryException](RepositoryException.md)**

      - - **javax.jcr.NamespaceException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class NamespaceException
      extends RepositoryException

  **Exception thrown by [`Session.setNamespacePrefix(String prefix, String uri)`](Session.md) if the specified `uri` is not registered in the [`NamespaceRegistry`](NamespaceRegistry.md)**
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NamespaceException``()`<br>Constructs a new instance of this class with `null` as its detail message.                                                                       |
    | `NamespaceException``(java.lang.String message)`<br>Constructs a new instance of this class with the specified detail message.                                               |
    | `NamespaceException``(java.lang.String message, java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified detail message and root cause. |
    | `NamespaceException``(java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified root cause.                                              |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class javax.jcr.[RepositoryException](RepositoryException.md)

      [`getCause`](RepositoryException.md)`, `[`getLocalizedMessage`](RepositoryException.md)`, `[`getMessage`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getStackTrace, getSuppressed, initCause, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NamespaceException

          public NamespaceException()

      Constructs a new instance of this class with `null` as its detail message.

    <!-- -->

    - #### NamespaceException

          public NamespaceException(java.lang.String message)

      Constructs a new instance of this class with the specified detail message.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the [`RepositoryException.getMessage()`](RepositoryException.md) method.

    <!-- -->

    - #### NamespaceException

          public NamespaceException(java.lang.String message,
                                    java.lang.Throwable rootCause)

      Constructs a new instance of this class with the specified detail message and root cause.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the [`RepositoryException.getMessage()`](RepositoryException.md) method.

      `rootCause` - root failure cause

    <!-- -->

    - #### NamespaceException

          public NamespaceException(java.lang.Throwable rootCause)

      Constructs a new instance of this class with the specified root cause.
      Parameters:
      `rootCause` - root failure cause

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](MergeException.md)**
- **[Next Class](NamespaceRegistry.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
