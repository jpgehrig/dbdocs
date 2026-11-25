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

- **[Prev Class](DOMResult.md)**
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

**javax.xml.transform.dom**

## **Class DOMSource**

- **java.lang.Object**

- - **javax.xml.transform.dom.DOMSource**

<!-- -->

- **All Implemented Interfaces:**
  **[Source](../Source.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DOMSource
      extends java.lang.Object
      implements Source

  **Acts as a holder for a transformation Source tree in the form of a Document Object Model (DOM) tree.**
  **See Also:**
  **[Document Object Model (DOM) Level 2 Specification](http://www.w3.org/TR/DOM-Level-2)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                 |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Source input of this type. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DOMSource``()`<br>Zero-argument default constructor.                                                                                                                                           |
    | `DOMSource``(`[`Node`](../../../../org/w3c/dom/Node.md)` n)`<br>Create a new input source with a DOM node.                                                                                      |
    | `DOMSource``(`[`Node`](../../../../org/w3c/dom/Node.md)` node, java.lang.String systemID)`<br>Create a new input source with a DOM node, and with the system ID also passed in as the base URI. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                |
    |-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getNode``()`<br>Get the node that represents a Source DOM tree.                                                      |
    | `java.lang.String`                        | `getSystemId``()`<br>Get the base ID (URL or system ID) from where URLs will be resolved.                             |
    | `void`                                    | `setNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` node)`<br>Set the node that will represents a Source DOM tree. |
    | `void`                                    | `setSystemId``(java.lang.String baseID)`<br>Set the base ID (URL or system ID) from where URLs will be resolved.      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Source input of this type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### DOMSource

          public DOMSource()

      Zero-argument default constructor. If this is used, and no DOM source is set, then the Transformer will create an empty source Document using [`DocumentBuilder.newDocument()`](../../parsers/DocumentBuilder.md).

    <!-- -->

    - #### DOMSource

          public DOMSource(Node n)

      Create a new input source with a DOM node. The operation will be applied to the subtree rooted at this node. In XSLT, a "/" pattern still means the root of the tree (not the subtree), and the evaluation of global variables and parameters is done from the root node also.
      Parameters:
      `n` - The DOM node that will contain the Source tree.

    <!-- -->

    - #### DOMSource

          public DOMSource(Node node,
                           java.lang.String systemID)

      Create a new input source with a DOM node, and with the system ID also passed in as the base URI.
      Parameters:
      `node` - The DOM node that will contain the Source tree.

      `systemID` - Specifies the base URI associated with node.

  <!-- -->

  - ### Method Detail

    - #### setNode

          public void setNode(Node node)

      Set the node that will represents a Source DOM tree.
      Parameters:
      `node` - The node that is to be transformed.

    <!-- -->

    - #### getNode

          public Node getNode()

      Get the node that represents a Source DOM tree.
      Returns:
      The node that is to be transformed.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String baseID)

      Set the base ID (URL or system ID) from where URLs will be resolved.
      Specified by:
      [`setSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Parameters:
      `baseID` - Base URL for this DOM tree.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the base ID (URL or system ID) from where URLs will be resolved.
      Specified by:
      [`getSystemId`](../Source.md) in interface [`Source`](../Source.md)

      Returns:
      Base URL for this DOM tree.

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

- **[Prev Class](DOMResult.md)**
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
