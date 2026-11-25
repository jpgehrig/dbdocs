Oracle Fleet Patching and Provisioning (Oracle FPP) is a software lifecycle management method for provisioning and maintaining Oracle homes. Oracle Fleet Patching and Provisioning enables mass deployment and maintenance of standard operating environments for databases, clusters, and user-defined software types.

**Note:**

Starting with Oracle Grid Infrastructure 19c, the feature formerly known as Rapid Home Provisioning (RHP) is now Oracle Fleet Patching and Provisioning (Oracle FPP).

Oracle Fleet Patching and Provisioning enables you to install clusters, and provision, patch, scale, and upgrade Oracle Grid Infrastructure, Oracle Restart, and Oracle Database homes. The supported versions are 11.2, 12.1, 12.2, 18c, and 19c. You can also provision applications and middleware using Oracle Fleet Patching and Provisioning.

Oracle Fleet Patching and Provisioning is a service in Oracle Grid Infrastructure that you can use in either of the following modes:

- Central Oracle Fleet Patching and Provisioning Server

  The Oracle Fleet Patching and Provisioning Server stores and manages standardized images, called gold images. Gold images can be deployed to any number of nodes across the data center. You can create new clusters and databases on the deployed homes and can use them to patch, upgrade, and scale existing installations.

  The Oracle Fleet Patching and Provisioning Server can manage the following types of installations:
  - Software homes on the cluster hosting the Oracle Fleet Patching and Provisioning Server itself.

  - Oracle Fleet Patching and Provisioning Clients running Oracle Grid Infrastructure 12c Release 2 (12.2), 18c, and 19c.

  - Installations running Oracle Grid Infrastructure 11g Release 2 (11.2) and 12c Release 1 (12.1).

  - Installations running without Oracle Grid Infrastructure.

  The Oracle Fleet Patching and Provisioning Server can provision new installations and can manage existing installations without requiring any changes to the existing installations. The Oracle Fleet Patching and Provisioning Server can automatically share gold images among peer servers to support enterprises with geographically distributed data centers.

- Oracle Fleet Patching and Provisioning Client

  The Oracle Fleet Patching and Provisioning Client can be managed from the Oracle Fleet Patching and Provisioning Server, or directly by executing commands on the client itself. The Oracle Fleet Patching and Provisioning Client is a service built into the Oracle Grid Infrastructure and is available in Oracle Grid Infrastructure 12c Release 2 (12.2) and later releases. The Oracle Fleet Patching and Provisioning Client can retrieve gold images from the Oracle Fleet Patching and Provisioning Server, upload new images based on the policy, and apply maintenance operations to itself.

### Oracle Fleet Patching and Provisioning

Deploying Oracle software using Oracle Fleet Patching and Provisioning has the following advantages:

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Minimizes downtime by deploying new homes as images (called gold images) out-of-place, without disrupting active databases or clusters.

- Simplifies maintenance by providing automatons which are invoked with a simple, consistent API across database versions and deployment models.

- Reduces maintenance risk with built-in validations and a “dry run” mode to test the operations.

- Enables you to resume or restart the commands in the event of an unforeseen issue, reducing the risk of maintenance operations.

- Minimizes and often eliminates the impact of patching and upgrades, with features that include:

  - Zero-downtime database upgrade with fully automated upgrade, executed entirely within the deployment without requiring any extra nodes or external storage.

  - Adaptive management of database sessions and OJVM during rolling patching.

  - Options for management of consolidated deployments.

- The deployment and maintenance operations enable customizations to include environment-specific actions into the automated workflow.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md)

**Parent topic:** [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md)
