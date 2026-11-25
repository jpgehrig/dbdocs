To use Oracle Database QoS Management, your system must meet certain requirements.

Also, your applications and database connections must conform to certain standards.

If you do not use a supported configuration, then Oracle Database QoS Management reports a configuration violation and is disabled.

- Supported Server Pool Configurations
- Supported Database Configurations
  Depending on your database configuration, all or only some of the Oracle Database QoS Management features are available,
- Supported Service Configurations
- Supported Workload and Objective Types
  Review the types of database workloads and objectives that are supported with Oracle Database QoS Management.

**Parent topic:** [Supported Workloads and Strategies](supported-workloads-and-strategies.md)

### 7.1.1 Supported Server Pool Configurations

Before Oracle Database Quality of Service (QoS) Management can manage the resources for your cluster, you must mark server pools as managed in your Performance Policy. If a server pool is not managed by Oracle Database QoS Management, then the server pool is not visible to the Oracle Database QoS Management server. Any workloads or resources in the unmarked server pools are not managed by Oracle Database QoS Management.

You can select server pools to be managed by Oracle Database QoS Management even if they do not contain any database instances, or have a current size of zero. This enables you to preconfigure a server pool for management by Oracle Database QoS Management before the workload is started. Also, if you configure a server pool to have a minimum size of zero, then Oracle Database QoS Management can remove the servers from that server pool to provide resources for higher priority workloads. In this case, even though there are no resources within the server pool for Oracle Database QoS Management to manage, any workloads that run in that server pool are still monitored and, if possible, resources are allocated to that server pool to support the workloads.

**Parent topic:** Supported Configurations for Oracle Database QoS Management

### 7.1.2 Supported Database Configurations

Depending on your database configuration, all or only some of the Oracle Database QoS Management features are available,

All the features of Oracle Database QoS Management are available for Oracle RAC databases running Oracle Database 12c release 2 software. For Oracle Database 11g release 2 and Oracle Database 12c release 1 Oracle RAC databases, your Oracle RAC database must be policy-managed database, or you can only use Oracle Database QoS Management in Measure-only or Monitor (12.1.0.2) modes.

For policy-managed databases, the database services should be created as `UNIFORM` services, meaning the service is offered by every available instance running in the specified server pool. If your application requires a `SINGLETON` service, then, to use Oracle Database QoS Management in management mode, the service must run in a server pool that has a maximum size of one. If you use a `SINGLETON` service in a server pool that has a maximum size greater than one, then Oracle Database QoS Management reports a configuration violation. If you selected Measure-only for the management mode for this database, then you can use `SINGLETON` services any configuration.

Oracle Database QoS Management supports multiple databases sharing a server pool. If you have multiple databases using the same server pool, then every database that uses the server pool must have Oracle Database QoS Management enabled if they all have performance classes defined. Oracle Database QoS Management also supports Oracle RAC One Node databases (sometimes referred to as singleton databases), but these databases must use server pools that have a maximum size of one if their performance classes are being managed and not simply measured or monitored.

When you create a database, the default value of the `CPU_COUNT` initialization parameter for the database instance is set to the value of the number of physical CPUs on each node that the instance runs on. If you have multiple database instances on the same node and you have performance classes in Management mode, then you must adjust the value of `CPU_COUNT` for each instance so that the sum of `CPU_COUNT` for each instance that runs on the node is equal to or less than the physical number of CPUs on that node. Also, the value of `CPU_COUNT` must be the same for every instance of a database. For example, for the `sales` database, you cannot have `CPU_COUNT` set to four for the `sales1` instance and `CPU_COUNT` set to two for the `sales2` instance if both instances are in the same server pool.

Starting with Oracle Database 12c release 2 (12.2), Oracle Database QoS Management provides full support for multitenant databases. In the multitenant architecture, an Oracle database functions as a multitenant container database (CDB). A CDB includes zero, one, or many customer-created pluggable databases (PDBs). A PDB is a portable collection of schemas, schema objects, and nonschema objects that appears to an Oracle Net client as a non-CDB. All Oracle databases before Oracle Database 12c were non-CDBs.

The Oracle Multitenant option enables you to consolidate data and code without altering existing schemas or applications. A PDB behaves the same as a non-CDB as seen from a client connecting with Oracle Net. Operations that act on an entire non-CDB act in the same way on an entire CDB, for example, when using Oracle Data Guard and database backup and recovery. Thus, the users, administrators, and developers of a non-CDB have substantially the same experience after the database has been consolidated. By consolidating hardware and sharing database memory and files, you reduce costs for hardware, storage, availability, and labor. For example, 100 PDBs on a single server can share one database instance and one set of database files, thereby requiring less hardware and fewer personnel.

Oracle Database QoS Management supports:

- Schema consolidation within a pluggable database (PDB) by adjusting the CPU shares of Performance Classes running in the PDB

- Database consolidation by adjusting the CPU shares between different PDBs within the same multitenant container database (CDB)

- Multiple CDB consolidation by adjusting CPU counts for all CDBs hosted on the same physical servers and the total number of CDB instances by varying the server pool size (if using policy-managed databases)

This functionality is seamlessly integrated into the Oracle Database QoS Management pages in Oracle Enterprise Manager Cloud Control.

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md)

**Parent topic:** Supported Configurations for Oracle Database QoS Management

### 7.1.3 Supported Service Configurations

Database services that are managed by Oracle Clusterware are required for Oracle Database QoS Management. All workloads managed by Oracle Database QoS Management must connect to the database using a database service that is managed by Oracle Clusterware. You cannot use the default database service; the default database service is not managed by Oracle Clusterware.

The services used to connect to the database should be `UNIFORM`. If your application requires a `SINGLETON` service, then, to use Oracle Database QoS Management, the service must run in a server pool that has a maximum size of one.

The Oracle RAC high availability framework monitors the database and its services and sends event notifications using fast application notification (FAN). Oracle Clusterware and Oracle Net Services provide load balancing for services according to rules specified in the service configuration. These rules are:

- The connection load balancing goal: Connections are routed to an instance using the current workload for that instance and the type of connection (`LONG` or `SHORT`) to determine which instance can provide the best performance. For Oracle Database QoS Management, the connection load balancing goal should be set to `LONG`, so that if a new server is allocated to a server pool for a service, new connections will migrate faster to the new server. By migrating connections more quickly to a new server, the workload is balanced faster across all the available instances and the response times for workloads improve at a faster rate.

- The run-time connection load balancing goal: The load balancing advisory data is used to determine which instance best meets the goal specified for the service. The two goals are `SERVICE_TIME`, for which load balancing advisory data is based on elapsed time for work done in the instance, and `THROUGHPUT`, for which the load balancing advisory data is based on the rate that work is completed in the instance. For Oracle Database QoS Management, the run-time connection load balancing goal should be set to `SERVICE_TIME` for all database services that use server pools except optionally those with a maximum size of one.

Run-time connection load balancing sends advice to connection pools on how to balance connection requests across instances in an Oracle RAC database. The load balancing advisory also provides advice about how to direct incoming work to the instances that provide the optimal quality of service for that work. This minimizes the need to relocate the work later.

To configure the load balancing goals for a service, use the Server Control (SRVCTL) utility, as shown in the following example, or use Enterprise Manager:

    srvctl modify service -db db_name -service service_name -rlbgoal SERVICE_TIME -clbgoal LONG

**Parent topic:** Supported Configurations for Oracle Database QoS Management

### 7.1.4 Supported Workload and Objective Types

Review the types of database workloads and objectives that are supported with Oracle Database QoS Management.

In the initial release of Oracle Database QoS Management, only online transaction processing (OLTP) workloads are supported. The only supported Performance Objective is average response time for database requests. Oracle Database QoS Management is designed to manage open workloads, or a workload in which demand is independent of the response time.

The database requests for your application workload must have an average response time of less than one second, and preferably, an average response time of less than 0.5 seconds. Each database request within a Performance Class should be homogenous with respect to resource usage. If a subset of the database requests in a workload use significantly more resources than the other requests, then you should create a new Performance Class to contain the database requests that require more resources.

Oracle Database QoS Management does not support workloads that involve parallel queries. By default, parallel queries run on all available instances of the database, regardless of which service was used to connect to the database; the workload is not contained, or restrained to running on only those instances that offer the service. For a similar reason, Oracle Database QoS Management does not support workloads that involve a significant amount of database requests involving queries to GV\$ views.

For a workload to be managed by Oracle Database QoS Management, the database connections must use a database service that is managed by Oracle Clusterware. The client or application that initiates the connection must be a JDBC (thick or thin) client, or an OCI client. Workloads that use a bequeath connection to the database are not managed by Oracle Database QoS Management.

**Related Topics**

- [Deciding to Create New Performance Classes](overview-oracle-database-qos-management.md)

**Parent topic:** Supported Configurations for Oracle Database QoS Management
