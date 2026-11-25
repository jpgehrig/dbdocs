Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](J3D_Geometry.md)
- [Next Class](JGeometry.GeomParser.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.geometry

## Class JGeometry

- java.lang.Object

- - oracle.spatial.geometry.JGeometry

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, [RNode](RNode.md)

  <!-- -->

  Direct Known Subclasses:
  [FastJGeometry](FastJGeometry.md), [J3D_Geometry](J3D_Geometry.md)

  ------------------------------------------------------------------------



      public class JGeometry
      extends java.lang.Object
      implements RNode, java.lang.Cloneable, java.io.Serializable

  A Java class that maps Oracle Spatial's SQL type MDSYS.SDO_GEOMETRY. Supports only Oracle JDBC Driver version 8.1.7 or higher. Provides basic access functions to the geometries stored in Oracle Spatial database.
  Note that this class is not synchornized, meaning if one thread is reading this geometry and another is modifying it (such as changing its ordinates array), there may be inconsistencies.

  However, this JGeometry class can be used to write thread safe applications by follwing these guidelines.

  These following static methods are not thread safe, rest of the static methods and other non static methods are thread safe in this class.

  public static STRUCT store(JGeometry geom, Connection conn) throws SQLException

  public static STRUCT store(JGeometry geom, Connection conn, boolean BigD) throws SQLException

  public static STRUCT store(JGeometry geom, Connection conn, Object\[\] descriptors )

  public static STRUCT store(JGeometry geom, Connection conn, Object\[\] descriptors, boolean BigD)

  protected final static void createDBDescriptors(Connection conn) throws SQLException

  public final static STRUCT store(Connection conn, JGeometry geom, StructDescriptor desc) throws Exception

  Use the store(conn,geom) method for storing the geometry objects to the database. This method will not change any static variables, so it is thread safe. All the other variations of the store method are not thread safe, so don't use those store methods in a thread safe application. Don't extend the JGeometry class to expose any of instance variables to external methods.

  The main methods for reading/writing db geometries are: `load(STRUCT)` and `store()`. Here is a simple example showing how to use these two methods:

           /// reading a geometry from database
           ResultSet rs = statement.executeQuery("SELECT geometry FROM states where name='Florida'");
           STRUCT st = (oracle.sql.STRUCT) rs.getObject(1);
           //convert STRUCT into geometry
           JGeometry j_geom = JGeometry.load(st);

           // ... manipulate the geometry or create a new JGeometry ...

           /// writing a geometry back to database
           PreparedStatement ps = connection.prepareStatement("UPDATE states set geometry=? where name='Florida'");
           //convert JGeometry instance to DB STRUCT
           STRUCT obj = JGeometry.store(j_geom, connection);
           ps.setObject(1, obj);
           ps.execute();


  If you are building new applications using an 11g release of this API, you can speed up reading and writing of JGoemetry objects using the new `load(byte[])` and `store(Connection, JGeometry)`. It improves its performance by using an internal SDO pickler to unlinearize an a SDO_GEOMETRY to a JGeometry object and linearize a JGeometry object to a Oracle pickler image for storing to an Oracle database. Here is a simple example showing how to use these two new methods:

           /// reading a geometry from database
           ResultSet rs = statement.executeQuery("SELECT geometry FROM states where name='Florida'");
           byte[] image = ((OracleResultSet)rs).getBytes(1);
           //convert image into a JGeometry object using the SDO pickler
           JGeometry j_geom = JGeometry.load(image);

           // ... manipulate the geometry or create a new JGeometry ...

           /// writing a geometry back to database
           PreparedStatement ps = connection.prepareStatement(
               "UPDATE states set geometry=? where name='Florida'");
           //convert JGeometry instance to DB STRUCT using the SDO pickler
           STRUCT obj = JGeometry.store(connection, j_geom);
           ps.setObject(1, obj);
           ps.execute();


  Requirements for this class:

         Oracle JDBC driver ver. 8.1.7 or higher;
         JDK 1.2 or higher (for Java2D support)


  Since:
  JDBC Driver 8.1.7

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type   | Class and Description                                                                                           |
    |---------------------|-----------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`JGeometry.GeomParser`](JGeometry.GeomParser.md)<br>Callbacks for parsing this geometry via parseGeometry      |
    | `static class `     | [`JGeometry.Point`](JGeometry.Point.md)<br>Deprecated. <br>use @link{oracle.spatial.geometry.JPoint2DD} instead |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                               |
    |-------------------|-----------------------------------------------------|
    | `static int`      | `GTYPE_COLLECTION`<br>collection geometry type      |
    | `static int`      | `GTYPE_CURVE`<br>curve geoemtry type                |
    | `static int`      | `GTYPE_MULTICURVE`<br>multi-curve geometry type     |
    | `static int`      | `GTYPE_MULTIPOINT`<br>multi-point geometry type     |
    | `static int`      | `GTYPE_MULTIPOLYGON`<br>multi-polygon geometry type |
    | `static int`      | `GTYPE_POINT`<br>point geometry type                |
    | `static int`      | `GTYPE_POLYGON`<br>polygon geometry type            |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JGeometry``(double minX, double minY, double maxX, double maxY, int srid)`<br>Creates a JGeometry instance that is a Rectangle.                               |
    | `JGeometry``(double x, double y, double z, int srid)`<br>Constructs a 3D JGeometry instance that is a point                                                    |
    | `JGeometry``(double x, double y, int srid)`<br>Constructs a 2D JGeometry instance that is a point                                                              |
    | `JGeometry``(int gtype, int srid, double x, double y, double z, int[] elemInfo, double[] ordinates)`<br>Constructs a JGeometry instance with given information |
    | `JGeometry``(int gtype, int srid, int[] elemInfo, double[] ordinates)`<br>Constructs a JGeometry instance with given information                               |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |--------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JGeometry`                                | `affineTransforms``(boolean translation, double tx, double ty, double tz, boolean scaling, JGeometry Psc1, double sx, double sy, double sz, boolean rotation, JGeometry P1, JGeometry line1, double angle, int dir, boolean shearing, double SHxy, double SHyx, double SHxz, double SHzx, double SHyz, double SHzy, boolean reflection, JGeometry Pref, JGeometry lineR, int dirR, boolean planeR, double[] n, double[] bigD)`<br>Returns the affine transformed JGeometry in 2D and 3D Euclidean space. |
    | `boolean`                                  | `anyInteract``(JGeometry A, double tolerance)`<br>This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry.                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                  | `anyInteract``(JGeometry A, double tolerance, boolean isGeodetic)`<br>This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry.                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                  | `anyInteract``(JGeometry A, double tolerance, java.lang.String isGeodetic)`<br>This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry.                                                                                                                                                                                                                                                                                                                                |
    | `double`                                   | `area``(double tolerance)`<br>Compute the area of the geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `JGeometry`                                | `buffer``(double bufferWidth)`<br>This method generates a new JGeometry object which is the buffered version of the input geometry.                                                                                                                                                                                                                                                                                                                                                                      |
    | `JGeometry`                                | `buffer``(double bufferWidth, double arcTol)`<br>This method generates a new JGeometry object which is the buffered version of the input geometry.                                                                                                                                                                                                                                                                                                                                                       |
    | `JGeometry`                                | `buffer``(double bufferWidth, double SMA, double iFlat, double arcT)`<br>This method generates a new JGeometry object which is the buffered version of the input geometry.                                                                                                                                                                                                                                                                                                                               |
    | `static java.lang.String`                  | `byteArrayToHexString``(byte[] in)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`JPoint2DD`](JPoint2DD.md)                | `centralLongLatforGNMProjection``()`<br>Choose the default central long/lat point for a Gnomic projection based on the geometry's MBR.                                                                                                                                                                                                                                                                                                                                                                   |
    | `static JGeometry`                         | `circle_polygon``(double center_longitude, double center_latitude, double radius, double arc_tolerance)`<br>This method return JGeometry which is the approximated Geodetic Circle.                                                                                                                                                                                                                                                                                                                      |
    | `static JGeometry`                         | `circle_polygon``(double center_longitude, double center_latitude, double radius, double start_azimuth, double end_azimuth, double arc_tolerance)`<br>This method return JGeometry which is the approximated Geodetic Arc CirclePolygon - Stroked circle (arc actually) polygon with start and end azimuths and tolerance.                                                                                                                                                                               |
    | `java.lang.Object`                         | `clone``()`<br>constructs an instance that is a clone of this `JGeometry`.                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static double[]`                          | `computeArc``(double x1, double y1, double x2, double y2, double x3, double y3)`<br>Helper method to compute center, radius, and angles for this arc from the three coordinate points.                                                                                                                                                                                                                                                                                                                   |
    | `JGeometry`                                | `concaveHullDig``(double digN)`<br>Return the concave hull of the specified multipoint geometry.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `JGeometry`                                | `convexHull``()`<br>Returns the convex hull of the input geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `double[]`                                 | `coord``(int idx0)`<br>Return one coordinate of size dim from the ordinates array, starting at ordinates\[idx0\] In a 2-dimensional geometry, coord(0) is the first coordinate, coord(2) is the second coordinate; note index starts at zero and needs to be incremented by dim for subsequent coordinates.                                                                                                                                                                                              |
    | `static JGeometry`                         | `createArc2d``(double[] coords, int dim, int srid)`<br>Creates a JGeometry simple arc in 2D                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static JGeometry`                         | `createCircle``(double x1, double y1, double x2, double y2, double x3, double y3, int srid)`<br>Creates a JGeometry that is a 2D Circle.                                                                                                                                                                                                                                                                                                                                                                 |
    | `static JGeometry`                         | `createCircle``(double x, double y, double radius, int srid)`<br>Creates a JGeometry that is a Circle with provided radius and center.                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.awt.Shape`                           | `createDoubleShape``()`<br>Creates a Java2D double shape object from this `JSDOGeometry` Double shape object use double, not float, as the coordinates data type.                                                                                                                                                                                                                                                                                                                                        |
    | `java.awt.Shape`                           | `createDoubleShape``(java.awt.geom.AffineTransform xfm)`<br>Creates a transformed shape from the geometry using the given affine transform.                                                                                                                                                                                                                                                                                                                                                              |
    | `static JGeometry`                         | `createLinearLineString``(double[] coords, int dim, int srid)`<br>Creates a JGeometry that is a single linear Line String.                                                                                                                                                                                                                                                                                                                                                                               |
    | `static JGeometry`                         | `createLinearMultiLineString``(java.lang.Object[] coords, int dim, int srid)`<br>Creates a JGeometry that is a linear multi-linestring.                                                                                                                                                                                                                                                                                                                                                                  |
    | `static JGeometry`                         | `createLinearPolygon``(double[] coords, int dim, int srid)`<br>Creates a JGeometry that is a simple linear Polygon without holes.                                                                                                                                                                                                                                                                                                                                                                        |
    | `static JGeometry`                         | `createLinearPolygon``(java.lang.Object[] coords, int dim, int srid)`<br>Creates a JGeometry that is a linear polygon which may have holes.                                                                                                                                                                                                                                                                                                                                                              |
    | `static JGeometry`                         | `createLRSLinearLineString``(double[] coords, int LRSdim, int srid)`<br>Creates a JGeometry that is a single LRS linear Line String.                                                                                                                                                                                                                                                                                                                                                                     |
    | `static JGeometry`                         | `createLRSLinearMultiLineString``(java.lang.Object[] coords, int LRSdim, int srid)`<br>Creates a JGeometry that is a LRS linear multi-linestring.                                                                                                                                                                                                                                                                                                                                                        |
    | `static JGeometry`                         | `createLRSLinearPolygon``(double[] coords, int LRSdim, int srid)`<br>Creates a JGeometry that is a simple LRS linear Polygon without holes.                                                                                                                                                                                                                                                                                                                                                              |
    | `static JGeometry`                         | `createLRSLinearPolygon``(java.lang.Object[] coords, int LRSdim, int srid)`<br>Creates a JGeometry that is a linear LRS polygon which may have holes.                                                                                                                                                                                                                                                                                                                                                    |
    | `static JGeometry`                         | `createLRSPoint``(double[] coord, int LRSdim, int srid)`                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static JGeometry`                         | `createMultiPoint``(java.lang.Object[] coords, int dim, int srid)`<br>Creates a JGeometry that is a multi-point geometry.                                                                                                                                                                                                                                                                                                                                                                                |
    | `static JGeometry`                         | `createNURBScurve``(double[] coords, int dim, int srid)`<br>Creates a JGeometry that is a single NURBS curve.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static JGeometry`                         | `createPoint``(double[] coord, int dim, int srid)`                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.awt.Shape`                           | `createShape``()`<br>Creates a Java2D shape object from this `JGeometry` Note: for point geometry this method returns null.                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.awt.Shape`                           | `createShape``(java.awt.geom.AffineTransform xfm)`<br>Creates a transformed shape from the geometry using the given affine transform.                                                                                                                                                                                                                                                                                                                                                                    |
    | `java.awt.Shape`                           | `createShape``(java.awt.geom.AffineTransform xfm, boolean simplify)`<br>Creates a simplified transformed shape from the geometry using the given affine transform.                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                  | `crossesMeridian``()`<br>Checks if the given geometry has any lines that cross the Prime Meridian.                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static double[]`                          | `decodePolyline``(java.lang.String encodedPolyline)`<br>Returns 2D polyline ordinates                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `double`                                   | `defaultTolerance``()`<br>Gives a tolerance that is appropriate for many use cases.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `JGeometry`                                | `densifyArcs``(double arc_tolerance)`<br>Arcs densification method to densify arcs into lines.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `JGeometry`                                | `densifyArcs``(double arc_tolerance, boolean flag)`                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `JGeometry`                                | `densifyGeodesic``()`<br>Chooses a default tolerance value and calls `densifyGeodesic(double)`.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `JGeometry`                                | `densifyGeodesic``(double tolerance)`<br>Densify a geodesic geometry by interpolating points along great circle arcs.                                                                                                                                                                                                                                                                                                                                                                                    |
    | `double`                                   | `distance``(JGeometry A, double tolerance)`<br>This method determines the distance between two 2D Geometries.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `double`                                   | `distance``(JGeometry A, double tolerance, java.lang.String isGeodetic)`<br>This method determines the distance between two 2D Geometries.                                                                                                                                                                                                                                                                                                                                                               |
    | `static java.lang.String`                  | `encodePolyline``(double[] polyline)`<br>Returns Google polyline encoding String for a series of 2D ordinates                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                  | `equals``(java.lang.Object otherObj)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static double[]`                          | `expandCircle``(double x1, double y1, double x2, double y2, double x3, double y3)`                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static JGeometry`                         | `fitArc``(int srid, double[] coords, double tol)`<br>Creates a 2D arc JGeometry that best fits the given coordinates.                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                  | `fitsInHemisphere``()`<br>Check if the Geometry fits in half a hemi sphere.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static double`                            | `geodetic3DLength``(JGeometry geom)`<br>This method computes Geodetic/Geographic 3D length geodetic geometry.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static double`                            | `geodetic3DLength``(JGeometry geom, double smax, double flat, double geog_crs_uom_factor)`<br>This method computes Geodetic/Geographic 3D length for a specified smax and flattening.                                                                                                                                                                                                                                                                                                                    |
    | [`CoordSysInfo`](CoordSysInfo.md)          | `getCoordSysInfo``()`<br>Returns a CoordSysInfo for the srid of this geometry (updating the sridCSI field if necessary).                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                      | `getDimensions``()`<br>Gets the dimensionality of this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `JGeometry`                                | `getElementAt``(int position)`<br>Gets an element in this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `JGeometry[]`                              | `getElements``()`<br>Gets an array of the (geometry) elements in this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `int[]`                                    | `getElemInfo``()`<br>Gets the reference to the element infomation array of this `JGeometry`.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `double[]`                                 | `getExtendedMBR``()`<br>Extends the MBR for a the Geodetic geometry to account for the curvature of the earth.                                                                                                                                                                                                                                                                                                                                                                                           |
    | `double[]`                                 | `getFirstPoint``()`<br>Gets the first coordinate for this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static StructDescriptor`                  | `getGeomDescriptor``(java.sql.Connection conn)`<br>Obtains a StructDescriptor object to the MDSYS.SDO_GEOMETRY PL/SQL object type from the given connection.                                                                                                                                                                                                                                                                                                                                             |
    | `java.awt.geom.Point2D`                    | `getJavaPoint``()`<br>Gets the java2D point rerepsentation of this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `java.awt.geom.Point2D[]`                  | `getJavaPoints``()`<br>Gets the java2D points rerepsentation of this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `java.awt.geom.Point2D`                    | `getLabelPoint``()`<br>Gets the SDO_GEOMETRY.sdo_point as a label point.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `double[]`                                 | `getLabelPointXYZ``()`<br>Returns the x,y and z value of the label point in a double array.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `double[]`                                 | `getLastPoint``()`<br>Gets the last coordinate of the geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `int`                                      | `getLRMDimension``()`<br>Gets the dimension index for LRS measure.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `double[]`                                 | `getMBR``()`<br>Gets the MBR of this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`Mer`](Mer.md)                            | `getMer``()`<br>Returns the bounding box of this spatial object.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `int`                                      | `getNumPoints``()`<br>Gets the number of points or verticies in this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static JGeometry`                         | `getNurbsApprox``(JGeometry geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.lang.Object[]`                | `getOracleDescriptors``(java.sql.Connection conn)`<br>Deprecated. <br>Use `getOracleDescriptors(java.sql.Connection)` and the storeJS method instead of store                                                                                                                                                                                                                                                                                                                                            |
    | `static java.lang.Object[]`                | `getOracleDescriptorsStr``()`<br>Obtains a set of Oracle type descriptors related to the SDO_GEOMETRY type from the given connection.                                                                                                                                                                                                                                                                                                                                                                    |
    | `double[]`                                 | `getOrdinatesArray``()`<br>Gets the reference to the ordinate array of this `JGeometry`.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.lang.Object[]`                       | `getOrdinatesOfElements``()`<br>Gets an array of the (top-level) elements in this geometry.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `int`                                      | `getOrientMultiPointOffset``()`<br>Returns the offset to get the orientation parameters for a Multi-point.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `double[]`                                 | `getPoint``()`<br>Gets the coordinate of this point geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `long`                                     | `getSize``()`<br>Gets an estimated size of the geometry in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                      | `getSRID``()`<br>Gets the geometry SRID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                      | `getType``()`<br>Gets the geometry type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                  | `hasCircularArcs``()`<br>Checks if this geometry is a compound one.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                  | `isCircle``()`<br>Checks if this geometry represents a circle.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                  | `isGeodetic``()`<br>Determine if the geometry is geodetic based on the SRID and coordinate system information.                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                  | `isGeodeticMBR``()`<br>Checks if this geometry represents a geodetic MBR.                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                  | `isInside``(JGeometry A, double tolerance)`<br>This method determines if a 2D/3D Geometry is inside another 2D/3D Geometry.                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                  | `isInside``(JGeometry A, double tolerance, java.lang.String isGeodetic)`<br>This method determines if a 2D/3D Geometry is inside another 2D/3D Geometry.                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                  | `isLRSGeometry``()`<br>Checks if this is a LRS (Linear Reference System) geometry.                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                  | `isMultiPoint``()`<br>Checks if this geometry is of Multi-Point type.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                  | `isOrientedMultiPoint``()`<br>Checks if this geometry is of Multi-Point type and oriented.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                  | `isOrientedPoint``()`<br>Checks if this geometry is of point type and oriented.                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                  | `isPoint``()`<br>Checks if this geometry is of point type.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                  | `isRectangle``()`<br>Checks if this geometry represents a rectangle.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `double`                                   | `length``(double tolerance)`<br>Compute the length + perimeter of the geometry (length of all curves plus perimeter of all polygons)                                                                                                                                                                                                                                                                                                                                                                     |
    | `static double[]`                          | `linearizeArc``(double x1, double y1, double x2, double y2, double x3, double y3)`                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static double[]`                          | `linearizeArc``(double x1, double y1, double x2, double y2, double x3, double y3, boolean forThisArc, int numPoints)`<br>returns a linearized array of 2D line segments for an ARC given in three points.                                                                                                                                                                                                                                                                                                |
    | `static double[]`                          | `linearizeArc``(double x1, double y1, double x2, double y2, double x3, double y3, double tolerance, boolean flag)`<br>For a given arc, returns a linearized array of 2D line segments.                                                                                                                                                                                                                                                                                                                   |
    | `static double[]`                          | `linearizeArc``(double x1, double y1, double x2, double y2, double x3, double y3, int numPoints)`<br>returns a linearized array of 2D line segments for an ARC given in three points.                                                                                                                                                                                                                                                                                                                    |
    | `static JGeometry`                         | `load``(STRUCT st)`<br>Deprecated. <br>Use java.sql.Struct and `loadJS(java.sql.Struct)` instead.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static JGeometry`                         | `loadJS``(java.sql.Struct st)`<br>Creates a JGeometry instance from a java.sql.Struct object representing a geometry column in a JDBC result set.                                                                                                                                                                                                                                                                                                                                                        |
    | `static JGeometry`                         | `loadJS``(java.sql.Struct st, int is_unit_radians, double smax, double flat)`<br>Creates a JGeometry instance from a java.sql.Struct object representing a geometry column in a JDBC result set.                                                                                                                                                                                                                                                                                                         |
    | `static JGeometry`                         | `make_2d``(JGeometry geom3D, boolean ignoreSRID, int targetSRID)`<br>This method converts 3D Geometry into 2D Geometry.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static JGeometry`                         | `make_3d``(JGeometry geom2D, boolean ignoreSRID, int targetSRID, double height)`<br>This method converts 2D Geometry into 3D Geometry.                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`J3D_Geometry`](J3D_Geometry.md) | `make_3dgeom``(JGeometry geom2D)`<br>Promote the given geometry to a J3D_Geometry.                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`J3D_Geometry`](J3D_Geometry.md) | `make_3dgeom``(JGeometry geom2D, boolean ignoreSRID, int targetSRID, double height)`<br>This method promotes a JGeometry to a J3D_Geometry.                                                                                                                                                                                                                                                                                                                                                              |
    | `static int`                               | `monoMeasure``(double[] coords, int dim)`<br>Edited version of PL/SQL monotonic_measure() monoMeasure() determines whether a line is monotonically increasing or decreasing Note: Repeated measures are not flagged as inconsistent (but are not valid in LRS); assumes measure is in the last position: X,Y,M or X,Y,Z,M                                                                                                                                                                                |
    | `void`                                     | `parseGeometry``(`[`JGeometry.GeomParser`](JGeometry.GeomParser.md)` action)`<br>Parse the geometry into meaningful pieces, calling the appropriate action on each piece.                                                                                                                                                                                                                                                                                                                                |
    | `static void`                              | `projectArrayToGNM``(double central_longitude, double central_latitude, int dim, double[] ordsIn, double[] ordsOut)`<br>Projects an array of vertices longitude/latitude/height to Gnomonic with a user-defined central longitude and latitude.                                                                                                                                                                                                                                                          |
    | `JGeometry`                                | `projectFromGNM_longLat``(double central_longitude, double central_latitude)`<br>Projects a geometry vertex by vertex from Gnomonic to longitude/latitude with a user-defined central longitude and latitude.                                                                                                                                                                                                                                                                                            |
    | `JGeometry`                                | `projectFromLTP``()`<br>This method generates a new JGeometry object by projecting the input from a Local Tangent Plane to geodetic long/lat.                                                                                                                                                                                                                                                                                                                                                            |
    | `JGeometry`                                | `projectToGNM_longLat``()`<br>Projects a geometry vertex by vertex from longitude/latitude/height to Gnomonic with an internally computed central longitude and latitude.                                                                                                                                                                                                                                                                                                                                |
    | `JGeometry`                                | `projectToGNM_longLat``(double central_longitude, double central_latitude)`<br>Projects a geometry vertex by vertex from longitude/latitude to Gnomonic with a user-defined central longitude and latitude.                                                                                                                                                                                                                                                                                              |
    | `JGeometry`                                | `projectToLTP``()`<br>This method generates a new JGeometry object by projecting the input to a Local Tangent Plane.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `JGeometry`                                | `projectToLTP``(double smax, double flat)`<br>This method generates a new JGeometry object by projecting the input to a Local Tangent Plane.                                                                                                                                                                                                                                                                                                                                                             |
    | `static double[]`                          | `reFormulateArc``(double[] d)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                     | `setLRMDimension``(int m)`<br>Sets the dimension index for LRS measure.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                     | `setSRID``(int srid)`<br>Sets the srid for this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                     | `setType``(int gt)`<br>Sets the geometry type for this geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `JGeometry`                                | `simplify``(double threshold)`<br>Generates a new JGeometry object which is the simplified version of the input geometry.                                                                                                                                                                                                                                                                                                                                                                                |
    | `JGeometry`                                | `simplify``(double threshold, double SMA, double iFlat)`<br>This method generates a new JGeometry object which is the simplified version of the input geometry.                                                                                                                                                                                                                                                                                                                                          |
    | `JGeometry`                                | `simplifyVW``(double threshold)`<br>Simplified interface to the Visvalingam-Whyatt (1993) line simplification algorithm, which uses area to decide which vertices to delete.                                                                                                                                                                                                                                                                                                                             |
    | `JGeometry`                                | `simplifyVW``(double vertexThreshold, boolean taller_triangles, double M, double N, double KS, double KH, double SM, double SK)`<br>This method is a new line simplification based on the enhanced version of Visvalingam-Whyatt (1993) line simplification algorithm using weighted effecive area concept (Ref: Zhou, Jones SDH'04: Shape Aware Line Generalization with Weighted Effective Area) on projected space.                                                                                   |
    | `static JGeometry`                         | `simplifyVW``(JGeometry geom, double vertexThreshold, boolean taller_triangles, double M, double N, double KS, double KH, double SM, double SK)`<br>Legacy method for calling simplifyVW.                                                                                                                                                                                                                                                                                                                |
    | `static JGeometry`                         | `simplifyVW``(JGeometry geom1, double vertexThreshold, boolean taller_triangles, double M, double N, double KS, double KH, double SM, double SK, double SMA, double iFlat)`<br>This method is a new line simplification based on the enhanced version of Visvalingam-Whyatt (1993) line simplification algorithm using weighted effecive area concept (Ref: Zhou, Jones SDH'04: Shape Aware Line Generalization with Weighted Effective Area) on geodetic space.                                         |
    | `static STRUCT`                            | `store``(java.sql.Connection conn, JGeometry geom)`<br>Deprecated. <br>Use `storeJS(Connection, JGeometry)` instead.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static STRUCT`                            | `store``(java.sql.Connection conn, JGeometry geom, StructDescriptor desc)`<br>Converts a JGeometry instance to an Oracle JDBC STRUCT object using the SdoPickler.                                                                                                                                                                                                                                                                                                                                        |
    | `static byte[]`                            | `store``(JGeometry geom)`<br>Converts a JGeometry instance to an Oracle pickler image of the SDO_GEOMETRY type.                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static STRUCT`                            | `store``(JGeometry geom, java.sql.Connection conn)`<br>Deprecated. <br>Use `storeJS(JGeometry, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static STRUCT`                            | `store``(JGeometry geom, java.sql.Connection conn, boolean BigD)`<br>Deprecated. <br>Use `storeJS(JGeometry, Connection, boolean)` instead.                                                                                                                                                                                                                                                                                                                                                              |
    | `static STRUCT`                            | `store``(JGeometry geom, java.sql.Connection conn, java.lang.Object[] descriptors)`<br>Deprecated. <br>Use `storeJS(JGeometry, Connection, Object[])` instead.                                                                                                                                                                                                                                                                                                                                           |
    | `static STRUCT`                            | `store``(JGeometry geom, java.sql.Connection conn, java.lang.Object[] descriptors, boolean BigD)`<br>Deprecated. <br>Use `storeJS(JGeometry, Connection, Object[], boolean)` instead.                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`                   | `storeJS``(java.sql.Connection conn, JGeometry geom)`<br>Converts a JGeometry instance to an Oracle JDBC Struct object using the SdoPickler.                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`                   | `storeJS``(JGeometry geom, java.sql.Connection conn)`<br>Converts the given geometry object into an Oracle JDBC Struct object.                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.sql.Struct`                   | `storeJS``(JGeometry geom, java.sql.Connection conn, boolean BigD)`                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static java.sql.Struct`                   | `storeJS``(JGeometry geom, java.sql.Connection conn, java.lang.Object[] descriptors)`<br>Converts the given geometry object into an Oracle JDBC Struct object.                                                                                                                                                                                                                                                                                                                                           |
    | `static java.sql.Struct`                   | `storeJS``(JGeometry geom, java.sql.Connection conn, java.lang.Object[] descriptors, boolean BigD)`                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                     | `tfm_8307_to_PopularMercator``(boolean ellipsoidal)`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `tfm_8307_to_PopularMercator``(int[] elemInfo, double[] ords, boolean ellipsoidal)`                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                     | `tfm_PopularMercator_to_8307``(boolean ellipsoidal)`                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `tfm_PopularMercator_to_8307``(int[] elemInfo, double[] ords, boolean ellipsoidal)`                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.lang.String`                         | `toGeoJson``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static java.lang.String`                  | `toGeoJsonCollection``(JGeometry[] geoms)`<br>For a given array of JGeoemtry, returns a GeoJSON string of a geometry collection.                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.lang.String`                         | `toString``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `java.lang.String`                         | `toStringFull``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.lang.String`                         | `toStringFull``(int doublePrecision)`<br>This is similar to the toStringFull method of Java String class.                                                                                                                                                                                                                                                                                                                                                                                                |
    | `double`                                   | `volume``(double tolerance)`<br>Compute the volume of the geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                      |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### GTYPE_POINT

          public static final int GTYPE_POINT

      point geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_CURVE

          public static final int GTYPE_CURVE

      curve geoemtry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_POLYGON

          public static final int GTYPE_POLYGON

      polygon geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_COLLECTION

          public static final int GTYPE_COLLECTION

      collection geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTIPOINT

          public static final int GTYPE_MULTIPOINT

      multi-point geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTICURVE

          public static final int GTYPE_MULTICURVE

      multi-curve geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTIPOLYGON

          public static final int GTYPE_MULTIPOLYGON

      multi-polygon geometry type
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### JGeometry

          public JGeometry(int gtype,
                           int srid,
                           double x,
                           double y,
                           double z,
                           int[] elemInfo,
                           double[] ordinates)

      Constructs a JGeometry instance with given information
      Parameters:
      `gtype` - the geometry type

      `srid` - the SRS id; if 0 is used then the MDSYS.SDO_GEOMETRY.SDO_SRID will be set to null when converted into DB format.

      `x` - x ordinate of a label point

      `y` - y ordinate of a label point

      `z` - z ordinate of a label point

      `elemInfo` - geometry element info array

      `ordinates` - geometry ordinates array

    <!-- -->

    - #### JGeometry

          public JGeometry(int gtype,
                           int srid,
                           int[] elemInfo,
                           double[] ordinates)

      Constructs a JGeometry instance with given information
      Parameters:
      `gtype` - the geometry type

      `srid` - the SRS id; if 0 is used then the MDSYS.SDO_GEOMETRY.SDO_SRID will be set to null when converted into DB format.

      `elemInfo` - geometry element info array

      `ordinates` - geometry ordinates array

    <!-- -->

    - #### JGeometry

          public JGeometry(double x,
                           double y,
                           int srid)

      Constructs a 2D JGeometry instance that is a point
      Parameters:
      `x` - x ordinate of a label point

      `y` - y ordinate of a label point

      `srid` - the SRS id; if 0 is used then the MDSYS.SDO_GEOMETRY.SDO_SRID will be set to null when converted into DB format.

    <!-- -->

    - #### JGeometry

          public JGeometry(double x,
                           double y,
                           double z,
                           int srid)

      Constructs a 3D JGeometry instance that is a point
      Parameters:
      `x` - x ordinate of a label point

      `y` - y ordinate of a label point

      `z` - z ordinate of a label point

      `srid` - the SRS id; if 0 is used then the MDSYS.SDO_GEOMETRY.SDO_SRID will be set to null when converted into DB format.

    <!-- -->

    - #### JGeometry

          public JGeometry(double minX,
                           double minY,
                           double maxX,
                           double maxY,
                           int srid)

      Creates a JGeometry instance that is a Rectangle. The coordinates for the lower-left and upper-right corners are supplied.
      Parameters:
      `minX` - the minimum x ordinate of the rectangle

      `minY` - the minimum y ordinate of the rectangle

      `maxX` - the maximum x ordinate of the rectangle

      `maxY` - the maximum y ordinate of the rectangle

      `srid` - the SRS id. if 0 is used then the MDSYS.SDO_GEOMETRY.SDO_SRID will be set to null when converted into DB format.

  <!-- -->

  - ### Method Detail

    - #### clone

          public java.lang.Object clone()

      constructs an instance that is a clone of this `JGeometry`. All the fields of this object is deep-copied over to the clone.
      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### createPoint

          public static JGeometry createPoint(double[] coord,
                                              int dim,
                                              int srid)

      Parameters:
      `coord` - The coordinates of the point (either 2 or 3 values for 2D or 3D respectively)

      `dim` - Ignored - dimension taken from size of coord array

      `srid` - Coordinate system

      Returns:
      Result

    <!-- -->

    - #### createLRSPoint

          public static JGeometry createLRSPoint(double[] coord,
                                                 int LRSdim,
                                                 int srid)

      Parameters:
      `coord` - array

      `LRSdim` - LRS dimensionality: X,Y,M=2D; X,Y,Z,M=3D

      `srid` - coordinate system

      Returns:
      result

    <!-- -->

    - #### createCircle

          public static JGeometry createCircle(double x,
                                               double y,
                                               double radius,
                                               int srid)

      Creates a JGeometry that is a Circle with provided radius and center.
      Parameters:
      `x` - the x ordinate of the circle's center

      `y` - the y ordinate of the circle's center

      `radius` - the radius of the circle

      `srid` - the srid of the circle

      Returns:
      result

    <!-- -->

    - #### createCircle

          public static JGeometry createCircle(double x1,
                                               double y1,
                                               double x2,
                                               double y2,
                                               double x3,
                                               double y3,
                                               int srid)

      Creates a JGeometry that is a 2D Circle. The three supplied coordinates form the circumference of the circle.
      Parameters:
      `x1` - x ordinate of point 1

      `y1` - y ordinate of point 1

      `x2` - x ordinate of point 2

      `y2` - y ordinate of point 2

      `x3` - x ordinate of point 3

      `y3` - y ordinate of point 3

      `srid` - srs id for the circle

      Returns:
      result

    <!-- -->

    - #### createArc2d

          public static JGeometry createArc2d(double[] coords,
                                              int dim,
                                              int srid)

      Creates a JGeometry simple arc in 2D
      Parameters:
      `coords` - coords

      `dim` - dim

      `srid` - srid

      Returns:
      result

    <!-- -->

    - #### fitArc

          public static JGeometry fitArc(int srid,
                                         double[] coords,
                                         double tol)
                                  throws java.lang.Exception

      Creates a 2D arc JGeometry that best fits the given coordinates. Returned arc will extend from the first coordinate to the last minimizing the distances to the remaining coordinates; if the best such arc does not deflect by at least the specified tolerance, then will throw an exception instead. Note may throw even if tol is zero if unable to compute an arc (for example, due to degenerate or nearly degenerate input). Srid is returned in the created geometry without validation. Arcs are not supported in geodetic coordinate systems. Running time on n coordinates is O(n^2)
      Parameters:
      `srid` - the SRS id. Should not be a geodetic coordinate system.

      `coords` - a list of at least three, 2D-coordinates.

      `tol` - minimum offset from a straight line - throws if "best arc" doesn't exceed this.

      Returns:
      result

      Throws:
      `java.lang.Exception` - some of the possible causes include: 13355 List of coordinates not 2D; 13342 Fewer than three coordinates provided; 13347 Start and end coordinate not distinct; 13050 Unable to fit an arc to the points (due to tol or other reasons).

    <!-- -->

    - #### createLinearLineString

          public static JGeometry createLinearLineString(double[] coords,
                                                         int dim,
                                                         int srid)

      Creates a JGeometry that is a single linear Line String.
      Parameters:
      `coords` - the coordinates of the linear line string

      `dim` - the dimensionality of the line string.

      `srid` - the srid of the linear line string

      Returns:
      a JGeometry object that is a linear line string

    <!-- -->

    - #### createNURBScurve

          public static JGeometry createNURBScurve(double[] coords,
                                                   int dim,
                                                   int srid)

      Creates a JGeometry that is a single NURBS curve.
      Parameters:
      `coords` - the coordinates of the nurbs curve

      `dim` - the dimensionality of the nurbs curve.

      `srid` - the srid of the nurbscurve

      Returns:
      a JGeometry object that is a nurbs curve

    <!-- -->

    - #### createLRSLinearLineString

          public static JGeometry createLRSLinearLineString(double[] coords,
                                                            int LRSdim,
                                                            int srid)

      Creates a JGeometry that is a single LRS linear Line String.
      Parameters:
      `coords` - the coordinates of the LRS linear line string

      `LRSdim` - the LRS dimensionality of the line string: X,Y,M=2D; X,Y,Z,M=3D

      `srid` - the srid of the linear line string

      Returns:
      a JGeometry object that is a LRS linear line string

    <!-- -->

    - #### createLinearMultiLineString

          public static JGeometry createLinearMultiLineString(java.lang.Object[] coords,
                                                              int dim,
                                                              int srid)

      Creates a JGeometry that is a linear multi-linestring.
      Parameters:
      `coords` - an array of all the linestrings' coordinates

      `dim` - the dimensionality of the linestring

      `srid` - the srid of the multi-linestring

      Returns:
      result

    <!-- -->

    - #### createLRSLinearMultiLineString

          public static JGeometry createLRSLinearMultiLineString(java.lang.Object[] coords,
                                                                 int LRSdim,
                                                                 int srid)

      Creates a JGeometry that is a LRS linear multi-linestring.
      Parameters:
      `coords` - an array of all the LRS linestrings' coordinates

      `LRSdim` - the LRS dimensionality of the linestring: X,Y,M=2D; X,Y,Z,M=3D

      `srid` - the srid of the multi-linestring

      Returns:
      result

    <!-- -->

    - #### createMultiPoint

          public static JGeometry createMultiPoint(java.lang.Object[] coords,
                                                   int dim,
                                                   int srid)

      Creates a JGeometry that is a multi-point geometry.
      Parameters:
      `coords` - the array of double-typed arrays each containing one point

      `dim` - the dimensionality of each point

      `srid` - the srid for the geometry.

      Returns:
      result

    <!-- -->

    - #### createLinearPolygon

          public static JGeometry createLinearPolygon(double[] coords,
                                                      int dim,
                                                      int srid)

      Creates a JGeometry that is a simple linear Polygon without holes. Note that if the supplied coordinate array does not close itself, meaning the last coordinate is not the same as the first, a new coordinate will be appended to the end of the input coordinates array. the new coordinate repeats the first one.
      Parameters:
      `coords` - the coordinates of the linear polygon

      `dim` - the dimensionality of the polygon

      `srid` - the srid of the polygon

      Returns:
      result

    <!-- -->

    - #### createLinearPolygon

          public static JGeometry createLinearPolygon(java.lang.Object[] coords,
                                                      int dim,
                                                      int srid)

      Creates a JGeometry that is a linear polygon which may have holes. Each array in the double array parameter represents a single ring of the polygon. The outer ring must be the first in the double array. Note that for each ring, if its coordinate array does not close itslef, meaning the last coordinate is not the same as the first, a new coordinate will be appended to the end of that ring's coordinates array. The new coordinate repeats the first one for the said ring.
      Parameters:
      `coords` - an array of double-typed arrays that contains all the rings' coordinates

      `dim` - the dimensionality of the polygon

      `srid` - the srid of the polygon

      Returns:
      result

    <!-- -->

    - #### createLRSLinearPolygon

          public static JGeometry createLRSLinearPolygon(double[] coords,
                                                         int LRSdim,
                                                         int srid)

      Creates a JGeometry that is a simple LRS linear Polygon without holes. Note that if the supplied coordinate array does not close itslef, meaning the last coordinate is not the same as the first, a new coordinate will be appended to the end of the input coordinates array. the new coordinate repeats the first one.
      Parameters:
      `coords` - the coordinates of the LRS linear polygon

      `LRSdim` - the LRS dimensionality of the polygon: X,Y,M=2D; X,Y,Z,M=3D

      `srid` - the srid of the polygon

      Returns:
      result

    <!-- -->

    - #### createLRSLinearPolygon

          public static JGeometry createLRSLinearPolygon(java.lang.Object[] coords,
                                                         int LRSdim,
                                                         int srid)

      Creates a JGeometry that is a linear LRS polygon which may have holes. Each array in the double array parameter represents a single ring of the polygon. The outer ring must be the first in the double array. Note that for each ring, if its coordinate array does not close itself, meaning the last coordinate is not the same as the first, a new coordinate will be appended to the end of that ring's coordinates array. The new coordinate repeats the first one for the said ring.
      Parameters:
      `coords` - an array of double-typed arrays that contains all the rings' coordinates

      `LRSdim` - the LRS dimensionality of the polygon: X,Y,M=2D; X,Y,Z,M=3D

      `srid` - the srid of the polygon

      Returns:
      result

    <!-- -->

    - #### monoMeasure

          public static int monoMeasure(double[] coords,
                                        int dim)

      Edited version of PL/SQL monotonic_measure() monoMeasure() determines whether a line is monotonically increasing or decreasing Note: Repeated measures are not flagged as inconsistent (but are not valid in LRS); assumes measure is in the last position: X,Y,M or X,Y,Z,M
      Parameters:
      `coords` - an array of double that contains all coordinates

      `dim` - the dimensionality of the feature: X,Y,M=3D; X,Y,Z,M=4D

      Returns:
      1 if increasing or all measures null; -1 if decreasing; 0 if measures are inconsistent

    <!-- -->

    - #### getType

          public int getType()

      Gets the geometry type.
      Known geom types (1st digit from right):

           GTYPE_POINT = 1;
           GTYPE_CURVE = 2;
           GTYPE_POLYGON = 3;
           GTYPE_COLLECTION = 4;
           GTYPE_MULTIPOINT = 5;
           GTYPE_MULTICURVE = 6;
           GTYPE_MULTIPOLYGON = 7;

      Returns:
      the geometry type

    <!-- -->

    - #### setType

          public void setType(int gt)

      Sets the geometry type for this geometry.
      Parameters:
      `gt` - the geometry type

    <!-- -->

    - #### getLRMDimension

          public int getLRMDimension()

      Gets the dimension index for LRS measure. This is the 2nd digit (from left) of the 4-digit SDO_Geometry GTYPE.
      Returns:
      the LRS mesaure dimension

    <!-- -->

    - #### setLRMDimension

          public void setLRMDimension(int m)

      Sets the dimension index for LRS measure. This is the 2nd digit (from left) of the 4-digit SDO_Geometry GTYPE.
      Parameters:
      `m` - the LRS measure dimension

    <!-- -->

    - #### getSRID

          public int getSRID()

      Gets the geometry SRID.
      Returns:
      the srid

    <!-- -->

    - #### setSRID

          public void setSRID(int srid)

      Sets the srid for this geometry.
      Parameters:
      `srid` - the srid

    <!-- -->

    - #### getLabelPoint

          public java.awt.geom.Point2D getLabelPoint()

      Gets the SDO_GEOMETRY.sdo_point as a label point.
      Returns:
      point

    <!-- -->

    - #### getLabelPointXYZ

          public double[] getLabelPointXYZ()

      Returns the x,y and z value of the label point in a double array.
      Note that if these values are not set in the database geometry, this method will return them as `Double.NaN`.
      Returns:
      a double array contianing 3 doubles

    <!-- -->

    - #### getPoint

          public double[] getPoint()

      Gets the coordinate of this point geometry. Retruns null if this geometry is not of point type.
      Returns:
      a double array which stores the oridnates of this point; null if this geometry is not a point

    <!-- -->

    - #### getJavaPoint

          public java.awt.geom.Point2D getJavaPoint()

      Gets the java2D point rerepsentation of this geometry. Returns null if this geometry is not of point type.
      Returns:
      a java Point2D.Double instance if this is a point geometry.

    <!-- -->

    - #### getJavaPoints

          public java.awt.geom.Point2D[] getJavaPoints()

      Gets the java2D points rerepsentation of this geometry. Returns null if this geometry is not of 2D multipoint type.
      Returns:
      an array of java Point2D.Double instances if this is a 2D multipoint geometry.

    <!-- -->

    - #### isPoint

          public final boolean isPoint()

      Checks if this geometry is of point type.
      Returns:
      true if this geometry is a point

    <!-- -->

    - #### isOrientedPoint

          public final boolean isOrientedPoint()

      Checks if this geometry is of point type and oriented.
      Returns:
      true if this geometry is a point

    <!-- -->

    - #### isMultiPoint

          public final boolean isMultiPoint()

      Checks if this geometry is of Multi-Point type.
      Returns:
      true if this geometry is a multi-point; otherwise false.

    <!-- -->

    - #### isOrientedMultiPoint

          public final boolean isOrientedMultiPoint()

      Checks if this geometry is of Multi-Point type and oriented.
      Returns:
      true if this geometry is an oriented multi-point (if any of the points is an oriented point).

    <!-- -->

    - #### isRectangle

          public final boolean isRectangle()

      Checks if this geometry represents a rectangle.
      Returns:
      true if this geometry is a rectangle.

    <!-- -->

    - #### isCircle

          public final boolean isCircle()

      Checks if this geometry represents a circle.
      Returns:
      true if this geometry is a circle.

    <!-- -->

    - #### isGeodeticMBR

          public final boolean isGeodeticMBR()

      Checks if this geometry represents a geodetic MBR.
      Returns:
      true if this geometry is a geodetic MBR.

    <!-- -->

    - #### isLRSGeometry

          public final boolean isLRSGeometry()

      Checks if this is a LRS (Linear Reference System) geometry.
      Returns:
      true if this is a LRS geometry; otherwise false

    <!-- -->

    - #### hasCircularArcs

          public final boolean hasCircularArcs()

      Checks if this geometry is a compound one. A compound geometry has circular arcs as part of its boundary.
      Returns:
      result

    <!-- -->

    - #### getDimensions

          public int getDimensions()

      Gets the dimensionality of this geometry.
      Returns:
      the dimensions of this geoemtry.

    <!-- -->

    - #### getOrdinatesArray

          public double[] getOrdinatesArray()

      Gets the reference to the ordinate array of this `JGeometry`. Unless you know what you are doing, you should not modify the values in the returned array.
      Returns:
      the ordinates array corresponding to the server side MDSYS.SDO_GEOMETRY.SDO_ORDINATE_ARRAY. Null will be returned if this geometry is a point with optimal storage (i.e., the coordinate is stored in the SDO_GEOM.SDO_POINT field).

    <!-- -->

    - #### getElemInfo

          public int[] getElemInfo()

      Gets the reference to the element infomation array of this `JGeometry`. Unless you know what you are doing, you should not modify the values in the returned array.
      Returns:
      the element information array corresponding to the server side MDSYS.SDO_GEOMETRY.SDO_ELEM_INFO_ARRAY.

    <!-- -->

    - #### getNumPoints

          public final int getNumPoints()

      Gets the number of points or verticies in this geometry. Not to be confused with the number of ordinates or double values in the ordinates array.
      Returns:
      the number of points (including all parts) in this geometry.

    <!-- -->

    - #### getFirstPoint

          public double[] getFirstPoint()

      Gets the first coordinate for this geometry. If the geometry is a point, the point's coordinate will be returned. If anything else, the first coordinate in the geometry's ordinates array (MDSYS.SDO_GEOMETRY.SDO_ORDINATES) will be returned.
      Returns:
      the first point of the geometry in an array that stores the ordinates. The size of the result array is the same as the dimension of the geometry.

    <!-- -->

    - #### getLastPoint

          public double[] getLastPoint()

      Gets the last coordinate of the geometry. If the geometry is a point its coordinate will be returned. For any other geometry types the last coordinate in the ordinates array (MDSYS.SDO_GEOMETRY.SDO_ORDINATES) will be returned. Note that this method does not take into account the logica separation that may exist for the ordinates array (such as that of a multi-polygon geometry). It merely picks the last coordinate in the array.
      Returns:
      the last point of the geometry in an array that stores the ordinates. The size of the result array is the same as the dimension of the geometry.

    <!-- -->

    - #### getMBR

          public double[] getMBR()

      Gets the MBR of this geometry. When a JSDOGeoemtry is first instantiated from a db geometry STRUCT, no MBR is computed. The MBR exists only after the first call to this method. The MBR will be recalculated only when the geoemtry's structure has been modified. Note that methods such as getOrdinatesArray() allow this geometry to be modified without the MBR being updated.
      Returns:
      a double array containing the minX,minY, maxX,maxY value of the MBR for 2D or a double array containing the minX,minY,minZ maxX,maxY, maxZ value of the MBR for 3D. The returned array should not be modified by the caller.

    <!-- -->

    - #### getExtendedMBR

          public double[] getExtendedMBR()
                                  throws java.lang.Exception

      Extends the MBR for a the Geodetic geometry to account for the curvature of the earth. If MBR is used for approximate searching, this should be called explicitly to epand the MBR on geodetic data.
      Returns:
      a new MBR

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      `java.lang.Exception`

      Since:
      19.1

    <!-- -->

    - #### fitsInHemisphere

          public boolean fitsInHemisphere()
                                   throws DataException

      Check if the Geometry fits in half a hemi sphere. This method is called to check the validity of geometry if it is used in anyInteract or other methods that do Gnomonic projection.
      Returns:
      true or false

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      19.1

    <!-- -->

    - #### crossesMeridian

          public boolean crossesMeridian()
                                  throws DataException

      Checks if the given geometry has any lines that cross the Prime Meridian. Returns TRUE if the geometry corsses PM, else returns FALSE.
      Returns:
      true/false

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      19.1

    <!-- -->

    - #### getMer

          public Mer getMer()

      Description copied from interface: [`RNode`](RNode.md)
      Returns the bounding box of this spatial object.
      Specified by:
      [`getMer`](RNode.md) in interface [`RNode`](RNode.md)

      Returns:
      a Mer that contains this object, preferably the minimal Mer. The caller must not modify the returned Mer.

    <!-- -->

    - #### getOrdinatesOfElements

          public java.lang.Object[] getOrdinatesOfElements()

      Gets an array of the (top-level) elements in this geometry. Each array element in the result array is itself an array of all the ordinates for a geometry element. In other words, if this geometry has three elements, each with 10,20 and 30 ordinates, then the result Object\[\] array will have three elements, each being double\[10\], double\[20\] and double\[30\].
      Note: applicable only to linear geometries without compound elements.

      Returns:
      an array of ordinates arrays

    <!-- -->

    - #### getElementAt

          public JGeometry getElementAt(int position)

      Gets an element in this geometry. The element to be returned is specified by the position parameter. The element returned is a single JGeometry.
      Note: applicable to all valid elements, including compound elements.

      Parameters:
      `position` - the position of the element to be returned (1..n)

      Returns:
      a JGeometry if successful; otherwise null is returned.

    <!-- -->

    - #### getElements

          public JGeometry[] getElements()

      Gets an array of the (geometry) elements in this geometry. Each array element in the result array is a JGeometry. If this geometry has three elements, there will be three JGeometries in the result array.
      Note: applicable to all valid elements, including compound elements.

      Returns:
      an array of JGeometries if successful; otherwise null is returned.

    <!-- -->

    - #### getOrientMultiPointOffset

          public int getOrientMultiPointOffset()

      Returns the offset to get the orientation parameters for a Multi-point.
      Returns:
      offset

    <!-- -->

    - #### createShape

          public final java.awt.Shape createShape()

      Creates a Java2D shape object from this `JGeometry` Note: for point geometry this method returns null. You should call getJavaPoint() for point or getJavaPoints() for multi-points.
      Returns:
      a Java2D shape representation of this geometry; NULL if the geometry is of Point or Multi-point type.

    <!-- -->

    - #### createShape

          public final java.awt.Shape createShape(java.awt.geom.AffineTransform xfm)

      Creates a transformed shape from the geometry using the given affine transform. We could also do some smart resampling of the shape based on the transformed coordinates.
      Parameters:
      `xfm` - xfm

      Returns:
      result

    <!-- -->

    - #### createShape

          public final java.awt.Shape createShape(java.awt.geom.AffineTransform xfm,
                                                  boolean simplify)

      Creates a simplified transformed shape from the geometry using the given affine transform. Redundant shape points are removed from the shape. We could also do some smart resampling of the shape based on the transformed coordinates.
      Parameters:
      `xfm` - can be null

      `simplify` - flag

      Returns:
      result

    <!-- -->

    - #### createDoubleShape

          public final java.awt.Shape createDoubleShape()

      Creates a Java2D double shape object from this `JSDOGeometry` Double shape object use double, not float, as the coordinates data type. Note: for point geometry this method returns null. You should call getJavaPoint() for point or getJavaPoints() for multi-points.
      Returns:
      a Java2D shape representation of this geometry; NULL if the geometry is of Point or Multi-point type.

    <!-- -->

    - #### createDoubleShape

          public final java.awt.Shape createDoubleShape(java.awt.geom.AffineTransform xfm)

      Creates a transformed shape from the geometry using the given affine transform. The shape use double for shape coordinates We could also do some smart resampling of the shape based on the transformed coordinates.
      Parameters:
      `xfm` - xfm

      Returns:
      transformed shape

    <!-- -->

    - #### load

          @Deprecated
          public static final JGeometry load(STRUCT st)
                                                   throws java.sql.SQLException

      Deprecated. Use java.sql.Struct and `loadJS(java.sql.Struct)` instead.
      Creates a JGeometry instance from a STRUCT object representing a geometry column in a JDBC result set.
      Parameters:
      `st` - the STRUCT object from an oracle result set.

      Returns:
      a JGeometry instance if successful; otherwise null is returned.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### loadJS

          public static final JGeometry loadJS(java.sql.Struct st)
                                        throws java.sql.SQLException

      Creates a JGeometry instance from a java.sql.Struct object representing a geometry column in a JDBC result set.
      Parameters:
      `st` - the Struct object from an oracle result set.

      Returns:
      a JGeometry instance if successful; otherwise null is returned.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### loadJS

          public static final JGeometry loadJS(java.sql.Struct st,
                                               int is_unit_radians,
                                               double smax,
                                               double flat)
                                        throws java.sql.SQLException

      Creates a JGeometry instance from a java.sql.Struct object representing a geometry column in a JDBC result set.
      Parameters:
      `st` - the Struct object from an oracle result set.

      `is_unit_radians` - Flag to tell that input ordinates are in radians (angular unit) and Geometry is Geodetic/Geograhic3D (i.e., due to G3D SRID)

      `smax` - Semi Major Axis Parameter

      `flat` - Flattenning Parameter

      Returns:
      a JGeometry instance if successful; otherwise null is returned.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### store

          @Deprecated
          public static STRUCT store(JGeometry geom,
                                                  java.sql.Connection conn)
                                           throws java.sql.SQLException

      Deprecated. Use `storeJS(JGeometry, Connection)` instead.
      Converts the given geometry object into an Oracle JDBC STRUCT object. You can then bind the STRUCT object to a SQL statment that inserts or updates the geometry in the database.
      Usage note: Do not bind the STRUCT object of a JGeometry of the geodetic MBR type to an SQL DML statement that inserts or updates the geometry in the database. a database, you are not allowed to use this method to convert it into a STRUCT object.
      Parameters:
      `geom` - the JGeometry instance to be converted.

      `conn` - the connection to use.

      Returns:
      an Oracle STRUCT object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### store

          @Deprecated
          public static STRUCT store(JGeometry geom,
                                                  java.sql.Connection conn,
                                                  boolean BigD)
                                           throws java.sql.SQLException

      Deprecated. Use `storeJS(JGeometry, Connection, boolean)` instead.
      Parameters:
      `geom` - geom

      `conn` - conn

      `BigD` - BigD

      Returns:
      result

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### storeJS

          public static java.sql.Struct storeJS(JGeometry geom,
                                                java.sql.Connection conn)
                                         throws java.sql.SQLException

      Converts the given geometry object into an Oracle JDBC Struct object. You can then bind the Struct object to a SQL statment that inserts or updates the geometry in the database.
      Usage note: Do not bind the Struct object of a JGeometry of the geodetic MBR type to an SQL DML statement that inserts or updates the geometry in the database. a database, you are not allowed to use this method to convert it into a Struct object.
      Parameters:
      `geom` - the JGeometry instance to be converted.

      `conn` - the connection to use.

      Returns:
      a java.sql.Struct object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### storeJS

          public static java.sql.Struct storeJS(JGeometry geom,
                                                java.sql.Connection conn,
                                                boolean BigD)
                                         throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### store

          @Deprecated
          public static STRUCT store(JGeometry geom,
                                                  java.sql.Connection conn,
                                                  java.lang.Object[] descriptors)
                                           throws java.sql.SQLException

      Deprecated. Use `storeJS(JGeometry, Connection, Object[])` instead.
      Converts the given geometry object into an Oracle JDBC STRUCT object. You can then bind the STRUCT object to a SQL statment that inserts or updates the geometry in the database.
      This method has an optional third parameter `descriptors`, which lets you supply SQL type descriptors that are most appropriate with the given connection. To obtain these descriptors, call the `getOracleDescriptors()` method. If NULL is passed in, this method will use the global static descriptors that are cached.
      Parameters:
      `geom` - the JGeometry instance to be converted.

      `conn` - the connection to use.

      `descriptors` - a set of SQL type descriptors to be used; or NULL if you wish to use the globally cached static descriptors

      Returns:
      an Oracle STRUCT object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### store

          @Deprecated
          public static STRUCT store(JGeometry geom,
                                                  java.sql.Connection conn,
                                                  java.lang.Object[] descriptors,
                                                  boolean BigD)
                                           throws java.sql.SQLException

      Deprecated. Use `storeJS(JGeometry, Connection, Object[], boolean)` instead.
      Parameters:
      `geom` - geom

      `conn` - conn

      `descriptors` - descriptors

      `BigD` - BigD

      Returns:
      result

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### storeJS

          public static java.sql.Struct storeJS(JGeometry geom,
                                                java.sql.Connection conn,
                                                java.lang.Object[] descriptors)
                                         throws java.sql.SQLException

      Converts the given geometry object into an Oracle JDBC Struct object. You can then bind the Struct object to a SQL statment that inserts or updates the geometry in the database.
      This method has an optional third parameter `descriptors`, which lets you supply SQL type descriptors that are most appropriate with the given connection. To obtain these descriptors, call the `getOracleDescriptorsStr()` method. If NULL is passed in, this method will use the global static descriptors that are cached.
      Parameters:
      `geom` - the JGeometry instance to be converted.

      `conn` - the connection to use.

      `descriptors` - a set of SQL type descriptors to be used; or NULL if you wish to use the globally cached static descriptors

      Returns:
      a java.sql.Struct object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### storeJS

          public static java.sql.Struct storeJS(JGeometry geom,
                                                java.sql.Connection conn,
                                                java.lang.Object[] descriptors,
                                                boolean BigD)
                                         throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getOracleDescriptors

          @Deprecated
          public static java.lang.Object[] getOracleDescriptors(java.sql.Connection conn)
                                                                      throws java.sql.SQLException

      Deprecated. Use `getOracleDescriptors(java.sql.Connection)` and the storeJS method instead of store
      Obtains a set of Oracle type descriptors related to the SDO_GEOMETRY type from the given connection. The descriptors are to be passed to the `store` method that requires them.
      Parameters:
      `conn` - an Oracle JDBC connection

      Returns:
      an Object array containing the SDO_GEOMETRY related SQL type desriptors from the provided connection for SDO_GEOMETRY.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### getOracleDescriptorsStr

          public static java.lang.Object[] getOracleDescriptorsStr()
                                                            throws java.sql.SQLException

      Obtains a set of Oracle type descriptors related to the SDO_GEOMETRY type from the given connection. The descriptors are to be passed to the `storeJS` method that requires them.
      Returns:
      an Object array containing the SDO_GEOMETRY related SQL type desriptors from the provided connection for SDO_GEOMETRY.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### coord

          public double[] coord(int idx0)

      Return one coordinate of size dim from the ordinates array, starting at ordinates\[idx0\] In a 2-dimensional geometry, coord(0) is the first coordinate, coord(2) is the second coordinate; note index starts at zero and needs to be incremented by dim for subsequent coordinates.
      Parameters:
      `idx0` - Zero-based index into the ordinates array.

      Returns:
      A double of size dim

    <!-- -->

    - #### computeArc

          public static final double[] computeArc(double x1,
                                                  double y1,
                                                  double x2,
                                                  double y2,
                                                  double x3,
                                                  double y3)

      Helper method to compute center, radius, and angles for this arc from the three coordinate points.
      Parameters:
      `x1` - x ordinate of point 1

      `y1` - y ordinate of point 1

      `x2` - x ordinate of point 2

      `y2` - y ordinate of point 2

      `x3` - x ordinate of point 3

      `y3` - y ordinate of point 3

      Returns:
      an array if an arc can be computed; null if the three points overlap or are co-linear. The array contains the following (in radians): centerX, centerY, radius, startAngle, midAngle, endAngle; returned angles are in the range 0..2\*pi

    <!-- -->

    - #### expandCircle

          public static double[] expandCircle(double x1,
                                              double y1,
                                              double x2,
                                              double y2,
                                              double x3,
                                              double y3)

    <!-- -->

    - #### linearizeArc

          public static double[] linearizeArc(double x1,
                                              double y1,
                                              double x2,
                                              double y2,
                                              double x3,
                                              double y3,
                                              int numPoints)

      returns a linearized array of 2D line segments for an ARC given in three points.
      Parameters:
      `x1` - x ordinate of point 1

      `y1` - y ordinate of point 1

      `x2` - x ordinate of point 2

      `y2` - y ordinate of point 2

      `x3` - x ordinate of point 3

      `y3` - y ordinate of point 3

      `numPoints` - number of points for this arc

      Returns:
      an double array in the form of (x1,y1,x2,y2....xn,yn)

    <!-- -->

    - #### linearizeArc

          public static double[] linearizeArc(double x1,
                                              double y1,
                                              double x2,
                                              double y2,
                                              double x3,
                                              double y3,
                                              boolean forThisArc,
                                              int numPoints)

      returns a linearized array of 2D line segments for an ARC given in three points.
      Parameters:
      `x1` - x ordinate of point 1

      `y1` - y ordinate of point 1

      `x2` - x ordinate of point 2

      `y2` - y ordinate of point 2

      `x3` - x ordinate of point 3

      `y3` - y ordinate of point 3

      `forThisArc` - true if numPoints refers to this arc; false if numPoints is the number of points per 360 degree circle.

      `numPoints` - number of points (see forThisArc)

      Returns:
      an double array in the form of (x1,y1,x2,y2....xn,yn)

    <!-- -->

    - #### linearizeArc

          public static double[] linearizeArc(double x1,
                                              double y1,
                                              double x2,
                                              double y2,
                                              double x3,
                                              double y3,
                                              double tolerance,
                                              boolean flag)

      For a given arc, returns a linearized array of 2D line segments.
      Parameters:
      `x1` - x ordinate of point 1

      `y1` - y ordinate of point 1

      `x2` - x ordinate of point 2

      `y2` - y ordinate of point 2

      `x3` - x ordinate of point 3

      `y3` - y ordinate of point 3

      `tolerance` - see flag parameter

      `flag` - Pass false if tolerance specifies maximum deviation from the input arc; true if tolerance specifies maximum distance between points in linearization.

      Returns:
      an double array in the form of (x1,y1,x2,y2....xn,yn)

    <!-- -->

    - #### linearizeArc

          public static double[] linearizeArc(double x1,
                                              double y1,
                                              double x2,
                                              double y2,
                                              double x3,
                                              double y3)

    <!-- -->

    - #### reFormulateArc

          public static double[] reFormulateArc(double[] d)

    <!-- -->

    - #### getSize

          public long getSize()

      Gets an estimated size of the geometry in bytes.
      Returns:
      size of this geometry in bytes.

    <!-- -->

    - #### toGeoJson

          public java.lang.String toGeoJson()

    <!-- -->

    - #### toGeoJsonCollection

          public static java.lang.String toGeoJsonCollection(JGeometry[] geoms)

      For a given array of JGeoemtry, returns a GeoJSON string of a geometry collection.
      Returns:
      a string of GeoJSON

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### toStringFull

          public java.lang.String toStringFull()

    <!-- -->

    - #### toStringFull

          public java.lang.String toStringFull(int doublePrecision)

      This is similar to the toStringFull method of Java String class. This converts the SDO Geometry to string with all of the coordinates w/ desired double precision for the double coordinates. There is rounding in this method due to the default rounding of NumberFormat class.
      Parameters:
      `doublePrecision` - Number of digits needed after decimal

      Returns:
      String

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object otherObj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### store

          public static byte[] store(JGeometry geom)
                              throws java.lang.Exception

      Converts a JGeometry instance to an Oracle pickler image of the SDO_GEOMETRY type.
      Parameters:
      `geom` - a JGeometry instancce.

      Returns:
      an Oracle pickler image for the SDO_GEOMETRY object type if successful; otherwise, an exception will be raised.

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      11gR1.

    <!-- -->

    - #### store

          @Deprecated
          public static final STRUCT store(java.sql.Connection conn,
                                                        JGeometry geom)
                                                 throws java.lang.Exception

      Deprecated. Use `storeJS(Connection, JGeometry)` instead.
      Converts a JGeometry instance to an Oracle JDBC STRUCT object using the SdoPickler.
      This method will use the class geometry descriptor to the MDSYS.SDO_GEOMETRY PL/SQL object type if it is not null; otherwise, the class geometry descriptor will be created.

      Parameters:
      `conn` - a JDBC connection.

      `geom` - a JGeometry instancce.

      Returns:
      an Oracle STRUCT object if successful; otherwise, an exception will be raised.

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### storeJS

          public static final java.sql.Struct storeJS(java.sql.Connection conn,
                                                      JGeometry geom)
                                               throws java.lang.Exception

      Converts a JGeometry instance to an Oracle JDBC Struct object using the SdoPickler.
      This method will use the class geometry descriptor to the MDSYS.SDO_GEOMETRY PL/SQL object type if it is not null; otherwise, the class geometry descriptor will be created.

      Parameters:
      `conn` - a JDBC connection.

      `geom` - a JGeometry instancce.

      Returns:
      an Oracle STRUCT object if successful; otherwise, an exception will be raised.

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      Oracle Database 12c Release 1 (12.1)

    <!-- -->

    - #### store

          public static final STRUCT store(java.sql.Connection conn,
                                           JGeometry geom,
                                           StructDescriptor desc)
                                    throws java.lang.Exception

      Converts a JGeometry instance to an Oracle JDBC STRUCT object using the SdoPickler.
      This method has a third parameter `geomDesc`, which lets you supply a StructDescriptor object to the MDSYS.SDO_GEOMETRY object type. You can use a Java statement like: ` StructDescriptor myGeomDesc = JGeometry.getGeomDescriptor(conn); ` to create such a descriptor with a JDBC connection. However, this method is not thread safe due to this geomDesc parameter.

      Parameters:
      `geom` - the JGeometry instance to be converted.

      `conn` - the JDBC connection to use.

      `desc` - a StructDescriptor object to the MDSYS.SDO_GEOMETRY object type to be used; or NULL if you wish to use the cached class geometry descriptor, and if the class geometry descriptor is null, then one will be created and used.

      Returns:
      an Oracle STRUCT object when successful; otherwise, an exception will be raised.

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### getGeomDescriptor

          public static StructDescriptor getGeomDescriptor(java.sql.Connection conn)
                                                    throws java.sql.SQLException

      Obtains a StructDescriptor object to the MDSYS.SDO_GEOMETRY PL/SQL object type from the given connection. The descriptor is to be passed to the `store(conn, geom, geomDesc)` method that requires it.
      Parameters:
      `conn` - an Oracle JDBC connection

      Returns:
      an structure descriptor for the Oracle SQL SDO_GEOMETRY object type for SDO_GEOMETRY.

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### byteArrayToHexString

          public static java.lang.String byteArrayToHexString(byte[] in)

    <!-- -->

    - #### projectToLTP

          public final JGeometry projectToLTP()
                                       throws DataException

      This method generates a new JGeometry object by projecting the input to a Local Tangent Plane. This geometry must have this.isGeodetic() == true
      Returns:
      an equivalent JGeometry projected onto a linear tangent plane

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      12.2

    <!-- -->

    - #### projectToLTP

          public final JGeometry projectToLTP(double smax,
                                              double flat)
                                       throws DataException

      This method generates a new JGeometry object by projecting the input to a Local Tangent Plane. This geometry must be geodetic (long/lat). The SRID is not verified.
      This method takes the Semi major Axis and Flattening as the parameters. The input geometry is assumed to be geodetic. Since this does not assume any DB connectivity, there are no checks done to make sure the input is in geodetic space.

      Parameters:
      `smax` - is the Semi Major Axis for the Datum used in the CS of the input.

      `flat` - is the Flattening from CS parameters

      Returns:
      an equivalent JGeometry projected onto a linear tangent plane

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### projectFromLTP

          public final JGeometry projectFromLTP()
                                         throws DataException

      This method generates a new JGeometry object by projecting the input from a Local Tangent Plane to geodetic long/lat.
      This method requires the gtransH and lttpH attributes set in the input JGeometry class. These are set in projectToLTP() method. So this method is always called after projectToLTP() method, so those attributes must be reused in calling this method. The input geometry is assumed to be in projected. This method has no parameters.

      Returns:
      a JGeometry class in geodetic long/lat.

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### projectToGNM_longLat

          public final JGeometry projectToGNM_longLat()
                                               throws DataException

      Projects a geometry vertex by vertex from longitude/latitude/height to Gnomonic with an internally computed central longitude and latitude.
      Gnomonic Projection for small test cases that cover less than half of the hemisphere.

      The input vertices are in longitude,latitude,height format. We directly convert to Gnomonic projected geometry.

      This is Java version of forward transformation algorithm in Map Projections- A Working Manual, 1987.

      The central_longitude and central_latitude are computed by choosing the centroid of the MBR of the input geometry. On the other hand, if you choose to enter central_longitude and central_latitude, use the other signature.

      Returns:
      projected geometry

      Throws:
      [`DataException`](DataException.md) - on error

    <!-- -->

    - #### centralLongLatforGNMProjection

          public final JPoint2DD centralLongLatforGNMProjection()

      Choose the default central long/lat point for a Gnomic projection based on the geometry's MBR.
      Returns:
      Long/lat point in degrees

    <!-- -->

    - #### projectToGNM_longLat

          public final JGeometry projectToGNM_longLat(double central_longitude,
                                                      double central_latitude)
                                               throws DataException

      Projects a geometry vertex by vertex from longitude/latitude to Gnomonic with a user-defined central longitude and latitude.
      Gnomonic Projection for small test cases that cover less than half of the hemisphere.

      The input vertices are in longitude,latitude,height format. We directly convert to Gnomonic projected geometry.

      This is Java version of forward transformation algorithm in Map Projections- A Working Manual, 1987.

      We assume central_longitude and central_latitude for central longitude and latitude respectively are computed properly (e.g., by choosing centroid of the centroid-MBR of geometries)

      Note for the inverse transform: As long as you keep the central coordinates (wrt which you did the forward transform) in the inverse transform, you will arrive back at original the long/lat coordinates.

      Parameters:
      `central_longitude` - Center of projection Longitude which should be near the centroid of the geometries in query

      `central_latitude` - Center of projection Latitude in which should be near the centroid of the geometries in query

      Returns:
      projected geometry

      Throws:
      [`DataException`](DataException.md) - on error

    <!-- -->

    - #### projectArrayToGNM

          public static final void projectArrayToGNM(double central_longitude,
                                                     double central_latitude,
                                                     int dim,
                                                     double[] ordsIn,
                                                     double[] ordsOut)
                                              throws DataException

      Projects an array of vertices longitude/latitude/height to Gnomonic with a user-defined central longitude and latitude.
      Gnomonic Projection for small test cases that cover less than half of the hemisphere.

      The input vertices are in longitude,latitude,height format. We directly convert to Gnomonic projected geometry.

      This is Java version of forward transformation algorithm in Map Projections- A Working Manual, 1987.

      We assume central_longitude and central_latitude for central longitude and latitude respectively are computed properly (e.g., by choosing centroid of the centroid-MBR of geometries)

      Note for the inverse transform: As long as you keep the central coordinates (wrt which you did the forward transform) in the inverse transform, you will arrive back at original the long/lat coordinates.

      Parameters:
      `central_longitude` - Center of projection Longitude which should be near the is centroid of the geometries in query

      `central_latitude` - Center of projection Latitude which should be near the is centroid of the geometries in query

      `dim` - Dimension of the ordinates. Only (x, y) values changed; if dim \> 2 additional ordinates are copied.

      `ordsIn` - Input array of ordinates (length must be a multiple of dim)

      `ordsOut` - Output array the same size as ordsIn. May be the same array as ordsIn (i.e., transform-in-place).

      Throws:
      [`DataException`](DataException.md) - if geometry is too large for gnomic projection (geometry currently not checked)

    <!-- -->

    - #### projectFromGNM_longLat

          public final JGeometry projectFromGNM_longLat(double central_longitude,
                                                        double central_latitude)
                                                 throws DataException

      Projects a geometry vertex by vertex from Gnomonic to longitude/latitude with a user-defined central longitude and latitude.
      This is Java version of the inverse transformation algorithm in Map Projections- A Working Manual, 1987.

      Input geometry (i.e., this) is in Gnomonic domain (multiplied by Radius of earth already).

      As long as you keep the central coordinates (wrt which you did the forward transform) in the inverse transform, you will arrive back at original the long/lat coordinates.

      Parameters:
      `central_longitude` - center of projection Longitude (which must match the value used in the forward transformation)

      `central_latitude` - center of projection Latitude (which must match the value used in the forward transformation)

      Returns:
      projected geoemtry

      Throws:
      [`DataException`](DataException.md) - on error

    <!-- -->

    - #### densifyArcs

          public final JGeometry densifyArcs(double arc_tolerance)

      Arcs densification method to densify arcs into lines.
      Arc_Tolerance is given in the units of geometry. For Geodetic, this is in meters. The Arc_Tolerance is the maximum length of the perpendicular line between the surface of the arc and the straight line between the start and end points of the arc. When the flag is set, Arc tolerance is the largest length of the cord

      Parameters:
      `arc_tolerance` - is the arc_tolerance used for densification

      Returns:
      a JGeometry class with no arcs

    <!-- -->

    - #### densifyArcs

          public JGeometry densifyArcs(double arc_tolerance,
                                       boolean flag)

    <!-- -->

    - #### simplify

          public JGeometry simplify(double threshold)
                             throws DataException

      Generates a new JGeometry object which is the simplified version of the input geometry.
      Parameters:
      `threshold` - in coordinate system units (meters for geodetic SRIDs)

      Returns:
      a new, simplified JGeometry

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      12.2

    <!-- -->

    - #### simplify

          public JGeometry simplify(double threshold,
                                    double SMA,
                                    double iFlat)
                             throws DataException

      This method generates a new JGeometry object which is the simplified version of the input geometry.
      This takes the threshold as the parameter and this threshold is assumed to be in the same unit as the Unit of Projection for projected geometry. If the geometry is geodetic, this buffer width should be in meters. This method takes the Semi major Axis and Inverse Flattening as two additional parameters. These parameters should be specified for geodetic data.

      Parameters:
      `threshold` - how much coarser the geometry should be

      `SMA` - is the Semi Major Axis for the Datum used in the CS of the input.

      `iFlat` - is the Flattening from CS parameters

      Returns:
      a JGeometry class

      Throws:
      [`DataException`](DataException.md) - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### buffer

          public JGeometry buffer(double bufferWidth)
                           throws java.lang.Exception

      This method generates a new JGeometry object which is the buffered version of the input geometry.
      If isGeodetic() is true the bufferwidth is interpreted as meters.

      If isGeodetic() is false, then the buffer will be done in the coordinate frame and the bufferWidth must be specified in the same units as the coordinate system.

      A tolerance value of 1% of the bufferwidth is assumed for densifying geodetic arcs (minimum tolerance 0.05).

      Parameters:
      `bufferWidth` - is the distance value used for buffer

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      12.2

    <!-- -->

    - #### buffer

          public JGeometry buffer(double bufferWidth,
                                  double arcTol)
                           throws java.lang.Exception

      This method generates a new JGeometry object which is the buffered version of the input geometry.
      If isGeodetic() is true, then bufferwidth and tolerance are interpreted as meters.

      If isGeodetic() is false, then the buffer will be done in the coordinate frame and the bufferWidth and tolerance must be specified in the same units as the coordinate system.

      Minimum arcTol is 0.05.

      Parameters:
      `bufferWidth` - is the distance value used for buffer

      `arcTol` - tolerance used in geodetic arc densification (ignored for non-geodetic)

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      12.2

    <!-- -->

    - #### buffer

          public JGeometry buffer(double bufferWidth,
                                  double SMA,
                                  double iFlat,
                                  double arcT)
                           throws java.lang.Exception,
                                  java.sql.SQLException

      This method generates a new JGeometry object which is the buffered version of the input geometry.
      This takes the bufferWidth as the parameter and this bufferWidth is assumed to be in the same unit as the Unit of Projection for projected geometry. If the geometry is geodetic, this buffer width should be in meters.

      This method takes the Semi major Axis and Inverse Flattening as two additional parameters. These parameters should be specified for geodetic data and passed as zero otherwise.

      Parameters:
      `bufferWidth` - is the distance value used for buffer

      `SMA` - is the Semi Major Axis for the Datum used in the CS of the input.

      `iFlat` - is the Flattening from CS parameters

      `arcT` - is the arc_tolerance for geodetic arc densification

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      `java.sql.SQLException` - if an error occurs.

      Since:
      Oracle Database 11g Release 1 (11.1)

    <!-- -->

    - #### parseGeometry

          public void parseGeometry(JGeometry.GeomParser action)
                             throws java.lang.Exception

      Parse the geometry into meaningful pieces, calling the appropriate action on each piece. Currently returns some circles as polygons of arc linestrings instead of using circle callback. Rectangles are returned as polygons (linear linestring)
      Parameters:
      `action` - the actions to perform on each piece

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### affineTransforms

          public JGeometry affineTransforms(boolean translation,
                                            double tx,
                                            double ty,
                                            double tz,
                                            boolean scaling,
                                            JGeometry Psc1,
                                            double sx,
                                            double sy,
                                            double sz,
                                            boolean rotation,
                                            JGeometry P1,
                                            JGeometry line1,
                                            double angle,
                                            int dir,
                                            boolean shearing,
                                            double SHxy,
                                            double SHyx,
                                            double SHxz,
                                            double SHzx,
                                            double SHyz,
                                            double SHzy,
                                            boolean reflection,
                                            JGeometry Pref,
                                            JGeometry lineR,
                                            int dirR,
                                            boolean planeR,
                                            double[] n,
                                            double[] bigD)
                                     throws java.lang.Exception

      Returns the affine transformed JGeometry in 2D and 3D Euclidean space.
      3D and 2D affine transformations: translation, scaling, rotation, shear, reflection. The input geometries Psc1, P1, line1, Pref and lineR are regular geometries where regular geometry is defined as a non-LRS and non-orientedPoint geometry. In 3D case:

      - Translation uses tx,ty,tz for translation about an arbitrary point;
      - Scaling uses:
        - PSc1,sx,sy,sz for scaling about arbitrary point and Psc1 must be on the geometry;
        - (0,0,0),sx,sy,sz for scaling about origin;
      - Rotation uses:
        - angle,dir for x,y or z-axis roll,
        - line1,angle for rotation about an arbitrary axis;
        - P1(2D point),angle for rotation about an arbitrary point (P1) (w/ equivalent 3D rotation);
      - Shearing can use all parameters;
      - Reflection uses:
        - lineR for reflection along an arbitrary axis,
        - dirR for reflection about (through) xy,xz,yz planes,
        - planeR,n,bigD for reflection about an arbitrary plane,
        - Pref through arbitrary point (i.e., centroid), which is known as self-reflection.

      In 2D case:

      - Translation uses tx,ty for translation about an arbitrary point;
      - Scaling uses:
        - PSc1,sx,sy,sz for scaling about arbitrary point and Psc1 must be on the geometry;
        - (0,0),sx,sy,sz (where only sz can be null in PL/SQL) for scaling about origin;
      - Rotation uses P1,angle for rotation about an arbitrary point;
      - Shearing uses SHxy,SHyx;
      - Reflection uses:
        - lineR for reflection about arbitrary axis, which also covers reflection about x,y-axis.
        - Pref (i.e., centroid) for self-reflection.

      Please note that: bigD=delta and N=(A,B,C) where N is the normal of the plane in 3-D space. Thus: Plane equation: Ax+By+Cz+bigD= 3DDotProd(N,anypointonplane)+bigD=0;

      Parameters:
      `translation` - Boolean flag to denote that translation is performed

      `tx` - translation parameter for x-axis

      `ty` - translation parameter for y-axis

      `tz` - translation parameter for z-axis

      `scaling` - Boolean flag to denote that scaling is performed

      `Psc1` - Arbitrary JGeometry point on geometry to do scaling

      `sx` - scaling parameter for x-axis

      `sy` - scaling parameter for y-axis

      `sz` - scaling parameter for z-axis

      `rotation` - Boolean flag to denote that rotation is performed

      `P1` - rotation parameter for 2-D/3-D rotation about an arbitrary JGeometry point

      `line1` - rotation parameter as JGeometry line geometry for rotation about an arbitrary axis

      `angle` - rotation parameter for rotation about an arbitrary axis or x,y, or z-axis roll

      `dir` - integer rotation parameter for x(0),y(1) or z(2)-axis roll, and it is -1 if rotation is true but this parameter is not used

      `shearing` - Boolean flag to denote that shearing is performed.

      `SHxy` - parameter for shearing due to x along y direction (also in 2-D)

      `SHyx` - parameter for shearing due to y along x direction (also in 2-D)

      `SHxz` - parameter for shearing due to x along z direction (not used in 2-D)

      `SHzx` - parameter for shearing due to z along x direction (not used in 2-D)

      `SHyz` - parameter for shearing due to y along z direction (not used in 2-D)

      `SHzy` - parameter for shearing due to z along y direction (not used in 2-D)

      `reflection` - Boolean flag to denote that reflection is performed

      `Pref` - JGeometry point geometry to do reflection through arbitrary point

      `lineR` - JGeometry line geometry to do reflection along an arbitrary axis

      `dirR` - integer parameter to do reflection about (through) xy(2),xz(1),yz(0) planes, and it is -1 if reflection parameter is true but this parameter is not used

      `planeR` - Boolean flag denoting that reflection about an arbitrary plane is performed

      `n` - 3-element double array for the normal vector of the plane

      `bigD` - single element double array for the constant number in plane equation (explained above)

      Returns:
      Transformed 3-D or 2-D geometry.

      Throws:
      `java.lang.Exception` - if an error occurs.

    <!-- -->

    - #### densifyGeodesic

          public JGeometry densifyGeodesic()
                                    throws java.lang.Exception

      Chooses a default tolerance value and calls `densifyGeodesic(double)`.
      Returns:
      a new geometry that is densified along geodesic (great circle) arcs.

      Throws:
      `java.lang.Exception` - if the geometry is not a 2D or 3D geodetic geometry

    <!-- -->

    - #### densifyGeodesic

          public JGeometry densifyGeodesic(double tolerance)
                                    throws java.lang.Exception

      Densify a geodesic geometry by interpolating points along great circle arcs. Creates and returns a new, densified geometry; this geometry is unchanged.
      Interpolation assumes a spherical earth; ellipsoid information is not used.

      Geometry must be geodetic, longitude/latitude, 2D and contain only linestring and optimized rectangle types. Coordinates must be in the range -180..+180, -90..+90.

      Linestring lengths must be less than 180 degrees. Optimized rectangles are not modified.

      Parameters:
      `tolerance` - the maximum deviation from the true geodesic line in the returned geometry.

      Returns:
      a new geometry that is densified along geodesic (great circle) arcs.

      Throws:
      `java.lang.Exception` - if the geometry is not a valid geodetic geometry

    <!-- -->

    - #### tfm_8307_to_PopularMercator

          public void tfm_8307_to_PopularMercator(int[] elemInfo,
                                                  double[] ords,
                                                  boolean ellipsoidal)

    <!-- -->

    - #### tfm_8307_to_PopularMercator

          public void tfm_8307_to_PopularMercator(boolean ellipsoidal)

    <!-- -->

    - #### tfm_PopularMercator_to_8307

          public void tfm_PopularMercator_to_8307(int[] elemInfo,
                                                  double[] ords,
                                                  boolean ellipsoidal)

    <!-- -->

    - #### tfm_PopularMercator_to_8307

          public void tfm_PopularMercator_to_8307(boolean ellipsoidal)

    <!-- -->

    - #### simplifyVW

          public static JGeometry simplifyVW(JGeometry geom1,
                                             double vertexThreshold,
                                             boolean taller_triangles,
                                             double M,
                                             double N,
                                             double KS,
                                             double KH,
                                             double SM,
                                             double SK,
                                             double SMA,
                                             double iFlat)
                                      throws java.lang.Exception,
                                             java.sql.SQLException

      This method is a new line simplification based on the enhanced version of Visvalingam-Whyatt (1993) line simplification algorithm using weighted effecive area concept (Ref: Zhou, Jones SDH'04: Shape Aware Line Generalization with Weighted Effective Area) on geodetic space. We have additional parameters like length of baseline, height, length of middle line, flatness, skewness and convexity of triangles on top of Visvalingam-Whyatt algorithm. We will have the option of flatness filters depending on needing to eliminate flatter or taller triangles. After we rank the vertices of input geometry using these filters begining from the most likely to be eliminated to the least likely to be eliminated, given a threshold of weighted effective area, a subset of vertices may be selected to get the less detailed representation of the input geometry. Currently convexity filter is unity except degenerate cases. This method generates a new JGeometry object which is the simplified version of the input geometry.
      This method takes geodetic information (the Semi-major Axis and Inverse Flattening as two additional parameters). For projected coordiante systems, use zero.

      Parameters:
      `geom1` - Input geometry which is a line string or polygon with n vertices where v_0 and v\_(n-1) are the end-points of this line string or polygon. Line is assumed to be open.

      `vertexThreshold` - Percentage of vertices to be eliminated i.e., Threshold of weighted effective area to select a subset of original vertices of input line or polygon geometry to get the less detailed representation of the input line or polygon.

      `taller_triangles` - If taller triangles preferred to flatter triangles, set to TRUE, else FALSE. This is needed for flatness filter.

      `M` - Flatness filter parameter

      `N` - Flatness filter parameter

      `KS` - Flatness filter parameter

      `KH` - Flatness filter parameter

      `SM` - Skewness filter parameter

      `SK` - Skewness filter parameter

      `SMA` - is the Semi Major Axis for the Datum used in the CS of the input.

      `iFlat` - is the Flattening from CS parameters

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      `java.sql.SQLException` - if an error occurs.

      Since:
      12*c*

    <!-- -->

    - #### simplifyVW

          public JGeometry simplifyVW(double vertexThreshold,
                                      boolean taller_triangles,
                                      double M,
                                      double N,
                                      double KS,
                                      double KH,
                                      double SM,
                                      double SK)
                               throws java.lang.Exception

      This method is a new line simplification based on the enhanced version of Visvalingam-Whyatt (1993) line simplification algorithm using weighted effecive area concept (Ref: Zhou, Jones SDH'04: Shape Aware Line Generalization with Weighted Effective Area) on projected space. We have additional parameters like length of baseline, height, length of middle line, flatness, skewness and convexity of triangles on top of Visvalingam-Whyatt algorithm. We will have the option of flatness filters depending on needing to eliminate flatter or taller triangles. After we rank the vertices of input geometry using these filters begining from the most likely to be eliminated to the least likely to be eliminated, given a threshold of weighted effective area, a subset of vertices may be selected to get the less detailed representation of the input geometry. Currently convexity filter is unity except degenerate cases. This method generates a new JGeometry object which is the simplified version of the input geometry.
      Parameters:
      `vertexThreshold` - Percentage of vertices to be eliminated i.e., Threshold of weighted effective area to select a subset of original vertices of input line or polygon geometry to get the less detailed representation of the input line or polygon.

      `taller_triangles` - If taller triangles preferred to flatter triangles, set to TRUE, else FALSE. This is needed for flatness filter.

      `M` - Flatness filter parameter

      `N` - Flatness filter parameter

      `KS` - Flatness filter parameter

      `KH` - Flatness filter parameter

      `SM` - Skewness filter parameter

      `SK` - Skewness filter parameter

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      12*c*

    <!-- -->

    - #### simplifyVW

          public static JGeometry simplifyVW(JGeometry geom,
                                             double vertexThreshold,
                                             boolean taller_triangles,
                                             double M,
                                             double N,
                                             double KS,
                                             double KH,
                                             double SM,
                                             double SK)
                                      throws java.lang.Exception

      Legacy method for calling simplifyVW.
      Parameters:
      `geom` - the geometry to simplify

      `vertexThreshold` - Percentage of vertices to be eliminated i.e., Threshold of weighted effective area to select a subset of original vertices of input line or polygon geometry to get the less detailed representation of the input line or polygon.

      `taller_triangles` - If taller triangles preferred to flatter triangles, set to TRUE, else FALSE. This is needed for flatness filter.

      `M` - Flatness filter parameter

      `N` - Flatness filter parameter

      `KS` - Flatness filter parameter

      `KH` - Flatness filter parameter

      `SM` - Skewness filter parameter

      `SK` - Skewness filter parameter

      Returns:
      a JGeometry class

      Throws:
      `java.lang.Exception` - if an error occurs.

      Since:
      12*c*

    <!-- -->

    - #### simplifyVW

          public JGeometry simplifyVW(double threshold)
                               throws java.lang.Exception

      Simplified interface to the Visvalingam-Whyatt (1993) line simplification algorithm, which uses area to decide which vertices to delete. If three consecutive vertices form a triangle with area smaller than threshold, the middle vertex will be removed, until all such triangles have an area of at least threshold.
      Parameters:
      `threshold` - Triangles smaller than this will be simplified, in coordinate system units^2 (m^2 for geodetic).

      Returns:
      new, simplified geoemtry

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### geodetic3DLength

          public static double geodetic3DLength(JGeometry geom)

      This method computes Geodetic/Geographic 3D length geodetic geometry.
      Parameters:
      `geom` - Input geometry whose length is sought

      Returns:
      double Length of Geodetic/Geograohic 3D geometry

    <!-- -->

    - #### geodetic3DLength

          public static double geodetic3DLength(JGeometry geom,
                                                double smax,
                                                double flat,
                                                double geog_crs_uom_factor)

      This method computes Geodetic/Geographic 3D length for a specified smax and flattening.
      On SQL side for sdo_length, COUNT_SHARED_EDGES parameter should be NULL (default value) for Geodetic/Geographic 3D length.

      Parameters:
      `geom` - Input geometry whose length is sought

      `smax` - Changes with SRID

      `flat` - Changes with SRID

      `geog_crs_uom_factor` - Height factor due to SRID

      Returns:
      double Length of Geodetic/Geograohic 3D geometry

    <!-- -->

    - #### circle_polygon

          public static JGeometry circle_polygon(double center_longitude,
                                                 double center_latitude,
                                                 double radius,
                                                 double arc_tolerance)

      This method return JGeometry which is the approximated Geodetic Circle. Stroked circle polygon with tolerance. The number of points generated will be determined by the input tolerance, which is the maximum error permitted between the stroked circle and the true circle. Produces an SDO_GEOMETRY which duplicates the first point as the last point. This routine is whole earth; there are no dateline or pole restrictions PL/SQL equivalent is sdo_util.circle_polygon.
      Parameters:
      `center_longitude` - center point x (2D) coordinate

      `center_latitude` - center point y (2D) coordinate

      `radius` - radius of circle

      `arc_tolerance` - tolerance for stroking the arc

      Returns:
      JGeometry which is a polygon

    <!-- -->

    - #### circle_polygon

          public static JGeometry circle_polygon(double center_longitude,
                                                 double center_latitude,
                                                 double radius,
                                                 double start_azimuth,
                                                 double end_azimuth,
                                                 double arc_tolerance)

      This method return JGeometry which is the approximated Geodetic Arc CirclePolygon - Stroked circle (arc actually) polygon with start and end azimuths and tolerance. The number of points generated will be determined by the input tolerance, which is the maximum error permitted between the stroked circle and the true circle. The output is an arc-like geometry. Produces an SDO_GEOMETRY which duplicates the first point as the last point. This routine is whole earth; there are no dateline or pole restrictions. 0 is due south, and angles increase in a counter clockwise direction. PL/SQL equivalent is sdo_util.circle_polygon.
      Parameters:
      `center_longitude` - center point x (2D) coordinate

      `center_latitude` - center point y (2D) coordinate

      `radius` - radius of circle

      `start_azimuth` - startAngle

      `end_azimuth` - endAngle

      `arc_tolerance` - tolerance for stroking the arc

      Returns:
      JGeometry which is a curve

    <!-- -->

    - #### make_3d

          public static JGeometry make_3d(JGeometry geom2D,
                                          boolean ignoreSRID,
                                          int targetSRID,
                                          double height)

      This method converts 2D Geometry into 3D Geometry. This method is equivalent to sdo_cs.make_3d. If SRID conversion is not needed, set ignoreSRID to TRUE and targetSRID parameter will be ignored.
      Parameters:
      `geom2D` - JGeometry to promote

      `ignoreSRID` - if true, the new geometry will have the input SRID; otherwise it will have targetSRID

      `targetSRID` - the new srid if ignoreSRID is false

      `height` - if input geometry is 2D, the value to use as the z value on each coordinate

      Returns:
      result

    <!-- -->

    - #### make_3dgeom

          public static J3D_Geometry make_3dgeom(JGeometry geom2D,
                                                 boolean ignoreSRID,
                                                 int targetSRID,
                                                 double height)

      This method promotes a JGeometry to a J3D_Geometry. This method is equivalent to sdo_cs.make_3d. If SRID conversion is not needed, set ignoreSRID to TRUE and targetSRID parameter will be ignored.
      Parameters:
      `geom2D` - JGeometry to promote (may be 2D or 3D)

      `ignoreSRID` - if true, the new geometry will have the input SRID; otherwise it will have targetSRID

      `targetSRID` - the new srid if ignoreSRID is false

      `height` - if input geometry is 2D, the value to use as the z value on each coordinate

      Returns:
      a J3D_Geometry version of this geometry

    <!-- -->

    - #### make_3dgeom

          public static J3D_Geometry make_3dgeom(JGeometry geom2D)

      Promote the given geometry to a J3D_Geometry.
      Parameters:
      `geom2D` - input geometry

      Returns:
      a J3D Geoemtry; if input is 2D, z values will be 0.

    <!-- -->

    - #### make_2d

          public static JGeometry make_2d(JGeometry geom3D,
                                          boolean ignoreSRID,
                                          int targetSRID)

      This method converts 3D Geometry into 2D Geometry. This method is equivalent to sdo_cs.make_2d.
      Parameters:
      `geom3D` - input 3D geometry

      `ignoreSRID` - if true, result will have SRID 0; if true, will have targetSRID

      `targetSRID` - used if ignoreSRID is false

      Returns:
      result

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(JGeometry A,
                                     double tolerance,
                                     java.lang.String isGeodetic)
                              throws java.lang.Exception

      This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry. If the geometry is Geodetic, pass in "TRUE" as the third parameter. The geometries can be any 2D/3D types supported by Oracle Spatial including geometries with arcs and compund elements.
      Parameters:
      `A` - 2D/3D Geometry

      `tolerance` - at which the given geometry is valid

      `isGeodetic` - is a string that is either "TRUE" or "FALSE"

      Returns:
      TRUE if the two geometries interact; FALSE otherwise

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(JGeometry A,
                                     double tolerance)
                              throws java.lang.Exception

      This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry. Computation is geodetic if the coordinate system is geodetic. The geometries can be any 2D/3D types supported by Oracle Spatial including geometries with arcs and compund elements.
      Parameters:
      `A` - 2D/3D Geometry

      `tolerance` - at which the given geometry is valid

      Returns:
      TRUE if the two geometries interact; FALSE otherwise

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(JGeometry A,
                                     double tolerance,
                                     boolean isGeodetic)
                              throws java.lang.Exception

      This method determines if a 2D/3D Geometry has anyinteraction with another 2D/3D Geometry. If the geometry is Geodetic, pass in true as the third parameter. The geometries can be any 2D/3D types supported by Oracle Spatial including geometries with arcs and compund elements.
      Parameters:
      `A` - 2D/3D Geometry

      `tolerance` - at which the given geometry is valid

      `isGeodetic` - is a string that is either "TRUE" or "FALSE"

      Returns:
      TRUE if the two geometries interact; FALSE otherwise

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### isInside

          public boolean isInside(JGeometry A,
                                  double tolerance,
                                  java.lang.String isGeodetic)
                           throws java.lang.Exception

      This method determines if a 2D/3D Geometry is inside another 2D/3D Geometry. Both geometries have to have same dimension. If the geometry is Geodetic, pass in "TRUE" as the third parameter. The A geometry has to be any polygon or any solid.
      Parameters:
      `A` - Geometry that is any polygon or any solid (it cannot be any point/curve geometry)

      `tolerance` - at which the given geometry is valid

      `isGeodetic` - is a string that is either "TRUE" or "FALSE"

      Returns:
      TRUE if self is inside A; FALSE otherwise

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### isInside

          public boolean isInside(JGeometry A,
                                  double tolerance)
                           throws java.lang.Exception

      This method determines if a 2D/3D Geometry is inside another 2D/3D Geometry. Both geometries have to have same dimension. The A geometry has to be any polygon or any solid.
      Parameters:
      `A` - Geometry that is any polygon or any solid (it cannot be any point/curve geometry)

      `tolerance` - at which the given geometry is valid

      Returns:
      TRUE if this is inside A; FALSE otherwise

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### getCoordSysInfo

          public CoordSysInfo getCoordSysInfo()

      Returns a CoordSysInfo for the srid of this geometry (updating the sridCSI field if necessary).
      Returns:
      a CoordSysInfo for this geometry.

    <!-- -->

    - #### isGeodetic

          public boolean isGeodetic()

      Determine if the geometry is geodetic based on the SRID and coordinate system information.
      Returns:
      true if the geometry is longitude/latitude.

    <!-- -->

    - #### defaultTolerance

          public double defaultTolerance()

      Gives a tolerance that is appropriate for many use cases.
      Returns:
      an appropriate tolerance value

    <!-- -->

    - #### area

          public double area(double tolerance)
                      throws java.lang.Exception

      Compute the area of the geometry.
      Currently does the computation in a linear tangent plane for geodetic geometries, which is inaccurate for geometries city-sized or larger. This may change in a later release.

      Parameters:
      `tolerance` - value the geometry is valid at

      Returns:
      area in coodinate system units (squared), or m^2 for geodetic.

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### length

          public double length(double tolerance)
                        throws java.lang.Exception

      Compute the length + perimeter of the geometry (length of all curves plus perimeter of all polygons)
      Parameters:
      `tolerance` - value the geometry is valid at.

      Returns:
      length + perimeter in coordinate system units (meters for geodetic).

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### volume

          public double volume(double tolerance)
                        throws java.lang.Exception

      Compute the volume of the geometry. Returns 0 if geometry is not 3D. Only solid geometries have non-zero volume.
      Parameters:
      `tolerance` - value the geometry is valid at

      Returns:
      volume in coordinate system units (cubed), or m^3 if geodetic.

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### distance

          public double distance(JGeometry A,
                                 double tolerance,
                                 java.lang.String isGeodetic)
                          throws java.lang.Exception

      This method determines the distance between two 2D Geometries.
      Parameters:
      `A` - 2D Geometry that is a polygon or multi-polygon

      `tolerance` - non-negative tolerance at which the given geometry is valid

      `isGeodetic` - is a string that is either "TRUE" or "FALSE" (WGS84 assumed for geodetic)

      Returns:
      distance between the two given geometries. For projected data, the distance is in the same UNIT as the unit of projection. For Geodetic, the distance is in METERS.

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### distance

          public double distance(JGeometry A,
                                 double tolerance)
                          throws java.lang.Exception

      This method determines the distance between two 2D Geometries. If the geometries are Geodetic, pass in "TRUE" as the third parameter.
      Parameters:
      `A` - 2D Geometry that is a polygon or multi-polygon

      `tolerance` - non-negative tolerance at which the given geometry is valid

      Returns:
      distance between the two given geometries. For projected data, the distance is in the same UNIT as the unit of projection. For Geodetic, the distance is in METERS.

      Throws:
      `java.lang.Exception` - on error

    <!-- -->

    - #### getNurbsApprox

          public static JGeometry getNurbsApprox(JGeometry geom)
                                          throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### convexHull

          public JGeometry convexHull()
                               throws java.lang.Exception

      Returns the convex hull of the input geometry. Currently circular arcs and circles will be replaced with their MBR (this behaviour is consistent with the database). This may change in a future release.
      Processing is done as if the points were in the plane and may not be appropriate for geodetic geometries.

      Returns:
      convex hull

      Throws:
      `java.lang.Exception` - "13050: unable to construct empty spatial object" if input has no points (May in future return an empty geometry)

    <!-- -->

    - #### concaveHullDig

          public JGeometry concaveHullDig(double digN)
                                   throws java.lang.Exception

      Return the concave hull of the specified multipoint geometry.
      Uses the "dig" algorithm of Jin-Seo Park and Se-Jonh Oh, "A New Concave Hull Algorithm and Concaveness Measure for n-dimensional Datasets". Starting with a convex hull, interior points that are within (edge length)/digN of an edge will be added to the hull, "digging out" dents in the hull. Larger values of digN limit dents to be shallower.

      Input geometry must be points only. Processing is done as if the points were on the plane and may not be appropriate for geodetic pointsets.

      Parameters:
      `digN` - non-negative parameter to the dig algorithm; larger values result in less "digging" of concavities. A digN of 0 will dig until all points are on the hull. Good values are data dependent; try a value of 3.0 to start.

      Returns:
      resulting polygon

      Throws:
      `java.lang.Exception` - if the input points do not have a valid convex hull "13024: polygon has less than three segments" (convex hull is not a polygon) "13028: Invalid Gtype in the SDO_GEOMETRY object" (input is not a MULTIPOINT)

    <!-- -->

    - #### encodePolyline

          public static java.lang.String encodePolyline(double[] polyline)
                                                 throws java.lang.Exception

      Returns Google polyline encoding String for a series of 2D ordinates
      Parameters:
      `polyline` - polyline ordinates in an array of double (range \[-180,180\])

      Returns:
      Encoding String for the polyline

      Throws:
      `java.lang.Exception` - if ordinate is out of range, an Exception is thrown

    <!-- -->

    - #### decodePolyline

          public static double[] decodePolyline(java.lang.String encodedPolyline)

      Returns 2D polyline ordinates
      Parameters:
      `encodedPolyline` - Google polyline encoded format

      Returns:
      polyline ordinates as an array of double

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](J3D_Geometry.md)
- [Next Class](JGeometry.GeomParser.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
