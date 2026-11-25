## 20  Spatial Operators

This chapter describes the operators that you can use when working with the spatial object data type.

For an overview of spatial operators, including how they differ from spatial procedures and functions, see [Spatial Operators\_ Procedures\_ and Functions](spatial-concepts.md). Table 20-1 lists the main operators.

Table 20-1 Main Spatial Operators

| Operator            | Description                                                                                                                                                                                        |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDO_FILTER          | Specifies which geometries may interact with a given geometry.                                                                                                                                     |
| SDO_JOIN            | Performs a spatial join based on one or more topological relationships.                                                                                                                            |
| SDO_NN              | Determines the nearest neighbor geometries to a geometry.                                                                                                                                          |
| SDO_NN_DISTANCE     | Returns the distance of an object returned by the SDO_NN operator.                                                                                                                                 |
| SDO_POINTINPOLYGON  | Takes a set of rows whose first column is a point's x-coordinate value and the second column is a point's y-coordinate value, and returns those rows that are within a specified polygon geometry. |
| SDO_RELATE          | Determines whether or not two geometries interact in a specified way. (See also Table 20-2 for convenient alternative operators for performing specific mask value operations.)                    |
| SDO_WITHIN_DISTANCE | Determines if two geometries are within a specified distance from one another.                                                                                                                     |

Table 20-2 lists operators, provided for convenience, that perform an SDO_RELATE operation of a specific mask type.

Table 20-2 Convenience Operators for SDO_RELATE Operations

| Operator                | Description                                                                                                                                                   |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDO_ANYINTERACT         | Checks if any geometries in a table have the ANYINTERACT topological relationship with a specified geometry.                                                  |
| SDO_CONTAINS            | Checks if any geometries in a table have the CONTAINS topological relationship with a specified geometry.                                                     |
| SDO_COVEREDBY           | Checks if any geometries in a table have the COVEREDBY topological relationship with a specified geometry.                                                    |
| SDO_COVERS              | Checks if any geometries in a table have the COVERS topological relationship with a specified geometry.                                                       |
| SDO_EQUAL               | Checks if any geometries in a table have the EQUAL topological relationship with a specified geometry.                                                        |
| SDO_INSIDE              | Checks if any geometries in a table have the INSIDE topological relationship with a specified geometry.                                                       |
| SDO_ON                  | Checks if any geometries in a table have the ON topological relationship with a specified geometry.                                                           |
| SDO_OVERLAPBDYDISJOINT  | Checks if any geometries in a table have the OVERLAPBDYDISJOINT topological relationship with a specified geometry.                                           |
| SDO_OVERLAPBDYINTERSECT | Checks if any geometries in a table have the OVERLAPBDYINTERSECT topological relationship with a specified geometry.                                          |
| SDO_OVERLAPS            | Checks if any geometries in a table overlap (that is, have the OVERLAPBDYDISJOINT or OVERLAPBDYINTERSECT topological relationship with) a specified geometry. |
| SDO_TOUCH               | Checks if any geometries in a table have the TOUCH topological relationship with a specified geometry.                                                        |

**Note:**

For any numbers in string (VARCHAR2) parameters to Spatial and Graph operators and subprograms, the period (.) must be used for any decimal points regardless of the locale. Example: `'distance=3.7'`

The rest of this chapter provides reference information on the operators, listed in alphabetical order.

For information about using operators with topologies, see [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/topology-data-model-overview.md).

- SDO_ANYINTERACT
- SDO_CONTAINS
- SDO_COVEREDBY
- SDO_COVERS
- SDO_EQUAL
- SDO_FILTER
- SDO_INSIDE
- SDO_JOIN
- SDO_NN
- SDO_NN_DISTANCE
- SDO_ON
- SDO_OVERLAPBDYDISJOINT
- SDO_OVERLAPBDYINTERSECT
- SDO_OVERLAPS
- SDO_POINTINPOLYGON
- SDO_RELATE
- SDO_TOUCH
- SDO_WITHIN_DISTANCE

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 20.1 SDO_ANYINTERACT

#### Format

    SDO_ANYINTERACT(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the ANYINTERACT topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=ANYINTERACT'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_ANYINTERACT(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the ANYINTERACT topological relationship, and FALSE otherwise.

#### Usage Notes

**Note:**

SDO_ANYINTERACT operator is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the ANYINTERACT relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_ANYINTERACT(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(4,6, 8,8))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a
             4 cola_d

**Parent topic:** Spatial Operators

### 20.2 SDO_CONTAINS

#### Format

    SDO_CONTAINS(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the CONTAINS topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=CONTAINS'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_CONTAINS(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the CONTAINS topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the CONTAINS relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 2,2, 4,6). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_a` contains the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_CONTAINS(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(2,2, 4,6))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             1 cola_a

**Parent topic:** Spatial Operators

### 20.3 SDO_COVEREDBY

#### Format

    SDO_COVEREDBY(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the COVEREDBY topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=COVEREDBY'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_COVEREDBY(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the COVEREDBY topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the COVEREDBY relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 1,1, 5,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_a` is covered by the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_COVEREDBY(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(1,1, 5,8))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             1 cola_a

**Parent topic:** Spatial Operators

### 20.4 SDO_COVERS

#### Format

    SDO_COVERS(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the COVERS topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=COVERS'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_COVERS(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the COVERS topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the COVERS relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 1,1, 4,6). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_a` covers the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_COVERS(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(1,1, 4,6))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             1 cola_a

**Parent topic:** Spatial Operators

### 20.5 SDO_EQUAL

#### Format

    SDO_EQUAL(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the EQUAL topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=EQUAL'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_EQUAL(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the EQUAL topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the EQUAL relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 1,1, 5,7). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, `cola_a` (and only `cola_a`) has the same boundary and interior as the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_EQUAL(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(1,1, 5,7))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             1 cola_a

**Parent topic:** Spatial Operators

### 20.6 SDO_FILTER

#### Format

    SDO_FILTER(geometry1, geometry2, param);

#### Description

Identifies either the set of spatial objects that are likely to interact spatially with a given object (such as an area of interest), or pairs of spatial objects that are likely to interact spatially. Objects interact spatially if they are not disjoint.

This operator performs only a primary filter operation. The secondary filtering operation, performed by the SDO_RELATE operator, can be used to determine with certainty if objects interact spatially.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| param     | Optionally specifies either or both of the `min_resolution` and `max_resolution` keywords. Data type is VARCHAR2.<br>The `min_resolution` keyword includes only geometries for which at least one side of the geometry's MBR is equal to or greater than the specified value. For example, `min_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is at least 10. (This keyword can be used to exclude geometries that are too small to be of interest.)<br>The `max_resolution` keyword includes only geometries for which at least one side of the geometry's MBR is less than or equal to the specified value. For example, `max_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is less than or equal to 10. (This keyword can be used to exclude geometries that are too large to be of interest.) |

#### Returns

The expression SDO_FILTER(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that are non-disjoint, and FALSE otherwise.

#### Usage Notes

**Note:**

SDO_FILTER operator is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

The SDO_FILTER operator must always be used in a WHERE clause and the condition that includes the operator should be an expression of the form SDO_FILTER(arg1, arg2) = 'TRUE'. (The expression must not equate to any value other than 'TRUE'.)

`geometry2` can come from a table or be a transient SDO_GEOMETRY object, such as a bind variable or SDO_GEOMETRY constructor.

- If the `geometry2` column is not spatially indexed, the operator indexes the query window in memory and performance is very good.

- If two or more geometries from `geometry2` are passed to the operator, the ORDERED optimizer hint must be specified, and the table in `geometry2` must be specified first in the FROM clause.

If `geometry1` and `geometry2` are based on different coordinate systems, `geometry2` is temporarily transformed to the coordinate system of `geometry1` for the operation to be performed, as described in [Different Coordinate Systems for Geometries with Operators and Functions](coordinate-systems-concepts.md).

**Note:**

If the DBMS_RLS.ADD_POLICY procedure has been used to add a fine-grained access control policy to a table or view, and if the specified policy function uses a spatial operator, the operator must be SDO_FILTER. No other spatial operators are supported in that context.

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example selects the geometries that are likely to interact with a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_FILTER(c.shape,
        SDO_GEOMETRY(2003, NULL, NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3),
          SDO_ORDINATE_ARRAY(4,6, 8,8))
        ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a
             4 cola_d

The following example is the same as the preceding example, except that it includes only geometries where at least one side of the geometry's MBR is equal to or greater than 4.1. In this case, only `cola_a` and `cola_b` are returned, because their MBRs have at least one side with a length greater than or equal to 4.1. The circle `cola_d` is excluded, because its MBR is a square whose sides have a length of 4.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_FILTER(c.shape,
        SDO_GEOMETRY(2003, NULL, NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3),
          SDO_ORDINATE_ARRAY(4,6, 8,8)),
        'min_resolution=4.1'
        ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a

The following example selects the GID values from the POLYGONS table where the GEOMETRY column objects are likely to interact spatially with the GEOMETRY column object in the QUERY_POLYS table that has a GID value of 1.

    SELECT A.gid
      FROM Polygons A, query_polys B
      WHERE B.gid = 1
      AND SDO_FILTER(A.Geometry, B.Geometry) = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object is likely to interact spatially with the geometry stored in the `aGeom` variable.

    Select A.Gid
      FROM Polygons A
      WHERE SDO_FILTER(A.Geometry, :aGeom) = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object is likely to interact spatially with the specified rectangle having the lower-left coordinates (x1,y1) and the upper-right coordinates (x2, y2).

    Select A.Gid
      FROM Polygons A
      WHERE SDO_FILTER(A.Geometry, sdo_geometry(2003,NULL,NULL,
                                       sdo_elem_info_array(1,1003,3),
                                       sdo_ordinate_array(x1,y1,x2,y2))
                       ) = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object is likely to interact spatially with any GEOMETRY column object in the QUERY_POLYS table. In this example, the ORDERED optimizer hint is used and the QUERY_POLYS (`geometry2`) table is specified first in the FROM clause, because multiple geometries from `geometry2` are involved (see the Usage Notes).

    SELECT /*+ ORDERED */
      A.gid
      FROM query_polys B, polygons A
      WHERE SDO_FILTER(A.Geometry, B.Geometry) = 'TRUE';

#### Related Topics

- SDO_RELATE

**Parent topic:** Spatial Operators

### 20.7 SDO_INSIDE

#### Format

    SDO_INSIDE(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the INSIDE topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=INSIDE'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_INSIDE(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the INSIDE topological relationship, and FALSE otherwise.

#### Usage Notes

**Note:**

SDO_INSIDE operator is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the INSIDE relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 5,6, 12,12). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_d` (the circle) is inside the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_INSIDE(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(5,6, 12,12))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             4 cola_d

**Parent topic:** Spatial Operators

### 20.8 SDO_JOIN

#### Format

    SDO_JOIN(table_name1, column_name1, table_name2, column_name2, params,preserve_join_order, table1_partition, table2_partition) RETURN SDO_ROWIDSET;

#### Description

Performs a spatial join based on one or more topological relationships.

#### Keywords and Parameters

| Value               | Description                                                                                                                                                                                                                                                                                                                                                       |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| table_name1         | Name of the first table to be used in the spatial join operation. The table must have a column of type SDO_GEOMETRY. Data type is VARCHAR2.                                                                                                                                                                                                                       |
| column_name1        | Name of the spatial column of type SDO_GEOMETRY in `table_name1`. A spatial R-tree index must be defined on this column. Data type is VARCHAR2.                                                                                                                                                                                                                   |
| table_name2         | Name of the second table to be used in the spatial join operation. (It can be the same as or different from `table_name1`. If `table_name2` is the same as `table_name1`, see "Optimizing Self-Joins" in this section.) The table must have a column of type SDO_GEOMETRY. Data type is VARCHAR2.                                                                 |
| column_name2        | Name of the spatial column of type SDO_GEOMETRY in `table_name2`. A spatial R-tree index must be defined on this column. Data type is VARCHAR2.                                                                                                                                                                                                                   |
| params              | Optional parameter string of keywords and values; available only if `mask=ANYINTERACT`. Determines the behavior of the operator. See Table 20-3 in the Usage Notes for information about the available keywords. Data type is VARCHAR2. Default is NULL.                                                                                                          |
| preserve_join_order | Optional parameter to specify if the join order is guaranteed to be preserved during processing of the operator. If the value is `0` (the default), the order of the tables might be changed; if the value is `1`, the order of the tables is not changed. Data type is NUMBER. Default is 0.                                                                     |
| table1_partition    | Name of the table partition in `table_name1`. Must be specified if the table has a partitioned spatial index; must be null if the table does not have a partitioned spatial index. (For information about using partitioned spatial indexes, see [Using Partitioned Spatial Indexes](indexing-querying-spatial-data.md).) Data type is VARCHAR2. Default is null. |
| table2_partition    | Name of the table partition in `table_name2`. Must be specified if the table has a partitioned spatial index; must be null if the table does not have a partitioned spatial index. (For information about using partitioned spatial indexes, see [Using Partitioned Spatial Indexes](indexing-querying-spatial-data.md).) Data type is VARCHAR2. Default is null. |

#### Returns

SDO_JOIN returns an object of SDO_ROWIDSET, which consists of a table of objects of SDO_ROWIDPAIR. Oracle Spatial and Graph defines the type SDO_ROWIDSET as:

    CREATE TYPE sdo_rowidset as TABLE OF sdo_rowidpair;

Oracle Spatial and Graph defines the object type SDO_ROWIDPAIR as:

    CREATE TYPE sdo_rowidpair AS OBJECT
       (rowid1  VARCHAR2(24),
        rowid2  VARCHAR2(24));

In the SDO_ROWIDPAIR definition, `rowid1` refers to a rowid from `table_name1`, and `rowid2` refers to a rowid from `table_name2`.

#### Usage Notes

SDO_JOIN is technically not an operator, but a table function. (For an explanation of table functions, see [Oracle Database PL/SQL Language Reference](../lnpls/chaining-pipelined-table-functions-multiple-transformations.md).) However, it is presented in the chapter with spatial operators because its usage is similar to that of the operators, and because it is not part of a package with other functions and procedures.

This table function is recommended when you need to perform full table joins.

The geometries in `column_name1` and `column_name2` must have the same SRID (coordinate system) value and the same number of dimensions.

For best performance, use the `/*+ ORDERED */` optimizer hint, and specify the SDO_JOIN table function first in the FROM clause.

If a table is version-enabled (using the Workspace Manager feature), you must specify the `<table_name>``_LT` table created by Workspace Manager. For example, if the COLA_MARKETS table is version-enabled and you want to perform a spatial join operation on that table, specify COLA_MARKETS_LT (not COLA_MARKETS) with the SDO_JOIN table function. (However, for all other spatial functions, procedures, and operators, do not use the `<table_name>``_LT` name.)

Table 20-3 shows the keywords for the `params` parameter.

Table 20-3 params Keywords for the SDO_JOIN Operator

| Keyword  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:---------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mask     | The topological relationship of interest.Valid values are 'mask=\<value\>' where \<value\> is one or more of the mask values valid for the SDO_RELATE operator (`TOUCH`, `OVERLAPBDYDISJOINT`, `OVERLAPBDYINTERSECT`, `EQUAL`, `INSIDE`, `COVEREDBY`, `CONTAINS`, `COVERS`, `ANYINTERACT`, `ON`), or `FILTER`, which checks if the MBRs (the filter-level approximations) intersect. Multiple masks are combined with the logical Boolean operator OR (for example, `'mask=inside+touch'`); however, `FILTER` cannot be combined with any other mask.<br>If this parameter is null or contains an empty string, `mask=FILTER` is assumed. |
| distance | Specifies a numeric distance value that is added to the tolerance value (explained in [Tolerance](spatial-concepts.md)) before the relationship checks are performed. For example, if the tolerance is 10 meters and you specify `'distance=100 unit=meter'`, two objects are considered to have spatial interaction if they are within 110 meters of each other.If you specify `distance` but not `unit`, the unit of measurement associated with the data is assumed.                                                                                                                                                                   |
| unit     | Specifies a unit of measurement to be associated with the distance value (for example, `'distance=100 unit=meter'`). See [Unit of Measurement Support](spatial-datatypes-metadata.md) for more information about unit of measurement specification. If you specify `unit`, you must also specify `distance`.Data type is VARCHAR2. Default = unit of measurement associated with the data. For geodetic data, the default is meters.                                                                                                                                                                                                      |

Before you call SDO_JOIN, you must commit any previous DML statements in your session. Otherwise, the following error will be returned: `ORA-13236: internal error in R-tree processing: [SDO_Join in active txns not supported]`

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Optimizing Self-Joins

If you are performing a self-join (that is, if `table_name1` and `table_name2` specify the same table), you can improve the performance by optimizing the self-join.

If SDO_JOIN is called without a mask (for example, `ANYINTERACT`) or distance specification, it compares only the index structure of the two geometry columns being joined. This can quickly identify geometry pairs that are "likely" to interact. If SDO_JOIN is called with a mask or distance specification, after the index is used to identify geometry pairs that are likely to interact, geometry coordinates are also compared to see if the geometry pairs actually do interact. Coordinate comparison is the most expensive part of the SDO_JOIN operation.

In a self-join, where the same geometry column is compared to itself, each geometry pair is returned twice in the result set. For example:

- For the geometry pair with ID values (1,2), the pair (2,1) is also returned. The undesired effect in SDO_JOIN is that the coordinates of the same geometry pair are compared twice, instead of once.

- ID pairs that are equal are returned twice. For example, a table with 50,000 rows will return ID pair (1,1) twice, ID pair (2,2) twice, and so on. This is also an undesired effect.

When calling SDO_JOIN in a self-join scenario, you can eliminate the undesired effects by eliminating duplicate comparison of geometry pairs and all coordinate comparisons where the ID values of the pairs match. This optimization uses SDO_JOIN for the primary filter only, and calls the [SDO_GEOM.RELATE](SDO_GEOM-reference.md) function to compare geometry coordinates. The following statement accomplishes this optimization by adding "`AND b.rowid < c.rowid`" as a predicate to the `WHERE` clause.

    SQL> set autotrace trace explain
    SQL> SELECT /*+ ordered use_nl (a,b) use_nl (a,c) */ b.id, c.id
               FROM TABLE(sdo_join('GEOD_STATES','GEOM','GEOD_STATES','GEOM')) a,
                           GEOD_STATES b,
                           GEOD_STATES c
              WHERE a.rowid1 = b.rowid
                   AND a.rowid2 = c.rowid
                   AND b.rowid < c.rowid
                   AND SDO_GEOM.RELATE (b.geom, 'ANYINTERACT', c.geom, .05) = 'TRUE'

    Execution Plan
    ----------------------------------------------------------
    Plan hash value: 1412731386
    ---------------------------------------------------------------------------------------------------
    | Id  | Operation                           | Name        | Rows  | Bytes | Cost (%CPU)| Time     |
    ---------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                    |             |     1 |  1124 | 12787   (1)| 00:02:34 |
    |   1 |  NESTED LOOPS                       |             |     1 |  1124 | 12787   (1)| 00:02:34 |
    |   2 |   NESTED LOOPS                      |             |  4574 |  2514K|  8206   (1)| 00:01:39 |
    |   3 |    COLLECTION ITERATOR PICKLER FETCH| SDO_JOIN    |       |       ||          |
    |*  4 |    TABLE ACCESS BY USER ROWID       | GEOD_STATES |     1 |   561 |1   (0)| 00:00:01 |
    |*  5 |   TABLE ACCESS BY USER ROWID        | GEOD_STATES |     1 |   561 |1   (0)| 00:00:01 |
    Predicate Information (identified by operation id):
    ---------------------------------------------------
       4 - access(CHARTOROWID(VALUE(KOKBF$)))
       5 - access(CHARTOROWID(VALUE(KOKBF$)))
           filter("B".ROWID<"C".ROWID AND
                   "SDO_GEOM"."RELATE"("B"."GEOM",'ANYINTERACT',"C"."GEOM",.05)='TRUE')

    SQL> set autotrace off

In the preceding example, It is very important that `AND b.rowid < c.rowid` be before the call to [SDO_GEOM.RELATE](SDO_GEOM-reference.md) in the `WHERE` clause. This will omit the undesired scenarios for the invocation of the [SDO_GEOM.RELATE](SDO_GEOM-reference.md) function. Also, note that the example uses the `ORDERED` and `USE_NL` hints, and that the execution plan does not contain `TABLE ACCESS FULL` or `HASH JOIN`.

#### Cross-Schema Invocation of SDO_JOIN

You can invoke the SDO_JOIN table function on an indexed table that is not in your schema, if you have been granted SELECT access to both the spatial table and to the index table for the spatial index that was created on the spatial table. To find the name of the index table for a spatial index, query the SDO_INDEX_TABLE column in the USER_SDO_INDEX_METADATA view. For example, the following statement returns the name of the index table for the COLA_MARKETS_IDX spatial index:

    SELECT sdo_index_table FROM user_sdo_index_metadata
      WHERE sdo_index_name = 'COLA_SPATIAL_IDX';

Assume that user A owns spatial table T1 (with index table MDRT_F9AA\$), and that user B owns spatial table T2 and wants to join geometries from both T1 and T2. Assume also that the geometry column in both tables is named GEOMETRY.

User A or a suitably privileged user must connect as user A and execute the following statements:

    GRANT select on T1 to B;
    GRANT select on MDRT_F9AA$ to B;

User B can now connect and execute an SDO_JOIN query, such as the following:

    SELECT COUNT(*) FROM
      (SELECT * FROM
        TABLE(SDO_JOIN('A.T1', 'GEOMETRY',
                       'B.T2', 'GEOMETRY',
                       'mask=anyinteract')) );

#### Examples

The following example joins the COLA_MARKETS table with itself to find, for each geometry, all other geometries that have any spatial interaction with it. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, `rowid1` and `rowid2` correspond to the names of the attributes in the SDO_ROWIDPAIR type definition. Note that in the output, `cola_d` (the circle) interacts only with itself, and not with any of the other geometries.

    SELECT /*+ ordered */ a.name, b.name
      FROM TABLE(SDO_JOIN('COLA_MARKETS', 'SHAPE',
                          'COLA_MARKETS', 'SHAPE',
                          'mask=ANYINTERACT')) c,
           cola_markets a,
           cola_markets b
      WHERE c.rowid1 = a.rowid AND c.rowid2 = b.rowid
      ORDER BY a.name;

    NAME                             NAME
    -------------------------------- --------------------------------
    cola_a                           cola_c
    cola_a                           cola_b
    cola_a                           cola_a
    cola_b                           cola_c
    cola_b                           cola_b
    cola_b                           cola_a
    cola_c                           cola_c
    cola_c                           cola_b
    cola_c                           cola_a
    cola_d                           cola_d

    10 rows selected.

#### Related Topics

- SDO_RELATE

**Parent topic:** Spatial Operators

### 20.9 SDO_NN

#### Format

    SDO_NN(geometry1, geometry2, param [, number]);

#### Description

Identifies the nearest neighbors for a geometry.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                                                                                                                                  |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is required. Data type is SDO_GEOMETRY.                                                                                                                                                               |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. The nearest neighbor or neighbors to `geometry2` will be returned from `geometry1`. (`geometry2` is specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |
| param     | Determines the behavior of the operator. The available keywords are listed in Table 20-4. If you do not specify this parameter, the operator returns all rows in increasing distance order from `geometry2`. Data type is VARCHAR2.                                          |
| number    | If the SDO_NN_DISTANCE ancillary operator is included in the call to SDO_NN, specifies the same number used in the call to SDO_NN_DISTANCE. Data type is NUMBER.                                                                                                             |

Table 20-4 lists the keywords for the `param` parameter.

Table 20-4 Keywords for the SDO_NN Param Parameter

| Keyword        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| distance       | Specifies the number of distance units after which to stop searching for nearest neighbors. If you do not also specify the `unit` keyword, the default is the unit of measurement associated with the data. Data type is NUMBER.<br>For example: 'distance=10 unit=mile'                                                                                                                                                                                                                                                             |
| ellipsoidal    | Specifies if ellipsoidal distance is always used with geodetic data (`true`), or if spherical distance is used in some cases (`false`, the default). See [Distance: Spherical versus Ellipsoidal with Geodetic Data](coordinate-systems-concepts.md).<br>For example: 'ellipsoidal=true'                                                                                                                                                                                                                                             |
| sdo_batch_size | Specifies the number of rows to be evaluated at a time when the SDO_NN expression may need to be evaluated multiple times in order to return the desired number of results that satisfy the WHERE clause. Available only when an R-tree index is used. If you specify `sdo_batch_size=0 `(or if you omit the `param` parameter completely), Spatial and Graph calculates a batch size suited to the result set size. See the Usage Notes and Examples for more information. Data type is NUMBER.<br>For example: 'sdo_batch_size=10' |
| sdo_num_res    | Specifies the number of results (nearest neighbors) to be returned. If neither `sdo_batch_size` nor `sdo_num_res` is specified, this is equivalent to specifying sdo_batch_size=0. See the Usage Notes and Examples for more information. Data type is NUMBER.<br>For example: 'sdo_num_res=5'                                                                                                                                                                                                                                       |
| unit           | If the `distance` keyword or the SDO_NN_DISTANCE ancillary operator is included in the call to SDO_NN, specifies the unit of measurement: a quoted string with `unit=` and an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table. See [Unit of Measurement Support](spatial-datatypes-metadata.md) for more information about unit of measurement specification. Data type is VARCHAR2. Default = unit of measurement associated with the data. For geodetic data, the default is meters.<br>For example: 'unit=KM'                  |

#### Returns

This operator returns the `sdo_num_res` number of objects from `geometry1` that are nearest to `geometry2` in the query. In determining how near two geometry objects are, the shortest possible distance between any two points on the surface of each object is used.

#### Usage Notes

**Note:**

SDO_NN operator is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

The operator is disabled if the table does not have a spatial index or if the number of dimensions for the query window does not match the number of dimensions specified when the index was created.

The operator must always be used in a WHERE clause, and the condition that includes the operator should be an expression of the form SDO_NN(arg1, arg2, '\<some_parameter\>') = 'TRUE'. (The expression must not equate to any value other than 'TRUE'.)

The operator can be used in the following ways:

- If all geometries in the layer are candidates, use the `sdo_num_res` keyword to specify the number of geometries returned.

  The `sdo_num_res` keyword is especially useful when you are concerned only with proximity (for example, the three closest banks, regardless of bank name).

- If any geometries in the table might be nearer than the geometries specified in the WHERE clause, use the `sdo_batch_size` keyword and use the WHERE clause (including the ROWNUM pseudocolumn) to limit the number of geometries returned.

  The `sdo_batch_size` keyword is especially useful when you need to consider one or more columns from the same table as the nearest neighbor search column in the WHERE clause (for example, the three closest banks whose name contains MegaBank).

- You can also specify both the `sdo_num_res` and `sdo_batch_size` keywords, as explained later in these Usage Notes.

As an example of the `sdo_batch_size` keyword, assume that a RESTAURANTS table contains different types of restaurants, and you want to find the two nearest Italian restaurants to your hotel but only if they are within two miles. The query might look like the following:

    SELECT r.name FROM restaurants r WHERE
       SDO_NN(r.geometry, :my_hotel,
          'sdo_batch_size=10 distance=2 unit=mile') = 'TRUE'
       AND r.cuisine = 'Italian' AND ROWNUM <=2;

In this example, the `ROWNUM <=2` clause is necessary to limit the number of results returned to no more than 2 where CUISINE is `Italian`. However, if the `sdo_batch_size` keyword is not specified in this example, and if `sdo_num_res=2` is specified instead of `ROWNUM <=2`, only the two nearest restaurants within two miles are considered, regardless of their CUISINE value; and if the CUISINE value of these two rows is not `Italian`, the query may return no rows.

The `sdo_batch_size` value can affect the performance of nearest neighbor queries. A good general guideline is to specify the number of candidate rows likely to satisfy the WHERE clause. Using the preceding example of a query for Italian restaurants, if approximately 20 percent of the restaurants nearest to the hotel are Italian and if you want 2 restaurants, an `sdo_batch_size` value of 10 will probably result in the best performance. On the other hand, if only approximately 5 percent of the restaurants nearest to the hotel are Italian and if you want 2 restaurants, an `sdo_batch_size` value of 40 would be better.

You can specify `sdo_batch_size=0`, which causes Spatial and Graph to calculate a batch size that is suitable for the result set size. However, the calculated batch size may not be optimal, and the calculation incurs some processing overhead; if you can determine a good `sdo_batch_size` value for a query, the performance will probably be better than if you specify `sdo_batch_size=0`.

Specify the `number` parameter only if you are using the SDO_NN_DISTANCE ancillary operator in the call to SDO_NN. See the information about the SDO_NN_DISTANCE operator in this chapter.

If two or more objects from `geometry1` are an equal distance from `geometry2`, any of the objects can be returned on any call to the function. For example, if `item_a`, `item_b`, and `item_c` are nearest to and equally distant from `geometry2,` and if `sdo_num_res=2`, two of those three objects are returned, but they can be any two of the three.

If the SDO_NN operator uses a partitioned spatial index (see [Using Partitioned Spatial Indexes](indexing-querying-spatial-data.md)), the requested number of geometries is returned for each partition that contains candidate rows based on the query criteria. For example, if you request the 5 nearest restaurants to a point and the spatial index has 4 partitions, the operator returns up to 20 (5\*4) geometries. In this case, you must use the ROWNUM pseudocolumn (here, `WHERE ROWNUM <=5`) to return the 5 nearest restaurants.

If `geometry1` and `geometry2` are based on different coordinate systems, `geometry2` is temporarily transformed to the coordinate system of `geometry1` for the operation to be performed, as described in [Different Coordinate Systems for Geometries with Operators and Functions](coordinate-systems-concepts.md).

SDO_NN is not supported for spatial joins.

In some situations the SDO_NN operator will not use the spatial index unless an optimizer hint forces the index to be used. This can occur when a query involves a join; and if the optimizer hint is not used in such situations, an internal error occurs. To prevent such errors, you should always specify an optimizer hint to use the spatial index with the SDO_NN operator, regardless of how simple or complex the query is. For example, the following excerpt from a query specifies to use the COLA_SPATIAL_IDX index that is defined on the COLA_MARKETS table:

    SELECT /*+ INDEX(c cola_spatial_idx) */
      c.mkt_id, c.name, ... FROM cola_markets c, ...;

However, if the column predicate in the WHERE clause specifies any nonspatial column in the table for `geometry1` that has an associated index, be sure that this index is not used by specifying the NO_INDEX hint for that index. For example, if there was an index named COLA_NAME_IDX defined on the NAME column, you would need to specify the hints in the preceding example as follows:

    SELECT /*+ INDEX(c cola_spatial_idx) NO_INDEX(c cola_name_idx) */
      c.mkt_id, c.name, ... FROM cola_markets c, ...;

(Note, however, that there is no index named COLA_NAME_IDX in the example in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

If you join two or more tables with the SDO_NN operator and the `sdo_num_res` keyword, specify the LEADING hint for the outer table, USE_NL hint to have a nested loops join, and the INDEX hint for the inner table (the table with the spatial index). For example:

    SELECT  /*+ LEADING(b) USE_NL(b a) INDEX(a cola_spatial_idx) */ a.gid
       FROM cola_qry  b,  cola_markets  a
          WHERE SDO_NN(a.shape, b.shape, 'sdo_num_res=1')='TRUE';

However, if you join two or more tables with the SDO_NN operator, the `sdo_batch_size` keyword, and the ROWNUM clause, the best way to implement the logic is to use a PL/SQL block. For example:

    BEGIN
      FOR item IN ( SELECT b.shape FROM cola_qry b)
      LOOP
        SELECT  /*+ INDEX(a cola_spatial_idx) */ a.gid INTO local_gid
        FROM cola_markets  a
        WHERE SDO_NN(a.shape, item.shape, 'sdo_batch_size=10')='TRUE'
          and a.name like 'cola%' and ROWNUM <2;
      END LOOP;
    END;

For detailed information about using optimizer hints, see [Oracle Database SQL Tuning Guide](../tgsql/influencing-the-optimizer.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds the two objects from the SHAPE column in the COLA_MARKETS table that are nearest to a specified point (10,7). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT /*+ INDEX(c cola_spatial_idx) */
     c.mkt_id, c.name  FROM cola_markets c  WHERE SDO_NN(c.shape,
       sdo_geometry(2001, NULL, sdo_point_type(10,7,NULL), NULL,
       NULL),  'sdo_num_res=2') = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             4 cola_d

The following example uses the `sdo_batch_size` keyword to find the two objects (ROWNUM \<=2), with a NAME value less than 'cola_d', from the SHAPE column in the COLA_MARKETS table that are nearest to a specified point (10,7). The value of 3 for `sdo_batch_size` represents a best guess at the number of nearest geometries that need to be evaluated before the WHERE clause condition is satisfied. (The example uses the definitions and data from [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT /*+ INDEX(c cola_spatial_idx) */ c.mkt_id, c.name
       FROM cola_markets c
       WHERE SDO_NN(c.shape,  sdo_geometry(2001, NULL,
          sdo_point_type(10,7,NULL), NULL,  NULL),
          'sdo_batch_size=3') = 'TRUE'
       AND c.name < 'cola_d' AND ROWNUM <= 2;

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             3 cola_c

See also the more complex SDO_NN examples in [SDO_NN Examples](complex-spatial-queries.md).

#### Related Topics

- SDO_NN_DISTANCE

**Parent topic:** Spatial Operators

### 20.10 SDO_NN_DISTANCE

#### Format

    SDO_NN_DISTANCE(number);

#### Description

Returns the distance of an object returned by the SDO_NN operator. Valid only within a call to the SDO_NN operator.

#### Keywords and Parameters

| Value  | Description                                                                                                        |
|:-------|:-------------------------------------------------------------------------------------------------------------------|
| number | Specifies a number that must be the same as the last parameter passed to the SDO_NN operator. Data type is NUMBER. |

#### Returns

This operator returns the distance of an object returned by the SDO_NN operator. In determining how near two geometry objects are, the shortest possible distance between any two points on the surface of each object is used.

#### Usage Notes

SDO_NN_DISTANCE is an ancillary operator to the SDO_NN operator. It returns the distance between the specified geometry and a nearest neighbor object. This distance is passed as ancillary data to the SDO_NN operator. (For an explanation of how operators can use ancillary data, see the section on ancillary data in [Oracle Database Data Cartridge Developer's Guide](../addci/defining-operators.md).)

You can choose any arbitrary number for the `number` parameter. The only requirement is that it must match the last parameter in the call to the SDO_NN operator.

Use a bind variable to store and operate on the distance value.

#### Examples

The following example finds the two objects from the SHAPE column in the COLA_MARKETS table that are nearest to a specified point (10,7), and it finds the distance between each object and the point. (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT   /*+ INDEX(c cola_spatial_idx) */
       c.mkt_id, c.name, SDO_NN_DISTANCE(1) dist
       FROM cola_markets c
       WHERE SDO_NN(c.shape,  sdo_geometry(2001, NULL,
          sdo_point_type(10,7,NULL), NULL,  NULL),
          'sdo_num_res=2', 1) = 'TRUE' ORDER BY dist;

        MKT_ID NAME                                   DIST
    ---------- -------------------------------- ----------
             4 cola_d                           .828427125
             2 cola_b                           2.23606798

Note the following about this example:

- 1 is used as the `number` parameter for SDO_NN_DISTANCE, and 1 is also specified as the last parameter to SDO_NN (after `'sdo_num_res=2'`).

- The column alias `dist` holds the distance between the object and the point. (For geodetic data, the distance unit is meters; for non-geodetic data, the distance unit is the unit associated with the data.)

The following example uses the `sdo_batch_size` keyword in selecting the two closest Italian restaurants to your hotel from a YELLOW_PAGES table that contains different types of businesses:

    SELECT * FROM
     (SELECT /*+ FIRST_ROWS */ y.name FROM YELLOW_PAGES  y
      WHERE SDO_NN(y.geometry, :my_hotel, 'sdo_batch_size=100', 1) = 'TRUE'
       AND y.business = 'Italian Restaurant'
      ORDER BY SDO_NN_DISTANCE(1))
    WHERE ROWNUM <=10;

In the preceding query, the FIRST_ROWS hint enables the optimizer to improve performance by pushing the ORDER BY operation into the spatial index. `:my_hotel` can be either a bind variable or a literal value.

The FIRST_ROWS hint is also available to a local partitioned spatial index. In the preceding example, if the YELLOW_PAGES table is partitioned by name, the query will be executed as follows:

1.  For each partition, the ORDER BY operation is processed using the spatial index until 10 rows are found.

2.  After all partitions are completed, all rows found in the preceding step are sorted, and the top 10 rows are returned.

#### Related Topics

- SDO_NN

**Parent topic:** Spatial Operators

### 20.11 SDO_ON

#### Format

    SDO_ON(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the ON topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=ON'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_ON(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the ON topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the ON relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) This example returns no rows because there are no line string geometries in the SHAPE column.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_ON(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(4,6, 8,8))
                ) = 'TRUE';

    no rows selected

**Parent topic:** Spatial Operators

### 20.12 SDO_OVERLAPBDYDISJOINT

#### Format

    SDO_OVERLAPBDYDISJOINT(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the OVERLAPBDYDISJOINT topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=OVERLAPBDYDISJOINT'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_OVERLAPBDYDISJOINT(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the OVERLAPBDYDISJOINT topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the OVERLAPBDYDISJOINT relationship with a line string geometry (here, a horizontal line from 0,6 to 2,6). (The example uses the definitions and data described and illustrated in[Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_a` has the OVERLAPBDYDISJOINT relationship with the line string geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_OVERLAPBDYDISJOINT(c.shape,
                SDO_GEOMETRY(2002, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,2,1),
                  SDO_ORDINATE_ARRAY(0,6, 2,6))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             1 cola_a

**Parent topic:** Spatial Operators

### 20.13 SDO_OVERLAPBDYINTERSECT

#### Format

    SDO_OVERLAPBDYINTERSECT(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the OVERLAPBDYINTERSECT topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=OVERLAPBDYINTERSECT'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_OVERLAPBDYINTERSECT(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the OVERLAPBDYINTERSECT topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the OVERLAPBDYINTERSECT relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, `cola_a`, `cola_b`, and `cola_d` have the OVERLAPBDYINTERSECT relationship with the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_OVERLAPBDYINTERSECT(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(4,6, 8,8))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a
             4 cola_d

**Parent topic:** Spatial Operators

### 20.14 SDO_OVERLAPS

#### Format

    SDO_OVERLAPS(geometry1, geometry2);

#### Description

Checks if any geometries in a table overlap (that is, have the OVERLAPBDYDISJOINT or OVERLAPBDYINTERSECT topological relationship with) a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=OVERLAPBDYDISJOINT+OVERLAPBDYINTERSECT'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

For information about 3D support with Spatial and Graph operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_OVERLAPS(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the OVERLAPBDYDISJOINT or OVERLAPBDYINTERSECT topological relationship, and FALSE otherwise.

#### Usage Notes

For the operator to evaluate to TRUE, the geometries must two polygons, two lines, or two multipoints. For example, if one geometry is a line and other is a polygon, they cannot overlap.

See also the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

#### Examples

The following example finds geometries that overlap a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, three of the geometries in the SHAPE column overlap the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_OVERLAPS(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(4,6, 8,8))
                ) = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a
             4 cola_d

**Parent topic:** Spatial Operators

### 20.15 SDO_POINTINPOLYGON

#### Format

    SDO_POINTINPOLYGON(cur, geom_obj, tol, params) RETURN ANYDATASET;

#### Description

Takes a set of rows, and returns those rows that are within a specified polygon geometry.

#### Keywords and Parameters

| Value    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:---------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cur      | One of the following:<br>• A REF cursor: the first two columns in the SELECT of the SQL for ref_cursor must be an X and Y point coordinates pair from a user table. The two columns must be of type NUMBER. (Any other columns can be number, character, and date types). Data type is SYS_REFCURSOR.<br>• A REF cursor: the first column in the SELECT of the SQL for the ref cursor must be a spatial geometry object from a user table. The column must be of type SDO_GEOMETRY. (Any other columns can be number, character, and date types). Data type is SYS_REFCURSOR. |
| geom_obj | Spatial geometry object: either a geometry from a table or a transient instance of a geometry, against which all of the selected points from `cur` will be checked. Data type is SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                |
| tol      | Tolerance value (see [Tolerance](spatial-concepts.md)). Must be greater than 0.0. Data type is NUMBER.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| params   | Optional parameter string of keywords and values. Determines the behavior of the operator. See Table 20-5 in the Usage Notes for information about the available keywords. Data type is VARCHAR2. Default is NULL.                                                                                                                                                                                                                                                                                                                                                            |

#### Returns

SDO_POINTINPOLYGON returns an object of ANYDATASET TYPE, which is described in [Oracle Database PL/SQL Packages and Types Reference](../arpls/ANYDATASET-TYPE.md). The ANYDATASET output columns are those specified by the `cur` parameter.

#### Usage Notes

SDO_POINTINPOLYGON is technically not an operator, but a table function. (For an explanation of table functions, see [Oracle Database PL/SQL Language Reference](../lnpls/chaining-pipelined-table-functions-multiple-transformations.md).) However, it is presented in the chapter with spatial operators because its usage is similar to that of the operators, and because it is not part of a package with other functions and procedures.

The SQL statement used in the `cur` parameter can have any number of predicates in the WHERE clause. This feature can be used to filter the data on other attributes before passing the resulting rows into the SDO_POINTINPOLYGON operator.

The output columns are identical to the input columns, but the only rows returned are those matching the selection criteria.

Table 20-5 shows the keywords for the `params` parameter.

Table 20-5 params Keywords for the SDO_POINTINPOLYGON Operator

| Keyword        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mask           | The topological relationship of interest. Valid values are 'mask=\<value\>' where \<value\> is one or more of the following: `TOUCH`, `OVERLAPBDYDISJOINT`, `OVERLAPBDYINTERSECT`, `EQUAL`, `INSIDE`, `COVEREDBY`, `CONTAINS`, `COVERS`, `ANYINTERACT`, `ON`. Multiple masks are combined with the logical Boolean operator OR, for example, '`mask=inside+touch'`. See [Spatial Relationships and Filtering](spatial-concepts.md) for an explanation of the nine-intersection relationship pattern.<br>If `cur` is a pair of X and Y point coordinates, `TOUCH` and `ON` are synonymous.<br>If this parameter is null or contains an empty string, `mask=ANYINTERACT` is assumed. |
| sdo_batch_size | Specifies the maximum number of rows that are processed in a batch. The default value is 4000 and the maximum value is 32768. Data type is NUMBER.<br>For example: 'sdo_batch_size=5000'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

To use parallel query servers, you must do either of the following:

- Specify the `/*+ PARALLEL(``<table alias>, <n>``) */` optimizer hint, where \<table_alias\> is the specified table alias and \<n\> is the degree-of-parallelism.

- Enable parallel query execution by entering the following command from a suitably privileged account:

      ALTER SESSION FORCE PARALLEL QUERY;

#### Examples

The following example creates a new table named COLA_MARKET_POINTS based on the data from the COLA_MARKETS table, which is described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md). The example then selects a point within each geometry where the MKT_ID column value is greater than 1. (It uses the [SDO_UTIL.INTERIOR_POINT](SDO_UTIL-reference.md) function to get a point that is guaranteed to be inside each geometry that matches the query criteria.)

    -- Create a new table with a different name based on the data from the
    -- COLA_MARKETS table. This table has four columns: X, Y, MKT_ID, and NAME.

    CREATE TABLE cola_market_points AS
    SELECT a.point.sdo_point.x X, a.point.sdo_point.y Y, MKT_ID, NAME
     FROM (
    SELECT mkt_id, name, sdo_util.interior_point(shape) point FROM cola_markets) a;

    -- Limit to MKT_ID > 1. Also, use the PARALLEL hint.
    SELECT /*+ PARALLEL(a, 4) */ *
    FROM TABLE(sdo_PointInPolygon(
      CURSOR(select * from cola_market_points where mkt_id > 1),
      SDO_GEOMETRY(
        2003,
        NULL,
        NULL,
        MDSYS.SDO_ELEM_INFO_ARRAY(1, 1003, 1),
        MDSYS.SDO_ORDINATE_ARRAY(1, 1, 8, 1, 8, 6, 5, 7, 1, 1)),
      0.05)) a;

             X          Y     MKT_ID NAME
    ---------- ---------- ---------- --------------------------------
        6.3125      2.875          2 cola_b
        4.6875      3.875          3 cola_c

The following example does the same SDO_POINTINPOLYGON query as the previous one, but without the need to create a COLA_MARKET_POINTS table, and where for each row with a MKT_ID column value greater than 1, a point geometry is returned instead the just the X and Y coordinate pair. (The output has been reformatted for readability.)

    -- Limit to MKT_ID > 1. Also, use the PARALLEL hint.
    SELECT /*+ PARALLEL(a, 4) */ name, mkt_id, point
    FROM TABLE(sdo_PointInPolygon(
      CURSOR(select sdo_util.interior_point(shape) point, mkt_id, name
             from cola_markets where mkt_id > 1),
    SDO_GEOMETRY
      2003,
      NULL,
      NULL,
      MDSYS.SDO_ELEM_INFO_ARRAY(1, 1003, 1),
      MDSYS.SDO_ORDINATE_ARRAY(1, 1, 8, 1, 8, 6, 5, 7, 1, 1)),  0.05)) a;

    NAME   MKT_ID  POINT(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    ------ ------- ----------------------------------------------------------------------------
    cola_b   2     SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(6.3125, 2.875, NULL), NULL, NULL)
    cola_c   3     SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(4.6875, 3.875, NULL), NULL, NULL)

The following example uses a bind variable in the WHERE clause, and it specifies a `params` string. It assumes the existence of a table named PIP_DATA.

    DECLARE
     my_cursor SYS_REFCURSOR;
     my_pip_cursor SYS_REFCURSOR;
     stmt varchar2(2000);
     cnt number;
    BEGIN
      stmt := 'SELECT count(*) FROM ' ||
              ' TABLE (Sdo_PointInPolygon(' ||
              'CURSOR(select * from pip_data where x < :x1),' ||
              ' :g1, :tol, ''mask=DISJOINT sdo_batch_size=6000'')) ';
     open my_cursor for stmt
     using 100, -- :x1
           SDO_GEOMETRY( 2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1, 1003, 1),
                  SDO_ORDINATE_ARRAY(10, 10, 70,10, 70, 70, 50,70,
                                     40,50, 20,70, 10,70, 10,10)), -- :g1
           0.05; -- :tol
     FETCH my_cursor into cnt;
     dbms_output.put_line(to_char(cnt));
    END;
    /

#### Related Topics

- [SDO_UTIL.INTERIOR_POINT](SDO_UTIL-reference.md)

**Parent topic:** Spatial Operators

### 20.16 SDO_RELATE

#### Format

    SDO_RELATE(geometry1, geometry2,  param);

#### Description

Identifies either the spatial objects that have a particular spatial interaction with a given object such as an area of interest, or pairs of spatial objects that have a particular spatial interaction.

This operator performs both primary and secondary filter operations.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| param     | Specifies the `mask` keyword, and optionally either or both of the `min_resolution` and `max_resolution` keywords. The data type for this parameter is VARCHAR2.<br>The `mask` keyword specifies the topological relationship of interest. This is a required parameter. Valid `mask` keyword values are one or more of the following in the nine-intersection pattern: `TOUCH`, `OVERLAPBDYDISJOINT`, `OVERLAPBDYINTERSECT`, `EQUAL`, `INSIDE`, `COVEREDBY`, `CONTAINS`, `COVERS`, `ANYINTERACT`, `ON`. Multiple masks are combined with the logical Boolean operator OR, for example, '`mask=inside+touch'`. See [Spatial Relationships and Filtering](spatial-concepts.md) for an explanation of the nine-intersection relationship pattern.<br>The `min_resolution` keyword includes only geometries for which at least one side of the geometry's MBR is equal to or greater than the specified value. For example, `min_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is at least 10. (This keyword can be used to exclude geometries that are too small to be of interest.)<br>The `max_resolution` keyword includes only geometries for which at least one side of the geometry's MBR is less than or equal to the specified value. For example, `max_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is less than or equal to 10. (This keyword can be used to exclude geometries that are too large to be of interest.)<br>For backward compatibility, any additional keywords for the `param` parameter that were supported before release 10.1 will still work; however, the use of those keywords is discouraged and is not supported for new uses of the operator. |

#### Returns

The expression SDO_RELATE(geometry1,geometry2, 'mask = \<some_mask_val\>') = 'TRUE' evaluates to TRUE for object pairs that have the topological relationship specified by \<some_mask_val\>, and FALSE otherwise.

#### Usage Notes

The operator is disabled if the number of dimensions for the query window does not match the number of dimensions specified when the index was created.

The operator must always be used in a WHERE clause, and the condition that includes the operator should be an expression of the form SDO_RELATE(arg1, arg2, 'mask = \<some_mask_val\>') = 'TRUE'. (The expression must not equate to any value other than 'TRUE'.)

`geometry2` can come from a table or be a transient SDO_GEOMETRY object, such as a bind variable or SDO_GEOMETRY constructor.

- If the `geometry2` column is not spatially indexed, the operator indexes the query window in memory and performance is very good.

- If `geometry2` passed to the operator originates from a table or view, the LEADING optimizer hint is not required, but may be helpful to inform the optimizer the driving table or view in the query should be the one that contains `geometry2`. The table or view specified in the LEADING hint should correspond to the table name or view name that contains `geometry2`. If the table or view is aliased in the FROM clause, the alias should be specified in the LEADING hint.

If `geometry1` and `geometry2` are based on different coordinate systems, `geometry2` is temporarily transformed to the coordinate system of `geometry1` for the operation to be performed, as described in [Different Coordinate Systems for Geometries with Operators and Functions](coordinate-systems-concepts.md).

Unlike with the [SDO_GEOM.RELATE](SDO_GEOM-reference.md) function, DISJOINT and DETERMINE masks are not allowed in the relationship mask with the SDO_RELATE operator. This is because SDO_RELATE uses the spatial index (if one is available) to find candidates that may interact, and the information to satisfy DISJOINT or DETERMINE is not present in the index.

Multiple masks can be combined using the logical Boolean operator OR, for example, `'mask=touch+coveredby'`. Effective with Release 12.1, if you set the SPATIAL_VECTOR_ACCELERATION system parameter to `TRUE` (highly recommended, as explained in [SPATIAL_VECTOR_ACCELERATION System Parameter](spatial-concepts.md)), you do not need to use UNION ALL with such masks. However, if you are not setting SPATIAL_VECTOR_ACCELERATION to `TRUE`, better performance may result if the spatial query specifies each mask individually and uses the UNION ALL syntax to combine the results. This is due to internal optimizations that Spatial and Graph can apply under certain conditions when masks are specified singly rather than grouped within the same SDO_RELATE operator call. (There are two exceptions, `inside+coveredby` and `contains+covers`, where the combination performs better than the UNION ALL alternative.)

For example, consider the following query using the logical Boolean operator OR to group multiple masks:

    SELECT a.gid
      FROM polygons a, query_polys B
      WHERE B.gid = 1
      AND SDO_RELATE(A.Geometry, B.Geometry,
                       'mask=touch+coveredby') = 'TRUE';

If SPATIAL_VECTOR_ACCELERATION is `TRUE`, then preceding query is simplest and has the best performance. However, if SPATIAL_VECTOR_ACCELEERATION is `FALSE`, the preceding query may result in better performance if it is expressed as follows, using UNION ALL to combine results of multiple SDO_RELATE operator calls, each with a single mask:

    SELECT a.gid
          FROM polygons a, query_polys B
          WHERE B.gid = 1
          AND SDO_RELATE(A.Geometry, B.Geometry,
                       'mask=touch') = 'TRUE'
    UNION ALL
    SELECT a.gid
          FROM polygons a, query_polys B
          WHERE B.gid = 1
          AND SDO_RELATE(A.Geometry, B.Geometry,
                       'mask=coveredby') = 'TRUE';

The following considerations apply to relationships between lines and a multipoint geometry (points in a point cluster). Assume the example of a line and a multipoint geometry (for example, SDO_GTYPE = 2005) consisting of three points.

- If none of the points has any interaction with the line, the relationship between the line and the point cluster is DISJOINT.

- If one of the points is on the interior of the line and the other two points are disjoint, the relationship between the line and the point cluster is OVERLAPBDYDISJOINT.

- If one of the points is on the boundary of the line (that is, if it is on the start point or end point of the line) and the other two points are disjoint, the relationship between the line and the point cluster is TOUCH.

- If one of the points is on the boundary of the line (that is, if it is on the start point or end point of the line), another point is on the interior of the line, and the third point is disjoint, the relationship between the line and the point cluster is OVERLAPBDYDISJOINT (not OVERLAPBDYINTERSECT).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following examples are similar to those for the SDO_FILTER operator; however, they identify a specific type of interaction (using the `mask` keyword), and they determine with certainty (not mere likelihood) if the spatial interaction occurs.

The following example selects the geometries that have any interaction with a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).)

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_RELATE(c.shape,
        SDO_GEOMETRY(2003, NULL, NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3),
          SDO_ORDINATE_ARRAY(4,6, 8,8)),
        'mask=anyinteract') = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a
             4 cola_d

The following example is the same as the preceding example, except that it includes only geometries where at least one side of the geometry's MBR is equal to or greater than 4.1. In this case, only `cola_a` and `cola_b` are returned, because their MBRs have at least one side with a length greater than or equal to 4.1. The circle `cola_d` is excluded, because its MBR is a square whose sides have a length of 4.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_RELATE(c.shape,
        SDO_GEOMETRY(2003, NULL, NULL,
          SDO_ELEM_INFO_ARRAY(1,1003,3),
          SDO_ORDINATE_ARRAY(4,6, 8,8)),
        'mask=anyinteract min_resolution=4.1') = 'TRUE';

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b
             1 cola_a

The following example selects the GID values from the POLYGONS table where the GEOMETRY column objects have any spatial interaction with the GEOMETRY column object in the QUERY_POLYS table that has a GID value of 1.

    SELECT A.gid
      FROM Polygons A, query_polys B
      WHERE B.gid = 1
      AND SDO_RELATE(A.Geometry, B.Geometry,
                       'mask=ANYINTERACT') = 'TRUE';

The following example selects the GID values from the POLYGONS table where a GEOMETRY column object has any spatial interaction with the geometry stored in the `aGeom` variable.

    SELECT A.Gid
      FROM Polygons A
      WHERE SDO_RELATE(A.Geometry, :aGeom, 'mask=ANYINTERACT') = 'TRUE';

The following example selects the GID values from the POLYGONS table where a GEOMETRY column object has any spatial interaction with the specified rectangle having the lower-left coordinates (x1,y1) and the upper-right coordinates (x2, y2).

    SELECT A.Gid
      FROM Polygons A
      WHERE SDO_RELATE(A.Geometry, sdo_geometry(2003,NULL,NULL,
                                       sdo_elem_info_array(1,1003,3),
                                       sdo_ordinate_array(x1,y1,x2,y2)),
                         'mask=ANYINTERACT') = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object has any spatial interaction with any GEOMETRY column object in the QUERY_POLYS table. In this example, the LEADING optimizer hint is used and QUERY_POLYS (`geometry2`) table is specified first in the FROM clause, because multiple geometries from `geometry2` are involved (see the Usage Notes).

    SELECT /*+ LEADING(B) */
      A.gid
      FROM query_polys B, polygons A
      WHERE SDO_RELATE(A.Geometry, B.Geometry, 'mask=ANYINTERACT') = 'TRUE';

#### Related Topics

- SDO_FILTER

- SDO_JOIN

- SDO_WITHIN_DISTANCE

- [SDO_GEOM.RELATE](SDO_GEOM-reference.md) function

**Parent topic:** Spatial Operators

### 20.17 SDO_TOUCH

#### Format

    SDO_TOUCH(geometry1, geometry2);

#### Description

Checks if any geometries in a table have the TOUCH topological relationship with a specified geometry. Equivalent to specifying the SDO_RELATE operator with `'mask=TOUCH'`.

See the section on the SDO_RELATE operator in this chapter for information about the operations performed by this operator and for usage requirements.

#### Keywords and Parameters

| Value     | Description                                                                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1 | Specifies a geometry column in a table. A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                         |
| geometry2 | Specifies either a geometry from a table or a transient instance of a geometry. (Specified using a bind variable or SDO_GEOMETRY constructor.) Data type is SDO_GEOMETRY. |

#### Returns

The expression SDO_TOUCH(geometry1,geometry2) = 'TRUE' evaluates to TRUE for object pairs that have the TOUCH topological relationship, and FALSE otherwise.

#### Usage Notes

See the Usage Notes for the SDO_RELATE operator in this chapter.

For an explanation of the topological relationships and the nine-intersection model used by Spatial and Graph, see [Spatial Relationships and Filtering](spatial-concepts.md).

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example finds geometries that have the TOUCH relationship with a query window (here, a rectangle with lower-left, upper-right coordinates 1,1, 5,7). (The example uses the definitions and data in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md).) In this example, only `cola_b` has the TOUCH relationship with the query window geometry.

    SELECT c.mkt_id, c.name
      FROM cola_markets c
      WHERE SDO_TOUCH(c.shape,
                SDO_GEOMETRY(2003, NULL, NULL,
                  SDO_ELEM_INFO_ARRAY(1,1003,3),
                  SDO_ORDINATE_ARRAY(1,1, 5,7))
                ) = 'TRUE';
      FROM cola_markets c

        MKT_ID NAME
    ---------- --------------------------------
             2 cola_b

**Parent topic:** Spatial Operators

### 20.18 SDO_WITHIN_DISTANCE

#### Format

    SDO_WITHIN_DISTANCE(geometry1, aGeom, params);

#### Description

Identifies the set of spatial objects that are within some specified distance of a given object, such as an area of interest or point of interest.

#### Keywords and Parameters

| Value          | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| geometry1      | Specifies a geometry column in a table. The column has the set of geometry objects that will be operated on to determine if they are within the specified distance of the given object (`aGeom`). A spatial index on this column is recommended. Data type is SDO_GEOMETRY.                                                                                                                                 |
| aGeom          | Specifies the object to be checked for distance against the geometry objects in `geometry1`. Specify either a geometry from a table (using a bind variable) or a transient instance of a geometry (using the SDO_GEOMETRY constructor). Data type is SDO_GEOMETRY.                                                                                                                                          |
| params         | A quoted string containing one or more keywords (with values) that determine the behavior of the operator. The remaining items (`distance`, `ellipsoidal`, `max_resolution`, `min_resolution`, `querytype`, and `unit`) are potential keywords for the `params` parameter. Data type is VARCHAR2.                                                                                                           |
| distance       | Specifies the distance value. If a coordinate system is associated with the geometry, the distance unit is assumed to be the unit associated with the coordinate system. This is a required keyword. Data type is NUMBER.                                                                                                                                                                                   |
| ellipsoidal    | Specifies if ellipsoidal distance is always used with geodetic data (`true`), or if spherical distance is used in some cases (`false`, the default). See [Distance: Spherical versus Ellipsoidal with Geodetic Data](coordinate-systems-concepts.md).<br>For example: 'ellipsoidal=true'                                                                                                                    |
| max_resolution | Includes only geometries for which at least one side of the geometry's MBR is less than or equal to the specified value. For example, `max_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is less than or equal to 10. (This keyword can be used to exclude geometries that are too large to be of interest.)                                    |
| min_resolution | Includes only geometries for which at least one side of the geometry's MBR is equal to or greater than the specified value. For example, `min_resolution=10` includes only geometries for which the width or the height (or both) of the geometry's MBR is at least 10. (This keyword can be used to exclude geometries that are too small to be of interest.)                                              |
| querytype      | Set `'querytype=FILTER'` to perform only a primary filter operation. If `querytype` is not specified, both primary and secondary filter operations are performed (default). Data type is VARCHAR2.                                                                                                                                                                                                          |
| unit           | Specifies the unit of measurement: a quoted string with `unit=` and an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `'unit=KM'`). See [Unit of Measurement Support](spatial-datatypes-metadata.md) for more information about unit of measurement specification. Data type is NUMBER. Default = unit of measurement associated with the data. For geodetic data, the default is meters. |

#### Returns

The expression SDO_WITHIN_DISTANCE(arg1, arg2, arg3) = 'TRUE' evaluates to TRUE for object pairs that are within the specified distance, and FALSE otherwise.

#### Usage Notes

**Note:**

SDO_WITHIN_DISTANCE operator is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

The distance between two extended objects (nonpoint objects such as lines and polygons) is defined as the minimum distance between these two objects. The distance between two adjacent polygons is zero.

The operator is disabled if the number of dimensions for the query window does not match the number of dimensions specified when the spatial index (if one is being used) was created.

The operator must always be used in a WHERE clause and the condition that includes the operator should be an expression of the form:

    SDO_WITHIN_DISTANCE(arg1, arg2, 'distance = <some_dist_val>') = 'TRUE'

(The expression must not equate to any value other than 'TRUE'.)

The geometry column must have a spatial index built on it. If the data is geodetic, the spatial index must be an R-tree index.

SDO_WITHIN_DISTANCE is not supported for spatial joins. See [Within-Distance Operator](indexing-querying-spatial-data.md) for a discussion on how to perform a spatial join within-distance operation.

For information about 3D support with spatial operators (which operators do and do not consider all three dimensions in their computations), see [Three-Dimensional Spatial Objects](spatial-concepts.md).

#### Examples

The following example selects the geometries that are within a distance of 10 from a query window (here, a rectangle with lower-left, upper-right coordinates 4,6, 8,8). (The example uses the definitions and data described and illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md). In this case, all geometries shown in that figure are returned.)

    SELECT c.name FROM cola_markets c WHERE SDO_WITHIN_DISTANCE(c.shape,
      SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(4,6, 8,8)),
      'distance=10') = 'TRUE';

    NAME
    --------------------------------
    cola_b
    cola_a
    cola_c
    cola_d

The following example is the same as the preceding example, except that it includes only geometries where at least one side of the geometry's MBR is equal to or greater than 4.1. In this case, only `cola_a` and `cola_b` are returned, because their MBRs have at least one side with a length greater than or equal to 4.1. The trapezoid `cola_c` is excluded, because its MBR has sides with lengths of 3 and 2; and the circle `cola_d` is excluded, because its MBR is a square whose sides have a length of 4.

    SELECT c.name FROM cola_markets c WHERE SDO_WITHIN_DISTANCE(c.shape,
      SDO_GEOMETRY(2003, NULL, NULL, SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(4,6, 8,8)),
      'distance=10 min_resolution=4.1') = 'TRUE';

    NAME
    --------------------------------
    cola_b
    cola_a

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object is within 10 distance units of the geometry stored in the `aGeom` variable.

    SELECT A.GID
      FROM POLYGONS A
      WHERE
        SDO_WITHIN_DISTANCE(A.Geometry, :aGeom, 'distance = 10') = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GEOMETRY column object is within 10 distance units of the specified rectangle having the lower-left coordinates (x1,y1) and the upper-right coordinates (x2, y2).

    SELECT A.GID
      FROM POLYGONS A
      WHERE
        SDO_WITHIN_DISTANCE(A.Geometry, sdo_geometry(2003,NULL,NULL,
                                 sdo_elem_info_array(1,1003,3),
                                 sdo_ordinate_array(x1,y1,x2,y2)),
                         'distance = 10') = 'TRUE';

The following example selects the GID values from the POLYGONS table where the GID value in the QUERY_POINTS table is 1 and a POLYGONS.GEOMETRY object is within 10 distance units of the QUERY_POINTS.GEOMETRY object.

    SELECT A.GID
      FROM POLYGONS A, Query_Points B
      WHERE B.GID = 1 AND
        SDO_WITHIN_DISTANCE(A.Geometry, B.Geometry, 'distance = 10') = 'TRUE';

See also the more complex SDO_WITHIN_DISTANCE examples in [SDO_WITHIN_DISTANCE Examples](complex-spatial-queries.md).

#### Related Topics

- SDO_FILTER

- SDO_RELATE

**Parent topic:** Spatial Operators
