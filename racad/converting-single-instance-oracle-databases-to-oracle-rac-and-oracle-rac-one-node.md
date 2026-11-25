Procedures for converting from Oracle Database single-instance databases to Oracle Real Application Clusters (Oracle RAC) and Oracle RAC One Node databases.

The procedures in this chapter assume that your original single-instance database and the target Oracle RAC database are using the same release and running on the same platform. If you are upgrading from an earlier version of Oracle RAC to Oracle RAC 12c, then use Oracle Database Upgrade Assistant (DBUA).

This chapter includes the following topics:

- Administrative Issues for Converting Databases to Oracle RAC

- Converting to Oracle RAC and Oracle RAC One Node Using DBCA

- Preparing to Convert with rconfig and Oracle Enterprise Manager

- Converting Databases to Oracle RAC Using rconfig

- Example of rconfig XML Input Files for ConvertToRAC

- Postconversion Steps

**Note:**

You must use clustered Oracle Automatic Storage Management (Oracle ASM) instances for Oracle RAC databases.

**Related Topics**

- [Oracle Database Options and Their Permitted Features](../dblic/Licensing-Information.md)

### Administrative Issues for Converting Databases to Oracle RAC

You must address administrative considerations before converting single-instance databases to Oracle RAC.

- Backup procedures should be available before converting from a single-instance Oracle Database to Oracle RAC. This includes taking a backup of your existing database before converting to Oracle RAC and being prepared to backup your Oracle RAC database immediately following the conversion.

- For archiving with Oracle RAC environments, the archive file format requires a thread number.

- The archived logs from all instances of an Oracle RAC database are required for media recovery. Because of this requirement, if you archive to a file and you do not use a cluster file system, or some other means to provide shared file systems, then you require a method of accessing the archive logs from all nodes on which the cluster database has instances.

- By default, all database files are migrated to Oracle Managed Files. This feature simplifies tablespace creation, ensures data file location consistency and compliance with Oracle Flexible Architecture rules, and reduces human error with data file management.

### Converting to Oracle RAC and Oracle RAC One Node Using DBCA

You can use Database Configuration Assistant (DBCA) to convert from single-instance Oracle databases to Oracle RAC or Oracle RAC One Node databases.

DBCA automates the configuration of the control file attributes, creates the undo tablespaces and the redo logs, and creates the initialization parameter file entries for cluster-enabled environments. DBCA also configures Oracle Net Services, Oracle Clusterware resources, and the configuration for Oracle RAC database management using Oracle Enterprise Manager or the Server Control utility (SRVCTL).

Before you use DBCA to convert a single-instance database to an Oracle RAC or an Oracle RAC One Node database, ensure that your system meets the following conditions:

- Your system uses supported hardware and operating system software. Your system is configured properly to support an Oracle RAC database.

- The nodes have access to shared storage; for example, either Oracle Cluster File System or Oracle ASM is available and accessible from all nodes. On Linux on POWER systems, ensure that GPFS is available and accessible from all nodes.

- Your applications have no design characteristics that preclude their use with cluster database processing.

If your platform supports a cluster file system, then you can use it for Oracle RAC. You can also convert to Oracle RAC and use a non-shared file system. In either case, Oracle strongly recommends that you use Oracle Universal Installer to install Oracle Database 12c, which sets up the Oracle home and inventory in an identical location on each of the selected nodes in your cluster.

This section includes the following topics:

- Converting Oracle Database Installations to Oracle RAC Using DBCA

- Converting Single Instance on a Cluster to Oracle RAC One Node Using DBCA

- Converting Single Instance on a Cluster to Oracle RAC Using DBCA

**Related Topics**

- [Converting Databases](administering-oracle-rac-one-node.md)

#### Converting Oracle Database Installations to Oracle RAC Using DBCA

To convert from a single-instance Oracle Database that is on a non-clustered computer to Oracle RAC, perform the procedures described in the following sections, and in the order shown:

- Use DBCA to Create an Image of the Single-Instance Database

- Complete the Oracle Clusterware Installation

- Validate the Cluster

- Copy the Preconfigured Database Image

- Install Oracle Database 12c Software with Oracle RAC

##### Use DBCA to Create an Image of the Single-Instance Database

Use DBCA to create a preconfigured image of your single-instance database by using the following procedure:

1.  Navigate to the `bin` directory in `$ORACLE_HOME`, and start DBCA.

2.  At the Welcome page, click Next.

3.  On the Operations page, select Manage Templates, and click Next.

4.  On the Template Management page, select Create a database template and From an existing database (structure as well as data), then click Next.

5.  On the Source Database page, select the database name in the Database instance list, and click Next.

6.  Use SQL to ensure that all pluggable databases (PDBs) are open, as follows:

        SQL> SELECT name, open_mode FROM v$pdbs;

    If any of the PDBs are in a state other than OPEN, then open them using SQL.

7.  On the Template Properties page, enter a name for your template in the Name field. Oracle recommends that you use the database name.

    By default, the template files are generated in the directory `$ORACLE_HOME/assistants/dbca/templates`. You can enter a description of the file in the Description field, and change the template file location in the Template data file field.

    When you have completed the entries, click Next.

8.  On the Location of Database Related Files page, select Maintain the file locations, so that you can restore the database to the current directory structure, and click Finish.

DBCA generates two files: a database structure file (`template_name``.dbc`), and a database preconfigured image file (`template_name``.dfb`).

##### Complete the Oracle Clusterware Installation

Complete the installation of Oracle Clusterware.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)

##### Validate the Cluster

Validate the cluster configuration using Cluster Verification Utility (CVU).

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cluster-verification-utility-reference.md)

##### Copy the Preconfigured Database Image

Copy the preconfigured database image. This includes copying the database structure `*.dbc` file and the database preconfigured image `*.dfb` file (that you used DBCA to create in a previous section) to a temporary location on the node in the cluster from which you plan to run DBCA.

**Related Topics**

- Use DBCA to Create an Image of the Single-Instance Database

##### Install Oracle Database 12c Software with Oracle RAC

1.  Run Oracle Universal Installer to install an Oracle Database with Oracle RAC.

2.  Select Cluster Installation Mode on the Specify Hardware Cluster Installation page of Oracle Universal Installer, and select the nodes to include in your Oracle RAC database.

3.  On the Oracle Universal Installer Database Configuration Types page, select the Advanced installation type.

    After installing the Oracle Database software, Oracle Universal Installer runs postinstallation configuration tools, such as Net Configuration Assistant (NETCA), DBCA, and so on.

4.  On the DBCA Template Selection page, use the template that you copied to a temporary location in the previous section. Use the browse option to select the template location.

    Select the option that you want to deploy. Your choices are the following: Oracle RAC database; Oracle RAC One Node database; or Oracle single-instance database.

5.  After creating the Oracle RAC database, DBCA displays the Password Management page on which you must change the passwords for database users who have SYSDBA and SYSOPER privileges. When DBCA exits, the conversion process is complete.

#### Converting Single Instance on a Cluster to Oracle RAC One Node Using DBCA

Use DBCA to convert a single-instance Oracle Database to Oracle RAC One Node by using the following procedure:

1.  Change directory to `$ORACLE_HOME/bin`.

2.  Start DBCA:

        $ dbca

3.  From the Welcome window, select Oracle RAC One Node database.

4.  Use the template that you selected to deploy in the previous section.

#### Converting Single Instance on a Cluster to Oracle RAC Using DBCA

There are three scenarios in which a single-instance database can exist on a cluster node:

- Scenario 1: The Oracle home for the single-instance database was installed on a cluster node and has Oracle RAC enabled.

- Scenario 2: The Oracle home for the single-instance database was installed on a cluster node, but the Oracle RAC feature is disabled for this Oracle home.

- Scenario 3: The Oracle home for the single-instance database was installed on only the local node in a cluster. This happens when you select the Local Installation option on the Oracle Universal Installer Specify Hardware Cluster Installation page during the Oracle Database 12c installation.

**Related Topics**

- Single-Instance Database on a Cluster Running from an Oracle RAC-Enabled Home
- Single-Instance Database on a Cluster Running from an Oracle RAC-Disabled Home
- Converting Oracle Database Installations to Oracle RAC Using DBCA
- Install Oracle Database 12c Software with Oracle RAC

##### Single-Instance Database on a Cluster Running from an Oracle RAC-Enabled Home

Perform the following procedures to convert a single-instance database on a cluster node running from an Oracle home that has the Oracle RAC option enabled.

1.  Use DBCA to create a preconfigured image of your single-instance database. To perform the conversion manually, shut down the single-instance database.

2.  Add nodes to your cluster. Ensure that all nodes can access the shared storage used by Oracle Clusterware and Oracle RAC.

3.  From the existing Oracle home, extend this home to the new nodes.

4.  From a newly added node, configure the listeners on the additional nodes using NETCA. Choose the same port number and protocol that you used on the existing node. If NETCA displays the existing node in the node list page, then do not select this node, because the listener is already configured on it.

5.  Convert the database using one of the following procedures:

    - Automated Conversion Procedure Using DBCA

    - Manual Conversion Procedure

**Related Topics**

- Use DBCA to Create an Image of the Single-Instance Database
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md)
- [Adding Oracle RAC to Nodes with Oracle Clusterware Installed](adding-and-deleting-oracle-rac-from-nodes-on-linux-and-unix-systems.md)

###### Automated Conversion Procedure Using DBCA

If you used DBCA to create a preconfigured image of your single-instance database as described in a previous section, then perform the following steps to complete the conversion to an Oracle RAC database:

1.  Start DBCA from the initial node. Select the names of the nodes to include as part of your cluster database. On the Template Selection page, select the preconfigured template that you created. Enter the database name and respond to the remaining DBCA prompts.

2.  Specify the shared storage location for the Oracle Database data files.

After creating the Oracle RAC database, DBCA displays the Password Management page on which you must change the passwords for the database users who have SYSDBA and SYSOPER privileges. When DBCA exits, the conversion process is complete.

**Related Topics**

- Use DBCA to Create an Image of the Single-Instance Database
- Manual Conversion Procedure

###### Manual Conversion Procedure

If you did not use DBCA to create a preconfigured image of your single-instance database as described in a previous section, then perform the following steps to complete the conversion:

1.  Create the Optimal Flexible Architecture directory structure on each of the nodes that you have added.

2.  Re-create the control files by running the `CREATE CONTROLFILE` SQL statement with the `REUSE` keyword and specify `MAXINSTANCES` and `MAXLOGFILES`, and so on, as needed for your Oracle RAC configuration. The `MAXINSTANCES` recommended default is 32.

3.  Shut down the database instance.

4.  If your single-instance database was using an SPFILE, then create a temporary parameter file (PFILE) from the SPFILE using the following SQL statement:

        CREATE PFILE='pfile_name' from spfile='spfile_name'

5.  Set the `CLUSTER_DATABASE` parameter to `TRUE`, and set the `INSTANCE_NUMBER` parameter to a unique value for each instance, using the `sid``.``parameter``=``value` syntax.

    If you optimized memory usage on your single-instance database, then adjust the size of the system global area (SGA) to avoid swapping and paging when you convert to Oracle RAC. You should make this adjustment because Oracle RAC requires about 350 bytes for each buffer to accommodate the Global Cache Service (GCS). For example, if you have 10,000 buffers, then Oracle RAC requires approximately 350 multiplied by 10,000 bytes more memory. Therefore, adjust the size of the SGA by changing the `DB_CACHE_SIZE` and `DB_nK_CACHE_SIZE` parameters accordingly.

6.  Start the database instance using the PFILE created in Step 4.

7.  If your single-instance database was using automatic undo management, then create an undo tablespace for each additional instance using the `CREATE UNDO TABLESPACE` SQL statement.

8.  Create redo threads that have at least two redo logs for each additional instance. Enable the new redo threads by using an `ALTER DATABASE` SQL statement. Then, shut down the database instance.

9.  Copy the Oracle password file from the initial node, or from the node on which you are working, to the corresponding location on the additional nodes on which the cluster database will have an instance. Replace the `ORACLE_SID` name in each password file appropriately for each additional instance.

10. Set the `REMOTE_LISTENER` parameter to the single client access name (SCAN) and port.

11. Configure the net service entries for the database and instances, and address entries for the `LOCAL_LISTENER` for each instance and for the `REMOTE_LISTENER` in the `tnsnames.ora` file, and copy the `tnsnames.ora` file to all nodes.

12. Create the SPFILE from the PFILE.

13. Create the `$ORACLE_HOME/dbs/init``sid``.ora` file that contains the following entry, where `spfile_path_name` is the complete path name of the SPFILE:

        spfile='spfile_path_name'

14. On the local node, use SQL\*Plus to run `catclust.sql`. This script creates the dictionary views needed for Oracle RAC databases. For example:

        SQL> start ?/rdbms/admin/catclust.sql

15. Add the configuration for the Oracle RAC or Oracle RAC One Node database and its instance-to-node mapping using SRVCTL.

    1.  To add the configuration of an Oracle RAC database, use the following commands:

            $ srvctl add database -dbname db_name -oraclehome Oracle_home -spfile spfile_path_name
            $ srvctl add instance -dbname db_name -instance inst1_name -node node1_name
            $ srvctl add instance -dbname db_name -instance inst2_name -node node2_name
            ...

    2.  To add the configuration of an Oracle RAC One Node database, use the following command:

            $ srvctl add database -dbname db_name -dbtype RACONENODE -oraclehome Oracle_home
              -spfile spfile_path_name

16. Start the Oracle RAC or Oracle RAC One Node database using SRVCTL:

        srvctl start database -d db_name

After starting the database with SRVCTL, your conversion process is complete. You can run the following SQL statement to see the status of all the instances in your Oracle RAC database:

    SQL> SELECT * FROM v$active_instances;

**Related Topics**

- Use DBCA to Create an Image of the Single-Instance Database
- [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md)

##### Single-Instance Database on a Cluster Running from an Oracle RAC-Disabled Home

You can create a single-instance database on a cluster running from an Oracle home with the Oracle RAC option disabled. To create an Oracle home on a cluster with Oracle RAC disabled, you can select local and non-cluster on the Node Selection Page of Oracle Universal Installer when installing the Oracle Database software. You can also performed a one-node cluster (with Oracle RAC) installation, but later disable the Oracle RAC option.

Perform the following procedures to convert this type of single-instance database to an Oracle RAC or Oracle RAC One Node database:

1.  Use DBCA to create a preconfigured image of your single-instance database as described in a previous section. To perform the conversion manually, shut down the single-instance database.

2.  Change the directory to the `lib` subdirectory in the `rdbms` directory under the Oracle home.

3.  Relink the `oracle` binary by running the following commands:

        make -f ins_rdbms.mk rac_on
        make -f ins_rdbms.mk ioracle

4.  Add nodes to your cluster. Ensure that all nodes can access the shared storage used by Oracle Clusterware and Oracle RAC.

**Related Topics**

- Use DBCA to Create an Image of the Single-Instance Database
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/adding-and-deleting-cluster-nodes.md)

### Preparing to Convert with rconfig and Oracle Enterprise Manager

You can use `rconfig` or Oracle Enterprise Manager to assist with converting a single-instance database installation to an Oracle RAC database.

The first of these, `rconfig`, is a command-line utility. Oracle Enterprise Manager Cloud Control database administration option, Convert to Cluster Database, provides a GUI-based conversion tool. The following sections describe how to use these conversion tools:

- Prerequisites for Converting to Oracle RAC Databases

- Configuration Changes During Oracle RAC Conversion Using rconfig

- Converting Databases to Oracle RAC Using rconfig or Oracle Enterprise Manager

- Converting Databases to Oracle RAC Using Oracle Enterprise Manager

**Note:**

Before you start the conversion, back up your existing database; you should take a backup of your database before starting any major change.

#### Prerequisites for Converting to Oracle RAC Databases

Your Oracle Real Application Clusters (Oracle RAC) environment must meet these prerequisites before you can convert your database.

Before you convert a single-instance database to an Oracle RAC database, ensure that the following conditions are met for each cluster node that you intend to make an Oracle RAC database node:

- Oracle Clusterware 19c is installed, configured, and running.

- Oracle RAC 19c software is installed.

- The Oracle software has the Oracle RAC option enabled.

- Shared storage, either Oracle Cluster File System or Oracle ASM, is available and accessible from all nodes.

- User equivalence exists for the `oracle` account, or the user account used to install the Oracle software.

- If you intend to use Oracle Enterprise Manager, then the Oracle Management Agent on each node is configured and running, and is configured with cluster and host information.

- You have backed up your existing database.

**Note:**

You must use clustered Oracle ASM instances for Oracle RAC databases.

#### Configuration Changes During Oracle RAC Conversion Using rconfig

These changes occur when you convert a single-instance database to Oracle RAC using the `rconfig` utility.

- During the conversion, `rconfig` places the target Oracle RAC database into archive log mode, and enables archiving for the database. If you do not plan to use archive log space, then you can disable archive logging after the conversion has completed.

- For the Shared Storage Type value, if you enter CFS, and you use a cluster file system for your single-instance database storage, then `rconfig` converts the environment to use Oracle Managed Files for database storage, and places the data files in a subdirectory located under the shared storage location.

- During the conversion, `rconfig` moves database files to a specified shared location, and configures them using Oracle Managed Files.

  To avoid using Oracle Managed Files with your converted database, the single-instance database files must be located in a shared file system, and you must indicate that `rconfig` should not move the files.

#### Converting Databases to Oracle RAC Using rconfig or Oracle Enterprise Manager

This list describes scenarios for converting a single-instance Oracle database to an Oracle RAC database.

- Converting a single-instance Oracle Database 19c database to an Oracle RAC 19c database, running out of the same Oracle home and using the same data files as the single-instance database.

  In this scenario, run the `rconfig` utility from the Oracle RAC database home, or use the Convert to RAC option on the single-instance database target of Oracle Enterprise Manager Cloud Control.

- Converting a single-instance database that uses a release of Oracle Database earlier than Oracle Database 19c to an Oracle RAC 19c database, running out of the same Oracle home and using the same data files as the single-instance database

  In this scenario, use Oracle Universal Installer and Database Upgrade Assistant (DBUA) to update the single-instance database to Oracle Database 19c. Then use `rconfig` or the Oracle Enterprise Manager Convert to RAC option, as described in the preceding scenario.

- Converting a single-instance Oracle Database 19c to an Oracle RAC 19c database, running out of a different Oracle home and using the same data files as the single-instance database.

  In this scenario, run the `rconfig` utility in the target database home, or use the Convert to RAC option in the single-instance database target of Oracle Enterprise Manager Cloud Control. Provide the file storage location when prompted.

  **Note:**

  If you specify Oracle home users for both the target database home and the source database home, then the Oracle home user for the target database home must be the same as the Oracle home user for the source database home.

- Converting a single-instance Oracle Database 19c to an Oracle RAC 19c database, running out of a different Oracle home, and where the host on which the single-instance database runs is not a node used by the Oracle RAC database.

  In this scenario, create a clone image of the single-instance database, and move the clone image to a host that is one of the nodes used by the Oracle RAC database. Then use `rconfig` or the Oracle Enterprise Manager Convert to RAC option, as described in the preceding scenario.

#### Converting Databases to Oracle RAC Using Oracle Enterprise Manager

You can use Oracle Enterprise Manager Cloud Control to convert a single-instance database to an Oracle RAC database.

To use this feature, complete the following steps:

1.  Log in to Oracle Enterprise Manager Cloud Control. From the Home page, click the Targets tab.

2.  On the Targets page, click the Databases secondary tab, and click the link in the Names column of the database to convert to Oracle RAC.

3.  On the Database home page, from the Availability menu, select Convert to Cluster Database.

4.  Log in as the database user `SYS` with `SYSDBA` privileges to the database you want to convert, and click Next.

5.  On the Convert to Cluster Database: Cluster Credentials page, provide a user name and password for the `oracle` user and password of the target database to convert. If the target database is using Oracle ASM, then also provide the SYSASM user and password, and then click Next.

6.  On the Hosts page, select the host nodes in the cluster to be cluster members in the installed Oracle RAC database. When you have completed your selection, click Next.

7.  On the Convert to Database: Options page, select whether you want to use the existing listener and port number, or specify a new listener and port number for the cluster. Also provide a prefix for cluster database instances on the cluster.

    When you have finished entering information, click Next, or click Help if you need assistance in deciding how to enter information.

8.  On the Convert to Cluster Database: Shared Storage page, either select the option to use your existing shared storage area, or select the option to have your database files copied to a new shared storage location. Also, decide if you want to use your existing fast recovery area or copy your recovery files to a new fast recovery area using files managed by Oracle Database.

    If you use Oracle ASM, then Oracle recommends that you place the data files and the recovery files in separate failure groups. A failure group is defined by shared hardware, such as a controller shared between two disks, or two disks that are on the same spindle. If two disks share hardware that could fail, making both disks unavailable, then theses disks are said to be in the same failure group. If you do not use Oracle ASM, then Oracle recommends that the data files and the recovery files are stored in separate locations, for example, separate Oracle ASM failure groups, so that a hardware failure does not affect availability.

    When you have finished entering information, click Next, or click Help if you need assistance in deciding how to enter information.

9.  On the Convert to Cluster Database: Review page, review the options you have selected. Click Submit Job to proceed with the conversion. To change any options you have selected, click Back. To cancel the conversion, click Cancel.

10. On the Confirmation page, click View Job to check the status of the conversion.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

### Converting Databases to Oracle RAC Using rconfig

You can use the command-line utility `rconfig` to convert a single-instance database to an Oracle RAC database, or to convert it to an Oracle RAC One Node database, depending on the values you provide in the `ConvertToRAC.xml` file. To use this feature, complete the following steps:

1.  As the `oracle` user, navigate to the directory `$ORACLE_HOME/assistants/rconfig/sampleXMLs`, and open the file `ConvertToRAC.xml` using a text editor, such as `vi`.

2.  Review the `ConvertToRAC.xml` file, and modify the parameters as required for your system. The XML sample file contains comments that provide instructions for how to configure the file. Do NOT put passwords in the XML file. Instead, let the `rconfig` utility prompt you to enter the passwords.

    **Caution:**

    Set the convert option `Convert verify="ONLY"` to perform a test conversion to ensure that a conversion can be completed successfully.
    When you have finished modifying parameters, save the file with a name of the format `file_name``.xml`. Make a note of the name you select.

3.  Navigate to the directory `$ORACLE_HOME/bin`, and use the following command to run the command `rconfig`, where `input.xml` is the name of the XML input file you configured in Step 2:

        rconfig input.xml

    For example, if you create an input XML file called `convert.xml`, then you would use the following command

        $ ./rconfig convert.xml

    The `rconfig` utility will prompt you for the necessary passwords.

**Note:**

The `Convert verify` option in the `ConvertToRAC.xml` file has three options:

- `Convert verify="YES"`: rconfig performs checks to ensure that the prerequisites for single-instance to Oracle RAC conversion have been met before it starts conversion

- `Convert verify="NO"`: rconfig does not perform prerequisite checks, and starts conversion

- `Convert verify="ONLY"` rconfig only performs prerequisite checks; it does not start conversion after completing prerequisite checks

If performing the conversion fails, then use the following procedure to recover and reattempt the conversion:

1.  Attempt to delete the database using the DBCA delete database option.

2.  Restore the source database.

3.  Review the conversion log, and fix any problems reported by `rconfig` that may have caused the conversion failure. The `rconfig` log files are under the `rconfig` directory in `$ORACLE_BASE/cfgtoollogs`.

4.  Reattempt the conversion.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

### Example of rconfig XML Input Files for ConvertToRAC

Review these two examples of an XML `ConvertToRAC` input file for the `rconfig` utility.

**Note:**

Do not include passwords in the XML file. Instead, let the `rconfig` utility prompt you for the passwords.

Example 15-1 Example rconfig ConvertToRAC XML File for Policy-Managed Databases

This example shows an XML input file to convert a single-instance database with Oracle ASM to a policy-managed Oracle RAC database (using server pools) on Oracle ASM storage.

    <?xml version="1.0" encoding="UTF-8"?>
    <n:RConfig xmlns:n="http://www.example.com/rconfig"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xsi:schemaLocation="http://www.example.com/rconfig">
        <n:ConvertToRAC>
    <!-- Verify does a precheck to ensure all pre-requisites are met, before the
     conversion is attempted. Allowable values are: YES|NO|ONLY -->
        <n:Convert verify="YES">
    <!--Specify current OracleHome of non-rac database for SourceDBHome -->
              <n:SourceDBHome>/oracle/product/12.1.0/db_1</n:SourceDBHome>
    <!--Specify OracleHome where the rac database should be configured. It can be same
     as SourceDBHome -->
              <n:TargetDBHome>/oracle/product/12.1.0/db_1</n:TargetDBHome>
    <!--Specify SID of non-rac database and credential. User with sysdba role is
     required to perform conversion -->
                  <n:SourceDBInfo SID="sales">
                <n:Credentials>
                  <n:User>sys</n:User>
                  <n:Role>sysdba</n:Role>
                </n:Credentials>
              </n:SourceDBInfo>
    <!--Specify the list of existing or new server pools which are used by the
     Policy Managed Cluster Database. -->
                  <n:ServerPoolList>
                    <n:ExistingServerPool name="custom"/>
                    <n:NewServerPool name="newpool" cardinality="2"/>
                  </n:ServerPoolList>
    <!--Specify RacOneNode along with servicename to convert database to RACOne
    Node -->
                  <!--n:RacOneNode  servicename="salesrac1service"/-->
    <!--InstancePrefix is not required for Policy Managed database. If specified, it
     will be ignored. Instance names are generated automatically based on db_unique_
    name for Policy Managed dababase.-->
    <!-- Listener details are no longer needed starting 11.2. Database is registered
     with default listener and SCAN listener running from Oracle Grid Infrastructure
     home. -->
    <!--Specify the type of storage to be used by rac database. Allowable values are
     CFS|ASM. The non-rac database should have same storage type. ASM credentials are
     no needed for conversion. -->
              <n:SharedStorage type="ASM">
    <!--Specify Database Area Location to be configured for rac database.If this field
     is left empty, current storage will be used for rac database. For CFS, this field
     will have directory path. -->
                <n:TargetDatabaseArea>+ASMDG</n:TargetDatabaseArea>
    <!--Specify Fast Recovery Area to be configured for rac database. If this field is
     left empty, current recovery area of non-rac database will be configured for rac
     database. If current database is not using recovery Area, the resulting rac
     database will not have a recovery area. -->
                <n:TargetFlashRecoveryArea>+ASMDG</n:TargetFlashRecoveryArea>
              </n:SharedStorage>
            </n:Convert>
        </n:ConvertToRAC>
    </n:RConfig>

Example 15-2 Example rconfig ConvertToRAC XML File for Administrator-Managed Databases

This example shows an XML input file to convert a single-instance database with Oracle ASM to an administrator-managed Oracle RAC database.

    <?xml version="1.0" encoding="UTF-8"?>
    <n:RConfig xmlns:n="http://www.example.com/rconfig"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xsi:schemaLocation="http://www.example.com/rconfig rconfig.xsd">
        <n:ConvertToRAC>
    <!-- Verify does a precheck to ensure all pre-requisites are met, before the
     conversion is attempted. Allowable values are: YES|NO|ONLY -->
        <n:Convert verify="YES">
    <!--Specify current OracleHome of non-rac database for SourceDBHome -->
              <n:SourceDBHome>/oracle/product/12.1.0/db_1</n:SourceDBHome>
    <!--Specify OracleHome where the rac database should be configured. It can be same
     as SourceDBHome -->
              <n:TargetDBHome>/oracle/product/12.1.0/db_1</n:TargetDBHome>
    <!--Specify SID of non-rac database and credential. User with sysdba role is
     required to perform conversion -->
                  <n:SourceDBInfo SID="sales">
                <n:Credentials>
                  <n:User>sys</n:User>
                  <n:Role>sysdba</n:Role>
                </n:Credentials>
              </n:SourceDBInfo>
    <!--Specify the list of nodes that should have rac instances running for the Admin
     Managed Cluster Database. LocalNode should be the first node in this nodelist.
     -->
              <n:NodeList>
                <n:Node name="node1"/>
                <n:Node name="node2"/>
              </n:NodeList>
    <!--Specify RacOneNode along with servicename to convert database to RACOne
    Node -->
    <!--n:RacOneNode  servicename="salesrac1service"/-->
    <!--Instance Prefix tag is optional starting with 11.2. If left empty, it is
     derived from db_unique_name.-->
              <n:InstancePrefix>sales</n:InstancePrefix>
    <!-- Listener details are no longer needed starting 11.2. Database is registered
     with default listener and SCAN listener running from Oracle Grid Infrastructure
     home. -->
    <!--Specify the type of storage to be used by rac database. Allowable values are
     CFS|ASM. The non-rac database should have same storage type. ASM credentials
    are not needed for conversion. -->
              <n:SharedStorage type="ASM">
    <!--Specify Database Area Location to be configured for rac database.If this field
     is left empty, current storage will be used for rac database. For CFS, this
    field will have directory path. -->
                <n:TargetDatabaseArea>+ASMDG</n:TargetDatabaseArea>
    <!--Specify Fast Recovery Area to be configured for rac database. If this field is
     left empty, current recovery area of non-rac database will be configured for rac
     database. If current database is not using recovery Area, the resulting rac
     database will not have a recovery area. -->
                <n:TargetFlashRecoveryArea>+ASMDG</n:TargetFlashRecoveryArea>
              </n:SharedStorage>
            </n:Convert>
        </n:ConvertToRAC>
    </n:RConfig>

### Postconversion Steps

After completing the conversion, follow the recommendations for configuring Oracle RAC environments.

- Follow the recommendations for using load balancing and transparent application failover as described in a previous chapter.

- Use locally managed tablespaces instead of dictionary managed tablespaces to reduce contention and manage sequences in Oracle RAC as described in Oracle Database Administrator’s Guide

- Follow the guidelines for using automatic segment space management as described in Oracle Database Administrator’s Guide

The buffer cache and shared pool capacity requirements in Oracle RAC are slightly greater than the requirements for single-instance Oracle databases. Therefore, you should increase the size of the buffer cache by about 10%, and the size of the shared pool by about 15%.

**Related Topics**

- [Workload Management with Dynamic Database Services](workload-management-with-dynamic-database-services.md)
- [About Locally Managed Tablespaces](../admin/managing-tablespaces.md)
- [Specifying Segment Space Management in Locally Managed Tablespaces](../admin/managing-tablespaces.md)
