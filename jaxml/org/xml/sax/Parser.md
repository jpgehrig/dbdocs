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

- **[Prev Class](Locator.md)**
- **[Next Class](SAXException.md)**

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

## **Interface Parser**

- **All Known Implementing Classes:**
  **[SAXParser](../../../oracle/xml/parser/v2/SAXParser.md), [XMLReaderAdapter](helpers/XMLReaderAdapter.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **This interface has been replaced by the SAX2 [`XMLReader`](XMLReader.md) interface, which includes Namespace support.**
  **
  **

      public interface Parser

  **Basic interface for SAX (Simple API for XML) parsers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This was the main event supplier interface for SAX1; it has been replaced in SAX2 by [`XMLReader`](XMLReader.md), which includes Namespace support and sophisticated configurability and extensibility.**

  **All SAX1 parsers must implement this basic interface: it allows applications to register handlers for different types of events and to initiate a parse from a URI, or a character stream.**

  **All SAX1 parsers must also implement a zero-argument constructor (though other constructors are also allowed).**

  **SAX1 parsers are reusable but not re-entrant: the application may reuse a parser object (possibly with a different input source) once the first parse has completed successfully, but it may not invoke the parse() methods recursively within a parse.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`EntityResolver`](EntityResolver.md), [`DTDHandler`](DTDHandler.md), [`DocumentHandler`](DocumentHandler.md), [`ErrorHandler`](ErrorHandler.md), [`HandlerBase`](HandlerBase.md), [`InputSource`](InputSource.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                                                                                  |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `parse``(`[`InputSource`](InputSource.md)` source)`<br>Deprecated. <br>Parse an XML document.                                                           |
    | `void`            | `parse``(java.lang.String systemId)`<br>Deprecated. <br>Parse an XML document from a system identifier (URI).                                           |
    | `void`            | `setDocumentHandler``(`[`DocumentHandler`](DocumentHandler.md)` handler)`<br>Deprecated. <br>Allow an application to register a document event handler. |
    | `void`            | `setDTDHandler``(`[`DTDHandler`](DTDHandler.md)` handler)`<br>Deprecated. <br>Allow an application to register a DTD event handler.                     |
    | `void`            | `setEntityResolver``(`[`EntityResolver`](EntityResolver.md)` resolver)`<br>Deprecated. <br>Allow an application to register a custom entity resolver.   |
    | `void`            | `setErrorHandler``(`[`ErrorHandler`](ErrorHandler.md)` handler)`<br>Deprecated. <br>Allow an application to register an error event handler.            |
    | `void`            | `setLocale``(java.util.Locale locale)`<br>Deprecated. <br>Allow an application to request a locale for errors and warnings.                             |

<!-- -->

- - ### Method Detail

    - #### setLocale

          void setLocale(java.util.Locale locale)
                  throws SAXException

      Deprecated. 
      Allow an application to request a locale for errors and warnings.
      SAX parsers are not required to provide localisation for errors and warnings; if they cannot support the requested locale, however, they must throw a SAX exception. Applications may not request a locale change in the middle of a parse.

      Parameters:
      `locale` - A Java Locale object.

      Throws:
      [`SAXException`](SAXException.md) - Throws an exception (using the previous or default locale) if the requested locale is not supported.

      See Also:
      [`SAXException`](SAXException.md), [`SAXParseException`](SAXParseException.md)

    <!-- -->

    - #### setEntityResolver

          void setEntityResolver(EntityResolver resolver)

      Deprecated. 
      Allow an application to register a custom entity resolver.
      If the application does not register an entity resolver, the SAX parser will resolve system identifiers and open connections to entities itself (this is the default behaviour implemented in HandlerBase).

      Applications may register a new or different entity resolver in the middle of a parse, and the SAX parser must begin using the new resolver immediately.

      Parameters:
      `resolver` - The object for resolving entities.

      See Also:
      [`EntityResolver`](EntityResolver.md), [`HandlerBase`](HandlerBase.md)

    <!-- -->

    - #### setDTDHandler

          void setDTDHandler(DTDHandler handler)

      Deprecated. 
      Allow an application to register a DTD event handler.
      If the application does not register a DTD handler, all DTD events reported by the SAX parser will be silently ignored (this is the default behaviour implemented by HandlerBase).

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The DTD handler.

      See Also:
      [`DTDHandler`](DTDHandler.md), [`HandlerBase`](HandlerBase.md)

    <!-- -->

    - #### setDocumentHandler

          void setDocumentHandler(DocumentHandler handler)

      Deprecated. 
      Allow an application to register a document event handler.
      If the application does not register a document handler, all document events reported by the SAX parser will be silently ignored (this is the default behaviour implemented by HandlerBase).

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The document handler.

      See Also:
      [`DocumentHandler`](DocumentHandler.md), [`HandlerBase`](HandlerBase.md)

    <!-- -->

    - #### setErrorHandler

          void setErrorHandler(ErrorHandler handler)

      Deprecated. 
      Allow an application to register an error event handler.
      If the application does not register an error event handler, all error events reported by the SAX parser will be silently ignored, except for fatalError, which will throw a SAXException (this is the default behaviour implemented by HandlerBase).

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The error handler.

      See Also:
      [`ErrorHandler`](ErrorHandler.md), [`SAXException`](SAXException.md), [`HandlerBase`](HandlerBase.md)

    <!-- -->

    - #### parse

          void parse(InputSource source)
              throws SAXException,
                     java.io.IOException

      Deprecated. 
      Parse an XML document.
      The application can use this method to instruct the SAX parser to begin parsing an XML document from any valid input source (a character stream, a byte stream, or a URI).

      Applications may not invoke this method while a parse is in progress (they should create a new Parser instead for each additional XML document). Once a parse is complete, an application may reuse the same Parser object, possibly with a different input source.

      Parameters:
      `source` - The input source for the top-level of the XML document.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - An IO exception from the parser, possibly from a byte stream or character stream supplied by the application.

      See Also:
      [`InputSource`](InputSource.md), `parse(java.lang.String)`, `setEntityResolver(org.xml.sax.EntityResolver)`, `setDTDHandler(org.xml.sax.DTDHandler)`, `setDocumentHandler(org.xml.sax.DocumentHandler)`, `setErrorHandler(org.xml.sax.ErrorHandler)`

    <!-- -->

    - #### parse

          void parse(java.lang.String systemId)
              throws SAXException,
                     java.io.IOException

      Deprecated. 
      Parse an XML document from a system identifier (URI).
      This method is a shortcut for the common case of reading a document from a system identifier. It is the exact equivalent of the following:

           parse(new InputSource(systemId));


      If the system identifier is a URL, it must be fully resolved by the application before it is passed to the parser.

      Parameters:
      `systemId` - The system identifier (URI).

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - An IO exception from the parser, possibly from a byte stream or character stream supplied by the application.

      See Also:
      `parse(org.xml.sax.InputSource)`

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

- **[Prev Class](Locator.md)**
- **[Next Class](SAXException.md)**

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
