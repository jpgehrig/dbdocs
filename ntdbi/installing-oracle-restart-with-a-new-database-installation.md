## Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation

Complete these steps to install Oracle Restart and then create a database that is managed by Oracle Restart.

Install Oracle Restart, which installs Oracle Restart and Oracle ASM, and creates one disk group.

1.  Log in as the Oracle Restart software owner user (`grid`).
2.  Download the Oracle Grid Infrastructure installation image files, create the Grid home directory, and extract the image files in this Grid home directory.
    For example:

    `C:\> mkdir \app\oracle\product\19.0.0\grid`

    `C:\> icacls grid:oinstall \app\oracle\product\19.0.0\grid`

    `C:\> cd \app\oracle\product\19.0.0\grid`

    `C:\> unzip -q download_location\grid_home.zip`

    **Note:**

    Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Grid home directory that you created.
3.  Run `setup.exe` to start the Oracle Grid Infrastructure installation wizard.
    `C:>` `Grid_home``\setup.exe`

    **Note:**

    You can use the `gridSetup.exe` command with the `-applyRU` and `-applyOneOffs` options to install Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.
4.  In the Select Configuration Option screen, select the Configure Oracle Restart option to install and configure Oracle Restart and Oracle ASM. Click Next.
5.  During installation, disk paths mounted on Oracle ASM and registered on Oracle ASMFD with the string `ORCL:*` are listed as default database storage candidate disks.
6.  Configure Oracle ASM as needed with additional disk groups.
    - The default Disk Group Name is DATA. You can enter a new name for the disk group, or use the default name.

    - Any additional disk devices that you create must be owned by the user performing the grid installation.
7.  Respond to the configuration prompts as needed to configure Oracle Grid Infrastructure. Click Help for information.
8.  Provide information to automate root scripts, or run scripts as root when prompted by Oracle Universal Installer.
    If you configure automation for running root scripts, and a root script fails, then you can fix the problem manually, and click Retry to run the root script again
9.  Start the Oracle Database installation, and select Oracle ASM disk groups for Oracle Database files storage. For assistance during installation, click Help on the Oracle Universal Installer page where you need more information.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](install-configure-oracle-grid-infrastructure-standalone-server.md)
