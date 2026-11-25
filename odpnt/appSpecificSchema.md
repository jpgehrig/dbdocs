Oracle Data Provider for .NET supports both the common schema collections described previously and the following Oracle-specific schema collections:

- Tables

- Columns

- Views

- XMLSchema

- Users

- Synonyms

- Sequences

- Functions

- Procedures

- ProcedureParameters

- Arguments

- Packages

- PackageBodies

- JavaClasses

- Indexes

- IndexColumns

- PrimaryKeys

- ForeignKeys

- ForeignKeyColumns

- UniqueKeys

### Tables

Table A-6 lists the column name, data type, and description of the Tables Schema Schema Collection.

Table A-6 Tables

| Column Name  | Data Type | Description                                     |
|:-------------|:----------|:------------------------------------------------|
| `OWNER`      | `String`  | Owner of the Table.                             |
| `TABLE_NAME` | `String`  | Name of the Table.                              |
| `TYPE`       | `String`  | Type of Table, for example, `System` or `User`. |

### Columns

Table A-7 lists the column name, data type, and description of the Columns Schema Collection .

Table A-7 Columns

| ColumnName      | Data Type | Description                                                                                                      |
|:----------------|:----------|:-----------------------------------------------------------------------------------------------------------------|
| `OWNER`         | `String`  | Owner of the table or view.                                                                                      |
| `TABLE_NAME`    | `String`  | Name of the table or view.                                                                                       |
| `COLUMN_NAME`   | `String`  | Name of the column.                                                                                              |
| `ID`            | `Decimal` | Sequence number of the column as created.                                                                        |
| `DATATYPE`      | `String`  | Data type of the column.                                                                                         |
| `LENGTH`        | `Decimal` | Length of the column in bytes.                                                                                   |
| `PRECISION`     | `Decimal` | Decimal precision for `NUMBER` data type; binary precision for `FLOAT` data type, null for all other data types. |
| `Scale`         | `Decimal` | Digits to right of decimal point in a number.                                                                    |
| `NULLABLE`      | `String`  | Specifies whether or not a column allows `NULL`s.                                                                |
| `CHAR_USED`     | `String`  | Indicates whether the column uses `BYTE` length semantics (B) or `CHAR` length semantics (C).                    |
| `LengthInChars` | `Decimal` | Length of the column in characters.<br>This value only applies to `CHAR`, `VARCHAR2`, `NCHAR`, and `NVARCHAR2`.  |

### Views

Table A-8 lists the column name, data type, and description of the Views Schema Collection.

Table A-8 Views

| Column Name        | Data Type | Description                                          |
|:-------------------|:----------|:-----------------------------------------------------|
| `OWNER`            | `String`  | Owner of the view.                                   |
| `VIEW_NAME`        | `String`  | Name of the view.                                    |
| `TEXT_LENGTH`      | `Decimal` | Length of the view text.                             |
| `TEXT`             | `String`  | View text.                                           |
| `TYPE_TEXT_LENGTH` | `Decimal` | Length of the type clause of the typed view.         |
| `TYPE_TEXT`        | `String`  | Type clause of the typed view.                       |
| `OID_TEXT_LENGTH`  | `Decimal` | Length of the `WITH` `OID` clause of the typed view. |
| `OID_TEXT`         | `String`  | `WITH` `OID` clause of the typed view.               |
| `VIEW_TYPE_OWNER`  | `String`  | Owner of the view type if the view is a typed view.  |
| `VIEW_TYPE`        | `String`  | Type of the view if the view is a typed view.        |
| `SUPERVIEW_NAME`   | `String`  | Name of the superview.<br>(Oracle9i or later)        |

### XMLSchema

Table A-9 lists the column name, data type and description of the XMLSchema Schema Collection.

**Note:**

This collection is only available with Oracle Database 10g and later.

Table A-9 XMLSchema

| Column Name       | Data Type | Description                                                         |
|:------------------|:----------|:--------------------------------------------------------------------|
| `OWNER`           | `String`  | Owner of the XML schema.                                            |
| `SCHEMA_URL`      | `String`  | Schema URL of the XML schema.                                       |
| `LOCAL`           | `String`  | Indicates whether the XML schema is local (`YES`) or global (`NO`). |
| `SCHEMA`          | `String`  | XML schema document.                                                |
| `INT_OBJNAME`     | `String`  | Internal database object name for the schema.                       |
| `QUAL_SCHEMA_URL` | `String`  | Fully qualified schema URL.                                         |
| `HIER_TYPE`       | `String`  | Hierarchy type for the schema.                                      |

### Users

Table A-10 lists the column name, data type and description of the Users Schema Collection.

Table A-10 Users

| Column Name  | Data Type  | Description            |
|:-------------|:-----------|:-----------------------|
| `NAME`       | `String`   | Name of the user.      |
| `ID`         | `Decimal`  | ID number of the user. |
| `CREATEDATE` | `DateTime` | User creation date.    |

### Synonyms

Table A-11 lists the column name, data type and description of the Synonyms Schema Collection.

Table A-11 Synonyms

| Column Name    | Data Type | Description                                                                                                                                                                                                                                |
|:---------------|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`        | `String`  | Owner of the synonym.                                                                                                                                                                                                                      |
| `SYNONYM_NAME` | `String`  | Name of the synonym.                                                                                                                                                                                                                       |
| `TABLE_OWNER`  | `String`  | Owner of the object referenced by the synonym. Although the column is called `TABLE_OWNER`, the object owned is not necessarily a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on.      |
| `TABLE_NAME`   | `String`  | Name of the object referenced by the synonym. Although the column is called `TABLE_NAME`, the object does not necessarily have to be a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on. |
| `DB_LINK`      | `String`  | Name of the database link referenced, if any.                                                                                                                                                                                              |

### Sequences

Table A-12 lists the column name, data type, and description of the Sequences Schema Collection.

Table A-12 Sequences

| Column Name      | Data Type | Description                                                                                                                                                                                                                    |
|:-----------------|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SEQUENCE_OWNER` | `String`  | Name of the owner of the sequence.                                                                                                                                                                                             |
| `SEQUENCE_NAME`  | `String`  | Sequence name.                                                                                                                                                                                                                 |
| `MIN_VALUE`      | `Decimal` | Minimum value of the sequence.                                                                                                                                                                                                 |
| `MAX_VALUE`      | `Decimal` | Maximum value of the sequence.                                                                                                                                                                                                 |
| `INCREMENT_BY`   | `Decimal` | Value by which sequence is incremented.                                                                                                                                                                                        |
| `CYCLE_FLAG`     | `String`  | Indicates if sequence wraps around on reaching limit.                                                                                                                                                                          |
| `ORDER_FLAG`     | `String`  | Indicates if sequence numbers are generated in order.                                                                                                                                                                          |
| `CACHE_SIZE`     | `Decimal` | Number of sequence numbers to cache.                                                                                                                                                                                           |
| `LAST_NUMBER`    | `Decimal` | Last sequence number written to disk. If a sequence uses caching, the number written to disk is the last number placed in the sequence cache. This number is likely to be greater than the last sequence number that was used. |

### Functions

Table A-13 lists the column name, data type, and description of the Functions Schema Collection.

Table A-13 Functions

| Column Name      | Data Type  | Description                                                                                                                  |
|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `String`   | Owner of the function.                                                                                                       |
| `OBJECT_NAME`    | `String`   | Name of the function.                                                                                                        |
| `SUBOBJECT_NAME` | `String`   | Name of the subobject (for example, partition).                                                                              |
| `OBJECT_ID`      | `Decimal`  | Dictionary object number of the function.                                                                                    |
| `DATA_OBJECT_ID` | `Decimal`  | Dictionary object number of the segment that contains the function.                                                          |
| `CREATED`        | `DateTime` | Timestamp for the creation of the function.                                                                                  |
| `LAST_DDL_TIME`  | `DateTime` | Timestamp for the last modification of the function resulting from a DDL statement (including grants and revokes).           |
| `TIMESTAMP`      | `String`   | Timestamp for the specification of the function (character data).                                                            |
| `STATUS`         | `String`   | Status of the function (`VALID`, `INVALID`, or N/A).                                                                         |
| `TEMPORARY`      | `String`   | Whether or not the function is temporary (the current session can see only data that it placed in this object itself).       |
| `GENERATED`      | `String`   | Indicates whether the name of this function is system generated (`Y`) or not (`N`).                                          |
| `SECONDARY`      | `String`   | Whether or not this is a secondary object created by the `ODCIIndexCreate` method of the Oracle Data Cartridge (`Y` \| `N`). |

### Procedures

Table A-14 lists the column name, data type, and description of the Procedures Schema Collection.

Table A-14 Procedures

| Column Name      | Data Type  | Description                                                                                                                  |
|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `String`   | Owner of the procedure.                                                                                                      |
| `OBJECT_NAME`    | `String`   | Name of the procedure.                                                                                                       |
| `SUBOBJECT_NAME` | `String`   | Name of the subobject (for example, partition).                                                                              |
| `OBJECT_ID`      | `Decimal`  | Dictionary object number of the procedure.                                                                                   |
| `DATA_OBJECT_ID` | `Decimal`  | Dictionary object number of the segment that contains the procedure.                                                         |
| `CREATED`        | `DateTime` | Timestamp for the creation of the procedure.                                                                                 |
| `LAST_DDL_TIME`  | `Decimal`  | Timestamp for the last modification of the procedure resulting from a DDL statement (including grants and revokes).          |
| `TIMESTAMP`      | `String`   | Timestamp for the specification of the procedure (character data).                                                           |
| `STATUS`         | `String`   | Status of the procedure (`VALID`, `INVALID`, or N/A).                                                                        |
| `TEMPORARY`      | `String`   | Whether or not the procedure is temporary (the current session can see only data that it placed in this object itself).      |
| `GENERATED`      | `String`   | Indicates whether the name of this procedure is system generated (`Y`) or not (`N`).                                         |
| `SECONDARY`      | `String`   | Whether or not this is a secondary object created by the `ODCIIndexCreate` method of the Oracle Data Cartridge (`Y` \| `N`). |

### ProcedureParameters

Table A-15 lists the column name, data type and description of the ProcedureParameters Schema Collection.

Table A-15 ProcedureParameters

| Column Name          | Data Type | Description                                                                                                                                                                       |
|:---------------------|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`              | `String`  | Owner of the object.                                                                                                                                                              |
| `OBJECT_NAME`        | `String`  | Name of the procedure or function.                                                                                                                                                |
| `PACKAGE_NAME`       | `String`  | Name of the package.                                                                                                                                                              |
| `OBJECT_ID`          | `Decimal` | Object number of the object.                                                                                                                                                      |
| `OVERLOAD`           | `String`  | Indicates the nth overloading ordered by its appearance in the source; otherwise, it is `NULL`.                                                                                   |
| `SUBPROGRAM_ID`      | `Decimal` | Subprogram id for the procedure or function                                                                                                                                       |
| `ARGUMENT_NAME`      | `String`  | If the argument is a scalar type, then the argument name is the name of the argument. A null argument name is used to denote a function return value.                             |
| `POSITION`           | `Decimal` | If `DATA_LEVEL` is zero, then this column holds the position of this item in the argument list, or zero for a function return value.                                              |
| `SEQUENCE`           | `Decimal` | Defines the sequential order of the argument. Argument sequence starts from `1`.                                                                                                  |
| `DATA_LEVEL`         | `Decimal` | Nesting depth of the argument for composite types.                                                                                                                                |
| `DATA_TYPE`          | `String`  | Data type of the argument.                                                                                                                                                        |
| `DEFAULT_VALUE`      | `String`  | Default value for the argument.                                                                                                                                                   |
| `DEFAULT_LENGTH`     | `Decimal` | Length of the default value for the argument.                                                                                                                                     |
| `IN_OUT`             | `String`  | Direction of the argument: \[`IN`\] \[`OUT`\] \[`IN`/`OUT`\].                                                                                                                     |
| `DATA_LENGTH`        | `Decimal` | Length of the column (in bytes).                                                                                                                                                  |
| `DATA_PRECISION`     | `Decimal` | Length in decimal digits (`NUMBER`) or binary digits (`FLOAT`).                                                                                                                   |
| `DATA_SCALE`         | `Decimal` | Digits to the right of the decimal point in a number.                                                                                                                             |
| `RADIX`              | `Decimal` | Argument radix for a number.                                                                                                                                                      |
| `CHARACTER_SET_NAME` | `String`  | Character set name for the argument.                                                                                                                                              |
| `TYPE_OWNER`         | `String`  | Owner of the type of the argument.                                                                                                                                                |
| `TYPE_NAME`          | `String`  | Name of the type of the argument. If the type is a package local type (that is, it is declared in a package specification), then this column displays the name of the package.    |
| `TYPE_SUBNAME`       | `String`  | Displays the name of the type declared in the package identified in the `TYPE_NAME` column.<br>Relevant only for package local types.                                             |
| `TYPE_LINK`          | `String`  | Displays the database link that refers to the remote package.<br>Relevant only for package local types when the package identified in the `TYPE_NAME` column is a remote package. |
| `PLS_TYPE`           | `String`  | For numeric arguments, the name of the PL/SQL type of the argument. Otherwise, `Null`.                                                                                            |
| `CHAR_LENGTH`        | `Decimal` | Character limit for string data types.                                                                                                                                            |
| `CHAR_USED`          | `String`  | Indicates whether the byte limit (`B`) or character limit (`C`) is official for the string.                                                                                       |

### Arguments

Table A-16 lists the column name, data type, and description of the Arguments Schema Collection.

Table A-16 Arguments

| Column Name      | Data Type | Description                                                                                                                                           |
|:-----------------|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `String`  | Owner of the object.                                                                                                                                  |
| `PACKAGE_NAME`   | `String`  | Name of the package.                                                                                                                                  |
| `OBJECT_NAME`    | `String`  | Name of the procedure or function.                                                                                                                    |
| `ARGUMENT_NAME`  | `String`  | If the argument is a scalar type, then the argument name is the name of the argument. A null argument name is used to denote a function return value. |
| `POSITION`       | `Decimal` | If `DATA_LEVEL` is zero, then this column holds the position of this item in the argument list, or zero for a function return value.                  |
| `SEQUENCE`       | `Decimal` | Defines the sequential order of the argument. Argument sequence starts from `1`.                                                                      |
| `DEFAULT_VALUE`  | `String`  | Default value for the argument.                                                                                                                       |
| `DEFAULT_LENGTH` | `Decimal` | Length of the default value for the argument.                                                                                                         |
| `IN_OUT`         | `String`  | Direction of the argument: \[`IN`\] \[`OUT`\] \[`IN`/`OUT`\].                                                                                         |
| `DATA_LENGTH`    | `Decimal` | Length of the column (in bytes).                                                                                                                      |
| `DATA_PRECISION` | `Decimal` | Length in decimal digits (`NUMBER`) or binary digits (`FLOAT`).                                                                                       |
| `DATA_SCALE`     | `Decimal` | Digits to the right of the decimal point in a number.                                                                                                 |
| `DATA_TYPE`      | `String`  | Data type of the argument.                                                                                                                            |
| `CHAR_USED`      | `String`  | Indicates whether the column uses `BYTE` length semantics (B) or `CHAR` length semantics (C).                                                         |

### Packages

Table A-17 lists the column name, data type, and description of the Packages Schema Collection.

Table A-17 Packages

| Column Name      | Data Type  | Description                                                                                                                  |
|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `String`   | Owner of the package.                                                                                                        |
| `OBJECT_NAME`    | `String`   | Name of the package.                                                                                                         |
| `SUBOBJECT_NAME` | `String`   | Name of the subobject (for example, partition).                                                                              |
| `OBJECT_ID`      | `Decimal`  | Dictionary object number of the package.                                                                                     |
| `DATA_OBJECT_ID` | `Decimal`  | Dictionary object number of the segment that contains the package.                                                           |
| `CREATED`        | `DateTime` | Timestamp for the creation of the package.                                                                                   |
| `LAST_DDL_TIME`  | `DateTime` | Timestamp for the last modification of the package resulting from a DDL statement (including grants and revokes).            |
| `TIMESTAMP`      | `String`   | Timestamp for the specification of the package (character data).                                                             |
| `STATUS`         | `String`   | Status of the package (`VALID`, `INVALID`, or N/A).                                                                          |
| `TEMPORARY`      | `String`   | Whether or not the package is temporary (the current session can see only data that it placed in this object itself).        |
| `GENERATED`      | `String`   | Indicates whether the name of this package was system generated (`Y`) or not (`N`).                                          |
| `SECONDARY`      | `String`   | Whether or not this is a secondary object created by the `ODCIIndexCreate` method of the Oracle Data Cartridge (`Y` \| `N`). |

### PackageBodies

Table A-18 lists the column name, data type, and description of the PackageBodies Schema Collection.

Table A-18 PackageBodies

| Column Name      | Data Type  | Description                                                                                                                  |
|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `String`   | Owner of the package body.                                                                                                   |
| `OBJECT_NAME`    | `String`   | Name of the package body.                                                                                                    |
| `SUBOBJECT_NAME` | `String`   | Name of the subobject (for example, partition).                                                                              |
| `OBJECT_ID`      | `Decimal`  | Dictionary object number of the package body.                                                                                |
| `DATA_OBJECT_ID` | `Decimal`  | Dictionary object number of the segment that contains the package body.                                                      |
| `CREATED`        | `DateTime` | Timestamp for the creation of the package body.                                                                              |
| `LAST_DDL_TIME`  | `DateTime` | Timestamp for the last modification of the package body resulting from a DDL statement (including grants and revokes).       |
| `TIMESTAMP`      | `String`   | Timestamp for the specification of the package body (character data).                                                        |
| `STATUS`         | `String`   | Status of the package body (`VALID`, `INVALID`, or N/A).                                                                     |
| `TEMPORARY`      | `String`   | Whether the package body is temporary (the current session can see only data that it placed in this object itself).          |
| `GENERATED`      | `String`   | Indicates whether the name of this package body is system generated (`Y`) or not (`N`).                                      |
| `SECONDARY`      | `String`   | Whether or not this is a secondary object created by the `ODCIIndexCreate` method of the Oracle Data Cartridge (`Y` \| `N`). |

### JavaClasses

Table A-19 lists the column name, data type, and description of the JavaClasses Schema Collection.

Table A-19 JavaClasses

| Column Name     | Data Type | Description                                                                                      |
|:----------------|:----------|:-------------------------------------------------------------------------------------------------|
| `OWNER`         | `String`  | Owner of the Java class.                                                                         |
| `NAME`          | `String`  | Name of the Java class.                                                                          |
| `MAJOR`         | `Decimal` | Major version number of the Java class, as defined in the JVM specification.                     |
| `MINOR`         | `Decimal` | Minor version number of the Java class, as defined in the JVM specification.                     |
| `KIND`          | `String`  | Indicates whether the stored object is a Java class (`CLASS`) or a Java interface (`INTERFACE`). |
| `ACCESSIBILITY` | `String`  | Accessibility of the Java class.                                                                 |
| `IS_INNER`      | `String`  | Indicates whether this Java class is an inner class (`YES`) or not (`NO`).                       |
| `IS_ABSTRACT`   | `String`  | Indicates whether this Java class is an abstract class (`YES`) or not (`NO`).                    |
| `IS_FINAL`      | `String`  | Indicates whether this Java class is a final class (`YES`) or not (`NO`).                        |
| `IS_DEBUG`      | `String`  | Indicates whether this Java class contains debug information (`YES`) or not (`NO`).              |
| `SOURCE`        | `String`  | Source designation of the Java class.                                                            |
| `SUPER`         | `String`  | Super class of this Java class.                                                                  |
| `OUTER`         | `String`  | Outer class of this Java class if this Java class is an inner class.                             |

### Indexes

Table A-20 lists the column name, data type, and description of the Indexes Schema Collection.

Table A-20 Indexes

| Column Name               | Data Type | Description                                                                                                                                                                                                                                                |
|:--------------------------|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                   | `String`  | Owner of the index.                                                                                                                                                                                                                                        |
| `INDEX_NAME`              | `String`  | Name of the index.                                                                                                                                                                                                                                         |
| `INDEX_TYPE`              | `String`  | Type of the index:<br>• `NORMAL`<br>• `BITMAP`<br>• `FUNCTION-BASED NORMAL`<br>• `FUNCTION-BASED BITMAP`<br>• `DOMAIN`                                                                                                                                     |
| `TABLE_OWNER`             | `String`  | Owner of the indexed object.                                                                                                                                                                                                                               |
| `TABLE_NAME`              | `String`  | Name of the indexed object.                                                                                                                                                                                                                                |
| `TABLE_TYPE`              | `String`  | Type of the indexed object (for example, `TABLE` or `CLUSTER`).                                                                                                                                                                                            |
| `UNIQUENESS`              | `String`  | Indicates whether the index is `UNIQUE` or `NONUNIQUE`.                                                                                                                                                                                                    |
| `COMPRESSION`             | `String`  | Indicates whether index compression is enabled (`ENABLED`) or not (`DISABLED`).                                                                                                                                                                            |
| `PREFIX_LENGTH`           | `Decimal` | Number of columns in the prefix of the compression key.                                                                                                                                                                                                    |
| `TABLESPACE_NAME`         | `String`  | Name of the tablespace containing the index.                                                                                                                                                                                                               |
| `INI_TRANS`               | `Decimal` | Initial number of transactions.                                                                                                                                                                                                                            |
| `MAX_TRANS`               | `Decimal` | Maximum number of transactions.                                                                                                                                                                                                                            |
| `INITIAL_EXTENT`          | `Decimal` | Size of the initial extent.                                                                                                                                                                                                                                |
| `NEXT_EXTENT`             | `Decimal` | Size of secondary extents.                                                                                                                                                                                                                                 |
| `MIN_EXTENTS`             | `Decimal` | Minimum number of extents allowed in the segment.                                                                                                                                                                                                          |
| `MAX_EXTENTS`             | `Decimal` | Maximum number of extents allowed in the segment.                                                                                                                                                                                                          |
| `PCT_INCREASE`            | `Decimal` | Percentage increase in extent size.                                                                                                                                                                                                                        |
| `PCT_THRESHOLD`           | `Decimal` | Threshold percentage of block space allowed per index entry.                                                                                                                                                                                               |
| `INCLUDE_COLUMN`          | `Decimal` | Column ID of the last column to be included in index-organized table primary key (non-overflow) index. This column maps to the `COLUMN_ID` column of the `*_TAB_COLUMNS` data dictionary views.                                                            |
| `FREELISTS`               | `Decimal` | Number of process freelists allocated to this segment.                                                                                                                                                                                                     |
| `FREELIST_GROUPS`         | `Decimal` | Number of freelist groups allocated to this segment.                                                                                                                                                                                                       |
| `PCT_FREE`                | `Decimal` | Minimum percentage of free space in a block.                                                                                                                                                                                                               |
| `LOGGING`                 | `String`  | Logging information.                                                                                                                                                                                                                                       |
| `BLEVEL`                  | `Decimal` | B\*-Tree level: depth of the index from its root block to its leaf blocks. A depth of `0` indicates that the root block and leaf block are the same.                                                                                                       |
| `LEAF_BLOCKS`             | `Decimal` | Number of leaf blocks in the index.                                                                                                                                                                                                                        |
| `DISTINCT_KEYS`           | `Decimal` | Number of distinct indexed values. For indexes that enforce `UNIQUE` and `PRIMARY` `KEY` constraints, this value is the same as the number of rows in the table (`USER_TABLES`.`NUM_ROWS`).                                                                |
| `AVG_LEAF_BLOCKS_PER_KEY` | `Decimal` | Average number of leaf blocks in which each distinct value in the index appears, rounded to the nearest integer. For indexes that enforce `UNIQUE` and `PRIMARY` `KEY` constraints, this value is always `1`.                                              |
| `AVG_DATA_BLOCKS_PER_KEY` | `Decimal` | Average number of data blocks in the table that are pointed to by a distinct value in the index, rounded to the nearest integer. This statistic is the average number of data blocks that contain rows that contain a given value for the indexed columns. |
| `CLUSTERING_FACTOR`       | `Decimal` | Indicates the amount of order of the rows in the table based on the values of the index.                                                                                                                                                                   |
| `STATUS`                  | `String`  | Indicates whether a nonpartitioned index is `VALID` or `UNUSABLE`.                                                                                                                                                                                         |
| `NUM_ROWS`                | `Decimal` | Number of rows in the index.                                                                                                                                                                                                                               |
| `SAMPLE_SIZE`             | `Decimal` | Size of the sample used to analyze the index.                                                                                                                                                                                                              |
| `LAST_ANALYZED`           | `Date`    | Date on which this index was most recently analyzed.                                                                                                                                                                                                       |
| `DEGREE`                  | `String`  | Number of threads per instance for scanning the index.                                                                                                                                                                                                     |
| `INSTANCES`               | `String`  | Number of instances across which the indexes to be scanned.                                                                                                                                                                                                |
| `PARTITIONED`             | `String`  | Indicates whether the index is partitioned (`YES`) or not (`NO`).                                                                                                                                                                                          |
| `TEMPORARY`               | `String`  | Indicates whether or not the index is on a temporary table.                                                                                                                                                                                                |
| `GENERATED`               | `String`  | Indicates whether the name of the index is system generated (`Y`) or not (`N`).                                                                                                                                                                            |
| `SECONDARY`               | `String`  | Indicates whether the index is a secondary object created by the `ODCIIndexCreate` method of the Oracle Data Cartridge (`Y`) or not (`N`).                                                                                                                 |
| `BUFFER_POOL`             | `String`  | Name of the default buffer pool to be used for the index blocks.                                                                                                                                                                                           |
| `USER_STATS`              | `String`  | Indicates whether statistics were entered directly by the user (`YES`) or not (`NO`).                                                                                                                                                                      |
| `DURATION`                | `String`  | Indicates the duration of a temporary table.                                                                                                                                                                                                               |
| `PCT_DIRECT_ACCESS`       | `Decimal` | For a secondary index on an index-organized table, the percentage of rows with `VALID` guess.                                                                                                                                                              |
| `ITYP_OWNER`              | `String`  | For a domain index, the owner of the index type.                                                                                                                                                                                                           |
| `ITYP_NAME`               | `String`  | For a domain index, the name of the index type.                                                                                                                                                                                                            |
| `PARAMETERS`              | `String`  | For a domain index, the parameter string.                                                                                                                                                                                                                  |
| `GLOBAL_STATS`            | `String`  | For partitioned indexes, indicates whether statistics are collected by analyzing the index as a whole (`YES`) or estimated from statistics on underlying index partitions and subpartitions (`NO`).                                                        |
| `DOMIDX_STATUS`           | `String`  | Status of the domain index:<br>• `NULL` - Index is not a domain index.<br>• `VALID` - Index is a valid domain index.<br>• `IDXTYP_INVLD` - Indextype of the domain index is invalid.                                                                       |
| `DOMIDX_OPSTATUS`         | `String`  | Status of the operation on the domain index:<br>• `NULL` - Index is not a domain index.<br>• `VALID` - Operation performed without errors.<br>• `FAILED` - Operation failed with an error.                                                                 |
| `FUNCIDX_STATUS`          | `String`  | Status of a function-based index:<br>• `NULL` - Index is not a function-based index.<br>• `ENABLED` - Function-based index is enabled.<br>• `DISABLED` - Function-based index is disabled.                                                                 |
| `JOIN_INDEX`              | `String`  | Indicates whether the index is a join index (`YES`) or not (`NO`).                                                                                                                                                                                         |
| `IOT_REDUNDANT_PKEY_ELIM` | `String`  | Indicates whether redundant primary key columns are eliminated from secondary indexes on index-organized tables (`YES`) or not (`NO`).                                                                                                                     |
| `DROPPED`                 | `String`  | Indicates whether the index has been dropped and is in the recycle bin (`YES`) or not (`NO`); null for partitioned tables.                                                                                                                                 |

### IndexColumns

Table A-21 lists the column name, data type, and description of the IndexColumns Schema Collection.

Table A-21 IndexColumns

| Column Name       | Data Type | Description                                                    |
|:------------------|:----------|:---------------------------------------------------------------|
| `INDEX_OWNER`     | `String`  | Owner of the index.                                            |
| `INDEX_NAME`      | String    | Name of the index.                                             |
| `TABLE_OWNER`     | String    | Owner of the table or cluster.                                 |
| `TABLE_NAME`      | String    | Name of the table or cluster.                                  |
| `COLUMN_NAME`     | String    | Column name or attribute of object type column.                |
| `COLUMN_POSITION` | `Decimal` | Position of column or attribute within the index.              |
| `COLUMN_LENGTH`   | `Decimal` | Indexed length of the column.                                  |
| `DESCEND`         | String    | Whether the column is sorted in descending order (`Y`/`N`).    |
| `CHAR_LENGTH`     | `Decimal` | Maximum codepoint length of the column.<br>(Oracle9i or later) |

### PrimaryKeys

Table A-22 lists the column name, data type, and description of the PrimaryKeys Schema Collection.

Table A-22 PrimaryKeys

| Column Name         | Data Type  | Description                                                                                                                                                                                                             |
|:--------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`             | `String`   | Owner of the constraint definition.                                                                                                                                                                                     |
| `CONSTRAINT_NAME`   | `String`   | Name of the constraint definition.                                                                                                                                                                                      |
| `TABLE_NAME`        | `String`   | Name associated with the table (or view) with constraint definition.                                                                                                                                                    |
| `SEARCH_CONDITION`  | `String`   | Text of search condition for a check constraint.                                                                                                                                                                        |
| `R_OWNER`           | `String`   | Owner of table referred to in a referential constraint.                                                                                                                                                                 |
| `R_CONSTRAINT_NAME` | `String`   | Name of the unique constraint definition for referenced table.                                                                                                                                                          |
| `DELETE_RULE`       | `String`   | Delete rule for a referential constraint (`CASCADE` or `NO` `ACTION`).                                                                                                                                                  |
| `STATUS`            | `String`   | Enforcement status of constraint (`ENABLED` or `DISABLED`).                                                                                                                                                             |
| `DEFERRABLE`        | `String`   | Whether or not the constraint is deferrable.                                                                                                                                                                            |
| `VALIDATED`         | `String`   | Whether all data obeys the constraint (`VALIDATED` or `NOT` `VALIDATED`).                                                                                                                                               |
| `GENERATED`         | `String`   | Whether the name of the constraint is user or system generated.                                                                                                                                                         |
| `BAD`               | `String`   | Indicates that this constraint specifies a century in an ambiguous manner. (`Yes`\| `No`)<br>To avoid errors resulting from this ambiguity, rewrite the constraint using the `TO_DATE` function with a four-digit year. |
| `RELY`              | `String`   | Whether an enabled constraint is enforced or unenforced.                                                                                                                                                                |
| `LAST_CHANGE`       | `DateTime` | When the constraint was last enabled or disabled.                                                                                                                                                                       |
| `INDEX_OWNER`       | `String`   | Name of the user owning the index.<br>(Oracle9i or later)                                                                                                                                                               |
| `INDEX_NAME`        | `String`   | Name of the index (only shown for unique and primary-key constraints).<br>(Oracle9i or later)                                                                                                                           |

### ForeignKeys

Table A-23 lists the column name, data type, and description of the ForeignKeys Schema Collection.

Table A-23 ForeignKeys

| Column Name                   | Data Type  | Description                                                                      |
|:------------------------------|:-----------|:---------------------------------------------------------------------------------|
| `PRIMARY_KEY_CONSTRAINT_NAME` | `String`   | Name of the constraint definition.                                               |
| `PRIMARY_KEY_OWNER`           | `String`   | Owner of the constraint definition.                                              |
| `PRIMARY_KEY_TABLE_NAME`      | `String`   | Name associated with the table (or view) with constraint definition.             |
| `FOREIGN_KEY_OWNER`           | `String`   | Owner of the constraint definition.                                              |
| `FOREIGN_KEY_CONSTRAINT_NAME` | `String`   | Name of the constraint definition.                                               |
| `FOREIGN_KEY_TABLE_NAME`      | `String`   | Name associated with the table (or view) with constraint definition.             |
| `SEARCH_CONDITION`            | `String`   | Text of search condition for a check constraint                                  |
| `R_OWNER`                     | `String`   | Owner of table referred to, in a referential constraint.                         |
| `R_CONSTRAINT_NAME`           | `String`   | Name of the unique constraint definition for referenced table.                   |
| `DELETE_RULE`                 | `String`   | Delete rule for a referential constraint (`CASCADE` or `NO` `ACTION`).           |
| `STATUS`                      | `String`   | Enforcement status of constraint (`ENABLED` or `DISABLED`).                      |
| `VALIDATED`                   | `String`   | Whether or not all data obeys the constraint (`VALIDATED` or `NOT` `VALIDATED`). |
| `GENERATED`                   | `String`   | Whether the name of the constraint is user or system generated.                  |
| `RELY`                        | `String`   | Whether an enabled constraint is enforced or unenforced.                         |
| `LAST_CHANGE`                 | `DateTime` | When the constraint was last enabled or disabled.                                |
| `INDEX_OWNER`                 | `String`   | Name of the user owning the index.<br>(Oracle9i or later)                        |
| `INDEX_NAME`                  | `String`   | Name of the index.<br>(Oracle9i or later)                                        |

### ForeignKeyColumns

Table A-24 lists the column name, data type, and description of the ForeignKeyColumns Schema Collection.

Table A-24 ForeignKeyColumns

| Column Name       | Data Type | Description                                                                                       |
|:------------------|:----------|:--------------------------------------------------------------------------------------------------|
| `OWNER`           | `String`  | Owner of the constraint definition.                                                               |
| `CONSTRAINT_NAME` | `String`  | Name of the constraint definition.                                                                |
| `TABLE_NAME`      | `String`  | Name of the table with constraint definition.                                                     |
| `COLUMN_NAME`     | `String`  | Name of the column or attribute of the object type column specified in the constraint definition. |
| `POSITION`        | `String`  | Original position of column or attribute in the definition of the object.                         |

### UniqueKeys

Table A-25 lists the column name, data type, and description of the UniqueKeys Schema Collection.

Table A-25 UniqueKeys

| Column Name         | Data Type | Description                                                                                                                                                                                                             |
|:--------------------|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`             | `String`  | Owner of the constraint definition.                                                                                                                                                                                     |
| `CONSTRAINT_NAME`   | `String`  | Name of the constraint definition.                                                                                                                                                                                      |
| `TABLE_NAME`        | `String`  | Name associated with the table (or view) with constraint definition.                                                                                                                                                    |
| `SEARCH_CONDITION`  | `String`  | Text of search condition for a check constraint.                                                                                                                                                                        |
| `R_OWNER`           | `String`  | Owner of table referred to in a referential constraint.                                                                                                                                                                 |
| `R_CONSTRAINT_NAME` | `String`  | Name of the unique constraint definition for referenced table.                                                                                                                                                          |
| `DELETE_RULE`       | `String`  | Delete rule for a referential constraint (`CASCADE` or `NO` `ACTION`).                                                                                                                                                  |
| `STATUS`            | `String`  | Enforcement status of constraint (`ENABLED` or `DISABLED`).                                                                                                                                                             |
| `DEFERRABLE`        | `String`  | Whether or not the constraint is deferrable.                                                                                                                                                                            |
| `VALIDATED`         | `String`  | Whether all data obeys the constraint (`VALIDATED` or `NOT` `VALIDATED`).                                                                                                                                               |
| `GENERATED`         | `String`  | Whether the name of the constraint is user or system generated.                                                                                                                                                         |
| `BAD`               | `String`  | Indicates that this constraint specifies a century in an ambiguous manner. (`Yes`\| `No`)<br>To avoid errors resulting from this ambiguity, rewrite the constraint using the `TO_DATE` function with a four-digit year. |
| `RELY`              | `String`  | Whether an enabled constraint is enforced or not.                                                                                                                                                                       |
| `LAST_CHANGE`       | `String`  | When the constraint was last enabled or disabled.                                                                                                                                                                       |
| `INDEX_OWNER`       | `String`  | Name of the user owning the index.<br>(Oracle9i or later)                                                                                                                                                               |
| `INDEX_NAME`        | `String`  | Name of the index (only shown for unique and primary-key constraints).<br>(Oracle9i or later)                                                                                                                           |
