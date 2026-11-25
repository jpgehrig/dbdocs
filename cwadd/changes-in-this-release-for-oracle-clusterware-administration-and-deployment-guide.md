This chapter lists new features in Oracle Clusterware for Oracle Database 19c and 18c.

### Changes in Oracle Clusterware Release 19c

Following is a list of features that are new in the Oracle Clusterware Administration and Deployment Guide for Oracle Clusterware 19c.

#### SRVCTL Changes for Oracle Clusterware 19c

Oracle Clusterware 19c includes changes to the server control utility (SRVCTL), including syntax changes to existing commands, and commands to manage Oracle Automatic Storage Management (Oracle ASM).

SRVCTL is one of the tools you use to manage Oracle Real Application Clusters (Oracle RAC) and Oracle Clusterware.

**See Also:**

[Server Control (SRVCTL) Command Reference](server-control-command-reference.md)

#### Rapid Home Provisioning Name Change

In this release, the feature previously known as Rapid Home Provisioning is renamed to Fleet Patching and Provisioning. There are no changes to the functionality, and the RHPCTL utility remains the tool you use to manage Fleet Patching and Provisioning operations.

#### Automated PDB Patching and Relocation

You can patch individual pluggable databases in a consolidated Oracle Multitenant environment, thus enabling bug fixes to be patched only on specific pluggable databases, rather than across the entire container database. Fine-grained single-instance pluggable database patching reduces possible risks incurred in widespread adoption of changes (such as bug fixes) and reduces the impact of making those changes only where they are necessary.

#### Zero-Downtime Oracle Grid Infrastructure Patching Using Fleet Patching and Provisioning

Zero-downtime Oracle Grid Infrastructure patching enables the application of one-off Oracle Grid Infrastructure patches without affecting the Oracle Real Application Clusters (Oracle RAC) database instances. Use Fleet Patching and Provisioning to apply patches, one at a time, to each node in the cluster. This functionality is available for all Oracle RAC clusters with two or more nodes but, currently, applies only to one-off patches (not release updates or release update revisions).

Using Fleet Patching and Provisioning to apply one-off Oracle Grid Infrastructure patches with zero database instance downtime reduces the impact on users and interruptions of service from the Oracle RAC database instances to nil. With prior database releases, you must shut down the database instance before applying an Oracle Grid Infrastructure patch, clearly impacting enterprise operations.

#### Automated Transaction Draining for Oracle Grid Infrastructure Upgrades

Automated transaction draining for Oracle Grid Infrastructure upgrades provides automatic draining of transactions against the database instances, one node at a time, according to the database service configurations. Transaction draining capabilities are an integral part of the database service design and are now automatically integrated into the application of rolling Oracle Grid Infrastructure patches.

Automated and coordinated draining of database transactions during rolling patching, using Fleet Patching and Provisioning, reduces the impact of patching operations. Once user transactions are drained, patching operations for a particular node on a cluster can be completed, after which the instance and services are restarted, locally, and new connections are established. The connections, prior to the patching operation, roll on to the next node in the cluster.

#### Oracle Restart Patching and Upgrading

Use Fleet Patching and Provisioning to patch and upgrade Oracle Restart. In previous releases, Oracle Restart environments required patching and upgrade operations to be done by the user, often involving manual intervention. Fleet Patching and Provisioning automates these procedures.

Using Fleet Patching and Provisioning to patch and upgrade Oracle Restart automates and standardizes the processes that are implemented in Oracle RAC database installations. This also reduces operational demands and risks, especially for larger numbers of Oracle Restart deployments.

#### Support the Specification of TLS Ciphers Using CRSCTL

Enhancements to the CRSCTL utility add support for the specification of Transport Layer Security (TLS) ciphers.

**See Also:**

[Transport Layer Security Cipher Suite Management](introduction-to-oracle-clusterware.md)

#### Secure Cluster Communication

Secure Cluster Communication protects the cluster interconnect from common security threats when used together with Single Network Support. Secure Cluster Communication includes message digest mechanisms, protection against fuzzing, and uses Transport Layer Security (TLS) to provide privacy and data integrity between the cluster members.

The increased security for the cluster interconnect is invoked automatically as part of a new Oracle Grid Infrastructure 19c deployment or an upgrade to Oracle Grid Infrastructure 19c. Database administrators or cluster administrators do not need to make any configuration changes for this feature.

#### Resupport of Direct File Placement for OCR and Voting Disks

Starting with Oracle Grid Infrastructure 19c, the desupport for direct OCR and voting disk file placement on shared file systems is rescinded for Oracle Standalone Clusters. For Oracle Domain Services Clusters the requirement to place OCR and voting files in Oracle Automatic Storage Management (Oracle ASM) on top on files hosted on shared file systems and used as ASM disks remains.

In Oracle Grid Infrastructure 12c Release 2 (12.2), Oracle announced that it would no longer support the placement of the Oracle Grid Infrastructure Oracle Cluster Registry (OCR) and voting files directly on a shared file system. This desupport is now rescinded. Starting with Oracle Grid Infrastructure 19c (19.3), with Oracle Standalone Clusters, you can again place OCR and voting disk files directly on shared file systems.

**See Also:**

[Managing Oracle Cluster Registry and Voting Files](managing-oracle-cluster-registry-and-voting-files.md)

#### Optional Install for the Grid Infrastructure Management Repository

Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.

The data contained in the GIMR is the basis for preventative diagnostics based on applied Machine Learning and can help to increase the availability of Oracle Real Application Clusters (RAC) databases. Having an optional installation for the GIMR allows for more flexible storage space management and faster deployment, especially during the installation of test and development systems.

**See Also:**

[Overview of Grid Infrastructure Management Repository](introduction-to-oracle-clusterware.md)

#### Deprecated Features in Oracle Clusterware 19c

The following features are deprecated in Oracle Clusterware 19c, and may be desupported in a future release:

##### Deprecation of Addnode Script

The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.

The `addnode` script can be removed in a future release. Instead of using the `addnode` script (`addnode.sh` or `addnode.bat`), add nodes by using the installer wizard. The installer wizard provides many enhancements over the `addnode` script. Using the installer wizard simplifies management by consolidating all software lifecycle operations into a single tool.

##### Deprecation of clone.pl Script

The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

##### Deprecation of Vendor Clusterware Integration with Oracle Clusterware

The integration of vendor or third party clusterware with Oracle Clusterware is deprecated in Oracle Database 19c.

The integration of vendor clusterware with Oracle Clusterware is deprecated and can be desupported in a future release. Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. In the absence of an integration between different cluster solutions, the system is subject to the dueling cluster solutions issue, which describes the fact that independent cluster solutions can make individual decisions about which corrective actions need to be taken in case of certain failures. As such, it is recommended that only one solution should be active at any point in time. Oracle recommends that customers align their next software or hardware upgrade with the transition off vendor cluster solutions for this reason.

##### Deprecation of Black Box Virtual Machine Management Using Oracle Clusterware

Direct management of virtual machine (VM) resources using Oracle Clusterware is deprecated in Oracle Database 19c, and can be removed in a future release.

Oracle continues to support the use of Oracle Clusterware management of black-box Oracle Grid Infrastructure virtual machines (GIVMs) on physical hardware using Oracle Clusterware 19c, which provides high availability and ease of management of virtual machines.

#### Desupported Features in Oracle Clusterware 19c

These are the desupported features for Oracle Clusterware 19c:

##### Desupport of Leaf Nodes in Flex Cluster Architecture

Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.

In Oracle Grid Infrastructure 19c (19.1) and later releases, all nodes in an Oracle Flex Cluster function as hub nodes. The capabilities offered by Leaf nodes in the original implementation of the Oracle Flex Cluster architecture can as easily be served by hub nodes. Therefore, leaf nodes are no longer supported.

##### Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition

Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

Upgrading Oracle Database Standard Edition databases that use Oracle Real Application Clusters (Oracle RAC) functionality from earlier releases to Oracle Database 19c is not possible. To upgrade those databases to Oracle Database 19c, either remove the Oracle RAC functionality before starting the upgrade, or upgrade from Oracle Database Standard Edition to Oracle Database Enterprise Edition.

For more information about each step, including how to reconfigure your system after an upgrade, refer to [My Oracle Support](https://support.oracle.com) Note 2504078.1: "Desupport of Oracle Real Application Clusters (RAC) with Oracle Database Standard Edition 19c."
