## 23 SDO_CSW Package (Catalog Services for the Web)

The MDSYS.SDO_CSW package contains subprograms for various processing operations related to support for Catalog Services for the Web (CSW).

To use the subprograms in this chapter, you must understand the conceptual and usage information about Catalog Services for the Web in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_CSW.CREATE_SPATIAL_IDX
- SDO_CSW.CREATE_XQFT_IDX
- SDO_CSW.INITIALIZE_CSW
- SDO_CSW.SYNC_INDEX

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 23.1 SDO_CSW.CREATE_SPATIAL_IDX

#### Format

    SDO_CSW.CREATE_SPATIAL_IDX(
        owner          IN VARCHAR2,
        csw_table_name IN VARCHAR2,
        srid           IN NUMBER);

#### Description

Creates a spatial index on the CSW table, if no spatial index already exists.

#### Parameters

owner
Name of the CSW schema for the table and spatial index.

csw_table_name
Name of the table that holds the CSW catalog data.

srid
The coordinate system (or SRID: spatial reference system) associated with the CSW catalog data. It should be the SRID in the geometry column of the CSW table. Example: `4326` (EPSG SRID value equivalent to Oracle SRID 8307).

You can specify a 2D or 3D SRID value, but the geometry column of the CSW table must have the appropriate number of dimensions for the specified SRID.

#### Usage Notes

If a spatial index already exists on `csw_table_name`, this procedure does nothing. If the spatial index already exists but needs to be re-created for CSW, you must drop the index, then create the index using this procedure. The USER_SDO_GEOM_METADATA view will be populated with the CSW table information.

This procedure uses the SDO_GEOMETRY objects from the XMLType column of the CSW table. These geometries are transformed into the coordinate reference system represented by the SRID parameter.

The created spatial index will have a name in the form csw_table_name`_IDX`.

For information about support for Catalog Services for the Web, see [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example creates a spatial index on the SCOTT.MY_CSW_CATALOG TABLE table, and it associates SRID 4326 with the spatial data.

    DECLARE
    BEGIN
      sdo_csw.create_spatial_idx('SCOTT', 'MY_CSW_CATALOG_TABLE', 4326);
    END;
    /

**Parent topic:** SDO_CSW Package (Catalog Services for the Web)

### 23.2 SDO_CSW.CREATE_XQFT_IDX

#### Format

    SDO_CSW.CREATE_XQFT_IDX(
        owner          IN VARCHAR2,
        csw_table_name IN VARCHAR2;

#### Description

Creates an XQFT (XML Search-XPath Query Full Text) index on the CSW table, if no such index already exists.

#### Parameters

owner
Name of the database schema for the CSW table and index.

csw_table_name
Name of the table that holds the CSW catalog data.

#### Usage Notes

If an XQFT index already exists on `csw_table_name` , and if you only need to update the index by synchronizing it with the current CSW data, you should instead use the SDO_CSW.SYNC_INDEX procedure, because that procedure takes less time to execute than SDO_CSW.CREATE_XQFT_IDX.

If an XQFT index already exists on `csw_table_name`, this procedure drops the existing one and re-creates the XQFT index. It also internally calls the CTX_DDL.DROP_PREFERENCE and CTX_DDL.DROP_SECTION_GROUP procedures.

This procedure internally calls the CTX_DDL.CREATE_PEREFERENCE procedure to create a BASIC_LEXER lexer named CSWLEX.

The created index will have a name in the form csw_table_name`_XQFT_IDX`.

For information about support for Catalog Services for the Web, see [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example creates an XQFT index on the SCOTT.MY_CSW_CATALOG_TABLE table.

    DECLARE
    BEGIN
      sdo_csw.create_xqft_idx('SCOTT', 'MY_CSW_CATALOG_TABLE');
    END;
    /

**Parent topic:** SDO_CSW Package (Catalog Services for the Web)

### 23.3 SDO_CSW.INITIALIZE_CSW

#### Format

    SDO_CSW.INITIALIZE_CSW(
        owner          IN VARCHAR2,
        csw_version    IN VARCHAR2,
        csw_xsd_id     IN NUMBER,
        csw_table_name IN VARCHAR2,
        srid           IN NUMBER,
        generate_index IN NUMBER);

#### Description

Initializes the Oracle Spatial and Graph Catalog Services for the Web (CSW) version 2.0.2 service database instance. This makes the schema of the current user the CSW schema, creates the CSW catalog table if it does not already exist, and prepares the indexes, as explained in the Usage Notes.

#### Parameters

owner
Name of the database schema to own the created table and indexes.

csw_version
CSW version number. Example: `2.0.2`.

csw_xsd_id
ID of the XSD in the MDSYS.SDO_XSD_TABLE table. Possible values: `1` for DCMI, `2` for ISO 19139.

csw_table_name
Name of the table to hold the CSW catalog data.

srid
The coordinate system (or SRID: spatial reference system) associated with the CSW data. It should be the SRID in the geometry column of the CSW table. Example: `4326` (EPSG SRID value equivalent to Oracle SRID 8307).

You can specify a 2D or 3D SRID value, but the geometry column of the CSW table must have the appropriate number of dimensions for the specified SRID.

generate_index
Determines whether to build indexes on the data in the `csw_table_name` table. `0` (zero) does not create any indexes on the table; `1` (or any positive nonzero value) builds all appropriate indexes on the table.

#### Usage Notes

This procedure lets you create the user table, specify an SRID value for the data, and control whether indexes are built on that table. It also populates the CSW metadata in the USER_CSW_SERVICE_INFO view to register the schema as the CSW schema. If `owner.csw_table_name` does not already exist, this procedure creates that table with the following columns:

    (Metadata_Id          VARCHAR(4000) PRIMARY KEY,
     Record_Instance_Xml  XMLType,
     Record_Geometry      SDO_GEOMETRY,
     XMLTYPE COLUMN       Record_Instance_Xml STORE AS BINARY XML)

If the CSW catalog table (and any indexes) already exist, then this procedure can also be used just to register the CSW catalog table by setting SRID parameter to NULL and GENERATE_INDEX parameter to 0. It then only populates the CSW metadata in the USER_CSW_SERVICE_INFO view to register the schema as the CSW schema.

For information about support for Catalog Services for the Web, see [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example uses the first format of the procedure. It makes SCOTT the CSW schema, associates SRID 4326 with the spatial data, and builds indexes on the data in the MY_CSW_CATALOG_TABLE table.

    DECLARE
    BEGIN
    sdo_csw.initialize_csw(
            'SCOTT',
            '2.0.2', -- must be 2.0.2
            1, -- for DCMI
            'MY_CSW_CATALOG_TABLE',
            4326,
            1
        );
    END;
    /

**Parent topic:** SDO_CSW Package (Catalog Services for the Web)

### 23.4 SDO_CSW.SYNC_INDEX

#### Format

    SDO_CSW.SYNC_INDEX(
        owner          IN VARCHAR2,
        csw_table_name IN VARCHAR2;

#### Description

Updates the XQFT (XML Search-XPath Query Full Text) index on the CSW user data table, by synchronizing the index with the data in the table.

#### Parameters

owner
Name of the database schema for the table and index.

csw_table_name
Name of the table that holds the CSW catalog data.

#### Usage Notes

This procedure should be run when there have been significant insert, update, or delete operations on the CSW user data table, because the existing XQFT nidex iautomaticallyically updated.

This procedure updates the index whose name is in the form csw_table_name`_XQFT_IDX`.

#### Examples

The following example updates the XQFT index on the MDMETT.CSW_TABLE table.

    DECLARE
    BEGIN
      sdo_csw.sync_index('MDMETT', 'CSW_TABLE');
    END;
    /

**Parent topic:** SDO_CSW Package (Catalog Services for the Web)
