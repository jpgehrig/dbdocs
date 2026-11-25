This section discusses optimizations for the following products:

- Oracle Real Application Clusters (Oracle RAC) is a cluster database with a shared cache architecture that overcomes the limitations of traditional shared-nothing and shared-disk approaches to provide highly scalable and available database solutions for business applications.

- Oracle Data Guard provides one or more standby databases to protect Oracle data from failures, disasters, human error, and data corruptions for high availability in mission critical applications.

- Oracle GoldenGate replicates data among heterogeneous data environments. It enables high availability solutions, real-time data integration, transactional change data capture, data replication, transformations, and verification between operational and analytical enterprise systems.

- Global Data Services (GDS), new in Oracle Database 12c, provides database workload management features across replicated databases, such as Data Guard and GoldenGate.

ODP.NET supports Oracle Real Application Clusters (Oracle RAC), Data Guard, and GoldenGate transparently, meaning you do not need to change ODP.NET code to use these Oracle components. To further take advantage of these technologies, ODP.NET offers connection pooling optimization features for achieving better application high availability and performance. You can do this through configuring ODP.NET to receive, respond, and send database status messages to .NET applications.

These optimization configurations include the use of features such as Fast Application Notification (FAN), Runtime Connection Load Balancing, and Fast Connection Failover (FCF).

These connection pooling optimizations can improve high availability and performance for Oracle Real Application Clusters and Global Data Services products:

- Fast Application Notification

- Runtime Connection Load Balancing

- Fast Connection Failover (FCF)

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md).
- [Oracle Data Guard Concepts and Administration](../sbydb/introduction-to-oracle-data-guard-concepts.md).
- [Oracle Database High Availability Overview](../haovw/ha-features.md).

### Fast Application Notification

Fast Application Notification (FAN) is a high availability and load balancing notification mechanism that Oracle RAC, Data Guard, and GoldenGate use to notify ODP.NET applications about cluster configuration and service-level information, including status changes such as UP or DOWN events and server load. FAN UP and DOWN events can apply to instances, services, and nodes. Based on information received, ODP.NET can adjust its connection pool accordingly to improve application availability and performance.

With FAN, Oracle RAC, Data Guard, and GoldenGate use one of two Oracle messaging infrastructures to send notifications to ODP.NET applications:

- Oracle Notification Service (ONS)

- Oracle Database Advanced Queueing (AQ).

Table 3-5 describes when each messaging system is used and the ODP.NET-related client configuration.

Table 3-5 Configurations for ODP.NET Driver Types

| ODP.NET Driver Type | Database Server Version | FAN Infrastructure | Configuration       | Manual ONS Configuration Locations                                                  |
|:--------------------|:------------------------|:-------------------|:--------------------|:------------------------------------------------------------------------------------|
| managed             | 12.1 and later          | ONS                | Automatic or Manual | Either of these two files:<br>• .NET configuration file<br>• ONS configuration file |
| managed             | 11.2 and earlier        | ONS                | Manual              | Either of these two files:<br>• .NET configuration file<br>• ONS configuration file |
| unmanaged           | 12.1 and later          | ONS                | Automatic or Manual | `oraaccess.xml` file                                                                |
| unmanaged           | 11.2 and earlier        | AQ                 | Automatic           | N/A                                                                                 |

For automatic ONS configuration, developers can add more nodes and ports for ODP.NET to listen to, in addition to the nodes and ports that ODP.NET obtains from the database automatically.

ODP.NET applications do not require code changes to migrate from the AQ to ONS FAN infrastructure. However, some ODP.NET client configuration changes may be necessary when migrating to ONS, a newer database server version, or from ODP.NET, Unmanaged Driver to the managed driver, as documented above.

On the database server side, FAN must be set up and configured.

Using FAN Messages from the database, ODP.NET can do the following:

- With Runtime Connection Load Balancing, ODP.NET load balances connections among Oracle RAC nodes, services, and service members and GDS resources. This feature improves ODP.NET response time and ensures better resource allocation of server resources.

- With the Fast Connection Failover (FCF) feature, Oracle RAC, Data Guard, and GoldenGate can inform the ODP.NET connection pool if database nodes, services, service members, or the databases have gone down. These DOWN messages indicate which connections in the pool are invalid and must be removed.

**See Also:**

- [onsConfig section](InstallManagedConfig.md) to configure the .NET configuration file.

- [Client Side ONS Daemon Configuration](InstallManagedConfig.md) to configure the ONS configuration file.

- [Configuring a Port to Listen for Database Notifications](InstallConfiguringPort.md) for more information on AQ configuration for FAN.

- Runtime Connection Load Balancing

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md) for more information about FAN.

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md) to configure `oraaccess.xml`.

- [Oracle Database Development Guide](../adfns/high-availability.md)

### Runtime Connection Load Balancing

With Runtime Connection Load Balancing, Oracle Data Provider for .NET balances work requests across Oracle RAC instances based on the load balancing advisory and service goal. Because workloads can constantly change, load balancing occurs when the application requests a new connection. Thus, ODP.NET optimizes service levels by connecting users to the least loaded nodes in real-time.

In Oracle Database 12c, Runtime Connection Load Balancing has been extended to Oracle Data Guard and Oracle GoldenGate so that ODP.NET 12c connections can be load balanced with these two database services as part of Global Data Services. No ODP.NET applications require code changes to use Global Data Services if they are already using Runtime Connection Load Balancing.

When Runtime Connection Load Balancing is enabled:

- The ODP.NET connection pool dispenses connections based on the load balancing advisory and service goal.

- The ODP.NET connection pool also balances the number of connections to each service member providing the service, based on the load balancing advisory and service goal.

By default, ODP.NET is enabled to receive Runtime Connection Load Balancing FAN messages from the server. The feature has been enabled via the "`Load Balancing=true`" and "`pooling=true`" settings in the connection string, which are the default values. This feature can only be used if "`pooling=true`". In order to use Runtime Connection Load Balancing, specific Oracle server configurations must be set.

The following connection string example enables Runtime Connection Load Balancing:

`"user id=scott;password=tiger;data source=erp;load balancing=true;"`

**See Also:**

- [Table 3-2](featConnecting.md)

- "[Configuring a Port to Listen for Database Notifications](InstallConfiguringPort.md)"

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) to set up the Oracle Net configuration that Runtime Connection Load Balancing requires

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for the required Oracle RAC configuration

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/intro-global-data-services.md)

### Fast Connection Failover (FCF)

When an Oracle RAC service, service member, node, or a Data Guard database fails, the severed ODP.NET connection objects may continue to exist in the application. If users attempt to use these invalid connections, they will encounter errors. FCF enables ODP.NET to free these severed connections proactively and quickly. Users then will be able to use the application after a server side failure without manual intervention from an administrator.

In Oracle Database 12c, FCF has been extended to Oracle Data Guard and Oracle GoldenGate for ODP.NET 12c connections through Global Data Services. No ODP.NET applications require code changes to use Global Data Services if they already use FCF.

ODP.NET applications can enable FCF through the High Availability Events, `"HA Events"`, connection string attribute. When HA Events are enabled:

- ODP.NET connection pool proactively removes connections from the pool when a Global Data Service or Oracle RAC service, service member, node, or database goes down.

- ODP.NET proactively forces threads waiting for responses from the downed database to exit out from the existing call to avoid any hangs. When such a connection is then returned to the pool, any resource associated with that connection is freed.

- ODP.NET establishes connections to existing Oracle instances if the removal of severed connections brings the total number of connections below the "`min pool size`", upon the next connection request.

By default, ODP.NET is enabled to receive FCF FAN messages from the server. This feature have been enabled via the `HA Events=true` and `pooling=true` settings in the connection string, which are the default values.

The following connection string example enables HA Events:

`"user id=scott;password=tiger;data source=erp;HA events=true;"`

**See Also:**

- [Table 3-2](featConnecting.md)

- [Configuring a Port to Listen for Database Notifications](InstallConfiguringPort.md)

- [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md) to set up the Oracle Net configuration that FCF requires

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for the required Oracle RAC configuration

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/intro-global-data-services.md)

### Using FCF Planned Outage to Minimize Service Disruption

FCF not only provides high availability services for unplanned outages, such as node failures, but also for planned outages, such as server repairs, upgrades, and changes, to minimize service disruption to ODP.NET application users.

When a database service is set to be stopped or relocated, a FAN message is published with a planned reason code. A FCF-aware ODP.NET connection pool (`HA Events=true`) receives the notification and commences to close idle connections, no longer allowing new connections to that specific database service. Active connections to that specific database service remain until users complete their tasks and the connection is returned to the pool. Thus, no users must stop work mid-stream due to a planned outage.

Eventually, all users complete their tasks and no connections remain to that database service. The database administrator can then stop the service for the planned outage task. This feature allows the database service to be stopped as quickly as possible without end user disruption.

Oracle planned outage support works with Oracle Real Application Clusters (Oracle RAC), Oracle Data Guard, and some single instance scenarios.

#### Oracle RAC Planned Outage

A typical planned outage scenario for Oracle RAC follows below. Note that the database server commands apply to Oracle RAC 12c Release 2 or higher. Commands for earlier releases may be different.

1.  There is a need to upgrade, patch, or repair a software or hardware issue on a database server. Stop the instance gracefully such that existing users experience no to few errors. You can wait until all users complete their work before doing so. Business requirements will dictate whether you wait for all users to log out or begin the planned outage after a set time. An administrator could issue the following command line operation using Oracle Server Control Utility (`srvctl`):

        srvctl relocate service –database <unique database name> –service <service name> –drain_timeout 120 –stopoption IMMEDIATE –oldinst <existing instance>

    This command relocates the database service from the existing instance to any instance it is configured to run on. Oracle Cluster Ready Services (CRS) will choose this instance, as the command line specifies no target. CRS will wait 120 seconds `(–drain_timeout 120`) for any active sessions to drain, after which any sessions remaining on the existing instance will be forcibly disconnected (`–stopoption IMMEDIATE`). If Application Continuity is used in conjunction with planned outage, an attempt is made to recover these killed sessions, masking the outage from end users.

    The relocate operation starts the service in the new location prior to stopping the service in its existing location. Immediate relocation allows draining with no brownout. If the service cannot be started, it is not stopped at the original location to maintain availability.

2.  Meanwhile in the connection pool, the FAN planned DOWN event clears idle sessions for the instance being shutdown from the ODP.NET connection pool immediately and marks that instance’s active sessions to be released at the next check-in. These FAN actions drain the sessions from this instance without disrupting the users.

    Existing connections on other instances remain usable, and new connections can be opened to these other instances.

3.  Not all sessions will check their connections into the pool immediately. The timeout period specified by `–drain_timeout` after which the instance is forcibly shut down, evicting any remaining client connections. Administrators can check whether any active sessions to the instance remain by querying the `v$session` table.

4.  Once the upgrade, patch, or repair is complete, restart the instance and the service on the original node. The FAN UP event will inform the ODP.NET pool that it can now use the original machine again.

**See Also:**

[Oracle Database High Availability Best Practices](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=HABPT044)

#### Oracle Data Guard Planned Outage

Oracle Data Guard performs switchovers from primary databases to standby databases in planned failover scenarios. During the switchover, administrators will want to limit end user disruptions. In Oracle Database 12c Release 2 and higher, these administrators can use the Data Guard command-line interface (`DGMGRL`) command to switch roles between primary and standby databases:

    SWITCHOVER TO <database name> [WAIT <timeout in seconds> ];  

The `WAIT` option specifies to wait for sessions to drain before proceeding with the switchover.

Similar to the Oracle RAC scenario, FAN informs the ODP.NET to remove idle connections from the pool. Connections subsequently checked in are destroyed until no active connections remain to that primary database, which will allow the switchover to begin.

When switchover to the standby completes, a FAN UP event informs ODP.NET that it can start creating connections to the standby instance.

During the Data Guard service relocation process, new incoming connection requests will not be accepted until the service has fully relocated. Incoming connection requests arriving during the interim, such as in the middle of an Oracle Data Guard switchover, will receive connectivity errors.

To prevent these errors, ODP.NET can pause connection attempts until the new database service is available. ODP.NET, Managed and Unmanaged Drivers block any connection attempts until the service is up or until the configured time limit expires from the time when the service DOWN event was received. This feature is useful for planned outages and service relocations. It works with Oracle RAC and Oracle Data Guard.

This time limit is the `ServiceRelocationConnectionTimeout` setting, which can be set in the .NET configuration file.

**See Also:**

[`ServiceRelocationConnectionTimeout`](InstallManagedConfig.md)

### Pool Behavior in an Oracle RAC Database

When connection pools are created for a single-instance database, pool size attributes are applied to the single service. Similarly, when connection pools are created for an Oracle RAC database, the pool size attributes are applied to a service and not to service members. For example, if "`Min Pool Size`" is set to `N`, then ODP.NET does not create `N` connections for each service member. Instead, it creates, at minimum, `N` connections for the entire service, where `N` connections are distributed among the service members.

The following pool size connection string attributes are applied to a service.

- `Min Pool Size`

- `Max Pool Size`

- `Incr Pool Size`

- `Decr Pool Size`

ODP.NET connects to the same Oracle RAC node when required by a distributed transaction that has already begun on a particular node, by an Oracle runtime connection load balancing advisory, or by Oracle RAC load balancing gravitation in which connections will gravitate to an under utilized node. If the connection pool has no idle connections to this particular node, then ODP.NET will create a new connection to this node. Node affinity is honored even when the connection pool runs out of idle connections to dispense.
