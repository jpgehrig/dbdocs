The Oracle Database Gateway for Informix translates a query that refers to an Oracle database data dictionary table into a query that retrieves the data from Informix system catalog tables. You perform queries on data dictionary tables over the database link in the same way you query data dictionary tables in the Oracle database. The gateway data dictionary is similar to the Oracle database data dictionary in appearance and use.

Topics:

- Data Dictionary Mapping

- Gateway Data Dictionary Descriptions

### Informix System Catalog Tables

Informix data dictionary information is stored in the Informix database as Informix system catalog tables. All Informix system catalog tables have names prefixed with “`sys`". The Informix system catalog tables define the structure of a database. When you change data definitions, Informix reads and modifies the Informix system catalog tables to add information about the user tables.

### Accessing the Gateway Data Dictionary

Accessing a gateway data dictionary table or view is identical to accessing a data dictionary in an Oracle database. You issue a SQL `SELECT` statement specifying a database link. The Oracle database data dictionary view and column names are used to access the gateway data dictionary in an Oracle database. Synonyms of supported views are also acceptable. For example, the following statement queries the data dictionary table `ALL_CATALOG` to retrieve all table names in the Informix database:

    SQL> SELECT * FROM "ALL_CATALOG"@IFMX;

When a data dictionary access query is issued, the gateway:

1.  Maps the requested table, view, or synonym to one or more Informix system catalog table names. The gateway translates all data dictionary column names to their corresponding Informix column names within the query. If the mapping involves one Informix system catalog table, the gateway translates the requested table name to its corresponding Informix system catalog table name within the query. If the mapping involves multiple Informix system catalog tables, the gateway constructs a join in the query using the translated Informix system catalog table names.
2.  Sends the translated query to Informix.
3.  Might convert the retrieved Informix data to give it the appearance of the Oracle database data dictionary table.
4.  Passes the data dictionary information from the translated Informix system catalog table to the Oracle database.
    **Note:**

    The values returned when querying the gateway data dictionary might not be the same as the ones returned by the Oracle SQL\*Plus `DESCRIBE` command.

### Direct Queries to Informix Tables

Queries issued directly to individual Informix system catalog tables are allowed but they return different results because the Informix system catalog table column names differ from those of the data dictionary view. Also, certain columns in an Informix system catalog table cannot be used in data dictionary processing.

### Supported Views and Tables

The gateway supports the following views and tables:

| Supported Views and Tables | Supported Views and Tables |
|:---------------------------|:---------------------------|
| `ALL_CATALOG`              | `ALL_COL_COMMENTS`         |
| `ALL_COL_PRIVS`            | `ALL_CONS_COLUMNS`         |
| `ALL_CONSTRAINTS`          | `ALL_IND_COLUMNS`          |
| `ALL_INDEXES`              | `ALL_OBJECTS`              |
| `ALL_SYNONYMS`             | `ALL_TAB_COLUMNS`          |
| `ALL_TAB_COMMENTS`         | `ALL_TAB_PRIVS`            |
| `ALL_TABLES`               | `ALL_USERS`                |
| `ALL_VIEWS`                | `COLUMN_PRIVILEGES`        |
| `DBA_CATALOG`              | `DBA_COL_COMMENTS`         |
| `DBA_OBJECTS`              | `DBA_TABLES`               |
| `DBA_TAB_COLUMNS`          | `DBA_TAB_COMMENTS`         |
| `DICT_COLUMNS`             | `DICTIONARY`               |
| `DUAL`                     | `TABLE_PRIVILEGES`         |
| `USER_CATALOG`             | `USER_COL_COMMENTS`        |
| `USER_COL_PRIVS`           | `USER_CONS_COLUMNS`        |
| `USER_CONSTRAINTS`         | `USER_IND_COLUMNS`         |
| `USER_INDEXES`             | `USER_OBJECTS`             |
| `USER_SYNONYMS`            | `USER_TAB_COLUMNS`         |
| `USER_TAB_COMMENTS`        | `USER_TAB_PRIVS`           |
| `USER_TABLES`              | `USER_USERS`               |
| `USER_VIEWS`               |                            |

No other Oracle database data dictionary tables or views are supported. If you use a view not on the list, you receive the Oracle database error code for no more rows available.

Queries through the gateway of any data dictionary table or view beginning with `ALL_` can returns rows from the Informix database even when access privileges for those Informix objects have not been granted. When querying an Oracle database with the Oracle data dictionary, rows are returned only for those objects you are permitted to access.

### Data Dictionary Mapping

The tables in this section list Oracle data dictionary view names and the equivalent Informix system catalog tables used. A plus sign (+) indicates that a join operation is involved.

Table C-1 Oracle Data Dictionary View Names and Informix Equivalents

| View Name           | Informix System Catalog Table Name                           |
|:--------------------|:-------------------------------------------------------------|
| `ALL_CATALOG`       | `systables`                                                  |
| `ALL_COL_COMMENTS`  | `systables` +` syscolumns`                                   |
| `ALL_COL_PRIVS`     | `systables` + `syscolumns` + `syscolauth`                    |
| `ALL_CONS_COLUMNS`  | `systables` + `sysconstraints` + `syscolumns` + `sysindexes` |
| `ALL_CONSTRAINTS`   | `systables` + `sysconstraints` + `sysreferences`             |
| `ALL_IND_COLUMNS`   | `systables` + `sysindexes` + `syscolumns`                    |
| `ALL_INDEXES`       | `sysindexes` + `systables`                                   |
| `ALL_OBJECTS`       | `systables` + `sysindexes` + `sysprocedures` + `sysprocplan` |
| `ALL_SYNONYMS`      | `systables` + `syssynonyms` + `syssyntable`                  |
| `ALL_TAB_COLUMNS`   | `systables` + `syscolumns`                                   |
| `ALL_TAB_COMMENTS`  | `systables`                                                  |
| `ALL_TAB_PRIVS`     | `systables` + `systabauth`                                   |
| `ALL_TABLES`        | `systables`                                                  |
| `ALL_USERS`         | `sysusers`                                                   |
| `ALL_VIEWS`         | `systables` + `sysviews`                                     |
| `COLUMN_PRIVILEGES` | `systables` + `syscolauth` + `syscolumns`                    |
| `DBA_CATALOG`       | `systables`                                                  |
| `DBA_COL_COMMENTS`  | `systables` + `syscolumns`                                   |
| `DBA_OBJECTS`       | `systables` + `sysindexes` + `sysprocedures` + `sysprocplan` |
| `DBA_TABLES`        | `systables`                                                  |
| `DBA_TAB_COLUMNS`   | `systables` + `syscolumns`                                   |
| `DBA_TAB_COMMENTS`  | `systables`                                                  |
| `DICT_COLUMNS`      | `systables` + `syscolumns`                                   |
| `DICTIONARY`        | `systables`                                                  |
| `DUAL`              | (Defined in the Gateway)                                     |
| `TABLE_PRIVILEGES`  | `systabauth` + `systables`                                   |
| `USER_CATALOG`      | `systables`                                                  |
| `USER_COL_COMMENTS` | `systables` + `syscolumns`                                   |
| `USER_COL_PRIVS`    | `systables` + `syscolumns` + `syscolauth`                    |
| `USER_CONS_COLUMNS` | `systables` + `sysconstraints` + `syscolumns` + `sysindexes` |
| `USER_CONSTRAINTS`  | `systables` + `sysconstraints` + `sysreferences`             |
| `USER_IND_COLUMNS`  | `systables` + `sysindexes` + `syscolumns`                    |
| `USER_INDEXES`      | `systables` + `sysindexes`                                   |
| `USER_OBJECTS`      | `systables` + `sysindexes` + `sysprocedures` + `sysprocplan` |
| `USER_SYNONYMS`     | `systables` + `syssynonyms` + `syssyntable`                  |
| `USER_TAB_COLUMNS`  | `systables` + `syscolumns`                                   |
| `USER_TAB_COMMENTS` | `systables`                                                  |
| `USER_TAB_PRIVS`    | `systables` + `systabauth`                                   |
| `USER_TABLES`       | `systables`                                                  |
| `USER_USERS`        | `sysusers`                                                   |
| `USER_VIEWS`        | `systables` + `sysviews`                                     |

#### Default Column Values

There is a minor difference between the gateway data dictionary and a typical Oracle database data dictionary. The Oracle database columns that are missing in an Informix system catalog table are filled with zeros, spaces, null values, not-applicable values (N.A.), or default values, depending on the column type.

### Gateway Data Dictionary Descriptions

The gateway data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

They are described here with information retrieved by an Oracle SQL\*Plus `DESCRIBE` command. The values in the Null? column might differ from the Oracle database data dictionary tables and views. Any default value is shown to the right of an item, but this is not information returned by `DESCRIBE`.

### ALL_CATALOG

Table C-2 ALL_CATALOG

| Name         | Type            | Value                                |
|:-------------|:----------------|:-------------------------------------|
| `OWNER`      | `VARCHAR2(32)`  | \-                                   |
| `TABLE_NAME` | `VARCHAR2(128)` | \-                                   |
| `TABLE_TYPE` | `VARCHAR2(7)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" |

### ALL_COL_COMMENTS

Table C-3 ALL_COL_COMMENTS

| Name          | Type            | Value |
|:--------------|:----------------|:------|
| `OWNER`       | `VARCHAR2(32)`  | \-    |
| `TABLE_NAME`  | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(128)` | \-    |
| `COMMENTS`    | `CHAR(1)`       | " "   |

### ALL_COL_PRIVS

Table C-4 ALL_COL_PRIVS

| Name           | Type            | Value                                      |
|:---------------|:----------------|:-------------------------------------------|
| `GRANTOR`      | `VARCHAR2(32)`  | \-                                         |
| `GRANTEE`      | `VARCHAR2(32)`  | \-                                         |
| `TABLE_SCHEMA` | `VARCHAR2(32)`  | \-                                         |
| `TABLE_NAME`   | `VARCHAR2(128)` | \-                                         |
| `COLUMN_NAME`  | `VARCHAR2(128)` | \-                                         |
| `PRIVILEGE`    | `VARCHAR2(10)`  | "`SELECT`" or "`UPDATE`" or "`REFERENCES`" |
| `GRANTABLE`    | `VARCHAR2(3)`   | "`YES`" or "`NO`"                          |

### ALL_CONS_COLUMNS

Table C-5 ALL_CONS_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `OWNER`           | `VARCHAR2(32)`  | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(128)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(128)` | \-    |
| `POSITION`        | `NUMBER(10)`    | `0`   |

### ALL_CONSTRAINTS

Table C-6 ALL_CONSTRAINTS

| Name                | Value                            |
|:--------------------|:---------------------------------|
| `OWNER`             | \-                               |
| `CONSTRAINT_NAME`   | \-                               |
| `CONSTRAINT_TYPE`   | "`R`" or "`P`" or "`U`" or "`C`" |
| `TABLE_NAME`        | \-                               |
| `SEARCH_CONDITION`  | " "                              |
| `R_OWNER`           | " "                              |
| `R_CONSTRAINT_NAME` | " "                              |
| `DELETE_RULE`       | " "                              |
| `STATUS`            | " "                              |
| `DEFERRABLE`        | " "                              |
| `DEFERRED`          | " "                              |
| `VALIDATED`         | " "                              |
| `GENERATED`         | " "                              |
| `BAD`               | " "                              |
| `RELY`              | " "                              |
| `LAST_CHANGE`       | \-                               |

### ALL_IND_COLUMNS

Table C-7 ALL_IND_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `INDEX_OWNER`     | `VARCHAR2(32)`  | \-    |
| `INDEX_NAME`      | `VARCHAR2(128)` | \-    |
| `TABLE_OWNER`     | `VARCHAR2(32)`  | \-    |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(128)` | \-    |
| `COLUMN_POSITION` | `NUMBER(10)`    | `0`   |
| `COLUMN_LENGTH`   | `NUMBER(10)`    | `0`   |
| `DESCEND`         | `CHAR(1)`       | " "   |

### ALL_INDEXES

Table C-8 ALL_INDEXES

| Name                      | Type            | Value                                 |
|:--------------------------|:----------------|:--------------------------------------|
| `OWNER`                   | `VARCHAR2(32)`  | \-                                    |
| `INDEX_NAME`              | `VARCHAR2(128)` | \-                                    |
| `INDEX_TYPE`              | `VARCHAR2(1)`   | `NULL`                                |
| `TABLE_OWNER`             | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`              | `VARCHAR2(128)` | \-                                    |
| `TABLE_TYPE`              | `VARCHAR(5)`    | "`TABLE`"                             |
| `UNIQUENESS`              | `VARCHAR2(9)`   | "`UNIQUE`" or "`NONUNIQUE`"           |
| `COMPRESSION`             | `VARCHAR2(1)`   | `NULL`                                |
| `PREFIX_LENGTH`           | `NUMBER`        | `0`                                   |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`   | `NULL`                                |
| `INI_TRANS`               | `NUMBER`        | `0`                                   |
| `MAX_TRANS`               | `NUMBER`        | `0`                                   |
| `INITIAL_EXTENT`          | `NUMBER`        | `0`                                   |
| `NEXT_EXTENT`             | `NUMBER`        | `0`                                   |
| `MIN_EXTENTS`             | `NUMBER`        | `0`                                   |
| `MAX_EXTENTS`             | `NUMBER`        | `0`                                   |
| `PCT_INCREASE`            | `NUMBER`        | `0`                                   |
| `PCT_THRESHOLD`           | `NUMBER`        | `0`                                   |
| `INCLUDE_COLUMN`          | `NUMBER`        | `0`                                   |
| `FREELISTS`               | `NUMBER`        | `0`                                   |
| `FREELIST_GROUPS`         | `NUMBER`        | `0`                                   |
| `PCT_FREE`                | `NUMBER`        | `0`                                   |
| `LOGGING`                 | `VARCHAR2(1)`   | `NULL`                                |
| `BLEVEL`                  | `NUMBER`        | `0`                                   |
| `LEAF_BLOCKS`             | `NUMBER`        | `0`                                   |
| `DISTINCT_KEYS`           | `NUMBER`        | `0`                                   |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`        | `0`                                   |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`        | `0`                                   |
| `CLUSTERING_FACTOR`       | `NUMBER`        | `0`                                   |
| `STATUS`                  | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_ROWS`                | `NUMBER`        | `0`                                   |
| `SAMPLE_SIZE`             | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`           | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `DEGREE`                  | `VARCHAR2(1)`   | `NULL`                                |
| `INSTANCES`               | `VARCHAR2(1)`   | `NULL`                                |
| `PARTITIONED`             | `VARCHAR2(1)`   | `NULL`                                |
| `TEMPORARY`               | `VARCHAR2(1)`   | `NULL`                                |
| `GENERATED`               | `VARCHAR2(1)`   | `NULL`                                |
| `SECONDARY`               | `VARCHAR2(1)`   | `NULL`                                |
| `BUFFER_POOL`             | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`              | `VARCHAR2(1)`   | `NULL`                                |
| `DURATION`                | `VARCHAR2(1)`   | `NULL`                                |
| `PCT_DIRECT_ACCESS`       | `NUMBER`        | `0`                                   |
| `ITYP_OWNER`              | `VARCHAR2(1)`   | `NULL`                                |
| `ITYP_NAME`               | `VARCHAR2(1)`   | `NULL`                                |
| `PARAMETERS`              | `VARCHAR2(1)`   | `NULL`                                |
| `GLOBAL_STATS`            | `VARCHAR2(1)`   | `NULL`                                |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`   | `NULL`                                |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`   | `NULL`                                |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`   | `NULL`                                |

### ALL_OBJECTS

Table C-9 ALL_OBJECTS

| Name             | Type            | Value                                                              |
|:-----------------|:----------------|:-------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(32)`  | \-                                                                 |
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                                 |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                                             |
| `OBJECT_ID`      | `NUMBER`        | \-                                                                 |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                                |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                                 |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                                 |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `STATUS`         | `VARCHAR2(1)`   | `NULL`                                                             |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                                             |

### ALL_SYNONYMS

Table C-10 ALL_SYNONYMS

| Name           | Type            | Value  |
|:---------------|:----------------|:-------|
| `OWNER`        | `VARCHAR2(32)`  | \-     |
| `SYNONYM_NAME` | `VARCHAR2(128)` | \-     |
| `TABLE_OWNER`  | `VARCHAR2(32)`  | \-     |
| `TABLE_NAME`   | `VARCHAR2(128)` | \-     |
| `DB_LINK`      | `CHAR(1)`       | `NULL` |

### ALL_TAB_COLUMNS

Table C-11 ALL_TAB_COLUMNS

| Name                   | Type            | Value                                 |
|:-----------------------|:----------------|:--------------------------------------|
| `OWNER`                | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`           | `VARCHAR2(128)` | \-                                    |
| `COLUMN_NAME`          | `VARCHAR2(128)` | \-                                    |
| `DATA_TYPE`            | `VARCHAR2(8)`   | \-                                    |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_LENGTH`          | `NUMBER`        | \-                                    |
| `DATA_PRECISION`       | `NUMBER`        | \-                                    |
| `DATA_SCALE`           | `NUMBER`        | \-                                    |
| `NULLABLE`             | `VARCHAR2(1)`   | "`Y`" or "`N`"                        |
| `COLUMN_ID`            | `NUMBER(5)`     | \-                                    |
| `DEFAULT_LENGTH`       | `NUMBER`        | `0`                                   |
| `DATA_DEFAULT`         | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_DISTINCT`         | `NUMBER`        | `0`                                   |
| `LOW_VALUE`            | `NUMBER`        | `0`                                   |
| `HIGH_VALUE`           | `NUMBER`        | `0`                                   |
| `DENSITY`              | `NUMBER`        | `0`                                   |
| `NUM_NULLS`            | `NUMBER`        | `0`                                   |
| `NUM_BUCKETS`          | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`        | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`                                   |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`   | `NULL`                                |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`                                   |
| `GLOBAL_STATS`         | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`           | `VARCHAR2(1)`   | `NULL`                                |
| `AVG_COL_LEN`          | `NUMBER`        | `0`                                   |

### ALL_TAB_COMMENTS

Table C-12 ALL_TAB_COMMENTS

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(32)`  | \-                    |
| `TABLE_NAME` | `VARCHAR2(128)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`   | `NULL`                |

### ALL_TAB_PRIVS

Table C-13 ALL_TAB_PRIVS

| Name           | Type            | Value                                                                                            |
|:---------------|:----------------|:-------------------------------------------------------------------------------------------------|
| `GRANTOR`      | `VARCHAR2(32)`  | \-                                                                                               |
| `GRANTEE`      | `VARCHAR2(32)`  | \-                                                                                               |
| `TABLE_SCHEMA` | `VARCHAR2(32)`  | \-                                                                                               |
| `TABLE_NAME`   | `VARCHAR2(128)` | \-                                                                                               |
| `PRIVILEGE`    | `VARCHAR2(10)`  | "`SELECT`" or "`UPDATE`" or "`INSERT`" or "`DELETE`" or "`INDEX`" or "`ALTER`" or "`REFERENCES`" |
| `GRANTABLE`    | `VARCHAR2 (3)`  | "`YES`"                                                                                          |

### ALL_TABLES

Table C-14 ALL_TABLES

| Name                        | Type            | Value                                 |
|:----------------------------|:----------------|:--------------------------------------|
| `OWNER`                     | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`                | `VARCHAR2(128)` | \-                                    |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL`                                |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL`                                |
| `PCT_FREE`                  | `NUMBER`        | `0`                                   |
| `PCT_USED`                  | `NUMBER`        | `0`                                   |
| `INI_TRANS`                 | `NUMBER`        | `0`                                   |
| `MAX_TRANS`                 | `NUMBER`        | `0`                                   |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`                                   |
| `NEXT_EXTENT`               | `NUMBER`        | `0`                                   |
| `MIN_EXTENTS`               | `NUMBER`        | `0`                                   |
| `MAX_EXTENTS`               | `NUMBER`        | `0`                                   |
| `PCT_INCREASE`              | `NUMBER`        | `0`                                   |
| `FREELISTS`                 | `NUMBER`        | `0`                                   |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`                                   |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL`                                |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_ROWS`                  | `NUMBER(10)`    | \-                                    |
| `BLOCKS`                    | `NUMBER`        | `0`                                   |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`                                   |
| `AVG_SPACE`                 | `NUMBER`        | `0`                                   |
| `CHAIN_CNT`                 | `NUMBER`        | `0`                                   |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`                                   |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`                                   |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`                                   |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL`                                |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL`                                |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL`                                |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL`                                |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`             | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL`                                |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL`                                |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL`                                |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL`                                |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL`                                |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL`                                |
| `DURATION`                  | `VARHCAR2(1)`   | `NULL`                                |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL`                                |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL`                                |

### ALL_USERS

Table C-15 ALL_USERS

| Name       | Type           | Value     |
|:-----------|:---------------|:----------|
| `USERNAME` | `VARCHAR2(32)` | \-        |
| `USER_ID`  | `NUMBER`       | `0`       |
| `CREATED`  | `DATE`         | `SYSDATE` |

### ALL_VIEWS

Table C-16 ALL_VIEWS

| Name               | Type            | Value |
|:-------------------|:----------------|:------|
| `OWNER`            | `VARCHAR2(32)`  | \-    |
| `VIEW_NAME`        | `VARCHAR2(128)` | \-    |
| `TEXT_LENGTH`      | `NUMBER(10)`    | `64`  |
| `TEXT`             | `VARCHAR2(64)`  | \-    |
| `TYPE_TEXT_LENGTH` | `NUMBER(10)`    | `0`   |
| `TYPE_TEXT`        | `CHAR(1)`       | " "   |
| `OID_TEXT_LENGTH`  | `NUMBER(10)`    | `0`   |
| `OID_TEXT`         | `CHAR(1)`       | " "   |
| `VIEW_TYPE_OWNER`  | `CHAR(1)`       | " "   |
| `VIEW_TYPE`        | `CHAR(1)`       | " "   |

### COLUMN_PRIVILEGES

Table C-17 COLUMN_PRIVILEGES

| Name              | Type            | Value     |
|:------------------|:----------------|:----------|
| `GRANTEE`         | `VARCHAR2(32)`  | \-        |
| `OWNER`           | `VARCHAR2(32)`  | \-        |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-        |
| `COLUMN_NAME`     | `VARCHAR2(128)` | \-        |
| `GRANTOR`         | `VARCHAR2(32)`  | \-        |
| `INSERT_PRIV`     | `VARCHAR2(1)`   | "`Y`"     |
| `UPDATE_PRIV`     | `VARCHAR2(1)`   | "`Y`"     |
| `REFERENCES_PRIV` | `VARCHAR2(1)`   | `NULL`    |
| `CREATED`         | `DATE`          | `SYSDATE` |

### DBA_CATALOG

Table C-18 DBA_CATALOG

| Name         | Type            | Value                                |
|:-------------|:----------------|:-------------------------------------|
| `OWNER`      | `VARCHAR2(32)`  | \-                                   |
| `TABLE_NAME` | `VARCHAR2(128)` | \-                                   |
| `TABLE_TYPE` | `VARCHAR2(7)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" |

### DBA_COL_COMMENTS

Table C-19 DBA_COL_COMMENTS

| Name          | Type            | Value |
|:--------------|:----------------|:------|
| `OWNER`       | `VARCHAR2(32)`  | \-    |
| `TABLE_NAME`  | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(128)` | \-    |
| `COMMENTS`    | `CHAR(1)`       | " "   |

### DBA_OBJECTS

Table C-20 DBA_OBJECTS

| Name             | Type            | Value                                                              |
|:-----------------|:----------------|:-------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(32)`  | \-                                                                 |
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                                 |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                                             |
| `OBJECT_ID`      | `NUMBER`        | \-                                                                 |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                                |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                                 |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                                 |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `STATUS`         | `VARCHAR2(1)`   | `NULL`                                                             |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                                             |

### DBA_TAB_COLUMNS

Table C-21 DBA_TAB_COLUMNS

| Name                   | Type            | Value                                 |
|:-----------------------|:----------------|:--------------------------------------|
| `OWNER`                | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`           | `VARCHAR2(128)` | \-                                    |
| `COLUMN_NAME`          | `VARCHAR2(128)` | \-                                    |
| `DATA_TYPE`            | `VARCHAR2(8)`   | \-                                    |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_LENGTH`          | `NUMBER`        | \-                                    |
| `DATA_PRECISION`       | `NUMBER`        | \-                                    |
| `DATA_SCALE`           | `NUMBER`        | \-                                    |
| `NULLABLE`             | `VARCHAR2(1)`   | "`Y`" or "`N`"                        |
| `COLUMN_ID`            | `NUMBER(5)`     | \-                                    |
| `DEFAULT_LENGTH`       | `NUMBER`        | `0`                                   |
| `DATA_DEFAULT`         | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_DISTINCT`         | `NUMBER`        | `0`                                   |
| `LOW_VALUE`            | `NUMBER`        | `0`                                   |
| `HIGH_VALUE`           | `NUMBER`        | `0`                                   |
| `DENSITY`              | `NUMBER`        | `0`                                   |
| `NUM_NULLS`            | `NUMBER`        | `0`                                   |
| `NUM_BUCKETS`          | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`        | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`                                   |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`   | `NULL`                                |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`                                   |
| `GLOBAL_STATS`         | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`           | `VARCHAR2(1)`   | `NULL`                                |
| `AVG_COL_LEN`          | `NUMBER`        | `0`                                   |

### DBA_TAB_COMMENTS

Table C-22 DBA_TAB_COMMENTS

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `OWNER`      | `VARCHAR2(32)`  | \-                    |
| `TABLE_NAME` | `VARCHAR2(128)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`   | `NULL`                |

### DBA_TABLES

Table C-23 DBA_TABLES

| Name                        | Type            | Value                                 |
|:----------------------------|:----------------|:--------------------------------------|
| `OWNER`                     | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`                | `VARCHAR2(128)` | \-                                    |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL`                                |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL`                                |
| `PCT_FREE`                  | `NUMBER`        | `0`                                   |
| `PCT_USED`                  | `NUMBER`        | `0`                                   |
| `INI_TRANS`                 | `NUMBER`        | `0`                                   |
| `MAX_TRANS`                 | `NUMBER`        | `0`                                   |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`                                   |
| `NEXT_EXTENT`               | `NUMBER`        | `0`                                   |
| `MIN_EXTENTS`               | `NUMBER`        | `0`                                   |
| `MAX_EXTENTS`               | `NUMBER`        | `0`                                   |
| `PCT_INCREASE`              | `NUMBER`        | `0`                                   |
| `FREELISTS`                 | `NUMBER`        | `0`                                   |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`                                   |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL`                                |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_ROWS`                  | `NUMBER(10)`    |                                       |
| `BLOCKS`                    | `NUMBER`        | `0`                                   |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`                                   |
| `AVG_SPACE`                 | `NUMBER`        | `0`                                   |
| `CHAIN_CNT`                 | `NUMBER`        | `0`                                   |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`                                   |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`                                   |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`                                   |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL`                                |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL`                                |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL`                                |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL`                                |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`             | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL`                                |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL`                                |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL`                                |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL`                                |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL`                                |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL`                                |
| `DURATION`                  | `VARHCAR2(1)`   | `NULL`                                |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL`                                |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL`                                |

### DICT_COLUMNS

Table C-24 DICT_COLUMNS

| Name          | Type            | Value |
|:--------------|:----------------|:------|
| `TABLE_NAME`  | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME` | `VARCHAR2(128)` | \-    |
| `COMMENTS`    | `VARCHAR2(1)`   | \-    |

### DICTIONARY

Table C-25 DICTIONARY

| Name         | Type            | Value |
|:-------------|:----------------|:------|
| `TABLE_NAME` | `VARCHAR2(128)` | \-    |
| `COMMENTS`   | `CHAR(1)`       | " "   |

### DUAL

Table C-26 DUAL

| Name    | Type          | Value |
|:--------|:--------------|:------|
| `DUMMY` | `VARCHAR2(1)` | "`X`" |

### TABLE_PRIVILEGES

Table C-27 TABLE_PRIVILEGES

| Name              | Type            | Value          |
|:------------------|:----------------|:---------------|
| `GRANTEE`         | `VARCHAR2(32)`  | \-             |
| `OWNER`           | `VARCHAR2(32)`  | \-             |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-             |
| `GRANTOR`         | `VARCHAR2(32)`  | \-             |
| `SELECT_PRIV`     | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `INSERT_PRIV`     | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `DELETE_PRIV`     | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `UPDATE_PRIV`     | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `REFERENCES_PRIV` | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `ALTER_PRIV`      | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `INDEX_PRIV`      | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `CREATED`         | `DATE`          | `SYSDATE`      |

### USER_CATALOG

Table C-28 USER_CATALOG

| Name         | Type            | Value                                |
|:-------------|:----------------|:-------------------------------------|
| `TABLE_NAME` | `VARCHAR2(128)` | \-                                   |
| `TABLE_TYPE` | `VARCHAR2(7)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" |

### USER_COL_COMMENTS

Table C-29 USER_COL_COMMENTS

| Name          | Type            | Value  |
|:--------------|:----------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(128)` | \-     |
| `COLUMN_NAME` | `VARCHAR2(128)` | \-     |
| `COMMENTS`    | `VARCHAR2(1)`   | `NULL` |

### USER_COL_PRIVS

Table C-30 USER_COL_PRIVS

| Name          | Type            | Value                                      |
|:--------------|:----------------|:-------------------------------------------|
| `GRANTOR`     | `VARCHAR2(32)`  | \-                                         |
| `OWNER`       | `VARCHAR2(32)`  | \-                                         |
| `TABLE_NAME`  | `VARCHAR2(128)` | \-                                         |
| `COLUMN_NAME` | `VARCHAR2(128)` | \-                                         |
| `GRANTEE`     | `VARCHAR2(32)`  | \-                                         |
| `PRIVILEGE`   | `VARCHAR2(10)`  | "`SELECT`" or "`UPDATE`" or "`REFERENCES`" |
| `GRANTABLE`   | `VARCHAR2(3)`   | "`YES`" or "`NO`"                          |

### USER_CONS_COLUMNS

Table C-31 USER_CONS_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `OWNER`           | `VARCHAR2(32)`  | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(128)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(128)` | \-    |
| `POSITION`        | `NUMBER`        | `0`   |

### USER_CONSTRAINTS

Table C-32 USER_CONSTRAINTS

| Name                | Type            | Value                            |
|:--------------------|:----------------|:---------------------------------|
| `OWNER`             | `VARCHAR2(32)`  | \-                               |
| `CONSTRAINT_NAME`   | `VARCHAR2(128)` | \-                               |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`   | "`R`" or "`P`" or "`U`" or "`C`" |
| `TABLE_NAME`        | `VARCHAR2(128)` | \-                               |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`   | `NULL`                           |
| `R_OWNER`           | `VARCHAR2(32)`  | `NULL`                           |
| `R_CONSTRAINT_NAME` | `VARCHAR2(128)` | `NULL`                           |
| `DELETE_RULE`       | `VARCHAR2(1)`   | `NULL`                           |
| `STATUS`            | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRABLE`        | `VARCHAR2(1)`   | `NULL`                           |
| `DEFERRED`          | `VARCHAR2(1)`   | `NULL`                           |
| `VALIDATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `GENERATED`         | `VARCHAR2(1)`   | `NULL`                           |
| `BAD`               | `VARCHAR2(1)`   | `NULL`                           |
| `RELY`              | `VARCHAR2(1)`   | `NULL`                           |
| `LAST_CHANGE`       | `DATE`          |                                  |

### USER_IND_COLUMNS

Table C-33 USER_IND_COLUMNS

| Name              | Type            | Value |
|:------------------|:----------------|:------|
| `INDEX_NAME`      | `VARCHAR2(128)` | \-    |
| `TABLE_NAME`      | `VARCHAR2(128)` | \-    |
| `COLUMN_NAME`     | `VARCHAR2(128)` | \-    |
| `COLUMN_POSITION` | `NUMBER`        | `0`   |
| `COLUMN_LENGTH`   | `NUMBER`        | `0`   |
| `DESCEND`         | `VARCHAR2(1)`   | \-    |

### USER_INDEXES

Table C-34 USER_INDEXES

| Name                      | Type            | Value                                 |
|:--------------------------|:----------------|:--------------------------------------|
| `INDEX_NAME`              | `VARCHAR2(128)` | \-                                    |
| `INDEX_TYPE`              | `VARCHAR2(1)`   | `NULL`                                |
| `TABLE_OWNER`             | `VARCHAR2(32)`  | \-                                    |
| `TABLE_NAME`              | `VARCHAR2(128)` | \-                                    |
| `TABLE_TYPE`              | `VARCHAR2(5)`   | "`TABLE`"                             |
| `UNIQUENESS`              | `VARCHAR2(9)`   | "`UNIQUE`" or "`NONUNIQUE`"           |
| `COMPRESSION`             | `VARCHAR2(1)`   | `NULL`                                |
| `PREFIX_LENGTH`           | `NUMBER`        | `0`                                   |
| `TABLESPACE_NAME`         | `VARCHAR2(1)`   | `NULL`                                |
| `INI_TRANS`               | `NUMBER`        | `0`                                   |
| `MAX_TRANS`               | `NUMBER`        | `0`                                   |
| `INITIAL_EXTENT`          | `NUMBER`        | `0`                                   |
| `NEXT_EXTENT`             | `NUMBER`        | `0`                                   |
| `MIN_EXTENTS`             | `NUMBER`        | `0`                                   |
| `MAX_EXTENTS`             | `NUMBER`        | `0`                                   |
| `PCT_INCREASE`            | `NUMBER`        | `0`                                   |
| `PCT_THRESHOLD`           | `NUMBER`        | `0`                                   |
| `INCLUDE_COLUMN`          | `NUMBER`        | `0`                                   |
| `FREELISTS`               | `NUMBER`        | `0`                                   |
| `FREELIST_GROUPS`         | `NUMBER`        | `0`                                   |
| `PCT_FREE`                | `NUMBER`        | `0`                                   |
| `LOGGING`                 | `VARCHAR2(1)`   | `NULL`                                |
| `BLEVEL`                  | `NUMBER`        | `0`                                   |
| `LEAF_BLOCKS`             | `NUMBER`        | `0`                                   |
| `DISTINCT_KEYS`           | `NUMBER`        | \-                                    |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`        | `0`                                   |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`        | `0`                                   |
| `CLUSTERING_FACTOR`       | `NUMBER`        | `0`                                   |
| `STATUS`                  | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_ROWS`                | `NUMBER`        | `0`                                   |
| `SAMPLE_SIZE`             | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`           | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `DEGREE`                  | `VARCHAR2(1)`   | `NULL`                                |
| `INSTANCES`               | `VARCHAR2(1)`   | `NULL`                                |
| `PARTITIONED`             | `VARCHAR2(1)`   | `NULL`                                |
| `TEMPORARY`               | `VARCHAR2(1)`   | `NULL`                                |
| `GENERATED`               | `VARCHAR2(1)`   | `NULL`                                |
| `SECONDARY`               | `VARCHAR2(1)`   | `NULL`                                |
| `BUFFER_POOL`             | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`              | `VARCHAR2(1)`   | `NULL`                                |
| `DURATION`                | `VARHCAR2(1)`   | `NULL`                                |
| `PCT_DIRECT_ACCESS`       | `NUMBER`        | `0`                                   |
| `ITYP_OWNER`              | `VARCHAR2(1)`   | `NULL`                                |
| `ITYP_NAME`               | `VARCHAR2(1)`   | `NULL`                                |
| `PARAMETERS`              | `VARCHAR2(1)`   | `NULL`                                |
| `GLOBAL_STATS`            | `VARCHAR2(1)`   | `NULL`                                |
| `DOMIDX_STATUS`           | `VARCHAR2(1)`   | `NULL`                                |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(1)`   | `NULL`                                |
| `FUNCIDX_STATUS`          | `VARCHAR2(1)`   | `NULL`                                |

### USER_OBJECTS

Table C-35 USER_OBJECTS

| Name             | Type            | Value                                                              |
|:-----------------|:----------------|:-------------------------------------------------------------------|
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                                 |
| `SUBOBJECT_NAME` | `VARCHAR2(1)`   | `NULL`                                                             |
| `OBJECT_ID`      | `NUMBER`        | \-                                                                 |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                                |
| `OBJECT_TYPE`    | `VARCHAR2(9)`   | "`TABLE`" or "`VIEW`" or "`SYNONYM`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | \-                                                                 |
| `LAST_DDL_TIME`  | `DATE`          | \-                                                                 |
| `TIMESTAMP`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `STATUS`         | `VARCHAR2(1)`   | `NULL`                                                             |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                                             |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                                             |

### USER_SYNONYMS

Table C-36 USER_SYNONYMS

| Name           | Type            | Value  |
|:---------------|:----------------|:-------|
| `SYNONYM_NAME` | `VARCHAR2(128)` | \-     |
| `TABLE_OWNER`‘ | `VARCHAR2(32)`  | \-     |
| `TABLE_NAME`   | `VARCHAR2(128)` | \-     |
| `DB_LINK`      | `VARCHAR2(1)`   | `NULL` |

### USER_TAB_COLUMNS

Table C-37 USER_TAB_COLUMNS

| Name                   | Type            | Value                                 |
|:-----------------------|:----------------|:--------------------------------------|
| `TABLE_NAME`           | `VARCHAR2(128)` | \-                                    |
| `COLUMN_NAME`          | `VARCHAR2(128)` | \-                                    |
| `DATA_TYPE`            | `VARCHAR2(8)`   | \-                                    |
| `DATA_TYPE_MOD`        | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_TYPE_OWNER`      | `VARCHAR2(1)`   | `NULL`                                |
| `DATA_LENGTH`          | `NUMBER`        | \-                                    |
| `DATA_PRECISION`       | `NUMBER`        | \-                                    |
| `DATA_SCALE`           | `NUMBER`        | \-                                    |
| `NULLABLE`             | `VARCHAR2(1)`   | "`Y`" or "`N`"                        |
| `COLUMN_ID`            | `NUMBER(5)`     | \-                                    |
| `DEFAULT_LENGTH`       | `NUMBER`        | `0`                                   |
| `DATA_DEFAULT`         | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_DISTINCT`         | `NUMBER`        | `0`                                   |
| `LOW_VALUE`            | `NUMBER`        | `0`                                   |
| `HIGH_VALUE`           | `NUMBER`        | `0`                                   |
| `DENSITY`              | `NUMBER`        | `0`                                   |
| `NUM_NULLS`            | `NUMBER`        | `0`                                   |
| `NUM_BUCKETS`          | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`        | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`                                   |
| `CHARACTER_SET_NAME`   | `VARCHAR2(1)`   | `NULL`                                |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`                                   |
| `GLOBAL_STATS`         | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`           | `VARCHAR2(1)`   | `NULL`                                |
| `AVG_COL_LEN`          | `NUMBER`        | `0`                                   |

### USER_TAB_COMMENTS

Table C-38 USER_TAB_COMMENTS

| Name         | Type            | Value                 |
|:-------------|:----------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(128)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(5)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(1)`   | `NULL`                |

### USER_TAB_PRIVS

Table C-39 USER_TAB_PRIVS

| Name           | Type            | Value                                                                    |
|:---------------|:----------------|:-------------------------------------------------------------------------|
| `GRANTEE`      | `VARCHAR2(32)`  | \-                                                                       |
| `TABLE_SCHEMA` | `VARCHAR2(32)`  | \-                                                                       |
| `TABLE_NAME`   | `VARCHAR2(128)` | \-                                                                       |
| `GRANTOR`      | `VARCHAR2(32)`  | \-                                                                       |
| `PRIVILEGE`    | `VARCHAR2(6)`   | "`SELECT`" or "`UPDATE`" or "`INSERT`" or "`DELETE`" or "`INDEX`" or " " |
| `GRANTABLE`    | `VARCHAR2(3)`   | "`YES`"                                                                  |

### USER_TABLES

Table C-40 USER_TABLES

| Name                        | Type            | Value                                 |
|:----------------------------|:----------------|:--------------------------------------|
| `TABLE_NAME`                | `VARCHAR2(128)` | \-                                    |
| `TABLESPACE_NAME`           | `VARCHAR2(1)`   | `NULL`                                |
| `CLUSTER_NAME`              | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_NAME`                  | `VARCHAR2(1)`   | `NULL`                                |
| `PCT_FREE`                  | `NUMBER`        | `0`                                   |
| `PCT_USED`                  | `NUMBER`        | `0`                                   |
| `INI_TRANS`                 | `NUMBER`        | `0`                                   |
| `MAX_TRANS`                 | `NUMBER`        | `0`                                   |
| `INITIAL_EXTENT`            | `NUMBER`        | `0`                                   |
| `NEXT_EXTENT`               | `NUMBER`        | `0`                                   |
| `MIN_EXTENTS`               | `NUMBER`        | `0`                                   |
| `MAX_EXTENTS`               | `NUMBER`        | `0`                                   |
| `PCT_INCREASE`              | `NUMBER`        | `0`                                   |
| `FREELISTS`                 | `NUMBER`        | `0`                                   |
| `FREELIST_GROUPS`           | `NUMBER`        | `0`                                   |
| `LOGGING`                   | `VARCHAR2(1)`   | `NULL`                                |
| `BACKED_UP`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NUM_ROWS`                  | `NUMBER(10)`    | `0`                                   |
| `BLOCKS`                    | `NUMBER`        | `0`                                   |
| `EMPTY_BLOCKS`              | `NUMBER`        | `0`                                   |
| `AVG_SPACE`                 | `NUMBER`        | `0`                                   |
| `CHAIN_CNT`                 | `NUMBER`        | `0`                                   |
| `AVG_ROW_LEN`               | `NUMBER`        | `0`                                   |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`        | `0`                                   |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`        | `0`                                   |
| `DEGREE`                    | `VARCHAR2(1)`   | `NULL`                                |
| `INSTANCES`                 | `VARCHAR2(1)`   | `NULL`                                |
| `CACHE`                     | `VARCHAR2(1)`   | `NULL`                                |
| `TABLE_LOCK`                | `VARCHAR2(1)`   | `NULL`                                |
| `SAMPLE_SIZE`               | `NUMBER`        | `0`                                   |
| `LAST_ANALYZED`             | `DATE`          | `to_date('01-01-1980', 'dd-mm-yyyy')` |
| `PARTITIONED`               | `VARCHAR2(1)`   | `NULL`                                |
| `IOT_TYPE`                  | `VARCHAR2(1)`   | `NULL`                                |
| `TEMPORARY`                 | `VARHCAR2(1)`   | `NULL`                                |
| `SECONDARY`                 | `VARCHAR2(1)`   | `NULL`                                |
| `NESTED`                    | `VARCHAR2(1)`   | `NULL`                                |
| `BUFFER_POOL`               | `VARCHAR2(1)`   | `NULL`                                |
| `ROW_MOVEMENT`              | `VARCHAR2(1)`   | `NULL`                                |
| `GLOBAL_STATS`              | `VARCHAR2(1)`   | `NULL`                                |
| `USER_STATS`                | `VARCHAR2(1)`   | `NULL`                                |
| `DURATION`                  | `VARCHAR2(1)`   | `NULL`                                |
| `SKIP_CORRUPT`              | `VARCHAR2(1)`   | `NULL`                                |
| `MONITORING`                | `VARCHAR2(1)`   | `NULL`                                |

### USER_USERS

Table C-41 USER_USERS

| Name                          | Type           | Value    |
|:------------------------------|:---------------|:---------|
| `USERNAME`                    | `VARCHAR2(32)` | \-       |
| `USER_ID`                     | `NUMBER`       | \-       |
| `ACCOUNT_STATUS`              | `VARCHAR2(4)`  | "`OPEN`" |
| `LOCK_DATE`                   | `DATE`         | `NULL`   |
| `EXPIRY_DATE`                 | `DATE`         | `NULL`   |
| `DEFAULT_TABLESPACE`          | `VARCHAR2(1)`  | `NULL`   |
| `TEMPORARY_TABLESPACE`        | `VARCHAR2(1)`  | `NULL`   |
| `CREATED`                     | `DATE`         | `NULL`   |
| `INITIAL_RSRC_CONSUMER_GROUP` | `VARCHAR2(1)`  | `NULL`   |
| `EXTERNAL_NAME`               | `VARCHAR2(1)`  | `NULL`   |

### USER_VIEWS

Table C-42 USER_VIEWS

| Name               | Type            | Value  |
|:-------------------|:----------------|:-------|
| `VIEW_NAME`        | `VARCHAR2(128)` | \-     |
| `TEXT_LENGTH`      | `NUMBER`        | `64`   |
| `TEXT`             | `VARCHAR2(64)`  | \-     |
| `TYPE_TEXT_LENGTH` | `NUMBER`        | `0`    |
| `TYPE_TEXT`        | `VARCHAR2(1)`   | `NULL` |
| `OID_TEXT_LENGTH`  | `NUMBER`        | `0`    |
| `OID_TEXT`         | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(1)`   | `NULL` |
| `VIEW_TYPE`        | `VARCHAR2(1)`   | `NULL` |
