## About Deploying Oracle Databases Using Oracle Fleet Patching and Provisioning

Provision, patch, and upgrade software homes on any number of nodes from a single cluster with standard gold images using Oracle FPP.

**Note:**

Starting with Oracle Database 19c, Rapid Home Provisioning feature is known as Oracle Fleet Patching and Provisioning or Oracle FPP.

With Oracle Fleet Patching and Provisioning (Oracle FPP), you create, store, and manage templates of Oracle homes as images (called gold images) of Oracle Databases, Grid Infrastructure, middleware, and applications. These gold images are maintained on an Oracle Fleet Patching and Provisioning Server, which can provision and maintain working copies of the images on any number of nodes in an Information Technology estate.

### Oracle Fleet Patching and Provisioning

Deploying Oracle software using Oracle FPP has the following advantages:

- Enables you to create and manage Oracle Real Application Clusters (Oracle RAC), single instance, and Oracle Real Application Clusters One Node (Oracle RAC One Node) databases. You can deploy single-instance databases with or without Oracle Grid Infrastructure.

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Supports change management. With standardized Oracle homes, an administrator has better control of the hosted Oracle software and can easily manage the mass deployment, patching, and upgrade of the software through a single location for change management.

- Minimizes downtime during patching and upgrades, eases rollbacks, and makes provisioning for large systems easier and more efficient.

- Simplifies maintenance and patching of database software.

- Reduces the cumulative time to patch software images, since a single Oracle home may be used for many database instances.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md) for information about setting up the Oracle Fleet Patching and Provisioning Server and Client, creating and using gold images for provisioning and patching Oracle Database homes.

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node](installing-oracle-rac-and-oracle-rac-one-node.md)
