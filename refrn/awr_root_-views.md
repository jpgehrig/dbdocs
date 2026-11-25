## 2.3 AWR_ROOT\_\* Views

The AWR_ROOT views show the AWR data stored only on a CDB root. In general, the AWR_ROOT views are equivalent to the DBA_HIST views.

When the AWR_ROOT views are accessed from a CDB root, they show the AWR data specific to the CDB root.

When the AWR_ROOT views are accessed from a PDB, they show the AWR data specific to that PDB.

**See Also:**

- "[AWR_PDB\_\* Views](awr_pdb_-views.md)"

- [Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for an introduction to AWR

- [Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for more information about AWR_ROOT views and related views for accessing AWR in a multitenant environment
