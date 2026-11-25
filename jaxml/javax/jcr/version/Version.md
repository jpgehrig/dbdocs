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

- **[Prev Class](OnParentVersionAction.md)**
- **[Next Class](VersionException.md)**

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

**javax.jcr.version**

## **Interface Version**

- **All Superinterfaces:**
  **[Item](../Item.md), [Node](../Node.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Version
      extends Node

  **A `Version` object wraps an `nt:version` node. It provides convenient access to version information.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                   |
    |---------------------------------------|------------------------------------------------------------------------------------------|
    | [`VersionHistory`](VersionHistory.md) | `getContainingHistory``()`<br>Returns the `VersionHistory` that contains this `Version`. |
    | `java.util.Calendar`                  | `getCreated``()`<br>Returns the date this version was created.                           |
    | `Version[]`                           | `getPredecessors``()`<br>Returns the predecessor versions of this version.               |
    | `Version[]`                           | `getSuccessors``()`<br>Returns the successor versions of this version.                   |

    - ### Methods inherited from interface javax.jcr.[Node](../Node.md)

      [`addMixin`](../Node.md)`, `[`addNode`](../Node.md)`, `[`addNode`](../Node.md)`, `[`canAddMixin`](../Node.md)`, `[`cancelMerge`](../Node.md)`, `[`checkin`](../Node.md)`, `[`checkout`](../Node.md)`, `[`doneMerge`](../Node.md)`, `[`getBaseVersion`](../Node.md)`, `[`getCorrespondingNodePath`](../Node.md)`, `[`getDefinition`](../Node.md)`, `[`getIndex`](../Node.md)`, `[`getLock`](../Node.md)`, `[`getMixinNodeTypes`](../Node.md)`, `[`getNode`](../Node.md)`, `[`getNodes`](../Node.md)`, `[`getNodes`](../Node.md)`, `[`getPrimaryItem`](../Node.md)`, `[`getPrimaryNodeType`](../Node.md)`, `[`getProperties`](../Node.md)`, `[`getProperties`](../Node.md)`, `[`getProperty`](../Node.md)`, `[`getReferences`](../Node.md)`, `[`getUUID`](../Node.md)`, `[`getVersionHistory`](../Node.md)`, `[`hasNode`](../Node.md)`, `[`hasNodes`](../Node.md)`, `[`hasProperties`](../Node.md)`, `[`hasProperty`](../Node.md)`, `[`holdsLock`](../Node.md)`, `[`isCheckedOut`](../Node.md)`, `[`isLocked`](../Node.md)`, `[`isNodeType`](../Node.md)`, `[`lock`](../Node.md)`, `[`merge`](../Node.md)`, `[`orderBefore`](../Node.md)`, `[`removeMixin`](../Node.md)`, `[`restore`](../Node.md)`, `[`restore`](../Node.md)`, `[`restore`](../Node.md)`, `[`restoreByLabel`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`unlock`](../Node.md)`, `[`update`](../Node.md)

    <!-- -->

    - ### Methods inherited from interface javax.jcr.[Item](../Item.md)

      [`accept`](../Item.md)`, `[`getAncestor`](../Item.md)`, `[`getDepth`](../Item.md)`, `[`getName`](../Item.md)`, `[`getParent`](../Item.md)`, `[`getPath`](../Item.md)`, `[`getSession`](../Item.md)`, `[`isModified`](../Item.md)`, `[`isNew`](../Item.md)`, `[`isNode`](../Item.md)`, `[`isSame`](../Item.md)`, `[`refresh`](../Item.md)`, `[`remove`](../Item.md)`, `[`save`](../Item.md)

<!-- -->

- - ### Method Detail

    - #### getContainingHistory

          VersionHistory getContainingHistory()
                                       throws RepositoryException

      Returns the `VersionHistory` that contains this `Version`.
      Returns:
      the `VersionHistory` that contains this `Version`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getCreated

          java.util.Calendar getCreated()
                                 throws RepositoryException

      Returns the date this version was created. This corresponds to the value of the `jcr:created` property in the `nt:version` node that represents this version.
      Returns:
      a `Calendar` object

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getSuccessors

          Version[] getSuccessors()
                           throws RepositoryException

      Returns the successor versions of this version. This corresponds to returning all the `nt:version` nodes referenced by the `jcr:successors` multi-value property in the `nt:version` node that represents this version.
      Returns:
      a `Version` array.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getPredecessors

          Version[] getPredecessors()
                             throws RepositoryException

      Returns the predecessor versions of this version. This corresponds to returning all the `nt:version` nodes whose `jcr:successors` property includes a reference to the `nt:version` node that represents this version.
      Returns:
      a `Version` array.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

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

- **[Prev Class](OnParentVersionAction.md)**
- **[Next Class](VersionException.md)**

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
