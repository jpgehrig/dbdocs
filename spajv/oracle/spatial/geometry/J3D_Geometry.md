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

- [Prev Class](FastJGeometry.PPStatus.md)
- [Next Class](JGeometry.md)

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

oracle.spatial.geometry

## Class J3D_Geometry

- java.lang.Object

- - [oracle.spatial.geometry.JGeometry](JGeometry.md)

  - - oracle.spatial.geometry.J3D_Geometry

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, [RNode](RNode.md)

  ------------------------------------------------------------------------



      public class J3D_Geometry
      extends JGeometry

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`JGeometry.GeomParser`](JGeometry.GeomParser.md)`, `[`JGeometry.Point`](JGeometry.Point.md)

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static int`      | `ETYPE_COMPOSITEPOLYGON`  |
    | `static int`      | `ETYPE_COMPOSITESOLID`    |
    | `static int`      | `ETYPE_COMPOSITESURFACE`  |
    | `static int`      | `ETYPE_POLYGON`           |
    | `static int`      | `ETYPE_SOLID`             |
    | `static int`      | `ETYPE_SURFACE`           |
    | `static int`      | `GTYPE_MULTISOLID`        |
    | `static int`      | `GTYPE_MULTISURFACE`      |
    | `static int`      | `GTYPE_SOLID`             |
    | `static int`      | `GTYPE_SURFACE`           |

    - ### Fields inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`GTYPE_COLLECTION`](JGeometry.md)`, `[`GTYPE_CURVE`](JGeometry.md)`, `[`GTYPE_MULTICURVE`](JGeometry.md)`, `[`GTYPE_MULTIPOINT`](JGeometry.md)`, `[`GTYPE_MULTIPOLYGON`](JGeometry.md)`, `[`GTYPE_POINT`](JGeometry.md)`, `[`GTYPE_POLYGON`](JGeometry.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                              |
    |----------------------------------------------------------------------------------------------------------|
    | `J3D_Geometry``(int gtype, int srid, double x, double y, double z)`                                      |
    | `J3D_Geometry``(int gtype, int srid, double x, double y, double z, int[] elemInfo, double[] ordinates)`  |
    | `J3D_Geometry``(int gtype, int srid, int[] elemInfo, double[] ordinates)`                                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                    | Method and Description                                                                                                                                                                                                                       |
    |--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                            | `anyInteract``(J3D_Geometry A, double tolerance)`<br>Returns whether two 3-D (Cartesian) geometries anyInteract or not.                                                                                                                      |
    | `boolean`                            | `anyInteract``(J3D_Geometry A, double tolerance, java.lang.String is_g3d)`<br>Returns whether two 3-D geometries anyInteract or not.                                                                                                         |
    | `boolean`                            | `anyInteract2``(J3D_Geometry A, boolean[] is_solid, boolean[] polygons, boolean[] holes, double tolerance)`                                                                                                                                  |
    | `static `[`JGeometry`](JGeometry.md) | `appendToCollection``(`[`JGeometry`](JGeometry.md)` collGeom, `[`JGeometry`](JGeometry.md)` scGeom)`<br>Returns a collection or multi-x geometry by appending simple (x) geometries in 3-D.                                                  |
    | `double`                             | `area``(double tolerance)`<br>Returns the total planar surface area of a 3-D geometry.                                                                                                                                                       |
    | `double`                             | `area``(double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the total planar surface area of a 3-D geometry.                                                                        |
    | `J3D_Geometry`                       | `centroid3d``(double tolerance)`<br>Returns the centroid aka center of mass, center of gravity of solid 3-D geometry of uniform material density.                                                                                            |
    | `void`                               | `clearBelongingGeometry``()`                                                                                                                                                                                                                 |
    | `java.util.ArrayList`                | `closestPoints``(J3D_Geometry A, double tolerance)`<br>Returns the closest points of approach between two 3-D (Cartesian) geometries.                                                                                                        |
    | `java.util.ArrayList`                | `closestPoints``(J3D_Geometry A, double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the closest points of approach between two 3-D geometries.                                     |
    | `double`                             | `distance``(J3D_Geometry A, double tolerance)`<br>Returns the minimum distance between two 3-D (Cartesian) geometries.                                                                                                                       |
    | `double`                             | `distance``(J3D_Geometry A, double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the minimum distance between two 3-D geometries.                                                    |
    | `double[]`                           | `distCpa``(J3D_Geometry A, double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the closest points of approach (and hence the minimum distance) between two J3D_Geometry geometries. |
    | `double[]`                           | `distCpa2``(J3D_Geometry A, boolean[] is_solid, boolean[] polygons, boolean[] holes, double tolerance, java.lang.String is_g3d)`                                                                                                             |
    | `static J3D_Geometry`                | `expandGeom``(J3D_Geometry geometry)`<br>Returns the expanded geometry.                                                                                                                                                                      |
    | `static `[`JGeometry`](JGeometry.md) | `extrusion``(`[`JGeometry`](JGeometry.md)` polygon, double[] grdHeight, double[] height, java.sql.Connection conn, double tolerance)`<br>Returns the extruded 3-D geometry from a 2-D polygon.                                               |
    | `static `[`JGeometry`](JGeometry.md) | `extrusion``(`[`JGeometry`](JGeometry.md)` polygon, double[] grdHeight, double[] height, java.sql.Connection conn, double tolerance, int optional3dSrid)`<br>Returns the extruded 3-D geometry from a 2-D polygon.                           |
    | `static `[`JGeometry`](JGeometry.md) | `extrusion``(`[`JGeometry`](JGeometry.md)` polygon, double grdHeight, double height, java.sql.Connection conn, double tolerance)`<br>Returns the extruded 3-D geometry from a 2-D polygon.                                                   |
    | `static `[`JGeometry`](JGeometry.md) | `extrusion``(`[`JGeometry`](JGeometry.md)` polygon, double grdHeight, double height, java.sql.Connection conn, double tolerance, int optional3dSrid)`<br>Returns the extruded 3-D geometry from a 2-D polygon.                               |
    | `J3D_Geometry`                       | `getBelongingGeometry``()`                                                                                                                                                                                                                   |
    | `J3D_Geometry`                       | `getElementByLabel``(java.lang.String label)`<br>Returns the sub-geometry indicated by the label string.                                                                                                                                     |
    | `void`                               | `getFlags``(J3D_Geometry simplegeom, boolean[] is_solid, boolean[] polygons, boolean[] holes)`                                                                                                                                               |
    | `java.lang.String`                   | `getLabelByElement``(J3D_Geometry qryElement, double tolerance)`<br>Computes the corresponding sub-geometry's label within the geometry.                                                                                                     |
    | `boolean`                            | `inside3d``(J3D_Geometry solid2, double tolerance)`<br>Returns whether the first Cartesian geometry is inside the solid (second Cartesian geometry) or not.                                                                                  |
    | `boolean`                            | `inside3d``(J3D_Geometry solid2, double tolerance, java.lang.String is_g3d)`<br>Returns whether the first geometry is inside the solid (second geometry) or not.                                                                             |
    | `double`                             | `length``(double tolerance)`<br>Returns the perimeter of a 3-D geometry.                                                                                                                                                                     |
    | `double`                             | `length``(double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the perimeter of a 3-D geometry.                                                                                      |
    | `double`                             | `length``(int count_shared_edges, double tolerance)`<br>Returns the perimeter of a 3-D geometry.                                                                                                                                             |
    | `double`                             | `length``(int count_shared_edges, double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the perimeter of a 3-D geometry.                                                              |
    | `boolean`                            | `pointInPolygon``(J3D_Geometry geom, double tolerance)`                                                                                                                                                                                      |
    | `static J3D_Geometry`                | `projectToGnomonicFromLongLat``(J3D_Geometry P, double central_longitude, double central_latitude)`                                                                                                                                          |
    | `void`                               | `setBelongingGeometry``(J3D_Geometry geom)`                                                                                                                                                                                                  |
    | `java.lang.String`                   | `validate``(boolean CONDITIONAL, double tolerance)`<br>Returns whether a 3-D (Cartesian) geometry is valid or not.                                                                                                                           |
    | `java.lang.String`                   | `validate``(boolean CONDITIONAL, double tolerance, java.lang.String is_g3d)`<br>Returns whether a 3-D geometry is valid or not.                                                                                                              |
    | `double`                             | `volume``(double tolerance)`<br>Returns the volume of a 3-D (Cartesian) geometry.                                                                                                                                                            |
    | `double`                             | `volume``(double tolerance, java.lang.String is_g3d, double smax, double flat, double geog_crs_uom_factor)`<br>Returns the volume of a 3-D geometry.                                                                                         |

    - ### Methods inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`affineTransforms`](JGeometry.md)`, `[`anyInteract`](JGeometry.md)`, `[`anyInteract`](JGeometry.md)`, `[`anyInteract`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`byteArrayToHexString`](JGeometry.md)`, `[`centralLongLatforGNMProjection`](JGeometry.md)`, `[`circle_polygon`](JGeometry.md)`, `[`circle_polygon`](JGeometry.md)`, `[`clone`](JGeometry.md)`, `[`computeArc`](JGeometry.md)`, `[`concaveHullDig`](JGeometry.md)`, `[`convexHull`](JGeometry.md)`, `[`coord`](JGeometry.md)`, `[`createArc2d`](JGeometry.md)`, `[`createCircle`](JGeometry.md)`, `[`createCircle`](JGeometry.md)`, `[`createDoubleShape`](JGeometry.md)`, `[`createDoubleShape`](JGeometry.md)`, `[`createLinearLineString`](JGeometry.md)`, `[`createLinearMultiLineString`](JGeometry.md)`, `[`createLinearPolygon`](JGeometry.md)`, `[`createLinearPolygon`](JGeometry.md)`, `[`createLRSLinearLineString`](JGeometry.md)`, `[`createLRSLinearMultiLineString`](JGeometry.md)`, `[`createLRSLinearPolygon`](JGeometry.md)`, `[`createLRSLinearPolygon`](JGeometry.md)`, `[`createLRSPoint`](JGeometry.md)`, `[`createMultiPoint`](JGeometry.md)`, `[`createNURBScurve`](JGeometry.md)`, `[`createPoint`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`crossesMeridian`](JGeometry.md)`, `[`decodePolyline`](JGeometry.md)`, `[`defaultTolerance`](JGeometry.md)`, `[`densifyArcs`](JGeometry.md)`, `[`densifyArcs`](JGeometry.md)`, `[`densifyGeodesic`](JGeometry.md)`, `[`densifyGeodesic`](JGeometry.md)`, `[`distance`](JGeometry.md)`, `[`distance`](JGeometry.md)`, `[`encodePolyline`](JGeometry.md)`, `[`equals`](JGeometry.md)`, `[`expandCircle`](JGeometry.md)`, `[`fitArc`](JGeometry.md)`, `[`fitsInHemisphere`](JGeometry.md)`, `[`geodetic3DLength`](JGeometry.md)`, `[`geodetic3DLength`](JGeometry.md)`, `[`getCoordSysInfo`](JGeometry.md)`, `[`getDimensions`](JGeometry.md)`, `[`getElementAt`](JGeometry.md)`, `[`getElements`](JGeometry.md)`, `[`getElemInfo`](JGeometry.md)`, `[`getExtendedMBR`](JGeometry.md)`, `[`getFirstPoint`](JGeometry.md)`, `[`getGeomDescriptor`](JGeometry.md)`, `[`getJavaPoint`](JGeometry.md)`, `[`getJavaPoints`](JGeometry.md)`, `[`getLabelPoint`](JGeometry.md)`, `[`getLabelPointXYZ`](JGeometry.md)`, `[`getLastPoint`](JGeometry.md)`, `[`getLRMDimension`](JGeometry.md)`, `[`getMBR`](JGeometry.md)`, `[`getMer`](JGeometry.md)`, `[`getNumPoints`](JGeometry.md)`, `[`getNurbsApprox`](JGeometry.md)`, `[`getOracleDescriptors`](JGeometry.md)`, `[`getOracleDescriptorsStr`](JGeometry.md)`, `[`getOrdinatesArray`](JGeometry.md)`, `[`getOrdinatesOfElements`](JGeometry.md)`, `[`getOrientMultiPointOffset`](JGeometry.md)`, `[`getPoint`](JGeometry.md)`, `[`getSize`](JGeometry.md)`, `[`getSRID`](JGeometry.md)`, `[`getType`](JGeometry.md)`, `[`hasCircularArcs`](JGeometry.md)`, `[`isCircle`](JGeometry.md)`, `[`isGeodetic`](JGeometry.md)`, `[`isGeodeticMBR`](JGeometry.md)`, `[`isInside`](JGeometry.md)`, `[`isInside`](JGeometry.md)`, `[`isLRSGeometry`](JGeometry.md)`, `[`isMultiPoint`](JGeometry.md)`, `[`isOrientedMultiPoint`](JGeometry.md)`, `[`isOrientedPoint`](JGeometry.md)`, `[`isPoint`](JGeometry.md)`, `[`isRectangle`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`load`](JGeometry.md)`, `[`loadJS`](JGeometry.md)`, `[`loadJS`](JGeometry.md)`, `[`make_2d`](JGeometry.md)`, `[`make_3d`](JGeometry.md)`, `[`make_3dgeom`](JGeometry.md)`, `[`make_3dgeom`](JGeometry.md)`, `[`monoMeasure`](JGeometry.md)`, `[`parseGeometry`](JGeometry.md)`, `[`projectArrayToGNM`](JGeometry.md)`, `[`projectFromGNM_longLat`](JGeometry.md)`, `[`projectFromLTP`](JGeometry.md)`, `[`projectToGNM_longLat`](JGeometry.md)`, `[`projectToGNM_longLat`](JGeometry.md)`, `[`projectToLTP`](JGeometry.md)`, `[`projectToLTP`](JGeometry.md)`, `[`reFormulateArc`](JGeometry.md)`, `[`setLRMDimension`](JGeometry.md)`, `[`setSRID`](JGeometry.md)`, `[`setType`](JGeometry.md)`, `[`simplify`](JGeometry.md)`, `[`simplify`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`tfm_8307_to_PopularMercator`](JGeometry.md)`, `[`tfm_8307_to_PopularMercator`](JGeometry.md)`, `[`tfm_PopularMercator_to_8307`](JGeometry.md)`, `[`tfm_PopularMercator_to_8307`](JGeometry.md)`, `[`toGeoJson`](JGeometry.md)`, `[`toGeoJsonCollection`](JGeometry.md)`, `[`toString`](JGeometry.md)`, `[`toStringFull`](JGeometry.md)`, `[`toStringFull`](JGeometry.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### GTYPE_SURFACE

          public static final int GTYPE_SURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_SOLID

          public static final int GTYPE_SOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTISOLID

          public static final int GTYPE_MULTISOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTISURFACE

          public static final int GTYPE_MULTISURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_POLYGON

          public static final int ETYPE_POLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_SURFACE

          public static final int ETYPE_SURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITEPOLYGON

          public static final int ETYPE_COMPOSITEPOLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITESURFACE

          public static final int ETYPE_COMPOSITESURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_SOLID

          public static final int ETYPE_SOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITESOLID

          public static final int ETYPE_COMPOSITESOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### J3D_Geometry

          public J3D_Geometry(int gtype,
                              int srid,
                              int[] elemInfo,
                              double[] ordinates)

    <!-- -->

    - #### J3D_Geometry

          public J3D_Geometry(int gtype,
                              int srid,
                              double x,
                              double y,
                              double z)

    <!-- -->

    - #### J3D_Geometry

          public J3D_Geometry(int gtype,
                              int srid,
                              double x,
                              double y,
                              double z,
                              int[] elemInfo,
                              double[] ordinates)

  <!-- -->

  - ### Method Detail

    - #### setBelongingGeometry

          public void setBelongingGeometry(J3D_Geometry geom)

    <!-- -->

    - #### getBelongingGeometry

          public J3D_Geometry getBelongingGeometry()

    <!-- -->

    - #### clearBelongingGeometry

          public void clearBelongingGeometry()

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(J3D_Geometry A,
                                     double tolerance)
                              throws java.lang.Exception

      Returns whether two 3-D (Cartesian) geometries anyInteract or not.
      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE. This signature assumes data are not in Geographic3D space.

      Parameters:
      `A` - Another J3D_Geometry geometry

      `tolerance` -

      Returns:
      TRUE or FALSE

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(J3D_Geometry A,
                                     double tolerance,
                                     java.lang.String is_g3d)
                              throws java.lang.Exception

      Returns whether two 3-D geometries anyInteract or not.
      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      If data are Geographic3D (by setting is_g3d as TRUE), then Gnomonic transformation (projection) is carried out here. The tolerance value is set to 0.05 in Gnomonic transformation no matter what the user input tolerance is.

      Geodetic/Geographic 3D geometries should not span long distances.

      Parameters:
      `A` - Another J3D_Geometry geometry

      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      Returns:
      TRUE or FALSE

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getFlags

          public void getFlags(J3D_Geometry simplegeom,
                               boolean[] is_solid,
                               boolean[] polygons,
                               boolean[] holes)
                        throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### pointInPolygon

          public boolean pointInPolygon(J3D_Geometry geom,
                                        double tolerance)

    <!-- -->

    - #### anyInteract2

          public boolean anyInteract2(J3D_Geometry A,
                                      boolean[] is_solid,
                                      boolean[] polygons,
                                      boolean[] holes,
                                      double tolerance)
                               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distance

          public double distance(J3D_Geometry A,
                                 double tolerance)
                          throws java.lang.Exception

      Returns the minimum distance between two 3-D (Cartesian) geometries.
      Calls distCpa to compute the closest points of approach and then minimum distance. The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Parameters:
      `A` - Another 3-D geometry

      `tolerance` -

      Returns:
      the minimum distance between two 3-D geometries

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distance

          public double distance(J3D_Geometry A,
                                 double tolerance,
                                 java.lang.String is_g3d,
                                 double smax,
                                 double flat,
                                 double geog_crs_uom_factor)
                          throws java.lang.Exception

      Returns the minimum distance between two 3-D geometries.
      Calls distCpa to compute the closest points of approach and then minimum distance. The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Parameters:
      `A` - Another 3-D geometry

      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      the minimum distance between two 3-D geometries

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distCpa

          public double[] distCpa(J3D_Geometry A,
                                  double tolerance,
                                  java.lang.String is_g3d,
                                  double smax,
                                  double flat,
                                  double geog_crs_uom_factor)
                           throws java.lang.Exception

      Returns the closest points of approach (and hence the minimum distance) between two J3D_Geometry geometries.
      Algorithm: Input: geom1 and geom2 If geometries anyInteract, then: Return cpa = null; Else: Compute the closest points of approach P1 and P2 between the two geometries geom1 and geom2 WITH considering polygon holes in polygons and solid holes in solids. The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Parameters:
      `A` - Another 3-D geometry

      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      the closest points of approach between two 3-D geometries

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distCpa2

          public double[] distCpa2(J3D_Geometry A,
                                   boolean[] is_solid,
                                   boolean[] polygons,
                                   boolean[] holes,
                                   double tolerance,
                                   java.lang.String is_g3d)
                            throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### projectToGnomonicFromLongLat

          public static J3D_Geometry projectToGnomonicFromLongLat(J3D_Geometry P,
                                                                  double central_longitude,
                                                                  double central_latitude)
                                                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validate

          public java.lang.String validate(boolean CONDITIONAL,
                                           double tolerance)
                                    throws java.lang.Exception

      Returns whether a 3-D (Cartesian) geometry is valid or not. If not valid, returns the error message with the erronous part of the geometry.
      The children of a geometry are done first here (aka self-validation). Then, the cross-validation is done. The label is stored backwards such that arrayList has pointID, edgeID, ringID, polygonID, csurfID, solidID, multiID. The elementExtractor's used here operate with allow_comp_sub_elements set to TRUE (default) because we would like to return comp-x in multi-x. ElementExtractor errors are caught ONLY here but not in crossElementValidation because each geometry has to go through elementExtractor before calling crossElementValidation function.

      Composite surface is expected to be: \>li\< \> , 1006, N\< \>/li\< \>li\< N tuples of the form \>/li\< \>li\< \>, 1003, x\< \>, 2003, x\<\* \>/li\<

      Composite solid should be of the form: \>li\< \> , 1008, N\< \>/li\< \>li\< N solids each of the form \>/li\< \>li\< \>, 1007, \< specified using 1 outer surface and N inner surfaces \>/li\< \>li\< \>, 1006, M\< and M tuples of the form \>,1003, \< m times \>/li\< followed by 0 or more inner solids specified as surfaces as: \>/li\< \>li\< \>, 2006, p\< and p tuples of the form \>,2003, \< \>/li\<

      The input parameter CONDITIONAL refers to rule for composite surface such that if two outerrings are on the same plane and share an edge, we return error if CONDITIONAL is set to TRUE. Note that the PL/SQL interface of validate function i.e., validate_geometry_with_context and validate_layer_with_context set this conditional input to TRUE by default. The elementExtractor's used here operate with allow_comp_sub_elements set to TRUE (default).

      When modeling a simple solid, each face of the solid must have full-edge intersection with its neighbor faces. Othwerwise, reachability test will catch this situation and report it as an error.

      This signature assumes data are not in Geographic3D space.

      Parameters:
      `CONDITIONAL` - (explained above)

      `tolerance` -

      Returns:
      validation string (TRUE if valid or the error number w/ label if invalid)

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validate

          public java.lang.String validate(boolean CONDITIONAL,
                                           double tolerance,
                                           java.lang.String is_g3d)
                                    throws java.lang.Exception

      Returns whether a 3-D geometry is valid or not. If not valid, returns the error message with the erronous part of the geometry.
      The children of a geometry are done first here (aka self-validation). Then, the cross-validation is done. The label is stored backwards such that arrayList has pointID, edgeID, ringID, polygonID, csurfID, solidID, multiID. The elementExtractor's used here operate with allow_comp_sub_elements set to TRUE (default) because we would like to return comp-x in multi-x. ElementExtractor errors are caught ONLY here but not in crossElementValidation because each geometry has to go through elementExtractor before calling crossElementValidation function.

      Composite surface is expected to be: \>li\< \> , 1006, N\< \>/li\< \>li\< N tuples of the form \>/li\< \>li\< \>, 1003, x\< \>, 2003, x\<\* \>/li\<

      Composite solid should be of the form: \>li\< \> , 1008, N\< \>/li\< \>li\< N solids each of the form \>/li\< \>li\< \>, 1007, \< specified using 1 outer surface and N inner surfaces \>/li\< \>li\< \>, 1006, M\< and M tuples of the form \>,1003, \< m times \>/li\< followed by 0 or more inner solids specified as surfaces as: \>/li\< \>li\< \>, 2006, p\< and p tuples of the form \>,2003, \< \>/li\<

      The input parameter CONDITIONAL refers to rule for composite surface such that if two outerrings are on the same plane and share an edge, we return error if CONDITIONAL is set to TRUE. Note that the PL/SQL interface of validate function i.e., validate_geometry_with_context and validate_layer_with_context set this conditional input to TRUE by default. The elementExtractor's used here operate with allow_comp_sub_elements set to TRUE (default).

      When modeling a simple solid, each face of the solid must have full-edge intersection with its neighbor faces. Othwerwise, reachability test will catch this situation and report it as an error.

      If data are Geographic3D (by setting is_g3d as TRUE), then Gnomonic transformation (projection) is carried out here. The tolerance value is set to 0.05 in Gnomonic transformation no matter what the user input tolerance is.

      Geodetic/Geographic 3D geometries should not span long distances.

      Parameters:
      `CONDITIONAL` - (explained above)

      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      Returns:
      validation string (TRUE if valid or the error number w/ label if invalid)

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### volume

          public double volume(double tolerance)
                        throws java.lang.Exception

      Returns the volume of a 3-D (Cartesian) geometry. The geometry could be simple, composite or multi solid geometry.
      First outer solid volume is computed, and then the inner solid volumes are subtracted from the outer solid volume. If there are no solids in the geometry, then it returns 0.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Overrides:
      [`volume`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `tolerance` -

      Returns:
      volume of the solid geometry in coordinate system units (cubed) or m^3 if geodetic

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### volume

          public double volume(double tolerance,
                               java.lang.String is_g3d,
                               double smax,
                               double flat,
                               double geog_crs_uom_factor)
                        throws java.lang.Exception

      Returns the volume of a 3-D geometry. The geometry could be simple, composite or multi solid geometry.
      First outer solid volume is computed, and then the inner solid volumes are subtracted from the outer solid volume. If there are no solids in the geometry, then it returns 0.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      If data is Geographic 3D, we only convert it to Cartesian coordinates and return the volume in the Cartesian space. If the geometry is larger than US street block size, there could be inaccuracies.

      Parameters:
      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      volume of the solid geometry in coordinate system units (m^3 if geodetic)

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### closestPoints

          public java.util.ArrayList closestPoints(J3D_Geometry A,
                                                   double tolerance)
                                            throws java.lang.Exception

      Returns the closest points of approach between two 3-D (Cartesian) geometries. The first one of the closest points belonging to the first geometry (this), and the second one belonging to the second geometry (A) are returned in a J3D_Geometry ArrayList of length 2. If the geometries interact, then null is returned.
      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Parameters:
      `A` - Another 3-D geometry

      `tolerance` -

      Returns:
      An ArrayList having two J3D_Geometry points which are the closest points of approach

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### closestPoints

          public java.util.ArrayList closestPoints(J3D_Geometry A,
                                                   double tolerance,
                                                   java.lang.String is_g3d,
                                                   double smax,
                                                   double flat,
                                                   double geog_crs_uom_factor)
                                            throws java.lang.Exception

      Returns the closest points of approach between two 3-D geometries. The first one of the closest points belonging to the first geometry (this), and the second one belonging to the second geometry (A) are returned in a J3D_Geometry ArrayList of length 2. If the geometries interact, then null is returned.
      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE.

      Parameters:
      `A` - Another 3-D geometry

      `tolerance` -

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      An ArrayList having two J3D_Geometry points which are the closest points of approach

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### area

          public double area(double tolerance)
                      throws java.lang.Exception

      Returns the total planar surface area of a 3-D geometry. Computed area includes inner solid areas and shared areas of contact. If there are no polygon or solid geometries, this function returns zero.
      Please note that the area of shared surfaces in composite solids will be double-counted.

      If data is Geographic 3D, the computation is currently done on a linear tangent plane, which introduces inaccuracies on objects of city size or larger. This may change in later releases.

      Overrides:
      [`area`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `tolerance` - tolerance value

      Returns:
      area in coordinate system units (squared) for projected coordinate systems and m^2 for geodetic.

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### area

          public double area(double tolerance,
                             java.lang.String is_g3d,
                             double smax,
                             double flat,
                             double geog_crs_uom_factor)
                      throws java.lang.Exception

      Returns the total planar surface area of a 3-D geometry. Computed area includes inner solid areas and shared areas of contact. If there are no polygon or solid geometries, this function returns zero.
      Please note that the area of shared surfaces in composite solids will be double-counted.

      If data is Geographic 3D, the computation is currently done on a linear tangent plane, which introduces inaccuracies on objects of city size or larger. This may change in later releases.

      Parameters:
      `tolerance` - tolerance value

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      area in coordinate system units (squared) for projected coordinate systems and m^2 for geodetic.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### length

          public double length(double tolerance)
                        throws java.lang.Exception

      Returns the perimeter of a 3-D geometry. All edge lengths are added. The parameter count_shared_edges is by default 1. If different value like 2 is needed, then the other interface accepting count_shared_edges must be used.
      Similar approach in validate for getting all surfaces. Returns 0 if there are only points in the geometry.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE in case of non-collection geometry and set to TRUE in case of collection geometry.

      If collection has line segment geometry(s) which are also shared by solid geometry(s), then the length of the line segment geometry(s) are not subtracted when count_shared_edges parameter is 1.

      Overrides:
      [`length`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `tolerance` - Tolerance value.

      Returns:
      length of 3-D geometry in coordinate system units (meters if geodetic)

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### length

          public double length(double tolerance,
                               java.lang.String is_g3d,
                               double smax,
                               double flat,
                               double geog_crs_uom_factor)
                        throws java.lang.Exception

      Returns the perimeter of a 3-D geometry. All edge lengths are added. The parameter count_shared_edges is by default 1. If different value like 2 is needed, then the other interface accepting count_shared_edges must be used.
      Similar approach in validate for getting all surfaces. Returns 0 if there are only points in the geometry.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE in case of non-collection geometry and set to TRUE in case of collection geometry.

      If collection has line segment geometry(s) which are also shared by solid geometry(s), then the length of the line segment geometry(s) are not subtracted when count_shared_edges parameter is 1.

      Parameters:
      `tolerance` - Tolerance value.

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      length of 3-D geometry

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### length

          public double length(int count_shared_edges,
                               double tolerance)
                        throws java.lang.Exception

      Returns the perimeter of a 3-D geometry. All edge lengths are added.
      Returns 0 if there are only points in the geometry. Then, find the coinciding (shared) edges. If there are such (partially or fully) shared edges, depending on the value of input parameter count_shared_edges, count these shared edges either: twice, which means you dont need to update length value baceuse we already counted them 2ice, or once, which means you need to subtract the shared length from the length value, or (LATER) zero times, which means you need to subtract twice the shared length from the length value.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE in case of non-collection geometry and set to TRUE in case of collection geometry.

      If collection has line segment geometry(s) which are also shared by solid geometry(s), then the length of the line segment geometry(s) are not subtracted when count_shared_edges parameter is 1.

      Parameters:
      `count_shared_edges` - (explained above)

      `tolerance` - Tolerance value.

      Returns:
      length of 3-D geometry in coordinate system units (meters if geodetic)

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### length

          public double length(int count_shared_edges,
                               double tolerance,
                               java.lang.String is_g3d,
                               double smax,
                               double flat,
                               double geog_crs_uom_factor)
                        throws java.lang.Exception

      Returns the perimeter of a 3-D geometry. All edge lengths are added.
      Returns 0 if there are only points in the geometry. Then, find the coinciding (shared) edges. If there are such (partially or fully) shared edges, depending on the value of input parameter count_shared_edges, count these shared edges either: twice, which means you dont need to update length value baceuse we already counted them 2ice, or once, which means you need to subtract the shared length from the length value, or (LATER) zero times, which means you need to subtract twice the shared length from the length value.

      The elementExtractor's used here operate with allow_comp_sub_elements set to FALSE in case of non-collection geometry and set to TRUE in case of collection geometry.

      If collection has line segment geometry(s) which are also shared by solid geometry(s), then the length of the line segment geometry(s) are not subtracted when count_shared_edges parameter is 1.

      Parameters:
      `count_shared_edges` - (explained above)

      `tolerance` - Tolerance value.

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      `smax` - Semi Major Axis constant (Used when is_g3d is TRUE)

      `flat` - Flattenning constant (Used when is_g3d is TRUE)

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      length of 3-D geometry

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### extrusion

          public static JGeometry extrusion(JGeometry polygon,
                                            double grdHeight,
                                            double height,
                                            java.sql.Connection conn,
                                            double tolerance)
                                     throws java.lang.Exception,
                                            java.sql.SQLException

      Returns the extruded 3-D geometry from a 2-D polygon.
      We expect: \>li\< A 2-D polygon w/ hole(s) or (outer) ring geometry in JGeometry (which will be the base of the solid that we will output): --\< In case of ring: This 2-D polygon (ring) input must be oriented in CCW (on x-y plane) and could be optimized rectangle. When we convert this 2-D polygon (ring) input to the 3-D polygon by adding z=0 coordinates to each vertex, we also check/validate that the orientation of the input polygon (ring) must be CCW on x-y plane and thus it must result +ive value from the dot-product of the normal of this polygon with the unit vector in the direction of +z axis; --\< In case of polygon w/ hole(s): The outer ring must be CCW oriented and inner rings must be CW oriented. We partition this polygon w/ hole(s) into outer rings such that it becomes composite surface without hole(s). In other words, we get rid of hole(s) in the input polygon w/ hole(s). Then, we apply extrusion for (an outer) ring procedure for each ring in this composite surface (comes as collection) and then output the resulting solid as composite solid. It must be noted that in this case user can either input a single grdHeight value and a single height value or grdHeight values and height values ONLY for the outer ring (we interpret those for inner ring(s)) since from satellite images if there are hole(s) in the image, the hole goes \*all\* the way down and since we donot allow patches on solids, we do the conversion from polygon w/ hole(s) to composite surface; and \>/li\< \>li\< A two double numbers of z-values where the first number is for ground height (i.e., the z-value for a vertex of the bottom face of the solid that we will output) and the second number is for height (i.e., the z-value for a vertex of the top face of the same solid that we will output). The height entry for a vertex is always greater or equal to the ground height entry for a vertex. If this is not so, we will issue an error. The extrusion is always either along +z or -z axis. First the newly extruded output solid's bottom face coordinate array, then top face coordinate array, and then side faces' coordinate are formed. \>/li\< \>li\< The parameter tolerance is for validating the input 2D polygon. The parameter cond is deprecated, always use "FALSE" value for cond parameter. \>/li\< \>li\< The connection parameter conn is to run the PL/SQL functions such as convert_2D_srid_to_3D to get the 3-D srid of output geometry wrt 2-D srid of input polygon. For Geodetic, we assume the unit is meter for z values and for projected we assume that it is the same unit as the projected SRID unit. \>/li\< Please note that if there is a single grdHeight value and a single height value for all of the polygon vertices, we replicate grdHeight and height values for each polygon vertex and call original extrusion method.

      For optimized rectangle 2-D polygon (ring) input: the user should give either one height value and one ground height value or 5 element double array for height and 5 element double array for ground height. Otherwise, an error will received. We expand optimized rectangle in CCW orientation. The 5 element arrays must be given in corresponding order with expanded polygon.

      Parameters:
      `polygon` - The polygon w/ hole(s) or outer ring of a 2-D polygon.

      `grdHeight` - A single value or an array of ground height values

      `height` - A single value or an array of ground height values

      `conn` - The database connection for calling pl/sql function mdsys.sdo_cs.convert_2d_srid_to_3d to determine the 3-D srid of the new extruded solid //@param cond Deprecated, always use "FALSE" value.

      `tolerance` -

      Returns:
      The extruded new solid geometry (as simple or composite solid depending on what the input 2-D polygon is).

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### extrusion

          public static JGeometry extrusion(JGeometry polygon,
                                            double grdHeight,
                                            double height,
                                            java.sql.Connection conn,
                                            double tolerance,
                                            int optional3dSrid)
                                     throws java.lang.Exception,
                                            java.sql.SQLException

      Returns the extruded 3-D geometry from a 2-D polygon.
      We expect: \>li\< A 2-D polygon w/ hole(s) or (outer) ring geometry in JGeometry (which will be the base of the solid that we will output): --\< In case of ring: This 2-D polygon (ring) input must be oriented in CCW (on x-y plane) and could be optimized rectangle. When we convert this 2-D polygon (ring) input to the 3-D polygon by adding z=0 coordinates to each vertex, we also check/validate that the orientation of the input polygon (ring) must be CCW on x-y plane and thus it must result +ive value from the dot-product of the normal of this polygon with the unit vector in the direction of +z axis; --\< In case of polygon w/ hole(s): The outer ring must be CCW oriented and inner rings must be CW oriented. We partition this polygon w/ hole(s) into outer rings such that it becomes composite surface without hole(s). In other words, we get rid of hole(s) in the input polygon w/ hole(s). Then, we apply extrusion for (an outer) ring procedure for each ring in this composite surface (comes as collection) and then output the resulting solid as composite solid. It must be noted that in this case user can either input a single grdHeight value and a single height value or grdHeight values and height values ONLY for the outer ring (we interpret those for inner ring(s)) since from satellite images if there are hole(s) in the image, the hole goes \*all\* the way down and since we donot allow patches on solids, we do the conversion from polygon w/ hole(s) to composite surface; and \>/li\< \>li\< A two double numbers of z-values where the first number is for ground height (i.e., the z-value for a vertex of the bottom face of the solid that we will output) and the second number is for height (i.e., the z-value for a vertex of the top face of the same solid that we will output). The height entry for a vertex is always greater or equal to the ground height entry for a vertex. If this is not so, we will issue an error. The extrusion is always either along +z or -z axis. First the newly extruded output solid's bottom face coordinate array, then top face coordinate array, and then side faces' coordinate are formed. \>/li\< \>li\< The parameter tolerance is for validating the input 2D polygon. The parameter cond is deprecated, always use "FALSE" value for cond parameter. \>/li\< \>li\< The connection parameter conn is to run the PL/SQL functions such as convert_2D_srid_to_3D to get the 3-D srid of output geometry wrt 2-D srid of input polygon. For Geodetic, we assume the unit is meter for z values and for projected we assume that it is the same unit as the projected SRID unit. \>/li\< \>li\< If the user knows the resultant solid geometry's 3D srid (null in pl/sql not accepted), this function lets that srid to be input as optional3dSrid. Otherwise, simply ignore optional3dSrid parameter and then this function will calculate the 3d srid for the resultant solid geometry. \>/li\<

      Please note that if there is a single grdHeight value and a single height value for all of the polygon vertices, we replicate grdHeight and height values for each polygon vertex and call original extrusion method.

      For optimized rectangle 2-D polygon (ring) input: the user should give either one height value and one ground height value or 5 element double array for height and 5 element double array for ground height. Otherwise, an error will received. We expand optimized rectangle in CCW orientation. The 5 element arrays must be given in corresponding order with expanded polygon.

      Parameters:
      `polygon` - The polygon w/ hole(s) or outer ring of a 2-D polygon.

      `grdHeight` - A single value

      `height` - A single value

      `conn` - The database connection for calling pl/sql function mdsys.sdo_cs.convert_2d_srid_to_3d to determine the 3-D srid of the new extruded solid //@param cond Deprecated, always use "FALSE" value.

      `tolerance` -

      `optional3dSrid` - If resultant 3D srid is known, that 3D srid can be input. It is the responsibility of user to verify this srid.

      Returns:
      The extruded new solid geometry (as simple or composite solid depending on what the input 2-D polygon is).

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### extrusion

          public static JGeometry extrusion(JGeometry polygon,
                                            double[] grdHeight,
                                            double[] height,
                                            java.sql.Connection conn,
                                            double tolerance)
                                     throws java.lang.Exception,
                                            java.sql.SQLException

      Returns the extruded 3-D geometry from a 2-D polygon.
      We expect: \>li\< A 2-D polygon w/ hole(s) or (outer) ring geometry in JGeometry (which will be the base of the solid that we will output): --\< In case of ring: This 2-D polygon (ring) input must be oriented in CCW (on x-y plane) and could be optimized rectangle. When we convert this 2-D polygon (ring) input to the 3-D polygon by adding z=0 coordinates to each vertex, we also check/validate that the orientation of the input polygon (ring) must be CCW on x-y plane and thus it must result +ive value from the dot-product of the normal of this polygon with the unit vector in the direction of +z axis; --\< In case of polygon w/ hole(s): The outer ring must be CCW oriented and inner rings must be CW oriented. We partition this polygon w/ hole(s) into outer rings such that it becomes composite surface without hole(s). In other words, we get rid of hole(s) in the input polygon w/ hole(s). Then, we apply extrusion for (an outer) ring procedure for each ring in this composite surface (comes as collection) and then output the resulting solid as composite solid. It must be noted that in this case user can either input a single grdHeight value and a single height value or grdHeight values and height values ONLY for the outer ring (we interpret those for inner ring(s)) since from satellite images if there are hole(s) in the image, the hole goes \*all\* the way down and since we donot allow patches on solids, we do the conversion from polygon w/ hole(s) to composite surface; and \>/li\< \>li\< A two double arrays of z-values where the first array is for ground height (i.e., the z-value for a vertex of the bottom face of the solid that we will output) and the second array is for height (i.e., the z-value for a vertex of the top face of the same solid that we will output). The height entry for a vertex is always greater or equal to the ground height entry for a vertex. If this is not so, we will issue an error. The extrusion is always either along +z or -z axis. First the newly extruded output solid's bottom face coordinate array, then top face coordinate array, and then side faces' coordinate are formed. \>/li\< \>li\< The parameter tolerance is for validating the input 2D polygon. The parameter cond is deprecated, always use "FALSE" value for cond parameter. \>/li\< \>li\< The connection parameter conn is to run the PL/SQL functions such as convert_2D_srid_to_3D to get the 3-D srid of output geometry wrt 2-D srid of input polygon. For Geodetic, we assume the unit is meter for z values and for projected we assume that it is the same unit as the projected SRID unit. \>/li\< Please note that if there is a single grdHeight value and a single height value for all of the polygon vertices, we replicate grdHeight and height values for each polygon vertex and call original extrusion method.

      For optimized rectangle 2-D polygon (ring) input: the user should give either one height value and one ground height value or 5 element double array for height and 5 element double array for ground height. Otherwise, an error will received. We expand optimized rectangle in CCW orientation. The 5 element arrays must be given in corresponding order with expanded polygon.

      Parameters:
      `polygon` - The polygon w/ hole(s) or outer ring of a 2-D polygon.

      `grdHeight` - An array of ground height values

      `height` - An array of ground height values

      `conn` - The database connection for calling pl/sql function mdsys.sdo_cs.convert_2d_srid_to_3d to determine the 3-D srid of the new extruded solid //@param cond Deprecated, always use "FALSE" value.

      `tolerance` -

      Returns:
      The extruded new solid geometry (as simple or composite solid depending on what the input 2-D polygon is).

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### extrusion

          public static JGeometry extrusion(JGeometry polygon,
                                            double[] grdHeight,
                                            double[] height,
                                            java.sql.Connection conn,
                                            double tolerance,
                                            int optional3dSrid)
                                     throws java.lang.Exception,
                                            java.sql.SQLException

      Returns the extruded 3-D geometry from a 2-D polygon.
      We expect: \>li\< A 2-D polygon w/ hole(s) or (outer) ring geometry in JGeometry (which will be the base of the solid that we will output): --\< In case of ring: This 2-D polygon (ring) input must be oriented in CCW (on x-y plane) and could be optimized rectangle. When we convert this 2-D polygon (ring) input to the 3-D polygon by adding z=0 coordinates to each vertex, we also check/validate that the orientation of the input polygon (ring) must be CCW on x-y plane and thus it must result +ive value from the dot-product of the normal of this polygon with the unit vector in the direction of +z axis; --\< In case of polygon w/ hole(s): The outer ring must be CCW oriented and inner rings must be CW oriented. We partition this polygon w/ hole(s) into outer rings such that it becomes composite surface without hole(s). In other words, we get rid of hole(s) in the input polygon w/ hole(s). Then, we apply extrusion for (an outer) ring procedure for each ring in this composite surface (comes as collection) and then output the resulting solid as composite solid. It must be noted that in this case user can either input a single grdHeight value and a single height value or grdHeight values and height values ONLY for the outer ring (we interpret those for inner ring(s)) since from satellite images if there are hole(s) in the image, the hole goes \*all\* the way down and since we donot allow patches on solids, we do the conversion from polygon w/ hole(s) to composite surface; and \>/li\< \>li\< A two double arrays of z-values where the first array is for ground height (i.e., the z-value for a vertex of the bottom face of the solid that we will output) and the second array is for height (i.e., the z-value for a vertex of the top face of the same solid that we will output). The height entry for a vertex is always greater or equal to the ground height entry for a vertex. If this is not so, we will issue an error. The extrusion is always either along +z or -z axis. First the newly extruded output solid's bottom face coordinate array, then top face coordinate array, and then side faces' coordinate are formed. \>/li\< \>li\< The parameter tolerance is for validating the input 2D polygon. The parameter cond is deprecated, always use "FALSE" value for cond parameter. \>/li\< \>li\< The connection parameter conn is to run the PL/SQL functions such as convert_2D_srid_to_3D to get the 3-D srid of output geometry wrt 2-D srid of input polygon. For Geodetic, we assume the unit is meter for z values and for projected we assume that it is the same unit as the projected SRID unit. \>/li\< \>li\< If the user knows the resultant solid geometry's 3D srid (null in pl/sql not accepted), this function lets that srid to be input as optional3dSrid. Otherwise, simply ignore optional3dSrid parameter and then this function will calculate the 3d srid for the resultant solid geometry. \>/li\<

      Please note that if there is a single grdHeight value and a single height value for all of the polygon vertices, we replicate grdHeight and height values for each polygon vertex and call original extrusion method.

      For optimized rectangle 2-D polygon (ring) input: the user should give either one height value and one ground height value or 5 element double array for height and 5 element double array for ground height. Otherwise, an error will received. We expand optimized rectangle in CCW orientation. The 5 element arrays must be given in corresponding order with expanded polygon.

      Parameters:
      `polygon` - The polygon w/ hole(s) or outer ring of a 2-D polygon.

      `grdHeight` - An array of ground height values

      `height` - An array of ground height values

      `conn` - The database connection for calling pl/sql function mdsys.sdo_cs.convert_2d_srid_to_3d to determine the 3-D srid of the new extruded solid //@param cond Deprecated, always use "FALSE" value.

      `tolerance` -

      `optional3dSrid` - If resultant 3D srid is known, that 3D srid can be input. It is the responsibility of user to verify this srid.

      Returns:
      The extruded new solid geometry (as simple or composite solid depending on what the input 2-D polygon is).

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### appendToCollection

          public static JGeometry appendToCollection(JGeometry collGeom,
                                                     JGeometry scGeom)
                                              throws java.lang.Exception

      Returns a collection or multi-x geometry by appending simple (x) geometries in 3-D.
      The outGeom could be collection or multi geometry. The scGeom is either "s"imple or "c"omposite geometry. We append scGeom to collGeom in outGeom, which is the output, as long as the following rules are satisfied: \>li\< collGeom of gtype collection can get any geometry. \>/li\< \>li\< collGeom of gtype Multi X can only get simple and comp-X's. \>/li\< \>li\< inGeom cannot be multi-x geometry (i.e., no multi-level nesting). \>/li\<

      Use append PL/SQL interface instead of this function.

      Parameters:
      `collGeom` - A collection or multi geometry

      `scGeom` - A simple or composite geometry

      Returns:
      appended collection or multi-x geometry

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### centroid3d

          public J3D_Geometry centroid3d(double tolerance)
                                  throws java.lang.Exception

      Returns the centroid aka center of mass, center of gravity of solid 3-D geometry of uniform material density.
      If input geometry is a collection or any curve, we return the zero point.

      The inner solid boundaries are treated like negative volumes (i.e.,masses with unit density). First, the centroids of outer solid boundaries are found. Then, we combine the centroids of outer solid boundaries into the global (net) centroid. Similarly, we do the same for inner solid boundaries. Then, the net (global) centroid will be combination of these two centroids by treating the one belonging to the inner solid boundaries as -ive mass. The centroid of any two objects lie on the line segment connecting them.

      The above approach is valid for polygons.

      For polygons/surfaces/solids, we shift all the coordinates WRT to the center of the MBR(geometry). This shift is done to avoid the round off errors in the area computation. The center of overall geometry (this) is added to the gloabl (net) centroid at the end. We donot need to restore the original geometry back to the input state since we donot modify input geometry.

      Parameters:
      `tolerance` - User tolerance

      Returns:
      J3D_Geometry point geometry which is the center of mass of geometry.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### inside3d

          public boolean inside3d(J3D_Geometry solid2,
                                  double tolerance)
                           throws java.lang.Exception

      Returns whether the first Cartesian geometry is inside the solid (second Cartesian geometry) or not.
      Inner geometries of first geometry are ignored. Composite solids are treated like multi-solids such that if the point is on a shared face of second geometry which is composite-solid, then the point is considered to be outside second geometry, which is solid.

      //@param this Any 3-D Cartesian geometry

      Parameters:
      `solid2` - 3-D Cartesian geometry

      `tolerance` - User tolerance

      Returns:
      true/false.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### inside3d

          public boolean inside3d(J3D_Geometry solid2,
                                  double tolerance,
                                  java.lang.String is_g3d)
                           throws java.lang.Exception

      Returns whether the first geometry is inside the solid (second geometry) or not.
      Inner geometries of first geometry are ignored. Composite solids are treated like multi-solids such that if the point is on a shared face of second geometry which is composite-solid, then the point is considered to be outside second geometry, which is solid.

      If data are Geographic3D (by setting is_g3d as TRUE), then Gnomonic transformation (projection) is carried out here. The tolerance value is set to 0.05 in Gnomonic transformation no matter what the user input tolerance is.

      Geodetic/Geographic 3D geometries should not span long distances.

      //@param this Any 3-D geometry

      Parameters:
      `solid2` - 3-D geometry

      `tolerance` - User tolerance

      `is_g3d` - Flag to denote whether input geometries are Geodetic/Geographic 3D or not (TRUE/FALSE)

      Returns:
      true/false.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getElementByLabel

          public J3D_Geometry getElementByLabel(java.lang.String label)
                                         throws java.lang.Exception

      Returns the sub-geometry indicated by the label string. Input 3-D geometry where we will pick the sub-geometry pointed by the label string.
      Parameters:
      `label` - The label indicating the sub-geometry that the user wants to extract. A generic label could be: pointID,edgeID,ringID,polygonID,csurfID,solidID,multiID

      Returns:
      J3D_Geometry Geometry which is pointed by the label.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getLabelByElement

          public java.lang.String getLabelByElement(J3D_Geometry qryElement,
                                                    double tolerance)
                                             throws java.lang.Exception

      Computes the corresponding sub-geometry's label within the geometry. This function is the reverse function of getElementByLabel. That is, this function accepts a simple but valid SDO_GEOMETRY object (i.e., qryElement) as input and it finds the corresponding label for it in a more complex SDO_GEOMETRY (i.e., this: the geometry where we are looking for qryElement).
      This function is commutable with the extract with label function. That is, if we start with a geometry and do extract with a label via getElementByLabel function and pass the result to this function, the resulting label should be the same as the one given as input to the extract (i.e., getElementByLabel) function.

      Inner solid boundary will be entered as GTYPE_POLYGON (3003) and ETYPE_COMPOSITESURFACE (1006) for qryElement input. Thus, this function matches the reverse orientation via reverseOrientation function.

      The outer geometries of qryElement is matched to the outer geometries of this (source) first, and then the inner geometries of qryElement are matched to the inner geometries of this (source).

      The threshold value is set to 10, which means if there are fewer than 10 sub-elements in the geometry, brute-force is used, else R-Tree is used.

      Parameters:
      `qryElement` - The geometry we are looking for

      `tolerance` - User defined tolerance

      Returns:
      String Label of the qryElement within this

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### expandGeom

          public static J3D_Geometry expandGeom(J3D_Geometry geometry)
                                         throws java.lang.Exception

      Returns the expanded geometry. If input geometry has 1003,3, 2003,3, 1007,3 or \_,1,n shortcut formats, this method will return a geometry where these elements are flattened (converted) to 1003,1, 2003,1, 1007,1 and \_,1,1 respectively. This method is especially used by the sdo_3gl.relateG3D pl/sql function.
      Parameters:
      `geometry` - The J3D_Geometry to be expanded

      Returns:
      J3D_Geometry

      Throws:
      `java.lang.Exception`

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

- [Prev Class](FastJGeometry.PPStatus.md)
- [Next Class](JGeometry.md)

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
