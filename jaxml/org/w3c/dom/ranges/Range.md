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

- **[Prev Class](DocumentRange.md)**
- **[Next Class](RangeException.md)**

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

**org.w3c.dom.ranges**

## **Interface Range**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Range

  **See also the [Document Object Model (DOM) Level 2 Traversal and Range Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                           |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static short`    | `END_TO_END`<br>Compare end boundary-point of `sourceRange` to end boundary-point of Range on which `compareBoundaryPoints` is invoked.         |
    | `static short`    | `END_TO_START`<br>Compare end boundary-point of `sourceRange` to start boundary-point of Range on which `compareBoundaryPoints` is invoked.     |
    | `static short`    | `START_TO_END`<br>Compare start boundary-point of `sourceRange` to end boundary-point of Range on which `compareBoundaryPoints` is invoked.     |
    | `static short`    | `START_TO_START`<br>Compare start boundary-point of `sourceRange` to start boundary-point of Range on which `compareBoundaryPoints` is invoked. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                          |
    |----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DocumentFragment`](../DocumentFragment.md) | `cloneContents``()`<br>Duplicates the contents of a Range                                                                                                                       |
    | `Range`                                      | `cloneRange``()`<br>Produces a new Range whose boundary-points are equal to the boundary-points of the Range.                                                                   |
    | `void`                                       | `collapse``(boolean toStart)`<br>Collapse a Range onto one of its boundary-points                                                                                               |
    | `short`                                      | `compareBoundaryPoints``(short how, Range sourceRange)`<br>Compare the boundary-points of two Ranges in a document.                                                             |
    | `void`                                       | `deleteContents``()`<br>Removes the contents of a Range from the containing document or document fragment without returning a reference to the removed content.                 |
    | `void`                                       | `detach``()`<br>Called to indicate that the Range is no longer in use and that the implementation may relinquish any resources associated with this Range.                      |
    | [`DocumentFragment`](../DocumentFragment.md) | `extractContents``()`<br>Moves the contents of a Range from the containing document or document fragment to a new DocumentFragment.                                             |
    | `boolean`                                    | `getCollapsed``()`<br>TRUE if the Range is collapsed                                                                                                                            |
    | [`Node`](../Node.md)                         | `getCommonAncestorContainer``()`<br>The deepest common ancestor container of the Range's two boundary-points.                                                                   |
    | [`Node`](../Node.md)                         | `getEndContainer``()`<br>Node within which the Range ends                                                                                                                       |
    | `int`                                        | `getEndOffset``()`<br>Offset within the ending node of the Range.                                                                                                               |
    | [`Node`](../Node.md)                         | `getStartContainer``()`<br>Node within which the Range begins                                                                                                                   |
    | `int`                                        | `getStartOffset``()`<br>Offset within the starting node of the Range.                                                                                                           |
    | `void`                                       | `insertNode``(`[`Node`](../Node.md)` newNode)`<br>Inserts a node into the Document or DocumentFragment at the start of the Range.                                               |
    | `void`                                       | `selectNode``(`[`Node`](../Node.md)` refNode)`<br>Select a node and its contents                                                                                                |
    | `void`                                       | `selectNodeContents``(`[`Node`](../Node.md)` refNode)`<br>Select the contents within a node                                                                                     |
    | `void`                                       | `setEnd``(`[`Node`](../Node.md)` refNode, int offset)`<br>Sets the attributes describing the end of a Range.                                                                    |
    | `void`                                       | `setEndAfter``(`[`Node`](../Node.md)` refNode)`<br>Sets the end of a Range to be after a node                                                                                   |
    | `void`                                       | `setEndBefore``(`[`Node`](../Node.md)` refNode)`<br>Sets the end position to be before a node.                                                                                  |
    | `void`                                       | `setStart``(`[`Node`](../Node.md)` refNode, int offset)`<br>Sets the attributes describing the start of the Range.                                                              |
    | `void`                                       | `setStartAfter``(`[`Node`](../Node.md)` refNode)`<br>Sets the start position to be after a node                                                                                 |
    | `void`                                       | `setStartBefore``(`[`Node`](../Node.md)` refNode)`<br>Sets the start position to be before a node                                                                               |
    | `void`                                       | `surroundContents``(`[`Node`](../Node.md)` newParent)`<br>Reparents the contents of the Range to the given node and inserts the node at the position of the start of the Range. |
    | `java.lang.String`                           | `toString``()`<br>Returns the contents of a Range as a string.                                                                                                                  |

<!-- -->

- - ### Field Detail

    - #### START_TO_START

          static final short START_TO_START

      Compare start boundary-point of `sourceRange` to start boundary-point of Range on which `compareBoundaryPoints` is invoked.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### START_TO_END

          static final short START_TO_END

      Compare start boundary-point of `sourceRange` to end boundary-point of Range on which `compareBoundaryPoints` is invoked.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### END_TO_END

          static final short END_TO_END

      Compare end boundary-point of `sourceRange` to end boundary-point of Range on which `compareBoundaryPoints` is invoked.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### END_TO_START

          static final short END_TO_START

      Compare end boundary-point of `sourceRange` to start boundary-point of Range on which `compareBoundaryPoints` is invoked.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getStartContainer

          Node getStartContainer()
                          throws DOMException

      Node within which the Range begins
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### getStartOffset

          int getStartOffset()
                      throws DOMException

      Offset within the starting node of the Range.
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### getEndContainer

          Node getEndContainer()
                        throws DOMException

      Node within which the Range ends
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### getEndOffset

          int getEndOffset()
                    throws DOMException

      Offset within the ending node of the Range.
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### getCollapsed

          boolean getCollapsed()
                        throws DOMException

      TRUE if the Range is collapsed
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### getCommonAncestorContainer

          Node getCommonAncestorContainer()
                                   throws DOMException

      The deepest common ancestor container of the Range's two boundary-points.
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setStart

          void setStart(Node refNode,
                        int offset)
                 throws RangeException,
                        DOMException

      Sets the attributes describing the start of the Range.
      Parameters:
      `refNode` - The `refNode` value. This parameter must be different from `null`.

      `offset` - The `startOffset` value.

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if `refNode` or an ancestor of `refNode` is an Entity, Notation, or DocumentType node.

      [`DOMException`](../DOMException.md) - INDEX_SIZE_ERR: Raised if `offset` is negative or greater than the number of child units in `refNode`. Child units are 16-bit units if `refNode` is a type of CharacterData node (e.g., a Text or Comment node) or a ProcessingInstruction node. Child units are Nodes in all other cases.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setEnd

          void setEnd(Node refNode,
                      int offset)
               throws RangeException,
                      DOMException

      Sets the attributes describing the end of a Range.
      Parameters:
      `refNode` - The `refNode` value. This parameter must be different from `null`.

      `offset` - The `endOffset` value.

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if `refNode` or an ancestor of `refNode` is an Entity, Notation, or DocumentType node.

      [`DOMException`](../DOMException.md) - INDEX_SIZE_ERR: Raised if `offset` is negative or greater than the number of child units in `refNode`. Child units are 16-bit units if `refNode` is a type of CharacterData node (e.g., a Text or Comment node) or a ProcessingInstruction node. Child units are Nodes in all other cases.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setStartBefore

          void setStartBefore(Node refNode)
                       throws RangeException,
                              DOMException

      Sets the start position to be before a node
      Parameters:
      `refNode` - Range starts before `refNode`

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if the root container of `refNode` is not an Attr, Document, or DocumentFragment node or if `refNode` is a Document, DocumentFragment, Attr, Entity, or Notation node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setStartAfter

          void setStartAfter(Node refNode)
                      throws RangeException,
                             DOMException

      Sets the start position to be after a node
      Parameters:
      `refNode` - Range starts after `refNode`

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if the root container of `refNode` is not an Attr, Document, or DocumentFragment node or if `refNode` is a Document, DocumentFragment, Attr, Entity, or Notation node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setEndBefore

          void setEndBefore(Node refNode)
                     throws RangeException,
                            DOMException

      Sets the end position to be before a node.
      Parameters:
      `refNode` - Range ends before `refNode`

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if the root container of `refNode` is not an Attr, Document, or DocumentFragment node or if `refNode` is a Document, DocumentFragment, Attr, Entity, or Notation node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### setEndAfter

          void setEndAfter(Node refNode)
                    throws RangeException,
                           DOMException

      Sets the end of a Range to be after a node
      Parameters:
      `refNode` - Range ends after `refNode`.

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if the root container of `refNode` is not an Attr, Document or DocumentFragment node or if `refNode` is a Document, DocumentFragment, Attr, Entity, or Notation node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### collapse

          void collapse(boolean toStart)
                 throws DOMException

      Collapse a Range onto one of its boundary-points
      Parameters:
      `toStart` - If TRUE, collapses the Range onto its start; if FALSE, collapses it onto its end.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### selectNode

          void selectNode(Node refNode)
                   throws RangeException,
                          DOMException

      Select a node and its contents
      Parameters:
      `refNode` - The node to select.

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if an ancestor of `refNode` is an Entity, Notation or DocumentType node or if `refNode` is a Document, DocumentFragment, Attr, Entity, or Notation node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### selectNodeContents

          void selectNodeContents(Node refNode)
                           throws RangeException,
                                  DOMException

      Select the contents within a node
      Parameters:
      `refNode` - Node to select from

      Throws:
      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if `refNode` or an ancestor of `refNode` is an Entity, Notation or DocumentType node.

      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### compareBoundaryPoints

          short compareBoundaryPoints(short how,
                                      Range sourceRange)
                               throws DOMException

      Compare the boundary-points of two Ranges in a document.
      Parameters:
      `how` - code representing the type of comparison, as defined above.

      `sourceRange` - The `Range` on which this current `Range` is compared to.

      Returns:
      -1, 0 or 1 depending on whether the corresponding boundary-point of the Range is respectively before, equal to, or after the corresponding boundary-point of `sourceRange`.

      Throws:
      [`DOMException`](../DOMException.md) - WRONG_DOCUMENT_ERR: Raised if the two Ranges are not in the same Document or DocumentFragment.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### deleteContents

          void deleteContents()
                       throws DOMException

      Removes the contents of a Range from the containing document or document fragment without returning a reference to the removed content.
      Throws:
      [`DOMException`](../DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if any portion of the content of the Range is read-only or any of the nodes that contain any of the content of the Range are read-only.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### extractContents

          DocumentFragment extractContents()
                                    throws DOMException

      Moves the contents of a Range from the containing document or document fragment to a new DocumentFragment.
      Returns:
      A DocumentFragment containing the extracted contents.

      Throws:
      [`DOMException`](../DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if any portion of the content of the Range is read-only or any of the nodes which contain any of the content of the Range are read-only.
      HIERARCHY_REQUEST_ERR: Raised if a DocumentType node would be extracted into the new DocumentFragment.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### cloneContents

          DocumentFragment cloneContents()
                                  throws DOMException

      Duplicates the contents of a Range
      Returns:
      A DocumentFragment that contains content equivalent to this Range.

      Throws:
      [`DOMException`](../DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if a DocumentType node would be extracted into the new DocumentFragment.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### insertNode

          void insertNode(Node newNode)
                   throws DOMException,
                          RangeException

      Inserts a node into the Document or DocumentFragment at the start of the Range. If the container is a Text node, this will be split at the start of the Range (as if the Text node's splitText method was performed at the insertion point) and the insertion will occur between the two resulting Text nodes. Adjacent Text nodes will not be automatically merged. If the node to be inserted is a DocumentFragment node, the children will be inserted rather than the DocumentFragment node itself.
      Parameters:
      `newNode` - The node to insert at the start of the Range

      Throws:
      [`DOMException`](../DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if an ancestor container of the start of the Range is read-only.
      WRONG_DOCUMENT_ERR: Raised if `newNode` and the container of the start of the Range were not created from the same document.
      HIERARCHY_REQUEST_ERR: Raised if the container of the start of the Range is of a type that does not allow children of the type of `newNode` or if `newNode` is an ancestor of the container.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

      [`RangeException`](RangeException.md) - INVALID_NODE_TYPE_ERR: Raised if `newNode` is an Attr, Entity, Notation, or Document node.

    <!-- -->

    - #### surroundContents

          void surroundContents(Node newParent)
                         throws DOMException,
                                RangeException

      Reparents the contents of the Range to the given node and inserts the node at the position of the start of the Range.
      Parameters:
      `newParent` - The node to surround the contents with.

      Throws:
      [`DOMException`](../DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if an ancestor container of either boundary-point of the Range is read-only.
      WRONG_DOCUMENT_ERR: Raised if `newParent` and the container of the start of the Range were not created from the same document.
      HIERARCHY_REQUEST_ERR: Raised if the container of the start of the Range is of a type that does not allow children of the type of `newParent` or if `newParent` is an ancestor of the container or if `node` would end up with a child node of a type not allowed by the type of `node`.
      INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

      [`RangeException`](RangeException.md) - BAD_BOUNDARYPOINTS_ERR: Raised if the Range partially selects a non-text node.
      INVALID_NODE_TYPE_ERR: Raised if `node` is an Attr, Entity, DocumentType, Notation, Document, or DocumentFragment node.

    <!-- -->

    - #### cloneRange

          Range cloneRange()
                    throws DOMException

      Produces a new Range whose boundary-points are equal to the boundary-points of the Range.
      Returns:
      The duplicated Range.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### toString

          java.lang.String toString()
                             throws DOMException

      Returns the contents of a Range as a string. This string contains only the data characters, not any markup.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      The contents of the Range.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

    <!-- -->

    - #### detach

          void detach()
               throws DOMException

      Called to indicate that the Range is no longer in use and that the implementation may relinquish any resources associated with this Range. Subsequent calls to any methods or attribute getters on this Range will result in a `DOMException` being thrown with an error code of `INVALID_STATE_ERR`.
      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if `detach()` has already been invoked on this object.

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

- **[Prev Class](DocumentRange.md)**
- **[Next Class](RangeException.md)**

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
