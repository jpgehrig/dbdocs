------------------------------------------------------------------------

#### new Glow(config)

This class represents a glow filter that can be applied to vector layers.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A configuration for glow filter. It can have these<br>attributes:<br>• color {String} The color of the glow. The string format is "#RRGGBB"<br>• strength {Number} The distance, in pixels, that a glow extends. Default value is 3.<br>• applyToLayer {boolean} When true, the filter is applied to the layer as a whole.<br>When false, the filter is applied to the individual features. Default is true. |

##### Returns:

An instance of OM.visualfilter.Glow

Type
OM.visualfilter.Glow

### Extends

- [OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md)
