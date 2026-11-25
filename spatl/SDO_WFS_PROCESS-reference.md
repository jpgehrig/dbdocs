## 38  SDO_WFS_PROCESS Package (WFS Processing)

The MDSYS.SDO_WFS_PROCESS package contains subprograms for various processing operations related to support for Web Feature Services.

To use the subprograms in this chapter, you must understand the conceptual and usage information about Web Feature Services in [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_WFS_PROCESS.DropFeatureType
- SDO_WFS_PROCESS.DropFeatureTypes
- SDO_WFS_PROCESS.GenCollectionProcs
- SDO_WFS_PROCESS.GetFeatureTypeId
- SDO_WFS_PROCESS.GrantFeatureTypeToUser
- SDO_WFS_PROCESS.GrantMDAccessToUser
- SDO_WFS_PROCESS.InsertCapabilitiesInfo
- SDO_WFS_PROCESS.InsertFtDataUpdated
- SDO_WFS_PROCESS.InsertFtMDUpdated
- SDO_WFS_PROCESS.PopulateFeatureTypeXMLInfo
- SDO_WFS_PROCESS.PublishFeatureType
- SDO_WFS_PROCESS.Publish_FeatureTypes_In_Schema
- SDO_WFS_PROCESS.RegisterMTableView
- SDO_WFS_PROCESS.RevokeFeatureTypeFromUser
- SDO_WFS_PROCESS.RevokeMDAccessFromUser
- SDO_WFS_PROCESS.UnRegisterMTableView

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 38.1 SDO_WFS_PROCESS.DropFeatureType

#### Format

    SDO_WFS_PROCESS.DropFeatureType(
         ftnsUrl IN VARCHAR2,
         ftName  IN VARCHAR2);

#### Description

Deletes a specified feature type.

#### Parameters

ftnsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

#### Usage Notes

If you want to drop a feature type whose content comes from a multitable view, you must call the SDO_WFS_PROCESS.UnRegisterMTableView procedure before you call the SDO_WFS_PROCESS.DropFeatureType procedure.

If you want to drop all feature types in the namespace, you can use the SDO_WFS_PROCESS.DropFeatureTypes procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example deletes the feature type named `COLA` in a specified namespace.

    BEGIN
        SDO_WFS_PROCESS.dropFeatureType('http://www.example.com/myns','COLA');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.2 SDO_WFS_PROCESS.DropFeatureTypes

#### Format

    SDO_WFS_PROCESS.DropFeatureTypes(
         ftnsUrl  IN VARCHAR2);

#### Description

Deletes all feature types in a specified namespace.

#### Parameters

ftnsUrl
Uniform resource locator (URL) of the namespace.

#### Usage Notes

To drop a single feature type in a namespace, use the SDO_WFS_PROCESS.DropFeatureType procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example deletes all feature types in a specified namespace.

    BEGIN
        SDO_WFS_PROCESS.dropFeatureTypes('http://www.example.com/myns');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.3 SDO_WFS_PROCESS.GenCollectionProcs

#### Format

    SDO_WFS_PROCESS.GenCollectionProcs();

#### Description

Generates helper procedures for relational feature types that have collection-based columns (for example, VARRAYs or nested tables).

#### Parameters

None.

#### Usage Notes

Use this procedure if any feature tables have features that are defined in collection-based columns (for example, VARRAYs or nested tables).

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example generates helper procedures for relational feature types that have collection-based columns.

    BEGIN
      SDO_WFS_PROCESS.GenCollectionProcs;
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.4 SDO_WFS_PROCESS.GetFeatureTypeId

#### Format

    SDO_WFS_PROCESS.GetFeatureTypeId(
         ftnsUrl IN VARCHAR2,
         ftName  IN VARCHAR2) RETURN NUMBER;

#### Description

Gets the feature type ID of a specified feature type.

#### Parameters

ftnsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

#### Usage Notes

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example gets the feature type ID of a feature type named `COLA`.

    DECLARE
      ftid number;
    BEGIN
      ftId := SDO_WFS_PROCESS.GetFeatureTypeId('http://www.example.com/myns','COLA');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.5 SDO_WFS_PROCESS.GrantFeatureTypeToUser

#### Format

    SDO_WFS_PROCESS.GrantFeatureTypeToUser(
         ftnsUrl  IN VARCHAR2,
         ftName   IN VARCHAR2,
         userName IN VARCHAR2);

#### Description

Grants access to a feature type to a database user.

#### Parameters

ftnsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

userName
Name of the database user.

#### Usage Notes

To revoke access to a feature type from a database user, use the SDO_WFS_PROCESS.RevokeFeatureTypeFromUser procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example grants access to the `COLA` feature type to user `SMITH`.

    BEGIN
      SDO_WFS_PROCESS.GrantFeatureTypeToUser('http://www.example.com/myns','COLA',
        'SMITH');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.6 SDO_WFS_PROCESS.GrantMDAccessToUser

#### Format

    SDO_WFS_PROCESS.GrantMDAccessToUser(
         userName  IN VARCHAR2);

#### Description

Grants access to Web Feature Service metadata tables to a database user.

#### Parameters

userName
Name of the database user.

#### Usage Notes

To call this procedure, you should be connected to the database as a user with the DBA role.

To revoke access to Web Feature Service metadata tables from a database user, use the SDO_WFS_PROCESS.RevokeMDAccessFromUser procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example grants access to Web Feature Service metadata tables to the database user named `WFS_REL_USER`.

    BEGIN
      SDO_WFS_PROCESS.GrantMDAccessToUser('WFS_REL_USER');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.7 SDO_WFS_PROCESS.InsertCapabilitiesInfo

#### Format

    SDO_WFS_PROCESS.InsertCapabilitiesInfo(
         capabilitiesInfo IN XMLTYPE);

#### Description

Inserts the capabilities template information.

#### Parameters

capabilitiesInfo
XML document for the capabilities template, which is used at runtime to generate capabilities documents.

#### Usage Notes

At runtime, the capabilities document is dynamically generated by binding feature type information from the WFS metadata with the capabilities template. For information about capabilities documents, see [Capabilities Documents](web-feature-service-wfs-concepts.md).

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example inserts the capabilities template information.

    BEGIN
      SDO_WFS_PROCESS.insertCapabilitiesInfo(
        xmltype(bfilename('WFSUSERDIR', 'capabilitiesTemplate.xml'),
           nls_charset_id('AL32UTF8')));
    END
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.8 SDO_WFS_PROCESS.InsertFtDataUpdated

#### Format

    SDO_WFS_PROCESS.InsertFtDataUpdated(
         ns             IN VARCHAR2,
         name           IN VARCHAR2,
         updatedRowList IN ROWPOINTERLIST,
         updateTs       IN TIMESTAMP);

#### Description

Inserts a notification that the data for one or more feature instances was updated in the database.

#### Parameters

ns
Namespace of the feature type.

name
Name of the feature type.

updatedRowList
Rowids of feature instances that have been updated.

updateTS
Date and time when the data was updated.

#### Usage Notes

This procedure is used for WFS cache data synchronization.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example inserts a notification that the data for the feature instances associated with specific rowids in the COLA_MARKETS_CS table was updated in the database.

    . . .
    begin
    updatedRowIdList:= . . . -- list of rowIds of the
    --          WFS_REL_USER.COLA_MARKETS_CS table
    --          that have been updated.
    . . .
    SDO_WFS_PROCESS.InsertFtDataUpdated(
        'http://www.example.com/myns','COLA', updatedRowIdList, sysdate);
    . . .
    end;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.9 SDO_WFS_PROCESS.InsertFtMDUpdated

#### Format

    SDO_WFS_PROCESS.InsertFtMDUpdated(
         ns       IN VARCHAR2,
         name     IN VARCHAR2,
         updateTs IN TIMESTAMP);

#### Description

Inserts a notification that the metadata for a feature type was updated in the database.

#### Parameters

ns
Namespace of the feature type.

name
Name of the feature type.

updateTS
Date and time when the metadata was updated.

#### Usage Notes

This procedure is used for WFS cache metadata synchronization.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example inserts a notification that the metadata for the `COLA` feature type was updated in the database.

    begin
    SDO_WFS_PROCESS.InsertFtMDUpdated(
        'http://www.example.com/myns','COLA', sysdate);
    end;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.10 SDO_WFS_PROCESS.PopulateFeatureTypeXMLInfo

#### Format

    SDO_WFS_PROCESS.PopulateFeatureTypeXMLInfo(
         xmlColTypeXsd IN XMLTYPE,
         fTypeId       IN NUMBER,
         columnName    IN VARCHAR2,
         objPathInfo   IN MDSYS.STRINGLIST);

#### Description

Populates metadata for a relational feature type that has an XMLType column.

#### Parameters

xmlColTypeXsd
Schema definition of the relational feature type that has an XMLType column.

fTypeId
ID of the relational feature type that has an XMLType column.

columnName
Name of the XMLType column in the feature table

objPathInfo
Path information. `The MDSYS.STRINGLIST type is defined as VARRAY(1000000) OF VARCHAR2(4000)`.

#### Usage Notes

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example populates the metadata for the relational feature type described by the XML schema definition in `ROADS.xsd` and stored in an XMLType column named DATACOL

    BEGIN
      SDO_WFS_PROCESS.populateFeatureTypeXMLInfo(
        xmltype(bfilename('WFSUSERDIR', 'ROADS.xsd'), nls_charset_id('AL32UTF8')),
        1,
        'DATACOL',
        mdsys.StringList('METADATA'));
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.11 SDO_WFS_PROCESS.PublishFeatureType

#### Format

    SDO_WFS_PROCESS.PublishFeatureType(
         dataSrc           IN VARCHAR2,
         ftNsUrl           IN VARCHAR2,
         ftName            IN VARCHAR2,
         ftNsAlias         IN VARCHAR2,
         featureDesc       IN XMLTYPE,
         schemaLocation    IN VARCHAR2,
         pkeyCol           IN VARCHAR2,
         columnInfo        IN MDSYS.STRINGLIST,
         pSpatialCol       IN VARCHAR2,
         featureMemberNs   IN VARCHAR2,
         featureMemberName IN VARCHAR2,
         srsNs             IN VARCHAR2,
         srsNsAlias        IN VARCHAR2,
         mandatoryColumnInfo IN MDSYS.STRINGLIST);

or

    SDO_WFS_PROCESS.PublishFeatureType(
         dataSrc             IN VARCHAR2,
         ftNsUrl             IN VARCHAR2,
         ftName              IN VARCHAR2,
         ftNsAlias           IN VARCHAR2,
         featureDesc         IN XMLTYPE,
         schemaLocation      IN VARCHAR2,
         pkeyCol             IN VARCHAR2,
         columnInfo          IN MDSYS.STRINGLIST,
         pSpatialCol         IN VARCHAR2,
         featureMemberNs     IN VARCHAR2,
         featureMemberName   IN VARCHAR2,
         srsNs               IN VARCHAR2,
         srsNsAlias          IN VARCHAR2,
         viewTableName       IN VARCHAR2,
         viewTablepkeyCol    IN VARCHAR2,
         mandatoryColumnInfo IN MDSYS.STRINGLIST);

or

    SDO_WFS_PROCESS.PublishFeatureType(
         dataSrc               IN VARCHAR2,
         ftNsUrl               IN VARCHAR2,
         ftName                IN VARCHAR2,
         ftNsAlias             IN VARCHAR2,
         featureDesc           IN XMLTYPE,
         schemaLocation        IN VARCHAR2,
         pkeyCol               IN VARCHAR2,
         columnInfo            IN MDSYS.STRINGLIST,
         pSpatialCol           IN VARCHAR2,
         featureMemberNs       IN VARCHAR2,
         featureMemberName     IN VARCHAR2,
         srsNs                 IN VARCHAR2,
         srsNsAlias            IN VARCHAR2,
         featureCollectionNs   IN VARCHAR2,
         featureCollectionName IN VARCHAR2,
         isGML3                IN VARCHAR2,
         formattedKeyCols      IN MDSYS.STRINGLIST,
         viewTableName         IN VARCHAR2,
         viewTablepkeyCol      IN VARCHAR2,
         viewTableFmtKeyCols   IN VARCHAR2,
         mandatoryColumnInfo   IN MDSYS.STRINGLIST);

#### Description

Publishes a feature type; that is, registers metadata related to the feature type.

#### Parameters

dataSrc
Name of the feature table or view containing the spatial features. It must be in the format schema-name.table-name or schema-name.view-name; that is, the name of the database user that owns the table must be included.

ftNsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

ftNsAlias
Alias of the namespace for the feature type.

featureDesc
Feature type description to be reported in the capabilities document, as a document of type XMLTYPE.

schemaLocation
String to be used to populate the `xsi:schemaLocation` attribute in the feature type XSD. If this parameter is null, a string is automatically generated.

pkeyCol
Primary key column in the feature table or view identified in `dataSrc`. If a feature type table or view has a multicolumn primary key, use a semicolon to separate the columns in the primary key. For example: `'COL1;COL2'`

columnInfo
Type string associated with each spatial column (SDO_GEOMETRY type) in the feature table identified in `dataSrc`., as an object of type MDSYS.STRINGLIST (for example, for WFS 1.1.n, `MDSYS.STRINGLIST('PolygonPropertyType', 'PointPropertyType')`.

See the Usage Notes for information about any spatial columns specified in the `columnInfo` parameter.

pSpatialCol
Spatial column of type SDO_GEOMETRY in the feature table.

featureMemberNs
Namespace of the feature member element that will contain feature instances in a feature collection. If this parameter is null, the default is: `http://www.opengis.net/gml`

featureMemberName
Name of the feature member element that will contain feature instances in a feature collection. If this parameter is null, the default is `featureMember`.

srsNs
User-defined namespace of the spatial reference system (coordinate system) associated with the spatial data for the feature type. This namespace (if specified) is also used to generate the `srsName` attribute in the `<boundedBy>` element of the FeatureCollection result generated for the GetFeature request.

srsNsAlias
Namespace alias of the namespace of the spatial reference system (coordinate system) associated with the spatial data for the feature type.

featureCollectionNs
Namespace of the WFS feature collection within which this feature type instances can occur.

featureCollectionName
Name of the WFS feature collection within which this feature type instances can occur.

isGML3
A string value: `Y` means that the geometries inside instances of this feature type are GML3.1.1 compliant; `N` means that the geometries inside instances of this feature type are GML 2.1.2 compliant.

formattedKeyCols
String formatted representation of the content of the primary key column or (for a multicolumn primary key) columns. For example, if ROAD_ID is the primary key column of type NUMBER, specify `MDSYS.STRINGLIST('to_char(ROAD_ID)')`. To specify multiple strings in the MDSYS.STRINGLIST type constructor, separate each with a comma. The list of string formatted primary key columns should be specified in the same order as the primary key columns specified in the `pkeyCol` parameter.

viewTableName
Name of the underlying table if the feature type will by defined on a view based on a single underlying table. The published feature type will be based on the view, specified in the `dataSrc` parameter (user-name.view-name). Do not enter a value for the `viewTableName` parameter if the feature type is based on a table or on a multitable view.

viewTablepkeyCol
Primary key column of the table specified in the `viewTableName` parameter, if the feature type will by defined on a view based on a single underlying table.

viewTableFmtKeyCols
If the feature type is based on a view defined on a single table, and if the view has one or more formatted primary key columns, this parameter represents a list of string formatted primary key columns in the underlying table that correspond to the string formatted primary key columns in the view (specified by `formattedkeyCols` parameter). For example, if ROAD_ID is the primary key column of type NUMBER, specify `MDSYS.STRINGLIST('to_char(ROAD_ID)')`. To specify multiple strings in the MDSYS.STRINGLIST type constructor, separate each with a comma.

If feature type is not based on a single table view, or if the feature type is based on a single table view but the feature type does not have formatted primary key columns, this parameter should be null.

mandatoryColumnInfo
List of columns that must be returned in the GetFeature request, irrespective of the columns requested. (The requested columns will be returned in all cases.) If this parameter is omitted, all columns are mandatory (that is, all columns will be returned). However, if this parameter is specified as NULL, no columns are mandatory (that is, only the requested columns will be returned). To specify column names, use the MDSYS.STRINGLIST type constructor as in the following example: `MDSYS.STRINGLIST('COL1', 'COL2', 'COL5')`

#### Usage Notes

In the `columnInfo` parameter, each column of type SDO_GEOMETRY in the feature type instances table must have the correct associated string value specified in the `columnInfo` parameter, with the string values in the same order as the order of the spatial columns in the table definition.

For WFS 1.0.n, for example, if the single SDO_GEOMETRY column named SHAPE in the feature type instances table contains polygon geometries, the `columnInfo` value must be `SHAPE_GEOMETRYTYPE>PolygonMemberType`. Table 38-1 lists the geometry types and their required associated `columnInfo` parameter values for WFS version 1.0.n. (Replace \<column-name\> with the name of the column.)

Table 38-1 Geometry Types and columnInfo Parameter Values (WFS 1.0.n)

| Geometry Type                | columnInfo Parameter Value                            |
|:-----------------------------|:------------------------------------------------------|
| Polygon or Surface           | \<column-name\>\_GEOMETRYTYPE\>PolygonMemberType      |
| Multipolygon or Multisurface | \<column-name\>\_GEOMETRYTYPE\>MultiPolygonMemberType |
| Point                        | \<column-name\>\_GEOMETRYTYPE\>PointMemberType        |
| Multipoint                   | \<column-name\>\_GEOMETRYTYPE\>MultiPointMemberType   |
| Line or Curve                | \<column-name\>\_GEOMETRYTYPE\>CurveMemberType        |
| Multiline or multicurve      | \<column-name\>\_GEOMETRYTYPE\>MultiCurveMemberType   |
| Solid                        | \<column-name\>\_GEOMETRYTYPE\>SolidMemberType        |
| Multisolid                   | \<column-name\>\_GEOMETRYTYPE\>MultiSolidMemberType   |
| Collection                   | \<column-name\>\_GEOMETRYTYPE\>GeometryMemberType     |

For WFS 1.1.n, for example, if the single SDO_GEOMETRY column in the feature type instances table contains polygon geometries, the `columnInfo` value must be `PolygonPropertyType`. Table 38-2 lists the geometry types and their required associated `columnInfo` parameter values for WFS version 1.1.n.

Table 38-2 Geometry Types and columnInfo Parameter Values (WFS 1.1.n)

| Geometry Type                | columnInfo Parameter Value |
|:-----------------------------|:---------------------------|
| Polygon or Surface           | PolygonPropertyType        |
| Multipolygon or Multisurface | MultiPolygonPropertyType   |
| Point                        | PointPropertyType          |
| Multipoint                   | MultiPointPropertyType     |
| Line or Curve                | CurvePropertyType          |
| Multiline or multicurve      | MultiCurvePropertyType     |
| Solid                        | SolidPropertyType          |
| Multisolid                   | MultiSolidPropertyType     |
| Collection                   | GeometryPropertyType       |

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example registers metadata for a feature type named `COLA` with the polygon geometries stored in the column named `SHAPE`. (It assumes the use of WFS 1.1.n.)

    DECLARE
    columnInfo MDSYS.StringList := MDSYS.StringList('PolygonPropertyType');
    BEGIN
    SDO_WFS_PROCESS.publishFeatureType(
     'WFS_USER.COLA_MARKETS_VIEW',
     'http://www.example.com/myns',
     'COLA',
     'myns',
     xmltype(bfilename('WFSUSERDIR', 'featuredesct.xml'), nls_charset_id('AL32UTF8')),
     null, 'MKT_ID', columnInfo, 'SHAPE', null, null, null, null);
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.12 SDO_WFS_PROCESS.Publish_FeatureTypes_In_Schema

#### Format

    SDO_WFS_PROCESS.Publish_FeatureTypes_In_Schema(
         p_owner              IN VARCHAR2,
         p_namespace_url      IN VARCHAR2,
         p_namespace_alias    IN VARCHAR2,
         p_wls_postxml_url    IN VARCHAR2,
         p_tablename_pattern  IN VARCHAR2 DEFAULT NULL,
         p_wfs_version        IN VARCHAR2 DEFAULT NULL,
         p_write_xsd          IN VARCHAR2 DEFAULT NULL);

#### Description

Publishes the feature types in a schema; that is, registers metadata related to the feature types (using “camel case”).

#### Parameters

p_owner
Name of the database user that owns the table containing the spatial features (which can have spatial and non-spatial properties).

p_namespace_url
Uniform resource locator (URL) of the namespace for the feature type. (Corresponds to the `ftNsUrl` parameter of the SDO_WFS_PROCESS.PublishFeatureType procedure.)

p_namespace_alias
Alias of the namespace for the feature type. (Corresponds to the `ftNsAlias` parameter of the SDO_WFS_PROCESS.PublishFeatureType procedure)

p_wls_postxml_url
The HTTP URL in the format to execute POST XML requests to the WFS Server:

- `http://hostname:listening_port/SpatialWS-SpatialWS-context-root/SpatialWSXmlServlet` \[old notation\]

- `http://hostname:listening_port/oraclespatial/wfs` \[new notation\]

This URL is used for any cache reload for the WFS engine.

p_tablename_pattern
The table name pattern to identify tables that need to be newly published or republished if they are already published. The default it is "%", which means all feature types in the schema.

p_wfs_version
The WFS version needed for the POST XML request. The default value is 1.1.0, the latest WFS version supported for Release 12.2.

p_write_xsd
If `Y`, then an XSD file is written to WFSUSERDIR. The file naming convention matches owner_tablename_columnname.xsd.

#### Usage Notes

This procedure publishes all feature types in a schema with each feature type XSD derived from the corresponding `DescribeFeatureType` response without using the WFS administration console.

This procedure assumes that each feature type table has a single spatial column, even though WFS can handle multiple spatial columns.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example performs all metadata registry operations . It assumes the use of WFS 1.1.0 (the default).

    EXECUTE  SDO_WFS_PROCESS.publish_featureTypes_in_schema(
       p_owner=> 'WFS_REL_USER',
       p_namespace_url => 'http://cite.opengeospatial.org/gmlsf',
       p_namespace_alias=> 'sf',
       p_wls_postxml_url=> 'http://localhost:7003/oraclespatial/wfs');

The following example publishes the GEOD_STATES table in the STUDENT schema.

    EXECUTE sdo_wfs_process.publish_featureTypes_in_schema (
       'STUDENT',
       'http://www.myserver.com/student_data',
       'sdns',
       'http://localhost:7001/oraclespatial/wfs',
       p_tablename_pattern=>'GEOD_STATES');

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.13 SDO_WFS_PROCESS.RegisterMTableView

#### Format

    SDO_WFS_PROCESS.RegisterMTableView(
         ftNsUrl              IN VARCHAR2,
         ftName               IN VARCHAR2,
         viewTableList        IN MDSYS.STRINGLIST,
         viewTablePkeyColList IN MDSYS.STRINGLIST,
         tablePkeyColList     IN MDSYS.STRINGLIST);

or

    SDO_WFS_PROCESS.RegisterMTableView(
         ftNsUrl                   IN VARCHAR2,
         ftName                    IN VARCHAR2,
         viewTableList             IN MDSYS.STRINGLIST,
         viewTablePkeyColList      IN MDSYS.STRINGLIST,
         formattedViewTableColList IN MDSYS.STRINGLISTLIST,
         tablePkeyColList          IN MDSYS.STRINGLIST);

#### Description

Enables the publishing of content from a multitable view as a feature instance.

#### Parameters

ftNsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

viewTableList
List of tables in the view. To specify table names, use the MDSYS.STRINGLIST type constructor as in the following example: `MDSYS.STRINGLIST('MYUSER.ROADS', 'MYUSER.ROADS_DESC')`

viewTablePkeyColList
List of view columns that correspond to the primary key columns in the tables in the view, in the order that corresponds to the order of the tables in `viewTableList`. To specify column names, use the MDSYS.STRINGLIST type constructor as in the following example: `MDSYS.STRINGLIST('ROAD_ID', 'ROAD_ID')`, where both the ROADS and ROAD_DESC table have ROAD_ID as primary key.

If the view has columns that correspond to table columns in a multicolumn primary key, use a semicolon to separate the columns in the primary key. For example: `'COL1;COL2'`

formattedViewTableColList
A list of string formatted table primary key columns that correspond to the string formatted primary key columns in the view, in the order that corresponds to the order of the tables in `viewTableList`. To specify column names, use the MDSYS.STRINGLISTLIST type constructor as in the following example: `MDSYS.STRINGLISTLIST(MDSYS.STRINGLIST('to_char(ROAD_ID)'), MDSYS.STRINGLIST('to_char(ROAD_ID)'))`

The list of string formatted primary key columns for each table should be specified in the same order as the primary key columns for each table specified in `tablePkeyColList` parameter.

tablePkeyColList
List of the primary key columns in the tables, in the order that corresponds to the order of the tables in `viewTableList`. For each table the primary key columns should be specified in the order that correspond to the key columns in the view as specified in `viewTablePkeyColList` parameter. To specify column names, use the MDSYS.STRINGLIST type constructor as in the following example: `MDSYS.STRINGLIST('ROAD_ID', 'ROAD_ID')`

If a table has a multicolumn primary key, use a semicolon to separate the columns in the primary key. For example : `'COL1;COL2'`

#### Usage Notes

If you need to publish content from a multitable view as a feature instance, you must call this procedure after calling the SDO_WFS_PROCESS.PublishFeatureType procedure.

To disable the publishing of content from a multitable view as a feature instance, use the SDO_WFS_PROCESS.UnRegisterMTableView procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example creates two feature tables, creates a view based on these tables. publishes a feature type, and registers the multitable view to enable the publishing of content from the view.

    CREATE TABLE cola_markets_cs (
      mkt_id NUMBER PRIMARY KEY,
      name VARCHAR2(32),
      shape MDSYS.SDO_GEOMETRY);

    CREATE TABLE cola_markets_cs_details (
      mkt_id NUMBER PRIMARY KEY,
      description VARCHAR2(400));

    create view cola_markets_view as select t1.mkt_id, t1.name, t1.shape,
      t2.description from
      cola_markets_cs t1, cola_markets_cs_details t2
      where t1.mkt_id = t2.mkt_id;

    DECLARE
    cm MDSYS.StringList := MDSYS.StringList('PolygonMemberType');
    BEGIN
    SDO_WFS_PROCESS.publishFeatureType(
     'WFS_USER.COLA_MARKETS_VIEW',
     'http://www.example.com/myns',
     'COLA',
     'myns',
     xmltype(bfilename('WFSUSERDIR', 'featuredesct.xml'), nls_charset_id('AL32UTF8')),
     null, 'MKT_ID', cm, 'SHAPE', null, null, null, null);
    END;
    /

    BEGIN
    SDO_WFS_PROCESS.registerMTableView('http://www.example.com/myns',
            'COLA', mdsys.StringList('WFS_USER.COLA_MARKETS_CS',
            'WFS_USER.COLA_MARKETS_CS_DETAILS'),
            mdsys.StringList('MKT_ID', 'MKT_ID'), -- view keys per table
            mdsys.StringList('MKT_ID', 'MKT_ID'));-- corresponding table keys
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.14 SDO_WFS_PROCESS.RevokeFeatureTypeFromUser

#### Format

    SDO_WFS_PROCESS.RevokeFeatureTypeFromUser(
         ftnsUrl  IN VARCHAR2,
         ftName   IN VARCHAR2,
         userName IN VARCHAR2);

#### Description

Revokes access to a feature type from a database user.

#### Parameters

ftnsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

userName
Name of the database user.

#### Usage Notes

To grant access to a feature type to a database user, use the SDO_WFS_PROCESS.GrantFeatureTypeToUser procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example revokes access to the `COLA` feature type from user `SMITH`.

    BEGIN
      SDO_WFS_PROCESS.RevokeFeatureTypeFromUser('http://www.example.com/myns','COLA',
        'SMITH');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.15 SDO_WFS_PROCESS.RevokeMDAccessFromUser

#### Format

    SDO_WFS_PROCESS.RevokeMDAccessFromUser(
         userName  IN VARCHAR2);

#### Description

Revokes access to Web Feature Service metadata tables from a database user.

#### Parameters

userName
Name of the database user.

#### Usage Notes

To call this procedure, you should be connected to the database as a user with the DBA role.

To grant access to Web Feature Service metadata tables to a database user, use the SDO_WFS_PROCESS.GrantMDAccessToUser procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example revokes access to Web Feature Service metadata tables from the database user named `WFS_REL_USER`.

    BEGIN
      SDO_WFS_PROCESS.RevokeMDAccessToUser('WFS_REL_USER');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)

### 38.16 SDO_WFS_PROCESS.UnRegisterMTableView

#### Format

    SDO_WFS_PROCESS.UnRegisterMTableView(
         ftNsUrl IN VARCHAR2,
         ftName  IN VARCHAR2);

#### Description

Disables the publishing of content from a multitable view as a feature instance.

#### Parameters

ftNsUrl
Uniform resource locator (URL) of the namespace for the feature type.

ftName
Name of the feature type.

#### Usage Notes

The SDO_WFS_PROCESS.RegisterMTableView procedure must have been called previously to enable the publishing of content from the multitable view as a feature instance.

If you want to drop a feature type whose content comes from a multitable view, you must call this procedure before you call the SDO_WFS_PROCESS.DropFeatureType procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example unregisters a multitable view to disable the publishing of content from the view.

    DECLARE
    BEGIN
      SDO_WFS_PROCESS.unRegisterMTableView('http://www.example.com/myns', 'COLA');
    END;
    /

**Parent topic:** SDO_WFS_PROCESS Package (WFS Processing)
