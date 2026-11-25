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

- **[Prev Class](ContentHandler.md)**
- **[Next Class](DTDHandler.md)**

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

## **Interface DocumentHandler**

- **All Known Subinterfaces:**
  **[XMLDocumentHandler](../../../oracle/xml/parser/v2/XMLDocumentHandler.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[CXMLHandlerBase](../../../oracle/xml/comp/CXMLHandlerBase.md), [DefaultXMLDocumentHandler](../../../oracle/xml/parser/v2/DefaultXMLDocumentHandler.md), [DocumentBuilder](../../../oracle/xml/parser/v2/DocumentBuilder.md), [HandlerBase](HandlerBase.md), [ParserAdapter](helpers/ParserAdapter.md), [XMLTokenizer](../../../oracle/xml/parser/v2/XMLTokenizer.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **This interface has been replaced by the SAX2 [`ContentHandler`](ContentHandler.md) interface, which includes Namespace support.**
  **
  **

      public interface DocumentHandler

  **Receive notification of general document events.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This was the main event-handling interface for SAX1; in SAX2, it has been replaced by [`ContentHandler`](ContentHandler.md), which provides Namespace support and reporting of skipped entities. This interface is included in SAX2 only to support legacy SAX1 applications.**

  **The order of events in this interface is very important, and mirrors the order of information in the document itself. For example, all of an element's content (character data, processing instructions, and/or subelements) will appear, in order, between the startElement event and the corresponding endElement event.**

  **Application writers who do not want to implement the entire interface can derive a class from HandlerBase, which implements the default functionality; parser writers can instantiate HandlerBase to obtain a default handler. The application can find the location of any document event using the Locator interface supplied by the Parser through the setDocumentLocator method.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser.setDocumentHandler(org.xml.sax.DocumentHandler)`](Parser.md), [`Locator`](Locator.md), [`HandlerBase`](HandlerBase.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `characters``(char[] ch, int start, int length)`<br>Deprecated. <br>Receive notification of character data.                                                 |
    | `void`            | `endDocument``()`<br>Deprecated. <br>Receive notification of the end of a document.                                                                         |
    | `void`            | `endElement``(java.lang.String name)`<br>Deprecated. <br>Receive notification of the end of an element.                                                     |
    | `void`            | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Deprecated. <br>Receive notification of ignorable whitespace in element content.               |
    | `void`            | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Deprecated. <br>Receive notification of a processing instruction.              |
    | `void`            | `setDocumentLocator``(`[`Locator`](Locator.md)` locator)`<br>Deprecated. <br>Receive an object for locating the origin of SAX document events.              |
    | `void`            | `startDocument``()`<br>Deprecated. <br>Receive notification of the beginning of a document.                                                                 |
    | `void`            | `startElement``(java.lang.String name, `[`AttributeList`](AttributeList.md)` atts)`<br>Deprecated. <br>Receive notification of the beginning of an element. |

<!-- -->

- - ### Method Detail

    - #### setDocumentLocator

          void setDocumentLocator(Locator locator)

      Deprecated. 
      Receive an object for locating the origin of SAX document events.
      SAX parsers are strongly encouraged (though not absolutely required) to supply a locator: if it does so, it must supply the locator to the application by invoking this method before invoking any of the other methods in the DocumentHandler interface.

      The locator allows the application to determine the end position of any document-related event, even if the parser is not reporting an error. Typically, the application will use this information for reporting its own errors (such as character content that does not match an application's business rules). The information returned by the locator is probably not sufficient for use with a search engine.

      Note that the locator will return correct information only during the invocation of the events in this interface. The application should not attempt to use it at any other time.

      Parameters:
      `locator` - An object that can return the location of any SAX document event.

      See Also:
      [`Locator`](Locator.md)

    <!-- -->

    - #### startDocument

          void startDocument()
                      throws SAXException

      Deprecated. 
      Receive notification of the beginning of a document.
      The SAX parser will invoke this method only once, before any other methods in this interface or in DTDHandler (except for setDocumentLocator).

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### endDocument

          void endDocument()
                    throws SAXException

      Deprecated. 
      Receive notification of the end of a document.
      The SAX parser will invoke this method only once, and it will be the last method invoked during the parse. The parser shall not invoke this method until it has either abandoned parsing (because of an unrecoverable error) or reached the end of input.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### startElement

          void startElement(java.lang.String name,
                            AttributeList atts)
                     throws SAXException

      Deprecated. 
      Receive notification of the beginning of an element.
      The Parser will invoke this method at the beginning of every element in the XML document; there will be a corresponding endElement() event for every startElement() event (even when the element is empty). All of the element's content will be reported, in order, before the corresponding endElement() event.

      If the element name has a namespace prefix, the prefix will still be attached. Note that the attribute list provided will contain only attributes with explicit values (specified or defaulted): \#IMPLIED attributes will be omitted.

      Parameters:
      `name` - The element type name.

      `atts` - The attributes attached to the element, if any.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endElement(java.lang.String)`, [`AttributeList`](AttributeList.md)

    <!-- -->

    - #### endElement

          void endElement(java.lang.String name)
                   throws SAXException

      Deprecated. 
      Receive notification of the end of an element.
      The SAX parser will invoke this method at the end of every element in the XML document; there will be a corresponding startElement() event for every endElement() event (even when the element is empty).

      If the element name has a namespace prefix, the prefix will still be attached to the name.

      Parameters:
      `name` - The element type name

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### characters

          void characters(char[] ch,
                          int start,
                          int length)
                   throws SAXException

      Deprecated. 
      Receive notification of character data.
      The Parser will call this method to report each chunk of character data. SAX parsers may return all contiguous character data in a single chunk, or they may split it into several chunks; however, all of the characters in any single event must come from the same external entity, so that the Locator provides useful information.

      The application must not attempt to read from the array outside of the specified range.

      Note that some parsers will report whitespace using the ignorableWhitespace() method rather than this one (validating parsers must do so).

      Parameters:
      `ch` - The characters from the XML document.

      `start` - The start position in the array.

      `length` - The number of characters to read from the array.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `ignorableWhitespace(char[], int, int)`, [`Locator`](Locator.md)

    <!-- -->

    - #### ignorableWhitespace

          void ignorableWhitespace(char[] ch,
                                   int start,
                                   int length)
                            throws SAXException

      Deprecated. 
      Receive notification of ignorable whitespace in element content.
      Validating Parsers must use this method to report each chunk of ignorable whitespace (see the W3C XML 1.0 recommendation, section 2.10): non-validating parsers may also use this method if they are capable of parsing and using content models.

      SAX parsers may return all contiguous whitespace in a single chunk, or they may split it into several chunks; however, all of the characters in any single event must come from the same external entity, so that the Locator provides useful information.

      The application must not attempt to read from the array outside of the specified range.

      Parameters:
      `ch` - The characters from the XML document.

      `start` - The start position in the array.

      `length` - The number of characters to read from the array.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `characters(char[], int, int)`

    <!-- -->

    - #### processingInstruction

          void processingInstruction(java.lang.String target,
                                     java.lang.String data)
                              throws SAXException

      Deprecated. 
      Receive notification of a processing instruction.
      The Parser will invoke this method once for each processing instruction found: note that processing instructions may occur before or after the main document element.

      A SAX parser should never report an XML declaration (XML 1.0, section 2.8) or a text declaration (XML 1.0, section 4.3.1) using this method.

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none was supplied.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

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

- **[Prev Class](ContentHandler.md)**
- **[Next Class](DTDHandler.md)**

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
