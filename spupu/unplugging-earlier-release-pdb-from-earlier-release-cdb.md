To prepare for upgrading the PDB, use this procedure to unplug the PDB from the earlier release CDB.

1.  Run the Pre-Upgrade Information Tool on the PDB.

    For example, where the PDB named `salespdb` is running in the CDB in `$ORACLE_HOME_12.2`:

        $ORACLE_HOME_12.2/jdk/bin/java -jar
        $ORACLE_HOME_19/rdbms/admin/preupgrade.jar dir /tmp -c salespdb

2.  Run `preupgrade_fixups.sql` on your source database.

    For example:

        CONNECT / AS SYSDBA
        SQL> ALTER SESSION SET CONTAINER=salespdb;

        SQL> @/tmp/preupgrade_fixups_salespdb.sql

3.  Follow all recommendations listed in `preupgrade.log`.

4.  Close the PDB you want to unplug.

    For example, use the following command to close the PDB `salespdb`:

        SQL> ALTER PLUGGABLE DATABASE salespdb CLOSE;

5.  Log back in to `CDB$ROOT`:
        CONNECT / AS SYSDBA
        SQL> ALTER SESSION SET CONTAINER=CDB$ROOT;

6.  Unplug the earlier release PDB using the following SQL command syntax, where `pdb` is the name of the PDB, and `path` is the location of the PDB XML file:

        ALTER PLUGGABLE DATABASE pdb UNPLUG INTO 'path/pdb.xml';

    For example, where the pdb name is `salespdb` and path is `/home/oracle/salespdb.xml`:

        SQL> ALTER PLUGGABLE DATABASE salespdb UNPLUG INTO '/home/oracle/salespdb.xml';

    The following response displays when the command is completed:

        Pluggable database altered

7.  Drop the pluggable database `salespdb`, but keep data files.

    Oracle recommends that you drop `salespdb` after this procedure to clean up leftover information in the CDB views, and to help to avoid future issues. As a best practice guideline, back up your PDB in the destination CDB first, and then issue the `DROP` command on the source.

    **Caution:**

    After you drop the PDB from its original CDB, you cannot revert to it using previously taken backup, because the `DROP` command removes backup files.

    To drop the pluggable database, enter the following command:

        SQL> DROP PLUGGABLE DATABASE salespdb KEEP DATAFILES;

8.  Exit.

**Parent topic:** [Upgrading Pluggable Databases Sequentially](upgrading-pluggable-databases-sequentially.md)
