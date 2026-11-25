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

- [Prev Package](../geometry/package-summary.md)
- [Next Package](image/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.spatial.georaster

- **Class Summary**

  | Class                                                       | Description                                                                                                                                                                                                                                                    |
  |-------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [BandReferenceInfo](BandReferenceInfo.md)                   | BandReferenceInfo is a Java class mapped to the XML element BandReferenceInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                        |
  | [GCPGeoreference](GCPGeoreference.md)                       | GCPGeoreference represents the PL/SQL type MDSYS.SDO_GEOR_GEOREFERENCE It could be used to load Ground Control Points into a GeoRaster using sdo_geor.georeference.                                                                                            |
  | [GCPPoint](GCPPoint.md)                                     |                                                                                                                                                                                                                                                                |
  | [GeorColormap](GeorColormap.md)                             | GeorColormap is combined with class GeorColormapEnrty to represent a GeoRaster colormap, which contains an array of GeorColormapEnrty instances, and each GeorColormapEnrty contains four components: red, green, blue, and alpha (alpha is optional).         |
  | [GeorColormapEntry](GeorColormapEntry.md)                   | A GeoRaster colormap entry, which contains five components: cellValue, red, green, blue, and alpha (alpha is optional).                                                                                                                                        |
  | [GeorFunctionalFittingModel](GeorFunctionalFittingModel.md) | GeorFunctionFittingModel is a Java class that maps to the XML type rationalPolynomialType defined in the GeoRaster XML schema.                                                                                                                                 |
  | [GeorGrayscale](GeorGrayscale.md)                           | GeorGrayscale class is combined with class GeorGrayscaleEntry to represent a GeoRaster grayscale, which contains an array of GeorGrayscaleEntry instances, and each GeorGrayscaleEntry contains a pair of cell value and gray value.                           |
  | [GeorGrayscaleEntry](GeorGrayscaleEntry.md)                 | A GeoRaster grayscale entry, which contains two components: cellvalue and gray.                                                                                                                                                                                |
  | [GeorHistogram](GeorHistogram.md)                           | GeorHistogram class is combined with class GeorHistogramEntry to represent a GeoRaster histogram, which contains an array of GeorHistogramEntry instances, and each GeorHistogramEntry contains a pair of cell value and count value.                          |
  | [GeorHistogramEntry](GeorHistogramEntry.md)                 | A GeoRaster grayscale entry, which contains two components: value and count.                                                                                                                                                                                   |
  | [GeorSpatialReference](GeorSpatialReference.md)             |                                                                                                                                                                                                                                                                |
  | [JGeoRaster](JGeoRaster.md)                                 | JGeoRaster is a Java class mapped to the Oracle Spatial GeoRaster SQL type MDSYS.SDO_GEORASTER, and it provides the capability to access, manipulate, and visualize the GeoRaster objects stored in an Oracle Spatial database.                                |
  | [JGeoRasterMeta](JGeoRasterMeta.md)                         | The GeoRaster Java library defines a full set of Java classes to store and represent all metadata of a GeoRaster object.                                                                                                                                       |
  | [JGeoRasterVM](JGeoRasterVM.md)                             | JGeoRasterVM supports the definition of a GeoRaster virtual mosaic for the purpose of displaying a collection of images as a single one without storing the resulting image and supporting most of the same visualization options as if it was a single image. |
  | [JRaster](JRaster.md)                                       | JRaster is a Java class that deals with raster data stored on the server side.                                                                                                                                                                                 |
  | [LayerInfo](LayerInfo.md)                                   | LayerInfo is a Java class mapped to the XML element LayerInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                                        |
  | [ObjectInfo](ObjectInfo.md)                                 | ObjectInfo is a Java class mapped to the XML element ObjectInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                                      |
  | [RasterInfo](RasterInfo.md)                                 | RasterInfo is a Java class mapped to the XML element RasterInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                                      |
  | [SpatialReferenceInfo](SpatialReferenceInfo.md)             | SpatialReferenceInfo is a Java class mapped to the XML element SpatialReferenceInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                  |
  | [SubLayerInfo](SubLayerInfo.md)                             | SubLayerInfo is a Java class mapped to the XML element subLayer or objectLayer in the Oracle Spatial GeoRaster metadata.                                                                                                                                       |
  | [TemporalReferenceInfo](TemporalReferenceInfo.md)           | TemporalReferenceInfo is a Java class mapped to the XML element TemporalReferenceInfo in the Oracle Spatial GeoRaster metadata.                                                                                                                                |

- **Exception Summary**

  | Exception                                   | Description                                                                                                                                         |
  |---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
  | [GeoRasterException](GeoRasterException.md) | The class GeoRasterException is a subclass of Exception, and it indicates conditions related to JGeoRaster that an application might want to catch. |

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

- [Prev Package](../geometry/package-summary.md)
- [Next Package](image/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
