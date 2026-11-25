To Plug the PDB from the earlier release CDB to the later release CDB, use the `CREATE PLUGGABLE DATABASE` command.

This procedure example shows how to plug in a PDB when you are using Oracle-Managed Files. Refer to Oracle Database Administrator’s Guide for additional information about plugging in PDBs.

1.  Connect to the later release CDB.

2.  Plug in the earlier release PDB using the following SQL command, where `pdb` is the name of the PDB, and `path` is the path where the PDB XML file is located:

    CREATE PLUGGABLE DATABASE pdb USING 'path/pdb.xml';

    For example:

        SQL> CREATE PLUGGABLE DATABASE salespdb USING '/home/oracle/salespdb.xml';

    The following response displays when the command is completed:

        Pluggable database created.

**Note:**

When you plug in an earlier release PDB, the PDB is in restricted mode. You can only open the PDB for upgrade.

**Related Topics**

- [Oracle Database Administrator’s Guide](../multi/plugging-in-a-pdb.md)

**Parent topic:** [Upgrading Pluggable Databases Sequentially](upgrading-pluggable-databases-sequentially.md)
