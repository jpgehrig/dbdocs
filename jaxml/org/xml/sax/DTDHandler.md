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

- **[Prev Class](DocumentHandler.md)**
- **[Next Class](EntityResolver.md)**

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

## **Interface DTDHandler**

- **All Known Subinterfaces:**
  **[TransformerHandler](../../../javax/xml/transform/sax/TransformerHandler.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[CXMLHandlerBase](../../../oracle/xml/comp/CXMLHandlerBase.md), [DefaultHandler](helpers/DefaultHandler.md), [DefaultXMLDocumentHandler](../../../oracle/xml/parser/v2/DefaultXMLDocumentHandler.md), [DocumentBuilder](../../../oracle/xml/parser/v2/DocumentBuilder.md), [HandlerBase](HandlerBase.md), [XMLFilterImpl](helpers/XMLFilterImpl.md), [XMLSAXSerializer](../../../oracle/xml/parser/v2/XMLSAXSerializer.md), [XMLTokenizer](../../../oracle/xml/parser/v2/XMLTokenizer.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DTDHandler

  **Receive notification of basic DTD-related events.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **If a SAX application needs information about notations and unparsed entities, then the application implements this interface and registers an instance with the SAX parser using the parser's setDTDHandler method. The parser uses the instance to report notation and unparsed entity declarations to the application.**

  **Note that this interface includes only those DTD events that the XML recommendation *requires* processors to report: notation and unparsed entity declarations.**

  **The SAX parser may report these events in any order, regardless of the order in which the notations and unparsed entities were declared; however, all DTD events must be reported after the document handler's startDocument event, and before the first startElement event.**

  **It is up to the application to store the information for future use (perhaps in a hash table or object tree). If the application encounters attributes of type "NOTATION", "ENTITY", or "ENTITIES", it can use the information that it obtained through this interface to find the entity and/or notation corresponding with the attribute value.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser.setDTDHandler(org.xml.sax.DTDHandler)`](Parser.md), [`HandlerBase`](HandlerBase.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                              |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `notationDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Receive notification of a notation declaration event.                                              |
    | `void`            | `unparsedEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId, java.lang.String notationName)`<br>Receive notification of an unparsed entity declaration event. |

<!-- -->

- - ### Method Detail

    - #### notationDecl

          void notationDecl(java.lang.String name,
                            java.lang.String publicId,
                            java.lang.String systemId)
                     throws SAXException

      Receive notification of a notation declaration event.
      It is up to the application to record the notation for later reference, if necessary.

      At least one of publicId and systemId must be non-null. If a system identifier is present, and it is a URL, the SAX parser must resolve it fully before passing it to the application through this event.

      There is no guarantee that the notation declaration will be reported before any unparsed entities that use it.

      Parameters:
      `name` - The notation name.

      `publicId` - The notation's public identifier, or null if none was given.

      `systemId` - The notation's system identifier, or null if none was given.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`, [`AttributeList`](AttributeList.md)

    <!-- -->

    - #### unparsedEntityDecl

          void unparsedEntityDecl(java.lang.String name,
                                  java.lang.String publicId,
                                  java.lang.String systemId,
                                  java.lang.String notationName)
                           throws SAXException

      Receive notification of an unparsed entity declaration event.
      Note that the notation name corresponds to a notation reported by the `notationDecl` event. It is up to the application to record the entity for later reference, if necessary.

      If the system identifier is a URL, the parser must resolve it fully before passing it to the application.

      Parameters:
      `name` - The unparsed entity's name.

      `publicId` - The entity's public identifier, or null if none was given.

      `systemId` - The entity's system identifier.

      `notationName` - The name of the associated notation.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `notationDecl(java.lang.String, java.lang.String, java.lang.String)`, [`AttributeList`](AttributeList.md)

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

- **[Prev Class](DocumentHandler.md)**
- **[Next Class](EntityResolver.md)**

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
