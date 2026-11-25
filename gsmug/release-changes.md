This preface contains:

### Changes in Oracle Database 19c

The following are changes in Oracle Database Global Data Services Concepts and Administration Guide for Oracle Database 19c.

#### New Features

The following features are new in this release:

##### Multiple Table Family Support for System-Managed Sharding

The Oracle Sharding feature for Oracle Database 18c supported only one table family (a set of related tables sharing the same sharding key) for each sharded database. In Oracle Database 19c, Oracle Sharding includes support for multiple table families where all data from different table families reside in the same chunks. This feature applies to system-managed sharded databases only. Different applications accessing different table families can now be hosted on one sharded database.

There is one new GDSCTL command, `CONFIG TABLE FAMILY`, and several other commands are extended to support this feature: `ADD SERVICE`, `MODIFY SERVICE`, `CONFIG SERVICE`, `CONFIG CHUNKS`, `STATUS ROUTING`, and `VALIDATE CATALOG`.

There are no new SQL keywords or statements introduced with this feature; however, some restrictions are changed with the use of `CREATE SHARDED TABLE`, `DUPLICATED TABLE`, and `TABLESPACE SET`.

See

- [Global Data Services Control Utility (GDSCTL) Command Reference](gdsctl-reference.md)

- [Using Oracle Sharding](../shard/architecture-and-concepts1.md)

- [Oracle Database SQL Language Reference](../sqlrf/Changes-in-This-Release-for-Oracle-Database-SQL-Language-Reference.md)

##### GSMROOTUSER

A new user called GSMROOTUSER is used to log into CDB\$ROOT for CDBs in a sharding configurations (this user is not used in GDS configurations). Any connections to CDB\$ROOT in a CDB will now be with GSMROOTUSER.

See

- [Global Data Services Control Utility (GDSCTL) Command Reference](gdsctl-reference.md)

#### Deprecation and Desupport

The following features are deprecated or desupported in this release:

##### Desupport of Setting Passwords in GDSCTL Command Line

To enhance security, starting with Oracle Database 19c, the ability to specify passwords from the Global Data Services Control Utility (GDSCTL) command-line when called from the operating system prompt is no longer supported.

This desupport applies only to password changes where GDSCTL is called from a user command-line prompt. For example, the following command is desupported:

    $ gdsctl add database -connect inst1 -pwd gsm_password

Specifying the password from the GDSCTL utility itself is still valid. For example, the following command is valid:

    GDSCTL> add database -connect inst1 -pwd gsm_password

This deprecation addresses the security vulnerability when specifying passwords in GDSCTL commands called from the operating system prompt.

### Changes in Oracle Database 18c Release 1 (18.1)

The following are changes in Oracle Database Global Data Services Concepts and Administration Guide for Oracle Database 18c Release 1 (18.1)

#### New Features

The following features are new in this release:

- ADD SHARD is extended and new commands ADD CDB, MODIFY CDB, CONFIG CDB, and REMOVE CDB are implemented so that Oracle Sharding can support a multitenant architecture.

  See [add shard](gdsctl-reference.md), [add cdb](gdsctl-reference.md), [modify cdb](gdsctl-reference.md), [config cdb](gdsctl-reference.md), and [remove cdb](gdsctl-reference.md).

- With the release of Oracle GoldenGate 18c, the composite sharding method is supported with GoldenGate replication. The `add shardgroup` and `create shardcatalog` command documentation is updated accordingly.

  See [add shardgroup](gdsctl-reference.md) and [create shardcatalog](gdsctl-reference.md).

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database Global Data Services Concepts and Administration Guide for Oracle Database 12c Release 2 (12.2.0.1).

#### New Features

The following features are new in this release:

- Oracle Sharding

  Oracle Sharding is a scalability and availability feature that supports distribution and replication of data across a pool of discrete Oracle databases that share no hardware or software. In this release, global service managers are used as shard directors which route connection requests to individual shards, the GDS catalog is extended to support a shard catalog which contains the metadata for the sharded database, and GDSCTL is enhanced with several new commands to facilitate the creation, monitoring, and lifecycle management of a sharded database.

  See [GDSCTL Commands Used For Oracle Sharding](gdsctl-sharding-env.md)
