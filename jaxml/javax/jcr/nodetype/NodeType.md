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

- **[Prev Class](NodeDefinition.md)**
- **[Next Class](NodeTypeIterator.md)**

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

## **Interface NodeType**

-

  ------------------------------------------------------------------------

  **
  **

      public interface NodeType

  **Represents a node type.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                           |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                         | `canAddChildNode``(java.lang.String childNodeName)`<br>Returns `true` if this node type allows the addition of a child node called `childNodeName` without specific node type information (that is, given the definition of this parent node type, the child node name is sufficient to determine the intended child node type). |
    | `boolean`                                         | `canAddChildNode``(java.lang.String childNodeName, java.lang.String nodeTypeName)`<br>Returns `true` if this node type allows the addition of a child node called `childNodeName` of node type `nodeTypeName`.                                                                                                                   |
    | `boolean`                                         | `canRemoveItem``(java.lang.String itemName)`<br>Returns true if removing the child item called `itemName` is allowed by this node type.                                                                                                                                                                                          |
    | `boolean`                                         | `canSetProperty``(java.lang.String propertyName, `[`Value`](../Value.md)` value)`<br>Returns `true` if setting `propertyName` to `value` is allowed by this node type.                                                                                                                                                           |
    | `boolean`                                         | `canSetProperty``(java.lang.String propertyName, `[`Value`](../Value.md)`[] values)`<br>Returns `true` if setting `propertyName` to `values` is allowed by this node type.                                                                                                                                                       |
    | [`NodeDefinition`](NodeDefinition.md)`[]`         | `getChildNodeDefinitions``()`<br>Returns an array containing the child node definitions of this node type, including the child node definitions inherited from supertypes of this node type.                                                                                                                                     |
    | [`NodeDefinition`](NodeDefinition.md)`[]`         | `getDeclaredChildNodeDefinitions``()`<br>Returns an array containing the child node definitions explicitly specified in the declaration of *this* node type.                                                                                                                                                                     |
    | [`PropertyDefinition`](PropertyDefinition.md)`[]` | `getDeclaredPropertyDefinitions``()`<br>Returns an array containing the property definitions explicitly specified in the declaration of *this* node type.                                                                                                                                                                        |
    | `NodeType[]`                                      | `getDeclaredSupertypes``()`<br>Returns the *direct* supertypes of this node type in the node type inheritance hierarchy, that is, those actually declared in this node type.                                                                                                                                                     |
    | `java.lang.String`                                | `getName``()`<br>Returns the name of the node type.                                                                                                                                                                                                                                                                              |
    | `java.lang.String`                                | `getPrimaryItemName``()`<br>Returns the name of the primary item (one of the child items of the node's of this node type).                                                                                                                                                                                                       |
    | [`PropertyDefinition`](PropertyDefinition.md)`[]` | `getPropertyDefinitions``()`<br>Returns an array containing the property definitions of this node type, including the property definitions inherited from supertypes of this node type.                                                                                                                                          |
    | `NodeType[]`                                      | `getSupertypes``()`<br>Returns all supertypes of this node type in the node type inheritance hierarchy.                                                                                                                                                                                                                          |
    | `boolean`                                         | `hasOrderableChildNodes``()`<br>Returns `true` if nodes of this type must support orderable child nodes; returns `false` otherwise.                                                                                                                                                                                              |
    | `boolean`                                         | `isMixin``()`<br>Returns `true` if this node type is a mixin node type.                                                                                                                                                                                                                                                          |
    | `boolean`                                         | `isNodeType``(java.lang.String nodeTypeName)`<br>Returns true if this node type is `nodeTypeName` or a subtype of `nodeTypeName`, otherwise returns `false`.                                                                                                                                                                     |

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName()

      Returns the name of the node type.
      Returns:
      the name of the node type

    <!-- -->

    - #### isMixin

          boolean isMixin()

      Returns `true` if this node type is a mixin node type. Returns `false` if this node type is a primary node type.
      Returns:
      a boolean

    <!-- -->

    - #### hasOrderableChildNodes

          boolean hasOrderableChildNodes()

      Returns `true` if nodes of this type must support orderable child nodes; returns `false` otherwise. If a node type returns `true` on a call to this method, then all nodes of that node type *must* support the method [`Node.orderBefore(java.lang.String, java.lang.String)`](../Node.md). If a node type returns `false` on a call to this method, then nodes of that node type *may* support these ordering methods. Only the primary node type of a node controls that node's status in this regard. This setting on a mixin node type will not have any effect on the node.
      Returns:
      Returns `true` if nodes of this type must support orderable child nodes; returns `false` otherwise.

    <!-- -->

    - #### getPrimaryItemName

          java.lang.String getPrimaryItemName()

      Returns the name of the primary item (one of the child items of the node's of this node type). If this node has no primary item, then this method returns `null`. This indicator is used by the method [`Node.getPrimaryItem()`](../Node.md).
      Returns:
      the name of the primary item.

    <!-- -->

    - #### getSupertypes

          NodeType[] getSupertypes()

      Returns all supertypes of this node type in the node type inheritance hierarchy. For primary types apart from `nt:base`, this list will always include at least `nt:base`. For mixin types, there is no required supertype.
      Returns:
      an array of `NodeType` objects.

      See Also:
      `getDeclaredSupertypes()`

    <!-- -->

    - #### getDeclaredSupertypes

          NodeType[] getDeclaredSupertypes()

      Returns the *direct* supertypes of this node type in the node type inheritance hierarchy, that is, those actually declared in this node type. In single-inheritance systems, this will always be an array of size 0 or 1. In systems that support multiple inheritance of node types this array may be of size greater than 1.
      Returns:
      an array of `NodeType` objects.

      See Also:
      `getSupertypes()`

    <!-- -->

    - #### isNodeType

          boolean isNodeType(java.lang.String nodeTypeName)

      Returns true if this node type is `nodeTypeName` or a subtype of `nodeTypeName`, otherwise returns `false`.
      Parameters:
      `nodeTypeName` - the name of a node type.

      Returns:
      a boolean

    <!-- -->

    - #### getPropertyDefinitions

          PropertyDefinition[] getPropertyDefinitions()

      Returns an array containing the property definitions of this node type, including the property definitions inherited from supertypes of this node type.
      Returns:
      an array containing the property definitions.

      See Also:
      `getDeclaredPropertyDefinitions()`

    <!-- -->

    - #### getDeclaredPropertyDefinitions

          PropertyDefinition[] getDeclaredPropertyDefinitions()

      Returns an array containing the property definitions explicitly specified in the declaration of *this* node type. This does *not* include property definitions inherited from supertypes of this node type.
      Returns:
      an array containing the property definitions.

      See Also:
      `getPropertyDefinitions()`

    <!-- -->

    - #### getChildNodeDefinitions

          NodeDefinition[] getChildNodeDefinitions()

      Returns an array containing the child node definitions of this node type, including the child node definitions inherited from supertypes of this node type.
      Returns:
      an array containing the child node definitions.

      See Also:
      `getDeclaredChildNodeDefinitions()`

    <!-- -->

    - #### getDeclaredChildNodeDefinitions

          NodeDefinition[] getDeclaredChildNodeDefinitions()

      Returns an array containing the child node definitions explicitly specified in the declaration of *this* node type. This does *not* include child node definitions inherited from supertypes of this node type.
      Returns:
      an array containing the child node definitions.

      See Also:
      `getChildNodeDefinitions()`

    <!-- -->

    - #### canSetProperty

          boolean canSetProperty(java.lang.String propertyName,
                                 Value value)

      Returns `true` if setting `propertyName` to `value` is allowed by this node type. Otherwise returns `false`.
      Parameters:
      `propertyName` - The name of the property

      `value` - A `Value` object.

    <!-- -->

    - #### canSetProperty

          boolean canSetProperty(java.lang.String propertyName,
                                 Value[] values)

      Returns `true` if setting `propertyName` to `values` is allowed by this node type. Otherwise returns `false`.
      Parameters:
      `propertyName` - The name of the property

      `values` - A `Value` array.

    <!-- -->

    - #### canAddChildNode

          boolean canAddChildNode(java.lang.String childNodeName)

      Returns `true` if this node type allows the addition of a child node called `childNodeName` without specific node type information (that is, given the definition of this parent node type, the child node name is sufficient to determine the intended child node type). Returns `false` otherwise.
      Parameters:
      `childNodeName` - The name of the child node.

    <!-- -->

    - #### canAddChildNode

          boolean canAddChildNode(java.lang.String childNodeName,
                                  java.lang.String nodeTypeName)

      Returns `true` if this node type allows the addition of a child node called `childNodeName` of node type `nodeTypeName`. Returns `false` otherwise.
      Parameters:
      `childNodeName` - The name of the child node.

      `nodeTypeName` - The name of the node type of the child node.

    <!-- -->

    - #### canRemoveItem

          boolean canRemoveItem(java.lang.String itemName)

      Returns true if removing the child item called `itemName` is allowed by this node type. Otherwise returns `false`.
      Parameters:
      `itemName` - The name of the child item

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

- **[Prev Class](NodeDefinition.md)**
- **[Next Class](NodeTypeIterator.md)**

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
