The following section covers the Oracle Database Gateway for DRDA data dictionary views accessible to all users of Oracle database. Any user with `SELECT` privileges for DB2 catalog tables can access most of the views.

N/A is used in the tables to denote that the column is not valid for the gateway.

### Supported Views

The following is a list of Oracle data dictionary views that are supported by the gateway for DB2 UDB for z/OS, DB2 UDB for iSeries, and DB2/UDB DRDA servers.

- `ALL_CATALOG`

- `ALL_COL_COMMENTS`

- `ALL_CONS_COLUMNS`

- `ALL_CONSTRAINTS`

- `ALL_INDEXES`

- `ALL_IND_COLUMNS`

- `ALL_OBJECTS`

- `ALL_SYNONYMS`

- `ALL_TAB_COMMENTS`

- `ALL_TABLES`

- `ALL_TAB_COLUMNS`

- `ALL_USERS`

- `ALL_VIEWS`

- `COL_PRIVILEGES`

- `DICTIONARY`

- `DUAL`

- `TABLE_PRIVILEGES`

- `USER_CATALOG`

- `USER_COL_COMMENTS`

- `USER_CONSTRAINTS`

- `USER_CONS_COLUMNS`

- `USER_INDEXES`

- `USER_OBJECTS`

- `USER_SYNONYMS`

- `USER_TABLES`

- `USER_TAB_COLUMNS`

- `USER_TAB_COMMENTS`

- `USER_USERS`

- `USER_VIEWS`

### ALL_CATALOG

The `ALL_CATALOG` view contains all tables, views, synonyms, and sequence accessible to the user.

| Column name  | Description         |
|:-------------|:--------------------|
| `OWNER`      | Owner of the object |
| `TABLE_NAME` | Name of the object  |
| `TABLE_TYPE` | Type of object      |

### ALL_COL_COMMENTS

The `ALL_COL_COMMENTS` view contains comments on columns of accessible tables and views.

| Column name   | Description         |
|:--------------|:--------------------|
| `OWNER`       | Owner of the object |
| `TABLE_NAME`  | Object name         |
| `COLUMN_NAME` | Column name         |
| `COMMENTS`    | Comments on column  |

### ALL_CONS_COLUMNS

The `ALL_CONS_COLUMNS` view contains information about accessible columns in constraint definitions.

| Column name       | Description                                               |
|:------------------|:----------------------------------------------------------|
| `OWNER`           | Owner of the constraint definition                        |
| `CONSTRAINT_NAME` | Name of the constraint definition                         |
| `TABLE_NAME`      | Name of the table with a constraint definition            |
| `COLUMN_NAME`     | Name of the column specified in the constraint definition |
| `POSITION`        | Original position of column in definition                 |

### ALL_CONSTRAINTS

The `ALL_CONSTRAINTS` view contains constraint definitions on accessible tables.

| Column name         | Description                                                    |
|:--------------------|:---------------------------------------------------------------|
| `OWNER`             | Owner of the constraint definition                             |
| `CONSTRAINT_NAME`   | Name of the constraint definition                              |
| `CONSTRAINT_TYPE`   | Type of the constraint definition                              |
| `TABLE_NAME`        | Name of the table with constraint definition                   |
| `SEARCH_CONDITION`  | Text of the search condition for table check                   |
| `R_OWNER`           | Owner of the table used in referential constraint              |
| `R_CONSTRAINT_NAME` | Name of the unique constraint definition for referenced table  |
| `DELETE_RULE`       | Delete rule for a referential constraint                       |
| `STATUS`            | Status of a constraint                                         |
| `DEFERRABLE`        | Whether the constraint is deferrable                           |
| `DEFERRED`          | Whether the constraint was initially deferred                  |
| `VALIDATED`         | Whether all data obeys the constraint                          |
| `GENERATED`         | Whether the name of the constraint is user or system generated |
| `BAD`               | Constraint specifies a century in an ambiguous manner          |
| `RELY`              | Whether an enabled constraint is enforced or unenforced        |
| `LAST_CHANGE`       | When the constraint was last enabled                           |
| `INDEX_OWNER`       | N/A                                                            |
| `INDEX_NAME`        | N/A                                                            |

### ALL_INDEXES

The `ALL_INDEXES` view contains description of indexes on tables accessible to the user.

| Column name               | Description                                                                                                                                                      |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                   | Owner of the index                                                                                                                                               |
| `INDEX_NAME`              | Name of the index                                                                                                                                                |
| `INDEX_TYPE`              | Type of the index                                                                                                                                                |
| `TABLE_OWNER`             | Owner of the indexed object                                                                                                                                      |
| `TABLE_NAME`              | Name of the indexed object                                                                                                                                       |
| `TABLE_TYPE`              | Type of the indexed object                                                                                                                                       |
| `UNIQUENESS`              | Uniqueness status of the index                                                                                                                                   |
| `COMPRESSION`             | N/A                                                                                                                                                              |
| `PREFIX_LENGTH`           | 0                                                                                                                                                                |
| `TABLESPACE_NAME`         | Name of the tablespace containing the index                                                                                                                      |
| `INI_TRANS`               | N/A                                                                                                                                                              |
| `MAX_TRANS`               | N/A                                                                                                                                                              |
| `INITIAL_EXTENT`          | N/A                                                                                                                                                              |
| `NEXT_EXTENT`             | N/A                                                                                                                                                              |
| `MIN_EXTENTS`             | N/A                                                                                                                                                              |
| `MAX_EXTENTS`             | N/A                                                                                                                                                              |
| `PCT_INCREASE`            | N/A                                                                                                                                                              |
| `PCT_THRESHOLD`           | Threshold percentage of block space allowed per index entry                                                                                                      |
| `INCLUDE_COLUMN`          | Column ID of the last column to be included in an index-organized table                                                                                          |
| `FREELISTS`               | Number of process freelists allocated to this segment                                                                                                            |
| `FREELIST_GROUPS`         | Number of freelist groups allocated to this segment                                                                                                              |
| `PCT_FREE`                | N/A                                                                                                                                                              |
| `LOGGING`                 | Logging information                                                                                                                                              |
| `BLEVEL`                  | Depth of the index from its root block to its leaf blocks. A depth of 1 indicates that the root block and the leaf block are the same.                           |
| `LEAF_BLOCKS`             | Number of leaf blocks in the index                                                                                                                               |
| `DISTINCT_KEYS`           | Number of distinct indexed values. For indexes that enforce `UNIQUE` and `PRIMARY` `KEY` constraints, this value is the same as the number of rows in the table. |
| `AVG_LEAF_BLOCKS_PER_KEY` | N/A                                                                                                                                                              |
| `AVG_DATA_BLOCKS_PER_KEY` | N/A                                                                                                                                                              |
| `CLUSTERING_FACTOR`       | N/A                                                                                                                                                              |
| `STATUS`                  | State of the index: `VALID`                                                                                                                                      |
| `NUM_ROWS`                | Number of rows in the index                                                                                                                                      |
| `SAMPLE_SIZE`             | Size of the sample used to analyze the index                                                                                                                     |
| `LAST_ANALYZED`           | Date on which an index was most recently analyzed                                                                                                                |
| `DEGREE`                  | Number of threads per instance for scanning the index                                                                                                            |
| `INSTANCES`               | Number of instances across which the index is to be scanned                                                                                                      |
| `PARTITIONED`             | Whether the index is partitioned                                                                                                                                 |
| `TEMPORARY`               | Whether the index is on a temporary table                                                                                                                        |
| `GENERATED`               | Whether the name of the index is system generated                                                                                                                |
| `SECONDARY`               | N/A                                                                                                                                                              |
| `BUFFER_POOL`             | Whether the index is a secondary object                                                                                                                          |
| `USER_STATS`              | N/A                                                                                                                                                              |
| `DURATION`                | N/A                                                                                                                                                              |
| `PCT_DIRECT_ACCESS`       | N/A                                                                                                                                                              |
| `ITYP_OWNER`              | N/A                                                                                                                                                              |
| `ITYP_NAME`               | N/A                                                                                                                                                              |
| `PARAMETERS`              | N/A                                                                                                                                                              |
| `GLOBAL_STATS`            | N/A                                                                                                                                                              |
| `DOMIDX_STATUS`           | N/A                                                                                                                                                              |
| `DOMIDX_OPSTATUS`         | N/A                                                                                                                                                              |
| `FUNCIDX_STATUS`          | N/A                                                                                                                                                              |
| `JOIN_INDEX`              | N/A                                                                                                                                                              |
| `IOT_REDUNDANT_PKEY_ELIM` | N/A                                                                                                                                                              |

### ALL_IND_COLUMNS

The `ALL_IND_COLUMNS` view contains the columns of indexes on all tables that are accessible to the current user.

| Column names      | Description                                            |
|:------------------|:-------------------------------------------------------|
| `INDEX_OWNER`     | Owner of the index                                     |
| `INDEX_NAME`      | Name of the index                                      |
| `TABLE_OWNER`     | Owner of the table or cluster                          |
| `TABLE_NAME`      | Name of the table or cluster                           |
| `COLUMN_NAME`     | Column name or attribute of object type column         |
| `COLUMN_POSITION` | Position of a column or attribute within the index     |
| `COLUMN_LENGTH`   | Indexed length of the column                           |
| `CHAR_LENGTH`     | Maximum codepoint length of the column                 |
| `DESCEND`         | Whether the column is sorted in descending order (Y/N) |

### ALL_OBJECTS

The `ALL_OBJECTS` view contains objects accessible to the user.

| Column name      | Description                                                      |
|:-----------------|:-----------------------------------------------------------------|
| `OWNER`          | Owner of the object                                              |
| `OBJECT_NAME`    | Name of object                                                   |
| `SUBOBJECT_NAME` | Name of the subobject                                            |
| `OBJECT_ID`      | Object number of the object                                      |
| `DATA_OBJECT_ID` | Dictionary object number of the segment that contains the object |
| `OBJECT_TYPE`    | Type of object                                                   |
| `CREATED`        | N/A                                                              |
| `LAST_DDL_TIME`  | N/A                                                              |
| `TIMESTAMP`      | N/A                                                              |
| `STATUS`         | State of the object                                              |
| `TEMPORARY`      | Whether the object is temporary                                  |
| `GENERATED`      | Whether the name of this object system is generated              |
| `SECONDARY`      | N/A                                                              |

### ALL_SYNONYMS

The `ALL_SYNONYMS` view contains all synonyms accessible to the user.

| Column name    | Description                                   |
|:---------------|:----------------------------------------------|
| `OWNER`        | Owner of the synonym                          |
| `SYNONYM_NAME` | Name of the synonym                           |
| `TABLE_OWNER`  | Owner of the object referenced by the synonym |
| `TABLE_NAME`   | Name of the object referenced by the synonym  |
| `DB_LINK`      | N/A                                           |

### ALL_TABLES

The `ALL_TABLES` view contains description of tables accessible to the user.

| Column name                 | Description                                                                 |
|:----------------------------|:----------------------------------------------------------------------------|
| `OWNER`                     | Owner of the table                                                          |
| `TABLE_NAME`                | Name of the table                                                           |
| `TABLESPACE_NAME`           | Name of the tablespace containing the table                                 |
| `CLUSTER_NAME`              | N/A                                                                         |
| `IOT_NAME`                  | Name of the index organized table                                           |
| `PCT_FREE`                  | N/A                                                                         |
| `PCT_USED`                  | N/A                                                                         |
| `INI_TRANS`                 | N/A                                                                         |
| `MAX_TRANS`                 | N/A                                                                         |
| `INITIAL_EXTENT`            | N/A                                                                         |
| `NEXT_EXTENT`               | N/A                                                                         |
| `MIN_EXTENTS`               | N/A                                                                         |
| `MAX_EXTENTS`               | N/A                                                                         |
| `PCT_INCREASE`              | N/A                                                                         |
| `FREELISTS`                 | Number of process freelists allocated to this segment                       |
| `FREELIST_GROUPS`           | Number of freelist groups allocated to this segment                         |
| `LOGGING`                   | Logging attribute                                                           |
| `BACKED_UP`                 | N/A                                                                         |
| `NUM_ROWS`                  | Number of rows in the table                                                 |
| `BLOCKS`                    | N/A                                                                         |
| `EMPTY_BLOCKS`              | N/A                                                                         |
| `AVG_SPACE`                 | N/A                                                                         |
| `CHAIN_CNT`                 | N/A                                                                         |
| `AVG_ROW_LEN`               | Average length of a row in the table in bytes                               |
| `AVG_SPACE_FREELIST_BLOCKS` | Average freespace of all blocks on a freelist                               |
| `NUM_FREELIST_BLOCKS`       | Number of blocks on the freelist                                            |
| `DEGREE`                    | Number of threads per instance for scanning the table                       |
| `INSTANCES`                 | Number of instances across which the table is to be scanned                 |
| `CACHE`                     | Whether the cluster is to be cached in the buffer cache                     |
| `TABLE_LOCK`                | Whether the table locking is enabled or disabled                            |
| `SAMPLE_SIZE`               | Sample size used in analyzing this table                                    |
| `LAST_ANALYZED`             | Date on which this table was most recently analyzed                         |
| `PARTITIONED`               | Whether this table is partitioned                                           |
| `IOT_TYPE`                  | Whether the table is an index-organized table                               |
| `TEMPORARY`                 | Can the current session only see data that it placed in this object itself? |
| `SECONDARY`                 | N/A                                                                         |
| `NESTED`                    | Whether the table is a nested table                                         |
| `BUFFER_POOL`               | Default buffer pool for the object                                          |
| `ROW_MOVEMENT`              | N/A                                                                         |
| `GLOBAL_STATS`              | N/A                                                                         |
| `USER_STATS`                | N/A                                                                         |
| `DURATION`                  | N/A                                                                         |
| `SKIP_CORRUPT`              | N/A                                                                         |
| `MONITORING`                | N/A                                                                         |
| `CLUSTER_OWNER`             | N/A                                                                         |
| `DEPENDENCIES`              | N/A                                                                         |
| `COMPRESSION`               | N/A                                                                         |

### ALL_TAB_COLUMNS

The `ALL_TAB_COLUMNS` view contains columns of all tables, views, and clusters accessible to the user.

| Column name            | Description                                                                                                                                                                                                    |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                | Owner of the table or view                                                                                                                                                                                     |
| `TABLE_NAME`           | Table or view name                                                                                                                                                                                             |
| `COLUMN_NAME`          | Column name                                                                                                                                                                                                    |
| `DATA_TYPE`            | Data type of the column                                                                                                                                                                                        |
| `DATA_TYPE_MOD`        | Data type modifier of the column                                                                                                                                                                               |
| `DATA_TYPE_OWNER`      | Owner of the data type of the column                                                                                                                                                                           |
| `DATA_LENGTH`          | Maximum length of the column in bytes                                                                                                                                                                          |
| `DATA_PRECISION`       | N/A                                                                                                                                                                                                            |
| `DATA_SCALE`           | Digits to the right of decimal point in a number                                                                                                                                                               |
| `NULLABLE`             | Whether the column permits nulls? Value is n if there is a `NOT NULL` constraint on the column or if the column is part of a `PRIMARY` key.                                                                    |
| `COLUMN_ID`            | Sequence number of the column as created                                                                                                                                                                       |
| `DEFAULT_LENGTH`       | N/A                                                                                                                                                                                                            |
| `DATA_DEFAULT`         | N/A                                                                                                                                                                                                            |
| `NUM_DISTINCT`         | Number of distinct values in each column of the table                                                                                                                                                          |
| `LOW_VALUE`            | For tables with more than three rows, the second lowest and second highest values. These statistics are expressed in hexadecimal notation for the internal representation of the first 32 bytes of the values. |
| `HIGH_VALUE`           | N/A                                                                                                                                                                                                            |
| `DENSITY`              | N/A                                                                                                                                                                                                            |
| `NUM_NULLS`            | Number of nulls in the column                                                                                                                                                                                  |
| `NUM_BUCKETS`          | Number of buckets in histogram for the column                                                                                                                                                                  |
| `LAST_ANALYZED`        | Date on which this column was most recently analyzed                                                                                                                                                           |
| `SAMPLE_SIZE`          | Sample size used in analyzing this column                                                                                                                                                                      |
| `CHARACTER_SET_NAME`   | Name of the character set                                                                                                                                                                                      |
| `CHAR_COL_DECL_LENGTH` | Length of the character set                                                                                                                                                                                    |
| `GLOBAL_STATS`         | N/A                                                                                                                                                                                                            |
| `USER_STATS`           | N/A                                                                                                                                                                                                            |
| `AVG_COL_LEN`          | Average length of the column (in bytes)                                                                                                                                                                        |
| `CHAR_LENGTH`          | Displays the length of the column in characters                                                                                                                                                                |
| `CHAR_USED`            | N/A                                                                                                                                                                                                            |

### ALL_TAB_COMMENTS

The `ALL_TAB_COMMENTS` view contains comments on tables and views accessible to the user.

| Column name  | Description            |
|:-------------|:-----------------------|
| `OWNER`      | Owner of the object    |
| `TABLE_NAME` | Name of the object     |
| `TABLE_TYPE` | Type of the object     |
| `COMMENTS`   | Comments on the object |

### ALL_USERS

The `ALL_USERS` contains information about all users of the database.

| Column name | Description      |
|:------------|:-----------------|
| `USERNAME`  | Name of the user |
| `USER_ID`   | N/A              |
| `CREATED`   | N/A              |

### ALL_VIEWS

The `ALL_VIEWS` view contains text of views accessible to the user.

| Column name        | Description                                                |
|:-------------------|:-----------------------------------------------------------|
| `OWNER`            | Owner of the view                                          |
| `VIEW_NAME`        | Name of the view                                           |
| `TEXT_LENGTH`      | `ALL_VIEWS` view will return `0` for `TEXT_LENGTH` column  |
| `TEXT`             | `ALL_VIEWS` view will return `NULL` for `TEXT` column      |
| `TYPE_TEXT_LENGTH` | Length of the type clause of the typed view                |
| `TYPE_TEXT`        | Type clause of the typed view                              |
| `OID_TEXT_LENGTH`  | Length of the `WITH OID` clause of the typed view          |
| `OID_TEXT`         | `WITH OID` clause of the typed view                        |
| `VIEW_TYPE_OWNER`  | Owner of the type of the view, if the view is a typed view |
| `VIEW_TYPE`        | Type of the view, if the view is a typed view              |
| `SUPERVIEW_NAME`   | N/A                                                        |

### COLUMN_PRIVILEGES

The `COLUMN_PRIVILEGES` view contains grants on columns for which the user is the grantor, grantee, or owner, or, the grantee is `PULBLIC`.

| Column name       | Description                                 |
|:------------------|:--------------------------------------------|
| `GRANTEE`         | Name of the user to whom access was granted |
| `OWNER`           | Username of the owner of the object         |
| `TABLE_NAME`      | Name of the object                          |
| `COLUMN_NAME`     | Name of the column                          |
| `GRANTOR`         | Name of the user who performed the grant    |
| `INSERT_PRIV`     | Permission to insert into the column        |
| `UPDATE_PRIV`     | Permission to update the column             |
| `REFERENCES_PRIV` | Permission to reference the column          |
| `CREATED`         | Timestamp for the grant                     |

### DICTIONARY

The `DICTIONARY` view contains list or data dictionary tables.

| Column name  | Description              |
|:-------------|:-------------------------|
| `TABLE_NAME` | Table name               |
| `COMMENTS`   | Description of the table |

### DUAL

The `DUAL` view contains list of dual tables.

| Column name | Description    |
|:------------|:---------------|
| `DUMMY`     | A dummy column |

### TABLE_PRIVILEGES

The `TABLE_PRIVILEGES` view contains grants on objects for which the user is the grantor, grantee, or owner, or, the grantee is `PUBLIC`.

| Column name       | Description                                        |
|:------------------|:---------------------------------------------------|
| `GRANTEE`         | Name of the user to whom access is granted         |
| `OWNER`           | Owner of the object                                |
| `TABLE_NAME`      | Name of the object                                 |
| `GRANTOR`         | Name of the user who performed the grant           |
| `SELECT_PRIV`     | Permission to select data from an object           |
| `INSERT_PRIV`     | Permission to insert data into an object           |
| `DELETE_PRIV`     | Permission to delete data from an object           |
| `UPDATE``_PRIV`   | Permission to update an object                     |
| `REFERENCES_PRIV` | N/A                                                |
| `ALTER_PRIV`      | Permission to alter an object                      |
| `INDEX_PRIV`      | Permission to create or drop an index on an object |
| `CREATED`         | Timestamp for the grant                            |

### USER_CATALOG

The `USER_CATALOG` view contains tables, views, synonyms, and sequences owned by the user.

| Column name  | Description        |
|:-------------|:-------------------|
| `TABLE_NAME` | Name of the object |
| `TABLE_TYPE` | Type of the object |

### USER_COL_COMMENTS

The `USER_COL_COMMENTS` view contains comments on columns of tables and views owned by the user.

| Column name   | Description            |
|:--------------|:-----------------------|
| `TABLE_NAME`  | Name of the object     |
| `COLUMN_NAME` | Name of the column     |
| `COMMENTS`    | Comments on the column |

### USER_CONSTRAINTS

The `USER_CONSTRAINTS` view contains constraint definitions on tables owned by the user.

| Column name         | Description                                                    |
|:--------------------|:---------------------------------------------------------------|
| `OWNER`             | Owner of the constraint definition                             |
| `CONSTRAINT_NAME`   | Name associated with the constraint definition                 |
| `CONSTRAINT_TYPE`   | Type of the constraint definition                              |
| `TABLE_NAME`        | Name associated with the table with constraint definition      |
| `SEARCH_CONDITION`  | Text of the search condition for table check                   |
| `R_OWNER`           | Owner of table used in referential constraint                  |
| `R_CONSTRAINT_NAME` | Name of the unique constraint definition for referenced table  |
| `DELETE_RULE`       | Delete rule for referential constraint                         |
| `STATUS`            | Status of a constraint                                         |
| `DEFERRABLE`        | Whether the constraint is deferrable                           |
| `DEFERRED`          | Whether the constraint was initially deferred                  |
| `VALIDATED`         | Whether all data obeys the constraint                          |
| `GENERATED`         | Whether the name of the constraint is user or system generated |
| `BAD`               | Constraint specifies a century in an ambiguous manner          |
| `LAST_CHANGE`       | When the constraint was last enabled                           |
| `INDEX_OWNER`       | N/A                                                            |
| `INDEX_NAME`        | N/A                                                            |

### USER_CONS_COLUMNS

The `USER_CONS_COLUMNS` contains information about columns in constraint definitions owned by the user.

| Column name       | Description                                                        |
|:------------------|:-------------------------------------------------------------------|
| `OWNER`           | Owner of the constraint definition                                 |
| `CONSTRAINT_NAME` | Name associated with the constraint definition                     |
| `TABLE_NAME`      | Name associated with table with constraint definition              |
| `COLUMN_NAME`     | Name associated with column specified in the constraint definition |
| `POSITION`        | Original position of column in definition                          |

### USER_INDEXES

The `USER_INDEXES` view contains description of the user's indexes:

| Column name               | Description                                                                                                                                                    |
|:--------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `INDEX_NAME`              | Name of the index                                                                                                                                              |
| `INDEX_TYPE`              | Type of index                                                                                                                                                  |
| `TABLE_OWNER`             | Owner of the indexed object                                                                                                                                    |
| `TABLE_NAME`              | Name of the indexed object                                                                                                                                     |
| `TABLE_TYPE`              | Type of the indexed object                                                                                                                                     |
| `UNIQUENESS`              | Uniqueness status of the index                                                                                                                                 |
| `COMPRESSION`             | N/A                                                                                                                                                            |
| `PREFIX_LENGTH`           | 0                                                                                                                                                              |
| `TABLESPACE_NAME`         | Name of the tablespace containing the index                                                                                                                    |
| `INI_TRANS`               | N/A                                                                                                                                                            |
| `MAX_TRANS`               | N/A                                                                                                                                                            |
| `INITIAL_EXTENT`          | N/A                                                                                                                                                            |
| `NEXT_EXTENT`             | N/A                                                                                                                                                            |
| `MIN_EXTENTS`             | N/A                                                                                                                                                            |
| `MAX_EXTENTS`             | N/A                                                                                                                                                            |
| `PCT_INCREASE`            | N/A                                                                                                                                                            |
| `PCT_THRESHOLD`           | Threshold percentage of block space allowed per index entry                                                                                                    |
| `INCLUDE_COLUMN`          | Column ID of the last column to be included in index-organized table                                                                                           |
| `FREELISTS`               | Number of process freelists allocated to a segment                                                                                                             |
| `FREELIST_GROUPS`         | Number of freelist groups allocated to a segment                                                                                                               |
| `PCT_FREE`                | N/A                                                                                                                                                            |
| `LOGGING`                 | Logging information                                                                                                                                            |
| `BLEVEL`                  | Depth of the index from its root block to its leaf blocks. A depth of 1 indicates that the root and leaf block are the same.                                   |
| `LEAF_BLOCKS`             | Number of leaf blocks in the index                                                                                                                             |
| `DISTINCT_KEYS`           | Number of distinct indexed values. For indexes that enforce `UNIQUE` and `PRIMARY KEY` constraints, this value is the same as the number of rows in the table. |
| `AVG_LEAF_BLOCKS_PER_KEY` | N/A                                                                                                                                                            |
| `AVG_DATA_BLOCKS_PER_KEY` | N/A                                                                                                                                                            |
| `CLUSTERING_FACTOR`       | N/A                                                                                                                                                            |
| `STATUS`                  | State of the indexes: `VALID`                                                                                                                                  |
| `NUM_ROWS`                | Number of rows in the index                                                                                                                                    |
| `SAMPLE_SIZE`             | Size of the sample used to analyze the index                                                                                                                   |
| `LAST_ANALYZED`           | Date on which the index was most recently analyzed                                                                                                             |
| `DEGREE`                  | Number of threads per instance for scanning the index                                                                                                          |
| `INSTANCES`               | Number of instances across which the index is to be scanned                                                                                                    |
| `PARTITIONED`             | Whether the index is partitioned                                                                                                                               |
| `TEMPORARY`               | Whether the index is on a temporary table                                                                                                                      |
| `GENERATED`               | Whether the name of the index is system generated                                                                                                              |
| `SECONDARY`               | N/A                                                                                                                                                            |
| `BUFFER_POOL`             | Whether the index is a secondary object                                                                                                                        |
| `USER_STATS`              | N/A                                                                                                                                                            |
| `DURATION`                | N/A                                                                                                                                                            |
| `PCT_DIRECT_ACCESS`       | N/A                                                                                                                                                            |
| `ITYP_OWNER`              | N/A                                                                                                                                                            |
| `ITYP_NAME`               | N/A                                                                                                                                                            |
| `PARAMETERS`              | N/A                                                                                                                                                            |
| `GLOBAL_STATS`            | N/A                                                                                                                                                            |
| `DOMIDX_STATUS`           | N/A                                                                                                                                                            |
| `DOMIDX_OPSTATUS`         | N/A                                                                                                                                                            |
| `FUNCIDX_STATUS`          | N/A                                                                                                                                                            |
| `JOIN_INDEX`              | N/A                                                                                                                                                            |
| `IOT_REDUNDANT_PKEY_ELIM` | N/A                                                                                                                                                            |

### USER_OBJECTS

The `USER_OBJECTS` view contains objects owned by the user.

| Column name      | Description                                                      |
|:-----------------|:-----------------------------------------------------------------|
| `OBJECT_NAME`    | Name of the object                                               |
| `SUBOBJECT_NAME` | Name of the subobject                                            |
| `OBJECT_ID`      | Object number of the object                                      |
| `DATA_OBJECT_ID` | Dictionary object number of the segment that contains the object |
| `OBJECT_TYPE`    | Type of object                                                   |
| `CREATED`        | N/A                                                              |
| `LAST_DDL_TIME`  | N/A                                                              |
| `TIMESTAMP`      | N/A                                                              |
| `STATUS`         | State of the object: `VALID`                                     |
| `TEMPORARY`      | Whether the object is temporary                                  |
| `GENERATED`      | Was the name of this object system generated?                    |
| `SECONDARY`      | N/A                                                              |

### USER_SYNONYMS

The `USER_SYNONYMS` view contains the private synonyms of the user.

| Column name    | Description                                   |
|:---------------|:----------------------------------------------|
| `SYNONYM_NAME` | Name of the synonym                           |
| `TABLE_OWNER`  | Owner of the object referenced by the synonym |
| `TABLE_NAME`   | Name of the object referenced by the synonym  |
| `DB_LINK`      | N/A                                           |

### USER_TABLES

The `USER_TABLES` view contains description of the tables owned by the user.

| Column name                 | Description                                                                 |
|:----------------------------|:----------------------------------------------------------------------------|
| `TABLE_NAME`                | Name of the table                                                           |
| `TABLESPACE_NAME`           | Name of the tablespace containing the table                                 |
| `CLUSTER_NAME`              | N/A                                                                         |
| `IOT_NAME`                  | Name of the index organized table                                           |
| `PCT_FREE`                  | N/A                                                                         |
| `PCT_USED`                  | N/A                                                                         |
| `INI_TRANS`                 | N/A                                                                         |
| `MAX_TRANS`                 | N/A                                                                         |
| `INITIAL_EXTENT`            | N/A                                                                         |
| `NEXT_EXTENT`               | N/A                                                                         |
| `MIN_EXTENTS`               | N/A                                                                         |
| `MAX_EXTENTS`               | N/A                                                                         |
| `PCT_INCREASE`              | N/A                                                                         |
| `FREELISTS`                 | Number of process freelists allocated to a segment                          |
| `FREELIST_GROUPS`           | Number of freelist groups allocated to a segment                            |
| `LOGGING`                   | Logging information                                                         |
| `BACKED_UP`                 | N/A                                                                         |
| `NUM_ROWS`                  | Number of rows in the table                                                 |
| `BLOCKS`                    | N/A                                                                         |
| `EMPTY_BLOCKS`              | N/A                                                                         |
| `AVG_SPACE`                 | N/A                                                                         |
| `CHAIN_CNT`                 | N/A                                                                         |
| `AVG_ROW_LEN`               | Average length of a row in the table in bytes                               |
| `AVG_SPACE_FREELIST_BLOCKS` | Average freespace of all blocks on a freelist                               |
| `NUM_FREELIST_BLOCKS`       | Number of blocks on the freelist                                            |
| `DEGREE`                    | Number of threads per instance for scanning the table                       |
| `INSTANCES`                 | Number of instances across which the table is to be scanned                 |
| `CACHE`                     | Whether the cluster is to be cached in the buffer cache                     |
| `TABLE_LOCK`                | Whether table locking is enabled or disabled                                |
| `SAMPLE_SIZE`               | Sample size used in analyzing this table                                    |
| `LAST_ANALYZED`             | Date on which this table was most recently analyzed                         |
| `PARTITIONED`               | Indicates whether this table is partitioned                                 |
| `IOT_TYPE`                  | If this is an index organized table                                         |
| `TEMPORARY`                 | Can the current session only see data that it placed in this object itself? |
| `SECONDARY`                 | N/A                                                                         |
| `NESTED`                    | If the table is a nested table                                              |
| `BUFFER_POOL`               | The default buffer pool for the object                                      |
| `ROW_MOVEMENT`              | N/A                                                                         |
| `GLOBAL_STATS`              | N/A                                                                         |
| `USER_STATS`                | N/A                                                                         |
| `DURATION`                  | N/A                                                                         |
| `SKIP_CORRUPT`              | N/A                                                                         |
| `MONITORING`                | N/A                                                                         |
| `CLUSTER_OWNER`             | N/A                                                                         |
| `DEPENDENCIES`              | N/A                                                                         |
| `COMPRESSION`               | N/A                                                                         |

### USER_TAB_COLUMNS

The `USER_TAB_COLUMNS` view contains columns of the tables, views, and clusters owned by the user.

| Column name            | Description                                                                                                                                                                                                    |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TABLE_NAME`           | Name of the table, view, or cluster                                                                                                                                                                            |
| `COLUMN_NAME`          | Name of the column                                                                                                                                                                                             |
| `DATA_TYPE`            | Data type of column                                                                                                                                                                                            |
| `DATA_TYPE_MOD`        | Data type modifier of the column                                                                                                                                                                               |
| `DATA_TYPE_OWNER`      | Owner of the data type of the column                                                                                                                                                                           |
| `DATA_LENGTH`          | Maximum length of the column in bytes                                                                                                                                                                          |
| `DATA_PRECISION`       | N/A                                                                                                                                                                                                            |
| `DATA_SCALE`           | Digits to the right of a decimal point in a number                                                                                                                                                             |
| `NULLABLE`             | Whether the column permits nulls. Value is n if there is a NOT NULL constraint on the column or if the column is part of a PRIMARY key.                                                                        |
| `COLUMN_ID`            | Sequence number of the column as created                                                                                                                                                                       |
| `DEFAULT_LENGTH`       | N/A                                                                                                                                                                                                            |
| `DATA_DEFAULT`         | N/A                                                                                                                                                                                                            |
| `NUM_DISTINCT`         | Number of distinct values in each column of the table                                                                                                                                                          |
| `LOW_VALUE`            | For tables with more than three rows, the second lowest and second highest values. These statistics are expressed in hexadecimal notation for the internal representation of the first 32 bytes of the values. |
| `HIGH_VALUE`           | N/A                                                                                                                                                                                                            |
| `DENSITY`              | N/A                                                                                                                                                                                                            |
| `NUM_NULLS`            | Number of nulls in the column                                                                                                                                                                                  |
| `NUM_BUCKETS`          | Number of buckets in histogram for the column                                                                                                                                                                  |
| `LAST_ANALYZED`        | Date on which this column was most recently analyzed                                                                                                                                                           |
| `SAMPLE_SIZE`          | Sample size used in analyzing this column                                                                                                                                                                      |
| `CHARACTER_SET_NAME`   | Name of the character set                                                                                                                                                                                      |
| `CHAR_COL_DECL_LENGTH` | Length of the character set                                                                                                                                                                                    |
| `GLOBAL_STATS`         | N/A                                                                                                                                                                                                            |
| `USER_STATS`           | N/A                                                                                                                                                                                                            |
| `AVG_COL_LEN`          | Average length of the column (in bytes)                                                                                                                                                                        |
| `CHAR_LENGTH`          | Length of the column in characters                                                                                                                                                                             |
| `CHAR_USED`            | N/A                                                                                                                                                                                                            |

### USER_TAB_COMMENTS

The `USER_TAB_COMMENTS` view contains comments on the tables and views owned by the user.

| Column name  | Description            |
|:-------------|:-----------------------|
| `TABLE_NAME` | Name of the object     |
| `TABLE_TYPE` | Type of the object     |
| `COMMENTS `  | Comments on the object |

### USER_VIEWS

The `USER_VIEWS` view contains text of views owned by the user.

| Column name        | Description                                                |
|:-------------------|:-----------------------------------------------------------|
| `VIEW_NAME`        | Name of the view                                           |
| `TEXT_LENGTH`      | Length of the view text                                    |
| `TEXT`             | First line of the view text                                |
| `TYPE_TEXT_LENGTH` | Length of the type clause of the typed view                |
| `TYPE_TEXT`        | Type clause of the typed view                              |
| `OID_TEXT_LENGTH`  | Length of the `WITH OID` clause of the typed view          |
| `OID_TEXT`         | `WITH OID` clause of the typed view                        |
| `VIEW_TYPE_OWNER`  | Owner of the type of the view, if the view is a typed view |
| `VIEW_TYPE`        | Type of the view, if the view is a typed view              |
| `SUPERVIEW_NAME`   | N/A                                                        |

### USER_USERS

The `USER_USERS` view contains information about the current user.

| Column name            | Description                                             |
|:-----------------------|:--------------------------------------------------------|
| `USERNAME`             | Name of the user                                        |
| `USER_ID`              | N/A                                                     |
| `ACCOUNT_STATUS`       | Indicates if the account is locked, expired or unlocked |
| `LOCK_DATE`            | Date on which the account was locked                    |
| `EXPIRE_DATE`          | Date of expiration of the account                       |
| `DEFAULT_TABLESPACE`   | N/A                                                     |
| `TEMPORARY_TABLESPACE` | N/A                                                     |
| `CREATED`              | N/A                                                     |
| `EXTERNAL_NAME`        | Name of the external user                               |
