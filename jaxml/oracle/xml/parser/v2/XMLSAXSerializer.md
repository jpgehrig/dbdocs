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

- **[Prev Class](XMLPrintDriver.md)**
- **[Next Class](XMLText.md)**

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

## **Class XMLSAXSerializer**

- **java.lang.Object**

- - **[org.xml.sax.helpers.DefaultHandler](../../../../org/xml/sax/helpers/DefaultHandler.md)**

  - - **oracle.xml.parser.v2.XMLSAXSerializer**

<!-- -->

- **All Implemented Interfaces:**
  **[ContentHandler](../../../../org/xml/sax/ContentHandler.md), [DTDHandler](../../../../org/xml/sax/DTDHandler.md), [EntityResolver](../../../../org/xml/sax/EntityResolver.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md), [DeclHandler](../../../../org/xml/sax/ext/DeclHandler.md), [LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **Use either XMLPrintDriver or ScalableDOMPrintDriver.**
  **
  **

      public class XMLSAXSerializer
      extends DefaultHandler
      implements ContentHandler, LexicalHandler, DeclHandler, DTDHandler, EntityResolver, ErrorHandler

  **Class to print the document based on a subset of SAX events. WARNING! DO NOT USE this class for general DOM serialization.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                    |
    |---------------------------|----------------------------------------------------------|
    | `static java.lang.String` | `ENCODING`<br>Deprecated. <br>Output encoding property   |
    | `static java.lang.String` | `INDENT`<br>Deprecated. <br>Output Indenting             |
    | `static java.lang.String` | `OMIT_XML_DECL`<br>Deprecated. <br>Print XML Declaration |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------|
    | `XMLSAXSerializer``(java.io.OutputStream os)`<br>Deprecated. <br>Create a XMLSAXSerializer to print the XML to the given OutputStream |
    | `XMLSAXSerializer``(java.io.PrintWriter pw)`<br>Deprecated. <br>Create a XMLSAXSerializer to print the XML to the given PrintWriter   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                    |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `attributeDecl``(java.lang.String eName, java.lang.String aName, java.lang.String type, java.lang.String mode, java.lang.String value)`<br>Deprecated. <br>Report an attribute type declaration.                                          |
    | `void`            | `characters``(char[] ch, int start, int length)`<br>Deprecated. <br>Receive notification of character data inside an element.                                                                                                             |
    | `void`            | `comment``(char[] ch, int start, int length)`<br>Deprecated. <br>Report an XML comment anywhere in the document.                                                                                                                          |
    | `void`            | `elementDecl``(java.lang.String name, java.lang.String model)`<br>Deprecated. <br>Report an element type declaration.                                                                                                                     |
    | `void`            | `endCDATA``()`<br>Deprecated. <br>Report the end of a CDATA section.                                                                                                                                                                      |
    | `void`            | `endDocument``()`<br>Deprecated. <br>Receive notification of the end of the document.                                                                                                                                                     |
    | `void`            | `endDTD``()`<br>Deprecated. <br>Report the end of DTD declarations.                                                                                                                                                                       |
    | `void`            | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Deprecated. <br>Receive notification of the end of an element.                                                                       |
    | `void`            | `endEntity``(java.lang.String name)`<br>Deprecated. <br>Report the end of an entity.                                                                                                                                                      |
    | `void`            | `externalEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>Report a parsed external entity declaration.                                                                       |
    | `void`            | `flush``()`<br>Deprecated. <br>Flushes the output stream or print writer                                                                                                                                                                  |
    | `void`            | `internalEntityDecl``(java.lang.String name, java.lang.String value)`<br>Deprecated. <br>Report an internal entity declaration.                                                                                                           |
    | `void`            | `notationDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>Receive notification of a notation declaration.                                                                          |
    | `void`            | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Deprecated. <br>Receive notification of a processing instruction.                                                                                            |
    | `void`            | `setDocumentLocator``(`[`Locator`](../../../../org/xml/sax/Locator.md)` loc)`<br>Deprecated. <br>Receive a Locator object for document events.                                                                                            |
    | `void`            | `setProperty``(java.lang.String property, java.lang.Object value)`<br>Deprecated. <br>Set output printing properties                                                                                                                      |
    | `void`            | `startCDATA``()`<br>Deprecated. <br>Report the start of a CDATA section.                                                                                                                                                                  |
    | `void`            | `startDocument``()`<br>Deprecated. <br>Receive notification of the beginning of the document.                                                                                                                                             |
    | `void`            | `startDTD``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>Report the start of DTD declarations, if any.                                                                                |
    | `void`            | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../../org/xml/sax/Attributes.md)` atts)`<br>Deprecated. <br>Receive notification of the beginning of an element. |
    | `void`            | `startEntity``(java.lang.String name)`<br>Deprecated. <br>Report the beginning of some internal and external XML entities.                                                                                                                |
    | `void`            | `unparsedEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId, java.lang.String notationName)`<br>Deprecated. <br>Receive notification of an unparsed entity declaration.                             |

    - ### Methods inherited from class org.xml.sax.helpers.[DefaultHandler](../../../../org/xml/sax/helpers/DefaultHandler.md)

      [`endPrefixMapping`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`error`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`fatalError`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`resolveEntity`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`skippedEntity`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`startPrefixMapping`](../../../../org/xml/sax/helpers/DefaultHandler.md)`, `[`warning`](../../../../org/xml/sax/helpers/DefaultHandler.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md)

      [`endPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/ContentHandler.md)`, `[`skippedEntity`](../../../../org/xml/sax/ContentHandler.md)`, `[`startPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[EntityResolver](../../../../org/xml/sax/EntityResolver.md)

      [`resolveEntity`](../../../../org/xml/sax/EntityResolver.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)

      [`error`](../../../../org/xml/sax/ErrorHandler.md)`, `[`fatalError`](../../../../org/xml/sax/ErrorHandler.md)`, `[`warning`](../../../../org/xml/sax/ErrorHandler.md)

<!-- -->

- - ### Field Detail

    - #### ENCODING

          public static final java.lang.String ENCODING

      Deprecated. 
      Output encoding property
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### INDENT

          public static final java.lang.String INDENT

      Deprecated. 
      Output Indenting
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OMIT_XML_DECL

          public static final java.lang.String OMIT_XML_DECL

      Deprecated. 
      Print XML Declaration
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLSAXSerializer

          public XMLSAXSerializer(java.io.PrintWriter pw)

      Deprecated. 
      Create a XMLSAXSerializer to print the XML to the given PrintWriter
      Parameters:
      `pw` - PrintWriter

    <!-- -->

    - #### XMLSAXSerializer

          public XMLSAXSerializer(java.io.OutputStream os)

      Deprecated. 
      Create a XMLSAXSerializer to print the XML to the given OutputStream
      Parameters:
      `os` - OutputStream

  <!-- -->

  - ### Method Detail

    - #### setProperty

          public void setProperty(java.lang.String property,
                                  java.lang.Object value)

      Deprecated. 
      Set output printing properties
      Parameters:
      `property` -

      `value` - of the property

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator loc)

      Deprecated. 
      Description copied from class: [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)
      Receive a Locator object for document events.
      By default, do nothing. Application writers may override this method in a subclass if they wish to store the locator for use with other document events.

      Specified by:
      [`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`setDocumentLocator`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `loc` - A locator for all SAX document events.

      See Also:
      [`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](../../../../org/xml/sax/ContentHandler.md), [`Locator`](../../../../org/xml/sax/Locator.md)

    <!-- -->

    - #### flush

          public void flush()
                     throws java.io.IOException

      Deprecated. 
      Flushes the output stream or print writer
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Deprecated. 
      Receive notification of the beginning of the document.
      Specified by:
      [`startDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startDocument`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.startDocument()`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Deprecated. 
      Receive notification of the end of the document.
      Specified by:
      [`endDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endDocument`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.endDocument()`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String namespaceURI,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Deprecated. 
      Receive notification of the beginning of an element.
      Specified by:
      [`startElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startElement`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified name (with prefix), or the empty string if qualified names are not available.

      `atts` - The attributes attached to the element. If there are no attributes, it shall be an empty Attributes object.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endElement(java.lang.String, java.lang.String, java.lang.String)`, [`Attributes`](../../../../org/xml/sax/Attributes.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String namespaceURI,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Deprecated. 
      Receive notification of the end of an element.
      Specified by:
      [`endElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endElement`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified XML 1.0 name (with prefix), or the empty string if qualified names are not available.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`ContentHandler.endElement(java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Deprecated. 
      Receive notification of a processing instruction.
      Specified by:
      [`processingInstruction`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`processingInstruction`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none is supplied.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.processingInstruction(java.lang.String, java.lang.String)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Deprecated. 
      Receive notification of character data inside an element.
      Specified by:
      [`characters`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`characters`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `ch` - The characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### startDTD

          public void startDTD(java.lang.String name,
                               java.lang.String publicId,
                               java.lang.String systemId)
                        throws SAXException

      Deprecated. 
      Report the start of DTD declarations, if any.
      Specified by:
      [`startDTD`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The document type name.

      `publicId` - The declared public identifier for the external DTD subset, or null if none was declared.

      `systemId` - The declared system identifier for the external DTD subset, or null if none was declared.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endDTD()`, `startEntity(java.lang.String)`

    <!-- -->

    - #### endDTD

          public void endDTD()
                      throws SAXException

      Deprecated. 
      Report the end of DTD declarations.
      This method is intended to report the end of the DOCTYPE declaration; if the document has no DOCTYPE declaration, this method will not be invoked.

      Specified by:
      [`endDTD`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startDTD(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### startEntity

          public void startEntity(java.lang.String name)
                           throws SAXException

      Deprecated. 
      Report the beginning of some internal and external XML entities.
      Specified by:
      [`startEntity`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endEntity(java.lang.String)`, [`DeclHandler.internalEntityDecl(java.lang.String, java.lang.String)`](../../../../org/xml/sax/ext/DeclHandler.md), [`DeclHandler.externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/ext/DeclHandler.md)

    <!-- -->

    - #### endEntity

          public void endEntity(java.lang.String name)
                         throws SAXException

      Deprecated. 
      Report the end of an entity.
      Specified by:
      [`endEntity`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity that is ending.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startEntity(java.lang.String)`

    <!-- -->

    - #### startCDATA

          public void startCDATA()
                          throws SAXException

      Deprecated. 
      Report the start of a CDATA section.
      The contents of the CDATA section will be reported through the regular [`characters`](../../../../org/xml/sax/ContentHandler.md) event; this event is intended only to report the boundary.

      Specified by:
      [`startCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endCDATA()`

    <!-- -->

    - #### endCDATA

          public void endCDATA()
                        throws SAXException

      Deprecated. 
      Report the end of a CDATA section.
      Specified by:
      [`endCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startCDATA()`

    <!-- -->

    - #### comment

          public void comment(char[] ch,
                              int start,
                              int length)
                       throws SAXException

      Deprecated. 
      Report an XML comment anywhere in the document.
      Specified by:
      [`comment`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `ch` - An array holding the characters in the comment.

      `start` - The starting position in the array.

      `length` - The number of characters to use from the array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### elementDecl

          public void elementDecl(java.lang.String name,
                                  java.lang.String model)
                           throws SAXException

      Deprecated. 
      Report an element type declaration.
      The content model will consist of the string "EMPTY", the string "ANY", or a parenthesised group, optionally followed by an occurrence indicator. The model will be normalized so that all parameter entities are fully resolved and all whitespace is removed, and will include the enclosing parentheses. Other normalization (such as removing redundant parentheses or simplifying occurrence indicators) is at the discretion of the parser.

      Specified by:
      [`elementDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The element type name.

      `model` - The content model as a normalized string.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### attributeDecl

          public void attributeDecl(java.lang.String eName,
                                    java.lang.String aName,
                                    java.lang.String type,
                                    java.lang.String mode,
                                    java.lang.String value)
                             throws SAXException

      Deprecated. 
      Report an attribute type declaration.
      Only the effective (first) declaration for an attribute will be reported. The type will be one of the strings "CDATA", "ID", "IDREF", "IDREFS", "NMTOKEN", "NMTOKENS", "ENTITY", "ENTITIES", a parenthesized token group with the separator "\|" and all whitespace removed, or the word "NOTATION" followed by a space followed by a parenthesized token group with all whitespace removed.

      The value will be the value as reported to applications, appropriately normalized and with entity and character references expanded.

      Specified by:
      [`attributeDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `eName` - The name of the associated element.

      `aName` - The name of the attribute.

      `type` - A string representing the attribute type.

      `mode` - A string representing the attribute defaulting mode ("#IMPLIED", "#REQUIRED", or "#FIXED") or null if none of these applies.

      `value` - A string representing the attribute's default value, or null if there is none.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### internalEntityDecl

          public void internalEntityDecl(java.lang.String name,
                                         java.lang.String value)
                                  throws SAXException

      Deprecated. 
      Report an internal entity declaration.
      Only the effective (first) declaration for each entity will be reported. All parameter entities in the value will be expanded, but general entities will not.

      Specified by:
      [`internalEntityDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `value` - The replacement text of the entity.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

    <!-- -->

    - #### externalEntityDecl

          public void externalEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId)
                                  throws SAXException

      Deprecated. 
      Report a parsed external entity declaration.
      Only the effective (first) declaration for each entity will be reported.

      If the system identifier is a URL, the parser must resolve it fully before passing it to the application.

      Specified by:
      [`externalEntityDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `publicId` - The entity's public identifier, or null if none was given.

      `systemId` - The entity's system identifier.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `internalEntityDecl(java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

    <!-- -->

    - #### notationDecl

          public void notationDecl(java.lang.String name,
                                   java.lang.String publicId,
                                   java.lang.String systemId)
                            throws SAXException

      Deprecated. 
      Description copied from class: [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)
      Receive notification of a notation declaration.
      By default, do nothing. Application writers may override this method in a subclass if they wish to keep track of the notations declared in a document.

      Specified by:
      [`notationDecl`](../../../../org/xml/sax/DTDHandler.md) in interface [`DTDHandler`](../../../../org/xml/sax/DTDHandler.md)

      Overrides:
      [`notationDecl`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `name` - The notation name.

      `publicId` - The notation public identifier, or null if not available.

      `systemId` - The notation system identifier.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DTDHandler.notationDecl(java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

    <!-- -->

    - #### unparsedEntityDecl

          public void unparsedEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId,
                                         java.lang.String notationName)
                                  throws SAXException

      Deprecated. 
      Description copied from class: [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)
      Receive notification of an unparsed entity declaration.
      By default, do nothing. Application writers may override this method in a subclass to keep track of the unparsed entities declared in a document.

      Specified by:
      [`unparsedEntityDecl`](../../../../org/xml/sax/DTDHandler.md) in interface [`DTDHandler`](../../../../org/xml/sax/DTDHandler.md)

      Overrides:
      [`unparsedEntityDecl`](../../../../org/xml/sax/helpers/DefaultHandler.md) in class [`DefaultHandler`](../../../../org/xml/sax/helpers/DefaultHandler.md)

      Parameters:
      `name` - The entity name.

      `publicId` - The entity public identifier, or null if not available.

      `systemId` - The entity system identifier.

      `notationName` - The name of the associated notation.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

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

- **[Prev Class](XMLPrintDriver.md)**
- **[Next Class](XMLText.md)**

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
