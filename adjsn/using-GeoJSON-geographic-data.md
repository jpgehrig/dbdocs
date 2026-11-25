GeoJSON objects are JSON objects that represent geographic data. Examples are provided of creating GeoJSON data, indexing it, and querying it.

### GeoJSON Objects: Geometry, Feature, Feature Collection

GeoJSON uses JSON objects that represent various geometrical entities and combinations of these together with user-defined properties.

A **position** is an array of two or more spatial (numerical) coordinates, the first three of which generally represent longitude, latitude, and altitude.

A **geometry** object has a `type` field and (except for a geometry-collection object) a `coordinates` field, as shown in Table 26-1.

A **geometry collection** is a geometry object with `type` `GeometryCollection`. Instead of a `coordinates` field it has a `geometries` field, whose value is an array of geometry objects other than `GeometryCollection` objects.

Table 26-1 GeoJSON Geometry Objects Other Than Geometry Collections

| `type` Field      | `coordinates` Field                                                                                                                                                                                                                                                  |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Point`           | A position.                                                                                                                                                                                                                                                          |
| `MultiPoint`      | An array of positions.                                                                                                                                                                                                                                               |
| `LineString`      | An array of two or more positions.                                                                                                                                                                                                                                   |
| `MultiLineString` | An array of `LineString` arrays of positions.                                                                                                                                                                                                                        |
| `Polygon`         | A `MultiLineString`, each of whose arrays is a `LineString` whose first and last positions coincide (are equivalent). If the array of a polygon contains more than one array then the first represents the outside polygon and the others represent holes inside it. |
| `MultiPolygon`    | An array of `Polygon` arrays, that is, multidimensional array of positions.                                                                                                                                                                                          |

A **feature** object has a `type` field of value `Feature`, a `geometry` field whose value is a geometric object, and a `properties` field whose value can be any JSON object.

A **feature collection** object has a `type` field of value `FeatureCollection`, and it has a `features` field whose value is an array of feature objects.

Example 26-1 presents a feature-collection object whose `features` array has three features. The `geometry` of the first feature is of type `Point`; that of the second is of type `LineString`; and that of the third is of type `Polygon`.

### Query and Index GeoJSON Data

You can use SQL/JSON query functions and conditions to examine GeoJSON data or to project parts of it as non-JSON data, including as Oracle Spatial and Graph `SDO_GEOMETRY` object-type instances. This is illustrated in Example 26-2, Example 26-3, and Example 26-5.

To improve query performance, you can create an Oracle Spatial and Graph index (type `MDSYS.SPATIAL_INDEX`) on function `json_value` applied to GeoJSON data. This is illustrated by Example 26-4.

Example 26-4 indexes only one particular element of an array of geometry features (the first element). A B-tree index on function `json_value` can target only a scalar value. To improve the performance of queries, such as that of Example 26-3, that target any number of array elements, you can do the following:

- Create an on-statement, refreshable materialized view of the array data, and place that view in memory.

- Create a spatial index on the array data.

This is shown in Example 26-6 and Example 26-7.

### SDO_GEOMETRY Object-Type Instances and Spatial Operations

You can convert Oracle Spatial and Graph `SDO_GEOMETRY` object-type instances to GeoJSON objects and GeoJSON objects to `SDO_GEOMETRY` instances.

You can use Oracle Spatial and Graph operations on `SDO_GEOMETRY` objects that you obtain from GeoJSON objects. For example, you can use operator `sdo_distance` in PL/SQL package `SDO_GEOM` to compute the minimum distance between two geometry objects. This is the distance between the closest two points or two segments, one point or segment from each object. This is illustrated by Example 26-5.

### JSON Data Guide Supports GeoJSON Data

A JSON data guide summarizes structural and type information contained in a set of JSON documents. If some of the documents contain GeoJSON data then that data is summarized in a data guide that you create using SQL aggregate function `json_dataguide`. If you use SQL function `json_dataguide` to create a view based on such a data guide, and you specify the formatting argument as `DBMS_JSON.GEOJSON` or `DBMS_JSON.GEOJSON+DBMS_JSON.PRETTY`, then a column that projects GeoJSON data from the document set is of SQL data type `SDO_GEOMETRY`.

**See Also:**

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about using GeoJSON data with Oracle Spatial and Graph

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about Oracle Spatial and Graph and `SDO_GEOMETRY` object type

- [GeoJSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=geojson_org) for information about GeoJSON

- [The GeoJSON Format Specification](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=geojson_spec) for details about GeoJSON data

Example 26-1 A Table With GeoJSON Data

This example creates table `j_geo`, which has a column, `geo_doc` of GeoJSON documents.

Only one such document is inserted here. It contains a GeoJSON object of `type` `FeatureCollection`, and a `features` array of objects of `type` `Feature`. Those objects have `geometry`, respectively, of `type` `Point`, `LineString`, and `Polygon`.

    CREATE TABLE j_geo
      (id      VARCHAR2 (32) NOT NULL,
       geo_doc VARCHAR2 (4000) CHECK (geo_doc is json));

    INSERT INTO j_geo
      VALUES (1,
              '{"type"     : "FeatureCollection",
                "features" : [{"type"       : "Feature",
                               "geometry"   : {"type" : "Point",
                                               "coordinates" : [-122.236111, 37.482778]},
                               "properties" : {"Name" : "Redwood City"}},
                              {"type"       : "Feature",
                               "geometry"   : {"type" : "LineString",
                                               "coordinates" : [[102.0, 0.0],
                                                                [103.0, 1.0],
                                                                [104.0, 0.0],
                                                                [105.0, 1.0]]},
                               "properties" : {"prop0" : "value0",
                                               "prop1" : 0.0}},
                              {"type"       : "Feature",
                               "geometry"   : {"type" : "Polygon",
                                               "coordinates" : [[[100.0, 0.0],
                                                                 [101.0, 0.0],
                                                                 [101.0, 1.0],
                                                                 [100.0, 1.0],
                                                                 [100.0, 0.0]]]},
                               "properties" : {"prop0" : "value0",
                                               "prop1" : {"this" : "that"}}}]}');

Example 26-2 Selecting a geometry Object From a GeoJSON Feature As an SDO_GEOMETRY Instance

This example uses SQL/JSON function `json_value` to select the value of field `geometry` from the first element of array `features`. The value is returned as Oracle Spatial and Graph data, not as JSON data, that is, as an instance of PL/SQL object type `SDO_GEOMETRY`, not as a SQL string or LOB instance.

    SELECT json_value(geo_doc, '$.features[0].geometry'
                      RETURNING SDO_GEOMETRY
                      ERROR ON ERROR)
      FROM j_geo;

The value returned is this, which represents a point with longitude and latitude (coordinates) -122.236111 and 37.482778, respectively.

    SDO_GEOMETRY(2001,
                 4326,
                 SDO_POINT_TYPE(-122.236111, 37.482778, NULL),
                 NULL,
                 NULL)

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_VALUE.md) for information about SQL/JSON function `json_value`

Example 26-3 Retrieving Multiple geometry Objects From a GeoJSON Feature As SDO_GEOMETRY

This example uses SQL/JSON function `json_table` to project the value of field `geometry` from each element of array `features`, as column `sdo_val` of a virtual table. The retrieved data is returned as `SDO_GEOMETRY`.

    SELECT jt.*
      FROM j_geo,
           json_table(geo_doc, '$.features[*]'
             COLUMNS (sdo_val SDO_GEOMETRY PATH '$.geometry')) jt;

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md) for information about SQL/JSON function `json_table`

The following three rows are returned for the query. The first represents the same `Point` as in Example 26-2. The second represents the `LineString` array. The third represents the `Polygon`.

    SDO_GEOMETRY(2001,
                 4326,
                 SDO_POINT_TYPE(-122.236111, 37.482778, NULL),
                 NULL,
                 NULL)

    SDO_GEOMETRY(2002,
                 4326,
                 NULL,
                 SDO_ELEM_INFO_ARRAY(1, 2, 1),
                 SDO_ORDINATE_ARRAY(102, 0, 103, 1, 104, 0, 105, 1))

    SDO_GEOMETRY(2003,
                 4326,
                 NULL,
                 SDO_ELEM_INFO_ARRAY(1, 1003, 1),
                 SDO_ORDINATE_ARRAY(100, 0, 101, 0, 101, 1, 100, 1, 100, 0))

The second and third elements of attribute `SDO_ELEM_INFO_ARRAY` specify how to interpret the coordinates provided by attribute `SDO_ORDINATE_ARRAY`. They show that the first row returned represents a line string (2) with straight segments (1), and the second row represents a polygon (2003) of straight segments (1).

Example 26-4 Creating a Spatial Index For Scalar GeoJSON Data

This example creates a `json_value` function-based index of type `MDSYS.SPATIAL_INDEX` on field `geometry` of the first element of array `features`. This can improve the performance of queries that use `json_value` to retrieve that value.

    CREATE INDEX geo_first_feature_idx
      ON j_geo (json_value(geo_doc, '$.features[0].geometry'
                           RETURNING SDO_GEOMETRY))
      INDEXTYPE IS MDSYS.SPATIAL_INDEX;

Example 26-5 Using GeoJSON Geometry With Spatial Operators

This example selects the documents (there is only one in this table) for which the `geometry` field of the first `features` element is within 100 kilometers of a given point. The point is provided literally here (its `coordinates` are the longitude and latitude of San Francisco, California). The distance is computed from this point to each geometry object.

The query orders the selected documents by the calculated distance. The tolerance in meters for the distance calculation is provided in this query as the literal argument 100.

    SELECT id,
           json_value(geo_doc, '$.features[0].properties.Name') "Name",
           SDO_GEOM.sdo_distance(
             json_value(geo_doc, '$.features[0].geometry'
                        RETURNING SDO_GEOMETRY),
             SDO_GEOMETRY(2001,
                          4326,
                          SDO_POINT_TYPE(-122.416667, 37.783333, NULL),
                          NULL,
                          NULL),
             100, -- Tolerance in meters
             'unit=KM') "Distance in kilometers"
      FROM  j_geo
      WHERE sdo_within_distance(
              json_value(geo_doc, '$.features[0].geometry'
                         RETURNING SDO_GEOMETRY),
              SDO_GEOMETRY(2001,
                           4326,
                           SDO_POINT_TYPE(-122.416667, 37.783333, NULL),
                           NULL,
                           NULL),
              'distance=100 unit=KM')
            = 'TRUE';

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_VALUE.md) for information about SQL/JSON function `json_value`

The query returns a single row:

    ID    Name           Distance in kilometers
    ----- -------------- ----------------------
    1     Redwood City   26.9443035

Example 26-6 Creating a Materialized View Over GeoJSON Data

    CREATE OR REPLACE MATERIALIZED VIEW geo_doc_view
      BUILD IMMEDIATE
      REFRESH FAST ON STATEMENT WITH ROWID
      AS SELECT g.rowid, jt.*
           FROM j_geo g,
                json_table(geo_doc, '$.features[*]'
                  COLUMNS (sdo_val SDO_GEOMETRY PATH '$.geometry')) jt;

Example 26-7 Creating a Spatial Index on a Materialized View Over GeoJSON Data

This example first prepares for the creation of the spatial index by populating some spatial-indexing metadata. It then creates the index on the `SDO_GEOMETRY` column, `sdo_val`, of materialized view `geo_doc_view`, which is created in Example 26-6. Except for the view and column names, the code for populating the indexing metadata is fixed — use it each time you need to create a spatial index on a materialized view.

    -- Populate spatial-indexing metadata

    INSERT INTO USER_SDO_GEOM_METADATA
      VALUES ('GEO_DOC_VIEW',
              'SDO_VAL',
              MDSYS.sdo_dim_array(
                MDSYS.sdo_dim_element('Longitude', -180, 180, 0.05),
                MDSYS.sdo_dim_element('Latitude', -90, 90, 0.05)),
              7
              4326);

    -- Create spatial index on geometry column of materialized view

    CREATE INDEX geo_all_features_idx ON geo_doc_view(sdo_val)
      INDEXTYPE IS MDSYS.SPATIAL_INDEX V2;

**Related Topics**

- [Creating a View Over JSON Data Using JSON_TABLE](function-JSON_TABLE.md)
- [JSON Data-Guide Fields](json-dataguide.md)

**Parent topic:** [GeoJSON Geographic Data](GeoJSON-geographic-data.md)
