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

- **[Prev Class](oraxsl.md)**
- **[Next Class](SAXAttrList.md)**

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

## **Interface PrintDriver**

- **All Known Implementing Classes:**
  **[XMLPrintDriver](XMLPrintDriver.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface PrintDriver

  **The `PrintDriver` defines methods used to print XML documents represented as DOM trees.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                              |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Closes the output stream or print writer                                                                             |
    | `void`            | `flush``()`<br>Flushes the output stream or print writer                                                                            |
    | `void`            | `printAttribute``(`[`XMLAttr`](XMLAttr.md)` attr)`<br>Prints a `XMLAttr` node                                                       |
    | `void`            | `printAttributeNodes``(`[`XMLElement`](XMLElement.md)` elem)`<br>Calls print method for each attribute of the `XMLElement`          |
    | `void`            | `printCDATASection``(`[`XMLCDATA`](XMLCDATA.md)` cdata)`<br>Prints a `XMLCDATA` node                                                |
    | `void`            | `printChildNodes``(`[`XMLNode`](XMLNode.md)` node)`<br>Calls print method for each child of the `XMLNode`                           |
    | `void`            | `printComment``(`[`XMLComment`](XMLComment.md)` comment)`<br>Prints a `XMLComment` node                                             |
    | `void`            | `printDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Prints an `DTD`.                                                                         |
    | `void`            | `printDocument``(`[`XMLDocument`](XMLDocument.md)` doc)`<br>Prints an `XMLDocument`.                                                |
    | `void`            | `printDocumentFragment``(`[`XMLDocumentFragment`](XMLDocumentFragment.md)` dfrag)`<br>Prints an empty `XMLDocumentFragment` object. |
    | `void`            | `printElement``(`[`XMLElement`](XMLElement.md)` elem)`<br>Prints an `XMLElement`.                                                   |
    | `void`            | `printEntityReference``(`[`XMLEntityReference`](XMLEntityReference.md)` en)`<br>Prints a `XMLEntityReference` node                  |
    | `void`            | `printProcessingInstruction``(`[`XMLPI`](XMLPI.md)` pi)`<br>Prints a `XMLPI` node                                                   |
    | `void`            | `printTextNode``(`[`XMLText`](XMLText.md)` text)`<br>Prints a `XMLText` node                                                        |
    | `void`            | `setEncoding``(java.lang.String enc)`<br>Sets the encoding of the print driver.                                                     |

<!-- -->

- - ### Method Detail

    - #### setEncoding

          void setEncoding(java.lang.String enc)
                    throws java.io.IOException

      Sets the encoding of the print driver.
      Parameters:
      `enc` - The encoding of the document being printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDoctype

          void printDoctype(DTD dtd)
                     throws java.io.IOException

      Prints an `DTD`.
      Parameters:
      `dtd` - The dtd to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDocument

          void printDocument(XMLDocument doc)
                      throws java.io.IOException

      Prints an `XMLDocument`.
      Parameters:
      `doc` - The document to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printElement

          void printElement(XMLElement elem)
                     throws java.io.IOException

      Prints an `XMLElement`.
      Parameters:
      `elem` - The element to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDocumentFragment

          void printDocumentFragment(XMLDocumentFragment dfrag)
                              throws java.io.IOException

      Prints an empty `XMLDocumentFragment` object.
      Parameters:
      `dfrag` - The document fragment to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printTextNode

          void printTextNode(XMLText text)
                      throws java.io.IOException

      Prints a `XMLText` node
      Parameters:
      `text` - The text node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printComment

          void printComment(XMLComment comment)
                     throws java.io.IOException

      Prints a `XMLComment` node
      Parameters:
      `comment` - The comment node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printCDATASection

          void printCDATASection(XMLCDATA cdata)
                          throws java.io.IOException

      Prints a `XMLCDATA` node
      Parameters:
      `cdata` - The XMLCDATA node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printProcessingInstruction

          void printProcessingInstruction(XMLPI pi)
                                   throws java.io.IOException

      Prints a `XMLPI` node
      Parameters:
      `pi` - The XMLPI node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printAttribute

          void printAttribute(XMLAttr attr)
                       throws java.io.IOException

      Prints a `XMLAttr` node
      Parameters:
      `attr` - The XMLAttr node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printEntityReference

          void printEntityReference(XMLEntityReference en)
                             throws java.io.IOException

      Prints a `XMLEntityReference` node
      Parameters:
      `en` - The XMLEntityReference node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printChildNodes

          void printChildNodes(XMLNode node)
                        throws java.io.IOException

      Calls print method for each child of the `XMLNode`
      Parameters:
      `node` - The node whose children are to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printAttributeNodes

          void printAttributeNodes(XMLElement elem)
                            throws java.io.IOException

      Calls print method for each attribute of the `XMLElement`
      Parameters:
      `elem` - The elem whose attributes are to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flush

          void flush()
              throws java.io.IOException

      Flushes the output stream or print writer
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### close

          void close()
              throws java.io.IOException

      Closes the output stream or print writer
      Throws:
      `java.io.IOException`

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

- **[Prev Class](oraxsl.md)**
- **[Next Class](SAXAttrList.md)**

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
