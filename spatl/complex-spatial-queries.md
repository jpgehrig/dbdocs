## B  Complex Spatial Queries: Examples

This appendix provides examples, with explanations, of queries that are more complex than the examples in the reference chapters.

This appendix focuses on operators that are frequently used in Spatial and Graph applications, such as [SDO_WITHIN_DISTANCE](spatial-operators-reference.md) and [SDO_NN](spatial-operators-reference.md).

This appendix is based on input from Oracle personnel who provide support and training to Spatial and Graph users. The Oracle Spatial and Graph training course covers many of these examples, and provides additional examples and explanations.

Before you use any of the examples in this appendix, be sure you understand the usage and reference information for the relevant operator or function in [Conceptual and Usage Information](spatial-concepts-usage.md) and [Reference Information](spatial-reference-information.md) .

- Tables Used in the Examples
- SDO_WITHIN_DISTANCE Examples
- SDO_NN Examples

**Parent topic:** [Supplementary Information](spatial-supplementary-information.md)

### B.1 Tables Used in the Examples

The examples in this appendix refer to tables named GEOD_CITIES, GEOD_COUNTIES, and GEOD_INTERSTATES, which are defined as follows:

    CREATE TABLE GEOD_CITIES(
      LOCATION     SDO_GEOMETRY,
      CITY         VARCHAR2(42),
      STATE_ABRV   VARCHAR2(2),
      POP90        NUMBER,
      RANK90       NUMBER);

    CREATE TABLE GEOD_COUNTIES(
      COUNTY_NAME   VARCHAR2(40),
      STATE_ABRV    VARCHAR2(2),
      GEOM          SDO_GEOMETRY);

    CREATE TABLE GEOD_INTERSTATES(
      HIGHWAY   VARCHAR2(35),
      GEOM      SDO_GEOMETRY);

**Parent topic:** Complex Spatial Queries: Examples

### B.2 SDO_WITHIN_DISTANCE Examples

The [SDO_WITHIN_DISTANCE](spatial-operators-reference.md) operator identifies the set of spatial objects that are within some specified distance of a given object. You can indicate that the distance is approximate or exact. If you specify `querytype=FILTER`, the distance is approximate because only a primary filter operation is performed; otherwise, the distance is exact because both primary and secondary filtering operations are performed.

Example B-1 Finding All Cities Within a Distance of a Highway

Example B-1 finds all cities within 15 miles of the interstate highway I170.

    SELECT /*+ ORDERED */ c.city
    FROM geod_interstates i, geod_cities c
    WHERE i.highway = 'I170'
       AND sdo_within_distance (
            c.location, i.geom,
           'distance=15 unit=mile') = 'TRUE';

Example B-1 finds all cities within 15 miles (`'distance=15 unit=mile'`) of the specified highway (`i.highway = 'I170'`), and by default the result is exact (because the `querytype` parameter was not used to limit the query to a primary filter operation). In the `WHERE` clause of this example:

- `i.highway` refers to the HIGHWAY column of the INTERSTATES table, and `I170` is a value from the HIGHWAY column.

- `c.location` specifies the search column (`geometry1`). This is the LOCATION column of the GEOD_CITIES table.

- `i.geom` specifies the query window (`aGeom`). This is the spatial geometry in the GEOM column of the GEOD_INTERSTATES table, in the row whose HIGHWAY column contains the value `I170`.

Example B-2 Finding All Highways Within a Distance of a City

Example B-2 finds all interstate highways within 15 miles of the city of Tampa.

    SELECT /*+ ORDERED */ i.highway
    FROM geod_cities c, geod_interstates i
    WHERE c.city = 'Tampa'
       AND sdo_within_distance (
            i.geom, c.location,
            'distance=15 unit=mile') = 'TRUE';

Example B-2 finds all highways within 15 miles (`'distance=15 unit=mile'`) of the specified city (`c.city = 'Tampa'`), and by default the result is exact (because the `querytype` parameter was not used to limit the query to a primary filter operation). In the `WHERE` clause of this example:

- `c.city` refers to the CITY column of the GEOD_CITIES table, and `Tampa` is a value from the CITY column.

- `i.geom` specifies the search column (`geometry1`). This is the GEOM column of the GEOD_INTERSTATES table.

- `c.location` specifies the query window (`aGeom`). This is the spatial geometry in the LOCATION column of the GEOD_CITIES table, in the row whose CITY column contains the value `Tampa`.

**Parent topic:** Complex Spatial Queries: Examples

### B.3 SDO_NN Examples

The [SDO_NN](spatial-operators-reference.md) operator determines the nearest neighbor geometries to a geometry. No assumptions should be made about the order of the returned results, unless you specify the [SDO_NN_DISTANCE](spatial-operators-reference.md) ancillary operator in the ORDER BY clause to have the results returned in distance order. If you specify no optional parameters, one nearest neighbor geometry is returned.

If you specify the optional `sdo_num_res` keyword, you can request how many nearest neighbors you want, but no other conditions in the WHERE clause are evaluated. For example, assume that you want the five closest banks from an intersection, but only where the bank name is `CHASE`. If the five closest banks are not named `CHASE`, [SDO_NN](spatial-operators-reference.md) with `sdo_num_res=5` will return no rows because the `sdo_num_res` keyword only takes proximity into account, and not any other conditions in the WHERE clause.

If you specify the optional `sdo_batch_size` keyword, any `sdo_num_res` specification is ignored, and [SDO_NN](spatial-operators-reference.md) keeps returning neighbor geometries in distance order to the WHERE clause. If the WHERE clause specifies `bank_name = 'CHASE' AND rownum < 6`, you can return the five closest banks with `bank_name = 'CHASE'`.

[SDO_NN_DISTANCE](spatial-operators-reference.md) is an ancillary operator to the SDO_NN operator. It returns the distance of an object returned by the [SDO_NN](spatial-operators-reference.md) operator and is valid only within a call to the [SDO_NN](spatial-operators-reference.md) operator.

See also [Example 5-1](indexing-querying-spatial-data.md)in [Using Partitioned Spatial Indexes](indexing-querying-spatial-data.md).

Example B-3 Finding the Cities Nearest to a Highway

Example B-3 finds the five cities nearest to the interstate highway I170 and the distance in miles from the highway for each city, ordered by distance in miles.

    SELECT /*+ ORDERED */
           c.city,
           sdo_nn_distance (1) distance_in_miles
    FROM geod_interstates i,
         geod_cities c
    WHERE i.highway = 'I170'
      AND sdo_nn(c.location, i.geom,
                 'sdo_num_res=5 unit=mile', 1) = 'TRUE'
    ORDER BY distance_in_miles;

In Example B-3, because the `/*+ ORDERED*/` optimizer hint is used, it is important to have an index on the GEOD_INTERSTATES.HIGHWAY column. In this example, the hint forces the query to locate highway I170 before it tries to find nearest neighbor geometries. In the `WHERE` clause of this example:

- `i.highway` refers to the HIGHWAY column of the GEOD_INTERSTATES table, and `I170` is a value from the HIGHWAY column.

- `c.location` specifies the search column (`geometry1`). This is the LOCATION column of the GEOD_CITIES table.

- `i.geom` specifies the query window (`geometry2`). This is the spatial geometry in the GEOM column of the GEOD_INTERSTATES table, in the row whose HIGHWAY column contains the value `I170`.

- `sdo_num_res=5` specifies how many nearest neighbor geometries to find.

- `unit=mile` specifies the unit of measurement to associate with distances returned by the [SDO_NN_DISTANCE](spatial-operators-reference.md) ancillary operator.

- `1` (in `sdo_nn_distance (1)` and `'sdo_num_res=5 unit=mile', 1`) is the `number` parameter value that associates the call to [SDO_NN](spatial-operators-reference.md) with the call to [SDO_NN_DISTANCE](spatial-operators-reference.md).

In Example B-3, `ORDER BY distance_in_miles` orders the results from the WHERE clause by distance in miles.

The statement in Example B-3 produces the following output (slightly reformatted for readability):

    CITY                    DISTANCE_IN_MILES
    ----------------------  ------------------------------
    St Louis                  5.36297295
    Springfield              78.7997464
    Peoria                  141.478022
    Evansville              158.22422
    Springfield             188.508631

Example B-4 Finding the Cities Above a Specified Population Nearest to a Highway

Example B-4 extends Example B-3 by limiting the results to cities with a 1990 population over a certain number. It finds the five cities nearest to the interstate highway I170 that have a population greater than 300,000, the 1990 population for each city, and the distance in miles from the highway for each city, ordered by distance in miles.

    SELECT /*+ ORDERED  NO_INDEX(c pop90_idx) */
           c.city, pop90,
           sdo_nn_distance (1) distance_in_miles
    FROM geod_interstates i,
         geod_cities c
    WHERE i.highway = 'I170'
      AND sdo_nn(c.location, i.geom,
                'sdo_batch_size=10 unit=mile', 1) = 'TRUE'
      AND c.pop90 > 300000
      AND rownum < 6
    ORDER BY distance_in_miles;

In Example B-4, because the `ORDERED` optimizer hint is used, it is important to have an index on the GEOD_INTERSTATES.HIGHWAY column. In this example, the hint forces the query to locate highway I170 before it tries to find nearest neighbor geometries.

To ensure correct results, disable all nonspatial indexes on columns that come from the same table as the SDO_NN search column (`geometry1`). In this example, the `NO_INDEX(c pop90_idx)` optimizer hint disables the nonspatial index on the POP90 column.

In the `WHERE` clause of this example:

- `sdo_batch_size=10` causes geometries to be returned continually (in distance order, in batches of 10 geometries), to be checked to see if they satisfy the other conditions in the WHERE clause.

- `c.pop90 > 300000` restricts the results to rows where the POP90 column value is greater than 300000.

- `rownum < 6` limits the number of results returned to five.

In Example B-4, `ORDER BY distance_in_miles` orders the results from the WHERE clause by distance in miles.

The statement in Example B-4 produces the following output (slightly reformatted for readability):

    CITY               POP90    DISTANCE_IN_MILES
    -----------------  -------  ---------------------
    St Louis            396685     5.36297295
    Kansas City         435146   227.404883
    Indianapolis        741952   234.708666
    Memphis             610337   244.202072
    Chicago            2783726   253.547961

**Parent topic:** Complex Spatial Queries: Examples
