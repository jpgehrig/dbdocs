Complete this procedure to install Oracle Grid Infrastructure software for Oracle Standalone Cluster.

1.  As the `grid` user, download the Oracle Grid Infrastructure image files and extract the files into the Grid home. For example:
        $ mkdir -p /u01/app/19.0.0/grid
        $ chown grid:oinstall /u01/app/19.0.0/grid
        $ cd /u01/app/19.0.0/grid
        $ unzip -q download_location/grid.zip

    `grid.zip` is the name of the Oracle Grid Infrastructure image zip file.

    **Note:**

    - You must extract the zip image software into the directory where you want your Grid home to be located.

    - Download and copy the Oracle Grid Infrastructure image files to the local node only. During installation, the software is copied and installed on all other nodes in the cluster.

    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
2.  Configure the shared disks for use with Oracle ASM Filter Driver:
    1.  Log in as the `root` user and set the environment variable `ORACLE_HOME` to the location of the Grid home.
        For C shell:

            $ su root
            # setenv ORACLE_HOME /u01/app/19.0.0/grid

        For bash shell:

            $ su root
            # export ORACLE_HOME=/u01/app/19.0.0/grid
    2.  Use Oracle ASM command line tool (ASMCMD) to provision the disk devices for use with Oracle ASM Filter Driver.
            # cd /u01/app/19.0.0/grid/bin
            # ./asmcmd afd_label DATA1 /dev/rdsk/cXtYdZsA --init
            # ./asmcmd afd_label DATA2 /dev/rdsk/cXtYdZsB --init
            # ./asmcmd afd_label DATA3 /dev/rdsk/cXtYdZsC --init
    3.  Verify the device has been marked for use with Oracle ASMFD.
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsA
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsB
            # ./asmcmd afd_lslbl /dev/rdsk/cXtYdZsC
3.  Log in as the `grid` user, and start the Oracle Grid Infrastructure installer by running the following command:
        $ /u01/app/19.0.0/grid/gridSetup.sh

    The installer starts and the Select Configuration Option window appears.
4.  Choose the option Configure Grid Infrastructure for a New Cluster, then click Next.
    The Select Cluster Configuration window appears.
5.  Choose the option Configure an Oracle Standalone Cluster, then click Next.
    Select the Configure as Extended Cluster option to extend an Oracle RAC cluster across two or more separate sites, each equipped with its own storage.
    The Grid Plug and Play Information window appears.
6.  In the Cluster Name and SCAN Name fields, enter the names for your cluster and cluster scan that are unique throughout your entire enterprise network.
    You can select Configure GNS if you have configured your domain name server (DNS) to send to the GNS virtual IP address name resolution requests for the subdomain GNS serves, as explained in this guide.

    For cluster member node public and VIP network addresses, provide the information required depending on the kind of cluster you are configuring:

    - If you plan to use automatic cluster configuration with DHCP addresses configured and resolved through GNS, then you only need to provide the GNS VIP names as configured on your DNS.

    - If you plan to use manual cluster configuration, with fixed IP addresses configured and resolved on your DNS, then provide the SCAN names for the cluster, and the public names, and VIP names for each cluster member node. For example, you can choose a name that is based on the node names' common prefix. The cluster name can be `mycluster` and the cluster SCAN name can be `mycluster-scan`.

    Click Next.
    The Cluster Node Information window appears.
7.  In the Public Hostname column of the table of cluster nodes, you should see your local node, for example `node1.example.com`.
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
8.   Select the usage type for each network interface displayed.
    Verify that each interface has the correct interface type associated with it. If you have network interfaces that should not be used by Oracle Clusterware, then set the network interface type to Do Not Use. For example, if you have only two network interfaces, then set the public interface to have a Use for value of Public and set the private network interface to have a Use for value of ASM & Private.
    Click Next. The Storage Option Information window appears.
9.  Select storage option for Oracle Cluster Registry (OCR) and voting files:
    1.  Select Use Oracle Flex ASM for storage to store OCR and voting files on an Oracle ASM disk group.
    2.  Select Use Shared File System to store OCR and voting files on a shared file system, and then click Next. The Create Grid Infrastructure Management Repository Option window appears.
10. Choose whether you want to create a Grid Infrastructure Management Repository for your Oracle Standalone Cluster installation, then click Next.
    If you choose Yes on this window, then the Grid Infrastructure Management Repository Option window appears. Otherwise, the Create ASM Disk Group window appears.
11. Choose whether you want to store the Grid Infrastructure Management Repository in a separate Oracle ASM disk group, then click Next.
    The Create ASM Disk Group window appears.
12. Provide the name and specifications for the Oracle ASM disk group.
    1.  In the Disk Group Name field, enter a name for the disk group, for example DATA.
    2.  Choose the Redundancy level for this disk group. Normal is the recommended option.
    3.  In the Add Disks section, choose the disks to add to this disk group.
        In the Add Disks section you should see the disks that you labeled in Step 2. If you do not see the disks, click the Change Discovery Path button and provide a path and pattern match for the disk, for example, `/dev/sd*`

        During installation, disks labelled as Oracle ASMFD disks or Oracle ASMLIB disks are listed as candidate disks when using the default discovery string. However, if the disk has a header status of MEMBER, then it is not a candidate disk.
    4.  If you want to use Oracle ASM Filter Driver (Oracle ASMFD) to manage your Oracle ASM disk devices, then select the option Configure Oracle ASM Filter Driver.
        If you are installing on Linux systems, and you want to use Oracle ASM Filter Driver (Oracle ASMFD) to manage your Oracle ASM disk devices, then you must deinstall Oracle ASM library driver (Oracle ASMLIB) before starting Oracle Grid Infrastructure installation.

    When you have finished providing the information for the disk group, click Next.
13. If you selected to use a different disk group for the GIMR, then the Grid Infrastructure Management Repository Option window appears. Provide the name and specifications for the GIMR disk group.
    1.  In the Disk Group Name field, enter a name for the disk group, for example DATA.
    2.  Choose the Redundancy level for this disk group. Normal is the recommended option.
    3.  In the Add Disks section, choose the disks to add to this disk group.

    When you have finished providing the information for the disk group, click Next.
    The Specify ASM Password window appears.
14. Choose the same password for the Oracle ASM SYS and ASMSNMP account, or specify different passwords for each account, then click Next.
    The Failure Isolation Support window appears.
15. Select the option Do not use Intelligent Platform Management Interface (IPMI), then click Next.
    The Specify Management Options window appears.
16. If you have Enterprise Manager Cloud Control installed in your enterprise, then choose the option Register with Enterprise Manager (EM) Cloud Control and provide the EM configuration information. If you do not have Enterprise Manager Cloud Control installed in your enterprise, then click Next to continue.
    The Privileged Operating System Groups window appears.
17. Accept the default operating system group names for Oracle ASM administration and click Next.
    The Specify Install Location window appears.
18. Specify the directory to use for the Oracle base for the Oracle Grid Infrastructure installation, then click Next. The Oracle base directory must be different from the Oracle home directory.
    If you copied the Oracle Grid Infrastructure installation files into the Oracle Grid home directory as directed in Step 1, then the default location for the Oracle base directory should display as `/u01/app/grid`.
    If you have not installed Oracle software previously on this computer, then the Create Inventory window appears.
19. Change the path for the inventory directory, if required. Then, click Next.
    If you are using the same directory names as the examples in this book, then it should show a value of `/u01/app/oraInventory`. The group name for the `oraInventory` directory should show `oinstall`.
    The Root Script Execution Configuration window appears.
20. Select the option to Automatically run configuration scripts. Enter the credentials for the root user or a sudo account, then click Next.
    Alternatively, you can Run the scripts manually as the `root` user at the end of the installation process when prompted by the installer.
    The Perform Prerequisite Checks window appears.
21. If any of the checks have a status of Failed and are not Fixable, then you must manually correct these issues. After you have fixed the issue, you can click the Check Again button to have the installer recheck the requirement and update the status. Repeat as needed until all the checks have a status of Succeeded. Click Next.
    The Summary window appears.
22. Review the contents of the Summary window and then click Install.
    The installer displays a progress indicator enabling you to monitor the installation process.
23. If you did not configure automation of the root scripts, then you are required to run certain scripts as the `root` user, as specified in the Execute Configuration Scripts window. Do not click OK until you have run all the scripts. Run the scripts on all nodes as directed, in the order shown.
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
24. Continue monitoring the installation until the Finish window appears. Then click Close to complete the installation process and exit the installer.

**Caution:**

After installation is complete, do not remove manually or run `cron` jobs that remove `/tmp/.oracle` or `/var/tmp/.oracle` directories or their files while Oracle software is running on the server. If you remove these files, then the Oracle software can encounter intermittent hangs. Oracle Clusterware installations can fail with the error:

`CRS-0184: Cannot communicate with the CRS daemon`.

After your Oracle Grid Infrastructure installation is complete, you can install Oracle Database on a cluster node for high availability, or install Oracle RAC.

**See Also:**

[Oracle Real Application Clusters Installation Guide](../rilin/installing-oracle-rac-and-oracle-rac-one-node.md) or [Oracle Database Installation Guide](../ladbi/installing-oracle-database.md) for your platform for information on installing Oracle Database

**Parent topic:** [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-new-cluster.md)
