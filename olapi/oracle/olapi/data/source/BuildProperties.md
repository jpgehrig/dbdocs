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

- [Prev Class](BooleanSource.md)
- [Next Class](BuildResult.md)

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

oracle.olapi.data.source

## Class BuildProperties

- java.lang.Object

- - oracle.olapi.data.source.BuildProperties

<!-- -->

-

  ------------------------------------------------------------------------



      public final class BuildProperties
      extends java.lang.Object

  Contains properties that affect a `BuildProcess`. You can create a new `BuildProperties`, set properties for a build, and then pass the `BuildProperties` to a `DataProvider.executeBuild` method.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `BuildProperties``()`<br>Creates a new `BuildProperties` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                         |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `getAddDimensions``()`<br>Indicates whether or not the build process includes all of the dimensions of the cubes in the build or only the dimensions specified by the `BuildProcess`.                                                                          |
    | `boolean`          | `getAtomicRefresh``()`<br>Indicates whether or not to prevent other users from having access to intermediate results during a build.                                                                                                                           |
    | `boolean`          | `getAutomaticOrder``()`<br>Indicates whether the build process automatically reorders the cubes and dimensions in the build, or whether it builds the items in the exact order specified by the `BuildProcess`.                                                |
    | `java.lang.String` | `getJobClass``()`<br>Gets the job class for the build.                                                                                                                                                                                                         |
    | `boolean`          | `getNestedRefresh``()`<br>Indicates whether or not the build process includes all of the dependent cubes in the build or only the cubes specified by the `BuildProcess`.                                                                                       |
    | `int`              | `getParallelism``()`<br>Get the number of parallel processes to allocate to the build process.                                                                                                                                                                 |
    | `boolean`          | `getRebuildFreepools``()`<br>Indicates whether or not the `BuildProcess` will rebuild the freepools on the AW\$ table.                                                                                                                                         |
    | `boolean`          | `getRefreshAfterErrors``()`<br>Indicates whether the build should stop immediately when it encounters an error or whether it should rollback the changes to the failed cube or dimension and attempt to continue with the other items in the build.            |
    | `java.lang.String` | `getRefreshMethod``()`<br>Gets the refresh method for the build.                                                                                                                                                                                               |
    | `java.lang.String` | `getSchedulerJobName``()`<br>Gets the text identifier for the build.                                                                                                                                                                                           |
    | `void`             | `setAddDimensions``(boolean val)`<br>Specifies whether or not the build process includes all of the dimensions of the cubes in the build or only the dimensions specified by the `BuildProcess`.                                                               |
    | `void`             | `setAtomicRefresh``(boolean val)`<br>Specifies whether or not to prevent other users from having access to intermediate results during a build.                                                                                                                |
    | `void`             | `setAutomaticOrder``(boolean val)`<br>Specifies whether the build process should automatically reorder the cubes and dimensions in the build, or whether it should build the items in the exact order specified by the `BuildProcess`.                         |
    | `void`             | `setJobClass``(java.lang.String jobClass)`<br>Specifies the job class to be used by the scheduler when scheduling builds.                                                                                                                                      |
    | `void`             | `setNestedRefresh``(boolean val)`<br>Specifies whether or not the build process includes all of the dependent cubes in the build or only the cubes specified by the `BuildProcess`.                                                                            |
    | `void`             | `setParallelism``(int n)`<br>Specifies the number of parallel processes to allocate to the build process.                                                                                                                                                      |
    | `void`             | `setRebuildFreepools``(boolean val)`<br>Specifies whether or not the `BuildProcess` will rebuild the freepools on the AW\$ table.                                                                                                                              |
    | `void`             | `setRefreshAfterErrors``(boolean val)`<br>Specifies whether the build should stop immediately when it encounters an error or whether it should rollback the changes to the failed cube or dimension and attempt to continue with the other items in the build. |
    | `void`             | `setRefreshMethod``(java.lang.String method)`<br>Specifies the refresh methods for the materialized views that are associated with the cubes in the build.                                                                                                     |
    | `void`             | `setSchedulerJobName``(java.lang.String name)`<br>Specifies a text identifier for the build that the analytic workspace writes to the build log.                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BuildProperties

          public BuildProperties()

      Creates a new `BuildProperties` object.

  <!-- -->

  - ### Method Detail

    - #### getParallelism

          public int getParallelism()

      Get the number of parallel processes to allocate to the build process.
      Returns:
      An integer that indicates the number of parallel processes that the database instance allocates to the build process.

    <!-- -->

    - #### setParallelism

          public void setParallelism(int n)

      Specifies the number of parallel processes to allocate to the build process. Partitioned cubes can be loaded and aggregated in parallel processes. For example, a cube with five partitions can use up to five processes. Dimensions are always loaded serially.
      The number of parallel processes actually used by a build is controlled by the smallest of the following factors:

      - The number of cubes in the build and the number of partitions in each cube.
      - The value specified for parallelism, which you can set using this method.
      - The setting of the `JOB_QUEUE_PROCESSES` database initialization parameter.

      For example, if a cube has 12 partitions, the parallelism value is set to 10, and the `JOB_QUEUE_PROCESSES` database initialization parameter is set to 4, then for that cube the build uses four processes, which appear as slave processes in the build log.

      Parameters:
      `n` - An integer that specifies the number of parallel processes to allocate to the build process.

    <!-- -->

    - #### getRefreshAfterErrors

          public boolean getRefreshAfterErrors()

      Indicates whether the build should stop immediately when it encounters an error or whether it should rollback the changes to the failed cube or dimension and attempt to continue with the other items in the build.
      Returns:
      A `boolean` that if `true` indicates that the analytic workspace rolls back the build of the cube or the dimension that encountered the error but continues building other objects. A value of `false` indicates that the build fails immediately on encountering an error.

    <!-- -->

    - #### setRefreshAfterErrors

          public void setRefreshAfterErrors(boolean val)

      Specifies whether the build should stop immediately when it encounters an error or whether it should rollback the changes to the failed cube or dimension and attempt to continue with the other items in the build.
      Parameters:
      `val` - A `boolean` that is `true` to indicate that the analytic workspace should roll back the build of the cube or the dimension that encountered the error but should continues building other objects. A value of `false` indicates that if an error occurs during the build, then the build fails immediately.

    <!-- -->

    - #### getAtomicRefresh

          public boolean getAtomicRefresh()

      Indicates whether or not to prevent other users from having access to intermediate results during a build.
      Returns:
      A `boolean` that if `true` indicates that other users of the analytic workspace do not have access to intermediate results of the build. A value of `false` indicates that the users do have access to the intermediate results.

    <!-- -->

    - #### setAtomicRefresh

          public void setAtomicRefresh(boolean val)

      Specifies whether or not to prevent other users from having access to intermediate results during a build.
      Parameters:
      `val` - A `boolean` that if `true` specifies that other users of the analytic workspace do not have access to the intermediate results of the build. These other users see either the state of the analytic workspace before the build or, if the build succeeds, the state of the analytic workspace after the build. If an error occurs during the build, then the analytic workspace rolls back any changes.

      A value of `false` specifies that other users do have access to the intermediate results. If an error occurs during the build, then intermediate results may be available.

    <!-- -->

    - #### getAddDimensions

          public boolean getAddDimensions()

      Indicates whether or not the build process includes all of the dimensions of the cubes in the build or only the dimensions specified by the `BuildProcess`.
      Returns:
      A `boolean` that if `true` indicates that the build automatically includes all the dimensions of the cube. A value of `false` indicates that the build includes only the dimensions specified by the `BuildProcess`.

    <!-- -->

    - #### setAddDimensions

          public void setAddDimensions(boolean val)

      Specifies whether or not the build process includes all of the dimensions of the cubes in the build or only the dimensions specified by the `BuildProcess`. Specify `true` to include all of the dimensions of the cubes in the build, or `false` to include only the dimensions specified by the `BuildProcess`.
      Parameters:
      `val` - A `boolean` that if `true` specifies that that the build automatically includes all the dimensions of the cube. However, if a materialized view for a particular dimension is fresh, then the build does not include that dimension. A value of `false` specifies that the build includes only the dimensions specified by the `BuildProcess`.

    <!-- -->

    - #### getNestedRefresh

          public boolean getNestedRefresh()

      Indicates whether or not the build process includes all of the dependent cubes in the build or only the cubes specified by the `BuildProcess`.
      Returns:
      A `boolean` that if `true` indicates that the build automatically includes all the dependent cubes. A value of `false` indicates that the build includes only the cubes specified by the `BuildProcess`.

    <!-- -->

    - #### setNestedRefresh

          public void setNestedRefresh(boolean val)

      Specifies whether or not the build process includes all of the dependent cubes in the build or only the cubes specified by the `BuildProcess`. Specify `true` to include all of the dependent cubes in the build, or `false` to include only the cubes specified by the `BuildProcess`.
      Parameters:
      `val` - A `boolean` that if `true` specifies that that the build automatically includes all the dependent cube. A value of `false` specifies that the build includes only the cubes specified by the `BuildProcess`.

    <!-- -->

    - #### getRebuildFreepools

          public boolean getRebuildFreepools()

      Indicates whether or not the `BuildProcess` will rebuild the freepools on the AW\$ table.
      Returns:
      A `boolean` that if `true` indicates that the build automatically rebuilds the freepools on the AW\$ table. A value of `false` indicates otherwise.

    <!-- -->

    - #### setRebuildFreepools

          public void setRebuildFreepools(boolean val)

      Specifies whether or not the `BuildProcess` will rebuild the freepools on the AW\$ table. Specify `true` to rebuild the freepools on the AW\$ table or `false` to do otherwise.
      Parameters:
      `val` - A `boolean` that if `true` specifies that the build will automatically rebuild the freepools on the AW\$ table. A value of `false` specifies otherwise.

    <!-- -->

    - #### getAutomaticOrder

          public boolean getAutomaticOrder()

      Indicates whether the build process automatically reorders the cubes and dimensions in the build, or whether it builds the items in the exact order specified by the `BuildProcess`.
      Returns:
      A `boolean` that if `true` indicates that the analytic workspace reorders the build items. For example, it builds all of the dimensions before building the cubes. A value of `false` indicates that the analytic workspace builds the objects as they appear in the list of `BuildItem` objects in the `BuildProcess`.

    <!-- -->

    - #### setAutomaticOrder

          public void setAutomaticOrder(boolean val)

      Specifies whether the build process should automatically reorder the cubes and dimensions in the build, or whether it should build the items in the exact order specified by the `BuildProcess`.
      Parameters:
      `val` - A `boolean` that if `true` specifies that the analytic workspace should reorder the build items in the build process. For example, it builds all of the dimensions before building the cubes A value of `false` specifies that the analytic workspace builds the objects as they appear in the list of `BuildItem` objects in the `BuildProcess`.

    <!-- -->

    - #### getSchedulerJobName

          public java.lang.String getSchedulerJobName()

      Gets the text identifier for the build.
      Returns:
      A `String` that identifies the build.

    <!-- -->

    - #### setSchedulerJobName

          public void setSchedulerJobName(java.lang.String name)

      Specifies a text identifier for the build that the analytic workspace writes to the build log. You can use this method to assign a text identifier for the build, which can be useful for tracking the build process. For information on the build log, see the `BuildResult` class.
      Parameters:
      `name` - A `String` to identify the build.

      See Also:
      [`BuildResult`](BuildResult.md)

    <!-- -->

    - #### getRefreshMethod

          public java.lang.String getRefreshMethod()

      Gets the refresh method for the build.
      Returns:
      A `String` that identifies the refresh method of the build.

    <!-- -->

    - #### setRefreshMethod

          public void setRefreshMethod(java.lang.String method)

      Specifies the refresh methods for the materialized views that are associated with the cubes in the build. You can specify a single method to apply to all of the materialized views or you can specify a series of methods.
      If you specify a series, then each method applies to the corresponding cube in the list of `BuildItem` objects in the `BuildProcess`. If the list of `BuildItem` objects is longer than the series of methods, then the last method in the series applies to the corresponding cube and all remaining cubes in the list. For example, if the `BuildProcess` has three `BuildItem` objects that represent cubes, then the following example specifies a complete refresh for the first cube and a fast solve for the second and third cubes.

           buildProperties.setRefreshMethod("CS");

      The following table lists the valid values that you can specify with this method, and provides brief descriptions of the actions that the values indicate.

      | **Method** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                              |
      |:----------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |    `C`     | Perform a complete refresh, which refreshes of all of the data for the cube.                                                                                                                                                                                                                                                                                                                                                                 |
      |    `?`     | Perform a fast refresh if possible, otherwise perform a complete refresh.                                                                                                                                                                                                                                                                                                                                                                    |
      |    `F`     | Perform a fast refresh, which refreshes only the data that needs to change due to changes to the relational source master tables. This method works only if the cube has an associated materialized view that was created as a fast refresh or rewrite materialized view. Also, a fast refresh is possible only if the master tables support the operation. If the required conditions do not exist, the refresh operation does not succeed. |
      |    `P`     | Perform a refresh by recomputing the rows in the materialized view that are affected by changed partitions in the master tables. This method requires that the cube have an associated fast refresh or rewrite materialized view.                                                                                                                                                                                                            |
      |    `S`     | Perform a fast solve, which recomputes the aggregate data only if the detail level data has changed.                                                                                                                                                                                                                                                                                                                                         |

      The methods specified by `C`, `S`, and `?` work for any cube. The methods specified by `F` and `P` work only for a cube that has an associated fast refresh materialized view or a rewrite materialized view.

      Parameters:
      `method` - A `String` that specifies refresh methods for the materialized views of the cubes in the build.

    <!-- -->

    - #### getJobClass

          public java.lang.String getJobClass()

      Gets the job class for the build.
      Returns:
      A `String` that identifies the job class of the build.

    <!-- -->

    - #### setJobClass

          public void setJobClass(java.lang.String jobClass)

      Specifies the job class to be used by the scheduler when scheduling builds.
      Parameters:
      `jobClass` - A `String` identifying the job class of the build.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BooleanSource.md)
- [Next Class](BuildResult.md)

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
