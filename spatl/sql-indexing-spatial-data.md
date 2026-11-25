## 19  SQL Statements for Indexing Spatial Data

This chapter describes the SQL statements used when working with the spatial object data type.

For complete reference information about any statement, see [Oracle Database SQL Language Reference](../sqlrf/index.md).

Bold italic text is often used in the Keywords and Parameters sections in this chapter to identify a grouping of keywords, followed by specific keywords in the group. For example, INDEX_PARAMS identifies the start of a group of index-related keywords.

- ALTER INDEX
- ALTER INDEX REBUILD
- ALTER INDEX RENAME TO
- CREATE INDEX
- DROP INDEX

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 19.1 ALTER INDEX

#### Purpose

Alters specific parameters for a spatial index.

#### Syntax

    ALTER INDEX [schema.]index PARAMETERS ('index_params  [physical_storage_params]' )
        [{ NOPARALLEL | PARALLEL [ integer ] }] ;

#### Keywords and Parameters

| Value                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| INDEX_PARAMS                             | Changes the characteristics of the spatial index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| sdo_indx_dims                            | Specifies the number of dimensions to be indexed. For example, a value of 2 causes only the first two dimensions to be indexed. Must be less than or equal to the number of actual dimensions. For usage information related to three-dimensional geometries, see [Three-Dimensional Spatial Objects](spatial-concepts.md). Data type is NUMBER. Default = 2.                                                                                                                                                          |
| sdo_rtr_pctfree                          | Specifies the minimum percentage of slots in each index tree node to be left empty when the index is created. Slots that are left empty can be filled later when new data is inserted into the table. The value can range from 0 to 50. The default value is best for most applications; however, a value of 0 is recommended if no updates will be performed to the geometry column. Data type is NUMBER. Default = 10.                                                                                               |
| PHYSICAL_STORAGE_PARAMS                  | Determines the storage parameters used for altering the spatial index data table. A spatial index data table is a standard Oracle table with a prescribed format. Not all physical storage parameters that are allowed in the STORAGE clause of a CREATE TABLE statement are supported. The following is a list of the supported subset.                                                                                                                                                                               |
| tablespace                               | Specifies the tablespace in which the index data table is created. This parameter is the same as TABLESPACE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                         |
| initial                                  | Is the same as INITIAL in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| next                                     | Is the same as NEXT in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| minextents                               | Is the same as MINEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| maxextents                               | Is the same as MAXEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| pctincrease                              | Is the same as PCTINCREASE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| { NOPARALLEL \| PARALLEL \[ integer \] } | Controls whether serial (NOPARALLEL) execution or parallel (PARALLEL) execution is used for subsequent queries and DML operations that use the index. For parallel execution you can specify an integer value of degree of parallelism. See the Usage Notes for the CREATE INDEX statement for guidelines and restrictions that apply to the use of the PARALLEL keyword. Default = NOPARALLEL. (If PARALLEL is specified without an integer value, the Oracle database calculates the optimum degree of parallelism.) |

#### Prerequisites

- You must have EXECUTE privileges on the index type and its implementation type.

- The spatial index to be altered is not marked in-progress.

#### Usage Notes

Use this statement to change the parameters of an existing index.

See the Usage Notes for the CREATE INDEX statement for usage information about many of the other available parameters.

#### Examples

The following example modifies the tablespace for partition IP2 of the spatial index named BGI.

    ALTER INDEX bgi MODIFY PARTITION ip2
       PARAMETERS ('tablespace=TBS_3');

#### Related Topics

- ALTER INDEX REBUILD

- ALTER INDEX RENAME TO

- CREATE INDEX

- ALTER TABLE (clauses for partition maintenance) in [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md)

**Parent topic:** SQL Statements for Indexing Spatial Data

### 19.2 ALTER INDEX REBUILD

#### Syntax

    ALTER INDEX [schema.]index REBUILD
         [PARAMETERS ('rebuild_params [physical_storage_params]' ) ]
         [{ NOPARALLEL | PARALLEL [ integer ] }] ;

or

    ALTER INDEX [schema.]index REBUILD ONLINE
         [PARAMETERS ('rebuild_params [physical_storage_params]' ) ]
         [{ NOPARALLEL | PARALLEL [ integer ] }] ;

or

    ALTER INDEX [schema.]index REBUILD PARTITION partition
         [PARAMETERS ('rebuild_params [physical_storage_params]' ) ];

#### Purpose

Rebuilds a spatial index or a specified partition of a partitioned index.

#### Keywords and Parameters

| Value                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| REBUILD_PARAMS                           | Specifies in a command string the index parameters to use in rebuilding the spatial index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| index_status=cleanup                     | For an online rebuild operation (ALTER INDEX REBUILD ONLINE), performs cleanup operations on tables associated with the older version of the index.                                                                                                                                                                                                                                                                                                                                                                                                        |
| layer_gtype                              | Checks to ensure that all geometries are of a specified geometry type. The value must be from the Geometry Type column in [SDO_GTYPE](spatial-datatypes-metadata.md) (except that UNKNOWN_GEOMETRY is not allowed). In addition, specifying POINT allows for optimized processing of point data. Data type is VARCHAR2.                                                                                                                                                                                                                                    |
| sdo_dml_batch_size                       | Specifies the number of index updates to be processed in each batch of updates after a commit operation. The default value is 4000; for example, if you insert 5000 rows into the spatial table and then perform a commit operation, the updates to the spatial index table are performed in two batches of insert operations (4000 and 1000). See the Usage Notes for the CREATE INDEX statement for more information. Data type is NUMBER.                                                                                                               |
| sdo_indx_dims                            | Specifies the number of dimensions to be indexed. For example, a value of 2 causes only the first two dimensions to be indexed. Must be less than or equal to the number of actual dimensions. For usage information related to three-dimensional geometries, see [Three-Dimensional Spatial Objects](spatial-concepts.md). Data type is NUMBER. Default = 2.                                                                                                                                                                                              |
| sdo_max_memory                           | Specifies the amount of maximum memory that can be allocated to perform a spatial index build or rebuild operation. Can be from 64000 (about 64 KB) to 200000000 (about 200 MB). If the specified number of bytes cannot be allocated, 64000 (about 64 KB) is allocated. Specifying a value greater than the default can significantly improve index creation performance; however, do not specify more than 20 percent of available memory. Data type is NUMBER. Default = 10000000 (about 10 MB).                                                        |
| sdo_rtr_pctfree                          | Specifies the minimum percentage of slots in each index tree node to be left empty when the index is created. Slots that are left empty can be filled later when new data is inserted into the table. The value can range from 0 to 50. Data type is NUMBER. Default = 10.                                                                                                                                                                                                                                                                                 |
| PHYSICAL_STORAGE_PARAMS                  | Determines the storage parameters used for rebuilding the spatial index data table. A spatial index data table is a regular Oracle table with a prescribed format. Not all physical storage parameters that are allowed in the STORAGE clause of a CREATE TABLE statement are supported. The following is a list of the supported subset.                                                                                                                                                                                                                  |
| tablespace                               | Specifies the tablespace in which the index data table is created. Same as TABLESPACE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| initial                                  | Is the same as INITIAL in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| next                                     | Is the same as NEXT in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| minextents                               | Is the same as MINEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| maxextents                               | Is the same as MAXEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| pctincrease                              | Is the same as PCTINCREASE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| { NOPARALLEL \| PARALLEL \[ integer \] } | Controls whether serial (NOPARALLEL) execution or parallel (PARALLEL) execution is used for the rebuilding of the index and for subsequent queries and DML operations that use the index. For parallel execution you can specify an integer value of degree of parallelism. See the Usage Notes for the CREATE INDEX statement for guidelines and restrictions that apply to the use of the PARALLEL keyword. Default = NOPARALLEL. (If PARALLEL is specified without an integer value, the Oracle database calculates the optimum degree of parallelism.) |

#### Prerequisites

- You must have EXECUTE privileges on the index type and its implementation type.

- The spatial index to be altered is not marked in-progress.

#### Usage Notes

An ALTER INDEX REBUILD 'rebuild_params' statement rebuilds the index using supplied parameters. Spatial index creation involves creating and inserting index data, for each row in the underlying table column being spatially indexed, into a table with a prescribed format. All rows in the underlying table are processed before the insertion of index data is committed, and this requires adequate rollback segment space.

The ONLINE keyword rebuilds the index without blocking the index; that is, queries can use the spatial index while it is being rebuilt. However, after all queries issued during the rebuild operation have completed, you must clean up the old index information (in the MDRT tables) by entering a SQL statement in the following form:

    ALTER INDEX [schema.]index REBUILD ONLINE PARAMETERS ('index_status=cleanup');

The following limitations apply to the use of the ONLINE keyword:

- Only query operations are permitted while the index is being rebuilt. Insert, update, and delete operations that would affect the index are blocked while the index is being rebuilt; and an online rebuild is blocked while any insert, update, or delete operations that would affect the index are being performed.

- You cannot use the ONLINE keyword for a rebuild operation if the index was created using the `'sdo_non_leaf_tbl=TRUE'` parameter.

- You cannot use the ONLINE keyword for a partitioned spatial index.

Effective with Release 12.1, the ALTER INDEX REBUILD statement reuses any previous parameters from the index creation. If new or changed parameters are passed, new parameters are merged with the previous ones, and changed parameters override the previous ones.

For more information about using the `layer_gtype` keyword to constrain data in a layer to a geometry type, see [Constraining Data to a Geometry Type](indexing-querying-spatial-data.md).

With a partitioned spatial index, you must use a separate ALTER INDEX REBUILD statement for each partition to be rebuilt.

If you want to use a local partitioned spatial index, follow the procedure in [Creating a Local Partitioned Spatial Index](indexing-querying-spatial-data.md).

See also the Usage Notes for the CREATE INDEX statement for usage information about many of the available parameters and about the use of the PARALLEL keyword.

#### Examples

The following example rebuilds OLDINDEX and specifies the tablespace in which to create the index data table.

    ALTER INDEX oldindex REBUILD PARAMETERS('tablespace=TBS_3');

#### Related Topics

- CREATE INDEX

- DROP INDEX

- [ALTER TABLE](../sqlrf/ALTER-TABLE.md) and [ALTER INDEX](../sqlrf/ALTER-INDEX.md) (clauses for partition maintenance) in Oracle Database SQL Language Reference

**Parent topic:** SQL Statements for Indexing Spatial Data

### 19.3 ALTER INDEX RENAME TO

#### Syntax

    ALTER INDEX [schema.]index RENAME TO <new_index_name>;

    ALTER INDEX [schema.]index PARTITION partition RENAME TO <new_partition_name>;

#### Purpose

Changes the name of a spatial index or a partition of a spatial index.

#### Keywords and Parameters

| Value              | Description                              |
|:-------------------|:-----------------------------------------|
| new_index_name     | Specifies the new name of the index.     |
| new_partition_name | Specifies the new name of the partition. |

#### Prerequisites

- You must have EXECUTE privileges on the index type and its implementation type.

- The spatial index to be altered is not marked in-progress.

#### Usage Notes

None.

#### Examples

The following example renames OLDINDEX to NEWINDEX.

    ALTER INDEX oldindex RENAME TO newindex;

#### Related Topics

- CREATE INDEX

- DROP INDEX

**Parent topic:** SQL Statements for Indexing Spatial Data

### 19.4 CREATE INDEX

#### Syntax

    CREATE INDEX [schema.]index ON [schema.]table (column)
         INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2
         [PARAMETERS ('index_params  [physical_storage_params]' )]
         [{ NOPARALLEL | PARALLEL [ integer ] }];

#### Purpose

Creates a spatial index on a column of type SDO_GEOMETRY.

#### Keywords and Parameters

| Value                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-----------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| INDEX_PARAMS                             | Determines the characteristics of the spatial index.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| layer_gtype                              | Checks to ensure that all geometries are of a specified geometry type. The value must be from the Geometry Type column in [SDO_GTYPE](spatial-datatypes-metadata.md) (except that UNKNOWN_GEOMETRY is not allowed). In addition, specifying POINT allows for optimized processing of point data. Data type is VARCHAR2.                                                                                                                                                                             |
| sdo_dml_batch_size                       | Specifies the number of index updates to be processed in each batch of updates after a commit operation. The default value is 4000; for example, if you insert 5000 rows into the spatial table and then perform a commit operation, the updates to the spatial index table are performed in two batches of insert operations (4000 and 1000). See the Usage Notes for more information. Data type is NUMBER.                                                                                       |
| sdo_indx_dims                            | Specifies the number of dimensions to be indexed. For example, a value of 2 causes only the first two dimensions to be indexed. Must be less than or equal to the number of actual dimensions. For usage information related to three-dimensional geometries, see [Three-Dimensional Spatial Objects](spatial-concepts.md). Data type is NUMBER. Default = 2.                                                                                                                                       |
| sdo_max_memory                           | Specifies the amount of maximum memory that can be allocated to perform a spatial index build or rebuild operation. Can be from 64000 (about 64 KB) to 200000000 (about 200 MB). If the specified number of bytes cannot be allocated, 64000 (about 64 KB) is allocated. Specifying a value greater than the default can significantly improve index creation performance; however, do not specify more than 20 percent of available memory. Data type is NUMBER. Default = 10000000 (about 10 MB). |
| sdo_non_leaf_tbl                         | `'sdo_non_leaf_tbl=TRUE'` creates a separate index table (with a name in the form MDNT\_...\$) for nonleaf nodes of the index, in addition to creating an index table (with a name in the form MDRT\_...\$) for leaf nodes. `'sdo_non_leaf_tbl=FALSE'` creates a single table (with a name in the form MDRT\_...\$) for both leaf nodes and nonleaf nodes of the index. See the Usage Notes for more information. Data type is VARCHAR2. Default = FALSE                                            |
| sdo_rtr_pctfree                          | Specifies the minimum percentage of slots in each index tree node to be left empty when the index is created. Slots that are left empty can be filled later when new data is inserted into the table. The value can range from 0 to 50. Data type is NUMBER. Default = 10.                                                                                                                                                                                                                          |
| sequence_initial                         | Specifies the "initial" sequence cache value used internally by Spatial and Graph during index creation. If the spatial data set size is expected to increase significantly, run-time performance of DML operations may be improved by increasing the `sequence_initial` value (for example, `'sequence_initial=500'`). Default = 100. (For "normal" DML environments, the default value is suggested.)                                                                                             |
| sequence_next                            | Specifies the "next" sequence cache value used internally by Spatial and Graph after index creation, that is, when the index is updated as a result of normal user DML operations. If large amounts of spatial data are expected to be added frequently, run-time performance of DML operations may be improved by increasing the `sequence_next` value (for example, `'sequence_next=500'`).Default = 100. (For "normal" DML environments, the default value is suggested.)                        |
| PHYSICAL_STORAGE_PARAMS                  | Determines the storage parameters used for creating the spatial index data table. A spatial index data table is a regular Oracle table with a prescribed format. Not all physical storage parameters that are allowed in the STORAGE clause of a CREATE TABLE statement are supported. The following is a list of the supported subset.                                                                                                                                                             |
| tablespace                               | Specifies the tablespace in which the index data table is created. Same as TABLESPACE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                            |
| initial                                  | Is the same as INITIAL in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| next                                     | Is the same as NEXT in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| minextents                               | Is the same as MINEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| maxextents                               | Is the same as MAXEXTENTS in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| pctincrease                              | Is the same as PCTINCREASE in the STORAGE clause of a CREATE TABLE statement.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| work_tablespace                          | Specifies the tablespace for temporary tables used in creating the index. (Applies only to creating spatial R-tree indexes, and not to other types of indexes.) Specifying a work tablespace reduces fragmentation in the index tablespace, but it requires storage space of two times the size of the final index; however, after the index is created you can drop or reuse the work tablespace.                                                                                                  |
| securefile                               | `'securefile=TRUE'` enables SecureFiles Intelligent Compression to be used; `'securefile=FALSE'` causes SecureFiles Intelligent Compression not to be used. See the `compression` parameter explanation for more information. Data type is VARCHAR2. Default = `'securefile=FALSE'`                                                                                                                                                                                                                 |
| compression                              | `'compression=<OFF|LOW|MEDIUM|HIGH>'` controls the level of spatial index node compression. To specify any value other than `OFF`, you must also specify `'securefile=TRUE'`, and you must have a license for the Oracle Advanced Compression Option and implement SecureFiles Intelligent Compression. See the Usage Notes for more information. Data type is VARCHAR2. Default = `'compression=OFF'`                                                                                              |
| { NOPARALLEL \| PARALLEL \[ integer \] } | Controls whether serial (NOPARALLEL) execution or parallel (PARALLEL) execution is used for the creation of the index and for subsequent queries and DML operations that use the index. For parallel execution you can specify an integer value of degree of parallelism. See the Usage Notes for more information about parallel index creation. Default = NOPARALLEL. (If PARALLEL is specified without an integer value, the Oracle database calculates the optimum degree of parallelism.)      |

#### Prerequisites

- All current SQL CREATE INDEX prerequisites apply.

- You must have EXECUTE privilege on the index type and its implementation type.

- The USER_SDO_GEOM_METADATA view must contain an entry with the dimensions and coordinate boundary information for the table column to be spatially indexed.

#### Usage Notes

For information about spatial indexes, see [Indexing of Spatial Data](spatial-concepts.md).

For an explaiation of “\_V2” in INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2, see [Using System-Managed Spatial Indexes](indexing-querying-spatial-data.md).

Before you create a spatial index, be sure that the rollback segment size and the SORT_AREA_SIZE parameter value are adequate, as described in [Creating a Spatial Index](indexing-querying-spatial-data.md).

If an R-tree index is used on linear referencing system (LRS) data and if the LRS data has four dimensions (three plus the M dimension), the `sdo_indx_dims` parameter must be used and must specify 3 (the number of dimensions minus one), to avoid the default `sdo_indx_dims` value of 2, which would index only the X and Y dimensions. For example, if the dimensions are X, Y, Z, and M, specify `sdo_indx_dims=3` to index the X, Y, and Z dimensions, but not the measure (M) dimension. (The LRS data model, including the measure dimension, is explained in [LRS Data Model](lrs-linear-referencing-system-concepts.md).)

A partitioned spatial index can be created on a partitioned table. See [Using Partitioned Spatial Indexes](indexing-querying-spatial-data.md) for more information about partitioned spatial indexes, including benefits and restrictions.

If you want to use a local partitioned spatial index, follow the procedure in [Creating a Local Partitioned Spatial Index](indexing-querying-spatial-data.md).

A spatial index cannot be created on an index-organized table.

You can specify the PARALLEL keyword to cause the index creation to be parallelized. For example:

    CREATE INDEX cola_spatial_idx ON cola_markets(shape)
       INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2 PARALLEL;

For information about using the PARALLEL keyword, see the description of the `parallel_clause` in the section on the CREATE INDEX statement in [Oracle Database SQL Language Reference](../sqlrf/CREATE-INDEX.md). In addition, the following notes apply to the use of the PARALLEL keyword for creating or rebuilding (using the ALTER INDEX REBUILD statement) spatial indexes:

- The performance cost and benefits from parallel execution for creating or rebuilding an index depend on system resources and load. If the CPUs or disk controllers are already heavily loaded, you should not specify the PARALLEL keyword.

- Specifying PARALLEL for creating or rebuilding an index on tables with simple geometries, such as point data, usually results in less performance improvement than on tables with complex geometries.

Other options available for regular indexes (such as ASC and DESC) are not applicable for spatial indexes.

Spatial index creation involves creating and inserting index data, for each row in the underlying table column being spatially indexed, into a table with a prescribed format. All rows in the underlying table are processed before the insertion of index data is committed, and this requires adequate rollback segment space.

If a tablespace name is provided in the parameters clause, the user (underlying table owner) must have appropriate privileges for that tablespace.

For more information about using the `layer_gtype` keyword to constrain data in a layer to a geometry type, see [Constraining Data to a Geometry Type](indexing-querying-spatial-data.md).

The `sdo_dml_batch_size` parameter can improve application performance, because Spatial and Graph can preallocate system resources to perform multiple index updates more efficiently than successive single index updates; however, to gain the performance benefit, you must not perform commit operations after each insert operation or at intervals less than or equal to the `sdo_dml_batch_size` value. You should not specify a value greater than 10000 (ten thousand), because the cost of the additional memory and other resources required will probably outweigh any marginal performance increase resulting from such a value.

Specifying `'sdo_non_leaf_tbl=TRUE'` can help query performance with large data sets if the entire R-tree table may not fit in the KEEP buffer pool. In this case, you must also cause Oracle to buffer the MDNT\_...\$ table in the KEEP buffer pool, for example, by using ALTER TABLE and specifying STORAGE (BUFFER_POOL KEEP). For partitioned indexes, the same `sdo_non_leaf_tbl` value must be used for all partitions. Any physical storage parameters, except for `tablespace`, are applied only to the MDRT\_...\$ table. The MDNT\_...\$ table uses only the `tablespace` parameter, if specified, and default values for all other physical storage parameters.

The `compression` parameter with a value of `LOW`, `MEDIUM`, or `HIGH` causes the SecureFiles Intelligent Compression feature to be used. The higher the compression, the higher the latency incurred.

- 'compression=HIGH' incurs more work, but compresses the data better.

- 'compression=LOW' uses a lightweight compression algorithm that removes most of the CPU cost that is typical with file compression. Compressed SecureFiles, thus providing a very efficient choice for SecureFiles LOB storage. SecureFiles LOBs compressed at `LOW` generally consume less storage and CPU time than BasicFiles LOBs, and help applications run faster because of a reduction in disk I/O.

**Note:**

When using `compression` with any value other than `OFF`, set the [`DB_BLOCK_CHECKING`](../refrn/DB_BLOCK_CHECKING.md) database parameter to `FALSE` or `OFF`. Using any other `DB_BLOCK_CHECKING` database parameter value in conjunction with a `compression` value other than `OFF` could adversely affect spatial index DML (insert, update, or delete) operations.

If you are creating a function-based spatial index, the number of parameters must not exceed 32. For information about using function-based spatial indexes, see [SDO_GEOMETRY Objects in Function-Based Indexes](extending-spatial-indexing.md).

To determine if a CREATE INDEX statement for a spatial index has failed, check to see if the DOMIDX_OPSTATUS column in the USER_INDEXES view is set to FAILED. This is different from the case of regular indexes, where you check to see if the STATUS column in the USER_INDEXES view is set to FAILED.

If the CREATE INDEX statement fails because of an invalid geometry, the ROWID of the failed geometry is returned in an error message along with the reason for the failure.

If the CREATE INDEX statement fails for any reason, then the DROP INDEX statement must be used to clean up the partially built index and associated metadata. If DROP INDEX does not work, add the FORCE parameter and try again.

#### Examples

The following example creates a spatial R-tree index named COLA_SPATIAL_IDX.

    CREATE INDEX cola_spatial_idx ON cola_markets(shape)
       INDEXTYPE IS MDSYS.SPATIAL_INDEX_V2;

#### Related Topics

- ALTER INDEX

- DROP INDEX

**Parent topic:** SQL Statements for Indexing Spatial Data

### 19.5 DROP INDEX

#### Syntax

    DROP INDEX [schema.]index [FORCE];

#### Purpose

Deletes a spatial index.

#### Keywords and Parameters

| Value | Description                                                                                                                                 |
|:------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| FORCE | Causes the spatial index to be deleted from the system tables even if the index is marked in-progress or some other error condition occurs. |

#### Prerequisites

You must have EXECUTE privileges on the index type and its implementation type.

#### Usage Notes

Use DROP INDEX indexname FORCE to clean up after a failure in the CREATE INDEX statement.

#### Examples

The following example deletes a spatial index named OLDINDEX and forces the deletion to be performed even if the index is marked in-process or an error occurs.

    DROP INDEX oldindex FORCE;

#### Related Topics

- CREATE INDEX

**Parent topic:** SQL Statements for Indexing Spatial Data
