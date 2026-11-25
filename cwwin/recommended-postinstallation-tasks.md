## Recommended Postinstallation Tasks

Oracle recommends that you complete these tasks as needed after installing Oracle Grid Infrastructure.

- [About Installing Oracle Autonomous Health Framework](downloading-and-installing-the-orachk-health-check-tool.md)
  Install the latest version of Oracle Autonomous Health Framework to perform proactive heath checks and collect diagnostics data for the Oracle software stack.
- [Optimize Memory Usage for Programs](optimize-memory-usage-for-programs.md)
  The Windows operating system should be optimized for Memory Usage of 'Programs' instead of 'System Caching'.
- [Create a Fast Recovery Area Disk Group](create-a-fast-recovery-area-disk-group.md)
  You should create a separate disk group for the fast recovery area.
- [Checking the SCAN Configuration](checking-the-scan-configuration.md)
  The SCAN is a name that provides service access for clients to the cluster. You can use the command `cluvfy comp scan` (located in `Grid_home``\bin`) to confirm that the DNS is correctly associating the SCAN with the addresses.

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
