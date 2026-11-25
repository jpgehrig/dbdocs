Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEAttributeDescriptor.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network.nfe.model.feature

## Interface NFEAttributeConstraint

- All Known Implementing Classes:
  [NFEBasicAttributeConstraint](NFEBasicAttributeConstraint.md)

  ------------------------------------------------------------------------



      public interface NFEAttributeConstraint

  Represents a constraint for an attribute definition. It can specify the attribute default value and whether the attribute is writable or not.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                               |
    |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEAttributeConstraint`                              | `createCopy``()`<br>Returns object copy.                                                                                                                             |
    | [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md) | `getAttributeDescriptor``()`<br>Gets the attribute descriptor where the constraint is enforced                                                                       |
    | `java.lang.Object`                                    | `getDefaultValue``()`<br>Gets the value the attribute must contain when it is created                                                                                |
    | `long`                                                | `getId``()`<br>Gets the constraint ID                                                                                                                                |
    | `boolean`                                             | `isReadOnly``()`<br>Gets whether the attribute is writable or read-only                                                                                              |
    | `boolean`                                             | `isVisible``()`<br>Tells whether the attribute is visible or not.                                                                                                    |
    | `void`                                                | `setAttributeDescriptor``(`[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)` attrDescriptor)`<br>Sets the attribute descriptor where the constraint is enforced |
    | `void`                                                | `setDefaultValue``(java.lang.Object defaultValue)`<br>Sets the value the attribute must contain when it is created                                                   |
    | `void`                                                | `setId``(long id)`<br>Sets the constraint ID                                                                                                                         |
    | `void`                                                | `setReadOnly``(boolean readOnly)`<br>Sets whether the attribute is writable or read-only                                                                             |
    | `void`                                                | `setVisible``(boolean visible)`<br>Sets whether the attribute is visible or not.                                                                                     |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Gets the constraint ID
      Returns:
      the constraint ID

    <!-- -->

    - #### setId

          void setId(long id)

      Sets the constraint ID
      Parameters:
      `id` - the constraint ID

    <!-- -->

    - #### setAttributeDescriptor

          void setAttributeDescriptor(NFEAttributeDescriptor attrDescriptor)

      Sets the attribute descriptor where the constraint is enforced
      Parameters:
      `attrDescriptor` - an attribute descriptor instance

    <!-- -->

    - #### getAttributeDescriptor

          NFEAttributeDescriptor getAttributeDescriptor()

      Gets the attribute descriptor where the constraint is enforced
      Returns:
      an attribute descriptor instance

    <!-- -->

    - #### setDefaultValue

          void setDefaultValue(java.lang.Object defaultValue)

      Sets the value the attribute must contain when it is created
      Parameters:
      `defaultValue` - an attribute default value. The type should match the type specified by the constraint's attribute descriptor

    <!-- -->

    - #### getDefaultValue

          java.lang.Object getDefaultValue()

      Gets the value the attribute must contain when it is created
      Returns:
      the attribute default value

    <!-- -->

    - #### setReadOnly

          void setReadOnly(boolean readOnly)

      Sets whether the attribute is writable or read-only
      Parameters:
      `readOnly` - true if the attribute is read-only

    <!-- -->

    - #### isReadOnly

          boolean isReadOnly()

      Gets whether the attribute is writable or read-only
      Returns:
      true if the attribute is read-only

    <!-- -->

    - #### setVisible

          void setVisible(boolean visible)

      Sets whether the attribute is visible or not. It is used with graphical editors.
      Parameters:
      `visible` - true for visible

    <!-- -->

    - #### isVisible

          boolean isVisible()

      Tells whether the attribute is visible or not. It is used with graphical editors.
      Returns:
      true for visible

    <!-- -->

    - #### createCopy

          NFEAttributeConstraint createCopy()

      Returns object copy.
      Returns:
      object copy

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEAttributeDescriptor.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
