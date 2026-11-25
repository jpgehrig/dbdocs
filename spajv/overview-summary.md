Skip navigation links

- Overview
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Oracle Spatial and Graph Java API

The Oracle Spatial and Graph Java API consists of interfaces and classes that support features available with Spatial and Graph, including GeoRaster, the Topology Data Model and Network Data Model Graph, and with the Map Visualization Component (formerly called MapViewer).

This API is a Java alternative for much of the PL/SQL API, which is provided in PL/SQL packages that are documented in the manuals; however, there are some PL/SQL packages (such as SDO_GEOM and SDO_UTIL) that do not have Java equivalent interfaces. The Java packages are grouped functionally as follows:

**Spatial and Graph core:**
  oracle.spatial.geometry
  oracle.spatial.util

**GeoRaster:**
  oracle.spatial.georaster
  oracle.spatial.georaster.image
  oracle.spatial.georaster.sql
  oracle.spatial.georaster.util

**Network data model:**
  oracle.spatial.network
  oracle.spatial.network.lod
  oracle.spatial.network.lod.config
  oracle.spatial.network.nfe
  oracle.spatial.network.nfe.(many)

**Topology data model:**
  oracle.spatial.topo

**Location tracking server:**
  oracle.spatial.objtrkr

**Packages**

| Package                                                                                                                                         | Description                                                                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [oracle.spatial.geometry](oracle/spatial/geometry/package-summary.md)                                                                           | Provides support for the SDO_GEOMETRY data type, which is documented in *Oracle Spatial and Graph Developer's Guide*.                                                                                                                      |
| [oracle.spatial.georaster](oracle/spatial/georaster/package-summary.md)                                                                         | Provides support for Oracle Spatial GeoRaster, which is documented in *Oracle Spatial and Graph GeoRaster Developer's Guide*.                                                                                                              |
| [oracle.spatial.georaster.image](oracle/spatial/georaster/image/package-summary.md)                                                             |                                                                                                                                                                                                                                            |
| [oracle.spatial.georaster.sql](oracle/spatial/georaster/sql/package-summary.md)                                                                 |                                                                                                                                                                                                                                            |
| [oracle.spatial.georaster.util](oracle/spatial/georaster/util/package-summary.md)                                                               |                                                                                                                                                                                                                                            |
| [oracle.spatial.network](oracle/spatial/network/package-summary.md)                                                                             | Provides support for the Oracle Spatial network data model, which is documented in *Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide*.                                                          |
| [oracle.spatial.network.lod](oracle/spatial/network/lod/package-summary.md)                                                                     | Provides support for the Load-On-Demand (LOD) approach of network analysis in the Oracle Spatial network data model, which is documented in *Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide.* |
| [oracle.spatial.network.lod.config](oracle/spatial/network/lod/config/package-summary.md)                                                       | Provides support for the configuration of Load-On-Demand (LOD) network analysis in the Oracle Spatial network data model.                                                                                                                  |
| [oracle.spatial.network.nfe](oracle/spatial/network/nfe/package-summary.md)                                                                     | Provides general NFE constants classes.                                                                                                                                                                                                    |
| [oracle.spatial.network.nfe.beans](oracle/spatial/network/nfe/beans/package-summary.md)                                                         | Provides classes to work with NFE services.                                                                                                                                                                                                |
| [oracle.spatial.network.nfe.expression](oracle/spatial/network/nfe/expression/package-summary.md)                                               | Provides support for the NFE expression analyzing that is used when applying NFE rules based on attributes conditions and when calculating customized cost in NFE Analysis.                                                                |
| [oracle.spatial.network.nfe.io](oracle/spatial/network/nfe/io/package-summary.md)                                                               | Provides the base exceptions and datasource classes.                                                                                                                                                                                       |
| [oracle.spatial.network.nfe.io.jdbc](oracle/spatial/network/nfe/io/jdbc/package-summary.md)                                                     | Provides implementations of the DataSource and JDBC utilities.                                                                                                                                                                             |
| [oracle.spatial.network.nfe.io.jdbc.dao](oracle/spatial/network/nfe/io/jdbc/dao/package-summary.md)                                             | Provides the data access objects implementations; it is not recommended to use the data access objects methods, instead use the NFE services.                                                                                              |
| [oracle.spatial.network.nfe.io.jdbc.service](oracle/spatial/network/nfe/io/jdbc/service/package-summary.md)                                     | Provides default NFE services implementations.                                                                                                                                                                                             |
| [oracle.spatial.network.nfe.io.service](oracle/spatial/network/nfe/io/service/package-summary.md)                                               | Provides the NFE services to perform operations related to NFE model, feature layers, analysis and workspace management.                                                                                                                   |
| [oracle.spatial.network.nfe.model](oracle/spatial/network/nfe/model/package-summary.md)                                                         | Provides classes for representing and managing an NFE model in memory.                                                                                                                                                                     |
| [oracle.spatial.network.nfe.model.edit](oracle/spatial/network/nfe/model/edit/package-summary.md)                                               | Provides classes that aid on the edition of an NFE model                                                                                                                                                                                   |
| [oracle.spatial.network.nfe.model.edit.undo](oracle/spatial/network/nfe/model/edit/undo/package-summary.md)                                     | Provides classes used to perform undo/redo actions for NFE model events.                                                                                                                                                                   |
| [oracle.spatial.network.nfe.model.event](oracle/spatial/network/nfe/model/event/package-summary.md)                                             | Contains event definitions and listeners used in an NFE model                                                                                                                                                                              |
| [oracle.spatial.network.nfe.model.feature](oracle/spatial/network/nfe/model/feature/package-summary.md)                                         | Provides memory representations of feature layers and elements contained in feature layers                                                                                                                                                 |
| [oracle.spatial.network.nfe.model.network](oracle/spatial/network/nfe/model/network/package-summary.md)                                         | Provides memory representations of a network and network elements such as nodes and links                                                                                                                                                  |
| [oracle.spatial.network.nfe.model.rule](oracle/spatial/network/nfe/model/rule/package-summary.md)                                               | Provides memory representations of NFE rules and contains classes used to manage and enforce such rules.                                                                                                                                   |
| [oracle.spatial.network.nfe.model.rule.handler](oracle/spatial/network/nfe/model/rule/handler/package-summary.md)                               | Contains the basic rule handlers definitions and implementations.                                                                                                                                                                          |
| [oracle.spatial.network.nfe.model.spatial](oracle/spatial/network/nfe/model/spatial/package-summary.md)                                         | Provides classes for finding and representing spatial relationships between elements in an NFE model                                                                                                                                       |
| [oracle.spatial.network.nfe.model.spatial.interaction](oracle/spatial/network/nfe/model/spatial/interaction/package-summary.md)                 | Provides classes for representing interactions between elements in an NFE model                                                                                                                                                            |
| [oracle.spatial.network.nfe.util](oracle/spatial/network/nfe/util/package-summary.md)                                                           | Provides classes that perform miscellaneous operations.                                                                                                                                                                                    |
| [oracle.spatial.network.nfe.vis.mapcanvas](oracle/spatial/network/nfe/vis/mapcanvas/package-summary.md)                                         | Provides classes used to visualize and interact with elements from an NFE model using a MapCanvas                                                                                                                                          |
| [oracle.spatial.network.nfe.vis.mapcanvas.behavior](oracle/spatial/network/nfe/vis/mapcanvas/behavior/package-summary.md)                       | Contains definitions of behavior that an NFE renderer must implement in order to support certain interaction/manipulation                                                                                                                  |
| [oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate](oracle/spatial/network/nfe/vis/mapcanvas/behavior/manipulate/package-summary.md) | Provides classes which describe the "manipulable" behavior for an NFE renderer.                                                                                                                                                            |
| [oracle.spatial.network.nfe.vis.mapcanvas.render](oracle/spatial/network/nfe/vis/mapcanvas/render/package-summary.md)                           | Provides renderers for visualizing different type of data from an NFE model as layers over a MapCanvas.                                                                                                                                    |
| [oracle.spatial.network.nfe.vis.mapcanvas.tool](oracle/spatial/network/nfe/vis/mapcanvas/tool/package-summary.md)                               | Provides tools for interacting with visual representations of an NFE model content                                                                                                                                                         |
| [oracle.spatial.network.nfe.vis.maps](oracle/spatial/network/nfe/vis/maps/package-summary.md)                                                   | Contains components used for visualization and editing of geometries.                                                                                                                                                                      |
| [oracle.spatial.network.nfe.vis.maps.core](oracle/spatial/network/nfe/vis/maps/core/package-summary.md)                                         | Contains the core components for working with a mapcanvas                                                                                                                                                                                  |
| [oracle.spatial.network.nfe.vis.maps.geoobject](oracle/spatial/network/nfe/vis/maps/geoobject/package-summary.md)                               | Contains geo-object implementations                                                                                                                                                                                                        |
| [oracle.spatial.network.nfe.vis.maps.graphics](oracle/spatial/network/nfe/vis/maps/graphics/package-summary.md)                                 | Contains graphic utilities                                                                                                                                                                                                                 |
| [oracle.spatial.network.nfe.vis.maps.index](oracle/spatial/network/nfe/vis/maps/index/package-summary.md)                                       | R-Tree index definition and implementations                                                                                                                                                                                                |
| [oracle.spatial.network.nfe.vis.maps.layer](oracle/spatial/network/nfe/vis/maps/layer/package-summary.md)                                       | Basic layer definitions and implementations                                                                                                                                                                                                |
| [oracle.spatial.network.nfe.vis.maps.layer.ui](oracle/spatial/network/nfe/vis/maps/layer/ui/package-summary.md)                                 | Multiple layer implementations                                                                                                                                                                                                             |
| [oracle.spatial.network.nfe.vis.maps.tools](oracle/spatial/network/nfe/vis/maps/tools/package-summary.md)                                       | Tool layer definition and other implementations                                                                                                                                                                                            |
| [oracle.spatial.network.nfe.workspace](oracle/spatial/network/nfe/workspace/package-summary.md)                                                 | Provides classes to describe workspace conflicts.                                                                                                                                                                                          |
| [oracle.spatial.objtrkr](oracle/spatial/objtrkr/package-summary.md)                                                                             | Provides support for the Oracle Spatial and Graph location tracking server, which is documented in *Oracle Spatial and Graph Developer's Guide*.                                                                                           |
| [oracle.spatial.topo](oracle/spatial/topo/package-summary.md)                                                                                   | Provides support for the Oracle Spatial and Graph topology data model, which is documented in *Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide*.                                               |
| [oracle.spatial.util](oracle/spatial/util/package-summary.md)                                                                                   | Provides classes that perform miscellaneous operations.                                                                                                                                                                                    |

Skip navigation links

- Overview
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
