## Changes In This Release for Oracle Real Application Clusters

This preface lists changes in Oracle Real Application Clusters Installation Guide

- Changes in Oracle Database 19c
  The following are changes in Oracle Real Application Clusters Installation Guide for Oracle Database 19c.

### Changes in Oracle Database 19c

The following are changes in Oracle Real Application Clusters Installation Guide for Oracle Database 19c.

- Deprecated Features for Oracle RAC 19c
- Desupported Features for Oracle RAC 19c

**Parent topic:** Changes In This Release for Oracle Real Application Clusters

#### Deprecated Features for Oracle RAC 19c

The following feature is deprecated in this release:

- Deprecation of the SERVICE_NAMES Initialization Parameter

  Starting with Oracle Database 19c, customer use of the `SERVICE_NAMES` parameter is deprecated. It can be desupported in a future release.

  The use of the `SERVICE_NAMES` parameter is no longer actively supported. It must not be used for high availability (HA) deployments. It is not supported to use service names parameter for any HA operations. This restriction includes FAN, load balancing, `FAILOVER_TYPE`, `FAILOVER_RESTORE`, `SESSION_STATE_CONSISTENCY`, and any other uses.

  To manage your services, Oracle recommends that you use the `SRVCTL` or `GDSCTL` command line utilities, or the `DBMS_SERVICE` package.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in Oracle Database 19c

#### Desupported Features for Oracle RAC 19c

The following feature is desupported in this release:

- Desupport of Leaf Nodes in Flex Cluster Architecture

  Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.

  In Oracle Grid Infrastructure 19c (19.1) and later releases, all nodes in an Oracle Flex Cluster function as hub nodes. The capabilities offered by Leaf nodes in the original implementation of the Oracle Flex Cluster architecture can as easily be served by hub nodes. Therefore, leaf nodes are no longer supported.

- Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition

  Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

  Upgrading Oracle Database Standard Edition databases that use Oracle Real Application Clusters (Oracle RAC) functionality from earlier releases to Oracle Database 19c is not possible. To upgrade those databases to Oracle Database 19c, either remove the Oracle RAC functionality before starting the upgrade, or upgrade from Oracle Database Standard Edition to Oracle Database Enterprise Edition. For more information about each step, including how to reconfigure your system after an upgrade, see My Oracle Support Note 2504078.1: "Desupport of Oracle Real Application Clusters (RAC) with Oracle Database Standard Edition 19c."

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

[My Oracle Support Note 2504078.1](https://support.oracle.com/rs?type=doc&id=2504078.1)

**Parent topic:** Changes in Oracle Database 19c
