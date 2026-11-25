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

- **[Prev Class](ItemDefinition.md)**
- **[Next Class](NodeType.md)**

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

## **Interface NodeDefinition**

- **All Superinterfaces:**
  **[ItemDefinition](ItemDefinition.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NodeDefinition
      extends ItemDefinition

  **A node definition. Used in node type definitions.**
  **See Also:**
  **[`NodeType.getChildNodeDefinitions()`](NodeType.md), [`Node.getDefinition()`](../Node.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                                        |
    |-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                     | `allowsSameNameSiblings``()`<br>Reports whether this child node can have same-name siblings.                                                                                  |
    | [`NodeType`](NodeType.md)     | `getDefaultPrimaryType``()`<br>Gets the default primary node type that will be assigned to the child node if it is created without an explicitly specified primary node type. |
    | [`NodeType`](NodeType.md)`[]` | `getRequiredPrimaryTypes``()`<br>Gets the minimum set of primary node types that the child node must have.                                                                    |

    - ### Methods inherited from interface javax.jcr.nodetype.[ItemDefinition](ItemDefinition.md)

      [`getDeclaringNodeType`](ItemDefinition.md)`, `[`getName`](ItemDefinition.md)`, `[`getOnParentVersion`](ItemDefinition.md)`, `[`isAutoCreated`](ItemDefinition.md)`, `[`isMandatory`](ItemDefinition.md)`, `[`isProtected`](ItemDefinition.md)

<!-- -->

- - ### Method Detail

    - #### getRequiredPrimaryTypes

          NodeType[] getRequiredPrimaryTypes()

      Gets the minimum set of primary node types that the child node must have. Returns an array to support those implementations with multiple inheritance. This method never returns an empty array. If this node definition places no requirements on the primary node type, then this method will return an array containing only the `NodeType` object representing `nt:base`, which is the base of all primary node types and therefore constitutes the least restrictive node type requirement. Note that any particular node instance still has only one assigned primary node type, but in multiple-inheritance-supporting implementations the `RequiredPrimaryTypes` attribute can be used to restrict that assigned node type to be a subtype of *all* of a specified set of node types.
      Returns:
      an array of `NodeType` objects.

    <!-- -->

    - #### getDefaultPrimaryType

          NodeType getDefaultPrimaryType()

      Gets the default primary node type that will be assigned to the child node if it is created without an explicitly specified primary node type. This node type must be a subtype of (or the same type as) the node types returned by `getRequiredPrimaryTypes`.
      If `null` is returned this indicates that no default primary type is specified and that therefore an attempt to create this node without specifying a node type will throw a `ConstraintViolationException`.

      Returns:
      a `NodeType`.

    <!-- -->

    - #### allowsSameNameSiblings

          boolean allowsSameNameSiblings()

      Reports whether this child node can have same-name siblings. In other words, whether the parent node can have more than one child node of this name.
      Returns:
      a boolean.

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

- **[Prev Class](ItemDefinition.md)**
- **[Next Class](NodeType.md)**

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
