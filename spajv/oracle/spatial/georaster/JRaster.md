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

- [Prev Class](JGeoRasterVM.md)
- [Next Class](LayerInfo.md)

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

## Class JRaster

- java.lang.Object

- - oracle.spatial.georaster.JRaster

<!-- -->

-

  ------------------------------------------------------------------------



      public class JRaster
      extends java.lang.Object

  JRaster is a Java class that deals with raster data stored on the server side. It provides the capability to retrieve and manipulate the raster block data and mask data of a GeoRaster object based on a specified rowNumber, columnNumber, bandNumber, and pyramidLevel.
  A JRaster object is always associated with a JGeoRaster object, and cannot be constructed directly. When a JGeoRaster is initiated successfully, a JRaster object is created automatically, and the following method defined for JGeoRaster can be used to retrieve an instance of JRaster:

           public JRaster getRasterObject()


  The JRaster class provides two categories of methods. The first category is for raster data accessing based on different query conditions, for example:

           public BLOB getRasterSubsetBlob(...)
           public byte[] getRasterSubset(...)
           public BLOB getBitmapMaskSubsetBlob(...)
           public byte[] getBitmapMaskSubset(...)
           public double getCellValue(...)
           public byte getBitmapMaskValue(...)
           ...

  The second category is for raster data updating based on the raster block, for example:

           public void initRDT()
           public void dropAllRasterBlocks()
           public Blob initRasterBlock((...)
           public byte[] getRasterBlock(...)
           public void generateBlockMBR()
            public void storeRasterBlock(...)
           ...


<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `appendRasterBlock``(byte[] data, java.sql.Blob rasterBlock)`<br>Stores data from byte array into a BLOB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                  | `changeCellValue``(`[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String layerNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                  | `changeCellValue``(long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                  | `changeCellValue``(long row, long column, java.lang.String bandNumbers, double newCellValue, double[] bgValues)`<br>Changes the value of raster cell in a specified point of a GeoRaster object to a single new value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                  | `dropAllRasterBlocks``()`<br>Drops all raster blocks of the associated GeoRaster object from raster data table in the Oracle database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                  | `generateBlockMBR``()`<br>Computes the minimum bounding rectangle (MBR) for each block in a GeoRaster object, and sets the blockMBR attribute for each raster block in the raster data table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `byte[]`                                | `getBitmapMaskSubset``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, int layerNo, java.lang.String cellDepth, java.lang.String compression, int quality, long[] outWindow)`<br>Returns binary mask data as a byte array for specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.                                                                                                                                                                                                                                                                                                                              |
    | `byte[]`                                | `getBitmapMaskSubset``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, int layerNo, java.lang.String cellDepth, java.lang.String compression, long[] outWindow)`<br>Returns binary mask data as a byte array for a specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.                                                                                                                                                                                                                                                                                                                             |
    | `oracle.sql.BLOB`                       | `getBitmapMaskSubsetBlob``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, int layerNo, java.lang.String cellDepth, java.lang.String compression, long[] outWindow)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `java.sql.Blob`                         | `getBitmapMaskSubsetBlobJS``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, int layerNo, java.lang.String cellDepth, java.lang.String compression, long[] outWindow)`<br>Returns binary mask data as a BLOB for the specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.                                                                                                                                                                                                                                                                                                                                       |
    | `java.sql.Blob`                         | `getBitmapMaskSubsetBlobJS``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, int layerNo, java.lang.String cellDepth, java.lang.String compression, long[] outWindow)`<br>Returns binary mask data as a BLOB for specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.                                                                                                                                                                                                                                                                                                                               |
    | `byte`                                  | `getBitmapMaskValue``(int layerNumber, int pyramidLevel, int rowNumber, int colNumber)`<br>Gets the value of a single cell from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `byte`                                  | `getBitmapMaskValue``(int layerNumber, int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` ptGeom)`<br>Gets the value of a single cell from a bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `double`                                | `getCellValue``(int pyramidLevel, int rowNumber, int colNumber, int bandNumber)`<br>Returns the value of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its band number.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `double`                                | `getCellValue``(`[`JGeometry`](../geometry/JGeometry.md)` ptGeom, int pyramidLevel, int layerNumber)`<br>Returns the value of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer number.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `java.math.BigDecimal[]`                | `getCellValues``(int pyramidLevel, int rowNumber, int colNumber, java.lang.String bandNumbers)`<br>Returns an array of values of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its band numbers.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.math.BigDecimal[]`                | `getCellValues``(`[`JGeometry`](../geometry/JGeometry.md)` ptGeom, int pyramidLevel, java.lang.String layerNumbers)`<br>Returns an array of values of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer numbers.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`JGeometry`](../geometry/JGeometry.md) | `getOutArea``()`<br>Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object of previous getReprojectedRasterSubset or getReprojectedRasterSubsetBlob call.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `byte[]`                                | `getRasterBlock``(int pyramidLevel, long bandBlockNumber, long rowBlockNumber, long columnBlockNumber, boolean isBitmapMask, boolean lock_for_write)`<br>Gets the byte array of a specified raster block.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.sql.Blob`                         | `getRasterBlockLocatorJS``(int pyramidLevel, long bandBlockNumber, long rowBlockNumber, long columnBlockNumber, boolean isBitmapMask, boolean lock_for_write)`<br>Gets the LOB locator of a specified raster block.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `oracle.sql.BLOB`                       | `getRasterData``(int pyramidLevel, java.lang.String storageParam, double[] bgValues)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.sql.Blob`                         | `getRasterDataJS``(int pyramidLevel, java.lang.String storageParam, double[] bgValues)`<br>Returns a single Blob object that contains all raster data of the associated GeoRaster object at the specified pyramid level.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `byte[]`                                | `getRasterSubset``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String bandNumbers, int numBands, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, long[] outWindow, double[] bgValues)`<br>Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.                                                                                                                                                                                                                                                                  |
    | `java.sql.Blob`                         | `getRasterSubset``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String layerNumbers, long[] outWindow, java.lang.String storageParam, double[] bgValues, java.lang.String polygonClip)`<br>Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.                                                                                                                                                                                                                                                                                                                        |
    | `java.sql.Blob`                         | `getRasterSubset``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String layerNumbers, java.lang.String storageParam, double[] bgValues, java.lang.String polygonClip)`<br>Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.                                                                                                                                                                                                                                                                                                                                          |
    | `byte[]`                                | `getRasterSubset``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, int numBands, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, long[] outWindow, double[] bgValues)`<br>Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.                                                                                                                                                                                                                                                     |
    | `oracle.sql.BLOB`                       | `getRasterSubsetBlob``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, long[] outWindow, double[] bgValues)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.sql.Blob`                         | `getRasterSubsetBlobJS``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, long[] outWindow, double[] bgValues)`<br>Returns binary raster data as a BLOB for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.                                                                                                                                                                                                                                                                                |
    | `java.sql.Blob`                         | `getRasterSubsetBlobJS``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, long[] outWindow, double[] bgValues)`<br>Returns binary raster data as a BLOB for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.                                                                                                                                                                                                                                                                   |
    | `java.math.BigDecimal[]`                | `getRasterSubsetDataArray``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` inWindow, java.lang.String layerNumbers, java.math.BigDecimal[] outWindow, java.lang.String storageParam, double[] bgValues, boolean polygonClip)`<br>Returns raster data as a BigDecimal array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.                                                                                                                                                                                                                                                                                                      |
    | `java.math.BigDecimal[]`                | `getRasterSubsetDataArray``(int pyramidLevel, long[] inWindow, java.lang.String bandNumbers, java.math.BigDecimal[] outWindow, java.lang.String storageParam, double[] bgValues)`<br>Returns raster data as a BigDecimal array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.                                                                                                                                                                                                                                                                                                                                                               |
    | `byte[]`                                | `getReprojectedRasterSubset``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String resampleParam, java.lang.String bandNumbers, int numBands, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Reproject subset of a GeoRaster object, and returns binary raster data as a byte array, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.             |
    | `byte[]`                                | `getReprojectedRasterSubset``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String resampleParam, java.lang.String bandNumbers, int numBands, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Reproject subset of a GeoRaster object, and returns binary raster data as a byte array, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object. |
    | `oracle.sql.BLOB`                       | `getReprojectedRasterSubsetBlob``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String resampleParam, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                       |
    | `oracle.sql.BLOB`                       | `getReprojectedRasterSubsetBlob``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String resampleParam, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                           |
    | `java.sql.Blob`                         | `getReprojectedRasterSubsetBlobJS``(int pyramidLevel, `[`JGeometry`](../geometry/JGeometry.md)` window, java.lang.String resampleParam, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.                           |
    | `java.sql.Blob`                         | `getReprojectedRasterSubsetBlobJS``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String resampleParam, java.lang.String bandNumbers, java.lang.String cellDepth, java.lang.String compression, java.lang.String interleaving, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.               |
    | `oracle.sql.BLOB`                       | `initRasterBlock``(int pLevel, int bandBlockNumber, int rowBlockNumber, int columnBlockNumber, `[`JGeometry`](../geometry/JGeometry.md)` mbr)`<br>Inserts a new row into raster data table with specified pLevel,bandBlockNumber, rowBlockNumber, columnBlockNumber, and mbr.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `java.sql.Blob`                         | `initRasterBlockJS``(int pLevel, int bandBlockNumber, int rowBlockNumber, int columnBlockNumber, `[`JGeometry`](../geometry/JGeometry.md)` mbr)`<br>Inserts a new row into raster data table with specified pLevel,bandBlockNumber, rowBlockNumber, columnBlockNumber, and mbr.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                  | `initRDT``()`<br>Initializes all rows in the RDT table, based on information like dimensionSize, blockSize, pyramidLevel, and so on, stored in the metadata.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                  | `setBitmapMask``(int layerNumber, `[`JGeoRaster`](JGeoRaster.md)` mask, java.lang.String NODATAMask)`<br>Attaches a bitmap mask to a GeoRaster object, or replaces or removes the current bitmap mask.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                  | `storeRasterBlock``(byte[] data, java.sql.Blob rasterBlock)`<br>Stores data from byte array into a BLOB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                  | `storeRasterBlock``(javax.imageio.stream.ImageInputStream data, java.sql.Blob rasterBlock)`<br>Stores data from an ImageInputStream into blob.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                               | `validateBlockMBR``()`<br>Checks the blockMBR attribute in each row of the raster data table associated with the specified GeoRaster object to see if its geometry is the actual minimum bounding rectangle (MBR) of that block.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getOutArea

          public JGeometry getOutArea()

      Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object of previous getReprojectedRasterSubset or getReprojectedRasterSubsetBlob call.
      Returns:
      a SDO_GEOMETRY object containing the MBR of the resulting object of previous getReprojectedRasterSubset or getReprojectedRasterSubsetBlob call.

    <!-- -->

    - #### getReprojectedRasterSubset

          public byte[] getReprojectedRasterSubset(int pyramidLevel,
                                                   JGeometry window,
                                                   java.lang.String resampleParam,
                                                   java.lang.String bandNumbers,
                                                   int numBands,
                                                   java.lang.String cellDepth,
                                                   java.lang.String compression,
                                                   java.lang.String interleaving,
                                                   int quality,
                                                   int outSRID,
                                                   long[] outWindow,
                                                   double[] bgValues)

      Reproject subset of a GeoRaster object, and returns binary raster data as a byte array, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `resampleParam` - a string containing the resampling parameters.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getReprojectedRasterSubset

          public byte[] getReprojectedRasterSubset(int pyramidLevel,
                                                   long startRow,
                                                   long startColumn,
                                                   long endRow,
                                                   long endColumn,
                                                   java.lang.String resampleParam,
                                                   java.lang.String bandNumbers,
                                                   int numBands,
                                                   java.lang.String cellDepth,
                                                   java.lang.String compression,
                                                   java.lang.String interleaving,
                                                   int quality,
                                                   int outSRID,
                                                   long[] outWindow,
                                                   double[] bgValues)

      Reproject subset of a GeoRaster object, and returns binary raster data as a byte array, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `resampleParam` - a string containing the resampling parameters.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getReprojectedRasterSubsetBlob

          @Deprecated
          public oracle.sql.BLOB getReprojectedRasterSubsetBlob(int pyramidLevel,
                                                                             JGeometry window,
                                                                             java.lang.String resampleParam,
                                                                             java.lang.String bandNumbers,
                                                                             java.lang.String cellDepth,
                                                                             java.lang.String compression,
                                                                             java.lang.String interleaving,
                                                                             int quality,
                                                                             int outSRID,
                                                                             long[] outWindow,
                                                                             double[] bgValues)

      Deprecated. 
      Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `resampleParam` - a string containing the resampling parameters.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getReprojectedRasterSubsetBlobJS

          public java.sql.Blob getReprojectedRasterSubsetBlobJS(int pyramidLevel,
                                                                JGeometry window,
                                                                java.lang.String resampleParam,
                                                                java.lang.String bandNumbers,
                                                                java.lang.String cellDepth,
                                                                java.lang.String compression,
                                                                java.lang.String interleaving,
                                                                int quality,
                                                                int outSRID,
                                                                long[] outWindow,
                                                                double[] bgValues)

      Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `resampleParam` - a string containing the resampling parameters.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getReprojectedRasterSubsetBlob

          @Deprecated
          public oracle.sql.BLOB getReprojectedRasterSubsetBlob(int pyramidLevel,
                                                                             long startRow,
                                                                             long startColumn,
                                                                             long endRow,
                                                                             long endColumn,
                                                                             java.lang.String resampleParam,
                                                                             java.lang.String bandNumbers,
                                                                             java.lang.String cellDepth,
                                                                             java.lang.String compression,
                                                                             java.lang.String interleaving,
                                                                             int quality,
                                                                             int outSRID,
                                                                             long[] outWindow,
                                                                             double[] bgValues)

      Deprecated. 
      Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `resampleParam` - a string containing the resampling parameters.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getReprojectedRasterSubsetBlobJS

          public java.sql.Blob getReprojectedRasterSubsetBlobJS(int pyramidLevel,
                                                                long startRow,
                                                                long startColumn,
                                                                long endRow,
                                                                long endColumn,
                                                                java.lang.String resampleParam,
                                                                java.lang.String bandNumbers,
                                                                java.lang.String cellDepth,
                                                                java.lang.String compression,
                                                                java.lang.String interleaving,
                                                                int quality,
                                                                int outSRID,
                                                                long[] outWindow,
                                                                double[] bgValues)

      Reproject subset of a GeoRaster object, and returns binary raster data as a Blob, based on parameters which specify a window, layers, and customized cell depth.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `resampleParam` - a string containing the resampling parameters.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getRasterSubsetBlob

          @Deprecated
          public oracle.sql.BLOB getRasterSubsetBlob(int pyramidLevel,
                                                                  long startRow,
                                                                  long startColumn,
                                                                  long endRow,
                                                                  long endColumn,
                                                                  java.lang.String bandNumbers,
                                                                  java.lang.String cellDepth,
                                                                  java.lang.String compression,
                                                                  java.lang.String interleaving,
                                                                  int quality,
                                                                  long[] outWindow,
                                                                  double[] bgValues)

      Deprecated. 
      Returns binary raster data as a BLOB for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data.

      See Also:
      [`RasterInfo`](RasterInfo.md)

    <!-- -->

    - #### getRasterSubsetBlobJS

          public java.sql.Blob getRasterSubsetBlobJS(int pyramidLevel,
                                                     long startRow,
                                                     long startColumn,
                                                     long endRow,
                                                     long endColumn,
                                                     java.lang.String bandNumbers,
                                                     java.lang.String cellDepth,
                                                     java.lang.String compression,
                                                     java.lang.String interleaving,
                                                     int quality,
                                                     long[] outWindow,
                                                     double[] bgValues)

      Returns binary raster data as a BLOB for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data.

      See Also:
      [`RasterInfo`](RasterInfo.md)

    <!-- -->

    - #### getRasterSubsetBlobJS

          public java.sql.Blob getRasterSubsetBlobJS(int pyramidLevel,
                                                     JGeometry window,
                                                     java.lang.String bandNumbers,
                                                     java.lang.String cellDepth,
                                                     java.lang.String compression,
                                                     java.lang.String interleaving,
                                                     int quality,
                                                     long[] outWindow,
                                                     double[] bgValues)

      Returns binary raster data as a BLOB for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level.

      `window` - a JGeometry object which represents the area of interest.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

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

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data.

    <!-- -->

    - #### getRasterSubset

          public java.sql.Blob getRasterSubset(int pyramidLevel,
                                               JGeometry window,
                                               java.lang.String layerNumbers,
                                               java.lang.String storageParam,
                                               double[] bgValues,
                                               java.lang.String polygonClip)

      Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If you specify a null value for this parameter, the operation or operations are performed on all layers.

      `storageParam` - A string specifying storage parameters to be applied in creating rasterBlob. The only supported storageParam keywords supported for this procedure are celldepth, compression, interleaving, and quality; all other keywords are ignored. Storage parameters are explained in Section 1.4.1. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB.

      `polygonClip` - The string TRUE causes the window or inWindow geometry object to be used for the subset operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the window or inWindow geometry object to be used for the subset operation.

      Returns:
      a single Blob object containing all cells of a specified pyramid level that are inside or on the boundary of polygon geometry object.

    <!-- -->

    - #### getRasterSubset

          public java.sql.Blob getRasterSubset(int pyramidLevel,
                                               JGeometry window,
                                               java.lang.String layerNumbers,
                                               long[] outWindow,
                                               java.lang.String storageParam,
                                               double[] bgValues,
                                               java.lang.String polygonClip)

      Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If you specify a null value for this parameter, the operation or operations are performed on all layers.

      `outWindow` - An array object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `storageParam` - A string specifying storage parameters to be applied in creating rasterBlob. The only supported storageParam keywords supported for this procedure are celldepth, compression, interleaving, and quality; all other keywords are ignored. Storage parameters are explained in Section 1.4.1. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB.

      `polygonClip` - The string TRUE causes the window or inWindow geometry object to be used for the subset operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the window or inWindow geometry object to be used for the subset operation.

      Returns:
      a single Blob object containing all cells of a specified pyramid level that are inside or on the boundary of polygon geometry object.

    <!-- -->

    - #### getRasterSubset

          public byte[] getRasterSubset(int pyramidLevel,
                                        JGeometry window,
                                        java.lang.String bandNumbers,
                                        int numBands,
                                        java.lang.String cellDepth,
                                        java.lang.String compression,
                                        java.lang.String interleaving,
                                        int quality,
                                        long[] outWindow,
                                        double[] bgValues)

      Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters which specify a window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

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

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getRasterSubset

          public byte[] getRasterSubset(int pyramidLevel,
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
                                        long[] outWindow,
                                        double[] bgValues)

      Returns binary raster data as a byte array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

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

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      binary raster data stored in a byte array.

    <!-- -->

    - #### getRasterSubsetDataArray

          public java.math.BigDecimal[] getRasterSubsetDataArray(int pyramidLevel,
                                                                 long[] inWindow,
                                                                 java.lang.String bandNumbers,
                                                                 java.math.BigDecimal[] outWindow,
                                                                 java.lang.String storageParam,
                                                                 double[] bgValues)
                                                          throws java.lang.Exception

      Returns raster data as a BigDecimal array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `inWindow` - A rectangular window from which to crop the cells. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - a string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `storageParam` - A string specifying storage parameters to be applied in creating rasterBlob. The only supported storageParam keywords supported for this procedure are celldepth, compression, interleaving, and quality; all other keywords are ignored. Storage parameters are explained in Storage Parameters. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      raster data stored in a BigDecimal array.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterSubsetDataArray

          public java.math.BigDecimal[] getRasterSubsetDataArray(int pyramidLevel,
                                                                 JGeometry inWindow,
                                                                 java.lang.String layerNumbers,
                                                                 java.math.BigDecimal[] outWindow,
                                                                 java.lang.String storageParam,
                                                                 double[] bgValues,
                                                                 boolean polygonClip)
                                                          throws java.lang.Exception

      Returns raster data as a BigDecimal array for the associated GeoRaster object, based on parameters that specify the window, layers, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `inWindow` - A rectangular window from which to crop the cells. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4). If you specify a null value for this parameter, the operation or operations are performed on all layers.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `storageParam` - A string specifying storage parameters to be applied in creating rasterBlob. The only supported storageParam keywords supported for this procedure are celldepth, compression, interleaving, and quality; all other keywords are ignored. Storage parameters are explained in Storage Parameters. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      `polygonClip` - TRUE causes the window or inWindow geometry object to be used for the subset operation; FALSE or a null value causes the MBR (minimum bounding rectangle) of the window or inWindow geometry object to be used for the subset operation.

      Returns:
      raster data stored in a BigDecimal array.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskSubsetBlobJS

          public java.sql.Blob getBitmapMaskSubsetBlobJS(int pyramidLevel,
                                                         JGeometry window,
                                                         int layerNo,
                                                         java.lang.String cellDepth,
                                                         java.lang.String compression,
                                                         long[] outWindow)

      Returns binary mask data as a BLOB for the specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNo` - the logical layer whose bitmap mask will be returned as a byte array

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
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      binary mask data.

    <!-- -->

    - #### getBitmapMaskSubsetBlob

          @Deprecated
          public oracle.sql.BLOB getBitmapMaskSubsetBlob(int pyramidLevel,
                                                                      long startRow,
                                                                      long startColumn,
                                                                      long endRow,
                                                                      long endColumn,
                                                                      int layerNo,
                                                                      java.lang.String cellDepth,
                                                                      java.lang.String compression,
                                                                      long[] outWindow)

      Deprecated. 
      Returns binary mask data as a BLOB for specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `layerNo` - logical layer whose bitmap mask will be returned as a byte array

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
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      binary mask data.

    <!-- -->

    - #### getBitmapMaskSubsetBlobJS

          public java.sql.Blob getBitmapMaskSubsetBlobJS(int pyramidLevel,
                                                         long startRow,
                                                         long startColumn,
                                                         long endRow,
                                                         long endColumn,
                                                         int layerNo,
                                                         java.lang.String cellDepth,
                                                         java.lang.String compression,
                                                         long[] outWindow)

      Returns binary mask data as a BLOB for specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `layerNo` - logical layer whose bitmap mask will be returned as a byte array

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
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      binary mask data.

    <!-- -->

    - #### getBitmapMaskSubset

          public byte[] getBitmapMaskSubset(int pyramidLevel,
                                            JGeometry window,
                                            int layerNo,
                                            java.lang.String cellDepth,
                                            java.lang.String compression,
                                            int quality,
                                            long[] outWindow)

      Returns binary mask data as a byte array for specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNo` - the logical layer whose bitmap mask will be returned as a byte array

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
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      binary mask data stored in a byte array.

    <!-- -->

    - #### getBitmapMaskSubset

          public byte[] getBitmapMaskSubset(int pyramidLevel,
                                            long startRow,
                                            long startColumn,
                                            long endRow,
                                            long endColumn,
                                            int layerNo,
                                            java.lang.String cellDepth,
                                            java.lang.String compression,
                                            long[] outWindow)

      Returns binary mask data as a byte array for a specified layer of the associated GeoRaster object, based on parameters that specify the window, layer, and customized cell depth.
      Parameters:
      `pyramidLevel` - pyramid level.

      `startRow` - upper-left row coordinate, not including ULTCoordinate

      `startColumn` - upper-left column coordinate, not including ULTCoordinate

      `endRow` - lower-right row coordinate, not including ULTCoordinate

      `endColumn` - lower-right column coordinate, not including ULTCoordinate

      `layerNo` - the logical layer whose bitmap mask will be returned as a byte array

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
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      binary mask data stored in a byte array.

    <!-- -->

    - #### dropAllRasterBlocks

          public void dropAllRasterBlocks()
                                   throws java.lang.Exception

      Drops all raster blocks of the associated GeoRaster object from raster data table in the Oracle database. This method is usually used by the loader to reload all GeoRaster data from outside.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### initRasterBlock

          public oracle.sql.BLOB initRasterBlock(int pLevel,
                                                 int bandBlockNumber,
                                                 int rowBlockNumber,
                                                 int columnBlockNumber,
                                                 JGeometry mbr)
                                          throws java.lang.Exception

      Inserts a new row into raster data table with specified pLevel,bandBlockNumber, rowBlockNumber, columnBlockNumber, and mbr. This method is usually used by the loader, and an empty blob gets returned.
      Parameters:
      `pLevel` - pyramid level

      `bandBlockNumber` - band block number

      `rowBlockNumber` - row block number

      `columnBlockNumber` - column block number

      `mbr` - geometry extent

      Returns:
      an empty BLOB object in the new row

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### initRasterBlockJS

          public java.sql.Blob initRasterBlockJS(int pLevel,
                                                 int bandBlockNumber,
                                                 int rowBlockNumber,
                                                 int columnBlockNumber,
                                                 JGeometry mbr)
                                          throws java.lang.Exception

      Inserts a new row into raster data table with specified pLevel,bandBlockNumber, rowBlockNumber, columnBlockNumber, and mbr. This method is usually used by the loader, and an empty blob gets returned.
      Parameters:
      `pLevel` - pyramid level

      `bandBlockNumber` - band block number

      `rowBlockNumber` - row block number

      `columnBlockNumber` - column block number

      `mbr` - geometry extent

      Returns:
      an empty BLOB object in the new row

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### storeRasterBlock

          public void storeRasterBlock(javax.imageio.stream.ImageInputStream data,
                                       java.sql.Blob rasterBlock)
                                throws java.lang.Exception

      Stores data from an ImageInputStream into blob. This method is usually used by loader.
      Parameters:
      `data` - ImageInputStream

      `rasterBlock` - blob

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### storeRasterBlock

          public void storeRasterBlock(byte[] data,
                                       java.sql.Blob rasterBlock)
                                throws java.lang.Exception

      Stores data from byte array into a BLOB. All data stored in the byte array will be streamingly written into BLOB without any change, before writting, position of BLOB will be set to 1. This method is usually used by the loader.
      Parameters:
      `data` - binary array

      `rasterBlock` - blob

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### appendRasterBlock

          public void appendRasterBlock(byte[] data,
                                        java.sql.Blob rasterBlock)
                                 throws java.lang.Exception

      Stores data from byte array into a BLOB. All data stored in the byte array will be streamingly written into BLOB without any change, before writing, position of BLOB will be set to it's end. This method is usually used by the loader.
      Parameters:
      `data` - binary array

      `rasterBlock` - blob

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(long row,
                                      long column,
                                      java.lang.String bandNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cell in a specified point of a GeoRaster object to a single new value.
      Parameters:
      `row` - row of the point where the values is changed to newCellValue

      `column` - column of the point where the values is changed to newCellValue

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `newCellValue` - the new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(long startRow,
                                      long startColumn,
                                      long endRow,
                                      long endColumn,
                                      java.lang.String bandNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.
      Parameters:
      `startRow` - startX of the Window in which to change the values of all cells to newCellValue

      `startColumn` - startY of the Window in which to change the values of all cells to newCellValue

      `endRow` - endX of the Window in which to change the values of all cells to newCellValue

      `endColumn` - endY of the Window in which to change the values of all cells to newCellValue

      `bandNumbers` - a string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `newCellValue` - the new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### changeCellValue

          public void changeCellValue(JGeometry window,
                                      java.lang.String layerNumbers,
                                      double newCellValue,
                                      double[] bgValues)
                               throws java.lang.Exception

      Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.
      Parameters:
      `window` - window in which to change the values of all cells to newCellValue

      `layerNumbers` - a string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `newCellValue` - the new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the cellDepth value for the GeoRaster object.

      `bgValues` - background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks. The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public double getCellValue(JGeometry ptGeom,
                                     int pyramidLevel,
                                     int layerNumber)
                              throws java.lang.Exception

      Returns the value of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer number.
      Parameters:
      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - point geometry that identifies the cell whose value is to be returned

      `layerNumber` - number of the logical layer that contains the cell whose value is to be returned. (The logical layer number is the physical band number plus 1.)

      Returns:
      cellValue.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValue

          public double getCellValue(int pyramidLevel,
                                     int rowNumber,
                                     int colNumber,
                                     int bandNumber)
                              throws java.lang.Exception

      Returns the value of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its band number.
      Parameters:
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

          public java.math.BigDecimal[] getCellValues(JGeometry ptGeom,
                                                      int pyramidLevel,
                                                      java.lang.String layerNumbers)
                                               throws java.lang.Exception

      Returns an array of values of a single cell located anywhere in the GeoRaster object by specifying a point geometry in its model coordinate system and its logical layer numbers.
      Parameters:
      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `ptGeom` - point geometry that identifies the cell whose value is to be returned

      `layerNumbers` - A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3)

      Returns:
      cellValue. Note that this function only works in version 11.2 or later.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellValues

          public java.math.BigDecimal[] getCellValues(int pyramidLevel,
                                                      int rowNumber,
                                                      int colNumber,
                                                      java.lang.String bandNumbers)
                                               throws java.lang.Exception

      Returns an array of values of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number in its cell coordinate system and its band numbers.
      Parameters:
      `pyramidLevel` - pyramid level containing the cell whose value is to be returned

      `rowNumber` - number of the row that contains the cell whose value is to be returned

      `colNumber` - number of the column that contains the cell whose value is to be returned

      `bandNumbers` - A string identifying the phisical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3)

      Returns:
      cellValue. Note that this function only works in version 11.2 or later.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateBlockMBR

          public void generateBlockMBR()
                                throws java.lang.Exception

      Computes the minimum bounding rectangle (MBR) for each block in a GeoRaster object, and sets the blockMBR attribute for each raster block in the raster data table. This method does not change the GeoRaster object. It sets the value of the blockMBR attribute in each row of the raster data table associated with the GeoRaster object.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValue

          public byte getBitmapMaskValue(int layerNumber,
                                         int pyramidLevel,
                                         int rowNumber,
                                         int colNumber)
                                  throws java.lang.Exception

      Gets the value of a single cell from a bitmap mask.
      Parameters:
      `layerNumber` - number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `pyramidLevel` - pyramid level containing the specified cell

      `rowNumber` - row number in cell space

      `colNumber` - column number in cell space

      Returns:
      the value of a single cell from a bitmap mask.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getBitmapMaskValue

          public byte getBitmapMaskValue(int layerNumber,
                                         int pyramidLevel,
                                         JGeometry ptGeom)
                                  throws java.lang.Exception

      Gets the value of a single cell from a bitmap mask.
      Parameters:
      `layerNumber` - number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

      `pyramidLevel` - pyramid level containing the specified cell

      `ptGeom` - point geometry in cell space or model space

      Returns:
      the value of a single cell from a bitmap mask.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterBlockLocatorJS

          public java.sql.Blob getRasterBlockLocatorJS(int pyramidLevel,
                                                       long bandBlockNumber,
                                                       long rowBlockNumber,
                                                       long columnBlockNumber,
                                                       boolean isBitmapMask,
                                                       boolean lock_for_write)
                                                throws java.lang.Exception

      Gets the LOB locator of a specified raster block.
      Parameters:
      `pyramidLevel` - pyramid level of the block

      `bandBlockNumber` - band number of the block

      `rowBlockNumber` - row number of the block

      `columnBlockNumber` - column number of the block

      `isBitmapMask` - the string TRUE specifies that a bitmap mask block will be accessed; the string FALSE specifies that a regular raster block will be accessed. If you do not specify this parameter, a regular raster block will be accessed. For an explanation of bitmap masks, see the Oracle Spatial GeoRaster Developer's Guide.

      `lock_for_write` - the string TRUE locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the string FALSE does not lock the row in the raster data table. If you do not specify this parameter, the row is not locked.

      Returns:
      the LOB locator of a specified raster block.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterBlock

          public byte[] getRasterBlock(int pyramidLevel,
                                       long bandBlockNumber,
                                       long rowBlockNumber,
                                       long columnBlockNumber,
                                       boolean isBitmapMask,
                                       boolean lock_for_write)
                                throws java.lang.Exception

      Gets the byte array of a specified raster block.
      Parameters:
      `pyramidLevel` - pyramid level of the block

      `bandBlockNumber` - band number of the block

      `rowBlockNumber` - row number of the block

      `columnBlockNumber` - column number of the block

      `isBitmapMask` - the string TRUE specifies that a bitmap mask block will be accessed; the string FALSE specifies that a regular raster block will be accessed. If you do not specify this parameter, a regular raster block will be accessed. For an explanation of bitmap masks, see the Oracle Spatial GeoRaster Developer's Guide.

      `lock_for_write` - the string TRUE locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the string FALSE does not lock the row in the raster data table. If you do not specify this parameter, the row is not locked.

      Returns:
      a byte array of a specified raster block.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterData

          @Deprecated
          public oracle.sql.BLOB getRasterData(int pyramidLevel,
                                                            java.lang.String storageParam,
                                                            double[] bgValues)
                                                     throws java.lang.Exception

      Deprecated. 
      Returns a single BLOB object that contains all raster data of the associated GeoRaster object at the specified pyramid level.
      Parameters:
      `pyramidLevel` - pyramid level for which to perform the operation

      `storageParam` - a string specifying storage parameters to be applied in creating rasterBlob. The only storageParam keywords supported for this method are celldepth, compression, interleaving, and quality; all other keywords are ignored. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the double array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, double\[\](1,5,10) fills the first band with 1, the second band with 5, and the third band with 10.

      Returns:
      a single BLOB object that contains all raster data of the associated GeoRaster object at the specified pyramid level.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterDataJS

          public java.sql.Blob getRasterDataJS(int pyramidLevel,
                                               java.lang.String storageParam,
                                               double[] bgValues)
                                        throws java.lang.Exception

      Returns a single Blob object that contains all raster data of the associated GeoRaster object at the specified pyramid level.
      Parameters:
      `pyramidLevel` - pyramid level for which to perform the operation

      `storageParam` - a string specifying storage parameters to be applied in creating rasterBlob. The only storageParam keywords supported for this method are celldepth, compression, interleaving, and quality; all other keywords are ignored. If storageParam is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

      `bgValues` - background values for filling sparse data. The number of elements in the double array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, double\[\](1,5,10) fills the first band with 1, the second band with 5, and the third band with 10.

      Returns:
      a single BLOB object that contains all raster data of the associated GeoRaster object at the specified pyramid level.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setBitmapMask

          public void setBitmapMask(int layerNumber,
                                    JGeoRaster mask,
                                    java.lang.String NODATAMask)
                             throws java.lang.Exception

      Attaches a bitmap mask to a GeoRaster object, or replaces or removes the current bitmap mask.
      Parameters:
      `layerNumber` - layer with which to associate the bitmap mask. A value of 0 (zero) indicates the object layer.

      `mask` - the bitmap mask to be attached to the GeoRaster object. If this parameter is null, any existing bitmap mask associated with the specified layer of the GeoRaster object is removed.

      `NODATAMask` - Specifies false if mask is not to be interpreted as a NODATA mask, or true if mask is to be interpreted as a NODATA mask.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateBlockMBR

          public boolean validateBlockMBR()
                                   throws java.lang.Exception

      Checks the blockMBR attribute in each row of the raster data table associated with the specified GeoRaster object to see if its geometry is the actual minimum bounding rectangle (MBR) of that block.
      Returns:
      the string TRUE if the blockMBR attribute is the MBR of each block, a null value if the GeoRaster object is null, an Oracle error code if the error is known, or FALSE for an unknown error.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### initRDT

          public void initRDT()
                       throws java.lang.Exception

      Initializes all rows in the RDT table, based on information like dimensionSize, blockSize, pyramidLevel, and so on, stored in the metadata. Each rasterBlock column will be initialized as an empty blob, and then can be retrieved by the following method:
      public Blob getRasterBlockLocator(int pyramidLevel,long bandBlockNumber,long rowBlockNumber,long columnBlockNumber,boolean isBitmapMask,boolean lock_for_write) throws Exception

      Note: this method will delete all rows associated with current rasterID first.

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

- [Prev Class](JGeoRasterVM.md)
- [Next Class](LayerInfo.md)

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
