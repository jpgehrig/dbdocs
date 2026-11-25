After installing Oracle Grid Infrastructure for a cluster (Oracle Clusterware and Oracle ASM configured for a cluster), if you need to change the Grid home path, then use the following example as a guide to detach the existing Grid home, and to attach a new Grid home.

**Note:**

Before changing the Grid home, you must shut down all executables that run in the Grid home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

1.  As the `root` user, copy the Oracle Grid Infrastructure binaries from the old Grid home location to the new Grid home location. For example, where the old Grid home is `/u01/app/19.0.0/grid` and the new Grid home is `/u01/app/19c/grid`.

        # mkdir /u01/app/19c/grid
        # cp -pR /u01/app/19.0.0/grid /u01/app/19c/grid

2.  Change the owner and group for the directory and files in the new Grid home.

        # chown -R grid:oinstall /u01/app/19c/grid

3.  As the `grid` user, run the `gridSetup.sh` command from the new Grid home directory and in the Select Configuration Option screen, select Setup Software Only.

        $ /u01/app/19c/grid/gridSetup.sh

    Complete the installation by selecting the installation options as prompted. This step relinks the Oracle Grid Infrastructure binaries and updates the Oracle Inventory (oraInventory) with the new Oracle Grid Infrastructure home.

    **Note:**

    Do not change the Oracle base path during the installation.

4.  As the `root` user, run the `root.sh` script from your new Grid home.

        # /u01/app/19c/grid/root.sh

5.  As the `grid` user, enable Oracle RAC, dNFS, and `ioracle` from the new Grid home.

        $ export ORACLE_HOME=/u01/app/19c/grid
        $ cd $ORACLE_HOME/rdbms/lib
        $ make -f ins_rdbms.mk dnfs_on rac_on ioracle ORACLE_HOME=$ORACLE_HOME

6.  As the `root` user, enter the following command to start up in the new home location.

        # cd Grid_home/crs/install
        # ./rootcrs.sh -move -dstcrshome Grid_home

7.  As the `grid` user, disable CRS from the old Grid home.

        $ Grid_home/oui/bin/runInstaller -updateNodeList -noClusterEnabled ORACLE_HOME=$ORACLE_HOME
        "CLUSTER_NODES={node1,node2}" CRS=false -doNotUpdateNodeList LOCAL_NODE=list_of_nodes

8.  Enable CRS from the new Grid home.

        $ Grid_home/oui/bin/runInstaller -updateNodeList -noClusterEnabled ORACLE_HOME=$ORACLE_HOME
        "CLUSTER_NODES={node1,node2}" CRS=true -doNotUpdateNodeList LOCAL_NODE=list_of_nodes

9.  Repeat steps 1 through 8 on each cluster member node.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
