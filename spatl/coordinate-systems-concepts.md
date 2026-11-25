## 6  Coordinate Systems (Spatial Reference Systems)

This chapter describes in detail the Oracle Spatial and Graph coordinate system support.

This support was introduced in [Coordinate System](spatial-concepts.md). You can store and manipulate SDO_GEOMETRY objects in a variety of coordinate systems.

For reference information about coordinate system transformation functions and procedures in the MDSYS.SDO_CS package, see [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md) .

- Terms and Concepts
  This topic explains important terms and concepts related to coordinate system support in Oracle Spatial and Graph.
- Geodetic Coordinate Support
  Effective with Oracle9i, Spatial and Graph provides a rational and complete treatment of geodetic coordinates.
- Local Coordinate Support
  Spatial and Graph provides a level of support for local coordinate systems.
- EPSG Model and Spatial and Graph
  The Oracle Spatial and Graph coordinate system support is based on, but is not always identical to, the European Petroleum Survey Group (EPSG) data model and dataset.
- Three-Dimensional Coordinate Reference System Support
  The Oracle Spatial and Graph support for three-dimensional coordinate reference systems complies with the EPSG model.
- TFM_PLAN Object Type
  The object type TFM_PLAN is used is by several SDO_CS package subprograms to specify a transformation plan.
- Coordinate Systems Data Structures
  The coordinate systems functions and procedures use information provided in the tables and views supplied with Oracle Spatial and Graph. The tables and views are part of the MDSYS schema; however, public synonyms are defined, so you do not need to specify MDSYS. before the table or view name.
- Legacy Tables and Views
  In releases of Spatial and Graph before 10.2, the coordinate systems functions and procedures used information provided in the following tables, some of which have new names or are now views instead of tables.
- Creating a User-Defined Coordinate Reference System
  If the coordinate systems supplied by Oracle are not sufficient for your needs, you can create user-defined coordinate reference systems.
- Notes and Restrictions with Coordinate Systems Support
  The following notes and restrictions apply to coordinate systems support in the current release of Oracle Spatial and Graph.
- U.S. National Grid Support
  The U.S. National Grid is a point coordinate representation using a single alphanumeric coordinate (for example, 18SUJ2348316806479498).
- Geohash Support
  A geohash is a standard String encoding of a longitude/latitude point.
- Google Maps Considerations
  Google Maps uses spherical math in its projections, as opposed to the ellipsoidal math used by Oracle Spatial and Graph. This difference can lead to inconsistencies in applications, such as when overlaying a map based on Google Maps with a map based on an Oracle Spatial and Graph ellipsoidal projection.
- Example of Coordinate System Transformation
  This topic presents a simplified example that uses coordinate system transformation functions and procedures.

**Parent topic:** [Conceptual and Usage Information](spatial-concepts-usage.md)

### 6.1 Terms and Concepts

This topic explains important terms and concepts related to coordinate system support in Oracle Spatial and Graph.

- Coordinate System (Spatial Reference System)
- Cartesian Coordinates
- Geodetic Coordinates (Geographic Coordinates)
- Projected Coordinates
- Local Coordinates
- Geodetic Datum
- Transformation

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.1.1 Coordinate System (Spatial Reference System)

A coordinate system (also called a spatial reference system) is a means of assigning coordinates to a location and establishing relationships between sets of such coordinates. It enables the interpretation of a set of coordinates as a representation of a position in a real world space.

The term coordinate reference system has the same meaning as coordinate system for Spatial and Graph, and the terms are used interchangeably. European Petroleum Survey Group (EPSG) specifications and documentation typically use the term coordinate reference system. (EPSG has its own meaning for the term coordinate system, as noted in SDO_COORD_SYS Table.)

**Parent topic:** Terms and Concepts

#### 6.1.2 Cartesian Coordinates

Cartesian coordinates are coordinates that measure the position of a point from a defined origin along axes that are perpendicular in the represented two-dimensional or three-dimensional space.

**Parent topic:** Terms and Concepts

#### 6.1.3 Geodetic Coordinates (Geographic Coordinates)

Geodetic coordinates (sometimes called geographic coordinates) are angular coordinates (longitude and latitude), closely related to spherical polar coordinates, and are defined relative to a particular Earth geodetic datum (described in Geodetic Datum). For more information about geodetic coordinate support, see Geodetic Coordinate Support.

**Parent topic:** Terms and Concepts

#### 6.1.4 Projected Coordinates

Projected coordinates are planar Cartesian coordinates that result from performing a mathematical mapping from a point on the Earth's surface to a plane. There are many such mathematical mappings, each used for a particular purpose.

**Parent topic:** Terms and Concepts

#### 6.1.5 Local Coordinates

Local coordinates are Cartesian coordinates in a non-Earth (non-georeferenced) coordinate system. Local Coordinate Support describes local coordinate support in Spatial and Graph.

**Parent topic:** Terms and Concepts

#### 6.1.6 Geodetic Datum

A geodetic datum (or datum) is a means of shifting and rotating an ellipsoid to represent the figure of the Earth, usually as an oblate spheroid, that approximates the surface of the Earth locally or globally, and is the reference for the system of geodetic coordinates.

Each geodetic coordinate system is based on a datum.

**Parent topic:** Terms and Concepts

#### 6.1.7 Transformation

Transformation is the conversion of coordinates from one coordinate system to another coordinate system.

If the coordinate system is georeferenced, transformation can involve datum transformation: the conversion of geodetic coordinates from one geodetic datum to another geodetic datum, usually involving changes in the shape, orientation, and center position of the reference ellipsoid.

**Parent topic:** Terms and Concepts

### 6.2 Geodetic Coordinate Support

Effective with Oracle9i, Spatial and Graph provides a rational and complete treatment of geodetic coordinates.

Before Oracle9i, spatial computations were based solely on flat (Cartesian) coordinates, regardless of the coordinate system specified for the layer of geometries. Consequently, computations for data in geodetic coordinate systems were inaccurate, because they always treated the coordinates as if they were on a flat surface, and they did not consider the curvature of the surface.

Now, ellipsoidal surface computations consider the curvatures of the Earth in the specified geodetic coordinate system and return correct, accurate results. In other words, spatial queries return the right answers all the time.

- Geodesy and Two-Dimensional Geometry
- Choosing a Geodetic or Projected Coordinate System
- Choosing Non-Ellipsoidal or Ellipsoidal Height
- Geodetic MBRs
- Distance: Spherical versus Ellipsoidal with Geodetic Data
- Other Considerations and Requirements with Geodetic Data

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.2.1 Geodesy and Two-Dimensional Geometry

A two-dimensional geometry is a surface geometry, but the important question is: What is the surface? A flat surface (plane) is accurately represented by Cartesian coordinates. However, Cartesian coordinates are not adequate for representing the surface of a solid. A commonly used surface for spatial geometry is the surface of the Earth, and the laws of geometry there are different than they are in a plane. For example, on the Earth's surface there are no parallel lines: lines are geodesics, and all geodesics intersect. Thus, closed curved surface problems cannot be done accurately with Cartesian geometry.

Spatial and Graph provides accurate results regardless of the coordinate system or the size of the area involved, without requiring that the data be projected to a flat surface. The results are accurate regardless of where on the Earth's surface the query is focused, even in "special" areas such as the poles. Thus, you can store coordinates in any datum and projections that you choose, and you can perform accurate queries regardless of the coordinate system.

**Parent topic:** Geodetic Coordinate Support

#### 6.2.2 Choosing a Geodetic or Projected Coordinate System

For applications that deal with the Earth's surface, the data can be represented using a geodetic coordinate system or a projected plane coordinate system. In deciding which approach to take with the data, consider any needs related to accuracy and performance:

- Accuracy

  For many spatial applications, the area is sufficiently small to allow adequate computations on Cartesian coordinates in a local projection. For example, the New Hampshire State Plane local projection provides adequate accuracy for most spatial applications that use data for that state.

  However, Cartesian computations on a plane projection will never give accurate results for a large area such as Canada or Scandinavia. For example, a query asking if Stockholm, Sweden and Helsinki, Finland are within a specified distance may return an incorrect result if the specified distance is close to the actual measured distance. Computations involving large areas or requiring very precise accuracy must account for the curvature of the Earth's surface.

- Performance

  Spherical computations use more computing resources than Cartesian computations. Some operations using geodetic coordinates may take longer to complete than the same operations using Cartesian coordinates.

It is important that you choose the correct type of coordinate system, because it affects the point at which anomalies related to floating point arithmetic are likely to appear.

**Parent topic:** Geodetic Coordinate Support

#### 6.2.3 Choosing Non-Ellipsoidal or Ellipsoidal Height

This section discusses guidelines for choosing the appropriate type of height for three-dimensional data: non-ellipsoidal or ellipsoidal. Although ellipsoidal height is widely used and is the default for many GPS applications, and although ellipsoidal computations incur less performance overhead in many cases, there are applications for which a non-ellipsoidal height may be preferable or even necessary.

Also, after any initial decision, you can change the reference height type, because transformations between different height datums are supported.

- Non-Ellipsoidal Height
- Ellipsoidal Height

**Parent topic:** Geodetic Coordinate Support

##### 6.2.3.1 Non-Ellipsoidal Height

Non-ellipsoidal height is measured from some point other than the reference ellipsoid. Some common non-ellipsoidal measurements of height are from ground level, mean sea level (MSL), or the reference geoid.

- Ground level: Measuring height from the ground level is conceptually the simplest approach, and it is common in very local or informal applications. For example, when modeling a single building or a cluster of buildings, ground level may be adequate.

  Moreover, if you ever need to integrate local ground height with a global height datum, you can achieve this with a transformation (EPSG method 9616) adding a local constant reference height. If you need to model local terrain undulations, you can achieve this with a transformation using an offset matrix (EPSG method 9635), just as you can between the geoid and the ellipsoid.

- Mean sea level (MSL): MSL is a common variation of sea level that provides conceptual simplicity, ignoring local variations and changes over time in sea level. It can also be extrapolated to areas covered by land.

  Height relative to MSL is useful for a variety of applications, such as those dealing with flooding risk, gravitational potential, and how thin the air is. MSL is commonly used for the heights of aircraft in flight.

- Geoid: The geoid, the equipotential surface closest to MSL, provides the most precise measurements of height in terms of gravitational pull, factoring in such things as climate and tectonic changes. The geoid can deviate from MSL by approximately 2 meters (plus or minus).

  If an application is affected more by purely gravitational effects than by actual local sea level, you may want to use the geoid as the reference rather than MSL. To perform transformations between MSL, geoid, or ellipsoid, you can use EPSG method 9635 and the appropriate time-stamped offset matrix.

Because most non-ellipsoidal height references are irregular and undulating surfaces, transformations between them are more complicated than with ellipsoidal heights. One approach is to use an offset grid file to define the transformation. This approach is implemented in EPSG method 9635. The grid file has to be acquired (often available publicly from government websites). Moreover, because most such non-ellipsoidal height datums (including the geoid, sea level, and local terrain) change over time, the timestamp of an offset matrix may matter, even if not by much. (Of course, the same principle applies to ellipsoids as well, since they are not static in the long term. After all, they are intended to approximate the changing geoid, MSL, or terrain.)

Regarding performance and memory usage with EPSG method 9635, at runtime the grid must be loaded before the transformation of a dataset. This load operation temporarily increases the footprint in main memory and incurs one-time loading overhead. If an entire dataset is transformed, the overhead can be relatively insignificant; however, if frequent transformations are performed on single geometries, the cumulative overhead can become significant.

**Parent topic:** Choosing Non-Ellipsoidal or Ellipsoidal Height

##### 6.2.3.2 Ellipsoidal Height

Ellipsoidal height is measured from a point on the reference ellipsoid. The ellipsoid is a convenient and relatively faithful approximation of the Earth. Although using an ellipsoid is more complex than using a sphere to represent the Earth, using an ellipsoid is, for most applications, simpler than using a geoid or local heights (although with some sacrifice in precision). Moreover, geoidal and sea-level heights are often not well suited for mathematical analysis, because the undulating and irregular shapes would make certain computations prohibitively complex and expensive.

GPS applications often assume ellipsoidal height as a reference and use it as the default. Because the ellipsoid is chosen to match the geoid (and similar sea level), ellipsoidal height tends not to deviate far from MSL height. For example, the geoid diverges from the NAD83 ellipsoid by only up to 50 meters. Other ellipsoids may be chosen to match a particular country even more closely.

Even if different parties use different ellipsoids, a WKT can conveniently describe such differences. A simple datum transformation can efficiently and accurately perform transformations between ellipsoids. Because no offset matrix is involved, no loading overhead is required. Thus, interoperability is simplified with ellipsoidal height, although future requirements or analysis might necessitate the use of MSL, a geoid, or other non-ellipsoidal height datums.

**Parent topic:** Choosing Non-Ellipsoidal or Ellipsoidal Height

#### 6.2.4 Geodetic MBRs

To create a query window for certain operations on geodetic data, use an MBR (minimum bounding rectangle) by specifying an SDO_ETYPE value of 1003 or 2003 (optimized rectangle) and an SDO_INTERPRETATION value of 3, as described in [Table 2-2](spatial-datatypes-metadata.md) in [SDO_ELEM_INFO](spatial-datatypes-metadata.md). A geodetic MBR can be used with the following operators: [SDO_FILTER](spatial-operators-reference.md), [SDO_RELATE](spatial-operators-reference.md) with the `ANYINTERACT` mask, [SDO_ANYINTERACT](spatial-operators-reference.md), and [SDO_WITHIN_DISTANCE](spatial-operators-reference.md).

Example 6-1 requests the names of all cola markets that are likely to interact spatially with a geodetic MBR.

Example 6-1 Using a Geodetic MBR

    SELECT c.name FROM cola_markets_cs c WHERE
       SDO_FILTER(c.shape,
           SDO_GEOMETRY(
               2003,
               8307,    -- SRID for WGS 84 longitude/latitude
               NULL,
               SDO_ELEM_INFO_ARRAY(1,1003,3),
               SDO_ORDINATE_ARRAY(6,5, 10,10))
           ) = 'TRUE';

Example 6-1 produces the following output (assuming the data as defined in Example of Coordinate System Transformation):

    NAME
    --------------------------------
    cola_c
    cola_b
    cola_d

The following considerations apply to the use of geodetic MBRs:

- Do not use a geodetic MBR with spatial objects stored in the database. Use it only to construct a query window.

- The lower-left Y coordinate (minY) must be less than the upper-right Y coordinate (maxY). If the lower-left X coordinate (minX) is greater than the upper-right X coordinate (maxX), the window is assumed to cross the date line meridian (that is, the meridian "opposite" the prime meridian, or both 180 and -180 longitude). For example, an MBR of (-10,10, -100, 20) with longitude/latitude data goes three-fourths of the way around the Earth (crossing the date line meridian), and goes from latitude lines 10 to 20.

- When Spatial and Graph uses the MBR internally for the query, the lines along the horizontal are treated as parallel lines to latitude and not as great circles. This might affect results for objects within a few meters of the edge of the MBR (especially objects in the middle latitudes in both hemispheres).

- When an optimized rectangle spans more than 119 degrees in longitude, it is internally divided into three rectangles; and as a result, these three rectangles share an edge that is the common boundary between them. If you validate the geometry of such an optimized rectangle, error code 13351 is returned because the internal rectangles have a shared edge. You can use such an optimized rectangle for queries with only the following: [SDO_ANYINTERACT](spatial-operators-reference.md) operator, [SDO_RELATE](spatial-operators-reference.md) operator with the ANYINTERACT mask, or [SDO_GEOM.RELATE](SDO_GEOM-reference.md) function with the ANYINTERACT mask. (Any other queries on such an optimized rectangle may return incorrect results.)

The following additional examples show special or unusual cases, to illustrate how a geodetic MBR is interpreted with longitude/latitude data:

- (10,0, -110,20) crosses the date line meridian and goes most of the way around the world, and goes from the equator to latitude 20.

- (10,-90, 40,90) is a band from the South Pole to the North Pole between longitudes 10 and 40.

- (10,-90, 40,50) is a band from the South Pole to latitude 50 between longitudes 10 and 40.

- (-180,-10, 180,5) is a band that wraps the equator from 10 degrees south to 5 degrees north.

- (-180,-90, 180,90) is the whole Earth.

- (-180,-90, 180,50) is the whole Earth below latitude 50.

- (-180,50, 180,90) is the whole Earth above latitude 50.

**Parent topic:** Geodetic Coordinate Support

#### 6.2.5 Distance: Spherical versus Ellipsoidal with Geodetic Data

When using a geodetic coordinate system, the distance between spatial objects can be computed as spherical or ellipsoidal.

The ellipsoidal distance is more accurate that the spherical distance, but it takes longer to compute. With previous releases (12.1 and earlier), with geodetic data, Spatial and Graph always used ellipsoidal distance for points and multipoints, but spherical distance for other geometry types.

Effective with Release 12.2, you have the option to specify ellipsoidal distance regardless of geometry type. The default distance measurement behavior is still as it was for Release 12.1. However, for spatial operators and functions that determine the distance between geometries, the “nearest neighbor” geometries, or whether geometries are within a given distance, you can specify whether ellipsoidal distance is needed, through the use of a keyword or parameter named `ellipsoidal`: `true` causes ellipsoidal distance to be returned regardless of the geometry type; `false` (the default) causes the pre-Release 12.2 behavior to be applied (ellipsoidal distance for points and multipoints, but spherical distance for other geometry types).

The default value of `false` prevents applications from returning different distance results after upgrading from Release 12.1 to 12.2, if that is a concern to you.

**Parent topic:** Geodetic Coordinate Support

#### 6.2.6 Other Considerations and Requirements with Geodetic Data

The following geometries are not permitted if a geodetic coordinate system is used or if any transformation is being performed (even if the transformation is from one projected coordinate system to another projected coordinate system):

- Circles

- Circular arcs

Geodetic coordinate system support is provided only for geometries that consist of points or geodesics (lines on the ellipsoid). If you have geometries containing circles or circular arcs in a projected coordinate system, you can densify them using the [SDO_GEOM.SDO_ARC_DENSIFY](SDO_GEOM-reference.md) function (documented in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md)) before transforming them to geodetic coordinates, and then perform spatial operations on the resulting geometries.

The following size limits apply with geodetic data:

- In general, no polygon element can have an area larger than or equal to one-half the surface of the Earth. Moreover, if the result of a union of two polygons is greater than one-half the surface of the Earth, the operation will not produce a correct result. For example, if A union B results in a polygon that is greater than one-half of the area of the Earth, the operations A difference B, A intersection B, and A XOR B are not supported, and only a relate operation with the ANYINTERACT mask is supported between those two polygons.

- In a line, the distance between two adjacent coordinates cannot be greater than or equal to one-half the perimeter (a great circle) of the Earth.

**Note:**

If the SPATIAL_VECTOR_ACCELERATION database system parameter value is `TRUE`, polygon elements that can have area larger than one-half the surface of the Earth are supported with some restrictions. Running [SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT](SDO_GEOM-reference.md) on such a geometry will result in the warning code 13367, indicating that the ring has the wrong orientation.

The warning in this case means that the ring is has an area larger than half the area of the Earth. Such geometries can be used in most operations except XOR and CONVEXHULL; however, such geometries are supported only if both the North and South poles are not contained in the polygons. That is, these large polygons may contain either the North Pole or the South Pole, but not both.

If you need to work with larger elements, first break these elements into multiple smaller elements and work with them. For example, you cannot create a geometry representing the entire ocean surface of the Earth; however, you can create multiple geometries, each representing part of the overall ocean surface. To work with a line string that is greater than or equal to one-half the perimeter of the Earth, you can add one or more intermediate points on the line so that all adjacent coordinates are less than one-half the perimeter of the Earth.

Tolerance is specified as meters for geodetic layers. If you use tolerance values that are typical for non-geodetic data, these values are interpreted as meters for geodetic data. For example, if you specify a tolerance value of 0.05 for geodetic data, this is interpreted as precise to 5 centimeters. If this value is more precise than your applications need, performance may be affected because of the internal computational steps taken to implement the specified precision. (For more information about tolerance, see [Tolerance](spatial-concepts.md).)

For geodetic layers, you must specify the dimensional extents in the index metadata as -180,180 for longitude and -90,90 for latitude. The following statement (from Example of Coordinate System Transformation) specifies these extents (with a 10-meter tolerance value in each dimension) for a geodetic data layer:

    INSERT INTO user_sdo_geom_metadata
        (TABLE_NAME,
         COLUMN_NAME,
         DIMINFO,
         SRID)
      VALUES (
      'cola_markets_cs',
      'shape',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),  -- 10 meters tolerance
        SDO_DIM_ELEMENT('Latitude', -90, 90, 10)  -- 10 meters tolerance
         ),
      8307   -- SRID for 'Longitude / Latitude (WGS 84)' coordinate system
    );

See Notes and Restrictions with Coordinate Systems Support for additional notes and restrictions relating to geodetic data.

**Parent topic:** Geodetic Coordinate Support

### 6.3 Local Coordinate Support

Spatial and Graph provides a level of support for local coordinate systems.

Local coordinate systems are often used in CAD systems, and they can also be used in local surveys where the relationship between the surveyed site and the rest of the world is not important.

Several local coordinate systems are predefined and included with Spatial and Graph in the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table). These supplied local coordinate systems, whose names start with Non-Earth, define non-Earth Cartesian coordinate systems based on different units of measurement (Meter, Millimeter, Inch, and so on).

In the current release, you cannot perform coordinate system transformation between local and Earth-based coordinate systems; and when transforming a geometry or layer of geometries between local coordinate systems, you can only to convert coordinates in a local coordinate system from one unit of measurement to another (for example, inches to millimeters). However, you can perform all other spatial operations (for example, using [SDO_RELATE](spatial-operators-reference.md), [SDO_WITHIN_DISTANCE](spatial-operators-reference.md), and other operators) with local coordinate systems.

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.4 EPSG Model and Spatial and Graph

The Oracle Spatial and Graph coordinate system support is based on, but is not always identical to, the European Petroleum Survey Group (EPSG) data model and dataset.

These are described in detail at [https://epsg.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/21&id=spatial_epsg), and the download for the EPSG geodetic parameter dataset includes a "Readme" that contains an entity-relationship (E-R) diagram. The approach taken by Oracle Spatial and Graph provides the benefits of standardization, expanded support, and flexibility:

- The EPSG model is a comprehensive and widely accepted standard for data representation, so users familiar with it can more easily understand Spatial and Graph storage and operations.

- Support is provided for more coordinate systems and their associated datums, ellipsoids, and projections. For example, some of the EPSG geographic and projected coordinate systems had no counterpart among coordinate systems supported for previous Spatial and Graph releases. Their addition results in an expanded set of supported coordinate systems.

- Data transformations are more flexible. Instead of there being only one possible Oracle-defined transformation path between a given source and target coordinate system, you can specify alternative paths to be used for a specific area of applicability (that is, use case) or as the systemwide default.

  The rest of this section describes this flexibility.

For data transformations (that is, transforming data from one coordinate system to another), you can now control which transformation rules are to be applied. In previous releases, and in the current release by default, Spatial and Graph performs transformations based only on the specified source and target coordinate systems, using predetermined intermediate transformation steps. The assumption behind that default approach is that there is a single correct or preferable transformation chain.

By default, then, Spatial and Graph applies certain transformation methods for each supported transformation between specific pairs of source and target coordinate systems. For example, there are over 500 supported transformations from specific coordinate systems to the WGS 84 (longitude/latitude) coordinate system, which has the EPSG SRID value of 4326. As one example, for a transformation from SRID 4605 to SRID 4326, Spatial and Graph can use the transformation method with the COORD_OP_ID value 1445, as indicated in the SDO_COORD_OPS table (described in SDO_COORD_OPS Table), which contains one row for each transformation operation between coordinate systems.

However, you can override the default transformation by specifying a different method (from the set of Oracle-supplied methods) for the transformation for any given source and target SRID combination. You can specify a transformation as the new systemwide default, or you can associate the transformation with a named use case that can be specified when transforming a layer of spatial geometries. (A use case is simply a name given to a usage scenario or area of applicability, such as Project XYZ or Mike's Favorite Transformations; there is no relationship between use cases and database users or schemas.)

To specify a transformation as either the systemwide default or associated with a use case, use the [SDO_CS.ADD_PREFERENCE_FOR_OP](SDO_CS-reference.md) procedure. To remove a previously specified preference, use the [SDO_CS.REVOKE_PREFERENCE_FOR_OP](SDO_CS-reference.md) procedure.

When it performs a coordinate system transformation, Spatial and Graph follows these general steps to determine the specific transformation to use:

1.  If a use case has been specified, the transformation associated with that use case is applied.

2.  If no use case has been specified and if a user-defined systemwide transformation has been created for the specified source and target coordinate system pair, that transformation is applied.

3.  If no use case has been specified and if no user-defined transformation exists for the specified source and target coordinate system pair, the behavior depends on whether or not EPSG rules have been created, such as by the [SDO_CS.CREATE_OBVIOUS_EPSG_RULES](SDO_CS-reference.md) procedure:

    - If the EPSG rules have been created and if an EPSG rule is defined for this transformation, the EPSG transformation is applied.

    - If the EPSG rules have not been created, or if they have been created but no EPSG rule is defined for this transformation, the Oracle Spatial and Graph default transformation is applied.

To return the version number of the EPSG dataset used by Spatial and Graph, use the [SDO_CS.GET_EPSG_DATA_VERSION](SDO_CS-reference.md) function.

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.5 Three-Dimensional Coordinate Reference System Support

The Oracle Spatial and Graph support for three-dimensional coordinate reference systems complies with the EPSG model.

**Note:**

Three-dimensional coordinate reference systems are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

The EPSG model (described in EPSG Model and Spatial and Graph) provides the following types of coordinate reference systems:

- Geographic 2D

- Projected 2D

- Geographic 3D, which consists of Geographic 2D plus ellipsoidal height, with longitude, latitude, and height based on the same ellipsoid and datum

- Compound, which consists of either Geographic 2D plus gravity-related height or Projected 2D plus gravity-related height

Thus, there are two categories of three-dimensional coordinate reference systems: those based on ellipsoidal height (geographic 3D, described in Geographic 3D Coordinate Reference Systems) and those based on gravity-related height (compound, described in Compound Coordinate Reference Systems).

Three-dimensional computations are more accurate than their two-dimensional equivalents, particularly when they are chained: For example, datum transformations internally always are performed in three dimensions, regardless of the dimensionality of the source and target CRS and geometries. When two-dimensional geometries are involved, one or more of the following can occur:

1.  When the input or output geometries and CRS are two-dimensional, the (unspecified) input height defaults to zero (above the ellipsoid, depending on the CRS) for any internal three-dimensional computations. This is a potential source of inaccuracy, unless the height was intended to be exactly zero. (Data can be two-dimensional because height values were originally either unavailable or not considered important; this is different from representing data in two dimensions because heights are known to be exactly zero.

2.  The transformation might then internally result in a non-zero height. Since the two-dimensional target CRS cannot accommodate the height value, the height value must be truncated, resulting in further inaccuracy.

3.  If further transformations are chained, the repeated truncation of height values can result in increasing inaccuracies. Note that an inaccurate input height can affect not only the output height of a transformation, but also the longitude and latitude.

However, if the source and target CRS are three-dimensional, there is no repeated truncation of heights. Consequently, accuracy is increased, particularly for transformation chains.

For an introduction to support in Spatial and Graph for three-dimensional geometries, see [Three-Dimensional Spatial Objects](spatial-concepts.md).

- Geographic 3D Coordinate Reference Systems
- Compound Coordinate Reference Systems
- Three-Dimensional Transformations
- Cross-Dimensionality Transformations
- 3D Equivalent for WGS 84?

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.5.1 Geographic 3D Coordinate Reference Systems

A geographic three-dimensional coordinate reference system is based on longitude and latitude, plus ellipsoidal height. The ellipsoidal height is the height relative to a reference ellipsoid, which is an approximation of the real Earth. All three dimensions of the CRS are based on the same ellipsoid.

Using ellipsoidal heights enables Spatial and Graph to perform internal operations with great mathematical regularity and efficiency. Compound coordinate reference systems, on the other hand, require more complex transformations, often based on offset matrixes. Some of these matrixes have to be downloaded and configured. Furthermore, they might have a significant footprint, on disk and in main memory.

The supported geographic 3D coordinate reference systems are listed in the SDO_CRS_GEOGRAPHIC3D view.

**Parent topic:** Three-Dimensional Coordinate Reference System Support

#### 6.5.2 Compound Coordinate Reference Systems

A compound three-dimensional coordinate reference system is based on a geographic or projected two-dimensional system, plus gravity-related height. Gravity-related height is the height as influenced by the Earth's gravitational force, where the base height (zero) is often an equipotential surface, and might be defined as above or below "sea level."

Gravity-related height is a more complex representation than ellipsoidal height, because of gravitational irregularities such as the following:

- Orthometric height

  Orthometric height is also referred to as the height above the geoid. The geoid is an equipotential surface that most closely (but not exactly) matches mean sea level. An equipotential surface is a surface on which each point is at the same gravitational potential level. Such a surface tends to undulate slightly, because the Earth has regions of varying density. There are multiple equipotential surfaces, and these might not be parallel to each other due to the irregular density of the Earth.

- Height relative to mean sea level, to sea level at a specific location, or to a vertical network warped to fit multiple tidal stations (for example, NGVD 29)

  Sea level is close to, but not identical to, the geoid. The sea level at a given location is often defined based on the "average sea level" at a specific port.

The supported compound coordinate reference systems are listed in the SDO_CRS_COMPOUND view, described in SDO_CRS_COMPOUND View.

You can create a customized compound coordinate reference system, which combines a horizontal CRS with a vertical CRS. (The horizontal CRS contains two dimensions, such as X and Y or longitude and latitude, and the vertical CRS contains the third dimension, such as Z or height or altitude.) Creating a Compound CRS explains how to create a compound CRS.

**Parent topic:** Three-Dimensional Coordinate Reference System Support

#### 6.5.3 Three-Dimensional Transformations

Spatial and Graph supports three-dimensional coordinate transformations for SDO_GEOMETRY objects directly, and indirectly for point clouds and TINs. (For example, a point cloud must be transformed to a table with an SDO_GEOMETRY column.) The supported transformations include the following:

- Three-dimensional datum transformations

- Transformations between ellipsoidal and gravity-related height

For three-dimensional datum transformations, the datum transformation between the two ellipsoids is essentially the same as for two-dimensional coordinate reference systems, except that the third dimension is considered instead of ignored. Because height values are not ignored, the accuracy of the results increases, especially for transformation chains.

For transformations between ellipsoidal and gravity-related height, computations are complicated by the fact that equipotential and other gravity-related surfaces tend to undulate, compared to any ellipsoid and to each other. Transformations might be based on higher-degree polynomial functions or bilinear interpolation. In either case, a significant parameter matrix is required to define the transformation.

For transforming between gravity-related and ellipsoidal height, the process usually involves a transformation, based on an offset matrix, between geoidal and ellipsoidal height. Depending on the source or target definition of the offset matrix, a common datum transformation might have to be appended or prefixed.

Example 6-2 Three-Dimensional Datum Transformation

Example 6-2 shows a three-dimensional datum transformation.

    set numwidth 9

    CREATE TABLE source_geoms (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      GEOMETRY SDO_GEOMETRY);

    INSERT INTO source_geoms VALUES(
      1,
      'reference geom',
      SDO_GEOMETRY(
      3001,
      4985,
      SDO_POINT_TYPE(
         4.0,
        55.0,
        1.0),
      NULL,
      NULL));

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'source_geoms',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',   -1000,1000, 10)),
      4985);

    commit;

    --------------------------------------------------------------------------------

    CALL SDO_CS.TRANSFORM_LAYER(
      'source_geoms',
      'GEOMETRY',
      'GEO_CS_4979',
      4979);

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'GEO_CS_4979',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',   -1000,1000, 10)),
      4979);

    set lines 210;

    --------------------------------------------------------------------------------

    CALL SDO_CS.TRANSFORM_LAYER(
      'GEO_CS_4979',
      'GEOMETRY',
      'source_geoms2',
      4985);

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'source_geoms2',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',   -1000,1000, 10)),
      4985);

    --------------------------------------------------------------------------------

    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'GEO_CS_4979';
    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'SOURCE_GEOMS';
    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'SOURCE_GEOMS2';

    drop table GEO_CS_4979;
    drop table source_geoms;
    drop table source_geoms2;

As a result of the transformation in Example 6-2, (4, 55, 1) is transformed to (4.0001539, 55.0000249, 4.218).

Example 6-3 Transformation Between Geoidal And Ellipsoidal Height

Example 6-3 configures a transformation between geoidal and ellipsoidal height, using a Hawaii offset grid. Note that without the initial creation of a rule (using the [SDO_CS.CREATE_PREF_CONCATENATED_OP](SDO_CS-reference.md) procedure), the grid would not be used.

    -- Create Sample operation:
    insert into mdsys.sdo_coord_ops (
      COORD_OP_ID,
      COORD_OP_NAME,
      COORD_OP_TYPE,
      SOURCE_SRID,
      TARGET_SRID,
      COORD_TFM_VERSION,
      COORD_OP_VARIANT,
      COORD_OP_METHOD_ID,
      UOM_ID_SOURCE_OFFSETS,
      UOM_ID_TARGET_OFFSETS,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      SHOW_OPERATION,
      IS_LEGACY,
      LEGACY_CODE,
      REVERSE_OP,
      IS_IMPLEMENTED_FORWARD,
      IS_IMPLEMENTED_REVERSE)
    values (
      1000000005,
      'Test Bi-linear Interpolation',
      'CONVERSION',
      null,
      null,
      null,
      null,
      9635,
      null,
      null,
      'Oracle',
      'Oracle',
      1,
      'FALSE',
      null,
      1,
      1,
      1);

    --Create sample parameters, pointing to the offset file
    --(in this case reusing values from an existing operation):
    insert into mdsys.sdo_coord_op_param_vals (
        coord_op_id,
        COORD_OP_METHOD_ID,
        PARAMETER_ID,
        PARAMETER_VALUE,
        PARAM_VALUE_FILE_REF,
        PARAM_VALUE_FILE,
        PARAM_VALUE_XML,
        UOM_ID) (
      select
        1000000005,
        9635,
        8666,
        PARAMETER_VALUE,
        PARAM_VALUE_FILE_REF,
        PARAM_VALUE_FILE,
        PARAM_VALUE_XML,
        UOM_ID
      from
        mdsys.sdo_coord_op_param_vals
      where
        coord_op_id = 999998 and
        parameter_id = 8666);

    --Create a rule to use this operation between SRIDs 7406 and 4359:
    call sdo_cs.create_pref_concatenated_op(
        300,
        'CONCATENATED OPERATION',
        TFM_PLAN(SDO_TFM_CHAIN(7406, 1000000005, 4359)),
        NULL);


    -- Now, actually perform the transformation:
    set numformat 999999.99999999

    -- Create the source table
    CREATE TABLE source_geoms (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      GEOMETRY SDO_GEOMETRY);

    INSERT INTO source_geoms VALUES(
      1,
      'reference geom',
      SDO_GEOMETRY(
      3001,
      7406,
      SDO_POINT_TYPE(
        -161,
          18,
         0),
      NULL,
      NULL));

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'source_geoms',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',    -100, 100, 10)),
      7406);

    commit;

    SELECT GEOMETRY "Source" FROM source_geoms;

    --------------------------------------------------------------------------------

    --Perform the transformation:
    CALL SDO_CS.TRANSFORM_LAYER(
      'source_geoms',
      'GEOMETRY',
      'GEO_CS_4359',
      4359);

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'GEO_CS_4359',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',    -100, 100, 10)),
      4359);

    set lines 210;

    SELECT GEOMETRY "Target" FROM GEO_CS_4359;

    --------------------------------------------------------------------------------

    --Transform back:
    CALL SDO_CS.TRANSFORM_LAYER(
      'GEO_CS_4359',
      'GEOMETRY',
      'source_geoms2',
      7406);

    INSERT INTO USER_SDO_GEOM_METADATA VALUES (
      'source_geoms2',
      'GEOMETRY',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),
        SDO_DIM_ELEMENT('Latitude',   -90,  90, 10),
        SDO_DIM_ELEMENT('Height',    -100, 100, 10)),
      7406);

    SELECT GEOMETRY "Source2" FROM source_geoms2;

    --------------------------------------------------------------------------------

    --Clean up (regarding the transformation):
    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'GEO_CS_4359';
    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'SOURCE_GEOMS';
    DELETE FROM USER_SDO_GEOM_METADATA WHERE table_name = 'SOURCE_GEOMS2';

    drop table GEO_CS_4359;
    drop table source_geoms;
    drop table source_geoms2;


    --Clean up (regarding the rule):
    CALL sdo_cs.delete_op(300);

    delete from mdsys.sdo_coord_op_param_vals where coord_op_id = 1000000005;

    delete from mdsys.sdo_coord_ops where coord_op_id = 1000000005;

    COMMIT;

With the configuration in Example 6-3:

- Without the rule, (-161.00000000, 18.00000000, .00000000) is transformed to (-161.00127699, 18.00043360, 62.03196364), based simply on a datum transformation.

- With the rule, (-161.00000000, 18.00000000, .00000000) is transformed to (-161.00000000, 18.00000000, 6.33070000).

**Parent topic:** Three-Dimensional Coordinate Reference System Support

#### 6.5.4 Cross-Dimensionality Transformations

You cannot directly perform a cross-dimensionality transformation (for example, from a two-dimensional geometry to a three-dimensional geometry) using the [SDO_CS.TRANSFORM](SDO_CS-reference.md) function or the [SDO_CS.TRANSFORM_LAYER](SDO_CS-reference.md) procedure. However, you can use the [SDO_CS.MAKE_3D](SDO_CS-reference.md) function to convert a two-dimensional geometry to a three-dimensional geometry, or the [SDO_CS.MAKE_2D](SDO_CS-reference.md) function to convert a three-dimensional geometry to a two-dimensional geometry; and you can use the resulting geometry to perform a transformation into a geometry with the desired number of dimensions.

For example, transforming a two-dimensional geometry into a three-dimensional geometry involves using the [SDO_CS.MAKE_3D](SDO_CS-reference.md) function. This function does not itself perform any coordinate transformation, but simply adds a height value and sets the target SRID. You must choose an appropriate target SRID, which should be the three-dimensional equivalent of the source SRID. For example, three-dimensional WGS 84 (4327) is the equivalent of two-dimensional WGS 84 (4326). If necessary, modify height values of vertices in the returned geometry.

There are many options for how to use the [SDO_CS.MAKE_3D](SDO_CS-reference.md) function, but the simplest is the following:

1.  Transform from the two-dimensional source SRID to two-dimensional WGS 84 (4326).

2.  Call [SDO_CS.MAKE_3D](SDO_CS-reference.md) to convert the geometry to three-dimensional WGS 84 (4327)

3.  Transform from three-dimensional WGS 84 (4327) to the three-dimensional target SRID.

Example 6-4 transforms a two-dimensional point from SRID 27700 to two-dimensional SRID 4326, converts the result of the transformation to a three-dimensional point with SRID 4327, and transforms the converted point to three-dimensional SRID 4327.

Example 6-4 Cross-Dimensionality Transformation

    SELECT
      SDO_CS.TRANSFORM(
        SDO_CS.MAKE_3D(
          SDO_CS.TRANSFORM(
            SDO_GEOMETRY(
              2001,
              27700,
              SDO_POINT_TYPE(577274.984, 69740.4923, NULL),
              NULL,
              NULL),
            4326),
          height => 0,
          target_srid => 4327),
        4327) "27700 > 4326 > 4327 > 4327"
    FROM DUAL;

    27700 > 4326 > 4327 > 4327(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INF
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(3001, 4327, SDO_POINT_TYPE(.498364058, 50.5006366, 0), NULL, NULL)

**Parent topic:** Three-Dimensional Coordinate Reference System Support

#### 6.5.5 3D Equivalent for WGS 84?

There are two possible answers to the question What is 3D equivalent for the WGS 84 coordinate system? (that is, 2D Oracle SRID 8308 or EPSG SRID 4326):

- 4979 (in many or most cases), or

- It depends on what you mean by height (for example, above ground level, above or below sea level, or something else).

There are many different height datums. Height can be relative to:

- The ellipsoid, which requires the use of a coordinate system of type GEOGRAPHIC3d, for which SRID values 4327, 43229, and 4979 are predefined in Oracle Spatial and Graph.

- A non-ellipsoidal height datum, which requires the use of a coordinate system of type COMPOUND, for which a custom SRID must usually be defined. The non-ellipsoidal height may be specified in relation to the geoid, to some local or mean sea level (or a network of local sea levels), or to some other definition of height (such as above ground surface).

To define a compound coordinate system (see Compound Coordinate Reference Systems) based on the two dimensions of the WGS 84 coordinate system, you must first select a predefined or custom vertical coordinate reference system (see Creating a Vertical CRS). To find the available vertical coordinate reference systems, enter the following statement:

    SELECT srid, COORD_REF_SYS_NAME from sdo_coord_ref_sys
      WHERE COORD_REF_SYS_KIND = 'VERTICAL' order by srid;

          SRID COORD_REF_SYS_NAME
    ---------- ---------------------------------------------------------------------
          3855 EGM2008 geoid height
          3886 Fao 1979 height
          4440 NZVD2009 height
          4458 Dunedin-Bluff 1960 height
          5600 NGPF height
          5601 IGN 1966 height
          5602 Moorea SAU 1981 height
          . . .
          5795 Guadeloupe 1951 height
          5796 Lagos 1955 height
          5797 AIOC95 height
          5798 EGM84 geoid height
          5799 DVR90 height

    123 rows selected.

After selecting a vertical coordinate reference system, create the compound SRID by entering a statement in the following form:

    INSERT INTO sdo_coord_ref_system (
      SRID,
      COORD_REF_SYS_NAME,
      COORD_REF_SYS_KIND,
      COORD_SYS_ID,
      DATUM_ID,
      GEOG_CRS_DATUM_ID,
      SOURCE_GEOG_SRID,
      PROJECTION_CONV_ID,
      CMPD_HORIZ_SRID,
      CMPD_VERT_SRID,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE,
      LEGACY_WKTEXT,
      LEGACY_CS_BOUNDS,
      IS_VALID,
      SUPPORTS_SDO_GEOMETRY)
    values (
      custom-SRID,
      'custom-name',
      'COMPOUND',
      NULL,
      NULL,
      6326,
      NULL,
      NULL,
      4326,
      vertical-SRID,
      'custom-information-source',
      'custom-data-source',
      'FALSE',
      NULL,
      NULL,
      NULL,
      'TRUE',
      'TRUE');

You can check the definition, based on the generated WKT, by entering a statement in the following form:

    SELECT wktext3d FROM cs_srs WHERE srid = custom-SRID;

    WKTEXT3D
    ------------------------------------------------------------------------------
    COMPD_CS[
      "NTF (Paris) + NGF IGN69",
      GEOGCS["NTF (Paris)",
        DATUM["Nouvelle Triangulation Francaise (Paris)",
          SPHEROID[
            "Clarke 1880 (IGN)",
            6378249.2,
            293.4660212936293951,
            AUTHORITY["EPSG", "7011"]],
          TOWGS84[-168.0, -60.0, 320.0, 0.0, 0.0, 0.0, 0.0],
          AUTHORITY["EPSG", "6807"]],
        PRIMEM["Paris", 2.337229, AUTHORITY["EPSG","8903"]],
        UNIT["grad", 0.015707963267949, AUTHORITY["EPSG", "9105"]],
        AXIS["Lat", NORTH],
        AXIS["Long", EAST],
        AUTHORITY["EPSG", "4807"]],
      VERT_CS["NGF IGN69",
        VERT_DATUM["Nivellement general de la France - IGN69", 2005,
          AUTHORITY["EPSG", "5119"]],
        UNIT["metre", 1.0, AUTHORITY["EPSG", "9001"]],
        AXIS["H", UP],
        AUTHORITY["EPSG", "5720"]],
      AUTHORITY["EPSG","7400"]]

When transforming between different height datums, you might use a VERTCON matrix. For example, between the WGS 84 ellipsoid and geoid, there is an offset matrix that allows height transformation. For more information, see the following:

- Example 6-3 in Three-Dimensional Transformations

- Creating a Transformation Operation

- Using British Grid Transformation OSTN02/OSGM02 (EPSG Method 9633)

**Parent topic:** Three-Dimensional Coordinate Reference System Support

### 6.6 TFM_PLAN Object Type

The object type TFM_PLAN is used is by several SDO_CS package subprograms to specify a transformation plan.

For example, to create a concatenated operation that consists of two operations specified by a parameter of type TFM_PLAN, use the [SDO_CS.CREATE_CONCATENATED_OP](SDO_CS-reference.md) procedure.

Oracle Spatial and Graph defines the object type TFM_PLAN as:

    CREATE TYPE tfm_plan AS OBJECT (
     THE_PLAN SDO_TFM_CHAIN);

The SDO_TFM_CHAIN type is defined as `VARRAY(1048576) OF NUMBER`.

Within the SDO_TFM_CHAIN array:

- The first element specifies the SRID of the source coordinate system.

- Each pair of elements after the first element specifies an operation ID and the SRID of a target coordinate system.

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.7 Coordinate Systems Data Structures

The coordinate systems functions and procedures use information provided in the tables and views supplied with Oracle Spatial and Graph. The tables and views are part of the MDSYS schema; however, public synonyms are defined, so you do not need to specify MDSYS. before the table or view name.

The definitions and data in these tables and views are based on the EPSG data model and dataset, as explained in EPSG Model and Spatial and Graph.

The coordinate system tables fit into several general categories:

- Coordinate system general information: SDO_COORD_SYS, SDO_COORD_REF_SYS

- Elements or aspects of a coordinate system definition: SDO_DATUMS, SDO_ELLIPSOIDS, SDO_PRIME_MERIDIANS

- Datum transformation support: SDO_COORD_OPS, SDO_COORD_OP_METHODS, SDO_COORD_OP_PARAM_USE, SDO_COORD_OP_PARAM_VALS, SDO_COORD_OP_PARAMS, SDO_COORD_OP_PATHS, SDO_PREFERRED_OPS_SYSTEM, SDO_PREFERRED_OPS_USER

- Others related to coordinate system definition: SDO_COORD_AXES, SDO_COORD_AXIS_NAMES, SDO_UNITS_OF_MEASURE

Several views are provided that are identical to or subsets of coordinate system tables:

- SDO_COORD_REF_SYSTEM, which contains the same columns as the SDO_COORD_REF_SYS table. Use the SDO_COORD_REF_SYSTEM view instead of the COORD_REF_SYS table for any insert, update, or delete operations.

- Subsets of SDO_DATUMS, selected according to the value in the DATUM_TYPE column: SDO_DATUM_ENGINEERING, SDO_DATUM_GEODETIC, SDO_DATUM_VERTICAL.

- Subsets of SDO_COORD_REF_SYS, selected according to the value in the COORD_REF_SYS_KIND column: SDO_CRS_COMPOUND, SDO_CRS_ENGINEERING, SDO_CRS_GEOCENTRIC, SDO_CRS_GEOGRAPHIC2D, SDO_CRS_GEOGRAPHIC3D, SDO_CRS_PROJECTED, SDO_CRS_VERTICAL.

Most of the rest of this section explains these tables and views, in alphabetical order. (Many column descriptions are adapted or taken from EPSG descriptions.) Relationships Among Coordinate System Tables and Views describes relationships among the tables and views, and it lists EPSG table names and their corresponding Oracle Spatial and Graph names. Finding Information About EPSG-Based Coordinate Systems describes how to find information about EPSG-based coordinate systems, and it provides several examples.

In addition to the tables and views in this section, Spatial and Graph provides several legacy tables whose definitions and data match those of certain Spatial and Graph system tables used in previous releases. Legacy Tables and Views describes the legacy tables.

**Note:**

You should not modify or delete any Oracle-supplied information in any of the tables or views that are used for coordinate system support.

If you want to create a user-defined coordinate system, see Creating a User-Defined Coordinate Reference System.

- SDO_COORD_AXES Table
- SDO_COORD_AXIS_NAMES Table
- SDO_COORD_OP_METHODS Table
- SDO_COORD_OP_PARAM_USE Table
- SDO_COORD_OP_PARAM_VALS Table
- SDO_COORD_OP_PARAMS Table
- SDO_COORD_OP_PATHS Table
- SDO_COORD_OPS Table
- SDO_COORD_REF_SYS Table
- SDO_COORD_REF_SYSTEM View
- SDO_COORD_SYS Table
- SDO_CRS_COMPOUND View
- SDO_CRS_ENGINEERING View
- SDO_CRS_GEOCENTRIC View
- SDO_CRS_GEOGRAPHIC2D View
- SDO_CRS_GEOGRAPHIC3D View
- SDO_CRS_PROJECTED View
- SDO_CRS_VERTICAL View
- SDO_DATUM_ENGINEERING View
- SDO_DATUM_GEODETIC View
- SDO_DATUM_VERTICAL View
- SDO_DATUMS Table
- SDO_ELLIPSOIDS Table
- SDO_PREFERRED_OPS_SYSTEM Table
- SDO_PREFERRED_OPS_USER Table
- SDO_PRIME_MERIDIANS Table
- SDO_UNITS_OF_MEASURE Table
- Relationships Among Coordinate System Tables and Views
- Finding Information About EPSG-Based Coordinate Systems

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.7.1 SDO_COORD_AXES Table

The SDO_COORD_AXES table contains one row for each coordinate system axis definition. This table contains the columns shown in Table 6-1.

Table 6-1 SDO_COORD_AXES Table

| Column Name             | Data Type    | Description                                                                                                                                                                                                         |
|:------------------------|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COORD_SYS_ID            | NUMBER(10)   | ID number of the coordinate system to which this axis applies.                                                                                                                                                      |
| COORD_AXIS_NAME_ID      | NUMBER(10)   | ID number of a coordinate system axis name. Matches a value in the COORD_AXIS_NAME_ID column of the SDO_COORD_AXIS_NAMES table (described in SDO_COORD_AXIS_NAMES Table). Example: `9901` (for `Geodetic latitude`) |
| COORD_AXIS_ORIENTATION  | VARCHAR2(24) | The direction of orientation for the coordinate system axis. Example: `east`                                                                                                                                        |
| COORD_AXIS_ABBREVIATION | VARCHAR2(24) | The abbreviation for the coordinate system axis orientation. Example: `E`                                                                                                                                           |
| UOM_ID                  | NUMBER(10)   | ID number of the unit of measurement associated with the axis. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table).                                    |
| ORDER                   | NUMBER(5)    | Position of this axis within the coordinate system (1, 2, or 3).                                                                                                                                                    |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.2 SDO_COORD_AXIS_NAMES Table

The SDO_COORD_AXIS_NAMES table contains one row for each axis that can be used in a coordinate system definition. This table contains the columns shown in Table 6-2.

Table 6-2 SDO_COORD_AXIS_NAMES Table

| Column Name        | Data Type    | Description                                                |
|:-------------------|:-------------|:-----------------------------------------------------------|
| COORD_AXIS_NAME_ID | NUMBER(10)   | ID number of the coordinate axis name. Example: `9926`     |
| COORD_AXIS_NAME    | VARCHAR2(80) | Name of the coordinate axis. Example: `Spherical latitude` |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.3 SDO_COORD_OP_METHODS Table

The SDO_COORD_OP_METHODS table contains one row for each coordinate systems transformation method. This table contains the columns shown in Table 6-3.

Table 6-3 SDO_COORD_OP_METHODS Table

| Column Name            | Data Type     | Description                                                                                                                                                                                                                                                                        |
|:-----------------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COORD_OP_METHOD_ID     | NUMBER(10)    | ID number of the coordinate system transformation method. Example: `9613`                                                                                                                                                                                                          |
| COORD_OP_METHOD_NAME   | VARCHAR2(50)  | Name of the method. Example: `NADCON`                                                                                                                                                                                                                                              |
| LEGACY_NAME            | VARCHAR2(50)  | Name for this transformation method in the legacy WKT strings. This name might differ syntactically from the name used by EPSG.                                                                                                                                                    |
| REVERSE_OP             | NUMBER(1)     | Contains `1` if reversal of the transformation (from the current target coordinate system to the source coordinate system) can be achieved by reversing the sign of each parameter value; contains `0` if a separate operation must be defined for reversal of the transformation. |
| INFORMATION_SOURCE     | VARCHAR2(254) | Origin of this information. Example: `US Coast and geodetic Survey - http://www.ngs.noaa.gov`                                                                                                                                                                                      |
| DATA_SOURCE            | VARCHAR2(40)  | Organization providing the data for this record. Example: `EPSG`                                                                                                                                                                                                                   |
| IS_IMPLEMENTED_FORWARD | NUMBER(1)     | Contains `1` if the forward operation is implemented; contains `0` if the forward operation is not implemented.                                                                                                                                                                    |
| IS_IMPLEMENTED_REVERSE | NUMBER(1)     | Contains `1` if the reverse operation is implemented; contains `0` if the reverse operation is not implemented.                                                                                                                                                                    |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.4 SDO_COORD_OP_PARAM_USE Table

The SDO_COORD_OP_PARAM_USE table contains one row for each combination of transformation method and transformation operation parameter that is available for use. This table contains the columns shown in Table 6-4.

Table 6-4 SDO_COORD_OP_PARAM_USE Table

| Column Name         | Data Type    | Description                                                                                                                                                                                                                                                         |
|:--------------------|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COORD_OP_METHOD_ID  | NUMBER(10)   | ID number of the coordinate system transformation method. Matches a value in the COORD_OP_METHOD_ID column of the COORD_OP_METHODS table (described in SDO_COORD_OP_METHODS Table).                                                                                 |
| PARAMETER_ID        | NUMBER(10)   | ID number of the parameter for transformation operations. Matches a value in the PARAMETER_ID column of the SDO_COORD_OP_PARAMS table (described in SDO_COORD_OP_PARAMS Table).                                                                                     |
| LEGACY_PARAM_NAME   | VARCHAR2(80) | Open GeoSpatial Consortium (OGC) name for the parameter.                                                                                                                                                                                                            |
| SORT_ORDER          | NUMBER(5)    | A number indicating the position of this parameter in the sequence of parameters for this method. Example: `2` for the second parameter                                                                                                                             |
| PARAM_SIGN_REVERSAL | VARCHAR2(3)  | `Yes` if reversal of the transformation (from the current target coordinate system to the source coordinate system) can be achieved by reversing the sign of each parameter value; `No` if a separate operation must be defined for reversal of the transformation. |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.5 SDO_COORD_OP_PARAM_VALS Table

The SDO_COORD_OP_PARAM_VALS table contains information about parameter values for each coordinate system transformation method. This table contains the columns shown in Table 6-5.

Table 6-5 SDO_COORD_OP_PARAM_VALS Table

| Column Name          | Data Type     | Description                                                                                                                                                                                                        |
|:---------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COORD_OP_ID          | NUMBER(10)    | ID number of the coordinate transformation operation. Matches a value in the COORD_OP_ID column of the SDO_COORD_OPS table (described in SDO_COORD_OPS Table).                                                     |
| COORD_OP_METHOD_ID   | NUMBER(10)    | Coordinate operation method ID. Must match a COORD_OP_METHOD_ID value in the SDO_COORD_OP_METHODS table (see SDO_COORD_OP_METHODS Table).                                                                          |
| PARAMETER_ID         | NUMBER(10)    | ID number of the parameter for transformation operations. Matches a value in the PARAMETER_ID column of the SDO_COORD_OP_PARAMS table (described in SDO_COORD_OP_PARAMS Table).                                    |
| PARAMETER_VALUE      | FLOAT(49)     | Value of the parameter for this operation.                                                                                                                                                                         |
| PARAM_VALUE_FILE_REF | VARCHAR2(254) | Name of the file (as specified in the original EPSG database) containing the value data, if a single value for the parameter is not sufficient.                                                                    |
| PARAM_VALUE_FILE     | CLOB          | The ASCII content of the file specified in the PARAM_VALUE_FILE_REF column. Used only for grid file parameters (for NADCON, NTv2, and height transformations "Geographic3D to Geographic2D+GravityRelatedHeight"). |
| PARAM_VALUE_XML      | XMLTYPE       | An XML representation of the content of the file specified in the PARAM_VALUE_FILE_REF column. (Optional, and currently only used for documentation.)                                                              |
| UOM_ID               | NUMBER(10)    | ID number of the unit of measurement associated with the operation. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table).                              |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.6 SDO_COORD_OP_PARAMS Table

The SDO_COORD_OP_PARAMS table contains one row for each available parameter for transformation operations. This table contains the columns shown in Table 6-6.

Table 6-6 SDO_COORD_OP_PARAMS Table

| Column Name        | Data Type     | Description                                                         |
|:-------------------|:--------------|:--------------------------------------------------------------------|
| PARAMETER_ID       | NUMBER(10)    | ID number of the parameter. Example: `8608`                         |
| PARAMETER_NAME     | VARCHAR2(80)  | Name of the operation. Example: `X-axis rotation`                   |
| INFORMATION_SOURCE | VARCHAR2(254) | Origin of this information. Example: `EPSG guidance note number 7.` |
| DATA_SOURCE        | VARCHAR2(40)  | Organization providing the data for this record. Example: `EPSG`    |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.7 SDO_COORD_OP_PATHS Table

The SDO_COORD_OP_PATHS table contains one row for each atomic step in a concatenated operation. This table contains the columns shown in Table 6-7.

Table 6-7 SDO_COORD_OP_PATHS Table

| Column Name         | Data Type  | Description                                                                                                                                                                                              |
|:--------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CONCAT_OPERATION_ID | NUMBER(10) | ID number of the concatenation operation. Must match a COORD_OP_ID value in the SDO_COORD_OPS table (described in SDO_COORD_OPS Table) for which the COORD_OP_TYPE value is `CONCATENATION`.             |
| SINGLE_OPERATION_ID | NUMBER(10) | ID number of the single coordinate operation for this step (atomic operation) in a concatenated operation. Must match a COORD_OP_ID value in the SDO_COORD_OPS table (described in SDO_COORD_OPS Table). |
| SINGLE_OP_SOURCE_ID | NUMBER(10) | ID number of source coordinate reference system for the single coordinate operation for this step. Must match an SRID value in the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table).       |
| SINGLE_OP_TARGET_ID | NUMBER(10) | ID number of target coordinate reference system for the single coordinate operation for this step. Must match an SRID value in the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table).       |
| OP_PATH_STEP        | NUMBER(5)  | Sequence number of this step (atomic operation) within this concatenated operation.                                                                                                                      |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.8 SDO_COORD_OPS Table

The SDO_COORD_OPS table contains one row for each transformation operation between coordinate systems. This table contains the columns shown in Table 6-8.

Table 6-8 SDO_COORD_OPS Table

| Column Name            | Data Type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-----------------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COORD_OP_ID            | NUMBER(10)    | ID number of the coordinate transformation operation. Example: `101`                                                                                                                                                                                                                                                                                                                                                                                    |
| COORD_OP_NAME          | VARCHAR2(80)  | Name of the operation. Example: `ED50 to WGS 84 (14)`                                                                                                                                                                                                                                                                                                                                                                                                   |
| COORD_OP_TYPE          | VARCHAR2(24)  | Type of operation. One of the following: `CONCATENATED OPERATION`, `CONVERSION`, or `TRANSFORMATION`                                                                                                                                                                                                                                                                                                                                                    |
| SOURCE_SRID            | NUMBER(10)    | SRID of the coordinate system from which to perform the transformation. Example: `4230`                                                                                                                                                                                                                                                                                                                                                                 |
| TARGET_SRID            | NUMBER(10)    | SRID of the coordinate system into which to perform the transformation. Example: `4326`                                                                                                                                                                                                                                                                                                                                                                 |
| COORD_TFM_VERSION      | VARCHAR2(24)  | Name assigned by EPSG to the coordinate transformation. Example: `5Nat-NSea90`                                                                                                                                                                                                                                                                                                                                                                          |
| COORD_OP_VARIANT       | NUMBER(5)     | A variant of the more generic method specified in COORD_OP_METHOD_ID. Example: `14`                                                                                                                                                                                                                                                                                                                                                                     |
| COORD_OP_METHOD_ID     | NUMBER(10)    | Coordinate operation method ID. Must match a COORD_OP_METHOD_ID value in the SDO_COORD_OP_METHODS table (see SDO_COORD_OP_METHODS Table). Several operations can use a method. Example: `9617`                                                                                                                                                                                                                                                          |
| UOM_ID_SOURCE_OFFSETS  | NUMBER(10)    | ID number of the unit of measurement for offsets in the source coordinate system. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table).                                                                                                                                                                                                                                                     |
| UOM_ID_TARGET_OFFSETS  | NUMBER(10)    | ID number of the unit of measurement for offsets in the target coordinate system. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table).                                                                                                                                                                                                                                                     |
| INFORMATION_SOURCE     | VARCHAR2(254) | Origin of this information. Example: `Institut de Geomatica; Barcelona`                                                                                                                                                                                                                                                                                                                                                                                 |
| DATA_SOURCE            | VARCHAR2(40)  | Organization providing the data for this record. Example: `EPSG`                                                                                                                                                                                                                                                                                                                                                                                        |
| SHOW_OPERATION         | NUMBER(3)     | (Not currently used.)                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| IS_LEGACY              | VARCHAR2(5)   | TRUE if the operation was included in Oracle Spatial before release 10.2; FALSE if the operation was new in Oracle Spatial release 10.2.                                                                                                                                                                                                                                                                                                                |
| LEGACY_CODE            | NUMBER(10)    | For any EPSG coordinate transformation operation that has a semantically identical legacy (in Oracle Spatial before release 10.2) counterpart, the COORD_OP_ID value of the legacy coordinate transformation operation.                                                                                                                                                                                                                                 |
| REVERSE_OP             | NUMBER(1)     | Contains `1` if reversal of the transformation (from the current target coordinate system to the source coordinate system) is defined as achievable by reversing the sign of each parameter value; contains `0` if a separate operation must be defined for reversal of the transformation. If REVERSE_OP contains `1`, the operations that are actually implemented are indicated by the values for IS_IMPLEMENTED_FORWARD and IS_IMPLEMENTED_REVERSE. |
| IS_IMPLEMENTED_FORWARD | NUMBER(1)     | Contains `1` if the forward operation is implemented; contains `0` if the forward operation is not implemented.                                                                                                                                                                                                                                                                                                                                         |
| IS_IMPLEMENTED_REVERSE | NUMBER(1)     | Contains `1` if the reverse operation is implemented; contains `0` if the reverse operation is not implemented.                                                                                                                                                                                                                                                                                                                                         |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.9 SDO_COORD_REF_SYS Table

The SDO_COORD_REF_SYS table contains one row for each coordinate reference system. This table contains the columns shown in Table 6-9. (The SDO_COORD_REF_SYS table is roughly patterned after the EPSG Coordinate Reference System table.)

**Note:**

If you need to perform an insert, update, or delete operation, you must perform it on the SDO_COORD_REF_SYSTEM view, which contains the same columns as the SDO_COORD_REF_SYS table. The SDO_COORD_REF_SYSTEM view is described in SDO_COORD_REF_SYSTEM View.

Table 6-9 SDO_COORD_REF_SYS Table

| Column Name           | Data Type      | Description                                                                                                                                                                                                                                                                                                                                                       |
|:----------------------|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID                  | NUMBER(10)     | ID number of the coordinate reference system. Example: `8307`                                                                                                                                                                                                                                                                                                     |
| COORD_REF_SYS_NAME    | VARCHAR2(80)   | Name of the coordinate reference system. Example: `Longitude / Latitude (WGS 84)`                                                                                                                                                                                                                                                                                 |
| COORD_REF_SYS_KIND    | VARCHAR2(24)   | Category for the coordinate system. Example: `GEOGRAPHIC2D`                                                                                                                                                                                                                                                                                                       |
| COORD_SYS_ID          | NUMBER(10)     | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table).                                                                                                                                                                                                |
| DATUM_ID              | NUMBER(10)     | ID number of the datum used for the coordinate reference system. Null for a projected coordinate system. For a geodetic coordinate system, must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table). Example: `10115`                                                                                                                           |
| GEOG_CRS_DATUM_ID     | NUMBER(10)     | ID number of the datum used for the coordinate reference system. For a projected coordinate system, must match the DATUM_ID value (in the SDO_DATUMS table, described in SDO_DATUMS Table) of the geodetic coordinate system on which the projected coordinate system is based. For a geodetic coordinate system, must match the DATUM_ID value. Example: `10115` |
| SOURCE_GEOG_SRID      | NUMBER(10)     | For a projected coordinate reference system, the ID number for the associated geodetic coordinate system.                                                                                                                                                                                                                                                         |
| PROJECTION_CONV_ID    | NUMBER(10)     | For a projected coordinate reference system, the COORD_OP_ID value of the conversion operation used to convert the projected coordinated system to and from the source geographic coordinate system.                                                                                                                                                              |
| CMPD_HORIZ_SRID       | NUMBER(10)     | (EPSG-assigned value; not used by Oracle Spatial and Graph. The EPSG description is: "For compound CRS only, the code of the horizontal component of the Compound CRS.")                                                                                                                                                                                          |
| CMPD_VERT_SRID        | NUMBER(10)     | (EPSG-assigned value; not used by Oracle Spatial and Graph. The EPSG description is: "For compound CRS only, the code of the vertical component of the Compound CRS.")                                                                                                                                                                                            |
| INFORMATION_SOURCE    | VARCHAR2(254)  | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                                                                                                                                                                                                                  |
| DATA_SOURCE           | VARCHAR2(40)   | Organization that supplied the data for this record (if not Oracle).                                                                                                                                                                                                                                                                                              |
| IS_LEGACY             | VARCHAR2(5)    | `TRUE` if the coordinate system definition was included in Oracle Spatial before release 10.2; `FALSE` if the coordinate system definition was new in Oracle Spatial release 10.2.                                                                                                                                                                                |
| LEGACY_CODE           | NUMBER(10)     | For any EPSG coordinate reference system that has a semantically identical legacy (in Oracle Spatial before release 10.2) counterpart, the SRID value of the legacy coordinate system.                                                                                                                                                                            |
| LEGACY_WKTEXT         | VARCHAR2(2046) | If IS_LEGACY is `TRUE`, contains the well-known text description of the coordinate system. Example: `GEOGCS [ "Longitude / Latitude (WGS 84)", DATUM ["WGS 84", SPHEROID ["WGS 84", 6378137, 298.257223563]], PRIMEM [ "Greenwich", 0.000000 ], UNIT ["Decimal Degree", 0.01745329251994330]]`                                                                    |
| LEGACY_CS_BOUNDS      | SDO_GEOMETRY   | For a legacy coordinate system, the dimensional boundary (if any).                                                                                                                                                                                                                                                                                                |
| IS_VALID              | VARCHAR2(5)    | `TRUE` if the EPSG record for the coordinate reference system is completely defined; `FALSE` if the EPSG record for the coordinate reference system is not completely defined.                                                                                                                                                                                    |
| SUPPORTS_SDO_GEOMETRY | VARCHAR2(5)    | `TRUE` if the COORD_REF_SYS_KIND column contains `ENGINEERING`, `GEOGRAPHIC2D`, or `PROJECTED CRS`; `FALSE` if the COORD_REF_SYS_KIND column contains any other value.                                                                                                                                                                                            |

See also the information about the following views that are defined based on the value of the COORD_REF_SYS_KIND column:

- SDO_CRS_COMPOUND (SDO_CRS_COMPOUND View)

- SDO_CRS_ENGINEERING (SDO_CRS_ENGINEERING View)

- SDO_CRS_GEOCENTRIC (SDO_CRS_GEOCENTRIC View)

- SDO_CRS_GEOGRAPHIC2D (SDO_CRS_GEOGRAPHIC2D View)

- SDO_CRS_GEOGRAPHIC3D (SDO_CRS_GEOGRAPHIC3D View)

- SDO_CRS_PROJECTED (SDO_CRS_PROJECTED View)

- SDO_CRS_VERTICAL (SDO_CRS_VERTICAL View)

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.10 SDO_COORD_REF_SYSTEM View

The SDO_COORD_REF_SYSTEM view contains the same columns as the SDO_COORD_REF_SYS table, which is described in SDO_COORD_REF_SYS Table. However, the SDO_COORD_REF_SYSTEM view has a trigger defined on it, so that any insert, update, or delete operations performed on the view cause all relevant Spatial and Graph system tables to have the appropriate operations performed on them.

Therefore, if you need to perform an insert, update, or delete operation, you must perform it on the SDO_COORD_REF_SYSTEM view, not the SDO_COORD_REF_SYS table.

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.11 SDO_COORD_SYS Table

The SDO_COORD_SYS table contains rows with information about coordinate systems. This table contains the columns shown in Table 6-10. (The SDO_COORD_SYS table is roughly patterned after the EPSG Coordinate System table, where a coordinate system is described as "a pair of reusable axes.")

Table 6-10 SDO_COORD_SYS Table

| Column Name        | Data Type     | Description                                                                                                                     |
|:-------------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------|
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system. Example: `6405`                                                                             |
| COORD_SYS_NAME     | VARCHAR2(254) | Name of the coordinate system. Example: `Ellipsoidal 2D CS. Axes: latitude, longitude. Orientations: north, east. UoM: dec deg` |
| COORD_SYS_TYPE     | VARCHAR2(24)  | Type of coordinate system. Example: `ellipsoidal`                                                                               |
| DIMENSION          | NUMBER(5)     | Number of dimensions represented by the coordinate system.                                                                      |
| INFORMATION_SOURCE | VARCHAR2(254) | Origin of this information.                                                                                                     |
| DATA_SOURCE        | VARCHAR2(50)  | Organization providing the data for this record.                                                                                |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.12 SDO_CRS_COMPOUND View

The SDO_CRS_COMPOUND view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `COMPOUND`. (For an explanation of compound coordinate reference systems, see Compound Coordinate Reference Systems.) This view contains the columns shown in Table 6-11.

Table 6-11 SDO_CRS_COMPOUND View

| Column Name        | Data Type     | Description                                                                                                                                                              |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                            |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                                 |
| CMPD_HORIZ_SRID    | NUMBER(10)    | (EPSG-assigned value; not used by Oracle Spatial and Graph. The EPSG description is: "For compound CRS only, the code of the horizontal component of the Compound CRS.") |
| CMPD_VERT_SRID     | NUMBER(10)    | (EPSG-assigned value; not used by Oracle Spatial and Graph. The EPSG description is: "For compound CRS only, the code of the vertical component of the Compound CRS.")   |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                         |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                                     |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.13 SDO_CRS_ENGINEERING View

The SDO_CRS_ENGINEERING view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `ENGINEERING`. This view contains the columns shown in Table 6-12.

Table 6-12 SDO_CRS_ENGINEERING View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| DATUM_ID           | NUMBER(10)    | ID number of the datum used for the coordinate reference system. Must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table).                       |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.14 SDO_CRS_GEOCENTRIC View

The SDO_CRS_GEOCENTRIC view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `GEOCENTRIC`. This view contains the columns shown in Table 6-13.

Table 6-13 SDO_CRS_GEOCENTRIC View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| DATUM_ID           | NUMBER(10)    | ID number of the datum used for the coordinate reference system. Must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table).                       |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.15 SDO_CRS_GEOGRAPHIC2D View

The SDO_CRS_GEOGRAPHIC2D view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `GEOGRAPHIC2D`. This view contains the columns shown in Table 6-14.

Table 6-14 SDO_CRS_GEOGRAPHIC2D View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| DATUM_ID           | NUMBER(10)    | ID number of the datum used for the coordinate reference system. Must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table).                       |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.16 SDO_CRS_GEOGRAPHIC3D View

The SDO_CRS_GEOGRAPHIC3D view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `GEOGRAPHIC3D`. (For an explanation of geographic 3D coordinate reference systems, see Geographic 3D Coordinate Reference Systems.)

**Note:**

SDO_CRS_GEOGRAPHIC3D view is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

This view contains the columns shown in Table 6-15.

Table 6-15 SDO_CRS_GEOGRAPHIC3D View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| DATUM_ID           | NUMBER(10)    | ID number of the datum used for the coordinate reference system. Must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table).                       |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.17 SDO_CRS_PROJECTED View

The SDO_CRS_PROJECTED view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `PROJECTED`. This view contains the columns shown in Table 6-16.

Table 6-16 SDO_CRS_PROJECTED View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| SOURCE_GEOG_SRID   | NUMBER(10)    | ID number for the associated geodetic coordinate system.                                                                                                           |
| PROJECTION_CONV_ID | NUMBER(10)    | COORD_OP_ID value of the conversion operation used to convert the projected coordinated system to and from the source geographic coordinate system.                |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.18 SDO_CRS_VERTICAL View

The SDO_CRS_VERTICAL view contains selected information from the SDO_COORD_REF_SYS table (described in SDO_COORD_REF_SYS Table) where the COORD_REF_SYS_KIND column value is `VERTICAL`. This view contains the columns shown in Table 6-17.

Table 6-17 SDO_CRS_VERTICAL View

| Column Name        | Data Type     | Description                                                                                                                                                        |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SRID               | NUMBER(10)    | ID number of the coordinate reference system.                                                                                                                      |
| COORD_REF_SYS_NAME | VARCHAR2(80)  | Name of the coordinate reference system.                                                                                                                           |
| COORD_SYS_ID       | NUMBER(10)    | ID number of the coordinate system used for the coordinate reference system. Must match a COORD_SYS_ID value in the SDO_COORD_SYS table (see SDO_COORD_SYS Table). |
| DATUM_ID           | NUMBER(10)    | ID number of the datum used for the coordinate reference system. Must match a DATUM_ID value in the SDO_DATUMS table (see SDO_DATUMS Table).                       |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition for the coordinate system (`Oracle` for all rows supplied by Oracle).                                                                   |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                               |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.19 SDO_DATUM_ENGINEERING View

The SDO_DATUM_ENGINEERING view contains selected information from the SDO_DATUMS table (described in SDO_DATUMS Table) where the DATUM_TYPE column value is `ENGINEERING`. This view contains the columns shown in Table 6-18.

Table 6-18 SDO_DATUM_ENGINEERING View

| Column Name        | Data Type     | Description                                                                                                                                                                          |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATUM_ID           | NUMBER(10)    | ID number of the datum.                                                                                                                                                              |
| DATUM_NAME         | VARCHAR2(80)  | Name of the datum.                                                                                                                                                                   |
| ELLIPSOID_ID       | NUMBER(10)    | ID number of the ellipsoid used in the datum definition. Must match an ELLIPSOID_ID value in the SDO_ELLIPSOIDS table (see SDO_ELLIPSOIDS Table). Example: `8045`                    |
| PRIME_MERIDIAN_ID  | NUMBER(10)    | ID number of the prime meridian used in the datum definition. Must match a PRIME_MERIDIAN_ID value in the SDO_PRIME_MERIDIANS table (see SDO_PRIME_MERIDIANS Table). Example: `8950` |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition of the datum. Example: `Ordnance Survey of Great Britain.`                                                                                                |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                                                 |
| SHIFT_X            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the x-axis.                                                                         |
| SHIFT_Y            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the y-axis.                                                                         |
| SHIFT_Z            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the z-axis.                                                                         |
| ROTATE_X           | NUMBER        | Number of arc-seconds of rotation about the x-axis.                                                                                                                                  |
| ROTATE_Y           | NUMBER        | Number of arc-seconds of rotation about the y-axis.                                                                                                                                  |
| ROTATE_Z           | NUMBER        | Number of arc-seconds of rotation about the z-axis.                                                                                                                                  |
| SCALE_ADJUST       | NUMBER        | A value to be used in adjusting the X, Y, and Z values after any shifting and rotation, according to the formula: 1.0 + (SCALE_ADJUST \* 10<sup>-6</sup>)                            |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.20 SDO_DATUM_GEODETIC View

The SDO_DATUM_GEODETIC view contains selected information from the SDO_DATUMS table (described in SDO_DATUMS Table) where the DATUM_TYPE column value is `GEODETIC`. This view contains the columns shown in Table 6-19.

Table 6-19 SDO_DATUM_GEODETIC View

| Column Name        | Data Type     | Description                                                                                                                                                                          |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATUM_ID           | NUMBER(10)    | ID number of the datum.                                                                                                                                                              |
| DATUM_NAME         | VARCHAR2(80)  | Name of the datum.                                                                                                                                                                   |
| ELLIPSOID_ID       | NUMBER(10)    | ID number of the ellipsoid used in the datum definition. Must match an ELLIPSOID_ID value in the SDO_ELLIPSOIDS table (see SDO_ELLIPSOIDS Table). Example: `8045`                    |
| PRIME_MERIDIAN_ID  | NUMBER(10)    | ID number of the prime meridian used in the datum definition. Must match a PRIME_MERIDIAN_ID value in the SDO_PRIME_MERIDIANS table (see SDO_PRIME_MERIDIANS Table). Example: `8950` |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition of the datum. Example: `Ordnance Survey of Great Britain.`                                                                                                |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                                                 |
| SHIFT_X            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the x-axis.                                                                         |
| SHIFT_Y            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the y-axis.                                                                         |
| SHIFT_Z            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the z-axis.                                                                         |
| ROTATE_X           | NUMBER        | Number of arc-seconds of rotation about the x-axis.                                                                                                                                  |
| ROTATE_Y           | NUMBER        | Number of arc-seconds of rotation about the y-axis.                                                                                                                                  |
| ROTATE_Z           | NUMBER        | Number of arc-seconds of rotation about the z-axis.                                                                                                                                  |
| SCALE_ADJUST       | NUMBER        | A value to be used in adjusting the X, Y, and Z values after any shifting and rotation, according to the formula: 1.0 + (SCALE_ADJUST \* 10<sup>-6</sup>)                            |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.21 SDO_DATUM_VERTICAL View

The SDO_DATUM_VERTICAL view contains selected information from the SDO_DATUMS table (described in SDO_DATUMS Table) where the DATUM_TYPE column value is `VERTICAL`. This view contains the columns shown in Table 6-20.

Table 6-20 SDO_DATUM_VERTICAL View

| Column Name        | Data Type     | Description                                                                                                                                                                          |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATUM_ID           | NUMBER(10)    | ID number of the datum.                                                                                                                                                              |
| DATUM_NAME         | VARCHAR2(80)  | Name of the datum.                                                                                                                                                                   |
| ELLIPSOID_ID       | NUMBER(10)    | ID number of the ellipsoid used in the datum definition. Must match an ELLIPSOID_ID value in the SDO_ELLIPSOIDS table (see SDO_ELLIPSOIDS Table). Example: `8045`                    |
| PRIME_MERIDIAN_ID  | NUMBER(10)    | ID number of the prime meridian used in the datum definition. Must match a PRIME_MERIDIAN_ID value in the SDO_PRIME_MERIDIANS table (see SDO_PRIME_MERIDIANS Table). Example: `8950` |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition of the datum. Example: `Ordnance Survey of Great Britain.`                                                                                                |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle).                                                                                                                 |
| SHIFT_X            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the x-axis.                                                                         |
| SHIFT_Y            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the y-axis.                                                                         |
| SHIFT_Z            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the z-axis.                                                                         |
| ROTATE_X           | NUMBER        | Number of arc-seconds of rotation about the x-axis.                                                                                                                                  |
| ROTATE_Y           | NUMBER        | Number of arc-seconds of rotation about the y-axis.                                                                                                                                  |
| ROTATE_Z           | NUMBER        | Number of arc-seconds of rotation about the z-axis.                                                                                                                                  |
| SCALE_ADJUST       | NUMBER        | A value to be used in adjusting the X, Y, and Z values after any shifting and rotation, according to the formula: 1.0 + (SCALE_ADJUST \* 10<sup>-6</sup>)                            |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.22 SDO_DATUMS Table

The SDO_DATUMS table contains one row for each datum. This table contains the columns shown in Table 6-21.

Table 6-21 SDO_DATUMS Table

| Column Name        | Data Type     | Description                                                                                                                                                                          |
|:-------------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATUM_ID           | NUMBER(10)    | ID number of the datum. Example: `10115`                                                                                                                                             |
| DATUM_NAME         | VARCHAR2(80)  | Name of the datum. Example: `WGS 84`                                                                                                                                                 |
| DATUM_TYPE         | VARCHAR2(24)  | Type of the datum. Example: `GEODETIC`                                                                                                                                               |
| ELLIPSOID_ID       | NUMBER(10)    | ID number of the ellipsoid used in the datum definition. Must match an ELLIPSOID_ID value in the SDO_ELLIPSOIDS table (see SDO_ELLIPSOIDS Table). Example: `8045`                    |
| PRIME_MERIDIAN_ID  | NUMBER(10)    | ID number of the prime meridian used in the datum definition. Must match a PRIME_MERIDIAN_ID value in the SDO_PRIME_MERIDIANS table (see SDO_PRIME_MERIDIANS Table). Example: `8950` |
| INFORMATION_SOURCE | VARCHAR2(254) | Provider of the definition of the datum. Example: `Ordnance Survey of Great Britain.`                                                                                                |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle). Example: `EPSG`                                                                                                 |
| SHIFT_X            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the x-axis.                                                                         |
| SHIFT_Y            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the y-axis.                                                                         |
| SHIFT_Z            | NUMBER        | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the z-axis.                                                                         |
| ROTATE_X           | NUMBER        | Number of arc-seconds of rotation about the x-axis.                                                                                                                                  |
| ROTATE_Y           | NUMBER        | Number of arc-seconds of rotation about the y-axis.                                                                                                                                  |
| ROTATE_Z           | NUMBER        | Number of arc-seconds of rotation about the z-axis.                                                                                                                                  |
| SCALE_ADJUST       | NUMBER        | A value to be used in adjusting the X, Y, and Z values after any shifting and rotation, according to the formula: 1.0 + (SCALE_ADJUST \* 10<sup>-6</sup>)                            |
| IS_LEGACY          | VARCHAR2(5)   | `TRUE` if the datum definition was included in Oracle Spatial before release 10.2; `FALSE` if the datum definition was new in Oracle Spatial release 10.2.                           |
| LEGACY_CODE        | NUMBER(10)    | For any EPSG datum that has a semantically identical legacy (in Oracle Spatial before release 10.2) counterpart, the DATUM_ID value of the legacy datum.                             |

See also the information about the following views that are defined based on the value of the DATUM_TYPE column: SDO_DATUM_ENGINEERING (SDO_DATUM_ENGINEERING View), SDO_DATUM_GEODETIC (SDO_DATUM_GEODETIC View), and SDO_DATUM_VERTICAL (SDO_DATUM_VERTICAL View).

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.23 SDO_ELLIPSOIDS Table

The SDO_ELLIPSOIDS table contains one row for each ellipsoid. This table contains the columns shown in Table 6-22.

Table 6-22 SDO_ELLIPSOIDS Table

| Column Name        | Data Type     | Description                                                                                                                                                                               |
|:-------------------|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ELLIPSOID_ID       | NUMBER        | ID number of the ellipsoid (spheroid). Example: `8045`                                                                                                                                    |
| ELLIPSOID_NAME     | VARCHAR2(80)  | Name of the ellipsoid. Example: `WGS 84`                                                                                                                                                  |
| SEMI_MAJOR_AXIS    | NUMBER        | Radius in meters along the semi-major axis (one-half of the long axis of the ellipsoid).                                                                                                  |
| UOM_ID             | NUMBER        | ID number of the unit of measurement for the ellipsoid. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table). Example: `9001` |
| INV_FLATTENING     | NUMBER        | Inverse flattening of the ellipsoid. That is, `1/f`, where` f = (a-b)/a`, and `a` is the semi-major axis and `b` is the semi-minor axis.                                                  |
| SEMI_MINOR_AXIS    | NUMBER        | Radius in meters along the semi-minor axis (one-half of the short axis of the ellipsoid).                                                                                                 |
| INFORMATION_SOURCE | VARCHAR2(254) | Origin of this information. Example: `Kort og Matrikelstyrelsen (KMS), Copenhagen.`                                                                                                       |
| DATA_SOURCE        | VARCHAR2(40)  | Organization that supplied the data for this record (if not Oracle). Example: `EPSG`                                                                                                      |
| IS_LEGACY          | VARCHAR2(5)   | `TRUE` if the ellipsoid definition was included in Oracle Spatial before release 10.2; `FALSE` if the ellipsoid definition was new in Oracle Spatial release 10.2.                        |
| LEGACY_CODE        | NUMBER        | For any EPSG ellipsoid that has a semantically identical legacy (in Oracle Spatial before release 10.2) counterpart, the ELLIPSOID_ID value of the legacy ellipsoid.                      |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.24 SDO_PREFERRED_OPS_SYSTEM Table

The SDO_PREFERRED_OPS_SYSTEM table contains one row for each specification of the user-defined default preferred coordinate transformation operation for a source and target SRID combination. If you insert a row into the SDO_PREFERRED_OPS_SYSTEM table, you are overriding the Oracle default operation for transformations between the specified source and target coordinate systems. The [SDO_CS.CREATE_OBVIOUS_EPSG_RULES](SDO_CS-reference.md) procedure inserts many rows into this table. The [SDO_CS.DELETE_ALL_EPSG_RULES](SDO_CS-reference.md) procedure deletes all rows from this table if the `use_case` parameter is null. This table contains the columns shown in Table 6-23.

Table 6-23 SDO_PREFERRED_OPS_SYSTEM Table

| Column Name | Data Type  | Description                                                                                                                                                                                                                                |
|:------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SOURCE_SRID | NUMBER(10) | ID number of the coordinate system (spatial reference system) from which to perform coordinate transformation, using the operation specified by COORD_OP_ID as the default preferred method for transforming to the specified target SRID. |
| COORD_OP_ID | NUMBER(10) | ID number of the coordinate transformation operation. Matches a value in the COORD_OP_ID column of the SDO_COORD_OPS table (described in SDO_COORD_OPS Table).                                                                             |
| TARGET_SRID | NUMBER(10) | ID number of coordinate system (spatial reference system) into which to perform coordinate transformation using the operation specified by COORD_OP_ID.                                                                                    |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.25 SDO_PREFERRED_OPS_USER Table

The SDO_PREFERRED_OPS_USER table contains one row for each specification of a user-defined source and target SRID and coordinate transformation operation. If you insert a row into the SDO_PREFERRED_OPS_USER table, you create a custom transformation between the source and target coordinate systems, and you can specify the name (the USE_CASE column value) of the transformation operation as the `use_case` parameter value with several SDO_CS functions and procedures. If you specify a use case with the [SDO_CS.DELETE_ALL_EPSG_RULES](SDO_CS-reference.md) procedure, rows associated with that use case are deleted from this table. This table contains the columns shown in Table 6-24.

Table 6-24 SDO_PREFERRED_OPS_USER Table

| Column Name | Data Type    | Description                                                                                                                                                    |
|:------------|:-------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| USE_CASE    | VARCHAR2(32) | Name of this specification of a source and target SRID and coordinate transformation operation.                                                                |
| SOURCE_SRID | NUMBER(10)   | ID number of the coordinate system (spatial reference system) from which to perform the transformation.                                                        |
| COORD_OP_ID | NUMBER(10)   | ID number of the coordinate transformation operation. Matches a value in the COORD_OP_ID column of the SDO_COORD_OPS table (described in SDO_COORD_OPS Table). |
| TARGET_SRID | NUMBER(10)   | ID number of the coordinate system (spatial reference system) into which to perform the transformation.                                                        |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.26 SDO_PRIME_MERIDIANS Table

The SDO_PRIME_MERIDIANS table contains one row for each prime meridian that can be used in a datum specification. This table contains the columns shown in Table 6-25.

Table 6-25 SDO_PRIME_MERIDIANS Table

| Column Name         | Data Type     | Description                                                                                                                                                                                                           |
|:--------------------|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PRIME_MERIDIAN_ID   | NUMBER(10)    | ID number of the prime meridian. Example: `8907`                                                                                                                                                                      |
| PRIME_MERIDIAN_NAME | VARCHAR2(80)  | Name of the prime meridian. Example: `Bern`                                                                                                                                                                           |
| GREENWICH_LONGITUDE | FLOAT(49)     | Longitude of the prime meridian as an offset from the Greenwich meridian. Example: `7.26225`                                                                                                                          |
| UOM_ID              | NUMBER(10)    | ID number of the unit of measurement for the prime meridian. Matches a value in the UOM_ID column of the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table). Example: `9110` for sexagesimal degree |
| INFORMATION_SOURCE  | VARCHAR2(254) | Origin of this information. Example: `Bundesamt fur Landestopographie`                                                                                                                                                |
| DATA_SOURCE         | VARCHAR2(254) | Organization that supplied the data for this record (if not Oracle). Example: `EPSG`                                                                                                                                  |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.27 SDO_UNITS_OF_MEASURE Table

The SDO_UNITS_OF_MEASURE table contains one row for each unit of measurement. This table contains the columns shown in Table 6-26.

Table 6-26 SDO_UNITS_OF_MEASURE Table

| Column Name        | Data Type      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UOM_ID             | NUMBER(10)     | ID number of the unit of measurement. Example: `10032`                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| UNIT_OF_MEAS_NAME  | VARCHAR2(2083) | Name of the unit of measurement; can also be a URL or URI. Example: `Meter`                                                                                                                                                                                                                                                                                                                                                                                                                    |
| SHORT_NAME         | VARCHAR2(80)   | Short name (if any) of the unit of measurement. Example: `METER`                                                                                                                                                                                                                                                                                                                                                                                                                               |
| UNIT_OF_MEAS_TYPE  | VARCHAR2(50)   | Type of measure for which the unit is used: `angle` for angle unit, `area` for area unit, `length` for distance unit, `scale` for scale unit, or `volume` for volume unit.                                                                                                                                                                                                                                                                                                                     |
| TARGET_UOM_ID      | NUMBER(10)     | ID number of a target unit of measurement. Corresponds to the TARGET_UOM_CODE column in the EPSG Unit of Measure table, which has the following description: "Other UOM of the same type into which the current UOM can be converted using the formula (POSC); POSC factors A and D always equal zero for EPSG supplied units of measure."                                                                                                                                                     |
| FACTOR_B           | NUMBER         | Corresponds to the FACTOR_B column in the EPSG Unit of Measure table, which has the following description: "A quantity in the target UOM (y) is obtained from a quantity in the current UOM (x) through the conversion: y = (B/C).x"<br>In a user-defined unit of measurement, FACTOR_B is usually the number of square meters or meters equal to one of the unit. For information about user-defined units, see [Creating a User-Defined Unit of Measurement](spatial-datatypes-metadata.md). |
| FACTOR_C           | NUMBER         | Corresponds to the FACTOR_C column in the EPSG Unit of Measure table.<br>For FACTOR_C in a user-defined unit of measurement, see [Creating a User-Defined Unit of Measurement](spatial-datatypes-metadata.md).                                                                                                                                                                                                                                                                                 |
| INFORMATION_SOURCE | VARCHAR2(254)  | Origin of this information. Example: `ISO 1000.`                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| DATA_SOURCE        | VARCHAR2(40)   | Organization providing the data for this record. Example: `EPSG`                                                                                                                                                                                                                                                                                                                                                                                                                               |
| IS_LEGACY          | VARCHAR2(5)    | TRUE if the unit of measurement definition was included in Oracle Spatial before release 10.2; FALSE if the unit of measurement definition was new in Oracle Spatial release 10.2.                                                                                                                                                                                                                                                                                                             |
| LEGACY_CODE        | NUMBER(10)     | For any EPSG unit of measure that has a semantically identical legacy (in Oracle Spatial before release 10.2) counterpart, the UOM_ID value of the legacy unit of measure.                                                                                                                                                                                                                                                                                                                     |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.28 Relationships Among Coordinate System Tables and Views

Although the spatial system tables and views are based on the EPSG data model and dataset, Spatial and Graph changes the names of some tables to conform to its own naming conventions, and it does not use some tables, as shown in Table 6-27.

Table 6-27 EPSG Table Names and Oracle Spatial and Graph Names

| EPSG Name                             | Oracle Name             |
|:--------------------------------------|:------------------------|
| Coordinate System                     | SDO_COORD_SYS           |
| Coordinate Axis                       | SDO_COORD_AXES          |
| Coordinate Reference System           | SDO_COORD_REF_SYSTEM    |
| Area Of Use                           | (Not used)              |
| Datum                                 | SDO_DATUMS              |
| Prime Meridian                        | SDO_PRIME_MERIDIANS     |
| Ellipsoid                             | SDO_ELLIPSOIDS          |
| Unit Of Measure                       | SDO_UNITS_OF_MEASURE    |
| Coordinate Operation                  | SDO_COORD_OPS           |
| Coord. Operation Parameter ValueCoord | SDO_COORD_OP_PARAM_VALS |
| Operation Parameter UsageCoord.       | SDO_COORD_OP_PARAM_USE  |
| Operation Parameter                   | SDO_COORD_OP_PARAMS     |
| Coordinate Operation Path             | SDO_COORD_OP_PATHS      |
| Coordinate Operation Method           | SDO_COORD_OP_METHODS    |
| Change                                | (Not used)              |
| Deprecation                           | (Not used)              |
| Supersession                          | (Not used)              |
| Naming System                         | (Not used)              |
| Alias                                 | (Not used)              |
| Any Entity                            | (Not used)              |

**Parent topic:** Coordinate Systems Data Structures

#### 6.7.29 Finding Information About EPSG-Based Coordinate Systems

This section explains how to query the Spatial and Graph coordinate systems data structures for information about geodetic and projected EPSG-based coordinate systems.

- Geodetic Coordinate Systems
- Projected Coordinate Systems

**Parent topic:** Coordinate Systems Data Structures

##### 6.7.29.1 Geodetic Coordinate Systems

A human-readable summary of a CRS is the WKT string. For example:

    SQL> select wktext from cs_srs where srid = 4326;

    WKTEXT
    --------------------------------------------------------------------------------
    GEOGCS [ "WGS 84", DATUM ["World Geodetic System 1984 (EPSG ID 6326)", SPHEROID
    ["WGS 84 (EPSG ID 7030)", 6378137, 298.257223563]], PRIMEM [ "Greenwich", 0.0000
    00 ], UNIT ["Decimal Degree", 0.01745329251994328]]

EPSG WKTs have been automatically generated by Spatial and Graph, for backward compatibility. Note that EPSG WKTs also contain numeric ID values (such as EPSG ID 6326 in the preceding example) for convenience. However, for more detailed information you should access the EPSG data stored in the coordinate systems data structures. The following example returns information about the ellipsoid, datum shift, rotation, and scale adjustment for SRID 4123:

    SQL> select
      ell.semi_major_axis,
      ell.inv_flattening,
      ell.semi_minor_axis,
      ell.uom_id,
      dat.shift_x,
      dat.shift_y,
      dat.shift_z,
      dat.rotate_x,
      dat.rotate_y,
      dat.rotate_z,
      dat.scale_adjust
    from
      sdo_coord_ref_system crs,
      sdo_datums dat,
      sdo_ellipsoids ell
    where
      crs.srid = 4123 and
      dat.datum_id = crs.datum_id and
      ell.ellipsoid_id = dat.ellipsoid_id;

    SEMI_MAJOR_AXIS INV_FLATTENING SEMI_MINOR_AXIS     UOM_ID    SHIFT_X    SHIFT_Y    SHIFT_Z   ROTATE_X   ROTATE_Y   ROTATE_Z SCALE_ADJUST
    --------------- -------------- --------------- ---------- ---------- ---------- ---------- ---------- ---------- ---------- ------------
            6378388            297      6356911.95       9001      -90.7     -106.1     -119.2       4.09       .218      -1.05         1.37

In the preceding example, the UOM_ID represents the unit of measure for SEMI_MAJOR_AXIS (`a`) and SEMI_MINOR_AXIS (`b`). INV_FLATTENING is `a/(a-b) `and has no associated unit. Shifts are in meters, rotation angles are given in arc seconds, and scale adjustment in parts per million.

To interpret the UOM_ID, you can query the units table, as shown in the following example:

    SQL> select UNIT_OF_MEAS_NAME from sdo_units_of_measure where UOM_ID = 9001;

    UNIT_OF_MEAS_NAME
    --------------------------------------------------------------------------------
    metre

Conversion factors for units of length are given relative to meters, as shown in the following example:

    SQL> select UNIT_OF_MEAS_NAME, FACTOR_B/FACTOR_C from sdo_units_of_measure where UOM_ID = 9002;

    UNIT_OF_MEAS_NAME
    --------------------------------------------------------------------------------
    FACTOR_B/FACTOR_C
    -----------------
    foot
                .3048

Conversion factors for units of angle are given relative to radians, as shown in the following example:

    SQL> select UNIT_OF_MEAS_NAME, FACTOR_B/FACTOR_C from sdo_units_of_measure where UOM_ID = 9102;

    UNIT_OF_MEAS_NAME
    --------------------------------------------------------------------------------
    FACTOR_B/FACTOR_C
    -----------------
    degree
           .017453293

**Parent topic:** Finding Information About EPSG-Based Coordinate Systems

##### 6.7.29.2 Projected Coordinate Systems

As mentioned in Geodetic Coordinate Systems, the WKT is a human-readable summary of a CRS, but the actual EPSG data is stored in the Spatial and Graph coordinate systems data structures. The following example shows the WKT string for a projected coordinate system:

    SQL> select wktext from cs_srs where srid = 32040;

    WKTEXT
    --------------------------------------------------------------------------------
    PROJCS["NAD27 / Texas South Central", GEOGCS [ "NAD27", DATUM ["North American D
    atum 1927 (EPSG ID 6267)", SPHEROID ["Clarke 1866 (EPSG ID 7008)", 6378206.4, 29
    4.978698213905820761610537123195175418]], PRIMEM [ "Greenwich", 0.000000 ], UNIT
     ["Decimal Degree", 0.01745329251994328]], PROJECTION ["Texas CS27 South Central
     zone (EPSG OP 14204)"], PARAMETER ["Latitude_Of_Origin", 27.8333333333333333333
    3333333333333333333], PARAMETER ["Central_Meridian", -98.99999999999999999999999
    999999999999987], PARAMETER ["Standard_Parallel_1", 28.3833333333333333333333333
    3333333333333], PARAMETER ["Standard_Parallel_2", 30.283333333333333333333333333
    33333333333], PARAMETER ["False_Easting", 2000000], PARAMETER ["False_Northing",
     0], UNIT ["U.S. Foot", .3048006096012192024384048768097536195072]]

To determine the base geographic CRS for a projected CRS, you can query the SDO_COORD_REF_SYSTEM table, as in the following example:

    SQL> select SOURCE_GEOG_SRID from sdo_coord_ref_system where srid = 32040;

    SOURCE_GEOG_SRID
    ----------------
                4267

The following example returns the projection method for the projected CRS 32040:

    SQL> select
      m.coord_op_method_name
    from
      sdo_coord_ref_sys crs,
      sdo_coord_ops ops,
      sdo_coord_op_methods m
    where
      crs.srid = 32040 and
      ops.coord_op_id = crs.projection_conv_id and
      m.coord_op_method_id = ops.coord_op_method_id;

    COORD_OP_METHOD_NAME
    --------------------------------------------------
    Lambert Conic Conformal (2SP)

The following example returns the projection parameters for the projected CRS 32040:

    SQL> select
      params.parameter_name || ' = ' ||
      vals.parameter_value || ' ' ||
      uom.unit_of_meas_name "Projection parameters"
    from
      sdo_coord_ref_sys crs,
      sdo_coord_op_param_vals vals,
      sdo_units_of_measure uom,
      sdo_coord_op_params params
    where
      crs.srid = 32040 and
      vals.coord_op_id = crs.projection_conv_id and
      uom.uom_id = vals.uom_id and
      params.parameter_id = vals.parameter_id;

    Projection parameters
    --------------------------------------------------------------------------------
    Latitude of false origin = 27.5 sexagesimal DMS
    Longitude of false origin = -99 sexagesimal DMS
    Latitude of 1st standard parallel = 28.23 sexagesimal DMS
    Latitude of 2nd standard parallel = 30.17 sexagesimal DMS
    Easting at false origin = 2000000 US survey foot
    Northing at false origin = 0 US survey foot


The following example is essentially the same query as the preceding example, but it also converts the values to the base unit:

    SQL> select
      params.parameter_name || ' = ' ||
      vals.parameter_value || ' ' ||
      uom.unit_of_meas_name || ' = ' ||
      sdo_cs.transform_to_base_unit(vals.parameter_value, vals.uom_id) || ' ' ||
      decode(
        uom.unit_of_meas_type,
        'area', 'square meters',
        'angle', 'radians',
        'length', 'meters',
        'scale', '', '') "Projection parameters"
    from
      sdo_coord_ref_sys crs,
      sdo_coord_op_param_vals vals,
      sdo_units_of_measure uom,
      sdo_coord_op_params params
    where
      crs.srid = 32040 and
      vals.coord_op_id = crs.projection_conv_id and
      uom.uom_id = vals.uom_id and
      params.parameter_id = vals.parameter_id;

    Projection parameters
    --------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    Latitude of false origin = 27.5 sexagesimal DMS = .485783308471754564814814814814814814815 radians
    Longitude of false origin = -99 sexagesimal DMS = -1.7278759594743845 radians
    Latitude of 1st standard parallel = 28.23 sexagesimal DMS = .495382619357723367592592592592592592593 radians
    Latitude of 2nd standard parallel = 30.17 sexagesimal DMS = .528543875145615595370370370370370370371 radians
    Easting at false origin = 2000000 US survey foot = 609601.219202438404876809753619507239014 meters
    Northing at false origin = 0 US survey foot = 0 meters

The following example returns the projection unit of measure for the projected CRS 32040. (The projection unit might be different from the length unit used for the projection parameters.)

    SQL> select
      axes.coord_axis_abbreviation || ': ' ||
      uom.unit_of_meas_name "Projection units"
    from
      sdo_coord_ref_sys crs,
      sdo_coord_axes axes,
      sdo_units_of_measure uom
    where
      crs.srid = 32040 and
      axes.coord_sys_id = crs.coord_sys_id and
      uom.uom_id = axes.uom_id;

    Projection units
    ------------------------------------------------------------------------------
    X: US survey foot
    Y: US survey foot

**Parent topic:** Finding Information About EPSG-Based Coordinate Systems

### 6.8 Legacy Tables and Views

In releases of Spatial and Graph before 10.2, the coordinate systems functions and procedures used information provided in the following tables, some of which have new names or are now views instead of tables.

- MDSYS.CS_SRS defines the valid coordinate systems. It associates each coordinate system with its well-known text description, which is in conformance with the standard published by the Open Geospatial Consortium (`http://www.opengeospatial.org`).

- MDSYS.SDO_ANGLE_UNITS defines the valid angle units.

- MDSYS.SDO_AREA_UNITS defines the valid area units.

- MDSYS.SDO_DIST_UNITS defines the valid distance units.

- MDSYS.SDO_DATUMS_OLD_FORMAT and MDSYS.SDO_DATUMS_OLD_SNAPSHOT are based on the MDSYS.SDO_DATUMS table before release 10.2, which defined valid datums.

- MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT and MDSYS.SDO_ELLIPSOIDS_OLD_SNAPSHOT are based on the MDSYS.SDO_ELLIPSOIDS table before release 10.2, which defined valid ellipsoids.

- MDSYS.SDO_PROJECTIONS_OLD_FORMAT and MDSYS.SDO_PROJECTIONS_OLD_SNAPSHOT are based on the MDSYS.SDO_PROJECTIONS table before release 10.2, which defined the valid map projections.

  **Note:**

  You should not modify or delete any Oracle-supplied information in these legacy tables.

  If you refer to a legacy table in a SQL statement, you must include the MDSYS. before the table name.

<!-- -->

- MDSYS.CS_SRS Table
- MDSYS.SDO_ANGLE_UNITS View
- MDSYS.SDO_AREA_UNITS View
- MDSYS.SDO_DATUMS_OLD_FORMAT and SDO_DATUMS_OLD_SNAPSHOT Tables
- MDSYS.SDO_DIST_UNITS View
- MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT and SDO_ELLIPSOIDS_OLD_SNAPSHOT Tables
- MDSYS.SDO_PROJECTIONS_OLD_FORMAT and SDO_PROJECTIONS_OLD_SNAPSHOT Tables

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.8.1 MDSYS.CS_SRS Table

The MDSYS.CS_SRS reference table contains over 4000 rows, one for each valid coordinate system. This table contains the following columns:

Table 6-28 MDSYS.CS_SRS Table

| Column Name | Data Type      | Description                                                                                                                                                                                                                                                                                           |
|:------------|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CS_NAME     | VARCHAR2(68)   | A well-known name, often mnemonic, by which a user can refer to the coordinate system.                                                                                                                                                                                                                |
| SRID        | NUMBER(38)     | The unique ID number (Spatial Reference ID) for a coordinate system. All SRID values are reserved for use by Oracle Spatial and Graph except for values 5000000 to 6000000 (5 million to 6 million) which are available for user-defined coordinate systems.                                          |
| AUTH_SRID   | NUMBER(38)     | An optional ID number that can be used to indicate how the entry was derived; it might be a foreign key into another coordinate table, for example.                                                                                                                                                   |
| AUTH_NAME   | VARCHAR2(256)  | An authority name for the coordinate system. Contains `Oracle` in the supplied table. Users can specify any value in any rows that they add.                                                                                                                                                          |
| WKTEXT      | VARCHAR2(2046) | The well-known text (WKT) description of the SRS, as defined by the Open Geospatial Consortium. For more information, see Well-Known Text (WKT).                                                                                                                                                      |
| CS_BOUNDS   | SDO_GEOMETRY   | An optional SDO_GEOMETRY object that is a polygon with WGS 84 longitude and latitude vertices, representing the spheroidal polygon description of the zone of validity for a projected coordinate system. Must be null for a geographic or non-Earth coordinate system. Is null in all supplied rows. |

- Well-Known Text (WKT)
- US-American and European Notations for Datum Parameters
- Procedures for Updating the Well-Known Text

**Parent topic:** Legacy Tables and Views

##### 6.8.1.1 Well-Known Text (WKT)

The WKTEXT column of the MDSYS.CS_SRS table contains the well-known text (WKT) description of the SRS, as defined by the Open Geospatial Consortium. The following is the WKT EBNF syntax.

    <coordinate system> ::=
         <horz cs> | <local cs>

    <horz cs> ::=
         <geographic cs> | <projected cs>

    <projected cs> ::=
         PROJCS [ "<name>", <geographic cs>, <projection>,
               {<parameter>,}* <linear unit> ]

    <projection> ::=
         PROJECTION [ "<name>" ]

    <parameter> ::=
         PARAMETER [ "<name>", <number> ]

    <geographic cs> ::=
         GEOGCS [ "<name>", <datum>, <prime meridian>, <angular unit> ]

    <datum> ::=
         DATUM [ "<name>", <spheroid>
         {, <shift-x>, <shift-y>, <shift-z>
           , <rot-x>, <rot-y>, <rot-z>, <scale_adjust>}
         ]

    <spheroid> ::=
         SPHEROID ["<name>", <semi major axis>, <inverse flattening> ]

    <prime meridian> ::=
         PRIMEM ["<name>", <longitude> ]

    <longitude> ::=
         <number>

    <semi-major axis> ::=
         <number>

    <inverse flattening> ::=
         <number>

    <angular unit> ::= <unit>

    <linear unit> ::= <unit>

    <unit> ::=
         UNIT [ "<name>", <conversion factor> ]

    <local cs> ::=
         LOCAL_CS [ "<name>", <local datum>, <linear unit>,
              <axis> {, <axis>}* ]

    <local datum> ::=
         LOCAL_DATUM [ "<name>", <datum type>
              {, <shift-x>, <shift-y>, <shift-z>
               , <rot-x>, <rot-y>, <rot-z>, <scale_adjust>}
              ]

    <datum type> ::=
         <number>

    <axis> ::=
         AXIS [ "<name>", NORTH | SOUTH | EAST |
               WEST | UP | DOWN | OTHER ]

Each `<parameter>` specification is one of the following:

- `Standard_Parallel_1` (in decimal degrees)

- `Standard_Parallel_2` (in decimal degrees)

- `Central_Meridian` (in decimal degrees)

- `Latitude_of_Origin` (in decimal degrees)

- `Azimuth` (in decimal degrees)

- `False_Easting` (in the unit of the coordinate system; for example, meters)

- `False_Northing` (in the unit of the coordinate system; for example, meters)

- `Perspective_Point_Height` (in the unit of the coordinate system; for example, meters)

- `Landsat_Number` (must be 1, 2, 3, 4, or 5)

- `Path_Number`

- `Scale_Factor`

**Note:**

If the WKT uses European rather than US-American notation for datum rotation parameters, or if the transformation results do not seem correct, see US-American and European Notations for Datum Parameters.

The default value for each `<parameter>` specification is 0 (zero). That is, if a specification is needed for a projection but no value is specified in the WKT, Spatial and Graph uses a value of 0.

The prime meridian (`PRIMEM`) is specified in decimal degrees of longitude.

An example of the WKT for a geodetic (geographic) coordinate system is:

    'GEOGCS [ "Longitude / Latitude (Old Hawaiian)", DATUM ["Old Hawaiian", SPHEROID
    ["Clarke 1866", 6378206.400000, 294.978698]], PRIMEM [ "Greenwich", 0.000000 ],
    UNIT ["Decimal Degree", 0.01745329251994330]]'

The WKT definition of the coordinate system is hierarchically nested. The Old Hawaiian geographic coordinate system (GEOGCS) is composed of a named datum (DATUM), a prime meridian (PRIMEM), and a unit definition (UNIT). The datum is in turn composed of a named spheroid and its parameters of semi-major axis and inverse flattening.

An example of the WKT for a projected coordinate system (a Wyoming State Plane) is:

    'PROJCS["Wyoming 4901, Eastern Zone (1983, meters)", GEOGCS [ "GRS 80", DATUM
    ["GRS 80", SPHEROID ["GRS 80", 6378137.000000, 298.257222]], PRIMEM [
    "Greenwich", 0.000000 ], UNIT ["Decimal Degree", 0.01745329251994330]],
    PROJECTION ["Transverse Mercator"], PARAMETER ["Scale_Factor", 0.999938],
    PARAMETER ["Central_Meridian", -105.166667], PARAMETER ["Latitude_Of_Origin",
    40.500000], PARAMETER ["False_Easting", 200000.000000], UNIT ["Meter",
    1.000000000000]]'

The projected coordinate system contains a nested geographic coordinate system as its basis, as well as parameters that control the projection.

Oracle Spatial and Graph supports all common geodetic datums and map projections.

An example of the WKT for a local coordinate system is:

    LOCAL_CS [ "Non-Earth (Meter)", LOCAL_DATUM ["Local Datum", 0], UNIT ["Meter", 1.0], AXIS ["X", EAST], AXIS["Y", NORTH]]

For more information about local coordinate systems, see Local Coordinate Support.

You can use the [SDO_CS.VALIDATE_WKT](SDO_CS-reference.md) function, described in [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md) , to validate the WKT of any coordinate system defined in the MDSYS.CS_SRS table.

**Parent topic:** MDSYS.CS_SRS Table

##### 6.8.1.2 US-American and European Notations for Datum Parameters

The datum-related WKT parameters are a list of up to seven Bursa Wolf transformation parameters. Rotation parameters specify arc seconds, and shift parameters specify meters.

Two different notations, US-American and European, are used for the three rotation parameters that are in general use, and these two notations use opposite signs. Spatial and Graph uses and expects the US-American notation. Therefore, if your WKT uses the European notation, you must convert it to the US-American notation by inverting the signs of the rotation parameters.

If you do not know if a parameter set uses the US-American or European notation, perform the following test:

1.  Select a single point for which you know the correct result.

2.  Perform the transformation using the current WKT.

3.  If the computed result does not match the known correct result, invert signs of the rotation parameters, perform the transformation, and check if the computed result matches the known correct result.

**Parent topic:** MDSYS.CS_SRS Table

##### 6.8.1.3 Procedures for Updating the Well-Known Text

If you insert or delete a row in the SDO_COORD_REF_SYSTEM view (described in SDO_COORD_REF_SYSTEM View), Spatial and Graph automatically updates the WKTEXT column in the MDSYS.CS_SRS table. (The format of the WKTEXT column is described in Well-Known Text (WKT).) However, if you update an existing row in the SDO_COORD_REF_SYSTEM view, the well-known text (WKT) value is not automatically updated.

In addition, information relating to coordinate reference systems is also stored in several other system tables, including SDO_DATUMS (described in SDO_DATUMS Table), SDO_ELLIPSOIDS (described in SDO_ELLIPSOIDS Table), and SDO_PRIME_MERIDIANS (described in SDO_PRIME_MERIDIANS Table). If you add, delete, or modify information in these tables, the WKTEXT values in the MDSYS.CS_SRS table are not automatically updated. For example, if you update an ellipsoid flattening value in the SDO_ELLIPSOIDS table, the well-known text string for the associated coordinate system is not updated.

However, you can manually update the WKTEXT values in the in the MDSYS.CS_SRS table by using any of several procedures whose names start with UPDATE_WKTS_FOR (for example, [SDO_CS.UPDATE_WKTS_FOR_ALL_EPSG_CRS](SDO_CS-reference.md) and [SDO_CS.UPDATE_WKTS_FOR_EPSG_DATUM](SDO_CS-reference.md)). If the display of SERVEROUTPUT information is enabled, these procedures display a message identifying the SRID value for each row in the MDSYS.CS_SRS table whose WKTEXT value is being updated. These procedures are described in [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md) .

**Parent topic:** MDSYS.CS_SRS Table

#### 6.8.2 MDSYS.SDO_ANGLE_UNITS View

The MDSYS.SDO_ANGLE_UNITS reference view contains one row for each valid angle UNIT specification in the well-known text (WKT) description in the coordinate system definition. The WKT is described in Well-Known Text (WKT).

The MDSYS.SDO_ANGLE_UNITS view is based on the SDO_UNITS_OF MEASURE table (described in SDO_UNITS_OF_MEASURE Table), and it contains the columns shown in Table 6-29.

Table 6-29 MDSYS.SDO_ANGLE_UNITS View

| Column Name       | Data Type     | Description                                                                                                                                                                                                          |
|:------------------|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDO_UNIT          | VARCHAR2(32)  | Name of the angle unit (often a shortened form of the UNIT_NAME value). Use the SDO_UNIT value with the `from_unit` and `to_unit` parameters of the [SDO_UTIL.CONVERT_UNIT](SDO_UTIL-reference.md) function.         |
| UNIT_NAME         | VARCHAR2(100) | Name of the angle unit. Specify a value from this column in the UNIT specification of the WKT for any user-defined coordinate system. Examples: `Decimal Degree, Radian, Decimal Second, Decimal Minute, Gon, Grad`. |
| CONVERSION_FACTOR | NUMBER        | The ratio of the specified unit to one radian. For example, the ratio of `Decimal Degree` to `Radian` is 0.017453293.                                                                                                |

**Parent topic:** Legacy Tables and Views

#### 6.8.3 MDSYS.SDO_AREA_UNITS View

The MDSYS.SDO_AREA_UNITS reference view contains one row for each valid area UNIT specification in the well-known text (WKT) description in the coordinate system definition. The WKT is described in Well-Known Text (WKT).

The MDSYS.SDO_AREA_UNITS view is based on the SDO_UNITS_OF MEASURE table (described in SDO_UNITS_OF_MEASURE Table), and it contains the columns shown in Table 6-30.

Table 6-30 SDO_AREA_UNITS View

| Column Name       | Data Type | Purpose                                                                                                                                                    |
|:------------------|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDO_UNIT          | VARCHAR2  | Values are taken from the SHORT_NAME column of the SDO_UNITS_OF MEASURE table.                                                                             |
| UNIT_NAME         | VARCHAR2  | Values are taken from the UNIT_OF_MEAS_NAME column of the SDO_UNITS_OF MEASURE table.                                                                      |
| CONVERSION_FACTOR | NUMBER    | Ratio of the unit to 1 square meter. For example, the conversion factor for a square meter is 1.0, and the conversion factor for a square mile is 2589988. |

**Parent topic:** Legacy Tables and Views

#### 6.8.4 MDSYS.SDO_DATUMS_OLD_FORMAT and SDO_DATUMS_OLD_SNAPSHOT Tables

The MDSYS.SDO_DATUMS_OLD_FORMAT and MDSYS.SDO_DATUMS_OLD_SNAPSHOT reference tables contain one row for each valid DATUM specification in the well-known text (WKT) description in the coordinate system definition. (The WKT is described in Well-Known Text (WKT).)

- MDSYS.SDO_DATUMS_OLD_FORMAT contains the new data in the old format (that is, EPSG-based datum specifications in a table using the format from before release 10.2).

- MDSYS.SDO_DATUMS_OLD_SNAPSHOT contains the old data in the old format (that is, datum specifications and table format from before release 10.2).

These tables contain the columns shown in the following table.

Table 6-31 MDSYS.SDO_DATUMS_OLD_FORMAT and SDO_DATUMS_OLD_SNAPSHOT Tables

| Column Name  | Data Type                                                    | Description                                                                                                                                                                                                                                                                      |
|:-------------|:-------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NAME         | VARCHAR2(80) for OLD_FORMAT<br>VARCHAR2(64) for OLD_SNAPSHOT | Name of the datum. Specify a value (Oracle-supplied or user-defined) from this column in the DATUM specification of the WKT for any user-defined coordinate system. Examples: `Adindan, Afgooye, Ain el Abd 1970, Anna 1 Astro 1965, Arc 1950, Arc 1960, Ascension Island 1958.` |
| SHIFT_X      | NUMBER                                                       | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the x-axis.                                                                                                                                                                     |
| SHIFT_Y      | NUMBER                                                       | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the y-axis.                                                                                                                                                                     |
| SHIFT_Z      | NUMBER                                                       | Number of meters to shift the ellipsoid center relative to the center of the WGS 84 ellipsoid on the z-axis.                                                                                                                                                                     |
| ROTATE_X     | NUMBER                                                       | Number of arc-seconds of rotation about the x-axis.                                                                                                                                                                                                                              |
| ROTATE_Y     | NUMBER                                                       | Number of arc-seconds of rotation about the y-axis.                                                                                                                                                                                                                              |
| ROTATE_Z     | NUMBER                                                       | Number of arc-seconds of rotation about the z-axis.                                                                                                                                                                                                                              |
| SCALE_ADJUST | NUMBER                                                       | A value to be used in adjusting the X, Y, and Z values after any shifting and rotation, according to the formula: 1.0 + (SCALE_ADJUST \* 10<sup>-6</sup>)                                                                                                                        |

To see the names of the datums in these tables, enter an appropriate SELECT statement. For example:

    SELECT name FROM MDSYS.SDO_DATUMS_OLD_FORMAT ORDER BY name;

**Parent topic:** Legacy Tables and Views

#### 6.8.5 MDSYS.SDO_DIST_UNITS View

The MDSYS.SDO_DIST_UNITS reference view contains one row for each valid distance UNIT specification in the well-known text (WKT) description in the coordinate system definition. The WKT is described in Well-Known Text (WKT).

The MDSYS.SDO_DIST_UNITS view is based on the SDO_UNITS_OF MEASURE table (described in SDO_UNITS_OF_MEASURE Table), and it contains the columns shown in Table 6-32.

Table 6-32 MDSYS.SDO_DIST_UNITS View

| Column Name       | Data Type | Description                                                                                                                            |
|:------------------|:----------|:---------------------------------------------------------------------------------------------------------------------------------------|
| SDO_UNIT          | VARCHAR2  | Values are taken from the SHORT_NAME column of the SDO_UNITS_OF MEASURE table.                                                         |
| UNIT_NAME         | VARCHAR2  | Values are taken from the UNIT_OF_MEAS_NAME column of the SDO_UNITS_OF MEASURE table.                                                  |
| CONVERSION_FACTOR | NUMBER    | Ratio of the unit to 1 meter. For example, the conversion factor for a meter is 1.0, and the conversion factor for a mile is 1609.344. |

**Parent topic:** Legacy Tables and Views

#### 6.8.6 MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT and SDO_ELLIPSOIDS_OLD_SNAPSHOT Tables

The MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT and MDSYS.SDO_ELLIPSOIDS_OLD_SNAPSHOT reference tables contain one row for each valid SPHEROID specification in the well-known text (WKT) description in the coordinate system definition. (The WKT is described in Well-Known Text (WKT).)

- MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT contains the new data in the old format (that is, EPSG-based ellipsoid specifications in a table using the format from before release 10.2).

- MDSYS.SDO_ELLIPSOIDS_OLD_SNAPSHOT contains the old data in the old format (that is, ellipsoid specifications and table format from before release 10.2).

These tables contain the columns shown in the following table.

Table 6-33 MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT and SDO_ELLIPSOIDS_OLD_SNAPSHOT Tables

| Column Name        | Data Type                                                    | Description                                                                                                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NAME               | VARCHAR2(80) for OLD_FORMAT<br>VARCHAR2(64) for OLD_SNAPSHOT | Name of the ellipsoid (spheroid). Specify a value from this column in the SPHEROID specification of the WKT for any user-defined coordinate system. Examples: `Clarke 1866, WGS 72, Australian, Krassovsky, International 1924.` |
| SEMI_MAJOR_AXIS    | NUMBER                                                       | Radius in meters along the semi-major axis (one-half of the long axis of the ellipsoid).                                                                                                                                         |
| INVERSE_FLATTENING | NUMBER                                                       | Inverse flattening of the ellipsoid. That is, `1/f`, where` f = (a-b)/a`, and `a` is the semi-major axis and `b` is the semi-minor axis.                                                                                         |

To see the names of the ellipsoids in these tables, enter an appropriate SELECT statement. For example:

    SELECT name FROM MDSYS.SDO_ELLIPSOIDS_OLD_FORMAT ORDER BY name;

**Parent topic:** Legacy Tables and Views

#### 6.8.7 MDSYS.SDO_PROJECTIONS_OLD_FORMAT and SDO_PROJECTIONS_OLD_SNAPSHOT Tables

The MDSYS.SDO_PROJECTIONS_OLD_FORMAT and MDSYS.SDO_PROJECTIONS_OLD_SNAPSHOT reference tables contain one row for each valid PROJECTION specification in the well-known text (WKT) description in the coordinate system definition. (The WKT is described in Well-Known Text (WKT).)

- MDSYS.SDO_PROJECTIONS_OLD_FORMAT contains the new data in the old format (that is, EPSG-based projection specifications in a table using the format from before release 10.2).

- MDSYS.SDO_PROJECTIONS_OLD_SNAPSHOT contains the old data in the old format (that is, projection specifications and table format from before release 10.2).

These tables contains the column shown in the following table.

Table 6-34 MDSYS.SDO_PROJECTIONS_OLD_FORMAT and SDO_PROJECTIONS_OLD_SNAPSHOT Tables

| Column Name | Data Type                                                    | Description                                                                                                                                                                                                                                                           |
|:------------|:-------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NAME        | VARCHAR2(80) for OLD_FORMAT<br>VARCHAR2(64) for OLD_SNAPSHOT | Name of the map projection. Specify a value from this column in the PROJECTION specification of the WKT for any user-defined coordinate system. Examples: `Geographic (Lat/Long), Universal Transverse Mercator, State Plane Coordinates, Albers Conical Equal Area.` |

To see the names of the projections in these tables, enter an appropriate SELECT statement. For example:

    SELECT name FROM MDSYS.SDO_PROJECTIONS_OLD_FORMAT ORDER BY name;

**Parent topic:** Legacy Tables and Views

### 6.9 Creating a User-Defined Coordinate Reference System

If the coordinate systems supplied by Oracle are not sufficient for your needs, you can create user-defined coordinate reference systems.

**Note:**

As mentioned in Coordinate System (Spatial Reference System) , the terms coordinate system and coordinate reference system (CRS) are often used interchangeably, although coordinate reference systems must be Earth-based.

The exact steps for creating a user-defined CRS depend on whether it is geodetic or projected. In both cases, supply information about the coordinate system (coordinate axes, axis names, unit of measurement, and so on). For a geodetic CRS, supply information about the datum (ellipsoid, prime meridian, and so on), as explained in Creating a Geodetic CRS. For a projected CRS, supply information about the source (geodetic) CRS and the projection (operation and parameters), as explained in Creating a Projected CRS.

For any user-defined coordinate system, the SRID value should be 5000000 to 6000000 (5 million to 6 million) which are available for user-defined coordinate systems.

- Creating a Geodetic CRS
- Creating a Projected CRS
- Creating a Vertical CRS
- Creating a Compound CRS
- Creating a Geographic 3D CRS
- Creating a Transformation Operation
- Using British Grid Transformation OSTN02/OSGM02 (EPSG Method 9633)

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.9.1 Creating a Geodetic CRS

If the necessary unit of measurement, coordinate axes, SDO_COORD_SYS table row, ellipsoid, prime meridian, and datum are already defined, insert a row into the SDO_COORD_REF_SYSTEM view (described in SDO_COORD_REF_SYSTEM View) to define the new geodetic CRS.

Example 6-5 inserts the definition for a hypothetical geodetic CRS named `My Own NAD27` (which, except for its SRID and name, is the same as the `NAD27` CRS supplied by Oracle).

If the necessary information for the definition does not already exist, follow these steps, as needed, to define the information before you insert the row into the SDO_COORD_REF_SYSTEM view:

1.  If the unit of measurement is not already defined in the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table), insert a row into that table to define the new unit of measurement.
2.  If the coordinate axes are not already defined in the SDO_COORD_AXES table (described in SDO_COORD_AXES Table), insert one row into that table for each new coordinate axis.
3.  If an appropriate entry for the coordinate system does not already exist in the SDO_COORD_SYS table (described in SDO_COORD_SYS Table), insert a row into that table. Example 6-6 inserts the definition for a fictitious coordinate system.
4.  If the ellipsoid is not already defined in the SDO_ELLIPSOIDS table (described in SDO_ELLIPSOIDS Table), insert a row into that table to define the new ellipsoid.
5.  If the prime meridian is not already defined in the SDO_PRIME_MERIDIANS table (described in SDO_PRIME_MERIDIANS Table), insert a row into that table to define the new prime meridian.
6.  If the datum is not already defined in the SDO_DATUMS table (described in SDO_DATUMS Table), insert a row into that table to define the new datum.

Example 6-5 Creating a User-Defined Geodetic Coordinate Reference System

    INSERT INTO SDO_COORD_REF_SYSTEM (
            SRID,
            COORD_REF_SYS_NAME,
            COORD_REF_SYS_KIND,
            COORD_SYS_ID,
            DATUM_ID,
            GEOG_CRS_DATUM_ID,
            SOURCE_GEOG_SRID,
            PROJECTION_CONV_ID,
            CMPD_HORIZ_SRID,
            CMPD_VERT_SRID,
            INFORMATION_SOURCE,
            DATA_SOURCE,
            IS_LEGACY,
            LEGACY_CODE,
            LEGACY_WKTEXT,
            LEGACY_CS_BOUNDS,
            IS_VALID,
            SUPPORTS_SDO_GEOMETRY)
      VALUES (
            9994267,
            'My Own NAD27',
            'GEOGRAPHIC2D',
            6422,
            6267,
            6267,
            NULL,
            NULL,
            NULL,
            NULL,
            NULL,
            'EPSG',
            'FALSE',
            NULL,
            NULL,
            NULL,
            'TRUE',
            'TRUE');

Example 6-6 Inserting a Row into the SDO_COORD_SYS Table

    INSERT INTO SDO_COORD_SYS (
            COORD_SYS_ID,
            COORD_SYS_NAME,
            COORD_SYS_TYPE,
            DIMENSION,
            INFORMATION_SOURCE,
            DATA_SOURCE)
      VALUES (
            9876543,
            'My custom CS. Axes: lat, long. Orientations: north, east. UoM: deg',
            'ellipsoidal',
            2,
            'Myself',
            'Myself');

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.2 Creating a Projected CRS

If the necessary unit of measurement, coordinate axes, SDO_COORD_SYS table row, source coordinate system, projection operation, and projection parameters are already defined, insert a row into the SDO_COORD_REF_SYSTEM view (described in SDO_COORD_REF_SYSTEM View) to define the new projected CRS.

Example 6-7 inserts the definition for a hypothetical projected CRS named `My Own NAD27 / Cuba Norte` (which, except for its SRID and name, is the same as the `NAD27 / Cuba Norte` CRS supplied by Oracle).

If the necessary information for the definition does not already exist, follow these steps, as needed, to define the information before you insert the row into the SDO_COORD_REF_SYSTEM view:

1.  If the unit of measurement is not already defined in the SDO_UNITS_OF_MEASURE table (described in SDO_UNITS_OF_MEASURE Table), insert a row into that table to define the new unit of measurement.
2.  If the coordinate axes are not already defined in the SDO_COORD_AXES table (described in SDO_COORD_AXES Table), insert one row into that table for each new coordinate axis.
3.  If an appropriate entry for the coordinate system does not already exist in SDO_COORD_SYS table (described in SDO_COORD_SYS Table), insert a row into that table. (See Example 6-6 in Creating a Geodetic CRS).
4.  If the projection operation is not already defined in the SDO_COORD_OPS table (described in SDO_COORD_OPS Table), insert a row into that table to define the new projection operation. Example 6-8 shows the statement used to insert information about coordinate operation ID 18061, which is supplied by Oracle.
5.  If the parameters for the projection operation are not already defined in the SDO_COORD_OP_PARAM_VALS table (described in SDO_COORD_OP_PARAM_VALS Table), insert one row into that table for each new parameter. Example 6-9 shows the statement used to insert information about parameters with ID values 8801, 8802, 8805, 8806, and 8807, which are supplied by Oracle.

Example 6-7 Creating a User-Defined Projected Coordinate Reference System

    INSERT INTO SDO_COORD_REF_SYSTEM (
            SRID,
            COORD_REF_SYS_NAME,
            COORD_REF_SYS_KIND,
            COORD_SYS_ID,
            DATUM_ID,
            GEOG_CRS_DATUM_ID,
            SOURCE_GEOG_SRID,
            PROJECTION_CONV_ID,
            CMPD_HORIZ_SRID,
            CMPD_VERT_SRID,
            INFORMATION_SOURCE,
            DATA_SOURCE,
            IS_LEGACY,
            LEGACY_CODE,
            LEGACY_WKTEXT,
            LEGACY_CS_BOUNDS,
            IS_VALID,
            SUPPORTS_SDO_GEOMETRY)
      VALUES (
            9992085,
            'My Own NAD27 / Cuba Norte',
            'PROJECTED',
            4532,
            NULL,
            6267,
            4267,
            18061,
            NULL,
            NULL,
            'Institut Cubano di Hidrografia (ICH)',
            'EPSG',
            'FALSE',
            NULL,
            NULL,
            NULL,
            'TRUE',
            'TRUE');

Example 6-8 Inserting a Row into the SDO_COORD_OPS Table

    INSERT INTO SDO_COORD_OPS (
            COORD_OP_ID,
            COORD_OP_NAME,
            COORD_OP_TYPE,
            SOURCE_SRID,
            TARGET_SRID,
            COORD_TFM_VERSION,
            COORD_OP_VARIANT,
            COORD_OP_METHOD_ID,
            UOM_ID_SOURCE_OFFSETS,
            UOM_ID_TARGET_OFFSETS,
            INFORMATION_SOURCE,
            DATA_SOURCE,
            SHOW_OPERATION,
            IS_LEGACY,
            LEGACY_CODE,
            REVERSE_OP,
            IS_IMPLEMENTED_FORWARD,
            IS_IMPLEMENTED_REVERSE)
      VALUES (
            18061,
            'Cuba Norte',
            'CONVERSION',
            NULL,
            NULL,
            NULL,
            NULL,
            9801,
            NULL,
            NULL,
            NULL,
            'EPSG',
            1,
            'FALSE',
            NULL,
            1,
            1,
            1);

Example 6-9 Inserting a Row into the SDO_COORD_OP_PARAM_VALS Table

    INSERT INTO SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
      VALUES (
            18061,
            9801,
            8801,
            22.21,
            NULL,
            9110);

     INSERT INTO SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
      VALUES (
            18061,
            9801,
            8802,
            -81,
            NULL,
            9110);

     INSERT INTO SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
      VALUES (
            18061,
            9801,
            8805,
            .99993602,
            NULL,
            9201);

    INSERT INTO SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
      VALUES (
            18061,
            9801,
            8806,
            500000,
            NULL,
            9001);

    INSERT INTO SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
      VALUES (
            18061,
            9801,
            8807,
            280296.016,
            NULL,
            9001);

Example 6-10 Creating a User-Defined Projected CRS: Extended Example

    -- Create an EPSG equivalent for the following CRS:
    --
    -- CS_NAME:    VDOT_LAMBERT
    -- SRID:       51000000
    -- AUTH_SRID:  51000000
    -- AUTH_NAME:  VDOT Custom Lambert Conformal Conic
    -- WKTEXT:
    --
    -- PROJCS[
    --   "VDOT_Lambert",
    --   GEOGCS[
    --     "GCS_North_American_1983",
    --     DATUM[
    --       "D_North_American_1983",
    --       SPHEROID["GRS_1980", 6378137.0, 298.257222101]],
    --     PRIMEM["Greenwich", 0.0],
    --     UNIT["Decimal Degree",0.0174532925199433]],
    --   PROJECTION["Lambert_Conformal_Conic"],
    --   PARAMETER["False_Easting", 0.0],
    --   PARAMETER["False_Northing", 0.0],
    --   PARAMETER["Central_Meridian", -79.5],
    --   PARAMETER["Standard_Parallel_1", 37.0],
    --   PARAMETER["Standard_Parallel_2", 39.5],
    --   PARAMETER["Scale_Factor", 1.0],
    --   PARAMETER["Latitude_Of_Origin", 36.0],
    --   UNIT["Meter", 1.0]]

    -- First, the base geographic CRS (GCS_North_American_1983) already exists in EPSG.
    -- It is 4269:
    -- Next, find the EPSG equivalent for PROJECTION["Lambert_Conformal_Conic"]:
    select
      coord_op_method_id,
      legacy_name
    from
      sdo_coord_op_methods
    where
      not legacy_name is null
    order by
      coord_op_method_id;

    -- Result:
    -- COORD_OP_METHOD_ID LEGACY_NAME
    -- ------------------ --------------------------------------------------
    --               9802 Lambert Conformal Conic
    --               9803 Lambert Conformal Conic (Belgium 1972)
    --               9805 Mercator
    --               9806 Cassini
    --               9807 Transverse Mercator
    --               9829 Polar Stereographic
    --
    -- 6 rows selected.
    --
    -- It is EPSG method 9802. Create a projection operation 510000001, based on it:

    insert into MDSYS.SDO_COORD_OPS (
            COORD_OP_ID,
            COORD_OP_NAME,
            COORD_OP_TYPE,
            SOURCE_SRID,
            TARGET_SRID,
            COORD_TFM_VERSION,
            COORD_OP_VARIANT,
            COORD_OP_METHOD_ID,
            UOM_ID_SOURCE_OFFSETS,
            UOM_ID_TARGET_OFFSETS,
            INFORMATION_SOURCE,
            DATA_SOURCE,
            SHOW_OPERATION,
            IS_LEGACY,
            LEGACY_CODE,
            REVERSE_OP,
            IS_IMPLEMENTED_FORWARD,
            IS_IMPLEMENTED_REVERSE)
    VALUES (
            510000001,
            'VDOT_Lambert',
            'CONVERSION',
            NULL,
            NULL,
            NULL,
            NULL,
            9802,
            NULL,
            NULL,
            NULL,
            NULL,
            1,
            'FALSE',
            NULL,
            1,
            1,
            1);

    -- Now, set the parameters. See which are required:

    select
      use.parameter_id || ': ' ||
      use.legacy_param_name
    from
      sdo_coord_op_param_use use
    where
      use.coord_op_method_id = 9802;

    -- result:
    -- 8821: Latitude_Of_Origin
    -- 8822: Central_Meridian
    -- 8823: Standard_Parallel_1
    -- 8824: Standard_Parallel_2
    -- 8826: False_Easting
    -- 8827: False_Northing
    --
    -- 6 rows selected.

    -- Also check the most common units we will need:

    select
      UOM_ID || ': ' ||
      UNIT_OF_MEAS_NAME
    from
      sdo_units_of_measure
    where
      uom_id in (9001, 9101, 9102, 9201)
    order by
      uom_id;

    -- result:
    -- 9001: metre
    -- 9101: radian
    -- 9102: degree
    -- 9201: unity

    -- Now, configure the projection parameters:

    -- 8821: Latitude_Of_Origin

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8821,
            36.0,
            NULL,
            9102);

    -- 8822: Central_Meridian

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8822,
            -79.5,
            NULL,
            9102);

    -- 8823: Standard_Parallel_1

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8823,
            37.0,
            NULL,
            9102);

    -- 8824: Standard_Parallel_2

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8824,
            39.5,
            NULL,
            9102);

    -- 8826: False_Easting

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8826,
            0.0,
            NULL,
            9001);

    -- 8827: False_Northing

        insert into MDSYS.SDO_COORD_OP_PARAM_VALS (
            COORD_OP_ID,
            COORD_OP_METHOD_ID,
            PARAMETER_ID,
            PARAMETER_VALUE,
            PARAM_VALUE_FILE_REF,
            UOM_ID)
          VALUES (
            510000001,
            9802,
            8827,
            0.0,
            NULL,
            9001);

    -- Now, create the actual projected CRS.Look at the GEOG_CRS_DATUM_ID
    -- and COORD_SYS_ID first. The GEOG_CRS_DATUM_ID is the datum of
    -- the base geog_crs (4269):

    select datum_id from sdo_coord_ref_sys where srid = 4269;

    --   DATUM_ID
    -- ----------
    --       6269

    -- And the COORD_SYS_ID is the Cartesian CS used for the projected CRS.
    -- We can use 4400, if meters will be the unit:

    select COORD_SYS_NAME from sdo_coord_sys where COORD_SYS_ID = 4400;

    -- Cartesian 2D CS. Axes: easting, northing (E,N). Orientations: east, north.
    -- UoM: m.

    -- Now create the projected CRS:

    insert into MDSYS.SDO_COORD_REF_SYSTEM (
            SRID,
            COORD_REF_SYS_NAME,
            COORD_REF_SYS_KIND,
            COORD_SYS_ID,
            DATUM_ID,
            SOURCE_GEOG_SRID,
            PROJECTION_CONV_ID,
            CMPD_HORIZ_SRID,
            CMPD_VERT_SRID,
            INFORMATION_SOURCE,
            DATA_SOURCE,
            IS_LEGACY,
            LEGACY_CODE,
            LEGACY_WKTEXT,
            LEGACY_CS_BOUNDS,
            GEOG_CRS_DATUM_ID)
    VALUES (
            51000000,
            'VDOT_LAMBERT',
            'PROJECTED',
            4400,
            NULL,
            4269,
            510000001,
            NULL,
            NULL,
            NULL,
            NULL,
            'FALSE',
            NULL,
            NULL,
            NULL,
            6269);

    -- To see the result:

    select srid, wktext from cs_srs where srid = 51000000;

    --  51000000
    -- PROJCS[
    --   "VDOT_LAMBERT",
    --   GEOGCS [
    --     "NAD83",
    --     DATUM [
    --       "North American Datum 1983 (EPSG ID 6269)",
    --       SPHEROID [
    --         "GRS 1980 (EPSG ID 7019)",
    --         6378137,
    --         298.257222101]],
    --     PRIMEM [ "Greenwich", 0.000000 ],
    --     UNIT ["Decimal Degree", 0.01745329251994328]],
    --   PROJECTION ["VDOT_Lambert"],
    --   PARAMETER ["Latitude_Of_Origin", 36],
    --   PARAMETER ["Central_Meridian", -79.50000000000000000000000000000000000028],
    --   PARAMETER ["Standard_Parallel_1", 37],
    --   PARAMETER ["Standard_Parallel_2", 39.5],
    --   PARAMETER ["False_Easting", 0],
    --   PARAMETER ["False_Northing", 0],
    --   UNIT ["Meter", 1]]

Example 6-10 provides an extended, annotated example of creating a user-defined projected coordinate system

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.3 Creating a Vertical CRS

A vertical CRS has only one dimension, usually height. On its own, a vertical CRS is of little use, but it can be combined with a two-dimensional CRS (geodetic or projected), to result in a compound CRS. Example 6-11 shows the statement that created the vertical CRS with SRID 5701, which is included with Spatial and Graph. This definition refers to an existing (one-dimensional) coordinate system (ID 6499; see SDO_COORD_SYS Table) and vertical datum (ID 5101; see SDO_DATUMS Table).

Example 6-11 Creating a Vertical Coordinate Reference System

    INSERT INTO MDSYS.SDO_COORD_REF_SYSTEM (
        SRID,
        COORD_REF_SYS_NAME,
        COORD_REF_SYS_KIND,
        COORD_SYS_ID,
        DATUM_ID,
        SOURCE_GEOG_SRID,
        PROJECTION_CONV_ID,
        CMPD_HORIZ_SRID,
        CMPD_VERT_SRID,
        INFORMATION_SOURCE,
        DATA_SOURCE,
        IS_LEGACY,
        LEGACY_CODE,
        LEGACY_WKTEXT,
        LEGACY_CS_BOUNDS)
      VALUES (
        5701,
        'Newlyn',
        'VERTICAL',
        6499,
        5101,
        NULL,
        NULL,
        NULL,
        NULL,
        NULL,
        'EPSG',
        'FALSE',
        NULL,
        NULL,
        NULL);

A vertical CRS might define some undulating equipotential surface. The shape of that surface, and its offset from some ellipsoid, is not actually defined in the vertical CRS record itself (other than textually). Instead, that definition is included in an operation between the vertical CRS and another CRS. Consequently, you can define several alternative operations between the same pair of geoidal and WGS 84-ellipsoidal heights. For example, there are geoid offset matrixes GEOID90, GEOID93, GEOID96, GEOID99, GEOID03, GEOID06, and others, and for each of these variants there can be a separate operation. Creating a Transformation Operation describes such an operation.

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.4 Creating a Compound CRS

A compound CRS combines an existing horizontal (two-dimensional) CRS and a vertical (one-dimensional) CRS. The horizontal CRS can be geodetic or projected. Example 6-12 shows the statement that created the compound CRS with SRID 7405, which is included with Spatial and Graph. This definition refers to an existing projected CRS and vertical CRS (IDs 27700 and 5701, respectively; see SDO_COORD_REF_SYS Table).

Example 6-12 Creating a Compound Coordinate Reference System

    INSERT INTO MDSYS.SDO_COORD_REF_SYSTEM (
        SRID,
        COORD_REF_SYS_NAME,
        COORD_REF_SYS_KIND,
        COORD_SYS_ID,
        DATUM_ID,
        SOURCE_GEOG_SRID,
        PROJECTION_CONV_ID,
        CMPD_HORIZ_SRID,
        CMPD_VERT_SRID,
        INFORMATION_SOURCE,
        DATA_SOURCE,
        IS_LEGACY,
        LEGACY_CODE,
        LEGACY_WKTEXT,
        LEGACY_CS_BOUNDS)
      VALUES (
        7405,
        'OSGB36 / British National Grid + ODN',
        'COMPOUND',
        NULL,
        NULL,
        NULL,
        NULL,
        27700,
        5701,
        NULL,
        'EPSG',
        'FALSE',
        NULL,
        NULL,
        NULL);

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.5 Creating a Geographic 3D CRS

A geographic 3D CRS is the combination of a geographic 2D CRS with ellipsoidal height.

**Note:**

Creating a 3D CRS is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

Example 6-13 shows the statement that created the geographic 3D CRS with SRID 4327, which is included with Spatial and Graph. This definition refers to an existing projected coordinate system (ID 6401; see SDO_COORD_SYS Table) and datum (ID 6326; see SDO_DATUMS Table).

Example 6-13 Creating a Geographic 3D Coordinate Reference System

    INSERT INTO MDSYS.SDO_COORD_REF_SYSTEM (
       SRID,
       COORD_REF_SYS_NAME,
       COORD_REF_SYS_KIND,
       COORD_SYS_ID,
       DATUM_ID,
       GEOG_CRS_DATUM_ID,
       SOURCE_GEOG_SRID,
       PROJECTION_CONV_ID,
       CMPD_HORIZ_SRID,
       CMPD_VERT_SRID,
       INFORMATION_SOURCE,
       DATA_SOURCE,
       IS_LEGACY,
       LEGACY_CODE,
       LEGACY_WKTEXT,
       LEGACY_CS_BOUNDS,
       IS_VALID,
       SUPPORTS_SDO_GEOMETRY)
     VALUES (
       4327,
       'WGS 84 (geographic 3D)',
       'GEOGRAPHIC3D',
       6401,
       6326,
       6326,
       NULL,
       NULL,
       NULL,
       NULL,
       'NIMA TR8350.2 January 2000 revision. http://164.214.2.59/GandG/tr8350_2.html',
       'EPSG',
       'FALSE',
       NULL,
       NULL,
       NULL,
       'TRUE',
       'TRUE');

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.6 Creating a Transformation Operation

Creating a Projected CRS described the creation of a projection operation, for the purpose of then creating a projected CRS. A similar requirement can arise when using a compound CRS based on orthometric height: you may want to transform from and to ellipsoidal height. The offset between the two heights is undulating and irregular.

By default, Spatial and Graph transforms between ellipsoidal and orthometric height using an identity transformation. (Between different ellipsoids, the default would instead be a datum transformation.) The identity transformation is a reasonable approximation; however, a more accurate approach involves an EPSG type 9635 operation, involving an offset matrix. Example 6-14 is a declaration of such an operation:

Example 6-14 Creating a Transformation Operation

    INSERT INTO MDSYS.SDO_COORD_OPS (
       COORD_OP_ID,
       COORD_OP_NAME,
       COORD_OP_TYPE,
       SOURCE_SRID,
       TARGET_SRID,
       COORD_TFM_VERSION,
       COORD_OP_VARIANT,
       COORD_OP_METHOD_ID,
       UOM_ID_SOURCE_OFFSETS,
       UOM_ID_TARGET_OFFSETS,
       INFORMATION_SOURCE,
       DATA_SOURCE,
       SHOW_OPERATION,
       IS_LEGACY,
       LEGACY_CODE,
       REVERSE_OP,
       IS_IMPLEMENTED_FORWARD,
       IS_IMPLEMENTED_REVERSE)
     VALUES (
       999998,
       'Test operation, based on GEOID03 model, using Hawaii grid',
       'TRANSFORMATION',
       NULL,
       NULL,
       NULL,
       NULL,
       9635,
       NULL,
       NULL,
       'NGS',
       'NGS',
       1,
       'FALSE',
       NULL,
       1,
       1,
       1);

    INSERT INTO MDSYS.SDO_COORD_OP_PARAM_VALS (
       COORD_OP_ID,
       COORD_OP_METHOD_ID,
       PARAMETER_ID,
       PARAMETER_VALUE,
       PARAM_VALUE_FILE_REF,
       UOM_ID)
     VALUES (
       999998,
       9635,
       8666,
       NULL,
       'g2003h01.asc',
       NULL);

The second INSERT statement in Example 6-14 specifies the file name `g2003h01.asc`, but not yet its actual CLOB content with the offset matrix. As with NADCON and NTv2 matrixes, geoid matrixes have to be loaded into the PARAM_VALUE_FILE column. Due to space and copyright considerations, Oracle does not supply most of these matrixes; however, they are usually available for download on the Web. Good sources are the relevant government websites, and you can search by file name (such as `g2003h01` in this example). Although some of these files are available in both binary format (such as .gsb) and ASCII format (such as .gsa or .asc), only the ASCII variant can be used with Spatial and Graph. The existing EPSG operations include file names in standard use.

Example 6-15 Loading Offset Matrixes

    DECLARE
      ORCL_HOME_DIR VARCHAR2(128);
      ORCL_WORK_DIR VARCHAR2(128);
      Src_loc       BFILE;
      Dest_loc      CLOB;
      CURSOR PARAM_FILES IS
        SELECT
          COORD_OP_ID,
          PARAMETER_ID,
          PARAM_VALUE_FILE_REF
        FROM
          MDSYS.SDO_COORD_OP_PARAM_VALS
        WHERE
          PARAMETER_ID IN (8656, 8657, 8658, 8666);
      PARAM_FILE PARAM_FILES%ROWTYPE;
      ACTUAL_FILE_NAME VARCHAR2(128);
      platform NUMBER;
      dest_offset  number := 1;
      src_offset   number := 1;
      lang_context number := 0;
      warning      number;
    BEGIN
      EXECUTE IMMEDIATE 'CREATE OR REPLACE DIRECTORY work_dir AS ''define_your_source_directory_here''';

      FOR PARAM_FILE IN PARAM_FILES LOOP
        CASE UPPER(PARAM_FILE.PARAM_VALUE_FILE_REF)
          /* NTv2, fill in your files here */
          WHEN 'NTV2_0.GSB'   THEN ACTUAL_FILE_NAME := 'ntv20.gsa';
          /* GEOID03, fill in your files here */
          WHEN 'G2003H01.ASC' THEN ACTUAL_FILE_NAME := 'g2003h01.asc';
          ELSE                     ACTUAL_FILE_NAME := NULL;
        END CASE;

        IF(NOT (ACTUAL_FILE_NAME IS NULL)) THEN
          BEGIN
            dbms_output.put_line('Loading file ' || actual_file_name || '...');
            Src_loc := BFILENAME('WORK_DIR', ACTUAL_FILE_NAME);
            DBMS_LOB.OPEN(Src_loc, DBMS_LOB.LOB_READONLY);
          END;

          UPDATE
            MDSYS.SDO_COORD_OP_PARAM_VALS
          SET
            PARAM_VALUE_FILE = EMPTY_CLOB()
          WHERE
            COORD_OP_ID = PARAM_FILE.COORD_OP_ID AND
            PARAMETER_ID = PARAM_FILE.PARAMETER_ID
          RETURNING
            PARAM_VALUE_FILE INTO Dest_loc;

          DBMS_LOB.OPEN(Dest_loc, DBMS_LOB.LOB_READWRITE);

          -- DBMS_LOB.LOADFROMFILE(Dest_loc, Src_loc, DBMS_LOB.LOBMAXSIZE);
          dbms_lob.loadclobfromfile (
             dest_lob     => dest_loc,
             src_bfile    => src_loc,
             amount       => DBMS_LOB.LOBMAXSIZE,
             dest_offset  => dest_offset,
             src_offset   => src_offset,
             bfile_csid   => 0,
             lang_context => lang_context,
             warning      => warning);

          DBMS_LOB.CLOSE(Dest_loc);
          DBMS_LOB.CLOSE(Src_loc);
          DBMS_LOB.FILECLOSE(Src_loc);
        END IF;
      END LOOP;
    END;
    /

Example 6-15 is a script for loading a set of such matrixes. It loads specified physical files (such as `ntv20.gsa`) into database CLOBs, based on the official file name reference (such as `NTV2_0.GSB`).

**Parent topic:** Creating a User-Defined Coordinate Reference System

#### 6.9.7 Using British Grid Transformation OSTN02/OSGM02 (EPSG Method 9633)

To use British Grid Transformation OSTN02/OSGM02 (EPSG method 9633) in a projected coordinate reference system, you must first insert a modified version of the `OSTN02_OSGM02_GB.txt` grid file into the PARAM_VALUE_FILE column (type CLOB) of the SDO_COORD_OP_PARAM_VALS table (described in SDO_COORD_OP_PARAM_VALS Table). The `OSTN02_OSGM02_GB.txt` file contains the offset matrix on which EPSG transformation method 9633 is based.

Follow these steps:

1.  Download the following file: [`http://www.ordnancesurvey.co.uk/docs/gps/ostn02-osgm02-files.zip`](http://www.ordnancesurvey.co.uk/docs/gps/ostn02-osgm02-files.zip)
2.  From this .zip file, extract the following file: `OSTN02_OSGM02_GB.txt`
3.  Edit your copy of `OSTN02_OSGM02_GB.txt`, and insert the following lines before the first line of the current file:
        SDO Header
        x: 0.0 - 700000.0
        y: 0.0 - 1250000.0
        x-intervals: 1000.0
        y-intervals: 1000.0
        End of SDO Header

    The is, after the editing operation, the contents of the file will look like this:

        SDO Header
        x: 0.0 - 700000.0
        y: 0.0 - 1250000.0
        x-intervals: 1000.0
        y-intervals: 1000.0
        End of SDO Header
        1,0,0,0.000,0.000,0.000,0
        2,1000,0,0.000,0.000,0.000,0
        3,2000,0,0.000,0.000,0.000,0
        4,3000,0,0.000,0.000,0.000,0
        5,4000,0,0.000,0.000,0.000,0
        . . .
        876949,698000,1250000,0.000,0.000,0.000,0
        876950,699000,1250000,0.000,0.000,0.000,0
        876951,700000,1250000,0.000,0.000,0.000,0
4.  Save the edited file, perhaps using a different name (for example, `my_OSTN02_OSGM02_GB.txt`).
5.  In the SDO_COORD_OP_PARAM_VALS table, for each operation of EPSG method 9633 that has PARAM_VALUE_FILE_REF value `OSTN02_OSGM02_GB.TXT`, update the PARAM_VALUE_FILE column to be the contents of the saved file (for example, the contents of `my_OSTN02_OSGM02_GB.txt`). You can use coding similar to that in Example 6-16.

Example 6-16 Using British Grid Transformation OSTN02/OSGM02 (EPSG Method 9633)

    DECLARE
      ORCL_HOME_DIR VARCHAR2(128);
      ORCL_WORK_DIR VARCHAR2(128);
      Src_loc       BFILE;
      Dest_loc      CLOB;
      CURSOR PARAM_FILES IS
        SELECT
          COORD_OP_ID,
          PARAMETER_ID,
          PARAM_VALUE_FILE_REF
        FROM
          MDSYS.SDO_COORD_OP_PARAM_VALS
        WHERE
          PARAMETER_ID IN (8656, 8657, 8658, 8664, 8666)
        order by
          COORD_OP_ID,
          PARAMETER_ID;
      PARAM_FILE PARAM_FILES%ROWTYPE;
      ACTUAL_FILE_NAME VARCHAR2(128);
      platform NUMBER;
    BEGIN
      EXECUTE IMMEDIATE 'CREATE OR REPLACE DIRECTORY work_dir AS ''' || system.geor_dir || '''';

      FOR PARAM_FILE IN PARAM_FILES LOOP
        CASE UPPER(PARAM_FILE.PARAM_VALUE_FILE_REF)
          /* NTv2 */
          WHEN 'NTV2_0.GSB'   THEN ACTUAL_FILE_NAME := 'ntv20.gsa';
          /* GEOID03 */
          WHEN 'G2003H01.ASC' THEN ACTUAL_FILE_NAME := 'g2003h01.asc';
          /* British Ordnance Survey (9633) */
          WHEN 'OSTN02_OSGM02_GB.TXT'
                              THEN ACTUAL_FILE_NAME := 'my_OSTN02_OSGM02_GB.txt';
          ELSE                ACTUAL_FILE_NAME := NULL;
        END CASE;

        IF(NOT (ACTUAL_FILE_NAME IS NULL)) THEN
          BEGIN
            dbms_output.put_line('Loading file ' || actual_file_name || '...');
            Src_loc := BFILENAME('WORK_DIR', ACTUAL_FILE_NAME);
            DBMS_LOB.OPEN(Src_loc, DBMS_LOB.LOB_READONLY);
          END;

          UPDATE
            MDSYS.SDO_COORD_OP_PARAM_VALS
          SET
            PARAM_VALUE_FILE = EMPTY_CLOB()
          WHERE
            COORD_OP_ID = PARAM_FILE.COORD_OP_ID AND
            PARAMETER_ID = PARAM_FILE.PARAMETER_ID
          RETURNING
            PARAM_VALUE_FILE INTO Dest_loc;

          DBMS_LOB.OPEN(Dest_loc, DBMS_LOB.LOB_READWRITE);
          DBMS_LOB.LOADFROMFILE(Dest_loc, Src_loc, DBMS_LOB.LOBMAXSIZE);
          DBMS_LOB.CLOSE(Dest_loc);
          DBMS_LOB.CLOSE(Src_loc);
          DBMS_LOB.FILECLOSE(Src_loc);
        END IF;
      END LOOP;
    END;
    /

Note that adding "header" information to a grid file is required only for British Grid Transformation OSTN02/OSGM02. It is not required for NADCON, NTv2, or VERTCON matrixes, because they already have headers of varying formats.

See also the following for related information:

- Creating a Projected CRS

- Creating a Transformation Operation

**Parent topic:** Creating a User-Defined Coordinate Reference System

### 6.10 Notes and Restrictions with Coordinate Systems Support

The following notes and restrictions apply to coordinate systems support in the current release of Oracle Spatial and Graph.

If you have geodetic data, see Geodetic Coordinate Support for additional considerations, guidelines, and restrictions.

- Different Coordinate Systems for Geometries with Operators and Functions
- 3D LRS Functions Not Supported with Geodetic Data
- Functions Supported by Approximations with Geodetic Data
- Unknown CRS and NaC Coordinate Reference Systems

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

#### 6.10.1 Different Coordinate Systems for Geometries with Operators and Functions

For spatial operators (described in [Spatial Operators](spatial-operators-reference.md) ) that take two geometries as input parameters, if the geometries are based on different coordinate systems, the query window (the second geometry) is transformed to the coordinate system of the first geometry before the operation is performed. This transformation is a temporary internal operation performed by Spatial and Graph; it does not affect any stored query-window geometry.

For SDO_GEOM package geometry functions (described in [SDO_GEOM Package (Geometry)](SDO_GEOM-reference.md)) that take two geometries as input parameters, both geometries must be based on the same coordinate system.

**Parent topic:** Notes and Restrictions with Coordinate Systems Support

#### 6.10.2 3D LRS Functions Not Supported with Geodetic Data

In the current release, the 3D formats of LRS functions (explained in [3D Formats of LRS Functions](lrs-linear-referencing-system-concepts.md)) are not supported with geodetic data.

**Parent topic:** Notes and Restrictions with Coordinate Systems Support

#### 6.10.3 Functions Supported by Approximations with Geodetic Data

In the current release, the following functions are supported by approximations with geodetic data:

- [SDO_GEOM.SDO_BUFFER](SDO_GEOM-reference.md)

- [SDO_GEOM.SDO_CENTROID](SDO_GEOM-reference.md)

- [SDO_GEOM.SDO_CONVEXHULL](SDO_GEOM-reference.md)

When these functions are used on data with geodetic coordinates, they internally perform the operations in an implicitly generated local-tangent-plane Cartesian coordinate system and then transform the results to the geodetic coordinate system. For [SDO_GEOM.SDO_BUFFER](SDO_GEOM-reference.md), generated arcs are approximated by line segments before the back-transform.

**Parent topic:** Notes and Restrictions with Coordinate Systems Support

#### 6.10.4 Unknown CRS and NaC Coordinate Reference Systems

The following coordinate reference systems are provided for Oracle internal use and for other possible special uses:

- `unknown CRS` (SRID 999999) means that the coordinate system is unknown, and its space could be geodetic or Cartesian. Contrast this with specifying a null coordinate reference system, which indicates an unknown coordinate system with a Cartesian space.

- `NaC` (SRID 999998) means Not-a-CRS. Its name is patterned after the `NaN` (Not-a-Number) value in Java. It is intended for potential use with nonspatial geometries.

The following restrictions apply to geometries based on the `unknown CRS` and `NaC` coordinate reference systems:

- You cannot perform coordinate system transformations on these geometries.

- Operations that require a coordinate system will return a null value when performed on these geometries. These operations include finding the area or perimeter of a geometry, creating a buffer, densifying an arc, and computing the aggregate centroid.

**Parent topic:** Notes and Restrictions with Coordinate Systems Support

### 6.11 U.S. National Grid Support

The U.S. National Grid is a point coordinate representation using a single alphanumeric coordinate (for example, 18SUJ2348316806479498).

This approach contrasts with the use of numeric coordinates to represent the location of a point, as is done with Oracle Spatial and Graph and with EPSG. A good description of the U.S. National Grid is available at [`http://www.ngs.noaa.gov/TOOLS/usng.html`](http://www.ngs.noaa.gov/TOOLS/usng.html).

To support the U.S. National Grid in Spatial and Graph, the SDO_GEOMETRY type cannot be used because it is based on numeric coordinates. Instead, a point in U.S. National Grid format is represented as a single string of type VARCHAR2. To allow conversion between the SDO_GEOMETRY format and the U.S. National grid format, the SDO_CS package (documented in [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md)) contains the following functions:

- [SDO_CS.FROM_USNG](SDO_CS-reference.md)

- [SDO_CS.TO_USNG](SDO_CS-reference.md)

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.12 Geohash Support

A geohash is a standard String encoding of a longitude/latitude point.

Some third-party software without advanced geospatial capabilities may be compatible with geohashes, since they support some types of simple, limited analysis of geographic data. For example, the approximate distance between objects can be guessed, based on the length of common prefix of the geohashes.

For more information about geohash, see [`https://en.wikipedia.org/wiki/Geohash`](https://en.wikipedia.org/wiki/Geohash).

To support geohashes, the SDO_GEOMETRY type cannot be used directly. Instead, you can use the SDO_CS package (documented in [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md) ) to convert between SDO_GEOMETRY and gaohash format, and to perform other geohash-related operations. That package contains the following subprograms related to geohash support:

- [SDO_CS.FROM_GEOHASH](SDO_CS-reference.md)

- [SDO_CS.GET_GEOHASH_CELL_HEIGHT](SDO_CS-reference.md)

- [SDO_CS.GET_GEOHASH_CELL_WIDTH](SDO_CS-reference.md)

- [SDO_CS.TO_GEOHASH](SDO_CS-reference.md)

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.13 Google Maps Considerations

Google Maps uses spherical math in its projections, as opposed to the ellipsoidal math used by Oracle Spatial and Graph. This difference can lead to inconsistencies in applications, such as when overlaying a map based on Google Maps with a map based on an Oracle Spatial and Graph ellipsoidal projection.

For example, an Oracle Spatial and Graph transformation from the ellipsoidal SRID 8307 to the spherical SRID 3785 accounts, by default, for the different ellipsoidal shapes, whereas Google Maps does not consider ellipsoidal shapes.

If you want Oracle Spatial and Graph to accommodate the Google Maps results, consider the following options:

- Use the spherical SRID 4055 instead of the ellipsoidal SRID 8307. This may be the simplest approach; however, if you need to accommodate SRID 8307-based data (such as from a third-party tool) as if it were spherical, you must use another option.

- Use SRID 3857 instead of SRID 3785. This more convenient than the next two options, because using SRID 3857 does not require that you declare an EPSG rule or that you specify the `USE_SPHERICAL` use case name in order to produce Google-compatible results.

- Declare an EPSG rule between the ellipsoidal and spherical coordinate systems. For example, declare an EPSG rule between SRIDs 8307 and 3785, ignoring the ellipsoidal shape of SRID 8307, as in the following example:

      CALL sdo_cs.create_pref_concatenated_op(
        302,
        'CONCATENATED OPERATION',
        TFM_PLAN(SDO_TFM_CHAIN(8307, 1000000000, 4055, 19847, 3785)),
        NULL);

  In this example, operation `1000000000` represents no-operation, causing the datum transformation between ellipsoid and sphere to be ignored.

  With this approach, you must declare a rule for each desired SRID pair (ellipsoidal and spherical).

- Specify a use case name of `USE_SPHERICAL` with the [SDO_CS.TRANSFORM](SDO_CS-reference.md) function or the [SDO_CS.TRANSFORM_LAYER](SDO_CS-reference.md) procedure, as in the following examples:

      SELECT
        SDO_CS.TRANSFORM(
          sdo_geometry(
            2001,
            4326,
            sdo_point_type(1, 1, null),
            null,
            null),
          'USE_SPHERICAL',
          3785)
      FROM DUAL;

      CALL SDO_CS.TRANSFORM_LAYER(
        'source_geoms',
        'GEOMETRY',
        'GEO_CS_3785_SPHERICAL',
        'USE_SPHERICAL',
        3785);

  If you specify a `use_case` parameter value of `USE_SPHERICAL` in such cases, the transformation defaults to using spherical math instead of ellipsoidal math, thereby accommodating Google Maps and some other third-party tools that use spherical math.

  If you use this approach (specifying `'USE_SPHERICAL'`) but you have also declared an EPSG rule requiring that ellipsoidal math be used in transformations between two specified SRIDs, then the declared EPSG rule takes precedence and ellipsoidal math is used for transformations between those two SRIDs.

**Parent topic:** Coordinate Systems (Spatial Reference Systems)

### 6.14 Example of Coordinate System Transformation

This topic presents a simplified example that uses coordinate system transformation functions and procedures.

It refers to concepts that are explained in this chapter and uses functions documented in [SDO_CS Package (Coordinate System Transformation)](SDO_CS-reference.md) .

Example 6-17 Simplified Example of Coordinate System Transformation

Example 6-17 uses mostly the same geometry data (cola markets) as in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md), except that instead of null SDO_SRID values, the SDO_SRID value 8307 is used. That is, the geometries are defined as using the coordinate system whose SRID is 8307 and whose well-known name is "Longitude / Latitude (WGS 84)". This is probably the most widely used coordinate system, and it is the one used for global positioning system (GPS) devices. The geometries are then transformed using the coordinate system whose SRID is 8199 and whose well-known name is "Longitude / Latitude (Arc 1950)".

Example 6-17 uses the geometries illustrated in [Simple Example: Inserting\_ Indexing\_ and Querying Spatial Data](spatial-datatypes-metadata.md), except that `cola_d` is a rectangle (here, a square) instead of a circle, because arcs are not supported with geodetic coordinate systems.

Example 6-17 does the following:

- Creates a table (COLA_MARKETS_CS) to hold the spatial data

- Inserts rows for four areas of interest (`cola_a`, `cola_b`, `cola_c`, `cola_d`), using the SDO_SRID value 8307

- Updates the USER_SDO_GEOM_METADATA view to reflect the dimension of the areas, using the SDO_SRID value 8307

- Creates a spatial index (COLA_SPATIAL_IDX_CS)

- Performs some transformation operations (single geometry and entire layer)

<!-- -->

    -- Create a table for cola (soft drink) markets in a
    -- given geography (such as city or state).

    CREATE TABLE cola_markets_cs (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      shape SDO_GEOMETRY);

    -- The next INSERT statement creates an area of interest for
    -- Cola A. This area happens to be a rectangle.
    -- The area could represent any user-defined criterion: for
    -- example, where Cola A is the preferred drink, where
    -- Cola A is under competitive pressure, where Cola A
    -- has strong growth potential, and so on.

    INSERT INTO cola_markets_cs VALUES(
      1,
      'cola_a',
      SDO_GEOMETRY(
        2003,  -- two-dimensional polygon
        8307,  -- SRID for 'Longitude / Latitude (WGS 84)' coordinate system
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,1), -- polygon
        SDO_ORDINATE_ARRAY(1,1, 5,1, 5,7, 1,7, 1,1) -- All vertices must
                  -- be defined for rectangle with geodetic data.
      )
    );

    -- The next two INSERT statements create areas of interest for
    -- Cola B and Cola C. These areas are simple polygons (but not
    -- rectangles).

    INSERT INTO cola_markets_cs VALUES(
      2,
      'cola_b',
      SDO_GEOMETRY(
        2003,  -- two-dimensional polygon
        8307,
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,1), -- one polygon (exterior polygon ring)
        SDO_ORDINATE_ARRAY(5,1, 8,1, 8,6, 5,7, 5,1)
      )
    );

    INSERT INTO cola_markets_cs VALUES(
      3,
      'cola_c',
      SDO_GEOMETRY(
        2003,  -- two-dimensional polygon
        8307,
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,1), --one polygon (exterior polygon ring)
        SDO_ORDINATE_ARRAY(3,3, 6,3, 6,5, 4,5, 3,3)
      )
    );

    -- Insert a rectangle (here, square) instead of a circle as in the original,
    -- because arcs are not supported with geodetic coordinate systems.
    INSERT INTO cola_markets_cs VALUES(
      4,
      'cola_d',
      SDO_GEOMETRY(
        2003,  -- two-dimensional polygon
        8307,  -- SRID for 'Longitude / Latitude (WGS 84)' coordinate system
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,1), -- polygon
        SDO_ORDINATE_ARRAY(10,9, 11,9, 11,10, 10,10, 10,9) -- All vertices must
                  -- be defined for rectangle with geodetic data.
      )
    );

    ---------------------------------------------------------------------------
    -- UPDATE METADATA VIEW --
    ---------------------------------------------------------------------------
    -- Update the USER_SDO_GEOM_METADATA view. This is required
    -- before the spatial index can be created. Do this only once for each
    -- layer (table-column combination; here: cola_markets_cs and shape).

    INSERT INTO user_sdo_geom_metadata
        (TABLE_NAME,
         COLUMN_NAME,
         DIMINFO,
         SRID)
      VALUES (
      'cola_markets_cs',
      'shape',
      SDO_DIM_ARRAY(
        SDO_DIM_ELEMENT('Longitude', -180, 180, 10),  -- 10 meters tolerance
        SDO_DIM_ELEMENT('Latitude', -90, 90, 10)  -- 10 meters tolerance
         ),
      8307   -- SRID for 'Longitude / Latitude (WGS 84)' coordinate system
    );

    -------------------------------------------------------------------
    -- CREATE THE SPATIAL INDEX --
    -------------------------------------------------------------------
    CREATE INDEX cola_spatial_idx_cs
    ON cola_markets_cs(shape)
    INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2;

    -------------------------------------------------------------------
    -- TEST COORDINATE SYSTEM TRANSFORMATION --
    -------------------------------------------------------------------

    -- Return the transformation of cola_c using to_srid 8199
    -- ('Longitude / Latitude (Arc 1950)')
    SELECT c.name, SDO_CS.TRANSFORM(c.shape, 8199)
      FROM cola_markets_cs c WHERE c.name = 'cola_c';

    -- Same as preceding, but using to_srname parameter.
    SELECT c.name, SDO_CS.TRANSFORM(c.shape, 'Longitude / Latitude (Arc 1950)')
      FROM cola_markets_cs c  WHERE c.name = 'cola_c';

    -- Transform the entire SHAPE layer and put results in the table
    -- named cola_markets_cs_8199, which the procedure will create.
    CALL SDO_CS.TRANSFORM_LAYER('COLA_MARKETS_CS','SHAPE','COLA_MARKETS_CS_8199',8199);

    -- Select all from the old (existing) table.
    SELECT * from cola_markets_cs;

    -- Select all from the new (layer transformed) table.
    SELECT * from cola_markets_cs_8199;

    -- Show metadata for the new (layer transformed) table.
    DESCRIBE cola_markets_cs_8199;

    -- Use a geodetic MBR with SDO_FILTER.
    SELECT c.name FROM cola_markets_cs c WHERE
       SDO_FILTER(c.shape,
           SDO_GEOMETRY(
               2003,
               8307,    -- SRID for WGS 84 longitude/latitude
               NULL,
               SDO_ELEM_INFO_ARRAY(1,1003,3),
               SDO_ORDINATE_ARRAY(6,5, 10,10))
           ) = 'TRUE';

Example 6-18 shows the output of the SELECT statements in Example 6-17. Notice the slight differences between the coordinates in the original geometries (SRID 8307) and the transformed coordinates (SRID 8199) -- for example, (1, 1, 5, 1, 5, 7, 1, 7, 1, 1) and (1.00078604, 1.00274579, 5.00069354, 1.00274488, 5.0006986, 7.00323528, 1.00079179, 7.00324162, 1.00078604, 1.00274579) for `cola_a`.

Example 6-18 Output of SELECT Statements in Coordinate System Transformation Example

    SQL> -- Return the transformation of cola_c using to_srid 8199
    SQL> -- ('Longitude / Latitude (Arc 1950)')
    SQL> SELECT c.name, SDO_CS.TRANSFORM(c.shape, 8199)
      2    FROM cola_markets_cs c WHERE c.name = 'cola_c';

    NAME
    --------------------------------
    SDO_CS.TRANSFORM(C.SHAPE,8199)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM
    --------------------------------------------------------------------------------
    cola_c
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3.00074114, 3.00291482, 6.00067068, 3.00291287, 6.0006723, 5.00307625, 4.0007
    1961, 5.00307838, 3.00074114, 3.00291482))

    SQL>
    SQL> -- Same as preceding, but using to_srname parameter.
    SQL> SELECT c.name, SDO_CS.TRANSFORM(c.shape, 'Longitude / Latitude (Arc 1950)')
      2    FROM cola_markets_cs c  WHERE c.name = 'cola_c';

    NAME
    --------------------------------
    SDO_CS.TRANSFORM(C.SHAPE,'LONGITUDE/LATITUDE(ARC1950)')(SDO_GTYPE, SDO_SRID, SDO
    --------------------------------------------------------------------------------
    cola_c
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3.00074114, 3.00291482, 6.00067068, 3.00291287, 6.0006723, 5.00307625, 4.0007
    1961, 5.00307838, 3.00074114, 3.00291482))

    SQL>
    SQL> -- Transform the entire SHAPE layer and put results in the table
    SQL> -- named cola_markets_cs_8199, which the procedure will create.
    SQL> CALL SDO_CS.TRANSFORM_LAYER('COLA_MARKETS_CS','SHAPE','COLA_MARKETS_CS_8199',8199);

    Call completed.

    SQL>
    SQL> -- Select all from the old (existing) table.
    SQL> SELECT * from cola_markets_cs;

        MKT_ID NAME
    ---------- --------------------------------
    SHAPE(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
             1 cola_a
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(1, 1, 5, 1, 5, 7, 1, 7, 1, 1))

             2 cola_b
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(5, 1, 8, 1, 8, 6, 5, 7, 5, 1))

             3 cola_c

        MKT_ID NAME
    ---------- --------------------------------
    SHAPE(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3, 3, 6, 3, 6, 5, 4, 5, 3, 3))

             4 cola_d
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(10, 9, 11, 9, 11, 10, 10, 10, 10, 9))


    SQL>
    SQL> -- Select all from the new (layer transformed) table.
    SQL> SELECT * from cola_markets_cs_8199;

    SDO_ROWID
    ------------------
    GEOMETRY(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
    AAABZzAABAAAOa6AAA
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(1.00078604, 1.00274579, 5.00069354, 1.00274488, 5.0006986, 7.00323528, 1.0007
    9179, 7.00324162, 1.00078604, 1.00274579))

    AAABZzAABAAAOa6AAB
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(5.00069354, 1.00274488, 8.00062191, 1.00274427, 8.00062522, 6.00315345, 5.000
    6986, 7.00323528, 5.00069354, 1.00274488))

    SDO_ROWID
    ------------------
    GEOMETRY(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------

    AAABZzAABAAAOa6AAC
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3.00074114, 3.00291482, 6.00067068, 3.00291287, 6.0006723, 5.00307625, 4.0007
    1961, 5.00307838, 3.00074114, 3.00291482))

    AAABZzAABAAAOa6AAD
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(10.0005802, 9.00337775, 11.0005553, 9.00337621, 11.0005569, 10.0034478, 10.00

    SDO_ROWID
    ------------------
    GEOMETRY(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
    05819, 10.0034495, 10.0005802, 9.00337775))


    SQL>
    SQL> -- Show metadata for the new (layer transformed) table.
    SQL> DESCRIBE cola_markets_cs_8199;
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     SDO_ROWID                                          ROWID
     GEOMETRY                                           SDO_GEOMETRY

    SQL>
    SQL> -- Use a geodetic MBR with SDO_FILTER
    SQL> SELECT c.name FROM cola_markets_cs c WHERE
      2     SDO_FILTER(c.shape,
      3         SDO_GEOMETRY(
      4             2003,
      5             8307,    -- SRID for WGS 84 longitude/latitude
      6             NULL,
      7             SDO_ELEM_INFO_ARRAY(1,1003,3),
      8             SDO_ORDINATE_ARRAY(6,5, 10,10))
      9         ) = 'TRUE';

    NAME
    --------------------------------
    cola_c
    cola_b
    cola_d

**Parent topic:** Coordinate Systems (Spatial Reference Systems)
