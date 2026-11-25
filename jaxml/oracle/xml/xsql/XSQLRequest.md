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

- **[Prev Class](XSQLParserHelper.md)**
- **[Next Class](XSQLRequestObjectListener.md)**

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

## **Class XSQLRequest**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLRequest**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XSQLRequest
      extends java.lang.Object

  **Programmatically process a request for an XSQL Page.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSQLRequest``(java.lang.String url)`<br>Create a Request for an XSQL Page                                                                                                                                |
    | `XSQLRequest``(java.lang.String url, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Create a Request for an XSQL Page, relative to current request                                                    |
    | `XSQLRequest``(java.net.URL url)`<br>Create a Request for an XSQL Page                                                                                                                                    |
    | `XSQLRequest``(java.net.URL url, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`<br>Create a Request for an XSQL Page                                                                                     |
    | `XSQLRequest``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` page, java.net.URL baseURL)`<br>Create a Request for an XSQL Page                                                                           |
    | `XSQLRequest``(`[`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md)` fact, java.lang.String url)`<br>Create a Request for an XSQL Page using a custom connection manager factory            |
    | `XSQLRequest``(`[`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md)` fact, java.net.URL url)`<br>Create a Request for an XSQL Page with a custom connection manager factory.                |
    | `XSQLRequest``(`[`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md)` fact, `[`XMLDocument`](../parser/v2/XMLDocument.md)` page, java.net.URL baseURL)`<br>Create a Request for an XSQL Page |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                        |
    |------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`                      | `getPageProcessorVersion``()`<br>Return the version number of the XSQL Page Processor                                                                                                         |
    | `static java.lang.String`                      | `getReleaseVersion``()`                                                                                                                                                                       |
    | `void`                                         | `process``()`<br>Process the request, writing output/errors to System.out/System.err                                                                                                          |
    | `void`                                         | `process``(java.util.Dictionary params)`<br>Process the request, writing output/errors to System.out/System.err                                                                               |
    | `void`                                         | `process``(java.util.Dictionary params, java.io.OutputStream out, java.io.PrintWriter err)`<br>Process the request, writing output to OutputStream and errors to PrintWriter                  |
    | `void`                                         | `process``(java.util.Dictionary params, java.io.PrintWriter out, java.io.PrintWriter err)`<br>Process the request, writing output/errors to respective PrintWriters                           |
    | `void`                                         | `process``(java.io.OutputStream out, java.io.PrintWriter err)`<br>Process the request, writing output to OutputStream and error to a PrintWriters                                             |
    | `void`                                         | `process``(java.io.PrintWriter out, java.io.PrintWriter err)`<br>Process the request, writing output/errors to respective PrintWriters                                                        |
    | [`Document`](../../../org/w3c/dom/Document.md) | `processToXML``()`<br>Process the request, writing output/errors to System.out/System.err                                                                                                     |
    | [`Document`](../../../org/w3c/dom/Document.md) | `processToXML``(java.util.Dictionary params)`<br>Process the request, writing output/errors to System.out/System.err                                                                          |
    | [`Document`](../../../org/w3c/dom/Document.md) | `processToXML``(java.util.Dictionary params, java.io.PrintWriter err)`<br>Process the request, writing output/errors to respective PrintWriters                                               |
    | [`Document`](../../../org/w3c/dom/Document.md) | `processToXML``(java.io.PrintWriter err)`<br>Process the request, writing errors to respective PrintWriters                                                                                   |
    | `void`                                         | `setPostedDocument``(`[`Document`](../../../org/w3c/dom/Document.md)` postedDoc)`<br>Programmatically set an XML Document to be treated the same as if it were posted as part of the request. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLRequest

          public XSQLRequest(XMLDocument page,
                             java.net.URL baseURL)

      Create a Request for an XSQL Page
      Parameters:
      `page` - XML Document representing XSQL page template

      `baseURL` - Base URL for resolving relative URI's in page.

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(XSQLConnectionManagerFactory fact,
                             XMLDocument page,
                             java.net.URL baseURL)

      Create a Request for an XSQL Page
      Parameters:
      `fact` - Instance of XSQLConnectionManagerFactory

      `page` - XML Document representing XSQL page template

      `baseURL` - Base URL for resolving relative URI's in page.

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(java.lang.String url)
                      throws java.net.MalformedURLException

      Create a Request for an XSQL Page
      Parameters:
      `url` - String representation of an URL to an XSQL Page

      Throws:
      `java.net.MalformedURLException`

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(XSQLConnectionManagerFactory fact,
                             java.lang.String url)
                      throws java.net.MalformedURLException

      Create a Request for an XSQL Page using a custom connection manager factory
      Parameters:
      `fact` - Instance of XSQLConnectionManagerFactory

      `url` - String representation of an URL to an XSQL Page

      Throws:
      `java.net.MalformedURLException`

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(java.net.URL url,
                             XSQLPageRequest env)

      Create a Request for an XSQL Page
      Parameters:
      `url` - URL to an XSQL Page

      `env` - Calling XSQLPageRequest environment

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(java.lang.String url,
                             XSQLPageRequest env)
                      throws java.net.MalformedURLException

      Create a Request for an XSQL Page, relative to current request
      Parameters:
      `url` - String representation of an URL to an XSQL Page

      `env` - Calling XSQLPageRequest environment

      Throws:
      `java.net.MalformedURLException`

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(java.net.URL url)

      Create a Request for an XSQL Page
      Parameters:
      `url` - URL to an XSQL Page

    <!-- -->

    - #### XSQLRequest

          public XSQLRequest(XSQLConnectionManagerFactory fact,
                             java.net.URL url)

      Create a Request for an XSQL Page with a custom connection manager factory.
      Parameters:
      `fact` - Instance of XSQLConnectionManagerFactory

      `url` - URL to an XSQL Page

  <!-- -->

  - ### Method Detail

    - #### getPageProcessorVersion

          public static java.lang.String getPageProcessorVersion()

      Return the version number of the XSQL Page Processor

    <!-- -->

    - #### setPostedDocument

          public void setPostedDocument(Document postedDoc)

      Programmatically set an XML Document to be treated the same as if it were posted as part of the request.
      Parameters:
      `postedDoc` - DOM Document

    <!-- -->

    - #### process

          public void process(java.io.OutputStream out,
                              java.io.PrintWriter err)

      Process the request, writing output to OutputStream and error to a PrintWriters
      Parameters:
      `out` - OutputStream to use to write the resulting page results

      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### process

          public void process(java.io.PrintWriter out,
                              java.io.PrintWriter err)

      Process the request, writing output/errors to respective PrintWriters
      Parameters:
      `out` - PrintWriter to use to write the resulting page results

      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### process

          public void process(java.util.Dictionary params,
                              java.io.OutputStream out,
                              java.io.PrintWriter err)

      Process the request, writing output to OutputStream and errors to PrintWriter
      Parameters:
      `params` - Dictionary (e.g. Hashtable) with XSQL Page parameters

      `out` - OutputStream to use to write the resulting page results

      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### process

          public void process(java.util.Dictionary params,
                              java.io.PrintWriter out,
                              java.io.PrintWriter err)

      Process the request, writing output/errors to respective PrintWriters
      Parameters:
      `params` - Dictionary (e.g. Hashtable) with XSQL Page parameters

      `out` - PrintWriter to use to write the resulting page results

      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### process

          public void process(java.util.Dictionary params)

      Process the request, writing output/errors to System.out/System.err
      Parameters:
      `params` - Dictionary (e.g. Hashtable) with XSQL Page parameters

    <!-- -->

    - #### process

          public void process()

      Process the request, writing output/errors to System.out/System.err

    <!-- -->

    - #### processToXML

          public Document processToXML(java.io.PrintWriter err)

      Process the request, writing errors to respective PrintWriters
      Parameters:
      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### processToXML

          public Document processToXML(java.util.Dictionary params,
                                       java.io.PrintWriter err)

      Process the request, writing output/errors to respective PrintWriters
      Parameters:
      `params` - Dictionary (e.g. Hashtable) with XSQL Page parameters

      `err` - PrintWriter to use to write the resulting page errors

    <!-- -->

    - #### processToXML

          public Document processToXML(java.util.Dictionary params)

      Process the request, writing output/errors to System.out/System.err
      Parameters:
      `params` - Dictionary (e.g. Hashtable) with XSQL Page parameters

    <!-- -->

    - #### processToXML

          public Document processToXML()

      Process the request, writing output/errors to System.out/System.err

    <!-- -->

    - #### getReleaseVersion

          public static java.lang.String getReleaseVersion()

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

- **[Prev Class](XSQLParserHelper.md)**
- **[Next Class](XSQLRequestObjectListener.md)**

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
