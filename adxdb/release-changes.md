This preface contains descriptions of changes in Oracle XML DB for recent releases of Oracle Database.

- Changes in Oracle Database Release 18c, Version 1, for Oracle XML DB
  The changes in Oracle Database Release 18c, Version 1, for Oracle XML DB are described.

### Changes in Oracle Database Release 18c, Version 1, for Oracle XML DB

The changes in Oracle Database Release 18c, Version 1, for Oracle XML DB are described.

- New Features
  There are no new features for Oracle XML DB in this release.
- Deprecated Features
  The following features are deprecated in this release, and may be desupported in a future release.
- Desupported Features
  The following features are desupported in this release.

**Parent topic:** Changes in This Release for Oracle XML DB Developer's Guide

#### New Features

There are no new features for Oracle XML DB in this release.

**Parent topic:** Changes in Oracle Database Release 18c, Version 1, for Oracle XML DB

#### Deprecated Features

The following features are deprecated in this release, and may be desupported in a future release.

- PL/SQL package `DBMS_XMLQUERY`. Use package `DBMS_XMLGEN` instead.

- PL/SQL package `DBMS_XMLSAVE`. Use package `DBMS_XMLSTORE` instead.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in Oracle Database Release 18c, Version 1, for Oracle XML DB

#### Desupported Features

The following features are desupported in this release.

- PL/SQL subprograms `generateSchema` and `generateSchemas` in package `DBMS_XMLSCHEMA`. There are no replacements for these subprograms.

- The following subprograms in package `DBMS_XDB`. Use the subprograms with the same names in package `DBMS_XDBCONFIG` instead.

  - `addhttpexpiremapping`

  - `addmimemapping`

  - `addschemalocmapping`

  - `addservlet`

  - `addservletmapping`

  - `addservletsecrole`

  - `addxmlextension`

  - `cfg_get`

  - `cfg_refresh`

  - `cfg_update`

  - `deletehttpexpiremapping`

  - `deletemimemapping`

  - `deleteschemalocmapping`

  - `deleteservlet`

  - `deleteservletmapping`

  - `deleteservletsecrole`

  - `deletexmlextension`

  - `getftpport`

  - `gethttpport`

  - `getlistenerendpoint`

  - `setftpport`

  - `sethttpport`

  - `setlistenerendpoint`

  - `setlistenerlocalaccess`

- The following constants in package `DBMS_XDB`. Use the constants with the same name in package `DBMS_XDBCONFIG` instead.

  - `xdb_endpoint_http`

  - `xdb_endpoint_http2`

  - `xdb_protocol_tcp`

  - `xdb_protocol_tcps`

- All Oracle-specific SQL functions for updating XML data. Use XQuery Update instead. These are the desupported XML-updating functions:

  - `updateXML`

  - `insertChildXML`

  - `insertChildXMLbefore`

  - `insertChildXMLafter`

  - `insertXMLbefore`

  - `insertXMLafter`

  - `appendChildXML`

  - `deleteXML`

- Oracle XQuery functions `ora:matches` and `ora:replace`. Use the corresponding standard XQuery functions instead, that is, the functions with the same names but with namespace prefix `fn`: `fn:matches` and `fn:replace`.

- The following Oracle constructs that provide support for XML translations are desupported. There is no replacement for any of these constructs.

  - PL/SQL package `DBMS_XMLTRANSLATIONS`

  - Oracle XPath function `ora:translate`

  - XML Schema annotations `xdb:maxOccurs`, `xdb:srclang`, and `xdb:translate`

- The following XML Schema annotations are desupported. There is no replacement for any of these annotations.

  - `xdb:defaultTableSchema`

  - `xdb:maintainOrder`

  - `xdb:mapUnboundedStringToLob`

  - `xdb:maxOccurs`

  - `xdb:SQLCollSchema`

  - `xdb:SQLSchema`

  - `xdb:srclang`

  - `xdb:translate`

- The value `xml_clobs` for export parameter `data_options`. There is no replacement for this parameter.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in Oracle Database Release 18c, Version 1, for Oracle XML DB
