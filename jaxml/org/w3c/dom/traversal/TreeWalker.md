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

- **[Prev Class](NodeIterator.md)**
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

**org.w3c.dom.traversal**

## **Interface TreeWalker**

-

  ------------------------------------------------------------------------

  **
  **

      public interface TreeWalker

  **`TreeWalker` objects are used to navigate a document tree or subtree using the view of the document defined by their `whatToShow` flags and filter (if any). Any function which performs navigation using a `TreeWalker` will automatically support any view defined by a `TreeWalker`.**
  **Omitting nodes from the logical view of a subtree can result in a structure that is substantially different from the same subtree in the complete, unfiltered document. Nodes that are siblings in the `TreeWalker` view may be children of different, widely separated nodes in the original view. For instance, consider a `NodeFilter` that skips all nodes except for Text nodes and the root node of a document. In the logical view that results, all text nodes will be siblings and appear as direct children of the root node, no matter how deeply nested the structure of the original document.**

  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                               |
    |-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../Node.md)          | `firstChild``()`<br>Moves the `TreeWalker` to the first visible child of the current node, and returns the new node.                                 |
    | [`Node`](../Node.md)          | `getCurrentNode``()`<br>The node at which the `TreeWalker` is currently positioned.                                                                  |
    | `boolean`                     | `getExpandEntityReferences``()`<br>The value of this flag determines whether the children of entity reference nodes are visible to the `TreeWalker`. |
    | [`NodeFilter`](NodeFilter.md) | `getFilter``()`<br>The filter used to screen nodes.                                                                                                  |
    | [`Node`](../Node.md)          | `getRoot``()`<br>The `root` node of the `TreeWalker`, as specified when it was created.                                                              |
    | `int`                         | `getWhatToShow``()`<br>This attribute determines which node types are presented via the `TreeWalker`.                                                |
    | [`Node`](../Node.md)          | `lastChild``()`<br>Moves the `TreeWalker` to the last visible child of the current node, and returns the new node.                                   |
    | [`Node`](../Node.md)          | `nextNode``()`<br>Moves the `TreeWalker` to the next visible node in document order relative to the current node, and returns the new node.          |
    | [`Node`](../Node.md)          | `nextSibling``()`<br>Moves the `TreeWalker` to the next sibling of the current node, and returns the new node.                                       |
    | [`Node`](../Node.md)          | `parentNode``()`<br>Moves to and returns the closest visible ancestor node of the current node.                                                      |
    | [`Node`](../Node.md)          | `previousNode``()`<br>Moves the `TreeWalker` to the previous visible node in document order relative to the current node, and returns the new node.  |
    | [`Node`](../Node.md)          | `previousSibling``()`<br>Moves the `TreeWalker` to the previous sibling of the current node, and returns the new node.                               |
    | `void`                        | `setCurrentNode``(`[`Node`](../Node.md)` currentNode)`                                                                                               |

<!-- -->

- - ### Method Detail

    - #### getRoot

          Node getRoot()

      The `root` node of the `TreeWalker`, as specified when it was created.

    <!-- -->

    - #### getWhatToShow

          int getWhatToShow()

      This attribute determines which node types are presented via the `TreeWalker`. The available set of constants is defined in the `NodeFilter` interface. Nodes not accepted by `whatToShow` will be skipped, but their children may still be considered. Note that this skip takes precedence over the filter, if any.

    <!-- -->

    - #### getFilter

          NodeFilter getFilter()

      The filter used to screen nodes.

    <!-- -->

    - #### getExpandEntityReferences

          boolean getExpandEntityReferences()

      The value of this flag determines whether the children of entity reference nodes are visible to the `TreeWalker`. If false, they and their descendants will be rejected. Note that this rejection takes precedence over `whatToShow` and the filter, if any.
      To produce a view of the document that has entity references expanded and does not expose the entity reference node itself, use the `whatToShow` flags to hide the entity reference node and set `expandEntityReferences` to true when creating the `TreeWalker`. To produce a view of the document that has entity reference nodes but no entity expansion, use the `whatToShow` flags to show the entity reference node and set `expandEntityReferences` to false.

    <!-- -->

    - #### getCurrentNode

          Node getCurrentNode()

      The node at which the `TreeWalker` is currently positioned.
      Alterations to the DOM tree may cause the current node to no longer be accepted by the `TreeWalker`'s associated filter. `currentNode` may also be explicitly set to any node, whether or not it is within the subtree specified by the `root` node or would be accepted by the filter and `whatToShow` flags. Further traversal occurs relative to `currentNode` even if it is not part of the current view, by applying the filters in the requested direction; if no traversal is possible, `currentNode` is not changed.
      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if an attempt is made to set `currentNode` to `null`.

    <!-- -->

    - #### setCurrentNode

          void setCurrentNode(Node currentNode)
                       throws DOMException

      Throws:
      [`DOMException`](../DOMException.md)

    <!-- -->

    - #### parentNode

          Node parentNode()

      Moves to and returns the closest visible ancestor node of the current node. If the search for `parentNode` attempts to step upward from the `TreeWalker`'s `root` node, or if it fails to find a visible ancestor node, this method retains the current position and returns `null`.
      Returns:
      The new parent node, or `null` if the current node has no parent in the `TreeWalker`'s logical view.

    <!-- -->

    - #### firstChild

          Node firstChild()

      Moves the `TreeWalker` to the first visible child of the current node, and returns the new node. If the current node has no visible children, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no visible children in the `TreeWalker`'s logical view.

    <!-- -->

    - #### lastChild

          Node lastChild()

      Moves the `TreeWalker` to the last visible child of the current node, and returns the new node. If the current node has no visible children, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no children in the `TreeWalker`'s logical view.

    <!-- -->

    - #### previousSibling

          Node previousSibling()

      Moves the `TreeWalker` to the previous sibling of the current node, and returns the new node. If the current node has no visible previous sibling, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no previous sibling. in the `TreeWalker`'s logical view.

    <!-- -->

    - #### nextSibling

          Node nextSibling()

      Moves the `TreeWalker` to the next sibling of the current node, and returns the new node. If the current node has no visible next sibling, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no next sibling. in the `TreeWalker`'s logical view.

    <!-- -->

    - #### previousNode

          Node previousNode()

      Moves the `TreeWalker` to the previous visible node in document order relative to the current node, and returns the new node. If the current node has no previous node, or if the search for `previousNode` attempts to step upward from the `TreeWalker`'s `root` node, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no previous node in the `TreeWalker`'s logical view.

    <!-- -->

    - #### nextNode

          Node nextNode()

      Moves the `TreeWalker` to the next visible node in document order relative to the current node, and returns the new node. If the current node has no next node, or if the search for nextNode attempts to step upward from the `TreeWalker`'s `root` node, returns `null`, and retains the current node.
      Returns:
      The new node, or `null` if the current node has no next node in the `TreeWalker`'s logical view.

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

- **[Prev Class](NodeIterator.md)**
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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
