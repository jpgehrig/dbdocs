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

- **[Prev Class](ParserFactory.md)**
- **[Next Class](XMLReaderAdapter.md)**

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

**org.xml.sax.helpers**

## **Class XMLFilterImpl**

- **java.lang.Object**

- - **org.xml.sax.helpers.XMLFilterImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[ContentHandler](../ContentHandler.md), [DTDHandler](../DTDHandler.md), [EntityResolver](../EntityResolver.md), [ErrorHandler](../ErrorHandler.md), [XMLFilter](../XMLFilter.md), [XMLReader](../XMLReader.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLFilterImpl
      extends java.lang.Object
      implements XMLFilter, EntityResolver, DTDHandler, ContentHandler, ErrorHandler

  **Base class for deriving an XML filter.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class is designed to sit between an [`XMLReader`](../XMLReader.md) and the client application's event handlers. By default, it does nothing but pass requests up to the reader and events on to the handlers unmodified, but subclasses can override specific methods to modify the event stream or the configuration requests as they pass through.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`XMLFilter`](../XMLFilter.md), [`XMLReader`](../XMLReader.md), [`EntityResolver`](../EntityResolver.md), [`DTDHandler`](../DTDHandler.md), [`ContentHandler`](../ContentHandler.md), [`ErrorHandler`](../ErrorHandler.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                      |
    |------------------------------------------------------------------------------------------------------------------|
    | `XMLFilterImpl``()`<br>Construct an empty XML filter, with no parent.                                            |
    | `XMLFilterImpl``(`[`XMLReader`](../XMLReader.md)` parent)`<br>Construct an XML filter with the specified parent. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                                                                             |
    |------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                   | `characters``(char[] ch, int start, int length)`<br>Filter a character data event.                                                                                                 |
    | `void`                                   | `endDocument``()`<br>Filter an end document event.                                                                                                                                 |
    | `void`                                   | `endElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName)`<br>Filter an end element event.                                                           |
    | `void`                                   | `endPrefixMapping``(java.lang.String prefix)`<br>Filter an end Namespace prefix mapping event.                                                                                     |
    | `void`                                   | `error``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Filter an error event.                                                                                            |
    | `void`                                   | `fatalError``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Filter a fatal error event.                                                                                  |
    | [`ContentHandler`](../ContentHandler.md) | `getContentHandler``()`<br>Get the content event handler.                                                                                                                          |
    | [`DTDHandler`](../DTDHandler.md)         | `getDTDHandler``()`<br>Get the current DTD event handler.                                                                                                                          |
    | [`EntityResolver`](../EntityResolver.md) | `getEntityResolver``()`<br>Get the current entity resolver.                                                                                                                        |
    | [`ErrorHandler`](../ErrorHandler.md)     | `getErrorHandler``()`<br>Get the current error event handler.                                                                                                                      |
    | `boolean`                                | `getFeature``(java.lang.String name)`<br>Look up the state of a feature.                                                                                                           |
    | [`XMLReader`](../XMLReader.md)           | `getParent``()`<br>Get the parent reader.                                                                                                                                          |
    | `java.lang.Object`                       | `getProperty``(java.lang.String name)`<br>Look up the value of a property.                                                                                                         |
    | `void`                                   | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Filter an ignorable whitespace event.                                                                                 |
    | `void`                                   | `notationDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Filter a notation declaration event.                                              |
    | `void`                                   | `parse``(`[`InputSource`](../InputSource.md)` input)`<br>Parse a document.                                                                                                         |
    | `void`                                   | `parse``(java.lang.String systemId)`<br>Parse a document.                                                                                                                          |
    | `void`                                   | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Filter a processing instruction event.                                                                |
    | [`InputSource`](../InputSource.md)       | `resolveEntity``(java.lang.String publicId, java.lang.String systemId)`<br>Filter an external entity resolution.                                                                   |
    | `void`                                   | `setContentHandler``(`[`ContentHandler`](../ContentHandler.md)` handler)`<br>Set the content event handler.                                                                        |
    | `void`                                   | `setDocumentLocator``(`[`Locator`](../Locator.md)` locator)`<br>Filter a new document locator event.                                                                               |
    | `void`                                   | `setDTDHandler``(`[`DTDHandler`](../DTDHandler.md)` handler)`<br>Set the DTD event handler.                                                                                        |
    | `void`                                   | `setEntityResolver``(`[`EntityResolver`](../EntityResolver.md)` resolver)`<br>Set the entity resolver.                                                                             |
    | `void`                                   | `setErrorHandler``(`[`ErrorHandler`](../ErrorHandler.md)` handler)`<br>Set the error event handler.                                                                                |
    | `void`                                   | `setFeature``(java.lang.String name, boolean state)`<br>Set the state of a feature.                                                                                                |
    | `void`                                   | `setParent``(`[`XMLReader`](../XMLReader.md)` parent)`<br>Set the parent reader.                                                                                                   |
    | `void`                                   | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set the value of a property.                                                                                     |
    | `void`                                   | `skippedEntity``(java.lang.String name)`<br>Filter a skipped entity event.                                                                                                         |
    | `void`                                   | `startDocument``()`<br>Filter a start document event.                                                                                                                              |
    | `void`                                   | `startElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName, `[`Attributes`](../Attributes.md)` atts)`<br>Filter a start element event.               |
    | `void`                                   | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Filter a start Namespace prefix mapping event.                                                            |
    | `void`                                   | `unparsedEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId, java.lang.String notationName)`<br>Filter an unparsed entity declaration event. |
    | `void`                                   | `warning``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Filter a warning event.                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLFilterImpl

          public XMLFilterImpl()

      Construct an empty XML filter, with no parent.
      This filter will have no parent: you must assign a parent before you start a parse or do any configuration with setFeature or setProperty.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../XMLReader.md), [`XMLReader.setProperty(java.lang.String, java.lang.Object)`](../XMLReader.md)

    <!-- -->

    - #### XMLFilterImpl

          public XMLFilterImpl(XMLReader parent)

      Construct an XML filter with the specified parent.
      See Also:
      `setParent(org.xml.sax.XMLReader)`, `getParent()`

  <!-- -->

  - ### Method Detail

    - #### setParent

          public void setParent(XMLReader parent)

      Set the parent reader.
      This is the [`XMLReader`](../XMLReader.md) from which this filter will obtain its events and to which it will pass its configuration requests. The parent may itself be another filter.

      If there is no parent reader set, any attempt to parse or to set or get a feature or property will fail.

      Specified by:
      [`setParent`](../XMLFilter.md) in interface [`XMLFilter`](../XMLFilter.md)

      Parameters:
      `parent` - The parent XML reader.

      Throws:
      `java.lang.NullPointerException` - If the parent is null.

      See Also:
      `getParent()`

    <!-- -->

    - #### getParent

          public XMLReader getParent()

      Get the parent reader.
      Specified by:
      [`getParent`](../XMLFilter.md) in interface [`XMLFilter`](../XMLFilter.md)

      Returns:
      The parent XML reader, or null if none is set.

      See Also:
      `setParent(org.xml.sax.XMLReader)`

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean state)
                          throws SAXNotRecognizedException,
                                 SAXNotSupportedException

      Set the state of a feature.
      This will always fail if the parent is null.

      Specified by:
      [`setFeature`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The feature name.

      `state` - The requested feature state.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot set the requested value.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../XMLReader.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)
                             throws SAXNotRecognizedException,
                                    SAXNotSupportedException

      Look up the state of a feature.
      This will always fail if the parent is null.

      Specified by:
      [`getFeature`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The feature name.

      Returns:
      The current state of the feature.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - When the XMLReader recognizes the feature name but cannot determine its state at this time.

      See Also:
      [`XMLReader.getFeature(java.lang.String)`](../XMLReader.md)

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.Object value)
                           throws SAXNotRecognizedException,
                                  SAXNotSupportedException

      Set the value of a property.
      This will always fail if the parent is null.

      Specified by:
      [`setProperty`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The property name.

      `value` - The requested property value.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - When the XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot set the requested value.

      See Also:
      [`XMLReader.setProperty(java.lang.String, java.lang.Object)`](../XMLReader.md)

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String name)
                                       throws SAXNotRecognizedException,
                                              SAXNotSupportedException

      Look up the value of a property.
      Specified by:
      [`getProperty`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The property name.

      Returns:
      The current value of the property.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - When the XMLReader does not recognize the feature name.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - When the XMLReader recognizes the property name but cannot determine its value at this time.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../XMLReader.md)

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver resolver)

      Set the entity resolver.
      Specified by:
      [`setEntityResolver`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `resolver` - The new entity resolver.

      Throws:
      `java.lang.NullPointerException` - If the resolver is null.

      See Also:
      [`XMLReader.setEntityResolver(org.xml.sax.EntityResolver)`](../XMLReader.md)

    <!-- -->

    - #### getEntityResolver

          public EntityResolver getEntityResolver()

      Get the current entity resolver.
      Specified by:
      [`getEntityResolver`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current entity resolver, or null if none was set.

      See Also:
      [`XMLReader.getEntityResolver()`](../XMLReader.md)

    <!-- -->

    - #### setDTDHandler

          public void setDTDHandler(DTDHandler handler)

      Set the DTD event handler.
      Specified by:
      [`setDTDHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new DTD handler.

      Throws:
      `java.lang.NullPointerException` - If the handler is null.

      See Also:
      [`XMLReader.setDTDHandler(org.xml.sax.DTDHandler)`](../XMLReader.md)

    <!-- -->

    - #### getDTDHandler

          public DTDHandler getDTDHandler()

      Get the current DTD event handler.
      Specified by:
      [`getDTDHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current DTD handler, or null if none was set.

      See Also:
      [`XMLReader.getDTDHandler()`](../XMLReader.md)

    <!-- -->

    - #### setContentHandler

          public void setContentHandler(ContentHandler handler)

      Set the content event handler.
      Specified by:
      [`setContentHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new content handler.

      Throws:
      `java.lang.NullPointerException` - If the handler is null.

      See Also:
      [`XMLReader.setContentHandler(org.xml.sax.ContentHandler)`](../XMLReader.md)

    <!-- -->

    - #### getContentHandler

          public ContentHandler getContentHandler()

      Get the content event handler.
      Specified by:
      [`getContentHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current content handler, or null if none was set.

      See Also:
      [`XMLReader.getContentHandler()`](../XMLReader.md)

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Set the error event handler.
      Specified by:
      [`setErrorHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new error handler.

      Throws:
      `java.lang.NullPointerException` - If the handler is null.

      See Also:
      [`XMLReader.setErrorHandler(org.xml.sax.ErrorHandler)`](../XMLReader.md)

    <!-- -->

    - #### getErrorHandler

          public ErrorHandler getErrorHandler()

      Get the current error event handler.
      Specified by:
      [`getErrorHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current error handler, or null if none was set.

      See Also:
      [`XMLReader.getErrorHandler()`](../XMLReader.md)

    <!-- -->

    - #### parse

          public void parse(InputSource input)
                     throws SAXException,
                            java.io.IOException

      Parse a document.
      Specified by:
      [`parse`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `input` - The input source for the document entity.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - An IO exception from the parser, possibly from a byte stream or character stream supplied by the application.

      See Also:
      [`XMLReader.parse(org.xml.sax.InputSource)`](../XMLReader.md)

    <!-- -->

    - #### parse

          public void parse(java.lang.String systemId)
                     throws SAXException,
                            java.io.IOException

      Parse a document.
      Specified by:
      [`parse`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `systemId` - The system identifier as a fully-qualified URI.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - An IO exception from the parser, possibly from a byte stream or character stream supplied by the application.

      See Also:
      [`XMLReader.parse(java.lang.String)`](../XMLReader.md)

    <!-- -->

    - #### resolveEntity

          public InputSource resolveEntity(java.lang.String publicId,
                                           java.lang.String systemId)
                                    throws SAXException,
                                           java.io.IOException

      Filter an external entity resolution.
      Specified by:
      [`resolveEntity`](../EntityResolver.md) in interface [`EntityResolver`](../EntityResolver.md)

      Parameters:
      `publicId` - The entity's public identifier, or null.

      `systemId` - The entity's system identifier.

      Returns:
      A new InputSource or null for the default.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      `java.io.IOException` - The client may throw an I/O-related exception while obtaining the new InputSource.

      See Also:
      [`EntityResolver.resolveEntity(java.lang.String, java.lang.String)`](../EntityResolver.md)

    <!-- -->

    - #### notationDecl

          public void notationDecl(java.lang.String name,
                                   java.lang.String publicId,
                                   java.lang.String systemId)
                            throws SAXException

      Filter a notation declaration event.
      Specified by:
      [`notationDecl`](../DTDHandler.md) in interface [`DTDHandler`](../DTDHandler.md)

      Parameters:
      `name` - The notation name.

      `publicId` - The notation's public identifier, or null.

      `systemId` - The notation's system identifier, or null.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`DTDHandler.notationDecl(java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

    <!-- -->

    - #### unparsedEntityDecl

          public void unparsedEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId,
                                         java.lang.String notationName)
                                  throws SAXException

      Filter an unparsed entity declaration event.
      Specified by:
      [`unparsedEntityDecl`](../DTDHandler.md) in interface [`DTDHandler`](../DTDHandler.md)

      Parameters:
      `name` - The entity name.

      `publicId` - The entity's public identifier, or null.

      `systemId` - The entity's system identifier, or null.

      `notationName` - The name of the associated notation.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Filter a new document locator event.
      Specified by:
      [`setDocumentLocator`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `locator` - The document locator.

      See Also:
      [`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](../ContentHandler.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Filter a start document event.
      Specified by:
      [`startDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.startDocument()`](../ContentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Filter an end document event.
      Specified by:
      [`endDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.endDocument()`](../ContentHandler.md)

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Filter a start Namespace prefix mapping event.
      Specified by:
      [`startPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix.

      `uri` - The Namespace URI.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.startPrefixMapping(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      Filter an end Namespace prefix mapping event.
      Specified by:
      [`endPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.endPrefixMapping(java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String uri,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Filter a start element event.
      Specified by:
      [`startElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The element's Namespace URI, or the empty string.

      `localName` - The element's local name, or the empty string.

      `qName` - The element's qualified (prefixed) name, or the empty string.

      `atts` - The element's attributes.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.startElement(java.lang.String, java.lang.String, java.lang.String, org.xml.sax.Attributes)`](../ContentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String uri,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Filter an end element event.
      Specified by:
      [`endElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The element's Namespace URI, or the empty string.

      `localName` - The element's local name, or the empty string.

      `qName` - The element's qualified (prefixed) name, or the empty string.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.endElement(java.lang.String, java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Filter a character data event.
      Specified by:
      [`characters`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use from the array.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.characters(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Filter an ignorable whitespace event.
      Specified by:
      [`ignorableWhitespace`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use from the array.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.ignorableWhitespace(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Filter a processing instruction event.
      Specified by:
      [`processingInstruction`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The text following the target.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.processingInstruction(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### skippedEntity

          public void skippedEntity(java.lang.String name)
                             throws SAXException

      Filter a skipped entity event.
      Specified by:
      [`skippedEntity`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `name` - The name of the skipped entity.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ContentHandler.skippedEntity(java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### warning

          public void warning(SAXParseException e)
                       throws SAXException

      Filter a warning event.
      Specified by:
      [`warning`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The nwarning as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ErrorHandler.warning(org.xml.sax.SAXParseException)`](../ErrorHandler.md)

    <!-- -->

    - #### error

          public void error(SAXParseException e)
                     throws SAXException

      Filter an error event.
      Specified by:
      [`error`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The error as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ErrorHandler.error(org.xml.sax.SAXParseException)`](../ErrorHandler.md)

    <!-- -->

    - #### fatalError

          public void fatalError(SAXParseException e)
                          throws SAXException

      Filter a fatal error event.
      Specified by:
      [`fatalError`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The error as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - The client may throw an exception during processing.

      See Also:
      [`ErrorHandler.fatalError(org.xml.sax.SAXParseException)`](../ErrorHandler.md)

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

- **[Prev Class](ParserFactory.md)**
- **[Next Class](XMLReaderAdapter.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
