Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Logger.md)
- [Next Class](Pc2Las.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.util

## Class Pc2Dem

- java.lang.Object

- - oracle.spatial.util.Pc2Dem

<!-- -->

-

  ------------------------------------------------------------------------



      public class Pc2Dem
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Pc2Dem``()`                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                                                                                           |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `createDemBlocks``(STRUCT pc, java.lang.String demBlockTable, java.lang.String pcDataTable, java.lang.String pcBlockingMethod, long demObjId, long demSrid, double pcQueryMbrMinX, double pcQueryMbrMinY, double pcQueryMbrMaxX, double pcQueryMbrMaxY, long demVertNumBlocks, long demHorizNumBlocks, double resolutionVert, double resolutionHoriz, int demBlockSizePixelsVert, int demBlockSizePixelsHoriz)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Pc2Dem

          public Pc2Dem()

  <!-- -->

  - ### Method Detail

    - #### createDemBlocks

          public static void createDemBlocks(STRUCT pc,
                                             java.lang.String demBlockTable,
                                             java.lang.String pcDataTable,
                                             java.lang.String pcBlockingMethod,
                                             long demObjId,
                                             long demSrid,
                                             double pcQueryMbrMinX,
                                             double pcQueryMbrMinY,
                                             double pcQueryMbrMaxX,
                                             double pcQueryMbrMaxY,
                                             long demVertNumBlocks,
                                             long demHorizNumBlocks,
                                             double resolutionVert,
                                             double resolutionHoriz,
                                             int demBlockSizePixelsVert,
                                             int demBlockSizePixelsHoriz)
                                      throws java.io.IOException,
                                             java.sql.SQLException

      Throws:
      `java.io.IOException`

      `java.sql.SQLException`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Logger.md)
- [Next Class](Pc2Las.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
