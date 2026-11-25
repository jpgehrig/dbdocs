Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ItemNotFoundException.md)**
- **[Next Class](LoginException.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**javax.jcr**

## **Interface ItemVisitor**

- **All Known Implementing Classes:**
  **[TraversingItemVisitor](util/TraversingItemVisitor.md), [TraversingItemVisitor.Default](util/TraversingItemVisitor.Default.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ItemVisitor

  **This interface defines two signatures of the `visit` method; one taking a `Node`, the other a `Property`. When an object implementing this interface is passed to [`Item.accept(ItemVisitor visitor)`](Item.md) the appropriate `visit` method is automatically called, depending on whether the `Item` in question is a `Node` or a `Property`. Different implementations of this interface can be written for different purposes. It is, for example, possible for the `visit(Node node)` method to call `accept` on the children of the passed node and thus recurse through the tree performing some operation on each `Item`.**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `visit``(`[`Node`](Node.md)` node)`<br>This method is called when the `ItemVisitor` is passed to the `accept` method of a `Node`.                 |
    | `void`            | `visit``(`[`Property`](Property.md)` property)`<br>This method is called when the `ItemVisitor` is passed to the `accept` method of a `Property`. |

<!-- -->

- - ### Method Detail

    - #### visit

          void visit(Property property)
              throws RepositoryException

      This method is called when the `ItemVisitor` is passed to the `accept` method of a `Property`. If this method throws an exception the visiting process is aborted.
      Parameters:
      `property` - The `Property` that is accepting this visitor.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurrs

    <!-- -->

    - #### visit

          void visit(Node node)
              throws RepositoryException

      This method is called when the `ItemVisitor` is passed to the `accept` method of a `Node`. If this method throws an exception the visiting process is aborted.
      Parameters:
      `node` - The `Node`

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurrs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ItemNotFoundException.md)**
- **[Next Class](LoginException.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
