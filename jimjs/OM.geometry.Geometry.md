------------------------------------------------------------------------

#### new Geometry(srid)

Geometry is an abstract base class of all geometry types. All other geometry types
extend this class. It can be used to define all 2-d geometry types supported by Oracle
Spatial.

You should never create any direct instance of this class.

##### Parameters:

| Name   | Type | Description                                                                                             |
|--------|------|---------------------------------------------------------------------------------------------------------|
| `srid` | int  | The spatial reference identifier. Any SRID value that is valid for Oracle Spatial11g. e.g. 8307 or 4326 |

### Methods

------------------------------------------------------------------------

#### densify()

Densify a simple geodetic or projected linestring or polygon.

MapViewer renders geodetic shapes as if they are in a two-dimentional cartesian coordinate
system, in which longitude is the X axis and latitude is the Y axis. Oracle Spatial treats
such shapes differently and always takes the spherical shape of the Earth into consideration.
A straight line with two end points is straight when being rendered by MapViewer, while it
is an arc on the Earth surface when being processed by Spatial. As the result, the result
of a spatial query with a geodetic geometry as the filter might not match the geometry shape
rendered by MapViewer. The discrepency becomes prominent when the geodetic geometry spans
across a large area. Similar discrepency can be seen when the filtering geometry of the
spatial query is in a projected system and the data been queried is geodetic.

This method can be used to address this problem. It densifies a simple linestring
or polygon by linearly interpolating additional points into line segments that expand more
than 1 longitude degree. The densified geometry will result in minimal discrepency when being
rendered on the map and used in spatial queries.

You only need to call this method explicitly to get the densified geometry when the filter
geometry is used in a dynamic JDBC theme based vector layer. There is no need to call this method
for geometry query paremeters used with a predefined theme based vecotor layer.

##### Returns:

The densified geoemtry.

Type
OM.geometry.Geometry

------------------------------------------------------------------------

#### getArea()

Returns the signed area of this geometry. The result is in the
square unit of the geometry's coordinates.

Note that if the geometry is clockwise then the result is a positive area,
if it is counter clockwise then a negative result is returned.

------------------------------------------------------------------------

#### getLength()

Returns the total length of this geometry's segments. The result is in
the same unit as the geometry's coordinates.

------------------------------------------------------------------------

#### getMBR()

Get the minimum bounding rectangle (MBR) of the geometry object.

##### Returns:

The MBR of the geometry as a Rectangle object.

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getOrdinates()

Get the coordinates of the geometry object.

##### Returns:

the coordinates.

Type
Array

------------------------------------------------------------------------

#### getSRID()

Get the SRID of the geometry object.

##### Returns:

SRID.

Type
int

------------------------------------------------------------------------

#### getType()

Get the type of the geometry object.
The type string is one of the constants defined in OM.GeomTypes. e.g. "Point", "LineString", or "Polygon".

##### Returns:

geometry type.

Type
String

------------------------------------------------------------------------

#### toString()

This method is used to convert geometry object to a geoJSON compliant string.

------------------------------------------------------------------------

#### transform(toSrid, callBack, mcsURL, dataSource, optObj)

Transform a geometry from one coordinate system to another.
If the original SRID and destination SRID are one of following
values: 8307, 4326, 54004, 53004, 3785, and 3857, then the transformation will be
done at the client side.
Otherwise the map client sends a request to the map tile server, which invokes Oracle
Spatial utilities to perform coordinate system transformation and returns the
result to the client.

##### Parameters:

| Name         | Type     | Description                                                                                                                                                                                                                                  |
|--------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `toSrid`     | int      | The toSrid specifies the SRID of the destination coordinate system.                                                                                                                                                                          |
| `callBack`   | function | The call back function that is executed after the<br>coordinate system transformation is finished.                                                                                                                                           |
| `mcsURL`     | string   | An optional parameter that specifies the URL of the map tile<br>server to be used to perform the coordinate system transformation.<br>If this parameter is omitted, the map tile server associated<br>with the first map tile layer is used. |
| `dataSource` | String   | An optional parameter. It's the name of the MapViewer<br>data source inside which the server side length calculation is to be performed.<br>If omitted, the data source associated with the first map tile layer added is used.              |
| `optObj`     | Object   | An optional parameter, for example, {bdutil: bdutil}.                                                                                                                                                                                        |

##### Returns:

The resulting Geometry object when transformation in client. Null when
transformation in server side.

Type
OM.geometry.Geometry
