------------------------------------------------------------------------

#### new ServerTheme(name, type)

Construct a new theme definition. Currently only a predefined theme (i.e. ServerPredefinedTheme) is supported.
This is an abstract base class, so always use a concrete sub-class such as ServerPredefinedTheme to create
a ServerTheme instance.

##### Parameters:

| Name   | Type   | Description                                                        |
|--------|--------|--------------------------------------------------------------------|
| `name` | String | The name of the theme to be created.                               |
| `type` | String | The type (e.g. 'predefined' or 'jdbc') of the theme to be created. |

### Methods

------------------------------------------------------------------------

#### getDataSourceName()

Get the current MapViewer data source name.

##### Returns:

returns the name of the data source.

Type
String

------------------------------------------------------------------------

#### setDataSourceName(dsrcName)

Set the name of the MapViewer data source where this theme is
defined.

##### Parameters:

| Name       | Type   | Description                            |
|------------|--------|----------------------------------------|
| `dsrcName` | String | The name of the MapViewer data source. |

------------------------------------------------------------------------

#### setName(nm)

Set the theme name

##### Parameters:

| Name | Type   | Description           |
|------|--------|-----------------------|
| `nm` | String | The theme name to set |
