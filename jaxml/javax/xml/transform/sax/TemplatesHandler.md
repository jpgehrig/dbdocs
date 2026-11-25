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

- **[Prev Class](SAXTransformerFactory.md)**
- **[Next Class](TransformerHandler.md)**

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

## **Interface TemplatesHandler**

- **All Superinterfaces:**
  **[ContentHandler](../../../../org/xml/sax/ContentHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface TemplatesHandler
      extends ContentHandler

  **A SAX ContentHandler that may be used to process SAX parse events (parsing transformation instructions) into a Templates object.**
  **Note that TemplatesHandler does not need to implement LexicalHandler.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type              | Method and Description                                                                                                                                                                                                            |
    |--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`             | `getSystemId``()`<br>Get the base ID (URI or system ID) from where relative URLs will be resolved.                                                                                                                                |
    | [`Templates`](../Templates.md) | `getTemplates``()`<br>When a TemplatesHandler object is used as a ContentHandler for the parsing of transformation instructions, it creates a Templates object, which the caller can get once the SAX events have been completed. |
    | `void`                         | `setSystemId``(java.lang.String systemID)`<br>Set the base ID (URI or system ID) for the Templates object created by this builder.                                                                                                |

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md)

      [`characters`](../../../../org/xml/sax/ContentHandler.md)`, `[`endDocument`](../../../../org/xml/sax/ContentHandler.md)`, `[`endElement`](../../../../org/xml/sax/ContentHandler.md)`, `[`endPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/ContentHandler.md)`, `[`processingInstruction`](../../../../org/xml/sax/ContentHandler.md)`, `[`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md)`, `[`skippedEntity`](../../../../org/xml/sax/ContentHandler.md)`, `[`startDocument`](../../../../org/xml/sax/ContentHandler.md)`, `[`startElement`](../../../../org/xml/sax/ContentHandler.md)`, `[`startPrefixMapping`](../../../../org/xml/sax/ContentHandler.md)

<!-- -->

- - ### Method Detail

    - #### getTemplates

          Templates getTemplates()

      When a TemplatesHandler object is used as a ContentHandler for the parsing of transformation instructions, it creates a Templates object, which the caller can get once the SAX events have been completed.
      Returns:
      The Templates object that was created during the SAX event process, or null if no Templates object has been created.

    <!-- -->

    - #### setSystemId

          void setSystemId(java.lang.String systemID)

      Set the base ID (URI or system ID) for the Templates object created by this builder. This must be set in order to resolve relative URIs in the stylesheet. This must be called before the startDocument event.
      Parameters:
      `systemID` - Base URI for this stylesheet.

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      Get the base ID (URI or system ID) from where relative URLs will be resolved.
      Returns:
      The systemID that was set with `setSystemId(java.lang.String)`.

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

- **[Prev Class](SAXTransformerFactory.md)**
- **[Next Class](TransformerHandler.md)**

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
