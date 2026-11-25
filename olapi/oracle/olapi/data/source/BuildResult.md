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

- [Prev Class](BuildProperties.md)
- [Next Class](BuildWarningsException.md)

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

## Class BuildResult

- java.lang.Object

- - oracle.olapi.data.source.BuildResult

<!-- -->

-

  ------------------------------------------------------------------------



      public final class BuildResult
      extends java.lang.Object

  A container for an integer that identifies a build process in the `CUBE_BUILD_LOG` table. An analytic workspace stores a log of a build in the `CUBE_BUILD_LOG` table. It updates the table dynamically, so that you can monitor the progress of a build. Analytic Workspace Manager creates this log automatically. You can create the log file yourself by running the SQL script `$ORACLE_HOME/olap/admin/utlolaplog.sql`.
  You can create a new `BuildResult` and then pass the `BuildResult` to a `DataProvider.executeBuild` method. The analytic workspace generates the identification number for the build process and stores it in the `BuildResult`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                              |
    |----------------------------------------------------------|
    | `BuildResult``()`<br>Creates a new `BuildResult` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                             |
    |-------------------|----------------------------------------------------------------------------------------------------|
    | `int`             | `getBuildID``()`<br>Gets the number that identifies a build process in the `CUBE_BUILD_LOG` table. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BuildResult

          public BuildResult()

      Creates a new `BuildResult` object.

  <!-- -->

  - ### Method Detail

    - #### getBuildID

          public final int getBuildID()

      Gets the number that identifies a build process in the `CUBE_BUILD_LOG` table.
      Returns:
      An integer that identifies a build process in the `CUBE_BUILD_LOG` table.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildProperties.md)
- [Next Class](BuildWarningsException.md)

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
