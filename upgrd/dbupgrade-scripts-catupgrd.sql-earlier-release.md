## About Dbupgrade Scripts and catupgrd.sql in Earlier Releases of Oracle Database

The function of the `catupgrd.sql` script is replaced by the Parallel Upgrade Utility, `catctl.pl`, and the `dbupgrade` and `dbupgrade.cmd` scripts.

In earlier releases of Oracle Database, the `catupgrd.sql` Upgrade Utility processed the upgrade. Starting with Oracle Database 12c release 1 (12.1), this script is replaced by the `catctl.pl` Parallel Upgrade Utility, and its command-line script, `dbupgrade`. The Parallel Upgrade Utility provides both parallel processing mode and serial modes.

The `dbupgrade` script calls `catctl.pl` to create and alter a set of data dictionary tables. The upgrade scripts also call `catctl.pl` to upgrade or install the following database components in the new Oracle Database 12c database:

- Oracle Database Catalog Views

- Oracle Database Packages and Types

- JServer JAVA Virtual Machine

- Oracle Database Java Packages

- Oracle XDK

- Oracle Real Application Clusters

- Oracle Workspace Manager

- Oracle Multimedia

- Oracle XML Database

- OLAP Analytic Workspace

- Oracle OLAP API

- Oracle Text

- Oracle Spatial and Graph

- Oracle Data Mining

- Oracle Label Security

- Messaging Gateway

- Oracle Database Vault

**Parent topic:** [Upgrading Oracle Database Manually Using Parallel Upgrade Utility](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)
