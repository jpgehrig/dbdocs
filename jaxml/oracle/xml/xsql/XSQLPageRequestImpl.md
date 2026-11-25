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

- **[Prev Class](XSQLPageRequest.md)**
- **[Next Class](XSQLParserHelper.md)**

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

## **Class XSQLPageRequestImpl**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLPageRequestImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[XSQLPageRequest](XSQLPageRequest.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XSQLServletPageRequest](XSQLServletPageRequest.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class XSQLPageRequestImpl
      extends java.lang.Object
      implements XSQLPageRequest

  **Base implementation of the XSQLPageRequest interface that case be used to derive new kinds of page request implementations.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                        |
    |------------------------------------------------------------------------------------|
    | `XSQLPageRequestImpl``()`                                                          |
    | `XSQLPageRequestImpl``(java.lang.String pageurl, java.util.Hashtable parameters)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                       |
    |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                                | `getBaseURI``()`<br>Returns a String representation of the requested document's Base URI                                                                     |
    | [`XSQLConnectionManagerFactory`](XSQLConnectionManagerFactory.md) | `getConnectionManagerFactory``()`<br>Returns the instance of the connection manager factory to use for this request                                          |
    | `java.lang.String`                                                | `getConnectionName``()`<br>Returns the name of the connection being used for this request May be null if no connection set/in-use.                           |
    | `java.io.PrintWriter`                                             | `getErrorWriter``()`<br>Returns a PrintWriter to print out errors processing this request                                                                    |
    | `java.sql.Connection`                                             | `getJDBCConnection``()`<br>Gets the JDBC connection being used for this request (can be null)                                                                |
    | `java.io.OutputStream`                                            | `getOutputStream``()`<br>Returns an OutputStream used for writing out the results of a page request                                                          |
    | `java.lang.String`                                                | `getPageEncoding``()`<br>Returns encoding of source XSQL Page associated with this request                                                                   |
    | `java.lang.String`                                                | `getParameter``(java.lang.String name)`<br>Returns the value of the requested parameter                                                                      |
    | `java.lang.String[]`                                              | `getParameterValues``(java.lang.String name)`<br>Returns an array of values for the requested parameter                                                      |
    | [`Document`](../../../org/w3c/dom/Document.md)                    | `getPostedDocument``()`<br>Returns the content of Posted XML for this request as an XML Document                                                             |
    | `java.lang.Object`                                                | `getRequestObject``(java.lang.String name)`<br>Gets a request-scope object                                                                                   |
    | [`Document`](../../../org/w3c/dom/Document.md)                    | `getRequestParamsAsXMLDocument``()`<br>Returns the content of a Request parameters as an XML Document                                                        |
    | `java.lang.String`                                                | `getSourceDocumentURI``()`<br>Returns a String representation of the requested document's URI                                                                |
    | `java.lang.String`                                                | `getStylesheetParameter``(java.lang.String name)`<br>Gets a stylesheet parameter by name                                                                     |
    | `java.util.Enumeration`                                           | `getStylesheetParameters``()`<br>Gets an enumeration of stylesheet parameter names                                                                           |
    | `java.lang.String`                                                | `getStylesheetURI``()`<br>Returns the URI of the stylesheet to be used to process the result.                                                                |
    | `java.lang.String`                                                | `getUserAgent``()`<br>Returns a String identifier of the requesting program                                                                                  |
    | `java.io.PrintWriter`                                             | `getWriter``()`<br>Returns a PrintWriter used for writing out the results of a page request                                                                  |
    | [`XSQLConnection`](XSQLConnection.md)                             | `getXSQLConnection``()`<br>Gets the XSQLConnection Object being used for this request Might be null.                                                         |
    | `oracle.xml.xsql.XSQLPage`                                        | `getXSQLPage``()`<br>Returns an instance of an XSQLPage representing the current request                                                                     |
    | `boolean`                                                         | `isErrorSignalled``()`<br>Returns true if processing error has occurred during this request                                                                  |
    | `boolean`                                                         | `isIncludedRequest``()`<br>Returns true if this request is being included in another.                                                                        |
    | `boolean`                                                         | `isOracleDriver``()`<br>Returns true if the current connection uses the Oracle JDBC Driver                                                                   |
    | `boolean`                                                         | `isUseOutputStream``()`<br>Returns true if request is using an output stream instead of a PrintWriter                                                        |
    | `boolean`                                                         | `printedErrorHeader``()`<br>Returns the state of whether an Error Header has been printed                                                                    |
    | `void`                                                            | `requestProcessed``()`<br>Allows Page Request to Perform end-of-request processing                                                                           |
    | `void`                                                            | `setConnectionName``(java.lang.String connName)`<br>Sets the connection being used for this request (can be null)                                            |
    | `void`                                                            | `setContentType``(java.lang.String mimetype)`<br>Sets the content type of the resulting page                                                                 |
    | `void`                                                            | `setErrorHandlerClass``(java.lang.String className)`<br>Sets classname to use to override default ErrorWriter for this request.                              |
    | `void`                                                            | `setIncludingRequest``(`[`XSQLPageRequest`](XSQLPageRequest.md)` includingEnv)`<br>Sets the Including Page Request object for this request.                  |
    | `void`                                                            | `setPageEncoding``(java.lang.String enc)`<br>Associates an XSQL Page with the request                                                                        |
    | `void`                                                            | `setPageParam``(java.lang.String name, java.lang.String value)`<br>Sets a dynamic page parameter value.                                                      |
    | `void`                                                            | `setPageParam``(java.lang.String name, java.lang.String[] value)`<br>Sets a dynamic page parameter value to a string array                                   |
    | `void`                                                            | `setPostedDocument``(`[`Document`](../../../org/w3c/dom/Document.md)` doc)`<br>Allows programmatic setting of the Posted Document                            |
    | `void`                                                            | `setPrintedErrorHeader``(boolean yes)`<br>Sets whether an Error Header has been printed                                                                      |
    | `void`                                                            | `setRequestObject``(java.lang.String name, java.lang.Object obj)`<br>Sets a request-scope object                                                             |
    | `void`                                                            | `setStylesheetParameter``(java.lang.String name, java.lang.String value)`<br>Sets the value of a parameter to be passed to the associated stylesheet         |
    | `void`                                                            | `setStylesheetURI``(java.lang.String uri)`<br>Sets the URI of the stylesheet to be used to process the result.                                               |
    | `void`                                                            | `signalError``(int errorCode, java.lang.String[] errorMessageArgs, java.lang.Object[] supplementalErrorInfo)`<br>Signals a processing error for this request |
    | `void`                                                            | `signalError``(java.lang.String message)`<br>Signals a processing error for this request                                                                     |
    | `java.lang.String`                                                | `translateURL``(java.lang.String filename)`<br>Returns a string representing an absolute URL resolved relative to the base URI for this request.             |
    | `boolean`                                                         | `useConnectionPooling``()`<br>Returns true if connection pooling is desired for this request                                                                 |
    | `boolean`                                                         | `useHTMLErrors``()`<br>Returns true if HTML-formatted error messages are desired for this request                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.xsql.[XSQLPageRequest](XSQLPageRequest.md)

      [`createNestedRequest`](XSQLPageRequest.md)`, `[`getRequestType`](XSQLPageRequest.md)

<!-- -->

- - ### Constructor Detail

    - #### XSQLPageRequestImpl

          public XSQLPageRequestImpl()

    <!-- -->

    - #### XSQLPageRequestImpl

          public XSQLPageRequestImpl(java.lang.String pageurl,
                                     java.util.Hashtable parameters)

  <!-- -->

  - ### Method Detail

    - #### printedErrorHeader

          public boolean printedErrorHeader()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the state of whether an Error Header has been printed
      Specified by:
      [`printedErrorHeader`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setPrintedErrorHeader

          public void setPrintedErrorHeader(boolean yes)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets whether an Error Header has been printed
      Specified by:
      [`setPrintedErrorHeader`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### isUseOutputStream

          public boolean isUseOutputStream()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns true if request is using an output stream instead of a PrintWriter
      Specified by:
      [`isUseOutputStream`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getParameter

          public java.lang.String getParameter(java.lang.String name)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the value of the requested parameter
      Specified by:
      [`getParameter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getParameterValues

          public java.lang.String[] getParameterValues(java.lang.String name)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns an array of values for the requested parameter
      Specified by:
      [`getParameterValues`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Parameters:
      `name` - the name of the parameter

    <!-- -->

    - #### getSourceDocumentURI

          public java.lang.String getSourceDocumentURI()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a String representation of the requested document's URI
      Specified by:
      [`getSourceDocumentURI`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getBaseURI

          public java.lang.String getBaseURI()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a String representation of the requested document's Base URI
      Specified by:
      [`getBaseURI`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getWriter

          public java.io.PrintWriter getWriter()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a PrintWriter used for writing out the results of a page request
      Specified by:
      [`getWriter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getErrorWriter

          public java.io.PrintWriter getErrorWriter()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a PrintWriter to print out errors processing this request
      Specified by:
      [`getErrorWriter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### useConnectionPooling

          public boolean useConnectionPooling()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns true if connection pooling is desired for this request
      Specified by:
      [`useConnectionPooling`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getUserAgent

          public java.lang.String getUserAgent()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a String identifier of the requesting program
      Specified by:
      [`getUserAgent`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setContentType

          public void setContentType(java.lang.String mimetype)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets the content type of the resulting page
      Specified by:
      [`setContentType`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### useHTMLErrors

          public boolean useHTMLErrors()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns true if HTML-formatted error messages are desired for this request
      Specified by:
      [`useHTMLErrors`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### translateURL

          public java.lang.String translateURL(java.lang.String filename)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns a string representing an absolute URL resolved relative to the base URI for this request.
      Specified by:
      [`translateURL`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setStylesheetURI

          public void setStylesheetURI(java.lang.String uri)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets the URI of the stylesheet to be used to process the result.
      Specified by:
      [`setStylesheetURI`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getStylesheetURI

          public java.lang.String getStylesheetURI()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the URI of the stylesheet to be used to process the result.
      Specified by:
      [`getStylesheetURI`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getRequestParamsAsXMLDocument

          public Document getRequestParamsAsXMLDocument()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the content of a Request parameters as an XML Document
      Specified by:
      [`getRequestParamsAsXMLDocument`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setPostedDocument

          public void setPostedDocument(Document doc)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Allows programmatic setting of the Posted Document
      Specified by:
      [`setPostedDocument`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getPostedDocument

          public Document getPostedDocument()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the content of Posted XML for this request as an XML Document
      Specified by:
      [`getPostedDocument`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setStylesheetParameter

          public void setStylesheetParameter(java.lang.String name,
                                             java.lang.String value)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets the value of a parameter to be passed to the associated stylesheet
      Specified by:
      [`setStylesheetParameter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getStylesheetParameters

          public java.util.Enumeration getStylesheetParameters()

      Gets an enumeration of stylesheet parameter names
      Specified by:
      [`getStylesheetParameters`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getStylesheetParameter

          public java.lang.String getStylesheetParameter(java.lang.String name)

      Gets a stylesheet parameter by name
      Specified by:
      [`getStylesheetParameter`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setPageEncoding

          public void setPageEncoding(java.lang.String enc)

      Associates an XSQL Page with the request
      Specified by:
      [`setPageEncoding`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getPageEncoding

          public java.lang.String getPageEncoding()

      Returns encoding of source XSQL Page associated with this request
      Specified by:
      [`getPageEncoding`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setConnectionName

          public void setConnectionName(java.lang.String connName)
                                 throws java.sql.SQLException

      Sets the connection being used for this request (can be null)
      Specified by:
      [`setConnectionName`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getJDBCConnection

          public java.sql.Connection getJDBCConnection()

      Gets the JDBC connection being used for this request (can be null)
      Specified by:
      [`getJDBCConnection`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getXSQLConnection

          public XSQLConnection getXSQLConnection()

      Gets the XSQLConnection Object being used for this request Might be null.
      Specified by:
      [`getXSQLConnection`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setIncludingRequest

          public void setIncludingRequest(XSQLPageRequest includingEnv)

      Sets the Including Page Request object for this request.
      Specified by:
      [`setIncludingRequest`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getConnectionName

          public java.lang.String getConnectionName()

      Returns the name of the connection being used for this request May be null if no connection set/in-use.
      Specified by:
      [`getConnectionName`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### requestProcessed

          public void requestProcessed()

      Allows Page Request to Perform end-of-request processing
      Specified by:
      [`requestProcessed`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### isOracleDriver

          public boolean isOracleDriver()

      Returns true if the current connection uses the Oracle JDBC Driver
      Specified by:
      [`isOracleDriver`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### isIncludedRequest

          public boolean isIncludedRequest()

      Returns true if this request is being included in another.
      Specified by:
      [`isIncludedRequest`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setPageParam

          public void setPageParam(java.lang.String name,
                                   java.lang.String value)

      Sets a dynamic page parameter value.
      Specified by:
      [`setPageParam`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setPageParam

          public void setPageParam(java.lang.String name,
                                   java.lang.String[] value)

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets a dynamic page parameter value to a string array
      Specified by:
      [`setPageParam`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setRequestObject

          public void setRequestObject(java.lang.String name,
                                       java.lang.Object obj)

      Sets a request-scope object
      Specified by:
      [`setRequestObject`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getRequestObject

          public java.lang.Object getRequestObject(java.lang.String name)

      Gets a request-scope object
      Specified by:
      [`getRequestObject`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getOutputStream

          public java.io.OutputStream getOutputStream()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns an OutputStream used for writing out the results of a page request
      Specified by:
      [`getOutputStream`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### getXSQLPage

          public oracle.xml.xsql.XSQLPage getXSQLPage()
                                               throws SAXParseException,
                                                      java.io.FileNotFoundException

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns an instance of an XSQLPage representing the current request
      Specified by:
      [`getXSQLPage`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

      Throws:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

      `java.io.FileNotFoundException`

    <!-- -->

    - #### getConnectionManagerFactory

          public XSQLConnectionManagerFactory getConnectionManagerFactory()

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Returns the instance of the connection manager factory to use for this request
      Specified by:
      [`getConnectionManagerFactory`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### isErrorSignalled

          public boolean isErrorSignalled()

      Returns true if processing error has occurred during this request
      Specified by:
      [`isErrorSignalled`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### signalError

          public void signalError(int errorCode,
                                  java.lang.String[] errorMessageArgs,
                                  java.lang.Object[] supplementalErrorInfo)

      Signals a processing error for this request
      Specified by:
      [`signalError`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### signalError

          public void signalError(java.lang.String message)

      Signals a processing error for this request
      Specified by:
      [`signalError`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

    <!-- -->

    - #### setErrorHandlerClass

          public void setErrorHandlerClass(java.lang.String className)
                                    throws oracle.xml.xsql.XSQLInitializationException

      Description copied from interface: [`XSQLPageRequest`](XSQLPageRequest.md)
      Sets classname to use to override default ErrorWriter for this request. Only has an effect if the current request is the topmost request. That is, nested requests cannot change the errorWriter just for the nested scope.
      Specified by:
      [`setErrorHandlerClass`](XSQLPageRequest.md) in interface [`XSQLPageRequest`](XSQLPageRequest.md)

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

- **[Prev Class](XSQLPageRequest.md)**
- **[Next Class](XSQLParserHelper.md)**

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
