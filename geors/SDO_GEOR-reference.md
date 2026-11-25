## 7 SDO_GEOR Package Reference

The SDO_GEOR package contains subprograms (functions and procedures) for creating, modifying, and retrieving information about GeoRaster objects. This chapter presents reference information, with one or more examples, for each subprogram.

The subprograms are presented in alphabetical order in this chapter. They can be grouped into several logical categories, as explained in [GeoRaster PL/SQL API](georaster-overview-and-concepts.md). Many of the subprograms are also discussed in [GeoRaster Database Creation and Management](georaster-database-creation-management.md) and [GeoRaster Data Query and Manipulation](georaster-data-manipulation.md).

Many examples in this chapter refer to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

All SDO_GEOR subprograms can work on GeoRaster objects defined in schemas other than the current connection schema.

- SDO_GEOR.addNODATA
- SDO_GEOR.addSourceInfo
- SDO_GEOR.affineTransform
- SDO_GEOR.calcCompressionRatio
- SDO_GEOR.changeCellValue
- SDO_GEOR.changeCellValues
- SDO_GEOR.changeFormatCopy
- SDO_GEOR.compressJP2
- SDO_GEOR.copy
- SDO_GEOR.createBlank
- SDO_GEOR.createTemplate
- SDO_GEOR.decompressJP2
- SDO_GEOR.deleteControlPoint
- SDO_GEOR.deleteNODATA
- SDO_GEOR.deletePyramid
- SDO_GEOR.evaluateDouble
- SDO_GEOR.evaluateDoubles
- SDO_GEOR.exportTo
- SDO_GEOR.generateAreaWeightedMean
- SDO_GEOR.generateBitmapPyramid
- SDO_GEOR.generateBlockMBR
- SDO_GEOR.generatePyramid
- SDO_GEOR.generateSpatialExtent
- SDO_GEOR.generateSpatialResolutions
- SDO_GEOR.generateStatistics
- SDO_GEOR.generateStatisticsMax
- SDO_GEOR.generateStatisticsMean
- SDO_GEOR.generateStatisticsMedian
- SDO_GEOR.generateStatisticsMin
- SDO_GEOR.generateStatisticsMode
- SDO_GEOR.generateStatisticsSTD
- SDO_GEOR.georeference
- SDO_GEOR.getBandDimSize
- SDO_GEOR.getBeginDateTime
- SDO_GEOR.getBinFunction
- SDO_GEOR.getBinTable
- SDO_GEOR.getBinType
- SDO_GEOR.getBitmapMask
- SDO_GEOR.getBitmapMaskSubset
- SDO_GEOR.getBitmapMaskValue
- SDO_GEOR.getBitmapMaskValues
- SDO_GEOR.getBlankCellValue
- SDO_GEOR.getBlockingType
- SDO_GEOR.getBlockSize
- SDO_GEOR.getCellCoordinate
- SDO_GEOR.getCellDepth
- SDO_GEOR.getCellValue
- SDO_GEOR.getCellValues
- SDO_GEOR.getColorMap
- SDO_GEOR.getColorMapTable
- SDO_GEOR.getCompressionType
- SDO_GEOR.getControlPoint
- SDO_GEOR.getDefaultAlpha
- SDO_GEOR.getDefaultBlue
- SDO_GEOR.getDefaultColorLayer
- SDO_GEOR.getDefaultGreen
- SDO_GEOR.getDefaultPyramidLevel
- SDO_GEOR.getDefaultRed
- SDO_GEOR.getEndDateTime
- SDO_GEOR.getGCPGeorefMethod
- SDO_GEOR.getGCPGeorefModel
- SDO_GEOR.getGeoreferenceType
- SDO_GEOR.getGrayScale
- SDO_GEOR.getGrayScaleTable
- SDO_GEOR.getHistogram
- SDO_GEOR.getHistogramTable
- SDO_GEOR.getID
- SDO_GEOR.getInterleavingType
- SDO_GEOR.getJP2TileSize
- SDO_GEOR.getLayerDimension
- SDO_GEOR.getLayerID
- SDO_GEOR.getLayerOrdinate
- SDO_GEOR.getModelCoordinate
- SDO_GEOR.getModelCoordLocation
- SDO_GEOR.getModelSRID
- SDO_GEOR.getNODATA
- SDO_GEOR.getPyramidMaxLevel
- SDO_GEOR.getPyramidType
- SDO_GEOR.getRasterBlockLocator
- SDO_GEOR.getRasterBlocks
- SDO_GEOR.getRasterData
- SDO_GEOR.getRasterRange
- SDO_GEOR.getRasterSubset
- SDO_GEOR.getScaling
- SDO_GEOR.getSourceInfo
- SDO_GEOR.getSpatialDimNumber
- SDO_GEOR.getSpatialDimSizes
- SDO_GEOR.getSpatialResolutions
- SDO_GEOR.getSpectralResolution
- SDO_GEOR.getSpectralUnit
- SDO_GEOR.getSRS
- SDO_GEOR.getStatistics
- SDO_GEOR.getTotalLayerNumber
- SDO_GEOR.getULTCoordinate
- SDO_GEOR.getVAT
- SDO_GEOR.getVersion
- SDO_GEOR.hasBitmapMask
- SDO_GEOR.hasGrayScale
- SDO_GEOR.hasNODATAMask
- SDO_GEOR.hasPseudoColor
- SDO_GEOR.importFrom
- SDO_GEOR.init
- SDO_GEOR.isBlank
- SDO_GEOR.isOrthoRectified
- SDO_GEOR.isRectified
- SDO_GEOR.isSpatialReferenced
- SDO_GEOR.mask
- SDO_GEOR.mergeLayers
- SDO_GEOR.mosaic
- SDO_GEOR.rectify
- SDO_GEOR.reproject
- SDO_GEOR.scaleCopy
- SDO_GEOR.schemaValidate
- SDO_GEOR.setBeginDateTime
- SDO_GEOR.setBinFunction
- SDO_GEOR.setBinTable
- SDO_GEOR.setBitmapMask
- SDO_GEOR.setBlankCellValue
- SDO_GEOR.setColorMap
- SDO_GEOR.setColorMapTable
- SDO_GEOR.setControlPoint
- SDO_GEOR.setDefaultAlpha
- SDO_GEOR.setDefaultBlue
- SDO_GEOR.setDefaultColorLayer
- SDO_GEOR.setDefaultGreen
- SDO_GEOR.setDefaultPyramidLevel
- SDO_GEOR.setDefaultRed
- SDO_GEOR.setEndDateTime
- SDO_GEOR.setGCPGeorefMethod
- SDO_GEOR.setGCPGeorefModel
- SDO_GEOR.setGrayScale
- SDO_GEOR.setGrayScaleTable
- SDO_GEOR.setHistogramTable
- SDO_GEOR.setID
- SDO_GEOR.setLayerID
- SDO_GEOR.setLayerOrdinate
- SDO_GEOR.setModelCoordLocation
- SDO_GEOR.setModelSRID
- SDO_GEOR.setNODATAMask
- SDO_GEOR.setOrthoRectified
- SDO_GEOR.setRasterType
- SDO_GEOR.setRectified
- SDO_GEOR.setScaling
- SDO_GEOR.setSourceInfo
- SDO_GEOR.setSpatialReferenced
- SDO_GEOR.setSpatialResolutions
- SDO_GEOR.setSpectralResolution
- SDO_GEOR.setSpectralUnit
- SDO_GEOR.setSRS
- SDO_GEOR.setStatistics
- SDO_GEOR.setULTCoordinate
- SDO_GEOR.setVAT
- SDO_GEOR.setVersion
- SDO_GEOR.subset
- SDO_GEOR.updateRaster
- SDO_GEOR.validateBlockMBR
- SDO_GEOR.validateGeoRaster
- SDO_GEOR.warp

### 7.1 SDO_GEOR.addNODATA

#### Format

    SDO_GEOR.addNODATA(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         nodata       IN NUMBER);

or

    SDO_GEOR.addNODATA(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         nodata       IN SDO_RANGE_ARRAY);

#### Description

Adds one or more NODATA values or value ranges, to represent NODATA cells in one layer or all layers in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Layer number in the GeoRaster object. A value of 0 (zero) indicates the object layer.

nodata
Either a single numeric value, or an array of numbers or number ranges. Any NODATA value range is inclusive at the lower bound and exclusive at the upper bound.

The SDO_RANGE_ARRAY type is described in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md)

#### Usage Notes

Some cells of a GeoRaster object may have no meaningful value assigned or collected. Such cells contain a NODATA value are thus called NODATA cells, which means that those cells are not semantically defined. The application is responsible for defining the meaning or significance of cells identified as NODATA cells. For more information about NODATA values and value ranges, see [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

Any NODATA values or value ranges associated with the object layer apply to all sublayers. For an explanation of layers, the object layer, and sublayers, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md).

NODATA values must be in the valid cell value range. Both the lower bound and the upper bound of a NODATA value range must be valid cell values as specified by the cell depth. Because NODATA value ranges are exclusive at the upper bound, if you want to specify the maximum valid cell value as NODATA, you must specify the maximum valid cell value as a single numeric NODATA value.

This procedure associates NODATA values or value ranges with a raster layer incrementally. It removes duplicate values or value ranges and combines adjacent values or value ranges to form a compact representation in the metadata whenever feasible. However, a single numeric NODATA value that is equal to the upper bound of a NODATA value range will not be combined together with the value range because it is not always feasible to calculate the new exclusive upper bound.

To delete one or more NODATA values or value ranges, use the SDO_GEOR.deleteNODATA procedure. To return the NODATA values for a GeoRaster object, use the SDO_GEOR.getNODATA function.

#### Examples

The following example specifies that cells with values that are greater than or equal to 5 and less than 7, or that are equal to 9, are to be considered NODATA cells for the object layer (and thus all sublayers) of a specified GeoRaster object.

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=1 FOR UPDATE;
      SDO_GEOR.addNODATA(gr, 0, sdo_range_array(sdo_range(5,7), sdo_range(9,null)));
      UPDATE georaster_table SET georaster=gr WHERE georid=1;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.2 SDO_GEOR.addSourceInfo

#### Format

    SDO_GEOR.addSourceInfo(
         georaster   IN OUT SDO_GEORASTER,
         sourceInfo  IN VARCHAR2);

#### Description

Adds to the source information for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

sourceInfo
String with source information. Cannot exceed 4096 characters.

#### Usage Notes

The specified `sourceInfo` string is added to the `<sourceInfo>` element in the metadata for the GeoRaster object (described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md)). You can call this procedure as many times as needed to put multiple string values in the `<sourceInfo>` element or to add string values to any existing values.

If you want to replace any existing source information value or values, use the SDO_GEOR.setSourceInfo procedure.

#### Examples

The following example sets and adds some source information for a specified GeoRaster object, and then retrieves the information.

    declare
     gr sdo_georaster;
    begin
     select georaster into gr from georaster_table where georid=1 for update;
     sdo_geor.setSourceInfo(gr, 'Copyright (c) 2002, 2007, Oracle Corporation.');
     sdo_geor.addSourceInfo(gr, 'All rights reserved.');
     update georaster_table set georaster=gr where georid=1;
    end;
    /

    select * from table(select sdo_geor.getSourceInfo(georaster) from georaster_table where id=1);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    Copyright (c) 2002, 2007, Oracle Corporation.
    All rights reserved.

**Parent topic:** SDO_GEOR Package Reference

### 7.3 SDO_GEOR.affineTransform

#### Format

    SDO_GEOR.affineTransform(
         inGeoRaster   IN SDO_GEORASTER,
         translation   IN SDO_NUMBER_ARRAY DEFAULT NULL,
         scales        IN SDO_NUMBER_ARRAY DEFAULT NULL,
         rotatePt      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         rotateAngle   IN NUMBER DEFAULT NULL,
         shear         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         reflection    IN NUMBER DEFAULT NULL,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

         inGeoRaster   IN SDO_GEORASTER,
         translation   IN SDO_NUMBER_ARRAY DEFAULT NULL,
         scales        IN SDO_NUMBER_ARRAY DEFAULT NULL,
         rotatePt      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         rotateAngle   IN NUMBER DEFAULT NULL,
         shear         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         reflection    IN NUMBER DEFAULT NULL,
         storageParam  IN VARCHAR DEFAULT2 DEFAULT NULL,
         rasterBlob    IN OUT NOCOPY_BLOB,
         outArea       OUT SDO_GEOMTRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam IN VARCHAR2 DEFAULT NULL);

#### Description

Performs affine transformation on the input GeoRaster image to produce an output GeoRaster image based on the values of the parameters `translation`, `scales`, `rotatePt`. `rotateAngle`, `shear`, and `reflection`.

#### Parameters

inGeoRaster
GeoRaster object on which to perform the operation. It does not need to be georeferenced. (Georeferencing is explained in [Georeferencing GeoRaster Objects](georaster-database-creation-management.md) and [Advanced Georeferencing](image-processing-virtual-mosaic.md).)

translation
When specified, should contain two integer numeric values with the number of rows and columns to be applied to the translation transformation. The values for row and columns translation are independent of each other, but positive values will translate the image to the right and to the bottom, and negative values will translate the image to the left and to the top. If this parameter is omitted, no translation is performed.

scales
When specified, should contain two numeric values with the scale factor to be applied to the rows and columns to be applied to the scale transformation. The values for row and columns scaling are independent from each other but values between 0 and 1 will reduce the size of the image in rows and/or columns while values greater than 1 will enlarge the size of image is rows and/or columns. If this parameter is omitted, no scaling is performed.

rotatePt
When specified, should contain two numeric value representing the cell space coordinate (row and columns) to be used as the center of the rotation operation. In practical terms, the image feature associated with rotatePt will be the center of the new output image. If this parameter is omitted, the center of the image is assumed.

rotateAngle
When specified, should contain a numeric value between -180 to 180 identifying the angle to be applied to the rotation transformation. A positive value indicates that the rotation will turn to the right and negative value indicates rotation to the left. See usage notes for more information. If this parameter is omitted, no rotation is performed.

shear
When specified, should contain two numeric value between the shear factor to be applied to the x and y coordinates respectively in a shear transformation. The values for row and columns shear are independent from each other. If this parameter is omitted, no shearing is performed.

reflection
When specified, should contain the numeric values 1 or 2, representing vertical or horizontal reflection, respectively. If this parameter is omitted, no reflection is performed.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`

rasterBlob
BLOB to hold the output reflecting the rectification. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

This procedure has two formats:

- The first format generates a GeoRaster object for persistent storage in the database.

- The second format generates a BLOB for temporary storage or immediate use, such as to display data on the screen.

This procedure performs the specified simple affine transformation operations individually or in combination.

For all the possible operations and combinations of operations, this procedure will transform the physical representation of the stored image and build new georeferencing information that preserves the original location of features in the image. Thus, the image might look the same when projected by a visualization tool.

#### Examples

In the following example, the output GeoRaster object will be generated from rotating the source image by -90 degrees (90 degrees to the left).

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      select georaster into gr1 from georaster_table where georid = 1;

      insert into georaster_table values(2, 'Rotated 90 left',
             sdo_geor.init('rdt0',2)) returning georaster into gr2;

      sdo_geor.affineTransform(inGeoRaster   => gr1,
                               translation   => null,
                               scales        => null,
                               rotatePt      => null,
                               rotateAngle   => -90,
                               shear         => null,
                               reflection    => null,
                               storageParam  => 'pyramid=true',
                               outGeoraster  => gr2);

      update georaster_table set georaster = gr2 where georid = 2;
      commit;
    END;

In the following example, the output GeoRaster object will be generated from enlarging the source image two times bigger while rotating it by 15 degrees to the right.

    DECLARE
      gr1 sdo_georaster;
      gr3 sdo_georaster;
    BEGIN
      select georaster into gr2 from georaster_table where georid = 1;

      insert into georaster_table values(3, 'Scaled x 2 Rotated 15',
             sdo_geor.init('rdt0',3)) returning georaster into gr3;

      sdo_geor.affineTransform(inGeoRaster   => gr1,
                               translation   => null,
                               scales        => sdo_number_array(2,2),
                               rotatePt      => null,
                               rotateAngle   => 15,
                               shear         => null,
                               reflection    => null,
                               storageParam  => 'blocksize=(512,512,3)',
                               outGeoraster  => gr3,
                               parallelParam => 'parallel=4');

      update georaster_table set georaster = gr3 where georid = 3;
      commit;
    END;

In the following example, the output GeoRaster object will be generated from shearing the source image by a factor of 5 in both rows and columns:

    DECLARE
      gr1 sdo_georaster;
      gr4 sdo_georaster;
    BEGIN
      select georaster into gr2 from georaster_table where georid = 1;

      insert into georaster_table values(4, 'Shear 5,5',
             sdo_geor.init('rdt0',4)) returning georaster into gr4;

      sdo_geor.affineTransform(inGeoRaster   => gr1,
                               translation   => null,
                               scales        => null,
                               rotatePt      => null,
                               rotateAngle   => null,
                               shear         => sdo_number_array(5,5),
                               reflection    => null,
                               storageParam  => 'pyramid=true',
                               outGeoraster  => gr4,
                               parallelParam => 'parallel=4');

      update georaster_table set georaster = gr4 where georid = 4;
      commit;
    END;

In the following example, the output GeoRaster object will be generated from the vertical reflection of the source image.

    DECLARE
      gr1 sdo_georaster;
      gr5 sdo_georaster;
    BEGIN
      select georaster into gr2 from georaster_table where georid = 1;

      insert into georaster_table values(5, 'Vertical reflection',
             sdo_geor.init('rdt0',5)) returning georaster into gr5;

      sdo_geor.affineTransform(inGeoRaster   => gr1,
                               translation   => null,
                               scales        => null,
                               rotatePt      => null,
                               rotateAngle   => null,
                               shear         => null,
                               reflection    => 1,
                               storageParam  => 'pyramid=true',
                               outGeoraster  => gr5,
                               parallelParam => 'parallel=4');

      update georaster_table set georaster = gr5 where georid = 5;
      commit;
    END;

**Parent topic:** SDO_GEOR Package Reference

### 7.4 SDO_GEOR.calcCompressionRatio

#### Format

    SDO_GEOR.calcCompressionRatio(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the compression ratio of a specified GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The compression ratio is the sum of the sizes of all raster blocks (including pyramids) in the uncompressed GeoRaster object divided by the sum of these sizes in the compressed form of the object. If the input GeoRaster object is not compressed, the compression ratio is 1 (that is, 1:1).

For a given original GeoRaster object, the greater the compression ratio, the smaller is the compressed GeoRaster object. For example, a compression ratio of 20 (that is, 20:1), the data is compressed to 5 percent of its original size.

For more information about GeoRaster compression, see [Compression and Decompression](georaster-overview-and-concepts.md).

#### Examples

The following example returns the compression type and compression ratio for the GeoRaster object in the GEORASTER column of table GEORASTER_TABLE where the GEORID column value is 1.

    SELECT sdo_geor.getCompressionType(georaster) compType,
        sdo_geor.calcCompressionRatio(georaster) compRatio
      FROM georaster_table WHERE georid=1;

**Parent topic:** SDO_GEOR Package Reference

### 7.5 SDO_GEOR.changeCellValue

#### Format

    SDO_GEOR.changeCellValue(
         georaster    IN OUT SDO_GEORASTER,
         window       IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         newCellValue IN NUMBER,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.changeCellValue(
         georaster    IN OUT SDO_GEORASTER,
         window       IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         newCellValue IN NUMBER,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Changes the value of raster cells in a specified window of a GeoRaster object to a single new value.

#### Parameters

georaster
GeoRaster object.

window
Window in which to change the values of all cells to `newCellValue`. The data type can be SDO_NUMBER_ARRAY or SDO_GEOMETRY. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, see the Usage Notes for SDO_SRID requirements and other information.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

newCellValue
The new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the `cellDepth` value for the GeoRaster object.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish.

This procedure can be used to mask, or conceal, parts of an image. For example, you can change irrelevant parts of an image to a dull color before displaying the image, to help people to focus on the relevant parts.

If the `window` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `window` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `window` parameter specifies a nonrectangular SDO_GEOMETRY object, this function calculates the MBR of the geometry and update the cells inside that MBR, including the cells on the boundary of the MBR.

If the `window` parameter specifies a geodetic MBR, it cannot cross the date line meridian. For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

If `georaster` is a blank GeoRaster object and the whole area is updated, the result is a blank GeoRaster object with the `blankCellValue` value set to `newCellValue`.

If `georaster` is a blank GeoRaster object and it is only partially updated, the result is a nonblank GeoRaster object with the original `blankCellValue` and `newCellValue` values set according to the `window` parameter and the `bandNumbers` or `layerNumbers` parameter.

If `georaster` is a nonblank GeoRaster object, the result is a nonblank GeoRaster object, even if all cells are set to the `newCellValue` value.

If `georaster` is null, this procedure performs no operation. If `georaster` is invalid, an exception is raised.

If any pyramids are defined on the GeoRaster object, the corresponding cell values for the pyramids are updated.

To return the value of a single cell located anywhere in the GeoRaster object, use the SDO_GEOR.getCellValue function.

#### Examples

The following example changes the value of all cells to 151 in a specified window in band number 1. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=110 FOR UPDATE;
      sdo_geor.changeCellValue(gr, sdo_number_array(100,67,134,113), '1', 151);
      UPDATE georaster_table SET georaster=gr WHERE georid=110;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.6 SDO_GEOR.changeCellValues

#### Format

    SDO_GEOR.changeCellValues(
         georaster     IN OUT SDO_GEORASTER,
         rowNumbers    IN SDO_NUMBER_ARRAY,
         colNumbers    IN SDO_NUMBER_ARRAY,
         bandNumber    IN NUMBER,
         newCellValues IN SDO_NUMBER_ARRAY,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.changeCellValues(
         georaster     IN OUT SDO_GEORASTER,
         ptGeom        IN SDO_GEOMETRY,
         layerNumber   IN NUMBER,
         newCellValues IN SDO_NUMBER_ARRAY,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Changes the value of raster cells specified by row/column arrays or by a multipoint geometry to new values.

#### Parameters

georaster
GeoRaster object.

rowNumbers
Numbers of the rows that contains the cells whose values are to be changed.

colNumbers
Numbers of the columns that contains the cells whose values are to be changed.

bandNumber
Number of the physical band that contains the cells whose value is to be changed.

ptGeom
Multipoint geometry that identifies the cells whose values are to be changed.

layerNumber
Number of the logical layer that contains the cells whose value is to be changed. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

newCellValues
The new cell value for each cell inside the window in the specified bands or layers. The value must be in the range designated by the `cellDepth` value for the GeoRaster object.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish.

This procedure can be used to mask, or conceal, parts of an image. For example, you can change irrelevant parts of an image to a dull color before displaying the image, to help people to focus on the relevant parts.

In the `ptGeom` SDO_GEOMETRY object, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `ptGeom` parameter geometry and the model space are different, the `ptGeom` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If `georaster` is null, this procedure performs no operation. If `georaster` is invalid, an exception is raised.

If any pyramids are defined on the GeoRaster object, the corresponding cell values for the pyramids are updated.

To return the values of cells located anywhere in the GeoRaster object, use the SDO_GEOR.getCellValues function.

#### Examples

The following example changes the value of two cells to 151 and 152 in band number 1. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=110 FOR UPDATE;
      sdo_geor.changeCellValues(gr, sdo_number_array(100,67),sdo_number_array(134,113), 1,
         sdo_number_array(151,152));
      UPDATE georaster_table SET georaster=gr WHERE georid=110;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.7 SDO_GEOR.changeFormatCopy

#### Format

    SDO_GEOR.changeFormatCopy(
         inGeoRaster   IN SDO_GEORASTER,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.changeFormatCopy(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Makes a copy of an existing GeoRaster object using a different storage format (for example, changing the blocking, cell depth, or interleaving).

#### Parameters

inGeoRaster
The SDO_GEORASTER object whose format is to be copied.

pyramidLevel
A number specifying the pyramid level of the source GeoRaster object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The SDO_GEORASTER object to hold the copy. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

This procedure creates a new GeoRaster object that has the specified changes, based on the original GeoRaster object or a specified pyramid level of it. After you use this procedure, you can check to ensure that the desired changes were made in the copy, and then discard the original GeoRaster object if you wish.

If you use the format that does not include the `pyramidLevel` parameter, the copy is based on the original GeoRaster object (pyramidLevel=0).

If the copy is to be made from a pyramid of the original GeoRaster object (`pyramidLevel` \> 0), and if the original GeoRaster object is georeferenced, georeferencing information is generated for the resulting GeoRaster object only when the georeference is a valid polynomial transformation. The resulting object's row and column ultCoordinates are set to (0,0).

To compress or decompress a GeoRaster object, use the `compression` keyword in the `storageParam` parameter. (There is no separate GeoRaster function or procedure for compressing or decompressing a GeoRaster object.)

If `inGeoRaster` is null, this procedure performs no operation.

If `storageParam` is null, `inGeoRaster` is copied to `outGeoRaster`.

If `outGeoRaster` has any raster data, it is deleted before the copy operation.

`inGeoRaster` and `outGeoRaster` must be different GeoRaster objects.

If pyramid data exists for `inGeoRaster`, any upper level pyramid data is copied to `outGeoRaster` unless the `storageParam` string contains `pyramid=FALSE`.

An exception is raised if one or more of the following are true:

- `inGeoRaster` is invalid.

- `outGeoRaster` has not been initialized.

- A raster data table for `outGeoRaster` does not exist and `outGeoRaster` is not a blank GeoRaster object.

#### Examples

The following example creates a GeoRaster object that is the same as the input object except that the block size is set to 2048 for both dimensions. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
        gr1 sdo_georaster;
        gr2 sdo_georaster;
    BEGIN
        SELECT georaster INTO gr2 from georaster_table WHERE georid=11 FOR UPDATE;
        SELECT georaster INTO gr1 from georaster_table WHERE georid=1;

        sdo_geor.changeFormatCopy(gr1, 'blocksize=(2048,2048)', gr2);
        UPDATE georaster_table SET georaster=gr2 WHERE georid=11;
        COMMIT;
    END;
    /

The following example creates a GeoRaster object that is the same as the input object except that raster data is compressed to deflate format and the compression process is running in parallel. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
        gr1 sdo_georaster;
        gr2 sdo_georaster;
    BEGIN
        SELECT georaster INTO gr2 from georaster_table WHERE georid=11 FOR UPDATE;
        SELECT georaster INTO gr1 from georaster_table WHERE georid=1;

        sdo_geor.changeFormatCopy(gr1, 'compression=deflate parallel=4', gr2);
        UPDATE georaster_table SET georaster=gr2 WHERE georid=11;
        COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.8 SDO_GEOR.compressJP2

#### Format

    SDO_GEOR.compressJP2(
         inGeoRaster    IN SDO_GEORASTER,
         compressParam  IN VARCHAR2,
         outGeoRaster   IN OUT SDO_GEORASTER);

#### Description

Compresses the image in a GeoRaster object using JPEG 2000 compression.

#### Parameters

inGeoRaster
The SDO_GEORASTER object whose data is to be compressed.

compressParam
A string specifying one or more keywords for the compression parameter. For an explanation of the available keywords, see the table in the Usage Notes.

outGeoRaster
The SDO_GEORASTER object to hold the result of the compression. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

#### Usage Notes

The output compressed image is in JPEG 2000 (JP2) file format and stored in one raster block of the `outGeoRaster` object. There are no pyramid raster blocks stored in the raster data table, because the pyramids are stored in the JP2 file as part of the compression.

If not specified in `rlevel` keyword of `compressParam`, the maximum number of pyramid level is calculated as: `floor(log2(tsize))`, where `tsize` is the minimal value of the `tilesize` parameter values for rows and columns. If the `tiling` parameter value is`false`, `tsize` is the minimal value of the image height and width.

If neither `ratio` nor `psnr` is specified, the compression is loss-less

This procedure supports 8–bit and 16–bit source GeoRaster objects. The maximum of number of tiles allowed is 65535.

The following table lists the available `compressParam` keywords for JPEG 2000 (JP2) compression.

Table 7-1 compressParam Keywords for JPEG 2000 (JP2) Compression

| Keyword                                    | Explanation                                                                                                                                                                                                                                                                                                                                                                                               |
|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| codeBlockSize=(cbrow, cbcol)               | Specifies the code block row and column size, where `cbrow` and `cbcol` are the size of the code block in rows and columns, respectively. It must be in the range of \[4, 1024\] and cbrow \* cbcol \<= 4096. By default, it is 64 x 64.                                                                                                                                                                  |
| dwt=reversible \| irreversible             | Specifies the discrete wavelet transform, where `reversible` means to use the DWT 5–3 transform, and `irreversible` means to use the DWT 9–7 transform. Irreversible transforms always result in lossy compression.                                                                                                                                                                                       |
| mct=true \| false                          | Specifies whether to use multiple component transform. By default, RGB-\>YCC conversion is used if there are 3 bands or more.                                                                                                                                                                                                                                                                             |
| precinctSize=(pcrow, pccol)                | Specifies the precinct size, where `pcrow` and `pccol` are the size of the precinct in rows and columns, respectively. By default it is 512 x 512 on each resolution.                                                                                                                                                                                                                                     |
| progressOrder=LRCP\|RLCP\|RPCL\|PCRL\|CPRL | Specifies the progression order: `LRCP` (layer-resolution-component-position progressive, or rate scalable), `RLCP` (resolution-layer-component-position progressive, or resolution scalable), `RPCL` (resolution-position-component-layer progressive), `PCRL` (position-component-resolution-layer progressive), or `CPRL` (component-position-resolution-layer) progressive. By default, it is `LRCP`. |
| psnr=(p1, p2, p3, ...)                     | Specifies the peak signal-to-noise ratio (PSNR), where p1, p2, p3, ... are the compression PSNR for layer 1, 2, 3, and so on of the JP2 code stream. It should be in increasing order. Example: psnr=(30, 40, 50). By default, the compression is loss-less. This parameter cannot be specified together with the `ratio` parameter.                                                                      |
| ratio=(r1, r2, r3, ...)                    | Specifies the compression ratio, where p1, p2, p3, ... are the compression ratios for layers 1, 2, 3, and so on of the JP2 code stream. It should be in decreasing order. Example: ratio=(30, 20, 10). By default, the compression is loss-less. This parameter cannot be specified together with the `psnr` parameter.                                                                                   |
| rlevel=n                                   | Specifies the number of decompositions of the wavelet transform, and thus the number of pyramids of the image. By default, the level of decomposition is floor(log2(tileSize)).                                                                                                                                                                                                                           |
| tileSize=(trow, tcol)                      | `trow` and `tcol` specify the row and column size of the tile. If the tile size is greater than the image size, no tiling is applied.                                                                                                                                                                                                                                                                     |
| tiling=true \| false                       | Specifies whether to use tiling in the JPEG2000 compression. By default, tiling is `true`. If `tiling` is `true` and if `tileSize` is not set, the default tile size is 512 x 512.                                                                                                                                                                                                                        |

**Note:**

For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

#### Examples

The following example creates a JPEG 2000 compressed GeoRaster object from the original object. The JP2 file internal tile size is 512 by 512 and the compression ratio values for JP2 layers 1, 2, and 3 are 30, 20, and 10, respectively. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (4, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=1;

      sdo_geor.compressJP2(gr1,’tilesize=(512, 512), ratio=(30, 20, 10)’, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.9 SDO_GEOR.copy

#### Format

    SDO_GEOR.copy(
         inGeoRaster  IN SDO_GEORASTER,
         outGeoRaster IN OUT SDO_GEORASTER);

#### Description

Makes a copy of an existing GeoRaster object.

#### Parameters

inGeoRaster
GeoRaster object to be copied.

outGeoRaster
GeoRaster object to hold the result of the copy operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

#### Usage Notes

The `outGeoRaster` object is an exact copy of the `inGeoRaster` object. To make any changes to the output GeoRaster object during a copy operation, use the SDO_GEOR.changeFormatCopy procedure.

If `inGeoRaster` is null, this procedure performs no operation.

If `outGeoRaster` has any raster data, it is deleted before the copy operation.

`inGeoRaster` and `outGeoRaster` must be different GeoRaster objects.

If pyramid data exists for `inGeoRaster`, the pyramid data is copied to `outGeoRaster`.

An exception is raised if one or more of the following are true:

- `inGeoRaster` is invalid.

- `outGeoRaster` has not been initialized.

- A raster data table for `outGeoRaster` does not exist and `outGeoRaster` is not a blank GeoRaster object.

#### Examples

The following example inserts an initialized GeoRaster object (`gr2`) into the GEORASTER column of table GEORASTER_TABLE, makes `gr2` an exact copy of another GeoRaster object (`gr1`), and updates the row that had been inserted using `gr2` for the GEORASTER column value. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table VALUES (11, sdo_geor.init('RDT_11', 1))
        RETURNING georaster INTO gr2;
      SELECT georaster INTO gr1 from georaster_table WHERE georid=1;

      sdo_geor.copy(gr1, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=11;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.10 SDO_GEOR.createBlank

#### Format

    SDO_GEOR.createBlank(
         rasterType      IN INTEGER,
         ultCoord        IN SDO_NUMBER_ARRAY,
         dimSizes        IN SDO_NUMBER_ARRAY,
         cellValue       IN NUMBER,
         rasterDataTable IN VARCHAR2 DEFAULT NULL,
         rasterID        IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEORASTER;

#### Description

Creates a blank GeoRaster object, in which all cells have the same value; the object must then be registered in the xxx_SDO_GEOR_SYSDATA views (see the Usage Notes).

#### Parameters

rasterType
The 5-digit rasterType attribute value, as specified in [rasterType Attribute](georaster-datatypes.md).

ultCoord
An array of the upper-left coordinate integer values for the GeoRaster object. The default value is `(0,0)` for a GeoRaster object without a band dimension, and `(0,0,0)` for a GeoRaster object with a band dimension. If this parameter is null, the default value of 0 is used for each dimension. If a value in the specified array is null, the default value of 0 is used for the corresponding dimension. The value for the band dimension must be 0, and you do not need to specify it. (If you specify an array of values, the number of values must not be less than the number of the spatial dimensions or more than the number of total dimensions.)

dimSizes
The number of cells along each dimension. The number of values in the array must be equal to the total number of dimensions, and the size of each dimension must be explicitly specified. The row and column dimension sizes must be greater than 1.

cellValue
The cell value for all raster cells in the created GeoRaster object. Must be from 0 to 255, because the cell depth of the created GeoRaster object is `8BIT_UNSIGNED`.

rasterDataTable
Name of the object table of type SDO_RASTER that stores the cell data blocks. Must not contain spaces, period separators, or mixed-case letters in a quoted string; the name is always converted to uppercase when stored in an SDO_GEORASTER object. The RDT should be in the same schema as its associated GeoRaster table. If you do not specify this parameter, GeoRaster generates a unique table name to be used for the raster data table. If you specify this parameter and the table already exists but is not an object table of type SDO_RASTER, an exception is raised.

rasterID
Number that uniquely identifies the cell blocks of this GeoRaster object in the raster data table. If you do not specify this parameter, a unique sequence number is generated for the ID.

#### Usage Notes

After creating the blank GeoRaster object and before performing any operations on the object, you must register it in the xxx_SDO_GEOR_SYSDATA views by inserting the empty GeoRaster object into a GeoRaster table. (The xxx_SDO_GEOR_SYSDATA views are described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md). GeoRaster operations are described in [GeoRaster Database Creation and Management](georaster-database-creation-management.md) and [GeoRaster Data Query and Manipulation](georaster-data-manipulation.md).)

The created GeoRaster object has no spatial reference information; therefore, its spatial extent geometry has a null SRID (coordinate system) value. The spatial extent geometry reflects the `ultCoord` and `dimSizes` values.

This function does not require that the specified raster data table exist. However, the table must exist before any raster data can be inserted into it.

Although the cell depth of the created GeoRaster object is `8BIT_UNSIGNED`, you can change the cell depth after you create the blank GeoRaster object by calling the SDO_GEOR.changeFormatCopy procedure. You can then call the SDO_GEOR.setBlankCellValue procedure to reset the cell value in a different range.

For guidelines that apply to the SDO_GEOR.createBlank and SDO_GEOR.init functions when a table has multiple GeoRaster object columns, see the Usage Notes for the SDO_GEOR.init function.

An exception is raised if any value for an input parameter is invalid.

#### Examples

The following example inserts a row containing a blank GeoRaster object into the table. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    INSERT INTO georaster_table (georid, georaster) VALUES (
      1,
      sdo_geor.createBlank(20001, SDO_NUMBER_ARRAY(0,0),
                           SDO_NUMBER_ARRAY(1024,1024), 255, 'RDT_1')
    );

**Parent topic:** SDO_GEOR Package Reference

### 7.11 SDO_GEOR.createTemplate

#### Format

    SDO_GEOR.createTemplate(
         georaster    IN OUT SDO_GEORASTER,
         rasterType   IN INTEGER,
         rasterSpec   IN VARCHAR2,
         maskLayers   IN VARCHAR2 DEFAULT NULL,
         initRDTEntry IN VARCHAR2 DEFAULT NULL);

#### Description

Populates a GeoRaster object with metadata of a general pattern, and optionally inserts entries with empty raster blocks into its raster data table.

#### Parameters

georaster
The GeoRaster object to be updated.

rasterType
The 5-digit rasterType attribute value, as specified in [rasterType Attribute](georaster-datatypes.md).

rasterSpec
A string with raster specification parameters, as explained in the Usage Notes.

maskLayers
A string identifying the logical layer numbers on which there are associated bitmap masks. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

initRDTEntry
The string `TRUE` causes the raster data table to be populated; the string `FALSE` causes the raster data table not to be populated. If you do not specify this parameter, the raster data table is not populated.

#### Usage Notes

This function populates a GeoRaster object with metadata of a general pattern and optionally inserts proper rows (with empty raster blocks) into its raster data table. If the raster data table is to be populated, the raster data table must exist and the GeoRaster object must have been registered in the GeoRaster SYSDATA table.

In general, only use this procedure with an empty GeoRaster object to populate its XML metadata and raster blocks. If you use an existing (good) GeoRaster object, the GeoRaster object will be replaced with the new template object upon update.

The `rasterSpec` parameter must be a quoted string that contains one or more keyword-value pairs. The following keywords are supported for this parameter:

- `blocking` (for example, `blocking=TRUE`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `blocksize` (for example, `blocksize=(512,512,3)`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `cellDepth` (for example, `cellDepth=8BIT_S`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `compression` (for example, `compression=JPEG-F`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `dimSize` (for example, `dimSize=(512,512,3)`): Specifies the row, column, and band dimension sizes. This keyword must be specified and must be consistent with the `rasterType` parameter.

- `interleaving` (for example, `interleaving=BIP`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `quality` (for example, `quality=75`). For an explanation of this keyword, see [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

  The `resampling` keyword is ignored if `rLevel` is not set.

- `rLevel` (for example, `rLevel=2`): Specifies the maximum pyramid reduction level. Must be a positive integer. If you specify this keyword, the pyramid type is set to `DECREASE` in the metadata; otherwise, the pyramid type is set to `NONE`.

- `ultCoord` (for example, `ultCoord=(0,0,0)`): Specifies the upper-left coordinate integer values for the GeoRaster object. The default value is 0 for all the dimensions. The value for the band dimension must be 0.

(Note that the following keywords in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md) are not supported for the `rasterSpec` parameter: `bitmapmask` and `pyramid`.)

If the `compression` keyword in the `rasterSpec` parameter is set as `JP2-F`, the blocking defaults to non-blocking no matter what the `rasterSpec` parameter specifies. If the `rlevel` keyword in the `rasterSpec` parameter is not set and `compression` is `JP2-F`, the pyramid maximum level in the GeoRaster metadata defaults to floor( log2(imageSize)), where `imageSize` is the minimum of the image row and column size. The pyramid maximum level should be adjusted later if the actual data has different levels of resolutions.

For more information about using this function in developing GeoRaster applications, see [Using Template-Related Subprograms to Develop GeoRaster Applications](georaster-data-manipulation.md).

#### Examples

The following example populates a GeoRaster object with metadata and initial raster data table rows.

    DECLARE
      gr sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (1, sdo_geor.init('RDT_1'))
        RETURNING georaster into gr;
      sdo_geor.createTemplate(gr, 21001,
                           'dimSize=(512,512,3) blocking=false rlevel=2',
                           null, 'TRUE');
      UPDATE georaster_table set georaster=gr where georid=1;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.12 SDO_GEOR.decompressJP2

#### Format

    SDO_GEOR.decompressJP2(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_NUMBER_ARRAY,
         bandNumbers   IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoraster  IN OUT SDO_GEORASTER);

or

    SDO_GEOR.decompressJP2(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_GEOMETRY,
         layerNumbers  IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoraster  IN OUT SDO_GEORASTER);

#### Description

Decompress the JPEG 2000 compressed GeoRaster image into a GeoRaster object.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be decompressed.

pyramidLevel
A number specifying the pyramid level to be decompressed in the source GeoRaster object.

cropArea
Crop area definition. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

#### Usage Notes

In the `storageParam` parameter, any `bitmapmask`, `compression`, `quality`, and `pyramid` keywords are ignored.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

#### Examples

The following example creates an uncompressed GeoRaster object that contains only specified bands from a specified window from the original object. The original object’s raster data is compressed in JPEG 2000 compression. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor.decompressJP2(gr1, 0, sdo_geometry(2003, NULL, NULL,
                                   sdo_elem_info_array(1, 1003, 3),
                                   sdo_ordinate_array(0,256,255,511)),
                      '3,1-2',’blocksize=(512, 512, 3)’, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.13 SDO_GEOR.deleteControlPoint

#### Format

    SDO_GEOR.deleteControlPoint (
         inGeoraster     IN SDO_GEORASTER,
         controlPointID  IN VARCHAR2);

#### Description

Deletes a ground control point (GCP) that has the specified control point ID value.

#### Parameters

inGeoraster
GeoRaster object.

controlPointID
Control point ID for `inGeoraster`. Must be a string not more than 32 characters.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

If the controlPointID is null, empty or not found in the existing GCPs stored in the GeoRaster object metadata, an exception is raised. If a GCP with the specified point ID is found, that GCP is deleted from the georeferencing model.

#### Examples

The following example deletes the GCP that has the ID value 23 in a specified GeoRaster object.

    DECLARE
       gr1  sdo_georaster;
    BEGIN
       SELECT georaster INTO gr1 from herman.georaster_table WHERE georid=10 FOR UPDATE;
       sdo_geor.deleteControlPoint(gr1, '23');
       UPDATE georaster_table SET georaster=gr1 WHERE georid=10;
       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.14 SDO_GEOR.deleteNODATA

#### Format

    SDO_GEOR.deleteNODATA(title
         georaster   IN OUT SDO_GEORASTER
         layerNumber IN NUMBER
         nodata      IN NUMBER);

or

    SDO_GEOR.deleteNODATA(
         georaster   IN OUT SDO_GEORASTER
         layerNumber IN NUMBER
         nodata      IN SDO_RANGE_ARRAY);

#### Description

Deletes one or more NODATA values or value ranges.

#### Parameters

georaster
GeoRaster object.

layerNumber
Layer number in the GeoRaster object. A value of 0 (zero) indicates the object layer.

nodata
Either a single numeric value, or an array of numbers or number ranges. Any NODATA value range is inclusive at the lower bound and exclusive at the upper bound.

The SDO_RANGE_ARRAY type is described in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md)

#### Usage Notes

When a NODATA value or value range is deleted, the cell depth of the GeoRaster object is taken into consideration to generate the correct new ranges. If the cell depth specifies floating cell values, you can only remove existing single numeric NODATA values or remove a sub-range from an existing NODATA value range.

For information about NODATA values and value ranges, see [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

To add one or more NODATA values or value ranges, use the SDO_GEOR.addNODATA procedure. To return the NODATA values for a GeoRaster object, use the SDO_GEOR.getNODATA function.

#### Examples

The following example removes cell value 9 from the NODATA metadata associated with the object layer.

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=0 FOR UPDATE;
      SDO_GEOR.deleteNODATA(gr, 0, 9);
      UPDATE georaster_table SET georaster=gr WHERE georid=0;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.15 SDO_GEOR.deletePyramid

#### Format

    SDO_GEOR.deletePyramid(
         georaster     IN OUT SDO_GEORASTER,
         pyramidLevel  IN NUMBER DEFAULT NULL);

#### Description

Deletes the pyramid data of a GeoRaster object from the given pyramid level and above.

#### Parameters

georaster
GeoRaster object for which pyramid data is to be deleted.

pyramidLevel
The level of pyramid (and above) for which to delete pyramid data. By default, all the pyramid data is deleted.

#### Usage Notes

For information about pyramid data, see [Pyramids](georaster-overview-and-concepts.md).

If `georaster` is null or has no pyramid data, this procedure performs no operation.

An exception is raised if `georaster` is invalid or if the value of `pyramidLevel` is less than 1.

#### Examples

The following example deletes the pyramid data for a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
    BEGIN
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=21;

      sdo_geor.deletePyramid(gr1);
      UPDATE georaster_table SET georaster=gr1 WHERE georid=21;
      COMMIT;
    END;
    /

The following example deletes the pyramid data for a GeoRaster object where the pyramid level is greater than or equal to 3. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
    BEGIN
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=21;

      sdo_geor.deletePyramid(gr1, 3);
      UPDATE georaster_table SET georaster=gr1 WHERE georid=21;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.16 SDO_GEOR.evaluateDouble

#### Format

    SDO_GEOR.evaluateDouble(
         georaster           IN SDO_GEORASTER,
         pyramidLevel        IN NUMBER,
         row                 IN NUMBER,
         column              IN NUMBER,
         bands               IN VARCHAR2,
         interpolationMethod IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.evaluateDouble(
         georaster           IN SDO_GEORASTER,
         pyramidLevel        IN NUMBER,
         ptGeom              IN SDO_GEOMETRY,
         layers              IN VARCHAR2,
         interpolationMethod IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Evaluates a direct location using a specified interpolation method, and returns the raster values (double precision numbers) for the specified bands or layers for that location.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the location whose raster values are to be returned.

row
The row coordinate of the location whose raster values are to be returned. This can be a floating point number.

column
The column coordinate of the location whose raster values are to be returned. This can be a floating point number.

bands
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

ptGeom
Point geometry that identifies the direct location whose raster values are to be returned.

layers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4). (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

interpolationMethod
A quoted string containing one or more keywords, each with an appropriate value. See the Usage Notes for information about the available keywords and values.

#### Usage Notes

This function returns interpolated raster values in double precision. In GeoRaster, the original cell values are always associated with the center of the cells, regardless of whether the cell coordinate system type is center-based or upperleft-based.

Identify the location in the GeoRaster object either by specifying its row, column, and band numbers in cell coordinate space, or by specifying a point geometry in either model coordinate space or cell coordinate space.

`interpolationMethod` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `interpolationMethod` (for example, `interpolationMethod=NN`): Specifies the interpolation method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the interpolation method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the interpolation calculation is a NODATA value, the result of the interpolation is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

If `interpolationMethod` is specified as `'interpolationMethod=NN'`, this function is equivalent to calling the SDO_GEOR.getCellValue function.

#### Examples

The following examples return the raster values for a specified location in the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

The examples show the two function formats, and they return the same values for the same location specified in either cell space or model space.

    SELECT SDO_GEOR.evaluateDouble(a.georaster, 0,
        10.2, 10.3,
        '0-2',
        'interpolationMethod=BILINEAR')
      FROM georaster_table a WHERE georid=21;

    SDO_GEOR.EVALUATEDOUBLE(A.GEORASTER,0,10.2,10.3,'0-2','interpolationMethod=BILINEAR')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(86.68, 135.68, 31.72)

    1 row selected.

    SELECT SDO_GEOR.evaluateDouble(a.georaster, 0,
        SDO_GEOMETRY(2001, 82394, SDO_POINT_TYPE(18492.775, 1012881.9, NULL),
                     NULL, NULL),
        '1-3',
        'interpolationMethod=BILINEAR')
      FROM georaster_table a WHERE georid=21;

    SDO_GEOR.EVALUATEDOUBLE(A.GEORASTER,0,SDO_GEOR.GETMODELCOORDINATE(A.GEORASTER,0,
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(86.68, 135.68, 31.72)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.17 SDO_GEOR.evaluateDoubles

#### Format

    SDO_GEOR.evaluateDoubles(
         georaster           IN SDO_GEORASTER,
         pyramidLevel        IN NUMBER,
         rows                IN SDO_NUMBER_ARRAY,
         cols                IN SDO_NUMBER_ARRAY,
         band                IN NUMBER,
         interpolationMethod IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.evaluateDoubles(
         georaster           IN SDO_GEORASTER,
         pyramidLevel        IN NUMBER,
         ptGeom              IN SDO_GEOMETRY,
         layer               IN NUMBER,
         interpolationMethod IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Evaluates multiple locations using a specified interpolation method, and returns the raster values (double precision numbers) for the specified band or layer for those locations.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the locations whose raster values are to be returned.

row
The row coordinates of the locations whose raster values are to be returned.

column
The column coordinates of the locations whose raster values are to be returned.

band
Number of the physical band that contains the cell whose value is to be returned.

ptGeom
Multipoint geometry that identifies the cells whose values are to be returned.

layers
Number of the logical layer that contains the cell whose value is to be returned. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

interpolationMethod
A quoted string containing one or more keywords, each with an appropriate value. See the Usage Notes for information about the available keywords and values.

#### Usage Notes

This function returns interpolated raster values in double precision. In GeoRaster, the original cell values are always associated with the center of the cells, regardless of whether the cell coordinate system type is center-based or upperleft-based.

`interpolationMethod` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `interpolationMethod` (for example, `interpolationMethod=NN`): Specifies the interpolation method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the interpolation method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the interpolation calculation is a NODATA value, the result of the interpolation is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

If `interpolationMethod` is specified as `'interpolationMethod=NN'`, this function is equivalent to calling the SDO_GEOR.getCellValues function.

#### Examples

The following example returns the raster values for specified locations in the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT SDO_GEOR.evaluateDoubles(a.georaster, 0,SDO_NUMBER_ARRAY(10.2,11.5),SDO_NUMBER_ARRAY(9.2,8.3),0,
        'interpolationMethod=BILINEAR')
      FROM georaster_table a WHERE georid=21;

    SDO_GEOR.EVALUATEDOUBLES(A.GEORASTER,0,SDO_NUMBER_ARRAY(10.2,11.5),SDO_NUMBER_ARRAY(9.2,8.3),0,'interpolationMethod=BILINEAR')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(86.68, 135.68)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.18 SDO_GEOR.exportTo

#### Format

    SDO_GEOR.exportTo(
         georaster     IN SDO_GEORASTER,
         subsetParam   IN VARCHAR2,
         r_destFormat  IN VARCHAR2,
         r_destType    IN VARCHAR2,
         r_destName    IN VARCHAR2,
         h_destFormat  IN VARCHAR2 DEFAULT NULL,
         h_destType    IN VARCHAR2 DEFAULT NULL,
         h_destName    IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.exportTo(
         georaster    IN SDO_GEORASTER,
         subsetParam  IN VARCHAR2,
         r_destFormat IN VARCHAR2,
         r_destBLOB   IN OUT NOCOPY BLOB);

or

    SDO_GEOR.exportTo(
         georaster     IN SDO_GEORASTER,
         subsetParam   IN VARCHAR2,
         r_destFormat  IN VARCHAR2,
         r_destBLOB    IN OUT NOCOPY BLOB,
         h_destFormat  IN VARCHAR2 DEFAULT NULL,
         h_destCLOB    IN  OUT NOCOPY CLOB DEFAULT NULL);

#### Description

Exports a GeoRaster object or a subset of a GeoRaster object to a file or to a BLOB object.

#### Parameters

georaster
GeoRaster object that will be exported.

subsetParam
String containing subset parameters, for exporting a subset of the GeoRaster object. The format and usage are as explained in [Storage Parameters](georaster-overview-and-concepts.md), although some keywords described in that section do not apply to this procedure. The following keywords are supported:

- `pLevel`: Pyramid level to be exported. The default is 0.

- `cropArea`: Specify the area to be exported in the format `cropArea = (startRow, startCol, endRow, endCol)`. It identifies the upper-left (`startRow`, `startCol`) and lower-right (`endRow`, `endCol`) coordinates of a rectangular window to be exported, and raster space is assumed. If `cropArea` is not specified, the entire image is exported.

- `layerNumber`: Layer numbers of the layers to be exported. For example, `layerNumber=(3-5)` exports layers 3, 4, and 5; and `layerNumber=(1,3,5)` exports layers 1, 3, and 5.

r_destFormat
Raster destination format. Must be one of the following: `TIFF`, `BMP`, or `PNG`. (`JPEG` and `GIF` are not supported for this procedure.)

r_destType
Type of destination for the export operation. Must be `FILE`.

r_destName
Destination file name (with full path specification) if `destType` is `FILE`. Do not specify the file extension. If you are using this procedure only to export the world file, specify a null value for this parameter.

r_destBLOB
BLOB object to hold the image file resulting from the export operation.

h_destFormat
Geoheader destination format. Must be `WORLDFILE`.

h_destType
Geoheader type of destination for the export operation. Must be `FILE`.

h_destName
Geoheader destination file name (with full path specification) if `h_destType` is `FILE`. Do not specify the file extension.

h_destCLOB
CLOB object to hold the geoheader file resulting from the export operation.

#### Usage Notes

**Note:**

This SDO_GEOR.exportTo procedure is not supported in Oracle Autonomous Database both in Serverless and Dedicated deployments.

Use a format with both r_xxx and h_xxx parameters only if the raster image and geoheader are in separate files.

This procedure does not support JPEG or GIF as a destination file format.

This procedure does not support GeoRaster objects that have a `cellDepth` value of `2BIT`.

GeoRaster objects with a cell depth of 8 bits or greater that have a BSQ or BIL interleaving are exported in BIP interleaved format.

Before you call this procedure, you must have write permission on the output file or the directory to contain the files. The following example (run as user `SYSTEM`) grants write permission on a specified file to user `HERMAN`:

    call dbms_java.grant_permission('HERMAN','SYS:java.io.FilePermission',
       '/mydirectory/myimages/img1.tif', 'write' );

The maximum amount of GeoRaster data that can be exported in a single operation is 67 megabytes (MB). Thus, the maximum dimensions of a GeoRaster object that can be exported at one time must be such that `width*height*bands*cellDepth/8 <= 67 MB` and `rowBlockSize*columnBlockSize*bands*cellDepth/8 <= 67 MB`. For example, for a 3-band, 8-bit GeoRaster object in which the width and height are equal:

- The largest exportable width and height are 4728x4728.

- The largest exportable block dimensions are 4096x4096.

#### Examples

The following example shows two export operations. The first operation exports an entire GeoRaster object (except for any georeferencing information) into a BMP format file. The second operation exports a subset of the GeoRaster object to a file with an ESRI world file.

    DECLARE
      geor SDO_GEORASTER;
      fileName VARCHAR2(1024);
      tfwName VARCHAR2(1024);

    BEGIN

    SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;

    -- Export the whole GeoRaster object into a BMP file, excluding any
    -- georeferencing information.
    sdo_geor.exportTo(geor, NULL, 'BMP', 'file',
      '/mydirectory/myimages/img1_export');

    -- Export a subset to a file with a world file.
    fileName := '/mydir/parrotExported';
    tfwName := '/mydir/parrotWorldFile';
    SELECT georaster INTO geor FROM georaster_table WHERE georid = 8;
    sdo_geor.exportTo(geor, 'cropArea=(0,0,500,500)',
      'TIFF', 'file', fileName, 'WORLDFILE', 'FILE', tfwName);

    END;
    /

The following example exports GeoRaster objects into BLOB and CLOB objects.

    CREATE TABLE blob_table (blob_col BLOB, blobid NUMBER unique, clob_col CLOB);
    INSERT INTO blob_table values (empty_blob(), 3, null);
    INSERT INTO blob_table VALUES (empty_blob(), 4, empty_clob());

    DECLARE
      lobd1 BLOB;
      lobd2 BLOB;
      lobd3 CLOB;
      geor1 SDO_GEORASTER;
      geor2 SDO_GEORASTER;

    BEGIN

    -- Example 1: Export to BLOB.
    SELECT blob_col INTO lobd1 FROM blob_table WHERE blobid=3 for update;
    SELECT georaster INTO geor1 FROM georaster_table WHERE georid = 13;
    sdo_geor.exportTo(geor1, '', 'TIFF', lobd1);
    UPDATE blob_table set blob_col = lobd1 WHERE blobid=3;
    COMMIT;

    -- Example 2: Export GeoRaster to BLOB with world file exported to CLOB.
    SELECT blob_col INTO lobd2 FROM blob_table WHERE blobid=4 for update;
    SELECT clob_col INTO lobd3 FROM blob_table WHERE blobid=4 for update;
    SELECT georaster INTO geor2 FROM georaster_table WHERE georid = 8;
    sdo_geor.exportTo(geor2, 'cropArea=(0,0,500,500)', 'TIFF', lobd2,
      'WORLDFILE', lobd3);
    UPDATE blob_table set blob_col = lobd2, clob_col = lobd3 WHERE blobid = 4;
    COMMIT;

    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.19 SDO_GEOR.generateAreaWeightedMean

#### Format

    SDO_GEOR.generateAreaWeightedMean(
         georaster   IN SDO_GEORASTER,
         window      IN SDO_GEOMETRY,
         bandNumber  IN NUMBER,
         nodata      IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

#### Description

Computes the area weighted statistical mean value on a specified band of the input GeoRaster object.

#### Parameters

georaster
GeoRaster object.

window
A polygon geometry object from which to generate statistics. If it is in the model space, it is transformed into raster space. See also the Usage Notes for the SDO_GEOR.generateStatisticsfunction for SDO_SRID requirements.

bandNumber
Band ordinate number of the layer for which to perform the operation.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

#### Usage Notes

This function computes area weighted statistical mean value for the cells within a specific window of the input GeoRaster object. It uses the area of the cell as the weight for each cell value when computing the statistical mean value, so that all subcells cut by the window boundary are processed appropriately.

#### Examples

The following example computes area weighted statistical mean value for the first band of the input GeoRaster object.

    SELECT sdo_geor.generateAreaWeightedMean(tmimage,sdo_geometry(2003,
              null,NULL,
              MDSYS.SDO_ELEM_INFO_ARRAY(1, 1003, 3),
              MDSYS.SDO_ORDINATE_ARRAY(9.5,9.5,12.5,12.5)),0)
         FROM landsat WHERE id=11;

**Parent topic:** SDO_GEOR Package Reference

### 7.20 SDO_GEOR.generateBitmapPyramid

#### Format

    SDO_GEOR.generateBitmapPyramid(
         src_geor      IN SDO_GEORASTER,
         tmp_geor      IN OUT SDO_GEORASTER,
         target_geor   IN OUT SDO_GEORASTER,
         pyramidParams IN VARCHAR2,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam IN VARCHAR2 DEFAULT NULL,    
         addColorMap   IN NUMBER DEFAULT 1);

#### Description

Generates pyramid data for a bitmap GeoRaster object.

#### Parameters

src_geor
Source GeoRaster object for which pyramid data is to be generated.

tmp_geor
Temporary GeoRaster object used to store temporary data

target_geor
Target GeoRaster object used to store the resulting GeoRaster data.

pyramidParams
A string containing the pyramid parameters. See the Usage Notes for information about the available keywords and values.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

addColorMap
A number to specify whether to add a colormap to the target GeoRaster object to display roads as white. 0 (zero) does not add such a colormap; 1 (the default) or any other nonzero value adds such a colormap.

#### Usage Notes

For bitmap raster of points, lines, or polylines, which are typically stored in 1-bit cell depth, the pyramiding approach described in [Image Pyramiding: Parallel Generation and Partial Update](image-processing-virtual-mosaic.md) may not create high-quality pyramids. Distorted point patterns and dashed lines are commonly seen in those pyramids. To solve such problems, you can instead use the GeoRaster raster algebra to perform bitmap pyramiding, as explained in [Bitmap Pyramiding](image-processing-virtual-mosaic.md).

`pyramidParams` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `rLevel` (for example, `rLevel=2`): Specifies the maximum reduction level: the number of pyramid levels to create at a smaller (reduced) size than the original object. If you do not specify this keyword, pyramid levels are generated until the smaller of the number of rows or columns is between 64 and 128. The dimension sizes at each lower resolution level are equal to the truncated integer values of the dimension sizes at the next higher resolution level, divided by 2.

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

  Note that for this procedure, `BILINEAR` and `AVERAGE4` have the same effect.

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the resampling method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

If you do not specify an `rLevel` value, the `rLevel` value is set to the default, which is calculated as follows:

    (int)(log2(a / 64))

In the preceding calculation:

- `log2` is a logarithmic function with 2 as its base.

- `a` is the smaller of the original row or column dimension size.

In the default case, the smaller of the row and column dimension sizes of the top-level overview (the smallest top-level pyramid) is between 64 and 128. If you specify an `rLevel` value greater than the maximum reduced-resolution level, the `rLevel` value is set to the maximum reduced-resolution level, which is calculated as follows:

    (int)(log2(a))

In this case, the smaller of the row and column dimension sizes of the top-level overview is 1.

#### Examples

The following example generates a bitmap pyramid.

    DECLARE
      src_gr sdo_georaster;
      tmp_gr sdo_georaster;
      target_gr sdo_georaster;
    BEGIN

      SELECT georaster INTO src_gr
        FROM georaster_table WHERE georid = 6;
      SELECT georaster INTO tmp_gr
        FROM georaster_table WHERE georid = 7 FOR UPDATE;
      SELECT georaster INTO target_gr
        FROM georaster_table WHERE georid = 8 FOR UPDATE;

     -- Generate bitmap pyramids.
      sdo_geor.generateBitmapPyramid(src_gr,tmp_gr,target_gr 'rLevel=5, resampling=NN');

      -- Update the target GeoRaster object.
      UPDATE georaster_table SET georaster =target_gr WHERE georid = 8;

    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.21 SDO_GEOR.generateBlockMBR

#### Format

    SDO_GEOR.generateBlockMBR(
         georaster  IN SDO_GEORASTER);

#### Description

Computes the minimum bounding rectangle (MBR) for each block in a GeoRaster object, and sets the `blockMBR` attribute for each raster block in the raster data table.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This procedure does not change the GeoRaster object. It sets the value of the `blockMBR` attribute (described in [blockMBR Attribute](georaster-datatypes.md)) in each row of the raster data table associated with the GeoRaster object.

If you created the GeoRaster object as described in [Creating New GeoRaster Objects](georaster-database-creation-management.md), the `blockMBR` attribute values were automatically calculated and they should not need to be validated or generated. However, if the GeoRaster object was generated by a third party, you should validate the `blockMBR` attribute values using the SDO_GEOR.validateBlockMBR function; and if any are not valid, call the SDO_GEOR.generateBlockMBR procedure.

#### Examples

The following example computes the MBR for a specified GeoRaster object and sets its `blockMBR` attribute.

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=1 FOR UPDATE;
      sdo_geor.generateBlockMBR(gr);
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.22 SDO_GEOR.generatePyramid

#### Format

    SDO_GEOR.generatePyramid(
         georaster     IN OUT SDO_GEORASTER,
         pyramidParams IN VARCHAR2,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam IN VARCHAR2 DEFAULT NULL);

#### Description

Generates pyramid data, which is stored together with the original data.

#### Parameters

georaster
GeoRaster object for which pyramid data is to be generated and stored.

pyramidParams
A string containing the pyramid parameters. See the Usage Notes for information about the available keywords and values.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

For information about pyramid data, see [Pyramids](georaster-overview-and-concepts.md).

`pyramidParams` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `rLevel` (for example, `rLevel=2`): Specifies the maximum reduction level: the number of pyramid levels to create at a smaller (reduced) size than the original object. If you do not specify this keyword, pyramid levels are generated until the smaller of the number of rows or columns is between 64 and 128. The dimension sizes at each lower resolution level are equal to the truncated integer values of the dimension sizes at the next higher resolution level, divided by 2.

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

  Note that for this procedure, `BILINEAR` and `AVERAGE4` have the same effect.

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the resampling method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

If `georaster` is null or is a blank GeoRaster object, or if pyramid data exists for `georaster` but it was created with the same pyramid parameters specified in `pyramidParams`, this procedure performs no operation.

If pyramid data exists for `georaster` and it was created using a different `resampling` value from that specified in `pyramidParams`, the old pyramid data is deleted and new pyramid data is generated. However, a different `nodata` specification in `pyramidParams` does not cause the pyramid data to be regenerated. To cause a new `nodata` value to take effect, you must delete the old pyramid data and then regenerate it.

If you do not specify an `rLevel` value, the `rLevel` value is set to the default, which is calculated as follows:

    (int)(log2(a / 64))

In the preceding calculation:

- `log2` is a logarithmic function with 2 as its base.

- `a` is the smaller of the original row or column dimension size.

In the default case, the smaller of the row and column dimension sizes of the top-level overview (the smallest top-level pyramid) is between 64 and 128. If you specify an `rLevel` value greater than the maximum reduced-resolution level, the `rLevel` value is set to the maximum reduced-resolution level, which is calculated as follows:

    (int)(log2(a))

In this case, the smaller of the row and column dimension sizes of the top-level overview is 1.

An exception is raised if `georaster` is invalid.

#### Examples

The following example creates pyramid data for a GeoRaster object.

    DECLARE
      gr sdo_georaster;
    BEGIN

      SELECT georaster INTO gr
        FROM georaster_table WHERE georid = 6 FOR UPDATE;

      -- Generate pyramids.
      sdo_geor.generatePyramid(gr, 'rLevel=5, resampling=NN');

      -- Update the original GeoRaster object.
      UPDATE georaster_table SET georaster = gr WHERE georid = 6;

      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.23 SDO_GEOR.generateSpatialExtent

#### Format

    SDO_GEOR.generateSpatialExtent(
         georaster  IN SDO_GEORASTER,
         height     IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEOMETRY;

#### Description

Generates a spatial geometry that contains the spatial extent (footprint) of the GeoRaster object.

#### Parameters

georaster
GeoRaster object.

height
Number specifying the Z value for three-dimensional (X, Y, Z) georeferencing.

#### Usage Notes

The returned SDO_GEOMETRY object is based on the model coordinate system of the GeoRaster object. If the GeoRaster object is not georeferenced, the SDO_GEOMETRY object has a null SDO_SRID value, which means the footprint geometry is in cell space; otherwise, the SDO_SRID value of the SDO_GEOMETRY object is the model SRID. Specifically:

- If the GeoRaster object is not georeferenced or if the model coordinate system is projected, the spatial extent object is a single polygon derived from eight boundary points.

- If the model coordinate system is geodetic, the spatial extent is densified according to the object's spatial footprint. If the area of the footprint is not larger than half of the Earth's surface, the result is a single geodetic polygon. Otherwise, a geodetic MBR is returned as the generated spatial extent object, and this returned object will be an invalid geometry according to Oracle Spatial and Graph validation rules, but index and query operations will work on this returned object.

The footprint is automatically adjusted, based on the GeoRaster object's model coordinate location (`CENTER` or `UPPERLEFT`), to cover the whole area in the model space. `CENTER` is the default model coordinate location for non-georeferenced cases.

If the model coordinate system is three-dimensional, the generated spatial extent is a three-dimensional geometry. To build a spatial index based on the generated value, you may need to convert it into a two-dimensional geometry before saving it in the `spatialExtent` attribute of the GeoRaster object. For more information about cross-dimensionality transformations, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

This function does not set the spatial extent of the GeoRaster object (`spatialExtent` attribute, described in [spatialExtent Attribute](georaster-datatypes.md)). For information about setting the spatial extent, see [Generating and Setting Spatial Extents](georaster-database-creation-management.md).

If `georaster` is null, this function returns a null SDO_GEOMETRY object. If `georaster` is not valid, an exception is raised.

#### Examples

The following example generates a three-dimensional spatial extent, with a Z or height dimension value of 10, in the geographic 3D coordinate system 4327 (the model SRID). (The output is slightly reformatted.)

    SELECT SDO_GEOR.generateSpatialExtent(georaster,10) spatialExtent
      FROM georaster_table where georid=10;

    SPATIALEXTENT(A.GEORASTER,10)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_IN
    ----------------------------------------------------------------------------------
    SDO_GEOMETRY(3003, 4327, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARRAY(.181818182, 1.1627907, 10, 12.1228111, 1.07010227, 10, 19.3902574, 1.07010229, 10, 25.1482989, 1.07010229, 10, 30.0714774, 1.07010229,
    10, 34.4500035, 1.07010229, 10, 38.3920079, 1.07010229, 10, 42.0490801,
    1.07010229, 10, 45.4612165, 1.07010229, 10, 48.6719786, 1.07010229, 10,
    53.6193472, 1.07010229, 10, 53.6193472, 12.346373, 10, 53.6178888, 15.3903048,
    10, 53.6178888, 18.3032341, 10, 50.6322061, 18.3032341, 10, 47.5331761,
    18.3032341, 10, 44.2541078, 18.3032341, 10, 40.7594212, 18.3032341, 10, 37,
    18.3032341, 10, 32.9046537, 18.3032341, 10, 28.3630834, 18.3032341, 10,
    23.1869539, 18.3032341, 10, 17, 18.3032341, 10, -2.220E-16, 18.3032341, 10, 0,
    16.3247208, 10, -2.220E-16, 13.6133114, 10, .181818182, 1.1627907, 10))

The following examples return the spatial extent geometry of GeoRaster objects in the GEORASTER column of the GEORASTER_TABLE table. (They refer to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.generateSpatialExtent(georaster) spatialExtent
      FROM georaster_table WHERE georid=2;

    SPATIALEXTENT(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINA
    --------------------------------------------------------------------------------

    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(0, 0, 256, 0, 511, 0, 511, 256, 511, 511, 256, 511, 0, 511, 0, 256, 0, 0))

    SET NUMWIDTH 20
    SELECT sdo_geor.generateSpatialExtent(georaster) spatialExtent
      FROM georaster_table WHERE georid=4;

    SPATIALEXTENT(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO,
    SDO_ORDINA
    --------------------------------------------------------------------------------

    SDO_GEOMETRY(2003, 82263, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_AR
    RAY(1828466.0909315, 646447.1932945, 1828466.0909315, 644479.85524, 1828466.0909
    315, 642512.5171855, 1830433.428986, 642512.5171855, 1832400.7670405, 642512.517
    1855, 1832400.7670405, 644479.85524, 1832400.7670405, 646447.1932945, 1830433.42
    8986, 646447.1932945, 1828466.0909315, 646447.1932945))

**Parent topic:** SDO_GEOR Package Reference

### 7.24 SDO_GEOR.generateSpatialResolutions

#### Format (Procedure)

    SDO_GEOR.generateSpatialResolutions(
        georaster      IN OUT SDO_GEORASTER,
        outResolution  OUT SDO_NUMBER_ARRAY);

#### Format (Function)

    SDO_GEOR.generateSpatialResolutions(
        georaster      IN SDO_GEORASTER,
        pyramidLevel   IN NUMBER DEFAULT NULL,
        SRID           IN NUMBER DEFAULT NULL,
        resolutionUnit IN VARCHAR2 DEFAULT NULL,
        ) RETURN SDO_NUMBER_ARRAY;

#### Description

Generates the spatial resolution value along each spatial dimension of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

outResolution
Generated spatial resolutions of the GeoRaster object. It is an array of two numbers that represent spatial resolutions on the X axis and Y axis, respectively.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

SRID
Coordinate system. Must be a value from the SRID column of the MDSYS.CS_SRS table. The srid value cannot be 0 (zero). If not specified, the default is the SRID associated with `georaster`.

resolutionUnit
Unit of measurement: a quoted string with `unit=`. If not specified, the unit associated with `SRID` is used.

#### Usage Notes

SDO_GEOR.generateSpatialResolutions has two formats:

- The procedure format sets the generated spatial resolutions in the metadata for the GeoRaster object. The metadata for the GeoRaster object is updated. The GeoRaster object must be georeferenced in order to get the spatial resolution generated.

- The function format generates and returns the spatial resolutions based on the georeferencing information in the metadata for the GeoRaster object. The metadata for the GeoRaster object is not updated.

The GeoRaster object must be georeferenced. The generated spatial resolution is the resolution at the center cell of the GeoRaster object.

In the returned array of numeric values, each value indicates the number of units of measurement associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measurement for the ground data is meters, each pixel represents an area of 10 meters by 10 meters.

The GeoRaster object is automatically validated after the operation completes.

See also the Usage Notes for the SDO_GEOR.getSpatialResolutions function.

#### Examples

The following example generates the spatial resolution value along each spatial dimension for pyramid level 2 of a specified GeoRaster object

    SELECT sdo_geor.generateSpatialResolutions(georaster, 2, 4326, null) FROM georaster_table WHERE georid=2;

    SDO_GEOR.GENERATESPATIALRESOLUTIONS(GEORASTER,2,4326,NULL)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(.000024266, .000018006)

**Parent topic:** SDO_GEOR Package Reference

### 7.25 SDO_GEOR.generateStatistics

#### Format (Storage in Metadata)

    SDO_GEOR.generateStatistics(
         georaster      IN OUT SDO_GEORASTER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         histogram      IN VARCHAR2,
         layerNumbers   IN VARCHAR2 DEFAULT NULL,
         useBin         IN VARCHAR2 DEFAULT 'TRUE',
         binFunction    IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN VARCHAR2;

or

    SDO_GEOR.generateStatistics(
         georaster      IN OUT SDO_GEORASTER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         histogram      IN VARCHAR2,
         layerNumbers   IN VARCHAR2 DEFAULT NULL,
         useBin         IN VARCHAR2 DEFAULT 'TRUE',
         binFunction    IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN VARCHAR2;

#### Format (No Storage in Metadata)

    SDO_GEOR.generateStatistics(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatistics(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers, or with one or more layers and pyramid levels. The two sets of function formats have significant usage differences:

- Storage in Metadata formats also set statistical data in the GeoRaster object metadata for each specified layer, and optionally for the whole raster. These formats return the string `TRUE` or `FALSE`, indicating success or failure of the operation.

- No Storage in Metadata formats do not set any GeoRaster object metadata, and they calculate statistics for a single layer or for the aggregation of specified layers. These formats return an SDO_NUMBER_ARRAY object where the six numbers reflect the aggregated minimum, maximum, mean, median, mode, and standard deviation values.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level on which to perform the operation.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

histogram
Specify `TRUE` to cause a histogram to be computed and stored, or `FALSE` to cause a histogram not to be computed and stored. Histograms are discussed in [SDO_GEOR_HISTOGRAM Object Type](georaster-datatypes.md). The XML definitions of the `<histogram>` element and the `histogramType` complex type are included in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md).

layerNumbers
Numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 1, 3, 4, 5, and 7. Layer 0 (zero) indicates the object layer.

bandNumbers
Band ordinate numbers of the layers for which values are used in computing the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'0,1,3-5,7'` specifies layers 1, 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

useBin
Specifies whether or not to use a provided bin function (specified in the `binFunction` parameter) when generating statistics. `TRUE` (the default) causes a bin function to be used as follows: (1) the bin function specified by the `binFunction` parameter, if it is not null; otherwise, (2) the bin function specified by the `<binFunction>` element in the GeoRaster XML metadata, if one is specified; otherwise, (3) a dynamically generated bin function, as explained in the Usage Notes. `FALSE` causes a dynamically generated bin function to be used, and causes the `binFunction` parameter and `<binFunction>` element to be ignored.

For information about bin functions, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

binFunction
Bin function as an array whose elements specify the bin type, total number of bins, first bin number, minimum cell value, and maximum cell value. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`. For more information about the bin function for SQO_GEOR.generateStatistics, see the Usage Notes. For information about bin functions and an example, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes and can set the statistical data described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md).

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

If `histogram` is `TRUE`, this function determines the range of each bin based on the bin function being used, and within each range it computes the count of each pixel value. The histogram and the bin function are related as follows: each bin is mapped to a (value, count) pair of the histogram, and the lower boundary of each bin is mapped to corresponding value of histogram (value, count) pair, with the following exceptions:

- If Min_r \< Min, then one more pair (Min_r, count) is added as the first pair of the histogram. (Min_r is the real minimum value of the data set computed by this function, and Min is the `min` value specified in the bin function.)

- If Max_r \> Max, then one more pair (Max_r, count) is added as the last pair of the histogram. (Max_r is the real maximum value of the data set computed by this function, and Max is the `max` value specified in the bin function.)

- Leading and trailing count=0 pairs in the histogram are suppressed. For example:

      (1,0) (2,0) (3,11) (4,12) becomes (3,11) (4,12)
      (1,11) (2,12) (3,0) (4,0) becomes (1,11) (2,12)

If `histogram` is `TRUE`, any existing histogram in the XML metadata is replaced by the new generated histogram.

SQO_GEOR.generateStatistics supports only LINEAR bin functions (`binType` = 0), not LOGARITHM or EXPLICIT bin functions. (The XML definitions of all bin function types are in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md).) If the `useBin` parameter value is FALSE, this function ignores any `binFunction` parameter value and any `<binFunction>` element in the GeoRaster XML metadata, and it uses a LINEAR bin function in which the `min` and `max` values are the actual minimum and maximum values of the data set, and the `numbins` value depends on the cell depth, as follows:

- If `cellDepth` = 1, `numbins` = 2.

- If `cellDepth` = 2, `numbins` = 4.

- If `cellDepth` = 4, `numbins` = 8.

- If `cellDepth` \>= 8, `numbins` = 256.

If the `useBin` parameter value is TRUE, this function uses a bin function as follows:

1.  If the `binFunction` parameter specifies a valid bin function, it is used.

2.  Otherwise, if a valid bin function is defined in the GeoRaster metadata, it is used.

3.  Otherwise, the same bin function is used as when the `useBin` parameter value is FALSE.

Contrast this function, which causes GeoRaster to compute and optionally set the statistics, with the SDO_GEOR.setStatistics procedure, in which you specify the statistics to be set.

To retrieve the statistical data associated with a layer, use the SDO_GEOR.getStatistics function.

#### Examples

The following example generates the statistical data and a histogram.

    DECLARE
      gr SDO_GEORASTER;
      ret VARCHAR2(256);
      window SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY(20,10,50,50);
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=1 FOR UPDATE;
      SDO_GEOR.setBinFunction(gr,1,sdo_number_array(0,10,1,50,200));
      ret := SDO_GEOR.generateStatistics(gr, 'samplingFactor=5', window, 'TRUE',
        '1-1', 'TRUE');
      UPDATE georaster_table SET georaster=gr WHERE georid=1;
      COMMIT;
    END;
    /

The following example generates the statistical data for all bands on pyramid level 1; however, it does not create a histogram or modify the GeoRaster object metadata.

    DECLARE
      gr sdo_georaster;
      window  sdo_geometry;
      stat   sdo_number_array;
    BEGIN
      SELECT tmimage INTO gr FROM landsat WHERE id=2021;
      stat:=sdo_geor.generateStatistics(gr,1,'samplingFactor=7',window,null,'false');
      dbms_output.put_line('min='||stat(1));
      dbms_output.put_line('max='||stat(2));
      dbms_output.put_line('mean='||stat(3));
      dbms_output.put_line('median='||stat(4));
      dbms_output.put_line('mode='||stat(5));
      dbms_output.put_line('std='||stat(6));
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.26 SDO_GEOR.generateStatisticsMax

#### Format

    SDO_GEOR.generateStatisticsMax(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMax(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMax(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsMax(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the maximum value. (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `MAX` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the maximum value.

    DECLARE
     gr sdo_georaster;
     window sdo_geometry;
     max number;
    BEGIN
     SELECT tmimage INTO gr FROM landsat WHERE id=2021;
     max:=sdo_geor.generateStatisticsMax(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.27 SDO_GEOR.generateStatisticsMean

#### Format

    SDO_GEOR.generateStatisticsMean(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMean(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMean(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsMean(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mean (average) value. (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `MEAN` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the mean value.

    DECLARE
      gr sdo_georaster;
      window sdo_geometry;
      mean number;
    BEGIN
      SELECT tmimage INTO gr FROM landsat WHERE id=2021;
      mean:=sdo_geor.generateStatisticsMean(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.28 SDO_GEOR.generateStatisticsMedian

#### Format

    SDO_GEOR.generateStatisticsMedian(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMedian(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMedian(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsMedian(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the median value. (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `MEDIAN` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the median value.

    DECLARE
      gr sdo_georaster;
      window sdo_geometry;
      median number;
    BEGIN
      SELECT tmimage INTO gr FROM landsat WHERE id=2021;
      median:=sdo_geor.generateStatisticsMedian(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.29 SDO_GEOR.generateStatisticsMin

#### Format

    SDO_GEOR.generateStatisticsMin(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMin(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMin(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsMin(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the minimum value. (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `MIN` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the minimum value.

    DECLARE
     gr sdo_georaster;
     window sdo_geometry;
     min number;
    BEGIN
     SELECT tmimage INTO gr FROM landsat WHERE id=2021;
     min:=sdo_geor.generateStatisticsMin(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.30 SDO_GEOR.generateStatisticsMode

#### Format

    SDO_GEOR.generateStatisticsMode(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMode(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsMode(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsMode(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the mode value (the value that occurs most frequently). (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `MODEVALUE` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the mode value.

    DECLARE
      gr sdo_georaster;
      window sdo_geometry;
      mode number;
    BEGIN
      SELECT tmimage INTO gr FROM landsat WHERE id=2021;
      mode:=sdo_geor.generateStatisticsMode(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.31 SDO_GEOR.generateStatisticsSTD

#### Format

    SDO_GEOR.generateStatisticsSTD(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE'
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsSTD(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_GEOR.generateStatisticsSTD(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.generateStatisticsSTD(
         georaster      IN OUT SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         samplingFactor IN VARCHAR2,
         samplingWindow IN SDO_GEOMETRY,
         bandNumbers    IN VARCHAR2 DEFAULT NULL,
         nodata         IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip    IN VARCHAR2 DEFAULT NULL',
         parallelParam  IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes statistical data associated with one or more layers on a specified pyramid level, and returns the standard deviation value. (It does not modify metadata in the GeoRaster object.)

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the returned resolution values. The default is pyramid level 0.

samplingFactor
Sampling factor in the format `'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed.

samplingWindow
A sampling window for which to generate statistics, specified either as a numeric array or as an SDO_GEOMETRY object. If the data type is SDO_NUMBER_ARRAY (defined as `VARRAY(1048576) OF NUMBER`), the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, it is transformed into raster space if it is in model space, and then the minimum bounding rectangle (MBR) of the geometry object in raster space is used as the window. The default value is the entire image.

In both cases, the intersection of the MBR of the sampling window in raster space and the MBR of the GeoRaster object in raster space is used for computing statistics. However, if `polygonClip` is `TRUE`, then the `samplingWindow` geometry object will be used for the operation instead of the MBR of the sampling window, in which case only cells within the `samplingWindow` geometry are counted.

If the data type is SDO_GEOMETRY, see also the Usage Notes for the SDO_GEOR.generateStatistics function for SDO_SRID requirements.

bandNumbers
Band ordinate numbers of the layers for which to compute the statistics. This is a string that can include numbers, number ranges indicated by hyphens (-), and commas to separate numbers and number ranges. For example, `'1,3-5,7'` specifies layers 2, 4, 5, 6, and 8. If `bandNumbers` is null, all bands are used in computing the statistics.

nodata
Specifies whether or not to compare each cell values with NODATA values defined in the metadata when computing statistics. `TRUE` causes all pixels with a NODATA value not to be considered; `FALSE` (the default) causes pixels with NODATA values to be considered as regular pixels. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
The string `TRUE` causes the `samplingWindow` geometry object to be used for the operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `samplingWindow` geometry object to be used for the operation.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, you cannot roll back the results of this function.

#### Usage Notes

This function computes statistical data and returns the `STD` value. (The statistical data is described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md); however, this function does not update any metadata.)

If `samplingWindow` is outside the GeoRaster object or if it contains only NODATA values, the following error is raised:

    ORA-13393: null or invalid samplingWindow parameter

See also the SDO_GEOR.generateStatistics function.

#### Examples

The following example computes statistical data for all bands on pyramid level 1, and returns the standard deviation value.

    DECLARE
     gr sdo_georaster;
     window sdo_geometry;
     std number;
    BEGIN
     SELECT tmimage INTO gr FROM landsat WHERE id=2021;
     std:=sdo_geor.generateStatisticsSTD(gr,1,'samplingFactor=7',window,null,'false');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.32 SDO_GEOR.georeference

#### Format (procedure)

    SDO_GEOR.georeference(
         georaster                IN OUT SDO_GEORASTER,
         srid                     IN NUMBER,
         modelCoordinateLocation  IN NUMBER,
         xCoefficients            IN SDO_NUMBER_ARRAY,
         yCoefficients            IN SDO_NUMBER_ARRAY);

#### Format (function)

    SDO_GEOR.georeference(
         georaster               IN OUT SDO_GEORASTER,
         FFMethodType            IN VARCHAR2,
         nGCP                    IN NUMBER,
         GCPs                    IN SDO_GEOR_GCP_COLLECTION,
         storeGCP                IN VARCHAR2 DEFAULT 'TRUE',
         srid                    IN NUMBER DEFAULT NULL,
         modelCoordinateLocation IN NUMBER DEFAULT NULL,
         setResolution           IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.georeference(
         georaster               IN OUT SDO_GEORASTER,
         gcpGeorefModel          IN SDO_GEOR_GCPGEOREFTYPE,
         storeGCP                IN VARCHAR2 DEFAULT 'TRUE',
         srid                    IN NUMBER DEFAULT NULL,
         modelCoordinateLocation IN NUMBER DEFAULT NULL,    
         setResolution           IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.georeference(
         georaster               IN OUT SDO_GEORASTER,
         FFMethodType            IN VARCHAR2 DEFAULT NULL,
         srid                    IN NUMBER DEFAULT NULL,
         modelCoordinateLocation IN NUMBER DEFAULT NULL,
         setResolution           IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

As a procedure, georeferences a GeoRaster object using specified cell-to-model transformation coefficients of an affine transformation. As a function, returns the solution of any one of the supported geometric models using ground control points (GCPs) that are either stored in the database or specified in parameters.

#### Parameters

georaster
The SDO_GEORASTER object to be georeferenced.

srid
Model coordinate system. For the procedure, must not be null or 0 (zero); for function, it can be null. It can be a value from the SRID column of the MDSYS.CS_SRS table. If it is not a value from the SRID column of the MDSYS.CS_SRS table, the SRID is not supported by Oracle Spatial and Graph, and some SRID-related operations may not be supported.

modelCoordinateLocation
A value specifying the model location of the base of the area represented by a cell: `0` for `CENTER` or `1` for `UPPERLEFT`.

xCoefficients
An array specifying the A, B, and C coefficient values in the calculation, as explained in the Usage Notes.

yCoefficients
An array specifying the D, E, and F coefficient values in the calculation, as explained in the Usage Notes.

FFMethodType
Polynomial or rational polynomial function used as georeference geometric model. Must be one of the following string values: `Affine`, `QuadraticPolynomial`, `CubicPolynomial`, `DLT`, `QuadraticRational`, or `RPC`.

gcpGeorefModel
Object containing the following: `FFMethodType`, `nGCP`, `GCPs`, `solutionAccuracy`.

nGCP
Number of ground control points in the GCP collection (`GCPs` parameter).

GCPs
The GCP collection, of type SDO_GEOR_GCP_COLLECTION (described in [SDO_GEOR_GCP\_ COLLECTION Collection Type](georaster-datatypes.md)).

storeGCP
A flag indicating whether the GCPs should be stored in the GeoRaster metadata. The string `TRUE` (the default) stores the points in the GeoRaster metadata; the string `FALSE` does not store the points in the GeoRaster metadata.

setResolution
A flag indicating whether the spatial resolution is calculated and stored in the GeoRaster metadata. The string `FALSE` or a null value does not store the spatial resolution in the GeoRaster metadata; the string `TRUE` stores the spatial resolution in the GeoRaster metadata.

#### Usage Notes

Notes for the Procedure Format

Use this procedure to georeference a GeoRaster object based on an existing affine transformation. Georeferencing is explained in [Georeferencing](georaster-overview-and-concepts.md) and [Georeferencing GeoRaster Objects](georaster-database-creation-management.md).

This procedure assumes that in the original georeferencing information in the source data, such as in an ESRI world file, the transformation formulas are the following:

    x = A * column + B * row + C
    y = D * column + E * row + F

Specify the preceding A, B, C, D, E, and F coefficients to the SDO_GEOR.georeference procedure. They are automatically adjusted internally to produce the correct georeferencing result: a, b, c, d, e, and f coefficients, as in the following formulas:

    row    = a + b * x + c * y
    column = d + e * x + f * y

In these formulas:

- row = Row index of the cell in raster space.

- column = Column index of the cell in raster space.

- x = East-West position of the point on the ground or in model space.

- y = North-South position of the point on the ground or in model space.

- a, b, c, d, e, and f are coefficients, and they are stored in the GeoRaster SRS metadata.

- b\*f – c\*e should not be equal to 0 (zero).

In these formulas, if b = 0, f = 0, c = -e, and both c and e are not 0 (zero), the raster data is called rectified, and the formula becomes:

    row    = a + c * y
    column = d - c * x

This procedure sets the spatial resolutions of the GeoRaster object.

The following also perform operations related to georeferencing:

- The SDO_GEOR.setSRS procedure sets or deletes georeferencing information.

- The SDO_GEOR.importFrom procedure can load an ESRI world file or a Digital Globe RPC file from a file or from a CLOB object.

- The GeoRaster loader tool (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)) can load an ESRI world file, a Digital Globe RPC file, or the geometadata from a GeoTIFF file.

Notes for the Function Formats (for Use with GCPs)

This function calculates the solution of the specified geometric model (the `FFMethodType`) using the GCPs that are either stored in the database or specified in parameters, and it stores the solution in the GeoRaster functional fitting model.

The returned array contains RMS values and residuals, which have the following order: the solution accuracy (rowRMS, colRMS, totalRMS) computed using control points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using check points, the ground positioning accuracy (xRMS, yRMS, zRMS, modelTotalRMS) computed using control points, and the (xResidual, yResidual) for each control point (not for check points). The ordering of the residuals is the same as the control points stored in the XML metadata (not necessarily in the sequential order of the control point ID values if the ID values are numbers).

There are always at least 17 values returned (assuming at least 3 control points). A positioning accuracy (RMS) value of –1.0 means that value does not exist. For a two-dimensional geometric model, the zRMS value is always –1.0; otherwise, zRMS values are always 0 in the current release.

The GCPs can either be retrieved from the GeoRaster metadata or provided using the GCP-related object types.

For the interface without GCP information (that is, the format without the `gcpGeorefModel` parameter), the GCPs are assumed to be stored in the GeoRaster object's metadata. If no GCPs are stored or if not enough GCPs are stored for the specified model, an exception is raised.

After this function call, the GeoRaster object is georeferenced and the coefficients of the functional fitting model are set in the GeoRaster SRS metadata component.

For more information about georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

#### Examples

The following example georeferences a GeoRaster object directly using the cell-to-model coefficients of an affine transformation. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid = 1 FOR UPDATE;
      sdo_geor.georeference(gr, 82394, 0,
                            sdo_number_array(28.5, 0, 1232804.04),
                            sdo_number_array(0, -28.5, 13678.09));
      UPDATE georaster_table SET georaster = gr WHERE georid = 1;
      COMMIT;
    END;
    /

    PL/SQL procedure successfully completed.

    SET NUMWIDTH 20
    SELECT georid, sdo_geor.getSRS(georaster) SRS FROM georaster_table
      WHERE georid = 1;

                  GEORID
    --------------------
    SRS(ISREFERENCED, ISRECTIFIED, ISORTHORECTIFIED, SRID,
    SPATIALRESOLUTION, SPATIA
    --------------------------------------------------------------------------------

                       1
    SDO_GEOR_SRS('TRUE', 'TRUE', NULL, 82394, SDO_NUMBER_ARRAY(28.5, 28.5), NULL, NU
    LL, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, NULL, NULL, NULL, SDO_NUMBER_ARRAY(1, 2, 1, 3,
     479.93298245614, 0, -.0350877192982456), SDO_NUMBER_ARRAY(1, 0, 0, 1, 1), SDO_N
    UMBER_ARRAY(1, 2, 1, 3, -43256.2821052632, .0350877192982456, 0), SDO_NUMBER_ARR
    AY(1, 0, 0, 1, 1))

If the original raster data is rectified and if the model coordinate of the center point of the upper-left corner cell is (x0, y0) and its spatial resolution is s, you can directly use the preceding example code to georeference the GeoRaster object by replacing 28.5 with s, 1232804.04 with x0, and 13678.09 with y0. If you have other information about the GeoRaster object, such as a well-defined precise envelope of the raster or the model coordinates of the center point, you can compute the (x0, y0) and the spatial resolution s, and then use the same approach to georeference the object.

The following example georeferences a GeoRaster object, using ground control point (GCP) information.

    DECLARE
       gr1                 sdo_georaster;
       gr2                  sdo_georaster;
       georefModel   SDO_GEOR_GCPGEOREFTYPE;
       GCPs              SDO_GEOR_GCP_COLLECTION;
       rms                  sdo_number_array;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=10 FOR UPDATE;

       GCPs := SDO_GEOR_GCP_COLLECTION(
                               SDO_GEOR_GCP('1', '', 1,
                                  2, sdo_number_array(25.625000, 73.875000),
                                  2, sdo_number_array(237036.937500, 897987.187500),
                                  NULL, NULL),
                                  SDO_GEOR_GCP('2', '', 1,
                                  2, sdo_number_array(100.625000, 459.125000),
                                  2, sdo_number_array(237229.562500, 897949.687500),
                                  NULL, NULL),
                                  SDO_GEOR_GCP('3', '', 1,
                                  2, sdo_number_array(362.375000, 77.875000),
                                  2, sdo_number_array(237038.937500, 897818.812500),
                                  NULL, NULL),
                                  SDO_GEOR_GCP('4', '', 1,
                                  2, sdo_number_array(478.875000, 402.125000),
                                  2, sdo_number_array(237201.062500, 897760.562500),
                                  NULL, NULL),
                                  SDO_GEOR_GCP('5', '', 2,
                                  2, sdo_number_array(167.470583,  64.030686),
                                  2, sdo_number_array(237032.015343, 897916.264708),
                                  NULL, NULL),
                                  SDO_GEOR_GCP('6', '', 2,
                                  2, sdo_number_array(101.456177,  257.915534),
                                  2, sdo_number_array(237128.957767, 897949.271912),
                                  NULL, NULL)
                           );

       georefModel := SDO_GEOR_GCPGEOREFTYPE('Affine',
    GCPs.count, GCPs, NULL);

       rms := sdo_geor.georeference(gr1, georefModel, 'FALSE', 26986, 1);
       UPDATE georaster_table SET georaster=gr1 WHERE georid=10;
       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.33 SDO_GEOR.getBandDimSize

#### Format

    SDO_GEOR.getBandDimSize(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of bands in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

For an explanation of bands, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md).

If `georaster` or its metadata is null, this function returns a null value.

#### Examples

The following example returns the spatial dimension sizes and the number of bands (one in this case) for a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT sdo_geor.getSpatialDimSizes(georaster) spatialDimSizes,
           sdo_geor.getBandDimSize(georaster) bandDimSize
      FROM georaster_table WHERE georid=21;

    SPATIALDIMSIZES                  BANDDIMSIZE
    --------------------------       -----------
    SDO_NUMBER_ARRAY(512, 512)           1

**Parent topic:** SDO_GEOR Package Reference

### 7.34 SDO_GEOR.getBeginDateTime

#### Format

    SDO_GEOR.getBeginDateTime(
         georaster  IN SDO_GEORASTER
         ) RETURN TIMESTAMP WITH TIME ZONE;

#### Description

Returns the beginning date and time for raster data collection in the metadata for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

To set the beginning date and time for raster data collection in the metadata for a GeoRaster object, use the SDO_GEOR.setBeginDateTime procedure.

If `georaster` or its metadata is null, this function returns a null value.

#### Examples

The following example returns the beginning and ending dates and times for raster data collection in the metadata for the GeoRaster object in a table named GEORASTER_TABLE where the GEORID column contains the value 4. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getBeginDateTime(georaster) beginDateTime,
      sdo_geor.getEndDateTime(georaster) endDateTime
      FROM georaster_table WHERE georid=4;

    BEGINDATETIME
    ---------------------------------------------------------------------------
    ENDDATETIME
    ---------------------------------------------------------------------------
    01-JAN-00 05.00.00.000000000 AM +00:00
    15-NOV-02 08.00.00.000000000 PM +00:00

**Parent topic:** SDO_GEOR Package Reference

### 7.35 SDO_GEOR.getBinFunction

#### Format

    SDO_GEOR.getBinFunction(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Gets the bin function associated with a layer.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the bin type. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the bin function as an array whose elements specify the bin type, total number of bins, first bin number, minimum cell value, and maximum cell value. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`.

If the bin type is `EXPLICIT`, an external bin table is used and this function returns a null value.

For a more detailed explanation of the bin function format, see the Usage Notes for the SDO_GEOR.setBinFunction procedure.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example gets the bin function for layer 3 of a specified GeoRaster object.

    SELECT sdo_geor.getBinFunction(georaster,3) FROM georaster_table WHERE georid=4;

    SDO_GEOR.GETBINFUNCTION(GEORASTER,3)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(0, 10, 1, 0, 511)

**Parent topic:** SDO_GEOR Package Reference

### 7.36 SDO_GEOR.getBinTable

#### Format

    SDO_GEOR.getBinTable(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the name of the bin table associated with a layer.

**Note:**

GeoRaster does not perform operations using the bin table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the bin table name. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function is relevant only if the bin type is `EXPLICIT`. To retrieve the bin type, use the SDO_GEOR.getBinType function.

To specify a bin table for a layer, use the SDO_GEOR.setBinTable procedure.

See also the information in the Usage Notes for the SDO_GEOR.getBinType function.

If `georaster` or its metadata is null, this function returns a null value.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example returns the name of the bin table for layer number 4 of a specified GeoRaster object in a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getBinTable(georaster, 4) FROM georaster_table WHERE georid=4;

**Parent topic:** SDO_GEOR Package Reference

### 7.37 SDO_GEOR.getBinType

#### Format

    SDO_GEOR.getBinType(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the bin type associated with a layer.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the bin type. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns one of the following bin type values: `LINEAR`, `LOGARITHM`, or `EXPLICIT`.

The `LINEAR` bin type is defined as follows:

    binNumber = numbins * (cellValue - min) / (max - min) + firstBinNumber
    if (binNumber less than 0) binNumber =  firstBinNumber
    if (binNumber greater than or equal to numbins) binNumber = numbins + firstBinNumber - 1

The `LOGARITHM` bin type is defined as follows:

    binNumber = numbins * (ln (1.0 + ((cellValue - min)/(max - min)))/ ln (2.0)) + firstBinNumber
    if (binNumber less than 0) binNumber =  firstBinNumber
    if (binNumber greater than or equal to numbins) binNumber = numbins + firstBinNumber - 1

The `EXPLICIT` bin type means that the value (or value range) for each bin is stored in a bin table (which you can set using the SDO_GEOR.setBinTable procedure and retrieve using the SDO_GEOR.getBinTable function).

A bin function maps values or value ranges of the GeoRaster cells to specific bin numbers, which are all integers. GeoRaster does not provide interfaces to manipulate and process bin functions.

If `georaster` or its metadata is null, this function returns a null value.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example returns the bin types for layers 0 and 1 of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT substr(sdo_geor.getBinType(georaster, 0),1,20) binType0,
           substr(sdo_geor.getBinType(georaster, 1),1,20) binType1
      FROM georaster_table WHERE georid=4;

    BINTYPE0        BINTYPE1
    --------------- ---------------
    EXPLICIT        LINEAR

**Parent topic:** SDO_GEOR Package Reference

### 7.38 SDO_GEOR.getBitmapMask

#### Format

    SDO_GEOR.getBitmapMask(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         storageParam IN VARCHAR2,
         mask         IN OUT SDO_GEORASTER);

#### Description

Gets the bitmap mask that is associated with a GeoRaster object or a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
The layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

mask
The resulting GeoRaster object to hold the bitmap mask. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as the input GeoRaster object (`georaster` parameter).

#### Usage Notes

If no bitmap mask is associated with the specified layer of the GeoRaster object, the resulting GeoRaster object is not updated.

If the `storageParam` parameter is null, the resulting GeoRaster object has a `celldepth` value of 1BIT celldepth, has `DEFLATE` compression if the input GeoRaster object is compressed, and has the same interleaving type and blocking size as the input GeoRaster object. It also contains all the bitmap mask pyramids if the input GeoRaster object has pyramids built on it.

A bitmap mask may have empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). If there is reblocking that leads to partially empty raster blocks, any cells in a partially empty block that are derived from an empty raster block are filled with the value 0 (zero).

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example retrieves the bitmap mask associated with the object layer of the specified GeoRaster object.

    DECLARE
      gr sdo_georaster;
      mk sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=4;
      INSERT INTO georaster_table (georid, georaster)
        VALUES (100, sdo_geor.init('rdt_1', 100))
        RETURNING georaster INTO mk;
      sdo_geor.getBitmapMask(gr, 0, 'compression=none', mk);
      UPDATE georaster_table SET georaster=mk WHERE georid=100;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.39 SDO_GEOR.getBitmapMaskSubset

#### Format

    SDO_GEOR.getBitmapMaskSubset(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         window       IN SDO_NUMBER_ARRAY,
         rasterBlob   IN OUT NOCOPY BLOB,
         storageParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getBitmapMaskSubset(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         inWindow     IN SDO_NUMBER_ARRAY,
         rasterBlob   IN OUT NOCOPY BLOB,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getBitmapMaskSubset(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         window       IN SDO_GEOMETRY,
         rasterBlob   IN OUT NOCOPY BLOB,
         storageParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getBitmapMaskSubset(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         inWindow     IN SDO_GEOMETRY,
         rasterBlob   IN OUT NOCOPY BLOB,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL);

#### Description

Gets a subset of a bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

pyramidLevel
Pyramid level containing the specified cell.

window, inWindow
A rectangular window for the subset, specified either as a numeric array with the lower-left and upper-right coordinates or as an SDO_GEOMETRY object. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`.

rasterBlob
BLOB to hold the output (the resulting subset).

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

storageParam
A string specifying storage parameters to be applied in creating `rasterBlob`. The only `storageParam` keywords supported for this procedure are `celldepth`, `compression`, `interleaving`, and `quality`; all other keywords are ignored. Storage parameters are explained in [Storage Parameters](georaster-overview-and-concepts.md).

If the `storageParam` parameter is null, the resulting GeoRaster object has a `celldepth` value of 1BIT celldepth, has `DEFLATE` compression if the input GeoRaster object is compressed, and has the same interleaving type as the input GeoRaster object.

#### Usage Notes

If there is no bitmap associated with the specified GeoRaster object at the specified raster layer, or the specified input window does not intersect with the spatial extent of the GeoRaster object, the procedure returns with `rasterBlob` truncated to length zero and the `outWindow` set to a null value.

This procedure operates on a single GeoRaster object. The procedure has four formats, depending on whether the input window is specified as a geometry object or as the upper-left and lower-right corners of a box, and on whether the `outWindow` parameter is used to return the coordinates of the output window.

If the `window` or `inWindow` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following: null (to specify raster space) or a value from the SRID column of the MDSYS.CS_SRS table.

If the SDO_SRID values for the `window` or `inWindow` parameter geometry and the model space are different, the geometry parameter is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `window` parameter specifies a geodetic MBR, it cannot cross the date line meridian. For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

After the procedure completes, the rasterBLOB parameter contains the cell (pixel) data in the cropped window without tiling. The cropped window is the overlapping portion of the specified window of interest and the source GeoRaster object's spatial extent. If the `outWindow` parameter is specified, after the procedure completes it contains the coordinates of the cropped window in the cell space.

A bitmap mask may have empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). Any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB.

The BLOB has no padding, except when the cell depth is less than 8 bits and the total number of bits needed for the output cannot be divided by 8; in these cases, unlike normal padding, only the last byte of the result is padded with 0 (zeros) for the trailing bits.

You can specify compression regardless of whether the input GeoRaster object is compressed or not. To have decompressed output for a compressed input GeoRaster object, specify `compression=NONE` in the `storageParam` parameter. For information about GeoRaster compression and decompression, see [Compression and Decompression](georaster-overview-and-concepts.md).

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example retrieves a subset of a bitmap mask associated with the object layer of a specified GeoRaster object.

    DECLARE
      gr sdo_georaster;
      lb blob;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=4;
      dbms_lob.createTemporary(lb, TRUE);
      sdo_geor.getBitmapMaskSubset(gr, 0, 0, sdo_number_array(0,0,99,99), lb, 'compression=none');
      dbms_lob.freeTemporary(lb);
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.40 SDO_GEOR.getBitmapMaskValue

#### Format

    SDO_GEOR.getBitmapMaskValue(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         rowNumber    IN NUMBER,
         colNumber    IN NUMBER
         ) RETURN NUMBER;

or

    SDO_GEOR.getBitmapMaskValue(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         ptGeom       IN SDO_GEOMETRY
         ) RETURN NUMBER;

#### Description

Gets the value of a single cell from a bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

pyramidLevel
Pyramid level containing the specified cell.

rowNumber
Row number in cell space.

colNumber
Column number in cell space.

ptGeom
Point geometry in cell space or model space.

#### Usage Notes

You can specify the cell by its row and column numbers or by a point geometry object.

If there is no bitmap associated with the specified GeoRaster object at the specified raster layer, or the specified cell is in an empty raster block, the function returns a null value.

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example gets the value of four cells from the bitmap mask associated with a specified GeoRaster object.

    SELECT sdo_geor.getBitmapMaskValue(georaster,0,0,0,0) c1,
           sdo_geor.getBitmapMaskValue(georaster,0,0,9,9) c2,
           sdo_geor.getBitmapMaskValue(georaster,0,0,9,10) c3,
           sdo_geor.getBitmapMaskValue(georaster,0,0,10,9) c4
      FROM georaster_table WHERE georid=0;

**Parent topic:** SDO_GEOR Package Reference

### 7.41 SDO_GEOR.getBitmapMaskValues

#### Format

    SDO_GEOR.getBitmapMaskValues(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         rowNumbers   IN SDO_NUMBER_ARRAY,
         colNumbers   IN SDO_NUMBER_ARRAY
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.getBitmapMaskValues(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER,
         pyramidLevel IN VARCHAR2,
         ptGeom       IN SDO_GEOMETRY
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Gets the values of multiple cells from a bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer on which to perform the operation. A value of 0 (zero) indicates the object layer.

pyramidLevel
Pyramid level containing the specified cell.

rowNumbers
Numbers of the rows that contain the cells whose values are to be returned.

colNumbers
Numbers of the columns that contain the cells whose values are to be returned.

ptGeom
Multipoint geometry that identifies the cells whose values are to be returned.

#### Usage Notes

You can specify the cells by an array of row and column numbers or by a multipoint geometry object.

If there is no bitmap associated with the specified GeoRaster object at the specified raster layer, or the specified cell is in an empty raster block, the function returns a null value.

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example gets the value of four cells from the bitmap mask associated with a specified GeoRaster object.

    SELECT sdo_geor.getBitmapMaskValues(georaster,0,0,sdo_number_array(0,9,9,10),sdo_number_array(0,9,10,9))
      FROM georaster_table WHERE georid=0;

**Parent topic:** SDO_GEOR Package Reference

### 7.42 SDO_GEOR.getBlankCellValue

#### Format

    SDO_GEOR.getBlankCellValue(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the cell value for all cells if a specified GeoRaster object is a blank GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

In a blank GeoRaster object, all cells have the same cell value. This function returns the cell value for all cells if the specified GeoRaster object is a blank GeoRaster object.

To set the cell value to be used if a specified GeoRaster object is a blank GeoRaster object, use the SDO_GEOR.setBlankCellValue procedure. To determine if a specified GeoRaster object is a blank GeoRaster object, use the SDO_GEOR.isBlank function.

If `georaster` is null, invalid, or is not a blank GeoRaster object, the SDO_GEOR.getBlankCellValue function returns a null value.

#### Examples

The following example returns the blank cell values for all blank GeoRaster objects in the GEORASTER column of table GEORASTER_TABLE.

    SELECT georid, sdo_geor.getBlankCellValue(georaster) blankValue
      FROM georaster_table WHERE sdo_geor.isBlank(georaster)='TRUE';

        GEORID BLANKVALUE
    ---------- ----------
             1        255
             2        155

**Parent topic:** SDO_GEOR Package Reference

### 7.43 SDO_GEOR.getBlockingType

#### Format

    SDO_GEOR.getBlockingType(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the blocking type for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns one of the following values: `NONE` or `REGULAR`:

- `NONE` means that the GeoRaster object is not blocked, but is a single BLOB object.

- `REGULAR` means that the GeoRaster object uses regular blocking, that is, each block has the same dimension sizes.

If `georaster` or its metadata is null, this function returns a null value.

#### Examples

The following example returns the cell depth, interleaving type, and blocking type of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getCellDepth(georaster) CellDepth,
           substr(sdo_geor.getInterleavingType(georaster),1,8) interleavingType,
           substr(sdo_geor.getBlockingType(georaster),1,8) blocking
      FROM georaster_table WHERE georid=21;

     CELLDEPTH INTERLEA BLOCKING
    ---------- -------- --------
             8 BSQ      REGULAR

**Parent topic:** SDO_GEOR Package Reference

### 7.44 SDO_GEOR.getBlockSize

#### Format

    SDO_GEOR.getBlockSize(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the number of cells for each dimension in each block of a GeoRaster object in an array showing the number of cells for each row, column, and (if relevant) band.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

If `georaster` or its metadata is null, or if `georaster` is not blocked, this function returns a null value.

#### Examples

The following example returns the number of cells (512 in each dimension) in each block of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getBlockSize(georaster) blockSize
       FROM georaster_table WHERE georid=21;

    BLOCKSIZE
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(512, 512)

**Parent topic:** SDO_GEOR Package Reference

### 7.45 SDO_GEOR.getCellCoordinate

#### Format

    SDO_GEOR.getCellCoordinate(
         georaster       IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         modelCoordinate IN SDO_GEOMETRY,
         subCell         IN VARCHAR2 DEFAULT NULL,
         height          IN NUMBER DEFAULT NULL,
         vert_id         IN NUMBER DEFAULT NULL,
         ellipsoidal     IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.getCellCoordinate(
         georaster       IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         modelCoordinate IN SDO_GEOMETRY,
         cellCoordinate  OUT SDO_GEOMETRY,
         subCell         IN VARCHAR2 DEFAULT NULL,
         height          IN NUMBER DEFAULT NULL,
         vert_id         IN NUMBER DEFAULT NULL,
         ellipsoidal     IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getCellCoordinate(
         georaster            IN SDO_GEORASTER,
         sourcePyramidLevel   IN NUMBER,
         sourceCellCoordinate IN SDO_NUMBER_ARRAY,
         targetPyramidLevel   IN NUMBER,
         subCell              IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.getCellCoordinate(
         georaster            IN SDO_GEORASTER,
         sourcePyramidLevel   IN NUMBER,
         sourceCellCoordinate IN SDO_GEOMETRY,
         targetPyramidLevel   IN NUMBER,
         subCell              IN VARCHAR2 DEFAULT NULL,
         ) RETURN SDO_GEOMETRY;

#### Description

Returns the coordinates in the cell (raster) coordinate system associated with the geometry at the specified model (ground) coordinates (first two formats), or converts cell coordinates between pyramid levels (last two formats).

Note that the second format is a procedure; the other formats are functions.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the cell specified in `modelCoordinate`.

modelCoordinate
The geometry that is to be converted.

cellCoordinate
The output geometry in the cell space of the GeoRaster object.

sourcePyramidLevel (last two formats)
Pyramid level with which the input cell coordinate is associated.

sourceCellCoordinate (last two formats)
Input cell coordinates to be converted. Must be a two-dimensional geometry, and its SDO_SRID value must be null.

targetPyramidLevel (last two formats)
Pyramid level of the returned (target) GeoRaster object.

subCell
String (`TRUE` or `FALSE`) specifying whether to return the cell coordinates in sub-pixel (floating) values.

height
Number specifying the Z value for three-dimensional (X, Y, Z) georeferencing.

vert_id
Number specifying the vertical reference ID.

ellipsoidal
String specifying whether the vertical reference system is ellipsoidal (`TRUE`) or not ellipsoidal (`FALSE`).

#### Usage Notes

The first two formats of this function return the coordinates in the cell (raster) coordinate system associated with the geometry at the specified model (ground) coordinates:

- Use the first format (a function without the `cellCoordinate` parameter) to transform a point in the ground coordinate system (a longitude, latitude pair) to the location of a point on the GeoRaster image.

- Use the second format (a procedure with the `cellCoordinate` parameter) to transform a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object. The conversion is done by converting the coordinates of each vertex of the input geometry from the ground coordinate system to the raster space of the GeoRaster object.

The last two formats of this function convert cell coordinates between pyramid levels. If the type of the `sourceCellCoordinate` parameter is SDO_NUMBER_ARRAY, it specifies the \<row,column\> pair for a point in the cell space at the source pyramid level. If the type of the sourceCellCoordinate parameter is SDO_GEOMETRY, it specifies a geometry in the cell space at the source pyramid level. The coordinates of each vertex of the input geometry are converted according to the specified pyramid levels.

- Use the first format (without the `cellCoordinate` parameter) to transform a point in the ground coordinate system (a longitude, latitude pair) to the location of a point on the GeoRaster image.

- Use the second format (with the `cellCoordinate` parameter) to transform a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object. The conversion is done by converting the coordinates of each vertex of the input geometry from the ground coordinate system to the raster space of the GeoRaster object.

If the SDO_SRID value of the `modelCoordinate` geometry is null, the parameter specifies a geometry in the raster space; otherwise, it specifies a point in a ground coordinate system. If the ground coordinate system is different from the model coordinate system, the `modelCoordinate` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed.

Contrast this function with SDO_GEOR.getModelCoordinate, which returns a point geometry containing the coordinates in the model (ground) coordinate system associated with the point at the specified cell coordinates.

#### Examples

The following example returns the cell coordinates in the raster image associated with model coordinate values (32343.64,7489527.23) in a specified GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getCellCoordinate(georaster, 0, sdo_geometry(2001,82394,
      sdo_point_type(32343.64,7489527.23,null), null,null)) coord
    FROM georaster_table WHERE georid=4;

    COORD
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(100, 100)

The following example returns the geometry at pyramid level 0 that is associated with the specified geometry at pyramid level 2, assuming the geometry is not georeferenced (the model coordination location is CENTER) and the ultCoordinate is (100,-100,0).

    SELECT sdo_geor.getCellCoordinate(georaster, 2,
                    sdo_geometry(2003,NULL,NULL,sdo_elem_info_array(1,1003,3),
                                 sdo_ordinate_array(100.8,-100.2,220.15,0.3)),
                    0, 'true') coord
    FROM georaster_table WHERE georid=1;

    COORD
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(104.7, -99.3, 582.1, 302.7))

**Parent topic:** SDO_GEOR Package Reference

### 7.46 SDO_GEOR.getCellDepth

#### Format

    SDO_GEOR.getCellDepth(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the cell depth in bits.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The cell depth determines the precision and the data size of an image. As the cell depth value decreases, less disk space is needed to store the image; as the cell depth value increases, more disk space is needed to store the image.

To return the cell depth as a string (such as `32BIT_S`) instead of a number, you can use the XMLType PL/SQL interface `extract`. The possible string values are listed in the `cellDepthType` definition in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The following example returns a string value for the cell depth of the GeoRaster object with the GEORID column value of 21 in the GEORASTER_TABLE table:

    SELECT t.georaster.metadata.extract(
             '/georasterMetadata/rasterInfo/cellDepth/text()',
             'xmlns=http://xmlns.oracle.com/spatial/georaster')
      FROM georaster_table t WHERE t.georid=21;

#### Examples

The following example returns the cell depth, interleaving type, and blocking type of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getCellDepth(georaster) CellDepth,
           substr(sdo_geor.getInterleavingType(georaster),1,8) interleavingType,
           substr(sdo_geor.getBlockingType(georaster),1,8) blocking
      FROM georaster_table WHERE georid=21;

     CELLDEPTH INTERLEA BLOCKING
    ---------- -------- --------
             8 BSQ      REGULAR

**Parent topic:** SDO_GEOR Package Reference

### 7.47 SDO_GEOR.getCellValue

#### Format

    SDO_GEOR.getCellValue(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         rowNumber    IN NUMBER,
         colNumber    IN NUMBER,
         bandNumber   IN NUMBER
         ) RETURN NUMBER;

or

    SDO_GEOR.getCellValue(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         rowNumber    IN NUMBER,
         colNumber    IN NUMBER,
         bands        IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.getCellValue(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         ptGeom       IN SDO_GEOMETRY,
         layerNumber  IN NUMBER
         ) RETURN NUMBER;

or

    SDO_GEOR.getCellValue(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         ptGeom       IN SDO_GEOMETRY,
         layers       IN VARCHAR2
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the value of a single cell located anywhere in the GeoRaster object by specifying its row, column, and band number or numbers in its cell coordinate system, or by specifying a point geometry in its model coordinate system and its logical layer number or numbers.

If the specified cell is in an empty raster block, the function returns a null value.

To change the value of raster data cells in a specified window of a GeoRaster object, use the SDO_GEOR.changeCellValue procedure.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the cell whose value is to be returned.

rowNumber
Number of the row that contains the cell whose value is to be returned.

colNumber
Number of the column that contains the cell whose value is to be returned.

bandNumber
Number of the physical band that contains the cell whose value is to be returned.

bands
A string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

ptGeom
Point geometry that identifies the cell whose value is to be returned.

layerNumber
Number of the logical layer that contains the cell whose value is to be returned. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

layers
A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4). (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

#### Usage Notes

This function returns the original cell value stored in the raster object. It does not do any interpolation using cell values. (To evaluate a point location using an interpolation method, use the SDO_GEOR.evaluateDouble function.) It does not apply the scaling function defined in the metadata (which is typically used to scale the original cell data to a desired value or range of values), and it does not apply the bin function. To get the scaled cell value, follow these steps:

1.  Call the SDO_GEOR.getCellValue function to return the original cell value.

2.  Call the SDO_GEOR.getScaling function to return the coefficients of the scaling function (a<sub>0</sub>, a<sub>1</sub>, b<sub>0</sub>, b<sub>1</sub>).

3.  Using PL/SQL or another programming language, calculate the result using the following formula:

        value = (a0 + a1 * cellvalue) / (b0 + b1 * cellvalue)

#### Examples

The following example returns the values of four cells of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getCellValue(georaster,0,383,47,0) V383_47,
           sdo_geor.getCellValue(georaster,0,47,383,0) V47_383,
           sdo_geor.getCellValue(georaster,0,128,192,0) V128_192,
           sdo_geor.getCellValue(georaster,0,320,256,0) V320_256
      FROM georaster_table WHERE georid=21;

       V383_47    V47_383   V128_192   V320_256
    ---------- ---------- ---------- ----------
            48         55         52         53

The following example returns the values of the cells in bands 0, 1, and 2 for row number 10, column number 10 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 1 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getcellvalue(a.georaster,0,10,10,'0-2')
      FROM georaster_table a WHERE georid=1;

    SDO_GEOR.GETCELLVALUE(A.GEORASTER,0,10,10,'0-2')
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(88, 137, 32)

**Parent topic:** SDO_GEOR Package Reference

### 7.48 SDO_GEOR.getCellValues

#### Format

    SDO_GEOR.getCellValues(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         rowNumbers   IN SDO_NUMBER_ARRAY,
         colNumbers   IN SDO_NUMBER_ARRAY,
         bandNumber   IN NUMBER
         ) RETURN SDO_NUMBER_ARRAY;

or

    SDO_GEOR.getCellValues(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         ptGeom       IN SDO_GEOMETRY,
         layerNumber  IN NUMBER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the values of one or more cells located anywhere in the GeoRaster object by specifying its row/column/band numbers in its cell coordinate space, or by specifying a multipoint geometry in either model coordinate space or cell coordinate space and its logical layer number.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the cells whose values are to be returned.

rowNumbers
Numbers of the rows that contains the cells whose values are to be returned.

colNumbers
Numbers of the columns that contains the cells whose values are to be returned.

bandNumber
Number of the physical band that contains the cells whose values are to be returned.

ptGeom
Multipoint geometry that identifies the cell whose value is to be returned.

layerNumber
Number of the logical layer that contains the cells whose values are to be returned. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

#### Usage Notes

This function returns the original cell values stored in the raster object. It does not do any interpolation using cell values. (To evaluate a point location using an interpolation method, use the SDO_GEOR.evaluateDoubles function.) It does not apply the scaling function defined in the metadata (which is typically used to scale the original cell data to a desired value or range of values), and it does not apply the bin function.

#### Examples

The following example returns the values of four cells of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getCellValues(georaster,0,SDO_NUMBER_ARRAY(383,47,128,320),SDO_NUMBER_ARRAY(47,383,192,256),0)
      FROM georaster_table WHERE georid=21;

    SDO_GEOR.GETCELLVALUES(A.GEORASTER,0,SDO_NUMBER_ARRAY(383,47,128,320),SDO_NUMBER_ARRAY(47,383,192,256),0)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(48,55,52,53)

**Parent topic:** SDO_GEOR Package Reference

### 7.49 SDO_GEOR.getColorMap

#### Format

    SDO_GEOR.getColorMap(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN SDO_GEOR_COLORMAP;

#### Description

Returns the colormap for pseudocolor display of a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the colormap. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns an object of type SDO_GEOR_COLORMAP. [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md) describes colormaps and this object type.

To set the colormap for a layer in a GeoRaster object, use the SDO_GEOR.setColorMap procedure.

If `georaster` or its metadata is null, this function returns a null value.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example returns the colormap for layer 1 of a GeoRaster object. (Part of the output is omitted.)

    SELECT sdo_geor.getColorMap(georaster, 1) FROM georaster_table
       WHERE georid = 4;

    SDO_GEOR.GETCOLORMAP(GEORASTER,1)(CELLVALUE, RED, GREEN, BLUE, ALPHA)
    --------------------------------------------------------------------------------
    SDO_GEOR_COLORMAP(SDO_NUMBER_ARRAY(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13,
     14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33,
     34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53,
     54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73,
     74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93,
     94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110,
    111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126,
    127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142,
    143, 144, 145, 146, 147, 148, 149, 150, 151, 152, 153, 154, 155, 156, 157, 158,
    159, 160, 161, 162, 163, 164, 165, 166, 167, 168, 169, 170, 171, 172, 173, 174,
    175, 176, 177, 178, 179, 180, 181, 182, 183, 184, 185, 186, 187, 188, 189, 190,
    191, 192, 193, 194, 195, 196, 197, 198, 199, 200, 201, 202, 203, 204, 205, 206,
    207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218, 219, 220, 221, 222,
    223, 224, 225, 226, 227, 228, 229, 230, 231, 232, 233, 234, 235, 236, 237, 238,
    239, 240, 241, 242, 243, 244, 245, 246, 247, 248, 249, 250, 251, 252, 253, 254,
    255), SDO_NUMBER_ARRAY(180, 180, 180, 180, 180, 180, 180, 180, 180, 180, 180, 18
    0, 127, 127, 100, 50, 50, 127, 159, 191, 223, 255, 255, 255, 255, 218, 182, 145,
     109, 72, 36, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
    0, 0, 36, 72, 109, 145, 182, 218, 255, 200, 206, 212, 218, 224, 230, 236, 242,
    248, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255), SDO_NUMBER_ARRAY(127, 127,
    127, 127, 127, 127, 127, 127, 127, 127, 127, 127, 180, 127, 50, 100, 50, 127,
    159, 191, 223, 255, 200, 150, 100, 122, 144, 166, 188, 210, 232, 255, 255, 255,
    248, 241, 234, 227, 220, 213, 206, 200, 150, 100, 87, 75, 62, 50, 37, 25, 12, 0,
    200, 127, 0, 0, 0, 0, 0, 0, 0, 0, 0, 28, 56, 85, 113, 141, 170, 198, 226, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255), SDO_NUMBER_ARRAY(127, 127, 127, 127,
    127, 127, 127, 127, 127, 127, 127, 127, 127, 180, 50, 50, 100, 127, 95, 63, 31,
    0, 0, 0, 0, 18, 36, 54, 72, 90, 108, 127, 100, 50, 43, 37, 31, 25, 18, 12, 6, 0,
    0, 0, 31, 63, 95, 127, 159, 191, 223, 255, 255, 255, 127, 108, 90, 72, 54, 36,
    18, 0, 0, 28, 56, 85, 113, 141, 170, 198, 226, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255), SDO_NUMBER_ARRAY(255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255, 255,
    255, 255, 255, 255, 255, 255, 255))

**Parent topic:** SDO_GEOR Package Reference

### 7.50 SDO_GEOR.getColorMapTable

#### Format

    SDO_GEOR.getColorMapTable(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the colormap table for pseudocolor display of a layer in a GeoRaster object.

**Note:**

GeoRaster does not perform operations using the colormap table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the colormap table. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the name of a user-defined colormap table. For information about colormaps, see [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md).

To set the colormap table for a layer in a GeoRaster object, use the SDO_GEOR.setColorMapTable procedure.

If `georaster` or its metadata is null, this function returns a null value.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example returns the colormap table for layer 2 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getColorMapTable(georaster, 2) FROM georaster_table WHERE georid=4;

    SDO_GEOR.GETCOLORMAPTABLE(GEORASTER,2)
    --------------------------------------------------------------------------------
    CMT1

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.51 SDO_GEOR.getCompressionType

#### Format

    SDO_GEOR.getCompressionType(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the compression type for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function can return `DEFLATE`, `JPEG-F`, or `NONE` (the latter value meaning that the GeoRaster object is not compressed). For information about GeoRaster compression, see [Compression and Decompression](georaster-overview-and-concepts.md).

#### Examples

The following example returns the compression type for the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, substr(sdo_geor.getCompressionType(georaster),1,20) compressionType
      FROM georaster_table;

        GEORID COMPRESSIONTYPE
    ---------- --------------------
             2 DEFLATE
             4 JPEG-F

**Parent topic:** SDO_GEOR Package Reference

### 7.52 SDO_GEOR.getControlPoint

#### Format

    SDO_GEOR.getControlPoint (
         inGeoraster     IN SDO_GEORASTER,
         controlPointID  IN VARCHAR2
         ) RETURN SDO_GEOR_GCP;

#### Description

Returns the ground control point (GCP) that has the specified control point ID value.

#### Parameters

inGeoraster
GeoRaster object.

controlPointID
Control point ID of `inGeoraster`. Must be a string not more than 32 characters.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

This function returns an object of type SDO_GEOR_GCP, which is described in [SDO_GEOR_GCP Object Type](georaster-datatypes.md).

In the control point ID is null, empty, or missing in `inGeoraster`, an exception is raised.

#### Examples

The following example returns the GCP that has the ID value 25 in a specified GeoRaster object.

    SELECT sdo_geor.getControlPoint(georaster, '25') FROM georaster_table
      WHERE georid =10;

    SDO_GEOR.GETCONTROLPOINT(GEORASTER,'25')(POINTID, DESCRIPTION, POINTTYPE, CELLDI
    --------------------------------------------------------------------------------
    SDO_GEOR_GCP('25', NULL, 2, 2, SDO_NUMBER_ARRAY(167.470583, 64.030686), 2, SDO_N
    UMBER_ARRAY(237032.015, 897916.265), NULL, NULL)

**Parent topic:** SDO_GEOR Package Reference

### 7.53 SDO_GEOR.getDefaultAlpha

#### Format

    SDO_GEOR.getDefaultAlpha(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of the layer to be used for the alpha color component (in the RGBA color space) for displaying a GeoRaster object. If this value is not set in the metadata, a null value is returned.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The default red, green, blue, and alpha values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

You can return the layer numbers for all four color components (RGBA) by using the SDO_GEOR.getDefaultColorLayer function.

#### Examples

The following example returns the layer numbers for the red, green, blue, and alpha color components for displaying the GeoRaster objects in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getDefaultRed(georaster) red,
      sdo_geor.getDefaultGreen(georaster) green,
      sdo_geor.getDefaultBlue(georaster) blue,
      sdo_geor.getDefaultAlpha(georaster) alpha
    FROM georaster_table;

        GEORID        RED      GREEN       BLUE      ALPHA
    ---------- ---------- ---------- ---------- ----------
             1          1          2          3          4
             2
             3         31         20         13         10

**Parent topic:** SDO_GEOR Package Reference

### 7.54 SDO_GEOR.getDefaultBlue

#### Format

    SDO_GEOR.getDefaultBlue(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of the layer to be used for the blue color component (in the RGB color space) for displaying a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

You can return the layer numbers for all three color components (RGB) by using the SDO_GEOR.getDefaultColorLayer function.

#### Examples

The following example returns the layer numbers for the red, blue, and green color components for displaying the GeoRaster objects in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getDefaultRed(georaster) red,
      sdo_geor.getDefaultGreen(georaster) green,
      sdo_geor.getDefaultBlue(georaster) blue
    FROM georaster_table;

        GEORID        RED      GREEN       BLUE
    ---------- ---------- ---------- ----------
             1          1          2          3
             2
             3         31         20         13

**Parent topic:** SDO_GEOR Package Reference

### 7.55 SDO_GEOR.getDefaultColorLayer

#### Format

    SDO_GEOR.getDefaultColorLayer(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the default numbers of the layers to be used for the red, green, blue, and alpha color components, respectively, for displaying a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The RGB layer numbers returned are used for true-color displays, not for pseudocolor or grayscale displays.

You can return the layer number for each color component (RGBA) by using the SDO_GEOR.getDefaultRed, SDO_GEOR.getDefaultGreen, SDO_GEOR.getDefaultBlue, and SDO_GEOR.getDefaultAlpha functions.

The alpha color component is optional. If the default alpha color component exists in the metadata, this functions returns an array of four numbers identifying the red, green, blue, and alpha color components, respectively. If only the default red, green, and blue color components exist in the metadata, this functions returns an array of three numbers identifying the red, green, and blue color components respectively.

#### Examples

The following example sets the default red, green, and blue color layers for the GeoRaster objects (GEORASTER column) in table GEORASTER_TABLE, and it returns an array with the layer numbers for the red, green, and blue color components for displaying these GeoRaster objects. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setDefaultRed(grobj, 2);
      sdo_geor.setDefaultGreen(grobj, 3);
      sdo_geor.setDefaultBlue(grobj, 1);
      sdo_geor.setDefaultAlpha(grobj, 4);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getDefaultColorLayer(georaster) FROM georaster_table WHERE georid=4;

    SDO_GEOR.GETDEFAULTCOLORLAYER(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(2, 3, 1)
    SDO_NUMBER_ARRAY(2, 3, 1, 4)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.56 SDO_GEOR.getDefaultGreen

#### Format

    SDO_GEOR.getDefaultGreen(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of the layer to be used for the green color component (in the RGB color space) for displaying a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

You can return the layer numbers for all three color components (RGB) by using the SDO_GEOR.getDefaultColorLayer function.

#### Examples

The following example returns the layer numbers for the red, blue, and green color components for displaying the GeoRaster objects in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getDefaultRed(georaster) red,
      sdo_geor.getDefaultGreen(georaster) green,
      sdo_geor.getDefaultBlue(georaster) blue
    FROM georaster_table;

        GEORID        RED      GREEN       BLUE
    ---------- ---------- ---------- ----------
             1          1          2          3
             2
             3         31         20         13

**Parent topic:** SDO_GEOR Package Reference

### 7.57 SDO_GEOR.getDefaultPyramidLevel

#### Format

    SDO_GEOR.getDefaultPyramidLevel(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of the default pyramid level for displaying a GeoRaster object. If this value is not set in the metadata, a null value is returned.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

Pyramid levels represent reduced or increased resolution images that require less or more storage space, respectively. For information about pyramids and pyramid levels, see [Pyramids](georaster-overview-and-concepts.md).

You can set the default pyramid level by using the SDO_GEOR.setDefaultPyramidLevel procedure.

#### Examples

The following example returns the default pyramid level for displaying a specified GeoRaster object in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getDefaultPyramidLevel(georaster) plevel,
    FROM georaster_table WHERE georid = 6;

        GEORID       PLEVEL
    ---------- ----------
             6          3

**Parent topic:** SDO_GEOR Package Reference

### 7.58 SDO_GEOR.getDefaultRed

#### Format

    SDO_GEOR.getDefaultRed(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of the layer to be used for the red color component (in the RGB color space) for displaying a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

You can return the layer numbers for all three color components (RGB) by using the SDO_GEOR.getDefaultColorLayer function.

#### Examples

The following example returns the layer numbers for the red, blue, and green color components for displaying the GeoRaster objects in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getDefaultRed(georaster) red,
      sdo_geor.getDefaultGreen(georaster) green,
      sdo_geor.getDefaultBlue(georaster) blue
    FROM georaster_table;

        GEORID        RED      GREEN       BLUE
    ---------- ---------- ---------- ----------
             1          1          2          3
             2
             3         31         20         13

**Parent topic:** SDO_GEOR Package Reference

### 7.59 SDO_GEOR.getEndDateTime

#### Format

    SDO_GEOR.getEndDateTime(
         georaster  IN SDO_GEORASTER
         ) RETURN TIMESTAMP WITH TIME ZONE;

#### Description

Returns the ending date and time for raster data collection in the metadata for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

To set the ending date and time for raster data collection in the metadata for a GeoRaster object, use the SDO_GEOR.setEndDateTime procedure.

If `georaster` or its metadata is null, this function returns a null value.

#### Examples

The following example returns the beginning and ending dates and times for raster data collection in the metadata for the GeoRaster object in a table named GEORASTER_TABLE where the GEORID column contains the value 4. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getBeginDateTime(georaster) beginDateTime,
      sdo_geor.getEndDateTime(georaster) endDateTime
      FROM georaster_table WHERE georid=4;

    BEGINDATETIME
    ---------------------------------------------------------------------------
    ENDDATETIME
    ---------------------------------------------------------------------------
    01-JAN-00 05.00.00.000000000 AM +00:00
    15-NOV-02 08.00.00.000000000 PM +00:00

**Parent topic:** SDO_GEOR Package Reference

### 7.60 SDO_GEOR.getGCPGeorefMethod

#### Format

    SDO_GEOR.getGCPGeorefMethod(
         inGeoraster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the ground control point (GCP)-based georeferencing geometric model type of a GeoRaster object.

#### Parameters

inGeoraster
GeoRaster object.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

If `inGeoraster` does contains valid georeferencing model information, it returns one of the following values: `Affine`, `QuadraticPolynomial`, `CubicPolynomial`, `DLT`, `QuadraticRational`, or `RPC`.

If `inGeoraster` does not contain any georeferencing model information, this function returns a null value.

#### Examples

The following example returns the GCP-based georeferencing model information in a specified GeoRaster object. (The output is reformatted for readability.)

    SELECT sdo_geor.getGCPGeorefMethod(georaster) FROM georaster_table
      WHERE georid =10;

    SDO_GEOR.GETGCPGEOREFMETHOD(GEORASTER)
    --------------------------------------------------------------------------------
    Affine

**Parent topic:** SDO_GEOR Package Reference

### 7.61 SDO_GEOR.getGCPGeorefModel

#### Format

    SDO_GEOR.getGCPGeorefModel(
         inGeoraster  IN SDO_GEORASTER
         ) RETURN SDO_GEOR_GCPGEOREFTYPE;

#### Description

Returns all information about the ground control point (GCP)-based georeferencing model in a GeoRaster object.

#### Parameters

inGeoraster
GeoRaster object.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

The SDO_GEOR_GCPGEOREFTYPE object type is defined in [SDO_GEOR_GCPGEOREFTYPE Object Type](georaster-datatypes.md).

If `inGeoraster` does not contain any georeferencing model information, this function returns a null value.

#### Examples

The following example returns the GCP-based georeferencing model information in a specified GeoRaster object. (The output is reformatted for readability.)

    SELECT sdo_geor.getGCPGeorefModel(georaster) FROM georaster_table WHERE georid=10;

    SDO_GEOR.GETGCPGEOREFMODEL(GEORASTER)(FFMETHODTYPE,
    NUMBERGCP, GCPS(POINTID, DES...
    --------------------------------------------------------------------------------
    SDO_GEOR_GCPGEOREFTYPE('Affine', 6,
    SDO_GEOR_GCP_COLLECTION(
    SDO_GEOR_GCP('21', NULL, 1, 2,SDO_NUMBER_ARRAY(25.625, 73.875), 2, SDO_NUMBER_ARRAY(237036.938,897987.188), NULL, NULL),
    SDO_GEOR_GCP('22', NULL, 1, 2,SDO_NUMBER_ARRAY(100.625, 459.125), 2,SDO_NUMBER_ARRAY(237229.563, 897949.688), NULL, NULL),
    SDO_GEOR_GCP('23', NULL, 1, 2, SDO_NUMBER_ARRAY(362.375, 77.875), 2,
    SDO_NUMBER_ARRAY(237038.938, 897818.813), NULL, NULL),
    SDO_GEOR_GCP('24', NULL, 1, 2, SDO_NUMBER_ARRAY(478.875, 402.125), 2,
    SDO_NUMBER_ARRAY(237201.063, 897760.563), NULL, NULL),
    SDO_GEOR_GCP('25', NULL, 2, 2, SDO_NUMBER_ARRAY(167.470583,
    64.030686), 2, SDO_NUMBER_ARRAY(237032.015, 897916.265), NULL, NULL),
    SDO_GEOR_GCP('26', NULL, 2, 2, SDO_NUMBER_ARRAY(101.456177,
    257.915534), 2, SDO_NUMBER_ARRAY(237128.958, 897949.272), NULL, NULL)),
    NULL)

**Parent topic:** SDO_GEOR Package Reference

### 7.62 SDO_GEOR.getGeoreferenceType

#### Format

    SDO_GEOR.getGeoreferenceType(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns a number that indicates the georeference type for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns one of the following numbers to indicate the georeference type: 1 for unknown type or null GeoRaster object, 2 for affine transform, 3 for direct linear transform (DLT), 4 for rational polynomial coefficient (RPC), 5 for cubic polynomial, 6 for quadratic rational polynomial, or 7 for quadratic polynomial.

For an explanation of georeferencing, see [Georeferencing](georaster-overview-and-concepts.md).

#### Examples

The following example returns the georeference type for the GeoRaster objects in a table named GEORASTER_TABLE. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT georid,sdo_geor.getGeoreferenceType(a.georaster)
      FROM georaster_table a ORDER BY georid;

        GEORID SDO_GEOR.GETGEOREFERENCETYPE(A.GEORASTER)
    ---------- -----------------------------------------
             1                                         1
             2                                         1
             3                                         1
             4                                         1
             5                                         1
             7                                         1
             8                                         2
             9                                         1
            10                                         1
            12                                         1
            13                                         1
            14                                         2
            15                                         1
            16                                         1
            17                                         1
            18                                         1
            19                                         2
            20                                         2
            21                                         4
            22                                         4

**Parent topic:** SDO_GEOR Package Reference

### 7.63 SDO_GEOR.getGrayScale

#### Format

    SDO_GEOR.getGrayScale(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN SDO_GEOR_GRAYSCALE;

#### Description

Returns the grayscale mappings for a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the grayscale mappings. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns an object of type SDO_GEOR_GRAYSCALE. [SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md) describes grayscale display and this object type.

To set the grayscale mappings for a layer in a GeoRaster object, use the SDO_GEOR.setGrayScale procedure.

#### Examples

The following example returns the grayscale mappings for layer 0 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 0 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getGrayScale(georaster, 0) FROM georaster_table WHERE georid=0;

    SDO_GEOR.GETGRAYSCALE(GEORASTER,0)(CELLVALUE, GRAY)
    --------------------------------------------------------------------------------
    SDO_GEOR_GRAYSCALE(SDO_NUMBER_ARRAY(10, 20, 30, 255), SDO_NUMBER_ARRAY(180, 210,
    230, 250))

**Parent topic:** SDO_GEOR Package Reference

### 7.64 SDO_GEOR.getGrayScaleTable

#### Format

    SDO_GEOR.getGrayScaleTable(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the grayscale mapping table for a layer in a GeoRaster object.

**Note:**

GeoRaster does not perform operations using the grayscale mapping table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the grayscale mapping table. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the name of a user-defined grayscale table. [SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md) describes grayscale display.

To set the grayscale mapping table for a layer in a GeoRaster object, use the SDO_GEOR.setGrayScaleTable procedure.

#### Examples

The following example returns the grayscale mapping tables for layers 0, 1, 2, and 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT substr(sdo_geor.getGrayScaleTable(georaster, 0),1,20) grayScaleTable0,
           substr(sdo_geor.getGrayScaleTable(georaster, 1),1,20) grayScaleTable1,
           substr(sdo_geor.getGrayScaleTable(georaster, 2),1,20) grayScaleTable2,
           substr(sdo_geor.getGrayScaleTable(georaster, 3),1,20) grayScaleTable3
      FROM georaster_table WHERE georid=4;

    GRAYSCALETABLE0      GRAYSCALETABLE1      GRAYSCALETABLE2      GRAYSCALETABLE3
    -------------------- -------------------- -------------------- -----------------
    SCL0                 SCL1                 SCL2                 SCL3

**Parent topic:** SDO_GEOR Package Reference

### 7.65 SDO_GEOR.getHistogram

#### Format

    SDO_GEOR.getHistogram(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN SDO_GEOR_HISTOGRAM;

#### Description

Returns the histogram for a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the histogram. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns an object of type SDO_GEOR_HISTOGRAM. [SDO_GEOR_HISTOGRAM Object Type](georaster-datatypes.md) describes this object type and briefly discusses histograms.

#### Examples

The following example returns the histogram for layer 1 of a 4-bit GeoRaster object in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getHistogram(georaster, 1) layer1
     FROM georaster_table WHERE georid=17;

    LAYER1(CELLVALUE, COUNT)
    --------------------------------------------------------------------------------
    SDO_GEOR_HISTOGRAM(SDO_NUMBER_ARRAY(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11,12, 13,
     14, 15), SDO_NUMBER_ARRAY(10, 18, 10, 110, 200, 120, 130, 150, 160, 103, 106,
     190, 12, 17, 10, 5))

**Parent topic:** SDO_GEOR Package Reference

### 7.66 SDO_GEOR.getHistogramTable

#### Format

    SDO_GEOR.getHistogramTable(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the histogram table for a layer in a GeoRaster object.

**Note:**

GeoRaster does not perform operations using the histogram table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the name of the histogram table. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns a user-defined histogram table. [SDO_GEOR_HISTOGRAM Object Type](georaster-datatypes.md) briefly discusses histograms.

To set the name of the histogram table for a layer, use the SDO_GEOR.setHistogramTable procedure.

#### Examples

The following example returns the histogram tables for layers 0 (the whole object), 1, 2, and 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT substr(sdo_geor.getHistogramTable(georaster, 0),1,20) histogramTable0,
           substr(sdo_geor.getHistogramTable(georaster, 1),1,20) histogramTable1,
           substr(sdo_geor.getHistogramTable(georaster, 2),1,20) histogramTable2,
           substr(sdo_geor.getHistogramTable(georaster, 3),1,20) histogramTable3
      FROM georaster_table WHERE georid=4;

    HISTOGRAMTABLE0      HISTOGRAMTABLE1      HISTOGRAMTABLE2      HISTOGRAMTABLE3
    -------------------- -------------------- -------------------- -----------------
    HIST0                HIST1                HIST2                HIST3

**Parent topic:** SDO_GEOR Package Reference

### 7.67 SDO_GEOR.getID

#### Format

    SDO_GEOR.getID(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the user-defined identifier value associated with a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

To set a user-defined identifier value for a GeoRaster object, use the SDO_GEOR.setID procedure.

#### Examples

The following example returns the user-defined identifier values of the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, substr(sdo_geor.getID(georaster),1,50) GEOR_ID
      FROM georaster_table;

        GEORID GEOR_ID
    ---------- --------------------------------------------------
             2 TM_102
             4 TM_104

**Parent topic:** SDO_GEOR Package Reference

### 7.68 SDO_GEOR.getInterleavingType

#### Format

    SDO_GEOR.getInterleavingType(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the interleaving type for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns one of the following values: `BSQ` (band sequential), `BIL` (band interleaved by line), or `BIP` (band interleaved by pixel).

To change the interleaving type for a GeoRaster object, use the SDO_GEOR.changeFormatCopy procedure, and use the `interleaving` keyword in the `storageParam` parameter string.

#### Examples

The following example returns the cell depth, interleaving type, and blocking type of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getCellDepth(georaster) CellDepth,
           substr(sdo_geor.getInterleavingType(georaster),1,8) interleavingType,
           substr(sdo_geor.getBlockingType(georaster),1,8) blocking
      FROM georaster_table WHERE georid=21;

     CELLDEPTH INTERLEA BLOCKING
    ---------- -------- --------
             8 BSQ      REGULAR

**Parent topic:** SDO_GEOR Package Reference

### 7.69 SDO_GEOR.getJP2TileSize

#### Format

    SDO_GEOR.getJP2TileSize(
         georaster   IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns an array showing the size of tiles in the JPEG2000 compressed GeoRaster image, in row and column order.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

If there is no tiling in the JPEG2000 compressed GeoRaster image, null is returned.

#### Examples

The following example returns the tile size in the JPEG2000 compressed GeoRaster object (GEORASTER column) in the row with the GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getJP2TileSize(georaster) JP2TileSize
       FROM georaster_table WHERE georid=21;

    JP2TILESIZE
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(350, 512)

**Parent topic:** SDO_GEOR Package Reference

### 7.70 SDO_GEOR.getLayerDimension

#### Format

    SDO_GEOR.getLayerDimension(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_STRING_ARRAY;

#### Description

Returns the dimension that is mapped as the logical layer dimension of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The layer dimension refers to the physical entity associated with the logical term layer. For the current release, the only supported layer dimension is `BAND`: that is, the logical concept layer is associated with the physical term band, as shown in [Figure 1-5](georaster-overview-and-concepts.md) in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md). In this case, layers will be mapped to the `BAND` dimension, so that the first layer is band 0, the second layer is band 1, and so on.

#### Examples

The following example returns the layer dimension of each GeoRaster object (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). (The output is reformatted for readability.)

    SELECT georid, sdo_geor.getLayerDimension(georaster) FROM georaster_table;

        GEORID SDO_GEOR.GETLAYERDIMENSION(GEORASTER)
    ---------- ------------------------------------------------------------------
             2 SDO_STRING_ARRAY('BAND')
             4 SDO_STRING_ARRAY('BAND')

**Parent topic:** SDO_GEOR Package Reference

### 7.71 SDO_GEOR.getLayerID

#### Format

    SDO_GEOR.getLayerID(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the user-defined identifier value associated with a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the user-defined identifier value. A value of 0 (zero) indicates the object layer.

#### Usage Notes

To set a user-defined identifier value for a layer in a GeoRaster object, use the SDO_GEOR.setLayerID procedure.

#### Examples

The following example returns the user-defined identifier values of layers 0, 1, 2, and 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT substr(sdo_geor.getLayerID(georaster, 0),1,12) layerID0,
           substr(sdo_geor.getLayerID(georaster, 1),1,12) layerID1,
           substr(sdo_geor.getLayerID(georaster, 2),1,12) layerID2,
           substr(sdo_geor.getLayerID(georaster, 3),1,12) layerID3
      FROM georaster_table WHERE georid=4;

    LAYERID0     LAYERID1     LAYERID2     LAYERID3
    ------------ ------------ ------------ ------------
    TM543        TM3          TM4          TM5

**Parent topic:** SDO_GEOR Package Reference

### 7.72 SDO_GEOR.getLayerOrdinate

#### Format

    SDO_GEOR.getLayerOrdinate(
         georaster   IN SDO_GEORASTER,
        layerNumber IN NUMBER
        ) RETURN NUMBER;

#### Description

Returns the band ordinate for a layer in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the physical band ordinate. A value of 0 (zero) indicates the object layer.

#### Usage Notes

The returned number refers to the physical band that a layer (`layerNumber` parameter value) is associated with. For the current release, by default the associations are as shown in [Figure 1-5](georaster-overview-and-concepts.md) in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md): layer 1 is band 0, layer 2 is band 1, and so on.

To set the band ordinate value for a layer, use the SDO_GEOR.setLayerOrdinate procedure.

#### Examples

The following example returns the band numbers associated with layers 0, 1, 2, and 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT sdo_geor.getLayerOrdinate(georaster, 0) layerOrdinate0,
           sdo_geor.getLayerOrdinate(georaster, 1) layerOrdinate1,
           sdo_geor.getLayerOrdinate(georaster, 2) layerOrdinate2,
           sdo_geor.getLayerOrdinate(georaster, 3) layerOrdinate3
      FROM georaster_table WHERE georid=4;

    LAYERORDINATE0 LAYERORDINATE1 LAYERORDINATE2 LAYERORDINATE3
    -------------- -------------- -------------- --------------
                                0              1              2

**Parent topic:** SDO_GEOR Package Reference

### 7.73 SDO_GEOR.getModelCoordinate

#### Format

    SDO_GEOR.getModelCoordinate(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         cellCoordinate IN SDO_NUMBER_ARRAY,
         height         IN NUMBER DEFAULT NULL,
         ) RETURN SDO_GEOMETRY;

or

    SDO_GEOR.getModelCoordinate(
         georaster       IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         cellCoordinate  IN SDO_GEOMETRY,
         modelCoordinate OUT SDO_GEOMETRY,
         height          IN NUMBER DEFAULT NULL);

#### Description

Returns a geometry associated with the specified cell (raster) coordinates at the specified pyramid level.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level containing the cell specified in `cellCoordinate`.

cellCoordinate
If the type is SDO_NUMBER_ARRAY, `cellCoordinate` is an array of two coordinates identifying the point in the cell coordinate system: the two coordinates are the row number and column number of the point. If the type is SDO_GEOMETRY, `cellCoordinate` specifies a geometry in the cell coordinate system

modelCoordinate
The output geometry.

height
Number specifying the Z value for three-dimensional (X, Y, Z) georeferencing.

#### Usage Notes

SDO_GEOR.getModelCoordinate has two formats:

- Use the first format (a function without the `modelCoordinate` parameter) to transform the location of a point in the GeoRaster object's raster space.

- Use the second format (a procedure with the `modelCoordinate` parameter) to transform a geometry in the raster space of the GeoRaster object. The conversion is done by converting the coordinates of each vertex of the input geometry. Use an appropriate input geometry so that the output geometry will be valid. For example, if the model coordinate system is geodetic, the input geometry should not contain any arcs.

Use SDO_GEOR.getModelCoordinate to transform the location of a point on the GeoRaster object to the longitude and latitude coordinates of its associated point in the ground coordinate system.

If the GeoRaster object is georeferenced, the output geometry contains the coordinates in the model (ground) coordinate system. If the GeoRaster object is not georeferenced, the output geometry contains cell coordinates at the original image level.

If the GeoRaster object is georeferenced, the SDO_SRID value of the output geometry is the same as the model SRID of the GeoRaster object.

Contrast SDO_GEOR.getModelCoordinate with SDO_GEOR.getCellCoordinate, which returns the coordinates in the cell (raster) coordinate system associated with the point at the specified model (ground) coordinates.

#### Examples

The following example returns a point geometry object containing the model coordinates associated with cell coordinates (100,100) in a specified GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SET NUMWIDTH 20
    SELECT sdo_geor.getModelCoordinate(georaster, 0,
    sdo_number_array(100,100)) mcoord
      FROM georaster_table WHERE georid=4;

    MCOORD(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------

    SDO_GEOMETRY(2001, 82394, SDO_POINT_TYPE(347.666315789474, 43274.9052631579, NUL
    L), NULL, NULL)

**Parent topic:** SDO_GEOR Package Reference

### 7.74 SDO_GEOR.getModelCoordLocation

#### Format

    SDO_GEOR.getModelCoordLocation(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the model coordinate location value for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns a null value if the GeoRaster object is not georeferenced or if the `modelCoordinateLocation` element is not specified in the SRS metadata. Otherwise, it returns the `modelCoordinateLocation` element value specified in the SRS metadata.

A null return value or a value of `CENTER` means that the cell coordinate system is center-based. A value of `UPPERLEFT` means that the cell coordinate system is based on the upper-left corner.

To set or delete the model coordinate location value for a GeoRaster object, use the SDO_GEOR.setModelCoordLocation procedure.

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

#### Examples

The following example returns the model coordinate location of a specified GeoRaster object.

    SELECT sdo_geor.getModelCoordLocation(georaster) modelCoordLocation
      FROM georaster_table
      WHERE georid = 1;

**Parent topic:** SDO_GEOR Package Reference

### 7.75 SDO_GEOR.getModelSRID

#### Format

    SDO_GEOR.getModelSRID(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the coordinate system (SDO_SRID value) associated with the model (ground) space for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns a null value if no coordinate system is associated with the model space.

To set the coordinate system (SDO_SRID value) associated with the model space, use the SDO_GEOR.setModelSRID procedure.

#### Examples

The following example returns the SDO_SRID values associated with the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getModelSRID(georaster) SRID FROM georaster_table;

        GEORID       SRID
    ---------- ----------
             2       82394
             4       82394

**Parent topic:** SDO_GEOR Package Reference

### 7.76 SDO_GEOR.getNODATA

#### Format

    SDO_GEOR.getNODATA(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN SDO_RANGE_ARRAY;

#### Description

Returns the values or value ranges that represent NODATA cells in a GeoRaster object (in ascending order, without duplicates).

#### Parameters

georaster
GeoRaster object.

layerNumber
Layer number in the GeoRaster object. A value of 0 (zero) indicates the object layer.

#### Usage Notes

Some cells of a GeoRaster object may have no meaningful value assigned or collected. Such cells contain a NODATA value are thus called NODATA cells, which means that those cells are not semantically defined. The application is responsible for defining the meaning or significance of cells identified as NODATA cells. For more information about NODATA values and value ranges, see [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

This function returns all the NODATA values and value ranges associated with a specified raster layer of the specified GeoRaster object, in ascending order and in a compact form with duplicates eliminated. The set of NODATA values and value ranges associated with a sublayer (`layerNumber` \> 0) is always a superset of the values and value ranges of the object layer (`layerNumber` = 0). The result for a sublayer is the combination of the NODATA metadata entries for the specified sublayer, the object layer, and any pre-release 11g NODATA metadata stored as part of the raster description information.

If the specified GeoRaster object or layer has more than one NODATA value, you must use the function format that returns an SDO_RANGE_ARRAY object. The SDO_RANGE_ARRAY type is described in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

If this function returns a null value, it means that all cells of the GeoRaster object or of the specified layer are defined and have a meaningful cell value.

To specify the NODATA values for a GeoRaster object, use the SDO_GEOR.addNODATA procedure.

#### Examples

The following example returns the value to be used for NODATA cells in the GeoRaster objects (GEORASTER column) in table GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT SDO_GEOR.getNODATA(georaster, 0) NODATA FROM georaster_table WHERE georid=0;

    NODATA
    ------------
    SDO_RANGE_ARRAY(SDO_RANGE(5,7))

**Parent topic:** SDO_GEOR Package Reference

### 7.77 SDO_GEOR.getPyramidMaxLevel

#### Format

    SDO_GEOR.getPyramidMaxLevel(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the level number of the top pyramid of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

For information about pyramids, see [Pyramids](georaster-overview-and-concepts.md).

#### Examples

The following example returns the pyramid type and level number of the top pyramid for the GeoRaster object (GEORASTER column) in the row with an GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT substr(sdo_geor.getPyramidType(georaster),1,10) pyramidType,
           sdo_geor.getPyramidMaxLevel(georaster) maxLevel
      FROM georaster_table WHERE georid=21;

    PYRAMIDTYP   MAXLEVEL
    ---------- ----------
    DECREASE            3

**Parent topic:** SDO_GEOR Package Reference

### 7.78 SDO_GEOR.getPyramidType

#### Format

    SDO_GEOR.getPyramidType(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the pyramid type for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The pyramid type can be `NONE` (no pyramids) or `DECREASE`.

For information about pyramids, see [Pyramids](georaster-overview-and-concepts.md).

#### Examples

The following example returns the pyramid type and level number of the top pyramid for the GeoRaster object (GEORASTER column) in the row with an GEORID column value of 21 in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT substr(sdo_geor.getPyramidType(georaster),1,10) pyramidType,
           sdo_geor.getPyramidMaxLevel(georaster) maxLevel
      FROM georaster_table WHERE georid=21;

    PYRAMIDTYP   MAXLEVEL
    ---------- ----------
    DECREASE            3

**Parent topic:** SDO_GEOR Package Reference

### 7.79 SDO_GEOR.getRasterBlockLocator

#### Format

    SDO_GEOR.getRasterBlockLocator(
         georaster         IN SDO_GEORASTER,
         pyramidLevel      IN NUMBER,
         bandBlockNumber   IN NUMBER,
         rowBlockNumber    IN NUMBER,
         columnBlockNumber IN NUMBER,
         loc               IN OUT NOCOPY BLOB,
         isBitmapMask      IN VARCHAR2 DEFAULT NULL,
         lock_for_write    IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getRasterBlockLocator(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         rowNumber      IN NUMBER,
         colNumber      IN NUMBER,
         bandNumber     IN NUMBER,
         offset         OUT NUMBER,
         loc            IN OUT NOCOPY BLOB,
         isBitmapMask   IN VARCHAR2 DEFAULT NULL,
         lock_for_write IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getRasterBlockLocator(
         georaster      IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         ptGeom         IN SDO_GEOMETRY,
         layerNumber    IN NUMBER,
         offset         OUT NUMBER,
         loc            IN OUT NOCOPY BLOB,
         isBitmapMask   IN VARCHAR2 DEFAULT NULL,
         lock_for_write IN VARCHAR2 DEFAULT NULL);

#### Description

This procedure has three formats:

- The first listed format returns the LOB locator of a raster block by specifying the `pyramidLevel`, `bandBlockNumber`, `rowBlockNumber`, and `columnBlockNumber` parameters.

- The second and third listed formats return the LOB locator of a raster block that contains a specific single cell and the offset of the cell within the raster block. The specific single cell is identified by the `pyramidLevel`, `rowNumber`, `columnNumber`, and `bandNumber` parameters or by a point geometry parameter (`ptGeom`) in either the cell coordinate space or the model coordinate space.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level of the block.

bandBlockNumber
Band number of the block.

bandNumber
Band number of the cell.

rowBlockNumber
Row number of the block.

rowNumber
Row number of the cell.

columnBlockNumber
Column number of the block.

columnNumber
Column number of the cell.

ptGeom
Point geometry that locates the cell.

layerNumber
Number of the logical layer that contains the cell whose value is to be returned. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band ordinate number plus 1.

offset
Output parameter to contain the offset (in bytes) of the cell inside the raster block that is located. If the raster block is compressed, it always refers to the offset of the cell in the decompressed version of the block.

loc
LOB locator.

isBitmapMask
The string `TRUE` specifies that a bitmap mask block will be accessed; the string `FALSE` specifies that a regular raster block will be accessed. If you do not specify this parameter, a regular raster block will be accessed. For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

lockForWrite
The string `TRUE` locks the row in the raster data table so that other users cannot lock or update that row until the current transaction ends; the string `FALSE` does not lock the row in the raster data table. If you do not specify this parameter, the row is not locked.

#### Usage Notes

This procedure gets the raster block locator (and for some formats, the offset) using the specified parameters. The LOB locator is not opened, and no data is read or processed. You should use standard LOB operations to open and close the LOB locator and to read data from and write data to the LOB locator.

To ensure that data is read or written correctly, you must understand the physical storage of the raster data (described in [GeoRaster Physical Storage](georaster-overview-and-concepts.md)), and you must compress and decompress the raster data as needed.

For information about LOB locators, see [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md).

#### Examples

The following example gets the LOB locators of two raster blocks, the first a regular raster block and the second a bitmap mask block. Both calls to the SDO_GEOR.getRasterBlockLocator procedure lock the row in the raster data table.

    DECLARE
      gr sdo_georaster;
      lb blob;
      offset number;
    BEGIN
      select georaster into gr from georaster_table where georid=1;
      sdo_geor.getRasterBlockLocator(gr, 0, 0, 0, 0, offset,lb, null, 'TRUE');
      sdo_geor.getRasterBlockLocator(gr, 0, 0, 0, 0, offset,lb, 'TRUE', 'TRUE');
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.80 SDO_GEOR.getRasterBlocks

#### Format

    SDO_GEOR.getRasterBlocks(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         window       IN SDO_NUMBER_ARRAY
         ) RETURN SDO_RASTERSET;

or

    SDO_GEOR.getRasterBlocks(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         window       IN SDO_GEOMETRY
         ) RETURN SDO_RASTERSET;

#### Description

Returns an object of the SDO_RASTERSET collection type that identifies all blocks of a specified pyramid level that have any spatial interaction with a specified window.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level from which to return the blocks that have any spatial interaction with the specified window.

window
Window from which to return the blocks that are in `pyramidLevel`. The data type can be SDO_NUMBER_ARRAY or SDO_GEOMETRY. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, see the Usage Notes for SDO_SRID requirements.

#### Usage Notes

The SDO_RASTERSET collection type is described in [SDO_RASTERSET Collection Type](georaster-datatypes.md).

If the `window` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `window` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

#### Examples

The following example returns a collection set that identifies all raster blocks that have any spatial interaction with the specified window. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
      ds sdo_rasterset;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=2;
      ds := sdo_geor.getRasterBlocks(gr, 0, sdo_number_array(11,65,192,244));
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.81 SDO_GEOR.getRasterData

#### Format

    SDO_GEOR.getRasterData(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         rasterBlob   IN OUT NOCOPY BLOB,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Creates a single BLOB object that contains all raster data of the input GeoRaster object at the specified pyramid level.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level for which to perform the operation.

rasterBlob
BLOB object to hold the result.

storageParam
A string specifying storage parameters to be applied in creating `rasterBlob`. The only `storageParam` keywords supported for this procedure are `celldepth`, `compression`, `interleaving`, and `quality`; all other keywords are ignored. Storage parameters are explained in [Storage Parameters](georaster-overview-and-concepts.md).

If `storageParam` is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

bgValues
Background values for filling sparse data. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

This parameter is useful when the source has empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). If this parameter is not specified, any cells that are derived from an empty raster block are filled with the value 0 in the output BLOB.

#### Usage Notes

If the GeoRaster object is blocked, the mosaic of all blocks of the specified pyramid level is returned.

After the procedure completes, the `rasterBlob` object contains the cell (pixel) data without tiling.

You can specify compression even if the input GeoRaster object is not compressed or is compressed in a different format from what you specify in the `storageParam` parameter. To have decompressed output for a compressed input GeoRaster object, specify `compression=NONE` in the `storageParam` parameter. For information about GeoRaster compression and decompression, see [Compression and Decompression](georaster-overview-and-concepts.md).

#### Examples

The following example creates a BLOB object, using full-format baseline JPEG (JPEG-F) compression, with all raster data from the GeoRaster object whose ID value is 2 in the GEORASTER_TABLE table. The definition of this table is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    DECLARE
      gr sdo_georaster;
      lb blob;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=2;
      dbms_lob.createTemporary(lb, FALSE);
      sdo_geor.getRasterData(gr, 0, lb, 'compress=JPEG-F');
      dbms_lob.freeTemporary(lb);
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.82 SDO_GEOR.getRasterRange

#### Format

    SDO_GEOR.getRasterRange(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER DEFAULT 0
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Computes and returns the minimum and maximum cell values of a specified layer of a GeoRaster object or of the GeoRaster object itself (the object layer).

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the range of cell values. A value of 0 (zero, the default) indicates the object layer. (As mentioned in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md), the logical layer number is the physical band number plus 1.)

#### Usage Notes

This function goes through all cell values of a specified layer of a GeoRaster object, and returns an SDO_NUMBER_ARRAY object with two values: the minimum and maximum cell values.

If the GeoRaster object already has statistical metadata generated, you can call the SDO_GEOR.getStatistics function to quickly retrieve the minimum and maximum values directly for the raster range.

For information about bands and layers, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md).

#### Examples

The following example computes and returns the raster range for the whole GeoRaster object.

    DECLARE
      gr sdo_georaster;
      range sdo_number_array;
    BEGIN
      select georaster into gr from georaster_table where georid=1;
      range:=sdo_geor.getRasterRange(gr, 0);
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.83 SDO_GEOR.getRasterSubset

#### Format

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         window       IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         inWindow     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         window       IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip  IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         inWindow     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip  IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         inWindow     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         rasterData   IN OUT SDO_NUMBER_ARRAY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         inWindow     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         rasterData   IN OUT SDO_NUMBER_ARRAY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2 DEFAULT NULL,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip  IN VARCHAR2 DEFAULT NULL);

or

    FUNCTION SDO_GEOR.getRasterSubset(
         georaster    IN SDO_GEORASTER,
         pyramidLevel IN NUMBER DEFAULT 0,
         inWindow     IN SDO_GEOMETRY DEFAULT NULL,
         layerNumber  IN NUMBER DEFAULT 1,
         pointPolygon IN NUMBER DEFAULT 1,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip  IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_GEOR_CELL_TABLE PIPELINED;

#### Description

The procedure formats create a single BLOB object or a single SDO_NUMBER_ARRAY object containing all cells of a specified pyramid level that are inside or on the boundary of either a specified rectangular window or polygon geometry object. The function format returns a nested table that holds the cell value, pyramid, row, column, layer, and area or point geometry of all cells inside and touching the specified window.

#### Parameters

georaster
GeoRaster object.

pyramidLevel
Pyramid level on which to perform the operation.

window, inWindow
A rectangular window or a polygon geometry object from which to crop the cells. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY and the `polygonClip` value is `FALSE`, the MBR of the geometry object is used as the window; if the data type is SDO_GEOMETRY and the `polygonClip` value is `TRUE`, the polygon geometry object (if valid) is used as the window. If the data type is SDO_GEOMETRY, see also the Usage Notes for SDO_SRID requirements.

If `window` or `inWindow` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers; if `window` or `inWindow` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers.

layerNumbers
A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4). If you specify a null value for this parameter, the operation or operations are performed on all layers.

layerNumber
For the function format, the layer number on which to perform the operation. The default value is 1.

bandNumbers
A string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3). If you specify a null value for this parameter, the operation or operations are performed on all bands.

rasterBlob
BLOB object to hold the result (the mosaicked raster subset) of the operation. It must exist or have been initialized before the operation.

rasterData
SDO_NUMBER_ARRAY object to hold the result (the mosaicked raster subset) of the operation.

(Note: The upper limit of element numbers in an SDO_NUMBER_ARRAY object is 1048576.)

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

storageParam
A string specifying storage parameters to be applied in creating `rasterBlob`. The only supported `storageParam` keywords supported for this procedure are `celldepth`, `compression`, `interleaving`, and `quality`; all other keywords are ignored. Storage parameters are explained in [Storage Parameters](georaster-overview-and-concepts.md).

If `storageParam` is null or not specified, the cell depth, interleaving, and compression type (and compression quality, if applicable) are the same as for the input GeoRaster object.

pointPolygon
If 0, the function returns a boundary polygon geometry for each cell; if 1 (the default), the function returns the central point geometry for each cell.

bgValues
Background values for filling sparse data. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). If this parameter is not specified, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB.

polygonClip
The string `TRUE` causes the `window` or `inWindow` geometry object to be used for the subset operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the `window` or `inWindow` geometry object to be used for the subset operation.

#### Usage Notes

This subprogram has several procedure formats and a function format. The procedure format to use depends whether the input window is specified as a geometry object or as the upper-left and lower-right corners of a box, whether the result of the operation is a BLOB or SDO_NUMEBR_ARRAY object, and on whether the `outWindow` parameter is used to return the coordinates of the output window.

If the `window` or `inWindow` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `window` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `window` or `inWindow` parameter specifies a geodetic MBR, it cannot cross the date line meridian. For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

After the procedure completes, the `rasterBLOB` parameter contains the cell (pixel) data in the cropped window without tiling. The cropped window is the overlapping portion of the specified window of interest and the source GeoRaster object's spatial extent. If the `outWindow` parameter is specified, after the procedure completes it contains the coordinates of the cropped window in the cell space.

The BLOB has no padding, except when the cell depth is less than 8 bits and the total number of bits needed for the output cannot be divided by 8; in these cases, unlike normal padding, only the last byte of the result is padded with 0 (zeros) for the trailing bits.

If `polygonClip` is `TRUE`, and if this procedure creates a rectangular image subset but the geometry is not a rectangle, check the validity of the `inWindow` geometry object with the function SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT. For an invalid geometry, this procedure operates as if the `polygonClip` value is `FALSE` or a null value.

You can specify compression even if the input GeoRaster object is not compressed or is compressed in a different format from what you specify in the `storageParam` parameter. To have decompressed output for a compressed input GeoRaster object, specify `compression=NONE` in the `storageParam` parameter. For information about GeoRaster compression and decompression, see [Compression and Decompression](georaster-overview-and-concepts.md).

If you want to get a subset and reproject it to another coordinate system, do not use this procedure, but instead use the SDO_GEOR.rectify or SDO_GEOR.reproject procedure using a format that includes the `rasterBlob` parameter, so that this BLOB holds the desired subset.

The SDO_GEOR_CELL_TABLE type for the result of the function format has the following definition:

    SDO_GEOR_CELL_TABLE TABLE OF MDSYS.SDO_GEOR_CELL
    Name                           Null?     Type
    ------------------------------ --------  ----------------------------
    VALUE                                    NUMBER
    PYRAMIDLEVEL                             NUMBER
    ROWNUMBER                                NUMBER
    COLNUMBER                                NUMBER
    LAYERNUMBER                              NUMBER
    GEOM                                     MDSYS.SDO_GEOMETRY

#### Examples

The following two examples retrieve raster data of a specified pyramid level inside a specified window into a BLOB object and an SDO_NUMBER_ARRAY object. (They refer to the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
      lb blob;
      win sdo_number_array;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=4;
      dbms_lob.createTemporary(lb, TRUE);
      win := sdo_number_array(-21,100,100,200);
      sdo_geor.getRasterSubset(gr, 0, win, null, lb);
      dbms_lob.freeTemporary(lb);
    END;
    /

    DECLARE
      gr sdo_georaster;
      data sdo_number_array;
      win sdo_number_array;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=4;
      win := sdo_number_array(-21,100,100,200);
      sdo_geor.getRasterSubset(gr, 0, win, null, data);
    END;
    /

The following example demonstrates how to get the window for the cropping.

    DECLARE
      gr sdo_georaster;
      lb blob;
      win1 sdo_geometry;
      win2 sdo_number_array;
    BEGIN
      SELECT georaster INTO gr FROM georaster_table WHERE georid=4;
      dbms_lob.createTemporary(lb, TRUE);
      win1 := sdo_geometry(2003,82263,null,sdo_elem_info_array(1,1003,3),
                           sdo_ordinate_array(1828466,646447,1823400,642512));
      sdo_geor.getRasterSubset(gr, 0, win1, '1-3', lb, win2, 'compression=NONE');
      dbms_lob.freeTemporary(lb);
      IF win2 IS NOT NULL THEN
        dbms_output.put_line('output window: (' || win2(1) || ',' ||
                              win2(2) || ',' || win2(3) || ',' || win2(4) || ')');
      END IF;
    END;
    /

The following example demonstrates how to do clipping while querying a subset using a polygon.

    DECLARE
      gr sdo_georaster;
      lb blob;
      win1 sdo_geometry;
      win2 sdo_number_array;
    BEGIN
      dbms_lob.createTemporary(lb, TRUE);
      SELECT georaster INTO gr FROM rstpoly_table WHERE georid=1;
      -- querying/clipping polygon
      win1 := sdo_geometry(2003, 26986, null, sdo_elem_info_array(1,1003,1),
                    sdo_ordinate_array(237040,   897924,
                                       237013.3, 897831.6,
                                       237129,   897840,
                                       237182.5, 897785.5,
                                       237239.9, 897902.7,
                                       237223,   897954,
                                       237133,   897899,
                                       237040,   897924));
      sdo_geor.getRasterSubset(gr, 0, win1, '1-3',
                               lb, win2, NULL, NULL, 'TRUE');
      -- Then work on the resulting subset stored in lb.
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.84 SDO_GEOR.getScaling

#### Format

    SDO_GEOR.getScaling(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the coefficients of the scaling function for a layer of a GeoRaster object.

**Note:**

GeoRaster does not perform operations using the scaling function in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the coefficients. A value of 0 (zero) indicates the object layer.

#### Usage Notes

The scaling function is as follows:

    value = (a0 + a1 * cellvalue) / (b0 + b1 * cellvalue)

The order of the coefficients is: a<sub>0</sub>, a<sub>1</sub>, b<sub>0</sub>, b<sub>1</sub>.

#### Examples

The following example returns the scaling coefficients for layer number 0 (the whole object) of a specified GeoRaster object in a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). It scales original value range 0.0 to 1000.0 to be in the range 0.0 to 250.0.

    SELECT sdo_geor.getScaling(georaster, 0) FROM georaster_table WHERE georid=0;

    SDO_GEOR.GETSCALING(GEORASTER,0)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(0.0, 0.25, 1, 0.0)

**Parent topic:** SDO_GEOR Package Reference

### 7.85 SDO_GEOR.getSourceInfo

#### Format

    SDO_GEOR.getSourceInfo(
         georaster   IN OUT SDO_GEORASTER,
         ) RETURN SDO_STRING2_ARRAY;

#### Description

Gets the source information for a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns the source information stored in the `<sourceInfo>` element in the metadata for the GeoRaster object (described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md)).

The SDO_STRING2_ARRAY type is defined as `VARRAY(2147483647) OF VARCHAR2(4096)`.

To replace or delete source information, use the SDO_GEOR.setSourceInfo procedure. To add source information, use the SDO_GEOR.addSourceInfo procedure.

#### Examples

The following example sets and adds some source information for a specified GeoRaster object, and then retrieves the information.

    declare
     gr sdo_georaster;
    begin
     select georaster into gr from georaster_table where georid=1 for update;
     sdo_geor.setSourceInfo(gr, 'Copyright (c) 2002, 2007, Oracle Corporation.');
     sdo_geor.addSourceInfo(gr, 'All rights reserved.');
     update georaster_table set georaster=gr where georid=1;
    end;
    /

    select * from table(select sdo_geor.getSourceInfo(georaster) from georaster_table where id=1);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    Copyright (c) 2002, 2007, Oracle Corporation.
    All rights reserved.

**Parent topic:** SDO_GEOR Package Reference

### 7.86 SDO_GEOR.getSpatialDimNumber

#### Format

    SDO_GEOR.getSpatialDimNumber(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the number of spatial dimensions of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

For the current release, this function always returns 2.

To return the number of cells in each spatial dimension of a GeoRaster object, use the SDO_GEOR.getSpatialDimSizes function.

#### Examples

The following example returns the GEORID column value, the number of spatial dimensions, and the number of cells in each spatial dimension for the GeoRaster objects in the table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). (The output is reformatted for readability.)

    SELECT georid, sdo_geor.getSpatialDimNumber(georaster) spatialDim,
               sdo_geor.getSpatialDimSizes(georaster) spatialDimSizes
       FROM georaster_table;

        GEORID SPATIALDIM SPATIALDIMSIZES
    ---------- ---------- --------------------------------------------------------
             0          2 SDO_NUMBER_ARRAY(1024, 1024)

             1          2 SDO_NUMBER_ARRAY(384, 251)

             2          2 SDO_NUMBER_ARRAY(512, 512)

             4          2 SDO_NUMBER_ARRAY(512, 512)

            11          2 SDO_NUMBER_ARRAY(7957, 5828)

**Parent topic:** SDO_GEOR Package Reference

### 7.87 SDO_GEOR.getSpatialDimSizes

#### Format

    SDO_GEOR.getSpatialDimSizes(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the number of cells in each spatial dimension of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

To return the number of spatial dimensions for a GeoRaster object, use the SDO_GEOR.getSpatialDimNumber function.

#### Examples

The following example returns the spatial dimension sizes and the number of bands for a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT sdo_geor.getSpatialDimSizes(georaster) spatialDimSizes,
           sdo_geor.getBandDimSize(georaster) bandDimSize
      FROM georaster_table WHERE georid=21;

    SPATIALDIMSIZES                  BANDDIMSIZE
    --------------------------       -----------
    SDO_NUMBER_ARRAY(512, 512)           1

**Parent topic:** SDO_GEOR Package Reference

### 7.88 SDO_GEOR.getSpatialResolutions

#### Format

    SDO_GEOR.getSpatialResolutions(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the spatial resolution value along each spatial dimension of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

Each value indicates the number of units of measurement associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measurement for the ground data is meters, each pixel represents an area of 10 meters by 10 meters.

The spatial resolutions may be inconsistent with the georeferencing information, especially when the GeoRaster object is not georectified. You can use the SDO_GEOR.setSpatialResolutions procedure to set the spatial resolutions to be the average resolutions for an image or the resolutions when the data was collected. In this case, georeferencing information should be used for precise measurement.

#### Examples

The following example returns the spatial resolution values along the column and row (X and Y) dimensions of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getSpatialResolutions(georaster) spatialResolution
      FROM georaster_table WHERE georid=42;

    SPATIALRESOLUTION
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(28.5, 28.5)

**Parent topic:** SDO_GEOR Package Reference

### 7.89 SDO_GEOR.getSpectralResolution

#### Format

    SDO_GEOR.getSpectralResolution(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the spectral resolution of a GeoRaster object if it is a hyperspectral or multiband image.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

Taken together, the spectral unit and spectral resolution identify the wavelength interval for a band. For example, if the spectral resolution value is 2 and the spectral unit value is `MILLIMETER`, the wavelength interval for a band is 2 millimeters.

To set the spectral resolution for a GeoRaster object, use the SDO_GEOR.setSpectralResolution procedure.

#### Examples

The following example returns the spectral unit and spectral resolution for all spatially referenced GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, substr(sdo_geor.getSpectralUnit(georaster),1,20) spectralUnit,
                   sdo_geor.getSpectralResolution(georaster) spectralResolution
      FROM georaster_table
     WHERE sdo_geor.isSpatialReferenced(georaster)='TRUE';

        GEORID SPECTRALUNIT         SPECTRALRESOLUTION
    ---------- -------------------- ------------------
             4 MILLIMETER                        0.075

**Parent topic:** SDO_GEOR Package Reference

### 7.90 SDO_GEOR.getSpectralUnit

#### Format

    SDO_GEOR.getSpectralUnit(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the unit of measurement for identifying the wavelength interval for a band.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function can return one of the following values: `METER`, `MILLIMETER`, `MICROMETER`, `NANOMETER`.

Taken together, the spectral unit and spectral resolution identify the wavelength interval for a band. For example, if the spectral resolution value is 2 and the spectral unit value is `MILLIMETER`, the wavelength interval for a band is 2 millimeters.

To set the spectral unit for a GeoRaster object, use the SDO_GEOR.setSpectralUnit procedure.

#### Examples

The following example returns the spectral unit and spectral resolution for all spatially referenced GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, substr(sdo_geor.getSpectralUnit(georaster),1,20) spectralUnit,
                   sdo_geor.getSpectralResolution(georaster) spectralResolution
      FROM georaster_table
     WHERE sdo_geor.isSpatialReferenced(georaster)='TRUE';

        GEORID SPECTRALUNIT         SPECTRALRESOLUTION
    ---------- -------------------- ------------------
             4 MILLIMETER                        0.075

**Parent topic:** SDO_GEOR Package Reference

### 7.91 SDO_GEOR.getSRS

#### Format

    SDO_GEOR.getSRS(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_GEOR_SRS;

#### Description

Returns an object of type SDO_GEOR_SRS containing information related to the spatial referencing of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The SDO_GEOR_SRS object type is described in [SDO_GEOR_SRS Object Type](georaster-datatypes.md).

#### Examples

The following example returns information related to the spatial referencing of all spatially referenced GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getSRS(georaster) SRS
      FROM georaster_table
      WHERE sdo_geor.isSpatialReferenced(georaster)='TRUE';

        GEORID
    ----------
    SRS(ISREFERENCED, ISRECTIFIED, ISORTHORECTIFIED, SRID, SPATIALRESOLUTION, SPATIA
    --------------------------------------------------------------------------------
             4
    SDO_GEOR_SRS('TRUE', 'TRUE', NULL, 82262, SDO_NUMBER_ARRAY(28.5, 28.5), NULL, NU
    LL, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, NULL, NULL, NULL, SDO_NUMBER_ARRAY(1, 2, 1, 3,
     32631.5614, 0, -.03508772), SDO_NUMBER_ARRAY(1, 0, 0, 1, 1), SDO_NUMBER_ARRAY(1
    , 2, 1, 3, -7894.7544, .035087719, 0), SDO_NUMBER_ARRAY(1, 0, 0, 1, 1) , NULL,
    NULL, NULL, NULL, NULL)

**Parent topic:** SDO_GEOR Package Reference

### 7.92 SDO_GEOR.getStatistics

#### Format

    SDO_GEOR.getStatistics(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns statistical data associated with a layer.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the statistics. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns statistical data described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The function returns an array with the following values: `MIN`, `MAX`, `MEAN`, `MEDIAN`, `MODEVALUE`, and `STD`.

To set the statistical data associated with a layer, use the SDO_GEOR.setStatistics procedure.

#### Examples

The following example returns statistical data for layer 1 of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getStatistics(georaster, 1) layer1
    FROM georaster_table WHERE georid=4;

    LAYER1
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(0, 255, 100, 127, 95, 25)

**Parent topic:** SDO_GEOR Package Reference

### 7.93 SDO_GEOR.getTotalLayerNumber

#### Format

    SDO_GEOR.getTotalLayerNumber(
         georaster  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the total number of layers in a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

For information about layers, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md).

#### Examples

The following example returns the total number of layers in each GeoRaster object (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    SELECT georid, sdo_geor.getTotalLayerNumber(georaster) totalLayerNumber
      FROM georaster_table;

        GEORID TOTALLAYERNUMBER
    ---------- ----------------
             2                1
             4                3

**Parent topic:** SDO_GEOR Package Reference

### 7.94 SDO_GEOR.getULTCoordinate

#### Format

    SDO_GEOR.getULTCoordinate(
         georaster  IN SDO_GEORASTER
         ) RETURN SDO_NUMBER_ARRAY ;

#### Description

Returns the cell coordinates of the upper-left corner of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns two or three numbers. If it returns two numbers, they are row and column ordinates. If it returns three numbers, they are row, column, and band ordinates.

#### Examples

The following example returns the row, column, and band ordinates for the upper-left corner of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT sdo_geor.getULTCoordinate(georaster) FROM georaster_table WHERE georid=23;

    SDO_GEOR.GETULTCOORDINATE(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(256, 0, 0)

**Parent topic:** SDO_GEOR Package Reference

### 7.95 SDO_GEOR.getVAT

#### Format

    SDO_GEOR.getVAT(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the name of the value attribute table (VAT) associated with a layer of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the VAT. A value of 0 (zero) indicates the object layer.

#### Usage Notes

For more information about value attribute tables, see [Geographic Information Systems](georaster-overview-and-concepts.md).

To set the name of the value attribute table to be associated with a layer of a GeoRaster object, use the SDO_GEOR.setVAT procedure.

#### Examples

The following example returns the value attribute tables for layers 0, 1, 2, and 3 of the GeoRaster objects (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The output is reformatted for readability.)

    SELECT substr(sdo_geor.getVAT(georaster, 0),1,20) vatTable0,
           substr(sdo_geor.getVAT(georaster, 1),1,20) vatTable1,
           substr(sdo_geor.getVAT(georaster, 2),1,20) vatTable2,
           substr(sdo_geor.getVAT(georaster, 3),1,20) vatTable3
      FROM georaster_table WHERE georid=4;

    VATTABLE0            VATTABLE1            VATTABLE2            VATTABLE3
    -------------------- -------------------- -------------------- ----------------
    VAT0                 VAT1                 VAT2                 VAT1

**Parent topic:** SDO_GEOR Package Reference

### 7.96 SDO_GEOR.getVersion

#### Format

    SDO_GEOR.getVersion(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the user-specified version of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The version returned is in the format major-version.minor-version.

To set the user-specified version of a GeoRaster object, use the SDO_GEOR.setVersion procedure.

#### Examples

The following example returns the user-specified version of the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). (The output is reformatted for readability.)

    SELECT georid, sdo_geor.getVersion(georaster) version FROM georaster_table;

        GEORID VERSION
    ---------- --------------------------------------------------------------------
             2  10.1
             4  9i.2

**Parent topic:** SDO_GEOR Package Reference

### 7.97 SDO_GEOR.hasBitmapMask

#### Format

    SDO_GEOR.hasBitmapMask(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Checks if a GeoRaster object or layer has an associated bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer to check. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the string `TRUE` if the GeoRaster object or layer has an associated bitmap mask, or `FALSE` if it does not have an associated bitmap mask.

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example checks if layers 0 through 4 of a specified GeoRaster object have associated bitmap masks.

    SELECT substr(sdo_geor.hasBitmapMask(georaster,0),1,12) BM0,
           substr(sdo_geor.hasBitmapMask(georaster,1),1,12) BM1,
           substr(sdo_geor.hasBitmapMask(georaster,2),1,12) BM2,
           substr(sdo_geor.hasBitmapMask(georaster,3),1,12) BM3
      FROM georaster_table WHERE georid=0;

**Parent topic:** SDO_GEOR Package Reference

### 7.98 SDO_GEOR.hasGrayScale

#### Format

    SDO_GEOR.hasGrayScale(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Checks if a layer of a GeoRaster object has grayscale information.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer to check. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the string `TRUE` if the layer has grayscale information, or `FALSE` if the layer does not use grayscale representation. [SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md) describes grayscale display.

If the layer has grayscale information, you can get and set the grayscale mappings and the grayscale mapping table name. See the following: SDO_GEOR.getGrayScale and SDO_GEOR.getGrayScaleTable functions, and SDO_GEOR.setGrayScale and SDO_GEOR.setGrayScaleTable procedures.

#### Examples

The following example checks if layers 0 and 1 of a specified GeoRaster object (GEORASTER column) have grayscale information. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT substr(sdo_geor.hasGrayScale(georaster, 0),1,15) hasGrayScale0,
           substr(sdo_geor.hasGrayScale(georaster, 1),1,15) hasGrayScale1
      FROM georaster_table WHERE georid=4;

    HASGRAYSCALE0   HASGRAYSCALE1
    --------------- ---------------
    TRUE            FALSE

**Parent topic:** SDO_GEOR Package Reference

### 7.99 SDO_GEOR.hasNODATAMask

#### Format

    SDO_GEOR.hasNODATAMask(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Checks if a GeoRaster object or layer has an associated NODATA bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer to check. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the string `TRUE` if the GeoRaster object or layer has an associated NODATA bitmap mask, or `FALSE` if it does not have an associated NODATA bitmap mask.

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example checks if layers 0 through 4 of a specified GeoRaster object have associated NODATA bitmap masks.

    SELECT substr(sdo_geor.hasNODATAMask(georaster,0),1,12) BM0,
           substr(sdo_geor.hasNODATAMask(georaster,1),1,12) BM1,
           substr(sdo_geor.hasNODATAMask(georaster,2),1,12) BM2,
           substr(sdo_geor.hasNODATAMask(georaster,3),1,12) BM3
      FROM georaster_table WHERE georid=0;

**Parent topic:** SDO_GEOR Package Reference

### 7.100 SDO_GEOR.hasPseudoColor

#### Format

    SDO_GEOR.hasPseudoColor(
         georaster   IN SDO_GEORASTER,
         layerNumber IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Checks if a layer of a GeoRaster object has pseudocolor information.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer to check. A value of 0 (zero) indicates the object layer.

#### Usage Notes

This function returns the string `TRUE` if the layer has pseudocolor information, or `FALSE` if the layer does not have pseudocolor information (that is, does not use pseudocolor representation). [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md) describes colormaps and pseudocolor display.

If the layer has pseudocolor information, you can get and set the colormap and colormap table name. See the following: SDO_GEOR.getColorMap and SDO_GEOR.getColorMapTable functions, and SDO_GEOR.setColorMap and SDO_GEOR.setColorMapTable procedures.

#### Examples

The following example checks if layers 0 and 1 of a specified GeoRaster object (GEORASTER column) have pseudocolor information. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT substr(sdo_geor.hasPseudoColor(georaster, 0),1,15) hasPseudoColor0,
           substr(sdo_geor.hasPseudoColor(georaster, 1),1,15) hasPseudoColor1
      FROM georaster_table WHERE georid=4;

    HASPSEUDOCOLOR0 HASPSEUDOCOLOR1
    --------------- ---------------
    FALSE           TRUE

**Parent topic:** SDO_GEOR Package Reference

### 7.101 SDO_GEOR.importFrom

#### Format

    SDO_GEOR.importFrom(
         georaster      IN OUT SDO_GEORASTER,
         storageParam   IN VARCHAR2,
         r_sourceFormat IN VARCHAR2,
         r_sourceType   IN VARCHAR2,
         r_sourceName   IN VARCHAR2,
         h_sourceFormat IN VARCHAR2 DEFAULT NULL,
         h_sourceType   IN VARCHAR2 DEFAULT NULL,
         h_sourceName   IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.importFrom(
         georaster      IN OUT SDO_GEORASTER,
         storageParam   IN VARCHAR2,
         r_sourceFormat IN VARCHAR2,
         r_sourceBLOB   IN BLOB,
         h_sourceFormat IN VARCHAR2 DEFAULT NULL,
         h_sourceCLOB   IN CLOB DEFAULT NULL);

#### Description

Imports an image file or BLOB object into a GeoRaster object stored in the database.

#### Parameters

georaster
GeoRaster object to hold the result of the operation.

storageParam
String containing storage parameters. The format and usage are as explained in [Storage Parameters](georaster-overview-and-concepts.md). Currently, the keywords supported for this operation are:

- `blocking`: (See the explanation in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

- `blocksize`: (See the explanation in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

- `compression`: (See the explanation in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).) The default value is `NONE`, which causes the raw data to be loaded without any compression.

- `quality`: (See the explanation in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

- `raster`: `TRUE` (the default) causes the raster image data in a GeoTIFF format file to be loaded along with the georeferencing information; `FALSE` causes only the georeferencing information to be loaded from the GeoTIFF format file, without the raster image data, into an existing GeoRaster object.

- `spatialExtent`: `FALSE` (the default) causes a spatial extent not to be generated; `TRUE` causes a spatial extent to be generated if the SRID is nonzero and matches the SRID of any existing spatial extent index.

r_sourceFormat
Raster source format. Must be one of the following: `TIFF`, `GIF`, `BMP`, or `PNG`. (`JPEG` is not supported for this procedure.)

r_sourceType
Type of source for the import operation. Must be `FILE`.

r_sourceName
Source file name (with full path specification) if `r_sourceType` is `FILE`. If you are using this procedure only to load the world file into an existing GeoRaster object, specify a null value for this parameter.

r_sourceBLOB
Raster source object of type BLOB.

h_sourceFormat
Geoheader source format. Must be `WORLDFILE`.

h_sourceType
Geoheader type of source for the import operation. Must be `FILE`.

h_sourceName
Geoheader source file name (with full path specification) if `h_sourceType` is `FILE`., and optionally an SRID value. To specify the SRID value, add it after the file name, separated by a comma. Example: `'/mypath/mydir/worldfile.tfw,82934'` (UNIX or Linux) or `'C:\mypath\mydir\worldfile.tfw,82934'` (Windows)

h_sourceCLOB
Geoheader source as an object of type CLOB.

#### Usage Notes

**Note:**

This SDO_GEOR.importFrom procedure is not supported in Oracle Autonomous Database both in Serverless and Dedicated deployments.

For information about using this procedure or the GeoRaster loader tool to load raster data, see [Loading Raster Data](georaster-database-creation-management.md).

If you receive an "insufficient memory" error when loading a very large image, see [Reformatting the Source Raster Before Loading](georaster-database-creation-management.md).

When loading an image into a GeoRaster database, you should always specify a block size, and it should generally be 512x512 or larger.

Specify values for the parameters with names that start with r\_ and h\_ only if the raster image and the geoheader are in separate files or objects.

This procedure can load an ESRI world file from a file or from a CLOB object.

This procedure does not support JPEG as a source file format.

This procedure does not support raster data that has a cell depth value of `2BIT` or source multiband raster data with BIL and BSQ interleaving types.

The imported GeoRaster object has the BIP interleaving type.

Before this procedure is called, the calling user and the MDSYS user must have read permission on the files to be imported or the directory that contains the files. The following example (run as user `SYSTEM`) grants read permission on a file to users `HERMAN` and `MDSYS`:

    call dbms_java.grant_permission('HERMAN','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );
    call dbms_java.grant_permission('MDSYS','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );

#### Examples

The following example initializes an empty GeoRaster object into which an external image in TIFF format is to be imported, and then imports the image. The example grants the necessary permissions at the beginning and revokes them at the end.

    connect / as sysdba

    call dbms_java.grant_permission('HERMAN','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );
    call dbms_java.grant_permission('MDSYS','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );

    connect herman/<password>

    DECLARE
       geor SDO_GEORASTER;
    BEGIN
    -- Initialize an empty GeoRaster object into which the external image
    -- is to be imported.
    INSERT INTO georaster_table
       values( 1, 'TIFF', sdo_geor.init('rdt_1') );

    -- Import the TIFF image.
    SELECT georaster INTO geor FROM georaster_table
       WHERE georid = 1 FOR UPDATE;
    sdo_geor.importFrom(geor, 'blocking=OPTIMALPADDING,blocksize=(512,512,3)', 'TIFF', 'file',
       '/mydirectory/myimages/img1.tif');
    UPDATE georaster_table SET georaster = geor WHERE georid = 1;
    COMMIT;
    END;/

    connect / as sysdba

    call dbms_java.revoke_permission('HERMAN','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );
    call dbms_java.revoke_permission('MDSYS','SYS:java.io.FilePermission',
      '/mydirectory/myimages/img1.tif', 'read' );

The following example imports images from a BLOB and an ESRI world file from a CLOB.

    CREATE TABLE blob_table (blob_col BLOB, blobid NUMBER unique, clob_col CLOB);
    INSERT INTO blob_table VALUES (empty_blob(), 1, null);
    INSERT INTO blob_table VALUES (empty_blob(), 2, empty_clob());
    COMMIT;

    DECLARE
      geor1 SDO_GEORASTER;
      lobd1 BLOB;
      lobd2 CLOB;
      fileName VARCHAR2(1024);
      file BFILE;
      wfile BFILE;
      wfname VARCHAR2(1024);
      amt INTEGER;
      amt1 INTEGER;

    BEGIN
    -- Import BLOB into GeoRaster object.
    -- First, if appropriate, load an existing image file into a BLOB object.
    EXECUTE IMMEDIATE 'CREATE DIRECTORY  blob_test_one AS '''/xyz'''';
    fileName := '/parrot.tif';
    file := BFILENAME('BLOB_TEST_ONE', fileName);
    wfname := '/parrot.tfw';
    wfile := BFILENAME('BLOB_TEST_ONE', wfname);
    SELECT clob_col into lobd2 from blob_table WHERE blobid = 2 for update;
    SELECT blob_col into lobd1 from blob_table WHERE blobid = 2 for update;
    dbms_lob.fileopen(file, dbms_lob.file_readonly);
    dbms_lob.fileopen(wfile, dbms_lob.file_readonly);
    amt1 := dbms_lob.getLength(wfile);
    dbms_lob.loadfromfile(lobd1, file, amt);
    dbms_lob.loadfromfile(lobd2, wfile, amt1);
    COMMIT;
    dbms_lob.fileclose(file);
    dbms_lob.fileclose(wfile);

    -- Then, import this BLOB into a GeoRaster object.
    SELECT georaster INTO geor1 from georaster_table WHERE georid = 14 for update;
    sdo_geor.importFrom(geor1,'', 'TIFF', lobd1, 'WORLDFILE', lobd2);
    sdo_geor.setModelSRID(geor1, 82394);
    UPDATE georaster_table SET georaster = geor1 WHERE georid = 14;
    COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.102 SDO_GEOR.init

#### Format

    SDO_GEOR.init(
         rasterDataTable IN VARCHAR2 DEFAULT NULL,
         rasterID        IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEORASTER;

#### Description

Initializes an empty GeoRaster object, which must then be registered n the xxx_SDO_GEOR_SYSDATA views (see the Usage Notes).

#### Parameters

rasterDataTable
Name of the object table of type SDO_RASTER that stores the cell data blocks. Must not contain spaces, period separators, or mixed-case letters in a quoted string; the name is always converted to uppercase when stored in an SDO_GEORASTER object. The RDT should be in the same schema as its associated GeoRaster table. If you do not specify this parameter, GeoRaster generates a unique table name to be used for the raster data table. If you specify this parameter and the table already exists but is not an object table of type SDO_RASTER, an exception is raised.

rasterID
Number that uniquely identifies the blocks of this GeoRaster object in its raster data table. If you do not specify this parameter, a unique sequence number is generated for the ID.

#### Usage Notes

After initializing the empty GeoRaster object and before performing any operations on the object, you must register it in the xxx_SDO_GEOR_SYSDATA views by inserting the empty GeoRaster object into a GeoRaster table. (The xxx_SDO_GEOR_SYSDATA views are described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md). GeoRaster operations are described in [GeoRaster Database Creation and Management](georaster-database-creation-management.md) and [GeoRaster Data Query and Manipulation](georaster-data-manipulation.md).)

This function returns an empty SDO_GEORASTER object with its `rasterDataTable` and `rasterID` attributes set. All other attributes of the SDO_GEORASTER object are null.

This function does not require that the specified raster data table exist. However, the table must exist before any data can be inserted into it, and you must create the table.

If a table has multiple GeoRaster object columns, and if for each column you plan to call the SDO_GEOR.init or SDO_GEOR.createBlank function with identical parameter values that contain a null `rasterDataTable` or `rasterID` parameter value, do not try to use the SDO_GEOR.init or SDO_GEOR.createBlank function on all such columns with a single INSERT or UPDATE statement. For example, assuming a table named LSAT_TABLE containing the columns (`georid NUMBER, type VARCHAR2(32), image_date VARCHAR2(32), image_15m SDO_GEORASTER, image_30m SDO_GEORASTER, image_60m SDO_GEORASTER`), do not use a statement like the following:

    INSERT INTO lsat_table VALUES(1, 'L1G', '2004-02-25',
      sdo_geor.init('RDT_1'), sdo_geor.init('RDT_1'),
      sdo_geor.init('RDT_1'));

Instead, in cases such as this, do either of the following:

- Always specify a rasterID parameter value when calling the function. The following example specifies raster ID values of 1, 2, and 3 for the GeoRaster objects being inserted into the last three columns:

      INSERT INTO lsat_table VALUES(1, 'L1G', '2004-02-25',
        sdo_geor.init('RDT_1', 1), sdo_geor.init('RDT_1', 2),
        sdo_geor.init('RDT_1', 3));

- Use the function with only one GeoRaster object with each INSERT or UPDATE statement. The following example inserts a row initializing one GeoRaster object column and specifying the other two as null, and then updates the row twice to initialize the second and third GeoRaster object columns:

      INSERT INTO lsat_table VALUES(1, 'L1G', '2004-02-25',
        sdo_geor.init('RDT_1'), null, null);
      UPDATE lsat_table SET image_30m = sdo_geor.init('RDT_1')
        WHERE georid = 1;
      UPDATE lsat_table SET image_60m = sdo_geor.init('RDT_1')
        WHERE georid = 1;

#### Examples

The following example inserts an initialized GeoRaster object into the GEORASTER_TABLE table. The raster data table associated with the GeoRaster object is RDT_1. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    INSERT INTO georaster_table (georid, georaster)
      VALUES (1, sdo_geor.init('RDT_1'));

**Parent topic:** SDO_GEOR Package Reference

### 7.103 SDO_GEOR.isBlank

#### Format

    SDO_GEOR.isBlank(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the GeoRaster object is a blank GeoRaster object, or `FALSE` if the GeoRaster object is not a blank GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

In a blank GeoRaster object, all cells have the same cell value.

To change the cell value of an existing blank GeoRaster object, use the SDO_GEOR.setBlankCellValue procedure. To return the cell value of a specified GeoRaster object, use the SDO_GEOR.getBlankCellValue function.

#### Examples

The following example determines whether or not each GeoRaster object in the GEORASTER column of the GEORASTER_TABLE table is a blank GeoRaster object. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT georid, substr(sdo_geor.isBlank(georaster),1,7) isBlank
      FROM georaster_table;

        GEORID ISBLANK
    ---------- -------
             2 FALSE
             4 FALSE

**Parent topic:** SDO_GEOR Package Reference

### 7.104 SDO_GEOR.isOrthoRectified

#### Format

    SDO_GEOR.isOrthoRectified(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the GeoRaster object is identified as orthorectified, or `FALSE` if the GeoRaster object is not identified as orthorectified.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function checks the GeoRaster metadata for the object to see if it is specified as orthorectified. It does not check if the object is actually orthorectified. Users are responsible for validating the GeoRaster object and ensuring that orthorectification is performed.

To specify that a GeoRaster object is orthorectified, use the SDO_GEOR.setOrthoRectified procedure.

#### Examples

The following example checks if the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table are specified as spatially referenced, rectified, and orthorectified. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT georid, substr(sdo_geor.isSpatialReferenced(georaster),1,20)
                 isSpatialReferenced,
               substr(sdo_geor.isRectified(georaster),1,20) isRectified,
               substr(sdo_geor.isOrthoRectified(georaster),1,20) isOrthoRectified
      FROM georaster_table;

        GEORID ISSPATIALREFERENCED  ISRECTIFIED          ISORTHORECTIFIED
    ---------- -------------------- -------------------- --------------------
             2 TRUE                 TRUE                 TRUE
             4 TRUE                 TRUE                 FALSE

**Parent topic:** SDO_GEOR Package Reference

### 7.105 SDO_GEOR.isRectified

#### Format

    SDO_GEOR.isRectified(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the GeoRaster object is identified as rectified, or `FALSE` if the GeoRaster object is not identified as rectified.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function checks the GeoRaster metadata for the object to see if it is specified as rectified. Users are responsible for validating the GeoRaster object and ensuring that rectification is performed.

To specify that a GeoRaster object is rectified, use the SDO_GEOR.setRectified procedure.

#### Examples

The following example checks if the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table are specified as spatially referenced, rectified, and orthorectified. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT georid, substr(sdo_geor.isSpatialReferenced(georaster),1,20)
                 isSpatialReferenced,
               substr(sdo_geor.isRectified(georaster),1,20) isRectified,
               substr(sdo_geor.isOrthoRectified(georaster),1,20) isOrthoRectified
      FROM georaster_table;

        GEORID ISSPATIALREFERENCED  ISRECTIFIED          ISORTHORECTIFIED
    ---------- -------------------- -------------------- --------------------
             2 TRUE                 TRUE                 TRUE
             4 TRUE                 TRUE                 FALSE

**Parent topic:** SDO_GEOR Package Reference

### 7.106 SDO_GEOR.isSpatialReferenced

#### Format

    SDO_GEOR.isSpatialReferenced(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the GeoRaster object is spatially referenced, or `FALSE` if the GeoRaster object is not spatially referenced.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

The GeoRaster object must have been validated.

#### Examples

The following example checks if the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table are specified as spatially referenced, rectified, and orthorectified. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    SELECT georid, substr(sdo_geor.isSpatialReferenced(georaster),1,20)
                 isSpatialReferenced,
               substr(sdo_geor.isRectified(georaster),1,20) isRectified,
               substr(sdo_geor.isOrthoRectified(georaster),1,20) isOrthoRectified
      FROM georaster_table;

        GEORID ISSPATIALREFERENCED  ISRECTIFIED          ISORTHORECTIFIED
    ---------- -------------------- -------------------- --------------------
             2 TRUE                 TRUE                 TRUE
             4 TRUE                 TRUE                 FALSE

The following example searches for all empty and nongeoreferenced GeoRaster objects.

    SELECT georid FROM georaster_table a
       WHERE sdo_geor.isSpatialReferenced(a.georaster) IS NULL OR
             sdo_geor.isSpatialReferenced(a.georaster) = 'FALSE';

**Parent topic:** SDO_GEOR Package Reference

### 7.107 SDO_GEOR.mask

#### Format

    SDO_GEOR.mask(
         inGeoRaster   IN SDO_GEORASTER,
         bandNumbers   IN VARCHAR2,
         mask          IN SDO_GEORASTER,
         storageParam  IN VARCHAR2,
         outGeoraster  IN OUT SDO_GEORASTER,
         zeroMapping   IN NUMBER DEFAULT 0,
         oneMapping    IN NUMBER DEFAULT 1,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Applies a mask to specified layers of an existing (input) GeoRaster object. The mask GeoRaster object and the input GeoRaster object can have the same storage format or different storage formats, and you can specify storage format options for the output GeoRaster object (for example, to change the blocking, cell depth, or interleaving).

For information about how to determine the mask value to use, see the Usage Notes.

#### Parameters

inGeoRaster
The SDO_GEORASTER object on which the mask operation is to be performed to create the new object.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for the second, third, and forth layers).

mask
The SDO_GEORASTER object to be used as a mask on the input GeoRaster object for generating the output GeoRaster object. If this parameter is specified as null, then available attached masks of the input GeoRaster object are applied to the specified layers.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The new SDO_GEORASTER object that reflects the results of the mask operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

If the output GeoRaster object has any existing raster data, it is deleted before the mask operation is performed. The output GeoRaster object is overwritten as a result of this function.

zeroMapping
Value used for mask cell value 0 (zero). The default value is 0.

oneMapping
Value used for mask cell value 1 (one). The default value is 1.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all layers) or the band dimension size (a different filling value for each layer, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first layer with 1, the second layer with 5, and the third layer with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

To determine the mask value to use with the `mask` parameter, apply the following logic:

    If(cellValue_mask==0)
       cellValue_target=cellValue_source * zeroMapping;
    else
       cellValue_target=cellValue_source * oneMapping;

where:

- `cellValue_source` is the cell value of `inGeoraster` at coordinate (x,y).

- `cellValue_target` is the cell value of `outGeoraster` at coordinate (x,y).

- `cellValue_mask` is the cell value of `mask` at coordinate (x,y).

If `inGeoRaster` is null, no operation is performed.

If pyramid data exists for `inGeoRaster`, then the `mask` GeoRaster object must have at least the same number of pyramid levels as `inGeoRaster`.

If `mask` is not null, its dimension (row and column) size must be equal to that of `inGeoRaster`, and `mask` must overlap on `inGeoRaster`. (You can check for overlap using the [SDO_GEOR_RA.isOverlap](sdo-geor-ra-ref.md) function.)

If `mask` is null and if no attached mask is available for the specified layers, then `inGeoRaster` is copied to `outGeoRaster`, which is also modified as specified by any `storageParam` specifications.

Contrast this function with the SDO_GEOR.setBitmapMask function: SDO_GEOR.mask calculates cell values in layers and stores them in the target GeoRaster object, whereas SDO_GEOR.setBitmapMask associates mask data with specified layers of the source GeoRaster object.

An exception is raised if one or more of the following are true:

- `inGeoRaster` is invalid.

- `outGeoRaster` has not been initialized.

- A raster data table for `outGeoRaster` does not exist and `outGeoRaster` is not a blank GeoRaster object.

#### Examples

The following example applies mask GeoRaster object `gr2` to the source GeoRaster object `gr1`. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      gr3 sdo_georaster;
    BEGIN
      select tmimage into gr1 from landsat where id=103;
      select tmimage into gr3 from landsat where id=1015;
      select grobj into gr2 from grtab where id=1;
      SDO_GEOR.mask(gr1,null,gr2,'blocksize=(100,100,3)',gr3,0.1,0.9,null);
      update landsat set tmimage=gr3 where id=1007;
    END;
    /

The following example applies the attached mask of the source GeoRaster object `gr1` to its second layer.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      gr3 sdo_georaster;
    BEGIN
      select tmimage into gr1 from landsat where id=103;
      select tmimage into gr3 from landsat where id=1015;
      gr2:=null;
      SDO_GEOR.mask(gr1,'1',gr2,'blocksize=(100,100,3)',gr3,0.1,0.9,null);
      update landsat set tmimage=gr3 where id=1007;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.108 SDO_GEOR.mergeLayers

#### Format

    SDO_GEOR.mergeLayers(
         targetGeoRaster    IN OUT SDO_GEORASTER,
         sourceGeoRaster    IN SDO_GEORASTER,
         sourceLayerNumbers IN VARCHAR2 DEFAULT NULL,
         bgValues           IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.mergeLayers(
         source1GeoRaster    IN SDO_GEORASTER,
         source1LayerNumbers IN VARCHAR2,
         source2GeoRaster    IN SDO_GEORASTER,
         source2LayerNumbers IN VARCHAR2,
         storageParam        IN VARCHAR2,
         outGeoRaster        IN OUT SDO_GEORASTER,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL,
         pyramidLevel        IN NUMBER DEFAULT NULL);

#### Description

Merges the layers of two GeoRaster objects, either by appending source layers to a target GeoRaster object (first format) or by performing a union operation (second format).

#### Parameters

targetGeoRaster
GeoRaster object to which layers in `sourceGeoRaster` are to be appended. Cannot be the same GeoRaster object as `sourceGeoRaster`. (Be sure to make a copy of this object before calling this procedure.)

sourceGeoRaster
GeoRaster object in which specified layers are to be appended to `targetGeoRaster`.

sourceLayerNumbers
String specifying one or more layer numbers of layers in `sourceGeoRaster` to be appended to `targetGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'1,3-5,7'` for layers 1, 3, 4, 5, and 7.

source1GeoRaster
One GeoRaster object in which specified layers are to be joined in a union operation with layers from `source2GeoRaster` in the output GeoRaster object `outGeoRaster`.

source1LayerNumbers
String specifying one or more layer numbers of layers in `source1GeoRaster` to be joined in a union operation with layers from `source2GeoRaster` in the output GeoRaster object `outGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'1,3-5,7'` for layers 1, 3, 4, 5, and 7.

source2GeoRaster
One GeoRaster object in which specified layers are to be joined in a union operation with layers from `source1GeoRaster` in the output GeoRaster object `outGeoRaster`.

source2LayerNumbers
String specifying one or more layer numbers of layers in `source2GeoRaster` to be joined in a union operation with layers from `source1GeoRaster` in the output GeoRaster object `outGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'1,3-5,7'` for layers 1, 3, 4, 5, and 7.

storageParam
A string specifying storage parameters to be applied in creating `outGeoRaster`. Storage parameters are explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The new SDO_GEORASTER object that reflects the results of the union operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `source1GeoRaster` or source2GeoRaster.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

pyramidLevel
A number specifying the pyramid level at which the source GeoRaster objects are merged. If not specified, pyramid level 0 is used.

#### Usage Notes

**Note:**

Be sure to make a copy of the `targetGeoRaster` object before you call this procedure, because the changes made to this GeoRaster object might not be reversible after the procedure completes.

The resulting GeoRaster object (`georaster` or `outGeoRaster` parameter) must not be the same GeoRaster object as `sourceGeoRaster`, `source1GeoRaster`, or `source2GeoRaster`.

The two GeoRaster objects to be appended or unioned together must have the same spatial dimension sizes and cover the same area. If one of the GeoRaster objects is georeferenced, the other one must also be georeferenced, have the same model SRID and spatial resolutions, and cover the same area in the model space. If neither GeoRaster object is georeferenced, their `ultCoordinates` must be the same.

The two GeoRaster objects to be appended or unioned together need not have the same cell depth. By default, the cell depth of the first source GeoRaster object will be used for the resulting GeoRaster object. To avoid data loss, or change the output cell depth, you can specify a different `cellDepth` in the `storageParam` for the resulting GeoRaster object.

#### Examples

The following example merges specified layers of two GeoRaster objects into a third GeoRaster object, by performing a union operation.

    declare
     gr1 sdo_georaster;
     gr2 sdo_georaster;
     gr3 sdo_georaster;
    begin
     select georaster into gr1 from georaster_table where georid=1;
     select georaster into gr2 from georaster_table where georid=2;
     insert into georaster_table(georid, georaster) values (3, sdo_geor.init('RDT_1'))
        returning georaster into gr3;
     sdo_geor.mergeLayers(gr1, '3', gr2, '2,1', 'blocking=false', gr3);
     update georaster_table set georaster=gr3 where georid=3;
     commit;
    end;
    /

For an example of using SDO_GEOR.mergLayers to append several layers to an existing GeoRaster object, see the example in [Band Merging](image-processing-virtual-mosaic.md).

**Parent topic:** SDO_GEOR Package Reference

### 7.109 SDO_GEOR.mosaic

#### Format

    SDO_GEOR.mosaic(
         georasterTableName  IN VARCHAR2,
         georasterColumnName IN VARCHAR2,
         georaster           IN OUT SDO_GEORASTER,
         storageParam        IN VARCHAR2,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Mosaics a set of source GeoRaster objects that are rectified, are geospatially aligned under the same SRID, and have the same resolution.

#### Parameters

georasterTableName
Name of the table or view containing all source GeoRaster objects.

georasterColumnName
Column of type SDO_GEORASTER in `georasterTableName`.

georaster
GeoRaster object to hold the result of the mosaic operation. Cannot be the same as any GeoRaster object in `georasterColumnName` in `georasterTableName`.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md). If this parameter is null, the resulting GeoRaster object has the same storage parameters (`blockSize`, `cellDepth`, `interleaving`, and `compression`) as the upper-left corner source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the upper-left corner GeoRaster object to be mosaicked.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)), which could happen when the source GeoRaster objects have empty raster blocks or when the source GeoRaster objects do not cover the whole area. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

This procedure has limited mosaicking capabilities, and works well for preprocessed and perfectly aligned source GeoRaster objects only. It does not work on unrectified rasters and does not support parallel processing. For advanced mosaicking capabilities, including parallel processing, use the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure. See [Large-Scale Image Mosaicking](image-processing-virtual-mosaic.md) for more information.

For this procedure, the source GeoRaster objects must be prepared images or raster data so that they can be mosaicked directly. The GeoRaster objects to be mosaicked must:

- Not be a mixture of georeferenced and nongeoreferenced objects. Either all of the objects are georeferenced, or none of the objects is georeferenced.

- Have the same SRID value if the objects are georeferenced, and the georeferencing method must be affine transformation. The affine transformations of the GeoRaster objects must have the same set of coefficients (A, B, D and E) or (b, c, e, f). This means that the images must have the same X resolution and Y resolution (although the X and Y resolutions do not have to be the same), the same rotation angle, and the same skewing factor; in other words, the images must have the same resolutions, and be rotated and skewed in the same way if the images are rotated and skewed.

- Have the same number of layers or bands. There is no restriction on the row and column dimension sizes of the source objects; for example, they do not need to be a power of 2.

- Have the same mapping between band number and layers.

If the GeoRaster objects to be mosaicked are georeferenced, they are co-located according to their georeferencing information. If the GeoRaster objects are not georeferenced, they are co-located according to their ULTCoordinate values. (The ULTCoordinate is explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If applicable, the resulting GeoRaster object takes the spatial reference metadata information from the upper-left corner source GeoRaster object in the model space. It also takes the cell space and any default storage attributes from the upper-left corner source GeoRaster object in the model space.

If the source GeoRaster objects have empty raster blocks or do not cover the whole area, the mosaicked result GeoRaster object may have empty or partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). A result raster block that is not covered by any of the source GeoRaster objects is kept empty. Any partially empty raster blocks are filled with the values specified in the `bgValues` parameter, or with 0 if the `bgValues` parameter is not specified.

If the source GeoRaster objects overlap, data of the overlapping area comes from the source object that covers it and that has the largest `ultCoordinate` in the cell space where all the source objects are co-located.

Any bitmap masks associated with the source GeoRaster objects are not considered, and the `bitmapmask` parameter is ignored if it is specified in the `storageParam` string.

If all source GeoRaster objects are blank and have the same `blankCellValue` value, the resulting GeoRaster object is blank and has that `blankCellValue` value; otherwise, the resulting GeoRaster object is not blank.

The GeoRaster object to contain the results of the mosaic operation (`georaster` parameter) must not be any of the source GeoRaster objects (the objects on which the mosaic operation is performed).

The mosaic operation performs internal commit operations at regular intervals, and thus it cannot be rolled back. If the operation is interrupted, dangling raster blocks may exist in the raster data table. You can handle dangling raster blocks by maintaining GeoRaster objects and system data in the database, as explained in [Maintaining GeoRaster Objects and System Data in the Database](georaster-database-creation-management.md).

#### Examples

The following example inserts an initialized GeoRaster object into the GEORASTER_TABLE table, returns the GeoRaster object into a variable named `gr`, mosaics all the GeoRaster objects in the GROBJ column of a table named GRTAB, and stores the resulting mosaicked GeoRaster object in the same variable. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md). The GRTAB table definition is not important to the example and is not presented here.)

    DECLARE
      gr sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
          VALUES (12, sdo_geor.init('rdt_1'))
          RETURNING georaster INTO gr;
      sdo_geor.mosaic('grtab', 'grobj', gr, 'blocking=optimalpadding blocksize=(512,512,1)');
      UPDATE georaster_table SET georaster=gr WHERE id=12;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.110 SDO_GEOR.rectify

#### Format

    SDO_GEOR.rectify(
         inGeoRaster      IN SDO_GEORASTER,
         pyramidLevel     IN NUMBER,
         elevationParam   IN VARCHAR2,
         DEM              IN SDO_GEORASTER,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         referencePoint   IN SDO_GEOMETRY,
         resampleParam    IN VARCHAR2,
         storageParam     IN VARCHAR2,
         outGeoRaster     IN OUT SDO_GEORASTER,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.rectify(
         inGeoRaster      IN SDO_GEORASTER,
         pyramidLevel     IN NUMBER,
         elevationParam   IN VARCHAR2,
         DEM              IN SDO_GEORASTER,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         referencePoint   IN SDO_GEOMETRY,
         resampleParam    IN VARCHAR2,
         storageParam     IN VARCHAR2,
         rasterBlob       IN OUT NOCOPY BLOB,
         outArea          OUT SDO_GEOMETRY,
         outWindow        OUT SDO_NUMBER_ARRAY,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL);

#### Description

Perform rectification on all or part of a georeferenced GeoRaster object. The resulting object can be a new GeoRaster object (for persistent storage) or a BLOB (for temporary use). If the input model coordinate system (SRID) is three-dimensional, the average elevation or a Digital Elevation Model (DEM) can be used to perform the orthorectification.

#### Parameters

inGeoRaster
GeoRaster object on which to perform the operation. It must be georeferenced (see the SDO_GEOR.georeference subprogram).

pyramidLevel
Pyramid level of the source GeoRaster object for the operation.

- For BLOB output, this parameter is required.

- For SDO_GEORASTER output, if this parameter is null and the `storageParam` `pyramid` value is `FALSE`, only the pyramid level 0 is rectified and the output will have only level 0. If this parameter is null and the `storageParam` `pyramid` value is `TRUE`, all the pyramid levels from the input are rectified.

- If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

elevationParam
A string containing one or more of the elevation parameters `average` (average surface height), `scale` (scale value applied to all `DEM` values), and `offset` (offset applied to all `DEM` values), where the new value is `(value + offset) * scale`. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, `'average=800 scale=3.2808399 offset=10'`). If this parameter is null, 0 is assumed for `average` and `offset`, and 1 is used for `scale`. Any `scale` and `offset` values are ignored if `DEM` is not specified.

The use of the `elevationParam` parameter requires that the input GeoRaster object have a 3D model SRID.

When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if `DEM` is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

**Note:**

For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

DEM
GeoRaster object with a digital elevation model (DEM); used to perform orthorectification, as explained in the Usage Notes. Must have the same SRID as outGeoRaster. The DEM area should cover the entire `outGeoRaster` area, or the `cropArea` if used. The elevation data is assumed to be on the first layer of the `DEM` GeoRaster object. If this parameter is null, the `elevationParam` value is used. For best results, the resolution of the `DEM` GeoRaster object should be close to the resolution of the input GeoRaster object.

The use of the `DEM` parameter requires that the input GeoRaster object have a 3D model SRID.

When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified in the `elevationParam` parameter even if `DEM` is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

outSRID
Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

outModelCoordLoc
A value specifying the model location of the base of the area represented by a cell: `0` for `CENTER` or `1` for `UPPERLEFT`. If null, `CENTER` is used.

cropArea
Crop area definition. If null, no cropping is performed, and `polygonClip` is ignored.

If `polygonClip` is `FALSE`, the MBR of the `cropArea` is used to crop the output image. If `polygonClip` is `TRUE`, the geometry of the `cropArea` is used to crop the output image. Areas outside the crop area are filled with the background value

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of `cropArea` to be used to crop the output image.

layerNumbers
A string identifying the logical layer numbers for the rectification and the output to `outGeoRaster`. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

outResolutions
An array of numeric values, one for each spatial dimension. Each value indicates the number of units of measure associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measure for the ground data is meters, each pixel represents an area of 10 meters by 10 meters. If null, the default is the resolution of the source data at the specified pyramid level.

resolutionUnit
The unit of the `outResolutions` parameter. If `resolutionUnit` is different from the `outGeoRaster` SRID unit, an appropriate conversion is computed (the value of the output resolution is calculated by converting the `outResolutions` value in `resolutionUnit` to the unit of the output SRID) . If `resolutionUnit` is null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name. This parameter is ignored if `outResolutions` is null.

referencePoint
A point of type SDO_GEOMETRY indicating a reference to where the `outGeoRaster` object should be aligned so that the distance between the `referencePoint` and the upper-left corner of the output will have an integer number of pixels.

resampleParam
A comma-separated quoted string of keyword=value pairs for specifying resampling parameters. See the Usage Notes for more information.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`

rasterBlob
BLOB to hold the output reflecting the rectification. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

This procedure has two formats:

- One format generates a GeoRaster object for persistent storage in the database.

- The other format generates a BLOB for temporary storage or immediate use, such as to display data on the screen.

This procedure uses a non-parametric rectification method that takes the georeferencing polynomials from the input GeoRaster object to transform the original image space into the target image space. Therefore, the input GeoRaster object must be georeferenced (see the SDO_GEOR.georeference subprogram).

Orthorectification can be performed if the input GeoRaster object has a 3D model SRID. A digital elevation model (`DEM`) GeoRaster object can be used to improve the accuracy of the orthorectification. If the `DEM` parameter is not specified, the `elevationParam` `average` value is used as the height for the whole target area. If the `elevationParam` `average` value is not specified, it is estimated based on the SRS and DEM information (see [Image Orthorectification](image-processing-virtual-mosaic.md)).

`resampleParam`, if specified, must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the resampling method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

#### Examples

In the following example, the input GeoRaster object is rectified to the same SRID. The input GeoRaster object was georeferenced using GCPs with SRID 32619.

The `layerNumbers` parameter indicates the order of selection of three bands of the seven bands from the input GeoRaster object, producing a three-band output GeoRaster object.

    DECLARE
      gr1   sdo_georaster;
      gr2   sdo_georaster;
    BEGIN
      select raster into gr1 from georaster_table where georid = 1;
      insert into georaster_table values(2, 'Rectified image',
             sdo_geor.init('georaster_rdt')) returning raster into gr2;
      sdo_geor.rectify(inGeoRaster       => gr1,
                       pyramidLevel      => null,
                       elevationParam    => null,
                       dem               => null,
                       outSRID           => null,
                       outModelCoordLoc  => null,
                       cropArea          => null,
                       polygonClip       => null,
                       layerNumbers      => '2,4,5',
                       outResolutions    => null,
                       resolutionUnit    => null,
                       referencePoint    => null,
                       resampleParam     => null,
                       storageParam      => null,
                       outGeoraster      => gr2);
      update georaster_table set georaster = gr2 where georid = 2;
      commit;
    END;

In the following example, the input GeoRaster object was georeferenced using 3D GCPs with SRID 32619, and the function produces an orthorectified GeoRaster with SRID 4326.

- The `dem` parameter specifies the GeoRaster object `gr3` as the digital elevation model for providing height values for each pixel for the orthorectification.

- `resampleParam` specifies the resampling method as `BILINEAR`.

- The `storageParam` parameter specifies the `interleaving` as `BSQ` and the `compression` as `DEFLATE`.

- The specified `outResolutions` value has the same unit of measurement as the output GeoRaster SRID because `resolutionUnit` is null.

- The point geometry specified by `referencePoint` causes the output image upper-left corner to be aligned with that coordinate, with a integer number of pixel (rows and columns resolution) in between them.

<!-- -->

    DECLARE
      gr1   sdo_georaster;
      gr2   sdo_georaster;
      gr3   sdo_georaster;
      pto   sdo_geometry;
    BEGIN
      pto := sdo_geometry(2001, 4326, sdo_point_type(-71.50,42.0, null));
      select raster into gr1 from georaster_table where georid = 1;
      select raster into gr1 from georaster_table where georid = 3;
      insert into georaster_table values(2, 'Rectified image',
             sdo_geor.init('georaster_rdt')) returning raster into gr2;
      sdo_geor.rectify(inGeoRaster       => gr1,
                       pyramidLevel      => 1,
                       elevationParam    => null,
                       dem               => gr3,
                       outSRID           => 4326,
                       outModelCoordLoc  => null,
                       cropArea          => null,
                       polygonClip       => null,
                       layerNumbers      => null,
                       outResolutions    => sdo_number_array(0.0025,0.0025),
                       resolutionUnit    => null,
                       referencePoint    => pto,
                       resampleParam     => 'resampling=BILINEAR',
                       storageParam      => 'interleaving=BSQ compress=DEFLATE',
                       outGeoraster      => gr2);
      update georaster_table set georaster = gr2 where georid = 2;
      commit;
    END;

In the following example, the input GeoRaster object was georeferenced using GCPs with SRID 32619, and the output GeoRaster object is projected to SRID 4326.

- `resampleParam` specifies the resampling method as `CUBIC`.

- The `storageParam` parameter specifies blockSize as (512,512,3). Because `interleaving` is not specified, the interleaving method for `inGeoRaster` is used.

- `outResolutions` and `resolutionUnit` are specified in meters, which is a different unit from `outSRID` 4316. In this case, the SDO_NUMBER_ARRAY values (30,30) are converted to degrees.

- The SDO_GEOMETRY polygon specified for `cropArea` is used to crop the output area to the extents of that polygon; and because `polygonClip` is `TRUE`, the area of the image outside of the polygon is set to background values.

- The model coordinate location of the output object is `UpperLeft` because `outModelCoordLoc` is specified as `1`.

<!-- -->

    DECLARE
      gr1   sdo_georaster;
      gr2   sdo_georaster;
      pol   sdo_geometry;
    BEGIN
      pol := sdo_geometry(2003,4326,NULL,sdo_elem_info_array(1,1003,1),
               sdo_ordinate_array(-70.869495075803073, 42.349420282160885,
                                  -70.468523716196913, 42.813138293441916,
                                  -70.957334345349082, 43.218053058782452,
                                  -71.350984405166344, 42.736563729419181,
                                  -70.869495075803073, 42.349420282160885));
      select raster into gr1 from georaster_table where georid = 1;
      insert into georaster_table values(2, 'Rectified image',
             sdo_geor.init('georaster_rdt')) returning raster into gr2;
      sdo_geor.rectify(inGeoRaster       => gr1,
                       pyramidLevel      => 0,
                       elevationParam    => null,
                       dem               => null,
                       outSRID           => 4326,
                       outModelCoordLoc  => 1,
                       cropArea          => pol,
                       polygonClip       => 'true',
                       layerNumbers      => null,
                       outResolutions    => sdo_number_array(30,30),
                       resolutionUnit    => 'unit=meter',
                       referencePoint    => null,
                       resampleParam     => 'resampling=CUBIC',
                       storageParam      => 'blocking=optimalpadding blockSize=(512,512,3)',
                       outGeoraster      => gr2);
      update georaster_table set georaster = gr2 where georid = 2;
      commit;
    END;

**Parent topic:** SDO_GEOR Package Reference

### 7.111 SDO_GEOR.reproject

#### Format

    SDO_GEOR.reproject(
         inGeoRaster     IN SDO_GEORASTER,
         resampleParam   IN VARCHAR2,
         storageParam    IN VARCHAR2,
         outSRID         IN NUMBER,
         outGeoraster    IN OUT SDO_GEORASTER,
         bgValues        IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.reproject(
         inGeoRaster     IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         cropArea        IN SDO_GEOMETRY,
         layerNumbers    IN VARCHAR2,
         resampleParam   IN VARCHAR2,
         storageParam    IN VARCHAR2,
         outSRID         IN NUMBER,
         outGeoraster    IN OUT SDO_GEORASTER,
         bgValues        IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.reproject(
         inGeoRaster     IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         cropArea        IN SDO_NUMBER_ARRAY,
         bandNumbers     IN VARCHAR2,
         resampleParam   IN VARCHAR2,
         storageParam    IN VARCHAR2,
         outSRID         IN NUMBER,
         outGeoraster    IN OUT SDO_GEORASTER,
         bgValues        IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.reproject(
         inGeoRaster     IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         cropArea        IN SDO_GEOMETRY,
         layerNumbers    IN VARCHAR2,
         resampleParam   IN VARCHAR2,
         storageParam    IN VARCHAR2,
         outSRID         IN NUMBER,
         rasterBlob      IN OUT NOCOPY BLOB,
         outArea         OUT SDO_GEOMETRY,
         outWindow       OUT SDO_NUMBER_ARRAY,
         bgValues        IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.reproject(
         inGeoRaster     IN SDO_GEORASTER,
         pyramidLevel    IN NUMBER,
         cropArea        IN SDO_NUMBER_ARRAY,
         bandNumbers     IN VARCHAR2,
         resampleParam   IN VARCHAR2,
         storageParam    IN VARCHAR2,
         outSRID         IN NUMBER,
         rasterBlob      IN OUT NOCOPY BLOB,
         outArea         OUT SDO_GEOMETRY,
         outWindow       OUT SDO_NUMBER_ARRAY,
         bgValues        IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Reprojects all or part of a GeoRaster object to a different Oracle Spatial and Graph coordinate system (specified by the outSRID parameter). The resulting object can be a new GeoRaster object (for persistent storage) or a BLOB (for temporary use).

#### Parameters

inGeoRaster
The SDO_GEORASTER object on which the reprojection operation is to be performed to create the new object.

pyramidLevel
A number specifying the pyramid level of the source GeoRaster object.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

resampleParam
A string containing the resampling parameters. See the Usage Notes for information about the available keywords and values.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The new SDO_GEORASTER object that reflects the results of the scaling operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

rasterBlob
BLOB to hold the output reflecting the new coordinate system. It must exist or have been initialized before the reprojection operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

This procedure has two general kinds of interfaces:

- The first three formats generate a persistent GeoRaster object for storage in the database.

- The remaining formats generate a BLOB for temporary storage for immediate use, such as to display data on the screen.

`inGeoRaster` should be georeferenced and have a SRID value from the SRID column of the MDSYS.CS_SRS table. `outSRID` should be different from the SRID of `inGeoRaster`. In some cases, the reprojection is inappropriate, such as reprojecting a GeoRaster object in NAD83, Massachusetts Mainland (SRID = 26986) to coordinate system NAD 27, UTM zone 49N (SRID = 2032649). In this case, the reprojection would result in a large distortion and thus is not performed.

`inGeoRaster` and `outGeoRaster` must be different GeoRaster objects. After the operation, the ULT coordinates of the resulting GeoRaster object are set to zero (0).

If the source or destination object has a three-dimensional coordinate system, the height (Z) values are set to zero (0).

If you use the format that includes the `pyramidLevel` parameter and you specify a value greater than zero (0), the reprojection is based on the specified pyramid level of the source GeoRaster object; otherwise, the reprojection is based on the original GeoRaster object (pyramidLevel=0). The output GeoRaster object has no pyramid data.

If the `cropArea` parameter data type is SDO_GEOMETRY, its SDO_SRID value must be a value from the SRID column of the MDSYS.CS_SRS table. If the SDO_SRID values for the `cropArea` parameter geometry and the `inGeoraster` object model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `cropArea` parameter specifies a geodetic MBR, it cannot cross the date line meridian. (For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).) Only the overlapping portion of the specified crop area and the spatial extent of the source GeoRaster object is reprojected.

`resampleParam` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the resampling method is `BILINEAR`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

#### Examples

The following example reprojects a GeoRaster object into the coordinate system defined by SRID 32618. The result is another GeoRaster object.

    DECLARE
       gr1 sdo_georaster;
       gr2 sdo_georaster;
    BEGIN
      SELECT georaster INTO gr1 from georaster_table WHERE georid=10;
      INSERT INTO reproject_table VALUES (21, 'WGS 84 / UTM zone 18N',
                                          SDO_GEOR.init('rdt_5', 21))
      RETURNING georaster INTO gr2;
      sdo_geor.Reproject(gr1, 0, 0, SDO_NUMBER_ARRAY(0, 0, 517, 517),
                                 null, null, 'blocking=optimalpadding, blocksize=(512,512,3),
                                 interleaving=BSQ', 32618, gr2);
       UPDATE georaster_table SET georaster=gr2 WHERE georid=21;
       COMMIT;
    END;
    /

The following example reprojects a GeoRaster object into the coordinate system defined by SRID 32618. The result is temporary BLOB containing data in JPEG-F format.

    DECLARE
       gr1 sdo_georaster;
       lob1 BLOB;
       outArea SDO_Geometry;
       outWindow SDO_NUMBER_ARRAY;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=10;
       dbms_lob.createTemporary(lob1, TRUE);
       sdo_geor.Reproject(gr1, 0, SDO_NUMBER_ARRAY(0, 0, 120, 300),
                                  '0',  null, 'compression = JPEG-F', 32618,
                                  lob1, outArea, outWindow);

       dbms_lob.freeTemporary(lob1);
       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.112 SDO_GEOR.scaleCopy

#### Format

    SDO_GEOR.scaleCopy(
         inGeoRaster    IN SDO_GEORASTER,
         scaleParam     IN VARCHAR2,
         resampleParam  IN VARCHAR2,
         storageParam   IN VARCHAR2,
         outGeoRaster   IN OUT SDO_GEORASTER,
         bgValues       IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.scaleCopy(
         inGeoRaster    IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         scaleParam     IN VARCHAR2,
         resampleParam  IN VARCHAR2,
         storageParam   IN VARCHAR2,
         outGeoRaster   IN OUT SDO_GEORASTER,
         bgValues       IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Scales a GeoRaster object by enlarging or reducing the image along row and column dimensions, and puts the result into a new object that reflects the scaling.

#### Parameters

inGeoRaster
The SDO_GEORASTER object on which the scaling operation is to be performed to create the new object (`outGeoRaster`).

pyramidLevel
A number specifying the pyramid level of the source GeoRaster object.

scaleParam
A string specifying a scaling parameter keyword and its associated value. The keyword must be one of the following:

**Note:**

For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

- `scaleFactor`, to reduce or enlarge as a multiple of the original size. This keyword must have a numeric value greater than 0 (zero) (for example, `'scaleFactor=0.75'`). A value of 1.0 will not change the current size; a value less than 1 will reduce the image; a value greater than 1 will enlarge the image. The number of cells along each dimension is the original number multiplied by `scaleFactor`. For example, if the `scaleFactor` value is 2 and the GeoRaster object has X and Y dimensions, the number of cells along each dimension is doubled.

- `maxDimSize`, to specify a size in terms of the maximum number of cells for each dimension. This keyword must have a numeric value for each dimension (for example, `'maxDimSize=(512,512)'`). The aspect ratio is not changed.

- `rowMaxDimSize` and `columnMaxDimSize`, to specify sizes in terms of the maximum number of cells for row and column dimensions. This pair of keywords must have numeric values for each dimension (for example, `'rowMaxDimSize=512,columnMaxDimSize=256'`). The aspect ratio can be changed, and the two keywords must be specified together.

- `rowScaleFactor` and `columnScaleFactor`, to reduce or enlarge as a multiple of the original size. This pair of keywords must have numeric values greater than 0 (zero). A value of 1.0 will not change the current size; a value less than 1 will reduce the image; a value greater than 1 will enlarge the image. The number of cells along row dimension is the original number multiplied by `rowScaleFactor`. The number of cells along column dimension is the original number multiplied by `columnScaleFactor`. `rowScaleFactor` and `columnScaleFactor` can be different numbers, but must be specified together.

resampleParam
A string containing the resampling parameters. See the Usage Notes for information about the available keywords and values.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The new SDO_GEORASTER object that reflects the results of the scaling operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

Use this procedure to create a new GeoRaster object reflecting the specified scaling, based on the original GeoRaster object or a specified pyramid level of the GeoRaster object. After you use this procedure, you can check to ensure that the desired changes were made in the copy of the original GeoRaster object, and then discard the original GeoRaster object if you wish.

If you use the format that does not include the `pyramidLevel` parameter, the scaling is based on the original GeoRaster object (pyramidLevel=0).

If you need to get the scaled cell values, use the procedure described in the Usage Notes for the SDO_GEOR.getCellValue function.

`inGeoRaster` and `outGeoRaster` must be different GeoRaster objects.

`resampleParam` must be a quoted string that contains one or more of the following keywords, each with an appropriate value:

- `resampling` (for example, `resampling=NN`): Specifies the resampling method. Must be one of the following: `NN`, `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).

- `nodata` (for example, `nodata=TRUE`): Specifies whether NODATA values and value ranges should be considered during the procedure. Must be either `TRUE` (NODATA values and value ranges should be considered) or `FALSE` (NODATA values and value ranges should not be considered). The default value is `FALSE`. If the value is `TRUE` and the resampling method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, whenever a cell value involved in the resampling calculation is a NODATA value, the result of the resampling is also a NODATA value. The resulting NODATA value is the minimum NODATA value associated with the current raster layer, if multiple NODATA values or value ranges exist.

Any upper-level pyramid data in the input GeoRaster object is not considered during this operation, and the output GeoRaster object has no pyramid data.

After the operation, the row and column ULT coordinates are always set to 0 (zero), even if no scaling is performed (that is, even if `scaleFactor=1`).

This procedure does not scale along the band dimension.

If the source GeoRaster object is georeferenced with a valid polynomial transformation, the georeferencing information for the resulting GeoRaster object is generated accordingly; otherwise, the result GeoRaster object contains no spatial reference information.

An exception is raised if one or more of the following are true:

- `inGeoRaster` is invalid.

- `outGeoRaster` has not been initialized.

- A raster data table for `outGeoRaster` does not exist and `outGeoRaster` is not a blank GeoRaster object.

#### Examples

The following example reduces an image to three-fourths (0.75) size, specifies `AVERAGE4` resampling, and specifies an optimized block size around 512 for each dimension in the storage parameters. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (21, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=2;

      sdo_geor.scaleCopy(gr1, 'scaleFactor=0.75', 'resampling=AVERAGE4',
                         'blocking=optimalpadding blocksize=(512,512)', gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=21;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.113 SDO_GEOR.schemaValidate

#### Format

    SDO_GEOR.schemaValidate(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Validates a GeoRaster object's metadata against the GeoRaster XML schema.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function returns the string `TRUE` if the metadata is valid, a null value if the GeoRaster object or its metadata is null, or one or more Oracle error codes indicating why the metadata is not valid and the exact location of the errors.

Use this function with the SDO_GEOR.validateGeoRaster function. If the SDO_GEOR.validateGeoRaster function identifies a GeoRaster object as invalid with an error code of 13454, the object's metadata is not valid according to the GeoRaster XML schema. If this happens, call the SDO_GEOR.schemaValidate function to get specific information, including the location in the metadata, about the errors.

#### Examples

The following example validates a GeoRaster object's metadata.

    SELECT t.georid,
           sdo_geor.schemavalidate(t.georaster)
      FROM georaster_table t
      WHERE t.georid = 1;

**Parent topic:** SDO_GEOR Package Reference

### 7.114 SDO_GEOR.setBeginDateTime

#### Format

    SDO_GEOR.setBeginDateTime(
         georaster  IN OUT SDO_GEORASTER,
         beginTime  TIMESTAMP WITH TIME ZONE);

#### Description

Sets the beginning date and time for raster data collection in the metadata for a GeoRaster object, or deletes the existing value if you specify a null `beginTime` parameter.

#### Parameters

georaster
GeoRaster object.

beginTime
Time specification.

#### Usage Notes

To see the current beginning date and time (if any) in the metadata for the GeoRaster object, use the SDO_GEOR.getBeginDateTime function.

An exception is raised if `beginTime` is later than the ending date and time specified in the metadata for the GeoRaster object (see the SDO_GEOR.setEndDateTime procedure).

The GeoRaster object is automatically validated after the operation completes.

#### Examples

The following example sets the beginning and ending dates and times for raster data collection in the metadata for a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setBeginDateTime(grobj, timestamp '2002-11-15 15:00:00');
      sdo_geor.setEndDateTime(grobj, timestamp '2002-11-15 15:00:10');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.115 SDO_GEOR.setBinFunction

#### Format

    SDO_GEOR.setBinFunction(
         georaster    IN SDO_GEORASTER,
         layerNumber  IN NUMBER
         binFunction  IN SDO_NUMBER_ARRAY);

#### Description

Sets the bin function associated with a layer.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to return the bin type. A value of 0 (zero) indicates the object layer.

binFunction
Bin function as an array whose elements specify the bin type, total number of bins, first bin number, minimum cell value, and maximum cell value. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`. See the Usage Notes for more information and an example.

#### Usage Notes

A bin function maps values or value ranges of the GeoRaster cells to specific bin numbers, which are all integers. If a bin function of type `LINEAR` is defined, it is used by the SDO_GEOR.generateStatistics function for calculating statistics on cell values. GeoRaster does not provide interfaces to manipulate and process bin functions.

The `binFunction` parameter specifies an array of five numbers, which have the following meaning:

- The first number identifies the bin type, and must be 0 (`LINEAR`) or 1 (`LOGARIGHM`).

- The second number identifies the total number of bins.

- The third number identifies the number of the first bin.

- The fourth number is the minimum cell value in the range.

- The fifth number is the maximum cell value in the range.

For example, if `binFunction` is `SDO_NUMBER_ARRAY(0,10,1,0,511)`, the bin type is `LINEAR`, there are 10 bins numbered 1 through 10 (that is, starting at 1), and cell values from 0 through 511 are uniformly distributed to bins 1 through 10.

An exception is raised if `layerNumber` is null, negative, or greater than the maximum layer number.

#### Examples

The following example sets the bin function for layer 3 of a specified GeoRaster object, using the `binFunction` parameter value explained in the Usage Notes.

    DECLARE
     gr sdo_georaster;
    BEGIN
     SELECT georaster INTO gr FROM georaster_table WHERE georid=4 FOR UPDATE;
     sdo_geor.setBinFunction(gr, 3, sdo_number_array(0,10,1,0,511));
     UPDATE georaster_table SET georaster=gr WHERE georid=4;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.116 SDO_GEOR.setBinTable

#### Format

    SDO_GEOR.setBinTable(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         tableName    IN VARCHAR2);

#### Description

Sets the name of the bin table associated with a layer, or deletes the existing value if you specify a null `tableName` parameter.

**Note:**

GeoRaster does not perform operations using the bin table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to set the bin table name. A value of 0 (zero) indicates the object layer.

tableName
Name of the bin table associated with a layer.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

This procedure is relevant only if the bin type is `EXPLICIT`. To retrieve the bin type, use the SDO_GEOR.getBinType function.

To return the bin table for a layer, use the SDO_GEOR.getBinTable function.

See also the information in the Usage Notes for the SDO_GEOR.getBinType function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `tableName` is an empty string (`''`).

#### Examples

The following example sets `BINT1` as the name of the bin table for layer number 3 of a specified GeoRaster object in the GEORASTER_TABLE table, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setBinTable(grobj, 3, 'BINT1');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.117 SDO_GEOR.setBitmapMask

#### Format

    SDO_GEOR.setBitmapMask(
         georaster   IN OUT SDO_GEORASTER,
         layerNumber IN NUMBER,
         mask        IN SDO_GEORASTER,
         NODATAMask  IN VARCHAR2 DEFAULT NULL);

#### Description

Attaches a bitmap mask to a GeoRaster object, or replaces or removes the current bitmap mask.

#### Parameters

georaster
GeoRaster object.

layerNumber
Layer with which to associate the bitmap mask. A value of 0 (zero) indicates the object layer.

mask
The bitmap mask to be attached to the GeoRaster object. If this parameter is null, any existing bitmap mask associated with the specified layer of the GeoRaster object is removed.

NODATAMask
Specifies whether `mask` is to be interpreted as a NODATA mask. The string `TRUE` causes `mask` to be interpreted as a NODATA mask; any other value (including null) causes `mask` not to be interpreted as a NODATA mask.

#### Usage Notes

If the specified GeoRaster object or layer already has an associated bitmap mask, this procedure replaces it with the specified mask, or removes it if the `mask` parameter specifies a null value.

If the `mask` parameter value is not null, the bitmap mask must be a valid 1BIT GeoRaster object with only one band, and the row and column dimension sizes of the bitmap mask must be the same as those of the target GeoRaster object. It cannot be the same GeoRaster object as the input GeoRaster object (`georaster` parameter).

This procedure raises an exception if the target GeoRaster object is a blank GeoRaster object.

For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Examples

The following example uses a GeoRaster object in the table GRTAB (where id=1) as the bitmap mask to be attached to layer number 1 of an GeoRaster object in the GEORASTER_TABLE (where georid=1). The bitmap mask will be interpreted as a NODATA mask.

    declare
      gr sdo_georaster;
      mk sdo_georaster;
    begin
      select georaster into gr from georaster_table where georid=1 for update;
      select grobj into mk from grtab where id=1;
      sdo_geor.setBitmapMask(gr, 1, mk, 'true');
      update georaster_table set georaster=gr where georid=0;
      commit;
    end;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.118 SDO_GEOR.setBlankCellValue

#### Format

    SDO_GEOR.setBlankCellValue(
         georaster  IN OUT SDO_GEORASTER,
         value      IN NUMBER);

#### Description

Sets (modifies) the cell value to be used for all cells if a specified GeoRaster object is a blank GeoRaster object.

#### Parameters

georaster
GeoRaster object.

value
Cell value to be used for the blank GeoRaster object. Cannot be a null value.

#### Usage Notes

In a blank GeoRaster object, all cells have the same cell value.

The GeoRaster object is automatically validated after the operation completes.

To return the blank cell value of a blank GeoRaster object, use the SDO_GEOR.getBlankCellValue function. To determine if a specified GeoRaster object is a blank GeoRaster object, use the SDO_GEOR.isBlank function.

An exception is raised if `value` is null or inconsistent with the `cellDepth` specification, or if the GeoRaster object is not blank.

#### Examples

The following example specifies a value of 255 to be used for all cells in the GeoRaster object column (GEORASTER) in the GEORASTER_TABLE table for the row with an GEORID column value of 1. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=1 FOR UPDATE;
      sdo_geor.setBlankCellValue(grobj, 255);
      UPDATE georaster_table SET georaster = grobj WHERE georid=1;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.119 SDO_GEOR.setColorMap

#### Format

    SDO_GEOR.setColorMap(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         colorMap     IN SDO_GEOR_COLORMAP);

#### Description

Sets the colormap for a layer in a GeoRaster object, or deletes the existing value if you specify a null `colorMap` parameter.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

colorMap
Colormap object of type SDO_GEOR_COLORMAP, which is described in [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md).

#### Usage Notes

The following must be true of the specified colormap object:

- The `cellValue` values are consistent with and in the value range for the `cellDepth` value of the GeoRaster object.

- The red, green, blue, and alpha values are integers from 0 to 255.

- The `cellValue` array contains no duplicate entries.

- The entries in the `cellValue` array are in ascending order.

The GeoRaster object is automatically validated after the operation completes.

You can create a colormap or retrieve a colormap from an existing GeoRaster object for use. To return the colormap for a layer in a GeoRaster object, use the SDO_GEOR.getColorMap function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if any of the following exist in `colorMap`: the red, green, blue, or alpha value is null or out of scope; duplicate values exist in the `cellValue` array, or any `cellValue` values are null, out of scope, or out of order.

#### Examples

The following example sets the colormap for layer 2 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. It assumes that the GeoRaster object is a bitmap. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
      cmobj sdo_geor_colormap;
    BEGIN
      cmobj := sdo_geor_colormap(sdo_number_array(0, 1),
                                 sdo_number_array(0, 255),
                                 sdo_number_array(0, 0),
                                 sdo_number_array(0, 0),
                                 sdo_number_array(255, 255));

      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setColorMap(grobj, 2, cmobj);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.120 SDO_GEOR.setColorMapTable

#### Format

    SDO_GEOR.setColorMapTable(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         tableName    IN VARCHAR2);

#### Description

Sets the colormap table for a layer in a GeoRaster object, or deletes the existing value if you specify a null `tableName` parameter.

**Note:**

This procedure registers the colormap table name with GeoRaster; however, GeoRaster does not perform operations using the colormap table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

tableName
Name of the user-defined colormap table. [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md) describes colormaps.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

To return the colormap table for a layer in a GeoRaster object, use the SDO_GEOR.getColorMapTable function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `tableName` is an empty string (`''`).

#### Examples

The following example sets the colormap table to be null for layer 2 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setColorMapTable(grobj, 2, null);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.121 SDO_GEOR.setControlPoint

#### Format

    SDO_GEOR.setControlPoint (
         inGeoraster  IN OUT SDO_GEORASTER,
         controlPoint IN SDO_GEOR_GCP);

#### Description

Adds a ground control point (GCP) for the GeoRaster object, or replaces an existing GCP if it has the same ID value as the input control point.

#### Parameters

inGeoraster
GeoRaster object.

controlPoint
GCP to be added for `inGeoraster`. Must be an object of type SDO_GEOR_GCP, which is described in [SDO_GEOR_GCP Object Type](georaster-datatypes.md).

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

If the `controlPoint` is null, the function returns without performing any action. If a GCP is found in the GeoRaster object metadata with the same point ID as defined in `controlPoint`, that GCP is replaced; otherwise, this GCP is added to the georeferencing model.

#### Examples

The following example adds a GCP for a specified GeoRaster object.

    DECLARE
       gr1            sdo_georaster;
       GCP         SDO_GEOR_GCP;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=10 FOR UPDATE;

       GCP := SDO_GEOR_GCP('21', 'Updated', 1,
                           2, sdo_number_array(25.625000, 73.875000),
                           2, sdo_number_array(237036.937500, 897987.187500),
                           NULL, NULL);
       sdo_geor.setControlPoint(gr1, GCP);
       UPDATE georaster_table SET georaster=gr1 WHERE georid=10;
       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.122 SDO_GEOR.setDefaultAlpha

#### Format

    SDO_GEOR.setDefaultAlpha(
         georaster     IN OUT SDO_GEORASTER,
         defaultAlpha  IN NUMBER);

#### Description

Sets the number of the layer to be used for the alpha color component (in the RGBA color space) for displaying a GeoRaster object, or deletes the existing value if you specify a null `defaultAlpha` parameter.

#### Parameters

georaster
GeoRaster object.

defaultAlpha
Number of the layer to be used for the alpha color component (in the RGBA color space) for displaying the specified GeoRaster object. Must be greater than 0 (zero) and less than or equal to the highest layer number in the GeoRaster object.

#### Usage Notes

The default red, green, blue, and alpha values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if you are trying to set the number of the layer to be used for the alpha color component only, or if `defaultAlpha` is not a valid layer number for the GeoRaster object.

#### Examples

The following example sets the default red, green, blue, and alpha color layers for the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, and it returns an array with the layer numbers for the red, green, blue, and alpha color components for displaying these GeoRaster objects. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setDefaultRed(grobj, 5);
      sdo_geor.setDefaultGreen(grobj, 4);
      sdo_geor.setDefaultBlue(grobj, 3);
      sdo_geor.setDefaultAlpha(grobj, 2);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getDefaultColorLayer(georaster) FROM georaster_table
      WHERE georid=4;

    SDO_GEOR.GETDEFAULTCOLORLAYER(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(5, 4, 3, 2)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.123 SDO_GEOR.setDefaultBlue

#### Format

    SDO_GEOR.setDefaultBlue(
         georaster    IN OUT SDO_GEORASTER,
         defaultBlue  IN NUMBER);

#### Description

Sets the number of the layer to be used for the blue color component (in the RGB color space) for displaying a GeoRaster object, or deletes the existing value if you specify a null `defaultBlue` parameter.

#### Parameters

georaster
GeoRaster object.

defaultBlue
Number of the layer to be used for the blue color component (in the RGB color space) for displaying the specified GeoRaster object. Must be greater than 0 (zero) and less than or equal to the highest layer number in the GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if you are trying to set or remove the number of the layer to be used for the blue color component only, or if `defaultBlue` is not a valid layer number for the GeoRaster object.

#### Examples

The following example sets the default red, green, and blue color layers for the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, and it returns an array with the layer numbers for the red, green, and blue color components for displaying these GeoRaster objects. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setDefaultRed(grobj, 5);
      sdo_geor.setDefaultGreen(grobj, 4);
      sdo_geor.setDefaultBlue(grobj, 3);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getDefaultColorLayer(georaster) FROM georaster_table
      WHERE georid=4;

    SDO_GEOR.GETDEFAULTCOLORLAYER(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(5, 4, 3)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.124 SDO_GEOR.setDefaultColorLayer

#### Format

    SDO_GEOR.setDefaultColorLayer(
         georaster   IN OUT SDO_GEORASTER,
         defaultRGB  IN SDO_NUMBER_ARRAY);

#### Description

Sets the default numbers of the layers to be used for the red, green, blue, and alpha color components, respectively, for displaying a GeoRaster object, or deletes the existing values if you specify a null `defaultRGB` parameter.

#### Parameters

georaster
GeoRaster object.

defaultRGB
Array of three or four numbers identifying the red, green, blue, and alpha color components, respectively, for displaying the specified GeoRaster object. Each number must be greater than 0 (zero) and less than or equal to the highest layer number in the GeoRaster object.

#### Usage Notes

The RGBA layer numbers specified are used for true-color displays, not for pseudocolor or grayscale displays.

The GeoRaster object is automatically validated after the operation completes.

You can set the layer number for each color component (RGB) by using the SDO_GEOR.setDefaultRed, SDO_GEOR.setDefaultGreen, SDO_GEOR.setDefaultBlue, and SDO_GEOR.setDefaultAlpha procedures.

The default RGBA layer numbers must be set or removed at the same time. The default alpha layer number is optional. If the default red, green, and blue layer numbers are set, the default alpha layer number can be set. If the default red, green, and blue layer numbers are removed, the default alpha layer number must also be removed.

Because the default alpha layer is optional, you can either (A) set the default red, green, and blue color components only by providing three numbers to this procedure or (B) set the default red, green, blue, and alpha color components by providing four numbers to this procedure. If `defaultRGB` is an array of three numbers, it identifies the red, green and blue color components only. If `defaultRGB` is an array of four numbers, it identifies the red, green, blue, and alpha components.

An exception is raised if `defaultRGB` is of the wrong size or if any elements in it are null or are invalid layer numbers for the GeoRaster object.

#### Examples

The following example specifies that layer number 1 is to be used for the red, green, blue. and alpha color components for displaying the GeoRaster object (GEORASTER column) in the row with an GEORID column value of 2 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=2 FOR UPDATE;
      sdo_geor.setDefaultColorLayer(grobj, sdo_number_array(1,1,1,1));
      UPDATE georaster_table SET georaster = grobj WHERE georid=2;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.125 SDO_GEOR.setDefaultGreen

#### Format

    SDO_GEOR.setDefaultGreen(
         georaster     IN OUT SDO_GEORASTER,
         defaultGreen  IN NUMBER);

#### Description

Sets the number of the layer to be used for the green color component (in the RGB color space) for displaying a GeoRaster object, or deletes the existing value if you specify a null `defaultGreen` parameter.

#### Parameters

georaster
GeoRaster object.

defaultGreen
Number of the layer to be used for the green color component (in the RGB color space) for displaying the specified GeoRaster object. Must be greater than 0 (zero) and less than or equal to the highest layer number in the GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if you are trying to set or remove the number of the layer to be used for the green color component only, or if `defaultGreen` is not a valid layer number for the GeoRaster object.

#### Examples

The following example sets the default red, green, and blue color layers for the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, and it returns an array with the layer numbers for the red, green, and blue color components for displaying these GeoRaster objects. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setDefaultRed(grobj, 5);
      sdo_geor.setDefaultGreen(grobj, 4);
      sdo_geor.setDefaultBlue(grobj, 3);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getDefaultColorLayer(georaster) FROM georaster_table
      WHERE georid=4;

    SDO_GEOR.GETDEFAULTCOLORLAYER(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(5, 4, 3)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.126 SDO_GEOR.setDefaultPyramidLevel

#### Format

    SDO_GEOR.setDefaultPyramidLevel(
         georaster            IN OUT SDO_GEORASTER,
         defaultPyramidLevel  IN NUMBER);

#### Description

Sets the number of the layer to be used for the default pyramid level for displaying a GeoRaster object, or deletes the existing value if you specify a null `defaultPyramidLevel` parameter.

#### Parameters

georaster
GeoRaster object.

defaultPyramidLevel
The default pyramid level for displaying the specified GeoRaster object. Must be greater than or equal to 0 (zero) and less than or equal to the maximum pyramid level in the GeoRaster object.

#### Usage Notes

Pyramid levels represent reduced or increased resolution images that require less or more storage space, respectively. For information about pyramids and pyramid levels, see [Pyramids](georaster-overview-and-concepts.md).

Specifying a default pyramid level is an optional operation, and is intended for use only when visualizing GeoRaster objects with pyramids generated.

The GeoRaster object is automatically validated after the operation completes.

When pyramids are removed from a GeoRaster object by any other operation (such as SDO_GEOR.deletePyramid or SDO_GEOR.subset), the default pyramid level for the object is also removed from the metadata.

An exception is raised if there are no pyramids generated for the GeoRaster object, or if `defaultPyramidLevel` is not a valid pyramid level number for the GeoRaster object.

You can get the default pyramid level by using the SDO_GEOR.getDefaultPyramidLevel function.

#### Examples

The following example generates the pyramids and sets the default pyramid level for a specified GeoRaster object (GEORASTER column) in the GEORASTER_TABLE table, and it returns the default pyramid level set for the GeoRaster object. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=6 FOR UPDATE;
      sdo_geor.generatePyramid(grobj, 'rLevel=5, resampling=NN');
      sdo_geor.setDefaultPyramidLevel(grobj, 3);
      UPDATE georaster_table SET georaster = grobj WHERE georid=6;
      COMMIT;
    END;
    /

    SELECT georid, sdo_geor.getDefaultPyramidLevel(georaster) FROM georaster_table
      WHERE georid=6;

           GEORID   PLEVEL
    -------------- ----------
                 6          3

**Parent topic:** SDO_GEOR Package Reference

### 7.127 SDO_GEOR.setDefaultRed

#### Format

    SDO_GEOR.setDefaultRed(
         georaster   IN OUT SDO_GEORASTER,
         defaultRed  IN NUMBER);

#### Description

Sets the number of the layer to be used for the red color component (in the RGB color space) for displaying a GeoRaster object, or deletes the existing value if you specify a null `defaultRed` parameter.

#### Parameters

georaster
GeoRaster object.

defaultRed
Number of the layer to be used for the red color component (in the RGB color space) for displaying the specified GeoRaster object. Must be greater than 0 (zero) and less than or equal to the highest layer number in the GeoRaster object.

#### Usage Notes

The default red, green, and blue values are used for true-color displays, not for pseudocolor or grayscale displays. These values are optional, and they are intended for use only when visualizing multilayer or hyperspectral GeoRaster objects.

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if you are trying to set or remove the number of the layer to be used for the red color component only, or if `defaultRed` is not a valid layer number for the GeoRaster object.

#### Examples

The following example sets the default red, green, and blue color layers for the GeoRaster objects (GEORASTER column) in the GEORASTER_TABLE table, and it returns an array with the layer numbers for the red, green, and blue color components for displaying these GeoRaster objects. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setDefaultRed(grobj, 5);
      sdo_geor.setDefaultGreen(grobj, 4);
      sdo_geor.setDefaultBlue(grobj, 3);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

    SELECT sdo_geor.getDefaultColorLayer(georaster) FROM georaster_table
      WHERE georid=4;

    SDO_GEOR.GETDEFAULTCOLORLAYER(GEORASTER)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(5, 4, 3)

    1 row selected.

**Parent topic:** SDO_GEOR Package Reference

### 7.128 SDO_GEOR.setEndDateTime

#### Format

    SDO_GEOR.setEndDateTime(
         georaster IN OUT SDO_GEORASTER,
         endTime   IN TIMESTAMP WITH TIME ZONE);

#### Description

Sets the ending date and time for raster data collection in the metadata for a GeoRaster object, or deletes the existing value if you specify a null `endTime` parameter.

#### Parameters

georaster
GeoRaster object.

endTime
Time specification.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

To see the current ending date and time (if any) in the metadata for the GeoRaster object, use the SDO_GEOR.getEndDateTime function.

An exception is raised if `endTime` is earlier than the beginning date and time specified in the metadata for the GeoRaster object (see the SDO_GEOR.setBeginDateTime procedure).

#### Examples

The following example sets the beginning and ending dates and times for raster data collection in the metadata for a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setBeginDateTime(grobj, timestamp '2002-11-15 15:00:00');
      sdo_geor.setEndDateTime(grobj, timestamp '2002-11-15 15:00:10');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.129 SDO_GEOR.setGCPGeorefMethod

#### Format

    SDO_GEOR.setGCPGeorefMethod(
         inGeoraster     IN OUT SDO_GEORASTER
         gcpGeorefMethod IN VARCHAR2);

#### Description

Sets the GCP-based georeferencing geometric model type of a GeoRaster object.

#### Parameters

inGeoraster
GeoRaster object.

gcpGeorefMethod
Georeferencing geometric model type to set for the GeoRaster object. Its value must be one of following strings: `Affine`, `QuadraticPolynomial`, `CubicPolynomial`, `DLT`, `QuadraticRational`, or `RPC`.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

If `inGeoraster` does not contain GCP-based georeferencing information, no action is performed; otherwise, the existing model type is replaced with the specified `gcpGeorefMethod` value.

The procedure just set the model type value; no new solution is calculated. To get the solution for the newly set model type, use the SDO_GEOR.georeference function.

#### Examples

The following example sets the GCP-based georeferencing geometric model type of a specified GeoRaster object, and updates the object.

    DECLARE
       gr1  sdo_georaster;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=10 FOR UPDATE;
       sdo_geor.setGCPGeorefMethod(gr1, 'DLT');
       UPDATE georaster_table SET georaster=gr1 WHERE georid=10;
       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.130 SDO_GEOR.setGCPGeorefModel

#### Format

    SDO_GEOR.setGCPGeorefModel(
         inGeoraster     IN OUT SDO_GEORASTER
         gcpGeorefModel  IN SDO_GEOR_GCPGEOREFTYPE);

#### Description

Sets the GCP-based georeferencing model information for a GeoRaster object.

#### Parameters

inGeoraster
GeoRaster object.

gcpGeorefModel
Object containing the following: `FFMethodType`, `nGCP`, `GCPs`, `solutionAccuracy`.

#### Usage Notes

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

The SDO_GEOR_GCPGEOREFTYPE object type is defined in [SDO_GEOR_GCPGEOREFTYPE Object Type](georaster-datatypes.md).

This procedure stores the GCP information in the GeoRaster SRS metadata component. If `gcpGeorefModel` is null and if the GeoRaster object has a georeferencing model, this model information will be deleted.

If there are not enough GCPs specified in `gcpGeorefModel` for the geometric model specified, the function will still succeed, but an exception will be raised if the SDO_GEOR.georeference is called specifying this GeoRaster object.

#### Examples

The following example sets the GCP-based georeferencing model information in a specified GeoRaster object.

    DECLARE
       gr1          sdo_georaster;
       georefModel  SDO_GEOR_GCPGEOREFTYPE;
       GCPs         SDO_GEOR_GCP_COLLECTION;
       rms          sdo_number_array;
    BEGIN
       SELECT georaster INTO gr1 from herman.georaster_table WHERE georid=10 FOR UPDATE;

       GCPs:=SDO_GEOR_GCP_COLLECTION(
                        SDO_GEOR_GCP('21', '', 1,
                                2, sdo_number_array(25.625000, 73.875000),
                                2, sdo_number_array(237036.937500, 897987.187500),
                                NULL, NULL),
                         SDO_GEOR_GCP('22', '', 1,
                                2, sdo_number_array(100.625000, 459.125000),
                                2, sdo_number_array(237229.562500, 897949.687500),
                                NULL, NULL),
                          SDO_GEOR_GCP('23', '', 1,
                                2, sdo_number_array(362.375000, 77.875000),
                                2, sdo_number_array(237038.937500, 897818.812500),
                                    NULL, NULL),
                           SDO_GEOR_GCP('24', '', 1,
                                 2, sdo_number_array(478.875000, 402.125000),
                                 2, sdo_number_array(237201.062500, 897760.562500),
                                 NULL, NULL),
                            SDO_GEOR_GCP('25', '', 2,
                                 2, sdo_number_array(167.470583,  64.030686),
                                 2, sdo_number_array(237032.015343, 897916.264708),
                                 NULL, NULL),
                             SDO_GEOR_GCP('26', '', 2,
                                 2, sdo_number_array(101.456177,  257.915534),
                                 2, sdo_number_array(237128.957767, 897949.271912),
                                 NULL, NULL)
                   );

       georefModel := SDO_GEOR_GCPGEOREFTYPE('Affine',
                                                                                 GCPs.count, GCPs, rms);
       sdo_geor.setGCPGeorefModel(gr1, georefModel);
       UPDATE georaster_table SET georaster=gr1 WHERE georid=10;

       COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.131 SDO_GEOR.setGrayScale

#### Format

    SDO_GEOR.setGrayScale(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         grayScale    IN SDO_GEOR_GRAYSCALE);

#### Description

Sets the grayscale mappings for a layer in a GeoRaster object, or deletes the existing values if you specify a null `grayScale` parameter.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to set the grayscale mappings. A value of 0 (zero) indicates the object layer.

grayScale
An object of type SDO_GEOR_GRAYSCALE, which is described in [SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md).

#### Usage Notes

The following must be true of the specified SDO_GEOR_GRAYSCALE object:

- The `cellValue` values are consistent with and in the value range for the `cellDepth` value of the GeoRaster object.

- The `gray` value is an integer from 0 to 255.

- The `cellValue` array contains no duplicate entries.

- The entries in the `cellValue` array are in ascending order.

The GeoRaster object is automatically validated after the operation completes.

To return the grayscale mappings for a layer in a GeoRaster object, use the SDO_GEOR.getGrayScale function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, any gray values are null or out of scope, the `cellValue` array contains any duplicate values, or any `cellValue` values are null, out of scope, or out of order.

#### Examples

The following example sets the grayscale mappings for layer 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
      gsobj sdo_geor_grayscale;
    BEGIN
      gsobj := sdo_geor_grayscale(sdo_number_array(1, 10, 20, 30, 255),
                             sdo_number_array(0, 180, 210, 230, 250));

      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setGrayScale(grobj, 3, gsobj);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.132 SDO_GEOR.setGrayScaleTable

#### Format

    SDO_GEOR.setGrayScaleTable(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         tableName    IN VARCHAR2);

#### Description

Sets the grayscale mapping table for a layer in a GeoRaster object, or deletes the existing value if you specify a null `tableName` parameter.

**Note:**

This procedure registers the grayscale mapping table name with GeoRaster; however, GeoRaster does not perform operations using the grayscale mapping table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to set the grayscale mapping table. A value of 0 (zero) indicates the object layer.

tableName
Name of the grayscale mapping table for a layer in the specified GeoRaster object.

#### Usage Notes

[SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md) describes grayscale display.

The GeoRaster object is automatically validated after the operation completes.

To return the grayscale mapping table for a layer in a GeoRaster object, use the SDO_GEOR.getGrayScaleTable function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `tableName` is an empty string (`''`).

#### Examples

The following example sets `GST1` as the grayscale mapping table for layer 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setGrayScaleTable(grobj, 3, 'GST1');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.133 SDO_GEOR.setHistogramTable

#### Format

    SDO_GEOR.setHistogramTable(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER
         tableName    IN VARCHAR2);

#### Description

Sets the histogram table for a layer in a GeoRaster object.

**Note:**

This procedure registers the histogram table name with GeoRaster; however, GeoRaster does not perform operations using the histogram table in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to set the name of the histogram table. A value of 0 (zero) indicates the object layer.

tableName
Name of the histogram table. If this parameter is null, the metadata information for any existing histogram table (but not the actual table) is deleted. If there is no statistics information for the layer, this parameter must be null. The parameter value cannot be an empty string (that is, it cannot be `''`).

#### Usage Notes

This procedure specifies a user-defined histogram table. [SDO_GEOR_HISTOGRAM Object Type](georaster-datatypes.md) briefly discusses histograms.

To return the name of the histogram table for a layer, use the SDO_GEOR.getHistogramTable function.

An exception is raised if one or more of the following are true:

- `layerNumber` is null or invalid for the GeoRaster object,.

- `tableName` is an empty string (`''`).

- The statistical data associated with the specified layer is not set.

  To set the statistical data for a layer, call the SDO_GEOR.setStatistics procedure.

#### Examples

The following example sets `HIST1` as the histogram table for layer 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setHistogramTable(grobj, 3, 'HIST1');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.134 SDO_GEOR.setID

#### Format

    SDO_GEOR.setID(
         georaster  IN OUT SDO_GEORASTER,
         id         IN VARCHAR2);

#### Description

Sets a user-defined identifier to be associated with a GeoRaster object, or deletes the existing value if you specify a null `id` parameter.

#### Parameters

georaster
GeoRaster object.

id
ID value to be associated with the GeoRaster object.

#### Usage Notes

This procedure is useful for assigning unique meaningful alphanumeric identifiers to GeoRaster objects, so that users and applications can easily identify the objects.

The GeoRaster object is automatically validated after the operation completes.

To return the user-defined identifier value for a GeoRaster object, use the SDO_GEOR.getID function.

#### Examples

The following example sets `newid` as the user-defined identifier value of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 2 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=2 FOR UPDATE;
      sdo_geor.setID(grobj, 'newid');
      UPDATE georaster_table SET georaster = grobj WHERE georid=2;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.135 SDO_GEOR.setLayerID

#### Format

    SDO_GEOR.setLayerID(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         id           IN VARCHAR2);

#### Description

Sets a user-defined identifier to be associated with a layer in a GeoRaster object, or deletes the existing value if you specify a null `id` parameter.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

id
ID value to be associated with the specified layer in the GeoRaster object.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

To return the user-defined identifier value for a layer in a GeoRaster object, use the SDO_GEOR.getLayerID function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `id` is null yet the corresponding layer information does exist.

#### Examples

The following example sets `TM_Band_2` as the user-defined identifier value of layer 2 in the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setLayerID(grobj, 2, 'TM_Band_2');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.136 SDO_GEOR.setLayerOrdinate

#### Format

    SDO_GEOR.setLayerOrdinate(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         ordinate     IN NUMBER);

#### Description

Sets the band ordinate value for a specified layer in a GeoRaster object, or deletes the existing value if you specify a null `ordinate` parameter.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

ordinate
Band ordinate value of the layer along the band dimension.

#### Usage Notes

The band ordinate of the layer refers to the physical band that a layer (`layerNumber` parameter value) is associated with. For the current release, the associations must be as shown in [Figure 1-5](georaster-overview-and-concepts.md) in [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md): layer 1 is band 0, layer 2 is band 1, and so on.

The band ordinate for the object layer is ignored by GeoRaster.

The GeoRaster object is automatically validated after the operation completes.

To return the band ordinate value for a layer, use the SDO_GEOR.getLayerOrdinate function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, if `ordinate` is null, or if ordinate does not equal `layerNumber`-1 when `layerNumber` does not specify the object layer.

#### Examples

The following example sets the band ordinate value for layer 1 to be 0 (zero) in the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setLayerOrdinate(grobj, 1, 0);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.137 SDO_GEOR.setModelCoordLocation

#### Format

    SDO_GEOR.setModelCoordLocation(
         georaster      IN OUT SDO_GEORASTER
         modelCoordLoc  IN VARCHAR2);

#### Description

Sets the model coordinate location value for a GeoRaster object, or deletes the current model coordinate location value (if any) if the `modelCoordLoc` parameter is specified as null.

#### Parameters

georaster
GeoRaster object.

modelCoordLoc
Model coordinate location to set for the GeoRaster object. It must be specified as either null (to delete any current model coordinate location value) or one of the following string values: `CENTER` (the cell coordinate system is center-based) or `UPPERLEFT` (the cell coordinate system is based on the upper-left corner).

#### Usage Notes

This procedure enables you to change the cell coordinate system from CENTER to UPPERLEFT or from UPPERLEFT to CENTER.

This procedure applies only to georeferenced GeoRaster objects, and it automatically adjusts the functional fitting coefficients of the GeoRaster SRS accordingly to reflect the change (to ensure that the relationship between cell coordinates and model coordinates does not change).

To get the model coordinate location value for a GeoRaster object, use the SDO_GEOR.getModelCoordLocation function.

For an explanation of georeferencing using GCPs, see [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

#### Examples

The following example changes the cell coordinate system to CENTER for a GeoRaster object.

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setModelCoordLocation(grobj, 'CENTER');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.138 SDO_GEOR.setModelSRID

#### Format

    SDO_GEOR.setModelSRID(
         georaster  IN OUT SDO_GEORASTER,
         srid       IN NUMBER);

#### Description

Sets the coordinate system (SDO_SRID value) for the model (ground) space for a GeoRaster object, or deletes the existing value if you specify a null `srid` parameter and the GeoRaster metadata does not contain spatial reference information.

#### Parameters

georaster
GeoRaster object.

srid
Coordinate system. Must be a value from the SRID column of the MDSYS.CS_SRS table if the GeoRaster metadata contains spatial reference information; or must be null (causing no coordinate system associated with the model space) if the GeoRaster metadata does not contain spatial reference information. The `srid` value cannot be 0 (zero).

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

If the original GeoRaster object had a different model space SRID value, this procedure does not change the raster data itself and it does not adjust the georeferencing coefficients accordingly. In other words, this procedure does not cause any reprojection or resampling on the cell data of the GeoRaster object, and you must specify the correct SRID.

To return the coordinate system (SDO_SRID value) associated with the model space for a GeoRaster object, use the SDO_GEOR.getModelSRID function.

#### Examples

The following example changes the coordinate system for a GeoRaster object to Longitude / Latitude (WGS 66), which is the coordinate system associated with SRID value 82394 in the MDSYS.CS_SRS system table. (The example refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setModelSRID(grobj, 82394);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.139 SDO_GEOR.setNODATAMask

#### Format

    SDO_GEOR.setNODATAMask(
         georaster     IN OUT SDO_GEORASTER,
         layerNumber   IN NUMBER,
         isNODATAMask  IN VARCHAR2);

#### Description

Specifies whether a bitmap mask of the specified GeoRaster layer is a NODATA mask, and updates the GeoRaster metadata accordingly.

#### Parameters

georaster
GeoRaster object.

layerNumber
Layer with the relevant bitmap mask. A value of 0 (zero) indicates the object layer.

mask
The bitmap mask to be attached to the GeoRaster object. If this parameter is null, any existing bitmap mask associated with the specified layer of the GeoRaster object is removed.

isNODATAMask
Specifies whether the bitmap mask of the `layerNumber` layer is to be interpreted as a NODATA mask. The string `TRUE` causes that bitmap mask to be interpreted as a NODATA mask; the string `FALSE` causes that bitmap mask not to be interpreted as a NODATA mask.

#### Usage Notes

For information about a bitmap mask being treated as a special type of NODATA, that is, a NODATA mask specifying one or more irregular areas as NODATA areas, see [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

#### Examples

The following example sets the bitmap mask of sublayer 1 to be a NODATA mask.

    declare
        gr sdo_georaster;
    begin
         select georaster into gr from georaster_table where georid=1 for update;
         sdo_geor.setNODATAMask(gr, 1, 'true');
          update georaster_table set georster=gr where georid=1;
          commit;
    end;

**Parent topic:** SDO_GEOR Package Reference

### 7.140 SDO_GEOR.setOrthoRectified

#### Format

    SDO_GEOR.setOrthoRectified(
         georaster         IN OUT SDO_GEORASTER,
         isOrthoRectified  IN VARCHAR2);

#### Description

Specifies whether or not a GeoRaster object is orthorectified, or deletes the existing value if you specify a null `isOrthoRectified` parameter.

#### Parameters

georaster
GeoRaster object.

isOrthoRectified
Specify `TRUE` to specify that the GeoRaster object is orthorectified, `FALSE` to specify that the GeoRaster object is not orthorectified, or null if the GeoRaster metadata does not contain spatial reference information. Must be `TRUE` or `FALSE` (case-insensitive) if the GeoRaster metadata contains spatial reference information.

#### Usage Notes

This procedure modifies the GeoRaster metadata for the object. It does not actually orthorectify the object. Users are responsible for ensuring that orthorectification is performed.

The GeoRaster object is automatically validated after the operation completes.

To be set as orthorectified, a GeoRaster object must be spatially referenced and rectified.

#### Examples

The following example identifies the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table as orthorectified. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setOrthoRectified(grobj, 'TRUE');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.141 SDO_GEOR.setRasterType

#### Format

    SDO_GEOR.setRasterType(
         georaster   IN OUT SDO_GEORASTER,
         rasterType  IN NUMBER);

#### Description

Sets the raster type of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

rasterType
Numeric value to be set as the rasterType attribute of the GeoRaster object. Must be a valid 5-digit numeric value, in the format described in [rasterType Attribute](georaster-datatypes.md).

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if `rasterType` is null or if the first three digits of the existing `rasterType` value are changed.

#### Examples

The following example sets the `rasterType` attribute value of a GeoRaster object to `20001`. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=2 FOR UPDATE;
      sdo_geor.setRasterType(grobj, 20001);
      UPDATE georaster_table SET georaster = grobj WHERE georid=2;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.142 SDO_GEOR.setRectified

#### Format

    SDO_GEOR.setRectified(
         georaster   IN OUT SDO_GEORASTER,
         isRectified IN VARCHAR2);

#### Description

Specifies whether or not a GeoRaster object is rectified, or deletes the existing value if you specify a null `isRectified` parameter.

#### Parameters

georaster
GeoRaster object.

isRectified
Specify `TRUE` to specify that the GeoRaster object is rectified, `FALSE` to specify that the GeoRaster object is not rectified, or null if the GeoRaster metadata does not contain spatial reference information. Must be `TRUE` or `FALSE` (case-insensitive) if the GeoRaster metadata contains spatial reference information.

#### Usage Notes

This procedure modifies the GeoRaster metadata for the object. It does not actually rectify the object. Users are responsible for ensuring that rectification is performed. (To rectify or orthorectify a GeoRaster object, you can use the SDO_GEOR.rectify procedure.)

The GeoRaster object is automatically validated after the operation completes.

A GeoRaster object must be spatially referenced if you want to set `isRectified` to `TRUE` (see the SDO_GEOR.setSpatialReferenced procedure).

#### Examples

The following example identifies the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table as not rectified. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setRectified(grobj, 'false');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.143 SDO_GEOR.setScaling

#### Format

    SDO_GEOR.setScaling(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         scalingFunc  IN SDO_NUMBER_ARRAY);

#### Description

Sets the scaling function associated with a layer, or deletes the existing value if you specify a null `scalingFunc` parameter.

**Note:**

GeoRaster does not perform operations using the scaling function in the current release.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

scalingFunc
An array of numeric values, with one value for each coefficient in the scaling function. The scaling function is as follows:

    value = (a0 + a1 * cellvalue) / (b0 + b1 * cellvalue)

The order of the coefficients is: a<sub>0</sub>, a<sub>1</sub>, b<sub>0</sub>, b<sub>1</sub>.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object; if `scalingFunc` is of the wrong array size; if one of a<sub>0</sub>, a<sub>1</sub>, b<sub>0</sub>, and b<sub>1</sub> is null; or if both b<sub>0</sub> and b<sub>1</sub> are 0 (zero).

#### Examples

The following example sets the coefficients of the scaling function for layer 2 of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setScaling(grobj, 2, sdo_number_array(1, 0.5, 1, 0));
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.144 SDO_GEOR.setSourceInfo

#### Format

    SDO_GEOR.setSourceInfo(
         georaster   IN OUT SDO_GEORASTER,
         sourceInfo  IN VARCHAR2);

#### Description

Sets the source information for a GeoRaster object, or deletes the existing value if you specify a null `sourceInfo` parameter.

#### Parameters

georaster
GeoRaster object.

sourceInfo
String with source information. Cannot exceed 4096 characters.

#### Usage Notes

The specified `sourceInfo` string is stored in the `<sourceInfo>` element in the metadata for the GeoRaster object (described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md)).

This procedure replaces any existing source information value or values. If you want to keep any existing values and add one or more values, use the SDO_GEOR.addSourceInfo procedure.

#### Examples

The following example sets and adds some source information for a specified GeoRaster object, and then retrieves the information.

    declare
     gr sdo_georaster;
    begin
     select georaster into gr from georaster_table where georid=1 for update;
     sdo_geor.setSourceInfo(gr, 'Copyright (c) 2002, 2007, Oracle Corporation.');
     sdo_geor.addSourceInfo(gr, 'All rights reserved.');
     update georaster_table set georaster=gr where georid=1;
    end;
    /

    select * from table(select sdo_geor.getSourceInfo(georaster) from georaster_table where id=1);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    Copyright (c) 2002, 2007, Oracle Corporation.
    All rights reserved.

**Parent topic:** SDO_GEOR Package Reference

### 7.145 SDO_GEOR.setSpatialReferenced

#### Format

    SDO_GEOR.setSpatialReferenced(
         georaster     IN OUT SDO_GEORASTER,
         isReferenced  IN VARCHAR2);

#### Description

Specifies whether or not a GeoRaster object is spatially referenced, or deletes the existing value if you specify a null `isReferenced` parameter.

#### Parameters

georaster
GeoRaster object.

isReferenced
Specify `TRUE` to specify that the GeoRaster object is spatially referenced, `FALSE` to specify that the GeoRaster object is not spatially referenced, or null if the GeoRaster metadata does not contain spatial reference information. Must be `TRUE` or `FALSE` (case-insensitive) if the GeoRaster metadata contains spatial reference information.

#### Usage Notes

This procedure sets the GeoRaster object to be spatially referenced or not spatially referenced.

The GeoRaster object is automatically validated after the operation completes.

#### Examples

The following example sets the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table as not spatially referenced. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setSpatialReferenced(grobj, 'FALSE');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.146 SDO_GEOR.setSpatialResolutions

#### Format

    SDO_GEOR.setSpatialResolutions(
         georaster    IN OUT SDO_GEORASTER,
         resolutions  IN SDO_NUMBER_ARRAY);

#### Description

Sets the spatial resolution value along each spatial dimension of a GeoRaster object, or deletes the existing values if you specify a null `resolutions` parameter.

#### Parameters

georaster
GeoRaster object.

resolutions
An array of numeric values, one for each spatial dimension. Each value indicates the number of units of measurement associated with the data area represented by that spatial dimension of a pixel. For example, if the spatial resolution values are (10,10) and the unit of measurement for the ground data is meters, each pixel represents an area of 10 meters by 10 meters.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

If resolutions is not null and if the GeoRaster metadata currently does not contain spatial reference information, this procedure adds spatial reference information with minimum default values.

See also the Usage Notes for the SDO_GEOR.getSpatialResolutions function.

#### Examples

The following example sets the spatial resolution values along the column and row (X and Y) dimensions of a GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setSpatialResolutions(grobj, sdo_number_array(28.5,28.5));
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.147 SDO_GEOR.setSpectralResolution

#### Format

    SDO_GEOR.setSpectralResolution(
         georaster  IN OUT SDO_GEORASTER,
         resolution IN NUMBER);

#### Description

Sets the spectral resolution of a GeoRaster object if it is a hyperspectral or multiband image, or deletes the existing value if you specify a null `resolution` parameter.

#### Parameters

georaster
GeoRaster object.

resolution
Spectral resolution value. Must be null if the GeoRaster metadata does not contain band reference information.

#### Usage Notes

Taken together, the spectral unit and spectral resolution identify the wavelength interval for a band. For example, if the spectral resolution value is 2 and the spectral unit value is `MILLIMETER`, the wavelength interval for a band is 2 millimeters.

The GeoRaster object is automatically validated after the operation completes.

To return the spectral resolution for a GeoRaster object, use the SDO_GEOR.getSpectralResolution function.

#### Examples

The following example sets 0.5 as the spectral resolution value for the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setSpectralResolution(grobj, 0.5);
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.148 SDO_GEOR.setSpectralUnit

#### Format

    SDO_GEOR.setSpectralUnit(
         georaster  IN OUT SDO_GEORASTER,
         unit       IN VARCHAR2);

#### Description

Sets the unit of measurement for identifying the wavelength interval for a band, or deletes the existing value if you specify a null `unit` parameter.

#### Parameters

georaster
GeoRaster object.

unit
Spectral unit. Must be one of the following values if the GeoRaster metadata contains band reference information: `METER`, `MILLIMETER`, `MICROMETER`, `NANOMETER`. Must be null if the GeoRaster metadata does not contain band reference information.

#### Usage Notes

Taken together, the spectral unit and spectral resolution identify the wavelength interval for a band. For example, if the spectral resolution value is 2 and the spectral unit value is `MILLIMETER`, the wavelength interval for a band is 2 millimeters.

The GeoRaster object is automatically validated after the operation completes.

To return the spectral unit for a GeoRaster object, use the SDO_GEOR.getSpectralUnit function.

#### Examples

The following example sets `MICROMETER` as the spectral unit for the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setSpectralUnit(grobj, 'micrometer');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.149 SDO_GEOR.setSRS

#### Format

    SDO_GEOR.setSRS(
         georaster  IN OUT SDO_GEORASTER,
         srs        IN SDO_GEOR_SRS);

#### Description

Sets the spatial reference information of a GeoRaster object, or deletes the existing information if you specify a null `srs` parameter.

#### Parameters

georaster
GeoRaster object.

srs
An object of type SDO_GEOR_SRS. The SDO_GEOR_SRS object type and its constructor are described in [SDO_GEOR_SRS Object Type](georaster-datatypes.md).

In this object, `isReferenced`, `isRectified`, and `isOrthoRectified` must be `TRUE` or `FALSE` (case-insensitive); `spatialResolution` must be an array of the correct size; the spatial tolerance cannot be negative; `CoordLocation` must be 0 or 1; and the polynomial parameters cannot be null.

#### Usage Notes

You can use this procedure to set the GeoRaster SRS for any functional fitting georeferencing models, including the affine transformation, DLT, and RPC models.

For the stored function (GCP) model only, you may find it more convenient not to use this procedure, but instead to use the SDO_GEOR.setGCPGeorefModel procedure to set the stored function (GCP) model.

The GeoRaster object is automatically validated after the operation completes.

To return the SDO_GEOR_SRS information for a GeoRaster object, use the SDO_GEOR.getSRS function.

#### Examples

The following examples specify spatial reference attributes of a GeoRaster object, and updates the GeoRaster object. (They refer to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).) Notes explain the operations in more detail.

The first example shows how to set an affine transformation model to a GeoRaster object.

    DECLARE
      grobj sdo_georaster;
      srs   sdo_geor_srs;

    BEGIN

    SELECT georaster INTO grobj FROM georaster_table WHERE georid=4;
    srs := sdo_geor_srs('TRUE', 'TRUE', null, 82262,
                           sdo_number_array(28.5, 28.5),0.5,0,
                           0,0,0,0,0,1,1,1,1,1,0,0,0,
                           SDO_NUMBER_ARRAY(1, 2, 1, 3, 32631.5614, 0, -.03508772),
                           SDO_NUMBER_ARRAY(1, 0, 0, 1, 1),
                           SDO_NUMBER_ARRAY(1, 2, 1, 3, -7894.7544, .03508772, 0),
                           SDO_NUMBER_ARRAY(1, 0, 0, 1, 1));
    sdo_geor.setSRS(grobj, srs);

    UPDATE georaster_table SET georaster = grobj WHERE georid=4;
    COMMIT;
    END;
    /

In the preceding example, the GeoRaster object has the following affine transformation:

    row = 32631.5614 + 0 * x + (-0.03508772) * y
    col = -7894.7544 + 0.03508772 * x + 0 * y

To use the generic functional fitting georeferencing model described in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md), the values of SRS attributes are as follows:

    xOff=yOff=zOff=0
    rowOff=columnOff=0
    xScale=yScale=zScale=1
    rowScale=columnScale=1
    polynomial p : pType=1, nVars=2, order=1, nCoefficients= 3
    polynomial q : pType=1, nVars=0, order=0, nCoefficients= 1
    polynomial r : pType=1, nVars=2, order=1, nCoefficients= 3
    polynomial s : pType=1, nVars=0, order=0, nCoefficients= 1

    rowNumerator = 32631.5614, 0, -0.03508772
    rowDenominator =  1
    columnNumerator = -7894.7544, 0.03508772, 0
    columnDenominator = 1

In the SRS structure, the `rowNumerator`, `rowDenominator`, `columnNumerator`, and `columnDenominator` elements are used to specify `pType`, `nVars`, `order`, and `nCoefficients`, and the remaining elements are used to specify coefficients of each polynomial.

The second example shows how to set a DLT model to a GeoRaster object. In a typical photogrammetry application, the interior orientation parameters and exterior orientation parameters of an oriented digital aerial photo can be used to derive a DLT model, which is widely used to simplify and approximate the rigorous model. The following is an example of a DLT model derived from a standard frame camera model.

    row = (-46507111.2127784 + 65.81484127*X + 13.13186856*Y - 49.62133265*Z) / (-41.47013322 + 0.00004128*X + 0.00009740*Y - 0.00655704*Z)

    col = (-5259855.00453679 - 12.07452653*X + 66.23319061*Y - 49.45792766*Z) / (-41.47013322 + 0.00004128*X + 0.00009740*Y - 0.00655704*Z)


For this example, the corresponding GeoRaster SRS parameters and coefficients are:

    rowOff=0, colOff=0; rowScale = colScale = 1;
    xOff = 0, yOff = 0, zOff = 0; xScale = yScale = zScale =1;
    polynomial p : pType=1, nVars=3, order=1, nCoefficients= 4
    polynomial q : pType=1, nVars=3, order=1, nCoefficients= 4
    polynomial r : pType=1, nVars=3, order=1, nCoefficients= 4
    polynomial s : pType=1, nVars=3, order=1, nCoefficients= 4

    rowNumerator = -5259855.00453679, -12.07452653, 66.23319061, -49.45792766
    rowDenominator = -41.47013322, 0.00004128, 0.00009740, -0.00655704
    columnNumerator = -46507111.2127784, 65.81484127, 13.13186856, -49.62133265
    columnDenominator = -41.47013322, 0.00004128, 0.00009740, -0.00655704

The following sets up the DLT model for the GeoRaster object. It uses the SDO_GEOR_SRS constructor to create an instance of the SDO_GEOR_SRS type, and then sets the appropriate attributes.

    DECLARE
       grobj sdo_georaster;
       srs sdo_geor_srs;
    BEGIN
       SELECT georaster INTO grobj FROM georaster_table WHERE georid = 101;

       -- Initiate the SRS object.
       srs:=sdo_geor_srs();

       -- Fill the parameters of the SRS object.
       srs.isReferenced := 'TRUE';
       srs.isRectified := 'FALSE';
       srs.isOrthoRectified := 'FALSE';
       srs.srid := 7406;
       srs.spatialResolution := sdo_number_array(0.07, 0.07);
       srs.coordLocation := 1;
       srs.rowOff := 0;
       srs.columnOff := 0;
       srs.xOff := 0;
       srs.yOff := 0;
       srs.zOff := 0;
       srs.rowScale := 1;
       srs.columnScale := 1;
       srs.xScale := 1;
       srs.yScale := 1;
       srs.zScale := 1;
       srs.rowNumerator := SDO_NUMBER_ARRAY(1, 3, 1, 4, -5259855.00453679,
         -12.07452653,66.23319061,-49.45792766);
       srs.rowDenominator := SDO_NUMBER_ARRAY(1, 3, 1, 4, -41.4701332195,
         0.0000412763, 0.0000974018, -0.0065570398);
       srs.columnNumerator := SDO_NUMBER_ARRAY(1, 3, 1, 4,
         -46507111.2127784, 65.81484127, 13.13186856, -49.62133265);
       srs.columnDenominator := SDO_NUMBER_ARRAY(1, 3, 1, 4,
         -41.4701332195, 0.0000412763, 0.0000974018, -0.0065570398);

       -- Set the SRS metadata to the GeoRaster object.
       sdo_geor.setSRS(grobj,srs);
       UPDATE georaster_table SET georaster = grobj WHERE georid= 101;
       COMMIT;

    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.150 SDO_GEOR.setStatistics

#### Format

    SDO_GEOR.setStatistics(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         statistics   IN SDO_NUMBER_ARRAY);

or

    SDO_GEOR.setStatistics(
         georaster      IN OUT SDO_GEORASTER,
         layerNumber    IN NUMBER,
         statistics     IN SDO_NUMBER_ARRAY,
         histogram      IN SDO_GEOR_HISTOGRAM,
         samplingFactor IN NUMBER DEFAULT 1,
         samplingWindow IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.setStatistics(
         georaster      IN OUT SDO_GEORASTER,
         layerNumber    IN NUMBER,
         statistics     IN SDO_NUMBER_ARRAY,
         histogram      IN SDO_GEOR_HISTOGRAM,
         samplingFactor IN NUMBER DEFAULT 1,
         samplingWindow IN SDO_GEOMETRY DEFAULT NULL);

#### Description

Sets statistical data associated with a layer.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to set the statistics. A value of 0 (zero) indicates the object layer.

statistics
An array with the following numeric values: `MIN`, `MAX`, `MEAN`, `MEDIAN`, `MODEVALUE`, `STD`. You must specify non-null values for all values in the array. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`.

If this parameter is null, all statistical information associated with the layer is deleted.

histogram
Histogram of type SDO_GEOR_HISTOGRAM. [SDO_GEOR_HISTOGRAM Object Type](georaster-datatypes.md) describes this object type and briefly discusses histograms.

samplingFactor
Sampling factor. The denominator n in 1/n, representing the number of cells sampled in computing the statistics. For example, if `samplingFactor` is 4, one-fourth of the cells were sampled. The default is 1; that is, all cells were sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they were computed.

samplingWindow
Sampling window: a rectangular window for which to set statistics, specified either as a numeric array with the lower-left and upper-right coordinates or as an SDO_GEOMETRY object. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`. The window must be inside the extent in cell space. The default for this parameter is the entire image.

#### Usage Notes

This procedure sets statistical data described by the `<statisticDatasetType>` element in the GeoRaster metadata XML schema, which is described in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md).

If `histogram` is specified as null, and if there is an existing histogram and you set the statistics using a different sampling factor or sampling window, the existing histogram is removed.

Contrast this procedure, in which you specify the statistics to be set, with the SDO_GEOR.generateStatistics function, which causes GeoRaster to compute and set the statistics.

To retrieve the statistical data associated with a layer, use the SDO_GEOR.getStatistics function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `statistics` is of the wrong array size or has any null array elements.

#### Examples

The following example sets the statistical data for layer 0 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setStatistics(grobj, 0, SDO_NUMBER_ARRAY(0, 255, 100, 127, 95, 25));
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.151 SDO_GEOR.setULTCoordinate

#### Format

    SDO_GEOR.setULTCoordinate(
         georaster  IN OUT SDO_GEORASTER,
         ultCoord   IN SDO_NUMBER_ARRAY);

#### Description

Sets or adjusts the cell coordinate values of the upper-left corner of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

ultCoord
An array of two numbers (row and column ordinates) if the rasterType value is 20001, or three numbers (row, column, and band ordinates) if the rasterType value is 21001. If you specify three numbers, the third one (band number) must be 0. For more information about the ULTCoordinate, see [GeoRaster Data Model](georaster-overview-and-concepts.md).

#### Usage Notes

If the metadata contains spatial reference information and the GeoRaster object is georeferenced, the spatial reference information is checked for validity. If it is valid, the spatial reference information including the georeferencing information is updated and adjusted according to the new ULT coordinates; otherwise, an exception is raised.

To return the upper-left coordinate values for a GeoRaster object, use the SDO_GEOR.getULTCoordinate function.

An exception is raised if `ultCoord` is null or of the wrong array size or has any null array elements.

#### Examples

The following example sets the row and column ordinates of the upper-left corner of a GeoRaster object, with logic to handle whether the rasterType value is 20001 or 21001. (The example refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
     grobj sdo_georaster;
    BEGIN
     SELECT georaster INTO grobj FROM georaster_table WHERE georid=1 FOR UPDATE;
     if grobj.rasterType = 20001 then
          sdo_geor.setULTCoordinate(grobj, sdo_number_array(0, 0));
     elsif grobj.rasterType = 21001 then
          sdo_geor.setULTCoordinate(grobj, sdo_number_array(0, 0, 0));
     end if;
     UPDATE georaster_table SET georaster = grobj WHERE georid=1;
     COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.152 SDO_GEOR.setVAT

#### Format

    SDO_GEOR.setVAT(
         georaster    IN OUT SDO_GEORASTER,
         layerNumber  IN NUMBER,
         vatName      IN VARCHAR2);

#### Description

Sets the name of the value attribute table (VAT) associated with a layer of a GeoRaster object, or deletes the existing value if you specify a null `vatName` parameter.

#### Parameters

georaster
GeoRaster object.

layerNumber
Number of the layer for which to perform the operation.

vatName
Name of the value attribute table.

#### Usage Notes

The GeoRaster object is automatically validated after the operation completes.

For more information about value attribute tables, see [Geographic Information Systems](georaster-overview-and-concepts.md).

To return the name of the value attribute table associated with a layer of a GeoRaster object, use the SDO_GEOR.getVAT function.

An exception is raised if `layerNumber` is null or invalid for the GeoRaster object, or if `vatName` is an empty string (`''`).

#### Examples

The following example specifies `VATT1` as the value attribute table to be associated with layer 3 of the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setVAT(grobj, 3, 'VATT1');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.153 SDO_GEOR.setVersion

#### Format

    SDO_GEOR.setVersion(
         georaster     IN OUT SDO_GEORASTER,
         majorVersion  IN VARCHAR2,
         minorVersion  IN VARCHAR2);

#### Description

Sets the user-specified version of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

<!-- -->

majorVersion
String representing the major version of the GeoRaster object. For example, if the complete version string is `15a.beta1`, specify the `majorVersion` value as `15a`.

If the parameter value is null, any existing `majorVersion` value in the GeoRaster object is deleted.

<!-- -->

minorVersion
String representing the minor version of the GeoRaster object. For example, if the complete version string is `15a.beta1`, specify the `minorVersion` value as `beta1`.

If the parameter value is null, any existing `minorVersion` value in the GeoRaster object is deleted.

#### Usage Notes

The major and minor version strings can reflect any versioning scheme that you choose. The `majorVersion` and `minorVersion` values can be any string, except that neither can be an empty string (that is, neither can be `''`).

To retrieve the version string for a GeoRaster object, use the SDO_GEOR.getVersion function, which returns the version in the format major-version.minor-version.

#### Examples

The following example sets `15a.beta1` as the version for the GeoRaster object (GEORASTER column) in the row with the GEORID column value of 4 in the GEORASTER_TABLE table. (The GEORASTER_TABLE table definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      grobj sdo_georaster;
    BEGIN
      SELECT georaster INTO grobj FROM georaster_table WHERE georid=4 FOR UPDATE;
      sdo_geor.setVersion(grobj, '15a', 'beta1');
      UPDATE georaster_table SET georaster = grobj WHERE georid=4;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.154 SDO_GEOR.subset

#### Format

    SDO_GEOR.subset(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         layerNumbers  IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip   IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.subset(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_GEOMETRY,
         layerNumbers  IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         polygonClip   IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.subset(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         bandNumbers   IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.subset(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_NUMBER_ARRAY,
         bandNumbers   IN VARCHAR2,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Performs either or both of the following operations: (1) spatial crop, cut, or clip, or (2) layer or band subset or duplicate.

#### Parameters

inGeoRaster
The SDO_GEORASTER object on which the operation or operations are to be performed.

pyramidLevel
A number specifying the pyramid level of the source GeoRaster object.

cropArea
Crop area definition. If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

layerNumbers
A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

bandNumbers
A string identifying the physical band numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The new SDO_GEORASTER object. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

polygonClip
The string `TRUE` causes the clipping window (`cropArea` geometry object) to be used for the subset operation; the string `FALSE` or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the subset operation.

#### Usage Notes

This procedure has a variety of possible uses. For example, you can call it to crop a small area or obtain a subset of a few layers of a GeoRaster object, you can duplicate layers, and you can specify storage parameters such as blocking and interleaving for the resulting object.

If you use the format that includes the `pyramidLevel` parameter and specify a value greater than zero (0), the cropping is done based on the specified pyramid level of the source GeoRaster object; otherwise, the cropping is done based on the original source GeoRaster object (`pyramidLevel` = 0).

If the source GeoRaster object is georeferenced and the `pyramidLevel` parameter value is greater than 0, the georeferencing information is generated for the resulting GeoRaster object only when the georeference is a valid polynomial transformation.

Any upper-level pyramid data in the input GeoRaster object is not considered in this operation, and the output GeoRaster object has no pyramid data.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `cropArea` parameter specifies a geodetic MBR, it cannot cross the date line meridian. For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

To be able to use the clipping window geometry object itself to subset the GeoRaster object, the geometry object must be a valid two-dimensional polygon geometry, simple or multipolygon, with an SDO_GTYPE value in the form 2nn3 or 2nn7. For any other SDO_GTYPE value, the MBR of the geometry object is used regardless of the value of the `polygonClip` parameter. (For an explanation of SDO_GTYPE values, see [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md).)

If the clipping window geometry object itself is applied to the subset process, all cells inside the polygon or touched by the polygon edges are returned; other cells within the MBR of the geometry object are clipped, that is, filled by the specified or default `bgValues` parameter values.

If `polygonClip` is `TRUE`, and if this procedure creates a rectangular image subset but the geometry is not a rectangle, check the validity of the `inWindow` geometry object with the function SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT. For an invalid geometry, this procedure operates as if the `polygonClip` value is `FALSE` or a null value.

`inGeoRaster` and `outGeoRaster` must be different GeoRaster objects.

Only the overlapping portion of the specified window of interest and the source GeoRaster object's spatial extent is copied.

If you want to reproject the output GeoRaster object to a different coordinate system, use the SDO_GEOR.rectify or SDO_GEOR.reproject procedure.

An exception is raised if one or more of the following are true:

- `inGeoRaster` is invalid.

- `outGeoRaster` has not been initialized.

- A raster data table for `outGeoRaster` does not exist and `outGeoRaster` is not a blank GeoRaster object.

- The specified window of interest falls outside of the GeoRaster object's spatial extent.

#### Examples

The following example creates a GeoRaster object that contains only specified bands from a specified window from the original object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor.subset(gr1, sdo_geometry(2003, NULL, NULL,
                                   sdo_elem_info_array(1, 1003, 3),
                                   sdo_ordinate_array(0,256,255,511)),
                      '3,1-2', null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example demonstrates how to do clipping while subsetting a GeoRaster object using a polygon. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr sdo_georaster;
      grsub sdo_georaster;
      win1 sdo_geometry;
    BEGIN
      Delete from georaster_table where georid = 111;
      INSERT INTO georaster_table VALUES (111, 'ClippedImage',
         sdo_geor.init('georaster_RDT', 111))
         RETURNING georaster INTO grsub;
      SELECT georaster INTO gr FROM georaster_table WHERE georid=1;
      win1 := sdo_geometry(2003, 26986, null, sdo_elem_info_array(1,1003,1),
                    sdo_ordinate_array(237040,   897924,
                                       237013.3, 897831.6,
                                       237129,   897840,
                                       237182.5, 897785.5,
                                       237239.9, 897902.7,
                                       237223,   897954,
                                       237133,   897899,
                                       237040,   897924));
      sdo_geor.subset(gr, 0, win1, '1-3',
                      'interleaving = BIL, compression=DEFLATE',
                      grsub, NULL, 'TRUE');
      UPDATE georaster_table SET georaster=grsub WHERE georid=111;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.155 SDO_GEOR.updateRaster

#### Format

    SDO_GEOR.updateRaster(
         targetGeoRaster     IN OUT SDO_GEORASTER,
         targetPyramidLevel  IN NUMBER,
         targetLayerNumbers  IN VARCHAR2,
         targetArea          IN SDO_GEOMETRY,
         sourceGeoRaster     IN SDO_GEORASTER,
         sourcePyramidLevel  IN NUMBER,
         sourceLayerNumbers  IN VARCHAR2,
         updateUpperPyramids IN VARCHAR2,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR.updateRaster(
         targetGeoRaster     IN OUT SDO_GEORASTER,
         targetPyramidLevel  IN NUMBER,
         targetBandNumbers   IN VARCHAR2,
         targetArea          IN SDO_NUMBER_ARRAY,
         sourceGeoRaster     IN SDO_GEORASTER,
         sourcePyramidLevel  IN NUMBER,
         sourceBandNumbers   IN VARCHAR2,
         updateUpperPyramids IN VARCHAR2,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Updates a specified pyramid of a specified area or the overlapping parts of one GeoRaster object with selected pyramid and selected bands or layers of another GeoRaster object.

#### Parameters

targetGeoRaster
GeoRaster object to be updated. (Be sure to make a copy of this object before you update it.)

targetPyramidLevel
Number specifying the pyramid level of the target GeoRaster object to be updated.

targetLayerNumbers
String specifying one or more layer numbers of layers in `targetGeoRaster` to be updated. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'1,3-5,7'` for layers 1, 3, 4, 5, and 7.

targetBandNumbers
String specifying one or more band numbers of bands in `targetGeoRaster` to be updated. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'0,3-5,7'` for bands 0, 3, 4, 5, and 7. Any bands that you specify for this parameter must be compatible with the bands to be updated in the target GeoRaster object.

targetArea
Area to be updated in `targetGeoRaster`: a rectangular window, specified either as a numeric array with the lower-left and upper-right coordinates or as an SDO_GEOMETRY object. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the target area; see also the Usage Notes for SDO_SRID requirements.

If `targetArea` is of type SDO_GEOMETRY, use the `targetLayerNumbers` and `sourceLayerNumbers` parameters to specify one or more layer numbers; if `targetArea` is of type SDO_NUMBER_ARRAY, use the `targetBandNumbers` and `sourceBandNumbers` parameters to specify one or more band numbers.

If the specified area does not intersect with the spatial extent of `targetGeoRaster`, no update is performed. If this parameter is specified as null, all of the overlapping area is updated.

For more information about using this parameter, see [Image Pyramiding: Parallel Generation and Partial Update](image-processing-virtual-mosaic.md).

sourceGeoRaster
GeoRaster object in which specified layers are to be used to update `targetGeoRaster`.

sourcePyramidLevel
Number specifying the pyramid level of the `sourceGeoRaster` object.

sourceLayerNumbers
String specifying one or more layer numbers of layers in `sourceGeoRaster` to be used to update `targetGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'1,3-5,7'` for layers 1, 3, 4, 5, and 7.

Any layers that you specify for this parameter must be compatible with the layers to be updated in the target GeoRaster object.

sourceBandNumbers
String specifying one or more band numbers of bands in `sourceGeoRaster` to be used to update `targetGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `'0,3-5,7'` for bands 0, 3, 4, 5, and 7.

Any bands that you specify for this parameter must be compatible with the bands to be updated in the target GeoRaster object.

updateUpperPyramids
String (`TRUE` or `FALSE`) specifying whether to update upper-level pyramids. (This parameter has no default value; you should always specify it.) For more information about using this parameter, see [Image Pyramiding: Parallel Generation and Partial Update](image-processing-virtual-mosaic.md).

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

#### Usage Notes

**Note:**

Be sure to make a copy of the `targetGeoRaster` object before you call this procedure, because the changes made to this GeoRaster object might not be reversible after the procedure completes.

If both GeoRaster objects are georeferenced, they must use the same coordinate system, have the same cell depth, and have the same spatial resolutions at the specified pyramid levels; however, the `targetPyramidLevel` and `sourcePyramidLevel` values can be different. If both GeoRaster objects are not georeferenced, the ULTCoordinates will be considered to co-locate them into each other.

The two GeoRaster objects can have different dimensions and sizes.

If the `targetArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `window` parameter geometry and the model space are different, the `window` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `targetArea` parameter specifies a geodetic MBR, it cannot cross the date line meridian. For information about geodetic MBRs, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

Any existing bitmap masks are not updated.

If the source GeoRaster object is not large enough to fill in the target area, the uncovered area will not be updated.

If the target GeoRaster object has pyramids or is compressed, or both, the updates will be reflected in the pyramids and the compression.

To update upper-level pyramids, you must specify the `updateUpperPyramids` parameter as '`TRUE`'. (This parameter has no default value; you should always specify '`TRUE`' or '`FALSE`'.)

#### Examples

The following example updates a specified area in band 1 of the specified target GeoRaster object with band 0 of the same area of another GeoRaster object.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      area sdo_number_array := sdo_number_array(-200,-50,201,162);
    BEGIN
      SELECT georaster INTO gr2 FROM georaster_table WHERE georid=0 FOR UPDATE;
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=1;
      SDO_GEOR.updateRaster(gr2, 0, '1', area, gr1, 0, '0', 'true');
      UPDATE GEORASTER_TABLE SET georaster=gr2 WHERE georid=0;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR Package Reference

### 7.156 SDO_GEOR.validateBlockMBR

#### Format

    SDO_GEOR.validateBlockMBR(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Validates the `blockMBR` attribute of each block of a GeoRaster object.

#### Parameters

georaster
GeoRaster object.

#### Usage Notes

This function checks the `blockMBR` attribute (described in [blockMBR Attribute](georaster-datatypes.md)) in each row of the raster data table associated with the specified GeoRaster object to see if its geometry is the actual minimum bounding rectangle (MBR) of that block.

This function returns the string `TRUE` if the `blockMBR` attribute is the MBR of each block, a null value if the GeoRaster object is null, an Oracle error code if the error is known, or `FALSE` for an unknown error.

If you created the GeoRaster object as described in [Creating New GeoRaster Objects](georaster-database-creation-management.md), the `blockMBR` attribute values were automatically calculated and they should not need to be validated or generated. However, if the GeoRaster object was generated by a third party, you should validate the `blockMBR` attribute values using this function; and if any are not valid, call the SDO_GEOR.generateBlockMBR procedure.

#### Examples

The following example validates the `blockMBR` attribute of each block of a specified GeoRaster object.

    SELECT sdo_geor.validateBlockMBR(georaster) FROM georaster_table WHERE georid=1;

    SDO_GEOR.VALIDATEBLOCKMBR(GEORASTER)
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_GEOR Package Reference

### 7.157 SDO_GEOR.validateGeoRaster

#### Format

    SDO_GEOR.validateGeoRaster(
         georaster  IN SDO_GEORASTER
         ) RETURN VARCHAR2;

#### Description

Validates a GeoRaster object, checking its raster data and metadata.

#### Parameters

georaster
GeoRaster object to be checked for validity.

#### Usage Notes

This function returns the string `TRUE` if the GeoRaster object is valid, a null value if the GeoRaster object is null, an Oracle error code if the error is known, or `FALSE` for an unknown error.You should use this function after you create, load, or modify a GeoRaster object, to ensure that it is valid before you process it further.

If this function identifies a GeoRaster object as invalid with an error code of 13454, the object's metadata is not valid according to the GeoRaster XML schema. If this happens, call the SDO_GEOR.schemaValidate function to find specific locations and other information about the errors.

This function not only validates GeoRaster metadata against the GeoRaster XML schema, but it also enforces restrictions and requirements in the current release that are not described in the XML schema. The following are some of the restrictions and requirements enforced by this function:

- Layer numbers must be from 1 to n where n is the total number of layers.

- The `cellRepresentationType` value must be `UNDEFINED`.

- If `totalBandBlocks` or `bandBlockSize` is specified in the metadata, both must be specified. If there is only one band, no band blocking is allowed.

- The total number of blocks times the blocking size along a dimension must match the dimension size plus padding size, and the size of each cell data BLOB object must match the metadata description in terms of blocking or nonblocking, or of empty or not empty.

- The size and number of GeoRaster data blocks stored in the raster data table must be consistent with the metadata description. For cell data, the number and size of the blocks are checked; the content of the blocks is not checked.

- The only pyramid types supported are `NONE` (no pyramids) and `DECREASE`. (For more information about pyramids, see [Pyramids](georaster-overview-and-concepts.md).)

- The name of the raster data table must not contain spaces, period separators, or mixed-case letters in a quoted string, and all the alphanumeric characters must be uppercase.

- The raster data table must be an object table of SDO_RASTER type, and the table must exist if the GeoRaster object is not blank. To use GeoRaster with Oracle Workspace Manager or Oracle Label Security (OLS), you can define an object view of SDO_RASTER type and use the object view as the raster storage.

- There must be an entry for the GeoRaster object in the ALL_SDO_GEOR_SYSDATA view.

- Each associated bitmap mask must have the correct number of rows in the RDT.

- Any NODATA values and value ranges are in the valid cell value range as designated by the cell depth.

- For an uncompressed GeoRaster object, the size of the BLOB object in each raster block is checked based on the blocking size and cell depth. However, for a compressed GeoRaster object, the size of the BLOB object in each raster block is not checked. Thus, when a compressed GeoRaster object is decompressed, the data might not be valid with respect to size. (A BLOB with zero length is valid; it is an empty raster block.)

- For an uncompressed GeoRaster object, the raster block size of each bitmap mask is checked, based on the blocking size and `1BIT` cell depth. (A BLOB with zero length is valid; it is an empty bitmap mask raster block.)

- A generic functional fitting polynomial model is supported, as described in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md). The limitations on offsets, scales, RMS values, pType, nVars, and number of coefficients of the polynomials are described in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md) and [Table 2-4](georaster-datatypes.md) in [SDO_GEOR_SRS Object Type](georaster-datatypes.md).

- The SRID in the GeoRaster SRS metadata is not checked against the CS_SRS table and is not validated. To validate the SRID, call SDO_GEOR.getModelSRID and SDO_CS.VALIDATE_WKT (the latter described in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_CS-reference.md)). The `verticalSRID` value is not used in the current release.

- Ground control points (GCPs), as the StoredFunction georeferencing model, are supported. The `gcpGeoreferenceModel` in the metadata should follow the definition of the SDO_GEOR_GCPGEOREFTYPE type as described in [SDO_GEOR_GCPGEOREFTYPE Object Type](georaster-datatypes.md), and each GCP should follow the specification of the SDO_GEOR_GCP type as described in [SDO_GEOR_GCP Object Type](georaster-datatypes.md). The number of GCPs is not checked against the `FFMethod` attribute, so you can have the flexibility to add GCPs gradually.

- The `RigorousModel` georeferencing model is not supported. If the functional polynomial coefficients are set, the `modelType` value must be set to `FunctionalFitting` and the `isReferenced` value is set as `TRUE`. If are GCPs are stored in the metadata, the `modelType` value must be set to `StoredFunction`. If both conditions are true, two `modelType` values are added to contain both `StoredFunction` and `FunctionalFitting` values.

- Spatial resolutions can be inconsistent with the affine transformation scales if the GeoRaster object is georeferenced.

- GeoRaster temporal referencing and band referencing are not supported, although in the temporal reference system (TRS) and band reference system (BRS) you can store the beginning and ending date and time, the spectral resolution, the spectral unit, and related descriptive information.

- Only one `layerInfo` element is supported. A layer can be defined only along one dimension, and this dimension must be `BAND`. However, within the `layerInfo` element, the number of `subLayer` elements is limited only by the total number of layers. The layer number for the `objectLayer` elements is 0, and the layer numbers for `subLayer` elements are 1 to n where n is the total number of layers.

- The scaling function, bin function, and statistical data or histogram can be stored in the GeoRaster metadata and must be valid against the XML schema, but the value ranges for these items are not restricted. GeoRaster interfaces that use this metadata are limited. Applications should validate this optional metadata before using it.

- The numbers of colormap values and grayscale mapping values are not restricted, but there must be no duplicate colormap or grayscale values, and the values in each array must be consistent with the `cellDepth` value of the GeoRaster object and must be in ascending order. The value range of the red, green, blue, alpha, and gray components must be integers from 0 to 255.

- Complex `cellDepth` values are not supported.

- This function does not check any external tables (such as a bin table, histogram table, grayscale table, or colormap table) whose names are registered in the XML metadata.

- This function does not validate the spatial extent geometry, or whether or not the spatial relationship between the geometry and the raster data is correct. To validate the spatial extent geometry, use the SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT or SDO_GEOM.VALIDATE_LAYER_WITH_CONTEXT procedure, which are documented in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

- This function does not validate the geometry specified in the `blockMBR` attribute in raster data tables, or whether or not the geometry precisely encloses the raster blocks. (The `blockMBR` attribute is described in [blockMBR Attribute](georaster-datatypes.md).) To validate the `blockMBR` geometries, use the SDO_GEOR.validateBlockMBR function.

If there is no entry for the GeoRaster object in the ALL_SDO_GEOR_SYSDATA view (described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md)), this procedure returns an error stating that the GeoRaster object is not registered. To prevent this error, be sure that the GeoRaster object is inserted into a GeoRaster table and that this table has the required GeoRaster DML trigger created on it. To enable cross-schema access, you must also ensure that users calling this procedure have an appropriate privilege on both the GeoRaster table and the associated raster data table.

#### Examples

The following example validates the GeoRaster objects in a table.

    SELECT t.georid,
           sdo_geor.validategeoraster(t.georaster) isvalid
      from georaster_table t order by georid;

        GEORID ISVALID
    ---------- ----------
             3 TRUE
             4 TRUE

**Parent topic:** SDO_GEOR Package Reference

### 7.158 SDO_GEOR.warp

#### Format

    SDO_GEOR.warp(
         inGeoRaster      IN SDO_GEORASTER,
         pyramidLevel     IN NUMBER,
         outSRS           IN NUMBER,
         cropArea         IN SDO_GEOMETRY,
         dimensionSize    IN SDO_NUMBER_ARRAY,
         layerNumbers     IN VARCHAR2,
         elevationParam   IN VARCHAR2,
         resampleParam    IN VARCHAR2,
         storageParam     IN VARCHAR2,
         outGeoRaster     IN OUT SDO_GEORASTER,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR.warp(
         inGeoRaster      IN SDO_GEORASTER,
         pyramidLevel     IN NUMBER,
         outSRS           IN NUMBER,
         cropArea         IN SDO_GEOMETRY,
         dimensionSize    IN SDO_NUMBER_ARRAY,
         layerNumbers     IN VARCHAR2,
         elevationParam   IN VARCHAR2,
         resampleParam    IN VARCHAR2,
         storageParam     IN VARCHAR2,
         rasterBlob       IN OUT NOCOPY BLOB,
         outArea          OUT SDO_GEOMETRY,
         outWindow        OUT SDO_NUMBER_ARRAY,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL);

#### Description

Perform geometric transformation on the input GeoRaster object to produce an output GeoRaster object with the specified output spatial reference system.

#### Parameters

inGeoRaster
GeoRaster object on which to perform the operation. It must be georeferenced (see [Georeferencing GeoRaster Objects](georaster-database-creation-management.md) and [Advanced Georeferencing](image-processing-virtual-mosaic.md)).

pyramidLevel
Pyramid level of the source GeoRaster object for the operation.

- For BLOB output, this parameter is required.

- For SDO_GEORASTER output, if this parameter is null, all pyramid levels from the input GeoRaster object are processed.

- If the number 0 or greater is specified, only that pyramid level is used for the rectification, producing a result in scale based on that pyramid level image.

outSRS
Coordinate system (spatial reference system) for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If it is null, the output GeoRaster object will have the same SRID as the input GeoRaster object.

cropArea
Defines the shape of the area to be covered by the output image. Areas outside this polygon will be filled with the background value. If this parameter is not specified, no cropping is performed.

dimensionSize
Dimension size array of the GeoRaster object. Defines the extent of the image in cell space.

layerNumbers
String specifying one or more numbers of layers from `inGeoRaster` to be transferred to `outGeoRaster`. Use commas to delimit numbers or ranges, and use a hyphen to indicate a range. Example: `’1,3-5,7’` for layers 1, 3, 4, 5, and 7. If this parameter is null (the default), all the layers will be processed.

elevationParam
A string containing one or more of the elevation parameters `average` (average surface height), `scale` (scale value applied to all `DEM` values), and `offset` (offset applied to all `DEM` values), where the new value is `(value + offset) * scale`. This parameter must be a quoted string that contains one or more keyword=value pairs (for example, `'average=800 scale=3.2808399 offset=10'`). If this parameter is null, 0 is assumed for `average` and `offset`, and 1 is used for `scale`. Any `scale` and `offset` values are ignored if `DEM` is not specified.

The use of the `elevationParam` parameter requires that the input GeoRaster object have a 3D model SRID.

When the input GeoRaster object has a 3D model SRID, the average elevation is important for defining the extents of the output image. If that information is available, it should be specified even if `DEM` is also specified. If the average elevation is not specified, the procedure will calculate an approximate value for the average elevation.

**Note:**

For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

resampleParam
A comma-separated quoted string of keyword=value pairs for specifying resampling parameters. See the Usage Notes for more information.

storaageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
GeoRaster object to hold the result of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`

rasterBlob
BLOB to hold the output reflecting the rectification. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

This procedure has two formats:

- One format generates a GeoRaster object for persistent storage in the database.

- The other format generates a BLOB for temporary storage or immediate use, such as to display data on the screen.

This procedure uses a non-parametric rectification method that takes the georeferencing polynomials from the input GeoRaster object to transform the original image space into the georeferencing polynomials given by the `outSRS` parameter. Therefore, the input GeoRaster object must be georeferenced (see the SDO_GEOR.georeference subprogram).

For more information, see [Image Warping](image-processing-virtual-mosaic.md).

#### Examples

In the following example, the output (generated) GeoRaster object will have the same spatial reference system (coordinate system) as `outSRS`. The input GeoRaster object is a fully georeferenced image.

    DECLARE
      srs sdo_geor_srs;
      gr2 sdo_georaster;
      gr3 sdo_georaster;
      gr4 sdo_georaster;
    BEGIN
      select georaster into gr2 from georaster_table where georid = 2;
      srs := sdo_geor.getSRS(gr2);
      select georaster into gr3 from georaster_table where georid = 3;

      insert into georaster_table values(4, 'Warped',
             sdo_geor.init('warp_rdt',4)) returning raster into gr4;

      sdo_geor.warp( inGeoRaster      => gr3,
                     pyramidLevel     => null,
                     outSRS           => srs,
                     cropArea         => null,
                     dimensionSize    => sdo_number_array(518,518),
                     layerNumbers     => ‘4,5,3’,
                     elevationParam   => `average=300`,
                     resampleParam    => ‘resampling=AVERAGE4’,
                     storageParam     => ‘pyramid=true’,
                     outGeoRaster     => gr4,
                     bgValues         => sdo_number_array(0,0,0),
                     parallelParam    => ‘parellel=4’ );

      update georaster_table set georaster = gr4 where georid = 4;
      commit;
    END;

**Parent topic:** SDO_GEOR Package Reference
