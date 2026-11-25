Complete these steps to Install Oracle Grid Infrastructure for a standalone server and then create a database that is managed by Oracle Restart.

Install Oracle Grid Infrastructure for a standalone server, which installs Oracle Restart and Oracle ASM, and creates one disk group.

You should have your network information, storage information, and operating system users and groups available to you before you start the installation. You should also be prepared to run root scripts or provide information to automate root scripts.

1.  Log in as the Oracle Restart software owner user (`oracle`).
2.  Download the Oracle Grid Infrastructure for a standalone server installation image files, create the Grid home directory, and extract the image files in this Grid home directory.
    For example:

        $ mkdir -p /u01/app/oracle/product/19.0.0/grid
        $ chgrp oinstall /u01/app/oracle/product/19.0.0/grid
        $ cd /u01/app/oracle/product/19.0.0/grid
        $ unzip -q /tmp/grid.zip

    **Note:**

    Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Grid home directory that you created.
3.  Run `gridSetup.sh` to start the Oracle Grid Infrastructure setup wizard:
        $ Grid_home/gridSetup.sh

    **Note:**

    You can use the `gridSetup.sh` command with the `-applyRU` and `-applyOneOffs` options to install Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.
4.  In the Select Configuration Option screen, select the Configure Oracle Grid Infrastructure for a Standalone Server (Oracle Restart) option to install and configure Oracle Restart and Oracle ASM. Click Next.
5.  During installation, disk paths mounted on Oracle ASM with the string` AFD:*` are listed as default database storage candidate disks.
6.  Configure Oracle ASM as needed with additional disk groups.
    - The default Disk Group Name is DATA. You can enter a new name for the disk group, or use the default name.

    - Any additional disk devices that you create must be owned by the user performing the grid installation.
7.  Respond to the configuration prompts as needed to configure Oracle Grid Infrastructure. Click Help for information.
8.  Provide information to automate root scripts, or run scripts as `root` when prompted by OUI.
    If you configure automation for running root scripts, and a root script fails, then you can fix the problem manually, and click Retry to run the root script again.
9.  Start the Oracle Database installation, and select Oracle ASM disk groups for Oracle Database files storage. For assistance during installation, click Help on the Oracle Universal Installer page where you need more information.

**Related Topics**

- [Optimal Flexible Architecture File Path Examples](optimal-flexible-architecture-file-path-examples.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
