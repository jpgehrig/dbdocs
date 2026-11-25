## 70  DBMS_EPG

The `DBMS_EPG` package implements the embedded PL/SQL gateway that enables a Web browser to invoke a PL/SQL stored procedure through an HTTP listener.

This chapter contains the following topics:

- Overview

- Security Model

- Exceptions

- Data Structures

  - VARCHAR2_TABLE Table Type

- Subprogram Groups

- Summary of DBMS_EPG Subprograms

### 70.1 DBMS_EPG Overview

The `DBMS_EPG` package is a platform on which PL/SQL users develop and deploy PL/SQL Web applications. The embedded PL/SQL gateway is an embedded version of the gateway that runs in the XML database HTTP server in the Oracle database. It provides the core features of `mod_plsql` in the database but does not require the Oracle HTTP server powered by Apache.

In order to make a PL/SQL application accessible from a browser by way of HTTP, a Database Access Descriptor (DAD) must be created and mapped to a virtual path. A DAD is a set of configuration values used for database access and the virtual path mapping makes the application accessible under a virtual path of the XML DB HTTP Server. A DAD is represented as a servlet in XML DB HTTP Server.

### 70.2 DBMS_EPG Security Model

The `XDBADMIN` role is required to invoke the configuration interface. It may invoked by the database user "`XDB`".

The authorization interface can be invoked by any user.

### 70.3 DBMS_EPG Exceptions

The table in this topic lists the exceptions raised by the `DBMS_EPG` package.

Table 70-1 DBMS_EPG Exceptions

| Exception       | Error Code | Description                                                                                                   |
|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------|
| `DAD_NOT_FOUND` | 20000      | Database Access Descriptor (DAD) %s not found. Ensure that the name of the DAD is correct and that it exists. |

### 70.4 DBMS_EPG Data Structures

The `DBMS_EPG` package defines a `TABLE` type.

#### VARCHAR2_TABLE Table Type

This type is used by the procedures `GET_ALL_GLOBAL_ATTRIBUTES`, `GET_ALL_DAD_ATTRIBUTES`, `GET_ALL_DAD_MAPPINGS`, and `GET_DAD_LIST` to return lists of attribute names, attribute values, virtual paths, and database access descriptors (DAD).

    TYPE VARCHAR2_TABLE IS TABLE OF VARCHAR2(4000) INDEX BY BINARY_INTEGER;

### 70.5 DBMS_EPG Subprogram Groups

The DBMS_EPG consists of two interfaces: configuration subprograms and authorization subprograms.

- Configuration Subprograms

- Authorization Subprograms

#### 70.5.1 DBMS_EPG Configuration Subprograms

The Configuration subprogram group contain the subprogram interfaces to examine and modify the global and database access descriptor (DAD) specific settings of the embedded PL/SQL gateway.

Table 70-2 Configuration Subprogram Group

| Subprogram                          | Description                                                       |
|:------------------------------------|:------------------------------------------------------------------|
| CREATE_DAD Procedure                | Creates a new DAD                                                 |
| DELETE_DAD_ATTRIBUTE Procedure      | Deletes a DAD attribute                                           |
| DELETE_GLOBAL_ATTRIBUTE Procedure   | Deletes a global attribute                                        |
| DROP_DAD Procedure                  | Drops a DAD                                                       |
| GET_ALL_DAD_ATTRIBUTES Procedure    | Retrieves all the attributes of a DAD.                            |
| GET_ALL_DAD_MAPPINGS Procedure      | Retrieves all virtual paths to which the specified DAD is mapped. |
| GET_ALL_GLOBAL_ATTRIBUTES Procedure | Retrieves all global attributes and values                        |
| GET_DAD_ATTRIBUTE Function          | Retrieves the value of a DAD attribute                            |
| GET_DAD_LIST Procedure              | Retrieves a list of all DADs for an Embedded Gateway instance.    |
| GET_GLOBAL_ATTRIBUTE Function       | Retrieves the value of a global attribute                         |
| MAP_DAD Procedure                   | Maps a DAD to the specified virtual path.                         |
| SET_DAD_ATTRIBUTE Procedure         | Sets the value for a DAD                                          |
| SET_GLOBAL_ATTRIBUTE Procedure      | Sets the value of a global attribute                              |
| UNMAP_DAD Procedure                 | Unmaps a DAD from the specified virtual path                      |

#### 70.5.2 DBMS_EPG Authorization Subprograms

The Authorization subprogram group contains the subprogram interfaces to authorize and deauthorize the use of a database user's privileges by the embedded PL/SQL gateway through a specific database access descriptor (DAD)

Table 70-3 Authorization Subprogram Group

| Subprogram                | Description                                                                                                           |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------|
| AUTHORIZE_DAD Procedure   | Authorizes a DAD to invoke procedures and access document tables with a database user's privileges                    |
| DEAUTHORIZE_DAD Procedure | Deauthorizes a DAD with regard to invoking procedures and accessing document tables with a database user's privileges |

### 70.6 Summary of DBMS_EPG Subprograms

This table lists the `DBMS_ALERT` subprograms and briefly describes them.

Table 70-4 DBMS_EPG Package Subprograms

| Subprogram                          | Description                                                                                                           |
|:------------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| AUTHORIZE_DAD Procedure             | authorizes a DAD to invoke procedures and access document tables with a database user's privileges                    |
| CREATE_DAD Procedure                | Creates a new DAD                                                                                                     |
| DEAUTHORIZE_DAD Procedure           | Deauthorizes a DAD with regard to invoking procedures and accessing document tables with a database user's privileges |
| DELETE_DAD_ATTRIBUTE Procedure      | Deletes a DAD attribute                                                                                               |
| DELETE_GLOBAL_ATTRIBUTE Procedure   | Deletes a global attribute                                                                                            |
| DROP_DAD Procedure                  | Drops a DAD                                                                                                           |
| GET_ALL_DAD_ATTRIBUTES Procedure    | Retrieves all the attributes of a DAD.                                                                                |
| GET_ALL_DAD_MAPPINGS Procedure      | Retrieves all virtual paths to which the specified DAD is mapped.                                                     |
| GET_ALL_GLOBAL_ATTRIBUTES Procedure | Retrieves all global attributes and values                                                                            |
| GET_DAD_ATTRIBUTE Function          | Retrieves the value of a DAD attribute                                                                                |
| GET_DAD_LIST Procedure              | Retrieves a list of all DADs for an Embedded Gateway instance.                                                        |
| GET_GLOBAL_ATTRIBUTE Function       | Retrieves the value of a global attribute                                                                             |
| MAP_DAD Procedure                   | Maps a DAD to the specified virtual path.                                                                             |
| SET_DAD_ATTRIBUTE Procedure         | Sets the value for a DAD                                                                                              |
| SET_GLOBAL_ATTRIBUTE Procedure      | Sets the value of a global attribute                                                                                  |
| UNMAP_DAD Procedure                 | Unmaps a DAD from the specified virtual path                                                                          |

#### 70.6.1 AUTHORIZE_DAD Procedure

This procedure authorizes a DAD to invoke procedures and access document tables with a database user's privileges. The invoker can always authorize the use of her/his own privileges.

**See Also:**

Authorization Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.AUTHORIZE_DAD (
       dad_name  IN  VARCHAR2,
       path     IN  VARCHAR2 DEFAULT NULL);

##### Parameters

Table 70-5 AUTHORIZE_DAD Procedure Parameters

| Parameter  | Description                                                               |
|:-----------|:--------------------------------------------------------------------------|
| `dad_name` | The name of the DAD to create                                             |
| `user`     | The user whose privileges to deauthorize. If use, the invoker is assumed. |

##### Usage Notes

- To authorize the use of another user's privileges, the invoker must have the `ALTER` `USER` system privilege.

- The DAD must exist but its "database-username" DAD attribute does not have to be set to user to authorize.

- Multiple users can authorize the same DAD and it is up to the DAD's "database-username" setting to decide which user's privileges to use.

##### Exceptions

Raises an error if the DAD or user does not exist, or the invoker does not have the needed system privilege.

##### Examples

    DBMS_EPG.AUTHORIZE_DAD('HR');

#### 70.6.2 CREATE_DAD Procedure

This procedure creates a new DAD.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.CREATE_DAD (
       dad_name  IN  VARCHAR2,
       path      IN  VARCHAR2 DEFAULT NULL);

##### Parameters

Table 70-6 CREATE_DAD Procedure Parameters

| Parameter  | Description                              |
|:-----------|:-----------------------------------------|
| `dad_name` | The name of the DAD to create            |
| `path`     | The virtual path to which to map the DAD |

#### 70.6.3 DEAUTHORIZE_DAD Procedure

This procedure deauthorizes a DAD with regard to invoking procedures and accessing document tables with a database user's privileges. The invoker can always deauthorize the use of his own privileges.

**See Also:**

Authorization Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.DEAUTHORIZE_DAD (
       dad_name  IN  VARCHAR2,
       path      IN  VARCHAR2 DEFAULT NULL);

##### Parameters

Table 70-7 DEAUTHORIZE_DAD Procedure Parameters

| Parameter  | Description                                                               |
|:-----------|:--------------------------------------------------------------------------|
| `dad_name` | The name of the DAD for which to deauthorize use                          |
| `user`     | The user whose privileges to deauthorize. If use, the invoker is assumed. |

##### Usage Notes

To deauthorize the use of another user's privileges, the invoker must have the `ALTER` `USER` system privilege.

##### Exceptions

Raises an error if the DAD or user does not exist, or the invoker does not have the needed system privilege.

##### Examples

    DBMS_EPG.DEAUTHORIZE_DAD('HR');

#### 70.6.4 DELETE_DAD_ATTRIBUTE Procedure

This procedure deletes a DAD attribute.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.DELETE_DAD_ATTRIBUTE (
       dad_name      IN  VARCHAR2,
       attr_name     IN  VARCHAR2);

##### Parameters

Table 70-8 DELETE_DAD_ATTRIBUTE Procedure Parameters

| Parameter   | Description                                             |
|:------------|:--------------------------------------------------------|
| `dad_name`  | The name of the DAD for which to delete a DAD attribute |
| `attr_name` | The name of the DAD attribute to delete                 |

##### Exceptions

Raises an error if DAD does not exist

#### 70.6.5 DELETE_GLOBAL_ATTRIBUTE Procedure

This procedure deletes a global attribute.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.DELETE_GLOBAL_ATTRIBUTE (
       attr_name     IN  VARCHAR2);

##### Parameters

Table 70-9 DELETE_GLOBAL_ATTRIBUTE Procedure Parameters

| Parameter   | Description                    |
|:------------|:-------------------------------|
| `attr_name` | The global attribute to delete |

#### 70.6.6 DROP_DAD Procedure

This procedure drops a DAD. All the virtual-path mappings of the DAD will be dropped also.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.DROP_DAD (
       dadname  IN  VARCHAR2);

##### Parameters

Table 70-10 DROP_DAD Procedure Parameters

| Parameter  | Description     |
|:-----------|:----------------|
| `dad_name` | The DAD to drop |

##### Exceptions

Raises an error if the DAD does not exist.

#### 70.6.7 GET_ALL_DAD_ATTRIBUTES Procedure

This procedure retrieves all the attributes of a DAD. The outputs are 2 correlated index-by tables of the name/value pairs.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_ALL_DAD_ATTRIBUTES (
       dad_name      IN          VARCHAR2,
       attr_names    OUT NOCOPY  VARCHAR2_TABLE,
       attr_values   OUT NOCOPY  VARCHAR2_TABLE);

##### Parameters

Table 70-11 GET_ALL_DAD_ATTRIBUTES Procedure Parameters

| Parameter     | Description          |
|:--------------|:---------------------|
| `dad_name`s   | The name of the DAD  |
| `attr_names`  | The attribute names  |
| `attr_values` | The attribute values |

##### Exceptions

Raises an error if DAD does not exist.

##### Usage Notes

If the DAD has no attributes set, then `attr_names` and `attr_values` will be set to empty arrays.

#### 70.6.8 GET_ALL_DAD_MAPPINGS Procedure

This procedure retrieves all the virtual paths to which the specified DAD is mapped.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_ALL_DAD_MAPPINGS (
       dad_name      IN          VARCHAR2,
       paths         OUT NOCOPY  VARCHAR2_TABLE);

##### Parameters

Table 70-12 GET_ALL_DAD_MAPPINGS Procedure Parameters

| Parameter   | Description                                    |
|:------------|:-----------------------------------------------|
| `dad_name`s | The name of the DAD                            |
| `paths`     | The virtual paths to which h the DAD is mapped |

##### Exceptions

Raises an error if DAD does not exist.

##### Usage Notes

If the DAD is not mapped to any virtual path, `paths` will be set to empty arrays.

#### 70.6.9 GET_ALL_GLOBAL_ATTRIBUTES Procedure

This procedure retrieves all global attributes and values. The outputs are 2 correlated index-by tables of the name/value pairs.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_ALL_GLOBAL_ATTRIBUTES (
       attr_names     OUT   NOCOPY  VARCHAR2_TABLE,
       attr_values    OUT   NOCOPY  VARCHAR2_TABLE);

##### Parameters

Table 70-13 GET_ALL_GLOBAL_ATTRIBUTES Procedure Parameters

| Parameter     | Description                         |
|:--------------|:------------------------------------|
| `attr_name`s  | The global attribute names          |
| `attr_values` | The values of the global attributes |

##### Usage Notes

If the gateway instance has no global attributes set, then `attr_names` and `attr_values` will be set to empty arrays.

#### 70.6.10 GET_DAD_ATTRIBUTE Function

This procedure retrieves the value of a DAD attribute.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_DAD_ATTRIBUTE (
       dad_name     IN  VARCHAR2,
       attr_name    IN  VARCHAR2)
     RETURN VARCHAR2;

##### Parameters

Table 70-14 GET_DAD_ATTRIBUTE Function Parameters

| Parameter   | Description                                          |
|:------------|:-----------------------------------------------------|
| `dad_name`  | The name of the DAD for which to delete an attribute |
| `attr_name` | The name of the attribute to delete                  |

##### Return values

Returns the DAD attribute value. Returns `NULL` if attribute is unknown or has not been set.

##### Exceptions

Raises an error if DAD does not exist.

#### 70.6.11 GET_DAD_LIST Procedure

This procedure retrieves a list of all DADs for an Embedded Gateway instance.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_DAD_LIST (
       dad_names     OUT NOCOPY  VARCHAR2_TABLE);

##### Parameters

Table 70-15 GET_DAD_LIST Procedure Parameters

| Parameter   | Description          |
|:------------|:---------------------|
| `dad_names` | The list of all DADs |

##### Usage Notes

If no DADs exist then `dad_names` will be set to an empty array.

#### 70.6.12 GET_GLOBAL_ATTRIBUTE Function

This function retrieves the value of a global attribute.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.GET_GLOBAL_ATTRIBUTE (
       attr_name  IN  VARCHAR2)
     RETURN VARCHAR2;

##### Parameters

Table 70-16 GET_GLOBAL_ATTRIBUTE Procedure Parameters

| Parameter   | Description                      |
|:------------|:---------------------------------|
| `attr_name` | The global attribute to retrieve |

##### Return Values

Returns the global attribute value. Returns `NULL` if attribute has not been set or is not a valid attribute.

#### 70.6.13 MAP_DAD Procedure

This procedure maps a DAD to the specified virtual path. If the virtual path exists already, the old virtual-path mapping will be overridden.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.MAP_DAD (
       dad_name  IN  VARCHAR2,
       path      IN  VARCHAR2);

##### Parameters

Table 70-17 MAP_DAD Procedure Parameters

| Parameter  | Description                |
|:-----------|:---------------------------|
| `dad_name` | The name of the DAD to map |
| `path`     | The virtual path to map    |

##### Exceptions

Raises and error if the DAD does not exist.

#### 70.6.14 SET_DAD_ATTRIBUTE Procedure

This procedure sets the value for a DAD.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.SET_DAD_ATTRIBUTE (
       dad_name    IN  VARCHAR2,
       attr_name   IN  VARCHAR2,   attr_value  IN  VARCHAR2);

##### Parameters

Table 70-18 SET_DAD_ATTRIBUTE Procedure Parameters

| Parameter    | Description                                        |
|:-------------|:---------------------------------------------------|
| `dad_name`   | The name of the DAD for which to set the attribute |
| `attr_name`  | The name of the attribute to set                   |
| `attr_value` | The attribute value to set                         |

Table 70-19 Mapping Between mod_plsql and Embedded PL/SQL Gateway DAD Attributes

| mod_plsql DAD Attribute          | Embedded PL/SQL Gateway DAD Attribute | Allows Multiple Occurr-ences | Legal Values                                                                                                        |
|:---------------------------------|:--------------------------------------|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------|
| `PlsqlAfterProcedure`            | `after-procedure`                     | No                           | String                                                                                                              |
| `PlsqlAlwaysDescribeProcedure`   | `always-describe-procedure`           | No                           | Enumeration of On, Off                                                                                              |
| `PlsqlAuthenticationMode`        | `authentication-mode`                 | No                           | Enumeration of Basic, SingleSignOn, GlobalOwa, CustomOwa, PerPackageOwa                                             |
| `PlsqlBeforeProcedure`           | `before-procedure`                    | No                           | String                                                                                                              |
| `PlsqlBindBucketLengths`         | `bind-bucket-lengths`                 | Yes                          | Unsigned integer                                                                                                    |
| `PlsqlBindBucketWidths`          | `bind-bucket-widths`                  | Yes                          | Unsigned integer                                                                                                    |
| `PlsqlCGIEnvironmentList`        | `cgi-environment-list`                | Yes                          | String                                                                                                              |
| `PlsqlCompatibilityMode`         | `compatibility-mode`                  | No                           | Unsigned integer                                                                                                    |
| `PlsqlDatabaseUsername`          | `database-usernam`e                   | No                           | String                                                                                                              |
| `PlsqlDefaultPage`               | `default-page`                        | No                           | String                                                                                                              |
| `PlsqlDocumentPath`              | `document-path`                       | No                           | String                                                                                                              |
| `PlsqlDocumentProcedure`         | `document-procedure`                  | No                           | String                                                                                                              |
| `PlsqlDocumentTablename`         | `document-table-name`                 | No                           | String                                                                                                              |
| `PlsqlErrorStyle`                | `error-style`                         | No                           | Enumeration of ApacheStyle, ModplsqlStyle, DebugStyle                                                               |
| `PlsqlExclusionList`             | `exclusion-list`                      | Yes                          | String                                                                                                              |
| `PlsqlFetchBufferSize`           | `fetch-buffer-size`                   | No                           | Unsigned integer                                                                                                    |
| `PlsqlInfoLogging`               | i`nfo-logging`                        | No                           | Enumeration of InfoDebug                                                                                            |
| `PlsqlOWADebugEnable`            | `owa-debug-enable`                    | No                           | Enumeration of On, Off                                                                                              |
| `PlsqlMaxRequestsPerSession`     | `max-requests-per-session`            | No                           | Unsigned integer                                                                                                    |
| `PlsqlNLSLanguage`               | `nls-language`                        | No                           | String                                                                                                              |
| `PlsqlPathAlias`                 | `path-alias`                          | No                           | String                                                                                                              |
| `PlsqlPathAliasProcedure`        | `path-alias-procedure`                | No                           | String                                                                                                              |
| `PlsqlRequestValidationFunction` | `request-validation-function`         | No                           | String                                                                                                              |
| `PlsqlSessionCookieName`         | `session-cookie-name`                 | No                           | String                                                                                                              |
| `PlsqlSessionStateManagement`    | `session-state-management`            | No                           | Enumeration of StatelessWithResetPackageState, StatelessWithFastRestPackageState, StatelessWithPreservePackageState |
| `PlsqlTransferMode`              | `transfer-mode`                       | No                           | Enumeration of Char, Raw                                                                                            |
| `PlsqlUploadAsLongRaw`           | `upload-as-long-raw`                  | No                           | String                                                                                                              |

##### Exceptions

Raises an error if DAD does not exist or the attribute is unknown.

##### Usage Notes

- If `attr_name` attribute has been set before, then the old value will be overwritten with the new `attr_value` argument.

- The embedded gateway assumes default values when the attributes are not set. The default values of the DAD attributes should be sufficient for most users of the embedded gateway. mod_plsql users should note the following

  - The `PlsqlDatabasePassword` attribute is not needed.

  - The `PlsqlDatabaseConnectString` attribute is not needed because the embedded gateway does not support logon to external databases.

##### Examples

    DBMS_EPG.SET_DAD_ATTRIBUTE('HR', 'default-page', 'HRApp.home');

#### 70.6.15 SET_GLOBAL_ATTRIBUTE Procedure

This procedure sets the value of a global attribute.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.SET_GLOBAL_ATTRIBUTE (
       attr_name    IN VARCHAR2,
       attr_value   IN VARCHAR2);

##### Parameters

Table 70-20 SET_GLOBAL_ATTRIBUTE Procedure Parameters

| Parameter    | Description                 |
|:-------------|:----------------------------|
| `attr_name`  | The global attribute to set |
| `attr_value` | The attribute value to set  |

Table 70-21 Mapping Between mod_plsql and Embedded PL/SQL Gateway Global Attributes

| mod_plsql Global Attribute | Embedded PL/SQL Gateway Global Attribute | Allows Multiple Occurr-ences | Legal Values     |
|:---------------------------|:-----------------------------------------|:-----------------------------|:-----------------|
| `PlsqlLogLevel`            | `log-level`                              | No                           | Unsigned integer |
| `PlsqlMaxParameters`       | `max-parameters`                         | No                           | Unsigned integer |

##### Usage Notes

- The attribute name is case sensitive. The value may or may not be case-sensitive depending on the attribute.

- If `attr_name` attribute has been set before, then the old value will be overwritten with the new `attr_value` argument.

##### Exceptions

Raises an error if the attribute is unknown.

##### Examples

    dbms_epg.set_global_attribute('max-parameters', '100');

#### 70.6.16 UNMAP_DAD Procedure

This procedure unmaps a DAD from the specified virtual path. If path is `NULL`, the procedure removes all virtual-path mappings for the DAD but keeps the DAD.

**See Also:**

Configuration Subprograms for other subprograms in this group

##### Syntax

    DBMS_EPG.UNMAP_DAD (
       dad_name IN VARCHAR2,
       path     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 70-22 UNMAP_DAD Procedure Parameters

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `dad_name` | The name of the DAD to unmap |
| `path`     | The virtual path to unmap    |

##### Usage Notes

Raises and error if the DAD does not exist.
