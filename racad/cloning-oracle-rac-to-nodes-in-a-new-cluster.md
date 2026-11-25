This chapter describes how to clone Oracle Real Application Clusters (Oracle RAC) database homes on Linux and UNIX systems to nodes in a new cluster.

This chapter describes a noninteractive cloning technique that you implement with scripts. The cloning techniques described in this chapter are best suited for performing multiple simultaneous cluster installations. Creating the scripts is a manual process and can be error prone. If you only have one cluster to install, then you should use the traditional automated and interactive installation methods, such as Oracle Universal Installer, or the Provisioning Pack feature of Oracle Enterprise Manager.

**Note:**

Cloning is not a replacement for Oracle Enterprise Manager cloning that is a part of the Provisioning Pack. During Oracle Enterprise Manager cloning, the provisioning process interactively asks you the details about the Oracle home (such as the location to which you want to deploy the clone, the name of the Oracle Database home, a list of the nodes in the cluster, and so on).

The Provisioning Pack feature of Oracle Enterprise Manager Cloud Control provides a framework to make it easy for you to automate the provisioning of new nodes and clusters. For data centers with many Oracle RAC clusters, the investment in creating a cloning procedure to easily provision new clusters and new nodes to existing clusters is worth the effort.

This chapter includes the following topics:

- Introduction to Cloning Oracle RAC

- Preparing to Clone Oracle RAC

- Deploying Oracle RAC Clone to Nodes in a Cluster

- Locating and Viewing Log Files Generated During Cloning

**Related Topics**

- [Using Cloning to Extend Oracle RAC to Nodes in the Same Cluster](using-cloning-to-extend-oracle-rac-to-nodes-in-the-same-cluster.md)

### Introduction to Cloning Oracle RAC

Cloning is the process of copying an existing Oracle RAC installation to a different location and updating the copied bits to work in the new environment. The changes made by one-off patches applied on the source Oracle home, would also be present after the clone operation. The source and the destination path (host to be cloned) need not be the same.

Some situations in which cloning is useful are:

- Cloning provides a way to prepare an Oracle home once and deploy it to many hosts simultaneously. You can complete the installation silently, as a noninteractive process. You do not need to use a graphical user interface (GUI) console and you can perform cloning from a Secure Shell (SSH) terminal session, if required.

- Cloning enables you to create an installation (copy of a production, test, or development installation) with all patches applied to it in a single step. Once you have performed the base installation and applied all patch sets and patches on the source system, the clone performs all of these individual steps as a single procedure. This is in contrast to going through the installation process to perform the separate steps to install, configure, and patch the installation on each node in the cluster.

- Installing Oracle RAC by cloning is a very quick process. For example, cloning an Oracle home to a new cluster of more than two nodes requires a few minutes to install the Oracle base software, plus a few minutes more for each node (approximately the amount of time it takes to run the `root.sh` script).

The cloned installation behaves the same as the source installation. For example, the cloned Oracle home can be removed using Oracle Universal Installer or patched using OPatch. You can also use the cloned Oracle home as the source for another cloning operation. You can create a cloned copy of a test, development, or production installation by using the command-line cloning scripts. The default cloning procedure is adequate for most usage cases. However, you can also customize various aspects of cloning, for example, to specify custom port assignments, or to preserve custom settings.

The cloning process works by copying all of the files from the source Oracle home to the destination Oracle home. Thus, any files used by the source instance that are located outside the source Oracle home's directory structure are not copied to the destination location.

The size of the binaries at the source and the destination may differ because these are relinked as part of the clone operation and the operating system patch levels may also differ between these two locations. Additionally, the number of files in the cloned home would increase because several files copied from the source, specifically those being instantiated, are backed up as part of the clone operation.

### Preparing to Clone Oracle RAC

Use this overview to understand the procedures you use to clone Oracle RAC.

In the preparation phase, you create a copy of an Oracle home that you then use to perform the cloning procedure on one or more nodes. You also install Oracle Clusterware.

#### Install Oracle RAC

Use the detailed instructions in Oracle Real Application Clusters Installation Guide for your platform for your platform to install the Oracle RAC software and patches:

1.  Install Oracle RAC and choose the Software only installation option.

2.  Patch the release to the required level (for example, 12.1.0.n).

3.  Apply one-off patches, if necessary.

#### Create a backup of the source home

Create a copy of the Oracle RAC home. Use this file to copy the Oracle RAC home to each node in the cluster.

When creating the backup (tar) file, the best practice is to include the release number in the name of the file. For example:

    # cd /opt/oracle/product/12c/db_1
    # tar –zcvf /pathname/db1120.tgz .

#### Install and start Oracle Clusterware

Before you can use cloning to create an Oracle RAC home, you must first install and start Oracle Clusterware on the node or nodes to which you want to copy a cloned Oracle RAC home. In other words, you configure an Oracle RAC home that you cloned from a source cluster onto the nodes in a target cluster in the same order that you installed the Oracle Clusterware and Oracle RAC software components on the original nodes.

**Related Topics**

- [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md)
- Deploying Oracle RAC Clone to Nodes in a Cluster
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cloning-oracle-clusterware.md)

### Deploying Oracle RAC Clone to Nodes in a Cluster

After you complete the prerequisite tasks described in "Preparing to Clone Oracle RAC", you can deploy cloned Oracle homes.

Deploy the Oracle RAC database home to a cluster, as follows:

1.  Perform any Oracle RAC preinstallation tasks, as described in your platform-specific Oracle RAC installation guide, to prepare the new cluster nodes, such things as:

    - Specify the kernel parameters.

    - Ensure Oracle Clusterware is active.

    - Ensure that Oracle ASM is active and that at least one Oracle ASM disk group exists and is mounted.

2.  Deploy the Oracle RAC database software, as follows:

    1.  Copy the clone of the Oracle home to all nodes. For example:

            [root@node1 root]# mkdir -p /opt/oracle/product/12c/db
            [root@node1 root]# cd /opt/oracle/product/12c/db
            [root@node1 db]# tar –zxvf /path_name/db1120.tgz

        When providing the home location and `path_name`, the home location can be in the same directory path or in a different directory path from the source home that you used to create the tar.

    2.  If either the `oracle` user or the `oinstall` group, or both is different between the source and destination nodes, then change the ownership of the Oracle Inventory files, as follows:

            [root@node1]# chown -R oracle:oinstall /opt/oracle/product/12c/db

        When you run the preceding command on the Oracle RAC home, it clears `setuid` and `setgid` information from the Oracle binary.

        **Note:**

        You can perform this step at the same time you perform Step 3 and Step 4 to run the `clone.pl` and `$ORACLE_HOME/root.sh` scripts on each cluster node.

3.  Run the `clone.pl` script on each node, which performs the main Oracle RAC cloning tasks, as follows:

    1.  Supply the environment variables and cloning parameters in the `start.sh` script, as described in Table 9-2 and Table 9-3. Because the `clone.pl` script is sensitive to the parameters being passed to it, you must be accurate in your use of brackets, single quotation marks, and double quotation marks.

    2.  Run the script as `oracle` or the user that owns the Oracle RAC software.

    The following table lists and describes the `clone.pl` script parameters:

    Table 9-1 clone.pl Script Parameters

    | Parameter                                                   | Description                                                                                                                                |
    |:------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
    | `ORACLE_HOME=``Oracle_home`                                 | The complete path to the Oracle home you want to clone. If you specify an invalid path, then the script exits. This parameter is required. |
    | `ORACLE_BASE=``ORACLE_BASE`                                 | The complete path to the Oracle base you want to clone. If you specify an invalid path, then the script exits. This parameter is required. |
    | `ORACLE_HOME_NAME= ``Oracle_home_name`` | -defaultHomeName` | The Oracle home name of the home you want to clone. Optionally, you can specify the `-defaultHomeName` flag. This parameter is optional.   |
    | `ORACLE_HOME_USER=``Oracle_home_user`                       | The OracleHomeUser for Windows services. This parameter is applicable to Windows only and is optional.                                     |
    | `OSDBA_GROUP=``group_name`                                  | Specify the operating system group you want to use as the OSDBA privileged group. This parameter is optional.                              |
    | `OSOPER_GROUP=``group_name`                                 | Specify the operating system group you want to use as the OSOPER privileged group. This parameter is optional.                             |
    | `OSASM_GROUP=``group_name`                                  | Specify the operating system group you want to use as the OSASM privileged group. This parameter is optional.                              |
    | `OSBACKUPDBA_GROUP=``group_name`                            | Specify the operating system group you want to use as the OSBACKUPDBA privileged group. This parameter is optional.                        |
    | `OSDGDBA_GROUP=``group_name`                                | Specify the operating system group you want to use as the OSDGDBA privileged group. This parameter is optional.                            |
    | `OSKMDBA_GROUP=``group_name`                                | Specify the operating system group you want to use as the OSKMDBA privileged group. This parameter is optional.                            |
    | `-debug`                                                    | Specify this option to run the `clone.pl` script in debug mode                                                                             |
    | `-help`                                                     | Specify this option to obtain help for the `clone.pl` script.                                                                              |

    The following example shows an excerpt from the `start.sh` script that calls the `clone.pl` script:

        ORACLE_BASE=/opt/oracle
        ORACLE_HOME=/opt/oracle/product/12c/db
        cd $ORACLE_HOME/clone
        THISNODE='host_name'

        E01=ORACLE_HOME=/opt/oracle/product/12c/db
        E02=ORACLE_HOME_NAME=OraDBRAC
        E03=ORACLE_BASE=/opt/oracle
        C01="-O CLUSTER_NODES={node1,node2}"
        C02="-O LOCAL_NODE=$THISNODE"

        perl $ORACLE_HOME/clone/bin/clone.pl $E01 $E02 $E03 $C01 $C02

    The following table lists and describes the environment variables E01, E02, and E03 that are shown in bold typeface in the preceding example:

    Table 9-2 Environment Variables Passed to the clone.pl Script

    | Symbol | Variable           | Description                                                                                                                                          |
    |:-------|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | E01    | `ORACLE_HOME`      | The location of the Oracle RAC database home. This directory location must exist and must be owned by the Oracle operating system group: `oinstall`. |
    | E02    | `ORACLE_HOME_NAME` | The name of the Oracle home for the Oracle RAC database. This is stored in the Oracle Inventory.                                                     |
    | E03    | `ORACLE_BASE`      | The location of the Oracle Base directory.                                                                                                           |

    The following table lists and describes the cloning parameters C01 and C02, that are shown in bold typeface in the preceding example:

    Table 9-3 Cloning Parameters Passed to the clone.pl Script.

    | Variable | Name          | Parameter       | Description                     |
    |:---------|:--------------|:----------------|:--------------------------------|
    | C01      | Cluster Nodes | `CLUSTER_NODES` | Lists the nodes in the cluster. |
    | C02      | Local Node    | `LOCAL_NODE`    | The name of the local node.     |

    The following example shows an excerpt from the `start.bat` script that the user must create that calls the `clone.pl` script:

        set ORACLE_home=C:\oracle\product\12c\db1
        cd %ORACLE_home%\clone\bin
        set THISNODE=%hostname%
        set E01=ORACLE_HOME=%ORACLE_home%
        set E02=ORACLE_HOME_NAME=OraDBRAC
        set E03=ORACLE_BASE=Oracle_Base
        set C01="CLUSTER_NODES={node1,node2}"
        set C02="-O LOCAL_NODE=%THISNODE%"
        perl clone.pl %E01% %E02% %E03% %C01% %C02%

4.  **Note:**

    This step applies to Linux and UNIX installations, only.

    Run the `$ORACLE_HOME/root.sh` as the `root` operating system user as soon as the `clone.pl` procedure completes on the node.

        [root@node1 root]# /opt/oracle/product/12c/db/root.sh -silent

    Note that you can run the script on each node simultaneously:

        [root@node2 root]# /opt/oracle/product/12c/db/root.sh -silent

    Ensure the script has completed on each node before proceeding to the next step.

5.  **Note:**

    You need only run DBCA on one node in the cluster to create Oracle RAC instances on all nodes.

    This step shows how to run DBCA in silent mode and provide response file input to create the Oracle RAC instances.

    The following example creates an Oracle RAC database named ERI on each node, creates database instances on each node, registers the instances in OCR, creates the database files in the Oracle ASM disk group called `DATA`, and creates sample schemas. It also sets the `SYS`, `SYSTEM`, `SYSMAN` and `DBSNMP` passwords to `password`, which is the password for each account:

        [oracle@node1 oracle]$ export ORACLE_HOME=/opt/oracle/product/12c/db
        [oracle@node1 oracle]$ cd $ORACLE_HOME/bin/
        [oracle@node1 bin]$./dbca -silent -createDatabase -templateName General_Purpose.dbc \
        -gdbName ERI -sid ERI \
        -sysPassword password -systemPassword password \
        -sysmanPassword password -dbsnmpPassword password \
        -emConfiguration LOCAL \
        -storageType ASM -diskGroupName DATA \
        -datafileJarLocation $ORACLE_HOME/assistants/dbca/templates \
        -nodelist node1,node2 -characterset WE8ISO8859P1 \
        -obfuscatedPasswords false -sampleSchema true

**Related Topics**

- Preparing to Clone Oracle RAC
- [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md)
- [Oracle Database 2 Day DBA](../admqs/installing-oracle-database-creating-database.md)

### Locating and Viewing Log Files Generated During Cloning

The cloning script runs multiple tools, each of which may generate its own log files.

After the `clone.pl` script finishes running, you can view log files to obtain more information about the cloning process.

The following log files that are generated during cloning are the key log files of interest for diagnostic purposes:

- `Central_Inventory``/logs/cloneActions``timestamp``.log`

  Contains a detailed log of the actions that occur during the Oracle Universal Installer part of the cloning.

- `Central_Inventory``/logs/oraInstall``timestamp``.err`

  Contains information about errors that occur when Oracle Universal Installer is running.

- `Central_Inventory``/logs/oraInstall``timestamp``.out`

  Contains other miscellaneous messages generated by Oracle Universal Installer.

- `$ORACLE_HOME/clone/logs/clone``timestamp``.log`

  Contains a detailed log of the actions that occur before cloning and during the cloning operations.

- `$ORACLE_HOME/clone/logs/error``timestamp``.log`

  Contains information about errors that occur before cloning and during cloning operations.

Table 9-4 describes how to find the location of the Oracle inventory directory.

Table 9-4 Finding the Location of the Oracle Inventory Directory

| Type of System...                           | Location of the Oracle Inventory Directory |
|:--------------------------------------------|:-------------------------------------------|
| All UNIX computers except Linux and IBM AIX | `/var/opt/oracle/oraInst.loc`              |
| IBM AIX and Linux                           | `/etc/oraInst.loc` file.                   |
| Windows                                     | `C:\Program Files\Oracle\Inventory`        |
