Perform these steps to move a PDB cross-platform from source release 19.19 RU (Linux x86-64 and Microsoft Windows x64) to target release 19.19 Linux for Arm (aarch64).

Before you unplug your PDB from the source container, run these queries to clear the datapatch inventory:

    /* Delete all rows from datapatch tables to clear the inventory */

    alter session set container=pdb_name;

    delete from dba_registry_sqlpatch;

    delete from dba_registry_sqlpatch_ru_info;

    commit;

**Parent topic:** [Issues Affecting Oracle on Linux for Arm (aarch64) for Oracle Database 19c](issues-affecting-linux-arm-aarch64-oracle-database-19.14.md)
