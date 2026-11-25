## 11  Introduction to Spatial Web Services

This chapter introduces the Oracle Spatial and Graph support for spatial web services.

**Note:**

You can deploy Oracle Spatial Web Services from Oracle Cloud Marketplace. This packaged application allows you to install Oracle Spatial web services (such as Web Feature Service (WFS), Web Coverage Services (WCS), and Catalog Services for the Web (CSW)) that are deployed in an Apache Tomcat web server instance on Oracle Cloud Infrastructure (OCI).

A web service enables developers of Oracle Spatial and Graph applications to provide feature data and metadata to their application users over the web.

**Note:**

If you are using Spatial and Graph Web Feature Service (WFS) or Catalog Services for the Web (CSW) support, and if you have data from a previous release that was indexed using one or more SYS.XMLTABLEINDEX indexes, you must drop the associated indexes before the upgrade and re-create the indexes after the upgrade.

For more information, see [Index Maintenance Before and After an Upgrade (WFS and CSW)](spatial-install-migrate-upgrade.md).

- Types of Spatial Web Services
  Oracle Spatial and Graph provides the following types of web services.
- Types of Users of Spatial Web Services
  In the general business sense of the word "user," implementing any spatial web services application involves the following kinds of people.
- Deploying and Configuring Spatial Web Services
  This topic describes actions that apply to deploying and configuring spatial web services, and particularly WFS, WCS, and CSW.
- Spatial Web Services Administration Console
  Oracle Spatial and Graph provides a Spatial Web Services administration console, which consists of several components to help configure the WFS, WCS, and CSW web service engines, to test each service, and to display error logs for diagnosis. It is shipped within the `sdows.ear` file.

**Parent topic:** [Spatial Web Services](spatial-web-services.md)

### 11.1 Types of Spatial Web Services

Oracle Spatial and Graph provides the following types of web services.

- Geocoding, which enables users to associate spatial locations (longitude and latitude coordinates) with postal addresses. Geocoding support is explained in [Geocoding Address Data](geocoding-address-data-concepts.md).

- Yellow Pages, which enables users to find businesses by name or category based on their relationship to a location. Yellow Pages support is explained in [Business Directory (Yellow Pages) Support](buasiness-directory-yp-concepts.md).

- Routing, which provides driving information and instructions for individual or multiple routes. Routing support is explained in [Routing Engine](routing-engine-concepts.md).

- OpenLS, which provides location-based services based on the Open Location Services Initiative (OpenLS) specification for geocoding, mapping, routing, and yellow pages. OpenLS support is explained in [OpenLS Support](openls-concepts.md).

- Web Feature Services (WFS), which enables users to find features (roads, rivers, and so on) based on their relationship to a location or a nonspatial attribute. WFS support is explained in [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

- Web Coverage Services (WCS), which provides access to coverage data in forms that are useful for client-side rendering, as input into scientific models, and for other clients.. WCS support is explained in [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

  For an overview of WCS, see <https://en.wikipedia.org/wiki/Web_Coverage_Service>. For an introductory comparison of WCS to related web services, see <http://gis.stackexchange.com/questions/80948/what-are-the-differences-between-wms-wfs-wcs-wps>.

- Catalog Services for the Web (CSW), which describes the Oracle Spatial and Graph implementation of the Open GIS Consortium specification for catalog services. According to this specification: "Catalogue services support the ability to publish and search collections of descriptive information (metadata) for data, services, and related information objects." CSW support is explained in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

- Web Map Service (WMS), which supports the rendering of spatial data. Specifically, the WMS 1.1.1 and 1.3.0 implementation specifications are implemented in the Map Visualization Component. This implementation is described in [OGC WMS Support in the Map Visualization Component](../jimpv/ogc-wms-support-map-visualzation-component.md) in Oracle Spatial and Graph Map Visualization Developer's Guide.

**Parent topic:** Introduction to Spatial Web Services

### 11.2 Types of Users of Spatial Web Services

In the general business sense of the word "user," implementing any spatial web services application involves the following kinds of people.

- Administrators set up the web services infrastructure. Administrators might create database users, grant privileges and access rights to new and existing database users, and do other operations that affect multiple database users.

  - For web feature services, administrators can use the WFS Admin Console to register feature tables and publish feature types.

  - For catalog service for the web services, administrators can use CSW Admin Console to publish record types.

  - For web coverage services, administrators can use WCS Admin Console to publish coverages.

  For example, an administrator might set up the infrastructure to enable access to spatial features, such as roads and rivers.

- Application developers create and manage the spatial data and metadata. They create spatial data tables, create spatial indexes, insert rows into the USER_SDO_GEOM_METADATA view, and use spatial functions and procedures to implement the application logic.

  For example, an application developer might create tables of roads and rivers, and implement application logic that enables end users to find roads and rivers based on spatial query criteria.

- End users access the services through HTTP requests using KVP, POST, or SOAP protocol.

  For example, an end user might ask for all roads that are within one mile of a specific river or that intersect (cross) that river.

From the perspective of an administrator, application developers and end users are all "users" because database users must be created to accommodate their needs. Application developers will connect to the database as users with sufficient privileges to create and manage spatial tables and to use Oracle Spatial and Graph functions and procedures. End users will access the database through HTTP requests.

The chapters about Spatial and Graph web services are written for administrators and application developers, not for end users.

**Parent topic:** Introduction to Spatial Web Services

### 11.3 Deploying and Configuring Spatial Web Services

This topic describes actions that apply to deploying and configuring spatial web services, and particularly WFS, WCS, and CSW.

These services are implemented as Java web applications and can be deployed to run on WebLogic 12.1.3 or later. The required Java version is JDK 1.8 or later.

- WFS, CSW, and CSW are packaged in the `sdows.ear` file.

- The Geocoder service is packaged in the `geocoder.ear.zip` file.

- The Routing Engine is packaged in the `routeserver.ear.zip` file.

In addition to the “general” instructions in this topic, see the chapter about each specific spatial web service that you plan to use for any additional deployment and configuration tasks.

Deploying any Oracle Spatial and Graph web services includes the following major tasks.

1.  Preparing WebLogic Server (Version 12.1.3 or Later)

2.  Creating a Domain on WebLogic Server

3.  Configuring server start arguments on WebLogic Server

4.  Deploying Spatial Web Services on WebLogic Server

5.  Ensuring the Web Service Web Application is in the Active State

6.  Configuring Each Spatial Web Service

#### Preparing WebLogic Server (Version 12.1.3 or Later)

Before you deploy the web service engine, it is recommended that you create a managed server in WebLogic Server.

For the Web Service Engine to be successfully deployed on a managed server, a WebLogic domain must be created.

#### Creating a Domain on WebLogic Server

You must ensure that a domain exists for web services on WebLogic Server. To create a spatial domain, follow these steps.

1.  Log in to the WebLogic Server console.

2.  Select Create a New WebLogic Domain, and click Next.

3.  Select Domain Source: Generate a Domain Configured Automatically, and click Next.

4.  Configure the Administrator Username and Password, and click Next.

5.  For Server Start Mode, select Development or Production.

6.  For JDK, select one of the available JDKs.

7.  For Customize Environment and Service Settings, either accept the default values or specify any customizations.

8.  On the Create WebLogic Domain page, click Create, then Next.

9.  On the Creating Domain page, click Done.

For more information about creating and configuring a domain, see the WebLogic Server documentation.

#### Configuring Server Start Arguments on WebLogic Server

Spatial Web Services web applications require a folder to save configuration files and log files. This folder is passed to WebLogic Server as a Java argument with name `sdows`. If you are running node manager, configure this argument using the WebLogic Server administration console by following these steps:

1.  Log in to the WLS console.

2.  Select Managed Server in Environment - Servers.

3.  On the Configuration tab, select Server Start.

4.  Add `-Dsdows=<configuration folder path>` to Arguments, where \<configuration folder path\> is the path to a writable folder where the configuration file and log files will be stored.

If you are not running node manager, edit the script edit the script \<WLS domain\>\bin\setDomainEnv. Search for `set JAVA_PROPERTIES`, and add to the end of the line:

     -Dsdows=<configuration folder path>

#### Deploying Spatial Web Services on WebLogic Server

To deploy a spatial web service on WebLogic Server, follow these steps.

1.  Log in to the WLS console

2.  Click Deployments, then Install.

3.  Select `sdows.ear` (a file), and click Next.

4.  Ensure that the Install this deployment as an application targeting style is selected, and click Next.

5.  In the list of potential servers to which to deploy the WFS Engine, select the name of the managed server that you created, select I will make the deployment accessible from the following location, and click Next.

6.  Ensure that the deployment name is `sdows`, and click Finish.

#### Ensuring the Web Services Web Application is in the Active State

After completing the necessary steps for a spatial web service, check on the Deployments page that the application is in the `Active` state.

If it is in the `Prepared` state, click Start to start the application.

#### Configuring Each Spatial Web Service

The next step is to configure each spatial web service that you will use (WFS, WCS, or CSW) independently. You must perform specific tasks that depend on which web services you will be supporting for use in your environment. You will probably need to create and grant privileges to database users. You may need to download and load special data (such as for geocoding), modify configuration files or create data sources in WebLogic Server.

See the chapter for each relevant spatial web service for instructions specific to that service.

**Parent topic:** Introduction to Spatial Web Services

### 11.4 Spatial Web Services Administration Console

Oracle Spatial and Graph provides a Spatial Web Services administration console, which consists of several components to help configure the WFS, WCS, and CSW web service engines, to test each service, and to display error logs for diagnosis. It is shipped within the `sdows.ear` file.

To access the administration console, go to a URL in the following format:

    http://<system-name>:<port>/oraclespatial/

Before you can use any Service page, select a data source from the list of all available data source names. (The currently selected data source is shown in the upper-right corner, and you can change it there at any time.)

- The Configuration File tabs let you modify service parameters like logging level or service provider information displayed in GetCapabilities response.

- The Test tabs for WFS, WCS, and CSW let you create simple requests for different operations, which you can edit to add or modify parameters, and then send as HTTP POST/XML requests. The responses are also displayed.

- The Log tabs for WFS, WCS, and CSW let you display the content of the log files for each service. Each Log tab also lets you download the logs compressed in a zip file, so that you can later use the information to diagnose problems.

The console pages and WFS, WCS, and CSW are described in more detail in the chapters about those services.

**Parent topic:** Introduction to Spatial Web Services
