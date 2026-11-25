## Changes in this Release for Oracle Clusterware

A list of changes in Oracle Grid Infrastructure Installation Guide for Windows.

- Changes in Oracle Clusterware 19c
  The following are the changes in this guide for Oracle Clusterware 19c:

### Changes in Oracle Clusterware 19c

The following are the changes in this guide for Oracle Clusterware 19c:

- Deprecated Features for Oracle Clusterware 19c
- Desupported Features for Oracle Clusterware 19c

**Parent topic:** Changes in this Release for Oracle Clusterware

#### Deprecated Features for Oracle Clusterware 19c

The following feature is deprecated in this release:

- Deprecation of Addnode Script

  The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.

  The `addnode` script can be removed in a future release. Instead of using the `addnode` script (`addnode.sh` or `addnode.bat`), add nodes by using the installer wizard. The installer wizard provides many enhancements over the `addnode` script. Using the installer wizard simplifies management by consolidating all software lifecycle operations into a single tool.

- Deprecation of `clone.pl` Script

  The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.

  The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

**Parent topic:** Changes in Oracle Clusterware 19c

#### Desupported Features for Oracle Clusterware 19c

The following feature is desupported in this release:

- Desupport of Leaf Nodes in Flex Cluster Architecture

  Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.

  In Oracle Grid Infrastructure 19c (19.1) and later releases, all nodes in an Oracle Flex Cluster function as hub nodes. The capabilities offered by Leaf nodes in the original implementation of the Oracle Flex Cluster architecture can as easily be served by hub nodes. Therefore, leaf nodes are no longer supported.

- Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition

  Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

  Upgrading Oracle Database Standard Edition databases that use Oracle Real Application Clusters (Oracle RAC) functionality from earlier releases to Oracle Database 19c is not possible. To upgrade those databases to Oracle Database 19c, either remove the Oracle RAC functionality before starting the upgrade, or upgrade from Oracle Database Standard Edition to Oracle Database Enterprise Edition. For more information about each step, including how to reconfigure your system after an upgrade, see My Oracle Support Note 2504078.1: "Desupport of Oracle Real Application Clusters (RAC) with Oracle Database Standard Edition 19c."

[Oracle Database Upgrade Guide](../upgrd/index.md)

[My Oracle Support Document 2504878.1](https://support.oracle.com/rs?type=doc&id=2504078.1)

**Parent topic:** Changes in Oracle Clusterware 19c
