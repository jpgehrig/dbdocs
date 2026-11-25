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

- [Prev Class](MVCreationOptions.md)
- [Next Class](RolapCubeOrganization.md)

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

## Class PrimaryDimensionOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.deployment.PrimaryDimensionOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [AWPrimaryDimensionOrganization](AWPrimaryDimensionOrganization.md), [RolapPrimaryDimensionOrganization](RolapPrimaryDimensionOrganization.md)

  ------------------------------------------------------------------------



      public abstract class PrimaryDimensionOrganization
      extends PublicMetadataObject

  A metadata object that represents the organization of an `MdmPrimaryDimension` as a relational OLAP (Rolap) object or as an analytic workspace (AW) object. An application gets or creates a concrete subclass of `PrimaryDimensionOrganization` with the [`findOrCreateAWPrimaryDimensionOrganization`](../mdm/MdmPrimaryDimension.md) method or the [`findOrCreateRolapPrimaryDimensionOrganization`](../mdm/MdmPrimaryDimension.md) method of the `MdmPrimaryDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                  |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | [`MdmPrimaryDimension`](../mdm/MdmPrimaryDimension.md) | `getPrimaryDimension``()`<br>Gets the `MdmPrimaryDimension` that is associated with the `PrimaryDimensionOrganization`. |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getPrimaryDimension

          public final MdmPrimaryDimension getPrimaryDimension()

      Gets the `MdmPrimaryDimension` that is associated with the `PrimaryDimensionOrganization`.
      Returns:
      The `MdmPrimaryDimension` associated with the `PrimaryDimensionOrganization`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MVCreationOptions.md)
- [Next Class](RolapCubeOrganization.md)

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
