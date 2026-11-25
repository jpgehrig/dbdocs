## 3  SQL Multimedia Type Support

Oracle Spatial and Graph supports the use of the ST\_xxx types specified in ISO 13249-3, Information technology - Database languages - SQL Multimedia and Application Packages - Part 3: Spatial.

- ST_GEOMETRY and SDO_GEOMETRY Interoperability
  The SQL Multimedia ST_GEOMETRY root type, including its subtypes, and the Oracle Spatial and Graph SDO_GEOMETRY type are essentially interoperable.
- ST_xxx Functions and Spatial and Graph Counterparts
  The following table lists SQL Multimedia functions and the comparable Oracle Spatial and Graph SDO_GEOMETRY method or Spatial and Graph function, procedure, operator.
- Tolerance Value with SQL Multimedia Types
  Because the SQL Multimedia standard does not define how tolerance is to be used with the ST\_ xxx, Spatial and Graph uses a default value of 0.005 in all the member methods of the ST_GEOMETRY type.
- Avoiding Name Conflicts
  To avoid possible conflicts between third-party names and Oracle-supplied names, any third-party implementation of ST\_xxx types on Oracle should use a schema prefix.
- Annotation Text Type and Views
  Oracle Spatial and Graph supports annotation text as specified in the OpenGIS Implementation Specification for Geographic information - Simple feature access - Part 1: Common architecture, which defines annotation text as "simply placed text that can carry either geographically-related or ad-hoc data and process-related information as displayable text. This text may be used for display in editors or in simpler maps. It is usually lacking in full cartographic quality, but may act as an approximation to such text as needed by any application."

**Parent topic:** [Conceptual and Usage Information](spatial-concepts-usage.md)

### 3.1 ST_GEOMETRY and SDO_GEOMETRY Interoperability

The SQL Multimedia ST_GEOMETRY root type, including its subtypes, and the Oracle Spatial and Graph SDO_GEOMETRY type are essentially interoperable.

The ST_GEOMETRY subtypes are:

- ST_CIRCULARSTRING

- ST_COMPOUNDCURVE

- ST_CURVE

- ST_CURVEPOLYGON

- ST_GEOMCOLLECTION

- ST_LINESTRING

- ST_MULTICURVE

- ST_MULTILINESTRING

- ST_MULTIPOINT

- ST_MULTIPOLYGON

- ST_MULTISURFACE

- ST_POINT

- ST_POLYGON

- ST_SURFACE

The ST_GEOMETRY type has an additional constructor method (that is, in addition to the constructors defined in the ISO standard) for creating an instance of the type using an SDO_GEOMETRY object. This constructor has the following format:

    ST_GEOMETRY(geom SDO_GEOMETRY);

Example 3-1 Using the ST_GEOMETRY Type for a Spatial Column

Example 3-1 creates a table using the ST_GEOMETRY type for a spatial column instead of the SDO_GEOMETRY type, and it uses the ST_GEOMETRY constructor to specify the SHAPE column value when inserting a row into that table.

    CREATE TABLE cola_markets (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      shape ST_GEOMETRY);

    INSERT INTO cola_markets VALUES(
      1,
      'cola_a',
      ST_GEOMETRY(
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3), -- one rectangle (1003 = exterior)
          SDO_ORDINATE_ARRAY(1,1, 5,7) -- only 2 points needed to
                -- define rectangle (lower left and upper right) with
                -- Cartesian-coordinate data
        )
      )
    );

If you create a table with a spatial column of type ST_GEOMETRY, you should add its information to the USER_SDO_GEOM_METADATA view and create a spatial index on the ST_GEOMETRY column, just as you would for spatial data defined using the SDO_GEOMETRY type. After you have performed these operations, you can use Oracle Spatial and Graph operators (described in [Spatial Operators](spatial-operators-reference.md) ) in the ST_GEOMETRY data. In addition to the operators defined in the standard, you can use the [SDO_NN](spatial-operators-reference.md) and [SDO_WITHIN_DISTANCE](spatial-operators-reference.md) operators.

Example 3-2 Creating, Indexing, Storing, and Querying ST_GEOMETRY Data

Example 3-2 performs many of the same basic operations as in [Simple Example: Inserting, Indexing, and Querying Spatial Data](spatial-datatypes-metadata.md), but it uses the ST_GEOMETRY type instead of the SDO_GEOMETRY type for the spatial column.

    CREATE TABLE cola_markets (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      shape ST_GEOMETRY);

    INSERT INTO cola_markets VALUES(
      1,
      'cola_a',
      ST_GEOMETRY(
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3), -- one rectangle (1003 = exterior)
          SDO_ORDINATE_ARRAY(1,1, 5,7) -- only 2 points needed to
                -- define rectangle (lower left and upper right) with
                -- Cartesian-coordinate data
        )
      )
    );

    INSERT INTO cola_markets VALUES(
      2,
      'cola_b',
      ST_GEOMETRY(
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,1), -- one polygon (exterior polygon ring)
          SDO_ORDINATE_ARRAY(5,1, 8,1, 8,6, 5,7, 5,1)
        )
      )
    );

    INSERT INTO cola_markets VALUES(
      3,
      'cola_c',
      ST_GEOMETRY(
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,1), -- one polygon (exterior polygon ring)
          SDO_ORDINATE_ARRAY(3,3, 6,3, 6,5, 4,5, 3,3)
        )
      )
    );

    INSERT INTO cola_markets VALUES(
      4,
      'cola_d',
      ST_GEOMETRY(
        SDO_GEOMETRY(
          2003,  -- two-dimensional polygon
          NULL,
          NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,4), -- one circle
          SDO_ORDINATE_ARRAY(8,7, 10,9, 8,11)
        )
      )
    );

    ---------------------------------------------------------------------------
    -- UPDATE METADATA VIEW --
    ---------------------------------------------------------------------------

    -- Update the USER_SDO_GEOM_METADATA view. This is required before
    -- the spatial index can be created. Do this only once for each layer
    -- (that is, table-column combination; here: cola_markets and shape).

    INSERT INTO user_sdo_geom_metadata
        (TABLE_NAME,
         COLUMN_NAME,
         DIMINFO,
         SRID)
      VALUES (
        'cola_markets',
        'shape',
        SDO_DIM_ARRAY(   -- 20X20 grid
          SDO_DIM_ELEMENT('X', 0, 20, 0.005),
          SDO_DIM_ELEMENT('Y', 0, 20, 0.005)
           ),
        NULL   -- SRID
      );

    -------------------------------------------------------------------
    -- CREATE THE SPATIAL INDEX --
    -------------------------------------------------------------------

    CREATE INDEX cola_spatial_idx
    ON cola_markets(shape)
    INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2;

    ---------------------------
    -- SDO_NN and SDO_WITHIN_DISTANCE
    --------------------------

    -- SDO_NN operator.

    SELECT  /*+ INDEX(c cola_spatial_idx) */ c.mkt_id, c.name
       FROM cola_markets c
       WHERE SDO_NN(c.shape,  sdo_geometry(2001, NULL,
          sdo_point_type(10,7,NULL), NULL,  NULL),  'sdo_num_res=2') = 'TRUE';

    -- SDO_NN_DISTANCE ancillary operator

    SELECT   /*+ INDEX(c cola_spatial_idx) */
       c.mkt_id, c.name, SDO_NN_DISTANCE(1) dist
       FROM cola_markets c
       WHERE SDO_NN(c.shape,  sdo_geometry(2001, NULL,
          sdo_point_type(10,7,NULL), NULL,  NULL),
          'sdo_num_res=2', 1) = 'TRUE' ORDER BY dist;

    -- SDO_WITHIN_DISTANCE operator (two examples)

    SELECT c.name FROM cola_markets c WHERE SDO_WITHIN_DISTANCE(c.shape,
      SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(4,6, 8,8)),
      'distance=10') = 'TRUE';

    -- What geometries are within a distance of 10 from a query window
    -- (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8)?
    -- But exclude geoms with MBRs with both sides < 4.1, i.e., cola_c and cola_d.

    SELECT c.name FROM cola_markets c WHERE SDO_WITHIN_DISTANCE(c.shape,
      SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(4,6, 8,8)),
      'distance=10 min_resolution=4.1') = 'TRUE';

    -------------------------------------
    -- Some ST_GEOMETRY member functions
    -------------------------------------

    SELECT c.shape.GET_WKB()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.GET_WKT()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_COORDDIM()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_ISVALID()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_SRID()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_SRID(8307)
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_ISEMPTY()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_ENVELOPE()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_BOUNDARY()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_GEOMETRYTYPE()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_ISSIMPLE()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_DIMENSION()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_CONVEXHULL()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_CENTROID()
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_GETTOLERANCE()
      FROM cola_markets c WHERE c.name = 'cola_b';

    -- Some member functions that require a parameter
    DECLARE
      cola_a_geom ST_GEOMETRY;
      cola_b_geom ST_GEOMETRY;
      cola_c_geom ST_GEOMETRY;
      cola_d_geom ST_GEOMETRY;
      returned_geom ST_GEOMETRY;
      returned_number NUMBER;

    BEGIN

    -- Populate geometry variables with cola market shapes.
    SELECT c.shape INTO cola_a_geom FROM cola_markets c
      WHERE c.name = 'cola_a';
    SELECT c.shape INTO cola_b_geom FROM cola_markets c
      WHERE c.name = 'cola_b';
    SELECT c.shape INTO cola_c_geom FROM cola_markets c
      WHERE c.name = 'cola_c';
    SELECT c.shape INTO cola_d_geom FROM cola_markets c
      WHERE c.name = 'cola_d';

    SELECT c.shape.ST_EQUALS(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Is cola_b equal to cola_a?: ' || returned_number);

    SELECT c.shape.ST_SYMMETRICDIFFERENCE(cola_a_geom) INTO returned_geom
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_DISTANCE(cola_d_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Distance between cola_b equal to cola_d: ' || returned_number);

    SELECT c.shape.ST_INTERSECTS(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b intersect cola_a?: ' || returned_number);

    SELECT c.shape.ST_CROSS(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b cross cola_a?: ' || returned_number);

    SELECT c.shape.ST_DISJOINT(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Is cola_b disjoint with cola_a?: ' || returned_number);

    SELECT c.shape.ST_TOUCH(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b touch cola_a?: ' || returned_number);

    SELECT c.shape.ST_WITHIN(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Is cola_b within cola_a?: ' || returned_number);

    SELECT c.shape.ST_OVERLAP(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b overlap cola_a?: ' || returned_number);

    SELECT c.shape.ST_CONTAINS(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b contain cola_a?: ' || returned_number);

    SELECT c.shape.ST_INTERSECTION(cola_a_geom) INTO returned_geom
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_DIFFERENCE(cola_a_geom) INTO returned_geom
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_UNION(cola_a_geom) INTO returned_geom
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_SYMDIFFERENCE(cola_a_geom) INTO returned_geom
      FROM cola_markets c WHERE c.name = 'cola_b';

    SELECT c.shape.ST_TOUCHES(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b touch cola_a?: ' || returned_number);

    SELECT c.shape.ST_CROSSES(cola_a_geom) INTO returned_number
      FROM cola_markets c WHERE c.name = 'cola_b';
    DBMS_OUTPUT.PUT_LINE('Does cola_b cross cola_a?: ' || returned_number);

    END;
    /

**Parent topic:** SQL Multimedia Type Support

### 3.2 ST_xxx Functions and Spatial and Graph Counterparts

The following table lists SQL Multimedia functions and the comparable Oracle Spatial and Graph SDO_GEOMETRY method or Spatial and Graph function, procedure, operator.

Note that in some cases the Oracle Spatial and Graph counterpart has more features than the SQL Multimedia function.

Table 3-1 ST_xxx Functions and Spatial and Graph Counterparts

| SQL Multimedia Function | Comparable Oracle Spatial and Graph Interface                                                  |
|:------------------------|:-----------------------------------------------------------------------------------------------|
| FROM_WKB                | [SDO_UTIL.FROM_WKBGEOMETRY](SDO_UTIL-reference.md)                                             |
| FROM_WKT                | [SDO_UTIL.FROM_WKTGEOMETRY](SDO_UTIL-reference.md)                                             |
| GET_WKB                 | SDO_GEOMETRY.Get_WKB                                                                           |
| GET_WKT                 | SDO_GEOMETRY.Get_WKT                                                                           |
| ST_BUFFER               | [SDO_GEOM.SDO_BUFFER](SDO_GEOM-reference.md)                                                   |
| ST_CENTROID             | [SDO_GEOM.SDO_CENTROID](SDO_GEOM-reference.md)                                                 |
| ST_CONTAINS             | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=CONTAINS`                                  |
| ST_CONVEXHULL           | [SDO_GEOM.SDO_CONVEXHULL](SDO_GEOM-reference.md)                                               |
| ST_COORDDIM             | SDO_GEOMETRY.Get_Dims and SDO_GEOMETRY.ST_CoordDim (equivalent)                                |
| ST_CROSS                | (None predefined; requires using [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with a complex mask) |
| ST_CROSSES              | (None predefined; requires using [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with a complex mask) |
| ST_DIFFERENCE           | [SDO_GEOM.SDO_DIFFERENCE](SDO_GEOM-reference.md)                                               |
| ST_DIMENSION            | SDO_GEOMETRY.Get_Dims                                                                          |
| ST_DISJOINT             | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=DISJOINT`                                  |
| ST_DISTANCE             | [SDO_GEOM.SDO_DISTANCE](SDO_GEOM-reference.md)                                                 |
| ST_ENVELOPE             | [SDO_GEOM.SDO_MBR](SDO_GEOM-reference.md)                                                      |
| ST_EQUALS               | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=EQUAL`                                     |
| ST_GEOMETRYTYPE         | SDO_GEOMETRY.Get_GType                                                                         |
| ST_INTERSECTION         | [SDO_GEOM.SDO_INTERSECTION](SDO_GEOM-reference.md)                                             |
| ST_INTERSECTS           | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=OVERLAPBDYDISJOINT + OVERLAPBDYINTERSECT`  |
| ST_ISVALID              | [SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT](SDO_GEOM-reference.md)                               |
| ST_OVERLAP              | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=CONTAINS`                                  |
| ST_RELATE               | [SDO_RELATE](spatial-operators-reference.md), [SDO_GEOM.RELATE](SDO_GEOM-reference.md)         |
| ST_SYMDIFFERENCE        | [SDO_GEOM.SDO_XOR](SDO_GEOM-reference.md)                                                      |
| ST_SYMMETRICDIFFERENCE  | [SDO_GEOM.SDO_XOR](SDO_GEOM-reference.md)                                                      |
| ST_TOUCH                | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=TOUCH`                                     |
| ST_TOUCHES              | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=TOUCH`                                     |
| ST_UNION                | [SDO_GEOM.SDO_UNION](SDO_GEOM-reference.md)                                                    |
| ST_WITHIN               | [SDO_GEOM.RELATE](SDO_GEOM-reference.md) with `mask=COVERS+CONTAINS`                           |

**Parent topic:** SQL Multimedia Type Support

### 3.3 Tolerance Value with SQL Multimedia Types

Because the SQL Multimedia standard does not define how tolerance is to be used with the ST\_ xxx, Spatial and Graph uses a default value of 0.005 in all the member methods of the ST_GEOMETRY type.

If you want to specify a different tolerance value to be used with ST_GEOMETRY member functions, override the default by inserting the desired value into the SDO_ST_TOLERANCE table.

The SDO_ST_TOLERANCE table is a global temporary table that should have a single row specifying the tolerance to be used with ST_GEOMETRY member methods. This table has a single column, defined as `(tolerance NUMBER)`.

For all spatial operators that use a spatial index, Spatial and Graph uses the tolerance value specified for the spatial column in the USER_SDO_GEOM_METADATA view.

**Parent topic:** SQL Multimedia Type Support

### 3.4 Avoiding Name Conflicts

To avoid possible conflicts between third-party names and Oracle-supplied names, any third-party implementation of ST\_xxx types on Oracle should use a schema prefix.

Some third-party vendors support their own version of ST\_xxx types on Oracle. For example, a vendor might create its own version of the ST_GEOMETRY type.

To avoid possible conflicts, that vendor’s implementation of ST\_xxx types on Oracle should use a schema prefix.. This will ensure that if someone specifies a column type as just ST_GEOMETRY, the column will be created with the Oracle implementation of the ST_GEOMETRY type.

**Parent topic:** SQL Multimedia Type Support

### 3.5 Annotation Text Type and Views

Oracle Spatial and Graph supports annotation text as specified in the OpenGIS Implementation Specification for Geographic information - Simple feature access - Part 1: Common architecture, which defines annotation text as "simply placed text that can carry either geographically-related or ad-hoc data and process-related information as displayable text. This text may be used for display in editors or in simpler maps. It is usually lacking in full cartographic quality, but may act as an approximation to such text as needed by any application."

The ST_ANNOTATION_TEXT object type can be used to store annotation text. This type has a constructor for inserting annotation text into a table, as explained in Using the ST_ANNOTATION_TEXT Constructor.

The USER_ANNOTATION_TEXT_METADATA and ALL_ANNOTATION_TEXT_METADATA views store metadata related to annotation text, as explained in Annotation Text Metadata Views.

- Using the ST_ANNOTATION_TEXT Constructor
- Annotation Text Metadata Views

**Parent topic:** SQL Multimedia Type Support

#### 3.5.1 Using the ST_ANNOTATION_TEXT Constructor

An annotation text object contains an array of objects, where each object consists of a text label, the point at which to start rendering the text label, a leader line (typically from the text label to the associated point on the map), and optionally extra attribute information. A single annotation text object may typically contain all the text labels for a map.

Each text label object has the following definition:

     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     PRIVATEVALUE                                       VARCHAR2(4000)
     PRIVATELOCATION                                    MDSYS.SDO_GEOMETRY
     PRIVATELEADERLINE                                  MDSYS.SDO_GEOMETRY
     PRIVATETEXTATTRIBUTES                              VARCHAR2(4000)

Example 3-3 Using the ST_ANNOTATION_TEXT Constructor

To insert the annotation for a single point, use the ST_ANNOTATION_TEXT constructor. This constructor specifies the information for a single point using an array, as shown in Example 3-3, which creates a table with a column of type ST_ANNOTATION_TEXT and inserts one row, using the ST_ANNOTATION_TEXT constructor in the INSERT statement.

    CREATE TABLE my_annotations (id NUMBER, textobj ST_ANNOTATION_TEXT);

    INSERT INTO my_annotations VALUES (2,
     ST_ANNOTATION_TEXT(
        ST_ANNOTATIONTEXTELEMENT_ARRAY(
               ST_ANNOT_TEXTELEMENT_ARRAY(
                     ST_ANNOTATIONTEXTELEMENT(
                        'Sample Label 2',
                        SDO_GEOMETRY(2001,null,sdo_point_type(10,10,null),null,null),
                        SDO_GEOMETRY(2002,null,null,
                            SDO_ELEM_INFO_ARRAY(1,2,1),
                            SDO_ORDINATE_ARRAY(5,10, 10,10)),
                        NULL)))));

In the ST_ANNOTATION_TEXT constructor in Example 3-3, the ST_ANNOTATIONTEXTELEMENT subelement specifies the following:

- The text for the label, in this case `Sample Label 2`

- A point geometry specifying where to start rendering the label, in this case location (10,10)

- A line string geometry specifying the start and end points of the leader line between the point of interest and the text label, in this case a line between locations (5,10) and (10,10)

- No text display attribute information (NULL), which means that the information TEXT_ATTRIBUTES column of the annotation text metadata views is used (see Table 3-2 in Annotation Text Metadata Views)

**Parent topic:** Annotation Text Type and Views

#### 3.5.2 Annotation Text Metadata Views

The annotation text metadata is stored in a global table owned by MDSYS (which users should never directly update). Each Spatial and Graph user has the following views available in the schema associated with that user:

- USER_ANNOTATION_TEXT_METADATA contains metadata information for all annotation text in tables owned by the user (schema). This is the only view that you can update, and it is the one in which Spatial and Graph users must insert metadata related to spatial tables.

- ALL_ANNOTATION_TEXT_METADATA contains metadata information for all annotation text in tables on which the user has SELECT permission.

Spatial and Graph users are responsible for populating these views. For each annotation text object, you must insert an appropriate row into the USER_ANNOTATION_TEXT_METADATA view. Oracle Spatial and Graph ensures that the ALL_ANNOTATION_TEXT_METADATA view is also updated to reflect the rows that you insert into USER_ANNOTATION_TEXT_METADATA.

The USER_ANNOTATION_TEXT_METADATA and ALL_ANNOTATION_TEXT_METADATA views contain the same columns, as shown Table 3-2, except that the USER_ANNOTATION_TEXT_METADATA view does not contain the OWNER column. (The columns are listed in their order in the view definition.)

Table 3-2 Columns in the Annotation Text Metadata Views

| Column Name     | Data Type      | Purpose                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OWNER           | VARCHAR2(32)   | Owner of the table specified in the TABLE_NAME column (ALL_ANNOTATION_TEXT_METADATA view only).                                                                                                                                                                                                                                                                                                                    |
| TABLE_NAME      | VARCHAR2(32)   | Name of the table containing the column of type ST_ANNOTATION_TEXT.                                                                                                                                                                                                                                                                                                                                                |
| COLUMN_NAME     | VARCHAR2(1024) | Name of the column of type ST_ANNOTATION_TEXT.                                                                                                                                                                                                                                                                                                                                                                     |
| TEXT_EXPRESSION | VARCHAR2(4000) | A value that can be used if text is not specified for a label. As explained in the OpenGIS specification: "Text to place is first derived from the contents of VALUE in the current element, if VALUE is not null. Otherwise, text is derived from the first non-null preceding element VALUE. If all preceding elements have null VALUE fields, VALUE is derived from the TEXT_EXPRESSION in the metadata table." |
| TEXT_ATTRIBUTES | VARCHAR2(4000) | Default text display attributes (font family and size, horizontal and vertical spacing, and so on) for the label text style and layout, unless overridden in the PRIVATETEXTATTRIBUTES attribute of the ST_ANNOTATION_TEXT constructor (described in Using the ST_ANNOTATION_TEXT Constructor). Use the format specified in the "XML for Text Attributes" section of the OpenGIS specification.                    |

**Parent topic:** Annotation Text Type and Views
