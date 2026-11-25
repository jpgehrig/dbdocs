## Changes in This Release for Oracle Spatial and Graph Developer's Guide

This preface contains:

- Changes in Oracle Database Release 19c

### Changes in Oracle Database Release 19c

The following are major Release 19c new features and changes for core Spatial and Graph capabilities covered in this and several other books:

- New JSON support in addition to GeoJSON. New JSON support is introduced to support all the data that can be represented with SDO_GEOMETRY (both from and to functions); this is in addition to the GeoJSON support introduced in Release 12.2.0.1.
- Spatial operator support without a spatial index:
  - A spatial index is recommended when querying against tables; but when queries need to be written against views where the geometry data is constructed on the fly, not using a spatial index allows the queries to be written the same way as if the data is coming from a table.
  - Data can be in NFS files, HDFS, and Object Store.
  - Data can be from a JOIN view or some other complex view.
  - Data can be stored in an external table using text format for geometry.
- Support for distributed transactions. R-tree index updates were not supported for distributed transactions before Release 19c.
- Sharding in the database: Spatial tables and indexes are now supported with Database Sharding.
- The location tracking server is updated to support INSIDE/OUTSIDE/TRANSIT states and have improved scalability.
- Web Services:
  - The OpenGIS Catalogue Services Specification (CSW) 2.0.2 ISO Metadata Application Profile is supported.
  - Multiple data source support: WFS/CS-W/WCS can support reading the data from multiple data sources in the same WebLogic Server instance.
- Map Visualization (documented in [Oracle Spatial and Graph Map Visualization Developer's Guide](../jimpv/index.md)):
  - Define tile layer dynamically in the V2 API (instead of pre-built in the server and stored permanently in metadata view).
  - Specify or change rendering style as needed.
  - Server generates tile images just like regular tile layers.
  - Large and complex queries supported, without unnecessary storage and management overhead.
  - Offline map cache for detached applications.
  - Vector tiles for thematic data.
- GeoRaster (documented in [Oracle Spatial and Graph GeoRaster Developer's Guide](../geors/index.md)):
  - Raster algebra support: All subprograms in the SDP_GEOR_RA package and the Java API support putting the result data in a temporary BLOB so that users can do raster analysis and cartographic modeling on-the-fly to support various real time applications.
  - GeoRaster must be enabled at schema level. (In previous releases, GeoRaster is enabled for the whole database.) This change enhances database security for the cloud.
- Oracle Locator Information Removed:
  - In previous versions, the ability to use the full set of Oracle Spatial and Graph required Oracle Database Enterprise Edition, whereas a subset of those features called Oracle Locator did not require Enterprise Edition. Now, however, all Oracle Spatial and Graph capabilities are available with both Enterprise Edition and Standard Edition 2.

    Therefore, references to Oracle Locator, including distinctions between it and Oracle Spatial and Graph, have been removed from this version of the manual.

**Parent topic:** Changes in This Release for Oracle Spatial and Graph Developer's Guide
