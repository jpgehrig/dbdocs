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

- **[Prev Class](XSQLServletPageRequest.md)**
- **[Next Class](XSQLUtil.md)**

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

**oracle.xml.xsql**

## **Class XSQLStylesheetProcessor**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLStylesheetProcessor**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLStylesheetProcessor
      extends java.lang.Object

  **XSLT Stylesheet Processing Engine**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static char`     | `APOS`                |
    | `static char`     | `QUOTE`               |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `XSQLStylesheetProcessor``()`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                               |
    |---------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `processToDocument``(`[`Document`](../../../org/w3c/dom/Document.md)` xml, java.lang.String xslURI, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`  |
    | `static void`                                           | `processToWriter``(`[`Document`](../../../org/w3c/dom/Document.md)` xml, java.lang.String xslURI, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### QUOTE

          public static final char QUOTE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### APOS

          public static final char APOS

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XSQLStylesheetProcessor

          public XSQLStylesheetProcessor()

  <!-- -->

  - ### Method Detail

    - #### processToDocument

          public static Document processToDocument(Document xml,
                                                   java.lang.String xslURI,
                                                   XSQLPageRequest env)
                                            throws java.lang.Exception,
                                                   SAXParseException,
                                                   XSLException,
                                                   java.io.FileNotFoundException

      Throws:
      `java.lang.Exception`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`XSLException`](../parser/v2/XSLException.md)

      `java.io.FileNotFoundException`

    <!-- -->

    - #### processToWriter

          public static void processToWriter(Document xml,
                                             java.lang.String xslURI,
                                             XSQLPageRequest env)
                                      throws java.lang.Exception,
                                             SAXParseException,
                                             XSLException,
                                             java.io.FileNotFoundException

      Throws:
      `java.lang.Exception`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`XSLException`](../parser/v2/XSLException.md)

      `java.io.FileNotFoundException`

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

- **[Prev Class](XSQLServletPageRequest.md)**
- **[Next Class](XSQLUtil.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
