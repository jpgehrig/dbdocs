## 31  SDO_SAM Package (Spatial Analysis and Mining)

The MDSYS.SDO_SAM package contains subprograms for spatial analysis and data mining.

To use the subprograms in this chapter, you must understand the conceptual information about spatial analysis and data mining in [Spatial Analysis and Mining](spatial-analysis-mining.md).

**Note:**

SDO_SAM subprograms are supported for two-dimensional geometries only. They are not supported for three-dimensional geometries.

The rest of this chapter provides reference information on the spatial analysis and mining subprograms, listed in alphabetical order.

- SDO_SAM.AGGREGATES_FOR_GEOMETRY
- SDO_SAM.AGGREGATES_FOR_LAYER
- SDO_SAM.BIN_GEOMETRY
- SDO_SAM.BIN_LAYER
- SDO_SAM.COLOCATED_REFERENCE_FEATURES
- SDO_SAM.SIMPLIFY_GEOMETRY
- SDO_SAM.SIMPLIFY_LAYER
- SDO_SAM.SPATIAL_CLUSTERS
- SDO_SAM.TILED_AGGREGATES
- SDO_SAM.TILED_BINS

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 31.1 SDO_SAM.AGGREGATES_FOR_GEOMETRY

#### Format

    SDO_SAM.AGGREGATES_FOR_GEOMETRY(
         theme_name       IN VARCHAR2,
         theme_colname    IN VARCHAR2,
         aggr_type_string IN VARCHAR2,
         aggr_col_string  IN VARCHAR2,
         geom             IN SDO_GEOMETRY,
         dst_spec         IN VARCHAR2 DEFAULT NULL
         ) RETURN NUMBER;

#### Description

Computes the thematic aggregate for a geometry.

#### Parameters

theme_name
Name of the theme table.

theme_colname
Name of the geometry column in `theme_name`.

aggr_type_string
Any Oracle SQL aggregate function that accepts one or more numeric values and computes a numeric value, such as `SUM`, `MIN`, `MAX`, or `AVG`.

aggr_col_string
Name of a column in `theme_name` on which to compute aggregate values, as explained in the Usage Notes. An example might be a POPULATION column.

geom
Geometry object.

dst_spec
A quoted string specifying either a distance buffer or a number of nearest neighbor geometries to consider. See the Usage Notes for an explanation of the format and meaning.

#### Usage Notes

For a specific geometry, this function identifies the geometries in the `theme_name` table, finds their intersection ratio, multiplies the specified aggregate using this intersection ratio, and aggregates it for the geometry. Specifically, for all rows of the `theme_name` table that intersect with the specified geometry, it returns the value from the following function:

    aggr_type_string(aggr_col_string * proportional_area_of_intersection(geometry, theme_name.theme_colname))

The `theme_colname` column must have a spatial index defined on it. For best performance, insert simplified geometries into this column.

The `dst_spec` parameter, if specified, is a quoted string that must contain either of the following:

- The `distance` keyword and optionally the `unit` keyword (unit of measurement associated with the distance value), to specify a buffer around the geometry. For example, `'distance=2 unit=km'` specifies a 2-kilometer buffer around the input geometry. If `dst_spec` is not specified, no buffer is used.

  If the `unit` keyword is specified, the value must be an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `'unit=km'`). If the `unit` keyword is not specified, the unit of measurement associated with the geometry is used. See [Unit of Measurement Support](spatial-datatypes-metadata.md) for more information about unit of measurement specification.

- The `sdo_num_res` keyword, to specify the number of nearest-neighbor geometries to consider, without considering proportional coverage. For example, `'sdo_num_res=5'` could be used in a query that asks for the populations of the five cities that are nearest to a specified point.

#### Examples

The following example computes the thematic aggregate for an area with a 3-mile radius around a specified point geometry. In this case, the total population of the area is computed based on the proportion of the circle's area within different counties, assuming uniform distribution of population within the counties.

    SELECT sdo_sam.aggregates_for_geometry(
      'GEOD_COUNTIES', 'GEOM',
      'sum', 'totpop',
      SDO_GEOMETRY(2001, 8307,
        SDO_POINT_TYPE(-73.943849, 40.6698,NULL),
        NULL, NULL),
      'distance=3 unit=mile')
    FROM DUAL a ;

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.2 SDO_SAM.AGGREGATES_FOR_LAYER

#### Format

    SDO_SAM.AGGREGATES_FOR_LAYER(
         theme_name       IN VARCHAR2,
         theme_colname    IN VARCHAR2,
         aggr_type_string IN VARCHAR2,
         aggr_col_string  IN VARCHAR2,
         tablename        IN VARCHAR2,
         colname          IN VARCHAR2,
         dst_spec         IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_REGAGGRSET;

#### Description

Computes thematic aggregates for a layer of geometries.

#### Parameters

theme_name
Name of the theme table.

theme_colname
Name of the geometry column in `theme_name`.

aggr_type_string
Any Oracle SQL aggregate function that accepts one or more numeric values and computes a numeric value, such as `SUM`, `MIN`, `MAX`, or `AVG`.

aggr_col_string
Name of a column in `theme_name` on which to compute aggregate values, as explained in the Usage Notes. An example might be a POPULATION column.

tablename
Name of the data mining table.

colname
Name of the column in `tablename` that holds the geometries.

dst_spec
A quoted string specifying either a distance buffer or a number of nearest neighbor geometries to consider. See the Usage Notes for the SDO_SAM.AGGREGATES_FOR_GEOMETRY function in this chapter for an explanation of the format and meaning.

#### Usage Notes

For each geometry in `tablename`, this function identifies the geometries in the `theme_name` table, finds their intersection ratio, multiplies the specified aggregate using this intersection ratio, and aggregates it for each geometry in `tablename`. Specifically, for all rows of the `theme_name` table, it returns the value from the following function:

    aggr_type_string(aggr_col_string * proportional_area_of_intersection(geometry, theme_name.theme_colname))

This function returns an object of type SDO_REGAGGRSET. The SDO_REGAGGRSET object type is defined as:

    TABLE OF SDO_REGAGGR

The SDO_REGAGGR object type is defined as:

     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     REGION_ID                                          VARCHAR2(24)
     GEOMETRY                                           MDSYS.SDO_GEOMETRY
     AGGREGATE_VALUE                                    NUMBER

The `theme_colname` column must have a spatial index defined on it. For best performance, insert simplified geometries into this column.

#### Examples

The following example computes the thematic aggregates for all geometries in a table named TEST_TAB for an area with a 3-mile radius around a specified point geometry. In this case, the total population of each area is computed based on the proportion of the circle's area within different counties, assuming uniform distribution of population within the counties.

    SELECT a.aggregate_value FROM TABLE(sdo_sam.aggregates_for_layer(
      'GEOD_COUNTIES', 'GEOM', 'SUM', TOTPOP', TEST_TAB', 'GEOM'
        'distance=3 unit=mile')) a;

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.3 SDO_SAM.BIN_GEOMETRY

#### Format

    SDO_SAM.BIN_GEOMETRY(
         geom          IN SDO_GEOMETRY,
         tol           IN SDO_DIM_ARRAY,
         bin_tablename IN VARCHAR2,
         bin_colname   IN VARCHAR2
         ) RETURN NUMBER;

or

    SDO_SAM.BIN_GEOMETRY(
         geom           IN SDO_GEOMETRY,
          dim           IN SDO_DIM_ARRAY,
          bin_tablename IN VARCHAR2,
          bin_colname   IN VARCHAR2  
         ) RETURN NUMBER;

#### Description

Computes the most-intersecting tile for a geometry.

#### Parameters

geom
Geometry for which to compute the bin.

tol
Tolerance value (see [Tolerance](spatial-concepts.md)).

dim
Dimensional array for the table that holds the geometries for the bins.

bin_tablename
Name of the table that holds the geometries for the bins.

bin_colname
Column in `bin_tablename` that holds the geometries for the bins.

#### Usage Notes

This function returns the bin that intersects most with the specified geometry. If multiple bins intersect to the same extent with the specified geometry, the bin with the smallest area is returned.

To perform this operation on all rows in the data mining table, using the specified `bin_tablename`, you can use the SDO_SAM.BIN_LAYER procedure.

#### Examples

The following example computes the bin for a specified geometry.

    SELECT sdo_sam.bin_geometry(a.geometry, 0.0000005, 'BINTBL', 'GEOMETRY')
      FROM poly_4pt a, user_sdo_geom_metadata b
      WHERE b.table_name='POLY_4PT' AND a.gid=1;

    SDO_SAM.BIN_GEOMETRY(A.GEOMETRY,0.0000005,'BINTBL','GEOMETRY')
    --------------------------------------------------------------
                                                                43

    1 row selected.

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.4 SDO_SAM.BIN_LAYER

#### Format

    SDO_SAM.BIN_LAYER(
         tablename       IN VARCHAR2,
         colname         IN VARCHAR2,
         bin_tablename   IN VARCHAR2,
         bin_colname     IN VARCHAR2,
         bin_id_colname  IN VARCHAR2,
         commit_interval IN NUMBER DEFAULT 20);

#### Description

Assigns each location (and the corresponding row) in a data mining table to a spatial bin.

#### Parameters

tablename
Name of the data mining table.

colname
Name of the column in `table_name` that holds the location coordinates.

bin_tablename
Name of the table that contains information (precomputed for the entire two-dimensional space) about the spatial bins.

bin_colname
Column in `bin_tablename` that holds the geometries for the bins.

bin_id_colname
Name of the column in the data mining table that holds the bin ID value of each geometry added to a bin. (Each affected row in the data mining table is updated with the ID value of the bin geometry in `bin_tablename`.)

commit_interval
Number of bin insert operations to perform before Spatial and Graph performs an internal commit operation. If `commit_interval` is not specified, a commit is performed after every 20 insert operations.

#### Usage Notes

This procedure computes the most-intersecting tile for each geometry in a specified layer using the bins in `bin_tablename`. The bin ID value for each geometry is added in `bin_id_colname`.

Using this procedure achieves the same result as using the SDO_SAM.BIN_GEOMETRY function on each row in the data mining table, using the specified `bin_tablename`.

#### Examples

The following example assigns each GEOMETRY column location and corresponding row in the POLY_4PT_TEMP data mining table to a spatial bin, and performs an internal commit operation after each bin table insertion.

    CALL SDO_SAM.BIN_LAYER('POLY_4PT_TEMP', 'GEOMETRY', 'BINTBL', 'GEOMETRY', 'BIN_ID', 1);

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.5 SDO_SAM.COLOCATED_REFERENCE_FEATURES

#### Format

    SDO_SAM.COLOCATED_REFERENCE_FEATURES(
         theme_tablename  IN VARCHAR2,
         theme_colname    IN VARCHAR2,
         theme_predicate  IN VARCHAR2,
         tablename        IN VARCHAR2,
         colname          IN VARCHAR2,
         ref_predicate    IN VARCHAR2,
         dst_spec         IN VARCHAR2,
         result_tablename IN VARCHAR2,
         commit_interval  IN NUMBER DEFAULT 100);

#### Description

Performs a partial predicate-based join of tables, and materializes the join results into a table.

#### Parameters

theme_tablename
Name of the table with which to join `tablename`.

theme_colname
Name of the geometry column in `theme_tablename`.

theme_predicate
Qualifying WHERE clause predicate to be applied to `theme_tablename`.

tablename
Name of the data mining table.

colname
Name of the column in `tablename` that holds the location coordinates.

ref_predicate
Qualifying WHERE clause predicate to be applied to `tablename`. Must a null or non-null value: if null, no predicate is applied; if non-null, it must be a single table predicate, such as `'country_code=10'.`

dst_spec
A quoted string containing a distance value and optionally a unit value for a buffer around the geometries. See the Usage Notes for an explanation of the format and meaning.

result_tablename
The table in which materialized join results are stored. This table must exist and must have the following definition: `(tid NUMBER, rid1 VARCHAR2(24), rid2 VARCHAR2(24))`

commit_interval
Number of internal join operations to perform before Spatial and Graph performs an internal commit operation. If `commit_interval` is not specified, a commit is performed after every 100 internal join operations.

#### Usage Notes

This procedure materializes each pair of rowids returned from a predicate-based join operation, and stores them in the `rid1, rid2` columns of `result_tablename`. The `tid` is a unique generated "interaction" number corresponding to each `rid1` value.

The `dst_spec` parameter, if specified, is a quoted string containing the `distance` keyword and optionally the `unit` keyword (unit of measurement associated with the distance value), to specify a buffer around the geometry. For example, `'distance=2 unit=km'` specifies a 2-kilometer buffer around the input geometry. If `dst_spec` is not specified, no buffer is used.

If the `unit` keyword is specified, the value must be an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `'unit=KM'`). If the `unit` keyword is not specified, the unit of measurement associated with the geometry is used. See [Unit of Measurement Support](spatial-datatypes-metadata.md) for more information about unit of measurement specification.

#### Examples

The following example identifies cities with a 1990 population (POP90 column value) greater than 120,000 that are located within 20 kilometers of interstate highways (GEOM column in the GEOD_INTERSTATES table). It stores the results in a table named COLOCATION_TABLE, and performs an internal commit operation after each 20 internal operations.

    EXECUTE SDO_SAM.COLOCATED_REFERENCE_FEATURES(
      'geod_cities', 'location', 'pop90 > 120000',
      'geod_interstates', 'geom', null,
      'distance=20 unit=km', 'colocation_table', 20);

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.6 SDO_SAM.SIMPLIFY_GEOMETRY

#### Format

    SDO_SAM.SIMPLIFY_GEOMETRY(
         geom                  IN SDO_GEOMETRY,
         dim                   IN SDO_DIM_ARRAY,
         pct_area_change_limit IN NUMBER DEFAULT 2
         ) RETURN SDO_GEOMETRY;

or

    SDO_SAM.SIMPLIFY_GEOMETRY(
         geom                  IN SDO_GEOMETRY,
         tol                   IN NUMBER,
         pct_area_change_limit IN NUMBER DEFAULT 2
         ) RETURN SDO_GEOMETRY;

#### Description

Simplifies a geometry.

#### Parameters

geom
Geometry to be simplified.

dim
Dimensional array for the geometry to be simplified.

tol
Tolerance value (see [Tolerance](spatial-concepts.md)).

pct_area_change_limit
The percentage of area changed to be used for each simplification iteration, as explained in the Usage Notes.

#### Usage Notes

This function reduces the number of vertices in a geometry by internally applying the [SDO_UTIL.SIMPLIFY](SDO_UTIL-reference.md) function (documented in [SDO_UTIL Package (Utility)](SDO_UTIL-reference.md)) with an appropriate threshold value.

Reducing the number of vertices may result in a change in the area of the geometry. The `pct_area_change_limit` parameter specifies how much area change can be tolerated while simplifying the geometry. It is usually a number from 1 to 100. The default value is 2; that is, the area of the geometry can either increase or decrease by at most two percent compared to the original geometry as a result of the geometry simplification.

#### Examples

The following example simplifies the geometries in the GEOMETRY column of the POLY_4PT_TEMP table.

    SELECT sdo_sam.simplify_geometry(a.geometry, 0.00000005)
      FROM poly_4pt_temp a, user_sdo_geom_metadata b
      WHERE b.table_name='POLY_4PT_TEMP' ;

    SDO_SAM.SIMPLIFY_GEOMETRY(A.GEOMETRY,0.00000005)(ORIG_AREA, CUR_AREA, ORIG_LEN,
    --------------------------------------------------------------------------------
    SDO_SMPL_GEOMETRY(28108.5905, 28108.5905, 758.440118, 758.440118, SDO_GEOMETRY(2
    003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARRAY(-122.4215,
    37.7862, -122.422, 37.7869, -122.421, 37.789, -122.42, 37.7866, -122.4215, 37.78
    62)))

    SDO_SMPL_GEOMETRY(4105.33806, 4105.33806, 394.723053, 394.723053, SDO_GEOMETRY(2
    003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARRAY(-122.4019,
    37.8052, -122.4027, 37.8055, -122.4031, 37.806, -122.4012, 37.8052, -122.4019, 3
    7.8052)))
       .
       .
       .
    50 rows selected.

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.7 SDO_SAM.SIMPLIFY_LAYER

#### Format

    SDO_SAM.SIMPLIFY_LAYER(
         theme_tablename       IN VARCHAR2,
         theme_colname         IN VARCHAR2,
         smpl_geom_colname     IN VARCHAR2,
         commit_interval       IN NUMBER DEFAULT 10,
         pct_area_change_limit IN NUMBER DEFAULT 2);

#### Description

Simplifies a geometry layer.

#### Parameters

theme_tablename
Name of the table containing the geometry layer to be simplified.

theme_colname
Column in `theme_tablename` of type SDO_GEOMETRY containing the geometries to be simplified.

smpl_geom_colname
Column in `theme_tablename` of type SDO_GEOMETRY into which the simplified geometries are to be placed by this procedure.

commit_interval
Number of geometries to simplify before Spatial and Graph performs an internal commit operation. If `commit_interval` is not specified, a commit is performed after every 10 simplification operations.

pct_area_change_limit
The percentage of area changed to be used for each simplification iteration, as explained in the Usage Notes for the SDO_SAM.SIMPLIFY_GEOMETRY function.

#### Usage Notes

This procedure simplifies all geometries in a layer. It is equivalent to calling the SDO_SAM.SIMPLIFY_GEOMETRY function for each geometry in the layer, except that each simplified geometry is put in a separate column in the table instead of being returned to the caller. See also the Usage Notes for the SDO_SAM.SIMPLIFY_GEOMETRY function.

#### Examples

The following example adds a column named SMPL_GEOM to the POLY_4PT_TEMP table, then simplifies all geometries in the GEOMETRY column of the POLY_4PT_TEMP table, placing each simplified geometry in the SMPL_GEOM column in the same row with its associated original geometry.

    ALTER TABLE poly_4pt_temp ADD (smpl_geom mdsys.sdo_geometry);

    Table altered.

    EXECUTE sdo_sam.simplify_layer('POLY_4PT_TEMP', 'GEOMETRY', 'SMPL_GEOM');

    PL/SQL procedure successfully completed.

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.8 SDO_SAM.SPATIAL_CLUSTERS

#### Format

    SDO_SAM.SPATIAL_CLUSTERS(
         tablename      IN VARCHAR2,
         colname        IN VARCHAR2,
         max_clusters   IN NUMBER,
         allow_outliers IN VARCHAR2 DEFAULT 'TRUE',
         tablepartition IN VARCHAR2 DEFAULT NULL
         ) RETURN SDO_REGIONSET;

#### Description

Computes clusters using the existing R-tree index, and returns a set of SDO_REGION objects where the geometry column specifies the boundary of each cluster and the `geometry_key` value is set to null.

#### Parameters

tablename
Name of the data mining table.

colname
Name of the column in `tablename` that holds the location coordinates.

max_clusters
Maximum number of clusters to obtain.

allow_outliers
`TRUE` (the default) causes outlying values (isolated instances) to be included in the spatial clusters; `FALSE` causes outlying values not to be included in the spatial clusters. (`TRUE` accommodates all data and may result in larger clusters; `FALSE` may exclude some data and may result in smaller clusters.)

tablepartition
Name of the partition in `tablename`.

#### Usage Notes

The clusters are computed using the spatial R-tree index on `tablename`.

#### Examples

The following example clusters the locations in cities into at most three clusters, and includes outlying values in the clusters.

    SELECT * FROM
      TABLE(sdo_sam.spatial_clusters('PROJ_CITIES', 'LOCATION', 3, 'TRUE'));

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.9 SDO_SAM.TILED_AGGREGATES

#### Format

    SDO_SAM.TILED_AGGREGATES(
         theme_name       IN VARCHAR2,
         theme_colname    IN VARCHAR2,
         aggr_type_string IN VARCHAR2,
         aggr_col_string  IN VARCHAR2,
         tiling_level     IN NUMBER DEFAULT NULL,
         tiling_domain    IN SDO_DIM_ARRAY DEFAULT NULL,
         zero_agg_tiles   IN NUMBER DEFAULT 0,
         xdivs            IN NUMBER DEFAULT NULL,
         ydivs            IN NUMBER DEFAULT NULL
         ) RETURN SDO_REGAGGRSET;

#### Description

Tiles aggregates for a domain. For each tile, computes the intersecting geometries from the theme table; the values in the `aggr_col_string` column are weighted proportionally to the area of the intersection, and aggregated according to `aggr_col_string`.

#### Parameters

theme_name
Table containing theme information (for example, demographic information).

theme_colname
Name of the column in the `theme_name` table that contains geometry objects.

aggr_type_string
Any Oracle SQL aggregate function that accepts one or more numeric values and computes a numeric value, such as `SUM`, `MIN`, `MAX`, or `AVG`.

aggr_col_string
Name of a column in the `theme_name` table on which to compute aggregate values. An example might be a POPULATION column.

tiling_level
Level to be used to create tiles. If you specify this parameter, the extent of each dimension is divided into 2^`tiling_level` parts, resulting in at most 4\*`tiling_level` tiles. (Specify either this parameter or the combination of the `xdivs` and `ydivs` parameters.)

tiling_domain
Domain for the tiling level. The parameter is not required, and if you do not specify it, the extent associated with the `theme_name` table is used.

zero_agg_tiles
Specify 0 to exclude tiles that have a value of 0 for the computed aggregate, or specify 1 to return all tiles. The default value is 0, which ensures that only tiles with a nonzero aggregate value are returned.

xdivs
The number of times that the extent in the first dimension is divided, such that the total number of parts is `xdivs` + 1. For example, if you specify 10 for `xdivs`, the extent of the first dimension is divided into 11 parts.

ydivs
The number of times that the extent in the second dimension is divided, such that the total number of parts is `ydivs` + 1. For example, if you specify 10 for `ydivs`, the extent of the second dimension is divided into 11 parts.

#### Usage Notes

This function is similar to SDO_SAM.AGGREGATES_FOR_LAYER, but the results are dynamically generated using tiling information. Given a `theme_name` table, the tiling domain is determined. Based on the `tiling_level` value or the `xdivs` and `ydivs` values, the necessary tiles are generated. For each tile geometry, thematic aggregates are computed as described in the Usage Notes for SDO_SAM.AGGREGATES_FOR_LAYER.

You must specify either the `tiling_level` parameter or both the `xdivs` and `ydivs` parameters. If you specify all three of these parameters, the `tiling_level` parameter is ignored and the `xdivs` and `ydivs` parameters are used.

If you specify the `xdivs` and `ydivs` parameters, the total number of grids (tiles) returned is `(xdivs+1)*(ydivs+1)`.

This function returns an object of type SDO_REGAGGRSET. The SDO_REGAGGRSET object type is defined as:

    TABLE OF SDO_REGAGGR

The SDO_REGAGGR object type is defined as:

     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     REGION_ID                                          VARCHAR2(24)
     GEOMETRY                                           MDSYS.SDO_GEOMETRY
     AGGREGATE_VALUE                                    NUMBER

#### Examples

The following example computes the sum of the population rows of POLY_4PT_TEMP table intersecting with each tile. The extent of the POLY_4PT_TEMP table stored in the USER_SDO_GEOM_METADATA view is used as the domain, and a tiling level of 2 is used (that is, the domain is divided into 16 tiles).

    SELECT a.geometry, a.aggregate_value
      from TABLE(sdo_sam.tiled_aggregates('POLY_4PT_TEMP',
                            'GEOMETRY', 'SUM', 'POPULATION', 2)) a;

    GEOMETRY(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
    AGGREGATE_VALUE
    ---------------
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-180, -90, -90, -45))
         .007150754

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-180, -45, -90, 0))
         .034831005

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-180, 0, -90, 45))
         7.73307783

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-90, -90, 0, -45))
         .019498368

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-90, -45, 0, 0))
         .939061456

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-90, 0, 0, 45))
         1.26691592

    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(0, 0, 90, 45))
                 40

    7 rows selected.

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)

### 31.10 SDO_SAM.TILED_BINS

#### Format

    SDO_SAM.TILED_BINS(
         l1           IN NUMBER,
         u1           IN NUMBER,
         l2           IN NUMBER,
         u2           IN NUMBER,
         tiling_level IN NUMBER DEFAULT NULL,
         srid         IN NUMBER DEFAULT NULL,
         xdivs        IN NUMBER DEFAULT NULL,
         ydivs        IN NUMBER DEFAULT NULL
         ) RETURN SDO_REGIONSET;

#### Description

Tiles a two-dimensional space and returns geometries corresponding to those tiles.

#### Parameters

l1
Lower bound of the extent in the first dimension.

u1
Upper bound of the extent in the first dimension.

l2
Lower bound of the extent in the second dimension.

u2
Upper bound of the extent in the second dimension.

tiling_level
Level to be used to tile the specified extent. If you specify this parameter, the extent of each dimension is divided into 2^`tiling_level` parts, resulting in at most 4\*`tiling_level` tiles. (Specify either this parameter or the combination of the `xdivs` and `ydivs` parameters.)

srid
SRID value to be included for the coordinate system in the returned tile geometries.

xdivs
The number of times that the extent in the first dimension is divided, such that the total number of parts is `xdivs` + 1. For example, if you specify 10 for `xdivs`, the extent of the first dimension is divided into 11 parts.

ydivs
The number of times that the extent in the second dimension is divided, such that the total number of parts is `ydivs` + 1. For example, if you specify 10 for `ydivs`, the extent of the second dimension is divided into 11 parts.

#### Usage Notes

You must specify either the `tiling_level` parameter or both the `xdivs` and `ydivs` parameters. If you specify all three of these parameters, the `tiling_level` parameter is ignored and the `xdivs` and `ydivs` parameters are used.

If you specify the `xdivs` and `ydivs` parameters, the total number of grids (tiles) returned is `(xdivs+1)*(ydivs+1)`.

This function returns an object of type SDO_REGIONSET. The SDO_REGIONSET object type is defined as:

    TABLE OF SDO_REGION

The SDO_REGION object type is defined as:

    Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                                 NUMBER
     GEOMETRY                                           MDSYS.SDO_GEOMETRY

#### Examples

The following example tiles the entire Earth's surface at the first tiling level, using the standard longitude and latitude coordinate system (SRID 8307). The resulting SDO_REGIONSET object contains four SDO_REGION objects, one for each tile.

    SELECT * FROM TABLE(sdo_sam.tiled_bins(-180, 180, -90, 90, 1, 8307))
      ORDER BY id;

            ID
    ----------
    GEOMETRY(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
             0
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-180, -90, 0, 0))

             1
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(-180, 0, 0, 90))

             2
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(0, -90, 180, 0))

             3
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(0, 0, 180, 90))

    4 rows selected.

**Parent topic:** SDO_SAM Package (Spatial Analysis and Mining)
