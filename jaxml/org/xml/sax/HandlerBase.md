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

- **[Prev Class](ErrorHandler.md)**
- **[Next Class](InputSource.md)**

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

## **Class HandlerBase**

- **java.lang.Object**

- - **org.xml.sax.HandlerBase**

<!-- -->

- **All Implemented Interfaces:**
  **[DocumentHandler](DocumentHandler.md), [DTDHandler](DTDHandler.md), [EntityResolver](EntityResolver.md), [ErrorHandler](ErrorHandler.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[DefaultXMLDocumentHandler](../../../oracle/xml/parser/v2/DefaultXMLDocumentHandler.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **This class works with the deprecated [`DocumentHandler`](DocumentHandler.md) interface. It has been replaced by the SAX2 [`DefaultHandler`](helpers/DefaultHandler.md) class.**
  **
  **

      public class HandlerBase
      extends java.lang.Object
      implements EntityResolver, DTDHandler, DocumentHandler, ErrorHandler

  **Default base class for handlers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class implements the default behaviour for four SAX1 interfaces: EntityResolver, DTDHandler, DocumentHandler, and ErrorHandler. It is now obsolete, but is included in SAX2 to support legacy SAX1 applications. SAX2 applications should use the [`DefaultHandler`](helpers/DefaultHandler.md) class instead.**

  **Application writers can extend this class when they need to implement only part of an interface; parser writers can instantiate this class to provide default handlers when the application has not supplied its own.**

  **Note that the use of this class is optional.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`EntityResolver`](EntityResolver.md), [`DTDHandler`](DTDHandler.md), [`DocumentHandler`](DocumentHandler.md), [`ErrorHandler`](ErrorHandler.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description            |
    |----------------------------------------|
    | `HandlerBase``()`<br>Deprecated. <br>  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                        |
    |---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                          | `characters``(char[] ch, int start, int length)`<br>Deprecated. <br>Receive notification of character data inside an element.                                                                                 |
    | `void`                          | `endDocument``()`<br>Deprecated. <br>Receive notification of the end of the document.                                                                                                                         |
    | `void`                          | `endElement``(java.lang.String name)`<br>Deprecated. <br>Receive notification of the end of an element.                                                                                                       |
    | `void`                          | `error``(`[`SAXParseException`](SAXParseException.md)` e)`<br>Deprecated. <br>Receive notification of a recoverable parser error.                                                                             |
    | `void`                          | `fatalError``(`[`SAXParseException`](SAXParseException.md)` e)`<br>Deprecated. <br>Report a fatal XML parsing error.                                                                                          |
    | `void`                          | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Deprecated. <br>Receive notification of ignorable whitespace in element content.                                                                 |
    | `void`                          | `notationDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>Receive notification of a notation declaration.                                              |
    | `void`                          | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Deprecated. <br>Receive notification of a processing instruction.                                                                |
    | [`InputSource`](InputSource.md) | `resolveEntity``(java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>Resolve an external entity.                                                                                        |
    | `void`                          | `setDocumentLocator``(`[`Locator`](Locator.md)` locator)`<br>Deprecated. <br>Receive a Locator object for document events.                                                                                    |
    | `void`                          | `startDocument``()`<br>Deprecated. <br>Receive notification of the beginning of the document.                                                                                                                 |
    | `void`                          | `startElement``(java.lang.String name, `[`AttributeList`](AttributeList.md)` attributes)`<br>Deprecated. <br>Receive notification of the start of an element.                                                 |
    | `void`                          | `unparsedEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId, java.lang.String notationName)`<br>Deprecated. <br>Receive notification of an unparsed entity declaration. |
    | `void`                          | `warning``(`[`SAXParseException`](SAXParseException.md)` e)`<br>Deprecated. <br>Receive notification of a parser warning.                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### HandlerBase

          public HandlerBase()

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### resolveEntity

          public InputSource resolveEntity(java.lang.String publicId,
                                           java.lang.String systemId)
                                    throws SAXException

      Deprecated. 
      Resolve an external entity.
      Always return null, so that the parser will use the system identifier provided in the XML document. This method implements the SAX default behaviour: application writers can override it in a subclass to do special translations such as catalog lookups or URI redirection.

      Specified by:
      [`resolveEntity`](EntityResolver.md) in interface [`EntityResolver`](EntityResolver.md)

      Parameters:
      `publicId` - The public identifer, or null if none is available.

      `systemId` - The system identifier provided in the XML document.

      Returns:
      The new input source, or null to require the default behaviour.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`EntityResolver.resolveEntity(java.lang.String, java.lang.String)`](EntityResolver.md)

    <!-- -->

    - #### notationDecl

          public void notationDecl(java.lang.String name,
                                   java.lang.String publicId,
                                   java.lang.String systemId)

      Deprecated. 
      Receive notification of a notation declaration.
      By default, do nothing. Application writers may override this method in a subclass if they wish to keep track of the notations declared in a document.

      Specified by:
      [`notationDecl`](DTDHandler.md) in interface [`DTDHandler`](DTDHandler.md)

      Parameters:
      `name` - The notation name.

      `publicId` - The notation public identifier, or null if not available.

      `systemId` - The notation system identifier.

      See Also:
      [`DTDHandler.notationDecl(java.lang.String, java.lang.String, java.lang.String)`](DTDHandler.md)

    <!-- -->

    - #### unparsedEntityDecl

          public void unparsedEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId,
                                         java.lang.String notationName)

      Deprecated. 
      Receive notification of an unparsed entity declaration.
      By default, do nothing. Application writers may override this method in a subclass to keep track of the unparsed entities declared in a document.

      Specified by:
      [`unparsedEntityDecl`](DTDHandler.md) in interface [`DTDHandler`](DTDHandler.md)

      Parameters:
      `name` - The entity name.

      `publicId` - The entity public identifier, or null if not available.

      `systemId` - The entity system identifier.

      `notationName` - The name of the associated notation.

      See Also:
      [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](DTDHandler.md)

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Deprecated. 
      Receive a Locator object for document events.
      By default, do nothing. Application writers may override this method in a subclass if they wish to store the locator for use with other document events.

      Specified by:
      [`setDocumentLocator`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `locator` - A locator for all SAX document events.

      See Also:
      [`DocumentHandler.setDocumentLocator(org.xml.sax.Locator)`](DocumentHandler.md), [`Locator`](Locator.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Deprecated. 
      Receive notification of the beginning of the document.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the beginning of a document (such as allocating the root node of a tree or creating an output file).

      Specified by:
      [`startDocument`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.startDocument()`](DocumentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Deprecated. 
      Receive notification of the end of the document.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the beginning of a document (such as finalising a tree or closing an output file).

      Specified by:
      [`endDocument`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.endDocument()`](DocumentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String name,
                                   AttributeList attributes)
                            throws SAXException

      Deprecated. 
      Receive notification of the start of an element.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the start of each element (such as allocating a new tree node or writing output to a file).

      Specified by:
      [`startElement`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `name` - The element type name.

      `attributes` - The specified or defaulted attributes.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](DocumentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String name)
                          throws SAXException

      Deprecated. 
      Receive notification of the end of an element.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions at the end of each element (such as finalising a tree node or writing output to a file).

      Specified by:
      [`endElement`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `name` - The element type name.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](DocumentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Deprecated. 
      Receive notification of character data inside an element.
      By default, do nothing. Application writers may override this method to take specific actions for each chunk of character data (such as adding the data to a node or buffer, or printing it to a file).

      Specified by:
      [`characters`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `ch` - The characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](DocumentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Deprecated. 
      Receive notification of ignorable whitespace in element content.
      By default, do nothing. Application writers may override this method to take specific actions for each chunk of ignorable whitespace (such as adding data to a node or buffer, or printing it to a file).

      Specified by:
      [`ignorableWhitespace`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `ch` - The whitespace characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.ignorableWhitespace(char[], int, int)`](DocumentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Deprecated. 
      Receive notification of a processing instruction.
      By default, do nothing. Application writers may override this method in a subclass to take specific actions for each processing instruction, such as setting status variables or invoking other methods.

      Specified by:
      [`processingInstruction`](DocumentHandler.md) in interface [`DocumentHandler`](DocumentHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none is supplied.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.processingInstruction(java.lang.String, java.lang.String)`](DocumentHandler.md)

    <!-- -->

    - #### warning

          public void warning(SAXParseException e)
                       throws SAXException

      Deprecated. 
      Receive notification of a parser warning.
      The default implementation does nothing. Application writers may override this method in a subclass to take specific actions for each warning, such as inserting the message in a log file or printing it to the console.

      Specified by:
      [`warning`](ErrorHandler.md) in interface [`ErrorHandler`](ErrorHandler.md)

      Parameters:
      `e` - The warning information encoded as an exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.warning(org.xml.sax.SAXParseException)`](ErrorHandler.md), [`SAXParseException`](SAXParseException.md)

    <!-- -->

    - #### error

          public void error(SAXParseException e)
                     throws SAXException

      Deprecated. 
      Receive notification of a recoverable parser error.
      The default implementation does nothing. Application writers may override this method in a subclass to take specific actions for each error, such as inserting the message in a log file or printing it to the console.

      Specified by:
      [`error`](ErrorHandler.md) in interface [`ErrorHandler`](ErrorHandler.md)

      Parameters:
      `e` - The warning information encoded as an exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.warning(org.xml.sax.SAXParseException)`](ErrorHandler.md), [`SAXParseException`](SAXParseException.md)

    <!-- -->

    - #### fatalError

          public void fatalError(SAXParseException e)
                          throws SAXException

      Deprecated. 
      Report a fatal XML parsing error.
      The default implementation throws a SAXParseException. Application writers may override this method in a subclass if they need to take specific actions for each fatal error (such as collecting all of the errors into a single report): in any case, the application must stop all regular processing when this method is invoked, since the document is no longer reliable, and the parser may no longer report parsing events.

      Specified by:
      [`fatalError`](ErrorHandler.md) in interface [`ErrorHandler`](ErrorHandler.md)

      Parameters:
      `e` - The error information encoded as an exception.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ErrorHandler.fatalError(org.xml.sax.SAXParseException)`](ErrorHandler.md), [`SAXParseException`](SAXParseException.md)

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

- **[Prev Class](ErrorHandler.md)**
- **[Next Class](InputSource.md)**

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
