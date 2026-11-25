## B SEM_MATCH Support for Spatial Queries

This appendix provides reference information for SPARQL extension functions for performing spatial queries in SEM_MATCH.

**Note:**

If you are using an Autonomous Database instance in a shared deployment, then the SEM_MATCH table function requires Oracle JVM to be enabled. See [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless to enable Oracle JVM on your Autonomous Database instance.

To use these functions, you must understand the concepts explained in [Spatial Support](rdf-semantic-graph-overview.md).

**Note:**

Throughout this appendix `geomLiteral` is used as a placeholder for `orageo:WKTLiteral`, `ogc:wktLiteral`, and `ogc:gmlLiteral`, which can be used interchangeably, in format representations and parameter descriptions. (However, `orageo:WKTLiteral` or `ogc:wktLiteral` is used in actual examples.)

This appendix includes the GeoSPARQL and Oracle-specific functions which are explained in the following sections:

- GeoSPARQL Functions for Spatial Support
- Oracle-Specific Functions for Spatial Support

### B.1 GeoSPARQL Functions for Spatial Support

This section provides reference information about the GeoSPARQL functions:

- ogcf:boundary
- ogcf:buffer
- ogcf:convexHull
- ogcf:difference
- ogcf:distance
- ogcf:envelope
- ogcf:getSRID
- ogcf:intersection
- ogcf:relate
- ogcf:sfContains
- ogcf:sfCrosses
- ogcf:sfDisjoint
- ogcf:sfEquals
- ogcf:sfIntersects
- ogcf:sfOverlaps
- ogcf:sfTouches
- ogcf:sfWithin
- ogcf:symDifference
- ogcf:union

**Parent topic:** SEM_MATCH Support for Spatial Queries

#### B.1.1 ogcf:boundary

##### Format

ogcf:boundary(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry object that is the closure of the boundary of `geom`.

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the boundaries of U.S. Congressional district polygons.

    SELECT cb
    FROM table(sem_match(
    'SELECT (ogcf:boundary(?cgeom) AS ?cb)
     WHERE
     { ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.2 ogcf:buffer

##### Format

ogcf:buffer(geom : geomLiteral, radius : xsd:decimal, units : xsd:anyURI) : ogc:wktLiteral

##### Description

Returns a buffer polygon the specified radius (measured in units) around a geometry.

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

radius
Radius value used to define the buffer.

units
Unit of measurement: a URI of the form `<http://xmlns.oracle.com/rdf/geo/uom/{SDO_UNIT}>` (for example, `<http://xmlns.oracle.com/rdf/geo/uom/KM>`). Any SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table will be recognized. See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons that are within a 100–kilometer buffer around a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (
         ogcf:sfWithin(?cgeom,
           ogcf:buffer("POINT(-71.46444 42.7575)"^^ogc:wktLiteral,
                         100,
                         <http://xmlns.oracle.com/rdf/geo/uom/KM>))) }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.3 ogcf:convexHull

##### Format

ogcf:convexHull(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a polygon geometry that represents the convex hull of geom. (The convex hull is a simple convex polygon that completely encloses the geometry object, using as few straight-line sides as possible to create the smallest polygon that completely encloses the geometry object.)

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons whose convex hull contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfContains(ogcf:convexHull(?cgeom),
          "POINT(-71.46444 42.7575)"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.4 ogcf:difference

##### Format

ogcf:difference(geom1 : geomLiteral, geom2 : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry object that is the topological difference (MINUS operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is within the difference of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfWithin(orageo:centroid(?cgeom),
            ogcf:difference(
              "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral,
              "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^ogc:wktLiteral))) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.5 ogcf:distance

##### Format

ogcf:distance(geom1 : geomLiteral, geom2 : geomLiteral, units : xsd:anyURI) : xsd:decimal

##### Description

Returns the distance in units between the two closest points of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

units
Unit of measurement: a URI of the form `<http://xmlns.oracle.com/rdf/geo/uom/{SDO_UNIT}>` (for example, `<http://xmlns.oracle.com/rdf/geo/uom/KM>`). Any SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table will be recognized. See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example orders U.S. Congressional districts based on distance from a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    'SELECT ?name ?cdist
     WHERE
     { # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
     }
     ORDER BY ASC(ogcf:distance(?cgeom,
                    "POINT(-71.46444 42.7575)"^^ogc:wktLiteral,
                    <http://xmlns.oracle.com/rdf/geo/uom/KM>))'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '))
    ORDER BY sem$rownum;

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.6 ogcf:envelope

##### Format

ogcf:envelope(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns the minimum bounding rectangle (MBR) of `geom`, that is, the single rectangle that minimally encloses `geom`.

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons whose minimum bounding rectangle contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfContains(ogcf:envelope(?cgeom),
          "POINT(-71.46444 42.7575)"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.7 ogcf:getSRID

##### Format

ogcf:getSRID(geom : geomLiteral) : xsd:anyURI

##### Description

Returns the spatial reference system URI for `geom`.

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

The URI returned has the form `<http://www.opengis.net/def/crs/EPSG/0/{srid}>`, where `{srid}` is a valid spatial reference system ID from the European Petroleum Survey Group (EPSG).

For URIs that are not in the EPSG Geodetic Parameter Dataset, the URI returned has the form `<http://xmlns.oracle.com/rdf/geo/srid/{srid}>` , where `{srid}` is a valid spatial reference system ID from Oracle Spatial and Graph.

For the default spatial reference system, WGS84 Longitude-Latitude, the URI `<http://www.opengis.net/def/crs/OGC/1.3/CRS84>` is returned.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds spatial reference system URIs for U.S. Congressional district polygons.

    SELECT csrid
    FROM table(sem_match(
    'SELECT (ogcf:getSRID(?cgeom) AS ?csrid)
     WHERE
     { ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.8 ogcf:intersection

##### Format

ogcf:intersection (geom1 : geomLiteral, geom2 : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry object that is the topological intersection (AND operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is within the intersection of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfWithin(orageo:centroid(?cgeom),
            ogcf:intersection(
               "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral,
               "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^ogc:wktLiteral))) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.9 ogcf:relate

##### Format

ogcf:relate(geom1 : geomLiteral, geom2 : geomLiteral, pattern-matrix : xsd:string) : xsd:boolean

##### Description

Returns `true` if the topological relationship between `geom1` and `geom2` satisfies the specified DE-9IM pattern-matrix. Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

pattern-matrix
A dimensionally extended 9-intersection model (DE-9IM) intersection pattern string consisting of `T` (true) and `F` (false) values. A DE-9IM pattern string describes the intersections between the interiors, boundaries, and exteriors of two geometries.

##### Usage Notes

When invoking `ogcf:relate` with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:relate` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:relate` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See the OGC Simple Features Specification (OGC 06-103r3) for a detailed description of DE-9IM intersection patterns. See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district that contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:relate(?cgeom,
          "POINT(-71.46444 42.7575)"^^ogc:wktLiteral,
          "TTTFFTFFT")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '
    ));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.10 ogcf:sfContains

##### Format

ogcf:sfContains(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if `geom1` spatially contains `geom2` as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfContains` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfContains` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that spatially contain a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfContains(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.11 ogcf:sfCrosses

##### Format

ogcf:sfCrosses(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if `geom1` spatially crosses `geom2` as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfCrosses` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfCrosses` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that spatially cross a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfCrosses(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.12 ogcf:sfDisjoint

##### Format

ogcf:fDisjoint(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if the two geometries are spatially disjoint as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

The `ogcf:sfDisjoint` filter cannot use a spatial index for evaluation, so performance will probably be much worse than with other simple features spatial functions.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that are spatially disjoint from a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfDisjoint(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.13 ogcf:sfEquals

##### Format

ogcf:sfEquals(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if the two geometries are spatially equal as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfEquals` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfEquals` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing , indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that are spatially equal to a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfEquals(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.14 ogcf:sfIntersects

##### Format

ogcf:sfIntersects(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if the two geometries are not disjoint as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfIntersects` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfIntersects` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that intersect a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfIntersects(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.15 ogcf:sfOverlaps

##### Format

ogcf:sfOverlaps(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if `geom1` spatially overlaps `geom2` as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfOverlaps` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfOverlaps` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that spatially overlap a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfOverlaps(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.16 ogcf:sfTouches

##### Format

ogcf:sfTouches(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if the two geometries spatially touch as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfTouches` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfTouches` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that spatially touch a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfTouches(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.17 ogcf:sfWithin

##### Format

ogcf:sfWithin(geom1 : geomLiteral, geom2 : geomLiteral) : xsd:boolean

##### Description

Returns `true` if `geom1` is spatially within `geom2` as defined by the OGC Simple Features specification (OGC 06-103r3). Returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `ogcf:sfWithin` spatial filter).

It is recommended to use a `LEADING(?var)` HINT0 hint when the query involves a restrictive `ogcf:sfWithin` spatial filter on `?var`.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds U.S. Congressional district polygons that are spatially within a constant polygon.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfWithin(?cgeom,
                 "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral)) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.18 ogcf:symDifference

##### Format

ogcf:symDifference(geom1 : geomLiteral, geom2 : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry object that is the topological symmetric difference (XOR operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons that are within a 100-kilometer buffer around a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfWithin(orageo:centroid(?cgeom),
                 ogcf:symDifference(
                    "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral,
                    "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^ogc:wktLiteral))) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

#### B.1.19 ogcf:union

##### Format

ogcf:union(geom1 : geomLiteral, geom2 : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry object that is the topological union (OR operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the OGC GeoSPARQL specification.

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is within the union of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (ogcf:sfWithin(orageo:centroid(?cgeom),
            ogcf:union(
              "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^ogc:wktLiteral,
              "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^ogc:wktLiteral))) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** GeoSPARQL Functions for Spatial Support

### B.2 Oracle-Specific Functions for Spatial Support

This section provides reference information about the Oracle-specific functions:

- orageo:aggrCentroid
- orageo:aggrConvexHull
- orageo:aggrMBR
- orageo:aggrUnion
- orageo:area
- orageo:buffer
- orageo:centroid
- orageo:convexHull
- orageo:difference
- orageo:distance
- orageo:getSRID
- orageo:intersection
- orageo:length
- orageo:mbr
- orageo:nearestNeighbor
- orageo:relate
- orageo:sdoDistJoin
- orageo:sdoJoin
- orageo:union
- orageo:withinDistance
- orageo:xor

**Parent topic:** SEM_MATCH Support for Spatial Queries

#### B.2.1 orageo:aggrCentroid

##### Format

orageo:aggrCentroid(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry literal that is the centroid of the group of specified geometry objects. (The centroid is also known as the "center of gravity.")

##### Parameters

geom
Geometry objects. Specified as a query variable.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_AGGR_CENTROID function in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-aggregate-functions.md).

##### Example

The following example finds the centroid of all the U.S. Congressional district polygons.

    SELECT centroid
    FROM table(sem_match(
    'select (orageo:aggrCentroid(?cgeom) as ?centroid)
     {?cdist orageo:hasExactGeometry ?cgeom } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.2 orageo:aggrConvexHull

##### Format

orageo:aggrConvexhull(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry literal that is the convex hull of the group of specified geometry objects.. (The convex hull is a simple convex polygon that, for this funciton, completely encloses the group of geometry objects, using as few straight-line sides as possible to create the smallest polygon that completely encloses the geometry objects.)

##### Parameters

geom
Geometry objects. Specified as a query variable.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_AGGR_CONVEXHULL function in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-aggregate-functions.md).

##### Example

The following example finds the convex hull of all the U.S. Congressional district polygons.

    SELECT chull
    FROM table(sem_match(
    'select (orageo:aggrConvexhull(?cgeom) as ?chull)
     {
       ?cdist orageo:hasExactGeometry ?cgeom } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.3 orageo:aggrMBR

##### Format

orageo:aggrMBR(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry literal that is the minimum bounding rectangle (MBR) of the group of specified geometry objects.

##### Parameters

geom
Geometry objects. Specified as a query variable.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_AGGR_MBR function in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-aggregate-functions.md).

##### Example

The following example finds the MBR of all the U.S. Congressional district polygons.

    SELECT mbr
    FROM table(sem_match(
    'select (orageo:aggrMBR(?cgeom) as ?mbr)
     {
       ?cdist orageo:hasExactGeometry ?cgeom } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.4 orageo:aggrUnion

##### Format

orageo:aggrUnion(geom : geomLiteral) : ogc:wktLiteral

##### Description

Returns a geometry literal that is the topological union of the group of specified geometry objects.

##### Parameters

geom
Geometry objects. Specified as a query variable.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_UNION function in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-aggregate-functions.md).

##### Example

The following example finds the union of all the U.S. Congressional district polygons.

    SELECT u
    FROM table(sem_match(
    'select (orageo:aggrUnion(?cgeom) as ?u)
     {
       ?cdist orageo:hasExactGeometry ?cgeom } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.5 orageo:area

##### Format

orageo:area(geom1 : geomLiteral, unit : Literal) : xsd:decimal

##### Description

Returns the area of `geom1` in terms of the specified unit of measure.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

unit
Unit of measurement: a quoted string with an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `"unit=SQ_KM"`). See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_AREA function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons with areas greater than 10,000 square kilometers.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:area(?cgeom, "unit=SQ_KM") > 10000) }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.6 orageo:buffer

##### Format

orageo:buffer(geom1 : geomLiteral, distance : xsd:decimal, unit : Literal) : geomLiteral

##### Description

Returns a buffer polygon at a specified distance around or inside a geometry.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

distance
Distance value. Distance value. If the value is positive, the buffer is generated around `geom1`; if the value is negative (valid only for polygons), the buffer is generated inside `geom1`.

unit
Unit of measurement: a quoted string with an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `"unit=KM"`). See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_BUFFER function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons that are completely inside a 100-kilometer buffer around a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (
         orageo:relate(?cgeom,
           orageo:buffer("POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
                         100, "unit=KM"),
          "mask=inside")) }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.7 orageo:centroid

##### Format

orageo:centroid(geom1 : geomLiteral) : geomLiteral

##### Description

Returns a point geometry that is the centroid of `geom1`. (The centroid is also known as the "center of gravity.")

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

For an input geometry consisting of multiple objects, the result is weighted by the area of each polygon in the geometry objects. If the geometry objects are a mixture of polygons and points, the points are not used in the calculation of the centroid. If the geometry objects are all points, the points have equal weight.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_CENTROID function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons with centroids within 200 kilometers of a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:withinDistance(orageo:centroid(?cgeom),
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "distance=200 unit=KM")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.8 orageo:convexHull

##### Format

orageo:convexHull(geom1 : geomLiteral) : geomLiteral

##### Description

Returns a polygon-type object that represents the convex hull of `geom1`. (The convex hull is a simple convex polygon that completely encloses the geometry object, using as few straight-line sides as possible to create the smallest polygon that completely encloses the geometry object.)

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

A convex hull is a convenient way to get an approximation of a complex geometry object.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_CONVEX_HULL function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose convex hull contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:convexHull(?cgeom),
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "mask=contains")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.9 orageo:difference

##### Format

orageo:difference(geom1 : geomLiteral, geom2 : geomLiteral) : geomLiteral

##### Description

Returns a geometry object that is the topological difference (MINUS operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_DIFFERENCE function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is inside the difference of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:centroid(?cgeom),
          orageo:difference(
                            "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^orageo:WKTLiteral,
                            "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^orageo:WKTLiteral),
          "mask=inside")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.10 orageo:distance

##### Format

orageo:distance(geom1 : geomLiteral, geom2 : geomLiteral, unit : Literal) : xsd:decimal

##### Description

Returns the distance between the nearest pair of points or segments of `geom1` and `geom2` in terms of the specified unit of measure.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

unit
Unit of measurement: a quoted string with an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `"unit=KM"`). See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

Use `orageo:withinDistance` instead of `orageo:distance` whenever possible, because orageo:withinDistance has a more efficient index-based implementation.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_DISTANCE function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the ten nearest U.S. Congressional districts to a specified point and orders them by distance from the point.

    SELECT name, cdist
    FROM table(sem_match(
    'SELECT ?name ?cdist
     WHERE
     { # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:nearestNeighbor(?cgeom,
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "sdo_num_res=10")) }
     ORDER BY ASC(orageo:distance(?cgeom,
                    "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
                    "unit=KM"))'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '))
    ORDER BY sem$rownum;

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.11 orageo:getSRID

##### Format

orageo:getSRID(geom : geomLiteral) : xsd:anyURI

##### Description

Returns the oracle spatial reference system (SRID) URI for `geom`.

##### Parameters

geom
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

##### Example

The following example finds spatial reference system URIs for U.S. Congressional district polygons.

    SELECT csrid
    FROM table(sem_match(
    'SELECT (orageo:getSRID(?cgeom) AS ?csrid)
     WHERE
     { ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/')
       )
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.12 orageo:intersection

##### Format

orageo:intersection(geom1 : geomLiteral, geom2 : geomLiteral) : geomLiteral

##### Description

Returns a geometry object that is the topological intersection (AND operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_INTERSECTION function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is inside the intersection of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:centroid(?cgeom),
          orageo:intersection(
                              "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^orageo:WKTLiteral,
                              "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^orageo:WKTLiteral),
          "mask=inside")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.13 orageo:length

##### Format

orageo:length(geom1 : geomLiteral, unit : Literal) : xsd:decimal

##### Description

Returns the length or perimeter of `geom1` in terms of the specified unit of measure.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

unit
Unit of measurement: a quoted string with an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `"unit=KM"`). See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_LENGTH function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons with lengths (perimeters) greater than 1000 kilometers.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:legnth(?cgeom, "unit=KM") > 1000) }'
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.14 orageo:mbr

##### Format

orageo:mbr(geom1 : geomLiteral) : geomLiteral

##### Description

Returns the minimum bounding rectangle of `geom1`, that is, the single rectangle that minimally encloses `geom1`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_MBR function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose minimum bounding rectangle contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:mbr(?cgeom),
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "mask=contains")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.15 orageo:nearestNeighbor

##### Format

orageo:nearestNeighbor(geom1:  geomLiteral, geom2 : geomLiteral, param : Literal) : xsd:boolean

##### Description

Returns `true` if `geom1` is a nearest neighbor of `geom2`, where the size of the nearest neighbors set is specified by `param`; returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

param
Determines the behavior of the operator. See the Usage Notes for the available keyword-value pairs.

##### Usage Notes

In the param parameter, the available keyword-value pairs are:

- `distance=``n` specifies the maximum allowable distance for the nearest neighbor search.

- `sdo_num_res=``n` specifies the size of the set for the nearest neighbor search.

- `unit=``unit` specifies the unit of measurement to use with `distance` value. If you do not specify a value, the unit of measurement associated with the data is used.

`geom1` must be a local variable (that is, a variable that appears in the basic graph pattern that contains the `orageo:nearestNeighbor` spatial filter).

It is a good idea to use a `'LEADING(?var)' HINT0` hint when your query involves a restrictive `orageo:relate` spatial filter on `?var.`

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_NN operator in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md).

##### Example

The following example finds the ten nearest U.S. Congressional districts to a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:nearestNeighbor(?cgeom,
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "sdo_num_res=10")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.16 orageo:relate

##### Format

orageo:relate(geom1:  geomLiteral, geom2 : geomLiteral, param : Literal) : xsd:boolean

##### Description

Returns `true` if `geom1` and `geom2` satisfy the topological spatial relation specified by the `param` parameter; returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

param
Specifies a list of mask relationships to check. See the list of keywords in the Usage Notes.

##### Usage Notes

The following `param` values (mask relationships) can be tested:

- ANYINTERACT: Returns TRUE if the objects are not disjoint.

- CONTAINS: Returns TRUE if the second object is entirely within the first object and the object boundaries do not touch; otherwise, returns FALSE.

- COVEREDBY: Returns TRUE if the first object is entirely within the second object and the object boundaries touch at one or more points; otherwise, returns FALSE.

- COVERS: Returns TRUE if the second object is entirely within the first object and the boundaries touch in one or more places; otherwise, returns FALSE.

- DISJOINT: Returns TRUE if the objects have no common boundary or interior points; otherwise, returns FALSE.

- EQUAL: Returns TRUE if the objects share every point of their boundaries and interior, including any holes in the objects; otherwise, returns FALSE.

- INSIDE: Returns TRUE if the first object is entirely within the second object and the object boundaries do not touch; otherwise, returns FALSE.

- ON: Returns ON if the boundary and interior of a line (the first object) is completely on the boundary of a polygon (the second object); otherwise, returns FALSE.

- OVERLAPBDYDISJOINT: Returns TRUE if the objects overlap, but their boundaries do not interact; otherwise, returns FALSE.

- OVERLAPBDYINTERSECT: Returns TRUE if the objects overlap, and their boundaries intersect in one or more places; otherwise, returns FALSE.

- TOUCH: Returns TRUE if the two objects share a common boundary point, but no interior points; otherwise, returns FALSE.

Values for `param` can be combined using the logical Boolean operator OR. For example, 'INSIDE + TOUCH' returns `TRUE` if the relationship between the geometries is INSIDE or TOUCH or both INSIDE and TOUCH; it returns `FALSE` if the relationship between the geometries is neither INSIDE nor TOUCH.

When invoking `orageo:relate` with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `orageo:relate` spatial filter).

It is a good idea to use a `'LEADING(?var)' HINT0` hint when your query involves a restrictive `orageo:relate` spatial filter on `?var.`

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_RELATE operator in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md).

##### Example

The following example finds the U.S. Congressional district that contains a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(?cgeom,
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          "mask=contains")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '
    ));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.17 orageo:sdoDistJoin

##### Format

orageo:sdoDistJoin(geom1 : geomLiteral, geom2 : geomLiteral, param : Literal) : xsd:boolean

##### Description

Performs a spatial join based on distance between two geometries. Returns `true` if the distance between `geom1` and `geom2` is within the given value specified in `param`; returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

param
Specifies a distance value and unit of measure to use for the distance-based spatial join. The distance value is added to the tolerance value of the associated spatial index. For example if `"distance=100 and unit=m"` is used with a tolerance value of 10 meters, then orageo:sdoDistJoin returns `true` if the distance between two geometries is no more than 110 meters.

##### Usage Notes

orageo:sdoDistJoin should be used when performing a distance-based spatial join between two large geometry collections. When performing a distance-based spatial join between one small geometry collection and one large geometry collection, invoking orageo:withinDistance with the small geometry collection as the first argument will usually give better performance than orageo:sdoDistJoin.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_JOIN operator in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md).

##### Example

The following example finds pairs of U.S. Congressional district polygons that are within 100 meters of each other.

    SELECT cdist1, cdist2
    FROM table(sem_match(
    '{ ?cdist1 orageo:hasExactGeometry ?cgeom1 .
       ?cdist2 orageo:hasExactGeometry ?cgeom2
       FILTER (orageo:sdoDistJoin(?cgeom1, ?cgeom2,
          "distance=100 unit=m")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '
    ));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.18 orageo:sdoJoin

##### Format

orageo:sdoJoin(geom1 : geomLiteral, geom2 : geomLiteral, param : Literal) : xsd:boolean

##### Description

Performs a spatial join based on one or more topological relationships. Returns `true` if `geom1` and `geom2` satisfy the spatial relationship specified by `param`; returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

param
Specifies a list of mask relationships to check. The topological relationship of interest.Valid values are 'mask=\<value\>' where \<value\> is one or more of the mask values that are valid for the SDO_RELATE operator (TOUCH, OVERLAPBDYDISJOINT, OVERLAPBDYINTERSECT, EQUAL, INSIDE, COVEREDBY, CONTAINS, COVERS, ANYINTERACT, ON). Multiple masks are combined with the logical Boolean operator OR (for example, `"mask=inside+touch"`).

##### Usage Notes

orageo:sdoJoin should be used when performing a spatial join between two large geometry collections. When performing a spatial join between one small geometry collection and one large geometry collection, invoking orageo:relate with the small geometry collection as the first argument will usually give better performance than orageo:sdoJoin.

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_JOIN operator in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md).

##### Example

The following example finds pairs of U.S. Congressional district polygons that have any spatial interaction.

    SELECT cdist1, cdist2
    FROM table(sem_match(
    '{ ?cdist1 orageo:hasExactGeometry ?cgeom1 .
       ?cdist2 orageo:hasExactGeometry ?cgeom2
       FILTER (orageo:sdoJoin(?cgeom1, ?cgeom2,
          "mask=anyinteract")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '
    ));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.19 orageo:union

##### Format

orageo:union(geom1 : geomLiteral, geom2 : geomLiteral) : geomLiteral

##### Description

Returns a geometry object that is the topological union (OR operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_UNION function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is inside the union of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:centroid(?cgeom),
          orageo:union("Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^orageo:WKTLiteral,
                       "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^orageo:WKTLiteral),
          "mask=inside")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.20 orageo:withinDistance

##### Format

orageo:withinDistance(geom1 : geomLiteral, geom2 : geomLiteral, distance : xsd:decimal, unit : Literal) : xsd:boolean

##### Description

Returns `true` if the distance between `geom1` and `geom2` is less than or equal to `distance` when measured in `unit`; returns `false` otherwise.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

distance
Distance value.

unit
Unit of measurement: a quoted string with an SDO_UNIT value from the MDSYS.SDO_DIST_UNITS table (for example, `"unit=KM"`). See the section about unit of measurement support in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md) for more information about unit of measurement specification.

##### Usage Notes

When invoking this function with a query variable and a constant geometry, always use the query variable as the first parameter and the constant geometry as the second parameter.

For best performance, `geom1` should be a local variable (that is, a variable that appears in the basic graph pattern that contains the `orageo:withinDistance` spatial filter).

It is a good idea to use a `'LEADING(?var)' HINT0` hint when your query involves a restrictive `orageo:withinDistance` spatial filter on `?var.`

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_WITHIN_DISTANCE operator in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-operators-reference.md).

##### Example

The following example finds the U.S. Congressional districts that are within 100 kilometers of a specified point.

    SELECT name, cdist
    FROM table(sem_match(
    '{ # HINT0={LEADING(?cgeom)}
       ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:withinDistance(?cgeom,
          "POINT(-71.46444 42.7575)"^^orageo:WKTLiteral,
          100, "KM")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support

#### B.2.21 orageo:xor

##### Format

orageo:xor(geom1 : geomLiteral, geom2 : geomLiteral) : geomLiteral

##### Description

Returns a geometry object that is the topological symmetric difference (XOR operation) of `geom1` and `geom2`.

##### Parameters

geom1
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

geom2
Geometry object. Specified as a query variable or a constant `geomLiteral` value.

##### Usage Notes

See [Spatial Support](rdf-semantic-graph-overview.md) for information about representing, indexing, and querying spatial data in RDF.

See also the SDO_GEOM.SDO_XOR function in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_GEOM-reference.md).

##### Example

The following example finds the U.S. Congressional district polygons whose centroid is inside the symmetric difference of two specified polygons.

    SELECT name, cdist
    FROM table(sem_match(
    '{ ?person usgovt:name ?name .
       ?person pol:hasRole ?role .
       ?role pol:forOffice ?office .
       ?office pol:represents ?cdist .
       ?cdist orageo:hasExactGeometry ?cgeom
       FILTER (orageo:relate(orageo:centroid(?cgeom),
          orageo:xor(
               "Polygon((-83.6 34.1, -83.2 34.1, -83.2 34.5, -83.6 34.5, -83.6 34.1))"^^orageo:WKTLiteral,
               "Polygon((-83.2 34.3, -83.0 34.3, -83.0 34.5, -83.2 34.5, -83.2 34.3))"^^orageo:WKTLiteral),
          "mask=inside")) } '
    ,sem_models('gov_all_vm'), null
    ,sem_aliases(
       sem_alias('usgovt','http://www.rdfabout.com/rdf/schema/usgovt/'),
       sem_alias('pol','http://www.rdfabout.com/rdf/schema/politico/'))
    ,null, null, ' ALLOW_DUP=T '));

**Parent topic:** Oracle-Specific Functions for Spatial Support
