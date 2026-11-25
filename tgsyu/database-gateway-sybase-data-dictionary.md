The Oracle Database Gateway for Sybase translates a query that refers to an Oracle database data dictionary table into a query that retrieves the data from Sybase system tables. You perform queries on data dictionary tables over the database link in the same way you query data dictionary tables in the Oracle database. The gateway data dictionary is similar to the Oracle database data dictionary in appearance and use.

Topics:

- Sybase System Tables

- Accessing the Gateway Data Dictionary

- Direct Queries to Sybase Tables

- Supported Views and Tables

- Data Dictionary Mapping

- Gateway Data Dictionary Descriptions

### C.1 Sybase System Tables

Sybase data dictionary information is stored in the Sybase database as Sybase system tables. All Sybase system tables have names prefixed with "sys". The Sybase system tables define the structure of a database. When you change data definitions, Sybase reads and modifies the Sybase system tables to add information about the user tables.

### C.2 Accessing the Gateway Data Dictionary

Accessing a gateway data dictionary table or view is identical to accessing a data dictionary in an Oracle database. You issue a SQL `SELECT` statement specifying a database link. The Oracle database data dictionary view and column names are used to access the gateway data dictionary in an Oracle database. Synonyms of supported views are also acceptable. For example, the following statement queries the data dictionary table `ALL_CATALOG` to retrieve all table names in the Sybase database:

    SQL> SELECT * FROM "ALL_CATALOG"@SYBS;

When a data dictionary access query is issued, the gateway:

1.  Maps the requested table, view, or synonym to one or more Sybase system table names. The gateway translates all data dictionary column names to their corresponding Sybase column names within the query. If the mapping involves one Sybase system table, the gateway translates the requested table name to its corresponding Sybase system table name within the query. If the mapping involves multiple Sybase system tables, the gateway constructs a join in the query using the translated Sybase system table names.
2.  Sends the translated query to Sybase.
3.  Might convert the retrieved Sybase data to give it the appearance of the Oracle database data dictionary table.
4.  Passes the data dictionary information from the translated Sybase system table to the Oracle database.
    **Note:**

    The values returned when querying the gateway data dictionary might not be the same as the ones returned by the Oracle SQL\*Plus `DESCRIBE` command.

### C.3 Direct Queries to Sybase Tables

Queries issued directly to individual Sybase system tables are allowed but they return different results because the Sybase system table column names differ from those of the data dictionary view. Also, certain columns in an Sybase system table cannot be used in data dictionary processing.

### C.4 Supported Views and Tables

The gateway supports the following views and tables:

| Supported Views and Tables | Supported Views and Tables |
|:---------------------------|:---------------------------|
| `ALL_CATALOG`              | `ALL_COL_COMMENTS`         |
| `ALL_CONS_COLUMNS`         | `ALL_CONSTRAINTS`          |
| `ALL_IND_COLUMNS`          | `ALL_INDEXES`              |
| `ALL_OBJECTS`              | `ALL_TAB_COLUMNS`          |
| `ALL_TAB_COMMENTS`         | `ALL_TABLES`               |
| `ALL_USERS`                | `ALL_VIEWS`                |
| `DBA_CATALOG`              | `DBA_COL_COMMENTS`         |
| `DBA_OBJECTS`              | `DBA_TABLES`               |
| `DBA_TAB_COLUMNS`          | `DBA_TAB_COMMENTS`         |
| `DICT_COLUMNS`             | `DICTIONARY`               |
| `DUAL`                     | `TABLE_PRIVILEGES`         |
| `USER_CATALOG`             | `USER_COL_COMMENTS`        |
| `USER_CONS_COLUMNS`        | `USER_CONSTRAINTS`         |
| `USER_IND_COLUMNS`         | `USER_INDEXES`             |
| `USER_OBJECTS`             | `USER_TAB_COLUMNS`         |
| `USER_TAB_COMMENTS`        | `USER_TABLES`              |
| `USER_USERS`               | `USER_VIEWS`               |

No other Oracle database data dictionary tables or views are supported. If you use a view not on the list, you receive the Oracle database error code for no more rows available.

Queries through the gateway of any data dictionary table or view beginning with `ALL_` can returns rows from the Sybase database even when access privileges for those Sybase objects have not been granted. When querying an Oracle database with the Oracle data dictionary, rows are returned only for those objects you are permitted to access.

### C.5 Data Dictionary Mapping

The tables in this section list Oracle data dictionary view names and the equivalent Sybase system tables used. A plus sign (+) indicates that a join operation is involved.

Table C-1 Oracle Data Dictionary View Names and Sybase Equivalents

| View Name           | Sybase System Table Name                     |
|:--------------------|:---------------------------------------------|
| `ALL_CATALOG`       | `sysusers` + `sysobjects`                    |
| `ALL_COL_COMMENTS`  | `sysusers` + `sysobjects` + `syscolumns`     |
| `ALL_CONS_COLUMNS`  | `sp_pkeys` + `sp_fkeys`                      |
| `ALL_CONSTRAINTS`   | `sysconstraints` + `sysusers` + `sysobjects` |
| `ALL_IND_COLUMNS`   | `sysusers` + `sysindexes` + `syscolumns`     |
| `ALL_INDEXES`       | `sysusers` + `sysindexes` + `sysobjects`     |
| `ALL_OBJECTS`       | `sysusers` + `sysobjects` + `sysindexes`     |
| `ALL_TAB_COLUMNS`   | `sysusers` + `sysobjects` + `syscolumns`     |
| `ALL_TAB_COMMENTS`  | `sysusers` + `sysobjects`                    |
| `ALL_TABLES`        | `sysusers` + `sysobjects`                    |
| `ALL_USERS`         | `sysusers`                                   |
| `ALL_VIEWS`         | `sysusers` + `sysobjects` + `syscomments`    |
| `DBA_CATALOG`       | `sysusers` + `sysobjects`                    |
| `DBA_COL_COMMENTS`  | `sysusers` + `sysobjects` + `syscolumns`     |
| `DBA_OBJECTS`       | `sysusers` + `sysobjects` + `sysindexes`     |
| `DBA_TABLES`        | `sysusers` + `sysobjects`                    |
| `DBA_TAB_COLUMNS`   | `sysusers` + `sysobjects` + `syscolumns`     |
| `DBA_TAB_COMMENTS`  | `sysusers` + `sysobjects`                    |
| `DICT_COLUMNS`      | `sysobjects` + `syscolumns`                  |
| `DICTIONARY`        | `sysobjects`                                 |
| `DUAL`              | (Defined in the Gateway)                     |
| `TABLE_PRIVILEGES`  | `sysprotects` + `sysusers` + `sysobjects`    |
| `USER_CATALOG`      | `sysusers` + `sysobjects`                    |
| `USER_COL_COMMENTS` | `sysusers` + `sysobjects` + `syscolumns`     |
| `USER_CONS_COLUMNS` | `sp_pkeys` + `sp_fkeys`                      |
| `USER_CONSTRAINTS`  | `sysconstraints` + `sysusers` + `sysobjects` |
| `USER_IND_COLUMNS`  | `sysusers` + `sysindexes` + `syscolumns`     |
| `USER_INDEXES`      | `sysusers` + `sysindexes` + `sysobjects`     |
| `USER_OBJECTS`      | `sysusers` + `sysobjects` + `sysindexes`     |
| `USER_TAB_COLUMNS`  | `sysusers` + `sysobjects` + `syscolumns`     |
| `USER_TAB_COMMENTS` | `sysusers` + `sysobjects`                    |
| `USER_TABLES`       | `sysusers` + `sysobjects`                    |
| `USER_USERS`        | `sysusers`                                   |
| `USER_VIEWS`        | `sysusers` + `sysobjects` + `syscomments`    |

#### C.5.1 Default Column Values

There is a minor difference between the gateway data dictionary and a typical Oracle database data dictionary. The Oracle database columns that are missing in an Sybase system table are filled with zeros, spaces, null values, not-applicable values (N.A.), or default values, depending on the column type.

### C.6 Gateway Data Dictionary Descriptions

The gateway data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

They are described here with information retrieved by an Oracle SQL\*Plus `DESCRIBE` command. The values in the Null? column might differ from the Oracle database data dictionary tables and views. Any default value is shown to the right of an item, but this is not information returned by `DESCRIBE`.

### C.7 ALL_CATALOG

Table C-2 ALL_CATALOG

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |

### C.8 ALL_COL_COMMENTS

Table C-3 ALL_COL_COMMENTS

| Name          | Type           | Value |
|:--------------|:---------------|:------|
| `OWNER`       | `VARCHAR2(30)` | \-    |
| `TABLE_NAME`  | `VARCHAR2(30)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)` | \-    |
| `COMMENTS`    | `CHAR(1)`      | " "   |

### C.9 ALL_CONS_COLUMNS

Table C-4 ALL_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(8192)` | \-    |
| `POSITION`        | `FLOAT(49)`      | \-    |

### C.10 ALL_CONSTRAINTS

Table C-5 ALL_CONSTRAINTS

| Name                | Type           | Value                |
|:--------------------|:---------------|:---------------------|
| `OWNER`             | `VARCHAR2(30)` | \-                   |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-                   |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | "`R`" or "`P`"       |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-                   |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`  | `NULL`               |
| `R_OWNER`           | `VARCHAR2(30)` | \-                   |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | \-                   |
| `DELETE_RULE`       | `VARCHAR2(9)`  | "`NO ACTION`" or " " |
| `STATUS`            | `VARCHAR2(7)`  | "`ENABLED`"          |
| `DEFERRABLE`        | `VARCHAR2(1)`  | `NULL`               |
| `DEFERRED`          | `VARCHAR2(1)`  | `NULL`               |
| `VALIDATED`         | `VARCHAR2(1)`  | `NULL`               |
| `GENERATED`         | `VARCHAR2(1)`  | `NULL`               |
| `BAD`               | `VARCHAR2(1)`  | `NULL`               |
| `RELY`              | `VARCHAR2(1)`  | `NULL`               |
| `LAST_CHANGE`       | `DATE`         | \-                   |

### C.11 ALL_IND_COLUMNS

Table C-6 ALL_IND_COLUMNS

| Name              | Type             | Value               |
|:------------------|:-----------------|:--------------------|
| `INDEX_OWNER`     | `VARCHAR2(30)`   | \-                  |
| `INDEX_NAME`      | `VARCHAR2(30)`   | \-                  |
| `TABLE_OWNER`     | `VARCHAR2(30)`   | \-                  |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-                  |
| `COLUMN_NAME`     | `VARCHAR2(8192)` | \-                  |
| `COLUMN_POSITION` | `FLOAT(49)`      | \-                  |
| `COLUMN_LENGTH`   | `FLOAT(49)`      | \-                  |
| `DESCEND`         | `VARCHAR(4)`     | "`DESC`" or "`ASC`" |

### C.12 ALL_INDEXES

Table C-7 ALL_INDEXES

| Name                      | Type           | Value                    |
|:--------------------------|:---------------|:-------------------------|
| `OWNER`                   | `VARCHAR2(30)` | \-                       |
| `INDEX_NAME`              | `VARCHAR2(30)` | \-                       |
| `INDEX_TYPE`              | `VARCHAR2(1)`  | `NULL`                   |
| `TABLE_OWNER`             | `VARCHAR2(30)` | \-                       |
| `TABLE_NAME`              | `VARCHAR2(30)` | \-                       |
| `TABLE_TYPE`              | `VARCHAR2(7)`  | "`TABLE`" or "`CLUSTER`" |
| `UNIQUENESS`              | `VARCHAR2(1)`  | `NULL`                   |
| `COMPRESSION`             | `VARCHAR2(1)`  | `NULL`                   |
| `PREFIX_LENGTH`           | `NUMBER`       | `0`                      |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`  | `NULL`                   |
| `INI_TRANS`               | `NUMBER`       | `0`                      |
| `MAX_TRANS`               | `NUMBER`       | `0`                      |
| `INITIAL_EXTENT`          | `NUMBER`       | `0`                      |
| `NEXT_EXTENT`             | `NUMBER`       | `0`                      |
| `MIN_EXTENTS`             | `NUMBER`       | `0`                      |
| `MAX_EXTENTS`             | `NUMBER`       | `0`                      |
| `PCT_INCREASE`            | `NUMBER`       | `0`                      |
| `PCT_THRESHOLD`           | `NUMBER`       | `0`                      |
| `INCLUDE_COLUMN`          | `NUMBER`       | `0`                      |
| `FREELISTS`               | `NUMBER`       | `0`                      |
| `FREELIST_GROUPS`         | `NUMBER`       | `0`                      |
| `PCT_FREE`                | `NUMBER`       | `0`                      |
| `LOGGING`                 | `VARCHAR2(1)`  | `NULL`                   |
| `BLEVEL`                  | `NUMBER`       | `0`                      |
| `LEAF_BLOCKS`             | `NUMBER`       | `0`                      |
| `DISTINCT_KEYS`           | `NUMBER`       | `0`                      |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`       | `0`                      |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`       | `0`                      |
| `CLUSTERING_FACTOR`       | `NUMBER`       | `0`                      |
| `STATUS`                  | `VARCHAR2(1)`  | `NULL`                   |
| `NUM_ROWS`                | `NUMBER`       | `0`                      |
| `SAMPLE_SIZE`             | `NUMBER`       | `0`                      |
| `LAST_ANALYZED`           | `DATE`         | `NULL`                   |
| `DEGREE`                  | `VARCHAR2(1)`  | `NULL`                   |
| `INSTANCES`               | `VARCHAR2(1)`  | `NULL`                   |
| `PARTITIONED`             | `VARCHAR2(1)`  | `NULL`                   |
| `TEMPORARY`               | `VARCHAR2(1)`  | `NULL`                   |
| `GENERATED`               | `VARCHAR2(1)`  | `NULL`                   |
| `SECONDARY`               | `VARCHAR2(1)`  | `NULL`                   |
| `BUFFER_POOL`             | `VARCHAR2(1)`  | `NULL`                   |
| `USER_STATS`              | `VARCHAR2(1)`  | `NULL`                   |
| `DURATION`                | `VARCHAR2(1)`  | `NULL`                   |
| `PCT_DIRECT_ACCESS`       | `NUMBER`       | `0`                      |
| `ITYP_OWNER`              | `VARCHAR2(1)`  | `NULL`                   |
| `ITYP_NAME`               | `VARCHAR2(1)`  | `NULL`                   |
| `PARAMETERS`              | `VARCHAR2(1)`  | `NULL`                   |
| `GLOBAL_STATS`            | `VARCHAR2(1)`  | `NULL`                   |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`  | `NULL`                   |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`  | `NULL`                   |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`  | `NULL`                   |

### C.13 ALL_OBJECTS

Table C-8 ALL_OBJECTS

| Name             | Type           | Value                                  |
|:-----------------|:---------------|:---------------------------------------|
| `OWNER`          | `VARCHAR2(30)` | \-                                     |
| `OBJECT_NAME`    | `VARCHAR2(30)` | \-                                     |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`  | `NULL`                                 |
| `OBJECT_ID`      | `NUMBER`       | \-                                     |
| `DATA_OBJECT_ID` | `NUMBER`       | 0                                      |
| `OBJECT_TYPE`    | `VARCHAR2(9)`  | "`TABLE`" or "`VIEW`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`         | \-                                     |
| `LAST_DDL_TIME`  | `DATE`         | \-                                     |
| `TIMESTAMP`      | `VARCHAR2(1)`  | `NULL`                                 |
| `STATUS`         | `VARCHAR2(5)`  | "`VALID`"                              |
| `TEMPORARY`      | `VARCHAR2(1)`  | `NULL`                                 |
| `GENERATED`      | `VARCHAR2(1)`  | `NULL`                                 |
| `SECONDARY`      | `VARCHAR2(1)`  | `NULL`                                 |

### C.14 ALL_TAB_COLUMNS

Table C-9 ALL_TAB_COLUMNS

| Name                   | Type           | Value          |
|:-----------------------|:---------------|:---------------|
| `OWNER`                | `VARCHAR2(30)` | \-             |
| `TABLE_NAME`           | `VARCHAR2(30)` | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)` | \-             |
| `DATA_TYPE`            | `VARCHAR2(8)`  | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`  | `NULL`         |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`  | `NULL`         |
| `DATA_LENGTH`          | `NUMBER`       | \-             |
| `DATA_PRECISION`       | `NUMBER`       | \-             |
| `DATA_SCALE`           | `NUMBER`       | \-             |
| `NULLABLE`             | `VARCHAR2(1)`  | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER`       | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`       | `0`            |
| `DATA_DEFAULT`         | `VARCHAR2(1)`  | `NULL`         |
| `NUM_DISTINCT`         | `NUMBER`       | `0`            |
| `LOW_VALUE`            | `NUMBER`       | `0`            |
| `HIGH_VALUE`           | `NUMBER`       | `0`            |
| `DENSITY`              | `NUMBER`       | `0`            |
| `NUM_NULLS`            | `NUMBER`       | `0`            |
| `NUM_BUCKETS`          | `NUMBER`       | `0`            |
| `LAST_ANALYZED`        | `DATE`         | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`       | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`  | `NULL`         |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`       | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(1)`  | `NULL`         |
| `USER_STATS`           | `VARCHAR2(1)`  | `NULL`         |
| `AVG_COL_LEN`          | `NUMBER`       | `0`            |

### C.15 ALL_TAB_COMMENTS

Table C-10 ALL_TAB_COMMENTS

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`  | `NULL`                |

### C.16 ALL_TABLES

Table C-11 ALL_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `OWNER`                     | `VARCHAR2(30)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `CHAR(1)`      | " "    |
| `CLUSTER_NAME`              | `CHAR(1)`      | " "    |
| `IOT_NAME`                  | `CHAR(1)`      | " "    |
| `PCT_FREE`                  | `NUMBER(10)`   | `0`    |
| `PCT_USED`                  | `NUMBER(10)`   | `0`    |
| `INI_TRANS`                 | `NUMBER(10)`   | `0`    |
| `MAX_TRANS`                 | `NUMBER(10)`   | `0`    |
| `INITIAL_EXTENT`            | `NUMBER(10)`   | `0`    |
| `NEXT_EXTENT`               | `NUMBER(10)`   | `0`    |
| `MIN_EXTENTS`               | `NUMBER(10)`   | `0`    |
| `MAX_EXTENTS`               | `NUMBER(10)`   | `0`    |
| `PCT_INCREASE`              | `NUMBER(10)`   | `0`    |
| `FREELISTS`                 | `NUMBER(10)`   | `0`    |
| `FREELIST_GROUPS`           | `NUMBER(10)`   | `0`    |
| `LOGGING`                   | `CHAR(1)`      | " "    |
| `BACKED_UP`                 | `CHAR(1)`      | " "    |
| `NUM_ROWS`                  | `NUMBER(10)`   | `0`    |
| `BLOCKS`                    | `NUMBER(10)`   | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER(10)`   | `0`    |
| `AVG_SPACE`                 | `NUMBER(10)`   | `0`    |
| `CHAIN_CNT`                 | `NUMBER(10)`   | `0`    |
| `AVG_ROW_LEN`               | `NUMBER(10)`   | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER(10)`   | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER(10)`   | `0`    |
| `DEGREE`                    | `CHAR(1)`      | " "    |
| `INSTANCES`                 | `CHAR(1)`      | " "    |
| `CACHE`                     | `CHAR(1)`      | " "    |
| `TABLE_LOCK`                | `CHAR(1)`      | " "    |
| `SAMPLE_SIZE`               | `NUMBER(10)`   | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `CHAR(1)`      | " "    |
| `IOT_TYPE`                  | `CHAR(1)`      | " "    |
| `TEMPORARY`                 | `CHAR(1)`      | " "    |
| `SECONDARY`                 | `CHAR(1)`      | " "    |
| `NESTED`                    | `CHAR(1)`      | " "    |
| `BUFFER_POOL`               | `CHAR(1)`      | " "    |
| `ROW_MOVEMENT`              | `CHAR(1)`      | " "    |
| `GLOBAL_STATS`              | `CHAR(1)`      | " "    |
| `USER_STATS`                | `CHAR(1)`      | " "    |
| `DURATION`                  | `CHAR(1)`      | " "    |
| `SKIP_CORRUPT`              | `CHAR(1)`      | " "    |
| `MONITORING`                | `CHAR(1)`      | " "    |

### C.17 ALL_USERS

Table C-12 ALL_USERS

| Name       | Type           | Value     |
|:-----------|:---------------|:----------|
| `USERNAME` | `VARCHAR2(30)` | \-        |
| `USER_ID`  | `NUMBER(10)`   | \-        |
| `CREATED`  | `DATE`         | `SYSDATE` |

### C.18 ALL_VIEWS

Table C-13 ALL_VIEWS

| Name               | Type              | Value |
|:-------------------|:------------------|:------|
| `OWNER`            | `CHAR(30)`        | \-    |
| `VIEW_NAME`        | `CHAR(30)`        | \-    |
| `TEXT_LENGTH`      | `NUMBER(10)`      | `0`   |
| `TEXT`             | `VARCHAR2(32512)` | \-    |
| `TYPE_TEXT_LENGTH` | `NUMBER(10)`      | `0`   |
| `TYPE_TEXT`        | `CHAR(1)`         | " "   |
| `OID_TEXT_LENGTH`  | `NUMBER(10)`      | `0`   |
| `OID_TEXT`         | `CHAR(1)`         | " "   |
| `VIEW_TYPE_OWNER`  | `CHAR(1)`         | " "   |
| `VIEW_TYPE`        | `CHAR(1)`         | " "   |

### C.19 DBA_CATALOG

Table C-14 DBA_CATALOG

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |

### C.20 DBA_COL_COMMENTS

Table C-15 DBA_COL_COMMENTS

| Name          | Type           | Value |
|:--------------|:---------------|:------|
| `OWNER`       | `VARCHAR2(30)` | \-    |
| `TABLE_NAME`  | `VARCHAR2(30)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)` | \-    |
| `COMMENTS`    | `CHAR(1)`      | " "   |

### C.21 DBA_OBJECTS

Table C-16 DBA_OBJECTS

| Name             | Type           | Value                                  |
|:-----------------|:---------------|:---------------------------------------|
| `OWNER`          | `VARCHAR2(30)` | \-                                     |
| `OBJECT_NAME`    | `VARCHAR2(30)` | \-                                     |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`  | `NULL`                                 |
| `OBJECT_ID`      | `NUMBER`       | \-                                     |
| `DATA_OBJECT_ID` | `NUMBER`       | `0`                                    |
| `OBJECT_TYPE`    | `VARCHAR2(9)`  | "`TABLE`" or "`VIEW`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`         | \-                                     |
| `LAST_DDL_TIME`  | `DATE`         | \-                                     |
| `TIMESTAMP`      | `VARCHAR2(1)`  | `NULL`                                 |
| `STATUS`         | `VARCHAR2(5)`  | `NULL`                                 |
| `TEMPORARY`      | `VARCHAR2(1)`  | `NULL`                                 |
| `GENERATED`      | `VARCHAR2(1)`  | `NULL`                                 |
| `SECONDARY`      | `VARCHAR2(1)`  | `NULL`                                 |

### C.22 DBA_TAB_COLUMNS

Table C-17 DBA_TAB_COLUMNS

| Name                  | Type           | Value          |
|:----------------------|:---------------|:---------------|
| `OWNER`               | `VARCHAR2(30)` | \-             |
| `TABLE_NAME`          | `VARCHAR2(30)` | \-             |
| `COLUMN_NAME`         | `VARCHAR2(30)` | \-             |
| `DATA_TYPE`           | `VARCHAR2(8)`  | \-             |
| `DATA_TYPE_MOD`       | `VARCHAR2(1)`  | `NULL`         |
| `DATA_TYPE_OWNER`     | `VARCHAR2(1)`  | `NULL`         |
| `DATA_LENGTH`         | `NUMBER`       | \-             |
| `DATA_PRECISION`      | `NUMBER`       | \-             |
| `DATA_SCALE`          | `NUMBER`       | \-             |
| `NULLABLE`            | `VARCHAR2(1)`  | "`Y`" or "`N`" |
| `COLUMN_ID`           | `NUMBER`       | \-             |
| `DEFAULT_LENGTH`      | `NUMBER`       | `0`            |
| `DATA_DEFAULT`        | `VARCHAR2(1)`  | `NULL`         |
| `NUM_DISTINCT`        | `NUMBER`       | `0`            |
| `LOW_VALUE`           | `NUMBER`       | `0`            |
| `HIGH_VALUE`          | `NUMBER`       | `0`            |
| `DENSITY`             | `NUMBER`       | `0`            |
| `NUM_NULLS`           | `NUMBER`       | `0`            |
| `NUM_BUCKETS`         | `NUMBER`       | `0`            |
| `LAST_ANALYZED`       | `DATE`         | `NULL`         |
| `SAMPLE_SIZE`         | `NUMBER`       | `0`            |
| `CHARACTER_SET_NAME`  | `VARCHAR2(1)`  | `NULL`         |
| `CHAR_COL_DEC_LENGTH` | `NUMBER`       | `0`            |
| `GLOBAL_STATS`        | `VARCHAR2(1)`  | `NULL`         |
| `USER_STATS`          | `VARCHAR2(1)`  | `NULL`         |
| `AVG_COL_LEN`         | `NUMBER`       | `0`            |

### C.23 DBA_TAB_COMMENTS

Table C-18 DBA_TAB_COMMENTS

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`  | `NULL`                |

### C.24 DBA_TABLES

Table C-19 DBA_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `OWNER`                     | `VARCHAR2(30)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `CHAR(1)`      | " "    |
| `CLUSTER_NAME`              | `CHAR(1)`      | " "    |
| `IOT_NAME`                  | `CHAR(1)`      | " "    |
| `PCT_FREE`                  | `NUMBER(10)`   | `0`    |
| `PCT_USED`                  | `NUMBER(10)`   | `0`    |
| `INI_TRANS`                 | `NUMBER(10)`   | `0`    |
| `MAX_TRANS`                 | `NUMBER(10)`   | `0`    |
| `INITIAL_EXTENT`            | `NUMBER(10)`   | `0`    |
| `NEXT_EXTENT`               | `NUMBER(10)`   | `0`    |
| `MIN_EXTENTS`               | `NUMBER(10)`   | `0`    |
| `MAX_EXTENTS`               | `NUMBER(10)`   | `0`    |
| `PCT_INCREASE`              | `NUMBER(10)`   | `0`    |
| `FREELISTS`                 | `NUMBER(10)`   | `0`    |
| `FREELIST_GROUPS`           | `NUMBER(10)`   | `0`    |
| `LOGGING`                   | `CHAR(1)`      | " "    |
| `BACKED_UP`                 | `CHAR(1)`      | " "    |
| `NUM_ROWS`                  | `NUMBER(10)`   | `0`    |
| `BLOCKS`                    | `NUMBER(10)`   | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER(10)`   | `0`    |
| `AVG_SPACE`                 | `NUMBER(10)`   | `0`    |
| `CHAIN_CNT`                 | `NUMBER(10)`   | `0`    |
| `AVG_ROW_LEN`               | `NUMBER(10)`   | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER(10)`   | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER(10)`   | `0`    |
| `DEGREE`                    | `CHAR(1)`      | " "    |
| `INSTANCES`                 | `CHAR(1)`      | " "    |
| `CACHE`                     | `CHAR(1)`      | " "    |
| `TABLE_LOCK`                | `CHAR(1)`      | " "    |
| `SAMPLE_SIZE`               | `NUMBER(10)`   | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `CHAR(1)`      | " "    |
| `IOT_TYPE`                  | `CHAR(1)`      | " "    |
| `TEMPORARY`                 | `CHAR(1)`      | " "    |
| `SECONDARY`                 | `CHAR(1)`      | " "    |
| `NESTED`                    | `CHAR(1)`      | " "    |
| `BUFFER_POOL`               | `CHAR(1)`      | " "    |
| `ROW_MOVEMENT`              | `CHAR(1)`      | " "    |
| `GLOBAL_STATS`              | `CHAR(1)`      | " "    |
| `USER_STATS`                | `CHAR(1)`      | " "    |
| `DURATION`                  | `CHAR(1)`      | " "    |
| `SKIP_CORRUPT`              | `CHAR(1)`      | " "    |
| `MONITORING`                | `CHAR(1)`      | " "    |

### C.25 DICT_COLUMNS

Table C-20 DICT_COLUMNS

| Name          | Type           | Value |
|:--------------|:---------------|:------|
| `TABLE_NAME`  | `VARCHAR2(30)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)` | \-    |
| `COMMENTS`    | `CHAR(1)`      | " "   |

### C.26 DICTIONARY

Table C-21 DICTIONARY

| Name         | Type           | Value |
|:-------------|:---------------|:------|
| `TABLE_NAME` | `VARCHAR2(30)` | \-    |
| `COMMENTS`   | `CHAR(1)`      | " "   |

### C.27 DUAL

Table C-22 DUAL

| Name    | Type          | Value |
|:--------|:--------------|:------|
| `DUMMY` | `VARCHAR2(1)` | "`X`" |

### C.28 TABLE_PRIVILEGES

Table C-23 TABLE_PRIVILEGES

| Name              | Type           | Value |
|:------------------|:---------------|:------|
| `GRANTEE`         | `VARCHAR2(30)` | \-    |
| `OWNER`           | `VARCHAR2(30)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)` | \-    |
| `GRANTOR`         | `VARCHAR2(30)` | \-    |
| `SELECT_PRIV`     | `VARCHAR2(1)`  | "`Y`" |
| `INSERT_PRIV`     | `VARCHAR2(1)`  | "`A`" |
| `DELETE_PRIV`     | `VARCHAR2(1)`  | "`Y`" |
| `UPDATE_PRIV`     | `VARCHAR2(1)`  | "`A`" |
| `REFERENCES_PRIV` | `VARCHAR2(1)`  | "`A`" |
| `ALTER_PRIV`      | `VARCHAR2(1)`  | "`Y`" |
| `INDEX_PRIV`      | `VARCHAR2(1)`  | "`Y`" |
| `CREATED`         | `DATE`         | \-    |

### C.29 USER_CATALOG

Table C-24 USER_CATALOG

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |

### C.30 USER_COL_COMMENTS

Table C-25 USER_COL_COMMENTS

| Name          | Type           | Value  |
|:--------------|:---------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(30)` | \-     |
| `COLUMN_NAME` | `VARCHAR2(30)` | \-     |
| `COMMENTS`    | `VARCHAR2(1)`  | `NULL` |

### C.31 USER_CONS_COLUMNS

Table C-26 USER_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-    |
| `POSITION`        | `NUMBER`         | \-    |

### C.32 USER_CONSTRAINTS

Table C-27 USER_CONSTRAINTS

| Name                | Type           | Value               |
|:--------------------|:---------------|:--------------------|
| `OWNER`             | `VARCHAR2(30)` | \-                  |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-                  |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | "`R`" or "`P`"      |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-                  |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`  | `NULL`              |
| `R_OWNER`           | `VARCHAR2(30)` | \-                  |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | \-                  |
| `DELETE_RULE`       | `VARCHAR2(9)`  | "`NOACTION`" or " " |
| `STATUS`            | `VARCHAR2(7)`  | "`ENABLED`"         |
| `DEFERRABLE`        | `VARCHAR2(1)`  | `NULL`              |
| `DEFERRED`          | `VARCHAR2(1)`  | `NULL`              |
| `VALIDATED`         | `VARCHAR2(1)`  | `NULL`              |
| `GENERATED`         | `VARCHAR2(1)`  | `NULL`              |
| `BAD`               | `VARCHAR2(1)`  | `NULL`              |
| `RELY`              | `VARCHAR2(1)`  | `NULL`              |
| `LAST_CHANGE`       | `DATE`         | \-                  |

### C.33 USER_IND_COLUMNS

Table C-28 USER_IND_COLUMNS

| Name              | Type             | Value               |
|:------------------|:-----------------|:--------------------|
| `INDEX_NAME`      | `VARCHAR2(30)`   | \-                  |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-                  |
| `COLUMN_NAME`     | `VARCHAR2(8192)` | \-                  |
| `COLUMN_POSITION` | `FLOAT(49)`      | \-                  |
| `COLUMN_LENGTH`   | `FLOAT(49)`      | \-                  |
| `DESCEND`         | `VARCHAR(4)`     | "`DESC`" or "`ASC`" |

### C.34 USER_INDEXES

Table C-29 USER_INDEXES

| Name                      | Type           | Value                    |
|:--------------------------|:---------------|:-------------------------|
| `INDEX_NAME`              | `VARCHAR2(30)` | \-                       |
| `INDEX_TYPE`              | `VARCHAR2(1)`  | `NULL`                   |
| `TABLE_OWNER`             | `VARCHAR2(30)` | \-                       |
| `TABLE_NAME`              | `VARCHAR2(30)` | \-                       |
| `TABLE_TYPE`              | `VARCHAR2(7)`  | "`TABLE`" or "`CLUSTER`" |
| `UNIQUENESS`              | `VARCHAR2(1)`  | `NULL`                   |
| `COMPRESSION`             | `VARCHAR2(1)`  | `NULL`                   |
| `PREFIX_LENGTH`           | `NUMBER`       | `0`                      |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`  | `NULL`                   |
| `INI_TRANS`               | `NUMBER`       | `0`                      |
| `MAX_TRANS`               | `NUMBER`       | `0`                      |
| `INITIAL_EXTENT`          | `NUMBER`       | `0`                      |
| `NEXT_EXTENT`             | `NUMBER`       | `0`                      |
| `MIN_EXTENTS`             | `NUMBER`       | `0`                      |
| `MAX_EXTENTS`             | `NUMBER`       | `0`                      |
| `PCT_INCREASE`            | `NUMBER`       | `0`                      |
| `PCT_THRESHOLD`           | `NUMBER`       | `0`                      |
| `INCLUDE_COLUMN`          | `NUMBER`       | `0`                      |
| `FREELISTS`               | `NUMBER`       | `0`                      |
| `FREELIST_GROUPS`         | `NUMBER`       | `0`                      |
| `PCT_FREE`                | `NUMBER`       | `0`                      |
| `LOGGING`                 | `VARCHAR2(1)`  | `NULL`                   |
| `BLEVEL`                  | `NUMBER`       | `0`                      |
| `LEAF_BLOCKS`             | `NUMBER`       | `0`                      |
| `DISTINCT_KEYS`           | `NUMBER`       | `0`                      |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`       | `0`                      |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`       | `0`                      |
| `CLUSTERING_FACTOR`       | `NUMBER`       | `0`                      |
| `STATUS`                  | `VARCHAR2(1)`  | `NULL`                   |
| `NUM_ROWS`                | `NUMBER`       | `0`                      |
| `SAMPLE_SIZE`             | `NUMBER`       | `0`                      |
| `LAST_ANALYZED`           | `DATE`         | `NULL`                   |
| `DEGREE`                  | `VARCHAR2(1)`  | `NULL`                   |
| `INSTANCES`               | `VARCHAR2(1)`  | `NULL`                   |
| `PARTITIONED`             | `VARCHAR2(1)`  | `NULL`                   |
| `TEMPORARY`               | `VARCHAR2(1)`  | `NULL`                   |
| `GENERATED`               | `VARCHAR2(1)`  | `NULL`                   |
| `SECONDARY`               | `VARCHAR2(1)`  | `NULL`                   |
| `BUFFER_POOL`             | `VARCHAR2(1)`  | `NULL`                   |
| `USER_STATS`              | `VARCHAR2(1)`  | `NULL`                   |
| `DURATION`                | `VARHCAR2(1)`  | `NULL`                   |
| `PCT_DIRECT_ACCESS`       | `NUMBER`       | `0`                      |
| `ITYP_OWNER`              | `VARCHAR2(1)`  | `NULL`                   |
| `ITYP_NAME`               | `VARCHAR2(1)`  | `NULL`                   |
| `PARAMETERS`              | `VARCHAR2(1)`  | `NULL`                   |
| `GLOBAL_STATS`            | `VARCHAR2(1)`  | `NULL`                   |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`  | `NULL`                   |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`  | `NULL`                   |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`  | `NULL`                   |

### C.35 USER_OBJECTS

Table C-30 USER_OBJECTS

| Name             | Type           | Value                                  |
|:-----------------|:---------------|:---------------------------------------|
| `OBJECT_NAME`    | `VARCHAR2(30)` | \-                                     |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`  | `NULL`                                 |
| `OBJECT_ID`      | `NUMBER`       | \-                                     |
| `DATA_OBJECT_ID` | `NUMBER`       | 0                                      |
| `OBJECT_TYPE`    | `VARCHAR2(9)`  | "`TABLE`" or "`VIEW`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`         | \-                                     |
| `LAST_DDL_TIME`  | `DATE`         | \-                                     |
| `TIMESTAMP`      | `VARCHAR2(1)`  | `NULL`                                 |
| `STATUS`         | `VARCHAR2(5)`  | "`VALID`"                              |
| `TEMPORARY`      | `VARCHAR2(1)`  | `NULL`                                 |
| `GENERATED`      | `VARCHAR2(1)`  | `NULL`                                 |
| `SECONDARY`      | `VARCHAR2(1)`  | `NULL`                                 |

### C.36 USER_TAB_COLUMNS

Table C-31 USER_TAB_COLUMNS

| Name                   | Type           | Value          |
|:-----------------------|:---------------|:---------------|
| `TABLE_NAME`           | `VARCHAR2(30)` | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)` | \-             |
| `DATA_TYPE`            | `VARCHAR2(8)`  | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`  | `NULL`         |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`  | `NULL`         |
| `DATA_LENGTH`          | `NUMBER`       | \-             |
| `DATA_PRECISION`       | `NUMBER`       | \-             |
| `DATA_SCALE`           | `NUMBER`       | \-             |
| `NULLABLE`             | `VARCHAR2(1)`  | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER`       | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`       | `0`            |
| `DATA_DEFAULT`         | `VARCHAR2(1)`  | `NULL`         |
| `NUM_DISTINCT`         | `NUMBER`       | `0`            |
| `LOW_VALUE`            | `NUMBER`       | `0`            |
| `HIGH_VALUE`           | `NUMBER`       | `0`            |
| `DENSITY`              | `NUMBER`       | `0`            |
| `NUM_NULLS`            | `NUMBER`       | `0`            |
| `NUM_BUCKETS`          | `NUMBER`       | `0`            |
| `LAST_ANALYZED`        | `DATE`         | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`       | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`  | `NULL`         |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`       | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(1)`  | `NULL`         |
| `USER_STATS`           | `VARCHAR2(1)`  | `NULL`         |
| `AVG_COL_LEN`          | `NUMBER`       | `0`            |

### C.37 USER_TAB_COMMENTS

Table C-32 USER_TAB_COMMENTS

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`  | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`  | `NULL`                |

### C.38 USER_TABLES

Table C-33 USER_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`  | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(1)`  | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(1)`  | `NULL` |
| `PCT_FREE`                  | `NUMBER`       | `0`    |
| `PCT_USED`                  | `NUMBER`       | `0`    |
| `INI_TRANS`                 | `NUMBER`       | `0`    |
| `MAX_TRANS`                 | `NUMBER`       | `0`    |
| `INITIAL_EXTENT`            | `NUMBER`       | `0`    |
| `NEXT_EXTENT`               | `NUMBER`       | `0`    |
| `MIN_EXTENTS`               | `NUMBER`       | `0`    |
| `MAX_EXTENTS`               | `NUMBER`       | `0`    |
| `PCT_INCREASE`              | `NUMBER`       | `0`    |
| `FREELISTS`                 | `NUMBER`       | `0`    |
| `FREELIST_GROUPS`           | `NUMBER`       | `0`    |
| `LOGGING`                   | `VARCHAR2(1)`  | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`  | `NULL` |
| `NUM_ROWS`                  | `NUMBER`       | `0`    |
| `BLOCKS`                    | `NUMBER`       | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(1)`  | `NULL` |
| `INSTANCES`                 | `VARCHAR2(1)`  | `NULL` |
| `CACHE`                     | `VARCHAR2(1)`  | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(1)`  | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(1)`  | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(1)`  | `NULL` |
| `TEMPORARY`                 | `VARHCAR2(1)`  | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`  | `NULL` |
| `NESTED`                    | `VARCHAR2(1)`  | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(1)`  | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`  | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(1)`  | `NULL` |
| `USER_STATS`                | `VARCHAR2(1)`  | `NULL` |
| `DURATION`                  | `VARCHAR2(1)`  | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`  | `NULL` |
| `MONITORING`                | `VARCHAR2(1)`  | `NULL` |

### C.39 USER_USERS

Table C-34 USER_USERS

| Name                          | Type           | Value     |
|:------------------------------|:---------------|:----------|
| `USERNAME`                    | `VARCHAR2(30)` | \-        |
| `USER_ID`                     | `NUMBER(5)`    | \-        |
| `ACCOUNT_STATUS`              | `VARCHAR2(4)`  | "`OPEN`"  |
| `LOCK_DATE`                   | `DATE`         | `NULL`    |
| `EXPIRY_DATE`                 | `DATE`         | `NULL`    |
| `DEFAULT_TABLESPACE`          | `VARCHAR2(1)`  | `NULL`    |
| `TEMPORARY_TABLESPACE`        | `VARCHAR2(1)`  | `NULL`    |
| `CREATED`                     | `DATE`         | `SYSDATE` |
| `INITIAL_RSRC_CONSUMER_GROUP` | `VARCHAR2(1)`  | `NULL`    |
| `EXTERNAL_NAME`               | `VARCHAR2(1)`  | `NULL`    |

### C.40 USER_VIEWS

Table C-35 USER_VIEWS

| Name               | Type            | Value  |
|:-------------------|:----------------|:-------|
| `VIEW_NAME`        | `VARCHAR2(30)`  | \-     |
| `TEXT_LENGTH`      | `NUMBER`        | `0`    |
| `TEXT`             | `VARCHAR2(255)` | \-     |
| `TYPE_TEXT_LENGTH` | `NUMBER`        | `0`    |
| `TYPE_TEXT`        | `VARCHAR2(1)`   | `NULL` |
| `OID_TEXT_LENGTH`  | `NUMBER`        | `0`    |
| `OID_TEXT`         | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE`        | `VARCHAR2(1)`   | `NULL` |
