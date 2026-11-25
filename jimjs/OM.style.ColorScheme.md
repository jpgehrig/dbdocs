------------------------------------------------------------------------

#### new ColorScheme(config)

This class represents a color scheme or ramp that can be used for thematic
mapping of numeric or categorical data. A color scheme can be generated based
on a single hue (when only the baseColor is specified in the options parameter),
or span across multiple hues or colors (when both fromColor and toColor
are specified in the options parameter). If all three attributes: baseColor, fromColor and
toColor are specified, then only fromColor and toColor are used, resulting in
a multi-hue color scheme.

For single hue color schemes, the generated color stops become progressively
darker (with decreased brightness) starting with the base color.
For multi-hue color schemes, the generated color stops change their hue from
the fromColor to the toColor.

If you need greater control of how the color stops are generated, you may
programmatically create a set of OM.style.Color styles and pass them to a ColorScheme.

##### Parameters:

| Name     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `config` | Object | A configuration object for color scheme styles. It has the following<br>attributes:<br>• styleName {String} A style name<br>• styles {Array} An array of custom color styles (OM.style.Color) to be used as color stops;<br>if not specified, the color stops will be auto-generated based on<br>the baseColor or fromColor and toColor.<br>• numClasses {int} The number of buckets. Only used when generating equal-range buckets.<br>• defaultStyle {OM.style.Color} The default style. Used when a feature's attribute value does not fall within<br>any bucket.<br>• baseColor {String} The base fill color string for each bucket. Format is "#rrggbb"<br>• fromColor {String} The fromColor (or initial color) for a multi-hue color scheme. Format is "#rrggbb"<br>• toColor {String} The toColor (or final color) for a multi-hue color scheme. Format is "#rrggbb"<br>• stroke {String} The stroke color. Format is "#rrggbb"<br>• strokeThickness {float} The stroke width. Default value is 1.<br>• strokeOpacity {float} The stroke opacity. A value between 0 (transparent) and 1 (opaque).<br>Default is 1.<br>• fillOpacity {float} The fill opacity. A value between 0 (transparent) and 1 (opaque). Default is 1.<br>• buckets {Array} The buckets array. Each element in the array is a OM.style.Bucket<br>• classification {String} The value can be "equal" or "custom". If it's<br>"equal", all buckets are generated automatically.<br>• algorithm {function} The custom (user-defined) function to use to generate buckets<br>• isNumeric {Boolean} Whether the attributes values are numeric. Default is true. |

##### Returns:

An instance of OM.style.ColorScheme

Type
OM.style.ColorScheme

##### Example

    new OM.style.ColorScheme ({
      styleName: 'Tornados 2010',
      numClasses : 5,
      classification: 'equal', // 'custom',
      defaultStyle: style,
      baseColor: "#ff000000",
      fillOpacity: 0.5,
      stroke:"#000000",
      strokeOpacity:0.6,
      strokeThickness:1
    })

### Methods

------------------------------------------------------------------------

#### getColorStops()

A convenient method to return the list of generated colors.

##### Returns:

An array of colors in hex-strings.

Type
Array
