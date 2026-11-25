## 21  Spatial Aggregate Functions

This chapter contains reference and usage information for the spatial aggregate functions.

See the usage information about spatial aggregate functions in [Spatial Aggregate Functions](spatial-concepts.md).

Most of these aggregate functions accept a parameter of type SDOAGGRTYPE, which is described in [SDOAGGRTYPE Object Type](spatial-concepts.md).

**Note:**

Spatial aggregate functions are supported for two-dimensional geometries only, except for SDO_AGGR_MBR, which is supported for both two-dimensional and three-dimensional geometries.

- SDO_AGGR_CENTROID
- SDO_AGGR_CONCAT_LINES
- SDO_AGGR_CONCAVEHULL
- SDO_AGGR_CONVEXHULL
- SDO_AGGR_LRS_CONCAT
- SDO_AGGR_MBR
- SDO_AGGR_SET_UNION
- SDO_AGGR_UNION

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 21.1 SDO_AGGR_CENTROID

#### Format

    SDO_AGGR_CENTROID(
         AggregateGeometry  SDOAGGRTYPE
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object that is the centroid ("center of gravity") of the specified geometry objects.

#### Parameters

AggregateGeometry
An object of type SDOAGGRTYPE (see [SDOAGGRTYPE Object Type](spatial-concepts.md)) that specifies the geometry column and dimensional array.

#### Usage Notes

The behavior of the function depends on whether the geometry objects are all polygons, all points, or a mixture of polygons and points:

- If the geometry objects are all polygons, the centroid of all the objects is returned.

- If the geometry objects are all points, the centroid of all the objects is returned.

- If the geometry objects are a mixture of polygons and points (specifically, if they include at least one polygon and at least one point), any points are ignored, and the centroid of all the polygons is returned.

The result is weighted by the area of each polygon in the geometry objects. If the geometry objects are a mixture of polygons and points, the points are not used in the calculation of the centroid. If the geometry objects are all points, the points have equal weight.

See also the information about the [SDO_GEOM.SDO_CENTROID](SDO_GEOM-reference.md) function in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md).

#### Examples

The following example returns the centroid of the geometry objects in the COLA_MARKETS table. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT SDO_AGGR_CENTROID(SDOAGGRTYPE(shape, 0.005))
      FROM cola_markets;

    SDO_AGGR_CENTROID(SDOAGGRTYPE(SHAPE,0.005))(SDO_GTYPE, SDO_SRID, SDO_POINT
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(5.21295938, 5.00744233, NULL), NULL, NUL
    L)

**Parent topic:** Spatial Aggregate Functions

### 21.2 SDO_AGGR_CONCAT_LINES

#### Format

    SDO_AGGR_CONCAT_LINES(
         geom  SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry that concatenates the specified line or multiline geometries.

#### Parameters

geom
Geometry objects.

#### Usage Notes

Each input geometry must be a two-dimensional line or multiline geometry (that is, the SDO_GTYPE value must be 2002 or 2006). This function is not supported for LRS geometries. To perform an aggregate concatenation of LRS geometric segments, use the SDO_AGGR_LRS_CONCAT spatial aggregate function.

The input geometries must be line strings whose vertices are connected by straight line segments. Circular arcs and compound line strings are not supported.

If any input geometry is a multiline geometry, the elements of the geometry must be disjoint. If they are not disjoint, this function may return incorrect results.

The topological relationship between the geometries in each pair of geometries to be concatenated must be DISJOINT or TOUCH; and if the relationship is TOUCH, the geometries must intersect only at two end points.

You can use the [SDO_UTIL.CONCAT_LINES](SDO_UTIL-reference.md) function (described in [SDO_UTIL Package (Utility)](SDO_UTIL-reference.md)) to concatenate two line or multiline geometries.

An exception is raised if any input geometries are not line or multiline geometries, or if not all input geometries are based on the same coordinate system.

#### Examples

The following example inserts two line geometries in the COLA_MARKETS table, and then returns the aggregate concatenation of these geometries. (The example uses the data definitions from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    -- First, insert two line geometries.
    INSERT INTO cola_markets VALUES(1001, 'line_1', SDO_GEOMETRY(2002, NULL, NULL,
      SDO_ELEM_INFO_ARRAY(1,2,1), SDO_ORDINATE_ARRAY(1,1, 5,1)));
    INSERT INTO cola_markets VALUES(1002, 'line_2', SDO_GEOMETRY(2002, NULL, NULL,
      SDO_ELEM_INFO_ARRAY(1,2,1), SDO_ORDINATE_ARRAY(5,1, 8,1)));
    -- Perform aggregate concatenation of all line geometries in layer.
    SELECT SDO_AGGR_CONCAT_LINES(c.shape) FROM cola_markets c
       WHERE c.mkt_id > 1000;

    SDO_AGGR_CONCAT_LINES(C.SHAPE)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    1, 1, 5, 1, 8, 1))

**Parent topic:** Spatial Aggregate Functions

### 21.3 SDO_AGGR_CONCAVEHULL

#### Format

    SDO_AGGR_CONCAVEHULL(
         AggregateGeometry  SDOAGGRTYPE
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object that is the concave hull of the specified geometry objects.

#### Parameters

AggregateGeometry
An object of type SDOAGGRTYPE (see [SDOAGGRTYPE Object Type](spatial-concepts.md)) that specifies the geometry column and dimensional array.

#### Usage Notes

See also the information about the [SDO_GEOM.SDO_CONCAVEHULL](SDO_GEOM-reference.md) function in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md).

#### Examples

The following example returns the concave hull of the geometry objects in the COLA_MARKETS table. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT SDO_AGGR_CONCAVEHULL(SDOAGGRTYPE(shape, 0.005))
      FROM cola_markets;

    SDO_AGGR_CONCAVEHULL(SDOAGGRTYPE(SHAPE,0.005))(SDO_GTYPE, SDO_SRID, SDO_POINT(X,
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3, 3, 5, 1, 8, 1, 10, 1, 12, 1, 14, 1, 14, 5, 13, 9, 14, 10, 14, 13, 12, 15,
    10, 14, 10, 13, 8, 11, 6, 12, 5, 13, 2, 11, 6, 10, 6, 9, 5, 7, 4, 5, 2, 4, 3, 3)
    )

**Parent topic:** Spatial Aggregate Functions

### 21.4 SDO_AGGR_CONVEXHULL

#### Format

    SDO_AGGR_CONVEXHULL(
         AggregateGeometry  SDOAGGRTYPE
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object that is the convex hull of the specified geometry objects.

#### Parameters

AggregateGeometry
An object of type SDOAGGRTYPE (see [SDOAGGRTYPE Object Type](spatial-concepts.md)) that specifies the geometry column and dimensional array.

#### Usage Notes

See also the information about the [SDO_GEOM.SDO_CONVEXHULL](SDO_GEOM-reference.md) function in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md).

#### Examples

The following example returns the convex hull of the geometry objects in the COLA_MARKETS table. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT SDO_AGGR_CONVEXHULL(SDOAGGRTYPE(shape, 0.005))
      FROM cola_markets;

    SDO_AGGR_CONVEXHULL(SDOAGGRTYPE(SHAPE,0.005))(SDO_GTYPE, SDO_SRID, SDO_POI
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(8, 1, 10, 7, 10, 11, 8, 11, 6, 11, 1, 7, 1, 1, 8, 1))

**Parent topic:** Spatial Aggregate Functions

### 21.5 SDO_AGGR_LRS_CONCAT

#### Format

    SDO_AGGR_LRS_CONCAT(
         AggregateGeometry  SDOAGGRTYPE
         ) RETURN SDO_GEOMETRY;

#### Description

Returns an LRS geometry that concatenates specified LRS geometries.

#### Parameters

AggregateGeometry
An object of type SDOAGGRTYPE (see [SDOAGGRTYPE Object Type](spatial-concepts.md)) that specifies the geometry column and dimensional array.

#### Usage Notes

This function performs an aggregate concatenation of any number of LRS geometries. If you want to control the order in which the geometries are concatenated, you must use a subquery with the NO_MERGE optimizer hint and the ORDER BY clause. (See the examples.)

The direction of the resulting segment is the same as the direction of the first geometry in the concatenation.

A 3D format of this function (SDO_AGGR_LRS_CONCAT_3D) is available. For information about 3D formats of LRS functions, see [3D Formats of LRS Functions](lrs-linear-referencing-system-concepts.md).)

For information about the Spatial and Graph linear referencing system, see [Linear Referencing System](lrs-linear-referencing-system-concepts.md).

#### Examples

The following example adds an LRS geometry to the LRS_ROUTES table, and then performs two queries that concatenate the LRS geometries in the table. The first query does not control the order of concatenation, and the second query controls the order of concatenation. Notice the difference in direction of the two segments: the segment resulting from the second query has decreasing measure values because the first segment in the concatenation (`Route0`) has decreasing measure values. (This example uses the definitions from the example in [Example of LRS Functions](lrs-linear-referencing-system-concepts.md).)

    -- Add a segment with route_id less than 1 (here, zero).
    INSERT INTO lrs_routes VALUES(
      0,
      'Route0',
      SDO_GEOMETRY(
        3302,  -- Line string; 3 dimensions (X,Y,M); 3rd is measure dimension.
        NULL,
        NULL,
        SDO_ELEM_INFO_ARRAY(1,2,1), -- One line string, straight segments
        SDO_ORDINATE_ARRAY(
          5,14,5,   -- Starting point - 5 is measure from start.
          10,14,0)  -- Ending point - 0 measure (decreasing measure)
      )
    );

    1 row created.

    -- Concatenate all routes (no ordering specified).
    SELECT SDO_AGGR_LRS_CONCAT(SDOAGGRTYPE(route_geometry, 0.005))
        FROM lrs_routes;

    SDO_AGGR_LRS_CONCAT(SDOAGGRTYPE(ROUTE_GEOMETRY,0.005))(SDO_GTYPE, SDO_SRID
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(3302, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    2, 2, 0, 2, 4, 2, 8, 4, 8, 12, 4, 12, 12, 10, 18, 8, 10, 22, 5, 14, 27, 10, 14,
    32))

    -- Aggregate concatenation using subquery for ordering.
    SELECT
    SDO_AGGR_LRS_CONCAT(SDOAGGRTYPE(route_geometry, 0.005))
    FROM (
                 SELECT /*+ NO_MERGE */ route_geometry
                 FROM lrs_routes
                 ORDER BY route_id);

    SDO_AGGR_LRS_CONCAT(SDOAGGRTYPE(ROUTE_GEOMETRY,0.005))(SDO_GTYPE, SDO_SRID
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(3302, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    2, 2, 32, 2, 4, 30, 8, 4, 24, 12, 4, 20, 12, 10, 14, 8, 10, 10, 5, 14, 5, 10, 14
    , 0))

**Parent topic:** Spatial Aggregate Functions

### 21.6 SDO_AGGR_MBR

#### Format

    SDO_AGGR_MBR(
         geom  SDO_GEOMETRY
         ) RETURN SDO_GEOMETRY;

#### Description

Returns the minimum bounding rectangle (MBR) of the specified geometries, that is, a single rectangle that minimally encloses the geometries.

#### Parameters

geom
Geometry objects.

#### Usage Notes

**Note:**

SDO_AGGR_MBR function is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

This function does not return an MBR geometry if a proper MBR cannot be constructed. Specifically:

- If the input geometries are all null, the function returns a null geometry.

- If all data in the input geometries is on a single point, the function returns the point.

- If all data in the input geometries consists of points on a straight line, the function returns a two-point line.

The [SDO_TUNE.EXTENT_OF](SDO_TUNE-reference.md) function, documented in [SDO_TUNE Package (Tuning)](SDO_TUNE-reference.md), also returns the MBR of geometries. The [SDO_TUNE.EXTENT_OF](SDO_TUNE-reference.md) function has better performance than the SDO_AGGR_MBR function if a spatial index is defined on the geometry column; however, the [SDO_TUNE.EXTENT_OF](SDO_TUNE-reference.md) function is limited to two-dimensional geometries, whereas the SDO_AGGR_MBR function is not. In addition, the [SDO_TUNE.EXTENT_OF](SDO_TUNE-reference.md) function computes the extent for all geometries in a table; by contrast, the SDO_AGGR_MBR function can operate on subsets of rows.

#### Examples

The following example returns the minimum bounding rectangle of the geometry objects in the COLA_MARKETS table. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT SDO_AGGR_MBR(shape) FROM cola_markets;

    SDO_AGGR_MBR(C.SHAPE)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SD
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARR
    AY(1, 1, 10, 11))

**Parent topic:** Spatial Aggregate Functions

### 21.7 SDO_AGGR_SET_UNION

#### Format (as Function in SDO_AGGR Package)

    SDO_AGGR.SDO_AGGR_SET_UNION(
         geometry SDO_GEOMETRY_ARRAY,
         tol      NUMBER
         ) RETURN SDO_GEOMETRY;

or

    SDO_AGGR.SDO_AGGR_SET_UNION(
         cur  SYS_REFCURSOR,
         tol  NUMBER      
         ) RETURN SDO_GEOMETRY;

#### Format (as Spatial Aggregate Function \[Deprecated\])

    SDO_AGGR_SET_UNION(
         geometry  SDO_GEOMETRY_ARRAY,
         tol       NUMBER
         ) RETURN SDO_GEOMETRY;

#### Description

Returns the aggregate union of all the geometry objects from an input VARRAY of SDO_GEOMETRY objects or a REF cursor.

#### Parameters

geometry
An array of geometry objects of object type SDO_GEOMETRY_ARRAY, which is defined as `VARRAY OF SDO_GEOMETRY`.

cur
A REF cursor that returns a set of the geometry objects for which to return the aggregate union of all the geometry objects.

tol
Tolerance value (see [Tolerance](spatial-concepts.md)).

#### Usage Notes

**Note:**

Effective with Oracle Database Release 12c (12.1), the format as a spatial aggregate function is deprecated, and will be removed in an upcoming major release.

You should instead use one of the formats for the SDO_AGGR.SDO_AGGR_SET_UNION function.

SDO_AGGR_SET_UNION provides faster performance than SDO_AGGR_UNION but less flexibility, and SDO_AGGR_SET_UNION should be considered when performance is especially important and when it satisfies your functional needs.

SDO_AGGR_UNION is a SQL aggregate function, and therefore it is very flexible and can be used with complex SQL GROUP BY clauses. However, SDO_AGGR_SET_UNION can be much faster than SDO_AGGR_UNION. SDO_AGGR_SET_UNION is useful when the geometries to be grouped can easily be gathered into a collection, such as a VARRAY of SDO_GEOMETRY objects).

SDO_AGGR_SET_UNION:

- Cannot aggregate a set of overlapping polygons. For overlapping polygons, use SDO_AGGR_UNION.

- Can effectively aggregate a set of non-overlapping polygons, including polygons that touch.

- Can aggregate sets of lines and points, even if they overlap.

#### Examples

The following example creates a generic routine to build a geometry set to pass to SDO_AGGR_SET_UNION. It takes as input a table name, column name, and optional predicate to apply, and returns an SDO_GEOMETRY_ARRAY ready to use with SDO_AGGR_SET_UNION. The first SELECT statement after the `get_geom_set` function creation calls the SDO_AGGR.SDO_AGGR_UNION PL/SQL function, the second SELECT statement calls the deprecated spatial aggregate function, and the third SELECT statement calls the SDO_AGGR.SDO_AGGR_UNION PL/SQL function using the format that specifies a cursor. All the SELECT statements return the same result. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    CREATE OR REPLACE FUNCTION get_geom_set (table_name  VARCHAR2,
                                             column_name VARCHAR2,
                                             predicate   VARCHAR2 := NULL)
      RETURN SDO_GEOMETRY_ARRAY DETERMINISTIC AS

      type            cursor_type is REF CURSOR;
      query_crs       cursor_type ;
      g               SDO_GEOMETRY;
      GeometryArr     SDO_GEOMETRY_ARRAY;
      where_clause    VARCHAR2(2000);
    BEGIN
      IF predicate IS NULL
      THEN
        where_clause := NULL;
      ELSE
        where_clause := ' WHERE ';
      END IF;

      GeometryArr := SDO_GEOMETRY_ARRAY();
      OPEN query_crs FOR ' SELECT ' || column_name ||
                         ' FROM ' || table_name ||
                           where_clause || predicate;
       LOOP
        FETCH query_crs into g;
         EXIT when query_crs%NOTFOUND ;
         GeometryArr.extend;
         GeometryArr(GeometryArr.count) := g;
       END LOOP;
       RETURN GeometryArr;
    END;
    /

    -- Call SDO_AGGR_SET_UNION function in SDO_AGGR PL/SQL package.
    SELECT sdo_aggr.sdo_aggr_set_union (get_geom_set ('COLA_MARKETS', 'SHAPE',
      'name <> ''cola_c'''), .0005 ) FROM dual;

    SDO_AGGR.SDO_AGGR_SET_UNION(GET_GEOM_SET('COLA_MARKETS','SHAPE','NAME<>''COLA_C'
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2007, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 2, 11, 1003, 1), SDO
    _ORDINATE_ARRAY(8, 11, 6, 9, 8, 7, 10, 9, 8, 11, 1, 7, 1, 1, 5, 1, 8, 1, 8, 6, 5
    , 7, 1, 7))

    -- CALL SDO_AGGR_SET_UNION spatial aggregate function (deprecated format).
    SELECT sdo_aggr_set_union (get_geom_set ('COLA_MARKETS', 'SHAPE',
      'name <> ''cola_c'''), .0005 ) FROM dual;

    SDO_AGGR.SDO_AGGR_SET_UNION(GET_GEOM_SET('COLA_MARKETS','SHAPE','NAME<>''COLA_C'
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2007, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 2, 11, 1003, 1), SDO
    _ORDINATE_ARRAY(8, 11, 6, 9, 8, 7, 10, 9, 8, 11, 1, 7, 1, 1, 5, 1, 8, 1, 8, 6, 5
    , 7, 1, 7))

    -- Call SDO_AGGR_SET_UNION function in SDO_AGGR PL/SQL package; specify
    -- a cursor as input.
    SELECT sdo_aggr.sdo_aggr_set_union
      (CURSOR(SELECT shape FROM COLA_MARKETS WHERE name <> 'cola_c'), .0005 )
      FROM dual;

    SDO_AGGR.SDO_AGGR_SET_UNION(CURSOR(SELECTSHAPEFROMCOLA_MARKETSWHERENAME<>'COLA_C
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2007, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 2, 11, 1003, 1), SDO
    _ORDINATE_ARRAY(8, 11, 6, 9, 8, 7, 10, 9, 8, 11, 1, 7, 1, 1, 5, 1, 8, 1, 8, 6, 5
    , 7, 1, 7))

**Parent topic:** Spatial Aggregate Functions

### 21.8 SDO_AGGR_UNION

#### Format

    SDO_AGGR_UNION(
         AggregateGeometry  SDOAGGRTYPE
         ) RETURN SDO_GEOMETRY;

#### Description

Returns a geometry object that is the topological union (OR operation) of the specified geometry objects.

#### Parameters

AggregateGeometry
An object of type SDOAGGRTYPE (see [SDOAGGRTYPE Object Type](spatial-concepts.md)) that specifies the geometry column and dimensional array.

#### Usage Notes

Do not use SDO_AGGR_UNION to merge line string or multiline string geometries; instead, use the SDO_AGGR_CONCAT_LINES spatial aggregate function.

See also the information about the [SDO_GEOM.SDO_UNION](SDO_GEOM-reference.md) function in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md).

#### Examples

The following example returns the union of all geometries except `cola_d` (in this case, `cola_a`, `cola_b`, and `cola_c`). (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT SDO_AGGR_UNION(
      SDOAGGRTYPE(c.shape, 0.005))
      FROM cola_markets c
      WHERE c.name <> 'cola_d';

    SDO_AGGR_UNION(SDOAGGRTYPE(C.SHAPE,0.005))(SDO_GTYPE, SDO_SRID, SDO_POINT(
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2007, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 2, 11, 1003, 1), SDO
    _ORDINATE_ARRAY(8, 11, 6, 9, 8, 7, 10, 9, 8, 11, 1, 7, 1, 1, 5, 1, 8, 1, 8, 6, 5
    , 7, 1, 7))

**Parent topic:** Spatial Aggregate Functions
