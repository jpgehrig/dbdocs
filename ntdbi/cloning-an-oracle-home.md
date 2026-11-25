## Cloning an Oracle Home

Follow these steps to clone an Oracle home.

**Note:**

During cloning, Oracle Universal Installer (OUI) prompts you to run scripts that require root privileges.

1.  Verify that the installation of Oracle Database to clone is successful.

    You can do this by reviewing the `installActions``date_time``.log` file for the installation session, which is typically located in the following directory:

    `C:\Program Files\Oracle\Inventory\logs`

    If you have installed patches, you can check their status by running the following commands at a command prompt:

        C:\ORACLE_HOME\OPatch> set ORACLE_HOME=ORACLE_HOME_using_patch
        C:\ORACLE_HOME\OPatch> opatch lsinventory

2.  Stop all processes related to the Oracle home. You can stop Oracle services by the following method:

    Microsoft Windows Services utility: From the Start menu, select Control Panel, then Administrative Tools, then Services. Right-click any service that begins with Oracle, and then from the menu, select Stop.

3.  Create a ZIP file with the Oracle home (but not Oracle base) directory.

    For example, if the source Oracle installation is in `C:\app`\\username`\product\19.0.0\dbhome_1` you zip the `dbhome_1` directory, leaving out the `admin`, `flash_recovery_area`, and `oradata` directories that are under `19.0.0`. These directories are created in the target installation later on when you create a new database there.

4.  Copy the ZIP file to the root directory of the target computer. If you use File Transfer Protocol (FTP), then transfer the ZIP file in binary mode only.

5.  Extract the ZIP file contents, selecting the Use folder names option.

6.  Repeat steps 4 and 5 for each computer where you want to clone the Oracle home, unless the Oracle home is on a shared storage device.

7.  In the source Oracle home, restart the services that you stopped in step 2.

8.  On the target computer, `cd` to the unzipped Oracle home directory, and perform the following steps:

    1.  Remove the `*.ora` files that are present in unzipped `ORACLE_HOME``\network\admin` directory, such as `listener.ora`, `sqlnet.ora`, and `tnsnames.ora`.

    2.  Delete unnecessary files from the unzipped Oracle home directory.

        The unzipped Oracle home directory contains files that are relevant only to the source Oracle home. Remove the unnecessary files from the unzipped Oracle home in the `log, crs/init, crf,` and `cdata` directories. The following example shows how to remove these unnecessary files from the unzipped Oracle home directory:

            [grid_home]# cd copy_path
                [grid_home]# rm -rf host_name
                [grid_home]# rm -rf log/host_name
                [grid_home]# rm -rf gpnp/host_name
                [grid_home]# rm -rf find gpnp -type f -exec rm -f {} \;
                   c:\<Gridhome> c:\mksnt\find gpnp -type f and delete these files.
                   gpnp/init/host_name
                   gpnp/init/host_name.pid
                     gpnp/profiles/peer/profile.xml
                   gpnp/profiles/peer/profile_orig.xml
                   gpnp/host_name/profiles/peer/profile.old
                   gpnp/host_name/profiles/peer/profile.xml
                            gpnp/host_name/profiles/peer/profile_orig.xml
                   gpnp/host_name/wallets/pa/cwallet.sso
                   gpnp/host_name/wallets/peer/cwallet.sso
                   gpnp/host_name/wallets/prdr/cwallet.sso
                   gpnp/host_name/wallets/root/ewallet.p12
                   gpnp/wallets/pa/cwallet.sso
                   gpnp/wallets/peer/cwallet.sso
                   gpnp/wallets/prdr/cwallet.sso
                   gpnp/wallets/roor/ewallet.p12

                [grid_home]# find cfgtoollogs -type f -exec rm -f {} \;
                [grid_home]# rm -rf crs/init/*
            [grid_home]# rm -rf cdata/*
            [grid_home]# rm -rf crf/*
            [grid_home]# rm -rf network/admin/*.ora

9.  From the `ORACLE_HOME\clone\bin` directory, run `clone.pl` for the unzipped Oracle home.

    Use the following syntax:

        C:\ORACLE_HOME\clone\bin>target_home\perl\bin\perl.exe clone.pl
        ORACLE_HOME="target location" ORACLE_BASE="target Base location" ORACLE_HOME_USER="Windows User Account" OSDBA_GROUP=OSDBA_privileged_group
        OSOPER_GROUP=OSOPER_privileged_group OSBACKUPDBA_GROUP=OSBACKUPDBA_privileged_group OSDGDBA_GROUP=OSDGDBA_privileged_group OSKMDBA_GROUP=OSKMDBA_privileged_group OSRACDBA_GROUP=OSRACDBA_privileged_group -defaultHomeName

    where `ORACLE_HOME_USER="Windows User Account"` is the Oracle Home User for the cloned home.

    Windows Built-in Account is used as the Oracle Home User if the parameter for `ORACLE_HOME_USER` is not specified.

    For example:

        C:\ORACLE_HOME\clone\bin>target_home\perl\bin\perl.exe clone.pl

        ORACLE_HOME="C:\app\username\product\19.0.0\dbhome_1"
        ORACLE_BASE="C:\app\username"
        ORACLE_HOME_USER="mydomain\username" -defaultHomeName
        OSDBA_GROUP=dba OSOPER_GROUP=oper OSBACKUPDBA_GROUP=backupdba OSDGDBA_GROUP=dgdba OSKMDBA_GROUP=kmdba OSRACDBAGROUP=racdba -defaultHomeName

    Oracle Universal Installer starts, and then records the cloning actions in the `cloneActions``timestamp``.log` file. This log file is normally located in `C:\Program Files\Oracle\Inventory\logs`.

    **Note:**

    - Run `\ORACLE_HOME\clone\bin>``target_home``\perl\bin\perl.exe clone.pl -help` command for more information about the command option flags.

    - Oracle recommends that you use the software-only installation option, available in the database installer, instead of `clone.pl` to clone your database.

10. To configure connection information for the new database, run Net Configuration Assistant.

    To start Net Configuration Assistant, select Start, then All Programs, then Oracle - HOMENAME, then Configuration and Migration Tools, and then Net Configuration Assistant.

11. To create a new database for the newly cloned Oracle home, run Oracle Database Configuration Assistant.

    To start Oracle Database Configuration Assistant, select Start, then All Programs, then Oracle - HOMENAME, then Configuration and Migration Tools, and then Database Configuration Assistant.

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
