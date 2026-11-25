## 201 DBMS_XDB_CONSTANTS

The `DBMS_XDB_CONSTANTS` package provides an interface to commonly used constants. Users should use constants instead of dynamic strings to avoid typographical errors.

This chapter contains the following topics:

- Security Model

- Summary of DBMS_XDB_CONSTANTS Subprograms

### 201.1 DBMS_XDB_CONSTANTS Security Model

Owned by `XDB`, the `DBMS_XDB_CONSTANTS` package must be created by `SYS` or `XDB`. The `EXECUTE` privilege is granted to `PUBLIC`. Subprograms in this package are executed using the privileges of the current user.

### 201.2 Summary of DBMS_XDB_CONSTANTS Subprograms

This table lists the `DBMS_XDB_CONSTANTS` subprograms and briefly describes them.

Table 201-1 DBMS_XDB_CONSTANTS Package Subprograms

| Subprograms                           | Description                                                                                     |
|:--------------------------------------|:------------------------------------------------------------------------------------------------|
| ENCODING_DEFAULT Function             | Returns `'AL32UTF8'`                                                                            |
| ENCODING_ISOLATIN1 Function           | Returns `'WE8ISO8859P1'`                                                                        |
| ENCODING_UTF8 Function                | Returns `'AL32UTF8'`                                                                            |
| ENCODING_WIN1252 Function             | Returns `'WE8MSWIN1252'`                                                                        |
| NAMESPACE_ACL Function                | Returns `'http://xmlns.oracle.com/xdb/acl.xsd'`                                                 |
| NAMESPACE_METADATA Function           | Returns `'http://xmlns.oracle.com/xdbuserMetaData'`                                             |
| NAMESPACE_ORACLE Function             | Returns `'http://xmlns.oracle.com'`                                                             |
| NAMESPACE_ORACLE_XDB Function         | Returns `'http://xmlns.oracle.com/xdb'`                                                         |
| NAMESPACE_RESOURCE Function           | Returns` 'http://xmlns.oracle.com/xdb/XDBResource.xsd'`                                         |
| NAMESPACE_RESOURCE_EVENT Function     | Returns `'http://xmlns.oracle.com/resourceEvent'`                                               |
| NAMESPACE_RESOURCE_CONFIG Function    | Returns `'http://xmlns.oracle.com/XDBResConfig.xsd'`                                            |
| NAMESPACE_XDBSCHEMA Function          | Returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`                                           |
| NAMESPACE_XMLDIFF Function            | Returns `'http://xmlns.oracle.com/xdb/xdiff.xsd'`                                               |
| NAMESPACE_XMLINSTANCE Function        | Returns `'http://www.w3.org/2001/XMLSchema-instance'`                                           |
| NAMESPACE_XMLSCHEMA Function          | Returns `'http://www.w3.org/2001/XMLSchema'`                                                    |
| NSPREFIX_ACL_ACL Function             | Returns `'xmlns:acl= 'http://xmlns.oracle.com/acs.xsd'`                                         |
| NSPREFIX_RESCONFIG_RC Function        | Returns `'xmlns:rc="http://xmlns.oracle.com/xdb/XDBResConfig.xsd"'`                             |
| NSPREFIX_RESOURCE_R Function          | Returns `'xmlns:r="http://xmlns.oracle.com/XDBResource.xsd'`                                    |
| NSPREFIX_XDB_XDB Function             | Returns `'http://xmlns.oracle.com/xdb'`                                                         |
| NSPREFIX_XMLINSTANCE_XSI Function     | Returns `'xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"'`                               |
| NSPREFIX_XMLDIFF_XD Function          | Returns `'xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"'`                                    |
| NSPREFIX_XMLSCHEMA_XSD Function       | Returns `'xmlns:xsd="http://www.w3.org/2001/XMLSchema"'`                                        |
| SCHEMAURL_ACL Function                | Returns `'http://xmlns.oracle.com/xdb/acl.xsd'`                                                 |
| SCHEMAELEM_RES_ACL Function           | Returns `'http://xmlns.oracle.com/xdb/acl.xsd#acl'`                                             |
| SCHEMAELEM_RESCONTENT_BINARY Function | Returns` 'http://xmlns.oracle.com/xdb/XDBSchema.xsd#binary'`                                    |
| SCHEMAELEM_RESCONTENT_TEXT Function   | Returns` 'http://xmlns.oracle.com/xdb/XDBSchema.xsd#text'`                                      |
| SCHEMAURL_RESOURCE Function           | Returns` 'http://xmlns.oracle.com/xdb/XDBResource.xsd'`                                         |
| SCHEMAURL_XDBSCHEMA Function          | Returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`                                           |
| XDBSCHEMA_PREFIXES Function           | Returns `'xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xdb="http://xmlns.oracle.com/xdb'` |
| XSD_ATTRIBUTE Function                | Returns `'attribute'`                                                                           |
| XSD_COMPLEX_TYPE Function             | Returns `'complexType'`                                                                         |
| XSD_ELEMENT Function                  | Returns `'element'`                                                                             |
| XSD_GROUP Function                    | Returns `'group'`                                                                               |

#### 201.2.1 ENCODING_DEFAULT Function

This function returns `'AL32UTF8'`.

##### Syntax

    DBMS_XDB_CONSTANTS.ENCODING_DEFAULT
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'AL32UTF8'`

#### 201.2.2 ENCODING_ISOLATIN1 Function

This function returns `'WE8ISO8859P1'`.

##### Syntax

    DBMS_XDB_CONSTANTS.ENCODING_ISOLATIN1
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'WE8ISO8859P1'`

#### 201.2.3 ENCODING_UTF8 Function

This function returns `'AL32UTF8'`.

##### Syntax

    DBMS_XDB_CONSTANTS.ENCODING_UTF8
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'AL32UTF8'`

#### 201.2.4 ENCODING_WIN1252 Function

This function returns `'WE8MSWIN1252'`.

##### Syntax

    DBMS_XDB_CONSTANTS.ENCODING_WIN1252
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'WE8MSWIN1252'`

#### 201.2.5 NAMESPACE_ACL Function

This function returns `'http://xmlns.oracle.com/xdb/acl.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_ACL
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/acl.xsd'`

#### 201.2.6 NAMESPACE_METADATA Function

This function returns `'http://xmlns.oracle.com/xdbuserMetaData'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_METADATA
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdbuserMetaData'`

#### 201.2.7 NAMESPACE_ORACLE Function

This function returns `'http://xmlns.oracle.com'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_ORACLE
      RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com'`

#### 201.2.8 NAMESPACE_ORACLE_XDB Function

This function returns `'http://xmlns.oracle.com/xdb'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_ORACLE_XDB
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb'`

#### 201.2.9 NAMESPACE_RESOURCE Function

This function returns `'/XDBResource.xsd'`

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_RESOURCE
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBResource.xsd`

#### 201.2.10 NAMESPACE_RESOURCE_EVENT Function

This function returns `'http://xmlns.oracle.com/resourceEvent'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_RESOURCE_EVENT
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/resourceEvent'`

#### 201.2.11 NAMESPACE_RESOURCE_CONFIG Function

This function returns `'http://xmlns.oracle.com/XDBResConfig.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_RESOURCE_CONFIG
      RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/XDBResConfig.xsd'`

#### 201.2.12 NAMESPACE_XDBSCHEMA Function

This function returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_XDBSCHEMA
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`

#### 201.2.13 NAMESPACE_XMLDIFF Function

This function returns `'http://xmlns.oracle.com/xdb/xdiff.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_XMLDIFF
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/xdiff.xsd'`

#### 201.2.14 NAMESPACE_XMLINSTANCE Function

This function returns `'http://www.w3.org/2001/XMLSchema-instance'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NAMESPACE_XMLINSTANCE
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://www.w3.org/2001/XMLSchema-instance'`

#### 201.2.15 NAMESPACE_XMLSCHEMA Function

This function returns `'http://www.w3.org/2001/XMLSchema'`.

##### Syntax

    DBMS_XDB_CONSTANTS. NAMESPACE_XMLSCHEMA
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://www.w3.org/2001/XMLSchema'`

#### 201.2.16 NSPREFIX_ACL_ACL Function

This function returns `'xmlns:acl= 'http://xmlns.oracle.com/acs.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_ACL_ACL
      RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:acl= 'http://xmlns.oracle.com/acs.xsd'`

#### 201.2.17 NSPREFIX_RESCONFIG_RC Function

This function returns `''xmlns:rc="http://xmlns.oracle.com/xdb/XDBResConfig.xsd"'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_RESCONFIG_RC
      RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`Returns ''xmlns:rc="http://xmlns.oracle.com/xdb/XDBResConfig.xsd"'`

#### 201.2.18 NSPREFIX_RESOURCE_R Function

This function returns `'xmlns:r="http://xmlns.oracle.com/XDBResource.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_RESOURCE_R
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:r="http://xmlns.oracle.com/XDBResource.xsd'`

#### 201.2.19 NSPREFIX_XDB_XDB Function

This function returns `'http://xmlns.oracle.com/xdb'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_XDB_XDB
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb'`

#### 201.2.20 NSPREFIX_XMLINSTANCE_XSI Function

This function returns `'xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_XMLINSTANCE_XSI
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`'

#### 201.2.21 NSPREFIX_XMLDIFF_XD Function

This function returns `'xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_XMLDIFF_XD
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:xd="http://xmlns.oracle.com/xdb/xdiff.xsd"'`

#### 201.2.22 NSPREFIX_XMLSCHEMA_XSD Function

This function returns `'xmlns:xsd="http://www.w3.org/2001/XMLSchema"'`.

##### Syntax

    DBMS_XDB_CONSTANTS.NSPREFIX_XMLSCHEMA_XSD
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:xsd="http://www.w3.org/2001/XMLSchema"'`

#### 201.2.23 SCHEMAURL_ACL Function

This function returns `'http://xmlns.oracle.com/xdb/acl.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAURL_ACL
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/acl.xsd'`

#### 201.2.24 SCHEMAELEM_RES_ACL Function

This function returns `'http://xmlns.oracle.com/xdb/acl.xsd#acl'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAELEM_RES_ACL
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/acl.xsd#acl'`

#### 201.2.25 SCHEMAELEM_RESCONTENT_BINARY Function

This function returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd#binary'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAELEM_RESCONTENT_BINARY
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBSchema.xsd#binary'`

#### 201.2.26 SCHEMAELEM_RESCONTENT_TEXT Function

This function returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd#text'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAELEM_RESCONTENT_TEXT
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBSchema.xsd#text'`

#### 201.2.27 SCHEMAURL_RESOURCE Function

This function returns `'http://xmlns.oracle.com/xdb/XDBResource.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAURL_RESOURCE
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBResource.xsd'`

#### 201.2.28 SCHEMAURL_XDBSCHEMA Function

This function returns `'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`.

##### Syntax

    DBMS_XDB_CONSTANTS.SCHEMAURL_XDBSCHEMA
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'http://xmlns.oracle.com/xdb/XDBSchema.xsd'`

#### 201.2.29 XDBSCHEMA_PREFIXES Function

This function returns `'xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xdb="http://xmlns.oracle.com/xdb'`.

##### Syntax

    DBMS_XDB_CONSTANTS.XDBSCHEMA_PREFIXES
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xdb="http://xmlns.oracle.com/xdb'`

#### 201.2.30 XSD_ATTRIBUTE Function

This function returns `'attribute'`.

##### Syntax

    DBMS_XDB_CONSTANTS.XSD_ATTRIBUTE
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'attribute'`

#### 201.2.31 XSD_COMPLEX_TYPE Function

This function returns `'complexType'`.

##### Syntax

    DBMS_XDB_CONSTANTS.XSD_COMPLEX_TYPE
      RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'complexType'`

#### 201.2.32 XSD_ELEMENT Function

This function returns `'element'`.

##### Syntax

    DBMS_XDB_CONSTANTS. XSD_ELEMENT
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'element'`

#### 201.2.33 XSD_GROUP Function

This function returns `'group'`

##### Syntax

    DBMS_XDB_CONSTANTS.XSD_GROUP
     RETURN VARCHAR2 DETERMINISTIC;

##### Return Value

`'group'`
