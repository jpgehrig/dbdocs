If the Oracle Clusterware stack does not start because of any error, then you can patch Oracle Grid Infrastructure using the OPatch utility.

1.  Download patches you want to apply from My Oracle Support:
    <https://support.oracle.com>
    Select the Patches and Updates tab to locate the patch.

    Oracle recommends that you select Recommended Patch Advisor, and enter the product group, release, and platform for your software. My Oracle Support provides you with a list of the most recent Release Updates (RUs) and Release Update Revisions (RURs).

    Place the patches in an accessible directory, such as `/tmp`.
2.  Review the patch documentation for the patch you want to apply, and complete all required steps before starting the patch upgrade.
3.  As the `root` user, stop the Oracle Clusterware stack on the first node.
        # $ORACLE_HOME/bin/crsctl stop crs
4.  Unlock the Oracle Grid Infrastructure home on the first node.
        # $ORACLE_HOME/crs/install/rootcrs.sh -unlock
5.  As the `grid` user, follow the instructions in the patch documentation to apply the patch on the first node.
        $ $ORACLE_HOME/OPatch/opatch apply patch_directory_location/patch_ID

    Wait for the patching to finish on the first node before patching other cluster nodes.
6.  As the `root` user, lock the Oracle Grid Infrastructure home on the first node.
        # $ORACLE_HOME/rdbms/install/rootadd_rdbms.sh
        # $ORACLE_HOME/crs/install/rootcrs.sh -lock
7.  Update Oracle Local Registry (OLR) to the patch level on the first node.
        # $ORACLE_HOME/bin/clscfg -localpatch
8.  Start the Oracle Clusterware stack on the first node.
        # $ORACLE_HOME/bin/crsctl start crs
9.  Update Oracle Cluster Registry (OCR) to the patch level on the first node.
        # $ORACLE_HOME/bin/clscfg -patch
10. Repeat steps 3 through 9 on all other cluster nodes.
    You can patch all other cluster nodes in parallel.

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
