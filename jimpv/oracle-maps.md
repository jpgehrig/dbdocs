Oracle Maps is the name for a suite of technologies for developing high-performance interactive web-based mapping applications.

Oracle Maps is included with the map visualization component.

The map visualization component allows users who have a valid license and comply with map tile providers’ Terms of Use to display map tiles from those licensed services.

- Oracle Maps JavaScript API
  The Oracle Maps JavaScript client is a browser-based map visualization engine that works on top of the map tile server and that uses HTML5 technology.
- Developing Oracle Maps Applications
  This topic describes how to develop Oracle Maps applications.
- Using Google Maps
  Applications can display Google Maps tiles as a built-in map tile layer, by creating and adding to the map window an instance of `MVGoogleTileLayer` .
- Transforming Data to a Spherical Mercator Coordinate System
  Popular online map services such as Google Maps use a spherical Mercator projection for their maps.
- Using Dynamic Tile Layers
  A dynamic tile layer is a tile layer defined on the client side.

### 4.1 Oracle Maps JavaScript API

The Oracle Maps JavaScript client is a browser-based map visualization engine that works on top of the map tile server and that uses HTML5 technology.

It implements the following functions:

- Fetching map tiles from the map tile server and displaying them as a map tile layer in the web browser.

- Controlling user interaction, such as dragging for map navigation, clicking features, drawing rectangles, and redlining.

  Drawing a rectangle refers to the application user creating a rectangle by clicking and holding the mouse button at one corner of the rectangle, dragging the mouse to the diagonally opposite corner, and releasing the mouse button.

  Redlining refers to the application user creating a polygon or polyline by clicking the mouse button and then moving the mouse and clicking multiple times, with each click extending the redline by a straight line. (Redline drawings are often rendered in red, although you can specify a line style that uses any color.)

To access these functions, use the JavaScript API, which consists of several JavaScript classes. For detailed information about all classes in the Oracle Maps JavaScript API ), see the Javadoc-style reference documentation, which is included in the `mvdemo.ear` file and is available at the following location: `http://``host:port``/mvdemo/api/oracle_maps_html5_api.jsp`

Tutorials and demos for the API are available as a standalone packaged application with the root context path `/mvdemo`. The tutorials start with the basics (display a map tile layer, add a navigation panel, display interactive features and information windows) and move on to more complex topics such as registering event listeners, programmatically creating and using styles, and spatial filtering.

The tutorials are all based on the MVDEMO sample data set (available from the [map visualization component page](https://www.oracle.com/database/technologies/spatial-studio/spatial-graph-map-vis-downloads.html) on the Oracle Technology Network) and assume a data source named `mvdemo`. The tutorial page has three panels. The left one lists the sample code, or demo, titles. Click on one and a map, or the result of executing that sample code, is displayed in the top right panel. The bottom panel has tabs titled JavaScript and HTML, which respectively show the JavaScript and HTML code fragments for the selected demo.

- About the Oracle Maps JavaScript API

**Parent topic:** Oracle Maps

#### 4.1.1 About the Oracle Maps JavaScript API

The Oracle Maps JavaScript API takes advantage of the capabilities of modern browsers and HTML5. Some of its features include:

- Built-in support of various third party map tile services, such as maps.oracle.com, Nokia Maps, OpenStreet Maps, and other mapping service providers

- Rich client side rendering of geospatial data with on-the-fly application of rendering styles and effects such as gradients, animation, and drop-shadows

- Autoclustering of large number of points and client side heat map generation

- Client side feature filtering based on attribute values as well as spatial predicates (query windows)

- A rich set of built-in map controls and tools, including a customizable navigation bar and information windows, configurable layer control, and red-lining and distance measurement tools

Existing server-side predefined styles and themes will work with the API. For example, the following code snippet creates an interactive vector layer based on a predefined theme `mvdemo.customers`, which has an associated predefined style:

    var baseURL  = "http://"+document.location.host+"/mapviewer";
    var layer = new OM.layer.VectorLayer("layer1",
     {
         def:{
                    type:OM.layer.VectorLayer.TYPE_PREDEFINED,
                    dataSource:"mvdemo",
                    theme:"customers",
                    url: baseURL
                }
      });

The API has the following top-level classes and subpackages, all of which are in the namespace `OM`:

- The `Map` class is the main class of the API.

- The `Feature` class represents individual geo features.

- The `MapContext` class a top-level class encapsulating some essential contextual information, such as the current map center point and zoom level. It is typically passed into event listeners.

- The `control` package contains all the map controls, such as navigation bar and overview map.

- The `event` package contains all the map and layer event classes.

- The `filter` package contains all the client-side filters (spatial or relational) for selecting, or subsetting, the displayed vector layer features.

- The `geometry` package contains various geometry classes.

- The `layer` package contains various tile and vector layer classes. The tile layer classes include access to a few online map services such as Oracle, Nokia, and OpenStreetMap. The vector layers are interactive feature layers.

- The `infowindow` package contains the customizable information windows and their styles.

- The `style` package contains styles applicable to vector data on the client side. It also includes visual effects such as animation, gradients, and drop shadows.

- The `tool` package contains various map tools such as for distance measuring, red-lining, and geometry drawing.

- The `universe` package contains built-in, or predefined, map universes. A map universe defines the bounding box and set of zoom level definitions for the map content.

- The `util` package contains various utility classes.

- The `visualfilter` package provides an interface for the various visual effects, such as gradients and drop shadows.

`OM.Map` is the main entry class for all map operations inside the web browser. This and other classes provide interfaces for adding application-specific logic, operations, and interactivity in web mapping applications. The application logic and operations can include the following:

- Create a map client instance and associate it with the map container DIV object created in the web page.

- Configure map parameters such as map center and map zoom level.

- Optionally, create and manipulate map tile layers. A map tile layer is not required. An application can have only interactive vector layers using a custom Universe that programmatically defines the zoom levels and scales.

- Create and manipulate vector layers.

- Display an information window on the map.

- Create fixed map decorations, such as a map title, a copyright note, and map controls.

- Access built-in utilities such as a navigation panel, rectangle or circle tool, scale bar, and overview map panel.

- Use event listeners to customize event handling and thus map interactions.

Other notes and considerations on using the Oracle Maps API:

- The "FOI server" in a previous version of the API is now a data server that streams the vector geometries and attributes for features to the client for local rendering. Therefore, the "FOI layers" in a previous version are now called vector layers.

- A background map tile layer is not required in order to display interactive vector layers. For example, an application can display a thematic map of states (such as color-filled by population quintile) with no background tile layer.

- The API depends on and includes `JQuery` and `JQueryUI`. So, `oraclemapsv2.js` includes `jquery-1.7.2.min.js` and `jquery-ui-1.8.16.min.js`. If your application also uses JQuery and JQueryUI and includes them already, then use the file `oraclemapsv2_core.js` in the `<script>` tag instead to load the Oracle Maps library. That is, use the following:

  `<script src="/mapviewer/jslib/v2/oraclemapsv2_core.js"></script>`

  instead of:

  `<script src="/mapviewer/jslib/v2/oraclemapsv2.js"></script>`

For information about developing applications using the API, see Developing Oracle Maps Applications and the Oracle-supplied tutorials and demos.

**Parent topic:** Oracle Maps JavaScript API

### 4.2 Developing Oracle Maps Applications

This topic describes how to develop Oracle Maps applications.

If the underlying base map and layers are managed in an Oracle database, each map tile layer displayed in the client application must have a corresponding database metadata entry in the USER_SDO_CACHED_MAPS metadata view (described in [xxx_SDO_CACHED_MAPS Views](map-visualization-concepts.md)) . Similarly, if an interactive layer is based on database content, it must have a metadata entry in the USER_SDO_THEMES view (described in [Map Visualization Component Metadata Views](map-visualization-concepts.md), especially [xxx_SDO_THEMES Views](map-visualization-concepts.md)). These tile and interactive layers, and the styles and styling rules for them, can be defined using the Map Builder tool (described in [Oracle Map Builder Tool](oracle-map-builder-tool.md)).

To develop Oracle Maps applications using the API, follow these basic steps:

1.  Import the `oraclemapsv2.js` library.

    The API is provided in a single JavaScript library packaged as part of the map visualization component EAR archive.

2.  After the map visualization component is deployed and started, load the library through a `<script>` tag, for example:

        <script  type="text/javascript" url="http://localhost:8080/mapviewer/jslib/v2/oraclemapsv2.js"/>

    **Note:**

    If you need a specific jQuery version other than the one packaged in `oraclemapsv2.js` (shown in the preceding example), then you can add your preferred jQuery first, followed by a list of libraries. For example:

        <script src="your_preferred_jQuery_library_listed_here_first.js "></script>
        <script src="v2/jquery/jquery.hammer-full.min.js"></script>
        <script src="v2/jquery/jquery.i18n.properties-min-1.0.9.js"></script>
        <script src="v2/jquery/jquery.mousewheel.min.js"></script>
        <script src="v2/rtree/rtree-min.js"></script>
        <script src="v2/fortknox-libs/fortknox-canvas.js"></script>
        <script src="v2/oraclemapsv2_core.js"></script>

3.  Create a `<DIV>` tag in the HTML page, which will contain the interactive map.

4.  Create a client-side map instance that will handle all map display functions.

    The class is named `OM.Map` and is the main entry point of the API.

5.  Set up a map universe (unless you also do the optional next step).

    A map universe basically defines the overall map extent, the number of zoom levels, and optionally the resolution (in map units per pixel) at each zoom level. Note that a predefined tile layer is not necessary in order to display interactive vector layers or themes. For example, an interactive thematic map of sales by region does not need to have a background map, or tile layer.

6.  (Optional) Add a tile layer that serves as the background map.

    The tile layer can be from the database, such as `mvdemo.demo_map`, or from a supported service, such as Nokia Maps. Adding a tile layer also implicitly defines a map universe, and therefore the preceding step (setting up a map universe) is not necessary in this case.

7.  Add one or more interactive vector layers.

    `OM.VectorLayer` uses HTML5 (Canvas or SVG) technology to render all the data in the browser. So, unless specified otherwise, all vector layer content is loaded once and there are no subsequent database queries, or data fetching, on map zoom or pan operations.

8.  Add one or more map controls, tools, and other application-specific UI controls so that users can set the displayed layers, styling, and visual effects.

If you need to prevent themes from being streamed by default, you must protect them is by adding authentication, that is, by adding a security constraint in the map visualization component `web.xml` file and by configuring the `mds.xml` file to authorize access to various themes. For information, see [Configuring and Securing the Map Data Server for the HTML5 API](introduction-to-map-visualization-component.md).

For detailed instructions and related information about using the API, see the Oracle-supplied tutorials and demos.

- Creating the Client Application with the API

**Parent topic:** Oracle Maps

#### 4.2.1 Creating the Client Application with the API

Oracle Maps applications run inside web browsers and require only HTML5 (Canvas) support and JavaScript enabled. No additional plugins are required.

The source for an Oracle Maps application is typically packaged in an HTML page, which consists of the following parts:

- A `<script>` element that loads the Oracle Maps client library into the browser's JavaScript engine. For example:

      <script src="/mapviewer/jslib/v2/oraclemapsv2.js"></script>

- An HTML `` element that will contain the map. For example:



- JavaScript code that creates the map client instance and sets the initial map content (tile and vector layer), the initial center and zoom, and map controls. This code should be packaged inside a function which is executed when the HTML page is loaded or ready. The function is specified in the `onload` attribute of the `<body>` element of the HTML page. For example:

      function on_load_mapview()
      {
        var baseURL  = "http://"+document.location.host+"/mapviewer";
        // Create an OM.Map instance to display the map
        var mapview = new OM.Map(document.getElementById("map"),
                                 {
                                   mapviewerURL:baseURL
                                 });
        // Add a map tile layer as background.
        var tileLayer = new OM.layer.TileLayer(
              "baseMap",
              {
                  dataSource:"mvdemo",
                  tileLayer:"demo_map",
                  tileServerURL:baseURL+"/mcserver"
              });
        mapview.addLayer(tileLayer);
        // Set the initial map center and zoom level
        var mapCenterLon = -122.45;
        var mapCenterLat = 37.7706;
        var mapZoom = 4;
        var mpoint = new OM.geometry.Point(mapCenterLon,mapCenterLat,8307);
        mapview.setMapCenter(mpoint);
        mapview.setMapZoomLevel(mapZoom);
        // Add a theme-based FOI layer to display customers on the map
        customersLayer = new OM.layer.VectorLayer("customers",
              {
                  def:
                      {
                      type:OM.layer.VectorLayer.TYPE_PREDEFINED,
                      dataSource:"mvdemo", theme:"customers",
                      url: baseURL,
                      loadOnDemand: false
                      }
              });
        mapview.addLayer(customersLayer);
        // Add a navigation panel on the right side of the map
        var navigationPanelBar = new OM.control.NavigationPanelBar();
        navigationPanelBar.setStyle(
      {backgroundColor:"#FFFFFF",buttonColor:"#008000",size:12});
        mapview.addMapDecoration(navigationPanelBar);
        // Add a scale bar
        var mapScaleBar = new OM.control.ScaleBar();
        mapview.addMapDecoration(mapScaleBar);
        // Display the map.
        // The initialization and display is done just once.
        mapview.init();
      }

- Additional HTML elements and JavaScript code that implement other application-specific user interface and control logic. For example, the HTML `<input>` element and JavaScript function `setLayerVisible` together implement a layer visibility control. The `setLayerVisible` function is coded as follows:

      function setLayerVisible(checkBox)
      {
        // Show the customers vector layer if the check box is checked and
        // hide it otherwise.
        if(checkBox.checked)
          customersLayer.setVisible(true) ;
        else
          customersLayer.setVisible(false);
      }

  The function is specified in the `onclick` attribute of the `<input>` element defining the checkbox. In the following example, the function is executed whenever the user clicks on the Show Customers check box:

      <INPUT TYPE="checkbox" onclick="setLayerVisible(this)" checked/>Show Customers

**Parent topic:** Developing Oracle Maps Applications

### 4.3 Using Google Maps

Applications can display Google Maps tiles as a built-in map tile layer, by creating and adding to the map window an instance of `MVGoogleTileLayer` .

Internally, the Oracle Maps client uses the official Google Maps API to display the map that is directly served by the Google Maps server.

To use the Google Maps tiles, your usage of the tiles must meet the terms of service specified by Google (see [`https://developers.google.com/readme/terms`](https://developers.google.com/readme/terms)).

If you need to overlay your own spatial data on top of the Google Maps tile layer, see also Transforming Data to a Spherical Mercator Coordinate System.)

The following sections describe the two options for using built-in map tile layers.

- Defining Google Maps Tile Layers on the Client Side
- Defining the Built-In Map Tile Layers on the Server Side

**Parent topic:** Oracle Maps

#### 4.3.1 Defining Google Maps Tile Layers on the Client Side

To define a built-in map tile layer on the client side, you need to create a `MVGoogleTileLayer` object, and add it to the MVMapView object. (As of Oracle Fusion Middleware Release 11.1.1.6, `MVGoogleTileLayer` uses the Google Maps Version 3 API by default.)

For example, to use Google tiles, add the Google tile layer to your map:

    mapview = new MVMapView(document.getElementById("map"), baseURL);
    tileLayer = new MVGoogleTileLayer() ;
    mapview.addMapTileLayer(tileLayer);

In your application, you can invoke the method `MVGoogleTileLayer.setMapType` to set the map type to be one of the types supported by the map providers, such as road, satellite, or hybrid.

For usage examples and more information, see the JavaScript API documentation for `MVGoogleTileLayer`, and the tutorial demo Built-in Google Maps Tile Layer.

**Parent topic:** Using Google Maps

#### 4.3.2 Defining the Built-In Map Tile Layers on the Server Side

You can define a built-in map tile layer (also called an external tile layer) on the server side in the metadata, and use it as a regular map visualization component tile layer on the client side. To define a built-in map tile layer on the server side, follow these steps:

1.  Log into the map visualization component administration page (explained in [Logging in to the Map Visualization Component Administration Page](introduction-to-map-visualization-component.md)).

2.  Select the Admin tab and clickCreate tile layer.

3.  For Tile Layer Type, choose Oracle Maps, Google Maps, HERE Maps, OpenStreet Maps, Tomtom Maps, or LocationBox Maps, and click Next.

4.  Provide a name for this external tile layer (such as GOOGLE_MAP), and select the data source where the tile layer definition is to be stored.

5.  Set the license key that you have obtained from the map provider and other relevant properties (details are available for specific external tile layers), and click Next.

6.  Review the XML Description of the external tile layer. You may click Previous to go to the previous page to make changes.

7.  Click Submit to create the tile layer.

After you have created the built-in map tile layer on the server side, you can use it like any other tile layer served by MapViewer. You do not need to add any `<script>` tag to load the external JavaScript library.

The following code snippetshows a Google Maps tile layer defined on the server side:

     var tileLayer = new OM.layer.TileLayer("google1", {
          dataSource:"mvdemo",
          tileLayer:"GOOGLE_MAP"
          });

      map.addLayer(tileLayer) ;

**Note:**

Each built-in tile layer has its own specific properties. You may need to check with the service provider for requirements.

If Google Maps will be used, you may need to provide the following properties:

- `key`: the key you obtained from Google Maps.

- `client`: the client ID, an optional property you may obtain from Google Maps. The key property is still needed when the client ID is provided.

- `lib_url`: the Google Maps API URL, for example: `http://maps.google.com/maps/api/js?sensor=false`. If not provided, a default value will be used.

- `version`: the current API version is 3.

- `mapTyelList`, a list of map types may be provided: MVGoogleTileLayer.TYPE_ROAD; MVGoogleTileLayer.TYPE_SHADED; MVGoogleTileLayer.TYPE_SATELLITE; MVGoogleTileLayer.TYPE_HYBRID.

- `mapTypeVisible`, a Boolean `true` or `false` value to indicate whether to have the map type buttons be displayed for selecting map types.

**Parent topic:** Using Google Maps

### 4.4 Transforming Data to a Spherical Mercator Coordinate System

Popular online map services such as Google Maps use a spherical Mercator projection for their maps.

If you are using an Oracle Database release earlier than 11.1.0.7, and if you need to overlay your own spatial data on top of such a tile layer, such as a Google Maps tile layer, you must set up the database to properly handle coordinate system transformation between the coordinate system of that tile layer and your own data coordinate system, if the two coordinate systems are not the same.

**Note:**

To perform the actions in this section, your database must be Release 10.2.0.1 or later.

Google Maps uses a Spherical Mercator coordinate system (EPSG: 3785), which is also widely used among commercial API providers such as Yahoo! Maps. This coordinate system (SRID 3785) was not provided with Oracle Spatial and Graph before Release 11.1.0.7. In order to enable the map visualization componentthe map visualization component and Oracle Spatial and Graph to transform your own data to this coordinate system, you must first add this coordinate system definition into your Oracle database if it is not already defined.

To check if this coordinate system is defined, you can enter the following statement:

    SELECT srid FROM mdsys.cs_srs WHERE srid=3785;

If the preceding statement returns a row, you do not need to perform the actions in this section. If the preceding statement does not return a row, you must perform the actions in this section in order to be able to overlay your own spatial data on top of the tile layer.

Follow these steps:

1.  Connect to the database as a privileged user, such as one with the DBA role.

2.  Run the `csdefinition.sql` script, as follows. (Replace `$MAPVIEWER_HOME` with the root directory of the WebLogic Server instance where your MapViewer is deployed, and enter the command on a single line.)

    - Linux: `$MAPVIEWER_HOME``/j2ee/home/applications/mapviewer/web/WEB-INF/admin/csdefinition.sql`

    - Windows: `$MAPVIEWER_HOME``\j2ee\home\applications\mapviewer\web\WEB-INF\admin\csdefinition.sql`

3.  If necessary, create a transformation rule to cause Oracle Spatial and Graph to skip datum conversion when transforming data from a specified coordinate system to the Spherical Mercator system. To find out if you need to create such a transformation rule, see Creating a Transformation Rule to Skip Datum Conversion.

4.  Either pre-transform your spatial data for better performance, or let the map visualization component transform the data at runtime ("on the fly"). Note that if your database release is earlier than 10.2.0.4, pre-transforming is the only option.

    - To pre-transform all your data into the Spherical Mercator coordinate system, use the SDO_CS.TRANSFORM_LAYER procedure on all the data, and use the transformed data for mapping. (See the SDO_CS.TRANSFORM_LAYER reference section in [Oracle Spatial and Graph Developer's Guide](../spatl/SDO_CS-reference.md).)

    - To let the map visualization component transform the data at runtime, do not transform the data before using it for mapping.

- Creating a Transformation Rule to Skip Datum Conversion

**Parent topic:** Oracle Maps

#### 4.4.1 Creating a Transformation Rule to Skip Datum Conversion

Spatial data is often in a coordinate system based on an ellipsoid datum, such as WGS84 or BNG. In such cases, Oracle Spatial and Graph by default applies datum conversion when transforming the data into the Spherical Mercator system. This will introduce a small amount of mismatch or error between your data and the Google Maps other map service tiles. If you want to address this issue, you can create transformation rules that tell Oracle Spatial and Graph to skip datum conversion when transforming data from a specified coordinate system to the Spherical Mercator system.

Example 4-1 shows SQL statements that are included in the `csdefinition.sql` script and that create such transformations rules. However, if the coordinate system of your spatial data is not covered by the rules shown in Example 4-1, you can create your own rule if the coordinate system of your data is not covered by these rules. (For more information about creating coordinate system transformation rules, see [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).)

Example 4-1 Transformation Rules Defined in the csdefinition.sql Script

    -- Create the tfm_plans, that is, the transformation rules.
    -- Note: This will result in an incorrect conversion since it ignores a datum
    -- datum between the ellipsoid and the sphere. However, the data will match
    -- up better on Google Maps.

    -- For wgs84 (8307)
    call sdo_cs.create_pref_concatenated_op( 83073785, 'CONCATENATED OPERATION 8307 3785', TFM_PLAN(SDO_TFM_CHAIN(8307, 1000000000, 4055, 19847, 3785)), NULL);

    -- For 4326, EPSG equivalent of 8307
    call sdo_cs.create_pref_concatenated_op( 43263785, 'CONCATENATED_OPERATION_4326_3785', TFM_PLAN(SDO_TFM_CHAIN(4326, 1000000000, 4055, 19847, 3785)), NULL);

    -- For OS BNG, Oracle SRID 81989
    call sdo_cs.create_pref_concatenated_op( 819893785, 'CONCATENATED OPERATION 81989 3785', TFM_PLAN(SDO_TFM_CHAIN(81989, -19916, 2000021, 1000000000, 4055, 19847, 3785)), NULL);

    -- For 27700, EPSG equivalent of 81989
    call sdo_cs.create_pref_concatenated_op( 277003785, 'CONCATENATED_OPERATION_27700_3785', TFM_PLAN(SDO_TFM_CHAIN(27700, -19916, 4277, 1000000000, 4055, 19847, 3785)), NULL);
    commit;

**Parent topic:** Transforming Data to a Spherical Mercator Coordinate System

### 4.5 Using Dynamic Tile Layers

A dynamic tile layer is a tile layer defined on the client side.

A dynamic tile layer differs from a regular tile layer in the following ways:

- It is defined by the client application, so it does not need to be predefined in the USER_SDO_CACHED_MAPS metadata.

- The server does not cache the map tiles.

- It can use third party maps services, when a map tile image URL generation function is provided.

Thus, a dynamic tile layer can be defined dynamically by a client application, and the map images may come from a map visualization component server or from a third party map service.

- Creating a Universe and Configuration Instance for a Dynamic Tile Layer
- Creating a Dynamic Tile Layer Using a Base Map
- Creating a Dynamic Tile Layer Using Predefined Themes
- Creating a Dynamic Tile Layer Using Spatial Tables Directly
- Creating a Dynamic Tile Layer Using Third Party Map Services
- Dynamic Tile Layer Use Case

**Parent topic:** Oracle Maps

#### 4.5.1 Creating a Universe and Configuration Instance for a Dynamic Tile Layer

Before creating a dynamic tile layer instance, you must create a universe and a tile layer configuration for a dynamic tile layer.

For example, assume that a variable named baseURL is properly defined (such as http://myapp.mycorp.com/mapviewer) and that the specified data source exists. You must create a tile layer configuration instance and a universe instance. You can use an Oracle Maps JavaScript API built-in universe or create your own. For simplicity, a built-in universe is used here.

A tile layer configuration instance only needs to define the dimension of an image tile, and 256 pixels for a tile image's width and height are commonly used. The following code snippet creates this instance:

      var  myuniv= new OM.universe.LatLonUniverse();  // a built-in universe
      var  myconfig=new OM.layer.TileLayerConfig(  // a tile layer configure instance
              {
                tileImageWidth: 256,
                tileImageHeight: 256
              });

**Parent topic:** Using Dynamic Tile Layers

#### 4.5.2 Creating a Dynamic Tile Layer Using a Base Map

Creating a dynamic tile layer using a base map is the simplest approach, because the map contents are already defined by a server-side map visualization component base map. Follow these steps.

1.  Create a `ServerMapRequest` instance and set its properties. For example:

                var req = new OM.server.ServerMapRequest(baseURL);
                req.setProperties({
                    dataSource:"MVDEMO",
                    basemap: 'demo_map',  // this basemap property defines the map contents
                    transparent:true,
                    antialiase:"false"
                });

2.  Create an object containing properties of this dynamic tile layer. For example:

                var dtl_props = {
                    universe: myuniv,
                    tileLayerConfig: myconfig,
                    tileServerURL: baseURL + "/omserver",  // map images come from this omserver
                    enableUTFGrid: true,  // the UTFGrid is enabled
                    enableUTFGridInfoWindow: true,  // the info window for displaying UTFGrid is enabled
                    utfGridResolution: 4   // one grid cell represents 16 (4 by 4) image pixels
                };

    In this example, the string value in variable `tileServerURL` is pointing to a map visualization component server. It could be the same server as where the web application is deployed, or another map visualization component server instance. For example, it can be in either of the following forms:

    - From the same Oracle Maps server instance:. For example:

          var baseURL=document.location.protocol+"//"+document.location.host+"/mapviewer";

    - From another Oracle Maps server instance. For example:

          var baseURL="http://myapp.mycorp.com/mapviewer ";

3.  Create a dynamic tile layer. For example:

          var dynamic_tilelayer_1 = new OM.layer.DynamicTileLayer("dtl1", dtl_props, req);

    The dynamic tile layer requests map images from the map visualization component's map server (omserver), which renders a fresh map image and does not cache the images on disk.

From the preceding examples, notice that three statements are given to create a dynamic tile layer: (1) create a map request instance (`ServerMapRequest`); (2) create an object containing the dynamic tile layer related properties; and (3) instantiate a dynamic tile layer.

The dynamic tile layer requests map images from the map visualization component's map server (`omserver`), which renders a fresh map image and does not cache the images on disk.

**Parent topic:** Using Dynamic Tile Layers

#### 4.5.3 Creating a Dynamic Tile Layer Using Predefined Themes

Another approach to creating a dynamic tile layer is to use predefined themes. Follow these steps.

1.  Create a `ServerMapRequest` instance and set its properties. For example:

                var req = new OM.server.ServerMapRequest(baseURL);
                req.setProperties({
                    dataSource:"MVDEMO",
                    transparent:true,
                    antialiase:"false",
                });
                // the three themes below are defined in the metadata already.
                var t1 = new OM.server.ServerPredefinedTheme("THEME_DEMO_STATES");
                var t2 = new OM.server.ServerPredefinedTheme("THEME_DEMO_HIGHWAYS");
                var t3 = new OM.server.ServerPredefinedTheme("THEME_DEMO_CITIES");
                req.addThemes([t1, t2, t3]);

2.  Create an object containing properties of this dynamic tile layer. For example:

                var dtl_props = {
                    universe: myuniv,
                    tileLayerConfig: myconfig,
                    tileServerURL: baseURL + "/omserver",
                    enableUTFGrid: true,
                    enableUTFGridInfoWindow: true,
                    utfGridResolution: 4
                };

3.  Create a dynamic tile layer. For example:

          var dynamic_tilelayer_2 = new OM.layer.DynamicTileLayer("dtl2", dtl_props, req);

    The dynamic tile layer requests map images from the map visualization component's map server (omserver), which renders a fresh map image and does not cache the images on disk.

Instead of specifying a server base map, in this approach the `ServerMapRequest` instance adds some map visualization component server predefined themes. From a practical perspective, this allows the client-side application to create tile layers using the server-side defined themes in the view USER_SDO_THEMES.

**Parent topic:** Using Dynamic Tile Layers

#### 4.5.4 Creating a Dynamic Tile Layer Using Spatial Tables Directly

You can directly use spatial tables for a dynamic tile layer by creating `ServerJBCTheme` instances and adding them into a `ServerMapRequest` instance. Follow these steps.

1.  Create a style. For example:

                var myc1 = new OM.style.Color({
                    styleName: "mycolor1",
                    stroke: "#333333",
                    strokeOpacity: 1.0,
                    fill: "#F2EFE9",
                    fillOpacity: 1.0
                });

2.  Create a JDBC theme and set its properties. Spatial tables are used in a SQL query statement. The statement, as a string type variable, is set as an attribute in the `OM.server.ServerJDBCTheme` instance. For example:

                var jdbcTStates= new OM.server.ServerJDBCTheme('theme_jdbc_states');
                jdbcTStates.setDataSourceName('mvdemo');
                jdbcTStates.setSRID('8307');
                jdbcTStates.setGeometryColumnName('geom');
                var sql='select totpop, poppsqmi, state, state_abrv, geom from states'; // the query
                jdbcTStates.setQuery(sql);  // set the SQL string
                jdbcTStates.addInfoColumn({column: 'state_abrv', name:'State'});
                jdbcTStates.addInfoColumn({column: 'totpop', name:'Population'});
                jdbcTStates.addInfoColumn({column: 'poppsqmi', name:'Pop. Density'});
                jdbcTStates.setRenderingStyleName('mycolor1');

3.  Create a `ServerMapRequest` instance and set its properties. For example:

                var req = new OM.server.ServerMapRequest(baseURL);
                req.setProperties({
                    dataSource:"MVDEMO",
                    transparent:true,
                    antialiase:"false",
                });
                req.addTheme(jdbcTStates);
                req.addStyle(myc1);

4.  Create an object containing properties of this dynamic tile layer. For example:

                var dtl_props = {
                    universe: myuniv,
                    tileLayerConfig: myconfig,
                    tileServerURL: baseURL + "/omserver",
                    enableUTFGrid: true,
                    enableUTFGridInfoWindow: true,
                    utfGridResolution: 4
                };

5.  Create a dynamic tile layer. For example:

          var dynamic_tilelayer_3 = new OM.layer.DynamicTileLayer("dtl3", dtl_props, req);

In this example, a dynamically defined style and a `ServerJDBCTheme` object are created first. The `ServerJDBCTheme` can make use the spatial tables directly using a SQL statement. The tables are then used by the `addTheme` and `addStyle` methods of a `ServerMapRequest` object.

**Parent topic:** Using Dynamic Tile Layers

#### 4.5.5 Creating a Dynamic Tile Layer Using Third Party Map Services

Another approach to create a dynamic tile layer is to use third party map services. The map service URL of a third party is provided by a client provided URL generation function. Follow these steps.

1.  Using the third party map service provider's specifications, create a URL construction function for building map image requests by a dynamic tile layer. For example:

        var urlb = function (w, h, minX, minY, maxX, maxY, options){
              var str="http://my.mycorp.com:8080/geoserver/ows?";
              var optParams="";
              str = str+"request=getmap"+
              "&bbox="+minX+","+minY+","+maxX+","+maxY+
              "&width="+w+
              "&height="+h;

            if (!OM.isNull(options)) {
              for (var key in options) {
                optParams=optParams +"&"+key +"="+options[key];
              }
            }
            return str+optParams;
          }

2.  Create an object containing properties of this dynamic tile layer. For example:

        var dtl_props = {
            universe: myuniv,
            tileLayerConfig: myconfig,
            urlBuilder: urlb,
            urlBuilderOptions: {
                      "layers":  "topp:states,sf:sfdem,sf:roads,sf:streams",
                      "CRS":     "CRS:84",
                      "service": "WMS",
                      "version": "1.3.0",
                      "format":  "image/png"
                }
        };

3.  Create a dynamic tile layer. For example:

          var dynamic_tilelayer_4 = new OM.layer.DynamicTileLayer("dl4", dtl_props);

In this example, a dynamic tile layer instance (`dynamic_tilelayer_4`) contains a `urlBuilder` property to provide a URL generation function (`iurlb`). The URL generation function will be used by the dynamic tile layer for fetching image tiles from the specified map service provider. This example uses a third party map provider, a `GeoServer` instance, to provide map images.

Additional map service provider required parameters can be provided in the `urlBuilderOptions` property. This example specifies several additional parameters (`layers`, `CRS`, `service`, `version`, and `format`) needed by the `GeoServer` instance.

**Parent topic:** Using Dynamic Tile Layers

#### 4.5.6 Dynamic Tile Layer Use Case

This topic describes a dynamic tile layer use case.

The code examples come from a dynamic tile layer application. The application uses the map visualization component server to provide map image tiles. It uses spatial tables directly via an `OM.server.ServerJDBCTheme` instance.

1.  Obtain the SQL query's "where" clause from an application's user interface using the `getWhereClauseFromUI()` function, assuming that this function is properly defined already in that application and returns expected results. For example:

            var  wherec = getWhereClauseFromUI();

2.  Create a JDBC theme and set its properties. For example:

            var objJDBCTheme= new OM.server.ServerJDBCTheme();
            objJDBCTheme.setDataSourceName('storm');
            objJDBCTheme.setSRID('3857');
            objJDBCTheme.setXColumnName('long_loc');
            objJDBCTheme.setYColumnName('lat_loc');

            objJDBCTheme.addInfoColumn({column: 'YEAR', name:'Year'});
            objJDBCTheme.addInfoColumn({column: 'MONTH', name:'Month'});
            objJDBCTheme.addInfoColumn({column: 'DAY', name:'Day'});
            objJDBCTheme.addInfoColumn({column: 'STATE', name:'State'});
            objJDBCTheme.addInfoColumn({column: 'LOSS', name:'Loss'});
            objJDBCTheme.addInfoColumn({column: 'CROPLOSS', name:'Crop_loss'});
            objJDBCTheme.addInfoColumn({column: 'FATALITIES', name:'Fatalities'});
            objJDBCTheme.addInfoColumn({column: 'INJURIES', name:'Injuries'});

            objJDBCTheme.setName('theme_tornado');
            objJDBCTheme.setQuery("SELECT s.geom.sdo_point.x long_loc,s.geom.sdo_point.y lat_loc,year,month,day,state,fatalities,injuries,loss,croploss from tornado_3857 s"+
        (wherec === "" ?"": wherec));
            objJDBCTheme.setRenderingStyleName('V.TORNADO');

3.  Create a `ServerMapRequest` instance and set its properties. For example:

                var req = new OM.server.ServerMapRequest(baseURL);
                req.setProperties({
                    dataSource:'storm',
                    transparent:true,  // map image is set to be transparent
                    antialiase:"false"
                });
                req.addTheme(objJDBCTheme);

4.  Create an object containing properties of this dynamic tile layer. For example:

                var dtl_props = {
                    universe: myuniv,
                    tileLayerConfig: myconfig,
                    tileServerURL: baseURL + "/omserver",
                    enableUTFGrid: true,
                    enableUTFGridInfoWindow: true,
                    utfGridResolution: 4
                };

5.  Create a dynamic tile layer. For example:

          var tornado_damage = new OM.layer.DynamicTileLayer("tornado_damage", dtl_props, req);

The code examples in the preceding steps illustrate the following:

- The map application fetches map images from a map visualization component server. Therefore, it may use all available features from the map visualization component server.

- The map image is set to be transparent (that is, the value for property `transparent` is `true`). This setting makes all of the non-overlapping features visible when multiple dynamic tile layers are stacked for display. For example, when you overlay a `tornado_damage` dynamic tile layer on top of a `hail_damage` dynamic tile layer, you may see both layers on the map when such events (as their names suggest) were happening at non-overlapping locations. This setting is more useful for multiple layers containing linear and point features. Note that since the API allows you to turn on/off a layer's visibility, you can always make a layer of interest stand out and be visible in your application.

- The dynamic tile layer also enables the map visualization component server's `UTFGrid` support (specifically, the value for property `enableUTFGrid` is set to `true`, with a resolution value set to 4 for the `utfGridResolution` property). This setting instructs map visualization component's API to request an additional `UTFGrid` file as a companion of its map tile image. It is a JSON file, and it contains a two-dimensional grid table in UTF encoding, that matches the tile image. It also contains some text attributes for each grid cell.

  When a mouse event (for example, a mouse click) is triggered at an image pixel, its corresponding grid cell can then be located, its UTF code be obtained, and subsequently, the text attributes associated with that grid cell's UTF code can be retrieved and displayed in a popup info window.

  The text attributes contained in that JSON file are specified using the `addInfoColumn()` method. Those text attributes will be displayed in an info window for a pixel being clicked on the map.

  Note that if server-side predefined geometry themes are used by a dynamic tile layer, the text attributes for an info window must have been specified in theme's `<hidden_info>` element. This also applies for the base map-based dynamic tile layers, where the predefined themes are found in the map visualization component's base map definition

  A resolution value (for example, `"utfGridResolution":4`) indicates the width and height of the grid cell compares with its companion map tile image pixel. In this example, one grid cell in the `UTFGrid` data set represents 16 pixels (4x4=16).

- This dynamic tile layer makes use of spatial table directly via a `ServerJDBCTheme` to define its map contents. In its embedded SQL statement, the client web application has the flexibility to construct the whole statement, including the tables to use, the columns to select, and the "where" clause to refine the query. In the code snippets, it assumes that a client function, `getWhereClauseFromUI()`, only constructs the 'where' clause in the JDBC theme definition.

The dynamic tile layer supported in the Oracle Maps JavaScript API allows the map visualization component server metadata to be used by the tile layer, and it offers flexibility in how a dynamic tile layer is defined and where to fetch its map images by the client application.

**Parent topic:** Using Dynamic Tile Layers
