------------------------------------------------------------------------

#### new Universe(config)

This class defines zoom levels, overall map bounds and spatial reference information
for the current mapping session. This contextual information is collectively called
a map Universe.
By default, a map universe is automatically derived from the tile layer
definition if there is one.

If the zoomLevels array is not specified, it will be automatically calculated
based on the following assumptions:

- numberOfZoomLevel sis specified and used to generated the zoom levels
- At zoom level 0, the full map extent is entirely contained in a single tile

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                             |
|----------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | The config specifies the Universe parameters. It can have the following attributes:<br><br>• srid {int} The map srid. Use an Oracle Spatial SRID value, e.g. 4326, 3785, 8307, 8265 etc.<br>• bounds {OM.geometry.Rectangle} The map bounds.<br>• zoomLevels {Array} An array of OM.universe.ZoomLevel. The map zoom level scheme.<br><br>• numberOfZoomLevels {int} The number of map zoom levels.<br> |

##### Returns:

The newly created Universe object,
or null if an error occurred.

Type
OM.universe.Universe

### Methods

------------------------------------------------------------------------

#### getMapBounds()

Get the map bounds. That is, the maximum map extent of this universe.

##### Returns:

The maximum map extent of this universe.

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getSRID()

Get the SRID for the map bounds.

##### Returns:

The SRID for the map bounds.

Type
int

------------------------------------------------------------------------

#### getZoomLevelNumber()

Get the number of defined zoom levels.

##### Returns:

The number of zoom levels.

Type
int

------------------------------------------------------------------------

#### getZoomLevels()

Get the map zoom level definitions array.

##### Returns:

An array of OM.universe.ZoomLevel.

Type
Array
