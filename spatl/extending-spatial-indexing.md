## 10  Extending Spatial Indexing Capabilities

This chapter shows how to create and use spatial indexes on objects other than a geometry column. In other chapters, the focus is on indexing and querying spatial data that is stored in a single column of type SDO_GEOMETRY.

This chapter shows how to:

- Embed an SDO_GEOMETRY object in a user-defined object type, and index the geometry attribute of that type

- Create and use a function-based index where the function returns an SDO_GEOMETRY object

The techniques in this chapter are intended for experienced and knowledgeable application developers. You should be familiar with the Spatial and Graph concepts and techniques described in other chapters. You should also be familiar with, or able to learn about, relevant Oracle database features, such as user-defined data types and function-based indexing.

- SDO_GEOMETRY Objects in User-Defined Type Definitions
  The SDO_GEOMETRY type can be embedded in a user-defined data type definition.
- SDO_GEOMETRY Objects in Function-Based Indexes
  A function-based spatial index facilitates queries that use location information (of type SDO_GEOMETRY) returned by a function or expression. In this case, the spatial index is created based on the precomputed values returned by the function or expression.

**Parent topic:** [Conceptual and Usage Information](spatial-concepts-usage.md)

### 10.1 SDO_GEOMETRY Objects in User-Defined Type Definitions

The SDO_GEOMETRY type can be embedded in a user-defined data type definition.

The procedure is very similar to that for using the SDO_GEOMETRY type for a spatial data column:

1.  Create the user-defined data type.

2.  Create a table with a column based on that data type.

3.  Insert data into the table.

4.  Update the USER_SDO_GEOM_METADATA view.

5.  Create the spatial index on the geometry attribute.

6.  Perform queries on the data.

For example, assume that you want to follow the cola markets scenario in the simplified example in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md), but want to incorporate the market name attribute and the geometry attribute in a single type. First, create the user-defined data type, as in the following example that creates an object type named MARKET_TYPE:

    CREATE OR REPLACE TYPE market_type AS OBJECT
      (name VARCHAR2(32), shape SDO_GEOMETRY);
    /

Create a table that includes a column based on the user-defined type. The following example creates a table named COLA_MARKETS_2 that will contain the same information as the COLA_MARKETS table used in the example in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).

    CREATE TABLE cola_markets_2 (
      mkt_id NUMBER PRIMARY KEY,
      market MARKET_TYPE);

Insert data into the table, using the object type name as a constructor. For example:

    INSERT INTO cola_markets_2 VALUES(
      1,
      MARKET_TYPE('cola_a',
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3), -- one rectangle (1003 = exterior)
          SDO_ORDINATE_ARRAY(1,1, 5,7) -- only 2 points needed to
                -- define rectangle (lower left and upper right)
          )
      )
    );

Update the USER_SDO_GEOM_METADATA view, using dot-notation to specify the column name and spatial attribute. The following example specifies MARKET.SHAPE as the COLUMN_NAME (explained in [COLUMN_NAME](spatial-datatypes-metadata.md)) in the metadata view.

    INSERT INTO user_sdo_geom_metadata
        (TABLE_NAME,
         COLUMN_NAME,
         DIMINFO,
         SRID)
      VALUES (
      'cola_markets_2',
      'market.shape',
      SDO_DIM_ARRAY(   -- 20X20 grid
        SDO_DIM_ELEMENT('X', 0, 20, 0.005),
        SDO_DIM_ELEMENT('Y', 0, 20, 0.005)
         ),
      NULL   -- SRID
    );

Create the spatial index, specifying the column name and spatial attribute using dot-notation. For example.

    CREATE INDEX cola_spatial_idx_2
    ON cola_markets_2(market.shape)
    INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2;

Perform queries on the data, using dot-notation to refer to attributes of the user-defined type. The following simple query returns information associated with the cola market named `cola_a`.

    SELECT c.mkt_id, c.market.name, c.market.shape
      FROM cola_markets_2 c
      WHERE c.market.name = 'cola_a';

The following query returns information associated with all geometries that have any spatial interaction with a specified query window, namely, the rectangle with lower-left coordinates (4,6) and upper-right coordinates (8,8).

    SELECT c.mkt_id, c.market.name, c.market.shape
      FROM cola_markets_2 c
      WHERE SDO_RELATE(c.market.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(4,6, 8,8)),
                'mask=anyinteract' = 'TRUE';

**Parent topic:** Extending Spatial Indexing Capabilities

### 10.2 SDO_GEOMETRY Objects in Function-Based Indexes

A function-based spatial index facilitates queries that use location information (of type SDO_GEOMETRY) returned by a function or expression. In this case, the spatial index is created based on the precomputed values returned by the function or expression.

If you are not already familiar with function-based indexes, see the following for detailed explanations of their benefits, options, and requirements, as well as usage examples:

- [Oracle Database Development Guide](../adfns/indexes.md)

- [Oracle Database Administrator's Guide](../admin/managing-indexes.md)

The procedure for using an SDO_GEOMETRY object in a function-based index is as follows:

1.  Create the function that returns an SDO_GEOMETRY object.

    The function must be declared as DETERMINISTIC.

2.  If the spatial data table does not already exist, create it, and insert data into the table.

3.  Update the USER_SDO_GEOM_METADATA view.

4.  Create the spatial index.

    For a function-based spatial index, the number of parameters must not exceed 32.

5.  Perform queries on the data.

The rest of this section describes two examples of using function-based indexes. In both examples, a function is created that returns an SDO_GEOMETRY object, and a spatial index is created on that function. In the first example, the input parameters to the function are a standard Oracle data type (NUMBER). In the second example, the input to the function is a user-defined object type.

- Example: Function with Standard Types
- Example: Function with a User-Defined Object Type

**Parent topic:** Extending Spatial Indexing Capabilities

#### 10.2.1 Example: Function with Standard Types

In the following example, the input parameters to the function used for the function-based index are standard numeric values (longitude and latitude).

Assume that you want to create a function that returns the longitude and latitude of a point and to use that function in a spatial index. First, create the function, as in the following example that creates a function named get_long_lat_pt:

    -- Create a function to return a point geometry (SDO_GTYPE = 2001) with
    -- input of 2 numbers: longitude and latitude (SDO_SRID = 8307, for
    -- "Longitude / Latitude (WGS 84)",  probably the most widely used
    --  coordinate system, and the one used for GPS devices.
    -- Specify DETERMINISTIC for the function.

    CREATE OR REPLACE FUNCTION get_long_lat_pt(longitude IN NUMBER,
                                               latitude IN NUMBER)
    RETURN SDO_GEOMETRY DETERMINISTIC IS
    BEGIN
         IF (longitude IS NULL) OR (latitude IS NULL) THEN
             RETURN NULL;
         END IF;
         RETURN SDO_GEOMETRY(2001, 8307,
                    SDO_POINT_TYPE(longitude, latitude, NULL),NULL, NULL);
    END;
    /

If the spatial data table does not already exist, create the table and add data to it, as in the following example that creates a table named long_lat_table:

    CREATE TABLE long_lat_table
    (lon NUMBER, lat NUMBER, name VARCHAR2(32));

    INSERT INTO long_lat_table VALUES (10,10, 'Place1');
    INSERT INTO long_lat_table VALUES (20,20, 'Place2');
    INSERT INTO long_lat_table VALUES (30,30, 'Place3');

Update the USER_SDO_GEOM_METADATA view, using dot-notation to specify the schema name and function name. The following example specifies SCOTT.GET_LONG_LAT_PT(LON,LAT) as the COLUMN_NAME (explained in [COLUMN_NAME](spatial-datatypes-metadata.md)) in the metadata view.

    -- Set up the metadata entry for this table.
    -- The column name sets up the function on top
    -- of the two columns used in this function,
    -- along with the owner of the function.
    INSERT INTO USER_SDO_GEOM_METADATA VALUES('LONG_LAT_TABLE',
     'scott.get_long_lat_pt(lon,lat)',
     SDO_DIM_ARRAY(
       SDO_DIM_ELEMENT('Longitude', -180, 180, 0.005),
       SDO_DIM_ELEMENT('Latitude', -90, 90, 0.005)), 8307);

Create the spatial index, specifying the function name with parameters. For example:

    CREATE INDEX long_lat_table_idx ON
       long_lat_table(get_long_lat_pt(lon,lat))
       INDEXTYPE IS mdsys.spatial_index_v2;

Perform queries on the data. The following example specifies the user-defined function in a call to the [SDO_FILTER](spatial-operators-reference.md) operator.

    SELECT NAME FROM long_lat_table a
      WHERE SDO_FILTER(
        get_long_lat_pt(a.lon,a.lat),
        SDO_GEOMETRY(2001, 8307, SDO_POINT_TYPE(10,10,NULL), NULL, NULL)
      )='TRUE';

    NAME
    --------------------------------
    Place1

**Parent topic:** SDO_GEOMETRY Objects in Function-Based Indexes

#### 10.2.2 Example: Function with a User-Defined Object Type

In the following example, the input parameter to the function used for the function-based index is an object of a user-defined type that includes the longitude and latitude.

Assume that you want to create a function that returns the longitude and latitude of a point and to create a spatial index on that function. First, create the user-defined data type, as in the following example that creates an object type named long_lat and its member function GetGeometry:

    CREATE TYPE long_lat as object (
       longitude NUMBER,
       latitude NUMBER,
    MEMBER FUNCTION GetGeometry(SELF IN long_lat)
    RETURN SDO_GEOMETRY DETERMINISTIC)
    /

    CREATE OR REPLACE TYPE BODY long_lat AS
      MEMBER FUNCTION GetGeometry(SELF IN long_lat)
      RETURN SDO_GEOMETRY IS
        BEGIN
           IF (longitude IS NULL) OR (latitude IS NULL) THEN
             RETURN NULL;
           END IF;
           RETURN SDO_GEOMETRY(2001, 8307,
               SDO_POINT_TYPE(longitude, latitude, NULL), NULL,NULL);
        END;
    END;
    /


If the spatial data table does not already exist, create the table and add data to it, as in the following example that creates a table named test_long_lat:

    CREATE TABLE test_long_lat
       (location long_lat, name VARCHAR2(32));

    INSERT INTO test_long_lat VALUES (long_lat(10,10), 'Place1');
    INSERT INTO test_long_lat VALUES (long_lat(20,20), 'Place2');
    INSERT INTO test_long_lat VALUES (long_lat(30,30), 'Place3');

Update the USER_SDO_GEOM_METADATA view, using dot-notation to specify the schema name, table name, and function name and parameter value. The following example specifies SCOTT.LONG_LAT.GETGEOMETRY(LOCATION) as the COLUMN_NAME (explained in [COLUMN_NAME](spatial-datatypes-metadata.md)) in the metadata view.

    INSERT INTO USER_SDO_GEOM_METADATA VALUES('test_long_lat',
     'scott.long_lat.GetGeometry(location)',
     SDO_DIM_ARRAY(
       SDO_DIM_ELEMENT('Longitude', -180, 180, 0.005),
       SDO_DIM_ELEMENT('Latitude', -90, 90, 0.005)), 8307);

Create the spatial index, specifying the column name and function name using dot-notation. For example:

    CREATE INDEX test_long_lat_idx ON test_long_lat(location.GetGeometry())
      INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2;

Perform queries on the data. The following query performs a primary filter operation, asking for the names of geometries that are likely to interact spatially with point (10,10).

    SELECT a.name FROM test_long_lat a
      WHERE SDO_FILTER(a.location.GetGeometry(),
                SDO_GEOMETRY(2001, 8307,
                    SDO_POINT_TYPE(10,10,NULL), NULL, NULL)
                ) = 'TRUE';

**Parent topic:** SDO_GEOMETRY Objects in Function-Based Indexes
