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

- **[Prev Class](XMLPI.md)**
- **[Next Class](XMLSAXSerializer.md)**

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

## **Class XMLPrintDriver**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLPrintDriver**

<!-- -->

- **All Implemented Interfaces:**
  **[PrintDriver](PrintDriver.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLPrintDriver
      extends java.lang.Object
      implements PrintDriver

  **The `XMLPrintDriver` implements `PrintDriver` interface.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                           |
    |-------------------------------------------------------------------------------------------------------|
    | `XMLPrintDriver``(java.io.OutputStream os)`<br>Create a new PrintDriver to output XML to OutputStream |
    | `XMLPrintDriver``(java.io.PrintWriter pw)`<br>Create a new PrintDriver to output XML to PrintWriter   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                  |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Closes the output stream or print writer.                                                                                                |
    | `void`            | `close``(int option)`<br>Closes the output stream or print writer based on option Legal values are: XMLOutputStream.REUSE and XMLOutputStream.NO_REUSE. |
    | `void`            | `flush``()`<br>Flushes the output stream or print writer                                                                                                |
    | `void`            | `printAttribute``(`[`XMLAttr`](XMLAttr.md)` attr)`<br>Prints a `XMLAttr` node                                                                           |
    | `void`            | `printAttributeNodes``(`[`XMLElement`](XMLElement.md)` elem)`<br>Calls print method for each attribute of the `XMLElement`                              |
    | `void`            | `printCDATASection``(`[`XMLCDATA`](XMLCDATA.md)` cdata)`<br>Prints a `XMLCDATA` node                                                                    |
    | `void`            | `printChildNodes``(`[`XMLNode`](XMLNode.md)` node)`<br>Calls print method for each child of the `XMLNode`                                               |
    | `void`            | `printComment``(`[`XMLComment`](XMLComment.md)` comment)`<br>Prints a `XMLComment` node                                                                 |
    | `void`            | `printDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Prints an `DTD`.                                                                                             |
    | `void`            | `printDocument``(`[`XMLDocument`](XMLDocument.md)` doc)`<br>Prints an `XMLDocument`.                                                                    |
    | `void`            | `printDocumentFragment``(`[`XMLDocumentFragment`](XMLDocumentFragment.md)` dfrag)`<br>Prints an empty `XMLDocumentFragment` object.                     |
    | `void`            | `printElement``(`[`XMLElement`](XMLElement.md)` elem)`<br>Prints an `XMLElement`.                                                                       |
    | `void`            | `printEntityReference``(`[`XMLEntityReference`](XMLEntityReference.md)` en)`<br>Prints a `XMLEntityReference` node                                      |
    | `void`            | `printNode``(`[`XMLNode`](XMLNode.md)` node)`                                                                                                           |
    | `void`            | `printProcessingInstruction``(`[`XMLPI`](XMLPI.md)` pi)`<br>Prints a `XMLPI` node                                                                       |
    | `void`            | `printTextNode``(`[`XMLText`](XMLText.md)` text)`<br>Prints a `XMLText` node                                                                            |
    | `void`            | `setEncoding``(java.lang.String enc)`<br>Sets the encoding of the print driver.                                                                         |
    | `void`            | `setFormatPrettyPrint``(boolean val)`<br>Sets the pretty format print                                                                                   |
    | `void`            | `setPrintInheritedNamespaces``(boolean val)`<br>Sets print inherited namespaces.                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLPrintDriver

          public XMLPrintDriver(java.io.PrintWriter pw)

      Create a new PrintDriver to output XML to PrintWriter
      Parameters:
      `pw` - - PrintWriter to use for output

    <!-- -->

    - #### XMLPrintDriver

          public XMLPrintDriver(java.io.OutputStream os)

      Create a new PrintDriver to output XML to OutputStream
      Parameters:
      `os` - - OutputStream to use for output

  <!-- -->

  - ### Method Detail

    - #### setEncoding

          public void setEncoding(java.lang.String enc)
                           throws java.io.IOException

      Sets the encoding of the print driver.
      Specified by:
      [`setEncoding`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `enc` - The encoding of the document being printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### setFormatPrettyPrint

          public void setFormatPrettyPrint(boolean val)

      Sets the pretty format print
      Parameters:
      `val` - boolean value

    <!-- -->

    - #### setPrintInheritedNamespaces

          public void setPrintInheritedNamespaces(boolean val)

      Sets print inherited namespaces. When printting an element this parameter constrols if all inherited namespaces will be printed or not.
      Parameters:
      `val` - boolean - true to print all inherited namespaces, false to omit inherited namespace

    <!-- -->

    - #### printNode

          public void printNode(XMLNode node)
                         throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDoctype

          public void printDoctype(DTD dtd)
                            throws java.io.IOException

      Prints an `DTD`.
      Specified by:
      [`printDoctype`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `dtd` - The dtd to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDocument

          public void printDocument(XMLDocument doc)
                             throws java.io.IOException

      Prints an `XMLDocument`.
      Specified by:
      [`printDocument`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `doc` - The document to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printElement

          public void printElement(XMLElement elem)
                            throws java.io.IOException

      Prints an `XMLElement`.
      Specified by:
      [`printElement`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `elem` - The element to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printDocumentFragment

          public void printDocumentFragment(XMLDocumentFragment dfrag)
                                     throws java.io.IOException

      Prints an empty `XMLDocumentFragment` object.
      Specified by:
      [`printDocumentFragment`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `dfrag` - The document fragment to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printTextNode

          public void printTextNode(XMLText text)
                             throws java.io.IOException

      Prints a `XMLText` node
      Specified by:
      [`printTextNode`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `text` - The text node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printComment

          public void printComment(XMLComment comment)
                            throws java.io.IOException

      Prints a `XMLComment` node
      Specified by:
      [`printComment`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `comment` - The comment node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printCDATASection

          public void printCDATASection(XMLCDATA cdata)
                                 throws java.io.IOException

      Prints a `XMLCDATA` node
      Specified by:
      [`printCDATASection`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `cdata` - The XMLCDATA node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printProcessingInstruction

          public void printProcessingInstruction(XMLPI pi)
                                          throws java.io.IOException

      Prints a `XMLPI` node
      Specified by:
      [`printProcessingInstruction`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `pi` - The XMLPI node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printAttribute

          public void printAttribute(XMLAttr attr)
                              throws java.io.IOException

      Prints a `XMLAttr` node
      Specified by:
      [`printAttribute`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `attr` - The XMLAttr node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printEntityReference

          public void printEntityReference(XMLEntityReference en)
                                    throws java.io.IOException

      Prints a `XMLEntityReference` node
      Specified by:
      [`printEntityReference`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `en` - The XMLEntityReference node.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printChildNodes

          public final void printChildNodes(XMLNode node)
                                     throws java.io.IOException

      Calls print method for each child of the `XMLNode`
      Specified by:
      [`printChildNodes`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `node` - The node whose children are to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printAttributeNodes

          public final void printAttributeNodes(XMLElement elem)
                                         throws java.io.IOException

      Calls print method for each attribute of the `XMLElement`
      Specified by:
      [`printAttributeNodes`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Parameters:
      `elem` - The elem whose attributes are to be printed.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flush

          public void flush()
                     throws java.io.IOException

      Flushes the output stream or print writer
      Specified by:
      [`flush`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### close

          public void close()
                     throws java.io.IOException

      Closes the output stream or print writer. Migrate to close(int option).
      Specified by:
      [`close`](PrintDriver.md) in interface [`PrintDriver`](PrintDriver.md)

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### close

          public void close(int option)
                     throws java.io.IOException

      Closes the output stream or print writer based on option Legal values are: XMLOutputStream.REUSE and XMLOutputStream.NO_REUSE.
      Parameters:
      `option` - determines whether output stream or print writer has to be closed.

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

- **[Prev Class](XMLPI.md)**
- **[Next Class](XMLSAXSerializer.md)**

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
