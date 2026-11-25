------------------------------------------------------------------------

#### new OSMUniverse()

This class defines open street map zoom level scheme, overall map extent and spatial reference information.

##### Returns:

The newly created OSMUniverse object.

Type
OM.universe.OSMUniverse

### Extends

- [OM.universe.Universe](OM.universe.Universe.md)

### Methods

------------------------------------------------------------------------

#### getMapBounds()

Get the map bounds. That is, the maximum map extent of this universe.

Inherited From:
- [OM.universe.Universe#getMapBounds](OM.universe.Universe.md)

##### Returns:

The maximum map extent of this universe.

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getSRID()

Get the SRID for the map bounds.

Inherited From:
- [OM.universe.Universe#getSRID](OM.universe.Universe.md)

##### Returns:

The SRID for the map bounds.

Type
int

------------------------------------------------------------------------

#### getZoomLevelNumber()

Get the number of defined zoom levels.

Inherited From:
- [OM.universe.Universe#getZoomLevelNumber](OM.universe.Universe.md)

##### Returns:

The number of zoom levels.

Type
int

------------------------------------------------------------------------

#### getZoomLevels()

Get the map zoom level definitions array.

Inherited From:
- [OM.universe.Universe#getZoomLevels](OM.universe.Universe.md)

##### Returns:

An array of OM.universe.ZoomLevel.

Type
Array
