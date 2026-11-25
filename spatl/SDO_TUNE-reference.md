## 34  SDO_TUNE Package (Tuning)

The MDSYS.SDO_TUNE package contains subprograms for spatial tuning.

- SDO_TUNE.AVERAGE_MBR
- SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE
- SDO_TUNE.EXTENT_OF
- SDO_TUNE.MIX_INFO

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 34.1 SDO_TUNE.AVERAGE_MBR

#### Format

    SDO_TUNE.AVERAGE_MBR(
         table_name  IN VARCHAR2,
         column_name IN VARCHAR2,
         width       OUT NUMBER,
         height      OUT NUMBER);

#### Description

Calculates the average minimum bounding rectangle (MBR) for geometries in a layer.

#### Parameters

table_name
Spatial geometry table.

column_name
Geometry column for which the average minimum bounding rectangle is to be computed.

width
Width of the average minimum bounding rectangle.

height
Height of the average minimum bounding rectangle.

#### Usage Notes

This procedure computes and stores the width and height of the average minimum bounding rectangle for all geometries in a spatial geometry table. It calculates the average MBR by keeping track of the maximum and minimum X and Y values for all geometries in a spatial geometry table.

#### Examples

The following example calculates the minimum bounding rectangle for the SHAPE column of the COLA_MARKETS table.

    DECLARE
      table_name  VARCHAR2(32) := 'COLA_MARKETS';
      column_name  VARCHAR2(32) := 'SHAPE';
      width  NUMBER;
      height  NUMBER;
    BEGIN
    SDO_TUNE.AVERAGE_MBR(
      table_name,
      column_name,
      width,
      height);
    DBMS_OUTPUT.PUT_LINE('Width = ' || width);
    DBMS_OUTPUT.PUT_LINE('Height = ' || height);
    END;
    /
    Width = 3.5
    Height = 4.5

#### Related Topics

[SDO_AGGR_MBR](spatial-aggregate-functions.md) spatial aggregate function (in [Spatial Aggregate Functions](spatial-aggregate-functions.md))

**Parent topic:** SDO_TUNE Package (Tuning)

### 34.2 SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE

#### Format

    SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE(
         schemaname IN VARCHAR2,
         tabname    IN VARCHAR2,
         colname    IN VARCHAR2,
         partname   IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

or

    SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE(
         number_of_geoms IN INTEGER,
         db_block_size   IN INTEGER,
         sdo_rtr_pctfree IN INTEGER DEFAULT 10,
         num_dimensions  IN INTEGER DEFAULT 2,
         is_geodetic     IN INTEGER DEFAULT 0
         ) RETURN NUMBER;

#### Description

Estimates the maximum number of megabytes needed for an R-tree spatial index table.

#### Parameters

schemaname
Schema that owns the spatial geometry table.

tabname
Spatial geometry table name.

colname
Geometry column name.

partname
Name of a partition containing geometries from `colname`. If you specify this parameter, the value returned by the function is the estimated size for an R-tree index table on geometries in that partition. If you do not specify this parameter, the value is the estimated size for an R-tree index table on all geometries in `colname`.

number_of_geoms
Approximate number of geometries in the spatial geometry table.

db_block_size
Database block size (in bytes).

sdo_rtr_pctfree
Minimum percentage of slots in each index tree node to be left empty when the index is created. Slots that are left empty can be filled later when new data is inserted into the table. The value can range from 0 to 50. The default value (10) is best for most applications; however, a value of 0 is recommended if no updates will be performed to the geometry column.

num_dimensions
Number of dimensions to be indexed. The default value is 2. If you plan to specify the `sdo_indx_dims` parameter in the [CREATE INDEX](sql-indexing-spatial-data.md) statement, the `num_dimensions` value should match the `sdo_indx_dims` value.

is_geodetic
A value indicating whether or not the spatial index will be a geodetic index: 1 for a geodetic index, or 0 (the default) for a non-geodetic index.

#### Usage Notes

The function returns the estimated maximum number of megabytes needed for the spatial index table (described in [Spatial Index Table Definition](spatial-datatypes-metadata.md)) for an R-tree spatial index to be created. The value returned is the maximum number of megabytes needed after index creation. During index creation, approximately three times this value of megabytes will be needed in the tablespace, to ensure that there is enough space for temporary tables while the index is being created.

This function has two formats:

- Use the format with character string parameters (`schemaname`, `tabname`, `colname`, and optionally `partname`) in most cases when the spatial geometry table already exists, you do not plan to add substantially more geometries to it before creating the index, and you plan to use the default R-tree indexing parameters.

- Use the format with integer parameters (`number_of_geoms`, `db_block_size`, `sdo_rtr_pctfree`, `num_dimensions`, `is_geodetic`) in any of the following cases: the spatial geometry table does not exist; the spatial geometry table exists but you plan to add substantially more geometries to it before creating the index; or the `num_dimensions` value is not 2 for non-geodetic data or 3 for geodetic data, and a nondefault value will be specified using the `sdo_indx_dims` parameter in the [CREATE INDEX](sql-indexing-spatial-data.md) statement.

#### Examples

The following example estimates the maximum number of megabytes needed for a spatial index table for an index given the following information: `number_of_geoms` `= 1000000` (one million), `db_block_size`` = 2048`, `sdo_rtr_pctfree`` = 10`, `num_dimensions`` = 2`, `is_geodetic = 0`.

    SELECT SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE(1000000, 2048, 10, 2, 0) FROM DUAL;

    SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE(1000000,2048,10,2,0)
    -----------------------------------------------------
                                                       82

The following example estimates the maximum number of megabytes needed for a spatial index table for an index on the SHAPE column in the COLA_MARKETS table in the SCOTT schema. The estimate is based on the geometries that are currently in the table.

    SELECT SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE('SCOTT', 'COLA_MARKETS', 'SHAPE') FROM DUAL;

    SDO_TUNE.ESTIMATE_RTREE_INDEX_SIZE('SCOTT','COLA_MARKETS','SHAPE')
    ---------------------------------------------------------------------
                                                                        1

**Parent topic:** SDO_TUNE Package (Tuning)

### 34.3 SDO_TUNE.EXTENT_OF

#### Format

    SDO_TUNE.EXTENT_OF(
         table_name  IN VARCHAR2,
         column_name IN VARCHAR2,
         use_index   VARCHAR2 default 'TRUE'
         ) RETURN SDO_GEOMETRY;

#### Description

Returns the minimum bounding rectangle (MBR) of all geometries in a layer.

#### Parameters

table_name
Spatial geometry table, or a view based on a spatial geometry table.

column_name
Geometry column for which the minimum bounding rectangle is to be returned.

use_index
The string `TRUE` (the default) causes the spatial index (if one exists) on the table to be used in the computations. The string `FALSE` causes any spatial index to be ignored. (See the Usage Notes for more information about this parameter.)

#### Usage Notes

The [SDO_AGGR_MBR](spatial-aggregate-functions.md) function, documented in [Spatial Aggregate Functions](spatial-aggregate-functions.md), also returns the MBR of geometries. The SDO_TUNE.EXTENT_OF function has better performance than the [SDO_AGGR_MBR](spatial-aggregate-functions.md) function if a spatial index is defined on the geometry column; however, the SDO_TUNE.EXTENT_OF function is limited to two-dimensional geometries, whereas the [SDO_AGGR_MBR](spatial-aggregate-functions.md) function is not. In addition, the SDO_TUNE.EXTENT_OF function computes the extent for all geometries in a table; by contrast, the [SDO_AGGR_MBR](spatial-aggregate-functions.md) function can operate on subsets of rows.

If an R-tree spatial index is used, this function may return an approximate MBR that encloses the largest extent of data stored in the index, even if data was subsequently deleted.

The default value of `TRUE` for `use_index` is best in most cases, but in some cases you may want to specify `FALSE`. A spatial index can sometimes have the extent as larger than the actual data extent because DML operations might delete data around the edges, resulting in a smaller actual extent, although such deletions do not reduce the index extent. In such cases, if you want the actual data extent, specify `use_index=>'FALSE'`. Note, however, that specifying `FALSE` will have a significant negative impact on the performance of the function because it will require a full table scan.

#### Examples

The following example calculates the minimum bounding rectangle for the objects in the SHAPE column of the COLA_MARKETS table.

    SELECT SDO_TUNE.EXTENT_OF('COLA_MARKETS', 'SHAPE')
      FROM DUAL;

    SDO_TUNE.EXTENT_OF('COLA_MARKETS','SHAPE')(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y,
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARRAY(1, 1, 10, 11))

#### Related Topics

[SDO_AGGR_MBR](spatial-aggregate-functions.md) aggregate function (in [Spatial Aggregate Functions](spatial-aggregate-functions.md))

SDO_TUNE.AVERAGE_MBR procedure

**Parent topic:** SDO_TUNE Package (Tuning)

### 34.4 SDO_TUNE.MIX_INFO

#### Format

    SDO_TUNE.MIX_INFO(
         table_name    IN VARCHAR2,
         column_name   IN VARCHAR2
         [, total_geom OUT INTEGER,
         point_geom    OUT INTEGER,
         curve_geom    OUT INTEGER,
         poly_geom     OUT INTEGER,
         complex_geom  OUT INTEGER] );

#### Description

Calculates geometry type information for a spatial layer, such as the percentage of each geometry type.

#### Parameters

table_name
Spatial geometry table.

column_name
Geometry object column for which the geometry type information is to be calculated.

total_geom
Total number of geometry objects.

point_geom
Number of point geometry objects.

curve_geom
Number of curve string geometry objects.

poly_geom
Number of polygon geometry objects.

complex_geom
Number of complex geometry objects.

#### Usage Notes

This procedure calculates geometry type information for the table. It calculates the total number of geometries, as well as the number of point, curve string, polygon, and complex geometries.

#### Examples

The following example displays information about the mix of geometry objects in the SHAPE column of the COLA_MARKETS table.

    CALL SDO_TUNE.MIX_INFO('COLA_MARKETS',  'SHAPE');
    Total number of geometries: 4
    Point geometries:        0  (0%)
    Curvestring geometries:   0  (0%)
    Polygon geometries:      4  (100%)
    Complex geometries:      0  (0%)

**Parent topic:** SDO_TUNE Package (Tuning)
