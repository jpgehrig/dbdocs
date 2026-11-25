## About the Grid Infrastructure Management Repository

Every Oracle Domain Services Cluster contains a Grid Infrastructure Management Repository (GIMR), but GIMR configuration is optional for Oracle Standalone Cluster.

The Grid Infrastructure Management Repository (GIMR), or the Management Database (MGMTDB) is a multitenant database with a pluggable database (PDB) for the GIMR of each cluster. The GIMR stores the following information about the cluster:

- Real time performance data that Cluster Health Monitor collects

- Fault, diagnosis, and metric data that Cluster Health Advisor collects

- Cluster-wide events about all resources that Oracle Clusterware collects

- Workload performance and CPU architecture data that Quality of Service Management (QoS) collects

- Metadata required for Oracle Fleet Patching and Provisioning

Starting with Oracle Grid Infrastructure 19c, configuring GIMR is optional for Oracle Standalone Cluster deployments. The Oracle Standalone Cluster locally hosts the GIMR on an Oracle ASM disk group or a shared file system; this GIMR is a multitenant database with a single pluggable database (PDB).

The global GIMR runs in an Oracle Domain Services Cluster. Oracle Domain Services Cluster locally hosts the GIMR in a separate Oracle ASM disk group. Oracle Member Cluster for Database uses the remote GIMR located on the Oracle Domain Services Cluster. Hosting the GIMR on a remote cluster reduces the overhead of running an extra infrastructure repository on a cluster. The GIMR for an Oracle Domain Services Cluster is a multitenant database with one PDB, and additional PDB for each member cluster that is added.

When you configure an Oracle Domain Services Cluster, the installer prompts to configure a separate Oracle ASM disk group for the GIMR, with the default name as `MGMT`.

**Related Topics**

- [About Oracle Standalone Clusters](about-oracle-standalone-clusters.md)
- [About Oracle Cluster Domain and Oracle Domain Services Cluster](about-oracle-domain-services-clusters.md)
- [About Oracle Member Clusters](about-oracle-member-clusters.md)

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
