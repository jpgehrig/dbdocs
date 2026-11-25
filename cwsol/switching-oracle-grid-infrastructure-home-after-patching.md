Use `switchGridHome` command to switch from the current Oracle Grid Infrastructure home to the patched Oracle Grid Infrastructure home.

You can use the `switchGridHome` command only to switch between different RUs of the same release.

1.  Download the Oracle Database Release Update (RU) that you want to apply from My Oracle Support.
2.  As the `grid` user, download the Oracle Grid Infrastructure image files and extract the files into a new Oracle Grid Infrastructure home directory.
        $ mkdir -p /u01/app/19.11.0/grid
        $ chown grid:oinstall /u01/app/19.11.0/grid
        $ cd /u01/app/19.11.0/grid
        $ unzip -q download_location/grid.zip

    **Note:**

    The new Oracle Grid Infrastructure home path must be different from the current Oracle Grid Infrastructure home path.
3.  Start the Oracle Grid Infrastructure installer with the `-switchGridHome` flag to switch to the patched Oracle Grid Infrastructure home after the installation and the optional `-applyRU` flag to apply Release Updates (RUs) during the installation.
        $ /u01/app/19.11.0/grid/gridSetup.sh -switchGridHome [-applyRU patch_directory_location]
        [-applyOneOffs comma_seperated_list_of_patch_directory_locations]
4.  Follow the steps in the configuration wizard to complete the Oracle Grid Infrastructure installation.
    All Oracle Grid Infrastructure services start running from the new Grid home after the installation is complete.
5.  If the patching fails, then perform the following steps to rollback the patch:
    1.  As the `root` user, run the prepatch script.
            # /u01/app/19.11.0/grid/crs/install/rootcrs.sh -prepatch -dstcrshome Old_GI_Home -rollback
    2.  As the `root` user, run the postpatch script.
            # /u01/app/19.11.0/grid/crs/install/rootcrs.sh -postpatch -dstcrshome Old_GI_Home -rollback

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
