## Create a Fast Recovery Area Disk Group

You should create a separate disk group for the fast recovery area.

During installation of Oracle Grid Infrastructure, if you select Oracle ASM for storage, a single disk group is created to store the Oracle Clusterware files. If you plan to create a single-instance database, an Oracle RAC database, or an Oracle RAC One Node database, then this disk group can also be used to store the data files for the database. However, Oracle recommends that you create a separate disk group for the fast recovery area.

- [About the Fast Recovery Area and the Fast Recovery Area Disk Group](about-fast-recovery-area-and-fast-recovery-area-disk-group.md)
  The fast recovery area is a unified storage location for all Oracle Database files related to recovery.
- [Creating the Fast Recovery Area Disk Group](creating-the-fast-recovery-area-disk-group.md)
  You can use ASMCA to create an Oracle ASM disk group for the fast recovery area.

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
