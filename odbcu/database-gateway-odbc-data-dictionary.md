Data dictionary information is stored in the non-Oracle system as system tables and is accessed through ODBC application programming interfaces (APIs).

The following topics explain how to access non-Oracle data dictionaries, use supported views and tables, and data dictionary mapping:

### Accessing the Non-Oracle Data Dictionary

Accessing a non-Oracle data dictionary table or view is identical to accessing a data dictionary in an Oracle database. You issue a `SELECT` statement specifying a database link. The Oracle data dictionary view and column names are used to access the non-Oracle data dictionary. Synonyms of supported views are also acceptable.

For example, the following statement queries the data dictionary table `ALL_USERS` to retrieve all users in the non-Oracle system:

    SQL SELECT * FROM all_users@sid1;


When you issue a data dictionary access query, the ODBC agent:

1.  Maps the requested table, view, or synonym to one or more ODBC APIs (see Data Dictionary Mapping). The agent translates all data dictionary column names to their corresponding non-Oracle column names within the query.
2.  Sends the sequence of APIs to the non-Oracle system.
3.  Possibly converts the retrieved non-Oracle data to give it the appearance of the Oracle data dictionary table.
4.  Passes the data dictionary information from the non-Oracle system table to Oracle.
    **Note:**

    The values returned when querying the Oracle Database Gateway for ODBC data dictionary may not be the same as those returned by the Oracle SQL\*Plus `DESCRIBE` command.

### Views and Tables Supported by Oracle Database Gateway for ODBC

Oracle Database Gateway for ODBC supports only the views and tables shown in the table, Oracle Database Gateway for ODBC Data Dictionary Mapping.

If you use an unsupported view, you receive an Oracle error message stating no rows were selected.

If you want to query data dictionary views using `SELECT... FROM DBA_*`, first connect as Oracle user `SYSTEM` or `SYS`. Otherwise, you receive the following error message:

    ORA-28506: Parse error in data dictionary translation for %s stored in %s

Using Oracle Database Gateway for ODBC, queries of the supported data dictionary tables and views beginning with the characters `ALL_` may return rows from the non-Oracle system when you do not have access privileges for those non-Oracle objects. When querying an Oracle database with the Oracle data dictionary, rows are returned only for those objects you are permitted to access.

#### Data Dictionary Mapping

The tables in this section list Oracle data dictionary view names and the equivalent ODBC APIs used.

Table C-1 shows a list of all Oracle data dictionary view names supported by Oracle Database Gateway for ODBC.

Table C-1 Oracle Database Gateway for ODBC Data Dictionary Mapping

| View       | ODBC API                                  |
|:-----------|:------------------------------------------|
| Table C-2  | `SQLTables`                               |
| Table C-3  | `SQLColumns`                              |
| Table C-4  | `SQLPrimaryKeys, SQLForeignKeys`          |
| Table C-5  | `SQLPrimaryKeys, SQLForeignKeys`          |
| Table C-6  | `SQLStatistics`                           |
| Table C-7  | `SQLStatistics`                           |
| Table C-8  | `SQLTables, SQLProcedures, SQLStatistics` |
| Table C-9  | `SQLColumns`                              |
| Table C-10 | `SQLTables`                               |
| Table C-11 | `SQLStatistics`                           |
| Table C-12 | `SQLTables`                               |
| Table C-13 | `SQLTables`                               |
| Table C-14 | `SQLTables`                               |
| Table C-15 | `SQLTables`                               |
| Table C-17 | `SQLColumns`                              |
| Table C-18 | `SQLPrimaryKeys, SQLForeignKeys`          |
| Table C-19 | `SQLPrimaryKeys, SQLForeignKeys`          |
| Table C-20 | `SQLStatistics`                           |
| Table C-21 | `SQLStatistics`                           |
| Table C-22 | `SQLTables, SQLProcedures, SQLStatistics` |
| Table C-23 | `SQLColumns`                              |
| Table C-24 | `SQLTables`                               |
| Table C-25 | `SQLStatistics`                           |
| Table C-26 | `SQLTables`                               |
| Table C-27 | `SQLTables`                               |

#### ALL_CATALOG

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-2 ALL_CATALOG

| Name         | Type           | Value                                |
|:-------------|:---------------|:-------------------------------------|
| `OWNER`      | `VARCHAR2(30)` | \-                                   |
| `TABLE_NAME` | `VARCHAR2(30)` | \-                                   |
| `TABLE_TYPE` | `VARCHAR2(11)` | `"TABLE" `or "`VIEW"` or `"SYNONYM"` |

#### ALL_COL_COMMENTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-3 ALL_COL_COMMENTS

| Name          | Type             | Value  |
|:--------------|:-----------------|:-------|
| `OWNER`       | `VARCHAR2(30)`   | \-     |
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-     |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-     |
| `COMMENTS`    | `VARCHAR2(4000)` | `NULL` |

#### ALL_CONS_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-4 ALL_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-    |
| `POSITION`        | `NUMBER`         | \-    |

#### ALL_CONSTRAINTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-5 ALL_CONSTRAINTS

| Name                | Type           | Value                                        |
|:--------------------|:---------------|:---------------------------------------------|
| `OWNER`             | `VARCHAR2(30)` | \-                                           |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-                                           |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | `"R"` or "`P"`                               |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-                                           |
| `SEARCH_CONDITION`  | `LONG`         | `NULL`                                       |
| `R_OWNER`           | `VARCHAR2(30)` | \-                                           |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | \-                                           |
| `DELETE_RULE`       | `VARCHAR2(9)`  | `"CASCADE"` or `"NO ACTION"` or `"SET NULL"` |
| `STATUS`            | `VARCHAR2(8)`  | `NULL`                                       |
| `DEFERRABLE`        | `VARCHAR2(14)` | `NULL`                                       |
| `DEFERRED`          | `VARCHAR2(9)`  | `NULL`                                       |
| `VALIDATED`         | `VARCHAR2(13)` | `NULL`                                       |
| `GENERATED`         | `VARCHAR2(14)` | `NULL`                                       |
| `BAD`               | `VARCHAR2(3)`  | `NULL`                                       |
| `RELY`              | `VARCHAR2(4)`  | `NULL`                                       |
| `LAST_CHANGE`       | `DATE`         | `NULL`                                       |

#### ALL_IND_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

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
| `DESCEND`         | `VARCHAR2(4)`    | `"DESC"` or "`ASC"` |

#### ALL_INDEXES

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-7 ALL_INDEXES

| Name                      | Type             | Value                       |
|:--------------------------|:-----------------|:----------------------------|
| `OWNER`                   | `VARCHAR2(30)`   | \-                          |
| `INDEX_NAME`              | `VARCHAR2(30)`   | \-                          |
| `INDEX_TYPE`              | `VARCHAR2(27)`   | `NULL`                      |
| `TABLE_OWNER`             | `VARCHAR2(30)`   | \-                          |
| `TABLE_NAME`              | `VARCHAR2(30)`   | \-                          |
| `TABLE_TYPE`              | `CHAR(5)`        | `"TABLE"`                   |
| `UNIQUENESS`              | `VARCHAR2(9)`    | `"UNIQUE"` or `"NONUNIQUE"` |
| `COMPRESSION`             | `VARCHAR2(8)`    | `NULL`                      |
| `PREFIX_LENGTH`           | `NUMBER`         | `0`                         |
| `TABLESPACE_NAME`         | `VARCHAR2(30)`   | `NULL`                      |
| `INI_TRANS`               | `NUMBER`         | `0`                         |
| `MAX_TRANS`               | `NUMBER`         | `0`                         |
| `INITIAL_EXTENT`          | `NUMBER`         | `0`                         |
| `NEXT_EXTENT`             | `NUMBER`         | `0`                         |
| `MIN_EXTENTS`             | `NUMBER`         | `0`                         |
| `MAX_EXTENTS`             | `NUMBER`         | `0`                         |
| `PCT_INCREASE`            | `NUMBER`         | `0`                         |
| `PCT_THRESHOLD`           | `NUMBER`         | `0`                         |
| `INCLUDE_COLUMNS`         | `NUMBER`         | `0`                         |
| `FREELISTS`               | `NUMBER`         | `0`                         |
| `FREELIST_GROUPS`         | `NUMBER`         | `0`                         |
| `PCT_FREE`                | `NUMBER`         | `0`                         |
| `LOGGING`                 | `VARCHAR2(3)`    | `NULL`                      |
| `BLEVEL`                  | `NUMBER`         | `0`                         |
| `LEAF_BLOCKS`             | `NUMBER`         | `0`                         |
| `DISTINCT_KEYS`           | `NUMBER`         |                             |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `CLUSTERING_FACTOR`       | `NUMBER`         | `0`                         |
| `STATUS`                  | `VARCHAR2(8)`    | `NULL`                      |
| `NUM_ROWS`                | `NUMBER`         | `0`                         |
| `SAMPLE_SIZE`             | `NUMBER`         | `0`                         |
| `LAST_ANALYZED`           | `DATE`           | `NULL`                      |
| `DEGREE`                  | `VARCHAR2(40)`   | `NULL`                      |
| `INSTANCES`               | `VARCHAR2(40)`   | `NULL`                      |
| `PARTITIONED`             | `VARCHAR2(3)`    | `NULL`                      |
| `TEMPORARY`               | `VARCHAR2(1)`    | `NULL`                      |
| `GENERATED`               | `VARCHAR2(1)`    | `NULL`                      |
| `SECONDARY`               | `VARCHAR2(1)`    | `NULL`                      |
| `BUFFER_POOL`             | `VARCHAR2(7)`    | `NULL`                      |
| `USER_STATS`              | `VARCHAR2(3)`    | `NULL`                      |
| `DURATION`                | `VARCHAR2(15)`   | `NULL`                      |
| `PCT_DIRECT_ACCESS`       | `NUMBER`         | `0`                         |
| `ITYP_OWNER`              | `VARCHAR2(30)`   | `NULL`                      |
| `ITYP_NAME`               | `VARCHAR2(30)`   | `NULL`                      |
| `PARAMETERS`              | `VARCHAR2(1000)` | `NULL`                      |
| `GLOBAL_STATS`            | `VARCHAR2(3)`    | `NULL`                      |
| `DOMIDX_STATUS`           | `VARCHAR2(12)`   | `NULL`                      |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(6)`    | `NULL`                      |
| `FUNCIDX_STATUS`          | `VARCHAR2(8)`    | `NULL`                      |

#### ALL_OBJECTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-8 ALL_OBJECTS

| Name             | Type           | Value                                                              |
|:-----------------|:---------------|:-------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(30)` | \-                                                                 |
| `OBJECT_NAME`    | `VARCHAR2(30)` | \-                                                                 |
| `SUBOBJECT_NAME` | `VARCHAR2(30)` | `NULL`                                                             |
| `OBJECT_ID`      | `NUMBER`       | `0`                                                                |
| `DATA_OBJECT_ID` | `NUMBER`       | `0`                                                                |
| `OBJECT_TYPE`    | `VARCHAR2(18)` | `"TABLE`" or "`VIEW`" or `"SYNONYM`" or `"INDEX`" or `"PROCEDURE"` |
| `CREATED`        | `DATE`         | `NULL`                                                             |
| `LAST_DDL_TIME`  | `DATE`         | `NULL`                                                             |
| `TIMESTAMP`      | `VARCHAR2(19)` | `NULL`                                                             |
| `STATUS`         | `VARCHAR2(7)`  | `NULL`                                                             |
| `TEMPORARY`      | `VARCHAR2(1)`  | `NULL`                                                             |
| `GENERATED`      | `VARCHAR2(1)`  | `NULL`                                                             |
| `SECONDARY`      | `VARCHAR2(1)`  | `NULL`                                                             |

#### ALL_TAB_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-9 ALL_TAB_COLUMNS

| Name                  | Type            | Value          |
|:----------------------|:----------------|:---------------|
| `OWNER`               | `VARCHAR2(30)`  | \-             |
| `TABLE_NAME`          | `VARCHAR2(30)`  | \-             |
| `COLUMN_NAME`         | `VARCHAR2(30)`  | \-             |
| `DATA_TYPE`           | `VARCHAR2(106)` | \-             |
| `DATA_TYPE_MOD`       | `VARCHAR2(3)`   | `NULL`         |
| `DATA_TYPE_OWNER`     | `VARCHAR2(30)`  | `NULL`         |
| `DATA_LENGTH`         | `NUMBER`        | \-             |
| `DATA_PRECISION`      | `NUMBER`        | \-             |
| `DATA_SCALE`          | `NUMBER`        | \-             |
| `NULLABLE`            | `VARCHAR2(1)`   | `"Y" `or` "N"` |
| `COLUMN_ID`           | `NUMBER`        | \-             |
| `DEFAULT_LENGTH`      | `NUMBER`        | `0`            |
| `DATA_DEFAULT`        | `LONG`          | `NULL`         |
| `NUM_DISTINCT`        | `NUMBER`        | `0`            |
| `LOW_VALUE`           | `RAW(32)`       | `NULL`         |
| `HIGH_VALUE`          | `RAW(32)`       | `NULL`         |
| `DENSITY`             | `NUMBER`        | `0`            |
| `NUM_NULLS`           | `NUMBER`        | `0`            |
| `NUM_BUCKETS`         | `NUMBER`        | `0`            |
| `LAST_ANALYZED`       | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`         | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`  | `VARCHAR2(44)`  | `NULL`         |
| `CHAR_COL_DEC_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`        | `VARCHAR2(3)`   | `NULL`         |
| `USER_STATS`          | `VARCHAR2(3)`   | `NULL`         |
| `AVG_COL_LEN`         | `NUMBER`        | `0`            |

#### ALL_TAB_COMMENTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-10 ALL_TAB_COMMENTS

| Name         | Type             | Value                 |
|:-------------|:-----------------|:----------------------|
| `OWNER`      | `VARCHAR2(30)`   | \-                    |
| `TABLE_NAME` | `VARCHAR2(30)`   | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)`   | `"TABLE"` or "`VIEW"` |
| `COMMENTS`   | `VARCHAR2(4000)` | `NULL`                |

#### ALL_TABLES

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-11 ALL_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `OWNER`                     | `VARCHAR2(30)` | \-     |
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(30)` | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(30)` | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(30)` | `NULL` |
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
| `LOGGING`                   | `VARCHAR2(3)`  | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`  | `NULL` |
| `NUM_ROWS`                  | `NUMBER`       | \-     |
| `BLOCKS`                    | `NUMBER`       | \-     |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(10)` | `NULL` |
| `INSTANCES`                 | `VARCHAR2(10)` | `NULL` |
| `CACHE`                     | `VARCHAR2(5)`  | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(8)`  | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(3)`  | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(12)` | `NULL` |
| `TEMPORARY`                 | `VARCHAR2(1)`  | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`  | `NULL` |
| `NESTED`                    | `VARCHAR2(3)`  | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(7)`  | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(8)`  | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(3)`  | `NULL` |
| `USER_STATS`                | `VARCHAR2(3)`  | `NULL` |
| `DURATION`                  | `VARHCAR2(15)` | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(8)`  | `NULL` |
| `MONITORING`                | `VARCHAR2(3)`  | `NULL` |

#### ALL_USERS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-12 ALL_USERS

| Name       | Type           | Value  |
|:-----------|:---------------|:-------|
| `USERNAME` | `VARCHAR2(30)` | \-     |
| `USER_ID`  | `NUMBER`       | `0`    |
| `CREATED`  | `DATE`         | `NULL` |

#### ALL_VIEWS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-13 ALL_VIEWS

| Name               | Type             | Value  |
|:-------------------|:-----------------|:-------|
| `OWNER`            | `VARCHAR2(30)`   | \-     |
| `VIEW_NAME`        | `VARCHAR2(30)`   | \-     |
| `TEXT_LENGTH`      | `NUMBER`         | `0`    |
| `TEXT`             | `LONG`           | `NULL` |
| `TYPE_TEXT_LENGTH` | `NUMBER`         | `0`    |
| `TYPE_TEXT`        | `VARCHAR2(4000)` | `NULL` |
| `OID_TEXT_LENGTH`  | `NUMBER`         | `0`    |
| `OID_TEXT`         | `VARCHAR2(4000)` | `NULL` |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(30)`   | `NULL` |
| `VIEW_TYPE`        | `VARCHAR2(30)`   | `NULL` |

#### DICTIONARY

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-14 DICTIONARY

| Name         | Type             | Value  |
|:-------------|:-----------------|:-------|
| `TABLE_NAME` | `VARCHAR2(30)`   | \-     |
| `COMMENTS`   | `VARCHAR2(4000)` | `NULL` |

#### DICT_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-15 DICT_COLUMNS

| Name          | Type             | Value  |
|:--------------|:-----------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-     |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-     |
| `COMMENTS`    | `VARCHAR2(4000)` | `NULL` |

#### USER_CATALOG

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-16 USER_CATALOG

| Name         | Type           | Value                                 |
|:-------------|:---------------|:--------------------------------------|
| `TABLE_NAME` | `VARCHAR2(30)` | \-                                    |
| `TABLE_TYPE` | `VARCHAR2(11)` | `"TABLE"` or, `"VIEW"` or `"SYNONYM"` |

#### USER_COL_COMMENTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-17 USER_COL_COMMENTS

| Name          | Type             | Value  |
|:--------------|:-----------------|:-------|
| `TABLE_NAME`  | `VARCHAR2(30)`   | \-     |
| `COLUMN_NAME` | `VARCHAR2(30)`   | \-     |
| `COMMENTS`    | `VARCHAR2(4000)` | `NULL` |

#### USER_CONS_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-18 USER_CONS_COLUMNS

| Name              | Type             | Value |
|:------------------|:-----------------|:------|
| `OWNER`           | `VARCHAR2(30)`   | \-    |
| `CONSTRAINT_NAME` | `VARCHAR2(30)`   | \-    |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-    |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | \-    |
| `POSITION`        | `NUMBER`         | \-    |

#### USER_CONSTRAINTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-19 USER_CONSTRAINTS

| Name                | Type           | Value                                        |
|:--------------------|:---------------|:---------------------------------------------|
| `OWNER`             | `VARCHAR2(30)` | \-                                           |
| `CONSTRAINT_NAME`   | `VARCHAR2(30)` | \-                                           |
| `CONSTRAINT_TYPE`   | `VARCHAR2(1)`  | `R` or `P`                                   |
| `TABLE_NAME`        | `VARCHAR2(30)` | \-                                           |
| `SEARCH_CONDITION`  | `LONG`         | `NULL`                                       |
| `R_OWNER`           | `VARCHAR2(30)` | \-                                           |
| `R_CONSTRAINT_NAME` | `VARCHAR2(30)` | \-                                           |
| `DELETE_RULE`       | `VARCHAR2(9)`  | `"CASCADE"` or `"NO ACTION`" or `"SET NULL"` |
| `STATUS`            | `VARCHAR2(8)`  | `NULL`                                       |
| `DEFERRABLE`        | `VARCHAR2(14)` | `NULL`                                       |
| `DEFERRED`          | `VARCHAR2(9)`  | `NULL`                                       |
| `VALIDATED`         | `VARCHAR2(13)` | `NULL`                                       |
| `GENERATED`         | `VARCHAR2(14)` | `NULL`                                       |
| `BAD`               | `VARCHAR2(3)`  | `NULL`                                       |
| `RELY`              | `VARCHAR2(4)`  | `NULL`                                       |
| `LAST_CHANGE`       | `DATE`         | `NULL`                                       |

#### USER_IND_COLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-20 USER_IND_COLUMNS

| Name              | Type             | Value               |
|:------------------|:-----------------|:--------------------|
| `INDEX_NAME`      | `VARCHAR2(30)`   | \-                  |
| `TABLE_NAME`      | `VARCHAR2(30)`   | \-                  |
| `COLUMN_NAME`     | `VARCHAR2(4000)` | `-`                 |
| `COLUMN_POSITION` | `NUMBER`         | `-`                 |
| `COLUMN_LENGTH`   | `NUMBER`         | `-`                 |
| `DESCEND`         | `VARCHAR2(4)`    | `"DESC"` or "`ASC"` |

#### USER_INDEXES

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-21 USER_INDEXES

| Name                      | Type             | Value                       |
|:--------------------------|:-----------------|:----------------------------|
| `INDEX_NAME`              | `VARCHAR2(30)`   | `-`                         |
| `INDEX_TYPE`              | `VARCHAR2(27)`   | `NULL`                      |
| `TABLE_OWNER`             | `VARCHAR2(30)`   | \-                          |
| `TABLE_NAME`              | `VARCHAR2(30)`   | \-                          |
| `TABLE_TYPE`              | `VARCHAR2(11)`   | `"TABLE"`                   |
| `UNIQUENESS`              | `VARCHAR2(9)`    | `"UNIQUE"` or `"NONUNIQUE"` |
| `COMPRESSION`             | `VARCHAR2(8)`    | `NULL`                      |
| `PREFIX_LENGTH`           | `NUMBER`         | `0`                         |
| `TABLESPACE_NAME`         | `VARCHAR2(30)`   | `NULL`                      |
| `INI_TRANS`               | `NUMBER`         | `0`                         |
| `MAX_TRANS`               | `NUMBER`         | `0`                         |
| `INITIAL_EXTENT`          | `NUMBER`         | `0`                         |
| `NEXT_EXTENT`             | `NUMBER`         | `0`                         |
| `MIN_EXTENTS`             | `NUMBER`         | `0`                         |
| `MAX_EXTENTS`             | `NUMBER`         | `0`                         |
| `PCT_INCREASE`            | `NUMBER`         | `0`                         |
| `PCT_THRESHOLD`           | `NUMBER`         | `0`                         |
| `INCLUDE_COLUMNS`         | `NUMBER`         | `0`                         |
| `FREELISTS`               | `NUMBER`         | `0`                         |
| `FREELIST_GROUPS`         | `NUMBER`         | `0`                         |
| `PCT_FREE`                | `NUMBER`         | `0`                         |
| `LOGGING`                 | `VARCHAR2(3)`    | `NULL`                      |
| `BLEVEL`                  | `NUMBER`         | `0`                         |
| `LEAF_BLOCKS`             | `NUMBER`         | `0`                         |
| `DISTINCT_KEYS`           | `NUMBER`         | \-                          |
| `AVG_LEAF_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `AVG_DATA_BLOCKS_PER_KEY` | `NUMBER`         | `0`                         |
| `CLUSTERING_FACTOR`       | `NUMBER`         | `0`                         |
| `STATUS`                  | `VARCHAR2(8)`    | `NULL`                      |
| `NUM_ROWS`                | `NUMBER`         | `0`                         |
| `SAMPLE_SIZE`             | `NUMBER`         | `0`                         |
| `LAST_ANALYZED`           | `DATE`           | `NULL`                      |
| `DEGREE`                  | `VARCHAR2(40)`   | `NULL`                      |
| `INSTANCES`               | `VARCHAR2(40)`   | `NULL`                      |
| `PARTITIONED`             | `VARCHAR2(3)`    | `NULL`                      |
| `TEMPORARY`               | `VARCHAR2(1)`    | `NULL`                      |
| `GENERATED`               | `VARCHAR2(1)`    | `NULL`                      |
| `SECONDARY`               | `VARCHAR2(1)`    | `NULL`                      |
| `BUFFER_POOL`             | `VARCHAR2(7)`    | `NULL`                      |
| `USER_STATS`              | `VARCHAR2(3)`    | `NULL`                      |
| `DURATION`                | `VARHCAR2(15)`   | `NULL`                      |
| `PCT_DIRECT_ACCESS`       | `NUMBER`         | `0`                         |
| `ITYP_OWNER`              | `VARCHAR2(30)`   | `NULL`                      |
| `ITYP_NAME`               | `VARCHAR2(30)`   | `NULL`                      |
| `PARAMETERS`              | `VARCHAR2(1000)` | `NULL`                      |
| `GLOBAL_STATS`            | `VARCHAR2(3)`    | `NULL`                      |
| `DOMIDX_STATUS`           | `VARCHAR2(12)`   | `NULL`                      |
| `DOMIDX_OPSTATUS`         | `VARCHAR2(6)`    | `NULL`                      |
| `FUNCIDX_STATUS`          | `VARCHAR2(8)`    | `NULL`                      |

#### USER_OBJECTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-22 USER_OBJECTS

| Name             | Type            | Value                                                      |
|:-----------------|:----------------|:-----------------------------------------------------------|
| `OBJECT_NAME`    | `VARCHAR2(128)` | \-                                                         |
| `SUBOBJECT_NAME` | `VARCHAR2(30)`  | `NULL`                                                     |
| `OBJECT_ID`      | `NUMBER`        | `0`                                                        |
| `DATA_OBJECT_ID` | `NUMBER`        | `0`                                                        |
| `OBJECT_TYPE`    | `VARCHAR2(18)`  | `"TABLE" or "VIEW" or "SYNONYM" or "INDEX" or "PROCEDURE"` |
| `CREATED`        | `DATE`          | `NULL`                                                     |
| `LAST_DDL_TIME`  | `DATE`          | `NULL`                                                     |
| `TIMESTAMP`      | `VARCHAR2(19)`  | `NULL`                                                     |
| `STATUS`         | `VARCHAR2(7)`   | `NULL`                                                     |
| `TEMPORARY`      | `VARCHAR2(1)`   | `NULL`                                                     |
| `GENERATED`      | `VARCHAR2(1)`   | `NULL`                                                     |
| `SECONDARY`      | `VARCHAR2(1)`   | `NULL`                                                     |

#### USER_TABCOLUMNS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-23 USER_TABCOLUMNS

| Name                   | Type            | Value          |
|:-----------------------|:----------------|:---------------|
| `TABLE_NAME`           | `VARCHAR2(30)`  | \-             |
| `COLUMN_NAME`          | `VARCHAR2(30)`  | \-             |
| `DATA_TYPE`            | `VARCHAR2(106)` | \-             |
| `DATA_TYPE_MOD`        | `VARCHAR2(3)`   | `NULL`         |
| `DATA_TYPE_OWNER`      | `VARCHAR2(30)`  | `NULL`         |
| `DATA_LENGTH`          | `NUMBER`        | \-             |
| `DATA_PRECISION`       | `NUMBER`        | \-             |
| `DATA_SCALE`           | `NUMBER`        | \-             |
| `NULLABLE`             | `VARCHAR2(1)`   | `"Y"` or "`N"` |
| `COLUMN_ID`            | `NUMBER`        | \-             |
| `DEFAULT_LENGTH`       | `NUMBER`        | `NULL`         |
| `DATA_DEFAULT`         | `LONG`          | `NULL`         |
| `NUM_DISTINCT`         | `NUMBER`        | `NULL`         |
| `LOW_VALUE`            | `RAW(32)`       | `NULL`         |
| `HIGH_VALUE`           | `RAW(32)`       | `NULL`         |
| `DENSITY`              | `NUMBER`        | `0`            |
| `NUM_NULLS`            | `NUMBER`        | `0`            |
| `NUM_BUCKETS`          | `NUMBER`        | `0`            |
| `LAST_ANALYZED`        | `DATE`          | `NULL`         |
| `SAMPLE_SIZE`          | `NUMBER`        | `0`            |
| `CHARACTER_SET_NAME`   | `VARCHAR2(44)`  | `NULL`         |
| `CHAR_COL_DECL_LENGTH` | `NUMBER`        | `0`            |
| `GLOBAL_STATS`         | `VARCHAR2(3)`   | `NULL`         |
| `USER_STATS`           | `VARCHAR2(3)`   | `NULL`         |
| `AVG_COL_LEN`          | `NUMBER`        | `0`            |

#### USER_TAB_COMMENTS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-24 USER_TAB_COMMENTS

| Name         | Type             | Value                 |
|:-------------|:-----------------|:----------------------|
| `TABLE_NAME` | `VARCHAR2(30)`   | \-                    |
| `TABLE_TYPE` | `VARCHAR2(11)`   | `"TABLE"` or `"VIEW"` |
| `COMMENTS`   | `VARCHAR2(4000)` | `NULL`                |

#### USER_TABLES

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-25 USER_TABLES

| Name                        | Type           | Value  |
|:----------------------------|:---------------|:-------|
| `TABLE_NAME`                | `VARCHAR2(30)` | \-     |
| `TABLESPACE_NAME`           | `VARCHAR2(30)` | `NULL` |
| `CLUSTER_NAME`              | `VARCHAR2(30)` | `NULL` |
| `IOT_NAME`                  | `VARCHAR2(30)` | `NULL` |
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
| `LOGGING`                   | `VARCHAR2(3)`  | `NULL` |
| `BACKED_UP`                 | `VARCHAR2(1)`  | `NULL` |
| `NUM_ROWS`                  | `NUMBER`       | \-     |
| `BLOCKS`                    | `NUMBER`       | \-     |
| `EMPTY_BLOCKS`              | `NUMBER`       | `0`    |
| `AVG_SPACE`                 | `NUMBER`       | `0`    |
| `CHAIN_CNT`                 | `NUMBER`       | `0`    |
| `AVG_ROW_LEN`               | `NUMBER`       | `0`    |
| `AVG_SPACE_FREELIST_BLOCKS` | `NUMBER`       | `0`    |
| `NUM_FREELIST_BLOCKS`       | `NUMBER`       | `0`    |
| `DEGREE`                    | `VARCHAR2(10)` | `NULL` |
| `INSTANCES`                 | `VARCHAR2(10)` | `NULL` |
| `CACHE`                     | `VARCHAR2(5)`  | `NULL` |
| `TABLE_LOCK`                | `VARCHAR2(8)`  | `NULL` |
| `SAMPLE_SIZE`               | `NUMBER`       | `0`    |
| `LAST_ANALYZED`             | `DATE`         | `NULL` |
| `PARTITIONED`               | `VARCHAR2(3)`  | `NULL` |
| `IOT_TYPE`                  | `VARCHAR2(12)` | `NULL` |
| `TEMPORARY`                 | `VARHCAR2(1)`  | `NULL` |
| `SECONDARY`                 | `VARCHAR2(1)`  | `NULL` |
| `NESTED`                    | `VARCHAR2(3)`  | `NULL` |
| `BUFFER_POOL`               | `VARCHAR2(7)`  | `NULL` |
| `ROW_MOVEMENT`              | `VARCHAR2(8)`  | `NULL` |
| `GLOBAL_STATS`              | `VARCHAR2(3)`  | `NULL` |
| `USER_STATS`                | `VARCHAR2(3)`  | `NULL` |
| `DURATION`                  | `VARCHAR2(15)` | `NULL` |
| `SKIP_CORRUPT`              | `VARCHAR2(8)`  | `NULL` |
| `MONITORING`                | `VARCHAR2(3)`  | `NULL` |

#### USER_USERS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-26 USER_USERS

| Name                          | Type             | Value  |
|:------------------------------|:-----------------|:-------|
| `USERNAME`                    | `VARCHAR2(30)`   | \-     |
| `USER_ID`                     | `NUMBER`         | `0`    |
| `ACCOUNT_STATUS`              | `VARCHAR2(32)`   | `OPEN` |
| `LOCK_DATE`                   | `DATE`           | `NULL` |
| `EXPIRY_DATE`                 | `DATE`           | `NULL` |
| `DEFAULT_TABLESPACE`          | `VARCHAR2(30)`   | `NULL` |
| `TEMPORARY_TABLESPACE`        | `VARCHAR2(30)`   | `NULL` |
| `CREATED`                     | `DATE`           | `NULL` |
| `INITIAL_RSRC_CONSUMER_GROUP` | `VARCHAR2(30)`   | `NULL` |
| `EXTERNAL_NAME`               | `VARCHAR2(4000)` | `NULL` |

#### USER_VIEWS

The Oracle Database Gateway for ODBC data dictionary tables and views provide the following information:

- Name, data type, and width of each column

- The contents of columns with fixed values

Table C-27 USER_VIEWS

| Name               | Type             | Value  |
|:-------------------|:-----------------|:-------|
| `VIEW_NAME`        | `VARCHAR2(30)`   | \-     |
| `TEXT_LENGTH`      | `NUMBER`         | `0`    |
| `TEXT`             | `LONG`           | `NULL` |
| `TYPE_TEXT_LENGTH` | `NUMBER`         | `0`    |
| `TYPE_TEXT`        | `VARCHAR2(4000)` | `NULL` |
| `OID_TEXT_LENGTH`  | `NUMBER`         | `0`    |
| `OID_TEXT`         | `VARCHAR2(4000)` | `NULL` |
| `VIEW_TYPE_OWNER`  | `VARCHAR2(30)`   | `NULL` |
| `VIEW_TYPE`        | `VARCHAR2(30)`   | `NULL` |
