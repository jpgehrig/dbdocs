## Changes in This Release for This Guide

This topic contains the following.

- Changes in Oracle Database Release 19c
- Changes in Oracle Database Release 18.1

### Changes in Oracle Database Release 19c

The following are changes in Oracle Spatial and Graph RDF Knowledge Graph Developer's Guide for Oracle Database Release 19c.

- Support Added for Schema-Private Semantic Networks
- Feature Name Change: RDF Knowledge Graph
- Support Added for Database Vault and Rolling Upgrades in 19.3
- Reduced Default Privileges for MDSYS
- Reduced Tablespace Privileges for MDSYS
- RDF Semantic Graph support added for Eclipse RDF4J
- Support for Subject-Property-Matrix Tables

**Parent topic:** Changes in This Release for This Guide

#### Support Added for Schema-Private Semantic Networks

Semantic networks can now be created in a regular user’s schema. Such networks are called schema-private semantic networks because the associated database objects are created in the network owner’s schema, and the network owner has exclusive privileges to those objects. (DBA users also have such privileges, and the network owner or a DBA can grant and revoke the privileges for other users.)

In previous releases, the only scenario was a single semantic network owned by the MDSYS user and asvailable to the entire database. That scenario is still supported, but you are encouraged to use schema-private semantic networks instead.

For more information, see [Semantic Networks](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 19c

#### Feature Name Change: RDF Knowledge Graph

The feature name previously called RDF Semantic Graph is now called RDF Knowledge Graph.

The terms semantic network and semantic data are still widely used throughout this guide.

**Parent topic:** Changes in Oracle Database Release 19c

#### Support Added for Database Vault and Rolling Upgrades in 19.3

Effective with Oracle Database Release 19.3, RDF knowledge graphs are supported for:

- Oracle Database Vault
- Rolling upgrades

**Parent topic:** Changes in Oracle Database Release 19c

#### Reduced Default Privileges for MDSYS

Starting with Release 12.2, MDSYS no longer has the INHERIT ANY PRIVILEGES privilege, so MDSYS-owned invoker rights procedures can no longer be executed as SYS. Administrative procedures, such as creating a semantic network, must be executed by a non-SYS user with DBA role (such as SYSTEM). If you execute such procedures as SYS, you will get an `ORA-01031: insufficient privileges` error.

See [RDF Privilege Considerations](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 19c

#### Reduced Tablespace Privileges for MDSYS

Effective with Release 19, the MDSYS user no longer has the UNLIMITED TABLESPACE privilege, and so MDSYS must be explicitly granted quota on the tablespace used for an MDSYS-owned semantic network.

See [RDF Privilege Considerations](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 19c

#### RDF Semantic Graph support added for Eclipse RDF4J

Using Oracle RDF Graph Adapter for Eclipse RDF4J, you can now utilize the powerful Eclipse RDF4J framework to work with RDF graph data. The adapter for Eclipse RDF4J provides integration with Eclipse RDF4J SAIL API, Eclipse RDF4J Server and Eclipse RDF4J Workbench.

The main features of the Oracle RDF Graph Adapter for Eclipse RDF4J include Java APIs to load RDF data (bulk and incremental) into the database, query RDF graphs, and update RDF data managed by the database.

See [RDF Semantic Graph Support for Eclipse RDF4J](rdf-graph-support-eclipse-rdf4j.md) for more information.

**Parent topic:** Changes in Oracle Database Release 19c

#### Support for Subject-Property-Matrix Tables

Starting with Oracle Database 19c Release Update (RU) 19.15, Subject-Property-Matrix (SPM) auxiliary tables are now supported using patch 33806152 which is available on [My Oracle Support](https://support.oracle.com/knowledge/Oracle%20Cloud/2521164_1.html).

SPM auxiliary tables can be used to speed up SPARQL query execution. For a given model, you can create one or more Single-Valued Property (SVP) tables that, for each subject, holds the values for many predicates in the same row. Using SVP tables reduces the number of joins required to evaluate “star pattern” SPARQL queries.

In addition, you can create one or more Multi-Valued Property (MVP) tables that hold all the triples for a given property. MVP tables allow for better query optimizer statistics and improved query plans.

You can also create one or more Property Chain (PCN) tables that hold sequences of triples joined by previous object value equal to next subject value. PCN tables improve performance by eliminating joins required to evaluate sequences of triple patterns that form a path.

SVP, MVP and PCN tables are automatically updated when DML operations happen on the underlying model.

For more information, see [Speeding up Query Execution with SPM Auxiliary Tables](rdf-semantic-graph-overview.md) .

**Parent topic:** Changes in Oracle Database Release 19c

### Changes in Oracle Database Release 18.1

The following are changes in Oracle Spatial and Graph RDF Semantic Graph Developer's Guide for Oracle Database Release 18.1.

- Support Added for Oracle Database In-Memory
- Support Added for Semantic Networks with Composite Partitioning
- Enhanced CLOB Support for Bulk Load Operations
- Native Support for Turtle and Trig RDF Formats
- Support for RDF Added to SQL Developer

**Parent topic:** Changes in This Release for This Guide

#### Support Added for Oracle Database In-Memory

RDF data can easily be loaded into memory to take advantage of the Oracle Database In-Memory feature. A semantic network can now be loaded into memory with the [SEM_APIS.ENABLE_INMEMORY](SEM_APIS-reference.md) procedure. In addition, in-memory virtual columns can be used at the virtual model level to add lexical values for RDF terms to the in-memory representation of the MDSYS.RDF_LINK\$ table, thus reducing the number of joins required to evaluate SPARQL queries.

For more information, see [RDF Support for Oracle Database In-Memory](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 18.1

#### Support Added for Semantic Networks with Composite Partitioning

Semantic networks can now be created with list-hash composite partitioning. With this scheme, a semantic network is initially list-partitioned by model id, and then each partition is subpartitioned using a hash of the RDF predicate ID. Composite partitioning improves SPARQL query performance through increased parallelization and better query optimizer statistics.

For more information, see [Semantic Networks](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 18.1

#### Enhanced CLOB Support for Bulk Load Operations

Staging tables that contain RDF quads with long literals (RDF object values greater than 4000 bytes in size) can now be efficiently loaded with [SEM_APIS.BULK_LOAD_FROM_STAGING_TABLE](SEM_APIS-reference.md).

New options have also been added to [SEM_APIS.LOAD_INTO_STAGING_TABLE](SEM_APIS-reference.md) for better handling of long literals when loading from an external table. The `VC_ONLY` option loads only RDF quads with object values not larger than 4000 bytes into a staging table, and the `CLOB_ONLY` option loads only RDF quads with object values larger than 4000 bytes. These options allow a very efficient two-phase bulk load where VARCHAR-only data is loaded in one bulk load operation and CLOB-only data is loaded in a second bulk load operation.

**Parent topic:** Changes in Oracle Database Release 18.1

#### Native Support for Turtle and Trig RDF Formats

Turtle and Trig RDF formats can now be directly loaded into Oracle Database without the need for third-party tools. SPARQL LOAD operations executed through [SEM_APIS.UPDATE_MODEL](SEM_APIS-reference.md) can now parse and insert RDF data serialized in Turtle and Trig formats in addition to the N-Triple and N-Quad formats that were previously supported.

RDF Views can now be created directly from R2RML mappings specified in Turtle or N-Triple format. New R2RML_STRING and R2RML_STRING_FMT arguments have been added to [SEM_APIS.CREATE_RDFVIEW_MODEL](SEM_APIS-reference.md) so that an R2RML mapping string can be used to create an RDF View model.

**Parent topic:** Changes in Oracle Database Release 18.1

#### Support for RDF Added to SQL Developer

You can use Oracle SQL Developer to create RDF-related objects and use RDF and OWL features.

For more information, see [RDF Support in Oracle SQL Developer](rdf-semantic-graph-overview.md).

**Parent topic:** Changes in Oracle Database Release 18.1
