------------------------------------------------------------------------

#### new Template(options)

A template represents a set of logically related layers whose data are
readily available as web resources, with default styling already defined
for out of the box thematic mapping.

Physically, a template is typically a single folder with a set of geo-JSON data
files, plus a mandatory config.xml file that defines
all the aspects of the template.

A template provides these mapping related information:

- the universe to be used
- the list of layers available for display
- for vector layers, the actual geographic and attribute data are stored as JSON files.
- well-defined key(s) for each vector layer to facilitate easy thematic mapping
- the inherent hierachical relationship (if any) between the layers, for easy navigation/drill.
- A flexible layer naming convention defined by an LDAP-like directory.
- references to one or more tile layers (which are always externally hosted services)
- other metadata about the layers

##### Parameters:

| Name      | Type   | Description                                                                                                                                                      |
|-----------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | an optional configuration object. The supported<br>properties are:<br><br><br>• url: the url of the config.xml file<br><br>• name: the name of this template<br> |

### Methods

------------------------------------------------------------------------

#### getConfig()

Returns the TempalteConfig object associated with this template.
All the information about a template is managed by the config instance.

##### Returns:

the TemplateConfig associated with this template

Type
[OM.template.TemplateConfig](OM.template.TemplateConfig.md)

------------------------------------------------------------------------

#### getTileLayer(tileLayer)

Returns a specific tile layer defined in the config.json file

##### Parameters:

| Name        | Type   | Description                |
|-------------|--------|----------------------------|
| `tileLayer` | String | The name of the tile layer |

##### Returns:

The tile layer

------------------------------------------------------------------------

#### getVectorLayer(vectorLayerName, layerName, attrArr)

Gets the specified vector layer from the template. If the layer has not
been created, it will be created (from the template files). Application
is responsible for the life cycle of a VectorLayer returned from the template.
For instance, application can add it to the OM.Map instance to be displayed.
It can also register custom event listeners on the layer, or set NSDP data
set as well as custom rendering styles et al.

A Vector layer can be retrieved from the template using either the unique
name (DN), or any of the aliases (CNs). If the template defines default
styles for the layer, then these styles will be created and set on
the layer prior to returning it.

Furthermore, the attrName is an array of attibutes that selects only
a sub-set of the features in a layer. For instance, to get a vector layer
that contains only the states of California and Nevada, the layerName and attrName
parameter may look like "usa_states", \["California", "Nevada"\]. In this case the
result vector layer contains only the two features for California and Nevada.

##### Parameters:

| Name              | Type   | Description                                                                                      |
|-------------------|--------|--------------------------------------------------------------------------------------------------|
| `vectorLayerName` | String | The name that will be assigned to the layer                                                      |
| `layerName`       | String | The name of the layer in the config.json file that<br>will be used                               |
| `attrArr`         | Array  | An array of attributes, meaning that only the features<br>with those attributes will be selected |

##### Returns:

the layer

Type
[OM.layer.VectorLayer](OM.layer.VectorLayer.md)

------------------------------------------------------------------------

#### setupMapControls(map)

Setup a given map with the information in the template file

##### Parameters:

| Name  | Type   | Description                                       |
|-------|--------|---------------------------------------------------|
| `map` | String | The map that can be affected by the template info |

------------------------------------------------------------------------

#### switchTileLayer()

Switch to (or replace an existing one with) the specified tile layer.
