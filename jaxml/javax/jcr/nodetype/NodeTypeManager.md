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

- **[Prev Class](NodeTypeIterator.md)**
- **[Next Class](NoSuchNodeTypeException.md)**

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

## **Interface NodeTypeManager**

- **All Known Subinterfaces:**
  **[OracleNodeTypeManager](../../../oracle/jcr/nodetype/OracleNodeTypeManager.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NodeTypeManager

  **Allows for the retrieval of node types. Accessed via [`Workspace.getNodeTypeManager()`](../Workspace.md).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                          |
    |-------------------------------------------|-------------------------------------------------------------------------------------------------|
    | [`NodeTypeIterator`](NodeTypeIterator.md) | `getAllNodeTypes``()`<br>Returns an iterator over all available node types (primary and mixin). |
    | [`NodeTypeIterator`](NodeTypeIterator.md) | `getMixinNodeTypes``()`<br>Returns an iterator over all available mixin node types.             |
    | [`NodeType`](NodeType.md)                 | `getNodeType``(java.lang.String nodeTypeName)`<br>Returns the named node type.                  |
    | [`NodeTypeIterator`](NodeTypeIterator.md) | `getPrimaryNodeTypes``()`<br>Returns an iterator over all available primary node types.         |

<!-- -->

- - ### Method Detail

    - #### getNodeType

          NodeType getNodeType(java.lang.String nodeTypeName)
                        throws NoSuchNodeTypeException,
                               RepositoryException

      Returns the named node type.
      Throws a `NoSuchNodeTypeException` if a node type by that name does not exist.

      Throws a `RepositoryException` if another error occurs.

      Parameters:
      `nodeTypeName` - the name of an existing node type.

      Returns:
      A `NodeType` object.

      Throws:
      [`NoSuchNodeTypeException`](NoSuchNodeTypeException.md) - if no node type by the given name exists.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getAllNodeTypes

          NodeTypeIterator getAllNodeTypes()
                                    throws RepositoryException

      Returns an iterator over all available node types (primary and mixin).
      Returns:
      An `NodeTypeIterator`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getPrimaryNodeTypes

          NodeTypeIterator getPrimaryNodeTypes()
                                        throws RepositoryException

      Returns an iterator over all available primary node types.
      Returns:
      An `NodeTypeIterator`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getMixinNodeTypes

          NodeTypeIterator getMixinNodeTypes()
                                      throws RepositoryException

      Returns an iterator over all available mixin node types. If none are available, an empty iterator is returned.
      Returns:
      An `NodeTypeIterator`.

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

- **[Prev Class](NodeTypeIterator.md)**
- **[Next Class](NoSuchNodeTypeException.md)**

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
