Oracle Database QoS Management works with Oracle Real Application Clusters (Oracle RAC) and Oracle Clusterware. Oracle Database QoS Management operates over an entire Oracle RAC cluster, which can support a variety of applications.

**Note:**

Oracle Database QoS Management supports only OLTP workloads. The following types of workloads (or database requests) are not supported:

- Batch workloads

- Workloads that require more than one second to complete

- Workloads that use parallel data manipulation language (DML)

- Workloads that query GV\$ views at a signification utilization level

<!-- -->

- Managing Database Resources to Meet Service Levels
  Oracle Database QoS Management manages the CPU resource for a cluster. Oracle Database QoS Management does not manage I/O resources, so I/O intensive applications are not managed effectively by Oracle Database QoS Management.
- High Availability Management and Oracle Database QoS Management
  Oracle Database QoS Management helps you achieve optimal performance levels for your application workloads.

**Parent topic:** [Introduction to Oracle Database QoS Management](introduction-oracle-database-qos-management.md)

### 6.4.1 Managing Database Resources to Meet Service Levels

Oracle Database QoS Management manages the CPU resource for a cluster. Oracle Database QoS Management does not manage I/O resources, so I/O intensive applications are not managed effectively by Oracle Database QoS Management.

Oracle Database QoS Management integrates with the Oracle RAC database through the following technologies to manage resources within a cluster:

- Database Services

- Oracle Database Resource Manager

- Oracle Clusterware

- Run-time Connection Load Balancing

Oracle Database QoS Management periodically evaluates the resource wait times for all used resources. If the average response time for the work requests in a Performance Class is greater than the value specified in its Performance Objective, then Oracle Database QoS Management uses the collected metrics to find the bottlenecked resource. If possible, Oracle Database QoS Management provides recommendations for adjusting the size of the server pools or making alterations to the consumer group mappings in the resource plan used by Oracle Database Resource Manager.

- Database Services
  Database services provide a mechanism you can use to group together related work requests.
- Oracle Database Resource Manager
  Oracle Database QoS Management uses Oracle Database Resource Manager to manage allocate resources to performance classes.
- Oracle Clusterware
  Oracle Database QoS Management manages and monitors server pools configured by Oracle Clusterware.
- Run-time Connection Load Balancing
  Applications that use resources managed by Oracle Database QoS Management can also benefit from connection load balancing and transparent application failover (TAF).

**Parent topic:** What Does Oracle Database QoS Management Manage?

#### 6.4.1.1 Database Services

Database services provide a mechanism you can use to group together related work requests.

An application connects to the cluster databases using database services. A user-initiated query against the database could use a different service than a web-based application. Different services can represent different types of work requests. Each call or request made to the Oracle RAC database is a work request.

You can also use database services to manage and measure database workloads for policy-managed, administrator-managed, and multitenant databases. To manage the resources used by a service, some services might be deployed on several Oracle RAC instances concurrently, whereas others might be deployed on only a single instance to isolate the workload that uses that service.

In an Oracle RAC cluster, Oracle Database QoS Management monitors the server pools and its nodes, on which the database services are offered. Services are created by the database administrator for a database. For a policy-managed database, the service runs on all servers in the specified server pool. If a singleton service is required due to the inability of the application to scale horizontally, then the service can be restricted to run in a server pool that has a minimum and maximum size of one. Policy-managed singleton service support in pools larger than one is restricted to measurement and monitoring only.

To use Oracle Database QoS Management for managing performance, create one or more policy-managed databases that run in server pools. If you have administrator-managed databases, then the database instances are placed in the Generic server pool and Oracle Database QoS Management can only monitor these databases.

When you first configure Oracle Database QoS Management, a default Performance Policy is created for each service that is discovered on the server pools being monitored. The name of these default Performance Classes are `service_name``_pc`. The workload you want to monitor and manage the resource for must use a database service to connect to the database.

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md)

**Parent topic:** Managing Database Resources to Meet Service Levels

#### 6.4.1.2 Oracle Database Resource Manager

Oracle Database QoS Management uses Oracle Database Resource Manager to manage allocate resources to performance classes.

Oracle Database Resource Manager (Resource Manager) is an example of a resource allocation method; Resource Manager can allocate CPU shares among a collection of resource consumer groups based on a resource plan specified by an administrator. A resource plan allocates the percentage of opportunities to run on the CPU.

Oracle Database QoS Management does not adjust existing Resource Manager plans; Oracle Database QoS Management activates a resource plan named `APPQOS_PLAN`, which is a complex, multilevel resource plan. Oracle Database QoS Management also creates consumer groups that represent Performance Classes and resource plan directives for each consumer group.

When you implement an Oracle Database QoS Management recommendation to promote or demote a consumer group for a Performance Class, Oracle Database QoS Management makes the recommended changes to the mapping of the Performance Class to the CPU shares specified in the resource plan. By altering the consumer group, the Performance Class that is currently not meeting its Performance Objective is given more access to the CPU resource.

For multitenant databases, instead of managing CPU shares directly for a PDB, Oracle Database QoS Management manages the CPU shares for the multitenant database by assigning PDB shares to each PDB in the CDB. Initially, each PDB in a multitenant database is assigned 50 PDB shares. If a Performance Class is not meeting its performance objectives, then PDB shares are reassigned from a donor PDB and assigned to the target PDB. Oracle Database QoS Management manages the assignment of PDB shares in a resource plan. The two resource plans used by Oracle Database QoS Management for multitenant databases are:

- `ORA$QOS_CDB_PLAN`: governs CPU shares for each PDB

- `ORA$QOS_PLAN`: governs the PDB shares

**Note:**

Do not edit the Oracle Database QoS Management resource plans except as specified in "Editing the Resource Plan for Oracle Database QoS Management".

**Related Topics**

- [Enabling Oracle Database QoS Management](configuring-qos-management-manage-db-workloads.md)
- [Editing the Resource Plan for Oracle Database QoS Management](editing-resource-plan-qos-management.md)
- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md)

**Parent topic:** Managing Database Resources to Meet Service Levels

#### 6.4.1.3 Oracle Clusterware

Oracle Database QoS Management manages and monitors server pools configured by Oracle Clusterware.

You must have Oracle Clusterware installed and configured before you can use Oracle Database QoS Management. The cluster administrator should create server pools to be used to deploy policy-managed Oracle RAC databases. Administrator-managed Oracle RAC databases use only the Generic server pool.

When you first configure Oracle Database QoS Management and create the initial Policy Set, you specify which server pools should be managed by Oracle Database QoS Management and which should only be monitored. If you select a server pool to be managed by Oracle Database QoS Management, then Oracle Database QoS Management monitors the resources used by all the Performance Classes that run in that server pool. If a Performance Class is not satisfying its Performance Objective, then Oracle Database QoS Management can recommend moving servers between server pools to provide additional resources where needed.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md)

**Parent topic:** Managing Database Resources to Meet Service Levels

#### 6.4.1.4 Run-time Connection Load Balancing

Applications that use resources managed by Oracle Database QoS Management can also benefit from connection load balancing and transparent application failover (TAF).

Run-time connection load balancing enables Oracle Clients to provide intelligent allocations of connections in the connection pool when applications request a connection to complete some work; the decision of which instance to route a new connection to is based on the current level of performance provided by the database instances.

Connection load balancing enables you to spread user connections across all of the instances that are supporting a service. For each service, you can define the method you want the listener to use for load balancing by setting the connection load balancing goal, using the appropriate SRVCTL command with the `-clbgoal` option. You can also specify a single TAF policy for all users of a service using SRVCTL with the options `-failovermethod`,`-failovertype`, and so on.

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for more information about run-time connection load balancing

- "[Supported Service Configurations](supported-configurations-qos-management.md)"

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for more information about configuring TAF

**Parent topic:** Managing Database Resources to Meet Service Levels

### 6.4.2 High Availability Management and Oracle Database QoS Management

Oracle Database QoS Management helps you achieve optimal performance levels for your application workloads.

Performance management and managing systems for high availability are closely related. Users typically consider a system to be up, or available, only when its performance is acceptable. You can use Oracle Database QoS Management and Performance Objectives to specify and maintain acceptable performance levels.

Oracle Database QoS Management is a run-time performance management product that optimizes resource allocations to help your system meet service-level agreements under dynamic workload conditions. Oracle Database QoS Management provides recommendations to help the work that is most critical to your business get the necessary resources. Oracle Database QoS Management assists in rebalancing resource allocations based upon current demand and resource availability. Nonessential work is suppressed to ensure that work vital to your business completes successfully.

Oracle Database QoS Management is not a feature to use for improving performance; the goal of Oracle Database QoS Management is to maintain optimal performance levels. Oracle Database QoS Management assumes that system parameters that affect both performance and availability have been set appropriately, and that they are constant. For example, the `FAST_START_MTTR_TARGET` database parameter controls how frequently the database writer checkpoints blocks to the data files to minimize instance recovery time. Using a low value for this parameter reduces the amount of time required to recover your database, but the overhead of writing redo log data more frequently can have a negative impact on the performance of your database. Oracle Database QoS Management does not make recommendations regarding the values specified for such parameters.

Management for high availability encompasses many issues that are not related to workload and that cannot be affected by managing workloads. For example, system availability depends crucially on the frequency and duration of software upgrade events. System availability also depends directly on the frequency of hardware failures. Managing workloads cannot change how often software upgrades are done or how often hardware fails.

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/design-and-deployment-techniques.md)
- [Oracle Database Performance Tuning Guide](../tgdba/performance-tuning-overview.md)

**Parent topic:** What Does Oracle Database QoS Management Manage?
