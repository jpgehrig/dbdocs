## 8 SDO_GEOR_ADMIN Package Reference

The SDO_GEOR_ADMIN package contains subprograms (functions and procedures) for administrative operations related to GeoRaster. This chapter presents reference information, with one or more examples, for each subprogram.

- SDO_GEOR_ADMIN.checkSysdataEntries
- SDO_GEOR_ADMIN.disableGeoRaster
- SDO_GEOR_ADMIN.enableGeoRaster
- SDO_GEOR_ADMIN.isGeoRasterEnabled
- SDO_GEOR_ADMIN.isRDTNameUnique
- SDO_GEOR_ADMIN.isUpgradeNeeded
- SDO_GEOR_ADMIN.listGeoRasterColumns
- SDO_GEOR_ADMIN.listGeoRasterObjects
- SDO_GEOR_ADMIN.listGeoRasterTables
- SDO_GEOR_ADMIN.listDanglingRasterData
- SDO_GEOR_ADMIN.listRDT
- SDO_GEOR_ADMIN.listRegisteredRDT
- SDO_GEOR_ADMIN.listUnregisteredRDT
- SDO_GEOR_ADMIN.maintainSysdataEntries
- SDO_GEOR_ADMIN.registerGeoRasterColumns
- SDO_GEOR_ADMIN.registerGeoRasterObjects
- SDO_GEOR_ADMIN.upgradeGeoRaster

### 8.1 SDO_GEOR_ADMIN.checkSysdataEntries

#### Format

    SDO_GEOR_ADMIN.checkSysdataEntries() RETURN SDO_STRING2_ARRAY;

#### Description

Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of GeoRaster system data entries that are invalid. It checks for errors such as the following:

- The RDT name is not unique.

- The GeoRaster table does not exist.

- The GeoRaster column does not exist.

- The GeoRaster objects does not exist.

- The GeoRaster object is non-empty or nonblank, but the RDT does not exist.

- Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID).

If you execute this function as a user with DBA role, then the function checks the GeoRaster system data entries across the database. Otherwise, it only checks the GeoRaster system data entries for the current schema.

The USER_SDO_GEOR_DATA and ALL_SDO_GEOR_SYSDATA views are described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md).

#### Examples

The following example checks the USER_SDO_GEOR_SYSDATA view for invalid entries under the current user schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.checkSysdataEntries FROM DUAL);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    The RDT name "RDT1" is not unique
    The GeoRaster object GEOR_TEST1.TABLE1.GEOR: RDT=RDT2 RID=3 is associated with a
     non-existing RDT table!
    The specification of GeoRaster column GEOR_TEST1.TABLE1.c1  is not correct.
    The GeoRaster object GEOR_TEST1.TABLE1.geor: RDT=dt3 RID=2 doesn't exist!
    The GeoRaster table GEOR_TEST1.t1  doesn't exist!

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.2 SDO_GEOR_ADMIN.disableGeoRaster

#### Format

    SDO_GEOR_ADMIN.disableGeoRaster();

#### Description

Disables the GeoRaster feature for the calling user in the database.

#### Parameters

None.

#### Usage Notes

This procedure disables the GeoRaster feature for the calling user. When this procedure is called, the session's current schema name must be the same as the session's current user name.

If there is any table that has SDO_GEORASTER column, this table will not be accessible after the GeoRaster feature is disabled. Calling SDO_GEOR_ADMIN.enableGeoRaster procedure will enable the access to this table again.

#### Examples

The following example disables the GeoRaster feature for the current session user.

    SQL> EXECUTE SDO_GEOR_ADMIN.disableGeoRaster;

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.3 SDO_GEOR_ADMIN.enableGeoRaster

#### Format

    SDO_GEOR_ADMIN.enableGeoRaster();

#### Description

Enables the GeoRaster feature for the current schema.

#### Parameters

None.

#### Usage Notes

The session user that calls the `SDO_GEOR_ADMIN.enableGeoRaster()` procedure must be same as the database user for the current schema.

The user must have the `CREATE TRIGGER` privilege.

#### Examples

The following example checks if GeoRaster is enabled for the current schema (before it is enabled), then enables GeoRaster for the current schema, and then again checks if GeoRaster is enabled for the current schema.

    SQL> SELECT /*+ NO_RESULT_CACHE */ SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

    ISGEORASTERENABLED
    ------------------------------------------------------------------------------
    FALSE

    SQL> EXECUTE SDO_GEOR_ADMIN.enableGeoRaster;

    PL/SQL procedure successfully completed.

    SQL> SELECT /*+ NO_RESULT_CACHE */ SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

    ISGEORASTERENABLED
    ------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.4 SDO_GEOR_ADMIN.isGeoRasterEnabled

#### Format

    SDO_GEOR_ADMIN.isGeoRasterEnabled() RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the GeoRaster feature is enabled for the current schema; returns the string `FALSE` if GeoRaster is not enabled for the current schema.

#### Parameters

None.

#### Usage Notes

The session user that calls `SDO_GEOR_ADMIN.isGeoRasterEnabled()` function must be same as the database user for the current schema.

The user must have the `CREATE TRIGGER` privilege.

When executing `SDO_GEOR_ADMIN.isGeoRasterEnabled()` function, avoid using Oracle result cache by adding the `NO_RESULT_CACHE` hint in the query.

#### Examples

The following example checks if GeoRaster is enabled for the current schema (before it is enables), then enables GeoRaster for the current schema, and then again checks if GeoRaster is enabled for the current schema.

    SQL> SELECT /*+ NO_RESULT_CACHE */ SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

    ISGEORASTERENABLED
    -------------------------------------------------------------------------------
    FALSE

    SQL> EXECUTE SDO_GEOR_ADMIN.enableGeoRaster;

    PL/SQL procedure successfully completed.

    SQL> SELECT /*+ NO_RESULT_CACHE */ SDO_GEOR_ADMIN.isGeoRasterEnabled FROM DUAL;

    ISGEORASTERENABLED
    -------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.5 SDO_GEOR_ADMIN.isRDTNameUnique

#### Format

    SDO_GEOR_ADMIN.isRDTNameUnique(
         rdtName VARCHAR2)
         RETURN  VARCHAR2;

#### Description

Checks if the specified raster data table (RDT) name is unique among RDT names in the database.

#### Parameters

rdtName
Name to be checked for uniqueness.

#### Usage Notes

You can use this function to check, before you create an RDT, if the RDT name that you plan to use is unique.

This function returns the string `TRUE` if the name is unique and the string `FALSE` if the name is not unique.

#### Examples

The following example checks if the name `MY_RDT` is unique.

    SELECT SDO_GEOR_ADMIN.IsRDTNameUnique('MY_RDT')  FROM DUAL;

    SDO_GEOR_ADMIN.ISRDTNAMEUNIQUE('MY_RDT')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.6 SDO_GEOR_ADMIN.isUpgradeNeeded

#### Format

    SDO_GEOR_ADMIN.isUpgradeNeeded() RETURN SDO_STRING2_ARRAY;

#### Description

Checks the GeoRaster system data entries and GeoRaster data for the current schema or for all the schemas in the database.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of GeoRaster system data entries and GeoRaster columns and objects that are invalid. It can report errors such as the following:

- System data entry error, the RDT name is not unique.

- System data entry error, the RDT/RID pair is not unique.

- System data entry error, the GeoRaster table does not exist.

- System data entry error, the GeoRaster column does not exist.

- System data entry error, the GeoRaster object does not exist.

- The GeoRaster object is non-empty or nonblank, but the RDT does not exist.

- Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID).

- There is a non-registered pair of (GeoRaster column, GeoRaster object).

If you execute this function as a user with DBA role, then the function checks the GeoRaster system data entries and GeoRaster data for all the schemas in the database. Otherwise, it only checks the GeoRaster system data entries and GeoRaster data for the current schema.

#### Examples

The following example checks the GeoRaster system data entries and GeoRaster data. It assumes that you are connected as a user with DBA role.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.isUpgradeNeeded FROM DUAL);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    The following GeoRaster columns aren't registered:
         SCHEMA:GEOR_TEST TABLE:TABLE1 COLUMN:GEOR
    The following GeoRaster objects aren't registered:
         SCHEMA:GEOR_TEST TABLE:TABLE1 COLUMN:GEOR RDT:RDT RID:3
         SCHEMA:GEOR_TEST TABLE:TABLE1 COLUMN:GEOR RDT:RDT RID:4

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.7 SDO_GEOR_ADMIN.listGeoRasterColumns

#### Format

    SDO_GEOR_ADMIN.listGeoRasterColumns() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the GeoRaster columns defined in the current schema or in all the schemas in the database.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of GeoRaster columns with their registration status. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- GeoRaster table name

- GeoRaster column name

- Status: registered (a DML trigger is created for the GeoRaster column) or unregistered (no DML trigger is created for the GeoRaster column)

If you execute this function as a user with DBA role, then the function lists the GeoRaster columns defined in all the schemas in the database. Otherwise, it only lists the GeoRaster columns defined in the current schema.

#### Examples

The following example lists the GeoRaster columns defined in the current schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listGeoRasterColumns FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('TEST_TABLE1', 'GEOR', 'registered')
    SDO_STRING2_ARRAY('TEST_TABLE2', 'GEOR', 'registered')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.8 SDO_GEOR_ADMIN.listGeoRasterObjects

#### Format

    SDO_GEOR_ADMIN.listGeoRasterObjects() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the GeoRaster objects defined in the current schema or in all the schemas in the database.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of GeoRaster objects with their registration status. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- GeoRaster table name

- GeoRaster column name

- RDT name

- Raster ID

- Status: registered (the GeoRaster object has been registered in the SYSDATA table) or unregistered (the GeoRaster object has not been registered in the SYSDATA table)

If you execute this function as a user with DBA role, then the function lists the GeoRaster objects defined in all the schemas in the database. Otherwise, it only lists the GeoRaster objects defined in the current schema.

#### Examples

The following example lists the GeoRaster objects defined in the current schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listGeoRasterObjects FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('TEST_TABLE1', 'GEOR', 'RDT_REGULAR_01', '1', 'registered')
    SDO_STRING2_ARRAY('TEST_TABLE2', 'GEOR', 'RDT_REGULAR_01', '2', 'registered')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.9 SDO_GEOR_ADMIN.listGeoRasterTables

#### Format

    SDO_GEOR_ADMIN.listGeoRasterTables() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the GeoRaster tables defined in the current schema.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of GeoRaster tables. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- GeoRaster table name

If you execute this function as a user with DBA role, then the function lists the GeoRaster tables defined in all the schemas in the database. Otherwise, it only lists the GeoRaster tables defined in the current schema.

#### Examples

The following example lists the GeoRaster tables defined in the database. It assumes that you are connected as a user with DBA role.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listGeoRasterTables FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('GEOR_TEST', 'TEST_TABLE1')
    SDO_STRING2_ARRAY('GEOR_TEST', 'TEST_TABLE2')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.10 SDO_GEOR_ADMIN.listDanglingRasterData

#### Format

    SDO_GEOR_ADMIN.listDanglingRasterData() RETURN SDO_STRING2_ARRAYSET;

#### Description

Checks the GeoRaster system data entries and GeoRaster data, and lists all dangling raster data.

#### Parameters

None.

#### Usage Notes

Raster data table (RDT) rows might exist for nonexistent GeoRaster objects or GeoRaster objects that are not referred to in the SYSDATA table. The raster blocks associated with such rows are referred to dangling blocks. The dangling raster blocks cause wasted disk space in the RDT although otherwise they do not present a problem as long as the necessary primary key is defined on the RDT. To find these dangling blocks in the current schema or in all schemas, call the SDO_GEOR_ADMIN.listDanglingRasterData function.

If you execute this function as a user with DBA role, then the function lists the dangling blocks in all the schemas in the database. Otherwise, it only lists the dangling blocks in the current schema.

Before you call this function, you should call SDO_GEOR_ADMIN.registerGeoRasterObjects to register all existing GeoRaster objects.

To remove the dangling raster block data from an RDT, delete the rows associated with the problems discovered by the SDO_GEOR_ADMIN.listDanglingRasterData function.

This function returns an array of comma-delimited list of dangling raster data. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- RDT name

- Raster ID

#### Examples

The following example lists all dangling raster data in the current schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listDanglingRasterData FROM DUAL);

    COLUMN_VALUE
    --------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('RDT11', '3')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.11 SDO_GEOR_ADMIN.listRDT

#### Format

    SDO_GEOR_ADMIN.listRDT() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the raster data tables (RDTs) defined in the current schema or in all the schemas in the database.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of RDTs. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- RDT name

If you execute this function as a user with DBA role, then the function lists the RDTs in all the schemas in the database. Otherwise, it only lists the RDTs in the current schema.

#### Examples

The following example lists the RDTs defined in the current schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listRDT FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('RDT_REGULAR_01')
    SDO_STRING2_ARRAY('RDT_REGULAR_02')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.12 SDO_GEOR_ADMIN.listRegisteredRDT

#### Format

    SDO_GEOR_ADMIN.listRegisteredRDT() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the registered raster data tables (RDTs) defined in the current schema or in all the schemas in the database. An RDT is registered if at least one entry in the SYSDATA table refers to it.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of RDTs. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- RDT name

If you execute this function as a user with DBA role, then the function lists the registered RDTs in all the schemas in the database. Otherwise, it only lists the registered RDTs in the current schema.

#### Examples

The following example lists the registered RDTs defined in the current schema.

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listRegisteredRDT FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('RDT1_REGULAR_01')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.13 SDO_GEOR_ADMIN.listUnregisteredRDT

#### Format

    SDO_GEOR_ADMIN.listUnregusteredRDT() RETURN SDO_STRING2_ARRAYSET;

#### Description

Lists the unregistered raster data tables (RDTs) defined in the current schema or in all the schemas in the database. An RDT is unregistered if no entries in the SYSDATA table refer to it.

#### Parameters

None.

#### Usage Notes

This function returns an array of comma-delimited list of RDTs. The list contains the following information:

- Schema name (only if you are connected as a user with DBA role)

- RDT name

If you execute this function as a user with DBA role, then the function lists the unregistered RDTs in all the schemas in the database. Otherwise, it only lists the unregistered RDTs in the current schema.

#### Examples

    SELECT * FROM THE (SELECT SDO_GEOR_ADMIN.listUnregisteredRDT FROM DUAL);

    COLUMN_VALUE
    ---------------------------------------------------------------------------------
    SDO_STRING2_ARRAY('RDT_REGULAR_02')

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.14 SDO_GEOR_ADMIN.maintainSysdataEntries

#### Format

    SDO_GEOR_ADMIN.maintainSysdataEntries() RETURN SDO_STRING2_ARRAY;

#### Description

Checks the USER_SDO_GEOR_SYSDATA view for any invalid entries, and takes corrective action as appropriate.

#### Parameters

None.

#### Usage Notes

This function performs the same checks as the SDO_GEOR_ADMIN.checkSysdataEntries function, and it takes the corrective action that is appropriate (if any). For each of the following errors, the function does the following:

- The RDT name is not unique. If you are connected as a user without DBA role, no action is taken; if you are connected as a user with DBA role, duplicate RDTs are renamed so that their names are unique.

- The GeoRaster table does not exist. The entry is deleted.

- The GeoRaster column does not exist. The entry is deleted.

- The GeoRaster objects does not exist. The entry is deleted.

- The GeoRaster object is non-empty or nonblank, but the RDT does not exist. The entry is deleted.

- Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID). The entry is deleted.

If you execute this procedure as a user with DBA role, then the maintenance is performed in all the schemas in the database. Otherwise, the maintenance is performed in the current schema.

The USER_SDO_GEOR_DATA and ALL_SDO_GEOR_SYSDATA views are described in [GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)](georaster-datatypes.md).

#### Examples

The following example checks the USER_SDO_GEOR_SYSDATA view for invalid entries, and performs corrective action as appropriate.

    DECLARE
      ret SDO_STRING2_ARRAY;
    BEGIN
      ret:=sdo_geor_admin.MAINTAINSYSDATAENTRIES;
      for i in 1..ret.count loop
        dbms_output.put_line(ret(i));
      end loop;
    END;
    /
    The RDT name GEOR_TEST1.RDT2 is renamed to GEOR_TEST1.RDT1!
    The sysdata entry (SCHEMA=GEOR_TEST1 RDT=dt1 RID=1) is deleted!

    PL/SQL procedure successfully completed.

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.15 SDO_GEOR_ADMIN.registerGeoRasterColumns

#### Format

    SDO_GEOR_ADMIN.registerGeoRasterColumns;

#### Description

Creates DML triggers for all GeoRaster columns defined in the current schema or in all the schemas in the database.

#### Parameters

None.

#### Usage Notes

You should not normally need to execute this procedure. You should execute it only if some error or other condition has resulted in GeoRaster columns without associated DML triggers.

If you execute this procedure as a user with DBA role, then the procedure registers all the GeoRaster columns defined in all the schemas in the database. Otherwise, it only registers the GeoRaster columns defined in the current schema.

#### Examples

The following example creates DML triggers for all GeoRaster columns defined in the current schema.

    EXECUTE sdo_geor_admin.registerGeoRasterColumns;

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.16 SDO_GEOR_ADMIN.registerGeoRasterObjects

#### Format

    SDO_GEOR_ADMIN.registerGeoRasterObjects;

#### Description

Registers all GeoRaster objects defined in the current schema or in all the schemas in the database.

#### Parameters

None.

#### Usage Notes

If you execute this procedure as a user with DBA role, then the procedure registers all the GeoRaster objects defined in all the schemas in the database. Otherwise, it only registers the GeoRaster objects defined in the current schema.

#### Examples

The following example registers all GeoRaster objects defined in the current schema.

    EXECUTE sdo_geor_admin.registerGeoRasterObjects;

**Parent topic:** SDO_GEOR_ADMIN Package Reference

### 8.17 SDO_GEOR_ADMIN.upgradeGeoRaster

#### Format

    SDO_GEOR_ADMIN.upgradeGeoRaster() RETURN SDO_STRING2_ARRAY;

#### Description

Checks the GeoRaster system data entries and GeoRaster data for the current schema or for all the schemas in the database, and performs any corrective action as appropriate.

#### Parameters

None.

#### Usage Notes

This function performs the same checks as the SDO_GEOR_ADMIN.isUpgradeNeeded function, and it takes the corrective action that is appropriate (if any) for the following errors:

- System data entry error, the RDT name is not unique.

- System data entry error, the RDT/RID pair is not unique.

- System data entry error, the GeoRaster table does not exist.

- System data entry error, the GeoRaster column does not exist.

- System data entry error, the GeoRaster object does not exist.

- The GeoRaster object is non-empty or nonblank, but the RDT does not exist.

- Duplicate GeoRaster objects exist (that is, one or more non-unique combinations of RDT and raster ID).

- There is a non-registered pair of (GeoRaster column, GeoRaster object).

If you execute this procedure as a user with DBA role, then the procedure performs checking and correction in all the schemas in the database. Otherwise, it only performs checking and correction in the current schema.

#### Examples

The following example checks the GeoRaster system data entries and GeoRaster data for the current schema, and performs any corrective action as appropriate.

    DECLARE
      ret SDO_STRING2_ARRAY;
    BEGIN
      ret:=sdo_geor_admin.upgradeGeoraster;
      for i in 1..ret.count loop
        dbms_output.put_line(ret(i));
      end loop;
    END;
    /

**Parent topic:** SDO_GEOR_ADMIN Package Reference
