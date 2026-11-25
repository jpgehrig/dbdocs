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

- [Prev Class](DeploymentException.md)
- [Next Class](PrimaryDimensionOrganization.md)

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

## Class MVCreationOptions

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.deployment.MVCreationOptions

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MVCreationOptions
      extends PublicMetadataObject

  A `BaseMetadataObject` that contains options that Oracle OLAP uses when it creates a materialized view (MV) for an analytic workspace cube or dimension. You create an `MVCreationOptions` with the `findOrCreateMVCreationOptions` method of an `AWCubeOrganization` or an `AWPrimaryDimensionOrganization`.
  The `setMVOption` method of an `AWCubeOrganization` or an `AWPrimaryDimensionOrganization` specifies the type of MV to create. If you do not create an `MVCreationOptions` object, then Oracle OLAP uses default option values when it creates the MV. With an `MVCreationOptions` you can specify values for the options. You can specify the type of method, the mode, and the type of constraints to use for the refreshing of the MV.

  You specify a refresh method type by using the `setRefreshType` method. The refresh method types are the following:

  - COMPLETE: Specifies a complete refresh of the MV, which involves of all the data for the materialized view.
  - FAST: Specifies an incremental refresh of the MV, which is involves only the data that changes due to changes in the data in the relational source master table.
  - FORCE: Specifies performing a fast refresh if possible, or otherwise performing a complete refresh.

  You specify a refresh mode with the `setRefreshOnOption` or the `setRefreshStartWithExpression` and the `setRefreshNextExpression` methods. If you specify a Refresh On mode, then do not specify a Refresh Starts With and Refresh Next mode. If you specify a Refresh Starts With and Refresh Next mode, then do not specify a Refresh On mode.

  The refresh modes are the following:

  - On Demand: Specifies a refresh initiated by the application. You can initiate a refresh by executing a `BuildProcess` that includes a `BuildItem` for the `MdmCube` or `MdmPrimaryDimension` with the MV. You execute a `BuildProcess` with a `DataProvider.executeBuild` method.
  - On Commit: Specifies a fast refresh whenever the database commits a transaction that changes the master table.
  - Start/Next: Specifies an automatic refresh that first occurs at the start time and recurs at intervals.

  Another aspect of creating an MV is to specify the whether or not to use enforced or trusted constraints when refreshing the MV. Trusted constraints can result in a more efficient refresh operation. However, if the trusted constraint information is invalid, then the refresh procedure may corrupt the MV. You specify the type of constraint with the `setUsingConstraints` method.

  For more information about how these options affect the creation of an MV, see the `create_mv_refresh` clause of the `CREATE MATERIALIZED VIEW` statement in *Oracle Database SQL Language Reference*.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type           | Field and Description                                                                                                                                                                    |
    |-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`   | `REFRESH_ON_COMMIT`<br>A constant that represents the refresh on commit mode, which indicates that a refresh occurs when the database commits a transaction that affects a source table. |
    | `static java.lang.String`   | `REFRESH_ON_DEFAULT`<br>A constant that represents the refresh on default mode, which indicates that a refresh occurs on the default setting.                                            |
    | `static java.lang.String`   | `REFRESH_ON_DEMAND`<br>A constant that represents the refresh on demand mode, which indicates that a refresh occurs on demand.                                                           |
    | `static java.lang.String`   | `REFRESH_TYPE_COMPLETE`<br>A constant that represents a complete refresh method type.                                                                                                    |
    | `static java.lang.String`   | `REFRESH_TYPE_DEFAULT`<br>A constant that represents the default refresh method type.                                                                                                    |
    | `static java.lang.String`   | `REFRESH_TYPE_FAST`<br>A constant that represents a fast refresh method type.                                                                                                            |
    | `static java.lang.String`   | `REFRESH_TYPE_FORCE`<br>A constant that represents a force refresh method type.                                                                                                          |
    | `static java.lang.String[]` | `VALID_REFRESH_ON_OPTIONS`<br>A constant that has the valid values for the conditions that initiate a refresh.                                                                           |
    | `static java.lang.String[]` | `VALID_REFRESH_TYPES`<br>A constant that has the valid values for the refresh method type.                                                                                               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                           |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getName``()`<br>Gets the name of this `MVCreationOptions`.                                                                                                                      |
    | `java.lang.String` | `getRefreshNextExpression``()`<br>Gets the expression that indicates when the next refresh of the MV occurs.                                                                     |
    | `java.lang.String` | `getRefreshOnOption``()`<br>Gets the mode that Oracle OLAP uses to determine when to refresh the data for the MV that is associated with the dimension or cube.                  |
    | `java.lang.String` | `getRefreshStartWithExpression``()`<br>Gets the expression that indicates when the initial refresh of the MV occurs.                                                             |
    | `java.lang.String` | `getRefreshType``()`<br>Gets the type of refresh method specified by this `MVCreationOptions`.                                                                                   |
    | `java.lang.String` | `getUsingConstraints``()`<br>Gets the value of the setting that specifies whether a refresh operation uses enforced or trusted contraints.                                       |
    | `void`             | `setRefreshNextExpression``(java.lang.String exp)`<br>Specifies an expression that determines the interval between automatic refreshes.                                          |
    | `void`             | `setRefreshOnOption``(java.lang.String option)`<br>Specifies the mode that Oracle OLAP uses to determine when to refresh the MV.                                                 |
    | `void`             | `setRefreshStartWithExpression``(java.lang.String exp)`<br>Specifies an expression that determines when the initial automatic refresh of the MV occurs.                          |
    | `void`             | `setRefreshType``(java.lang.String type)`<br>Specifies the type of refresh method that the database uses when it refreshes the MV that is associated with the cube or dimension. |
    | `void`             | `setUsingConstraints``(java.lang.String exp)`<br>Specifies whether to use enforced or trusted constraints for refreshing the MV.                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### REFRESH_TYPE_FAST

          public static final java.lang.String REFRESH_TYPE_FAST

      A constant that represents a fast refresh method type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REFRESH_TYPE_COMPLETE

          public static final java.lang.String REFRESH_TYPE_COMPLETE

      A constant that represents a complete refresh method type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REFRESH_TYPE_FORCE

          public static final java.lang.String REFRESH_TYPE_FORCE

      A constant that represents a force refresh method type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REFRESH_TYPE_DEFAULT

          public static final java.lang.String REFRESH_TYPE_DEFAULT

      A constant that represents the default refresh method type.

    <!-- -->

    - #### VALID_REFRESH_TYPES

          public static final java.lang.String[] VALID_REFRESH_TYPES

      A constant that has the valid values for the refresh method type.

    <!-- -->

    - #### VALID_REFRESH_ON_OPTIONS

          public static final java.lang.String[] VALID_REFRESH_ON_OPTIONS

      A constant that has the valid values for the conditions that initiate a refresh.

    <!-- -->

    - #### REFRESH_ON_DEFAULT

          public static final java.lang.String REFRESH_ON_DEFAULT

      A constant that represents the refresh on default mode, which indicates that a refresh occurs on the default setting.

    <!-- -->

    - #### REFRESH_ON_DEMAND

          public static final java.lang.String REFRESH_ON_DEMAND

      A constant that represents the refresh on demand mode, which indicates that a refresh occurs on demand.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### REFRESH_ON_COMMIT

          public static final java.lang.String REFRESH_ON_COMMIT

      A constant that represents the refresh on commit mode, which indicates that a refresh occurs when the database commits a transaction that affects a source table.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getRefreshType

          public final java.lang.String getRefreshType()

      Gets the type of refresh method specified by this `MVCreationOptions`.
      Returns:
      A `String` that contains the type of refresh method for the MV.

    <!-- -->

    - #### setRefreshType

          public final void setRefreshType(java.lang.String type)

      Specifies the type of refresh method that the database uses when it refreshes the MV that is associated with the cube or dimension. The following table lists the constants that represent the valid values for the `type` parameter.
      | Constant                | Description                                                                                                                                                                                                                                                 |
      |-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | `REFRESH_TYPE_COMPLETE` | Refresh all of the data for the cube.                                                                                                                                                                                                                       |
      | `REFRESH_TYPE_FAST`     | Refresh only the data for the cube that needs to change due to changes to the relational source master tables. A fast refresh is possible only if the master tables support the operation. If fast refresh is not possible, the operation does not succeed. |
      | `REFRESH_TYPE_FORCE`    | Perform a fast refresh if possible, otherwise perform a complete refresh.                                                                                                                                                                                   |
      | `REFRESH_TYPE_DEFAULT`  | Use the default refresh type, which is `FORCE`.                                                                                                                                                                                                             |

      Parameters:
      `type` - A `String` that contains a refresh method type for the MV.

    <!-- -->

    - #### getRefreshStartWithExpression

          public final java.lang.String getRefreshStartWithExpression()

      Gets the expression that indicates when the initial refresh of the MV occurs.
      Returns:
      A `String` that contains an expression that indicates when the initial refresh of the MV occurs.

    <!-- -->

    - #### setRefreshStartWithExpression

          public final void setRefreshStartWithExpression(java.lang.String exp)

      Specifies an expression that determines when the initial automatic refresh of the MV occurs. You specify a time interval for the next automatic refresh with the `setRefreshNextExpression` method. If you specify a time to start automatic refreshes but you do not specify time for the next refresh, then the automatic refresh occurs only once, at the time specified by this method.
      If you specify a time to start automatic refreshes, then you should not specify a Refresh On mode.

      Parameters:
      `exp` - A `String` that contains an expression that evaluates to a future datetime value.

    <!-- -->

    - #### getRefreshNextExpression

          public final java.lang.String getRefreshNextExpression()

      Gets the expression that indicates when the next refresh of the MV occurs.
      Returns:
      A `String` that contains an expression that indicates when the next refresh of the MV occurs.

    <!-- -->

    - #### setRefreshNextExpression

          public final void setRefreshNextExpression(java.lang.String exp)

      Specifies an expression that determines the interval between automatic refreshes. If you specify a next refresh time, then you should also set the time for the initial refresh with the `setRefreshStartWithExpression` method. If you do not set the time for the initial refresh, then the database determines the first automatic refresh time by evaluating the expression specified by this method in relation to the creation time of the MV.
      If you specify a time inteval for automatic refreshes, then you should not specify a Refresh On mode.

      Parameters:
      `exp` - A `String` that contains an expression that evaluates to a future datetime value.

    <!-- -->

    - #### getRefreshOnOption

          public final java.lang.String getRefreshOnOption()

      Gets the mode that Oracle OLAP uses to determine when to refresh the data for the MV that is associated with the dimension or cube.
      Returns:
      A `String` that contains the mode that determines when Oracle OLAP refreshes the data in the MV.

    <!-- -->

    - #### setRefreshOnOption

          public final void setRefreshOnOption(java.lang.String option)

      Specifies the mode that Oracle OLAP uses to determine when to refresh the MV. The following table lists the constants that represent the valid values for the `option` parameter.
      | Constant             | Description                                                                                                      |
      |----------------------|------------------------------------------------------------------------------------------------------------------|
      | `REFRESH_ON_DEMAND`  | Specifies that Oracle OLAP refreshes the MV on demand.                                                           |
      | `REFRESH_ON_COMMIT`  | Specifies that Oracle OLAP refreshes the MV when the database commits a transaction that affects a master table. |
      | `REFRESH_ON_DEFAULT` | Specifies that Oracle OLAP refreshes the MV on the default setting, which is On Demand.                          |

      If you specify a Refresh On mode, then you should not specify a Starts With or Next time period for automatic refreshes.

      Parameters:
      `option` - A `String` that contains a refresh on option for the cube.

    <!-- -->

    - #### getUsingConstraints

          public final java.lang.String getUsingConstraints()

      Gets the value of the setting that specifies whether a refresh operation uses enforced or trusted contraints.
      Returns:
      A `String` that contains `ENFORCED` or `TRUSTED`.

    <!-- -->

    - #### setUsingConstraints

          public final void setUsingConstraints(java.lang.String exp)

      Specifies whether to use enforced or trusted constraints for refreshing the MV. Trusted constraints can result in more a efficient refresh operation. However, if the trusted constraint information is invalid, then the refresh procedure may corrupt the MV.
      Parameters:
      `exp` - A `String` that contains `ENFORCED` or `TRUSTED`.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `MVCreationOptions`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of this `MVCreationOptions`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DeploymentException.md)
- [Next Class](PrimaryDimensionOrganization.md)

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
