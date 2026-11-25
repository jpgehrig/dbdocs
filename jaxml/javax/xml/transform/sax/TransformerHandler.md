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

- **[Prev Class](TemplatesHandler.md)**
- **Next Class**

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

**javax.xml.transform.sax**

## **Interface TransformerHandler**

- **All Superinterfaces:**
  **[ContentHandler](../../../../org/xml/sax/ContentHandler.md), [DTDHandler](../../../../org/xml/sax/DTDHandler.md), [LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface TransformerHandler
      extends ContentHandler, LexicalHandler, DTDHandler

  **A TransformerHandler listens for SAX ContentHandler parse events and transforms them to a Result.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                  | Method and Description                                                                                                                              |
    |------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                 | `getSystemId``()`<br>Get the base ID (URI or system ID) from where relative URLs will be resolved.                                                  |
    | [`Transformer`](../Transformer.md) | `getTransformer``()`<br>Get the Transformer associated with this handler, which is needed in order to set parameters and output properties.         |
    | `void`                             | `setResult``(`[`Result`](../Result.md)` result)`<br>Enables the user of the TransformerHandler to set the to set the Result for the transformation. |
    | `void`                             | `setSystemId``(java.lang.String systemID)`<br>Set the base ID (URI or system ID) from where relative URLs will be resolved.                         |

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md)

      [`characters`](../../../../org/xml/sax/ContentHandler.md)`, `[`endDocument`](../../../../org/xml/sax/ContentHandler.md)`, `[`endElement`](../../../../org/xml/sax/ContentHandler.md)`, `[`endPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/ContentHandler.md)`, `[`processingInstruction`](../../../../org/xml/sax/ContentHandler.md)`, `[`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md)`, `[`skippedEntity`](../../../../org/xml/sax/ContentHandler.md)`, `[`startDocument`](../../../../org/xml/sax/ContentHandler.md)`, `[`startElement`](../../../../org/xml/sax/ContentHandler.md)`, `[`startPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.ext.[LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md)

      [`comment`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`endCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`endDTD`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`endEntity`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`startCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`startDTD`](../../../../org/xml/sax/ext/LexicalHandler.md)`, `[`startEntity`](../../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[DTDHandler](../../../../org/xml/sax/DTDHandler.md)

      [`notationDecl`](../../../../org/xml/sax/DTDHandler.md)`, `[`unparsedEntityDecl`](../../../../org/xml/sax/DTDHandler.md)

<!-- -->

- - ### Method Detail

    - #### setResult

          void setResult(Result result)
                  throws java.lang.IllegalArgumentException

      Enables the user of the TransformerHandler to set the to set the Result for the transformation.
      Parameters:
      `result` - A Result instance, should not be null.

      Throws:
      `java.lang.IllegalArgumentException` - if result is invalid for some reason.

    <!-- -->

    - #### setSystemId

          void setSystemId(java.lang.String systemID)

      Set the base ID (URI or system ID) from where relative URLs will be resolved.
      Parameters:
      `systemID` - Base URI for the source tree.

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      Get the base ID (URI or system ID) from where relative URLs will be resolved.
      Returns:
      The systemID that was set with `setSystemId(java.lang.String)`.

    <!-- -->

    - #### getTransformer

          Transformer getTransformer()

      Get the Transformer associated with this handler, which is needed in order to set parameters and output properties.

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

- **[Prev Class](TemplatesHandler.md)**
- **Next Class**

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
