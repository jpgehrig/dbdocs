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

- [Prev Class](RolapPrimaryDimensionOrganization.md)
- Next Class

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

## Class SecondaryPartitionLevel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.deployment.SecondaryPartitionLevel

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class SecondaryPartitionLevel
      extends PublicMetadataObject

  A `BaseMetadataObject` that represents a secondary partitioning level for an `AWCubeOrganization`. Secondary partitions can improve the performance of building or refreshing a cube that has many dimensions.
  You create a `SecondaryPartitionLevel` with the [`findOrCreateSecondaryPartitionLevel`](AWCubeOrganization.md) method of an `AWCubeOrganization`. You then use the `setLevel` method of the `SecondaryPartitionLevel` to specify the hierarchy level that you want to use as the basis of the secondary partitioning.

  With a `SecondaryPartitionLevel` you can specify the creation of partitions for the dimension members of a level that is in the top-level partition of a primary partition. You specify a primary partition level for a cube by using the [`setPartitionLevel`](AWCubeOrganization.md) method of an `AWCubeOrganization`. That method creates a partition of the cube for each dimension member of the specified hierarchy level. The partition includes the dimension member and any descendants of the member. It also creates a top-level partition that includes all of the levels above the level specified for partitioning.

  For example, the `CALENDAR_YEAR` hierarchy of the `TIME_AWJ` dimension of the `UNITS_CUBE_AWJ` cube has four hierarchy levels: `TOTAL_TIME`, `YEAR`, `QUARTER`, and `MONTH`. If you specify the `QUARTER` level as the basis for the primary partitioning, then when you build the cube Oracle OLAP generates a partition for each quarter and a top-level partition that contains the members of the `YEAR` and `TOTAL_TIME` levels. Each `QUARTER` partition also contains the `MONTH` level members that are the children of the quarter.

  You could then create a `SecondaryPartitionLevel` for partitioning a level that is in the top-level partition of the primary partitioning. For example, if you specify `YEAR` as the level for a `SecondaryPartitionLevel` for the cube, then when you build the cube, Oracle OLAP generates a partition for each member of the `YEAR` level. The secondary partitions would contain only the `YEAR` members because the descendants of a year already belong to the primary partitions of the `QUARTER` level.

  The secondary partitioning levels must be in the same dimension as the primary partitioning level. You can specify up to three secondary partitioning levels. The order in which you create the `SecondaryPartitionLevel` objects determines the order in which Oracle OLAP computes the measure values dimensioned by the dimension members in the partitions. You can change the order of the `SecondaryPartitionLevel` objects by removing a `SecondaryPartitionLevel` and then by specifying a different position when you add the `SecondaryPartitionLevel` back to the `AWCubeOrganization`. You remove and add a `SecondaryPartitionLevel` with the `removeSecondaryPartitionLevel` and `addSecondaryPartitionLevel` methods of the `AWCubeOrganization`.

  A dimension member can be in only one partition, so if you have more than one secondary partitioning level, then you should have the levels in ascending order, with the lowest secondary partitioning level in the first position.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                                                                          |
    |----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AWCubeOrganization`](AWCubeOrganization.md)      | `getAWCubeOrganization``()`<br>Gets the `AWCubeOrganization` that contains this `SecondaryPartitionLevel`.                                                                                                                                                      |
    | [`MdmHierarchyLevel`](../mdm/MdmHierarchyLevel.md) | `getLevel``()`<br>Gets the dimension hierarchy level that is the basis for the secondary partitioning of the cube that is associated with this `SecondaryPartitionLevel`.                                                                                       |
    | `int`                                              | `getPrecomputePercent``()`<br>Gets the percentage of the aggregate measure values that Oracle OLAP computes and stores during a build or refresh operation for the measure values that are specified by the dimension members in the secondary partitions.      |
    | `void`                                             | `setLevel``(`[`MdmHierarchyLevel`](../mdm/MdmHierarchyLevel.md)` level)`<br>Specifies the dimension hierarchy level to use as the basis for the secondary partitioning of the cube that is associated with this `SecondaryPartitionLevel`.                      |
    | `void`                                             | `setPrecomputePercent``(int val)`<br>For the measure values that are specified by the dimension members in the secondary partitions, specifies the percentage of the aggregate values that Oracle OLAP computes and stores during a build or refresh operation. |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getAWCubeOrganization

          public final AWCubeOrganization getAWCubeOrganization()

      Gets the `AWCubeOrganization` that contains this `SecondaryPartitionLevel`.
      Returns:
      The `AWCubeOrganization` that contains this `SecondaryPartitionLevel`.

    <!-- -->

    - #### setLevel

          public final void setLevel(MdmHierarchyLevel level)

      Specifies the dimension hierarchy level to use as the basis for the secondary partitioning of the cube that is associated with this `SecondaryPartitionLevel`. When it builds the cube, Oracle OLAP generates a secondary partition for each dimension member of the hierachy level.
      Parameters:
      `level` - The `MdmHierarchyLevel` to use as the basis for the secondary partitioning the cube associated with this `SecondaryPartitionLevel`.

    <!-- -->

    - #### getLevel

          public final MdmHierarchyLevel getLevel()

      Gets the dimension hierarchy level that is the basis for the secondary partitioning of the cube that is associated with this `SecondaryPartitionLevel`.
      Returns:
      The `MdmHierarchyLevel` that is the basis for the secondary partitioning the cube associated with this `SecondaryPartitionLevel`.

    <!-- -->

    - #### getPrecomputePercent

          public final int getPrecomputePercent()

      Gets the percentage of the aggregate measure values that Oracle OLAP computes and stores during a build or refresh operation for the measure values that are specified by the dimension members in the secondary partitions.
      Returns:
      An integer that represents the percentage of the measure values that Oracle OLAP precomputes for the secondary partitions.

    <!-- -->

    - #### setPrecomputePercent

          public final void setPrecomputePercent(int val)

      For the measure values that are specified by the dimension members in the secondary partitions, specifies the percentage of the aggregate values that Oracle OLAP computes and stores during a build or refresh operation.
      Parameters:
      `val` - An integer that represents the percentage of the measure values for Oracle OLAP to precompute. The value can be 0 (zero) or greater.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](RolapPrimaryDimensionOrganization.md)
- Next Class

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
