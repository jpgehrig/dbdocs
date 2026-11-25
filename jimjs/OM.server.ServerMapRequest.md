------------------------------------------------------------------------

#### new ServerMapRequest(url)

This class constructs a generic server map request to be sent to the server.
The instance, once created, will then be used to add or set attributes and properties to be used
to formulate the map request.
For example:

- baseURL="http://"+document.location.host+"/mapviewer";

- var req = new OM.server.ServerMapRequest(baseURL);

- req.addTheme(myTheme);

- req.setProperties({

- - dataSource:"mvdemo",
  - basemap: 'demo_map',
  - transparent:true,
  - antialiase:"false"
  - });

##### Parameters:

| Name  | Type   | Description                                                                                 |
|-------|--------|---------------------------------------------------------------------------------------------|
| `url` | String | The base URL of the mapviewer server. For example:<br><br>• http://localhost:8080/mapviewer |

##### Returns:

An instance of OM.layer.ServerMapRequest

Type
OM.layer.ServerMapRequest

### Methods

------------------------------------------------------------------------

#### addStyle(objStyle)

Add a style

##### Parameters:

| Name       | Type                    | Description       |
|------------|-------------------------|-------------------|
| `objStyle` | [OM.style](OM.style.md) | A OM.style object |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### addStyles()

Add styles from an array

##### Parameters:

| Type | Description |
|------|-------------|
|      |             |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### addTheme(objTheme)

Add a theme.

##### Parameters:

| Name       | Type   | Description                     |
|------------|--------|---------------------------------|
| `objTheme` | Object | A ServerPredefinedTheme object. |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### addThemes(arThemes)

Add an array of themes.

##### Parameters:

| Name       | Type  | Description                      |
|------------|-------|----------------------------------|
| `arThemes` | array | An array of ServerTheme objects. |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### getTheme(themeName)

Get the theme instance, null if not found.

##### Parameters:

| Name        | Type   | Description      |
|-------------|--------|------------------|
| `themeName` | String | The theme's name |

##### Returns:

a theme object that has the given name; null if not found.

------------------------------------------------------------------------

#### getThemes()

Get array of themes in the server map request instance.

##### Returns:

themes object array

Type
array

------------------------------------------------------------------------

#### hasTheme(name)

##### Parameters:

| Name   | Type  | Description                   |
|--------|-------|-------------------------------|
| `name` | Sring | The theme name to search for. |

##### Returns:

return true if a theme with the given name found; false otherwise.

Type
Boolean

------------------------------------------------------------------------

#### setBasemap(basemap)

Set the basemap name

##### Parameters:

| Name      | Type   | Description      |
|-----------|--------|------------------|
| `basemap` | String | The basemap name |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setBBox(minx, miny, maxx, maxy, srid)

Set the bounding box

##### Parameters:

| Name   | Type | Description               |
|--------|------|---------------------------|
| `minx` | type | The minimum x             |
| `miny` | type | The minimum Y             |
| `maxx` | type | The maximum x             |
| `maxy` | type | The maximum y             |
| `srid` | type | The srid. Defautl is 8307 |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setBindingParameters(layerbp)

Set each theme's binding parameters

##### Parameters:

| Name      | Type  | Description                                                                                                                                                                                                                                                                                                            |
|-----------|-------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `layerbp` | array | an array of JSON objects. Each JSON object has a key and value<br>pair. The key is a theme's name. The value is binding parameters, an array of JSON object containing binding parameters.<br>For example, a layerbp may look like:<br>\[{'WIND_THEME', \[{value:0.0, type:'Double'}, {value:'CA', type:'String'}\]}\] |

##### Returns:

a theme object that has the given name; null if not found.

------------------------------------------------------------------------

#### setClientTileRequest(flag)

Set the client tile request flag.

##### Parameters:

| Name   | Type    | Description                                  |
|--------|---------|----------------------------------------------|
| `flag` | Boolean | The client tile request flag, true or false. |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setEnableUTFGrid(flag)

Set the flag to enable or disable the utfgrid generation

##### Parameters:

| Name   | Type    | Description            |
|--------|---------|------------------------|
| `flag` | Boolean | Boolean, true or false |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setImageFormat(format)

Set the map image format

##### Parameters:

| Name     | Type   | Description                                       |
|----------|--------|---------------------------------------------------|
| `format` | String | The map image format, such as PNG_STREAM, PNG_URL |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setImageHeight(w)

##### Parameters:

| Name | Type | Description     |
|------|------|-----------------|
| `w`  | int  | The image width |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setImageWidth(w)

##### Parameters:

| Name | Type | Description     |
|------|------|-----------------|
| `w`  | int  | The image width |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setMapServerURL(url)

Set the map server URL

##### Parameters:

| Name  | Type   | Description                                                      |
|-------|--------|------------------------------------------------------------------|
| `url` | string | The map server url. For example, http://localhost:8080/mapviewer |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setProperties(props)

Set attributes needed by a map request

##### Parameters:

| Name    | Type   | Description                                                    |
|---------|--------|----------------------------------------------------------------|
| `props` | object | A JSON object containing attributes related with a map request |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setUTFGridResolution(res)

Set the UTFGrid resolution

##### Parameters:

| Name  | Type    | Description                                           |
|-------|---------|-------------------------------------------------------|
| `res` | Integer | The utfgrid resolution. Typical values are 2, 4, or 8 |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### toXMLString()

Build an XML map request string

##### Returns:

Type
String

------------------------------------------------------------------------

#### toXMLString_Themes(mapArea)

##### Parameters:

| Name      | Type                                              | Description                                                                                                                                                                                 |
|-----------|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mapArea` | [OM.geometry.Rectangle](OM.geometry.Rectangle.md) | Optional parameter with the request map area. In general it is null.<br>Currently applies just for server GeoRaster class to be used on a binding parameter of type 'Tile_mbr' if it exits. |

##### Returns:

The XML string for themes

Type
String
