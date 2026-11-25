## Changing the Oracle Grid Infrastructure Home Path

After installing Oracle Grid Infrastructure for a cluster, you might need to change the location of the Grid home.

If you need to change the Grid home path, then use the following example as a guide to detach the existing Grid home, and to attach a new Grid home.

**Caution:**

Before changing the Grid home, you must shut down all executables that run in the Grid home directory that you are modifying. In addition, shut down all applications that use Oracle shared libraries.

1.  Login as an Administrator user or the Oracle Installation user for Oracle Grid Infrastructure (for example, `grid`).
2.  Change directory to `Grid_home``\bin` and enter the command `crsctl stop crs`. For example:
        C:\> cd app\19.0.0\grid\bin
        C:\..\BIN> crsctl stop crs
3.  Detach the existing Grid home.
    Run a command similar to the following command, where `C:\app\19.0.0\grid` is the existing Grid home location:
        C:\> cd app\19.0.0\grid\oui\bin
        C:\..\bin> setup.exe -silent -detachHome ORACLE_HOME=
        'C:\app\19.0.0\grid' -local
4.  Move the installed files for Oracle Grid Infrastructure from the old Grid home to the new Grid home.
    For example, if the old Grid home is `C:\app\19.0.0\grid` and the new Grid home is `D:\app\19c\grid`, use the following command:
        C:\> xcopy C:\app\19.0.0\grid D:\app\19c\grid /E /I /H /K
5.  Install Oracle Grid Infrastructure in the new home.
    For example:

        C:\> perl clone.pl ORACLE_BASE=C:\app\grid ORACLE_HOME=C:\app\19.0.0\grid
        ORACLE_HOME_NAME=OraHome1Grid ORACLE_HOME_USER=Oracle_home_user_name
        "LOCAL_NODE=node1" "CLUSTER_NODES={node1,node2}" CRS=TRUE

    When you navigate to the `Grid_home``\clone\bin` directory and run the `clone.pl` script, provide values for the input parameters that provide the path information for the new Grid home.
    **Note:**

    You cannot specify a different Oracle Home user when changing the Oracle Grid Infrastructure home path.
6.  Start Oracle Clusterware in the new home location.
        D:\> cd app\19c\grid\crs\install
        D:\..install\> rootcrs.bat -dstcrshome D:\app\19c\grid -move

    **WARNING:**

    While cloning, ensure that you do not change the Oracle home base, otherwise the move operation will fail.
7.  Repeat steps 1 through 6 on each cluster member node.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cloning-oracle-clusterware.md)

**Parent topic:** [Modifying or Deinstalling Oracle Grid Infrastructure](modifying-or-deinstalling-oracle-grid-infrastructure.md)
