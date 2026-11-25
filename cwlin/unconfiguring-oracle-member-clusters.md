## Unconfiguring Oracle Member Cluster

Run this procedure to unconfigure Oracle Member Cluster.

1.  Run the deinstall tool to unconfigure Oracle Member Cluster:
        Grid_home/deinstall/deinstall.sh
2.  Complete the deinstallation by running the root script on all the nodes when prompted.
        # rootcrs.sh -deconfig
3.  Delete the Member Cluster Manifest File for the Oracle Member Cluster and stored on the Oracle Domain Services Cluster:
        crsctl delete member_cluster_configuration member_cluster_name

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-control-crsctl-utility-reference.md)

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
