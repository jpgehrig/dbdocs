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

- [Prev Class](SdoGeorAdminPKG.md)
- [Next Class](SdoGeoRaster.md)

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

## Class SdoGeorAggrPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorAggrPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorAggrPKG
      extends java.lang.Object

  SdoGeorAggrPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR_AGGR. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorAggrPKG
         SdoGeorAggrPKG  pkg=new SdoGeorAggrPKG(connection);
         //reading a GeoRaster object from database based on a query
         Statement stmt = connection.createStatement();
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         rs.next();
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster = new SdoGeoRaster(geor);
         rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=2");
         rs.next();
         geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster1 = new SdoGeoRaster(geor);
         //Appends the source GeoRaster object to the target GeoRaster object.
         pkg.append(sdoGeoRaster,sdoGeoRaster1,0,null,null);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------|
    | `SdoGeorAggrPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorAggrPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |--------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                     | `append``(`[`SdoGeoRaster`](SdoGeoRaster.md)` targetGeoRaster, `[`SdoGeoRaster`](SdoGeoRaster.md)` sourceGeoRaster, java.lang.Integer sourcePyramidLevel, java.lang.String appendParam, double[] bgValues)`<br>Appends the source GeoRaster object to the target GeoRaster object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.sql.Connection`                      | `getConnection``()`<br>Returns a connection which points to target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`JGeometry`](../../geometry/JGeometry.md) | `getMosaicExtent``(java.lang.String inGeoRasters, java.lang.Integer outSRID)`<br>Calculates and returns the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`JGeometry`](../../geometry/JGeometry.md) | `getMosaicExtent``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer outSRID)`<br>Calculates and returns the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `double[]`                                 | `getMosaicResolutions``(java.lang.String inGeoRasters, java.lang.String resolutionUnit)`<br>Returns the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `double[]`                                 | `getMosaicResolutions``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.String resolutionUnit)`<br>Returns the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                     | `getMosaicStatistics``(java.lang.String inGeoRasters, int skipFactor, boolean genHistogram, double[][][] outStatistics, `[`GeorHistogram`](../GeorHistogram.md)`[][] outHistograms)`<br>Returns the statistics of a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                     | `getMosaicStatistics``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, int skipFactor, boolean genHistogram, double[][][] outStatistics, `[`GeorHistogram`](../GeorHistogram.md)`[][] outHistograms)`<br>Returns the statistics of a virtual mosaic or a collection of GeoRaster objects                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `java.sql.Blob`                            | `getMosaicSubset``(java.lang.String inGeoRasters, java.lang.Integer pyramidLevel, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, java.lang.String storageParam, double[] bgValues)`<br>Performs subsetting over a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                                                                    |
    | `java.sql.Blob`                            | `getMosaicSubset``(java.lang.String inGeoRasters, java.lang.Integer pyramidLevel, java.lang.String elevationParam, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, java.lang.String storageParam, double[] bgValues, `[`SdoGeoRaster`](SdoGeoRaster.md)` referenceImage, double[] referenceValue1, double[] referenceValue2, `[`GeorHistogram`](../GeorHistogram.md)`[] referenceHistograms)`<br>Performs subsetting over a virtual mosaic or a collection of GeoRaster objects.                                                                           |
    | `java.sql.Blob`                            | `getMosaicSubset``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer pyramidLevel, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, java.lang.String storageParam, double[] bgValues)`<br>Performs subsetting over a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                      |
    | `java.sql.Blob`                            | `getMosaicSubset``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer pyramidLevel, java.lang.String elevationParam, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, long[] outWindow, java.lang.String storageParam, double[] bgValues, `[`SdoGeoRaster`](SdoGeoRaster.md)` referenceImage, double[] referenceValue1, double[] referenceValue2, `[`GeorHistogram`](../GeorHistogram.md)`[] referenceHistograms)`<br>Performs subsetting over a virtual mosaic or a collection of GeoRaster objects.                             |
    | `void`                                     | `mosaicSubset``(java.lang.String inGeoRasters, java.lang.Integer pyramidLevel, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelDegree)`<br>Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                                                                        |
    | `void`                                     | `mosaicSubset``(java.lang.String inGeoRasters, java.lang.Integer pyramidLevel, java.lang.String elevationParam, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelDegree, `[`SdoGeoRaster`](SdoGeoRaster.md)` referenceImage, double[] referenceValue1, double[] referenceValue2, `[`GeorHistogram`](../GeorHistogram.md)`[] referenceHistograms)`<br>Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects.                                               |
    | `void`                                     | `mosaicSubset``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer pyramidLevel, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelDegree)`<br>Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects.                                                                                                                                                                                                          |
    | `void`                                     | `mosaicSubset``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer pyramidLevel, java.lang.String elevationParam, java.lang.Integer outSRID, java.lang.Integer outModelCoordLoc, `[`JGeometry`](../../geometry/JGeometry.md)` referencePoint, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, boolean polygonClip, boolean boundaryClip, java.lang.String layerNumbers, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String mosaicParam, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, int parallelDegree, `[`SdoGeoRaster`](SdoGeoRaster.md)` referenceImage, double[] referenceValue1, double[] referenceValue2, `[`GeorHistogram`](../GeorHistogram.md)`[] referenceHistograms)`<br>Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. |
    | `void`                                     | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                     | `validateForMosaicSubset``(java.lang.String inGeoRasters, java.lang.Integer outSRID, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String resultTableName)`<br>Checks if it is feasible to do mosaicking or subset query operations over a virtual mosaic or a large collection of GeoRaster objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                     | `validateForMosaicSubset``(java.lang.String georasterTableNames, java.lang.String georasterColumnNames, java.lang.Integer outSRID, double[] outResolutions, java.lang.String resolutionUnit, java.lang.String resultTableName)`<br>Checks if it is feasible to do mosaicking or subset query operations over a virtual mosaic or a large collection of GeoRaster objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoGeorAggrPKG

          public SdoGeorAggrPKG(java.sql.Connection conn)

      Constructs an `SdoGeorAggrPKG` object using the given connection.
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

    - #### append

          public void append(SdoGeoRaster targetGeoRaster,
                             SdoGeoRaster sourceGeoRaster,
                             java.lang.Integer sourcePyramidLevel,
                             java.lang.String appendParam,
                             double[] bgValues)
                      throws java.lang.Exception

      Appends the source GeoRaster object to the target GeoRaster object. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `targetGeoRaster` - GeoRaster object to be updated. Cannot be the same as sourceGeoRaster. (Be sure to make a copy of this object before you update it.)

      `sourceGeoRaster` - GeoRaster object to be appended to targetGeoRaster.

      `sourcePyramidLevel` - Pyramid level of the source GeoRaster object to be appended at the target GeoRaster object pyramid Level 0. If NULL, pyramid level 0 is used.

      `appendParam` - A comma-separated quoted string of keyword=value pairs for specifying parameters for the operation. It can contain one or more of the keywords in Table 8-1 "mosaicParam Keywords" of Spatial GeoRaster Developer's Guide in the SDO_GEOR_AGGR.mosaicSubset reference section. If a nondefault value for colorBalance is specified, it is performed on the source GeoRaster object using the target GeoRaster object's statistics as the reference, and the following keywords (if specified) are ignored: maxVal, minVal, std, and min.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4 of Spatial GeoRaster Developer's Guide). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicExtent

          public JGeometry getMosaicExtent(java.lang.String georasterTableNames,
                                           java.lang.String georasterColumnNames,
                                           java.lang.Integer outSRID)
                                    throws java.lang.Exception

      Calculates and returns the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If this parameter is null (the default), 4326 (EPSG SRID value for the WGS 84 (longitude/latitude) coordinate system) is used.

      Returns:
      a JGeometry object that is the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicExtent

          public JGeometry getMosaicExtent(java.lang.String inGeoRasters,
                                           java.lang.Integer outSRID)
                                    throws java.lang.Exception

      Calculates and returns the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If this parameter is null (the default), 4326 (EPSG SRID value for the WGS 84 (longitude/latitude) coordinate system) is used.

      Returns:
      a JGeometry object that is the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicResolutions

          public double[] getMosaicResolutions(java.lang.String inGeoRasters,
                                               java.lang.String resolutionUnit)
                                        throws java.lang.Exception

      Returns the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `resolutionUnit` - Unit of measure for the returned resolution range. If specified, it must be a quoted string in the format 'unit=value' where value is the unit name. If not specified or null, the returned resolution range is in the unit of meter.

      Returns:
      a double array which stores the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicResolutions

          public double[] getMosaicResolutions(java.lang.String georasterTableNames,
                                               java.lang.String georasterColumnNames,
                                               java.lang.String resolutionUnit)
                                        throws java.lang.Exception

      Returns the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `resolutionUnit` - Unit of measure for the returned resolution range. If specified, it must be a quoted string in the format 'unit=value' where value is the unit name. If not specified or null, the returned resolution range is in the unit of meter.

      Returns:
      a double array which stores the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicStatistics

          public void getMosaicStatistics(java.lang.String inGeoRasters,
                                          int skipFactor,
                                          boolean genHistogram,
                                          double[][][] outStatistics,
                                          GeorHistogram[][] outHistograms)
                                   throws java.lang.Exception

      Returns the statistics of a virtual mosaic or a collection of GeoRaster objects.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `skipFactor` - number indicating every nth image to be used for calculating the statistics, if null, defaults to 1

      `genHistogram` - Whether to generate and return the histograms, if null, defaults to false.

      `outStatistics` - The output statistics, it is an array of statistics for all bands from band 0 to band n. For each band, if genHistogram parameter is false, the statistics has (min,max,mean,std) accordingly; if genHistogram parameter is true, The statistics has (min,max,mean,std,median,mode) accordingly.

      `outHistograms` - The output Histograms for all bands in an array. Returned when genHistogram parameter is true, otherwise, null is returned. For example double\[\]\[\]\[\] stats = new double\[1\]\[\]\[\]; GeorHistogram\[\]\[\] hists = new GeorHistogram\[1\]\[\]; aggrPKG.getMosaicStatistics("select image from images_table", 1, false, stats, hists);

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicStatistics

          public void getMosaicStatistics(java.lang.String georasterTableNames,
                                          java.lang.String georasterColumnNames,
                                          int skipFactor,
                                          boolean genHistogram,
                                          double[][][] outStatistics,
                                          GeorHistogram[][] outHistograms)
                                   throws java.lang.Exception

      Returns the statistics of a virtual mosaic or a collection of GeoRaster objects
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `skipFactor` - number indicating every nth image to be used for calculating the statistics, if null, defaults to 1

      `genHistogram` - Whether to generate and return the histograms, if null, defaults to false.

      `outStatistics` - The output statistics, it is an array of statistics for all bands from band 0 to band n. For each band, if genHistogram parameter is false, the statistics has (min,max,mean,std) accordingly; if genHistogram parameter is true, The statistics has (min,max,mean,std,median,mode) accordingly.

      `outHistograms` - The output Histograms for all bands in an array. Returned when genHistogram parameter is true, otherwise, null is returned. For example double\[\]\[\]\[\] stats = new double\[1\]\[\]\[\]; GeorHistogram\[\]\[\] hists = new GeorHistogram\[1\]\[\]; aggrPKG.getMosaicStatistics("images_table", "image", 1, false, stats, hists);

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicSubset

          public java.sql.Blob getMosaicSubset(java.lang.String inGeoRasters,
                                               java.lang.Integer pyramidLevel,
                                               java.lang.Integer outSRID,
                                               java.lang.Integer outModelCoordLoc,
                                               JGeometry referencePoint,
                                               JGeometry cropArea,
                                               boolean polygonClip,
                                               boolean boundaryClip,
                                               java.lang.String layerNumbers,
                                               double[] outResolutions,
                                               java.lang.String resolutionUnit,
                                               java.lang.String mosaicParam,
                                               JGeometry[] outArea,
                                               long[] outWindow,
                                               java.lang.String storageParam,
                                               double[] bgValues)
                                        throws java.lang.Exception

      Performs subsetting over a virtual mosaic or a collection of GeoRaster objects. It performs mosaic operations dynamically for the queried area and returns the required result in a BLOB on-the-fly. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `outArea` - Geometry object that describes the extent of the output data.

      `outWindow` - An array to hold the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Returns:
      an BLOB (binary large object) to hold the result of the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicSubset

          public java.sql.Blob getMosaicSubset(java.lang.String inGeoRasters,
                                               java.lang.Integer pyramidLevel,
                                               java.lang.String elevationParam,
                                               java.lang.Integer outSRID,
                                               java.lang.Integer outModelCoordLoc,
                                               JGeometry referencePoint,
                                               JGeometry cropArea,
                                               boolean polygonClip,
                                               boolean boundaryClip,
                                               java.lang.String layerNumbers,
                                               double[] outResolutions,
                                               java.lang.String resolutionUnit,
                                               java.lang.String mosaicParam,
                                               JGeometry[] outArea,
                                               long[] outWindow,
                                               java.lang.String storageParam,
                                               double[] bgValues,
                                               SdoGeoRaster referenceImage,
                                               double[] referenceValue1,
                                               double[] referenceValue2,
                                               GeorHistogram[] referenceHistograms)
                                        throws java.lang.Exception

      Performs subsetting over a virtual mosaic or a collection of GeoRaster objects. It performs mosaic operations dynamically for the queried area and returns the required result in a BLOB on-the-fly. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `elevationParam` - A string containing one or more of the elevation parameter average (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, 'average=800'). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for average. The use of the elevationParam parameter requires that the input GeoRaster objects have a 3D model SRID.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE value causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE value causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `outArea` - Geometry object that describes the extent of the output data.

      `outWindow` - An array to hold the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `referenceImage` - Specifies the reference image used during the color balance operation. If null, it defaults to the first image from the query.

      `referenceValue1` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceValue2` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceHistograms` - Specifies the reference histograms used during the color balance operation.

      Returns:
      an BLOB (binary large object) to hold the result of the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicSubset

          public java.sql.Blob getMosaicSubset(java.lang.String georasterTableNames,
                                               java.lang.String georasterColumnNames,
                                               java.lang.Integer pyramidLevel,
                                               java.lang.Integer outSRID,
                                               java.lang.Integer outModelCoordLoc,
                                               JGeometry referencePoint,
                                               JGeometry cropArea,
                                               boolean polygonClip,
                                               boolean boundaryClip,
                                               java.lang.String layerNumbers,
                                               double[] outResolutions,
                                               java.lang.String resolutionUnit,
                                               java.lang.String mosaicParam,
                                               JGeometry[] outArea,
                                               long[] outWindow,
                                               java.lang.String storageParam,
                                               double[] bgValues)
                                        throws java.lang.Exception

      Performs subsetting over a virtual mosaic or a collection of GeoRaster objects. It performs mosaic operations dynamically for the queried area and returns the required result in a BLOB on-the-fly. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `outArea` - Geometry object that describes the extent of the output data.

      `outWindow` - An array to hold the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      Returns:
      an BLOB (binary large object) to hold the result of the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMosaicSubset

          public java.sql.Blob getMosaicSubset(java.lang.String georasterTableNames,
                                               java.lang.String georasterColumnNames,
                                               java.lang.Integer pyramidLevel,
                                               java.lang.String elevationParam,
                                               java.lang.Integer outSRID,
                                               java.lang.Integer outModelCoordLoc,
                                               JGeometry referencePoint,
                                               JGeometry cropArea,
                                               boolean polygonClip,
                                               boolean boundaryClip,
                                               java.lang.String layerNumbers,
                                               double[] outResolutions,
                                               java.lang.String resolutionUnit,
                                               java.lang.String mosaicParam,
                                               JGeometry[] outArea,
                                               long[] outWindow,
                                               java.lang.String storageParam,
                                               double[] bgValues,
                                               SdoGeoRaster referenceImage,
                                               double[] referenceValue1,
                                               double[] referenceValue2,
                                               GeorHistogram[] referenceHistograms)
                                        throws java.lang.Exception

      Performs subsetting over a virtual mosaic or a collection of GeoRaster objects. It performs mosaic operations dynamically for the queried area and returns the required result in a BLOB on-the-fly. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `elevationParam` - A string containing one or more of the elevation parameter average (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, 'average=800'). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for average. The use of the elevationParam parameter requires that the input GeoRaster objects have a 3D model SRID.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `outArea` - Geometry object that describes the extent of the output data.

      `outWindow` - An array to hold the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `referenceImage` - Specifies the reference image used during the color balance operation. If null, it defaults to the first image from the query.

      `referenceValue1` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceValue2` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceHistograms` - Specifies the reference histograms used during the color balance operation.

      Returns:
      an BLOB (binary large object) to hold the result of the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mosaicSubset

          public void mosaicSubset(java.lang.String inGeoRasters,
                                   java.lang.Integer pyramidLevel,
                                   java.lang.Integer outSRID,
                                   java.lang.Integer outModelCoordLoc,
                                   JGeometry referencePoint,
                                   JGeometry cropArea,
                                   boolean polygonClip,
                                   boolean boundaryClip,
                                   java.lang.String layerNumbers,
                                   double[] outResolutions,
                                   java.lang.String resolutionUnit,
                                   java.lang.String mosaicParam,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   int parallelDegree)
                            throws java.lang.Exception

      Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. The output data is written into a GeoRaster object for persistent storage or other processing. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects. corresponding to the table names in georasterTableNames.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `outGeoRaster` - Output GeoRaster object

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mosaicSubset

          public void mosaicSubset(java.lang.String inGeoRasters,
                                   java.lang.Integer pyramidLevel,
                                   java.lang.String elevationParam,
                                   java.lang.Integer outSRID,
                                   java.lang.Integer outModelCoordLoc,
                                   JGeometry referencePoint,
                                   JGeometry cropArea,
                                   boolean polygonClip,
                                   boolean boundaryClip,
                                   java.lang.String layerNumbers,
                                   double[] outResolutions,
                                   java.lang.String resolutionUnit,
                                   java.lang.String mosaicParam,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   int parallelDegree,
                                   SdoGeoRaster referenceImage,
                                   double[] referenceValue1,
                                   double[] referenceValue2,
                                   GeorHistogram[] referenceHistograms)
                            throws java.lang.Exception

      Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. The output data is written into a GeoRaster object for persistent storage or other processing. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects. corresponding to the table names in georasterTableNames.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `elevationParam` - A string containing one or more of the elevation parameter average (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, 'average=800'). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for average. The use of the elevationParam parameter requires that the input GeoRaster objects have a 3D model SRID.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `outGeoRaster` - Output GeoRaster object

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      `referenceImage` - Specifies the reference image used during the color balance operation. If null, it defaults to the first image from the query.

      `referenceValue1` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceValue2` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceHistograms` - Specifies the reference histograms used during the color balance operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mosaicSubset

          public void mosaicSubset(java.lang.String georasterTableNames,
                                   java.lang.String georasterColumnNames,
                                   java.lang.Integer pyramidLevel,
                                   java.lang.Integer outSRID,
                                   java.lang.Integer outModelCoordLoc,
                                   JGeometry referencePoint,
                                   JGeometry cropArea,
                                   boolean polygonClip,
                                   boolean boundaryClip,
                                   java.lang.String layerNumbers,
                                   double[] outResolutions,
                                   java.lang.String resolutionUnit,
                                   java.lang.String mosaicParam,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   int parallelDegree)
                            throws java.lang.Exception

      Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. The output data is written into a GeoRaster object for persistent storage or other processing. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point in JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `outGeoRaster` - Output GeoRaster object

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### mosaicSubset

          public void mosaicSubset(java.lang.String georasterTableNames,
                                   java.lang.String georasterColumnNames,
                                   java.lang.Integer pyramidLevel,
                                   java.lang.String elevationParam,
                                   java.lang.Integer outSRID,
                                   java.lang.Integer outModelCoordLoc,
                                   JGeometry referencePoint,
                                   JGeometry cropArea,
                                   boolean polygonClip,
                                   boolean boundaryClip,
                                   java.lang.String layerNumbers,
                                   double[] outResolutions,
                                   java.lang.String resolutionUnit,
                                   java.lang.String mosaicParam,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   int parallelDegree,
                                   SdoGeoRaster referenceImage,
                                   double[] referenceValue1,
                                   double[] referenceValue2,
                                   GeorHistogram[] referenceHistograms)
                            throws java.lang.Exception

      Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. The output data is written into a GeoRaster object for persistent storage or other processing. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables

      `pyramidLevel` - Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the outResolutions parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the outResolutions parameter.

      `elevationParam` - A string containing one or more of the elevation parameter average (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, 'average=800'). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for average. The use of the elevationParam parameter requires that the input GeoRaster objects have a 3D model SRID.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outModelCoordLoc` - A value specifying the model location of the base of the area represented by a cell: 0 for CENTER or 1 for UPPERLEFT. If null, CENTER is used.

      `referencePoint` - A point JGeometry type used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the referencePoint and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the cropArea, or when the cropArea is null, the upper-left corner of the output extent.

      `cropArea` - Crop area definition. If the JGeometry object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If polygonClip is FALSE, the MBR of the cropArea is used to crop the mosaicked data. If polygonClip is TRUE, the geometry of the cropArea is used to crop the mosaicked data.

      `polygonClip` - The TRUE causes the cropArea value to be used to crop the mosaicked data; the FALSE causes the MBR of the cropArea to be used to crop the mosaicked data.

      `boundaryClip` - The TRUE causes the boundary of the virtual mosaic to be used to clip the cropArea; the FALSE causes the area that is outside the virtual mosaic but within the cropArea to be filled with the background value.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 8-1, "mosaicParam Keywords" in the SDO_GEOR_AGGR.mosaicSubset reference section.

      `storageParam` - A string specifying storage parameters, as explained in Section 1.4.1. If this parameter is null, the resulting GeoRaster object has the same storage parameters (blockSize, cellDepth, interleaving, and compression) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

      `outGeoRaster` - Output GeoRaster object

      `bgValues` - Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see Section 1.4.4). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0).

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      `referenceImage` - Specifies the reference image used during the color balance operation. If null, it defaults to the first image from the query.

      `referenceValue1` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceValue2` - Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

      `referenceHistograms` - Specifies the reference histograms used during the color balance operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateForMosaicSubset

          public void validateForMosaicSubset(java.lang.String inGeoRasters,
                                              java.lang.Integer outSRID,
                                              double[] outResolutions,
                                              java.lang.String resolutionUnit,
                                              java.lang.String resultTableName)
                                       throws java.lang.Exception

      Checks if it is feasible to do mosaicking or subset query operations over a virtual mosaic or a large collection of GeoRaster objects. Any validation errors and notes are stored in a user-created result table.
      Parameters:
      `inGeoRasters` - SQL query string for the input GeoRaster objects.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `resultTableName` - Name of the validation result table. This table must already exist, and it must have the following column definitions: time timestamp, type varchar2(16), description varchar2(512), table_name varchar2(130), column_name varchar2(1024), rdt_table_name varchar2(130), raster_id number

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateForMosaicSubset

          public void validateForMosaicSubset(java.lang.String georasterTableNames,
                                              java.lang.String georasterColumnNames,
                                              java.lang.Integer outSRID,
                                              double[] outResolutions,
                                              java.lang.String resolutionUnit,
                                              java.lang.String resultTableName)
                                       throws java.lang.Exception

      Checks if it is feasible to do mosaicking or subset query operations over a virtual mosaic or a large collection of GeoRaster objects. Any validation errors and notes are stored in a user-created result table.
      Parameters:
      `georasterTableNames` - Names (comma-separated) of the tables containing the source GeoRaster objects.

      `georasterColumnNames` - Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in georasterTableNames.

      `outSRID` - Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

      `outResolutions` - Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

      `resolutionUnit` - The unit of the outResolutions parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if outResolutions is null.

      `resultTableName` - Name of the validation result table. This table must already exist, and it must have the following column definitions: time timestamp, type varchar2(16), description varchar2(512), table_name varchar2(130), column_name varchar2(1024), rdt_table_name varchar2(130), raster_id number

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

- [Prev Class](SdoGeorAdminPKG.md)
- [Next Class](SdoGeoRaster.md)

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
