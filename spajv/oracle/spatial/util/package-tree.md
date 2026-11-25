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

- [Prev](../topo/package-tree.md)
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.spatial.util

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.spatial.util.[Adapters](Adapters.md)
  - oracle.spatial.util.[AdapterShapefileJGeom](AdapterShapefileJGeom.md)
  - oracle.spatial.util.[ByteOrder](ByteOrder.md)
    - oracle.spatial.util.[ByteOrderBigEndian](ByteOrderBigEndian.md)
    - oracle.spatial.util.[ByteOrderLittleEndian](ByteOrderLittleEndian.md)
  - oracle.spatial.util.[ClipPcFlatCells](ClipPcFlatCells.md)
  - oracle.spatial.util.[ClipPcIntoTxt](ClipPcIntoTxt.md)
  - java.awt.Component (implements java.awt.image.ImageObserver, java.awt.MenuContainer, java.io.Serializable)
    - java.awt.Container
      - java.awt.Window (implements javax.accessibility.Accessible)
        - java.awt.Frame (implements java.awt.MenuContainer)
          - oracle.spatial.util.[RTree.RTreePlot](RTree.RTreePlot.md)
  - oracle.spatial.util.[Contour](Contour.md)
  - oracle.spatial.util.[CoordRefSys](CoordRefSys.md)
  - oracle.spatial.util.[CoordRefSys.Srid](CoordRefSys.Srid.md)
    - oracle.spatial.util.[CoordRefSys.GeodeticSrid](CoordRefSys.GeodeticSrid.md)
    - oracle.spatial.util.[CoordRefSys.ProjectedSrid](CoordRefSys.ProjectedSrid.md)
      - oracle.spatial.util.[CoordRefSys.LambertConformalConicSrid](CoordRefSys.LambertConformalConicSrid.md)
      - oracle.spatial.util.[CoordRefSys.TransverseMercatorSrid](CoordRefSys.TransverseMercatorSrid.md)
  - oracle.spatial.util.[CustomCrsExport](CustomCrsExport.md)
  - oracle.spatial.util.[DBFReaderJGeom](DBFReaderJGeom.md)
  - oracle.spatial.util.[DBFReaderJGeom.RecordColumn](DBFReaderJGeom.RecordColumn.md)
    - oracle.spatial.util.[DBFReaderJGeom.CharacterColumn](DBFReaderJGeom.CharacterColumn.md)
    - oracle.spatial.util.[DBFReaderJGeom.DateColumn](DBFReaderJGeom.DateColumn.md)
    - oracle.spatial.util.[DBFReaderJGeom.LogicalColumn](DBFReaderJGeom.LogicalColumn.md)
    - oracle.spatial.util.[DBFReaderJGeom.NumericColumn](DBFReaderJGeom.NumericColumn.md)
  - oracle.spatial.util.[DBMS](DBMS.md)
  - oracle.spatial.util.[ExtendedKML2](ExtendedKML2.md)
  - oracle.spatial.util.[Generalization3D](Generalization3D.md)
  - oracle.spatial.util.[GeoHash](GeoHash.md) (implements java.io.Serializable)
  - oracle.spatial.util.[GML](GML.md)
  - oracle.spatial.util.[GML2](GML2.md)
  - oracle.spatial.util.[GML3](GML3.md)
  - oracle.spatial.util.[GML3g](GML3g.md)
  - oracle.spatial.util.[GroupingLOD1Generalization](GroupingLOD1Generalization.md)
  - oracle.spatial.util.[Hilbert](Hilbert.md)
  - oracle.spatial.util.[JDBCAdapter](JDBCAdapter.md)
  - oracle.spatial.util.[JDBCUtil](JDBCUtil.md)
  - oracle.spatial.util.[KML](KML.md)
  - oracle.spatial.util.[KML2](KML2.md)
  - oracle.spatial.util.[Las2SqlLdr](Las2SqlLdr.md)
  - oracle.spatial.util.[Las2SqlLdr.LasFileStream](Las2SqlLdr.LasFileStream.md)
  - oracle.spatial.util.[Las2SqlLdr.PointData](Las2SqlLdr.PointData.md)
  - oracle.spatial.util.[Las2SqlLdr.PointData.MBR](Las2SqlLdr.PointData.MBR.md)
  - oracle.spatial.util.[Las2SqlLdr.PointData.SinglePoint](Las2SqlLdr.PointData.SinglePoint.md)
  - oracle.spatial.util.[Las2SqlLdrIndep](Las2SqlLdrIndep.md)
  - oracle.spatial.util.[LASImportExport](LASImportExport.md)
  - oracle.spatial.util.[Logger](Logger.md)
  - oracle.spatial.util.[Pc2Dem](Pc2Dem.md)
  - oracle.spatial.util.[Pc2Las](Pc2Las.md)
  - oracle.spatial.util.[PCPyramidFilter](PCPyramidFilter.md)
  - oracle.spatial.util.[PcSampleDataSet](PcSampleDataSet.md)
  - oracle.spatial.util.[RTree](RTree.md) (implements java.io.Serializable)
  - oracle.spatial.util.[RTree.ComparatorImpl](RTree.ComparatorImpl.md) (implements java.util.Comparator\<T\>)
  - oracle.spatial.util.[RTreeJoinRes](RTreeJoinRes.md)
  - oracle.spatial.util.[SampleShapefileToJGeom](SampleShapefileToJGeom.md)
  - oracle.spatial.util.[SampleShapefileToJGeomFeature](SampleShapefileToJGeomFeature.md)
  - oracle.spatial.util.[SchemaEntityResolver](SchemaEntityResolver.md) (implements org.xml.sax.EntityResolver)
  - oracle.spatial.util.[SDODoubleGeneralPath](SDODoubleGeneralPath.md) (implements java.lang.Cloneable, java.awt.Shape)
  - oracle.spatial.util.[SdoPointInPolygon](SdoPointInPolygon.md)
  - oracle.spatial.util.[SegY2SqlLdr](SegY2SqlLdr.md)
  - oracle.spatial.util.[ShapefileFeatureJGeom](ShapefileFeatureJGeom.md)
  - oracle.spatial.util.[ShapefileReaderJGeom](ShapefileReaderJGeom.md)
  - oracle.spatial.util.[SqlLdrStreamWrapper](SqlLdrStreamWrapper.md)
  - oracle.spatial.util.[StAXCityGML](StAXCityGML.md)
  - oracle.spatial.util.[StAXGML](StAXGML.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.spatial.util.[GeometryExceptionWithContext](GeometryExceptionWithContext.md)
  - oracle.spatial.util.[TIN2Contours](TIN2Contours.md)
  - oracle.spatial.util.[Util](Util.md)
  - oracle.spatial.util.[WKBasis](WKBasis.md) (implements oracle.spatial.util.[WKAdapter](WKAdapter.md))
    - oracle.spatial.util.[WKB](WKB.md) (implements oracle.spatial.util.[WKAdapter](WKAdapter.md))
    - oracle.spatial.util.[WKT](WKT.md) (implements oracle.spatial.util.[WKAdapter](WKAdapter.md))
  - oracle.spatial.util.[XMLValidator](XMLValidator.md)
  - oracle.spatial.util.[XMLValidator2](XMLValidator2.md)

## Interface Hierarchy

- java.lang.Iterable\<T\>
  - java.util.Collection\<E\>
    - oracle.spatial.geometry.[RTreeInterface](../geometry/RTreeInterface.md)\<T\>
      - oracle.spatial.util.[RTreeInterface](RTreeInterface.md)\<T\>
- oracle.spatial.util.[JDBCExtensionInterface](JDBCExtensionInterface.md)
- oracle.spatial.util.[WKAdapter](WKAdapter.md)
- oracle.spatial.util.[WKInputStream](WKInputStream.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.spatial.util.[Util.CheckType](Util.CheckType.md)
    - oracle.spatial.util.[GML3.GMLVersion](GML3.GMLVersion.md)

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

- [Prev](../topo/package-tree.md)
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
