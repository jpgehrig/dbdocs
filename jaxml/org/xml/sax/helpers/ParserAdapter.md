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

- **[Prev Class](NamespaceSupport.md)**
- **[Next Class](ParserFactory.md)**

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

## **Class ParserAdapter**

- **java.lang.Object**

- - **org.xml.sax.helpers.ParserAdapter**

<!-- -->

- **All Implemented Interfaces:**
  **[DocumentHandler](../DocumentHandler.md), [XMLReader](../XMLReader.md)**

  ------------------------------------------------------------------------

  **
  **

      public class ParserAdapter
      extends java.lang.Object
      implements XMLReader, DocumentHandler

  **Adapt a SAX1 Parser as a SAX2 XMLReader.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class wraps a SAX1 [`Parser`](../Parser.md) and makes it act as a SAX2 [`XMLReader`](../XMLReader.md), with feature, property, and Namespace support. Note that it is not possible to report [`skippedEntity`](../ContentHandler.md) events, since SAX1 does not make that information available.**

  **This adapter does not test for duplicate Namespace-qualified attribute names.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`XMLReaderAdapter`](XMLReaderAdapter.md), [`XMLReader`](../XMLReader.md), [`Parser`](../Parser.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                             |
    |-----------------------------------------------------------------------------------------|
    | `ParserAdapter``()`<br>Construct a new parser adapter.                                  |
    | `ParserAdapter``(`[`Parser`](../Parser.md)` parser)`<br>Construct a new parser adapter. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                       |
    |------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                   | `characters``(char[] ch, int start, int length)`<br>Adapt a SAX1 characters event.                                           |
    | `void`                                   | `endDocument``()`<br>Adapt a SAX1 end document event.                                                                        |
    | `void`                                   | `endElement``(java.lang.String qName)`<br>Adapt a SAX1 end element event.                                                    |
    | [`ContentHandler`](../ContentHandler.md) | `getContentHandler``()`<br>Return the current content handler.                                                               |
    | [`DTDHandler`](../DTDHandler.md)         | `getDTDHandler``()`<br>Return the current DTD handler.                                                                       |
    | [`EntityResolver`](../EntityResolver.md) | `getEntityResolver``()`<br>Return the current entity resolver.                                                               |
    | [`ErrorHandler`](../ErrorHandler.md)     | `getErrorHandler``()`<br>Return the current error handler.                                                                   |
    | `boolean`                                | `getFeature``(java.lang.String name)`<br>Check a parser feature.                                                             |
    | `java.lang.Object`                       | `getProperty``(java.lang.String name)`<br>Get a parser property.                                                             |
    | `void`                                   | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Adapt a SAX1 ignorable whitespace event.                        |
    | `void`                                   | `parse``(`[`InputSource`](../InputSource.md)` input)`<br>Parse an XML document.                                              |
    | `void`                                   | `parse``(java.lang.String systemId)`<br>Parse an XML document.                                                               |
    | `void`                                   | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Adapt a SAX1 processing instruction event.      |
    | `void`                                   | `setContentHandler``(`[`ContentHandler`](../ContentHandler.md)` handler)`<br>Set the content handler.                        |
    | `void`                                   | `setDocumentLocator``(`[`Locator`](../Locator.md)` locator)`<br>Adapt a SAX1 document locator event.                         |
    | `void`                                   | `setDTDHandler``(`[`DTDHandler`](../DTDHandler.md)` handler)`<br>Set the DTD handler.                                        |
    | `void`                                   | `setEntityResolver``(`[`EntityResolver`](../EntityResolver.md)` resolver)`<br>Set the entity resolver.                       |
    | `void`                                   | `setErrorHandler``(`[`ErrorHandler`](../ErrorHandler.md)` handler)`<br>Set the error handler.                                |
    | `void`                                   | `setFeature``(java.lang.String name, boolean state)`<br>Set a feature for the parser.                                        |
    | `void`                                   | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set a parser property.                                     |
    | `void`                                   | `startDocument``()`<br>Adapt a SAX1 start document event.                                                                    |
    | `void`                                   | `startElement``(java.lang.String qName, `[`AttributeList`](../AttributeList.md)` qAtts)`<br>Adapt a SAX1 startElement event. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ParserAdapter

          public ParserAdapter()
                        throws SAXException

      Construct a new parser adapter.
      Use the "org.xml.sax.parser" property to locate the embedded SAX1 driver.

      Throws:
      [`SAXException`](../SAXException.md) - If the embedded driver cannot be instantiated or if the org.xml.sax.parser property is not specified.

    <!-- -->

    - #### ParserAdapter

          public ParserAdapter(Parser parser)

      Construct a new parser adapter.
      Note that the embedded parser cannot be changed once the adapter is created; to embed a different parser, allocate a new ParserAdapter.

      Parameters:
      `parser` - The SAX1 parser to embed.

      Throws:
      `java.lang.NullPointerException` - If the parser parameter is null.

  <!-- -->

  - ### Method Detail

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean state)
                          throws SAXNotRecognizedException,
                                 SAXNotSupportedException

      Set a feature for the parser.
      The only features supported are namespaces and namespace-prefixes.

      Specified by:
      [`setFeature`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The feature name, as a complete URI.

      `state` - The requested feature state.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - If the feature name is not known.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - If the feature state is not supported.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../XMLReader.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)
                             throws SAXNotRecognizedException,
                                    SAXNotSupportedException

      Check a parser feature.
      The only features supported are namespaces and namespace-prefixes.

      Specified by:
      [`getFeature`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The feature name, as a complete URI.

      Returns:
      The current feature state.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - If the feature name is not known.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - If querying the feature state is not supported.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../XMLReader.md)

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.Object value)
                           throws SAXNotRecognizedException,
                                  SAXNotSupportedException

      Set a parser property.
      No special properties are currently supported.

      Specified by:
      [`setProperty`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The property name.

      `value` - The property value.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - If the feature name is not known.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - If the feature state is not supported.

      See Also:
      [`XMLReader.setProperty(java.lang.String, java.lang.Object)`](../XMLReader.md)

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String name)
                                       throws SAXNotRecognizedException,
                                              SAXNotSupportedException

      Get a parser property.
      No special properties are currently supported.

      Specified by:
      [`getProperty`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `name` - The property name.

      Returns:
      The property value.

      Throws:
      [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) - If the feature name is not known.

      [`SAXNotSupportedException`](../SAXNotSupportedException.md) - If the feature state is not supported.

      See Also:
      [`XMLReader.getProperty(java.lang.String)`](../XMLReader.md)

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver resolver)

      Set the entity resolver.
      Specified by:
      [`setEntityResolver`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `resolver` - The new entity resolver.

      Throws:
      `java.lang.NullPointerException` - If the entity resolver parameter is null.

      See Also:
      [`XMLReader.setEntityResolver(org.xml.sax.EntityResolver)`](../XMLReader.md)

    <!-- -->

    - #### getEntityResolver

          public EntityResolver getEntityResolver()

      Return the current entity resolver.
      Specified by:
      [`getEntityResolver`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current entity resolver, or null if none was supplied.

      See Also:
      [`XMLReader.getEntityResolver()`](../XMLReader.md)

    <!-- -->

    - #### setDTDHandler

          public void setDTDHandler(DTDHandler handler)

      Set the DTD handler.
      Specified by:
      [`setDTDHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new DTD handler.

      Throws:
      `java.lang.NullPointerException` - If the DTD handler parameter is null.

      See Also:
      [`XMLReader.setEntityResolver(org.xml.sax.EntityResolver)`](../XMLReader.md)

    <!-- -->

    - #### getDTDHandler

          public DTDHandler getDTDHandler()

      Return the current DTD handler.
      Specified by:
      [`getDTDHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current DTD handler, or null if none was supplied.

      See Also:
      [`XMLReader.getEntityResolver()`](../XMLReader.md)

    <!-- -->

    - #### setContentHandler

          public void setContentHandler(ContentHandler handler)

      Set the content handler.
      Specified by:
      [`setContentHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new content handler.

      Throws:
      `java.lang.NullPointerException` - If the content handler parameter is null.

      See Also:
      [`XMLReader.setEntityResolver(org.xml.sax.EntityResolver)`](../XMLReader.md)

    <!-- -->

    - #### getContentHandler

          public ContentHandler getContentHandler()

      Return the current content handler.
      Specified by:
      [`getContentHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current content handler, or null if none was supplied.

      See Also:
      [`XMLReader.getEntityResolver()`](../XMLReader.md)

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Set the error handler.
      Specified by:
      [`setErrorHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `handler` - The new error handler.

      Throws:
      `java.lang.NullPointerException` - If the error handler parameter is null.

      See Also:
      [`XMLReader.setEntityResolver(org.xml.sax.EntityResolver)`](../XMLReader.md)

    <!-- -->

    - #### getErrorHandler

          public ErrorHandler getErrorHandler()

      Return the current error handler.
      Specified by:
      [`getErrorHandler`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Returns:
      The current error handler, or null if none was supplied.

      See Also:
      [`XMLReader.getEntityResolver()`](../XMLReader.md)

    <!-- -->

    - #### parse

          public void parse(java.lang.String systemId)
                     throws java.io.IOException,
                            SAXException

      Parse an XML document.
      Specified by:
      [`parse`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `systemId` - The absolute URL of the document.

      Throws:
      `java.io.IOException` - If there is a problem reading the raw content of the document.

      [`SAXException`](../SAXException.md) - If there is a problem processing the document.

      See Also:
      `parse(org.xml.sax.InputSource)`, [`Parser.parse(java.lang.String)`](../Parser.md)

    <!-- -->

    - #### parse

          public void parse(InputSource input)
                     throws java.io.IOException,
                            SAXException

      Parse an XML document.
      Specified by:
      [`parse`](../XMLReader.md) in interface [`XMLReader`](../XMLReader.md)

      Parameters:
      `input` - An input source for the document.

      Throws:
      `java.io.IOException` - If there is a problem reading the raw content of the document.

      [`SAXException`](../SAXException.md) - If there is a problem processing the document.

      See Also:
      `parse(java.lang.String)`, [`Parser.parse(org.xml.sax.InputSource)`](../Parser.md)

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Adapt a SAX1 document locator event.
      Specified by:
      [`setDocumentLocator`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `locator` - A document locator.

      See Also:
      [`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](../ContentHandler.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Adapt a SAX1 start document event.
      Specified by:
      [`startDocument`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.startDocument()`](../DocumentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Adapt a SAX1 end document event.
      Specified by:
      [`endDocument`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.endDocument()`](../DocumentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String qName,
                                   AttributeList qAtts)
                            throws SAXException

      Adapt a SAX1 startElement event.
      If necessary, perform Namespace processing.

      Specified by:
      [`startElement`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `qName` - The qualified (prefixed) name.

      `qAtts` - The XML 1.0 attribute list (with qnames).

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](../DocumentHandler.md), [`AttributeList`](../AttributeList.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String qName)
                          throws SAXException

      Adapt a SAX1 end element event.
      Specified by:
      [`endElement`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `qName` - The qualified (prefixed) name.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](../DocumentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Adapt a SAX1 characters event.
      Specified by:
      [`characters`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../DocumentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Adapt a SAX1 ignorable whitespace event.
      Specified by:
      [`ignorableWhitespace`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.ignorableWhitespace(char[], int, int)`](../DocumentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Adapt a SAX1 processing instruction event.
      Specified by:
      [`processingInstruction`](../DocumentHandler.md) in interface [`DocumentHandler`](../DocumentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The remainder of the processing instruction

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`DocumentHandler.processingInstruction(java.lang.String, java.lang.String)`](../DocumentHandler.md)

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

- **[Prev Class](NamespaceSupport.md)**
- **[Next Class](ParserFactory.md)**

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
