## 36  SDO_WCS Package (Web Coverage Service)

The MDSYS.SDO_WCS package contains subprograms associated with Oracle Spatial and Graph support for Web Coverage Service (WCS).

It assumes that you are familiar with the concepts and techniques described in [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

- SDO_WCS.CreateTempTable
- SDO_WCS.DropTempTable
- SDO_WCS.GrantPrivilegesToWCS
- SDO_WCS.Init
- SDO_WCS.PublishCoverage
- SDO_WCS.RevokePrivilegesFromWCS
- SDO_WCS.UnpublishCoverage
- SDO_WCS.ValidateCoverages

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 36.1 SDO_WCS.CreateTempTable

#### Format

    SDO_WCS.CreateTempTable(
         schema_name      IN VARCHAR2 DEFAULT USER,
         tablespace_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Creates temporary tables necessary during GetCoverage processing when reprojection or transformation is involved.

#### Parameters

schema_name
Name of the schema in which temporary tables will be created. If not specified, the tables are created in invoking user’s schema.

tablespace_name
Name of the tablespace for temporary tables. If not specified, the user's default tablespace is used.

#### Usage Notes

Each temporary GeoRaster object is stored in the same schema as the original GeoRaster object. When a [GetCoverage Operation (WCS)](web-coverage-service-wcs-support.md) response has been sent to the client, any temporary GeoRaster created during processing of a request is deleted.

This procedure must be invoked for all schemas whose GeoRaster objects will be published as coverages.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example creates WCS temporary tables in the invoker's schema.

    CALL SDO_WCS.createTempTable();

The following example creates WCS temporary tables in the SCOTT schema. The invoking user must have privileges to create tables in the SCOTT schema.

    CALL SDO_WCS.createTempTable(‘SCOTT’);

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.2 SDO_WCS.DropTempTable

#### Format

    SDO_WCS.DropTempTable(
         schema_name   IN VARCHAR2 DEFAULT USER);

#### Description

Drops WCS temporary tables from a schema. (WCS Temporary tables are necessary for WCS GeoCoverage processing.)

#### Parameters

schema_name
Name of the database schema containing WCS temporary tables to be dropped. If not specified, the invoker's schema is used.

#### Usage Notes

If `schema_name` is not the invoking user, the invoking user must have privileges to drop tables from that schema.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example drop WCS temporary tables from the invoker's schema.

    BEGIN
    SDO_WCS.DropTempTable();
    END;

The following example drops WCS temporary tables from the SCOTT schema. The invoking user must have privileges to drop tables in the SCOTT schema.

    BEGIN
    SDO_WCS.DropTempTable(‘SCOTT’);
    END;

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.3 SDO_WCS.GrantPrivilegesToWCS

#### Format

    SDO_WCS.GrantPrivilegesToWCS(
         table_name  IN VARCHAR2,
         wcs_schema  IN VARCHAR2,
       updateable  IN VARCHAR2 DEFAULT 'FALSE');

#### Description

Grants select and update privileges on all GeoRaster objects and the raster data tables of the GeoRaster table to the WCS schema when the WCS schema is different from the user schema (that is, the schema with GeoRaster objects).

#### Parameters

table_name
Name of the table that contains GeoRaster objects that will be published as coverages.

wcs_schema
Name of the schema to be used as the WCS schema.

updateable
The string `TRUE` or `FALSE` (default) indicating if update privilege is to be granted.

#### Usage Notes

If the user schema (schema with GeoRaster objects published as coverages) and the WCS schema are the same, do not use this procedure.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example grant read privileges on all GeoRaster objects and the raster data tables of a table named GEORASTER_TABLE in the current schema to a WCS schema named WCS_1.

    BEGIN
      SDO_WCS.grantPrivilegesToWCS(‘GEORASTER_TABLE’,’WCS_1’);
    END;
    /

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.4 SDO_WCS.Init

#### Format

    SDO_WCS.Init();

#### Description

Creates metadata tables and sequences to store references to GeoRaster objects published as WCS coverages. The calling schema becomes a WCS schema, and is configured in the Java EE container where the Spatial Web Services web application is deployed.

#### Parameters

(None.)

#### Usage Notes

This procedure must be called once before publishing any coverages and before configuring a WCS data source in WebLogic Server.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example creates the necessary WCS metadata tables. It then publishes coverages on GeoRaster objects in the GEORASTER_TABLE.RASTER column in the SCOTT schema.

    BEGIN
      SDO_WCS.Init();
      SDO_WCS.PublishCoverage(‘SCOTT’,’GEORASTER_TABLE’,’RASTER’);
    END;
    /

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.5 SDO_WCS.PublishCoverage

#### Format

    SDO_WCS.PublishCoverage(
         georaster   IN SDO_GEORASTER,
         updateable  IN VARCHAR2 DEFAULT 'FALSE');

or

    SDO_WCS.PublishCoverage(
         user_name   IN VARCHAR2,
       table_name  IN VARCHAR2,
         column_name IN VARCHAR2,
         updateable  IN VARCHAR2 DEFAULT 'FALSE');

#### Description

Publishes GeoRaster objects as WCS coverages.

#### Parameters

georaster
A GeoRaster object to be published as a WCS coverage.

user_name
Name of the user (schema) that owns the table with GeoRaster columns.

table_name
Name of the GeoRaster table whose GeoRaster objects are to be published.

column_name
Name of the GeoRaster column in `table_name`.

updateable
Contains the string `TRUE` if the published coverages are to be editable through a transaction request; contains the string `FALSE` (default) if the published coverages are not to be editable through a transaction request.

#### Usage Notes

A unique coverage Id is assigned to each GeoRaster published. The [GetCapabilities Operation (WCS)](web-coverage-service-wcs-support.md) response will show the newly generated coverage ID. A GeoRaster object can only be published once.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example publishes a specific GeoRaster object (`where ID=1`) from a table named GEORASTER_TABLE in the SCOTT schema as a coverage.

    DECLARE
      gr1   SDO_GEORASTER;
    BEGIN
      SELECT raster INTO gr1 FROM SCOTT.GEORASTER_TABLE where ID=1;
      SDO_WCS.PublishCoverage(gr1);
    END;
    /

The following example publishes all GeoRaster objects in the RASTER column of the IMAGE table in the SCOTT schema.

    CALL SDO_WCS.publishCoverage('SCOTT','IMAGE','RASTER');

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.6 SDO_WCS.RevokePrivilegesFromWCS

#### Format

    SDO_WCS.RevokePrivilegesFromWCS(
         table_name  IN VARCHAR2,
         wcs_schema  IN VARCHAR2);

#### Description

Revokes select and update privileges on the specified table in the invoking user’s schema from the specified wcs_schema user.

#### Parameters

table_name
The name of a GeoRaster table that previously was granted privileges using SDO_WCS.GrantPrivilegesToWCS procedure.

wcs_schema
Name of the WCS schema from which to revoke the privileges. Must not be the same as the user schema containing the GeoRaster objects.

#### Usage Notes

Do not use this procedure when the WCS schema is the same as the schema for the GeoRaster objects.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example revokes read and update privileges on GEORASTER_TABLE and all raster data tables associated with it from the WCS schema named WCS_1.

    BEGIN
      SDO_WCS.RevokePrivilegesFromWCS('GEORASTER_TABLE','WCS_1'’);
    END;
    /

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.7 SDO_WCS.UnpublishCoverage

#### Format

    SDO_WCS.UnpublishCoverage(
         coverage_id  IN VARCHAR2);

#### Description

Unpublishes a coverage.

#### Parameters

coverage_id
A string specifying a coverage ID from the list of coverages of a GetCapabilities response.

#### Usage Notes

A [GetCapabilities Operation (WCS)](web-coverage-service-wcs-support.md) response contains the list of all coverage ID from the given WCS server instance. After this procedure runs, the specified coverage ID will not appear in a GetCapabilities response.

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example unpublishes the coverage with coverage Id C0001.

    DECLARE
    BEGIN
      SDO_WCS.UnpublishCoverage(‘C0001’);
    END;
    /

**Parent topic:** SDO_WCS Package (Web Coverage Service)

### 36.8 SDO_WCS.ValidateCoverages

#### Format

    SDO_WCS.ValidateCoverages(
         ) RETURN MDSYS.SDO_WCS_INVALID_COVERAGE;

#### Description

Validates GeoRaster objects in the WCS metadata tables and returns the coverage IDs of all invalid WCS metadata entries.

#### Parameters

(None.)

#### Usage Notes

This procedure must be invoked by a WCS user.

When GeoRaster objects are deleted, references to them might remain in WCS metadata tables. Such references are invalid metadata entries.

This function returns an MDSYS.SDO_WCS_INVALID_COVERAGE object, which is defined as: `TABLE OF VARCHAR2(4000)`

Each element of the returned object is a coverage Id from the WCS metadata tables in which the corresponding GeoRaster object was not found. Invalid metadata entries are not handled by the [DescribeCoverage Operation (WCS)](web-coverage-service-wcs-support.md) and [GetCoverage Operation (WCS)](web-coverage-service-wcs-support.md).

For information about support for WCS, see [Web Coverage Service (WCS) Support](web-coverage-service-wcs-support.md).

#### Examples

The following example iterates over all invalid coverage IDs and unpublishes them, leaving only valid coverages in the WCS metadata.

    DECLARE
    BEGIN
       FOR i IN (select * from table(SDO_WCS.ValidateCoverages()))
       LOOP
          SDO_WCS.UnpublishCoverage(i.column_value);
       END LOOP;
    END;
    /

**Parent topic:** SDO_WCS Package (Web Coverage Service)
