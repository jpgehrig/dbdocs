Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](SdoGeorAggrPKG.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.georaster.sql

## Class SdoGeorAdminPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorAdminPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorAdminPKG
      extends java.lang.Object

  SdoGeorAdminPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR_ADMIN. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorAdminPKG
         SdoGeorAdminPKG  pkg=new SdoGeorAdminPKG(connection);
         //do upgrade
         pkg.upgradeGeoRaster();

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------|
    | `SdoGeorAdminPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorAdminPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                           |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`    | `checkSysdataEntries``()`<br>Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries.                                                                      |
    | `java.sql.Connection` | `getConnection``()`<br>Returns a connection which points to target database.                                                                                     |
    | `boolean`             | `isRDTNameUnique``(java.lang.String rdtName)`<br>Checks if the specified raster data table (RDT) name is unique among RDT names in the database.                 |
    | `java.lang.String`    | `isUpgradeNeeded``()`<br>Checks the GeoRaster system data entries and GeoRaster data for the current schema.                                                     |
    | `java.lang.String`    | `listDanglingRasterData``()`<br>Checks the GeoRaster system data entries and GeoRaster data, and lists all dangling raster data.                                 |
    | `java.lang.String`    | `listGeoRasterColumns``()`<br>Lists the GeoRaster columns defined in the current schema.                                                                         |
    | `java.lang.String`    | `listGeoRasterObjects``()`<br>Lists the GeoRaster objects defined in the current schema.                                                                         |
    | `java.lang.String`    | `listGeoRasterTables``()`<br>Lists the GeoRaster tables defined in the current schema.                                                                           |
    | `java.lang.String`    | `listRDT``()`<br>Lists the raster data tables (RDTs) defined in the current schema.                                                                              |
    | `java.lang.String`    | `listRegisteredRDT``()`<br>Lists registered raster data tables (RDTs) defined in the current schema.                                                             |
    | `java.lang.String`    | `listUnregisteredRDT``()`<br>Lists unregistered raster data tables (RDTs) defined in the current schema.                                                         |
    | `java.lang.String`    | `maintainSysdataEntries``()`<br>Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries, and takes corrective action as appropriate.                       |
    | `void`                | `registerGeoRasterColumns``()`<br>Creates DML triggers for all GeoRaster columns defined in the current schema.                                                  |
    | `void`                | `registerGeoRasterObjects``()`<br>Registers all GeoRaster objects defined in the current schema.                                                                 |
    | `void`                | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                          |
    | `java.lang.String`    | `upgradeGeoRaster``()`<br>Checks the GeoRaster system data entries and GeoRaster data for the current schema, and performs any corrective action as appropriate. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoGeorAdminPKG

          public SdoGeorAdminPKG(java.sql.Connection conn)

      Constructs an `SdoGeorAdminPKG` object using the given connection.
      Parameters:
      `conn` - a JDBC connection.

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public void setConnection(java.sql.Connection conn)

      Sets the connection which points to the target database.
      Parameters:
      `conn` - a JDBC connection

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns a connection which points to target database.
      Returns:
      a connection which points to target database.

    <!-- -->

    - #### checkSysdataEntries

          public java.lang.String checkSysdataEntries()
                                               throws java.lang.Exception

      Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries. If you call this function while connected as the MDSYS user, the entries in the ALL_SDO_GEOR_SYSDATA view instead of the USER_SDO_GEOR_METADATA view are checked.
      Returns:
      an list of GeoRaster system data entries that are invalid. It checks for errors such as the following: The RDT name is not unique. The GeoRaster table does not exist. The GeoRaster column does not exist. The GeoRaster objects does not exist. The GeoRaster object is non-empty or nonblank, but the RDT does not exist. Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isRDTNameUnique

          public boolean isRDTNameUnique(java.lang.String rdtName)
                                  throws java.lang.Exception

      Checks if the specified raster data table (RDT) name is unique among RDT names in the database.
      Parameters:
      `rdtName` - Name to be checked for uniqueness.

      Returns:
      true/false to indicate if a raster data table (RDT) name is unique among RDT names in the database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isUpgradeNeeded

          public java.lang.String isUpgradeNeeded()
                                           throws java.lang.Exception

      Checks the GeoRaster system data entries and GeoRaster data for the current schema. This function returns an array of comma-delimited list of GeoRaster system data entries and GeoRaster columns and objects that are invalid. It can report errors such as the following: System data entry error, the RDT name is not unique. System data entry error, the RDT/RID pair is not unique. System data entry error, the GeoRaster table does not exist. System data entry error, the GeoRaster column does not exist. System data entry error, the GeoRaster object does not exist. The GeoRaster object is non-empty or nonblank, but the RDT does not exist. Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID). There is a non-registered pair of (GeoRaster column, GeoRaster object). If you call this function while connected as the MDSYS user, the GeoRaster system data entries and GeoRaster data for the entire database are checked.
      Returns:
      an list of GeoRaster system data entries that are invalid.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listGeoRasterColumns

          public java.lang.String listGeoRasterColumns()
                                                throws java.lang.Exception

      Lists the GeoRaster columns defined in the current schema. This function returns an array of comma-delimited list of GeoRaster columns with their registration status. The list contains the following information: Schema name (only if you are connected as the MDSYS user) GeoRaster table name GeoRaster column name Status: registered (a DML trigger is created for the GeoRaster column) or unregistered (no DML trigger is created for the GeoRaster column) If you call this function while connected as the MDSYS user, all GeoRaster columns defined in the database are listed.
      Returns:
      A list of GeoRaster columns defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listGeoRasterObjects

          public java.lang.String listGeoRasterObjects()
                                                throws java.lang.Exception

      Lists the GeoRaster objects defined in the current schema. This function returns an array of comma-delimited list of GeoRaster objects with their registration status. The list contains the following information: Schema name (only if you are connected as the MDSYS user) GeoRaster table name GeoRaster column name RDT name Raster ID Status: registered (the GeoRaster object has been registered is the SYSDATA table) or unregistered (the GeoRaster object has not been registered is the SYSDATA table) If you call this function while connected as the MDSYS user, all GeoRaster objects defined in the database are listed.
      Returns:
      A list of GeoRaster objects defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listGeoRasterTables

          public java.lang.String listGeoRasterTables()
                                               throws java.lang.Exception

      Lists the GeoRaster tables defined in the current schema. This function returns an array of comma-delimited list of GeoRaster tables. The list contains the following information: Schema name (only if you are connected as the MDSYS user) GeoRaster table name If you call this function while connected as the MDSYS user, all GeoRaster tables defined in the database are listed.
      Returns:
      A list of GeoRaster tables defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listDanglingRasterData

          public java.lang.String listDanglingRasterData()
                                                  throws java.lang.Exception

      Checks the GeoRaster system data entries and GeoRaster data, and lists all dangling raster data. If you call this function while connected as the MDSYS user, all dangling raster data in the database is listed.
      Returns:
      A list of all dangling raster data defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listRDT

          public java.lang.String listRDT()
                                   throws java.lang.Exception

      Lists the raster data tables (RDTs) defined in the current schema. If you call this function while connected as the MDSYS user, all RDT in the database is listed.
      Returns:
      A list of rdts defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listRegisteredRDT

          public java.lang.String listRegisteredRDT()
                                             throws java.lang.Exception

      Lists registered raster data tables (RDTs) defined in the current schema. If you call this function while connected as the MDSYS user, all registered RDT in the database is listed.
      Returns:
      A list of registered rdts defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### listUnregisteredRDT

          public java.lang.String listUnregisteredRDT()
                                               throws java.lang.Exception

      Lists unregistered raster data tables (RDTs) defined in the current schema. If you call this function while connected as the MDSYS user, all unregistered RDT in the database is listed.
      Returns:
      A list of unregistered rdts defined in the current schema or database.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### maintainSysdataEntries

          public java.lang.String maintainSysdataEntries()
                                                  throws java.lang.Exception

      Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries, and takes corrective action as appropriate. This function performs the same checks as the SDO_GEOR_ADMIN.checkSysdataEntries function, and it takes the corrective action that is appropriate (if any). For each of the following errors, the function does the following: The RDT name is not unique. If you are connected as a user other then MDSYS, no action is taken; if you are connected as user MDSYS, duplicate RDTs are renamed so that their names are unique. The GeoRaster table does not exist. The entry is deleted. The GeoRaster column does not exist. The entry is deleted. The GeoRaster objects does not exist. The entry is deleted. The GeoRaster object is non-empty or nonblank, but the RDT does not exist. The entry is deleted. Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID). The entry is deleted. If you call this function while connected as the MDSYS user, the entries in the ALL_SDO_GEOR_SYSDATA view instead of the USER_SDO_GEOR_METADATA view are checked.
      Returns:
      A list of actions executed by this function.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### registerGeoRasterColumns

          public void registerGeoRasterColumns()
                                        throws java.lang.Exception

      Creates DML triggers for all GeoRaster columns defined in the current schema. If you execute this procedure while connected as the MDSYS user, DML triggers are created for all GeoRaster columns defined in all schemas.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### registerGeoRasterObjects

          public void registerGeoRasterObjects()
                                        throws java.lang.Exception

      Registers all GeoRaster objects defined in the current schema. If you execute this procedure while connected as the MDSYS user, all GeoRaster objects defined in all schemas are registered.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### upgradeGeoRaster

          public java.lang.String upgradeGeoRaster()
                                            throws java.lang.Exception

      Checks the GeoRaster system data entries and GeoRaster data for the current schema, and performs any corrective action as appropriate. This function performs the same checks as the SDO_GEOR_ADMIN.isUpgradeNeeded function, and it takes the corrective action that is appropriate (if any) for the following errors: System data entry error, the RDT name is not unique. System data entry error, the RDT/RID pair is not unique. System data entry error, the GeoRaster table does not exist. System data entry error, the GeoRaster column does not exist. System data entry error, the GeoRaster object does not exist. The GeoRaster object is non-empty or nonblank, but the RDT does not exist. Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID). There is a non-registered pair of (GeoRaster column, GeoRaster object). If you call this function while connected as the MDSYS user, the GeoRaster system data entries and GeoRaster data for the entire database are checked, and any appropriate corrective actions are taken.
      Returns:
      A list of actions executed by this function.

      Throws:
      `java.lang.Exception`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](SdoGeorAggrPKG.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
