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

- [Prev Class](ObjectInfo.md)
- [Next Class](SpatialReferenceInfo.md)

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

## Class RasterInfo

- java.lang.Object

- - oracle.spatial.georaster.RasterInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class RasterInfo
      extends java.lang.Object

  RasterInfo is a Java class mapped to the XML element RasterInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                   |
    |---------------------------|---------------------------------------------------------------------------------------------------------|
    | `static int`              | `BAND_DIMENSION`<br>A integer indicating band dimension.                                                |
    | `static java.lang.String` | `BLOCKING_NONE`<br>A string indicating NONE blocking.                                                   |
    | `static java.lang.String` | `BLOCKING_REGULAR`<br>A string indicating REGULAR blocking.                                             |
    | `static java.lang.String` | `CELL_DEPTH_128BIT_COMPLEX`<br>A string indicating 128BIT_COMPLEX cell depth.                           |
    | `static java.lang.String` | `CELL_DEPTH_16BIT_S`<br>A string indicating 16BIT_S cell depth.                                         |
    | `static java.lang.String` | `CELL_DEPTH_16BIT_U`<br>A string indicating 16BIT_U cell depth.                                         |
    | `static java.lang.String` | `CELL_DEPTH_1BIT`<br>A string indicating 1BIT cell depth.                                               |
    | `static java.lang.String` | `CELL_DEPTH_2BIT`<br>A string indicating 2BIT cell depth.                                               |
    | `static java.lang.String` | `CELL_DEPTH_32BIT_REAL`<br>A string indicating 32BIT_REAL cell depth.                                   |
    | `static java.lang.String` | `CELL_DEPTH_32BIT_S`<br>A string indicating 32BIT_S cell depth.                                         |
    | `static java.lang.String` | `CELL_DEPTH_32BIT_U`<br>A string indicating 32BIT_U cell depth.                                         |
    | `static java.lang.String` | `CELL_DEPTH_4BIT`<br>A string indicating 4BIT cell depth.                                               |
    | `static java.lang.String` | `CELL_DEPTH_64BIT_COMPLEX`<br>A string indicating 64BIT_COMPLEX cell depth.                             |
    | `static java.lang.String` | `CELL_DEPTH_64BIT_REAL`<br>A string indicating 64BIT_REAL cell depth.                                   |
    | `static java.lang.String` | `CELL_DEPTH_8BIT_S`<br>A string indicating 8BIT_S cell depth.                                           |
    | `static java.lang.String` | `CELL_DEPTH_8BIT_U`<br>A string indicating 8BIT_U cell depth.                                           |
    | `static java.lang.String` | `CELL_DIMENSION_BAND`<br>A string indicating BAND dimension.                                            |
    | `static java.lang.String` | `CELL_DIMENSION_COLUMN`<br>A string indicating COLUMN dimension.                                        |
    | `static java.lang.String` | `CELL_DIMENSION_ROW`<br>A string indicating ROW dimension.                                              |
    | `static java.lang.String` | `CELL_DIMENSION_TEMPORAL`<br>A string indicating TEMPORAL dimension.                                    |
    | `static java.lang.String` | `CELL_DIMENSION_VERTICAL`<br>A string indicating VERTICAL dimension.                                    |
    | `static java.lang.String` | `CELL_INTERLEVING_BIL`<br>A string indicating BIL interleaving.                                         |
    | `static java.lang.String` | `CELL_INTERLEVING_BIP`<br>A string indicating BIP interleaving.                                         |
    | `static java.lang.String` | `CELL_INTERLEVING_BSQ`<br>A string indicating BSQ interleaving.                                         |
    | `static java.lang.String` | `CELL_REPRESENTION_UNDEFINED`<br>A string indicating UNDEFINED cell representation.                     |
    | `static int`              | `COLUMN_DIMENSION`<br>A integer indicating column dimension.                                            |
    | `static java.lang.String` | `COMPRESSION_DEFLATE`<br>A string indicating DEFLATE compression.                                       |
    | `static java.lang.String` | `COMPRESSION_JP2_C`<br>A string indicating JP2-C compression, but not supported in the current version. |
    | `static java.lang.String` | `COMPRESSION_JP2_F`<br>A string indicating JP2-F compression, but not supported in the current version. |
    | `static java.lang.String` | `COMPRESSION_JPEG_B`<br>Deprecated. <br>A string indicating JPEG-B compression.                         |
    | `static java.lang.String` | `COMPRESSION_JPEG_F`<br>A string indicating JPEG-F compression.                                         |
    | `static java.lang.String` | `COMPRESSION_LT_JP2`<br>A string indicating LT-JP2 compression.                                         |
    | `static java.lang.String` | `COMPRESSION_LT_MG2`<br>A string indicating LT-MG2 compression.                                         |
    | `static java.lang.String` | `COMPRESSION_LT_MG3`<br>A string indicating LT-MG3 compression.                                         |
    | `static java.lang.String` | `COMPRESSION_NONE`<br>A string indicating NONE compression.                                             |
    | `static java.lang.String` | `COMPRESSION_RLE`<br>A string indicating RLE compression.                                               |
    | `static java.lang.String` | `PYRAMID_BIDIRECTION`<br>A string indicating BIDIRECTION pyramid.                                       |
    | `static java.lang.String` | `PYRAMID_DECREASE`<br>A string indicating DECREASE pyramid.                                             |
    | `static java.lang.String` | `PYRAMID_INCREASE`<br>A string indicating INCREASE pyramid.                                             |
    | `static java.lang.String` | `PYRAMID_NONE`<br>A string indicating NONE pyramid.                                                     |
    | `static java.lang.String` | `RESAMPLING_AVERAGE16`<br>A string indicating AVERAGE16 resampling.                                     |
    | `static java.lang.String` | `RESAMPLING_AVERAGE4`<br>A string indicating AVERAGE4 resampling.                                       |
    | `static java.lang.String` | `RESAMPLING_BILINEAR`<br>A string indicating BILINEAR resampling.                                       |
    | `static java.lang.String` | `RESAMPLING_CUBIC`<br>A string indicating CUBIC resampling.                                             |
    | `static java.lang.String` | `RESAMPLING_NN`<br>A string indicating NN resampling.                                                   |
    | `static int`              | `ROW_DIMENSION`<br>A integer indicating row dimension.                                                  |
    | `static int`              | `TEMPORAL_DIMENSION`<br>A integer indicating temporal dimension.                                        |
    | `static int`              | `VERTICAL_DIMENSION`<br>A integer indicating vertical dimension.                                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                              |
    |---------------------|---------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`  | `getBlockingType``()`<br>Returns the blocking type.                                                                 |
    | `java.lang.Long`    | `getBlockSize``(int dimension)`<br>Returns the block size of the specified dimension.                               |
    | `static int`        | `getCellBits``(java.lang.String cellDepth)`                                                                         |
    | `java.lang.String`  | `getCellDepth``()`<br>Returns the cell depth of the current GeoRaster object.                                       |
    | `int`               | `getCellDepthBits``()`<br>Returns the cell bits number of the current GeoRaster object.                             |
    | `java.lang.String`  | `getCellRepresentation``()`<br>Returns the cell representation of the current GeoRaster object.                     |
    | `java.lang.Integer` | `getCompressionQuality``()`<br>Returns the compression quality.                                                     |
    | `java.lang.String`  | `getCompressionType``()`<br>Returns the compression type.                                                           |
    | `java.lang.Long`    | `getDimensionSize``(int dimension)`<br>Returns the dimension size of the specified dimension.                       |
    | `java.lang.String`  | `getInterleaving``()`<br>Returns the interleaving type.                                                             |
    | `java.lang.Long`    | `getPyramidMaxLevel``()`<br>Returns the maximum pyramid level.                                                      |
    | `java.lang.String`  | `getPyramidResampling``()`<br>Returns the pyramid resampling.                                                       |
    | `java.lang.String`  | `getPyramidType``()`<br>Returns the pyramid type.                                                                   |
    | `java.lang.Long`    | `getTotalBlockNumber``(int dimension)`<br>Returns the total number of blocks of the specified dimension.            |
    | `java.lang.Integer` | `getTotalDimensions``()`<br>Returns the total number of dimensions of the current GeoRaster object.                 |
    | `java.lang.Long`    | `getULTCoordinate``(int dimension)`<br>Returns the ULT value of the specified dimension.                            |
    | `void`              | `setCompressionQuality``(java.lang.Integer quality)`<br>Sets the compression quality.                               |
    | `void`              | `setCompressionType``(java.lang.String type)`<br>Sets the compression type.                                         |
    | `void`              | `setDimensionSize``(int dimension, java.lang.Long size)`<br>Sets the dimension size of the specified dimension.     |
    | `void`              | `setPyramidMaxLevel``(java.lang.Long maxlevel)`<br>Sets the maximum pyramid level.                                  |
    | `void`              | `setPyramidType``(java.lang.String pyramidType)`<br>Sets the pyramid type.                                          |
    | `void`              | `setULTCoordinate``(int dimension, java.lang.Long ULTCoordinate)`<br>Sets the ULT value of the specified dimension. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ROW_DIMENSION

          public static final int ROW_DIMENSION

      A integer indicating row dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COLUMN_DIMENSION

          public static final int COLUMN_DIMENSION

      A integer indicating column dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BAND_DIMENSION

          public static final int BAND_DIMENSION

      A integer indicating band dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### VERTICAL_DIMENSION

          public static final int VERTICAL_DIMENSION

      A integer indicating vertical dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEMPORAL_DIMENSION

          public static final int TEMPORAL_DIMENSION

      A integer indicating temporal dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_REPRESENTION_UNDEFINED

          public static final java.lang.String CELL_REPRESENTION_UNDEFINED

      A string indicating UNDEFINED cell representation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_1BIT

          public static final java.lang.String CELL_DEPTH_1BIT

      A string indicating 1BIT cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_2BIT

          public static final java.lang.String CELL_DEPTH_2BIT

      A string indicating 2BIT cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_4BIT

          public static final java.lang.String CELL_DEPTH_4BIT

      A string indicating 4BIT cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_8BIT_U

          public static final java.lang.String CELL_DEPTH_8BIT_U

      A string indicating 8BIT_U cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_8BIT_S

          public static final java.lang.String CELL_DEPTH_8BIT_S

      A string indicating 8BIT_S cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_16BIT_U

          public static final java.lang.String CELL_DEPTH_16BIT_U

      A string indicating 16BIT_U cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_16BIT_S

          public static final java.lang.String CELL_DEPTH_16BIT_S

      A string indicating 16BIT_S cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_32BIT_U

          public static final java.lang.String CELL_DEPTH_32BIT_U

      A string indicating 32BIT_U cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_32BIT_S

          public static final java.lang.String CELL_DEPTH_32BIT_S

      A string indicating 32BIT_S cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_32BIT_REAL

          public static final java.lang.String CELL_DEPTH_32BIT_REAL

      A string indicating 32BIT_REAL cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_64BIT_REAL

          public static final java.lang.String CELL_DEPTH_64BIT_REAL

      A string indicating 64BIT_REAL cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_64BIT_COMPLEX

          public static final java.lang.String CELL_DEPTH_64BIT_COMPLEX

      A string indicating 64BIT_COMPLEX cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DEPTH_128BIT_COMPLEX

          public static final java.lang.String CELL_DEPTH_128BIT_COMPLEX

      A string indicating 128BIT_COMPLEX cell depth.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DIMENSION_ROW

          public static final java.lang.String CELL_DIMENSION_ROW

      A string indicating ROW dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DIMENSION_COLUMN

          public static final java.lang.String CELL_DIMENSION_COLUMN

      A string indicating COLUMN dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DIMENSION_VERTICAL

          public static final java.lang.String CELL_DIMENSION_VERTICAL

      A string indicating VERTICAL dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DIMENSION_BAND

          public static final java.lang.String CELL_DIMENSION_BAND

      A string indicating BAND dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_DIMENSION_TEMPORAL

          public static final java.lang.String CELL_DIMENSION_TEMPORAL

      A string indicating TEMPORAL dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_NONE

          public static final java.lang.String COMPRESSION_NONE

      A string indicating NONE compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_RLE

          public static final java.lang.String COMPRESSION_RLE

      A string indicating RLE compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_JPEG_B

          public static final java.lang.String COMPRESSION_JPEG_B

      Deprecated. A string indicating JPEG-B compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_JPEG_F

          public static final java.lang.String COMPRESSION_JPEG_F

      A string indicating JPEG-F compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_DEFLATE

          public static final java.lang.String COMPRESSION_DEFLATE

      A string indicating DEFLATE compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_LT_MG2

          public static final java.lang.String COMPRESSION_LT_MG2

      A string indicating LT-MG2 compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_LT_MG3

          public static final java.lang.String COMPRESSION_LT_MG3

      A string indicating LT-MG3 compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_LT_JP2

          public static final java.lang.String COMPRESSION_LT_JP2

      A string indicating LT-JP2 compression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_JP2_C

          public static final java.lang.String COMPRESSION_JP2_C

      A string indicating JP2-C compression, but not supported in the current version.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPRESSION_JP2_F

          public static final java.lang.String COMPRESSION_JP2_F

      A string indicating JP2-F compression, but not supported in the current version.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BLOCKING_NONE

          public static final java.lang.String BLOCKING_NONE

      A string indicating NONE blocking.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BLOCKING_REGULAR

          public static final java.lang.String BLOCKING_REGULAR

      A string indicating REGULAR blocking.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_INTERLEVING_BSQ

          public static final java.lang.String CELL_INTERLEVING_BSQ

      A string indicating BSQ interleaving.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_INTERLEVING_BIL

          public static final java.lang.String CELL_INTERLEVING_BIL

      A string indicating BIL interleaving.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CELL_INTERLEVING_BIP

          public static final java.lang.String CELL_INTERLEVING_BIP

      A string indicating BIP interleaving.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PYRAMID_NONE

          public static final java.lang.String PYRAMID_NONE

      A string indicating NONE pyramid.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PYRAMID_INCREASE

          public static final java.lang.String PYRAMID_INCREASE

      A string indicating INCREASE pyramid.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PYRAMID_DECREASE

          public static final java.lang.String PYRAMID_DECREASE

      A string indicating DECREASE pyramid.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PYRAMID_BIDIRECTION

          public static final java.lang.String PYRAMID_BIDIRECTION

      A string indicating BIDIRECTION pyramid.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RESAMPLING_NN

          public static final java.lang.String RESAMPLING_NN

      A string indicating NN resampling.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RESAMPLING_BILINEAR

          public static final java.lang.String RESAMPLING_BILINEAR

      A string indicating BILINEAR resampling.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RESAMPLING_CUBIC

          public static final java.lang.String RESAMPLING_CUBIC

      A string indicating CUBIC resampling.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RESAMPLING_AVERAGE4

          public static final java.lang.String RESAMPLING_AVERAGE4

      A string indicating AVERAGE4 resampling.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RESAMPLING_AVERAGE16

          public static final java.lang.String RESAMPLING_AVERAGE16

      A string indicating AVERAGE16 resampling.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getCellRepresentation

          public java.lang.String getCellRepresentation()

      Returns the cell representation of the current GeoRaster object.
      Returns:
      the cell representation of the current GeoRaster object.

    <!-- -->

    - #### getCellDepth

          public java.lang.String getCellDepth()

      Returns the cell depth of the current GeoRaster object.
      Returns:
      the cell depth of the current GeoRaster object.

    <!-- -->

    - #### getCellDepthBits

          public int getCellDepthBits()

      Returns the cell bits number of the current GeoRaster object.
      Returns:
      the cell bits number of the current GeoRaster object.

    <!-- -->

    - #### getTotalDimensions

          public java.lang.Integer getTotalDimensions()

      Returns the total number of dimensions of the current GeoRaster object.
      Returns:
      the total number of dimensions of the current GeoRaster object.

    <!-- -->

    - #### getDimensionSize

          public java.lang.Long getDimensionSize(int dimension)

      Returns the dimension size of the specified dimension.
      Parameters:
      `dimension` - dimension number

      Returns:
      dimension size of the specified dimension.

    <!-- -->

    - #### setDimensionSize

          public void setDimensionSize(int dimension,
                                       java.lang.Long size)

      Sets the dimension size of the specified dimension.
      Parameters:
      `dimension` - dimension number

      `size` - dimension size of the specified dimension.

    <!-- -->

    - #### getULTCoordinate

          public java.lang.Long getULTCoordinate(int dimension)

      Returns the ULT value of the specified dimension.
      Parameters:
      `dimension` - dimension number

      Returns:
      ult value of the specified dimension.

    <!-- -->

    - #### setULTCoordinate

          public void setULTCoordinate(int dimension,
                                       java.lang.Long ULTCoordinate)

      Sets the ULT value of the specified dimension.
      Parameters:
      `dimension` - dimension number

      `ULTCoordinate` - ult value of the specified dimension.

    <!-- -->

    - #### getBlockingType

          public java.lang.String getBlockingType()

      Returns the blocking type.
      Returns:
      blocking type.

    <!-- -->

    - #### getTotalBlockNumber

          public java.lang.Long getTotalBlockNumber(int dimension)

      Returns the total number of blocks of the specified dimension.
      Parameters:
      `dimension` - dimension number

      Returns:
      total number of blocks of the specified dimension.

    <!-- -->

    - #### getBlockSize

          public java.lang.Long getBlockSize(int dimension)

      Returns the block size of the specified dimension.
      Parameters:
      `dimension` - dimension number

      Returns:
      block size of the specified dimension.

    <!-- -->

    - #### getInterleaving

          public java.lang.String getInterleaving()

      Returns the interleaving type.
      Returns:
      interleaving type.

    <!-- -->

    - #### getPyramidType

          public java.lang.String getPyramidType()

      Returns the pyramid type.
      Returns:
      pyramid type.

    <!-- -->

    - #### setPyramidType

          public void setPyramidType(java.lang.String pyramidType)

      Sets the pyramid type.
      Parameters:
      `pyramidType` - pyramid type

    <!-- -->

    - #### getPyramidResampling

          public java.lang.String getPyramidResampling()

      Returns the pyramid resampling.
      Returns:
      pyramid resampling.

    <!-- -->

    - #### getPyramidMaxLevel

          public java.lang.Long getPyramidMaxLevel()

      Returns the maximum pyramid level.
      Returns:
      maximum pyramid level.

    <!-- -->

    - #### setPyramidMaxLevel

          public void setPyramidMaxLevel(java.lang.Long maxlevel)

      Sets the maximum pyramid level.
      Parameters:
      `maxlevel` - maximum pyramid level

    <!-- -->

    - #### getCompressionType

          public java.lang.String getCompressionType()

      Returns the compression type.
      Returns:
      compression type.

    <!-- -->

    - #### setCompressionType

          public void setCompressionType(java.lang.String type)

      Sets the compression type.
      Parameters:
      `type` - compression type

    <!-- -->

    - #### getCompressionQuality

          public java.lang.Integer getCompressionQuality()

      Returns the compression quality.
      Returns:
      compression quality.

    <!-- -->

    - #### setCompressionQuality

          public void setCompressionQuality(java.lang.Integer quality)

      Sets the compression quality.
      Parameters:
      `quality` - compression quality

    <!-- -->

    - #### getCellBits

          public static int getCellBits(java.lang.String cellDepth)

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

- [Prev Class](ObjectInfo.md)
- [Next Class](SpatialReferenceInfo.md)

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
