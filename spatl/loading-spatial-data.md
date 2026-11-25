## 4  Loading Spatial Data

This chapter describes how to load spatial data into a database, including storing the data in a table with a column of type SDO_GEOMETRY.

After you have loaded spatial data, you can create a spatial index for it and perform queries on it.

The process of loading data can be classified into two categories:

- Bulk loading of data

  This process is used to load large volumes of data into the database and uses the SQL\*Loader utility to load the data.

- Transactional insert operations

  This process is typically used to insert relatively small amounts of data into the database using the INSERT statement in SQL.

<!-- -->

- Bulk Loading
  Bulk loading can import large amounts of data into an Oracle database.
- Transactional Insert Operations Using SQL
  Oracle Spatial and Graph uses standard Oracle tables that can be accessed or loaded with standard SQL syntax. This topic contains examples of transactional insertions into columns of type SDO_GEOMETRY. This process is typically used to add relatively small amounts of data into the database.
- Recommendations for Loading and Validating Spatial Data
  You should validate all geometry data, and fix any validation errors, before performing any spatial operations on the data.

**Parent topic:** [Conceptual and Usage Information](spatial-concepts-usage.md)

### 4.1 Bulk Loading

Bulk loading can import large amounts of data into an Oracle database.

Bulk loading is accomplished with the SQL\*Loader utility. (For information about SQL\*Loader, see [Oracle Database Utilities](../sutil/oracle-sql-loader.md).)

- Bulk Loading SDO_GEOMETRY Objects
- Bulk Loading Point-Only Data in SDO_GEOMETRY Objects

**Parent topic:** Loading Spatial Data

#### 4.1.1 Bulk Loading SDO_GEOMETRY Objects

Example 4-1 is the SQL\*Loader control file for loading four geometries. When this control file is used with SQL\*Loader, it loads the same cola market geometries that are inserted using SQL statements in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).

Example 4-1 Control File for a Bulk Load of Cola Market Geometries

    LOAD DATA
    INFILE *
    TRUNCATE
    CONTINUEIF NEXT(1:1) = '#'
    INTO TABLE COLA_MARKETS
    FIELDS TERMINATED BY '|'
    TRAILING NULLCOLS (
    mkt_id INTEGER EXTERNAL,
    name CHAR,
    shape COLUMN OBJECT
    (
    SDO_GTYPE INTEGER EXTERNAL,
    SDO_ELEM_INFO VARRAY TERMINATED BY '|/'
    (elements FLOAT EXTERNAL),
    SDO_ORDINATES VARRAY TERMINATED BY '|/'
    (ordinates FLOAT EXTERNAL)
    )
    )
    begindata
     1|cola_a|
    #2003|1|1003|3|/
    #1|1|5|7|/
     2|cola_b|
    #2003|1|1003|1|/
    #5|1|8|1|8|6|5|7|5|1|/
     3|cola_c|
    #2003|1|1003|1|/
    #3|3|6|3|6|5|4|5|3|3|/
     4|cola_d|
    #2003|1|1003|4|/
    #8|7|10|9|8|11|/

Notes on Example 4-1:

- The `EXTERNAL` keyword in the definition `mkt_id INTEGER EXTERNAL` means that each value to be inserted into the MKT_ID column (1, 2, 3, and 4 in this example) is an integer in human-readable form, not binary format.

- In the data after `begindata`, each MKT_ID value is preceded by one space, because the `CONTINUEIF NEXT(1:1) = '#'` specification causes the first position of each data line to be ignored unless it is the number sign (#) continuation character.

Example 4-2 Control File for a Bulk Load of Polygons

Example 4-2 assumes that a table named POLY_4PT was created as follows:

    CREATE TABLE POLY_4PT (GID VARCHAR2(32),
                           GEOMETRY SDO_GEOMETRY);

Assume that the ASCII data consists of a file with delimited columns and separate rows fixed by the limits of the table with the following format:

    geometry rows:    GID, GEOMETRY

The coordinates in the GEOMETRY column represent polygons. Example 4-2 shows the control file for loading the data.

    LOAD DATA
     INFILE *
     TRUNCATE
     CONTINUEIF NEXT(1:1) = '#'
     INTO TABLE POLY_4PT
     FIELDS TERMINATED BY '|'
     TRAILING NULLCOLS (
      GID  INTEGER EXTERNAL,
      GEOMETRY COLUMN OBJECT
       (
         SDO_GTYPE       INTEGER EXTERNAL,
         SDO_ELEM_INFO   VARRAY TERMINATED BY '|/'
           (elements     FLOAT EXTERNAL),
         SDO_ORDINATES   VARRAY TERMINATED BY '|/'
           (ordinates    FLOAT EXTERNAL)
       )
    )
    begindata
     1|2003|1|1003|1|/
    #-122.4215|37.7862|-122.422|37.7869|-122.421|37.789|-122.42|37.7866|
    #-122.4215|37.7862|/
     2|2003|1|1003|1|/
    #-122.4019|37.8052|-122.4027|37.8055|-122.4031|37.806|-122.4012|37.8052|
    #-122.4019|37.8052|/
     3|2003|1|1003|1|/
    #-122.426|37.803|-122.4242|37.8053|-122.42355|37.8044|-122.4235|37.8025|
    #-122.426|37.803|/

**Parent topic:** Bulk Loading

#### 4.1.2 Bulk Loading Point-Only Data in SDO_GEOMETRY Objects

Example 4-3 shows a control file for loading a table with point data.

Example 4-3 Control File for a Bulk Load of Point-Only Data

    LOAD DATA
     INFILE *
     TRUNCATE
     CONTINUEIF NEXT(1:1) = '#'
     INTO TABLE POINT
     FIELDS TERMINATED BY '|'
     TRAILING NULLCOLS (
      GID      INTEGER EXTERNAL,
      GEOMETRY COLUMN OBJECT
       (
         SDO_GTYPE       INTEGER EXTERNAL,
         SDO_POINT COLUMN OBJECT
           (X            FLOAT EXTERNAL,
            Y            FLOAT EXTERNAL)
       )
    )

    BEGINDATA
     1| 2001| -122.4215| 37.7862|
     2| 2001| -122.4019| 37.8052|
     3| 2001| -122.426| 37.803|
     4| 2001| -122.4171| 37.8034|
     5| 2001| -122.416151| 37.8027228|

**Parent topic:** Bulk Loading

### 4.2 Transactional Insert Operations Using SQL

Oracle Spatial and Graph uses standard Oracle tables that can be accessed or loaded with standard SQL syntax. This topic contains examples of transactional insertions into columns of type SDO_GEOMETRY. This process is typically used to add relatively small amounts of data into the database.

The INSERT statement in Oracle SQL has a limit of 999 arguments. Therefore, you cannot create a variable-length array of more than 999 elements using the SDO_GEOMETRY constructor inside a transactional INSERT statement; however, you can insert a geometry using a host variable, and the host variable can be built using the SDO_GEOMETRY constructor with more than 999 values in the SDO_ORDINATE_ARRAY specification. (The host variable is an OCI, PL/SQL, or Java program variable.)

To perform transactional insertions of geometries, you can create a procedure to insert a geometry, and then invoke that procedure on each geometry to be inserted. Example 4-4 creates a procedure to perform the insert operation.

Example 4-4 Procedure to Perform a Transactional Insert Operation

    CREATE OR REPLACE PROCEDURE
            INSERT_GEOM(GEOM SDO_GEOMETRY)
    IS

    BEGIN
      INSERT INTO TEST_1 VALUES (GEOM);
      COMMIT;
    END;
    /

Using the procedure created in Example 4-4, you can insert data by using a PL/SQL block, such as the one in Example 4-5, which loads a geometry into the variable named `geom` and then invokes the INSERT_GEOM procedure to insert that geometry.

Example 4-5 PL/SQL Block Invoking a Procedure to Insert a Geometry

    DECLARE
    geom SDO_geometry :=
      SDO_geometry (2003, null, null,
              SDO_elem_info_array (1,1003,3),
              SDO_ordinate_array (-109,37,-102,40));
    BEGIN
      INSERT_GEOM(geom);
      COMMIT;
    END;
    /

For additional examples with various geometry types, see the following:

- [Rectangle](spatial-datatypes-metadata.md)

- [Polygon with a Hole](spatial-datatypes-metadata.md)

- [Compound Line String](spatial-datatypes-metadata.md)

- [Compound Polygon](spatial-datatypes-metadata.md)

- [Point](spatial-datatypes-metadata.md)

- [Oriented Point](spatial-datatypes-metadata.md)

- [Type 0 (Zero) Element](spatial-datatypes-metadata.md)

**Parent topic:** Loading Spatial Data

### 4.3 Recommendations for Loading and Validating Spatial Data

You should validate all geometry data, and fix any validation errors, before performing any spatial operations on the data.

The recommended procedure for loading and validating spatial data is as follows:

1.  Load the data, using a method described in Bulk Loading or Transactional Insert Operations Using SQL.
2.  Use the [SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT](SDO_GEOM-reference.md) function or the [SDO_GEOM.VALIDATE_LAYER_WITH_CONTEXT](SDO_GEOM-reference.md) procedure on all spatial data loaded into the database.
3.  For any geometries with the wrong orientation or an invalid ETYPE or GTYPE value, use [SDO_MIGRATE.TO_CURRENT](SDO_MIGRATE-reference.md) on these invalid geometries to fix them.
4.  For any geometries that are invalid for other reasons, use [SDO_UTIL.RECTIFY_GEOMETRY](SDO_UTIL-reference.md) to fix these geometries.

For detailed information about using any of these subprograms, see the usage notes in its reference information section.

**Parent topic:** Loading Spatial Data
