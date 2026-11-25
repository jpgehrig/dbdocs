## Changes in this Release for Oracle Grid Infrastructure

The following are changes in Oracle Grid Infrastructure Installation Guide for Oracle Grid Infrastructure 19c.

- New Features
  Review new features available with Oracle Grid Infrastructure 19c.
- Deprecated Features
  Review features that are deprecated starting with Oracle Grid Infrastructure 19c.
- Desupported Features
  Review features that are desupported with Grid Infrastructure 19c.
- Other Changes
  Review other changes for Oracle Grid Infrastructure 19c.

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

### New Features

Review new features available with Oracle Grid Infrastructure 19c.

- Support for Dry-Run Validation of Oracle Clusterware Upgrade
- Multiple ASMB
- Parity Protected Files
- Secure Cluster Communication
- Zero-Downtime Oracle Grid Infrastructure Patching
- Zero-Downtime Oracle Grid Infrastructure Patching Using Oracle Fleet Patching and Provisioning
- Resupport of Direct File Placement for OCR and Voting Disks
- Optional Install for the Grid Infrastructure Management Repository

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

**Parent topic:** Changes in this Release for Oracle Grid Infrastructure

#### Support for Dry-Run Validation of Oracle Clusterware Upgrade

Starting with Oracle Grid Infrastructure 19c, the Oracle Grid Infrastructure installation wizard (`gridSetup.sh`) enables you to perform a dry-run mode upgrade to check your system’s upgrade readiness.

In dry-run upgrade mode, the installation wizard performs all of the system readiness checks that it would perform in an actual upgrade and enables you to verify whether your system is ready for upgrade before you start the upgrade. This mode does not perform an actual upgrade. It helps anticipate potential problems with the system setup and avoid upgrade failures.

**Related Topics**

- [Using Dry-Run Upgrade Mode to Check System Upgrade Readiness](using-dry-run-upgrade-mode-to-validate-readiness-for-oracle-grid-infrastructure.md)

**Parent topic:** New Features

#### Multiple ASMB

Given that +ASM1 has dg1 mounted but not dg2, and +ASM2 has dg2 mounted but not dg1, the Multiple ASMB project allows for the Database to use both dg1 and dg2 by connecting to both ASM instances simultaneously. Instead of having just ASMB, we can now have ASMBn.

This feature increases the availability of the Real Application Clusters (RAC) stack by allowing DB to use multiple disk groups even if a given ASM instance happens not to have all of them mounted.

**Parent topic:** New Features

#### Parity Protected Files

You cannot use parity protection for write-once files in Oracle Database Automatic Storage Management (Oracle ASM). Write-once files are files such archive logs and backup sets.

A great deal of space is consumed when two or three way Oracle ASM mirroring is used for files associated with database backup operations. Backup files are write-once files, and this feature allows parity protection for protection rather than conventional mirroring. Considerable space savings are the result.

**Related Topics**

- [About Oracle ASM File Group Properties](../ostmg/asm-filegroups.md)

**Parent topic:** New Features

#### Secure Cluster Communication

Secure Cluster Communication protects the cluster interconnect from common security threats when used together with Single Network Support. Secure Cluster Communication includes message digest mechanisms, protection against fuzzing, and uses Transport Layer Security (TLS) to provide privacy and data integrity between the cluster members.

The increased security for the cluster interconnect is invoked automatically as part of a new Oracle Grid Infrastructure 19c deployment or an upgrade to Oracle Grid Infrastructure 19c. Database administrators or cluster administrators do not need to make any configuration changes for this feature.

**Parent topic:** New Features

#### Zero-Downtime Oracle Grid Infrastructure Patching

Zero-Downtime Oracle Grid Infrastructure Patching enables patching of Oracle Grid Infrastructure without interrupting database operations. Patches are applied out-of-place and in a rolling fashion, with one node being patched at a time, while the database instances on the node remain operational. Zero-Downtime Oracle Grid Infrastructure Patching supports Oracle Real Application Clusters (Oracle RAC) databases on clusters with two or more nodes.

Zero-Downtime Grid Infrastructure Patching significantly increases database availability by allowing customers to perform a rolling patch of Oracle Grid Infrastructure without interrupting database operations on the node being patched and without impacting capacity or performance on those database instances.

**Related Topics**

- [Zero-Downtime Oracle Grid Infrastructure Patching](../fppad/zero-downtime-grid-patching.md)

**Parent topic:** New Features

#### Zero-Downtime Oracle Grid Infrastructure Patching Using Oracle Fleet Patching and Provisioning

Zero-Downtime Oracle Grid Infrastructure Patching enables the application of one-off Oracle Grid Infrastructure patches without impacting the Oracle RAC database instances. Use Oracle Fleet Patching and Provisioning (Oracle FPP) to apply patches in a rolling fashion across the cluster. This functionality is available for all Oracle Real Application Clusters with two or more nodes, but currently applies only to one-off patches (not the RU's and RUR's).

Using Oracle Fleet Patching and Provisioning to apply one-off Oracle Grid Infrastructure patches with zero database instance downtime reduces the impact on users and interruptions of service from the Oracle RAC database instances to nil. With prior database releases, you must shut down the database instance before applying an Oracle Grid Infrastructure patch, clearly impacting enterprise operations.

**Related Topics**

- [Zero-Downtime Oracle Grid Infrastructure Patching](../fppad/zero-downtime-grid-patching.md)

**Parent topic:** New Features

#### Resupport of Direct File Placement for OCR and Voting Disks

Starting with Oracle Grid Infrastructure 19c, the desupport for direct OCR and voting disk file placement on shared file systems is rescinded for Oracle Standalone Clusters. For Oracle Domain Services Clusters the requirement to place OCR and voting files in Oracle Automatic Storage Management (Oracle ASM) on top of files hosted on shared file systems and used as ASM disks remains.

In Oracle Grid Infrastructure 12c Release 2 (12.2), Oracle announced that it would no longer support the placement of the Oracle Grid Infrastructure Oracle Cluster Registry (OCR) and voting files directly on a shared file system. This desupport is now rescinded. Starting with Oracle Grid Infrastructure 19c (19.3), with Oracle Standalone Clusters, you can again place OCR and voting disk files directly on shared file systems.

**Related Topics**

- [Using a Cluster File System for Oracle Clusterware Files](using-a-cluster-file-system-for-oracle-clusterware-files.md)

**Parent topic:** New Features

#### Optional Install for the Grid Infrastructure Management Repository

Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.

The data contained in the GIMR is the basis for preventative diagnostics based on applied Machine Learning and can help to increase the availability of Oracle Real Application Clusters (Oracle RAC) databases. Having an optional installation for the GIMR allows for more flexible storage space management and faster deployment, especially during the installation of test and development systems.

**Related Topics**

- [About the Grid Infrastructure Management Repository](about-gimr.md)

**Parent topic:** New Features

### Deprecated Features

Review features that are deprecated starting with Oracle Grid Infrastructure 19c.

For more information about deprecated features, parameters, and views, refer to Oracle Database Upgrade Guide

- Deprecation of Addnode Script

  The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.

  The `addnode` script can be removed in a future release. Instead of using the `addnode` script (`addnode.sh` or `addnode.bat`), add nodes by using the installer wizard. The installer wizard provides many enhancements over the `addnode` script. Using the installer wizard simplifies management by consolidating all software lifecycle operations into a single tool.

- Deprecation of clone.pl Script

  The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.

  The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

- Deprecation of Cluster Domain - Member Clusters

  Starting with Oracle Grid Infrastructure 19c (19.5), Member Clusters, which are part of the Oracle Cluster Domain architecture, are deprecated.

  Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. The deprecation of Member Clusters affects the clustering used with the DSC, but not its ability to host services for other production clusters. Oracle recommends that you align your next software or hardware upgrade with the transition off Cluster Domain - Member Clusters.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in this Release for Oracle Grid Infrastructure

### Desupported Features

Review features that are desupported with Grid Infrastructure 19c.

For more information about desupported features, parameters, and views, refer to Oracle Database Upgrade Guide

- Desupport of Leaf Nodes in Flex Cluster Architecture

  Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.

  In Oracle Grid Infrastructure 19c (19.1) and later releases, all nodes in an Oracle Flex Cluster function as hub nodes. The capabilities offered by Leaf nodes in the original implementation of the Oracle Flex Cluster architecture can as easily be served by hub nodes. Therefore, leaf nodes are no longer supported.

- Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition

  Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

  Upgrading Oracle Database Standard Edition databases that use Oracle Real Application Clusters (Oracle RAC) functionality from earlier releases to Oracle Database 19c is not possible. To upgrade those databases to Oracle Database 19c, either remove the Oracle RAC functionality before starting the upgrade, or upgrade from Oracle Database Standard Edition to Oracle Database Enterprise Edition. For more information about each step, including how to reconfigure your system after an upgrade, see My Oracle Support Note 2504078.1: "Desupport of Oracle Real Application Clusters (RAC) with Oracle Database Standard Edition 19c."

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)
- [My Oracle Support Document 2504878.1](https://support.oracle.com/rs?type=doc&id=2504078.1)

**Parent topic:** Changes in this Release for Oracle Grid Infrastructure

### Other Changes

Review other changes for Oracle Grid Infrastructure 19c.

- Rapid Home Provisioning (RHP) Name Change

  Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).

- Operating System Package Names

  To simplify the installation of operating system packages required for an Oracle Database and Oracle Grid Infrastructure installation on Linux, starting with 19c, only the operating system package names will be listed and not the exact package version. Install or update to the latest version of these packages from the minimum supported Linux distribution.Only packages that are officially released by Oracle or your operating system vendor are supported.

**Parent topic:** Changes in this Release for Oracle Grid Infrastructure
