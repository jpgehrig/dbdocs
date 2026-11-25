------------------------------------------------------------------------

#### new style.StyleStore()

### Methods

------------------------------------------------------------------------

#### \<static\> getServerSideStyle(dataSource, styleName, options)

This method gets a predefined style from the server and puts it into the style
cache if it is not already cached.

##### Parameters:

| Name         | Type   | Description                                                                                                                                                                                                                                                                                                                               |
|--------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `dataSource` | String | The data source name (e.g. "mvdemo")                                                                                                                                                                                                                                                                                                      |
| `styleName`  | String | The style name ("m.circle")                                                                                                                                                                                                                                                                                                               |
| `options`    | Object | It has two properties.<br>• url {String} The URL for the MapViewer instance. The default value is local domain.<br>It should be of the form "http://hostname:port/app_name" without the "/" at the end.<br>• callback {function} A function to handle the returned style.<br>The function must accept a parameter of type OM.style.Style. |

##### Returns:

. The callback function receives and handles the style.

Type
void
