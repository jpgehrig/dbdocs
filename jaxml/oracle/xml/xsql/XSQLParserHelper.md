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

- **[Prev Class](XSQLPageRequestImpl.md)**
- **[Next Class](XSQLRequest.md)**

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

## **Class XSQLParserHelper**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLParserHelper**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLParserHelper
      extends java.lang.Object

  **Common XML Parsing Routines**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XSQLParserHelper``()`      |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                    |
    |---------------------------------------------------------|-------------------------------------------------------------------------------------------|
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `newDocument``()`                                                                         |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parse``(java.io.InputStream is, java.net.URL baseUrl, java.io.PrintWriter errorWriter)`  |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parse``(java.io.Reader r, java.io.PrintWriter errorWriter)`                              |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parse``(java.io.Reader r, java.net.URL baseUrl, java.io.PrintWriter errorWriter)`        |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parse``(java.net.URL url, java.io.PrintWriter errorWriter)`                              |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parseFromString``(java.lang.StringBuffer xmlString, java.io.PrintWriter errorWriter)`    |
    | `static `[`Document`](../../../org/w3c/dom/Document.md) | `parseFromString``(java.lang.String xmlString, java.io.PrintWriter errorWriter)`          |
    | `static void`                                           | `print``(`[`Document`](../../../org/w3c/dom/Document.md)` d, java.io.OutputStream out)`   |
    | `static void`                                           | `print``(`[`Document`](../../../org/w3c/dom/Document.md)` d, java.io.PrintWriter out)`    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLParserHelper

          public XSQLParserHelper()

  <!-- -->

  - ### Method Detail

    - #### parseFromString

          public static Document parseFromString(java.lang.String xmlString,
                                                 java.io.PrintWriter errorWriter)
                                          throws java.net.MalformedURLException,
                                                 java.io.IOException,
                                                 SAXParseException,
                                                 SAXException

      Throws:
      `java.net.MalformedURLException`

      `java.io.IOException`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### parseFromString

          public static Document parseFromString(java.lang.StringBuffer xmlString,
                                                 java.io.PrintWriter errorWriter)
                                          throws java.net.MalformedURLException,
                                                 java.io.IOException,
                                                 SAXParseException,
                                                 SAXException

      Throws:
      `java.net.MalformedURLException`

      `java.io.IOException`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### parse

          public static Document parse(java.net.URL url,
                                       java.io.PrintWriter errorWriter)
                                throws java.io.IOException,
                                       SAXParseException,
                                       SAXException

      Throws:
      `java.io.IOException`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### parse

          public static Document parse(java.io.Reader r,
                                       java.net.URL baseUrl,
                                       java.io.PrintWriter errorWriter)
                                throws java.io.IOException,
                                       SAXParseException,
                                       SAXException

      Throws:
      `java.io.IOException`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### parse

          public static Document parse(java.io.InputStream is,
                                       java.net.URL baseUrl,
                                       java.io.PrintWriter errorWriter)
                                throws java.io.IOException,
                                       SAXParseException,
                                       SAXException

      Throws:
      `java.io.IOException`

      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### parse

          public static Document parse(java.io.Reader r,
                                       java.io.PrintWriter errorWriter)
                                throws SAXParseException,
                                       SAXException

      Throws:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### newDocument

          public static Document newDocument()

    <!-- -->

    - #### print

          public static void print(Document d,
                                   java.io.OutputStream out)

    <!-- -->

    - #### print

          public static void print(Document d,
                                   java.io.PrintWriter out)

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

- **[Prev Class](XSQLPageRequestImpl.md)**
- **[Next Class](XSQLRequest.md)**

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
