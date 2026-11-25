Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.spatial.geometry

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - java.util.AbstractCollection\<E\> (implements java.util.Collection\<E\>)
    - oracle.spatial.geometry.[AbstractRTree](AbstractRTree.md)\<T\> (implements oracle.spatial.geometry.[RTreeInterface](RTreeInterface.md)\<T\>)
      - oracle.spatial.geometry.[RStarTree](RStarTree.md)\<T\> (implements oracle.spatial.geometry.[RTreeInterface](RTreeInterface.md)\<T\>, java.io.Serializable)
  - oracle.spatial.geometry.[Chain](Chain.md)
  - oracle.spatial.geometry.[Chain.AccurateSum](Chain.AccurateSum.md)
  - oracle.spatial.geometry.[CompJGeom](CompJGeom.md)
  - oracle.spatial.geometry.[CoordSysInfo](CoordSysInfo.md) (implements java.io.Serializable)
  - oracle.spatial.geometry.[ElementExtractor](ElementExtractor.md)
  - oracle.spatial.geometry.[JGeometry](JGeometry.md) (implements java.lang.Cloneable, oracle.spatial.geometry.[RNode](RNode.md), java.io.Serializable)
    - oracle.spatial.geometry.[FastJGeometry](FastJGeometry.md)
    - oracle.spatial.geometry.[J3D_Geometry](J3D_Geometry.md)
  - oracle.spatial.geometry.[JGeometry.Point](JGeometry.Point.md)
  - oracle.spatial.geometry.[JGeomToGeoJson](JGeomToGeoJson.md)
  - oracle.spatial.geometry.[JPoint2DD](JPoint2DD.md) (implements java.io.Serializable)
    - oracle.spatial.geometry.[Chain.CenterPoint](Chain.CenterPoint.md)
  - oracle.spatial.geometry.[JPoint3DD](JPoint3DD.md)
    - oracle.spatial.geometry.[UnitSphere](UnitSphere.md)
  - oracle.spatial.geometry.[LRSGeometryG3D](LRSGeometryG3D.md)
  - oracle.spatial.geometry.[Mer](Mer.md) (implements oracle.spatial.geometry.[RNode](RNode.md), java.io.Serializable)
  - oracle.spatial.geometry.[Ops](Ops.md)
  - oracle.spatial.geometry.[OpsJGeometry](OpsJGeometry.md)
  - oracle.spatial.geometry.[Pair](Pair.md)\<P,Q\> (implements java.io.Serializable)
    - oracle.spatial.geometry.[AbstractRTree.PairDebug](AbstractRTree.PairDebug.md)\<P,Q\>
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.spatial.geometry.[DataException](DataException.md)
  - oracle.spatial.geometry.[Union](Union.md)

## Interface Hierarchy

- java.lang.Iterable\<T\>
  - java.util.Collection\<E\>
    - oracle.spatial.geometry.[RTreeInterface](RTreeInterface.md)\<T\>
- oracle.spatial.geometry.[JGeometry.GeomParser](JGeometry.GeomParser.md)
- oracle.spatial.geometry.[RNode](RNode.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.spatial.geometry.[FastJGeometry.FastOp](FastJGeometry.FastOp.md)
    - oracle.spatial.geometry.[FastJGeometry.PPStatus](FastJGeometry.PPStatus.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
