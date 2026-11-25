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

- [Prev Class](JGeoRasterMeta.md)
- [Next Class](JRaster.md)

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

## Class JGeoRasterVM

- java.lang.Object

- - oracle.spatial.georaster.JGeoRasterVM

<!-- -->

-

  ------------------------------------------------------------------------



      public class JGeoRasterVM
      extends java.lang.Object

  JGeoRasterVM supports the definition of a GeoRaster virtual mosaic for the purpose of displaying a collection of images as a single one without storing the resulting image and supporting most of the same visualization options as if it was a single image.
  A GeoRaster virtual mosaic is defined by:

           * A GeoRaster table or a list of GeoRaster tables and a GeoRaster column or a list of GeoRaster columns
           * A condition for each table/view is optional. If not informed, the whole table/view will used.
             from the table(s) listed (see GeoRaster Developer's Guide Section 5.16.1).
           * A database view with a GeoRaster column (see GeoRaster Developer's Guide Section 5.16.2).
           * A SQL query statement (a cursor) that results in a collection of GeoRaster objects (see GeoRaster Developer's
             Guide Section 5.16.3).


  Regardless of how the JGeoRasterVM is defined, the GeoRaster objects in the virtual mosaic collection must all have the spatialExtent attribute defined, or they will not participated on the resulting virtual mosaic.

  There are four construtors of that class:

           JGeoRasterVM(Connection connection, String[] tables, String[] columns, String[] conditions, String srid,
                        MosaicParameters mosaicParam)
           JGeoRasterVM(Connection connection, String[] tables, String[] columns, String[] conditions, String srid,
                        MosaicParameters mosaicParam,
                        double[] resolutions, String resolutionUnit)
           JGeoRasterVM(Connection connection, String sql, MosaicParameters mosaicParam)
           JGeoRasterVM(Connection connection, String sql, MosaicParameters mosaicParam,
                        double[] resolutions, String resolutionUnit)


  See each constructor's documentation for more details.

  Here is an example showing how to use the constructor by passing a list of table or views, the sdo_georaster column names and a condition for each instance table/view:

           String[] tables_or_views = { "table1", "table2" };
           String[] georaster_columns = { "image", "raster" };
           String[] conditions = { "year < 2000", "code = 'K1'" };
           MosaicParameters param = new MosaicParameters();
           param.setFillGap(true);
           param.setIncludeNODATA(true);
           JGeoRasterVM geoRasterVM = new JGeoRasterVM( connection, tables_or_views, georaster_columns, conditions, "4326",
                                                        param );


  In that example the resolution of the virtual mosaic will be calculated automatically. But the resolution can be enforced by using another constructor, for example:

           String[] tables_or_views = { "table1", "table2" };
           String[] georaster_columns = { "image", "raster" };
           MosaicParameters param = new MosaicParameters();
           param.setFillGap(true);
           param.setIncludeNODATA(true);
           double[] resolutions = { 30, 30 };
           JGeoRasterVM geoRasterVM = new JGeoRasterVM( connection, tables_or_views, georaster_columns, null, "4326",
                                                        param, resolutions, "meters" );



  Here is an example showing how to use the constructor by passing a SQL query:

           String georaster_query = "select image from table1 where id < 1000";
           MosaicParameters param = new MosaicParameters();
           param.setFillGap(true);
           param.setNODATA(true);
           JGeoRasterVM geoRasterVM = new JGeoRasterVM( connection, georaster_quey, "4326", param );


  When a constructor is invoked the following takes will be process:

           * A query will be executed to locate the first valid GeoRaster object,
             calculate the full dimensions of the resulting mosaic image
           * if the resolutions parameter was not informed it will be calculated automatically.
           * If the resolutionUnit was informed it will be automatically calculated based on the srid unit.


  If the parameter srid is not informed, the JGeoRasterVM object will assume the SRID of the first GeoRaster found on the first table or view, or the first GeoRaster found on the SQL query provided by the user.

  Before creating a JGeoRasterVM object it is possible to validate it. See SdoGeoRasterPKG validateForMosaicSubset for more details.

  After a JGeoRasterVM is succesfully initialized it is possible to get an instance of GeoRasterImage to deal with visualization as shown in this example:

           String[] tables_or_views = { "table1", "table2" };
           String[] georaster_columns = { "image", "raster" };
           String[] conditions = { "state = 'CB'", "area > 5000" };
           MosaicParameters param = new MosaicParameters();
           param.setFillGap(true);
           param.setNODATA(true);
           int pyramidLevel = 1;
           long dspWidth = 512;
           long dspHeight = 512;
           JGeoRasterVM geoRasterVM = new JGeoRasterVM( connection, tables_or_views, georaster_columns, conditions, "4326", param);

           GeoRasterImage rasterImg = new GeoRasterImage(geoRasterVM, param);
           RenderedImage renderedImg = rasterImg.getRasterImage(pyramidLevel, 1, 1, dspWidth, dspHeight, null);


<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `CHUNKSIZE`           |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JGeoRasterVM``(java.sql.Connection connection, java.lang.String[] tables, java.lang.String[] columns, java.lang.String[] conditions, java.lang.String srid, `[`MosaicParameters`](util/MosaicParameters.md)` mosaicParam)`<br>Virtual Mosaic constructor.                                                        |
    | `JGeoRasterVM``(java.sql.Connection connection, java.lang.String[] tables, java.lang.String[] columns, java.lang.String[] conditions, java.lang.String srid, `[`MosaicParameters`](util/MosaicParameters.md)` mosaicParam, double[] resolutions, java.lang.String resolutionUnit)`<br>Virtual Mosaic constructor. |
    | `JGeoRasterVM``(java.sql.Connection connection, java.lang.String sqlQuery, java.lang.String srid, `[`MosaicParameters`](util/MosaicParameters.md)` mosaicParam)`<br>Virtual Mosaic constructor.                                                                                                                   |
    | `JGeoRasterVM``(java.sql.Connection connection, java.lang.String sqlQuery, java.lang.String srid, `[`MosaicParameters`](util/MosaicParameters.md)` mosaicParam, double[] resolutions, java.lang.String resolutionUnit)`<br>Virtual Mosaic constructor.                                                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`                                         | `getBandCount``()`<br>Get the band dimension of the Virtual Mosaic object.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `java.lang.String`                             | `getColumnNames``()`<br>Return the list of columns names                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `java.sql.Connection`                          | `getConnection``()`<br>Return the current sql connection                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `java.lang.String`                             | `getElevationParam``()`<br>Get elevation Parameters                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `double[]`                                     | `getExtent``()`<br>Get the Virtual Mosaic extent                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `double`                                       | `getExtent``(int index)`<br>Get one of the Virtual Mosaic extent values                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`JGeoRaster`](JGeoRaster.md)                  | `getFirstGeoRasterObject``()`<br>Return the first GeoRaster object found on the virtual mosaic                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`GeorHistogram`](GeorHistogram.md)            | `getHistogram``(int layer)`<br>Get the histogram data                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`JGeoRasterMeta`](JGeoRasterMeta.md)          | `getMetadataObject``()`<br>Returns the JGeoRasterMeta object contained in this JGeoRasterVM object.                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`MosaicParameters`](util/MosaicParameters.md) | `getMosaicParameters``()`<br>Return the active MosaicPameters                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `byte[]`                                       | `getMosaicSubset``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, int numBands, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, java.lang.String outSRID, long[] outWindow, double[] bgValues)`<br>This private method performs the same operation as JRaster.getRasterSubset but for Virtual Mosaic and it should only be called by getRasterImageVM at this point. |
    | [`JGeometry`](../geometry/JGeometry.md)        | `getOutArea``()`<br>Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the virtual mosaic                                                                                                                                                                                                                                                                                                                                        |
    | [`GeorHistogram`](GeorHistogram.md)`[]`        | `getReferenceHistograms``()`<br>Get reference histogram                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`SdoGeoRaster`](sql/SdoGeoRaster.md)          | `getReferenceImage``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `double[]`                                     | `getReferenceValue1``()`<br>Get reference value 1                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `double[]`                                     | `getReferenceValue2``()`<br>Get reference value 2                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `double[]`                                     | `getResolutionRange``()`<br>Get the Virtual Mosaic resolution range                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `double`                                       | `getResolutionRange``(int index)`<br>Get one of the Virtual Mosaic resolution range                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `double`                                       | `getResolutions``(int index)`<br>Get one of the Virtual Mosaic base resolution values, the resolution used when the object was created.                                                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                             | `getSqlQuery``()`<br>Return the SQL query, if exist                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.lang.String`                             | `getSrid``()`<br>Return the current SRID of the Virtual Mosaic object                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `double[]`                                     | `getStatistics``(int layer)`<br>Get the statistics data                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                             | `getTableNames``()`<br>Return the list of tables names                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                         | `refresh``()`<br>Recalculate the extents and resolutions of the virtual mosaic based on the attributes provided in the constructor                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                         | `setConnection``(java.sql.Connection connection)`<br>Set a current valid connection to the JGeoRasterVM object to be used in subsequent getRasterSubset requests.                                                                                                                                                                                                                                                                                                                         |
    | `void`                                         | `setElevationParam``(java.lang.String elevationParam)`<br>Set elevation Parameters                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                         | `setMosaicParameters``(`[`MosaicParameters`](util/MosaicParameters.md)` mosaicParams)`<br>Set the parameters for virtual mosaiac                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                         | `setReferenceHistograms``(`[`GeorHistogram`](GeorHistogram.md)`[] referenceHistograms)`<br>Set reference histogram                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                         | `setReferenceImage``(`[`SdoGeoRaster`](sql/SdoGeoRaster.md)` referenceImage)`                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                         | `setReferenceValue1``(double[] referenceValue1)`<br>Set reference value 1                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                         | `setReferenceValue2``(double[] referenceValue2)`<br>Set reference value 2                                                                                                                                                                                                                                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### CHUNKSIZE

          public static final int CHUNKSIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### JGeoRasterVM

          public JGeoRasterVM(java.sql.Connection connection,
                              java.lang.String[] tables,
                              java.lang.String[] columns,
                              java.lang.String[] conditions,
                              java.lang.String srid,
                              MosaicParameters mosaicParam,
                              double[] resolutions,
                              java.lang.String resolutionUnit)
                       throws GeoRasterException

      Virtual Mosaic constructor.
      Parameters:
      `connection` - database connection

      `tables` - array of GeoRaster table and/or view names

      `columns` - array of GeoRaster columns names, one for each table

      `conditions` - array of query conditions, one for each table. The parameter can be null or one individal element can also be null.

      `srid` - (optional) output srid

      `mosaicParam` - A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters (see setMosaicParameters).

      `resolutions` - array of output resolutions (X and Y)

      `resolutionUnit` - unit of the given resolutions

      Throws:
      `java.lang.Exception`

      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### JGeoRasterVM

          public JGeoRasterVM(java.sql.Connection connection,
                              java.lang.String[] tables,
                              java.lang.String[] columns,
                              java.lang.String[] conditions,
                              java.lang.String srid,
                              MosaicParameters mosaicParam)
                       throws GeoRasterException

      Virtual Mosaic constructor.
      Parameters:
      `connection` - database connection

      `tables` - array of GeoRaster table and/or view names

      `columns` - array of GeoRaster columns names

      `conditions` - array of query conditions, one for each table. The parameter can be null or one individal element can also be null.

      `srid` - valid srid

      `mosaicParam` - mosaic parameters

      Throws:
      `java.lang.Exception`

      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### JGeoRasterVM

          public JGeoRasterVM(java.sql.Connection connection,
                              java.lang.String sqlQuery,
                              java.lang.String srid,
                              MosaicParameters mosaicParam,
                              double[] resolutions,
                              java.lang.String resolutionUnit)
                       throws GeoRasterException

      Virtual Mosaic constructor.
      Parameters:
      `connection` - database connection

      `sqlQuery` - a SQL query

      `srid` - SRID of the VirtualMosaic

      `mosaicParam` - mosaic parameters

      `resolutions` - array of output resolutions (X and Y)

      `resolutionUnit` - unit of the given resolutions

      Throws:
      `java.lang.Exception`

      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### JGeoRasterVM

          public JGeoRasterVM(java.sql.Connection connection,
                              java.lang.String sqlQuery,
                              java.lang.String srid,
                              MosaicParameters mosaicParam)
                       throws GeoRasterException

      Virtual Mosaic constructor.
      Parameters:
      `connection` - database connection

      `sqlQuery` - a SQL query

      `srid` - SRID of the VirtualMosaic

      `mosaicParam` - mosaic parameters

      Throws:
      `java.lang.Exception`

      [`GeoRasterException`](GeoRasterException.md)

  <!-- -->

  - ### Method Detail

    - #### getMetadataObject

          public JGeoRasterMeta getMetadataObject()

      Returns the JGeoRasterMeta object contained in this JGeoRasterVM object.
      Returns:
      JGeoRasterMeta object contained in this JGeoRasterVM object.

    <!-- -->

    - #### getExtent

          public double[] getExtent()

      Get the Virtual Mosaic extent
      Returns:
      the Virtual Mosaic extent

    <!-- -->

    - #### getStatistics

          public double[] getStatistics(int layer)

      Get the statistics data
      Parameters:
      `layer` - layer number

      Returns:
      statistics data for specified layer

    <!-- -->

    - #### getHistogram

          public GeorHistogram getHistogram(int layer)

      Get the histogram data
      Parameters:
      `layer` - layer number

      Returns:
      histogram data for specified layer

    <!-- -->

    - #### getExtent

          public double getExtent(int index)

      Get one of the Virtual Mosaic extent values
      Parameters:
      `index` - of the requested resolution as follows: 0 for minimum X 1 for minimum Y 2 for maximum X 3 for maximum Y

      Returns:
      one of the Virtual Mosaic extent values

    <!-- -->

    - #### getResolutionRange

          public double[] getResolutionRange()

      Get the Virtual Mosaic resolution range
      Returns:
      the resolution of the virtual mosaic

    <!-- -->

    - #### getResolutionRange

          public double getResolutionRange(int index)

      Get one of the Virtual Mosaic resolution range
      Parameters:
      `index` - of the requested resolution as follows: 0 for minimum X resolution 1 for minimum Y resolution 2 for maximum X resolution 3 for maximum Y resolution

      Returns:
      the resolution value specified by the index.

    <!-- -->

    - #### getResolutions

          public double getResolutions(int index)

      Get one of the Virtual Mosaic base resolution values, the resolution used when the object was created.
      Parameters:
      `index` - of the requested resolution as follows: 0 for base X resolution 1 for base Y resolution

      Returns:
      the resolution value specified by the index.

    <!-- -->

    - #### getBandCount

          public long getBandCount()

      Get the band dimension of the Virtual Mosaic object.
      Returns:
      long number of bands

    <!-- -->

    - #### getSrid

          public java.lang.String getSrid()

      Return the current SRID of the Virtual Mosaic object
      Returns:
      String containing an SRID value

    <!-- -->

    - #### setMosaicParameters

          public void setMosaicParameters(MosaicParameters mosaicParams)

      Set the parameters for virtual mosaiac
      Parameters:
      `mosaicParams` - a MosaicParameters object

    <!-- -->

    - #### getTableNames

          public java.lang.String getTableNames()

      Return the list of tables names
      Returns:
      String with table names separeted by comma ","

    <!-- -->

    - #### getColumnNames

          public java.lang.String getColumnNames()

      Return the list of columns names
      Returns:
      String with column names separeted by comma ","

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Return the current sql connection
      Returns:
      Connection sql connection

    <!-- -->

    - #### getSqlQuery

          public java.lang.String getSqlQuery()

      Return the SQL query, if exist
      Returns:
      the active SQL query

    <!-- -->

    - #### getFirstGeoRasterObject

          public JGeoRaster getFirstGeoRasterObject()

      Return the first GeoRaster object found on the virtual mosaic
      Returns:
      a JGeoRaster

    <!-- -->

    - #### getMosaicSubset

          public byte[] getMosaicSubset(int pyramidLevel,
                                        long startRow,
                                        long startColumn,
                                        long endRow,
                                        long endColumn,
                                        java.lang.String bandNumbers,
                                        int numBands,
                                        java.lang.String cellDepth,
                                        java.lang.String compression,
                                        java.lang.String interleaving,
                                        int quality,
                                        java.lang.String outSRID,
                                        long[] outWindow,
                                        double[] bgValues)
                                 throws GeoRasterException

      This private method performs the same operation as JRaster.getRasterSubset but for Virtual Mosaic and it should only be called by getRasterImageVM at this point.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row of are of interest

      `startColumn` - start column of are of interest

      `endRow` - end row of are of interest

      `endColumn` - end column of are of interest

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

      `numBands` - number of bands specified by bandNumbers.

      `cellDepth` - cellDepth of the returned raster data; must be one of the following values:

                                     RasterInfo.CELL_DEPTH_1BIT
                                     RasterInfo.CELL_DEPTH_2BIT
                                     RasterInfo.CELL_DEPTH_4BIT
                                     RasterInfo.CELL_DEPTH_8BIT_U
                                     RasterInfo.CELL_DEPTH_8BIT_S
                                     RasterInfo.CELL_DEPTH_16BIT_U
                                     RasterInfo.CELL_DEPTH_16BIT_S
                                     RasterInfo.CELL_DEPTH_32BIT_U
                                     RasterInfo.CELL_DEPTH_32BIT_S
                                     RasterInfo.CELL_DEPTH_32BIT_REAL
                                     RasterInfo.CELL_DEPTH_64BIT_REAL

      `compression` - compression type of the returned raster data; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `interleaving` - interleaving type of the returned raster data; must be one of the following values:

                                     RasterInfo.CELL_INTERLEVING_BSQ
                                     RasterInfo.CELL_INTERLEVING_BIL
                                     RasterInfo.CELL_INTERLEVING_BIP

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outSRID` - target srid number

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### setConnection

          public void setConnection(java.sql.Connection connection)

      Set a current valid connection to the JGeoRasterVM object to be used in subsequent getRasterSubset requests. The JGeoRasterVM will be using this connection with the same JGeoRasterVM attributes definied at the constructor.
      Parameters:
      `connection` - database connection

    <!-- -->

    - #### refresh

          public void refresh()

      Recalculate the extents and resolutions of the virtual mosaic based on the attributes provided in the constructor

    <!-- -->

    - #### getOutArea

          public JGeometry getOutArea()

      Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the virtual mosaic
      Returns:
      a SDO_GEOMETRY object containing the MBR of the resulting virtual mosaic

    <!-- -->

    - #### getMosaicParameters

          public MosaicParameters getMosaicParameters()

      Return the active MosaicPameters
      Returns:
      the active MosaicPameters

    <!-- -->

    - #### getReferenceImage

          public SdoGeoRaster getReferenceImage()

      Returns:

    <!-- -->

    - #### setReferenceImage

          public void setReferenceImage(SdoGeoRaster referenceImage)

      Parameters:
      `referenceImage` -

    <!-- -->

    - #### getReferenceValue1

          public double[] getReferenceValue1()

      Get reference value 1
      Returns:

    <!-- -->

    - #### setReferenceValue1

          public void setReferenceValue1(double[] referenceValue1)

      Set reference value 1
      Parameters:
      `referenceValue1` -

    <!-- -->

    - #### getReferenceValue2

          public double[] getReferenceValue2()

      Get reference value 2
      Returns:

    <!-- -->

    - #### setReferenceValue2

          public void setReferenceValue2(double[] referenceValue2)

      Set reference value 2
      Parameters:
      `referenceValue2` -

    <!-- -->

    - #### getReferenceHistograms

          public GeorHistogram[] getReferenceHistograms()

      Get reference histogram
      Returns:

    <!-- -->

    - #### setReferenceHistograms

          public void setReferenceHistograms(GeorHistogram[] referenceHistograms)

      Set reference histogram
      Parameters:
      `referenceHistograms` -

    <!-- -->

    - #### getElevationParam

          public java.lang.String getElevationParam()

      Get elevation Parameters
      Returns:

    <!-- -->

    - #### setElevationParam

          public void setElevationParam(java.lang.String elevationParam)

      Set elevation Parameters
      Parameters:
      `elevationParam` -

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

- [Prev Class](JGeoRasterMeta.md)
- [Next Class](JRaster.md)

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
