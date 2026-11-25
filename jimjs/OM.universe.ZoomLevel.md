------------------------------------------------------------------------

#### new ZoomLevel(resolution, options)

The zoom level scheme of the map is usually the same as that of the tile layer, in which case the application
does not need to explicitly set the zoom level scheme. The application needs to invoke this method only when
the map has multiple tile layers and the zoom level schemes of the tile layers are different.

##### Parameters:

| Name         | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `resolution` | double | Map resolution (map units per pixel).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `options`    | Object | The config specifies the Universe parameters. It can have the following attributes.<br><br>• stretchRatio {float} Optional. stretchRatio is used only when map's vertical resolution and horizontal<br>resolution are different. The map's horizontal resolution is always specified by<br>the resolution attribute. The vertical resolution is calculated by multiplying<br>the map's horizontal resolution by stretchRatio.<br>The default value of this attribute is 1.<br><br>• infotip {String} The info string displayed when the mouse hovers on the navigation panel zoom slider.<br> |

##### Returns:

The newly created ZoomLevel object.

Type
OM.universe.ZoomLevel
