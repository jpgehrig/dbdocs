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

- [Prev Class](ElementExtractor.md)
- [Next Class](FastJGeometry.FastOp.md)

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

## Class FastJGeometry

- java.lang.Object

- - [oracle.spatial.geometry.JGeometry](JGeometry.md)

  - - oracle.spatial.geometry.FastJGeometry

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, [RNode](RNode.md)

  ------------------------------------------------------------------------



      public final class FastJGeometry
      extends JGeometry

  Subclass of JGeometry that is capable of preprocessing the geometry and storing extra information to allow later operations to be performed faster.
  Currently does not handle arcs or splines.

  Since:
  release specific (what release of product did this appear in)

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                                                        |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`FastJGeometry.FastOp`](FastJGeometry.FastOp.md)<br>Operations can be accelerated by doing preprocessing beforehand.                                                                                        |
    | `static class `   | [`FastJGeometry.PPStatus`](FastJGeometry.PPStatus.md)<br>Whether a particular operation is PREPROCESSed, should NEVER be preprocessed, or may be AUTOmatcially done at the discretion of the implementation. |

    - ### Nested classes/interfaces inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`JGeometry.GeomParser`](JGeometry.GeomParser.md)`, `[`JGeometry.Point`](JGeometry.Point.md)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`GTYPE_COLLECTION`](JGeometry.md)`, `[`GTYPE_CURVE`](JGeometry.md)`, `[`GTYPE_MULTICURVE`](JGeometry.md)`, `[`GTYPE_MULTIPOINT`](JGeometry.md)`, `[`GTYPE_MULTIPOLYGON`](JGeometry.md)`, `[`GTYPE_POINT`](JGeometry.md)`, `[`GTYPE_POLYGON`](JGeometry.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FastJGeometry``(`[`JGeometry`](JGeometry.md)` geom, double tolerance)`<br>All eligible operations will be preprocessed automatically at the discretion of the implementation.                                                                                      |
    | `FastJGeometry``(`[`JGeometry`](JGeometry.md)` geom, double tolerance, java.util.EnumSet<`[`FastJGeometry.FastOp`](FastJGeometry.FastOp.md)`> opsSet, boolean defaultAuto)`<br>Creates a shallow copy of the given geometry that will be preprocessed as specified. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                           |
    |-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                             | `anyInteract``(`[`JGeometry`](JGeometry.md)` B, double tolerance)`<br>This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry. |
    | `double`                                              | `distance``(`[`JGeometry`](JGeometry.md)` A)`<br>Compute distance to geometry A using the tolerance and isGeodetic values passed at creation.                    |
    | `double`                                              | `distance``(`[`JGeometry`](JGeometry.md)` B, double tolerance)`<br>This method determines the distance between two 2D Geometries.                                |
    | [`FastJGeometry.PPStatus`](FastJGeometry.PPStatus.md) | `getPPStatus``(`[`FastJGeometry.FastOp`](FastJGeometry.FastOp.md)` op)`<br>Return the preprocessing status of the specified operation.                           |
    | `boolean`                                             | `isInside``(`[`JGeometry`](JGeometry.md)` B, double tolerance)`<br>Determine whether this geometry is inside B.                                                  |

    - ### Methods inherited from class oracle.spatial.geometry.[JGeometry](JGeometry.md)

      [`affineTransforms`](JGeometry.md)`, `[`anyInteract`](JGeometry.md)`, `[`anyInteract`](JGeometry.md)`, `[`area`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`buffer`](JGeometry.md)`, `[`byteArrayToHexString`](JGeometry.md)`, `[`centralLongLatforGNMProjection`](JGeometry.md)`, `[`circle_polygon`](JGeometry.md)`, `[`circle_polygon`](JGeometry.md)`, `[`clone`](JGeometry.md)`, `[`computeArc`](JGeometry.md)`, `[`concaveHullDig`](JGeometry.md)`, `[`convexHull`](JGeometry.md)`, `[`coord`](JGeometry.md)`, `[`createArc2d`](JGeometry.md)`, `[`createCircle`](JGeometry.md)`, `[`createCircle`](JGeometry.md)`, `[`createDoubleShape`](JGeometry.md)`, `[`createDoubleShape`](JGeometry.md)`, `[`createLinearLineString`](JGeometry.md)`, `[`createLinearMultiLineString`](JGeometry.md)`, `[`createLinearPolygon`](JGeometry.md)`, `[`createLinearPolygon`](JGeometry.md)`, `[`createLRSLinearLineString`](JGeometry.md)`, `[`createLRSLinearMultiLineString`](JGeometry.md)`, `[`createLRSLinearPolygon`](JGeometry.md)`, `[`createLRSLinearPolygon`](JGeometry.md)`, `[`createLRSPoint`](JGeometry.md)`, `[`createMultiPoint`](JGeometry.md)`, `[`createNURBScurve`](JGeometry.md)`, `[`createPoint`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`createShape`](JGeometry.md)`, `[`crossesMeridian`](JGeometry.md)`, `[`decodePolyline`](JGeometry.md)`, `[`defaultTolerance`](JGeometry.md)`, `[`densifyArcs`](JGeometry.md)`, `[`densifyArcs`](JGeometry.md)`, `[`densifyGeodesic`](JGeometry.md)`, `[`densifyGeodesic`](JGeometry.md)`, `[`distance`](JGeometry.md)`, `[`encodePolyline`](JGeometry.md)`, `[`equals`](JGeometry.md)`, `[`expandCircle`](JGeometry.md)`, `[`fitArc`](JGeometry.md)`, `[`fitsInHemisphere`](JGeometry.md)`, `[`geodetic3DLength`](JGeometry.md)`, `[`geodetic3DLength`](JGeometry.md)`, `[`getCoordSysInfo`](JGeometry.md)`, `[`getDimensions`](JGeometry.md)`, `[`getElementAt`](JGeometry.md)`, `[`getElements`](JGeometry.md)`, `[`getElemInfo`](JGeometry.md)`, `[`getExtendedMBR`](JGeometry.md)`, `[`getFirstPoint`](JGeometry.md)`, `[`getGeomDescriptor`](JGeometry.md)`, `[`getJavaPoint`](JGeometry.md)`, `[`getJavaPoints`](JGeometry.md)`, `[`getLabelPoint`](JGeometry.md)`, `[`getLabelPointXYZ`](JGeometry.md)`, `[`getLastPoint`](JGeometry.md)`, `[`getLRMDimension`](JGeometry.md)`, `[`getMBR`](JGeometry.md)`, `[`getMer`](JGeometry.md)`, `[`getNumPoints`](JGeometry.md)`, `[`getNurbsApprox`](JGeometry.md)`, `[`getOracleDescriptors`](JGeometry.md)`, `[`getOracleDescriptorsStr`](JGeometry.md)`, `[`getOrdinatesArray`](JGeometry.md)`, `[`getOrdinatesOfElements`](JGeometry.md)`, `[`getOrientMultiPointOffset`](JGeometry.md)`, `[`getPoint`](JGeometry.md)`, `[`getSize`](JGeometry.md)`, `[`getSRID`](JGeometry.md)`, `[`getType`](JGeometry.md)`, `[`hasCircularArcs`](JGeometry.md)`, `[`isCircle`](JGeometry.md)`, `[`isGeodetic`](JGeometry.md)`, `[`isGeodeticMBR`](JGeometry.md)`, `[`isInside`](JGeometry.md)`, `[`isLRSGeometry`](JGeometry.md)`, `[`isMultiPoint`](JGeometry.md)`, `[`isOrientedMultiPoint`](JGeometry.md)`, `[`isOrientedPoint`](JGeometry.md)`, `[`isPoint`](JGeometry.md)`, `[`isRectangle`](JGeometry.md)`, `[`length`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`linearizeArc`](JGeometry.md)`, `[`load`](JGeometry.md)`, `[`loadJS`](JGeometry.md)`, `[`loadJS`](JGeometry.md)`, `[`make_2d`](JGeometry.md)`, `[`make_3d`](JGeometry.md)`, `[`make_3dgeom`](JGeometry.md)`, `[`make_3dgeom`](JGeometry.md)`, `[`monoMeasure`](JGeometry.md)`, `[`parseGeometry`](JGeometry.md)`, `[`projectArrayToGNM`](JGeometry.md)`, `[`projectFromGNM_longLat`](JGeometry.md)`, `[`projectFromLTP`](JGeometry.md)`, `[`projectToGNM_longLat`](JGeometry.md)`, `[`projectToGNM_longLat`](JGeometry.md)`, `[`projectToLTP`](JGeometry.md)`, `[`projectToLTP`](JGeometry.md)`, `[`reFormulateArc`](JGeometry.md)`, `[`setLRMDimension`](JGeometry.md)`, `[`setSRID`](JGeometry.md)`, `[`setType`](JGeometry.md)`, `[`simplify`](JGeometry.md)`, `[`simplify`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`simplifyVW`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`store`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`storeJS`](JGeometry.md)`, `[`tfm_8307_to_PopularMercator`](JGeometry.md)`, `[`tfm_8307_to_PopularMercator`](JGeometry.md)`, `[`tfm_PopularMercator_to_8307`](JGeometry.md)`, `[`tfm_PopularMercator_to_8307`](JGeometry.md)`, `[`toGeoJson`](JGeometry.md)`, `[`toGeoJsonCollection`](JGeometry.md)`, `[`toString`](JGeometry.md)`, `[`toStringFull`](JGeometry.md)`, `[`toStringFull`](JGeometry.md)`, `[`volume`](JGeometry.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FastJGeometry

          public FastJGeometry(JGeometry geom,
                               double tolerance,
                               java.util.EnumSet<FastJGeometry.FastOp> opsSet,
                               boolean defaultAuto)
                        throws java.lang.Exception

      Creates a shallow copy of the given geometry that will be preprocessed as specified. After preprocessing the specified operations will run faster.
      Preprocessing does not help in all cases:

      - Preprocessing takes time and uses some extra storage. Generally preprocessing should be considered only when an operation on a geometry is likely to be repeated at least 50 times.
      - Preprocessing may not be useful if the tolerance does not match the value passed at creation.
      - Some geometries may not be preprocessable (e.g., a single point; splines).
      - Only 2D geometries can be preprocessed.

      If preprocessing can not be done, or if the preprocessed information is not usable (e.g., due to tolerance), the normal, non-preprocessed operation will be performed.
      Preprocessing is intended to be harmless; operations should return their contracted results whether or not preprocessing succeeded, regardless of the values used for preprocessing. However, results do change in some cases due to the different algorithms. If exactly reproducable results are required, especially for results affected by tolerances, preprocessing should be used always or never for that operation. AUTO is particularly discouraged if exactly reproducable results are required.

      Preprocessing information is usable both when a method on FastJGeometry is called, and also when a FastJGeometry is passed to a JGeometry method.

      This object is not thread-safe.

      Example usage: ` JGeometry geom = new JGeometry(2003, SRID, new int[] { 1, 2, 1 }, new double[] { 3,3, 6,6 }); FastJGeometry fastGeom = new FastJGeometry(fjg, 0.05, false, EnumSet.of(JGeometry.FastOp.DISTANCE, JGeometry.FastOp.ANYINTERACT)); JGeometry otherGeom = new JGeometry(2003, SRID, new int[] { 1, 2, 1 }, new double[] { 0,0, 9,9 }); double dist1 = fastGeom.distance(otherGeom); // Defaults tolerance and isGeodetic values double dist2 = otherGeom.distance(fastGeom, 0.05, false); // Returns same answer using same preprocessed info in fjg // (parameter order doesn't matter for distance). `

      AUTO allows the implementation freedom to decide when to preprocess based on usage.

      Parameters:
      `geom` - must not be modified after this object is created.

      `tolerance` -

      `isGeodetic` -

      `opsSet` - list of operations to preprcoess immediately

      `defaultAuto` - true = other operations are AUTO (may also be preprocessed); false = NEVER preprocess other operations

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### FastJGeometry

          public FastJGeometry(JGeometry geom,
                               double tolerance)
                        throws java.lang.Exception

      All eligible operations will be preprocessed automatically at the discretion of the implementation.
      Parameters:
      `geom` -

      `tolerance` -

      `isGeodetic` -

      Throws:
      `java.lang.Exception`

  <!-- -->

  - ### Method Detail

    - #### getPPStatus

          public FastJGeometry.PPStatus getPPStatus(FastJGeometry.FastOp op)

      Return the preprocessing status of the specified operation.
      - PREPROCESS means the operation has been preprocessed.
      - AUTO means that preprocessing for the operation hasn't happend yet, but may automatically happen when the operation is used.
      - NEVER means that the operation never stores preprocessed information.

      Parameters:

      `op` -

      Returns:

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(JGeometry B,
                                     double tolerance)
                              throws java.lang.Exception

      This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry. The geometries can be any 2D/3D types supported by Oracle Spatial including geometries with arcs and compund elements.
      Overrides:
      [`anyInteract`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `B` - 2D/3D Geometry

      `tolerance` - at which the given geometry is valid

      `isGeodetic` - true if the geometries are geodetic

      Returns:
      TRUE if the two geometries interact; FALSE otherwise

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distance

          public double distance(JGeometry B,
                                 double tolerance)
                          throws java.lang.Exception

      This method determines the distance between two 2D Geometries.
      Overrides:
      [`distance`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `B` - 2D Geometry that is a polygon or multi-polygon

      `tolerance` - at which the given geometry is valid

      `isGeodetic` - if the geometries are geodetic

      Returns:
      distance between the two given geometries. For projected data, the distance is in the same UNIT as the unit of projection. For Geodetic, the distance is in METERS.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distance

          public double distance(JGeometry A)
                          throws java.lang.Exception

      Compute distance to geometry A using the tolerance and isGeodetic values passed at creation.
      Parameters:
      `A` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isInside

          public boolean isInside(JGeometry B,
                                  double tolerance)
                           throws java.lang.Exception

      Determine whether this geometry is inside B.
      Overrides:
      [`isInside`](JGeometry.md) in class [`JGeometry`](JGeometry.md)

      Parameters:
      `B` -

      `tolerance` -

      `isGeodetic` -

      Returns:
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

- [Prev Class](ElementExtractor.md)
- [Next Class](FastJGeometry.FastOp.md)

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
