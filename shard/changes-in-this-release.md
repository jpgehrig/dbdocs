## Changes in This Release for Oracle Sharding

This preface contains:

### Changes in Oracle Database 19c

The following are changes in Using Oracle Sharding for Oracle Database 19c.

#### New Features

The following features are new in this release:

##### Multiple Table Family Support for System-Managed Sharding

The Oracle Sharding feature for Oracle Database 18c supported only one table family (a set of related tables sharing the same sharding key) for each sharded database. In Oracle Database 19c, Oracle Sharding includes support for multiple table families where all data from different table families reside in the same chunks. This feature applies to system-managed sharded databases only. Different applications accessing different table families can now be hosted on one sharded database.

There is one new GDSCTL command, `CONFIG TABLE FAMILY`, and several other commands are extended to support this feature: `ADD SERVICE`, `MODIFY SERVICE`, `CONFIG SERVICE`, `CONFIG CHUNKS`, `STATUS ROUTING`, and `VALIDATE CATALOG`.

There are no new SQL keywords or statements introduced with this feature; however, some restrictions are changed with the use of `CREATE SHARDED TABLE` and `TABLESPACE SET`.

See

- [Sharded Table Family](architecture-and-concepts1.md)

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/gdsctl-reference.md)

- [Oracle Database SQL Language Reference](../sqlrf/Changes-in-This-Release-for-Oracle-Database-SQL-Language-Reference.md)

##### Support for Multiple PDB-Shards in the Same CDB

In Oracle Database 18c, Oracle Sharding introduced the capability for using a single PDB in a CDB as a shard or a shard catalog database. In Oracle Database 19c, Oracle Sharding enables you to use more than one PDB in a CDB for shards or shard catalog databases, with certain restrictions. For example, this feature allows a CDB to contain shard PDBs from different sharded databases (SDBs), each with their own separate catalog databases.

See [Compatibility and Migration from Oracle Database 18c](sharding-lifecycle-management.md) for information about how to migrate shard PDBs to 19c.

##### Generation of Unique Sequence Numbers Across Shards

Before Oracle Database 19c, if you needed a unique number across shards you had to manage it yourself. In Oracle Database 19c, Oracle Sharding allows you to independently generate sequence numbers on each shard which are unique across all shards.

To support this feature, new `SEQUENCE` object clauses, `SHARD` and `NOSHARD`, are included in the `SEQUENCE` object DDL syntax.

See

- [Generating Unique Sequence Numbers Across Shards](schema-design1.md)

- [Oracle Database SQL Language Reference](../sqlrf/Changes-in-This-Release-for-Oracle-Database-SQL-Language-Reference.md)

##### Support for Multi-Shard Query Coordinators on Shard Catalog Standbys

Before Oracle Database 19c, only the primary shard catalog database could be used as the multi-shard query coordinator. In Oracle Database 19c you can also enable the multi-shard query coordinator on Oracle Active Data Guard standbys of the shard catalog database. This improves the scalability and availability of multi-shard query workload.

See

- [Query Processing and the Query Coordinator](architecture-and-concepts1.md)

##### Propagation of Parameter Settings Across Shards

Before Oracle Database 19c, database administrators had to configure `ALTER SYSTEM` parameter settings on each shard in a sharded database. This feature provides ease of manageability by allowing administrators to centrally manage and propagate parameter settings from the shard catalog to all of the database shards. Once settings are configured at the shard catalog, they are automatically propagated to all shards of the sharded database.

See [Propagation of Parameter Settings Across Shards](sharding-lifecycle-management.md)

#### Deprecation and Desupport

The following features are deprecated or desupported in this release:

##### Desupport of Setting Passwords in GDSCTL Command Line

To enhance security, starting with Oracle Database 19c, the ability to specify passwords from the Global Data Services Control Utility (GDSCTL) command-line when called from the operating system prompt is no longer supported.

This desupport applies only to password changes where GDSCTL is called from a user command-line prompt. For example, the following command is desupported:

    $ gdsctl add database -connect inst1 -pwd gsm_password

Specifying the password from the GDSCTL utility itself is still valid. For example, the following command is valid:

    GDSCTL> add database -connect inst1 -pwd gsm_password

This deprecation addresses the security vulnerability when specifying passwords in GDSCTL commands called from the operating system prompt.
