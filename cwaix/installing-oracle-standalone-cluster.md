Complete this procedure to install Oracle Grid Infrastructure software for Oracle Standalone Cluster.

1.  As the `grid` user, download the Oracle Grid Infrastructure image files and extract the files into the Grid home. For example:
        mkdir -p /u01/app/19.0.0/grid
        chown grid:oinstall /u01/app/19.0.0/grid
        cd /u01/app/19.0.0/grid
        unzip -q download_location/grid.zip

    `grid.zip` is the name of the Oracle Grid Infrastructure image zip file.

    **Note:**

    - You must extract the zip image software into the directory where you want your Grid home to be located.

    - Download and copy the Oracle Grid Infrastructure image files to the local node only. During installation, the software is copied and installed on all other nodes in the cluster.
2.  Log in as the `grid` user, and start the Oracle Grid Infrastructure installer by running the following command:
        /u01/app/19.0.0/grid/gridSetup.sh

    The installer starts and the Select Configuration Option window appears.
3.  Choose the option Configure Grid Infrastructure for a New Cluster, then click Next.
    The Select Cluster Configuration window appears.
4.  Choose the option Configure an Oracle Standalone Cluster, then click Next.
    Select the Configure as Extended Cluster option to extend an Oracle RAC cluster across two or more separate sites, each equipped with its own storage.
    The Grid Plug and Play Information window appears.
5.  In the Cluster Name and SCAN Name fields, enter the names for your cluster and cluster scan that are unique throughout your entire enterprise network.
    You can select Configure GNS if you have configured your domain name server (DNS) to send to the GNS virtual IP address name resolution requests for the subdomain GNS serves, as explained in this guide.

    For cluster member node public and VIP network addresses, provide the information required depending on the kind of cluster you are configuring:

    - If you plan to use automatic cluster configuration with DHCP addresses configured and resolved through GNS, then you only need to provide the GNS VIP names as configured on your DNS.

    - If you plan to use manual cluster configuration, with fixed IP addresses configured and resolved on your DNS, then provide the SCAN names for the cluster, and the public names, and VIP names for each cluster member node. For example, you can choose a name that is based on the node names' common prefix. The cluster name can be `mycluster` and the cluster SCAN name can be `mycluster-scan`.

    Click Next.
    The Cluster Node Information window appears.
6.  In the Public Hostname column of the table of cluster nodes, you should see your local node, for example `node1.example.com`.
    The following is a list of additional information about node IP addresses:

    - For the local node only, OUI automatically fills in public and VIP fields. If your system uses vendor clusterware, then OUI may fill additional fields.

    - Host names and virtual host names are not domain-qualified. If you provide a domain in the address field during installation, then OUI removes the domain from the address.

    - Interfaces identified as private for private IP addresses should not be accessible as public interfaces. Using public interfaces for Cache Fusion can cause performance problems.

    - When you enter the public node name, use the primary host name of each node. In other words, use the name displayed by the `/bin/hostname` command.

    1.  Click Add to add another node to the cluster.
    2.  Enter the second node's public name (`node2`), and virtual IP name (`node2-vip`), then click OK. Provide the virtual IP (VIP) host name for all cluster nodes, or none.
        You are returned to the Cluster Node Information window. You should now see all nodes listed in the table of cluster nodes.
    3.  Make sure all nodes are selected, then click the SSH Connectivity button at the bottom of the window.
        The bottom panel of the window displays the SSH Connectivity information.
    4.  Enter the operating system user name and password for the Oracle software owner (`grid`). If you have configured SSH connectivity between the nodes, then select the Reuse private and public keys existing in user home option. Click Setup.
        A message window appears, indicating that it might take several minutes to configure SSH connectivity between the nodes. After a short period, another message window appears indicating that passwordless SSH connectivity has been established between the cluster nodes. Click OK to continue.
    5.  When returned to the Cluster Node Information window, click Next to continue.

    The Specify Network Interface Usage window appears.
7.   Select the usage type for each network interface displayed.
    Verify that each interface has the correct interface type associated with it. If you have network interfaces that should not be used by Oracle Clusterware, then set the network interface type to Do Not Use. For example, if you have only two network interfaces, then set the public interface to have a Use for value of Public and set the private network interface to have a Use for value of ASM & Private.
    Click Next. The Storage Option Information window appears.
8.  Select storage option for Oracle Cluster Registry (OCR) and voting files:
    1.  Select Use Oracle Flex ASM for storage to store OCR and voting files on an Oracle ASM disk group.
    2.  Select Use Shared File System to store OCR and voting files on a shared file system, and then click Next. The Create Grid Infrastructure Management Repository Option window appears.
9.  Choose whether you want to create a Grid Infrastructure Management Repository for your Oracle Standalone Cluster installation, then click Next.
    If you choose Yes on this window, then the Grid Infrastructure Management Repository Option window appears. Otherwise, the Create ASM Disk Group window appears.
10. Choose whether you want to store the Grid Infrastructure Management Repository in a separate Oracle ASM disk group, then click Next.
    The Create ASM Disk Group window appears.
11. Provide the name and specifications for the Oracle ASM disk group.
    1.  In the Disk Group Name field, enter a name for the disk group, for example DATA.
    2.  Choose the Redundancy level for this disk group. Normal is the recommended option.
    3.  In the Add Disks section, choose the disks to add to this disk group.

    When you have finished providing the information for the disk group, click Next.
12. If you selected to use a different disk group for the GIMR, then the Grid Infrastructure Management Repository Option window appears. Provide the name and specifications for the GIMR disk group.
    1.  In the Disk Group Name field, enter a name for the disk group, for example DATA.
    2.  Choose the Redundancy level for this disk group. Normal is the recommended option.
    3.  In the Add Disks section, choose the disks to add to this disk group.

    When you have finished providing the information for the disk group, click Next.
    The Specify ASM Password window appears.
13. Choose the same password for the Oracle ASM SYS and ASMSNMP account, or specify different passwords for each account, then click Next.
    The Failure Isolation Support window appears.
14. Select the option Do not use Intelligent Platform Management Interface (IPMI), then click Next.
    The Specify Management Options window appears.
15. If you have Enterprise Manager Cloud Control installed in your enterprise, then choose the option Register with Enterprise Manager (EM) Cloud Control and provide the EM configuration information. If you do not have Enterprise Manager Cloud Control installed in your enterprise, then click Next to continue.
    The Privileged Operating System Groups window appears.
16. Accept the default operating system group names for Oracle ASM administration and click Next.
    The Specify Install Location window appears.
17. Specify the directory to use for the Oracle base for the Oracle Grid Infrastructure installation, then click Next. The Oracle base directory must be different from the Oracle home directory.
    If you copied the Oracle Grid Infrastructure installation files into the Oracle Grid home directory as directed in Step 1, then the default location for the Oracle base directory should display as `/u01/app/grid`.
    If you have not installed Oracle software previously on this computer, then the Create Inventory window appears.
18. Change the path for the inventory directory, if required. Then, click Next.
    If you are using the same directory names as the examples in this book, then it should show a value of `/u01/app/oraInventory`. The group name for the `oraInventory` directory should show `oinstall`.
    The Root Script Execution Configuration window appears.
19. Select the option to Automatically run configuration scripts. Enter the credentials for the root user or a sudo account, then click Next.
    Alternatively, you can Run the scripts manually as the `root` user at the end of the installation process when prompted by the installer.
    The Perform Prerequisite Checks window appears.
20. If any of the checks have a status of Failed and are not Fixable, then you must manually correct these issues. After you have fixed the issue, you can click the Check Again button to have the installer recheck the requirement and update the status. Repeat as needed until all the checks have a status of Succeeded. Click Next.
    The Summary window appears.
21. Review the contents of the Summary window and then click Install.
    The installer displays a progress indicator enabling you to monitor the installation process.
22. If you did not configure automation of the root scripts, then you are required to run certain scripts as the `root` user, as specified in the Execute Configuration Scripts window. Do not click OK until you have run all the scripts. Run the scripts on all nodes as directed, in the order shown.
    For example, on Oracle Linux you perform the following steps (note that for clarity, the examples show the current user, node and directory in the prompt):

    1.  As the `grid` user on `node1`, open a terminal window, and enter the following commands:

            [grid@node1 grid]$ cd /u01/app/oraInventory
            [grid@node1 oraInventory]$ su

    2.  Enter the password for the `root` user, and then enter the following command to run the first script on `node1`:

            [root@node1 oraInventory]# ./orainstRoot.sh

    3.  After the `orainstRoot.sh` script finishes on `node1`, open another terminal window, and as the `grid` user, enter the following commands:

            [grid@node1 grid]$ ssh node2
            [grid@node2 grid]$ cd /u01/app/oraInventory
            [grid@node2 oraInventory]$ su

    4.  Enter the password for the `root` user, and then enter the following command to run the first script on `node2`:

            [root@node2 oraInventory]#./orainstRoot.sh

    5.  After the `orainstRoot.sh` script finishes on `node2`, go to the terminal window you opened in part a of this step. As the `root` user on `node1`, enter the following commands to run the second script, `root.sh`:

            [root@node1 oraInventory]# cd /u01/app/19.0.0/grid
            [root@node1 grid]# ./root.sh

        Press Enter at the prompt to accept the default value.

        **Note:**

        You must run the `root.sh` script on the first node and wait for it to finish. You can run `root.sh` scripts concurrently on all other nodes except for the last node on which you run the script. Like the first node, the `root.sh` script on the last node must be run separately.

    6.  After the `root.sh` script finishes on `node1`, go to the terminal window you opened in part c of this step. As the `root` user on `node2`, enter the following commands:

            [root@node2 oraInventory]#cd /u01/app/19.0.0/grid
            [root@node2 grid]#./root.sh

        After the `root.sh` script completes, return to the Oracle Universal Installer window where the Installer prompted you to run the `orainstRoot.sh` and `root.sh` scripts. Click OK.

        The software installation monitoring window reappears.
23. Continue monitoring the installation until the Finish window appears. Then click Close to complete the installation process and exit the installer.

**Caution:**

After installation is complete, do not remove manually or run `cron` jobs that remove `/tmp/.oracle` or `/var/tmp/.oracle` directories or their files while Oracle software is running on the server. If you remove these files, then the Oracle software can encounter intermittent hangs. Oracle Clusterware installations can fail with the error:

`CRS-0184: Cannot communicate with the CRS daemon`.

After your Oracle Grid Infrastructure installation is complete, you can install Oracle Database on a cluster node for high availability, or install Oracle RAC.

**See Also:**

[Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md) or [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform for information on installing Oracle Database

**Parent topic:** [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-new-cluster.md)
