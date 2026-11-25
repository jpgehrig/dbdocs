## Downgrading Oracle Grid Infrastructure to 12c Release 2 (12.2) when Upgrade Fails

If upgrade of Oracle Grid Infrastructure fails before CVU post upgrade checks succeed, then you can run `setup.exe` and downgrade Oracle Grid Infrastructure to the earlier release.

Run this procedure to downgrade Oracle Clusterware only when the upgrade fails before CVU post upgrade checks succeed:

1.  From the later release Grid home, run `setup.exe` in silent mode, to downgrade Oracle Clusterware:
        C:\> C:\app\19.0.0\grid\setup.exe -silent –downgrade

    On UNIX systems, run `gridSetup.sh` instead of `setup.exe`.

**Note:**

- You can downgrade the cluster nodes in any sequence.

- Ensure that the user who performs the downgrade procedure is the same user who performed the upgrade procedure, and belongs to the same user groups, `ORA_ASMDBA` and `ORA_ASMADMIN`.

[Downgrading Oracle Standalone Cluster to 12c Release 2 (12.2)](downgrading-oracle-standalone-cluster-to-12c-release-2-12-2.md)

[Downgrading to Oracle Grid Infrastructure 12c Release 1 (12.1.0.2)](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)

**Parent topic:** [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12c-release-2-12-2.md)
