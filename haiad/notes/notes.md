Oracle Maximum Availability Architecture (MAA) provides architecture, configuration, and life cycle best practices for your Oracle database to meet your high availability service levels for Oracle databases residing in on-premises, Oracle Public Cloud, Cloud@Customer, or hybrid database architecture consisting of both on-premise and cloud databases.

Oracle MAA offers a choice of standard MAA reference architectures--Bronze, Silver, Gold, and Platinum--for high availability, data protection, and disaster recovery. Each MAA reference architecture, or high availability tier, uses an optimal set of Oracle capabilities that, when deployed together, reliably achieve target service levels for unplanned outages and planned maintenance events.

Oracle MAA uses Chaos Engineering throughout its testing and development life cycles to ensure that end-to-end application and database availability is preserved, or at its optimal levels, for any fault or maintenance event. *Chaos Engineering* is the discipline of experimenting on a system to build confidence in the system's capability to withstand turbulent conditions in production. Specifically, MAA introduces various faults and planned maintenance events to evaluate application and database impact throughout our development, stress, and testing cycles. With that experimentation, best practices, defects, and lessons learned are derived, and that knowledge is put back into practice to evolve and improve our MAA solutions.

For more information about the MAA reference architectures, click on the objects in the graphic above, or see [**Oracle Maximum Availability Architecture**](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf).

Not explicitly listed, every database needs to run on a reliable system platform. **[Oracle Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf)** is engineered to be the highest performing and most available platform for running Oracle Databases.

Monitoring databases and systems is critical to proactively detect, prevent, and recover from issues before they have an availability impact. **[Oracle Enterprise Manager](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/index.html)** is Oracle's MAA strategic monitoring platform.

Lastly, **[Oracle Cloud](https://docs.cloud.oracle.com/iaas/Content/Database/Concepts/databaseoverview.htm)** works collaboratively and continuously with MAA to incorporate all of the MAA reference architectures, configuration best practices, and life cycle operations. Oracle Cloud and MAA evolution go hand-in-hand, delivering a fully Oracle-managed MAA solution with all cloud database services, including [**Autonomous Database**](https://docs.cloud.oracle.com/iaas/Content/Database/Concepts/adboverview.htm).






The Oracle MAA Bronze reference architecture provides basic database service at the lowest possible cost. A reduced level of high availability and data protection is accepted in exchange for reduced cost and implementation complexity. This architecture may be suitable for databases used for test, development, and less critical production applications and databases.

MAA Bronze uses the high availability capabilities included in Oracle Database Enterprise Edition. MAA Bronze defaults to the Oracle Database single-instance or multitenant architecture. Oracle Restart or Oracle Clusterware high availability capabilities are used to restart a failed instance, database server, or any relevant managed service. For logical corruptions such as human error, you can use Flashback operations to ”rewind” the database to a specific point in time. In the worst-case scenario of a complete site outage, there is additional time required to restore and recover the system and database from backups which may result in hours or days of downtime.

In MAA Bronze, a local backup within the same data center is always recommended for the fastest recovery. Oracle also recommends maintaining a second copy of backups in a remote data center to protect against site outages and disasters. You can use [Oracle Cloud Database Backup Service](https://docs.oracle.com/en/cloud/paas/db-backup-cloud/index.html) to maintain a cloud-based backup of on-premises databases.

As shown in the table below, the MAA Bronze level of service illustrates the tradeoff between reduced implementation and maintenance costs, and expected downtime during planned and unplanned outages.



| Unplanned Outage                         | RTO/RPO Service Level Objectives<sup>1</sup>                                |
|------------------------------------------|-----------------------------------------------------------------------------|
| Recoverable node or instance failure     | Minutes to hour                                                             |
| Disasters: corruptions and site failures | Hours to days<br>RPO since last backup or near zero with Recovery Appliance |
| Planned Maintenance                      | <br>                                                                        |
| Software/hardware updates                | Minutes to hour                                                             |
| Major database upgrade                   | Minutes to hour                                                             |



<sup>1</sup>RPO is zero unless explicitly specified

For more information about Oracle capabilities used in this MAA reference architecture, click on the graphic above, or click Next.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






Built on **[Oracle Database Enterprise Edition](../../dblic/Licensing-Information.md),**, the following are some of the required features to achieve an MAA Bronze level of service:

- **[Oracle Recovery Manager (RMAN)](../../haovw/ha-features.md)** is used to perform regular backups of Oracle Database. RMAN provides data validation during backup and restore operations and provides advanced capabilities such as block recovery, table level recovery, schema level recovery, and multitenant PDB and CDB backup and recovery, that is not found in third-party utilities. The RPO, if there is an unrecoverable outage, is equal to the data generated since the last database and archive backup was taken. Copies of database backups are also retained at a remote location or on the Cloud for the dual purpose of archival and disaster recovery should a disaster strike the primary data center.
- **[Automatic Storage Management (ASM)](../../haovw/ha-features.md)** is an Oracle-integrated file system and volume manager that includes intelligent data-aware software mirroring to protect against disk failure and some corruptions.
- **[Oracle Flashback Technologies](../../haovw/ha-features.md)** provide fast error correction at a level of granularity that is appropriate to repair an individual transaction, table, pluggable database (PDB), or the full database. Flashback provides the most comprehensive toolset for logical repair, and allows an administrator to view previous transaction data versions for advanced analysis and repair.
- **[Oracle Restart](../../haovw/ha-features.md)** automatically restarts the database, the listener, and other Oracle components after a hardware or software failure, or whenever a database host computer restarts. **[Oracle Clusterware](../../haovw/ha-features.md),** when available, has the same benefits.
- **[Oracle Corruption Protection](../../haovw/ha-features.md)** checks for physical corruption and logical intra-block corruptions. In-memory corruptions are detected and prevented from being written to disk, and in many cases can be repaired automatically. For more details on data protection recommendations for MAA Bronze or other tiered solutions, see [Best Practices for Corruption Detection, Prevention, and Automatic Repair - in a Data Guard Configuration (Doc ID 1302539.1).](https://support.oracle.com/rs?type=doc&id=1302539.1)

**Optionally,** you can enhance your high availability architecture by using these recommended features and capabilities:

- **[Zero Data Loss Recovery Appliance (ZDLRA)](../../haovw/ha-features.md)** provides a sophisticated data center-wide backup and recovery solution for all Oracle databases. Key benefits include: incremental backup forever after first full backup, which minimizes overall impact on the source or protected databases and significantly reduces backup windows; real-time redo transport, reducing RPO for all databases to near zero; continuous data protection and validation, to ensure recovery readiness; and enhanced recovery and migration benefits.
- **[Online Maintenance](../../haovw/ha-features.md)** includes online redefinition and reorganization for database maintenance, online file movement, and online patching.
- **[Oracle Multitenant](../../haovw/ha-features.md)** and **[Resource Manager](../../admin/managing-resources-with-oracle-database-resource-manager.md)** are the MAA best practice solutions for database consolidation and virtualization from Oracle Database 12c onward. Pluggable database (PDB) operations enable higher availability for pluggable database relocation, migration, failover, and upgrade cases. Resource Manager prevents applications and databases from consuming excessive resources, which can result in availability issues and potential downtime. Resource Manager controls can govern use of CPU, memory, OS processes, I/O (Exadata only), and network (Exadata only).

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Silver reference architecture is designed for databases that can't afford to wait for a cold restart or a restore from backup, should there be an unrecoverable database instance or server failure. This architecture may be suitable for production applications that are business critical and need to reduce downtime for local failures and most common planned maintenance activities.

MAA Silver is built on the foundation of the MAA Bronze architecture, and adds **Oracle Real Application Clusters (Oracle RAC)** active-active clustering for minimal or zero downtime in the event of database instance or server failure, as well as zero database downtime for most common planned maintenance events.

The most optimized Oracle RAC Platform with lowest application brownouts, integrated MAA configuration best practices and database and system optimizations for scaling, high availability and quality of service is Oracle's [Exadata Database Machine](https://docs.oracle.com/en/engineered-systems/exadata-database-machine/index.html), [Exadata Database Service on Cloud@Customer (Exadata Cloud@Customer Gen 2)](https://docs.oracle.com/en/engineered-systems/exadata-cloud-at-customer/), or [Exadata Database Service on Dedicated Infrastructure (Exadata Cloud Service Gen 2)](https://docs.oracle.com/en/engineered-systems/exadata-cloud-service/ecscm/index.html).

Just like in MAA Bronze, Recovery Manager (RMAN) provides database-optimized backups to restore availability should there be a complete cluster outage or disaster.

As shown in the table below, the MAA Silver level of service lets you dramatically decrease expected downtime for hardware failures, and brings most planned downtime due to software and hardware upgrades down to zero, when compared to the MAA Silver level of service.



|                                          |                                                                             |
|------------------------------------------|-----------------------------------------------------------------------------|
| Unplanned Outage                         | RTO/RPO Service Level Objectives<sup>1</sup>                                |
| Recoverable node or instance failure     | **Single digit seconds**<sup>2</sup>                                        |
| Disasters: corruptions and site failures | Hours to days<br>RPO since last backup or near zero with Recovery Appliance |
| Planned Maintenance                      |                                                                             |
| Software/hardware updates                | **Zero**<sup>2</sup>                                                        |
| Major database upgrade                   | Minutes to hour                                                             |



<sup>1</sup> RPO is zero unless explicitly specified

<sup>2</sup> To achieve zero downtime or lowest impact for online processing, apply MAA application checklist best practices. For long running transactions such as batch operations, it's best to defer outside the planned maintenance window.

For more information about Oracle capabilities used in this MAA reference architectures, click the graphic above, or click Next.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The active-active architecture of **[Oracle RAC](../../haovw/ha-features.md)** (or Oracle RAC on Extended Clusters) provides a number of advantages for the MAA Silver reference architecture:

- **Improved high availability** If a server or database instance fails, connections to surviving instances are not affected; connections to the failed instance are quickly failed over to surviving instances that are already running and open on other servers in the Oracle RAC cluster.
- **Scalability** Oracle RAC is ideal for high volume applications or consolidated environments where scalability and the ability to dynamically add or re-prioritize capacity across more than a single server are required. An individual database may have instances running on one or more nodes of a cluster. Similarly, a database service may be available on one or more database instances. Additional nodes, database instances, and database services can be provisioned online. The ability to easily distribute workload across the cluster makes Oracle RAC the ideal complement for **[Oracle Multitenant](../../haovw/ha-features.md)** when consolidating many databases.
- **Reliable performance** in consolidated database environments can be delivered by using **[Oracle Quality of Service (QoS)](../../cwadd/oracle-clusterware-administration.md)** to allocate capacity for high priority database services. Capacity can be dynamically shifted between workloads to quickly respond to changing requirements.
- **[High availability maintained during planned maintenance](../../haovw/ha-planned-downtime.md)** by implementing changes in a rolling manner across Oracle RAC nodes. This includes database, hardware, operating system, or network maintenance that requires a server or database instance to be taken offline or restarted; software maintenance to update or patch the database or Oracle Grid Infrastructure; or moving a database instance to another server to increase capacity or balance the workload.
- **[Application Failover Practices or Application Continuity](http://www.oracle.com/pls/topic/lookup?ctx=db19&id=GUID-5EBF37EA-48AB-4508-A14E-86A2583A24BF)** mask recoverable outages and Oracle RAC rolling planned maintenance activities in the application tier by draining and relocating connections and optionally replaying application requests at another available Oracle RAC instance. With application checklist practices, Oracle recommends simple non-intrusive application changes that include 1) using Oracle services, 2) modifying connection strings, and 3) enabling fast application notification and draining. Optionally enabling application continuity or transparent application continuity (TAC) requires some additional application investment to reap benefits of application replay after failure. For steps and guidance, see [Continuous Availability - Application Checklist for Continuous Service for MAA Solutions](https://www.oracle.com//technetwork/database/clustering/checklist-ac-6676160.pdf)
- [**Oracle Clusterware**](../../haovw/ha-features.md), grouped with Oracle Automatic Storage Management (ASM) as Oracle Grid Infrastructure, is the integrated foundation for Oracle Real Application Clusters and the high availability and resource management framework for all applications on any major platform supported for Oracle RAC.
- **Site Failure and limited DR protection (Oracle RAC on Extended Clusters only)** is provided when a single database consisting of Oracle RAC nodes is spread across multiple data centers. If a site failure occurs with an **[Oracle RAC on Extended Clusters](https://www.oracle.com/technetwork/database/availability/maa-extclusters-installguide-3748227.pdf)** architecture (also known as Oracle Stretched RAC or Oracle Extended RAC), the application can transparently fail over to surviving Oracle RAC nodes and instances in the other sites. To ensure stability and performance, Oracle RAC on Extended Clusters requires low network latency (less than 1 ms) and high network bandwidth (10 GigE or higher) for Oracle RAC interconnect. An additional storage quorum device in a third site and **[Oracle ASM Extended Disk Groups](../../ostmg/asm-filegroups.md)** are required. Oracle RAC on Extended Clusters gives you the benefits of Oracle RAC but does not comprehensively address disaster recovery. Oracle MAA recommends adding [**Oracle Data Guard**](../../haovw/ha-features.md) to complete the MAA Gold architecture so that other unplanned outages such as data corruptions, database failures, cluster failures, and regional failures are covered.

MAA Silver requires **[Oracle Database Enterprise Edition](../../dblic/Licensing-Information.md)**, **[Oracle RAC](../../haovw/ha-features.md)**, and **[Oracle Enterprise Manager](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/index.html)** life-cycle, management, diagnostic, and tuning packs for on-premises databases. **[Oracle RAC One-Node](../../haovw/ha-features.md)** is an option for active-passive high availability if scalability is not required, and your environment can tolerate slightly higher recovery time for database and Oracle RAC instance failures.

Optionally, you can enhance your high availability architecture by using these recommended features and capabilities:

- [**Fleet Patching and Provisioning**](../../fppad/fleet-patching-provisioning.md)
- [**Oracle Exadata Database Machine**](https://www.oracle.com/a/tech/docs/exadata-maa-wp.pdf) or **[Exadata Cloud Service](https://docs.cloud.oracle.com/iaas/Content/Database/Concepts/exaoverview.htm)**

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Gold reference architecture is well suited for service level requirements that cannot tolerate long periods of downtime and data loss. This set of architecture patterns provides high availability and comprehensive data protection for all types of unplanned outages, including data corruptions, database failures, and site outages. Mission critical production applications that require quick recovery time and zero or minimal data loss for all database and system outages and planned maintenance activities will benefit from the capabilities included in the Gold reference architecture.

MAA Gold, building on MAA Silver, provides you with four architecture patterns using [**Oracle Active Data Guard**](../../haovw/ha-features.md) (or Oracle Data Guard). While Active Data Guard provides better RTO and protection overall, both Oracle Active Data Guard and Data Guard are viable for MAA Gold.

The architecture patterns vary from a single remote active standby with Fast Start Failover and HA Observer, to multiple standby database configurations including standby reader farms, and finally a far sync (across regions) zero data loss standby configuration.

As shown in the table below, the MAA Gold level of service reduces failover and switchover times from hours to seconds, and lets you do major database upgrades with minimal interruptions.



|                                          |                                                     |
|------------------------------------------|-----------------------------------------------------|
| Unplanned Outage                         | RTO/RPO Service Level Objectives<sup>1</sup>        |
| Recoverable node or instance failure     | Single digit seconds<sup>2</sup>                    |
| Disasters: corruptions and site failures | **Seconds to 2 minutes**<br>**RPO zero or seconds** |
| Planned Maintenance                      | <br>                                                |
| Software/hardware updates                | Zero<sup>2</sup>                                    |
| Major database upgrade                   | **Less than 30 seconds**                            |



<sup>1</sup> RPO is zero unless explicitly specified

<sup>2</sup> To achieve zero downtime or lowest impact for online processing, apply MAA application checklist best practices. For long running transactions such as batch operations, it's best to defer outside the planned maintenance window.

Click on the graphic above, or click Next, for details about each architecture pattern for MAA Gold.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Gold Remote Standby pattern includes a remote synchronized copy of the production database (Standby Database) using [**Oracle Active Data Guard**](../../haovw/ha-features.md) to eliminate single point of failure. The active standby database provides a high level of protection from unplanned outages and reduces downtime for planned maintenance activities, such as database upgrades. The most notable attribute is that the standby provides low RTO (recovery time) and RPO (data loss potential) in the case of a disaster such as a database, cluster, or site failure.

For more information about Oracle capabilities used in this MAA reference architecture, click the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Gold Multiple Standby Databases pattern gives you the benefits of both local and remote standby databases.

Automatic failover to a local standby in the same region provides you with significant local disaster isolation and application failover simplicity. The local standby can be located in a separate fault domain or availability domain from the primary database. Application failover in this architecture pattern follows the recommendations described in [Continuous Availability - Application Checklist for Continuous Service for MAA Solutions.](https://www.oracle.com//technetwork/database/clustering/checklist-ac-6676160.pdf)

The business value of a local standby database is seen in zero data loss failover and application downtime reduced to seconds. By enabling synchronous redo transport, a zero data loss Data Guard configuration becomes more viable due to the lower latency between primary and standby database systems. Applications automatically and transparently fail over to the local standby, maintaining the same latency between application servers and the database, which is particularly important for OLTP applications and package applications, because higher latency can significantly impact throughput and overall application response time.

If a regional disaster occurs, making the primary and local standby systems inaccessible, the application and database can fail over to the remote standby. Even though database downtime is still very low when regional disaster occurs, the application downtime can be higher due to additional orchestration required for DNS, application, and database failover operations to the secondary region.

To make the secondary region symmetric, you can add another standby in that region. Another variation is to add additional standby databases for reporting.

For more information about Oracle capabilities used in this MAA reference architecture, click the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Gold Standby Reader Farm pattern provides all of the benefits of the MAA Gold Multiple Standby Databases pattern, plus it allows read-only operations to scale across many standby databases for local and regional reader farm scalability.

For more information about Oracle capabilities used in this MAA reference architecture, click the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Gold Cross-Region Far Sync Standby pattern gives you a zero data loss solution when network latency or distance between primary and standby are too great. When a transaction commits, the redo is acknowledged by a fault independent far sync server that validates and resubmits the changes to remote standby. If a primary database failure or possibly site failure occurs, the surviving far sync server sends the last committed changes to remote standby ensuring zero data loss.

Note that this configuration requires Oracle Active Data Guard for Far Sync, although other MAA Gold patterns have expanded to include Oracle Data Guard or Oracle Active Data Guard.

For more information about Oracle capabilities used in this MAA reference architecture, click the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






MAA Gold, based on an [**Oracle Active Data Guard**](../../haovw/ha-features.md) solution with a primary and standby database, provides a number of advantages for MAA Gold.

- **Improved data protection.** If a primary or standby database detects a physical data corruption, Oracle can initiate auto block repair on the data corruption with zero application and database downtime. This is a major benefit to maintain data integrity and availability for all databases in an Active Data Guard environment. Furthermore, the standby database can detect lost writes and logical block corruptions, prevent logical corruptions, and provide a mechanism to fail over automatically, reducing the impact of these corruptions and downtime.
- **Disaster recovery protection** with reduced downtime and zero or near zero data loss from database, cluster, or site failures, application protection, and a reduced downtime and data loss solution using the standby database.
  - **Zero Data Loss with Maximum Availability or Maximum Protection** modes with synchronous transport support. **Near zero data loss with Maximum Performance** with streaming ASYNC transport support.
  - **Bounded RTO (recovery time) and RPO (data loss) with Data Guard Fast-Start Failover.** The maximum protection and maximum availability modes provide an automatic failover environment guaranteed to lose no data. Maximum performance mode provides an automatic failover environment guaranteed to lose no more than the amount of data (in seconds) specified by the FastStartFailoverLagLimit configuration property. This property indicates the maximum amount of data loss that is permissible in order for an automatic failover to occur. All Data Guard Fast-Start Failover solution provides a quorum of 2 to ensure data consistency in this distributed Data Guard environment.
- **Offload workload and operation from primary databases** to the standby database.
  - Expensive backup operations, and those respective backups can be used to restore the primary or standby databases
  - Read-intensive queries and report jobs
  - Testing software or hardware updates on the standby to ensure overall availability and integrity prior to applying the same changes on the primary provides additional validation besides using just test environments
  - Testing with snapshot standby without sacrificing potential data loss
  - Validation and early detection, prevention and auto repair of data corruptions are built-in with Active Data Guard and redo apply
- **Reduce downtime for planned maintenance** by implementing changes in an Oracle RAC and Data Guard rolling manner across Oracle RAC nodes or primary and standby databases. Using [**DBMS_ROLLING**](../../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md) and transient logical solution, the standby can be upgraded and switched to with seconds of downtime while maintaining disaster recovery protection.
- **[Application Failover Best Practices or Application Continuity](http://www.oracle.com/pls/topic/lookup?ctx=db19&id=GUID-5EBF37EA-48AB-4508-A14E-86A2583A24BF)** reduces downtime for primary database failure or complete database planned maintenance by draining and relocating connections and optionally replaying application requests at the new primary database after a Data Guard role transition. Application failover best practices recommend simple non-intrusive application changes that include using Oracle services, modifying connection strings to accommodate both primary and local standby databases, and enabling fast application notification and draining. Optionally enabling Application Continuity or Transparent Application Continuity (TAC) will require some additional application investment to reap the benefits of application replay after failure. See [Continuous Availability - Application Checklist for Continuous Service for MAA Solutions](https://www.oracle.com/technetwork/database/clustering/checklist-ac-6676160.pdf) for steps and guidance.
- **Simplify migration** to new platforms and technologies by using standby database to switch to new platform like Exadata or Exadata cloud or to enable new database options and capabilities like Transparent Data Encryption (TDE)..

Optionally, you can enhance your MAA Gold high availability architecture by using these recommended features and capabilities:

- [**Global Data Services**](../../gsmug/intro-global-data-services.md) is an Oracle Database workload management solution that provides dynamic load balancing of client connections and workload requests across the replicas.
- **[Full Stack Disaster Recovery](https://docs.oracle.com/iaas/disaster-recovery/index.html)** is an Oracle Cloud Infrastructure (OCI) disaster recovery orchestration and management service that provides comprehensive disaster recovery capabilities for all layers of an application stack, including infrastructure, middleware, database, and application.
- Select **[Oracle Enterprise Manager](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/index.html)** packs

To achieve an MAA Gold level of service use **[Oracle Active Data Guard](../../haovw/ha-features.md)** and **[Oracle RAC](../../haovw/ha-features.md)**.

Oracle Active Data Guard provides more Oracle database protection and advantages than third party replication, as shown in the following table.



| **Benefits**                                                                                                                                 | **Oracle Active Data Guard**      | **Third Party Replication**                                                                         |
|----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|-----------------------------------------------------------------------------------------------------|
| Data corruption protection                                                                                                                   | Yes                               | No                                                                                                  |
| Auto block repair of physical block corruptions                                                                                              | Yes                               | No                                                                                                  |
| RTO                                                                                                                                          | Seconds to 2 minutes              | Up to 30 minutes                                                                                    |
| RPO                                                                                                                                          | Zero or near zero                 | Zero (within region only) to near zero                                                              |
| Active standby reporting                                                                                                                     | Yes                               | None (additional copies required to create reporting database)                                      |
| Network bandwidth required                                                                                                                   | Small (redo changes only)         | Typical 7X bandwidth because all database, redo, temp, undo, and controlfile changes are replicated |
| Application integration                                                                                                                      | Yes (with Application Continuity) | None (needs to be customized)                                                                       |
| Automatic failover with quorum of 2 with Data Guard broker observers (preserves data consistency and prevents split brain primary databases) | Yes                               | None (needs to be customized)                                                                       |
| Database rolling upgrade (DBMS_ROLLING)                                                                                                      | Yes                               | No                                                                                                  |
| Scalable reader farm while maintaining protection and disaster recovery                                                                      | Yes                               | No                                                                                                  |



For more information about Oracle capabilities used in this MAA reference architectures click on the objects in the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Platinum reference architecture has the potential to provide zero downtime for outages and planned maintenance activities that are not achievable with MAA Gold. MAA Platinum builds on MAA Gold by adding **Oracle GoldenGate** replication to eliminate downtime for migrations, application upgrades, and database upgrades. Each Oracle GoldenGate database is protected by a standby database to enable zero or near data loss in case of database, cluster, or site failure.

Oracle GoldenGate provides the following benefits:

- Uni-directional or bi-directional, replication allowing reads and updates in any replica if desired
- Replicas can run on different platforms, database versions, or database or application configurations, allowing for online migration and database and application upgrades
- Replicas are online, so applications can switch over with zero downtime during outages and planned maintenance activities (note that the application switchover must be customized, rather than built in as it is with Application Continuity)

Unlike the other MAA architectures, application considerations are required to integrate Oracle GoldenGate into the architecture, especially if there’s a need to switch over to other replicas. Global Data Services, or custom application service management may be required to achieve zero or minimum application downtime for activities such as migration, database upgrade, or site switch when one replica is down. Also, if multiple replicas are updated concurrently at any point, conflict detection and resolution must be configured.

To address zero downtime application upgrade, the best solution is to make application changes on an alternative primary database replica and then switch over from the primary database to the alternative primary database replica when all transactions are synchronized.

As shown in the table below, the MAA Platinum level of service addresses the most mission critical Oracle requirements, and delivers zero data loss and highest uptime potential.



|                                          |                                                |
|------------------------------------------|------------------------------------------------|
| Unplanned Outage                         | RTO/RPO Service Level Objectives<sup>1</sup>   |
| Recoverable node or instance failure     | **Zero or single digit seconds**<sup>2,3</sup> |
| Disasters: corruptions and site failures | **Zero**<sup>3</sup>                           |
| Planned Maintenance                      | <br>                                           |
| Software/hardware updates                | Zero<sup>2</sup>                               |
| Major database upgrade                   | **Zero**<sup>3</sup>                           |



<sup>1</sup> RPO is zero unless explicitly specified

<sup>2</sup> To achieve zero downtime or lowest impact for online processing, apply MAA application checklist best practices. For long running transactions such as batch operations, it's best to defer outside the planned maintenance window.

<sup>3</sup> Application failover is custom or with Global Data Services

For more information about Oracle capabilities used in this MAA reference architectures, click on the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**






The MAA Platinum reference architecture requires the same services as MAA Gold, plus **[Oracle GoldenGate](../../haovw/ha-features.md)** for on-premises deployments, or **[Oracle GoldenGate Cloud Service](https://www.oracle.com/integration/goldengate/)** for cloud deployments. See [MAA Platinum and Oracle GoldenGate Best Practices](../../haovw/maa-platinum-reference-architecture-overview.md) for more information.

For more information about Oracle capabilities used in this MAA reference architectures click on the objects in the graphic above.

Learn more about Oracle MAA blueprints for reduced planned and unplanned downtime for Oracle Database **[on-premises](https://www.oracle.com/a/tech/docs/maa-onpremises-overview.pdf),** on **[Exadata Database Machine](https://www.oracle.com/a/tech/docs/exadata-maa.pdf),** and on **[Oracle Cloud](https://www.oracle.com/a/tech/docs/cloud-maa-overview.pdf).**
