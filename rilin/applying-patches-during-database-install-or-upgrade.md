## Applying Patches During an Oracle Database Installation or Upgrade

Starting with Oracle Database 18c, you can download and apply Release Updates (RUs) during an Oracle Database installation or upgrade.

1.  Download the patches you want to apply from My Oracle Support:
    <https://support.oracle.com>
2.  Select the Patches and Updates tab to locate the patch.
    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software.
3.  Move the patches to an accessible directory like `/tmp`.
4.  Change to the Oracle Database home directory:
        $ cd $ORACLE_HOME
5.  Apply Release Updates (RUs) during the installation or upgrade process:
        $ ./runInstaller -applyRU patch_directory_location
6.  Complete the remaining steps in the Oracle Database configuration wizard to complete the installation or upgrade.

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node Databases](running-oracle-universal-installer-to-install-oracle-database.md)
