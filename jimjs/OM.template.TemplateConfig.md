------------------------------------------------------------------------

#### new TemplateConfig()

### Methods

------------------------------------------------------------------------

#### getConfig()

Returns the data of config.json as an Object

##### Returns:

The config.json data

Type
Object

------------------------------------------------------------------------

#### getStyle(name)

Given a style name, returns the corresponding style in the template file

##### Parameters:

| Name   | Type   | Description           |
|--------|--------|-----------------------|
| `name` | String | the name of the style |

##### Returns:

The style defined in the
template file.

Type
OM.Style

------------------------------------------------------------------------

#### getTileLayer(name)

Return the tile layer defined in the template file that corresponds to a
given name

##### Parameters:

| Name   | Type   | Description                                  |
|--------|--------|----------------------------------------------|
| `name` | String | The name of the tile layer we want to obtain |

##### Returns:

The tile layer (elocation, google, nokia, etc.)

------------------------------------------------------------------------

#### getVectorLayer(idName, name)

Given a distinushed or component name, find the corresponding vector layer.

##### Parameters:

| Name     | Type   | Description                                                                                      |
|----------|--------|--------------------------------------------------------------------------------------------------|
| `idName` | String | The name that will be assigned to the layer                                                      |
| `name`   | String | the name for the vector layer. It can be the distinushed name,<br>or one of the component names. |

##### Returns:

The vector layer that corresponds to the given name

Type
[OM.layer.VectorLayer](OM.layer.VectorLayer.md)

------------------------------------------------------------------------

#### initMap(map)

Given an OM.Map, load the initial components from the config.json file and add those
components to the map.

##### Parameters:

| Name  | Type                | Description                                      |
|-------|---------------------|--------------------------------------------------|
| `map` | [OM.Map](OM.Map.md) | The map that will add the template initial data. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### initVectorLayerList()

Returns the list of vector layers displayed during template initialization.

------------------------------------------------------------------------

#### tileLayerList()

Returns an array of strings with the name of the tile layers defined
in the template file

##### Returns:

An array of tile layers name

Type
Array

------------------------------------------------------------------------

#### vectorLayerList()

Return an array of strings with the name of the vector layers defined
in the template file

##### Returns:

An array of vector layers name

Type
Array
