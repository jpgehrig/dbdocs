Review the following topics for information about using earlier Oracle Database releases with Oracle Grid Infrastructure 19c installations:

- [General Restrictions for Using Earlier Oracle Database Releases](general-restrictions-for-using-earlier-oracle-database-releases.md)
  You can use Oracle Database 19c, 18c, Oracle Database 12c releases 1 and 2, and Oracle Database 11g release 2 (11.2.0.3 or later) with Oracle Grid Infrastructure 19c.
- [Making Oracle ASM Available to Earlier Oracle Database Releases](making-oracle-asm-available-to-earlier-oracle-database-releases.md)
  To use Oracle ASM with Oracle Database releases earlier than Oracle Database 12c Release 2 (12.2), you must pin all the cluster nodes.
- [Using ASMCA to Administer Disk Groups for Earlier Database Releases](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
  Use Oracle ASM Configuration Assistant (ASMCA) to create and modify disk groups when you install earlier Oracle databases and Oracle RAC databases on Oracle Grid Infrastructure installations.
- [Pinning Cluster Nodes for Oracle Database Release 11.x](pinning-cluster-nodes-for-oracle-database-release-11-x.md)
  When Oracle Clusterware 12c Release 2 (12.2) or later releases are installed on a cluster with no previous Oracle software version, it configures the cluster nodes dynamically, which is compatible with Oracle Database Release 11.2 and later, but Oracle Database 10g and 11.1 require a persistent configuration.
- [Using the Correct LSNRCTL Commands](using-the-correct-lsnrctl-commands.md)
  To administer Oracle Database 19c local and scan listeners using the `lsnrctl` command, set your `$ORACLE_HOME` environment variable to the path for the Oracle Grid Infrastructure home (Grid home).

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
