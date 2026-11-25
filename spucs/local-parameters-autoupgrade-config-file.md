To configure information for specific Oracle Databases for the AutoUpgrade utility upgrade, you provide information in the AutoUpgrade local parameters.

### Usage Notes

Local parameters take precedence over any global parameters set in the AutoUpgrade configuration file. Local parameters that either must be set locally, or as a locally modifiable global parameter are indicated by (Required). All local parameters take a prefix (in examples, identified by a value you define to identify a particular database or upgrade. The prefix identifies the specific upgrade job to which the parameter applies in the configuration file.

Example: The set of parameters for the first upgrade in the configuration file uses the prefix `sales`, and the set of parameters for the next upgrade in the configuration file uses the prefix `employees`:

    sales.source_home=/u01/app/oracle/12.2/dbhome1
    .
    .
    .
    employees.sid=salescdb
    employees.source_home-/03/app/oracle/21/dbhome1

- add_after_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add after the upgrade.
- add_during_upgrade_pfile
  (Optional) Specifies a path and file name of a PFILE whose parameters you want to add during the upgrade.
- after_action
  (Optional) In `deploy` mode, specifies a custom action that you want to have performed after completing the deploy job for the database identified by the prefix address.
- before_action
  (Optional) In `deploy` mode, specifies a custom action that you want to have performed before starting the upgrade job for the specific database job addressed by the prefix. If you want to have a script run before all upgrade jobs, then specify that script by using the local parameter (global.before_action)
- catctl_options
  (Optional) Specifies one or more of a set of `catctl.pl` options that you can select for AutoUpgrade to submit for `catctl.pl` to override default behavior.
- checklist
  (Optional) Specifies the path to a checklist that you can use to override the default list of fixups that AutoUpgrade performs, such as fixups that you do not want implemented automatically, due to policy or security concerns.
- del_after_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed after upgrade.
- del_during_upgrade_pfile
  (Optional) Specifies a path and file name of a PFILE whose parameters you want to have removed during upgrade.
- drop_win_src_service
  (Optional) For upgrades on Microsoft Windows, specifies whether to drop the Windows operating system service for the source Oracle Database after upgrade.
- env
  (Optional) Specifies custom operating system environment variables set on your operating system, excluding `ORACLE_SID`, `ORACLE_HOME`, `ORACLE_BASE`, and `TNS_ADMIN`.
- exclusion_list
  (Optional) Sets a list of PDBs that you want to be excluded from the AutoUpgrade run. This parameter only applies to the multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.
- ignore_errors
  (Optional) Enables you to specify a comma-delimited list of specific Oracle errors that you want AutoUpgrade to ignore during the upgrade or patching process.
- keep_source_pdb
  (Optional) Specifies if the source PDB in an unplug-plug upgrade operation is kept in a closed state instead of being removed from the source CDB.
- log_dir
  (Optional) Sets the location of log files that are generated for database upgrades that are in the set of databases included in the upgrade job identified by the prefix for the parameter.
- manage_standbys_clause
  (Optional) Specifies whether standby Oracle Data Guard standby databases you identify by `DB_UNIQUE_NAME` are excluded from AutoUpgrade plug-in upgrades, so that standby database files can be reused.
- pdbs
  (Optional) Sets a list of PDBs on which you want the upgrade to run. This parameter only applies to upgrades of multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.
- raise_compatible
  (Optional) Increases the Oracle Database `COMPATIBLE` initialization parameter to the default value of the target release after the upgrade is completed successfully.
- remove_rac_config
  (Optional) Specifies whether to remove a non-CDB Oracle RAC database from clusterware on the source Oracle home after a successful conversion to the target CDB home, or to leave the source database unchanged.
- remove_underscore_parameters
  (Optional) Removes underscore (hidden) parameters from `PFILE` files during upgrade, and after upgrade, for all Oracle Databases in the configuration file.
- replay
  (Optional) Specifies whether to use replay to upgrade the database.
- restoration
  (Optional) Generates a Guaranteed Restore Point (GRP) for database restoration.
- revert_after_action
  (Optional) Specifies a custom action that you want to have run on the operating system after a system restoration is completed for the specific database job addressed by the prefix, and the database is up.
- revert_before_action
  (Optional) Specifies a custom action that you want to have run on the operating system before a system restoration is completed for the specific database job addressed by the prefix, and the database is up.
- run_hcheck
  (Optional) Specifies whether you run Oracle Dictionary Health Checks as part of preupgrade checks to identify database dictionary inconsistencies.
- run_utlrp
  (Optional) Enables or disables running `utlrp` as part of the upgrade.
- sid
  (Required) Identifies the Oracle system identifier (SID) of the database that you want to upgrade.
- skip_tde_key_import
  (Optional) When set to `yes`, the upgrade is run, but import of the source database KeyStore into the target database is skipped, without raising an error.
- source_base
  (Optional) Specifies the source `ORACLE_BASE` path for the source Oracle home.
- source_dblink
  (Optional) Specifies the database link set up for an unplug-plug relocate (hot clone) upgrade.
- source_home
  (Required for analyze, fixups, and deploy modes. Optional for upgrade mode.) Current Oracle home (`ORACLE_HOME`) of the database that you want to upgrade.
- source_ldap_admin_dir
  (Optional) Specifies the path to the `LDAP_ADMIN` directory in the source database home.
- source_tns_admin_dir
  (Optional) Specifies the path to the `TNS_ADMIN` directory in the source database home.
- start_time
  (Optional) Sets a future start time for the upgrade job to run. Use this parameter to schedule upgrade jobs to balance the load on your server, and to prevent multiple jobs from starting immediately.
- target_base
  (Optional) Specifies the target `ORACLE_BASE` path for the target Oracle home.
- target_cdb
  (Optional) Specifies the `SID` of the target CDB into which a non-CDB Oracle Database is plugged in. This parameter is mandatory when you want to upgrade and convert a non-CDB Oracle Database.
- target_pdb_copy_option=file_name_convert
  (Optional) Specifies the `file_name_convert` option used by the create pluggable database statement that AutoUpgrade runs when converting a non-CDB database to a PDB or an existing PDB from a different source CDB into a PDB in the specified target CDB.
- target_pdb_name
  (Optional) Specifies the name that you want to assign to a non-CDB source Oracle Database after it is plugged in to the target CDB.
- target_ldap_admin_dir
  (Optional) Specifies the path to the `LDAP_ADMIN` directory in the target database home.
- target_tns_admin_dir
  (Optional) Specifies the path to the `TNS_ADMIN` directory in the target database home.
- timezone_upg
  (Optional) Enables or disables running the time zone upgrade as part of the AutoUpgrade process.
- tune_setting
  (Optional) Enables special workflows that alter the behavior of AutoUpgrade during runtime, depending on the workflow option that you specify.
- upgrade_node
  (Optional) Specifies the node on which the current user configuration is valid. The default value is `localhost`.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)

### add_after_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add after the upgrade.

#### Examples

    sales3.add_after_upgrade_pfile=/path/to/my/pfile_add.ora

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### add_during_upgrade_pfile

(Optional) Specifies a path and file name of a PFILE whose parameters you want to add during the upgrade.

#### Examples

    sales3.add_during_upgrade_pfile=/path/to/my/newpfile.ora

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### after_action

(Optional) In `deploy` mode, specifies a custom action that you want to have performed after completing the deploy job for the database identified by the prefix address.

#### Usage Notes

The script that you use must be in the form of `name``.``ext` (for example, `myscript.sh`, so that AutoUpgrade can identify the type of script that you want to run. Permitted extension options:

- Unix shell (`.sh`)

- Microsoft Windows batch (`.bat`, `.cmd`)

- Microsoft Windows PowerShell (`.ps1`)

- Oracle SQL file (`.sql`), with a local operation only designated by the prefix.

By default, if the script fails, then AutoUpgrade continues to run. Use the `Y` flag to specify that AutoUpgrade stops if the operating system detects that your script fails. If the script finishes with a status different than `0`, then it is considered a failed completion.

In contrast to the global `after_action` parameter, the local `after_action` parameter can specify a SQL script, which then runs on the database using the target Oracle Database binaries on a non-CDB Oracle home, or on `CDB$ROOT`. If you want to run additional container-specific actions, then they must be set within the code. For more complex scenarios, you can run container-specific actions in a shell.

The output of the script is captured and stored in files. Both `stdout` and `stderr` are captured. The files are stored in the `postupgrade` subdirectory in the directory matching the specific database or job.

The following environment variables are set in the shell that runs the script:

- `ORACLE_SID`
- `ORACLE_UNQNAME`
- `ORACLE_BASE`
- `ORACLE_HOME`
- `TNS_ADMIN`

#### Examples

Run the specified script after AutoUpgrade starts processing, with the `Y` flag set to stop AutoUpgrade if the script fails:

    sales2.after_action=/user/path/script.sh Y

Run the specified script after AutoUpgrade starts processing the deploy option, with AutoUpgrade set to continue to run if the script fails:

    sales3.after_action=/user/path/script.sh

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### before_action

(Optional) In `deploy` mode, specifies a custom action that you want to have performed before starting the upgrade job for the specific database job addressed by the prefix. If you want to have a script run before all upgrade jobs, then specify that script by using the local parameter (global.before_action)

#### Usage Notes

The script that you use must be in the form of `name``.``ext` (for example,` myscript.sh`), so that AutoUpgrade can identify the type of script that you want to run. Permitted extension options:

- Unix shell (`.sh`)

- Microsoft Windows batch (`.bat`, `.cmd`)

- Microsoft Windows PowerShell (`.ps1`)

- Oracle SQL file (`.sql)`, with a local operation only designated by the prefix.

By default, if the script fails, then AutoUpgrade continues to run. Use the `Y` flag to specify that AutoUpgrade stops if the operating system detects that your script fails. If the script finishes with a status different than `0`, then it is considered a failed completion.

In contrast to the global `before_action` parameter, the local `before_action` parameter can specify a SQL script, which can run on the database in the source database Oracle home, using the earlier release Oracle Database binaries. The script runs on a non-CDB Oracle home, or on `CDB$ROOT`. If you want to run additional container-specific actions, then they must be set within the code. For more complex scenarios, you can run container-specific actions in a shell.

The output of the script is captured and stored in files. Both `stdout` and `stderr` are captured. The files are stored in the `preupgrade` subdirectory in the directory matching the specific database or job.

The following environment variables are set in the shell that runs the script:

- `ORACLE_SID`
- `ORACLE_UNQNAME`
- `ORACLE_BASE`
- `ORACLE_HOME`
- `TNS_ADMIN`

#### Examples

Run the specified script before AutoUpgrade starts processing `deploy` mode, with the `Y` flag set to stop AutoUpgrade if the script fails:

    sales.before_action=/user/path/script.sh Y

Run the specified script before AutoUpgrade starts processing, with AutoUpgrade set to continue to run if the script fails:

    sales4.before_action=/user/path/script.sh

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### catctl_options

(Optional) Specifies one or more of a set of `catctl.pl` options that you can select for AutoUpgrade to submit for `catctl.pl` to override default behavior.

#### Usage Notes

Available `catctl.pl` options:

- `-n` Number of processes to use for parallel operations. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) . For Classic upgrades, the default for `CDB$ROOT` is 8.
- `-N` Number of processors to use when upgrading PDBs. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) For Classic upgrades, the default is 2
- `-T` Takes offline user schema-based table spaces.
- `-z` Turns on production debugging information for `catcon.pl`.

#### Examples

    sales4.catctl_options=-n 24 -N 4

**Related Topics**

- [Upgrade Script (catctl.pl) Parameters](../upgrd/upgrading-parallel-upgrade-utility-catctl-pl.md)

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### checklist

(Optional) Specifies the path to a checklist that you can use to override the default list of fixups that AutoUpgrade performs, such as fixups that you do not want implemented automatically, due to policy or security concerns.

#### Usage Notes

To use this parameter during other AutoUpgrade modes, you must run AutoUpgrade in `analyze` mode. After AutoUpgrade finishes the analysis, you can then find the checklist file identified by the database name under the precheck directory (`dbname``_checklist.cfg`). Update the file manually to exclude the fixups that you want AutoUpgrade to bypass, and save the file with a new name. When you run AutoUpgrade again, you can specify the parameter pointing to the checklist file that you created, and modify fixups that are performed for individual databases. If you do not specify a checklist file path, then the set of fixups that run during the upgrade is the latest version of the checklist file that is created during the deploy mode that you specified.

#### Examples

    sales.checklist=/u01/app/oracle/upgrade-jobs/salesdb_checklist.cfg

In the preceding example, `salesdb_checklist.cfg` is the checklist configuration file for the database `salesdb`.

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### del_after_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed after upgrade.

#### Examples

    sales3.del_after_upgrade_pfile=/path/to/my/pfile_del.ora

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### del_during_upgrade_pfile

(Optional) Specifies a path and file name of a PFILE whose parameters you want to have removed during upgrade.

#### Examples

    sales3.del_during_upgrade_pfile=/path/to/my/oldpfile.ora

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### drop_win_src_service

(Optional) For upgrades on Microsoft Windows, specifies whether to drop the Windows operating system service for the source Oracle Database after upgrade.

#### Usage Notes

By default, for Oracle Database upgrades on Microsoft Windows operating systems, after AutoUpgrade shuts down the Windows Oracle Database service and completes the upgrade, it leaves the service in place. Leaving the service down but in place gives you the option to restore the database to the source Oracle home without having to recreate the Microsoft Windows service for the database. However, you can choose to have the Microsoft Windows service for the source database removed automatically after upgrade is completed successfully. If either `no` is specified, or no value is is specified, then the service is shut down on the source, but left in place after the upgrade.

#### Options

    [yes | no]

The default value is `no`.

#### Examples

    upg1.drop_win_src_service=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### env

(Optional) Specifies custom operating system environment variables set on your operating system, excluding `ORACLE_SID`, `ORACLE_HOME`, `ORACLE_BASE`, and `TNS_ADMIN`.

#### Usage Notes

Use this parameter to provide environment setting that are indicated in the database `sqlnet.ora` file, such as secure socket layer cipher suites that are used for Oracle Wallet. Multiple settings are comma-delimited.

Syntax:

    prefix=VARIABLE1=value1 [, VARIABLE2=value2, ...]

#### Example

Assume that for the PDB `sales2`, the value for `WALLET_LOCATION` is set using custom environment variables:

    WALLET_LOCATION=
      (SOURCE=
        (METHOD=file)
        (METHOD_DATA=(DIRECTORY=/databases/wallets/$CUSTOM_ENV1/$CUSTOM_ENV2))

In that case, for AutoUpgrade to know what those custom environment variables are, you must provide them using the `env` parameter, where `dir1` is the path indicated by the environment variable `CUSTOM_ENV1`, and `dir2` is the path specified by `CUSTOM_ENV2`:

    sales2.env=CUSTOM_ENV1=dir1,CUSTOM_ENV2=dir2

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### exclusion_list

(Optional) Sets a list of PDBs that you want to be excluded from the AutoUpgrade run. This parameter only applies to the multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.

#### Usage Notes

Use this parameter to provide a list of PDBs to exclude from the AutoUpgrade run. The PDB list is comma-delimited. It can contain either a list of PDB names, or an asterisk character (\*), which indicates that you want ot exclude all PDBs that are open on the CDB at the time that you run AutoUpgrade.

Syntax:

    prefix.exclusion_list=[pdb-name|*][,pdb-name,...]

#### Examples

Assume that you want to exclude PDBs `pdb1` and `pdb2` from the upgrade of cdb sales1. The following entry in the configuration file excludes `pdb1` and `pdb2` from being processed during the AutoUpgrade run:

    sales1.exclusion_list=pdb1,pdb2

This entry in the configuration file excludes all open PDBs from the CDB `sales2`:

    sales2.exclusion_list=*

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### ignore_errors

(Optional) Enables you to specify a comma-delimited list of specific Oracle errors that you want AutoUpgrade to ignore during the upgrade or patching process.

#### Usage Notes

If you add this parameter to your configuration file, then the error numbers that you specify are ignored during the upgrade for the upgrade prefix that you specify.

#### Examples

    sales3.ignore_errors=ORA-48181,ORA-00001

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### keep_source_pdb

(Optional) Specifies if the source PDB in an unplug-plug upgrade operation is kept in a closed state instead of being removed from the source CDB.

#### Usage Notes

By default, the source PDB is removed from the source CDB during the upgrade process. When `keep_source_pdb` is set to `YES`, the source PDB is not removed from the earlier release system. You are only able to set the parameter to `YES` when the copy option is specified in the parameter `target_pdb_copy_option`. When the copy option is not used, this parameter is ignored, because the PDB must be dropped. Without a copy, the existing datafiles can only be used by a single CDB.

#### Options

    [yes | no]

The default value is `no`.

#### Example

    sales1.keep_source_pdb=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### log_dir

(Optional) Sets the location of log files that are generated for database upgrades that are in the set of databases included in the upgrade job identified by the prefix for the parameter.

#### Usage Notes

When set, AutoUpgrade creates a hierarchical directory based on a local log file path that you specify. For example, where the job identifier prefix is `sales`, and where `log_dir` is identified as `upgrade-jobs`, and `stage1`, `stage2`, and `stagen` represent stages of the upgrades:

    /u01/app/oracle/upgrade-jobs
                                          /temp/
                                          /sales/
                                          /sales/stage1
                                          /sales/stage2
                                          /sales/stagen

You cannot use wild cards for paths, such as tilde (`~`). You must use a complete path.

#### Example

    salesdb.log_dir=/u01/app/oracle/upgrade-jobs

By default, if the global configuration file parameter `global.autoupg_log_dir` is specified, and you do not specify `log_dir`, then the default is the path specified in `global.autoupg_log_dir`.

When neither `global.autoupg_log_dir` nor `log_dir` is specified, then by default the log files are placed in the location indicated by the `orabase` utility for the databases that you include in your configuration file. In that case, the default logs directory is in the path `ORACLE_BASE``/cfgtoollogs/autoupgrade`.

If the `orabase` utility fails for all databases included in the configuration file, then the log file location is then based on the `temp` directory for the user running AutoUpgrade.

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### manage_standbys_clause

(Optional) Specifies whether standby Oracle Data Guard standby databases you identify by `DB_UNIQUE_NAME` are excluded from AutoUpgrade plug-in upgrades, so that standby database files can be reused.

#### Usage Notes

Before upgrades of database configurations with standby databases, to reduce potential issues, Oracle recommends that you run AutoUpgrade in analyze mode on your standby databases.

#### Options

In the following syntax, `pdb-name` is a `DB_UNIQUE_NAME` of a source PDB that you are upgrading to the target CDB in an unplug/plug upgrade.

    manage_standbys_clause=STANDBYS=[STANDBYS=NONE|STANDBYS=ALL|STANDBYS=ALL EXCEPT ('pdb-name', 'pdb-name', ...)|STANDBYS=('pdb-name', 'pdb-name', ...)]

The default value is `NONE`.

#### Examples

In the following example, any non-CDB or pluggable database that is a member of an Oracle Data Guard standby is not excluded from AutoUpgrade plug-in upgrades:

    upg2.sid=cdb1
    upg2.pdbs=*
    upg2.target_cdb=cdb21x
    upg2.source_home=/source/18x
    upg2.target_home=/target/21x
    upg2.manage_standbys_clause=standbys=none

In the following example, applying the redo on data files on all standby databases is deferred on all AutoUpgrade plug-in upgrades:

    upg3.sid=cdb2
    upg3.pdbs=*
    upg3.target_cdb=cdb21x
    upg3.source_home=/source/18x
    upg3.target_home=/target/21x
    upg3.manage_standbys_clause=standbys=all

In the following example, during the AutoUpgrade plug-in upgrades, applying the redo on data files is deferred on all standby PDBs except PDBs `cdb3_stby_1` and `cdb3_stby_2`.

    upg4.sid=cdb3
    upg4.pdbs=*
    upg4.target_cdb=cdb21x
    upg4.source_home=/source/12.2x
    upg4.target_home=/target/21x
    upg4.manage_standbys_clause=standbys=all except ('cdb3_stby_1','cdb3_stby_2')

In the following example, during the AutoUpgrade plug-in upgrades, applying the redo on data files is deferred only on standby PDB `cdb4_stby1`.

    upg4.sid=cdb4
    upg4.pdbs=*
    upg4.target_cdb=cdb21x
    upg4.source_home=/source/12.2x
    upg4.target_home=/target/21x
    upg4.manage_standbys_clause=standbys=('cdb4_stby_1')

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### pdbs

(Optional) Sets a list of PDBs on which you want the upgrade to run. This parameter only applies to upgrades of multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.

#### Usage Notes

The PDB list is comma-deliminated. The list can contain either PDB names, or a star character (`*`), which indicates that you want to upgrade all PDBs that are open on the CDB at the time that you run AutoUpgrade. If the parameter is not specified, then the default value is `*`.

If running in `ANALYZE` mode, AutoUpgrade ignores the PDBs in a mounted state.

If running in `FIXUPS`, `DEPLOY` or `UPGRADE` mode, AutoUpgrade opens the PDBs in mount state in read-write mode, upgrade mode, or both, depending on the execution mode.

#### Example

    sales1.pdbs=pdb1, pdb2, pdbn
       upgr1.pdbs=*

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### raise_compatible

(Optional) Increases the Oracle Database `COMPATIBLE` initialization parameter to the default value of the target release after the upgrade is completed successfully.

#### Usage Notes

Options:

- `Y` : Increase the `COMPATIBLE` parameter setting to the target release
- `N` : Do not increase the `COMPATIBLE` parameter setting to the target release

The default is `N`.

**Caution:**

- After the `COMPATIBLE` parameter is increased, database downgrade is not possible.
- Oracle recommends that you only raise the `COMPATIBLE` parameter to the current release level after you have thoroughly tested the upgraded database.
- Regardless of what value you use for the `autoupgrade` command-line parameter `restore`, if you set the value of the configuration file parameter `raise_compatible` to `yes`, then before starting the upgrade, you must delete manually any guaranteed restore point you have created. After the upgrade is completed successfully, AutoUpgrade deletes the guaranteed restore point it creates before starting the upgrade. When AutoUpgrade starts the POSTUPGRADE stage, there is no way to restore the database.

#### Example

    sales1.raise_compatible=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### remove_rac_config

(Optional) Specifies whether to remove a non-CDB Oracle RAC database from clusterware on the source Oracle home after a successful conversion to the target CDB home, or to leave the source database unchanged.

#### Usage Notes

By default, the source Oracle RAC database configuration on a non-CDB is removed from the source Oracle Grid Infrastructure when it is migrated to a CDB during the upgrade process. When `remove_rac_config` is set to `no`, the source Oracle RAC database is not removed from the earlier release non-CDB system.

#### Options

    [yes | no]

The default value is `yes`.

#### Example

    upg1.remove_rac_config=no

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### remove_underscore_parameters

(Optional) Removes underscore (hidden) parameters from `PFILE` files during upgrade, and after upgrade, for all Oracle Databases in the configuration file.

#### Usage Notes

Underscore parameters should only be used by advice of Oracle Support.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales1.remove_underscore_parameters=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### replay

(Optional) Specifies whether to use replay to upgrade the database.

#### Usage Notes

By default, AutoUpgrade performs a Classic upgrade to upgrade the database.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    upg1.replay=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### restoration

(Optional) Generates a Guaranteed Restore Point (GRP) for database restoration.

#### Usage Notes

If you set `restoration=no`, then both the database backup and restoration must be performed manually. Use this option for databases that operate in `NOARCHIVELOG` mode, and for Standard Edition and Standard Edition 2 databases, which do not support the Oracle Flashback technology feature Flashback Database. If you do not specify the parameter, then the default value (`yes`) is used, and a guaranteed restore point is created.

#### Options

`[yes | no]`

The default value is `yes`.

#### Example

    sales1.restoration=no

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### revert_after_action

(Optional) Specifies a custom action that you want to have run on the operating system after a system restoration is completed for the specific database job addressed by the prefix, and the database is up.

#### Usage Notes

The action that you specify with `revert_after_action` runs on the target Oracle home binaries after the restoration process is completed, and the database is up.

The script that you specify to run must be in the form of `name``.``ext` (for example, `myscript.sh`), so that AutoUpgrade can identify the type of script that you want to run. Permitted extension options:

- Unix shell (`.sh`)
- Microsoft Windows batch (`.bat`, `.cmd`)
- Microsoft Windows PowerShell (`.ps1`)
- Oracle SQL script (`.sql`), with a local operation on the database designated by the `revert_before_action` parameter prefix.

#### Options

Stop on fail: \[`Y|N`\]. The default is N.

By default, if the specified script fails, then AutoUpgrade continues to run (`N`. To specify that AutoUpgrade stops if the script fails, use the `Y` flag. If the script finishes running on the operating system with a status different than `0`, then AutoUpgrade identifies the script as failed.

#### Examples

Run the script you specify on the operating system after AutoUpgrade completes processing the restoration, with the `Y` flag set to stop AutoUpgrade if the script fails:

    sales3.revert_after_action =/user/path/script.sh Y

Run the script you specify on the operating system after AutoUpgrade completes processing the restoration. With no flag, the default stop on fail option is `N`, so AutoUpgrade continues to run if the script fails:

    sales3.revert_after_action =/user/path/script.sh

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### revert_before_action

(Optional) Specifies a custom action that you want to have run on the operating system before a system restoration is completed for the specific database job addressed by the prefix, and the database is up.

#### Usage Notes

The action that you specify with `revert_before_action` runs on the target Oracle home binaries before database restoration is started, and the database is up.

The script that you specify to run must be in the form of `name``.``ext` (for example, `myscript.sh`), so that AutoUpgrade can identify the type of script that you want to run. Permitted extension options:

- Unix shell (`.sh`)
- Microsoft Windows batch (`.bat`, `.cmd`)
- Microsoft Windows PowerShell (`.ps1`)
- Oracle SQL script (`.sql`), with a local operation on the database designated by the `revert_before_action` parameter prefix.

#### Options

Stop on fail: \[`Y|N`\]. The default is `N`.

By default, if the specified script fails, then AutoUpgrade continues to run (`N`. To specify that AutoUpgrade stops if the script fails, use the `Y` flag. If the script finishes running on the operating system with a status different than `0`, then AutoUpgrade identifies the script as failed.

#### Examples

Run the script you specify on the operating system before AutoUpgrade starts the restoration, with the `Y` flag set to stop AutoUpgrade if the script fails:

    sales3.revert_before_action =/user/path/script.sh Y

Run the script you specify on the operating system before AutoUpgrade starts the restoration. With no flag, the default stop on fail option is `N`, so AutoUpgrade continues to run if the script fails:

    sales3.revert_before_action =/user/path/script.sh

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### run_hcheck

(Optional) Specifies whether you run Oracle Dictionary Health Checks as part of preupgrade checks to identify database dictionary inconsistencies.

#### Usage Notes

To help to identify database dictionary inconsistencies, you can specify that AutoUpgrade runs the `DBMS_HCHECK` PL/SQL package on the source database as part of preupgrade checks. If set, the AutoUpgrade `run_hcheck` parameter enables you to specify for each upgrade source database that AutoUpgrade runs either the full array of Oracle Dictionary Health Checks on the database dictionary, or that it runs only the most critical set of checks. If the check detects potential or critical problems with the database dictionary, then it prevents the upgrade from starting.

Oracle Dictionary Health Check results are stored under the AutoUpgrade precheck directory in the format `dbname``_healthcheck_result.log`, where `dbname` is the name of the database on which the check was run. For more information about Oracle Dictionary Health Check, refer to the `DBMS_HCHECK` package documentation in Oracle Database PL/SQL Packages and Types Reference.

#### Options

`[full| critical]`

If the parameter is not set, then the default is to not run `DBMS_HCHECK`.

#### Example

    sales1.run_hcheck=full
    sales2.run_hcheck=critical

**Related Topics**

- [DBMS_HCHECK](../arpls/dbms-dictionary-check.md)

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### run_utlrp

(Optional) Enables or disables running `utlrp` as part of the upgrade.

#### Usage Notes

The `utlrp` utility recompiles all Data Dictionary objects that become invalid during a database upgrade. Oracle recommends that you run this utility after every Oracle Database upgrade.

#### Options

`[yes | no]`

The default value is `yes`.

#### Example

    prefix.run_utlrp=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### sid

(Required) Identifies the Oracle system identifier (SID) of the database that you want to upgrade.

#### Example

    sales1.sid=salesdb

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### skip_tde_key_import

(Optional) When set to `yes`, the upgrade is run, but import of the source database KeyStore into the target database is skipped, without raising an error.

#### Usage Notes

**Note:**

This parameter is deprecated, because it is no longer needed. It can be removed in a future AutoUpgrade release. Instead of using this parameter, Oracle recommends that you either use the `-load_password` command line option to add the TDE password to AutoUpgrade's keystore, or add the TDE password to a Secure External Password Store (SEPS).

You can use this option for nonCDB-to-PDB and unplug/plug operations. When import of the source database KeyStore into the target database is skipped, AutoUpgrade will leave the PDB open in upgrade mode, so that you can import the keys manually yourself. After you import the keys, you must then restart the database in normal mode.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales1.skip_tde_key_import=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### source_base

(Optional) Specifies the source `ORACLE_BASE` path for the source Oracle home.

#### Examples

    source_base=/u01/app/oracle
    sales4.source_base=/u04/app/oracle4

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### source_dblink

(Optional) Specifies the database link set up for an unplug-plug relocate (hot clone) upgrade.

#### Usage Notes

To set up an unplug-plug relocate upgrade for a non-CDB or a PDB, you must first set up a database link between the source database and the target database location. You then pass that database link to AutoUpgrade using the `source_dblink` parameter. You identify source database name associated with the database link as a suffix to `source_dblink`. parameter. You also have the option to specify a time value, in seconds, that the database is refreshed from the database link.

**Note:**

This option is available for source database releases Oracle Database 12.1.0.2 and later.

The `source_dblink` parameter becomes active when you use the `target_pdb_copy_option` parameter. When you use `source_dblink`, you must also must specify a value for the `file_name_convert` parameter, either to convert file names, or to specify not to convert file names. If `file_name_convert` is set to `none`, then you must also set `db_create_file_dest` to specify where you want to place the database files.

You can also choose to set a refresh interval, in seconds, specifying how frequently the target database is updated over the database link from the source database. You can use the refresh interval with the `start_time` parameter to keep the source database refreshed for the target location. If no refresh rate is specified, then the source database is cloned only one time, and no refresh occurs. If the refresh rate is specified, but you do not specify a future start time using the `start_time` parameter, then the refresh interval value is ignored, and the database is cloned only one time.

#### Options

- (Required) The source database name, specified as a suffix.
- (Required) The name of the database link that you created.
- (Optional) The refresh rate for the target database from the source database, in seconds. If you specify a refresh rate, then typically you also specify a future start time using the `start_time` parameter.
- (Optional) `CLONE_ONLY`. Adding this option specifies that the PDB that is created is a clone that is never refreshed, and that the upgrade is started immediately after the clone operation is completed. This option is required when the source is Oracle Database 12.1 (Release 12.1.0.2).

#### Examples

In the following example, two database links are created:

- `pdbxcdb18x_link`, created on the PDB source database named `pdbx`:

      CREATE DATABASE LINK pdbxcdb18x_link CONNECT TO remote-user IDENTIFIED BY password
      USING'(DESCRIPTION =(ADDRESS = (PROTOCOL = TCP)(HOST
      GRANT CREATE SESSION, CREATE PLUGGABLE DATABASE, SELECT_CATALOG_ROLE TO remote-user;
      GRANT READ ON sys.enc$ TO remote-user;

- `db18x_link`, created on the non-CDB source database named `db18x`:

      CREATE DATABASE LINK db18x_link CONNECT TO remote-user IDENTIFIED BY password
      USING'(DESCRIPTION =(ADDRESS = (PROTOCOL = TCP)(HOST = db-node1)(PORT = 1521))
      (CONNECT_DATA = (SERVICE_NAME = db18x)))';

In the AutoUpgrade configuration file, the database name associated with the database link is specified by using that name as a suffix to `source_dblink`: The suffix: `pdbx` for the PDB source database, and the suffix `db18x` for the non-CDB source database.

In the following example, `source_dblink` is used to specify the dblink for the source database `pdbx`. The PDB upgrade deployment starts immediately after you start AutoUpgrade, because no time interval is specified:

    upg1.source_dblink.pdbx=pdbxcdb18x

Using the same configuration file, AutoUpgrade starts the upgrade of the database named `db18x` in 1 hour and 40 minutes after AutoUpgrade is started from the command line. Between the time that AutoUpgrade is started, and the deployment time specified by `start_time`, the cloned target database is refreshed every 20 seconds from the source.

    upg1.source_dblink.db18x=db18x_link 20
    upg1.start_time=+1h40m

In the following example, the source database `db18x` is cloned to the target PDB `db18x_link`, and the upgrade is started immediately after that source database is cloned successfully:

    upg1.source_dblink.db18x=db18x_link CLONE_ONLY

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### source_home

(Required for analyze, fixups, and deploy modes. Optional for upgrade mode.) Current Oracle home (`ORACLE_HOME`) of the database that you want to upgrade.

#### Usage Notes

For the mode `upgrade`, the source home and target home values can be the same path.

#### Example

    sales2.source_home=/path/to/my/source/oracle/home

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### source_ldap_admin_dir

(Optional) Specifies the path to the `LDAP_ADMIN` directory in the source database home.

#### Usage Notes

This parameter has no effect on Microsoft Windows, because on Windows, the `LDAP_ADMIN` environmental variable is set within the registry.

#### Example

    sales1.source_ldap_admin_dir=/u01/app/oracle/12.2/dbhome01/ldap/admin

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### source_tns_admin_dir

(Optional) Specifies the path to the `TNS_ADMIN` directory in the source database home.

#### Usage Notes

This parameter has no effect on Microsoft Windows, because on Windows, the `TNS_ADMIN` environmental variable is set within the registry.

#### Example

    sales1.source_tns_admin_dir=/u01/app/oracle/12.2/dbhome01/network/admin

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### start_time

(Optional) Sets a future start time for the upgrade job to run. Use this parameter to schedule upgrade jobs to balance the load on your server, and to prevent multiple jobs from starting immediately.

#### Usage Notes

Values must either take the form `now` (start immediately), or take the English Date Format form DD/MM/YYYY or MM/DD/YYYY, where MM is month, DD is day, and YYYY is year. If you do not set a value, then the default is `now`.

Permitted values:

    now
    30/12/2019 15:30:00
    01/11/2020 01:30:15
    2/5/2020 3:30:50

If more than one job is started with the `start_time` value set to `now`, then AutoUpgrade schedules start times based on resources available in the system, which can result in start time for jobs that are separated by a few minutes.

Values are invalid that use the wrong deliminator for the date or time element, or that use the wrong date or hour format, such as the following:

    30-12-2019 15:30:00
    01/11/2020 3:30:15pm
    2020/06/01 01:30:15

#### Examples

    sales1.start_time=now
    sales2.start_time=07/11/2020 01:30:15

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_base

(Optional) Specifies the target `ORACLE_BASE` path for the target Oracle home.

#### Examples

    target_base=/u01/app/oracle
    sales4.target_base=/u04/app/oracle4

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_cdb

(Optional) Specifies the `SID` of the target CDB into which a non-CDB Oracle Database is plugged in. This parameter is mandatory when you want to upgrade and convert a non-CDB Oracle Database.

#### Example

    emp.target_cdb=salescdb

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_pdb_copy_option=file_name_convert

(Optional) Specifies the `file_name_convert` option used by the create pluggable database statement that AutoUpgrade runs when converting a non-CDB database to a PDB or an existing PDB from a different source CDB into a PDB in the specified target CDB.

#### Usage Notes

**Caution:**

Specifying `target_pdb_copy_option` enables AutoUpgrade to manage the recovery as needed. When `target_pdb_copy_option` is not set, and the default `nocopy` option is used, there is no recovery of the default PDB. Ensure that you have a backup of your source PDB.

This option is only used when creating a pluggable database within the target CDB. If you do not specify this parameter, then the default value of the parameter is `NOCOPY`, and existing data files on the source database are reused. When you do specify this parameter, then you must append a suffix to the parameter that specifies either the source database name or PDB name (`target_pdb_copy_option.``suffix`, and specify `file_name_convert=` with one of the following options:

- Specify source file names (f) and target replacement file names (r) ('f', 'r'), or specify `NONE`
- If you are creating a refreshable clone database, then append a suffix to the parameter that specifies either the source database name or PDB name (`target_pdb_copy_option.``suffix`

On the target CDB, if you are using ASM, or if you have the parameters `DB_CREATE_FILE_DEST` or `PDB_FILE_NAME_CONVERT` set, and you want these parameters on the target CDB to take effect for replacement file names, then set the value of `prefix``.target_pdb_copy_option.``source-db-name-or-pdb``=file_name_convert=NONE`.

If you want one or more data file names changed during conversion on the target CDB, then enter values for the parameter to indicate the source database name or PDB, specified as a suffix, the source filename you want to change, and the target filename to which you want the existing files copied, using the syntax `prefix``.target_pdb_copy_option.``source-db-name-or-pdb``=('``f1``', '``r1``', '``f2``', '``r2'``, . . .)`, where `f1` is the first filename pattern on your source, `r1` is the first replacement filename pattern on your target CDB, `f2` is the second filename pattern on your source, `r2` is the second replacement file pattern on your target CDB, and so on.

#### Syntax

    prefix.target_pdb_copy_option.source-db-name-or-pdb=file_name_convert=('f1', 'r1', 'f2', 'r2', 'f3', 'r3'...)

#### Example

In this example, AutoUpgrade will copy existing datafiles during conversion of a database specified with the prefix string `upg1`, and with the suffix `sales` to replace the file path string and filename `/old/path/pdb_2` with the file path string and filename `/new/path/depsales`:

    upg1.target_pdb_copy_option.sales=file_name_convert=('/old/path/pdb_2', '/new/path/depsales')

To convert OMF files with `target_pdb_copy_option``source-db-name-or-pdb``=file_name_convert`, the target Oracle home must be Oracle Database 19c Release Update 6 or later (19.6.0), or Oracle Database 18c Release Update 10 or later (18.10.0).

In this example, the parameter is configured so that data files that are stored on Oracle ASM, but not stored as Oracle-managed files, are copied from `+DATA/dbname/sales` to `+DATA/dbname/depsales`:

    upg1.target_pdb_copy_option.sales=file_name_convert=('+DATA/dbname/sales', '+DATA/dbname/depsales')

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_pdb_name

(Optional) Specifies the name that you want to assign to a non-CDB source Oracle Database after it is plugged in to the target CDB.

#### Usage Notes

This parameter is optional. It is used when you want to upgrade and convert a non-CDB Oracle Database to a PDB, or you want to unplug a PDB from a source release CDB and plug it in for an upgrade to a targetr release CDB.

When you upgrade and convert an existing non-CDB database to a PDB on a target CDB, the `target_cdb` parameter is mandatory, because it specifies the target CDB. If you want to determine how the PDB is created on the target CDB, you can use the optional parameters `target_pdb_name` and `target_pdb_copy_option` to specify how the PDB is created on the target CDB. However, if neither optional parameters are used, then a full upgrade of the source CDB is performed.

The default name for the target PDB when you convert a non-CDB to a PDB is to use the database unique name of the non-CDB Oracle Database. To specify a name that is different from the existing name of the non-CDB when you plug it in to the CDB, set the new name by using `target_pdb_name`. In addition, if you are creating a refreshable clone database, then append a suffix to the parameter that specifies either the source database name or PDB name (`target_name``.``suffix`)

#### Examples

In the following example, the source non-CDB database is `emp19`. The target_pdb_name parameter is used to change the name to `emp23pdb` on the target CDB database.

    upg.target_pdb_name=emp23pdb

For a refreshable clone, add a prefix to indicate the source database for the clone. In this example, the the source container database is `db122b` and we are cloning `pdb1` from `db122b` into the target container database `db19`. The suffix `pdb1` is used as the identifier for both `target_pdb_name` and `source_dblink`. The `pdb1` suffix identifier associates both the target pdb name and the dblink used to move the data from the source, `pdb1`, into the target PDB `PLUG122`.

    global.autoupg_log_dir=/tmp/logs
    upg1.source_home=/u01/app/oracle/122
    upg1.target_home=/u01/app/oracle/19
    upg1.sid=db122b
    upg1.target_cdb=db19
    upg1.pdbs=pdb1
    upg1.target_pdb_name.pdb1=PLUG122
    upg1.target_pdb_copy_option.pdb1=file_name_convert=('/u01/app/oracle/oradata/db122b/pdb1', '/u01/app/oracle/plug/pdb122b')
    upg1.source_dblink.pdb1=pdbxcdb122x_link

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_ldap_admin_dir

(Optional) Specifies the path to the `LDAP_ADMIN` directory in the target database home.

#### Example

    sales1.target_ldap_admin_dir=/u01/app/oracle/19/dbhome01/ldap/admin

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### target_tns_admin_dir

(Optional) Specifies the path to the `TNS_ADMIN` directory in the target database home.

#### Example

    sales1.target_tns_admin_dir=/u01/app/oracle/19/dbhome01/network/admin

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### timezone_upg

(Optional) Enables or disables running the time zone upgrade as part of the AutoUpgrade process.

#### Usage Notes

To preserve data integrity, Oracle recommends that you upgrade the time zone file (`DST`) settings at the time of your database upgrade. In particular, upgrade the timezone when you have data that depend on the time zone, such as `timestamp with time zone` table columns. Note that this setting can be disabled by overwriting the fixup on the checklist file.

If you explicitly disable the time zone file upgrade in your AutoUpgrade configuration file, then Oracle recommends that you perform this task either as part of your upgrade plan, or at a later point in time.

#### Options

`[yes | no]`

The default value is `yes` for upgrade, and `no` for patching.

#### Example

    sales1.timezone_upg=no

**Note:**

If you patch a database with RU 19.18 or later, then updated time zone files are installed in the Oracle home by default. A new database created with Database Configuration Assistant (DBCA) in a patched Oracle home will be created with the latest time zone files.

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### tune_setting

(Optional) Enables special workflows that alter the behavior of AutoUpgrade during runtime, depending on the workflow option that you specify.

#### Usage Notes

The `tune_setting` parameter enables you to fine-tune upgrade steps or the resources allocated to the processing of the upgrades specified by the container databases or pluggable databases (CDBs or PDBs) specified by the parameter prefix in your AutoUpgrade configuration file. This capability can be useful for some upgrades if you find the default AutoUpgrade values are insufficient for your system requirements, or when you want to enable nondefault AutoUpgrade options.

#### Syntax

    prefix.tune_setting=option[, option, option, ...]

Select the `tune_setting` options that provide the AutoUpgrade runtime tuning that you require from the list that follows. To combine multiple tuning options with the `tune_setting` parameter, use comma delimiters. Example:

    sales3.tune_setting=proactive_fixups=true,query_hint_parallel=8,utlrp_threads_per_pdb=8

**Note:**

You can concatinate multiple parameters together in a single `tune_setting` entry

| Option                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `active_nodes_limit`    | Sets a new total of active cluster member nodes that you want to use during a distributed upgrade of Oracle Real Application Clusters databases. The default is 2. If the number you specify is equal to or greater than the maximum number of cluster member nodes, then all nodes are taken.<br>`sales3.tune_setting=active_nodes_limit=4`                                                                                                                                                                                                                                                                                                                                                                                   |
| `distributed_upgrade`   | Specifies that AutoUpgrade performs a **distributed upgrade**. A distributed upgrade leverages the resources of the Oracle Clusterware cluster member nodes to perform the upgrades of PDBs more rapidly on the cluster. Use this option when a CDB in an Oracle RAC cluster of at least two nodes is being upgraded. When you choose this option, the `proactive_fixups` option is also enabled by default. Example:<br>`sales3.tune_setting=proactive_fixups=true,distributed_upgrade=true`                                                                                                                                                                                                                                  |
| `make_pdbs_available`   | Opens the PDBs designated by the prefix in read/write and non-restricted mode after postfixups are complete when **proactive fixups** mode is used. This option enables PDBs designated by the prefix to become available for service immediately after the upgrade is completed, while other PDBs continue to be upgraded, which can be useful for large fleet upgrade deployments.<br>Precautions:<br>Choosing this option enables the PDBs you designate to accept service requests from users, while other PDBs are being upgraded. The response time of the PDBs for service requests, and the time required for ongoing PDB upgrades can each be affected.<br>Example:<br>`sales3.tune_setting=make_pdbs_available=true` |
| `proactive_fixups`      | Enables proactive fixups mode, where the PDBs are upgraded as the last stage of the upgrade. When the number of PDBs is higher than the CPU count defined in the database, divided by 2, choosing this tuning option can result in a faster upgrade. Example:<br>`sales3.tune_setting=proactive_fixups=true`<br>Precautions:<br>If the number of CPUs is higher than the number of PDBs, then changing this setting may not improve performance.                                                                                                                                                                                                                                                                               |
| `query_hint_parallel`   | Specifies a parallel thread specification to the code that gathers data from the tablespaces during the query of the PDBs specified by the prefix, so that you can allocate a greater number or lesser number of parallel threads to the PDBs specified by the prefix. Example:<br>`sales3.tune_setting=query_hint_parallel=8`<br>Choosing this option can cause AutoUpgrade to consume more system resources.                                                                                                                                                                                                                                                                                                                 |
| `utlrp_threads_per_pdb` | Overwrites default maximum number of threads generated by the recompilation of invalid objects in the CDB, and uses the number of threads that you specify. Example:<br>`sales3.tune_setting=utlrp_threads_per_pdb=8`<br>Precautions:<br>If the number of threads specified exceeds available threads on the system, then performance can be compromised.                                                                                                                                                                                                                                                                                                                                                                      |
| `utlrp_pdb_in_parallel` | Overwrites default maximum number of concurrent recompilation threads to the number that you specify. Use this option to overwrite the default maximum number of concurrent processes of recompilation of invalid objects. Example:<br>`sales3.tune_setting=utlrp_pdbs_in_parallel=2`<br>Precautions:<br>Each PDB process requires from the system as many threads as specified by `utlrp_threads_per_pdb`.                                                                                                                                                                                                                                                                                                                    |

#### Examples

In the following example, the database upgrades specified with the prefix `sales3` are Oracle Real Application Clusters Oracle Database instances. The `tune_setting` parameter is used to set these database instances to use the setting `distributed_upgrade`, which distributes the upgrade load across multiple CDBs in the Oracle Grid Infrastructure cluster:

    sales3.tune_setting=proactive_fixups=true,distributed_upgrade=true

In the following example, the database upgrades specified with the prefix `sales3` are tuned with multiple `tune_setting` parameter options:

    sales3.tune_setting=proactive_fixups=true,query_hint_parallel=8,utlrp_threads_per_pdb=8

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### upgrade_node

(Optional) Specifies the node on which the current user configuration is valid. The default value is `localhost`.

#### Usage Notes

The purpose of this parameter is to prevent AutoUpgrade from processing databases that are listed in the configuration file that you use with AutoUpgrade, where the value for the `upgrade_node` parameter does not correspond to the current host name. It does not enable running AutoUpgrade remotely. You can use the keyword `localhost` as a wild card to indicate that databases on the local host should be processed.

Use case:

The configuration file `config.cfg` contains 10 databases. Five of the databases have the value of `upgrade_node` set to `denver01`. The remaining five have the value of `upgrade_node` set to `denver02`. If AutoUpgrade is run on the server `denver01` using the configuration file `config.cfg`, then AutoUpgrade only processes the databases where `upgrade_node` is set to `denver01`. It ignores the databases where` upgrade_node` is set to `denver02`. The utility `hostname` identifies the value used to resolve the upgrade node.

#### Example

    hostname
    denver02
    sales1.upgrade_node=denver01

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File
