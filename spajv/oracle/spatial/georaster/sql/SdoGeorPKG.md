Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SdoGeorIpPKG.md)
- [Next Class](SdoGeorPKG.SdoGeorGCP.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.georaster.sql

## Class SdoGeorPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorPKG
      extends java.lang.Object

  SdoGeorPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorPKG
         SdoGeorPKG  pkg=new SdoGeorPKG(connection);
         //reading a GeoRaster object from database based on a query
         Statement stmt = connection.createStatement();
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         rs.next();
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster = new SdoGeoRaster(geor);
         //change cell value of the GeoRaster object
         pkg.changeCellValue(sdoGeoRaster,10,10,"1",10.0,null);
         //submit change
         connection.commit();

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                             |
    |-------------------|-----------------------------------------------------------------------------------|
    | `class `          | [`SdoGeorPKG.SdoGeorGCP`](SdoGeorPKG.SdoGeorGCP.md)<br>Deprecated.                |
    | `class `          | [`SdoGeorPKG.SdoGeorGCPRefType`](SdoGeorPKG.SdoGeorGCPRefType.md)<br>Deprecated.  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `long`            | `offset`              |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                               |
    |-----------------------------------------------------------------------------------------------------------|
    | `SdoGeorPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |--------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                     | `affineTransform``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] translation, double[] scales, double[] rotatePoint, java.lang.Double rotateAngle, double[] shear, java.lang.Integer reflection, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, double[] bgValues)`<br>Apply affine geometric trasnformation on GeoRaster Objects                                                                                                                                                                                                                                                                                                          |
    | `void`                                     | `affineTransform``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] translation, double[] scales, double[] rotatePoint, java.lang.Double rotateAngle, double[] shear, java.lang.Integer reflection, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelParam)`<br>Apply affine geometric trasnformation on GeoRaster Objects                                                                                                                                                                                                                                                                                                                                           |
    | `double`                                   | `calcCompressionRatio``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Computes the compression ratio of the GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                     | `changeCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.String layerNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                     | `changeCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                     | `changeCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long row, long column, java.lang.String bandNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cell in a specified point of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                     | `changeCellValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int[] rowNumbers, int[] colNumbers, int bandNumber, double[] newCellValues, double[] bgValues)`<br>Changes the value of raster cells specified by row/column arrays or by a multipoint geometry to new values.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                     | `changeCellValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, int layerNumber, double[] newCellValues, double[] bgValues)`<br>Changes the value of raster cells specified by row/column arrays or by a multipoint geometry to new values.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                     | `changeFormatCopy``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Makes a copy of an existing GeoRaster object using a different storage format (for example, changing the blocking, cell depth, or interleaving).                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                     | `compressJP2``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String compressParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster)`<br>Compresses the image in a GeoRaster object using JPEG 2000 compression.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                     | `copy``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, `[`SdoGeoRaster`](SdoGeoRaster.md)` target)`<br>Makes a copy of an existing GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                     | `createTemplate``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int rasterType, java.lang.String rasterSpec, java.lang.String maskLayers, java.lang.String initRDTEntry)`<br>Populates a GeoRaster object with metadata of a general pattern, and optionally inserts entries with empty raster blocks into its raster data table.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                     | `decompressJP2``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, double[] cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster)`<br>Decompress the JPEG 2000 compressed GeoRaster image into a GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                     | `decompressJP2``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String bandNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster)`<br>Decompress the JPEG 2000 compressed GeoRaster image into a GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `deletePyramid``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Deletes the pyramid data of a GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `java.math.BigDecimal[]`                   | `evaluateDouble``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int rowNumber, int colNumber, java.lang.String bands, java.lang.String interpolationMethod)`<br>Evaluates a direct location using a specified interpolation method, and returns the raster values for the specified bands for that location.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.math.BigDecimal[]`                   | `evaluateDouble``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, java.lang.String layers, java.lang.String interpolationMethod)`<br>Evaluates a direct location using a specified interpolation method, and returns the raster values for the specified layers for that location.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `java.math.BigDecimal[]`                   | `evaluateDoubles``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int[] rowNumbers, int[] colNumbers, int bandNumber, java.lang.String interpolationMethod)`<br>Evaluates multiple locations using a specified interpolation method, and returns the raster values (double precision numbers) for the specified band or layer for those locations.                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.math.BigDecimal[]`                   | `evaluateDoubles``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, int layerNumber, java.lang.String interpolationMethod)`<br>Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.                                                                                                                                                                                                                                                  |
    | `double`                                   | `generateAreaWeightedMean``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.Integer bandNumber, boolean nodata)`<br>Computes the area weighted mean value on a specified band of the input GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `generateBitmapPyramid``(`[`SdoGeoRaster`](SdoGeoRaster.md)` src_geor, `[`SdoGeoRaster`](SdoGeoRaster.md)` tmp_geor, `[`SdoGeoRaster`](SdoGeoRaster.md)` target_geor, java.lang.String pyramidParams, double[] bgValues, int parallelParam)`<br>Generates pyramid data for a bitmap GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                     | `generateBlockMBR``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Computes the minimum bounding rectangle (MBR) for each block in a GeoRaster object, and sets the blockMBR attribute for each raster block in the raster data table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `generatePyramid``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, java.lang.String pyramidParams, double[] bgValues)`<br>Generates pyramid data, which is stored together with the original data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`JGeometry`](../../geometry/JGeometry.md) | `generateSpatialExtent``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, java.lang.Double height)`<br>Generates a Spatial geometry that contains the spatial extent (footprint) of the GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.math.BigDecimal[]`                   | `generateSpatialResolutions``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster)`<br>Sets the generated spatial resolutions in the metadata for the GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `java.math.BigDecimal[]`                   | `generateSpatialResolutions``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, long pyramidLevel, java.lang.Integer SRID, java.lang.String resolutionUnit)`<br>Generates and returns the spatial resolutions based on the georeferencing information in the metadata for the GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                     | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, boolean histogram, java.lang.String layerNumbers, boolean useBin, double[] binFunction, boolean nodata)`<br>Computes and sets statistical data associated with one or more layers.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int samplingFactor, long[] samplingWindow, boolean histogram, java.lang.String layerNumbers, boolean useBin, double[] binFunction, boolean nodata)`<br>Computes and sets statistical data associated with one or more layers.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `java.math.BigDecimal[]`                   | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers and pyramid levels.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `java.math.BigDecimal[]`                   | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers and pyramid levels.                                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.math.BigDecimal[]`                   | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers and pyramid levels.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.math.BigDecimal[]`                   | `generateStatistics``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers and pyramid levels.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `double`                                   | `generateStatisticsMax``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value.                                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                   | `generateStatisticsMax``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value.                                                                                                                                                                                                                                                                                                                                             |
    | `double`                                   | `generateStatisticsMax``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `double`                                   | `generateStatisticsMax``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `double`                                   | `generateStatisticsMean``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value.                                                                                                                                                                                                                                                                                                                                                                   |
    | `double`                                   | `generateStatisticsMean``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value.                                                                                                                                                                                                                                                                                                                                               |
    | `double`                                   | `generateStatisticsMean``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `double`                                   | `generateStatisticsMean``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `double`                                   | `generateStatisticsMedian``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value.                                                                                                                                                                                                                                                                                                                                                               |
    | `double`                                   | `generateStatisticsMedian``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value.                                                                                                                                                                                                                                                                                                                                           |
    | `double`                                   | `generateStatisticsMedian``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value.                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `double`                                   | `generateStatisticsMedian``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `double`                                   | `generateStatisticsMin``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value.                                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                   | `generateStatisticsMin``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value.                                                                                                                                                                                                                                                                                                                                             |
    | `double`                                   | `generateStatisticsMin``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `double`                                   | `generateStatisticsMin``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `double`                                   | `generateStatisticsMode``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value.                                                                                                                                                                                                                                                                                                                                                                   |
    | `double`                                   | `generateStatisticsMode``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value.                                                                                                                                                                                                                                                                                                                                               |
    | `double`                                   | `generateStatisticsMode``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `double`                                   | `generateStatisticsMode``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `double`                                   | `generateStatisticsSTD``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value.                                                                                                                                                                                                                                                                                                                                                                     |
    | `double`                                   | `generateStatisticsSTD``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, `[`JGeometry`](../../geometry/JGeometry.md)` samplingWindow, java.lang.String bandNumbers, boolean nodata, boolean polygonClip, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value.                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                   | `generateStatisticsSTD``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value.                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `double`                                   | `generateStatisticsSTD``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, long pyramidLevel, int samplingFactor, long[] samplingWindow, java.lang.String bandNumbers, boolean nodata, int parallelDegree)`<br>Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value.                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `java.math.BigDecimal[]`                   | `georeference``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`GCPGeoreference`](../GCPGeoreference.md)` gcpGeoreference, java.lang.Boolean storeGCP, java.lang.Integer srid, java.lang.Integer modelCoordinateLocation, java.lang.String setResolution)`<br>returns the solution of any one of the supported geometric models using ground control points (GCPs) that are specified in the parameters.                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `georeference``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int srid, int modelCoordinateLocation, double[] xCoefficients, double[] yCoefficients)`<br>Georeferences a GeoRaster object using specified cell-to-model transformation coefficients.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.math.BigDecimal[]`                   | `georeference``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`SdoGeorPKG.SdoGeorGCPRefType`](SdoGeorPKG.SdoGeorGCPRefType.md)` gcpGeorefModel, java.lang.Boolean storeGCP, java.lang.Integer srid, java.lang.Integer modelCoordinateLocation, java.lang.String setResolution)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `java.math.BigDecimal[]`                   | `georeference``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, java.lang.String FFMethodType, java.lang.Integer srid, java.lang.Integer modelCoordinateLocation, java.lang.String setResolution)`<br>returns the solution of any one of the supported geometric models using ground control points (GCPs) that are stored in the database.                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.math.BigDecimal[]`                   | `georeference``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, java.lang.String FFMethodType, int nGCP, `[`SdoGeorPKG.SdoGeorGCP`](SdoGeorPKG.SdoGeorGCP.md)`[] gcps, java.lang.Boolean storeGCP, java.lang.Integer srid, java.lang.Integer modelCoordinateLocation, java.lang.String setResolution)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                     | `getBitmapMask``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, int layer, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target)`<br>Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `double`                                   | `getBitmapMaskValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int rowNumber, int colNumber, int bandNumber)`<br>Gets the value of a single cell from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                   | `getBitmapMaskValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, int pyramidLevel, int layerNumber)`<br>Gets the value of a single cell from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.math.BigDecimal[]`                   | `getBitmapMaskValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int layerNumber, int pyramidLevel, int[] rowNumbers, int[] colNumbers)`<br>Gets the values of multiple cells from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.math.BigDecimal[]`                   | `getBitmapMaskValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int layerNumber, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom)`<br>Gets the values of multiple cells from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `double`                                   | `getCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int rowNumber, int colNumber, int bandNumber)`<br>Returns the value of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its logical layer number.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `java.math.BigDecimal[]`                   | `getCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int rowNumber, int colNumber, java.lang.String bands)`<br>Returns the values of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band numbers in its cell coordinate system.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.math.BigDecimal[]`                   | `getCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, java.lang.String layers)`<br>Returns the values of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer numbers.                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                   | `getCellValue``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, int pyramidLevel, int layerNumber)`<br>Returns the value of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer number.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `java.math.BigDecimal[]`                   | `getCellValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, int[] rowNumbers, int[] colNumbers, int bandNumber)`<br>Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.                                                                                                                                                                                                                                                                                                            |
    | `java.math.BigDecimal[]`                   | `getCellValues``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, int layerNumber)`<br>Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.                                                                                                                                                                                                                                                                                          |
    | `java.sql.Connection`                      | `getConnection``()`<br>Returns a connection which points to target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                      | `getGeoreferenceType``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Returns a number that indicates the georeference type for a GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.sql.Blob`                            | `getRasterBlockLocator``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, long pyramidLevel, long bandBlockNumber, long rowBlockNumber, long columnBlockNumber, boolean isBitmapMask, boolean lock_for_write)`<br>returns the LOB locator of a raster block by specifying the pyramidLevel, bandBlockNumber, rowBlockNumber, and columnBlockNumber parameters.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.sql.Blob`                            | `getRasterBlockLocator2``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, long pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` ptGeom, long layerNumber, boolean isBitmapMask, boolean lock_for_write)`<br>return the LOB locator of a raster block that contains a specific single cell and the offset of the cell within the raster block.                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.sql.Blob`                            | `getRasterBlockLocator2``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, long pyramidLevel, long rowNumber, long columnNumber, long bandNumber, boolean isBitmapMask, boolean lock_for_write)`<br>return the LOB locator of a raster block that contains a specific single cell and the offset of the cell within the raster block.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `double[]`                                 | `getRasterRange``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, int layerNumber)`<br>Gets the minimum and maximum cell values of a specified layer of a GeoRaster object or of the GeoRaster object itself (the object layer).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                     | `mask``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String bandNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` mask, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double zeroMapping, double oneMapping, double[] bgValues)`<br>Applies a mask to specified layers of an existing (input) GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                     | `mergeLayers``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, java.lang.String sourceLayerNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Merges the layers of two GeoRaster objects, either by appending source layers to a target GeoRaster object (first format) or by performing a union operation.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                     | `mergeLayers``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source1, java.lang.String source1LayerNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` source2, java.lang.String source2LayerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Merges the layers of two GeoRaster objects, either by appending source layers to a target GeoRaster object (first format) or by performing a union operation.                                                                                                                                                                                                                                                                                         |
    | `void`                                     | `mosaic``(java.lang.String georasterTableName, java.lang.String georasterColumnName, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, java.lang.String storageParam, double[] bgValues)`<br>Mosaics GeoRaster objects into one GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                     | `rectify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.lang.String elevationParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` dem, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, java.lang.String resampleParam, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, double[] bgValues)`<br>Perform rectification on all or part of a georeferenced GeoRaster object. |
    | `void`                                     | `rectify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.lang.String elevationParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` dem, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, java.lang.String resampleParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelDegree)`<br>Perform rectification on all or part of a georeferenced GeoRaster object.                                 |
    | `java.sql.Blob`                            | `reproject``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, int pyramidLevel, double[] cropArea, java.lang.String bandNumbers, java.lang.String resampleParam, java.lang.String storageParam, int outSRID, `[`JGeometry`](../../geometry/JGeometry.md)` outArea, double[] outWindow, double[] bgValues)`<br>Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `reproject``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, int pyramidLevel, double[] cropArea, java.lang.String bandNumbers, java.lang.String resampleParam, java.lang.String storageParam, int outSRID, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoraster, double[] bgValues)`<br>Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).                                                                                                                                                                                                                                                                                                           |
    | `void`                                     | `reproject``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String resampleParam, java.lang.String storageParam, int outSRID, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)` outArea, double[] outWindow, double[] bgValues)`<br>Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).                                                                                                                                                                                                                  |
    | `void`                                     | `reproject``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String resampleParam, java.lang.String storageParam, int outSRID, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoraster, double[] bgValues)`<br>Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).                                                                                                                                                                                                                                                                      |
    | `void`                                     | `reproject``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String resampleParam, java.lang.String storageParam, int outSRID, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoraster, double[] bgValues)`<br>Reprojects a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                     | `scaleCopy``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, java.lang.String scaleParam, int pyramidLevel, java.lang.String resampleParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Scales a GeoRaster object by enlarging or reducing the image along row and column dimensions, and puts the result into a new object that reflects the scaling.                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `scaleCopy``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, java.lang.String scaleParam, java.lang.String resampleParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Scales a GeoRaster object by enlarging or reducing the image along row and column dimensions, and puts the result into a new object that reflects the scaling.                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                     | `setBitmapMask``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, int layer, `[`SdoGeoRaster`](SdoGeoRaster.md)` mask, java.lang.Integer NODATAMask)`<br>Attaches a bitmap mask to a GeoRaster object, or replaces or removes the current bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                     | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                     | `setModelCoordLocation``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, java.lang.String modelCoordLoc)`<br>Sets the model coordinate location value for a GeoRaster object, or deletes the current model coordinate location value (if any) if the modelCoordLoc parameter is specified as null.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, double[] cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, int pyramid, double[] cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, int pyramid, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, int pyramid, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues, java.lang.String polygonClip)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                     | `subset``(`[`SdoGeoRaster`](SdoGeoRaster.md)` source, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` target, double[] bgValues, java.lang.String polygonClip)`<br>Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `updateRaster``(`[`SdoGeoRaster`](SdoGeoRaster.md)` target, int targetPyramidLevel, java.lang.String targetLayerNumbers, `[`JGeometry`](../../geometry/JGeometry.md)` targetArea, `[`SdoGeoRaster`](SdoGeoRaster.md)` source, int sourcePyramidLevel, java.lang.String sourceLayerNumbers, boolean updateUpperPyramids, double[] bgValues)`<br>Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.                                                                                                                                                                                                              |
    | `void`                                     | `updateRaster``(`[`SdoGeoRaster`](SdoGeoRaster.md)` target, int targetPyramidLevel, java.lang.String targetLayerNumbers, long[] targetArea, `[`SdoGeoRaster`](SdoGeoRaster.md)` source, int sourcePyramidLevel, java.lang.String sourceLayerNumbers, boolean updateUpperPyramids, double[] bgValues)`<br>Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.                                                                                                                                                                                                                                                    |
    | `boolean`                                  | `validateBlockMBR``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Validates the blockMBR attribute of each block of a GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                  | `validateGeoRaster``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Validates a GeoRaster object, checking its raster data and metadata.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                     | `warp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`GeorSpatialReference`](../GeorSpatialReference.md)` outSRS, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, double[] dimensionSize, java.lang.String layerNumbers, java.lang.String elevationParam, java.lang.String resampleParam, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, double[] bgValues)`<br>Perform geometric transformation on the input GeoRaster object to produce an output GeoRaster object with the specified output spatial reference system.                                                                                  |
    | `void`                                     | `warp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`GeorSpatialReference`](../GeorSpatialReference.md)` outSRS, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, double[] dimensionSize, java.lang.String layerNumbers, java.lang.String elevationParam, java.lang.String resampleParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelParam)`<br>Perform geometric transformation on the input GeoRaster object to produce an output GeoRaster object with the specified output spatial reference system.                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### offset

          public long offset

  <!-- -->

  - ### Constructor Detail

    - #### SdoGeorPKG

          public SdoGeorPKG(java.sql.Connection conn)

      Constructs an `SdoGeorPKG` object using the given connection.
      Parameters:
      `conn` - a JDBC connection.

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public void setConnection(java.sql.Connection conn)

      Sets the connection which points to the target database.
      Parameters:
      `conn` - a JDBC connection

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns a connection which points to target database.
      Returns:
      a connection which points to target database.

    <!-- -->

    - #### generateStatisticsMax

          public double generateStatisticsMax(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMax

          public double generateStatisticsMax(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMax

          public double generateStatisticsMax(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMax

          public double generateStatisticsMax(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMin

          public double generateStatisticsMin(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMin

          public double generateStatisticsMin(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMin

          public double generateStatisticsMin(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMin

          public double generateStatisticsMin(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMean

          public double generateStatisticsMean(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               long[] samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMean

          public double generateStatisticsMean(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               long[] samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               int parallelDegree)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMean

          public double generateStatisticsMean(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               JGeometry samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               boolean polygonClip)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMean

          public double generateStatisticsMean(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               JGeometry samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               boolean polygonClip,
                                               int parallelDegree)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMedian

          public double generateStatisticsMedian(SdoGeoRaster georaster,
                                                 long pyramidLevel,
                                                 int samplingFactor,
                                                 long[] samplingWindow,
                                                 java.lang.String bandNumbers,
                                                 boolean nodata)
                                          throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMedian

          public double generateStatisticsMedian(SdoGeoRaster georaster,
                                                 long pyramidLevel,
                                                 int samplingFactor,
                                                 long[] samplingWindow,
                                                 java.lang.String bandNumbers,
                                                 boolean nodata,
                                                 int parallelDegree)
                                          throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMedian

          public double generateStatisticsMedian(SdoGeoRaster georaster,
                                                 long pyramidLevel,
                                                 int samplingFactor,
                                                 JGeometry samplingWindow,
                                                 java.lang.String bandNumbers,
                                                 boolean nodata,
                                                 boolean polygonClip)
                                          throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMedian

          public double generateStatisticsMedian(SdoGeoRaster georaster,
                                                 long pyramidLevel,
                                                 int samplingFactor,
                                                 JGeometry samplingWindow,
                                                 java.lang.String bandNumbers,
                                                 boolean nodata,
                                                 boolean polygonClip,
                                                 int parallelDegree)
                                          throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMode

          public double generateStatisticsMode(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               long[] samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMode

          public double generateStatisticsMode(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               long[] samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               int parallelDegree)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMode

          public double generateStatisticsMode(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               JGeometry samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               boolean polygonClip)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsMode

          public double generateStatisticsMode(SdoGeoRaster georaster,
                                               long pyramidLevel,
                                               int samplingFactor,
                                               JGeometry samplingWindow,
                                               java.lang.String bandNumbers,
                                               boolean nodata,
                                               boolean polygonClip,
                                               int parallelDegree)
                                        throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsSTD

          public double generateStatisticsSTD(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsSTD

          public double generateStatisticsSTD(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              long[] samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsSTD

          public double generateStatisticsSTD(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatisticsSTD

          public double generateStatisticsSTD(SdoGeoRaster georaster,
                                              long pyramidLevel,
                                              int samplingFactor,
                                              JGeometry samplingWindow,
                                              java.lang.String bandNumbers,
                                              boolean nodata,
                                              boolean polygonClip,
                                              int parallelDegree)
                                       throws java.lang.Exception

      Computes statistical data associated with one or more layers on a specified pyramid level, and returns the STD value. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - A rectangular window or a polygon geometry object from which to generate statistics. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space; and if the polygonClip value is FALSE, the MBR of the geometry object is used as the window, but if the polygonClip value is TRUE, the polygon geometry object (if valid) is used as the window.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the value FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public java.math.BigDecimal[] generateStatistics(SdoGeoRaster georaster,
                                                           long pyramidLevel,
                                                           int samplingFactor,
                                                           long[] samplingWindow,
                                                           java.lang.String bandNumbers,
                                                           boolean nodata)
                                                    throws java.lang.Exception

      Computes statistical data associated with one or more layers and pyramid levels. This method does not set any GeoRaster object metadata, and it calculates statistics for a single layer or for the aggregation of specified layers. These formats return an SDO_NUMBER_ARRAY object where the six numbers reflect the aggregated minimum, maximum, mean, median, mode, and standard deviation values.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - sampling window: a rectangular window for which to set statistics, specified as a numeric array with the lower-left and upper-right coordinates. The window must be inside the extent in cell space. A null value for this parameter indicates the entire image.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public java.math.BigDecimal[] generateStatistics(SdoGeoRaster georaster,
                                                           long pyramidLevel,
                                                           int samplingFactor,
                                                           long[] samplingWindow,
                                                           java.lang.String bandNumbers,
                                                           boolean nodata,
                                                           int parallelDegree)
                                                    throws java.lang.Exception

      Computes statistical data associated with one or more layers and pyramid levels. This method does not set any GeoRaster object metadata, and it calculates statistics for a single layer or for the aggregation of specified layers. These formats return an SDO_NUMBER_ARRAY object where the six numbers reflect the aggregated minimum, maximum, mean, median, mode, and standard deviation values.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - sampling window: a rectangular window for which to set statistics, specified as a numeric array with the lower-left and upper-right coordinates. The window must be inside the extent in cell space. A null value for this parameter indicates the entire image.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public java.math.BigDecimal[] generateStatistics(SdoGeoRaster georaster,
                                                           long pyramidLevel,
                                                           int samplingFactor,
                                                           JGeometry samplingWindow,
                                                           java.lang.String bandNumbers,
                                                           boolean nodata,
                                                           boolean polygonClip)
                                                    throws java.lang.Exception

      Computes statistical data associated with one or more layers and pyramid levels. This method does not set any GeoRaster object metadata, and it calculates statistics for a single layer or for the aggregation of specified layers. These formats return an SDO_NUMBER_ARRAY object where the six numbers reflect the aggregated minimum, maximum, mean, median, mode, and standard deviation values.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - Sampling window: a rectangular window for which to set statistics, specified as an SDO_GEOMETRY object. The default for this parameter is the entire image.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public java.math.BigDecimal[] generateStatistics(SdoGeoRaster georaster,
                                                           long pyramidLevel,
                                                           int samplingFactor,
                                                           JGeometry samplingWindow,
                                                           java.lang.String bandNumbers,
                                                           boolean nodata,
                                                           boolean polygonClip,
                                                           int parallelDegree)
                                                    throws java.lang.Exception

      Computes statistical data associated with one or more layers and pyramid levels. This method does not set any GeoRaster object metadata, and it calculates statistics for a single layer or for the aggregation of specified layers. These formats return an SDO_NUMBER_ARRAY object where the six numbers reflect the aggregated minimum, maximum, mean, median, mode, and standard deviation values.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - Pyramid level on which to perform the operation.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - Sampling window: a rectangular window for which to set statistics, specified as an SDO_GEOMETRY object. The default for this parameter is the entire image.

      `bandNumbers` - Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '0,1,3-5,7' specifies layers 1, 2, 4, 5, 6, and 8. If bandNumbers is null, all bands are used in computing the statistics.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      `polygonClip` - The value TRUE causes the samplingWindow geometry object to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the samplingWindow geometry object to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster").\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rectify

          public void rectify(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              java.lang.String elevationParam,
                              SdoGeoRaster dem,
                              java.lang.Integer outSRID,
                              java.lang.Integer outModelCoordLoc,
                              JGeometry cropArea,
                              boolean polygonClip,
                              java.lang.String layerNumbers,
                              double[] outResolutions,
                              java.lang.String resolutionUnit,
                              JGeometry referencePoint,
                              java.lang.String resampleParam,
                              java.lang.String storageParam,
                              SdoGeoRaster outGeoRaster,
                              double[] bgValues,
                              int parallelDegree)
                       throws java.lang.Exception

      Perform rectification on all or part of a georeferenced GeoRaster object. The resulting object can be a new GeoRaster object (for persistent storage) or a BLOB (for temporary use). If the input model coordinate system (SRID) is three-dimensional, the average elevation or a Digital Elevation Model (DEM) can be used to perform the orthorectification.
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation. It must be georeferenced.

      `pyramidLevel` - Pyramid level of the source GeoRaster object for the operation. For BLOB output, this parameter is required. For SDO_GEORASTER output, if this parameter is null and the storageParam pyramid value is FALSE, only the pyramid level 0 is rectified and the output will have only level 0. If this parameter is null and the storageParam pyramid value is TRUE, all the pyramid levels from the input are rectified. If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

      `elevationParam` - A string containing one or more of the elevation parameters average (average surface height), scale (scale value applied to all DEM values), and offset (offset applied to all DEM values), where the new value is (value + offset) \* scale. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, 'average=800 scale=3.2808399 offset=10'). If this parameter is null, 0 is assumed for average and offset, and 1 is used for scale. Any scale and offset values are ignored if DEM is not specified. The use of the elevationParam parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

      `DEM` - GeoRaster object with a digital elevation model (DEM); used to perform orthorectification, as explained in the Usage Notes. Must have the same SRID as outGeoRaster. The DEM area should cover the entire outGeoRaster area, or the cropArea if used. The elevation data is assumed to be on the first layer of the DEM GeoRaster object. If this parameter is null, the elevationParam value is used. For best results, the resolution of the DEM GeoRaster object should be close to the resolution of the input GeoRaster object. The use of the DEM parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified in the elevationParam parameter even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `cropArea` - Crop area definition. If null, no cropping is performed, and polygonClip is ignored. If polygonClip is FALSE, the MBR of the cropArea is used to crop the output image. If polygonClip is TRUE, the geometry of the cropArea is used to crop the output image. Areas outside the crop area are filled with the background value

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the mosaicked data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      `layerNumbers` - A string identifying the logical layer numbers for the rectification and the output to outGeoRaster. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `outResolutions` - An array of numeric values, one for each spatial dimension. Each value indicates the number of units of measure associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measure for the ground data is meters, each pixel represents an area of 10 meters by 10 meters. If null, the default is the resolution of the source data at the specified pyramid level.

      `resolutionUnit` - The unit of the outResolutions parameter. If resolutionUnit is different from the outGeoRaster SRID unit, an appropriate conversion is computed (the value of the output resolution is calculated by converting the outResolutions value in resolutionUnit to the unit of the output SRID) . If resolutionUnit is null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `referencePoint` - A point of type SDO_GEOMETRY indicating a reference to where the outGeoRaster object should be aligned so that the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels.

      `resampleParam` - A comma-separated quoted string of keyword=value pairs for specifying resampling parameters. See the Usage Notes for more information.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1.

      `outGeoRaster` - GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Section 1.4.3.) Cannot be the same GeoRaster object as inGeoRaster

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rectify

          public void rectify(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              java.lang.String elevationParam,
                              SdoGeoRaster dem,
                              java.lang.Integer outSRID,
                              java.lang.Integer outModelCoordLoc,
                              JGeometry cropArea,
                              boolean polygonClip,
                              java.lang.String layerNumbers,
                              double[] outResolutions,
                              java.lang.String resolutionUnit,
                              JGeometry referencePoint,
                              java.lang.String resampleParam,
                              java.lang.String storageParam,
                              java.sql.Blob[] rasterBlob,
                              JGeometry[] outArea,
                              long[] outWindow,
                              double[] bgValues)
                       throws java.lang.Exception

      Perform rectification on all or part of a georeferenced GeoRaster object. The resulting object can be a new GeoRaster object (for persistent storage) or a BLOB (for temporary use). If the input model coordinate system (SRID) is three-dimensional, the average elevation or a Digital Elevation Model (DEM) can be used to perform the orthorectification.
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation. It must be georeferenced.

      `pyramidLevel` - Pyramid level of the source GeoRaster object for the operation. For BLOB output, this parameter is required. For SDO_GEORASTER output, if this parameter is null and the storageParam pyramid value is FALSE, only the pyramid level 0 is rectified and the output will have only level 0. If this parameter is null and the storageParam pyramid value is TRUE, all the pyramid levels from the input are rectified. If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

      `elevationParam` - A string containing one or more of the elevation parameters average (average surface height), scale (scale value applied to all DEM values), and offset (offset applied to all DEM values), where the new value is (value + offset) \* scale. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, 'average=800 scale=3.2808399 offset=10'). If this parameter is null, 0 is assumed for average and offset, and 1 is used for scale. Any scale and offset values are ignored if DEM is not specified. The use of the elevationParam parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

      `DEM` - GeoRaster object with a digital elevation model (DEM); used to perform orthorectification, as explained in the Usage Notes. Must have the same SRID as outGeoRaster. The DEM area should cover the entire outGeoRaster area, or the cropArea if used. The elevation data is assumed to be on the first layer of the DEM GeoRaster object. If this parameter is null, the elevationParam value is used. For best results, the resolution of the DEM GeoRaster object should be close to the resolution of the input GeoRaster object. The use of the DEM parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified in the elevationParam parameter even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `cropArea` - Crop area definition. If null, no cropping is performed, and polygonClip is ignored. If polygonClip is FALSE, the MBR of the cropArea is used to crop the output image. If polygonClip is TRUE, the geometry of the cropArea is used to crop the output image. Areas outside the crop area are filled with the background value

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the mosaicked data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      `layerNumbers` - A string identifying the logical layer numbers for the rectification and the output to outGeoRaster. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `outResolutions` - An array of numeric values, one for each spatial dimension. Each value indicates the number of units of measure associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measure for the ground data is meters, each pixel represents an area of 10 meters by 10 meters. If null, the default is the resolution of the source data at the specified pyramid level.

      `resolutionUnit` - The unit of the outResolutions parameter. If resolutionUnit is different from the outGeoRaster SRID unit, an appropriate conversion is computed (the value of the output resolution is calculated by converting the outResolutions value in resolutionUnit to the unit of the output SRID) . If resolutionUnit is null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `referencePoint` - A point of type SDO_GEOMETRY indicating a reference to where the outGeoRaster object should be aligned so that the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels.

      `resampleParam` - A comma-separated quoted string of keyword=value pairs for specifying resampling parameters. See the Usage Notes for more information.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1.

      `rasterBlob` - BLOB array to hold the output reflecting the rectification. It can't be null.

      `outArea` - An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mask

          public void mask(SdoGeoRaster inGeoRaster,
                           java.lang.String bandNumbers,
                           SdoGeoRaster mask,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           double zeroMapping,
                           double oneMapping,
                           double[] bgValues)
                    throws java.lang.Exception

      Applies a mask to specified layers of an existing (input) GeoRaster object. The mask GeoRaster object and the input GeoRaster object can have the same storage format or different storage formats, and you can specify storage format options for the output GeoRaster object (for example, to change the blocking, cell depth, or interleaving).
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object on which the mask operation is to be performed to create the new object.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for the second, third, and forth layers).

      `mask` - The SDO_GEORASTER object to be used as a mask on the input GeoRaster object for generating the output GeoRaster object. If this parameter is specified as null, then available attached masks of the input GeoRaster object are applied to the specified layers.

      `storageParam` - a string specifying storage parameters

      `outGeoRaster` - The new SDO_GEORASTER object that reflects the results of the mask operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Section 1.4.3.) Cannot be the same GeoRaster object as inGeoRaster. If the output GeoRaster object has any existing raster data, it is deleted before the mask operation is performed. The output GeoRaster object is overwritten as a result of this function.

      `zeroMapping` - Value used for mask cell value 0 (zero). The default value is 0.

      `oneMapping` - Value used for mask cell value 1 (one). The default value is 1.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all layers) or the band dimension size (a different filling value for each layer, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first layer with 1, the second layer with 5, and the third layer with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterRange

          public double[] getRasterRange(SdoGeoRaster geoRaster,
                                         int layerNumber)
                                  throws java.lang.Exception

      Gets the minimum and maximum cell values of a specified layer of a GeoRaster object or of the GeoRaster object itself (the object layer).
      Parameters:
      `geoRaster` - source GeoRaster objects.

      `layerNumber` - Number of the layer for which to return the range of cell values. A value of 0 (zero, the default) indicates the object layer. (As mentioned in Section 1.5, the logical layer number is the physical band number plus 1.)

      Returns:
      a double array with two values: the minimum and maximum cell values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterBlockLocator

          public java.sql.Blob getRasterBlockLocator(SdoGeoRaster geoRaster,
                                                     long pyramidLevel,
                                                     long bandBlockNumber,
                                                     long rowBlockNumber,
                                                     long columnBlockNumber,
                                                     boolean isBitmapMask,
                                                     boolean lock_for_write)
                                              throws java.lang.Exception

      returns the LOB locator of a raster block by specifying the pyramidLevel, bandBlockNumber, rowBlockNumber, and columnBlockNumber parameters.
      Parameters:
      `geoRaster` - GeoRaster object.

      `pyramidLevel` - Pyramid level of the block.

      `bandBlockNumber` - Band number of the block.

      `rowBlockNumber` - Row number of the block.

      `columnBlockNumber` - Column number of the block.

      `isBitmapMask` - A boolean value to specifies that a bitmap mask block will be accessed or a regular raster block will be accessed.

      `lock_for_write` - A boolean value TRUE locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the boolean value FALSE does not lock the row in the raster data table. The default bgValues are zero (0).

      Returns:
      a BLOB (binary large object) for specified raster block.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterBlockLocator2

          public java.sql.Blob getRasterBlockLocator2(SdoGeoRaster geoRaster,
                                                      long pyramidLevel,
                                                      long rowNumber,
                                                      long columnNumber,
                                                      long bandNumber,
                                                      boolean isBitmapMask,
                                                      boolean lock_for_write)
                                               throws java.lang.Exception

      return the LOB locator of a raster block that contains a specific single cell and the offset of the cell within the raster block. The specific single cell is identified by the pyramidLevel, rowNumber, columnNumber, and bandNumber parameters or by a point geometry parameter (ptGeom) in either the cell coordinate space or the model coordinate space. After each call of this method, the member variable offset of this class is updated, and it will contain the offset (in bytes) of the cell inside the raster block that is located. If the raster block is compressed, it always refers to the offset of the cell in the decompressed version of the block.
      Parameters:
      `geoRaster` - GeoRaster object.

      `pyramidLevel` - Pyramid level of the block.

      `rowNumber` - Row number of the cell.

      `columnNumber` - Column number of the cell.

      `bandNumber` - Band number of the cell.

      `isBitmapMask` - A boolean value to specifies that a bitmap mask block will be accessed or a regular raster block will be accessed.

      `lock_for_write` - A boolean value TRUE locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the boolean value FALSE does not lock the row in the raster data table. The default bgValues are zero (0).

      Returns:
      a BLOB (binary large object) for specified raster block.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterBlockLocator2

          public java.sql.Blob getRasterBlockLocator2(SdoGeoRaster geoRaster,
                                                      long pyramidLevel,
                                                      JGeometry ptGeom,
                                                      long layerNumber,
                                                      boolean isBitmapMask,
                                                      boolean lock_for_write)
                                               throws java.lang.Exception

      return the LOB locator of a raster block that contains a specific single cell and the offset of the cell within the raster block. The specific single cell is identified by the pyramidLevel, rowNumber, columnNumber, and bandNumber parameters or by a point geometry parameter (ptGeom) in either the cell coordinate space or the model coordinate space. After each call of this method, the member variable offset of this class is updated, and it will contain the offset (in bytes) of the cell inside the raster block that is located. If the raster block is compressed, it always refers to the offset of the cell in the decompressed version of the block.
      Parameters:
      `geoRaster` - GeoRaster object.

      `pyramidLevel` - Pyramid level of the block.

      `ptGeom` - Point geometry that locates the cell.

      `layerNumber` - Layer number of the cell.

      `isBitmapMask` - A boolean value to specifies that a bitmap mask block will be accessed or a regular raster block will be accessed.

      `lock_for_write` - A boolean value TRUE locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the boolean value FALSE does not lock the row in the raster data table. The default bgValues are zero (0).

      Returns:
      a BLOB (binary large object) for specified raster block.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateSpatialResolutions

          public java.math.BigDecimal[] generateSpatialResolutions(SdoGeoRaster geoRaster,
                                                                   long pyramidLevel,
                                                                   java.lang.Integer SRID,
                                                                   java.lang.String resolutionUnit)
                                                            throws java.lang.Exception

      Generates and returns the spatial resolutions based on the georeferencing information in the metadata for the GeoRaster object. The metadata for the GeoRaster object is not updated.
      Parameters:
      `geoRaster` - GeoRaster object.

      `pyramidLevel` - Pyramid level of the returned resolution values.

      `SRID` - Coordinate system. Must be a value from the SRID column of the MDSYS.CS_SRS table. The srid value cannot be 0 (zero). If not specified, the default is the SRID associated with georaster.

      `resolutionUnit` - Unit of measurement: a quoted string with unit=. If not specified, the unit associated with SRID is used.

      Returns:
      the spatial resolutions based on the georeferencing information in the metadata for the GeoRaster object. The metadata for the GeoRaster object is not updated.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateSpatialResolutions

          public java.math.BigDecimal[] generateSpatialResolutions(SdoGeoRaster geoRaster)
                                                            throws java.lang.Exception

      Sets the generated spatial resolutions in the metadata for the GeoRaster object. The metadata for the GeoRaster object is updated. The GeoRaster object must be georeferenced in order to get the spatial resolution generated.
      Parameters:
      `geoRaster` - GeoRaster object.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeFormatCopy

          public void changeFormatCopy(SdoGeoRaster source,
                                       java.lang.String storageParam,
                                       SdoGeoRaster target,
                                       double[] bgValues)
                                throws java.lang.Exception

      Makes a copy of an existing GeoRaster object using a different storage format (for example, changing the blocking, cell depth, or interleaving).
      Parameters:
      `source` - source GeoRaster object

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### copy

          public void copy(SdoGeoRaster source,
                           SdoGeoRaster target)
                    throws java.lang.Exception

      Makes a copy of an existing GeoRaster object.
      Parameters:
      `source` - source GeoRaster object

      `target` - target GeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mergeLayers

          public void mergeLayers(SdoGeoRaster source,
                                  java.lang.String sourceLayerNumbers,
                                  SdoGeoRaster target,
                                  double[] bgValues)
                           throws java.lang.Exception

      Merges the layers of two GeoRaster objects, either by appending source layers to a target GeoRaster object (first format) or by performing a union operation.
      Parameters:
      `source` - source GeoRaster object

      `sourceLayerNumbers` - String specifying one or more layer numbers of layers in source GeoRaster object to be appended to target georaster object. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1, 3, 4, 5, and 7.

      `target` - target GeoRaster object

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mergeLayers

          public void mergeLayers(SdoGeoRaster source1,
                                  java.lang.String source1LayerNumbers,
                                  SdoGeoRaster source2,
                                  java.lang.String source2LayerNumbers,
                                  java.lang.String storageParam,
                                  SdoGeoRaster target,
                                  double[] bgValues)
                           throws java.lang.Exception

      Merges the layers of two GeoRaster objects, either by appending source layers to a target GeoRaster object (first format) or by performing a union operation.
      Parameters:
      `source1` - the first source GeoRaster object

      `source1LayerNumbers` - String specifying one or more layer numbers of layers in the first source GeoRaster object to be appended to target GeoRaster object. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1,3, 4, 5, and 7.

      `source2` - the second source GeoRaster object

      `source2LayerNumbers` - String specifying one or more layer numbers of layers in the second source GeoRaster object to be appended to the target GeoRaster object. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1,3, 4, 5, and 7.

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mosaic

          public void mosaic(java.lang.String georasterTableName,
                             java.lang.String georasterColumnName,
                             SdoGeoRaster target,
                             java.lang.String storageParam,
                             double[] bgValues)
                      throws java.lang.Exception

      Mosaics GeoRaster objects into one GeoRaster object.
      Parameters:
      `georasterTableName` - name of the table containing all source GeoRaster objects

      `georasterColumnName` - column of type SDO_GEORASTER in georasterTableName.

      `target` - target GeoRaster object to hold the result of the mosaic operation

      `storageParam` - a string specifying storage parameters

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### scaleCopy

          public void scaleCopy(SdoGeoRaster source,
                                java.lang.String scaleParam,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                SdoGeoRaster target,
                                double[] bgValues)
                         throws java.lang.Exception

      Scales a GeoRaster object by enlarging or reducing the image along row and column dimensions, and puts the result into a new object that reflects the scaling.
      Parameters:
      `source` - source GeoRaster objects

      `scaleParam` - a string specifying a scaling parameter keyword and its associated value. The keyword must be scaleFactor or maxDimSize:

      scaleFactor: to reduce or enlarge as a multiple of the original size. This keyword must have a numeric value greater than 0 (zero) (for example, 'scaleFactor=0.75'). A value of 1.0 will not change the current size; a value less than 1 will reduce the image; a value greater than 1 will enlarge the image. The number of cells along each dimension is the original number multiplied by scaleFactor. For example, if the scaleFactor value is 2 and the GeoRaster object has X and Y dimensions, the number of cells along each dimension is doubled.

      maxDimSize: to specify a size in terms of the maximum number of cells for each dimension. This keyword must have a numeric value for each dimension (for example, 'maxDimSize=(512,512)'). The aspect ratio is not changed.

      `resampleParam` - a string specifying a resampling parameter (for example, 'resampling=NN'). For the current release, the only supported keyword is resampling, and its value must be one of the following:

      NN: value of the nearest neighbor cell in the original GeoRaster object

      BILINEAR: distance-weighted average of the 4 nearest cells in the original GeoRaster object

      AVERAGE4: simple average of the 4 nearest cells in the original GeoRaster object

      AVERAGE16: simple average of the 16 nearest cells in the original GeoRaster object

      CUBIC: cubic convolution of the 16 nearest cells in the original GeoRaster object

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the scaleCopy operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### scaleCopy

          public void scaleCopy(SdoGeoRaster source,
                                java.lang.String scaleParam,
                                int pyramidLevel,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                SdoGeoRaster target,
                                double[] bgValues)
                         throws java.lang.Exception

      Scales a GeoRaster object by enlarging or reducing the image along row and column dimensions, and puts the result into a new object that reflects the scaling.
      Parameters:
      `source` - source GeoRaster objects

      `scaleParam` - a string specifying a scaling parameter keyword and its associated value. The keyword must be scaleFactor or maxDimSize:

      scaleFactor: to reduce or enlarge as a multiple of the original size. This keyword must have a numeric value greater than 0 (zero) (for example, 'scaleFactor=0.75'). A value of 1.0 will not change the current size; a value less than 1 will reduce the image; a value greater than 1 will enlarge the image. The number of cells along each dimension is the original number multiplied by scaleFactor. For example, if the scaleFactor value is 2 and the GeoRaster object has X and Y dimensions, the number of cells along each dimension is doubled.

      maxDimSize: to specify a size in terms of the maximum number of cells for each dimension. This keyword must have a numeric value for each dimension (for example, 'maxDimSize=(512,512)'). The aspect ratio is not changed.

      `pyramidLevel` - pyramid level

      `resampleParam` - a string specifying a resampling parameter (for example, 'resampling=NN'). For the current release, the only supported keyword is resampling, and its value must be one of the following:

      NN: value of the nearest neighbor cell in the original GeoRaster object

      BILINEAR: distance-weighted average of the 4 nearest cells in the original GeoRaster object

      AVERAGE4: simple average of the 4 nearest cells in the original GeoRaster object

      AVERAGE16: simple average of the 16 nearest cells in the original GeoRaster object

      CUBIC: cubic convolution of the 16 nearest cells in the original GeoRaster object

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the scaleCopy operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### updateRaster

          public void updateRaster(SdoGeoRaster target,
                                   int targetPyramidLevel,
                                   java.lang.String targetLayerNumbers,
                                   long[] targetArea,
                                   SdoGeoRaster source,
                                   int sourcePyramidLevel,
                                   java.lang.String sourceLayerNumbers,
                                   boolean updateUpperPyramids,
                                   double[] bgValues)
                            throws java.lang.Exception

      Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.
      Parameters:
      `target` - target GeoRaster object

      `targetPyramidLevel` - pyramid level of target GeoRaster object

      `targetLayerNumbers` - String specifying one or more layer numbers of layers in the target GeoRaster object to be updated. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1, 3, 4, 5, and 7.

      `targetArea` - area to be updated in targetGeoRaster: a rectangular window, specified by a numeric array with the lower-left and upper-right coordinates.

      `source` - source GeoRaster object

      `sourcePyramidLevel` - pyramid level of source GeoRaster object

      `sourceLayerNumbers` - string specifying one or more layer numbers of layers in sourceGeoRaster to be used to update targetGeoRaster. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1, 3, 4, 5, and 7. Any layers that you specify for this parameter must be compatible with the layers to be updated in the target GeoRaster object.

      `updateUpperPyramids` - TRUE or FALSE to specify whether to update upper-level pyramids.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### updateRaster

          public void updateRaster(SdoGeoRaster target,
                                   int targetPyramidLevel,
                                   java.lang.String targetLayerNumbers,
                                   JGeometry targetArea,
                                   SdoGeoRaster source,
                                   int sourcePyramidLevel,
                                   java.lang.String sourceLayerNumbers,
                                   boolean updateUpperPyramids,
                                   double[] bgValues)
                            throws java.lang.Exception

      Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.
      Parameters:
      `target` - target GeoRaster object

      `targetPyramidLevel` - pyramid level of target GeoRaster object

      `targetLayerNumbers` - String specifying one or more layer numbers of layers in the target GeoRaster object to be updated. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1, 3, 4, 5, and 7.

      `targetArea` - area to be updated in targetGeoRaster.

      `source` - source GeoRaster object

      `sourcePyramidLevel` - pyramid level of source GeoRaster object

      `sourceLayerNumbers` - string specifying one or more layer numbers of layers in sourceGeoRaster to be used to update targetGeoRaster. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: '1,3-5,7' for layers 1, 3, 4, 5, and 7. Any layers that you specify for this parameter must be compatible with the layers to be updated in the target GeoRaster object.

      `updateUpperPyramids` - TRUE or FALSE to specify whether to update upper-level pyramids.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues,
                             java.lang.String polygonClip)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the subset operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the subset operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             int pyramid,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `pyramid` - pyramid level

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             int pyramid,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues,
                             java.lang.String polygonClip)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `pyramid` - pyramid level

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the subset operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the subset operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             double[] cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### subset

          public void subset(SdoGeoRaster source,
                             int pyramid,
                             double[] cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String storageParam,
                             SdoGeoRaster target,
                             double[] bgValues)
                      throws java.lang.Exception

      Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.
      Parameters:
      `source` - source GeoRaster objects

      `pyramid` - pyramid level

      `cropArea` - crop area definition

      `layerNumbers` - a string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object to hold the result of the subset operation.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### georeference

          public void georeference(SdoGeoRaster georaster,
                                   int srid,
                                   int modelCoordinateLocation,
                                   double[] xCoefficients,
                                   double[] yCoefficients)
                            throws java.lang.Exception

      Georeferences a GeoRaster object using specified cell-to-model transformation coefficients.
      Parameters:
      `georaster` - the SDO_GEORASTER object to be georeferenced

      `srid` - model coordinate system. Must not be null or 0 (zero). It can be a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial, and some SRID-related operations may not be supported.

      `modelCoordinateLocation` - a value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT.

      `xCoefficients` - an array specifying the A, B, and C coefficient values in the calculation

      `yCoefficients` - an array specifying the D, E, and F coefficient values in the calculation

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMask

          public void getBitmapMask(SdoGeoRaster source,
                                    int layer,
                                    java.lang.String storageParam,
                                    SdoGeoRaster target)
                             throws java.lang.Exception

      Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.
      Parameters:
      `source` - source GeoRaster object

      `layer` - the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `storageParam` - a string specifying storage parameters

      `target` - target GeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setBitmapMask

          public void setBitmapMask(SdoGeoRaster georaster,
                                    int layer,
                                    SdoGeoRaster mask,
                                    java.lang.Integer NODATAMask)
                             throws java.lang.Exception

      Attaches a bitmap mask to a GeoRaster object, or replaces or removes the current bitmap mask.
      Parameters:
      `georaster` - GeoRaster object.

      `layer` - the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `mask` - The bitmap mask to be attached to the GeoRaster object. If this parameter is null, any existing bitmap mask associated with the specified layer of the GeoRaster object is removed.

      `NODATAMask` - Specifies 0 if mask is not to be interpreted as a NODATA mask, or 1 if mask is to be interpreted as a NODATA mask.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### deletePyramid

          public void deletePyramid(SdoGeoRaster georaster)
                             throws java.lang.Exception

      Deletes the pyramid data of a GeoRaster object.
      Parameters:
      `georaster` - GeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generatePyramid

          public void generatePyramid(SdoGeoRaster georaster,
                                      java.lang.String pyramidParams,
                                      double[] bgValues)
                               throws java.lang.Exception

      Generates pyramid data, which is stored together with the original data.
      Parameters:
      `georaster` - GeoRaster object

      `pyramidParams` - a string containing the pyramid parameters. pyramidParams must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

      rLevel (for example, rLevel=2): Specifies the maximum reduction level: the number of pyramid levels to create at a smaller (reduced) size than the original object. If you do not specify this keyword, pyramid levels are generated until the smaller of the number of rows or columns is between 64 and 128. The dimension sizes at each lower resolution level are equal to the truncated integer values of the dimension sizes at the next higher resolution level, divided by 2.

      resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN (value of the nearest neighbor cell in the original GeoRaster object), BILINEAR (distance-weighted average of the 4 nearest cells in the original GeoRaster object), AVERAGE4 (simple average of the 4 nearest cells in the original GeoRaster object), AVERAGE16 (simple average of the 16 nearest cells in the original GeoRaster object), CUBIC (cubic convolution of the 16 nearest cells in the original GeoRaster object).

      nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, AVERAGE4, AVERAGE16 or CUBIC, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks.

      The number of elements must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateBlockMBR

          public void generateBlockMBR(SdoGeoRaster georaster)
                                throws java.lang.Exception

      Computes the minimum bounding rectangle (MBR) for each block in a GeoRaster object, and sets the blockMBR attribute for each raster block in the raster data table.
      Parameters:
      `georaster` - GeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public void generateStatistics(SdoGeoRaster georaster,
                                         int samplingFactor,
                                         long[] samplingWindow,
                                         boolean histogram,
                                         java.lang.String layerNumbers,
                                         boolean useBin,
                                         double[] binFunction,
                                         boolean nodata)
                                  throws java.lang.Exception

      Computes and sets statistical data associated with one or more layers.
      Parameters:
      `georaster` - source GeoRaster object.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - sampling window: a rectangular window for which to set statistics, specified as a numeric array with the lower-left and upper-right coordinates. The window must be inside the extent in cell space. A null value for this parameter indicates the entire image.

      `histogram` - Specify TRUE to cause a histogram to be computed and stored, or FALSE to cause a histogram not to be computed and stored.

      `layerNumbers` - Numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '1,3-5,7' specifies layers 1, 3, 4, 5, and 7. Layer 0 (zero) indicates the object layer.

      `useBin` - Specifies whether or not to use a provided bin function (specified in the binFunction parameter) when generating statistics. TRUE (the default) causes a bin function to be used as follows: (1) the bin function specified by the binFunction parameter, if it is not null; otherwise, (2) the bin function specified by the element in the GeoRaster XML metadata, if one is specified; otherwise, (3) a dynamically generated bin function, as explained in the Usage Notes. FALSE causes a dynamically generated bin function to be used, and causes the binFunction parameter and element to be ignored.For information about bin functions, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

      `binFunction` - Bin function as an array whose elements specify the bin type, total number of bins, first bin number, minimum cell value, and maximum cell value. The SDO_NUMBER_ARRAY type is defined as VARRAY(1048576) OF NUMBER. For more information about the bin function for SQO_GEOR.generateStatistics, see the Usage Notes. For information about bin functions and an example, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateStatistics

          public void generateStatistics(SdoGeoRaster georaster,
                                         int samplingFactor,
                                         JGeometry samplingWindow,
                                         boolean histogram,
                                         java.lang.String layerNumbers,
                                         boolean useBin,
                                         double[] binFunction,
                                         boolean nodata)
                                  throws java.lang.Exception

      Computes and sets statistical data associated with one or more layers.
      Parameters:
      `georaster` - source GeoRaster object.

      `samplingFactor` - Sampling factor in the format 'samplingFactor=n', with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

      `samplingWindow` - sampling window: a rectangular window for which to set statistics, specified as an SDO_GEOMETRY object. The window must be inside the extent in cell space. A null value for this parameter indicates the entire image.

      `histogram` - Specify TRUE to cause a histogram to be computed and stored, or FALSE to cause a histogram not to be computed and stored.

      `layerNumbers` - numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, '1,3-5,7' specifies layers 1, 3, 4, 5, and 7. Layer 0 (zero) indicates the object layer.

      `useBin` - Specifies whether or not to use a provided bin function (specified in the binFunction parameter) when generating statistics. TRUE (the default) causes a bin function to be used as follows: (1) the bin function specified by the binFunction parameter, if it is not null; otherwise, (2) the bin function specified by the element in the GeoRaster XML metadata, if one is specified; otherwise, (3) a dynamically generated bin function, as explained in the Usage Notes. FALSE causes a dynamically generated bin function to be used, and causes the binFunction parameter and element to be ignored.For information about bin functions, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

      `binFunction` - Bin function as an array whose elements specify the bin type, total number of bins, first bin number, minimum cell value, and maximum cell value. The SDO_NUMBER_ARRAY type is defined as VARRAY(1048576) OF NUMBER. For more information about the bin function for SQO_GEOR.generateStatistics, see the Usage Notes. For information about bin functions and an example, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### calcCompressionRatio

          public double calcCompressionRatio(SdoGeoRaster georaster)
                                      throws java.lang.Exception

      Computes the compression ratio of the GeoRaster object.
      Parameters:
      `georaster` - source GeoRaster object

      Returns:
      the compression ratio of the given GeoRaster object.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateSpatialExtent

          public JGeometry generateSpatialExtent(SdoGeoRaster georaster,
                                                 java.lang.Double height)
                                          throws java.lang.Exception

      Generates a Spatial geometry that contains the spatial extent (footprint) of the GeoRaster object.
      Parameters:
      `georaster` - source GeoRaster object

      `height` - number specifying the Z value for three-dimensional (X, Y, Z) georeferencing. For two-dimensional georeferencing, use null.

      Returns:
      a JGeometry object that contains the spatial extent (footprint) of the GeoRaster object.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateBlockMBR

          public boolean validateBlockMBR(SdoGeoRaster georaster)
                                   throws java.lang.Exception

      Validates the blockMBR attribute of each block of a GeoRaster object.
      Parameters:
      `georaster` - source GeoRaster object

      Returns:
      true or false to indicate if the blockMBR attribute of the given GeoRaster object is valid.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateGeoRaster

          public boolean validateGeoRaster(SdoGeoRaster georaster)
                                    throws java.lang.Exception

      Validates a GeoRaster object, checking its raster data and metadata.
      Parameters:
      `georaster` - source GeoRaster object

      Returns:
      true or false to indicate if the given GeoRaster object is valid.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(SdoGeoRaster georaster,
                                      long row,
                                      long column,
                                      java.lang.String bandNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cell in a specified point of a GeoRaster object to a single new value.
      Parameters:
      `georaster` - source GeoRaster object

      `row` - row of the point where the values is changed to newCellValue

      `column` - column of the point where the values is changed to newCellValue

      `bandNumbers` - a string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `newCellValue` - the new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(SdoGeoRaster georaster,
                                      long startRow,
                                      long startColumn,
                                      long endRow,
                                      long endColumn,
                                      java.lang.String bandNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.
      Parameters:
      `georaster` - source GeoRaster object.

      `startRow` - startRow of the window in which to change the values of all cells to newCellValue

      `startColumn` - startColumn of the window in which to change the values of all cells to newCellValue

      `endRow` - endRow of the window in which to change the values of all cells to newCellValue

      `endColumn` - endColumn of the window in which to change the values of all cells to newCellValue

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `newCellValue` - The new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(SdoGeoRaster georaster,
                                      JGeometry window,
                                      java.lang.String layerNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.
      Parameters:
      `georaster` - source GeoRaster object.

      `window` - window in which to change the values of all cells to newCellValue

      `layerNumbers` - a string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `newCellValue` - the new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public double getCellValue(SdoGeoRaster georaster,
                                     JGeometry ptGeom,
                                     int pyramidLevel,
                                     int layerNumber)
                              throws java.lang.Exception

      Returns the value of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer number.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - point geometry that identifies the cell whose value is to be returned

      `layerNumber` - number of the logical layer that contains the cell whose value is to be returned. (The logical layer number is the physical band number plus 1.)

      Returns:
      cellValue.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public double getCellValue(SdoGeoRaster georaster,
                                     int pyramidLevel,
                                     int rowNumber,
                                     int colNumber,
                                     int bandNumber)
                              throws java.lang.Exception

      Returns the value of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its logical layer number.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumber` - number of the row that contains the cell whose value is to be returned

      `colNumber` - number of the column that contains the cell whose value is to be returned

      `bandNumber` - number of the physical band that contains the cell whose value is to be returned

      Returns:
      cellValue.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValue

          public double getBitmapMaskValue(SdoGeoRaster georaster,
                                           JGeometry ptGeom,
                                           int pyramidLevel,
                                           int layerNumber)
                                    throws java.lang.Exception

      Gets the value of a single cell from a bitmap mask.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - point geometry that identifies the cell whose value is to be returned

      `layerNumber` - number of the logical layer that contains the cell whose value is to be returned. (The logical layer number is the physical band number plus 1.)

      Returns:
      cellValue.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValue

          public double getBitmapMaskValue(SdoGeoRaster georaster,
                                           int pyramidLevel,
                                           int rowNumber,
                                           int colNumber,
                                           int bandNumber)
                                    throws java.lang.Exception

      Gets the value of a single cell from a bitmap mask.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumber` - number of the row that contains the cell whose value is to be returned

      `colNumber` - number of the column that contains the cell whose value is to be returned

      `bandNumber` - number of the physical band that contains the cell whose value is to be returned

      Returns:
      cellValue.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValues

          public java.math.BigDecimal[] getCellValues(SdoGeoRaster georaster,
                                                      int pyramidLevel,
                                                      int[] rowNumbers,
                                                      int[] colNumbers,
                                                      int bandNumber)
                                               throws java.lang.Exception

      Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumbers` - numbers of the rows that contain the cells whose values are to be returned

      `colNumbers` - numbers of the columns that contain the cells whose values are to be returned

      `bandNumber` - number of the physical band that contains the cell whose value is to be returned

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValues

          public java.math.BigDecimal[] getCellValues(SdoGeoRaster georaster,
                                                      int pyramidLevel,
                                                      JGeometry ptGeom,
                                                      int layerNumber)
                                               throws java.lang.Exception

      Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - multipoint geometry that identifies the cell whose value is to be returned.

      `layerNumber` - number of the logical layer that contains the cells whose values are to be returned.

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValues

          public void changeCellValues(SdoGeoRaster georaster,
                                       int[] rowNumbers,
                                       int[] colNumbers,
                                       int bandNumber,
                                       double[] newCellValues,
                                       double[] bgValues)
                                throws java.lang.Exception

      Changes the value of raster cells specified by row/column arrays or by a multipoint geometry to new values.
      Parameters:
      `georaster` - source GeoRaster object

      `rowNumbers` - numbers of the rows that contain the cells whose values are to be returned

      `colNumbers` - numbers of the columns that contain the cells whose values are to be returned

      `bandNumber` - number of the physical band that contains the cell whose value is to be returned

      `newCellValues` - The new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Empty Raster Blocks). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValues

          public void changeCellValues(SdoGeoRaster georaster,
                                       JGeometry ptGeom,
                                       int layerNumber,
                                       double[] newCellValues,
                                       double[] bgValues)
                                throws java.lang.Exception

      Changes the value of raster cells specified by row/column arrays or by a multipoint geometry to new values.
      Parameters:
      `georaster` - source GeoRaster object

      `ptGeom` - multipoint geometry that identifies the cell whose value is to be returned.

      `layerNumber` - number of the logical layer that contains the cells whose values are to be returned.

      `newCellValues` - The new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Empty Raster Blocks). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### evaluateDoubles

          public java.math.BigDecimal[] evaluateDoubles(SdoGeoRaster georaster,
                                                        int pyramidLevel,
                                                        int[] rowNumbers,
                                                        int[] colNumbers,
                                                        int bandNumber,
                                                        java.lang.String interpolationMethod)
                                                 throws java.lang.Exception

      Evaluates multiple locations using a specified interpolation method, and returns the raster values (double precision numbers) for the specified band or layer for those locations.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumbers` - numbers of the rows that contain the cells whose values are to be returned

      `colNumbers` - numbers of the columns that contain the cells whose values are to be returned

      `bandNumber` - number of the physical band that contains the cell whose value is to be returned

      `interpolationMethod` - interpolationMethod(for example, interpolationMethod=NN): Specifies the interpolation method. Must be one of the following: NN, BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, AVERAGE16.

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### evaluateDoubles

          public java.math.BigDecimal[] evaluateDoubles(SdoGeoRaster georaster,
                                                        int pyramidLevel,
                                                        JGeometry ptGeom,
                                                        int layerNumber,
                                                        java.lang.String interpolationMethod)
                                                 throws java.lang.Exception

      Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - multipoint geometry that identifies the cell whose value is to be returned.

      `layerNumber` - number of the logical layer that contains the cells whose values are to be returned.

      `interpolationMethod` - interpolationMethod(for example, interpolationMethod=NN): Specifies the interpolation method. Must be one of the following: NN, BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, AVERAGE16.

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValues

          public java.math.BigDecimal[] getBitmapMaskValues(SdoGeoRaster georaster,
                                                            int layerNumber,
                                                            int pyramidLevel,
                                                            int[] rowNumbers,
                                                            int[] colNumbers)
                                                     throws java.lang.Exception

      Gets the values of multiple cells from a bitmap mask.
      Parameters:
      `georaster` - source GeoRaster object

      `layerNumber` - number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumbers` - numbers of the rows that contain the cells whose values are to be returned

      `colNumbers` - numbers of the columns that contain the cells whose values are to be returned

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValues

          public java.math.BigDecimal[] getBitmapMaskValues(SdoGeoRaster georaster,
                                                            int layerNumber,
                                                            int pyramidLevel,
                                                            JGeometry ptGeom)
                                                     throws java.lang.Exception

      Gets the values of multiple cells from a bitmap mask.
      Parameters:
      `georaster` - source GeoRaster object

      `layerNumber` - number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - multipoint geometry that identifies the cell whose value is to be returned.

      Returns:
      cellValues.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setModelCoordLocation

          public void setModelCoordLocation(SdoGeoRaster georaster,
                                            java.lang.String modelCoordLoc)
                                     throws java.lang.Exception

      Sets the model coordinate location value for a GeoRaster object, or deletes the current model coordinate location value (if any) if the modelCoordLoc parameter is specified as null.
      Parameters:
      `georaster` - source GeoRaster object.

      `modelCoordLoc` - Model coordinate location to set for the GeoRaster object. It must be specified as either null (to delete any current model coordinate location value) or one of the following string values: CENTER (the cell coordinate system is center-based) or UPPERLEFT (the cell coordinate system is based on the upper-left corner).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createTemplate

          public void createTemplate(SdoGeoRaster georaster,
                                     int rasterType,
                                     java.lang.String rasterSpec,
                                     java.lang.String maskLayers,
                                     java.lang.String initRDTEntry)
                              throws java.lang.Exception

      Populates a GeoRaster object with metadata of a general pattern, and optionally inserts entries with empty raster blocks into its raster data table.
      Parameters:
      `georaster` - source GeoRaster object.

      `rasterType` - The 5-digit rasterType attribute value, as specified in Section 2.1.1 of GeoRaster document.

      `rasterSpec` - The rasterSpec parameter must be a quoted string that contains one or more keyword-value pairs. The following keyword are supported for this parameter: blocking (for example, blocking=TRUE). For an explanation of this keyword, see Table 1-1 in Section 1.4.1 of GeoRaster document , "Storage Parameters". blocksize (for example, blocksize=(128,128,3)). For an explanation of this keyword, see Table 1-1 in Section 1.4.1 of GeoRaster document, "Storage Parameters". cellDepth (for example, cellDepth=8BIT_S). For an explanation of this keyword, see Table 1-1 in Section 1.4.1, "Storage Parameters". compression (for example, compression=JPEG-B). For an explanation of this keyword, see Table 1-1 in Section 1.4.1, "Storage Parameters". dimSize (for example, dimSize=(256,256,3)): Specifies the row, column, and band dimension sizes. This keyword must be specified and must be consistent with the rasterType parameter. interleaving (for example, interleaving=BIP). For an explanation of this keyword, see Table 1-1 in Section 1.4.1, "Storage Parameters". quality (for example, quality=75). For an explanation of this keyword, see Table 1-1 in Section 1.4.1, "Storage Parameters". resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN (value of the nearest neighbor cell in the original GeoRaster object), BILINEAR (distance-weighted average of the 4 nearest cells in the original GeoRaster object), AVERAGE4 (simple average of the 4 nearest cells in the original GeoRaster object), AVERAGE16 (simple average of the 16 nearest cells in the original GeoRaster object), CUBIC (cubic convolution of the 16 nearest cells in the original GeoRaster object). This keyword is ignored if rLevel is not set. rLevel (for example, rLevel=2): Specifies the maximum pyramid reduction level. Must be a positive integer. If you specify this keyword, the pyramid type is set to DECREASE in the metadata; otherwise the pyramid type is set to NONE. ultCoord (for example, ultCoord=(0,0,0)): Specifies the upper-left coordinate integer values for the GeoRaster object. The default value is 0 for all the dimensions. The value for the band dimension must be 0.

      `maskLayers` - A string identifying the logical layer numbers on which there are associated bitmap masks. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `initRDTEntry` - The string TRUE causes the raster data table to be populated; the string FALSE causes the raster data table not to be populated. If you do not specify this parameter, the raster data table is not populated.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getGeoreferenceType

          public int getGeoreferenceType(SdoGeoRaster georaster)
                                  throws java.lang.Exception

      Returns a number that indicates the georeference type for a GeoRaster object.
      Parameters:
      `georaster` - source GeoRaster object.

      Returns:
      one of the following numbers to indicate the georeference type: 1 for unknown type or null GeoRaster object, 2 for affine transform, 3 for direct linear transform (DLT), 4 for rational polynomial coefficient (RPC), 5 for cubic polynomial, 6 for quadratic rational polynomial, or 7 for quadratic polynomial.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### evaluateDouble

          public java.math.BigDecimal[] evaluateDouble(SdoGeoRaster georaster,
                                                       int pyramidLevel,
                                                       int rowNumber,
                                                       int colNumber,
                                                       java.lang.String bands,
                                                       java.lang.String interpolationMethod)
                                                throws java.lang.Exception

      Evaluates a direct location using a specified interpolation method, and returns the raster values for the specified bands for that location.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned.

      `rowNumber` - number of the row that contains the cell whose value is to be returned.

      `colNumber` - number of the column that contains the cell whose value is to be returned.

      `bands` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `interpolationMethod` - interpolationMethod(for example, interpolationMethod=NN): Specifies the interpolation method. Must be one of the following: NN, BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, AVERAGE16.

      Returns:
      cell values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### evaluateDouble

          public java.math.BigDecimal[] evaluateDouble(SdoGeoRaster georaster,
                                                       int pyramidLevel,
                                                       JGeometry ptGeom,
                                                       java.lang.String layers,
                                                       java.lang.String interpolationMethod)
                                                throws java.lang.Exception

      Evaluates a direct location using a specified interpolation method, and returns the raster values for the specified layers for that location.
      Parameters:
      `georaster` - source GeoRaster object

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - Point geometry that identifies the direct location whose raster values are to be returned.

      `layers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). (the logical layer number is the physical band number plus 1).

      `interpolationMethod` - interpolationMethod(for example, interpolationMethod=NN): Specifies the interpolation method. Must be one of the following: NN, BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, AVERAGE16.

      Returns:
      cell values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public java.math.BigDecimal[] getCellValue(SdoGeoRaster georaster,
                                                     int pyramidLevel,
                                                     int rowNumber,
                                                     int colNumber,
                                                     java.lang.String bands)
                                              throws java.lang.Exception

      Returns the values of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band numbers in its cell coordinate system.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned.

      `rowNumber` - number of the row that contains the cell whose value is to be returned.

      `colNumber` - number of the column that contains the cell whose value is to be returned.

      `bands` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      Returns:
      cell values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public java.math.BigDecimal[] getCellValue(SdoGeoRaster georaster,
                                                     int pyramidLevel,
                                                     JGeometry ptGeom,
                                                     java.lang.String layers)
                                              throws java.lang.Exception

      Returns the values of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer numbers.
      Parameters:
      `georaster` - source GeoRaster object.

      `pyramidLevel` - pyramid level containing the cell whose value is to be returned.

      `ptGeom` - Point geometry that identifies the cell whose values is to be returned.

      `layers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). (the logical layer number is the physical band number plus 1).

      Returns:
      cell values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### georeference

          @Deprecated
          public java.math.BigDecimal[] georeference(SdoGeoRaster georaster,
                                                                  java.lang.String FFMethodType,
                                                                  int nGCP,
                                                                  SdoGeorPKG.SdoGeorGCP[] gcps,
                                                                  java.lang.Boolean storeGCP,
                                                                  java.lang.Integer srid,
                                                                  java.lang.Integer modelCoordinateLocation,
                                                                  java.lang.String setResolution)
                                                           throws java.lang.Exception

      Deprecated. 
      returns the solution of any one of the supported geometric models using ground control points (GCPs) that are specified in the parameters.
      Parameters:
      `georaster` - The SdoGeoRaster object to be georeferenced.

      `FFMethodType` - Polynomial or rational polynomial function used as georeference geometric model. Must be one of the following string values: Affine, QuadraticPolynomial, CubicPolynomial, DLT, QuadraticRational, or RPC.

      `nGCP` - Number of ground control points in the GCP array (gcps parameter).

      `gcps` - A GCP array of type SdoGeorGCP.

      `storeGCP` - A flag indicating whether the GCPs should be stored in the GeoRaster metadata.

      `srid` - Model coordinate system. it can be null or a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial and Graph, and some SRID-related operations may not be supported.

      `modelCoordinateLocation` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT.

      `setResolution` - A flag indicating whether the spatial resolution is calculated and stored in the GeoRaster metadata. The string FALSE or a null value does not store the spatial resolution in the GeoRaster metadata; the string TRUE stores the spatial resolution in the GeoRaster metadata.

      Returns:
      The returned array contains RMS values and residuals, which have the following order: the solution accuracy (rowRMS, colRMS, totalRMS) computed using control points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using check points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using control points, and the (xResidual, yResidual) for each control point (not for check points). The ordering of the residuals is the same as the control points stored in the XML metadata (not necessarily in the sequential order of the control point ID values if the ID values are numbers).There are always at least 17 values returned (assuming at least 3 control points). A positioning accuracy (RMS) value of -1.0 means that value does not exist. For a two-dimensional geometric model, the zRMS value is always -1.0; otherwise, zRMS values are always 0 in the current release.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### georeference

          public java.math.BigDecimal[] georeference(SdoGeoRaster georaster,
                                                     GCPGeoreference gcpGeoreference,
                                                     java.lang.Boolean storeGCP,
                                                     java.lang.Integer srid,
                                                     java.lang.Integer modelCoordinateLocation,
                                                     java.lang.String setResolution)
                                              throws java.lang.Exception

      returns the solution of any one of the supported geometric models using ground control points (GCPs) that are specified in the parameters.
      Parameters:
      `georaster` - The SdoGeoRaster object to be georeferenced.

      `gcpGeoreference` - A GCPGeoreference object.

      `storeGCP` - A flag indicating whether the GCPs should be stored in the GeoRaster metadata.

      `srid` - Model coordinate system. it can be null or a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial and Graph, and some SRID-related operations may not be supported.

      `modelCoordinateLocation` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT.

      `setResolution` - A flag indicating whether the spatial resolution is calculated and stored in the GeoRaster metadata. The string FALSE or a null value does not store the spatial resolution in the GeoRaster metadata; the string TRUE stores the spatial resolution in the GeoRaster metadata.

      Returns:
      The returned array contains RMS values and residuals, which have the following order: the solution accuracy (rowRMS, colRMS, totalRMS) computed using control points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using check points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using control points, and the (xResidual, yResidual) for each control point (not for check points). The ordering of the residuals is the same as the control points stored in the XML metadata (not necessarily in the sequential order of the control point ID values if the ID values are numbers).There are always at least 17 values returned (assuming at least 3 control points). A positioning accuracy (RMS) value of -1.0 means that value does not exist. For a two-dimensional geometric model, the zRMS value is always -1.0; otherwise, zRMS values are always 0 in the current release.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### georeference

          @Deprecated
          public java.math.BigDecimal[] georeference(SdoGeoRaster georaster,
                                                                  SdoGeorPKG.SdoGeorGCPRefType gcpGeorefModel,
                                                                  java.lang.Boolean storeGCP,
                                                                  java.lang.Integer srid,
                                                                  java.lang.Integer modelCoordinateLocation,
                                                                  java.lang.String setResolution)
                                                           throws java.lang.Exception

      Deprecated. 
      returns the solution of any one of the supported geometric models using ground control points (GCPs) that are specified in the parameters.
      Parameters:
      `georaster` - The SdoGeoRaster object to be georeferenced.

      `gcpGeorefModel` - A SdoGeorGCPRefType object containing the following: FFMethodType, nGCP, GCPs, solutionAccuracy.

      `storeGCP` - A flag indicating whether the GCPs should be stored in the GeoRaster metadata.

      `srid` - Model coordinate system. it can be null or a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial and Graph, and some SRID-related operations may not be supported.

      `modelCoordinateLocation` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT.

      `setResolution` - A flag indicating whether the spatial resolution is calculated and stored in the GeoRaster metadata. The string FALSE or a null value does not store the spatial resolution in the GeoRaster metadata; the string TRUE stores the spatial resolution in the GeoRaster metadata.

      Returns:
      The returned array contains RMS values and residuals, which have the following order: the solution accuracy (rowRMS, colRMS, totalRMS) computed using control points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using check points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using control points, and the (xResidual, yResidual) for each control point (not for check points). The ordering of the residuals is the same as the control points stored in the XML metadata (not necessarily in the sequential order of the control point ID values if the ID values are numbers).There are always at least 17 values returned (assuming at least 3 control points). A positioning accuracy (RMS) value of -1.0 means that value does not exist. For a two-dimensional geometric model, the zRMS value is always -1.0; otherwise, zRMS values are always 0 in the current release.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### georeference

          public java.math.BigDecimal[] georeference(SdoGeoRaster georaster,
                                                     java.lang.String FFMethodType,
                                                     java.lang.Integer srid,
                                                     java.lang.Integer modelCoordinateLocation,
                                                     java.lang.String setResolution)
                                              throws java.lang.Exception

      returns the solution of any one of the supported geometric models using ground control points (GCPs) that are stored in the database.
      Parameters:
      `georaster` - The SdoGeoRaster object to be georeferenced.

      `FFMethodType` - Polynomial or rational polynomial function used as georeference geometric model. Must be one of the following string values: Affine, QuadraticPolynomial, CubicPolynomial, DLT, QuadraticRational, or RPC.

      `srid` - Model coordinate system. it can be null or a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial and Graph, and some SRID-related operations may not be supported.

      `modelCoordinateLocation` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT.

      `setResolution` - A flag indicating whether the spatial resolution is calculated and stored in the GeoRaster metadata. The string FALSE or a null value does not store the spatial resolution in the GeoRaster metadata; the string TRUE stores the spatial resolution in the GeoRaster metadata.

      Returns:
      The returned array contains RMS values and residuals, which have the following order: the solution accuracy (rowRMS, colRMS, totalRMS) computed using control points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using check points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using control points, and the (xResidual, yResidual) for each control point (not for check points). The ordering of the residuals is the same as the control points stored in the XML metadata (not necessarily in the sequential order of the control point ID values if the ID values are numbers).There are always at least 17 values returned (assuming at least 3 control points). A positioning accuracy (RMS) value of -1.0 means that value does not exist. For a two-dimensional geometric model, the zRMS value is always -1.0; otherwise, zRMS values are always 0 in the current release.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### reproject

          public void reproject(SdoGeoRaster inGeoRaster,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                int outSRID,
                                SdoGeoRaster outGeoraster,
                                double[] bgValues)
                         throws java.lang.Exception

      Reprojects a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).
      Parameters:
      `inGeoRaster` - The GeoRaster object on which the reprojection operation is to be performed to create the new object.

      `resampleParam` - A string containing the resampling parameters, resampleParam must be a quoted string that contains one or more of the following keywords, each with an appropriate value: resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN, BILINEAR, CUBIC, AVERAGE4, AVERAGE16. nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, CUBIC, AVERAGE4, or AVERAGE16, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1 of GeoRaster document.

      `outSRID` - Output srid.

      `outGeoraster` - Output georaster object.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks . The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### reproject

          public void reproject(SdoGeoRaster inGeoRaster,
                                int pyramidLevel,
                                JGeometry cropArea,
                                java.lang.String layerNumbers,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                int outSRID,
                                SdoGeoRaster outGeoraster,
                                double[] bgValues)
                         throws java.lang.Exception

      Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).
      Parameters:
      `inGeoRaster` - The GeoRaster object on which the reprojection operation is to be performed to create the new object.

      `pyramidLevel` - A number specifying the pyramid level of the source GeoRaster object.

      `cropArea` - A JGeometry object, and the minimum bounding rectangle (MBR) of the JGeometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `resampleParam` - A string containing the resampling parameters, resampleParam must be a quoted string that contains one or more of the following keywords, each with an appropriate value: resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN, BILINEAR, CUBIC, AVERAGE4, AVERAGE16. nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, CUBIC, AVERAGE4, or AVERAGE16, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1 of GeoRaster document.

      `outSRID` - Output srid.

      `outGeoraster` - output georaster object.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### reproject

          public void reproject(SdoGeoRaster inGeoRaster,
                                int pyramidLevel,
                                double[] cropArea,
                                java.lang.String bandNumbers,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                int outSRID,
                                SdoGeoRaster outGeoraster,
                                double[] bgValues)
                         throws java.lang.Exception

      Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).
      Parameters:
      `inGeoRaster` - The GeoRaster object on which the reprojection operation is to be performed to create the new object.

      `pyramidLevel` - A number specifying the pyramid level of the source GeoRaster object.

      `cropArea` - The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `resampleParam` - A string containing the resampling parameters, resampleParam must be a quoted string that contains one or more of the following keywords, each with an appropriate value: resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN, BILINEAR, CUBIC, AVERAGE4, AVERAGE16. nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, CUBIC, AVERAGE4, or AVERAGE16, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1 of GeoRaster document.

      `outSRID` - Output srid.

      `outGeoraster` - output georaster object.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### reproject

          public void reproject(SdoGeoRaster inGeoRaster,
                                int pyramidLevel,
                                JGeometry cropArea,
                                java.lang.String layerNumbers,
                                java.lang.String resampleParam,
                                java.lang.String storageParam,
                                int outSRID,
                                java.sql.Blob[] rasterBlob,
                                JGeometry outArea,
                                double[] outWindow,
                                double[] bgValues)
                         throws java.lang.Exception

      Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).
      Parameters:
      `inGeoRaster` - The GeoRaster object on which the reprojection operation is to be performed to create the new object.

      `pyramidLevel` - A number specifying the pyramid level of the source GeoRaster object.

      `cropArea` - A JGeometry object, and the minimum bounding rectangle (MBR) of the JGeometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `resampleParam` - A string containing the resampling parameters, resampleParam must be a quoted string that contains one or more of the following keywords, each with an appropriate value: resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN, BILINEAR, CUBIC, AVERAGE4, AVERAGE16. nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, CUBIC, AVERAGE4, or AVERAGE16, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1 of GeoRaster document.

      `outSRID` - Output srid.

      `rasterBlob` - output raster blob array.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### reproject

          public java.sql.Blob reproject(SdoGeoRaster inGeoRaster,
                                         int pyramidLevel,
                                         double[] cropArea,
                                         java.lang.String bandNumbers,
                                         java.lang.String resampleParam,
                                         java.lang.String storageParam,
                                         int outSRID,
                                         JGeometry outArea,
                                         double[] outWindow,
                                         double[] bgValues)
                                  throws java.lang.Exception

      Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter).
      Parameters:
      `inGeoRaster` - The GeoRaster object on which the reprojection operation is to be performed to create the new object.

      `pyramidLevel` - A number specifying the pyramid level of the source GeoRaster object.

      `cropArea` - The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `resampleParam` - A string containing the resampling parameters, resampleParam must be a quoted string that contains one or more of the following keywords, each with an appropriate value: resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN, BILINEAR, CUBIC, AVERAGE4, AVERAGE16. nodata (for example, nodata=TRUE): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either TRUE (NODATA values and value ranges should be considered) or FALSE (NODATA values and value ranges should not be considered). The default value is FALSE. If the value is TRUE and the resampling method is BILINEAR, CUBIC, AVERAGE4, or AVERAGE16, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1 of GeoRaster document.

      `outSRID` - Output srid.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Returns:
      Output georaster blob.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### decompressJP2

          public void decompressJP2(SdoGeoRaster inGeoRaster,
                                    java.lang.Integer pyramidLevel,
                                    double[] cropArea,
                                    java.lang.String layerNumbers,
                                    java.lang.String storageParam,
                                    SdoGeoRaster outGeoRaster)
                             throws java.lang.Exception

      Decompress the JPEG 2000 compressed GeoRaster image into a GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be decompressed.

      `pyramidLevel` - A number specifying the pyramid level to be decompressed in the source GeoRaster object.

      `cropArea` - Crop area definition. If cropArea is of type SDO_GEOMETRY, use the layerNumbers parameter to specify one or more layer numbers; if cropArea is of type SDO_NUMBER_ARRAY, use the bandNumbers parameter to specify one or more band numbers. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### decompressJP2

          public void decompressJP2(SdoGeoRaster inGeoRaster,
                                    java.lang.Integer pyramidLevel,
                                    JGeometry cropArea,
                                    java.lang.String bandNumbers,
                                    java.lang.String storageParam,
                                    SdoGeoRaster outGeoRaster)
                             throws java.lang.Exception

      Decompress the JPEG 2000 compressed GeoRaster image into a GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be decompressed.

      `pyramidLevel` - A number specifying the pyramid level to be decompressed in the source GeoRaster object.

      `cropArea` - Crop area definition. If cropArea is of type SDO_GEOMETRY, use the layerNumbers parameter to specify one or more layer numbers; if cropArea is of type SDO_NUMBER_ARRAY, use the bandNumbers parameter to specify one or more band numbers. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### compressJP2

          public void compressJP2(SdoGeoRaster inGeoRaster,
                                  java.lang.String compressParam,
                                  SdoGeoRaster outGeoRaster)
                           throws java.lang.Exception

      Compresses the image in a GeoRaster object using JPEG 2000 compression.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be compressed.

      `compressParam` - A string specifying one or more keywords for the compression parameter. For an explanation of the available keywords, see JPEG 2000 (JP2) Compression Parameters.

      `outGeoRaster` - The SDO_GEORASTER object to hold the result of the compression. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateAreaWeightedMean

          public double generateAreaWeightedMean(SdoGeoRaster georaster,
                                                 JGeometry window,
                                                 java.lang.Integer bandNumber,
                                                 boolean nodata)
                                          throws java.lang.Exception

      Computes the area weighted mean value on a specified band of the input GeoRaster object. (It does not modify metadata in the GeoRaster object.)
      Parameters:
      `georaster` - GeoRaster object.

      `window` - A polygon geometry object from which to generate statistics,it is transformed into raster space if it is in model space,see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

      `bandNumber` - Band ordinate number of the layer for which to perform the operation.

      `nodata` - Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. TRUE causes all pixels with a NODATA value not to be considered; FALSE (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in NODATA Values and Value Ranges.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### warp

          public void warp(SdoGeoRaster inGeoRaster,
                           java.lang.Integer pyramidLevel,
                           GeorSpatialReference outSRS,
                           JGeometry cropArea,
                           double[] dimensionSize,
                           java.lang.String layerNumbers,
                           java.lang.String elevationParam,
                           java.lang.String resampleParam,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           double[] bgValues,
                           int parallelParam)
                    throws java.lang.Exception

      Perform geometric transformation on the input GeoRaster object to produce an output GeoRaster object with the specified output spatial reference system.
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation. It must be georeferenced (see Georeferencing GeoRaster Objects and Advanced Georeferencing).

      `pyramidLevel` - Pyramid level of the source GeoRaster object for the operation. For BLOB output, this parameter is required. For SDO_GEORASTER output, if this parameter is null, all pyramid levels from the input GeoRaster object are processed. If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

      `outSRS` - Coordinate system (spatial reference system) for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

      `cropArea` - Defines the shape of the area to be covered by the output image. Areas outside this polygon will be filled with the background value. If this parameter is not specified, no cropping is performed.

      `dimensionSize` - Dimension size array of the GeoRaster object. Defines the extent of the image in cell space.

      `layerNumbers` - String specifying one or more numbers of layers from inGeoRaster to be transferred to outGeoRaster. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example:'1,3-5,7' for layers 1, 3, 4, 5, and 7. If this parameter is null (the default) all the layers will be processed.

      `elevationParam` - A string containing one or more of the elevation parameters average (average surface height), scale (scale value applied to all DEM values), and offset (offset applied to all DEM values), where the new value is (value + offset) \* scale. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, 'average=800 scale=3.2808399 offset=10'). If this parameter is null, 0 is assumed for average and offset, and 1 is used for scale. Any scale and offset values are ignored if DEM is not specified. The use of the elevationParam parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation. Note:For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

      `resampleParam` - A comma-separated quoted string of keyword=value pairs for specifying resampling parameters.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Empty Raster Blocks). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `parallelParam` - Specifies the degree of parallelism for the operation. If specified, must be greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### warp

          public void warp(SdoGeoRaster inGeoRaster,
                           java.lang.Integer pyramidLevel,
                           GeorSpatialReference outSRS,
                           JGeometry cropArea,
                           double[] dimensionSize,
                           java.lang.String layerNumbers,
                           java.lang.String elevationParam,
                           java.lang.String resampleParam,
                           java.lang.String storageParam,
                           java.sql.Blob[] rasterBlob,
                           JGeometry[] outArea,
                           long[] outWindow,
                           double[] bgValues)
                    throws java.lang.Exception

      Perform geometric transformation on the input GeoRaster object to produce an output GeoRaster object with the specified output spatial reference system.
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation. It must be georeferenced (see Georeferencing GeoRaster Objects and Advanced Georeferencing).

      `pyramidLevel` - Pyramid level of the source GeoRaster object for the operation. For BLOB output, this parameter is required. For SDO_GEORASTER output, if this parameter is null, all pyramid levels from the input GeoRaster object are processed. If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

      `outSRS` - Coordinate system (spatial reference system) for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

      `cropArea` - Defines the shape of the area to be covered by the output image. Areas outside this polygon will be filled with the background value. If this parameter is not specified, no cropping is performed.

      `dimensionSize` - Dimension size array of the GeoRaster object. Defines the extent of the image in cell space.

      `layerNumbers` - String specifying one or more numbers of layers from inGeoRaster to be transferred to outGeoRaster. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example:'1,3-5,7' for layers 1, 3, 4, 5, and 7. If this parameter is null (the default) all the layers will be processed.

      `elevationParam` - A string containing one or more of the elevation parameters average (average surface height), scale (scale value applied to all DEM values), and offset (offset applied to all DEM values), where the new value is (value + offset) \* scale. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, 'average=800 scale=3.2808399 offset=10'). If this parameter is null, 0 is assumed for average and offset, and 1 is used for scale. Any scale and offset values are ignored if DEM is not specified. The use of the elevationParam parameter requires that the input GeoRaster object have a 3D model SRID. When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if DEM is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation. Note:For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

      `resampleParam` - A comma-separated quoted string of keyword=value pairs for specifying resampling parameters.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - BLOB to hold the output reflecting the rectification. It must exist or have been initialized before the operation.

      `outArea` - An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateBitmapPyramid

          public void generateBitmapPyramid(SdoGeoRaster src_geor,
                                            SdoGeoRaster tmp_geor,
                                            SdoGeoRaster target_geor,
                                            java.lang.String pyramidParams,
                                            double[] bgValues,
                                            int parallelParam)
                                     throws java.lang.Exception

      Generates pyramid data for a bitmap GeoRaster object.
      Parameters:
      `src_geor` - Source GeoRaster object for which pyramid data is to be generated.

      `tmp_geor` - Temporary GeoRaster object used to store temporary data

      `target_geor` - Target GeoRaster object used to store the resulting GeoRaster data.

      `pyramidParams` - A string containing the pyramid parameters. See the Usage Notes for information about the available keywords and values.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Empty Raster Blocks). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `parallelParam` - Specifies the degree of parallelism for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### affineTransform

          public void affineTransform(SdoGeoRaster inGeoRaster,
                                      double[] translation,
                                      double[] scales,
                                      double[] rotatePoint,
                                      java.lang.Double rotateAngle,
                                      double[] shear,
                                      java.lang.Integer reflection,
                                      java.lang.String storageParam,
                                      SdoGeoRaster outGeoRaster,
                                      double[] bgValues,
                                      int parallelParam)
                               throws java.lang.Exception

      Apply affine geometric trasnformation on GeoRaster Objects
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation

      `translation` - An array of numbers contains the shift in x and y directions. If it is NULL, no translation happens.

      `scales` - An array of numbers contains the multiplication factors of image row and column. The first number is for column, and the second for row. If any one is NULL, no scale for that dimension; if the parameter is NULL, no scale applies.

      `rotatePoint` - Defines the point (X,Y) about which to rotate; if new use the default point (0,0).

      `rotateAngle` - The angle to rotate. If is NULL no rotation applies.

      `shear` - Array of numbers contains the shearing in x and y directions. The first number is X axis, and the second for Y axis. If any one is NULL, no shearing for that dimension; if the parameter is NULL, no shearing applies.

      `reflection` - Defines the axis about which the image is reflected, 1 represent X axis, and 2 for Y axis. If it is NULL, no reflection applies.

      `storageParam` - A string specifying storage parameters for the result.

      `outGeoRaster` - GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Empty Raster Blocks). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `parallelParam` - Specifies the degree of parallelism for the operation. If specified, must be greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### affineTransform

          public void affineTransform(SdoGeoRaster inGeoRaster,
                                      double[] translation,
                                      double[] scales,
                                      double[] rotatePoint,
                                      java.lang.Double rotateAngle,
                                      double[] shear,
                                      java.lang.Integer reflection,
                                      java.lang.String storageParam,
                                      java.sql.Blob[] rasterBlob,
                                      JGeometry[] outArea,
                                      long[] outWindow,
                                      double[] bgValues)
                               throws java.lang.Exception

      Apply affine geometric trasnformation on GeoRaster Objects
      Parameters:
      `inGeoRaster` - GeoRaster object on which to perform the operation

      `translation` - An array of numbers contains the shift in x and y directions. If it is NULL, no translation happens.

      `scales` - An array of numbers contains the multiplication factors of image row and column. The first number is for column, and the second for row. If any one is NULL, no scale for that dimension; if the parameter is NULL, no scale applies.

      `rotatePoint` - Defines the point (X,Y) about which to rotate; if new use the default point (0,0).

      `rotateAngle` - The angle to rotate. If is NULL no rotation applies.

      `shear` - Array of numbers contains the shearing in x and y directions. The first number is X axis, and the second for Y axis. If any one is NULL, no shearing for that dimension; if the parameter is NULL, no shearing applies.

      `reflection` - Defines the axis about which the image is reflected, 1 represent X axis, and 2 for Y axis. If it is NULL, no reflection applies.

      `storageParam` - A string specifying storage parameters for the result.

      `rasterBlob` - BLOB to hold the output reflecting the rectification. It must exist or have been initialized before the operation.

      `outArea` - An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Throws:
      `java.lang.Exception`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SdoGeorIpPKG.md)
- [Next Class](SdoGeorPKG.SdoGeorGCP.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
