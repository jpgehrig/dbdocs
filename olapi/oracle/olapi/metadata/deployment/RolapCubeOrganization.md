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

- [Prev Class](PrimaryDimensionOrganization.md)
- [Next Class](RolapPrimaryDimensionOrganization.md)

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

## Class RolapCubeOrganization

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.deployment.CubeOrganization](CubeOrganization.md)

      - - oracle.olapi.metadata.deployment.RolapCubeOrganization

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class RolapCubeOrganization
      extends CubeOrganization

  A `CubeOrganization` for a relational deployment of an `MdmCube`. A `RolapCubeOrganization` specifies the form of SQL `SELECT` statement that organizes the data of the measures of the cube. To get an existing `RolapCubeOrganization` or to create a new one, use the [`findOrCreateRolapCubeOrganization`](../mdm/MdmCube.md) method of the `MdmCube`.
  The SQL `SELECT` statement can use a `GROUP BY ROLLUP` or `GROUP BY GROUPING SETS` clause, or it can use an embedded totals column of a view. For more information on the `GROUP BY` clauses, see *Oracle Database Data Warehousing Guide* or *Oracle Database SQL Reference*.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type           | Field and Description                                                                                                                                                                       |
    |-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`   | `ET_FORM`<br>A constant that represents an organization of the measure data of the cube that results from the use of an embedded totals column of a view in the `SELECT` statement.         |
    | `static java.lang.String`   | `GROUPING_SET_FORM`<br>A constant that represents an organization of the measure data of the cube that results from the use of a `GROUP BY GROUPING SETS` clause in the `SELECT` statement. |
    | `static java.lang.String`   | `ROLLUP_FORM`<br>A constant that represents an organization of the measure data of the cube that results from the use of a `GROUP BY ROLLUP` clause in the `SELECT` statement.              |
    | `static java.lang.String[]` | `VALID_GROUPING_FORMS`<br>A constant that has the valid values for the forms of organization.                                                                                               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                       |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getGroupingForm``()`<br>Gets the grouping form for the cube that is associated this `RolapCubeOrganization`.                                |
    | `java.lang.String` | `getName``()`<br>Gets the name of this `MetadataObject`.                                                                                     |
    | `void`             | `setGroupingForm``(java.lang.String type)`<br>Specifies the grouping form for the cube that is associated with this `RolapCubeOrganization`. |

    - ### Methods inherited from class oracle.olapi.metadata.deployment.[CubeOrganization](CubeOrganization.md)

      [`addSparseDimension`](CubeOrganization.md)`, `[`clearSparseDimensions`](CubeOrganization.md)`, `[`getCube`](CubeOrganization.md)`, `[`getSparseDimensions`](CubeOrganization.md)`, `[`removeSparseDimension`](CubeOrganization.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ROLLUP_FORM

          public static final java.lang.String ROLLUP_FORM

      A constant that represents an organization of the measure data of the cube that results from the use of a `GROUP BY ROLLUP` clause in the `SELECT` statement.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### GROUPING_SET_FORM

          public static final java.lang.String GROUPING_SET_FORM

      A constant that represents an organization of the measure data of the cube that results from the use of a `GROUP BY GROUPING SETS` clause in the `SELECT` statement.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ET_FORM

          public static final java.lang.String ET_FORM

      A constant that represents an organization of the measure data of the cube that results from the use of an embedded totals column of a view in the `SELECT` statement.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VALID_GROUPING_FORMS

          public static final java.lang.String[] VALID_GROUPING_FORMS

      A constant that has the valid values for the forms of organization.

  <!-- -->

  - ### Method Detail

    - #### getGroupingForm

          public final java.lang.String getGroupingForm()

      Gets the grouping form for the cube that is associated this `RolapCubeOrganization`. The grouping form is one of the values indicated by the `VALID_GROUPING_FORMS` constant.
      Returns:
      A `String` that contains the null storage type of the cube.

    <!-- -->

    - #### setGroupingForm

          public final void setGroupingForm(java.lang.String type)

      Specifies the grouping form for the cube that is associated with this `RolapCubeOrganization`.
      The grouping form can be one of the following constants:
         `ET_FORM`
         `ROLLUP_FORM`
         `GROUPING_SET_FORM`

      The following table lists the constants that represent the valid values for the `type` parameter.

      | Constant            | Description                                                                                                                                 |
      |---------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
      | `ET_FORM`           | Indicates that Oracle OLAP uses the embedded totals column of a view in the `SELECT` statement that specifies the measure data of the cube. |
      | `ROLLUP_FORM`       | Indicates that Oracle OLAP uses a `GROUP BY ROLLUP` clause in the `SELECT` statement that specifies the measure data of the cube.           |
      | `GROUPING_SET_FORM` | Indicates that Oracle OLAP uses a `GROUP BY GROUPING SETS` clause in the `SELECT` statement that specifies the measure data of the cube.    |

      Parameters:
      `type` - A `String` that contains a grouping form for the cube.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `MetadataObject`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of this `MetadataObject`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](PrimaryDimensionOrganization.md)
- [Next Class](RolapPrimaryDimensionOrganization.md)

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
