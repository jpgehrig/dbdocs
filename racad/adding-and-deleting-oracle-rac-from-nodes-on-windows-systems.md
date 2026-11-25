This chapter describes how to extend an existing Oracle Real Application Clusters (Oracle RAC) home to other nodes and instances in the cluster, and delete Oracle RAC from nodes and instances in the cluster. This chapter provides instructions for Windows systems.

**Note:**

In this chapter, the entries for `Grid_home` refer to the full path name for the Oracle Grid Infrastructure home, and the entries for `Oracle_home` refer to substitutes for environment variables for the Oracle home with Oracle RAC.

If your goal is to clone an existing Oracle RAC home to create multiple new Oracle RAC installations across the cluster, then use the cloning procedures that are described in "Cloning Oracle RAC to Nodes in a New Cluster".

This chapter includes the following topics:

- Adding Oracle RAC to Nodes with Oracle Clusterware Installed

- Deleting Oracle RAC from a Cluster Node

**Note:**

- Ensure that you have a current backup of Oracle Cluster Registry (OCR) before adding or deleting Oracle RAC by running the `ocrconfig -showbackup` command.

- For all of the add node and delete node procedures, temporary directories such as `%TEMP%` or `C:\Temp` should not be shared directories. If your temporary directories are shared, then set your temporary environment variable, such as `%TEMP%`, to a location on a local node. In addition, use a directory path that exists on all of the nodes.

**Related Topics**

- [Cloning Oracle RAC to Nodes in a New Cluster](cloning-oracle-rac-to-nodes-in-a-new-cluster.md)

### Adding Oracle RAC to Nodes with Oracle Clusterware Installed

Before beginning this procedure, ensure that your existing nodes have the correct path to the `Grid_home` and that the `Oracle_home` environment variables are set correctly.

To add Oracle RAC database instances to nodes that already have Oracle Clusterware installed, you must extend the Oracle RAC home that is on an existing node (`node1` in this procedure) of the cluster to the target nodes.

1.  Navigate to the `Oracle_home``\addnode` directory on `node1` and run the `addnode.bat` script using the following syntax, where `node2` is the name of the node you are adding:

        addnode.bat "CLUSTER_NEW_NODES={node2}"

    To run this command in silent mode:

        addNode.bat -silent "CLUSTER_NEW_NODES={node2}"

    For the Oracle home directory you use, if an Oracle home user was specified when the Oracle Database software was installed, then OUI requires the password for the Oracle home user. OUI checks the wallet (stored in the OCR) for the user and extracts the password from there. If the user information is not contained in the wallet, then the `addnode.bat` script generates an error unless you specify the `-promptPasswd` flag on the command line.

2.  If you store your policy-managed database on Oracle Automatic Storage Management (Oracle ASM), [Oracle Managed Files](glossary.md) is enabled, and if there is space in a server pool for `node2`, then `crsd` adds the Oracle RAC database instance to `node2` and no further action is necessary. If Oracle Managed Files is not enabled, then you must manually add undo and redo logs.

    If there is no space in a server pool, then `node2` moves into the Free server pool. Use the `srvctl modify srvpool` command to increase the cardinality of the server pool to accommodate `node2`, after which time `node2` moves out of the Free server pool and into the modified server pool, and `crsd` adds the Oracle RAC database instance to `node2`.

3.  If you have an administrator-managed database, then add a new instance on `node2`

If you have a shared Oracle home that is shared using Oracle Automatic Storage Management Cluster File System (Oracle ACFS), then do the following to extend the Oracle database home to `node2`:

1.  Start the Oracle ACFS resource on the new node by running the following command as `root` from the `Grid_home``\bin` directory:

        $ srvctl start filesystem -device volume_device_name [-node node_name]

    **Note:**

    Make sure the Oracle ACFS resources, including Oracle ACFS registry resource and Oracle ACFS file system resource where the Oracle home is located, are online on the newly added node.

2.  Run the following command as the user that installed Oracle RAC from the `Oracle_home``\oui\bin` directory on the node you are adding to add the Oracle RAC database home:

        setup.exe -attachHome ORACLE_HOME="ORACLE_HOME" LOCAL_NODE="node2"
          ORACLE_HOME_NAME="home_name" -cfs

3.  Navigate to the `Oracle_home``\addnode` directory on `node1` and run the `addnode.bat` script as the user that installed Oracle RAC using the following syntax:

        addnode.bat -noCopy "CLUSTER_NEW_NODES={node2}"

    **Note:**

    Use the `-noCopy` option because the Oracle home on the destination node is already fully populated with software.

If you have a shared Oracle home on a shared file system that is not Oracle ACFS, then you must first create a mount point for the Oracle RAC database home on the target node, mount and attach the Oracle RAC database home, and update the Oracle Inventory, as follows:

1.  Run the `srvctl config database -db ``db_name` command on an existing node in the cluster to obtain the mount point information.

2.  Mount the file system that hosts the Oracle RAC database home.

3.  Run the following command as the user that installed Oracle RAC from the `Oracle_home``\oui\bin` directory on the node you are adding to add the Oracle RAC database home:

        setup.exe -attachHome ORACLE_HOME="ORACLE_HOME" "CLUSTER_NODES=
          local_node_name}" LOCAL_NODE="node_name" ORACLE_HOME_NAME="home_name"

4.  Update the Oracle Inventory as the user that installed Oracle RAC, as follows:

        setup.exe -updateNodeList ORACLE_HOME=mount_point_path "CLUSTER_NODES={node_list}"

    In the preceding command, `node_list` refers to a list of all nodes where the Oracle RAC database home is installed, including the node you are adding.

**Note:**

Oracle recommends that you back up your voting disk and Oracle Cluster Registry (OCR) files after you complete the node addition process.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md)
- Adding Administrator-Managed Oracle RAC Database Instances to Target Nodes

#### Adding Administrator-Managed Oracle RAC Database Instances to Target Nodes

You can use either Oracle Enterprise Manager or DBCA to add Oracle RAC database instances to the target nodes.

This section describes using DBCA to add Oracle RAC database instances.

These tools guide you through the following tasks:

- Creating a new database instance on each target node

- Creating and configuring high availability components

- Creating the Oracle Net configuration for a non-default listener from the Oracle home

- Starting the new instance

- Creating and starting services if you entered services information on the Services Configuration page

After adding the instances to the target nodes, you should perform any necessary service configuration procedures.

**Related Topics**

- [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md)

##### Using DBCA in Interactive Mode to Add Database Instances to Target Nodes

To add a database instance to a target node using DBCA in interactive mode, perform the following steps:

1.  Ensure that your existing nodes have the Oracle home environment variable set correctly.

2.  Start DBCA by entering `dbca` at the system prompt from the `Oracle_home``\bin` directory on an existing node.

    DBCA performs certain CVU checks while running. However, you can also run CVU from the command line to perform various verifications.

3.  On the Database Operations page, select Instance Management, click Next, and DBCA displays the Instance Management page.

4.  Select Add Instance and click Next. DBCA displays the List of Cluster Databases page that shows the databases and their current status, such as `ACTIVE` or `INACTIVE`.

5.  From the List of Cluster Databases page, select the active Oracle RAC database to which you want to add an instance. Click Next and DBCA displays the List of Cluster Database Instances page showing the names of the existing instances for the Oracle RAC database that you selected.

6.  Click Next to add a new instance and DBCA displays the Adding an Instance page.

7.  On the Adding an Instance page, enter the instance name in the field at the top of this page if the instance name that DBCA provides does not match your existing instance naming scheme. Then select the new node name from the list.

    **Note:**

    If you installed the Oracle home with the Oracle Home User option, then DBCA prompts you for that password on this page.

8.  Review the information on the Summary Page and click Finish to initiate instance addition operation. DBCA displays a progress dialog showing DBCA performing the instance addition operation.

##### Creating the OraMTS Service for Microsoft Transaction Server

Oracle Services for Microsoft Transaction Server (OraMTS) permit Oracle databases to be used as resource managers in Microsoft application-coordinated transactions. OraMTS acts as a proxy for the Oracle database to the Microsoft Distributed Transaction Coordinator (MSDTC). As a result, OraMTS provides client-side connection pooling and allows client components that leverage Oracle to participate in promotable and distributed transactions. In addition, OraMTS can operate with Oracle databases running on any operating system, given that the services themselves are run on Windows.

On releases earlier than Oracle Database 12c, the OraMTS service was created as part of a software-only installation. Starting with Oracle Database 12c, you must use a configuration tool to create this service.

Create the OraMTS service after adding a node or performing a software-only installation for Oracle RAC, as follows:

1.  Open a command window.

2.  Change directories to `%ORACLE_HOME%\bin`.

3.  Run the OraMTSCtl utility to create the OraMTS Service, where `host_name` is a list of nodes on which the service should be created:

        C:\..bin> oramtsctl.exe -new -host host_name

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cluster-verification-utility-reference.md)
- [Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/using-mts-with-oracledb.md)

##### Using DBCA in Silent Mode to Add Database Instances to Target Nodes

Add instances to nodes on which you have extended an Oracle Clusterware home and an Oracle Database home.

Use DBCA in silent mode with the following syntax:

    dbca -silent -addInstance -nodeName node_name -gdbName gdb_name
    [-instanceName instance_name -sysDBAUserName sysdba -sysDBAPassword password]

Perform any necessary service configuration procedures.

**Related Topics**

- [Service Management Policy](workload-management-with-dynamic-database-services.md)
- [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md)

### Deleting Oracle RAC from a Cluster Node

To remove Oracle RAC from a cluster node, you must delete the database instance and the Oracle RAC software before removing the node from the cluster.

**Note:**

If there are no database instances on the node you want to delete, then remove Oracle RAC.

This section includes the following procedures to delete nodes from clusters in an Oracle RAC environment:

- Deleting Instances from Oracle RAC Databases

- Removing Oracle RAC

- Deleting Nodes from the Cluster

**Related Topics**

- Removing Oracle RAC

#### Deleting Instances from Oracle RAC Databases

The procedures for deleting instances are different for policy-managed and administrator-managed databases.

Deleting a policy-managed database instance involves reducing the size of the server pool in which the database instance resides. Deleting an administrator-managed database instance involves using DBCA to delete the database instance.

##### Deleting Policy-Managed Databases

To delete a policy-managed database, decrease the size of the server pool in which a database instance resides. This effectively removes the instance without having to remove the Oracle RAC software from the node or the node from the cluster.

For example, you can delete a policy-managed database by running the following commands on any node in the cluster:

    $ srvctl stop instance -db db_unique_name -node node_name
    $ srvctl relocate server -servers "server_name_list" -serverpool Free

The first command stops on the instance on a particular node and the second command moves the list of servers out of their current server pool and into the Free server pool.

##### Deleting Instances from Administrator-Managed Databases

**Note:**

Before deleting an instance from an Oracle RAC database using SRVCTL, do the following:

- If you have services configured, then relocate the services

- Modify the services so that each service can run on one of the remaining instances

- Ensure that the instance to be removed from an administrator-managed database is neither a preferred nor an available instance of any service

**Related Topics**

- Removing Oracle RAC
- [Administering Services with SRVCTL](workload-management-with-dynamic-database-services.md)

##### Using DBCA in Interactive Mode to Delete Instances from Nodes

To delete an instance using DBCA in interactive mode, perform the following steps:

1.  Verify there is a current backup of OCR.

    Run the `ocrconfig -showbackup` command to ensure there is a valid backup.

2.  Start DBCA.

    Start DBCA on a node other than the node that hosts the instance that you want to delete. The database and the instance that you plan to delete should continue to be started and running during this step.

3.  On the DBCA Operations page, select Instance Management, click Next, and DBCA displays the Instance Management page.

4.  On the Instance Management page, select Delete Instance, click Next, and DBCA displays the List of Cluster Databases page.

5.  Select an Oracle RAC database from which to delete an instance. Click Next and DBCA displays the List of Cluster Database Instances page. The List of Cluster Database Instances page shows the instances that are associated with the Oracle RAC database that you selected and the status of each instance.

6.  On the List of Cluster Databases page, select the Oracle RAC database from which to delete the instance, as follows:

    1.  On the List of Cluster Database Instances page, DBCA displays the instances that are associated with the Oracle RAC database that you selected and the status of each instance. Select the cluster database from which you will delete the instance. Click Finish.

    2.  Click OK on the Confirmation dialog to proceed to delete the instance.

    3.  Click OK on the next Confirmation dialog to delete the instance and related Optimal Flexible Architecture (OFA) directory structure.

        DBCA displays a progress dialog showing that DBCA is deleting the instance. During this operation, DBCA removes the instance and the instance's Oracle Net configuration.

        Click No and exit DBCA or click Yes to perform another operation. If you click Yes, then DBCA displays the Operations page.

7.  Verify that the dropped instance's redo thread has been removed using SQL\*Plus to query the `V$LOG` view from an existing instance. If the redo thread is not disabled, then disable the thread. For example:

        SQL> ALTER DATABASE DISABLE THREAD 2;

8.  Verify that the instance has been removed from OCR by running the following command, where `db_unique_name` is the name of the database:

        srvctl config database -db db_unique_name

9.  If you are deleting more than one node, then repeat these steps to delete the instances from all the nodes that you are going to delete.

##### Using DBCA in Silent Mode to Delete Instances from Nodes

You can use DBCA in silent mode to delete a database instance from a node.

To remove an instance, use the following command syntax. Provide a node name only if you are deleting an instance from a node other than the one on where DBCA is running as shown in the following example where `password` is the SYSDBA password:

    dbca -silent -deleteInstance [-nodeName node_name] -gdbName gdb_name
    -instanceName instance_name [-sysDBAUserName sysdba] [-sysDBAPassword password]

The following table describes the values that you need to supply for each variable.

Table 12-1 Variables in the DBCA Silent Mode Syntax

| Variable        | Description                                                                                                                             |
|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `node_name`     | The node on which you want to add (or delete) the instance.                                                                             |
| `gdb_name`      | Global database name.                                                                                                                   |
| `instance_name` | Name of the instance. Provide an instance name only if you want to override the Oracle naming convention for Oracle RAC instance names. |
| `sysdba`        | Name of the Oracle user with `SYSDBA` privileges.                                                                                       |
| `password`      | Password for the `SYSDBA` user.                                                                                                         |

At this point, you have accomplished the following:

- Deregistered the selected instance from its associated Oracle Net Services listeners

- Deleted the selected database instance from the instance's configured node

- Removed the Oracle Net configuration

- Deleted the Oracle Flexible Architecture directory structure from the instance's configured node.

#### Removing Oracle RAC

This procedure removes the Oracle RAC software from the node you are deleting from the cluster and updates inventories on the remaining nodes.

1.  If there is a listener in the Oracle RAC home on the node you are deleting, then you must disable and stop it before deleting the Oracle RAC software. Run the following commands on any node in the cluster, specifying the name of the listener and the name of the node you are deleting:

        C:\srvctl disable listener -listener listener_name -node name_of_node_to_delete
        C:\srvctl stop listener -listener listener_name -node name_of_node_to_delete

2.  Deinstall the Oracle home from the node that you are deleting by running the following command from the `Oracle_home\``deinstall` directory:

        deinstall -local

If you have a shared Oracle RAC home, then append the `-cfs` option to the command example in this step and provide a complete path location for the cluster file system.

#### Deleting Nodes from the Cluster

After you delete the instance, you can begin the process of deleting the node from the cluster. You accomplish this by running scripts on the node you want to delete to remove the Oracle Clusterware installation and you run scripts on the remaining nodes to update the node list.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md)
