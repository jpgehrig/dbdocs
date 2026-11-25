## Patching and Switching Oracle Grid Infrastructure Homes

Use `switchGridHome` command to switch from the current Oracle Grid Infrastructure home to the patched Oracle Grid Infrastructure home.

You can use the `switchGridHome` command only to switch between different RUs of the same release.

1.  Download the Oracle Database Release Update (RU) that you want to apply from My Oracle Support.
2.  As the `grid` user, download the Oracle Grid Infrastructure image files and extract the files into a new Oracle Grid Infrastructure home directory.
        $ mkdir -p /u01/app/19.17.0/grid
        $ chown grid:oinstall /u01/app/19.17.0/grid
        $ cd /u01/app/19.17.0/grid
        $ unzip -q download_location/grid.zip

    **Note:**

    The new Oracle Grid Infrastructure home path must be different from the current Oracle Grid Infrastructure home path.
3.  Download and install the latest OPatch version.
    For more information, see [My Oracle Support note 274526.1](https://support.oracle.com/rs?type=doc&id=274526.1).
4.  Start the Oracle Grid Infrastructure installer with the `-switchGridHome` flag to switch to the patched Oracle Grid Infrastructure home after the installation and the optional `-applyRU` flag to apply Release Updates (RUs) during the installation.
        $ /u01/app/19.17.0/grid/gridSetup.sh -switchGridHome [-applyRU patch_directory_location]
        [-applyOneOffs comma_seperated_list_of_patch_directory_locations]
5.  Follow the steps in the configuration wizard to complete the Oracle Grid Infrastructure installation. During configuration, select the option to Automatically run configuration scripts.
    All Oracle Grid Infrastructure services start running from the new Grid home after the installation is complete.
6.  Verify that the patching has completed.
        $ crsctl query crs activeversion -f
        Oracle Clusterware active version on the cluster is [19.0.0.0.0]. The cluster upgrade state is [NORMAL].
        The cluster active patch level is [patch_level].
7.  If the patching fails, then perform the following steps to rollback the patch:
    1.  As the `root` user, run the prepatch script.
            # /u01/app/19.17.0/grid/crs/install/rootcrs.sh -prepatch -dstcrshome Old_GI_Home -rollback
    2.  As the `root` user, run the postpatch script.
            # /u01/app/19.17.0/grid/crs/install/rootcrs.sh -postpatch -dstcrshome Old_GI_Home -rollback
8.  If you have successfully switched to the new Grid home on all nodes and want to switch back to the old Grid home, then perform the following steps:
    1.  As the `root` user, unlock the old Grid home.
            # Old_GI_Home/crs/install/rootcrs.sh -unlock -crshome Old_GI_Home
    2.  As the `grid` user, run `switchGridHome` from the old Grid home.
            $ Old_GI_Home/gridSetup.sh -silent -switchGridHome [-zeroDowntimeGIPatching] [-skipDriverUpdate]

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
