------------------------------------------------------------------------

#### new DropShadow(config)

This class represents a drop shadow that can be applied to vector layers.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | Configuration for drop shadow. It can have these<br>attributes:<br>• angle {int} The direction toward which the shadow is cast<br>(in degrees: \[0, 360\], clockwise). The default value is 45.<br>• color {String} The color of the shadow. The string format is "#RRGGBB"<br>• knockout {Boolean} If knockout is true, then the object to which the shadow<br>effect is applied knocks out the shadow where it overlaps, allowing the<br>background to show through.<br>• offset {float} The offset between the casted shadow and the object (in pixels).<br>The value should be a positive value. Default value is 2.<br>• opacity {float} The opacity of the shadow. A number between 0 and 1.<br>Default value is 0.5<br>• radius {float} Defines how hazy, or how blurry, the drop shadow is.<br>Default value is 2.<br>• applyToLayer {boolean} When true, the filter is applied to the layer as a<br>whole. When false, the filter is applied to the individual features. Default is true. |

##### Returns:

An instance of OM.effect.DropShadow

Type
OM.effect.DropShadow

### Extends

- [OM.visualfilter.VisualFilter](OM.visualfilter.VisualFilter.md)
