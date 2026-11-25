If upgrade of Oracle Grid Infrastructure fails before CVU post upgrade checks succeed, then you can run `gridSetup.sh` and downgrade Oracle Grid Infrastructure to the earlier release.

Run this procedure to downgrade Oracle Clusterware only when the upgrade fails before CVU post upgrade checks succeed.

1.  From the later release Grid home, run `gridSetup.sh` in silent mode, to downgrade Oracle Clusterware:
        $ /u01/app/19.0.0/grid/gridSetup.sh -silent –downgrade [–nodes] nodes_to_be_downgraded
        [-oldHome] previous_release_grid_home_to_downgrade_to
        [–configmethod] root | sudo [–sudopath path_to_sudo_program]
        [-sudousername sudoer_name]

    On Windows systems, run `setup.exe` instead of `gridSetup.sh`.

**Note:**

You can downgrade the cluster nodes in any sequence.

**Related Topics**

- [Downgrading Oracle Domain Services Cluster to 12c Release 2 (12.2)](downgrading-oracle-domain-services-cluster-to-12c-release-2.md)

**Parent topic:** [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12c-release2.md)
