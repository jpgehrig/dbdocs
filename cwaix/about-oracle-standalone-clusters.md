An Oracle Standalone Cluster hosts all Oracle Grid Infrastructure services and Oracle ASM locally and requires direct access to shared storage.

Oracle Standalone Clusters contain multiple cluster nodes. The number of nodes in an Oracle Standalone Cluster can be as many as 64. The cluster nodes can host different types of applications. Oracle Standalone Cluster nodes are tightly connected, and have direct access to shared storage. Shared storage is locally mounted on each of the Oracle Standalone Cluster nodes, with an Oracle ASM instance or a shared file system location available to all the nodes.

Oracle Standalone Clusters host Grid Infrastructure Management Repository (GIMR) locally, if GIMR was configured during the installation. The GIMR is a multitenant database, which stores information about the cluster. This information includes the real time performance data the Cluster Health Monitor collects, and includes metadata required for Oracle Fleet Patching and Provisioning.

When you deploy an Oracle Standalone Cluster, you can also choose to configure it as an Oracle Extended cluster. An Oracle Extended Cluster consists of nodes that are located in multiple locations or sites.

**Parent topic:** [Understanding Cluster Configuration Options](understanding-cluster-configuration-options.md)
