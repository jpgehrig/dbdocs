## 24  SDO_CSW_PROCESS Package \[deprecated\]

The MDSYS.SDO_CSW_PROCESS package is deprecated.

You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

The rest of this chapter provides reference information on the deprecated MDSYS.SDO_CSW_PROCESS subprograms, listed in alphabetical order.

- SDO_CSW_PROCESS.DeleteCapabilitiesInfo
- SDO_CSW_PROCESS.DeleteDomainInfo
- SDO_CSW_PROCESS.DeletePluginMap
- SDO_CSW_PROCESS.DeleteRecordViewMap
- SDO_CSW_PROCESS.GetRecordTypeId
- SDO_CSW_PROCESS.InsertCapabilitiesInfo
- SDO_CSW_PROCESS.InsertDomainInfo
- SDO_CSW_PROCESS.InsertPluginMap
- SDO_CSW_PROCESS.InsertRecordViewMap
- SDO_CSW_PROCESS.InsertRtDataUpdated
- SDO_CSW_PROCESS.InsertRtMDUpdated

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 24.1 SDO_CSW_PROCESS.DeleteCapabilitiesInfo

#### Format

    SDO_CSW_PROCESS.DeleteCapabilitiesInfo();

#### Description

Deletes the capabilities information that had been set by the SDO_CSW_PROCESS.InsertCapabilitiesInfo procedure.

#### Parameters

None.

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example deletes the capabilities information that had been set by the SDO_CSW_PROCESS.InsertCapabilitiesInfo procedure.

    BEGIN
      SDO_CSW_PROCESS.DeleteCapabilitiesInfo;
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.2 SDO_CSW_PROCESS.DeleteDomainInfo

#### Format

    SDO_CSW_PROCESS.DeleteDomainInfo(
         recordTypeId  IN NUMBER,
         propertyName  IN VARCHAR2,
         parameterName IN VARCHAR2);

#### Description

Deletes domain information related to a record type.

#### Parameters

recordTypeId
ID of the record type.

propertyName
Name of the property.

parameterName
Name of domain parameter to be deleted.

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example deletes domain information about the `resultType` parameter for a specified record type.

    DECLARE
      rtId NUMBER;
    BEGIN
      rtId :=
        sdo_csw_process.getRecordTypeId('http://www.opengis.net/cat/csw', 'Record');
      sdo_csw_process.deleteDomainInfo(rtId, null, 'GetRecords.resultType');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.3 SDO_CSW_PROCESS.DeletePluginMap

#### Format

    SDO_CSW_PROCESS.DeletePluginMap(
        rtnsUrl IN VARCHAR2,
        rtName  IN VARCHAR2);

#### Description

Unregisters a plugin for processing and extracting non-GML spatial content for a record type.

#### Parameters

rtnsUrl
Uniform resource locator of namespace of the record type.

rtName
Name of the record type.

#### Usage Notes

To register a plugin, which is a user-defined implementation of the `extractSDO` function, use the SDO_CSW_PROCESS.InsertPluginMap procedure.

For information about creating and using the `extractSDO` function, see [Spatial Path Extractor Function (extractSDO) \[deprecated implementation\]](csw_support_old.md).

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example unregisters a plugin.

    BEGIN
      SDO_CSW_PROCESS.deletePluginMap('http://www.opengis.net/cat/csw',
        'Record');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.4 SDO_CSW_PROCESS.DeleteRecordViewMap

#### Format

    SDO_CSW_PROCESS.DeleteRecordViewMap(
        recordTypeNs   IN VARCHAR2,
        viewSrcName    IN VARCHAR2,
        targetTypeName IN VARCHAR2);

#### Description

Deletes information related to record view transformation.

#### Parameters

recordTypeNs
URL of the namespace of the record type.

viewSrcName
Name of the source record type (for example, `BriefRecord`, `DCMIRecord`, `Record`, or `SummaryRecord`).

targetTypeName
Name of the destination record type (for example, `BriefRecord`, `DCMIRecord`, `Record`, or `SummaryRecord`).

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example deletes information related to record view transformation from source record type `BriefRecord` and destination record type `Record`.

    BEGIN
      SDO_CSW_PROCESS.deleteRecordViewMap('http://www.opengis.net/cat/csw',
        'BriefRecord',
        'Record');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.5 SDO_CSW_PROCESS.GetRecordTypeId

#### Format

    SDO_CSW_PROCESS.GetRecordTypeId(
         rtnsUrl IN VARCHAR2,
         rtName  IN VARCHAR2) RETURN NUMBER;

#### Description

Gets the record type ID for a type (specified by namespace and type name).

#### Parameters

rtnsUrl
Uniform resource locator (URL) of the namespace of the record type.

rtName
Name of the record type.

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example gets the record type ID of a record type named `Record`.

    DECLARE
      rtId NUMBER;
    BEGIN
      rtId := SDO_CSW_PROCESS.getRecordTypeId('http://www.opengis.net/cat/csw',
        'Record');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.6 SDO_CSW_PROCESS.InsertCapabilitiesInfo

#### Format

    SDO_CSW_PROCESS.InsertCapabilitiesInfo(
         capabilitiesInfo IN XMLTYPE);

#### Description

Inserts the capabilities template information.

#### Parameters

capabilitiesInfo
XML document for the capabilities template, which is used at runtime to generate capabilities documents.

#### Usage Notes

At runtime, the capabilities document is dynamically generated by binding feature type information from the CSW metadata with the capabilities template. For information about capabilities documents, see [Capabilities Documents \[deprecated implementation\]](csw_support_old.md).

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example inserts the capabilities template information.

    BEGIN
      SDO_CSW_PROCESS.insertCapabilitiesInfo(
        xmltype(bfilename('CSWUSERDIR', 'cswloadcapabilities.xml'),
           nls_charset_id('AL32UTF8')));
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.7 SDO_CSW_PROCESS.InsertDomainInfo

#### Format

    SDO_CSW_PROCESS.InsertDomainInfo(
        recordTypeId  IN NUMBER,
        propertyName  IN VARCHAR2,
        parameterName IN VARCHAR2,
        pValue        IN MDSYS.STRINGLIST);

#### Description

Inserts domain information related to a record type.

#### Parameters

recordTypeId
ID of the record type

propertyName
Name of a domain property.

parameterName
Name of a domain parameter

pValue
An array of strings containing parameter values for `parameterName`. `The MDSYS.STRINGLIST type is defined as VARRAY(1000000) OF VARCHAR2(4000)`.

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example inserts domain information for the record type named `Record`.

    DECLARE
      rtId NUMBER;
    BEGIN
      rtId := SDO_CSW_PROCESS.getRecordTypeId(
        'http://www.opengis.net/cat/csw', 'Record');
      SDO_CSW_PROCESS.insertDomainInfo(rtId,
        null,
        'GetRecords.resultType',
        MDSYS.STRINGLIST('hits', 'results', 'validate'));
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.8 SDO_CSW_PROCESS.InsertPluginMap

#### Format

    SDO_CSW_PROCESS.InsertPluginMap(
        rtnsUrl           IN VARCHAR2,
        rtName            IN VARCHAR2,
        pluginPackageName IN VARCHAR2);

#### Description

Registers a plugin for processing and extracting non-GML spatial content for a record type.

#### Parameters

rtnsUrl
Uniform resource locator of the namespace of the record type.

rtName
Name of the record type.

pluginPackageName
Name of the PL/SQL package object for the plugin.

#### Usage Notes

The plugin must contain the user-defined implementation of the `extractSDO` function. A plugin is needed if the records are not in GML format. For detailed information about creating and using the `extractSDO` function, see [Spatial Path Extractor Function (extractSDO) \[deprecated implementation\]](csw_support_old.md).

You must grant EXECUTE access on the plugin package (`pluginPackageName` parameter) to user MDSYS and to the CSW administrative user.

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example registers a plugin.

    BEGIN
      SDO_CSW_PROCESS.insertPluginMap('http://www.opengis.net/cat/csw',
        'Record', 'csw_admin_usr.csw_RT_1_package');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.9 SDO_CSW_PROCESS.InsertRecordViewMap

#### Format

    SDO_CSW_PROCESS.InsertRecordViewMap(
        recordTypeNs   IN VARCHAR2,
        viewSrcName    IN VARCHAR2,
        targetTypeName IN VARCHAR2,
        mapInfo        IN XMLTYPE,
        mapType        IN VARCHAR2);

#### Description

Inserts information related to record view transformation.

#### Parameters

recordTypeNs
URL of the namespace of the record type.

viewSrcName
Name of the source record type (for example, `BriefRecord`, `DCMIRecord`, `Record`, or `SummaryRecord`).

targetTypeName
Name of the destination of the record type (for example, `BriefRecord`, `DCMIRecord`, `Record`, or `SummaryRecord`).

mapInfo
XSLT definition of the mapping. (See the comments in the example at the end of this section for a transformation from `BriefRecord` type to `Record` type.)

mapType
Map type (brief, summary, and so on)

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example inserts information related to transformation from `BriefRecord` type to `Record` type.

    create or replace directory CSWUSERDIR as 'dir_path_where_mapinfo.xsl_file_is_located' ;

    /*
    // Content of  mapinfo.xsl could be that which transforms
    // all <csw:BriefRecord> node  to <csw:Record> node, where csw is
    // the namespace alias for "http://www.opengis.net/cat/csw"

    <?xml version="1.0" encoding="UTF-8"?>
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:csw="http://www.opengis.net/cat/csw">
    <xsl:output method="xml" version="1.0" encoding="UTF-8" indent="yes" />

    <xsl:template match="/">
      <csw:Record xmlns:csw="http://www.opengis.net/cat/csw" xmlns:dc="http://www.purl.org/dc/elements/1.1/" xmlns:ows="http://www.opengis.net/ows" xmlns:dct="http://www.purl.org/dc/terms/">
        <xsl:apply-templates select="@*|node()"/>
      </csw:Record>
    </xsl:template>

    <xsl:template match="csw:BriefRecord">
      <xsl:apply-templates select="@*|node()"/>
    </xsl:template>

    <xsl:template match="@*|node()">
      <xsl:copy>
        <xsl:apply-templates select="@*|node()"/>
      </xsl:copy>
    </xsl:template>

    </xsl:stylesheet>
    */

    DECLARE
      rtId NUMBER;
    BEGIN
      SDO_CSW_PROCESS.insertRecordViewMap('http://www.opengis.net/cat/csw',
        'BriefRecord',
        'Record',
        xmltype(bfilename('CSWUSERDIR', 'mapinfo.xsl'), nls_charset_id('AL32UTF8')),
        'brief');
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.10 SDO_CSW_PROCESS.InsertRtDataUpdated

#### Format

    SDO_CSW_PROCESS.InsertRtDataUpdated(
         ns             IN VARCHAR2,
         name           IN VARCHAR2,
         updatedRowList IN ROWPOINTERLIST,
         updateTs       IN TIMESTAMP);

#### Description

Inserts a notification that the data for a record type was updated in the database.

#### Parameters

ns
Namespace of the record type.

name
Name of the record type.

updatedRowList
List of rowids of rows that have been updated.

updateTS
Timestamp value indicating when the data was updated.

#### Usage Notes

This procedure is used for CSW cache data synchronization. It queries the MDSYS.CSW_RECORD_TYPES\$ system table.

For information about support for Catalog Services for the Web, see [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example inserts a notification for a specified record type that the data was updated for the rows associated with specific rowids.

    BEGIN
    updatedRowIdList:= . . . -- list of rowIds that have been updated
    --  in the table referred to by the dataPointer column of the
    --  mdsys.CSW_Record_Types$ table for the row whose
    --  typeNameNS column value is 'http://www.opengis.net/cat/csw' and
    --  typeName column value is 'Record'
    . . .
      SDO_CSW_PROCESS.insertRtDataUpdated('http://www.opengis.net/cat/csw',
        'Record',  updatedRowIdList, sysdate);
    . . .
    END;
    /

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]

### 24.11 SDO_CSW_PROCESS.InsertRtMDUpdated

#### Format

    SDO_CSW_PROCESS.InsertRtMDUpdated(
         ns       IN VARCHAR2,
         name     IN VARCHAR2,
         updateTs IN TIMESTAMP);

#### Description

Inserts a notification that the metadata for a record type was updated in the database.

#### Parameters

ns
Namespace of the record type.

name
Name of the record type.

updateTS
Date and time when the metadata was updated.

#### Usage Notes

The MDSYS.SDO_CSW_PROCESS package is deprecated. You are encouraged not to use it, and instead to use the [SDO_CSW Package (Catalog Services for the Web)](SDO_CSW-reference.md) and the CSW support described in [Catalog Services for the Web (CSW) Support](catalog-services-web-csw-concepts.md).

#### Examples

The following example inserts a notification that the metadata for the `Record` record type was updated in the database.

    BEGIN
      SDO_CSW_PROCESS.insertRtMDUpdated('http://www.opengis.net/cat/csw',
        'Record', sysdate);
    END;

**Parent topic:** SDO_CSW_PROCESS Package \[deprecated\]
