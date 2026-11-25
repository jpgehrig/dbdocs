## 10 SDO_GEOR_GDAL Package Reference

The SDO_GEOR_GDAL package integrates the open source software GDAL with Oracle Database Server through external procedures and provides PL/SQL APIs to execute a set of GDAL operations. This chapter presents reference information, with one or more examples, for each subprogram.

**Note:**

The SDO_GEOR_GDAL package is not supported in Oracle Autonomous Database in both shared and dedicated deployments.

The functions and procedures in the SDO_GEOR_GDAL package execute on the Oracle Database server machine and can work together with any other GeoRaster PL/SQL APIs.

Currently, the SDO_GEOR_GDAL package is only available on Windows x64 and Linux x86-64 operating systems.

For more information, including configuration requirements, see [Using the SDO_GEOR_GDAL Package](georaster-overview-and-concepts.md).

- SDO_GEOR_GDAL.dem
- SDO_GEOR_GDAL.translate

### 10.1 SDO_GEOR_GDAL.dem

#### Format

    SDO_GEOR_GDAL.dem(
         inGeoRaster     IN SDO_GEORASTER,
         outGeoRaster    IN OUT SDO_GEORASTER,
         processing      IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         createOptions   IN VARCHAR2 DEFAULT NULL,
         metadataOptions IN VARCHAR2 DEFAULT NULL,
         colorDirectory  IN VARCHAR2 DEFAULT NULL,
         colorFileName   IN VARCHAR2 DEFAULT NULL,
         openOptions     IN VARCHAR2 DEFAULT NULL);

#### Description

Processes an input Digital Elevation Model (DEM) to produce an output GeoRaster object that reflects specified processing and translation options.

#### Parameters

inGeoRaster
GeoRaster object, typically a Digital Elevation Model (DEM).

outGeoRaster
GeoRaster object to hold the result of the operation. Must be a valid initialized GeoRaster object. Cannot be the same GeoRaster object as `inGeoRaster`

processing
When specified, identifies the name of the DEM processing technique to apply:

- `aspect` generates an aspect map.

- `color-relief` generates a color relief map.

- `hillshade` generates a shaded relief map.

- `Roughness` generates a map of roughness.

- `slope` generates a slope map.

- `TPI` generates a map of Topographic Position Index.

- `TRI` generates a map of Terrain Ruggedness Index.

options
When specified, identifies options for the GDAL translate operation. See the Usage Notes for a table of names and explanations of possible `options` parameter values.

Example: `options => 'outputType=float32'`

createOptions
When specified, identifies options specific to the output driver. Format 'name=value', with options separated by space. Example: `"COMPRESS=JPEG-F GENPYRAMID=NN"`

metadataOptions
When specified, assigns metadata values specific to the output driver. Format 'name=value', with options separated by space. Example: `"TIFFTAG_POINTAREA=AREA"`

colorDirectory
When specified, identifies the name of a directory object related to the file system directory where the input color table file is located.

colorFileName
When specified, identifies the base file name of a GDAL compatible color table file.

openOptions
When specified, identifies ptions specific to the input driver format. See the GDAL supported format list for details.

#### Usage Notes

The `openOptions` parameter possible keywords are listed in the following table.

Table 10-1 openOptions Parameter Possible Values for dem Operations

| Keyword         | Explanation                                                                                                                                                                                                                                                                                                                           |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `alg`           | Indicates whether to use the ZevenbergenThorne algorithm instead of Horn’s formula. Boolean type; default is `false`.                                                                                                                                                                                                                 |
| `altitude`      | For `hillshade` processing only. Indicates the altitude of the light, in degrees (90 if the light comes from above the DEM, 0 if it is raking light).                                                                                                                                                                                 |
| `azimuth`       | For `hillshade` processing only. The default value is 315. It should rarely be changed, because this is the value generally used to generate shaded maps.                                                                                                                                                                             |
| `band`          | Band number that identifies the DEM. Values start at 1 (the default).                                                                                                                                                                                                                                                                 |
| `Combined`      | For `hillshade` processing only. Indicates whether to compute combined shading, a combination of slope and oblique shading.                                                                                                                                                                                                           |
| `computeEdges`  | Indicates whether to compute values at raster edges or not. Boolean type; default is `false`.                                                                                                                                                                                                                                         |
| `outputType`    | Output pixel data type. Supported values are: `Byte`, `Int16`, `UInt16`, `UInt32`, `Int32`, `Float32`, `Float64`, `CInt16`, `CInt32`, `CFloat32` , and `CFloat64`. Example: `'outputtype=float64'`<br>If this option is not specified, the input data type will be used.<br>Check if the output format supports the data type in use. |
| `scale`         | Indicates the ratio to multiply the vertical units. For example, use `scale=111120` if the vertical units are meters (or `scale=370400` if they are in feet) and need to be converted.                                                                                                                                                |
| `Trigonometric` | For `aspect` processing only. Indicates whether to return the trigonometric angle instead of azimuth. `0deg` means East, `90deg` means North, `180deg` means West, and `270deg` means South.                                                                                                                                          |
| `zeroForFlat`   | For `aspect` processing only. Indicates whether to return 0 for flat areas with `slope=0`, instead of -9999.                                                                                                                                                                                                                          |
| `zFactor`       | For `hillshade` processing only, indicate the vertical exaggeration.                                                                                                                                                                                                                                                                  |

For convenience, the arguments of the `options` parameter can also be entered in the same format as the GDAL `gdal_dem` command line tool. Example: `”-b 1 –scale 10”`

#### Examples

The following example produces an aspect map from an input DEM.

    DECLARE
      gr6 sdo_georaster;
      gr7 sdo_georaster;
    BEHIN
      delete from imagery where id = 7;
      insert into imagery values(7, sdo_geor.init('dem_rdt',7))
             returning raster into gr7;
      select raster into gr6 from imagery where id = 6;
      sdo_geor_gdal.dem(inGeoRaster     => gr6,
                        outGeoRaster    => gr7,
                        processing      => 'aspect',
                        options         => 'outputType=float32');
      update imagery set raster = gr7 where id = 7;
      commit;
    END;

**Parent topic:** SDO_GEOR_GDAL Package Reference

### 10.2 SDO_GEOR_GDAL.translate

#### Format

    SDO_GEOR_GDAL.translate(
         inDirectory     IN SDO_VARCHAR2,
         InFileName      IN OUT SDO_VARCHAR2,
         outGeoRaster    IN OUT SDO_GEORASTER,
         options         IN VARCHAR2 DEFAULT NULL,
         createOptions   IN VARCHAR2 DEFAULT NULL,
         metadataOptions IN VARCHAR2 DEFAULT NULL,
         openOptions     IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_GDAL.translate(
         inGeoRaster     IN SDO_GEORASTER,
         outDirectory    IN VARCHAR2,
         outFileName     IN VARCHAR2,
         options         IN VARCHAR2 DEFAULT NULL,
         createOptions   IN VARCHAR2 DEFAULT NULL,
         metadataOptions IN VARCHAR2 DEFAULT NULL,
         openOptions     IN VARCHAR2 DEFAULT NULL);

or

    SDO_GEOR_GDAL.translate(
         inGeoRaster     IN SDO_GEORASTER,
         outGeoRaster    IN OUT SDO_GEORASTER,
         options         IN VARCHAR2 DEFAULT NULL,
         createOptions   IN VARCHAR2 DEFAULT NULL,
         metadataOptions IN VARCHAR2 DEFAULT NULL,
         openOptions     IN VARCHAR2 DEFAULT NULL);

#### Description

Converts raster data between different formats, potentially performing some operations like subsettings, resampling, and rescaling pixels in the process.

#### Parameters

inDirectory
The name of a directory object pointing at the system directory containing the input file.

inFileName
A base file name (file name without path) of any GDAL compatible raster data source specification.

inGeoRaster
Input GeoRaster object.

outGeoRaster
GeoRaster object to hold the result of the operation. Must be a valid initialized GeoRaster object. Cannot be the same GeoRaster object as `inGeoRaster`.

outDirectory
The name of a directory object pointing at the system directory to contain the output file.

outFileName
Name of the output file.

options
When specified, identifies options for the GDAL translate operation. See the Usage Notes for a table of names and explanations of possible `options` parameter values.

Example: `options => 'srcwin=100,100,2500,2500'`

createOptions
When specified, identifies options specific to the output driver. Format 'name=value', with options separated by space. Example: `"COMPRESS=JPEG-F GENPYRAMID=NN"`.

metadataOptions
When specified, assigns metadata values specific to the output driver. Format 'name=value', with options separated by space. Example: `"TIFFTAG_POINTAREA=AREA"`.

openOptions
When specified, identifies ptions specific to the input driver format. See the GDAL supported format list for details.

#### Usage Notes

This function performs the same action as the GDAL `translate` command.

The options parameter possible keywords are listed in the following table.

Table 10-2 options Parameter Possible Values for translate Operations

| Keyword          | Explanation                                                                                                                                                                                                                                                                                                                         |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bandList`       | Array of band numbers. Integer list; 1 is the first band. Example: `'bandlist=4,3,2'`<br>If not specified, the band list from the input file will be used.                                                                                                                                                                          |
| `eco`            | Show error when `projWin` is completely outside. Boolean type; default is `false`. Example: `'eco=true'`                                                                                                                                                                                                                            |
| `epo`            | Show error when `projWin` is partially outside. Boolean type; default is `false`. Example: `'epo=true'`                                                                                                                                                                                                                             |
| `exponentList`   | Apply non linear scaling with a power function. Must be positive. Used with the scale option. Example: ` 'exponent=10,100'`                                                                                                                                                                                                         |
| `format`         | The name of GDAL driver that support dataset creating. String type. Example: `'format=gtiff'`. This option is not needed for sdo_georaster output. For file output, if this option is not specified, 'GTIFF' is assumed.                                                                                                            |
| `GCP`            | Ground Control Points. May be provided multiple times to provide a set of GCPs. In the format `“pixel,line,easting,northing,elevation”` where elevation is optional. Example: `“gcp=10,40,234.2,734 gcp=13,54,28.4,837 gcp=20,90,285.2,934”`                                                                                        |
| `maskBandList`   | Array of band numbers. Integer list, where 1 is the first band. Example: `'maskbandlist=1'`<br>If not specified, the band list from the input file will be used.                                                                                                                                                                    |
| `nodata`         | List of Nodata value (or `none` to unset it) for each output band. Example: `”nodata=9990”`                                                                                                                                                                                                                                         |
| `outputBounds`   | Assigned the output bounds of the output image in the format `“upper-left-x, upper-left-y, lower-right-x, lower-right-y”`. Example: `'outputbounds=293.992,643.447,361.104, 118.648'`                                                                                                                                               |
| `outputBoundSRS` | The spatial reference system (SRS) for `outputBounds`. Example: `outputBoundsSRS=EPSG:4326`. If not specified, assumes the input image SRS.                                                                                                                                                                                         |
| `outputType`     | Output pixel data type. Supported values are: `Byte`, `Int16`, `UInt16`, `UInt32`, `Int32`, `Float32`, `Float64`, `CInt16`, `CInt32`, `CFloat32`, and `CFloat64`. Example: `'outputtype=float64'`<br>If this option is not specified, the input data type will be used.<br>Check if the output format support the data type in use. |
| `outsize`        | Set the size of the output image defined by rows and columns or by the relative percentage of the original image size. Example:<br>`'outsize=50%,50%', 'outsize=1024,512', 'outsize=200%,200%'`<br>If not specified, the original size of the input image will be used.                                                             |
| `projWin`        | Source window sub region from input image defined in coordinates as in `“upper-left-x, upper-left-y, lower-right-x, lower-right-y”`. Example: `'srcwin=180,90,0,0'`. If not specified, the entire input image will be used.                                                                                                         |
| `projWinSRS`     | The spatial reference system (SRS) for `projWin`. Example: `projWinSRS=EPSG:4326`. If not specified, assumes the input image SRS.                                                                                                                                                                                                   |
| `rat`            | Indicate whether to copy the source image raster attribute table to the output image . Default is `true`. Example: “rat=false”<br>The operation depend on the capacity of the output format to support raster attribute table.                                                                                                      |
| `resampleAlg`    | Resampling mode {`nearest`(default), `bilinear`, `cubic`, `cubicspline`, `lanczos`, `average`, `mode`}. Example:: `resample=cubic`                                                                                                                                                                                                  |
| `rgbExpand`      | Indicate whether to translate a dataset with 1 band with a color table as a dataset with 3 (RGB) or 4 (RGBA) bands. Expands a dataset with a color table that only contains gray levels to a gray indexed dataset. {`gray|rgb|rgba`}. Example: `“rgbExpand=rgb”`                                                                    |
| `scale`          | List of values to rescale the pixel values from the input image to the output image. The values cam be defined as `“src_min,src_max”` or `“src_min,src_max,dst_min,dst_max”`. Example: `'scale=-10,2400,0,255'`                                                                                                                     |
| `srcWin`         | Source window subregion from input image defined in pixels coordinates as in `“left_x, top_y, width, height”`. Example: `'srcwin=10,31,400,800'`<br>If not specified, the entire input image will be used.                                                                                                                          |
| `stats`          | Calculate and store statistics on output image. Boolean type; default is `false`. Example: `'stats=true'`                                                                                                                                                                                                                           |
| `strict`         | Raise an error if are data type mismatches and lost data when translating to the output format. Boolean type; default is `false`. Example: `'strict=true'`                                                                                                                                                                          |
| `xyRes`          | Output horizontal and vertical output image resolution. Example: : `'xyres=30.0,30.0'`. If not specified, the resolution of the input image will be used.                                                                                                                                                                           |

For convenience, the arguments of the `options` parameter can also be entered in the same format as the GDAL `gdal_translate` command line tool. Example: `“-srcwin 10 10 512 512 –outsize 1024 1024“`

#### Examples

The following example loads a geotiff file from the file system to an initialized GeoRaster object.

    CREATE OR REPLACE DIRECTORY mydata_dir AS '/folder_name/data/';

    BEGIN
      delete from imagery where id = 1;
      insert into imagery values(1, sdo_geor.init('imagery_rdt',1))
             returning raster into gr;
      sdo_geor_gdal.translate(inDirectory   => 'mydata_dir',
                              inFileName    => 'sample.tif',
                              outGeoRaster  => gr);
      update imagery set raster = gr where id = 1;
      commit;
    END;

The following example exports a GeoRaster object to a geotiff file.

    CREATE OR REPLACE DIRECTORY dump_dir AS '/folder_name/dump/';

    DECLARE
      gr sdo_georaster;
    BEGIN
      select raster into gr from imagery where id = 1;
      sdo_geor_gdal.translate(inGeoRaster   => gr,
                              outDirectory  => 'dump_dir',
                              outFileName   => 'copy_imagery_id_1.tif');
    END;

The following example copies a GeoRaster object into another cropping part of the image while changing the resolution and the scale of values.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      delete from imagery where id = 2;
      select raster into gr1 where id = 2;
      insert into imagery values(2, sdo_geor.init('imagery',2))
             returning raster into gr2;
      sdo_geor_gdal.translate(
                    inGeoraster   => gr1,
                    options       => 'srcwin=100,100,2500,2500' ||
                                     'scale=0,255' ||
                                     'resxy=400,400',
                    outGeoRaster  => gr);
      update imagery set raster = gr2 where id = 2;
      commit;
    END;

The following example exports a GeoRaster object into a file in Erdas `.img` format.

    CREATE OR REPLACE DIRECTORY myoutput_dir AS '/folder_name/data/';

    DECLARE
      gr sdo_georaster;
    BEGIN
      select raster into gr where id = 3;
      sdo_geor_gdal.translate(
                    inGeoraster   => gr,
                    outDirectory  => myoutput_dir,,
                    outFilename   => 'exported.img',
                    options       => 'format=hfa');
    END;

**Parent topic:** SDO_GEOR_GDAL Package Reference
