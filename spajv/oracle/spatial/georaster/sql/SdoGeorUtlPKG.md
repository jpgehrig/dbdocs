Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SdoGeorRaPKG.md)
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.georaster.sql

## Class SdoGeorUtlPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorUtlPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorUtlPKG
      extends java.lang.Object

  SdoGeorUtlPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR_UTL. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorUtlPKG
         SdoGeorUtlPKG  pkg=new SdoGeorUtlPKG(connection);
         //reading a GeoRaster object from database based on a query
         Statement stmt = connection.createStatement();
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         rs.next();
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster = new SdoGeoRaster(geor);
         //calcRasterStorageSize
         size=pkg.calcRasterStorageSize(sdoGeoRaster);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------|
    | `SdoGeorUtlPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorUtlPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                      | Method and Description                                                                                                                                                                                                                                                                                                   |
    |----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.math.BigDecimal[]`               | `calcOptimizedBlockSize``(long[] dimensionSize, long[] blockSize, long pyramidLevel)`<br>Calculates an optimal blockSize value that will use less padding space in the GeoRaster object storage, based on the GeoRaster dimension sizes and the user-specified block size values.                                        |
    | `double`                               | `calcRasterNominalSize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, boolean padding, boolean pyramid, boolean bitmapMask)`<br>Returns the total raster block length (in bytes) of a GeoRaster object, as if it were not compressed and did not contain any empty raster blocks.                                      |
    | `double`                               | `calcRasterStorageSize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster)`<br>Returns the actual length (in bytes) of all raster blocks of a GeoRaster object.                                                                                                                                                             |
    | `double`                               | `calcSurfaceArea``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` window, int parallel)`<br>Calculates the three dimensional (3D) surface area represented by digital elevation model (DEM) data that is stored in a GeoRaster object.                                      |
    | `void`                                 | `clearReportTable``(java.lang.Long client_id)`<br>Deletes records in the table that contains GeoRaster operation status information.                                                                                                                                                                                     |
    | `void`                                 | `createDMLTrigger``(java.lang.String tableName, java.lang.String columnName)`<br>Creates the required standard GeoRaster data manipulation language (DML) trigger on a GeoRaster column in a GeoRaster table, so that the appropriate operations are performed when its associated trigger is fired.                     |
    | `void`                                 | `createReportTable``()`<br>Creates the table to contain GeoRaster operation status information.                                                                                                                                                                                                                          |
    | `void`                                 | `disableReport``()`<br>Disables status reporting on GeoRaster operations in the current session.                                                                                                                                                                                                                         |
    | `void`                                 | `dropReportTable``()`<br>Drops the table that contains GeoRaster operation status information.                                                                                                                                                                                                                           |
    | `void`                                 | `emptyBlocks``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, double[] bgValues)`<br>Trims all blocks that contain only the specified background values to empty LOBs, thus making them empty blocks.                                                                                                                    |
    | `void`                                 | `enableReport``()`<br>Enables status reporting on GeoRaster operations in the current session.                                                                                                                                                                                                                           |
    | `void`                                 | `fillEmptyBlocks``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster, double[] bgValues)`<br>Fills in all empty blocks with specified background values.                                                                                                                                                                     |
    | [`GeorColormap`](../GeorColormap.md)   | `generateColorRamp``(`[`GeorColormap`](../GeorColormap.md)` colorSeeds, java.math.BigDecimal[] rampSteps, java.lang.String cellValueType, java.lang.String interpoParam)`<br>Generates an SDO_GEOR_COLORMAP object with a color ramp (gradient) by interpolating the red, green, blue, and alpha values entered as seed. |
    | [`GeorGrayscale`](../GeorGrayscale.md) | `generateGrayRamp``(`[`GeorGrayscale`](../GeorGrayscale.md)` grayScale, java.math.BigDecimal[] rampSteps, java.lang.String cellValueType, java.lang.String interpoParam)`<br>Generates an SDO_GEOR_GRAYSCALE object with a grayscale ramp (gradient) by interpolating the values entered as seed.                        |
    | `java.lang.String`                     | `getAllStatusReport``()`<br>Returns the current status for all operations for all clients in the status table.                                                                                                                                                                                                           |
    | `java.sql.Connection`                  | `getConnection``()`<br>Returns a connection which points to target database.                                                                                                                                                                                                                                             |
    | `long`                                 | `getMaxMemSize``()`<br>Returns the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.                                                                                                                                                                                |
    | `double`                               | `getProgress``(long client_id, long seq_id)`<br>Returns the progress of the operation for a specified client (session) and optionally for a specified operation.                                                                                                                                                         |
    | `long`                                 | `getReadBlockMemSize``()`<br>Returns the size in bytes of the GeoRaster internal data block for read-only operations.                                                                                                                                                                                                    |
    | `java.lang.String`                     | `getStatusReport``(long client_id, long seq_id)`<br>Returns the current status of the operations in the status table for a specified client (session) and optionally for a specified operation.                                                                                                                          |
    | `long`                                 | `getWriteBlockMemSize``()`<br>Returns the size in bytes of the GeoRaster internal data block for read/write operations.                                                                                                                                                                                                  |
    | `int`                                  | `isReporting``()`<br>Checks if any session has status reporting enabled.                                                                                                                                                                                                                                                 |
    | `void`                                 | `makeRDTNamesUnique``()`<br>Renames some existing registered raster data tables that do not have unique names so that all raster data table names are unique within the database, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.                                     |
    | `void`                                 | `recreateDMLTriggers``()`<br>Re-creates the required standard GeoRaster data manipulation language (DML) triggers on all GeoRaster columns that the current user has privileges to access, so that the appropriate operations are performed when the triggers are fired.                                                 |
    | `void`                                 | `renameRDT``(java.lang.String oldRDT, java.lang.String newRDT)`<br>Renames one or more existing registered raster data tables owned by the current user, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.                                                              |
    | `void`                                 | `setClientID``(long client_id)`<br>Sets the client ID for a session.                                                                                                                                                                                                                                                     |
    | `void`                                 | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                                                                                                                                                                                  |
    | `void`                                 | `setMaxMemSize``(java.lang.Long maxMemSize)`<br>Sets the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.                                                                                                                                                          |
    | `void`                                 | `setReadBlockMemSize``(java.lang.Long memBlockSize)`<br>Sets the size of the GeoRaster internal data block for read-only operations.                                                                                                                                                                                     |
    | `void`                                 | `setSeqID``(long seq_id)`<br>Sets the sequence ID for a session.                                                                                                                                                                                                                                                         |
    | `void`                                 | `setWriteBlockMemSize``(java.lang.Long memBlockSize)`<br>Sets the size of the GeoRaster internal data block for read/write operations.                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoGeorUtlPKG

          public SdoGeorUtlPKG(java.sql.Connection conn)

      Constructs an `SdoGeorUtlPKG` object using the given connection.
      Parameters:
      `conn` - a JDBC connection.

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public void setConnection(java.sql.Connection conn)

      Sets the connection which points to the target database.
      Parameters:
      `conn` - a JDBC connection

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns a connection which points to target database.
      Returns:
      a connection which points to target database.

    <!-- -->

    - #### calcOptimizedBlockSize

          public java.math.BigDecimal[] calcOptimizedBlockSize(long[] dimensionSize,
                                                               long[] blockSize,
                                                               long pyramidLevel)
                                                        throws java.lang.Exception

      Calculates an optimal blockSize value that will use less padding space in the GeoRaster object storage, based on the GeoRaster dimension sizes and the user-specified block size values.
      Parameters:
      `dimensionSize` - Dimension size array of the GeoRaster object.

      `blockSize` - Block size array, which holds the user-specified block size values

      `pyramidLevel` - Maximum pyramid level.

      Returns:
      Outputs the adjusted optimal block size values.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### calcRasterNominalSize

          public double calcRasterNominalSize(SdoGeoRaster georaster,
                                              boolean padding,
                                              boolean pyramid,
                                              boolean bitmapMask)
                                       throws java.lang.Exception

      Returns the total raster block length (in bytes) of a GeoRaster object, as if it were not compressed and did not contain any empty raster blocks.
      Parameters:
      `georaster` - georaster object.

      `padding` - The TRUE causes padding in the raster blocks to be considered; the FALSE causes padding in the raster blocks not to be considered.

      `pyramid` - The TRUE causes the size of any pyramids to be considered; the FALSE causes the size of any pyramids not to be considered.

      `bitmapMask` - The TRUE (the default) causes any associated bitmap masks to be considered; the FALSE causes any associated bitmap masks not to be considered.

      Returns:
      total raster block length (in bytes).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### calcRasterStorageSize

          public double calcRasterStorageSize(SdoGeoRaster georaster)
                                       throws java.lang.Exception

      Returns the actual length (in bytes) of all raster blocks of a GeoRaster object.
      Parameters:
      `georaster` - georaster object.

      Returns:
      the actual length (in bytes) of all raster blocks of a GeoRaster object.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createDMLTrigger

          public void createDMLTrigger(java.lang.String tableName,
                                       java.lang.String columnName)
                                throws java.lang.Exception

      Creates the required standard GeoRaster data manipulation language (DML) trigger on a GeoRaster column in a GeoRaster table, so that the appropriate operations are performed when its associated trigger is fired.
      Parameters:
      `tableName` - Name of a GeoRaster table (the table containing rows with at least one GeoRaster object column).

      `columnName` - Name of a column of type SDO_GEORASTER in the GeoRaster table.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### fillEmptyBlocks

          public void fillEmptyBlocks(SdoGeoRaster georaster,
                                      double[] bgValues)
                               throws java.lang.Exception

      Fills in all empty blocks with specified background values.
      Parameters:
      `georaster` - georaster object.

      `bgValues` - background values for filling partially empty raster blocks.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### makeRDTNamesUnique

          public void makeRDTNamesUnique()
                                  throws java.lang.Exception

      Renames some existing registered raster data tables that do not have unique names so that all raster data table names are unique within the database, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### renameRDT

          public void renameRDT(java.lang.String oldRDT,
                                java.lang.String newRDT)
                         throws java.lang.Exception

      Renames one or more existing registered raster data tables owned by the current user, and updates the GeoRaster system data and all affected GeoRaster objects to reflect the new names.
      Parameters:
      `oldRDT` - Name of the registered raster data table or tables to be renamed. For multiple tables, use a comma-delimited list.

      `newRDT` - New names to be assigned to the raster data table or tables that are specified in oldRDTs. For multiple tables, use a comma-delimited list with an order exactly reflecting the names in oldRDTs. If this parameter is null, GeoRaster assigns a unique new name to each input raster data table.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### emptyBlocks

          public void emptyBlocks(SdoGeoRaster georaster,
                                  double[] bgValues)
                           throws java.lang.Exception

      Trims all blocks that contain only the specified background values to empty LOBs, thus making them empty blocks. Can be used to reduce disk space required for GeoRaster storage.
      Parameters:
      `georaster` - georaster object.

      `bgValues` - Background values for determining if a block can be made an empty raster block. The number of ARRAY object must be either one (same filling value used for all layers) or the layer dimension size (a different filling value for each layer, respectively).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### recreateDMLTriggers

          public void recreateDMLTriggers()
                                   throws java.lang.Exception

      Re-creates the required standard GeoRaster data manipulation language (DML) triggers on all GeoRaster columns that the current user has privileges to access, so that the appropriate operations are performed when the triggers are fired.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### enableReport

          public void enableReport()
                            throws java.lang.Exception

      Enables status reporting on GeoRaster operations in the current session.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### clearReportTable

          public void clearReportTable(java.lang.Long client_id)
                                throws java.lang.Exception

      Deletes records in the table that contains GeoRaster operation status information.
      Parameters:
      `client_id` - ID of the client whose records are to be deleted. If this parameter is not specified, all records in the table are deleted.(The client ID can be set by using the SDO_GEOR_UTL.setClientID procedure.)

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createReportTable

          public void createReportTable()
                                 throws java.lang.Exception

      Creates the table to contain GeoRaster operation status information.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### disableReport

          public void disableReport()
                             throws java.lang.Exception

      Disables status reporting on GeoRaster operations in the current session.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### dropReportTable

          public void dropReportTable()
                               throws java.lang.Exception

      Drops the table that contains GeoRaster operation status information.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getAllStatusReport

          public java.lang.String getAllStatusReport()
                                              throws java.lang.Exception

      Returns the current status for all operations for all clients in the status table.
      Returns:
      the current status for all operations for all clients in the status table.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getProgress

          public double getProgress(long client_id,
                                    long seq_id)
                             throws java.lang.Exception

      Returns the progress of the operation for a specified client (session) and optionally for a specified operation. The returned value is the percentage of completion as a floating point number between 0 and 1.
      Parameters:
      `client_id` - Unique numeric value identifying the session.

      `seq_id` - Unique numeric value (within the specified session) identifying the operation for which to return status information.

      Returns:
      the progress of the operation

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getStatusReport

          public java.lang.String getStatusReport(long client_id,
                                                  long seq_id)
                                           throws java.lang.Exception

      Returns the current status of the operations in the status table for a specified client (session) and optionally for a specified operation.
      Parameters:
      `client_id` - Unique numeric value identifying the session.

      `seq_id` - Unique numeric value (within the specified session) identifying the operation for which to return status information.

      Returns:
      the current status of the operations in the status table for a specified client

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isReporting

          public int isReporting()
                          throws java.lang.Exception

      Checks if any session has status reporting enabled.
      Returns:
      1 if one or more sessions have status reporting enabled; it returns 0 if no sessions have status reporting enabled.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setClientID

          public void setClientID(long client_id)
                           throws java.lang.Exception

      Sets the client ID for a session.
      Parameters:
      `client_id` - Unique ID value to identify the session.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setSeqID

          public void setSeqID(long seq_id)
                        throws java.lang.Exception

      Sets the sequence ID for a session.
      Parameters:
      `seq_id` - Unique ID value to identify the operation in a session.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### calcSurfaceArea

          public double calcSurfaceArea(SdoGeoRaster geoRaster,
                                        JGeometry window,
                                        int parallel)
                                 throws java.lang.Exception

      Calculates the three dimensional (3D) surface area represented by digital elevation model (DEM) data that is stored in a GeoRaster object.
      Parameters:
      `georaster` - GeoRaster object in which DEM data is stored.

      `window` - The 2D geometry object specifying the area of which the 3D surface area is to be calculated.

      `parallel` - Degree of parallelism for the operation. It should be more than 0. The recommended value is 2 times the number of CPUs

      Returns:
      the three dimensional (3D) surface area

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateColorRamp

          public GeorColormap generateColorRamp(GeorColormap colorSeeds,
                                                java.math.BigDecimal[] rampSteps,
                                                java.lang.String cellValueType,
                                                java.lang.String interpoParam)
                                         throws java.lang.Exception

      Generates an SDO_GEOR_COLORMAP object with a color ramp (gradient) by interpolating the red, green, blue, and alpha values entered as seed.
      Parameters:
      `colorSeeds` - An SDO_GEOR_COLORMAP object with the seed values to be used as the beginning and end values for the interpolation. Should contain at least two groups, each containing a pixel value and set of RGBA values. (RGBA = red, green, blue, alpha)

      `rampSteps` - An array where each item indicates how many interpolated values will be generated for each section of the color ramp. Should contain at least one integer value indicating how many values will be generated for each section.

      `cellValueType` - A string indicating whether the cell values should be creates as integer or real values. The possible values for this parameter are integer (the default) or real.

      `interpoParam` - A string specifying the interpolation method. The possible values are method=linear (the default) and method=cosine.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setMaxMemSize

          public void setMaxMemSize(java.lang.Long maxMemSize)
                             throws java.lang.Exception

      Sets the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.
      Parameters:
      `maxMemSize` - Number of bytes that can be used for managing memory using the GeoRaster buffer system. The default value is 16777216 (16 MB).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMaxMemSize

          public long getMaxMemSize()
                             throws java.lang.Exception

      Returns the upper limit size of the memory that can be used for managing memory using the GeoRaster buffer system.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setReadBlockMemSize

          public void setReadBlockMemSize(java.lang.Long memBlockSize)
                                   throws java.lang.Exception

      Sets the size of the GeoRaster internal data block for read-only operations.
      Parameters:
      `memBlockSize` - Number of bytes that can be used for the GeoRaster internal data block for read-only operations. The default value is 32768 (32k).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setWriteBlockMemSize

          public void setWriteBlockMemSize(java.lang.Long memBlockSize)
                                    throws java.lang.Exception

      Sets the size of the GeoRaster internal data block for read/write operations.
      Parameters:
      `memBlockSize` - Number of bytes that can be used for the GeoRaster internal data block for read/write operations. The default value is 65536 (64 K).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getReadBlockMemSize

          public long getReadBlockMemSize()
                                   throws java.lang.Exception

      Returns the size in bytes of the GeoRaster internal data block for read-only operations.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getWriteBlockMemSize

          public long getWriteBlockMemSize()
                                    throws java.lang.Exception

      Returns the size in bytes of the GeoRaster internal data block for read/write operations.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### generateGrayRamp

          public GeorGrayscale generateGrayRamp(GeorGrayscale grayScale,
                                                java.math.BigDecimal[] rampSteps,
                                                java.lang.String cellValueType,
                                                java.lang.String interpoParam)
                                         throws java.lang.Exception

      Generates an SDO_GEOR_GRAYSCALE object with a grayscale ramp (gradient) by interpolating the values entered as seed.
      Parameters:
      `grayScale` - An SDO_GEOR_GRAYSCALE object with the seed values to be used as the beginning and end values for the interpolation. Should should contain at least one pixel-value/gray-value pair.

      `rampSteps` - An array where each item indicates how many interpolated values will be generated for each section of the gray ramp. Should contain at least one integer value indicating how many values will be generated for each section of the gray ramp.

      `cellValueType` - A string indicating whether the cell values should be creates as integer or real values. The possible values for this parameter are integer (the default) or real.

      `interpoParam` - A string specifying the interpolation method. The possible values are method=linear (the default) and method=cosine.

      Throws:
      `java.lang.Exception`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SdoGeorRaPKG.md)
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
