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

- **[Prev Class](Repository.md)**
- **[Next Class](Session.md)**

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

## **Class RepositoryException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **javax.jcr.RepositoryException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[AccessDeniedException](AccessDeniedException.md), [ConstraintViolationException](nodetype/ConstraintViolationException.md), [InvalidItemStateException](InvalidItemStateException.md), [InvalidQueryException](query/InvalidQueryException.md), [InvalidSerializedDataException](InvalidSerializedDataException.md), [ItemExistsException](ItemExistsException.md), [ItemNotFoundException](ItemNotFoundException.md), [LockException](lock/LockException.md), [LoginException](LoginException.md), [MergeException](MergeException.md), [NamespaceException](NamespaceException.md), [NoSuchNodeTypeException](nodetype/NoSuchNodeTypeException.md), [NoSuchWorkspaceException](NoSuchWorkspaceException.md), [PathNotFoundException](PathNotFoundException.md), [ReferentialIntegrityException](ReferentialIntegrityException.md), [UnsupportedRepositoryOperationException](UnsupportedRepositoryOperationException.md), [ValueFormatException](ValueFormatException.md), [VersionException](version/VersionException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class RepositoryException
      extends java.lang.Exception

  **Main exception thrown by classes in this package. May contain an error message and/or another nested exception.**
  **See Also:**
  **[Serialized Form](../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                   |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `RepositoryException``()`<br>Constructs a new instance of this class with `null` as its detail message.                                                                       |
    | `RepositoryException``(java.lang.String message)`<br>Constructs a new instance of this class with the specified detail message.                                               |
    | `RepositoryException``(java.lang.String message, java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified detail message and root cause. |
    | `RepositoryException``(java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified root cause.                                              |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                 |
    |-----------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Throwable` | `getCause``()`<br>Returns the cause of this exception or `null` if the cause is nonexistent or unknown.                                |
    | `java.lang.String`    | `getLocalizedMessage``()`<br>Returns the localized message, including the localized message from the nested exception if there is one. |
    | `java.lang.String`    | `getMessage``()`<br>Returns the detail message, including the message from the nested exception if there is one.                       |
    | `void`                | `printStackTrace``()`<br>Prints this `RepositoryException` and its backtrace to the standard error stream.                             |
    | `void`                | `printStackTrace``(java.io.PrintStream s)`<br>Prints this `RepositoryException` and its backtrace to the specified print stream.       |
    | `void`                | `printStackTrace``(java.io.PrintWriter s)`<br>Prints this `RepositoryException` and its backtrace to the specified print writer.       |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getStackTrace, getSuppressed, initCause, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RepositoryException

          public RepositoryException()

      Constructs a new instance of this class with `null` as its detail message.

    <!-- -->

    - #### RepositoryException

          public RepositoryException(java.lang.String message)

      Constructs a new instance of this class with the specified detail message.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `getMessage()` method.

    <!-- -->

    - #### RepositoryException

          public RepositoryException(java.lang.String message,
                                     java.lang.Throwable rootCause)

      Constructs a new instance of this class with the specified detail message and root cause.
      Parameters:
      `message` - the detail message. The detail message is saved for later retrieval by the `getMessage()` method.

      `rootCause` - root failure cause

    <!-- -->

    - #### RepositoryException

          public RepositoryException(java.lang.Throwable rootCause)

      Constructs a new instance of this class with the specified root cause.
      Parameters:
      `rootCause` - root failure cause

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Returns the detail message, including the message from the nested exception if there is one.
      Overrides:
      `getMessage` in class `java.lang.Throwable`

      Returns:
      the detail message (which may be `null`).

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage()

      Returns the localized message, including the localized message from the nested exception if there is one.
      Overrides:
      `getLocalizedMessage` in class `java.lang.Throwable`

      Returns:
      The localized description of this exception.

    <!-- -->

    - #### getCause

          public java.lang.Throwable getCause()

      Returns the cause of this exception or `null` if the cause is nonexistent or unknown. (The cause is the throwable that caused this exception to get thrown.)
      Overrides:
      `getCause` in class `java.lang.Throwable`

      Returns:
      the cause of this exception or `null` if the cause is nonexistent or unknown.

    <!-- -->

    - #### printStackTrace

          public void printStackTrace()

      Prints this `RepositoryException` and its backtrace to the standard error stream.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintStream s)

      Prints this `RepositoryException` and its backtrace to the specified print stream.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `s` - `PrintStream` to use for output

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintWriter s)

      Prints this `RepositoryException` and its backtrace to the specified print writer.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `s` - `PrintWriter` to use for output

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

- **[Prev Class](Repository.md)**
- **[Next Class](Session.md)**

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
