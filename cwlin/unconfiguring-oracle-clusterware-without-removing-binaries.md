## Unconfiguring Oracle Clusterware Without Removing Binaries

Running the `rootcrs.sh` command flags `-deconfig -force` enables you to unconfigure Oracle Clusterware on one or more nodes without removing installed binaries.

This feature is useful if you encounter an error on one or more cluster nodes during installation when running the `root.sh` command, such as a missing operating system package on one node. By running `rootcrs.sh -deconfig -force` on nodes where you encounter an installation error, you can unconfigure Oracle Clusterware on those nodes, correct the cause of the error, and then run `root.sh` again.

**Note:**

Stop any databases, services, and listeners that may be installed and running before deconfiguring Oracle Clusterware. In addition, dismount Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and disable Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM) volumes.

**Caution:**

Commands used in this section remove the Oracle Grid infrastructure installation for the entire cluster. If you want to remove the installation from an individual node, then see [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md).

To unconfigure Oracle Clusterware:

1.  Log in as the `root` user on a node where you encountered an error.

2.  Change directory to Grid_home/crs/install. For example:

        # cd /u01/app/19.0.0/grid/crs/install


3.  Run `rootcrs.sh` with the `-deconfig` and `-force` flags. For example:

        # ./rootcrs.sh -deconfig -force

    Repeat on other nodes as required.

4.  If you are deconfiguring Oracle Clusterware on all nodes in the cluster, then on the last node, enter the following command:

        # ./rootcrs.sh -deconfig -force -lastnode

    The `-lastnode` flag completes deconfiguration of the cluster, including the OCR and voting files.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
