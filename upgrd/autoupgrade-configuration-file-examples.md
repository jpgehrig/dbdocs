## AutoUpgrade Configuration File Examples

Use these examples to understand how you can modify your own AutoUpgrade configuration files to perform a variety of configuration actions during the upgrade.

- Create Configuration File for AutoUpgrade
  To use AutoUpgrade to complete the upgrade, you first create a configuration file with AutoUpgrade from the new release Oracle home.
- Updating the TDE Wallet Store Location During Upgrade Using AutoUpgrade
  See how you can use AutoUpgrade configuration file parameters to update your Transparent Data Encryption (TDE) wallet store during upgrade.
- AutoUpgrade Configuration File with Two Database Entries
  See how you can specify upgrade options for multiple databases in a configuration file.
- Standardizing Upgrades With AutoUpgrade Configuration File Entries
  See how to enforce standardization of your database configurations during upgrades using AutoUpgrade.
- AutoUpgrade Configuration File for Incremental Upgrade of a Set of PDBs
  See how you can selectively upgrade a subset of PDBs using AutoUpgrade, without affecting the other PDBs on the source CDB.
- AutoUpgrade Configuration File For Upgrading PDBs Already in the Target CDB
  See how you can specify an upgrade of earlier release PDBs that are on a later release CDB.
- How to Run AutoUpgrade in a Script or Batch job
  Learn how to run AutoUpgrade in your own scripts in noninteractive mode by calling AutoUpgrade using the `noconsole` parameter.
- Unplug-Plug Relocate Upgrades With AutoUpgrade
  See how you can use the Unplug-Plug Relocate feature (also known as Hot-Cloning upgrade) to create PDBs that can be refreshed for a given period before upgrading them.
- Ignore Fixups and Checks Using the AutoUpgrade Configuration File
  To skip an entire check and fixup step for a database, you can direct AutoUpgrade to read the fixup `runfix` flag from the fixups checklist file, and set the flag for that fixup from `YES` to `SKIP`.
- Run Custom Scripts Using AutoUpgrade
  Learn how to use AutoUpgrade to run your own scripts as part of the deploy process.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### Create Configuration File for AutoUpgrade

To use AutoUpgrade to complete the upgrade, you first create a configuration file with AutoUpgrade from the new release Oracle home.

In the following example, the AutoUpgrade utility is run using the parameter `sample_config_file`. This parameter generates a configuration file in the home of the user running AutoUpgrade that you can edit to provide environment paths and settings and upgrade preferences for the upgrade. To generate the configuration file (`config`), you run AutoUpgrade from the new release Oracle Database home using the `sample_config_file` parameter, and specify an output file name.

**Note:**

AutoUpgrade is regularly updated. For additional examples, and for information about the most recent AutoUpgrade releases, including new command-line parameters and options, and new or enhanced configuration file parameters, refer to the Oracle Database Upgrade Guide for the release to which you want to upgrade. Also refer to the My Oracle Support note "AutoUpgrade Tool (Doc ID 2485457.1)," which will contain information about the most recent AutoUpgrade updates.

In this example, user `oracle` navigates to the location of an earlier release Oracle home, which in this example is Oracle Database 19c:

    cd /u01/app/oracle/product/19.0.0/

Next, the Oracle user starts AutoUpgrade from the Oracle Database 23ai Oracle home, and creates a configuration file in its user home directory, `/home/oracle`:

    java -jar /u01/app/oracle/product/23/rdbms/admin/autoupgrade.jar -create_sample_file config
    Created sample configuration file /home/oracle/sample_config.cfg

After you create the configuration file, open it up in your preferred text editor, and modify parameter settings as needed for your environment.

    cd /
    vi sample_config.cfg

**Related Topics**

- [Oracle Database Documentation](https://docs.oracle.com/en/database/oracle/oracle-database/index.html)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** AutoUpgrade Configuration File Examples

### Updating the TDE Wallet Store Location During Upgrade Using AutoUpgrade

See how you can use AutoUpgrade configuration file parameters to update your Transparent Data Encryption (TDE) wallet store during upgrade.

In previous releases, if you used Oracle Wallet with TDE, then you specified the location of the existing keystore directory location by using the deprecated `sqlnet.ora` parameter `SQLNET.ENCRYPTION_WALLET_LOCATION`. In Oracle Database 19c and later releases, you should specify the keystore location by using the `WALLET_ROOT` system parameter in the database initialization parameter file (`PFILE`). What you need to do depends on how your source Oracle Database release is configured:

- If your source Oracle Database release has `WALLET_ROOT` set already, then the parameter files that AutoUpgrade generates automatically pick up the `WALLET_ROOT` system parameter from the source database during the upgrade, and use that parameter in target database parameter files.

- If your source Oracle Database release does not have the initialization parameter `WALLET_ROOT` set, then you can use AutoUpgrade to complete that task during the upgrade.

1.  Create a text file on your operating system with the `WALLET_ROOT` initialization parameter value for the directory that you want to use, and that provides the configuration option you want for the `TDE_CONFIGURATION` dynamic initialization parameter to create the type of keystores that you require. For example, if you configure `TDE_CONFIGURATION` to use `FILE` for Transparent Data Encryption software keystores, then Oracle Database creates the software keystore in `WALLET_ROOT/tde` (lower case).
2.  In the AutoUpgrade configuration file, use the AutoUpgrade configuration file parameters` add_during_upgrade_pfile` and `add_after_upgrade_pfile` to refer to that file on the operating system to set `WALLET_ROOT` and `TDE_CONFIGURATION` during the upgrade.

For example, if you want `WALLET_ROOT` to use the path `/u01/app/oracle/admin/hr/wallet`, and Transparent Data Encryption to store software keystores in the location `WALLET_ROOT/tde`, then you can create a text file called `tde-upgrade`, which contains the following lines:

    WALLET_ROOT=/u01/app/oracle/admin/hr/wallet
    tde_configuration="KEYSTORE_CONFIGURATION=FILE"

You can then specify for AutoUpgrade to set these parameters in the AutoUpgrade configuration file. For example, to set the Transparent Data Encryption keystore during and after the upgrade, as part of the AutoUpgrade operation, add the following line to your local configuration file to call that text file:

    #
    #      Example local pfile configuration entries
    upg1.add_after_upgrade_pfile=/usr/home/oracle/tde-upgrade
    upg1.add_during_upgrade_pfile=/usr/home/oracle/tde-upgrade

**Related Topics**

- [How Configuring Transparent Data Encryption Works](../asoag/configuring-transparent-data-encryption.md)

**Parent topic:** AutoUpgrade Configuration File Examples

### AutoUpgrade Configuration File with Two Database Entries

See how you can specify upgrade options for multiple databases in a configuration file.

This example is of an AutoUpgrade configuration file that specifies the upgrade of two databases. The configuration file specifies that AutoUpgrade performs the following actions:

Database 1

- An in-place database upgrade of the Oracle Database 12c Release 2 (12.2) CDB, where the source and target Oracle homes use the same Oracle Base directory (the database home directory for Oracle Database installation owner `oracle` (`/u01/app/oracle/`) on the same server hardware, with the same system identifier (sid=HR1).
- During the upgrade, all the PDBs of the CDB are upgraded (`pdbs=*`)
- The upgrade starts immediately (`start_time=now`)
- The database upgrade logs will be sent to the path `/database/logs/hr` (`log_dir=/database/logs/hr`)
- The Time Zone upgrade will run on all the containers (`timezone_upg=yes`)

Database 2

- An in-place database upgrade of the Oracle Database 18c CDB, where the source and target Oracle homes use the same Oracle Base directory (the database home directory for Oracle Database installation owner `oracle` (`/u01/app/oracle/`) on the same server hardware, with the same system identifier (`sid=SALES1`).
- The upgrade starts immediately (`start_time=now`)
- The database upgrade logs will be sent to the path `/database/logs/sales` (`log_dir=/database/logs/sales`).
- The Time Zone upgrade will not run on any containers (`timezone_upg=no`).

For both databases:

- The parameter `upgrade_node` specifies the actual system host name (`nodename-1`), and not to an alias assigned to the host name. (You can also use the keyword `localhost` to refer to the current system.)
- The global AutoUpgrade log files (also known as job manager logs) are placed under the path `/database/jobmgr` (`autoupg_log_dir=/database/jobmgr`).

<!-- -->

    #
    # Global logging directory pertains to all jobs
    #
    global.autoupg_log_dir=/database/jobmgr

    #
    # Database 1
    #
    upg1.source_home=/u01/app/oracle/product/12.2.0.2/dbhome_1
    upg1.target_home=/u01/app/oracle/product/19.0.0/dbhome_1
    upg1.sid=HR1
    upg1.start_time=now
    upg1.pdbs=*
    upg1.log_dir=/database/logs/hr
    upg1.upgrade_node=nodename1
    upg1.run_utlrp=yes
    upg1.timezone_upg=yes
    upg1.target_version=21

    #
    # Database 2
    #
    upg2.source_home=/u01/app/oracle/product/18.0.0/dbhome_1
    upg2.target_home=/u01/app/oracle/product/19.0.0/dbhome_1
    upg2.sid=SALES1
    upg2.start_time=now
    upg2.log_dir=/database/logs/sales
    upg2.upgrade_node=nodename1
    upg2.timezone_upg=no
    upg2.target_version=21

On the Oracle Database Upgrades and Migration YouTube Channel, you can see a similar upgrade scenario, Oracle Database AutoUpgrade 19c - Upgrading 2 databases in parallel (11:57), demonstrated by Mike Dietrich.

**Related Topics**

- [Oracle Database AutoUpgrade 19c - Upgrading 2 databases in parallel](https://www.youtube.com/watch?v=kr3aZrqA9Go)

**Parent topic:** AutoUpgrade Configuration File Examples

### Standardizing Upgrades With AutoUpgrade Configuration File Entries

See how to enforce standardization of your database configurations during upgrades using AutoUpgrade.

In the following configuration file, you can see how you can use AutoUpgrade configuration file entries to standardize their database configurations. The global `PFILE` entries are applied to all databases within the configuration file. The local `PFILE` entries are applied only to a specific database in the configuration file. The syntax for these `PFILE` values follow the same Oracle rules for `PFILE` configurations.

    #
    #    Example global pfile configuration entries
    #
    global.del_during_upgrade_pfile=/database/pfiles/global_during_delinit.ora
    global.add_during_upgrade_pfile=/database/pfiles/global_during_addinit.ora
    global.del_after_upgrade_pfile=/database/pfiles/global_after_delinit.ora
    global.add_after_upgrade_pfile=/database/pfiles/global_after_addinit.ora

    #
    #      Example local pfile configuration entries
    #
    upg1.del_during_upgrade_pfile=/database/pfiles/hr_during_delinit.ora
    upg1.add_during_upgrade_pfile=/database/pfiles/hr_during_addinit.ora
    upg1.del_after_upgrade_pfile=/database/pfiles/hr_after_delinit.ora
    upg1.add_after_upgrade_pfile=/database/pfiles/hr_after_addinit.ora

During the AutoUpgrade process, the files `during_upgrade_pfile_dbname.ora` and `after_upgrade_pfile_dbname.ora` are both created. These files are used to start the database during the upgrade, and after the upgrade. If you want to change a system parameter during the upgrade, or after the upgrade, then you can modify both files.

The global `PFILE` entries are applied first, and then the local `PFILE` entries designated by the job prefix `upgl` are applied. Within those two configuration files, entries in the parameter `del_upgrade_pfile` are applied first, followed by entries in the parameter `add_upgrade_pfile`. The parameters in these `PFILE` configuration entries are applied directly either to the `PFILE` `during_upgrade_pfile_dbname.ora` or to the `PFILE` `after_upgrade_pfile_dbname.ora`, depending on which `PFILE` is targeted.

Actions:

- `del_during_upgrade_pfile` Removes entries from `during_upgrade_pfile_dbname.ora`
- `add_during_upgrade_pfile` Add entries to `during_upgrade_pfile_dbname.ora`.
- `del_after_upgrade_pfile` Removes entries from `after_upgrade_pfile_dbname.ora`
- `add_after_upgrade_pfile` Add entries to `after_upgrade_pfile_dbname.ora.`

The files referenced by the parameters `del_during_upgrade_pfile` and `del_after_upgrade_pfile` have a single database parameter listed on each line. You cannot add any prefix to the parameter, because the entire line is part of the parameter name. Consider the following example:

    #
    # global.del_during_upgrade_pfile
    #
    processes
    *.open_cursors

The result of this configuration setting is to remove from the `PFILE` for each database listed in the configuration file all references to the `processes` parameter, but not references to the `open_cursors` parameter: Only instances of `open_cursors` that have a prefix are removed. However, the parameters removed from the `PFILE` includes all parameters that are prefixed. For example, `*.processes` and `instance_name.processes` are both removed with this syntax.

The files referenced by the parameters `add_during_upgrade_pfile` and `add_after_upgrade_pfile` have a single parameter listed on each line with the format `parameter``=``value`. If you delete the entry from the `PFILE`, then the value field can be left empty. If the parameter is prefixed with `*.` or `instancename.`, then those references are not added to the modified `PFILE`. To update the value of an existing parameter, you must first delete it. You can then add the parameter with the desired value. Consider the following example:

    #
    # global.add_during_upgrade_pfile
    #
    processes=400
    *.open_cursors=250

This global configuration file entry results in adding the following entries to the `PFILE` for each database that is listed in the configuration file:

    processes=400
    open_cursors=250

The parameter `after_upgrade_pfile_dbname` is used to create the database `SPFILE` during the postupgrade process.

**Parent topic:** AutoUpgrade Configuration File Examples

### AutoUpgrade Configuration File for Incremental Upgrade of a Set of PDBs

See how you can selectively upgrade a subset of PDBs using AutoUpgrade, without affecting the other PDBs on the source CDB.

In this scenario, you upgrade two specific PDBs, without upgrading the other PDBs in the source CDB, To perform the incremental upgrade, you direct AutoUpgrade in the configuration file to unplug the PDBs you specify from an earlier release CDB, plug them into a target release CDB, and then upgrade the earlier release PDBs on the target CDB. This selection of PDBs to unplug, plug in, and upgrade, enables you to perform an incremental upgrade of PDBs on the earlier release CDB to reduce downtime.

The following configuration file identifies the CDB `CDB122` as the source CDB. The source CDB has 10 PDBs, `PDB1` through `PDB10`, but only `PDB1` and `PDB2` are upgraded. During the upgrade, the PDB named `PDB2` has its name changed to `DEPSALES`, and the database file names for `PDB2` are changed to `DEPSALES`:

    global.autoupg_log_dir=/home/oracle/autoupg
    upg1.sid=CDB122
    upg1.source_home=/u03/app/oracle/product/12.2.0/dbhome_1
    upg1.target_home=/u01/app/oracle/product/19.0.0/dbhome_1
    upg1.target_cdb=CDB19C
    upg1.pdbs=PDB2, PDB1
    upg1.target_pdb_name.PDB2=DEPSALES
    upg1.target_pdb_name.PDB1=EMPLOYEES
    upg1.target_pdb_copy_option.PDB2=file_name_convert=('PDB2','DEPSALES')

This configuration file directs AutoUpgrade to do the following:

- Select PDBs from the source Oracle Database `CDB122` in the home `/u03/app/oracle/product/12.2.0/dbhome_1`
- Upgrade PDBs `PDB2` and `PDB1` to the target Oracle Database 19c Oracle home `/u01/app/oracle/product/19.0.0/dbhome_1`
- Change the name of `PDB2` to `DEPSALES`, and copy the `PDB2` files using the new filename `DEPSALES`.
- Change the name of `PDB1` to `EMPLOYEES`.

**Parent topic:** AutoUpgrade Configuration File Examples

### AutoUpgrade Configuration File For Upgrading PDBs Already in the Target CDB

See how you can specify an upgrade of earlier release PDBs that are on a later release CDB.

In this scenario, you upgrade specific PDBs that were excluded in a previous upgrade of the CDB and PDBs, or PDBs that were added to the CDB through manual Non-CDB to PDB or Unplug-Plug operations. The PDBs are in an earlier release version.

The configuration file has a Database 1 section that identifies the CDB database as `CDB19X`, which is the CDB that has the existing PDBs `PDB1` and `PDB2`. In this scenario CDB19X has 10 PDBs, PDB1 through PDB10, but PDB1 and PDB2 were excluded from an earlier upgrade procedure. CDB19X and PDBs 3 through 10 are all upgraded to the later release, but PDB1 and PDB2 remain on an earlier release. We will now run AutoUpgrade to upgrade the remaining two PDBs on the earlier release, specifying that the target upgrade PDBs `PDB1` and `PDB2` are on `CDB19X` (`upg1.sid=CDB19X`), and the upgrade should start immediately with `upg.start_time=now`.

**Note:**

Before you begin, the PDBs PDB1 and PDB2 must already be in Upgrade mode.

Update the configuration file (`config.cfg`):

    #
    # Global logging directory pertains to all jobs
    #
    global.autoupg_log_dir=/home/oracle/autoupg
    #
    # Database 1
    #
    upg1.sid=CDB19X
    upg1.start_time=now
    upg1.target_home=/u01/app/oracle/product/19.0.0/dbhome_1
    upg1.pdbs= PDB1,PDB2

Start the upgrade with AutoUpgrade:

    java -jar autoupgrade.jar -config config.cfg -mode upgrade

**Parent topic:** AutoUpgrade Configuration File Examples

### How to Run AutoUpgrade in a Script or Batch job

Learn how to run AutoUpgrade in your own scripts in noninteractive mode by calling AutoUpgrade using the `noconsole` parameter.

By default, AutoUpgrade runs in console mode, which enables you to run commands to monitor specific aspects of your AutoUpgrade jobs while they are running on your systems.

**Note:**

You can run only one AutoUpgrade instance at a time that is associated with a given configuration file.

Example 3-15 Running a script using `noconsole` mode

In this example, AutoUpgrade is run in Deploy mode, using the settings specified in the configuration file `autoupgrade.cfg`, and turning off console using the `noconsole` parameter.

    java -jar autoupgrade.jar -config autoupgrade.cfg -mode deploy -noconsole

Using the `noconsole` mode turns off requirements for user input, so you can enter this command in a script to run the upgrades you specify in the configuration file.

**Parent topic:** AutoUpgrade Configuration File Examples

### Unplug-Plug Relocate Upgrades With AutoUpgrade

See how you can use the Unplug-Plug Relocate feature (also known as Hot-Cloning upgrade) to create PDBs that can be refreshed for a given period before upgrading them.

You can use the Unplug-Plug relocate upgrade as a method to create clones from other PDBs, or from non-CDB databases. If the source database is a non-CDB, then AutoUpgrade upgrades and converts the non-CDB as part of the upgrade process. This feature is compatible with Oracle Database 12c release 1 (12.1.0.2) and later releases as the source release. Starting with AutoUgrade version 22.5, AutoUpgrade supports unplug-relocate operations using a source of at least Oracle Database 12c Release 1 (12.1.0.2). When a 12.1.0.2 source is used, the deploy operation requires the source to be in read only mode, and the target CDB to not be in local undo mode. The `CLONE_ONLY` option is also required when specifying the `source_dblink parameter`.Oracle Database Release 11g (11.2) is not compatible as a source version for the AutoUpgrade Hot-Cloning feature.

To use the Unplug-Plug relocate upgrade method, the following configuration must be complete:

- On the database that you plan to clone, a user must exist that is granted the `CREATE SESSION`,`CREATE PLUGGABLE DATABASE`, `SELECT_CATALOG_ROLE`, and `GRANT READ ON sys.enc$` privileges.
- On the CDB where you plan to relocate the PDB, you must create a database link (`@dblink`) on the CDB that points to the database that you plan to clone.
- The target CDB must have configured all of the components that the source database has configured, or the upgrade process will fail.

Make a note of the database link, because you need it to fill out the AutoUpgrade configuration file.

In the following example, we will go through each step in the process, for both a non-CDB and a PDB. The scenario below is composed of two hosts:

- `db-node1:` The source database host location, where step 1 is run.
- `db-node2`: The target database host location, where step 2 is run.

**Note:**

This example uses two separate hosts, but this procedure can also be run on a single host.

1.  Grant a user on the database that you want to clone the `CREATE SESSION`, `CREATE PLUGGABLE DATABASE`, and `SELECT_CATALOG_ROLE` privileges. Also, on SYS, give the user `GRANT READ ON sys.enc$`. In this example, the user `clone` is created with these privileges,

    - Non-CDB:

          alter system set local_listener='(ADDRESS=(PROTOCOL=TCP)(HOST=db-node1)(PORT=1521))';
          ALTER SYSTEM REGISTER;
          CREATE USER clone IDENTIFIED BY some-password;
          GRANT CREATE SESSION, CREATE PLUGGABLE DATABASE, SELECT_CATALOG_ROLE TO clone;
          GRANT READ ON sys.enc$ TO user;

    <!-- -->

    - PDB:

          alter system set local_listener='(ADDRESS=(PROTOCOL=TCP)(HOST=db-node1)(PORT=1521))';
          ALTER SYSTEM REGISTER;
          CREATE USER c##clone IDENTIFIED BY some-password CONTAINER=ALL;
          GRANT CREATE SESSION, CREATE PLUGGABLE DATABASE, SELECT_CATALOG_ROLE TO c##clone CONTAINER=ALL;
          GRANT READ ON sys.enc$ TO c##clone CONTAINER=ALL;

      On a PDB, you can also limit the scope of creating the user to a single PDB on the CDB by specifying a particular PDB name. For example:
          CREATE USER c##clone IDENTIFIED BY some-password CONTAINER=PDBX;

2.  Configure the CDB to which you want to clone the PDB by creating a database link pointing to the source database on the source system that you plan to clone.

    In the following example, the database link points to the source database `db18x`:

    - Non-CDB

      In the following example, the database link points to the source database `db18x`:

          CREATE DATABASE LINK db18x_link
          CONNECT TO clone IDENTIFIED BY some-password
          USING'(DESCRIPTION =(ADDRESS = (PROTOCOL = TCP)(HOST = db-node1)(PORT =
          1521))(CONNECT_DATA = (SERVICE_NAME = db18x)))';

    - PDB

      In the following example, the database link points to the source PDB `pdbx` on the CDB `cdb18x`:

          CREATE DATABASE LINK pdbxcdb18x_link
          CONNECT TO c##clone IDENTIFIED BY some-password
          USING'(DESCRIPTION =(ADDRESS = (PROTOCOL = TCP)(HOST = db-node1) (PORT =
          1521))(CONNECT_DATA = (SERVICE_NAME = pdbx)))';

3.  Update the AutoUpgrade configuration file with the information needed to identify the databases that you want to clone.

    Each database that you plan to clone must have the AutoUpgrade local parameter `target_pdb_copy_option` set to convert file names.

    **Note:**

    On the target CDB, if you have the parameters `DB_CREATE_FILE_DEST` or `PDB_FILE_NAME_CONVERT` set, and you want these parameters on the target CDB to take effect, then set the value of `prefix``.target_pdb_copy_option=file_name_convert=NONE`. However, you must have a file name and path specified either in the configuration file, or on the target CDB, or the upgrade will fail.
    By using the prefix for local parameters for each database, you can combine non-CDB and PDB upgrades in the same configuration file to relocate both non-CDBs and PDBs to the same target CDB. The following is an example of the relevant portion of the configuration file where both the non-CDB database `db18x` is configured for upgrade, and the PDB `pdbx` is configured for upgrade. In this case, file names for `db18x` are set to change the prepended name from `DB18x` to `db18x`, and the file names for the :

        upg1.sid=db18x
        upg1.source_home=/source/18x
        upg1.target_home=/target/19x
        upg1.target_cdb=cdb19x
        upg2.sid=cdb18x
        upg2.pdbs=pdbx
        upg2.target_cdb=cdb19x
        upg2.source_home=/source/18x
        upg2.target_home=/target/19x

    Each database has a `target_pdb_copy_option` set. For example, here the non-CDB filenames are converted from the prepended string `DB18X` to `db18x`:

        upg1.target_pdb_copy_option.db18x=file_name_convert=('DB18X', 'db18x')

    Each database must have the local parameter `source_dblink` set to the database link that you created on the target CDB:

        upg1.source_dblink.db18x=db18x_link

    To improve consistency, you can also use the local parameter `start_time` in combination with `source_dblink` with the optional refresh rate (in seconds) to set a refresh rate for the data, and schedule the job start time. The following parameters combined start AutoUpgrade, but sets a delay for the deployment of the upgrade of one hour and 40 minutes from the time that AutoUpgrade was started, and sets a refresh rate from the source database files to the target database files every 20 seconds:

        upg1.source_dblink.db18x=db18x_link 20
        upg1.start_time=+1h40m

    If you do not set a refresh rate for `source_dblink`, then the database files of the cloned database are cloned only once, without a refresh. If `start_time` is not set (so there is no delay in the processing of the upgrade), then the `source_dblink` refresh rate value is ignored.

4.  Start the Unplug-Plug relocate deployment, specifying the configuration file you created for this task:

        java -jar autoupgrade.jar -config config.cfg -mode deploy

Example 3-16 Configuration File for Unplug-Plug Relocate of Non-CDB and PDB with No Refresh Rate for Data Files

    global.autoupg_log_dir=/home/oracle/xupg
    #database1
    upg1.sid=cdb18x
    upg1.target_cdb=cdb19x
    upg1.source_home=/databases/ee/product/18x/dbhome_1
    upg1.target_home=/databases/ee/product/19x/dbhome_1
    upg1.pdbs=pdbx
    upg1.target_pdb_name.pdbx=pdbxr
    upg1.target_pdb_copy_option.pdbx=file_name_convert=('pdbx', 'pdbxr')
    upg1.source_dblink.pdbx=pdbxcdb18x_link
    #database2
    upg2.sid=db18x
    upg2.target_cdb=cdb19x
    upg2.source_home=/databases/ee/product/18x/dbhome_1
    upg2.target_home=/databases/ee/product/19x/dbhome_1
    upg2.target_pdb_copy_option.db18x=file_name_convert=('DB18X', 'db18x')
    upg2.source_dblink.db18x=db18x_link
    upg2.target_pdb_name.db18x=db18x

Example 3-17 Configuration File for Unplug-Plug Relocate of Non-CDB and PDB with Deployment Delay and Refresh Rate for Data Files

    global.autoupg_log_dir=/home/oracle/xupg
    #database1
    upg1.sid=cdb18x
    upg1.target_cdb=cdb19x
    upg1.source_home=/databases/ee/product/18x/dbhome_1
    upg1.target_home=/databases/ee/product/19x/dbhome_1
    upg1.pdbs=pdbx
    upg1.target_pdb_name.pdbx=pdbxr
    upg1.target_pdb_copy_option.pdbx=file_name_convert=('pdbx', 'pdbxr')
    upg1.source_dblink.pdbx=pdbxcdb18x_link 600
    upg1.start_time=+3h
    #database2
    upg2.sid=db18x
    upg2.target_cdb=cdb19x
    upg2.source_home=/databases/ee/product/18x/dbhome_1
    upg2.target_home=/databases/ee/product/19x/dbhome_1
    upg2.target_pdb_copy_option.db18x=file_name_convert=('DB18X', 'db18x')
    upg2.source_dblink.db18x=db18x_link 900
    upg2.target_pdb_name.db18x=db18x
    upg2.start_time=+3h30m

Example 3-18 Simple Configuration File for Unplug-Plug Relocate of a PDB

    global.autoupg_log_dir=/home/oracle/xupg #database1
    upg1.sid=cdb18x
    upg1.target_cdb=cdb19x
    upg1.source_home=/databases/ee/product/18x/dbhome_1
    upg1.target_home=/databases/ee/product/19x/dbhome_1
    upg1.pdbs=pdbx
    upg1.target_pdb_copy_option.pdbx=file_name_convert=('pdbx', 'pdbxr')
    upg1.source_dblink.pdbx=pdbxcdb18x_link

For more examples of unplug-plug upgrades, see Mike Dietrich's blog, "Upgrade Your Database Now!" and Daniel Overby Hansen's blog, "Databases are Fun". New use case examples are regularly presented on these sites. Two examples are appended below.

**Related Topics**

- [Unplug/Plug Upgrade with AutoUpgrade](https://mikedietrichde.com/2021/06/07/unplug-plug-upgrade-with-autoupgrade/)
- [Upgrading an Encrypted PDB](https://dohdatabase.com/2022/03/31/upgrading-an-encrypted-pdb/)

**Parent topic:** AutoUpgrade Configuration File Examples

### Ignore Fixups and Checks Using the AutoUpgrade Configuration File

To skip an entire check and fixup step for a database, you can direct AutoUpgrade to read the fixup `runfix` flag from the fixups checklist file, and set the flag for that fixup from `YES` to `SKIP`.

To override the default list of fixups that AutoUpgrade performs automatically for upgrades, you can load an existing checklist of fixup steps in to AutoUpgrade by using the local configuration file parameter `checklist`. In the checklist that you specify with the local parameter, you can set a precheck fixup as follows:

- `YES` (the default): Run checks, and run fixups
- `NO`: Run checks, but do not run fixups.
- `_SKIP`: Do not run checks, and do not run fixups.

In the configuration file, the local parameter checklist is used to direct AutoUpgrade to an existing checklist file.

    global.autoupg_log_dir=/home/oracle/autoupg

    upg1.sid=db12204
    upg1.source_home=/databases/ee/product/12.2.0/dbhome_1
    upg1.target_home=/databases/ee/product/21.1.0/dbhome_1
    upg1.checklist=/home/oracle/autoupg/db12204/100/prechecks/db11204_checklist.cfg

In the Fixups checklist file, the `runfix` flag for the `DICTIONARY_STATS` fixup is is set to skip that step.

    [SID] [db21.1.0]
    ==========================================
    [container] [db21.1.0]
    ==========================================
    [checkname] EXISTENCE_OF_DATAPUMP_AQ_TABLES
    [stage] PRECHECKS
    [fixup_available] YES
    [runfix] YES
    [severity] WARNING
    ----------------------------------------------------
    [checkname] DICTIONARY_STATS
    [stage] PRECHECKS
    [fixup_available] YES
    [runfix] _SKIP
    [severity] RECOMMEND
    ----------------------------------------------------

**Parent topic:** AutoUpgrade Configuration File Examples

### Run Custom Scripts Using AutoUpgrade

Learn how to use AutoUpgrade to run your own scripts as part of the deploy process.

You can configure four parameters in the configuration file that enable you to run custom scripts:

- `before_action`

  Run a custom script on the source Oracle home before the database is upgraded, during the Preupgrade stage when the database is up.

- `after_action`

  Run a custom script on the target Oracle home after the database is upgraded, during the Postupgrade stage or PDB upgrade stage, depending on the options set in the configuration file.

- `revert_before_action`

  Run a custom script on the target Oracle home before the database is restored, typically when the database is still up. Due to the nature of the upgrade process, be aware that the database can be down when the script is started. You can use this script to undo actions performed by a `before_action` custom script.

- `revert_after_action`

  Run a custom script on the source Oracle home after the database restored, and the database is up. You can use this script to undo actions performed by an `after_action` custom script.

See parameter descriptions under "AutoUpgrade Utility Configuration Files" for more detailed information about these parameters.

Example 3-19 Using `before_action` and `after_action` in the Configuration File

In the following example of configuration file `config.cfg`, the local parameter `before_action` is used in the configuration file to run the script `script1.sh` in the path `/path/to/a/` before the restoration, and the local parameter `after_action` is used to run the script `script2.sh` in the path `/path/to/a/` after the upgrade.

Contents of the configuration file `config.cfg`:

    global.autoupg_log_dir=/home/oracle/autoupg
    upg1.sid=db12204
    upg1.source_home=/databases/ee/product/12.2.0/dbhome_1
    upg1.target_home=/databases/ee/product/19.0.0/dbhome_1
    upg1.before_action=/path/to/a/script1.sh
    upg1.after_action=/path/to/a/script2.sh

The configuration file is called by AutoUpgrade from the command line:

    java -jar autoupgrade.jar -config config.cfg -restore -jobs 100,101,...

Because these scripts are run during the preupgrade and postupgrade stages, restoration to the GRP occurs before or after the scripts are run. The scripts do not affect the actual GRP process itself, which makes them safer for reruns if the script actions can affect the database.

Example 3-20 Using `revert_before_action` and `revert_after_action` in the Configuration File

In the following example of configuration file `config.cfg`, the local parameter `revert_before_action` is used in the configuration file to run the script `script3.sh` in the path `/path/to/a/` before the restoration, and the local parameter `revert_after_action` is used to run the script `script4.sh` in the path `/path/to/a/` after the upgrade.

    global.autoupg_log_dir=/home/oracle/autoupg
    upg1.sid=db12204
    upg1.source_home=/databases/ee/product/12.2.0/dbhome_1
    upg1.target_home=/databases/ee/product/19.0.0/dbhome_1
    upg1.revert_before_action=/path/to/a/script3.sh
    upg1.revert_after_action=/path/to/a/script4.sh

Again, the configuration file is used to direct AutoUpgrade as it runs the restore jobs:

    java -jar autoupgrade.jar -config config.cfg -restore -jobs 100,101,...

In this case, the scripts are run on the target Oracle Database binaries when the database is up. The `script3.sh` script called by `revert_before_action` is run when the database is up, before starting the restoration to the GRP, and the `script4.sh` script called by `revert_after_action` is run on the database after restoration to the earlier release is complete, and the database is up in the original Oracle home.

**Related Topics**

- [AutoUpgrade Utility Configuration Files](autoupgrade-utility-configuration-files.md)

**Parent topic:** AutoUpgrade Configuration File Examples
