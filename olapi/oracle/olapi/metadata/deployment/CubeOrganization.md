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

- [Prev Class](AWPrimaryDimensionOrganization.md)
- [Next Class](DeploymentException.md)

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

## Class CubeOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.deployment.CubeOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [AWCubeOrganization](AWCubeOrganization.md), [RolapCubeOrganization](RolapCubeOrganization.md)

  ------------------------------------------------------------------------



      public abstract class CubeOrganization
      extends PublicMetadataObject

  The base class for a metadata object that represents the organization of an `MdmCube` as an analytic workspace (AW) object or as a relational OLAP (Rolap) object. An application gets or creates a concrete subclass of `CubeOrganization` with the [`findOrCreateAWCubeOrganization`](../mdm/MdmCube.md) method or the [`findOrCreateRolapCubeOrganization`](../mdm/MdmCube.md) method of the `MdmCube`.
  A sparse dimension is one for which the measures of the cube have data for less than 80% of the members of the dimension. Oracle OLAP stores the data for sparse dimensions in a structure that is more efficient for querying the data. You can specify a sparse dimension by calling the `addSparseDimension` method and passing it the `MdmDimensionality` object associated with the dimension.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type              | Method and Description                                                                                                                                        |
    |--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                         | `addSparseDimension``(`[`MdmDimensionality`](../mdm/MdmDimensionality.md)` dim)`<br>Adds an `MdmDimensionality` to the sparse dimensions of the cube.         |
    | `void`                         | `clearSparseDimensions``()`<br>Removes all of the `MdmDimensionality` objects from the list of sparse dimensions of the cube.                                 |
    | [`MdmCube`](../mdm/MdmCube.md) | `getCube``()`<br>Gets the `MdmCube` that is associated with the `CubeOrganization`.                                                                           |
    | `java.util.List`               | `getSparseDimensions``()`<br>Gets the `MdmDimensionality` objects for the sparse dimensions of the cube.                                                      |
    | `void`                         | `removeSparseDimension``(`[`MdmDimensionality`](../mdm/MdmDimensionality.md)` dim)`<br>Removes an `MdmDimensionality` from the sparse dimensions of the cube. |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getCube

          public final MdmCube getCube()

      Gets the `MdmCube` that is associated with the `CubeOrganization`.
      Returns:
      The `MdmCube` associated with the `CubeOrganization`.

    <!-- -->

    - #### getSparseDimensions

          public final java.util.List getSparseDimensions()

      Gets the `MdmDimensionality` objects for the sparse dimensions of the cube.
      Returns:
      A `List` of the `MdmDimensionality` objects for the sparse dimensions of the `CubeOrganization`.

    <!-- -->

    - #### removeSparseDimension

          public final void removeSparseDimension(MdmDimensionality dim)

      Removes an `MdmDimensionality` from the sparse dimensions of the cube.
      Parameters:
      `dim` - The `MdmDimensionality` to remove from the list of the sparse dimensions of the `CubeOrganization`.

    <!-- -->

    - #### addSparseDimension

          public final void addSparseDimension(MdmDimensionality dim)

      Adds an `MdmDimensionality` to the sparse dimensions of the cube.
      Parameters:
      `dim` - The `MdmDimensionality` to add to the list of the sparse dimensions of the `CubeOrganization`.

    <!-- -->

    - #### clearSparseDimensions

          public final void clearSparseDimensions()

      Removes all of the `MdmDimensionality` objects from the list of sparse dimensions of the cube.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AWPrimaryDimensionOrganization.md)
- [Next Class](DeploymentException.md)

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
