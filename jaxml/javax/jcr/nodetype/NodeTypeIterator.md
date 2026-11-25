Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NodeType.md)**
- **[Next Class](NodeTypeManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**javax.jcr.nodetype**

## **Interface NodeTypeIterator**

- **All Superinterfaces:**
  **java.util.Iterator, [RangeIterator](../RangeIterator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NodeTypeIterator
      extends RangeIterator

  **An iterator for `NodeType` objects.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                              |
    |---------------------------|---------------------------------------------------------------------|
    | [`NodeType`](NodeType.md) | `nextNodeType``()`<br>Returns the next `NodeType` in the iteration. |

    - ### Methods inherited from interface javax.jcr.[RangeIterator](../RangeIterator.md)

      [`getPosition`](../RangeIterator.md)`, `[`getSize`](../RangeIterator.md)`, `[`skip`](../RangeIterator.md)

    <!-- -->

    - ### Methods inherited from interface java.util.Iterator

      `forEachRemaining, hasNext, next, remove`

<!-- -->

- - ### Method Detail

    - #### nextNodeType

          NodeType nextNodeType()

      Returns the next `NodeType` in the iteration.
      Returns:
      the next `NodeType` in the iteration.

      Throws:
      `java.util.NoSuchElementException` - if iteration has no more `NodeType`s.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NodeType.md)**
- **[Next Class](NodeTypeManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
