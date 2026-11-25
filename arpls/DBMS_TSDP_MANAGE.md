## 184  DBMS_TSDP_MANAGE

The `DBMS_TSDP_MANAGE` package provides an interface to import and manage sensitive columns and sensitive column types in the database, and is used in conjunction with the DBMS_TSDP_PROTECT package with regard to transparent sensitive data protection (TSDP) policies.

`DBMS_TSDP_MANAGE` is available with the Enterprise Edition only.

This chapter contains the following topics:

- Overview

- Security Model

- Summary of DBMS_TSDP_MANAGE Subprograms

**Related Topics**

- [DBMS_TSDP_PROTECT](DBMS_TSDP_PROTECT.md)

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md)

### 184.1 DBMS_TSDP_MANAGE Overview

The `DBMS_TSDP_MANAGE` package lets you manage sensitive columns and sensitive types in the Oracle database.

The identified sensitive columns are classified based on the sensitive types. By Using the [DBMS_TSDP_PROTECT](DBMS_TSDP_PROTECT.md) package to create a policy that protects data for a given class based on a column type rather than the data itself, you can then manage security for these types in a uniform fashion and modify the settings to accommodate changing compliance regulations.

You also can export the policies to other databases, when you perform a full export using Data Pump. You cannot export the policy itself, but an export of the database will include the TSDP policies.

### 184.2 DBMS_TSDP_MANAGE Security Model

All procedures are executed with invoker's rights. The `DBMS_TSDP_MANAGE` package is owned by `SYS`.

The `EXECUTE` privilege on this package should be granted as appropriate. Typically, an application database administrator should be granted the `EXECUTE` privilege for this package, while the [DBMS_TSDP_PROTECT](DBMS_TSDP_PROTECT.md) package would be governed by a security administrator.

### 184.3 Summary of DBMS_TSDP_MANAGE Subprograms

This table lists the `DBMS_TSDP_MANAGE` subprograms and briefly describes them.

Table 184-1 DBMS_TSDP_MANAGE Package Subprograms

| Subprogram                           | Description                                                                                                                                             |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| ADD_SENSITIVE_COLUMN Procedure       | Adds a column to the sensitive column list                                                                                                              |
| ADD_SENSITIVE_TYPE Procedure         | Creates and adds a sensitive column type to the list of sensitive column types in the database                                                          |
| ALTER_SENSITIVE_COLUMN Procedure     | Alters the sensitive type and/or the comment of a column in the sensitive column list.                                                                  |
| DROP_SENSITIVE_COLUMN Procedure      | Removes columns from the sensitive column list                                                                                                          |
| DROP_SENSITIVE_TYPE Procedure        | Drops a sensitive column type from the list sensitive column types in the database                                                                      |
| DROP_SENSITIVE_TYPE_SOURCE Procedure | Drops sensitive column types corresponding to a source from the list sensitive column types in the database                                             |
| IMPORT_DISCOVERY_RESULT Procedure    | Imports sensitive columns from an external source. This can be an Application Data Model (ADM) from an Oracle Enterprise Manager Cloud Control instance |
| IMPORT_SENSITIVE_TYPES Procedure     | Imports a list of sensitive column types from a source                                                                                                  |
| REMOVE_DISCOVERY_RESULT Procedure    | Removes sensitive columns corresponding to an Application Data Model (ADM) from an Oracle Enterprise Manager Cloud Control instance.                    |

#### 184.3.1 ADD_SENSITIVE_COLUMN Procedure

This procedure adds a column to the sensitive column list.

##### Syntax

    DBMS_TSDP_MANAGE.ADD_SENSITIVE_COLUMN (
       schema_name        IN VARCHAR2,
       table_name         IN VARCHAR2,
       column_name        IN VARCHAR2,
       sensitive_type     IN VARCHAR2,
       user_comment       IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 184-2 ADD_SENSITIVE_COLUMN Procedure Parameters

| Parameter        | Description                                 |
|:-----------------|:--------------------------------------------|
| `schema_name`    | Schema to which the column belongs          |
| `table_name`     | Table containing the column                 |
| `column_name`    | Sensitive column name                       |
| `sensitive_type` | Identifier of the sensitive column type     |
| `user_comment`   | User comment regarding the sensitive column |

##### Examples

Add a column `SAL` in `SCOTT.EMP`:

     DBMS_TSDP_MANAGE.ADD_SENSITIVE_COLUMN (
       schema_name        => 'SCOTT',
       table_name         => 'EMP',
       column_name        => 'SAL',
       sensitive_type     => 'SALARY_TYPE',
       user_comment       => 'Salary column');

#### 184.3.2 ALTER_SENSITIVE_COLUMN Procedure

This procedure alters the Sensitive Type and/or the Comment of a Column in the sensitive column list.

##### Syntax

    DBMS_TSDP_MANAGE.ALTER_SENSITIVE_COLUMN (
       schema_name        IN VARCHAR2,
       table_name         IN VARCAHR2,
       column_name        IN VARCAHR2,
       sensitive_type     IN VARCAHR2,
       user_comment       IN VARCAHR2 DEFAULT NULL);

##### Parameters

Table 184-3 ALTER_SENSITIVE_COLUMN Procedure Parameters

| Parameter        | Description                                 |
|:-----------------|:--------------------------------------------|
| `schema_name`    | Schema to which the column belongs          |
| `table_name`     | Table containing the column                 |
| `column_name`    | Sensitive column name                       |
| `sensitive_type` | Identifier of the sensitive column type     |
| `user_comment`   | User comment regarding the sensitive column |

##### Examples

Alter the column `SAL` in `SCOTT.EMP` that is listed in the sensitive column list:

     DBMS_TSDP_MANAGE.ALTER_SENSITIVE_COLUMN (
       schema_name        => 'SCOTT',
       table_name         => 'EMP',
       column_name        => 'SAL',
       sensitive_type     => 'FINANCE_Type',
       user_comment       => 'Finance Type. Earlier categorized as Salary Type');

#### 184.3.3 ADD_SENSITIVE_TYPE Procedure

This procedure creates and adds a sensitive column type to the list sensitive column types in the database.

##### Syntax

    DBMS_TSDP_MANAGE.ADD_SENSITIVE_TYPE (
       sensitive_type     IN  VARCHAR2,
       user_comment       IN  VARCAHR2 DEFAULT NULL);

##### Parameters

Table 184-4 ADD_SENSITIVE_TYPE Procedure Parameters

| Parameter        | Description                                 |
|:-----------------|:--------------------------------------------|
| `sensitive_type` | Name of the sensitive column type           |
| `user_comment`   | User comment regarding the sensitive column |

##### Examples

Add a sensitive column type called `SALARY_TYPE` that is intended to be associated with columns containing salary data:

     DBMS_TSDP_MANAGE.ADD_SENSITIVE_TYPE (
       sensitive_type     => 'SALARY_TYPE',
       user_comment       => 'Salary data');

#### 184.3.4 DROP_SENSITIVE_COLUMN Procedure

This procedure removes columns from the sensitive column list.

##### Syntax

    DBMS_TSDP_MANAGE.DROP_SENSITIVE_COLUMN (
       schema_name        IN VARCHAR2 DEFAULT '%',
       table_name         IN VARCAHR2 DEFAULT '%',
       column_name        IN VARCAHR2 DEFAULT '%');

##### Parameters

Table 184-5 DROP_SENSITIVE_COLUMN Procedure Parameters

| Parameter     | Description                        |
|:--------------|:-----------------------------------|
| `schema_name` | Schema to which the column belongs |
| `table_name`  | Table containing the column        |
| `column_name` | Sensitive column name              |

##### Examples

Remove column `SAL` in `SCOTT.EMP` from the sensitive column list:

     DBMS_TSDP_MANAGE.DROP_SENSITIVE_COLUMN (
       schema_name        => 'SCOTT',
       table_name         => 'EMP',
       column_name        => 'SAL');

#### 184.3.5 DROP_SENSITIVE_TYPE Procedure

This procedure drops a sensitive column type from the list sensitive column types in the database.

##### Syntax

    DBMS_TSDP_MANAGE.DROP_SENSITIVE_TYPE (
       sensitive_type     IN VARCHAR2);

##### Parameters

Table 184-6 DROP_SENSITIVE_TYPE Procedure Parameters

| Parameter        | Description                                     |
|:-----------------|:------------------------------------------------|
| `sensitive_type` | Name of the sensitive column type to be dropped |

##### Examples

To drop `SALARY_TYPE`:

     DBMS_TSDP_MANAGE.DROP_SENSITIVE_TYPE (
       sensitive_type     => 'SALARY_TYPE');

#### 184.3.6 DROP_SENSITIVE_TYPE_SOURCE Procedure

This procedure drops sensitive column types corresponding to a source from the list sensitive column types in the database.

##### Syntax

    DBMS_TSDP_MANAGE.DROP_SENSITIVE_TYPE_SOURCE (
       source      IN VARCHAR2);

##### Parameters

Table 184-7 DROP_SENSITIVE_TYPE_SOURCE Procedure Parameters

| Parameter | Description        |
|:----------|:-------------------|
| `source`  | Name of the source |

##### Examples

To drop all sensitive column types corresponding to an Application Data Model (ADM) from an Oracle Enterprise Manager Cloud Control instance, `ADM_DEMO`:

     DBMS_TSDP_MANAGE.DROP_SENSITIVE_TYPE_SOURCE (
        source      =>  'ADM_DEMO');

#### 184.3.7 IMPORT_DISCOVERY_RESULT Procedure

This procedure can be used to import sensitive columns, along with the associated sensitive types, from an external source. The external source can be an Application Data Model (ADM) instance from Oracle Enterprise Manager Cloud Control.

##### Syntax

    DBMS_TSDP_MANAGE.IMPORT_DISCOVERY_RESULT (
      discovery_result         IN  CLOB,
      discovery_source         IN  VARCHAR2,
      force                    IN  FORCE DEFAULT FALSE);

    DBMS_TSDP_MANAGE.IMPORT_DISCOVERY_RESULT (
      discovery_result         IN  XMLTYPE,
      discovery_source         IN  VARCHAR2,
      force                    IN  FORCE DEFAULT FALSE);

##### Parameters

Table 184-8 IMPORT_DISCOVERY_RESULT Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `discovery_result` | List of sensitive columns, along with the optional list of (the definitions of) the sensitive column types in XML format (possibly as a `CLOB`).                                                                                                                                                                                                                                                                                                                                             |
| `discovery_source` | Source of the import. The discovery_sourcename identifies the list of imported sensitive columns. In case of ADM, this should be the ADM name.                                                                                                                                                                                                                                                                                                                                               |
| `force`            | Specifies if the discovery result should be imported or not when the discovery result contains columns sensitive columns that are already identified as sensitive by another source.<br>• `FALSE` (default) - the discovery result will not be imported in case of conflicting columns. None of the columns and the sensitive types are imported.<br>• `TRUE` - the discovery result is imported and the attributes of the conflicting columns is set based on the incoming discovery result |

##### Examples

Import the list of sensitive columns of ADM instance, `ADM_Demo`:

     DBMS_TSDP_MANAGE.IMPORT_DISCOVERY_RESULT (
       discovery_results        =>  xml_adm_result,
       discovery_source         => 'ADM_Demo');

#### 184.3.8 IMPORT_SENSITIVE_TYPES Procedure

This procedure imports a list of sensitive column types from a source.

##### Syntax

    DBMS_TSDP_MANAGE.IMPORT_SENSITIVE_TYPES (
      sensitive_types        IN CLOB,
      source                 IN VARCHAR2);

    DBMS_TSDP_MANAGE.IMPORT_SENSITIVE_TYPES (
      sensitive_types        IN XMLTYPE,
      source                 IN VARCHAR2);

##### Parameters

Table 184-9 IMPORT_SENSITIVE_TYPES Procedure Parameters

| Parameter         | Description                                                                                                                                                                                                             |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sensitive_types` | List of sensitive column types in XML Format (possibly as a `CLOB`)                                                                                                                                                     |
| `source`          | Source of the import. The source identifies the list of imported sensitive column types. In case of Application Data Model (ADM) from an Oracle Enterprise Manager Cloud Control instance, this should be the ADM name. |

##### Examples

Import the list of sensitive column types of ADM instance, `ADM_Demo`:

     DBMS_TSDP_MANAGE.IMPORT_SENSITIVE_TYPES (
       sensitive_types        =>  xml_adm_result,
       source                 => 'ADM_Demo');

#### 184.3.9 REMOVE_DISCOVERY_RESULT Procedure

This procedure removes sensitive columns corresponding to an Application Data Model (ADM) from an Oracle Enterprise Manager Cloud Control instance.

##### Syntax

    DBMS_TSDP_MANAGE.REMOVE_DISCOVERY_RESULT (
      discovery_source     IN  VARCHAR2);

##### Parameters

Table 184-10 REMOVE_DISCOVERY_RESULT Procedure Parameters

| Parameter          | Description                                                                                                |
|:-------------------|:-----------------------------------------------------------------------------------------------------------|
| `discovery_source` | Source of the import. In case of ADM, this should be the ADM name, the results of which is to be removed.  |

##### Examples

Remove the sensitive columns corresponding to ADM instance, `ADM_Demo`:

     DBMS_TSDP_MANAGE.REMOVE_DISCOVERY_RESULT (
       discovery_source    => 'ADM_Demo');
