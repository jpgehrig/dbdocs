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

- **[Prev Class](ConstraintViolationException.md)**
- **[Next Class](NodeDefinition.md)**

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

## **Interface ItemDefinition**

- **All Known Subinterfaces:**
  **[NodeDefinition](NodeDefinition.md), [PropertyDefinition](PropertyDefinition.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ItemDefinition

  **Superinterface of [`NodeDefinition`](NodeDefinition.md) and [`PropertyDefinition`](PropertyDefinition.md).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                                                                          |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------|
    | [`NodeType`](NodeType.md) | `getDeclaringNodeType``()`<br>Gets the node type that contains the declaration of *this* `ItemDefinition`.      |
    | `java.lang.String`        | `getName``()`<br>Gets the name of the child item.                                                               |
    | `int`                     | `getOnParentVersion``()`<br>Gets the on-parent-version status of the child item.                                |
    | `boolean`                 | `isAutoCreated``()`<br>Reports whether the item is to be automatically created when its parent node is created. |
    | `boolean`                 | `isMandatory``()`<br>Reports whether the item is mandatory.                                                     |
    | `boolean`                 | `isProtected``()`<br>Reports whether the child item is protected.                                               |

<!-- -->

- - ### Method Detail

    - #### getDeclaringNodeType

          NodeType getDeclaringNodeType()

      Gets the node type that contains the declaration of *this* `ItemDefinition`.
      Returns:
      a `NodeType` object.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Gets the name of the child item. If `"*"`, this `ItemDefinition` defines a residual set of child items. That is, it defines the characteristics of all those child items with names apart from the names explicitly used in other child item definitions.
      Returns:
      a `String` denoting the name or `"*"`.

    <!-- -->

    - #### isAutoCreated

          boolean isAutoCreated()

      Reports whether the item is to be automatically created when its parent node is created. If `true`, then this `ItemDefinition` will necessarily not be a residual set definition but will specify an actual item name (in other words getName() will not return "\*").
      Returns:
      a `boolean`.

    <!-- -->

    - #### isMandatory

          boolean isMandatory()

      Reports whether the item is mandatory. A mandatory item is one that, if its parent node exists, must also exist.
      This means that a mandatory single-value property must have a value (since there is no such thing a `null` value). In the case of multi-value properties this means that the property must exist, though it can have zero or more values.

      An attempt to save a node that has a mandatory child item without first creating that child item will throw a `ConstraintViolationException` on `save`.

      Returns:
      a `boolean`

    <!-- -->

    - #### getOnParentVersion

          int getOnParentVersion()

      Gets the on-parent-version status of the child item. This governs what to do if the parent node of this child item is versioned; an [`OnParentVersionAction`](../version/OnParentVersionAction.md).
      Returns:
      an `int`.

    <!-- -->

    - #### isProtected

          boolean isProtected()

      Reports whether the child item is protected. In level 2 implementations, a protected item is one that cannot be removed (xcept by removing its parent) or modified through the the standard write methods of this API (that is, `Item.remove`, `Node.addNode`, `Node.setProperty` and `Property.setValue`).
      A protected node may be removed or modified (in a level 2 implementation), however, through some mechanism not defined by this specification or as a side-effect of operations other than the standard write methods of the API.

      Returns:
      a `boolean`.

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

- **[Prev Class](ConstraintViolationException.md)**
- **[Next Class](NodeDefinition.md)**

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
