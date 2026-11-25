## 15  SEM_APIS Package Subprograms

The SEM_APIS package contains subprograms (functions and procedures) for working with the Resource Description Framework (RDF) and Web Ontology Language (OWL) in an Oracle database.

To use the subprograms in this chapter, you must understand the conceptual and usage information in [RDF Semantic Graph Overview](rdf-semantic-graph-overview.md) and [OWL Concepts](owl-concepts.md)

**Note:**

If you are using an Autonomous Database instance in a shared deployment, then all the subprograms related to the following features require Oracle JVM to be enabled:

- Querying semantic data using SEM_APIS.SPARQL_TO_SQL
- Querying semantic data using SEM_MATCH Table Function
- Performing SPARQL update operations on a semantic model
- Using RDF Graph Adapter for Eclipse RDF4J
- User-Defined Inferencing and Querying

See [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless to enable Oracle JVM on your Autonomous Database instance.

This chapter provides reference information about the subprograms, listed in alphabetical order.

- SEM_APIS.ADD_DATATYPE_INDEX
- SEM_APIS.ADD_SEM_INDEX
- SEM_APIS.ALTER_DATATYPE_INDEX
- SEM_APIS.ALTER_ENTAILMENT
- SEM_APIS.ALTER_MODEL
- SEM_APIS.ALTER_SEM_INDEX_ON_ENTAILMENT
- SEM_APIS.ALTER_SEM_INDEX_ON_MODEL
- SEM_APIS.ALTER_SEM_INDEXES
- SEM_APIS.ALTER_SPM_TAB
- SEM_APIS.ANALYZE_ENTAILMENT
- SEM_APIS.ANALYZE_MODEL
- SEM_APIS.APPEND_SEM_NETWORK_DATA
- SEM_APIS.BUILD_PG_RDFVIEW_INDEXES
- SEM_APIS.BUILD_SPM_TAB
- SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE
- SEM_APIS.CLEANUP_BNODES
- SEM_APIS.CLEANUP_FAILED
- SEM_APIS.COMPOSE_RDF_TERM
- SEM_APIS.CONVERT_TO_GML311_LITERAL
- SEM_APIS.CONVERT_TO_WKT_LITERAL
- SEM_APIS.CREATE_ENTAILMENT
- SEM_APIS.CREATE_INDEX_ON_SPM_TAB
- SEM_APIS.CREATE_PG_RDFVIEW
- SEM_APIS.CREATE_RDFVIEW_MODEL
- SEM_APIS.CREATE_RULEBASE
- SEM_APIS.CREATE_SEM_MODEL
- SEM_APIS.CREATE_SEM_NETWORK
- SEM_APIS.CREATE_SOURCE_EXTERNAL_TABLE
- SEM_APIS.CREATE_SPARQL_UPDATE_TABLES
- SEM_APIS.CREATE_VIRTUAL_MODEL
- SEM_APIS.DELETE_ENTAILMENT_STATS
- SEM_APIS.DELETE_MODEL_STATS
- SEM_APIS.DISABLE_CHANGE_TRACKING
- SEM_APIS.DISABLE_INC_INFERENCE
- SEM_APIS.DISABLE_INMEMORY
- SEM_APIS.DISABLE_INMEMORY_FOR_ENT
- SEM_APIS.DISABLE_INMEMORY_FOR_MODEL
- SEM_APIS.DISABLE_NETWORK_SHARING
- SEM_APIS.DROP_DATATYPE_INDEX
- SEM_APIS.DROP_ENTAILMENT
- SEM_APIS.DROP_PG_RDFVIEW
- SEM_APIS.DROP_PG_RDFVIEW_INDEXES
- SEM_APIS.DROP_RDFVIEW_MODEL
- SEM_APIS.DROP_RULEBASE
- SEM_APIS.DROP_SEM_INDEX
- SEM_APIS.DROP_SEM_MODEL
- SEM_APIS.DROP_SEM_NETWORK
- SEM_APIS.DROP_SPARQL_UPDATE_TABLES
- SEM_APIS.DROP_SPM_TAB
- SEM_APIS.DROP_USER_INFERENCE_OBJS
- SEM_APIS.DROP_VIRTUAL_MODEL
- SEM_APIS.ENABLE_CHANGE_TRACKING
- SEM_APIS.ENABLE_INC_INFERENCE
- SEM_APIS.ENABLE_INMEMORY
- SEM_APIS.ENABLE_INMEMORY_FOR_ENT
- SEM_APIS.ENABLE_INMEMORY_FOR_MODEL
- SEM_APIS.ENABLE_NETWORK_SHARING
- SEM_APIS.ESCAPE_CLOB_TERM
- SEM_APIS.ESCAPE_CLOB_VALUE
- SEM_APIS.ESCAPE_RDF_TERM
- SEM_APIS.ESCAPE_RDF_VALUE
- SEM_APIS.EXPORT_ENTAILMENT_STATS
- SEM_APIS.EXPORT_MODEL_STATS
- SEM_APIS.EXPORT_RDFVIEW_MODEL
- SEM_APIS.GATHER_SPM_INFO
- SEM_APIS.GET_CHANGE_TRACKING_INFO
- SEM_APIS.GET_INC_INF_INFO
- SEM_APIS.GET_MODEL_ID
- SEM_APIS.GET_MODEL_NAME
- SEM_APIS.GET_TRIPLE_ID
- SEM_APIS.GETV\$DATETIMETZVAL
- SEM_APIS.GETV\$DATETZVAL
- SEM_APIS.GETV\$GEOMETRYVAL
- SEM_APIS.GETV\$NUMERICVAL
- SEM_APIS.GETV\$STRINGVAL
- SEM_APIS.GETV\$TIMETZVAL
- SEM_APIS.GRANT_MODEL_ACCESS_PRIV
- SEM_APIS.GRANT_MODEL_ACCESS_PRIVS
- SEM_APIS.GRANT_NETWORK_ACCESS_PRIVS
- SEM_APIS.GRANT_NETWORK_SHARING_PRIVS
- SEM_APIS.IMPORT_ENTAILMENT_STATS
- SEM_APIS.IMPORT_MODEL_STATS
- SEM_APIS.IS_TRIPLE
- SEM_APIS.LOAD_INTO_STAGING_TABLE
- SEM_APIS.LOOKUP_ENTAILMENT
- SEM_APIS.MERGE_MODELS
- SEM_APIS.MIGRATE_DATA_TO_CURRENT
- SEM_APIS.MOVE_SEM_NETWORK_DATA
- SEM_APIS.PRIVILEGE_ON_APP_TABLES
- SEM_APIS.PURGE_UNUSED_VALUES
- SEM_APIS.REFRESH_SEM_NETWORK_INDEX_INFO
- SEM_APIS.REMOVE_DUPLICATES
- SEM_APIS.RENAME_ENTAILMENT
- SEM_APIS.RENAME_MODEL
- SEM_APIS.RES2VID
- SEM_APIS.RESTORE_SEM_NETWORK_DATA
- SEM_APIS.REVOKE_MODEL_ACCESS_PRIV
- SEM_APIS.REVOKE_MODEL_ACCESS_PRIVS
- SEM_APIS.REVOKE_NETWORK_ACCESS_PRIVS
- SEM_APIS.REVOKE_NETWORK_SHARING_PRIVS
- SEM_APIS.SET_ENTAILMENT_STATS
- SEM_APIS.SET_MODEL_STATS
- SEM_APIS.SPARQL_TO_SQL
- SEM_APIS.SWAP_NAMES
- SEM_APIS.TRUNCATE_SEM_MODEL
- SEM_APIS.UNESCAPE_CLOB_TERM
- SEM_APIS.UNESCAPE_CLOB_VALUE
- SEM_APIS.UNESCAPE_RDF_TERM
- SEM_APIS.UNESCAPE_RDF_VALUE
- SEM_APIS.UPDATE_MODEL
- SEM_APIS.VALIDATE_ENTAILMENT
- SEM_APIS.VALIDATE_GEOMETRIES
- SEM_APIS.VALIDATE_MODEL
- SEM_APIS.VALUE_NAME_PREFIX
- SEM_APIS.VALUE_NAME_SUFFIX

**Parent topic:** [Reference Information](part-ref-supp.md)

### 15.1 SEM_APIS.ADD_DATATYPE_INDEX

#### Format

    SEM_APIS.ADD_DATATYPE_INDEX(
         datatype        IN VARCHAR2,
         tablespace_name IN VARCHAR2 DEFAULT NULL,
         parallel        IN PLS_INTEGER DEFAULT NULL,
         online          IN BOOLEAN DEFAULT FALSE,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Adds a data type index for the specified data type to a semantic network.

#### Parameters

datatype
URI of the data type to index.

tablespace_name
Destination tablespace for the index.

parallel
Degree of parallelism to use when building the index.

online
`TRUE` allows DML operations affecting the index during creation of the index; `FALSE` (the default) does not allow DML operations affecting the index during creation of the index.

options
String specifying options for index creation using the form OPTION_NAME=option_value. Supported options associated with spatial index creation are `SRID`, `TOLERANCE`, and `DIMENSIONS`. For materialized spatial index creation, use `MATERIALIZE=T`. Supported options associated with text index creation are `PREFIX_INDEX`, `PREFIX_MIN_LENGTH`, `PREFIX_MAX_LENGTH`, `SUBSTRING_INDEX`, `PREDLIST`, `PREFIXES`, and `STRING_LITERALS_ONLY`. For function-based numeric or `dateTime` index creation, use `FUNCTION=T`. The option name keywords are case sensitive and must be specified in uppercase.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges or be the network owner to call this procedure.

For more information about data type indexing, see [Using Data Type Indexes](rdf-semantic-graph-overview.md).

For information about creating a like index, see the lightweight text search material in [Full-Text Search](rdf-semantic-graph-overview.md).

For information about creating a data type index on RDF spatial data, see [Indexing Spatial Data](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates an index on `xsd:string` typed literals and plain literals in the MY_TBS tablespace.

    EXECUTE SEM_APIS.ADD_DATATYPE_INDEX('http://www.w3.org/2001/XMLSchema#string', tablespace_name=>'MY_TBS', parallel=>4);

**Parent topic:** SEM_APIS Package Subprograms

### 15.2 SEM_APIS.ADD_SEM_INDEX

#### Format

    SEM_APIS.ADD_SEM_INDEX(
        index_code          IN VARCHAR2,
        tablespace_name     IN VARCHAR2 DEFAULT NULL,
        compression_length  IN NUMBER(38) DEFAULT NULL,
        options             IN VARCHAR2 DEFAULT NULL,
        network_owner       IN VARCHAR2 DEFAULT NULL,
        network_name        IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a semantic network index that results in creation of a non-unique B-tree index in UNUSABLE status for each of the existing models and entailments of the semantic network.

#### Parameters

index_code
Index code string.

tablespace_name
Destination tablespace for the index.

compression_length

options

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges to call this procedure.

For an explanation of semantic network indexes, see [Using Semantic Network Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a semantic network index with the index code string `CSPGM` on the models and entailments of the semantic network.

    EXECUTE SEM_APIS.ADD_SEM_INDEX('CSPGM');

**Parent topic:** SEM_APIS Package Subprograms

### 15.3 SEM_APIS.ALTER_DATATYPE_INDEX

#### Format

    SEM_APIS.ALTER_DATATYPE_INDEX(
         datatype        IN VARCHAR2,
         command         IN VARCHAR2,
         tablespace_name IN VARCHAR2 DEFAULT NULL,
         parallel        IN PLS_INTEGER DEFAULT NULL,
         online          IN BOOLEAN DEFAULT FALSE,
          network_owner   IN VARCHAR2 DEFAULT NULL,
          network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Alters a data type index.

#### Parameters

datatype
URI of the data type to index.

options
String specifying the command to be performed: `REBUILD` to rebuild the data type index, or `UNUSABLE` to marks the data type index as unusable. The value for this parameter is not case-sensitive.

tablespace_name
Destination tablespace for the index.

parallel
Degree of parallelism to use when rebuilding the index.

online
`TRUE` allows DML operations affecting the index during rebuilding of the index; `FALSE` (the default) does not allow DML operations affecting the index during rebuilding of the index.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges to call this procedure.

For an explanation of data type indexes, see [Using Data Type Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example rebuilds the index on `xsd:string` typed literals and plain literals in the MY_TBS tablespace.

    EXECUTE SEM_APIS.ALTER_DATATYPE_INDEX('http://www.w3.org/2001/XMLSchema#string', command=>'REBUILD', tablespace_name=>'MY_TBS', parallel=>4);

**Parent topic:** SEM_APIS Package Subprograms

### 15.4 SEM_APIS.ALTER_ENTAILMENT

#### Format

    SEM_APIS.ALTER_ENTAILMENT(
         entailment_name IN VARCHAR2,
         command         IN VARCHAR2,
         tablespace_name IN VARCHAR2,
         parallel        IN NUMBER(38) DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Alters an entailment (rules index). Currently, the only action supported is to move the entailment to a specified tablespace.

#### Parameters

entailment_name
Name of the entailment.

command
Must be the string `MOVE`.

tablespace_name
Name of the destination tablespace.

parallel
Degree of parallelism to be associated with the operation. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of entailments, see [Entailments (Rules Indexes)](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example moves the entailment named `rdfs_rix_family` to the tablespace named `my_tbs`.

    EEXECUTE SEM_APIS.ALTER_ENTAILMENT('rdfs_rix_family', 'MOVE',  'my_tbs');

**Parent topic:** SEM_APIS Package Subprograms

### 15.5 SEM_APIS.ALTER_MODEL

#### Format

    SEM_APIS.ALTER_MODEL(
         model_name      IN VARCHAR2,
         command         IN VARCHAR2,
         tablespace_name IN VARCHAR2,
         parallel        IN NUMBER(38) DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Alters a model. Currently, the only action supported is to move the model to a specified tablespace.

#### Parameters

model_name
Name of the model.

command
Must be the string `MOVE`.

tablespace_name
Name of the destination tablespace.

parallel
Degree of parallelism to be associated with the operation. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of models, see [Semantic Data Modeling](rdf-semantic-graph-overview.md) and [Semantic Data in the Database](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example moves the model named `family` to the tablespace named `my_tbs`.

    EEXECUTE SEM_APIS.ALTER_MODEL('family', 'MOVE',  'my_tbs');

**Parent topic:** SEM_APIS Package Subprograms

### 15.6 SEM_APIS.ALTER_SEM_INDEX_ON_ENTAILMENT

#### Format

    SEM_APIS.ALTER_SEM_INDEX_ON_ENTAILMENT(
         entailment_name  IN VARCHAR2,
         index_code       IN VARCHAR2,
         command          IN VARCHAR2,
         tablespace_name  IN VARCHAR2 DEFAULT NULL,
         use_compression  IN BOOLEAN DEFAULT NULL,
         parallel         IN NUMBER(38) DEFAULT NULL,
         online           IN BOOLEAN DEFAULT FALSE),
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Alters a semantic network index on an entailment.

#### Parameters

entailment_name
Name of the entailment.

index_code
Index code string.

command
String value containing one of the following commands: `REBUILD` rebuilds the semantic network index on the entailment, or `UNUSABLE` marks as unusable the semantic network index on the entailment. The value for this parameter is not case-sensitive.

tablespace_name
Name of the destination tablespace for the rebuild operation.

use_compression
Specifies whether compression should be used when rebuilding the index.

parallel
Degree of parallelism to be associated with the operation. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

online
`TRUE` allows DML operations affecting the index during the rebuilding of the index; `FALSE` (the default) does not allow DML operations affecting the index during the rebuilding of the index.

options
(Not currently used.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of semantic network indexes, see [Using Semantic Network Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example rebuilds (and makes usable if it is unusable) the semantic network index on the entailment named `rdfs_rix_family`.

    EXECUTE SEM_APIS.ALTER_SEM_INDEX_ON_ENTAILMENT('rdfs_rix_family', 'pscm', 'rebuild');

**Parent topic:** SEM_APIS Package Subprograms

### 15.7 SEM_APIS.ALTER_SEM_INDEX_ON_MODEL

#### Format

    SEM_APIS.ALTER_SEM_INDEX_ON_MODEL(
         model_name       IN VARCHAR2,
         index_code       IN VARCHAR2,
         command          IN VARCHAR2,
         tablespace_name  IN VARCHAR2 DEFAULT NULL,
         use_compression  IN BOOLEAN DEFAULT NULL,
         parallel         IN NUMBER(38) DEFAULT NULL,
         online           IN BOOLEAN DEFAULT FALSE),
         options          IN VARCHAR2 DEFAULT NULL),
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Alters a semantic network index on a model.

#### Parameters

model_name
Name of the model.

index_code
Index code string.

command
String value containing one of the following commands: `REBUILD` rebuilds the semantic network index on the model, or `UNUSABLE` marks as unusable the semantic network index on the model. The value for this parameter is not case-sensitive.

tablespace_name
Name of the destination tablespace for the rebuild operation.

use_compression
Specifies whether compression should be used when rebuilding the index.

parallel
Degree of parallelism to be associated with the operation. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

online
`TRUE` allows DML operations affecting the index during the rebuilding of the index; `FALSE` (the default) does not allow DML operations affecting the index during the rebuilding of the index.

options
(Not currently used.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of semantic network indexes, see [Using Semantic Network Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example rebuilds (and makes usable if it is unusable) the semantic network index on the model named `family`.

    EXECUTE SEM_APIS.ALTER_SEM_INDEX_ON_MODEL('family', 'pscm', 'rebuild');

**Parent topic:** SEM_APIS Package Subprograms

### 15.8 SEM_APIS.ALTER_SEM_INDEXES

#### Format

    SEM_APIS.ALTER_SEM_INDEXES(
         attr_name  IN VARCHAR2,
         new_val    IN VARCHAR2,
         options    IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Alters an attribute of all indexes on RDF_VALUE\$ and RDF_LINK\$ tables.

#### Parameters

attr_name
Attribute to be altered..

new_val
New value for the attribute.

options
(Not currently used.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges to call this procedure.

Currently, the only `attr_name` value supported is `VISIBILITY`, and the only `new_val` values supported are `Y` (visible indexes) and `N` (invisible indexes).

For an explanation of semantic network indexes, see [Using Semantic Network Indexes](rdf-semantic-graph-overview.md), including the subtopic about using invisible indexes.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example makes all semantic network indexes invisible.

    EXECUTE SEM_APIS.ALTER_SEM_INDEXES(‘VISIBILITY’, 'N');

**Parent topic:** SEM_APIS Package Subprograms

### 15.9 SEM_APIS.ALTER_SPM_TAB

#### Format

    SEM_APIS.ALTER_SPM_TAB (
         model_name         IN VARCHAR2,
         pred_name          IN VARCHAR2,
         command            IN VARCHAR2,
         degree             IN NUMBER DEFAULT NULL,
         options            IN VARCHAR2 DEFAULT NULL,
         network_owner      IN DBMS_ID DEFAULT NULL,
         network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Alters the presence or extent of presence of the columns corresponding to a predicate in a given SPM table.

#### Parameters

model_name
Name of the RDF model.

pred_name
Name of the target predicate.

command
Determines the type of alteration.

The supported commands are:

- `ADD_PREDICATE:` Adds columns for the target predicate to an SPM table, where the target predicate is found. Applies to SVP tables only and succeeds only if the target predicate is single-valued in the given RDF model.
- `DROP_PREDICATE:` Drops columns for the target predicate from the SPM table, where the target predicate is found. Note that this applies to SVP tables only.
- `ADD_VALUE:` Adds value columns for the target predicate to an SPM table, where the target predicate is found.
- `DROP_VALUE:` Drops value columns for the target predicate from an SPM table, where the target predicate is found.

degree
Degree of parallelism to use for alter index operation.

options
String specifying any of the options to use during the operation.

Supported options are:

- `SVP_NAME=<name>: `Locates the target SVP table.
- `PCN_NAME=<name>: `Locates the target PCN table.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

#### Examples

The following example adds in-line lexical value for email:

        begin
            sem_apis.alter_spm_tab(
            model_name    =>'m1',
            pred_name     =>'<http://www.example.com#email>',
            command       =>'ADD_VALUE',
            network_owner =>'RDFUSER',
            network_name  =>'NET1'
            );
        end;

**Parent topic:** SEM_APIS Package Subprograms

### 15.10 SEM_APIS.ANALYZE_ENTAILMENT

#### Format

    SEM_APIS.ANALYZE_ENTAILMENT(
         entailment_name  IN VARCHAR2,
         estimate_percent IN NUMBER DEFAULT to_estimate_percent_type (get_param('ESTIMATE_PERCENT')),
         method_opt       IN VARCHAR2 DEFAULT get_param('METHOD_OPT'),
         degree           IN NUMBER DEFAULT to_degree_type(get_param('DEGREE')),
         cascade          IN BOOLEAN DEFAULT to_cascade_type(get_param('CASCADE')),
         no_invalidate    IN BOOLEAN DEFAULT to_no_invalidate_type (get_param('NO_INVALIDATE')),
         force            IN BOOLEAN DEFAULT FALSE),
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Collects statistics for a specified entailment (rules index).

#### Parameters

entailment_name
Name of the entailment.

estimate_percent
Percentage of rows to estimate in the internal table partition containing information about the entailment (`NULL` means compute). The valid range is \[0.000001,100\]. Use the constant `DBMS_STATS`.`AUTO_SAMPLE_SIZE` to have Oracle determine the appropriate sample size for good statistics. This is the usual default.

method_opt
Accepts either of the following options, or both in combination, for the internal table partition containing information about the entailment:

- `FOR ALL [INDEXED | HIDDEN] COLUMNS` `[size_clause]`

- `FOR COLUMNS `\[size clause\] column\|attribute \[size_clause\] \[,column\|attribute \[size_clause\]...\]

`size_clause` is defined as `size_clause := SIZE {integer | REPEAT | AUTO | SKEWONLY}`

`column` is defined as `column := column_name | (extension)`

- `- integer` : Number of histogram buckets. Must be in the range \[1,254\].
- `- REPEAT` : Collects histograms only on the columns that already have histograms.
- `- AUTO` : Oracle determines the columns to collect histograms based on data distribution and the workload of the columns.
- `- SKEWONLY` : Oracle determines the columns to collect histograms based on the data distribution of the columns.
- \- `column_name` : name of a column
- \- `extension: `Can be either a column group in the format of (`column_name`, `column_name` \[, ...\]) or an expression.

The usual default is `FOR ALL COLUMNS SIZE AUTO`.

degree
Degree of parallelism for the internal table partition containing information about the entailment. The usual default for `degree` is `NULL`, which means use the table default value specified by the `DEGREE` clause in the `CREATE TABLE` or `ALTER TABLE` statement. Use the constant `DBMS_STATS.DEFAULT_DEGREE` to specify the default value based on the initialization parameters. The `AUTO_DEGREE` value determines the degree of parallelism automatically. This is either 1 (serial execution) or `DEFAULT_DEGREE` (the system default value based on number of CPUs and initialization parameters) according to size of the object.

cascade
Gathers statistics on the indexes for the internal table partition containing information about the entailment. Use the constant `DBMS_STATS.AUTO_CASCADE` to have Oracle determine whether index statistics are to be collected or not. This is the usual default.

no_invalidate
Does not invalidate the dependent cursors if set to `TRUE`. The procedure invalidates the dependent cursors immediately if set to `FALSE`. Use `DBMS_STATS`.`AUTO_INVALIDATE`. to have Oracle decide when to invalidate dependent cursors. This is the usual default.

force
`TRUE` gathers statistics even if the entailment is locked; `FALSE` (the default) does not gather statistics if the entailment is locked.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Index statistics collection can be parellelized except for cluster, domain, and join indexes.

This procedure internally calls the DBMS_STATS.GATHER_TABLE_STATS procedure, which collects statistics for the internal table partition that contains information about the entailment. The DBMS_STATS.GATHER_TABLE_STATS procedure is documented in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md).

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about entailments, see [Entailments (Rules Indexes)](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example collects statistics for the entailment named `rdfs_rix_family`.

    EXECUTE SEM_APIS.ANALYZE_ENTAILMENT('rdfs_rix_family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.11 SEM_APIS.ANALYZE_MODEL

#### Format

    SEM_APIS.ANALYZE_MODEL(
         model_name       IN VARCHAR2,
         estimate_percent IN NUMBER DEFAULT to_estimate_percent_type (get_param('ESTIMATE_PERCENT')),
         method_opt       IN VARCHAR2 DEFAULT get_param('METHOD_OPT'),
         degree           IN NUMBER DEFAULT to_degree_type(get_param('DEGREE')),
         cascade          IN BOOLEAN DEFAULT to_cascade_type(get_param('CASCADE')),
         no_invalidate    IN BOOLEAN DEFAULT to_no_invalidate_type (get_param('NO_INVALIDATE')),
         force            IN BOOLEAN DEFAULT FALSE),
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Collects optimizer statistics for a specified model.

#### Parameters

model_name
Name of the model.

estimate_percent
Percentage of rows to estimate in the internal table partition containing information about the model (`NULL` means compute). The valid range is \[0.000001,100\]. Use the constant `DBMS_STATS`.`AUTO_SAMPLE_SIZE` to have Oracle determine the appropriate sample size for good statistics. This is the usual default.

method_opt
Accepts either of the following options, or both in combination, for the internal table partition containing information about the model:

- `FOR ALL [INDEXED | HIDDEN] COLUMNS` `[size_clause]`

- `FOR COLUMNS `\[size clause\] column\|attribute \[size_clause\] \[,column\|attribute \[size_clause\]...\]

`size_clause` is defined as `size_clause := SIZE {integer | REPEAT | AUTO | SKEWONLY}`

`column` is defined as `column := column_name | (extension)`

- `- integer` : Number of histogram buckets. Must be in the range \[1,254\].
- `- REPEAT` : Collects histograms only on the columns that already have histograms.
- `- AUTO` : Oracle determines the columns to collect histograms based on data distribution and the workload of the columns.
- `- SKEWONLY` : Oracle determines the columns to collect histograms based on the data distribution of the columns.
- \- `column_name` : name of a column
- \- `extension: `Can be either a column group in the format of (`column_name`, `column_name` \[, ...\]) or an expression.

The usual default is `FOR ALL COLUMNS SIZE AUTO`.

degree
Degree of parallelism for the internal table partition containing information about the model. The usual default for `degree` is `NULL`, which means use the table default value specified by the `DEGREE` clause in the `CREATE TABLE` or `ALTER TABLE` statement. Use the constant `DBMS_STATS.DEFAULT_DEGREE` to specify the default value based on the initialization parameters. The `AUTO_DEGREE` value determines the degree of parallelism automatically. This is either 1 (serial execution) or `DEFAULT_DEGREE` (the system default value based on number of CPUs and initialization parameters) according to size of the object.

cascade
Gathers statistics on the indexes for the internal table partition containing information about the model. Use the constant `DBMS_STATS.AUTO_CASCADE` to have Oracle determine whether index statistics are to be collected or not. This is the usual default.

no_invalidate
Does not invalidate the dependent cursors if set to `TRUE`. The procedure invalidates the dependent cursors immediately if set to `FALSE`. Use `DBMS_STATS`.`AUTO_INVALIDATE`. to have Oracle decide when to invalidate dependent cursors. This is the usual default.

force
`TRUE` gathers statistics even if the model is locked; `FALSE` (the default) does not gather statistics if the model is locked.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Index statistics collection can be parellelized except for cluster, domain, and join indexes.

This procedure internally calls the DBMS_STATS.GATHER_TABLE_STATS procedure, which collects optimizer statistics for the internal table partition that contains information about the model. The DBMS_STATS.GATHER_TABLE_STATS procedure is documented in [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md).

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example collects statistics for the semantic model named `family`.

    EXECUTE SEM_APIS.ANALYZE_MODEL('family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.12 SEM_APIS.APPEND_SEM_NETWORK_DATA

#### Format

    SEM_APIS.APPEND_SEM_NETWORK_DATA(
         from_schema    IN DBMS_ID,
         degree         IN INTEGER DEFAULT NULL,
         options        IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Appends moved semantic network data from a staging schema into a semantic network.

#### Parameters

from_schema
The staging schema that contains moved semantic network data to be appended.

degree
Degree of parallelism to use for any SQL insert or index building operations. The default is no parallel execution.

options
String specifying any options to use during the append operation. Supported options are:

- PURGE=T – drop all remaining semantic network data in the staging schema after the append operation completes.

network_owner
Owner of the destination semantic network for the append operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the destination semantic network for the append operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Partition exchange operations rather than SQL INSERT statements are used to move most of the data during the append operation, so the staging schema will no longer contain complete semantic network data after the operation is complete.

You must have DBA privileges to call this procedure.

For more information and examples, see [Moving, Restoring, and Appending a Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example appends a semantic network from the RDFEXPIMPU staging schema into the MYNET semantic network owned by RDFADMIN.

    EXECUTE sem_apis.append_sem_network_data(from_schema=>'RDFEXPIMPU',network_owner=>'RDFADMIN',network_name=>'MYNET'):

**Parent topic:** SEM_APIS Package Subprograms

### 15.13 SEM_APIS.BUILD_PG_RDFVIEW_INDEXES

#### Format

    SEM_APIS.BUILD_PG_RDFVIEW_INDEXES(
         pg_name         IN VARCHAR2,
         tsblespace_name IN VARCHAR2 DEFAULT NULL,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

or

    SEM_APIS.BUILD_PG_RDFVIEW_INDEXES(
         pg_name         IN VARCHAR2,
         tsblespace_name IN VARCHAR2 DEFAULT NULL,
         pg_edge_kv_tab  IN VARCHAR2,
         pg_node_kv_tab  IN VARCHAR2,
         pg_edge_tab     IN VARCHAR2,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a set of default indexes to speed up queries against property graph RDF views.

#### Parameters

pg_name
Name of the property graph to index.

tablespace_name
Destination tablespace for the indexes.

pg_edge_kv_tab
Name of the table storing edge properties

 pg_node_kv_tab
Name of the table storing node properties.

pg_edge_tab
Name of the table storing distinct edges.

options
String specifying options for index creation using the form OPTION_NAME=option_value. Supported options are:

- SUB_K=N, SUB_EL=N (use a substring of N characters for property key name or edge label)

- GT_TABLE=T (assume a populated GT\$ table)

- PARALLEL=N (use a degree of parallelism of N during index creation)

- SKIP_VAL_IDX=T (skip creation of indexes on vertex/edge property values)

- SKIP_FUNC_IDX=T (skip creation of function based indexes on edge start and end vertex URIs)

- SUB_V_IDX=N (use a substring of N characters when indexing string-valued vertex and edge properties)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Indexes should be created on the property graph tables for improved performance of RDF view queries. You can create any number of index schemes on these tables, but the SEM_APIS.BUILD_PG_RDFVIEW_INDEXES procedure is provided for convenience.

Several indexes are created by default by the SEM_APIS.BUILD_PG_RDFVIEW_INDEXES procedure. The following indexes are used to look up vertex and edge properties based on property name and type:

    create index g1$ntk on g1vt$(
      T
    , substr(K,1,200))
    compress local nologging;

    create index g1$etk on g1ge$(
      T
    , substr(k,1,200))
    compress local nologging;

The following indexes are used for graph traversals. If you indicate that the G1LGT\$ table is populated (by specifying `options => ‘GT_TABLE=T’`), these indexes will be created on the G1GT\$ table instead of on the G1GE\$ table.

    create index g1$lsd on g1ge$(
      substr(el,1,200)
    , svid
    , dvid
    , eid)
    compress local nologging;

    create index g1$lds on g1ge$(
      substr(el,1,200)
    , dvid
    , svid
    , eid)
    compress local nologging;

The following function-based are used for graph traversals based on vertex URIs. These function-based indexes can be skipped with the `'SKIP_FUNC_IDX=T'` option. If you indicate that the G1LGT\$ table is populated (by specifying `options => ‘GT_TABLE=T’`), these indexes will be created on the G1GT\$ table instead of on the G1GE\$ table.

    create index g1$lsd on g1ge$(
      substr(el,1,200)
    , svid
    , dvid
    , eid)
    compress local nologging;

    create index g1$lds on g1ge$(
      substr(el,1,200)
    , dvid
    , svid
    , eid)
    compress local nologging;

The following function-based indexes are used to look up vertices and edges based on their URIs.

    create index g1$idf on g1ge$(
      '<http://xmlns.oracle.com/pg/edge/e'||TO_CHAR("EID")||'>')
    compress local nologging;

    create index g1$vid on g1vt$(
      '<http://xmlns.oracle.com/pg/vertex/v'||TO_CHAR("VID")||'>')
    compress local nologging;

The following indexes are used to lookup vertices and edges based on their property values. These indexes can be skipped with the 'SKIP_VAL_IDX=T' option..

    -- varchar --
    create index g1$nvt on g1vt$(
      substr(to_char(V),1,200)
    , T
    compress local nologging;

    -- number --
    create index g1$nnt on g1vt$(
      VN
    , T
    compress local nologging;

    -- date --
    create index g1$ndt on g1vt$(
      VT
    , T
    compress local nologging;

    -- varchar --
    create index g1$evt on g1ge$(
      substr(to_char(V),1,200)
    , T
    compress local nologging;

    -- number --
    create index g1$ent on g1ge$(
      VN
    , T
    compress local nologging;

    -- date --
    create index g1$edt on g1ge$(
      VT
    , T
    compress local nologging;

For more information, see [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example builds indexes for the property graph G1 in tablespace MY_TBS and skips creation of value indexes.

    EXECUTE SEM_APIS.BUILD_PG_RDFVIEW_INDEXES('G1', 'MY_TBS', ' SKIP_VAL_IDX=T ');

The following example builds indexes for the property graph G1in tablespace MY_TBS with property graph tables MY_EDGE_KV_TAB, MY_NODE_KV_TAB, and MY_EDGE_TAB. In addition, a populated distinct edges table is specified.

    EXECUTE SEM_APIS.BUILD_PG_RDFVIEW_INDEXES('G1', 'MY_TBS', 'MY_EDGE_KV_TAB', 'MY_NODE_KV_TAB', 'MY_EDGE_TAB', 'GT_TABLE=T');

**Parent topic:** SEM_APIS Package Subprograms

### 15.14 SEM_APIS.BUILD_SPM_TAB

#### Format

    SEM_APIS.BUILD_SPM_TAB (
        model_name         IN VARCHAR2,
        pred_info_tabname  IN DBMS_ID DEFAULT NULL,
        pred_name          IN VARCHAR2 DEFAULT NULL,
        tablespace_name    IN DBMS_ID DEFAULT NULL,
        degree             IN NUMBER DEFAULT NULL,
        pred_info_owner    IN DBMS_ID DEFAULT NULL,
        options            IN VARCHAR2 DEFAULT NULL,
        network_owner      IN DBMS_ID DEFAULT NULL,
        network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Creates an SPM table for the specified RDF model.

The type of SPM table can be SVP, MVP, or PCN depending upon values passed for the `pred_info_tabname`, `pred_name`, and `options` parameters. More information on these parameters are described in the following Parameters section.

#### Parameters

model_name
Name of the RDF model.

pred_info_tabname
Name of the table to use to get predicate information, when creating an SVP or a PCN table. Otherwise, this value must be `NULL`.

pred_name
Name of the target predicate, when creating an MVP table. Otherwise, this value must be NULL.

tablespace_name
Name of the target tablespace for the SPM table.

degree
Degree of parallelism to use for alter index operation.

pred_info_owner
Owner of the` pred_info_tabname`. If `NULL`, then the invoker is assumed to be the owner.

options
String specifying any options to use during the operation.

Supported options are:

- `CREATE_ANYWAY=T`: Drops the target SPM table is it exists.
- `PCN_NAME=<name>`: Generates the given name for the PCN table.
- `SVP_NAME=<name>`: Generates the given name for the SVP table, if the specified name is not `DEFAULT`.
- `INCLUDE_VALUE=T`: Includes the lexical value columns, when creating an MVP table.
- `INCLUDE_VALUE`: Same as `INCLUDE_VALUE=T`.
- `S_INDEX=F`: Index on the `START_NODE_ID` column, will not be created for an MVP table.
- `P_INDEX=F`: Indexes on the individual predicate columns (that make up the predicate-chain) will not be created.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

- This operation has a DDL semantics.

- The invoker must be the owner of the RDF model or the RDF network or both.

- The network owner must have READ privilege on table specified by `pred_info_tabname`.

- When creating SVP and PCN tables, content of the `INCLUDE` column in each row (that corresponds to a predicate) in `pred_info_tabname` determines whether the `ID` column and optionally the `VALUE` columns corresponding to a predicate must be included in the SPM table that is being created.

  The following are all the possibilities regarding inclusion (and relative position) or exclusion of columns for a predicate, based on `INCLUDE` column content:

  - `INCLUDE=N`: excluded in SVP table.
  - `INCLUDE=NULL` and `max_cnt=1`: included in SVP table.
  - `INCLUDE=V` and `max_cnt=1`: included in SVP table along with value columns.
  - `INCLUDE=<positiveInteger>C` or `INCLUDE=<positiveInteger>CV`: included in PCN table, along with value columns if `V` is present. The specified`<positiveInteger>` determines the relative ordering of columns for different predicates included in the PCN table.

#### Examples

The following example creates a SVP table:

    begin
          sem_apis.build_spm_tab(
            model_name        => 'M1',
            pred_info_tabname => 'M1_PRED_INFO',
            pred_name         => NULL,
            options           => 'svp_name=fnm_lnm_hght ',
            degree            => 2,
            network_owner     => 'RDFUSER',
            network_name      => 'NET1'
         );
    end;

The following example creates a PCN table:

    begin
          sem_apis.build_spm_tab(
            model_name        => 'M1',
            pred_info_tabname => 'M1_PRED_INFO',
            pred_name         => NULL,
            options           => ' pcn_name=addr_state ',
            degree            => 2,
            network_owner     => 'RDFUSER',
            network_name      => 'NET1'
         );
    end;

The following example creates a MVP table:

    begin
          sem_apis.build_spm_tab(
            model_name        => 'M1',
            pred_info_tabname => NULL,
            pred_name         => '<http://www.example.com#friendOf>',
            options           => ' mvp_pred_id=6549504896746291108 ',,
            degree            => 2,
            network_owner     => 'RDFUSER',
            network_name      => 'NET1'
         );
    end;

**Parent topic:** SEM_APIS Package Subprograms

### 15.15 SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE

#### Format

    SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE(
         model_name    IN VARCHAR2,
         table_owner   IN VARCHAR2,
         table_name    IN VARCHAR2,
         flags         IN VARCHAR2 DEFAULT NULL,
         debug         IN INTEGER DEFAULT NULL,
         start_comment IN VARCHAR2 DEFAULT NULL,
         end_comment   IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Loads semantic data from a staging table.

#### Parameters

model_name
Name of the model.

table_owner
Name of the schema that owns the staging table that holds semantic data to be loaded.

table_name
Name of the staging table that holds semantic data to be loaded.

flags
An optional quoted string with one or more of the following keyword specifications:

- `COMPRESS=CSCQH` uses COLUMN STORE COMPRESS FOR QUERY HIGH on the RDF_LINK\$ partition for the model.

- `COMPRESS=CSCQL` uses COLUMN STORE COMPRESS FOR QUERY LOW on the RDF_LINK\$ partition for the model.

- COMPRESS=RSCA uses ROW STORE COMPRESS ADVANCED on the RDF_LINK\$ partition for the model.

- COMPRESS=RSCAB uses ROW STORE COMPRESS BASIC on the RDF_LINK\$ partition for the model.

- `DEL_BATCH_DUPS=USE_INSERT` allows the use of an insertion-based strategy for duplicate elimination that may lead to faster processing if the input data contains many duplicates.

- `MBV_METHOD=SHADOW` allows the use of a different value loading strategy that may lead to faster processing for large loads.

- `PARALLEL_CREATE_INDEX` allows internal indexes to be created in parallel, which may improve the performance of the bulk load processing.

- `PARALLEL=<``integer``>` allows much of the processing used during bulk load to be done in parallel using the specified degree of parallelism to be associated with the operation.

- `PARSE` allows parsing of triples retrieved from the staging table (also parses triples containing graph names).

- `<task>``_JOIN_HINT=``<join_type>`, where \<task\> can be any of the following internal tasks performed during bulk load: `IZC` (is zero collisions), `MBV` (merge batch values), or `MBT` (merge batch triples, used when adding triples to a non-empty model), and where \<join_type\> can be `USE_NL` and `USE_HASH`.

debug
(Reserved for future use)

start_comment
Optional comment about the start of the load operation.

end_comment
Optional comment about the end of the load operation.

<!-- -->

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must first load semantic data into a staging table before calling this procedure. See [Bulk Loading Semantic Data Using a Staging Table](rdf-semantic-graph-overview.md) for more information.

Using BULK_LOAD_FROM_STAGING_TABLE with Fine Grained Access Control (OLS)

When fine-grained access control (explained in [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md) ) is enabled for the entire network using OLS, only a user with FULL access privileges to the associated policy may perform the bulk load operation. When OLS is enabled, full access privileges to the OLS policy are granted using the SA_USER_ADMIN.SET_USER_PRIVS procedure.

When the OLS is used, the label column in the tables storing the RDF triples must be maintained. By default, with OLS enabled, the label column in the tables storing the RDF triples is set to null. If you have FULL access, you can reset the labels for the newly inserted triples as well as any resources introduced by the new batch of triples by using appropriate subprograms ([SEM_RDFSA.SET_RESOURCE_LABEL](SEM_RDFSA-reference.md) and [SEM_RDFSA.SET_PREDICATE_LABEL](SEM_RDFSA-reference.md)).

Optionally, you can define a numeric column named RDF\$STC_CTXT1 in the staging table and the application table, to assign the sensitivity label of the triple before the data is loaded into the desired model. Such labels are automatically applied to the corresponding triples stored in the RDF_LINK\$ table. The labels for the newly introduced resources may still have to be applied separately before or after the load, and the system does not validate the labels assigned during bulk load operation.

The RDF\$STC_CTXT1 column in the application table has no significance, and it may be dropped after the bulk load operation.

By default, SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE uses the semantic network compression setting (stored in RDF_PARAMETER table) for the model.

#### Examples

The following example loads semantic data stored in the staging table named STAGE_TABLE in schema SCOTT into the semantic model named `family`. The example includes some join hints.

    EXECUTE SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE('family', 'scott', 'stage_table', flags => 'IZC_JOIN_HINT=USE_HASH MBV_JOIN_HINT=USE_HASH');

**Parent topic:** SEM_APIS Package Subprograms

### 15.16 SEM_APIS.CLEANUP_BNODES

#### Format

    SEM_APIS.CLEANUP_BNODES(
         model_name      IN VARCHAR2,
         tablespace_name IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL);

#### Description

Corrects blank node identifiers for blank nodes in a specified model.

#### Parameters

model_name
Name of the model.

tablespace_name
Name of the tablespace to use for storing intermediate data.

options
String specifying one or more options to influence the behavior of the procedure. See the Usage Notes for available option values.

#### Usage Notes

See [Blank Nodes: Special Considerations for SPARQL Update](rdf-semantic-graph-overview.md).

The `options` parameter can contain one or more of the following keywords:

- `APPEND`: Uses the APPEND hint when populating tables during blank node correction.

- `PARALLEL(``n``)`: Uses n as the degree of parallelism during blank node correction.

- `RECOVER_FAILED=T`: Include this option when a previous attempt to correct blank nodes has been interrupted, and transient tables with intermediate data have not been deleted.

#### Examples

The following example corrects blank node identifiers for the `electronics` semantic model.

    EXECUTE SEM_APIS.CLEANUP_BNODES('electronics');

**Parent topic:** SEM_APIS Package Subprograms

### 15.17 SEM_APIS.CLEANUP_FAILED

#### Format

    SEM_APIS.CLEANUP_FAILED(
         rdf_object_type  IN VARCHAR2,
         rdf_object_name  IN VARCHAR2),
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 default NULL);

#### Description

Drops (deletes) a specified rulebase or entailment if it is in a failed state.

#### Parameters

rdf_object_type
Type of the RDF object: `RULEBASE` for a rulebase or `RULES_INDEX` for an entailment (rules index).

rdf_object_name
Name of the RDF object of type `rdf_object_type`.

options
(Not currently used.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure checks to see if the specified RDF object is in a failed state; and if the object is in a failed state, the procedure deletes the object.

A rulebase or entailment is in a failed state if a system failure occurred during the creation of that object. You can check if a rulebase or entailment is in a failed state by checking to see if the value of the STATUS column is `FAILED` in the SDO_RULEBASE_INFO view (described in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md)) or the SDO_RULES_INDEX_INFO view (described in [Entailments (Rules Indexes)](rdf-semantic-graph-overview.md)), respectively.

If the rulebase or entailment is not in a failed state, this procedure performs no action and returns a successful status.

An exception is generated if the RDF object is currently being used.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes the rulebase named `family_rb` if (and only if) that rulebase is in a failed state.

    EXECUTE SEM_APIS.CLEANUP_FAILED('RULEBASE', 'family_rb');

**Parent topic:** SEM_APIS Package Subprograms

### 15.18 SEM_APIS.COMPOSE_RDF_TERM

#### Format

    SEM_APIS.COMPOSE_RDF_TERM(
         value_name    IN VARCHAR2,
         value_type    IN VARCHAR2,
         literal_type  IN VARCHAR2,
         language_type IN VARCHAR2
         ) RETURN VARCHAR2;

or

    SEM_APIS.COMPOSE_RDF_TERM(
         value_name    IN VARCHAR2,
         value_type    IN VARCHAR2,
         literal_type  IN VARCHAR2,
         language_type IN VARCHAR2,
         long_value    IN CLOB,
         options       IN VARCHAR2 DEFAULT NULL,
         ) RETURN CLOB;

#### Description

Creates and returns an RDF term using the specified parameters.

#### Parameters

value_name
Value name. Must match a value in the VALUE_NAME column in the RDF_VALUE\$ table (described in [Statements](rdf-semantic-graph-overview.md)) or in the var attribute returned from SEM_MATCH table function.

value_type
The type of text information. Must match a value in the VALUE_TYPE column in the RDF_VALUE\$ table (described in [Statements](rdf-semantic-graph-overview.md)) or in the var\$RDFVTYP attribute returned from SEM_MATCH table function.

literal_type
For typed literals, the type information; otherwise, null. Must either be a null value or match a value in the LITERAL_TYPE column in the RDF_VALUE\$ table (described in [Statements](rdf-semantic-graph-overview.md)) or in the var\$RDFLTYP attribute returned from SEM_MATCH table function.

language_type
Language tag. Must match a value in the LANGUAGE_TYPE column in the RDF_VALUE\$ table (described in [Statements](rdf-semantic-graph-overview.md)) or in the var\$RDFLANG attribute returned from SEM_MATCH table function.

long_value
The character string if the length of the lexical value is greater than 4000 bytes. Must match a value in the LONG_VALUE column in the RDF_VALUE\$ table (described in [Statements](rdf-semantic-graph-overview.md)) or in the var\$RDFCLOB attribute returned from SEM_MATCH table function.

options
(Reserved for future use.)

#### Usage Notes

If you specify an inconsistent combination of values for the parameters, this function returns a null value. If a null value is returned but you believe that the values for the parameters are appropriate (reflecting columns from the same row in the RDF_VALUE\$ table or from a SEM_MATCH query for the same variable), contact Oracle Support.

#### Examples

The following example returns, for each member of the family whose height is known, the RDF term for the height and also just the value portion of the height.

    SELECT x, SEM_APIS.COMPOSE_RDF_TERM(h, h$RDFVTYP, h$RDFLTYP, h$RDFLANG)
           h_rdf_term, h
      FROM TABLE(SEM_MATCH(
        '{?x :height ?h}',
        SEM_Models('family'),
        null,
        SEM_ALIASES(SEM_ALIAS('','http://www.example.org/family/')),
        null))
    ORDER BY x;
    X
    --------------------------------------------------------------------------------
    H_RDF_TERM
    --------------------------------------------------------------------------------
    H
    --------------------------------------------------------------------------------
    http://www.example.org/family/Cathy
    "5.8"^^<http://www.w3.org/2001/XMLSchema#decimal>
    5.8

    http://www.example.org/family/Cindy
    "6"^^<http://www.w3.org/2001/XMLSchema#decimal>
    6

    http://www.example.org/family/Jack
    "6"^^<http://www.w3.org/2001/XMLSchema#decimal>
    6

    http://www.example.org/family/Tom
    "5.75"^^<http://www.w3.org/2001/XMLSchema#decimal>
    5.75

    4 rows selected.

The following example returns the RDF terms for a few of the values stored in the RDF_VALUE\$ table.

    SELECT SEM_APIS.COMPOSE_RDF_TERM(value_name, value_type, literal_type,
         language_type)
      FROM RDF_VALUE$ WHERE ROWNUM < 5;

    SEM_APIS.COMPOSE_RDF_TERM(VALUE_NAME,VALUE_TYPE,LITERAL_TYPE,LANGUAGE_TYPE)
    --------------------------------------------------------------------------------
    <http://www.w3.org/1999/02/22-rdf-syntax-ns#object>
    <http://www.w3.org/1999/02/22-rdf-syntax-ns#type>
    <http://www.w3.org/1999/02/22-rdf-syntax-ns#subject>
    <http://www.w3.org/1999/02/22-rdf-syntax-ns#Property>

**Parent topic:** SEM_APIS Package Subprograms

### 15.19 SEM_APIS.CONVERT_TO_GML311_LITERAL

#### Format

    SEM_APIS.CONVERT_TO_GML311_LITERAL(
         geom         IN SDO_GEOMETRY,
         options      IN VARCHAR2 default NULL
         )RETURN CLOB;

#### Description

Serializes an SDO_GEOMETRY object into an `ogc:gmlLiteral` value.

#### Parameters

geom
SDO_GEOMETRY object to be serialized.

options
(Reserved for future use.)

#### Usage Notes

The procedure SDO_UTIL.TO_GML311GEOMETRY is used internally to create the geometry literal with a certain spatial reference system URI.

For more information about geometry serialization, see [SDO_UTIL.TO_GML311GEOMETRY](../spatl/SDO_UTIL-reference.md).

#### Examples

The following example shows the use of this function for a geometry with SRID 8307 The COLA_MARKETS table is the one from the [simple example](../spatl/spatial-datatypes-metadata.md) in Oracle Spatial and Graph Developer's Guide.

    INSERT INTO cola_markets VALUES(
      10,
      'cola_x',
      SDO_GEOMETRY(
        2003,
        8307, -- SRID
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(1,1, 6,13)
      )
    );
    commit;

    SELECT
    sem_apis.convert_to_gml311_literal(shape) as gml1
    FROM cola_markets;

    "<gml:Polygon srsName=\"SDO:8307\" xmlns:gml=\"http://www.opengis.net/gml\"><gml
    :exterior><gml:LinearRing><gml:posList srsDimension=\"2\">1.0 1.0 6.0 1.0 6.0 13.0 1.0 13.0 1.0 1.0 </gml:posList></gml:LinearRing></gml:exterior></gml:Polygon>
    "^^<http://www.opengis.net/ont/geosparql#gmlLiteral>

**Parent topic:** SEM_APIS Package Subprograms

### 15.20 SEM_APIS.CONVERT_TO_WKT_LITERAL

#### Format

    SEM_APIS.CONVERT_TO_WKT_LITERAL(
         geom         IN SDO_GEOMETRY,
         srid_prefix  IN VARCHAR2 default NULL,
         options      IN VARCHAR2 default NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 default NULL
         )RETURN CLOB;

#### Description

Serializes an SDO_GEOMETRY object into an `ogc:wktLiteral` value.

#### Parameters

geom
SDO_GEOMETRY object to be serialized.

srid_prefix
Spatial reference system URI prefix that should be used in the `ogc:wktLiteral` instead of the default. The resulting SRID URI will be of the form `<srid_prefix/{srid}>`.

options
String specifying options for transformation. Available options are:

- ORACLE_PREFIX=T. Generate SRID URIs of the form `<http://xmlns.oracle.com/rdf/geo/srid/{srid}>`.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The procedure SDO_UTIL.TO_WKTGEOMETRY is used internally to create the geometry literal with a certain spatial reference system URI.

Standard SRID URIs are used by default (`<http://www.opengis.net/def/crs/EPSG/0/{srid}>` or (`<http://www.opengis.net/def/crs/OGC/1.3/CRS84>>`).

For more information about geometry serialization, see [SDO_UTIL.TO_WKTGEOMETRY](../spatl/SDO_UTIL-reference.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example shows three different uses of this function for a geometry with SRID 8307. The COLA_MARKETS table is the one from the [simple example](../spatl/spatial-datatypes-metadata.md) in Oracle Spatial and Graph Developer's Guide.

    INSERT INTO cola_markets VALUES(
      10,
      'cola_x',
      SDO_GEOMETRY(
        2003,
        8307, -- SRID
        NULL,
        SDO_ELEM_INFO_ARRAY(1,1003,3),
        SDO_ORDINATE_ARRAY(1,1, 6,13)
      )
    );
    commit;

    SELECT
    sem_apis.convert_to_wkt_literal(shape) as wkt1,
    sem_apis.convert_to_wkt_literal(shape,'http://my.org/') as wkt2,
    sem_apis.convert_to_wkt_literal(shape,null,' ORACLE_PREFIX=T ') as wkt3
    FROM cola_markets;

    "<http://www.opengis.net/def/crs/OGC/1.3/CRS84> POLYGON ((1.0 1.0, 6.0 1.0, 6.0 13.0, 1.0 13.0, 1.0 1.0))"^^<http://www.opengis.net/ont/geosparql#wktLiteral>
    "<http://my.org/8307> POLYGON ((1.0 1.0, 6.0 1.0, 6.0 13.0, 1.0 13.0, 1.0 1.0))"^^<http://www.opengis.net/ont/geosparql#wktLiteral>
    "<http://xmlns.oracle.com/rdf/geo/srid/8307> POLYGON ((1.0 1.0, 6.0 1.0, 6.0 13.0, 1.0 13.0, 1.0 1.0))"^^<http://www.opengis.net/ont/geosparql#wktLiteral>

**Parent topic:** SEM_APIS Package Subprograms

### 15.21 SEM_APIS.CREATE_ENTAILMENT

#### Format

    SEM_APIS.CREATE_ENTAILMENT(
         entailment_name_in IN VARCHAR2,
         models_in          IN SEM_MODELS,
         rulebases_in       IN SEM_RULEBASES,
         passes             IN NUMBER DEFAULT SEM_APIS.REACH_CLOSURE,
         inf_components_in  IN VARCHAR2 DEFAULT NULL,
         options            IN VARCHAR2 DEFAULT NULL,
         delta_in           IN SEM_MODELS DEFAULT NULL,
         label_gen          IN RDFSA_LABELGEN DEFAULT NULL,      
         include_named_g    IN SEM_GRAPHS DEFAULT NULL,      
         include_default_g  IN SEM_MODELS DEFAULT NULL,      
         include_all_g      IN SEM_MODELS DEFAULT NULL,      
         inf_ng_name        IN VARCHAR2 DEFAULT NULL,      
         inf_ext_user_func_name IN VARCHAR2 DEFAULT NULL,
         ols_ladder_inf_lbl_sec IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates an entailment (rules index) that can be used to perform OWL or RDFS inferencing, and optionally use user-defined rules.

#### Parameters

entailment_name_in
Name of the entailment to be created.

models_in
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

rulebases_in
One or more rulebase names. Its data type is SEM_RULEBASES, which has the following definition: `TABLE OF VARCHAR2(25)`. Rules and rulebases are explained in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md).

passes
The number of rounds that the inference engine should run. The default value is `SEM_APIS.REACH_CLOSURE`, which means the inference engine will run till a closure is reached. If the number of rounds specified is less than the number of actual rounds needed to reach a closure, the status of the entailment will then be set to `INCOMPLETE`.

inf_components_in
A comma-delimited string of keywords representing inference components, for performing selective or component-based inferencing. If this parameter is null, the default set of inference components is used. See the Usage Notes for more information about inference components.

options
A comma-delimited string of options to control the inference process by overriding the default inference behavior. To enable an option, specify `option-name``=T`; to disable an option, you can specify `option-name``=F` (the default). The available option-name values are `COL_COMPRESS`, `DEST_MODEL`, `DISTANCE,DOP`, `ENTAIL_ANYWAY`, `HASH_PART`, `INC`, `LOCAL_NG_INF`, `OPT_SAMEAS`, `RAW8`, `PROOF`, and `USER_RULES`. See the Usage Notes for explanations of each value.

delta_in
If incremental inference is in effect, specifies one or more models on which to perform incremental inference. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

The triples in the first model in `delta_in` are copied to the first model in `models_in`, and the entailment (rules index) in `rules_index_in` is updated; then the triples in the second model (if any) in `delta_in` are copied to the second model (if any) in `models_in`, and the entailment in `rules_index_in` is updated; and so on until all triples are copied and the entailment is updated. (The `delta_in` parameter has no effect if incremental inference is not enabled for the entailment.)

label_gen
An instance of RDFSA_LABELGEN or a subtype of it, defining the logic for generating Oracle Label Security (OLS) labels for inferred triples. What you specify for this parameter depends on whether you use the default label generator or a custom label generator:

- If you use the default label generator, specify one of the following constants: `SEM_RDFSA.LABELGEN_RULE` for Use Rule Label, `SEM_RDFSA.LABELGEN_SUBJECT` for Use Subject Label, `SEM_RDFSA.LABELGEN_PREDICATE` for Use Predicate Label, `SEM_RDFSA.LABELGEN_OBJECT` for Use Object Label, `SEM_RDFSA.LABELGEN_DOMINATING` for Use Dominating Label, `SEM_RDFSA.LABELGEN_ANTECED` for Use Antecedent Labels.

- If you use a custom label generator, specify the custom label generator type.

include_named_g
Causes all triples from the specified named graphs (across all source models) to participate in named graph based global inference (NGGI, explained in [Named Graph Based Global Inference (NGGI)](owl-concepts.md)). For example, `include_named_g => sem_graphs('<urn:G1>','<urn:G2>')` implies that triples from named graphs `G1` and `G2` will be included in NGGI.

Its data type is SEM_GRAPHS, which has the following definition: `TABLE OF VARCHAR2(4000)`.

include_default_g
Causes all triples with a null graph name in the specified models to participate in named graph based global inference (NGGI, explained in [Named Graph Based Global Inference (NGGI)](owl-concepts.md)). For example, `include_default_g => sem_models('m1')` causes all triples with a null graph name from model `M1` to be included in NGGI.

include_all_g
Causes all triples, regardless of their graph name values, in the specified models to participate in named graph based global inference (NGGI, explained in [Named Graph Based Global Inference (NGGI)](owl-concepts.md)). For example, `include_all_g => sem_models('m2')`causes all triples in model `M2` to be included in NGGI.

inf_ng_name
Assigns the specified graph name to all the new triples inferred by the named graph based global inference (NGGI, explained in [Named Graph Based Global Inference (NGGI)](owl-concepts.md)).

inf_ext_user_func_name
The name of a user-defined inference function, or a comma-delimited list of names of user-defined functions. For information about creating user-defined inference functions, including format requirements and options for certain parameters, see [API Support for User-Defined Inferencing](user-defined-inferencing.md). (For information about user-defined inferencing, including examples, see [User-Defined Inferencing and Querying](user-defined-inferencing.md).)

ols_ladder_inf_lbl_sec

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For the `inf_components_in` parameter, you can specify any combination of the following keywords: `SCOH`, `COMPH`, `DISJH`, `SYMMH`, `INVH`, `SPIH`, `MBRH`, `SPOH`, `DOMH`, `RANH`, `EQCH`, `EQPH`, `FPH`, `IFPH`, `DOM`, `RAN`, `SCO`, `DISJ`, `COMP`, `INV`, `SPO`, `FP`, `IFP`, `SYMM`, `TRANS`, `DIF`, `SAM`, `CHAIN`, `HASKEY`, `ONEOF`, `INTERSECT`, `INTERSECTSCOH`, `MBRLST`, `PROPDISJH`, `SKOSAXIOMS`, `SNOMED`, `SVFH`, `THINGH`, `THINGSAM`, `UNION`, `RDFP1`, `RDFP2`, `RDFP3`, `RDFP4`, `RDFP6`, `RDFP7`, `RDFP8AX`, `RDFP8BX`, `RDFP9`, `RDFP10`, `RDFP11`, `RDFP12A`, `RDFP12B`, `RDFP12C`, `RDFP13A`, `RDFP13B`, `RDFP13C`, `RDFP14A`, `RDFP14BX`, `RDFP15`, `RDFP16`, `RDFS2`, `RDFS3`, `RDFS4a`, `RDFS4b`, `RDFS5`, `RDFS6`, `RDFS7`, `RDFS8`, `RDFS9`, `RDFS10`, `RDFS11`, `RDFS12`, `RDFS13`. For an explanation of the meaning of these keywords, see Table 15-1, where the keywords are listed in alphabetical order.

The default set of inference components for the OWLPrime vocabulary includes the following: `SCOH`, `COMPH`, `DISJH`, `SYMMH`, `INVH`, `SPIH`, `SPOH`, `DOMH`, `RANH`, `EQCH`, `EQPH`, `FPH`, `IFPH`, `SAMH`, `DOM`, `RAN`, `SCO`, `DISJ`, `COMP`, `INV`, `SPO`, `FP`, `IFP`, `SYMM`, `TRANS`, `DIF`, `RDFP14A`, `RDFP14BX`, `RDFP15`, `RDFP16`. However, note the following:

- Component `SAM` is not in this default OWLPrime list, because it tends to generate many new triples for some ontologies.

- Effective with Release 11.2, the native OWL inference engine supports the following new inference components: `CHAIN`, `HASKEY`, `INTERSECT`, `INTERSECTSCOH`, `MBRLST`, `ONEOF`, `PROPDISJH`, `SKOSAXIOMS`, `SNOMED`, `SVFH`, `THINGH`, `THINGSAM`, `UNION`. However, for backward compatibility, the OWLPrime rulebase and any existing rulebases do not include these new components by default; instead, to use these new inference components, you must specify them explicitly, and they are included in Table 15-1 The following example creates an OWLPrime entailment for two OWL ontologies named `LUBM` and `UNIV`. Because of the additional inference components specified, this entailment will include the new semantics introduced in those inference components.

      EXECUTE sem_apis.create_entailment('lubm1000_idx',sem_models('lubm','univ'),
          sem_rulebases('owlprime'), SEM_APIS.REACH_CLOSURE,
          'INTERSECT,INTERSECTSCOH,SVFH,THINGH,THINGSAM,UNION');

Table 15-1 Inferencing Keywords for inf_components_in Parameter

| Keyword           | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAIN             | Captures the property chain semantics defined in OWL 2. Only chains of length 2 are supported. By default, this is included in the `SKOSCORE` rulebase. Subproperty chaining is an OWL 2 feature, and for backward compatibility this component is not by default included in the `OWLPrime` rulebase. (For information about property chain handling, see [Property Chain Handling](simple-knowledge-organizaiton-system-skos.md).) (New as of Release 11.2.) |
| COMPH             | Performs inference based on owl:complementOf assertions and the interaction of owl:complementOf with other language constructs.                                                                                                                                                                                                                                                                                                                                |
| DIF               | Generates owl:differentFrom assertions based on the symmetricity of owl:differentFrom.                                                                                                                                                                                                                                                                                                                                                                         |
| DISJ              | Infers owl:differentFrom relationships at instance level using owl:disjointWith assertions.                                                                                                                                                                                                                                                                                                                                                                    |
| DISJH             | Performs inference based on owl:disjointWith assertions and their interactions with other language constructs.                                                                                                                                                                                                                                                                                                                                                 |
| DOM               | Performs inference based on RDFS2.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| DOMH              | Performs inference based on rdfs:domain assertions and their interactions with other language constructs.                                                                                                                                                                                                                                                                                                                                                      |
| EQCH              | Performs inference that are relevant to owl:equivalentClass.                                                                                                                                                                                                                                                                                                                                                                                                   |
| EQPH              | Performs inference that are relevant to owl:equivalentProperty.                                                                                                                                                                                                                                                                                                                                                                                                |
| FP                | Performs instance-level inference using instances of owl:FunctionalProperty.                                                                                                                                                                                                                                                                                                                                                                                   |
| FPH               | Performs inference using instances of owl:FunctionalProperty.                                                                                                                                                                                                                                                                                                                                                                                                  |
| HASKEY            | Covers the semantics behind "keys" defined in OWL 2. In OWL 2, a collection of properties can be treated as a key to a class expression. For efficiency, the size of the collection must not exceed 3. (New as of Release 11.2.)                                                                                                                                                                                                                               |
| IFP               | Performs instance-level inference using instances of owl:InverseFunctionalProperty.                                                                                                                                                                                                                                                                                                                                                                            |
| IFPH              | Performs inference using instances of owl:InverseFunctionalProperty.                                                                                                                                                                                                                                                                                                                                                                                           |
| INTERSECT         | Handles the core semantics of owl:intersectionOf. For example, if class C is the intersection of classes C1, C2 and C3, then C is a subclass of C1, C2, and C3. In addition, common instances of all C1, C2, and C3 are also instances of C. (New as of Release 11.2.)                                                                                                                                                                                         |
| INTERSECTSCOH     | Handles the fact that an intersection is the maximal common subset. For example, if class C is the intersection of classes C1, C2, and C3, then any common subclass of all C1, C2, and C3 is a subclass of C. (New as of Release 11.2.)                                                                                                                                                                                                                        |
| INV               | Performs instance-level inference using owl:inverseOf assertions.                                                                                                                                                                                                                                                                                                                                                                                              |
| INVH              | Performs inference based on owl:inverseOf assertions and their interactions with other language constructs.                                                                                                                                                                                                                                                                                                                                                    |
| MBRLST            | Captures the semantics that for any resource, every item in the list given as the value of the `skos:memberList` property is also a value of the `skos:member` property. (See S36 in the SKOS detailed specification.) By default, this is included in the `SKOSCORE` rulebase. (New as of Release 11.2.)                                                                                                                                                      |
| ONEOF             | Generates classification assertions based on the definition of the enumeration classes. In OWL, class extensions can be enumerated explicitly with the `owl:oneOf` constructor. (New as of Release 11.2.)                                                                                                                                                                                                                                                      |
| PROPDISJH         | Captures the interaction between `owl:propertyDisjointWith` and `rdfs:subPropertyOf`. By default, this is included in SKOSCORE rulebase. propertyDisjointWith is an OWL 2 feature, and for backward compatibility this component is not by default included in the `OWLPrime` rulebase. (New as of Release 11.2.)                                                                                                                                              |
| RANH              | Performs inference based on `rdfs:range` assertions and their interactions with other language constructs.                                                                                                                                                                                                                                                                                                                                                     |
| RDFP\*            | (The rules corresponding to components with a prefix of RDFP can be found in Completeness, decidability and complexity of entailment for RDF Schema and a semantic extension involving the OWL vocabulary, by H.J. Horst.)                                                                                                                                                                                                                                     |
| RDFS2, ... RDFS13 | RDFS2, RDFS3, RDFS4a, RDFS4b, RDFS5, RDFS6, RDFS7, RDFS8, RDFS9, RDFS10, RDFS11, RDFS12, and RDFS13 are described in Section 7.3 of RDF Semantics ([`http://www.w3.org/TR/rdf-mt/`](http://www.w3.org/TR/rdf-mt/)). Note that many of the RDFS components are not relevant for OWL inference.                                                                                                                                                                  |
| SAM               | Performs inference about individuals based on existing assertions for those individuals and owl:sameAs.                                                                                                                                                                                                                                                                                                                                                        |
| SAMH              | Infers owl:sameAs assertions using transitivity and symmetricity of owl:sameAs.                                                                                                                                                                                                                                                                                                                                                                                |
| SCO               | Performs inference based on RDFS9.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| SCOH              | Generates the subClassOf hierarchy based on existing rdfs:subClassOf assertions. Basically, C1 rdfs:subClassOf C2 and C2 rdfs:subClassOf C3 will infer C1 rdfs:subClassOf C3 based on transitivity. SCOH is also an alias of RDFS11.                                                                                                                                                                                                                           |
| SKOSAXIOMS        | Captures most of the axioms defined in the SKOS detailed specification. By default, this is included in the `SKOSCORE` rulebase. (New as of Release 11.2.)                                                                                                                                                                                                                                                                                                     |
| SNOMED            | Performs inference based on the semantics of the OWL 2 EL profile, which captures the expressiveness of SNOMED CT (Systematized Nomenclature of Medicine - Clinical Terms), which is one of the most expressive and complex medical terminologies. (New as of Release 11.2.)                                                                                                                                                                                   |
| SPIH              | Performs inference based on interactions between rdfs:subPropertyOf and owl:inverseOf assertions.                                                                                                                                                                                                                                                                                                                                                              |
| SPO               | Performs inference based on RDFS7.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| SPOH              | Generates rdfs:subPropertyOf hierarchy based on transitivity of rdfs:subPropertyOf. It is an alias of RDFS5.                                                                                                                                                                                                                                                                                                                                                   |
| SVFH              | Handles the following semantics that involves the interaction between owl:someValuesFrom and rdfs:subClassOf. Consider two existential restriction classes C1 and C2 that both use the same restriction property. Assume further that the owl:someValuesFrom constraint class for C1 is a subclass of that for C2. Then C1 can be inferred as a subclass of C2. (New as of Release 11.2.)                                                                      |
| SYMM              | Performs instance-level inference using instances of owl:SymmetricProperty.                                                                                                                                                                                                                                                                                                                                                                                    |
| SYMH              | Performs inference for properties of type owl:SymmetricProperty.                                                                                                                                                                                                                                                                                                                                                                                               |
| THINGH            | Handles the semantics that any defined OWL class is a subclass of owl:Thing. The consequence of this rule is that instances of all defined OWL classes will become instances of owl:Thing. The size of the inferred graph will very likely be bigger with this component selected. (New as of Release 11.2.)                                                                                                                                                   |
| THINGSAM          | Handles the semantics that instances of owl:Thing are equal to (owl:sameAs) themselves. This component is provided for the convenience of some applications. Note that an application does not have to select this inference component to figure out an individual is equal to itself; this kind of information can easily be built in the application logic. (New as of Release 11.2.)                                                                        |
| TRANS             | Calculates transitive closure for instances of owl:TransitiveProperty.                                                                                                                                                                                                                                                                                                                                                                                         |
| UNION             | Captures the core semantics of the `owl:unionOf` construct. Basically, the `union` class is a superclass of all member classes. For backward compatibility, this component is not by default included in the `OWLPrime` rulebase. (New as of Release 11.2.)                                                                                                                                                                                                    |

To deselect a component, use the component name followed by a minus (-) sign. For example, `SCOH-` deselects inference of the `subClassOf` hierarchy.

For the `options` parameter, you can enable the following options to override the default inferencing behavior:

- `COL_COMPRESS=T` creates temporary, intermediate working tables. This option can reduce the space required for such tables, and can improve the performance of the CREATE_ENTAILMENT operation with large data sets.

  By default `COL_COMPRESS=T` uses the "compress for query level low" setting; however, you can add `CPQH=T` to change to the "compress for query level high" setting.

  **Note:**

  You can specify `COL_COMPRESS=T` only on systems that support Hybrid Columnar Compression (HCC). For information about HCC, see [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md).

- `DEST_MODEL=``<model_name>` specifies, for incremental inference, the destination model to which the `delta_in` model or models are to be added. The specified destination model must be one of the models specified in the `models_in` parameter.

- `DISTANCE=T` generates ancillary distance information that is useful for semantic operators.

- `DOP=``n` specifies the degree of parallelism for parallel inference, which can improve inference performance. For information about parallel inference, see [Using Parallel Inference](owl-concepts.md).

- `ENTAIL_ANYWAY=T` forces OWL inferencing to proceed and reuse existing inferred data (entailment) when the entailment has a valid status. By default, SEM_APIS.CREATE_ENTAILMENT quits immediately if there is already a valid entailment for the combination of models and rulebases.

- `HASH_PART=``n` creates the specified number of hash partitions for internal working tables. (The number must be a power of 2: 2, 4, 8, 16, 32, and so on.) You may want to specify a value if there are many distinct predicates in the semantic data model. In Oracle internal testing on benchmark ontologies, HASH_PART=32 worked well.

- `INC=T` enables incremental inference for the entailment. For information about incremental inference, see [Performing Incremental Inference](owl-concepts.md).

- `LOCAL_NG_INF=T` causes named graph based local inference (NGLI) to be used instead of named graph based global inference (NGGI). For information about NGLI, see [Named Graph Based Local Inference (NGLI)](owl-concepts.md).

- `MODEL_PARTITIONS=``n` overrides the default number of subpartitions in a composite partitioned semantic network and creates the specified number (n) of subpartitions in the final entailment partition in RDF_LINK\$.

- `OPT_SAMEAS=T` uses consolidated `owl:sameAs` entailment for the entailment. If you specify this option, you cannot specify `PROOF=T`. For information about optimizing `owl:sameA`s inference, see [Optimizing owl:sameAs Inference](owl-concepts.md).

- `RAW8=T` uses RAW8 data types for the auxiliary inference tables. This option can improve entailment performance by up to 30% in some cases.

- `PROOF=T` generates proof for inferred triples. Do not specify this option unless you need to; it slows inference performance because it causes more data to be generated. If you specify this option, you cannot specify `OPT_SAMEAS=T`.

- `USER_RULES=T` causes any user-defined rules to be applied. If you specify this option, you cannot specify `PROOF=T` or `DISTANCE=T`, and you must accept the default value for the `passes` parameter.

For the `delta_in` parameter, inference performance is best if the value is small compared to the overall size of those models. In a typical scenario, the best results might be achieved when the delta contains fewer than 10,000 triples; however, some tests have shown significant inference performance improvements with deltas as large as 100,000 triples.

For the `label_gen` parameter, if you want to use the default OLS label generator, specify the appropriate SEM_RDFSA package constant value fromTable 15-2.

Table 15-2 SEM_RDFSA Package Constants for label_gen Parameter

| Constant                      | Description                                                                                                                                                                                                               |
|:------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SEM_RDFSA.LABELGEN_SUBJECT    | Label generator that applies the label associated with the inferred triple's subject as the triple's label.                                                                                                               |
| SEM_RDFSA.LABELGEN_PREDICATE  | Label generator that applies the label associated with the inferred triple's subject as the triple's label.                                                                                                               |
| SEM_RDFSA.LABELGEN_OBJECT     | Label generator that applies the label associated with the inferred triple's subject as the triple's label.                                                                                                               |
| SEM_RDFSA.LABELGEN_RULE       | Label generator that applies the label associated with the rule that directly produced the inferred triple as the triple's label. If you specify this option, you must also specify `PROOF=T` in the `options` parameter. |
| SEM_RDFSA.LABELGEN_DOMINATING | Label generator that computes a dominating label of all the available labels for the triple's components (subject, predicate, object, and rule), and applies it as the label for the inferred triple.                     |

Fine-Grained Access Control (OLS) Considerations

When fine-grained access control is enabled for the entire network using OLS, only a user with FULL access privileges to the associated policy may create an entailment. When OLS is enabled, full access privileges to the OLS policy are granted using the `SA_USER_ADMIN.SET_USER_PRIVS` procedure.

Inferred triples accessed through generated labels might not be same as conceptual triples inferred directly from the user accessible triples and rules. The labels generated using a subset of triple components may be weaker than intended. For example, one of the antecedents for the inferred triple may have a higher label than any of the components of the triple. When the label is generated based on just the triple components, end users with no access to one of the antecedents may still have access to the inferred triple. Even when the antecedents are used for custom label generation, the generated label may be stronger than intended. The inference process is not exhaustive, and information pertaining to any alternate ways of inferring the same triple is not available. So, the label generated using a given set of antecedents may be too strong, because the user with access to all the triples in the alternate path could infer the triple with lower access.

Even when generating a label that dominates all its components and antecedents, the label may not be precise. This is the case when labels considered for dominating relationship have non-overlapping group information. For example, consider two labels `L:C:NY` and `L:C:NH` where L is a level, C is a component and NY and NH are two groups. A simple label that dominates these two labels is `L:C:NY,NH`, and a true supremum for the two labels is `L:C:US`, where US is parent group for both NY and NH. Unfortunately, neither of these two dominating labels is precise for the triple inferred from the triples with first two labels. If `L:C:NY,NH` is used for the inferred triple, a user with membership in either of these groups has access to the inferred triple, whereas the same user does not have access to one of its antecedents. On the other hand, if `L:C:US` is used for the inferred triple, a user with membership in both the groups and not in the US group will not be able to access the inferred triple, whereas that user could infer the triple by directly accessing its components and antecedents.

Because of these unique challenges with inferred triples, extra caution must be taken when choosing or implementing the label generator.

See also the OLS example in the Examples section.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates an entailment named `OWLTST_IDX` using the OWLPrime rulebase, and it causes proof to be generated for inferred triples.

    EXECUTE sem_apis.create_entailment('owltst_idx', sem_models('owltst'), sem_rulebases('OWLPRIME'), SEM_APIS.REACH_CLOSURE, null, 'PROOF=T');

The following example assumes an OLS environment. It creates a rulebase with a rule, and it creates an entailment.

    -- Create an entailment with a rule. --
    exec sdo_rdf_inference.create_entailment('contracts_rb');

    insert into rdfr_contracts_rb values (
      'projectLedBy', '(?x :drivenBy ?y) (?y :hasVP ?z)',  NULL,
      '(?x :isLedBy ?z)',
      SDO_RDF_Aliases(SDO_RDF_Alias('','http://www.myorg.com/pred/')));

    -- Assign sensitivity label for the predicate to be inferred. --
    -- Yhe predicate label may be set globally or it can be assign to --
    -- the one or the models used to infer the data – e.g: CONTRACTS.
    begin
      sem_rdfsa.set_predicate_label(
             model_name   => 'rdf$global',
             predicate    => 'http://www.myorg.com/pred/isLedBy',
             label_string => 'TS:US_SPCL');
    end;
    /

    -- Create index with a specific label generator. --
    begin
      sem_apis.create_entailment(
             entailment_name_in => 'contracts_inf',
             models_in          => SDO_RDF_Models('contracts'),
             rulebases_in       => SDO_RDF_Rulebases('contracts_rb'),
             options            => 'USER_RULES=T',
             label_gen          => sem_rdfsa.LABELGEN_PREDICATE);
    end;
    /

    -- Check for any label exceptions and update them accordingly. --
    update rdfi_contracts_inf set ctxt1 = 1100 where ctxt1 = -1;

    -- The new entailment is now ready for use in SEM_MATCH queries. --

**Parent topic:** SEM_APIS Package Subprograms

### 15.22 SEM_APIS.CREATE_INDEX_ON_SPM_TAB

#### Format

    SEM_APIS.create_index_on_spm_tab (
         index_name         IN VARCHAR2,
         model_name         IN VARCHAR2,
         key_string         IN VARCHAR2 DEFAULT NULL,
         pred_name          IN VARCHAR2 DEFAULT NULL,
         tablespace_name    IN DBMS_ID DEFAULT NULL,
         degree             IN NUMBER DEFAULT NULL,
         prefixes           IN VARCHAR2 DEFAULT NULL,
         prefix_length      IN NUMBER DEFAULT NULL,
         options            IN VARCHAR2 DEFAULT NULL,
         network_owner      IN DBMS_ID DEFAULT NULL,
         network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a unique or a nonunique B-tree index on Subject-Predicate Matrix table.

#### Parameters

index_name
Name of the index.

model_name
Source of the data used to build the index.

key_string
Index key is composed of subject ID, graph ID, and predicates and their corresponding value components.

The following codes are used for representing index keys:

- `G`: graph ID
- `S`: subject ID
- `VP`: value prefix
- `VS`: value suffix
- `VT`: value type
- `LT`: literal type
- `LA`: language type
- `VN`: order number
- `VD`: order date
- `‘S’`: can be used only once. If it is specified, a unique index is created. Otherwise, a nonunique index is created.
- `‘+’`: is used to represent the associated predicate. For example, in the following key string `‘<p1> +G G+ <p2>,’`, the first `G` is associated with `<p1>` whereas the second `G` is associated with `<p2>`.
- `‘*’`: is used to represent all corresponding IDs associated with all predicates. For example, in the following key string `‘G* <p1> <p2>,’`, the index key will have all graph ID’s corresponding to` <p1> and <p2>`.

pred_name
Identifies an MVP table on which the index is built.

tablespace_name
Destination tablespace for the index.

degree
Degree of parallelism to use for create index operation.

prefixes
SPARQL preamble style string.

For example, `‘PREFIX bsbm: <http://www4.wiwiss.fu-berlin.de/bizer/bsbm/v01/vocabulary/> PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>‘`

prefix_length
Number of columns to be compressed.

options
String specifying any options to use during the create index operation. Supported options are:

- PCN_NAME= \<name\> - index is created on the named PCN table.
- SVP_NAME= \<name\> - index created on the named SVP table.
- CREATE_ANYWAY=T - the index is replaced.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

#### Examples

The following example creates the index `‘idx1’` on model `‘berlin’`.

    EXECUTE sem_apis.create_index_on_spm_tab('idx1', 'berlin',
            'bsbm:productPropertyNumeric1 +G G+ bsbm:productPropertyNumeric2 S',
             prefixes=>' PREFIX bsbm: <http://www4.wiwiss.fu-berlin.de/bizer/bsbm/v01/vocabulary/>',
             network_owner=>'rdfuser', network_name=>'mynet');

**Parent topic:** SEM_APIS Package Subprograms

### 15.23 SEM_APIS.CREATE_PG_RDFVIEW

#### Format

    SEM_APIS.CREATE_PG_RDFVIEW(
         model_name      IN VARCHAR2,
         pg_name         IN VARCHAR2,
         tsblespace_name IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

or

    SEM_APIS.CREATE_PG_RDFVIEW(
         model_name      IN VARCHAR2,
         pg_name         IN VARCHAR2,
         tsblespace_name IN VARCHAR2 DEFAULT NULL,
         pg_stag_tab     IN VARCHAR2,
         pg_edge_kv_tab  IN VARCHAR2,
         pg_node_kv_tab  IN VARCHAR2,
         pg_edge_tab     IN VARCHAR2,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 default NULL);

#### Description

Creates an RDF ciew model for a property graph stored in Oracle Database.

#### Parameters

model_name
Name of the RDF view model to create.

pg_name
Name of the property graph for the RDF view.

tablespace_name
Destination tablespace for the RDF view model and the R2RML staging table.

pg_stag_tab
Name of the staging table. (See the Usage Notes for more information.)

pg_edge_kv_tab
Name of the table storing edge properties

 pg_node_kv_tab
Name of the table storing node properties.

pg_edge_tab
Name of the table storing distinct edges.

options
String specifying options for index creation using the form OPTION_NAME=option_value. Supported options are:

- SUB_K=N, SUB_EL=N (use a substring of N characters for property key name or edge label)

- GT_TABLE=T (assume a populated GT\$ table)

- RECREATE=T (re-create an existing property graph RDF view model)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure has two formats. The first format has minimal input that uses default names for the staging table and each table in the property graph schema, and that creates the staging table automatically if it does not exist. The second format lets you specify custom table names for the staging table and the property graph tables.

If you use the second format, the staging table must already exist. If the staging table is not empty, you must specify the `RECREATE=T` option. (With the second format, if the staging table is not empty and if you do not specify the `RECREATE=T` option, then an error is generated.)

For more information, see [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates the RDF view M1 for the property graph G1 in tablespace MY_TBS, and it specifies a populated distinct edges table.

    EXECUTE SEM_APIS.CREATE_PG_RDFVIEW('M1', 'G1', 'MY_TBS', ' GT_TABLE=T ');

The following example creates the RDF view M1 for the property graph G1 in tablespace MY_TBS with property graph tables MY_EDGE_KV_TAB, MY_NODE_KV_TAB, and MY_EDGE_TAB. and staging table MY_STAB.

    EXECUTE SEM_APIS.CREATE_PG_RDFVIEW('M1', 'G1', 'MY_TBS', 'MY_STAB', 'MY_EDGE_KV_TAB', 'MY_NODE_KV_TAB', 'MY_EDGE_TAB');

**Parent topic:** SEM_APIS Package Subprograms

### 15.24 SEM_APIS.CREATE_RDFVIEW_MODEL

#### Format

    SEM_APIS.CREATE_RDFVIEW_MODEL(
         model_name          IN VARCHAR2,
         tables              IN SYS.ODCIVarchar2List,
         prefix              IN VARCHAR2 DEFAULT NULL,
         r2rml_table_owner   IN VARCHAR2 DEFAULT NULL,
         r2rml_table_name    IN VARCHAR2 DEFAULT NULL,
         schema_table_owner  IN VARCHAR2 DEFAULT NULL,
         schema_table_name   IN VARCHAR2 DEFAULT NULL,
         options             IN VARCHAR2 DEFAULT NULL,
         r2rml_string        IN CLOB     DEFAULT NULL,
         r2rml_string_fmt    IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Creates an RDF view using direct mapping for the specified list of tables or views or using R2RML mapping.

#### Parameters

model_name
Name of the RDF view to be created.

tables
List of tables or views that are the sources of relational data for the RDF view to be created using direct mapping. This parameter must be null if you want to use R2RML mapping.

prefix
Base prefix to be added at the beginning of the URIs in the RDF view.

r2rml_table_owner
For R2ML mapping, this parameter is required and specifies the name of the schema that owns the staging table that holds the R2RML mapping (in N-triple format) to be used for creating the RDF view.

For direct mapping, this parameter is optional and specifies the name of the schema that owns the staging table into which the R2RML mapping (in N-triple format) generated from the direct mapping will be stored.

r2rml_table_name
For R2ML mapping, this parameter is required and specifies the name of the staging table that holds the R2RML mapping (in N-triple format) to be used for creating the RDF view.

For direct mapping, this parameter is optional and specifies the name of the staging table into which the R2RML mapping (in N-triple format) generated from the direct mapping will be stored.

schema_table_owner
Name of the schema that owns the staging table where the RDF schema generated for the RDF view will be stored.

schema_table_name
Name of the staging table where the RDF schema generated for the RDF view will be stored.

options
For direct mapping, you can optionally specify any combination (including none) of the following:

- `CONFORMANCE=T` suppresses some of the information that would otherwise get included by default, including use of database constraint names and schema-qualified table or view names for constructing RDF predicate names.

- `GENERATE_ONLY=T` only generates the R2RML mapping for the specified tables and stores it in the specified `r2rml_table_name`, but the underlying RDF view model is not created. If you specify this option, the `r2rml_table_name` parameter must not be null.

- `KEY_BASED_REF_PROPERTY=T` uses the foreign key column names to construct the RDF predicate name. If this option is not specified, then the database constraint name is used for constructing the RDF predicate name.

  For direct mapping, RDF predicate names are derived from the corresponding database names; therefore, preserving the name for the foreign key constraint is the default behavior.

  For an example that uses `KEY_BASED_REF_PROPERTY=T` , see [Example 10-1](rdf-views.md) in [Creating an RDF View with Direct Mapping](rdf-views.md).

- `SCALAR_COLUMNS_ONLY=T` generates the R2RML mapping for only the scalar columns in the specified tables or views. Other non-scalar columns in the tables or views are ignored. Without this option, if you attempt to create a direct mapping on a table with user-defined types or LOB columns, an error is raised.

r2rml_string
An R2RML mapping string in Turtle or N-Triple format to be used for creating the RDF view.

r2rml_string_fmt
The format of the R2RML mapping string specified in `r2rml_string`. Possible values are `TURTLE` and `N-TRIPLE`.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must grant the `SELECT` and `INSERT` privileges on `r2rml_table_name` and `schema_table_name` to `MDSYS`.

For more information about RDF views, see [RDF Views: Relational Data as RDF](rdf-views.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates an RDF view using direct mapping for tables EMP and DEPT. The prefix used for the URIs is `http://empdb/`.

    BEGIN
      sem_apis.create_rdfview_model(
        model_name => 'empdb_model_direct',
        tables => sem_models('EMP', 'DEPT'),
        prefix => 'http://empdb/',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );
    END;
    /

The following example creates an RDF view using R2RML mapping as specified by the RDF triples in the staging table SCOTT.R2RTAB.

    BEGIN
      sem_apis.create_rdfview_model(
        model_name => 'empdb_model_R2RML',
        tables => NULL,
        r2rml_table_owner => 'SCOTT',
        r2rml_table_name => 'R2RTAB',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );
    END;
    /

The following example creates an RDF view using an R2RML mapping specified directly as a string.

    DECLARE
      r2rmlStr CLOB;
    BEGIN

      r2rmlStr :=
       '@prefix rr: <http://www.w3.org/ns/r2rml#>. '||
       '@prefix xsd: <http://www.w3.org/2001/XMLSchema#>. '||
       '@prefix ex: <http://example.com/ns#>. '||'

        ex:TriplesMap_Emp
            rr:logicalTable [ rr:tableName "EMP" ];
            rr:subjectMap [
                rr:template "http://data.example.com/employee/{EMPNO}";
                rr:class ex:Employee;
            ];
            rr:predicateObjectMap [
                rr:predicate ex:empNum;
                rr:objectMap [ rr:column "EMPNO" ; rr:datatype xsd:integer ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:empName;
                rr:objectMap [ rr:column "ENAME" ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:jobType;
                rr:objectMap [ rr:column "JOB" ];
            ];
            rr:predicateObjectMap [
                rr:predicate ex:worksForDeptNum;
                rr:objectMap [ rr:column "DEPTNO" ; rr:dataType xsd:integer ];
            ].';

      sem_apis.create_rdfview_model(
        model_name => 'empdb_model_R2RML',
        tables => NULL,
        r2rml_string => r2rmlStr,
        r2rml_string_fmt => 'TURTLE',
        network_owner=>'RDFUSER',
        network_name=>'NET1'
      );

    END;
    /

The following example creates an RDF view using direct mapping as specified by the RDF triples in the tables EMP and DEPT in the schema-private network owned by RDFUSER. It also selects information about employees who work at the Boston location.

    BEGIN
      sem_apis.create_rdfview_model(
      model_name => 'empdb_model',
      tables => SYS.ODCIVarchar2List('EMP', 'DEPT'),
      prefix => 'http://empdb/',
      options => 'KEY_BASED_REF_PROPERTY=T',
      network_owner=>'RDFUSER',
      network_name=>'NET1'
      );
    END;
    /

    SELECT e.empno FROM emp e, dept d WHERE e.deptno = d.deptno AND d.loc = 'Boston';

    SELECT emp
    FROM TABLE(SEM_MATCH('{?emp emp:ref-DEPTNO ?dept . ?dept dept:LOC "Boston"}',SEM_Models('empdb_model'),NULL,SEM_ALIASES(
    SEM_ALIAS('dept','http://empdb/RDFUSER.DEPT#'),SEM_ALIAS('emp','http://empdb/RDFUSER.EMP#')),null,null,null,null,null,'RDF_USER','NET1'));

**Parent topic:** SEM_APIS Package Subprograms

### 15.25 SEM_APIS.CREATE_RULEBASE

#### Format

    SEM_APIS.CREATE_RULEBASE(
         rulebase_name  IN VARCHAR2),
         options        IN VARCHAR2 DEFAULT NULL),
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a rulebase.

#### Parameters

rulebase_name
Name of the rulebase.

options
(Not currently used.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure creates a user-defined rulebase. After creating the rulebase, you can add rules to it. To cause the rules in the rulebase to be applied in a query of RDF data, you can specify the rulebase in the call to the SEM_MATCH table function.

Rules and rulebases are explained in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md). The SEM_MATCH table function is described in [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md),

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a rulebase named family_rb. (It is an excerpt from [Example 1-122](rdf-semantic-graph-overview.md) in [Example: Family Information](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.CREATE_RULEBASE('family_rb');

**Parent topic:** SEM_APIS Package Subprograms

### 15.26 SEM_APIS.CREATE_SEM_MODEL

#### Format

    SEM_APIS.CREATE_SEM_MODEL(
         model_name       IN VARCHAR2,
         table_name       IN VARCHAR2,
         column_name      IN VARCHAR2,
         model_tablespace IN VARCHAR2 DEFAULT NULL,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a semantic technology model.

#### Parameters

model_name
Name of the model.

table_name
Name of the table to hold references to semantic technology data for this model.

This parameter must be `NULL` for a schema-private network.

column_name
Name of the column of type SDO_RDF_TRIPLE_S in `table_name`.

This parameter must be `NULL` for a schema-private network.

model_tablespace
Name of the tablespace for the tables and other database objects used by Oracle to support this model. The default value is the tablespace that was specified in the call to the SEM_APIS.CREATE_SEM_NETWORK procedure.

options
An optional quoted string with one or more of the following model creation options:

- `COMPRESS=CSCQH` uses COLUMN STORE COMPRESS FOR QUERY HIGH on the RDF_LINK\$ partition for the model.

- `COMPRESS=CSCQL` uses COLUMN STORE COMPRESS FOR QUERY LOW on the RDF_LINK\$ partition for the model.

- `COMPRESS=RSCA` uses ROW STORE COMPRESS ADVANCED on the RDF_LINK\$ partition for the model.

- `COMPRESS=RSCB` uses ROW STORE COMPRESS BASIC on the RDF_LINK\$ partition for the model.

- `MODEL_PARTITIONS=``n` overrides the default number of subpartitions in a composite partitioned semantic network and creates the specified number (n) of subpartitions in the RDF_LINK\$ partition for the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an MDSYS-owned network, you must create the table to hold references to semantic technology data before calling this procedure to create the semantic technology model. However, this table creation step is not required when using a schema-private network. For more information, see [Quick Start for Using Semantic Data](getting-started-semantic-data-mdsys-owned-network.md).

This procedure adds the model to the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

This procedure is the only supported way to create a model. Do not use SQL INSERT statements with the SEM_MODEL\$ view.

To delete a model, use the SEM_APIS.DROP_SEM_MODEL procedure.

The options `COMPRESS=CSCQH`, `COMPRESS=CSCQL`, and `COMPRESS=RSCA` should be used only if you have the appropriate licenses.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a semantic technology model named `articles` in the schema-private network. (This example is an excerpt from [Example 1-121](rdf-semantic-graph-overview.md) in [Example: Journal Article Information](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.CREATE_SEM_MODEL('articles', NULL, NULL, network_owner=>'RDFUSER', network_name=>'NET1');

As part of this operation, a new updatable view, RDFUSER.NET1#RDFT_articles, gets created automatically. You can use this view for any SQL DML statements affecting the data. The following example uses the SDO_RDF_TRIPLE_S constructor to insert data into the model:

    INSERT INTO RDFUSER.NET1#RDFT_articles VALUES (
      SDO_RDF_TRIPLE_S ('articles','<http://nature.example.com/Article1>',
        '<http://purl.org/dc/elements/1.1/creator>',
        '"Jane Smith"',
        'RDFUSER',
        'NET1'));

**Parent topic:** SEM_APIS Package Subprograms

### 15.27 SEM_APIS.CREATE_SEM_NETWORK

#### Format

    SEM_APIS.CREATE_SEM_NETWORK(
         tablespace_name  IN VARCHAR2,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates structures for persistent storage of semantic data.

#### Parameters

tablespace_name
Name of the tablespace to be used for tables created by this procedure. This tablespace will be the default for all models that you create, although you can override the default when you create a model by specifying the `model_tablespace` parameter in the call to the SEM_APIS.CREATE_SEM_MODEL procedure.

options
An optional quoted string with one or more of the following network creation options:

- `COMPRESS=CSCQH` uses COLUMN STORE COMPRESS FOR QUERY HIGH on the RDF_LINK\$ and RDF_VALUE\$ tables.

- `COMPRESS=CSCQL` uses COLUMN STORE COMPRESS FOR QUERY LOW on the RDF_LINK\$ and RDF_VALUE\$ tables.

- `COMPRESS=RSCA` uses ROW STORE COMPRESS ADVANCED on the RDF_LINK\$ and RDF_VALUE\$ tables.

- `COMPRESS=RSCB` uses ROW STORE COMPRESS BASIC on the RDF_LINK\$ and RDF_VALUE\$ tables. This is the default compression level.

- `MODEL_PARTITIONING=BY_HASH_P` uses list-hash composite partitioning to partition RDF_LINK\$ by model ID and further subpartition each model by a hash of the predicate ID.

- `MODEL_PARTITIONS=``n` sets the default number (n) of subpartitions to use for each model. This value should be greater than 1. A default value of 32 will be used when `MODEL_PARTITIONS` is omitted or set to a value less than or equal to 1. This option is used in conjunction with `MODEL_PARTITIONING=BY_HASH_P`.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure creates system tables and other database objects used for semantic technology support.

You should create a tablespace for the semantic technology system tables and specify the tablespace name in the call to this procedure. (You should not specify the `SYSTEM` tablespace.) The size needed for the tablespace that you create will depend on the amount of semantic technology data you plan to store.

You must connect to the database as a user with DBA privileges or as the intended network owner in order to call this procedure, and you should call the procedure only once for the database.

To drop these structures for persistent storage of semantic data, you must connect as a user with DBA privileges or as the owner of the schema-private network, and call the SEM_APIS.DROP_SEM_NETWORK procedure.

The options `COMPRESS=CSCQH`, `COMPRESS=CSCQL`, and `COMPRESS=RSCA` should be used only if you have the appropriate licenses.

After the semantic network is created, a row in the RDF_PARAMETER table with NAMESPACE = 'NETWORK' and ATTRIBUTE = 'COMPRESSION' will indicate the type of compression used for the semantic network.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a tablespace for semantic technology system tables and creates structures for persistent storage of semantic data in this tablespace. Advanced compression is used for the semantic network.

    CREATE TABLESPACE rdf_tblspace
     DATAFILE '/oradata/orcl/rdf_tblspace.dat' SIZE 1024M REUSE
     AUTOEXTEND ON NEXT 256M MAXSIZE UNLIMITED
     SEGMENT SPACE MANAGEMENT AUTO;
    . . .
    EXECUTE SEM_APIS.CREATE_SEM_NETWORK('rdf_tblspace', options=>'MODEL_PARTITIONING=BY_HASH_P MODEL_PARTITIONS=16');

**Parent topic:** SEM_APIS Package Subprograms

### 15.28 SEM_APIS.CREATE_SOURCE_EXTERNAL_TABLE

#### Format

    SEM_APIS.CREATE_SOURCE_EXTERNAL_TABLE(
         source_table   IN VARCHAR2,
         def_directory  IN VARCHAR2,
         log_directory  IN VARCHAR2 DEFAULT NULL,
         bad_directory  IN VARCHAR2 DEFAULT NULL,
         log_file       IN VARCHAR2 DEFAULT NULL,
         bad_file       IN VARCHAR2 DEFAULT NULL,
         parallel       IN INTEGER DEFAULT NULL,
         source_table_owner IN VARCHAR2 DEFAULT NULL,
         flags          IN VARCHAR2 DEFAULT NULL);

#### Description

Creates an external table to map an N-Triple or N-Quad format file into a table.

#### Parameters

source_table
Name of the external table to be created.

def_directory
Database directory where the input files are located. To load from this staging table, you must have READ privilege on this directory.

log_directory
Database directory where the log files will be generated when loading from the external table. If not specified, the value of the `def_directory` parameter is used. When loading from the external table, you must have WRITE privilege on this directory.

bad_directory
Database directory where the bad files will be generated when loading from the external table. If not specified, the value of the `def_directory` parameter is used. When loading from the external table, you must have WRITE privilege on this directory.

log_file
Name of the log file. If not specified, the name will be generated automatically during a load operation.

bad_file
Name of the bad file. If not specified, the name will be generated automatically during a load operation.

parallel
Degree of parallelism to associate with the external table being created.

source_table_owner
Owner for the external table being created. If not specified, the invoker becomes the owner.

flags
(Reserved for future use)

#### Usage Notes

For more information and an example, see [Loading N-Quad Format Data into a Staging Table Using an External Table](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a source external table. (This example is an excerpt from [Example 1-100](rdf-semantic-graph-overview.md) in [Loading N-Quad Format Data into a Staging Table Using an External Table](rdf-semantic-graph-overview.md).)

    BEGIN
      sem_apis.create_source_external_table(
        source_table    => 'stage_table_source'
       ,def_directory   => 'DATA_DIR'
       ,bad_file        => 'CLOBrows.bad'
       );
    END;

**Parent topic:** SEM_APIS Package Subprograms

### 15.29 SEM_APIS.CREATE_SPARQL_UPDATE_TABLES

#### Format

    SEM_APIS.CREATE_SPARQL_UPDATE_TABLES();

#### Description

Creates global temporary tables in the caller’s schema for use with SPARQL Update operations.

#### Parameters

None.

#### Usage Notes

Invoking SEM_APIS.UPDATE_MODEL with `STREAMING=F`, `FORCE_BULK=T`, or `DEL_AS_INS=T` option requires that the following temporary tables exist in the caller’s schema: RDF_UPD_DEL\$, RDF_UPD_INS\$, and RDF_UPD_INS_CLOB\$. These tables are created with the following definitions:

      CREATE GLOBAL TEMPORARY TABLE RDF_UPD_DEL$ (
        RDF$STC_GRAPH VARCHAR2(4000),
        RDF$STC_SUB   VARCHAR2(4000),
        RDF$STC_PRED  VARCHAR2(4000),
        RDF$STC_OBJ   VARCHAR2(4000),
        RDF$STC_CLOB  CLOB
      ) ON COMMIT PRESERVE ROWS';
      CREATE GLOBAL TEMPORARY TABLE RDF_UPD_INS$ (
        RDF$STC_GRAPH VARCHAR2(4000),
        RDF$STC_SUB   VARCHAR2(4000),
        RDF$STC_PRED  VARCHAR2(4000),
        RDF$STC_OBJ   VARCHAR2(4000)
      ) ON COMMIT PRESERVE ROWS';
      CREATE GLOBAL TEMPORARY TABLE RDF_UPD_INS_CLOB$ (
        RDF$STC_GRAPH VARCHAR2(4000),
        RDF$STC_SUB   VARCHAR2(4000),
        RDF$STC_PRED  VARCHAR2(4000),
        RDF$STC_OBJ   VARCHAR2(4000),
        RDF$STC_CLOB  CLOB
      ) ON COMMIT PRESERVE ROWS';

If you need to drop these tables, use the SEM_APIS.DROP_SPARQL_UPDATE_TABLES.

For more information, see [Support for SPARQL Update Operations on a Semantic Model](rdf-semantic-graph-overview.md).

#### Examples

The following example creates the necessary global temporary tables in the caller’s schema for use with SPARQL Update operations.

    EXECUTE SEM_APIS.CREATE_SPARQL_UPDATE_TABLES;

**Parent topic:** SEM_APIS Package Subprograms

### 15.30 SEM_APIS.CREATE_VIRTUAL_MODEL

#### Format

    SEM_APIS.CREATE_VIRTUAL_MODEL(
         vm_name       IN VARCHAR2,
         models        IN SEM_MODELS,
         rulebases     IN SEM_RULEBASES DEFAULT NULL,
         options       IN VARCHAR2 DEFAULT NULL,
         entailments   IN SEM_ENTAILMENTS DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a virtual model containing the specified semantic models and/or entailments. Entailments can be specified in one of the following ways:

- By specifying one or more models and one or more rulebases. In this case, a virtual model will be created using the single entailment that corresponds to the exact combination of models and rulebases specified. An error is raised if no such entailment exists.

- By specifying zero or more models and one or more entailments. In this case, the contents of the models and entailments will be combined regardless of their relationship.

The first method ensures a sound and complete dataset, whereas the second method relaxes the sound and complete constraints for more flexibility.

#### Parameters

vm_name
Name of the virtual model to be created.

models
One or more semantic model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`. If this parameter is null, no models are included in the virtual model definition.

rulebases
One or more rulebase names. Its data type is SEM_RULEBASES, which has the following definition: `TABLE OF VARCHAR2(25)`. If this parameter is null, no rulebases are included in the virtual model definition. Rules and rulebases are explained in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md).

If you specify this parameter, you cannot also specify the `entailments` parameter.

options
Options for creation:

- `PXN=T` forces a UNION ALL-based view definition for the virtual model. This is the default for virtual models with 16 or fewer components.

- `PXN=F` forces an IN LIST-based view definition for the virtual model. This is the default for virtual models with more than 16 components.

- `PXN=F INMEMORY=T` (in combination) let you to create an in-memory virtual model.

  If you specify `INMEMORY=T` but not `PXN=F`, then the in-memory virtual columns are created, but the performance will suffer. If you do not specify `INMEMORY=T`, the virtual model is not created in-memory. (See also [Using In-Memory Virtual Columns with RDF](rdf-semantic-graph-overview.md).)

- `REPLACE=T` lets you to replace a virtual model without dropping it. (Using this option is analogous to using CREATE OR REPLACE VIEW with a view.)

entailments
One or more entailment names. Its data type is SEM_ENTAILMENTS, which has the following definition: `TABLE OF VARCHAR2(25)`. If this parameter is null, no entailments are included in the virtual model definition. Entailments are explained in [Using OWL Inferencing](owl-concepts.md).

If you specify this parameter, you cannot also specify the `rulebases` parameter.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of virtual models, including usage information, see [Virtual Models](rdf-semantic-graph-overview.md).

An entailment must exist for each specified combination of semantic model and rulebase.

To create a virtual model, you must either be (A) the owner of each specified model and any corresponding entailments, or (B) a user with DBA privileges.

To replace a virtual model, you must be the owner of the virtual model or a user with DBA privileges.

The option `INMEMORY=T` should be used only if you have the appropriate licenses.

This procedure creates views with names in the following format:

- SEMV\_vm_name, which corresponds to a UNION ALL of the triples in each model and entailment. This view may contain duplicates.

- SEMU\_vm_name, which corresponds to a UNION of the triples in each model and entailment. This view will not contain duplicates (thus, the U in SEMU indicates unique).

To use the example in [Virtual Models](rdf-semantic-graph-overview.md) of a virtual model vm1 created from models m1, m2, m3, and with an entailment created for m1, m2 ,and m3 using the OWLPrime rulebase, this procedure will create the following two views (assuming that m1, m2, and m3, and the OWLPRIME entailment have internal model_id values 1, 2, 3, 4):

    CREATE VIEW MDSYS.SEMV_VM1 AS
      SELECT p_value_id, start_node_id, canon_end_node_id, end_node_id, g_id, model_id
      FROM MDSYS.rdf_link$ partition (MODEL_1)
    UNION ALL
      SELECT p_value_id, start_node_id, canon_end_node_id, end_node_id, g_id, model_id
      FROM MDSYS.rdf_link$ partition (MODEL_2)
    UNION ALL
      SELECT p_value_id, start_node_id, canon_end_node_id, end_node_id, g_id, model_id
      FROM MDSYS.rdf_link$ partition (MODEL_3)
    UNION ALL
      SELECT p_value_id, start_node_id, canon_end_node_id, end_node_id, g_id, model_id
      FROM MDSYS.rdf_link$ partition (MODEL_4);

    CREATE VIEW MDSYS.SEMU_VM1 AS
      SELECT p_value_id, start_node_id, canon_end_node_id, MIN(end_node_id) end_node_id, g_id, MIN(model_id) model_id
      FROM MDSYS.rdf_link$
      WHERE model_id in (1, 2, 3, 4)
      GROUP BY p_value_id, start_node_id, canon_end_node_id, g_id;

The user that invokes this procedure will be the owner of the virtual model and will have SELECT WITH GRANT privileges on the SEMU\_vm_name and SEMV\_vm_name views. To query the corresponding virtual model, a user must have select privileges on these views.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a virtual model named `VM1`.

    EXECUTE sem_apis.create_virtual_model('VM1', sem_models('model_1', 'model_2'), sem_rulebases('OWLPRIME'));

The following example creates a virtual model named `VM1` using the relaxed entailment specification.

    EXECUTE sem_apis.create_virtual_model('VM1', models=>sem_models('model_1', 'model_2'), entailments=>sem_entailments('entailment1','entailment2'));

The following example effectively redefines virtual model `VM1` by using the `REPLACE=T` option.

    EXECUTE sem_apis.create_virtual_model('VM1', models=>sem_models('model_1', 'model_2'), entailments=>sem_entailments('entailment1'), options=>'REPLACE=T');

**Parent topic:** SEM_APIS Package Subprograms

### 15.31 SEM_APIS.DELETE_ENTAILMENT_STATS

#### Format

    SEM_APIS.DELETE_ENTAILMENT_STATS (
         entailment_name  IN VARCHAR2,
         cascade_parts    IN BOOLEAN DEFAULT TRUE,
         cascade_columns  IN BOOLEAN DEFAULT TRUE,
         cascade_indexes  IN BOOLEAN DEFAULT TRUE,
         no_invalidate    IN BOOLEAN DEFAULT DBMS_STATS.AUTO_INVALIDATE,
         force            IN BOOLEAN DEFAULT FALSE,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes statistics for a specified entailment.

#### Parameters

entailment_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.DELETE_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to entailment statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes statistics for an entailment named `OWLTST_IDX`.

    EXECUTE SEM_APIS.DELETE_ENTAILMENT_STATS('owltst_idx');

**Parent topic:** SEM_APIS Package Subprograms

### 15.32 SEM_APIS.DELETE_MODEL_STATS

#### Format

    SEM_APIS.DELETE_MODEL_STATS (
         model_name       IN VARCHAR2,
         cascade_parts    IN BOOLEAN DEFAULT TRUE,
         cascade_columns  IN BOOLEAN DEFAULT TRUE,
         cascade_indexes  IN BOOLEAN DEFAULT TRUE,
         no_invalidate    IN BOOLEAN DEFAULT DBMS_STATS.AUTO_INVALIDATE,
         force            IN BOOLEAN DEFAULT FALSE,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes statistics for a specified model.

#### Parameters

model_name
Name of the model.

(other parameters)
See the parameter explanations for the [DBMS_STATS.DELETE_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to model statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Only the model owner or a users with DBA privileges can execute this procedure.

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes statistics for a model named `FAMILY`.

    EXECUTE SEM_APIS.DELETE_MODEL_STATS('family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.33 SEM_APIS.DISABLE_CHANGE_TRACKING

#### Format

    SEM_APIS.DISABLE_CHANGE_TRACKING(
         models_in     IN SEM_MODELS,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Disables change tracking for a specified set of models.

#### Parameters

models_in
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Disabling change tracking on a model automatically disables incremental inference on all entailment that use the model.

To use this procedure, you must be the owner of the specified model, and incremental inference must have been previously enabled.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example disables change tracking for the `family` model.

    EXECUTE sem_apis.disable_change_tracking(sem_models('family'));

**Parent topic:** SEM_APIS Package Subprograms

### 15.34 SEM_APIS.DISABLE_INC_INFERENCE

#### Format

    SEM_APIS.DISABLE_INC_INFERENCE(
         entailment_name IN VARCHAR2,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Disables incremental inference for a specified entailment (rules index).

#### Parameters

entailment_name
Name of the entailment for which to disable incremental inference.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must be the owner of the specified entailment, and incremental inference must have been previously enabled by the SEM_APIS.ENABLE_INC_INFERENCE procedure.

Calling this procedure automatically disables change tracking for all models owned by the invoking user that were having changes tracked only because of this particular inference.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables incremental inference for the entailment named `RDFS_RIX_FAMILY`.

    EXECUTE sem_apis.disable_inc_inference('rdfs_rix_family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.35 SEM_APIS.DISABLE_INMEMORY

#### Format

    SEM_APIS.DISABLE_INMEMORY(
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Disables in-memory population of RDF data in a semantic network.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example disables in-memory population of RDF data in the semantic network.

    EXECUTE SEM_APIS.DISABLE_INMEMORY;

**Parent topic:** SEM_APIS Package Subprograms

### 15.36 SEM_APIS.DISABLE_INMEMORY_FOR_ENT

#### Format

    SEM_APIS.DISABLE_INMEMORY_FOR_ENT(
         entailment_name IN VARCHAR2,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Disables in-memory population of RDF data for an entailment in a semantic network.

#### Parameters

entailment_name
Name of the entailment.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example disables in-memory population of RDF data for entailment RIDX1 in the MDSYS-owned semantic network.

    EXECUTE SEM_APIS.DISABLE_INMEMORY_FOR_ENT('RIDX1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.37 SEM_APIS.DISABLE_INMEMORY_FOR_MODEL

#### Format

    SEM_APIS.DISABLE_INMEMORY_FOR_MODEL(
         model_name    IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Disables in-memory population of RDF data for a model in a semantic network.

#### Parameters

model_name
Name of the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables in-memory population of RDF data for model M1 in the MDSYS-owned semantic network.

    EXECUTE SEM_APIS.DISABLE_INMEMORY_FOR_MODEL('M1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.38 SEM_APIS.DISABLE_NETWORK_SHARING

#### Format

    SEM_APIS.DISABLE_NETWORK_SHARING(
         network_owner IN VARCHAR2,
         network_name  IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL);

#### Description

Disables sharing of a semantic network.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

options
(Reserved for future use)

#### Usage Notes

To use this procedure, you must have DBA privileges or be the owner of the specified network.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables sharing of the `mynetwork` schema-private network owned by database user `scott`.

    EXECUTE SEM_APIS.DISABLE_NETWORK_SHARING('scott', 'mynetwork');

**Parent topic:** SEM_APIS Package Subprograms

### 15.39 SEM_APIS.DROP_DATATYPE_INDEX

#### Format

    SEM_APIS.DROP_DATATYPE_INDEX(
         datatype      IN VARCHAR2,
         force_drop    IN BOOLEAN default FALSE,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) an existing data type index.

#### Parameters

datatype
URI of the data type for the index to drop.

force_drop
`TRUE` forces the index to be dropped if an error occurs during the processing of the statement; `FALSE` (the default) does not drop the index if an error occurs during the processing of the statement.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges to call this procedure.

For an explanation of data type indexes, see [Using Data Type Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the data type index for `xsd:string` typed literals and plain literals.

    EXECUTE SEM_APIS.DROP_DATATYPE_INDEX('http://www.w3.org/2001/XMLSchema#string');

**Parent topic:** SEM_APIS Package Subprograms

### 15.40 SEM_APIS.DROP_ENTAILMENT

#### Format

    SEM_APIS.DROP_ENTAILMENT(
         entailment_name_in IN VARCHAR2,
         named_g_in         IN SEM_GRAPHS DEFAULT NULL,
         dop                IN INT DEFAULT 1,
         network_owner      IN VARCHAR2 DEFAULT NULL,
         network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) an entailment (rules index).

#### Parameters

entailment_name_in
Name of the entailment to be deleted.

named_g_in
Causes only the triples with the specified graph names in the entailment to be deleted. A null value (the default) drops the entire entailment.

For example, `named_g_in => sem_graphs('<urn:G1>','<urn:G2>')` drops only the triples in entailment with graph names `G1` and `G2`; the rest of the entailment graph is not dropped.

dop
Degree of parallelism for a parallel execution of triple deletion. Applies only if the `named_g_in` parameter is not null.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You can use this procedure to delete an entailment that you created using the SEM_APIS.CREATE_ENTAILMENT procedure.

If you drop only a subset of the entailment with specified named graphs (that is, when `named_g_in` is not null) on an entailment with a `VALID` or `INCOMPLETE` status, then the resulting status of the entailment after the drop is set to `INCOMPLETE`.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes a entailment named `OWLTST_IDX`.

    EXECUTE sem_apis.drop_entailment('owltst_idx');

The following example deletes only inferred triples with graph names `G1` and `G2` that belong to the entailment named `OWLNG_IDX`. Any inferred triples in the default graph and other named graphs remain in the entailment.

    EXECUTE sem_apis.drop_entailment('owlng_idx',sem_graphs('<urn:G1>','<urn:G2>'));

**Parent topic:** SEM_APIS Package Subprograms

### 15.41 SEM_APIS.DROP_PG_RDFVIEW

#### Format

    SEM_APIS.DROP_PG_RDFVIEW(
         model_name    IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

or

    SEM_APIS.DROP_PG_RDFVIEW(
         model_name    IN VARCHAR2,
         pg_stag_tab   IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops an RDF view model for a property graph stored in Oracle Database.

#### Parameters

model_name
Name of the RDF view model to drop.

pg_stag_tab
Name of the staging table. (See also the `TRUNCATE=T` option.)

options
String specifying options for index creation using the form OPTION_NAME=option_value. Supported options are:

- TRUNCATE=T (truncate the staging table instead of dropping it)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For more information, see [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the RDF view M1.

    EXECUTE SEM_APIS.DROP_PG_RDFVIEW('M1');

The following example drops the RDF view with the staging table MY_STAB, and truncates the staging table instead of dropping it.

    EXECUTE SEM_APIS.DROP_PG_RDFVIEW('M1', 'MY_STAB', 'TRUNCATE_STAB=T');

**Parent topic:** SEM_APIS Package Subprograms

### 15.42 SEM_APIS.DROP_PG_RDFVIEW_INDEXES

#### Format

    SEM_APIS.DROP_PG_RDFVIEW_INDEXES(
         pg_name       IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops indexes that were created using the SEM_APIS.BUILD_PG_RDFVIEW_INDEXES procedure.

#### Parameters

pg_name
Name of the property graph to index.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For more information, see [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops indexes for the property graph G1.

    EXECUTE SEM_APIS.DROP_PG_RDFVIEW_INDEXES('G1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.43 SEM_APIS.DROP_RDFVIEW_MODEL

#### Format

    SEM_APIS.DROP_RDFVIEW_MODEL(
         model_name    IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) an RDF view.

#### Parameters

model_name
Name of the RDF view to be dropped.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must be the owner of the RDF view to be dropped.

For more information about RDF views, see [RDF Views: Relational Data as RDF](rdf-views.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops an RDF view.

    BEGIN
      sem_apis.drop_rdfview_model(
        model_name => 'empdb_model'
      );
    END;
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.44 SEM_APIS.DROP_RULEBASE

#### Format

    SEM_APIS.DROP_RULEBASE(
         rulebase_name  IN VARCHAR2,
         options        IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes a rulebase.

#### Parameters

rulebase_name
Name of the rulebase.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure deletes the specified rulebase, making it no longer available for use in calls to the SEM_MATCH table function. For information about rulebases, see [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md).

Only the creator of a rulebase can delete the rulebase.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the rulebase named `family_rb`.

    EXECUTE SEM_APIS.DROP_RULEBASE('family_rb');

**Parent topic:** SEM_APIS Package Subprograms

### 15.45 SEM_APIS.DROP_SEM_INDEX

#### Format

    SEM_APIS.DROP_SEM_INDEX(
         index_code    IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops a semantic network index on the models and entailments of the semantic network.

#### Parameters

index_code
Index code string. Must match the `index_code` value that was specified in an earlier call to the SEM_APIS.ADD_SEM_INDEX procedure.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For an explanation of semantic network indexes, see [Using Semantic Network Indexes](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops a semantic network index with the index code string `pcsm` on the models and entailments of the semantic network.

    EXECUTE SEM_APIS.DROP_SEM_INDEX('pscm');

**Parent topic:** SEM_APIS Package Subprograms

### 15.46 SEM_APIS.DROP_SEM_MODEL

#### Format

    SEM_APIS.DROP_SEM_MODEL(
         model_name  IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) a semantic technology model.

#### Parameters

model_name
Name of the model.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure deletes the model from the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

This procedure is the only supported way to delete a model. Do not use SQL DELETE statements with the SEM_MODEL\$ view.

Only the creator of a model can delete the model.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the semantic technology model named `articles`.

    EXECUTE SEM_APIS.DROP_SEM_MODEL('articles');

**Parent topic:** SEM_APIS Package Subprograms

### 15.47 SEM_APIS.DROP_SEM_NETWORK

#### Format

    SEM_APIS.DROP_SEM_NETWORK(
         cascade       IN BOOLEAN DEFAULT FALSE,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Removes structures used for persistent storage of semantic data.

#### Parameters

cascade
`TRUE` drops any existing semantic technology models and rulebases, and removes structures used for persistent storage of semantic data; `FALSE` (the default) causes the operation to fail if any semantic technology models or rulebases exist.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To remove structures used for persistent storage of semantic data, you must connect as a user with DBA privileges or as the owner of the schema-private network, and call this procedure.

If any version-enabled models exist, this procedure will fail regardless of the value of the `cascade` parameter.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example removes structures used for persistent storage of semantic data.

    EXECUTE SEM_APIS.DROP_SEM_NETWORK;

**Parent topic:** SEM_APIS Package Subprograms

### 15.48 SEM_APIS.DROP_SPARQL_UPDATE_TABLES

#### Format

    SEM_APIS.DROP_SPARQL_UPDATE_TABLES();

#### Description

Drops the global temporary tables in the caller’s schema for use with SPARQL Update operations.

#### Parameters

None.

#### Usage Notes

This procedure drops the global temporary tables that were created by the SEM_APIS.CREATE_SPARQL_UPDATE_TABLES procedure.

For more information, see [Support for SPARQL Update Operations on a Semantic Model](rdf-semantic-graph-overview.md).

#### Examples

The following example drops the global temporary tables that had been created in the caller’s schema for use with SPARQL Update operations.

    EXECUTE SEM_APIS.DROP_SPARQL_UPDATE_TABLES;

**Parent topic:** SEM_APIS Package Subprograms

### 15.49 SEM_APIS.DROP_SPM_TAB

#### Format

    SEM_APIS.DROP_SPM_TAB (
         model_name         IN VARCHAR2,
         target             IN VARCHAR2,
         options            IN VARCHAR2 DEFAULT NULL,
         network_owner      IN DBMS_ID DEFAULT NULL,
         network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Drops a specific SPM table identified by name and type, all SPM tables of given type, or all SPM tables.

#### Parameters

model_name
Name of the RDF model.

target
Must be NULL, unless used for dropping all SPM tables or SPM tables belonging to a specific category namely SVP, PCN, or MVP. In that case, the supported options are:

- `ALL_SPM`: drops all SPM tables.
- `SVP_ALL`: drops all SVP tables.
- `MVP_ALL`: drops all MVP tables.
- `PCN_ALL`: drops all PCN tables.

options
String specifying any of the following supported drop options:

- `SVP_NAME=<name>`: locates the target SVP table.
- `PCN_NAME=<name>`: locates the target PCN table.
- `MVP_PRED_ID=<number>`: locates the target MVP table.
- `MVP_PRED_NAME=<absolute_IRI>`: locates the target MVP table.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

- This operation has a DDL semantics.
- The invoker must be the owner of the target RDF model or the RDF network or both.

#### Examples

The following example drops all SPM tables:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', ' ALL_SPM ', network_owner=>'RDFUSER', network_name=>'NET1');

The following example drops all SVP tables:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', ' SVP_ALL ', network_owner=>'RDFUSER', network_name=>'NET1');

The following example drops all MVP tables:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', ' MVP_ALL ', network_owner=>'RDFUSER', network_name=>'NET1');

The following example drops all PCN tables:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', ' PCN_ALL ', network_owner=>'RDFUSER', network_name=>'NET1');

The following example drops a specific SVP table named `pinfo`:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', null, options=>' svp_name=pinfo ', network_owner=>'RDFUSER', network_name=>NET1)

The following example drops the default SVP table that was created without a name:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', null, options=>' svp_name=default ', network_owner=>'RDFUSER', network_name=>NET1)

The following example drops a specific PCN table named `cof_dto_name`:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', null, options=>' pcn_name=cof_dto_name ', network_owner=>'RDFUSER', network_name=>NET1)

The following example drops a specific MVP table, identified by an ID specified for the predicate, `mvp_pred_id`:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', null, options=>' mvp_pred_id=6549504896746291108 ', network_owner=>'RDFUSER', network_name=>NET1)

The following example drops a specific MVP table, identified by a predicate specified as shown:

    EXECUTE SEM_APIS.DROP_SPM_TAB('m1', null, options=>' mvp_pred_name=<http://demo/donatedTo> ' , network_owner=>'RDFUSER', network_name=>NET1)

**Parent topic:** SEM_APIS Package Subprograms

### 15.50 SEM_APIS.DROP_USER_INFERENCE_OBJS

#### Format

    SEM_APIS.DROP_USER_INFERENCE_OBJS(
         uname         IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) all rulebases and entailments owned by a specified database user.

#### Parameters

uname
Name of a database user. (This value is case-sensitive; for example, `HERMAN` and `herman` are considered different users.)

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have sufficient privileges to delete rules and rulebases for the specified user.

This procedure does not delete the database user. It deletes only RDF rulebases and entailments owned by that user.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes all rulebases and entailments owned by user `SCOTT`.

    EXECUTE SEM_APIS.DROP_USER_INFERENCE_OBJS('SCOTT');

    PL/SQL procedure successfully completed.

**Parent topic:** SEM_APIS Package Subprograms

### 15.51 SEM_APIS.DROP_VIRTUAL_MODEL

#### Format

    SEM_APIS.DROP_VIRTUAL_MODEL(
         vm_name       IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops (deletes) a virtual model.

#### Parameters

vm_name
Name of the virtual model to be deleted.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You can use this procedure to delete a virtual model that you created using the SEM_APIS.CREATE_VIRTUAL_MODEL procedure. A virtual model is deleted automatically if any of its component models, rulebases, or entailment are deleted.

To use this procedure, you must be the owner of the specified virtual model.

For an explanation of virtual models, including usage information, see [Virtual Models](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes a virtual model named `VM1`.

    EXECUTE sem_apis.drop_virtual_model('VM1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.52 SEM_APIS.ENABLE_CHANGE_TRACKING

#### Format

    SEM_APIS.ENABLE_CHANGE_TRACKING(
         models_in     IN SEM_MODELS,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Enables change tracking for a specified set of models.

#### Parameters

models_in
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Change tracking must be enabled on a model before incremental inference can be enabled on any entailments that use the model.

To use this procedure, you must be the owner of the specified model or models.

If the owner of an entailment is also an owner of any underlying models, then enabling incremental inference on the entailment (by calling the SEM_APIS.ENABLE_INC_INFERENCE procedure) automatically enables change tracking on those models owned by that user.

To disable change tracking for a set of models, use the SEM_APIS.DISABLE_CHANGE_TRACKING procedure.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables change tracking for the `family` model.

    EXECUTE sem_apis.enable_change_tracking(sem_models('family'));

**Parent topic:** SEM_APIS Package Subprograms

### 15.53 SEM_APIS.ENABLE_INC_INFERENCE

#### Format

    SEM_APIS.ENABLE_INC_INFERENCE(
         entailment_name IN VARCHAR2,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Enables incremental inference for a specified entailment (rules index).

#### Parameters

entailment_name
Name of the entailment for which to enable incremental inference.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must be the owner of the specified entailment.

Before this procedure is executed, all underlying models involved in the entailment must have change tracking enabled. If the owner of the entailment is also an owner of any underlying models, calling this procedure automatically enables change tracking on those models. However, if some underlying model are not owned by the owner of the entailment, the appropriate model owners must first call the SEM_APIS.ENABLE_CHANGE_TRACKING procedure to enable change tracking on those models.

To disable incremental inference for an entailment, use the SEM_APIS.DISABLE_INC_INFERENCE procedure.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables incremental inference for the entailment named `RDFS_RIX_FAMILY`.

    EXECUTE sem_apis.enable_inc_inference('rdfs_rix_family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.54 SEM_APIS.ENABLE_INMEMORY

#### Format

    SEM_APIS.ENABLE_INMEMORY(
         populate_wait IN BOOLEAN,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Loads RDF data for the semantic network into memory.

#### Parameters

populate_wait
Boolean value to indicate whether to wait until all RDF data is loaded into memory before finishing:

- `true`: Wait until all RDF data is loaded into memory.

- `false`: Do not wait for RDF data loading into memory.

options
Options for in-memory data population:

- The string `POPULATE_TRIPLES=F` disables populating RDF_LINK\$ table data in memory. (RDF_VALUE\$ table data is still populated in memory.) If this option is not specified, RDF_LINK\$ table data is populated in memory by default.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

To disable in-memory population of RDF data in the semantic network, use the SEM_APIS.DISABLE_INMEMORY.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables in-memory population of RDF data, and waits until all RDF data is loaded into memory before finishing.

    EXECUTE SEM_APIS.ENABLE_INMEMORY(true);

**Parent topic:** SEM_APIS Package Subprograms

### 15.55 SEM_APIS.ENABLE_INMEMORY_FOR_ENT

#### Format

    SEM_APIS.ENABLE_INMEMORY_FOR_ENT(
         entailment_name IN VARCHAR2,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Enables in-memory population of RDF data for an entailment in a semantic network.

#### Parameters

entailment_name
Name of the entailment.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables in-memory population of RDF data for entailment RIDX1 in the MDSYS-owned semantic network.

    EXECUTE SEM_APIS.ENABLE_INMEMORY_FOR_ENT('RIDX1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.56 SEM_APIS.ENABLE_INMEMORY_FOR_MODEL

#### Format

    SEM_APIS.ENABLE_INMEMORY_FOR_MODEL(
         model_name    IN VARCHAR2,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Enables in-memory population of RDF data for a model in a semantic network.

#### Parameters

model_name
Name of the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must have DBA privileges.

See the information in [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables in-memory population of RDF data for model M1 in the MDSYS-owned semantic network.

    EXECUTE SEM_APIS.ENABLE_INMEMORY_FOR_MODEL('M1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.57 SEM_APIS.ENABLE_NETWORK_SHARING

#### Format

    SEM_APIS.ENABLE_NETWORK_SHARING(
         network_owner IN VARCHAR2,
         network_name  IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL);

#### Description

Enables sharing of a semantic network.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

options
(Reserved for future use)

#### Usage Notes

To use this procedure, you must have DBA privileges or be the owner of the specified network.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example enables sharing of the `mynetwork` schema-private network owned by database user `scott`.

    EXECUTE SEM_APIS.ENABLE_NETWORK_SHARING('scott', 'mynetwork');

**Parent topic:** SEM_APIS Package Subprograms

### 15.58 SEM_APIS.ESCAPE_CLOB_TERM

#### Format

    SEM_APIS.ESCAPE_CLOB_TERM(
         term        IN  CLOB CHARACTER SET ANY_CS,
         utf_encode  IN NUMBER DEFAULT 1
         ) RETURN CLOB CHARACTER SET val%CHARSET;

#### Description

Returns the input RDF term with special characters and non-ASCII characters escaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

term
The RDF term to escape.

utf_encode
Set to 1 (the default) if non-ASCII characters and non-printable ASCII characters other than chr(8), chr(9), chr(10), chr(12), and chr(13) should be escaped. Otherwise, such characters will not be escaped.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example escapes an input RDF term containing TAB and NEWLINE characters.

    SELECT SEM_APIS.ESCAPE_CLOB_TERM('"abc' || chr(9) || 'def' || chr(10) || 'hij"^^<http://www.w3.org/2001/XMLSchema#string>')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.59 SEM_APIS.ESCAPE_CLOB_VALUE

#### Format

    SEM_APIS.ESCAPE_CLOB_VALUE(
         val          IN  CLOB CHARACTER SET ANY_CS,
         start_offset IN NUMBER DEFAULT 1,
         end_offset   IN NUMBER DEFAULT 0,
         utf_encode   IN NUMBER DEFAULT 1,
          include_start IN NUMBER DEFAULT 0
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input CLOB value with special characters and non-ASCII characters escaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

val
The CLOB text to escape.

start_offset
The offset in `val` from which to start character escaping. The default (1) causes escaping to start at the first character of `val`.

end_offset
The offset in `val` from which to end character escaping. The default (0) causes escaping to continue through the end of `val`.

utf_encode
Set to 1 (the default) if non-ASCII characters and non-printable ASCII characters other than chr(8), chr(9), chr(10), chr(12), and chr(13) should be escaped. Otherwise, such characters will not be escaped.

include_start
Set to 1 if the characters in val from 1 to `start_offset` should be prefixed (prepended) to the return value. Otherwise, no such characters will be prefixed to the return value.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example escapes an input character string containing TAB and NEWLINE characters.

    SELECT SEM_APIS.ESCAPE_CLOB_VALUE('abc' || chr(9) || 'def' || chr(10) || 'hij')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.60 SEM_APIS.ESCAPE_RDF_TERM

#### Format

    SEM_APIS.ESCAPE_RDF_TERM(
         term       IN  VARCHAR2 CHARACTER SET ANY_CS,
         utf_encode IN NUMBER DEFAULT 1
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input RDF term with special characters and non-ASCII characters escaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

term
The RDF term to escape.

utf_encode
Set to 1 (the default) if non-ASCII characters and non-printable ASCII characters other than chr(8), chr(9), chr(10), chr(12), and chr(13) should be escaped. Otherwise, such characters will not be escaped.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example escapes an input RDF term containing TAB and NEWLINE characters.

    SELECT SEM_APIS.ESCAPE_RDF_TERM('"abc' || chr(9) || 'def' || chr(10) || 'hij"^^<http://www.w3.org/2001/XMLSchema#string>')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.61 SEM_APIS.ESCAPE_RDF_VALUE

#### Format

    SEM_APIS.ESCAPE_RDF_VALUE(
         val         IN  VARCHAR2 CHARACTER SET ANY_CS,
         utf_encode  IN NUMBER DEFAULT 1
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input CLOB value with special characters and non-ASCII characters escaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

val
The text to escape.

utf_encode
Set to 1 (the default) if non-ASCII characters and non-printable ASCII characters other than chr(8), chr(9), chr(10), chr(12), and chr(13) should be escaped. Otherwise, such characters will not be escaped.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example escapes an input character string containing TAB and NEWLINE characters.

    SELECT SEM_APIS.ESCAPE_RDF_VALUE('abc' || chr(9) || 'def' || chr(10) || 'hij')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.62 SEM_APIS.EXPORT_ENTAILMENT_STATS

#### Format

    SEM_APIS.EXPORT_ENTAILMENT_STATS (
         entailment_name IN VARCHAR2,
         stattab         IN VARCHAR2,
         statid          IN VARCHAR2 DEFAULTNULL,
         cascade         IN BOOLEAN DEFAULT TRUE,
         statown         IN VARCHAR2 DEFAULT NULL,
         stat_category   IN VARCHAR2 DEFAULT 'OBJECT_STATS',
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Exports statistics for a specified entailment and stores them in the user statistics table.

#### Parameters

entailment_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.EXPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to entailment statistics.

Specifying `cascade` also exports all index statistics associated with the entailment.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example exports statistics for an entailment named `OWLTST_IDX` and stores them in a table named `STAT_TABLE`.

    EXECUTE SEM_APIS.EXPORT_ENTAILMENT_STATS('owltst_idx', 'stat_table');

**Parent topic:** SEM_APIS Package Subprograms

### 15.63 SEM_APIS.EXPORT_MODEL_STATS

#### Format

    SEM_APIS.EXPORT_MODEL_STATS (
         model_name    IN VARCHAR2,
         stattab       IN VARCHAR2,
         statid        IN VARCHAR2 DEFAULT NULL,
         cascade       IN BOOLEAN DEFAULT TRUE,
         statown       IN VARCHAR2 DEFAULT NULL,
         stat_category IN VARCHAR2 DEFAULT 'OBJECT_STATS',
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Exports statistics for a specified model and stores them in the user statistics table.

#### Parameters

entailment_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.EXPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference.

Specifying `cascade` also exports all index statistics associated with the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example exports statistics for a model named `FAMILY` and stores them in a table named `STAT_TABLE`.

    EXECUTE SEM_APIS.EXPORT_MODEL_STATS('family', 'stat_table');

**Parent topic:** SEM_APIS Package Subprograms

### 15.64 SEM_APIS.EXPORT_RDFVIEW_MODEL

#### Format

    SEM_APIS.EXPORT_RDFVIEW_MODEL(
         model_name       IN VARCHAR2,
         rdf_table_owner  IN VARCHAR2 DEFAULT NULL,
         rdf_table_name   IN VARCHAR2 DEFAULT NULL,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Exports (materializes) the virtual RDF triples of an RDF view to a staging table.

#### Parameters

model_name
Name of the RDF view to be exported.

rdf_table_owner
Name of the schema that owns the staging table where the RDF triples obtained from the RDF view are to be stored.

rdf_table_name
Name of the staging table where the RDF triples obtained from the RDF view are to be stored.

options
(Reserved for future use)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have the SELECT privilege for the database view SEMM\_\<model_name\>.

For more information about RDF views, see [RDF Views: Relational Data as RDF](rdf-views.md). For information about exporting RDF views, see [Exporting Virtual Content of an RDF View into a Staging Table](rdf-views.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example exports RDF triples from RDF view `empdb_model` to the staging table SCOTT.RDFTAB.

    BEGIN
      sem_apis.export_rdfview_model(
        model_name => 'empdb_model',
        rdf_table_owner => 'SCOTT',
        rdf_table_name => 'RDFTAB'
      );
    END;
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.65 SEM_APIS.GATHER_SPM_INFO

#### Format

    SEM_APIS.GATHER_SPM_INFO (
        model_name         IN VARCHAR2,
        pred_info_tabname  IN DBMS_ID,
        tablespace_name    IN DBMS_ID DEFAULT NULL,
        degree             IN NUMBER DEFAULT NULL,
        options            IN VARCHAR2 DEFAULT NULL,
        network_owner      IN DBMS_ID DEFAULT NULL,
        network_name       IN VARCHAR2 DEFAULT NULL);

#### Description

Gathers information about predicate use in a given RDF model.

For more information on SPM tables content, see [Creating SPM Tables](rdf-semantic-graph-overview.md).

#### Parameters

model_name
Name of the RDF model.

pred_info_tabname
Name of the table to be created to contain the information about predicate use.

tablespace_name
Name of the target tablespace for the `pred_info_tabname` table.

degree
Degree of parallelism.

options
String specifying the options to use during the operation.

Supported option is:

`CREATE_ANYWAY=T`: Truncate the table specified in `pred_info_tabname`.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

- The `pred_info_tabname` table will be created in the invoker’s schema.
- Invoker must have READ privilege for the RDF model.

#### Examples

The following example creates a new table `M1_PRED_INFO` in the invoker’s schema. This table contains predicate use information for the specified model `M1` in the RDF network named `NET1` owned by `RDFUSER`.

       begin
            sem_apis.gather_spm_info(
            model_name        => 'M1',
            pred_info_tabname => 'M1_PRED_INFO',
            degree            => 2,
            network_owner     => 'RDFUSER',
            network_name      => 'NET1'
            );
       end;

**Parent topic:** SEM_APIS Package Subprograms

### 15.66 SEM_APIS.GET_CHANGE_TRACKING_INFO

#### Format

    SEM_APIS.GET_CHANGE_TRACKING_INFO(
         model_name           IN VARCHAR2,
         enabled              OUT BOOLEAN,
         tracking_start_time  OUT TIMESTAMP,
         network_owner        IN VARCHAR2 DEFAULT NULL,
         network_name         IN VARCHAR2 DEFAULT NULL);

#### Description

Returns change tracking information for a model.

#### Parameters

model_name
Name of the semantic technology model.

enabled
Boolean value returned by the procedure: `TRUE` if change tracking is enabled for the model, or `FALSE` if change tacking is not enabled for the model.

tracking_start_time
Timestamp indicating when change tracking was enabled for the model (if it is enabled).

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The `model_name` value must match a value in the MODEL_NAME column in the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

To enable change tracking for a set of models, use the SEM_APIS.ENABLE_CHANGE_TRACKING procedure.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example displays change tracking information for a model.

    DECLARE
      bEnabled  boolean;
      tsEnabled  timestamp;

    BEGIN
      EXECUTE IMMEDIATE 'create table m1 (t SDO_RDF_TRIPLE_S)';
      sem_apis.create_sem_model('m1','m1','t');

      sem_apis.enable_change_tracking(sem_models('m1'));

      sem_apis.get_change_tracking_info('m1', bEnabled,  tsEnabled);
      dbms_output.put_line('is enabled:' || case when bEnabled then 'true' else 'false' end);
      dbms_output.put_line('enabled at:' || tsEnabled);
    END;
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.67 SEM_APIS.GET_INC_INF_INFO

#### Format

    SEM_APIS.GET_INC_INF_INFO(
         entailment_name     IN VARCHAR2,
         enabled             OUT BOOLEAN,
         prev_inf_start_time OUT TIMESTAMP,
         network_owner       IN VARCHAR2 DEFAULT NULL,
         network_name        IN VARCHAR2 DEFAULT NULL);

#### Description

Returns incremental inference information for an entailment.

#### Parameters

entailment_name
Name of the entailment.

enabled
Boolean value returned by the procedure: `TRUE` if incremental inference is enabled for the entailment, or `FALSE` if incremental inference is not enabled for the entailment.

prev_inf_start_time
Timestamp indicating when the entailment was most recently updated (if incremental inference is enabled).

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To enable incremental inference for an entailment, use the SEM_APIS.ENABLE_INC_INFERENCE procedure.

For an explanation of incremental inference, including usage information, see [Performing Incremental Inference](owl-concepts.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example displays incremental inference information for an entailment.

    DECLARE
      bEnabled boolean;
      tsEnabled timestamp;

    DECLARE
      EXECUTE IMMEDIATE 'create table m1 (t SDO_RDF_TRIPLE_S)';
      sem_apis.create_sem_model('m1','m1','t');

      sem_apis.create_entailment('m1_inf',sem_models('m1'),
    sem_rulebases('owlprime'),null,null,'INC=T');

      sem_apis.get_inc_inf_info('m1_inf', bEnabled,  tsEnabled);
      dbms_output.put_line('is enabled:' || case when bEnabled then 'true' else 'false'
      end);
      dbms_output.put_line('enabled at:' || tsEnabled);
    END
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.68 SEM_APIS.GET_MODEL_ID

#### Format

    SEM_APIS.GET_MODEL_ID(
         model_name  IN VARCHAR2
         ) RETURN NUMBER;

#### Description

Returns the model ID number of a semantic technology model.

#### Parameters

model_name
Name of the semantic technology model.

#### Usage Notes

The `model_name` value must match a value in the MODEL_NAME column in the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

#### Examples

The following example returns the model ID number for the model named `articles`. (This example is an excerpt from [Example 1-121](rdf-semantic-graph-overview.md) in [Example: Journal Article Information](rdf-semantic-graph-overview.md).)

    SELECT SEM_APIS.GET_MODEL_ID('articles') AS model_id FROM DUAL;

      MODEL_ID
    ----------
             1

**Parent topic:** SEM_APIS Package Subprograms

### 15.69 SEM_APIS.GET_MODEL_NAME

#### Format

    SEM_APIS.GET_MODEL_NAME(
         model_id  IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the model name of a semantic technology model.

#### Parameters

model_id
ID number of the semantic technology model.

#### Usage Notes

The `model_id` value must match a value in the MODEL_ID column in the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

#### Examples

The following example returns the model ID number for the model with the ID value of 1. This example is an excerpt from [Example 1-121](rdf-semantic-graph-overview.md) in [Example: Journal Article Information](rdf-semantic-graph-overview.md).)

    SQL> SELECT SEM_APIS.GET_MODEL_NAME(1) AS model_name FROM DUAL;

    MODEL_NAME
    --------------------------------------------------------------------------------
    ARTICLES

**Parent topic:** SEM_APIS Package Subprograms

### 15.70 SEM_APIS.GET_TRIPLE_ID

#### Format

    SEM_APIS.GET_TRIPLE_ID(
         model_id  IN NUMBER,
         subject   IN VARCHAR2,
         property  IN VARCHAR2,
         object    IN VARCHAR2
         ) RETURN VARCHAR2;

or

    SEM_APIS.GET_TRIPLE_ID(
         model_name IN VARCHAR2,
         subject    IN VARCHAR2,
         property   IN VARCHAR2,
         object     IN VARCHAR2
         ) RETURN VARCHAR2;

#### Description

Returns the ID of a triple in the specified semantic technology model, or a null value if the triple does not exist.

#### Parameters

model_id
ID number of the semantic technology model. Must match a value in the MODEL_ID column of the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

model_name
Name of the semantic technology model. Must match a value in the MODEL_NAME column of the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

subject
Subject. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

property
Property. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

object
Object. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

#### Usage Notes

This function has two formats, enabling you to specify the semantic technology model by its model number or its name.

#### Examples

The following example returns the ID number of a triple. (This example is an excerpt from [Example 1-121](rdf-semantic-graph-overview.md) in [Example: Journal Article Information](rdf-semantic-graph-overview.md).)

    SELECT SEM_APIS.GET_TRIPLE_ID(
      'articles',
      'http://nature.example.com/Article2',
      'http://purl.org/dc/terms/references',
      'http://nature.example.com/Article3') AS RDF_triple_id FROM DUAL;

    RDF_TRIPLE_ID
    --------------------------------------------------------------------------------
    2_9F2BFF05DA0672E_90D25A8B08C653A_46854582F25E8AC5

**Parent topic:** SEM_APIS Package Subprograms

### 15.71 SEM_APIS.GETV\$DATETIMETZVAL

#### Format

    SEM_APIS.GETV$DATETIMETZVAL(
         value_type     IN VARCHAR2,
         vname_prefix   IN VARCHAR2,
         vname_suffix   IN VARCHAR2,
         literal_type   IN VARCHAR2,
         language_type  IN VARCHAR2,
         ) RETURN NUMBER;

#### Description

Returns a TIMESTAMP WITH TIME ZONE value for xsd:dateTime typed literals, and returns a null value for all other RDF terms. Greenwich Mean Time is used as the default time zone for xsd:dateTime values without time zones.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

#### Usage Notes

For better performance, consider creating a function-based index on this function. For more information, see [Function-Based Indexes for FILTER Constructs Involving Typed Literals](rdf-semantic-graph-overview.md).

#### Examples

The following example returns TIMESTAMP WITH TIME ZONE values for all xsd:dateTime literals in the RDF_VALUE\$ table:

    SELECT SEM_APIS.GETV$DATETIMETZVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.72 SEM_APIS.GETV\$DATETZVAL

#### Format

    SEM_APIS.GETV$DATETZVAL(
         value_type     IN VARCHAR2,
         vname_prefix   IN VARCHAR2,
         vname_suffix   IN VARCHAR2,
         literal_type   IN VARCHAR2,
         language_type  IN VARCHAR2,
         ) RETURN TIMESTAMP WITH TIME ZONE;

#### Description

Returns a TIMESTAMP WITH TIME ZONE value for xsd:date typed literals, and returns a null value for all other RDF terms. Greenwich Mean Time is used as the default time zone for xsd:date values without time zones.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

#### Usage Notes

For better performance, consider creating a function-based index on this function. For more information, see [Function-Based Indexes for FILTER Constructs Involving Typed Literals](rdf-semantic-graph-overview.md).

#### Examples

The following example returns TIMESTAMP WITH TIME ZONE values for all xsd:date literals in the RDF_VALUE\$ table:

    SELECT SEM_APIS.GETV$DATETZVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.73 SEM_APIS.GETV\$GEOMETRYVAL

#### Format

    SEM_APIS.GETV$GEOMETRYVAL(
         value_type    IN VARCHAR2,
         vname_prefix  IN VARCHAR2,
         vname_suffix  IN VARCHAR2,
         literal_type  IN VARCHAR2,
         language_type IN VARCHAR2,
         long_value    IN CLOB,
         srid          IN NUMBER,
         ) RETURN SDO_GEOMETRY;

#### Description

Returns an SDO_GEOMETRY object in the spatial reference system identified by an input SRID for ogc:wktLiteral or ogc:gmlLiteral typed literals, and returns a null value for all other RDF terms.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

long_value
CLOB value for long literals.

srid
Target coordinate system (spatial reference system) identifier for the SDO_GEOMETRY object to be returned.

#### Usage Notes

ogc:wktLiteral and ogc:gmlLiteral values encode spatial reference system information in the literal value itself (referred to as the source SRID).

If the `srid` parameter value (the target SRID) is different from the source SRID, the newly created SDO_GEOMETRY object is transformed to the target SRID before it is returned.

This operation can be expensive in terms of performance.

For information about the SDO_GEOMETRY type (including SRID values), see [Oracle Spatial and Graph Developer’s Guide](../spatl/spatial-datatypes-metadata.md).

#### Examples

The following example returns SDO_GEOMETRY values in the WGS84 (Longitude, Latitude) spatial reference system (SRID 8307) for all geometry literals in the RDF_VALUE\$ table:

    SELECT SEM_APIS.GETV$GEOMETRYVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type, long_value, 8307)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.74 SEM_APIS.GETV\$NUMERICVAL

#### Format

    SEM_APIS.GETV$NUMERICVAL(
         value_type     IN VARCHAR2,
         vname_prefix   IN VARCHAR2,
         vname_suffix   IN VARCHAR2,
         literal_type   IN VARCHAR2,
         language_type  IN VARCHAR2,
         ) RETURN NUMBER;

#### Description

Returns a numeric value for XML Schema numeric typed literals, and returns a null value for all other RDF terms.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

#### Usage Notes

For better performance, consider creating a function-based index on this function. For more information, see [Function-Based Indexes for FILTER Constructs Involving Typed Literals](rdf-semantic-graph-overview.md).

#### Examples

The following example returns numeric values for all numeric literals in the RDF_VALUE\$ table:

    SELECT SEM_APIS.GETV$NUMERICVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.75 SEM_APIS.GETV\$STRINGVAL

#### Format

    SEM_APIS.GETV$STRINGVAL(
         value_type     IN VARCHAR2,
         vname_prefix   IN VARCHAR2,
         vname_suffix   IN VARCHAR2,
         literal_type   IN VARCHAR2,
         language_type  IN VARCHAR2,
         ) RETURN TIMESTAMP WITH TIME ZONE;

#### Description

Returns a VARCHAR2 string of the lexical form of plain literals and xsd:string typed literals, and returns a null value for all other RDF terms. CHR(0) is returned for empty literals.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

#### Usage Notes

For better performance, consider creating a function-based index on this function. For more information, see [Function-Based Indexes for FILTER Constructs Involving Typed Literals](rdf-semantic-graph-overview.md).

#### Examples

The following example returns lexical values for all plain literals and xsd:string literals in the RDF_VALUE\$ table:

    SELECT SEM_APIS.GETV$STRINGVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.76 SEM_APIS.GETV\$TIMETZVAL

#### Format

    SEM_APIS.GETV$TIMETZVAL(
         value_type     IN VARCHAR2,
         vname_prefix   IN VARCHAR2,
         vname_suffix   IN VARCHAR2,
         literal_type   IN VARCHAR2,
         language_type  IN VARCHAR2,
         ) RETURN TIMESTAMP WITH TIME ZONE;

#### Description

Returns a TIMESTAMP WITH TIME ZONE value for xsd:time typed literals, and returns a null value for all other RDF terms. Greenwich Mean Time is used as the default time zone for xsd:time values without time zones. 2009-06-26 is used as the default date in all the generated TIMESTAMP WITH TIME ZONE values.

#### Parameters

value_type
Type of the RDF term.

vname_prefix
Prefix value of the RDF term.

vname_suffix
Suffix value of the RDF term.

literal_type
Literal type of the RDF term.

language_type
Language type of the RDF term.

#### Usage Notes

For better performance, consider creating a function-based index on this function. For more information, see [Function-Based Indexes for FILTER Constructs Involving Typed Literals](rdf-semantic-graph-overview.md).

Because xsd:time values include only a time but not a date, the returned TIMESTAMP WITH TIME ZONE values (which include a date component) have 2009-06-26 added as the date. This is done so that the returned values can be indexed internally, and so that the date is the same for all of them.

#### Examples

The following example returns TIMESTAMP WITH TIME ZONE values (using the default 2009-06-26 for the date) for all xsd:time literals in the RDF_VALUE\$ table. (

    SELECT SEM_APIS.GETV$DATETIMETZVAL(value_type, vname_prefix, vname_suffix,
      literal_type, language_type)
      FROM RDF_VALUE$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.77 SEM_APIS.GRANT_MODEL_ACCESS_PRIV

#### Format

    SEM_APIS.GRANT_MODEL_ACCESS_PRIV(
         model_name      IN VARCHAR2,
         user_name       IN VARCHAR2,
         privilege       IN VARCHAR2,
         user_view       IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Grants access privilege on a model or entailment.

#### Parameters

model_name
Name of the model.

user_name
Database user that is recipient of this privilege.

privilege
Specifies the type of privilege that is granted. Currently allowed values include the following:

- `QUERY`: Query the model using SPARQL
- `SELECT`, `READ`: Retrieve model content using SQL. For schema-private network, the source for the content is the `RDFT_<model>` view in the network owner's schema or the view name, if any, specified for the `user_view` parameter. For MDSYS-owned network, the source for the content is the application table.
- `INSERT`, `UPDATE`, `DELETE`: Perform SPARQL Update (DML) operations on the model or SQL DML operations. For SQL DML, the target object is different depending upon the type of network. For schema-private network, it is the `RDFT_<model>` view in the network owner's schema and for MDSYS-owned network, it is the application table.

**Note:**

`QUERY` is the only valid choice if the model is not a regular model (that is, not created using `sem_apis.create_sem_model`).

user_view
Applicable to schema-private network only. If a view was created on the `RDFT_<model>` view at model creation time using `sem_apis.create_sem_model` or later, privilege is granted on that view.

options
If user specifies the word `ENTAILMENT` as part of the string value, then the specified `model_name` is taken as the name of an entailment (rules index). (Additional words or phrases may be allowed in future.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The recipient must already have query-only or full access to the semantic network (which guarantees access to dictionary tables, but not individual models). This operation grants access to the specified model.

#### Examples

The following example grants privilege to database user `USER1` to use SPARQL query against a semantic technology model named `articles` in the schema-private network `NET1` owned by database user `RDFUSER`. (This example refers to the model described in [Example 1-121](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.GRANT_MODEL_ACCESS_PRIV('articles', 'USER1', 'QUERY', network_owner=>'RDFUSER', network_name=>'NET1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.78 SEM_APIS.GRANT_MODEL_ACCESS_PRIVS

#### Format

    SEM_APIS.GRANT_MODEL_ACCESS_PRIVS(
         model_name      IN VARCHAR2,
         user_name       IN VARCHAR2,
         priv_list       IN SYS.ODCIVARCHAR2LIST,
         user_view       IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Grants access privileges on a model or entailment.

#### Parameters

model_name
Name of the model.

user_name
Database user that is recipient of this privilege.

priv_list
Specifies the list of privileges that are granted. Currently allowed values include the following:

- `QUERY`: Query the model using SPARQL
- `SELECT`, `READ`: Retrieve model content using SQL. For schema-private network, the source for the content is the `RDFT_<model>` view in the network owner's schema or the view name, if any, specified for the `user_view` parameter. For MDSYS-owned network, the source for the content is the application table.
- `INSERT`, `UPDATE`, `DELETE`: Perform SPARQL Update (DML) operations on the model or SQL DML operations. For SQL DML, the target object is different depending upon the type of network. For schema-private network, it is the `RDFT_<model>` view in the network owner's schema and for MDSYS-owned network, it is the application table.

**Note:**

`QUERY` is the only valid choice if the model is not a regular model (that is, not created using `sem_apis.create_sem_model`).

user_view
Applicable to schema-private network only. If a view was created on the `RDFT_<model>` view at model creation time using `sem_apis.create_sem_model` or later, privileges are granted on that view.

options
If user specifies the word `ENTAILMENT` as part of the string value, then the specified `model_name` is taken as the name of an entailment (rules index).(Additional words or phrases may be allowed in future.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The recipient must already have query-only or full access to the semantic network (which guarantees access to dictionary tables, but not individual models). This operation grants access to the specified model.

#### Examples

The following example grants privileges to perform DML operations against a semantic technology model named `articles` in the schema-private network `NET1` owned by database user `RDFUSER`. (This example refers to the model described in [Example 1-121](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.GRANT_MODEL_ACCESS_PRIVS('articles', 'USER1', sys.odcivarchar2list('INSERT','UPDATE','DELETE'), network_owner=>'RDFUSER', network_name=>'NET1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.79 SEM_APIS.GRANT_NETWORK_ACCESS_PRIVS

#### Format

    SEM_APIS.GRANT_NETWORK_ACCESS_PRIVS(
         network_owner  IN VARCHAR2,
         network_name   IN VARCHAR2,
         network_user   IN VARCHAR2,
         options        IN VARCHAR2 default NULL);

#### Description

Grants query-only or full access privileges to a database user other than the owner of a schema-private semantic network.

#### Parameters

network_owner
Owner of the network. (Cannot be MDSYS.)

network_name
Name of the network. (Must be a schema-private network.)

network_user
Database user (other than the network owner) to which to grant access privileges to the network.

options
String specifying options for access using the form OPTION_NAME=option_value. By default, full access privileges are given; but to give query-only access, specify `QUERY_ONLY=T` for the option value.

#### Usage Notes

You must have DBA privileges or be the owner of the specified network to call this procedure.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example grants full access on the `mynet1` network owned by `scott` to `rdfuser1`.

    EXECUTE SEM_APIS.GRANT_NETWORK_ACCESS_PRIVS('scott','mynet1','rdfuser1');

The following example grants query-only access on the `mynet1` network owned by `scott` to `rdfuser2`.

    EXECUTE SEM_APIS.GRANT_NETWORK_ACCESS_PRIVS('scott','mynet1','rdfuser2', options=>' QUERY_ONLY=T ');

**Parent topic:** SEM_APIS Package Subprograms

### 15.80 SEM_APIS.GRANT_NETWORK_SHARING_PRIVS

#### Format

    SEM_APIS.GRANT_NETWORK_SHARING_PRIVS(
         network_owner  IN VARCHAR2,
         options        IN VARCHAR2 default NULL);

#### Description

Grants to a database user the privileges required for sharing, with other database users, any schema-private networks owned (currently or in the future) by the database user.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

options
(Reserved for future use)

#### Usage Notes

You must have DBA privileges to call this procedure.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example grants to database user `scott` the privileges for sharing any schema-private networks that this user owns or will own.

    EXECUTE SEM_APIS.GRANT_NETWORK_SHARING_PRIVS('scott');

**Parent topic:** SEM_APIS Package Subprograms

### 15.81 SEM_APIS.IMPORT_ENTAILMENT_STATS

#### Format

    SEM_APIS.IMPORT_ENTAILMENT_STATS (
         entailment_name  IN VARCHAR2,
         stattab          IN VARCHAR2,
         statid           IN VARCHAR2 DEFAULT NULL,
         cascade          IN BOOLEAN DEFAULT TRUE,
         statown          IN VARCHAR2 DEFAULT NULL,
         no_invalidate    IN BOOLEAN DEFAULT FALSE,
         force            IN BOOLEAN DEFAULT FALSE,
         stat_category    IN VARCHAR2 DEFAULT 'OBJECT_STATS',
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Retrieves statistics for an entailment from a user statistics table and stores them in the dictionary.

#### Parameters

entailment_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.IMPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to entailment statistics.

Specifying `cascade` also exports all index statistics associated with the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example imports statistics for an entailment named `OWLTST_IDX` from a table named `STAT_TABLE`.

    EXECUTE SEM_APIS.IMPORT_ENTAILMENT_STATS('owltst_idx', 'stat_table');

**Parent topic:** SEM_APIS Package Subprograms

### 15.82 SEM_APIS.IMPORT_MODEL_STATS

#### Format

    SEM_APIS.IMPORT_MODEL_STATS (
         model_name    IN VARCHAR2,
         stattab       IN VARCHAR2,
         statid        IN VARCHAR2 DEFAULT NULL,
         cascade       IN BOOLEAN DEFAULT TRUE,
         statown       IN VARCHAR2 DEFAULT NULL,
         no_invalidate IN BOOLEAN DEFAULT FALSE,
         force         IN BOOLEAN DEFAULT FALSE,
         stat_category IN VARCHAR2 DEFAULT 'OBJECT_STATS,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Retrieves statistics for a specified model from a user statistics table and stores them in the dictionary.

#### Parameters

model_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.IMPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference.

Specifying `cascade` also imports all index statistics associated with the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example imports statistics for a model named `FAMILY` from a table named `STAT_TABLE`, and stores them in the dictionary.

    EXECUTE SEM_APIS.IMOPRT_MODEL_STATS('family', 'stat_table');

**Parent topic:** SEM_APIS Package Subprograms

### 15.83 SEM_APIS.IS_TRIPLE

#### Format

    SEM_APIS.IS_TRIPLE(
         model_id  IN NUMBER,
         subject   IN VARCHAR2,
         property  IN VARCHAR2,
         object    IN VARCHAR2) RETURN VARCHAR2;

or

    SEM_APIS.IS_TRIPLE(
         model_name IN VARCHAR2,
         subject    IN VARCHAR2,
         property   IN VARCHAR2,
         object     IN VARCHAR2) RETURN VARCHAR2;

#### Description

Checks if a statement is an existing triple in the specified model in the database.

#### Parameters

model_id
ID number of the semantic technology model. Must match a value in the MODEL_ID column of the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

model_name
Name of the semantic technology model. Must match a value in the MODEL_NAME column of the SEM_MODEL\$ view, which is described in [Metadata for Models](rdf-semantic-graph-overview.md).

subject
Subject. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

property
Property. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

object
Object. Must match a value in the VALUE_NAME column of the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

#### Usage Notes

This function returns the string value `FALSE`, `TRUE`, or `TRUE (EXACT)`:

- `FALSE` means that the statement is not a triple in the specified model the database.

- `TRUE` means that the statement matches the value of a triple or is the canonical representation of the value of a triple in the specified model the database.

- `TRUE (EXACT)` means that the specified `subject`, `property`, and `object` values have exact matches in a triple in the specified model in the database.

#### Examples

The following example checks if a statement is a triple in the database. In this case, there is an exact match. (This example is an excerpt from [Example 1-121](rdf-semantic-graph-overview.md) in [Example: Journal Article Information](rdf-semantic-graph-overview.md).)

    SELECT SEM_APIS.IS_TRIPLE(
      'articles',
      'http://nature.example.com/Article2',
      'http://purl.org/dc/terms/references',
      'http://nature.example.com/Article3') AS is_triple FROM DUAL;

    IS_TRIPLE
    --------------------------------------------------------------------------------
    TRUE (EXACT)

**Parent topic:** SEM_APIS Package Subprograms

### 15.84 SEM_APIS.LOAD_INTO_STAGING_TABLE

#### Format

    SEM_APIS.LOAD_INTO_STAGING_TABLE(
         stagong_table    IN VARCHAR2,
         source_table     IN VARCHAR2,
         input_format     IN VARCHAR2 DEFAULT NULL,
         parallel         IN INTEGER DEFAULT NULL,
         staging_table_owner IN VARCHAR2 DEFAULT NULL,
         source_table_owner  IN VARCHAR DEFAULT NULL,
         flags            IN VARCHAR DEFAULT NULL);

#### Description

Loads data into a staging table from an external table mapped to an N-Triple or N-Quad format input file.

#### Parameters

staging_table
Name of the staging table.

source_table
Name of the source external table.

input_format
Format of the input file mapped by the source external table: `N-TRIPLE` or `N-QUAD`

parallel
Degree of parallelism to use during the load.

staging_table_owner
Owner for the staging table being created. If not specified, the invoker is assumed to be the owner.

source_table_owner
Owner for the source table. If not specified, the invoker is assumed to be the owner.

flags
(Reserved for future use)

#### Usage Notes

For more information and an example, see [Loading N-Quad Format Data into a Staging Table Using an External Table](rdf-semantic-graph-overview.md).

#### Examples

The following example loads the staging table. (This example is an excerpt from [Example 1-100](rdf-semantic-graph-overview.md) in [Loading N-Quad Format Data into a Staging Table Using an External Table](rdf-semantic-graph-overview.md).)

    BEGIN
      sem_apis.load_into_staging_table(
        staging_table => 'STAGE_TABLE'
       ,source_table  => 'stage_table_source'
       ,input_format  => 'N-QUAD');
    END;

**Parent topic:** SEM_APIS Package Subprograms

### 15.85 SEM_APIS.LOOKUP_ENTAILMENT

#### Format

    SEM_APIS.LOOKUP_ENTAILMENT (
         models     IN SEM_MODELS,
         rulebases  IN SEM_RULEBASES
         ) RETURN VARCHAR2;

#### Description

Returns the name of the entailment (rules index) based on the specified models and rulebases.

#### Parameters

models
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

rulebases
One or more rulebase names. Its data type is SEM_RULEBASES, which has the following definition: `TABLE OF VARCHAR2(25)`Rules and rulebases are explained in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md).

#### Usage Notes

For a rulebase index to be returned, it must be based on all specified models and rulebases.

#### Examples

The following example finds the entailment that is based on the `family` model and the `RDFS` and `family_rb` rulebases. (It is an excerpt from [Example 1-122](rdf-semantic-graph-overview.md) in [Example: Family Information](rdf-semantic-graph-overview.md).)

    SELECT SEM_APIS.LOOKUP_ENTAILMENT(SEM_MODELS('family'),
      SEM_RULEBASES('RDFS','family_rb')) AS lookup_entailment FROM DUAL;

    LOOKUP_ENTAILMENT
    --------------------------------------------------------------------------------
    RDFS_RIX_FAMILY

**Parent topic:** SEM_APIS Package Subprograms

### 15.86 SEM_APIS.MERGE_MODELS

#### Format

    SEM_APIS.MERGE_MODELS(
         source_model         IN VARCHAR2,
         destination_model    IN VARCHAR2,
         rebuild_apptab_index IN BOOLEAN DEFAULT TRUE,
         drop_source_model    IN BOOLEAN DEFAULT FALSE,
         options              IN VARCHAR2 DEFAULT NULL,
         network_owner        IN VARCHAR2 DEFAULT NULL,
         network_name         IN VARCHAR2 DEFAULT NULL);

#### Description

Inserts the content from a source model into a destination model, and updates the destination application table.

#### Parameters

source_model
Name of the source model.

destination_model
Name of the destination model.

rebuild_apptab_index
`TRUE` causes indexes on the destination application table to be rebuilt after the models are merged; `FALSE` does not rebuild any indexes.

drop_source_model
`TRUE` causes the source model (`source_model`) to be deleted after the models are merged; `FALSE` (the default) does not delete the source model.

options
A comma-delimited string of options that overrides the default behavior of the procedure. Currently, only the `DOP` (degree of parallelism) option is supported, to enable parallel execution of this procedure and to specify the degree of parallelism to be associated with the operation.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Before you merge any models, if you are using positional parameters, check to be sure that you are specifying the correct models for the first and second parameters (source model for the first, destination model for the second). This is especially important if you plan to specify `drop_source_model=TRUE`.

If appropriate, make copies of the destination model or both models before performing the merge. To make a copy of a model, use SEM_APIS.CREATE_SEM_MODEL to create an empty model with the desired name for the copy, and use SEM_APIS.MERGE_MODELS to populate the newly created copy as the destination model.

Some common uses for this procedure include the following:

- If you have read-only access to a model that you want to modify, you can clone that model into an empty model on which you have full access, and then modify this latter model.

- If you want to consolidate multiple models, you can use this procedure as often as necessary to merge the necessary models. Merging all models beforehand and using only the merged model simplifies entailment and can improve entailment performance.

On a multi-core or multi-cpu machine, the `DOP` (degree of parallelism) option can be beneficial. See Examples for an example that uses the `DOP` option.

If the source model is large, you may want to update the optimizer statistics on the destination after the merge operation by calling the SEM_APIS.ANALYZE_MODEL procedure.

The following considerations apply to the use of this procedure:

- You must be the owner of the destination model and have SELECT privilege on the source model. If `drop_second_model=TRUE`, you must also be owner of the source model.

- This procedure is not supported on virtual models (explained in [Virtual Models](rdf-semantic-graph-overview.md)).

- No table constraints are allowed on the destination application table.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example inserts the contents of model `M1` into `M2`.

    EXECUTE SEM_APIS.MERGE_MODELS('M1', 'M2');

The following example inserts the contents of model `M1` into `M2`, and it specifies a degree of parallelism of 4 (up to four parallel threads for execution of the merge operation).

    EXECUTE SEM_APIS.MERGE_MODELS('M1', 'M2', null, null, 'DOP=4');

**Parent topic:** SEM_APIS Package Subprograms

### 15.87 SEM_APIS.MIGRATE_DATA_TO_CURRENT

#### Format

    SEM_APIS.MIGRATE_DATA_TO_CURRENT(
         options  IN VARCHAR2 DEFAULT NULL);

#### Description

Migrates semantic data from before Oracle Database Release 12.2 data to the format needed for use with RDF in the current Oracle Database release.

#### Parameters

options
If you specify `INS_AS_SEL=T`, the migration is performed using a bulk load operation. If you do not specify that value, then by default update operations are performed. See the Usage Notes for more information.

#### Usage Notes

It is strongly recommended that you use this procedure to migrate semantic data created using Oracle Database 11.1. 11.2, and 12.1, as explained in [Required Migration of Pre-12.2 Semantic Data](rdf-semantic-graph-overview.md).

This procedure does not perform any operation on semantic data that is already in the current format.

For the `options` parameter, if the amount of data to be migrated is small, the default (not specifying the parameter) probably provides adequate performance. However, for large amounts of data, specifying `INS_AS_SEL=T` can improve performance significantly.

#### Examples

The following example migrates Release 11.2 semantic data in the network to the format for the current Oracle Database version. It performs the migration using a bulk load operation.

    EXECUTE sem_apis.migrate_data_to_current('INS_AS_SEL=T');

The following example migrates Release 11.2 semantic data in the network to the format for the current Oracle Database version. It performs the migration using update operations (the default).

    EXECUTE sem_apis.migrate_data_to_current;

**Parent topic:** SEM_APIS Package Subprograms

### 15.88 SEM_APIS.MOVE_SEM_NETWORK_DATA

#### Format

    SEM_APIS.MOVE_SEM_NETWORK_DATA(
         dest_schema    IN DBMS_ID,
         dest_tbs_name  IN DBMS_ID DEFAULT NULL,
         degree         IN INTEGER DEFAULT NULL,
         options        IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Moves semantic network data from a source semantic network to a destination (staging) schema.

#### Parameters

dest_schema
The staging schema to which the semantic network data will be moved.

dest_tbs_name
The tablespace to use for objects created in the destination (staging) schema. If null, the default tablespace for the destination schema will be used.

degree
Degree of parallelism to use for any SQL insert or index building operations. The default is no parallel execution.

options
(Reserved for future use.)

network_owner
Owner of the source semantic network for the move operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the source semantic network for the move operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

You must have DBA privileges to call this procedure.

For more information and examples, see [Moving, Restoring, and Appending a Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example moves a semantic network from the MYNET semantic network owned by RDFADMIN to the RDFEXPIMPU staging schema\>

    EXECUTE sem_apis.move_sem_network_data(dest_schema=>'RDFEXPIMPU',network_owner=>'RDFADMIN',network_name=>'MYNET');

**Parent topic:** SEM_APIS Package Subprograms

### 15.89 SEM_APIS.PRIVILEGE_ON_APP_TABLES

#### Format

    SEM_APIS.PRIVILEGE_ON_APP_TABLES(
         command       IN VARCHAR2 DEFAULT 'GRANT',
         privilege     IN VARCHAR2 DEFAULT 'SELECT',
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Grants (or revokes) SELECT or INSERT privilege to (or from) MDSYS on application tables corresponding to all the RDF models owned by the invoker.

#### Parameters

command
SQL statement, with possible values `GRANT` (the default) or `REVOKE` (case insensitive).

privilege
Privilege name, with possible values `SELECT` (the default) or `INSERT` (case insensitive).


network_owner

Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)


network_name

Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example grants SELECT privilege to MDSYS on application tables corresponding to all the RDF models owned by the invoker.

    EXECUTE SEM_APIS.PRIVILEGE_ON_APP_TABLES('grant', 'select');

**Parent topic:** SEM_APIS Package Subprograms

### 15.90 SEM_APIS.PURGE_UNUSED_VALUES

#### Format

    SEM_APIS.PURGE_UNUSED_VALUES(
         flags         IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Purges purges invalid geometry literal values from the semantic network.

#### Parameters

flags
An optional quoted string with one or more of the following keyword specifications:

- `MBV_METHOD=SHADOW` allows the use of a different value loading strategy that may lead to faster processing when a large number of values need to be purged.

- `PARALLEL=``<integer>` allows much of the processing to be done in parallel using the specified `integer` degree of parallelism to be associated with the operation. If only `PARALLEL` is specified without a degree, a default degree will be used.

- `PUV_COMPUTE_VIDS_USED` allows use of a different strategy that may lead to faster processing when most of the values are expected to be purged.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Before calling this procedure, you must grant to MDSYS the SELECT privilege on application tables for all the currently existing RDF models.

For more usage information and an extended example, see [Purging Unused Values](rdf-semantic-graph-overview.md).

It is recommended that you execute this procedure after using SEM_APIS.VALIDATE_GEOMETRIES to check that all geometry literals in the specified model are valid for the provided SRID and tolerance values.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example purges unused values using a degree of parallelism of 4.

    EXECUTE SEM_APIS.PURGE_UNUSED_VALUES(flags => 'PARALLEL=4');

**Parent topic:** SEM_APIS Package Subprograms

### 15.91 SEM_APIS.REFRESH_SEM_NETWORK_INDEX_INFO

#### Format

    SEM_APIS.REFRESH_SEM_NETWORK_INDEX_INFO(
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Refreshes the information about semantic network indexes.

#### Parameters

options
(Reserved for future use)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure updates the information in the SEM_NETWORK_INDEX_INFO view, which is described in [SEM_NETWORK_INDEX_INFO View](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example refreshes the information about semantic network indexes.

    EXECUTE sem_apis.refresh_sem_network_index_info;

**Parent topic:** SEM_APIS Package Subprograms

### 15.92 SEM_APIS.REMOVE_DUPLICATES

#### Format

    SEM_APIS.REMOVE_DUPLICATES(
         model_name           IN VARCHAR2,
         threshold            IN FLOAT DEFAULT 0.3,
         rebuild_apptab_index IN BOOLEAN DEFAULT TRUE,
         options              IN VARCHAR2 DEFAULT NULL,
         network_owner        IN VARCHAR2 DEFAULT NULL,
         network_name         IN VARCHAR2 DEFAULT NULL);

#### Description

Removes duplicate triples from a model.

#### Parameters

model_name
Name of the model.

threshold
A value to determine how numerous triples must be in order for the removal operation to be performed. This procedure removes triples only if the number of triples in the model exceeds the following formula: (total-triples - total-unique-triples + 0.01) / (total-unique-triples + 0.01). For the default value of 0.3 and a model containing 1000 total triples (including duplicates), duplicate triples would be removed only if the number of duplicates exceeds approximately 230.

The lower the threshold value, the fewer duplicates are needed for the procedure to remove duplicates; the higher the threshold value, the more duplicates are needed for the procedure to remove duplicates.

rebuild_apptab_index
`TRUE` (the default) causes all usable indexes on tables that were affected by this operation to be rebuilt after the duplicate triples are removed; `FALSE` does not rebuild any indexes.

options
(Reserved for future use.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

When duplicate triples are removed, all information in the removed rows is lost, including information in columns other than the triple column.

This procedure is not supported on virtual models (explained in [Virtual Models](rdf-semantic-graph-overview.md)).

If the model is empty, or if it contains no duplicate triples or not enough duplicate triples (as computed using the `threshold` value), this procedure does not perform any removal operations.

If there are not enough duplicates (as computed using the `threshold` value) to perform the operation, an informational message is displayed.

If unusable indexes are involved, be sure that the SKIP_UNUSABLE_INDEXES system parameter is set to `TRUE`. Although `TRUE` is the default value for this parameter, some production databases may use the value `FALSE`; therefore, if you need to change it, enter the following:

    SQL> alter session set skip_unusable_indexes=true;

To use this procedure on an application table with one or more user-defined triggers, you must connect as a DBA user and grant the ALTER ANY TRIGGER privilege to the MDSYS user, as follows:

    SQL> grant alter any trigger to MDSYS;

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example removes duplicate triples in the model named `family`. It accepts the default threshold value of 0.3 and (by default) rebuilds indexes after the duplicates are removed.

    EXECUTE SEM_APIS.REMOVE_DUPLICATES('family');

**Parent topic:** SEM_APIS Package Subprograms

### 15.93 SEM_APIS.RENAME_ENTAILMENT

#### Format

    SEM_APIS.RENAME_ENTAILMENT(
         old_name       IN VARCHAR2,
         new_name       IN VARCHAR2,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Renames an entailment (rules index).

#### Parameters

old_name
Name of the existing entailment to be renamed.

new_name
New name for the entailment.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example renames a entailment named `OWLTST_IDX` to `MY_OWLTST_IDX`.

    EXECUTE sem_apis.rename_entailment('owltst_idx', 'my_owltst_idx');

**Parent topic:** SEM_APIS Package Subprograms

### 15.94 SEM_APIS.RENAME_MODEL

#### Format

    SEM_APIS.RENAME_MODEL(
         old_name       IN VARCHAR2,
         new_name       IN VARCHAR2,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Renames a model.

#### Parameters

old_name
Name of the existing model to be renamed.

new_name
New name for the model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

The following considerations apply to the use of this procedure:

- You must be the owner of the existing model.

- This procedure is not supported on virtual models (explained in [Virtual Models](rdf-semantic-graph-overview.md)).

Contrast this procedure with SEM_APIS.SWAP_NAMES, which swaps (exchanges) the names of two existing models.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example renames a model named `MODEL1` to `MODEL2`.

    EXECUTE sem_apis.rename_model('model1', 'model2');

**Parent topic:** SEM_APIS Package Subprograms

### 15.95 SEM_APIS.RES2VID

#### Format

    SEM_APIS.RES2VID(
         vTab     IN VARCHAR2,
         uri   IN VARCHAR2,
         lt   IN VARCHAR2 DEFAULT NULL,
         lang   IN VARCHAR2 DEFAULT NULL,
         lval  IN CLOB DEFAULT NULL,
         ) RETURN NUMBER;

#### Description

Returns the VALUE_ID for the canonical version of an RDF term, or NULL if the term does not exist in the values table.

#### Parameters

vTab
Values table to query for the VALUE_ID value. (Usually RDF_VALUE\$)

uri
Prefix value of the RDF term.

lt
Data type URI of a types literal to look up. Do not include the enclosing angle brackets (‘\<’ and ‘\>’).

lang
Language tag of a language tagged literal to look up.

lval
The plain literal portion of a long literal to look up.

#### Usage Notes

For information about the components of an RDF term stored in the RDF_VALUE\$ table, see [Semantic Metadata Tables and Views](rdf-semantic-graph-overview.md)..

See also [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md).

#### Examples

The following example returns VALUE_ID values for the canonical versions of RDF terms. Comments before each SQL statement describe the purpose of the statement.

    -- Look up the VALUE_ID for the RDF term <http://www.example.com/a>.
    SELECT  sem_apis.res2vid('RDF_VALUE$','<http://www.example.com/a>') FROM DUAL;

    -- Look up the VALUE_ID for the RDF term "abc".
    SELECT sem_apis.res2vid('RDF_VALUE$','"abc"') FROM DUAL;

    -- Look up the VALUE_ID for the RDF term "10"^^<http://www.w3.org/2001/XMLSchema#decimal>.
    SELECT sem_apis.res2vid('RDF_VALUE$','"10"','http://www.w3.org/2001/XMLSchema#decimal') FROM DUAL;

    -- Look up the VALUE_ID for the RDF term "abc"@en.
    SELECT sem_apis.res2vid('RDF_VALUE$','"abc"',lang=>'en') FROM DUAL;

    -- Look up the VALUE_ID for the long literal RDF term '"a CLOB literal"'.
    SELECT sem_apis.res2vid('RDF_VALUE$',null,lval=>'"a CLOB literal"') FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.96 SEM_APIS.RESTORE_SEM_NETWORK_DATA

#### Format

    SEM_APIS.RESTORE_SEM_NETWORK_DATA(
         from_schema    DBMS_ID,
         degree         INTEGER DEFAULT NULL,
         options        VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Restores moved semantic network data from a staging schema back into a source semantic network.

#### Parameters

from_schema
The staging schema that contains moved semantic network data to be restored.

degree
Degree of parallelism to use for any SQL insert or index building operations. The default is no parallel execution.

options
String specifying any options to use during the append operation. Supported options are:

- PURGE=T – drop all remaining semantic network data in the staging schema after the append operation completes.

network_owner
Owner of the destination semantic network for the restore operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the destination semantic network for the restore operation. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Partition exchange operations rather than SQL INSERT statements are used to move most of the data during the append operation, so the staging schema will no longer contain complete semantic network data after the restore operation is complete.

Moved semantic network data can only be restored into the original source semantic network from which it was moved.

You must have DBA privileges to call this procedure.

For more information, see [Moving, Restoring, and Appending a Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example restores a semantic network from the RDFEXPIMPU staging schema into the MYNET semantic network owned by RDFADMIN.

    EXECUTE sem_apis.restore_sem_network_data(from_schema=>'RDFEXPIMPU',network_owner=>'RDFADMIN',network_name=>'MYNET');

**Parent topic:** SEM_APIS Package Subprograms

### 15.97 SEM_APIS.REVOKE_MODEL_ACCESS_PRIV

#### Format

    SEM_APIS.REVOKE_MODEL_ACCESS_PRIV(
         model_name      IN VARCHAR2,
         user_name       IN VARCHAR2,
         privilege       IN VARCHAR2,
         user_view       IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Revokes access privilege on a model or entailment.

#### Parameters

model_name
Name of the model.

user_name
Database user that is recipient of this privilege.

privilege
Specifies the type of privilege that is granted. Currently allowed values include the following:

- `QUERY`: Query the model using SPARQL
- `SELECT`, `READ`: Retrieve model content using SQL. For schema-private network, the source for the content is the `RDFT_<model>` view in the network owner's schema or the view name, if any, specified for the `user_view` parameter. For MDSYS-owned network, the source for the content is the application table.
- `INSERT`, `UPDATE`, `DELETE`: Perform SPARQL Update (DML) operations on the model or SQL DML operations. For SQL DML, the target object is different depending upon the type of network. For schema-private network, it is the `RDFT_<model>` view in the network owner's schema and for MDSYS-owned network, it is the application table.

**Note:**

`QUERY` is the only valid choice if the model is not a regular model (that is, not created using `sem_apis.create_sem_model`).

user_view
Applicable to schema-private network only. If a view was created on the `RDFT_<model>` view at model creation time using `sem_apis.create_sem_model` or later, privilege is revoked on that view.

options
If user specifies the word `ENTAILMENT` as part of the string value, then the specified `model_name` is taken as the name of an entailment (rules index). (Additional words or phrases may be allowed in future.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This does not affect the recipient's query-only or full access to the semantic network (which guarantees access to dictionary tables, but not individual models). This operation revokes access to the specified model only.

#### Examples

The following example revokes privilege from database user `USER1` for use of SPARQL query against a semantic technology model named `articles` in the schema-private network `NET1` owned by database user `RDFUSER`. (This example refers to the model described in [Example 1-121](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.REVOKE_MODEL_ACCESS_PRIV('articles', 'USER1', 'QUERY', network_owner=>'RDFUSER', network_name=>'NET1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.98 SEM_APIS.REVOKE_MODEL_ACCESS_PRIVS

#### Format

    SEM_APIS.REVOKE_MODEL_ACCESS_PRIVS(
         model_name      IN VARCHAR2,
         user_name       IN VARCHAR2,
         priv_list       IN VARCHAR2,
         user_view       IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Revokes access privileges on a model or entailment.

#### Parameters

model_name
Name of the model.

user_name
Database user that is recipient of this privilege.

privilege
Specifies the type of privilege that is granted. Currently allowed values include the following:

- `QUERY`: Query the model using SPARQL
- `SELECT`, `READ`: Retrieve model content using SQL. For schema-private network, the source for the content is the `RDFT_<model>` view in the network owner's schema or the view name, if any, specified for the `user_view` parameter. For MDSYS-owned network, the source for the content is the application table.
- `INSERT`, `UPDATE`, `DELETE`: Perform SPARQL Update (DML) operations on the model or SQL DML operations. For SQL DML, the target object is different depending upon the type of network. For schema-private network, it is the `RDFT_<model>` view in the network owner's schema and for MDSYS-owned network, it is the application table.

**Note:**

`QUERY` is the only valid choice if the model is not a regular model (that is, not created using `sem_apis.create_sem_model`).

user_view
Applicable to schema-private network only. If a view was created on the `RDFT_<model>` view at model creation time using `sem_apis.create_sem_model` or later, privileges are revoked on that view.

options
If user specifies the word `ENTAILMENT` as part of the string value, then the specified `model_name` is taken as the name of an entailment (rules index). (Additional words or phrases may be allowed in future.)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This does not affect the recipient's query-only or full access to the semantic network (which guarantees access to dictionary tables, but not individual models). This operation revokes access to the specified model only.

#### Examples

The following example revokes privilege from database user `USER1` for performing DML operations against a semantic technology model named `articles` in the schema-private network `NET1` owned by database user `RDFUSER`. (This example refers to the model described in [Example 1-121](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.REVOKE_MODEL_ACCESS_PRIVS('articles', 'USER1', sys.odcivarchar2list('INSERT','UPDATE','DELETE'), network_owner=>'RDFUSER', network_name=>'NET1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.99 SEM_APIS.REVOKE_NETWORK_ACCESS_PRIVS

#### Format

    SEM_APIS.REVOKE_NETWORK_ACCESS_PRIVS(
         network_owner  IN VARCHAR2,
         network_name   IN VARCHAR2,
         network_user   IN VARCHAR2,
         options        IN VARCHAR2 default NULL);

#### Description

Revokes access privileges from a database user other than the owner of a schema-private semantic network.

#### Parameters

network_owner
Owner of the network. (Cannot be MDSYS.)

network_name
Name of the network. (Must be a schema-private network.)

network_user
Database user (other than the network owner) from which to revoke access privileges to the network.

options
String specifying options for access using the form OPTION_NAME=option_value.

If `CASCADE=T` is specified, any RDF objects owned by the database user will be dropped as part of this operation.

#### Usage Notes

You must have DBA privileges or be the owner of the specified network to call this procedure.

If the database user (`network_user`) owns any RDF objects in the schema-private network and if `CASCADE=T` is not specified, an error will be raised.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example revokes full access on the `mynet1` network owned by `scott` from `rdfuser1`.

    EXECUTE SEM_APIS.REVOKE_NETWORK_ACCESS_PRIVS('scott','mynet1','rdfuser1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.100 SEM_APIS.REVOKE_NETWORK_SHARING_PRIVS

#### Format

    SEM_APIS.REVOKE_NETWORK_SHARING_PRIVS(
         network_owner  IN VARCHAR2,
         options        IN VARCHAR2 default NULL);

#### Description

Revokes from a database user the privileges required for sharing, with other database users, any schema-private networks owned (currently or in the future) by the database user

#### Parameters

network_owner
Owner of the network. (Cannot be MDSYS.)

options
(Reserved for future use)

#### Usage Notes

You must have DBA privileges to call this procedure.

If the database user owns at least one schema-private network that has sharing enabled, an exception will be raised. (The user must first disable sharing of any such networks.)

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example revokes from database user `scott` the privileges for sharing any schema-private networks that this user owns or will own.

    EXECUTE SEM_APIS.REVOKE_NETWORK_SHARING_PRIVS('scott');

**Parent topic:** SEM_APIS Package Subprograms

### 15.101 SEM_APIS.SET_ENTAILMENT_STATS

#### Format

    SEM_APIS.SET_ENTAILMENT_STATS (
         entailment_name IN VARCHAR2,
         numrows         IN NUMBER DEFAULT NULL,
         numblks         IN NUMBER DEFAULT NULL,
         avgrlen         IN NUMBER DEFAULT NULL,
         flags           IN NUMBER DEFAULT NULL,
         no_invalidate   IN BOOLEAN DEFAULT DBMS_STATS.AUTO_INVALIDATE,
         cachedblk       IN NUMBER DEFAULT NULL,
         cachehit        IN NUMBER DEFAULT NULL,
         force           IN BOOLEAN DEFAULT FALSE,
         network_owner   IN VARCHAR2 DEFAULT NULL,
         network_name    IN VARCHAR2 DEFAULT NULL);

#### Description

Sets statistics for a specified entailment.

#### Parameters

entailment_name
Name of the entailment.

(other parameters)
See the parameter explanations for the [DBMS_STATS.SET_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to entailment statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets statistics for an entailment named `OWLTST_IDX`.

    EXECUTE SEM_APIS.SET_ENTAILMENT_STATS('owltst_idx', numrows => 100);

**Parent topic:** SEM_APIS Package Subprograms

### 15.102 SEM_APIS.SET_MODEL_STATS

#### Format

    SEM_APIS.SET_MODEL_STATS (
         model_name     IN VARCHAR2,
         numrows        IN NUMBER DEFAULT NULL,
         numblks        IN NUMBER DEFAULT NULL,
         avgrlen        IN NUMBER DEFAULT NULL,
         flags          IN NUMBER DEFAULT NULL,
         no_invalidate  IN BOOLEAN DEFAULT DBMS_STATS.AUTO_INVALIDATE,
         cachedblk      IN NUMBER DEFAULT NULL,
         cachehit       IN NUMBER DEFAULT NULL,
         force          IN BOOLEAN DEFAULT FALSE,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Sets statistics for a specified model.

#### Parameters

model_name
Name of the model.

(other parameters)
See the parameter explanations for the [DBMS_STATS.DELETE_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to model statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example sets statistics for a model named `FAMILY`.

    EXECUTE SEM_APIS.SET_MODEL_STATS('family', numrows => 100);

**Parent topic:** SEM_APIS Package Subprograms

### 15.103 SEM_APIS.SPARQL_TO_SQL

#### Format

    SEM_APIS.SPARQL_TO_SQL(
        sparql_query  IN CLOB,
        models        IN RDF_MODELS DEFAULT NULL,
        rulebases     IN RDF_RULEBASES DEFAULT NULL,
        aliases       IN RDF_ALIASES DEFAULT NULL,
        index_status  IN VARCHAR2 DEFAULT NULL,
        options       IN VARCHAR2 DEFAULT NULL
        graphs        IN RDF_GRAPHS DEFAULT NULL,
        named_graphs  IN RDF_GRAPHS DEFAULT NULL,
        network_owner IN VARCHAR2 DEFAULT NULL,
        network_name  IN VARCHAR2 DEFAULT NULL) RETURN CLOB;

#### Description

Translates a SPARQL query into a SQL query string that can be executed by an application programl.

#### Parameters

sparql_query
A string literal with one or more triple patterns, usually containing variables.

models
The model or models to use.

rulebases
One or more rulebases whose rules are to be applied to the query

aliases
One or more namespaces to be used for expansion of qualified names in the query pattern.

index_status
The status of the relevant entailment for this query.

options
Options that can affect the results of queries.

graphs
The set of named graphs from which to construct the default graph for the query.

named_graphs
The set of named graphs that can be matched by a GRAPH clause.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Before using this procedure, be sure you understand the material in [Using the SEM_APIS.SPARQL_TO_SQL Function to Query Semantic Data](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example translates a SPARQL query into a SQL query string.

    DECLARE
      sparql_stmt clob;
      sql_stmt    clob;
    BEGIN
      sparql_stmt := '{?x :grandParentOf ?y . ?x rdf:type :Male}';
      sql_stmt := sem_apis.sparql_to_sql(
                    sparql_stmt,
                    sem_models('family'),
                    SEM_Rulebases('RDFS','family_rb'),
                    SEM_ALIASES(SEM_ALIAS('','http://www.example.org/family/')),
                    null);
      execute immediate
        'create table gf_table as
         select x grandfather, y grandchild from('|| sql_stmt || ')';
    END;
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.104 SEM_APIS.SWAP_NAMES

#### Format

    SEM_APIS.SWAP_NAMES(
         model1         IN VARCHAR2,
         model2         IN VARCHAR2,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Swaps (exchanges) the names of two existing models.

#### Parameters

model1
Name of a model.

model2
Name of another model.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

As a result of this procedure, the name of model `model1` is changed to the (old) name of `model2`, and the name of model `model2` is changed to the (old) name of `model1`.

The order of the names does not affect the result. For example, you could specify `TEST` for `model1` and `PRODUCTION` for `model2`, or `PRODUCTION` for `model1` and `TEST` for `model2`, and the result will be the same.

Contrast this procedure with SEM_APIS.RENAME_MODEL, which renames an existing model.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example changes the name of the (old) TEST model to PRODUCTION, and the name of the (old) PRODUCTION model to TEST.

    EXECUTE sem_apis.swap_names('test', 'production');

**Parent topic:** SEM_APIS Package Subprograms

### 15.105 SEM_APIS.TRUNCATE_SEM_MODEL

#### Format

    SEM_APIS.TRUNCATE_SEM_MODEL(
         model_name    IN VARCHAR2,
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Truncates a semantic technology model.

#### Parameters

model_name
Name of the model.

options
(Reserved for future use)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure removes all triples and quads from the specified semantic model. For an MDSYS-owned network, it also truncates the corresponding application table.

For a schema-private network, this is the only supported way to truncate a model. For the MDSYS-owned network, you can truncate the model by using this procedure or by truncating the corresponding application table.

To delete a model, use the SEM_APIS.DROP_SEM_MODEL procedure.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example truncates a semantic technology model named `articles`. (This example refers to the model described in [Example 1-121](rdf-semantic-graph-overview.md).)

    EXECUTE SEM_APIS.TRUNCATE_SEM_MODEL('articles', NULL, network_owner=>'RDFUSER', network_name=>'NET1');

**Parent topic:** SEM_APIS Package Subprograms

### 15.106 SEM_APIS.UNESCAPE_CLOB_TERM

#### Format

    SEM_APIS.UNESCAPE_CLOB_TERM(
         term  IN CLOB CHARACTER SET ANY_CS
         ) RETURN CLOB CHARACTER SET val%CHARSET;

#### Description

Returns the input RDF term with special characters and non-ASCII characters unescaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

term
The RDF term to unescape.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example unescapes an input RDF term containing TAB and NEWLINE characters.

    SEM_APIS.UNESCAPE_CLOB_TERM('"abc\tdef\nhij"^^<http://www.w3.org/2001/XMLSchema#string>')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.107 SEM_APIS.UNESCAPE_CLOB_VALUE

#### Format

    SEM_APIS.UNESCAPE_CLOB_VALUE(
         val           IN  CLOB CHARACTER SET ANY_CS,
         start_offset  IN NUMBER DEFAULT 1,
         end_offset    IN NUMBER DEFAULT 0,
         include_start IN NUMBER DEFAULT 0
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input CLOB value with special characters and non-ASCII characters unescaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

val
The CLOB text to unescape.

start_offset
The offset in `val` from which to start character unescaping. The default (1) causes escaping to start at the first character of `val`.

end_offset
The offset in `val` from which to end character unescaping. The default (0) causes escaping to continue through the end of `val`.

include_start
Set to 1 if the characters in val from 1 to `start_offset` should be prefixed (prepended) to the return value. Otherwise, no such characters will be prefixed to the return value.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example unescapes an input character string containing TAB and NEWLINE characters.

    SELECT SEM_APIS.UNESCAPE_CLOB_VALUE('abc\tdef\nhij')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.108 SEM_APIS.UNESCAPE_RDF_TERM

#### Format

    SEM_APIS.UNESCAPE_RDF_TERM(
         term  IN VARCHAR2 CHARACTER SET ANY_CS
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input RDF term with special characters and non-ASCII characters unescaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

term
The RDF term to unescape.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example unescapes an input RDF term containing TAB and NEWLINE characters.

    SELECT SEM_APIS.UNESCAPE_RDF_TERM('"abc\tdef\nhij"^^<http://www.w3.org/2001/XMLSchema#string>')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.109 SEM_APIS.UNESCAPE_RDF_VALUE

#### Format

    SEM_APIS.UNESCAPE_RDF_VALUE(
         val  IN VARCHAR2 CHARACTER SET ANY_CS
         ) RETURN VARCHAR2 CHARACTER SET val%CHARSET;

#### Description

Returns the input CLOB value with special characters and non-ASCII characters unescaped as specified by the W3C N-Triples format ([`http://www.w3.org/TR/rdf-testcases/#ntriples`](http://www.w3.org/TR/rdf-testcases/#ntriples)).

#### Parameters

val
The text to unescape.

utf_encode
Set to 1 (the default) if non-ASCII characters and non-printable ASCII characters other than chr(8), chr(9), chr(10), chr(12), and chr(13) should be escaped. Otherwise, such characters will not be escaped.

#### Usage Notes

For information about using the `DO_UNESCAPE` keyword in the `options` parameter of the SEM_MATCH table function, see [Using the SEM_MATCH Table Function to Query Semantic Data](rdf-semantic-graph-overview.md).

#### Examples

The following example unescapes an input character string containing TAB and NEWLINE characters.

    SELECT SEM_APIS.UNESCAPE_RDF_VALUE('abc\tdef\nhij')
      FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.110 SEM_APIS.UPDATE_MODEL

#### Format

    SEM_APIS.UPDATE_MODEL(
         apply_model         IN VARCHAR2,
         update_stmt         IN CLOB,
         match_models        IN RDF_MODELS DEFAULT NULL,
         match_rulebases     IN RDF_RULEBASES DEFAULT NULL,
         match_index_status  IN VARCHAR2 DEFAULT NULL,
         match_options       IN VARCHAR2 DEFAULT NULL,
         options             IN VARCHAR2 DEFAULT NULL,
         network_owner       IN VARCHAR2 DEFAULT NULL,
         network_name        IN VARCHAR2 DEFAULT NULL);

#### Description

Executes a SPARQL Update statement on a semantic model.

#### Parameters

apply_model
Name of the RDF model to be updated. This is the name specified when the model was created using the SEM_APIS.CREATE_SEM_MODEL procedure.

It cannot be a virtual model (see [Virtual Models](rdf-semantic-graph-overview.md)) or an RDF view).

update_stmt
One or more SPARQL Update commands to be executed on the `apply_model` model. Use the semicolon (;) to separate commands.

match_models
A list of models that forms the SPARQL data set to query for graph pattern matching during a SPARQL Update operation (INSERT WHERE, DELETE WHERE, COPY, MOVE, ADD). Can include virtual models and/or RDF views If this parameter is not specified, the `apply_model` model is used.

match_rulebases
A list of rulebases to use with `match_models` to provide an entailment that generates additional triples or quads to use for graph pattern matching during a SPARQL Update operation.

match_index_status
The desired status for any entailments used for graph pattern matching during a SPARQL Update operation.

match_options
String specifying hints to influence graph pattern matching during a SPARQL Update operation. The set of hints that can be used here is identical to those that can be used in the `options` parameter of SEM_MATCH.

options
String specifying hints that affect SPARQL operations. See the Usage Notes for a list of available options.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

Before using this procedure, be sure you understand the material in [Support for SPARQL Update Operations on a Semantic Model](rdf-semantic-graph-overview.md).

The `options` parameter can specify one or more of the following options:

- APP_TAB_IDX={INDEX_NAME} uses an INDEX optimizer hint for INDEX_NAME when doing DML operations on the application table.

- APPEND uses the SQL APPEND hint with DML operations.

- AUTOCOMMIT=F avoids starting and committing a transaction for each SEM_APIS.UPDATE_MODEL call. Instead, this option gives transaction control to the caller. Each SEM_APIS.UPDATE_MODEL call will execute as part of a main transaction that is started, committed, or rolled back by the caller.

- BULK_OPTIONS={OPTIONS_STRING} uses OPTIONS_STRING as the `flags` parameter when calling SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE.

- CLOB_UPDATE_SUPPORT=T turns on CLOB functionality.

- DEL_AS_INS=T performs a large delete operation by inserting all data that should remain after the delete operation instead of doing deletions. This option may significantly improve the performance of large delete operations.

- DYNAMIC_SAMPLING(n) uses DYNAMIC_SAMPLING(n) SQL optimizer hint with query operations.

- FORCE_BULK=T uses the SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE procedure for bulk insertion of triples. This option may provide better performance on large updates.

- LOAD_CLOB_ONLY=T loads only triples/quads with object values longer than 4000 bytes in length when executing LOAD operations on N-Triple or N-Quad documents.

- LOAD_OPTIONS={ OPTIONS_STRING } uses `OPTIONS_STRING` as the extra file names when performing a LOAD operation.

- MM_OPTIONS={ OPTIONS_STRING } uses OPTIONS_STRING as the options parameter for operations calling SEM_APIS.MERGE_MODELS.

- PARALLEL(n) uses the SQL `PARALLEL(n)` hint for query and DML operations.

- RESUME_LOAD=T allows resuming an interrupted LOAD operation.

- SERIALIZABLE=T uses the SERIALIZABLE transaction isolation level for SEM_APIS.UPDATE_MODEL operations. READ COMMITTED is the default transaction isolation level.

- STREAMING=F materializes intermediate data and uses INSERT AS SELECT operations instead of streaming through JDBC Result Sets. This mode may provide better performance on large updates or updates with complex patterns in the WHERE clause.

- STRICT_BNODE=F enables ID-only operations for ADD, COPY, and MOVE. (ID-only operations are explained in [Blank Nodes: Special Considerations for SPARQL Update](rdf-semantic-graph-overview.md).)

You can override some options settings at the session level by using the MDSYS.SDO_SEM_UPDATE_CTX.SET_PARAM procedure, as explained in [Setting UPDATE_MODEL Options at the Session Level](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example inserts six triples into a semantic model.

    BEGIN
      sem_apis.update_model('electronics',
       'PREFIX : <http://www.example.org/electronics/>
        INSERT DATA {
           :camera1 :name "Camera 1" .
           :camera1 :price 120 .
           :camera1 :cameraType :Camera .
           :camera2 :name "Camera 2" .
           :camera2 :price 150 .
           :camera2 :cameraType :Camera .
          } ');
    END;
    /

**Parent topic:** SEM_APIS Package Subprograms

### 15.111 SEM_APIS.VALIDATE_ENTAILMENT

#### Format

    SEM_APIS.VALIDATE_ENTAILMENT(
         models_in      IN SEM_MODELS,
         rulebases_in   IN SEM_RULEBASES,
         criteria_in    IN VARCHAR2 DEFAULT NULL,
         max_conflict   IN NUMBER DEFAULT 100,
         options        IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL
         ) RETURN RDF_LONGVARCHARARRAY;

#### Description

Validates entailments (rules indexes) that can be used to perform OWL or RDFS inferencing for one or more models.

#### Parameters

models_in
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

rulebases_in
One or more rulebase names. Its data type is SEM_RULEBASES, which has the following definition: `TABLE OF VARCHAR2(25)`. Rules and rulebases are explained in [Inferencing: Rules and Rulebases](rdf-semantic-graph-overview.md).

criteria_in
A comma-delimited string of validation checks to run. If you do not specify this parameter, by default all of the following checks are run:

- `UNSAT`: Find unsatisfiable classes.

- `EMPTY`: Find instances that belong to unsatisfiable classes.

- `SYNTAX_S`: Find triples whose subject is neither URI nor blank node.

- `SYNTAX_P`: Find triples whose predicate is not URI.

- `SELF_DIF`: Find individuals that are different from themselves.

- `INST`: Find individuals that simultaneously belong to two disjoint classes.

- `SAM_DIF`: Find pairs of individuals that are same (owl:sameAs) and different (owl:differentFrom) at the same time.

To specify fewer checks, specify a string with only the checks to be performed. For example, `criteria_in => 'UNSAT'` causes the validation process to search only for unsatisfiable classes.

max_conflict
The maximum number of conflicts to find before the validation process stops. The default value is 100.

options
(Not currently used. Reserved for Oracle use.).

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure can be used to detect inconsistencies in the original entailment. For more information, see [Validating OWL Models and Entailments](owl-concepts.md).

This procedure returns a null value if no errors are detected or (if errors are detected) an object of type RDF_LONGVARCHARARRAY, which has the following definition: `VARRAY(32767) OF VARCHAR2(4000)`

To create an entailment, use the SEM_APIS.CREATE_ENTAILMENT procedure.

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

For an example of this procedure, see [Example 3-5](owl-concepts.md) in [Validating OWL Models and Entailments](owl-concepts.md).

**Parent topic:** SEM_APIS Package Subprograms

### 15.112 SEM_APIS.VALIDATE_GEOMETRIES

#### Format

    SEM_APIS.VALIDATE_GEOMETRIES(
         model_name      IN VARCHAR2,
         SRID            IN NUMBER,
         tolerance       IN NUMBER,
         parallel        IN PLS_INTEGER DEFAULT NULL,
         tablespace_name IN VARCHAR2 DEFAULT NULL,
         options         IN VARCHAR2 DEFAULT NULL,
         network_owner  IN VARCHAR2 DEFAULT NULL,
         network_name   IN VARCHAR2 DEFAULT NULL);

#### Description

Determines if all geometry literals in the specified model are valid for the provided SRID and tolerance values.

#### Parameters

model_name
Name of the model containing geometry literals to validate. Only native models can be specified.

SRID
SRID for the spatial reference system.

tolerance
Tolerance value that should be used for validation.

parallel
Degree of parallelism to be associated with the operation. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

tablespace_name
Destination tablespace for the tables {model_name}\_IVG\$, {model_name}\_FXT\$, and {model_name}\_NFT\$.

options
String specifying options for validation. Supported options are:

- RECTIFY=T. Staging tables {model_name}\_FXT\$ and {model_name}\_NFT\$ are created, containing rectifiable and non-rectifiable triples, respectively. You can use these tables to correct the model.

- AUTOCORRECT=T. Triples containing invalid but rectifiable geometries are corrected. Also, table {model_name}\_NFT\$ containing triples with non-rectifiable geometries is created so that you can correct such triples manually.

- STANDARD_CRS_URI=T. Use standard CRS (coordinate reference systems) URIs.

- GML_LIT_SRL=T. Use ogc:gmlLiteral serialization for corrected geometry literals. ogc:wktLiteral serialization is the default.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

This procedure is a wrapper for [SDO_GEOM.VALIDATE_GEOMETRY_WITH_CONTEXT](../spatl/SDO_GEOM-reference.md) function.

A table {model_name}\_IVG\$ containing invalid WKT literals is created. Optionally, staging tables {model_name}\_FXT\$ and {model_name}\_NFT\$ can be created, containing rectifiable and non-rectifiable triples, respectively. Staging tables allow the user to correct invalid geometries. Invalid but rectifiable geometry literals in a model can also be rectified automatically if specified.

After correction of invalid geometries in a model, it is recommended that you execute SEM_APIS.PURGE_UNUSED_VALUES to purge invalid geometry literal values from the semantic network.

For an explanation of models, see [Semantic Data Modeling](rdf-semantic-graph-overview.md) and [Semantic Data in the Database](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example creates a model with some invalid geometry literals and then validates the model using the `RECTIFY=T` and `STANDARD_CRS_URI=T` options.

    -- Create model
    CREATE TABLE atab (id int, tri sdo_rdf_triple_s);
    GRANT INSERT ON atab TO mdsys;
    EXEC sem_apis.create_sem_model('m','atab','tri');

    -- Insert invalid geometries
    -- Duplicated coordinates - rectifiable
    insert into atab(tri) values (sdo_rdf_triple_s('m','<http://my.org/geom1>', '<http://www.opengis.net/rdf#asWKT>', '"POLYGON((1.0 2.0, 3.0 2.0, 1.0 4.0, 1.0 2.0, 1.0 2.0))"^^<http://xmlns.oracle.com/rdf/geo/WKTLiteral>'));
    -- Boundary is not closed – rectifiable
    insert into atab(tri) values (sdo_rdf_triple_s('m','<http://my.org/geom2>', '<http://www.opengis.net/rdf#asWKT>', '"POLYGON((1.0 2.0, 3.0 2.0, 3.0 4.0, 1.0 4.0))"^^<http://xmlns.oracle.com/rdf/geo/WKTLiteral>'));
    -- Less than 4 points – non rectifiable
    insert into atab(tri) values (sdo_rdf_triple_s('m:<http://my.org/g2>','<http://my.org/geom3>', '<http://www.opengis.net/rdf#asWKT>', '"POLYGON((1.0 2.0, 3.0 2.0, 1.0 4.0))"^^<http://xmlns.oracle.com/rdf/geo/WKTLiteral>'));
    commit;

    -- Validate
    EXEC sem_apis.validate_geometries(model_name=>'m',SRID=>8307,tolerance=>1.0, options=>'STANDARD_CRS_URI=T RECTIFY=T');

    -- Check invalid geometries
    SELECT original_vid, error_msg, corrected_geom_literal FROM M_IVG$;

    -- Check rectified triples
    select RDF$STC_GRAPH, RDF$STC_SUB, RDF$STC_PRED, RDF$STC_OBJ from M_FXT$;

    -- Check non-rectified triples
    select RDF$STC_GRAPH, RDF$STC_SUB, RDF$STC_PRED, RDF$STC_OBJ, ERROR_MSG from M_NFT$;

**Parent topic:** SEM_APIS Package Subprograms

### 15.113 SEM_APIS.VALIDATE_MODEL

#### Format

    SEM_APIS.VALIDATE_MODEL(
         models_in    IN SEM_MODELS,
         criteria_in  IN VARCHAR2 DEFAULT NULL,
         max_conflict IN NUMBER DEFAULT 100,
         options      IN VARCHAR2 DEFAULT NULL
         ) RETURN RDF_LONGVARCHARARRAY;

#### Description

Validates one or more models.

#### Parameters

models_in
One or more model names. Its data type is SEM_MODELS, which has the following definition: `TABLE OF VARCHAR2(25)`

criteria_in
A comma-delimited string of validation checks to run. If you do not specify this parameter, by default all of the following checks are run:

- `UNSAT`: Find unsatisfiable classes.

- `EMPTY`: Find instances that belong to unsatisfiable classes.

- `SYNTAX_S`: Find triples whose subject is neither URI nor blank node.

- `SYNTAX_P`: Find triples whose predicate is not URI.

- `SELF_DIF`: Find individuals that are different from themselves.

- `INST`: Find individuals that simultaneously belong to two disjoint classes.

- `SAM_DIF`: Find pairs of individuals that are same (owl:sameAs) and different (owl:differentFrom) at the same time.

To specify fewer checks, specify a string with only the checks to be performed. For example, `criteria_in => 'UNSAT'` causes the validation process to search only for unsatisfiable classes.

max_conflict
The maximum number of conflicts to find before the validation process stops. The default value is 100.

options
(Not currently used. Reserved for Oracle use.).

#### Usage Notes

This procedure can be used to detect inconsistencies in the original data model. For more information, see [Validating OWL Models and Entailments](owl-concepts.md).

This procedure returns a null value if no errors are detected or (if errors are detected) an object of type RDF_LONGVARCHARARRAY, which has the following definition: `VARRAY(32767) OF VARCHAR2(4000)`

#### Examples

The following example validates the model named `family`.

    SELECT SEM_APIS.VALIDATE_MODEL(SEM_MODELS('family')) FROM DUAL;

**Parent topic:** SEM_APIS Package Subprograms

### 15.114 SEM_APIS.VALUE_NAME_PREFIX

#### Format

    SEM_APIS.VALUE_NAME_PREFIX (
         value_name  IN VARCHAR2,
         value_type  IN VARCHAR2
         ) RETURN VARCHAR2;

#### Description

Returns the value in the VNAME_PREFIX column for the specified value name and value type pair in the RDF_VALUE\$ table.

#### Parameters

value_name
Value name. Must match a value in the VALUE_NAME column in the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

value_type
Value type. Must match a value in the VALUE_TYPE column in the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

#### Usage Notes

This function usually causes an index on the RDF_VALUE\$ table to be used for processing a lookup for values, and thus can make a query run faster.

#### Examples

The following query returns value name portions of all the lexical values in RDF_VALUE\$ table with a prefix value same as that returned by the VALUE_NAME_PREFIX function. This query uses an index on the RDF_VALUE\$ table, thereby providing efficient lookup.

    SELECT value_name FROM RDF_VALUE$
      WHERE vname_prefix = SEM_APIS.VALUE_NAME_PREFIX(
        'http://www.w3.org/1999/02/22-rdf-syntax-ns#type','UR');

    VALUE_NAME
    --------------------------------------------------------------------------------
    http://www.w3.org/1999/02/22-rdf-syntax-ns#Alt
    http://www.w3.org/1999/02/22-rdf-syntax-ns#Bag
    http://www.w3.org/1999/02/22-rdf-syntax-ns#List
    http://www.w3.org/1999/02/22-rdf-syntax-ns#Property
    http://www.w3.org/1999/02/22-rdf-syntax-ns#Seq
    http://www.w3.org/1999/02/22-rdf-syntax-ns#Statement
    http://www.w3.org/1999/02/22-rdf-syntax-ns#XMLLiteral
    http://www.w3.org/1999/02/22-rdf-syntax-ns#first
    http://www.w3.org/1999/02/22-rdf-syntax-ns#nil
    http://www.w3.org/1999/02/22-rdf-syntax-ns#object
    http://www.w3.org/1999/02/22-rdf-syntax-ns#predicate
    http://www.w3.org/1999/02/22-rdf-syntax-ns#rest
    http://www.w3.org/1999/02/22-rdf-syntax-ns#subject
    http://www.w3.org/1999/02/22-rdf-syntax-ns#type
    http://www.w3.org/1999/02/22-rdf-syntax-ns#value

    15 rows selected.

**Parent topic:** SEM_APIS Package Subprograms

### 15.115 SEM_APIS.VALUE_NAME_SUFFIX

#### Format

    SEM_APIS.VALUE_NAME_SUFFIX (
         value_name  IN VARCHAR2,
         value_type  IN VARCHAR2
         ) RETURN VARCHAR2;

#### Description

Returns the value in the VNAME_SUFFIX column for the specified value name and value type pair in the RDF_VALUE\$ table.

#### Parameters

value_name
Value name. Must match a value in the VALUE_NAME column in the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

value_type
Value type. Must match a value in the VALUE_TYPE column in the RDF_VALUE\$ table, which is described in [Statements](rdf-semantic-graph-overview.md).

#### Usage Notes

This function usually causes an index on the RDF_VALUE\$ table to be used for processing a lookup for values, and thus can make a query run faster.

#### Examples

The following query returns value name portions of all the lexical values in RDF_VALUE\$ table with a suffix value same as that returned by the VALUE_NAME_SUFFIX function. This query uses an index on the RDF_VALUE\$ table, thereby providing efficient lookup.

    SELECT value_name FROM RDF_VALUE$
      WHERE vname_suffix = SEM_APIS.VALUE_NAME_SUFFIX(
        'http://www.w3.org/1999/02/22-rdf-syntax-ns#type','UR');

    VALUE_NAME
    --------------------------------------------------------------------------------
    http://www.w3.org/1999/02/22-rdf-syntax-ns#type

**Parent topic:** SEM_APIS Package Subprograms
