Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](MdmMemberListMapOwner.md)
- [Next Class](MdmMetadataProvider.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.metadata.mdm

## Class MdmMetadataProperty

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.mdm.MdmMetadataProperty

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmMetadataProperty
      extends PublicMetadataObject

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                          |
    |--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                               | `getKey``()`<br>Gets the value that of this `MdmMetadataProperty`.                                              |
    | `java.lang.String`                               | `getName``()`<br>Gets the name of this `MdmMetadataProperty`.                                                   |
    | [`BaseMetadataObject`](../BaseMetadataObject.md) | `getPropertyOwningObject``()`<br>Gets the `BaseMetadataObject` that contains this `MdmMetadataProperty` object. |
    | `java.lang.String`                               | `getValue``()`<br>Gets the value that of this `MdmMetadataProperty`.                                            |
    | `void`                                           | `setKey``(java.lang.String value)`<br>Specifies the value of the Key for this `MdmMetadataProperty`.            |
    | `void`                                           | `setValue``(java.lang.String value)`<br>Specifies the value of this `MdmMetadataProperty`.                      |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getValue

          public final java.lang.String getValue()

      Gets the value that of this `MdmMetadataProperty`.
      Returns:
      A `String` that is the value of this `MdmMetadataProperty`.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.String value)

      Specifies the value of this `MdmMetadataProperty`.
      Parameters:
      `value` - A `String` that specifies the value for this `MdmMetadataProperty`.

    <!-- -->

    - #### getKey

          public final java.lang.String getKey()

      Gets the value that of this `MdmMetadataProperty`.
      Returns:
      A `String` that is the value of this `MdmMetadataProperty`.

    <!-- -->

    - #### setKey

          public final void setKey(java.lang.String value)

      Specifies the value of the Key for this `MdmMetadataProperty`.
      Parameters:
      `value` - A `String` that specifies the value for the Key for this `MdmMetadataProperty`.

    <!-- -->

    - #### getPropertyOwningObject

          public final BaseMetadataObject getPropertyOwningObject()

      Gets the `BaseMetadataObject` that contains this `MdmMetadataProperty` object.
      Returns:
      The `BaseMetadataObjectt` that owns this `MdmMetadataProperty`.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `MdmMetadataProperty`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of this `MdmMetadataProperty`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMemberListMapOwner.md)
- [Next Class](MdmMetadataProvider.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
