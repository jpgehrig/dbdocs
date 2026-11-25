Review these requirements before you install and deploy the Standard Edition High Availability feature.

- You must configure Standard Edition High Availability using at least two nodes of a cluster running Oracle Grid Infrastructure 19.13 or later for Standalone Cluster.
- You must configure Standard Edition High Availability using Oracle Database home of version 19.13 or later.
  **Note:**

  When updating your Oracle Database home using Release Update (RU) 19.13 or later, ensure that you apply the Oracle Clusterware (OCW) RU of the same version to the Oracle Database home.
- Ensure that all cluster nodes on which you plan to install Oracle Database have the same operating system users, groups, and resource limits for the database software owner.
- You must store the Oracle Database binaries only on local storage.
- You must store the Oracle Database data files only on Oracle ASM.
- You must have the same single-instance Standard Edition 2 installation and updates on each node. You must also use the same Oracle base and Oracle home directory structure on each node.
- You must perform the same Oracle home operations on all the nodes.
- You must use an SPFILE for the database instance initialization parameters and a database password file stored for the database instance initialization parameters in Oracle ASM. This approach ensures that the parameters are consistent across all nodes and the password file is available after a failover or a relocation.
- You must register the Standard Edition 2 single-instance database with SCAN listeners as remote listener and node listeners as local listener.

**Parent topic:** [Installing Standard Edition High Availability](configuring-standard-edition-high-availability.md)
