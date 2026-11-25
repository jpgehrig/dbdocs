## Oracle Fleet Patching and Provisioning Features

Oracle Fleet Patching and Provisioning (FPP) provides various features to ease configuration and management tasks.

When you manage Oracle software using Oracle Fleet Patching and Provisioning, Oracle FPP:

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Minimizes the maintenance window by deploying new homes (working copies of gold images) out-of-place, without disrupting active databases or clusters.

- Simplifies local maintenance operations using Oracle FPP Local Mode with a consistent API across database versions and deployment models.

- Reduces maintenance risk with built-in validations and a dry-run mode to ensure operations will succeed end-to-end.

- In the event of an issue, commands are resumable and restartable, further reducing the impact of maintenance operations.

- Minimizes and, in many cases, eliminates the impact of patching and upgrades, with features that include:

  - Zero-downtime database upgrade: A fully-automated upgrade executed entirely within the deployment with no extra nodes or external storage required.

  - Adaptive management of database sessions and OJVM during rolling patching.

  - Options for fine-grained management of consolidated deployments.

The deployment and maintenance operations are extensible, allowing customizations to include environment-specific actions into the automated workflow.

### Oracle Fleet Patching and Provisioning Local Mode

- Zero-downtime database upgrade automates all of the steps involved in a database upgrade to minimize or even eliminate application downtime while upgrading an Oracle database. It also minimizes resource requirements and provides a fallback path in case the upgrade must be rolled back.

- Adaptive Oracle RAC Rolling Patching for OJVM Deployments: In a clustered environment, the default approach for Oracle Fleet Patching and Provisioning for patching a database is Oracle RAC rolling patching. However non-rolling may be required if the patched database home contains OJVM patches. In this case, Oracle Fleet Patching and Provisioning determines whether rolling patching is possible and does so, if applicable.

- Dry-run command evaluation: Before running any command, Oracle Fleet Patching and Provisioning checks various preconditions to ensure the command will succeed. However, some conditions cannot be detected prior to a command running. And, while Oracle Fleet Patching and Provisioning allows a failed command to be reverted or resumed after an error condition is corrected, it is preferable to address as many potential issues as possible before the command is run. The command evaluation mode will test the preconditions for a given command, without making any changes, and report potential problems and correct them before the command is actually run.

- Oracle FPP Local Mode: Prior to Oracle Database 18c, performing any Oracle Fleet Patching and Provisioning operation (for example, switching a database home to a later version) required the presence of a central Oracle Fleet Patching and Provisioning Server. Beginning with Oracle Database 18c, key functionality can be performed independently, with no central Oracle Fleet Patching and Provisioning Server in the architecture.

### Global Fleet Standardization and Management

- Sharing gold images between peer Oracle Fleet Patching and Provisioning Servers: Large enterprises typically host multiple data centers and, within each data center, there may be separate network segments. In the Oracle Fleet Patching and Provisioning architecture, one Oracle Fleet Patching and Provisioning Server operates on a set of targets within a given data center (or network segment of a data center). Therefore each data center requires at least one Oracle Fleet Patching and Provisioning Server.

  While each data center may have some unique requirements in terms of the gold images that target servers will use, the goal of standardization is using the same gold image across all data centers whenever possible. To that end, Oracle Fleet Patching and Provisioning supports peer-to-peer sharing of gold images to easily propagate gold images among multiple Oracle Fleet Patching and Provisioning Servers.

- Gold image drift detection and aggregation: After you provision a software home from a gold image, you may have to apply a patch directly to the deployed home. At this point the deployed home has drifted from the gold image. Oracle Fleet Patching and Provisioning provides two capabilities for monitoring and reporting drift:
  - Oracle Fleet Patching and Provisioning compares a specific home to its parent gold image and lists any patches that are applied to the home but that are not in the gold image.

  - Oracle Fleet Patching and Provisioning compares a specific gold image to all of its descendant homes and lists the aggregation of all patches applied to those homes that are not in the gold image. This provides a build specification for a new gold image that could be applied to all of the descendants of the original gold image, such that no patches will be lost from any of those deployments.

  **See Also:**

  - [rhpctl query image](image-commands.md) for information about the `-drift` option for this command

  - [rhpctl query workingcopy](workingcopy-commands.md) for information about the `-drift` option for this command

- Configuration collection and reporting: The Oracle Fleet Patching and Provisioning Server can collect and retain operating system configuration and the root file system contents of specified Oracle Fleet Patching and Provisioning Clients. If an Oracle Fleet Patching and Provisioning Client node is rendered unusable (for example, a user accidentally deletes or changes operating system configuration or the root file system), then it can be difficult to determine the problem and correct it. This feature automates the collection of relevant information, enabling simple restoration in the event of node failure.

### Flexibility and Extensibility

- RESTful API: Oracle Fleet Patching and Provisioning provides a RESTful API for many common operations, including provisioning, patching, upgrading, and query operations.
  **See Also:**

  [Oracle Database REST API Reference](../dbrst/index.md)

- Customizable authentication: Host-to-host authentication in certain environments, particularly in compliance-conscious industries, such as financials and e-commerce, often uses technologies and products that are not supported, natively, by Oracle Fleet Patching and Provisioning. This feature allows integrating Oracle Fleet Patching and Provisioning authentication with the mechanisms in use at your data center.

- Command scheduler: The ability to schedule and bundle automated tasks is essential for maintenance of a large database estate. Oracle Fleet Patching and Provisioning supports scheduling tasks such as provisioning software homes, switching to a new home, and scaling a cluster. Also, you can add a list of clients to a command, facilitating large-scale operations.

- Configurable connectivity: As security concerns and compliance requirements increase, so do the restrictions on connectivity across the intranets of many enterprises. You can configure the small set ports used for communication between the Oracle Fleet Patching and Provisioning Server and its Clients, allowing low-impact integration into firewalled or audit-conscious environments.

### Other Oracle Fleet Patching and Provisioning Features

- Zero-downtime upgrade: Automation of all of upgrade steps involved minimizes or even eliminates application downtime while upgrading an Oracle Database. It also minimizes resource requirements and provides a fallback path in case you must roll back the upgrade. You can run a zero-downtime upgrade on certain versions of Oracle RAC and Oracle RAC One Node databases.

- Provision new server pools: The Oracle Fleet Patching and Provisioning Server can install and configure Oracle Grid Infrastructure on nodes that have no Oracle software inventory and can then manage those deployments with the full complement of Oracle Fleet Patching and Provisioning functionality.

- Provision and manage any software home: Oracle Fleet Patching and Provisioning enables you to create a gold image from any software home. You can then provision that software to any Oracle Fleet Patching and Provisioning Client or target as a working copy of a gold image. The software may be any binary that you will run on an Oracle Fleet Patching and Provisioning Client or target.

- Provision, scale, patch, and upgrade Oracle Grid Infrastructure: The Oracle Fleet Patching and Provisioning Server can provision Oracle Grid Infrastructure 11g release 2 (11.2.0.4) homes, and later, add or delete nodes from an Oracle Grid Infrastructure configuration, and can also be used to patch and upgrade Oracle Grid Infrastructure homes. In addition, there is a rollback capability that facilitates undoing a failed patch procedure. While patching Oracle Grid Infrastructure, you can use Oracle Fleet Patching and Provisioning to optionally patch any database homes hosted on the cluster.

- Provision, scale, patch, and upgrade Oracle Database: You can use Oracle Fleet Patching and Provisioning, you can provision, scale, and patch Oracle Database 11g release 2 (11.2.0.4), and later releases. You can also upgrade Oracle Databases from 11g release 2 (11.2.0.4), 12c release 1 (12.1.0.2), 12c release 2 (12.2), and 18c to Oracle Database 19c.

  When you provision such software, Oracle Fleet Patching and Provisioning offers additional features for creating various types of databases (such as Oracle RAC, single instance, and Oracle Real Application Clusters One Node (Oracle RAC One Node) databases) on different types of storage, and other options, such as using templates and creating container databases (CDBs). The Oracle Fleet Patching and Provisioning Server can add nodes to an Oracle RAC configuration, and remove nodes from an Oracle RAC configuration. Oracle Fleet Patching and Provisioning also improves and makes more efficient patching of database software, allowing for rapid and remote patching of the software, in most cases, without any downtime for the database.

- Support for single-instance databases: You can use Oracle Fleet Patching and Provisioning to provision, patch, and upgrade single-instance databases running on clusters or Oracle Restart, or on single, standalone nodes.

- Advanced patching capabilities: When patching an Oracle Grid Infrastructure or Oracle Database home, Oracle Fleet Patching and Provisioning offers a batch mode that speeds the patching process by patching some or all nodes of a cluster in parallel and/or a specific node order, rather than sequentially.

  For Oracle Database homes, you can define disjoint sets of nodes. Each set of nodes is updated sequentially. By defining sets with reference to the database instances running on them, you can minimize the impact of rolling updates by ensuring that services are never taken completely offline. A “smartmove” option is available to help define the sets of batches to meet this goal.

  Integration with Application Continuity is another enhancement to help eliminate the impact of maintenance. This provides the ability to gracefully drain and relocate services within a cluster, completely masking the maintenance from users.

- Notifications:The Oracle Fleet Patching and Provisioning Server is the central repository for the software homes available to the data center. Therefore, it is essential that administrators throughout the data center be aware of changes to the inventory which might impact their areas of responsibility.

  Oracle Fleet Patching and Provisioning enables you and other users to subscribe to image series events. Anyone subscribed will be notified by email of any changes to the images available in a particular image series. Also, users can be notified by email when a working copy of a gold image is added to or deleted from a client.

- Custom workflow support: You can create actions for various Oracle Fleet Patching and Provisioning operations, such as importing images, adding or deleting working copies of the gold images, and managing a software home. You can define different actions for each operation, and further differentiate by the type of image to which the operation applies. Actions that you define can be executed before or after the given operation, and are executed on the deployment the operation applies to, whether it is the Oracle Fleet Patching and Provisioning Server, a target that is not running an Oracle Fleet Patching and Provisioning Client, or a target that is running an Oracle Fleet Patching and Provisioning Client.

- Resume failed operations: If an operation, such as adding an image, provisioning a working copy of a gold image, or performing a scale, patch or upgrade fails, then Oracle Fleet Patching and Provisioning reports the error and stops. After the problem is corrected (for example, a directory permissions or ownership misconfiguration on a target node), you can rerun the RHPCTL command that failed, and it will resume from the point of failure. This avoids redoing any work that may have been completed prior to the failure.

- Audit command: The Oracle Fleet Patching and Provisioning Server records the execution of all Oracle Fleet Patching and Provisioning operations and also records their outcome (whether success or failure). An audit mechanism enables you to query the audit log in a variety of dimensions, and also to manage its contents and size.

**Parent topic:** [Oracle Fleet Patching and Provisioning Overview](fleet-patching-provisioning.md)
