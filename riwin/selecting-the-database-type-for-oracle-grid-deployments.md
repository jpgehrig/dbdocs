## Selecting the Database Type for Oracle Grid Infrastructure Deployments

During installation, Oracle Universal Installer (OUI) detects if you have Oracle Grid Infrastructure for a cluster installed. If you do, then you must specify the type of database you plan to create.

- Determine which type of database you plan to create after installing the software:
  - A single-instance database

  - An Oracle RAC database

  - An Oracle RAC One Node database

  If you plan to create databases of different types on this cluster, then choose the most advanced option.

  For example, if you plan to create only single-instance and Oracle RAC One Node databases, then choose the Oracle RAC One Node database option. If you plan to create single-instance databases and Oracle RAC databases, then choose the Oracle RAC database option.
- If you plan to install Oracle RAC One Node, then you can install the Oracle RAC software on two or more nodes in the cluster.
  An Oracle RAC One Node installation starts an instance on one of the nodes you select as an Oracle RAC One Node pool member. If that instance goes down, then the Oracle RAC One Node instance fails over to another pool member. This feature relocates database instances and connections to other cluster nodes for high availability.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/converting-single-instance-oracle-databases-to-oracle-rac-and-oracle-rac-one-node.md) for information about how to convert single-instance databases to Oracle RAC

**Parent topic:** [Selecting Installation Options for Oracle RAC](selecting-installation-options-for-oracle-rac.md)
