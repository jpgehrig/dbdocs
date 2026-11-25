Oracle Fleet Patching and Provisioning (Oracle FPP) is a software lifecycle management method for provisioning and patching Oracle homes.

Oracle Fleet Patching and Provisioning enables you to install clusters, and provision, patch, and upgrade Oracle Grid Infrastructure, Oracle Database, and Oracle Restart homes. The supported versions are 11.2, 12.1, 12.2, 18c, and 19c. You can also provision applications and middleware using Oracle FPP. A single cluster, known as the Oracle Fleet Patching and Provisioning Server, stores and manages standardized images, called gold images, which can be provisioned to any number of nodes. You can install Oracle Grid Infrastructure cluster configurations such as Oracle Standalone Clusters, Oracle Member Clusters, and Oracle Member Cluster for Applications. After deployment, you can expand and contract clusters and Oracle RAC Databases.

You can provision Oracle Grid Infrastructure on a remote set of nodes in a cloud computing environment from a single cluster where you store templates of Oracle homes as images (called gold images) of Oracle software, such as databases, middleware, and applications.

### Oracle Fleet Patching and Provisioning

Deploying Oracle software using Oracle FPP has the following advantages:

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Supports change management. With standardized Oracle homes, an administrator has better control of the hosted Oracle software and can easily manage the mass deployment and maintenance of the software through a single location for change management.

- Minimizes downtime during patching and upgrades, eases rollbacks, and makes provisioning for large systems easier and more efficient.

- Reduces the cumulative time to patch software images, since a single Oracle home may be used for many database instances.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md) for information about setting up the Oracle Fleet Patching and Provisioning Server and Client, creating and using gold images for provisioning and patching Oracle Grid Infrastructure, Oracle Database, and Oracle Restart homes.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
