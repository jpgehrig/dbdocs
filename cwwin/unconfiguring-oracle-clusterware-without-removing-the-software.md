## Unconfiguring Oracle Clusterware Without Removing the Software

By running `rootcrs.bat -deconfig -force` on nodes where you encounter an installation error, you can unconfigure Oracle Clusterware on those nodes, correct the cause of the error, and then run `rootcrs.bat` again to reconfigure Oracle Clusterware.

Running the `rootcrs.bat` command with the options `-deconfig -force` enables you to unconfigure Oracle Clusterware on one or more nodes without removing the installed software. This feature is useful if you encounter an error on one or more cluster nodes during installation, such as incorrectly configured shared storage.

Before unconfiguring Oracle Clusterware you must:

- Stop any databases, services, and listeners that may be installed and running

- Dismount ACFS file systems

- Disable ADVM volumes

**Caution:**

Commands used in this section remove the Oracle Grid infrastructure installation for the entire cluster. To remove the installation from an individual node, refer to [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md).

1.  Log in using a member of the Administrators group on a node where you encountered an error during installation.
2.  Stop any databases, services, and listeners currently running from the Grid home.
3.  If present, unmount all Oracle Automatic Storage Management Cluster File System (Oracle ACFS) file systems.
4.  Change directory to `Grid_home``\crs\install`.
    For example:
        C:\> cd C:\app\19.0.0\grid\crs\install
5.  Run `rootcrs.bat` with the `-deconfig -force` options.
    For example:
        C:\..\install> rootcrs.bat -deconfig -force

    **Note:**

    The `-force` option must be specified when running the `rootcrs.bat` script if there exist running resources that depend on the resources started from the Oracle Clusterware home you are deleting, such as databases, services, or listeners. You must also use the `-force` option if you are removing a partial, or failed installation.
6.  Repeat Step 1 through Step 5 on other nodes as required.
7.  If you are unconfiguring Oracle Clusterware on all nodes in the cluster, then on the last node, enter the following command:
        C:\..\install> rootcrs.bat -deconfig -force -lastnode

    The `-lastnode` option completes the unconfiguring of the cluster, including the Oracle Cluster Registry (OCR) and voting files.
    **Caution:**

    Run the `rootcrs.bat -deconfig -force -lastnode` command on a cluster node.

**Parent topic:** [Modifying or Deinstalling Oracle Grid Infrastructure](modifying-or-deinstalling-oracle-grid-infrastructure.md)
