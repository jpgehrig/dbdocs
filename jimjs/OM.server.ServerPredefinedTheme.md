------------------------------------------------------------------------

#### new ServerPredefinedTheme(name)

Construct a definition of a predefined theme that exists in a MapViewer datasource. For example:

- var stateTheme = new OM.server.ServerPredefinedTheme('THEME_DEMO_STATES');


Such a theme instance may be added into a server map request instance.
For example:

- var req = new OM.server.ServerMapRequest(baseURL);
- req.addTheme(stateTheme);

##### Parameters:

| Name   | Type   | Description                                                                                                                                           |
|--------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | String | The name of the predefined theme; a theme<br>with this name must exist in the MapViewer metadata view of the datasource to which the request is sent. |

### Extends

- [OM.server.ServerTheme](OM.server.ServerTheme.md)

### Methods

------------------------------------------------------------------------

#### getDataSourceName()

Get the current MapViewer data source name.

Inherited From:
- [OM.server.ServerTheme#getDataSourceName](OM.server.ServerTheme.md)

##### Returns:

returns the name of the data source.

Type
String

------------------------------------------------------------------------

#### setBindingParameters(bParams)

Set the binding parameters. It is an array of {value, type} objects, e.g.
\[
{value: loss_min, type: 'Double'},
{value: loss_max, type: 'Double'},
{value: croploss_min, type: 'Double'},
{value: croploss_max, type: 'Double'},
{value: fat_min, type: 'Double'},
{value: fat_max, type: 'Double'},
{value: inj_min, type: 'Double'},
{value: inj_max, type: 'Double'}
\]
The order and number of the parameter objects in the array must match those in the predefined theme in MapViewer theme metadata.

##### Parameters:

| Name      | Type  | Description                                              |
|-----------|-------|----------------------------------------------------------|
| `bParams` | Array | An array of bind parameter (i.e. {value, type}) objects. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setDataSourceName(dsrcName)

Set the name of the MapViewer data source where this theme is
defined.

##### Parameters:

| Name       | Type   | Description                            |
|------------|--------|----------------------------------------|
| `dsrcName` | String | The name of the MapViewer data source. |

Inherited From:
- [OM.server.ServerTheme#setDataSourceName](OM.server.ServerTheme.md)

------------------------------------------------------------------------

#### setName(nm)

Set the theme name

##### Parameters:

| Name | Type   | Description           |
|------|--------|-----------------------|
| `nm` | String | The theme name to set |

Inherited From:
- [OM.server.ServerTheme#setName](OM.server.ServerTheme.md)

------------------------------------------------------------------------

#### toXMLString()

Convert the theme definition into a \<theme\> element string that is
compliant with the MapViewer XML Request API.

##### Returns:

The XML \<theme\> string for this pre-defined theme.

Type
String
