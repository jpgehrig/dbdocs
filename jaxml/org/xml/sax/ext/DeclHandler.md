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

- **Prev Class**
- **[Next Class](LexicalHandler.md)**

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

## **Interface DeclHandler**

- **All Known Implementing Classes:**
  **[DocumentBuilder](../../../../oracle/xml/parser/v2/DocumentBuilder.md), [XMLSAXSerializer](../../../../oracle/xml/parser/v2/XMLSAXSerializer.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DeclHandler

  **SAX2 extension handler for DTD declaration events.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This is an optional extension handler for SAX2 to provide information about DTD declarations in an XML document. XML readers are not required to support this handler, and this handler is not included in the core SAX2 distribution.**

  **Note that data-related DTD declarations (unparsed entities and notations) are already reported through the [`DTDHandler`](../DTDHandler.md) interface.**

  **If you are using the declaration handler together with a lexical handler, all of the events will occur between the [`startDTD`](LexicalHandler.md) and the [`endDTD`](LexicalHandler.md) events.**

  **To set the DeclHandler for an XML reader, use the [`setProperty`](../XMLReader.md) method with the propertyId "http://xml.org/sax/properties/declaration-handler". If the reader does not support declaration events, it will throw a [`SAXNotRecognizedException`](../SAXNotRecognizedException.md) or a [`SAXNotSupportedException`](../SAXNotSupportedException.md) when you attempt to register the handler.**

  **Since:**
  **1.0**

  **See Also:**
  **[`XMLReader`](../XMLReader.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                   |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `attributeDecl``(java.lang.String eName, java.lang.String aName, java.lang.String type, java.lang.String valueDefault, java.lang.String value)`<br>Report an attribute type declaration. |
    | `void`            | `elementDecl``(java.lang.String name, java.lang.String model)`<br>Report an element type declaration.                                                                                    |
    | `void`            | `externalEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Report a parsed external entity declaration.                                      |
    | `void`            | `internalEntityDecl``(java.lang.String name, java.lang.String value)`<br>Report an internal entity declaration.                                                                          |

<!-- -->

- - ### Method Detail

    - #### elementDecl

          void elementDecl(java.lang.String name,
                           java.lang.String model)
                    throws SAXException

      Report an element type declaration.
      The content model will consist of the string "EMPTY", the string "ANY", or a parenthesised group, optionally followed by an occurrence indicator. The model will be normalized so that all parameter entities are fully resolved and all whitespace is removed,and will include the enclosing parentheses. Other normalization (such as removing redundant parentheses or simplifying occurrence indicators) is at the discretion of the parser.

      Parameters:
      `name` - The element type name.

      `model` - The content model as a normalized string.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### attributeDecl

          void attributeDecl(java.lang.String eName,
                             java.lang.String aName,
                             java.lang.String type,
                             java.lang.String valueDefault,
                             java.lang.String value)
                      throws SAXException

      Report an attribute type declaration.
      Only the effective (first) declaration for an attribute will be reported. The type will be one of the strings "CDATA", "ID", "IDREF", "IDREFS", "NMTOKEN", "NMTOKENS", "ENTITY", "ENTITIES", a parenthesized token group with the separator "\|" and all whitespace removed, or the word "NOTATION" followed by a space followed by a parenthesized token group with all whitespace removed.

      Any parameter entities in the attribute value will be expanded, but general entities will not.

      Parameters:
      `eName` - The name of the associated element.

      `aName` - The name of the attribute.

      `type` - A string representing the attribute type.

      `valueDefault` - A string representing the attribute default ("#IMPLIED", "#REQUIRED", or "#FIXED") or null if none of these applies.

      `value` - A string representing the attribute's default value, or null if there is none.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### internalEntityDecl

          void internalEntityDecl(java.lang.String name,
                                  java.lang.String value)
                           throws SAXException

      Report an internal entity declaration.
      Only the effective (first) declaration for each entity will be reported. All parameter entities in the value will be expanded, but general entities will not.

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `value` - The replacement text of the entity.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

    <!-- -->

    - #### externalEntityDecl

          void externalEntityDecl(java.lang.String name,
                                  java.lang.String publicId,
                                  java.lang.String systemId)
                           throws SAXException

      Report a parsed external entity declaration.
      Only the effective (first) declaration for each entity will be reported.

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `publicId` - The declared public identifier of the entity, or null if none was declared.

      `systemId` - The declared system identifier of the entity.

      Throws:
      [`SAXException`](../SAXException.md) - The application may raise an exception.

      See Also:
      `internalEntityDecl(java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../DTDHandler.md)

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

- **Prev Class**
- **[Next Class](LexicalHandler.md)**

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
