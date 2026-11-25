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

- [Prev Class](BandReferenceInfo.md)
- [Next Class](GCPPoint.md)

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

oracle.spatial.georaster

## Class GCPGeoreference

- java.lang.Object

- - oracle.spatial.georaster.GCPGeoreference

<!-- -->

-

  ------------------------------------------------------------------------



      public class GCPGeoreference
      extends java.lang.Object

  GCPGeoreference represents the PL/SQL type MDSYS.SDO_GEOR_GEOREFERENCE It could be used to load Ground Control Points into a GeoRaster using sdo_geor.georeference. Example:
      GCPGeoreference gcpg = new GCPGeoreference("Affine");

      gcpg.addGCP("1", null, 25.625, 73.875, 237036.9375, 897987.1875);
      gcpg.addGCP("2", null, 100.625, 459.125, 237229.5625, 897949.6875);
      gcpg.addGCP("3", null, 362.375, 77.875, 237038.9375, 897818.8125);
      gcpg.addGCP("4", null, 478.875, 402.125, 237201.0625, 897760.5625);
      gcpg.addGCP("5", null, 167.47, 64.03, 237032.0153, 897916.2647);

      georPKG.georeference(geor, gcpg, false, 4326, 0, null);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                 |
    |-----------------------------------------------------------------------------|
    | `GCPGeoreference``(int method)`<br>GCPGeoreference constructor              |
    | `GCPGeoreference``(java.lang.String method)`<br>GCPGeoreference constructor |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                                              |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                    | `addCheckPoint``(java.lang.String id, java.lang.String description, java.lang.Double row, java.lang.Double column, java.lang.Double x, java.lang.Double y)`<br>Add a 2D Gound Check Point (not a Ground Control Point)                                              |
    | `void`                    | `addCheckPoint``(java.lang.String id, java.lang.String description, java.lang.Double row, java.lang.Double column, java.lang.Integer vertical, java.lang.Double x, java.lang.Double y, java.lang.Double z)`<br>Add a Gound Check Point (not a Ground Control Point) |
    | `void`                    | `addGCP``(`[`GCPPoint`](GCPPoint.md)` point)`<br>Add a Ground Control Point                                                                                                                                                                                         |
    | `void`                    | `addGCP``(int type, java.lang.String id, java.lang.String description, java.lang.Double row, java.lang.Double column, java.lang.Integer vertical, java.lang.Double x, java.lang.Double y, java.lang.Double z)`<br>Add a Gound Control Point                         |
    | `void`                    | `addGCP``(java.lang.String id, java.lang.String description, java.lang.Double row, java.lang.Double column, java.lang.Double x, java.lang.Double y)`<br>Add a 2D Gound Control Point (not a Ground Check Point)                                                     |
    | `void`                    | `addGCP``(java.lang.String id, java.lang.String description, java.lang.Double row, java.lang.Double column, java.lang.Integer vertical, java.lang.Double x, java.lang.Double y, java.lang.Double z)`<br>Add a Gound Control Point (not a Ground Check Point)        |
    | `void`                    | `addGCPs``(java.util.Vector points)`                                                                                                                                                                                                                                |
    | [`GCPPoint`](GCPPoint.md) | `getGCP``(int index)`<br>Get a Ground Control Point                                                                                                                                                                                                                 |
    | `STRUCT`                  | `toSTRUCT``(java.sql.Connection conn)`<br>Converts the GCPGeoreference into an Oracle JDBC Struct object.                                                                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GCPGeoreference

          public GCPGeoreference(int method)

      GCPGeoreference constructor
      Parameters:
      `method` - a valid Functional Fitting Method: SpatialReferenceInfo.GEOREFERENCE_TYPE_AFFINE SpatialReferenceInfo.GEOREFERENCE_TYPE_DLT SpatialReferenceInfo.GEOREFERENCE_TYPE_CUBICPOLYNOMIAL SpatialReferenceInfo.GEOREFERENCE_TYPE_QUADRATICPOLYNOMIAL SpatialReferenceInfo.GEOREFERENCE_TYPE_QUADRATICRATIONAL SpatialReferenceInfo.GEOREFERENCE_TYPE_RPC

    <!-- -->

    - #### GCPGeoreference

          public GCPGeoreference(java.lang.String method)

      GCPGeoreference constructor
      Parameters:
      `method` - a valid Functional Fitting Method "AFFINE" "DLT" "CUBICPOLYNOMIAL" "QUADRATICPOLYNOMIAL" "QUADRATICRATIONAL" "RPC"

  <!-- -->

  - ### Method Detail

    - #### addGCP

          public void addGCP(GCPPoint point)

      Add a Ground Control Point
      Parameters:
      `point` - a GCPPoint object

    <!-- -->

    - #### addGCPs

          public void addGCPs(java.util.Vector points)

    <!-- -->

    - #### getGCP

          public GCPPoint getGCP(int index)

      Get a Ground Control Point
      Parameters:
      `index` - a valid index starting from 0

      Returns:
      a GCPPoint object

    <!-- -->

    - #### addGCP

          public void addGCP(int type,
                             java.lang.String id,
                             java.lang.String description,
                             java.lang.Double row,
                             java.lang.Double column,
                             java.lang.Integer vertical,
                             java.lang.Double x,
                             java.lang.Double y,
                             java.lang.Double z)

      Add a Gound Control Point
      Parameters:
      `type` - the Ground Control Point type, 0 - Ground Control Point 1 - Ground Check Point

      `id` - Point id

      `description` - Point description

      `row` - Cell coordinate row

      `column` - Cell coordinate column

      `vertical` - Cell coordinate vertical

      `x` - Model coordinate X or longitude

      `y` - Model coordinate Y or latitude

      `z` - Model coordinate Z or hight

    <!-- -->

    - #### addGCP

          public void addGCP(java.lang.String id,
                             java.lang.String description,
                             java.lang.Double row,
                             java.lang.Double column,
                             java.lang.Integer vertical,
                             java.lang.Double x,
                             java.lang.Double y,
                             java.lang.Double z)

      Add a Gound Control Point (not a Ground Check Point)
      Parameters:
      `id` - Point id

      `description` - Point description

      `row` - Cell coordinate row

      `column` - Cell coordinate column

      `vertical` - Cell coordinate vertical

      `x` - Model coordinate X or longitude

      `y` - Model coordinate Y or latitude

      `z` - Model coordinate Z or hight

    <!-- -->

    - #### addGCP

          public void addGCP(java.lang.String id,
                             java.lang.String description,
                             java.lang.Double row,
                             java.lang.Double column,
                             java.lang.Double x,
                             java.lang.Double y)

      Add a 2D Gound Control Point (not a Ground Check Point)
      Parameters:
      `id` - Point id

      `description` - Point description

      `row` - Cell coordinate row

      `column` - Cell coordinate column

      `x` - Model coordinate X or longitude

      `y` - Model coordinate Y or latitude

    <!-- -->

    - #### addCheckPoint

          public void addCheckPoint(java.lang.String id,
                                    java.lang.String description,
                                    java.lang.Double row,
                                    java.lang.Double column,
                                    java.lang.Integer vertical,
                                    java.lang.Double x,
                                    java.lang.Double y,
                                    java.lang.Double z)

      Add a Gound Check Point (not a Ground Control Point)
      Parameters:
      `id` - Point id

      `description` - Point description

      `row` - Cell coordinate row

      `column` - Cell coordinate column

      `vertical` - Cell coordinate vertical

      `x` - Model coordinate X or longitude

      `y` - Model coordinate Y or latitude

      `z` - Model coordinate Z or hight

    <!-- -->

    - #### addCheckPoint

          public void addCheckPoint(java.lang.String id,
                                    java.lang.String description,
                                    java.lang.Double row,
                                    java.lang.Double column,
                                    java.lang.Double x,
                                    java.lang.Double y)

      Add a 2D Gound Check Point (not a Ground Control Point)
      Parameters:
      `id` - Point id

      `description` - Point description

      `row` - Cell coordinate row

      `column` - Cell coordinate column

      `x` - Model coordinate X or longitude

      `y` - Model coordinate Y or latitude

    <!-- -->

    - #### toSTRUCT

          public STRUCT toSTRUCT(java.sql.Connection conn)
                          throws java.sql.SQLException

      Converts the GCPGeoreference into an Oracle JDBC Struct object. You can then bind the Struct object to a SQL statment that inserts or updates the geometry in the database.
      Parameters:
      `conn` - the connection to use.

      Returns:
      a java.sql.Struct object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

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

- [Prev Class](BandReferenceInfo.md)
- [Next Class](GCPPoint.md)

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
