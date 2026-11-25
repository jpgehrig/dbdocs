## 9 SDO_GEOR_AGGR Package Reference

The SDO_GEOR_AGGR package contains subprograms (functions and procedures) for performing advanced large-scale mosaicking, appending, and virtual mosaic operations on GeoRaster objects. This chapter presents reference information, with one or more examples, for each subprogram.

- SDO_GEOR_AGGR.append
- SDO_GEOR_AGGR.getMosaicExtent
- SDO_GEOR_AGGR.getMosaicResolutions
- SDO_GEOR_AGGR.getMosaicStatistics
- SDO_GEOR_AGGR.getMosaicSubset
- SDO_GEOR_AGGR.mosaicSubset
- SDO_GEOR_AGGR.validateForMosaicSubset

### 9.1 SDO_GEOR_AGGR.append

#### Format

    SDO_GEOR_AGGR.append(
         targetGeoRaster    IN OUT SDO_GEORASTER,
         sourceGeoRaster    IN SDO_GEORASTER,
         sourcePyramidLevel IN NUMBER,
         appendParam        IN VARCHAR2,
         bgValues           IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Appends the source GeoRaster object to the target GeoRaster object. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.

#### Parameters

targetGeoRaster
GeoRaster object to be updated. Cannot be the same as `sourceGeoRaster`. (Be sure to make a copy of this object before you update it.)

sourceGeoRaster
GeoRaster object to be appended to `targetGeoRaster`.

sourcePyramidLevel
Pyramid level of the source GeoRaster object to be appended at the target GeoRaster object pyramid Level 0. If NULL, pyramid level 0 is used.

appendParam
A comma-separated quoted string of keyword=value pairs for specifying parameters for the operation. It can contain one or more of the keywords in Table 9-1 in the SDO_GEOR_AGGR.mosaicSubset reference section, unless specified in that table that the keyword is always ignored for SDO_GEOR_AGGR.append.

If a nondefault value for `colorBalance` is specified, it is performed on the source GeoRaster object using the target GeoRaster object's statistics as the reference, and the following keywords (if specified) are ignored: `maxVal`, `minVal`, `std`, and `min`.

bgValues
Background values for filling partially empty raster blocks. It is only useful when the source GeoRaster object has empty raster blocks and the current operation leads to partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth.

#### Usage Notes

**Note:**

Be sure to make a copy of the `targetGeoRaster` object before you call this procedure, because the changes made to this GeoRaster object might not be reversible after the procedure completes.

The source and target GeoRaster objects must have the same number of bands or layers. If the cell depths of the source and target GeoRaster objects are not the same, the cell value of the source GeoRaster object is either expanded or truncated to the cell depth of the target GeoRaster object.

The target GeoRaster object's raster data must be blocked.

There is no change on metadata of target GeoRaster object, except that the extent and the number of blocks are updated and the statistics are removed.

The source GeoRaster object is appended to the target GeoRaster object pyramid level 0. The pyramids of the target GeoRaster object are also updated.

The overlapping areas and gaps of the source and target GeoRaster objects are resolved according to the rules defined in the `appendParam` parameter.

The source GeoRaster object can be located on or touching any side of the target GeoRaster object (that is, it does not have to be on the right or bottom side). The target GeoRaster object will be automatically expanded accordingly.

#### Examples

The following example appends the GeoRaster object with `georid` = 2 to the GeoRaster object with at `georid` = 1.

    declare
        gr1 sdo_georaster;
        gr1 sdo_georaster;
    begin
         select georaster into gr1 from georaster_table where georid = 1 for update;
         select georaster into gr2 from georaster_table where georid = 2;
         sdo_geor_aggr.append(gr1, gr2, 0, null);
         update georaster_table set georaster = gr1 where georid= 1;
         commit;
    end;
    /

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.2 SDO_GEOR_AGGR.getMosaicExtent

#### Format

    SDO_GEOR_AGGR.getMosaicExtent(
         inGeoRasters IN SYS_REFCURSOR,
         outSRID      IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEOMETRY;

or

    SDO_GEOR_AGGR.getMosaicExtent(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         outSRID              IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEOMETRY;

#### Description

Calculates and returns the minimum bounding rectangle (MBR) of the spatial extent of a virtual mosaic or a collection of GeoRaster objects.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

outSRID
Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table. If this parameter is null (the default), 4326 (EPSG SRID value for the WGS 84 (longitude/latitude) coordinate system) is used.

#### Usage Notes

In calculating the spatial extent of a virtual mosaic or a collection of GeoRaster objects, this function tries to use the `spatialExtent` attribute of each GeoRaster object. If the `spatialExtent` attribute is null, the extent of the GeoRaster object is calculated based on the object's metadata.

#### Examples

The following example shows how to get the spatial extent when the virtual mosaic or the collection of GeoRaster objects is a cursor.

    declare
        cur sys_refcursor,
    begin
         open cur for select georaster from georaster_table_1 union all select georaster from georaster_table_2;
         extent := sdo_geor_aggr.getMosaicExtent(cur, 26986);
         close cur;
    end;
    /

The following example shows how to get the mosaic extent by specifying the table column names.

    select sdo_geor_aggr.getMosaicExtent('georaster_table_1, georaster_table_2', 'georaster, georaster', 26986) from dual;

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.3 SDO_GEOR_AGGR.getMosaicResolutions

#### Format

    SDO_GEOR_AGGR.getMosaicResolutions(
         inGeoRasters    IN SYS_REFCURSOR,
          resolutionUnit IN VARCHAR2 DEFAULT NULL
          ) RETURN  SDO_RANGE_ARRAY;;

or

    SDO_GEOR_AGGR.getMosaicResolutions(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
          resolutionUnit      IN VARCHAR2 DEFAULT NULL
          ) RETURN  SDO_RANGE_ARRAY;

#### Description

Returns the resolution range of a virtual mosaic or a collection of GeoRaster objects in a specified unit.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

resolutionUnit
Unit of measure for the returned resolution range. If specified, it must be a quoted string in the format `'unit=``value``'` where value is the unit name value (a valid UNIT_OF_MEAS_NAME value from the SDO_UNITS_OF_MEASURE table). If not specified or null, the returned resolution range is in the unit of `meter`.

#### Usage Notes

The returned resolution range is in the format of SDO_RANGE_ARRAY(SDO_RANGE(`min_x`, `max_x`), SDO_RANGE(`min_y`, `max_y`)). where `min_x`, `max_x` are the minimum and maximum resolution on the x dimension, and `min_y`, `max_y` are the minimum and maximum resolution on the y dimension.

The SDO_RANGE_ARRAY type is defined as `VARRAY(1048576) OF SDO_RANGE`. The SDO_RANGE type is defined as:

    Name                                      Null?    Type
    ----------------------------------------- -------- -------
    LB                                                 NUMBER
    UB                                                 NUMBER

#### Examples

The following example gets the spatial resolution of a virtual mosaic or a collection of GeoRaster objects with the returned values in meters.

    SELECT sdo_geor_aggr.getMosaicResolutions('georatser_table_1, georaster_table_2', 'georaster, georaster', 'unit=meter') FROM DUAL;

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.4 SDO_GEOR_AGGR.getMosaicStatistics

#### Format

    SDO_GEOR_AGGR.getMosaicStatistics(
         inGeoRasters   IN SYS_REFCURSOR,
         skipFactor     IN NUMBER DEFAULT 1,
         genHistogram   IN VARCHAR2 DEFAULT 'FALSE',
         outStatistics  OUT SDO_NUMBER_ARRAYSET,
         outHistograms  OUT SDO_GEOR_HISTOGRAM_ARRAY);

or

    SDO_GEOR_AGGR.getMosaicStatistics(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         skipFactor           IN NUMBER DEFAULT 1,
         genHistogram         IN VARCHAR2 DEFAULT 'FALSE',
         outStatistics        OUT SDO_NUMBER_ARRAYSET,
         outHistograms        OUT SDO_GEOR_HISTOGRAM_ARRAY);

#### Description

Calculates and returns the estimated statistics of a virtual mosaic or a collection of GeoRaster objects.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

skipFactor
Number indicating every nth image to be used during the calculation. For example, if `skipFactor` is 3, then every third image in the source images is used in the statistics calculation. The `skipFactor` parameter can be used to reduce the calculation time for a large image set. The default is 1 (that is, every image is used; no images are skipped).

genHistogram
String (`true` or `false`) whether to return the estimated histogram of the virtual mosaic. The default is `false`.

outStatistics
The returned statistics in the order of the bands of the source images. For each band, if `genHistogram` is `false`, the statistics that are returned are min, max, mean, and std; but if `genHistogram` is `true`, the statistics that are returned are min, max, mean, std, median, and mode.

For example, if the source images have three bands and

- if `genHistogram` is `false`, the `ourStatistics` parameter has the value: `sdo_number_arrayset(sdo_number_array(17.0, 255.0, 154.64, 71.29), sdo_number_array(14.0, 255.0, 155.86, 56.08), sdo_number_array(0.0, 255.0, 98.60, 73.08))`

- if `genHistogram` is `true`, the `ourStatistics` parameter has the value: `sdo_number_arrayset(sdo_number_array(17.0, 255.0, 154.64, 71.29, 112.0, 255.0), sdo_number_array(14.0, 255.0, 155.86, 56.08, 143.0, 255.0), sdo_number_array(0.0, 255.0, 98.60, 73.08, 61.0, 0.0))`

The SDO_NUMBER_ARRAYSET type is defined as `VARRAY(1048576) OF SDO_NUMBER_ARRAY`.

outHistograms
If `genHistogram` is the string `true`, `outHistograms` will contain the returned histograms as an array of type [SDO_GEOR_HISTOGRAM_ARRAY Collection Type](georaster-datatypes.md), with each item containing the histogram for each band.

If `genHistogram` is the string `false`, `outHistograms` will be null.

#### Usage Notes

To calculate the statistics of the source images, the statistics of the source images must be present in the GeoRaster object's metadata.

The source images must have the same number of bands and same `celldepth`.

The returned statistics for non-overlapping source images with `celldepth` less than or equal to `16bit` are accurate calculations; otherwise, the returned statistics are close estimates.

#### Examples

The following example shows how to get the statistics when the virtual mosaic or the collection of GeoRaster objects is a cursor. The `skipFactor` is 1 and `genHistogram` parameter is `false`.

    declare
        cur sys_refcursor,
        outStats sdo_number_arrayset := null;
        outHists sdo_geor_histogram_array := null;
    begin
         open cur for select georaster from georaster_table_1 union all select georaster from georaster_table_2;
         sdo_geor_aggr.getMosaicStatistics(cur, 1, 'false', outStats, outHists);
         close cur;
    end;
    /

The following example shows how to get the statistics by specifying the table column names. The `skipFactor` is 5 and `genHistogram` parameter is `true`.

    declare
        outStats sdo_number_arrayset := null;
        outHists sdo_geor_histogram_array := null;
    begin
         sdo_geor_aggr.getMosaicStatistics('georaster_table_1, georaster_table_2', 'georaster, georaster', 5, 'true', outStats, outHists);
    end;
    /

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.5 SDO_GEOR_AGGR.getMosaicSubset

#### Format

    SDO_GEOR_AGGR.getMosaicSubset(
         inGeoRasters     IN SYS_REFCURSOR,
         pyramidLevel     IN NUMBER,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         referencePoint   IN SDO_GEOMETRY,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         boundaryClip     IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         mosaicParam      IN VARCHAR2,
         rasterBlob       IN OUT NOCOPY BLOB,
         outArea          OUT SDO_GEOMETRY,
         outWindow        OUT SDO_NUMBER_ARRAY,
         storageParam     IN VARCHAR2 DEFAULT NULL,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR_AGGR.getMosaicSubset(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         pyramidLevel         IN NUMBER,
         outSRID              IN NUMBER,
         outModelCoordLoc     IN NUMBER,
         referencePoint       IN SDO_GEOMETRY,
         cropArea             IN SDO_GEOMETRY,
         polygonClip          IN VARCHAR2,
         boundaryClip         IN VARCHAR2,
         layerNumbers         IN VARCHAR2,
         outResolutions       IN SDO_NUMBER_ARRAY,
         resolutionUnit       IN VARCHAR2,
         mosaicParam          IN VARCHAR2,
         rasterBlob           IN OUT NOCOPY BLOB,
         outArea              OUT SDO_GEOMETRY,
         outWindow            OUT SDO_NUMBER_ARRAY,
         storageParam         IN VARCHAR2 DEFAULT NULL,
         bgValues             IN SDO_NUMBER_ARRAY DEFAULT NULL);

or

    SDO_GEOR_AGGR.getMosaicSubset(
         inGeoRasters     IN SYS_REFCURSOR,
         pyramidLevel     IN NUMBER,
         elevationParam   IN VARCHAR2,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         referencePoint   IN SDO_GEOMETRY,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         boundaryClip     IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         mosaicParam      IN VARCHAR2,
         rasterBlob       IN OUT NOCOPY BLOB,
         outArea          OUT SDO_GEOMETRY,
         outWindow        OUT SDO_NUMBER_ARRAY,
         storageParam     IN VARCHAR2 DEFAULT NULL,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceImage   IN SDO_GEORASTER DEFAULT NULL,
         referenceValue1  IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceValue2  IN SDO_NUMBER_ARRAY DEFAULT NULL,
         refHistograms    IN SDO_GEOR_HISTOGRAM_ARRAY DEFAULT NULL);

or

    SDO_GEOR_AGGR.getMosaicSubset(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         pyramidLevel         IN NUMBER,
         elevationParam       IN VARCHAR2,
         outSRID              IN NUMBER,
         outModelCoordLoc     IN NUMBER,
         referencePoint       IN SDO_GEOMETRY,
         cropArea             IN SDO_GEOMETRY,
         polygonClip          IN VARCHAR2,
         boundaryClip         IN VARCHAR2,
         layerNumbers         IN VARCHAR2,
         outResolutions       IN SDO_NUMBER_ARRAY,
         resolutionUnit       IN VARCHAR2,
         mosaicParam          IN VARCHAR2,
         rasterBlob           IN OUT NOCOPY BLOB,
         outArea              OUT SDO_GEOMETRY,
         outWindow            OUT SDO_NUMBER_ARRAY,
         storageParam         IN VARCHAR2 DEFAULT NULL,
         bgValues             IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceImage       IN SDO_GEORASTER DEFAULT NULL,
         referenceValue1      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceValue2      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         refHistograms        IN SDO_GEOR_HISTOGRAM_ARRAY DEFAULT NULL);

#### Description

Performs subsetting over a virtual mosaic or a collection of GeoRaster objects. It performs mosaic operations dynamically for the queried area and returns the required result in a BLOB on-the-fly. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

For information about defining and using MIN_X_RES\$ and MAX_X_RES\$ columns in these tables, see the Usage Notes and [Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$](image-processing-virtual-mosaic.md).

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

pyramidLevel
Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the `outResolutions` parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects is determined by the `outResolutions` parameter.

elevationParam
A string containing the elevation parameter `average` (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, `'average=800'`). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for `average`.

The use of the `elevationParam` parameter requires that the input GeoRaster objects have a 3D model SRID and a nonzero average height.

outSRID
Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

outModelCoordLoc
A value specifying the model location of the base of the area represented by a cell: `0` for `CENTER` or `1` for `UPPERLEFT`. If null, `CENTER` is used.

referencePoint
A point of type SDO_GEOMETRY used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the `referencePoint` and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the `cropArea`, or when the `cropArea` is null, the upper-left corner of the output extent.

cropArea
Crop area definition. If the SDO_GEOMETRY object has a non-null SRID, the coordinates specified in the SDO_GEOMETRY object are in model space and the source GeoRaster objects must be georeferenced; otherwise, the coordinates specified in the SDO_GEOMETRY object are in cell space and the source GeoRaster objects can be georeferenced or non-georeferenced. If `polygonClip` is `FALSE`, the MBR of the `cropArea` is used to crop the mosaicked data. If `polygonClip` is `TRUE`, the geometry of the `cropArea` is used to crop the mosaicked data.

polygonClip
The string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of the `cropArea` to be used to crop the mosaicked data.

boundaryClip
The string `TRUE` or a null value causes the boundary of the virtual mosaic to be used to clip the `cropArea`; the string `FALSE` causes the area that is outside the virtual mosaic but within the `cropArea` to be filled with the background value.

layerNumbers
A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

outResolutions
Resolution requested for the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

resolutionUnit
The unit of the `outResolutions` parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name value (a valid UNIT_OF_MEAS_NAME value from the SDO_UNITS_OF_MEASURE table). This parameter is ignored if `outResolutions` is null.

mosaicParam
A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 9-1 in the SDO_GEOR_AGGR.mosaicSubset reference section.

rasterBlob
BLOB (binary large object) to hold the result of the operation. It must exist or have been initialized before the operation is performed. It is usually a temporary BLOB.

outArea
Geometry object that describes the extent of the output data.

outWindow
An SDO_NUMBER_ARRAY object that identifies the coordinates of the upper-left and lower-right corners of the output window in the cell space. For this function, the upper-left corner of the output window is always (0,0).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md). If this parameter is null, the resulting GeoRaster object has the same storage parameters (`cellDepth`, `interleaving`, and `compression`) as the first encountered source GeoRaster object in the model space (if applicable) or cell space.

If `pyramid=true` is specified, it is ignored for this procedure, but not for SDO_GEOR_AGGR.mosaicSubset.

If `bitmapmask=true` is specified, it is ignored for this procedure.

bgValues
Background cell values for filling partially empty raster blocks (full empty raster blocks are left as empty without filling). They are used to fill the empty areas resulted from the mosaicking operation, such as the areas that are outside of the clipping polygon or the gap areas not covered by any source images. (See also[Empty Raster Blocks](georaster-overview-and-concepts.md).) The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth.

referenceImage
Specifies the reference image used during the color balance operation. If null, it defaults to the source image that is closest to the center of the output mosaic.

referenceValue1
Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

referenceValue2
Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

referenceHistograms
Specifies the reference histograms used during the color balance operation.

#### Usage Notes

The first two formats of the procedure provide the basic color balancing method and assume that the elevation of the output GeoRaster object is 0. The last two formats of the procedure provide more advanced color balancing method using the reference values or reference images, and they let you specify the elevation value for the output GeoRaster object.

The source GeoRaster objects must be prepared images or raster data so that they can be mosaicked. That is, the GeoRaster objects in the virtual mosaic must:

- Not be a mixture of georeferenced and nongeoreferenced objects. Either all of the objects are georeferenced, or none of the objects is georeferenced.

- Have the same number of layers or bands. There is no restriction on the row and column dimension sizes of the source objects.

If the GeoRaster objects to be mosaicked are georeferenced, they are co-located according to their georeferencing information. If the GeoRaster objects are not georeferenced, they are co-located according to their ULTCoordinate values. (The ULTCoordinate is explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

The resulting GeoRaster object's spatial reference metadata information is determined by the `outSRID` and `outResolutions` parameters. If `outSRID` is not specified, the SRID of the first encountered source GeoRaster object is used. If `outResolutions` is not specified, the spatial resolution of the first encountered source GeoRaster object at thespecified pyramid level (`pyramidLevel` parameter) is used. The spatial resolution must be set in the metadata of all the source images.

If any source GeoRaster object has a different SRID from `outSRID` or is not rectified, it is dynamically reprojected or rectified so that the mosaicked GeoRaster object has uniform SRID and spatial resolution values.

If the source GeoRaster objects overlap, data of the overlapping area follows the rules specified in the `mosaicParam` parameter. By default, the cell value of the last encountered source GeoRaster object is used.

The source GeoRaster objects that contributes to the output mosaic are selected by the `cropArea` parameter spatially and  `outResolutions` parameter in resolution wise (resolution selection).

- The `cropArea` parameter is used to query the source GeoRaster objects' spatial extents to determine the GeoRaster objects that are covered by the `cropArea` geometry; thus, a patial index should be built on the `spatialExtent` attribute of the GeoRaster objects.

- The `outResolutions` parameter is used to find the source GeoRaster objects so that the `outResolutions` value is within the resolution range of the source GeoRaster objects. A GeoRaster object's spatial resolution range is determined by the resolution at pyramid level 0 and the resolution at the top pyramid level of the GeoRaster object. It is a half pyramid lower than the pyramid level 0 and a half pyramid level higher than the top pyramid level. For example, if a GeoRaster object has a resolution of 30 meters at pyramid level 0 and a resolution of 960 meters at the top pyramid level 5, this GeoRaster object’s spatial resolution range is between 22.5 meters ((30 + 30/2)/2) and 1440 meters ((960 + 960\*2)/2).

The resolution selection using the `outResolutions` parameter can be speeded up by defining the columns MIN_X_RES\$ and MAX_X_RES\$ (both of type NUMBER) in the tables listed in the `georasterTableNames` parameter, where MIN_X_RES\$ and MAX_X_RES\$ specify the minimum and maximum spatial resolution values, respectively, of the source GeoRaster object. (A B-tree index should be created on the MIN_X_RES\$ and MAX_X_RES\$ columns if there are a large number of source GeoRaster objects.) To take advantage of this feature, the procedure format with the `georasterTableNames` parameter must be used. It also requires that the resolution values stored in the MIN_X_RES\$ and MAX_X_RES\$ columns have the same unit as the unit of the SRID that is stored in the source GeoRaster object’s `spatialExtent` attribute.

The resolution selection can be turned off by setting `resFilter=false` in the `mosaicParam` parameter. When the resolution selection is turned off, the source GeoRaster objects will only be filtered spatially.

If the source GeoRaster objects have empty raster blocks or do not cover the whole area, the empty areas are filled with the values specified in the `bgValues` parameter, or with 0 if the `bgValues` parameter is not specified.

In order to use the `colorBalance` option in `mosaicParam`, you should call [SDO_GEOR.generateStatistics](SDO_GEOR-reference.md) on the source images to generate the image's statistics and store them in the metadata for the source image.

If all source GeoRaster objects are blank and have the same `blankCellValue` value, the resulting `rasterBlob` is filled with the `blankCellValue` value.

For more information, see [Virtual Mosaic](image-processing-virtual-mosaic.md).

#### Examples

The following example gets the subset of a virtual mosaic (defined as two GeoRaster tables) at SRID 32610 with resolution of 30 meters by specifying a `cropArea` window. NODATA is considered at the resampling process (if there is one) and at the overlapping area of the source images.

    declare
      lb blob;
      cropArea sdo_geometry;
      outArea  sdo_geometry := null;
      outWin   sdo_number_array:=null;
      resolutions sdo_number_array;
    begin
        dbms_lob.createTemporary(lb, TRUE);

         cropArea :=  sdo_geometry(2003, 26986, null,
                        sdo_elem_info_array(1, 1003, 3),
                        sdo_ordinate_array(399180, 4247820,
                                           496140,4353900) );
          resolutions := sdo_number_array(30, 30);
         sdo_geor_aggr.getMosaicSubset('georaster_table_1, georaster_table_2',
                     'georaster, georaster',
                     0, 32610, null, null, cropArea,
                     null, null, null, resolutions, null,
                     'nodata=true',
                     lb, outArea, outWin);
        dbms_lob.freeTemporary(lb);
        if outWin is not null then
            dbms_output.put_line('output window: (' || outWin(1) || ',' || outWin(2) ||', ' || outWin(3) || ', ' || outWin(4) || ')');
        end if;
    end;

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.6 SDO_GEOR_AGGR.mosaicSubset

#### Format

    SDO_GEOR_AGGR.mosaicSubset(
         inGeoRasters     IN SYS_REFCURSOR,
         pyramidLevel     IN NUMBER,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         referencePoint   IN SDO_GEOMETRY,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         boundaryClip     IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         mosaicParam      IN VARCHAR2,
         storageParam     IN VARCHAR2,
         outGeoRaster     IN OUT SDO_GEORASTER,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_AGGR.mosaicSubset(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         pyramidLevel         IN NUMBER,
         outSRID             IN NUMBER,
         outModelCoordLoc    IN NUMBER,
         referencePoint      IN SDO_GEOMETRY,
         cropArea            IN SDO_GEOMETRY,
         polygonClip         IN VARCHAR2,
         boundaryClip        IN VARCHAR2,
         layerNumbers        IN VARCHAR2,
         outResolutions      IN SDO_NUMBER_ARRAY,
         resolutionUnit      IN VARCHAR2,
         mosaicParam         IN VARCHAR2,
         storageParam        IN VARCHAR2,
         outGeoRaster        IN OUT SDO_GEORASTER,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam       IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_AGGR.mosaicSubset(
         inGeoRasters     IN SYS_REFCURSOR,
         pyramidLevel     IN NUMBER,
         elevationParam   IN VARCHAR2,
         outSRID          IN NUMBER,
         outModelCoordLoc IN NUMBER,
         referencePoint   IN SDO_GEOMETRY,
         cropArea         IN SDO_GEOMETRY,
         polygonClip      IN VARCHAR2,
         boundaryClip     IN VARCHAR2,
         layerNumbers     IN VARCHAR2,
         outResolutions   IN SDO_NUMBER_ARRAY,
         resolutionUnit   IN VARCHAR2,
         mosaicParam      IN VARCHAR2,
        storageParam      IN VARCHAR2,
         outGeoRaster     IN OUT SDO_GEORASTER,
         bgValues         IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam    IN VARCHAR2 DEFAULT NULL,
         referenceImage   IN SDO_GEORASTER DEFAULT NULL,
         referenceValue1  IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceValue2  IN SDO_NUMBER_ARRAY DEFAULT NULL,
         refHistograms    IN SDO_GEOR_HISTOGRAM_ARRAY DEFAULT NULL);

or

    SDO_GEOR_AGGR.mosaicSubset(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         pyramidLevel        IN NUMBER,
         elevationParam      IN VARCHAR2,
        outSRID             IN NUMBER,
         outModelCoordLoc    IN NUMBER,
         referencePoint      IN SDO_GEOMETRY,
         cropArea            IN SDO_GEOMETRY,
         polygonClip         IN VARCHAR2,
         boundaryClip        IN VARCHAR2,
         layerNumbers        IN VARCHAR2,
         outResolutions      IN SDO_NUMBER_ARRAY,
         resolutionUnit      IN VARCHAR2,
         mosaicParam         IN VARCHAR2,
         storageParam        IN VARCHAR2,
         outGeoRaster        IN OUT SDO_GEORASTER,
         bgValues            IN SDO_NUMBER_ARRAY DEFAULT NULL,
         parallelParam       IN VARCHAR2 DEFAULT NULL,
         referenceImage      IN SDO_GEORASTER DEFAULT NULL,
         referenceValue1     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         referenceValue2     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         refHistograms       IN SDO_GEOR_HISTOGRAM_ARRAY DEFAULT NULL);

#### Description

Performs advanced large-scale mosaicking or subsetting from a virtual mosaic or a collection of GeoRaster objects. The output data is written into a GeoRaster object for persistent storage or other processing. Internal rectification, common point rules, gap filling, and color balancing are performed whenever necessary.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

For information about defining and using MIN_X_RES\$ and MAX_X_RES\$ columns in these tables, see the Usage Notes and [Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$](image-processing-virtual-mosaic.md).

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

pyramidLevel
Pyramid level of the source GeoRaster objects for the operation. This parameter is used when the `outResolutions` parameter is not specified; otherwise, the pyramid level of the source GeoRaster objects involved in the mosaic is determined by the `outResolutions` parameter.

The `pyramidLevel` parameter and the option `pyramid=true` in the `storageParam` parameter are valid only when the source GeoRaster objects have the same resolution on pyramid level 0. 

If the `outResolutions` parameter is not null, the `pyramidLevel` parameter is ignored.

elevationParam
A string containing the elevation parameter `average` (average surface height). This parameter must be a quoted string that contains a keyword=value pair (for example, `'average=800'`). This parameter specifies the elevation of the output GeoRaster object. If this parameter is null, 0 is assumed for `average`.

The use of the `elevationParam` parameter requires that the input GeoRaster objects have a 3D model SRID and a nonzero average surface height.

outSRID
Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

outModelCoordLoc
A value specifying the model location of the base of the area represented by a cell: `0` for `CENTER` or `1` for `UPPERLEFT`. If null, `CENTER` is used.

referencePoint
A point of type SDO_GEOMETRY used as the reference point of mosaic. If a point is specified, the mosaicked image's upper left corner aligns with the reference point, that is, the distance between the `referencePoint` and the upper-left corner of the output will have an integer number of pixels. If this parameter is null, the reference point implicitly uses the upper-left corner of the `cropArea`, or when the `cropArea` is null, the upper-left corner of the output extent.

cropArea
Crop area definition. If the SDO_GEOMETRY object has a non-null SRID, the coordinates specified in the SDO_GEOMETRY object are in model space and the source GeoRaster objects must be georeferenced; otherwise, the coordinates specified in the SDO_GEOMETRY object are in cell space and the source GeoRaster objects can be georeferenced or non-georeferenced. If `polygonClip` is `FALSE`, the MBR of the `cropArea` is used to crop the mosaicked data. If `polygonClip` is `TRUE`, the geometry of the `cropArea` is used to crop the mosaicked data.

polygonClip
The string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of the `cropArea` to be used to crop the mosaicked data.

boundaryClip
The string `TRUE` or a null value causes the boundary of the virtual mosaic to be used to clip the `cropArea`; the string `FALSE` causes the area that is outside the virtual mosaic but within the `cropArea` to be filled with the background value

layerNumbers
A string identifying the logical layer numbers on which the operation or operations are to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4). If not specified, the mosaic result contains the same number of bands as the source GeoRaster objects.

outResolutions
Resolution of the output GeoRaster data. If null, the default is the resolution of the first encountered GeoRaster object. See the Usage Notes for details.

resolutionUnit
The unit of the `outResolutions` parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name value (a valid UNIT_OF_MEAS_NAME value from the SDO_UNITS_OF_MEASURE table). This parameter is ignored if `outResolutions` is null.

mosaicParam
A comma-separated quoted string of keyword=value pairs for specifying mosaic parameters. It can contain one or more of the keywords in Table 9-1.

**Note:**

For any numbers in string (VARCHAR2) parameters to GeoRaster subprograms, the period (.) must be used for any decimal points regardless of the locale.

Table 9-1 mosaicParam Keywords

| Keyword             | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cbreference         | (Supported with the procedure formats that include the `referenceImage`, `referenceValue1`, /`referenceValue2`, and `refHistograms` parameters.) Specifies the source of the reference value used in `colorBalance`. Can have one of the following values:<br>• `VALUE`: The reference value is specified in the `referenceValue1` and `referenceValue2` parameters.<br>• `IMAGE`: The reference value is retrieved from the `referenceImage` parameter.<br>• `OVERLAP`: the reference value is derived from the overlapping area of the source images.<br>• (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| colorBalance        | Specifies the method for color balancing. Can have one of the following values:<br>• `NONE` (the default): No color balancing is performed.<br>• `LINEARSTRETCHING`: Use the linear stretching method to stretch the source image’s cell values to the reference minimum and maximum value.<br>• If the `cbreference` parameter is `VALUE`, then parameter `referenceValue1` has the reference minimum values and parameter `referenceValue2` has the reference maximum values. If the `referenceValue1` or `referenceValue2` is null, default values 0 and 255 are used, respectively. If the `referenceValue1` or `referenceValue2` has only one value, it is applied to all the bands; otherwise, the reference values are corresponding to each band. Thus, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands in the source images.<br>• If the `cbreference` parameter is `IMAGE`, then the minimum and maximum values of `referenceImage` are used as the reference.<br>• If the `cbreference` parameter is not specified, the `minVal` and `maxVal` parameters are used to specify the minimum and maximum reference values, respectively.<br>• `STATISTICMATCHING`: Stretch the source images to match the reference statistics.<br>• If the `cbreference` parameter is `VALUE`, then parameter `referenceValue1` has the reference mean value and parameter `referenceValue2` has the reference standard deviation value. If the `referenceValue1` or `referenceValue2` is null, default values 128 and 100 are used, respectively. If the `referenceValue1` or `referenceValue2` has only one value, it is applied to all the bands; otherwise, the reference values are corresponding to each band. Thus, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands in the source images.<br>• If the `cbreference` parameter is `IMAGE`, then the reference image’s mean and standard deviation values are used for the matching.<br>• If the `cbreference` parameter is `OVERLAP`, then the mean and standard deviation values are derived from the overlapping area.<br>• If the `cbreference` parameter is not specified, the `std` and `mean` parameters are used to specify the reference statistics.<br>• `HISTOGRAMMATCHING`: Use the reference histogram as the source image’s histogram.<br>• If the `cbreference` parameter is `VALUE`, then parameter `referenceHistogram` defines the reference histograms for each band. If only one reference histogram is specified, it is applied to all the bands.<br>• If the `cbreference` parameter is `IMAGE`, then the referencce image’s histograms for each band are used as the reference for matching<br>• If the `cbreference` parameter is `OVERLAP`, then histograms at the overlapping area are used to derive the matching. |
| commonPointRule     | Specifies the method for getting the cell value at the overlapping area. Can have one of the following values:<br>• `START`: The value from the first encountered GeoRaster object is used.<br>• `END`: The value from the last encountered GeoRaster object is used.<br>• `LATEST`: The value from the GeoRaster object that has the most recent `EndDateTime` in the metadata is used.<br>• `OLDEST`: The value from the GeoRaster object that has the oldest `EndDateTime` in the metadata is used.<br>• `CTC`: The call value from the GeoRaster object that is closest to the center of the output window is used.<br>• `HIGH`: The maximum cell value of all the overlapping GeoRaster objects is used.<br>• `LOW`: The minimum cell value of all the overlapping GeoRaster objects is used.<br>• `AVERAGE`: The average of all cell values from the overlapping GeoRaster objects is used.<br>• `HIGHRES`: The value from the GeoRaster object that has the highest spatial resolution is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| fillGap             | Specifies whether or not to fill the narrow gap between source images. `TRUE` causes any gap that is less than or equal to 2 pixels wide to be filled with the nearest-neighbor pixel value. `FALSE` causes any gaps to be filled with zero or `bgValue`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| maxVal              | Ignored if `colorBalance` is not `LINEARSTRETCHING` or if the `cbreference` keyword is specified; otherwise, specifies the highest value in the range of the linear stretching method. Defaults to 255. (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| mean                | Ignored if `colorBalance` is not `STATISTICMATCHING` or if the `cbreference` keyword is specified; otherwise, specifies the reference mean of the statistic matching method. (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| minVal              | Ignored if `colorBalance` is not `LINEARSTRETCHING` or if the `cbreference` keyword is specified; otherwise, specifies the lowest value in the range of the linear stretching method. Defaults to 0. (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| nodata              | Specifies whether or not to consider NODATA (NODATA value or NODATA bitmap mask) when handling the overlap area or when resampling is performed. The default value is `FALSE`.<br>When handling the overlap area, `nodata=TRUE` causes any NODATA values cells not to be involved in the overlap area calculation; `nodata=FALSE` causes all the overlapped cells to be involved in the overlap area calculation.<br>When resampling is performed and the resampling method is `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`, if any of the cells involved in the resampling has a NODATA value, then `nodata=TRUE` causes the result of the resampling to be a NODATA value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| resampling          | Specifies the resampling method (if resampling is involved or rectification is needed) to be used during the mosaic operation. Can have one of the following values: `NN` (the default), `BILINEAR`, `BIQUADRATIC`, `CUBIC`, `AVERAGE4`, or `AVERAGE16`. For more information, see [Resampling and Interpolation](georaster-overview-and-concepts.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| resamplingTolerance | Specifies the tolerance for not doing resampling when the source GeoRaster objects are not perfectly aligned. The value should be between 0 and 0.5, where the unit is pixel or cell (for example, `0.5` meaning one-half pixel or cell). If not specified, `0.5` is used, which means no resampling will occur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| resFilter           | Specifies whether or not to filter the source GeoRaster objects to select only the GeoRaster object that is in the range of the output resolution (`outResolution` parameter). `TRUE` (the default) enables resolution filtering. `FALSE` disables resolution filtering, causing all the source GeoRaster objects to be involved in the mosaicking process. (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| std                 | Ignored if `colorBalance` is not `STATISTICMATCHING` or if the `cbreference` keyword is specified; otherwise, specifies the reference standard deviation for the statistic matching method. (Always ignored if specified in `appendParam` for SDO_GEOR_AGGR.append.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md). If this parameter is null, the resulting GeoRaster object has the same storage parameters (`blockSize`, `cellDepth`, `interleaving`, and `compression`) as the first encountered source GeoRaster object in the model space (if applicable) or cell space. However, it is recommended that you specify the storage parameters, particularly the blocking size, as appropriate for the size of the output mosaic, unless you want the mosaic to have the same storage parameters as those of the first encountered GeoRaster object to be mosaicked.

If `pyramid=true` is specified, the pyramids of the source GeoRaster objects are mosaicked when the `outResolutions` parameter is null and the `pyramidLevel` parameter is not null. The maximum pyramid level of the result GeoRaster object is the minimal value of the maximum pyramid level of the source GeoRaster objects. By default, `pyramid=false`, and thus the pyramids are not mosaicked.

If `bitmapmask=true` is specified, the bitmap masks of the source GeoRaster objects are mosaicked also.

outGeoRaster
GeoRaster object to hold the result of the operation. Cannot be the same as any source GeoRaster object.

bgValues
Background cell values for filling partially empty raster blocks (full empty raster blocks are left as empty without filling). They are used to fill the empty areas resulted from the mosaicking operation, such as the areas that are outside of the clipping polygon or the gap areas not covered by any source images. (See also[Empty Raster Blocks](georaster-overview-and-concepts.md).) The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit operation. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting mosaicked GeoRaster object explicitly in order to roll back the operation.

referenceImage
Specifies the reference image used during the color balance operation. If null, it defaults to the first image from the query.

referenceValue1
Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

referenceValue2
Specifies the reference value or values used during the color balance operation. The meaning of the values is determined by the color balance method.

referenceHistograms
Specifies the reference histograms used during the color balance operation.

#### Usage Notes

The first two formats of the procedure provide the basic color balancing method and assume that the elevation of the output GeoRaster object is 0. The last two formats of the procedure provide more advanced color balancing method using the reference values or reference images, and they let you specify the elevation value for the output GeoRaster object.

The source GeoRaster objects must be prepared images or raster data so that they can be mosaicked. That is, the GeoRaster objects to be mosaicked must:

- Not be a mixture of georeferenced and nongeoreferenced objects. Either all of the objects are georeferenced, or none of the objects is georeferenced.

- Have the same number of layers or bands. There is no restriction on the row and column dimension sizes of the source objects.

If the GeoRaster objects to be mosaicked are georeferenced, they are co-located according to their georeferencing information. If the GeoRaster objects are not georeferenced, they are co-located according to their ULTCoordinate values. (The ULTCoordinate is explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

The resulting GeoRaster object's spatial reference metadata information is determined by the `outSRID` and `outResolutions` parameters. If `outSRID` is not specified, the SRID of the first encountered source GeoRaster object is used. If `outResolutions` is not specified, the spatial resolution of the first encountered source GeoRaster object at specified pyramid level (`pyramidLevel` parameter) is used. The spatial resolution must be set in the metadata of all the source images.

If any source GeoRaster object has a different SRID from `outSRID` or is not rectified, it is dynamically reprojected or rectified so that the mosaicked GeoRaster object has uniform SRID and spatial resolution values.

If the source GeoRaster objects overlap, data of the overlapping area follows the rules specified in the `mosaicParam` parameter. By default, the cell value of the last encountered source GeoRaster object is used.

The source GeoRaster objects that contributes to the output mosaic are selected by the `cropArea` parameter spatially and  `outResolutions` parameter in resolution wise (resolution selection).

- The `cropArea` parameter is used to query the source GeoRaster objects' spatial extents to determine the GeoRaster objects that are covered by the `cropArea` geometry,. Thus, a spatial index should be built on the `spatialExtent` attribute of the GeoRaster objects.

- The `outResolutions` parameter is used to find the source GeoRaster objects so that the `outResolutions` value is within the resolution range of the source GeoRaster objects. A GeoRaster object's spatial resolution range is determined by the resolution at pyramid level 0 and the resolution at the top pyramid level of the GeoRaster object. It is a half pyramid lower than the pyramid level 0 and a half pyramid level higher than the top pyramid level. For example, if a GeoRaster object has a resolution of 30 meters at pyramid level 0 and a resolution of 960 meters at the top pyramid level 5, this GeoRaster object’s spatial resolution range is between 22.5 meters ((30 + 30/2)/2) and 1440 meters ((960 + 960\*2)/2).

The resolution selection using the `outResolutions` parameter can be speeded up by defining the columns MIN_X_RES\$ and MAX_X_RES\$ (both of type NUMBER) in the tables listed in `georasterTableNames` parameter, where MIN_X_RES\$ and MAX_X_RES\$ specify the minimum and maximum spatial resolution values, respectively, of the source GeoRaster object. (A B-tree index should be created on the MIN_X_RES\$ and MAX_X_RES\$ columns if there are a large number of source GeoRaster objects.)  To take advantage of this feature, the procedure format with the `georasterTableNames` parameter must be used. It also requires that the resolution values stored in the MIN_X_RES\$ and MAX_X_RES\$ columns have the same unit as the unit of the SRID that is stored in the source GeoRaster object spatialExtent attribute.

The resolution selection can be turned off by setting `resFilter=false` in the `mosaicParam` parameter. When the resolution selection is turned off, the source GeoRaster objects will only be filtered spatially.

If the source GeoRaster objects have empty raster blocks or do not cover the whole area, the mosaicked result GeoRaster object may have empty or partially empty raster blocks (see [Empty Raster Blocks](georaster-overview-and-concepts.md)). A result raster block that is not covered by any of the source GeoRaster objects is kept empty. Any partially empty raster blocks are filled with the values specified in the `bgValues` parameter, or with 0 if the `bgValues` parameter is not specified.

If the `bitmapmask` parameter is set to `true` in the `storageParam` string, the bitmap masks are mosaicked. By default, the bitmap masks are not mosaciked. Note that the bitmap mask may also be considered as NODATA; and if they are, see the NODATA keyword in Table 9-1.

In order to use the `colorBalance` option in `mosaicParam`, you should you should call [SDO_GEOR.generateStatistics](SDO_GEOR-reference.md) on the source images to generate the image's statistics and store them in the metadata for the source image.

If all source GeoRaster objects are blank and have the same `blankCellValue` value, the resulting GeoRaster object is blank and has that `blankCellValue` value; otherwise, the resulting GeoRaster object is not blank.

The GeoRaster object to contain the results of the mosaic operation (`georaster` parameter) must not be any of the source GeoRaster objects (the objects on which the mosaic operation is performed).

The mosaic operation performs internal commit operations at regular intervals, and thus it cannot be rolled back. If the operation is interrupted, dangling raster blocks may exist in the raster data table. You can handle dangling raster blocks by maintaining GeoRaster objects and system data in the database, as explained as explained in [Maintaining GeoRaster Objects and System Data in the Database](georaster-database-creation-management.md).

For more information, see [Large-Scale Image Mosaicking](image-processing-virtual-mosaic.md) and [Virtual Mosaic](image-processing-virtual-mosaic.md).

#### Examples

The following example shows how to mosaic the source images at the specified `pyramidLevel`. This requires that all the source images have the same spatial resolutions and have a pyramid generated on the specified `pyramidLevel`.

    DECLARE
    gr sdo_georaster;
    BEGIN
        INSERT INTO georaster_table (georid, georaster)
            VALUES (10, SDO_GEOR.init('RDT_1',10))
            RETURNING georaster INTO gr;

    -- mosaic at pyramidLevel=1,output SRID defaults to
    -- the SRID of the first source image, fillGap=true.
    -- Enable parallel processing with parallel degree set as 4.
        SDO_GEOR_AGGR.mosaicSubset('georaster_table_1, georaster_table_2',
                       'georaster, georaster',
                       1, null, null, null, null, null,
                       null, null, null, null, null,
                       'fillGap=true',
                       'blocking=optimalpadding, blocksize=(512,512,3)',
                       gr, null, 'parallel=4');

        UPDATE georaster_table SET georaster = gr WHERE georid=10;
        COMMIT;
    END;
    /

The following example shows how to mosaic the first band of the source images with the `outSRID`, `outResolutions` and `cropArea` parameters. The overlapping area is determined by the `commonPointRule` mosaic parameter.

    DECLARE
    gr             sdo_georaster;
    outSRID        number;
    cropArea       sdo_geometry;
    resolutions    sdo_number_array;
    resolutionUnit varchar2(16);
    bgValues       sdo_number_array;
    layerNumbers   varchar2(8);
    mosaicParam    varchar2(64);
    BEGIN
        INSERT INTO georaster_table (georid, georaster)
            VALUES (10, SDO_GEOR.init('RDT_1',10))
            RETURNING georaster INTO gr;

        -- set the parameters
        outSRID := 4326;
        cropArea :=  sdo_geometry(2003, 26986, null,
                  sdo_elem_info_array(1, 1003, 3),
                  sdo_ordinate_array(399180, 4247820,
                                     496140,4353900) );
        resolutions := sdo_number_array(30, 30);
        resolutionUnit := ‘unit=meter’;
        layerNumbers := ‘0’;
        bgValues := sdo_number_array(0);
        mosaicParam := ‘commonPointRule=high, nodata=true’;

    -- Enable parallel processing with parallel degree set as 4.
        SDO_GEOR_AGGR.mosaicSubset('georaster_table_1, georaster_table_2',
                       'georaster, georaster',
                       null, null, outSRID, null, null, cropArea,
                       null, null, layerNumbers, resolutions,
                       resolutionUnit, mosaicParam,
                       'blocking=optimalpadding, blocksize=(512,512,3)',
                       gr, bgValues, 'parallel=4');

        UPDATE georaster_table SET georaster = gr WHERE georid=10;
        commit;
    END;
    /

**Parent topic:** SDO_GEOR_AGGR Package Reference

### 9.7 SDO_GEOR_AGGR.validateForMosaicSubset

#### Format

    SDO_GEOR_AGGR.validateForMosaicSubset(
         inGeoRasters    IN SYS_REFCURSOR,
         outSRID         IN NUMBER,
         outResolutions  IN SDO_NUMBER_ARRAY,
         resolutionUnit  IN VARCHAR2,
         resultTableName IN VARCHAR2);

or

    SDO_GEOR_AGGR.validateForMosaicSubset(
         georasterTableNames  IN VARCHAR2,
         georasterColumnNames IN VARCHAR2,
         outSRID              IN NUMBER,
         outResolutions       IN SDO_NUMBER_ARRAY,
         resolutionUnit       IN VARCHAR2,
         resultTableName      IN VARCHAR2);

#### Description

Checks if it is feasible to do mosaicking or subset query operations over a virtual mosaic or a large collection of GeoRaster objects. Any validation errors and notes are stored in a user-created result table.

#### Parameters

inGeoRasters
Source GeoRaster objects in a cursor.

georasterTableNames
Names (comma-separated) of the tables containing the source GeoRaster objects.

georasterColumnNames
Names (comma-separated) of the columns of type SDO_GEORASTER in tables corresponding to the table names in `georasterTableNames`.

outSRID
Coordinate system for the output GeoRaster object. Must be either null or a value from the SRID column of the MDSYS.CS_SRS table.

outResolutions
Resolution of the output GeoRaster data. If null, the default is the resolution of the first encountered source GeoRaster object.

resolutionUnit
The unit of the `outResolutions` parameter. If null, the default is the unit of the output SRID. If specified, it must be a quoted string in the format "unit=value" where value is the unit name value (a valid UNIT_OF_MEAS_NAME value from the SDO_UNITS_OF_MEASURE table). This parameter is ignored if `outResolutions` is null.

resultTableName
Name of the validation result table. This table must already exist, and it must have the following column definitions:

    time timestamp,
    type varchar2(16),
    description varchar2(512),
    table_name varchar2(32),
    column_name varchar2(1024),
    rdt_table_name varchar2(32),
    raster_id number

#### Usage Notes

The following considerations apply to the `resultTableName` parameter value:

- If the specified table does not exist, an error is generated.

- If the parameter is not specified or is specified as null, the procedure throws an error at the first validation error found; otherwise, the procedure puts all the validation errors in the table and completes without error.

- If the specified table is not empty, the procedure appends rows to the existing data in the table; and if there is a unique constraint on any column and if the newly appended data has the same value as existing data in that constrained column, an error is generated.

- The TYPE column of the table contains a string indicating the type of issue, such as `ERROR` (something that must be fixed) or `NOTE` (information that may or may not require some action). The DESCRIPTION column provides details about the issue.

This procedure performs the following validation checks:

- The source GeoRaster objects must have the same band dimension size.

- The source GeoRaster objects must have consistent georeference status, that is, either all are georeferenced or all are not georeferenced.

- If reprojection or rectification to be performed when doing the mosaic, the operation must be feasible.

#### Examples

The following example checks if a mosaic operation is possible. Any validation errors are stored in the predefined table MOSAIC_ERROR.

    EXECUTE sdo_geor_aggr.validateForMosaicSubset('georaster_table_1, georaster_table_2', 'georaster, georaster', 26986, sdo_number_array(30, 30), 'unit=meter', 'mosaic_error');

    -- Check the validation results:
    SELECT table_name table, column_name column, rdt_table_name rdt, raster_id rid, type, description FROM mosaic_error ORDER BY time;

    TABLE       COLUMN    RDT   RID TYPE  DESCRIPTION
    ----------  --------  ----- --- ----- ---------------------------------------
    GEORASTER_1 GEORASTER RDT_1   2 ERROR The source georaster object is
                                          not georeferenced.

**Parent topic:** SDO_GEOR_AGGR Package Reference
