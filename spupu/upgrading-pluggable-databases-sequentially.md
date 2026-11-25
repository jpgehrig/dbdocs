To upgrade PDBs after upgrading the Container Database (CDB), use the unplug-plug technique.

- [Unplugging the Earlier Release PDB from the Earlier Release CDB](unplugging-earlier-release-pdb-from-earlier-release-cdb.md)
  To prepare for upgrading the PDB, use this procedure to unplug the PDB from the earlier release CDB.
- [Plugging in the Earlier Release PDB to the Later Release CDB](plugging-in-earlier-release-pdb-to-the-later-release-cdb.md)
  To Plug the PDB from the earlier release CDB to the later release CDB, use the `CREATE PLUGGABLE DATABASE` command.
- [Upgrading the Earlier Release PDB to the Later Release](upgrading-earlier-release-pdb-to-later-release.md)
  Open PDBs in `UPGRADE` mode use the Parallel Upgrade Utility to carry out the upgrade of the earlier-release PDB to the release level of the CDB.
- [Use Inclusion or Exclusion Lists for PDB Upgrades](use-inclusion-or-exclusion-lists-for-pdb-upgrades.md)
  If you want to upgrade a subset of earlier release PDBs, then use inclusion or exclusion lists to avoid reupgrading the CDB or PDBs that are at the new release level.
