This chapter describes how to keep your Oracle Database software up-to-date. It contains the following sections:

- About Software Management and Patch Releases

- Upgrading a Database

- Removing Oracle Database Software

- Managing Oracle Database Software: Oracle by Example Series

### 14.1 About Software Management and Patch Releases

Software management involves keeping your Oracle Database software up-to-date with the latest product fixes. When a product defect, or a bug, is discovered, a patch is created to fix the problem. A patch corrects a single defect in the installed software. Individual patches, also referred to as interim patches, are made available to customers who for business reasons cannot wait until the next patch set to receive the product fix.

Oracle periodically issues maintenance releases for its software, in the form of patch sets. A patch set is a collection of product fixes that have been released up to the time of the maintenance release. Patch sets are fully tested and integrated product fixes. All the product fixes in the patch set have been tested and are certified to work with each other.

Every patch or patch set is associated with a bug number for identification purposes. Patch sets are also associated with version numbers. For example, if you use Oracle Database 12c Release 1 (12.1.0.1), then an available patch set is 12.1.0.2. The version number of the patched software does not change if an interim patch is applied.

Every patch has an associated README file that describes how it fixes the software. The README file also has instructions for applying the patch.

Every patch set is accompanied by a Patch Set Notes file that contains installation instructions and information about the product fixes contained within the patch set. When you apply a patch set to your Oracle software, you change the maintenance release number for your installed software. Applying a patch set affects the software residing in your Oracle home only, with no change to the data in the database.

You can use Oracle OPatch and Oracle Universal Installer (OUI) to apply patches and patch sets respectively. Alternatively, you can automate the application of these patches using Oracle Enterprise Manager Cloud Control. Use of these products is beyond the scope of this documentation.

### 14.2 Upgrading a Database

Oracle provides upgrade options and strategies that are designed for your database environment, and an array of tools that automate the Oracle Database upgrade process.

**See:**

[Oracle Database Upgrade Guide](../upgrd/index.md) for information about these topics:

- Upgrade tools and processes

- Preparing to upgrade Oracle Database

- Steps for upgrading Oracle Database

- Post-upgrade tasks for Oracle Database

- Upgrading applications after upgrading Oracle Database

- Downgrading Oracle Database to an earlier release

- Migrating data

### 14.3 Removing Oracle Database Software

If you want to remove an Oracle software installation, you can use the deinstallation tool to completely uninstall the software from your computer.

Starting with Oracle Database 12c, the deinstallation tool is integrated with the database installation media. You can run the deinstallation tool using the `runInstaller` command with the `-deinstall` and `-home` options from the base directory of the Oracle Database, Oracle Database Client or Oracle Grid Infrastructure installation media.

The deinstallation Tool (`deinstall`) is also available in Oracle home directories after installation as `$ORACLE_HOME/deinstall/deinstall`.

The default method for running the deinstallation tool is from the `deinstall` directory in the Oracle home as the installation owner:

#### To remove an Oracle home from your computer:

1.  Execute the deinstallation tool using these commands:
        $ cd $ORACLE_HOME
        $ $ORACLE_HOME/deinstall/deinstall

    **Note:**

    Do not shut down the Oracle database or stop any database processes before running the deinstallation tool.
2.  Enter the specified information at the prompts, or just press Enter to accept the default values.
3.  When prompted, follow the directions to run the root script. You must be the `root` user to do so.

**See Also:**

[Oracle Database Installation Guide](../install-and-upgrade.md) for your platform for more information about the deinstallation tool

### 14.4 Managing Oracle Database Software: Oracle by Example Series

Oracle By Example (OBE) has a series on the Oracle Database 2 Day DBA guide. This OBE series steps you through the tasks in this chapter, and includes annotated screenshots.

The series consists of a tutorial which explains how to remove Oracle Database software. The tutorial can be accessed in two ways:

- [Manage Oracle Database Software Series](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_obe_software)

- [Manage Oracle Database Software](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_lp_software)
