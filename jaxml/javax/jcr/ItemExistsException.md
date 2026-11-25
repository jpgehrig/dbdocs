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

- **[Prev Class](Item.md)**
- **[Next Class](ItemNotFoundException.md)**

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

## **Class ItemExistsException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.jcr.RepositoryException](RepositoryException.md)**

      - - **javax.jcr.ItemExistsException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class ItemExistsException
      extends RepositoryException

  **An exception thrown when an attempt is made to place an item in a position where another item already exists.**
  **See Also:**
  **[Serialized Form](../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                   |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ItemExistsException``()`<br>Constructs a new instance of this class with `null` as its detail message.                                                                       |
    | `ItemExistsException``(java.lang.String message)`<br>Constructs a new instance of this class with the specified detail message.                                               |
    | `ItemExistsException``(java.lang.String message, java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified detail message and root cause. |
    | `ItemExistsException``(java.lang.Throwable rootCause)`<br>Constructs a new instance of this class with the specified root cause.                                              |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class javax.jcr.[RepositoryException](RepositoryException.md)**

      **[`getCause`](RepositoryException.md)`, `[`getLocalizedMessage`](RepositoryException.md)`, `[`getMessage`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)`, `[`printStackTrace`](RepositoryException.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getStackTrace, getSuppressed, initCause, setStackTrace, toString`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **ItemExistsException**

          public ItemExistsException()

      **Constructs a new instance of this class with `null` as its detail message.**

    - #### **ItemExistsException**

          public ItemExistsException(java.lang.String message)

      **Constructs a new instance of this class with the specified detail message.**
      **Parameters:**
      **`message` - the detail message. The detail message is saved for later retrieval by the [`RepositoryException.getMessage()`](RepositoryException.md) method.**

    - #### **ItemExistsException**

          public ItemExistsException(java.lang.String message,
                                     java.lang.Throwable rootCause)

      **Constructs a new instance of this class with the specified detail message and root cause.**
      **Parameters:**
      **`message` - the detail message. The detail message is saved for later retrieval by the [`RepositoryException.getMessage()`](RepositoryException.md) method.**

      **`rootCause` - root failure cause**

    - #### **ItemExistsException**

          public ItemExistsException(java.lang.Throwable rootCause)

      **Constructs a new instance of this class with the specified root cause.**
      **Parameters:**
      **`rootCause` - root failure cause**

**Skip navigation links**

- **[Overview](../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../deprecated-list.md)**
- **[Index](../../index-all.md)**
- **[Help](../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Item.md)**
- **[Next Class](ItemNotFoundException.md)**

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
