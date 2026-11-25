Complete this procedure to install Oracle Grid Infrastructure software for Oracle Member Cluster for Oracle Database and Oracle Member Cluster for Applications.

You must create a Member Cluster Manifest File as explained in this guide before performing the installation.

Use this procedure to install an Oracle Member Cluster for Oracle Databases or Oracle Member Cluster for Applications.

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
4.  Choose either the Configure an Oracle Member Cluster for Oracle Databases or Configure an Oracle Member Cluster for Applications option, then click Next.
    The Cluster Domain Services window appears.
5.  Select the Manifest file that contains the configuration details about the management repository and other services for the Oracle Member Cluster.
    For Oracle Member Cluster for Oracle Databases, you can also specify the Grid Naming Service and Oracle ASM Storage server details using a Member Cluster Manifest file.

    Click Next.
6.  If you selected to configure an Oracle Member Cluster for applications, then the Configure Virtual Access window appears. Provide a Cluster Name and optional Virtual Host Name.
    The virtual host name serves as a connection address for the Oracle Member Cluster, and to provide service access to the software applications that you want the Oracle Member Cluster to install and run.
    Click Next.
    The Cluster Node Information window appears.
7.  In the Public Hostname column of the table of cluster nodes, you should see your local node, for example `node1.example.com`.
    The following is a list of additional information about node IP addresses:

    - For the local node only, Oracle Universal Installer (OUI) automatically fills in public and VIP fields. If your system uses vendor clusterware, then OUI may fill additional fields.

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
8.   Select the usage type for each network interface displayed, then click Next.
    Verify that each interface has the correct interface type associated with it. If you have network interfaces that should not be used by Oracle Clusterware, then set the network interface type to Do Not Use. For example, if you have only two network interfaces, then set the public interface to have a Use for value of Public and set the private network interface to have a Use for value of ASM & Private.
    Note: For Oracle Member Cluster for Applications configurations, you can choose to have one public network interface, instead of requiring two network interfaces, one private or ASM, and the other public.
    Click Next. The ASM Client Storage window appears.
9.  Choose the disk group to store Oracle Cluster Registry (OCR) and voting files for the cluster on the Oracle Domain Services Cluster.
    Click Next.
    The Operating System Groups window appears.
10. Accept the default operating system group names for Oracle ASM administration and click Next.
    The Specify Install Location window appears.
11. Specify the directory to use for the Oracle base for the Oracle Grid Infrastructure installation, then click Next. The Oracle base directory must be different from the Oracle home directory.
    If you copied the Oracle Grid Infrastructure installation files into the Oracle Grid home directory as directed in Step 1, then the default location for the Oracle base directory should display as `/u01/app/grid`.
    If you have not installed Oracle software previously on this computer, then the Create Inventory window appears.
12. Change the path for the inventory directory, if required. Then, click Next.
    If you are using the same directory names as the examples in this book, then it should show a value of `/u01/app/oraInventory`. The group name for the `oraInventory` directory should show `oinstall`.
    The Root Script Execution Configuration window appears.
13. Select the option to Automatically run configuration scripts. Enter the credentials for the root user or a sudo account, then click Next.
    Alternatively, you can Run the scripts manually as the `root` user at the end of the installation process when prompted by the installer.
    The Perform Prerequisite Checks window appears.
14. If any of the checks have a status of Failed and are not Fixable, then you must manually correct these issues. After you have fixed the issue, you can click the Check Again button to have the installer recheck the requirement and update the status. Repeat as needed until all the checks have a status of Succeeded. Click Next.
    The Summary window appears.
15. Review the contents of the Summary window and then click Install.
    The installer displays a progress indicator enabling you to monitor the installation process.
16. If you did not configure automation of the root scripts, then you are required to run certain scripts as the `root` user, as specified in the Execute Configuration Scripts window appears. Do not click OK until you have run the scripts. Run the scripts on all nodes as directed, in the order shown.
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

            [root@node2 oraInventory]# ./orainstRoot.sh

    5.  After the `orainstRoot.sh` script finishes on `node2`, go to the terminal window you opened in part a of this step. As the `root` user on `node1`, enter the following commands to run the second script, `root.sh`:

            [root@node1 oraInventory]# cd /u01/app/19.0.0/grid
            [root@node1 grid]# ./root.sh

        Press Enter at the prompt to accept the default value.

        **Note:**

        You must run the `root.sh` script on the first node and wait for it to finish. f your cluster has three or more nodes, then `root.sh` can be run concurrently on all nodes but the first. Node numbers are assigned according to the order of running `root.sh`. If you want to create a particular node number assignment, then run the root scripts in the order of the node assignments you want to make, and wait for the script to finish running on each node before proceeding to run the script on the next node. However, Oracle system identifier, or SID, for your Oracle RAC databases, do not follow the node numbers.

    6.  After the `root.sh` script finishes on `node1`, go to the terminal window you opened in part c of this step. As the `root` user on `node2`, enter the following commands:

            [root@node2 oraInventory]# cd /u01/app/19.0.0/grid
            [root@node2 grid]# ./root.sh

        After the `root.sh` script completes, return to the OUI window where the Installer prompted you to run the `orainstRoot.sh` and `root.sh` scripts. Click OK.

        The software installation monitoring window reappears.

    When you run `root.sh` during Oracle Grid Infrastructure installation, the Trace File Analyzer (TFA) Collector is also installed in the directory.`grid_home/tfa`.
17. After` root.sh` runs on all the nodes, OUI runs Net Configuration Assistant (`netca`) and Cluster Verification Utility. These programs run without user intervention.
18. During installation of Oracle Member Cluster for Oracle Databases, if the Member Cluster Manifest file does not include configuration details for Oracle ASM, then Oracle Automatic Storage Management Configuration Assistant (`asmca`) configures Oracle ASM for storage.
19. Continue monitoring the installation until the Finish window appears. Then click Close to complete the installation process and exit the installer.

**Caution:**

After installation is complete, do not remove manually or run `cron` jobs that remove `/tmp/.oracle` or `/var/tmp/.oracle` directories or their files while Oracle software is running on the server. If you remove these files, then the Oracle software can encounter intermittent hangs. Oracle Clusterware installations can fail with the error:

`CRS-0184: Cannot communicate with the CRS daemon`.

After your Oracle Grid Infrastructure installation is complete, you can install Oracle Database on a cluster node for high availability, other applications, or install Oracle RAC.

**See Also:**

[Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md) or [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform for information on installing Oracle Database

**Parent topic:** [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-new-cluster.md)
