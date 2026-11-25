## Part I  Conceptual and Usage Information

This document has the following parts:

- Part I provides conceptual and usage information about Oracle Spatial and Graph.

- [Spatial Web Services](spatial-web-services.md) provides conceptual and usage information about Oracle Spatial and Graph web services.

- [Reference Information](spatial-reference-information.md) provides reference information about Oracle Spatial and Graph operators, functions, and procedures.

- [Supplementary Information](spatial-supplementary-information.md) provides supplementary information (appendixes and a glossary).

Part I is organized for efficient learning about Oracle Spatial and Graph. It covers basic concepts and techniques first, and proceeds to more advanced material, such as coordinate systems, the linear referencing system, geocoding, and extending spatial indexing.

- [Spatial Concepts](spatial-concepts.md)
  Oracle Spatial and Graph is an integrated set of functions, procedures, data types, and data models that support spatial and graph analytics. The spatial features enable spatial data to be stored, accessed, and analyzed quickly and efficiently in an Oracle database.
- [Spatial Data Types and Metadata](spatial-datatypes-metadata.md)
  The spatial features in Oracle Spatial and Graph consist of a set of object data types, type methods, and operators, functions, and procedures that use these types. A geometry is stored as an object, in a single row, in a column of type SDO_GEOMETRY. Spatial index creation and maintenance is done using basic DDL (CREATE, ALTER, DROP) and DML (INSERT, UPDATE, DELETE) statements.
- [SQL Multimedia Type Support](sql-multimedia-type-support.md)
  Oracle Spatial and Graph supports the use of the ST\_xxx types specified in ISO 13249-3, Information technology - Database languages - SQL Multimedia and Application Packages - Part 3: Spatial.
- [Loading Spatial Data](loading-spatial-data.md)
  This chapter describes how to load spatial data into a database, including storing the data in a table with a column of type SDO_GEOMETRY.
- [Indexing and Querying Spatial Data](indexing-querying-spatial-data.md)
  After you have loaded spatial data, you should create a spatial index on it to enable efficient query performance using the data.
- [Coordinate Systems (Spatial Reference Systems)](coordinate-systems-concepts.md)
  This chapter describes in detail the Oracle Spatial and Graph coordinate system support.
- [Linear Referencing System](lrs-linear-referencing-system-concepts.md)
  Linear referencing is a natural and convenient means to associate attributes or events to locations or portions of a linear feature. It has been widely used in transportation applications (such as for highways, railroads, and transit routes) and utilities applications (such as for gas and oil pipelines).
- [Location Tracking Server](location-tracking-server-concepts.md)
  The Oracle Spatial and Graph location tracking server enables you to define regions, track the movement of objects into or out of those regions, and receive notifications when certain movements occur.
- [Spatial Analysis and Mining](spatial-analysis-mining.md)
  This chapter describes the Oracle Spatial and Graph features that enable the use of spatial data in data mining applications.
- [Extending Spatial Indexing Capabilities](extending-spatial-indexing.md)
  This chapter shows how to create and use spatial indexes on objects other than a geometry column. In other chapters, the focus is on indexing and querying spatial data that is stored in a single column of type SDO_GEOMETRY.
