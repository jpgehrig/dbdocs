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

- **[Prev Class](DOMLocator.md)**
- **[Next Class](DOMSource.md)**

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

## **Class DOMResult**

- **java.lang.Object**

- - **javax.xml.transform.dom.DOMResult**

<!-- -->

- **All Implemented Interfaces:**
  **[Result](../Result.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DOMResult
      extends java.lang.Object
      implements Result

  **Acts as a holder for a transformation result tree, in the form of a Document Object Model (DOM) tree. If no output DOM source is set, the transformation will create a Document node as the holder for the result of the transformation, which may be retrieved with getNode.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                  |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type. |

    -

      ### **Fields inherited from interface javax.xml.transform.[Result](../Result.md)**

      **[`PI_DISABLE_OUTPUT_ESCAPING`](../Result.md)`, `[`PI_ENABLE_OUTPUT_ESCAPING`](../Result.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------|
    | `DOMResult``()`<br>Zero-argument default constructor.                                                                                     |
    | `DOMResult``(`[`Node`](../../../../org/w3c/dom/Node.md)` node)`<br>Use a DOM node to create a new output target.                          |
    | `DOMResult``(`[`Node`](../../../../org/w3c/dom/Node.md)` node, java.lang.String systemID)`<br>Create a new output target with a DOM node. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                           |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getNode``()`<br>Get the node that will contain the result DOM tree.                                                             |
    | `java.lang.String`                        | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.                                                    |
    | `void`                                    | `setNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` node)`<br>Set the node that will contain the result DOM tree.             |
    | `void`                                    | `setSystemId``(java.lang.String systemId)`<br>Method setSystemId Set the systemID that may be used in association with the node. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### DOMResult

          public DOMResult()

      Zero-argument default constructor.

    <!-- -->

    - #### DOMResult

          public DOMResult(Node node)

      Use a DOM node to create a new output target. In practice, the node should be a [`Document`](../../../../org/w3c/dom/Document.md) node, a [`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md) node, or a [`Element`](../../../../org/w3c/dom/Element.md) node. In other words, a node that accepts children.
      Parameters:
      `node` - The DOM node that will contain the result tree.

    <!-- -->

    - #### DOMResult

          public DOMResult(Node node,
                           java.lang.String systemID)

      Create a new output target with a DOM node. In practice, the node should be a [`Document`](../../../../org/w3c/dom/Document.md) node, a [`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md) node, or a [`Element`](../../../../org/w3c/dom/Element.md) node. In other words, a node that accepts children.
      Parameters:
      `node` - The DOM node that will contain the result tree.

      `systemID` - The system identifier which may be used in association with this node.

  <!-- -->

  - ### Method Detail

    - #### setNode

          public void setNode(Node node)

      Set the node that will contain the result DOM tree. In practice, the node should be a [`Document`](../../../../org/w3c/dom/Document.md) node, a [`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md) node, or a [`Element`](../../../../org/w3c/dom/Element.md) node. In other words, a node that accepts children.
      Parameters:
      `node` - The node to which the transformation will be appended.

    <!-- -->

    - #### getNode

          public Node getNode()

      Get the node that will contain the result DOM tree. If no node was set via setNode, the node will be set by the transformation, and may be obtained from this method once the transformation is complete.
      Returns:
      The node to which the transformation will be appended.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Method setSystemId Set the systemID that may be used in association with the node.
      Specified by:
      [`setSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Parameters:
      `systemId` - The system identifier as a URI string.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier that was set with setSystemId.
      Specified by:
      [`getSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Returns:
      The system identifier that was set with setSystemId, or null if setSystemId was not called.

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

- **[Prev Class](DOMLocator.md)**
- **[Next Class](DOMSource.md)**

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
