Oracle recommends that you complete these tasks after installation.

- [Configuring IPMI-based Failure Isolation Using Crsctl](configuring-ipmi-based-failure-isolation-using-crsctl.md)
  On Oracle Solaris and AIX platforms, where Oracle does not currently support the native IPMI driver, DHCP addressing is not supported and manual configuration is required for IPMI support.
- [Creating a Backup of the root.sh Script](creating-a-backup-of-the-root-sh-script.md)
  Oracle recommends that you back up the `root.sh` script after you complete an installation.
- [About Installing Oracle Autonomous Health Framework](downloading-and-installing-the-orachk-health-check-tool.md)
  Install the latest version of Oracle Autonomous Health Framework to perform proactive heath checks and collect diagnostics data for the Oracle software stack.
- [Creating a Fast Recovery Area](creating-a-fast-recovery-area.md)
  During an Oracle Restart installation, you can create only one disk group. During an Oracle Clusterware installation, you can create multiple disk groups. If you plan to add an Oracle Database for a standalone server or an Oracle RAC database, then you should create the fast recovery area for database files.
- [Checking the SCAN Configuration](checking-the-scan-configuration.md)
  The Single Client Access Name (SCAN) is a name that is used to provide service access for clients to the cluster. Because the SCAN is associated with the cluster as a whole, rather than to a particular node, the SCAN makes it possible to add or remove nodes from the cluster without needing to reconfigure clients.
- [Setting Resource Limits for Oracle Clusterware and Associated Databases and Applications](setting-resource-limits-for-oracle-clusterware-and-associated-databases-and-applications.md)
  After you have completed Oracle Grid Infrastructure installation, you can set resource limits in the `Grid_home``/crs/install/s_crsconfig_``nodename``_env.txt` file.

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
