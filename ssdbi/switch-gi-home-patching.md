Perform an out-of-place Oracle Restart patching by switching from the current Oracle Grid Infrastructure home to a patched Oracle Grid Infrastructure home.

1.  Download the 19.3 Oracle Grid Infrastructure base release image files.
    <https://www.oracle.com/database/technologies/oracle-database-software-downloads.html#19c>
2.  As the `grid` user, extract the downloaded image files into a new Oracle Grid Infrastructure home directory.
        $ mkdir -p /u01/app/oracle/product/19.17.0/grid
        $ chown grid:oinstall /u01/app/oracle/product/19.17.0/grid
        $ cd /u01/app/oracle/product/19.17.0/grid
        $ unzip -q download_location/grid.zip

    Here:
    - `/u01/app/oracle/product/19.17.0/grid` is the new Grid home.
    - `/u01/app/oracle/product/19.16.0/grid` is the old Grid home.
3.  As the `grid` user, download and install the latest version of the OPatch utility in the new Grid home.
    <https://updates.oracle.com/download/6880880.html>

        $ mv /u01/app/oracle/product/19.17.0/grid/OPatch /u01/app/oracle/product/19.17.0/grid/bak_OPatch
        $ unzip latest_Opatch.zip -d /u01/app/oracle/product/19.17.0/grid/
4.  Download the Oracle Database RU version that you want to apply from [My Oracle Support](https://support.oracle.com). In this example, Oracle Database 19.17 RU.
    For more information, see, [Downloading Release Update Patches](downloading-and-installing-patch-updates.md)
5.  Start the Oracle Grid Infrastructure installer to perform a software-only Oracle Restart installation. You can apply the optional `-applyRU` or `-applyOneOff` flags to apply Release Updates (RUs) during the installation.
         $ /u01/app/oracle/product/19.17.0/grid/gridSetup.sh [-applyRU patch_directory_location]
        [-applyOneOffs comma_separated_list_of_patch_directory_locations]
6.  Follow the steps in the configuration wizard to complete the Oracle Grid Infrastructure installation.
7.  As the `root` user, run the following command to prepare the new home for the out-of-place patching:
        # /u01/app/oracle/product/19.17.0/grid/crs/install/roothas.sh -prepatch -dstcrshome
        /u01/app/oracle/product/19.17.0/grid

    This command does not shut down any services.
8.  Run the following command to switch to the new Oracle Grid Infrastructure home and perform the out of place patching:
        # /u01/app/oracle/product/19.17.0/grid/crs/install/roothas.sh -postpatch -dstcrshome
        /u01/app/oracle/product/19.17.0/grid

    This command shuts down the old Oracle Grid Infrastructure home and starts resources from the new Oracle Grid Infrastructure home. All Oracle Grid Infrastructure services start running from the new Grid home.
9.  Update the Oracle central inventory (oraInventory).
        $ /u01/app/oracle/product/19.17.0/grid/oui/bin/runInstaller -updateNodeList ORACLE_HOME=/u01/app/oracle/product/19.17.0/grid CRS=TRUE
        $ /u01/app/oracle/product/19.16.0/grid/oui/bin/runInstaller -updateNodeList ORACLE_HOME=/u01/app/oracle/product/19.16.0/grid CRS=FALSE
10. If the patching fails, then perform the following steps to rollback the patch:
    1.  As the `root` user, run the `prepatch` script.
            # /u01/app/oracle/product/19.17.0/grid/crs/install/roothas.sh -prepatch -dstcrshome Old_GI_Home -rollback
    2.  As the `root` user, run the `postpatch` script.
            # /u01/app/oracle/product/19.17.0/grid/crs/install/roothas.sh -postpatch -dstcrshome Old_GI_Home -rollback
11. If you have successfully switched to the new Grid home on all nodes and want to switch back to the old Grid home, then perform the following steps:
    1.  As the `root` user, run the `prepatch` script.
            # Old_GI_Home/crs/install/roothas.sh -prepatch -dstcrshome Old_GI_Home
    2.  As the `grid` user, run the `postpatch` script.
            # Old_GI_Home/crs/install/roothas.sh -postpatch -dstcrshome Old_GI_Home
    3.  Update the Oracle central inventory (oraInventory).
            $ /u01/app/oracle/product/19.16.0/grid/oui/bin/runInstaller -updateNodeList ORACLE_HOME=/u01/app/oracle/product/19.16.0/grid CRS=TRUE
            $ /u01/app/oracle/product/19.17.0/grid/oui/bin/runInstaller -updateNodeList ORACLE_HOME=/u01/app/oracle/product/19.17.0/grid CRS=FALSE

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
