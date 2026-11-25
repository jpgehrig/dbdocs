## 3 GeoRaster Database Creation and Management

This chapter describes how to perform important GeoRaster database creation and management operations. A typical workflow to build and manage a GeoRaster database consists of most or all of the steps described.

After you enable GeoRaster for all schemas that will use the feature, create the GeoRaster objects, load the data, and validate the GeoRaster objects, you can perform the remaining operations in any order, depending on your application needs. You may also be able to skip certain operations.

Some operations can be performed using SQL, and some operations must be performed using PL/SQL blocks. You must update the GeoRaster object after you insert, update, reformat, compress, decompress, or delete the metadata or cell data of the GeoRaster object and before you commit the changes (see [Updating GeoRaster Objects Before Committing](georaster-data-manipulation.md)). For some examples of these operations, see the demo files described in [GeoRaster PL/SQL and Java Demo Files](georaster-overview-and-concepts.md) and the examples in [SDO_GEOR Package Reference](SDO_GEOR-reference.md).

See also the operations in [GeoRaster Data Query and Manipulation](georaster-data-manipulation.md).

Other chapters in this book cover advanced topics ([Raster Algebra and Analytics](raster-algebra-and-analytics.md) and [Image Processing and Virtual Mosaic](image-processing-virtual-mosaic.md)), and provide detailed reference information about GeoRaster PL/SQL packages ([SDO_GEOR Package Reference](SDO_GEOR-reference.md), [SDO_GEOR_ADMIN Package Reference](SDO_GEOR_ADMIN-reference.md), [SDO_GEOR_AGGR Package Reference](SDO_GEOR_AGGR-referencer-ref.md), [SDO_GEOR_RA Package Reference](sdo-geor-ra-ref.md), and [SDO_GEOR_UTL Package Reference](SDO_GEOR_UTL-reference.md)).

- Enabling GeoRaster at the Schema Level
- Adding Data Files and Temporary Tablespaces for GeoRaster Users
- Creating the GeoRaster Table and Raster Data Tables
- Creating New GeoRaster Objects
- Loading Raster Data
- Validating GeoRaster Objects
- Georeferencing GeoRaster Objects
- Generating and Setting Spatial Extents
- Indexing GeoRaster Objects
- Viewing GeoRaster Objects
- Exporting GeoRaster Objects
- Using GeoRaster with Workspace Manager and Label Security
- Maintaining Efficient Tablespace Use by GeoRaster Objects
- Checking GeoRaster Tables and Objects in the Database
- Maintaining GeoRaster Objects and System Data in the Database
- Transferring GeoRaster Data Between Databases

### 3.1 Enabling GeoRaster at the Schema Level

GeoRaster must be enabled for each database schema that will use the GeoRaster feature.

By default, the GeoRaster feature is disabled after the Oracle Spatial and Graph is initially installed. GeoRaster can be enabled only within the scope of a schema (that is, not for the entire database), and it must be enabled for each schema that will use the GeoRaster feature.

To enable GeoRaster, follow these steps for each schema for which GeoRaster will be enabled:

1.  Ensure that the user for this schema has the `CREATE TRIGGER` privilege (which is required for GeoRaster to work properly). If the user does not have the `CREATE TRIGGER` privilege (or if you do not know), connect as a user with DBA privilege and execute the following code:
        GRANT CREATE TRIGGER TO scott;
2.  Connect to the database as the user for that schema. For example:
        CONNECT scott/<password-for-scott>
3.  Enter the following statement:
        EXECUTE SDO_GEOR_ADMIN.enableGeoRaster;
4.  Verify that GeoRaster is now enabled by checking that the following statement returns `TRUE`:
        SELECT /*+ NO_RESULT_CACHE */ SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

For each database schema, [SDO_GEOR_ADMIN.enableGeoRaster](SDO_GEOR_ADMIN-reference.md) only needs to be called once. In any case, user can call [SDO_GEOR_ADMIN.isGeoRasterEnabled](SDO_GEOR_ADMIN-reference.md) function to check if GeoRaster feature is enabled. [SDO_GEOS_ADMIN.disableGeoRaster](SDO_GEOR_ADMIN-reference.md) procedure can be used to disable GeoRaster feature for the database schema.

If a GeoRaster table has been created and populated with data, then after a database upgrade, GeoRaster is automatically enabled for that table’s schema, and you do not need to re-enable GeoRaster for the schema. (Just ensure that the CREATE TRIGGER privilege is granted to the user.)

**Parent topic:** GeoRaster Database Creation and Management

### 3.2 Adding Data Files and Temporary Tablespaces for GeoRaster Users

A GeoRaster database is typically very large. For storage and performance reasons, a database schema should use one or more user tablespaces for GeoRaster data storage (avoid using the system tablespace for storing GeoRaster data), and you should add data files to the tablespaces appropriately. If Oracle Automatic Storage Management (Oracle ASM) or a bigfile tablespace is not being used, you should create many data files for each tablespace and distribute the data files on different disks if possible. You also should create data files or alter existing data files, so that they automatically increase in size when more space is needed in the database.

A GeoRaster table can contain a large (potentially almost unlimited) number of GeoRaster objects. A raster data table (RDT) should be used to contain the raster blocks of a limited number of GeoRaster objects, depending on the size of the rasters. In contrast with GeoRaster tables, an RDT should not grow too large, unless partitioning is to be applied. Also, RDTs can be created on different tablespaces, so that the raster blocks are distributed to different disks. (See also Creating the GeoRaster Table and Raster Data Tables.)

A GeoRaster database may use a temporary tablespace for some operations. When compression is involved in GeoRaster operations, particularly for large scale mosaicking operations, some temporary spaces are needed to store intermediate compressed or uncompressed data. If the GeoRaster user does not have a temporary tablespace, the database system temporary tablespace is used. This is not efficient and may slow down the mosaicking and other operations. Therefore, you should always create temporary tablespaces for GeoRaster users. For example:

    CONNECT system/<password>;
    CREATE TEMPORARY TABLESPACE geor_temp TEMPFILE 'geor_temp_1.f' SIZE 1G AUTOEXTEND ON;
    ALTER USER <georaster_user> TEMPORARY TABLESPACE geor_temp;

In general, the amount of temporary space needed is limited. However, for large scale mosaicking, if the result is to be compressed, the temporary space needed is equal to the uncompressed image size of the result. Therefore, specify `AUTOEXTEND ON` when you create temporary tablespaces for GeoRaster users.

**Parent topic:** GeoRaster Database Creation and Management

### 3.3 Creating the GeoRaster Table and Raster Data Tables

Before you can work with GeoRaster objects, you must create a GeoRaster table and one or more raster data tables, if they do not already exist.

- Creating a GeoRaster Table
- Creating Raster Data Tables
- Creating GeoRaster DML Triggers

**Parent topic:** GeoRaster Database Creation and Management

#### 3.3.1 Creating a GeoRaster Table

A GeoRaster table is any table that includes at least one column of type SDO_GEORASTER. The column can be an attribute column of another user-defined object type. Example 3-1 creates a GeoRaster table named CITY_IMAGES, which contains a column named IMAGE for storing GeoRaster objects.

Example 3-1 Creating a GeoRaster Table for City Images

    CREATE TABLE city_images (image_id NUMBER PRIMARY KEY, image_description VARCHAR2(50), image SDO_GEORASTER);

For more information about GeoRaster tables, see [GeoRaster Physical Storage](georaster-overview-and-concepts.md).

**Parent topic:** Creating the GeoRaster Table and Raster Data Tables

#### 3.3.2 Creating Raster Data Tables

After creating a GeoRaster table, you should create one or more raster data tables (RDTs) to be used with the objects in the GeoRaster table. You can create the RDT as an object table or as a relational table. You should use the LOB storage format SecureFiles LOBs (SecureFiles) when creating RDTs. Using SecureFiles significantly improves the performance of GeoRaster operations, compared to using the original LOB storage paradigm BasicFiles LOBS (BasicFiles).

**Note:**

The RDT names must be unique in the database as described in [Raster Data Table](georaster-overview-and-concepts.md).

Example 3-2 creates an RDT using SecureFiles. The RDT will be used to store all raster blocks of one or many GeoRaster objects in the CITY_IMAGES table or other GeoRaster tables. (The association between a GeoRaster object and the RDT is not made until you create a GeoRaster object, as explained in Creating New GeoRaster Objects.)

Example 3-2 Creating a Raster Data Table Using SecureFiles

    CREATE TABLE city_images_rdt OF SDO_RASTER
      (PRIMARY KEY (rasterID, pyramidLevel, bandBlockNumber,
        rowBlockNumber, columnBlockNumber))
      TABLESPACE im_tbs_2
      LOB(rasterBlock) STORE AS SECUREFILE
        (CACHE);

Example 3-3 Creating a Raster Data Table (Relational) Using SecureFiles

Example 3-3 creates an RDT with the same name as in Example 3-2, also using SecureFiles, but creating it as a relational table instead of an object table.

    CREATE TABLE city_images_rdt
      (rasterID NUMBER,
      pyramidLevel NUMBER,
      bandBlockNumber NUMBER,
      rowBlockNumber NUMBER,
      columnBlockNumber NUMBER,
      blockMBR SDO_GEOMETRY,
      rasterBlock BLOB,
      CONSTRAINT pkey PRIMARY KEY (rasterId, pyramidLevel, bandBlockNumber,
        rowBlockNumber, columnBlockNumber))
      LOB (rasterblock) STORE AS SECUREFILE(cache);

The CREATE TABLE statement for the RDT must include the following clause (which is included in the preceding examples):

      (PRIMARY KEY (rasterID, pyramidLevel, bandBlockNumber,
        rowBlockNumber, columnBlockNumber))

This PRIMARY KEY clause creates a B-tree index on the raster data table, and this index is essential for optimal query performance.

When you use BasicFiles, you can specify a larger CHUNK size (16 or 32 KB) for the LOB storage to improve performance. With SecureFiles, there is no need to specify the CHUNK size parameter, and there are few other storage parameters to consider. Raster data tables using SecureFiles LOBs must be created in a tablespace with the automatic segment space management option. For information about using Oracle SecureFiles and performance considerations for BasicFiles LOBs, see [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/index.md).

For reference information about creating tables, including specifying LOB storage, see the section about the CREATE TABLE statement in [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md).

For more information about the keywords and options when creating an RDT, see [Raster Data Table](georaster-overview-and-concepts.md).

**Parent topic:** Creating the GeoRaster Table and Raster Data Tables

#### 3.3.3 Creating GeoRaster DML Triggers

To ensure the consistency and integrity of internal GeoRaster tables and data structures, GeoRaster automatically creates a unique DML trigger for each GeoRaster column whenever a user creates a GeoRaster table (that is, a table with at least one GeoRaster column). This implies that you do not need to manually create the GeoRaster DML triggers in general.

However, there is an exception. That is, if you use the ALTER TABLE statement to add one or more GeoRaster columns, you must call the [SDO_GEOR_UTL.createDMLTrigger](SDO_GEOR_UTL-reference.md) procedure to create the DML trigger on each added GeoRaster column. For example, if you added a new column `added_geor_col` to your table `my_geor_tab`, you must run the following command:

    EXECUTE SDO_GEOR_UTL.createDMLTrigger('MY_GEOR_TAB', 'ADDED_GEOR_COL');

Also, in some scenarios, such as a database upgrade or a data migration, you can call the [SDO_GEOR_UTL.recreateDMLTriggers](SDO_GEOR_UTL-reference.md) procedure to re-create the DML triggers on all GeoRaster columns.

The trigger is fired after each of the following data manipulation language (DML) operations affecting a GeoRaster object: insertion of a row, update of a GeoRaster object, and deletion of a row.

GeoRaster automatically performs the following actions when the trigger is fired:

- After an insert operation, the trigger inserts a row with the GeoRaster table name, GeoRaster column name, raster data table name, and `rasterID` value into the USER_SDO_GEOR_SYSDATA view (described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md)). If an identical entry already exists, an exception is raised.

- After an update operation, if the new GeoRaster object is null or empty, the trigger deletes the old GeoRaster object. If there is no entry in the USER_SDO_GEOR_SYSDATA view for the old GeoRaster object (that is, if the old GeoRaster object is null), the trigger inserts a row into that view for the new GeoRaster object. If there is an entry in the USER_SDO_GEOR_SYSDATA view for the old GeoRaster object, the trigger updates the information to reflect the new GeoRaster object.

- After a delete operation, the trigger deletes raster data blocks for the GeoRaster object in its raster data table, and it deletes the row in the USER_SDO_GEOR_SYSDATA view for the GeoRaster object.

**Parent topic:** Creating the GeoRaster Table and Raster Data Tables

### 3.4 Creating New GeoRaster Objects

Before you can store a GeoRaster image in a GeoRaster table, you must create the GeoRaster object and insert it into a GeoRaster table before you start working on it. To create a new GeoRaster object, you have the following options:

- Initialize an empty GeoRaster object, using the [SDO_GEOR.init](SDO_GEOR-reference.md) function.

- Create a blank GeoRaster object, using the [SDO_GEOR.createBlank](SDO_GEOR-reference.md) function.

You cannot perform any GeoRaster operations if the object has not been properly created (that is, if the object is an atomic null). The [SDO_GEOR.init](SDO_GEOR-reference.md) and [SDO_GEOR.createBlank](SDO_GEOR-reference.md) functions initialize GeoRaster objects with their raster data table and raster ID values if these are not already specified, and the GeoRaster DML trigger ensures that the raster data table name and raster ID value pair is unique for the current user.

If the new GeoRaster object will hold raster cell data (resulting from another GeoRaster procedure, such as [SDO_GEOR.importFrom](SDO_GEOR-reference.md), [SDO_GEOR.subset](SDO_GEOR-reference.md), or [SDO_GEOR.copy](SDO_GEOR-reference.md)), and if the raster data table for this new GeoRaster object does not exist, you must first create the raster data table. For information about creating a raster data table, including examples, see Creating Raster Data Tables.

To avoid potential GeoRaster data problems (some of which are described in Maintaining GeoRaster Objects and System Data in the Database), an initialized GeoRaster object must be registered in the GeoRaster system views, which is done automatically when you insert the GeoRaster object into a GeoRaster table. This should be done before you perform any other operations on the GeoRaster object. Any GeoRaster operations that need to manipulate the raster data table raise an exception if the source or target GeoRaster object is not registered.

**Parent topic:** GeoRaster Database Creation and Management

### 3.5 Loading Raster Data

To load and export imagery or raster data, you can consider third-party ETL tools (see the note in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)). For example, you can use the gdal_translate command line and other GDAL utilities, which fully support GeoRaster through the Oracle Spatial and Graph GeoRaster driver.

You can also use features in GeoRaster to load raster data, With GeoRaster, you have the following options:

- Use the GDAL based ETL tool for concurrent batch loading and exporting of large amount of images in GDAL supported formats. This tool is described in [GDAL-Based ETL Wizard for Concurrent Batch Loading and Exporting](georaster-overview-and-concepts.md).

- In PL/SQL call the [SDO_GEOR_GDAL.translate](SDO_GEOR_GDAL-reference.md) procedure (for non-autonomous databases only) to load images into GeoRaster objects.

- In PL/SQL, call the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure to load some small images into GeoRaster objects.

- Use the GeoRaster JAI-based loader tool or viewer tool, which are described in [JAI-Based Viewer\_ Loader\_ and Exporter](georaster-overview-and-concepts.md).

It is recommended to use [GDAL](georaster-overview-and-concepts.md), the [GDAL-Based ETL](georaster-overview-and-concepts.md), and [SDO_GEOR_GDAL.translate](SDO_GEOR_GDAL-reference.md) to load and export image and raster files. With the last option (JAI-based tool), you can do the following:

- Compress raster data and store the data in JPEG-compressed or DEFLATE-compressed GeoRaster objects.

- Load an ESRI world file or a Digital Globe RPC text file (.rpb) into an existing GeoRaster object, and georeference the raster data without reloading it. You can also specify an SRID with the world file and generate the spatial extent of the data.

- Load a GeoTIFF format file with georeferencing, with or without raster data. To load and export the georeferencing information of GeoTIFF images, the GeoTIFF libraries are required. See Georeferencing GeoRaster Objects for instructions.

After loading raster data into a GeoRaster object, you must ensure that the object is valid by calling the [SDO_GEOR.validateGeoRaster](SDO_GEOR-reference.md) function, as explained in Validating GeoRaster Objects.

Because an ESRI world file or .`rpb` file does not contain coordinate system information, you can specify the SRID value of a coordinate reference system for the load operation. However, if you do not specify an SRID, the model SRID of the GeoRaster objects is set to 0 (zero) by the loader, which means that the GeoRaster object is invalid, and therefore you must use the [SDO_GEOR.setModelSRID](SDO_GEOR-reference.md) procedure to specify a valid model space for this object. If you do not yet know the coordinate system of the model space, you can specify the SRID value as 999999, which means that the coordinate reference system is unknown. (Specifically, SRID 999999 is associated with a coordinate reference system named `unknown CRS`.) Later, when you know the actual coordinate reference system of the model space, you can set the SRID value accordingly.

For more information about the `unknown CRS` (SRID 999999) coordinate reference system, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).

- Loading with Blocking and Optimal Padding
- Loading JPEG and JPEG 2000 Images Without Decompression
- Reformatting the Source Raster Before Loading

**Parent topic:** GeoRaster Database Creation and Management

#### 3.5.1 Loading with Blocking and Optimal Padding

Unless you want to load JPEG or JPEG2000 images and store them without any change, when you load an image or raster file into GeoRaster object, always consider and apply appropriate blocking of the data, because file formats might have very different blocking schemes. In general, blocking sizes should be 512x512 or larger. There is no absolute rule for the blocking sizes, but the larger the raster, the larger the blocking sizes you might use. For regular rasters, 512x512 to 2048x2048 is appropriate. For very small images (less than 1024x1024x3), no blocking may be a good choice. Avoid blocking sizes that are either too small (such as 64x64 and 128x128) or too large, and avoid extreme blocking sizes such as 0.5 (one-half), 1, or 8 rows of pixels per block. Generally, the rectangular shape of blocks should be a square or close to a square. For different applications, you might tune the blocking to balance efficient storage with optimal performance.

You should also always apply optimal padding during loading. In other words, specify `blocking=OPTIMALPADDING` in addition to specifying `blocksize`. GeoRaster applies padding to the right column and bottom row of blocks to make them the same size as other blocks. If the block size is not optimal for a specific raster, the default resulting padding would waste some storage space. When you specify`blocking=OPTIMALPADDING`, all GeoRaster procedures and the ETL tools automatically adjust the GeoRaster dimension size array so that it will be optimal for reducing the amount of padding in GeoRaster object storage. The adjustment is always made around the user-specified values. See the explanation of the `blocking` keyword in the table in the Usage Notes for the [SDO_GEOR_UTL.calcOptimizedBlockSize](SDO_GEOR_UTL-reference.md)procedure.

For how to apply optimal padding when using the GDAL command line, see the following example:

    gdal_translate -of georaster /images/image_1.tif \
          georaster:georaster/georaster@my_db, image_table, raster \
          -co "insert=(id,label,raster) values (1, 'image_1', sdo_geor.init('rdt_table', 1)" \
          -co blockxsize= 512 \
          -co blockysize=512 \
          -co blockbsize=3 \
          -co blocking=optimalpadding \
          -co interleave=BIP

**Parent topic:** Loading Raster Data

#### 3.5.2 Loading JPEG and JPEG 2000 Images Without Decompression

GeoRaster supports JPEG compression, in which the GeoRaster blocks are stored as JPEG files. GeoRaster also supports JPEG 2000 compression, in which the GeoRaster has a single block stored as a JPEG 2000 file. There are some special cases where you can load and export JPEG or JPEG 2000 images without decompressing and recompressing, thus improving performance significantly.

For JPEG, you can use the JAI-based GeoRaster loader to load the image directly without decompression and recompression if the image file is a JPEG file, the GeoRaster object's compression type is specified as JPEG-F and no blocking is specified for the GeoRaster object's storage (that is, the GeoRaster object has only one block).

For JPEG 2000, you can use GDAL or the GDAL-based GeoRaster ETL tool to load the image directly without decompression and recompression – if the image file is a JPEG2000 file and if no parameters in use require any change to the internal structure of the JPEG 2000 file. For example, the following script loads the JPEG 2000 file directly without decompression.

    gdal_translate -of georaster /images/image_3.jp2 \
          georaster:georaster/georaster@my_db,image_table,raster \
          -co "insert=(id,label,raster) values (3, 'image_3', sdo_geor.init('rdt_table', 3)" \
          -co compress=jp2-f

However, if any of the parameter in use require changing the internal structure of the JPEG 2000 data, direct loading will not be possible. The following example requires decompression and recompression, resulting in a substantial increase of the loading time.

    gdal_translate -of georaster /images/image_4.jp2 \
          georaster:georaster/georaster@my_db,image_table,raster \
          -co "insert=(id,label,raster) values (4, 'image_4', sdo_geor.init('rdt_table', 4)" \
          -co compress=jp2-f \
          -co blockxsize=1024 \
          -co blockysize=1024 \
          -srcwin 100 200 1000 1000 \
          -outsize 50% 50%

**Parent topic:** Loading Raster Data

#### 3.5.3 Reformatting the Source Raster Before Loading

The GeoRaster JAI-based loader does not support source raster files in BSQ interleaving, and it might raise an "insufficient memory" error if the files are too big, and it might have other restrictions. To avoid such problems, you can reformat and reblock the source files so that they can be properly loaded. However, it is always recommended that you use the GDAL-based ETL loader, which generally does not have such issues and requirements, before you consider the following approach.

As an example, one way to do this is to use GDAL, an Open Source raster transformation library available from [`http://www.gdal.org`](http://www.gdal.org), to reformat or reblock the image or raster file so that JAI (Java Advanced Imaging) can handle it. GDAL supports GeoRaster natively and can import and export GeoRaster objects directly, and can also process GeoRaster objects; for more information, see [`http://www.oracle.com/technetwork/database/enterprise-edition/getting-started-with-gdal-133874.pdf`](http://www.oracle.com/technetwork/database/enterprise-edition/getting-started-with-gdal-133874.pdf). You can also use GDAL to generate TFW files. For example, execute commands such as the following two (each command on a single line) using the GDAL command line or (for batch conversion) shell:

    gdal_translate -of GTiff -co "TFW=YES" -co "INTERLEAVE=PIXEL" -co "TILED=YES" D:\my_image.tif D:\my_new_image.tif

    gdal_translate -of GTiff -co "TILED=YES" -co "TFW=YES" D:\my_image.ecw D:\my_new_image.tif

In the preceding example, the first command generates a TFW file, changes the interleaving to BIP (which is supported by JAI), and reblocks the image to 256x256. The second command converts ECW to TIFF, generates TFW, and reblocks the image.

Then use the GeoRaster loader tool (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)) , specifying reblocking so that the image can be loaded successfully and later retrieved from the database efficiently, as in the following example (a single command):

    java -Xmx1024m oracle.spatial.georaster.tools.GeoRasterLoader mymachine db11 6521 georaster georaster thin 32 T globe image "blocking=true, blocksize=(512,512,3)" "D:my_image.tif,2,RDT_15, D:\my_image.tfw,82213"

If you receive an "insufficient memory" error when calling [SDO_GEOR.importFrom](SDO_GEOR-reference.md) to load a very large image, try loading the image with a different blocking size parameter or reblock the image into smaller internal tile sizes using GDAL before loading. For extremely large images, you can also use GDAL to tile the image into multiple smaller image files with sizes that JAI can handle, or you use GDAL to load and export the images directly.

**Parent topic:** Loading Raster Data

### 3.6 Validating GeoRaster Objects

Before you use a GeoRaster object or after you manually edit the raster data and metadata of a GeoRaster object, you should ensure that the object is valid. Validation for a GeoRaster object includes checking the registration of the GeoRaster object, checking the metadata and the raster cell data, and making sure that the metadata and data are consistent. For example, validation checks the raster type, dimension information, and the actual sizes of cell blocks, and it performs other checks.

If you used the GeoRaster loader tool described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md), the GeoRaster objects were validated during the load operation.

GeoRaster provides the following validation subprograms:

- [SDO_GEOR.validateGeoRaster](SDO_GEOR-reference.md) validates the GeoRaster object, including cell data and metadata. It returns `TRUE` if the object is valid; otherwise, it returns one of the following: an Oracle error code indicating why the GeoRaster object is invalid, `FALSE` if validation fails for an unknown reason, or `NULL` if the GeoRaster object is null. You should always use this function after you create a GeoRaster object.

- [SDO_GEOR.schemaValidate](SDO_GEOR-reference.md) validates the metadata against the GeoRaster XML schema. You can use this function to locate errors if the [SDO_GEOR.validateGeoRaster](SDO_GEOR-reference.md) function returned the error code 13454. The [SDO_GEOR.schemaValidate](SDO_GEOR-reference.md) and [SDO_GEOR.validateGeoRaster](SDO_GEOR-reference.md) functions do not validate the spatial extent geometry.

- [SDO_GEOR.validateBlockMBR](SDO_GEOR-reference.md) validates the `blockMBR` geometry associated with each raster block stored in the raster data table. If there are any invalid `blockMBR` geometries, call the [SDO_GEOR.generateBlockMBR](SDO_GEOR-reference.md) procedure to regenerate them.

**Parent topic:** GeoRaster Database Creation and Management

### 3.7 Georeferencing GeoRaster Objects

Georeferencing, as explained in [Georeferencing](georaster-overview-and-concepts.md), establishes the relationship between cell coordinates of GeoRaster data and real-world ground coordinates (or some local coordinates). If you need to georeference GeoRaster objects, the following approaches are available:

- If the original image is already georeferenced and if the georeferencing information is stored in an ESRI world file or .`rpb` file containing RPC coefficients you can use the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure to load an ESRI world file or .`rpb` file from a file or from a CLOB object, along with the image data itself (in either FILE or BLOB format). You can also use the GeoRaster client-side loader tool (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)) to load an ESRI world file or .`rpb` file from a file, along with the image file itself.

  Because an ESRI world file or .`rpb` file does not specify the model coordinate system, you can set the model space of the georeferenced GeoRaster object using an Oracle SRID in either of the following ways: specify the SRID along with the world file as a parameter to the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure or the GeoRaster client-side loader (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)); or, after loading the world file, call the [SDO_GEOR.setModelSRID](SDO_GEOR-reference.md) procedure. You can also call the [SDO_GEOR.setModelSRID](SDO_GEOR-reference.md) procedure to change the model space of a georeferenced GeoRaster object.

- If the original image is a georeferenced GeoTIFF image, you can use the GeoRaster client-side loader tool (described in [GeoRaster Tools: Viewer, Loader, Exporter](georaster-overview-and-concepts.md)) to load only the georeferencing information from a GeoTIFF image, without the raster image data, into an existing GeoRaster object, by specifying `raster=false` along with `geotiff=true`. You can specify a backup SRID with the `srid` storage parameter, in case the GeoTIFF configuration values do not match any SRID recognized by Oracle Spatial and Graph.

- You can use the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure to add, modify, and delete georeferencing information by directly accessing the GeoRaster SRS metadata. For example, you can create an SDO_GEOR_SRS object and assign the coefficients and related georeferencing information, and then call the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure to add or update the spatial reference information of any GeoRaster object. You can use the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure to set up the spatial reference information for all supported functional fitting georeferencing models. Examples of setting up the SRS information from an existing DLT model and from an existing RPC model are included in reference section for the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure.

  If you know that one GeoRaster object has the same SRS information as another GeoRaster object, you can call the [SDO_GEOR.getSRS](SDO_GEOR-reference.md) function to retrieve an SDO_GEOR_SRS object from this GeoRaster object, and then call the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure to georeference the first GeoRaster object.

- If the GeoRaster object can be georeferenced using an affine transformation, you can call the [SDO_GEOR.georeference](SDO_GEOR-reference.md) procedure to georeference a GeoRaster object directly. As described in the reference information for the [SDO_GEOR.georeference](SDO_GEOR-reference.md), this procedure takes the coefficients `A`, `B`, `C`, `D`, `E`, `F` and other information, converts them into the coefficients `a`, `b`, `c`, `d`, `e`, `f`, and stores them in the spatial reference information of a GeoRaster object. If the original raster data is rectified and if the model coordinate of its origin (upper-left corner) is (x0, y0) and its spatial resolution or scale is `s`, then the following are true: A = s, B = 0, C = x0, D = 0, E = -s, F = y0.

- If you have ground control points (GCPs) or want to collect GCPs yourself, you can call the [SDO_GEOR.georeference](SDO_GEOR-reference.md) function to georeference the GeoRaster object. For more information, see [Advanced Georeferencing](image-processing-virtual-mosaic.md).

Based on the SRS information of a georeferenced GeoRaster object, transforming GeoRaster coordinate information means finding the model (ground) coordinate associated with a specific cell (raster) coordinate, and the reverse. That is, you can do the following:

- Given a specific cell coordinate, you can find the associated model space coordinate using the [SDO_GEOR.getModelCoordinate](SDO_GEOR-reference.md) function. For example, if you identify a point in an image, you can find the longitude and latitude coordinates associated with that point.

- Given a model space coordinate, you can find the associated cell coordinate using the [SDO_GEOR.getCellCoordinate](SDO_GEOR-reference.md) function. For example, if you identify longitude and latitude coordinates, you can find the cell in an image associated with those coordinates.

**Parent topic:** GeoRaster Database Creation and Management

### 3.8 Generating and Setting Spatial Extents

When a GeoRaster object is created, its spatial extent (`spatialExtent` attribute, described in [spatialExtent Attribute](georaster-datatypes.md)) is not necessarily the enclosing geometry in its model space coordinate system. The spatial extent (footprint) geometry might initially be null, or it might reflect the cell space coordinate system or some other coordinate system. The ability to generate and set spatial extents is useful for building large GeoRaster databases of a global or large regional scope, in which the spatial extents are in one global geodetic coordinate system while the GeoRaster objects (imagery, DEMs, and so on) are in different projected coordinate systems. In such a case, you can create a spatial (R-tree) index on the spatial extents, which requires that all spatial extent geometries have the same SRID value.

To ensure that the spatial extent geometry of each GeoRaster object in a table is correct for its model space coordinate system (or for any other coordinate system that you may want to use), you must set the spatial extent. Moreover, to use a spatial index on the spatial extent geometries (described in Indexing GeoRaster Objects), all indexed geometries must be based on the same coordinate system (that is, have the same SRID value).

You can set the spatial extent in any of the following ways: specify `spatialExtent=TRUE` as a storage parameter to the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure or the GeoRaster client-side loader (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)), use the SQL UPDATE statement, or set the spatial extent during loading with GDAL. If you use the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure or the loader, the SRID cannot be null or 0 (zero), and if there is an R-tree index on the GeoRaster spatial extent, the SRID of the spatial extent must match the SRID of the existing spatial index; otherwise, the spatial extent is set to a null value.

In addition, if you do not already have the spatial extent geometry, you can generate it using the [SDO_GEOR.generateSpatialExtent](SDO_GEOR-reference.md) function, and use that geometry to update the GeoRaster object. The following example updates the spatial extent geometry of a specified GeoRaster object in the CITY_IMAGES table (created in Example 3-1 in Creating a GeoRaster Table) to the generated spatial extent (reflecting the model coordinate system) of that object:

    UPDATE city_images c
      SET c.image.spatialExtent = sdo_geor.generateSpatialExtent(image)
        WHERE c.image_id = 100;
    COMMIT;

The following example updates the spatial extent geometry of all GeoRaster objects in the CITY_IMAGES table to the generated spatial extent (reflecting the model coordinate system) of that object:

    UPDATE city_images c
      SET c.image.spatialExtent = sdo_geor.generateSpatialExtent(image)
        WHERE c.image.spatialExtent is null;
    COMMIT;

If you already know the spatial extent geometry for a GeoRaster object, or if you want the spatial extent geometry to be based on a coordinate system other than the one for the model space, construct the SDO_GEOMETRY object or select it from a table, and then update the GeoRaster object to set its spatial extent attribute to that geometry, as shown in the following example:

    DECLARE
     geom sdo_geometry;
    BEGIN
    -- Set geom to an SDO_GEOMETRY object that covers the spatial extent
    -- of the desired GeoRaster object. If necessary, perform coordinate
    -- system transformation before setting geom.
    -- geom := sdo_geometry(...);
      UPDATE city_images c
        SET c.image.spatialExtent = geom WHERE c.image_id = 100;
      COMMIT;
    END;

- Special Considerations if the GeoRaster Table Has a Spatial Index

**Parent topic:** GeoRaster Database Creation and Management

#### 3.8.1 Special Considerations if the GeoRaster Table Has a Spatial Index

If you create a spatial R-tree index on the GeoRaster spatial extents (as described in Indexing GeoRaster Objects), all spatial extent geometries must have the same SRID value. However, the GeoRaster objects may have different model SRIDs, and most GeoRaster operations automatically generate a spatial extent for the output GeoRaster objects based on the model SRID of the source GeoRaster object or objects. This can cause problems when the resulting GeoRaster object with a spatial extent is updated into a GeoRaster table, which might already have a spatial index built on its `spatialExtent` attribute but using a different SRID.

In such cases, you must transform the spatial extent to the same SRID as that of the spatial index before the insert or update operation. The following example performs a mosaic operation, but then transforms the spatial extent of the resulting GeoRaster object to SRID 4326 before updating the GeoRaster table with that object.

    DECLARE
      gr sdo_georaster;
    BEGIN
      SELECT georaster INTO gr FROM mosaic_test WHERE georid=1 FOR UPDATE;
      sdo_geor.mosaic('mosaic_data', 'georaster', gr, 'blocking=OPTIMALPADDING,
    blocksize=(512,512)');
      -- Transform the spatial extent geometry, if ncessary.
      -- In this example example, the modelSRID of the mosaic is 27302,
      -- but the SRID of the spatial index on mosaic_test is 4326.
      gr.spatialExtent := sdo_cs.transform(gr.spatialExtent, 4326);
      UPDATE mosaic_test SET georaster=gr WHERE georid=1;
    END;
    /

If a spatial R-tree index exists, a commit operation after an insert or update operation causes the index to be updated if the inserted or updated GeoRaster object has a spatial extent geometry. This could slow some operations if you perform a commit after each operation, particularly for batch jobs such as batch image loading. It is usually more efficient to balance the performance of index updates with GeoRaster operations, and to commit only in batches after the operations.

For example, image data loading (the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure and the GeoRaster loader) is followed by an internal commit operation, so it would be inefficient to load while generating spatial extents by specifying `spatialExtent=TRUE`. Instead, you should probably specify `spatialExtent=FALSE`, and then update the `spatialExtent` attribute afterward, to speed the loading process.

**Parent topic:** Generating and Setting Spatial Extents

### 3.9 Indexing GeoRaster Objects

GeoRaster data can be indexed in various ways. The most important index you can create on a GeoRaster object is a spatial (R-tree) index on the spatial extent (footprint) geometry of the GeoRaster object (`spatialExtent` attribute, described in [spatialExtent Attribute](georaster-datatypes.md)). For large-scale geospatial image and raster databases, you should always create spatial indexes on the GeoRaster columns. The following are the basic steps to create a spatial index on GeoRaster column. (The examples assume that the GeoRaster table name is CITY_IMAGES and its GeoRaster column name is IMAGE.)

1.  Insert a row into the USER_SDO_GEOM_METADATA view with the georaster table name (CITY_IMAGES in this example) and the spatial extent of the GeoRaster column name (IMAGE.SPATIALEXTENT). Be sure that the correct SRID value (3371 in this example) is registered.
        INSERT INTO user_sdo_geom_metadata
            (TABLE_NAME,
             COLUMN_NAME,
             DIMINFO,
             SRID)
        VALUES (
             'city_images',
             'image.spatialextent',
             SDO_DIM_ARRAY(
                SDO_DIM_ELEMENT('X', -1000000000, 1000000000, 0.005),
                SDO_DIM_ELEMENT('Y', -1000000000, 1000000000, 0.005)),
             3371
        );
2.  Create a spatial index on the GeoRaster column, as in the following example which creates a spatial index named CITY_IMAGES_IDX on the spatial extents of the images using default values for all parameters.
        CREATE INDEX city_images_idx
              ON city_images (image.spatialextent)
              INDEXTYPE IS MDSYS.SPATIAL_INDEX;

    The preceding statement may fail if there are some invalid spatial extents or if the SRID values in the GeoRaster table do not match the SRID registered in the preceding step. If the statement fails, ensure that all GeoRaster objects have a valid `spatialExtent` geometry attribute and that all `spatialExtent` geometries have the same SRID. (Null for the `spatialExtent` values is acceptable.) Then re-create the spatial index.

See also Special Considerations if the GeoRaster Table Has a Spatial Index for special considerations if the GeoRaster table already has a spatial index. For more information about creating spatial indexes and about advanced capabilities, see [Oracle Spatial and Graph Developer's Guide](../spatl/indexing-querying-spatial-data.md).

You can also create one or more other indexes, such as:

- Function-based indexes on metadata objects using the Oracle XMLType or Oracle Text document indexing functionality

- Standard indexes on other user-defined columns of the GeoRaster table, such as cloud coverage, water coverage, or vegetation

You should also create a single B-tree index on the `rasterId`, `pyramidLevel`, `bandBlockNumber`, `rowBlockNumber`, and `columnBlockNumber` columns of each raster data table. This should be done using `PRIMARY KEY (rasterID, pyramidLevel, bandBlockNumber,rowBlockNumber, columnBlockNumber)`, as shown in Example 3-2 and Example 3-3.

**Parent topic:** GeoRaster Database Creation and Management

### 3.10 Viewing GeoRaster Objects

To view GeoRaster objects, you have the following options:

- Call the [SDO_GEOR.exportTo](SDO_GEOR-reference.md) procedure to export GeoRaster objects to image files, and then display the images using image tools or a Web browser.

- Use the standalone GeoRaster viewer tool (one of the tools described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)).

- Use Oracle Fusion Middleware MapViewer or its associated Map Builder utility.

With the GeoRaster viewer tool, you can select a GeoRaster object of a database schema (user), query and display the whole or a subset of a GeoRaster object, zoom in and zoom out, scroll, and perform other basic operations. The pyramid level, cell coordinates, and model coordinates (if the object is georeferenced) are displayed for the point at the mouse pointer location. You can display individual cell values and choose different layers of a multiband or hyperspectral image for RGB full color display. The blocking boundaries can be overlapped on the top of the display. Depending on the data and your requests, the viewer can display the raster data in grayscale, pseudocolor, and 24-bit true color over an intranet or the Internet. Some of the basic GeoRaster metadata is also displayed.

The GeoRaster viewer tool allows you to display a virtual mosaic defined as one or a list of GeoRaster tables or views.

The GeoRaster viewer tool provides a set of image processing operators for enhanced display of the GeoRaster objects, especially for those whose cell depth is greater than 8 or is a floating-point number. It can also display and apply bitmap masks on the GeoRaster objects if they have bitmap masks.

The GeoRaster viewer tool also includes menu commands to call the GeoRaster loader and exporter tools, thus enabling you to use a single tool as an interface to the capabilities of all the GeoRaster tools.

Visualization applications can leverage the default RGBA and default pyramid level specifications in the GeoRaster objects. You can set up different bands in a multiband image as the default Red, Green, Blue, and Alpha channels by calling [SDO_GEOR.setDefaultColorLayer](SDO_GEOR-reference.md) or [SDO_GEOR.setDefaultRed](SDO_GEOR-reference.md), [SDO_GEOR.setDefaultGreen](SDO_GEOR-reference.md), [SDO_GEOR.setDefaultBlue](SDO_GEOR-reference.md), and [SDO_GEOR.setDefaultAlpha](SDO_GEOR-reference.md). For large images, you can call [SDO_GEOR.setDefaultPyramidLevel](SDO_GEOR-reference.md) to set up the best resolution (pyramid) level of an image for initial display in the applications. For example, for a complete overview of a whole image, it is best to set the top pyramid level as the default pyramid level.

**Parent topic:** GeoRaster Database Creation and Management

### 3.11 Exporting GeoRaster Objects

To load and export imagery or raster data, always consider third-party ETL tools (see the note in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md))

If you use features in GeoRaster to export GeoRaster objects to image files, you have the following options:

- Use the GDAL-based ETL tool for concurrent batch exporting, which is described in [GDAL-Based ETL Wizard for Concurrent Batch Loading and Exporting](georaster-overview-and-concepts.md).

- Call the [SDO_GEOR.exportTo](SDO_GEOR-reference.md) procedure (which can export either to a file or to a BLOB object).

- Use the GeoRaster exporter tool or viewer tool, which are described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md).

**Parent topic:** GeoRaster Database Creation and Management

### 3.12 Using GeoRaster with Workspace Manager and Label Security

Oracle Workspace Manager provides a versioning capability for the raster blocks of a GeoRaster object. Oracle Label Security supports GeoRaster objects with enhanced security at the row level of raster blocks.

To use GeoRaster with Oracle Workspace Manager or Oracle Label Security, you should create a raster data table (RDT) as a relational table for the GeoRaster objects (see Example 3-3). You do not need to define an object view of SDO_RASTER type on the base relational RDT.

- Using GeoRaster with Workspace Manager
- Using GeoRaster with Label Security

**Parent topic:** GeoRaster Database Creation and Management

#### 3.12.1 Using GeoRaster with Workspace Manager

With Workspace Manager, you can conveniently manage changes to the raster data by saving different raster data versions and making modifications in different workspaces. To use GeoRaster with Workspace Manager, you must use relational raster data tables for raster storage and version-enable these relational raster data tables. For example (general format):

    EXECUTE DBMS_WM.EnableVersioning (<rdt_relational_table>, 'VIEW_WO_OVERWRITE');

**Note:**

You can version-enable only raster data tables. Do not version-enable any GeoRaster tables, where GeoRaster objects are stored, and do not perform any operations that will require a GeoRaster table to be modified while you are in a workspace.

After you version-enable a relational RDT, you can use the subprograms in the DBMS_WM package to manage changes to the raster data. If you need to directly modify a raster block, call the DBMS_WM.copyForUpdate procedure before the operation, as shown in the following example:

    declare
      geor sdo_georaster;
      cond varchar2(1000);
      lb   blob;
      r1   raw(1024);
      amt  number;
    begin
      r1 := utl_raw.copies(utl_raw.cast_to_raw('0'),1024);

      select georaster into geor from georaster_table where georid=1;
      cond := 'rasterId=' || geor.rasterId || ' AND pyramidLevel=0 AND ' ||
              ' bandBlockNumber=0 AND rowBlockNumber=0 AND columnBlockNumber=0';
      dbms_wm.copyForUpdate(geor.rasterDataTable, cond);
      sdo_geor.getRasterBlockLocator(geor, 0, 0, 0, 0, lb, null, 'TRUE');
      amt := 1024;
      dbms_lob.write(lb, amt, 1, r1);
    end;
    /

However, if you modify raster data using GeoRaster subprograms, you do not need to call the DBMS_WM.copyForUpdate procedure beforehand.

For information about Workspace Manager, see [Oracle Database Workspace Manager Developer's Guide](../adwsm/introduction-to-workspace-manager.md).

**Parent topic:** Using GeoRaster with Workspace Manager and Label Security

#### 3.12.2 Using GeoRaster with Label Security

Oracle Label Security provides row-level access control for sensitive data based on a user's level of security clearance. To use GeoRaster with Label Security, follow these basic steps:

1.  Create the GeoRaster table and relational RDT or RDTs.
2.  Create an Oracle Label Security policy and define the label components.
3.  Create labeling functions for the GeoRaster table and the relational RDT or RDTs.
    The labels for rows in a GeoRaster table should be generated according to the application's requirements. Use the same label for both the row that stores a GeoRaster object and for the GeoRaster object's raster rows in the associated RDT; otherwise, the GeoRaster objects might be invalid or have an inconsistent status.

    The following example creates the labeling function for a relational RDT:

        CREATE OR REPLACE FUNCTION gen_rdt_label(rdt_name varchar2, rid number)
          RETURN LBACSYS.LBAC_LABEL
        AS
          tabname varchar2(80);
          schema  varchar2(32);
          grcol   varchar2(1024);
          colname varchar2(30);
          label   NUMBER;
        BEGIN
          EXECUTE IMMEDIATE
           'SELECT v.owner, v.table_name, v.column_name grcol, p.column_name ' ||
           '  FROM all_sdo_geor_sysdata v, all_sa_policies p, all_sa_table_policies t '
           || ' WHERE v.rdt_table_name=:1 AND v.raster_id=:2 AND ' ||
           ' v.owner=t.schema_name AND v.table_name=t.table_name AND ' ||
           ' p.policy_name=t.policy_name '
           INTO schema, tabname, grcol, colname
           USING upper(rdt_name), rid;
          EXECUTE IMMEDIATE
            'SELECT t.' || colname  ||
             ' FROM ' || schema || '.' || tabname || ' t ' ||
             ' WHERE t.' || grcol || '.rasterdatatable=:1 AND ' ||
             '       t.' || grcol || '.rasterid=:2'
            INTO label
            USING upper(rdt_name), rid;
          RETURN LBACSYS.LBAC_LABEL.NEW_LBAC_LABEL(label);
        END;
        /
4.  Apply the Label Security policy to a GeoRaster table and its associated RDT or RDTs.
    The following example (general format) applies a Label Security policy to an RDT using the labeling function example from the preceding step.

        BEGIN
          SA_POLICY_ADMIN.REMOVE_TABLE_POLICY(<policy_name>,<schema_name>,<rdt_relational_table>);
          SA_POLICY_ADMIN.APPLY_TABLE_POLICY(
            POLICY_NAME => <policy_name>,
            SCHEMA_NAME => <schema_name>,
            TABLE_NAME  => <rdt_relational_table>,
            TABLE_OPTIONS => 'READ_CONTROL,WRITE_CONTROL,CHECK_CONTROL',
            LABEL_FUNCTION => '<schema_name>.gen_rdt_label(<rdt_relational_table>,:new.rasterid)',
            PREDICATE => NULL);
        END;
        /
5.  Create and authorize users, and complete other administrative tasks related to Label Security.

You can load GeoRaster data before or after applying the policy to the tables.

The ALL_SDO_GEOR_SYSDATA view (described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md)) contains system data for all GeoRaster objects accessible by the current user, and accessibility in this case is determined by the user's privileges as defined in the context of discretionary access control (DAC).

After the label for a GeoRaster table row is updated, ensure that the related data labels in the RDT are updated, so that the labels are synchronized.

For information about Label Security, see [Oracle Label Security Administrator's Guide](../olsag/introduction-to-oracle-label-security.md).

**Parent topic:** Using GeoRaster with Workspace Manager and Label Security

### 3.13 Maintaining Efficient Tablespace Use by GeoRaster Objects

After delete or rollback operations, unused space allocated to a raster data table is not automatically returned to the underlying tablespace. This could result in wasted tablespace area. Since GeoRaster databases are usually large, it’s a good practice to efficiently maintain tablespace usage, particularly when disk space is limited. If the raster data table is created using BasicFiles LOBs in an automatic segment space management tablespace, you can explicitly shrink the `rasterBlock` LOB segment or the raster data table by altering the raster data table, so that the table segment can be compacted and unused LOB segment can be released to the tablespace, as shown in Example 3-4 and Example 3-5.

Example 3-4 Shrinking a BasicFile RasterBlock LOB Segment

    ALTER TABLE city_images_rdt MODIFY LOB (rasterBlock) (SHRINK SPACE);

Example 3-5 Shrinking a Raster Data Table

    ALTER TABLE city_images_rdt ENABLE ROW MOVEMENT;
    ALTER TABLE city_images_rdt SHRINK SPACE CASCADE;

As a good practice, if there will be some temporary GeoRaster objects to be created and used, you can always consider creating temporary GeoRaster tables and RDT tables to hold those GeoRaster objects. Once they are not needed, the temporary GeoRaster and RDT tables can be dropped to release the disk space.

**Parent topic:** GeoRaster Database Creation and Management

### 3.14 Checking GeoRaster Tables and Objects in the Database

For database management purposes, you might need check on GeoRaster tables and objects in the whole database or under a specific schema. After the GeoRaster database is created, you have the following options for checking or listing existing GeoRaster tables, RDT tables, and GeoRaster objects.

- Use the following subprograms check the status of existing GeoRaster objects and related objects in the current schema or the database, depending on the privileges associated with the database connection.

  [SDO_GEOR_ADMIN.listGeoRasterObjects](SDO_GEOR_ADMIN-reference.md) lists all GeoRaster objects defined in the current schema; or if you call this function as a user with DBA role, all GeoRaster objects defined in the database are listed.

  [SDO_GEOR_ADMIN.listGeoRasterColumns](SDO_GEOR_ADMIN-reference.md) lists all GeoRaster columns defined in the current schema; or if you call this function as a user with DBA role, all GeoRaster columns defined in the database are listed.

  [SDO_GEOR_ADMIN.listGeoRasterTables](SDO_GEOR_ADMIN-reference.md) lists all GeoRaster tables defined in the current schema; or if you call this function as a user with DBA role, all GeoRaster tables defined in the database are listed.

  [SDO_GEOR_ADMIN.listRDT](SDO_GEOR_ADMIN-reference.md) lists all  raster data tables (RDTs) defined in the current schema; or if you call this function as a user with DBA role, all raster data tables (RDTs) defined in the database are listed.

  [SDO_GEOR_ADMIN.listRegisteredRDT](SDO_GEOR_ADMIN-reference.md) lists all registered raster data tables (RDTs) defined in the current schema; or if you call this function as a user with DBA role, all registered RDTs defined in the database are listed . An RDT is registered if at least one entry in the SYSDATA table refers to it.

  [SDO_GEOR_ADMIN.listUnregisteredRDT](SDO_GEOR_ADMIN-reference.md) lists all unregistered raster data tables (RDTs) defined in the current schema; or if you call this function as a user with DBA role, all unregistered RDTs defined in the database are listed.. An RDT is unregistered if no entry in the SYSDATA table refers to it.

- Run SQL queries directly against GeoRaster sysdata views, and check or list GeoRaster tables and objects stored in the different schemas. This approach is more flexible than calling subprograms. It also enables some query results that cannot be returned by functions defined in the SDO_GEOR_ADMIN package. The following are some sample queries.

  List all GeoRaster objects that are defined in the schema HERMAN and MYTEST and accessible by the current schema.

      SELECT owner,TABLE_NAME,COLUMN_NAME,RDT_TABLE_NAME,RASTER_ID from all_sdo_geor_sysdata where owner='HERMAN' or owner='MYTEST';

  Count the total number of GeoRaster objects accessible by the current schema.

      SELECT count(*) from all_sdo_geor_sysdata;

  Count the total number of GeoRaster objects stored in the GeoRaster table GTF_TABLE in the current schema.

      SELECT count(*) from user_sdo_geor_sysdata where TABLE_NAME='GTF_TABLE';

  List all GeoRaster objects stored in the RDT table RDT_1 in the current schema.

      SELECT TABLE_NAME,COLUMN_NAME,RDT_TABLE_NAME,RASTER_ID from user_sdo_geor_sysdata where RDT_TABLE_NAME='RDT_1';

  Find out all GeoRaster tables that store some raster data in or reference the RDT table RDT_1 in the current schema.

      SELECT distinct TABLE_NAME from user_sdo_geor_sysdata where RDT_TABLE_NAME='RDT_1';

  List all RDT tables that are used by the GeoRaster table GTF_TABLE in the current schema.

      SELECT distinct RDT_TABLE_NAME from user_sdo_geor_sysdata where TABLE_NAME='GTF_TABLE';

**Parent topic:** GeoRaster Database Creation and Management

### 3.15 Maintaining GeoRaster Objects and System Data in the Database

Although GeoRaster provides internal database mechanism to prevent the creation of invalid GeoRaster objects and system data, sometimes such GeoRaster objects and system data might exist in the database, especially after an upgrade from a previous release, or after some user errors in operations on GeoRaster system data. Examples of such invalid objects and system data include the following:

- An entry in the GeoRaster system data views (xxx\_SDO_GEOR_SYSDATA, described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md)) refers to a nonexistent GeoRaster table or column.

- Two or more GeoRaster objects have the same pair of RDT name and raster ID values.

- Some GeoRaster objects, tables, columns, or RDTs not registered.

- An RDT name is not unique.

- A GeoRaster object is non-empty or nonblank, but an associated RDT does not exist.

After a database upgrade, you should do the following.

- Call the [SDO_GEOR_ADMIN.isGeoRasterEnabled](SDO_GEOR_ADMIN-reference.md) function to ensure that GeoRaster is enabled for the current schema.

- Call the [SDO_GEOR_ADMIN.isUpgradeNeeded](SDO_GEOR_ADMIN-reference.md) function to check for any invalid GeoRaster objects and invalid system data for the current version.

- If there are any errors or invalid data, call the [SDO_GEOR_ADMIN.upgradeGeoRaster](SDO_GEOR_ADMIN-reference.md) function to have the problems automatically corrected.

- If you connect as a user with DBA role, the [SDO_GEOR_ADMIN.upgradeGeoRaster](SDO_GEOR_ADMIN-reference.md) function upgrades all GeoRaster objects in the database; otherwise, it upgrades only GeoRaster objects in the schema of the current user. (See the reference and usage information about [SDO_GEOR_ADMIN.upgradeGeoRaster](SDO_GEOR_ADMIN-reference.md).

For regular maintenance due to possible user errors, several functions and procedures will be helpful in checking for and correcting invalid GeoRaster objects and system data entries:

- To check if GeoRaster is enabled, call [SDO_GEOR_ADMIN.isGeoRasterEnabled](SDO_GEOR_ADMIN-reference.md).

- To enable GeoRaster, call [SDO_GEOR_ADMIN.enableGeoRaster](SDO_GEOR_ADMIN-reference.md).

- To check for errors, call [SDO_GEOR_ADMIN.checkSysdataEntries](SDO_GEOR_ADMIN-reference.md) and [SDO_GEOR_ADMIN.listUnregisteredRDT](SDO_GEOR_ADMIN-reference.md).

- To check for dangling raster data, call [SDO_GEOR_ADMIN.listDanglingRasterData](SDO_GEOR_ADMIN-reference.md).

- To correct all invalid system data entries, call [SDO_GEOR_ADMIN.maintainSysdataEntries](SDO_GEOR_ADMIN-reference.md).

- To create correct DML triggers for all GeoRaster columns, call [SDO_GEOR_ADMIN.registerGeoRasterColumns](SDO_GEOR_ADMIN-reference.md).

- To register all existing GeoRaster objects in the sysdata table, call [SDO_GEOR_ADMIN.registerGeoRasterObjects](SDO_GEOR_ADMIN-reference.md).

See the reference and usage information about these procedures and functions in [SDO_GEOR_ADMIN Package Reference](SDO_GEOR_ADMIN-reference.md).

**Parent topic:** GeoRaster Database Creation and Management

### 3.16 Transferring GeoRaster Data Between Databases

GeoRaster data can be transferred between schemas in the same database or between databases. There are several ways to transfer the GeoRaster data:

- Using [GDAL](georaster-overview-and-concepts.md) or the [GeoRaster ETL tool](georaster-overview-and-concepts.md) to transport the GeoRaster data between schemas in the same database or between databases. In this approach, you export the rasters from the source GeoRaster table into an exchange file format, such as GeoTIFF, and then import them into the target schema or database.
- Using the [SDO_GEOR.copy](SDO_GEOR-reference.md) or [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedures to transfer GeoRaster data between schemas in the same database. The GeoRaster objects are copied from one schema to another directly, if access is granted.
- Using Data Pump Export and Import utilities to transfer GeoRaster data between schemas in the same database or between databases. See Using Data Pump Utility to Transfer GeoRaster Data for more information.
- Using Transportable Tablespaces to transfer GeoRaster data between databases. See Using Transportable Tablespaces To Transfer GeoRaster Data for more information.
- Using Oracle Database Link to transfer GeoRaster data between databases. See Using Database Link with GeoRaster Data for more information.

It is required that in any GeoRaster database, the name of each raster data table (RDT) must be unique and the pair of `(rasterDataTable, rasterID)` of a GeoRaster object must be unique in a database (see [Raster Data Table](georaster-overview-and-concepts.md)). So, when transferring GeoRaster data between databases using the Data Pump, the Transportable Tablespace, or Database Link approaches, conflicts of `rasterDataTable` name or `rasterID` in the target database might happen. Since changing the RDT name and making it unique will automatically make the pair of attributes `(rasterDataTable, rasterID)` unique, it is recommended to always resolve the conflicts by changing RDT names, as shown in the examples in the following subsections for each of these data transfer approaches. If a GeoRaster table with the same name already exists in the target database, it is also recommended to create a new GeoRaster table for the transferred GeoRaster objects in the target database instead of appending them to the existing GeoRaster table.

- Using Data Pump Utility to Transfer GeoRaster Data
- Using Transportable Tablespaces To Transfer GeoRaster Data
- Using Database Link with GeoRaster Data

**Parent topic:** GeoRaster Database Creation and Management

#### 3.16.1 Using Data Pump Utility to Transfer GeoRaster Data

Data Pump Utility can be used to transfer the GeoRaster data between schemas in the same database or between databases. The following instructions are for transferring GeoRaster data between databases. But, they also apply to GeoRaster data transfer between schemas. For information about the Data Pump Export and Import utilities and the original Export and Import utilities, see [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md).

To export GeoRaster data using Data Pump, do as you would for other types of data, but exclude the GeoRaster internal DML triggers (whose names start with `GRDMLTR_`) and the internal DDL triggers (named `SDO_GEOR_ADDL_TRIGGER` and `SDO_GEOR_BDDL_TRIGGER`). For example:

    expdp herman DIRECTORY=dump_dir DUMPFILE=data.dmp
    TABLES=herman.georaster_table,herman.rdt_1,herman.rdt_2
    PARFILE=exclude.par
    Enter password: password

In the preceding code, the `exclude.par` file contains the following:

    exclude=trigger:"like 'GRDMLTR_%'"
    exclude=trigger:"= 'SDO_GEOR_ADDL_TRIGGER'"
    exclude=trigger:"= 'SDO_GEOR_BDDL_TRIGGER'"

The following are the general steps to import GeoRaster data (that is, the GeoRaster tables and the associated raster data tables (RDTs)) into a target database using Data Pump:

1.  Ensure the target database schema is GeoRaster enabled. Follow the steps explained in Enabling GeoRaster at the Schema Level.
2.  Check if there is a conflict between the GeoRaster objects in the Data Pump dump file and the GeoRaster objects in the target database.
    1.  If the target database has no GeoRaster objects, then there is no conflict.
    2.  If the GeoRaster table names and RDT names in the dump file are known, use [SDO_GEOR_ADMIN.isRDTNameUnique](SDO_GEOR_ADMIN-reference.md) function in the target database to find out if there is RDT name conflict. For example:
            SELECT SDO_GEOR_ADMIN.isRDTNameUnique(<rdt_name>) FROM DUAL;

        In the preceding code, `<rdt_name>` is the name of the RDT in the dump file. If the query returns `‘FALSE’`, then there is RDT name conflict on `<rdt_name>`.
    3.  If the GeoRaster table names and RDT names in the dump file are not known, use `impdp` with the `SQLFILE` option to retrieve all the import DDL statements into a file. Get the GeoRaster table names and RDT names from the DDL statements in that file. For example:
            impdp scott DIRECTORY=dpump_dir DUMPFILE=data.dmp SQLFILE=dpump_dir:ddl.sql REMAP_SCHEMA=herman:scott

        In the preceding code, `ddl.sql` contains the DDL statements to be executed by `impdp`. Then for each RDT name in `ddl.sql`, use [SDO_GEOR_ADMIN.isRDTNameUnique](SDO_GEOR_ADMIN-reference.md) function in the target database to find out if there is RDT name conflict.
3.  Skip this step and go to step 4 if you detect a RDT name conflict in step 2 or if you intend to change the names of the imported RDT tables. Otherwise, import the GeoRaster tables and RDT tables as described in the following and validate the imported data. After this, you may skip step 4 as the GeoRaster data is already imported as required by the end of this step.
    Import GeoRaster data as you would for other types of data, but exclude the GeoRaster internal DML triggers (whose names start with `GRDMLTR_`) and DDL triggers (`SDO_GEOR_ADDL_TRIGGER` and `SDO_GEOR_BDDL_TRIGGER`) if you did not exclude them in the export operation. For example:

        impdp scott DIRECTORY=dpump_dir DUMPFILE=data.dmp PARFILE=exclude.par
         REMAP_SCHEMA=herman:scott TABLES=herman.georaster_table,herman.rdt_1,herman.rdt_2

    In the preceding code, the `exclude.par` file contains the following:

        exclude=trigger:"like 'GRDMLTR_%'"
        exclude=trigger:"= 'SDO_GEOR_ADDL_TRIGGER'"
        exclude=trigger:"= 'SDO_GEOR_BDDL_TRIGGER'"

    If you do not exclude the GeoRaster internal DML triggers and DDL triggers, some `impdp` errors such as the following will be raised. However, you can safely ignore the errors.

        ORA-39083: Object type TRIGGER failed to create with error:
        ORA-13391:  GeoRaster reserved names cannot be used to create regular triggers
4.  Resolve the conflicts and import GeoRaster data.
    1.  Import RDTs using `impdp` with `REMAP_TABLE` option to change the RDT names to new RDT names during the import (make sure the RDT names are unique across the target database). To make the data transfer easier and as a recommendation, the new RDT names can be constructed by appending a string and a number to the end of all old RDT names.
        For example:
            impdp scott DIRECTORY=dpump_dir DUMPFILE=data.dmp
            TABLES=herman.rdt_1,herman.rdt_2 REMAP_SCHEMA=herman:scott
            REMAP_TABLE=herman.rdt_1:rdt_1_imp_1, herman.rdt_2:rdt_2_imp_1

        In the preceding code, `rdt_1` is remapped to `rdt_1_imp_1`, and `rdt_2` is remapped to `rdt_2_imp_1`.
    2.  Import GeoRaster table metadata using `impdp` with `CONTENT=METADATA_ONLY` option and exclude the GeoRaster DML and DDL triggers as described in step 3.
        For example:
            impdp scott DIRECTORY=dpump_dir DUMPFILE=data.dmp TABLES=herman.georaster_table
            REMAP_SCHEMA=herman:scott CONTENT=metadata_only PARFILE=exclude.par

        If the GeoRaster table already exists in the target schema, it is recommended to use `REMAP_TABLE` option in the preceding code to remap the imported GeoRaster table name to a new name.
    3.  Login to the target database where the GeoRaster table metadata are imported and create a temporary DML trigger for each imported GeoRaster table, which will automatically replace the `rasterDataTable` attribute of the imported GeoRaster objects with the new RDT names during the data import in step d. The new RDT names must be the same as the new RDT names in step a.
        This is a sample DML trigger definition:
            DEFINE tname=georaster_table  -- the georaster table name
            DEFINE cname=grobj            -- the georaster column name
            DEFINE rdt_suffix=’IMP’       -- the string to append  to the RDT names
            DEFINE seq_num=1              -- the number to append  to the RDT names

            CREATE OR REPLACE TRIGGER tmp_dml_trigger
              BEFORE INSERT ON &tname
              FOR EACH ROW
              BEGIN
              -- the new RDT table name is constructed as the old RDT table name appended with
              -- the string defined in rdt_suffix and the sequence number defined in seq_num.
              :new.&cname.rasterDataTable := :new.&cname.rasterDataTable||’_&rdt_suffix’||’_’||’&seq_num’;
              END;
            /
    4.  Import GeoRaster table data using `impdp` with `CONTENT=DATA_ONLY` option. For example:
            impdp scott DIRECTORY=dpump_dir DUMPFILE=data.dmp
            TABLES=herman.georaster_table REMAP_SCHEMA=herman:scott CONTENT=data_only

        If you used the `REMAP_TABLE` option in step b, then include the option in the preceding code too.
    5.  Drop the temporary DML trigger created in step c. Validate and verify the imported data.

    The preceding examples transfer a GeoRaster table, `georaster_table`, and two RDTs, ` rdt_1` and `rdt_2`, from schema `HERMAN` in the source database to schema `SCOTT` in the target database. It assumes all GeoRaster objects in the `georaster_table` store their raster cell data in either `rdt_1` or `rdt_2` and these two RDTs are not used by any other GeoRaster tables.

**Parent topic:** Transferring GeoRaster Data Between Databases

#### 3.16.2 Using Transportable Tablespaces To Transfer GeoRaster Data

Oracle Database transportable tablespaces feature can be used to transfer GeoRaster data between databases. See [Transporting Tablespaces Between Databases](../admin/transporting-data.md) in Oracle Database Administrator’s Guidefor more information about using the transporting tablespaces feature with spatial data.

If a tablespace to be transported contains any spatial indexes on the GeoRaster tables or raster data tables (RDTs), you may have to take some preparatory steps. See the Usage Notes for the [SDO_UTIL.INITIALIZE_INDEXES_FOR_TTS](../spatl/SDO_UTIL-reference.md) procedure in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_UTIL-reference.md) for more information about using the transportable tablespace feature with spatial data.

The steps explained in the following sections enable you to use transportable tablespaces to transfer GeoRaster data between databases:

- Export the Tablespaces from the Source Database
- Import the Tablespaces into the Target Database

**Parent topic:** Transferring GeoRaster Data Between Databases

##### 3.16.2.1 Export the Tablespaces from the Source Database

To export the tablespaces from the source database for GeoRaster data migration, perform the following steps:

1.  Ensure the tablespaces to be transferred is self-contained. For example, run the following as DBA in SQL\*Plus:
        EXECUTE DBMS_TTS.TRANSPORT_SET_CHECK(‘tbs_1, tbs_2’, TRUE);
        SELECT * FROM TRANSPORT_SET_VIOLATIONS;

    In the preceding code, `tbs_1` and `tbs_2` are the names of the tablespaces to be transported.
2.  Make the tablespaces to be transported `READ ONLY`. For example, run the following as DBA in SQL\*Plus:
        ALTER TABLESPACE tbs_1 READ ONLY;
        ALTER TABLESPACE tbs_2 READ ONLY;
3.  Run Data Pump export utility as a user with `DATAPUMP_EXP_FULL_DATABASE` role. For example:
        $ expdp <user_name> DUMPFILE=tbs_meta.dmp DIRECTORY=data_pump_dir TRANSPORT_TABLESPACES=tbs_1,tbs_2 LOGFILE=tts_exp.log
4.  Transport the exported dump file from step 3 and tablespace data files to a directory that is accessible to the target database.
5.  Restore the tablespaces to `READ WRITE` mode.
        ALTER TABLESPACE tbs_1 READ WRITE;
        ALTER TABLESPACE tbs_2 READ WRITE;

**Parent topic:** Using Transportable Tablespaces To Transfer GeoRaster Data

##### 3.16.2.2 Import the Tablespaces into the Target Database

To import the tablespaces into the target database for GeoRaster data migration, perform the following steps:

1.  Ensure the target database schema is GeoRaster enabled. Follow the steps explained in Enabling GeoRaster at the Schema Level.
2.  Run the Data Pump import utility. For example:
        $ impdp <user_name> DIRECTORY=data_pump_dir DUMPFILE=tbs_meta.dmp
        LOGFILE=tts_imp.log TRANSPORT_DATAFILES='/app/oracle/oradata/tbs_1.dbf', ’/app/oracle/oradata/tbs_2.dbf’
        REMAP_SCHEMA=src_gruser1:target_gruser1 REMAP_SCHEMA=src_gruser2:target_gruser2 PARFILE=exclude.par

    In the preceding code, `<user_name>` is a user with `DATAPUMP_EXP_FULL_DATABASE` role.

    The `exclude.par` file contains the following:

        exclude=trigger:"like 'GRDMLTR_%'"
        exclude=trigger:"= 'SDO_GEOR_ADDL_TRIGGER'"
        exclude=trigger:"= 'SDO_GEOR_BDDL_TRIGGER'"

    If the GeoRaster table name already exists in the target database schema, use `REMAP_TABLE` option of the `impdp` command to remap the GeoRaster table name to a new name.
3.  Place the transported tablespaces into `READ WRITE` mode.
        ALTER TABLESPACE tbs_1 READ WRITE;
        ALTER TABLESPACE tbs_2 READ WRITE;
4.  Check if there are conflicts of RDT names in the target database.
    1.  Determine the GeoRaster tables and columns in the transported tablespaces by running the following query as DBA:
            SELECT t.owner, t.table_name, c.column_name
            FROM dba_all_tables t, dba_tab_columns c
            WHERE t.tablespace_name IN ('TBS_1', ‘TBS_2’)
                 AND t.owner = c.owner
                 AND t.table_name = c.table_name
                 AND c.data_type = 'SDO_GEORASTER'
                 AND c.data_type_owner IN ('MDSYS', 'PUBLIC');

        In the preceding code, `‘TBS_1’` and `‘TBS_2’` are the names of the transported tablespaces. This query returns a list of GeoRaster table and column names that are in the transported tablespaces.
    2.  Determine if there are RDT name conflicts.
            SELECT a.rdt_name
                        FROM ( SELECT UNIQUE t.<column_name>.rasterdatatable rdt_name
                                FROM <owner>.<table_name> t) a
                            WHERE SDO_GEOR_ADMIN.isRDTNameUnique(a.rdt_name)=’FALSE’;

        In the preceding code, `<owner>`, `<table_name>` and `<column_name>` are the names returned in step a.

        This query will return the conflicted RDT names in the transported tablespaces that need to be renamed.
5.  Skip this step and go to step 6 if there are no RDT name conflicts in step 4. Otherwise, resolve the conflicts in the target database by renaming the transported RDT.
    1.  Determine the DML trigger name (starts with `‘GRDMLTR_’`) on the transported GeoRaster table by querying `DBA_TRIGGERS` view.
            SELECT owner, trigger_name FROM dba_triggers WHERE table_owner = ‘<owner>’
            AND table_name = ‘<table_name>’ AND trigger_name LIKE 'GRDMLTR_%';

        In the preceding code, `<table_name>` and `<owner>` are the name and the owner of the GeoRaster table that has conflicted RDT name found in step 4.
    2.  Connect as DBA and disable the DML trigger returned in step a:
            ALTER TRIGGER <owner>.<TRIGGER_NAME> DISABLE;
    3.  Rename the conflicting RDT to a new name and update the `rasterDataTable` attribute of the GeoRaster objects in the GeoRaster table. Connect as the owner to the RDT in SQL\*Plus:
            RENAME <old_rdt> to <new_rdt>;
            UPDATE <table_name> t  SET t.<column_name>.rasterDataTable = ‘<new_rdt>’
            WHERE t.<column_name>.rasterDataTable=’<old_rdt>’;

        In the preceding code:

        - `<old_rdt>:` Old RDT name that conflicts
        - `<new_rdt>:` New RDT name that is unique in the target database
        - `<table_name>:` GeoRaster table name
        - `<column_name>:` GeoRaster column name associated with the conflicted RDT name returned in step 4

        Repeat this step for all conflicting RDTs.
    4.  Connect as DBA and enable the DML trigger that was disabled at step b.
            ALTER TRIGGER <owner>.<TRIGGER_NAME> ENABLE;
6.  If there are no conflicts or the conflicts have been resolved in step 5, call [SDO_GEOR_ADMIN.registerGeoRasterObjects](SDO_GEOR_ADMIN-reference.md) to register the transported GeoRaster object. For example run the following as DBA in SQL\*Plus:
        EXECUTE SDO_GEOR_ADMIN.registerGeoRasterObjects;

**Parent topic:** Using Transportable Tablespaces To Transfer GeoRaster Data

#### 3.16.3 Using Database Link with GeoRaster Data

From Oracle Database Release 12.2 onwards, database link can be used to transfer GeoRaster data from one database to another.

You can execute a SQL query through a database link to access remote GeoRaster object’s attributes and binary data in the raster data tables (RDTs). The GeoRaster data manipulations provided in the GeoRaster PL/SQL packages cannot be used on the remote GeoRaster objects through a database link.

**Note:**

You can check the interoperability support between different releases of the database in [Oracle Interoperability Support](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=148065162110635&id=207303.1&_afrWindowMode=0&_adf.ctrl-state=d9x9exsy1_4).

To transfer GeoRaster data through a database link:

1.  Ensure the target database schema is GeoRaster enabled. Follow the steps explained in Enabling GeoRaster at the Schema Level.

2.  Create the database link in the target database by executing the following SQL statement:

        CREATE PUBLIC DATABASE LINK <dblink name>
              CONNECT TO <username> IDENTIFIED BY <password>
              USING '<tnsname>';

    In the preceding code:

    - `<dblink name>:` Name of the database link
    - `<username>:` Username to connect to the source database schema where the GeoRaster table is located
    - `<password>:` Password for the source database user
    - `<tnsname>:` Source database connection name defined in the `tnsname.ora` in the target database

3.  Identify the GeoRaster table and RDT(s) to be transferred from the source database. Run the following query from the target database to get the RDTs associated with the GeoRaster objects in the GeoRaster table.

        SELECT UNIQUE t.<column_name>.rasterDataTable FROM <source_georaster_table>@<dblink_name> t;

    In the preceding code, `<column_name>` is the GeoRaster column name of` <source_georaster_table>` in the source database.

4.  Transfer the RDT data from the source database to the target database:

        CREATE TABLE <target_rdt_table> AS (SELECT * FROM <source_rdt_table>@<dblink_name>);

    The `<source_rdt_table>` in the preceding code is the RDT identified in step 3 (this example assumes that `<source_rdt_table>` only contains the raster data that is to be transferred). If `<source_rdt_table>` is unique in the target database (`SDO_GEOR_ADMIN.isRDTNameUnique(‘<source_rdt_table>’)` returns `true`), then `<target_rdt_table>` should be the same as `<source_rdt_table>`. Otherwise, choose a unique name for `<target_rdt_table>`.

5.  Transfer the GeoRaster objects in the GeoRaster table from the source database to the target database. A new GeoRaster table can be created in the target database as follows:

        CREATE TABLE <target_georaster_table> AS (SELECT * FROM <source_georaster_table>@<dblink_name>);

    If the name of the new RDT created in step 4 in the target database, `<target_rdt_table>`, is different from the RDT name in the source database, `<source_rdt_table>`, then the `rasterDataTable` attribute of the GeoRaster objects in the `<target_georaster_table>` needs to be updated as follows:
    1.  Connect as the schema user to find out the GeoRaster DML trigger name on the GeoRaster table:

            SELECT trigger_name FROM user_triggers WHERE table_name = ‘<target_georaster_table>’ AND trigger_name LIKE 'GRDMLTR_%';

        In the preceding code, `<target_georaster_table>` is the GeoRaster table name in the target database

    2.  Connect as DBA and disable the GeoRaster DML trigger:

            ALTER TRIGGER <owner>.<trigger_name> DISABLE;

    3.  Connect as the schema user and update the `rasterDataTable` attribute of the GeoRaster object:

            UPDATE <target_georaster_table> t  SET t.<column_name>.rasterDataTable = ‘<target_rdt_table>’
            WHERE t.<column_name>.rasterDataTable=’<source_rdt_table>’;

        In the preceding code, `<source_rdt_table>` and `<target_rdt_table>` are the table names used in step 4. `<column_name>` is the GeoRaster column name in the `<target_georaster_table>`.

    4.  Connect as DBA and enable the GeoRaster DML trigger:

            ALTER TRIGGER <owner>.<trigger_name> ENABLE;

6.  Connect as the schema user and register the transferred GeoRaster objects in the target database:

        EXECUTE SDO_GEOR_ADMIN.registerGeorasterObjects;

    Database link can also be used in the Data Pump import utility to transfer GeoRaster data directly from the source database to the target database. See Using Data Pump Utility to Transfer GeoRaster Data about how to use Data Pump import utility to transfer GeoRaster data.

**Parent topic:** Transferring GeoRaster Data Between Databases
