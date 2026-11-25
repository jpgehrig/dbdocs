Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Range.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.w3c.dom.ranges**

## **Class RangeException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **org.w3c.dom.ranges.RangeException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class RangeException
      extends java.lang.RuntimeException

  **Range operations may throw a `RangeException` as specified in their method descriptions.**
  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                       |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static short`    | `BAD_BOUNDARYPOINTS_ERR`<br>If the boundary-points of a Range do not meet specific requirements.                                                                            |
    | `short`           | `code`                                                                                                                                                                      |
    | `static short`    | `INVALID_NODE_TYPE_ERR`<br>If the container of an boundary-point of a Range is being set to either a node of an invalid type or a node with an ancestor of an invalid type. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                               |
    |-----------------------------------------------------------|
    | `RangeException``(short code, java.lang.String message)`  |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Field Detail**

    - #### **code**

          public short code

    - #### **BAD_BOUNDARYPOINTS_ERR**

          public static final short BAD_BOUNDARYPOINTS_ERR

      **If the boundary-points of a Range do not meet specific requirements.**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

    - #### **INVALID_NODE_TYPE_ERR**

          public static final short INVALID_NODE_TYPE_ERR

      **If the container of an boundary-point of a Range is being set to either a node of an invalid type or a node with an ancestor of an invalid type.**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

  <!-- -->

  -

    ### **Constructor Detail**

    - #### **RangeException**

          public RangeException(short code,
                                java.lang.String message)

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Range.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
