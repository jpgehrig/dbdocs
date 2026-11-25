## Changes in this Release for Oracle Database

The following are changes in Oracle Real Application Clusters Installation Guide for Oracle Database 19c.

- New Features
  Review new features available with Oracle Database 19c.
- Deprecated Features
  Review features that are deprecated starting with Oracle Database 19c.
- Desupported Features
  Review features that are desupported with Oracle Database 19c.
- Other Changes
  Review other changes for Oracle Database 19c.

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

### New Features

Review new features available with Oracle Database 19c.

- Root Scripts Automation Support for Oracle Database Installation
- Resupport of Direct File Placement for OCR and Voting Disks
- Optional Install for the Grid Infrastructure Management Repository

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

**Parent topic:** Changes in this Release for Oracle Database

#### Root Scripts Automation Support for Oracle Database Installation

Starting with Oracle Database 19c, the database installer, or setup wizard, provides options to set up permissions to run the root configuration scripts automatically, as required, during a database installation. You continue to have the option to run the root configuration scripts manually.

Setting up permissions for root configuration scripts to run without user intervention can simplify database installation and help avoid inadvertent permission errors.

**Related Topics**

- [Installing Oracle RAC and Oracle RAC One Node Database Software](installing-oracle-rac-rac-one-node-software-only.md)

**Parent topic:** New Features

#### Resupport of Direct File Placement for OCR and Voting Disks

Starting with Oracle Grid Infrastructure 19c, the desupport for direct OCR and voting disk file placement on shared file systems is rescinded for Oracle Standalone Clusters. For Oracle Domain Services Clusters the requirement to place OCR and voting files in Oracle Automatic Storage Management (Oracle ASM) on top of files hosted on shared file systems and used as ASM disks remains.

In Oracle Grid Infrastructure 12c Release 2 (12.2), Oracle announced that it would no longer support the placement of the Oracle Grid Infrastructure Oracle Cluster Registry (OCR) and voting files directly on a shared file system. This desupport is now rescinded. Starting with Oracle Grid Infrastructure 19c (19.3), with Oracle Standalone Clusters, you can again place OCR and voting disk files directly on shared file systems.

**Related Topics**

- [Using a Cluster File System for Oracle Clusterware Files](../cwlin/using-a-cluster-file-system-for-oracle-clusterware-files.md)

**Parent topic:** New Features

#### Optional Install for the Grid Infrastructure Management Repository

Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.

The data contained in the GIMR is the basis for preventative diagnostics based on applied Machine Learning and can help to increase the availability of Oracle Real Application Clusters (Oracle RAC) databases. Having an optional installation for the GIMR allows for more flexible storage space management and faster deployment, especially during the installation of test and development systems.

**Related Topics**

- [About the Grid Infrastructure Management Repository](../cwlin/about-gimr.md)

**Parent topic:** New Features

### Deprecated Features

Review features that are deprecated starting with Oracle Database 19c.

For more information about deprecated features, parameters, and views, refer to Oracle Database Upgrade Guide

- Init.ora Parameter CLUSTER_DATABASE_INSTANCES is Deprecated

  The Oracle Database initialization parameter `CLUSTER_DATABASE_INSTANCES` is deprecated in Oracle Database 19c (19.1)

  The `init.ora` parameter `CLUSTER_DATABASE_INSTANCES` specifies the number of configured Oracle Real Application Clusters (Oracle RAC) instances. Starting with Oracle Database 19c and later releases, the number of configurable Oracle RAC instances is derived automatically from the Oracle Clusterware resource definitions. There is no replacement for this parameter, because there is no longer a reason to have this parameter.

- Deprecation of the SERVICE_NAMES Initialization Parameter

  Starting with Oracle Database 19c, customer use of the `SERVICE_NAMES` parameter is deprecated. It can be desupported in a future release.

  The use of the `SERVICE_NAMES` parameter is no longer actively supported. It must not be used for high availability (HA) deployments. It is not supported to use service names parameter for any HA operations. This restriction includes FAN, load balancing, `FAILOVER_TYPE`, `FAILOVER_RESTORE`, `SESSION_STATE_CONSISTENCY`, and any other uses.

  To manage your services, Oracle recommends that you use the `SRVCTL` or `GDSCTL` command line utilities, or the `DBMS_SERVICE` package.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in this Release for Oracle Database

### Desupported Features

Review features that are desupported with Oracle Database 19c.

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

**Parent topic:** Changes in this Release for Oracle Database

### Other Changes

Review other changes for Oracle Database 19c.

- Rapid Home Provisioning (RHP) Name Change

  Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).

**Parent topic:** Changes in this Release for Oracle Database
