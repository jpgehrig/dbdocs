## Completing an Oracle Clusterware Upgrade when Nodes Become Unreachable

If some nodes become unreachable in the middle of an upgrade, then you cannot complete the upgrade without user intervention.

Because the upgrade did not complete successfully on the unreachable nodes, the upgrade is incomplete. Oracle Clusterware remains in the earlier release.

1.  Confirm that the upgrade is incomplete by entering the following command:
        crsctl query crs activeversion
2.  To resolve the incomplete upgrade, run the `gridConfig.bat —upgrade` command with the `-force` option on any of the nodes where the `gridConfig.bat` script has already completed as follows:
        Grid_home\crs\config\gridConfig.bat -upgrade -force

    For example, as the Oracle Installation User for Oracle Grid Infrastructure, run the following command:

        C:\> C:\app\12.2.0\grid\crs\config\gridConfig.bat -upgrade -force

    The force cluster upgrade has the following limitations:

    - All active nodes must be upgraded to the newer release

    - All inactive nodes (accessible or inaccessible) may be either upgraded or not upgraded

    - For inaccessible nodes, after patch set upgrades, you can delete the node from the cluster. If the node becomes accessible later, and the patch version upgrade path is supported, then you can upgrade it to the new patch version.

    This command forces the upgrade to complete.
3.  Verify that the upgrade has completed by using the command `crsctl query crs activeversion`.
    The active release should be the upgrade release.

**Parent topic:** [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)
