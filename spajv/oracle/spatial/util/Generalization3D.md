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

- [Prev Class](ExtendedKML2.md)
- [Next Class](GeoHash.md)

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

## Class Generalization3D

- java.lang.Object

- - oracle.spatial.util.Generalization3D

<!-- -->

-

  ------------------------------------------------------------------------



      public class Generalization3D
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                  |
    |----------------------------------------------------------------------------------------------|
    | `Generalization3D``()`<br>Java class that generalizes 3D buildings for different LOD levels. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                            |
    |-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`J3D_Geometry`](../geometry/J3D_Geometry.md) | `groundPlanSimplification``(`[`J3D_Geometry`](../geometry/J3D_Geometry.md)` A, java.sql.Connection conn, int choice, double tolerance)`<br>Simplifies input 3D building geometry. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Generalization3D

          public Generalization3D()

      Java class that generalizes 3D buildings for different LOD levels. The LOD levels are as follows: LOD 4 - Full texture - Given by Navteq LOD 3 - Same geometry, no texture LOD 2 - "SIMPLIFIED GEOMETRY": How?- This class resolves this issue. We either keep ground footprint kept unchanged (choice = 1) or, simplify footprint to reduce faces (choice = 0). Roofs are ignored. LOD 1 - Extrude geometry : Use footprint and average height LOD 0 - Group LOD 1 Geometry : Footprints on ground must be merged like hull operation then extrude This last operation is called typification. We assume during generalization for LOD2 that: - building's ground is at z=0 plane and height is +ive. - building has one store i.e., the ground is connected to roof polygons via single level of polygon. - building has ground polygon(s) defined implicitly : In other words, we deduce ground plan from side walls of the building. - If ground plan is explicitly defined (NOT supported), we need to deduce ground plan directly from polygon(s) having z-coordinates equal to zero within tolerance (epsilon). Then, use getGroundPlan_old function for this case.
      Since:
      JDBC Driver

  <!-- -->

  - ### Method Detail

    - #### groundPlanSimplification

          public J3D_Geometry groundPlanSimplification(J3D_Geometry A,
                                                       java.sql.Connection conn,
                                                       int choice,
                                                       double tolerance)
                                                throws java.lang.Exception

      Simplifies input 3D building geometry. LOD 4 - Full texture - Given by Navteq LOD 3 - Same geometry, no texture LOD 2 - "SIMPLIFIED GEOMETRY": How?- This function simplifies at this level. We either keep ground footprint kept unchanged (choice = 1) or, simplify footprint to reduce faces (choice = 0). Roofs are ignored. LOD 1 - Extrude geometry : Use footprint and average height LOD 0 - Group LOD 1 Geometry : Footprints on ground must be merged like hull operation -\> extrude This last operation is called typification. We assume during generalization for LOD2 that: - building's ground is at z=0 plane and height is +ive. - building has one store i.e., the ground is connected to roof polygons via single level of polygon. - building has ground polygon(s) defined implicitly : In other words, we deduce ground plan from side walls of the building. - If ground plan is explicitly defined (NOT supported), we need to deduce ground plan directly from polygon(s) having z-coordinates equal to zero within tolerance (epsilon). Then, use getGroundPlan_old function for this case.
      Parameters:
      `A` - J3D_Geometry geometry which is input (original) 3D building

      `conn` - Database connection

      `choice` - 1: Simplification using building ground plan, 0: Simplification using simplified building ground plan.

      `tolerance` - Tolerance

      Returns:
      a J3D_Geometry (3D) geometry,

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

- [Prev Class](ExtendedKML2.md)
- [Next Class](GeoHash.md)

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
