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

- [Prev Class](AW.md)
- [Next Class](AWCubeOrganization.md)

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

oracle.olapi.metadata.deployment

## Class AWAttributeOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.deployment.AWAttributeOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class AWAttributeOrganization
      extends PublicMetadataObject

  A metadata object that represents the organization of an `MdmAttribute` for an `AWPrimaryDimensionOrganization`. An application gets an `AWAttributeOrganization` for an attribute with the `getAttributeOrganization` method of the `AWPrimaryDimensionOrganization`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                     | Method and Description                                                                                                  |
    |-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                             | `createAttributeIndex``()`<br>Indicates whether Oracle OLAP creates an index for the attribute.                         |
    | [`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md)                      | `getAttribute``()`<br>Gets the `MdmBaseAttribute` that is associated with this `AWAttributeOrganization`.               |
    | [`AWPrimaryDimensionOrganization`](AWPrimaryDimensionOrganization.md) | `getAWDimensionOrganization``()`<br>Gets the `AWPrimaryDimensionOrganization` that owns this `AWAttributeOrganization`. |
    | `void`                                                                | `setCreateAttributeIndex``(boolean val)`<br>Specifies whether Oracle OLAP creates an index for the attribute.           |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### createAttributeIndex

          public final boolean createAttributeIndex()

      Indicates whether Oracle OLAP creates an index for the attribute.
      Returns:
      A `boolean` that indicates whether Oracle OLAP creates an index for the attribute.

    <!-- -->

    - #### setCreateAttributeIndex

          public final void setCreateAttributeIndex(boolean val)

      Specifies whether Oracle OLAP creates an index for the attribute. An index enables a query to execute more quickly. It can, however, cause a build of the dimension to take longer.
      Parameters:
      `val` - A `boolean` that is `true` if you want Oracle OLAP to create an index for the attribute, or `false` otherwise.

    <!-- -->

    - #### getAWDimensionOrganization

          public final AWPrimaryDimensionOrganization getAWDimensionOrganization()

      Gets the `AWPrimaryDimensionOrganization` that owns this `AWAttributeOrganization`.
      Returns:
      The `AWPrimaryDimensionOrganization` that owns this `AWAttributeOrganization`.

    <!-- -->

    - #### getAttribute

          public final MdmBaseAttribute getAttribute()

      Gets the `MdmBaseAttribute` that is associated with this `AWAttributeOrganization`.
      Returns:
      The `MdmBaseAttribute` associated with this `AWAttributeOrganization`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AW.md)
- [Next Class](AWCubeOrganization.md)

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
