## Applying Patches Using Zero-Downtime Oracle Grid Infrastructure Patching

Starting with Oracle Database 19c Release Update (RU) 19.16, you can keep your Oracle RAC database instances running and accessible to the database users during Oracle Grid Infrastructure patching.

Use the `switchGridHome` command to switch from the current Oracle Grid Infrastructure home to the patched Oracle Grid Infrastructure home. Refer My Oracle Support note 2635015.1 for more information about zero-downtime Oracle Grid Infrastructure 19c patching. You can use the `switchGridHome` command only to switch between different RUs of the same release.

**Note:**

You can use zero-downtime patching only for out-of-place patching of Oracle Grid Infrastructure 19c Release Update (RU) 19.16 or later releases with Oracle RAC or Oracle RAC One Node databases of 19c or later releases. If your Oracle RAC or Oracle RAC One Node database release is older than 19c, then the database instances stop during zero-downtime patching.

1.  Download the Oracle Database Release Update (RU) 19.16 or later from My Oracle Support.
2.  As the `grid` user, download the Oracle Grid Infrastructure 19c image files and extract the files into a new Oracle Grid Infrastructure home directory.
        $ mkdir -p /u01/app/19.17.0/grid
        $ chown grid:oinstall /u01/app/19.17.0/grid
        $ cd /u01/app/19.17.0/grid
        $ unzip -q download_location/grid.zip

    **Note:**

    The new Oracle Grid Infrastructure home path must be different from the current Oracle Grid Infrastructure home path.
3.  Start the Oracle Grid Infrastructure installer with the `-switchGridHome` flag to switch to the patched Oracle Grid Infrastructure home after the installation.
        $ /u01/app/19.17.0/grid/gridSetup.sh -switchGridHome
        [-applyRU patch_directory_location] [-applyOneOffs comma_seperated_list_of_patch_directory_locations]
4.  Follow the steps in the configuration wizard to complete the Oracle Grid Infrastructure installation.
    During configuration, do not select the option to Automatically run configuration scripts.
5.  When prompted, run the `root.sh` script with the `-transparent` and `-nodriverupdate` flags on the first node.
6.  Run the `root.sh` script with the `-transparent` and `-nodriverupdate` flags on all other nodes.
    All Oracle Grid Infrastructure services start running from the new Grid home after the installation is complete.
7.  Verify that the patching has completed.
        $ crsctl query crs activeversion -f
        Oracle Clusterware active version on the cluster is [19.0.0.0.0]. The cluster upgrade state is [NORMAL].
        The cluster active patch level is [patch_level].
8.  If the patching fails, then perform the following steps to rollback the patch:
    1.  As the `root` user, run the prepatch script.
            # /u01/app/19.17.0/grid/crs/install/rootcrs.sh -prepatch -dstcrshome Old_GI_Home
            -nodriverupdate -transparent -rollback
    2.  As the `root` user, run the postpatch script.
            # /u01/app/19.17.0/grid/crs/install/rootcrs.sh -postpatch -dstcrshome Old_GI_Home
            -nodriverupdate -transparent -rollback
9.  If you have successfully switched to the new Grid home on all nodes and want to switch back to the old Grid home, then perform the following steps:
    1.  As the `root` user, unlock the old Grid home.
            # Old_GI_Home/crs/install/rootcrs.sh -unlock -crshome Old_GI_Home
    2.  As the `grid` user, run `switchGridHome` from the old Grid home.
            $ Old_GI_Home/gridSetup.sh -silent -switchGridHome [-zeroDowntimeGIPatching] [-skipDriverUpdate]

**Related Topics**

- [Zero-Downtime Grid Infrastucture Patching Using Oracle FPP](../fppad/zero-downtime-grid-patching.md)

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
