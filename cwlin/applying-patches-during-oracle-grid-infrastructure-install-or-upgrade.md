## Applying Patches During an Oracle Grid Infrastructure Installation or Upgrade

Starting with Oracle Grid Infrastructure 18c, you can download and apply Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.

1.  Download the patches you want to apply from My Oracle Support:
    <https://support.oracle.com>
2.  Select the Patches and Updates tab to locate the patch.
    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software.
3.  Move the patches to an accessible directory like `/tmp`.
4.  Change to the Oracle Grid Infrastructure home directory:
        $ cd /u01/app/19.0.0/grid
5.  Apply Release Updates (RUs) and any one-off patches during the installation or upgrade process:
        $ ./gridSetup.sh -applyRU patch_directory_location -applyOneOffs comma_seperated_list_of_patch_directory_locations

    **Note:**

    You can apply RUs and one-off patches separately or together in the same command.
6.  Complete the remaining steps in the Oracle Grid Infrastructure configuration wizard to complete the installation or upgrade.

**Related Topics**

- [Oracle Grid Infrastructure Upgrading Oracle Restart for Linux and Unix-Based Operating Systems](../upgor/preface.md)

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
