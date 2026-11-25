## 4 GeoRaster Data Query and Manipulation

This chapter describes how to perform several important GeoRaster data query and manipulation operations. Typical GeoRaster data query and manipulation involve most or all of the operations described.

See also the operations in [GeoRaster Database Creation and Management](georaster-database-creation-management.md).

Other chapters in this book cover advanced topics ([Raster Algebra and Analytics](raster-algebra-and-analytics.md) and [Image Processing and Virtual Mosaic](image-processing-virtual-mosaic.md)), and provide detailed reference information about GeoRaster PL/SQL packages ( [SDO_GEOR Package Reference](SDO_GEOR-reference.md), [SDO_GEOR_ADMIN Package Reference](SDO_GEOR_ADMIN-reference.md), [SDO_GEOR_AGGR Package Reference](SDO_GEOR_AGGR-referencer-ref.md), [SDO_GEOR_RA Package Reference](sdo-geor-ra-ref.md), and [SDO_GEOR_UTL Package Reference](SDO_GEOR_UTL-reference.md)).

- Querying and Searching GeoRaster Objects
- Changing and Optimizing Raster Storage
- Copying GeoRaster Objects
- Subsetting GeoRaster Objects with Polygon Clipping
- Querying and Updating GeoRaster Metadata
- Querying and Updating GeoRaster Cell Data
- Interpolating Cell Values
- Processing and Analyzing GeoRaster Objects
- Monitoring and Reporting GeoRaster Operation Progress
- Compressing and Decompressing GeoRaster Objects
- Deleting GeoRaster Objects, and Performing Actions on GeoRaster Tables and RDTs
- Performing Cross-Schema Operations
- Managing Memory to Improve Performance
- Updating GeoRaster Objects Before Committing
- Updating GeoRaster Objects in a Loop
- Using Template-Related Subprograms to Develop GeoRaster Applications

### 4.1 Querying and Searching GeoRaster Objects

GeoRaster tables are regular relational tables that can have various columns, such as an ID number, a name, a timestamp, and a unique description in the form of a string. These columns can be indexed, and GeoRaster objects can be queried using the standard database indexing and query statements, as shown in many examples in this manual.

After the GeoRaster tables are spatially indexed (see [Indexing GeoRaster Objects](georaster-database-creation-management.md)), you can quickly query or search GeoRaster objects using a geometry as well. For example, you may want to find all images (maybe hundreds or more) inside a specific region and then generate full pyramids for each image, as in the following example.

Example 4-1 Searching GeoRaster Objects and Generating Pyramids for Them

    DECLARE
      type curtype is ref cursor;
      my_cursor curtype;
      stmt varchar2(1000);
      tid     number;
      gr    sdo_georaster;
      gm  sdo_geometry;
    BEGIN
      -- 1. Define the query area in EPSG 4326 (WGS84) coordinate system
      gm := sdo_geometry(2003, 4326, null,
                  sdo_elem_info_array(1,1003,3),
                  sdo_ordinate_array(5,6,30,30));

      -- 2. Define the query statement on the GeoRaster table (city_images)using the given geometry
      stmt := 'select id from city_images t ' ||
        'where sdo_inside(t.image.spatialextent, :1)=''TRUE''';

      -- 3. Spatially query all images INSIDE the query area
      --    and generate full pyramids for each of the images
      open my_cursor for stmt using gm;
      loop
        fetch my_cursor into tid;
        exit when my_cursor%NOTFOUND;
        -- retrieve the image to generate the pyramids
        select image into gr from city_images where id = tid for update;
        sdo_geor.generatePyramid(gr, 'resampling=bilinear', null, ‘parallel=4’);
        update city_images set image=gr
           where id = tid;
        commit;
      end loop;
      close my_cursor;
    END;

You can also wrap up such blocks into a PL/SQL procedure and store it in the database, then call the stored procedure directly. These features enable you to organize complex processes and automate database administration tasks.

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.2 Changing and Optimizing Raster Storage

You can change or specify some aspects of the way raster image data is or will be stored: the raster blocking size, cell depth, interleaving type, and other aspects. Such flexibility allows you to optimize the raster data storage format to save disk space and improve application performance.

To load and process a GeoRaster object to create another GeoRaster object, you can specify storage parameters with GeoRaster PL/SQL subprograms. That is, you can specify the output format when you call functions or procedures such as [SDO_GEOR.importFrom](SDO_GEOR-reference.md), [SDO_GEOR.subset](SDO_GEOR-reference.md), [SDO_GEOR.rectify](SDO_GEOR-reference.md), [SDO_GEOR_AGGR.append](SDO_GEOR_AGGR-referencer-ref.md), [SDO_GEOR.mergeLayers](SDO_GEOR-reference.md), [SDO_GEOR.createTemplate](SDO_GEOR-reference.md), [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md), and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md). You cannot directly make such changes on an existing GeoRaster object; however, you can use the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md)procedure, and specify the desired storage parameter values with the `storageParam` parameter, to make a copy of the existing GeoRaster object.

The `storageParam` parameter for the resulting GeoRaster objects should be based on factors such as the data size, dimension sizes, and application needs, as you determine them. However, the block sizes can also be optimized automatically based on the dimension sizes of the GeoRaster object and the desired output required by users, so that each GeoRaster object uses only minimum padding space but still meets the application requirements. Depending on the raster dimension size and your desired blocking size, padding might waste some storage space, so you should always consider specifying `blocking=OPTIMALPADDING` in the `storageParam` parameter for the output GeoRaster when a GeoRaster procedure is called.

For more information, see [Storage Parameters](georaster-overview-and-concepts.md), especially [Table 1-1](georaster-overview-and-concepts.md). For examples of applying optimal padding, see the PL/SQL example at the end of [Storage Parameters](georaster-overview-and-concepts.md) and the GDAL example in [Loading with Blocking and Optimal Padding](georaster-database-creation-management.md)

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.3 Copying GeoRaster Objects

To copy a GeoRaster object, you must either copy it into an empty GeoRaster object or overwrite an existing valid GeoRaster object. (Empty GeoRaster objects are explained in [Blank and Empty GeoRaster Objects](georaster-overview-and-concepts.md).) To make an identical copy of the source GeoRaster object, use the [SDO_GEOR.copy](SDO_GEOR-reference.md) procedure; to make a copy that includes storage format changes, use the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure (see Changing and Optimizing Raster Storage).

To copy a GeoRaster object using an empty GeoRaster object, follow these steps:

1.  Initialize an empty GeoRaster object while inserting it into the destination table, returning the empty GeoRaster object.

2.  Use the [SDO_GEOR.copy](SDO_GEOR-reference.md) or [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure to copy the GeoRaster object into the returned empty GeoRaster object.

3.  Use UPDATE statement to update the desired row in the destination table so that its GeoRaster column contains the copied GeoRaster object.

4.  When you are ready to commit the transaction, use the COMMIT statement.

For an example of copying using an empty GeoRaster object, see the example for the [SDO_GEOR.copy](SDO_GEOR-reference.md) procedure in [SDO_GEOR Package Reference](SDO_GEOR-reference.md).

To copy a GeoRaster object so that it overwrites (replaces) an existing GeoRaster object, follow these steps:

1.  Select the existing GeoRaster object for update.
2.  Use the [SDO_GEOR.copy](SDO_GEOR-reference.md) or [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure to copy the selected GeoRaster object into either a valid existing GeoRaster object or an empty GeoRaster object.
3.  Use UPDATE statement to update the desired row in the destination table so that its GeoRaster column contains the copied GeoRaster object.
4.  When you are ready to commit the transaction, use the COMMIT statement.

For an example of copying to replace an existing GeoRaster object and to change its storage format, see the example for the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure in [SDO_GEOR Package Reference](SDO_GEOR-reference.md).

Parallel copying and subsetting are supported with the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure. For parallelized copying and change format copying, See [Example 6-24](image-processing-virtual-mosaic.md) in [Parallel Compression, Copying, and Subsetting](image-processing-virtual-mosaic.md).

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.4 Subsetting GeoRaster Objects with Polygon Clipping

With GeoRaster, subsetting means cropping rasters spatially, extracting or duplicating raster layers, or doing both together. To perform subsetting, use the [SDO_GEOR.subset](SDO_GEOR-reference.md) procedure. For example, you can call this procedure to crop a small area or obtain a subset of a few layers of a GeoRaster object, to duplicate layers, to specify storage parameters such as blocking and interleaving for the resulting object, and to perform polygon clipping.

For examples, see the [SDO_GEOR.subset](SDO_GEOR-reference.md) reference topic.

You can also use the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure to perform subsetting with parallelism (see [Parallel Compression, Copying, and Subsetting](image-processing-virtual-mosaic.md)).

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.5 Querying and Updating GeoRaster Metadata

You can query metadata for a GeoRaster object, and you can update many attributes of the metadata.

You can use many functions, most of whose names start with get, to query the metadata and ancillary information (for example, [SDO_GEOR.getTotalLayerNumber](SDO_GEOR-reference.md) and [SDO_GEOR.hasPseudoColor](SDO_GEOR-reference.md)).

You can use several subprograms, most of whose names start with set, to update metadata and ancillary data (for example, [SDO_GEOR.setSRS](SDO_GEOR-reference.md) and [SDO_GEOR.setColorMap](SDO_GEOR-reference.md)).

For many of the get functions, there is a corresponding procedure, whose name starts with set, to set, modify, or delete the value of a metadata attribute. For most set procedures, to delete the value of the metadata attribute that the procedure is designed to modify, specify a null value for the attribute. For example, to delete the bin table for a layer of a GeoRaster object, call the [SDO_GEOR.setBinTable](SDO_GEOR-reference.md) procedure and specify a null `tableName` parameter. However, in most cases you cannot specify a null value for other related attributes. For example, you cannot specify a null `layerNumber` parameter in a call to the [SDO_GEOR.setBinTable](SDO_GEOR-reference.md) procedure.

Note the following recommendations, requirements, and restrictions:

- Most GeoRaster metadata can also be retrieved using XMLType methods or XML-specific SQL functions, such as `extract`, and be modified using XQuery Update. However, if a GeoRaster get or set subprogram exists for the metadata attribute you want to retrieve or change, use the GeoRaster subprogram instead of an XMLType interface, because the GeoRaster subprograms validate any changes before they are made. If you do call XMLType methods or XML-specific SQL functions to update metadata, you should validate the GeoRaster object before you commit the transaction.

- Never directly set the metadata to be null.

- Do not directly update the rasterType attribute of a GeoRaster object; instead, call the [SDO_GEOR.setRasterType](SDO_GEOR-reference.md) procedure.

- To change the raster data table name, use the [SDO_GEOR_UTL.renameRDT](SDO_GEOR_UTL-reference.md) procedure.

- In general, you should not directly update the attributes of a GeoRaster object, except for the `spatialExtent` attribute.

- After updating a GeoRaster object's metadata or cell data (or both) and before you commit a database transaction, you should call the SQL UPDATE statement to update the GeoRaster object (see Updating GeoRaster Objects Before Committing).

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.6 Querying and Updating GeoRaster Cell Data

To query cell (pixel) data of a GeoRaster object for processing and visualization, you can query the raster data for a cell (pixel), a range of cells, or the entire raster of a GeoRaster object:

- [SDO_GEOR.getCellValue](SDO_GEOR-reference.md) returns cell values of one or multiple layers or bands for a specified location.

- [SDO_GEOR.getCellValues](SDO_GEOR-reference.md) returns the cell values of one or more cells in an array.

- [SDO_GEOR.evaluateDouble](SDO_GEOR-reference.md) evaluates a direct location based on neighboring cell values by using a specified interpolation method, and returns the raster values (double precision numbers) for the specified bands or layers for that location. (See Interpolating Cell Values for more information.)

- [SDO_GEOR.evaluateDoubles](SDO_GEOR-reference.md) evaluates multiple locations using a specified interpolation method, and returns the raster values (double precision numbers) for the specified band or layer for those locations.

- [SDO_GEOR.getRasterSubset](SDO_GEOR-reference.md) creates a single BLOB object or a single in-memory SDO_NUMBER_ARRAY object containing all cells of a precise subset of the GeoRaster object (as specified by a rectangular window or a clipping polygon geometry, layer or band numbers, and pyramid level). This BLOB object or SDO_NUMBER_ARRAY object contains only raster cells and no related metadata.

- [SDO_GEOR.getRasterData](SDO_GEOR-reference.md) creates a single BLOB object containing all cells of the GeoRaster object at a specified pyramid level. This BLOB object contains only raster cells and no related metadata.

- [SDO_GEOR.getRasterBlocks](SDO_GEOR-reference.md) returns an object that includes all image data inside or touching a specified window. Specifically, it returns an object of the SDO_RASTERSET collection type that identifies all blocks of a specified pyramid level that are inside or touch a specified window.

- [SDO_GEOR.reproject](SDO_GEOR-reference.md) not only transforms a whole GeoRaster object from one projected coordinate system to another, but can also include the same capability as [SDO_GEOR.getRasterSubset](SDO_GEOR-reference.md) by directly transforming the query result into a different coordinate system on-the-fly.

- [SDO_GEOR.rectify](SDO_GEOR-reference.md) performs reprojection, rectification, or orthorectification on all or part of a georeferenced GeoRaster object based on a query window. The resulting object can be a new GeoRaster object (for persistent storage) or a BLOB (for temporary use).

- [SDO_GEOR_RA.findCells](sdo-geor-ra-ref.md) generates a new GeoRaster object based on the cell values using the GeoRaster Raster Algebra language. (See [Cell Value-Based Conditional Queries](raster-algebra-and-analytics.md) for more information.)

- [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) mosaics a number of GeoRaster objects into one GeoRaster object.

- [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) lets you query a virtual mosaic and returns a mosaicked subset on-the-fly.

- [SDO_GEOR.getBitmapMask](SDO_GEOR-reference.md), [SDO_GEOR.getBitmapMaskSubset](SDO_GEOR-reference.md), [SDO_GEOR.getBitmapMaskValue](SDO_GEOR-reference.md), and [SDO_GEOR.getBitmapMaskValues](SDO_GEOR-reference.md) let you query bitmap masks on the basis of a full raster, a window, or single cells.

You can also use the [SDO_GEOR.exportTo](SDO_GEOR-reference.md) procedure to export all or part of a raster image to a BLOB object (binary image format) or to a file of a specified file format type.

There are two types of raster updates: space-based and cell value-based

- Space-based raster update allows you update a GeoRaster object's raster data inside a specified window entirely using either a single value or another GeoRaster object.

  To update or change the value of raster cells in a specified window to a single value, you can use the [SDO_GEOR.changeCellValue](SDO_GEOR-reference.md) procedure. To change the value of raster cells specified by row/column arrays or by a multipoint geometry to new values, you can use the [SDO_GEOR.changeCellValues](SDO_GEOR-reference.md)procedure. You can call the [SDO_GEOR.updateRaster](SDO_GEOR-reference.md) procedure to update a specified pyramid of a specified area, or the overlapping parts of one GeoRaster object, with a specified pyramid and specified bands or layers of another GeoRaster object. Both the [SDO_GEOR.changeCellValue](SDO_GEOR-reference.md) and the [SDO_GEOR.updateRaster](SDO_GEOR-reference.md) procedures support all pyramid levels, including the original raster data (that is, pyramid level 0).

  The [SDO_GEOR_AGGR.append](SDO_GEOR_AGGR-referencer-ref.md) procedure can also be used to update an existing image with a new image (see [Image Appending](image-processing-virtual-mosaic.md)).

- Cell value-based raster update allows you update a GeoRaster object's raster data based on the cell values using the GeoRaster Raster Algebra language.

  [SDO_GEOR_RA.rasterUpdate](sdo-geor-ra-ref.md) selects cells from the specified GeoRaster object based on Boolean strings specified in the `conditions` parameter, and updates corresponding cell values by calculating expression strings specified in the `vals` parameter. Both the `conditions` and `vals` parameters can be complicated expressions using the raster algebra language. (See [Cell Value-Based Conditional Updates (Edits)](raster-algebra-and-analytics.md) for more information.)

If statistics are already set in the GeoRaster object when you perform space-based or raster cell value-based updates, the statistics are not removed or updated automatically after you run the raster update procedures. If necessary, you should remove or regenerate the statistics.

**Note:**

If you use any procedure that adds or overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use the procedure on the copied object. After you are satisfied with the result of the procedure, you can discard the original GeoRaster object if you wish.

If you want to change the raster data table name, the attributes of a GeoRaster object, or any other metadata, see the recommendations, requirements, and restrictions noted in Querying and Updating GeoRaster Metadata.

After updating a GeoRaster object's metadata or cell data (or both) and before you commit a database transaction, you should call the SQL UPDATE statement to update the GeoRaster object (see Updating GeoRaster Objects Before Committing).

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.7 Interpolating Cell Values

GeoRaster objects are grid coverages. The "evaluate" operation of a grid coverage is also called grid interpolation, a method for interpolating cell values at point positions between the cells or within the cells. This operation in GeoRaster is performed by the [SDO_GEOR.evaluateDouble](SDO_GEOR-reference.md) function, which evaluates any point in the raster and returns a double number value for that location. You can use any one of the six different interpolation methods (listed in [Resampling and Interpolation](georaster-overview-and-concepts.md)) to do the evaluation. For example, if a georaster object is a DEM layer, you can find out the elevation of a random point location, using the following example:

    SELECT SDO_GEOR.evaluateDouble(a.georaster, 0,
        SDO_GEOMETRY(2001, 4326, SDO_POINT_TYPE(112.704, 41.917, NULL),
                     NULL, NULL),
        '1',
        'interpolationMethod=BILINEAR')
      FROM georaster_table a WHERE raster_name='myDEM';

If you call [SDO_GEOR.evaluateDouble](SDO_GEOR-reference.md) with `'interpolationMethod=NN'`, the GeoRaster object is treated as a discrete raster and the preceding is the same as calling [SDO_GEOR.getCellValue](SDO_GEOR-reference.md), which gives you the same value (that is, the cell value) at a different point location inside a cell. In this case, you can directly call [SDO_GEOR.getCellValue](SDO_GEOR-reference.md) instead, particularly when you query only the cell values of a single band. Other interpolation methods treat the raster as a continuous surface and may give you different values at different point locations inside a cell.

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.8 Processing and Analyzing GeoRaster Objects

You can perform a variety of raster and image processing operations on GeoRaster data, including changing the internal raster storage format, subsetting (cropping), scaling, rotating, masking, stretching, filtering, dodging, reprojecting (from one coordinate system to another), rectifying, orthorectifying, warping, mosaicking, appending, and generating pyramids. GeoRaster also supports virtual mosaic. Some relevant subprograms are [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md), [SDO_GEOR.subset](SDO_GEOR-reference.md), [SDO_GEOR.reproject](SDO_GEOR-reference.md), [SDO_GEOR.rectify](SDO_GEOR-reference.md), [SDO_GEOR.generatePyramid](SDO_GEOR-reference.md), [SDO_GEOR.deletePyramid](SDO_GEOR-reference.md), [SDO_GEOR.scaleCopy](SDO_GEOR-reference.md), [SDO_GEOR.mergeLayers](SDO_GEOR-reference.md), [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md), [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md), and [SDO_GEOR_AGGR.append](SDO_GEOR_AGGR-referencer-ref.md). For detailed descriptions, see [Image Processing and Virtual Mosaic](image-processing-virtual-mosaic.md), [SDO_GEOR Package Reference](SDO_GEOR-reference.md), and [SDO_GEOR_AGGR Package Reference](SDO_GEOR_AGGR-referencer-ref.md).

For raster cell value-based algebraic operations and cartographic modeling and analysis, GeoRaster supports a raster algebra language (PL/SQL and Algebraic Expressions) and related raster operations, including conditional queries ([SDO_GEOR_RA.findCells](sdo-geor-ra-ref.md)), cell value-based updates or edits ([SDO_GEOR_RA.rasterUpdate](sdo-geor-ra-ref.md)), logical and mathematical operations ([SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md)), and image and raster segmentation ([SDO_GEOR_RA.classify](sdo-geor-ra-ref.md)). The [SDO_GEOR.generateStatistics](SDO_GEOR-reference.md) function supports polygon-based statistics and histogram generation. The following on-the-fly functions support interactive statistical analysis of a GeoRaster object or its layers: [SDO_GEOR.generateStatisticsMax](SDO_GEOR-reference.md), [SDO_GEOR.generateStatisticsMean](SDO_GEOR-reference.md), [SDO_GEOR.generateStatisticsMedian](SDO_GEOR-reference.md), [SDO_GEOR.generateStatisticsMin](SDO_GEOR-reference.md), [SDO_GEOR.generateStatisticsMode](SDO_GEOR-reference.md), and [SDO_GEOR.generateStatisticsSTD](SDO_GEOR-reference.md). For detailed descriptions, see [Raster Algebra and Analytics](raster-algebra-and-analytics.md) and [SDO_GEOR_RA Package Reference](sdo-geor-ra-ref.md).

See also the GeoRaster PL/SQL demo files, described in [GeoRaster PL/SQL and Java Demo Files](georaster-overview-and-concepts.md), for examples and explanatory comments.

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.9 Monitoring and Reporting GeoRaster Operation Progress

GeoRaster lets you monitor and report the execution progress of many operations (listed in [Reporting Operation Progress in GeoRaster](georaster-overview-and-concepts.md)). The following are the basic steps for reporting the progress of an operation:

1.  Use the [SDO_GEOR_UTL.createReportTable](SDO_GEOR_UTL-reference.md) procedure to create the report table under the appropriate user's schema. (This must be called once before you can monitor any operations.)

        EXECUTE SDO_GEOR_UTL.createReportTable;

2.  In the user session where the operations are to be executed and monitored, perform the following actions:

    1.  Use [SDO_GEOR_UTL.enableReport](SDO_GEOR_UTL-reference.md) to enable the monitoring. (You must call this procedure in order to be able to get the status report later.)

            EXECUTE SDO_GEOR_UTL.enableReport;

    2.  Optionally, use [SDO_GEOR_UTL.setClientID](SDO_GEOR_UTL-reference.md) to set the client ID. The client ID is used to identify the user session that executes the operation. If this procedure is not called, the client ID defaults to the SQL session ID. For example:

            EXECUTE SDO_GEOR_UTL.setClientID(100);

    3.  Optionally, use [SDO_GEOR_UTL.setSeqID](SDO_GEOR_UTL-reference.md) to set the sequence ID. The sequence ID is used to identify the repeated operations in the same SQL session. If this procedure is not called, the sequence ID defaults to 0. For example:

            EXECUTE SDO_GEOR_UTL.setSeqID(1);

    4.  Execute the operation to be monitored. For example:

            -- Generate pyramid for georid=6. The progress of this generatePyramid call
            -- can be monitored by step 3.
            DECLARE
              gr sdo_georaster;
            BEGIN
               SELECT georaster INTO gr
                FROM georaster_table WHERE georid = 6 FOR UPDATE;
              sdo_geor.generatePyramid(gr, 'rLevel=5, resampling=NN');
              UPDATE georaster_table SET georaster = gr WHERE georid = 6;
               COMMIT;
            END;
            /

    5.  Optionally, repeat steps c and d for each additional operation to be monitored. For example:

            EXECUTE SDO_GEOR_UTL.setSeqID(2);
            -- Generate pyramid for georid=7. The progress of this generatePyramid call
            -- can be monitored by step 3.
            DECLARE
              gr sdo_georaster;
            BEGIN
               SELECT georaster INTO gr
                FROM georaster_table WHERE georid = 7 FOR UPDATE;
              sdo_geor.generatePyramid(gr, 'rLevel=5, resampling=NN');
              UPDATE georaster_table SET georaster = gr WHERE georid = 7;
               COMMIT;
            END;
            /

    6.  Optionally, use [SDO_GEOR_UTL.disableReport](SDO_GEOR_UTL-reference.md) to disable the monitoring. If this procedure is not called, the monitoring is automatically stopped when the user session ends.

            EXECUTE SDO_GEOR_UTL.disableReport;

3.  From another session under the same user, retrieve the execution status report.

    To get the progress of a specific operation identified by client ID and sequence ID, use the [SDO_GEOR_UTL.getProgress](SDO_GEOR_UTL-reference.md) function. This function returns the progress as a number between 0 and 1 reflecting the percentage of completion. For example, the following query shows that the operation if 55% complete:

        SELECT sdo_geor_utl.getProgress(100, 2) progress FROM DUAL;

        PROGRESS
        --------
            0.55

        1 row selected.

    To get the status report of a specific operation identified by client ID and sequence ID, use the [SDO_GEOR_UTL.getStatusReport](SDO_GEOR_UTL-reference.md) function. This function returns an array of strings describing the progress and other information about the operation. For example:

        -- Check the status of the generatePyramid on georid=6
        SELECT sdo_geor_utl.getStatusReport(100, 1) FROM DUAL;
        SDO_GEOR_UTL.GETSTATUSREPORT(100,1)
        -----------------------------------------------------------------------------
        SDO_STRING2_ARRAY('31-OCT-11 02.20.04.854558 PM', 'GeneratePyramid', 'RDT:RDT_1', 'RID:6', '100% complete', 'operation completed')

        1 row selected.

        -- Check the status of the generatePyramid on georid=7
        SELECT sdo_geor_utl.getStatusReport(100, 2) FROM DUAL;

        SDO_GEOR_UTL.GETSTATUSREPORT(100,2)
        -----------------------------------------------------------------------------
        SDO_STRING2_ARRAY('31-OCT-11 02.20.08.854558 PM', 'GeneratePyramid', 'RDT:RDT_1', 'RID:7', '55% complete', 'operation completed')

        1 row selected.

    To get the status of all the monitored operations, enter the following statement:

        SELECT * from the (select sdo_geor_utl.getAllStatusReport() FROM DUAL);
        COLUMN_VALUE
        ------------------------------------------------------------------------------
        SDO_STRING2_ARRAY('Client:100', 'Sequence:1', '31-OCT-11 02.20.04.854558 PM', 'GeneratePyramid', 'RDT:RDT_1', 'RID:6', '100% complete', 'operation completed')
        SDO_STRING2_ARRAY('Client:100', 'Sequence:2', '31-OCT-11 02.20.08.854558 PM', 'GeneratePyramid', 'RDT:RDT_1', 'RID:7', '55% complete', NULL)

        2 rows selected.

If you need to clear or drop the report table, use the [SDO_GEOR_UTL.clearReportTable](SDO_GEOR_UTL-reference.md) or [SDO_GEOR_UTL.dropReportTable](SDO_GEOR_UTL-reference.md) procedure, respectively:

    EXECUTE SDO_GEOR_UTL.clearReportTable;
    -- or:
    EXECUTE SDO_GEOR_UTL.dropReportTable;

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.10 Compressing and Decompressing GeoRaster Objects

You can reduce the storage space requirements for GeoRaster objects by compressing them using JPEG-F, DEFLATE, or JPEG 2000 compression. You can decompress any compressed GeoRaster object, although this is not required for any GeoRaster operations, because any GeoRaster operation that can be performed on an uncompressed (decompressed) GeoRaster object can be performed on a compressed GeoRaster object.

For JPEG-F and DEFLATE, to compress or decompress a GeoRaster object, use the `compression` keyword in the `storageParam` parameter with the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure, or with several other procedures that load and process a GeoRaster object to create another GeoRaster object, including [SDO_GEOR.importFrom](SDO_GEOR-reference.md), [SDO_GEOR.mosaic](SDO_GEOR-reference.md), [SDO_GEOR.scaleCopy](SDO_GEOR-reference.md), [SDO_GEOR.subset](SDO_GEOR-reference.md), raster algebra (SDO_GEOR_RA) procedures, and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md). (For JPEG-F and DEFLATE compression, there are no separate procedures for compressing and decompressing a GeoRaster object.)

For JPEG 2000, use the [SDO_GEOR.compressJP2](SDO_GEOR-reference.md) and [SDO_GEOR.decompressJP2](SDO_GEOR-reference.md) procedures to compress and decompress a GeoRastrer object, respectively. Most other procedures and functions (except for [SDO_GEOR.changeCellValue](SDO_GEOR-reference.md), [SDO_GEOR.reproject](SDO_GEOR-reference.md), [sdo_geor.scaleScopy](SDO_GEOR-reference.md), and [sdo_geor.mosaic](SDO_GEOR-reference.md)) can internally decompress the JP2 compressed GeoRaster object while performing the operation.

For more information about GeoRaster compression and decompression, see [Compression and Decompression](georaster-overview-and-concepts.md), including information about support for third-party compression solutions in [Third-Party Plug-ins for Compression](georaster-overview-and-concepts.md).

In addition, when JPEG-F or DEFLATE compression is used with GeoRaster objects, some special usage considerations apply:

- If a large GeoRaster object is to be compressed and will have full pyramids built on it, it is faster to generate pyramids on the uncompressed GeoRaster object first, then apply compression.

- For large scale mosaicking, it is faster to mosaic without applying compression first, then generate pyramids, then apply compression.

- In some operations, GeoRaster uses temporary tablespaces to compress and decompress data, so adding temporary tablespaces for GeoRaster users is essential for performance (see [Adding Temporary Tablespaces for GeoRaster Users](georaster-database-creation-management.md)).

Parallel compression and decompression for JPEG and DEFLATE are supported with the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure, if reformatting is not needed, by using the `parallel` keyword in the `storageParam` parameter. You can also call the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure, which provides better performance if you want to change the raster format while doing parallelized compression or decompression. Parallel compression and decompression significantly improve performance, which is especially useful for large images. See [Example 6-23](image-processing-virtual-mosaic.md) in [Parallel Compression, Copying, and Subsetting](image-processing-virtual-mosaic.md)

If you want to store compressed GeoRaster objects, make sure you create a temporary tablespace for the users. For more information, see [Adding Temporary Tablespaces for GeoRaster Users](georaster-database-creation-management.md).

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.11 Deleting GeoRaster Objects, and Performing Actions on GeoRaster Tables and RDTs

GeoRaster automatically maintains the GeoRaster metadata and the relationship between GeoRaster tables and raster data tables (RDTs). Therefore, for most operations you can use the relevant traditional SQL statement.

- To delete a GeoRaster object, delete the row containing the object using the DELETE statement (for example, `DELETE FROM geor_table WHERE ...;`).

  After a GeoRaster object is deleted from a GeoRaster table, all related raster data stored in the RDT is deleted automatically. Never insert or delete any rows directly in a raster data table.

- To drop a GeoRaster table, use the DROP statement (for example, `DROP geor_table;`).

  After a GeoRaster table is dropped, all raster data associated with GeoRaster objects in the deleted GeoRaster table is deleted automatically.

- To rename a GeoRaster table, use the RENAME statement (for example, `RENAME geor_table1 TO geor_table2;`).

- To add a GeoRaster column to a table, use the ALTER TABLE statement.

  However, if you use the ALTER TABLE statement to add one or more GeoRaster columns, you must call the [SDO_GEOR_UTL.createDMLTrigger](SDO_GEOR_UTL-reference.md) procedure to create the DML trigger on each added GeoRaster column. For example:

      ALTER TABLE geor_table ADD (image SDO_GEORASTER);
      CALL sdo_geor_utl.createdmltrigger('GEOR_TABLE','IMAGE');)

- To drop a GeoRaster column in a table, use the ALTER TABLE statement (for example, `ALTER TABLE geor_table DROP COLUMN image;`).

  Caution: Dropping a GeoRaster column will delete all GeoRaster objects in that column.

- To drop an RDT, you must first delete all GeoRaster objects that reference the RDT, after which you can use the DROP statement on the RDT.

  If you do not delete all GeoRaster objects that reference the RDT before attempting to drop the RDT, an exception is raised.

- To rename an RDT, use the [SDO_GEOR_UTL.renameRDT](SDO_GEOR_UTL-reference.md) procedure.

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.12 Performing Cross-Schema Operations

All GeoRaster operations can work on GeoRaster objects defined in schemas other than the current connection schema. In other words, GeoRaster fully supports cross-schema access, update, and processing.

For more information, see [Cross-Schema Support with GeoRaster](georaster-overview-and-concepts.md).

Example 4-2 Cross-Schema Copy Operation

In the following example, USER2 makes a copy of an image from USER1 and stores it in the USER2 schema. Assume that USER1 owns the GEORASTER_TABLE table and that USER2 owns the G_TABLE table.

    --connect to user1 and grant permissons to user2
    --assume user1 stores the image in georaster_table and the image’s RDT table is rdt_1
    conn user1/pswd1
     grant select on georaster_table to user2;
    grant select on rdt_1 to user2;

    --connect to user2 and make a copy of a georaster from user1
    conn user2/pswd2
    SQL> DECLARE
       gr1 sdo_georaster;
       gr2 sdo_georaster;
    BEGIN
       --select the image from georaster_table in user1
       select georaster into gr1 from user1.georaster_table where georid = 100;
       -- the copy is to be stored in g_table in user2, assuming the georaster object is already initiated
       select geor into gr2 from g_table where id = 1 for update;
       sdo_geor.changeFormatCopy(gr1, 'blocking=OPTIMALPADDING blocksize=(512,512,3) interleaving=BIP', gr2);
       update g_table set geor=gr2 where id=1;
       commit;
    END;
    /

Example 4-3 Cross-Schema Raster Algebra and Copy Operation

In the following example, USER2 runs a raster algebra operation on an image in the USER1 schema and stores the result in USER1. Assume that USER1 owns both the GEORASTER_TABLE and G_TABLE tables. The existing image is in GEORASTER_TABLE and the image’s raster data table is RDT_1. The resulting image is stored in G_TABLE and its raster data table is RDT_2.

    --connect to user1 and grant permissons to user2
    conn user1/pswd1
    grant select on georaster_table to user2;
    grant select on rdt_1 to user2;
    grant select, update, insert, delete on g_table to user2;
    grant select, update, insert, delete on rdt_2 to user2;

    --connect to user2 and run a raster algebra operation on an image in user1
    conn user2/pswd2
    DECLARE
       gr1 sdo_georaster;
       gr2 sdo_georaster;
    BEGIN
       --select the image from georaster_table in user1
       select georaster into gr1 from user1.georaster_table where georid = 100;
       -- the result is to be stored in g_table in user1, assuming the georaster object is already initiated
       select geor into gr2 from user1.g_table where id = 1 for update;
       sdo_geor_ra.rasterMathOp(gr1,sdo_string2_array('{0}','{1}','{2}'), 'blocking=OPTIMALPADDING blocksize=(512,512,3) interleaving=BIP',gr2);
       update user1.g_table set geor=gr2 where id=1;
       commit;
    END;
    /

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.13 Managing Memory to Improve Performance

GeoRaster has its own buffer system to read and write raster (LOB) data. This system is separate from the Oracle Database buffer system. The following table lists parameters that can be used to configure the GeoRaster buffer system, which is used for all I/O operations on GeoRaster objects.

Table 4-1 GeoRaster Buffering Parameters

| Parameter Name    | Description                                                                                        | Default Value |
|:------------------|:---------------------------------------------------------------------------------------------------|:--------------|
| MemMaxSize        | Upper limit size of the memory that can be used for GeoRaster buffering for each GeoRaster object. | 17 MB         |
| MemReadBlockSize  | Internal data block size for read-only operations for caching raster data.                         | 32 KB         |
| MemWriteBlockSize | Internal data block size for read/write operations for caching raster data.                        | 64 KB         |

You can get and set the values of these parameters using the following PL/SQL subprograms:

- [SDO_GEOR_UTL.getMaxMemSize](SDO_GEOR_UTL-reference.md)

- [SDO_GEOR_UTL.setMaxMemSize](SDO_GEOR_UTL-reference.md)

- [SDO_GEOR_UTL.getReadBlockMemSize](SDO_GEOR_UTL-reference.md)

- [SDO_GEOR_UTL.setReadBlockMemSize](SDO_GEOR_UTL-reference.md)

- [SDO_GEOR_UTL.getWriteBlockMemSize](SDO_GEOR_UTL-reference.md)

- [SDO_GEOR_UTL.setWriteBlockMemSize](SDO_GEOR_UTL-reference.md)

Because the parameters are set using PL/SQL, their values are defined for the duration of the database session. For any subsequent sessions, if you want to use any nondefault values for any of the parameters, you must set them using the appropriate procedures.

In general, using large values for the parameters improves performance for GeoRaster I/O operations. The following are some specific considerations and guidelines.

- Allocating more memory (increasing `MemMaxSize`) reduces disk access; and ideally, allocating big enough memory to hold an entire GeoRaster object will dramatically improve performance. However, Oracle Database allows multiple users and concurrent access, and so you should aim for balanced memory allocation in such an environment.

- Increasing the read block size (increasing `MemReadBlockSize`) reduces the number of OCI LOB read operations, thus improving performance. However, due to different interleaving between source and target GeoRaster objects in an operation, if the `MemReadBlockSize` value cannot hold the entire GeoRaster object, the read block size might be too large and cause frequent read block page-in and page-out operations, thus degrading performance.

- Almost all GeoRaster operations are write-driven, so that a larger write block size (increasing `MemWriteBlockSize`) will reduce number of OCI LOB write operations and thus improve performance.

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.14 Updating GeoRaster Objects Before Committing

Before you commit a database transaction that inserts, updates, reformats, compresses, decompresses, or deletes GeoRaster cell data or metadata, you should use the SQL UPDATE statement to update the GeoRaster object. If you do not update the GeoRaster object after changing cell data, one or more of the following can result: an invalid GeoRaster object, dangling raster data, and inconsistent metadata. If you do not update the GeoRaster object after changing GeoRaster metadata, the metadata changes will not take effect.

If you decide to roll back the transaction instead of committing it, an UPDATE statement is not needed.

In Example 4-4, the UPDATE statement is required after the call to the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure and before the COMMIT statement.

Example 4-4 Updating a GeoRaster Object Before Committing

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

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.15 Updating GeoRaster Objects in a Loop

When multiple GeoRaster objects are to be updated, a cursor is generally used. However, if the GeoRaster operation in the loop is parallel enabled or the COMMIT statement is executed after each UPDATE statement, the SQL query for the cursor cannot have the FOR UPDATE clause because the commit within the loop will invalidate the cursor with that clause.

Example 4-5 Updating GeoRaster Objects in a Loop With Parallel Processing Enabled

In the following example, pyramids were generated on all the GeoRaster objects in the table. An explicit commit is executed after each update, and parallel processing is enabled (`parallel=4`) for the [SDO_GEOR.generatePyramid](SDO_GEOR-reference.md) procedure. The query of the GeoRaster object with FOR UPDATE clause is executed within the loop, not in the cursor query statement.

    DECLARE
        gr1 sdo_georaster;
    BEGIN
        FOR rec in (SELECT georid FROM georaster_table ORDER BY georid) LOOP
          SELECT georaster INTO gr1 FROM georaster_table WHERE georid=rec.georid FOR UPDATE;
          sdo_geor.generatePyramid(gr1, 'rlevel=5, resampling=bilinear', null, 'parallel=4');
          UPDATE georaster_table SET georaster=gr1 WHERE georid=rec.georid;
          COMMIT;
        END LOOP;
     END;
    /

Example 4-6 Updating GeoRaster Objects in a Loop Without Parallel Processing Enabled

If the GeoRaster operation in the loop is not parallel enabled (as is the case in this example), instead of executing a COMMIT after each update, the COMMIT statement can be executed outside the cursor loop, to avoid invalidating the cursor with FOR UPDATE clause. Also note that the example adds NODATA to all the GeoRaster objects in the table.

    BEGIN
    FOR rec in (SELECT georid, georaster FROM georaster_table FOR UPDATE)
        LOOP
          sdo_geor.addNODATA(rec.georaster, 0, 0);
          UPDATE georaster_table SET georaster=rec.georaster
            WHERE georid=rec.georid;
    END LOOP;
    COMMIT;
     END;
    /

**Parent topic:** GeoRaster Data Query and Manipulation

### 4.16 Using Template-Related Subprograms to Develop GeoRaster Applications

The [SDO_GEOR.createTemplate](SDO_GEOR-reference.md) and [SDO_GEOR.getRasterBlockLocator](SDO_GEOR-reference.md) subprograms enable you to develop GeoRaster applications, such as ETL tools and image processing systems that work with GeoRaster objects, by reading and writing GeoRaster metadata and binary raster data without dealing directly with the Oracle XMLType, the GeoRaster XML schema, and Oracle BLOBs.

After you create a new GeoRaster object (explained in [Creating New GeoRaster Objects](georaster-database-creation-management.md)), you can use the [SDO_GEOR.createTemplate](SDO_GEOR-reference.md) function to populate the metadata of the GeoRaster object with basic information, such as raster type, dimension sizes, ultCoordinates, cell depth, interleaving type, blocking and block size, pyramid resampling method and reducing level, and compression method and quality. This function can optionally populate the raster data table with the correct number of rows and row data consisting of raster blocks containing empty BLOBs.

The XML metadata generated by the [SDO_GEOR.createTemplate](SDO_GEOR-reference.md) function conforms to the GeoRaster metadata schema. You can then use other GeoRaster subprogams to query or update the metadata (see Querying and Updating GeoRaster Metadata).

You can use the [SDO_GEOR.getRasterBlockLocator](SDO_GEOR-reference.md) procedure to get the raster block locator by specifying the pyramid level and block number. If you have the raster block locator, you can then use the OCI or Java JDBC LOB interfaces to read and write the binary raster data. (The [SDO_GEOR.getRasterBlockLocator](SDO_GEOR-reference.md) procedure does not itself read or process LOB data.) To use this approach, you must understand the physical storage of the raster data (explained in [GeoRaster Physical Storage](georaster-overview-and-concepts.md)), and you must compress and decompress the data as necessary before reading from or writing to the BLOB.

**Parent topic:** GeoRaster Data Query and Manipulation
