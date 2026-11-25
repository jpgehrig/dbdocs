These are the Oracle Universal Installer (OUI) bugs in Oracle Database 19c.

You should also review [Compatibility, Upgrading, Downgrading, and Installation](compat-upgrade-downgrade-install.md) for other issues related to installation and upgrades.

- Bug 18336219
- Bug 23006768
- Bug 27080535
- Bug 27120934

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 18336219

Oracle Database installer does not check if the password specified for `ASMSNMP` on the Specify Management Options screen is correct. If you proceed with the configuration and specify an incorrect password, then Oracle Enterprise Manager Cloud Control cannot discover details and monitor the Oracle ASM instance.

#### Workaround \#1:

Ensure that the correct password (the same password specified earlier during the Oracle Grid Infrastructure for a cluster installation) is specified in the Specify Management Options screen of Oracle Database installer.

#### Workaround \#2:

On the Oracle Enterprise Manager Cloud Control portal, navigate to the Oracle ASM credentials screen and update the password for `ASMSNMP`. Once the password is saved on Oracle Enterprise Manager Cloud Control, the Oracle ASM monitoring starts working.

**Parent topic:** Oracle Universal Installer Known Bugs

### Bug 23006768

When installing an Oracle RAC database on an Oracle Member Cluster for Database that is configured to use an Oracle ASM service of an Oracle Domain Services Cluster (DSC) and, if the network selected for `ASM` or `ASM & Private` usage is not of the same type as the Oracle ASM network of the DSC, then the database instance terminates with the following error:

    IOS hit ORA-00600: internal error code, arguments: [kfias_creg!net]

#### Workaround:

During the installation of the Oracle Member Cluster for Database, choose the network interface for `ASM` or `ASM & Private` so that it is on the same network as the Oracle ASM network of the DSC.

**Parent topic:** Oracle Universal Installer Known Bugs

### Bug 27080535

When deinstalling the Oracle Grid Infrastructure for a standalone server home with an Oracle Management Server configuration, the `emConfig.txt` file in `ORACLE_BASE/admin/emca` is not deleted.

#### Workaround:

To remove the `emConfig.txt` file, run the following command:

    rm -rf $ORACLE_BASE/admin/emca/emConfig.txt

During the last `ORACLE_HOME` deinstallation, to remove `ORACLE_BASE`, run the following command after the deinstallation tool exits:

    rm -rf $ORACLE_BASE

**Parent topic:** Oracle Universal Installer Known Bugs

### Bug 27120934

After downgrading Oracle Clusterware using the Grid Setup Wizard, from Oracle Database 19c to Oracle Clusterware release 12.1 or release 11.2, the unused data files of the Oracle Grid Infrastructure Management Repository (GIMR) of the 19c Oracle Grid Infrastructure home could still be present in the disk group.

#### Workaround:

Before starting the downgrade procedure using the Grid Setup Wizard, delete the GIMR database using the following command:

    <Active_GI_HOME>/bin/dbca -silent -deleteDatabase -sourceDB -MGMTDB

**Parent topic:** Oracle Universal Installer Known Bugs
