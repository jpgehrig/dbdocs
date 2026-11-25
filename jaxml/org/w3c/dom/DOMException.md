Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DOMErrorHandler.md)**
- **[Next Class](DOMImplementation.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**org.w3c.dom**

## **Class DOMException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **org.w3c.dom.DOMException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBDOMException](../../../oracle/xdb/dom/XDBDOMException.md), [XMLDOMException](../../../oracle/xml/parser/v2/XMLDOMException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DOMException
      extends java.lang.RuntimeException

  **DOM operations only raise exceptions in "exceptional" circumstances, i.e., when an operation is impossible to perform (either for logical reasons, because data is lost, or because the implementation has become unstable). In general, DOM methods return specific error values in ordinary processing situations, such as out-of-bound errors when using `NodeList`.**
  **Implementations should raise other exceptions under other circumstances. For example, implementations should raise an implementation-dependent exception if a `null` argument is passed.**

  **Some languages and object systems do not support the concept of exceptions. For such systems, error conditions may be indicated using native error reporting mechanisms. For some bindings, for example, methods may return error codes similar to those listed in the corresponding method descriptions.**

  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                         |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | `short`           | `code`                                                                                                                        |
    | `static short`    | `DOMSTRING_SIZE_ERR`<br>If the specified range of text does not fit into a DOMString                                          |
    | `static short`    | `HIERARCHY_REQUEST_ERR`<br>If any node is inserted somewhere it doesn't belong                                                |
    | `static short`    | `INDEX_SIZE_ERR`<br>If index or size is negative, or greater than the allowed value                                           |
    | `static short`    | `INUSE_ATTRIBUTE_ERR`<br>If an attempt is made to add an attribute that is already in use elsewhere                           |
    | `static short`    | `INVALID_ACCESS_ERR`<br>If a parameter or an operation is not supported by the underlying object.                             |
    | `static short`    | `INVALID_CHARACTER_ERR`<br>If an invalid or illegal character is specified, such as in a name.                                |
    | `static short`    | `INVALID_MODIFICATION_ERR`<br>If an attempt is made to modify the type of the underlying object.                              |
    | `static short`    | `INVALID_STATE_ERR`<br>If an attempt is made to use an object that is not, or is no longer, usable.                           |
    | `static short`    | `NAMESPACE_ERR`<br>If an attempt is made to create or change an object in a way which is incorrect with regard to namespaces. |
    | `static short`    | `NO_DATA_ALLOWED_ERR`<br>If data is specified for a node which does not support data                                          |
    | `static short`    | `NO_MODIFICATION_ALLOWED_ERR`<br>If an attempt is made to modify an object where modifications are not allowed                |
    | `static short`    | `NOT_FOUND_ERR`<br>If an attempt is made to reference a node in a context where it does not exist                             |
    | `static short`    | `NOT_SUPPORTED_ERR`<br>If the implementation does not support the requested type of object or operation.                      |
    | `static short`    | `SYNTAX_ERR`<br>If an invalid or illegal string is specified.                                                                 |
    | `static short`    | `WRONG_DOCUMENT_ERR`<br>If a node is used in a different document than the one that created it (that doesn't support it)      |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                             |
    |---------------------------------------------------------|
    | `DOMException``(short code, java.lang.String message)`  |

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

    - #### **INDEX_SIZE_ERR**

          public static final short INDEX_SIZE_ERR

      **If index or size is negative, or greater than the allowed value**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **DOMSTRING_SIZE_ERR**

          public static final short DOMSTRING_SIZE_ERR

      **If the specified range of text does not fit into a DOMString**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **HIERARCHY_REQUEST_ERR**

          public static final short HIERARCHY_REQUEST_ERR

      **If any node is inserted somewhere it doesn't belong**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **WRONG_DOCUMENT_ERR**

          public static final short WRONG_DOCUMENT_ERR

      **If a node is used in a different document than the one that created it (that doesn't support it)**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **INVALID_CHARACTER_ERR**

          public static final short INVALID_CHARACTER_ERR

      **If an invalid or illegal character is specified, such as in a name. See production 2 in the XML specification for the definition of a legal character, and production 5 for the definition of a legal name character.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **NO_DATA_ALLOWED_ERR**

          public static final short NO_DATA_ALLOWED_ERR

      **If data is specified for a node which does not support data**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **NO_MODIFICATION_ALLOWED_ERR**

          public static final short NO_MODIFICATION_ALLOWED_ERR

      **If an attempt is made to modify an object where modifications are not allowed**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **NOT_FOUND_ERR**

          public static final short NOT_FOUND_ERR

      **If an attempt is made to reference a node in a context where it does not exist**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **NOT_SUPPORTED_ERR**

          public static final short NOT_SUPPORTED_ERR

      **If the implementation does not support the requested type of object or operation.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **INUSE_ATTRIBUTE_ERR**

          public static final short INUSE_ATTRIBUTE_ERR

      **If an attempt is made to add an attribute that is already in use elsewhere**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **INVALID_STATE_ERR**

          public static final short INVALID_STATE_ERR

      **If an attempt is made to use an object that is not, or is no longer, usable.**
      **Since:**
      **DOM Level 2**

      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **SYNTAX_ERR**

          public static final short SYNTAX_ERR

      **If an invalid or illegal string is specified.**
      **Since:**
      **DOM Level 2**

      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **INVALID_MODIFICATION_ERR**

          public static final short INVALID_MODIFICATION_ERR

      **If an attempt is made to modify the type of the underlying object.**
      **Since:**
      **DOM Level 2**

      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **NAMESPACE_ERR**

          public static final short NAMESPACE_ERR

      **If an attempt is made to create or change an object in a way which is incorrect with regard to namespaces.**
      **Since:**
      **DOM Level 2**

      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **INVALID_ACCESS_ERR**

          public static final short INVALID_ACCESS_ERR

      **If a parameter or an operation is not supported by the underlying object.**
      **Since:**
      **DOM Level 2**

      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

  <!-- -->

  -

    ### **Constructor Detail**

    - #### **DOMException**

          public DOMException(short code,
                              java.lang.String message)

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DOMErrorHandler.md)**
- **[Next Class](DOMImplementation.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
