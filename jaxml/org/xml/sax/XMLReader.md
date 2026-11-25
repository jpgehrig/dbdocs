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

- **[Prev Class](XMLFilter.md)**
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

**org.xml.sax**

## **Interface XMLReader**

- **All Known Subinterfaces:**
  **[XMLFilter](XMLFilter.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[ParserAdapter](helpers/ParserAdapter.md), [SAXParser](../../../oracle/xml/parser/v2/SAXParser.md), [XMLFilterImpl](helpers/XMLFilterImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XMLReader

  **Interface for reading an XML document using callbacks.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  ****Note:** despite its name, this interface does *not* extend the standard Java `Reader` interface, because reading XML is a fundamentally different activity than reading character data.**

  **XMLReader is the interface that an XML parser's SAX2 driver must implement. This interface allows an application to set and query features and properties in the parser, to register event handlers for document processing, and to initiate a document parse.**

  **All SAX interfaces are assumed to be synchronous: the `parse` methods must not return until parsing is complete, and readers must wait for an event-handler callback to return before reporting the next event.**

  **This interface replaces the (now deprecated) SAX 1.0 [`Parser`](Parser.md) interface. The XMLReader interface contains two important enhancements over the old Parser interface:**

  1.  **it adds a standard way to query and set features and properties; and**
  2.  **it adds Namespace support, which is required for many higher-level XML standards.**

  **There are adapters available to convert a SAX1 Parser to a SAX2 XMLReader and vice-versa.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`XMLFilter`](XMLFilter.md), [`ParserAdapter`](helpers/ParserAdapter.md), [`XMLReaderAdapter`](helpers/XMLReaderAdapter.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                                              |
    |---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | [`ContentHandler`](ContentHandler.md) | `getContentHandler``()`<br>Return the current content handler.                                                                      |
    | [`DTDHandler`](DTDHandler.md)         | `getDTDHandler``()`<br>Return the current DTD handler.                                                                              |
    | [`EntityResolver`](EntityResolver.md) | `getEntityResolver``()`<br>Return the current entity resolver.                                                                      |
    | [`ErrorHandler`](ErrorHandler.md)     | `getErrorHandler``()`<br>Return the current error handler.                                                                          |
    | `boolean`                             | `getFeature``(java.lang.String name)`<br>Look up the value of a feature.                                                            |
    | `java.lang.Object`                    | `getProperty``(java.lang.String name)`<br>Look up the value of a property.                                                          |
    | `void`                                | `parse``(`[`InputSource`](InputSource.md)` input)`<br>Parse an XML document.                                                        |
    | `void`                                | `parse``(java.lang.String systemId)`<br>Parse an XML document from a system identifier (URI).                                       |
    | `void`                                | `setContentHandler``(`[`ContentHandler`](ContentHandler.md)` handler)`<br>Allow an application to register a content event handler. |
    | `void`                                | `setDTDHandler``(`[`DTDHandler`](DTDHandler.md)` handler)`<br>Allow an application to register a DTD event handler.                 |
    | `void`                                | `setEntityResolver``(`[`EntityResolver`](EntityResolver.md)` resolver)`<br>Allow an application to register an entity resolver.     |
    | `void`                                | `setErrorHandler``(`[`ErrorHandler`](ErrorHandler.md)` handler)`<br>Allow an application to register an error event handler.        |
    | `void`                                | `setFeature``(java.lang.String name, boolean value)`<br>Set the state of a feature.                                                 |
    | `void`                                | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set the value of a property.                                      |

<!-- -->

- - ### Method Detail

    - #### getFeature

          boolean getFeature(java.lang.String name)
                      throws SAXNotRecognizedException,
                             SAXNotSupportedException

      Look up the value of a feature.
      The feature name is any fully-qualified URI. It is possible for an XMLReader to recognize a feature name but to be unable to return its value; this is especially true in the case of an adapter for a SAX1 Parser, which has no way of knowing whether the underlying parser is performing validation or expanding external entities.

      All XMLReaders are required to recognize the http://xml.org/sax/features/namespaces and the http://xml.org/sax/features/namespace-prefixes feature names.

      Some feature values may be available only in specific contexts, such as before, during, or after a parse.

      Typical usage is something like this:

           XMLReader r = new MySAXDriver();

                                   // try to activate validation
           try {
             r.setFeature("http://xml.org/sax/features/validation", true);
           } catch (SAXException e) {
             System.err.println("Cannot activate validation.");
           }

                                   // register event handlers
           r.setContentHandler(new MyContentHandler());
           r.setErrorHandler(new MyErrorHandler());

                                   // parse the first document
           try {
             r.parse("http://www.foo.com/mydoc.xml");
           } catch (IOException e) {
             System.err.println("I/O exception reading XML document");
           } catch (SAXException e) {
             System.err.println("XML exception reading document.");
           }


      Implementors are free (and encouraged) to invent their own features, using names built on their own URIs.

      Parameters:
      `name` - The feature name, which is a fully-qualified URI.

      Returns:
      The current state of the feature (true or false).

      Throws:
      [`SAXNotRecognizedException`](SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot determine its value at this time.

      See Also:
      `setFeature(java.lang.String, boolean)`

    <!-- -->

    - #### setFeature

          void setFeature(java.lang.String name,
                          boolean value)
                   throws SAXNotRecognizedException,
                          SAXNotSupportedException

      Set the state of a feature.
      The feature name is any fully-qualified URI. It is possible for an XMLReader to recognize a feature name but to be unable to set its value; this is especially true in the case of an adapter for a SAX1 [`Parser`](Parser.md), which has no way of affecting whether the underlying parser is validating, for example.

      All XMLReaders are required to support setting http://xml.org/sax/features/namespaces to true and http://xml.org/sax/features/namespace-prefixes to false.

      Some feature values may be immutable or mutable only in specific contexts, such as before, during, or after a parse.

      Parameters:
      `name` - The feature name, which is a fully-qualified URI.

      `value` - The requested state of the feature (true or false).

      Throws:
      [`SAXNotRecognizedException`](SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot set the requested value.

      See Also:
      `getFeature(java.lang.String)`

    <!-- -->

    - #### getProperty

          java.lang.Object getProperty(java.lang.String name)
                                throws SAXNotRecognizedException,
                                       SAXNotSupportedException

      Look up the value of a property.
      The property name is any fully-qualified URI. It is possible for an XMLReader to recognize a property name but to be unable to return its state; this is especially true in the case of an adapter for a SAX1 [`Parser`](Parser.md).

      XMLReaders are not required to recognize any specific property names, though an initial core set is documented for SAX2.

      Some property values may be available only in specific contexts, such as before, during, or after a parse.

      Implementors are free (and encouraged) to invent their own properties, using names built on their own URIs.

      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      Returns:
      The current value of the property.

      Throws:
      [`SAXNotRecognizedException`](SAXNotRecognizedException.md) - When the XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot determine its value at this time.

      See Also:
      `setProperty(java.lang.String, java.lang.Object)`

    <!-- -->

    - #### setProperty

          void setProperty(java.lang.String name,
                           java.lang.Object value)
                    throws SAXNotRecognizedException,
                           SAXNotSupportedException

      Set the value of a property.
      The property name is any fully-qualified URI. It is possible for an XMLReader to recognize a property name but to be unable to set its value; this is especially true in the case of an adapter for a SAX1 [`Parser`](Parser.md).

      XMLReaders are not required to recognize setting any specific property names, though a core set is provided with SAX2.

      Some property values may be immutable or mutable only in specific contexts, such as before, during, or after a parse.

      This method is also the standard mechanism for setting extended handlers.

      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      `value` - The requested value for the property.

      Throws:
      [`SAXNotRecognizedException`](SAXNotRecognizedException.md) - When the XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot set the requested value.

    <!-- -->

    - #### setEntityResolver

          void setEntityResolver(EntityResolver resolver)

      Allow an application to register an entity resolver.
      If the application does not register an entity resolver, the XMLReader will perform its own default resolution.

      Applications may register a new or different resolver in the middle of a parse, and the SAX parser must begin using the new resolver immediately.

      Parameters:
      `resolver` - The entity resolver.

      Throws:
      `java.lang.NullPointerException` - If the resolver argument is null.

      See Also:
      `getEntityResolver()`

    <!-- -->

    - #### getEntityResolver

          EntityResolver getEntityResolver()

      Return the current entity resolver.
      Returns:
      The current entity resolver, or null if none has been registered.

      See Also:
      `setEntityResolver(org.xml.sax.EntityResolver)`

    <!-- -->

    - #### setDTDHandler

          void setDTDHandler(DTDHandler handler)

      Allow an application to register a DTD event handler.
      If the application does not register a DTD handler, all DTD events reported by the SAX parser will be silently ignored.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The DTD handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      See Also:
      `getDTDHandler()`

    <!-- -->

    - #### getDTDHandler

          DTDHandler getDTDHandler()

      Return the current DTD handler.
      Returns:
      The current DTD handler, or null if none has been registered.

      See Also:
      `setDTDHandler(org.xml.sax.DTDHandler)`

    <!-- -->

    - #### setContentHandler

          void setContentHandler(ContentHandler handler)

      Allow an application to register a content event handler.
      If the application does not register a content handler, all content events reported by the SAX parser will be silently ignored.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The content handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      See Also:
      `getContentHandler()`

    <!-- -->

    - #### getContentHandler

          ContentHandler getContentHandler()

      Return the current content handler.
      Returns:
      The current content handler, or null if none has been registered.

      See Also:
      `setContentHandler(org.xml.sax.ContentHandler)`

    <!-- -->

    - #### setErrorHandler

          void setErrorHandler(ErrorHandler handler)

      Allow an application to register an error event handler.
      If the application does not register an error handler, all error events reported by the SAX parser will be silently ignored; however, normal processing may not continue. It is highly recommended that all SAX applications implement an error handler to avoid unexpected bugs.

      Applications may register a new or different handler in the middle of a parse, and the SAX parser must begin using the new handler immediately.

      Parameters:
      `handler` - The error handler.

      Throws:
      `java.lang.NullPointerException` - If the handler argument is null.

      See Also:
      `getErrorHandler()`

    <!-- -->

    - #### getErrorHandler

          ErrorHandler getErrorHandler()

      Return the current error handler.
      Returns:
      The current error handler, or null if none has been registered.

      See Also:
      `setErrorHandler(org.xml.sax.ErrorHandler)`

    <!-- -->

    - #### parse

          void parse(InputSource input)
              throws java.io.IOException,
                     SAXException

      Parse an XML document.
      The application can use this method to instruct the XML reader to begin parsing an XML document from any valid input source (a character stream, a byte stream, or a URI).

      Applications may not invoke this method while a parse is in progress (they should create a new XMLReader instead for each nested XML document). Once a parse is complete, an application may reuse the same XMLReader object, possibly with a different input source.

      During the parse, the XMLReader will provide information about the XML document through the registered event handlers.

      This method is synchronous: it will not return until parsing has ended. If a client application wants to terminate parsing early, it should throw an exception.

      Parameters:
      `input` - The input source for the top-level of the XML document.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - An IO exception from the parser, possibly from a byte stream or character stream supplied by the application.

      See Also:
      [`InputSource`](InputSource.md), `parse(java.lang.String)`, `setEntityResolver(org.xml.sax.EntityResolver)`, `setDTDHandler(org.xml.sax.DTDHandler)`, `setContentHandler(org.xml.sax.ContentHandler)`, `setErrorHandler(org.xml.sax.ErrorHandler)`

    <!-- -->

    - #### parse

          void parse(java.lang.String systemId)
              throws java.io.IOException,
                     SAXException

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

- **[Prev Class](XMLFilter.md)**
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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
