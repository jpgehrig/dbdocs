## AutoUpgrade and Oracle Database Configuration Options

When you run AutoUpgrade, it determines the type of database (Oracle Database, Oracle Database Standalone with Oracle ASM, or Oracle RAC), and performs an upgrade for that type of database

- Non-CDB to PDB Upgrade Guidelines and Examples
  Before conversion, back up your datafiles and database, and follow the guidelines for your source Oracle Database release.
- AutoUpgrade Process Flow for Oracle Grid Infrastructure Managed Configurations
  When AutoUpgrade detects Oracle RAC or Oracle RAC One Node, it proceeds to perform upgrade steps required for all Oracle RAC instances.
- Oracle RAC Requirements for Upgrade with AutoUpgrade
  To determine if AutoUpgrade can upgrade your Oracle Real Application Clusters (Oracle RAC) or Oracle RAC One Node database, review the use case requirements.
- Preparing for Oracle RAC Upgrades Using AutoUpgrade
  Review to find what information you must collect before the upgrade, and other upgrade preparation guidelines.
- AutoUpgrade and Oracle Data Guard
  The AutoUpgrade utility that you download from My Oracle Support can simplify the upgrade process for your primary and secondary databases configured for Oracle Data Guard.
- How to Run AutoUpgrade Using the Fast Deploy Option
  To minimize downtime, you can upgrade your database by running AutoUpgrade using the Fast Deploy option.
- How to Perform an Unplug-Plug Upgrade of an Encrypted PDB
  Learn how you can perform unplug-plug upgrades of encrypted PDBs using the AutoUpgrade Utility.
- How to Perform a Non-CDB to PDB Conversion of an Encrypted PDB
  With AutoUpgrade 22.1 and later updates, AutoUpgrade simplifies the upgrade and conversion of Oracle Databases that use Transparent Data Encryption (TDE).
- How to Use a Standby Database as Source for Refreshable Clone PDBs
  To reduce load on the primary database for upgrades, you can use a snapshot standby database as the source for a refreshable clone PDBs to reduce load on the primary database.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### Non-CDB to PDB Upgrade Guidelines and Examples

Before conversion, back up your datafiles and database, and follow the guidelines for your source Oracle Database release.

To ensure that you can recover from a failed conversion, Oracle strongly recommends that allow time in your upgrade plan to implement your backup strategy before you use AutoUpgrade to perform a non-CDB upgrade and conversion.

#### Guidelines for Upgrade Planning

The non-CDB-to-PDB conversion and upgrade process is not recoverable. To ensure a proper upgrade and conversion, and to reduce unexpected downtime, Oracle strongly recommends that you address any error conditions found during the analyze phase.

If you use the `target_pdb_copy_option` in your configuration file to create copies of your data files, then your existing database is available as a backup. This is a safe option, but will require additional time and disk space. If you do not set the `target_pdb_copy_option` in your AutoUpgrade configuration file, then the database conversion uses the same file location and file names that are used with existing database files. To prevent potential data loss, ensure that your data is backed up, and consider your file placement plans before starting AutoUpgrade.

#### GRP and Upgrades from Non-CDB to Multitenant Architecture

- During the upgrade, AutoUpgrade creates a guaranteed restore point (GRP) that is available only in the context of the upgrade stage of the AutoUpgrade Deploy workflow. To ensure against any potential data loss, you must implement your backup strategy before starting AutoUpgrade.
- Database conversion from non-CDB to the multitenant architecture is performed during the AutoUpgrade Drain stage. After this stage is complete, the GRP that AutoUpgrade creates is removed, and it is not possible to use the AutoUpgrade `restore` command to restore the database. In the event that you require a recovery to the earlier non-CDB Oracle Database release, you must be prepared to recover the database manually.

Example 3-4 Upgrading and Converting a Non-CDB to Oracle Database 19c Using Multitenant Architecture

During the Deploy conversion and upgrade workflow, AutoUpgrade creates a GRP, and runs the Prefixup stage. If any part of the Deploy workflow up to the Prefixup stage completion fails, then AutoUpgrade can restore the database back to the GRP created at the start of the deployment,

However, after the Prefixup stage is complete, the upgraded database is plugged in to the target release Oracle Database container database (CDB) to complete conversion. As soon as the non-CDB is plugged into the CDB, the GRP is no longer valid, and is dropped.

If anything goes wrong during the plug-in, and you did not choose to use the `target_pdb_copy_option` in your configuration file to create copies of your data files, then be aware that AutoUpgrade cannot recover and restore the database. In that event, you must restore the database manually.

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### AutoUpgrade Process Flow for Oracle Grid Infrastructure Managed Configurations

When AutoUpgrade detects Oracle RAC or Oracle RAC One Node, it proceeds to perform upgrade steps required for all Oracle RAC instances.

When you start AutoUpgrade, it detects when Oracle Database is managed with Oracle Grid Infrastructure, either with Oracle Real Application Clusters (Oracle RAC), or an Oracle RAC One Node configuration. Before you start AutoUpgrade, you must already have upgraded Oracle Grid Infrastructure to a release equal to or more recent than the Oracle Database release to which you are upgrading.

**Note:**

Choosing this upgrade option requires downtime of the clustered database while AutoUpgrade completes upgrades of database instances, and system configuration. If you use Oracle Enterprise Manager, then you must reconfigure it after the upgrade.

During an upgrade, when AutoUpgrade detects that the Oracle Database is an Oracle Clusterware resource, it performs the following steps, in sequence:

1.  AutoUpgrade shuts down the database, or all instances of the Oracle RAC database.
2.  AutoUpgrade disables Oracle RAC and Oracle RAC One Node services.
3.  If the Oracle Clusterware resource is Oracle RAC, then AutoUpgrade disables the Oracle RAC database resource in Oracle Clusterware.
4.  AutoUpgrade starts up the Oracle Database instance:
    - If the instance was an Oracle RAC instance, then AutoUpgrade starts the local Oracle Database instance in upgrade mode, with `CLUSTER_DATABASE` set to false.
    - If the instance was a single-instance Oracle Database, then it starts up the instance in normal mode.
5.  AutoUpgrade upgrades the local Oracle Database Oracle home binaries to the new Oracle Database release binaries.
6.  During an upgrade, AutoUpgrade runs `srvctl upgrade database` from the local Oracle Database home, and for Oracle RAC, upgrades the configuration of the Oracle RAC services to the new release. During a patch operation, instead of `srvctl upgrade database`, AutoUpgrade runs `srvctl modify database`.
7.  AutoUpgrade enables Oracle Grid Infrastructure services for the database, using `srvctl enable database`. For Oracle RAC instances, it changes `CLUSTER_DATABASE` to true.
8.  AutoUpgrade recreates the server parameter file (`SPFILE`) with the updated parameters, and the parameter options you previously set for your environment that are not affected by the release upgrade.
9.  If the Oracle Database is an instance of an Oracle RAC database, then AutoUpgrade repeats this process on each other cluster member node, until all instances of the Oracle RAC database are upgraded.
10. AutoUpgrade starts up the Oracle Database. For Oracle RAC, it starts all instances of Oracle Real Application Clusters on the cluster.

During a patch operation, the process is similar, with the following differences:

1.  AutoUpgrade shuts down the database, or all instances of the Oracle RAC database.

2.  AutoUpgrade disables Oracle RAC and Oracle RAC One Node services.

3.  If the Oracle Clusterware resource is Oracle RAC, then AutoUpgrade disables the Oracle RAC database resource in Oracle Clusterware.

4.  AutoUpgrade starts up the Oracle Database instance:

    - If the instance was an Oracle RAC instance, then AutoUpgrade starts the local Oracle Database instance in upgrade mode, with `CLUSTER_DATABASE` set to false.
    - If the instance was a single-instance Oracle Database, then it starts up the instance in normal mode.

    In comparison to an upgrade operation, patch maintenance also performs the following steps in this stage, so that the database is ready to start up after the drain stage is complete:

    - AutoUpgrade upgrades the local Oracle Database Oracle home binaries to the new Oracle Database release binaries.
    - AutoUpgrade runs `srvctl modify database` from the local Oracle Database home, and patches the database. For Oracle RAC, it also patches the configuration of the Oracle RAC services to the new release update.
    - AutoUpgrade enables Oracle Grid Infrastructure services for the database, using `srvctl enable database`. F
    - AutoUpgrade recreates the server parameter file (`SPFILE`) with the updated parameters, and the parameter options you previously set for your environment that are not affected by the release patch maintenance.
    - If the Oracle Database is an instance of an Oracle RAC database, then AutoUpgrade repeats this process on each other cluster member node, until all instances of the Oracle RAC database are upgraded.
    - AutoUpgrade starts up the Oracle Database. For Oracle RAC, it starts all instances of Oracle Real Application Clusters on the cluster.

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### Oracle RAC Requirements for Upgrade with AutoUpgrade

To determine if AutoUpgrade can upgrade your Oracle Real Application Clusters (Oracle RAC) or Oracle RAC One Node database, review the use case requirements.

#### Requirements for Using AutoUpgrade with Oracle RAC Databases

You can use AutoUpgrade to perform upgrades of Oracle RAC or Oracle Real Application Clusters One Node systems. However, your system must meet all of the following requirements:

- Using AutoUpgrade with Oracle RAC deployments is now support for both POSIX systems and Microsoft Windows systems.
- For Microsoft Windows only, AutoUpgrade has integrated the Oracle RAC API, so there is no requirement to have SSH enabled on the Windows platforms. AutoUpgrade is supported with releases 19, 21 and 23 of Oracle Grid Infrastructure on Microsoft Windows. Database upgrades and patching are supported for databases that run in the supported Oracle Grid Infrastructure releases. Oracle recommends using the AutoUpgrade Windows Credentials feature as a complete solution when upgrading or patching in a Microsoft Windows Oracle RAC environment.
- Must meet the upgrade requirements to upgrade to the new Oracle Database release.
- Must be registered and managed through the Server Control (`SRVCTL`) utility.

#### Required Tasks for Database Administrators to Use AutoUpgrade

As the database administrator, you must complete the following tasks:

- Create an adequate backup strategy to prevent data loss from any problems resulting from the upgrade.
- Configure Listener and Transparent Network Substrate (TNS) files, both for local `tnsnames.ora` and SCAN listeners, if needed.
- Configure Oracle Wallet certificates and management (if needed), and configure for automatic login.

**Related Topics**

- [Enabling Full Deployments for AutoUpgrade](enabling-full-deployments-autoupgrade.md)

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### Preparing for Oracle RAC Upgrades Using AutoUpgrade

Review to find what information you must collect before the upgrade, and other upgrade preparation guidelines.

To use AutoUpgrade for Oracle Real Application Clusters (Oracle RAC) upgrades, ensure that you collect information as needed before the upgrade, and be prepared to provide information during the upgrade.

#### Scope Limits for AutoUpgrade and Oracle RAC

AutoUpgrade does not perform upgrades of the Oracle Clusterware and Oracle ASM components of Oracle Grid Infrastructure. Before you start AutoUpgrade to upgrade your Oracle RAC database, you must first complete a successful Oracle Grid Infrastructure upgrade to the new release.

#### File System Preparation Before Upgrades Using AutoUpgrade

AutoUpgrade can identify the `PFILE` and `SPFILE` files shared on Oracle ASM. AutoUpgrade recreates the SPFILE as part of the upgrade. If you are sharing an `SPFILE` on the cluster using Oracle ASM, then you do not need to complete this procedure.

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### AutoUpgrade and Oracle Data Guard

The AutoUpgrade utility that you download from My Oracle Support can simplify the upgrade process for your primary and secondary databases configured for Oracle Data Guard.

- How AutoUpgrade Performs Oracle Data Guard Upgrades
  AutoUpgrade can detect Oracle Data Guard configurations, and defer shipping logs to standby databases configured for the primary database.
- Steps AutoUpgrade Completes for Oracle Data Guard Upgrades
  The steps that AutoUpgrade completes vary, depending on whether standby databases are managed manually, or through Data Guard Broker.
- Steps After the Primary Database is Upgraded
  For Oracle Data Guard upgrades, after you upgrade the primary database you must complete these procedures.

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

#### How AutoUpgrade Performs Oracle Data Guard Upgrades

AutoUpgrade can detect Oracle Data Guard configurations, and defer shipping logs to standby databases configured for the primary database.

AutoUpgrade automatically detects the presence of an Oracle Data Guard deployment, and whether that deployment is configured manually, or uses Data Guard Broker to manage and monitor Oracle Data Guard configurations.

When you set the parameter `defer_standby_log_shipping` to `no` (the default) in the configuration file, AutoUpgrade can defer the log-shipping to configured standby databases, both when Oracle Data Guard is configured manually, and when Oracle Data Guard is configured through Data Guard Broker.

##### Preparation Before AutoUpgrade Upgrades of Databases with Oracle Data Guard

Before you begin the upgrade, to be prepared in case of a failure during the primary database upgrade, or in case the primary database must be reverted to the source Oracle home, ensure that your standby databases are protected and recoverable.

**Parent topic:** AutoUpgrade and Oracle Data Guard

#### Steps AutoUpgrade Completes for Oracle Data Guard Upgrades

The steps that AutoUpgrade completes vary, depending on whether standby databases are managed manually, or through Data Guard Broker.

For Oracle Data Guard earlier release (**source**) databases where Oracle Data Guard is managed manually, or through Data Guard Broker, to manage log-shipping to standby databases, you can set `defer_standby_log_shipping=yes` in your AutoUpgrade configuration file (the default is `no`). However, the specific actions that AutoUpgrade takes vary, depending on how you manage standby databases.

**Note:**

For standby databases managed either manually or through Data Guard Broker, after the upgrade completes, you must run `ENABLE DATABASE ``database-name;` on each of the standby archive log destinations after successful upgrade on the primary database, and perform all steps needed to have standby databases upgraded through the redo log apply.

##### Manually Managed Oracle Data Guard Standby Databases

For Oracle Data Guard standby databases supported for direct upgrade, AutoUpgrade places in `DEFER` mode all `VALID` and `ENABLED` standby archive log destinations before starting the upgrade process for both manually managed and Data Guard Broker managed standby databases.

##### Data Guard Broker-Managed Oracle Data Guard Standby Databases

For Oracle Database releases supported for direct upgrade with Oracle Data Guard standby databases that are managed using Data Guard Broker, AutoUpgrade completes the following actions:

- The primary database state is set to `TRANSPORT-OFF` to all standby databases configured with Data Guard Broker
- The Data Guard Broker files are copied from the source Oracle home to the target Oracle home.

**Note:**

If the Data Guard Broker files are located outside of the Oracle home, then files are not found and copied.

**Parent topic:** AutoUpgrade and Oracle Data Guard

#### Steps After the Primary Database is Upgraded

For Oracle Data Guard upgrades, after you upgrade the primary database you must complete these procedures.

- Ensure that redo transport is enabled on the primary database, so that the upgrade is applied to the standby databases.
- Check that the archives are applied, and that there is a minimal gap. Oracle recommends that Apply Lag and Transport Lag is not bigger than 5 minutes.

Example 3-5 Checking Redo Transport Service Status

To check the status of the redo transport services on the primary database, use the Data Guard broker command-line interface (`DGMGRL`) `LogXptStatus` monitorable property. For example:

    DGMGRL> SHOW DATABASE 'sales1' 'LogXptStatus' ;

Example 3-6 Checking Apply Lag and Transport Lag

To check that the archives are applied, and verify that Apply Lag and Transport Lag is not bigger than 5 minutes, log in to the primary database and submit a SQL query similar to the following:

    [oracle]$ sqlplus / as sysdba
    SYS@sales1>

    SET LINESIZE 200
    COL VALUE FOR A30
    SELECT NAME,VALUE,TIME_COMPUTED,DATUM_TIME FROM V$DATAGUARD_STATS WHERE NAME LIKE '%lag';

The result should be similar to this output:

    NAME VALUE TIME_COMPUTED DATUM_TIME
    -------------- -------------- --------------------- --------------------
    transport lag +00 00:00:00 timestamp timestamp
    apply lag +00 00:01:07 timestamp timestamp

**Related Topics**

- [Scenario 13: Monitoring a Data Guard Configuration](../dgbkr/examples-using-data-guard-broker-DGMGRL-utility.md)

**Parent topic:** AutoUpgrade and Oracle Data Guard

### How to Run AutoUpgrade Using the Fast Deploy Option

To minimize downtime, you can upgrade your database by running AutoUpgrade using the Fast Deploy option.

Starting with AutoUpgrade 21.2, if your applications require minimal downtime, you can now upgrade with less downtime by using Fast Deploy. With the Fast Deploy option, you can run the prechecks and prefixups while the database is still online. After the fixups run on the source database, you can then run AutoUpgrade in Deploy mode, and skip the prechecks and prefixups stages, so that only the actual upgrade requires downtime.

**Note:**

Oracle recommends that you run AutoUpgrade using standard Analyze and Deploy modes. If you choose to use the Fast Deploy method, then be aware that there is a small risk that new issues can develop in the time duration after you run AutoUpgrade in the preupgrade Analyze mode and before you run AutoUpgrade in Upgrade mode, which can cause a problem. Assess that risk, and take precautions accordingly.

1.  Create your AutoUpgrade configuration file, providing information about your source and target systems, and your upgrade preferences. In the steps that follow, that file name is `myconfig.cfg`.

2.  Analyze the database using Analyze mode.

        – java -jar autoupgrade.jar -config myconfig.cfg -mode analyze

3.  Run the preupgrade fixups using Fixups mode.

        – java -jar autoupgrade.jar -config myconfig.cfg -mode fixups

4.  Upgrade the database using Upgrade mode.

        – java -jar autoupgrade.jar -config myconfig.cfg -mode upgrade

    As this command runs, the database can experience downtime, because databases being upgraded are opened in `UPGRADE` mode in the target Oracle home.

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### How to Perform an Unplug-Plug Upgrade of an Encrypted PDB

Learn how you can perform unplug-plug upgrades of encrypted PDBs using the AutoUpgrade Utility.

**Caution:**

If you choose to specify the directory for AutoUpgrade to create with `global.keystore`, then be aware that it contains a software keystore. It should be protected using the same security best practices as you use with the TDE keystore files.

To perform upgrades of encrypted PDBs, AutoUpgrade requires loading the password for the TDE keystore into its own secure keystore. To load the passwords, you set the AutoUpgrade global configuration file parameter `keystore` in your configuration file, and run AutoUpgrade using the command-line parameter `load_password`. This parameter must be used in conjunction with the `-config` parameter. It takes no arguments. Instead, it starts an interactive prompt with specific commands that enable you to provide information required for the keystore. AutoUpgrade stores the passwords you load securely during the upgrade, and uses those passwords when needed.

**Note:**

If the database is using an Oracle Secure External Password Store (SEPS), and a TDE keystore password is required, then AutoUpgrade uses the `IDENTIFIED BY EXTERNAL STORE` clause, so it does not require loading passwords into the AutoUpgrade password keystore. However, if all databases are configured with a Secure External Password Store, then you still need to define `global.keystore` in your configuration file.

The AutoUpgrade keystore is similar to other keystores that Oracle Database uses. You have the option to create it as an auto-login keystore. For example, if the external keystore is `ewallet.p12` AutoUpgrade creates an auto-login keystore `cwallet.sso`, which is used to open the `ewallet.p12` keystore.

Before you begin to upgrade the encrypted PDB, the following must be true:

- AutoUpgrade must be version 22.2 or later. Oracle strongly recommends that you always download and run the latest version of AutoUpgrade.
- You must use an external TDE keystore
- You have to have available to you the external keystore password of the source and target CDB.

Example 3-7 Upgrading an Encrypted PDB with an Unplug Plug Upgrade Using AutoUpgrade

In the following example, an Oracle Database 12c Release 2 (12.2) PDB using Transparent Data Encryption (TDE) is upgraded to Oracle Database 19c, using the AutoUpgrade `load_password` command option with the AutoUpgrade configuration file keystore parameter to provide a secure store for the TDE keys during the upgrade.

1.  Ensure that you have the latest version of AutoUpgrade:

        $ java -jar autoupgrade.jar -version

    If the AutoUpgrade version is an earlier release, then download the most recent version of AutoUpgrade from My Oracle Support AutoUpgrade Tool (Doc ID 2485457.1)

2.  Create your AutoUpgrade configuration file. In this example, the configuration file `PDB1.cfg` is created with the path to the keystore, which is specified in the `admin` folder under the Oracle base directory, in the path `/u01/app/oracle/admin/autoupgrade/keystore`. The source CDB is `CDB1`,and the target CDB is `CDB2`:

        global.autoupg_log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade
        global.keystore=/u01/app/oracle/admin/autoupgrade/keystore
        upg1.log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade/DB12
        upg1.source_home=/u01/app/oracle/product/12.2.0/dbhome_1
        upg1.target_home=/u01/app/oracle/product/19.1.0/dbhome_1
        upg1.sid=CDB1
        upg.pdbs=PDB1
        upg1.target_cdb=CDB2

    **Note:**

    If you do not specify a keystore location, and an AutoUpgrade keystore has not been created previously, then AutoUpgrade creates the AutoUpgrade keystore for you.

3.  Run AutoUpgrade in Analyze mode:

        $ java -jar autoupgrade.jar -config PDB1.cfg -mode analyze

    The summary report indicates that TDE keystore passwords are needed before starting the upgrade (`TDE_PASSWORDS_REQURED`):

        [Stage Name]    PRECHECKS
        [Status]        FAILURE
        [Start Time]    2022-03-29 07:58:52
        [Duration]
        [Log Directory] /u01/app/oracle/cfgtoollogs/autoupgrade/PDB1/CDB1/100/prechecks
        [Detail]        /u01/app/oracle/cfgtoollogs/autoupgrade/PDB1/CDB1/100/prechecks/cdb1_preupgrade.log
                Check failed for PDB1, manual intervention needed for the below checks
                [TDE_PASSWORDS_REQUIRED]

4.  Add the TDE keystore passwords into the AutoUpgrade keystore:

        $ java -jar autoupgrade.jar -config PDB1.cfg -load_password

    The first time you run AutoUpgrade with the `-load_password` command option, you are prompted to create a password for the AutoUpgrade keystore, where TDE passwords can be stored securely:

        Starting AutoUpgrade Password Loader - Type help for available options
        Creating new keystore - Password required
        Enter password:
        Enter password again:
        Keystore was successfully created

    If do not use a SEPS keystore, then AutoUpgrade prompts you to add the TDE keystore passwords for the databases specified with `source_home` in your configuration file to AutoUpgrade's own keystore, where that database requires a TDE keystore password. This is what we have specified in the configuration file example.

    In the following example, the source and target TDE keystore passwords are loaded:

        TDE> ADD CDB1
        Enter your secret/Password:
        Re-enter your secret/Password:

        TDE> ADD CDB2
        Enter your secret/Password:
        Re-enter your secret/Password:

    Confirm that the passwords are loaded:

        TDE> LIST
        +---------------+-----------------+-----------------+--------------+----------------------+
        |ORACLE_SID     |Action Required  |TDE Password     |SEPS Status   |Active Wallet Type    |
        +---------------+-----------------+-----------------+--------------+----------------------+
        | CDB1          |                 | Verified        | Inactive     | Auto-login           |
        | CDB2          |                 | Verified        | Inactive     | Any                  |
        +---------------+-----------------+-----------------+--------------+----------------------+

    When the `Action Required` column is empty, the TDE passwords are available for the upgrade.

    If you use a SEPS keystore on the source CDB or target CDB, then AutoUpgrade automatically detects the SEPS keystore as the source for the TDE password. AutoUpgrade uses the `IDENTIFIED BY EXTERNAL STORE` clause, and does not need to load the TDE keystore passwords to the AutoUpgrade keystore. Again, the TDE LIST command should show an empty `Action Required` column:

        TDE> LIST
        +--------------+------------------+-------------------------+--------------+---------------------+
        |ORACLE_SID    |Action Required    | TDE Password           |SEPS Status   |Active Wallet Type   |
        +--------------+-------------------+------------------------+--------------+---------------------+
        | CDB1         |                   |No password loaded      | Verified     | Any                 |
        | CDB2         |                   |No password loaded      | Verified     | Any                 |
        +--------------+-------------------+------------------------+--------------+---------------------+

    Both options can be used in the same configuration file. For example, if you do not use a SEPS keystore for the source non-CDB database, but you do use a SEPS keystore for the target CDB, then you only need to load a password for the source non-CDB.

5.  Save the TDE passwords into the AutoUpgrade keystore. (Optional): In this example, we will convert the keystore to an auto-login keystore:

        TDE> save
        Convert the keystore to auto-login [YES|NO] ? YES
        TDE> exit

6.  Analyze the PDB again:

        $ java -jar autoupgrade.jar -config PDB1.cfg -mode analyze

    Review the report and confirm all issues are resolved.

7.  Start the upgrade and conversion:

        $ java -jar autoupgrade.jar -config PDB1.cfg -mode deploy

8.  AutoUpgrade proceeds to upgrade `PDB1` on the target Oracle Database, using the TDE passwords as needed to complete the upgrade. Because in this example we have configured AutoUpgrade to create an AutoUpgrade auto-login keystore, and access the TDE passwords using its own secure keystore, you are not prompted to provide TDE passwords during the upgrade.

**Related Topics**

- [Managing the Secure External Password Store for Password Credentials](../dbseg/configuring-authentication.md)
- [Upgrading an Encrypted PDB](https://dohdatabase.com/2022/03/31/upgrading-an-encrypted-pdb/)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### How to Perform a Non-CDB to PDB Conversion of an Encrypted PDB

With AutoUpgrade 22.1 and later updates, AutoUpgrade simplifies the upgrade and conversion of Oracle Databases that use Transparent Data Encryption (TDE).

To protect sensitive information during upgrades while simplifying the upgrade process, you can use the AutoUpgrade global configuration file parameter `keystore`, and the AutoUpgrade command-line parameter `load_password` to load TDE passwords securely into the AutoUpgrade keystore, and use those passwords when needed.

Before you can use the AutoUpgrade keystore, you specify the location of the external password store in your AutoUpgrade configuration file using `global.keystore`.

**Note:**

If you specify the AutoUpgrade keystore path, then that path should be different from any other file path you specify in AutoUpgrade, so that the keystore is not in any log file location. If the AutoUpgrade keystore path directory does not exist, then AutoUpgrade automatically creates it..

If the database is using an Oracle Secure External Password Store (SEPS), and a TDE keystore password is required, then AutoUpgrade uses the `IDENTIFIED BY EXTERNAL STORE` clause, so it does not require loading passwords into the AutoUpgrade password keystore. However, if all databases are configured with a Secure External Password Store, you still need to define `global.keystore` in your configuration file.

Example 3-8 Upgrading a Database Using TDE and Converting from Non-CDB to PDB

In the following example, an Oracle Database 12c Release 2 (12.2) non-CDB database using Transparent Data Encryption (TDE) is upgraded to Oracle Database 19c and converted to a PDB, using the AutoUpgrade `load_password` command option with the AutoUpgrade configuration file keystore parameter to provide a secure store for the TDE keys during PDB conversion and upgrade.

1.  Ensure that you have the latest version of AutoUpgrade:

        $ java -jar autoupgrade.jar -version

    If the AutoUpgrade version is an earlier release, then download the most recent version of AutoUpgrade from My Oracle Support AutoUpgrade Tool (Doc ID 2485457.1)

2.  Create your AutoUpgrade configuration file. In this example, the path to the keystore is specified in the admin folder under the Oracle base directory, in the path `/u01/app/oracle/admin/autoupgrade/keystore`:

        global.autoupg_log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade
        global.keystore=/u01/app/oracle/admin/autoupgrade/keystore
        upg1.log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade/DB12
        upg1.source_home=/u01/app/oracle/product/12.2.0
        upg1.target_home=/u01/app/oracle/product/19.1.0
        upg1.sid=DB12
        upg1.target_cdb=CDB2

3.  Run AutoUpgrade in Analyze mode:

        $ java -jar autoupgrade.jar -config DB12.cfg -mode analyze

    The summary report indicates that no additional preupgrade tasks need to be completed before starting the upgrade:

        [Stage Name]    PRECHECKS
        [Status]        SUCCESS
        [Start Time]    2022-03-30 10:28:38
        [Duration]
        [Log Directory] /u01/app/oracle/cfgtoollogs/autoupgrade/DB12/DB12/100/prechecks
        [Detail]        /u01/app/oracle/cfgtoollogs/autoupgrade/DB12/DB12/100/prechecks/db12_preupgrade.log
                        Check passed and no manual intervention needed

    If the `TDE_PASSWORDS_REQUIRED` check fails, then load the TDE password:

        $ java -jar autoupgrade.jar -config DB12.cfg -load_password

    The first time you run AutoUpgrade with the `-load_password` command option, if AutoUpgrade requires a TDE password to perform the upgrade, then you are prompted to create a password for the AutoUpgrade keystore, where the TDE password can be stored securely:

        Starting AutoUpgrade Password Loader - Type help for available options
        Creating new keystore - Password required
        Enter password:
        Enter password again:
        Keystore was successfully created

    If do not use a SEPS keystore, then AutoUpgrade prompts you to add the TDE keystore passwords for the databases specified with `source_home` in your configuration file to AutoUpgrade's own keystore, where that database requires a TDE keystore password. This is what we have specified in the configuration file example.

    In the following example, the source and target TDE keystore passwords are loaded:

        TDE> ADD DB12
        Enter your secret/Password:
        Re-enter your secret/Password:

        TDE> ADD CDB2
        Enter your secret/Password:
        Re-enter your secret/Password:

4.  To check the TDE configuration, you can run AutoUpgrade again using the `-load_password` command parameter. This time, because the password is already loaded, the TDE console prompt appears. Run the TDE console `list` command to check the TDE configuration:

        $ java -jar autoupgrade.jar -config DB12.cfg -load_password

        TDE> list
        +----------+---------------+------------------+-----------+------------------+
        |ORACLE_SID|Action Required|   TDE Password   |SEPS Status|Active Wallet Type|
        +----------+---------------+------------------+-----------+------------------+
        |      CDB2|               |No password loaded|   Verified|               Any|
        |      DB12|               |No password loaded|    Unknown|        Auto-login|
        +----------+---------------+------------------+-----------+------------------+

    In the table output for the list command, the `Action Required` column is empty. This result verifies that you have provided the TDE keystore password. In the `SEPS Status` column, AutoUpgrade reports that it checked the password storage access on the target Oracle Database, `CDB2`, and confirms that the password works. Because the TDE console functionality to check the password was a feature added in Oracle Database 19c, AutoUpgrade is unable to confirm the password check for TDE on Oracle Database 12c Release 2 (12.2), so the result `Unknown` is expected.

    If you use a SEPS keystore on the source CDB or target CDB, then AutoUpgrade automatically detects the SEPS keystore as the source for the TDE password. AutoUpgrade uses the `IDENTIFIED BY EXTERNAL STORE` clause, and does not need to load the TDE keystore passwords to the AutoUpgrade keystore. Again, the TDE LIST command should show an empty `Action Required` column.

    Both options can be used in the same configuration file. For example, if you do not use a SEPS keystore for the source non-CDB database, but you do use a SEPS keystore for the target CDB, then you only need to load a password for the source non-CDB.

5.  Start the upgrade and conversion:

        $ java -jar autoupgrade.jar -config DB12.cfg -mode deploy

6.  AutoUpgrade proceeds to upgrade and convert the source non-CDB Oracle Database to a PDB on the target Oracle Database, using the TDE passwords as needed to complete the upgrade.

**Caution:**

As with any other Oracle Database keystore, protect the AutoUpgrade keystore files:

- Apply restrictive file system permissions
- Audit access
- Back up the keystore

**Related Topics**

- [Managing the Secure External Password Store for Password Credentials](../dbseg/configuring-authentication.md)
- [AutoUpgrade and Secure External Password Store Enables Complete Automation](https://dohdatabase.com/2022/04/04/autoupgrade-and-secure-external-password-store-enables-complete-automation/)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options

### How to Use a Standby Database as Source for Refreshable Clone PDBs

To reduce load on the primary database for upgrades, you can use a snapshot standby database as the source for a refreshable clone PDBs to reduce load on the primary database.

When you perform non-CDB to PDB conversions or unplug-plug upgrades using refreshable clone PDBs, the target CDB connects to the source database and copies the entire database. This puts load on the source database.

If the source database is part of an Oracle Data Guard configuration, then you can offload the work to a snapshot standby database to prevent overloading the primary database.

To use this technique, the source standby database must be a snapshot standby database. A mounted or open physical standby database or an Active Data Guard database can't be used as the source of a refreshable clone PDB.

Also, if you use this technique for conversion and upgrade tests, then you may not find it desirable to run the pre-upgrade fixups on the primary database.

With this option, after you perform the initial clone of the source database, refreshing that clone is a limited drain on resources. Accordingly, when you clone the source active Oracle Data Guard standby database as a snapshot standby, you can perform checks and upgrade your database using the snapshot standby database without consuming resources and incurring downtime.

It's mostly the initial cloning of the source database that consumes resources. Once beyond that, the refresh phase (where redo is shipped and applied) doesn't take many resources.

In all cases, there'll not be any downtime, however, the initial cloning can really have an impact on the source database.

Example 3-9

1.  Convert the source standby database to a snapshot standby database:

        DGMGRL> convert database '...' to snapshot standby;

    **Note:**

    If you don't manage your Oracle Data Guard configuration using Data Guard broker, then you can use the equivalent SQL commands instead to convert the source standby database to a snapshot standby database.

2.  If you perform an unplug-plug upgrade, then ensure the PDB is open on the source snapshot standby database.

        alter pluggable database ... open;

    If you perform non-CDB to PDB conversions, then you can skip this step.

    **Note:**

    If the PDB is not open on the source standby database, then you receive an ORA-03150 error when querying the source database over the database link (ORA-03150: end-of-file on communication channel for database link).

3.  In the source standby database, create the user account used by the database link, and grant appropriate permissions:

        create user dblinkuser identified by ...;
        grant create session, create pluggable database, select_catalog_role to
        dblinkuser;
        grant read on sys.enc$ to dblinkuser;

    **Note:**

    If you perform unplug-plug upgrades, then you must perform this operation in the source PDB, not in CDB\$ROOT.

4.  In the target CDB, create a database link that points to the source standby database, where `alias-to-source-standby` is the alias to the soruce standby database:

        create database link clonepdb
        connect to dblinkuser identified by ...
        using 'alias-to-source-standby';

    **Note:**

    If you perform unplug-plug upgrades, then the alias must point directly into the source PDB on the snapshot standby database.

5.  Create an AutoUpgrade configuration file.

    The following example shows an unplug-plug upgrade:

        global.global_log_dir=/home/oracle/autoupgrade/log
        global.keystore=/home/oracle/autoupgrade/keystore
        upg1.source_home=/u01/app/oracle/product/19.0.0.0/dbhome_1
        upg1.target_home=/u01/app/oracle/product/23.0.0/dbhome_1
        upg1.sid=CDB19
        upg1.target_cdb=CDB23
        upg1.pdbs=PDB1
        upg1.source_dblink.PDB1=CLONEPDB 300
        upg1.target_pdb_copy_option.PDB1=file_name_convert=none
        upg1.start_time=+12h

6.  Start AutoUpgrade in deploy mode:

        java -jar autoupgrade.jar ... -mode deploy

    AutoUpgrade starts to create a clone of the source database, and then proceeds to apply redo at the specified refresh rate. In the REFRESHPDB stage, you can change the start time (as specified in the configuration file) by using the PROCEED command.

7.  After the entire process is completed, you convert the source standby database back to a physical standby database:

        DGMGRL> convert database '...' to physical standby;

**Parent topic:** AutoUpgrade and Oracle Database Configuration Options
