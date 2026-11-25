## Configuring Software Binaries for Oracle Grid Infrastructure for a Cluster

Configure the software binaries by starting Oracle Grid Infrastructure configuration wizard in GUI mode.

1.  Log in on a cluster node as the Oracle Grid Infrastructure installation owner, and change directory to `Grid_home`.
2.  Start the Oracle Grid Infrastructure configuration wizard:
        $ ./gridSetup.sh
3.   Provide information as needed for configuration. OUI validates the information and configures the installation on all cluster nodes.
4.  When you complete providing information, OUI shows you the Summary page, listing the information you have provided for the cluster. Verify that the summary has the correct information for your cluster, and click Install to start configuration of the local node.
    When configuration of the local node is complete, OUI copies the Oracle Grid Infrastructure configuration file to other cluster member nodes.
5.  When prompted, run `root` scripts.
6.  When you confirm that all `root` scripts are run, OUI checks the cluster configuration status, and starts other configuration tools as needed.

**Parent topic:** [Installing Only the Oracle Grid Infrastructure Software](installing-only-the-oracle-grid-infrastructure-software.md)
