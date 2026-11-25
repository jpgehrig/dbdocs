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

- **[Prev Class](XSLExtensionElement.md)**
- **[Next Class](XSLProcessor.XSLTVersion.md)**

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

## **Class XSLProcessor**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XSLProcessor**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XSLProcessor
      extends java.lang.Object

  **This class provides methods to create `XSLStylesheet` objects and to transform an input XML document using a previously constructed `XSLStylesheet`.
  The transformation effected is as specified by the [XSLT 1.0](http://www.w3.org/TR/xslt) or [XSLT 2.0 Working Draft](http://www.w3.org/TR/2003/WD-xslt20-20030502) specifications. The function setXSLTVersion controls the choice of the specification used for transformation.**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                            |
    |-------------------|------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`XSLProcessor.XSLTVersion`](XSLProcessor.XSLTVersion.md)<br>Version class used in XSLProcessor.setXSLTVersion() |

  <!-- -->

  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                                                  | Field and Description                                                                                  |
    |--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
    | `static `[`XSLProcessor.XSLTVersion`](XSLProcessor.XSLTVersion.md) | `XSLT10`<br>XSLTVersion for [XSLT 1.0](http://www.w3.org/TR/xslt) specification.                       |
    | `static `[`XSLProcessor.XSLTVersion`](XSLProcessor.XSLTVersion.md) | `XSLT20`<br>XSLTVersion for [XSLT 2.0 WD](http://www.w3.org/TR/2003/WD-xslt20-20030502) specification. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description               |
    |-------------------------------------------|
    | `XSLProcessor``()`<br>Default Constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                                            |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `getParam``(java.lang.String name)`<br>Deprecated. <br>- use getParam(String, String);                                                                                                                                                            |
    | `java.lang.Object`                              | `getParam``(java.lang.String uri, java.lang.String name)`<br>Gets the value of a top-level stylesheet parameter.                                                                                                                                  |
    | [`XSLStylesheet`](XSLStylesheet.md)             | `newXSLStylesheet``(java.io.InputStream xsl)`<br>Constructs an XSLStylesheet using the given Inputstream XSL function document('') is not supported as there is no way to re-access the input Stylesheet as XMLDocument.                          |
    | [`XSLStylesheet`](XSLStylesheet.md)             | `newXSLStylesheet``(java.io.Reader xsl)`<br>Constructs an XSLStylesheet using the given Reader XSL function document('') is not supported as there is no way to re-access the input Stylesheet as XMLDocument.                                    |
    | [`XSLStylesheet`](XSLStylesheet.md)             | `newXSLStylesheet``(java.net.URL xsl)`<br>Constructs an XSLStylesheet using the given URL                                                                                                                                                         |
    | [`XSLStylesheet`](XSLStylesheet.md)             | `newXSLStylesheet``(`[`XMLDocument`](XMLDocument.md)` xsl)`<br>Constructs an XSLStylesheet using the given XMLDocument                                                                                                                            |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, java.io.InputStream xml, java.net.URL ref)`<br>Transform input XML document using given InputStream and stylesheet.                                                                      |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, java.io.Reader xml, java.net.URL ref)`<br>Transform input XML document using given Reader and stylesheet.                                                                                |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, java.net.URL xml, java.net.URL ref)`<br>Transform input XML document using given URL and stylesheet.                                                                                     |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocument`](XMLDocument.md)` xml)`<br>Transform input XML document using given XMLDocument and stylesheet.                                                                          |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocument`](XMLDocument.md)` xml, `[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` handler)`<br>Transform input XML document using given XMLDocument and stylesheet. |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocumentFragment`](XMLDocumentFragment.md)` inp)`<br>Transform input XML document using given XMLDocument and stylesheet.                                                          |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocumentFragment`](XMLDocumentFragment.md)` xml, java.io.OutputStream os)`<br>Transform input XML using given XMLDocumentFragment and stylesheet.                                  |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocumentFragment`](XMLDocumentFragment.md)` xml, java.io.PrintWriter pw)`<br>Transform input XML using given XMLDocumentFragment and stylesheet.                                   |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocumentFragment`](XMLDocumentFragment.md)` inp, `[`XMLDocumentHandler`](XMLDocumentHandler.md)` handler)`<br>Transform input XML document using given XMLDocument and stylesheet. |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocument`](XMLDocument.md)` xml, java.io.OutputStream os)`<br>Transform input XML document using given XMLDocument and stylesheet.                                                 |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocument`](XMLDocument.md)` xml, java.io.PrintWriter pw)`<br>Transform input XML document using given XMLDocument and stylesheet.                                                  |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLDocument`](XMLDocument.md)` xml, `[`XMLDocumentHandler`](XMLDocumentHandler.md)` handler)`<br>Transform input XML document using given XMLDocument and stylesheet.                 |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLElement`](XMLElement.md)` inp)`<br>Transform input XML document using given XMLDocument and stylesheet.                                                                            |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLElement`](XMLElement.md)` inp, `[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` handler)`<br>Transform input XML document using given XMLElement and stylesheet.    |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLElement`](XMLElement.md)` xml, java.io.OutputStream os)`<br>Transform input XML using given XMLElement and stylesheet.                                                             |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLElement`](XMLElement.md)` xml, java.io.PrintWriter pw)`<br>Transform input XML using given XMLElement and stylesheet.                                                              |
    | `void`                                          | `processXSL``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl, `[`XMLElement`](XMLElement.md)` xml, `[`XMLDocumentHandler`](XMLDocumentHandler.md)` handler)`<br>Transform input XML document using given XMLElement and stylesheet.                    |
    | `void`                                          | `removeParam``(java.lang.String uri, java.lang.String name)`<br>Removes the value of a top-level stylesheet parameter.                                                                                                                            |
    | `void`                                          | `resetParams``()`<br>Resets all the params set.                                                                                                                                                                                                   |
    | `void`                                          | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                   |
    | `void`                                          | `setBaseURL``(java.net.URL url)`<br>Set base url to resolve include/import hrefs EntityResolver if set is used before using the base url                                                                                                          |
    | `void`                                          | `setEntityResolver``(`[`EntityResolver`](../../../../org/xml/sax/EntityResolver.md)` eResolver)`<br>Set entity resolver to resolve include/import hrefs if not set, base url (if set) is used.                                                    |
    | `void`                                          | `setErrorStream``(java.io.OutputStream out)`<br>Creates an output stream for the output of warnings.                                                                                                                                              |
    | `void`                                          | `setFunctionResolver``(javax.xml.xpath.XPathFunctionResolver fresolver)`<br>Set XPathFunctionResolver to resolve extension functions                                                                                                              |
    | `void`                                          | `setLocale``(java.util.Locale locale)`<br>Applications can use this to set the locale for error reporting.                                                                                                                                        |
    | `void`                                          | `setOutputEncoding``(java.lang.String externalenc)`<br>If output encoding is not specified in XSL document, output charset as "UTF-8" in META element by default.                                                                                 |
    | `void`                                          | `setParam``(java.lang.String uri, java.lang.String name, java.lang.Object value)`<br>Sets the value of a top-level stylesheet parameter.                                                                                                          |
    | `void`                                          | `setXSLTVersion``(`[`XSLProcessor.XSLTVersion`](XSLProcessor.XSLTVersion.md)` version)`<br>Set the specification version to be used for transformation.                                                                                           |
    | `void`                                          | `showWarnings``(boolean flag)`<br>Switch to determine whether to output warnings.                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### XSLT10

          public static final XSLProcessor.XSLTVersion XSLT10

      XSLTVersion for [XSLT 1.0](http://www.w3.org/TR/xslt) specification.
      See Also:
      `setXSLTVersion(oracle.xml.parser.v2.XSLProcessor.XSLTVersion)`

    <!-- -->

    - #### XSLT20

          public static final XSLProcessor.XSLTVersion XSLT20

      XSLTVersion for [XSLT 2.0 WD](http://www.w3.org/TR/2003/WD-xslt20-20030502) specification.
      See Also:
      `setXSLTVersion(oracle.xml.parser.v2.XSLProcessor.XSLTVersion)`

  <!-- -->

  - ### Constructor Detail

    - #### XSLProcessor

          public XSLProcessor()

      Default Constructor

  <!-- -->

  - ### Method Detail

    - #### setFunctionResolver

          public void setFunctionResolver(javax.xml.xpath.XPathFunctionResolver fresolver)

      Set XPathFunctionResolver to resolve extension functions
      Parameters:
      `fresolver` - - XPathFunctionResolver

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml,
                                 ContentHandler handler)
                          throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. The output of the transformation is reported through ContentHandler As the result of XSLT is a document fragment, the following functions in ContentHandler will not be called: - setDocumentLocator, startDocument, endDocument
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `handler` - ContentHandler

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml,
                                 XMLDocumentHandler handler)
                          throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. The output of the transformation is reported through XMLDocumentHandler As the result of XSLT is a document fragment, the following functions in XMLDocumentHandler will not be called: - setDocumentLocator, startDocument, endDocument, - setDoctype, endDoctype, setXMLDecl, setTextDecl
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `handler` - XMLDocument handler

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml,
                                 java.io.OutputStream os)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML document using given XMLDocument and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `os` - Outputstream to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml,
                                 java.io.PrintWriter pw)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML document using given XMLDocument and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `pw` - PrintWriter to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                XMLDocument xml)
                                         throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLElement inp,
                                 ContentHandler handler)
                          throws XSLException

      Transform input XML document using given XMLElement and stylesheet. The output of the transformation is reported through ContentHandler As the result of XSLT is a document fragment, the following functions in ContentHandler will not be called: - setDocumentLocator, startDocument, endDocument,
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `inp` - XML input to be transformed (as a DOM Tree)

      `handler` - ContentHandler

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLElement xml,
                                 XMLDocumentHandler handler)
                          throws XSLException

      Transform input XML document using given XMLElement and stylesheet. As the result of XSLT is a document fragment, the following functions in XMLDocumentHandler will not be called: - setDocumentLocator, startDocument, endDocument, - setDoctype, endDoctype, setXMLDecl, setTextDecl
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `handler` - XMLDocument Handler

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLElement xml,
                                 java.io.OutputStream os)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML using given XMLElement and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `os` - Outputstream to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLElement xml,
                                 java.io.PrintWriter pw)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML using given XMLElement and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `pw` - PrintWriter to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                XMLElement inp)
                                         throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `inp` - XML input to be transformed (as a DOM Tree)

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocumentFragment inp,
                                 XMLDocumentHandler handler)
                          throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. As the result of XSLT is a document fragment, the following functions in XMLDocumentHandler will not be called: - setDocumentLocator, startDocument, endDocument, - setDoctype, endDoctype, setXMLDecl, setTextDecl
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `inp` - XML input to be transformed (as a DOM Tree)

      `handler` - XMLDocument handler

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocumentFragment xml,
                                 java.io.OutputStream os)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML using given XMLDocumentFragment and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `os` - Outputstream to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocumentFragment xml,
                                 java.io.PrintWriter pw)
                          throws XSLException,
                                 java.io.IOException

      Transform input XML using given XMLDocumentFragment and stylesheet.
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a DOM Tree)

      `pw` - PrintWriter to which the result is printed

      Throws:
      `XSLException,` - IOException on error.

      [`XSLException`](XSLException.md)

      `java.io.IOException`

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                XMLDocumentFragment inp)
                                         throws XSLException

      Transform input XML document using given XMLDocument and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `inp` - XML input to be transformed (as a DOM Tree)

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                java.io.InputStream xml,
                                                java.net.URL ref)
                                         throws XSLException

      Transform input XML document using given InputStream and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a java.io.Inputstream)

      `ref` - Reference URL to resolve external entities in input xml file

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                java.net.URL xml,
                                                java.net.URL ref)
                                         throws XSLException

      Transform input XML document using given URL and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a java.net.URL)

      `ref` - Reference URL to resolve external entities in input xml file

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### processXSL

          public XMLDocumentFragment processXSL(XSLStylesheet xsl,
                                                java.io.Reader xml,
                                                java.net.URL ref)
                                         throws XSLException

      Transform input XML document using given Reader and stylesheet. This function doesn't support `xsl:output`, to use xsl:output use processXSL functions which accept OutputStream or PrintWriter
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      `xml` - XML input to be transformed (as a java.io.Reader)

      `ref` - Reference URL to resolve external entities in input xml file

      Returns:
      `XMLDocumentFragment`

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### newXSLStylesheet

          public XSLStylesheet newXSLStylesheet(XMLDocument xsl)
                                         throws XSLException

      Constructs an XSLStylesheet using the given XMLDocument
      Parameters:
      `xsl` - XSL input as a DOM Tree

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### newXSLStylesheet

          public XSLStylesheet newXSLStylesheet(java.io.InputStream xsl)
                                         throws XSLException

      Constructs an XSLStylesheet using the given Inputstream XSL function document('') is not supported as there is no way to re-access the input Stylesheet as XMLDocument.
      Parameters:
      `xsl` - XSL input as an Inputstream

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### newXSLStylesheet

          public XSLStylesheet newXSLStylesheet(java.net.URL xsl)
                                         throws XSLException

      Constructs an XSLStylesheet using the given URL
      Parameters:
      `xsl` - XSL input as a URL

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### newXSLStylesheet

          public XSLStylesheet newXSLStylesheet(java.io.Reader xsl)
                                         throws XSLException

      Constructs an XSLStylesheet using the given Reader XSL function document('') is not supported as there is no way to re-access the input Stylesheet as XMLDocument.
      Parameters:
      `xsl` - XSL input as a Reader

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.OutputStream out)
                                    throws java.io.IOException

      Creates an output stream for the output of warnings. If an output stream for warnings is not specified, the processor will not output any warnings
      Parameters:
      `out` - The output stream to use for errors and warnings

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### setLocale

          public void setLocale(java.util.Locale locale)

      Applications can use this to set the locale for error reporting.
      Parameters:
      `locale` - `Locale` to set

    <!-- -->

    - #### showWarnings

          public final void showWarnings(boolean flag)

      Switch to determine whether to output warnings.
      Parameters:
      `flag` - determines whether warnings should be shown By default, warnings are not output

    <!-- -->

    - #### setBaseURL

          public void setBaseURL(java.net.URL url)

      Set base url to resolve include/import hrefs EntityResolver if set is used before using the base url
      Parameters:
      `url` - Base URL to be set

      See Also:
      `setEntityResolver(org.xml.sax.EntityResolver)`

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver eResolver)

      Set entity resolver to resolve include/import hrefs if not set, base url (if set) is used.
      Parameters:
      `eResolver` - EntityResolver

    <!-- -->

    - #### setParam

          public void setParam(java.lang.String uri,
                               java.lang.String name,
                               java.lang.Object value)
                        throws XSLException

      Sets the value of a top-level stylesheet parameter. The param functions CANNOT be used along with param functions in XSLStylesheet. If the param functions in XSLProcessor are used, any parameters set using XSLStylesheet functions will be ignored.
      Parameters:
      `uri` - URI of parameter

      `name` - parameter name

      `value` - parameter value (Strings will be treated as XPath Expr for backward compatibility)

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### getParam

          public java.lang.Object getParam(java.lang.String uri,
                                           java.lang.String name)
                                    throws XSLException

      Gets the value of a top-level stylesheet parameter. The parameter value is expected to be a valid XPath expression (note that string literal values would therefore have to be explicitly quoted).
      Parameters:
      `uri` - URI of parameter

      `name` - parameter name

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### removeParam

          public void removeParam(java.lang.String uri,
                                  java.lang.String name)
                           throws XSLException

      Removes the value of a top-level stylesheet parameter.
      Parameters:
      `uri` - URI of parameter

      `name` - parameter name

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### resetParams

          public void resetParams()
                           throws XSLException

      Resets all the params set.
      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### setOutputEncoding

          public void setOutputEncoding(java.lang.String externalenc)

      If output encoding is not specified in XSL document, output charset as "UTF-8" in META element by default. This function provides to specify the charset programatically. If empty string is passed to this function, it wont print charset in META element in the output document. This function needs to be called before ProcessXSL().
      Parameters:
      `externalenc` - Externally specified Output encoding

    <!-- -->

    - #### setXSLTVersion

          public void setXSLTVersion(XSLProcessor.XSLTVersion version)

      Set the specification version to be used for transformation.
      Parameters:
      `version` - - XSLTVersion

      See Also:
      `XSLT10`, `XSLT20`

    <!-- -->

    - #### getParam

          public java.lang.Object getParam(java.lang.String name)
                                    throws TransformerException,
                                           java.io.IOException

      Deprecated. - use getParam(String, String);
      Sets the value of a top-level stylesheet parameter.
      Parameters:
      `name` - - the parameter name

      Throws:
      [`TransformerException`](../../../../javax/xml/transform/TransformerException.md)

      `java.io.IOException`

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

- **[Prev Class](XSLExtensionElement.md)**
- **[Next Class](XSLProcessor.XSLTVersion.md)**

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
