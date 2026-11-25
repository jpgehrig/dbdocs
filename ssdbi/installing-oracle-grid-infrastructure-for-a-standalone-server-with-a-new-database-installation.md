Complete these steps to install Oracle Grid Infrastructure for a standalone server and then create a database that is managed by Oracle Restart.

Install Oracle Grid Infrastructure for a standalone server, which installs Oracle Restart and Oracle ASM, and creates one disk group.

You should have your network information, storage information, and operating system users and groups available to you before you start the installation. You should also be prepared to run root scripts or provide information to automate root scripts.

1.  Log in as the Oracle Restart software owner user (`oracle`).
2.  If this is the first time you are installing Oracle software, then create the Oracle base and the Oracle inventory directories as per the Oracle Optimal Flexible Architecture (OFA) recommendations. Specify the correct owner, group, and permissions for these directories.
        # mkdir -p /u01/app/oracle
        # mkdir -p /u01/app/oraInventory
        # chown -R oracle:oinstall /u01/app/oracle
        # chown -R oracle:oinstall /u01/app/oraInventory
        # chmod -R 775 /u01/app
3.  Download the Oracle Grid Infrastructure for a standalone server installation image files, create the grid home directory, and extract the image files in this grid home directory.
    For example:

        $ mkdir -p /u01/app/oracle/product/19.0.0/grid
        $ cd /u01/app/oracle/product/19.0.0/grid
        $ unzip -q /tmp/grid_home.zip

    **Note:**

    - Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Grid home directory that you created.
    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
4.  Configure and provision the shared disks for use with Oracle ASM Filter Driver (Oracle ASMFD).
    1.  Log in as `root` and set \$ORACLE_HOME to the grid home location and \$ORACLE_BASE to a temporary location.
            su root
            # set ORACLE_HOME=/u01/app/oracle/product/19.0.0/grid
            # set ORACLE_BASE=/tmp

        You set \$ORACLE_BASE to a temporary location to avoid creating diagnostic or trace files in the Grid home before the Oracle Grid Infrastructure installation.
    2.  Use the ASMCMD `afd_label` command to provision disk devices for use with Oracle ASM Filter Driver. For example:
            # cd /u01/app/oracle/product/19.0.0/grid/bin
            # ./asmcmd afd_label DATA1 /dev/rdsk/cXtYdZsA --init
            # ./asmcmd afd_label DATA2 /dev/rdsk/cXtYdZsB --init
            # ./asmcmd afd_label DATA3 /dev/rdsk/cXtYdZsC --init
    3.  Use the ASMCMD `afd_lslbl` command to verify the device has been marked for use with Oracle ASMFD. For example:
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsA
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsB
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsC
    4.  Unset \$ORACLE_BASE.
            # unset ORACLE_BASE
5.  Log in as the Oracle Restart software owner user amd run `gridSetup.sh` to start the Oracle Grid Infrastructure setup wizard:
        $ Grid_home/gridSetup.sh

    Where Grid_home is the Oracle Grid Infrastructure home directory.

    **Note:**

    You can use the `gridSetup.sh` command with the `-applyRU` and `-applyOneOffs` options to install Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.
6.  In the Select Configuration Option screen, select the Configure Oracle Grid Infrastructure for a Standalone Server (Oracle Restart) option to install and configure Oracle Restart and Oracle ASM. Click Next.
7.  During installation, disk paths mounted on Oracle ASM and registered on Oracle ASMFD with the string` AFD:*` are listed as default database storage candidate disks.
8.  Configure Oracle ASM as needed with additional disk groups.
    - The default Disk Group Name is DATA. You can enter a new name for the disk group, or use the default name.

    - Any additional disk devices that you create must be owned by the user performing the grid installation.
9.  If you want to use Oracle ASM Filter Driver (Oracle ASMFD) to manage your Oracle ASM disk devices, then select Configure Oracle ASM Filter Driver on the Create ASM Disk Group screen.
    On Linux, if you want to use Oracle ASM Filter Driver (Oracle ASMFD) to manage your Oracle ASM disk devices, then you must deinstall Oracle ASM library driver (Oracle ASMLIB) before you start the Oracle Grid Infrastructure installation.
10. Respond to the configuration prompts as needed to configure Oracle Grid Infrastructure. Click Help for information.
11. Provide information to automate root scripts, or run scripts as root when prompted by OUI.
    If you configure automation for running root scripts, and a root script fails, then you can fix the problem manually, and click Retry to run the root script again.
12. Start the Oracle Database installation, and select Oracle ASM disk groups for Oracle Database files storage. For assistance during installation, click Help on the Oracle Universal Installer page where you need more information.

**Related Topics**

- [Applying Patches During an Oracle Grid Infrastructure Installation or Upgrade](applying-patches-during-gi-install.md)
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/administer-filter-driver.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
