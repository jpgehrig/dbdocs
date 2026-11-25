## Changes in This Release for Oracle Spatial and Graph GeoRaster Developer's Guide

This preface contains the following.

- Changes in Oracle Database 19.1
- Changes in Oracle Database 18.1

### Changes in Oracle Database 19.1

The following are changes in Oracle Spatial and Graph GeoRaster Developer's Guide for Oracle Database 19.1.

- GeoRaster Must Be Enabled at Schema Level
- SDO_GEOR_RA Support for Result Data in a BLOB

**Parent topic:** Changes in This Release for Oracle Spatial and Graph GeoRaster Developer's Guide

#### GeoRaster Must Be Enabled at Schema Level

The GeoRaster feature of Oracle Spatial and Graph must be enabled for each schema that will be using GeoRaster. In previous releases, you enabled GeoRaster for the entire database (by executing a procedure named MDSYS.enableGeoRaster).

See [Enabling GeoRaster at the Schema Level](georaster-database-creation-management.md) for information and instructions. See also the following new PL/SQL related subprograms:

- [SDO_GEOR_ADMIN.enableGeoRaster](SDO_GEOR_ADMIN-reference.md) (enable GeoRaster for the current schema)

- [SDO_GEOR_ADMIN.isGeoRasterEnabled](SDO_GEOR_ADMIN-reference.md) (check if GeoRaster is enabled for the current schema)

**Parent topic:** Changes in Oracle Database 19.1

#### SDO_GEOR_RA Support for Result Data in a BLOB

All subprograms in the SDO_GEOR_RA package support putting the result data in a BLOB to support on-the-fly raster algebra. These subprograms include one or more formats that include a parameter named `rasterBlob`.

For information, see the individual subprogram topics in the [SDO_GEOR_RA Package Reference](sdo-geor-ra-ref.md) chapter.

**Parent topic:** Changes in Oracle Database 19.1

### Changes in Oracle Database 18.1

The following are changes in Oracle Spatial and Graph GeoRaster Developer's Guide for Oracle Database 18.1.

- New SDO_GEOR_GDAL Package
- GeoRaster PL/SQL API Changes
- GeoRaster Java API Changes
- 4GB Limit Removed for External JPEG 2000 Image Files
- Mixed Case User and Schema Names Supported

**Parent topic:** Changes in This Release for Oracle Spatial and Graph GeoRaster Developer's Guide

#### New SDO_GEOR_GDAL Package

The new SDO_GEOR_GDAL PL/SQL package integrates part of GDAL into Oracle database server. It provides server-side raster data loading, exporting, and in-database terrain analysis and visualization capabilities. It also enables and simplifies development of C/C++ plug-ins through the GDAL API.

For a description of this package and reference information about its subprograms, see [SDO_GEOR_GDAL Package Reference](SDO_GEOR_GDAL-reference.md).

**Parent topic:** Changes in Oracle Database 18.1

#### GeoRaster PL/SQL API Changes

The following changes relate to GeoRaster PL/SQL subprograms.

- Several SDO_GEOR_IP subprograms have new formats with BLOB as output to support on-the-fly image processing and visualization: [SDO_GEOR_IP.equalize](SDO_GEOR_IP-reference-ref.md), [SDO_GEOR_IP.filter](SDO_GEOR_IP-reference-ref.md), [SDO_GEOR_IP.normalize](SDO_GEOR_IP-reference-ref.md), [SDO_GEOR_IP.piecewiseStretch](SDO_GEOR_IP-reference-ref.md), [SDO_GEOR_IP.stretch](SDO_GEOR_IP-reference-ref.md).

- Many SDO_GEOR_RA subprograms have new formats to support putting the result data in a BLOB instead of a GeoRaster object. These new BLOB-related formats include the parameters `rasterBlob`, `outArea`, and `outWindow`. The reference information for all of these subprograms is in [SDO_GEOR_RA Package Reference](sdo-geor-ra-ref.md).

- A new format for [SDO_GEOR_IP.dodge](SDO_GEOR_IP-reference-ref.md) dodges an image to a reference image.

- The new SDO_GEOR_AGGR.getMosaicStatistics procedure generates statistics and a histogram for virtual mosaics.

- A new pipelined table function for [SDO_GEOR.getRasterSubset](SDO_GEOR-reference.md) returns a table of cell values, so that users can leverage SQL analytics more easily.

**Parent topic:** Changes in Oracle Database 18.1

#### GeoRaster Java API Changes

The following changes relate to GeoRaster Java API.

- Java APIs are added for the new PL/SQL functions and procedures, except for the SDO_GEOR_GDAL package.

- New global image processing functions are added to the Java API, including automatic linear stretching, manual linear stretching, piecewise stretching, normalization, and equalization. These functions allow image processing based on the statistics of the GeoRaster object to achieve consistent visualization enhancements for large images and virtual mosaics.

  The GeoRaster Viewer is enhanced to use the new set of global image processing in the Java API.

Reference information about the GeoRaster Java API is included in [Oracle Spatial and Graph Java API Reference](../spajv/index.md).

**Parent topic:** Changes in Oracle Database 18.1

#### 4GB Limit Removed for External JPEG 2000 Image Files

The size limit of 4GB for external JPEG 2000 image files is removed, so that such large JPEG 2000 images can be directly loaded into database without decompression.

**Parent topic:** Changes in Oracle Database 18.1

#### Mixed Case User and Schema Names Supported

Mixed case user names and schema names are supported for use with GeoRaster.

**Parent topic:** Changes in Oracle Database 18.1
