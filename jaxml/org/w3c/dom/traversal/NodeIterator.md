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

- **[Prev Class](NodeFilter.md)**
- **[Next Class](TreeWalker.md)**

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

## **Interface NodeIterator**

-

  ------------------------------------------------------------------------

  **
  **

      public interface NodeIterator

  **`Iterators` are used to step through a set of nodes, e.g. the set of nodes in a `NodeList`, the document subtree governed by a particular `Node`, the results of a query, or any other set of nodes. The set of nodes to be iterated is determined by the implementation of the `NodeIterator`. DOM Level 2 specifies a single `NodeIterator` implementation for document-order traversal of a document subtree. Instances of these iterators are created by calling `DocumentTraversal` `.createNodeIterator()`.**
  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                                |
    |-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                        | `detach``()`<br>Detaches the `NodeIterator` from the set which it iterated over, releasing any computational resources and placing the iterator in the INVALID state. |
    | `boolean`                     | `getExpandEntityReferences``()`<br>The value of this flag determines whether the children of entity reference nodes are visible to the iterator.                      |
    | [`NodeFilter`](NodeFilter.md) | `getFilter``()`<br>The `NodeFilter` used to screen nodes.                                                                                                             |
    | [`Node`](../Node.md)          | `getRoot``()`<br>The root node of the `NodeIterator`, as specified when it was created.                                                                               |
    | `int`                         | `getWhatToShow``()`<br>This attribute determines which node types are presented via the iterator.                                                                     |
    | [`Node`](../Node.md)          | `nextNode``()`<br>Returns the next node in the set and advances the position of the iterator in the set.                                                              |
    | [`Node`](../Node.md)          | `previousNode``()`<br>Returns the previous node in the set and moves the position of the `NodeIterator` backwards in the set.                                         |

<!-- -->

- - ### Method Detail

    - #### getRoot

          Node getRoot()

      The root node of the `NodeIterator`, as specified when it was created.

    <!-- -->

    - #### getWhatToShow

          int getWhatToShow()

      This attribute determines which node types are presented via the iterator. The available set of constants is defined in the `NodeFilter` interface. Nodes not accepted by `whatToShow` will be skipped, but their children may still be considered. Note that this skip takes precedence over the filter, if any.

    <!-- -->

    - #### getFilter

          NodeFilter getFilter()

      The `NodeFilter` used to screen nodes.

    <!-- -->

    - #### getExpandEntityReferences

          boolean getExpandEntityReferences()

      The value of this flag determines whether the children of entity reference nodes are visible to the iterator. If false, they and their descendants will be rejected. Note that this rejection takes precedence over `whatToShow` and the filter. Also note that this is currently the only situation where `NodeIterators` may reject a complete subtree rather than skipping individual nodes.

      To produce a view of the document that has entity references expanded and does not expose the entity reference node itself, use the `whatToShow` flags to hide the entity reference node and set `expandEntityReferences` to true when creating the iterator. To produce a view of the document that has entity reference nodes but no entity expansion, use the `whatToShow` flags to show the entity reference node and set `expandEntityReferences` to false.

    <!-- -->

    - #### nextNode

          Node nextNode()
                 throws DOMException

      Returns the next node in the set and advances the position of the iterator in the set. After a `NodeIterator` is created, the first call to `nextNode()` returns the first node in the set.
      Returns:
      The next `Node` in the set being iterated over, or `null` if there are no more members in that set.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if this method is called after the `detach` method was invoked.

    <!-- -->

    - #### previousNode

          Node previousNode()
                     throws DOMException

      Returns the previous node in the set and moves the position of the `NodeIterator` backwards in the set.
      Returns:
      The previous `Node` in the set being iterated over, or `null` if there are no more members in that set.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if this method is called after the `detach` method was invoked.

    <!-- -->

    - #### detach

          void detach()

      Detaches the `NodeIterator` from the set which it iterated over, releasing any computational resources and placing the iterator in the INVALID state. After `detach` has been invoked, calls to `nextNode` or `previousNode` will raise the exception INVALID_STATE_ERR.

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

- **[Prev Class](NodeFilter.md)**
- **[Next Class](TreeWalker.md)**

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
