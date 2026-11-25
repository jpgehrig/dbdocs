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

- [Prev Class](AWCubeOrganization.md)
- [Next Class](CubeOrganization.md)

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

## Class AWPrimaryDimensionOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.deployment.PrimaryDimensionOrganization](PrimaryDimensionOrganization.md)

      - - oracle.olapi.metadata.deployment.AWPrimaryDimensionOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class AWPrimaryDimensionOrganization
      extends PrimaryDimensionOrganization

  A `PrimaryDimensionOrganization` for an analytic workspace. An `AWPrimaryDimensionOrganization` contains information about how the data for an `MdmPrimaryDimension` is organized and maintained by Oracle OLAP. An application creates an `AWPrimaryDimensionOrganization` with the [`findOrCreateAWPrimaryDimensionOrganization`](../mdm/MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`.
  With the `setMVOption` method, you can specify the creation of an MV (materialized view) for the dimension. With the `findOrCreateMVCreationOptions` method you can get or create an object that contains options that affect the MV.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type           | Field and Description                                                                                                                                                                                                                           |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`   | `COMPLETE_REFRESH_MV_OPTION`<br>A constant that indicates that Oracle OLAP creates a materialized view that supports a complete refresh operation.                                                                                              |
    | `static java.lang.String`   | `COMPLETE_REFRESH_READY_MV_OPTION`<br>A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of a materialized view that is capable of a complete refresh.                             |
    | `static java.lang.String`   | `HIERARCHY_RULE_CONSISTENT`<br>A constant that indicates that the parent-child relationships are consistent across the hierarchies of the dimension.                                                                                            |
    | `static java.lang.String`   | `HIERARCHY_RULE_SOLVE_CONSISTENT`<br>A constant that indicates that the parent-child relationships only need to be consistent across the hierarchies of the dimension when the hierarchies appear together in a `ConsistentSolveSpecification`. |
    | `static java.lang.String`   | `HIERARCHY_RULE_STAR_CONSISTENT`<br>A constant that indicates that the hierarchies of the dimension are consistent with a star schema organization.                                                                                             |
    | `static java.lang.String`   | `NONE_MV_OPTION`<br>A constant that indicates that Oracle OLAP does not a create materialized view for the dimension.                                                                                                                           |
    | `static java.lang.String[]` | `VALID_HIERARCHY_RULES`<br>A constant that has the valid values for hierarchy rules.                                                                                                                                                            |
    | `static java.lang.String[]` | `VALID_MV_OPTIONS`<br>A constant that has the valid values for materialized view options.                                                                                                                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                          |
    |------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MVCreationOptions`](MVCreationOptions.md)                | `findOrCreateMVCreationOptions``()`<br>Gets the `MVCreationOptions` that is associated with this `AWPrimaryDimensionOrganization` or creates one if it does not already exist.                                  |
    | `boolean`                                                  | `getAddUniqueKeyPrefix``()`<br>Indicates whether or not each member of this dimension has a unique level-based prefix added to the key expressions when a build loads the data into the analytic workspace.     |
    | [`AWAttributeOrganization`](AWAttributeOrganization.md)    | `getAttributeOrganization``(`[`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md)` attr)`<br>Gets the `AWAttributeOrganization` that is associated with the specified `MdmBaseAttribute`.                           |
    | `java.util.List`                                           | `getAttributeOrganizations``()`<br>Gets the `AWAttributeOrganization` objects that are associated with this `AWPrimaryDimensionOrganization`.                                                                   |
    | [`AW`](AW.md)                                              | `getAW``()`<br>Gets the analytic workspace that is associated with this `AWPrimaryDimensionOrganization`.                                                                                                       |
    | [`BuildSpecification`](../../syntax/BuildSpecification.md) | `getDefaultBuildSpecification``()`<br>Gets the default `BuildSpecification` of this `AWPrimaryDimensionOrganization`.                                                                                           |
    | `java.lang.String`                                         | `getHierarchyConsistencyRule``()`<br>Gets the hierarchy consistency rule that is associated with this `AWPrimaryDimensionOrganization`.                                                                         |
    | [`MVCreationOptions`](MVCreationOptions.md)                | `getMVCreationOptions``()`<br>Gets the `MVCreationOptions` object of the AWPrimaryDimensionOrganization                                                                                                         |
    | `java.lang.String`                                         | `getMVOption``()`<br>Gets the materialized view option for the dimension that is associated with this `AWPrimaryDimensionOrganization`.                                                                         |
    | `void`                                                     | `removeAttributeOrganization``(`[`AWAttributeOrganization`](AWAttributeOrganization.md)` org)`<br>Removes the specified `AWAttributeOrganization` from this `AWPrimaryDimensionOrganization`.                   |
    | `void`                                                     | `setAddUniqueKeyPrefix``(boolean val)`<br>Specifies whether each member of this dimension has a unique level-based prefix added to the key expressions when a build loads the data into the analytic workspace. |
    | `void`                                                     | `setAW``(`[`AW`](AW.md)` aw)`<br>Specifies an analytic workspace with which to associate this `AWPrimaryDimensionOrganization`.                                                                                 |
    | `void`                                                     | `setDefaultBuildSpecification``(`[`BuildSpecification`](../../syntax/BuildSpecification.md)` spec)`<br>Specifies a `BuildSpecification` to use as the default for this `AWPrimaryDimensionOrganization`.        |
    | `void`                                                     | `setHierarchyConsistencyRule``(java.lang.String option)`<br>Specifies the hierarchy consistency rule for the dimension that is associated with this `AWPrimaryDimensionOrganization`.                           |
    | `void`                                                     | `setMVCreationOptions``(`[`MVCreationOptions`](MVCreationOptions.md)` mvCreationOptions)`<br>Specifies an `MVCreationOptions` to associate with this `AWPrimaryDimensionOrganization`.                          |
    | `void`                                                     | `setMVOption``(java.lang.String option)`<br>Specifies the materialized view option for the dimension that is associated with this `AWPrimaryDimensionOrganization`.                                             |

    - ### Methods inherited from class oracle.olapi.metadata.deployment.[PrimaryDimensionOrganization](PrimaryDimensionOrganization.md)

      [`getPrimaryDimension`](PrimaryDimensionOrganization.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NONE_MV_OPTION

          public static final java.lang.String NONE_MV_OPTION

      A constant that indicates that Oracle OLAP does not a create materialized view for the dimension.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPLETE_REFRESH_MV_OPTION

          public static final java.lang.String COMPLETE_REFRESH_MV_OPTION

      A constant that indicates that Oracle OLAP creates a materialized view that supports a complete refresh operation.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPLETE_REFRESH_READY_MV_OPTION

          public static final java.lang.String COMPLETE_REFRESH_READY_MV_OPTION

      A constant that indicates that Oracle OLAP determines that the conditions exist that permit the future creation of a materialized view that is capable of a complete refresh.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_MV_OPTIONS

          public static final java.lang.String[] VALID_MV_OPTIONS

      A constant that has the valid values for materialized view options.

    <!-- -->

    - #### HIERARCHY_RULE_CONSISTENT

          public static final java.lang.String HIERARCHY_RULE_CONSISTENT

      A constant that indicates that the parent-child relationships are consistent across the hierarchies of the dimension.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### HIERARCHY_RULE_SOLVE_CONSISTENT

          public static final java.lang.String HIERARCHY_RULE_SOLVE_CONSISTENT

      A constant that indicates that the parent-child relationships only need to be consistent across the hierarchies of the dimension when the hierarchies appear together in a `ConsistentSolveSpecification`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### HIERARCHY_RULE_STAR_CONSISTENT

          public static final java.lang.String HIERARCHY_RULE_STAR_CONSISTENT

      A constant that indicates that the hierarchies of the dimension are consistent with a star schema organization.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_HIERARCHY_RULES

          public static final java.lang.String[] VALID_HIERARCHY_RULES

      A constant that has the valid values for hierarchy rules.

  <!-- -->

  - ### Method Detail

    - #### findOrCreateMVCreationOptions

          public MVCreationOptions findOrCreateMVCreationOptions()

      Gets the `MVCreationOptions` that is associated with this `AWPrimaryDimensionOrganization` or creates one if it does not already exist. The `MVCreationOptions` specifies options that Oracle OLAP uses when it creates a materialized view for the `MdmPrimaryDimension` that is associated with this `AWPrimaryDimensionOrganization`.
      With the `setMVOptions` method, you can specify whether or not to create MVs for the dimension. If you specify creating MVs, you can use an `MVCreationOptions` object to specify values that Oracle OLAP uses when it actually creates the MVs.

      Returns:
      An `MVCreationOptions` that contains options that affect the creation of materialized views.

    <!-- -->

    - #### getMVCreationOptions

          public final MVCreationOptions getMVCreationOptions()

      Gets the `MVCreationOptions` object of the AWPrimaryDimensionOrganization
      Returns:
      A `MVCreationOptions` object

    <!-- -->

    - #### getAddUniqueKeyPrefix

          public final boolean getAddUniqueKeyPrefix()

      Indicates whether or not each member of this dimension has a unique level-based prefix added to the key expressions when a build loads the data into the analytic workspace.
      Returns:
      A `boolean` that is `true` if a unique prefix is added to the key expressions or `false` otherwise.

    <!-- -->

    - #### setAddUniqueKeyPrefix

          public final void setAddUniqueKeyPrefix(boolean val)

      Specifies whether each member of this dimension has a unique level-based prefix added to the key expressions when a build loads the data into the analytic workspace.
      Parameters:
      `val` - A `boolean` that is `true` if a unique prefix is added to the key expressions or `false` otherwise.

    <!-- -->

    - #### getHierarchyConsistencyRule

          public final java.lang.String getHierarchyConsistencyRule()

      Gets the hierarchy consistency rule that is associated with this `AWPrimaryDimensionOrganization`.
      Returns:
      A `String` that contains the hierarchy consistency rule for the dimension.

    <!-- -->

    - #### setHierarchyConsistencyRule

          public final void setHierarchyConsistencyRule(java.lang.String option)

      Specifies the hierarchy consistency rule for the dimension that is associated with this `AWPrimaryDimensionOrganization`. The hierarchy consistency rule indicates the organization with which the parent-child relationships of the hierarchies are consistent.
      The following table lists the constants that represent the valid values for the `option` parameter.

      **Note:** To create materialized views for the dimension, the hierarchies of the dimension must be consistent with a star schema organization.

      | **Constant**                      | **Description**                                                                                                                                                                                                                                                                                                                                                     |
      |-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `HIERARCHY_RULE_CONSISTENT`       | Specifies that the parent-child relationships are consistent across the hierarchies of the dimension.                                                                                                                                                                                                                                                               |
      | `HIERARCHY_RULE_SOLVE_CONSISTENT` | Specifies that the parent-child relationships are not consistent across the hierarchies of the dimension. An example of inconsistent hierarchies occurs when the parent-child relationship is reversed in two hierarchies. For example, in hierarchy 1, dimension member A is the parent of member B, while and in hierarchy 2, member B is the parent of member A. |
      | `HIERARCHY_RULE_STAR_CONSISTENT`  | Specifies that the hierarchies of the dimension are consistent with a star schema organization.                                                                                                                                                                                                                                                                     |

      Parameters:
      `option` - A `String` that contains a hierarchy consistency rule for the dimension.

    <!-- -->

    - #### getAW

          public final AW getAW()

      Gets the analytic workspace that is associated with this `AWPrimaryDimensionOrganization`.
      Returns:
      The `AW` associated with this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### setAW

          public final void setAW(AW aw)

      Specifies an analytic workspace with which to associate this `AWPrimaryDimensionOrganization`.
      Parameters:
      `aw` - The `AW` with which to associate this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### getAttributeOrganizations

          public java.util.List getAttributeOrganizations()

      Gets the `AWAttributeOrganization` objects that are associated with this `AWPrimaryDimensionOrganization`.
      Returns:
      A `List` of the `AWAttributeOrganization` objects associated with this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### getAttributeOrganization

          public AWAttributeOrganization getAttributeOrganization(MdmBaseAttribute attr)

      Gets the `AWAttributeOrganization` that is associated with the specified `MdmBaseAttribute`. If the `AWAttributeOrganization` does not already exit, then this method creates one and adds it to the list of `AWAttributeOrganization` objects for this `AWPrimaryDimensionOrganization`.
      Parameters:
      `attr` - The `AWAttributeOrganization` associated with the specified `MdmBaseAttribute`.

      Returns:
      The `AWAttributeOrganization` associated with the specified `MdmBaseAttribute`.

    <!-- -->

    - #### removeAttributeOrganization

          public void removeAttributeOrganization(AWAttributeOrganization org)

      Removes the specified `AWAttributeOrganization` from this `AWPrimaryDimensionOrganization`.
      Parameters:
      `org` - The `AWAttributeOrganization` to remove from this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### getMVOption

          public final java.lang.String getMVOption()

      Gets the materialized view option for the dimension that is associated with this `AWPrimaryDimensionOrganization`.
      Returns:
      A `String` that contains the materialized view option for the dimension.

    <!-- -->

    - #### setMVOption

          public final void setMVOption(java.lang.String option)

      Specifies the materialized view option for the dimension that is associated with this `AWPrimaryDimensionOrganization`. The creation of a materialized view for the dimension requires that the hierarchy consistency rule is `HIERARCHY_RULE_STAR_CONSISTENT`. If you specify the creation of a materialized view with this method, then you can use an `MVCreationOptions` object to specify options that Oracle OLAP uses when it actually creates the MV.
      The following table lists the constants that represent the valid values for the `option` parameter.

      | **Constant**                       | **Description**                                                                                                                                                                                   |
      |------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `NONE_MV_OPTION`                   | Specifies that Oracle OLAP does create materialized views for the dimension.                                                                                                                      |
      | `COMPLETE_REFRESH_MV_OPTION`       | Specifies that Oracle OLAP that creates a materialized views that supports a complete refresh operation.                                                                                          |
      | `COMPLETE_REFRESH_READY_MV_OPTION` | Specifies that Oracle OLAP determines that the conditions exist that permit the future creation of a materialized view that is capable of a complete refresh but does not actually create the MV. |

      For more information on materialized views for an analytic workspace, see *Oracle OLAP User's Guide*.

      Parameters:
      `option` - A `String` that contains a materialized view option for the dimension.

    <!-- -->

    - #### setMVCreationOptions

          public final void setMVCreationOptions(MVCreationOptions mvCreationOptions)

      Specifies an `MVCreationOptions` to associate with this `AWPrimaryDimensionOrganization`. An `MVCreationOptions` contains options that Oracle OLAP uses when it creates a materialized view (MV) for an analytic workspace dimension.
      Parameters:
      `mvCreationOptions` - The `MVCreationOptions` to associate with this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### getDefaultBuildSpecification

          public BuildSpecification getDefaultBuildSpecification()

      Gets the default `BuildSpecification` of this `AWPrimaryDimensionOrganization`.
      Returns:
      The default `BuildSpecification` for this `AWPrimaryDimensionOrganization`.

    <!-- -->

    - #### setDefaultBuildSpecification

          public void setDefaultBuildSpecification(BuildSpecification spec)

      Specifies a `BuildSpecification` to use as the default for this `AWPrimaryDimensionOrganization`.
      Parameters:
      `spec` - The `BuildSpecification` to use as the default for this `AWPrimaryDimensionOrganization`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AWCubeOrganization.md)
- [Next Class](CubeOrganization.md)

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
