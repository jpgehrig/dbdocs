##   Oracle® Spatial and Graph Map Visualization JavaScript API Reference (Release 19.1)

This is the online documentation for the Oracle Maps HTML5-based JavaScript API.
The Oracle Maps JavaScript API Version 2 (V2) takes advantage of the capabilities of modern browsers. Some of its features include:

- Built-in support of various third party map tile services, such as maps.oracle.com, Nokia Maps, Bing Maps, OpenStreet Maps, and other mapping service providers.
- Rich client side rendering of geospatial data with on-the-fly application of rendering styles and effects such as gradients, animation, and drop-shadows.
- Autoclustering of large number of points and client side heat map generation.
- A set of built-in map controls and tools, including a customizable navigation bar and information windows, configurable layer control, and red-lining and distance measurement tools.

The V2 API is *not* backward compatible with the existing Oracle Maps JavaScript V1 API applications. The API has the following top-level classes and subpackages, all of which are in the namespace **OM**:

- The **Map** class is the main class of the API.
- The **Feature** class represents individual geo features (or FOIs as they were known in V1).
- The **MapContext** class a top-level class encapsulating some essential contextual information, such as the current map center point and zoom level. It is typically passed into event listeners.
- The **control** package contains all the map controls, such as navigation bar and overview map.
- The **event** package contains all the map and layer event classes.
- The **filter** package contains all the client-side filters (spatial or relational) for selecting, or subsetting, the displayed vector layer features.
- The **geometry** package contains various geometry classes.
- The **layer** package contains various tile and vector layer classes. The tile layer classes include access to a few online map services such as Oracle, Nokia, Bing, and OpenStreetMap. The vector layers are interactive feature layers and correspond to the MVThemeBasedFOI and MVFOI classes of V1.
- The **infowindow** package contains the customizable information windows and their styles.
- The **style** package contains styles applicable to vector data on the client side. It also includes visual effects such as animation, gradients, and drop shadows.
- The **tool** package contains various map tools such as for distance measuring, red-lining, and geometry drawing.
- The **universe** package contains built-in, or predefined, *map universes*. A map universe defines the bounding box and set of zoom level definitions for the map content. It is similar to a tile layer configuration in the V1 API.
- The **util** package contains various utility classes.
- The **visualfilter** package provides an interface for the various visual effects, such as gradients and drop shadows.
- The **gv** package contains global variables for configuration options such as resource paths or protocol (http or https) for requests.

**OM.Map** is the main entry class for all map operations inside the web browser. This and other classes provide interfaces for adding application-specific logic, operations, and interactivity in web mapping applications.

The library consists of a set of JavaScript, CSS, message,and image files. The resources (CSS, images, messages) are assumed to be accessible from the same URL where the oraclemapsv2.js file is accessed. If for any reason the resources have to be accessed from a different URL then use the OM.gv.setResourcePath() method to set it. For example, here is how this method is used in the standalone demo application whch just uses the Oracle Maps library in a local directory and no web server or MapViewer instance.

    <!DOCTYPE html>

    <html>
        <head>
            <title>Oracle Maps HTML5 API Tutorial: Hello World!</title>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width">
        <!-- Import the Oracle Maps API lib -->
            <script type="text/javascript" src="../../oraclemapsv2.js"></script>
            <script type="text/javascript">
        function showMap() {
            // Set the resource path. It is the same location as the oraclemapsv2.js
            // use OM.gv.setResourcePath("http://host:port/mapviewer/jslib/v2");
            // instead to load the resources from a different URL
            OM.gv.setResourcePath("../..");
            var myUniverse = new OM.universe.Universe(
                {
                //Specifies what spatial reference system is used by this new universe.
                //8307 is the SRID for WGS84 or longitude/latitude.
                srid: 8307,
                //The boundary of the universe
                bounds: new OM.geometry.Rectangle(-180, -65, 180, 65, 8307),
                //How many zoom-able levels the map will provide
                numberOfZoomLevels: 5
                });

                //This is the container DIV to display the map; it needs to be
                //passed into the map instance.
                var mapDiv = document.getElementById('map');
                var mapOptions = {
                    //Specifies the URL to a MapViewer server instance. This is needed
                    //only if your application will be accessing spatial data stored in
                    //a database via the MapViewer server. In this case we don't really
                    //need it so we can set it to an empty url.
                    mapviewerURL: '',

                    //this map will use the universe created earlier.
                    universe: myUniverse
                };

                //creates the actual  map instance. This returns a blank map that is
                //yet to be initialized.
                var map = new OM.Map(mapDiv, mapOptions);
            //Create a layer

                //In order to display a Marker on the map, we must create a Feature object
                //for it.  Each Feature object must have a geometry that defines its shape or
                //location, plus optional properties and attributes.

                //First, lets create a point object that defines the location of the marker
                //feature. It will be located at the longitude 0 and latitude 1.
                var point = new OM.geometry.Point(0, 1);

                //Next, create a feature object for the point. You must specify a
                //unique ID (within a layer), 'pt_1' in this case. We are also
                //specifying a label text 'Hello World!' for this feature.
                var feature = new OM.Feature('pt_1', point, {label: "Hello World!"});

                //Note that you cannot add a feature directly to the map. Instead features
                //must always be added to a layer object which can be directly added to the map.
                //So lets create such a vector layer.

                //Define the various options and properties for the new layer to be
                //created.
                var layerOptions = {
                        def: {
                            //this will be a local layer since all the features are
                            //created locally and on the fly, instead of being loaded from
                            //a remote URL or service.
                            type: OM.layer.VectorLayer.TYPE_LOCAL
                        }
                };

                //Create the actual layer object with the specified name and properties.
                var layer = new OM.layer.VectorLayer('Layer 1', layerOptions);

                //add the point feature to the layer
                layer.addFeature(feature);

                //ensure the feature's label text is displayed on the map
                layer.setLabelsVisible(true);

                //finally, add the layer to the map for display
                map.addLayer(layer);

                //Now we can complete the initialization of the map. You must
                //only call this method once.  Note however map content (features and
                //layers)  can be added even after calling this method.
                map.init();
        };
             $(document).ready( function(){

                    showMap();
                });
            </script>
        </head>
        <body>



        </body>
    </html>
