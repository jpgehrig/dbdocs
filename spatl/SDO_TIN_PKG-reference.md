## 32  SDO_TIN_PKG Package (TINs)

The MDSYS.SDO_TIN_PKG package contains subprograms to support working with triangulated irregular networks (TINs).

**Note:**

SDO_TIN_PKG subprograms are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

To use the subprograms in this package, you must understand the main concepts related to three-dimensional geometries, including the use of triangulated irregular networks (TINs) to model surfaces. [Three-Dimensional Spatial Objects](spatial-concepts.md) describes support for three-dimensional geometries, [Modeling Surfaces](spatial-concepts.md) describes the use of TINs to model surfaces, and [TIN-Related Object Types](spatial-datatypes-metadata.md) describes data types related to TINs.

- SDO_TIN_PKG.CLIP_TIN
- SDO_TIN_PKG.CREATE_TIN
- SDO_TIN_PKG.DROP_DEPENDENCIES
- SDO_TIN_PKG.INIT
- SDO_TIN_PKG.PROJECT_ORDINATES_ONTO_TIN
- SDO_TIN_PKG.TO_DEM
- SDO_TIN_PKG.TO_GEOMETRY

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 32.1 SDO_TIN_PKG.CLIP_TIN

#### Format

    SDO_TIN_PKG.CLIP_TIN(
         inp         IN SDO_TIN,
         qry         IN SDO_GEOMETRY,
         qry_min_res IN NUMBER,
         qry_max_res IN NUMBER,
         blkid       IN NUMBER DEFAULT NULL
         ) RETURN SDO_TIN_BLK_TYPE;

#### Description

Performs a clip operation on a TIN.

#### Parameters

inp
TIN on which to perform the clip operation.

qry
Window from which to select objects to be returned; typically a polygon for two-dimensional geometries or a frustum for three-dimensional geometries.

qry_min_res
Minimum resolution value. Objects in `qry` with resolutions equal to or greater than `qry_min_res` and less than or equal to `qry_max_res` are returned by the clip operation.

qry_max_res
Maximum resolution value. Objects in `qry` with resolutions equal to or greater than `qry_min_res` and less than or equal to `qry_max_res` are returned by the clip operation.

blkid
Block ID number of the block to which to restrict the objects returned by the clip operation. If this parameter is null, all objects that satisfy the other parameters are returned.

#### Usage Notes

This function returns triangles from a TIN that are within a specified query window and that satisfy any other requirements specified by the parameters. A common use of this function is to perform queries on TINs. You can maximize the performance of a TIN query by minimizing the number of objects that the function needs to consider for the operation.

The SDO_TIN and SDO_TIN_BLK_TYPE data types are described in [TIN-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

#### Examples

The following example performs a clip operation on a TIN. It is taken from the `$ORACLE_HOME/md/demo/TIN/examples/plsql/tin.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    declare
      inp  sdo_tin;
    begin
      select tin INTO inp  from base where rownum=1;
      insert into restst
      select * from
        table(sdo_tin_pkg.clip_tin
               (
                inp,  -- Input TIN object
                sdo_geometry(2003, null, null,
                  mdsys.sdo_elem_info_array(1, 1003, 3),
                  mdsys.sdo_ordinate_array(-74.1, -73.9, 39.99999,40.00001)), -- Query
                null, null));
    end;
    . . .

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.2 SDO_TIN_PKG.CREATE_TIN

#### Format

    SDO_TIN_PKG.CREATE_TIN(
         inp           IN SDO_TIN,
         inptable      IN VARCHAR2,
         clstPcdataTbl IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a TIN using the points specified in the `inptable` parameter.

#### Parameters

inp
SDO_TIN object to be used. This object must have been created by the SDO_TIN_PKG.INIT function

inptable
Name of the table or view containing the input TIN data. This table or view should have the following columns:

- RID (VARCHAR2(24)): Unique ID for each point

- VAL_D1 (NUMBER): Ordinate in dimension 1

- VAL_D2 (NUMBER): Ordinate in dimension 2

- . . .

- VAL_Dn (NUMBER): Ordinate in dimension n, where n is the highest-numbered dimension. n should match the `tin_tot_dimensions` parameter value in the call to the SDO_TIN_PKG.INIT function when the TIN was initialized.

clstPcdataTbl
Name of the table for storing the resulting point data. If you do not specify a value, this table is not created. For more information about the table, see the Usage Notes.

#### Usage Notes

The first few dimensions of the TIN are indexed and can later be searched using the SDO_TIN_PKG.CLIP_TIN function. The exact number of dimensions to index is determined by the dimensionality of the TIN extent in the initialized TIN object, specifically: `inp.tin_extent.sdo_gtype/1000`

If you specify a view name in the `inptable` parameter, the query `SELECT ROWID FROM <view-name>` must not return any errors.

If you specify a table name in the `clstPcdataTbl` parameter, the table must exist and have the following columns:

- PTN_ID (NUMBER)

- POINT_ID (NUMBER)

- RID (VARCHAR2(24): Unique ID for each point

- VAL_D1 (NUMBER): Ordinate in dimension 1

- VAL_D2 (NUMBER): Ordinate in dimension 2

- . . .

- VAL_Dn (NUMBER): Ordinate in dimension n, where n is the highest-numbered dimension. n should match the `tin_tot_dimensions` parameter value in the call to the SDO_TIN_PKG.INIT function when the TIN was initialized.

If a value is specified for the `clstPcdataTbl` parameter, this function populates the table by assigning appropriate values for PTN_ID and POINT_ID and by copying the values from the `inptable` table or view for other attributes. This table can be created as an index organized table. It can be used in applications for searching using SQL queries on dimensions other than those reflected in the index dimensionality. (For an explanation of index dimensionality and total dimensionality, see the explanation of the `tin_tot_dimensions` parameter of the SDO_TIN_PKG.INIT function.)

The SDO_TIN data type is described in [TIN-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

#### Examples

The following example creates a TIN. It is taken from the `$ORACLE_HOME/md/demo/TIN/examples/plsql/tin.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    -- Create the blocks for the TIN.
    sdo_tin_pkg.create_tin(
      tin,       -- Initialized TIN object
      'INPTAB', -- Name of input table to ingest into the pointcloud
      'RES'     -- Name of output table that stores the points (with ptn_id,pt_id)
    );
    /
    . . .

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.3 SDO_TIN_PKG.DROP_DEPENDENCIES

#### Format

    SDO_TIN_PKG.DROP_DEPENDENCIES(
         basetable IN VARCHAR2,
         col       IN VARCHAR2);

#### Description

Drops the dependencies between a TIN block table and a specified base table and column.

#### Parameters

basetable
Name of a base table that was specified (in the `basetable` parameter of the SDO_TIN_PKG.INIT function) when the TIN was initialized.

col
Name of a column in base table that was specified in the `basecol` parameter of the SDO_TIN_PKG.INIT function.

#### Usage Notes

This procedure truncates the TIN block table and removes the association between the block table and the base table and column combination.

After you execute this procedure, you can drop the TIN block table or associate the table with another base table and column combination. For more information, see the Usage Notes for the SDO_TIN_PKG.INIT function.

#### Examples

The following example drops the dependencies between a TIN block table and a base table and column named BASE and TIN, respectively.

    . . .
    declare
    begin
      mdsys.sdo_tin_pkg.drop_dependencies('BASE', 'TIN');
    end;
    /

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.4 SDO_TIN_PKG.INIT

#### Format

    SDO_TIN_PKG.INIT(
         basetable           IN VARCHAR2,
         basecol             IN VARCHAR2,
         blktable            IN VARCHAR2,
         ptn_params          IN VARCHAR2,
         tin_extent          IN SDO_GEOMETRY,
         tin_tol             IN NUMBER DEFAULT 0.000000000000005,
         tin_tot_dimensions  IN NUMBER DEFAULT 2,
         tin_domain          IN SDO_ORGSCL_TYPE DEFAULT NULL,
         tin_break_lines     IN SDO_GEOMETRY DEFAULT NULL,
         tin_stop_lines      IN SDO_GEOMETRY DEFAULT NULL,
         tin_void_rgns       IN SDO_GEOMETRY DEFAULT NULL,
         tin_val_attr_tables IN SDO_STRING_ARRAY DEFAULT NULL,
         tin_other_attrs     IN XMLTYPE DEFAULT NULL,
         ) RETURN SDO_TIN;

#### Description

Initializes a TIN by creating an SDO_TIN object.

#### Parameters

basetable
Name of the base table containing a column of type SDO_TIN.

basecol
Name of the column of type SDO_TIN in the base table.

blktable
Name of the TIN block table, which is used for storing the blocks of the TIN. This table must exist, and must have been created by a statement in the following form: `CREATE TABLE <table-name> AS select * from mdsys.sdo_tin_blk_table;`

Each TIN block table can only be associated with only one `basetable` and `basecol` combination.

ptn_params
Parameters for partitioning the TIN, specified as a quoted string with keywords delimited by commas. For example: '`blk_capacity=1000,work_tablespace=my_work_ts'`. If this parameter is null, the TIN is not partitioned. The following keywords are permitted:

- `blk_capacity=n`, where n is the maximum number of rows in each partition. The default value is 5000. If specified, must be a number greater than or equal to 50.

- `work_tablespace=x`, where x is the name of the tablespace in which to create temporary tables during the partitioning operations.

tin_extent
SDO_GEOMETRY object representing the spatial extent of the TIN (the minimum bounding object enclosing all objects in the TIN. This parameter must not be null.

For geodetic data, this geometry must have two dimensions; otherwise, it can have up to four dimensions. The dimensionality of this geometry is used as the minimum value permitted for the `tin_tot_dimensions` parameter, as explained in the description of that parameter.

tin_tol
Tolerance value for objects in the TIN. (For information about spatial tolerance, see Section 1.5.5.) If this parameter is null, the default value is 0.0000000000005.

tin_tot_dimensions
A number specifying the total dimensionality of the TIN object. For each point in the TIN blocks, `tin_tot_dimensions` ordinates (values) are stored.

The total dimensionality must be greater than or equal to the index dimensionality, which is the number of dimensions in the `tin_extent` geometry. Specifying total dimensionality greater than index dimensionality enables necessary nonspatial attributes to be retrieved in the same fetch operation with spatial data. The maximum total dimensionality value is 8. The default value for this parameter is 2.

tin_domain
(Not currently used.)

tin_break_lines
(Not currently used.)

tin_stop_lines
(Not currently used.)

tin_void_rgns
(Not currently used.)

tin_val_attr_tables
SDO_STRING_ARRAY object specifying the names of any value attribute tables for the TIN. If this parameter is null, the TIN has no associated value attribute tables. Type SDO_STRING_ARRAY is defined as VARRAY(1048576) OF VARCHAR2(32).

tin_other_attrs
XMLTYPE object specifying any other attributes of the TIN. If this parameter is null, the TIN has no other attributes.

This parameter can include metadata on TIN pyramiding, as explained in the Usage Notes.

#### Usage Notes

After you use this function to initialize an SDO_TIN object, you can create a TIN by specifying this object as input to the SDO_TIN_PKG.CREATE_TIN procedure.

The SDO_TIN data type is described in [TIN-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

The `tin_other_attrs` parameter can be used to specify metadata for TIN pyramiding, for example:

    xmltype(
     '<opc:sdoTinObjectMetadata
              xmlns:opc="http://xmlns.oracle.com/spatial/vis3d/2011/sdovis3d.xsd"
              xmlns:las="http://liblas.org/schemas/LAS/1.0"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <opc:sdoTinPyramid/>
            </opc:sdoTinObjectMetadata>')

TIN pyramiding creates multiple pyramid levels from level 1 (most detailed) to level n (least detailed). In contrast to point cloud pyramiding (described in the Usage Notes for [SDO_PC_PKG.INIT](SDO_PC_PKG-reference.md)), there is no option relating to preserving level 1 with TIN pyramiding. A TIN with pyramiding will require more storage space than one without pyramiding, because level 1 is basically equal to the TIN without pyramiding, and all other levels require additional space.

#### Examples

The following example initializes a TIN by creating an SDO_TIN object. It is taken from the `$ORACLE_HOME/md/demo/TIN/examples/plsql/tin.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    declare
      tin sdo_tin;
    begin
      -- Initialize the TIN object.
      tin := sdo_tin_pkg.init(
              'BASE', -- Table that has the SDO_TIN column defined
              'TIN',   -- Column name of the SDO_TIN object
              'BLKTAB', -- Table to store blocks of the TIN
               'blk_capacity=1000', -- max # of points per block
               mdsys.sdo_geometry(2003, null, null,
                  mdsys.sdo_elem_info_array(1,1003,3),
                  mdsys.sdo_ordinate_array(-180, -90, 180, 90)),  -- Extent
                  0.0000000005, -- Tolerance for TIN
                  3, -- Total number of dimensions
                  null);
    . . .

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.5 SDO_TIN_PKG.PROJECT_ORDINATES_ONTO_TIN

#### Format

    SDO_TIN_PKG.PROJECT_ORDINATES_ONTO_TIN(
         ordinates2D SDO_ORDINATE_ARRAY,
         tin         SDO_TIN
         ) RETURN SDO_ORDINATE_ARRAY;

#### Description

Projects two-dimensional points onto a TIN, thereby determining point heights.

#### Parameters

ordinates2D
SDO_ORDINATE_ARRAY object with the two-dimensional points to be projected. These cannot be oriented points (which are described in [Oriented Point](spatial-datatypes-metadata.md)).

tin
SDO_TIN object onto which to project the points.

#### Usage Notes

This function can be thought of as performing height interpolation for the specified two-dimensional input points.

The SDO_TIN data type is described in [TIN-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

#### Examples

The following example projects two-dimensional points (2.3, 3.4), (4.5, 5.6), (6.7, 7.8) onto a TIN, yielding three-dimensional points (2.3, 3.4, 5.7), (4.5, 5.6, 10.1), (6.7, 7.8, 14.5). In this example, the TIN shape is an inclined surface with `zi=xi+yi`.

    SELECT
      sdo_tin_pkg.project_ordinates_onto_tin(
        ordinates2d => sdo_ordinate_array(
          2.3,  3.4,
          4.5,  5.6,
          6.7,  7.8),
        tin => (select tin from tins where tin_id = 1))
    FROM DUAL;

    SDO_TIN_PKG.PROJECT_ORDINATES_ONTO_TIN(ORDINATES2D=>SDO_ORDINATE_ARRAY(2.3,3.4,4
    --------------------------------------------------------------------------------
    SDO_ORDINATE_ARRAY(2.3, 3.4, 5.7, 4.5, 5.6, 10.1, 6.7, 7.8, 14.5)

    1 row selected.

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.6 SDO_TIN_PKG.TO_DEM

#### Format

    SDO_TIN_PKG.TO_DEM(
         tin                 IN SDO_TIN,
         dem                 IN OUT SDO_GEORASTER,
         blocksize           IN NUMBER,
         crs_units_per_pixel IN NUMBER);

#### Description

Creates a DEM (Digital Elevation Model) GeoRaster object from a TIN.

#### Parameters

tin
TIN object. (The SDO_TIN data type is described in [TIN-Related Object Types](spatial-datatypes-metadata.md).)

dem
DEM GeoRaster object. (The SDO_GEORASTER data type is described in [Oracle Spatial and Graph GeoRaster Developer's Guide](../geors/georaster-datatypes.md).)

blocksize
Pixel block size for the DEM.

crs_units_per_pixel
TIN and DEM coordinate reference system (SRID) units for each pixel. For example, if the SRID unit of measure is decimal degree and if each pixel represents 1/100 of a degree, the `crs_units_per_pixel` value is `0.01`.

#### Usage Notes

This procedure modifies the specified GeoRaster object (`dem` parameter) based on information in the input TIN.

The TIN and the DEM must have the same coordinate reference system (SRID).

For the `dem` parameter, the input SDO_GEORASTER object can be obtained by inserting a GeoRaster object into a table and returning the GeoRaster object into a variable; for example:

    INSERT INTO raster_table VALUES (1, sdo_geor.init('raster_data_table'))
       RETURNING raster_image INTO geor;

To determine the horizontal extent in pixels of the DEM, divide the horizontal extent in SRID units by the `crs_units_per_pixel` parameter value. For example, assume the following:

- The TIN and DEM SRID is 4326.

- The SRID unit is decimal degrees.

- The input TIN has a horizontal extent of 7 decimal degrees.

- The `crs_units_per_pixel` value is `0.01`.

In this example, the DEM horizontal extent is 700 pixels (7/.01 = 700).

The SDO_TIN data type is described in [TIN-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

#### Examples

The following example creates a DEM from a TIN. It is taken from the `$ORACLE_HOME/md/demo/TIN/examples/plsql/tin.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    create table raster_table (id number, raster_image sdo_georaster);

    create table raster_data_table of sdo_raster
      (primary key (rasterId, pyramidLevel, bandBlockNumber, rowBlockNumber, columnBlockNumber))
      lob(rasterblock) store as (nocache nologging);

    DECLARE
      inp sdo_tin;
      geor sdo_georaster;
    BEGIN
      select tin INTO inp from tins_hawaii_4326 where rownum=1;
      insert into raster_table values (1, sdo_geor.init('raster_data_table')) returning raster_image into geor;
      sdo_tin_pkg.to_dem(
        tin                 => inp,
        dem                 => geor,
        blocksize           => 128,
        crs_units_per_pixel => 0.01);
      update raster_table set raster_image = geor where id = 1;
    END;
    /

**Parent topic:** SDO_TIN_PKG Package (TINs)

### 32.7 SDO_TIN_PKG.TO_GEOMETRY

#### Format

    SDO_TIN_PKG.TO_GEOMETRY(
         pts         IN BLOB,
         trs         IN BLOB,
         num_pts     IN NUMBER,
         num_trs     IN NUMBER,
         tin_ind_dim IN NUMBER,
         tin_tot_dim IN NUMBER,
         srid        IN NUMBER DEFAULT NULL,
         blk_domain  IN SDO_ORGSCL_TYPE DEFAULT NULL,
         get_ids     IN NUMBER DEFAULT NULL
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object representing all or part of a TIN.

#### Parameters

pts
BLOB containing points.

trs
BLOB containing triangles.

num_pts
Maximum number of points to be included in the resulting geometry.

num_pts
Maximum number of triangles to be included in the resulting geometry.

tin_ind_dim
Number of spatial dimensions that are indexed.

tin_tot_dim
Number of spatial dimensions defined for the data.

srid
Spatial reference (coordinate system) ID associated with the data. If this parameter is null, no SRID value is associated with the data.

blk_domain
(Not currently used.)

get_ids
Null or 0 (the default) does not include the block ID and point ID for each point in the returned geometry; 1 includes the block ID and point ID for each point in the returned geometry. If `get_ids` is 1, each point in the returned geometry has its spatial dimensions and two additional dimensions. For example: (x, y, z, blk_id, pt_id).

#### Usage Notes

This function returns a single collection SDO_GEOMETRY object that represents all point geometries in the `pts` parameter and all triangle geometries in the `trs` parameter. For example, the points and triangles could reflect the result of a clip operation or the contents of an entire block.

[Modeling Surfaces](spatial-concepts.md) describes how to use TINs to model surfaces.

#### Examples

The following example returns a multipoint collection geometry object representing a TIN. It is taken from the `$ORACLE_HOME/md/demo/TIN/examples/plsql/tin.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    -- Return points in blk_id of the TIN as a multipoint collection.
    select sdo_tin_pkg.to_geometry(
                        a.points,   -- point LOB
                        a.triangles,   -- point LOB
                        a.num_points, -- # of points in the LOB
                        a.num_triangles, -- # of points in the LOB
                        2,  -- index dimensionality (gtype dim in extent in INIT)
                        3,  -- total dimensionality
                        null -- SRID
                        ) from blktab a where blk_id=0;
    . . .

**Parent topic:** SDO_TIN_PKG Package (TINs)
