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

- **[Prev Class](XSQLStylesheetProcessor.md)**
- **Next Class**

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

## **Class XSQLUtil**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLUtil**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLUtil
      extends java.lang.Object

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `FILEURLPREF`         |
    | `static java.lang.String` | `JARPREF`             |
    | `static java.lang.String` | `JAVASCHEME`          |
    | `static java.lang.String` | `NULL`                |
    | `static java.lang.String` | `ZIPPREF`             |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XSQLUtil``()`              |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                              | Method and Description                                                                         |
    |----------------------------------------------------------------|------------------------------------------------------------------------------------------------|
    | `static java.lang.String`                                      | `arrayParamName``(java.lang.String name)`                                                      |
    | `static java.lang.String`                                      | `baseUriOf``(java.lang.String path)`                                                           |
    | `static java.lang.Class`                                       | `classForName``(java.lang.String classname)`                                                   |
    | `static java.lang.String`                                      | `commaSeparatedListOfValues``(java.lang.String[] values, boolean quoted)`                      |
    | `static `[`XSQLDocumentSerializer`](XSQLDocumentSerializer.md) | `createSerializer``(java.lang.String name, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`     |
    | `static `[`XMLDocument`](../parser/v2/XMLDocument.md)          | `DictionaryOfParamsAsXMLDocument``(java.util.Dictionary dict)`                                 |
    | `static `[`XSQLErrorHandler`](XSQLErrorHandler.md)             | `getDefaultErrorHandler``()`                                                                   |
    | `static `[`XSQLErrorHandler`](XSQLErrorHandler.md)             | `getErrorHandler``()`                                                                          |
    | `static boolean`                                               | `isAbsoluteURL``(java.lang.String url)`                                                        |
    | `static boolean`                                               | `isArrayParamName``(java.lang.String name)`                                                    |
    | `static java.lang.String`                                      | `quoteLessThanSigns``(java.lang.String msg)`                                                   |
    | `static java.lang.String`                                      | `relativize``(java.lang.String url, java.lang.String baseUrl)`                                 |
    | `static java.lang.String`                                      | `resolveParams``(java.lang.String value, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`       |
    | `static java.lang.String`                                      | `safeURLAsString``(java.net.URL u)`                                                            |
    | `static `[`NodeList`](../../../org/w3c/dom/NodeList.md)        | `select``(`[`Document`](../../../org/w3c/dom/Document.md)` d, java.lang.String pattern)`       |
    | `static `[`NodeList`](../../../org/w3c/dom/NodeList.md)        | `select``(`[`Element`](../../../org/w3c/dom/Element.md)` n, java.lang.String pattern)`         |
    | `static `[`NodeList`](../../../org/w3c/dom/NodeList.md)        | `select``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` d, java.lang.String pattern)`         |
    | `static `[`NodeList`](../../../org/w3c/dom/NodeList.md)        | `select``(`[`XMLElement`](../parser/v2/XMLElement.md)` n, java.lang.String pattern)`           |
    | `static `[`Node`](../../../org/w3c/dom/Node.md)                | `selectFirst``(`[`Document`](../../../org/w3c/dom/Document.md)` d, java.lang.String pattern)`  |
    | `static `[`Node`](../../../org/w3c/dom/Node.md)                | `selectFirst``(`[`Element`](../../../org/w3c/dom/Element.md)` n, java.lang.String pattern)`    |
    | `static `[`Node`](../../../org/w3c/dom/Node.md)                | `selectFirst``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` d, java.lang.String pattern)`    |
    | `static `[`Node`](../../../org/w3c/dom/Node.md)                | `selectFirst``(`[`XMLElement`](../parser/v2/XMLElement.md)` n, java.lang.String pattern)`      |
    | `static java.lang.String`                                      | `stringParamValue``(java.lang.Object val)`                                                     |
    | `static java.lang.String[]`                                    | `stringParamValues``(java.lang.Object val)`                                                    |
    | `static long`                                                  | `timestampOf``(java.lang.String filename)`                                                     |
    | `static java.lang.String[]`                                    | `tokenizeIntoArray``(java.lang.String s)`                                                      |
    | `static java.lang.String[]`                                    | `tokenizeIntoArrayUsingCommasIfPresent``(java.lang.String s)`                                  |
    | `static java.lang.String`                                      | `translate``(java.lang.String u, java.lang.String path)`                                       |
    | `static java.lang.String`                                      | `translate``(java.net.URL u, java.lang.String path)`                                           |
    | `static boolean`                                               | `untrustedAbsoluteStylesheetURL``(java.lang.String url)`                                       |
    | `static java.lang.String`                                      | `valueOf``(`[`Element`](../../../org/w3c/dom/Element.md)` n, java.lang.String pattern)`        |
    | `static java.lang.String`                                      | `valueOf``(`[`Node`](../../../org/w3c/dom/Node.md)` n, java.lang.String pattern)`              |
    | `static java.lang.String`                                      | `valueOf``(`[`XMLElement`](../parser/v2/XMLElement.md)` n, java.lang.String pattern)`          |
    | `static java.lang.String`                                      | `valueOf``(`[`XMLNode`](../parser/v2/XMLNode.md)` n, java.lang.String pattern)`                |
    | `static java.lang.String`                                      | `XL``(java.lang.String s, java.lang.String enc)`                                               |
    | `static java.lang.String[]`                                    | `XLArr``(java.lang.String[] s, java.lang.String enc)`                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### JARPREF

          public static final java.lang.String JARPREF

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ZIPPREF

          public static final java.lang.String ZIPPREF

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FILEURLPREF

          public static final java.lang.String FILEURLPREF

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NULL

          public static final java.lang.String NULL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JAVASCHEME

          public static final java.lang.String JAVASCHEME

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XSQLUtil

          public XSQLUtil()

  <!-- -->

  - ### Method Detail

    - #### select

          public static NodeList select(Document d,
                                        java.lang.String pattern)

    <!-- -->

    - #### select

          public static NodeList select(XMLDocument d,
                                        java.lang.String pattern)

    <!-- -->

    - #### select

          public static NodeList select(Element n,
                                        java.lang.String pattern)

    <!-- -->

    - #### select

          public static NodeList select(XMLElement n,
                                        java.lang.String pattern)

    <!-- -->

    - #### selectFirst

          public static Node selectFirst(Document d,
                                         java.lang.String pattern)

    <!-- -->

    - #### selectFirst

          public static Node selectFirst(XMLDocument d,
                                         java.lang.String pattern)

    <!-- -->

    - #### selectFirst

          public static Node selectFirst(Element n,
                                         java.lang.String pattern)

    <!-- -->

    - #### selectFirst

          public static Node selectFirst(XMLElement n,
                                         java.lang.String pattern)

    <!-- -->

    - #### valueOf

          public static java.lang.String valueOf(Element n,
                                                 java.lang.String pattern)

    <!-- -->

    - #### valueOf

          public static java.lang.String valueOf(Node n,
                                                 java.lang.String pattern)

    <!-- -->

    - #### valueOf

          public static java.lang.String valueOf(XMLElement n,
                                                 java.lang.String pattern)

    <!-- -->

    - #### valueOf

          public static java.lang.String valueOf(XMLNode n,
                                                 java.lang.String pattern)

    <!-- -->

    - #### DictionaryOfParamsAsXMLDocument

          public static XMLDocument DictionaryOfParamsAsXMLDocument(java.util.Dictionary dict)

    <!-- -->

    - #### XL

          public static java.lang.String XL(java.lang.String s,
                                            java.lang.String enc)

    <!-- -->

    - #### XLArr

          public static java.lang.String[] XLArr(java.lang.String[] s,
                                                 java.lang.String enc)

    <!-- -->

    - #### safeURLAsString

          public static java.lang.String safeURLAsString(java.net.URL u)

    <!-- -->

    - #### translate

          public static java.lang.String translate(java.lang.String u,
                                                   java.lang.String path)

    <!-- -->

    - #### translate

          public static java.lang.String translate(java.net.URL u,
                                                   java.lang.String path)
                                            throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stringParamValue

          public static java.lang.String stringParamValue(java.lang.Object val)

    <!-- -->

    - #### stringParamValues

          public static java.lang.String[] stringParamValues(java.lang.Object val)

    <!-- -->

    - #### resolveParams

          public static java.lang.String resolveParams(java.lang.String value,
                                                       XSQLPageRequest env)

    <!-- -->

    - #### tokenizeIntoArray

          public static java.lang.String[] tokenizeIntoArray(java.lang.String s)

    <!-- -->

    - #### tokenizeIntoArrayUsingCommasIfPresent

          public static java.lang.String[] tokenizeIntoArrayUsingCommasIfPresent(java.lang.String s)

    <!-- -->

    - #### commaSeparatedListOfValues

          public static java.lang.String commaSeparatedListOfValues(java.lang.String[] values,
                                                                    boolean quoted)

    <!-- -->

    - #### createSerializer

          public static XSQLDocumentSerializer createSerializer(java.lang.String name,
                                                                XSQLPageRequest env)

    <!-- -->

    - #### isAbsoluteURL

          public static boolean isAbsoluteURL(java.lang.String url)

    <!-- -->

    - #### untrustedAbsoluteStylesheetURL

          public static boolean untrustedAbsoluteStylesheetURL(java.lang.String url)

    <!-- -->

    - #### relativize

          public static java.lang.String relativize(java.lang.String url,
                                                    java.lang.String baseUrl)

    <!-- -->

    - #### baseUriOf

          public static java.lang.String baseUriOf(java.lang.String path)

    <!-- -->

    - #### classForName

          public static java.lang.Class classForName(java.lang.String classname)
                                              throws java.lang.ClassNotFoundException

      Throws:
      `java.lang.ClassNotFoundException`

    <!-- -->

    - #### getErrorHandler

          public static XSQLErrorHandler getErrorHandler()

    <!-- -->

    - #### getDefaultErrorHandler

          public static XSQLErrorHandler getDefaultErrorHandler()

    <!-- -->

    - #### isArrayParamName

          public static boolean isArrayParamName(java.lang.String name)

    <!-- -->

    - #### arrayParamName

          public static java.lang.String arrayParamName(java.lang.String name)

    <!-- -->

    - #### timestampOf

          public static long timestampOf(java.lang.String filename)

    <!-- -->

    - #### quoteLessThanSigns

          public static java.lang.String quoteLessThanSigns(java.lang.String msg)

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

- **[Prev Class](XSQLStylesheetProcessor.md)**
- **Next Class**

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
