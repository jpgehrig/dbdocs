## Glossary

### area

An extent or region of dimensional space.

**Parent topic:** Glossary

### attribute

Descriptive information characterizing a geographical feature such as a point, line, or area.

**Parent topic:** Glossary

### attribute data

Nondimensional data that provides additional descriptive information about multidimensional data, for example, a class or feature such as a bridge or a road.

**Parent topic:** Glossary

### batch geocoding

An operation that simultaneously geocodes many records from one table. See also geocoding.

**Parent topic:** Glossary

### boundary

1.  The lower or upper extent of the range of a dimension, expressed by a numeric value.

2.  The line representing the outline of a polygon.

**Parent topic:** Glossary

### Cartesian coordinate system

A coordinate system in which the location of a point in n-dimensional space is defined by distances from the point to the reference plane. Distances are measured parallel to the planes intersecting a given reference plane. See also coordinate system.

**Parent topic:** Glossary

### colocation

The presence of two or more spatial objects at the same location or at significantly close distances from each other.

**Parent topic:** Glossary

### contain

A geometric relationship where one object encompasses another and the inner object does not touch any boundaries of the outer. The outer object contains the inner object. See also inside.

**Parent topic:** Glossary

### convex hull

A simple convex polygon that completely encloses the associated geometry object.

**Parent topic:** Glossary

### coordinate

A set of values uniquely defining a point in an n-dimensional coordinate system.

**Parent topic:** Glossary

### coordinate reference system

Synonymous with coordinate system in Oracle Spatial and Graph documentation. The term coordinate reference system is used extensively by the European Petroleum Survey Group (EPSG).

**Parent topic:** Glossary

### coordinate system

A reference system for the unique definition for the location of a point in n-dimensional space. Also called a spatial reference system. See also Cartesian coordinate system, geodetic coordinates, projected coordinates, and local coordinates.

**Parent topic:** Glossary

### cover

A geometric relationship in which one object encompasses another and the inner object touches the boundary of the outer object in one or more places.

**Parent topic:** Glossary

### data dictionary

A repository of information about data. A data dictionary stores relational information on all objects in a database.

**Parent topic:** Glossary

### datum transformation

See transformation.

**Parent topic:** Glossary

### dimensional data

Data that has one or more dimensional components and is described by multiple values.

**Parent topic:** Glossary

### direction

The direction of an LRS geometric segment is indicated from the start point of the geometric segment to the end point. Measures of points on a geometric segment always increase along the direction of the geometric segment.

**Parent topic:** Glossary

### disjoint

A geometric relationship where two objects do not interact in any way. Two disjoint objects do not share any element or piece of their geometry.

**Parent topic:** Glossary

### element

A basic building block (point, line string, or polygon) of a geometry.

**Parent topic:** Glossary

### equal

A geometric relationship in which two objects are considered to represent the same geometric figure. The two objects must be composed of the same number of points; however, the ordering of the points defining geometries of the two objects may differ (clockwise or counterclockwise).

**Parent topic:** Glossary

### extent

A rectangle bounding a map, the size of which is determined by the minimum and maximum map coordinates.

**Parent topic:** Glossary

### feature

An object with a distinct set of characteristics in a spatial database.

**Parent topic:** Glossary

### geocoding

The process of converting tables of address data into standardized address, location, and possibly other data. See also batch geocoding.

**Parent topic:** Glossary

### geodetic coordinates

Angular coordinates (longitude and latitude) closely related to spherical polar coordinates and defined relative to a particular Earth geodetic datum. Also referred to as geographic coordinates.

**Parent topic:** Glossary

### geodetic datum

A means of representing the figure of the Earth, usually as an oblate ellipsoid of revolution, that approximates the surface of the Earth locally or globally, and is the reference for the system of geodetic coordinates.

**Parent topic:** Glossary

### geographic coordinates

See geodetic coordinates.

**Parent topic:** Glossary

### geographic information system (GIS)

A computerized database management system used for the capture, conversion, storage, retrieval, analysis, and display of spatial data.

**Parent topic:** Glossary

### geographically referenced data

See spatiotemporal data.

**Parent topic:** Glossary

### geometric segment (LRS segment)

An LRS element that contains start and end measures for its start and end points, and that can contain measures for other points on the segment.

**Parent topic:** Glossary

### geometry

The geometric representation of the shape of a spatial feature in some coordinate space. A geometry is an ordered sequence of vertices that are connected by straight line segments or circular arcs.

**Parent topic:** Glossary

### georeferenced data

See spatiotemporal data.

**Parent topic:** Glossary

### GIS

See geographic information system (GIS).

**Parent topic:** Glossary

### grid

A data structure composed of points located at the nodes of an imaginary grid. The spacing of the nodes is constant in both the horizontal and vertical directions.

**Parent topic:** Glossary

### hole

A subelement of a polygon that negates a section of its interior. For example, consider a polygon representing a map of buildable land with an inner polygon (a hole) representing where a lake is located.

**Parent topic:** Glossary

### homogeneous

Spatial data of one feature type such as points, lines, or regions.

**Parent topic:** Glossary

### hyperspatial data

In mathematics, any space having more than the three standard X, Y, and Z dimensions. Sometimes referred to as multidimensional data.

**Parent topic:** Glossary

### index

A database object that is used for fast and efficient access to stored information.

**Parent topic:** Glossary

### inside

A geometric relationship where one object is surrounded by a larger object and the inner object does not touch the boundary of the outer. The smaller object is inside the larger. See also contain.

**Parent topic:** Glossary

### key

A field in a database used to obtain access to stored information.

**Parent topic:** Glossary

### latitude

North/south position of a point on the Earth defined as the angle between the normal to the Earth's surface at that point and the plane of the equator.

**Parent topic:** Glossary

### layer

A collection of geometries having the same attribute set and stored in a geometry column.

**Parent topic:** Glossary

### line

A geometric object represented by a series of points, or inferred as existing between two coordinate points.

**Parent topic:** Glossary

### line string

One or more pairs of points that define a line segment. See also multiline string.

**Parent topic:** Glossary

### linear feature

Any spatial object that can be treated as a logical set of linear segments.

**Parent topic:** Glossary

### local coordinates

Cartesian coordinates in a non-Earth (non-georeferenced) coordinate system.

**Parent topic:** Glossary

### longitude

East/west position of a point on the Earth defined as the angle between the plane of a reference meridian and the plane of a meridian passing through an arbitrary point.

**Parent topic:** Glossary

### LRS point

A point with linear measure information along a geometric segment. See also geometric segment (LRS segment).

**Parent topic:** Glossary

### measure

The linear distance (in the LRS measure dimension) to a point measured from the start point (for increasing values) or end point (for decreasing values) of the geometric segment.

**Parent topic:** Glossary

### measure range

The measure values at the start and end of a geometric segment.

**Parent topic:** Glossary

### minimum bounding rectangle (MBR)

A single rectangle that minimally encloses a geometry or a collection of geometries.

**Parent topic:** Glossary

### multidimensional data

See hyperspatial data.

**Parent topic:** Glossary

### multiline string

A geometry object made up of nonconnected line string elements (for example, a street with a gap caused by a city park, such as Sixth Avenue in New York City with Central Park as the gap). See also line string.

**Parent topic:** Glossary

### multipolygon

A polygon collection geometry in which rings must be grouped by polygon, and the first ring of each polygon must be the exterior ring.

**Parent topic:** Glossary

### neighborhood influence

See spatial correlation.

**Parent topic:** Glossary

### offset

The perpendicular distance between a point along a geometric segment and the geometric segment. Offsets are positive if the points are on the left side along the segment direction and are negative if they are on the right side. Points are on a geometric segment if their offsets to the segment are zero.

**Parent topic:** Glossary

### oriented point

A special type of point geometry that includes coordinates representing the locations of the point and a virtual end point, to indicate an orientation vector that can be used for rotating a symbol at the point or extending a label from the point

**Parent topic:** Glossary

### polygon

A class of spatial objects having a nonzero area and perimeter, and representing a closed boundary region of uniform characteristics.

**Parent topic:** Glossary

### primary filter

The operation that permits fast selection of candidate records to pass along to the secondary filter. The primary filter compares geometry approximations to reduce computation complexity and is considered a lower-cost filter. Because the primary filter compares geometric approximations, it returns a superset of the exact result set. See also secondary filter and two-tier query model.

**Parent topic:** Glossary

### projected coordinates

Planar Cartesian coordinates that result from performing a mathematical mapping from a point on the Earth's surface to a plane. There are many such mathematical mappings, each used for a particular purpose.

**Parent topic:** Glossary

### projection

The point on the LRS geometric segment with the minimum distance to the specified point.

**Parent topic:** Glossary

### proximity

A measure of distance between objects.

**Parent topic:** Glossary

### query

A set of conditions or questions that form the basis for the retrieval of information from a database.

**Parent topic:** Glossary

### query window

Area within which the retrieval of spatial information and related attributes is performed.

**Parent topic:** Glossary

### RDBMS

See Relational Database Management System (RDBMS).

**Parent topic:** Glossary

### recursion

A process, function, or routine that executes continuously until a specified condition is met.

**Parent topic:** Glossary

### region

An extent or area of multidimensional space.

**Parent topic:** Glossary

### Relational Database Management System (RDBMS)

A computer program designed to store and retrieve shared data. In a relational system, data is stored in tables consisting of one or more rows, each containing the same set of columns. Oracle Database is an object-relational database management system. Other types of database systems are called hierarchical or network database systems.

**Parent topic:** Glossary

### resolution

The number of subdivision levels of data.

**Parent topic:** Glossary

### scale

The ratio of the distance on a map, photograph, or image to the corresponding image on the ground, all expressed in the same units.

**Parent topic:** Glossary

### secondary filter

The operation that applies exact computations to geometries that result from the primary filter. The secondary filter yields an accurate answer to a spatial query. The secondary filter operation is computationally expensive, but it is only applied to the primary filter results, not the entire data set. See also primary filter and two-tier query model.

**Parent topic:** Glossary

### shape points

Points that are specified when an LRS segment is constructed, and that are assigned measure information.

**Parent topic:** Glossary

### sort

The operation of arranging a set of items according to a key that determines the sequence and precedence of items.

**Parent topic:** Glossary

### spatial

A generic term used to reference the mathematical concept of n-dimensional data.

**Parent topic:** Glossary

### spatial binning

The process of discretizing the location values into a small number of groups associated with geographical areas. Also referred to as spatial discretization.

**Parent topic:** Glossary

### spatial correlation

The phenomenon of the location of a specific object in an area affecting some nonspatial attribute of the object. Also referred to as neighborhood influence.

**Parent topic:** Glossary

### spatial data

Data that is referenced by its location in n-dimensional space. The position of spatial data is described by multiple values. See also hyperspatial data.

**Parent topic:** Glossary

### spatial data model

A model of how objects are located on a spatial context.

**Parent topic:** Glossary

### spatial data structures

A class of data structures designed to store spatial information and facilitate its manipulation.

**Parent topic:** Glossary

### spatial database

A database containing information indexed by location.

**Parent topic:** Glossary

### spatial discretization

See spatial binning.

**Parent topic:** Glossary

### spatial join

A query in which each of the geometries in one layer is compared with each of the geometries in the other layer. Comparable to a spatial cross product.

**Parent topic:** Glossary

### spatial query

A query that includes criteria for which selected features must meet location conditions.

**Parent topic:** Glossary

### spatial reference system

See coordinate system.

**Parent topic:** Glossary

### spatiotemporal data

Data that contains time or location (or both) components as one of its dimensions, also referred to as geographically referenced data or georeferenced data.

**Parent topic:** Glossary

### SQL\*Loader

A utility to load formatted data into spatial tables.

**Parent topic:** Glossary

### tolerance

The distance that two points can be apart and still be considered the same (for example, to accommodate rounding errors). The tolerance value must be a positive number greater than zero. The significance of the value depends on whether or not the spatial data is associated with a geodetic coordinate system.

**Parent topic:** Glossary

### touch

A geometric relationship where two objects share a common point on their boundaries, but their interiors do not intersect.

**Parent topic:** Glossary

### transformation

The conversion of coordinates from one coordinate system to another coordinate system. If the coordinate system is georeferenced, transformation can involve datum transformation: the conversion of geodetic coordinates from one geodetic datum to another geodetic datum, usually involving changes in the shape, orientation, and center position of the reference ellipsoid.

**Parent topic:** Glossary

### two-tier query model

The query model used by Spatial and Graph to resolve spatial queries and spatial joins. Two distinct filtering operations (primary and secondary) are performed to resolve queries. The output of both operations yields the exact result set. See also primary filter and secondary filter.

**Parent topic:** Glossary
