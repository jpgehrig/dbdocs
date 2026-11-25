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

- [Prev Class](AWAttributeOrganization.md)
- [Next Class](AWPrimaryDimensionOrganization.md)

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

## Class AWCubeOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.deployment.CubeOrganization](CubeOrganization.md)

      - - oracle.olapi.metadata.deployment.AWCubeOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class AWCubeOrganization
      extends CubeOrganization

  A `CubeOrganization` for an analytic workspace. An `AWCubeOrganization` contains options that affect the data loading, aggregation method, storage, and querying of an `MdmCube`. To get an existing `AWCubeOrganization` or to create a new one, use the [`findOrCreateAWCubeOrganization`](../mdm/MdmCube.md) method of the `MdmCube`.
  One option controls the creation of materialized views (MVs) for the measures and dimensions that are associated with the cube. MVs can be automatically refreshed, which can be useful in maintaining the analytic workspace. An MV can be used by the database query rewrite system, which can result in significantly enhanced performance of SQL queries. However, a cube that uses MVs has limitations because the cube must meet certain requirements, which are listed in the description of the `setMVOption` method. Another limitation is that a cube that has MVs cannot have a derived measure.

  Oracle Database has systems for refreshing the data associated with an MV and for transparently rewriting a query so that it uses an MV. With the `setMVOption` method, you can specify whether or not to create an MV and the type of MV to create. The options that specify the creation of an MV determine the structure of the MV and the conditions required for the creation of the MV. If you specify the creation of a MV, then you can use an `MVCreationOptions` object to set values that affect the actual creation of the MV and that can replace the default values.

  A Java application can demand a refresh by calling the `DataProvider.executeBuild` method for the cube. Building the cube refreshes the MV. You can specify properties that affect the building of the cube by passing a `BuildProperties` object to the `executeBuild` method.

  For more information on cube partitioning, sparsity types, storage types, and the use of MVs, see *Oracle OLAP User's Guide*.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type           | Field and Description                                                                                                                                                                                                                                                                                                 |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`   | `COMPLETE_REFRESH_MV_OPTION`<br>A constant that indicates that Oracle OLAP creates a materialized view that supports a complete refresh operation.                                                                                                                                                                    |
    | `static java.lang.String`   | `COMPRESSED_SPARSE_TYPE`<br>A constant that indicates an extremely sparse cube.                                                                                                                                                                                                                                       |
    | `static java.lang.String`   | `DENSE_SPARSE_TYPE`<br>A constant that indicates a dense cube.                                                                                                                                                                                                                                                        |
    | `static java.lang.String`   | `FAST_REFRESH_MV_OPTION`<br>A constant that indicates that Oracle OLAP creates a materialized view that supports a fast refresh operation.                                                                                                                                                                            |
    | `static java.lang.String`   | `FAST_REFRESH_READY_MV_OPTION`<br>A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of a materialized view that is capable of a fast refresh.                                                                                                           |
    | `static java.lang.String`   | `GENERIC_NULL_STORAGE`<br>A constant that indicates that Oracle OLAP does not distinguish between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value.                                                                                                                   |
    | `static java.lang.String`   | `INDEPENDENT_MEASURE_STORAGE`<br>A constant that indicates that Oracle OLAP stores the values of each of the measures of the cube in a separate object.                                                                                                                                                               |
    | `static java.lang.String`   | `MV_READY_NULL_STORAGE`<br>A constant that indicates that Oracle OLAP makes a distinction between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value.                                                                                                                   |
    | `static java.lang.String`   | `NONE_MV_OPTION`<br>A constant that indicates that Oracle OLAP does not a create materialized view for the cube.                                                                                                                                                                                                      |
    | `static java.lang.String`   | `REWRITE_MV_OPTION`<br>A constant that indicates that Oracle OLAP creates a materialized view that is accessible to the database query rewrite system.                                                                                                                                                                |
    | `static java.lang.String`   | `REWRITE_READY_MV_OPTION`<br>A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of an materialized viewt that is accessible to the database query rewrite system.                                                                                        |
    | `static java.lang.String`   | `REWRITE_WITH_ATTRIBUTES_MV_OPTION`<br>A constant that indicates that Oracle OLAP creates a materialized view that has query rewrite enabled and that includes columns for all `MdmDimensionLevel` attributes for which the [`MdmBaseAttribute.isPopulateLineage`](../mdm/MdmBaseAttribute.md) method returns `true`. |
    | `static java.lang.String`   | `SHARED_MEASURE_STORAGE`<br>A constant that indicates that Oracle OLAP stores the values of all of the measures of the cube in the same object.                                                                                                                                                                       |
    | `static java.lang.String`   | `SPARSE_GLOBAL_SPARSE_TYPE`<br>A constant that indicates a sparse cube that has partitions and that stores all of the partitioned data in a single object.                                                                                                                                                            |
    | `static java.lang.String`   | `SPARSE_SPARSE_TYPE`<br>A constant that indicates a sparse cube.                                                                                                                                                                                                                                                      |
    | `static java.lang.String[]` | `VALID_MEASURE_STORAGE_TYPES`<br>A constant that has the valid values for the types of measure storage.                                                                                                                                                                                                               |
    | `static java.lang.String[]` | `VALID_MV_OPTIONS`<br>A constant that has the valid values for materialized view options.                                                                                                                                                                                                                             |
    | `static java.lang.String[]` | `VALID_NULL_STORAGE_TYPES`<br>A constant that has the valid values for the types of storage of null values.                                                                                                                                                                                                           |
    | `static java.lang.String[]` | `VALID_SPARSE_TYPES`<br>A constant that has the valid values for sparsity type.                                                                                                                                                                                                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                         | `addBuildSpecification``(`[`BuildSpecification`](../../syntax/BuildSpecification.md)` spec)`<br>Adds a `BuildSpecification` to the list of those that are contained by this `AWCubeOrganization`.                                                                               |
    | `void`                                                                         | `addSecondaryPartitionLevel``(`[`SecondaryPartitionLevel`](SecondaryPartitionLevel.md)` level, int levelNumber)`<br>Adds a `SecondaryPartitionLevel` to the `List` of those that are contained by this `AWCubeOrganization`.                                                    |
    | [`MVCreationOptions`](MVCreationOptions.md)                                    | `findOrCreateMVCreationOptions``()`<br>Gets the `MVCreationOptions` that is contained by this `AWCubeOrganization` or creates one if it does not already exist.                                                                                                                 |
    | [`SecondaryPartitionLevel`](SecondaryPartitionLevel.md)                        | `findOrCreateSecondaryPartitionLevel``(java.lang.String name)`<br>Gets the specified `SecondaryPartitionLevel` that is contained by this `AWCubeOrganization` or creates one if it does not already exist.                                                                      |
    | [`AW`](AW.md)                                                                  | `getAW``()`<br>Gets the analytic workspace that is associated with this `AWCubeOrganization`.                                                                                                                                                                                   |
    | `java.util.List<`[`BuildSpecification`](../../syntax/BuildSpecification.md)`>` | `getBuildSpecifications``()`<br>Gets the `BuildSpecification` objects that are contained by this `AWCubeOrganization`.                                                                                                                                                          |
    | `java.lang.String`                                                             | `getCubeStorageType``()`<br>Gets the Oracle OLAP DML data type for the shared measure storage.                                                                                                                                                                                  |
    | [`BuildSpecification`](../../syntax/BuildSpecification.md)                     | `getDefaultBuildSpecification``()`<br>Gets the default `BuildSpecification` of this `AWCubeOrganization`.                                                                                                                                                                       |
    | `java.lang.String`                                                             | `getMeasureStorage``()`<br>Gets the storage type of the measures of the cube that contains this `AWCubeOrganization`.                                                                                                                                                           |
    | [`MVCreationOptions`](MVCreationOptions.md)                                    | `getMVCreationOptions``()`<br>Gets the `MVCreationOptions` object of the AWCubeOrganization                                                                                                                                                                                     |
    | `java.lang.String`                                                             | `getMVOption``()`<br>Gets the materialized view option for the cube that contains this `AWCubeOrganization`.                                                                                                                                                                    |
    | `java.lang.String`                                                             | `getNullStorage``()`<br>Gets the null storage type of the measures of the cube that contains this `AWCubeOrganization`.                                                                                                                                                         |
    | [`MdmHierarchyLevel`](../mdm/MdmHierarchyLevel.md)                             | `getPartitionLevel``()`<br>Gets the dimension level that is the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.                                                                                                                         |
    | [`SymmetricCondition`](../../syntax/SymmetricCondition.md)                     | `getPrecomputeCondition``()`<br>Gets the `SymmetricCondition` that specifies the dimension members for which Oracle OLAP computes and stores aggregate measure values during a build or refresh operation.                                                                      |
    | `int`                                                                          | `getPrecomputePercent``()`<br>Gets the percentage of the aggregate measure values for a compressed cube that Oracle OLAP computes and stores during a build or refresh operation.                                                                                               |
    | `int`                                                                          | `getPrecomputePercentTop``()`<br>Gets the percentage of the measure values for the top level of a hierarchy of a compressed and partitioned cube that Oracle OLAP computes and stores during a build or refresh operation.                                                      |
    | `java.util.List<`[`SecondaryPartitionLevel`](SecondaryPartitionLevel.md)`>`    | `getSecondaryPartitionLevels``()`<br>Gets the `SecondaryPartitionLevel` objects that are contained by this `AWCubeOrganization`.                                                                                                                                                |
    | `java.lang.String`                                                             | `getSparseType``()`<br>Gets the sparsity type of the cube that contains this `AWCubeOrganization`.                                                                                                                                                                              |
    | [`SQLDataType`](../../syntax/SQLDataType.md)                                   | `getSQLCubeStorageType``()`<br>Gets the SQL data type for the shared measure storage.                                                                                                                                                                                           |
    | `void`                                                                         | `removeBuildSpecification``(`[`BuildSpecification`](../../syntax/BuildSpecification.md)` spec)`<br>Removes a `BuildSpecification` from the list of those that are contained by this `AWCubeOrganization`.                                                                       |
    | `void`                                                                         | `removeSecondaryPartitionLevel``(`[`SecondaryPartitionLevel`](SecondaryPartitionLevel.md)` partitionLevel)`<br>Removes the specified `SecondaryPartitionLevel` from those that are contained by this `AWCubeOrganization`.                                                      |
    | `void`                                                                         | `setAW``(`[`AW`](AW.md)` aw)`<br>Specifies an `AW` as the container of the `MdmCube` that contains this `AWCubeOrganization`.                                                                                                                                                   |
    | `void`                                                                         | `setCubeStorageType``(java.lang.String exp)`<br>Specifies the Oracle OLAP DML data type for the shared measure storage for the cube that contains this `AWCubeOrganization`.                                                                                                    |
    | `void`                                                                         | `setDefaultBuildSpecification``(`[`BuildSpecification`](../../syntax/BuildSpecification.md)` spec)`<br>Specifies a `BuildSpecification` to use as the default for this `AWCubeOrganization`.                                                                                    |
    | `void`                                                                         | `setMeasureStorage``(java.lang.String type)`<br>Specifies the measure storage type for the cube that contains this `AWCubeOrganization`.                                                                                                                                        |
    | `void`                                                                         | `setMVCreationOptions``(`[`MVCreationOptions`](MVCreationOptions.md)` mvCreationOptions)`<br>Specifies an `MVCreationOptions` for this `AWCubeOrganization`.                                                                                                                    |
    | `void`                                                                         | `setMVOption``(java.lang.String option)`<br>Specifies the materialized view option for the cube that contains this `AWCubeOrganization`.                                                                                                                                        |
    | `void`                                                                         | `setNullStorage``(java.lang.String type)`<br>Specifies the null storage type for the cube that contains this `AWCubeOrganization`.                                                                                                                                              |
    | `void`                                                                         | `setPartitionLevel``(`[`MdmHierarchyLevel`](../mdm/MdmHierarchyLevel.md)` level)`<br>Specifies the dimension level to use as the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.                                                        |
    | `void`                                                                         | `setPrecomputeCondition``(`[`SymmetricCondition`](../../syntax/SymmetricCondition.md)` cond)`<br>Specifies a `SymmetricCondition` that identifies the dimension members for which Oracle OLAP computes and stores aggregate measure values during a build or refresh operation. |
    | `void`                                                                         | `setPrecomputePercent``(int val)`<br>Specifies the percentage of the aggregate measure values of a compressed cube for Oracle OLAP to compute and store during a build or refresh operation.                                                                                    |
    | `void`                                                                         | `setPrecomputePercentTop``(int val)`<br>Specifies the percentage of the measure values for the top level of a hierarchy for Oracle OLAP to compute and store during a build or refresh operation.                                                                               |
    | `void`                                                                         | `setSparseType``(java.lang.String type)`<br>Specifies the sparsity type for the cube that contains this `AWCubeOrganization`.                                                                                                                                                   |
    | `void`                                                                         | `setSQLCubeStorageType``(`[`SQLDataType`](../../syntax/SQLDataType.md)` type)`<br>Specifies a SQL data type for the shared measure storage for the cube that contains this `AWCubeOrganization`.                                                                                |

    - ### Methods inherited from class oracle.olapi.metadata.deployment.[CubeOrganization](CubeOrganization.md)

      [`addSparseDimension`](CubeOrganization.md)`, `[`clearSparseDimensions`](CubeOrganization.md)`, `[`getCube`](CubeOrganization.md)`, `[`getSparseDimensions`](CubeOrganization.md)`, `[`removeSparseDimension`](CubeOrganization.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DENSE_SPARSE_TYPE

          public static final java.lang.String DENSE_SPARSE_TYPE

      A constant that indicates a dense cube.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPRESSED_SPARSE_TYPE

          public static final java.lang.String COMPRESSED_SPARSE_TYPE

      A constant that indicates an extremely sparse cube.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SPARSE_SPARSE_TYPE

          public static final java.lang.String SPARSE_SPARSE_TYPE

      A constant that indicates a sparse cube.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SPARSE_GLOBAL_SPARSE_TYPE

          public static final java.lang.String SPARSE_GLOBAL_SPARSE_TYPE

      A constant that indicates a sparse cube that has partitions and that stores all of the partitioned data in a single object.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_SPARSE_TYPES

          public static final java.lang.String[] VALID_SPARSE_TYPES

      A constant that has the valid values for sparsity type.

    <!-- -->

    - #### NONE_MV_OPTION

          public static final java.lang.String NONE_MV_OPTION

      A constant that indicates that Oracle OLAP does not a create materialized view for the cube.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPLETE_REFRESH_MV_OPTION

          public static final java.lang.String COMPLETE_REFRESH_MV_OPTION

      A constant that indicates that Oracle OLAP creates a materialized view that supports a complete refresh operation.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FAST_REFRESH_MV_OPTION

          public static final java.lang.String FAST_REFRESH_MV_OPTION

      A constant that indicates that Oracle OLAP creates a materialized view that supports a fast refresh operation.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FAST_REFRESH_READY_MV_OPTION

          public static final java.lang.String FAST_REFRESH_READY_MV_OPTION

      A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of a materialized view that is capable of a fast refresh.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REWRITE_MV_OPTION

          public static final java.lang.String REWRITE_MV_OPTION

      A constant that indicates that Oracle OLAP creates a materialized view that is accessible to the database query rewrite system.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REWRITE_WITH_ATTRIBUTES_MV_OPTION

          public static final java.lang.String REWRITE_WITH_ATTRIBUTES_MV_OPTION

      A constant that indicates that Oracle OLAP creates a materialized view that has query rewrite enabled and that includes columns for all `MdmDimensionLevel` attributes for which the [`MdmBaseAttribute.isPopulateLineage`](../mdm/MdmBaseAttribute.md) method returns `true`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REWRITE_READY_MV_OPTION

          public static final java.lang.String REWRITE_READY_MV_OPTION

      A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of an materialized viewt that is accessible to the database query rewrite system.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_MV_OPTIONS

          public static final java.lang.String[] VALID_MV_OPTIONS

      A constant that has the valid values for materialized view options.

    <!-- -->

    - #### SHARED_MEASURE_STORAGE

          public static final java.lang.String SHARED_MEASURE_STORAGE

      A constant that indicates that Oracle OLAP stores the values of all of the measures of the cube in the same object.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### INDEPENDENT_MEASURE_STORAGE

          public static final java.lang.String INDEPENDENT_MEASURE_STORAGE

      A constant that indicates that Oracle OLAP stores the values of each of the measures of the cube in a separate object.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_MEASURE_STORAGE_TYPES

          public static final java.lang.String[] VALID_MEASURE_STORAGE_TYPES

      A constant that has the valid values for the types of measure storage.

    <!-- -->

    - #### GENERIC_NULL_STORAGE

          public static final java.lang.String GENERIC_NULL_STORAGE

      A constant that indicates that Oracle OLAP does not distinguish between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MV_READY_NULL_STORAGE

          public static final java.lang.String MV_READY_NULL_STORAGE

      A constant that indicates that Oracle OLAP makes a distinction between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_NULL_STORAGE_TYPES

          public static final java.lang.String[] VALID_NULL_STORAGE_TYPES

      A constant that has the valid values for the types of storage of null values.

  <!-- -->

  - ### Method Detail

    - #### findOrCreateMVCreationOptions

          public MVCreationOptions findOrCreateMVCreationOptions()

      Gets the `MVCreationOptions` that is contained by this `AWCubeOrganization` or creates one if it does not already exist. The `MVCreationOptions` specifies options that Oracle OLAP uses when it creates a materialized view for the `MdmCube` that contains this `AWCubeOrganization`.
      With the `setMVOptions` method, you can specify the type of materialized view to create or you can specify not to create one for the cube. If you specify creating a type of materialized view, you can use an `MVCreationOptions` object to specify values that Oracle OLAP uses when it actually creates the MV.

      Returns:
      An `MVCreationOptions` that contains options that affect the creation of a materialized view.

    <!-- -->

    - #### getMVCreationOptions

          public final MVCreationOptions getMVCreationOptions()

      Gets the `MVCreationOptions` object of the AWCubeOrganization
      Returns:
      A `MVCreationOptions` object

    <!-- -->

    - #### setAW

          public final void setAW(AW aw)

      Specifies an `AW` as the container of the `MdmCube` that contains this `AWCubeOrganization`.
      Parameters:
      `aw` - The `AW` to contain the `MdmCube` of this `AWCubeOrganization`.

    <!-- -->

    - #### getSecondaryPartitionLevels

          public final java.util.List<SecondaryPartitionLevel> getSecondaryPartitionLevels()

      Gets the `SecondaryPartitionLevel` objects that are contained by this `AWCubeOrganization`.
      Returns:
      A `List` of the `SecondaryPartitionLevel` objects of this `AWCubeOrganization`.

    <!-- -->

    - #### removeSecondaryPartitionLevel

          public final void removeSecondaryPartitionLevel(SecondaryPartitionLevel partitionLevel)

      Removes the specified `SecondaryPartitionLevel` from those that are contained by this `AWCubeOrganization`.
      Parameters:
      `partitionLevel` - The `SecondaryPartitionLevel` to remove from this `AWCubeOrganization`.

    <!-- -->

    - #### addSecondaryPartitionLevel

          public void addSecondaryPartitionLevel(SecondaryPartitionLevel level,
                                                 int levelNumber)

      Adds a `SecondaryPartitionLevel` to the `List` of those that are contained by this `AWCubeOrganization`. The `levelNumber` parameter specifies the position in the list of the `SecondaryPartitionLevel`. Be sure to order the list so that the levels are in ascending order, with the lowest secondary partitioning level in the first position in the list. You can change the order of the `SecondaryPartitionLevel` objects in the list by removing a `SecondaryPartitionLevel` and then by specifying a different position when you add it back to the `AWCubeOrganization`. Oracle OLAP automatically reorders the positions of the subsequent members of the list.
      Parameters:
      `level` - The `SecondaryPartitionLevel` to add to this `AWCubeOrganization`.

      `levelNumber` - An integer that specifies a position in the `List` of `SecondaryPartitionLevel` objects.

    <!-- -->

    - #### findOrCreateSecondaryPartitionLevel

          public final SecondaryPartitionLevel findOrCreateSecondaryPartitionLevel(java.lang.String name)

      Gets the specified `SecondaryPartitionLevel` that is contained by this `AWCubeOrganization` or creates one if it does not already exist. An `AWCubeOrganization` can have up to three secondary partition levels in addition to the primary partition level that is specified by the `setPartitionLevel` method.
      Parameters:
      `name` - A `String` that contains the name of an existing `SecondaryPartitionLevel` or a name for a new one.

      Returns:
      The existing or new `SecondaryPartitionLevel`.

    <!-- -->

    - #### getPartitionLevel

          public final MdmHierarchyLevel getPartitionLevel()

      Gets the dimension level that is the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.
      Returns:
      The `MdmHierarchyLevel` that is the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.

    <!-- -->

    - #### setPartitionLevel

          public final void setPartitionLevel(MdmHierarchyLevel level)

      Specifies the dimension level to use as the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.
      Parameters:
      `level` - The `MdmHierarchyLevel` to use as the basis for the primary partitioning of the cube that contains this `AWCubeOrganization`.

    <!-- -->

    - #### getSparseType

          public final java.lang.String getSparseType()

      Gets the sparsity type of the cube that contains this `AWCubeOrganization`.
      Returns:
      A `String` that contains the sparsity type of the cube.

    <!-- -->

    - #### setSparseType

          public final void setSparseType(java.lang.String type)

      Specifies the sparsity type for the cube that contains this `AWCubeOrganization`. You can specify a sparsity type for all of the dimensions of the cube by using this method or you can specify individual dimensions as sparse by using the `addSparseDimension` method.
      The following table lists the constants that represent the valid values for the `type` parameter.

      | **Constant**                | **Description**                                                                                                                                                                                                                                             |
      |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `DENSE_SPARSE_TYPE`         | Specifies that the data in the cube is dense, which means that data exists for 80% or more of the measure values of the cube.                                                                                                                               |
      | `SPARSE_SPARSE_TYPE`        | Specifies that the data in the cube is sparse, which means that no data exists for more than 20% of the measure values of the cube.                                                                                                                         |
      | `COMPRESSED_SPARSE_TYPE`    | Specifies that the data in the cube is extremely sparse, which means that the cube has seven or more dimensions, some of which have hundreds of thousands of members, and some dimension hierarchies have many levels in which a parent has only one child. |
      | `SPARSE_GLOBAL_SPARSE_TYPE` | For a sparse cube that is partitioned, indicates the use of a single object to store data for all of the partitions. This type exists for backward compatibility. Do not specify this type for a new cube.                                                  |

      Parameters:
      `type` - A `String` that contains a sparsity type for the cube.

    <!-- -->

    - #### getMVOption

          public final java.lang.String getMVOption()

      Gets the materialized view option for the cube that contains this `AWCubeOrganization`.
      Returns:
      A `String` that contains the materialized view option for the cube.

    <!-- -->

    - #### setMVOption

          public final void setMVOption(java.lang.String option)

      Specifies the materialized view option for the cube that contains this `AWCubeOrganization`. This option determines the structure of the materialized view. The different types of materialized view have different requirements.
      To specify an MV option of `COMPLETE_REFRESH_MV_OPTION`, the cube must meet the following requirements.

      - The null storage option must be `MV_READY_NULL_STORAGE`, which is the default if the MV option is other than `NONE_MV_OPTION`.
      - The sparsity type must be `COMPRESSED_SPARSE_TYPE`.
      - The cube must have at least one dimension.
      - The MV option of all of the dimensions of the cube must be `COMPLETE_REFRESH_MV_OPTION`.

      To specify an MV option of `FAST_REFRESH_MV_OPTION` or `FAST_REFRESH_READY_MV_OPTION`, the cube must meet the following requirements in addition to the requirements for the `COMPLETE_REFRESH_MV_OPTION`.

      - The MV must not require aggregation or dimension joins.
      - The measures and dimensions must be mapped to a physical fact table and not a view.
      - The dimension members must have unique keys. The fact table must contain a primary key and the MV must include all columns of that primary key. The primary key constraints must be enabled and validated.

      To specify an MV option of `REWRITE_MV_OPTION` or `REWRITE_READY_MV_OPTION`, the cube must meet the following requirements in addition to the requirements for the `COMPLETE_REFRESH_MV_OPTION`.

      - The `ConsistentSolveSpecification` for the cube specify a single aggregation method over all of the hierarchies of all of the dimensions.
      - The aggregation method must be `SUM`, `MAX`, or `MIN`.
      - The leaf-level data in the analytic workspace must match the leaf-level data in the relational master tables; if it does not match, then a refresh must occur that uses the same aggregation method as the `ConsistentSolveSpecification`.
      - No dimension of the cube can have a value hierarchy.
      - No dimension can have a skip level or ragged hierarchy.
      - The hierarchy consistency rule of all of the dimensions must be `HIERARCHY_RULE_STAR_CONSISTENT`.

      The following table lists the constants that represent the valid values for the `option` parameter.

      | **Constant**                        | **Description**                                                                                                                                                                                                                  |
      |-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `NONE_MV_OPTION`                    | Specifies that Oracle OLAP does not create a materialized view for the cube.                                                                                                                                                     |
      | `COMPLETE_REFRESH_MV_OPTION`        | Specifies that Oracle OLAP creates a materialized view for the cube.                                                                                                                                                             |
      | `FAST_REFRESH_MV_OPTION`            | Specifies that Oracle OLAP creates a materialized view that supports an incremental refresh.                                                                                                                                     |
      | `FAST_REFRESH_READY_MV_OPTION`      | Specifies that Oracle OLAP determines that the conditions exist for the creation of a materialized view that is capable of a fast refresh but does not actually create the MV.                                                   |
      | `REWRITE_MV_OPTION`                 | Specifies that Oracle OLAP creates a materialized view that the database query rewrite system can use.                                                                                                                           |
      | `REWRITE_READY_MV_OPTION`           | Specifies that Oracle OLAP determines that the conditions exist for the creation of a rewrite materialized view but does not actually create the MV.                                                                             |
      | `REWRITE_MV_OPTION`                 | Specifies that Oracle OLAP creates a materialized view that the database query rewrite system can use.                                                                                                                           |
      | `REWRITE_WITH_ATTRIBUTES_MV_OPTION` | Specifies that Oracle OLAP creates a materialized view that has query rewrite enabled and that includes columns for all `MdmDimensionLevel` attributes for which the `MdmBaseAttribute.isPopulateLineage` method returns `true`. |

      If you specify the creation of a materialized view with this method, then you can use an `MVCreationOptions` object to specify options that Oracle OLAP uses when it actually creates the MV.
      Parameters:
      `option` - A `String` that contains a materialized view option for the cube.

    <!-- -->

    - #### getMeasureStorage

          public final java.lang.String getMeasureStorage()

      Gets the storage type of the measures of the cube that contains this `AWCubeOrganization`.
      Returns:
      A `String` that contains the measure storage type of the cube.

    <!-- -->

    - #### setMeasureStorage

          public final void setMeasureStorage(java.lang.String type)

      Specifies the measure storage type for the cube that contains this `AWCubeOrganization`. The following table lists the constants that represent the valid values for the `type` parameter.
      | **Constant**                  | **Description**                                                                                                                                                                                                                                                                                    |
      |-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `INDEPENDENT_MEASURE_STORAGE` | Specifies that Oracle OLAP stores the values of each of the measures of the cube in separate objects.                                                                                                                                                                                              |
      | `SHARED_MEASURE_STORAGE`      | Specifies that Oracle OLAP stores the values of all of the measures of the cube in the same object. Specify the shared measure storage type only if all of the measures have the same data type. If you use this type of storage, then specify the data type with the `setCubeStorageType` method. |

      Parameters:
      `type` - A `String` that contains a measure storage type for the cube.

    <!-- -->

    - #### getNullStorage

          public final java.lang.String getNullStorage()

      Gets the null storage type of the measures of the cube that contains this `AWCubeOrganization`.
      Returns:
      A `String` that contains the null storage type of the cube.

    <!-- -->

    - #### setNullStorage

          public final void setNullStorage(java.lang.String type)

      Specifies the null storage type for the cube that contains this `AWCubeOrganization`.
      The following table lists the constants that represent the valid values for the `type` parameter.

      | **Constant**            | **Description**                                                                                                                                           |
      |-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `GENERIC_NULL_STORAGE`  | Specifies that Oracle OLAP does not distinguish between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value. |
      | `MV_READY_NULL_STORAGE` | Specifies that Oracle OLAP makes a distinction between a true NA value and an NA value that exists because Oracle OLAP has not yet calculated the value.  |

      Parameters:
      `type` - A `String` that contains a null storage type for the cube.

    <!-- -->

    - #### getCubeStorageType

          public final java.lang.String getCubeStorageType()

      Gets the Oracle OLAP DML data type for the shared measure storage. However, if the SQL data type for the shared measure storage is not null, then this method returns the OLAP DML data type as converted by Oracle OLAP from the SQL data type.
      Returns:
      A `String` that contains the OLAP DML data type for the shared measure storage.

      See Also:
      `setCubeStorageType(java.lang.String)`, `setSQLCubeStorageType(oracle.olapi.syntax.SQLDataType)`

    <!-- -->

    - #### setCubeStorageType

          public final void setCubeStorageType(java.lang.String exp)

      Specifies the Oracle OLAP DML data type for the shared measure storage for the cube that contains this `AWCubeOrganization`. The OLAP DML data type applies to every measure of the cube. For information on the OLAP DML data types, see *Oracle OLAP DML Reference*.
      To specify an OLAP DML data type for the cube storage type, do the following:

      1.  Set the measure storage type of the cube to `SHARED_MEASURE_STORAGE` with the `setMeasureStorage` method.
      2.  Verify that the cube storage type is not a SQL data type by calling the `getSQLCubeStorageType` method. If that method returns a value other than `null`, then clear the value by calling the `setSQLCubeStorageType` method and passing it `null`.
      3.  Call this method and pass it a `String` that contains an OLAP DML data type.

      Parameters:
      `exp` - A `String` that contains an expression that resolves to the OLAP DML data type shared by all of the measures of the cube.

      See Also:
      `setMeasureStorage(java.lang.String)`, `setSQLCubeStorageType(oracle.olapi.syntax.SQLDataType)`

    <!-- -->

    - #### getSQLCubeStorageType

          public final SQLDataType getSQLCubeStorageType()

      Gets the SQL data type for the shared measure storage.
      Returns:
      The `SQLDataType` for the shared measure storage or `null` if the SQL data type has not been specified by the `setSQLCubeStorageType` method.

    <!-- -->

    - #### setSQLCubeStorageType

          public final void setSQLCubeStorageType(SQLDataType type)

      Specifies a SQL data type for the shared measure storage for the cube that contains this `AWCubeOrganization`. The SQL data type applies to every measure of the cube.
      To specify a SQL data type for the cube storage type, do the following:

      1.  Set the measure storage type of the cube to `SHARED_MEASURE_STORAGE` with the `setMeasureStorage` method.
      2.  Verify that the cube storage type is not an Oracle OLAP DML data type by calling the `getCubeStorageType` method. If that method returns a value other than `null`, then clear the value by calling the `setCubeStorageType` method and passing it `null`.
      3.  Call this method and pass it a `SQLDataType`.

      Parameters:
      `type` - A `SQLDataType` that contains the SQL data type that is shared by all of the measures of the cube.

      See Also:
      `setMeasureStorage(java.lang.String)`, `setCubeStorageType(java.lang.String)`

    <!-- -->

    - #### getPrecomputeCondition

          public SymmetricCondition getPrecomputeCondition()

      Gets the `SymmetricCondition` that specifies the dimension members for which Oracle OLAP computes and stores aggregate measure values during a build or refresh operation.
      Returns:
      The `SymmetricCondition` that specifies the dimension members for which Oracle OLAP precomputes measure values.

    <!-- -->

    - #### setPrecomputeCondition

          public void setPrecomputeCondition(SymmetricCondition cond)

      Specifies a `SymmetricCondition` that identifies the dimension members for which Oracle OLAP computes and stores aggregate measure values during a build or refresh operation. This precompute condition applies to any type of cube. If you specify a precompute condition, do not also specify precompute percent values.
      Parameters:
      `cond` - The `SymmetricCondition` that specifies the dimension members for which Oracle OLAP precomputes measure values.

    <!-- -->

    - #### getPrecomputePercent

          public final int getPrecomputePercent()

      Gets the percentage of the aggregate measure values for a compressed cube that Oracle OLAP computes and stores during a build or refresh operation.
      Returns:
      An integer that represents the percentage of the measure values that Oracle OLAP precomputes.

    <!-- -->

    - #### setPrecomputePercent

          public final void setPrecomputePercent(int val)

      Specifies the percentage of the aggregate measure values of a compressed cube for Oracle OLAP to compute and store during a build or refresh operation.
      Parameters:
      `val` - An integer that represents the percentage of the measure values for Oracle OLAP to precompute. The value can be 0 (zero) or greater.

    <!-- -->

    - #### getPrecomputePercentTop

          public final int getPrecomputePercentTop()

      Gets the percentage of the measure values for the top level of a hierarchy of a compressed and partitioned cube that Oracle OLAP computes and stores during a build or refresh operation.
      Returns:
      An integer that represents the percentage of the measure values for the top level of a hierarchy of a compressed and partitioned cube that Oracle OLAP precomputes.

    <!-- -->

    - #### setPrecomputePercentTop

          public final void setPrecomputePercentTop(int val)

      Specifies the percentage of the measure values for the top level of a hierarchy for Oracle OLAP to compute and store during a build or refresh operation.
      Parameters:
      `val` - An integer, which must be greater than 0 (zero), that represents the percentage of the measure values for the top level of a hierarchy of a compressed and partitioned cube for Oracle OLAP to precompute.

    <!-- -->

    - #### getAW

          public final AW getAW()

      Gets the analytic workspace that is associated with this `AWCubeOrganization`.
      Returns:
      The `AW` associated with this `AWCubeOrganization`.

    <!-- -->

    - #### addBuildSpecification

          public void addBuildSpecification(BuildSpecification spec)

      Adds a `BuildSpecification` to the list of those that are contained by this `AWCubeOrganization`.
      Parameters:
      `spec` - The `BuildSpecification` to add to this `AWCubeOrganization`.

    <!-- -->

    - #### removeBuildSpecification

          public void removeBuildSpecification(BuildSpecification spec)

      Removes a `BuildSpecification` from the list of those that are contained by this `AWCubeOrganization`.
      Parameters:
      `spec` - The `BuildSpecification` to remove from this `AWCubeOrganization`.

    <!-- -->

    - #### getBuildSpecifications

          public java.util.List<BuildSpecification> getBuildSpecifications()

      Gets the `BuildSpecification` objects that are contained by this `AWCubeOrganization`.
      Returns:
      A `List` of the `BuildSpecification` objects contained by this `AWCubeOrganization`.

    <!-- -->

    - #### getDefaultBuildSpecification

          public BuildSpecification getDefaultBuildSpecification()

      Gets the default `BuildSpecification` of this `AWCubeOrganization`.
      Returns:
      The default `BuildSpecification` for this `AWCubeOrganization`.

    <!-- -->

    - #### setDefaultBuildSpecification

          public void setDefaultBuildSpecification(BuildSpecification spec)

      Specifies a `BuildSpecification` to use as the default for this `AWCubeOrganization`.
      Parameters:
      `spec` - The `BuildSpecification` to use as the default for this `AWCubeOrganization`.

    <!-- -->

    - #### setMVCreationOptions

          public final void setMVCreationOptions(MVCreationOptions mvCreationOptions)

      Specifies an `MVCreationOptions` for this `AWCubeOrganization`. An `MVCreationOptions` contains options that Oracle OLAP uses when it creates a materialized view (MV) for an analytic workspace cube.
      Parameters:
      `mvCreationOptions` - The `MVCreationOptions` contained by this `AWCubeOrganization`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AWAttributeOrganization.md)
- [Next Class](AWPrimaryDimensionOrganization.md)

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
