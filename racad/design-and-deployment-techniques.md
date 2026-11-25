This chapter briefly describes database design and deployment techniques for Oracle Real Application Clusters (Oracle RAC) environments. It also describes considerations for high availability and provides general guidelines for various Oracle RAC deployments.

This chapter includes the following topics:

- Deploying Oracle RAC for High Availability

- General Design Considerations for Oracle RAC

- General Database Deployment Topics for Oracle RAC

### Deploying Oracle RAC for High Availability

Many customers implement Oracle RAC to provide high availability for their Oracle Database applications. For true high availability, you must make the entire infrastructure of the application highly available. This requires detailed planning to ensure there are no single points of failure throughout the infrastructure. Even though Oracle RAC makes your database highly available, if a critical application becomes unavailable, then your business can be negatively affected. For example, if you choose to use the Lightweight Directory Access Protocol (LDAP) for authentication, then you must make the LDAP server highly available. If the database is up but the users cannot connect to the database because the LDAP server is not accessible, then the entire system appears to be down to your users.

This section includes the following topics:

- About Designing a High Availability System

- Best Practices for Deploying Oracle RAC in a High Availability Environment

- Consolidating Multiple Applications in a Database or Multiple Databases in a Cluster

- Scalability of Oracle RAC

#### About Designing a High Availability System

For mission critical systems, you must be able to perform failover and recovery, and your environment must be resilient to all types of failures.

For mission critical systems, you must be able to perform failover and recovery, and your environment must be resilient to all types of failures. To reach these goals, start by defining service level requirements for your business. The requirements should include definitions of maximum transaction response time and recovery expectations for failures within the data center (such as for node failure) or for disaster recovery (if the entire data center fails). Typically, the service level objective is a target response time for work, regardless of failures. Determine the recovery time for each redundant component. Even though you may have hardware components that are running in an active/active mode, do not assume that if one component fails the other hardware components can remain operational while the faulty components are being repaired. Also, when components are running in active/passive mode, perform regular tests to validate the failover time. For example, recovery times for storage channels can take minutes. Ensure that the outage times are within your business' service level agreements, and where they are not, work with the hardware vendor to tune the configuration and settings.

When deploying mission critical systems, the testing should include functional testing, destructive testing, and performance testing. Destructive testing includes the injection of various faults in the system to test the recovery and to make sure it satisfies the service level requirements. Destructive testing also allows the creation of operational procedures for the production system.

To help you design and implement a mission critical or highly available system, Oracle provides a range of solutions for every organization regardless of size. Small work groups and global enterprises alike are able to extend the reach of their critical business applications. With Oracle and the Internet, applications and their data are now reliably accessible everywhere, at any time. The Oracle Maximum Availability Architecture (MAA) is the Oracle best practices blueprint that is based on proven Oracle high availability technologies and recommendations. The goal of the MAA is to remove the complexity in designing an optimal high availability architecture.

**Related Topics**

- [Oracle Maximum Availability Architecture (MAA)](http://www.oracle.com/au/products/database/maa-096107.html)

#### Best Practices for Deploying Oracle RAC in a High Availability Environment

Applications can take advantage of many Oracle Database, Oracle Clusterware, and Oracle RAC features and capabilities to minimize or mask any failure in the Oracle RAC environment. For example, you can:

- Remove TCP/IP timeout waits by using the VIP address to connect to the database.

- Create detailed operational procedures and ensure you have the appropriate support contracts in place to match defined service levels for all components in the infrastructure.

- Take advantage of the Oracle RAC Automatic Workload Management features such as connect time failover, Fast Connection Failover, Fast Application Notification, and the Load Balancing Advisory.

- Place voting disks on separate volume groups to mitigate outages due to slow I/O throughput. To survive the failure of x voting devices, configure 2x + 1 mirrors.

- Use Oracle Database Quality of Service Management (Oracle Database QoS Management) to monitor your system and detect performance bottlenecks.

- Place OCR with I/O service times in the order of 2 milliseconds (ms) or less.

- Tune database recovery using the `FAST_START_MTTR_TARGET` initialization parameter.

- Use Oracle Automatic Storage Management (Oracle ASM) to manage database storage.

- Ensure that strong change control procedures are in place.

- Check the surrounding infrastructure for high availability and resiliency, such as LDAP, NIS, and DNS. These entities affect the availability of your Oracle RAC database. If possible, perform a local backup procedure routinely.

- Use Oracle Enterprise Manager to administer your entire Oracle RAC environment, not just the Oracle RAC database. Use Oracle Enterprise Manager to create and modify services, and to start and stop the cluster database instances and the cluster database.

- Use Recovery Manager (RMAN) to back up, restore, and recover data files, control files, server parameter files (SPFILEs) and archived redo log files. You can use RMAN with a media manager to back up files to external storage. You can also configure parallelism when backing up or recovering Oracle RAC databases. In Oracle RAC, RMAN channels can be dynamically allocated across all of the Oracle RAC instances. Channel failover enables failed operations on one node to continue on another node. You can start RMAN from Oracle Enterprise Manager Backup Manager or from the command line.

- If you use sequence numbers, then always use `CACHE` with the `NOORDER` option for optimal performance in sequence number generation. With the `CACHE` option, however, you may have gaps in the sequence numbers. If your environment cannot tolerate sequence number gaps, then use the `NOCACHE` option or consider pre-generating the sequence numbers. If your application requires sequence number ordering but can tolerate gaps, then use `CACHE` and `ORDER` to cache and order sequence numbers in Oracle RAC. If your application requires ordered sequence numbers without gaps, then use `NOCACHE` and `ORDER`. The `NOCACHE` and `ORDER` combination has the most negative effect on performance compared to other caching and ordering combinations.

  **Note:**

  If your environment cannot tolerate sequence number gaps, then consider pre-generating the sequence numbers or use the `ORDER` and `CACHE` options.
  Starting with Oracle Database 18c, you can use scalable sequences to provide better data load scalability instead of configuring a very large sequence cache. Scalable sequences improve the performance of concurrent data load operations, especially when the sequence values are used for populating primary key columns of tables.

- If you use indexes, then consider alternatives, such as reverse key indexes to optimize index performance. Reverse key indexes are especially helpful if you have frequent inserts to one side of an index, such as indexes that are based on insert date.

**Related Topics**

- [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md)
- [Configuring Recovery Manager and Archiving](configuring-recovery-manager-and-archiving.md)
- [Making a Sequence Scalable](../admin/managing-views-sequences-and-synonyms.md)

#### Consolidating Multiple Applications in a Database or Multiple Databases in a Cluster

Many people want to consolidate multiple applications in a single database or consolidate multiple databases in a single cluster. Oracle Clusterware and Oracle RAC support both types of consolidation.

Creating a cluster with a single pool of storage managed by Oracle ASM provides the infrastructure to manage multiple databases whether they are single instance databases or Oracle RAC databases.

##### Managing Capacity During Consolidation

With Oracle RAC databases, you can adjust the number of instances and which nodes run instances for a given database, based on workload requirements. Features such as cluster-managed services allow you to manage multiple workloads on a single database or across multiple databases.

It is important to properly manage the capacity in the cluster when adding work. The processes that manage the cluster—including processes both from Oracle Clusterware and the database—must be able to obtain CPU resources in a timely fashion and must be given higher priority in the system. Oracle Database Quality of Service Management (Oracle Database QoS Management) can assist consolidating multiple applications in a cluster or database by dynamically allocating CPU resources to meet performance objectives. You can also use cluster configuration policies to manage resources at the cluster level.

**Related Topics**

- [Oracle Database Quality of Service Management User's Guide](../atnms/overview-oracle-database-qos-management.md)

##### Managing the Global Cache Service Processes During Consolidation

Oracle recommends that the number of real time Global Cache Service Processes (LMSn) on a server is less than or equal to the number of processors. (Note that this is the number of recognized CPUs that includes cores. For example, a dual-core CPU is considered to be two CPUs.) It is important that you load test your system when adding instances on a node to ensure that you have enough capacity to support the workload.

If you are consolidating many small databases into a cluster, you may want to reduce the number of LMSn created by the Oracle RAC instance. By default, Oracle Database calculates the number of processes based on the number of CPUs it finds on the server. This calculation may result in more LMSn processes than is needed for the Oracle RAC instance. One LMS process may be sufficient for up to 4 CPUs.To reduce the number of LMSn processes, set the `GC_SERVER_PROCESSES` initialization parameter minimally to a value of 1. Add a process for every four CPUs needed by the application. In general, it is better to have few busy LMSn processes. Oracle Database calculates the number of processes when the instance is started, and you must restart the instance to change the value.

##### Using a Database Cloud for Consolidation

A database cloud is a set of databases integrated by the Global Data Services framework into a single virtual server that offers one or more global services, while ensuring high performance, availability and optimal utilization of resources.

Global Data Services manages these virtualized resources with minimum administration overhead, and allows the database cloud to quickly scale to handle additional client requests. The databases that constitute a cloud can be globally distributed, and clients can connect to the database cloud by simply specifying a service name, without needing to know anything about the components and topology of the cloud.

A database cloud can be comprised of multiple database pools. A [database pool](glossary.md) is a set of databases within a database cloud that provide a unique set of global services and belong to a certain administrative domain. Partitioning of cloud databases into multiple pools simplifies service management and provides higher security by allowing each pool to be administered by a different administrator. A database cloud can span multiple geographic regions. A [region](glossary.md) is a logical boundary that contains database clients and servers that are considered to be close to each other. Usually a region corresponds to a data center, but multiple data centers can be in the same region if the network latencies between them satisfy the service-level agreements of the applications accessing these data centers.

Global services enable you to integrate locally and globally distributed, loosely coupled, heterogeneous databases into a scalable and highly available private database cloud. This database cloud can be shared by clients around the globe. Using a private database cloud provides optimal utilization of available resources and simplifies the provisioning of database services.

**Related Topics**

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/global-data-services-admin.md)

#### Scalability of Oracle RAC

Oracle RAC provides concurrent, transactionally consistent access to a single copy of the data from multiple systems. It provides scalability beyond the capacity of a single server. If your application scales transparently on symmetric multiprocessing (SMP) servers, then it is realistic to expect the application to scale well on Oracle RAC, without the need to make changes to the application code.

Traditionally, when a database server runs out of capacity, it is replaced with a new larger server. As servers grow in capacity, they become more expensive. However, for Oracle RAC databases, you have alternatives for increasing the capacity:

- You can migrate applications that traditionally run on large SMP servers to run on clusters of small servers.

- You can maintain the investment in the current hardware and add a new server to the cluster (or create or add a new cluster) to increase the capacity.

Adding servers to a cluster with Oracle Clusterware and Oracle RAC does not require an outage. As soon as the new instance is started, the application can take advantage of the extra capacity.

All servers in the cluster must run the same operating system and same version of Oracle Database but the servers do not have to have the same capacity. With Oracle RAC, you can build a cluster that fits your needs, whether the cluster is made up of servers where each server is a two-CPU commodity server or clusters where the servers have 32 or 64 CPUs in each server. The Oracle parallel execution feature allows a single SQL statement to be divided up into multiple processes, where each process completes a subset of work. In an Oracle RAC environment, you can define the parallel processes to run only on the instance where the user is connected or to run across multiple instances in the cluster.

**Related Topics**

- [Cloning Oracle RAC to Nodes in a New Cluster](cloning-oracle-rac-to-nodes-in-a-new-cluster.md)
- [Using Cloning to Extend Oracle RAC to Nodes in the Same Cluster](using-cloning-to-extend-oracle-rac-to-nodes-in-the-same-cluster.md)
- [Adding and Deleting Oracle RAC from Nodes on Linux and UNIX Systems](adding-and-deleting-oracle-rac-from-nodes-on-linux-and-unix-systems.md)
- [Adding and Deleting Oracle RAC from Nodes on Windows Systems](adding-and-deleting-oracle-rac-from-nodes-on-windows-systems.md)

### General Design Considerations for Oracle RAC

This section briefly describes database design and deployment techniques for Oracle RAC environments. It also describes considerations for high availability and provides general guidelines for various Oracle RAC deployments.

Consider performing the following steps during the design and development of applications that you are deploying on an Oracle RAC database:

1.  Tune the design and the application

2.  Tune the memory and I/O

3.  Tune contention

4.  Tune the operating system

**Note:**

If an application does not scale on an SMP system, then moving the application to an Oracle RAC database cannot improve performance.

Consider using hash partitioning for insert-intensive online transaction processing (OLTP) applications. Hash partitioning:

- Reduces contention on concurrent inserts into a single database structure

- Affects sequence-based indexes when indexes are locally partitioned with a table and tables are partitioned on sequence-based keys

- Is transparent to the application

If you use hash partitioning for tables and indexes for OLTP environments, then you can greatly improve performance in your Oracle RAC database. Note that you cannot use index range scans on an index with hash partitioning.

### General Database Deployment Topics for Oracle RAC

This section describes considerations when deploying Oracle RAC databases. Oracle RAC database performance is not compromised if you do not employ these techniques. If you have an effective noncluster design, then your application will run well on an Oracle RAC database.

This section includes the following topics:

- Tablespace Use in Oracle RAC

- Object Creation and Performance in Oracle RAC

- Node Addition and Deletion and the SYSAUX Tablespace in Oracle RAC

- Distributed Transactions and Oracle RAC

- Deploying OLTP Applications in Oracle RAC

- Flexible Implementation with Cache Fusion

- Deploying Data Warehouse Applications with Oracle RAC

- Data Security Considerations in Oracle RAC

#### Tablespace Use in Oracle RAC

In addition to using locally managed tablespaces, you can further simplify space administration by using automatic segment space management (ASSM) and automatic undo management.

ASSM distributes instance workloads among each instance's subset of blocks for inserts. This improves Oracle RAC performance because it minimizes block transfers. To deploy automatic undo management in an Oracle RAC environment, each instance must have its own undo tablespace.

#### Object Creation and Performance in Oracle RAC

As a general rule, only use DDL statements for maintenance tasks and avoid executing DDL statements during peak system operation periods. In most systems, the amount of new object creation and other DDL statements should be limited. Just as in noncluster Oracle databases, excessive object creation and deletion can increase performance overhead.

#### Node Addition and Deletion and the SYSAUX Tablespace in Oracle RAC

If you add nodes to your Oracle RAC database environment, then you may need to increase the size of the `SYSAUX` tablespace. Conversely, if you remove nodes from your [cluster database](glossary.md), then you may be able to reduce the size of your `SYSAUX` tablespace.

**See Also:**

Your platform-specific Oracle RAC installation guide for guidelines about sizing the `SYSAUX` tablespace for multiple instances

#### Distributed Transactions and Oracle RAC

If you are running XA Transactions in an Oracle RAC environment and the performance is poor, then direct all branches of a tightly coupled distributed transaction to the same instance by creating multiple Oracle Distributed Transaction Processing (DTP) services, with one or more on each Oracle RAC instance.

Each DTP service is a singleton service that is available on one and only one Oracle RAC instance. All access to the database server for distributed transaction processing must be done by way of the DTP services. Ensure that all of the branches of a single global distributed transaction use the same DTP service. In other words, a network connection descriptor, such as a TNS name, a JDBC URL, and so on, must use a DTP service to support distributed transaction processing.

**Related Topics**

- [Distributed Transaction Processing in Oracle RAC](workload-management-with-dynamic-database-services.md)
- [Oracle Database Development Guide](../adfns/xa.md)

#### Deploying OLTP Applications in Oracle RAC

Cache Fusion makes Oracle RAC databases the optimal deployment servers for online transaction processing (OLTP) applications. This is because these types of applications require:

- High availability if there are failures

- Scalability to accommodate increased system demands

- Load balancing according to demand fluctuations

The high availability features of Oracle Database and Oracle RAC can re-distribute and load balance workloads to surviving instances without interrupting processing. Oracle RAC also provides excellent scalability so that if you add or replace a node, then Oracle Database re-masters resources and re-distributes processing loads.

#### Flexible Implementation with Cache Fusion

To accommodate the frequently changing workloads of online transaction processing systems, Oracle RAC remains flexible and dynamic despite changes in system load and system availability. Oracle RAC addresses a wide range of service levels that, for example, fluctuate due to:

- Varying user demands

- Peak scalability issues like trading storms (bursts of high volumes of transactions)

- Varying availability of system resources

#### Deploying Data Warehouse Applications with Oracle RAC

This section discusses how to deploy data warehouse systems in Oracle RAC environments by briefly describing the data warehouse features available in shared disk architectures.

This section includes the following topics:

- Speed-Up for Data Warehouse Applications on Oracle RAC

- Parallel Execution in Data Warehouse Systems and Oracle RAC

##### Speed-Up for Data Warehouse Applications on Oracle RAC

Oracle RAC is ideal for data warehouse applications because it augments the noncluster benefits of Oracle Database. Oracle RAC does this by maximizing the processing available on all of the nodes that belong to an Oracle RAC database to provide speed-up for data warehouse systems.

The query optimizer considers parallel execution when determining the optimal execution plans. The default cost model for the query optimizer is CPU+I/O and the cost unit is time. In Oracle RAC, the query optimizer dynamically computes intelligent defaults for parallelism based on the number of processors in the nodes of the cluster. An evaluation of the costs of alternative access paths, table scans versus indexed access, for example, takes into account the degree of parallelism available for the operation. This results in Oracle Database selecting the execution plans that are optimized for your Oracle RAC configuration.

##### Parallel Execution in Data Warehouse Systems and Oracle RAC

Parallel execution uses multiple processes to run SQL statements on one or more CPUs and is available on both noncluster Oracle databases and Oracle RAC databases.

Oracle RAC takes full advantage of parallel execution by distributing parallel processing across all available instances. The number of processes that can participate in parallel operations depends on the degree of parallelism assigned to each table or index.

**Related Topics**

- [Oracle Database Performance Tuning Guide](../tgdba/performance-tuning-overview.md)
- [Oracle Database Concepts](../cncpt/process-architecture.md)

#### Data Security Considerations in Oracle RAC

This section describes the following two Oracle RAC security considerations:

- Transparent Data Encryption and Keystores

- Windows Firewall Considerations

##### Transparent Data Encryption and Keystores

Oracle Database enables Oracle RAC nodes to share the [keystore](glossary.md) (wallet). This eliminates the need to manually copy and synchronize the keystore across all nodes. Oracle recommends that you create the keystore on a shared file system. This allows all instances to access the same shared keystore.

Oracle RAC uses keystores in the following ways:

1.  Any keystore operation, like opening or closing the keystore, performed on any one Oracle RAC instance is applicable for all other Oracle RAC instances. This means that when you open and close the keystore for one instance, then it opens and closes the keystore for all Oracle RAC instances.

2.  When using a shared file system, ensure that the `ENCRYPTION_WALLET_LOCATION` parameter for all Oracle RAC instances points to the same shared keystore location. The security administrator must also ensure security of the shared keystore by assigning appropriate directory permissions.

    **Note:**

    If Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is available for your operating system, then Oracle recommends that you store the keystore in Oracle ACFS. If you do not have Oracle ACFS in Oracle ASM, then use the Oracle ASM Configuration Assistant (ASMCA) to create it. You must add the mount point to the `sqlnet.ora` file in each instance, as follows:

        ENCRYPTION_WALLET_LOCATION=
          (SOURCE = (METHOD = FILE)
            (METHOD_DATA =
              (DIRECTORY = /opt/oracle/acfsmounts/data_keystore)))

    This file system is mounted automatically when the instances start. Opening and closing the keystore, and commands to set or rekey and rotate the TDE master encryption key, are synchronized between all nodes.

3.  A master key rekey performed on one instance is applicable for all instances. When a new Oracle RAC node comes up, it is aware of the current keystore open or close status.

4.  Do not issue any keystore `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` or `CLOSE` SQL statements while setting up or changing the master key.

Oracle does not support the use of individual TDE wallets for each Oracle RAC node. Instead, use shared wallets for TDE in the Oracle RAC environment. This enables all of the instances to access the same shared software keystore.

**Related Topics**

- [Oracle Database Advanced Security Guide](../asoag/using-transparent-data-encryption-with-other-oracle-features.md)

##### Windows Firewall Considerations

By default, all installations of Windows Server 2003 Service Pack 1 and higher enable the Windows Firewall to block virtually all TCP network ports to incoming connections. As a result, any Oracle products that listen for incoming connections on a TCP port will not receive any of those connection requests, and the clients making those connections will report errors.

Depending upon which Oracle products you install and how they are used, you may need to perform additional Windows post-installation configuration tasks so that the Firewall products are functional on Windows Server 2003.

##### Securely Run ONS Clients Using Wallets

You can configure and use SSL certificates to set up authentication between the ONS server in the database tier and the notification client in the middle tier.

JDBC or Oracle Universal Connection Pools, and other Oracle RAC features, such as Fast Connection Failover, subscribe to notifications from the Oracle Notification Service (ONS) running on Oracle RAC nodes. These connections are not usually authenticated.

1.  Starting with Oracle Database 18c, a default wallet is created during the installation of Oracle Grid Infrastructure.
2.  If you are running a client-side ONS daemon on the middle tier, then there are two possible configurations:
    - ONS started from OPMN (as in OracleAS 10.1.3.x), which uses `opmn.xml` for its configuration.
    - ONS started standalone (as when using ONSCTL), which uses `ons.config` for its configuration.

    For the first configuration, refer to the OPMN Administrator's Guide for the Oracle Application Server release. This involves modifying the `opmn.xml` file to specify the wallet location.

    For the second configuration, the client-side ONS daemon can, potentially, run on different servers. Copy the wallet from step 1 to those client-side servers and specify the path on that client-side server in either the `ons.config` file or in the `opmn.xml` file.
3.  If you are running a remote ONS configuration without a client-side ONS daemon, then configure the client-side server.
    1.  Export the ONS resource to the client cluster.
        Use a command similar to the following, where cluster_name is the name of the remote cluster, and filename is the name of the file to which the credentials data will be written.
            $ srvctl export ons -clientcluster cluster_name -clientdata filename
    2.  Specify the path on the client-side server.
        Modify either the `ons.config` file or the `opmn.xml` file to point to the location of the copied file.

**Related Topics**

- [Configuration of Client-Side ONS Daemon](../jjucp/fast-connection-failover.md)
- [Remote Configuration of ONS](../jjucp/fast-connection-failover.md)

### Introduction to Hang Manager

Hang Manager is an Oracle Real Application Clusters (Oracle RAC) environment feature that autonomously resolves hangs and keeps the resources available.

Enabled by default, Hang Manager:

- Reliably detects database hangs and deadlocks

- Autonomously resolves database hangs and deadlocks

- Supports Oracle Database QoS Performance Classes, Ranks, and Policies to maintain SLAs

- Logs all detections and resolutions

- Provides SQL interface to configure sensitivity (Normal/High) and trace file sizes

A database hangs when a session blocks a chain of one or more sessions. The blocking session holds a resource such as a lock or latch that prevents the blocked sessions from progressing. The chain of sessions has a root or a final blocker session, which blocks all the other sessions in the chain. Hang Manager resolves these issues autonomously by detecting and resolving the hangs.

#### Hang Manager Architecture

Hang Manager autonomously runs as a `DIA0` task within the database.

Hang Manager works in the following three phases:

- Detect: In this phase, Hang Manager collects the data on all the nodes and detects the sessions that are waiting for the resources held by another session.

- Analyze: In this phase, Hang Manager analyzes the sessions detected in the Detect phase to determine if the sessions are part of a potential delay. If the sessions are suspected as delayed, Hang Manager then waits for a certain threshold time period to ensure that the sessions are delayed.

- Verify: In this phase, after the threshold time period is up, Hang Manager verifies that the sessions are delayed and selects a session that's causing the delay.

After selecting the session that's causing the delay, Hang Manager applies resolution methods on that session. If the chain of sessions or the delay resolves automatically, then Hang Manager does not apply delay resolution methods. However, if the delay does not resolve by itself, then Hang Manager resolves the delay by terminating the session that's causing the delay. If terminating the session fails, then Hang Manager terminates the process of the session. This entire process is autonomous and does not block resources for a long period and does not affect the performance.

For example, if a high rank session is included in the chain of delayed sessions, then Hang Manager expedites the termination of the session that's causing the delay. Termination of the session that's causing the delay prevents the high rank session from waiting too long and helps to maintain performance objective of the high rank session.

#### Optional Configuration for Hang Manager

You can adjust the sensitivity, and control the size and number of the log files used by Hang Manager.

##### Sensitivity

If Hang Manager detects a delay, then Hang Manager waits for a certain threshold time period to ensure that the sessions are delayed. Change threshold time period by using `DBMS_HANG_MANAGER` to set the `sensitivity` parameter to either `Normal` or `High`. If the `sensitivity` parameter is set to `Normal`, then Hang Manager waits for the default time period. However, if the sensitivity is set to `High`, then the time period is reduced by 50%.

By default, the `sensitivity` parameter is set to `Normal`. To set Hang Manager sensitivity, run the following commands in SQL\*Plus as `SYS` user:

- To set the `sensitivity` parameter to `Normal`:
      exec dbms_hang_manager.set(dbms_hang_manager.sensitivity, dbms_hang_manager.sensitivity_normal);
- To set the `sensitivity` parameter to `High`:
      exec dbms_hang_manager.set(dbms_hang_manager.sensitivity, dbms_hang_manager.sensitivity_high);

##### Size of the Trace Log File

The Hang Manager logs detailed diagnostics of the delays in the trace files with `_base_` in the file name. Change the size of the trace files in bytes with the `base_file_size_limit` parameter. Run the following command in SQL\*Plus, for example, to set the trace file size limit to 100 MB:

    exec dbms_hang_manager.set(dbms_hang_manager.base_file_size_limit, 104857600);

##### Number of Trace Log Files

The base Hang Manager trace files are part of a trace file set. Change the number of trace files in trace file set with the `base_file_set_count`  parameter. Run the following command in SQL\*Plus, for example, to set the number of trace files in trace file set to 6:

    exec dbms_hang_manager.set(dbms_hang_manager.base_file_set_count,6);

By default, `base_file_set_count` parameter is set to 5.

#### Hang Manager Diagnostics and Logging

Hang Manager autonomously resolves delays and continuously logs the resolutions in the database alert logs and the diagnostics in the trace files.

Hang Manager logs the resolutions in the database alert logs as Automatic Diagnostic Repository (ADR) incidents with incident code `ORA–32701`.

You also get detailed diagnostics about the delay detection in the trace files. Trace files and alert logs have file names starting with `database instance``_dia0_`.

- The trace files are stored in the `$ ``ADR_BASE``/diag/rdbms/``database name``/``database instance``/incident/``incdir_xxxxxx` directory

- The alert logs are stored in the `$ ``ADR_BASE``/diag/rdbms/``database name``/``database instance``/trace` directory

Example 13-1 Hang Manager Trace File for a Local Instance

This example shows an example of the output you see for Hang Manager for the local database instance

    Trace Log File .../oracle/log/diag/rdbms/hm1/hm11/incident/incdir_111/hm11_dia0_11111_i111.trc
    Oracle Database 12c Enterprise Edition Release 12.2.0.1.0 - 64bit Production
    ...
    *** 2016-07-16T12:39:02.715475-07:00
    HM: Hang Statistics - only statistics with non-zero values are listed

                current number of active sessions 3
                  current number of hung sessions 1
      instance health (in terms of hung sessions) 66.67%
           number of cluster-wide active sessions 9
             number of cluster-wide hung sessions 5
       cluster health (in terms of hung sessions) 44.45%

    *** 2016-07-16T12:39:02.715681-07:00
    Resolvable Hangs in the System
                          Root       Chain Total               Hang
       Hang Hang          Inst Root  #hung #hung  Hang   Hang  Resolution
         ID Type Status   Num  Sess   Sess  Sess  Conf   Span  Action
      ----- ---- -------- ---- ----- ----- ----- ------ ------ -------------------
          1 HANG RSLNPEND    3    44     3     5   HIGH GLOBAL Terminate Process
      Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.

Example 13-2 Error Message in the Alert Log Indicating a Hung Session

This example shows an example of a Hang Manager alert log on the primary instance

    2016-07-16T12:39:02.616573-07:00
    Errors in file .../oracle/log/diag/rdbms/hm1/hm1/trace/hm1_dia0_i1111.trc  (incident=1111):
    ORA-32701: Possible hangs up to hang ID=1 detected
    Incident details in: .../oracle/log/diag/rdbms/hm1/hm1/incident/incdir_1111/hm1_dia0_11111_i1111.trc
    2016-07-16T12:39:02.674061-07:00
    DIA0 requesting termination of session sid:44 with serial # 23456 (ospid:34569) on instance 3
         due to a GLOBAL, HIGH confidence hang with ID=1.
         Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.
    DIA0: Examine the alert log on instance 3 for session termination status of hang with ID=1.

Example 13-3 Error Message in the Alert Log Showing a Session Delay Resolved by Hang Manager

This example shows an example of a Hang Manager alert log on the local instance for resolved delays

    2016-07-16T12:39:02.707822-07:00
    Errors in file .../oracle/log/diag/rdbms/hm1/hm11/trace/hm11_dia0_11111.trc  (incident=169):
    ORA-32701: Possible hangs up to hang ID=1 detected
    Incident details in: .../oracle/log/diag/rdbms/hm1/hm11/incident/incdir_169/hm11_dia0_30676_i169.trc
    2016-07-16T12:39:05.086593-07:00
    DIA0 terminating blocker (ospid: 30872 sid: 44 ser#: 23456) of hang with ID = 1
         requested by master DIA0 process on instance 1
         Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.
         by terminating session sid:44 with serial # 23456 (ospid:34569)
    ...
    DIA0 successfully terminated session sid:44 with serial # 23456 (ospid:34569) with status 0.
