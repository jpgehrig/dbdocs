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

- **Prev Class**
- **[Next Class](BinXMLEncoder.md)**

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

**oracle.xml.binxml**

## **Interface BinXMLDecoder**

-

  ------------------------------------------------------------------------

  **
  **

      public interface BinXMLDecoder

  **The interface for converting a binary stream into XML. The XML can be pushed out to a ContentHandler using SAX or pulled using XMLStreamReader.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                      |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `decode``(`[`ContentHandler`](../../../org/xml/sax/ContentHandler.md)` cntHdlr, `[`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)` errHdlr)`<br>Decode and output XML SAX events to the cntHdlr and errors to errHdlr |
    | [`InfosetReader`](../scalable/InfosetReader.md) | `getReader``()`<br>Returns object for reading the decoded XML in pull style                                                                                                                                                 |
    | [`BinXMLSerializer`](BinXMLSerializer.md)       | `getSerializer``()`<br>Returns object for pull style serialization                                                                                                                                                          |
    | `void`                                          | `setDeclHandler``(`[`DeclHandler`](../../../org/xml/sax/ext/DeclHandler.md)` hdlr)`<br>Specify the handler to receive decoded DTD declaration events                                                                        |
    | `void`                                          | `setDTDHandler``(`[`DTDHandler`](../../../org/xml/sax/DTDHandler.md)` hdlr)`<br>Specify the handler to receive decoded DTD events                                                                                           |
    | `void`                                          | `setGUID``(byte[] guid)`<br>set BinXMLDecoder GUID                                                                                                                                                                          |
    | `void`                                          | `setLexicalHandler``(`[`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)` hdlr)`<br>Specify the handler to receive decoded events for comments and CDATA section boundaries                                     |

<!-- -->

- - ### Method Detail

    - #### decode

          void decode(ContentHandler cntHdlr,
                      ErrorHandler errHdlr)
               throws BinXMLException

      Decode and output XML SAX events to the cntHdlr and errors to errHdlr
      Parameters:
      `cntHdlr` - Content handler for SAX events

      `errHdlr` - for handling errors

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### setDTDHandler

          void setDTDHandler(DTDHandler hdlr)

      Specify the handler to receive decoded DTD events
      Parameters:
      `hdlr` - handler for decoded DTD events

    <!-- -->

    - #### setDeclHandler

          void setDeclHandler(DeclHandler hdlr)

      Specify the handler to receive decoded DTD declaration events
      Parameters:
      `hdlr` - handler for decoded DTD declaration events

    <!-- -->

    - #### setLexicalHandler

          void setLexicalHandler(LexicalHandler hdlr)

      Specify the handler to receive decoded events for comments and CDATA section boundaries
      Parameters:
      `hdlr` - lexical handler to be used during decoding

    <!-- -->

    - #### getReader

          InfosetReader getReader()
                           throws BinXMLException

      Returns object for reading the decoded XML in pull style
      Returns:
      object for pull style reading of decoded XML

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getSerializer

          BinXMLSerializer getSerializer()

      Returns object for pull style serialization
      Returns:
      serializer for decoded xml

    <!-- -->

    - #### setGUID

          void setGUID(byte[] guid)

      set BinXMLDecoder GUID
      Parameters:
      `guid` -

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

- **Prev Class**
- **[Next Class](BinXMLEncoder.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
