Describes how to add nodes to an existing cluster, and how to delete nodes from clusters.

This chapter provides procedures for these tasks for Linux, UNIX, and Windows systems.

**Note:**

- Unless otherwise instructed, perform all add and delete node steps as the user who installed Oracle Clusterware.

- You can use Fleet Patching and Provisioning to add and delete cluster nodes.

- Oracle recommends that you use the cloning procedure described in "Cloning Oracle Clusterware" to create clusters.

This chapter includes the following topics:

- Prerequisite Steps for Adding Cluster Nodes

- Adding and Deleting Cluster Nodes on Linux and UNIX Systems

- Adding and Deleting Cluster Nodes on Windows Systems

**Related Topics**

- [Cloning Oracle Clusterware](cloning-oracle-clusterware.md)

### Prerequisite Steps for Adding Cluster Nodes

**Note:**

Ensure that you perform the preinstallation tasks listed in Oracle Grid Infrastructure Installation and Upgrade Guide for Linux before adding a node to a cluster.

Do not install Oracle Clusterware. The software is copied from an existing node when you add a node to the cluster.

Complete the following steps to prepare nodes to add to the cluster:

1.  Make physical connections.

    Connect the nodes' hardware to the network infrastructure of your cluster. This includes establishing electrical connections, configuring network interconnects, configuring shared disk subsystem connections, and so on. See your hardware vendor documentation for details about this step.

2.  Install the operating system.

    Install a cloned image of the operating system that matches the operating system on the other nodes in your cluster. This includes installing required service patches, updates, and drivers. See your operating system vendor documentation for details about this process.

    **Note:**

    Oracle recommends that you use a cloned image. However, if the installation fulfills the installation requirements, then install the operating system according to the vendor documentation.

3.  Create Oracle users.

    You must create all Oracle users on the new node that exist on the existing nodes. For example, if you are adding a node to a cluster that has two nodes, and those two nodes have different owners for the Oracle Grid Infrastructure home and the Oracle home, then you must create those owners on the new node, even if you do not plan to install an Oracle home on the new node.

    **Note:**

    Perform this step only for Linux and UNIX systems.

    As `root`, create the Oracle users and groups using the same user ID and group ID as on the existing nodes.

4.  Ensure that SSH is configured on the node.

    **Note:**

    SSH is configured when you install Oracle Clusterware. If SSH is not configured, then see Oracle Grid Infrastructure Installation and Upgrade Guide for information about configuring SSH.

5.  Verify the hardware and operating system installations with the Cluster Verification Utility (CVU).

    After you configure the hardware and operating systems on the nodes you want to add, you can run the following commands to verify that the nodes you want to add are reachable by other nodes in the cluster. You can also use this command to verify user equivalence to all given nodes from the local node, node connectivity among all of the given nodes, accessibility to shared storage from all of the given nodes, and so on.

    1.  From the `Grid_home``/bin` directory on an existing node, run the CVU command to obtain a detailed comparison of the properties of the reference node with all of the other nodes that are part of your current cluster environment. Replace `ref_node` with the name of a node in your existing cluster against which you want CVU to compare the nodes to be added. Specify a comma-delimited list of nodes after the `-n` option. In the following example, `orainventory_group` is the name of the Oracle Inventory group, and `osdba_group` is the name of the OSDBA group:

            $ cluvfy comp peer [-refnode ref_node] -n node_list
            [-orainv orainventory_group] [-osdba osdba_group] [-verbose]

    2.  Ensure that the Grid Infrastructure Management Repository has at least an additional 500 MB of space for each node added above four, as follows:

            $ oclumon manage -get repsize

        Add additional space, if required, as follows:

            $ oclumon manage -repos changerepossize total_in_MB

        **See Also:**

        Oracle Autonomous Health Framework User's Guide for more information about using OCLUMON

    **Note:**

    For the reference node, select a cluster node against which you want CVU to compare, for example, the nodes that you want to add that you specify with the `-n` option.

After completing the procedures in this section, you are ready to add the nodes to the cluster.

**Note:**

Avoid changing host names after you complete the Oracle Clusterware installation, including adding or deleting domain qualifications. Nodes with changed host names must be deleted from the cluster and added back with the new name.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/oracle-grid-infrastructure-installation-checklist.md)
- [Oracle Autonomous Health Framework User's Guide](../atnms/oclumon-command-reference.md)

### Adding and Deleting Cluster Nodes on Linux and UNIX Systems

Add or delete cluster nodes on Linux and UNIX systems.

The procedure in the section for adding nodes assumes that you have performed the steps in the "Prerequisite Steps for Adding Cluster Nodes" section.

The last step of the node addition process includes extending the Oracle Clusterware home from an Oracle Clusterware home on an existing node to the nodes that you want to add.

This section includes the following topics:

- Adding a Cluster Node on Linux and UNIX Systems

- Deleting a Cluster Node on Linux and UNIX Systems

**Note:**

Beginning with Oracle Clusterware 11g release 2 (11.2), Oracle Universal Installer defaults to silent mode when adding nodes.

**Related Topics**

- Prerequisite Steps for Adding Cluster Nodes

#### Adding a Cluster Node on Linux and UNIX Systems

There are two methods that you can use to add a node to your cluster.

##### Using Fleet Patching and Provisioning to Add a Node

If you have a Fleet Patching and Provisioning Server, then you can use Fleet Patching and Provisioning to add a node to a cluster with one command, as shown in the following example:

    $ rhpctl addnode gihome -client rhpclient -newnodes clientnode2:clientnode2-vip -root

The preceding example adds a node named `clientnode2` with VIP `clientnode2-vip` to the Fleet Patching and Provisioning Client named `rhpclient`, using root credentials (login for the node you are adding).

##### Using Oracle Grid Infrastructure Installer to Add a Node

If you do you not want to use Fleet Patching and Provisioning to add a node to the cluster, then you can use the Oracle Grid Infrastructure installer to accomplish the task.

**Note:**

You can use the `$Oracle_home``/install/response/gridSetup.rsp` template to create a response file to add nodes using the Oracle Grid Infrastructure Installer for non-interactive (silent mode) operation.

To add a node to the cluster using the Oracle Grid Infrastructure installer

1.  Run `./gridSetup.sh` to start the installer.

2.  On the Select Configuration Option page, select Add more nodes to the cluster.

3.  On the Cluster Node Information page, click Add... to provide information for nodes you want to add.

4.  When the verification process finishes on the Perform Prerequisite Checks page, check the summary and then click Install.

5.  If prompted, then run the `orainstRoot.sh` script as root to populate the `/etc/oraInst.loc` file with the location of the central inventory. For example:

        # /opt/oracle/oraInventory/orainstRoot.sh

6.  Run the `Grid_home``/root.sh` script on the `node3` as `root` and run the subsequent script, as instructed.

    **Note:**

    - If you ran the `root.sh` script in the previous step, then you do not need to run it again.

    - If you have a policy-managed database, then you must ensure that the Oracle home is cloned to the new node before you run the `root.sh` script.

    - If you have any administrator-managed database instances configured on the nodes which are going to be added to the cluster, then you must extend the Oracle home to the new node before you run the `root.sh` script.

      Alternatively, remove the administrator-managed database instances using the `srvctl remove instance` command.

7.  If you have an Oracle RAC or Oracle RAC One Node database configured on the cluster and you have a local Oracle home, then do the following to extend the Oracle database home to `node3`:

    1.  Navigate to the `Oracle_home``/addnode` directory on `node1` and run the `addnode.sh` script as the user that installed Oracle RAC using the following syntax:

            $ ./addnode.sh "CLUSTER_NEW_NODES='{node3,node4}'"

    2.  Run the `Oracle_home``/root.sh` script on `node3` as `root`, where `Oracle_home` is the Oracle RAC home.

    3.  Open the pluggable databases (PDBs) on the newly added node using the following commands in your SQL\*Plus session:

            SQL> CONNECT / AS SYSDBA
            SQL> ALTER PLUGGABLE DATABASE pdb_name OPEN;

    If you have a shared Oracle home that is shared using Oracle Automatic Storage Management Cluster File System (Oracle ACFS), then do the following to extend the Oracle database home to `node3`:

    1.  Run the `Grid_home``/root.sh` script on `node3` as `root`, where `Grid_home` is the Oracle Grid Infrastructure home.

    2.  Run the following command as the user that installed Oracle RAC from the `Oracle_home``/oui/bin` directory on the node you are adding to add the Oracle RAC database home:

            $ ./runInstaller -attachHome ORACLE_HOME="ORACLE_HOME" "CLUSTER_NODES={node3}"
            LOCAL_NODE="node3" ORACLE_HOME_NAME="home_name" -cfs

    3.  Navigate to the `Oracle_home``/addnode` directory on `node1` and run the `addnode.sh` script as the user that installed Oracle RAC using the following syntax:

            $ ./addnode.sh -noCopy "CLUSTER_NEW_NODES='{node3,node4}'"

        **Note:**

        Use the `-noCopy` option because the Oracle home on the destination node is already fully populated with software.

    If you have a shared Oracle home on a shared file system that is not Oracle ACFS, then you must first create a mount point for the Oracle RAC database home on the target node, mount and attach the Oracle RAC database home, and update the Oracle Inventory, as follows:

    1.  Run the `srvctl config database -db ``db_name` command on an existing node in the cluster to obtain the mount point information.

    2.  Run the following command as `root` on `node3` to create the mount point:

            # mkdir -p mount_point_path

    3.  Mount the file system that hosts the Oracle RAC database home.

    4.  Run the following command as the user that installed Oracle RAC from the `Oracle_home``/oui/bin` directory on the node you are adding to add the Oracle RAC database home:

            $ ./runInstaller -attachHome ORACLE_HOME="ORACLE_HOME" "CLUSTER
            _NODES={local_node_name}" LOCAL_NODE="node_name" ORACLE_HOME_NAME="home_name" -cfs

        Navigate to the `Oracle_home``/addnode` directory on `node1` and run the `addnode.sh` script as the user that installed Oracle RAC using the following syntax:

            $ ./addnode.sh -noCopy "CLUSTER_NEW_NODES='{node3,node4}'"

        **Note:**

        Use the `-noCopy` option because the Oracle home on the destination node is already fully populated with software.

    **Note:**

    After running `addnode.sh`, ensure the `Grid_home``/network/admin/samples` directory has permissions set to 750.

8.  Start the Oracle ACFS resource on the new node by running the following command as `root` from the `Grid_home``/bin` directory:

        # srvctl start filesystem -device volume_device_name -node node3

    **Note:**

    Ensure the Oracle ACFS resources, including Oracle ACFS registry resource and Oracle ACFS file system resource where the Oracle home is located, are online on the newly added node.

9.  Run the following CVU command as the user that installed Oracle Clusterware to check cluster integrity. This command verifies that any number of specified nodes has been successfully added to the cluster at the network, shared storage, and clusterware levels:

        $ cluvfy stage -post nodeadd -n node3 [-verbose]

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)
- [cluvfy stage nodeadd](cluster-verification-utility-reference.md)
- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-windows-systems.md)
- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-linux-and-unix-systems.md)

#### Deleting a Cluster Node on Linux and UNIX Systems

Delete a node from a cluster on Linux and UNIX systems.

**Note:**

- If you delete the last node of a cluster that is serviced by GNS, then you must delete the entries for that cluster from GNS.

- If you have nodes in the cluster that are unpinned, then Oracle Clusterware ignores those nodes after a time and there is no need for you to remove them.

- If one creates node-specific configuration for a node (such as disabling a service on a specific node, or adding the node to the candidate list for a server pool) that node-specific configuration is not removed when the node is deleted from the cluster. Such node-specific configuration must be removed manually.

- Voting files are automatically backed up in OCR after any changes you make to the cluster.

- When you want to delete a non-Hub Node from an Oracle Flex Cluster, you need only complete steps 1 through 4 of this procedure.

To delete a node from a cluster:

1.  Ensure that `Grid_home` correctly specifies the full directory path for the Oracle Clusterware home on each node, where `Grid_home` is the location of the installed Oracle Clusterware software.
2.  Run the following command as either `root` or the user who installed Oracle Clusterware to determine whether the node you want to delete is active and whether it is pinned:
        $ olsnodes -s -t

    If the node is pinned, then run the `crsctl unpin css` command. Otherwise, proceed to the next step.
3.  On the node that you are deleting, stop all the running Oracle Database instances:
        $ srvctl stop instance -n node_to_be_deleted
4.  On the node that you are deleting, depending on whether you have a shared or local Oracle home, complete one of the following procedures as the user who installed Oracle Clusterware:
    - For a local home, deinstall the Oracle Clusterware home from the node that you want to delete, as follows, by running the following command, where `Grid_home` is the path defined for the Oracle Clusterware home:

          $ Grid_home/deinstall/deinstall -local

      **Caution:**

      - If you do not specify the `-local` flag, then the command removes the Oracle Grid Infrastructure home from every node in the cluster.

      - If you cut and paste the preceding command, then paste it into a text editor before pasting it to the command line to remove any formatting this document might contain.

      **Note:**

      Alternatively, after you configure Oracle Grid Infrastructure, if you want to delete any node from the grid infrastructure, then you can do so by running `Grid_home``/gridSetup.sh`, selecting Remove nodes from the cluster and following the prompts.

    - If you have a shared home, then run the following commands in the following order on the node you want to delete.

      Run the following command to deconfigure Oracle Clusterware:

          $ Grid_home/crs/install/rootcrs.sh -deconfig -force

      Run the following command from the `Grid_home``/oui/bin` directory to detach the Grid home:

          $ ./runInstaller -detachHome ORACLE_HOME=Grid_home -silent -local

      Manually delete any configuration files, as prompted by the installation utility.
5.  From any node that you are not deleting, run the following command from the `Grid_home``/bin` directory as `root` to delete the node from the cluster:
        # crsctl delete node -n node_to_be_deleted
6.  Run the following CVU command to verify that the specified nodes have been successfully deleted from the cluster:
        $ cluvfy stage -post nodedel -n node_list [-verbose]
7.  If you remove a cluster node on which Oracle Clusterware is down, then determine whether the VIP for the deleted node still exists, as follows:
        $ srvctl config vip -node deleted_node_name

    If the VIP still exists, then delete it, as follows:

        $ srvctl stop vip -vip vip_name
        $ srvctl remove vip -vip vip_name

Using Fleet Patching and Provisioning to Delete a Node

Alternatively, you can use Fleet Patching and Provisioning to delete a node from a cluster with one command, as shown in the following example:

    $ rhpctl deletenode gihome -client rhpclient -node clientnode2 -root

The preceding example deletes a node named `clientnode2` from the Fleet Patching and Provisioning Client named `rhpclient`, using root credentials (login for the node you are deleting).

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-linux-and-unix-systems.md)
- [cluvfy stage nodedel](cluster-verification-utility-reference.md)

### Adding and Deleting Cluster Nodes on Windows Systems

This section explains cluster node addition and deletion on Windows systems. This section includes the following topics:

- Adding a Node to a Cluster on Windows Systems

- Deleting a Cluster Node on Windows Systems

**See Also:**

Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows for more information about deleting an entire cluster

#### Adding a Node to a Cluster on Windows Systems

Ensure that you complete the prerequisites listed in "Prerequisite Steps for Adding Cluster Nodes" before adding nodes.

This procedure describes how to add a node to your cluster. This procedure assumes that:

- There is an existing cluster with two nodes named `node1` and `node2`

- You are adding a node named `node3`

- You have successfully installed Oracle Clusterware on `node1` and `node2` in a local home, where `Grid_home` represents the successfully installed home

**Note:**

Do not use the procedures described in this section to add cluster nodes in configurations where the Oracle database has been upgraded from Oracle Database 10g release 1 (10.1) on Windows systems.

To add a node:

1.  Verify the integrity of the cluster and `node3`:

        C:\>cluvfy stage -pre nodeadd -n node3 [-fixup] [-verbose]

    You can specify the `-fixup` option and a directory into which CVU prints instructions to fix the cluster or node if the verification fails.

2.  On `node1`, go to the `Grid_home``\addnode` directory and run the `addnode.bat` script, as follows:

        C:\>addnode.bat "CLUSTER_NEW_NODES={node3}"
        "CLUSTER_NEW_VIRTUAL_HOSTNAMES={node3-vip}"

3.  Run the following command on the new node:

        C:\>Grid_home\crs\config\gridconfig.bat

4.  The following steps are required only if you have database homes configured to use Oracle ACFS:

    1.  For each database configured to use Oracle ACFS, run the following command from the Oracle RAC database home:

            C:\>ORACLE_HOME\bin\srvctl stop database -db database_unique_name

        **Note:**

        Run the `srvctl config database` command to list all of the databases configured with Oracle Clusterware. Use the `srvctl config database -db ``database_unique_name` to find the database details. If the `ORACLE_HOME` path leads to the Oracle ACFS mount path, then the database uses Oracle ACFS. Use the command output to find the database instance name configured to run on the newly added node.

    2.  Use Windows Server Manager Control to stop and delete services.

    3.  For each of the databases and database homes collected in the first part of this step, run the following command:

            C:\> ORACLE_HOME\bin\srvctl start database -db database_unique_name

5.  Run the following command to verify the integrity of the Oracle Clusterware components on all of the configured nodes, both the preexisting nodes and the nodes that you have added:

        C:\>cluvfy stage -post crsinst -n all [-verbose]

After you complete the procedure in this section for adding nodes, you can optionally extend Oracle Database with Oracle RAC components to the new nodes, making them members of an existing Oracle RAC database.

**See Also:**

Oracle Real Application Clusters Administration and Deployment Guide for more information about extending Oracle Database with Oracle RAC to new nodes

##### Creating the OraMTS Service for Microsoft Transaction Server

Oracle Services for Microsoft Transaction Server (OraMTS) permit Oracle databases to be used as resource managers in Microsoft application-coordinated transactions. OraMTS acts as a proxy for the Oracle database to the Microsoft Distributed Transaction Coordinator (MSDTC). As a result, OraMTS provides client-side connection pooling and allows client components that leverage Oracle to participate in promotable and distributed transactions. In addition, OraMTS can operate with Oracle databases running on any operating system, given that the services themselves are run on Windows.

On releases earlier than Oracle Database 12c, the OraMTS service was created as part of a software-only installation. Starting with Oracle Database 12c, you must use a configuration tool to create this service.

Create the OraMTS service after adding a node or performing a software-only installation for Oracle RAC, as follows:

1.  Open a command window.

2.  Change directories to `%ORACLE_HOME%\bin`.

3.  Run the `OraMTSCtl` utility to create the OraMTS Service, where `host_name` is a list of nodes on which the service should be created:

        C:\..bin> oramtsctl.exe -new -host host_name

**Related Topics**

- Prerequisite Steps for Adding Cluster Nodes
- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-windows-systems.md)
- [Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/program.md)

**See Also:**

Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows for more information about OraMTS, which allows Oracle databases to be used as resource managers in distributed transactions

#### Deleting a Cluster Node on Windows Systems

Delete a cluster node from Windows systems.

This procedure assumes that Oracle Clusterware is installed on `node1`, `node2`, and `node3`, and that you are deleting `node3` from the cluster.

**Note:**

- Oracle does not support using Oracle Enterprise Manager to delete nodes on Windows systems.

- If you delete the last node of a cluster that is serviced by GNS, then you must delete the entries for that cluster from GNS.

- You can remove the Oracle RAC database instance from the node before removing the node from the cluster but this step is not required. If you do not remove the instance, then the instance is still configured but never runs. Deleting a node from a cluster does not remove a node's configuration information from the cluster. The residual configuration information does not interfere with the operation of the cluster.

  See Also: Oracle Real Application Clusters Administration and Deployment Guide for more information about deleting an Oracle RAC database instance

To delete a cluster node on Windows systems:

1.  Only if you have a local home, on the node you want to delete, run the following command with `-local` option to update the node list:
        C:\>Grid_home\oui\bin\setup.exe -updateNodeList ORACLE_HOME=Grid_home "CLUSTER_NODES=
        {node_to_be_deleted}" CRS=TRUE -local

    **Note:**

    If you are deleting a non-Hub Node from an Oracle Flex Cluster, then you do not have run this command.
2.  Run the deinstall tool on the node you want to delete to deinstall and deconfigure the Oracle Clusterware home, as follows:
        C:\Grid_home\deinstall\>deinstall.bat -local

    **Caution:**

    - If you do not specify the `-local` flag, then the command removes the Oracle Grid Infrastructure home from every node in the cluster.

    - If you cut and paste the preceding command, then paste it into a text editor before pasting it to the command line to remove any formatting this document might contain.
3.  On a node that you are not deleting, run the following command:
        C:\>Grid_home\bin\crsctl delete node -n node_to_be_deleted
4.  Run the following CVU command to verify that the specified nodes have been successfully deleted from the cluster:
        C:\>cluvfy stage -post nodedel -n node_list [-verbose]
5.  If you remove a cluster node on which Oracle Clusterware is down, then determine whether the VIP for the deleted node still exists, as follows:
        C:\> ORACLE_HOME\bin\srvctl config vip -node deleted_node_name

    If the VIP still exists, then delete it, as follows:

        C:\> ORACLE_HOME\bin\srvctl stop vip -vip vip_name
        C:\> ORACLE_HOME\bin\srvctl remove vip -vip vip_name

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-windows-systems.md)
- [cluvfy stage nodedel](cluster-verification-utility-reference.md)
