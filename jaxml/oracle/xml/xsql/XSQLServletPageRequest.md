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

- **[Prev Class](XSQLServlet.md)**
- **[Next Class](XSQLStylesheetProcessor.md)**

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

## **Class XSQLServletPageRequest**

- **java.lang.Object**

- - **[oracle.xml.xsql.XSQLPageRequestImpl](XSQLPageRequestImpl.md)**

  - - **oracle.xml.xsql.XSQLServletPageRequest**

<!-- -->

- **All Implemented Interfaces:**
  **[XSQLPageRequest](XSQLPageRequest.md)**

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLServletPageRequest
      extends XSQLPageRequestImpl

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                             |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSQLServletPageRequest``(javax.servlet.http.HttpServletRequest req, javax.servlet.http.HttpServletResponse resp, javax.servlet.ServletConfig config)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                             |
    |------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XSQLPageRequest`](XSQLPageRequest.md)        | `createNestedRequest``(java.lang.String baseuri, java.net.URL pageurl, java.util.Dictionary params, java.io.PrintWriter overriddenWriter, java.io.OutputStream overriddenOutputStream)`<br>Returns an instance of a nested Request |
    | `java.lang.String`                             | `getCookie``(java.lang.String name)`                                                                                                                                                                                               |
    | `javax.servlet.http.HttpServletRequest`        | `getHttpServletRequest``()`<br>Get the HttpServletRequest that initiated this XSQL Page Request.                                                                                                                                   |
    | `javax.servlet.http.HttpServletResponse`       | `getHttpServletResponse``()`<br>Get the HttpServletResponse that is associated with this XSQL Page Request                                                                                                                         |
    | `java.lang.String`                             | `getParameter``(java.lang.String name)`<br>Use HTTP Parameters as the source of parameters instead                                                                                                                                 |
    | `java.lang.String[]`                           | `getParameterValues``(java.lang.String name)`<br>Returns an array of values for the requested parameter                                                                                                                            |
    | [`Document`](../../../org/w3c/dom/Document.md) | `getPostedDocument``()`<br>Returns the content of Posted XML for this request as an XML Document                                                                                                                                   |
    | [`Document`](../../../org/w3c/dom/Document.md) | `getRequestParamsAsXMLDocument``()`<br>Returns the content of a Request parameters as an XML Document                                                                                                                              |
    | `java.lang.String`                             | `getRequestType``()`<br>Returns a string identifying the type of page request being made.                                                                                                                                          |
    | `javax.servlet.ServletConfig`                  | `getServletConfig``()`<br>Get the ServletConfig associated with servlet processing this request.                                                                                                                                   |
    | `javax.servlet.ServletContext`                 | `getServletContext``()`<br>Get the ServletContext associated with servlet processing this request                                                                                                                                  |
    | `java.lang.String`                             | `getUserAgent``()`<br>Returns a String identifier of the requesting program                                                                                                                                                        |
    | `void`                                         | `setContentType``(java.lang.String mimetype)`<br>Sets the content type of the resulting page                                                                                                                                       |
    | `void`                                         | `setCookie``(java.lang.String name, java.lang.String value, java.lang.String maxage, java.lang.String domain, java.lang.String path, boolean immediate)`                                                                           |
    | `void`                                         | `setPageEncoding``(java.lang.String enc)`<br>Associates an XSQL Page with the request                                                                                                                                              |
    | `java.lang.String`                             | `translateURL``(java.lang.String path)`<br>Returns a string representing an absolute URL resolved relative to the base URI for this request.                                                                                       |
    | `boolean`                                      | `useHTMLErrors``()`<br>Returns true if HTML-formatted error messages are desired for this request                                                                                                                                  |

    - ### Methods inherited from class oracle.xml.xsql.[XSQLPageRequestImpl](XSQLPageRequestImpl.md)

      [`getBaseURI`](XSQLPageRequestImpl.md)`, `[`getConnectionManagerFactory`](XSQLPageRequestImpl.md)`, `[`getConnectionName`](XSQLPageRequestImpl.md)`, `[`getErrorWriter`](XSQLPageRequestImpl.md)`, `[`getJDBCConnection`](XSQLPageRequestImpl.md)`, `[`getOutputStream`](XSQLPageRequestImpl.md)`, `[`getPageEncoding`](XSQLPageRequestImpl.md)`, `[`getRequestObject`](XSQLPageRequestImpl.md)`, `[`getSourceDocumentURI`](XSQLPageRequestImpl.md)`, `[`getStylesheetParameter`](XSQLPageRequestImpl.md)`, `[`getStylesheetParameters`](XSQLPageRequestImpl.md)`, `[`getStylesheetURI`](XSQLPageRequestImpl.md)`, `[`getWriter`](XSQLPageRequestImpl.md)`, `[`getXSQLConnection`](XSQLPageRequestImpl.md)`, `[`getXSQLPage`](XSQLPageRequestImpl.md)`, `[`isErrorSignalled`](XSQLPageRequestImpl.md)`, `[`isIncludedRequest`](XSQLPageRequestImpl.md)`, `[`isOracleDriver`](XSQLPageRequestImpl.md)`, `[`isUseOutputStream`](XSQLPageRequestImpl.md)`, `[`printedErrorHeader`](XSQLPageRequestImpl.md)`, `[`requestProcessed`](XSQLPageRequestImpl.md)`, `[`setConnectionName`](XSQLPageRequestImpl.md)`, `[`setErrorHandlerClass`](XSQLPageRequestImpl.md)`, `[`setIncludingRequest`](XSQLPageRequestImpl.md)`, `[`setPageParam`](XSQLPageRequestImpl.md)`, `[`setPageParam`](XSQLPageRequestImpl.md)`, `[`setPostedDocument`](XSQLPageRequestImpl.md)`, `[`setPrintedErrorHeader`](XSQLPageRequestImpl.md)`, `[`setRequestObject`](XSQLPageRequestImpl.md)`, `[`setStylesheetParameter`](XSQLPageRequestImpl.md)`, `[`setStylesheetURI`](XSQLPageRequestImpl.md)`, `[`signalError`](XSQLPageRequestImpl.md)`, `[`signalError`](XSQLPageRequestImpl.md)`, `[`useConnectionPooling`](XSQLPageRequestImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLServletPageRequest

          public XSQLServletPageRequest(javax.servlet.http.HttpServletRequest req,
                                        javax.servlet.http.HttpServletResponse resp,
                                        javax.servlet.ServletConfig config)

  <!-- -->

  - ### Method Detail

    - #### getParameter

          public java.lang.String getParameter(java.lang.String name)

      Use HTTP Parameters as the source of parameters instead
      Specified by:
      [`getParameter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`getParameter`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getParameterValues

          public java.lang.String[] getParameterValues(java.lang.String name)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns an array of values for the requested parameter
      Specified by:
      [`getParameterValues`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`getParameterValues`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getUserAgent

          public java.lang.String getUserAgent()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a String identifier of the requesting program
      Specified by:
      [`getUserAgent`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`getUserAgent`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### setContentType

          public void setContentType(java.lang.String mimetype)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets the content type of the resulting page
      Specified by:
      [`setContentType`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`setContentType`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### useHTMLErrors

          public boolean useHTMLErrors()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns true if HTML-formatted error messages are desired for this request
      Specified by:
      [`useHTMLErrors`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`useHTMLErrors`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### translateURL

          public java.lang.String translateURL(java.lang.String path)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a string representing an absolute URL resolved relative to the base URI for this request.
      Specified by:
      [`translateURL`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`translateURL`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### getRequestType

          public java.lang.String getRequestType()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a string identifying the type of page request being made.

    <!-- -->

    - #### getRequestParamsAsXMLDocument

          public Document getRequestParamsAsXMLDocument()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the content of a Request parameters as an XML Document
      Specified by:
      [`getRequestParamsAsXMLDocument`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`getRequestParamsAsXMLDocument`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### getPostedDocument

          public Document getPostedDocument()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the content of Posted XML for this request as an XML Document
      Specified by:
      [`getPostedDocument`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`getPostedDocument`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### getHttpServletRequest

          public javax.servlet.http.HttpServletRequest getHttpServletRequest()

      Get the HttpServletRequest that initiated this XSQL Page Request.

    <!-- -->

    - #### getHttpServletResponse

          public javax.servlet.http.HttpServletResponse getHttpServletResponse()

      Get the HttpServletResponse that is associated with this XSQL Page Request

    <!-- -->

    - #### getServletContext

          public javax.servlet.ServletContext getServletContext()

      Get the ServletContext associated with servlet processing this request

    <!-- -->

    - #### getServletConfig

          public javax.servlet.ServletConfig getServletConfig()

      Get the ServletConfig associated with servlet processing this request.

    <!-- -->

    - #### setPageEncoding

          public void setPageEncoding(java.lang.String enc)

      Description copied from class: [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)
      Associates an XSQL Page with the request
      Specified by:
      [`setPageEncoding`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Overrides:
      [`setPageEncoding`](XSQLPageRequestImpl.md) in class [`XSQLPageRequestImpl`](XSQLPageRequestImpl.md)

    <!-- -->

    - #### setCookie

          public void setCookie(java.lang.String name,
                                java.lang.String value,
                                java.lang.String maxage,
                                java.lang.String domain,
                                java.lang.String path,
                                boolean immediate)

    <!-- -->

    - #### getCookie

          public java.lang.String getCookie(java.lang.String name)

    <!-- -->

    - #### createNestedRequest

          public XSQLPageRequest createNestedRequest(java.lang.String baseuri,
                                                     java.net.URL pageurl,
                                                     java.util.Dictionary params,
                                                     java.io.PrintWriter overriddenWriter,
                                                     java.io.OutputStream overriddenOutputStream)

      Returns an instance of a nested Request

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

- **[Prev Class](XSQLServlet.md)**
- **[Next Class](XSQLStylesheetProcessor.md)**

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
