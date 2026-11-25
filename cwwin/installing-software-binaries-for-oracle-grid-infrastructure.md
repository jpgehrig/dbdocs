## Installing Software Binaries for Oracle Grid Infrastructure for a Cluster

If you use the Set Up Software Only option during installation, then Oracle Universal Installer (OUI) installs the software binaries on multiple nodes. You can then perform the additional steps of configuring Oracle Clusterware and Oracle ASM.

You can install Oracle Grid Infrastructure for a cluster software on multiple nodes at a time:

1.  Log in to Windows as the installation user for Oracle Grid Infrastructure, which must be a member of the Administrators users group.
2.  Create the Grid home directory.
    For example:

        mkdir C:\app\19.0.0\grid

    Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations.
3.  Download the Oracle Grid Infrastructure image files and copy the files to the Grid home.
    For example:

        cd C:\app\19.0.0\grid
        unzip -q download_location\grid_home.zip

    Unzip the installation image files only in the newly created Grid home directory.

    **Note:**

    Download and copy the Oracle Grid Infrastructure image files to the local node only. During installation, the software is copied and installed on all other nodes in the cluster.
4.  Run the `gridSetup.bat` command from the newly created Grid home directory, and select the Configuration Option as Set Up Software Only.
5.  Complete installation of Oracle Grid Infrastructure software on one or more nodes by providing information in the installer screens in response to your configuration selection. You can install Oracle Grid Infrastructure software on multiple nodes at a time.
6.  When the software is configured, run the `orainstRoot.bat` script on all nodes, if prompted.
7.  Ensure that you have completed all storage and server preinstallation requirements.
8.  Verify that all of the cluster nodes meet the installation requirements.
    Use the command:

        runcluvfy.bat stage -pre crsinst -n node_list
9.  Configure the cluster using the Oracle Universal Installer (OUI) configuration wizard or configure the cluster using a response file.

[Configuring the Software Binaries for Oracle Grid Infrastructure for a Cluster](configuring-software-binaries-for-oracle-grid-infrastructure.md)

[Configuring the Software Binaries Using a Response File](configuring-the-software-binaries-using-a-response-file.md)

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
