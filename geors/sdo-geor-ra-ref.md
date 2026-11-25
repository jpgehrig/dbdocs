## 12 SDO_GEOR_RA Package Reference

The SDO_GEOR_RA package contains subprograms (functions and procedures) for raster algebra and analytic operations related to GeoRaster. This chapter presents reference information, with one or more examples, for each subprogram.

To use the subprograms in ths chapter, you should junderstand the main concepts and techniques described in [Raster Algebra and Analytics](raster-algebra-and-analytics.md).

- SDO_GEOR_RA.classify
- SDO_GEOR_RA.diff
- SDO_GEOR_RA.findCells
- SDO_GEOR_RA.isOverlap
- SDO_GEOR_RA.over
- SDO_GEOR_RA.rasterMathOp
- SDO_GEOR_RA.rasterUpdate
- SDO_GEOR_RA.stack

### 12.1 SDO_GEOR_RA.classify

#### Format

Operation on a Single GeoRaster Object

    SDO_GEOR_RA.classify(
         inGeoRaster   IN SDO_GEORASTER,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.classify(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         inGeoRaster  IN SDO_GEORASTER,
         cropArea     IN SDO_NUMBER_ARRAY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'false',
         nodataValue  IN NUMBER default 0);

    SDO_GEOR_RA.classify(
         inGeoRaster  IN SDO_GEORASTER,
         cropArea     IN SDO_GEOMETRY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue  IN NUMBER default 0,
         polygonClip  IN VARCHAR2 DEFAULT 'FALSE');

Operation on an Array of GeoRaster Objects

    SDO_GEOR_RA.classify(
         georArray     IN SDO_GEORASTER_ARRAY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_NUMBER_ARRAY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.classify(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_GEOMETRY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         georArray    IN SDO_GEORASTER_ARRAY,
         cropArea     IN SDO_NUMBER_ARRAY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue  IN NUMBER default 0);

    SDO_GEOR_RA.classify(
         georArray    IN SDO_GEORASTER_ARRAY,
         cropArea     IN SDO_GEOMETRY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue  IN NUMBER default 0,
         polygonClip  IN VARCHAR2 DEFAULT 'FALSE');

Operation on GeoRaster Objects Specified by a Cursor

    SDO_GEOR_RA.classify(
         inGeoRasters  IN SYS_REFCURSOR,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_NUMBER_ARRAY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.classify(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_GEOMETRY,
         expression    IN VARCHAR2,
         rangeArray    IN SDO_NUMBER_ARRAY,
         valueArray    IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.classify(
         inGeoRasters IN SYS_REFCURSOR,
         cropArea     IN SDO_NUMBER_ARRAY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue  IN NUMBER default 0);

    SDO_GEOR_RA.classify(
         inGeoRasters IN SYS_REFCURSOR,
         cropArea     IN SDO_GEOMETRY,
         expression   IN VARCHAR2,
         rangeArray   IN SDO_NUMBER_ARRAY,
         valueArray   IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue  IN NUMBER default 0,
         polygonClip  IN VARCHAR2 DEFAULT 'FALSE');

#### Description

Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.

There are several formats for each of three input GeoRaster object or objects specification options (SDO_GEORASTER, SDO_GEORASTER_ARRAY, SYS_REEFCURSOR). Within each group of formats, you can specify no crop area or a crop area of SDO_NUMBER_ARRAY or SDO_GEOMETRY. For an SDO_GEOMETRY crop area, you can specify a polygon clip option, and the output can be either a GeoRaster object or a BLOB.

#### Parameters

inGeoRaster
Input GeoRaster object.

georArray
An array of GeoRaster objects. The data type is SDO_GEOR_ARRAY, which is defined as `VARRAY(10485760) OF SDO_GEORASTER`.

inGeoRasters
Cursor (SYS_REFCURSOR type) for the input GeoRaster objects.

cropArea
Crop area definition. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as a rectangular crop area to generate the output GeoRaster object. If the parameter `polygonClip` is `TRUE`, then only cells within the crop area geometry are processed, and all cells outside the crop area geometry are set to zero (0). If the parameter `polygonClip` is `FALSE`, then all cells within the minimum bounding rectangle are processed.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

expression
An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

rangeArray
A number array that defines ranges for classifying cell values. The array must contain at least one element.

valueArray
A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in `rangeArray` (that is, its length must be `rangeArray`+1).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

nodata
The string `TRUE` specifies if any cell value involved in the expression evaluation has a NODATA value, the expression is evaluated as a NODATA value; thus, the corresponding cells in the output GeoRaster object are to be set to the value specified for the `nodataValue` parameter. The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

nodataValue
The value used to set NODATA cells if the `nodata` parameter value is the string `TRUE`.

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` geometry to be used to process the data; the string `FALSE` or a null value causes the minimum bounding rectangle (MBR) of the`cropArea` geometry to be used to process the data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

This procedure generates a new raster either in a GeoRaster object or a single BLOB, based on the input GeoRaster object or objects and the `expression` parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, `expression` is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object:

    if  (value of expression < rangeArray[0])
        cellValue=valueArray[0]
    else if (value of expression >= rangeArray[n-1])
        cellValue=valueArray[n]
    else if rangeArray[m-1] <= value of expression < rangeArray[m]
         cellValue=valueArray[m]

In the `expression` calculation:

- Length of `rangeArray` is n

- Length of `valueArray` is n+1

- 0 \< m \< n-1

For more information, see [Raster Algebra Language](raster-algebra-and-analytics.md).

There are several formats for each of the input GeoRaster object or objects specification options (SDO_GEORASTER, SDO_GEORASTER_ARRAY, SYS_REFCURSOR). Within each group of formats, you can specify no crop area or a crop area of SDO_NUMBER_ARRAY or SDO_GEOMETRY. For an SDO_GEOMETRY crop area, you can specify a polygon clip option, and the output can be either a GeoRaster object or a BLOB.

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

#### Examples

The following example classifies cell values based on the cell values of the first layer. The output is a GeoRaster object.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      rangeArray SDO_NUMBER_ARRAY;
      valueArray SDO_NUMBER_ARRAY;
    BEGIN
      rangeArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180);
      valueArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180,190);
      select georaster into geor from georaster_table where georid = 1;
      insert into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.classify(geor,'{0}',rangeArray,valueArray,null,geor1);
      update georaster_table set georaster = geor1 where georid = 5;
      commit;
    END;
    /

The following example classifies cell values based on the cell values of the first layer. The output is a BLOB.

    DECLARE
      geor       SDO_GEORASTER;
      out_lob    BLOB;
      outArea sdo_geometry;
      outWindow sdo_number_array;
      rangeArray SDO_NUMBER_ARRAY;
      valueArray SDO_NUMBER_ARRAY;
    BEGIN
      rangeArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180);
      valueArray:=sdo_number_array(70,80,90,100,110,120,130,140,150,160,170,180,190);
      select georaster into geor from georaster_table where georid = 1;
      dbms_lob.create_temporary(out_lob, TRUE);
      sdo_geor_ra.classify(geor,'{0}',rangeArray,valueArray,null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.2 SDO_GEOR_RA.diff

#### Format

    SDO_GEOR_RA.diff(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.diff(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         ploygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.diff(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER default 0;

    SDO_GEOR_RA.diff(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER default 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE');

#### Description

Generates a new GeoRaster object by performing the diff operation (explained in the Usage Notes). The new raster is either in a GeoRaster object or a single BLOB.

#### Parameters

geor
First input GeoRaster object.

geor1
Second input GeoRaster object.

cropArea
Crop area definition. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as a rectangular crop area to generate the output GeoRaster object. If the parameter `polygonClip` is `TRUE`, then only cells within the crop area geometry are processed, and all cells outside the crop area geometry are set to zero (0). See also the Usage Notes for [SDO_GEOR.reproject](SDO_GEOR-reference.md) for SDO_SRID requirements.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

nodata
The string `TRUE` specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the `nodataValue` parameter. The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

nodataValue
The value used to set NODATA cells if the `nodata` parameter value is the string `TRUE`.

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of `cropArea` to be used to crop the output image.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

This procedure generates a new GeoRaster object by taking two input GeoRaster objects and applying the over operation: specifically, for each cell value in each layer, if the values in the two input objects are different, the value on the first input is output, but if the values in the two input objects are the same, the output is zero.

The two input GeoRaster objects must have same dimension size and same number of bands; otherwise, the ORA-13397 error is generated.

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

For more information, see [Logical Operations](raster-algebra-and-analytics.md).

#### Examples

The following example performs the diff operation on the two input GeoRaster objects. The output is a GeoRaster object.

    declare
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geom       sdo_geometry;
    begin
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      select georaster into geor2 from georaster_table where georid = 102 for update;
      geom:=null;
      sdo_geor_ra.diff(geor,geor1,geom,null,geor2);
      update georaster_table set georaster = geor2 where georid = 102;
    end;
    /

The following example performs the diff operation on the two input GeoRaster objects. The output is a GeoRaster object. The output is a BLOB.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      out_lob    BLOB;
      outArea    sdo_geometry;
      outWindow  sdo_number_array;
      geom       sdo_geometry;
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      dbms_lob.create_temporary(out_lob, TRUE);
      geom:=null;
      sdo_geor_ra.diff(geor,geor1,geom,null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.3 SDO_GEOR_RA.findCells

#### Format

    SDO_GEOR_AGGR.findCells(
         inGeoRaster   IN SDO_GEORASTER,
         condition     IN VARCHAR2,
         storageParam  IN VARCHAR2
         outGeoRaster  OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_AGGR.findCells(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         condition     IN VARCHAR2,
         storageParam  IN VARCHAR2
         outGeoRaster  OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_AGGR.findCells(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         condition     IN VARCHAR2,
         storageParam  IN VARCHAR2
         outGeoRaster  OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_AGGR.findCells(
         inGeoRaster  IN SDO_GEORASTER,
         cropArea     IN SDO_GEOMETRY,
         condition    IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’;

    SDO_GEOR_AGGR.findCells(
         inGeoRaster  IN SDO_GEORASTER,
         cropArea     IN SDO_GEOMETRY,
         condition    IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’,
         polygonClip  IN VARCHAR2 DEFAULT ‘FALSE’);

#### Description

Generates a new raster either in a GeoRaster object or a single BLOB based on the input GeoRaster object, but masking all cells that do not satisfy the `condition` parameter specification.

#### Parameters

inGeoRaster
Input GeoRaster object.

cropArea
Crop area definition. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as a rectangular crop area to generate the output GeoRaster object; see also the Usage Notes for [SDO_GEOR.reproject](SDO_GEOR-reference.md) for SDO_SRID requirements.. If the parameter `polygonClip` is `TRUE`, then only cells within the crop area geometry are processed, and all cells outside the crop area geometry are set to zero (0). If the parameter `polygonClip` is `FALSE`, then all cells within the minimum bounding rectangle are processed.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

condition
An expression string used to filter out cells. (See the Usage Notes for more information.).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

nodata
The string `TRUE` means that the original values for any NODATA cells in the GeoRaster object are kept, and NODATA values are considered in the `condition` parameter evaluation. If any cell value involved in the `condition` parameter evaluation has a NODATA value, the `condition` parameter is evaluated as FALSE (see the Usage Notes regarding the `condition` parameter). The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` geometry to be used to process the data; the string `FALSE` or a null value causes the minimum bounding rectangle (MBR) of the`cropArea` geometry to be used to process the data.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

This procedure generates a new raster either in a GeoRaster object or a single BLOB based on the input GeoRaster object and the `condition` parameter, which is `booleanExpr`, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If `condition` is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, `bgValues` are filled for the cell in the output GeoRaster object

For more information, see [Raster Algebra Language](raster-algebra-and-analytics.md).

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

#### Examples

The following example changes cell values to default background values 0, if cell value of the second layer is less than or equal to 200.

    DECLARE
      geor  SDO_GEORASTER;
      geor1 SDO_GEORASTER;
    BEGIN
      select georaster into geor from georaster_table where georid = 1;
      insert into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.findcells(geor, '{1}>200',null,geor1);
      update georaster_table set georaster = geor1 where georid = 5;
      commit;
    END;
    /

The following example changes cell values to default background values 0, if cell value of the second layer is less than or equal to 200. The output is in a BLOB..

    DECLARE
      geor  SDO_GEORASTER;
      out_lob    BLOB;
      outArea    sdo_geometry;
      outWindow  sdo_number_array;
    BEGIN
      select georaster into geor from georaster_table where georid = 1;
      dbms_lob.create_temporary(out_lob, TRUE);
      sdo_geor_ra.findcells(geor, '{1}>200',null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

The following example uses a geometry object (`geom`) as the input `cropArea`.

    DECLARE
      geor       SDO_GEORASTER;
      geor0      SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geom       SDO_GEOMETRY;
    BEGIN
      geom:= sdo_geometry(2003,82394, NULL,
                             sdo_elem_info_array(1, 1003, 1),
                             sdo_ordinate_array(21783.775, 1008687.9,
                                               18783.775, 966687.905,
                                               63783.775, 966687.905,
                                               81783.775, 990687.905,
                                               21783.775, 1008687.9));
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      sdo_geor_ra.findcells(geor,geom,'({1}=42)','blocking=true, blocksize=(256,256,3)',geor1,null,'false');
      update georaster_table set georaster = geor1 where georid = 101;
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.4 SDO_GEOR_RA.isOverlap

#### Format

    SDO_GEOR.isOverlap(
         georaster1 IN SDO_GEORASTER,
         georaster2 IN SDO_GEORASTER,
         tolerance  IN NUMBER DEFAULT 0.5
         ) RETURN VARCHAR2;

or

    SDO_GEOR_RA.isOverlap(
         georArray IN SDO_GEORASTER_ARRAY,
         tolerance IN NUMBER DEFAULT 0.5
         ) RETURN VARCHAR2;

or

    SDO_GEOR_RA.isOverlap(
         geor_cur  IN SYS_REFCURSOR,
         tolerance IN NUMBER DEFAULT 0.5
         ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if two or more GeoRaster objects overlap, or `FALSE` if two or more GeoRaster objects do not overlap. (See the Usage Notes for the logic used to determine of two GeoRaster objects, whether georeferenced or not, overlap.)

#### Parameters

georaster1
GeoRaster object.

georaster2
GeoRaster object.

georArray
An array of GeoRaster objects. The data type is SDO_GEOR_ARRAY, which is defined as `VARRAY(10485760) OF SDO_GEORASTER`.

geor_cur
Cursor (SYS_REFCURSOR type) for the input GeoRaster objects.

tolerance
Tolerance value used to determine if two cells in the cell space overlap in the model space. The value should be between 0 and 1, and the unit is cell. For example, 0.5 (the default) means one-half cell, namely, that two cells overlap if the distance between them in 0.5 cell or less.

#### Usage Notes

The GeoRaster objects being compared for overlap must be either all georeferenced or all non-georeferenced.

The following logic is applied to determine if two GeoRaster objects overlap:

1.  If the row or column dimension size of two GeoRaster objects is different, then return `'FALSE'`. Otherwise, continue to the next step.

2.  Check if both GeoRaster objects are georeferenced.

    1.  If one is georeferenced and the other one is not, then return `'FALSE'`.

    2.  If both are non-georeferenced, and if the `ultCoordinate` of both GeoRaster objects is the same, then return `'TRUE'`; else, return `'FALSE'`.

    3.  If both are georeferenced, go to the next step.

3.  Check the `pType`, `nVars`, `order`, and `nCoefficients` values (explained in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md)) of the `p`, `q`, `r`, and `s` polynomials. If any are different, then return 'FALSE'; else, go to the next step.

4.  Calculate the upper-left, upper-right, lower-left, and lower-right four points from cell space to model space. If the distance of corresponding points of the two GeoRaster objects is within the tolerance value (converted from cell space to model space), then return `'TRUE'`; else, return `'FALSE`'.

The raster algebra functions of GeoRaster require the raster layers from different GeoRaster objects have the same size and completely overlap each other. Before you apply raster algebra operations over two or more GeoRaster objects or perform other operations, you can use the SDO_GEOR_RA.isOverlap function to determine if the GeoRaster objects are of the same size and cover the same ground area.

#### Examples

The following examples check if two GeoRaster objects overlap. (They use two different formats of the function.)

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
    BEGIN

      SELECT georaster INTO geor FROM georaster_table WHERE georid = 1;
      SELECT georaster INTO geor1 FROM georaster_table WHERE georid = 30;
      dbms_output.put_line(sdo_geor_ra.isOverlap(geor,geor1,0.5));
    END;
    /

    DECLARE
      mycursor  sys_refcursor;
    BEGIN
      OPEN mycursor FOR
        SELECT georaster FROM georaster_table WHERE georid = 1 or georid=30;
      dbms_output.put_line(sdo_geor_ra.isOverlap(mycursor,0.5));
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.5 SDO_GEOR_RA.over

#### Format

    SDO_GEOR_RA.over(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.over(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         ploygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.over(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0;

    SDO_GEOR_RA.over(
         geor          IN SDO_GEORASTER,
         geor1         IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         storageParam  IN VARCHAR2,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0,
         polygonClip   IN VARCHAR2 DEFAULT ‘FALSE’);

#### Description

Generates a new raster, either in a GeoRaster object or in a single BLOB, by performing the over operation (explained in the Usage Notes).

#### Parameters

geor
First input GeoRaster object.

geor1
Second input GeoRaster object.

cropArea
Crop area definition. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as a rectangular crop area to generate the output GeoRaster object. If the parameter `polygonClip` is `TRUE`, then only cells within the crop area geometry are processed, and all cells outside the crop area geometry are set to zero (0). See also the Usage Notes for [SDO_GEOR.reproject](SDO_GEOR-reference.md) for SDO_SRID requirements.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

nodata
The string `TRUE` specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the `nodataValue` parameter. The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

nodataValue
The value used to set NODATA cells if the `nodata` parameter value is the string `TRUE`.

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of `cropArea` to be used to crop the output image.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

This procedure generates a new raster, either in a GeoRaster object or in a single BLOB, by taking two input GeoRaster objects and applying the over operation: specifically, each cell in each layer in the output raster will contain the value from the corresponding cell in first input GeoRaster object if that value is not zero; otherwise, it will contain the value of the corresponding cell in the second GeoRaster object.

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

For more information, see [Logical Operations](raster-algebra-and-analytics.md).

#### Examples

The following example performs the over operation on the two input GeoRaster objects. The output is in a GeoRaster object.

    DECLARE
      geor       MDSYS.SDO_GEORASTER;
      geor1      MDSYS.SDO_GEORASTER;
      geor2      MDSYS.SDO_GEORASTER;
      geom       mdsys.sdo_geometry;
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      select georaster into geor2 from georaster_table where georid = 102 for update;
      geom:=null;
      mdsys.sdo_geor_ra.over(geor,geor1,geom,null,geor2);
      update georaster_table set georaster = geor2 where georid = 102;
    END;
    /

The following example performs the over operation on the two input GeoRaster objects. The output is in a BLOB.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      out_lob    BLOB;
      outArea    sdo_geometry;
      outWindow  sdo_number_array;
      geom       sdo_geometry;
    BEGIN
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101;
      dbms_lob.create_temporary(out_lob, TRUE);
      geom:=null;
      sdo_geor_ra.over(geor,geor1,geom,null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.6 SDO_GEOR_RA.rasterMathOp

#### Format

Operation on a Single GeoRaster Object

    SDO_GEOR_RA.rasterMathOp(
         inGeoRaster   IN SDO_GEORASTER,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.rasterMathOp(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0;

    SDO_GEOR_RA.rasterMathOp(
         inGeoRaster   IN SDO_GEORASTER,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT  BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0,
         polygonClip   IN VARCHAR2 DEFAULT ‘FALSE’);

Operation on an Array of GeoRaster Objects

    SDO_GEOR_RA.rasterMathOp(
         georArray     IN SDO_GEORASTER_ARRAY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_NUMBER_ARRAY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.rasterMathOp(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0;

    SDO_GEOR_RA.rasterMathOp(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0,
         polygonClip   IN VARCHAR2 DEFAULT ‘FALSE’);

Operation on GeoRaster Objects Specified by a Cursor

    SDO_GEOR_RA.rasterMathOp(
         inGeoRasters  IN SYS_REFCURSOR,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_NUMBER_ARRAY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.rasterMathOp(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0;

    SDO_GEOR_RA.rasterMathOp(
         inGeoRasters  IN SYS_REFCURSOR,
         cropArea      IN SDO_GEOMETRY,
         operation     IN SDO_STRING2_ARRAY,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         rasterBlob    IN OUT BLOB,
         outArea       OUT SDO_GEOMETRY,
         outWindow     OUT SDO_NUMBER_ARRAY,
         nodata        IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue   IN NUMBER default 0,
         polygonClip   IN VARCHAR2 DEFAULT ‘FALSE’);

Operation on All Corresponding Cells of Each Layer

    SDO_GEOR_RA.rasterMathOp(
         georaster0    IN SDO_GEORASTER,
         georaster1    IN SDO_GEORASTER,
         constant      IN NUMBER,
         operator      IN PLS_INTEGER,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         georaster0    IN SDO_GEORASTER,
         georaster1    IN SDO_GEORASTER,
         cropArea      IN SDO_NUMBER_ARRAY,
         constant      IN NUMBER,
         operator      IN PLS_INTEGER,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.rasterMathOp(
         georaster0    IN SDO_GEORASTER,
         georaster1    IN SDO_GEORASTER,
         cropArea      IN SDO_GHEOMETRY,
         constant      IN NUMBER,
         operator      IN PLS_INTEGER,
         storageParam  IN VARCHAR2 DEFAULT NULL,
         outGeoRaster  IN OUT SDO_GEORASTER,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterMathOp(
         georaster0   IN SDO_GEORASTER,
         georaster1   IN SDO_GEORASTER,
         cropArea     IN SDO_GEOMETRY,
         constant     IN NUMBER,
         operator     IN PLS_INTEGER,
         storageParam IN VARCHAR2 DEFAULT NULL,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue  IN NUMBER default 0;

    SDO_GEOR_RA.rasterMathOp(
         georaster0   IN SDO_GEORASTER,
         georaster1   IN SDO_GEORASTER,
         cropArea     IN SDO_GEOMETRY,
         constant     IN NUMBER,
         operator     IN PLS_INTEGER,
         storageParam IN VARCHAR2 DEFAULT NULL,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         bgValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue  IN NUMBER default 0,
         polygonClip  IN VARCHAR2 DEFAULT ‘FALSE’);

#### Description

Performs a raster algebra operation on one or more GeoRaster objects, including general mathematical, statistical, casting, logical, and relational operations or combinations of them.

#### Parameters

inGeoRaster
Input GeoRaster object.

georArray
An array of GeoRaster objects. The data type is SDO_GEOR_ARRAY, which is defined as `VARRAY(10485760) OF SDO_GEORASTER`.

inGeoRasters
Cursor (SYS_REFCURSOR type) for the input GeoRaster objects.

georaster0
The left operand.

georaster1
The right operand.

cropArea
Crop area definition. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as a rectangular crop area to generate the output GeoRaster object. If the parameter `polygonClip` is `TRUE`, then only cells within the crop area geometry are processed, and all cells outside the crop area geometry are set to zero (0). See also the Usage Notes for [SDO_GEOR.reproject](SDO_GEOR-reference.md) for SDO_SRID requirements.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

operation
An array of `arithmeticExpr` expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The data type is SDO_STRING2_ARRAY, which is defined as `VARRAY(2147483647) OF VARCHAR2(4096)`.

The syntax for the `arithmeticExpr` expressions is explained in [Raster Algebra Language](raster-algebra-and-analytics.md).

constant
Constant value for some operators (see the `operator` parameter), such as `addConst` and `divConstant`.

operator
One of the following math operators, which are defined in the SDO_GEOR_RA package:

    OPERATOR_ABSOLUTE
    OPERATOR_ADD
    OPERATOR_ADDCONST
    OPERATOR_DIVIDE
    OPERATOR_DIVIDECONST
    OPERATOR_EXP
    OPERATOR_INVERT
    OPERATOR_LOG
    OPERATOR_MULTIPLY
    OPERATOR_MULTIPLYCONST
    OPERATOR_SUBTRACT
    OPERATOR_SUBTRACTCONST

For the definitions of these operators, see the Usage Notes.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

bgValues
Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

nodata
The string `TRUE` specifies that if there are any NODATA cells in the operands of the math operation, the operation result is evaluated as a NODATA value; thus, the corresponding cells in the output GeoRaster object are to be set to the value specified for the `nodataValue` parameter. The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

nodataValue
The value used to set NODATA cells if the `nodata` parameter value is the string `TRUE`.

polygonClip
Ignored if `cropArea` is null. Otherwise, the string `TRUE` causes the `cropArea` value to be used to crop the mosaicked data; the string `FALSE` or a null value causes the MBR of `cropArea` to be used to crop the output image.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

This procedure has 20 formats, which can be considered as 4 groups of 5 formats each:

- Operation on a single GeoRaster object
- Operation on an array of GeoRaster objects
- Operation on GeoRaster objects specified by a cursor (SYS_REFCURSOR type)
- Operation on all corresponding cells of each layer or one or two GeoRaster objects

Within each group, the options include specifying a crop areas of type SDO_NUMBER_ARRAY or SDO_GEOMETRY, and for an SDO_GEOMETRY crop area, whether to use the crop area’s geometry object or the MBR of that object. The output raster can be in a GeoRaster object or a single BLOB.

The first three groups of formats are used to generate a new raster from layers of one or more input GeoRaster objects based on the `operation` parameter. For example, the following example generates a new GeoRaster object that has three layers, and each layer's value is the cell value of the input GeoRaster object minus 10:

    sdo_geor_ra.rasterMathOp(geor,SDO_STRING2_ARRAY('{0,0}-10','{0,1}-10','{0,2}-10'),null,geor1);

The fourth group of formats applies a mathematical operation on all corresponding cells of each layer of input GeoRaster objects, and generates a new GeoRaster object with the same dimension size as the first input GeoRaster object (`geoRaster0`). The two input GeoRaster objects must have same row/column/band dimension size.

For the fourth group of formats, when the output raster is a GeoRaster object, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object; when the output raster is in a BLOB, all pyramids and masks are removed from the output.

For the `operator` parameter, the operators have the following definitions:

    OPERATOR_ABSOLUTE  :
     if (src[x][y][b] < 0) {
         dst[x][y][b] = -src[x][y][b];
     } else {
         dst[x][y][b] =  src[x][y][b];
     }

    OPERATOR_ADD
       dst[x][y][b]=src1[x][y][b]+src2[x][y][b]
    OPERATOR_ADDCONST
       dst[x][y][b]=src[x][y][b] +constant   --constant is the third parameter

    OPERATOR_DIVIDE
       dst[x][y][b]=src1[x][y][b]/src2[x][y][b]

    OPERATOR_DIVIDECONST
       dst[x][y][b]=src[x][y][b]/constant   --constant is the third parameter

    OPERATOR_EXP
       dst[x][y][b]=exp(src[x][y][b])

    OPERATOR_INVERT        :
       Inverts the cell values: dst[x][y][b]=-src[x][y][b]

    OPERATOR_LOG           :
       dst[x][y][b]=log(src[x][y][b])

    OPERATOR_MULTIPLY
       dst[x][y][b]=src1[x][y][b]*src2[x][y][b]

    OPERATOR_MULTIPLYCONST
       dst[x][y][b]=src[x][y][b]*constant   --constant is the third parameter

    OPERATOR_SUBTRACT
       dst[x][y][b]=src1[x][y][b]-src2[x][y][b]

    OPERATOR_SUBTRACTCONST
       dst[x][y][b]=src[x][y][b]-constant   --constant is the third parameter

For more information about the raster algebra language, see [Raster Algebra Language](raster-algebra-and-analytics.md).

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

#### Examples

The following example adds the constant 10 to all cell values of the input GeoRaster object. The output is a GeoRaster object.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
    BEGIN

      select georaster into geor from georaster_table where georid = 1;
      insert into georaster_table values (5, sdo_geor.init('rdt_1', 5)) returning georaster into geor1;
      sdo_geor_ra.rasterMathOp(geor,null,10,sdo_geor_ra.OPERATOR_ADDCONST,null,geor1);
      update georaster_table set georaster = geor1 where georid = 5;
      commit;
    END;
    /

The following example adds the constant 10 to all cell values of the input GeoRaster object. The output is a BLOB.

    DECLARE
      geor       SDO_GEORASTER;
      out_lob    BLOB;
      outArea    sdo_geometry;
      outWindow  sdo_number_array;
    BEGIN

      select georaster into geor from georaster_table where georid = 1;
      dbms_lob.create_temporary(out_lob, TRUE);
      sdo_geor_ra.rasterMathOp(geor,null,10,sdo_geor_ra.OPERATOR_ADDCONST,null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);

    END;
    /

The following example generates a new three-layer GeoRaster object from three layers of the input GeoRaster object, and each cell value in the new GeoRaster object is the value of the corresponding "old" cell divided by 2.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geo_array  SDO_GEORASTER_ARRAY;
    BEGIN
      select georaster into geor from georaster_table where georid = 2;
      insert into georaster_table values (20, sdo_geor.init('rdt_1', 20)) returning georaster into geor1;
      geo_array:=SDO_GEORASTER_ARRAY(geor);
      sdo_geor_ra.rasterMathOp(geo_array,SDO_STRING2_ARRAY('{0,0}/2','{0,1}/2','{0,2}/2'),null,geor1);
      update georaster_table set georaster = geor1 where georid = 20;
      commit;
    END;
    /

The following example performs a raster math operation with a geometry object as the crop area.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geom       SDO_GEOMETRY;
      geo_array  SDO_GEORASTER_ARRAY;
    BEGIN
      geom:= sdo_geometry(2003,82394, NULL,
                             sdo_elem_info_array(1, 1003, 1),
                             sdo_ordinate_array(21783.775, 1008687.9,
                                                     18783.775, 966687.905,
                                                     63783.775, 966687.905,
                                                     81783.775, 990687.905,
                                                     21783.775, 1008687.9));
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      geo_array:=SDO_GEORASTER_ARRAY(geor);
      mdsys.sdo_geor_ra.rasterMathOp(geo_array,geom,SDO_STRING2_ARRAY('{0,0}/2','{0,1}/2','{0,2}/2'),null,geor1);
      update georaster_table set georaster = geor1 where georid = 101;
      commit;
    END;
    /

**See Also:**

- [Logical Operations](raster-algebra-and-analytics.md) for examples on applying raster logical operations
- [Raster Data Scaling and Offsetting](raster-algebra-and-analytics.md) for examples on performing cell data scaling and offsetting operations
- [Example 5-23](raster-algebra-and-analytics.md) for mapping cell values from one data type to another using casting operations
- [Example 5-24](raster-algebra-and-analytics.md) for performing complex cartographic modeling

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.7 SDO_GEOR_RA.rasterUpdate

#### Format

    SDO_GEOR_RA.rasterUpdate(
         geoRaster     IN OUT SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         conditions    IN SDO_STRING2_ARRAY,
         vals          IN SDO_STRING2_ARRAYSET,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterUpdate(
         geoRaster     IN OUT SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         targetArea    IN SDO_NUMBER_ARRAY,
         conditions    IN SDO_STRING2_ARRAY,
         vals          IN SDO_STRING2_ARRAYSET,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_RA.rasterUpdate(
         geoRaster     IN OUT SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         targetArea    IN SDO_GEOMETRY,
         conditions    IN SDO_STRING2_ARRAY,
         vals          IN SDO_STRING2_ARRAYSET,
         bgValues      IN SDO_NUMBER_ARRAY DEFAULT NULL,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

#### Description

Updates all cells for which the `conditions` specification is true, using values calculated from the `vals` specification.

#### Parameters

geoRaster
GeoRaster object that is used for input and for output (updating based on specified conditions).

pyramidLevel
Pyramid level to be updated. If this parameter is null, all pyramid levels are updated.

targetArea
Target area definition. If the data type is SDO_GEOMETRY, then if the parameter `polygonClip` is `TRUE`, only cells within the target area geometry are updated, and all cells outside the target area geometry keep original values; but if the parameter `polygonClip` is `FALSE`, all cells in the MBR of the target area geometry are updated.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

conditions
An array of `booleanExpr` expression strings used to select cells. (See the Usage Notes for more information.) The data type is SDO_STRING2_ARRAY, which is defined as `VARRAY(2147483647) OF VARCHAR2(4096)`.

vals
An array or arrays of `arithmeticExpr` expressions, with the outer array corresponding to each condition and the inner array corresponding to each layer. The data type is SDO_STRING2_ARRAYSET, which is defined as `VARRAY(2147483647) OF SDO_STRING2_ARRAY`.

bgValues
Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, `SDO_NUMBER_ARRAY(1,5,10)` fills the first band with 1, the second band with 5, and the third band with 10. The default `bgValues` are zero (0).

The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

nodata
The string `TRUE` means that the original values for any NODATA cells in the GeoRaster object are not to be updated, and NODATA values are considered in the `conditions` parameter evaluation. If any cell value involved in the `conditions` parameter evaluation has a NODATA value, the `conditions` parameter is evaluated as FALSE (See the Usage Notes regarding the `conditions` parameter). The string `FALSE` (the default) causes cells with NODATA values to be considered as regular cells and thus eligible for updating. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

polygonClip
Ignored if `targetArea` is null. Otherwise, the string `TRUE` causes the `targetArea` geometry value to be used to update raster cell values; the string `FALSE` or a null value causes the MBR of `targetArea` geometry to be used to update raster cell values.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish.

This procedure selects cells from the specified GeoRaster object based on `booleanExpr` strings specified in the `conditions` parameter, and updates corresponding cell values by calculating `arithmeticExpr` expression strings specified in the vals parameter. For example, if:

    conditions = SDO_STRING2_ARRAY('{0}=48','{0}=108')
    vals = SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123'))

Then:

- For all cells whose first layer value equals 48, their first, second, and third layer values are set to 123,54,89, respectively.

- For all cells whose first layer value equals 108, their first, second, and third layer values are set to 98,56,123, respectively.

For more information, see [Raster Algebra Language](raster-algebra-and-analytics.md).

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

#### Examples

The following example updates all cells for which the `conditions` specification is true, using values calculated from the `vals` specification.

    DECLARE
      geor SDO_GEORASTER;
    BEGIN
      select georaster into geor from georaster_table where georid = 1;
      sdo_geor_ra.rasterUpdate(geor,0,SDO_STRING2_ARRAY('(abs({0}-{1})=48)&({2}-{1}=-101)','2*{0}-{1}/3=108'),SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')));
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference

### 12.8 SDO_GEOR_RA.stack

#### Format

    SDO_GEOR_RA.stack(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_NUMBER_ARRAY,
         layerList     IN SDO_NUMBER_ARRAY,
         method        IN VARCHARs,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         parallelParam IN VARCHAR2 DEFAULT NULL);

    SDO_GEOR_RA.stack(
         georArray     IN SDO_GEORASTER_ARRAY,
         cropArea      IN SDO_GEOMETRY,
         layerList     IN SDO_NUMBER_ARRAY,
         method        IN VARCHARs,
         storageParam  IN VARCHAR2,
         outGeoRaster  IN OUT SDO_GEORASTER,
         nodata        IN VARCHAR2 DEFAULT 'FALSE',
         nodataValue   IN NUMBER DEFAULT 0,
         polygonClip   IN VARCHAR2 DEFAULT 'FALSE',
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    DO_GEOR_RA.stack(
         georArray    IN SDO_GEORASTER_ARRAY,
         cropArea     IN SDO_GEOMETRY,
         layerList    IN SDO_NUMBER_ARRAY,
         method       IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue  IN NUMBER default 0,;

    SDO_GEOR_RA.stack(
         georArray    IN SDO_GEORASTER_ARRAY,
         cropArea     IN SDO_GEOMETRY,
         layerList    IN SDO_NUMBER_ARRAY,
         method       IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT NOCOPY BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY,
         nodata       IN VARCHAR2 DEFAULT ‘FALSE’,
         nodataValue  IN NUMBER default 0,
         polygonClip  IN VARCHAR2 DEFAULT ‘FALSE’);

#### Description

Generates a single-layer raster either in a GeoRaster object or a single BLOB whose cell values are a local statistics value of a list of layers of the input GeoRaster array. The input layers are specified by the `layerList` parameter, and the statistics method is specified by the `method` parameter.

#### Parameters

georArray
An array of GeoRaster objects. The data type is SDO_GEOR_ARRAY, which is defined as `VARRAY(10485760) OF SDO_GEORASTER`.

cropArea
Crop area definition. If the SDO_GEOMETRY object has a non-null SRID, the source GeoRaster objects must be georeferenced; otherwise, the source GeoRaster objects can be georeferenced or non-georeferenced. If `polygonClip` is `FALSE`, the MBR of the `cropArea` is used to crop the data. If `polygonClip` is `TRUE`, the geometry of the `cropArea` is used to crop the data.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

layerList
A number array to specify which bands of the input GeoRaster objects are used to compute statistics value for output. For example, if `georArray` specifies three GeoRaster objects `geor1`,`geor2`,`geor3`, which have 2,3,4 bands respectively, a layer list {0,3,7} is used to specify three bands as follows:

- The first band of the first GeoRaster object `geor1`

- The second band of the second GeoRaster object `geor2`

- The third band of the third GeoRaster object `geor3`

method
A string to specify what local statistics value should be returned. It should be one of the following values: `max`, `min`, `median`, `mean`, `std`, `sum`, `minority`, `majority`, `diversity`.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
Output GeoRaster object.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

nodata
The string `TRUE` specifies that if there are any NODATA cells in the specified `layerList` parameter, the corresponding cells in the output GeoRaster object are to be set to the value specified for the `nodataValue` parameter. The string `FALSE` (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in [NODATA Values and Value Ranges](georaster-overview-and-concepts.md).

nodataValue
The value used to set NODATA cells if the `nodata` parameter value is the string `TRUE`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

Specifying `parallelParam` means that you cannot roll back the results of this procedure, as explained in the Usage Notes.

#### Usage Notes

All of the input GeoRaster objects must have same dimension size; otherwise, the ORA-13397 error is generated.

If you specify `parallelParam`, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.

#### Examples

The following example performs the stack operation on two input GeoRaster objects. The output is a GeoRaster object.

    DECLARE
      geor       SDO_GEORASTER;
      geor1      SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geom       mdsys.sdo_geometry;
    BEGIN
      geom:= sdo_geometry(2003,82394, NULL,
                   sdo_elem_info_array(1, 1003, 1),
                   sdo_ordinate_array(20283.775, 1011087.9,
                                      18783.775, 1008687.9,
                                      21783.775, 1008687.9,
                                      22683.775+0.001, 1009587.9+0.001,
                                      20283.775, 1011087.9));
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor2 from georaster_table where georid = 102;
      select georaster into geor1 from georaster_table where georid = 101 for update;
      sdo_geor_ra.stack(SDO_GEORASTER_ARRAY(geor,geor2),geom,SDO_NUMBER_ARRAY(3,5),'max',null,geor1,'false',0,'TRUE');
      update georaster_table set georaster = geor1 where georid = 101;
    END;
    /

The following example performs the stack operation on two input GeoRaster objects. The output is a BLOB.

    DECLARE
      geor       SDO_GEORASTER;
      geor2      SDO_GEORASTER;
      geom       sdo_geometry;
      out_lob    BLOB;
      outArea    sdo_geometry;
      outWindow  sdo_number_array;
    BEGIN
      geom:= null;
      select georaster into geor from georaster_table where georid = 100;
      select georaster into geor2 from georaster_table where georid = 102;
      dbms_lob.create_temporary(out_lob, TRUE);
      sdo_geor_ra.stack(SDO_GEORASTER_ARRAY(geor,geor2),geom,SDO_NUMBER_ARRAY(3,5),'max',null,out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_RA Package Reference
