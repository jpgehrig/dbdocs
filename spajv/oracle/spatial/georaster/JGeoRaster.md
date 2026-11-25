Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeorSpatialReference.md)
- [Next Class](JGeoRasterMeta.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.georaster

## Class JGeoRaster

- java.lang.Object

- - oracle.spatial.georaster.JGeoRaster

<!-- -->

-

  ------------------------------------------------------------------------



      public class JGeoRaster
      extends java.lang.Object

  JGeoRaster is a Java class mapped to the Oracle Spatial GeoRaster SQL type MDSYS.SDO_GEORASTER, and it provides the capability to access, manipulate, and visualize the GeoRaster objects stored in an Oracle Spatial database.
  Two constructors are defined in the class to allow users to initiate an instance based on different parameters:

               public JGeoRaster(STRUCT georaster) throws Exception

               public JGeoRaster(Connection conn, String rasterDataTable, NUMBER rasterID) throws GeoRasterException

  Here is sample code showing how to use these two constructors:
            /// reading a GeoRaster object from database based on a query
            ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
            STRUCT geor = (STRUCT) rs.getObject(1);
            //convert STRUCT into JGeoRaster
            JGeoRaster j_geor = new JGeoRaster(geor);
            or
            /// reading a GeoRaster object from database based on connection,RDT and rid.
            JGeoRaster j_geor = new JGeoRaster(conn,rasterDataTable,rasterID);

  When a constructor is invoked to initiate a JGeoRaster object, the following tasks will be done in the init process:

            * Validate connection, rdt, and rid, and make sure they identify a valid GeoRaster object in the target database.
            * Fetch rasterType, spatialExtent, and schema/table/column name of the target Georaster object to
              initiate attributes of JGeoRaster object.
            * Fetch metadata XML string of the target Georaster object to initiate the contained JGeoRasterMeta object,
              for JGeoRasterMeta initiation, check class JGeoRasterMeta.
              Note:If current GeoRaster object is an empty GeoRaster object(created by function init()), then the
              following xml string will be used to initiate JGeoRasterMeta
              ""


  After a JGeoRaster is successfully initialized, the JGeoRaster object is associated with the corresponding GeoRaster object in the target database through RDT and rid, and it is also working as a root access point of all GeoRaster Java API operations, from which users can deal with different tasks, like:
            * Retrieving and updating metadata
            * Retrieving and updating raster data
            * Visualizing GeoRaster objects
            * Accessing the server-side PL/SQL API through JDBC

  To get other GeoRaster Java objects from a JGeoRaster object:
            //get an instance of JGeoRasterMeta to deal with metadata
            public JGeoRasterMeta getMetadataObject()

            //get an instance of JRaster to deal with raster data
            public JRaster getRasterObject()

            //get an instance of GeoRasterImage to deal with visualization
            public GeoRasterImage getGeoRasterImageObject()

            //get an instance of SdoGeorPKG to access PL/SQL APIs in the package SOD_GEOR through JDBC
            public SdoGeorPKG getSdoGeorPKG()


  Note that this class may not be synchronized with server-side changes.If one thread is reading this GeoRaster object and another is modifying it (such as changing its metadata), there may be inconsistencies. It is not synchronized with any raster data or metadata update through the SdoGeorPKG in the same thread either. In other words, the changes made by any other parties other than by the current JGeoRaster instance and its associated metadata and raster objects are not reflected in the current JGeoRaster instance.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JGeoRaster``(java.sql.Connection conn, java.lang.String rasterDataTable, NUMBER rasterID)`<br>Constructs an `GeoRaster` object with given connection, rasterDataTable, and rasterID. |
    | `JGeoRaster``(oracle.sql.STRUCT georaster)`<br>Deprecated.                                                                                                                            |
    | `JGeoRaster``(java.sql.Struct georaster, java.sql.Connection conn)`<br>Constructs an `GeoRaster` object with the given Struct and connection.                                         |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                      |
    |---------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.sql.Connection`                       | `getConnection``()`<br>Returns the connection object associated with current GeoRaster object.                                                                                                              |
    | `java.lang.String`                          | `getGeoRasterColumn``()`<br>Returns the column where the current GeoRaster is stored.                                                                                                                       |
    | [`GeoRasterImage`](image/GeoRasterImage.md) | `getGeoRasterImageObject``()`<br>Deprecated.                                                                                                                                                                |
    | `java.lang.String`                          | `getGeoRasterTable``()`<br>Returns the table where the current GeoRaster is stored.                                                                                                                         |
    | [`JGeoRasterMeta`](JGeoRasterMeta.md)       | `getMetadataObject``()`<br>Returns the JGeoRasterMeta object contained in this JGeoRaster object.                                                                                                           |
    | `static oracle.sql.STRUCT`                  | `getOracleSTRUCT``(java.lang.Object o)`<br>Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc.                                                                |
    | `static java.sql.Struct`                    | `getOracleSTRUCTJS``(java.lang.Object o)`<br>Returns java.sql.Struct while running within WLS or any J2EE container such as OC4J, JBoss etc.                                                                |
    | `java.lang.String`                          | `getRasterDataTable``()`<br>Returns the raster data table where the current GeoRaster is stored.                                                                                                            |
    | `NUMBER`                                    | `getRasterID``()`<br>Returns the raster ID assigned to the current GeoRaster.                                                                                                                               |
    | [`JRaster`](JRaster.md)                     | `getRasterObject``()`<br>Returns the JRaster object contained in this JGeoRaster object.                                                                                                                    |
    | `int`                                       | `getRasterType``()`<br>Returns the raster type.                                                                                                                                                             |
    | `java.lang.String`                          | `getSchemaName``()`<br>Returns the schema where the current GeoRaster is stored.                                                                                                                            |
    | [`SdoGeorPKG`](sql/SdoGeorPKG.md)           | `getSdoGeorPKG``()`<br>Returns a SdoGeorPKG object, which is used to remotely execute PL/SQL functions and procedures defined in the server-side package SDO_GEOR.                                          |
    | [`JGeometry`](../geometry/JGeometry.md)     | `getSpatialExtent``()`<br>Returns the spatial extent.                                                                                                                                                       |
    | `void`                                      | `loadFromDB``()`<br>Fetches data from GeoRaster object in the Oracle Database server, which is associated with current JGeoRaster object by RDT and RID, and reinitiates JGeoRaster instance with new data. |
    | `void`                                      | `setConnection``(java.sql.Connection connection)`<br>Sets the connection object associated with current GeoRaster object.                                                                                   |
    | `void`                                      | `setRasterType``(int rasterType)`<br>Sets the rasterType.                                                                                                                                                   |
    | `void`                                      | `setSpatialExtent``(`[`JGeometry`](../geometry/JGeometry.md)` spatialExtent)`<br>Sets the spatial extent.                                                                                                   |
    | `void`                                      | `storeToDB``()`<br>Updates the GeoRaster object in the Oracle Database server, which is associated with current JGeoRaster object by RDT and RID.                                                           |
    | `boolean`                                   | `validate``()`<br>Validates the current JGeoRaster object.                                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JGeoRaster

          @Deprecated
          public JGeoRaster(oracle.sql.STRUCT georaster)
                                  throws java.lang.Exception

      Deprecated. 
      Constructs an `GeoRaster` object with the given STRUCT.
      Parameters:
      `georaster` - GeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### JGeoRaster

          public JGeoRaster(java.sql.Struct georaster,
                            java.sql.Connection conn)
                     throws java.lang.Exception

      Constructs an `GeoRaster` object with the given Struct and connection.
      Parameters:
      `georaster` - GeoRaster object

      `conn` - db connection

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### JGeoRaster

          public JGeoRaster(java.sql.Connection conn,
                            java.lang.String rasterDataTable,
                            NUMBER rasterID)
                     throws GeoRasterException

      Constructs an `GeoRaster` object with given connection, rasterDataTable, and rasterID.
      Parameters:
      `conn` - connection to an oracle database

      `rasterDataTable` - raster data table

      `rasterID` - raster ID number

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

  <!-- -->

  - ### Method Detail

    - #### getRasterType

          public int getRasterType()

      Returns the raster type.
      Returns:
      raster type.

    <!-- -->

    - #### setRasterType

          public void setRasterType(int rasterType)

      Sets the rasterType.
      Parameters:
      `rasterType` - raster type

    <!-- -->

    - #### getMetadataObject

          public JGeoRasterMeta getMetadataObject()

      Returns the JGeoRasterMeta object contained in this JGeoRaster object.
      Returns:
      JGeoRasterMeta object contained in this JGeoRaster object.

    <!-- -->

    - #### getRasterObject

          public JRaster getRasterObject()

      Returns the JRaster object contained in this JGeoRaster object.
      Returns:
      JRaster object contained in this JGeoRaster object.

    <!-- -->

    - #### getGeoRasterImageObject

          @Deprecated
          public GeoRasterImage getGeoRasterImageObject()

      Deprecated. 
      Creates a GeoRasterImage object, which is an image rendering engine, and by which any portion (rectangle) of GeoRaster object can be retrieved as a renderable image.
      Returns:
      a GeoRasterImage object.

    <!-- -->

    - #### getSdoGeorPKG

          public SdoGeorPKG getSdoGeorPKG()

      Returns a SdoGeorPKG object, which is used to remotely execute PL/SQL functions and procedures defined in the server-side package SDO_GEOR.
      Returns:
      a SdoGeorPKG object.

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns the connection object associated with current GeoRaster object.
      Returns:
      the connection object associated with current GeoRaster object.

    <!-- -->

    - #### getSchemaName

          public java.lang.String getSchemaName()

      Returns the schema where the current GeoRaster is stored.
      Returns:
      the schema where the current GeoRaster is stored.

    <!-- -->

    - #### getGeoRasterTable

          public java.lang.String getGeoRasterTable()

      Returns the table where the current GeoRaster is stored.
      Returns:
      the table where the current GeoRaster is stored.

    <!-- -->

    - #### getGeoRasterColumn

          public java.lang.String getGeoRasterColumn()

      Returns the column where the current GeoRaster is stored.
      Returns:
      the column where the current GeoRaster is stored.

    <!-- -->

    - #### getRasterDataTable

          public java.lang.String getRasterDataTable()

      Returns the raster data table where the current GeoRaster is stored.
      Returns:
      the raster data table where the current GeoRaster is stored.

    <!-- -->

    - #### getRasterID

          public NUMBER getRasterID()

      Returns the raster ID assigned to the current GeoRaster.
      Returns:
      the raster ID assigned to the current GeoRaster.

    <!-- -->

    - #### setSpatialExtent

          public void setSpatialExtent(JGeometry spatialExtent)

      Sets the spatial extent.

    <!-- -->

    - #### getSpatialExtent

          public JGeometry getSpatialExtent()

      Returns the spatial extent.
      Returns:
      spatial extent as a JGeometry.

    <!-- -->

    - #### storeToDB

          public void storeToDB()
                         throws java.lang.Exception

      Updates the GeoRaster object in the Oracle Database server, which is associated with current JGeoRaster object by RDT and RID. All changes are based on changes in the current JGeoRaster object in the Java side.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### loadFromDB

          public void loadFromDB()
                          throws GeoRasterException

      Fetches data from GeoRaster object in the Oracle Database server, which is associated with current JGeoRaster object by RDT and RID, and reinitiates JGeoRaster instance with new data.
      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### validate

          public boolean validate()
                           throws java.lang.Exception

      Validates the current JGeoRaster object.
      Returns:
      true or false to indicate if current JGeoRaster is valid.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getOracleSTRUCT

          public static oracle.sql.STRUCT getOracleSTRUCT(java.lang.Object o)
                                                   throws java.lang.Exception

      Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `o` - object in a result set

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getOracleSTRUCTJS

          public static java.sql.Struct getOracleSTRUCTJS(java.lang.Object o)
                                                   throws java.lang.Exception

      Returns java.sql.Struct while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `o` - object in a result set

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setConnection

          public void setConnection(java.sql.Connection connection)

      Sets the connection object associated with current GeoRaster object.
      Parameters:
      `conn` - the connection object associated with current GeoRaster object

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeorSpatialReference.md)
- [Next Class](JGeoRasterMeta.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
