## Installing Oracle Grid Infrastructure for a New Cluster

Complete this procedure to install Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM) on your cluster.

If you have any questions during installation, then click the Help button on the installer page.

You should have your network information, storage information, and operating system users and groups available to you before you start installation.

1.  Log in to Windows as the installation user for Oracle Grid Infrastructure, which must be a member of the Administrators users group.
2.  Create the Grid home directory.
    For example:

        mkdir C:\app\19.0.0\grid

    Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations.
3.  Download the Oracle Grid Infrastructure image files and copy the files to the Grid home.
    For example:

        cd C:\app\19.0.0\grid
        unzip -q download_location\grid_home.zip

    Unzip the installation image files only in this Grid home directory that you created.

    **Note:**

    Download and copy the Oracle Grid Infrastructure image files to the local node only. During installation, the software is copied and installed on all other nodes in the cluster.
4.  Start the Oracle Grid Infrastructure Setup Wizard by running the following command:
        Grid_home\setup.exe

    You can run this command from a Virtual Network Computing (VNC) session, or Terminal Services in console mode.
5.  Select one of the following configuration options:
    - Configure Oracle Grid Infrastructure for a Cluster

      Select this option to configure a new Oracle Flex Cluster deployment.

    - Configure Oracle Grid Infrastructure for a standalone server (Oracle Restart)

      Select this option to install Oracle Grid Infrastructure in an Oracle Restart configuration. Use this option for single servers supporting Oracle Database and other applications.

    - Upgrade Oracle Grid Infrastructure

      Select this option to upgrade Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM).

    - Set Up Software Only

      Select this option to configure Oracle Grid Infrastructure software and register the Oracle Grid Infrastructure home with the central inventory
6.  Choose the type of Oracle Flex Cluster from the following options:
    - Configure a Flex Cluster: Select this option to configure an Oracle Real Application Clusters deployment consisting of cluster member nodes.

    - Configure an Extended Cluster: Select this option to configure a type of Oracle Flex Cluster consisting of cluster nodes located in multiple geographically-separated locations called sites.

      Configure an Application Cluster: Select this option to configure an Oracle ASM client cluster that can run non-database applications. This cluster configuration enables high availability of any software application.
7.  Respond to the installation screens that appear in response to your configuration selection.
    Installation screens vary depending on the installation option you select.
    For cluster member node public and VIP network addresses, provide the information required depending on the kind of cluster you are configuring:

    - If you plan to use automatic cluster configuration with DHCP addresses configured and resolved through GNS, then you only need to provide the GNS VIP names as configured on your DNS.

    The following is a list of additional information about node IP addresses:

    - For the local node only, the installer automatically fills in public and VIP fields. If your system uses vendor clusterware, then the installer may fill additional fields.

    - Host names and virtual host names are not domain-qualified. If you provide a domain in the address field during installation, then the installer removes the domain from the address.

    - Interfaces identified as private for private IP addresses should not be accessible as public interfaces. Using public interfaces for Cache Fusion can cause performance problems.

    When you enter the public node name, use the primary host name of each node. In other words, use the name displayed by the `hostname` command.
8.  Provide information and run scripts as prompted by the installer.
    After the installation interview, you can click Details to see the log file.
9.  After you have specified all the information needed for installation, the installer installs the software on each node. The installer then runs Oracle Net Configuration Assistant (NETCA), Oracle Private Interconnect Configuration Assistant, and Cluster Verification Utility (CVU). These programs run without user intervention.
10. During the installation, Oracle Automatic Storage Management Configuration Assistant (`asmca`) configures Oracle ASM for storage.

When you have verified that your Oracle Grid Infrastructure installation has completed successfully, you can either use Oracle Clusterware and Oracle ASM to maintain high availability for other applications, or you can install Oracle Database and Oracle RAC software.

You can manage Oracle Grid Infrastructure and Oracle Automatic Storage Management (Oracle ASM) using Oracle Enterprise Manager Cloud Control. To register the Oracle Grid Infrastructure cluster with Oracle Enterprise Manager, ensure that Oracle Management Agent is installed and running on all nodes of the cluster.

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
