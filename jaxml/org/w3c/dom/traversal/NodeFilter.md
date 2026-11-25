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

- **[Prev Class](DocumentTraversal.md)**
- **[Next Class](NodeIterator.md)**

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

**org.w3c.dom.traversal**

## **Interface NodeFilter**

- **All Known Subinterfaces:**
  **[LSSerializerFilter](../ls/LSSerializerFilter.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NodeFilter

  **Filters are objects that know how to "filter out" nodes. If a `NodeIterator` or `TreeWalker` is given a `NodeFilter`, it applies the filter before it returns the next node. If the filter says to accept the node, the traversal logic returns it; otherwise, traversal looks for the next node and pretends that the node that was rejected was not there.**
  **The DOM does not provide any filters. `NodeFilter` is just an interface that users can implement to provide their own filters.**

  **`NodeFilters` do not need to know how to traverse from node to node, nor do they need to know anything about the data structure that is being traversed. This makes it very easy to write filters, since the only thing they have to know how to do is evaluate a single node. One filter may be used with a number of different kinds of traversals, encouraging code reuse.**

  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                |
    |-------------------|----------------------------------------------------------------------|
    | `static short`    | `FILTER_ACCEPT`<br>Accept the node.                                  |
    | `static short`    | `FILTER_REJECT`<br>Reject the node.                                  |
    | `static short`    | `FILTER_SKIP`<br>Skip this single node.                              |
    | `static int`      | `SHOW_ALL`<br>Show all `Nodes`.                                      |
    | `static int`      | `SHOW_ATTRIBUTE`<br>Show `Attr` nodes.                               |
    | `static int`      | `SHOW_CDATA_SECTION`<br>Show `CDATASection` nodes.                   |
    | `static int`      | `SHOW_COMMENT`<br>Show `Comment` nodes.                              |
    | `static int`      | `SHOW_DOCUMENT`<br>Show `Document` nodes.                            |
    | `static int`      | `SHOW_DOCUMENT_FRAGMENT`<br>Show `DocumentFragment` nodes.           |
    | `static int`      | `SHOW_DOCUMENT_TYPE`<br>Show `DocumentType` nodes.                   |
    | `static int`      | `SHOW_ELEMENT`<br>Show `Element` nodes.                              |
    | `static int`      | `SHOW_ENTITY`<br>Show `Entity` nodes.                                |
    | `static int`      | `SHOW_ENTITY_REFERENCE`<br>Show `EntityReference` nodes.             |
    | `static int`      | `SHOW_NOTATION`<br>Show `Notation` nodes.                            |
    | `static int`      | `SHOW_PROCESSING_INSTRUCTION`<br>Show `ProcessingInstruction` nodes. |
    | `static int`      | `SHOW_TEXT`<br>Show `Text` nodes.                                    |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                        |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`           | `acceptNode``(`[`Node`](../Node.md)` n)`<br>Test whether a specified node is visible in the logical view of a `TreeWalker` or `NodeIterator`. |

<!-- -->

- - ### Field Detail

    - #### FILTER_ACCEPT

          static final short FILTER_ACCEPT

      Accept the node. Navigation methods defined for `NodeIterator` or `TreeWalker` will return this node.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FILTER_REJECT

          static final short FILTER_REJECT

      Reject the node. Navigation methods defined for `NodeIterator` or `TreeWalker` will not return this node. For `TreeWalker`, the children of this node will also be rejected. `NodeIterators` treat this as a synonym for `FILTER_SKIP`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FILTER_SKIP

          static final short FILTER_SKIP

      Skip this single node. Navigation methods defined for `NodeIterator` or `TreeWalker` will not return this node. For both `NodeIterator` and `TreeWalker`, the children of this node will still be considered.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_ALL

          static final int SHOW_ALL

      Show all `Nodes`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_ELEMENT

          static final int SHOW_ELEMENT

      Show `Element` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_ATTRIBUTE

          static final int SHOW_ATTRIBUTE

      Show `Attr` nodes. This is meaningful only when creating an iterator or tree-walker with an attribute node as its `root`; in this case, it means that the attribute node will appear in the first position of the iteration or traversal. Since attributes are never children of other nodes, they do not appear when traversing over the document tree.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_TEXT

          static final int SHOW_TEXT

      Show `Text` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_CDATA_SECTION

          static final int SHOW_CDATA_SECTION

      Show `CDATASection` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_ENTITY_REFERENCE

          static final int SHOW_ENTITY_REFERENCE

      Show `EntityReference` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_ENTITY

          static final int SHOW_ENTITY

      Show `Entity` nodes. This is meaningful only when creating an iterator or tree-walker with an `Entity` node as its `root`; in this case, it means that the `Entity` node will appear in the first position of the traversal. Since entities are not part of the document tree, they do not appear when traversing over the document tree.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_PROCESSING_INSTRUCTION

          static final int SHOW_PROCESSING_INSTRUCTION

      Show `ProcessingInstruction` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_COMMENT

          static final int SHOW_COMMENT

      Show `Comment` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_DOCUMENT

          static final int SHOW_DOCUMENT

      Show `Document` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_DOCUMENT_TYPE

          static final int SHOW_DOCUMENT_TYPE

      Show `DocumentType` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_DOCUMENT_FRAGMENT

          static final int SHOW_DOCUMENT_FRAGMENT

      Show `DocumentFragment` nodes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_NOTATION

          static final int SHOW_NOTATION

      Show `Notation` nodes. This is meaningful only when creating an iterator or tree-walker with a `Notation` node as its `root`; in this case, it means that the `Notation` node will appear in the first position of the traversal. Since notations are not part of the document tree, they do not appear when traversing over the document tree.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### acceptNode

          short acceptNode(Node n)

      Test whether a specified node is visible in the logical view of a `TreeWalker` or `NodeIterator`. This function will be called by the implementation of `TreeWalker` and `NodeIterator`; it is not normally called directly from user code. (Though you could do so if you wanted to use the same filter to guide your own application logic.)
      Parameters:
      `n` - The node to check to see if it passes the filter or not.

      Returns:
      a constant to determine whether the node is accepted, rejected, or skipped, as defined above.

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

- **[Prev Class](DocumentTraversal.md)**
- **[Next Class](NodeIterator.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
