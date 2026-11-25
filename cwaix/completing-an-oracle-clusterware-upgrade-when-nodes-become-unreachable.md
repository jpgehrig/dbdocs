If some nodes become unreachable in the middle of an upgrade, then you cannot complete the upgrade, because the upgrade script (`rootupgrade.sh`) did not run on the unreachable nodes. Because the upgrade is incomplete, Oracle Clusterware remains in the previous release.

You can confirm that the upgrade is incomplete by entering the command `crsctl query crs activeversion`.

To resolve this problem, run the `rootupgrade.sh` command with the `-force` flag using the following syntax:

Grid_home`/rootupgrade -force`

For example:

    # /u01/app/19.0.0/grid/rootupgrade -force

This command forces the upgrade to complete. Verify that the upgrade has completed by using the command` crsctl query crs activeversion`. The active release should be the upgrade release.

The force cluster upgrade has the following limitations:

- All active nodes must be upgraded to the newer release.

- All inactive nodes (accessible or inaccessible) may be either upgraded or not upgraded.

- For inaccessible nodes, after patch set upgrades, you can delete the node from the cluster. If the node becomes accessible later, and the patch version upgrade path is supported, then you can upgrade it to the new patch version.

**Parent topic:** [Performing Rolling Upgrade of Oracle Grid Infrastructure](performing-rolling-upgrade-of-oracle-grid-infrastructure.md)
