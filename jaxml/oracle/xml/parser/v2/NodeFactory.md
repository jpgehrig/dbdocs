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

- **[Prev Class](ElementDecl.md)**
- **[Next Class](NodeReadHandler.md)**

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

## **Class NodeFactory**

- **java.lang.Object**

- - **oracle.xml.parser.v2.NodeFactory**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class NodeFactory
      extends java.lang.Object
      implements java.io.Serializable

  **This class specifies methods to create various nodes of the DOM tree built during parsing. Applications can override these methods to create their own custom classes to be added to the DOM tree while parsing. Applications have to register their own NodeFactory using the DOMParser's setNodeFactory() method. If a null pointer is returned by these methods, then the node will not be added to the DOM tree.**
  **See Also:**
  **[`DOMParser.setNodeFactory(oracle.xml.parser.v2.NodeFactory)`](DOMParser.md), [Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                              |
    |----------------------------------------------------------|
    | `NodeFactory``()`<br>Default constructor for NodeFactory |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                                                 |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLAttr`](XMLAttr.md)                         | `createAttribute``(java.lang.String tag, java.lang.String text)`<br>Creates an attribute node with the specified tag, and text.                                                                                                                        |
    | [`XMLAttr`](XMLAttr.md)                         | `createAttributeNS``(java.lang.String localName, java.lang.String prefix, java.lang.String namespaceURI, java.lang.String value)`<br>Creates an attribute node with the specified tag, and text.                                                       |
    | [`XMLCDATA`](XMLCDATA.md)                       | `createCDATASection``(java.lang.String text)`<br>Creates a CDATA node with the specified text.                                                                                                                                                         |
    | [`XMLComment`](XMLComment.md)                   | `createComment``(java.lang.String text)`<br>Creates a comment node with the specified text.                                                                                                                                                            |
    | [`XMLDocument`](XMLDocument.md)                 | `createDocument``()`<br>Creates a document node.                                                                                                                                                                                                       |
    | [`XMLDocumentFragment`](XMLDocumentFragment.md) | `createDocumentFragment``()`<br>Creates a document fragment node.                                                                                                                                                                                      |
    | [`XMLElement`](XMLElement.md)                   | `createElement``(java.lang.String tag)`<br>Creates an Element node with the specified tag.                                                                                                                                                             |
    | [`XMLElement`](XMLElement.md)                   | `createElementNS``(java.lang.String localName, java.lang.String prefix, java.lang.String namespaceURI)`<br>Creates an Element node with the specified local name,prefix , namespaceURI.                                                                |
    | [`XMLEntityReference`](XMLEntityReference.md)   | `createEntityReference``(java.lang.String tag)`<br>Creates an entity reference node with the specified tag.                                                                                                                                            |
    | [`XMLPI`](XMLPI.md)                             | `createProcessingInstruction``(java.lang.String tag, java.lang.String text)`<br>Creates a PI node with the specified tag, and text.                                                                                                                    |
    | [`XMLText`](XMLText.md)                         | `createTextNode``(java.lang.String text)`<br>Creates a text node with the specified text.                                                                                                                                                              |
    | `boolean`                                       | `isNamespaceAware``()`<br>Check if the NodeFactory is namespace aware If TRUE, createElementNS(localName, prefix, namespaceURI) and createAttributeNS(localName, prefix, namespaceURI, value) functions will be used to create Element and Attr nodes. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NodeFactory

          public NodeFactory()

      Default constructor for NodeFactory

  <!-- -->

  - ### Method Detail

    - #### isNamespaceAware

          public boolean isNamespaceAware()

      Check if the NodeFactory is namespace aware If TRUE, createElementNS(localName, prefix, namespaceURI) and createAttributeNS(localName, prefix, namespaceURI, value) functions will be used to create Element and Attr nodes. The default is FALSE, to keep backward compatibilty. Subclasses must override this function and return 'true' to create namespace aware nodes.
      Returns:
      \- boolean - namespace awareness

    <!-- -->

    - #### createDocument

          public XMLDocument createDocument()

      Creates a document node. This method cannot return a null pointer.
      Returns:
      The created document

    <!-- -->

    - #### createElement

          public XMLElement createElement(java.lang.String tag)

      Creates an Element node with the specified tag.
      Parameters:
      `tag` - The name of the element.

      Returns:
      The created element.

    <!-- -->

    - #### createElementNS

          public XMLElement createElementNS(java.lang.String localName,
                                            java.lang.String prefix,
                                            java.lang.String namespaceURI)

      Creates an Element node with the specified local name,prefix , namespaceURI.
      Parameters:
      `localName` - the name of the element

      `prefix` - the prefix of the element,

      `namespaceURI` - the namespace of the element

      Returns:
      The created element.

    <!-- -->

    - #### createTextNode

          public XMLText createTextNode(java.lang.String text)

      Creates a text node with the specified text.
      Parameters:
      `text` - The text associated with the node.

      Returns:
      The created text node.

    <!-- -->

    - #### createCDATASection

          public XMLCDATA createCDATASection(java.lang.String text)

      Creates a CDATA node with the specified text.
      Parameters:
      `text` - The text associated with the node.

      Returns:
      The created CDATA node.

    <!-- -->

    - #### createComment

          public XMLComment createComment(java.lang.String text)

      Creates a comment node with the specified text.
      Parameters:
      `text` - The text associated with the node.

      Returns:
      The created comment node.

    <!-- -->

    - #### createProcessingInstruction

          public XMLPI createProcessingInstruction(java.lang.String tag,
                                                   java.lang.String text)

      Creates a PI node with the specified tag, and text.
      Parameters:
      `tag` - The name of the node.

      `text` - The text associated with the node.

      Returns:
      The created PI node.

    <!-- -->

    - #### createAttribute

          public XMLAttr createAttribute(java.lang.String tag,
                                         java.lang.String text)

      Creates an attribute node with the specified tag, and text.
      Parameters:
      `tag` - The name of the node.

      `text` - The text associated with the node.

      Returns:
      The created attribute node.

    <!-- -->

    - #### createAttributeNS

          public XMLAttr createAttributeNS(java.lang.String localName,
                                           java.lang.String prefix,
                                           java.lang.String namespaceURI,
                                           java.lang.String value)

      Creates an attribute node with the specified tag, and text.
      Parameters:
      `localName` - the name of the node.

      `prefix` - the prefix of the node.

      `namespaceURI` - the namespace of the node

      `value` - The value associated with the node.

      Returns:
      The created attribute node.

    <!-- -->

    - #### createDocumentFragment

          public XMLDocumentFragment createDocumentFragment()

      Creates a document fragment node.
      Returns:
      The created document fragment node.

    <!-- -->

    - #### createEntityReference

          public XMLEntityReference createEntityReference(java.lang.String tag)

      Creates an entity reference node with the specified tag.
      Parameters:
      `tag` - The name of the node.

      Returns:
      The created entity reference node.

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

- **[Prev Class](ElementDecl.md)**
- **[Next Class](NodeReadHandler.md)**

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
