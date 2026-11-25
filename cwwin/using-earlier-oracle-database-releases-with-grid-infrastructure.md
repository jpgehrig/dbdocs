## Using Earlier Oracle Database Releases with Grid Infrastructure

Review the guidelines and restrictions for using earlier Oracle Database releases with Oracle Grid Infrastructure 19c installations.

- [General Restrictions for Using Earlier Oracle Database Releases](general-restrictions-for-using-earlier-oracle-database-releases.md)
  You can use Oracle Database 12c Release 1 and Release 2 and Oracle Database 11g Release 2 with Oracle Grid Infrastructure 12c Release 2 (12.2).
- [Configuring Earlier Release Oracle Database on Oracle ACFS](configuring-earlier-release-oracle-database-on-oracle-acfs.md)
  Review this information to configure a 11.2 release Oracle Database on Oracle Automatic Storage Management Cluster File System (Oracle ACFS).
- [Using ASMCA to Administer Disk Groups for Earlier Database Releases](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
  Starting with Oracle Grid Infrastructure 11g Release 2, Oracle ASM is installed as part of an Oracle Grid Infrastructure installation, with Oracle Clusterware.
- [Using the Correct LSNRCTL Commands](using-the-correct-lsnrctl-commands.md)
  Do not attempt to use the `lsnrctl` programs from Oracle home locations for earlier releases because they cannot be used with the new release.
- [Starting and Stopping Cluster Nodes or Oracle Clusterware Resources](starting-and-stopping-cluster-nodes-or-clusterware-resources.md)
  Before shutting down Oracle Clusterware 19c, if you have an Oracle Database 12c Release 1 (12.1) or Oracle Database 11g Release 2 (11.2) database registered with Oracle Clusterware 19c, then you must perform additional steps to ensure the resources are stopped.

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
