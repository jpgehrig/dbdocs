------------------------------------------------------------------------

#### new InsidePolygon(geom)

This is a filter class that tests if a feature's geometry is inside the specified
filter polygon.

##### Parameters:

| Name   | Type                                            | Description         |
|--------|-------------------------------------------------|---------------------|
| `geom` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | The filter geometry |

##### Returns:

An instance of OM.filter.InsidePolygon

Type
OM.filter.InsidePolygon

### Extends

- [OM.filter.Filter](OM.filter.Filter.md)

### Methods

------------------------------------------------------------------------

#### pointInPolygon(mx, my, polygon)

checks whether point (mx,my) is inside the specified polygon.

##### Parameters:

| Name      | Type   | Description          |
|-----------|--------|----------------------|
| `mx`      | number | x-value of the poing |
| `my`      | number | y-value of the point |
| `polygon` | Object | the polygon          |
