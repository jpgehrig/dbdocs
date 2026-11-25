This preface includes:

- Changes in Oracle Real Application Clusters Release 19c

- Changes in Oracle Real Application Clusters Release 18c, Version 18.1

- Changes in Oracle Real Application Clusters 12c Release 2 (12.2)

- Changes in Oracle Real Application Clusters 12c Release 1 (12.1)

### Changes in Oracle Real Application Clusters Release 19c

The following topics list features that are new, deprecated, or desupported in the Oracle Real Application Clusters Administration and Deployment Guide for Oracle Database 19c.

#### New Features

The following features are new in this release.

- Co-location Tag for Client Routing

  Starting with Oracle Database release 19.3, a `colocation_tag` allows for providing a string value as part of the `CONNECT_DATA` of a connect string. Clients with the same colocation tag are routed to the same instance that offers a given service, when possible. If co-location is not possible at the time the connection is made, then the tag is ignored and the connections are routed to an available instance as they would be without the tag.

  Co-location of sessions on the same instance can help to decrease inter-instance communication and thereby increase performance for workload that benefits from being executed in the same instance.

  See [Service Co-location](workload-management-with-dynamic-database-services.md).

- Dynamic Services Fallback Option

  For a dynamic database service that is placed using `preferred` and `available` settings, starting with Oracle Database release 19.3, you can now specify that this service should fall back to a preferred instance when it becomes available and after it was failed over to an available instance. A service fails over to an available instance when there are no preferred instances available. The Dynamic Services Fallback Option allows for more control in placing dynamic database services and ensures that a given service is available on a preferred instance as much as possible.

  See [Instance Preference](workload-management-with-dynamic-database-services.md).

- RAC Resource Runtime Management

  With Oracle Database SGA Runtime Management, the SGA can grow during runtime. Starting with Oracle Database 19.3, Oracle RAC Resource Runtime Management allows for automatic and runtime adjustment of resources that otherwise used to be allocated at database startup only. This enables more efficient resource allocation.

  For information about automatic memory management, see [About Automatic Memory Management](../admin/managing-memory.md) in the Oracle Database Administrator’s Guide.

- Optional Install for the Grid Infrastructure Management Repository

  Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.

  The data contained in the GIMR is the basis for preventative diagnostics based on applied Machine Learning and can help to increase the availability of Oracle Real Application Clusters (Oracle RAC) databases. Having an optional installation for the GIMR allows for more flexible storage space management and faster deployment, especially during the installation of test and development systems.

  See [About Grid Infrastructure Management Repository](../cwlin/about-gimr.md) in Oracle Grid Infrastructure Installation and Upgrade Guide for Linux.

#### Resupport of Direct File Placement for OCR and Voting Disks

Starting with Oracle Grid Infrastructure 19c, the desupport for direct placement of OCR and voting files on shared file systems is rescinded for Oracle Standalone Clusters.

In Oracle Grid Infrastructure 12c Release 2 (12.2), Oracle announced that it would no longer support the placement of the Oracle Grid Infrastructure Oracle Cluster Registry (OCR) and voting files directly on a shared file system. This desupport is now rescinded. Starting with Oracle Grid Infrastructure 19c (19.3), with Oracle Standalone Clusters, you can again place OCR and voting disk files directly on shared file systems. However, for Oracle Domain Services Clusters, you must continue to place OCR and voting files in quorum failure groups managed by Oracle Automatic Storage Management (Oracle ASM).

#### Deprecated Features in Oracle Real Application Clusters 19c

The following features are deprecated in Oracle Real Application Clusters 19c, and may be desupported in a future release:

##### Deprecation of Addnode Script

The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.

The `addnode` script can be removed in a future release. Instead of using the `addnode` script (`addnode.sh` or `addnode.bat`), add nodes by using the installer wizard. The installer wizard provides many enhancements over the `addnode` script. Using the installer wizard simplifies management by consolidating all software lifecycle operations into a single tool.

##### Deprecation of clone.pl Script

The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

##### Deprecation of Vendor Clusterware Integration with Oracle Clusterware

Starting with Oracle Clusterware 19c (19.5), the integration of vendor or third party clusterware with Oracle Clusterware is deprecated.

The integration of vendor clusterware with Oracle Clusterware is deprecated, and can be desupported in a future release. Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. In the absence of an integration between different cluster solutions, the system is subject to the dueling cluster solutions issue: Independent cluster solutions can make individual decisions about which corrective actions must be taken in case of certain failures. To avoid conflicts, only one cluster solution should be active at any point in time. For this reason, Oracle recommends that you align your next software or hardware upgrade with the transition off of vendor cluster solutions.

#### Desupported Features in Oracle Real Application Clusters 19c

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for more information

- Desupport of Oracle Real Application Clusters in the Standard Edition 2 (SE2) Database Edition

  Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

- Desupport of Oracle Streams

  Starting in Oracle Database 19c (19.1), Oracle Streams is desupported. Oracle GoldenGate is the replication solution for Oracle Database.

  Note that Oracle Database Advanced Queuing is not deprecated, and is fully supported in Oracle Database 19c. Oracle Streams did not support features added in Oracle Database 12c (12.1) and later releases, including the multitenant architecture, `LONG VARCHAR`, and other new features. Oracle Streams replication functionality is superseded by GoldenGate.

### Changes in Oracle Real Application Clusters Release 18c, Version 18.1

Following is a list of features that are new in the Oracle Real Application Clusters Administration and Deployment Guide for Oracle Real Application Clusters 18c (18.1).

#### Continuous Application Availability

Continuous application availability is achieved with a combination of planned maintenance and Transparent Application Continuity. Planned maintenance of a database includes draining and migration of database sessions before you begin any planned maintenance, without applications being aware of the activity. Transparent database session draining occurs when Application Continuity is enabled and fails sessions over to another database instance at points within the transaction that are safe, such as when an application submits a connection test or at request boundaries within a transaction.

Transparent Application Continuity transparently tracks and records session and transactional states so that the database session can be recovered following recoverable outages. This is done safely and with no reliance on application knowledge or code changes, enabling Application Continuity to be standard for your applications. Transparency is achieved by consuming a new state-tracking infrastructure that categorizes session state usage as the application issues user calls.

See "[Transparent Application Continuity](ensuring-application-continuity.md)".

#### Oracle RAC Sharding

Oracle RAC Sharding affinitizes table partitions to Oracle RAC instances, and routes database requests that specify a partitioning key to the instance that logically holds the corresponding partition. This provides better cache utilization and dramatically reduces block pings across instances. The partitioning key can only be added to the most performance critical requests. Requests that don’t specify the key still work transparently and can be routed to any instance. No changes to the database schema are required to enable this feature. Oracle RAC Sharding provides performance and scalability benefits with minimal application changes.

See "[Oracle RAC Sharding](workload-management-with-dynamic-database-services.md)".

#### Scalable Sequences

Scalable sequences alleviate index leaf block contention when loading data into tables that use sequence values as keys.

**See Also:**

[Making a Sequence Scalable](../admin/managing-views-sequences-and-synonyms.md)

### Changes in Oracle Real Application Clusters 12c Release 2 (12.2)

Following is a list of features that are new in the Oracle Real Application Clusters Administration and Deployment Guide for Oracle Real Application Clusters 12c release 2 (12.2).

#### SCAN Listener Supports HTTP Protocol

Currently, when a connection request comes in, the SCAN listener load balances among the handlers located on the same node. It then directly hands off the connection to the least loaded handler on the node. With this release, the SCAN listener is aware of the HTTP protocol so that it can redirect HTTP clients to the appropriate handler, which can reside on nodes in the cluster other than the node on which the SCAN listener resides.

#### IPv6 Support for Oracle Real Application Clusters on The Private Network

You can configure cluster nodes to use either IPv4- or IPv6-based IP addresses on a private network, and you can use more than one private network for a cluster.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

#### Extend Oracle Database QoS Management to Fully Support Administrator-Managed Databases

In this release, full Oracle Database Quality of Service Management (Oracle Database QoS Management) support is available by also supporting its Management mode. Oracle supports schema consolidation within an administrator-managed Oracle RAC database by adjusting the CPU shares of performance classes running in the database. Additionally, database consolidation is supported by adjusting CPU counts per databases hosted on the same physical servers.

As administrator-managed databases do not run in server pools, the ability to expand or shrink the number of instances by changing the server pool size that is supported in policy-managed database deployments is not available for administrator-managed databases. This deployment support is integrated into the Oracle Database QoS Management pages in Oracle Enterprise Manager Cloud Control.

**See Also:**

[Oracle Database Quality of Service Management User's Guide](../atnms/supported-configurations-qos-management.md)

#### Oracle Real Application Clusters Reader Nodes

Oracle RAC Reader Nodes facilitate Oracle Flex Cluster architecture by allocating a set of read/write instances running Online Transaction Processing (OLTP) workloads and a set of read-only database instances across Hub Nodes and Leaf Nodes in the cluster. In this architecture, updates to the read-write instances are immediately propagated to the read-only instances on the Leaf Nodes, where they can be used for online reporting or instantaneous queries.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-flex-clusters.md)

#### Server Weight-Based Node Eviction

Server weight-based node eviction acts as a tie-breaker mechanism in situations where Oracle Clusterware must evict a particular node or a group of nodes from a cluster, in which all nodes represent an equal choice for eviction. The server weight-based node eviction mechanism helps to identify the node or the group of nodes to be evicted based on additional information about the load on those servers. Two principle mechanisms, a system-inherent automatic mechanism and a user input-based mechanism, exist to provide respective guidance.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

#### Separation of Duty for Administering Oracle Real Application Clusters

Starting with Oracle Database 12c release 2 (12.2), Oracle Database provides support for separation of duty best practices when administering Oracle Real Application Clusters (Oracle RAC) by introducing the SYSRAC administrative privilege for the clusterware agent. This feature removes the need to use the powerful SYSDBA administrative privilege for Oracle RAC.

SYSRAC, like SYSDG, SYSBACKUP and SYSKM, helps enforce separation of duties and reduce reliance on the use of SYSDBA on production systems. This administrative privilege is the default mode for connecting to the database by the clusterware agent on behalf of the Oracle RAC utilities, such as SRVCTL.

#### In-Memory FastStart

In-Memory FastStart optimizes the population of database objects in the In-Memory column store by storing In-Memory compression units directly on disk.

**See Also:**

[Oracle Database In-Memory Guide](../inmem/managing-im-faststart-for-im-column-store.md)

### Changes in Oracle Real Application Clusters 12c Release 1 (12.1)

The following are changes in Oracle Real Application Clusters Administration and Deployment Guide for Oracle Real Application Clusters (Oracle RAC) 12c:

- Changes in Oracle Real Application Clusters 12c Release 1 (12.1.0.2)

- Changes in Oracle Real Application Clusters 12c Release 1 (12.1.0.1)

- Deprecated Features

- Desupported Features

#### Changes in Oracle Real Application Clusters 12c Release 1 (12.1.0.2)

The following features are new in this release:

- In-Memory Column Store

  The In-Memory Column Store is an optional area in the SGA that stores whole tables, table partitions, and individual columns in a compressed columnar format. The database uses special techniques, including SIMD vector processing, to scan columnar data extremely rapidly. The In-Memory Column Store is a supplement to, rather than a replacement for, the database buffer cache.

  **See Also:**

  [Oracle Database Data Warehousing Guide](../dwhsg/index.md) for more information

- In-Memory Transaction Manager

  The In-Memory Transaction Manager is an independent engine that automatically provides read consistency for transactions that apply changes to the In-Memory Column Store. This engine is necessary because tables and partitions residing in the In-Memory Column Store are stored in columnar format in memory and in row-major format in the data files and database buffer cache.

  **See Also:**

  [Improving Query Performance with the In-Memory Column Store](../admin/managing-memory.md) in Oracle Database Administrator’s Guide for more information

- Fleet Patching and Provisioning

  Fleet Patching and Provisioning enables you to deploy Oracle homes based on images stored in a catalog of precreated software homes.

  **See Also:**

  [Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md) for more information

- Full Database In-Memory Caching

  In this release you can cache an entire database in memory. Use this feature when the buffer cache size of each instance is greater than the size of the whole database. In Oracle RAC systems, for well-partitioned applications, you can use this feature when the combined buffer caches of all database instances (with some extra space to handle duplicate cached blocks between instances) is greater than the database size.

  **See Also:**

  [Oracle Database Performance Tuning Guide](../tgdba/tuning-database-buffer-cache.md) for more information

- Memory Guard Does Not Require Oracle Database QoS Management to be Active

  With this release, Memory Guard is enabled by default independent of whether you use Oracle Database Quality of Service Management (Oracle Database QoS Management). Memory Guard detects memory stress on a node and causes new sessions to be directed to other instances until the existing workload drains and frees memory. When free memory increases on the node, then services are enabled again to automatically accept new connections.

#### Changes in Oracle Real Application Clusters 12c Release 1 (12.1.0.1)

The following features are new in this release:

- Application Continuity

  Before this release, application developers were required to deal explicitly with outages of the underlying software, hardware, and communications layers if they wanted to mask outages from end users.

  In Oracle Database 10g, Fast Application Notification (FAN) quickly delivered exception conditions to applications. However, neither FAN nor earlier Oracle technology reported the outcome of the last transaction to the application, or recovered the in-progress request from an application perspective. As a result, outages were exposed leading to user inconvenience and lost revenue. Users could unintentionally make duplicate purchases and submit multiple payments for the same invoice. In the problematic cases, the administrator needed to reboot the mid-tier to deal with the incoming problems this caused.

  Application Continuity is an application-independent feature that attempts to recover incomplete requests from an application perspective and masks many system, communication, hardware failures, and storage outages from the end user.

  **See Also:**

  - [Oracle Database Concepts](../cncpt/transactions.md) for more information

  - [Ensuring Application Continuity](ensuring-application-continuity.md)

- Transaction Guard for Java

  This feature exposes the new Application Continuity infrastructure to Java. It provides support for:

  - At-most-once transaction execution protocol, such as transaction idempotence

  - API for retrieving logical transaction ID (LTXID)

  - Attribute to get Connection or Session status

  **See Also:**

  [Oracle Database JDBC Developer’s Guide](../jjdbc/transaction-guard.md) for more information

- Transaction Idempotence

  This feature delivers a general purpose, application-independent infrastructure that enables recovery of work from an application perspective and masks most system, communication, and hardware failures from the user. Transaction idempotence ensures that your transactions are executed on time and, at most, once.

  **See Also:**

  [Oracle Database Development Guide](../adfns/sql-processing-for-application-developers.md) for more information

- Oracle Flex Clusters

  Large clusters consisting of, potentially, thousands of nodes, provide a platform for Oracle RAC to support massive parallel query operations.

  **See Also:**

  [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-flex-clusters.md) for more information about Oracle Flex Clusters

- Shared Oracle ASM Password File in a Disk Group

  This feature implements the infrastructure needed to address the bootstrapping issues of storing an Oracle Automatic Storage Management (Oracle ASM) shared password file in an Oracle ASM disk group.

  **See Also:**

  [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md)

- Global Data Services

  Similar to the way Oracle RAC supports a database service and enables service-level workload management across database instances in a cluster, Global Data Services provides Oracle RAC-like connect-time and run-time load balancing, failover, and centralized service management for a set of replicated databases that offer common services. The set of databases can include Oracle RAC and nonclustered Oracle databases interconnected with Oracle Data Guard, Oracle GoldenGate, or any other replication technology.

  **See Also:**

  [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/intro-global-data-services.md) for more information

- Shared Grid Naming Service

  One instance of Grid Naming Service (GNS) can service any number of clusters.

  **See Also:**

  [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for more information

- What-If Command Evaluation for Oracle RAC

  This feature of Oracle Clusterware improves resource management and availability, through a mechanism that provides a policy response to a hypothetical planned or unplanned event, without modifying the state of the system.

  In Oracle RAC, enhancements to SRVCTL aid you in determining the impact of certain commands before you run them to determine the potential impact of the command.

  **See Also:**

  - "[SRVCTL Usage Information](server-control-utility-reference.md)" for a list of SRVCTL commands with What-If functionality

  - [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-control-crsctl-utility-reference.md) for a list of Oracle Clusterware Control (CRSCTL) utility commands with similar enhancements

- Restricting Service Registration for Oracle RAC Deployments

  This feature allows listener registration only from local IPs by default and provides the ability to configure and dynamically update a set of IP addresses or subnets from which registration requests are allowed by the listener.

  **See Also:**

  [Oracle Database Net Services Administrator's Guide](../netag/index.md) for more information

- Restricting Service Registration with Valid Node Checking

  This feature enables the network administrator to specify a list of nodes and subnet information from which the Single Client Access Name (SCAN) listener accepts registration. You can specify the nodes and subnets information using SRVCTL, and SRVCTL stores the information in the SCAN listener resource profile and this information is also written to the `listener.ora` file. Restricting client access to a database makes Oracle RAC even more secure and less vulnerable to security threads and attacks.

- Pluggable Databases

  Pluggable Databases enables an Oracle database to contain a portable collection of schemas, schema objects, and nonschema objects that appears to an Oracle Net client as a separate database. This self-contained collection is called a pluggable database (PDB). A container database (CDB) is an Oracle database that includes zero, one, or many user-created pluggable databases (PDBs). You can unplug a PDB from a CDB and plug it into a different CDB.

  **See Also:**

  [Oracle Database Administrator’s Guide](../multi/managing-a-multitenant-environment.md)

- Support of Oracle Home User on Windows

  Starting with Oracle Database 12c, Oracle Database supports the use of an Oracle home user, which you can specify at installation time. The Oracle home user is associated with a Windows domain user. The Windows domain user should be a low-privileged (non-Administrator) account to ensure that the Oracle home user has a limited set of privileges, thus ensuring that the Oracle Database services have only those privileges required to run Oracle products.

  Windows Administrator user privileges are still required to perform Oracle software maintenance tasks including installation, upgrade, patching, and so on. Oracle Database administrative tools have been enhanced to ask for the password of the Oracle home user, if needed. In Oracle RAC environments, you can store the password for the Oracle home user in a secure wallet. If such a wallet exists, then the Oracle Database administrative tools automatically use the password from the wallet and do not require the user to enter the password for the Oracle home user.

- Cluster Resources for Oracle ACFS and Oracle ADVM

  Oracle Clusterware resource support includes enhancements for Oracle homes stored on Oracle Automatic Storage Management Cluster File System (Oracle ACFS), Oracle ACFS General Purpose file systems for Grid homes, and Oracle ASM Dynamic Volume Manager (Oracle ADVM) volumes. These resources, that Oracle Clusterware manages, support automatic loading of Oracle ACFS, Oracle ADVM and OKS drivers, disk group mounts, dynamic volume enablement, and automatic Oracle ACFS file system mounts.

  **See Also:**

  [Oracle Automatic Storage Management Administrator's Guide](../ostmg/understand-acfs-admin.md) for more information

- Oracle Highly Available NFS

  You can configure Oracle ACFS as a highly available, exported file system service. This service uses Oracle ACFS' clusterwide data consistency and coherency, in combination with virtual IP addresses, to provide failover capability for NFS exports. By mounting the NFS export from this virtual IP address, a client can be assured that, if one node of the cluster is available, then the NFS export will be available.

  **See Also:**

  [Oracle Automatic Storage Management Administrator's Guide](../ostmg/understand-acfs-admin.md) for more information

- Policy-Based Cluster Management and Administration

  Oracle Grid Infrastructure allows running multiple applications in one cluster. Using a policy-based approach, the workload introduced by these applications can be allocated across the cluster using a policy. In addition, a policy set enables different policies to be applied to the cluster over time as required. You can define policy sets using a web-based interface or a command-line interface.

  Hosting various workloads in the same cluster helps to consolidate the workloads into a shared infrastructure that provides high availability and scalability. Using a centralized policy-based approach allows for dynamic resource reallocation and prioritization as the demand changes.

  **See Also:**

  [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md) for more information

- Online Resource Attribute Modification

  Oracle Clusterware manages hardware and software components for high availability using a resource model. You use resource attributes to define how Oracle Clusterware manages those resources. You can modify certain resource attributes and implement those changes without having to restart the resource using online resource attribute modification. You manage online resource attribute modification with certain SRVCTL and CRSCTL commands.

#### Deprecated Features

Deprecation of single-letter SRVCTL CLI options

All SRVCTL commands have been enhanced to accept full-word options instead of the single-letter options. All new SRVCTL command options added in this release support full-word options, only, and do not have single-letter equivalents. The use of single-letter options with SRVCTL commands might be desupported in a future release.

#### Desupported Features

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for more information

- Oracle Cluster File System for Windows

  Oracle no longer supports Oracle Cluster File System (OCFS) on Windows.

- Raw (block) storage devices for Oracle Database and related technologies

  Oracle Database 12c release 1 (12.1) and its related grid technologies, such as Oracle Clusterware, no longer support the direct use of raw or block storage devices. You must move existing files from raw or block devices to Oracle ASM before you upgrade to Oracle Clusterware 12c release 1 (12.1).
