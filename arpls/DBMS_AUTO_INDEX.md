## 31 DBMS_AUTO_INDEX

The `DBMS_AUTO_INDEX` package provides the interface for managing auto indexes in an Oracle database.

This chapter contains the following topics:

- DBMS_AUTO_INDEX Overview

- Summary of DBMS_AUTO_INDEX Subprograms

### 31.1 DBMS_AUTO_INDEX Overview

The `DBMS_AUTO_INDEX` package is the interface for configuring auto indexes and generating reports of auto indexing operations in an Oracle database.

### 31.2 Summary of DBMS_AUTO_INDEX Subprograms

This table lists the `DBMS_AUTO_INDEX` package subprograms and briefly describes them.

Table 31-1 DBMS_AUTO_INDEX Package Subprograms

| Procedure                        | Description                                                                                                                   |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| CONFIGURE Procedure              | Configures settings related to automatic indexing.                                                                            |
| DROP_AUTO_INDEXES Procedure      | This procedure can be used to manually drop the automatically created indexes that overrides the retention parameter setting. |
| DROP_SECONDARY_INDEXES Procedure | Deletes all the indexes, except the ones used for constraints, from a schema or a table.                                      |
| REPORT_ACTIVITY Function         | Returns a report of the automatic indexing operations executed during a specific period in a database.                        |
| REPORT_LAST_ACTIVITY Function    | Returns a report of the last automatic indexing operation executed in a database.                                             |

#### 31.2.1 CONFIGURE Procedure

This procedure configures settings related to automatic indexing.

##### Syntax

    DBMS_AUTO_INDEX.CONFIGURE (
       parameter_name         IN VARCHAR2,
       parameter_value        IN VARCHAR2,
       allow                  IN BOOLEAN  DEFAULT TRUE);

##### Parameters

Table 31-2 CONFIGURE Procedure Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `parameter_name`  | Automatic indexing configuration setting. It can have one of the following values:<br>• `AUTO_INDEX_MODE`: Modes of operation of auto indexes. It can have one of the following values:<br>• `IMPLEMENT`: In this mode, new auto indexes are created as visible indexes and any existing invisible auto indexes are also set to visible indexes. In this mode, auto indexes are available to be used in SQL statements.<br>• `REPORT ONLY`: In this mode, new auto indexes are created as invisible indexes and are not available to be used in SQL statements.<br>• `OFF`: Setting the mode to `OFF` prevents new auto indexes from being considered and created. However, it does not disable existing auto indexes.<br>• `AUTO_INDEX_SCHEMA`: Schemas to include or exclude from using auto indexes. Its value is case-sensitive and can include wildcards. Its behavior is controlled by the `allow` parameter.<br>• The automatic indexing process manages two schema lists – the inclusion list and the exclusion list. The inclusion list contains the schemas that can use auto indexes. The exclusion list contains the schemas that cannot use auto indexes. Initially, both these lists are empty and all the schemas in the database can use auto indexes when automatic indexing is enabled for a database.<br>• If the inclusion list contains at least one schema, then only the schemas listed in the inclusion list can use auto indexes.<br>• If the inclusion list is empty and the exclusion list contains at least one schema, then all the schemas can use auto indexes, except the schemas listed in the exclusion list.<br>• If both the lists (the inclusion list and the exclusion list) contain at least one schema, then all the schemas can use auto indexes, except the schemas listed in the exclusion list.<br>• `AUTO_INDEX_RETENTION_FOR_AUTO`: Number of days for which the unused auto indexes are retained in the database, after which they are deleted. Default value is 373 days.<br>• `AUTO_INDEX_RETENTION_FOR_MANUAL`: Number of days for which the unused manually created indexes (non-auto indexes) are retained in the database, after which they are deleted. When it is set to `NULL`, the manually created indexes are not deleted by the automatic indexing process. Default value is `NULL`.<br>• `AUTO_INDEX_REPORT_RETENTION`: Number of days for which automatic indexing logs are retained in the database before they are deleted. As automatic indexing report is generated based on these logs, automatic indexing report cannot be generated for a period beyond the value specified for `AUTO_INDEX_REPORT_RETENTION`. Default value is 373 days.<br>• `AUTO_INDEX_DEFAULT_TABLESPACE`: Tablespace to use to store auto indexes. Default is `NULL`, which means the default permanent tablespace specified during the database creation is used to store auto indexes.<br>• `AUTO_INDEX_SPACE_BUDGET`: Percentage of tablespace size to use for auto indexes. This configuration setting can be used only when the default tablespace specified during the database creation is used for storing auto indexes.<br>• `AUTO_INDEX_COMPRESSION`:<br>• Values to enable and disable advanced index compression for auto indexes. The supported values are:<br>• `ON`: to enable advanced index compression for auto indexes<br>• `OFF`: to disable advanced index compression for auto indexes<br>• The default value is `OFF`. |
| `parameter_value` | Value for the configuration setting specified in `parameter_name`.<br>When it is set to `NULL`, the configuration setting is assigned the default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `allow`           | This parameter is applicable only for the `AUTO_INDEX_SCHEMA` configuration setting and it can have one of the following values:<br>• `TRUE`: Add the specified schema to the inclusion list.<br>• `FALSE`: Add the specified schema to the exclusion list.<br>• `NULL`: Remove the specified schema from the list to which it is currently added.<br>Refer to the description of the `AUTO_INDEX_SCHEMA` configuration setting for more information about the inclusion list and the exclusion list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

##### Examples

These examples are based on the assumption that the inclusion list and the exclusion list are initially empty.

The following example adds the `SH` and `HR` schemas to the exclusion list, so that only the `SH` and `HR` schemas cannot use auto indexes.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_SCHEMA',
             parameter_value => 'SH',
             allow           => FALSE);

        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_SCHEMA',
             parameter_value => 'HR',
             allow           => FALSE);
    end;

The following example removes the `HR` schema from the exclusion list, so that it can also use auto indexes. Now, only the `SH` schema cannot use auto indexes, because it is the only schema added to the exclusion list.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_SCHEMA',
             parameter_value => 'HR',
             allow           => NULL);
    end;

The following example removes all the schemas from the exclusion list, so that all the schemas can use auto indexes.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_SCHEMA',
             parameter_value => NULL,
             allow           => TRUE);
    end;

The following example adds the `HR` schema to the inclusion list, so that only the `HR` schema can use auto indexes.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_SCHEMA',
             parameter_value => 'HR',
             allow           => TRUE);
    end;

The following example sets the retention period for auto indexes to 90 days.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_RETENTION_FOR_AUTO',
             parameter_value => '90');
    end;

The following example sets the retention period for auto indexes to the default value of 373 days.

    begin
        dbms_auto_index.configure(
             parameter_name  => 'AUTO_INDEX_RETENTION_FOR_AUTO',
             parameter_value => NULL);
    end;

#### 31.2.2 DROP_AUTO_INDEXES Procedure

This procedure can be used to manually drop the automatically created indexes that overrides the retention parameter setting.

##### Syntax

    DBMS_AUTO_INDEX.DROP_AUTO_INDEXES (
       owner           IN  VARCHAR2 DEFAULT NULL,
       index_name      IN  VARCHAR2 DEFAULT NULL,
       allow_recreate  IN  BOOLEAN DEFAULT FALSE);

##### Parameters

Table 31-3 DROP_AUTO_INDEXES Procedure Parameters

| Parameter        | Description                                                                            |
|:-----------------|:---------------------------------------------------------------------------------------|
| `owner`          | The name of the index owner.                                                           |
| `index_name`     | The name of the index.                                                                 |
| `allow_recreate` | Set this parameter to allow or disallow automatic creation of the dropped index again. |

##### Examples

Drop a single index and allow recreate:

    exec dbms_auto_index.drop_auto_indexes('SH','"SYS_AI_612ud3j5ngf0c"',TRUE);

Drop all indexes owned by SH and allow recreate:

    exec dbms_auto_index.drop_auto_indexes('SH',NULL,TRUE);

Drop all indexes owned by HR, disallowing recreate and then change the recreation status back to allow:

    exec dbms_auto_index.drop_auto_indexes('HR',NULL);
    exec dbms_auto_index.drop_auto_indexes('HR', NULL, TRUE);

##### Usage Notes

- If the values of the parameters owner and index_name are explicitly set to `NULL`, all auto indexes which the user has privileges on will be dropped.
- If owner is explicitly specified and `index_name` is set to `NULL`, all auto indexes within the given schema will be dropped. The dropped indexes are not recreated automatically by the system by default. Set `allow_recreate` parameter to `TRUE` to change this behavior.
- This procedure updates the `allow_recreate` status associated with the dropped indexes from `FALSE` to `TRUE` and vice-versa.

#### 31.2.3 DROP_SECONDARY_INDEXES Procedure

This procedure deletes all the indexes, except the ones used for constraints, from a schema or a table.

##### Syntax

    DBMS_AUTO_INDEX.DROP_SECONDARY_INDEXES (
       ownname    IN  VARCHAR2 DEFAULT NULL,
       tabname    IN  VARCHAR2 DEFAULT NULL);

##### Parameters

Table 31-4 DROP_SECONDARY_INDEXES Procedure Parameters

| Parameter | Description                                                                                                                             |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `ownname` | (Optional) Name of the schema from which all the indexes need to be deleted.<br>Note: The indexes used for constraints are not deleted. |
| `tabname` | (Optional) Name of the table from which all the indexes need to be deleted.<br>Note: The indexes used for constraints are not deleted.  |

##### Examples

The following example deletes all the indexes, except the ones used for constraints, from the `SH` schema.

    begin
        dbms_auto_index.drop_secondary_indexes('SH');
    end;

The following example deletes all the indexes, except the ones used for constraints, from the `EMP` table in the `HR` schema.

    begin
        dbms_auto_index.drop_secondary_indexes('HR', 'EMP');
    end;

The following example deletes all the indexes, except the ones used for constraints, for which the user has the delete privileges from all the schemas in a database.

    begin
        dbms_auto_index.drop_secondary_indexes;
    end;

#### 31.2.4 REPORT_ACTIVITY Function

This function returns a report of the automatic indexing operations executed during a specific period in a database.

##### Syntax

    DBMS_AUTO_INDEX.REPORT_ACTIVITY (
       activity_start  IN  TIMESTAMP WITH TIME ZONE DEFAULT SYSTIMESTAMP - 1,
       activity_end    IN  TIMESTAMP WITH TIME ZONE DEFAULT SYSTIMESTAMP,
       type            IN  VARCHAR2 DEFAULT 'TEXT',
       section         IN  VARCHAR2 DEFAULT 'ALL',
       level           IN  VARCHAR2 DEFAULT 'TYPICAL')
    RETURN CLOB;

##### Parameters

Table 31-5 REPORT_ACTIVITY Function Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `activity_start` | Time starting from which the executed automatic indexing operations are considered for the report. If `NULL` is specified, the last executed automatic indexing operation is considered for the report. If no value is specified for this parameter, then the current time minus one day (24 hours) is considered at the start time.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `activity_end`   | Time till which the executed automatic indexing operations are considered for the report. If no value is specified, then the current time is considered as the end time.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `type`           | Format of the report. It can have one of the following values:<br>• `TEXT`<br>• `HTML`<br>• `XML`<br>The default value is `TEXT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `section`        | Sections to include in the report. It can have a combination of the following values:<br>• `SUMMARY`: Include only the summary details section in the report.<br>• `INDEX_DETAILS`: Include only the auto index details section in the report.<br>• `VERIFICATION_DETAILS`: Include only the auto index verification details section in the report.<br>• `ERRORS`: Include only the error details section in the report.<br>• `ALL`: Include all the sections (summary details, auto index details, auto index verification details, and error details) in the report. This is the default value.<br>A combination of these values can be specified using the `+` or `-` operators as shown in the following examples:<br>• `SUMMARY +INDEX_DETAILS +ERRORS`: Include summary details, auto index details, and error details sections in the report.<br>• `ALL -ERRORS`: Include all the sections in the report, except the error details section. |
| `level`          | Level of automatic indexing information to include in the report. It can have one of the following values:<br>• `BASIC`: Include basic automatic indexing information in the report.<br>• `TYPICAL`: Include typical automatic indexing information in the report. This is the default value.<br>• `ALL`: Include all the automatic indexing information in the report.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

##### Return Value

A report of the automatic indexing operations executed during the specified period in a database.

##### Examples

The following example generates a typical report of the automatic indexing operations executed in the last 24 hours. The report is generated in the text format and contains all the sections (summary details, auto index details, auto index verification details, and error details).

    declare
      report clob := null;
    begin
      report := dbms_auto_index.report_activity();
    end;

#### 31.2.5 REPORT_LAST_ACTIVITY Function

This function returns a report of the last automatic indexing operation executed in a database.

##### Syntax

    DBMS_AUTO_INDEX.REPORT_LAST_ACTIVITY (
       type            IN  VARCHAR2 DEFAULT 'TEXT',
       section         IN  VARCHAR2 DEFAULT 'ALL',
       level           IN  VARCHAR2 DEFAULT 'TYPICAL')
    RETURN CLOB;

##### Parameters

Table 31-6 REPORT_LAST_ACTIVITY Function Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type`    | Format of the report. It can have one of the following values:<br>• `TEXT`<br>• `HTML`<br>• `XML`<br>The default value is `TEXT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `section` | Sections to include in the report. It can have a combination of the following values:<br>• `SUMMARY`: Include only the summary details section in the report.<br>• `INDEX_DETAILS`: Include only the auto index details section in the report.<br>• `VERIFICATION_DETAILS`: Include only the auto index verification details section in the report.<br>• `ERRORS`: Include only the error details section in the report.<br>• `ALL`: Include all the sections (summary details, auto index details, auto index verification details, and error details) in the report. This is the default value.<br>A combination of these values can be specified using the `+` or `-` operators as shown in the following examples:<br>• `SUMMARY +INDEX_DETAILS +ERRORS`: Include summary details, auto index details, and error details sections in the report.<br>• `ALL -ERRORS`: Include all the sections in the report, except the error details section. |
| `level`   | Level of automatic indexing information to include in the report. It can have one of the following values:<br>• `BASIC`: Include basic automatic indexing information in the report.<br>• `TYPICAL`: Include typical automatic indexing information in the report. This is the default value.<br>• `ALL`: Include all the automatic indexing information in the report.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

##### Return Value

A report of the last automatic indexing operation executed in a database.

##### Examples

The following example generates a typical report of the last automatic indexing operation executed in a database. The report is generated in the text format and contains all the sections (summary details, auto index details, auto index verification details, and error details).

    declare
      report clob := null;
    begin
      report := dbms_auto_index.report_last_activity();
    end;
