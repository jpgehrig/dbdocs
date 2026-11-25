## Cloning an Oracle Database Home

Cloning an Oracle home involves creating a copy of the Oracle home and then configuring it for a new environment.

If you are performing multiple Oracle Database installations, then you may want to use cloning to create each Oracle home, because copying files from an existing Oracle Database installation takes less time than creating a new version of them. This method is also useful if the Oracle home that you are cloning has had patches applied to it. When you clone the Oracle home, the new Oracle home has the patch updates.

Perform these steps to clone an Oracle home.

**Note:**

During cloning, Oracle Universal Installer (OUI) prompts you to run scripts that require root privileges.

1.  Verify that the installation of Oracle Database that you want clone is successful.
    You can do this by reviewing the `installActionsdate_time.log` file for the installation session, which is typically located in the `/u01/app/oracle/oraInventory/logs` directory.

    If you install patches, then check their status using the following:

        $ cd $ORACLE_HOME/OPatch

    Include `$ORACLE_HOME/OPatch` in `$PATH`

        $ opatch lsinventory
2.  Stop all processes related to the Oracle home.
3.  Create a ZIP or TAR file with the Oracle home (but not the Oracle base) directory.
    For example, if the source Oracle installation is in the path `/u01/app/oracle/product/19.0.0/dbhome_1`, then you zip the `dbhome_1` directory by using the following command:

        # zip -r dbhome_1.zip /u01/app/oracle/product/19.0.0/dbhome_1

    You can also use the TAR command. For example:

        # tar -cvf dbhome_1.tar /u01/app/oracle/product/19.0.0/dbhome_1

    Do not include the `admin`, `fast_recovery_area`, and `oradata` directories that are under the Oracle base directory. These directories are created in the target installation later, when you create a new database there.
4.  Copy the ZIP or TAR file to the root directory of the target computer. If you use File Transfer Protocol (FTP), then transfer the ZIP or TAR file in binary mode only.
5.  Extract the ZIP or TAR file content using the following command:
        # unzip -d / dbhome_1.zip
        # tar -xvf dbhome_1.tar
6.  If necessary, change the ownership of the Oracle Database home to the Oracle Database installation owner user (`oracle`) belonging to the Oracle Inventory group (`oinstall`).
        # chown -R oracle:oinstall /u01/app/oracle/product/19.0.0/dbhome_1
7.  On the target computer, change the directory to the unzipped Oracle home directory, and remove all the `.ora` (\*`.ora`) files present in the unzipped `$ORACLE_HOME/network/admin` directory.
8.  Delete unnecessary files from the unzipped Oracle home directory.
    The unzipped Oracle home directory contains files that are relevant only to the source Oracle home. The following example shows how to remove these unnecessary files from the unzipped Oracle home directory:

    Remove the `.ora` files from the `network/admin` directory, and remove the old database entries from the `dbs` directory.

        # cd $ORACLE_HOME
        # rm -rf network/admin/*.ora
        # rm dbs/old_database_entries
9.  From the `$ORACLE_HOME/clone/bin` directory, run the `clone.pl` file for the unzipped Oracle home.
    Use the following syntax (you can also include one or more of the extended Oracle Database groups in the syntax):

    \$ORACLE_HOME/perl/bin/perl \$ORACLE_HOME/clone/bin/clone.pl ORACLE_BASE="target_oracle_base" ORACLE_HOME="target_oracle_home" OSDBA_GROUP=OSDBA_privileged_group OSOPER_GROUP=OSOPER_privileged_group OSBACKUPDBA_GROUP=OSBACKUPDBA_privileged_group OSDGDBA_GROUP=OSDGDBA_privileged_group OSKMDBA_GROUP=OSKMDBA_privileged_group OSRACDBA_GROUP=OSRACDBA_privileged_group `-defaultHomeName`
    For example:

        $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/clone/bin/clone.pl ORACLE_BASE="/u01/app/oracle" ORACLE_HOME="/u01/app/oracle/product/19.0.0/dbhome_1"
        OSDBA_GROUP=dba OSOPER_GROUP=oper OSBACKUPDBA_GROUP=backupdba OSDGDBA_GROUP=dgdba OSKMDBA_GROUP=kmdba OSRACDBA_GROUP=racdba -defaultHomeName

    **Note:**

    - In this command, if you do not provide the parameters for the operating system groups, then `clone.pl` uses the operating system group values from the source home.

    - Run the `$ORACLE_HOME/perl/bin/perl $ORACLE_HOME/clone/bin/clone.pl -help` command for more information about the command option flags.

    - The `clone.pl `script is deprecated in Oracle Database 19c and can be removed in a future release. Hence, Oracle recommends that you use the software-only installation option, available in the database installer, instead of `clone.pl `to clone your database.

    OUI starts, and then records the cloning actions in the `cloneActionstimestamp.log` file. This log file is typically located in `/u01/app/oracle/oraInventory/logs` directory.
10.  Use the following commands to run Net Configuration Assistant to configure the connection information for the new database:
        $ cd $ORACLE_HOME/bin
        $ ./netca
11. Use the following commands to run Database Configuration Assistant to create a new Oracle Database for the newly-cloned oracle home:
        $ cd $ORACLE_HOME/bin
        $ ./dbca

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cloning-oracle-clusterware.md)
- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Oracle Database Postinstallation Tasks](oracle-database-postinstallation-tasks.md)
