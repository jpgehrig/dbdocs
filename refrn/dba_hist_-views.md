## 2.5 DBA_HIST\_\* Views

The DBA_HIST views show the local Automatic Workload Repository (AWR) data present on a CDB root or a PDB.

If a DBA_HIST view is queried from a CDB root, the view shows all the AWR data stored on the CDB root.

If a DBA_HIST view is queried from a PDB, the view shows the subset of the CDB root AWR data that is specific to that PDB. Also, the view shows the PDB level snapshots at that PDB, if they exist.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for an introduction to AWR

- [Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for an introduction to Oracle Database views for accessing AWR data stored on the CDB root and individual PDBs in a multitenant environment
