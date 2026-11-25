A static class that holds various configuration properties that are shared
among multiple Map instances on the same page.

In most cases an application should only make changes to these public properties
before it creates the first instance of OM.Map.

### Members

------------------------------------------------------------------------

#### \<static\> unitFactors

Constants defining distance units and their conversion factors

### Methods

------------------------------------------------------------------------

#### \<static\> addCSTransformFunction(fromSrid, toSrid, func)

Add a custom coordinate system transform function.

##### Parameters:

| Name       | Type     | Description             |
|------------|----------|-------------------------|
| `fromSrid` | int      | Original SRID.          |
| `toSrid`   | int      | Target SRID.            |
| `func`     | function | The transform function. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### \<static\> addSRS(t, u, s)

Add a customSpatial Reference System definition.

##### Parameters:

| Name | Type   | Description                                                            |
|------|--------|------------------------------------------------------------------------|
| `t`  | string | type of the custom SRS, possible values are 'GEODETIC' and 'PROJECTED' |
| `u`  | string | The unit for the current srid.                                         |
| `s`  | number | The srid for the custom SRS.                                           |

------------------------------------------------------------------------

#### \<static\> enableFeatureDragging()

Control whether an editable feature is draggable.
Default value is true.
Note that this flag is ignored for point features which are always
draggable.

##### Parameters:

| Name    | Type    | Description |
|---------|---------|-------------|
| `flag.` | Boolean |             |

##### Returns:

Type
void

------------------------------------------------------------------------

#### \<static\> enableProxy()

Enable (if flag = true) or disable (flag = false) the use of the proxy servlet.

##### Parameters:

| Name    | Type    | Description                                                  |
|---------|---------|--------------------------------------------------------------|
| `flag.` | boolean | Proxy servlet use is enabled if true and disabled otherwise. |

------------------------------------------------------------------------

#### \<static\> featureDragDisabled(feature)

Checks if dragging a whole feature is disabled.
Note that this is typically controlled via the global var OM.gv.featureDrag.
For point features dragging will always be enavled

##### Parameters:

| Name      | Type                        | Description               |
|-----------|-----------------------------|---------------------------|
| `feature` | [OM.Feature](OM.Feature.md) | the feature to be checked |

##### Returns:

returns true if feature dragging is disabled.

Type
boolean

------------------------------------------------------------------------

#### \<static\> getBaseMapViewerURL()

Get the URL to the MapViewer instance

##### Returns:

the MapViewer URL

Type
string

------------------------------------------------------------------------

#### \<static\> getImgResourcePath()

Returns the URL path at which the various resources (images) for this
library can be found.

##### Returns:

the base URL path for loading required resources such as images.

Type
String

------------------------------------------------------------------------

#### \<static\> getProxyPath()

Get the proxy servlet path.

##### Returns:

The proxy servlet path.

Type
string

------------------------------------------------------------------------

#### \<static\> getUseRTree()

Determine whether an im-memory R-Tree is being used index features in a vector layer

##### Returns:

Returns true is an in-memory R-Tree index is being used.

Type
Boolean

------------------------------------------------------------------------

#### \<static\> isSecureHTTPEnabled()

Check if Secure HTTP is enabled

##### Returns:

true is HTTPS is being used false if HTTP is being used.

Type
boolean

------------------------------------------------------------------------

#### \<static\> setBaseMapViewerURL(mvUrl)

Set the full URL to the base MapViewer instance. The base MapViewer is where
the API will go to resolve references to server-side pre-defined styles, themes and tile layers. For instance if a
MapViewer URL is not explicitly specified when adding a pre-defined vector layer,
then the API will attempt to load the layer from the base MapViewer.
It is also where the client API will send spatial coordinate transformation requests if the
particular transformation is not supported in the client.
The default value is set to document.location.protocol + "//"+document.location.host+"/mapviewer".

##### Parameters:

| Name    | Type   | Description                                                                                          |
|---------|--------|------------------------------------------------------------------------------------------------------|
| `mvUrl` | String | the complete URL to the base MapViewer. It must start<br>with http or https and end with /mapviewer. |

------------------------------------------------------------------------

#### \<static\> setHttpMethod(method)

By default Oracle Maps will use http POST to send requests.
Use this method to change it to GET if needed.

##### Parameters:

| Name     | Type   | Description            |
|----------|--------|------------------------|
| `method` | String | Either "POST" or "GET" |

------------------------------------------------------------------------

#### \<static\> setLogLevel(level)

Set the global logging level. Must be one of the following values ordered by
their increasing priority or severity:
"finest", "finer", "fine", "info", "config", "warning", and "severe".

Internal log messages logged at a priority below the set level will not be
displayed in the browser console.

##### Parameters:

| Name    | Type   | Description                          |
|---------|--------|--------------------------------------|
| `level` | string | The global logging level to be used. |

------------------------------------------------------------------------

#### \<static\> setProxyPath(path)

Set the proxy servlet path.

##### Parameters:

| Name   | Type   | Description                                            |
|--------|--------|--------------------------------------------------------|
| `path` | string | The proxy servlet path. Default is "/mapviewer/proxy". |

##### Returns:

Type
null

------------------------------------------------------------------------

#### \<static\> setResourcePath(newPath)

By default Oracle Maps looks for all the required image and css files in
the "images" and "css" folders under the relative URL path "/mapviewer/jslib/v2/".
Use this method to change the resource path, provided all the resources
can be found using the same name and (if applicable) same sub-folder.

##### Parameters:

| Name      | Type   | Description                                       |
|-----------|--------|---------------------------------------------------|
| `newPath` | String | the new URL path for the image and css resources. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### \<static\> setSecureHttp(flag)

Specify whether HTTPS or HTTP should be used when loading external tiles or images Default is "http:".
If flag is true https will be used for all URLs.
Affects how resources (icons, images) and external map tile from services such as Here, Bing, and Oracle are loaded.

##### Parameters:

| Name   | Type    | Description                                                          |
|--------|---------|----------------------------------------------------------------------|
| `flag` | Boolean | if "true" protocol is "https" else "http". Default value is "false". |

##### Returns:

Type
void

------------------------------------------------------------------------

#### \<static\> setShowManipulator()

Control whether an editable feature will show its manipulator.
Default value is true.

##### Parameters:

| Name    | Type    | Description |
|---------|---------|-------------|
| `flag.` | Boolean |             |

##### Returns:

Type
void

------------------------------------------------------------------------

#### \<static\> setTabIndexEnabled(flag)

If flag is "true" then the attribute "tabindex='1'" will be add to the map's DIV container so that it can be focused.
Default value is true.

##### Parameters:

| Name   | Type    | Description                  |
|--------|---------|------------------------------|
| `flag` | Boolean | if "true" tabindex=1 is set. |

##### Returns:

Type
void

------------------------------------------------------------------------

#### \<static\> setTouchMoveThreshold()

Specify the threshold so a tap will not move the map

##### Parameters:

| Name      | Type    | Description |
|-----------|---------|-------------|
| `pixels.` | Integer |             |

##### Returns:

Type
null

------------------------------------------------------------------------

#### \<static\> setUseRTree()

Specify whether to use an im-memory R-Tree to index features in a vector layer

##### Parameters:

| Name    | Type    | Description                    |
|---------|---------|--------------------------------|
| `flag.` | Boolean | Use an R-Tree if flag is true. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### \<static\> useSecureHTTP(flag)

Specify whether HTTPS (Secure) or HTTP should be used when loading external tiles or images Default is "http:".
If flag is true https will be used for all URLs.
Affects how resources (icons, images) and external map tile from services such as Here, Bing, and Oracle are loaded.

##### Parameters:

| Name   | Type    | Description                                      |
|--------|---------|--------------------------------------------------|
| `flag` | Boolean | if true https else http. Default value is false. |

##### Returns:

Type
void
