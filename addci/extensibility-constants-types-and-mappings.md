System Defined Constants and System Defined Types apply generically to all supported languages, as well as mappings that are specific to the PL/SQL, C, and Java languages.

### 19.1 System Defined Constants

Consider the constants defined in the `ODCIConst` package installed as part of the `catodci.sql` script. There are equivalent definitions for use within C routines in `odci.h`. You should use these constants instead of hard coding their underlying values in your routines.

The system defined constants fall into two broad categories:

- Bit-field values that may be combined using the `OR` operator: Table 19-3, Table 19-4, Table 19-5, Table 19-6, Table 19-7, Table 19-8, Table 19-9, Table 19-10

- Distinct values, where only one option may be specified: Table 19-1, Table 19-2, Table 19-12, Table 19-11

#### 19.1.1 ODCIArgDesc.ArgType System Defined Constants

Table 19-1 ODCIArgDesc.ArgType Values

| Name        | Description                       |
|:------------|:----------------------------------|
| `ArgOther`  | Argument is other expression      |
| `ArgCol`    | Argument is a column name         |
| `ArgLit`    | Argument is a literal value       |
| `ArgAttr`   | Argument is an ADT `attr` column  |
| `ArgCursor` | Argument is a `CURSOR` expression |
| `ArgNull`   | Argument is `NULL`                |

#### 19.1.2 ODCIEnv.CallProperty System Defined Constants

Table 19-2 ODCIEnv.CallProperty Values

| Name                      | Description                                                     |
|:--------------------------|:----------------------------------------------------------------|
| `None`                    | Default option                                                  |
| `FirstCall`               | First partition call                                            |
| `Intermediate Call`       | Intermediate partition call                                     |
| `FinalCall`               | Final call after last partition                                 |
| `StatsGlobal`             | Used to specify global statistics gathering                     |
| `StatsGlobalAndPartition` | Used to specify global and partition-level statistics gathering |
| `StatsPartition`          | Used to specify partition-level statistics gathering            |

#### 19.1.3 ODCIIndexAlter System Defined Constants

Table 19-3 ODCIIndexAlter Options

| Name                     | Description                                                         |
|:-------------------------|:--------------------------------------------------------------------|
| `AlterIndexNone`         | Default option                                                      |
| `AlterIndexRename`       | Rename Partition option                                             |
| `AlterIndexRebuild`      | Rebuild Index option                                                |
| `AlterIndexUpdBlockRefs` | IOT update block references                                         |
| `AlterIndexMigrate`      | Migrate user-managed domain index to a system-managed domain index. |
| `AlterIndexRenameCol`    | Rename the column on which the domain index is based                |
| `AlterIndexRenameTab`    | Rename the table on which the domain index is based                 |

#### 19.1.4 ODCIIndexInfo.Flags System Defined Constants

Table 19-4 ODCIIndexInfo.Flags Bits

| Name                  | Bits Value                  | Description                                                                                                                                                                        |
|:----------------------|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Local`               | `CONSTANT INTEGER := 1;`    | Indicates a local domain index                                                                                                                                                     |
| `Parallel`            | `CONSTANT INTEGER := 16;`   | Indicates that a parallel degree was specified for the index creation or alter operation                                                                                           |
| `Unusable`            | `CONSTANT INTEGER := 32;`   | Indicates that `UNUSABLE` was specified during index creation, and that the index is marked unusable                                                                               |
| `IndexOnIOT`          | `CONSTANT INTEGER := 64;`   | Indicates that the domain index is defined on an index-organized table                                                                                                             |
| `RangePartn`          | `CONSTANT INTEGER := 2;`    | For a local domain index, indicates that the base table is range-partitioned. Is set only in conjunction with the `Local` bit                                                      |
| `ListPartn`           | `CONSTANT INTEGER := 512;`  | For a local domain index, indicates that the base table is list-partitioned. Is set only in conjunction with the `Local` bit.                                                      |
| `HashPartn`           | `CONSTANT INTEGER := 4;`    | For a local domain index, indicates that the base table is hash-partitioned. Is set only in conjunction with the `Local` bit                                                       |
| `TransTblspc`         | `CONSTANT INTEGER := 128;`  | Indicates that the domain index is created in a transportable tablespace session.                                                                                                  |
| `FunctionIdx`         | `CONSTANT INTEGER := 256;`  | Indicates that the index is a function-based domain index                                                                                                                          |
| `Online`              | `CONSTANT INTEGER := 8;`    | Indicates an online domain index                                                                                                                                                   |
| `UpdateGlobalIndexes` | `CONSTANT INTEGER := 1024;` | Indicates that the index is an updated global domain index                                                                                                                         |
| `RefPartn`            | `CONSTANT INTEGER := 2048;` | For a local domain index, indicates that the base table is reference-partitioned. Is set only in conjunction with the `Local` bit.                                                 |
| `CompPartn`           | `CONSTANT INTEGER := 8192;` | For a local domain index, indicates that the base table is composite partitioned. Is set in conjunction with the Local bit and the `RangePartn`, `ListPartn`, or `HashPartn` bits. |
| `SubPartn`            | `CONSTANT INTEGER := 16384` | For a local domain index, indicates that the partition information for the current call refers to a subpartition. Is set in conjunction with the `CompPartn` bit.                  |

#### 19.1.5 ODCIIPartInfo.PartOp System Defined Constants

Table 19-5 Description of the ODCIIPartInfo.PartOp System Defined Constant

| Name            | Description                 |
|:----------------|:----------------------------|
| `AddPartition`  | The partition to be added   |
| `DropPartition` | The partition to be dropped |

#### 19.1.6 ODCIIPredInfo.Flags System Defined Constants

Table 19-6 ODCIIPredInfo.Flags Bits

| Name               | Description                                          |
|:-------------------|:-----------------------------------------------------|
| `PredExactMatch`   | Equality predicate                                   |
| `PredPrefixMatch`  | `LIKE` predicate                                     |
| `PredIncludeStart` | Include start value in index range scan              |
| `PredIncludeStop`  | Include stop value in index range scan               |
| `PredObjectFunc`   | Left hand side of predicate is a standalone function |
| `PredObjectPkg`    | Left hand side of predicate is a package function    |
| `PredObjectType`   | Left hand site of predicate is a type method         |
| `PredMultiTable`   | Predicate contains columns from several tables       |
| `PredNotEqual`     | Inequality predicate                                 |

#### 19.1.7 ODCIFuncInfo.Flags System Defined Constants

Table 19-7 ODCIFuncInfo.Flags Bits

| Name         | Description         |
|:-------------|:--------------------|
| `ObjectFunc` | Standalone function |
| `ObjectPkg`  | Package function    |
| `ObjectType` | Type method         |

#### 19.1.8 ODCIQueryInfo.Flags System Defined Constants

Table 19-8 ODCIQueryInfo.Flags Bits

| Name             | Description                    |
|:-----------------|:-------------------------------|
| `QueryFirstRows` | Optimizer mode is `FIRST_ROWS` |
| `QueryAllRows`   | Optimizer mode is `ALL_ROWS`   |

#### 19.1.9 ODCIStatsOptions.Flags System Defined Constants

Table 19-9 ODCIStatsOptions.Flags Bits

| Name            | Description                     |
|:----------------|:--------------------------------|
| `EstimateStats` | Estimate statistics option      |
| `ComputeStats`  | Compute exact statistics option |
| `Validate`      | Validate index option           |

#### 19.1.10 ODCIStatsOptions.Options System Defined Constants

Table 19-10 ODCIStatsOptions.Options Bits

| Name            | Description                          |
|:----------------|:-------------------------------------|
| `PercentOption` | Compute statistics by sampling       |
| `RowOption`     | Compute statistics based on all rows |

#### 19.1.11 Return Status System Defined Constants

Table 19-11 Return Status Values

| Name          | Description                                                                                                             |
|:--------------|:------------------------------------------------------------------------------------------------------------------------|
| `Success`     | Indicates a successful operation.                                                                                       |
| `Error`       | Indicates an error.                                                                                                     |
| `Warning`     | Indicates a warning.                                                                                                    |
| `ErrContinue` | Indicates that there is an error in an index partition, but continues to work on the next partition.                    |
| `Fatal`       | Indicates that all dictionary entries of the index are cleaned up, and that the `CREATE INDEX` operation is rolled back |

#### 19.1.12 ScnFlg System Defined Constants

Table 19-12 ScnFlg Values; Function with Index Context

| Name          | Description                        |
|:--------------|:-----------------------------------|
| `RegularCall` | User defined operator regular call |
| `CleanupCall` | User defined operator cleanup call |

### 19.2 System-Defined Types

Several system-defined types are defined by Oracle and must be created by running the `catodci.sql` catalog script. The C mappings for these object types are defined in `odci.h`. The `ODCIIndex` and `ODCIStats` routines described in [Extensible Indexing Interface](extensible-indexing-interface.md) and [Extensible Optimizer Interface](extensible-optimizer-interface.md) use these types as parameters.

Unless otherwise mentioned, the names parsed as type attributes are unquoted identifiers.

#### 19.2.1 ODCIArgDesc

Object type. Stores function or operator arguments.

Table 19-13 ODCIArgDesc Function and Operator Argument Description - Attributes

| Name                  | Data Type        | Description                                                                                                                                   |
|:----------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `ArgType`             | `NUMBER`         | Argument type                                                                                                                                 |
| `TableName`           | `VARCHAR2(30)`   | Name of table                                                                                                                                 |
| `TableSchema`         | `VARCHAR2(30)`   | Schema containing the table                                                                                                                   |
| `ColName`             | `VARCHAR2(4000)` | Name of column. This could be top level column name such as "A", or a nested column "A"."B" Note that the column name are quoted identifiers. |
| `TablePartitionLower` | `VARCHAR2(30)`   | Contains the name of the lowest table partition that is accessed in the query                                                                 |
| `TablePartitionUpper` | `VARCHAR2(30)`   | Contains the name of the highest table partition that is accessed in the query                                                                |
| `Cardinality`         | `NUMBER`         | Cardinality value for `CURSOR` expressions                                                                                                    |

#### 19.2.2 ODCIArgDescList

Contains a list of argument descriptors

##### Data Type

    VARRAY(32767) of ODCIArgDesc

#### 19.2.3 ODCIRidList

Stores list of rowids. The rowids are stored in their character format.

##### Data Type

`VARRAY(32767) OF VARCHAR2("M_URID_SZ")`

#### 19.2.4 ODCIColInfo

Stores column related information.

##### Data Type

Object type.

Table 19-14 ODCIColInfo Column Related Information - Attributes

| Name                  | Data Type        | Purpose                                                                                                                                       |
|:----------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `TableSchema`         | `VARCHAR2(30)`   | Schema containing table                                                                                                                       |
| `TableName`           | `VARCHAR2(30)`   | Name of table                                                                                                                                 |
| `ColName`             | `VARCHAR2(4000)` | Name of column. This could be top level column name such as "A", or a nested column "A"."B" Note that the column name are quoted identifiers. |
| `ColTypeName`         | `VARCHAR2(30)`   | Data Type of column                                                                                                                           |
| `ColTypeSchema`       | `VARCHAR2(30)`   | Schema containing data type if user-defined data type                                                                                         |
| `TablePartition`      | `VARCHAR2(30)`   | For a local domain index, contains the name of the specific base table partition                                                              |
| `TablePartitionIden`  | `NUMBER`         | Base table partition physical identifier                                                                                                      |
| `TablePartitionTotal` | `NUMBER`         | Total number of partitions in a table                                                                                                         |

#### 19.2.5 ODCIColInfoList

Stores information related to a list of columns.

##### Data Type

`VARRAY(32) OF ODCIColInfo`

#### 19.2.6 ODCICost

Object type. Stores cost information.

Table 19-15 ODCICost Cost Information - Attributes

| Name            | Data Type       | Purpose                                                                                                            |
|:----------------|:----------------|:-------------------------------------------------------------------------------------------------------------------|
| `CPUCost`       | `NUMBER`        | CPU cost                                                                                                           |
| `IOCost`        | `NUMBER`        | I/O cost                                                                                                           |
| `NetworkCost`   | `NUMBER`        | Communication cost                                                                                                 |
| `IndexCostInfo` | `VARCHAR2(255)` | Optional user-supplied information about the domain index for display in the `PLAN` table (255 characters maximum) |

#### 19.2.7 ODCIEnv

Object type. Contains general information about the environment in which the extensibility routines are executing.

Table 19-16 ODCIEnv Environment Variable Descriptor Information - Attributes

| Name           | Data Type | Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EnvFlags`     | `NUMBER`  | • 1 = Debugging On<br>• 2 = NoData; used in ODCIIndexAlter() method with alter_option = AlterIndexRebuild to indicate that there is no data in the base partition. It is set only when ODCIIndexAlter() is used as part of `TRUNCATE TABLE` and partition management operations.<br>• 4 = `UserParamString`; used in ODCIIndexAlter() method with alter_option = AlterIndexRebuild to indicate that the parameter string was specified by the user. It is set only when ODCIIndexAlter is invoked when rebuilding an index partition.<br>• 8 = RowMigration; used in ODCIIndexInsert() and ODCIIndexDelete() to indicate that the respective call to these interfaces is done because an UPDATE operation caused the row to be migrated from one partition to another. |
| `CallProperty` | `NUMBER`  | • 0 = None<br>• 1 = First Call<br>• 2 = Intermediate Call<br>• 3 = Final Call<br>• 6 = Global Statistics<br>• 7 = Global and Partition Statistics<br>• 8 = Partition Statistics                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DebugLevel`   | `NUMBER`  | Indicates the level of debugging                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

##### Usage Notes

`CallProperty` is used only for `CREATE INDEX`, `DROP INDEX`, `TRUNCATE TABLE`, and for some extensible optimizer-related calls. In all other cases, including DML and query routines for local domain indexes, it is set to `0`.

#### 19.2.8 ODCIFuncInfo

Object type. Stores functional information.

Table 19-17 ODCIFuncInfo Function Information - Attributes

| Name           | Data Type      | Purpose                          |
|:---------------|:---------------|:---------------------------------|
| `ObjectSchema` | `VARCHAR2(30)` | Object schema name               |
| `ObjectName`   | `VARCHAR2(30)` | Function/package/type name       |
| `MethodName`   | `VARCHAR2(30)` | Method name for package/type     |
| `Flags`        | `NUMBER`       | Function flags - see `ODCIConst` |

#### 19.2.9 ODCIIndexInfo

Object type. Stores the metadata information related to a domain index. It is passed as a parameter to all `ODCIIndex` routines.

Table 19-18 ODCIIndexInfo Index Related Information - Attributes

| Name                  | Data Type         | Purpose                                                                                                                                                                      |
|:----------------------|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IndexSchema`         | `VARCHAR2(30)`    | Schema containing domain index                                                                                                                                               |
| `IndexName`           | `VARCHAR2(30)`    | Name of domain index                                                                                                                                                         |
| `IndexCols`           | `ODCIColInfoList` | List of indexed columns                                                                                                                                                      |
| `IndexPartition`      | `VARCHAR2(30)`    | For a local domain index, contains the name of the specific index partition                                                                                                  |
| `IndexInfoFlags`      | `NUMBER`          | Possible flags are:<br>• `Local`<br>• `RangePartn`<br>• `Parallel`<br>• `Unusable`<br>• `IndexOnIOT`<br>• `ListPartn`<br>• `TransTblspc`<br>• `FunctionIdx`<br>• `HashPartn` |
| `IndexParaDegree `    | `NUMBER`          | The degree of parallelism, if one is specified when creating or rebuilding a domain index or local domain index partition in parallel                                        |
| `IndexPartitionIden`  | `NUMBER`          | The index partition object identifier, for local domain indexes                                                                                                              |
| `IndexPartitionTotal` | `NUMBER`          | The total number of partitions in an index                                                                                                                                   |

#### 19.2.10 ODCIIndexCtx

Object type. Stores the index context, including the domain index metadata and the rowid. It is passed as parameter to the functional implementation of an operator that expects index context.

Table 19-19 ODCIIndexCtx Index Context Related Information - Attributes

| Name        | Data Type               | Purpose                                                |
|:------------|:------------------------|:-------------------------------------------------------|
| `IndexInfo` | `ODCIIndexInfo`         | Stores the metadata information about the domain index |
| `rid`       | `VARCHAR2("M_URID_SZ")` | Row identifier of the current row                      |

#### 19.2.11 ODCIObject

Object type. Stores information about a schema object.

Table 19-20 ODCIObject Index Context Related Information - Attributes

| Name           | Data Type      | Purpose                                   |
|:---------------|:---------------|:------------------------------------------|
| `ObjectSchema` | `VARCHAR2(30)` | Name of schema in which object is located |
| `ObjectName`   | `VARCHAR2(30)` | Name of object                            |

#### 19.2.12 ODCIObjectList

Stores information about a list of schema objects.

##### Data Type

`VARRAY(32) OF ODCIObject`

#### 19.2.13 ODCIPartInfo

Object type. Contains the names of both the table partition and the index partition.

Table 19-21 ODCIPartInfo Index-Related Information - Attributes

| Name                 | Data Type      | Purpose                                     |
|:---------------------|:---------------|:--------------------------------------------|
| `TablePartition`     | `VARCHAR2(30)` | Table partition name                        |
| `IndexPartition`     | `VARCHAR2(30)` | Index partition name                        |
| `IndexPartitionIden` | NUMBER         | Index partition object identifier           |
| `PartOp`             | NUMBRER        | Partition operation that is being performed |

#### 19.2.14 ODCIPartInfoList

Stores information related to a list of partitions.

##### Data Type

`VARRAY(64000) OF ODCIPartInfo`

#### 19.2.15 ODCIPredInfo

Object type. Stores the metadata information related to a predicate containing a user-defined operator or function. It is also passed as a parameter to the [ODCIIndexStart()](extensible-indexing-interface.md) query routine.

Table 19-22 ODCIPredInfo Operator Related Information - Attributes

| Name           | Data Type      | Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ObjectSchema` | `VARCHAR2(30)` | Schema of operator/function                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `ObjectName`   | `VARCHAR2(30)` | Name of operator/function                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `MethodName`   | `VARCHAR2(30)` | Name of method, applies only to package methods type                                                                                                                                                                                                                                                                                                                                                                                                         |
| `Flags`        | `NUMBER`       | Possible flags are:<br>• `PredExactMatch` - Exact Match<br>• `PredPrefixMatch` - Prefix Match<br>• `PredIncludeStart` - Bounds include the start key value<br>• `PredIncludeStop` - Bounds include the stop key value<br>• `PredMultiTable` - Predicate involves multiple tables<br>• `PredNotEqual` - Predicate inequality<br>• `PredObjectFunc` - Object is a function<br>• `PredObjectPkg` - Object is a package<br>• `PredObjectType` - Object is a type |

#### 19.2.16 ODCIQueryInfo

Object type. Stores information about the context of a query. It is passed as a parameter to the [ODCIIndexStart()](extensible-indexing-interface.md) routine.

Table 19-23 ODCIQueryInfo Index Context Related Information - Attributes

| Name     | Data Type        | Purpose                                                                                                                                                                                                           |
|:---------|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Flags`  | `NUMBER`         | The following flags can be set:<br>• `QueryFirstRows` - Set when the optimizer hint `FIRST_ROWS` is specified in the query<br>• `QueryAllRows` - Set when the optimizer hint `ALL_ROWS` is specified in the query |
| `AncOps` | `ODCIObjectList` | Ancillary operators referenced in the query                                                                                                                                                                       |

#### 19.2.17 ODCIStatsOptions

Object type. Stores options information for `DBMS_STATS`.

Table 19-24 ODCIStatsOptions Cost Information - Attributes

| Name      | Data Type | Purpose                               |
|:----------|:----------|:--------------------------------------|
| `Sample`  | `NUMBER`  | Sample size                           |
| `Options` | `NUMBER`  | `DBMS_STATS` options - see "ODCICost" |
| `Flags`   | `NUMBER`  | `DBMS_STATS` flags - see "ODCICost"   |

#### 19.2.18 ODCITabFuncStats

Object type. Stores cardinality information for a table function.

Table 19-25 ODCITabFuncStats Parameter

| Parameter  | Data Type | Purpose                                                                   |
|:-----------|:----------|:--------------------------------------------------------------------------|
| `num_rows` | `NUMBER`  | Contains the number of rows expected to be returned by the table function |

#### 19.2.19 ODCITabStats

Stores table statistics for a table function.

##### Data Type

`NUMBER`

Table 19-26 ODCITabStats - Attributes

| Name       | Data Type | Purpose                 |
|:-----------|:----------|:------------------------|
| `Num_rows` | `NUMBER`  | Number of rows in table |

#### 19.2.20 ODCIBFileList

Stores `varray`s of `BFILE`s.

##### Data Type

`VARRAY(32767) OF BFILE`

#### 19.2.21 ODCITabFuncInfo

Object type. Stores information on which attributes of user-defined types in a collection must be set by a table function.

Table 19-27 ODCITabFuncInfo Parameters

| Name      | Data Type        | Purpose                                                                                                          |
|:----------|:-----------------|:-----------------------------------------------------------------------------------------------------------------|
| `Attrs`   | `ODCINumberList` | Indicates the attributes that must be set                                                                        |
| `RetType` | `AnyType`        | For `AnyDataSet` table functions, indicates the actual return type to be expected in the `AnyDataSet` collection |

#### 19.2.22 ODCIDateList

Stores `varray`s of `DATE`s.

##### Data Type

`VARRAY(32767) OF DATE`

#### 19.2.23 ODCINumberList

Stores `varray`s of` NUMBER`s.

##### Data Type

`VARRAY(32767) OF NUMBER`

#### 19.2.24 ODCIRawList

Stores `varray`s of `Raw`s.

##### Data Type

`VARRAY(32767) OF Raw(2000)`

#### 19.2.25 ODCIVarchar2List

Stores `varray`s of `VARCHAR2`s

##### Data Type

`VARRAY(32767) OF VARCHAR2(4000)`

#### 19.2.26 ODCIFuncCallInfo

Object type. Stores information about the functional implementation of an operator.

Table 19-28 ODCIFuncCallInfo - Attributes

| Name      | Data Type     | Purpose                                                       |
|:----------|:--------------|:--------------------------------------------------------------|
| `ColInfo` | `ODCIColInfo` | Information about the column on which the operator is invoked |

##### Usage Notes

A functional implementation can be defined with this parameter only if the operator binding is declared `WITH COLUMN CONTEXT`. This is useful if the functional implementation requires information about the column it was invoked on, and there is no domain index defined on the column. This argument is only populated in the function invocation if the first argument of the operator invocation is a column and there is no domain index defined on that column.

### 19.3 Mappings of Constants and Types

Consider language-specific constant and type mappings.

#### 19.3.1 Mappings in PL/SQL

A variety of PL/SQL mappings are common to both Extensible Indexing and the Extensible Optimizer.

- Constants are defined in the `ODCIConst` package found in `catodci.sql`

- Types are defined as object types found in `catodci.sql`

#### 19.3.2 Mappings in C

Mappings of constants and types are defined for C in the public header file `odci.h`. Each C structure to which a type is mapped has a corresponding indicator structure called `structname_ind` and a reference definition called `structname_ref`.
