## 30  SDO_PC_PKG Package (Point Clouds)

The MDSYS.SDO_PC_PKG package contains subprograms to support working with point clouds.

To use the subprograms in this package, you must understand the main concepts related to three-dimensional geometries, including the use of point clouds to model solids. [Three-Dimensional Spatial Objects](spatial-concepts.md) describes support for three-dimensional geometries, [Modeling Solids](spatial-concepts.md) describes the use of point clouds to model solids, and [Point Cloud-Related Object Types](spatial-datatypes-metadata.md) describes data types related to point clouds.

**Note:**

SDO_PC_PKG subprograms are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

- SDO_PC_PKG.CLIP_PC
- SDO_PC_PKG.CLIP_PC_FLAT
- SDO_PC_PKG.CLIP_PC_FLAT_STRING
- SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES
- SDO_PC_PKG.CREATE_PC
- SDO_PC_PKG.DROP_DEPENDENCIES
- SDO_PC_PKG.GET_PT_IDS
- SDO_PC_PKG.HAS_PYRAMID
- SDO_PC_PKG.INIT
- SDO_PC_PKG.PC2DEM
- SDO_PC_PKG.PRESERVES_LEVEL1
- SDO_PC_PKG.SDO_PC_NN
- SDO_PC_PKG.SDO_PC_NN_FOR_EACH
- SDO_PC_PKG.TO_GEOMETRY

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 30.1 SDO_PC_PKG.CLIP_PC

#### Format

    SDO_PC_PKG.CLIP_PC(
         inp           IN SDO_PC,
         ind_dim_qry   IN SDO_GEOMETRY,
         other_dim_qry IN SDO_MBR,
         qry_min_res   IN NUMBER,
         qry_max_res   IN NUMBER,
         blkno         IN NUMBER DEFAULT NULL,
         include_custom_dims IN NUMBER DEFAULT 0
         ) RETURN SDO_PC_BLK_TYPE;

#### Description

Performs a clip operation on a point cloud.

#### Parameters

inp
Point cloud on which to perform the clip operation.

ind_dimqry
For querying the indexed dimensions of the point cloud: window from which to select objects to be returned; typically a polygon for two-dimensional geometries or a frustum for three-dimensional geometries.

other_dimqry
For querying the nonindexed dimensions of the point cloud: window from which to select objects to be returned; typically a polygon for two-dimensional geometries or a frustum for three-dimensional geometries. The nonindexed dimensions are those that are included in the total dimensionality but are not indexed. For an explanation of index dimensionality and total dimensionality, see the explanation of the `pc_tot_dimensions` parameter of the SDO_PC_PKG.INIT function.

The SDO_MBR type is defined as `(LOWER_LEFT SDO_VPOINT_TYPE, UPPER_RIGHT SDO_VPOINT_TYPE)` and SDO_V_POINT_TYPE is defined as V`ARRAY(64) OF NUMBER`.

qry_min_res
Minimum resolution value. Objects in `qry` with resolutions equal to or greater than `qry_min_res` and less than or equal to `qry_max_res` are returned by the clip operation.

qry_max_res
Maximum resolution value. Objects in `qry` with resolutions equal to or greater than `qry_min_res` and less than or equal to `qry_max_res` are returned by the clip operation.

blkid
Block ID number of the block to which to restrict the objects returned by the clip operation. If this parameter is null, all objects that satisfy the other parameters are returned.

include_custom_dims
Numeric value 0 or 1, which determines whether the point cloud blocks returned by the function contain only the regular (type NUMBER) dimensions, as included in the PC_TOT_DIMENSIONS count of SDO_PC. If only these regular dimensions should be returned, then `include_custom_dims=0` (the default). The stored point cloud blocks in the block table still contain any additional custom dimensions, but this individual CLIP_PC query then does not return them.

`include_custom_dims=1` includes both regular and custom dimensions.

See the Usage Notes for more information about custom dimensions.

#### Usage Notes

This function returns points from a point cloud that are within a specified query window and that satisfy any other requirements specified by the parameters. A common use of this function is to perform queries on point clouds. You can maximize the performance of a point cloud query by minimizing the number of objects that the function needs to consider for the operation.

The SDO_PC and SDO_PC_BLK_TYPE data types are described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).

This function supports the storage and querying of custom dimensions. Custom dimensions can be of type NUMBER or other types, and they are not included in the PC_TOT_DIMENSIONS count of SDO_PC. If `include_custom_dims=1`, the custom dimensions can be part of a query result, but they cannot be part of the query restriction, either in the `ind_dimqry` or `other_dimqry` parameters, because custom dimensions might not be of numeric type (and thus cannot be represented in the numeric interface of `ind_dimqry` or `other_dimqry`).

Custom dimensions cannot be created using the SDO_PC_PKG.CREATE_PC procedure.

Contrast this function with SDO_PC_PKG.CLIP_PC_FLAT, which takes as input point cloud data stored in a flat table (as opposed to an SDO_PC object).

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example performs a clip operation on a point cloud. It is taken from the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    declare
      inp  sdo_pc;
    begin
      select pc INTO inp  from base where rownum=1;
      insert into restst
        select * from
          table(sdo_pc_pkg.clip_pc
               (
                inp,  -- Input point cloud object
                sdo_geometry(2003, 8307, null,
                  sdo_elem_info_array(1, 1003, 3),
                  sdo_ordinate_array(-175.86157, -14.60521, 0,0)), -- Query
                  null, null, null));
    end;
    /
    . . .

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.2 SDO_PC_PKG.CLIP_PC_FLAT

#### Format

    SDO_PC_PKG.CLIP_PC_FLAT(
         geometry       IN SDO_GEOMETRY,
         table_name     IN VARCHAR2,
         tolerance      IN NUMBER,
         other_dim_qry  IN SDO_MBR,
         mask           IN VARCHAR2 DEFAULT NULL
         ) RETURN REF CURSOR;

#### Description

Performs a clip operation on a flat-format point cloud, in which the point cloud data is stored in a flat table.

#### Parameters

geometry
Two-dimensional geometry to serve as the clip window. For example:

    geometry =>
      SDO_GEOMETRY(
        2003,
        NULL,
        NULL,
        SDO_ELEM_INFO_ARRAY(1, 1003, 3),
        SDO_ORDINATE_ARRAY(
          0.75, 0.75,
          1.25, 1.25))

table_name
Name of the table or view containing the point cloud data. The first two columns in the table or view must be named X and Y and be of type Oracle NUMBER. Optionally, following X and Y, the table or view can contain a Z column of type NUMBER, and additional nonspatial point cloud attributes. The additional nonspatial point cloud attributes can be any data type, but must be type Oracle NUMBER if they will participate as constraints in the `other_dim_qry` parameter.

tolerance
Tolerance value for objects in the point cloud (see [Tolerance](spatial-concepts.md) for information about spatial tolerance). If this parameter is null, the default value is 0.0000000000005

other_dim_qry
Minimum bounding rectangle (MBR) to provide a user defined query ranges for any Oracle NUMBER type columns (not including the X and Y columns).

The SDO_MBR type is defined as `(LOWER_LEFT SDO_VPOINT_TYPE, UPPER_RIGHT SDO_VPOINT_TYPE)` and SDO_V_POINT_TYPE is defined as V`ARRAY(64) OF NUMBER`.

Specify NULL in the SDO_V_POINT_TYPE array for Oracle NUMBER type columns that are not constrained by a query range.

mask
The topological relationship of interest, as applicable to points interacting with polygons. Valid values are `'mask=``<value>``'` where `<value>` is one or more of the mask values valid for the [SDO_RELATE](spatial-operators-reference.md) operator (`TOUCH`, `OVERLAPBDYDISJOINT`, `OVERLAPBDYINTERSECT`, `EQUAL`, `INSIDE`, `COVEREDBY`, `CONTAINS`, `COVERS`, `ANYINTERACT`, `ON`), or `FILTER`, which performs an approximate check. `FILTER` will return all the candidates that intersect the polygon, and possibly a few more. Multiple masks are combined with the logical Boolean operator `OR` (for example, `'mask=inside+touch'`); however, `FILTER` cannot be combined with any other mask.

If this parameter is null or contains an empty string, `mask=ANYINTERACT` is assumed.

#### Usage Notes

This function works with flat-format point clouds, in contrast to SDO_PC_PKG.CLIP_PC, which works with input point cloud data stored in an SDO_PC object. The flat format has been added to point cloud support to offer an alternative to SDO_PC, depending on hardware environment and usage patterns. One advantage of the flat format is its dynamic nature, since updates to the point data do not require reblocking.

In environments other than Exadata, it is highly recommended that you create a compound B-tree index on the X, Y columns. In the compound B-tree index, also include any other Oracle NUMBER columns that will constrained with user-defined query ranges described for the `other_dim_qry` parameter. Any point cloud data update will result in an automatic update of that B-tree index.

Contrast this function with SDO_PC_PKG.CLIP_PC, which takes as input point cloud data stored in an SDO_PC object.

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids. It includes some discussion of the SDO_PC and flat table approaches for storing point cloud data.

#### Examples

The following example creates a view named INPTAB2 from the first three columns of a table named INPPTAB. It then performs a clip operation on the point cloud date.

    CREATE VIEW inptab2 AS (select x x, y y, z z from inptab);

    DECLARE
      my_cursor sys_refcursor;
      TYPE rec IS RECORD(x NUMBER, y NUMBER, z number);
      TYPE lst IS TABLE OF rec;
      result_list lst;
    BEGIN
      my_cursor :=
        SDO_PC_PKG.CLIP_PC_FLAT(
          geometry =>
            MDSYS.SDO_GEOMETRY(
              2003,
              NULL,
              NULL,
              MDSYS.SDO_ELEM_INFO_ARRAY(1, 1003, 3),
              MDSYS.SDO_ORDINATE_ARRAY(
                0.75, 0.75,
                1.25, 1.25)),
          table_name    => 'INPTAB2',
          tolerance     => 0.05,
          other_dim_qry => null,
          mask          => null);

      FETCH my_cursor BULK COLLECT INTO result_list;
      FOR I in 1 .. result_list.COUNT LOOP
        dbms_output.put_line(
          '(' || result_list(i).x || ', ' ||
                 result_list(i).y || ', ' ||
                 result_list(i).z || ')');
      END LOOP;
      CLOSE my_cursor;
    END;
    /

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.3 SDO_PC_PKG.CLIP_PC_FLAT_STRING

#### Format

    SDO_PC_PKG.CLIP_PC_FLAT_STRING(
         geometry       IN SDO_GEOMETRY,
         table_name     IN VARCHAR2,
         tolerance      IN NUMBER,
         other_dim_qry  IN SDO_MBR,
         mask           IN VARCHAR2 DEFAULT NULL,
         dop            IN NUMBER DEFAULT NULL,
         sdo_level      IN NUMBER DEFAULT 4,
         sdo_ntiles     IN NUMBER DEFAULT 100
         ) RETURN CLOB;

#### Description

Generates a SQL query string to perform a clip operation on a flat-format point cloud, in which the point cloud data is stored in a flat table. The query is not executed, but merely generated for either subsequent execution or inspection.

#### Parameters

geometry
Two-dimensional geometry to serve as the clip window. For example:

    geometry =>
      SDO_GEOMETRY(
        2003,
        NULL,
        NULL,
        SDO_ELEM_INFO_ARRAY(1, 1003, 3),
        SDO_ORDINATE_ARRAY(
          0.75, 0.75,
          1.25, 1.25))

table_name
Name of the table or view containing the point cloud data. The first two columns in the table or view must be named X and Y and be of type Oracle NUMBER. Optionally, following X and Y, the table or view can contain a Z column of type NUMBER, and additional nonspatial point cloud attributes. The additional nonspatial point cloud attributes can be any data type, but must be type Oracle NUMBER if they will participate as constraints in the `other_dim_qry` parameter.

tolerance
Tolerance value for objects in the point cloud (see [Tolerance](spatial-concepts.md) for information about spatial tolerance). If this parameter is null, the default value is 0.0000000000005

other_dim_qry
Minimum bounding rectangle (MBR) to provide a user defined query ranges for any Oracle NUMBER type columns (not including the X and Y columns).

The SDO_MBR type is defined as `(LOWER_LEFT SDO_VPOINT_TYPE, UPPER_RIGHT SDO_VPOINT_TYPE)` and SDO_V_POINT_TYPE is defined as V`ARRAY(64) OF NUMBER`.

Specify NULL in the SDO_V_POINT_TYPE array for Oracle NUMBER type columns that are not constrained by a query range.

As an example:

    other_dim_qry => MDSYS.SDO_MBR(
                       SDO_VPOINT_TYPE(10, 81),
                       SDO_VPOINT_TYPE(11, 82))

means that the third value (x and y being first and second) is between 10 and 11. The fourth value should be between 81 and 82.

mask
The topological relationship of interest, as applicable to points interacting with polygons. Valid values are `'mask=``<value>``'` where `<value>` is one or more of the mask values valid for the [SDO_RELATE](spatial-operators-reference.md) operator (`TOUCH`, `OVERLAPBDYDISJOINT`, `OVERLAPBDYINTERSECT`, `EQUAL`, `INSIDE`, `COVEREDBY`, `CONTAINS`, `COVERS`, `ANYINTERACT`, `ON`), or `FILTER`, which performs an approximate check. `FILTER` will return all the candidates that intersect the polygon, and possibly a few more. Multiple masks are combined with the logical Boolean operator `OR` (for example, `'mask=inside+touch'`); however, `FILTER` cannot be combined with any other mask.

If this parameter is null or contains an empty string, `mask=ANYINTERACT` is assumed.

dop
Degree of parallelism for the clip operation. This may appear in the generated SQL statement, for example, as: `select /*+ PARALLEL ( 16 )*/ * from “LIDAR_DATA" …`

sdo_level
Specifies the level of tessellation. A value between 1 and 5 is common, and 4 is the default. This affects the generated tiles, for example, (x \>= 2.2500000125 and x \< 2.500000025 and y \>= 2.12500000625 and y \< 2.7500000375).

sdo_ntiles
Specifies the maximum number of tiles to generate. A value between 1 and 200 is common, and 100 is the default. This affects the generated tiles.

#### Usage Notes

This function is similar to the SDO_PC_PKG.CLIP_PC_FLAT function, except that it:

- Does not execute the query, but merely generates a SQL query string.
- Provides more tuning capability with the `sdo_level` and `sdo_ntiles` parameters. For most queries, the values `sdo_level=1` and `sdo_ntiles=10` are optimal.

See also the Usage Notes for SDO_PC_PKG.CLIP_PC_FLAT.

#### Examples

The following example creates a table named LIDAR_DATA, with columns X, Y, Z, and VAL (for some values). It then generates, and subsequently even executes (in a separate statement), a clip operation SQL statement on the point cloud.

    SQL> create table lidar_data(x number, y number, z number, val number);

    Table created.

    SQL>
    SQL> begin
      2    for y in 1..1024 loop
      3      for x in 1..1024 loop
      4        insert into lidar_data (x, y, z, val) values (x, y, x + y, x * y);
      5      end loop;
      6    end loop;
      7  end;
      8  /

    PL/SQL procedure successfully completed.

    SQL> SELECT
      2    sdo_pc_pkg.clip_pc_flat_string (
      3      geometry      => SDO_GEOMETRY(
      4                         2003,
      5                         8307,
      6                         NULL,
      7                         SDO_ELEM_INFO_ARRAY(1, 1003, 1),
      8                         SDO_ORDINATE_ARRAY(
      9                           1, 1,
     10                           2, 1,
     11                           2, 2,
     12                           3, 2,
     13                           3, 3,
     14                           1, 3,
     15                           1, 1)),
     16      table_name    => 'LIDAR_DATA',
     17      tolerance     => .00000005,
     18      other_dim_qry => MDSYS.SDO_MBR(
     19                         SDO_VPOINT_TYPE(0, 0),
     20                         SDO_VPOINT_TYPE(1000, 1000000)),
     21      mask          => 'FILTER',
     22      dop           => 16,
     23      sdo_level     => 4,
     24      sdo_ntiles    => 100) "Query"
     25  FROM
     26    dual;

    Query
    --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    select  /*+ PARALLEL ( 16 )*/ * from "LIDAR_DATA" WHERE  (
      (x >= 1.2499999625 and x <  1.37499996875 and y >= 1.2499999625 and y <  2.7500000375) OR
      (x >= 2.7500000375 and x <  2.87500004375 and y >= 2.12500000625 and y <  2.87500004375) OR
      (x >= 1.37499996875 and x <  1.499999975 and y >= 1.2499999625 and y <  2.7500000375) OR
      (x >= 2.2500000125 and x <  2.500000025 and y >= 2.12500000625 and y <  2.7500000375) OR
      (x >= 2.500000025 and x <  2.7500000375 and y >= 2.12500000625 and y <  2.7500000375) OR
      (x >= 1.12499995625 and x <  1.87499999375 and y >= 1.12499995625 and y <  1.2499999625) OR
      (x >= 1.7499999875 and x <  2 and y >= 2.12500000625 and y <  2.7500000375) OR
      (x >= 1.12499995625 and x <  1.2499999625 and y >= 1.2499999625 and y <  2.87500004375) OR
      (x >= 2 and x <  2.2500000125 and y >= 2.12500000625 and y <  2.7500000375) OR
      (x >= 1.7499999875 and x <  1.87499999375 and y >= 1.2499999625 and y <  2.12500000625) OR
      (x >= 1.2499999625 and x <  2.7500000375 and y >= 2.7500000375 and y <  2.87500004375) OR
      (x >= 1.499999975 and x <  1.62499998125 and y >= 1.2499999625 and y <  2.7500000375) OR
      (x >= 1.62499998125 and x <  1.7499999875 and y >= 1.2499999625 and y <  2.7500000375))  AND ( "Z" BETWEEN 0 AND 1000 )  AND ( "VAL" BETWEEN 0 AND 1000000 )   UNION ALL select  * from "LIDAR_DATA" W
    HERE  (
      (x >= .99999995 and x <  1.87499999375 and y >= .99999995 and y <  1.12499995625) OR
      (x >= .99999995 and x <  1.12499995625 and y >= 1.12499995625 and y <  2.87500004375) OR
      (x >= .99999995 and x <  2.87500004375 and y >= 2.87500004375 and y <  3.0000000500000001402157) OR
      (x >= 2 and x <  2.12500000625 and y >= .99999995 and y <  1.87499999375) OR
      (x >= 1.87499999375 and x <  2 and y >= .99999995 and y <  2.12500000625) OR
      (x >= 2.87500004375 and x <  3.0000000500000001402157 and y >= 1.87499999375 and y <  3.0000000500000001402157) OR
      (x >= 2 and x <  2.87500004375 and y >= 2 and y <  2.12500000625) OR
      (x >= 2 and x <  2.87500004375 and y >= 1.87499999375 and y <  2))  AND ("Z" BETWEEN 0 AND 1000 )  AND ("VAL" BETWEEN 0 AND 1000000 )

    1 row selected.

    SQL>
    SQL> declare
      2    stm varchar2(4096);
      3  begin
      4    SELECT
      5      sdo_pc_pkg.clip_pc_flat_string (
      6        geometry      => SDO_GEOMETRY(
      7                           2003,
      8                           8307,
      9                           NULL,
     10                           SDO_ELEM_INFO_ARRAY(1, 1003, 1),
     11                           SDO_ORDINATE_ARRAY(
     12                             1, 1,
     13                             2, 1,
     14                             2, 2,
     15                             3, 2,
     16                             3, 3,
     17                             1, 3,
     18                             1, 1)),
     19        table_name    => 'LIDAR_DATA',
     20        tolerance     => .00000005,
     21        other_dim_qry => MDSYS.SDO_MBR(
     22                           SDO_VPOINT_TYPE(0, 0),
     23                           SDO_VPOINT_TYPE(1000, 1000000)),
     24        mask          => 'FILTER',
     25        dop           => 16,
     26        sdo_level     => 4,
     27        sdo_ntiles    => 100) "Query"
     28    into
     29      stm
     30    FROM
     31      dual;
     32
     33    execute immediate 'create table result as (' || stm || ')';
     34  end;
     35  /

    PL/SQL procedure successfully completed.

    SQL>
    SQL> select * from result order by x, y;

             X          Y          Z        VAL
    ---------- ---------- ---------- ----------
             1          1          2          1
             1          2          3          2
             1          3          4          3
             2          1          3          2
             2          2          4          4
             2          3          5          6
             3          2          5          6
             3          3          6          9

    8 rows selected.

    SQL>
    SQL> drop table result;

    Table dropped.

    SQL> drop table lidar_data;

    Table dropped.

    SQL> SQL>

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.4 SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES

#### Format

    SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES(
         pc                  IN SDO_PC,
         sampling_resolution IN NUMBER,
         elevations          IN SDO_ORDINATE_ARRAY,
         region              IN SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY_ARRAY;

or

    SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES(
         pc_flat_table       IN VARCHAR2,
         srid                IN NUMBER,
         sampling_resolution IN NUMBER,
         elevations          IN SDO_ORDINATE_ARRAY,
         region              IN SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY_ARRAY;

or

    SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES(
         pc                  IN SDO_PC,
         sampling_resolution IN NUMBER,
         elevations_min      IN NUMBER,
         elevations_interval IN NUMBER,
         elevations_max      IN NUMBER,
         region              IN SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY_ARRAY;

or

    SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES(
         pc_flat_table       IN VARCHAR2,
         srid                IN SDO_PC,
         sampling_resolution IN NUMBER,
         elevations_min      IN NUMBER,
         elevations_interval IN NUMBER,
         elevations_max      IN NUMBER,
         region              IN SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY_ARRAY;

#### Description

Generates contour lines for a point cloud.

#### Parameters

pc
Point cloud object for which to generate contour lines.

sampling_resolution
A numeric value that determines the grid cell height and width in the coordinate reference system of the point cloud. The smaller the number, the more detailed are the resulting contour geometries.

The process of the contour generation is grid-based. The points within a grid cell get averaged. This means:

- Two slightly different point clouds may result in the same contours, as long as the grid cells yield the same averages.

- The number of vertices and smoothness of the contour lines is a direct function of the resolution.

elevations
An array of elevations for which contours should be generated.

elevations_min
The starting elevation value in a set of equidistant elevations for which contours should be generated.

elevations_interval
The interval to use for elevation values between `elevations_min` and `elevations_max` when generating coutours.

For example, if `elevations_min` is 100, `elevations_max` is 150, and `elevations_interval` is 10, then coutours are generated for elevations 100, 110, 120, 130, 140, and 150.

elevations_max
The ending elevation value in a set of equidistant elevations for which contours should be generated.

region
A window (within the extent of the point cloud) further restricting the region within which the contour lines should be generated.

#### Usage Notes

This function returns an array of SDO_GEOMETRY contours. The sequence of contours within the array is the same as the sequence in the `elevations` input parameter or in the computed values based on the `elevations_min` , `elevations_max`, and `elevations_interval` input parameters. Each contour is a multiline string.

Contours enclosing higher elevations are oriented counterclockwise (like outer rings). Contours enclosing lower elevations are oriented clockwise (like inner rings).

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example creates contour lines from a a specified a point cloud object.

    SELECT sdo_pc_pkg.create_contour_geometries(
      (SELECT pc FROM pcs WHERE pc_id = 1),
      sampling_resolution => 50,
      elevations => sdo_ordinate_array(100, 101, 102, 103, 104, 105, 106, 107, 108, 109),
      region => mdsys.sdo_geometry(2003, null, null, mdsys.sdo_elem_info_array(1, 1003, 3), mdsys.sdo_ordinate_array(-1000, 0, 999, 100)))
      FROM DUAL;

    SDO_PC_PKG.CREATE_CONTOUR_GEOMETRIES((SELECTPCFROMPCSWHEREPC_ID=1),SAMPLING_RESO
    --------------------------------------------------------------------------------
    SDO_GEOMETRY_ARRAY(SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1, 5
    , 2, 1), SDO_ORDINATE_ARRAY(-75.5, 24.5, -25.5, 74.5, 25.5, 74.5, 74.5, 25.5, 75
    .5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1, 7, 2, 1)
    , SDO_ORDINATE_ARRAY(-76.5, 24.5, -75.5, 25.5, -26.5, 74.5, 26.5, 74.5, 74.5, 26
    .5, 76.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1, 7,
     2, 1), SDO_ORDINATE_ARRAY(-77.5, 24.5, -75.5, 26.5, -27.5, 74.5, 27.5, 74.5, 74
    .5, 27.5, 77.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2,
     1, 7, 2, 1), SDO_ORDINATE_ARRAY(-78.5, 24.5, -75.5, 27.5, -28.5, 74.5, 28.5, 74
    .5, 74.5, 28.5, 78.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY
    (1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-79.5, 24.5, -75.5, 28.5, -29.5, 74.5, 29
    .5, 74.5, 74.5, 29.5, 79.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO
    _ARRAY(1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-80.5, 24.5, -75.5, 29.5, -30.5, 74
    .5, 30.5, 74.5, 74.5, 30.5, 80.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, SDO_ELE
    M_INFO_ARRAY(1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-81.5, 24.5, -75.5, 30.5, -31
    .5, 74.5, 31.5, 74.5, 74.5, 31.5, 81.5, 24.5)), SDO_GEOMETRY(2002, NULL, NULL, S
    DO_ELEM_INFO_ARRAY(1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-82.5, 24.5, -75.5, 31.
    5, -32.5, 74.5, 32.5, 74.5, 74.5, 32.5, 82.5, 24.5)), SDO_GEOMETRY(2002, NULL, N
    ULL, SDO_ELEM_INFO_ARRAY(1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-83.5, 24.5, -75.
    5, 32.5, -33.5, 74.5, 33.5, 74.5, 74.5, 33.5, 83.5, 24.5)), SDO_GEOMETRY(2002, N
    ULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1, 7, 2, 1), SDO_ORDINATE_ARRAY(-84.5, 24.5
    , -75.5, 33.5, -34.5, 74.5, 34.5, 74.5, 74.5, 34.5, 84.5, 24.5)))

    1 row selected.

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.5 SDO_PC_PKG.CREATE_PC

#### Format

    SDO_PC_PKG.CREATE_PC(
         inp           IN SDO_PC,
         inptable      IN VARCHAR2,
         clstPcdataTbl IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a point cloud using the points specified in the `inptable` parameter.

#### Parameters

inp
SDO_PC object to be used. This object must have been created by the SDO_PC_PKG.INIT function.

inptable
Name of the table or view containing the input point cloud data. This table or view should have the following columns:

- RID (VARCHAR2(24)): Unique ID for each point

- VAL_D1 (NUMBER): Ordinate in dimension 1

- VAL_D2 (NUMBER): Ordinate in dimension 2

- . . .

- VAL_Dn (NUMBER): Ordinate in dimension n, where n is the highest-numbered dimension. n should match the `pc_tot_dimensions` parameter value in the call to the SDO_PC_PKG.INIT function when the point cloud was initialized.

clstPcdataTbl
Name of the table for storing the resulting point data. If you do not specify a value, this table is not created. For more information about the table, see the Usage Notes.

#### Usage Notes

The first few dimensions of the point cloud are indexed and can later be searched using the SDO_PC_PKG.CLIP_PC function. The exact number of dimensions to index is determined by the dimensionality of the point cloud extent in the initialized point cloud object, specifically: `inp.pc_extent.sdo_gtype/1000`

If you specify a view name in the `inptable` parameter, the query `SELECT ROWID FROM <view-name>` must not return any errors.

If you specify a table name in the `clstPcdataTbl` parameter, the table must exist and have the following columns:

- PTN_ID (NUMBER)

- POINT_ID (NUMBER)

- RID (VARCHAR2(24): Unique ID for each point

- VAL_D1 (NUMBER): Ordinate in dimension 1

- VAL_D2 (NUMBER): Ordinate in dimension 2

- . . .

- VAL_Dn (NUMBER): Ordinate in dimension n, where n is the highest-numbered dimension. n should match the `pc_tot_dimensions` parameter value in the call to the SDO_PC_PKG.INIT function when the point cloud was initialized.

If a value is specified for the `clstPcdataTbl` parameter, this function populates the table by assigning appropriate values for PTN_ID and POINT_ID and by copying the values from the `inptable` table or view for other attributes. This table can be created as an index organized table. It can be used in applications for searching using SQL queries on dimensions other than those reflected in the index dimensionality. (For an explanation of index dimensionality and total dimensionality, see the explanation of the `pc_tot_dimensions` parameter of the SDO_PC_PKG.INIT function.)

The SDO_PC and SDO_PC_BLK_TYPE data types are described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example creates a point cloud. It is taken from the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    -- Create the blocks for the point cloud.
    sdo_pc_pkg.create_pc(
      pc,       -- Initialized PointCloud object
      'INPTAB', -- Name of input table to ingest into the pointcloud
      'RES'     -- Name of output table that stores the points (with ptn_id,pt_id)
      );
    . . .

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.6 SDO_PC_PKG.DROP_DEPENDENCIES

#### Format

    SDO_PC_PKG.DROP_DEPENDENCIES(
         basetable IN VARCHAR2,
         col       IN VARCHAR2);

#### Description

Drops the dependencies between a point cloud block table and a specified base table and column.

#### Parameters

basetable
Name of a base table that was specified (in the `basetable` parameter of the SDO_PC_PKG.INIT function) when the point cloud was initialized.

col
Name of a column in base table that was specified in the `basecol` parameter of the SDO_PC_PKG.INIT function.

#### Usage Notes

This procedure truncates the point cloud block table and removes the association between the block table and the base table and column combination.

After you execute this procedure, you can drop the point cloud block table or associate the table with another base table and column combination. For more information, see the Usage Notes for the SDO_PC_PKG.INIT function.

#### Examples

The following example drops the dependencies between a point cloud block table and a base table and column named BASE and PC, respectively.

    . . .
    declare
    begin
      mdsys.sdo_pc_pkg.drop_dependencies('BASE', 'PC');
    end;
    /

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.7 SDO_PC_PKG.GET_PT_IDS

#### Format

    SDO_PC_PKG.GET_PT_IDS(
         pts         IN BLOB,
         num_pts     IN NUMBER,
         pc_tot_dim  IN NUMBER,
         blk_domain  IN SDO_ORGSCL_TYPE DEFAULT NULL,
         ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the block ID and point ID values of the points in a block in a point cloud.

#### Parameters

pts
Binary large object (BLOB) containing the point cloud block.

num_pts
Number of points in the point cloud block. For a point cloud block, the number of points is stored in the NUM_POINTS column of the point cloud block table, which is described in [Table 2-7](spatial-datatypes-metadata.md) in [SDO_PC Object Type](spatial-datatypes-metadata.md).

pc_tot_dim
Number of dimensions for the points in the point cloud block.

blk_domain
(Not currently used.)

#### Usage Notes

This function returns an SDO_NUMBER_ARRAY object. The array contains multiple pairs of numbers, with each pair identifying the block ID and point ID of a point. For any specific call to this function, the block ID values associated with all points in the returned array will be the same. The SDO_NUMBER_ARRAY type is defined as `VARRAY(1048576) OF NUMBER`.

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example returns the block ID and point ID values of points in a point cloud block. It is taken from the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    SELECT SDO_PC_PKG.GET_PT_IDS(
        a.points,   -- LOB containing the points
        a.num_points, -- # of points in the LOB
        3 -- Total dimensionality of the points in the LOB
    ) FROM restst a WHERE num_points >0;

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.8 SDO_PC_PKG.HAS_PYRAMID

#### Format

    SDO_PC_PKG.HAS_PYRAMID(
         inp  IN SDO_PC
         ) RETURN NUMBER;

#### Description

Returns 1 if the specified point cloud object has a pyramid, or 0 is it does not have a pyramid (that is, if it has just a single level of blocks).

#### Parameters

inp
Input point cloud object. (The SDO_PC data type is described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).)

#### Usage Notes

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example checks if the point cloud objects in column PC of table PCS have pyramids. The result shows that SDO_PC object in the only row in the table does not have a pyramid.

    SELECT id, sdo_pc_pkg.has_pyramid(pc) "Has Pyramid" FROM pcs ORDER BY id;

            ID Has Pyramid
    ---------- -----------
             2           0

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.9 SDO_PC_PKG.INIT

#### Format

    SDO_PC_PKG.INIT(
         basetable          IN VARCHAR2,
         basecol            IN VARCHAR2,
         blktable           IN VARCHAR2,
         ptn_params         IN VARCHAR2,
         pc_extent          IN SDO_GEOMETRY,
         pc_tol             IN NUMBER DEFAULT 0.0000000000005,
         pc_tot_dimensions  IN NUMBER DEFAULT 2,
         pc_domain          IN SDO_ORGSCL_TYPE DEFAULT NULL,
         pc_val_attr_tables IN SDO_STRING_ARRAY DEFAULT NULL,
         pc_other_attrs     IN XMLTYPE DEFAULT NULL
         ) RETURN SDO_PC;

#### Description

Initializes a point cloud by creating an SDO_PC object.

#### Parameters

basetable
Name of the base table containing a column of type SDO_PC.

basecol
Name of the column of type SDO_PC in the base table.

blktable
Name of the point cloud block table, which is used for storing the blocks of point cloud. This table must exist, and must have been created by a statement in the following form: `CREATE TABLE <table-name> AS select * from mdsys.sdo_pc_blk_table;`

Each point cloud block table can only be associated with only one `basetable` and `basecol` combination.

ptn_params
Parameters for partitioning the point cloud, specified as a quoted string with keywords delimited by commas. For example: '`blk_capacity=1000,work_tablespace=my_work_ts'`. If this parameter is null, the point cloud is not partitioned. The following keywords are permitted:

- `blk_capacity=n`, where n is the maximum number of rows in each partition. The default value is 5000. If specified, must be a number greater than or equal to 50.

- `work_tablespace=x`, where x is the name of the tablespace in which to create temporary tables during the partitioning operations.

pc_extent
SDO_GEOMETRY object representing the spatial extent of the point cloud (the minimum bounding object enclosing all objects in the point cloud). This parameter must not be null.

For geodetic data, this geometry must have two dimensions; otherwise, it can have up to four dimensions. The dimensionality of this geometry is used as the minimum value permitted for the `pc_tot_dimensions` parameter, as explained in the description of that parameter.

pc_tol
Tolerance value for objects in the point cloud. (For information about spatial tolerance, see Section 1.5.5.) If this parameter is null, the default value is 0.0000000000005.

pc_tot_dimensions
A number specifying the total dimensionality of the point cloud object. For each point in the point cloud blocks, `pc_tot_dimensions` ordinates (values) are stored.

The total dimensionality must be greater than or equal to the index dimensionality, which is the number of dimensions in the `pc_extent` geometry. Specifying total dimensionality greater than index dimensionality enables necessary nonspatial attributes to be retrieved in the same fetch operation with spatial data. The maximum total dimensionality value is 8. The default value for this parameter is 2.

pc_domain
(Not currently used.)

pc_val_attr_tables
SDO_STRING_ARRAY object specifying the names of any value attribute tables for the point cloud. If this parameter is null, the point cloud has no associated value attribute tables. Type SDO_STRING_ARRAY is defined as VARRAY(1048576) OF VARCHAR2(32).

pc_other_attrs
XMLTYPE object specifying any other attributes of the point cloud. If this parameter is null, the point cloud has no other attributes.

This parameter can include metadata on point cloud pyramiding, as explained in the Usage Notes.

#### Usage Notes

After you use this function to initialize an SDO_PC object, you can create a point cloud by specifying this object as input to the SDO_PC_PKG.CREATE_PC procedure.

The SDO_PC data type is described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

After you use this function, the `blktable` table is kept in synchronization with the base table. For example, if a row is deleted from the basetable, the corresponding blocks of the point cloud object in that row are also deleted from the block table; and if the base table base table is truncated, the block table is truncated also.

The block table can be dropped only after either of the following occurs: the base table is dropped, or the SDO_PC_PKG.DROP_DEPENDENCIES procedure is executed.

The `pc_other_attrs` parameter can be used to specify metadata for point cloud pyramiding, for example:

    xmltype(
     '<opc:sdoPcObjectMetadata
        xmlns:opc="http://xmlns.oracle.com/spatial/vis3d/2011/sdovis3d.xsd"
        xmlns:las="http://liblas.org/schemas/LAS/1.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <opc:sdoPcPyramid preserveLevel1="true"/>
      </opc:sdoPcObjectMetadata>')

The XML Schema Definition (XSD) for the `pc_other_attrs` parameter can be viewed by entering the following statements:

    SET LONG 40000
    SELECT xmlschema FROM sdo_xml_schemas WHERE description = 'EPSG  sdo3d.xsd';

Point cloud pyramiding creates multiple pyramid levels from level 1 (leaves) to level n (root). Generally, points already stored at level i are not repeated, at any of the more detailed levels. Any point is physically stored, exactly once. The leaf level 1 can be exempted from this rule by specifying `preserveLevel1="true"` (as in the preceding example), so that applications that are not pyramiding-compliant do not need to adapt. However, this `preserveLevel1="true"` option (of exempting and thus preserving level 1) doubles the space requirement, because each point is then stored twice: once at root level 1, and once in the rest of the pyramid.

#### Examples

The following example initializes a point cloud by creating an SDO_PC object, and it displays the ID of the object. It is taken from the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    declare
      pc sdo_pc;
    begin
      -- Initialize the point cloud object.
      pc := sdo_pc_pkg.init(
              'BASE', -- Table that has the SDO_POINT_CLOUD column defined
              'PC',   -- Column name of the SDO_POINT_CLOUD object
              'BLKTAB', -- Table to store blocks of the point cloud
              'blk_capacity=1000', -- max # of points per block
              mdsys.sdo_geometry(2003, 8307, null,
                  mdsys.sdo_elem_info_array(1,1003,3),
                  mdsys.sdo_ordinate_array(-180, -90, 180, 90)),  -- Extent
                  0.5, -- Tolerance for point cloud
                  3, -- Total number of dimensions
                  null);
    . . .

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.10 SDO_PC_PKG.PC2DEM

#### Format

    SDO_PC_PKG.PC2DEM(
          geor        IN OUT SDO_GEORASTER,
          pc          IN SDO_PC,
          mbr2d       IN SDO_GEOMETRY,
          resolution  IN NUMBER,
          blocksize   IN NUMBER);

or

    SDO_PC_PKG.PC2DEM(
          geor            IN OUT SDO_GEORASTER,
          pc              IN SDO_PC,
          mbr2d           IN SDO_GEOMETRY,
          resolutionVert  IN NUMBER,
          resolutionHoriz IN NUMBER,
          blocksizeVert   IN NUMBER);
          blocksizeHoriz  IN NUMBER);

#### Description

Creates a DEM (Digital Elevation Model) GeoRaster object from an existing (blocked model) point cloud object..

#### Parameters

geor
GeoRaster object. (The SDO_GEORASTER data type is described in [Oracle Spatial and Graph GeoRaster Developer's Guide](../geors/georaster-datatypes.md).)

pc
Point cloud object. (The SDO_PC data type is described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).)

mbr2d
The two-dimensional minimum bounding rectangle (MBR) within which the DEM should be generated.

resolution
Resolution in coordinate reference system units per pixel, such as meters per pixel or degrees per pixel.

blockSize
Block size in pixels.

resolutionVert
If the horizontal and vertical resolutions differ: the vertical resolution in coordinate reference system units per pixel, such as meters per pixel or degrees per pixel.

resolutionHoriz
If the horizontal and vertical resolutions differ: the horizontal resolution in coordinate reference system units per pixel, such as meters per pixel or degrees per pixel.

blockSizeVert
If the horizontal and vertical block sizes differ: the vertical block size.

blockSizeHoriz
If the horizontal and vertical block sizes differ: the horizontal block size.

#### Usage Notes

This procedure modifies the specified GeoRaster object (`geor` parameter) based on information in the input point cloud.

The `pc` and `geor` objects must have the same coordinate reference system (SRID).

For the `geor` parameter, the input SDO_GEORASTER object can be obtained by inserting a GeoRaster object into a table and returning the GeoRaster object into a variable; for example:

    INSERT INTO raster_table VALUES (1, sdo_geor.init('raster_data_table'))
       RETURNING raster_image INTO geor;

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example creates a DEM from a point cloud.

    DECLARE
    pc   sdo_pc;
    geor sdo_georaster;
    mbr  sdo_geometry :=
      SDO_GEOMETRY(
        2003,
        27700,
        NULL,
        SDO_ELEM_INFO_ARRAY(1, 1003, 3),
        SDO_ORDINATE_ARRAY(
          668000, 5535000,
          672000, 5539000));
    BEGIN
      select pc INTO pc from pcs where id = 2;

      insert into raster (id, raster)
         values(2, sdo_geor.init('raster_data', 2))
         returning raster into geor;

      sdo_pc_pkg.pc2dem(
        geor         => geor,
        pc           => pc,
        mbr2d        => mbr,
        resolution   => 1.0,
        blockSize    => 512);

      sdo_geor.generatePyramid(
        georaster     => geor,
        pyramidParams => 'rLevel=7, resampling=BILINEAR');

      update raster set raster = geor where id = 2;
      commit;
    END;
    /

For additional examples, see the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.11 SDO_PC_PKG.PRESERVES_LEVEL1

#### Format

    SDO_PC_PKG.PRESERVES_LEVEL1(
         inp  IN SDO_PC
         ) RETURN NUMBER;

#### Description

Returns 1 if the specified point cloud object has a single block level containing all the points; otherwise, returns 0.

#### Parameters

inp
Input point cloud object. (The SDO_PC data type is described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).)

#### Usage Notes

A point cloud object can have a single block level containing all the points in either of the following cases:

- There is no pyramid, and all points are at the same level. In this case, the function returns 1.

- There is a pyramid, but the leaf level repeats one or more points from any other pyramid levels (in addition to containing points not already in other levels). In this case, the function returns 1. However, if there was a pyramid and the leaf level did not repeat any points from other pyramid levels, the function would return 0.

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example checks if the point cloud objects in column PC of table PCS have pyramids, and if each SDO_PC object has a single block level containing all the points for that object. The result shows that SDO_PC object in the only row in the table does not have a pyramid, and that this object does have a single block level containing all the points.

    SELECT id, sdo_pc_pkg.has_pyramid(pc) "Has Pyramid",
       sdo_pc_pkg.preserves_level1(pc) "Preserves Level 1"
       FROM pcs ORDER BY id;

            ID Has Pyramid Preserves Level 1
    ---------- ----------- -----------------
             2           0                 1

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.12 SDO_PC_PKG.SDO_PC_NN

#### Format

    SDO_PC_PKG.SDO_PC_NN(
         pc     IN SDO_PC,
         center IN SDO_GEOMETRY,
         n      IN NUMBER
         ) RETURN BLOB;

#### Description

Returns the nearest n points in the input point cloud object to the specified 3D point.

#### Parameters

pc
Point cloud object of type SDO_PC.

center
A 3D point representing the center around which we are looking for the nearest N points.

n
The number of nearest points to be found.

#### Usage Notes

The SDO_PC data type is described in [Point Cloud-Related Object Types](spatial-datatypes-metadata.md).

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example returns the 3200 closest points from a specified “center” point within a specified point cloud object.

    select
      rownum pt_pos,
      sdo_geometry(
        3001,
        null,
        sdo_point_type(x, y, z),
        null,
        null) pts
    from
      table(
        sdo_util.getvertices(
          geometry => sdo_pc_pkg.to_geometry(
                        pts => sdo_pc_pkg.sdo_pc_nn(
                                 pc     => (select pc from pcs where id = 1),
                                 center => sdo_geometry(
                                             3001,
                                             null,
                                             sdo_point_type(15, 15, 30),
                                             null,
                                             null),
                                 n      => 3200),
                        num_pts    => 3200,
                        pc_tot_dim => 3,
                        srid       => null,
                        blk_domain => null,
                        get_ids    => 1)))
    order by
      sqrt(
        (x - 15) * (x - 15) +
        (y - 15) * (y - 15) +
        (z - 30) * (z - 30)),
      x,
      y,
      z;

        PT_POS
    ----------
    PTS(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
             1
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(15, 15, 30), NULL, NULL)

             2
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(15, 15, 30), NULL, NULL)

             4
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(14, 15, 29), NULL, NULL)

            10
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(14, 15, 29), NULL, NULL)

             5
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(14, 16, 30), NULL, NULL)

            11
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(14, 16, 30), NULL, NULL)

             3
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(15, 14, 29), NULL, NULL)

    ...

          3200
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(33, 28, 61), NULL, NULL)

          3199
    SDO_GEOMETRY(3001, NULL, SDO_POINT_TYPE(46, 2, 48), NULL, NULL)

    3200 rows selected.

    Elapsed: 00:00:15.57

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.13 SDO_PC_PKG.SDO_PC_NN_FOR_EACH

#### Format

    SDO_PC_PKG.SDO_PC_NN_FOR_EACH(
         blocks     IN SIMPLE_BLK_REF,
         pc          IN SDO_PC,
         n           IN NUMBER,
         max_dist    IN NUMBER,
         qry_min_res IN NUMBER,
         qry_max_res IN NUMBER
         ) RETURN POINT_NEIGHBOR_PAIR_TAB;

#### Description

Returns the nearest n points, for each point within a query range.

#### Parameters

blocks
A table of PC blocks, individual query windows, and non-spatial query constraints.

pc
Point cloud object of type SDO_PC.

n
Number of nearest points to find for each point in the query range.

max_dist
Maximum distance to check for neighbors.

qry_min_res
Minimum pyramid level for point clouds with pyramids. (As shown in the Example, different query windows (closer to or farther from the beholder) can be used for different pyramid levels.

qry_max_res
Maximum pyramid level for point clouds with pyramids. (As shown in the Example, different query windows (closer to or farther from the beholder) can be used for different pyramid levels.

#### Usage Notes

The types related to this function are defined as follows.

    TYPE SIMPLE_BLK_REF is RECORD (
      blk_id        number,
      ind_dim_qry   MDSYS.sdo_geometry,
      other_dim_qry MDSYS.sdo_mbr);

    TYPE POINT_NEIGHBOR_PAIR_ROW is RECORD (
      obj_id          number,
      blk_id          number,
      pt_id           number,
      pt_x            number,
      pt_y            number,
      pt_z            number,
      neighbor_rank   number,
      neighbor_dist   number,
      neighbor_blk_id number,
      neighbor_pt_id  number,
      neighbor_x      number,
      neighbor_y      number,
      neighbor_z      number);

    TYPE POINT_NEIGHBOR_PAIR_TAB is TABLE of POINT_NEIGHBOR_PAIR_ROW;

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example returns the nearest 10 points, for each point within the specified query range.

    define query_window = SDO_GEOMETRY(2003,NULL,NULL,SDO_ELEM_INFO_ARRAY(1,1003,3),SDO_ORDINATE_ARRAY(100,100,102,102));

    with
      candidates AS (
        select
          blocks.blk_id,
          SDO_GEOM.SDO_INTERSECTION(subqueries.ind_dim_qry, blocks.blk_extent, 0.05),
          subqueries.other_dim_qry
        from
          blocks blocks,
          (
            select 1 min_res, 1 max_res, &query_window ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual union all
            select 2 min_res, 5 max_res, &query_window ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual
          ) subqueries
        where
          blocks.obj_id = 1 and
          blocks.pcblk_min_res <= max_res and
          blocks.pcblk_max_res >= min_res and
          SDO_ANYINTERACT(blocks.blk_extent, subqueries.ind_dim_qry) = 'TRUE')
    select /*+ parallel (2) */
      *
    from
      table(
        sdo_pc_pkg.sdo_pc_nn_for_each(
          blocks      => cursor(select * from candidates),
          pc          => (select pc from pcs where id = 1),
          n           => 10,
          max_dist    => 10,
          qry_min_res => 1,
          qry_max_res => 1))
    order by
      obj_id,
      blk_id,
      pt_id,
      neighbor_rank;

    old  10:         select 1 min_res, 1 max_res, &query_window ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual union all
    new  10:         select 1 min_res, 1 max_res, SDO_GEOMETRY(2003,NULL,NULL,SDO_ELEM_INFO_ARRAY(1,1003,3),SDO_ORDINATE_ARRAY(100,100,102,102)) ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual union all
    old  11:         select 2 min_res, 5 max_res, &query_window ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual
    new  11:         select 2 min_res, 5 max_res, SDO_GEOMETRY(2003,NULL,NULL,SDO_ELEM_INFO_ARRAY(1,1003,3),SDO_ORDINATE_ARRAY(100,100,102,102)) ind_dim_qry, cast(null as sdo_mbr) other_dim_qry from dual

        OBJ_ID     BLK_ID      PT_ID       PT_X       PT_Y       PT_Z NEIGHBOR_RANK NEIGHBOR_DIST NEIGHBOR_BLK_ID NEIGHBOR_PT_ID NEIGHBOR_X NEIGHBOR_Y NEIGHBOR_Z
    ---------- ---------- ---------- ---------- ---------- ---------- ------------- ------------- --------------- -------------- ---------- ---------- ----------
             1          2        272        100        100        200             1             0               2            272        100        100        200
             1          2        272        100        100        200             2    1.41421356               2            268         99        101        200
             1          2        272        100        100        200             3    1.41421356               2            271         99        100        199
             1          2        272        100        100        200             4    1.41421356               2            293        100         99        199
             1          2        272        100        100        200             5    1.41421356               2            275        100        101        201
             1          2        272        100        100        200             6    1.41421356               2            273        101        100        201
             1          2        272        100        100        200             7    1.41421356               2            292        101         99        200
             1          2        272        100        100        200             8    2.44948974               2            269         98        101        199
             1          2        272        100        100        200             9    2.44948974               2            250         99         99        198
             1          2        272        100        100        200            10    2.44948974               2            267         99        102        201
             1          2        273        101        100        201             1             0               2            273        101        100        201
             1          2        273        101        100        201             2    1.41421356               2            272        100        100        200
             1          2        273        101        100        201             3    1.41421356               2            275        100        101        201
             1          2        273        101        100        201             4    1.41421356               2            292        101         99        200
             1          2        273        101        100        201             5    1.41421356               2            274        101        101        202
             1          2        273        101        100        201             6    1.41421356               2            291        102         99        201
             1          2        273        101        100        201             7    1.41421356               2            286        102        100        202
             1          2        273        101        100        201             8    2.44948974               2            268         99        101        200
             1          2        273        101        100        201             9    2.44948974               2            293        100         99        199
             1          2        273        101        100        201            10    2.44948974               2            276        100        102        202
             1          2        274        101        101        202             1             0               2            274        101        101        202
             1          2        274        101        101        202             2    1.41421356               2            276        100        102        202
             1          2        274        101        101        202             3    1.41421356               2            275        100        101        201
             1          2        274        101        101        202             4    1.41421356               2            273        101        100        201
             1          2        274        101        101        202             5    1.41421356               2            279        101        102        203
             1          2        274        101        101        202             6    1.41421356               2            286        102        100        202
             1          2        274        101        101        202             7    1.41421356               2            285        102        101        203
             1          2        274        101        101        202             8    2.44948974               2            267         99        102        201
             1          2        274        101        101        202             9    2.44948974               2            272        100        100        200
             1          2        274        101        101        202            10    2.44948974               2            277        100        103        203
             1          2        275        100        101        201             1             0               2            275        100        101        201
             1          2        275        100        101        201             2    1.41421356               2            267         99        102        201
             1          2        275        100        101        201             3    1.41421356               2            268         99        101        200
             1          2        275        100        101        201             4    1.41421356               2            272        100        100        200
             1          2        275        100        101        201             5    1.41421356               2            276        100        102        202
             1          2        275        100        101        201             6    1.41421356               2            273        101        100        201
             1          2        275        100        101        201             7    1.41421356               2            274        101        101        202
             1          2        275        100        101        201             8    2.44948974               2            264         98        102        200
             1          2        275        100        101        201             9    2.44948974               2            266         99        103        202
             1          2        275        100        101        201            10    2.44948974               2            271         99        100        199
             1          2        276        100        102        202             1             0               2            276        100        102        202
             1          2        276        100        102        202             2    1.41421356               2            266         99        103        202
             1          2        276        100        102        202             3    1.41421356               2            267         99        102        201
             1          2        276        100        102        202             4    1.41421356               2            277        100        103        203
             1          2        276        100        102        202             5    1.41421356               2            275        100        101        201
             1          2        276        100        102        202             6    1.41421356               2            274        101        101        202
             1          2        276        100        102        202             7    1.41421356               2            279        101        102        203
             1          2        276        100        102        202             8    2.44948974               2            265         98        103        201
             1          2        276        100        102        202             9    2.44948974               2            469         99        104        203
             1          2        276        100        102        202            10    2.44948974               2            268         99        101        200
             1          2        279        101        102        203             1             0               2            279        101        102        203
             1          2        279        101        102        203             2    1.41421356               2            277        100        103        203
             1          2        279        101        102        203             3    1.41421356               2            276        100        102        202
             1          2        279        101        102        203             4    1.41421356               2            274        101        101        202
             1          2        279        101        102        203             5    1.41421356               2            278        101        103        204
             1          2        279        101        102        203             6    1.41421356               2            280        102        102        204
             1          2        279        101        102        203             7    1.41421356               2            285        102        101        203
             1          2        279        101        102        203             8    2.44948974               2            266         99        103        202
             1          2        279        101        102        203             9    2.44948974               2            458        100        104        204
             1          2        279        101        102        203            10    2.44948974               2            275        100        101        201
             1          2        280        102        102        204             1             0               2            280        102        102        204
             1          2        280        102        102        204             2    1.41421356               2            278        101        103        204
             1          2        280        102        102        204             3    1.41421356               2            279        101        102        203
             1          2        280        102        102        204             4    1.41421356               2            285        102        101        203
             1          2        280        102        102        204             5    1.41421356               2            281        102        103        205
             1          2        280        102        102        204             6    1.41421356               2            283        103        102        205
             1          2        280        102        102        204             7    1.41421356               2            284        103        101        204
             1          2        280        102        102        204             8    2.44948974               2            277        100        103        203
             1          2        280        102        102        204             9    2.44948974               2            457        101        104        205
             1          2        280        102        102        204            10    2.44948974               2            274        101        101        202
             1          2        285        102        101        203             1             0               2            285        102        101        203
             1          2        285        102        101        203             2    1.41421356               2            274        101        101        202
             1          2        285        102        101        203             3    1.41421356               2            279        101        102        203
             1          2        285        102        101        203             4    1.41421356               2            280        102        102        204
             1          2        285        102        101        203             5    1.41421356               2            286        102        100        202
             1          2        285        102        101        203             6    1.41421356               2            284        103        101        204
             1          2        285        102        101        203             7    1.41421356               2            287        103        100        203
             1          2        285        102        101        203             8    2.44948974               2            276        100        102        202
             1          2        285        102        101        203             9    2.44948974               2            273        101        100        201
             1          2        285        102        101        203            10    2.44948974               2            278        101        103        204
             1          2        286        102        100        202             1             0               2            286        102        100        202
             1          2        286        102        100        202             2    1.41421356               2            273        101        100        201
             1          2        286        102        100        202             3    1.41421356               2            274        101        101        202
             1          2        286        102        100        202             4    1.41421356               2            291        102         99        201
             1          2        286        102        100        202             5    1.41421356               2            285        102        101        203
             1          2        286        102        100        202             6    1.41421356               2            287        103        100        203
             1          2        286        102        100        202             7    1.41421356               2            288        103         99        202
             1          2        286        102        100        202             8    2.44948974               2            275        100        101        201
             1          2        286        102        100        202             9    2.44948974               2            292        101         99        200
             1          2        286        102        100        202            10    2.44948974               2            279        101        102        203

    90 rows selected.

    Elapsed: 00:00:03.02

**Parent topic:** SDO_PC_PKG Package (Point Clouds)

### 30.14 SDO_PC_PKG.TO_GEOMETRY

#### Format

    SDO_PC_PKG.TO_GEOMETRY(
         pts        IN BLOB,
         num_pts    IN NUMBER,
         pc_tot_dim IN NUMBER,
         srid       IN NUMBER DEFAULT NULL,
         blk_domain IN SDO_ORGSCL_TYPE DEFAULT NULL
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object representing all or part of a point cloud.

#### Parameters

pts
BLOB containing the points.

num_pts
Maximum number of points to be included in the resulting geometry.

pc_tot_dim
Number of spatial dimensions defined for the data.

srid
Spatial reference (coordinate system) ID associated with the data. If this parameter is null, no SRID value is associated with the data.

blk_domain
(Not currently used.)

#### Usage Notes

This function returns a single multipoint SDO_GEOMETRY object that represents all point geometries in the `pts` parameter. For example, the points could reflect the result of a clip operation or the contents of an entire block.

[Modeling Solids](spatial-concepts.md) describes how to use point clouds to model solids.

#### Examples

The following example returns a multipoint collection geometry object representing a point cloud. It is taken from the `$ORACLE_HOME/md/demo/PointCloud/examples/plsql/pc.sql` example program, which is available if you installed the files from the Oracle Database Examples media (see [Oracle Database Examples Installation Guide](../exmpl/index.md)).

    . . .
    -- Return points in blk_id of the point cloud as a multipoint collection.
    select sdo_pc_pkg.to_geometry(
                        a.points,   -- point LOB
                        a.num_points, -- # of points in the LOB
                        3,  -- total dimensionality
                        8307 -- SRID
                        ) from blktab a where blk_id=0;
    . . .

**Parent topic:** SDO_PC_PKG Package (Point Clouds)
