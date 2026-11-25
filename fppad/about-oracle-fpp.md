## About Oracle Fleet Patching and Provisioning

Oracle Fleet Patching and Provisioning (Oracle FPP) is a service in Oracle Grid Infrastructure.

**Note:**

- Oracle does not support Oracle FPP on HP-UX and Windows operating systems.

- The Oracle FPP Server does not manage operating system images on generic servers.

- Oracle FPP enables you to manage and patch the whole Oracle software stack on Oracle Exadata, including Oracle Grid Infrastructure, Oracle Database, RoCE/IB switches, Cell Storage Servers, and compute nodes.

You can use Oracle Fleet Patching and Provisioning in any of the following modes:

- As a local server (Oracle Fleet Patching and Provisioning Local Mode), that is the default configuration when you install Oracle Grid Infrastructure. Oracle FPP Local Mode operation enables you to perform Oracle Grid Infrastructure and Oracle Database patching operations on the local cluster in a simplified environment without having to register or deploy gold images. Deploy either the Oracle Grid Infrastructure or the Oracle Database patched home and run the patch operation using either the `rhpctl move gihome` or `rhpctl move database` command, specifying the source and destination paths instead of working copy names.

- As a central server (Oracle Fleet Patching and Provisioning Server), that stores and manages standardized images, called gold images. You can deploy gold images to any number of nodes across a data center. You can use the deployed homes to create new clusters and databases, and patch, upgrade, and scale existing installations.

  The server manages software homes on the cluster hosting the Oracle Fleet Patching and Provisioning Server, itself, Oracle Fleet Patching and Provisioning Clients, and can also manage Oracle Grid Infrastructure and Oracle Database installations running 11g release 2 (11.2.0.4) and later releases. The server can also manage `rhpclient`-less targets, which do not have Oracle Clusterware installed. Refer to My Oracle Support note 551141.1 for more information about Oracle Grid Infrastructure and Oracle Database upgrade paths.

  An Oracle Fleet Patching and Provisioning Server can provision new installations and can manage existing installations without any changes to the existing installations (such as no agent, daemon, or configuration prerequisites). Oracle Fleet Patching and Provisioning Servers also include capabilities for automatically sharing gold images among peer Oracle Fleet Patching and Provisioning Servers to support enterprises with geographically distributed data centers.

**Note:**

Combined Oracle FPP patching for Oracle Grid Infrastructure and Oracle Database is not supported for standalone configurations.

### Oracle Fleet Patching and Provisioning Advantages

Deploying Oracle software using Oracle Fleet Patching and Provisioning has the following advantages:

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Minimizes downtime by deploying new homes as images (working copies of gold images) out-of-place rolling patching, without disrupting active databases or clusters.

- Simplifies local maintenance operations using Oracle FPP Local Mode with a consistent API across database versions and deployment models.

- Provides REST API interface for Oracle FPP operations to ensure flexibility when integrating with bespoke and third-party orchestration engines.

- Reduces maintenance risk with built-in validations and a dry run mode to test the operations.

- Enables you to resume or restart the commands in the event of an unforeseen issue, reducing the impact of maintenance operations.

- Schedules and submits operations at a scheduled time instead of running the command immediately. The job scheduler performs the job and stores the metadata for the job, along with the current job status.

- Minimizes and often eliminates the impact of patching and upgrades, with features that include:
  - Zero-downtime database upgrade with fully automated upgrade, completed entirely within the deployment without requiring any extra nodes or external storage.
  - Options to do rolling patching to ensure continuous availability of the services.
  - Adaptive management of database sessions and OJVM during rolling patching.
  - Options for management of consolidated deployments.

- The deployment and maintenance operations enable customizations to include environment-specific actions into the automated workflow.

**Related Topics**

- [My Oracle Support Note 551141.1](https://support.oracle.com/rs?type=doc&id=551141.1)

**Parent topic:** [Oracle Fleet Patching and Provisioning Overview](fleet-patching-provisioning.md)
