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

- **[Prev Class](AttributesImpl.md)**
- **[Next Class](LocatorImpl.md)**

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

## **Class DefaultHandler**

- **java.lang.Object**

- - **org.xml.sax.helpers.DefaultHandler**

<!-- -->

- **All Implemented Interfaces:**
  **[ContentHandler](../ContentHandler.md), [DTDHandler](../DTDHandler.md), [EntityResolver](../EntityResolver.md), [ErrorHandler](../ErrorHandler.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XMLSAXSerializer](../../../../oracle/xml/parser/v2/XMLSAXSerializer.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DefaultHandler
      extends java.lang.Object
      implements EntityResolver, DTDHandler, ContentHandler, ErrorHandler

  **Default base class for SAX2 event handlers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class is available as a convenience base class for SAX2 applications: it provides default implementations for all of the callbacks in the four core SAX2 handler classes:**

  - **[`EntityResolver`](../EntityResolver.md)**
  - **[`DTDHandler`](../DTDHandler.md)**
  - **[`ContentHandler`](../ContentHandler.md)**
  - **[`ErrorHandler`](../ErrorHandler.md)**

  **Application writers can extend this class when they need to implement only part of an interface; parser writers can instantiate this class to provide default handlers when the application has not supplied its own.**

  **This class replaces the deprecated SAX1 [`HandlerBase`](../HandlerBase.md) class.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`EntityResolver`](../EntityResolver.md), [`DTDHandler`](../DTDHandler.md), [`ContentHandler`](../ContentHandler.md), [`ErrorHandler`](../ErrorHandler.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `DefaultHandler``()`        |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                  | Method and Description                                                                                                                                                                        |
    |------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                             | `characters``(char[] ch, int start, int length)`<br>Receive notification of character data inside an element.                                                                                 |
    | `void`                             | `endDocument``()`<br>Receive notification of the end of the document.                                                                                                                         |
    | `void`                             | `endElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName)`<br>Receive notification of the end of an element.                                                    |
    | `void`                             | `endPrefixMapping``(java.lang.String prefix)`<br>Receive notification of the end of a Namespace mapping.                                                                                      |
    | `void`                             | `error``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Receive notification of a recoverable parser error.                                                                          |
    | `void`                             | `fatalError``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Report a fatal XML parsing error.                                                                                       |
    | `void`                             | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Receive notification of ignorable whitespace in element content.                                                                 |
    | `void`                             | `notationDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Receive notification of a notation declaration.                                              |
    | `void`                             | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Receive notification of a processing instruction.                                                                |
    | [`InputSource`](../InputSource.md) | `resolveEntity``(java.lang.String publicId, java.lang.String systemId)`<br>Resolve an external entity.                                                                                        |
    | `void`                             | `setDocumentLocator``(`[`Locator`](../Locator.md)` locator)`<br>Receive a Locator object for document events.                                                                                 |
    | `void`                             | `skippedEntity``(java.lang.String name)`<br>Receive notification of a skipped entity.                                                                                                         |
    | `void`                             | `startDocument``()`<br>Receive notification of the beginning of the document.                                                                                                                 |
    | `void`                             | `startElement``(java.lang.String uri, java.lang.String localName, java.lang.String qName, `[`Attributes`](../Attributes.md)` attributes)`<br>Receive notification of the start of an element. |
    | `void`                             | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Receive notification of the start of a Namespace mapping.                                                            |
    | `void`                             | `unparsedEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId, java.lang.String notationName)`<br>Receive notification of an unparsed entity declaration. |
    | `void`                             | `warning``(`[`SAXParseException`](../SAXParseException.md)` e)`<br>Receive notification of a parser warning.                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultHandler

          public DefaultHandler()

  <!-- -->

  - ### Method Detail

    - #### resolveEntity

          public InputSource resolveEntity(java.lang.String publicId,
                                           java.lang.String systemId)
                                    throws java.io.IOException,
                                           SAXException

      Resolve an external entity.
      Always return null, so that the parser will use the system identifier provided in the XML document. This method implements the SAX default behaviour: application writers can override it in a subclass to do special translations such as catalog lookups or URI redirection.

      Specified by:
      [`resolveEntity`](../EntityResolver.md) in interface [`EntityResolver`](../EntityResolver.md)

      Parameters:
      `publicId` - The public identifer, or null if none is available.

      `systemId` - The system identifier provided in the XML document.

      Returns:
      The new input source, or null to require the default behaviour.

      Throws:
      `java.io.IOException` - If there is an error setting up the new input source.

      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`EntityResolver.resolveEntity(java.lang.String, java.lang.String)`](../EntityResolver.md)

    <!-- -->

    - #### notationDecl

          public void notationDecl(java.lang.String name,
                                   java.lang.String publicId,
                                   java.lang.String systemId)
                            throws SAXException

      Receive notification of a notation declaration.
      By default, do nothing. Application writers may override this method in a subclass if they wish to keep track of the notations declared in a document.

      Specified by:
      [`notationDecl`](../DTDHandler.md) in interface [`DTDHandler`](../DTDHandler.md)

      Parameters:
      `name` - The notation name.

      `publicId` - The notation public identifier, or null if not available.

      `systemId` - The notation system identifier.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DTDHandler.notationDecl(java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

    <!-- -->

    - #### unparsedEntityDecl

          public void unparsedEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId,
                                         java.lang.String notationName)
                                  throws SAXException

      Receive notification of an unparsed entity declaration.
      By default, do nothing. Application writers may override this method in a subclass to keep track of the unparsed entities declared in a document.

      Specified by:
      [`unparsedEntityDecl`](../DTDHandler.md) in interface [`DTDHandler`](../DTDHandler.md)

      Parameters:
      `name` - The entity name.

      `publicId` - The entity public identifier, or null if not available.

      `systemId` - The entity system identifier.

      `notationName` - The name of the associated notation.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Receive a Locator object for document events.
      By default, do nothing. Application writers may override this method in a subclass if they wish to store the locator for use with other document events.

      Specified by:
      [`setDocumentLocator`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `locator` - A locator for all SAX document events.

      See Also:
      [`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](../ContentHandler.md), [`Locator`](../Locator.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Receive notification of the beginning of the document.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the beginning of a document (such as allocating the root node of a tree or creating an output file).

      Specified by:
      [`startDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.startDocument()`](../ContentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Receive notification of the end of the document.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the end of a document (such as finalising a tree or closing an output file).

      Specified by:
      [`endDocument`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.endDocument()`](../ContentHandler.md)

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Receive notification of the start of a Namespace mapping.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the start of each Namespace prefix scope (such as storing the prefix mapping).

      Specified by:
      [`startPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix being declared.

      `uri` - The Namespace URI mapped to the prefix.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.startPrefixMapping(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      Receive notification of the end of a Namespace mapping.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the end of each prefix mapping.

      Specified by:
      [`endPrefixMapping`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix being declared.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.endPrefixMapping(java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String uri,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes attributes)
                            throws SAXException

      Receive notification of the start of an element.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the start of each element (such as allocating a new tree node or writing output to a file).

      Specified by:
      [`startElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The element uri

      `localName` - The element type name.

      `qName` - The element qname

      `attributes` - The specified or defaulted attributes.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.startElement(java.lang.String, java.lang.String, java.lang.String, org.xml.sax.Attributes)`](../ContentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String uri,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Receive notification of the end of an element.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the end of each element (such as finalising a tree node or writing output to a file).

      Specified by:
      [`endElement`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `uri` - The element uri.

      `localName` - The element type name.

      `qName` - The qname of the element.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.endElement(java.lang.String, java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Receive notification of character data inside an element.
      By default, do nothing. Application writers may override this method to take specific actions for each chunk of character data (such as adding the data to a node or buffer, or printing it to a file).

      Specified by:
      [`characters`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - The characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.characters(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Receive notification of ignorable whitespace in element content.
      By default, do nothing. Application writers may override this method to take specific actions for each chunk of ignorable whitespace (such as adding data to a node or buffer, or printing it to a file).

      Specified by:
      [`ignorableWhitespace`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `ch` - The whitespace characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.ignorableWhitespace(char[], int, int)`](../ContentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Receive notification of a processing instruction.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions for each processing instruction, such as setting status variables or invoking other methods.

      Specified by:
      [`processingInstruction`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none is supplied.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.processingInstruction(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### skippedEntity

          public void skippedEntity(java.lang.String name)
                             throws SAXException

      Receive notification of a skipped entity.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions for each processing instruction, such as setting status variables or invoking other methods.

      Specified by:
      [`skippedEntity`](../ContentHandler.md) in interface [`ContentHandler`](../ContentHandler.md)

      Parameters:
      `name` - The name of the skipped entity.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.processingInstruction(java.lang.String, java.lang.String)`](../ContentHandler.md)

    <!-- -->

    - #### warning

          public void warning(SAXParseException e)
                       throws SAXException

      Receive notification of a parser warning.
      The default implementation does nothing. Application writers may override this method in a subclass to take specific actions for each warning, such as inserting the message in a log file or printing it to the console.

      Specified by:
      [`warning`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The warning information encoded as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.warning(org.xml.sax.SAXParseException)`](../ErrorHandler.md), [`SAXParseException`](../SAXParseException.md)

    <!-- -->

    - #### error

          public void error(SAXParseException e)
                     throws SAXException

      Receive notification of a recoverable parser error.
      The default implementation does nothing. Application writers may override this method in a subclass to take specific actions for each error, such as inserting the message in a log file or printing it to the console.

      Specified by:
      [`error`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The warning information encoded as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.warning(org.xml.sax.SAXParseException)`](../ErrorHandler.md), [`SAXParseException`](../SAXParseException.md)

    <!-- -->

    - #### fatalError

          public void fatalError(SAXParseException e)
                          throws SAXException

      Report a fatal XML parsing error.
      The default implementation throws a SAXParseException. Application writers may override this method in a subclass if they need to take specific actions for each fatal error (such as collecting all of the errors into a single report): in any case, the application must stop all regular processing when this method is invoked, since the document is no longer reliable, and the parser may no longer report parsing events.

      Specified by:
      [`fatalError`](../ErrorHandler.md) in interface [`ErrorHandler`](../ErrorHandler.md)

      Parameters:
      `e` - The error information encoded as an exception.

      Throws:
      [`SAXException`](../SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.fatalError(org.xml.sax.SAXParseException)`](../ErrorHandler.md), [`SAXParseException`](../SAXParseException.md)

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

- **[Prev Class](AttributesImpl.md)**
- **[Next Class](LocatorImpl.md)**

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
