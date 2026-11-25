## G  Oracle Text Views

This appendix lists all of the views provided by Oracle Text. The system provides the following views:

- CTX_ALEXER_DICTS

- CTX_AUTO_OPTIMIZE_INDEXES

- CTX_AUTO_OPTIMIZE_STATUS

- CTX_CLASSES

- CTX_FILTER_BY_COLUMNS

- CTX_FILTER_CACHE_STATISTICS

- CTX_INDEXES

- CTX_INDEX_ERRORS

- CTX_INDEX_OBJECTS

- CTX_INDEX_PARTITIONS

- CTX_INDEX_SETS

- CTX_INDEX_SET_INDEXES

- CTX_INDEX_SUB_LEXERS

- CTX_INDEX_SUB_LEXER_VALUES

- CTX_INDEX_VALUES

- CTX_OBJECTS

- CTX_OBJECT_ATTRIBUTES

- CTX_OBJECT_ATTRIBUTE_LOV

- CTX_ORDER_BY_COLUMNS

- CTX_PARAMETERS

- CTX_PENDING

- CTX_PREFERENCES

- CTX_PREFERENCE_VALUES

- CTX_SECTIONS

- CTX_SECTION_GROUPS

- CTX_SQES

- CTX_STOPLISTS

- CTX_STOPWORDS

- CTX_SUB_LEXERS

- CTX_THESAURI

- CTX_THES_PHRASES

- CTX_TRACE_VALUES

- CTX_USER_ALEXER_DICTS

- CTX_USER_AUTO_OPTIMIZE_INDEXES

- CTX_USER_EXTRACT_POLICIES

- CTX_USER_EXTRACT_POLICY_VALUES

- CTX_USER_EXTRACT_RULES

- CTX_USER_EXTRACT_STOP_ENTITIES

- CTX_USER\_ FILTER_BY_COLUMNS

- CTX_USER_INDEXES

- CTX_USER_INDEX_ERRORS

- CTX_USER_INDEX_OBJECTS

- CTX_USER_INDEX_PARTITIONS

- CTX_USER_INDEX_SETS

- CTX_USER_INDEX_SET_INDEXES

- CTX_USER_INDEX_SUB_LEXERS

- CTX_USER_INDEX_SUB_LEXER_VALS

- CTX_USER_INDEX_VALUES

- CTX_USER_ORDER_BY_COLUMNS

- CTX_USER_PENDING

- CTX_USER_PREFERENCES

- CTX_USER_PREFERENCE_VALUES

- CTX_USER_SECTIONS

- CTX_USER_SECTION_GROUPS

- CTX_USER_SQES

- CTX_USER_STOPLISTS

- CTX_USER_STOPWORDS

- CTX_USER_SUB_LEXERS

- CTX_USER_THESAURI

- CTX_USER_THES_PHRASES

- CTX_VERSION

### G.1 CTX_ALEXER_DICTS

This view displays all dictionaries created by any user. This view can be queried by CTXSYS.

| Column Name | Type           | Description                  |
|:------------|:---------------|:-----------------------------|
| `ALD_OWNER` | `VARCHAR2(30)` | Name of the dictionary owner |
| `ALD_NAME`  | `VARCHAR2(30)` | Name of the dictionary       |
| `ALD_LANG`  | `VARCHAR2(30)` | Language of the dictionary   |

### G.2 CTX_AUTO_OPTIMIZE_INDEXES

This view displays all the indexes that are registered for auto optimization. It can be queried by `CTXSYS`.

| Column Name          | Type           | Description    |
|:---------------------|:---------------|:---------------|
| `AOI_INDEX_OWNER`    | `VARCHAR2(30)` | Index owner    |
| `AOI_INDEX_NAME`     | `VARCHAR2(30)` | Index name     |
| `AOI_PARTITION_NAME` | `VARCHAR2(30)` | Partition name |

### G.3 CTX_AUTO_OPTIMIZE_STATUS

This view displays the status of auto optimization jobs. It can be queried by `CTXSYS`.

| Column Name     | Type                         | Description                                     |
|:----------------|:-----------------------------|:------------------------------------------------|
| `AOS_TIMESTAMP` | `TIMESTAMP(6) WITH TIMEZONE` | Time at which the auto optimization job started |
| `AOS_STATUS`    | `VARCHAR2(30)`               | Status of the auto optimization job             |
| `AOS_ERROR`     | `VARCHAR2(4000)`             | Errors raised by the auto optimization job      |

### G.4 CTX_CLASSES

This view displays all the preference categories registered in the Text data dictionary. It can be queried by any user.

| Column Name       | Type           | Description       |
|:------------------|:---------------|:------------------|
| `CLA_NAME`        | `VARCHAR2(30)` | Class name        |
| `CLA_DESCRIPTION` | `VARCHAR2(80)` | Class description |

### G.5 CTX_FILTER_BY_COLUMNS

This view displays all `FILTER` `BY` columns registered in the Text data dictionary. It can be queried by any user.

| Column Name        | Type            | Description      |
|:-------------------|:----------------|:-----------------|
| `FBC_INDEX_OWNER`  | `VARCHAR2(30)`  | Index owner name |
| `FBC_INDEX_NAME`   | `VARCHAR2(30)`  | Index name       |
| `FBC_TABLE_OWNER`  | `VARCHAR2(30)`  | Table owner name |
| `FBC_TABLE_NAME`   | `VARCHAR2(30)`  | Table name       |
| `FBC_COLUMN_NAME`  | `VARCHAR2(256)` | Column name      |
| `FBC_COLUMN_TYPE`  | `VARCHAR2(30)`  | Column type      |
| `FBC_SECTION_TYPE` | `VARCHAR2(30)`  | Section type     |
| `FBC_SECTION_NAME` | `VARCHAR2(30)`  | Section name     |
| `FBC_SECTION_ID`   | `NUMBER`        | Section ID       |

### G.6 CTX_FILTER_CACHE_STATISTICS

This view displays various statistics related to the query filter cache. This view can be queried by all users and it displays the statistics for all indexes.

| Column Name          | Type           | Description                                                                  |
|:---------------------|:---------------|:-----------------------------------------------------------------------------|
| `FCS_INDEX_OWNER`    | `VARCHAR2(30)` | Index owner name                                                             |
| `FCS_INDEX_NAME`     | `VARCHAR2(30)` | Index name                                                                   |
| `FCS_PARTITION_NAME` | `VARCHAR2(30)` | Index partition name                                                         |
| `FCS_SIZE`           | `NUMBER`       | Current size of the filter cache in bytes                                    |
| `FCS_ENTRIES`        | `NUMBER`       | Number of queries for which the query results are cached in the filter cache |
| `FCS_REQUESTS`       | `NUMBER`       | Number of query requests to the filter cache                                 |
| `FCS_HITS`           | `NUMBER`       | Number of query requests for which matches were found in the filter cache    |

### G.7 CTX_INDEXES

This view displays all indexes that are registered in the Text data dictionary for the current user. It can be queried by `CTXSYS`.

| Column Name            | Type             | Description                                                                                                                         |
|:-----------------------|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------|
| `IDX_CHARSET_COLUMN`   | `VARCHAR2(256)`  | Name of the charset column in base table                                                                                            |
| `IDX_DOCID_COUNT`      | `NUMBER`         | Number of documents indexed                                                                                                         |
| `IDX_FORMAT_COLUMNS`   | `VARCHAR2(256)`  | Name of the format column in base table                                                                                             |
| `IDX_ID`               | `NUMBER`         | Internal index ID                                                                                                                   |
| `IDX_KEY_NAME`         | `VARCHAR2(256)`  | Primary key column(s)                                                                                                               |
| `IDX_LANGUAGE_COLUMN`  | `VARCHAR2(256)`  | Name of the language column in base table                                                                                           |
| `IDX_NAME`             | `VARCHAR2(30)`   | Name of index                                                                                                                       |
| `IDX_OWNER`            | `VARCHAR2(30)`   | Owner of index                                                                                                                      |
| `IDX_STATUS`           | `VARCHAR2(12)`   | Status                                                                                                                              |
| `IDX_SYNC_INTERVAL`    | `VARCHAR2(2000)` | Interval string required by scheduler job. Only meaningful for `AUTOMATIC` sync. Always null for `MANUAL` and `ON` `COMMIT` sync.   |
| `IDX_SYNC_JOBNAME`     | `VARCHAR2(50)`   | Scheduler job name for automatic sync. Only meaningful for `AUTOMATIC` sync and always null for other types of sync.                |
| `IDX_SYNC_MEMORY`      | `VARCHAR2(100)`  | Sync memory size. Only meaningful for `ON` `COMMIT` and `AUTOMATIC` types of sync. For `MANUAL` sync, this is always null.          |
| `IDX_SYNC_PARA_DEGREE` | `NUMBER`         | Degree of parallelism for sync. Only meaningful for the `AUTOMATIC` type of sync; always null for `MANUAL` and `ON` `COMMIT` syncs. |
| `IDX_SYNC_TYPE`        | `VARCHAR2(20)`   | Type of synching: `MANUAL`, `AUTOMATIC`, or `ON` `COMMIT`                                                                           |
| `IDX_TABLE`            | `VARCHAR2(30)`   | Table name                                                                                                                          |
| `IDX_TABLE_OWNER`      | `VARCHAR2(30)`   | Owner of table                                                                                                                      |
| `IDX_TEXT_NAME`        | `VARCHAR2(30)`   | Text column name                                                                                                                    |
| `IDX_TYPE`             | `VARCHAR2(7)`    | Type of index: `CONTEXT`, `CTXCAT`, or `CTXRULE`                                                                                    |

### G.8 CTX_INDEX_ERRORS

This view displays the DML errors and is queryable by `CTXSYS`.

| Column Name       | Type             | Description                                                                           |
|:------------------|:-----------------|:--------------------------------------------------------------------------------------|
| `ERR_INDEX_OWNER` | `VARCHAR2(30)`   | Index owner                                                                           |
| `ERR_INDEX_NAME`  | `VARCHAR2(30)`   | Name of index                                                                         |
| `ERR_TIMESTAMP`   | `DATE`           | Time of error                                                                         |
| `ERR_TEXTKEY`     | `VARCHAR2(18)`   | ROWID of errored document or name of errored operation (for example, `ALTER` `INDEX`) |
| `ERR_TEXT`        | `VARCHAR2(4000)` | Error text                                                                            |

### G.9 CTX_INDEX_OBJECTS

This view displays the objects that are used for each class in the index. It can be queried by `CTXSYS`.

| Column Name       | Type           | Description |
|:------------------|:---------------|:------------|
| `IXO_INDEX_OWNER` | `VARCHAR2(30)` | Index owner |
| `IXO_INDEX_NAME`  | `VARCHAR2(30)` | Index name  |
| `IXO_CLASS`       | `VARCHAR2(30)` | Class name  |
| `IXO_OBJECT`      | `VARCHAR2(30)` | Object name |

### G.10 CTX_INDEX_PARTITIONS

This view displays all index partitions. It can be queried by `CTXSYS`.

| Column Name                | Type           | Description                                               |
|:---------------------------|:---------------|:----------------------------------------------------------|
| `IXP_ID`                   | `NUMBER(38)`   | Index partition ID                                        |
| `IXP_INDEX_OWNER`          | `VARCHAR2(30)` | Index owner                                               |
| `IXP_INDEX_NAME`           | `VARCHAR2(30)` | Index name                                                |
| `IXP_INDEX_PARTITION_NAME` | `VARCHAR2(30)` | Index partition name                                      |
| `IXP_SYNC_TYPE`            | `VARCHAR2(20)` | Type of synching: `MANUAL`, `AUTOMATIC`, or `ON` `COMMIT` |
| `IXP_TABLE_OWNER`          | `VARCHAR2(30)` | Table owner                                               |
| `IXP_TABLE_NAME`           | `VARCHAR2(30)` | Table name                                                |
| `IXP_TABLE_PARTITION_NAME` | `VARCHAR2(30)` | Table partition name                                      |
| `IXP_DOCID_COUNT`          | `NUMBER(38)`   | Number of documents associated with the partition         |
| `IXP_STATUS`               | `VARCHAR2(12)` | Partition status                                          |

### G.11 CTX_INDEX_SETS

This view displays all index set names. It can be queried by any user.

| Column Name | Type           | Description     |
|:------------|:---------------|:----------------|
| `IXS_OWNER` | `VARCHAR2(30)` | Index set owner |
| `IXS_NAME`  | `VARCHAR2(30)` | Index set name  |

### G.12 CTX_INDEX_SET_INDEXES

This view displays all the sub-indexes in an index set. It can be queried by any user.

| Column Name           | Type            | Description                     |
|:----------------------|:----------------|:--------------------------------|
| `IXX_INDEX_SET_OWNER` | `VARCHAR2(30)`  | Index set owner                 |
| `IXX_INDEX_SET_NAME`  | `VARCHAR2(30)`  | Index set name                  |
| `IXX_COLLIST`         | `VARCHAR2(500)` | Column list of the sub-index    |
| `IXX_STORAGE`         | `VARCHAR2(500)` | Storage clause of the sub-index |

### G.13 CTX_INDEX_SUB_LEXERS

This view shows the sub-lexers for each language for each index. It can be queried by `CTXSYS`.

| Column Name       | Type           | Description                                 |
|:------------------|:---------------|:--------------------------------------------|
| `ISL_INDEX_OWNER` | `VARCHAR2(30)` | Index owner                                 |
| `ISL_INDEX_NAME`  | `VARCHAR2(30)` | Index name                                  |
| `ISL_LANGUAGE`    | `VARCHAR2(30)` | Language of sub-lexer                       |
| `ISL_ALT_VALUE`   | `VARCHAR2(30)` | Alternate value of language                 |
| `ISL_OBJECT`      | `VARCHAR2(30)` | Name of lexer object used for this language |

### G.14 CTX_INDEX_SUB_LEXER_VALUES

Shows the sub-lexer attributes and their values. Accessible by `CTXSYS`.

| Column Name       | Type            | Description                                 |
|:------------------|:----------------|:--------------------------------------------|
| `ISV_INDEX_OWNER` | `VARCHAR2(30)`  | Index owner                                 |
| `ISV_INDEX_NAME`  | `VARCHAR2(30)`  | Index name                                  |
| `ISV_LANGUAGE`    | `VARCHAR2(30)`  | Language of sub-lexer                       |
| `ISV_OBJECT`      | `VARCHAR2(30)`  | Name of lexer object used for this language |
| `ISV_ATTRIBUTE`   | `VARCHAR2(30)`  | Name of sub-lexer attribute                 |
| `ISV_VALUE`       | `VARCHAR2(500)` | Value of attribute of sub-lexer             |

### G.15 CTX_INDEX_VALUES

This view displays attribute values for each object used in indexes. This view is queryable by `CTXSYS`.

| Column Name       | Type            | Description     |
|:------------------|:----------------|:----------------|
| `IXV_INDEX_OWNER` | `VARCHAR2(30)`  | Index owner     |
| `IXV_INDEX_NAME`  | `VARCHAR2(30)`  | Index name      |
| `IXV_CLASS`       | `VARCHAR2(30)`  | Class name      |
| `IXV_OBJECT`      | `VARCHAR2(30)`  | Object name     |
| `IXV_ATTRIBUTE`   | `VARCHAR2(30)`  | Attribute name  |
| `IXV_VALUE`       | `VARCHAR2(500)` | Attribute value |

### G.16 CTX_OBJECTS

This view displays all of the Text objects registered in the Text data dictionary. This view can be queried by any user.

| Column Name       | Type           | Description                                        |
|:------------------|:---------------|:---------------------------------------------------|
| `OBJ_CLASS`       | `VARCHAR2(30)` | Object class (Datastore, Filter, Lexer, and so on) |
| `OBJ_NAME`        | `VARCHAR2(30)` | Object name                                        |
| `OBJ_DESCRIPTION` | `VARCHAR2(80)` | Object description                                 |

### G.17 CTX_OBJECT_ATTRIBUTES

This view displays the attributes that can be assigned to preferences of each object. It can be queried by all users.

| Column Name       | Type            | Description                                                                                                             |
|:------------------|:----------------|:------------------------------------------------------------------------------------------------------------------------|
| `OAT_CLASS`       | `VARCHAR2(30)`  | Object class (Data Store, Filter, Lexer, and so on)                                                                     |
| `OAT_OBJECT`      | `VARCHAR2(30)`  | Object name                                                                                                             |
| `OAT_ATTRIBUTE`   | `VARCHAR2(64)`  | Attribute name                                                                                                          |
| `OAT_DESCRIPTION` | `VARCHAR2(80)`  | Description of attribute                                                                                                |
| `OAT_REQUIRED`    | `VARCHAR2(1)`   | Required attribute, either Y or N                                                                                       |
| `OAT_STATIC`      | `VARCHAR2(1)`   | Not currently used                                                                                                      |
| `OAT_DATATYPE`    | `VARCHAR2(64)`  | Attribute datatype. The value `PROCEDURE` indicates that the attribute of the object should be a stored procedure name. |
| `OAT_DEFAULT`     | `VARCHAR2(500)` | Default value for attribute                                                                                             |
| `OAT_MIN`         | `NUMBER`        | Minimum value                                                                                                           |
| `OAT_MAX`         | `NUMBER`        | Maximum value                                                                                                           |
| `OAT_MAX_LENGTH`  | `NUMBER`        | Maximum length                                                                                                          |

### G.18 CTX_OBJECT_ATTRIBUTE_LOV

This view displays the allowed values for certain object attributes provided by Oracle Text. It can be queried by all users.

| Column Name       | Type           | Description                 |
|:------------------|:---------------|:----------------------------|
| `OAL_CLASS`       | `NUMBER(38)`   | Class of object             |
| `OAL_OBJECT`      | `VARCHAR2(30)` | Object name                 |
| `OAL_ATTRIBUTE`   | `VARCHAR2(32)` | Attribute name              |
| `OAl_LABEL`       | `VARCHAR2(30)` | Attribute value label       |
| `OAL_VALUE`       | `VARCHAR2(64)` | Attribute value             |
| `OAL_DESCRIPTION` | `VARCHAR2(80)` | Attribute value description |

### G.19 CTX_ORDER_BY_COLUMNS

This view displays the `ORDER` `BY` columns registered in the Text data dictionary. It can be queried by any user.

| Column Name           | Type            | Description     |
|:----------------------|:----------------|:----------------|
| `OBC_INDEX_OWNER`     | `VARCHAR2(30)`  | Index owner     |
| `OBC_INDEX_NAME`      | `VARCHAR2(30)`  | Index name      |
| `OBC_TABLE_OWNER`     | `VARCHAR2(30)`  | Table owner     |
| `OBC_TABLE_NAME`      | `VARCHAR2(30)`  | Table name      |
| `OBC_COLUMN_NAME`     | `VARCHAR2(236)` | Column name     |
| `OBC_COLUMN_POSITION` | `VARCHAR2(30)`  | Column position |
| `OBC_COLUMN_TYPE`     | `VARCHAR2(30)`  | Column type     |
| `OBC_SECTION_NAME`    | `VARCHAR2(30)`  | Section name    |
| `OBC_SECTION_TYPE`    | `VARCHAR2(30)`  | Section type    |
| `OBC_SECTION_ID`      | `NUMBER`        | Section ID      |
| `OBC_SORT_ORDER`      | `VARCHAR2(8)`   | Sort order      |

### G.20 CTX_PARAMETERS

This view displays all system-defined parameters as defined by `CTXSYS`. It can be queried by any user.

| Column Name | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PAR_NAME`  | `VARCHAR2(30)`  | Parameter name:<br>`auto_optimize`<br>`auto_optimize_logfile`<br>`max_index_memory`<br>`ctx_doc_key_type`<br>`default_index_memory`<br>`default_datastore`<br>`default_filter_binary`<br>`default_filter_text`<br>`default_filter_file`<br>`default_section_html`<br>`default_section_xml`<br>`default_section_text`<br>`default_lexer`<br>`default_stoplist`<br>`default_storage`<br>`default_wordlist`<br>`default_ctxcat_lexer`<br>`default_ctxcat_index_set`<br>`default_ctxcat_stoplist`<br>`default_ctxcat_storage`<br>`default_ctxcat_wordlist`<br>`default_ctxrule_lexer`<br>`default_ctxrule_s``toplist`<br>`default_ctxrule_s``torage`<br>`default_ctxrule_``wordlist`<br>`log_directory` |
| `PAR_VALUE` | `VARCHAR2(500)` | Parameter value. For `max_index_memory` and `default_index_memory`, `PAR_VALUE` stores a string consisting of the memory amount. For the other parameter names, `PAR_VALUE` stores the names of the preferences used as defaults for index creation.                                                                                                                                                                                                                                                                                                                                                                                                                                                |

### G.21 CTX_PENDING

This view displays a row for each of the user's entries in the DML Queue. It can be queried by `CTXSYS`.

| Column Name          | Type           | Description                                                               |
|:---------------------|:---------------|:--------------------------------------------------------------------------|
| `PND_INDEX_OWNER`    | `VARCHAR2(30)` | Index owner                                                               |
| `PND_INDEX_NAME`     | `VARCHAR2(30)` | Name of index                                                             |
| `PND_PARTITION_NAME` | `VARCHAR2(30)` | Name of partition for local partition indexes. `NULL` for normal indexes. |
| `PND_ROWID`          | `ROWID`        | `ROWID` to be indexed                                                     |
| `PND_TIMESTAMP`      | `DATE`         | Time of modification                                                      |

### G.22 CTX_PREFERENCES

This view displays preferences created byOracle Text users, as well as all the system-defined preferences included with Oracle Text. The view contains one row for each preference. It can be queried by all users.

| Column Name  | Type           | Description                  |
|:-------------|:---------------|:-----------------------------|
| `PRE_OWNER`  | `VARCHAR2(30)` | Username of preference owner |
| `PRE_NAME`   | `VARCHAR2(30)` | Preference name              |
| `PRE_CLASS`  | `VARCHAR2(30)` | Preference class             |
| `PRE_OBJECT` | `VARCHAR2(30)` | Object used                  |

### G.23 CTX_PREFERENCE_VALUES

This view displays the values assigned to all the preferences in the Text data dictionary. The view contains one row for each value. It can be queried by all users.

| Column Name      | Type            | Description                  |
|:-----------------|:----------------|:-----------------------------|
| `PRV_OWNER`      | `VARCHAR2(30)`  | Username of preference owner |
| `PRV_PREFERENCE` | `VARCHAR2(30)`  | Preference name              |
| `PRV_ATTRIBUTE`  | `VARCHAR2(64)`  | Attribute name               |
| `PRV_VALUE`      | `VARCHAR2(500)` | Attribute value              |

### G.24 CTX_SECTIONS

This view displays information about all the sections, including SDATA and MDATA sections, that have been created in the Text data dictionary. It can be queried by any user.

| Column Name         | Type           | Description                                                                                                                    |
|:--------------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `SEC_OWNER`         | `VARCHAR2(30)` | Owner of the section group                                                                                                     |
| `SEC_SECTION_GROUP` | `VARCHAR2(30)` | Name of the section group                                                                                                      |
| `SEC_TYPE`          | `VARCHAR2(30)` | Type of section, either `ZONE`, `FIELD`, `SPECIAL`, `ATTR`, `STOP`                                                             |
| `SEC_ID`            | `NUMBER`       | Section ID                                                                                                                     |
| `SEC_NAME`          | `VARCHAR2(30)` | Name of section                                                                                                                |
| `SEC_TAG`           | `VARCHAR2(64)` | Section tag                                                                                                                    |
| `SEC_VISIBLE`       | `VARCHAR2(1)`  | Y or N visible indicator for field sections only.<br>Y indicator for READ ONLY `MDATA` sections.                               |
| `SEC_DATATYPE`      | `VARCHAR2(30)` | Shows the datatype name (`NUMBER`, `VARCHAR2`, `DATE` or `RAW`) if the section is an `SDATA` section. Otherwise, it is `NULL`. |

### G.25 CTX_SECTION_GROUPS

This view displays information about all the section groups that have been created in the Text data dictionary. It can be queried by any user.

| Column Name | Type           | Description            |
|:------------|:---------------|:-----------------------|
| `SGP_OWNER` | `VARCHAR2(30)` | Owner of section group |
| `SGP_NAME`  | `VARCHAR2(30)` | Name of section group  |
| `SGP_TYPE`  | `VARCHAR2(30)` | Type of section group  |

### G.26 CTX_SQES

This view displays the definitions for all SQEs that have been created by users. It can be queried by all users.

| Column Name | Type           | Description  |
|:------------|:---------------|:-------------|
| `SQE_OWNER` | `VARCHAR2(30)` | Owner of SQE |
| `SQE_NAME`  | `VARCHAR2(30)` | Name of SQE  |
| `SQE_QUERY` | `CLOB`         | Query Text   |

### G.27 CTX_STOPLISTS

This view displays stoplists. Queryable by all users.

| Column Name | Type           | Description                          |
|:------------|:---------------|:-------------------------------------|
| `SPL_OWNER` | `VARCHAR2(30)` | Owner of stoplist                    |
| `SPL_NAME`  | `VARCHAR2(30)` | Name of stoplist                     |
| `SPL_COUNT` | `NUMBER`       | Number of stopwords                  |
| `SPL_TYPE`  | `VARCHAR2(30)` | Type of stoplist, `MULTI` or `BASIC` |

### G.28 CTX_STOPWORDS

This view displays the stopwords in each stoplist. Queryable by all users.

| Column Name    | Type            | Description                                               |
|:---------------|:----------------|:----------------------------------------------------------|
| `SPW_OWNER`    | `VARCHAR2(30)`  | Stoplist owner                                            |
| `SPW_STOPLIST` | `VARCHAR2(30)`  | Stoplist name                                             |
| `SPW_TYPE`     | `VARCHAR2(10)`  | Stop type, either `STOP_WORD`, `STOP_CLASS`, `STOP_THEME` |
| `SPW_WORD`     | `VARCHAR2(80)`  | Stopword                                                  |
| `SPW_LANGUAGE` | `VARCHAR2(30)`  | Stopword language                                         |
| `SPW_PATTERN`  | `VARCHAR2(512)` | Stop pattern                                              |

### G.29 CTX_SUB_LEXERS

This view contains information on multi-lexers and the sub-lexer preferences they contain. It can be queried by any user.

| Column Name     | Type           | Description                                                    |
|:----------------|:---------------|:---------------------------------------------------------------|
| `SLX_OWNER`     | `VARCHAR2(30)` | Owner of the multi-lexer preference                            |
| `SLX_NAME`      | `VARCHAR2(30)` | Name of the multi-lexer preference                             |
| `SLX_LANGUAGE`  | `VARCHAR2(30)` | Language of the referenced lexer (full name, not abbreviation) |
| `SLX_ALT_VALUE` | `VARCHAR2(30)` | An alternate value for the language                            |
| `SLX_SUB_OWNER` | `VARCHAR2(30)` | Owner of the sub-lexer                                         |
| `SLX_SUB_NAME`  | `VARCHAR2(30)` | Name of the sub-lexer                                          |

### G.30 CTX_THESAURI

This view displays information about all the thesauri that have been created in the Text data dictionary. It can be queried by any user.

| Column Name | Type           | Description     |
|:------------|:---------------|:----------------|
| `THS_OWNER` | `VARCHAR2(30)` | Thesaurus owner |
| `THS_NAME`  | `VARCHAR2(30)` | Thesaurus name  |

### G.31 CTX_THES_PHRASES

This view displays phrase information for all thesauri in the Text data dictionary. It can be queried by any user.

| Column Name      | Type             | Description           |
|:-----------------|:-----------------|:----------------------|
| `THP_THESAURUS`  | `VARCHAR2(30)`   | Thesaurus name        |
| `THP_PHRASE`     | `VARCHAR2(256)`  | Thesaurus phrase      |
| `THP_QUALIFIER`  | `VARCHAR2(256)`  | Thesaurus qualifier   |
| `THP_SCOPE_NOTE` | `VARCHAR2(2000)` | Thesaurus scope notes |

### G.32 CTX_TRACE_VALUES

This view contains one row for each active trace, and shows the current value of each trace.

| Column Name | Type             | Description         |
|:------------|:-----------------|:--------------------|
| `TRC_ID`    | `BINARY_INTEGER` | Trace ID            |
| `TRC_VALUE` | `NUMBER`         | Current trace value |

**Note:**

The error "ORA-00955: name is already used by an existing object" can safely be ignored if this error is raised in the postinstall steps for patch releases. This may occur when this view is present in the database being patched.

### G.33 CTX_USER_ALEXER_DICTS

This view displays all dictionaries created by the current user.

| Column Name | Type           | Description                |
|:------------|:---------------|:---------------------------|
| `ALD_NAME`  | `VARCHAR2(30)` | Name of the dictionary     |
| `ALD_LANG`  | `VARCHAR2(30)` | Language of the dictionary |

### G.34 CTX_USER_AUTO_OPTIMIZE_INDEXES

This view displays the user indexes that are registered for auto optimization. It can be queried by all users.

| Column Name          | Type           | Description    |
|:---------------------|:---------------|:---------------|
| `AOI_INDEX_NAME`     | `VARCHAR2(30)` | Index name     |
| `AOI_PARTITION_NAME` | `VARCHAR2(30)` | Partition name |

### G.35 CTX_USER_EXTRACT_POLICIES

This view displays all of the entity extraction policies owned by the current user. All users can query this view.

| Column Name | Type           | Description                   |
|:------------|:---------------|:------------------------------|
| `EPL_NAME`  | `VARCHAR2(30)` | Entity extraction policy name |

### G.36 CTX_USER_EXTRACT_POLICY_VALUES

This view displays all of the values for the entity extraction policies owned by the current user. All users can query this view.

| Column Name       | Type            | Description                   |
|:------------------|:----------------|:------------------------------|
| `EPV_POLICY_NAME` | `VARCHAR2(30)`  | Entity extraction policy name |
| `EPV_CLASS`       | `VARCHAR2(30)`  | Object class                  |
| `EPV_OBJECT`      | `VARCHAR2(30)`  | Object name                   |
| `EPV_ATTRIBUTE`   | `VARCHAR2(30)`  | Object attribute name         |
| `EPV_VALUE`       | `VARCHAR2(500)` | Object attribute value        |

### G.37 CTX_USER_EXTRACT_RULES

This view displays the entity extraction rules for the policies owned by the current user. All users can query this view.

| Column Name       | Type             | Description                                                          |
|:------------------|:-----------------|:---------------------------------------------------------------------|
| `ERL_POLICY_NAME` | `VARCHAR2(30)`   | Entity extraction policy name                                        |
| `ERL_RULE_ID`     | `INTEGER`        | Entity extraction rule ID                                            |
| `ERL_LANGUAGE`    | `VARCHAR2(30)`   | Entity extraction rule language                                      |
| `ERL_RULE`        | `VARCHAR2(512`)  | Entity extraction rule contents                                      |
| `ERL_TYPE`        | `VARCHAR2(4000)` | String mapping backreferences to entity types                        |
| `ERL_STATUS`      | `VARCHAR2(30)`   | Entity extraction rule status: compiled, not compiled, to be deleted |
| `ERL_COMMENTS`    | `VARCHAR2(4000)` | Comments                                                             |

### G.38 CTX_USER_EXTRACT_STOP_ENTITIES

This view displays the stop entities owned by the current user. All users can query this view.

| Column Name       | Type             | Description                                                                  |
|:------------------|:-----------------|:-----------------------------------------------------------------------------|
| `ESE_POLICY_NAME` | `VARCHAR2(30)`   | Entity extraction policy name                                                |
| `ESE_NAME`        | `VARCHAR2(512)`  | Stop entity name                                                             |
| `ESE_TYPE`        | `VARCHAR2(30)`   | Stop entity type                                                             |
| `ESE_STATUS`      | `VARCHAR2(30)`   | Entity extraction rule status: compiled, not compiled, to be deleted, subset |
| `ESE_COMMENTS`    | `VARCHAR2(4000)` | Comments                                                                     |

### G.39 CTX_USER\_ FILTER_BY_COLUMNS

This view displays all `FILTER` `BY` columns registered in the Text data dictionary for the current user. It can be queried by any user.

| Column Name        | Type            | Description      |
|:-------------------|:----------------|:-----------------|
| `FBC_INDEX_NAME`   | `VARCHAR2(30)`  | Index name       |
| `FBC_TABLE_OWNER`  | `VARCHAR2(30)`  | Table owner name |
| `FBC_TABLE_NAME`   | `VARCHAR2(30)`  | Table name       |
| `FBC_COLUMN_NAME`  | `VARCHAR2(256)` | Column name      |
| `FBC_COLUMN_TYPE`  | `VARCHAR2(30)`  | Column type      |
| `FBC_SECTION_TYPE` | `VARCHAR2(30)`  | Section type     |
| `FBC_SECTION_NAME` | `VARCHAR2(30)`  | Section name     |
| `FBC_SECTION_ID`   | `NUMBER`        | Section ID       |

### G.40 CTX_USER_INDEXES

This view displays all indexes that are registered in the Text data dictionary for the current user. It can be queried by all users.

| Column Name            | Type             | Description                                                                                                                                   |
|:-----------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `IDX_CHARSET_COLUMN`   | `VARCHAR2(256)`  | Name of the charset column of base table                                                                                                      |
| `IDX_DOCID_COUNT`      | `NUMBER`         | Number of documents indexed                                                                                                                   |
| `IDX_FORMAT_COLUMN`    | `VARCHAR2(256)`  | Name of the format column of base table                                                                                                       |
| `IDX_ID`               | `NUMBER`         | Internal index ID                                                                                                                             |
| `IDX_KEY_NAME`         | `VARCHAR(256)`   | Primary key column(s)                                                                                                                         |
| `IDX_LANGUAGE_COLUMN`  | `VARCHAR2(256)`  | Name of the language column of base table                                                                                                     |
| `IDX_NAME`             | `VARCHAR2(30)`   | Name of index                                                                                                                                 |
| `IDX_STATUS`           | `VARCHAR2(12)`   | Status, either `INDEXED` or `INDEXING`                                                                                                        |
| `IDX_SYNC_INTERVAL`    | `VARCHAR2(2000)` | This is the interval string required by scheduler job. Only meaningful for `AUTOMATIC` sync. Always null for `MANUAL` and `ON` `COMMIT` sync. |
| `IDX_SYNC_JOBNAME`     | `VARCHAR2(50)`   | This is the scheduler job name for automatic sync. Only meaningful for `AUTOMATIC` sync and always null for other types of sync.              |
| `IDX_SYNC_MEMORY`      | `VARCHAR2(100`)  | The sync memory size. Only meaningful for `ON` `COMMIT` and `AUTOMATIC` types of sync. For `MANUAL` sync, this is always null.                |
| `IDX_SYNC_PARA_DEGREE` | `NUMBER`         | Degree of parallelism for sync. Only meaningful for the `AUTOMATIC` type of sync; always null for `MANUAL` and `ON` `COMMIT` syncs.           |
| `IDX_SYNC_TYPE`        | `VARCHAR2(20)`   | Type of synching: `AUTOMATIC`, `MANUAL` or `ON` `COMMIT`                                                                                      |
| `IDX_TABLE`            | `VARCHAR2(30)`   | Table name                                                                                                                                    |
| `IDX_TABLE_OWNER`      | `VARCHAR2(30)`   | Owner of table                                                                                                                                |
| `IDX_TEXT_NAME`        | `VARCHAR2(30)`   | Text column name                                                                                                                              |
| `IDX_TYPE`             | `VARCHAR2(30)`   | Type of index: `CONTEXT`, `CTXCAT`, or `CTXRULE`                                                                                              |

### G.41 CTX_USER_INDEX_ERRORS

This view displays the indexing errors for the current user and is queryable by all users.

| Column Name      | Type             | Description                                                                             |
|:-----------------|:-----------------|:----------------------------------------------------------------------------------------|
| `ERR_INDEX_NAME` | `VARCHAR2(30)`   | Name of index                                                                           |
| `ERR_TIMESTAMP`  | `DATE`           | Time of error                                                                           |
| `ERR_TEXTKEY`    | `VARCHAR2(18)`   | `ROWID` of errored document or name of errored operation (for example, `ALTER` `INDEX`) |
| `ERR_TEXT`       | `VARCHAR2(4000)` | Error text                                                                              |

### G.42 CTX_USER_INDEX_OBJECTS

This view displays the preferences that are attached to the indexes defined for the current user. It can be queried by all users.

| Column Name      | Type           | Description        |
|:-----------------|:---------------|:-------------------|
| `IXO_INDEX_NAME` | `VARCHAR2(30)` | Name of index      |
| `IXO_CLASS`      | `VARCHAR2(30)` | Object name        |
| `IXO_OBJECT`     | `VARCHAR2(80)` | Object description |

### G.43 CTX_USER_INDEX_PARTITIONS

This view displays all index partitions for the current user. It is queryable by all users.

| Column Name                | Type             | Description                                                                                                                                   |
|:---------------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `IXP_DOCID_COUNT`          | `NUMBER(38)`     | Number of documents associated with the index partition                                                                                       |
| `IXP_ID`                   | `NUMBER(38)`     | Index partition ID                                                                                                                            |
| `IXP_INDEX_NAME`           | `VARCHAR2(30)`   | Index name                                                                                                                                    |
| `IXP_INDEX_PARTITION_NAME` | `VARCHAR2(30)`   | Index partition name                                                                                                                          |
| `IDX_SYNC_INTERVAL`        | `VARCHAR2(2000)` | This is the interval string required by scheduler job. Only meaningful for `AUTOMATIC` sync. Always null for `MANUAL` and `ON` `COMMIT` sync. |
| `IDX_SYNC_JOBNAME`         | `VARCHAR2(50)`   | This is the scheduler job name for automatic sync. It is only meaningful for `AUTOMATIC` sync and always null for other types of sync.        |
| `IDX_SYNC_MEMORY`          | `VARCHAR2(100`)  | The sync memory size. Only meaningful for `ON` `COMMIT` and `AUTOMATIC` types of sync. For `MANUAL` sync, this is always null.                |
| `IDX_SYNC_PARA_DEGREE`     | `NUMBER`         | Degree of parallelism for sync. Only meaningful for the `AUTOMATIC` type of sync; always null for `MANUAL` and `ON` `COMMIT` syncs.           |
| `IDX_SYNC_TYPE`            | `VARCHAR2(20)`   | Type of synching: `AUTOMATIC`, `MANUAL` or `ON` `COMMIT`                                                                                      |
| `IXP_STATUS`               | `VARCHAR2(12)`   | Partition status                                                                                                                              |
| `IXP_TABLE_OWNER`          | `VARCHAR2(30)`   | Table owner                                                                                                                                   |
| `IXP_TABLE_NAME`           | `VARCHAR2(30)`   | Table name                                                                                                                                    |
| `IXP_TABLE_PARTITION_NAME` | `VARCHAR2(30)`   | Table partition name                                                                                                                          |

### G.44 CTX_USER_INDEX_SETS

This view displays all index set names that belong to the current user. It is queryable by all users.

| Column Name | Type           | Description    |
|:------------|:---------------|:---------------|
| `IXS_NAME`  | `VARCHAR2(30)` | Index set name |

### G.45 CTX_USER_INDEX_SET_INDEXES

This view displays all the indexes in an index set that belong to the current user. It is queryable by all users.

| Column Name          | Type            | Description                 |
|:---------------------|:----------------|:----------------------------|
| `IXX_INDEX_SET_NAME` | `VARCHAR2(30)`  | Index set name              |
| `IXX_COLLIST`        | `VARCHAR2(500)` | Column list of the index    |
| `IXX_STORAGE`        | `VARCHAR2(500)` | Storage clause of the index |

### G.46 CTX_USER_INDEX_SUB_LEXERS

This view shows the sub-lexers for each language for each index for the querying user. This view can be queried by all users.

| Column Name      | Type           | Description                                 |
|:-----------------|:---------------|:--------------------------------------------|
| `ISL_INDEX_NAME` | `VARCHAR2(30)` | Index name                                  |
| `ISL_LANGUAGE`   | `VARCHAR2(30)` | Language of sub-lexer                       |
| `ISL_ALT_VALUE`  | `VARCHAR2(30)` | Alternate value of language                 |
| `ISL_OBJECT`     | `VARCHAR2(30)` | Name of lexer object used for this language |

### G.47 CTX_USER_INDEX_SUB_LEXER_VALS

Shows the sub-lexer attributes and their values for the querying user. This view can be queried by all users.

| Column Name      | Type            | Description                                 |
|:-----------------|:----------------|:--------------------------------------------|
| `ISV_INDEX_NAME` | `VARCHAR2(30)`  | Index name                                  |
| `ISV_LANGUAGE`   | `VARCHAR2(30)`  | Language of sub-lexer                       |
| `ISV_OBJECT`     | `VARCHAR2(30)`  | Name of lexer object used for this language |
| `ISV_ATTRIBUTE`  | `VARCHAR2(30)`  | Name of sub-lexer attribute                 |
| `ISV_VALUE`      | `VARCHAR2(500)` | Value of sub-lexer attribute                |

### G.48 CTX_USER_INDEX_VALUES

This view displays attribute values for each object used in indexes for the current user. This view is queryable by all users.

| Column Name      | Type            | Description     |
|:-----------------|:----------------|:----------------|
| `IXV_INDEX_NAME` | `VARCHAR2(30)`  | Index name      |
| `IXV_CLASS`      | `VARCHAR2(30)`  | Class name      |
| `IXV_OBJECT`     | `VARCHAR2(30)`  | Object name     |
| `IXV_ATTRIBUTE`  | `VARCHAR2(30)`  | Attribute name  |
| `IXV_VALUE`      | `VARCHAR2(500)` | Attribute value |

### G.49 CTX_USER_ORDER_BY_COLUMNS

This view displays all `ORDER` `BY` columns registered in the Text data dictionary for the current user. It can be queried by any user.

| Column Name           | Type            | Description     |
|:----------------------|:----------------|:----------------|
| `OBC_INDEX_NAME`      | `VARCHAR2(30)`  | Index name      |
| `OBC_TABLE_OWNER`     | `VARCHAR2(30)`  | Table owner     |
| `OBC_TABLE_NAME`      | `VARCHAR2(30)`  | Table name      |
| `OBC_COLUMN_NAME`     | `VARCHAR2(236)` | Column name     |
| `OBC_COLUMN_POSITION` | `VARCHAR2(30)`  | Column position |
| `OBC_COLUMN_TYPE`     | `VARCHAR2(30)`  | Column type     |
| `OBC_SECTION_NAME`    | `VARCHAR2(30)`  | Section name    |
| `OBC_SECTION_TYPE`    | `VARCHAR2(30)`  | Section type    |
| `OBC_SECTION_ID`      | `NUMBER`        | Section ID      |
| `OBC_SORT_ORDER`      | `VARCHAR2(8)`   | Sort order      |

### G.50 CTX_USER_PENDING

This view displays a row for each of the user's entries in the DML Queue. It can be queried by all users.

| Column Name          | Type           | Description                                                               |
|:---------------------|:---------------|:--------------------------------------------------------------------------|
| `PND_INDEX_NAME`     | `VARCHAR2(30)` | Name of index                                                             |
| `PND_PARTITION_NAME` | `VARCHAR2(30)` | Name of partition for local partition indexes. `NULL` for normal indexes. |
| `PND_ROWID`          | `ROWID`        | Rowid to be indexed                                                       |
| `PND_TIMESTAMP`      | `DATE`         | Time of modification                                                      |

### G.51 CTX_USER_PREFERENCES

This view displays all preferences defined by the current user. It can be queried by all users.

| Column Name  | Type           | Description      |
|:-------------|:---------------|:-----------------|
| `PRE_NAME`   | `VARCHAR2(30)` | Preference name  |
| `PRE_CLASS`  | `VARCHAR2(30)` | Preference class |
| `PRE_OBJECT` | `VARCHAR2(30)` | Object used      |

### G.52 CTX_USER_PREFERENCE_VALUES

This view displays all the values for preferences defined by the current user. It can be queried by all users.

| Column Name      | Type            | Description     |
|:-----------------|:----------------|:----------------|
| `PRV_PREFERENCE` | `VARCHAR2(30)`  | Preference name |
| `PRV_ATTRIBUTE`  | `VARCHAR2(64)`  | Attribute name  |
| `PRV_VALUE`      | `VARCHAR2(500)` | Attribute value |

### G.53 CTX_USER_SECTIONS

This view displays information about the sections that have been created in the Text data dictionary for the current user. It can be queried by all users.

| Column Name          | Type           | Description                                                                                                                    |
|:---------------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `SEC_DATATYPE`       | `VARCHAR2(30)` | Shows the datatype name (`NUMBER`, `VARCHAR2`, `DATE` or `RAW`) if the section is an `SDATA` section. Otherwise, it is `NULL`. |
| `SEC__SECTION_GROUP` | `VARCHAR2(30)` | Name of the section group                                                                                                      |
| `SEC_TYPE`           | `VARCHAR2(30)` | Type of section, either `ZONE`, `FIELD`, `SPECIAL`, `STOP`, or `ATTR`                                                          |
| `SEC_ID`             | `NUMBER`       | Section ID                                                                                                                     |
| `SEC_NAME`           | `VARCHAR2(30)` | Name of section                                                                                                                |
| `SEC_TAG`            | `VARCHAR2(64)` | Section tag                                                                                                                    |
| `SEC_VISIBLE`        | `VARCHAR2(1)`  | Y or N visible indicator for field sections                                                                                    |

### G.54 CTX_USER_SECTION_GROUPS

This view displays information about the section groups that have been created in the Text data dictionary for the current user. It can be queried by all users.

| Column Name | Type           | Description           |
|:------------|:---------------|:----------------------|
| `SGP_NAME`  | `VARCHAR2(30)` | Name of section group |
| `SGP_TYPE`  | `VARCHAR2(30)` | Type of section group |

### G.55 CTX_USER_SESSION_SQES

This view displays the definitions of all session-duration SQEs that have been created by the current user.

| Column Name | Type           | Description                                                            |
|:------------|:---------------|:-----------------------------------------------------------------------|
| `SQE_OWNER` | `VARCHAR2(30)` | Name of owner of SQE                                                   |
| `SQE_NAME`  | `VARCHAR2(30)` | Name of SQE (shared namespace between persistent and session-duration) |
| `SQE_QUERY` | `CLOB`         | Query text (max size of 32k)                                           |

### G.56 CTX_USER_SQES

This view displays the definitions of all persistent duration SQEs that have been created by the current user. In other words, it does not display session duration SQEs.

| Column Name | Type           | Description  |
|:------------|:---------------|:-------------|
| `SQE_OWNER` | `VARCHAR2(30)` | Owner of SQE |
| `SQE_NAME`  | `VARCHAR2(30)` | Name of SQE  |
| `SQE_QUERY` | `CLOB`         | Query text   |

### G.57 CTX_USER_STOPLISTS

This view displays stoplists for current user. It is queryable by all users.

| Column Name | Type           | Description                          |
|:------------|:---------------|:-------------------------------------|
| `SPL_NAME`  | `VARCHAR2(30)` | Name of stoplist                     |
| `SPL_COUNT` | `NUMBER`       | Number of stopwords                  |
| `SPL_TYPE`  | `VARCHAR2(30)` | Type of stoplist, `MULTI` or `BASIC` |

### G.58 CTX_USER_STOPWORDS

This view displays stopwords in each stoplist for current user. Queryable by all users.

| Column Name    | Type            | Description                                               |
|:---------------|:----------------|:----------------------------------------------------------|
| `SPW_STOPLIST` | `VARCHAR2(30)`  | Stoplist name                                             |
| `SPW_TYPE`     | `VARCHAR2(10)`  | Stop type, either `STOP_WORD`, `STOP_CLASS`, `STOP_THEME` |
| `SPW_WORD`     | `VARCHAR2(80)`  | Stopword                                                  |
| `SPW_LANGUAGE` | `VARCHAR2(30)`  | Stopword language                                         |
| `SPW_PATTERN`  | `VARCHAR2(512)` | Stop pattern                                              |

### G.59 CTX_USER_SUB_LEXERS

For the current user, this view contains information on multi-lexers and the sub-lexer preferences they contain. It can be queried by any user.

| Column Name     | Type           | Description                                                    |
|:----------------|:---------------|:---------------------------------------------------------------|
| `SLX_NAME`      | `VARCHAR2(30)` | Name of the multi-lexer preference                             |
| `SLX_LANGUAGE`  | `VARCHAR2(30)` | Language of the referenced lexer (full name, not abbreviation) |
| `SLX_ALT_VALUE` | `VARCHAR2(30)` | An alternate value for the language                            |
| `SLX_SUB_OWNER` | `VARCHAR2(30)` | Owner of the sub-lexer                                         |
| `SLX_SUB_NAME`  | `VARCHAR2(30)` | Name of the sub-lexer                                          |

### G.60 CTX_USER_THESAURI

This view displays the information about all of the thesauri that have been created in the system by the current user. It can be viewed by all users.

| Column Name | Type           | Description    |
|:------------|:---------------|:---------------|
| `THS_NAME`  | `VARCHAR2(30)` | Thesaurus name |

### G.61 CTX_USER_THES_PHRASES

This view displays the phrase information of all thesauri owned by the current user. It can be queried by all users.

| Column Name      | Type             | Description              |
|:-----------------|:-----------------|:-------------------------|
| `THP_THESAURUS`  | `VARCHAR2(30)`   | Thesaurus name           |
| `THP_PHRASE`     | `VARCHAR2(256)`  | Thesaurus phrase         |
| `THP_QUALIFIER`  | `VARCHAR2(256)`  | Phrase qualifier         |
| `THP_SCOPE_NOTE` | `VARCHAR2(2000)` | Scope note of the phrase |

### G.62 CTX_VERSION

This view displays the `CTXSYS` data dictionary and code version number information.

| Column Name | Type          | Description                                                                                                                                                                                             |
|:------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `VER_DICT`  | `CHAR(9)`     | The `CTXSYS` data dictionary version number                                                                                                                                                             |
| `VER_CODE`  | `VARCHAR2(9)` | The version number of the code linked in to the Oracle Database shadow process<br>This column fetches the version number for linked-in code. Thus, use this column to detect and verify patch releases. |
