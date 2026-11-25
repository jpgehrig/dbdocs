The Oracle Database Gateway for SQL Server translates a query that refers to an Oracle database data dictionary table into a query that retrieves the data from SQL Server system tables. You perform queries on data dictionary tables over the database link in the same way you query data dictionary tables in the Oracle database. The gateway data dictionary is similar to the Oracle database data dictionary in appearance and use.

Topics:

- Data Dictionary Support

- Data Dictionary Mapping

- Gateway Data Dictionary Descriptions

### C.1 Data Dictionary Support

The following paragraphs describe the Oracle Database Gateway for SQL Server data dictionary support.

#### C.1.1 SQL Server System Tables

SQL Server data dictionary information is stored in the SQL Server database as SQL Server system tables. All SQL Server system tables have names prefixed with "`sys`". The SQL Server system tables define the structure of a database. When you change data definitions, SQL Server reads and modifies the SQL Server system tables to add information about the user tables.

#### C.1.2 Accessing the Gateway Data Dictionary

Accessing a gateway data dictionary table or view is identical to accessing a data dictionary in an Oracle database. You issue a SQL `SELECT` statement specifying a database link. The Oracle database data dictionary view and column names are used to access the gateway data dictionary in an Oracle database. Synonyms of supported views are also acceptable. For example, the following statement queries the data dictionary table `ALL_CATALOG` to retrieve all table names in the SQL Server database:

    SQL> SELECT * FROM "ALL_CATALOG"@MSQL;

When a data dictionary access query is issued, the gateway:

1.  Maps the requested table, view, or synonym to one or more SQL Server system table names. The gateway translates all data dictionary column names to their corresponding SQL Server column names within the query. If the mapping involves one SQL Server system table, the gateway translates the requested table name to its corresponding SQL Server system table name within the query. If the mapping involves multiple SQL Server system tables, the gateway constructs a join in the query using the translated SQL Server system table names.
2.  Sends the translated query to SQL Server.
3.  Might convert the retrieved SQL Server data to give it the appearance of the Oracle database data dictionary table.
4.  Passes the data dictionary information from the translated SQL Server system table to the Oracle database.
    **Note:**

    The values returned when querying the gateway data dictionary might not be the same as the ones returned by the Oracle SQL\*Plus `DESCRIBE` command.

#### C.1.3 Direct Queries to SQL Server Tables

Queries issued directly to individual SQL Server system tables are allowed but they return different results because the SQL Server system table column names differ from those of the data dictionary view. Also, certain columns in an SQL Server system table cannot be used in data dictionary processing.

#### C.1.4 Supported Views and Tables

The gateway supports the following views and tables:

|                     |                     |
|---------------------|---------------------|
| `ALL_CATALOG`       | `ALL_COL_COMMENTS`  |
| `ALL_CONS_COLUMNS`  | `ALL_CONSTRAINTS`   |
| `ALL_IND_COLUMNS`   | `ALL_INDEXES`       |
| `ALL_OBJECTS`       | `ALL_TAB_COLUMNS`   |
| `ALL_TAB_COMMENTS`  | `ALL_TABLES`        |
| `ALL_USERS`         | `ALL_VIEWS`         |
| `DBA_CATALOG`       | `DBA_COL_COMMENTS`  |
| `DBA_OBJECTS`       | `DBA_TAB_COLUMNS`   |
| `DBA_TAB_COMMENTS`  | `DBA_TABLES`        |
| `DICT_COLUMNS`      | `DICTIONARY`        |
| `DUAL`              | `TABLE_PRIVILEGES`  |
| `USER_CATALOG`      | `USER_COL_COMMENTS` |
| `USER_CONS_COLUMNS` | `USER_CONSTRAINTS`  |
| `USER_IND_COLUMNS`  | `USER_INDEXES`      |
| `USER_OBJECTS`      | `USER_TAB_COLUMNS`  |
| `USER_TAB_COMMENTS` | `USER_TABLES`       |
| `USER_USERS`        | `USER_VIEWS`        |

No other Oracle database data dictionary tables or views are supported. If you use a view not on the list, you will receive the Oracle database error code for no more rows available.

Queries through the gateway of any data dictionary table or view beginning with ALL\_ can return rows from the SQL Server database even when access privileges for those SQL Server objects have not been granted. When querying an Oracle database with the Oracle data dictionary, rows are returned only for those objects you are permitted to access.

### C.2 Data Dictionary Mapping

The tables in this section list Oracle data dictionary view names and the equivalent SQL Server system tables used. A plus sign (+) indicates that a join operation is involved.

Table C-1 Oracle Data Dictionary View Names and SQL Server Equivalents

| View Name           | SQL Server System Table Name                                                  |
|:--------------------|:------------------------------------------------------------------------------|
| `ALL_CATALOG`       | `sysusers` + `sysobjects`                                                     |
| `ALL_COL_COMMENTS`  | `sysusers `+ `sysobjects` + `syscolumns`                                      |
| `ALL_CONS_COLUMNS`  | `sp_pkeys` + `sp_fkeys`                                                       |
| `ALL_CONSTRAINTS`   | `sysusers` + `sysobjects` + `sysindexes` + `sysconstraints` + `sysreferences` |
| `ALL_IND_COLUMNS`   | `sysusers` + `sysindexes` + `syscolumns`                                      |
| `ALL_INDEXES`       | `sysusers` + `sysindexes` + `sysobjects`                                      |
| `ALL_OBJECTS`       | `sysusers` + `sysobjects` + `sysindexes`                                      |
| `ALL_TAB_COLUMNS`   | `sysusers` + `sysobjects` + `syscolumns`                                      |
| `ALL_TAB_COMMENTS`  | `sysusers` + `sysobjects`                                                     |
| `ALL_TABLES`        | `sysusers` + `sysobjects`                                                     |
| `ALL_USERS`         | `sysusers`                                                                    |
| `ALL_VIEWS`         | `sysusers` + `sysobjects` + `syscomments`                                     |
| `DBA_CATALOG`       | `sysusers` + `sysobjects`                                                     |
| `DBA_COL_COMMENTS`  | `sysusers` + `sysobjects` + `syscolumns`                                      |
| `DBA_OBJECTS`       | `sysusers` + `sysobjects` + `sysindexes`                                      |
| `DBA_TABLES`        | `sysusers` + `sysobjects`                                                     |
| `DBA_TAB_COLUMNS`   | `sysusers` + `sysobjects` + `syscolumns`                                      |
| `DBA_TAB_COMMENTS`  | `sysusers` + `sysobjects`                                                     |
| `DICT_COLUMNS`      | `sysobjects` + `syscolumns`                                                   |
| `DICTIONARY`        | `sysobjects`                                                                  |
| `DUAL`              | `sysusers`                                                                    |
| `TABLE_PRIVILEGES`  | `sysprotects` + `sysusers` + `sysobjects`                                     |
| `USER_CATALOG`      | `sysusers` + `sysobjects`                                                     |
| `USER_COL_COMMENTS` | `sysusers` + `sysobjects` + `syscolumns`                                      |
| `USER_CONS_COLUMNS` | `sp_pkeys` + `sp_fkeys`                                                       |
| `USER_CONSTRAINTS`  | `sysusers` + `sysobjects` + `sysindexes` + `sysconstraints` + `sysreferences` |
| `USER_IND_COLUMNS`  | `sysusers` + `sysindexes` + `syscolumns`                                      |
| `USER_INDEXES`      | `sysusers` + `sysindexes` + `sysobjects`                                      |
| `USER_OBJECTS`      | `sysusers` + `sysobjects` + `sysindexes`                                      |
| `USER_TAB_COLUMNS`  | `sysusers` + `sysobjects` + `syscolumns`                                      |
| `USER_TAB_COMMENTS` | `sysusers` + `sysobjects`                                                     |
| `USER_TABLES`       | `sysusers` + `sysobjects`                                                     |
| `USER_USERS`        | `sysusers`                                                                    |
| `USER_VIEWS`        | `sysusers` + `sysobjects` + `syscomments`                                     |

#### C.2.1 Default Column Values

There is a minor difference between the gateway data dictionary and a typical Oracle database data dictionary. The Oracle database columns that are missing in an SQL Server system table are filled with zeros, spaces, null values, not-applicable values (N.A.), or default values, depending on the column type.

### C.3 Gateway Data Dictionary Descriptions

The gateway data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

They are described here with information retrieved by an Oracle SQL\*Plus `DESCRIBE` command. The values in the `Null?` column might differ from the Oracle database data dictionary tables and views. Any default value is shown to the right of an item, but this is not information returned by `DESCRIBE`.

**Note:**

The column width of some columns in the translated data dictionary tables would be different when the gateway connects to a SQL Server Version 7.0 database.

### C.4 ALL_CATALOG

Table C-2 ALL_CATALOG

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(256)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(256)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |

### C.5 ALL_COL_COMMENTS

Table C-3 ALL_COL_COMMENTS

| Name          | Type            | Value |
|:--------------|:----------------|:------|
| `OWNER`       | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`  | `VARCHAR2(256)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(256)` | \-    |
| `COMMENTS`    | `VARCHAR2(1)`   | \-    |

### C.6 ALL_CONS_COLUMNS

Table C-4 ALL_CONS_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `OWNER`           | `VARCHAR2(256)` | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(256)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(256)` | \-    |
| `POSITION`        | `NUMBER(5)`     | \-    |

### C.7 ALL_CONSTRAINTS

Table C-5 ALL_CONSTRAINTS

| Name                | Type            | Value                            |
|:--------------------|:----------------|:---------------------------------|
| `OWNER`             | `VARCHAR2(256)` | \-                               |
| `CONSTRAINT_NAME`   | `VARCHAR2(256)` | \-                               |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`   | "`C`" or "`P`" or "`R`" or "`U`" |
| `TABLE_NAME`        | `VARCHAR2(256)` | \-                               |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`   | `NULL`                           |
| `R_OWNER`           | `VARCHAR2(256)` | \-                               |
| `R_CONSTRAINT_NAME` | `VARCHAR2(256)` | \-                               |
| `DELETE_RULE`       | `VARCHAR2(1)`   | `NULL`                           |
| `STATUS`            | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRABLE`        | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRED`          | `VARCHAR2(1)`   | `NULL`                           |
| `VALIDATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `GENERATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `BAD`               | `VARCHAR2(1)`   | `NULL`                           |
| `RELY`              | `VARCHAR2(1)`   | `NULL`                           |
| `LAST_CHANGE`       | `DATE`          | \-                               |

### C.8 ALL_IND_COLUMNS

Table C-6 ALL_IND_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `INDEX_OWNER`     | `VARCHAR2(256)` | \-    |
| `INDEX_NAME`      | `VARCHAR2(256)` | \-    |
| `TABLE_OWNER`     | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(256)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(256)` | \-    |
| `COLUMN_POSITION` | `NUMBER(3)`     | \-    |
| `COLUMN_LENGTH`   | `NUMBER`        | \-    |
| `Char_LENGTH`     | `NUMBER`        | \-    |
| `DESCEND`         | `VARCHAR2(4)`   | \-    |

### C.9 ALL_INDEXES

Table C-7 ALL_INDEXES

| Name                      | Type            | Value                    |
|:--------------------------|:----------------|:-------------------------|
| `OWNER`                   | `VARCHAR2(256)` | \-                       |
| `INDEX_NAME`              | `VARCHAR2(256)` | \-                       |
| `INDEX_TYPE`              | `VARCHAR2(1)`   | `NULL`                   |
| `TABLE_OWNER`             | `VARCHAR2(256)` | \-                       |
| `TABLE_NAME`              | `VARCHAR2(256)` | \-                       |
| `TABLE_TYPE`              | `VARCHAR(7)`    | "`TABLE`" or "`CLUSTER`" |
| `UNIQUENESS`              | `VARCHAR2(1)`   | `NULL`                   |
| `COMPRESSION`             | `VARCHAR2(1)`   | `NULL`                   |
| `PREFIX_LENGTH`           | `NUMBER`        | `0`                      |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`   | `NULL`                   |
| `INI_TRANS`               | `NUMBER`        | `0`                      |
| `MAX_TRANS`               | `NUMBER`        | `0`                      |
| `INITIAL_EXTENT`          | `NUMBER`        | `0`                      |
| `NEXT_EXTENT`             | `NUMBER`        | `0`                      |
| `MIN_EXTENTS`             | `NUMBER`        | `0`                      |
| `MAX_EXTENTS`             | `NUMBER`        | `0`                      |
| `PCT_INCREASE`            | `NUMBER`        | `0`                      |
| `PCT_THRESHOLD`           | `NUMBER`        | `0`                      |
| `INCLUDE_COLUMN`          | `NUMBER`        | `0`                      |
| `FREELISTS`               | `NUMBER`        | `0`                      |
| `FREELIST_GROUPS`         | `NUMBER`        | `0`                      |
| `PCT_FREE`                | `NUMBER`        | `0`                      |
| `LOGGING`                 | `VARCHAR2(1)`   | `NULL`                   |
| `BLEVEL`                  | `NUMBER`        | `0`                      |
| `LEAF_BLOCKS`             | `NUMBER`        | `0`                      |
| `DISTINCT_KEYS`           | `NUMBER`        | `0`                      |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`        | `0`                      |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`        | `0`                      |
| `CLUSTERING_FACTOR`       | `NUMBER`        | `0`                      |
| `STATUS`                  | `VARCHAR2(1)`   | `NULL`                   |
| `NUM_ROWS`                | `NUMBER`        | `0`                      |
| `SAMPLE_SIZE`             | `NUMBER`        | `0`                      |
| `LAST_ANALYZED`           | `DATE`          | `NULL`                   |
| `DEGREE`                  | `VARCHAR2(1)`   | `NULL`                   |
| `INSTANCES`               | `VARCHAR2(1)`   | `NULL`                   |
| `PARTITIONED`             | `VARCHAR2(1)`   | `NULL`                   |
| `TEMPORARY`               | `VARCHAR2(1)`   | `NULL`                   |
| `GENERATED`               | `VARCHAR2(1)`   | `NULL`                   |
| `SECONDARY`               | `VARCHAR2(1)`   | `NULL`                   |
| `BUFFER_POOL`             | `VARCHAR2(1)`   | `NULL`                   |
| `USER_STATS`              | `VARCHAR2(1)`   | `NULL`                   |
| `DURATION`                | `VARCHAR2(1)`   | `NULL`                   |
| `PCT_DIRECT_ACCESS`       | `NUMBER`        | `0`                      |
| `ITYP_OWNER`              | `VARCHAR2(1)`   | `NULL`                   |
| `ITYP_NAME`               | `VARCHAR2(1)`   | `NULL`                   |
| `PARAMETERS`              | `VARCHAR2(1)`   | `NULL`                   |
| `GLOBAL_STATS`            | `VARCHAR2(1)`   | `NULL`                   |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`   | `NULL`                   |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`   | `NULL`                   |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`   | `NULL`                   |

### C.10 ALL_OBJECTS

Table C-8 ALL_OBJECTS

| Name             | Type            | Value                                               |
|:-----------------|:----------------|:----------------------------------------------------|
| `OWNER`          | `VARCHAR2(256)` | \-                                                  |
| `OBJECT_NAME`    | `VARCHAR2(256)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`        | \-                                                  |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                  |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                  |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                              |
| `STATUS`         | `VARCHAR2(5)`   | "`VALID`"                                           |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                              |

### C.11 ALL_TAB_COLUMNS

Table C-9 ALL_TAB_COLUMNS

| Name                  | Type            | Value          |
|:----------------------|:----------------|:---------------|
| `OWNER`               | `VARCHAR2(256)` | \-             |
| `TABLE_NAME`          | `VARCHAR2(256)` | \-             |
| `COLUMN_NAME`         | `VARCHAR2(256)` | \-             |
| `DATA_TYPE`           | `VARCHAR2(9)`   | \-             |
| `DATA_TYPE_MOD`       | `VARCHAR2(1)`   | `NULL`         |
| `DATA_TYPE_OWNER`     | `VARCHAR2(1)`   | `NULL`         |
| `DATA_LENGTH`         | `NUMBER`        | \-             |
| `DATA_PRECISION`      | `NUMBER`        | \-             |
| `DATA_SCALE`          | `NUMBER`        | \-             |
| `NULLABLE`            | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `COLUMN_ID`           | `NUMBER(5)`     | \-             |
| `DEFAULT_LENGTH`      | `NUMBER`        | `0`            |
| `DATA_DEFAULT`        | `VARCHAR2(1)`   | `NULL`         |
| `NUM_DISTINCT`        | `NUMBER`        | `0`            |
| `LOW_VALUE`           | `NUMBER`        | `0`            |
| `HIGH_VALUE`          | `NUMBER`        | `0`            |
| `DENSITY`             | `NUMBER`        | `0`            |
| `NUM_NULLS`           | `NUMBER`        | `0`            |
| `NUM_BUCKETS`         | `NUMBER`        | `0`            |
| `LAST_ANALYZED`       | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`         | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`  | `VARCHAR2(1)`   | `NULL`         |
| `CHAR_COL_DEC_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`        | `VARCHAR2(1)`   | `NULL`         |
| `USER_STATS`          | `VARCHAR2(1)`   | `NULL`         |
| `AVG_COL_LEN`         | `NUMBER`        | `0`            |
| `CHAR_LENGTH`         | `NUMBER`        |                |
| `CHAR_USED`           | `VARCHAR2(1)`   |                |
| `V80_FMT_IMAGE`       | `VARCHAR2(1)`   |                |
| `DATA_UPGRADED`       | `VARCHAR2(1)`   |                |
| `HISTOGRAM`           | `VARCHAR2(1)`   |                |

### C.12 ALL_TAB_COMMENTS

Table C-10 ALL_TAB_COMMENTS

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(256)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(256)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`   | `NULL`                |

### C.13 ALL_TABLES

Table C-11 ALL_TABLES

| Name                        | Type            | Value  |
|:----------------------------|:----------------|:-------|
| `OWNER`                     | `VARCHAR2(256)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(256)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL` |
| `PCT_FREE`                  | `NUMBER`        | `0`    |
| `PCT_USED`                  | `NUMBER`        | `0`    |
| `INI_TRANS`                 | `NUMBER`        | `0`    |
| `MAX_TRANS`                 | `NUMBER`        | `0`    |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`    |
| `NEXT_EXTENT`               | `NUMBER`        | `0`    |
| `MIN_EXTENTS`               | `NUMBER`        | `0`    |
| `MAX_EXTENTS`               | `NUMBER`        | `0`    |
| `PCT_INCREASE`              | `NUMBER`        | `0`    |
| `FREELISTS`                 | `NUMBER`        | `0`    |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`    |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL` |
| `NUM_ROWS`                  | `NUMBER`        | `0`    |
| `BLOCKS`                    | `NUMBER`        | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`    |
| `AVG_SPACE`                 | `NUMBER`        | `0`    |
| `CHAIN_CNT`                 | `NUMBER`        | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`    |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL` |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL` |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`    |
| `LAST_ANALYZED`             | `DATE`          | `NULL` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL` |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL` |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL` |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL` |
| `DURATION`                  | `VARHCAR2(1)`   | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL` |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL` |

### C.14 ALL_USERS

Table C-12 ALL_USERS

| Name       | Type            | Value |
|:-----------|:----------------|:------|
| `USERNAME` | `VARCHAR2(256)` | \-    |
| `USER_ID`  | `NUMBER(10)`    | \-    |
| `CREATED`  | `DATE`          | \-    |

### C.15 ALL_VIEWS

Table C-13 ALL_VIEWS

| Name               | Type            | Value |
|:-------------------|:----------------|:------|
| `OWNER`            | `VARCHAR2(256)` | \-    |
| `VIEW_NAME`        | `VARCHAR2(256)` | \-    |
| `TEXT_LENGTH`      | `NUMBER`        | `0`   |
| `TEXT`             | `VARCHAR2(1)`   | \-    |
| `TYPE_TEXT_LENGTH` | `NUMBER`        | `0`   |
| `TYPE_TEXT`        | `VARCHAR2(1)`   | \-    |
| `OID_TEXT_LENGTH`  | `NUMBER`        | `0`   |
| `OID_TEXT`         | `VARCHAR2(1)`   | \-    |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(1)`   | \-    |
| `VIEW_TYPE`        | `VARCHAR2(1)`   | \-    |

### C.16 DBA_CATALOG

Table C-14 DBA_CATALOG

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(256)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(256)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |

### C.17 DBA_COL_COMMENTS

Table C-15 DBA_COL_COMMENTS

| Name          | Type            | Value  |
|:--------------|:----------------|:-------|
| `OWNER`       | `VARCHAR2(256)` | \-     |
| `TABLE_NAME`  | `VARCHAR2(256)` | \-     |
| `COLUMN_NAME` | `VARCHAR2(256)` | \-     |
| `COMMENTS`    | `VARCHAR2(1)`   | `NULL` |

### C.18 DBA_OBJECTS

Table C-16 DBA_OBJECTS

| Name             | Type            | Value                                               |
|:-----------------|:----------------|:----------------------------------------------------|
| `OWNER`          | `VARCHAR2(256)` | \-                                                  |
| `OBJECT_NAME`    | `VARCHAR2(256)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`        | \-                                                  |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                  |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                  |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                              |
| `STATUS`         | `VARCHAR2(5)`   | `NULL`                                              |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                              |

### C.19 DBA_TAB_COLUMNS

Table C-17 DBA_TAB_COLUMNS

| Name                  | Type            | Value          |
|:----------------------|:----------------|:---------------|
| `OWNER`               | `VARCHAR2(256)` | \-             |
| `TABLE_NAME`          | `VARCHAR2(256)` | \-             |
| `COLUMN_NAME`         | `VARCHAR2(256)` | \-             |
| `DATA_TYPE`           | `VARCHAR2(9)`   | \-             |
| `DATA_TYPE_MOD`       | `VARCHAR2(1)`   | `NULL`         |
| `DATA_TYPE_OWNER`     | `VARCHAR2(1)`   | `NULL`         |
| `DATA_LENGTH`         | `NUMBER`        | \-             |
| `DATA_PRECISION`      | `NUMBER`        | \-             |
| `DATA_SCALE`          | `NUMBER`        | \-             |
| `NULLABLE`            | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `COLUMN_ID`           | `NUMBER(5)`     | \-             |
| `DEFAULT_LENGTH`      | `NUMBER`        | `0`            |
| `DATA_DEFAULT`        | `VARCHAR2(1)`   | `NULL`         |
| `NUM_DISTINCT`        | `NUMBER`        | `0`            |
| `LOW_VALUE`           | `NUMBER`        | `0`            |
| `HIGH_VALUE`          | `NUMBER`        | `0`            |
| `DENSITY`             | `NUMBER`        | `0`            |
| `NUM_NULLS`           | `NUMBER`        | `0`            |
| `NUM_BUCKETS`         | `NUMBER`        | `0`            |
| `LAST_ANALYZED`       | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`         | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`  | `VARCHAR2(1)`   | `NULL`         |
| `CHAR_COL_DEC_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`        | `VARCHAR2(1)`   | `NULL`         |
| `USER_STATS`          | `VARCHAR2(1)`   | `NULL`         |
| `AVG_COL_LEN`         | `NUMBER`        | `0`            |

### C.20 DBA_TAB_COMMENTS

Table C-18 DBA_TAB_COMMENTS

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(256)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(256)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`   | `NULL`                |

### C.21 DBA_TABLES

Table C-19 DBA_TABLES

| Name                        | Type            | Value  |
|:----------------------------|:----------------|:-------|
| `OWNER`                     | `VARCHAR2(256)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(256)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL` |
| `PCT_FREE`                  | `NUMBER`        | `0`    |
| `PCT_USED`                  | `NUMBER`        | `0`    |
| `INI_TRANS`                 | `NUMBER`        | `0`    |
| `MAX_TRANS`                 | `NUMBER`        | `0`    |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`    |
| `NEXT_EXTENT`               | `NUMBER`        | `0`    |
| `MIN_EXTENTS`               | `NUMBER`        | `0`    |
| `MAX_EXTENTS`               | `NUMBER`        | `0`    |
| `PCT_INCREASE`              | `NUMBER`        | `0`    |
| `FREELISTS`                 | `NUMBER`        | `0`    |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`    |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL` |
| `NUM_ROWS`                  | `NUMBER`        | `0`    |
| `BLOCKS`                    | `NUMBER`        | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`    |
| `AVG_SPACE`                 | `NUMBER`        | `0`    |
| `CHAIN_CNT`                 | `NUMBER`        | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`    |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL` |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL` |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`    |
| `LAST_ANALYZED`             | `DATE`          | `NULL` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL` |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL` |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL` |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL` |
| `DURATION`                  | `VARHCAR2(1)`   | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL` |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL` |

### C.22 DICT_COLUMNS

Table C-20 DICT_COLUMNS

| Name          | Type            | Value  |
|:--------------|:----------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(256)` | \-     |
| `COLUMN_NAME` | `VARCHAR2(256)` | \-     |
| `COMMENTS`    | `VARCHAR2(1)`   | `NULL` |

### C.23 DICTIONARY

Table C-21 DICTIONARY

| Name         | Type            | Value |
|:-------------|:----------------|:------|
| `TABLE_NAME` | `VARCHAR2(256)` | \-    |
| `COMMENTS`   | `VARCHAR2(1)`   | \-    |

### C.24 DUAL

Table C-22 DUAL

| Name    | Type          | Value |
|:--------|:--------------|:------|
| `DUMMY` | `VARCHAR2(1)` | "`X`" |

### C.25 TABLE_PRIVILEGES

Table C-23 TABLE_PRIVILEGES

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `GRANTEE`         | `VARCHAR2(256)` | \-    |
| `OWNER`           | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(256)` | \-    |
| `GRANTOR`         | `VARCHAR2(256)` | \-    |
| `SELECT_PRIV`     | `VARCHAR2(1)`   | "`Y`" |
| `INSERT_PRIV`     | `VARCHAR2(1)`   | "`A`" |
| `DELETE_PRIV`     | `VARCHAR2(1)`   | "`Y`" |
| `UPDATE_PRIV`     | `VARCHAR2(1)`   | "`A`" |
| `REFERENCES_PRIV` | `VARCHAR2(1)`   | "`A`" |
| `ALTER_PRIV`      | `VARCHAR2(1)`   | "`Y`" |
| `INDEX_PRIV`      | `VARCHAR2(1)`   | "`Y`" |
| `CREATED`         | `DATE`          | \-    |

### C.26 USER_CATALOG

Table C-24 USER_CATALOG

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(256)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |

### C.27 USER_COL_COMMENTS

Table C-25 USER_COL_COMMENTS

| Name          | Type            | Value  |
|:--------------|:----------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(256)` | \-     |
| `COLUMN_NAME` | `VARCHAR2(256)` | \-     |
| `COMMENTS`    | `VARCHAR2(1)`   | `NULL` |

### C.28 USER_CONS_COLUMNS

Table C-26 USER_CONS_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `OWNER`           | `VARCHAR2(30)`  | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(256)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(256)` | \-    |
| `POSITION`        | `NUMBER(5)`     | \-    |

### C.29 USER_CONSTRAINTS

Table C-27 USER_CONSTRAINTS

| Name                | Type            | Value                            |
|:--------------------|:----------------|:---------------------------------|
| `OWNER`             | `VARCHAR2(256)` | \-                               |
| `CONSTRAINT_NAME`   | `VARCHAR2(256)` | \-                               |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`   | "`R`" or "`P`" or "`U`" or "`C`" |
| `TABLE_NAME`        | `VARCHAR2(256)` | \-                               |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`   | `NULL`                           |
| `R_OWNER`           | `VARCHAR2(256)` | \-                               |
| `R_CONSTRAINT_NAME` | `VARCHAR2(256)` | \-                               |
| `DELETE_RULE`       | `VARCHAR2(1)`   | `NULL`                           |
| `STATUS`            | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRABLE`        | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRED`          | `VARCHAR2(1)`   | `NULL`                           |
| `VALIDATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `GENERATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `BAD`               | `VARCHAR2(1)`   | `NULL`                           |
| `RELY`              | `VARCHAR2(1)`   | `NULL`                           |
| `LAST_CHANGE`       | `DATE`          | \-                               |

### C.30 USER_IND_COLUMNS

Table C-28 USER_IND_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `INDEX_NAME`      | `VARCHAR2(256)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(256)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(256)` | \-    |
| `COLUMN_POSITION` | `NUMBER(3)`     | \-    |
| `COLUMN_LENGTH`   | `NUMBER`        | \-    |
| `CHAR_LENGTH`     | `NUMBER`        | \-    |
| `DESCEND`         | `VARCHAR2(4)`   | \-    |

### C.31 USER_INDEXES

Table C-29 USER_INDEXES

| Name                      | Type            | Value                    |
|:--------------------------|:----------------|:-------------------------|
| `INDEX_NAME`              | `VARCHAR2(256)` | \-                       |
| `INDEX_TYPE`              | `VARCHAR2(1)`   | `NULL`                   |
| `TABLE_OWNER`             | `VARCHAR2(256)` | \-                       |
| `TABLE_NAME`              | `VARCHAR2(256)` | \-                       |
| `TABLE_TYPE`              | `VARCHAR2(7)`   | "`TABLE`" or "`CLUSTER`" |
| `UNIQUENESS`              | `VARCHAR2(1)`   | `NULL`                   |
| `COMPRESSION`             | `VARCHAR2(1)`   | `NULL`                   |
| `PREFIX_LENGTH`           | `NUMBER`        | `0`                      |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`   | `NULL`                   |
| `INI_TRANS`               | `NUMBER`        | `0`                      |
| `MAX_TRANS`               | `NUMBER`        | `0`                      |
| `INITIAL_EXTENT`          | `NUMBER`        | `0`                      |
| `NEXT_EXTENT`             | `NUMBER`        | `0`                      |
| `MIN_EXTENTS`             | `NUMBER`        | `0`                      |
| `MAX_EXTENTS`             | `NUMBER`        | `0`                      |
| `PCT_INCREASE`            | `NUMBER`        | `0`                      |
| `PCT_THRESHOLD`           | `NUMBER`        | `0`                      |
| `INCLUDE_COLUMN`          | `NUMBER`        | `0`                      |
| `FREELISTS`               | `NUMBER`        | `0`                      |
| `FREELIST_GROUPS`         | `NUMBER`        | `0`                      |
| `PCT_FREE`                | `NUMBER`        | `0`                      |
| `LOGGING`                 | `VARCHAR2(1)`   | `NULL`                   |
| `BLEVEL`                  | `NUMBER`        | `0`                      |
| `LEAF_BLOCKS`             | `NUMBER`        | `0`                      |
| `DISTINCT_KEYS`           | `NUMBER`        | `0`                      |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`        | `0`                      |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`        | `0`                      |
| `CLUSTERING_FACTOR`       | `NUMBER`        | `0`                      |
| `STATUS`                  | `VARCHAR2(1)`   | `NULL`                   |
| `NUM_ROWS`                | `NUMBER`        | `0`                      |
| `SAMPLE_SIZE`             | `NUMBER`        | `0`                      |
| `LAST_ANALYZED`           | `DATE`          | `NULL`                   |
| `DEGREE`                  | `VARCHAR2(1)`   | `NULL`                   |
| `INSTANCES`               | `VARCHAR2(1)`   | `NULL`                   |
| `PARTITIONED`             | `VARCHAR2(1)`   | `NULL`                   |
| `TEMPORARY`               | `VARCHAR2(1)`   | `NULL`                   |
| `GENERATED`               | `VARCHAR2(1)`   | `NULL`                   |
| `SECONDARY`               | `VARCHAR2(1)`   | `NULL`                   |
| `BUFFER_POOL`             | `VARCHAR2(1)`   | `NULL`                   |
| `USER_STATS`              | `VARCHAR2(1)`   | `NULL`                   |
| `DURATION`                | `VARHCAR2(1)`   | `NULL`                   |
| `PCT_DIRECT_ACCESS`       | `NUMBER`        | `0`                      |
| `ITYP_OWNER`              | `VARCHAR2(1)`   | `NULL`                   |
| `ITYP_NAME`               | `VARCHAR2(1)`   | `NULL`                   |
| `PARAMETERS`              | `VARCHAR2(1)`   | `NULL`                   |
| `GLOBAL_STATS`            | V`ARCHAR2(1)`   | `NULL`                   |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`   | `NULL`                   |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`   | `NULL`                   |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`   | `NULL`                   |

### C.32 USER_OBJECTS

Table C-30 USER_OBJECTS

| Name             | Type            | Value                                               |
|:-----------------|:----------------|:----------------------------------------------------|
| `OBJECT_NAME`    | `VARCHAR2(256)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`        | \-                                                  |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                  |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                  |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                              |
| `STATUS`         | `VARCHAR2(5)`   | "`VALID`"                                           |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                              |

### C.33 USER_TAB_COLUMNS

Table C-31 USER_TAB_COLUMNS

| Name                   | Type            | Value          |
|:-----------------------|:----------------|:---------------|
| `TABLE_NAME`           | `VARCHAR2(256)` | \-             |
| `COLUMN_NAME`          | `VARCHAR2(256)` | \-             |
| `DATA_TYPE`            | `VARCHAR2(9)`   | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`   | `NULL`         |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`   | `NULL`         |
| `DATA_LENGTH`          | `NUMBER`        | \-             |
| `DATA_PRECISION`       | `NUMBER`        | \-             |
| `DATA_SCALE`           | `NUMBER`        | \-             |
| `NULLABLE`             | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER(5)`     | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`        | `0`            |
| `DATA_DEFAULT`         | `VARCHAR2(1)`   | `NULL`         |
| `NUM_DISTINCT`         | `NUMBER`        | `0`            |
| `LOW_VALUE`            | `NUMBER`        | `0`            |
| `HIGH_VALUE`           | `NUMBER`        | `0`            |
| `DENSITY`              | `NUMBER`        | `0`            |
| `NUM_NULLS`            | `NUMBER`        | `0`            |
| `NUM_BUCKETS`          | `NUMBER`        | `0`            |
| `LAST_ANALYZED`        | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`   | `NULL`         |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(1)`   | `NULL`         |
| `USER_STATS`           | `VARCHAR2(1)`   | `NULL`         |
| `AVG_COL_LEN`          | `NUMBER`        | `0`            |
| `CHAR_LENGTH`          | `NUMBER`        | `0`            |
| `CHAR_USED`            | `VARCHAR2(1)`   |                |
| `V80_FMT_IMAGE`        | `VARCHAR2(1)`   |                |
| `DATA_UPGRADED`        | `VARCHAR2(1)`   |                |
| `HISTOGRAM`            | `VARCHAR2(1)`   |                |

### C.34 USER_TAB_COMMENTS

Table C-32 USER_TAB_COMMENTS

| Name         | Type              | Value                 |
|:-------------|:------------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(256``)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`     | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`     | `NULL`                |

### C.35 USER_TABLES

Table C-33 USER_TABLES

| Name                        | Type            | Value  |
|:----------------------------|:----------------|:-------|
| `TABLE_NAME`                | `VARCHAR2(256)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL` |
| `PCT_FREE`                  | `NUMBER`        | `0`    |
| `PCT_USED`                  | `NUMBER`        | `0`    |
| `INI_TRANS`                 | `NUMBER`        | `0`    |
| `MAX_TRANS`                 | `NUMBER`        | `0`    |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`    |
| `NEXT_EXTENT`               | `NUMBER`        | `0`    |
| `MIN_EXTENTS`               | `NUMBER`        | `0`    |
| `MAX_EXTENTS`               | `NUMBER`        | `0`    |
| `PCT_INCREASE`              | `NUMBER`        | `0`    |
| `FREELISTS`                 | `NUMBER`        | `0`    |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`    |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL` |
| `NUM_ROWS`                  | `NUMBER`        | `0`    |
| `BLOCKS`                    | `NUMBER`        | `0`    |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`    |
| `AVG_SPACE`                 | `NUMBER`        | `0`    |
| `CHAIN_CNT`                 | `NUMBER`        | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`    |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL` |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL` |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`    |
| `LAST_ANALYZED`             | `DATE`          | `NULL` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL` |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL` |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL` |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL` |
| `DURATION`                  | `VARCHAR2(1)`   | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL` |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL` |

### C.36 USER_USERS

Table C-34 USER_USERS

| Name                          | Type            | Value    |
|:------------------------------|:----------------|:---------|
| `USERNAME`                    | `VARCHAR2(256)` | \-       |
| `USER_ID`                     | `NUMBER(5)`     | \-       |
| `ACCOUNT_STATUS`              | `VARCHAR2(4)`   | "`OPEN`" |
| `LOCK_DATE`                   | `DATE`          | `NULL`   |
| `EXPIRY_DATE`                 | `DATE`          | `NULL`   |
| `DEFAULT_TABLESPACE`          | `VARCHAR2(1)`   | `NULL`   |
| `TEMPORARY_TABLESPACE`        | `VARCHAR2(1)`   | `NULL`   |
| `CREATED`                     | `DATE`          | \-       |
| `INITIAL_RSRC_CONSUMER_GROUP` | `VARCHAR2(1)`   | `NULL`   |
| `EXTERNAL_NAME`               | `VARCHAR2(1)`   | `NULL`   |

### C.37 USER_VIEWS

Table C-35 USER_VIEWS

| Name               | Type            | Value  |
|:-------------------|:----------------|:-------|
| `VIEW_NAME`        | `VARCHAR2(256)` | \-     |
| `TEXT_LENGTH`      | `NUMBER`        | `0`    |
| `TEXT`             | `VARCHAR2(1)`   | \-     |
| `TYPE_TEXT_LENGTH` | `NUMBER`        | `0`    |
| `TYPE_TEXT`        | `VARCHAR2(1)`   | `NULL` |
| `OID_TEXT_LENGTH`  | `NUMBER`        | `0`    |
| `OID_TEXT`         | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE`        | `VARCHAR2(1)`   | `NULL` |
