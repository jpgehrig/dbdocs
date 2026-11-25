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

- **Prev Class**
- **[Next Class](NodeFilter.md)**

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

## **Interface DocumentTraversal**

- **All Known Implementing Classes:**
  **[XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DocumentTraversal

  **`DocumentTraversal` contains methods that create iterators and tree-walkers to traverse a node and its children in document order (depth first, pre-order traversal, which is equivalent to the order in which the start tags occur in the text representation of the document). In DOMs which support the Traversal feature, `DocumentTraversal` will be implemented by the same objects that implement the Document interface.**
  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                      |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NodeIterator`](NodeIterator.md) | `createNodeIterator``(`[`Node`](../Node.md)` root, int whatToShow, `[`NodeFilter`](NodeFilter.md)` filter, boolean entityReferenceExpansion)`<br>Create a new `NodeIterator` over the subtree rooted at the specified node. |
    | [`TreeWalker`](TreeWalker.md)     | `createTreeWalker``(`[`Node`](../Node.md)` root, int whatToShow, `[`NodeFilter`](NodeFilter.md)` filter, boolean entityReferenceExpansion)`<br>Create a new `TreeWalker` over the subtree rooted at the specified node.     |

<!-- -->

- - ### Method Detail

    - #### createNodeIterator

          NodeIterator createNodeIterator(Node root,
                                          int whatToShow,
                                          NodeFilter filter,
                                          boolean entityReferenceExpansion)
                                   throws DOMException

      Create a new `NodeIterator` over the subtree rooted at the specified node.
      Parameters:
      `root` - The node which will be iterated together with its children. The iterator is initially positioned just before this node. The `whatToShow` flags and the filter, if any, are not considered when setting this position. The root must not be `null`.

      `whatToShow` - This flag specifies which node types may appear in the logical view of the tree presented by the iterator. See the description of `NodeFilter` for the set of possible `SHOW_` values.These flags can be combined using `OR`.

      `filter` - The `NodeFilter` to be used with this `TreeWalker`, or `null` to indicate no filter.

      `entityReferenceExpansion` - The value of this flag determines whether entity reference nodes are expanded.

      Returns:
      The newly created `NodeIterator`.

      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the specified `root` is `null`.

    <!-- -->

    - #### createTreeWalker

          TreeWalker createTreeWalker(Node root,
                                      int whatToShow,
                                      NodeFilter filter,
                                      boolean entityReferenceExpansion)
                               throws DOMException

      Create a new `TreeWalker` over the subtree rooted at the specified node.
      Parameters:
      `root` - The node which will serve as the `root` for the `TreeWalker`. The `whatToShow` flags and the `NodeFilter` are not considered when setting this value; any node type will be accepted as the `root`. The `currentNode` of the `TreeWalker` is initialized to this node, whether or not it is visible. The `root` functions as a stopping point for traversal methods that look upward in the document structure, such as `parentNode` and nextNode. The `root` must not be `null`.

      `whatToShow` - This flag specifies which node types may appear in the logical view of the tree presented by the tree-walker. See the description of `NodeFilter` for the set of possible SHOW\_ values.These flags can be combined using `OR`.

      `filter` - The `NodeFilter` to be used with this `TreeWalker`, or `null` to indicate no filter.

      `entityReferenceExpansion` - If this flag is false, the contents of `EntityReference` nodes are not presented in the logical view.

      Returns:
      The newly created `TreeWalker`.

      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the specified `root` is `null`.

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

- **Prev Class**
- **[Next Class](NodeFilter.md)**

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
