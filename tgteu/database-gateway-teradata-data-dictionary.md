The Oracle Database Gateway for Teradata User's Guide translates a query that refers to an Oracle database data dictionary table into a query that retrieves the data from Teradata system catalog tables. You perform queries on data dictionary tables over the database link in the same way you query data dictionary tables in the Oracle database. The gateway data dictionary is similar to the Oracle database data dictionary in appearance and use.

Topics:

- Data Dictionary Mapping

- Gateway Data Dictionary Descriptions

### Teradata System Catalog Tables

Teradata data dictionary information is stored in the Teradata database as Teradata system catalog tables. The Teradata system catalog tables define the structure of a database. When you change data definitions, Teradata reads and modifies the Teradata system catalog tables to add information about the user tables.

### Accessing the Gateway Data Dictionary

Accessing a gateway data dictionary table or view is identical to accessing a data dictionary in an Oracle database. You issue a SQL `SELECT` statement specifying a database link. The Oracle database data dictionary view and column names are used to access the gateway data dictionary in an Oracle database. Synonyms of supported views are also acceptable. For example, the following statement queries the data dictionary table `ALL_CATALOG` to retrieve all table names in the Teradata database:

    SQL> SELECT * FROM ALL_CATALOG@TERA;

When a data dictionary access query is issued, the gateway:

1.  Maps the requested table, view, or synonym to one or more Teradata system table names. The gateway translates all data dictionary column names to their corresponding Teradata database column names within the query. Refer to "Data Dictionary Mapping" for details.
2.  Sends the translated query to Teradata.
3.  Might convert the retrieved Teradata data to give it the appearance of the Oracle database data dictionary table.
4.  Passes the data dictionary information from the translated Teradata system catalog table to the Oracle database.
    **Note:**

    The values returned when querying the gateway data dictionary might not be the same as the ones returned by the Oracle Enterprise Manager `DESCRIBE` command.

### Direct Queries to Teradata Tables

Queries issued directly to individual Teradata system catalog tables are allowed but they return different results because the Teradata system catalog table column names differ from those of the data dictionary view. Also, certain columns in a Teradata system catalog table cannot be used in data dictionary processing.

### Supported Views and Tables

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
| `DUAL`                     | `USER_COL_COMMENTS`        |
| `USER_CATALOG`             | `USER_CONSTRAINTS`         |
| `USER_CONS_COLUMNS`        | `USER_INDEXES`             |
| `USER_IND_COLUMNS`         | `USER_TAB_COLUMNS`         |
| `USER_OBJECTS`             | `USER_TABLES`              |
| `USER_TAB_COMMENTS`        | `USER_VIEWS`               |
| `USER_USERS`               |                            |

No other Oracle database data dictionary tables or views are supported. If you use a view not on the list, you receive the Oracle database error code for no more rows available.

Queries through the gateway of any data dictionary table or view beginning with ALL\_ can returns rows from the Teradata database even when access privileges for those Teradata objects have not been granted. When querying an Oracle database with the Oracle data dictionary, rows are returned only for those objects you are permitted to access.

### Data Dictionary Mapping

The table in this section lists Oracle data dictionary view names and the equivalent Teradata system tables used. A plus sign (+) indicates that a join operation is involved.

Table C-1 Oracle Data Dictionary View Names and Teradata Equivalents

| View Name           | Teradata System Table Name                   |
|:--------------------|:---------------------------------------------|
| `ALL_CATALOG`       | `DBC.TablesX` + `DBC.IndicesX`               |
| `ALL_COL_COMMENTS`  | `DBC.ColumnsX`                               |
| `ALL_CONS_COLUMNS`  | `DBC.Indices`                                |
| `ALL_CONSTRAINTS`   | `DBC.IndicesX`                               |
| `ALL_IND_COLUMNS`   | `DBC.Indices` + `DBC.Tables` + `DBC.Columns` |
| `ALL_INDEXES`       | `DBC.Indices`                                |
| `ALL_OBJECTS`       | `DBC.IndicesX` + `DBC.TablesX`               |
| `ALL_TAB_COLUMNS`   | `DBC.ColumnsX` + `DBC.TablesX`               |
| `ALL_TAB_COMMENTS`  | `DBC.Tables`                                 |
| `ALL_TABLES`        | `DBC.TablesX`                                |
| `ALL_USERS`         | `DBC.Databases`                              |
| `ALL_VIEWS`         | `DBC.Tables`                                 |
| `DBA_CATALOG`       | `DBC.Tables` + `DBC.Indices`                 |
| `DBA_COL_COMMENTS`  | `DBC.Columns` + `DBC.Tables`                 |
| `DBA_OBJECTS`       | `DBC.Indices` + `DBC.Tables`                 |
| `DBA_TAB_COLUMNS`   | `DBC.Columns` + `DBC.Tables`                 |
| `DBA_TAB_COMMENTS`  | `DBC.Tables`                                 |
| `DBA_TABLES`        | `DBC.Tables`                                 |
| `DICT_COLUMNS`      | `DBC.Columns`                                |
| `DICTIONARY`        | `DBC.Tables`                                 |
| `DUAL`              | `DBC.Tables`                                 |
| `USER_CATALOG`      | `DBC.Tables` + `DBC.Indices`                 |
| `USER_COL_COMMENTS` | `DBC.Columns`                                |
| `USER_CONS_COLUMNS` | `DBC.Indices`                                |
| `USER_CONSTRAINTS`  | `DBC.IndicesX`                               |
| `USER_IND_COLUMNS`  | `DBC.Indices` + `DBC.Tables` + `DBC.Columns` |
| `USER_INDEXES`      | `DBC.Indices`                                |
| `USER_OBJECTS`      | `DBC.Indices` + `DBC.Tables`                 |
| `USER_TAB_COLUMNS`  | `DBC.ColumnsX `+ `DBC.TablesX`               |
| `USER_TAB_COMMENTS` | `DBC.TablesX`                                |
| `USER_TABLES`       | `DBC.Tables`                                 |
| `USER_USERS`        | `DBC.DatabasesX`                             |
| `USER_VIEWS`        | `DBC.Tables`                                 |

#### Default Column Values

There is a minor difference between the gateway data dictionary and a typical Oracle database data dictionary. The Oracle database columns that are missing in a Teradata system catalog table are filled with zeros, spaces, null values, not-applicable values (N.A.), or default values, depending on the column type.

### Gateway Data Dictionary Descriptions

The gateway data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

They are described here with information retrieved by an SQL\*PLUS `DESCRIBE` command. The values in the Null? column might differ from the Oracle database data dictionary tables and views. Any hardcoded default value is shown to the right of an item, but this is not information returned by `DESCRIBE`.

### ALL_CATALOG

Table C-2 ALL_CATALOG

| Name         | Type           | Value                             |
|:-------------|:---------------|:----------------------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                                |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                                |
| `TABLE_TYPE` | `VARCHAR2(11)` | "`TABLE`", "`VIEW`", or "`INDEX`" |

### ALL_COL_COMMENTS

Table C-3 ALL_COL_COMMENTS

| Name          | Type             | Value |
|:--------------|:-----------------|:------|
| `OWNER`       | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-    |
| `COMMENTS`    | `VARCHAR2(4000)` | " "   |

### ALL_CONS_COLUMNS

Table C-4 ALL_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-    |
| `POSITION`        | `NUMBER`         | \-    |

### ALL_CONSTRAINTS

Table C-5 ALL_CONSTRAINTS

| Name                | Type           | Value          |
|:--------------------|:---------------|:---------------|
| `OWNER`             | `VARCHAR2(30)` | \-             |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-             |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | "`R`" or "`P`" |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-             |
| `SEARCH_CONDITION`  | `VARCHAR2(1)`  | " "            |
| `R_OWNER`           | `VARCHAR2(30)` | " "            |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | " "            |
| `DELETE_RULE`       | `VARCHAR2(9)`  | " "            |
| `STATUS`            | `VARCHAR2(8)`  | " "            |
| `DEFERRABLE`        | `VARCHAR2(14)` | " "            |
| `DEFERRED`          | `VARCHAR2(9)`  | " "            |
| `VALIDATED`         | `VARCHAR2(13)` | " "            |
| `GENERATED`         | `VARCHAR2(14)` | " "            |
| `BAD`               | `VARCHAR2(3)`  | " "            |
| `RELY`              | ` VARCHAR2(4)` | " "            |
| `LAST_CHANGE`       | `DATE`         | `NULL`         |
| `INDEX_OWNER`       | `VARCHAR2(30)` | " "            |
| `INDEX_NAME`        | `VARCHAR2(30)` | " "            |
| `INVALID`           | `VARCHAR2(7)`  | " "            |
| `VIEW_RELATED`      | `VARCHAR2(14)` | " "            |

### ALL_IND_COLUMNS

Table C-6 ALL_IND_COLUMNS

| Name              | Type             | Value               |
|:------------------|:-----------------|:--------------------|
| `INDEX_OWNER`     | `VARCHAR2(30)`   | \-                  |
| `INDEX_NAME`      | `VARCHAR2(30)`   | \-                  |
| `TABLE_OWNER`     | `VARCHAR2(30)`   | \-                  |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-                  |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-                  |
| `COLUMN_POSITION` | `NUMBER`         | \-                  |
| `COLUMN_LENGTH`   | `NUMBER`         | \-                  |
| `DESCEND`         | `VARCHAR2(4)`    | "`DESC`" or "`ASC`" |

### ALL_INDEXES

Table C-7 ALL_INDEXES

| Name                      | Type             | Value                       |
|:--------------------------|:-----------------|:----------------------------|
| `OWNER`                   | `VARCHAR2(30)`   | \-                          |
| `INDEX_NAME`              | `VARCHAR2(30)`   | \-                          |
| `INDEX_TYPE`              | `VARCHAR2(27)`   | " "                         |
| `TABLE_OWNER`             | `VARCHAR2(30)`   | \-                          |
| `TABLE_NAME`              | `VARCHAR2(30)`   | \-                          |
| `TABLE_TYPE`              | `VARCHAR2(5)`    | "`TABLE`"                   |
| `UNIQUENESS`              | `VARCHAR2(9)`    | "`UNIQUE`" or "`NONUNIQUE`" |
| `COMPRESSION`             | `VARCHAR2(8)`    | " "                         |
| `PREFIX_LENGTH`           | `NUMBER`         | `0`                         |
| `TABLESPACE_NAME`         | `VARCHAR2(30)`   | " "                         |
| `INI_TRANS`               | `NUMBER`         | `0`                         |
| `MAX_TRANS`               | `NUMBER(10)`     | `0`                         |
| `INITIAL_EXTENT`          | `NUMBER(10)`     | `0`                         |
| `NEXT_EXTENT`             | `NUMBER(10)`     | `0`                         |
| `MIN_EXTENTS`             | `NUMBER(10)`     | `0`                         |
| `MAX_EXTENTS`             | `NUMBER(10)`     | `0`                         |
| `PCT_INCREASE`            | `NUMBER(10)`     | `0`                         |
| `PCT_THRESHOLD`           | `NUMBER(10)`     | `0`                         |
| `INCLUDE_COLUMN`          | `NUMBER(10)`     | `0`                         |
| `FREELISTS`               | `NUMBER(10)`     | `0`                         |
| `FREELIST_GROUPS`         | `NUMBER(10)`     | `0`                         |
| `PCT_FREE`                | `NUMBER(10)`     | `0`                         |
| `LOGGING`                 | `VARCHAR2(3)`    | " "                         |
| `BLEVEL`                  | `NUMBER`         | `0`                         |
| `LEAF_BLOCKS`             | `NUMBER`         | `0`                         |
| `DISTINCT_KEYS`           | `NUMBER`         | \-                          |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `CLUSTERING_FACTOR`       | `NUMBER`         | `0`                         |
| `STATUS`                  | `CHAR(1)`        | " "                         |
| `NUM_ROWS`                | `NUMBER`         | `0`                         |
| `SAMPLE_SIZE`             | `NUMBER`         | `0`                         |
| `LAST_ANALYZED`           | `DATE`           | `NULL`                      |
| `DEGREE`                  | `VARCHAR2(40)`   | " "                         |
| `INSTANCES`               | `VARCHAR2(3)`    | " "                         |
| `PARTITIONED`             | `VARCHAR2(3)`    | " "                         |
| `TEMPORARY`               | `VARCHAR2(1)`    | " "                         |
| `GENERATED`               | `VARCHAR2(1)`    | " "                         |
| `SECONDARY`               | `VARCHAR2(1)`    | " "                         |
| `BUFFER_POOL`             | `VARCHAR2(7)`    | " "                         |
| `USER_STATS`              | `VARCHAR2(3)`    | " "                         |
| `DURATION`                | `VARCHAR2(15)`   | " "                         |
| `PCT_DIRECT_ACCESS`       | `NUMBER`         | `0`                         |
| `ITYP_OWNER`              | `VARCHAR2(30)`   | " "                         |
| `ITYP_NAME`               | `VARCHAR2(30)`   | " "                         |
| `PARAMETERS`              | `VARCHAR2(1000)` | " "                         |
| `GLOBAL_STATS`            | `VARCHAR2(3)`    | " "                         |
| `DOMIDX_STATUS`           | `VARCHAR2(12)`   | " "                         |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(6)`    | " "                         |
| `FUNCIDX_STATUS`          | `VARCHAR2(8)`    | " "                         |
| `JOIN_INDEX`              | `VARCHAR2(3)`    |                             |
| `IOT_REDUNDANT_PKEY_ELIM` | `VARCHAR2(3)`    |                             |
| `DROPPED`                 | `VARCHAR2(3)`    |                             |
| `VISIBILITY`              | `VARCHAR2(9)`    |                             |
| `DOMIDX_MANAGEMENT`       | `VARCHAR2(14)`   |                             |

### ALL_OBJECTS

Table C-8 ALL_OBJECTS

| Name             | Type           | Value                                               |
|:-----------------|:---------------|:----------------------------------------------------|
| `OWNER`          | `VARCHAR2(30)` | \-                                                  |
| `OBJECT_NAME`    | `VARCHAR2(30)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(30)` | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`       | `0`                                                 |
| `DATA_OBJECT_ID` | `NUMBER`       | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(19)` | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`         | `NULL`                                              |
| `LAST_DDL_TIME`  | `DATE`         | `NULL`                                              |
| `TIMESTAMP`      | `VARCHAR2(19)` | `NULL`                                              |
| `STATUS`         | `VARCHAR2(7)`  | `NULL`                                              |
| `TEMPORARY`      | `VARCHAR2(1)`  | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`  | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`  | `NULL`                                              |
| `NAMESPACE`      | `NUMBER`       | `NULL`                                              |
| `EDITION_NAME`   | `VARCHAR2(30)` | `NULL`                                              |

### ALL_TAB_COLUMNS

Table C-9 ALL_TAB_COLUMNS

| Name                   | Type             | Value          |
|:-----------------------|:-----------------|:---------------|
| `OWNER`                | `VARCHAR2(30)`   | \-             |
| `TABLE_NAME`           | `VARCHAR2(30)`   | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)`   | \-             |
| `DATA_TYPE`            | `VARCHAR2(106)`  | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(3)`    | " "            |
| `DATA_TYPE_OWNER`      | `VARCHAR2(30)`   | " "            |
| `DATA_LENGTH`          | `NUMBER`         | \-             |
| `DATA_PRECISION`       | `NUMBER`         | \-             |
| `DATA_SCALE`           | `NUMBER`         | \-             |
| `NULLABLE`             | `VARCHAR2(1)`    | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER`         | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`         | `0`            |
| `DATA_DEFAULT`         | `VARCHAR2(1024)` | " "            |
| `NUM_DISTINCT`         | `NUMBER`         | `0`            |
| `LOW_VALUE`            | `RAW(32)`        | `0`            |
| `HIGH_VALUE`           | `RAW(32)`        | `0`            |
| `DENSITY`              | `NUMBER`         | `0`            |
| `NUM_NULLS`            | `NUMBER`         | `0`            |
| `NUM_BUCKETS`          | `NUMBER`         | `0`            |
| `LAST_ANALYZED`        | `DATE`           | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`         | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(44)`   | " "            |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`         | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(3)`    | " "            |
| `USER_STATS`           | `VARCHAR2(3)`    | " "            |
| `AVG_COL_LEN`          | `NUMBER`         | `0`            |
| `CHAR_LENGTH`          | `NUMBER`         |                |
| `CHAR_USED`            | `VARCHAR2(1)`    |                |
| `V80_FMT_IMAGE`        | `VARCHAR2(3)`    |                |
| `DATA_UPGRADED`        | `VARCHAR2(3)`    |                |
| `HISTOGRAM`            | `VARCHAR2(15)`   |                |

### ALL_TAB_COMMENTS

Table C-10 ALL_TAB_COMMENTS

| Name         | Type             | Value                 |
|:-------------|:-----------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)`   | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)`   | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(4000)` | " "                   |

### ALL_TABLES

Table C-11 ALL_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `OWNER`                     | `VARCHAR2(30)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(30)` | " "    |
| `CLUSTER_NAME`              | `VARCHAR2(30)` | " "    |
| `IOT_NAME`                  | `VARCHAR2(8)`  | " "    |
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
| `LOGGING`                   | `VARCHAR2(3)`  | " "    |
| `BACKED_UP`                 | `VARCHAR2(1)`  | " "    |
| `NUM_ROWS`                  | `NUMBER`       | \-     |
| `BLOCKS`                    | `NUMBER`       | \-     |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(10)` | " "    |
| `INSTANCES`                 | `VARCHAR2(10)` | " "    |
| `CACHE`                     | `VARCHAR2(5)`  | " "    |
| `TABLE_LOCK`                | `VARCHAR2(8)`  | " "    |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(3)`  | " "    |
| `IOT_TYPE`                  | `VARCHAR2(12)` | " "    |
| `TEMPORARY`                 | `VARCHR2(1)`   | " "    |
| `SECONDARY`                 | `VARCHR2(1)`   | " "    |
| `NESTED`                    | `VARCHAR2(3)`  | " "    |
| `BUFFER_POOL`               | `VARCHAR2(7)`  | " "    |
| `ROW_MOVEMENT`              | `VARCHAR2(8)`  | " "    |
| `GLOBAL_STATS`              | `VARCHAR2(3)`  | " "    |
| `USER_STATS`                | `VARCHAR2(3)`  | " "    |
| `DURATION`                  | `VARCHAR2(15)` | " "    |
| `SKIP_CORRUPT`              | `VARCHAR2(8)`  | " "    |
| `MONITORING`                | `VARCHAR2(3)`  | " "    |
| `CLUSTER_OWNER`             | `VARCHAR2(30)` |        |
| `DEPENDENCIES`              | `VARCHAR2(8)`  |        |
| `COMPRESSION`               | `VARCHAR2(8)`  |        |
| `DROPPED`                   | `VARCHAR2(3)`  |        |

### ALL_USERS

Table C-12 ALL_USERS

| Name       | Type           | Value  |
|:-----------|:---------------|:-------|
| `USERNAME` | `VARCHAR2(30)` | \-     |
| `USER_ID`  | `NUMBER`       | `0`    |
| `CREATED`  | `DATE`         | `NULL` |

### ALL_VIEWS

Table C-13 ALL_VIEWS

| Name               | Type             | Value |
|:-------------------|:-----------------|:------|
| `OWNER`            | `VARCHAR2(30)`   | \-    |
| `VIEW_NAME`        | `VARCHAR2(30)`   | \-    |
| `TEXT_LENGTH`      | `NUMBER`         | `0`   |
| `TEXT`             | `VARCHAR2(1)`    | " "   |
| `TYPE_TEXT_LENGTH` | `NUMBER`         | `0`   |
| `TYPE_TEXT`        | `VARCHAR2(4000)` | " "   |
| `OID_TEXT_LENGTH`  | `NUMBER`         | `0`   |
| `OID_TEXT`         | `VARCHAR2(4000)` | " "   |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(30)`   | " "   |
| `VIEW_TYPE`        | `VARCHAR2(30)`   | " "   |
| `SUPERVIEW_NAME`   | `VARCHAR2(30)`   |       |
| `EDITIONING_VIEW`  | `VARCHAR2(1)`    |       |
| `READ_ONLY`        | `VARCHAR2(1)`    |       |

### DBA_CATALOG

Table C-14 DBA_CATALOG

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)` | "`TABLE`" or "`VIEW`" |

### DBA_COL_COMMENTS

Table C-15 DBA_COL_COMMENTS

| Name          | Type             | Value |
|:--------------|:-----------------|:------|
| `OWNER`       | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-    |
| `COMMENTS`    | `VARCHAR2(4000)` | " "   |

### DBA_OBJECTS

Table C-16 DBA_OBJECTS

| Name             | Type            | Value                                               |
|:-----------------|:----------------|:----------------------------------------------------|
| `OWNER`          | `VARCHAR2(30)`  | \-                                                  |
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(30)`  | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`        | `0`                                                 |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(19)`  | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | `NULL`                                              |
| `LAST_DDL_TIME`  | `DATE`          | `NULL`                                              |
| `TIMESTAMP`      | `VARCHAR2(19)`  | `NULL`                                              |
| `STATUS`         | `VARCHAR2(7)`   | `NULL`                                              |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `NAMESPACE`      | `NUMBER`        |                                                     |
| `EDITION_NAME`   | `VARCHAR2(30)`  |                                                     |

### DBA_TAB_COLUMNS

Table C-17 DBA_TAB_COLUMNS

| Name                   | Type             | Value          |
|:-----------------------|:-----------------|:---------------|
| `OWNER`                | `VARCHAR2(30)`   | \-             |
| `TABLE_NAME`           | `VARCHAR2(30)`   | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)`   | \-             |
| `DATA_TYPE`            | `VARCHAR2(106)`  | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(3)`    | " "            |
| `DATA_TYPE_OWNER`      | `VARCHAR2(30)`   | " "            |
| `DATA_LENGTH`          | `NUMBER`         | \-             |
| `DATA_PRECISION`       | `NUMBER`         | \-             |
| `DATA_SCALE`           | `NUMBER`         | \-             |
| `NULLABLE`             | `VARCHAR2(1)`    | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER`         | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`         | `0`            |
| `DATA_DEFAULT`         | `VARCHAR2(1024)` | " "            |
| `NUM_DISTINCT`         | `NUMBER`         | `0`            |
| `LOW_VALUE`            | `RAW(32)`        | `0`            |
| `HIGH_VALUE`           | `RAW(32)`        | `0`            |
| `DENSITY`              | `NUMBER`         | `0`            |
| `NUM_NULLS`            | `NUMBER`         | `0`            |
| `NUM_BUCKETS`          | `NUMBER`         | `0`            |
| `LAST_ANALYZED`        | `DATE`           | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`         | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(44)`   | " "            |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`         | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(3)`    | " "            |
| `USER_STATS`           | `VARCHAR2(3)`    | " "            |
| `AVG_COL_LEN`          | `NUMBER`         | `0`            |
| `CHAR_LENGTH`          | `NUMBER`         |                |
| `CHAR_USED`            | `VARCHAR2(1)`    |                |
| `V80_FMT_IMAGE`        | `VARCHAR2(3)`    |                |
| `DATA_UPGRADED`        | `VARCHAR2(3)`    |                |
| `HISTOGRAM`            | `VARCHAR2(15)`   |                |

### DBA_TAB_COMMENTS

Table C-18 DBA_TAB_COMMENTS

| Name         | Type             | Value                 |
|:-------------|:-----------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)`   | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)`   | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(4000)` | " "                   |

### DBA_TABLES

Table C-19 DBA_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `OWNER`                     | `VARCHAR2(30)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(30)` | " "    |
| `CLUSTER_NAME`              | `VARCHAR2(30)` | " "    |
| `IOT_NAME`                  | `VARCHAR2(30)` | " "    |
| `STATUS`                    | `VARCHAR2(8)`  |        |
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
| `LOGGING`                   | `VARCHAR2(3)`  | " "    |
| `BACKED_UP`                 | `VARCHAR2(1)`  | " "    |
| `NUM_ROWS`                  | `NUMBER`       | \-     |
| `BLOCKS`                    | `NUMBER`       | \-     |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(10)` | " "    |
| `INSTANCES`                 | `VARCHAR2(10)` | " "    |
| `CACHE`                     | `VARCHAR2(5)`  | " "    |
| `TABLE_LOCK`                | `VARCHAR2(8)`  | " "    |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(3)`  | " "    |
| `IOT_TYPE`                  | `VARCHAR2(12)` | " "    |
| `TEMPORARY`                 | `VARCHAR2(1)`  | " "    |
| `SECONDARY`                 | `VARCHAR2(1)`  | " "    |
| `NESTED`                    | `VARCHAR2(3)`  | " "    |
| `BUFFER_POOL`               | `VARCHAR2(7)`  | " "    |
| `ROW_MOVEMENT`              | `VARCHAR2(8)`  | " "    |
| `GLOBAL_STATS`              | `VARCHAR2(3)`  | " "    |
| `USER_STATS`                | `VARCHAR2(3)`  | " "    |
| `DURATION`                  | `VARCHAR2(15)` | " "    |
| `SKIP_CORRUPT`              | `VARCHAR2(8)`  | " "    |
| `MONITORING`                | `VARCHAR2(3)`  | " "    |
| `CLUSTER_OWNER`             | `VARCHAR2(30)` |        |
| `DEPENDENCIES`              | `VARCHAR2(8)`  |        |
| `COMPRESSION`               | `VARCHAR2(8)`  |        |
| `DROPPED`                   | `VARCHAR2(3)`  |        |

### DICT_COLUMNS

Table C-20 DICT_COLUMNS

| Name          | Type             | Value |
|:--------------|:-----------------|:------|
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-    |
| `COMMENTS`    | `VARCHAR2(4000)` | " "   |

### DICTIONARY

Table C-21 DICTIONARY

| Name         | Type             | Value |
|:-------------|:-----------------|:------|
| `TABLE_NAME` | `VARCHAR2(30)`   | \-    |
| `COMMENTS`   | `VARCHAR2(4000)` | " "   |

### DUAL

Table C-22 DUAL

| Name    | Type          | Value |
|:--------|:--------------|:------|
| `DUMMY` | `VARCHAR2(1)` | "`X`" |

### USER_CATALOG

Table C-23 USER_CATALOG

| Name         | Type           | Value                 |
|:-------------|:---------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(30)` | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)` | "`TABLE`" or "`VIEW`" |

### USER_COL_COMMENTS

Table C-24 USER_COL_COMMENTS

| Name          | Type             | Value |
|:--------------|:-----------------|:------|
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-    |
| `COMMENTS`    | `VARCHAR2(4000)` | " "   |

### USER_CONS_COLUMNS

Table C-25 USER_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-    |
| `POSITION`        | `NUMBER`         | \-    |

### USER_CONSTRAINTS

Table C-26 USER_CONSTRAINTS

| Name                | Type           | Value          |
|:--------------------|:---------------|:---------------|
| `OWNER`             | `VARCHAR2(30)` | \-             |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-             |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | "`R`" or "`P`" |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-             |
| `SEARCH_CONDITION`  | `CHAR(1)`      | " "            |
| `R_OWNER`           | `VARCHAR2(30)` | \-             |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | \-             |
| `DELETE_RULE`       | `VARCHAR2(9)`  | " "            |
| `STATUS`            | `VARCHAR2(8)`  | " "            |
| `DEFERRABLE`        | `VARCHAR2(14)` | " "            |
| `DEFERRED`          | `VARCHAR2(9)`  | " "            |
| `VALIDATED`         | `VARCHAR2(13)` | " "            |
| `GENERATED`         | `VARCHAR2(14)` | " "            |
| `BAD`               | `VARCHAR2(3)`  | " "            |
| `RELY`              | `VARCHAR2(4)`  | " "            |
| `LAST_CHANGE`       | `DATE`         | `NULL`         |
| `INDEX_OWNER`       | `VARCHAR2(30)` |                |
| `INDEX_NAME`        | `VARCHAR2(30)` |                |
| `INVALID`           | `VARCHAR2(7)`  |                |
| `VIEW_RELATED`      | `VARCHAR2(14)` |                |

### USER_IND_COLUMNS

Table C-27 USER_IND_COLUMNS

| Name              | Type             | Value               |
|:------------------|:-----------------|:--------------------|
| `INDEX_NAME`      | `VARCHAR2(30)`   | \-                  |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-                  |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-                  |
| `COLUMN_POSITION` | `NUMBER`         | \-                  |
| `COLUMN_LENGTH`   | `NUMBER`         | \-                  |
| `CHAR_LENGTH`     | `NUMBER`         |                     |
| `DESCEND`         | `VARCHAR2(4)`    | "`DESC`" or "`ASC`" |

### USER_INDEXES

Table C-28 USER_INDEXES

| Name                      | Type             | Value                       |
|:--------------------------|:-----------------|:----------------------------|
| `INDEX_NAME`              | `VARCHAR2(30)`   | \-                          |
| `INDEX_TYPE`              | `VARCHAR2(27)`   | " "                         |
| `TABLE_OWNER`             | `VARCHAR2(30)`   | \-                          |
| `TABLE_NAME`              | `VARCHAR2(30)`   | \-                          |
| `TABLE_TYPE`              | `VARCHAR2(11)`   | "`TABLE`"                   |
| `UNIQUENESS`              | `VARCHAR2(9)`    | "`UNIQUE`" or "`NONUNIQUE`" |
| `COMPRESSION`             | `VARCHAR2(8)`    | " "                         |
| `PREFIX_LENGTH`           | `NUMBER`         | `0`                         |
| `TABLESPACE_NAME`         | `VARCHAR2(30)`   | " "                         |
| `INI_TRANS`               | `NUMBER`         | `0`                         |
| `MAX_TRANS`               | `NUMBER`         | `0`                         |
| `INITIAL_EXTENT`          | `NUMBER`         | `0`                         |
| `NEXT_EXTENT`             | `NUMBER`         | `0`                         |
| `MIN_EXTENTS`             | `NUMBER`         | `0`                         |
| `MAX_EXTENTS`             | `NUMBER`         | `0`                         |
| `PCT_INCREASE`            | `NUMBER`         | `0`                         |
| `PCT_THRESHOLD`           | `NUMBER`         | `0`                         |
| `INCLUDE_COLUMN`          | `NUMBER`         | `0`                         |
| `FREELISTS`               | `NUMBER`         | `0`                         |
| `FREELIST_GROUPS`         | `NUMBER`         | `0`                         |
| `PCT_FREE`                | `NUMBER`         | `0`                         |
| `LOGGING`                 | `VARCHAR2(3)`    | " "                         |
| `BLEVEL`                  | `NUMBER`         | `0`                         |
| `LEAF_BLOCKS`             | `NUMBER`         | `0`                         |
| `DISTINCT_KEYS`           | `NUMBER`         | \-                          |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `CLUSTERING_FACTOR`       | `NUMBER`         | 0                           |
| `STATUS`                  | `VARCHAR2(8)`    | " "                         |
| `NUM_ROWS`                | `NUMBER`         | `0`                         |
| `SAMPLE_SIZE`             | `NUMBER`         | `0`                         |
| `LAST_ANALYZED`           | `DATE`           | `NULL`                      |
| `DEGREE`                  | `VARCHAR2(40)`   | " "                         |
| `INSTANCES`               | `VARCHAR2(40)`   | " "                         |
| `PARTITIONED`             | `VARCHAR2(3)`    | " "                         |
| `TEMPORARY`               | `VARCHAR2(1)`    | " "                         |
| `GENERATED`               | `VARCHAR2(1)`    | " "                         |
| `SECONDARY`               | `VARCHAR2(1)`    | " "                         |
| `BUFFER_POOL`             | `VARCHAR2(7)`    | " "                         |
| `USER_STATS`              | `VARCHAR2(3)`    | " "                         |
| `DURATION`                | `VARCHAR2(15)`   | " "                         |
| `PCT_DIRECT_ACCESS`       | `NUMBER`         | `0`                         |
| `ITYP_OWNER`              | `VARCHAR2(30)`   | " "                         |
| `ITYP_NAME`               | `VARCHAR2(30)`   | " "                         |
| `PARAMETERS`              | `VARCHAR2(1000)` | " "                         |
| `GLOBAL_STATS`            | `VARCHAR2(3)`    | " "                         |
| `DOMIDX_STATUS`           | `VARCHAR2(12)`   | " "                         |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(6)`    | " "                         |
| `FUNCIDX_STATUS`          | `VARCHAR2(8)`    | " "                         |
| `JOIN_INDEX`              | `VARCHAR2(3)`    |                             |
| `IOT_REDUNDANT_PKEY_ELIM` | `VARCHAR2(3)`    |                             |
| `DROPPED`                 | `VARCHAR2(3)`    |                             |
| `VISIBILITY`              | `VARCHAR2(10)`   |                             |
| `DOMIDX_MANAGEMENT`       | `VARCHAR2(14)`   |                             |

### USER_OBJECTS

Table C-29 USER_OBJECTS

| Name             | Type            | Value                                               |
|:-----------------|:----------------|:----------------------------------------------------|
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                  |
| `SUBOBJECT_NAME` | `VARCHAR2(30)`  | `NULL`                                              |
| `OBJECT_ID`      | `NUMBER`        | `0`                                                 |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                 |
| `OBJECT_TYPE`    | `VARCHAR2(19)`  | "`TABLE`" or "`VIEW`" or "`INDEX`" or "`PROCEDURE`" |
| `CREATED`        | `DATE`          | `NULL`                                              |
| `LAST_DDL_TIME`  | `DATE`          | `NULL`                                              |
| `TIMESTAMP`      | `VARCHAR2(19)`  | `NULL`                                              |
| `STATUS`         | `VARCHAR2(7)`   | `NULL`                                              |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                              |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                              |
| `NAMESPACE`      | `NUMBER`        |                                                     |
| `EDITION_NAME`   | `VARCHAR2(30)`  |                                                     |

### USER_TAB_COLUMNS

Table C-30 USER_TAB_COLUMNS

| Name                   | Type            | Value          |
|:-----------------------|:----------------|:---------------|
| `TABLE_NAME`           | `VARCHAR2(30)`  | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)`  | \-             |
| `DATA_TYPE`            | `VARCHAR2(106)` | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(3)`   | " "            |
| `DATA_TYPE_OWNER`      | `VARCHAR2(30)`  | " "            |
| `DATA_LENGTH`          | `NUMBER`        | \-             |
| `DATA_PRECISION`       | `NUMBER`        | \-             |
| `DATA_SCALE`           | `NUMBER`        | \-             |
| `NULLABLE`             | `VARCHAR2(1)`   | "`Y`" or "`N`" |
| `COLUMN_ID`            | `NUMBER`        | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`        | `0`            |
| `DATA_DEFAULT`         | `CHAR(1)`       | " "            |
| `NUM_DISTINCT`         | `NUMBER`        | `0`            |
| `LOW_VALUE`            | `RAW(32)`       | `0`            |
| `HIGH_VALUE`           | `RAW(32)`       | `0`            |
| `DENSITY`              | `NUMBER`        | `0`            |
| `NUM_NULLS`            | `NUMBER`        | `0`            |
| `NUM_BUCKETS`          | `NUMBER`        | `0`            |
| `LAST_ANALYZED`        | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(44)`  | " "            |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(3)`   | " "            |
| `USER_STATS`           | `VARCHAR2(3)`   | " "            |
| `AVG_COL_LEN`          | `NUMBER`        | `0`            |
| `CHAR_LENGTH`          | `NUMBER`        |                |
| `CHAR_USED`            | `VARCHAR2(1)`   |                |
| `V80_FMT_IMAGE`        | `VARCHAR2(3)`   |                |
| `DATA_UPGRADED`        | `VARCHAR2(3)`   |                |
| `HISTOGRAM`            | `VARCHAR2(15)`  |                |

### USER_TAB_COMMENTS

Table C-31 USER_TAB_COMMENTS

| Name         | Type             | Value                 |
|:-------------|:-----------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(30)`   | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)`   | "`TABLE`" or "`VIEW`" |
| `COMMENTS`   | `VARCHAR2(4000)` | " "                   |

### USER_TABLES

Table C-32 USER_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(30)` | " "    |
| `CLUSTER_NAME`              | `VARCHAR2(30)` | " "    |
| `IOT_NAME`                  | `VARCHAR2(30)` | " "    |
| `STATUS`                    | `VARCHAR2(8)`  |        |
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
| `LOGGING`                   | `VARCHAR2(3)`  | " "    |
| `BACKED_UP`                 | `VARCHAR2(1)`  | " "    |
| `NUM_ROWS`                  | `NUMBER`       | \-     |
| `BLOCKS`                    | `NUMBER`       | \-     |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(10)` | " "    |
| `INSTANCES`                 | `VARCHAR2(10)` | " "    |
| `CACHE`                     | `VARCHAR2(5)`  | " "    |
| `TABLE_LOCK`                | `VARCHAR2(8)`  | " "    |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(3)`  | " "    |
| `IOT_TYPE`                  | `VARCHAR2(12)` | " "    |
| `TEMPORARY`                 | `VARCHAR2(1)`  | " "    |
| `SECONDARY`                 | `VARCHAR2(1)`  | " "    |
| `NESTED`                    | `VARCHAR2(3)`  | " "    |
| `BUFFER_POOL`               | `VARCHAR2(7)`  | " "    |
| `ROW_MOVEMENT`              | `VARCHAR2(8)`  | " "    |
| `GLOBAL_STATS`              | `VARCHAR2(3)`  | " "    |
| `USER_STATS`                | `VARCHAR2(3)`  | " "    |
| `DURATION`                  | `VARCHAR2(15)` | " "    |
| `SKIP_CORRUPT`              | `VARCHAR2(8)`  | " "    |
| `MONITORING`                | `VARCHAR2(3)`  | " "    |

### USER_USERS

Table C-33 USER_USERS

| Name                          | Type             | Value    |
|:------------------------------|:-----------------|:---------|
| `USERNAME`                    | `VARCHAR2(30)`   | \-       |
| `USER_ID`                     | `NUMBER`         | `0`      |
| `ACCOUNT_STATUS`              | `VARCHAR2(32)`   | "`OPEN`" |
| `LOCK_DATE`                   | `DATE`           | `NULL`   |
| `EXPIRY_DATE`                 | `DATE`           | `NULL`   |
| `DEFAULT_TABLESPACE`          | `VARCHAR2(30)`   | `NULL`   |
| `TEMPORARY_TABLESPACE`        | `VARCHAR2(30)`   | `NULL`   |
| `CREATED`                     | `DATE`           | `NULL`   |
| `INITIAL_RSRC_CONSUMER_GROUP` | `VARCHAR2(30)`   | `NULL`   |
| `EXTERNAL_NAME`               | `VARCHAR2(4000)` | `NULL`   |

### USER_VIEWS

Table C-34 USER_VIEWS

| Name               | Type             | Value |
|:-------------------|:-----------------|:------|
| `VIEW_NAME`        | `VARCHAR2(30)`   | \-    |
| `TEXT_LENGTH`      | `NUMBER`         | `0`   |
| `TEXT`             | `CHAR(1)`        | " "   |
| `TYPE_TEXT_LENGTH` | `NUMBER`         | `0`   |
| `TYPE_TEXT`        | `VARCHAR2(4000)` | " "   |
| `OID_TEXT_LENGTH`  | `NUMBER`         | `0`   |
| `OID_TEXT`         | `VARCHAR2(4000)` | " "   |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(30)`   | " "   |
| `VIEW_TYPE`        | `VARCHAR2(30)`   | " "   |
| `SUPERVIEW_NAME`   | `VARCHAR2(30)`   |       |
| `EDITIONING_VIEW`  | `VARCHAR2(1)`    |       |
