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

- **[Prev Class](XMLDocumentHandler.md)**
- **[Next Class](XMLDOMImplementation.md)**

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

**oracle.xml.parser.v2**

## **Class XMLDOMException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **[org.w3c.dom.DOMException](../../../../org/w3c/dom/DOMException.md)**

        - - **oracle.xml.parser.v2.XMLDOMException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XMLDOMException
      extends DOMException

  **This class is used to throw DOM exceptions.**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from class org.w3c.dom.[DOMException](../../../../org/w3c/dom/DOMException.md)**

      **[`code`](../../../../org/w3c/dom/DOMException.md)`, `[`DOMSTRING_SIZE_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`HIERARCHY_REQUEST_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INDEX_SIZE_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INUSE_ATTRIBUTE_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INVALID_ACCESS_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INVALID_CHARACTER_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INVALID_MODIFICATION_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`INVALID_STATE_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`NAMESPACE_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`NO_DATA_ALLOWED_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`NO_MODIFICATION_ALLOWED_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`NOT_FOUND_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`NOT_SUPPORTED_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`SYNTAX_ERR`](../../../../org/w3c/dom/DOMException.md)`, `[`WRONG_DOCUMENT_ERR`](../../../../org/w3c/dom/DOMException.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------|
    | `XMLDOMException``(short code)`<br>Constructs a `XMLDOMException` exception with a specified message and a code.                     |
    | `XMLDOMException``(short code, java.lang.String s)`<br>Constructs a `XMLDOMException` exception with a specified message and a code. |

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

    ### **Constructor Detail**

    - #### **XMLDOMException**

          public XMLDOMException(short code,
                                 java.lang.String s)

      **Constructs a `XMLDOMException` exception with a specified message and a code.**
      **Parameters:**
      **`code` - Code indicated in DOM interface, uses default message**

    - #### **XMLDOMException**

          public XMLDOMException(short code)

      **Constructs a `XMLDOMException` exception with a specified message and a code.**
      **Parameters:**
      **`code` - Code indicated in DOM interface, uses default message**

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

- **[Prev Class](XMLDocumentHandler.md)**
- **[Next Class](XMLDOMImplementation.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
