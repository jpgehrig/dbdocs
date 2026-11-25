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

- **[Prev Class](DeclHandler.md)**
- **[Next Class](Locator2.md)**

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

**org.xml.sax.ext**

## **Interface LexicalHandler**

- **All Known Subinterfaces:**
  **[TransformerHandler](../../../../javax/xml/transform/sax/TransformerHandler.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[CXMLHandlerBase](../../../../oracle/xml/comp/CXMLHandlerBase.md), [DocumentBuilder](../../../../oracle/xml/parser/v2/DocumentBuilder.md), [XMLSAXSerializer](../../../../oracle/xml/parser/v2/XMLSAXSerializer.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface LexicalHandler

  **SAX2 extension handler for lexical events.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This is an optional extension handler for SAX2 to provide lexical information about an XML document, such as comments and CDATA section boundaries; XML readers are not required to support this handler, and it is not part of the core SAX2 distribution.**

  **The events in the lexical handler apply to the entire document, not just to the document element, and all lexical handler events must appear between the content handler's startDocument and endDocument events.**

  **To set the LexicalHandler for an XML reader, use the [`setProperty`](../XMLReader.md) method with the propertyId "http://xml.org/sax/properties/lexical-handler". If the reader does not support lexical events, it will throw a [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) or a [`SAXNotSupportedException`](../SAXNotSupportedException.md) when you attempt to register the handler.**

  **Since:**
  **1.0**

  **See Also:**
  **[`XMLReader.setProperty(java.lang.String, java.lang.Object)`](../XMLReader.md), [`SAXNotRecognizedException`](../SAXNotRecognizedException.md), [`SAXNotSupportedException`](../SAXNotSupportedException.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `comment``(char[] ch, int start, int length)`<br>Report an XML comment anywhere in the document.                                           |
    | `void`            | `endCDATA``()`<br>Report the end of a CDATA section.                                                                                       |
    | `void`            | `endDTD``()`<br>Report the end of DTD declarations.                                                                                        |
    | `void`            | `endEntity``(java.lang.String name)`<br>Report the end of an entity.                                                                       |
    | `void`            | `startCDATA``()`<br>Report the start of a CDATA section.                                                                                   |
    | `void`            | `startDTD``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Report the start of DTD declarations, if any. |
    | `void`            | `startEntity``(java.lang.String name)`<br>Report the beginning of some internal and external XML entities.                                 |

<!-- -->

- - ### Method Detail

    - #### startDTD

          void startDTD(java.lang.String name,
                        java.lang.String publicId,
                        java.lang.String systemId)
                 throws SAXException

      Report the start of DTD declarations, if any.
      This method is intended to report the beginning of the DOCTYPE declaration; if the document has no DOCTYPE declaration, this method will not be invoked.

      All declarations reported through [`DTDHandler`](../DTDHandler.md) or [`DeclHandler`](DeclHandler.md) events must appear between the startDTD and `endDTD` events. Declarations are assumed to belong to the internal DTD subset unless they appear between `startEntity` and `endEntity` events. Comments and processing instructions from the DTD should also be reported between the startDTD and endDTD events, in their original order of (logical) occurrence; they are not required to appear in their correct locations relative to DTDHandler or DeclHandler events, however.

      Note that the start/endDTD events will appear within the start/endDocument events from ContentHandler and before the first [`startElement`](../ContentHandler.md) event.

      Parameters:
      `name` - The document type name.

      `publicId` - The declared public identifier for the external DTD subset, or null if none was declared.

      `systemId` - The declared system identifier for the external DTD subset, or null if none was declared.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `endDTD()`, `startEntity(java.lang.String)`

    <!-- -->

    - #### endDTD

          void endDTD()
               throws SAXException

      Report the end of DTD declarations.
      This method is intended to report the end of the DOCTYPE declaration; if the document has no DOCTYPE declaration, this method will not be invoked.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `startDTD(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### startEntity

          void startEntity(java.lang.String name)
                    throws SAXException

      Report the beginning of some internal and external XML entities.
      The reporting of parameter entities (including the external DTD subset) is optional, and SAX2 drivers that support LexicalHandler may not support it; you can use the `http://xml.org/sax/features/lexical-handler/parameter-entities` feature to query or control the reporting of parameter entities.

      General entities are reported with their regular names, parameter entities have '%' prepended to their names, and the external DTD subset has the pseudo-entity name "\[dtd\]".

      When a SAX2 driver is providing these events, all other events must be properly nested within start/end entity events. There is no additional requirement that events from [`DeclHandler`](DeclHandler.md) or [`DTDHandler`](../DTDHandler.md) be properly ordered.

      Note that skipped entities will be reported through the [`skippedEntity`](../ContentHandler.md) event, which is part of the ContentHandler interface.

      Because of the streaming event model that SAX uses, some entity boundaries cannot be reported under any circumstances:

      - general entities within attribute values
      - parameter entities within declarations

      These will be silently expanded, with no indication of where the original entity boundaries were.

      Note also that the boundaries of character references (which are not really entities anyway) are not reported.

      All start/endEntity events must be properly nested.

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%', and if it is the external DTD subset, it will be "\[dtd\]".

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `endEntity(java.lang.String)`, [`DeclHandler.internalEntityDecl(java.lang.String, java.lang.String)`](DeclHandler.md), [`DeclHandler.externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`](DeclHandler.md)

    <!-- -->

    - #### endEntity

          void endEntity(java.lang.String name)
                  throws SAXException

      Report the end of an entity.
      Parameters:
      `name` - The name of the entity that is ending.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `startEntity(java.lang.String)`

    <!-- -->

    - #### startCDATA

          void startCDATA()
                   throws SAXException

      Report the start of a CDATA section.
      The contents of the CDATA section will be reported through the regular [`characters`](../ContentHandler.md) event; this event is intended only to report the boundary.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `endCDATA()`

    <!-- -->

    - #### endCDATA

          void endCDATA()
                 throws SAXException

      Report the end of a CDATA section.
      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `startCDATA()`

    <!-- -->

    - #### comment

          void comment(char[] ch,
                       int start,
                       int length)
                throws SAXException

      Report an XML comment anywhere in the document.
      This callback will be used for comments inside or outside the document element, including comments in the external DTD subset (if read). Comments in the DTD must be properly nested inside start/endDTD and start/endEntity events (if used).

      Parameters:
      `ch` - An array holding the characters in the comment.

      `start` - The starting position in the array.

      `length` - The number of characters to use from the array.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

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

- **[Prev Class](DeclHandler.md)**
- **[Next Class](Locator2.md)**

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
