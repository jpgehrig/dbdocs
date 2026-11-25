## A  Installation, Migration, Compatibility, and Upgrade

This appendix provides information about installation, migration, compatibility, and upgrade relating to Oracle Spatial and Graph.

If you are upgrading to the current Oracle Database release, Oracle Spatial and Graph is automatically upgraded as part of the operation. For information about the upgrade procedure, see [Oracle Database Upgrade Guide](../upgrd/major-steps-upgrade-process-oracle-database.md).

If you need to downgrade Spatial and Graph to the previous Oracle Database release, follow the instructions for downgrading a database back to the previous Oracle Database release in [Oracle Database Upgrade Guide](../upgrd/downgrading-oracle-db-after-upgrade.md).

If you need to migrate spatial data from one database to another, see Migrating Spatial Data from One Database to Another.

If you use Oracle Spatial and Graph GeoRaster, see Ensuring That GeoRaster Works Properly After an Installation or Upgrade.

If you are using Spatial and Graph Web Feature Service (WFS) or Catalog Services for the Web (CSW) support, and if you have data from a previous release that was indexed using one or more SYS.XMLTABLEINDEX indexes, see Index Maintenance Before and After an Upgrade (WFS and CSW).

If you need to support geometries with more than 1,048,576 ordinates, see Increasing the Size of Ordinate Arrays to Support Very Large Geometries.

- Manually Installing Spatial and Graph
- Migrating Spatial Data from One Database to Another
- Ensuring That GeoRaster Works Properly After an Installation or Upgrade
- Index Maintenance Before and After an Upgrade (WFS and CSW)
- Increasing the Size of Ordinate Arrays to Support Very Large Geometries

**Parent topic:** [Supplementary Information](spatial-supplementary-information.md)

### A.1 Manually Installing Spatial and Graph

This section applies if you do not have Oracle Spatial and Graph installed by default at the time of Oracle Database installation and you want to install Spatial and Graph later.

To install Spatial and Graph manually, you must execute the following steps using a SQL based interface such as SQL Developer or SQLPLUS:

1.  Connect to Oracle Database as `SYSDBA`:

        CONNECT / AS SYSDBA

2.  Execute the `mdinst.sql` script as shown:

        @$ORACLE_HOME/md/admin/mdinst.sql

#### Multitenant Installations

To install Spatial and Graph in CDB\$ROOT and all the PDBs in a multitenant environment, run the `catcon.pl` script to execute `mdinst.sql` as shown:

    cd $ORACLE_HOME/perl/bin/
    perl $ORACLE_HOME/rdbms/admin/catcon.pl -u sys/knl_test7 -s -e -b mdinst.log mdinst.sql > mdinst_catcon.log >> mdinst_catcon.err

**Note:**

Spatial and Graph must always be installed in CDB\$ROOT before it is installed in any other PDBs.

If you want to install Spatial and Graph only in some specific PDBs, see [Running Oracle-Supplied SQL Scripts in a CDB](../multi/administering-a-cdb-with-sql-plus.md) for more information.

**Parent topic:** Installation, Migration, Compatibility, and Upgrade

### A.2 Migrating Spatial Data from One Database to Another

Migrating spatial data refers to moving or copying Oracle Spatial and Graph geometry objects from one Oracle database to another. (The databases can have the same or different Oracle Database release numbers.)

If you are migrating spatial data using database links, export/import, Oracle Data Pump, or transportable tablespaces, the MDSYS schema must already exist in the destination database.

In limited situations you might also need to use the [SDO_MIGRATE.TO_CURRENT](SDO_MIGRATE-reference.md) subprogram (described in [SDO_MIGRATE Package (Upgrading)](SDO_MIGRATE-reference.md) ). See the Usage Notes for that subprogram.

**Parent topic:** Installation, Migration, Compatibility, and Upgrade

### A.3 Ensuring That GeoRaster Works Properly After an Installation or Upgrade

To use the GeoRaster feature of Oracle Spatial and Graph, you must enable it.

After an upgrade, verify that GeoRaster objects and data are valid and that GeoRaster is enabled for all schemas that use the feature, as explained in “Maintaining GeoRaster Objects and System Data in the Database” in [Oracle Spatial and Graph GeoRaster Developer's Guide](../geors/georaster-database-creation-management.md).

- Enabling GeoRaster at the Schema Level

**Parent topic:** Installation, Migration, Compatibility, and Upgrade

#### A.3.1 Enabling GeoRaster at the Schema Level

GeoRaster must be enabled for each database schema that will use the GeoRaster feature.

By default, the GeoRaster feature is disabled after the Oracle Spatial and Graph is initially installed. GeoRaster can be enabled only within the scope of a schema (that is, not for the entire database), and it must be enabled for each schema that will use the GeoRaster feature.

To enable GeoRaster, follow these steps for each schema for which GeoRaster will be enabled:

1.  Ensure that the user for this schema has the `CREATE TRIGGER` privilege (which is required for GeoRaster to work properly). If the user does not have the `CREATE TRIGGER` privilege (or if you do not know), connect as a user with DBA privilege and execute the following code:
        GRANT CREATE TRIGGER TO scott;
2.  Connect to the database as the user for that schema. For example:
        CONNECT scott/<password-for-scott>
3.  Enter the following statement:
        EXECUTE SDO_GEOR_ADMIN.enableGeoRaster;
4.  Verify that GeoRaster is now enabled by checking that the following statement returns `TRUE`:
        SELECT SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

For each database schema, [SDO_GEOR_ADMIN.enableGeoRaster](../geors/SDO_GEOR_ADMIN-reference.md) only needs to be called once. In any case, user can call [SDO_GEOR_ADMIN.isGeoRasterEnabled](../geors/SDO_GEOR_ADMIN-reference.md) function to check if GeoRaster feature is enabled. [SDO_GEOS_ADMIN.disableGeoRaster](../geors/SDO_GEOR_ADMIN-reference.md) procedure can be used to disable GeoRaster feature for the database schema.

If a GeoRaster table has been created and populated with data, then after a database upgrade, GeoRaster is automatically enabled for that table’s schema, and you do not need to re-enable GeoRaster for the schema. (Just ensure that the CREATE TRIGGER privilege is granted to the user.)

**Parent topic:** Ensuring That GeoRaster Works Properly After an Installation or Upgrade

### A.4 Index Maintenance Before and After an Upgrade (WFS and CSW)

Effective with Release 11.2, the SYS.XMLTABLEINDEX index type is deprecated, and therefore the Spatial WFS and CSW `createXMLTableIndex` methods create indexes of type XDB.XMLINDEX instead of type SYS.XMLTABLEINDEX as in previous releases. However, if you have data from a previous release that was indexed using one or more SYS.XMLTABLEINDEX indexes, you must drop the associated indexes before the upgrade and re-create the indexes after the upgrade, as follows:

1.  Using Oracle Database Release 11.1, call the `dropXMLTableIndex` method (in `oracle.spatial.csw.CSWAdmin` or `oracle.spatial.wfs.WFSAdmin`, as appropriate depending on the application) to drop associated indexes.

2.  Upgrade the database from Release 11.1 to Release 11.2.

3.  Using Oracle Database Release 11.2, call the `createXMLTableIndex` (in `oracle.spatial.csw.CSWAdmin` or `oracle.spatial.wfs.WFSAdmin`, as appropriate depending on the application) to create indexes that were dropped in step 1.

For information about Spatial and Graph Web Feature Service (WFS) support, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

For information about Spatial and Graph Catalog Services for the Web (CSW) support, see [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

**Parent topic:** Installation, Migration, Compatibility, and Upgrade

### A.5 Increasing the Size of Ordinate Arrays to Support Very Large Geometries

If you need to support geometries with more than 1,048,576 ordinates, you must follow the instructions in this section. However, doing so involves significant extra work (running a script, migrating existing spatial data), some database downtime, and some considerations and restrictions. Therefore, you should not perform the actions in this section unless you need to.

To increase the size of ordinate arrays to support geometries with up to 10M ordinates, follow these steps:

1.  Ensure that no users are using any spatial tables or Oracle Spatial and Graph features.
2.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).
3.  If any materialized views exist on tables containing SDO_GEOMETRY columns, drop all such materialized views before performing the next step (running `sdoupggeom.sql`).
    You can re-create these materialized views after the upgrade operation is completed.
4.  Enter the following statement:
    - Linux: `@$ORACLE_HOME/md/admin/sdoupggeom.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\sdoupggeom.sql`

    One of the actions of the `sdoupggeom.sql` script is to automatically migrate all spatial data to accommodate the new SDO_ORDINATE_ARRAY definition. This script may take a long time to complete, and the amount of time will depend on the amount of spatial data that exists in the database.

After you perform these steps, the following considerations and restrictions apply:

- Any existing transportable tablespaces that were created with the old SDO_ORDINATE_ARRAY definition will not work.

- If an export file was created using the Original Export utility on a database with the old SDO_ORDINATE_ARRAY definition, and if that file needs to be imported into a database that is using the new SDO_ORDINATE_ARRAY definition, you must specify the `TOID_NOVALIDATE` flag with the Original Import utility, as in the following example:

      imp scott/<password> file=states.dmp tables=states TOID_NOVALIDATE=MDSYS.SDO_GEOMETRY,MDSYS.SDO_ORDINATE_ARRAY,MDSYS.SDO_ELEM_INFO_ARRAY

- If you plan to use Oracle Data Pump to import data after `sdoupggeom.sql` has been executed on a source database, you must also run `sdoupggeom.sql` on the target (destination) database after the import operation.

**Parent topic:** Installation, Migration, Compatibility, and Upgrade
