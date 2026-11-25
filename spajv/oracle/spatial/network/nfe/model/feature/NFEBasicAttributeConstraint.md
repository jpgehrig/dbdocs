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

- [Prev Class](NFEAttributeType.md)
- [Next Class](NFEBasicAttributeDescriptor.md)

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

## Class NFEBasicAttributeConstraint

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEBasicAttributeConstraint

<!-- -->

- All Implemented Interfaces:
  [NFEAttributeConstraint](NFEAttributeConstraint.md)

  ------------------------------------------------------------------------



      public class NFEBasicAttributeConstraint
      extends java.lang.Object
      implements NFEAttributeConstraint

  The deault implementation of [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description        |
    |------------------------------------|
    | `NFEBasicAttributeConstraint``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                               |
    |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEAttributeConstraint`](NFEAttributeConstraint.md) | `createCopy``()`<br>Returns object copy.                                                                                                                             |
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

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicAttributeConstraint

          public NFEBasicAttributeConstraint()

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Gets the constraint ID
      Specified by:
      [`getId`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Returns:
      the constraint ID

    <!-- -->

    - #### setId

          public void setId(long id)

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Sets the constraint ID
      Specified by:
      [`setId`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Parameters:
      `id` - the constraint ID

    <!-- -->

    - #### setAttributeDescriptor

          public void setAttributeDescriptor(NFEAttributeDescriptor attrDescriptor)

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Sets the attribute descriptor where the constraint is enforced
      Specified by:
      [`setAttributeDescriptor`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Parameters:
      `attrDescriptor` - an attribute descriptor instance

    <!-- -->

    - #### getAttributeDescriptor

          public NFEAttributeDescriptor getAttributeDescriptor()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Gets the attribute descriptor where the constraint is enforced
      Specified by:
      [`getAttributeDescriptor`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Returns:
      an attribute descriptor instance

    <!-- -->

    - #### setDefaultValue

          public void setDefaultValue(java.lang.Object defaultValue)

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Sets the value the attribute must contain when it is created
      Specified by:
      [`setDefaultValue`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Parameters:
      `defaultValue` - an attribute default value. The type should match the type specified by the constraint's attribute descriptor

    <!-- -->

    - #### getDefaultValue

          public java.lang.Object getDefaultValue()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Gets the value the attribute must contain when it is created
      Specified by:
      [`getDefaultValue`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Returns:
      the attribute default value

    <!-- -->

    - #### setReadOnly

          public void setReadOnly(boolean readOnly)

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Sets whether the attribute is writable or read-only
      Specified by:
      [`setReadOnly`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Parameters:
      `readOnly` - true if the attribute is read-only

    <!-- -->

    - #### isReadOnly

          public boolean isReadOnly()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Gets whether the attribute is writable or read-only
      Specified by:
      [`isReadOnly`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Returns:
      true if the attribute is read-only

    <!-- -->

    - #### setVisible

          public void setVisible(boolean visible)

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Sets whether the attribute is visible or not. It is used with graphical editors.
      Specified by:
      [`setVisible`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Parameters:
      `visible` - true for visible

    <!-- -->

    - #### isVisible

          public boolean isVisible()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Tells whether the attribute is visible or not. It is used with graphical editors.
      Specified by:
      [`isVisible`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

      Returns:
      true for visible

    <!-- -->

    - #### createCopy

          public NFEAttributeConstraint createCopy()

      Description copied from interface: [`NFEAttributeConstraint`](NFEAttributeConstraint.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEAttributeConstraint.md) in interface [`NFEAttributeConstraint`](NFEAttributeConstraint.md)

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

- [Prev Class](NFEAttributeType.md)
- [Next Class](NFEBasicAttributeDescriptor.md)

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
