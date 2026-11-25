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

- [Prev Class](GML3g.md)
- [Next Class](Hilbert.md)

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

## Class GroupingLOD1Generalization

- java.lang.Object

- - oracle.spatial.util.GroupingLOD1Generalization

<!-- -->

-

  ------------------------------------------------------------------------



      public class GroupingLOD1Generalization
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                               |
    |-------------------------------------------------------------------------------------------|
    | `GroupingLOD1Generalization``()`<br>Java class that groups LOD1 geometries to generalize. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                               |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.ArrayList` | `typification``(java.lang.String tableName, java.lang.String columnName, java.sql.Connection conn, double tolerance)`<br>Groups the LOD1 geometries. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GroupingLOD1Generalization

          public GroupingLOD1Generalization()

      Java class that groups LOD1 geometries to generalize. The LOD levels are as follows: LOD 4 - Full texture - Given by Navteq LOD 3 - Same geometry, no texture LOD 2 - "SIMPLIFIED GEOMETRY" LOD 1 - Extrude geometry : Use footprint and average height LOD 0 - Group LOD 1 Geometry : How?- This class resolves this issue. Footprints on ground must be merged like hull operation then extrude This last operation is called typification. We assume during grouping that: - buildings' grounds are at z=0 plane and height is +ive.
      Since:
      JDBC Driver

  <!-- -->

  - ### Method Detail

    - #### typification

          public java.util.ArrayList typification(java.lang.String tableName,
                                                  java.lang.String columnName,
                                                  java.sql.Connection conn,
                                                  double tolerance)
                                           throws java.lang.Exception

      Groups the LOD1 geometries. The LOD levels are as follows: LOD 4 - Full texture - Given by Navteq LOD 3 - Same geometry, no texture LOD 2 - "SIMPLIFIED GEOMETRY" LOD 1 - Extrude geometry : Use footprint and average height LOD 0 - Group LOD 1 Geometry : How?- This class resolves this issue. Footprints on ground must be merged like hull operation then extrude This last operation is called typification. Execution plan: a) Ground plan computation using 3D MBR formation method in JGeometry class and then ignores the z-coordinates. Very cheap computation!i Dont use g3dconv since some geoms (buildings) may not touch the ground. b) Use sdo_sam.bin_layer function to get groups of buildings and then c) Use the convex_hull (concave hull later by Ying Hu) to combine a group into a single geometry. d) Use extrusion to get 3D geometries.
      Parameters:
      `tableName` - Table name where a bunch of groups of (3D Building) J3D_Geometry geometries to be generalized exist.

      `columnName` - Column name of the table name where the geometries to be generalizaed exist.

      `conn` - Database connection

      `tolerance` - Tolerance

      Returns:
      an ArrayList of JGeometry (3D) geometries

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      Oracle Database 11g Release 2 (11.2)

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

- [Prev Class](GML3g.md)
- [Next Class](Hilbert.md)

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
