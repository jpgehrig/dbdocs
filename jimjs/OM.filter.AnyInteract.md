------------------------------------------------------------------------

#### new AnyInteract(geom)

This is a spatial filter that implements the any-interact relationship. A
feature passes this filter if its geometry has any interaction (i.e. is not disjoint) with the
filter's geometry.

##### Parameters:

| Name   | Type                                            | Description            |
|--------|-------------------------------------------------|------------------------|
| `geom` | [OM.geometry.Geometry](OM.geometry.Geometry.md) | The filtering geometry |

##### Returns:

An instance of OM.filter.AnyInteract

Type
OM.filter.AnyInteract

### Extends

- [OM.filter.Filter](OM.filter.Filter.md)
