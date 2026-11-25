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

- **[Prev Class](EntityResolver.md)**
- **[Next Class](HandlerBase.md)**

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

**org.xml.sax**

## **Interface ErrorHandler**

- **All Known Implementing Classes:**
  **[CompressReaderProcess](../../../oracle/xml/pipeline/processes/CompressReaderProcess.md), [CompressWriterProcess](../../../oracle/xml/pipeline/processes/CompressWriterProcess.md), [CXMLHandlerBase](../../../oracle/xml/comp/CXMLHandlerBase.md), [DefaultHandler](helpers/DefaultHandler.md), [DefaultXMLDocumentHandler](../../../oracle/xml/parser/v2/DefaultXMLDocumentHandler.md), [DocErrorHandler](../../../oracle/xml/schemavalidator/DocErrorHandler.md), [DocumentBuilder](../../../oracle/xml/parser/v2/DocumentBuilder.md), [DOMParserProcess](../../../oracle/xml/pipeline/processes/DOMParserProcess.md), [HandlerBase](HandlerBase.md), [Process](../../../oracle/xml/pipeline/controller/Process.md), [SAXParserProcess](../../../oracle/xml/pipeline/processes/SAXParserProcess.md), [XMLFilterImpl](helpers/XMLFilterImpl.md), [XMLSAXSerializer](../../../oracle/xml/parser/v2/XMLSAXSerializer.md), [XMLTokenizer](../../../oracle/xml/parser/v2/XMLTokenizer.md), [XPathProcess](../../../oracle/xml/pipeline/processes/XPathProcess.md), [XSDSchemaBuilder](../../../oracle/xml/pipeline/processes/XSDSchemaBuilder.md), [XSDValProcess](../../../oracle/xml/pipeline/processes/XSDValProcess.md), [XSLProcess](../../../oracle/xml/pipeline/processes/XSLProcess.md), [XSLStylesheetProcess](../../../oracle/xml/pipeline/processes/XSLStylesheetProcess.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ErrorHandler

  **Basic interface for SAX error handlers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **If a SAX application needs to implement customized error handling, it must implement this interface and then register an instance with the XML reader using the [`setErrorHandler`](XMLReader.md) method. The parser will then report all errors and warnings through this interface.**

  ****WARNING:** If an application does *not* register an ErrorHandler, XML parsing errors will go unreported and bizarre behaviour may result.**

  **For XML processing errors, a SAX driver must use this interface instead of throwing an exception: it is up to the application to decide whether to throw an exception for different types of errors and warnings. Note, however, that there is no requirement that the parser continue to provide useful information after a call to `fatalError` (in other words, a SAX driver class could catch an exception and report a fatalError).**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser.setErrorHandler(org.xml.sax.ErrorHandler)`](Parser.md), [`SAXParseException`](SAXParseException.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                      |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `error``(`[`SAXParseException`](SAXParseException.md)` exception)`<br>Receive notification of a recoverable error.          |
    | `void`            | `fatalError``(`[`SAXParseException`](SAXParseException.md)` exception)`<br>Receive notification of a non-recoverable error. |
    | `void`            | `warning``(`[`SAXParseException`](SAXParseException.md)` exception)`<br>Receive notification of a warning.                  |

<!-- -->

- - ### Method Detail

    - #### warning

          void warning(SAXParseException exception)
                throws SAXException

      Receive notification of a warning.
      SAX parsers will use this method to report conditions that are not errors or fatal errors as defined by the XML 1.0 recommendation. The default behaviour is to take no action.

      The SAX parser must continue to provide normal parsing events after invoking this method: it should still be possible for the application to process the document through to the end.

      Filters may use this method to report other, non-XML warnings as well.

      Parameters:
      `exception` - The warning information encapsulated in a SAX parse exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](SAXParseException.md)

    <!-- -->

    - #### error

          void error(SAXParseException exception)
              throws SAXException

      Receive notification of a recoverable error.
      This corresponds to the definition of "error" in section 1.2 of the W3C XML 1.0 Recommendation. For example, a validating parser would use this callback to report the violation of a validity constraint. The default behaviour is to take no action.

      The SAX parser must continue to provide normal parsing events after invoking this method: it should still be possible for the application to process the document through to the end. If the application cannot do so, then the parser should report a fatal error even if the XML 1.0 recommendation does not require it to do so.

      Filters may use this method to report other, non-XML errors as well.

      Parameters:
      `exception` - The error information encapsulated in a SAX parse exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](SAXParseException.md)

    <!-- -->

    - #### fatalError

          void fatalError(SAXParseException exception)
                   throws SAXException

      Receive notification of a non-recoverable error.
      This corresponds to the definition of "fatal error" in section 1.2 of the W3C XML 1.0 Recommendation. For example, a parser would use this callback to report the violation of a well-formedness constraint.

      The application must assume that the document is unusable after the parser has invoked this method, and should continue (if at all) only for the sake of collecting addition error messages: in fact, SAX parsers are free to stop reporting any other events once this method has been invoked.

      Parameters:
      `exception` - The error information encapsulated in a SAX parse exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](SAXParseException.md)

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

- **[Prev Class](EntityResolver.md)**
- **[Next Class](HandlerBase.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
