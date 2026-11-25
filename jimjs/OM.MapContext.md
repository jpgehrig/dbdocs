------------------------------------------------------------------------

#### new MapContext()

Use OM.Map.getMapContext() to get the map context instance to invoke its methods.

This is a convenience class which contains the essential contextual information related to the
current map instance, such as universe, current center point and zoom level
etc.

Note that instances of this class are always automatically constructed
and stored as a field of a OM.Map instance for easy access in an
event listener or map decoration.

### Methods

------------------------------------------------------------------------

#### getCenterPoint()

##### Returns:

The current center point.

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getDeviceHeight()

##### Returns:

height The device height

Type
Number

------------------------------------------------------------------------

#### getDeviceWidth()

##### Returns:

width The device width

Type
Number

------------------------------------------------------------------------

#### getDeviceWindow()

##### Returns:

The device window

Type
Object

------------------------------------------------------------------------

#### getPreviousCenterPoint()

##### Returns:

The previous center point.

Type
[OM.geometry.Point](OM.geometry.Point.md)

------------------------------------------------------------------------

#### getPreviousZoomLevel;()

##### Returns:

The previous zoom level.

Type
Number

------------------------------------------------------------------------

#### getQueryWindow()

##### Returns:

queryWindow The query window

Type
[OM.geometry.Rectangle](OM.geometry.Rectangle.md)

------------------------------------------------------------------------

#### getUniverse()

##### Returns:

The universe currently in use.

Type
[OM.universe.Universe](OM.universe.Universe.md)

------------------------------------------------------------------------

#### getZoomLevel()

##### Returns:

The current zoom level.

Type
Number
