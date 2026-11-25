## 13 SDO_GEOR_UTL Package Reference

The SDO_GEOR_UTL package contains subprograms (functions and procedures) for utility operations related to GeoRaster. This chapter presents reference information, with one or more examples, for each subprogram.

- SDO_GEOR_UTL.calcOptimizedBlockSize
- SDO_GEOR_UTL.calcRasterNominalSize
- SDO_GEOR_UTL.calcRasterStorageSize
- SDO_GEOR_UTL.calcSurfaceArea
- SDO_GEOR_UTL.clearReportTable
- SDO_GEOR_UTL.createDMLTrigger
- SDO_GEOR_UTL.createReportTable
- SDO_GEOR_UTL.disableReport
- SDO_GEOR_UTL.dropReportTable
- SDO_GEOR_UTL.emptyBlocks
- SDO_GEOR_UTL.enableReport
- SDO_GEOR_UTL.fillEmptyBlocks
- SDO_GEOR_UTL.generateColorRamp
- SDO_GEOR_UTL.generateGrayRamp
- SDO_GEOR_UTL.getAllStatusReport
- SDO_GEOR_UTL.getMaxMemSize
- SDO_GEOR_UTL.getReadBlockMemSize
- SDO_GEOR_UTL.getProgress
- SDO_GEOR_UTL.getStatusReport
- SDO_GEOR_UTL.getWriteBlockMemSize
- SDO_GEOR_UTL.isReporting
- SDO_GEOR_UTL.makeRDTNamesUnique
- SDO_GEOR_UTL.recreateDMLTriggers
- SDO_GEOR_UTL.renameRDT
- SDO_GEOR_UTL.setClientID
- SDO_GEOR_UTL.setMaxMemSize
- SDO_GEOR_UTL.setReadBlockMemSize
- SDO_GEOR_UTL.setSeqID
- SDO_GEOR_UTL.setWriteBlockMemSize

### 13.1 SDO_GEOR_UTL.calcOptimizedBlockSize

#### Format

    SDO_GEOR_UTL.calcOptimizedBlockSize(
         dimensionSize IN SDO_NUMBER_ARRAY,
         blockSize     IN OUT SDO_NUMBER_ARRAY,
         pyramidLevel  IN number default 0);

#### Description

Calculates an optimal `blockSize` value that will use less padding space in the GeoRaster object storage, based on the GeoRaster dimension sizes and the user-specified block size values.

#### Parameters

dimensionSize
Dimension size array of the GeoRaster object.

blockSize
Block size array, which holds the user-specified block size values and into which the procedure outputs the adjusted optimal block size values.

pyramidLevel
Maximum pyramid level. The default value is 0.

#### Usage Notes

This procedure enables you to give desired block size values (which may not be optimal), automatically adjust them, and then determine the block size array values for a specified GeoRaster dimension size array that will be optimal for reducing the amount of padding space in GeoRaster object storage. The adjustment is always made around the user-specified values. For more information, see the explanations of the `blocking` and `blockSize` keywords in [Table 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

In the `dimensionSize` and `blockSize` parameter values, specify the values for the dimensions in this order: row, column, band.

An exception is generated if the input `dimensionSize` or `blockSize` parameter contains any invalid values.

#### Examples

The following example calculates and displays an optimal block size value, based on a specified dimension size array of (12371,11261,13) and a specified block size array of (512,512,5). Note that the optimal `rowBlockSize` value returned is 538 as opposed to the original value of 512, and the optimal `bandBlockSize` value returned is 1 as opposed to the original value of 5.

    DECLARE
      dimensionSize    sdo_number_array;
      blockSize        sdo_number_array;
    BEGIN
      dimensionSize:=sdo_number_array(12371,11261,13);
      blockSize:=sdo_number_array(512,512,5);
      sdo_geor_utl.calcOptimizedBlockSize(dimensionSize,blockSize);
      dbms_output.put_line('Optimized rowBlockSize = '||blockSize(1));
      dbms_output.put_line('Optimized colBlockSize = '||blockSize(2));
      dbms_output.put_line('Optimized bandBlockSize = '||blockSize(3));
    END;
    /
    Optimized rowBlockSize = 538
    Optimized colBlockSize = 512
    Optimized bandBlockSize = 1

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.2 SDO_GEOR_UTL.calcRasterNominalSize

#### Format

    SDO_GEOR_UTL.calcRasterNominalSize(
         geor        IN SDO_GEORASTER,
         padding     IN VARCHAR2 DEFAULT 'TRUE',
         pyramid     IN VARCHAR2 DEFAULT 'TRUE',
         bitmapMask  IN VARCHAR2 DEFAULT 'TRUE'
         ) RETURN NUMBER;

#### Description

Returns the total raster block length (in bytes) of a GeoRaster object, as if it were not compressed and did not contain any empty raster blocks.

#### Parameters

geor
GeoRaster object.

padding
The string `TRUE` (the default) causes padding in the raster blocks to be considered; the string `FALSE` causes padding in the raster blocks not to be considered.

pyramid
The string `TRUE` (the default) causes the size of any pyramids to be considered; the string `FALSE` causes the size of any pyramids not to be considered.

bitmapMask
The string `TRUE` (the default) causes any associated bitmap masks to be considered; the string `FALSE` causes any associated bitmap masks not to be considered. For an explanation of bitmap masks, see [Bitmap Masks](georaster-overview-and-concepts.md).

#### Usage Notes

This function does not consider any LOB storage overhead, so the result is only an approximation of the real storage requirements for the GeoRaster object.

The result of this function will be greater than or equal to the result of the SDO_GEOR_UTL.calcRasterStorageSize function on the same GeoRaster object. If this function returns a larger value than the SDO_GEOR_UTL.calcRasterStorageSize function on the same GeoRaster object, the difference in the values reflects the space saved by the use of compression or empty raster blocks, or both.

For information about GeoRaster compression, see [Compression and Decompression](georaster-overview-and-concepts.md).

#### Examples

The following example calculates the nominal raster size (in bytes) of a GeoRaster object, according to its current blocking scheme. The returned size includes (by default) any padding in the raster blocks, any associated bitmap masks, and any pyramids.

    SELECT SDO_GEOR_UTL.calcRasterNominalSize(georaster) nsize FROM georaster_table
      WHERE georid=1;

         NSIZE
    ----------
        289150

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.3 SDO_GEOR_UTL.calcRasterStorageSize

#### Format

    SDO_GEOR_UTL.calcRasterStorageSize(
         geor  IN SDO_GEORASTER
         ) RETURN NUMBER;

#### Description

Returns the actual length (in bytes) of all raster blocks of a GeoRaster object.

#### Parameters

geor
GeoRaster object.

#### Usage Notes

The function calculates the actual length of all raster blocks of a GeoRaster object. It does not consider any LOB storage overhead, so the result is only an approximation of the real storage size of the GeoRaster object. In essence, this function executes the following statement:

    EXECUTE IMMEDIATE
    'SELECT SUM(DBMS_LOB.getLength(rasterBlock)) FROM ' || geor.rasterDataTable || ' WHERE rasterId=' || geor.rasterId;

The result of this function will be less than or equal to the result of the SDO_GEOR_UTL.calcRasterNominalSize function on the same GeoRaster object. If this function returns a smaller value than the SDO_GEOR_UTL.calcRasterNominalSize function on the same GeoRaster object, the difference in the values reflects the space saved by the use of compression or empty raster blocks, or both.

#### Examples

The following example calculates ratio (as a decimal fraction) of the actual size to the nominal size of a specified GeoRaster object. In this example, the actual size is about one-twentieth (1/20) of the nominal size.

    SELECT SDO_GEOR_UTL.calcRasterStorageSize(georaster)/
      SDO_GEOR_UTL.calcRasterNominalSize(georaster) ratio
        FROM georaster_table WHERE georid=1;

         RATIO
    ----------
    .056198816

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.4 SDO_GEOR_UTL.calcSurfaceArea

#### Format

    SDO_GEOR_UTL.calcSurfaceArea(
         georaster IN SDO_GEORASTER,
         window    IN SDO_GEOMETRY,
         parallel  IN NUMBER
      ) RETURN NUMBER;

#### Description

Calculates and returns the three–dimensional (3D) surface area represented by digital elevation model (DEM) data that is stored in a GeoRaster object.

#### Parameters

georaster
GeoRaster object in which DEM data is stored.

window
The 2D geometry object specifying the area of which the 3D surface area is to be calculated.

parallel
Degree of parallelism for the operation. It should be more than 0. The recommended value is 2 times the number of CPUs

#### Usage Notes

This function first finds out all cells within or touching a certain area specified by the `window` parameter, splits each of the cells into two 3D triangles, computes the 3D surface area of each triangle, and then returns the sum of these area values as the result. The areas of the triangles that intersect with the window boundary are computed based on the intersected geometries, so this function returns the surface area with a high degree of precision.

If the `parallel` parameter value is less than 1, then 1 is used (that is, no parallelism).

#### Examples

The following example calculates the surface area within `geom` using DEM data. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      geor  SDO_GEORASTER;
      geom  SDO_GEOMETRY;
      area  number;
    BEGIN
      geom:=sdo_geometry(2003,82394, NULL,
                         mdsys.sdo_elem_info_array(1, 1003, 1),
                         mdsys.sdo_ordinate_array(20283.775, 1011087.9,
                                                 18783.775, 1008687.9,
                                                 21783.775, 1008687.9,
                                                 22683.775+0.001, 1009587.9,
                                                 20283.775, 1011087.9));
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 3;
      area:=SDO_GEOR_UTL.calcSurfaceArea(geor,geom,2);
    END;
    /

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.5 SDO_GEOR_UTL.clearReportTable

#### Format

    SDO_GEOR_UTL.clearReportTable(
         client_id  IN NUMBER DEFAULT NULL);

#### Description

Deletes records in the table that contains GeoRaster operation status information.

#### Parameters

client_id
ID of the client whose records are to be deleted. If this parameter is not specified, all records in the table are deleted.

(The client ID can be set by using the SDO_GEOR_UTL.setClientID procedure.)

#### Usage Notes

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example deletes all the records in the report table.

    EXECUTE SDO_GEOR_UTL.clearReportTable;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.6 SDO_GEOR_UTL.createDMLTrigger

#### Format

    SDO_GEOR_UTL.createDMLTrigger(
         tableName   IN VARCHAR2,
         columnName  IN VARCHAR2);

#### Description

Creates the required standard GeoRaster data manipulation language (DML) trigger on a GeoRaster column in a GeoRaster table, so that the appropriate operations are performed when its associated trigger is fired.

#### Parameters

tableName
Name of a GeoRaster table (the table containing rows with at least one GeoRaster object column).

columnName
Name of a column of type SDO_GEORASTER in the GeoRaster table.

#### Usage Notes

**Note:**

A more convenient alternative may be to use the SDO_GEOR_UTL.recreateDMLTriggers procedure, where one call to the procedure re-creates or creates the DML triggers on all GeoRaster columns that the current user has privileges to access.

As explained in [GeoRaster DML Trigger](georaster-database-creation-management.md), to ensure the consistency and integrity of internal GeoRaster tables and data structures, GeoRaster automatically creates a unique DML trigger for each GeoRaster column whenever a user creates a GeoRaster table (that is, a table with at least one GeoRaster column), with the following exception: if you use the ALTER TABLE statement to add one or more GeoRaster columns. In this case, you must call the SDO_GEOR_UTL.createDMLTrigger procedure to create the DML trigger on each added GeoRaster column.

Otherwise, you usually do not need to call this procedure, although but it is still useful for re-creating the DML trigger in some scenarios, such as a database upgrade or a data migration.

#### Examples

The following example creates the standard GeoRaster DML trigger for a table named XYZ_GEOR_TAB containing a GeoRaster column named GEOR_COL.

    EXECUTE sdo_geor_utl.createDMLTrigger('XYZ_GEOR_TAB', 'GEOR_COL');

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.7 SDO_GEOR_UTL.createReportTable

#### Format

    SDO_GEOR_UTL.createReportTable;

#### Description

Creates the table to contain GeoRaster operation status information.

#### Parameters

None.

#### Usage Notes

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example creates the table to contain GeoRaster operation status information.

    EXECUTE SDO_GEOR_UTL.createReportTable;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.8 SDO_GEOR_UTL.disableReport

#### Format

    SDO_GEOR_UTL.disableReport;

#### Description

Disables status reporting on GeoRaster operations in the current session.

#### Parameters

None.

#### Usage Notes

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example disables status reporting on GeoRaster operations in the current session.

    EXECUTE SDO_GEOR_UTL.disableReport;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.9 SDO_GEOR_UTL.dropReportTable

#### Format

    SDO_GEOR_UTL.dropReportTable;

#### Description

Drops the table that contains GeoRaster operation status information.

#### Parameters

None.

#### Usage Notes

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example drops the table that contains GeoRaster operation status information.

    EXECUTE SDO_GEOR_UTL.dropReportTable;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.10 SDO_GEOR_UTL.emptyBlocks

#### Format

    SDO_GEOR_UTL.emptyBlocks(
         georaster IN OUT SDO_GEORASTER,
         bgValues  IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Trims all blocks that contain only the specified background values to empty LOBs, thus making them empty blocks. Can be used to reduce disk space required for GeoRaster storage.

#### Parameters

georaster
GeoRaster object.

bgValues
Background values for determining if a block can be made an empty raster block. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all layers) or the layer dimension size (a different filling value for each layer, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) means that a block with the first layer with 1, the second layer with 5, and the third layer with 10 are made empty blocks. If this parameter is null, then `bgValues` will be the default value (a single element SDO_NUMBER_ARRAY(0)).

#### Usage Notes

If `georaster` is null, this procedure performs no operation.

Contrast this procedure with SDO_GEOR_UTL.fillEmptyBlocks, which uses specified background values to fill in all empty blocks.

#### Examples

The following example empties blocks whose cell values are background values (255,0,0).

    DECLARE
      geor  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 3 FOR UPDATE;
      SDO_GEOR_UTL.emptyBlocks(geor, SDO_NUMBER_ARRAY(255,0,0));
      UPDATE georaster_table SET georaster = geor WHERE georid = 3;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.11 SDO_GEOR_UTL.enableReport

#### Format

    SDO_GEOR_UTL.enableReport;

#### Description

Enables status reporting on GeoRaster operations in the current session.

#### Parameters

None.

#### Usage Notes

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example enables status reporting on GeoRaster operations in the current session.

    EXECUTE SDO_GEOR_UTL.enableReport;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.12 SDO_GEOR_UTL.fillEmptyBlocks

#### Format

    SDO_GEOR_UTL.fillEmptyBlocks(
         georaster IN OUT SDO_GEORASTER,
         bgValues  IN SDO_NUMBER_ARRAY DEFAULT NULL);

#### Description

Fills in all empty blocks with specified background values.

#### Parameters

georaster
GeoRaster object in which to fill empty blocks.

bgValues
Background values for filling empty raster blocks. The number of elements in the SDO_NUMBER_ARRAY object must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, SDO_NUMBER_ARRAY(1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. If this parameter is null, then `bgValues` will be 0 (zero).

#### Usage Notes

If `georaster` is null, this procedure performs no operation.

If pyramid data exists for `georaster`, the pyramid is regenerated based on pyramid information stored in the metadata.

Contrast this procedure with SDO_GEOR_UTL.emptyBlocks, which turns blocks with specified background values into empty blocks.

#### Examples

The following example empties blocks that have background values (255,0,0).

    DECLARE
      geor  SDO_GEORASTER;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 3 FOR UPDATE;
      SDO_GEOR_UTL.emptyBlocks(geor, SDO_NUMBER_ARRAY(255,0,0));
      UPDATE georaster_table SET georaster = geor WHERE georid = 3;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.13 SDO_GEOR_UTL.generateColorRamp

#### Format

    SDO_GEOR_UTL.generateColorRamp(
         colorSeeds     IN SDO_GEOR_COLORMAP,
         rampSteps      IN SDO_NUMBER_ARRAY,
         cellValueType  IN VARCHAR2 DEFAULT 'integer',
         interpoParam   IN VARCHAR2 DEFAULT 'method=linear'
         ) RETURN SDO_GEOR_COLORMAP;

#### Description

Generates an SDO_GEOR_COLORMAP object with a color ramp (gradient) by interpolating the red, green, blue, and alpha values entered as seed.

#### Parameters

colorSeeds
An SDO_GEOR_COLORMAP object with the seed values to be used as the beginning and end values for the interpolation. Should contain at least two groups, each containing a pixel value and set of RGBA values. (RGBA = red, green, blue, alpha)

rampSteps
An array where each item indicates how many interpolated values will be generated for each section of the color ramp. Should contain at least one integer value indicating how many values will be generated for each section.

cellValueType
A string indicating whether the cell values should be creates as integer or real values. The possible values for this parameter are `integer` (the default) or `real`.

interpoParam
A string specifying the interpolation method. The possible values are `method=linear` (the default) and `method=cosine`.

#### Usage Notes

This function returns an object of type SDO_GEOR_COLORMAP, which is described in [SDO_GEOR_COLORMAP Object Type](georaster-datatypes.md).

A color ramp can have several different sections with different lengths for each section. If `colorSeeds` specifies three RGBA values, the function will generate two sections on the same color ramp. The number of color levels for each section is controlled by `rampSteps` array. The total number of the colors in the generated colormap is the sum of the values in the rampSteps array and the number of colors in the input colormap seed. To generate independent sections, insert a new item in the `colorSeeds` parameter, and a new item in `rampSteps`. (Any value of 0 in `rampSteps` indicates that no interpolated values are needed to generate in that section.)

#### Examples

The following example generates and applies a color ramp containing 256 colors interpolated linearly from green to red. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.)

    DECLARE
      gr sdo_georaster;
      cmp sdo_geor_colormap;
    BEGIN
      select raster into gr from ramp_test where id = 1 for update;

      cmp := sdo_geor_utl.generateColorRamp(
                colorSeeds => sdo_geor_colormap(
                  sdo_number_array(   1,1000),
                  sdo_number_array(   0, 255),
                  sdo_number_array( 255,   0),
                  sdo_number_array(   0,   0),
                  sdo_number_array( 255, 255)),
                rampSteps  => sdo_number_array( 254 ),
                cellValueType => 'integer',
                interpoParam  => 'method=linear' );

      sdo_geor.setColorMap( gr, 0, cmp );

      update ramp_test set raster = gr where id = 1;
      commit;
    END;

The following example generates and applies a color ramp that goes from shades of green turning into blue and from blue turning into red. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.) The two sections will share the second item from the `colorSeeds` parameter value, the blue color.

    DECLARE
      gr sdo_georaster;
      cmp sdo_geor_colormap;
    BEGIN
      select raster into gr from ramp_test where id = 1 for update;

      cmp := sdo_geor_utl.generateColorRamp(
                colorSeeds => sdo_geor_colormap(
                  sdo_number_array(   1, 500, 1000),
                  sdo_number_array(   0,   0,  255),
                  sdo_number_array( 255,   0,    0),
                  sdo_number_array(   0, 255,    0),
                  sdo_number_array( 255, 255,  255)),
                rampSteps  => sdo_number_array( 126, 127 ),
                cellValueType => 'integer',
                interpoParam  => 'method=linear' );

      sdo_geor.setColorMap( gr, 0, cmp );

      update ramp_test set raster = gr where id = 1;
      commit;
    END;

The following example generates a color ramp of 256 items with a section that goes from green to blue and a section that goes from white to red. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.)

    DECLARE
      gr sdo_georaster;
      cmp sdo_geor_colormap;
    BEGIN
      select raster into gr from ramp_test where id = 1 for update;

      cmp := sdo_geor_utl.generateColorRamp(
                colorSeeds => sdo_geor_colormap(
                  sdo_number_array(   1, 500,  500, 1000),
                  sdo_number_array(   0,   0,  255,  255),
                  sdo_number_array( 255,   0,  255,    0),
                  sdo_number_array(   0, 255,  255,    0),
                  sdo_number_array( 255, 255,  255,  255)),
                rampSteps  => sdo_number_array( 126, 0, 126 ),
                cellValueType => 'integer',
                interpoParam  => 'method=linear' );

      sdo_geor.setColorMap( gr, 0, cmp );

      update ramp_test set raster = gr where id = 1;
      commit;
    END;

The value of 0 in the `rampSteps` array (`rampSteps => sdo_number_array( 126, 0, 126 );`) indicates that no interpolated values are needed for generation in the second section.

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.14 SDO_GEOR_UTL.generateGrayRamp

#### Format

    SDO_GEOR_UTL.generateGrayRamp(
         graySeeds      IN SDO_GEOR_GRAYSCALE,
         rampSteps      IN SDO_NUMBER_ARRAY,
         cellValueType  IN VARCHAR2 DEFAULT 'integer',
         interpoParam   IN VARCHAR2 DEFAULT 'method=linear'
         ) RETURN SDO_GEOR_GRAYSCALE;

#### Description

Generates an SDO_GEOR_GRAYSCALE object with a grayscale ramp (gradient) by interpolating the values entered as seed.

#### Parameters

graySeeds
An SDO_GEOR_GRAYSCALE object with the seed values to be used as the beginning and end values for the interpolation. Should contain at least two pixel-value/gray-value pairs.

rampSteps
An array where each item indicates how many interpolated values will be generated for each section of the gray ramp. Should contain at least one integer value indicating how many values will be generated for each section of the gray ramp.

cellValueType
A string indicating whether the cell values should be creates as integer or real values. The possible values for this parameter are `integer` (the default) or `real`.

interpoParam
A string specifying the interpolation method. The possible values are `method=linear` (the default) and `method=cosine`.

#### Usage Notes

This function returns an object of type SDO_GEOR_GRAYSCALE, which is described in [SDO_GEOR_GRAYSCALE Object Type](georaster-datatypes.md).

A gray ramp can have several different sections with different lengths for each section. If `graySeeds` specifies three values, the function will generate two sections on the same gray ramp. The number of gray levels for each section is controlled by `rampSteps` array. The total number of the generated grayscale is the sum of the values in the `rampSteps` array and the number of values in the `graySeeds`. To generate independent sections, insert a new item in the `graySeeds` parameter, and a new item in `rampSteps`. (Any value of 0 in `rampSteps` indicates that no interpolated values are needed to generate in that section.)

#### Examples

The following example generates and applies a gray ramp containing 102 grayscales interpolated linearly from 0 to 255. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.)

    DECLARE
      gr sdo_georaster;
      gs sdo_geor_grayscale;
    BEGIN
      select raster into gr from ramp_test where id = 3 for update;

      gs := sdo_geor_utl.generateGrayRamp(
               graySeeds  => sdo_geor_grayscale(
                 sdo_number_array( 0, 1000),
                 sdo_number_array( 0,  255)),
               rampSteps  => sdo_number_array( 100 ),
               cellValueType => 'integer',
               interpoParam  => 'method=linear' );

      sdo_geor.setGrayScale( gr, 0, gs );

      update ramp_test set raster = gr where id = 3;
      commit;
    END;

The following example generates and applies a gray ramp of 203 grayscale values, with 100 interpolated values between -100 and 0 and 100 interpolated values between 0 and 1000. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.).

    DECLARE
      gr sdo_georaster;
      gs sdo_geor_grayscale;
    BEGIN
      select raster into gr from ramp_test where id = 3 for update;

      gs := sdo_geor_utl.generateGrayRamp(
               graySeeds  => sdo_geor_grayscale(
                 sdo_number_array( -100, 0, 1000),
                 sdo_number_array(  255, 0,  255)),
               rampSteps  => sdo_number_array( 100, 100 ),
               cellValueType => 'real',
               interpoParam  => 'method=linear' );

      sdo_geor.setGrayScale( gr, 0, gs );

      update ramp_test set raster = gr where id = 3;
      commit;
    END;

The following example generates a gray ramp of 204 grayscale values, with 100 interpolated values between -100 and 0 and 100 interpolated values between 100 and 1000. (It assumes the existence of a table named RAMP_TEST containing at least columns named ID and RASTER.)

    DECLARE
      gr sdo_georaster;
      gs sdo_geor_grayscale;
    BEGIN
      select raster into gr from ramp_test where id = 3 for update;

      gs := sdo_geor_utl.generateGrayRamp(
               graySeeds  => sdo_geor_grayscale(
                 sdo_number_array( -100,  0, 100, 1000),
                 sdo_number_array(    0, 10, 100,  200)),
               rampSteps  => sdo_number_array( 100, 0, 100 ),
               cellValueType => 'real',
               interpoParam  => 'method=linear' );

      sdo_geor.setGrayScale( gr, 0, gs );

      update ramp_test set raster = gr where id = 3;
      commit;
    END;

The value of 0 in the `rampSteps` array (`rampSteps => sdo_number_array( 100, 0, 100 );`) indicates that no interpolated values are needed for generation in the second section.

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.15 SDO_GEOR_UTL.getAllStatusReport

#### Format

    SDO_GEOR_UTL.getAllStatusReport() RETURN SDO_STRING2_ARRAYSET;

#### Description

Returns the current status for all operations for all clients in the status table.

#### Parameters

None.

#### Usage Notes

This function returns an array with a comma-delimited list of status information: \<client_id\>, \<sequence_id\>, \<timestamp\>, \<operation name\>, \<RDT table name\>, \<Raster ID\>, \<progress\>, \<description\>. The data type is SDO_STRING2_ARRAYSET, which is defined as `VARRAY(2147483647) OF SDO_STRING2_ARRAY`.

If the status table has not been created, the function returns `'The report table does not exist.'`

This function is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example returns the current status for all operations for all clients. It returns two SDO_STRING2_ARRAY objects.

    SELECT * from the (SELECT SDO_GEOR_UTL.getAllStatusReport FROM DUAL);

    COLUMN_VALUE
    -------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('Client:23', 'Sequence:1', '24-SEP-12 11.10.42.030169 AM', 'Mosaic', 'RDT:LANDSAT_MOSAIC_RDT', 'RID:1', '100% complete', NULL)
    SDO_STRING2_ARRAY('Client:1', 'Sequence:0', '24-SEP-12 11.10.42.379631 AM', 'GeneratePyramid', 'RDT:LANDSAT_MOSAIC_RDT', 'RID:1', '100% complete', 'operation completed')

    2 rows selected.

The following example also returns the current status for all operations for all clients. It uses a different SELECT statement format than the preceding example, and returns a single SDO_STRING2_ARRAYSET object that contains two SDO_STRING2_ARRAY objects.

    set linesize 80
    SELECT SDO_GEOR_UTL.getAllStatusReport FROM DUAL;

    SDO_GEOR_UTL.GETALLSTATUSREPORT()
    --------------------------------------------------------------------------------
    SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('Client:27', 'Sequence:1', '26-SEP-12 11.
    31.03.473087 AM', 'Mosaic', 'RDT:LANDSAT_MOSAIC_RDT', 'RID:1', '100% complete',
    NULL), SDO_STRING2_ARRAY('Client:-1', 'Sequence:0', '26-SEP-12 11.31.03.962948 A
    M', 'GeneratePyramid', 'RDT:LANDSAT_MOSAIC_RDT', 'RID:1', '100% complete', 'oper
    ation completed'))

    1 row selected.

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.16 SDO_GEOR_UTL.getMaxMemSize

#### Format

    SDO_GEOR_UTL.getMaxMemSize RETURN NUMBER;

#### Description

Returns the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.

#### Parameters

(None.)

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example returns the current upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.

    SELECT sdo_geor_utl.getMaxMemSize FROM DUAL;

    GETMAXMEMSIZE
    -------------
         16777216

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.17 SDO_GEOR_UTL.getReadBlockMemSize

#### Format

    SDO_GEOR_UTL.getReadBlockMemSize RETURN NUMBER;

#### Description

Returns the size in bytes of the GeoRaster internal data block for read-only operations.

#### Parameters

(None.)

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example returns the current size in bytes of the GeoRaster internal data block for read-only operations.

    SELECT sdo_geor_utl.getReadBlockMemSize FROM DUAL;

    GETREADBLOCKMEMSIZE
    -------------------
                  32768

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.18 SDO_GEOR_UTL.getProgress

#### Format

    SDO_GEOR_UTL.getProgress(
         client_id IN NUMBER,
         seq_id    IN NUMBER DEFAULT 0
         ) RETURN NUMBER;

#### Description

Returns the progress of the operation for a specified client (session) and optionally for a specified operation. The returned value is the percentage of completion as a floating point number between 0 and 1.

#### Parameters

client_id
Unique numeric value identifying the session.

seq_id
Unique numeric value (within the specified session) identifying the operation for which to return status information.

#### Usage Notes

This function returns a number that is the latest estimated progress of the operation identified by the `client_id` and `seq_id`. Make sure that the correct `client_id` and `seq_id` values are used.

If the status table has no record of the specified operation with the given `client_id` and `seq_id`, null is returned.

If the status table has not been created, the function returns `'The report table does not exist.'`

This function is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example returns the progress of the operation with client ID 5 and operation sequence ID 3.

    SELECT sdo_geor_utl.getgetProgress(5, 3) progress FROM dual;

    PROGRESS
    --------
        .305

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.19 SDO_GEOR_UTL.getStatusReport

#### Format

    SDO_GEOR_UTL.getStatusReport(
         client_id IN NUMBER,
         seq_id    IN NUMBER DEFAULT 0
         ) RETURN SDO_STRING2_ARRAY;

#### Description

Returns the current status of the operations in the status table for a specified client (session) and optionally for a specified operation.

#### Parameters

client_id
Unique numeric value identifying the session.

seq_id
Unique numeric value (within the specified session) identifying the operation for which to return status information.

#### Usage Notes

This function returns the current status of a specified session (`client_id`) in an array of comma-delimited lists of status information: \<client_id\>, \<sequence_id\>, \<timestamp\>, \<operation name\>, \<RDT table name\>, \<Raster ID\>, \<progress\>, \<description\>. The data type is SDO_STRING2_ARRAY, which is defined as `VARRAY(2147483647) OF VARCHAR2(4096)`.

If the status table has not been created, the function returns `'The report table does not exist.'`

This function is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example returns the status of the operation with client ID 5 and operation sequence ID 3.

    SELECT sdo_geor_utl.getStatusReport(5, 3) FROM dual;

    SDO_GEOR_UTL.GETSTATUSREPORT(5,3)
    --------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('24-SEP-12 11.10.43.477804 AM', 'Mosaic', 'RDT:LANDSAT_MOSAIC_
    RDT', 'RID:2', '100% complete', 'operation completed')

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.20 SDO_GEOR_UTL.getWriteBlockMemSize

#### Format

    SDO_GEOR_UTL.getWriteBlockMemSize RETURN NUMBER;

#### Description

Returns the size in bytes of the GeoRaster internal data block for read/write operations.

#### Parameters

(None.)

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example returns the current size in bytes of the GeoRaster internal data block for read/write operations.

    SELECT sdo_geor_utl.getWriteBlockMemSize FROM DUAL;

    GETWRITEBLOCKMEMSIZE
    --------------------
                   65536

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.21 SDO_GEOR_UTL.isReporting

#### Format

    SDO_GEOR_UTL.isReporting() RETURN NUMBER;

#### Description

Checks if any session has status reporting enabled.

#### Parameters

None.

#### Usage Notes

This function returns 1 if one or more sessions have status reporting enabled; it returns 0 if no sessions have status reporting enabled.

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example checks if any session has status reporting enabled.

    SELECT SDO_GEOR_UTL.isReporting FROM DUAL;

    ISREPORTING
    -----------
              1

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.22 SDO_GEOR_UTL.makeRDTNamesUnique

#### Format

    SDO_GEOR_UTL.makeRDTNamesUnique;

#### Description

Renames some existing registered raster data tables that do not have unique names so that all raster data table names are unique within the database, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.

#### Parameters

None.

#### Usage Notes

If one or more registered raster data tables have the same name (under different schemas), you can use this procedure or the SDO_GEOR_UTL.renameRDT procedure, or both, to eliminate the duplication.

Run this procedure when you are connected to the database with the DBA role.

This procedure is not transactional, and the result cannot be rolled back.

#### Examples

The following example automatically renames some existing registered raster data tables that do not have unique names so that all registered raster data table names are unique within the database, and it updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.

    EXECUTE sdo_geor_utl.makeRDTNamesUnique;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.23 SDO_GEOR_UTL.recreateDMLTriggers

#### Format

    SDO_GEOR_UTL.recreateDMLTriggers;

#### Description

Re-creates the required standard GeoRaster data manipulation language (DML) triggers on all GeoRaster columns that the current user has privileges to access, so that the appropriate operations are performed when the triggers are fired.

#### Parameters

(None)

#### Usage Notes

As explained in [GeoRaster DML Trigger](georaster-database-creation-management.md), to ensure the consistency and integrity of internal GeoRaster tables and data structures, GeoRaster automatically creates a unique DML trigger for each GeoRaster column whenever a user creates a GeoRaster table (that is, a table with at least one GeoRaster column), with the following exception: if you use the ALTER TABLE statement to add one or more GeoRaster columns. If this happens you can either call the SDO_GEOR_UTL.createDMLTrigger procedure for those added GeoRaster columns or call the SDO_GEOR_UTL.recreateDMLTriggers procedure to recreate the DML triggers on all GeoRaster columns.

You usually do not need to call this procedure, but it is useful for re-creating the DML triggers in some scenarios, such as a database upgrade or a data migration.

#### Examples

The following example re-creates the standard GeoRaster DML triggers.

    EXECUTE sdo_geor_utl.recreateDMLTriggers;

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.24 SDO_GEOR_UTL.renameRDT

#### Format

    SDO_GEOR_UTL.renameRDT(
         oldRDTs  VARCHAR2,
         newRDTs  VARCHAR2 DEFAULT NULL);

#### Description

Renames one or more existing registered raster data tables owned by the current user, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.

#### Parameters

oldRDTs
Name of the registered raster data table or tables to be renamed. For multiple tables, use a comma-delimited list.

newRDTs
New names to be assigned to the raster data table or tables that are specified in `oldRDTs`. For multiple tables, use a comma-delimited list with an order exactly reflecting the names in `oldRDTs`. If this parameter is null, GeoRaster assigns a unique new name to each input raster data table.

#### Usage Notes

If one or more registered raster data tables owned by different users have the same name, you can use this procedure or the SDO_GEOR_UTL.makeRDTNamesUnique procedure, or both, to eliminate the duplication.

Before using this procedure, you must connect to the database as the owner of the raster data table or tables. You cannot use this procedure to rename a raster data table owned by another user.

If any table in `oldRDTs` is not included in the GeoRaster system data, it is ignored.

If any table in `newRDTs` conflicts with a name in the GeoRaster system data or with the name of another object owned by the current user, an exception is raised.

This procedure is not transactional, and the result cannot be rolled back.

#### Examples

The following example renames the registered raster data tables RDT_1 and RDT_2 to ST_RDT_1 and ST_RDT_2, respectively.

    EXECUTE sdo_geor_utl.renameRDT('RDT_1,RDT_2','ST_RDT_1,ST_RDT_2');

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.25 SDO_GEOR_UTL.setClientID

#### Format

    SDO_GEOR_UTL.setClientID(
         client_id  IN NUMBER);

#### Description

Sets the client ID for a session.

#### Parameters

client_id
Unique ID value to identify the session.

#### Usage Notes

This procedure can be used to identify different sessions under the same user. The client ID can be the database session ID or the client ID in the mid-tier environment.

If this procedure is not called, the client ID in the status report defaults to the database session ID.

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example sets the client ID to 1.

    EXECUTE SDO_GEOR_UTL.setClientID(1);

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.26 SDO_GEOR_UTL.setMaxMemSize

#### Format

    SDO_GEOR_UTL.setMaxMemSize(
         maxMemSize  IN NUMBER DEFAULT 16777216);

#### Description

Sets the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.

#### Parameters

maxMemSize
Number of bytes that can be used for managing memory using the GeoRaster buffer system. The default value is 16777216 (16 MB).

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example sets the `maxMemSize` value to 100 million bytes (approximately 100 MB).

    EXECUTE sdo_geor_utl.setMaxMemSize(100000000);

The following example sets the `maxMemSize` value to the default size (16 MB).

    EXECUTE sdo_geor_utl.setMaxMemSize();

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.27 SDO_GEOR_UTL.setReadBlockMemSize

#### Format

    SDO_GEOR_UTL.setReadBlockMemSize(
         memBlockSize  IN NUMBER DEFAULT 32768);

#### Description

Sets the size of the GeoRaster internal data block for read-only operations.

#### Parameters

memBlockSize
Number of bytes that can be used for the GeoRaster internal data block for read-only operations. The default value is 32768 (32 KB).

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example sets the `memBlockSize` value to 1 million bytes (approximately 1 MB).

    EXECUTE sdo_geor_utl.setReadBlockMemSize(1000000);

The following example sets the `memBlockSize` value to the default value (32 KB).

    EXECUTE sdo_geor_utl.setReadBlockMemSize();

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.28 SDO_GEOR_UTL.setSeqID

#### Format

    SDO_GEOR_UTL.setSeqID(
         seq_id  IN NUMBER);

#### Description

Sets the sequence ID for a session.

#### Parameters

seq_id
Unique ID value to identify the operation in a session.

#### Usage Notes

This procedure can be used to identify different operations in the same session.

If this procedure is not called, the sequence ID in the status report defaults to 0.

This procedure is one of the subprograms available for monitoring and reporting the progress of GeoRaster operations. For an overview of this capability, see [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md).

#### Examples

The following example sets the sequence ID to 1.

    EXECUTE SDO_GEOR_UTL.setSeqID(1);

**Parent topic:** SDO_GEOR_UTL Package Reference

### 13.29 SDO_GEOR_UTL.setWriteBlockMemSize

#### Format

    SDO_GEOR_UTL.setWriteBlockMemSize(
         memBlockSize  IN NUMBER);

#### Description

Sets the size of the GeoRaster internal data block for read/write operations.

#### Parameters

memBlockSize
Number of bytes that can be used for the GeoRaster internal data block for read/write operations. The default value is 65536 (64 KB).

#### Usage Notes

[Managing Memory for GeoRaster Buffering](georaster-data-manipulation.md) provides conceptual and usage information, including explanations of the relevant parameters.

#### Examples

The following example sets the `memBlockSize` value to 1 million bytes (approximately 1 MB).

    EXECUTE sdo_geor_utl.setWriteBlockMemSize(1000000);

The following example sets the `memBlockSize` value to the default value (64 KB).

    EXECUTE sdo_geor_utl.setWriteBlockMemSize();

**Parent topic:** SDO_GEOR_UTL Package Reference
