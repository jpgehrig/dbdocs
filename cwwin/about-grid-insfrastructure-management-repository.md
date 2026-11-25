## About the Grid Infrastructure Management Repository

The Grid Infrastructure Management Repository (GIMR) is a multitenant database with a pluggable database (PDB) for the GIMR of each cluster.

Every Oracle Domain Services Cluster contains a Grid Infrastructure Management Repository (GIMR). However, GIMR configuration is optional for Oracle Standalone Cluster. The GIMR stores the following information about the cluster:

- Real time performance data that Cluster Health Monitor collects

- Fault, diagnosis, and metric data that Cluster Health Advisor collects

- Cluster-wide events about all resources that Oracle Clusterware collects

- Workload performance and CPU architecture data that Quality of Service Management (QoSM) collects

The global GIMR runs in an Oracle Domain Services Cluster. Oracle Domain Services Cluster locally hosts the GIMR in a separate Oracle ASM disk group. Oracle Member Cluster for Database uses the remote GIMR located on the Oracle Domain Services Cluster. Hosting the GIMR on a remote cluster reduces the overhead of running an extra infrastructure repository on a cluster. The GIMR for an Oracle Domain Services Cluster is a multitenant database with one PDB, and additional PDB for each member cluster that is added.

When you configure an Oracle Domain Services Cluster, the installer prompts to configure a separate Oracle ASM disk group for the GIMR, with the default name as `MGMT`.

- [Guidelines for the Grid Infrastructure Management Repository](guidelines-for-configuring-grid-insfrastructure-management-repository.md)
  Consider these guidelines while configuring the Grid Infrastructure Management Repository (GIMR) for your deployment.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-asm.md)
