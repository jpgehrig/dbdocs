## 11 SDO_GEOR_IP Package Reference

The SDO_GEOR_IP package contains subprograms (functions and procedures) for performing image processing operations on GeoRaster objects. This chapter presents reference information, with one or more examples, for each subprogram.

Many examples in this chapter refer to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).

All SDO_GEOR_IP subprograms can work on GeoRaster objects defined in schemas other than the current connection schema.

- SDO_GEOR_IP.dodge
- SDO_GEOR_IP.equalize
- SDO_GEOR_IP.filter
- SDO_GEOR_IP.histogramMatch
- SDO_GEOR_IP.normalize
- SDO_GEOR_IP.piecewiseStretch
- SDO_GEOR_IP.stretch

### 11.1 SDO_GEOR_IP.dodge

#### Format

    SDO_GEOR_IP.dodge(
         inGeoRaster        IN SDO_GEORASTER,
         gridsize           IN SDO_NUMBER_ARRAY,
         samplingFactor     IN VARCHAR2 DEFAULT NULL,
         means              IN SDO_NUMBER_ARRAY DEFAULT NULL,
         standardDeviations IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam       IN VARCHAR2 DEFAULT NULL,
         outGeoraster       IN OUT SDO_GEORASTER,
         parallelParam      IN VARCHAR2 DEFAULT NULL);  

or

    SDO_GEOR_IP.dodge(
         inGeoRaster        IN SDO_GEORASTER,
         gridsize           IN SDO_NUMBER_ARRAY,
         samplingFactor     IN VARCHAR2 DEFAULT NULL,
         refGeoraster       IN SDO_GEORASTER,
         standardDeviations IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam       IN VARCHAR2 DEFAULT NULL,
         outGeoraster       IN OUT SDO_GEORASTER,
         parallelParam      IN VARCHAR2 DEFAULT NULL);  

#### Description

Apply a dodging algorithm on the input GeoRaster object to color balance the image.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be processed.

gridSize
The size of each grid in x and y direction, respectively. It is an array of one or two numbers. If only one number is specified, then it is for both x and y direction.

samplingFactor
Sampling factor, used to control the calculation of the statistics, in the format`'samplingFactor=n'`, with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example, if `samplingFactor` is 4, one-sixteenth of the cells are sampled; but if `samplingFactor` is 1, all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed. If not specified (null), the default is 1.

`samplingFactor` cannot be greater than or equal to one-half (0.5) of `gridSize`.

means
The target mean values for each output bands. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number bands of the output GeoRaster object. If null, it is calculated as the average mean value over all the grids.

standardDeviations
The target standard deviation values for each output bands. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. If null, it is calculated as the average standard deviation over all the grids.

refGeoraster
The reference GeoRaster object.  The output of the dodging result will adapt to the statistics of the reference GeoRaster object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

This dodging operation uses an adaptive image enhancement method to make the image tone more balanced, that is, the darker area becomes brighter and the bright area becomes darker. The statistics for the grid defined by the `gridsize` parameter are collected on the fly and adjusted to the target mean and standard deviation values. The grid size should be smaller than the imbalanced area in order to remove the imbalance. Adjust the `gridSize` parameter to achieve the best result.

The input GeoRaster image must have a `cellDepth` value of `8BIT_U`. Any `celldepth` value in the storage parameters is ignored. The cell depth of the `outGeoRaster` object is always `8BIT_U`.

Color map in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object that is the result of dodging on the input GeoRaster object. The desired mean and standard deviation are set as 125 and 80, respectively. The grid size is 512 on x and y direction. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.dodge(gr1, sdo_number_array(512, 512), ‘samplingFactor=3’, sdo_number_array(125), sdo_number_array(80), null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example creates a GeoRaster object that is the result of dodging on the input GeoRaster object based on the reference GeoRaster object. Parallel processing is enabled with parallel degree of 4. The grid size is 512 on x and y direction. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
    gr1 sdo_georaster;
    gr2 sdo_georaster;
    refgr sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster) VALUES (41, sdo_geor.init('RDT_1'))
         RETURNING georaster INTO gr2;
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;
      SELECT georaster INTO refgr FROM georaster_table WHERE georid=1;
      sdo_geor_ip.dodge(gr1, sdo_number_array(512, 512), ‘samplingFactor=3’, refgr, null,
                        gr2, 'parallel=4');
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
    COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.2 SDO_GEOR_IP.equalize

#### Format

    SDO_GEOR_IP.equalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.equalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.equalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.equalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

#### Description

Process the input GeoRaster object by using histogram equalization method. The processed image is stored in the output GeoRaster object or in a BLOB.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be equalized.

pyramidLevel
A number specifying the pyramid level to be equalized in the source GeoRaster object. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

#### Usage Notes

The input GeoRaster object must have histogram generated for each output band.

The equalization is performed based on the histograms stored in the metadata of the input GeoRaster object.

Color map stored in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

The cell depth of the output GeoRaster object is always `8BIT_U`.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

If the `cropArea` parameter specifies a geodetic MBR, it cannot cross the date line meridian

#### Examples

The following example creates a GeoRaster object that has each input band equalized based on the histogram stored in the metadata. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.equalize(gr1, cropArea, null, null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example performs the image equalization based on the histogram stored in the metadata; the output is in a temporary BLOB. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      out_lob BLOB;
      cropArea sdo_number_array := null;
      outArea sdo_geometry;
      outWindow sdo_number_array;
    BEGIN
      dbms_lob.create_temporary(out_lob, TRUE);
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.equalize(gr1, cropArea, null, null, out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.3 SDO_GEOR_IP.filter

#### Format

    SDO_GEOR_IP.filter(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         filterParam  IN VARCHAR2,
         filterKernel IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.filter(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         filterParam  IN VARCHAR2,
         filterKernel IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.filter(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         filterParam  IN VARCHAR2,
         filterKernel IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.filter(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         filterParam  IN VARCHAR2,
         filterKernel IN SDO_NUMBER_ARRAY,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

#### Description

Applies the convolution filter on the input GeoRaster object. The processed image is stored in the output GeoRaster object or in a BLOB.

#### Parameters

inGeoRaster
The SDO_GEORASTER object for the filter operation.

pyramidLevel
A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

filterParam
The type of the filter to be applied on the input GeoRaster. It is in the format `‘filterType=`value`’` where value can be one of the following: `LPF` (low-pass filter, the default), `HPF` (high-pass filter), `HBF` (high-boost filter), `MIN` (minimum filter), `MAX` (maximum filter), `MEDIAN` (median filter), `MODE` (mode filter), or `CUSTOM` (user-provided filter kernel).

`filterParam` can also include:

- `‘kernelSize=(`kx, ky`)’` where kx, ky are the size of the kernel on the x and y direction. For a filter type other than `CUSTOM`, the `kx` and `ky` should be odd numbers greater than or equal to 3.

- `‘p1 = `value`’`, used by the `HBF` filter to indicate the degree of boost.

filterKernel
Required only when `filterType=CUSTOM`. It is the `kx * ky` numbers in an SDO_NUMBER_ARRAY object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

#### Usage Notes

For an introduction to image filtering, see [Image Filtering](image-processing-virtual-mosaic.md).

The following are `filterKernel` values for some of the predefined 3x3 filters:

- LPF: (1, 1, 1, 1, 1, 1, 1, 1, 1)\*1/9

- HPF: (-1, -1, -1, -1, 8, -1, -1, -1, -1)\*1/9

- HBF: (-k, -k, -k, -k, 8k, -k, -k, -k, -k)\*1/9, where k is the boost factor specified by parameter `p1`

For `kernelSize`, kx \* ky must be less than 10000.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

Color map in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object that is the result of using the default low-pass filter on the input GeoRaster object. The filter kernel size is 3 by 3. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_geometry := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.filter(gr1, 0, cropArea, null, ‘filtertype=LPF, kernelsize=(3, 3)’, null, null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example applies a custom (user–provided) 3 by 3 filter on the input GeoRaster object; the output is in a temporary BLOB. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_geometry := null;
      out_lob  BLOB;
      outArea  sdo_geometry := null;
      outWindow sdo_geometry := null;
    BEGIN
      dbms_lob.create_temporary(out_lob, TRUE);

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.filter(gr1, 0, cropArea, null, ‘filtertype=CUSTOM, kernelsize=(3,3)’, sdo_number_array(1/4, 1/2, 1/4, 1/2, 1, 1/2, 1/4, 1.2, 1/4 ), null, out_lob, outArea, outWindow);

      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);

     END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.4 SDO_GEOR_IP.histogramMatch

#### Format

    SDO_GEOR_IP.histogramMatch(
         inGeoRaster    IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         cropArea       IN SDO_NUMBER_ARRAY,
         bandNumbers    IN VARCHAR2,
         refHistograms  IN SDO_GEOR_HISTOGRAM_ARRAY,
         storageParam   IN VARCHAR2,
         outGeoraster   IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.histogramMatch(
         inGeoRaster    IN SDO_GEORASTER,
         pyramidLevel   IN NUMBER,
         cropArea       IN SDO_GEOMETRY,
         layerNumbers   IN VARCHAR2,
         refHistograms  IN SDO_GEOR_HISTOGRAM_ARRAY,
         storageParam   IN VARCHAR2,
         outGeoraster   IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.histogramMatch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         refGeoRaster IN SDO_GEORASTER,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.histogramMatch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         refGeoRaster IN SDO_GEORASTER,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

#### Description

Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (`refGeoRaster`) or a reference histogram (`refHistograms`).

#### Parameters

inGeoRaster
The SDO_GEORASTER object for the histogram matching operation.

pyramidLevel
A number specifying the pyramid level for the histogram matching operation. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

refHistograms
An array of reference histograms. If there is only one element in the array, all the output bands match to this histogram; otherwise, the length of the array must be the same as the number of the bands in the output GeoRaster object.

refGeoRaster
The reference GeoRaster object. The reference GeoRaster object must have a histogram stored in the metadata, and must have the same number of bands as the input GeoRaster object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

#### Usage Notes

The input GeoRaster object must have histograms generated for each band and stored in the metadata.

The reference GeoRaster object must have the same number of bands as the input GeoRaster object. The cell depth of the reference GeoRaster cannot be greater than the cell depth of the `outGeoRaster` object. The reference GeoRaster object must have histograms set in the metadata.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

Color map stored in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object that is the result of histogram matching the input GeoRaster object to the reference histograms. In the example, the reference histograms are stored in a table `histogram_table(histogram sdo_geor_histogram, band number)`. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
      refHists sdo_geor_histogram_array;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      -- get the source GeoRaster object
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      -- get the reference histogram
      SELECT histogram bulk collect into refHists from histogram_table order by band;

      sdo_geor_ip.histogramMatch(gr1, 0, cropArea, null, refHists, null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example creates a GeoRaster object that is the result of histogram matching the input GeoRaster object to the reference GeoRaster object. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      refgr sdo_georaster;
      cropArea sdo_number_array := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      -- get the source GeoRaster object
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      -- get the reference GeoRaster object
      SELECT georaster INTO refgr FROM georaster_table WHERE georid=5;

      sdo_geor_ip.histogramMatch(gr1, 0, cropArea, null, refgr, null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.5 SDO_GEOR_IP.normalize

#### Format

    SDO_GEOR_IP.normalize(
         inGeoRaster        IN SDO_GEORASTER,
         pyramidLevel       IN NUMBER,
         cropArea           IN SDO_NUMBER_ARRAY,
         bandNumbers        IN VARCHAR2,
         means              IN SDO_NUMBER_ARRAY,
         standardDeviations IN SDO_NUMBER_ARRAY,
         storageParam       IN VARCHAR2,
         outGeoraster       IN OUT SDO_GEORASTER,
         parallelParam      IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.normalize(
         inGeoRaster        IN SDO_GEORASTER,
         pyramidLevel       IN NUMBER,
         cropArea           IN SDO_GEOMETRY,
         layerNumbers       IN VARCHAR2,
         means              IN SDO_NUMBER_ARRAY,
         standardDeviations IN SDO_NUMBER_ARRAY,
         storageParam       IN VARCHAR2,
         outGeoraster       IN OUT SDO_GEORASTER,
         parallelParam      IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.normalize(
         inGeoRaster        IN SDO_GEORASTER,
         pyramidLevel       IN NUMBER,
         cropArea           IN SDO_NUMBER_ARRAY,
         bandNumbers        IN VARCHAR2,
         means              IN SDO_NUMBER_ARRAY,
         standardDeviations IN SDO_NUMBER_ARRAY,
         storageParam       IN VARCHAR2,
         rasterBlob         IN OUT BLOB,
         outArea            OUT SDO_GEOMETRY,
         outWindow          OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.normalize(
         inGeoRaster        IN SDO_GEORASTER,
         pyramidLevel       IN NUMBER,
         cropArea           IN SDO_GEOMETRY,
         layerNumbers       IN VARCHAR2,
         means              IN SDO_NUMBER_ARRAY,
         standardDeviations IN SDO_NUMBER_ARRAY,
         storageParam       IN VARCHAR2,
         rasterBlob         IN OUT BLOB,
         outArea            OUT SDO_GEOMETRY,
         outWindow          OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.normalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         refGeoRaster IN SDO_GEORASTER,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.normalize(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         refGeoRaster IN SDO_GEORASTER,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

#### Description

Normalizes the input GeoRaster object using the specified mean and standard deviation.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be normalized.

pyramidLevel
A number specifying the pyramid level to be normalized in the source GeoRaster object. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

means
The target mean values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target mean values must be in the range of the cell depth of the `outGeoRaster` object. If null, it defaults to 128.

standardDeviations
The target standard deviation values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target standard deviation values must be in the range of the cell depth of the `outGeoRaster` object. If null, it defaults to 100.

refGeoRaster
The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of `refGeoRaster` are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

#### Usage Notes

The input GeoRaster object must have statistics generated for each output band.

The reference GeoRaster object must have the same number of bands as the input GeoRaster object. The cell depth of the `refGeoRaster` object cannot be greater than the cell depth of the `outGeoRaster` object. The reference GeoRaster object must have statistics set in the metadata.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

Color map in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object and performs normalization on the bands of the input GeoRaster object based on the given means and standard deviations. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.normalize(gr1, 0, cropArea, null, sdo_number_array(50, 80, 100), sdo_number_array(30, 20, 50), null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following exampleperforms normalization on the bands of the input GeoRaster object based on the given means and standard deviations; the output is in a temporary BLOB. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
      out_lob  BLOB;
      outArea  sdo_geometry := null;
      outWindow sdo_geometry := null;
    BEGIN
      dbms_lob.create_temporary(out_lob, TRUE);

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.normalize(gr1, 0, cropArea, null, sdo_number_array(50, 80, 100), sdo_number_array(30, 20, 50), null, out_lob, outArea, outWindow);
      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);

    END;
    /

The following example creates a GeoRaster object and performs normalization on the bands of the input GeoRaster object based on the given reference GeoRaster object . (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      refgr sdo_georaster;
      cropArea sdo_number_array := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      -- get the source GeoRaster object
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      -- get the reference GeoRaster object
      SELECT georaster INTO refgr FROM georaster_table WHERE georid=5;

      sdo_geor_ip.normalize(gr1, 0, cropArea, null, refgr, null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.6 SDO_GEOR_IP.piecewiseStretch

#### Format

    SDO_GEOR_IP.piecewiseStretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         inValues     IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         outValues    IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.piecewiseStretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         inValues     IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         outValues    IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         storageParam IN VARCHAR2,
         outGeoraster IN OUT SDO_GEORASTER,
         parallelParam IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_IP.piecewiseStretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_NUMBER_ARRAY,
         bandNumbers  IN VARCHAR2,
         inValues     IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         outValues    IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.piecewiseStretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel IN NUMBER,
         cropArea     IN SDO_GEOMETRY,
         layerNumbers IN VARCHAR2,
         inValues     IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         outValues    IN SDO_NUMBER_ARRAYSET DEFAULT NULL,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

#### Description

Performs a linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object or in a BLOB.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be stretched.

pyramidLevel
A number specifying the pyramid level to be stretched in the source GeoRaster object. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

inValues
An array of SDO_NUMBER_ARRAY objects corresponding to each input band. If only one element is specified, all the output bands are stretched in the same way. Each SDO_NUMBER_ARRAY specifies the input GeoRaster object cell value ranges used in the stretch. For example, sdo_number_array(0, 50, 255) specifies two value ranges, from 0 to 50 and 50 to 255.

outValues
An array of SDO_NUMBER_ARRAY objects corresponding to each output band. If only one element is specified, all the output bands are stretched in the same way. Each SDO_NUMBER_ARRAY specifies the target values ranges corresponding to the value ranges of the `inValues` parameter. For example, sdo_number_array(0, 200, 255) specifies two value ranges, from 0 to 200 and 200 to 255.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

#### Usage Notes

The `inValues` and `outValues` parameters must have the same number of values, and the range specified in the `inValues` parameter must be in ascending order. The values in the `inValues` parameter must be in the range of the cell depth of the `inGeoRaster` object. The values in the `outValues` parameter must be in the range of the cell depth of the `outGeoRaster` object.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

Color map stored in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object that piecewise stretches all bands of the input GeoRaster object into different cell depths: a linear stretch of input values between 0 and 255 to the range 0 to 2000. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
      inValues sdo_number_arrayset;
      outValues sdo_number_arrayset;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      -- define the input and output value ranges
      inValues := sdo_number_arrayset(sdo_number_array(0, 255));
      outValues := sdo_number_arrayset(sdo_number_array(0, 2000));

      sdo_geor_ip.piecewisestretch(gr1, 0, cropArea, null,
                    inValues, outValues, 'celldepth=16bit_u', gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example piecewise stretches each band for different ranges; the output is in a temporary BLOB. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      cropArea sdo_number_array := null;
      inValues sdo_number_arrayset;
      outValues sdo_number_arrayset;
      out_lob  BLOB;
      outArea  sdo_geometry := null;
      outWindow sdo_geometry := null;
     BEGIN
      dbms_lob.create_temporary(out_lob, TRUE);

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      -- define the input and output values ranges
      inValues := sdo_number_arrayset(sdo_number_array(0, 30, 80, 255),
                                      sdo_number_array(0, 10, 50, 255),
                                      sdo_number_array(0, 50, 150, 255));
      outValues := sdo_number_arrayset(
                       sdo_number_array(0, 80, 200, 255),
                       sdo_number_array(0, 60, 150, 255),
                       sdo_number_array(0, 100, 250,255) );

      sdo_geor_ip.piecewisestretch(gr1, 0, cropArea, null, inValues, outValues,
                                         null, out_lob, outArea, outWindow);

      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);

    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference

### 11.7 SDO_GEOR_IP.stretch

#### Format

    SDO_GEOR_IP.stretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_NUMBER_ARRAY,
         bandNumbers   IN VARCHAR2,
         minValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         maxValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam  IN VARCHAR2,
         outGeoraster  IN OUT SDO_GEORASTER),
         parallelParam IN VARCHAR2 DEFAULT NULL);    

or

    SDO_GEOR_IP.stretch(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_GEOMETRY,
         layerNumbers  IN VARCHAR2,
         minValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         max_values    IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam  IN VARCHAR2,
         outGeoraster  IN OUT SDO_GEORASTER),
         parallelParam IN VARCHAR2 DEFAULT NULL); 

or

    SDO_GEOR_IP.stretch(
         inGeoRaster  IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_NUMBER_ARRAY,
         bandNumbers   IN VARCHAR2,
         minValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         maxValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

or

    SDO_GEOR_IP.stretch(
         inGeoRaster   IN SDO_GEORASTER,
         pyramidLevel  IN NUMBER,
         cropArea      IN SDO_GEOMETRY,
         layerNumbers  IN VARCHAR2,
         minValues     IN SDO_NUMBER_ARRAY DEFAULT NULL,
         max_values    IN SDO_NUMBER_ARRAY DEFAULT NULL,
         storageParam IN VARCHAR2,
         rasterBlob   IN OUT BLOB,
         outArea      OUT SDO_GEOMETRY,
         outWindow    OUT SDO_NUMBER_ARRAY);

#### Description

Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object or in a BLOB.

#### Parameters

inGeoRaster
The SDO_GEORASTER object to be stretched.

pyramidLevel
A number specifying the pyramid level to be stretched in the source GeoRaster object. If null, the default is 0.

cropArea
Crop area definition. If `cropArea` is of type SDO_GEOMETRY, use the `layerNumbers` parameter to specify one or more layer numbers; if `cropArea` is of type SDO_NUMBER_ARRAY, use the `bandNumbers` parameter to specify one or more band numbers.

If the data type is SDO_NUMBER_ARRAY, the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed. If the data type is SDO_GEOMETRY, the minimum bounding rectangle (MBR) of the geometry object is used as the crop area; see also the Usage Notes for SDO_SRID requirements.

bandNumbers
A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `1-3` for bands 1, 2, and 3).

layerNumbers
A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, `2-4` for layers 2, 3, and 4).

minValues
The minimum values of the bands to be stretched. If it is null, the minimum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the SDO_NUMBER_ARRAY, it is used as the minimum value of all the input bands; otherwise, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands of the output GeoRaster object.

maxValues
The maximum values of the bands to be stretched. If it is null, the maximum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the SDO_NUMBER_ARRAY, it is used as the maximum value of all the input bands; otherwise, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands of the output GeoRaster object.

storageParam
A string specifying storage parameters, as explained in [Storage Parameters](georaster-overview-and-concepts.md).

outGeoRaster
The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) Cannot be the same GeoRaster object as `inGeoRaster`.

parallelParam
Specifies the degree of parallelism for the operation. If specified, must be in the form `parallel=`n, where n is greater than 1. The database optimizer uses the degree of parallelism specified by this parameter. If not specified, then by default there is no parallel processing. (For more information, see [Parallel Processing in GeoRaster](georaster-overview-and-concepts.md).)

If parallelism is specified, the procedure performs an internal commit while the process is running. Therefore, you cannot roll back the results of this procedure. If an error occurs (even if it is raised by the Oracle parallel server), you must delete the resulting output GeoRaster object explicitly in order to roll back the operation.

rasterBlob
BLOB to hold the output of the processing result. It must exist or have been initialized before the operation.

outArea
An SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

outWindow
An SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

#### Usage Notes

The input GeoRaster object is stretched to 0-255 using the values in `minValues` and `maxValues` parameters, or the minimum and maximum values stored in the statistics metadata of the image. If the `minValues` and `maxValues` parameters are null, the input GeoRaster object must have the statistics set in its metadata.

The cell depth of the output GeoRaster object is always `8BIT_U`. When a GeoRaster image needs to be stretched to an image with a cell depth other than `8BIT_U`, you can use SDO_GEOR_IP.piecewiseStretch.

If the `cropArea` parameter data type is SDO_GEOMETRY, the SDO_SRID value must be one of the following:

- Null, to specify raster space

- A value from the SRID column of the MDSYS.CS_SRS table

  If the SDO_SRID values for the `cropArea` parameter geometry and the model space are different, the `cropArea` parameter geometry is automatically transformed to the coordinate system of the model space before the operation is performed. (Raster space and model space are explained in [GeoRaster Data Model](georaster-overview-and-concepts.md).)

Color map stored in the input GeoRaster object is not supported.

The output GeoRaster object has no pyramid or mask.

#### Examples

The following example creates a GeoRaster object that stretches band 2 of the input GeoRaster object from value range of (30, 150) to (0, 255). (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.stretch(gr1, 0, cropArea, '2', sdo_number_array(30), sdo_number_array(150), null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

The following example stretches band 2 of the input GeoRaster object from value range of (30, 150) to (0, 255); the output is in a temporary BLOB. (It refers to a table named GEORASTER_TABLE, whose definition is presented after [Example 1-1](georaster-overview-and-concepts.md) in [Storage Parameters](georaster-overview-and-concepts.md).)

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_number_array := null;
      out_lob  BLOB;
      outArea  sdo_geometry := null;
      outWindow sdo_geometry := null;
     BEGIN
      dbms_lob.create_temporary(out_lob, TRUE);

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.stretch(gr1, 0, cropArea, '2', sdo_number_array(30), sdo_number_array(150), null, out_lob, outArea, outWindow);

      if outWindow is not null then
         dbms_output.put_line('output window: (' || outWindow(1) || ',' ||
                               outWindow(2) || ',' || outWindow(3) || ',' || outWindow(4) || ')');
      end if;
      dbms_lob.freeTemporary(out_lob);
    END;
    /

**Parent topic:** SDO_GEOR_IP Package Reference
