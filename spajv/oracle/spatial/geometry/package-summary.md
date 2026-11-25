Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Package
- [Next Package](../georaster/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.spatial.geometry

- **Interface Summary**

  | Interface                                                          | Description                                                                                                                                                                             |
  |--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [JGeometry.GeomParser](JGeometry.GeomParser.md)                    | Callbacks for parsing this geometry via parseGeometry                                                                                                                                   |
  | [RNode](RNode.md)                                                  | Marks an object with a Mer.                                                                                                                                                             |
  | [RTreeInterface](RTreeInterface.md)\<T extends [RNode](RNode.md)\> | An RTree or RTree-like data structure, in which objects are stored by Mers in a nested hierarchy where the Mer of each internal (non-data) node covers the Mers of all its descendents. |

- **Class Summary**

  | Class                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
  |------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AbstractRTree](AbstractRTree.md)\<T extends [RNode](RNode.md)\> | This class provides a skeletal implementation of the [`RTreeInterface`](RTreeInterface.md) interface to minimize the effort required to implement an RTree.                                                                                                                                                                                                                                                                                                                                                 |
  | [AbstractRTree.PairDebug](AbstractRTree.PairDebug.md)\<P,Q\>     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | [Chain](Chain.md)                                                | Provides an efficient double-ended list of vertices, which can be referenced by either end.                                                                                                                                                                                                                                                                                                                                                                                                                 |
  | [Chain.AccurateSum](Chain.AccurateSum.md)                        | Accurately accumulate a summation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
  | [Chain.CenterPoint](Chain.CenterPoint.md)                        | Abusing subclassing --- this is used to store the centers of circular arcs in Chain.                                                                                                                                                                                                                                                                                                                                                                                                                        |
  | [CompJGeom](CompJGeom.md)                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | [CoordSysInfo](CoordSysInfo.md)                                  | Immutable, thread-safe class that stores simplified coordinate system information.                                                                                                                                                                                                                                                                                                                                                                                                                          |
  | [ElementExtractor](ElementExtractor.md)                          | This extractor extracts elements from J3D_Geometry in an iterative fashion Composite surface is expected to be: \< , 1006, N\> N tuples of the form \<, 1003, x\> \<, 2003, x\>\* Composite solid should be of the form: \< , 1008, N\> N solids each of the form \<, 1007,\> specified using 1 outer surface and N inner surfaces \<, 1006, m\> and M tuples of the form \<,1003,\> m times followed by 0 or more inner solids specified as surfaces as: \<, 2006, p\> and p tuples of the form \<,2003,\> |
  | [FastJGeometry](FastJGeometry.md)                                | Subclass of JGeometry that is capable of preprocessing the geometry and storing extra information to allow later operations to be performed faster.                                                                                                                                                                                                                                                                                                                                                         |
  | [J3D_Geometry](J3D_Geometry.md)                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | [JGeometry](JGeometry.md)                                        | A Java class that maps Oracle Spatial's SQL type MDSYS.SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
  | [JGeometry.Point](JGeometry.Point.md)                            | Deprecated<br>use @link{oracle.spatial.geometry.JPoint2DD} instead                                                                                                                                                                                                                                                                                                                                                                                                                                          |
  | [JGeomToGeoJson](JGeomToGeoJson.md)                              | Provides convenient methods to generate JSON fragments.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
  | [JPoint2DD](JPoint2DD.md)                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | [JPoint3DD](JPoint3DD.md)                                        | Immutable 3D point or vector.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
  | [LRSGeometryG3D](LRSGeometryG3D.md)                              | This class defines an LRS Geodetic 3D geometry object                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
  | [Mer](Mer.md)                                                    | Provides helper methods for mers stored as bare arrays, as well as an encapsulated type.                                                                                                                                                                                                                                                                                                                                                                                                                    |
  | [Ops](Ops.md)                                                    | Utility class for a variety of geometry operations.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
  | [OpsJGeometry](OpsJGeometry.md)                                  | Behavior is undefined if the underlying geometry is modified.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
  | [Pair](Pair.md)\<P,Q\>                                           | A simple utility class for holding a pair of elements.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
  | [RStarTree](RStarTree.md)\<T extends [RNode](RNode.md)\>         | TODO Must work for arbitrary dimension --- check that there's no 2D-specific stuff! An in-memory implementation of R\*-tree.                                                                                                                                                                                                                                                                                                                                                                                |
  | [Union](Union.md)                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | [UnitSphere](UnitSphere.md)                                      | Immutable 3D representation of a point on a sphere with conversions to and from long/lat.                                                                                                                                                                                                                                                                                                                                                                                                                   |

- **Enum Summary**

  | Enum                                                | Description                                                                                                                                         |
  |-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
  | [FastJGeometry.FastOp](FastJGeometry.FastOp.md)     | Operations can be accelerated by doing preprocessing beforehand.                                                                                    |
  | [FastJGeometry.PPStatus](FastJGeometry.PPStatus.md) | Whether a particular operation is PREPROCESSed, should NEVER be preprocessed, or may be AUTOmatcially done at the discretion of the implementation. |

- **Exception Summary**

  | Exception                         | Description                                            |
  |-----------------------------------|--------------------------------------------------------|
  | [DataException](DataException.md) | Reports SDOVIS exception related with map data access. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Package
- [Next Package](../georaster/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
