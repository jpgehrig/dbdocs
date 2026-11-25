## Installing Software Binaries for Oracle Grid Infrastructure for a Cluster

You can install Oracle Grid Infrastructure software binaries for a cluster software on multiple nodes at a time.

Use this procedure to install Oracle Grid Infrastructure for a cluster software:

1.  Download the Grid home image files.
2.  Run the `gridSetup.sh` command and select the Configuration Option as Set Up Software Only.
    **Note:**

    You can use the `gridSetup.sh` command with the `-applyRU` and `-applyOneOffs` flags to install Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.
3.  Complete installation of Oracle Grid Infrastructure software on one or more nodes by providing information in the installer screens in response to your configuration selection. You can install Oracle Grid Infrastructure software on multiple nodes at a time.
4.  When the software is configured, run the `orainstRoot.sh` script on all nodes, when prompted.
5.  On all nodes, the `root.sh` script output provides information about how to proceed, depending on the configuration you plan to complete in this installation. Make note of this information.
6.  Ensure that you have completed all storage and server preinstallation requirements.
7.  Verify that all of the cluster nodes meet the installation requirements:
        runcluvfy.sh stage -pre crsinst -n node_list
8.  Configure the cluster using the Oracle Universal Installer (OUI) configuration wizard or response files.

**Related Topics**

- [Configuring Software Binaries for Oracle Grid Infrastructure for a Cluster](configuring-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
- [Configuring the Software Binaries Using a Response File](configuring-the-software-binaries-using-a-response-file.md)
- [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-new-cluster.md)
- [Applying Patches During an Oracle Grid Infrastructure Installation or Upgrade](applying-patches-during-oracle-grid-infrastructure-install-or-upgrade.md)

**Parent topic:** [Installing Only the Oracle Grid Infrastructure Software](installing-only-the-oracle-grid-infrastructure-software.md)
