You can upgrade PDBs by unplugging a PDB from an earlier release CDB, plugging it into a later release CDB, and then upgrading that PDB to the later release.

CDBs can contain zero, one, or more pluggable databases (PDBs). After you install a new Oracle Database release, or after you upgrade the CDB (`CDB$ROOT`), you can upgrade one or more PDB without upgrading all of the PDBs on the CDB.

You can choose the upgrade plan that meets the needs for your service delivery. For example, you can use Oracle Database Upgrade Assistant (DBUA) to upgrade a set of PDBs, or you can use a manual upgrade to upgrade PDBs individually, or with inclusion or exclusion lists. You can upgrade the CDB and all PDBs (an In Parallel manual upgrade), or you can upgrade the CDB, and then upgrade PDBs sequentially, either individually, or in sets using inclusion or exclusion lists.

The following is a high-level list of the steps required for sequential PDB upgrades:

1.  Unplug the earlier release PDB from the earlier release CDB.

2.  Drop the PDB from the CDB.

3.  Plug the earlier release PDB into the later release CDB.

4.  Upgrade the earlier release PDB to a later release.

With Oracle Database 12c Release 2 (12.2) and later releases, you can provide lists to the Parallel Upgrade Utility to upgrade PDBs:

- Priority lists, to set the order in which PDBs are upgraded

- Inclusion lists, which enable you to designate a set of PDBs to upgrade after the PDBs listed in the priority list are upgraded

- Exclusion lists, which enable you to designate a set of PDBs that are not upgraded

**Note:**

A PDB cannot be recovered unless it is backed up. After upgrading using the method of creating a CDB and plugging in a PDB, be sure to back up the PDB.

**Related Topics**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md)
- [Oracle Database Administrator’s Guide](../multi/removing-a-pdb.md)

**Parent topic:** [Upgrading Multitenant Architecture Sequentially Using Unplug-Plug](upgrade-multitenant-architecture-sequentially.md)
