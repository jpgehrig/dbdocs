## Configuring the Software Binaries for Oracle Grid Infrastructure for a Cluster

Configure the software binaries by starting Oracle Grid Infrastructure configuration wizard in GUI mode.

After you have installed the Oracle Grid Infrastructure software on at least the local node, you can configure Oracle Grid Infrastructure on all the nodes in your cluster.

1.  Log in to one of the cluster nodes as the Oracle Installation user, and change directory to `Grid_home`.
2.  Start the Oracle Grid Infrastructure configuration wizard:
        C:\Grid_home> setup.exe

    The configuration script starts Oracle Universal Installer in Configuration Wizard mode.
3.  Provide information as needed for configuration.
    The configuration wizard mode validates the information and configures the installation on all cluster nodes.
4.  Verify that the summary has the correct information for your cluster, and click Install to start configuration of the local node.
    When you complete providing information, OUI shows you the Summary page, listing the information you have provided for the cluster.
    When configuration of the local node is complete, OUI copies the Oracle Grid Infrastructure configuration file to other cluster member nodes.
5.  Once all the `root` scripts are run, OUI checks the cluster configuration status, and starts other configuration tools as needed.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cloning-oracle-clusterware.md)

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
