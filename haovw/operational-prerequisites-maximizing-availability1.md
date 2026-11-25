## 7 Operational Prerequisites to Maximizing Availability

Use the following operational best practices to provide a successful MAA implementation.

### Understand High Availability and Performance Service-Level Agreements

Understand and document your high availability (HA) and performance service-level agreements (SLAs):

- Understand the attributes of High Availability and various causes of downtime as described in [Overview of High Availability](overview-of-ha.md).

- Establish high availability and performance SLAs from lines of business, upper management, and technical teams as described in [High Availability Requirements](ha-requirements-architecture.md), and [A Methodology for Documenting High Availability Requirements](ha-requirements-architecture.md).

### Implement and Validate a High Availability Architecture That Meets Your SLAs

When you have agreement on your high availability and performance service level requirements:

- Map the requirements to one of the Oracle MAA standard and validated MAA reference architectures, as described in [High Availability and Data Protection – Getting From Requirements to Architecture](ha-requirements-architecture.md)
- Evaluate the outage and planned maintenance matrices relevant to your reference architecture in [Oracle Database High Availability Solutions for Unplanned Downtime](ha-unplanned-downtime.md) and [Oracle Database High Availability Solutions for Planned Downtime](ha-planned-downtime.md)
- Learn about the database features required to implement your MAA architecture in [High Availability Architectures](https://docs.oracle.com/en/database/oracle/oracle-database/21/haiad/)

### Establish Test Practices and Environment

You must validate or automate the following to ensure that your high availability SLAs are met:

- All software update and upgrade maintenance events
- All repair operations, including those for various types of unplanned outages
- Backup, restore, and recovery operations

If you use Oracle Data Guard for disaster recovery and data protection, Oracle recommends that you:

- Perform periodic switchover operations, or conduct full application and database failover tests
- Validate end-to-end role transition procedures by performing application and Data Guard switchovers periodically

A good test environment and proper test practices are essential prerequisites to achieving the highest stability and availability in your production environment. By validating every change in your test environment thoroughly, you can proactively detect, prevent, and avoid problems before applying the same change on your production systems.

These practices involve the following:

#### Configuring Test and QA Environments

The test environment should be a replica of the production MAA environment (for example, using the MAA Gold reference architecture.) There will be trade offs if the test system is not identical to the MAA service-level driven standard reference architecture that you plan to implement. It is recommended that you perform functional, performance, and availability tests with a workload that mimics production. Evaluate if availability and performance SLAs are maintained after each change, and ensure that clear fallback or repair procedures are in place if things go awry, while applying the change on the production environment.

With a properly configured test system, many problems can be avoided, because changes are validated with an equivalent production and standby database configuration containing a full data set and using a workload framework to mimic production (for example, using Oracle Real Application Testing.)

Do not try to reduce costs by eliminating the test system, because that decision ultimately affects the stability and the availability of your production applications. Using only a subset of system resources for testing and QA has the tradeoffs shown in the following table, which is an example of the MAA Gold reference architecture.

Table 7-1 Tradeoffs for Different Test and QA Environments

| Test Environment                                                          | Benefits and Tradeoffs                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Full Replica of Production and Standby Systems                            | Validate:<br>• All software updates and upgrades<br>• All functional tests<br>• Full performance at production scale<br>• Full high availability and disaster recovery testing                                                                                                                                                                                                                                                                                                                                 |
| Full Replica of Production Systems                                        | Validate:<br>• All software updates and upgrades<br>• All functional tests<br>• Full performance at production scale<br>• Full high availability minus the standby system<br>Cannot Validate:<br>• Disaster recovery testing<br>• Any standby redo apply or read only workload performance testing<br>• Redo transport performance and impact on production system resources due to redo transport<br>• Any use case using the standby database such as Database Rolling Upgrade, Snapshot Standby, and so on. |
| Standby System                                                            | Validate:<br>• Most software update changes<br>• All read-only functional tests<br>• Full performance--if using Data Guard Snapshot Standby, but this can extend recovery time if a failover is required<br>• Resource management and scheduling--required if standby and test databases exist on the same system<br>Cannot Validate:<br>• Role transition and disaster recovery testing<br>• Any use case using the standby database such as Database Rolling Upgrade, Snapshot Standby, and so on.           |
| Shared System Resource                                                    | Validate:<br>• Most software update changes<br>• All functional tests<br>Cannot Validate:<br>This environment may be suitable for performance testing if enough system resources can be allocated to mimic production. Typically, however, the environment includes a subset of production system resources, compromising performance validation. Resource management and scheduling is required. Standby or disaster recovery testing may not be possible or limited.                                         |
| Smaller or Subset of the system resources                                 | Validate:<br>• All software update changes<br>• All functional tests<br>• Limited full-scale high availability evaluations<br>Cannot Validate:<br>• Performance testing at production scale<br>• Standby or disaster recovery testing may not be possible or limited.                                                                                                                                                                                                                                          |
| Different hardware or platform system resources but same operating system | Validate:<br>• Some software update changes<br>• Limited firmware patching test<br>• All functional tests unless limited by new hardware features<br>• Limited production scale performance tests<br>• Limited full-scale high availability evaluations<br>• Standby or disaster recovery testing may not be possible or limited.                                                                                                                                                                              |

**See Also:**

[Oracle Database Testing Guide](../ratug/introduction-to-oracle-database-testing.md)

#### Performing Preproduction Validation Steps

Pre-production validation and testing of hardware, software, database, application or any changes is an important way to maintain stability. The high-level pre-production validation steps are:

1.  Review the patch or upgrade documentation or any document relevant to that change. Evaluate the possibility of performing a rolling upgrade if your SLAs require zero or minimal downtime. Evaluate any rolling upgrade opportunities to minimize or eliminate planned downtime. Evaluate whether the patch or the change qualifies for Standby-First Patching.

    Note:

    Standby-First Patch enables you to apply a patch initially to a physical standby database while the primary database remains at the previous software release (this applies to certain types of software updates and does not apply to major release upgrades; use the Data Guard transient logical standby and DBMS_ROLLING method for patch sets and major releases). Once you are satisfied with the change, then perform a switchover to the standby database. The fallback is to switchback if required. Alternatively, you can proceed to the following step and apply the change to your production environment. For more information, see "Oracle Patch Assurance - Data Guard Standby-First Patch Apply" in My Oracle Support Note 1265700.1 at <https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1265700.1>

2.  Validate the application in a test environment and ensure the change meets or exceeds your functionality, performance, and availability requirements. Automate the procedure and be sure to also document and test a fallback procedure. This requires comparing metrics captured before and after patch application on the test and against metrics captured on the production system. Real Application Testing may be used to capture the workload on the production system and replay it on the test system. AWR and SQL Performance Analyzer may be used to assess performance improvement or regression resulting from the patch.

    Validate the new software on a test system that mimics your production environment, and ensure the change meets or exceeds your functionality, performance, and availability requirements. Automate the patch or upgrade procedure and ensure fallback. Being thorough during this step eliminates most critical issues during and after the patch or upgrade.

3.  Use Oracle Real Application Testing and test data management features to comprehensively validate your application while also complying with any security restrictions your line of business may have. Oracle Real Application Testing (a separate database option) enables you to perform real-world testing of Oracle Database. By capturing production workloads and assessing the impact of system changes on these workloads before production deployment, Oracle Real Application Testing minimizes the risk of instabilities associated with system changes. SQL Performance Analyzer and Database Replay are key components of Oracle Real Application Testing. Depending on the nature and impact of the system change being tested, and on the type of system on which the test will be performed, you can use either or both components to perform your testing.

    When performing real-world testing there is a risk of exposing sensitive data to non-production users in a test environment. The test data management features of Oracle Database help to minimize this risk by enabling you to perform data masking and data subsetting on the test data.

4.  If applicable, perform final pre-production validation of all changes on a Data Guard standby database before applying them to production. Apply the change in a Data Guard environment, if applicable.

5.  Apply the change in your production environment.

**See Also:**

[Data Guard Redo Apply and Standby-First Patching](ha-features.md) and [Data Guard Transient Logical Rolling Upgrades](ha-features.md)

[Converting a Physical Standby Database into a Snapshot Standby Database](../sbydb/managing-oracle-data-guard-physical-standby-databases.md) and [Performing a Rolling Upgrade With an Existing Physical Standby Database](../sbydb/using-sql-apply-to-perform-rolling-upgrade.md) in Oracle Data Guard Concepts and Administration

[Oracle Database Rolling Upgrades: Using a Data Guard Physical Standby Database](https://www.oracle.com/technetwork/database/availability/database-upgrade-dbms-rolling-4126957.pdf) on <http://www.oracle.com/goto/maa>

[Oracle Patch Assurance - Data Guard Standby-First Patch Apply (Doc ID 1265700.1)](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1265700.1)

### Set Up and Use Security Best Practices

Corporate data can be at grave risk if placed on a system or database that does not have proper security measures in place. A well-defined security policy can help protect your systems from unwanted access and protect sensitive corporate information from sabotage. Proper data protection reduces the chance of outages due to security breaches.

**See Also:**

[Oracle Database Security Guide](../dbseg/introduction-to-oracle-database-security.md).

### Establish Change Control Procedures

Institute procedures that manage and control changes as a way to maintain the stability of the system and to ensure that no changes are incorporated in the primary database unless they have been rigorously evaluated on your test systems, or any one of the base architectures in the MAA service-level tiers.

Review the changes and get feedback and approval from your change management team.

### Apply Recommended Software Updates and Security Updates Periodically

Maintaining software at current or recent versions provides many benefits, such as better software security, improved resource utilization and stability, continued compatibility with newer related software, better support and faster resolution of issues, and the ability to receive fixes for newly discovered issues.

Update all software on a regular basis. Oracle recommends following these practices:

- Learn the release and support timelines for all software that your MAA environment depends upon in order to develop a plan for upgrade to a new major software release and a plan for installing proactive updates for current releases.

  For example, Oracle Database release and support timelines is available in My Oracle Support Note 742060.1 “Release Schedule of Current Database Releases”.

- Upgrade to a later major software release before proactive software updates for your current release cease.

- Install proactive software updates for your current release as they become available, typically on a monthly or quarterly basis.

  However, business requirements may dictate that the adoption of certain proactive updates is delayed or skipped. In such cases Oracle recommends that the currently running software never lags the most recently released proactive update by more than 12 months.

- Install reactive software patches (also known as interim or one-off patches) for critical issues published in My Oracle Support Alerts as soon as feasible.

- Validate the software update process and perform soak testing on a test system before updating software on production systems.

- Use Oracle health check tools, Orachk and Exachk, to provide Oracle software upgrade and proactive update advice, critical issue software update recommendations, patching and upgrading pre-checks, database and system health checks, and MAA recommendations.

  Orachk supports non-engineered systems and Oracle Database Appliance. Exachk supports engineered systems Oracle Exadata Database Machine and Oracle Zero Data Loss Recovery Appliance.

See also:

For Oracle Database and Grid Infrastructure:

- “Release Schedule of Current Database Releases” in My Oracle Support Note [742060.1](https://support.oracle.com/rs?type=doc&id=742060.1)
- "Primary Note for Database Proactive Patch Program" in My Oracle Support Note [888.1](https://support.oracle.com/rs?type=doc&id=888.1)
- "Oracle Database 19c Important Recommended One-off Patches" in My Oracle Support Note [555.1](https://support.oracle.com/rs?type=doc&id=555.1)

For engineered systems (Exadata Database Machine and Zero Data Loss Recovery Appliance):

- "Exadata Database Machine and Exadata Storage Server Supported Versions" in My Oracle Support Note [888828.1](https://support.oracle.com/rs?type=doc&id=888828.1)
- “Exadata Critical Issues” in My Oracle Support Note [1270094.1](https://support.oracle.com/rs?type=doc&id=1270094.1)
- "Oracle Exadata: Exadata and Linux Important Recommended Fixes" in My Oracle Support Note [556.1](https://support.oracle.com/rs?type=doc&id=556.1)
- "Oracle Exadata Database Machine Exachk" in My Oracle Support Note [1070954.1](https://support.oracle.com/rs?type=doc&id=1070954.1)

For non-engineered systems:

- "Autonomous Health Framework (AHF) - Including TFA and Orachk/Exachk" in My Oracle Support Note [2550798.1](https://support.oracle.com/rs?type=doc&id=2550798.1)

### Establish Disaster Recovery Environment

To achieve the same performance and HA characteristics as the source or primary database, the disaster recovery environment or target should be symmetric or similarly configured to the production system.

If the disaster recovery target is a standby database or Oracle GoldenGate replica, symmetric or similar database compute CPU, memory, and throughput is required to match the same performance. Similarly, the storage should be able to handle the same IOPS, throughput, and response time.

When the disaster recovery target is used by other applications or databases for database consolidation and cost efficiency, additional resources will be required to ensure acceptable performance with other concurrent workloads.

### Establish and Validate Disaster Recovery Practices 

Disaster recovery validation is required to ensure that you meet your disaster recovery service level requirements such as RTO and RPO.

Whether you have a standby database, Oracle GoldenGate replica, or leverage database backups from Zero Data Loss Recovery Appliance (Recovery Appliance), ZFS Storage, or another third party, it is important to ensure that the operations and database administration teams are well prepared to failover or restore the database and application any time the primary database is down or underperforming. The concerned teams should be able to detect and decide to failover or restore as required. Such efficient preparation before disasters will significantly reduce overall downtime.

If you use Data Guard or Oracle GoldenGate for high availability, disaster recovery, and data protection, Oracle recommends that you perform regular application and database switchover operations every three to six months, or conduct full application and database failover tests.

Periodic RMAN cross checks, RMAN backup validations, and complete database restore and recovery are required to validate your disaster recovery solution through backups. Inherent backup checks and validations are done automatically with the Recovery Appliance, but periodic restore and recovery tests are still recommended.

See also: [Role Transition, Assessment, and Tuning](tune-and-troubleshoot-oracle-data-guard.md)

### Establish Escalation Management Procedures

Establish escalation management procedures so repair is not hindered. Most repair solutions, when conducted properly are automatic and transparent with the MAA solution. The challenges occur when the primary database or system is not meeting availability or performance SLAs and failover procedures are not automatic as in the case with some Data Guard failover scenarios. Downtime can be prolonged if proper escalation policies are not followed and decisions are not made quickly.

If availability is the top priority, perform failover and repair operations first and then proceed with gathering logs and information for Root Cause Analysis (RCA) after the application service has been reestablished. For simple data gathering, use the Trace File Analyzer Collector (TFA).

**See Also:**

MAA web page at [`http://www.oracle.com/goto/maa`](http://www.oracle.com/goto/maa)

My Oracle Support note 1513912.2 “TFA Collector - Tool for Enhanced Diagnostic Gathering” at [1513912.2](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1513912.2)

### Configure Monitoring and Service Request Infrastructure for High Availability

To maintain your High Availability environment, you should configure the monitoring infrastructure that can detect and react to performance and high availability related thresholds before any downtime has occurred.

Also, where available, Oracle can detect failures, dispatch field engineers, and replace failed hardware components such as disks, flash cards, fans, or power supplies without customer involvement.

#### Run Database Health Checks Periodically

Oracle Database health checks are designed to evaluate your hardware and software configuration and MAA compliance to best practices.

All of the Oracle health check tools will evaluate Oracle Grid Infrastructure, Oracle Database, and provide an automated MAA scorecard or review that highlights when key architectural and configuration settings are not enabled for tolerance of failures or fast recovery. For Oracle's engineered systems such as Exadata Database Machine, there may be hundreds of additional software, fault and configuration checks.

Oracle recommends periodically (for example, monthly for Exadata Database Machine) downloading the latest database health check, running the health check, and addressing the key FAILURES, WARNINGS, and INFO messages. Use Exachk for Engineered Systems such as Oracle Exadata Database Machine and Oracle Zero Data Loss Recovery Appliance, and use Orachk for non-engineered systems and Oracle Database Appliance.

Furthermore, it is recommended that you run the health check prior to and after any planned maintenance activity.

You must evaluate:

- Existing or new critical health check alerts prior to planned maintenance window

- Existing software or critical software recommendations

- Adding any new recommendations to the planned maintenance window after testing

**See Also:**

My Oracle Support Note 1268927.2 "ORAchk - Health Checks for the Oracle Stack" at [`https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1268927.2`](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1268927.2)

My Oracle Support Note 1070954.1 "Oracle Exadata Database Machine exachk or HealthCheck" at [`https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1070954.1`](https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1070954.1)

#### Configure Monitoring

When deciding on the best route for monitoring your Exadata fleet, you need to consider how the fleet you are monitoring is deployed (On-Premises, Cloud@Customer, Oracle Cloud Infrastructure) and where your monitoring is or can be deployed.

- On-Premises

  For fleets including on-premises Exadata, Enterprise Manager includes necessary monitoring for responsibilities spanning all three deployment types and is the MAA Best Practice.

- Cloud

  For fleets only in Cloud@Customer and/or OCI, who do not currently have Enterprise Manager or On-Premises monitoring deployment options, the OCI Observability & Management services provide various options for basic and advanced monitoring and manageability.

Configure Oracle Enterprise Manager Monitoring

If your Exadata fleet includes On-Premises deployment, you should configure and use Enterprise Manager and the monitoring infrastructure that detects and reacts to performance and high availability related thresholds to avoid potential downtime.

The monitoring infrastructure assists you with monitoring for High Availability and enables you to do the following:

- Monitor system, network, application, database and storage statistics

- Monitor performance and service statistics

- Create performance and high availability thresholds as early warning indicators of system or application problems

- Provide performance and availability advice

- Established alerts and tools and database performance

- Receive alerts for engineered systems hardware faults

Enterprise Manager provides monitoring and management for Exadata and Databases deployed on-premises, on Cloud@Customer, and OCI.

- For on-premises Exadata deployments, see [Oracle Exadata Database Machine Getting Started Guide](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/emxig/oracle-exadata-database-machine-administration.html#GUID-045490C8-F951-4673-AE3A-DC84596CDDA4).
- For Cloud@Customer and OCI Exadata deployments, see [Oracle Enterprise Manager Cloud Control for Oracle Exadata Cloud](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/emxcs/introduction-monitoring-exadata-cloud-service.html#GUID-1D4FF933-7ECC-4650-99A4-FC16FCEB97DF)

Configure Enterprise Manager for high availability to ensure that the manageability solution is as highly available as the systems that you're monitoring.

For configuration details for HA see [Oracle Enterprise Manager Cloud Control Advanced Installation and Configuration Guide](https://docs.oracle.com/en/enterprise-manager/cloud-control/enterprise-manager-cloud-control/13.5/emadv/high-availability-solutions.html#GUID-5AEB4464-DCAA-4C3D-9A02-D5D51FD262B1). For additional MAA Best Practices for Enterprise Manager see <http://www.oracle.com/goto/maa>.

Oracle Observability and Management Services can be used in conjunction with Enterprise Manager to provide additional Exadata manageability features. For details, see the following:

- Operations Insights [Exadata Insights](https://docs.oracle.com/iaas/operations-insights/doc/exadata-insights.html)
- [Harvest Entity Model Data from Enterprise Manager Cloud Control Collect Logs](https://docs.oracle.com/iaas/logging-analytics/doc/harvest-entity-model-data-enterprise-manager-cloud-control-and-collect-logs.html)

Configure OCI Observability and Management Services Monitoring

If your Exadata fleet includes only Cloud@Customer and/or OCI deployment, and you do not currently have Enterprise Manager or on-premises monitoring deployment options, you should configure and use the OCI Observability and Management platform of services that work together to provide monitoring and management of Oracle Cloud targets.

Basic default metrics and events for performance, high availability, and health are available in the OCI console. For details see the following documentation:

- Exadata Database Service on Dedicated Infrastructure
  - Metrics for [VM Clusters](https://docs.oracle.com/iaas/exadatacloud/exacs/monitor-metrics-for-vmcluster-resources.html) and [Exadata Database Service on Dedicated Infrastructure](https://docs.oracle.com/iaas/exadatacloud/exacs/metrics-for-exadata-database-service-on-dedicated-infrastructure-in-the-monitoring-service.html#GUID-B82F2A9D-56C4-459A-9EEE-A3330741F31F) available in the Monitoring Service
  - [Events](https://docs.oracle.com/iaas/exadatacloud/exacs/ecs-events.html#GUID-2D522773-82F2-49B3-8DDF-6B2928AC5DB9)
- Exadata Database Service on Cloud@Customer
  - Metrics for [VM Clusters](https://docs.oracle.com/iaas/exadata/doc/monitor-metrics-for-vm-cluster-resources.html) and [Exadata Database Service on Cloud@Customer](https://docs.oracle.com/en/engineered-systems/exadata-cloud-at-customer/ecccm/metrics-for-exacc-in-the-monitoring-service.html#GUID-07C62351-92DB-45B6-A661-315A88B5F049) available in the Monitoring Service
  - [Events](https://docs.oracle.com/iaas/exadata/doc/ecc-customer-events.html)

Advanced metrics and management features are available in the Database Management service:

- Exadata Database Service on Dedicated Infrastructure
  - Metrics available in the [Database Management Service](https://docs.oracle.com/iaas/database-management/doc/database-management-oracle-databases.html)
  - [Diagnose and Troubleshoot Problems with Pluggable Databases](https://docs.oracle.com/iaas/exadatacloud/exacs/monitor-metrics-to-diagnose-and-troubleshoot-problems-with-pdbs.html)

Advanced analytics features are available in the Operations Insights Service:

- Exadata Database Service on Dedicated Infrastructure
  - [Operations Insights for Oracle Databases](https://docs.oracle.com/iaas/exadatacloud/exacs/ecs-operational-insights.html)

See also: [Oracle Cloud Observability and Management Platform](https://www.oracle.com/manageability/)

#### Configure Automatic Service Request Infrastructure

In addition to monitoring infrastructure with Enterprise Manager, Oracle can detect failures, dispatch field engineers, and replace failing hardware without customer involvement.

For example, Oracle Automatic Service Request (ASR) is a secure, scalable, customer-installable software solution available as a feature. The software resolves problems faster by using auto-case generation for Oracle's server and storage systems when specific hardware faults occur.

See also: [Oracle Automatic Service Request (Doc ID 1185493.1)](https://support.oracle.com/rs?type=doc&id=1185493.1)

### Exercise Capacity Planning

Periodically perform capacity planning exercises to ensure that your current hardware resources can accommodate existing workload and projected growth.

With database consolidation, this exercise should be done before migrating or adding a new database to the existing system.

Note that concurrent workloads can interfere with each other and can cause unpredictable behavior at times, so performance and HA testing may be required.

Using Database multitenant container databases, database resource management, or Exadata consolidation practices can help optimize existing system resources and constrain workload usage to meet expectations.

### Check the Latest MAA Best Practices

The MAA solution encompasses the full stack of Oracle technologies, so you can find MAA best practices for Oracle Database, Oracle Cloud, Oracle Exadata, Zero Data Loss Recovery Appliance, Oracle Fusion Middleware, Oracle Applications Unlimited, and Oracle Enterprise Manager on the MAA pages.

MAA solutions and best practices continue to be developed and published on <http://www.oracle.com/goto/maa>.
