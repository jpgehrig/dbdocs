## 17  SEM_PERF Package Subprograms

The SEM_PERF package contains subprograms for examining and enhancing the performance of the Resource Description Framework (RDF) and Web Ontology Language (OWL) support in an Oracle database.

To use the subprograms in this chapter, you must understand the conceptual and usage information in [RDF Semantic Graph Overview](rdf-semantic-graph-overview.md) and [OWL Concepts](owl-concepts.md).

This chapter provides reference information about the subprograms, listed in alphabetical order.

- SEM_PERF.ANALYZE_AUX_TABLES
- SEM_PERF.DELETE_NETWORK_STATS
- SEM_PERF.DROP_EXTENDED_STATS
- SEM_PERF.EXPORT_NETWORK_STATS
- SEM_PERF.GATHER_STATS
- SEM_PERF.IMPORT_NETWORK_STATS

**Parent topic:** [Reference Information](part-ref-supp.md)

### 17.1 SEM_PERF.ANALYZE_AUX_TABLES

#### Format

    SEM_PERF.ANALYZE_AUX_TABLES(
         model_name       IN VARCHAR2,
         estimate_percent IN NUMBER DEFAULT DBMS_STATS.AUTO_SAMPLE_SIZE,
         method_opt       IN VARCHAR2 DEFAULT NULL,
         degree           IN NUMBER DEFAULT DBMS_STATS.AUTO_DEGREE,
         network_owner    IN DBMS_ID  DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Analyzes all the SPM tables currently present for the given RDF model.

#### Parameters

model_name
Name of the RDF model.

estimate_percent
Determines the percentage of rows to sample. For more information on gathering the `estimate_percent` statistics, see [DBMS_STATS.GATHER_TABLE_STATS](../arpls/DBMS_STATS.md) procedure.

method_opt
Determines the column statistics collection. For more information on gathering the column statistics, see [DBMS_STATS.GATHER_TABLE_STATS](../arpls/DBMS_STATS.md)

degree
Determines the degree of parallelism used for gathering statistics. For more information on this procedure parameter see [DBMS_STATS.GATHER_TABLE_STATS](../arpls/DBMS_STATS.md)

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

#### Examples

The following example gathers statistics for SPM auxiliary tables.

    EXECUTE SEM_PERF.ANALYZE_AUX_TABLES('m1',network_owner=>'RDFUSER',network_name=>'NET1');

**Parent topic:** SEM_PERF Package Subprograms

### 17.2 SEM_PERF.DELETE_NETWORK_STATS

#### Format

    SEM_PERF.DELETE_NETWORK_STATS (
         cascade_parts    IN BOOLEAN DEFAULT TRUE,
         cascade_columns  IN BOOLEAN DEFAULT TRUE,
         cascade_indexes  IN BOOLEAN DEFAULT TRUE,
         no_invalidate    IN BOOLEAN DEFAULT DBMS_STATS.AUTO_INVALIDATE,
         force            IN BOOLEAN DEFAULT FALSE,
         options          IN VARCHAR2 DEFAULT NULL,
         network_owner    IN VARCHAR2 DEFAULT NULL,
         network_name     IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes statistics for the semantic network.

#### Parameters

options
Controls the scope of the operation:

- If `MDSYS.SDO_RDF.VALUE_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_VALUE\$ table.

- If `MDSYS.SDO_RDF.LINK_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_LINK\$ table.

- If null (the default), the operation applies to both the MDSYS.RDF_VALUE\$ and MDSYS.RDF_LINK\$ tables.

(other parameters)
See the parameter explanations for the [DBMS_STATS.DELETE_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to network statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example deletes statistics for the semantic network:

    EXECUTE SEM_APIS.DELETE_NETWORK_STATS;

**Parent topic:** SEM_PERF Package Subprograms

### 17.3 SEM_PERF.DROP_EXTENDED_STATS

#### Format

    SEM_PERF.DROP_EXTENDED_STATS (
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Drops column groups used for extended optimizer statistics on the RDF_LINK\$ table.

#### Parameters

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must connect as a user with permission to execute it. By default, when Spatial and Graph is installed as part of Oracle Database, only the MDSYS user can execute this procedure; however, execution permission on this procedure can be granted to users as needed.

The default column groups that will be dropped from RDF_LINK\$ are: `(CANON_END_NODE_ID, START_NODE_ID) (P_VALUE_ID, CANON_END_NODE_ID) (P_VALUE_ID, START_NODE_ID)`

See also:

- [Dropping Extended Statistics at the Network Level](rdf-semantic-graph-overview.md)

- The information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) in Oracle Database PL/SQL Packages and Types Reference

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example drops extended statistics for the semantic network:

    EXECUTE SEM_PERF.DROP_EXTENDED_STATS;

**Parent topic:** SEM_PERF Package Subprograms

### 17.4 SEM_PERF.EXPORT_NETWORK_STATS

#### Format

    SEM_PERF.EXPORT_NETWORK_STATS (
         stattab        IN VARCHAR2,
         statid         IN VARCHAR2 DEFAULT NULL,
         cascade        IN BOOLEAN DEFAULT TRUE,
         statown        IN VARCHAR2 DEFAULT NULL,
         stat_category  IN VARCHAR2 DEFAULT 'OBJECT_STATS',
         options        IN VARCHAR2 DEFAULT NULL);

#### Description

Exports the statistics for the semantic network and stores them in the user statistics table.

#### Parameters

options
Controls the scope of the operation:

- If `MDSYS.SDO_RDF.VALUE_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_VALUE\$ table.

- If `MDSYS.SDO_RDF.LINK_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_LINK\$ table.

- If null (the default), the operation applies to both the MDSYS.RDF_VALUE\$ and MDSYS.RDF_LINK\$ tables.

(other parameters)
See the parameter explanations for the [DBMS_STATS.EXPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example exports the statistics for the semantic network and stores them in a table named `STAT_TABLE`.

    EXECUTE SEM_APIS.EXPORT_NETWORK_STATS('stat_table');

**Parent topic:** SEM_PERF Package Subprograms

### 17.5 SEM_PERF.GATHER_STATS

#### Format

    SEM_PERF.GATHER_STATS(
         just_on_values_table  IN BOOLEAN DEFAULT FALSE,
         degree                IN NUMBER(38) DEFAULT NULL,
         estimate_percent      IN NUMBER DEFAULT DBMS_STATS.AUTO_SAMPLE_SIZE,
         value_method_opt      IN VARCHAR2 DEFAULT NULL,
         link_method_opt       IN VARCHAR2 DEFAULT NULL,
         network_owner         IN VARCHAR2 DEFAULT NULL,
         network_name          IN VARCHAR2 DEFAULT NULL);

#### Description

Gathers statistics about RDF and OWL tables and their indexes.

#### Parameters

just_on_values_table
`TRUE` collects statistics only on the table containing the lexical values of triples; `FALSE` (the default) collects statistics on all major tables related to the storage of RDF and OWL data.

A value of `TRUE` reduces the execution time for the procedure; and it may be sufficient if you need only to collect statistics on the values table (for example, if you use other interfaces to collect any other statistics that you might need).

degree
Degree of parallelism. For more information about parallel execution, see [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md).

estimate_percent
Determines the percentage of rows in MDSYS.RDF_LINK\$ and MDSYS.RDF_VALUE\$ to sample.

The valid range is between 0.000001 and 100. You can use the constant `DBMS_STATS.AUTO_SAMPLE_SIZE` (the default) to enable Oracle Database to determine the appropriate sample size for optimal statistics.

value_method_opt
Accepts either of the following options, or both in combination, for the MDSYS.RDF_VALUE\$ table:

- `FOR ALL [INDEXED | HIDDEN] COLUMNS [size_clause]`

- `FOR COLUMNS [size clause] column|attribute [size_clause] [,column|attribute [size_clause]...]`

`size_clause` is defined as: `size_clause := SIZE {integer | REPEAT | AUTO | SKEWONLY}`

`column` is defined as: `column := column_name | (extension)`

- `integer` : Number of histogram buckets. Must be in the range \[1, 2048\].

- `REPEAT` : Collects histograms only on the columns that already have histograms.

- `AUTO` : Oracle Database determines the columns to collect histograms based on data distribution and the workload of the columns.

- `SKEWONLY` : Oracle Database determines the columns to collect histograms based on the data distribution of the columns.

- `column_name` : name of a column

- `extension`: Can be either a column group in the format of (column_name, column_name \[, ...\]) or an expression.

The usual default is: `FOR ALL COLUMNS SIZE 2048`

link_method_opt
Accepts either of the following options, or both in combination, for the MDSYS.RDF_LINK\$ table:

- `FOR ALL [INDEXED | HIDDEN] COLUMNS [size_clause]`

- `FOR COLUMNS [size clause] column|attribute [size_clause] [,column|attribute [size_clause]...]`

`size_clause` is defined as: `size_clause := SIZE {integer | REPEAT | AUTO | SKEWONLY}`

`column` is defined as: `column := column_name | (extension)`

- `integer` : Number of histogram buckets. Must be in the range \[1,254\].

- `REPEAT` : Collects histograms only on the columns that already have histograms.

- `AUTO` : Oracle Database determines the columns to collect histograms based on data distribution and the workload of the columns.

- `SKEWONLY` : Oracle Database determines the columns to collect histograms based on the data distribution of the columns.

- `column_name` : Name of a column.

- `extension`: Can be either a column group in the format of `(column_name, column_name [, ...])` or an expression.

The usual default is: `FOR ALL COLUMNS SIZE AUTO FOR COLUMNS SIZE 2048 P_VALUE_ID CANON_END_NODE_ID START_NODE_ID G_ID (CANON_END_NODE_ID, START_NODE_ID) (P_VALUE_ID, CANON_END_NODE_ID) (P_VALUE_ID, START_NODE_ID)`

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

To use this procedure, you must connect as a user with permission to execute it. By default, when Spatial and Graph is installed as part of Oracle Database, only the MDSYS user can execute this procedure; however execution permission on this procedure can be granted to users as needed.

This procedure collects statistical information that can help you to improve inferencing performance, as explained in [Enhancing Inference Performance](owl-concepts.md). This procedure internally calls the DBMS_STATS.GATHER_TABLE_STATS procedure to collect statistics on RDF- and OWL-related tables and their indexes, and stores the statistics in the Oracle Database data dictionary. For information about using the DBMS_STATS package, see [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md).

Gathering statistics uses significant system resources, so execute this procedure when it cannot adversely affect essential applications and operations.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

#### Examples

The following example gathers statistics about RDF and OWL related tables and their indexes.

    EXECUTE SEM_PERF.GATHER_STATS;

**Parent topic:** SEM_PERF Package Subprograms

### 17.6 SEM_PERF.IMPORT_NETWORK_STATS

#### Format

    SEM_PERF.IMPORT_NETWORK_STATS (
         stattab       IN VARCHAR2,
         statid        IN VARCHAR2 DEFAULT NULL,
         cascade       IN BOOLEAN DEFAULT TRUE,
         statown       IN VARCHAR2 DEFAULT NULL,
         no_invalidate IN BOOLEAN DEFAULT FALSE,
         force         IN BOOLEAN DEFAULT FALSE,
         stat_category IN VARCHAR2 DEFAULT 'OBJECT_STATS',
         options       IN VARCHAR2 DEFAULT NULL,
         network_owner IN VARCHAR2 DEFAULT NULL,
         network_name  IN VARCHAR2 DEFAULT NULL);

#### Description

Retrieves the statistics for the semantic network from a user statistics table and stores them in the dictionary.

#### Parameters

options
Controls the scope of the operation:

- If `MDSYS.SDO_RDF.VALUE_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_VALUE\$ table.

- If `MDSYS.SDO_RDF.LINK_TABLE_ONLY`, the operation applies only to the MDSYS.RDF_LINK\$ table.

- If null (the default), the operation applies to both the MDSYS.RDF_VALUE\$ and MDSYS.RDF_LINK\$ tables.

(other parameters)
See the parameter explanations for the [DBMS_STATS.IMPORT_TABLE_STATS](../arpls/index.md) procedure in Oracle Database PL/SQL Packages and Types Reference, although `force` here applies to network statistics.

network_owner
Owner of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

network_name
Name of the semantic network. (See [Table 1-1](rdf-semantic-graph-overview.md).)

#### Usage Notes

See the information about the [DBMS_STATS package](../arpls/DBMS_STATS.md) inOracle Database PL/SQL Packages and Types Reference.

See also [Managing Statistics for Semantic Models and the Semantic Network](rdf-semantic-graph-overview.md).

For information about semantic network types and options, see [Semantic Networks](rdf-semantic-graph-overview.md).

#### Examples

The following example imports the statistics for the semantic network in a table named `STAT_TABLE`, and stores them in the dictionary.

    EXECUTE SEM_APIS.IMPORT_NETWORK_STATS('stat_table');

**Parent topic:** SEM_PERF Package Subprograms
