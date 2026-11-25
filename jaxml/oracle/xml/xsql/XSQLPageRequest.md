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

- **[Prev Class](XSQLNamedConnectionManager.md)**
- **[Next Class](XSQLPageRequestImpl.md)**

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

## **Interface XSQLPageRequest**

- **All Known Implementing Classes:**
  **[XSQLPageRequestImpl](XSQLPageRequestImpl.md), [XSQLServletPageRequest](XSQLServletPageRequest.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLPageRequest

  **Interface representing a request for an XSQL Page**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                             |
    |-------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSQLPageRequest`                                                 | `createNestedRequest``(java.lang.String baseuri, java.net.URL pageurl, java.util.Dictionary params, java.io.PrintWriter overriddenWriter, java.io.OutputStream overriddenOutputStream)`<br>Returns an instance of a nested Request |
    | `java.lang.String`                                                | `getBaseURI``()`<br>Returns a String representation of the requested document's Base URI                                                                                                                                           |
    | [`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md) | `getConnectionManagerFactory``()`<br>Returns the instance of the connection manager factory to use for this request                                                                                                                |
    | `java.lang.String`                                                | `getConnectionName``()`<br>Returns the name of the connection being used for this request May be null if no connection set/in-use.                                                                                                 |
    | `java.io.PrintWriter`                                             | `getErrorWriter``()`<br>Returns a PrintWriter to print out errors processing this request                                                                                                                                          |
    | `java.sql.Connection`                                             | `getJDBCConnection``()`<br>Gets the JDBC connection being used for this request (can be null)                                                                                                                                      |
    | `java.io.OutputStream`                                            | `getOutputStream``()`<br>Returns an OutputStream used for writing out the results of a page request                                                                                                                                |
    | `java.lang.String`                                                | `getPageEncoding``()`<br>Returns encoding of source XSQL Page associated with this request                                                                                                                                         |
    | `java.lang.String`                                                | `getParameter``(java.lang.String name)`<br>Returns the value of the requested parameter                                                                                                                                            |
    | `java.lang.String[]`                                              | `getParameterValues``(java.lang.String name)`<br>Returns an array of values for the requested parameter                                                                                                                            |
    | [`Document`](../../../org/w3c/dom/Document.md)                    | `getPostedDocument``()`<br>Returns the content of Posted XML for this request as an XML Document                                                                                                                                   |
    | `java.lang.Object`                                                | `getRequestObject``(java.lang.String name)`<br>Gets a request-scope object                                                                                                                                                         |
    | [`Document`](../../../org/w3c/dom/Document.md)                    | `getRequestParamsAsXMLDocument``()`<br>Returns the content of a Request parameters as an XML Document                                                                                                                              |
    | `java.lang.String`                                                | `getRequestType``()`<br>Returns a string identifying the type of page request being made.                                                                                                                                          |
    | `java.lang.String`                                                | `getSourceDocumentURI``()`<br>Returns a String representation of the requested document's URI                                                                                                                                      |
    | `java.lang.String`                                                | `getStylesheetParameter``(java.lang.String name)`<br>Gets a stylesheet parameter by name                                                                                                                                           |
    | `java.util.Enumeration`                                           | `getStylesheetParameters``()`<br>Gets an enumeration of stylesheet parameter names                                                                                                                                                 |
    | `java.lang.String`                                                | `getStylesheetURI``()`<br>Returns the URI of the stylesheet to be used to process the result.                                                                                                                                      |
    | `java.lang.String`                                                | `getUserAgent``()`<br>Returns a String identifier of the requesting program                                                                                                                                                        |
    | `java.io.PrintWriter`                                             | `getWriter``()`<br>Returns a PrintWriter used for writing out the results of a page request                                                                                                                                        |
    | [`XSQLConnection`](XSQLConnection.md)                             | `getXSQLConnection``()`<br>Gets the XSQLConnection Object being used for this request Might be null.                                                                                                                               |
    | `oracle.xml.xsql.XSQLPage`                                        | `getXSQLPage``()`<br>Returns an instance of an XSQLPage representing the current request                                                                                                                                           |
    | `boolean`                                                         | `isErrorSignalled``()`<br>Returns true if processing error has occurred during this request                                                                                                                                        |
    | `boolean`                                                         | `isIncludedRequest``()`<br>Returns true if this request is being included in another.                                                                                                                                              |
    | `boolean`                                                         | `isOracleDriver``()`<br>Returns true if the current connection uses the Oracle JDBC Driver                                                                                                                                         |
    | `boolean`                                                         | `isUseOutputStream``()`<br>Returns true if request is using an output stream instead of a PrintWriter                                                                                                                              |
    | `boolean`                                                         | `printedErrorHeader``()`<br>Returns the state of whether an Error Header has been printed                                                                                                                                          |
    | `void`                                                            | `requestProcessed``()`<br>Allows Page Request to Perform end-of-request processing                                                                                                                                                 |
    | `void`                                                            | `setConnectionName``(java.lang.String connName)`<br>Sets the connection name to use for this request                                                                                                                               |
    | `void`                                                            | `setContentType``(java.lang.String mimetype)`<br>Sets the content type of the resulting page                                                                                                                                       |
    | `void`                                                            | `setErrorHandlerClass``(java.lang.String className)`<br>Sets classname to use to override default ErrorWriter for this request.                                                                                                    |
    | `void`                                                            | `setIncludingRequest``(XSQLPageRequest includingEnv)`<br>Sets the Including Page Request object for this request.                                                                                                                  |
    | `void`                                                            | `setPageEncoding``(java.lang.String enc)`<br>Sets encoding of source XSQL page associated with this request.                                                                                                                       |
    | `void`                                                            | `setPageParam``(java.lang.String name, java.lang.String value)`<br>Sets a dynamic page parameter value.                                                                                                                            |
    | `void`                                                            | `setPageParam``(java.lang.String name, java.lang.String[] value)`<br>Sets a dynamic page parameter value to a string array                                                                                                         |
    | `void`                                                            | `setPostedDocument``(`[`Document`](../../../org/w3c/dom/Document.md)` doc)`<br>Allows programmatic setting of the Posted Document                                                                                                  |
    | `void`                                                            | `setPrintedErrorHeader``(boolean yes)`<br>Sets whether an Error Header has been printed                                                                                                                                            |
    | `void`                                                            | `setRequestObject``(java.lang.String name, java.lang.Object obj)`<br>Sets a request-scope object                                                                                                                                   |
    | `void`                                                            | `setStylesheetParameter``(java.lang.String name, java.lang.String value)`<br>Sets the value of a parameter to be passed to the associated stylesheet                                                                               |
    | `void`                                                            | `setStylesheetURI``(java.lang.String uri)`<br>Sets the URI of the stylesheet to be used to process the result.                                                                                                                     |
    | `void`                                                            | `signalError``(int errorCode, java.lang.String[] errorMessageArgs, java.lang.Object[] supplementalErrorInfo)`<br>Signals a processing error for this request                                                                       |
    | `void`                                                            | `signalError``(java.lang.String message)`<br>Signals a processing error for this request                                                                                                                                           |
    | `java.lang.String`                                                | `translateURL``(java.lang.String url)`<br>Returns a string representing an absolute URL resolved relative to the base URI for this request.                                                                                        |
    | `boolean`                                                         | `useConnectionPooling``()`<br>Returns true if connection pooling is desired for this request                                                                                                                                       |
    | `boolean`                                                         | `useHTMLErrors``()`<br>Returns true if HTML-formatted error messages are desired for this request                                                                                                                                  |

<!-- -->

- - ### Method Detail

    - #### printedErrorHeader

          boolean printedErrorHeader()

      Returns the state of whether an Error Header has been printed

    <!-- -->

    - #### setPrintedErrorHeader

          void setPrintedErrorHeader(boolean yes)

      Sets whether an Error Header has been printed

    <!-- -->

    - #### getParameter

          java.lang.String getParameter(java.lang.String name)

      Returns the value of the requested parameter
      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getParameterValues

          java.lang.String[] getParameterValues(java.lang.String name)

      Returns an array of values for the requested parameter
      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getSourceDocumentURI

          java.lang.String getSourceDocumentURI()

      Returns a String representation of the requested document's URI

    <!-- -->

    - #### getBaseURI

          java.lang.String getBaseURI()

      Returns a String representation of the requested document's Base URI

    <!-- -->

    - #### getWriter

          java.io.PrintWriter getWriter()

      Returns a PrintWriter used for writing out the results of a page request

    <!-- -->

    - #### useConnectionPooling

          boolean useConnectionPooling()

      Returns true if connection pooling is desired for this request

    <!-- -->

    - #### useHTMLErrors

          boolean useHTMLErrors()

      Returns true if HTML-formatted error messages are desired for this request

    <!-- -->

    - #### getErrorWriter

          java.io.PrintWriter getErrorWriter()

      Returns a PrintWriter to print out errors processing this request

    <!-- -->

    - #### getUserAgent

          java.lang.String getUserAgent()

      Returns a String identifier of the requesting program

    <!-- -->

    - #### setContentType

          void setContentType(java.lang.String mimetype)

      Sets the content type of the resulting page

    <!-- -->

    - #### translateURL

          java.lang.String translateURL(java.lang.String url)

      Returns a string representing an absolute URL resolved relative to the base URI for this request.

    <!-- -->

    - #### getRequestType

          java.lang.String getRequestType()

      Returns a string identifying the type of page request being made.

    <!-- -->

    - #### setStylesheetURI

          void setStylesheetURI(java.lang.String uri)

      Sets the URI of the stylesheet to be used to process the result.

    <!-- -->

    - #### getStylesheetURI

          java.lang.String getStylesheetURI()

      Returns the URI of the stylesheet to be used to process the result.

    <!-- -->

    - #### getPostedDocument

          Document getPostedDocument()

      Returns the content of Posted XML for this request as an XML Document

    <!-- -->

    - #### setPostedDocument

          void setPostedDocument(Document doc)

      Allows programmatic setting of the Posted Document

    <!-- -->

    - #### getRequestParamsAsXMLDocument

          Document getRequestParamsAsXMLDocument()

      Returns the content of a Request parameters as an XML Document

    <!-- -->

    - #### setPageEncoding

          void setPageEncoding(java.lang.String enc)

      Sets encoding of source XSQL page associated with this request.

    <!-- -->

    - #### getPageEncoding

          java.lang.String getPageEncoding()

      Returns encoding of source XSQL Page associated with this request

    <!-- -->

    - #### setStylesheetParameter

          void setStylesheetParameter(java.lang.String name,
                                      java.lang.String value)

      Sets the value of a parameter to be passed to the associated stylesheet

    <!-- -->

    - #### getStylesheetParameters

          java.util.Enumeration getStylesheetParameters()

      Gets an enumeration of stylesheet parameter names

    <!-- -->

    - #### getStylesheetParameter

          java.lang.String getStylesheetParameter(java.lang.String name)

      Gets a stylesheet parameter by name

    <!-- -->

    - #### setConnectionName

          void setConnectionName(java.lang.String connName)
                          throws java.sql.SQLException

      Sets the connection name to use for this request
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getConnectionName

          java.lang.String getConnectionName()

      Returns the name of the connection being used for this request May be null if no connection set/in-use.

    <!-- -->

    - #### getJDBCConnection

          java.sql.Connection getJDBCConnection()

      Gets the JDBC connection being used for this request (can be null)

    <!-- -->

    - #### requestProcessed

          void requestProcessed()

      Allows Page Request to Perform end-of-request processing

    <!-- -->

    - #### getXSQLConnection

          XSQLConnection getXSQLConnection()

      Gets the XSQLConnection Object being used for this request Might be null.

    <!-- -->

    - #### setIncludingRequest

          void setIncludingRequest(XSQLPageRequest includingEnv)

      Sets the Including Page Request object for this request.

    <!-- -->

    - #### isIncludedRequest

          boolean isIncludedRequest()

      Returns true if this request is being included in another.

    <!-- -->

    - #### isOracleDriver

          boolean isOracleDriver()

      Returns true if the current connection uses the Oracle JDBC Driver

    <!-- -->

    - #### setPageParam

          void setPageParam(java.lang.String name,
                            java.lang.String value)

      Sets a dynamic page parameter value.

    <!-- -->

    - #### setPageParam

          void setPageParam(java.lang.String name,
                            java.lang.String[] value)

      Sets a dynamic page parameter value to a string array

    <!-- -->

    - #### setRequestObject

          void setRequestObject(java.lang.String name,
                                java.lang.Object obj)

      Sets a request-scope object

    <!-- -->

    - #### getRequestObject

          java.lang.Object getRequestObject(java.lang.String name)

      Gets a request-scope object

    <!-- -->

    - #### createNestedRequest

          XSQLPageRequest createNestedRequest(java.lang.String baseuri,
                                              java.net.URL pageurl,
                                              java.util.Dictionary params,
                                              java.io.PrintWriter overriddenWriter,
                                              java.io.OutputStream overriddenOutputStream)

      Returns an instance of a nested Request

    <!-- -->

    - #### getOutputStream

          java.io.OutputStream getOutputStream()

      Returns an OutputStream used for writing out the results of a page request

    <!-- -->

    - #### getXSQLPage

          oracle.xml.xsql.XSQLPage getXSQLPage()
                                        throws SAXParseException,
                                               java.io.FileNotFoundException

      Returns an instance of an XSQLPage representing the current request
      Throws:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      `java.io.FileNotFoundException`

    <!-- -->

    - #### isUseOutputStream

          boolean isUseOutputStream()

      Returns true if request is using an output stream instead of a PrintWriter

    <!-- -->

    - #### getConnectionManagerFactory

          XSQLConnectionManagerFactory getConnectionManagerFactory()

      Returns the instance of the connection manager factory to use for this request

    <!-- -->

    - #### isErrorSignalled

          boolean isErrorSignalled()

      Returns true if processing error has occurred during this request

    <!-- -->

    - #### signalError

          void signalError(int errorCode,
                           java.lang.String[] errorMessageArgs,
                           java.lang.Object[] supplementalErrorInfo)

      Signals a processing error for this request

    <!-- -->

    - #### signalError

          void signalError(java.lang.String message)

      Signals a processing error for this request

    <!-- -->

    - #### setErrorHandlerClass

          void setErrorHandlerClass(java.lang.String className)
                             throws oracle.xml.xsql.XSQLInitializationException

      Sets classname to use to override default ErrorWriter for this request. Only has an effect if the current request is the topmost request. That is, nested requests cannot change the errorWriter just for the nested scope.
      Throws:
      `oracle.xml.xsql.XSQLInitializationException`

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

- **[Prev Class](XSQLNamedConnectionManager.md)**
- **[Next Class](XSQLPageRequestImpl.md)**

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
