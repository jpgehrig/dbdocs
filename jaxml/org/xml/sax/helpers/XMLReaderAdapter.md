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

- **[Prev Class](XMLFilterImpl.md)**
- **[Next Class](XMLReaderFactory.md)**

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

## **Class XMLReaderAdapter**

- **java.lang.Object**

- - **org.xml.sax.helpers.XMLReaderAdapter**

<!-- -->

- **All Implemented Interfaces:**
  **[ContentHandler](../ContentHandler.md), [Parser](../Parser.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLReaderAdapter
      extends java.lang.Object
      implements Parser, ContentHandler

  **Adapt a SAX2 XMLReader as a SAX1 Parser.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class wraps a SAX2 [`XMLReader`](../XMLReader.md) and makes it act as a SAX1 [`Parser`](../Parser.md). The XMLReader must support a true value for the http://xml.org/sax/features/namespace-prefixes property or parsing will fail with a [`SAXException`](../SAXException.md); if the XMLReader supports a false value for the http://xml.org/sax/features/namespaces property, that will also be used to improve efficiency.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`Parser`](../Parser.md), [`XMLReader`](../XMLReader.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                               |
    |-------------------------------------------------------------------------------------------|
    | `XMLReaderAdapter``()`<br>Create a new adapter.                                           |
    | `XMLReaderAdapter``(`[`XMLReader`](../XMLReader.md)` xmlReader)`<br>Create a new adapter. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                   |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `characters``(char[] ch, int start, int length)`<br>Adapt a SAX2 characters event.                                                                                       |
    | `void`            | `endDocument``()`<br>End document event.                                                                                                                                 |
    | `void`            | `endElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName)`<br>Adapt a SAX2 end element event.                                              |
    | `void`            | `endPrefixMapping``(java.lang.String prefix)`<br>Adapt a SAX2 end prefix mapping event.                                                                                  |
    | `void`            | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Adapt a SAX2 ignorable whitespace event.                                                                    |
    | `void`            | `parse``(`[`InputSource`](../InputSource.md)` input)`<br>Parse the document.                                                                                             |
    | `void`            | `parse``(java.lang.String systemId)`<br>Parse the document.                                                                                                              |
    | `void`            | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Adapt a SAX2 processing instruction event.                                                  |
    | `void`            | `setDocumentHandler``(`[`DocumentHandler`](../DocumentHandler.md)` handler)`<br>Register the SAX1 document event handler.                                                |
    | `void`            | `setDocumentLocator``(`[`Locator`](../Locator.md)` locator)`<br>Set a document locator.                                                                                  |
    | `void`            | `setDTDHandler``(`[`DTDHandler`](../DTDHandler.md)` handler)`<br>Register the DTD event handler.                                                                         |
    | `void`            | `setEntityResolver``(`[`EntityResolver`](../EntityResolver.md)` resolver)`<br>Register the entity resolver.                                                              |
    | `void`            | `setErrorHandler``(`[`ErrorHandler`](../ErrorHandler.md)` handler)`<br>Register the error event handler.                                                                 |
    | `void`            | `setLocale``(java.util.Locale locale)`<br>Set the locale for error reporting.                                                                                            |
    | `void`            | `skippedEntity``(java.lang.String name)`<br>Adapt a SAX2 skipped entity event.                                                                                           |
    | `void`            | `startDocument``()`<br>Start document event.                                                                                                                             |
    | `void`            | `startElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName, `[`Attributes`](../Attributes.md)` atts)`<br>Adapt a SAX2 start element event. |
    | `void`            | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Adapt a SAX2 start prefix mapping event.                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLReaderAdapter

          public XMLReaderAdapter()
                           throws SAXException

      Create a new adapter.
      Use the "org.xml.sax.driver" property to locate the SAX2 driver to embed.

      Throws:
      [`SAXException`](../SAXException.md) - If the embedded driver cannot be instantiated or if the org.xml.sax.driver property is not specified.

    <!-- -->

    - #### XMLReaderAdapter

          public XMLReaderAdapter(XMLReader xmlReader)

      Create a new adapter.
      Create a new adapter, wrapped around a SAX2 XMLReader. The adapter will make the XMLReader act like a SAX1 Parser.

      Parameters:
      `xmlReader` - The SAX2 XMLReader to wrap.

      Throws:
      `java.lang.NullPointerException` - If the argument is null.

  <!-- -->

  - ### Method Detail

    - #### setLocale

          public void setLocale(java.util.Locale locale)
                         throws SAXException

      Set the locale for error reporting.
      This is not supported in SAX2, and will always throw an exception.

      Specified by:
      [`setLocale`](../Parser.md) in interface [`Parser`](../Parser.md)

      Parameters:
      `locale` - The locale for error reporting.

      Throws:
      [`SAXException`](../SAXException.md) - Throws an exception (using the previous or default locale) if the requested locale is not supported.

      See Also:
      [`Parser.setLocale(java.util.Locale)`](../Parser.md)

    <!-- -->

    - #### setEntityResolver

          public void setEntityResolver(EntityResolver resolver)

      Register the entity resolver.
      Specified by:
      [`setEntityResolver`](../Parser.md) in interface [`Parser`](../Parser.md)

      Parameters:
      `resolver` - The new resolver.

      See Also:
      [`Parser.setEntityResolver(org.xml.sax.EntityResolver)`](../Parser.md)

    <!-- -->

    - #### setDTDHandler

          public void setDTDHandler(DTDHandler handler)

      Register the DTD event handler.
      Specified by:
      [`setDTDHandler`](../Parser.md) in interface [`Parser`](../Parser.md)

      Parameters:
      `handler` - The new DTD event handler.

      See Also:
      [`Parser.setDTDHandler(org.xml.sax.DTDHandler)`](../Parser.md)

    <!-- -->

    - #### setDocumentHandler

          public void setDocumentHandler(DocumentHandler handler)

      Register the SAX1 document event handler.
      Note that the SAX1 document handler has no Namespace support.

      Specified by:
      [`setDocumentHandler`](../Parser.md) in interface [`Parser`](../Parser.md)

      Parameters:
      `handler` - The new SAX1 document event handler.

      See Also:
      [`Parser.setDocumentHandler(org.xml.sax.DocumentHandler)`](../Parser.md)

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Register the error event handler.
      Specified by:
      [`setErrorHandler`](../Parser.md) in interface [`Parser`](../Parser.md)

      Parameters:
      `handler` - The new error event handler.

      See Also:
      [`Parser.setErrorHandler(org.xml.sax.ErrorHandler)`](../Parser.md)

    <!-- -->

    - #### parse

          public void parse(java.lang.String systemId)
                     throws java.io.IOException,
                            SAXException

      Parse the document.
      This method will throw an exception if the embedded XMLReader does not support the http://xml.org/sax/features/namespace-prefixes property.

      Specified by:
      [`parse`](../Parser.md) in interface [`Parser`](../Parser.md)

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

      Parse the document.
      This method will throw an exception if the embedded XMLReader does not support the http://xml.org/sax/features/namespace-prefixes property.

      Specified by:
      [`parse`](../Parser.md) in interface [`Parser`](../Parser.md)

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

      Set a document locator.
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

      Start document event.
      Specified by:
      [`startDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.startDocument()`](../ContentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      End document event.
      Specified by:
      [`endDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.endDocument()`](../ContentHandler.md)

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)

      Adapt a SAX2 start prefix mapping event.
      Specified by:
      [`startPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The prefix being mapped.

      `uri` - The Namespace URI being mapped to.

      See Also:
      [`ContentHandler.startPrefixMapping(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)

      Adapt a SAX2 end prefix mapping event.
      Specified by:
      [`endPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The prefix being mapped.

      See Also:
      [`ContentHandler.endPrefixMapping(java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String uri,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Adapt a SAX2 start element event.
      Specified by:
      [`startElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The Namespace URI.

      `localName` - The Namespace local name.

      `qName` - The qualified (prefixed) name.

      `atts` - The SAX2 attributes.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.endDocument()`](../ContentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String uri,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Adapt a SAX2 end element event.
      Specified by:
      [`endElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The Namespace URI.

      `localName` - The Namespace local name.

      `qName` - The qualified (prefixed) name.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.endElement(java.lang.String, java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Adapt a SAX2 characters event.
      Specified by:
      [`characters`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.characters(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Adapt a SAX2 ignorable whitespace event.
      Specified by:
      [`ignorableWhitespace`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - An array of characters.

      `start` - The starting position in the array.

      `length` - The number of characters to use.

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.ignorableWhitespace(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Adapt a SAX2 processing instruction event.
      Specified by:
      [`processingInstruction`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The remainder of the processing instruction

      Throws:
      [`SAXException`](../SAXException.md) - The client may raise a processing exception.

      See Also:
      [`ContentHandler.processingInstruction(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### skippedEntity

          public void skippedEntity(java.lang.String name)
                             throws SAXException

      Adapt a SAX2 skipped entity event.
      Specified by:
      [`skippedEntity`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `name` - The name of the skipped entity.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.skippedEntity(java.lang.String)`](../ContentHandler.md)

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

- **[Prev Class](XMLFilterImpl.md)**
- **[Next Class](XMLReaderFactory.md)**

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
