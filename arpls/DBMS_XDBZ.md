## 206  DBMS_XDBZ

The DBMS_XDBZ package controls the Oracle XML DB repository security, which is based on Access Control Lists (ACLs).

This chapter contains the following topics:

- Security Model

- Constants

- Summary of DBMS_XDBZ Subprograms

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/XML-DB-basics.md)

### 206.1 DBMS_XDBZ Security Model

Owned by `XDB`, the `DBMS_XDBZ` package must be created by `SYS` or `XDB`. The `EXECUTE` privilege is granted to `PUBLIC`. Subprograms in this package are executed using the privileges of the current user.

### 206.2 DBMS_XDBZ Constants

The `DBMS_XDBZ` package defines several constants that can be used for specifying parameter values.

The package uses the constants shown in following tables.

Table 206-1 DBMS_XDBZ Constants - Name Format

| Constant                    | Type          | Value | Description                   |
|:----------------------------|:--------------|:------|:------------------------------|
| `NAME_FORMAT_SHORT`         | `PLS_INTEGER` | `1`   | DB user name or LDAP nickname |
| `NAME_FORMAT_DISTINGUISHED` | `PLS_INTEGER` | `2`   | LDAP distinguished name       |

Table 206-2 DBMS_XDBZ Constants - Enable Option

| Constant             | Type          | Value | Description                                                                                                        |
|:---------------------|:--------------|:------|:-------------------------------------------------------------------------------------------------------------------|
| `ENABLE_CONTENTS`    | `PLS_INTEGER` | `1`   | Enables hierarchy for contents and is used by users when calling the ENABLE_HIERARCHY Procedure                    |
| `ENABLE_RESMETADATA` | `PLS_INTEGER` | `2`   | Enables hierarchy for resource metadata, that is, this table will store schema based custom metadata for resources |

Table 206-3 DBMS_XDBZ Constants - Enable Option Exercised

| Constant                 | Type          | Value | Description                                                                                                                                      |
|:-------------------------|:--------------|:------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `IS_ENABLED_CONTENTS`    | `PLS_INTEGER` | `1`   | If hierarchy was enabled for contents, that is, the ENABLE_HIERARCHY Procedure was called with `hierarchy_type` as `ENABLE_CONTENTS`             |
| `IS_ENABLED_RESMETADATA` | `PLS_INTEGER` | `2`   | If hierarchy was enabled for resource metadata, that is, the ENABLE_HIERARCHY Procedure was called with `hierarchy_type` as `ENABLE_RESMETADATA` |

### 206.3 Summary of DBMS_XDBZ Subprograms

This table lists the `DBMS_XDBZ` subprograms and briefly describes them.

Table 206-4 DBMS_XDBZ Package Subprograms

| Method                        | Description                                                                           |
|:------------------------------|:--------------------------------------------------------------------------------------|
| DISABLE_HIERARCHY Procedure   | Disables repository support for the specified `XMLTYPE` table or view                 |
| ENABLE_HIERARCHY Procedure    | Enables repository support for the specified `XMLType` table or view                  |
| GET_ACLOID Function           | Retrieves the ACL Object ID for the specified resource                                |
| GET_USERID Function           | Retrieves the user ID for the specified user                                          |
| IS_HIERARCHY_ENABLED Function | Determines if repository support for the specified `XMLType` table or view is enabled |
| PURGELDAPCACHE Function       | Purges the LDAP nickname cache                                                        |

#### 206.3.1 CREATENONCEKEY Procedure

This procedure generates a nonce value for use in digest authentication.

##### Syntax

    DBMS_XDBZ.CREATENONCEKEY;

#### 206.3.2 DISABLE_HIERARCHY Procedure

This procedure disables repository support for a particular `XMLType` table or view.

##### Syntax

    DBMS_XDBZ.DISABLE_HIERARCHY(
       object_schema IN VARCHAR2,
       object_name   IN VARCHAR2);

##### Parameters

Table 206-5 DISABLE_HIERARCHY Procedure Parameters

| Parameter       | Description                                |
|:----------------|:-------------------------------------------|
| `object_schema` | Schema name of the `XMLType` table or view |
| `object_name`   | Name of the `XMLType` table or view        |

#### 206.3.3 ENABLE_HIERARCHY Procedure

This procedure enables repository support for a particular `XMLType` table or view. This allows the use of a uniform ACL-based security model across all documents in the repository.

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/repository-access-control.md) for more information about

##### Syntax

    DBMS_XDBZ.ENABLE_HIERARCHY(
       object_schema   IN   VARCHAR2,
       object_name     IN   VARCHAR2,
       hierarchy_type  IN   PLS_INTEGER := DBMS_XDBZ.ENABLE_CONTENTS);

##### Parameters

Table 206-6 ENABLE_HIERARCHY Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `object_schema`  | Schema name of the `XMLType` table or view                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `object_name`    | Name of the `XMLType` table or view                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `hierarchy_type` | How to enable the hierarchy.<br>• `ENABLE_CONTENTS` - enable hierarchy for contents, that is, this table will store contents of resources in the repository<br>• `ENABLE_RESMETADATA` - enable hierarchy for resource metadata, that is, this table will store schema based custom metadata for resources<br>If this subprogram is called on a table, another call will have no effect. Note that you cannot enable hierarchy for both contents and resource metadata. |

#### 206.3.4 GET_ACLOID Function

This function retrieves the ACL Object ID for the specified resource, if the repository path is known.

##### Syntax

    DBMS_XDBZ.GET_ACLOID(
       aclpath   IN   VARCHAR2,
       acloid    OUT  RAW)
     RETURN BOOLEAN;

##### Parameters

Table 206-7 GET_ACLOID Function Parameters

| Parameter | Description                          |
|:----------|:-------------------------------------|
| `aclpath` | ACL resource path for the repository |
| `acloid`  | Returned Object ID                   |

##### Return Values

Returns `TRUE` if successful.

#### 206.3.5 GET_USERID Function

This function retrieves the user ID for the specified user name. The local database is searched first, and if found, the `USERID` is returned in 4-byte database format. Otherwise, the LDAP directory is searched, if available, and if found, the `USERID` is returned in 4-byte database format.

##### Syntax

    DBMS_XDBZ.GET_USERID(
       username IN  VARCHAR2,
       userid   OUT RAW,
       format   IN  BINARY_INTEGER := NAME_FORMAT_SHORT)
     RETURN BOOLEAN;

##### Parameters

Table 206-8 GET_USERID Function Parameters

| Parameter  | Description                                                                                                                                                                                                 |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `username` | Name of the database or LDAP user.                                                                                                                                                                          |
| `userid`   | Return parameter for the matching user id.                                                                                                                                                                  |
| `format`   | Format of the specified user name; valid options are:<br>• `DBMS_XDBZ.NAME_FORMAT_SHORT` (default) -- DB user name or LDAP nickname<br>• `DBMS_XDBZ.NAME_FORMAT_DISTINGUISHIED` -- LDAP distinguished name. |

##### Return Values

Returns `TRUE` if successful.

#### 206.3.6 IS_HIERARCHY_ENABLED Function

This function determines if repository support for the specified `XMLType` table or view is enabled.

##### Syntax

    DBMS_XDBZ.IS_HIERARCHY_ENABLED(
       object_schema   IN  VARCHAR2,
       object_name     IN  VARCHAR2,
       hierarchy_type  IN  PLS_INTEGER := IS_ENABLED_CONTENTS)
     RETURN BOOLEAN;

##### Parameters

Table 206-9 IS_HIERARCHY_ENABLED Function Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                        |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `object_schema`  | Schema name of the `XMLType` table or view                                                                                                                                                                                                                                                                                                                                         |
| `object_name`    | Name of the `XMLType` table or view                                                                                                                                                                                                                                                                                                                                                |
| `hierarchy_type` | Type of hierarchy to check for:<br>• `IS_ENABLED_CONTENTS` - if hierarchy was enabled for contents, that is, the ENABLE_HIERARCHY Procedure was called with `hierarchy_type` as `ENABLE_CONTENTS`<br>• `IS_ENABLED_RESMETADATA` - if hierarchy was enabled for resource metadata, that is, the ENABLE_HIERARCHY Procedure was called with `hierarchy_type` as `ENABLE_RESMETADATA` |

##### Return Values

Returns `TRUE` if the given XMLTYPE table or view has the XDB Hierarchy enabled with the specified type.

#### 206.3.7 PURGELDAPCACHE Function

This function purges the LDAP nickname cache.

It returns `TRUE` if successful.

##### Syntax

    DBMS_XDBZ.PURGELDAPCACHE
     RETURN BOOLEAN;
