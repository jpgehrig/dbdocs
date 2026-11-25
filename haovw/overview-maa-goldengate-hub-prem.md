## Overview of MAA GoldenGate Hub

To achieve the highest levels of availability, resulting in zero or near-zero downtime for both unplanned outages and planned maintenance activities, customers frequently use the combination of Oracle Real Application Clusters (Oracle RAC), Oracle Active Data Guard, and Oracle GoldenGate.

This architecture, typically referred as Platinum MAA or Never Down Architecture, delivers near zero Recovery Time Objective (RTO, or downtime incurred during outage) and potentially zero or near zero Recovery Point Objective (RPO, or data loss potential).

Traditionally, Oracle GoldenGate is installed and run locally on the database server that the GoldenGate processes connect to. When used with Oracle Grid Infrastructure Standalone Agent (XAG), Oracle GoldenGate processes can be configured to seamlessly relocate or failover between Oracle RAC nodes and follow Oracle Active Data Guard switchover and failovers.

Using MAA Oracle GoldenGate Hub (MAA GGHub) moves the GoldenGate software and processes off of the Exadata database servers, reducing complexity and system resource utilization. MAA GGHub centralizes Oracle GoldenGate management and offloads the majority of the Oracle GoldenGate processing and associated CPU and storage resource utilization from Exadata system resources. Connectivity between the GoldenGate processes and the databases they operate against is managed with Oracle Net Services.

To achieve an MAA Platinum solution on-premises, you follow these high level steps:

1.  Review [Oracle MAA Platinum Tier for Oracle Exadata](https://www.oracle.com/a/tech/docs/exadata-maa-platinum-focused.pdf) to understand Platinum MAA benefits and use cases.

2.  Deploy or migrate your database onto Exadata Database Machine

3.  Add symmetric standby databases.

4.  Configure and deploy Oracle Data Guard Fast Start Failover using the Oracle MAA best practice recommendations in [Configure Fast Start Failover](configure-and-deploy-oracle-data-guard.md).

5.  Set up MAA GGHub, which is detailed in the topics that follow.

6.  Configure Bidirectional Replication and Automatic Conflict Detection and Resolution. See [Bi-Directional Replication](https://docs.oracle.com/en/middleware/goldengate/core/21.3/coredoc/administer-configuring-bi-directional-replication.html?source=%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723%2C%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723&source=%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723%2C%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723&source=%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723%2C%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723&source=%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723%2C%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723&source=%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723%2C%3Aow%3Alp%3Acpo%3A%3Arc_bumk180724p00001%3Alpd100743723#GUID-BF69D963-8336-4209-A3A1-FCD94B27ACF6) and [Automatic Conflict Detection and Resolution](https://docs.oracle.com/en/middleware/goldengate/core/21.3/oracle-db/automatic-conflict-detection-and-resolution1.html).

7.  Decide on application failover options such as Global Data Services (see [Oracle Global Data Services Best Practices](oracle-global-data-services-best-practices.md)), or use your own customized application failover.

Refer to the [Reference for Oracle GoldenGate](https://docs.oracle.com/en/middleware/goldengate/core/21.3/reference/tranlogoptions.html#GUID-B6ADFEC9-10E6-456D-9477-088513E113AF) for more information about the Extract `TRANLOGOPTIONS` parameters.

When creating an Extract using the Oracle GoldenGate Administration Service GUI, leave the `Trail SubDirectory` parameter blank so that the trail files are automatically created in the deployment directories stored on the shared file system. The default location for trail files is the /\<deployment directory\>/var/lib/data directory.

**Note:**

To capture from a multitenant database, you must use an Extract configured at the root level using a c## account. To apply data into a multitenant database, a separate Replicat is needed for each PDB because a Replicat connects at the PDB level and doesn't have access to objects outside of that PDB.
