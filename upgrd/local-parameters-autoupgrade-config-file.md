## Local Parameters for the AutoUpgrade Configuration File

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
- close_source
  (Optional) Closes the source non-CDB or source PDB just before AutoUpgrade starts a non-CDB to PDB conversion, starts an unplug-relocate upgrade, or uses a refreshable clone PDB.
- del_after_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed after upgrade.
- del_during_upgrade_pfile
  (Optional) Specifies a path and file name of a PFILE whose parameters you want to have removed during upgrade.
- delete_wincredential_file
  (Optional) Deletes the Microsoft Windows credential object file when the AutoUpgrade job is complete.
- download
  (Optional for AutoUpgrade patching) Specifies whether to automatically download patches from My Oracle Support. .
- drop_grp_after_patching
  For AutoUpgrade patching, deletes the Guaranteed Restore Point (GRP) after database patch maintenance.
- drop_win_src_service
  (Optional) For upgrades on Microsoft Windows, specifies whether to drop the Windows operating system service for the source Oracle Database after upgrade.
- em_blackout_suffix
  (Optional) Enables you to specify a suffix to add to the default autoupgrade blackout
- em_target_name
  (Optional) Enables you to specify that the database that you name is monitored by Enterprise Manager so the monitoring can be updated to the new Oracle home.
- emcli_path
  (Optional) Enables you to specify the path to the Enterprise Manager Command Line Interface (EMCLI) command.
- env
  (Optional) Specifies custom operating system environment variables set on your operating system, excluding `ORACLE_SID`, `ORACLE_HOME`, `ORACLE_BASE`, and `TNS_ADMIN`.
- exclusion_list
  (Optional) Sets a list of PDBs that you want to be excluded from the AutoUpgrade run. This parameter only applies to the multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.
- folder
  (Required for AutoUpgrade patching) Specifies the directory that contains the patch zip files as well as the required Oracle Database base image.
- home_settings.option
  (Optional) A set of parameters that enable you to specify information about the source and target Oracle homes.
- ignore_errors
  (Optional) Enables you to specify a comma-delimited list of specific Oracle errors that you want AutoUpgrade to ignore during the upgrade or patching process.
- keep_pdb_save_state
  (Optional) Specifies that if the PDB has a saved state in the source CDB, then you can either save or not save the PDB state on the target CDB.
- keep_source_pdb
  (Optional) Specifies if the source PDB in an unplug-plug upgrade operation is kept in a closed state instead of being removed from the source CDB.
- log_dir
  (Optional) Sets the location of log files that are generated for database upgrades that are in the set of databases included in the upgrade job identified by the prefix for the parameter.
- manage_standbys_clause
  (Optional) Specifies whether standby Oracle Data Guard standby databases you identify by `DB_UNIQUE_NAME` are excluded from AutoUpgrade plug-in upgrades, so that standby database files can be reused.
- method
  (Optional for AutoUpgrade patching) Specifies whether to create a new target Oracle home, and if so, how it will be created.
- parallel_pdb_creation_clause
  (Optional) Specifies the number of parallel execution servers to use when creating a pluggable database. This can be used for scenarios like PDB relocate, clone PDB, etc. It doesn't apply for cases when creating a PDB using an XML file.
- patch
  (Required for AutoUpgrade patching) Specifies a comma-delimited list of the patches that you want to install.
- patch_in_upgrade_mode
  (Optional) Specifies that the database that you want to patch is patched in upgrade mode, instead of normal mode.
- patch_node
  (Optional) For AutoUpgrade patching, specifies the node on which the current user configuration is valid. The default value is `localhost`.
- pdbs
  (Optional) Sets a list of PDBs on which you want the upgrade to run. This parameter only applies to upgrades of multitenant architecture (CDB) databases. If you are plugging in and upgrading a non-CDB database, then this parameter is ignored.
- platform
  (Optional) Specifies the platform used by AutoUpgrade Patching when downloading patches from My Oracle Support.
- raise_compatible
  (Optional) Increases the Oracle Database `COMPATIBLE` initialization parameter to the default value of the target release after the upgrade is completed successfully.
- remove_rac_config
  (Optional) Specifies whether to remove a non-CDB Oracle RAC database from clusterware on the source Oracle home after a successful conversion to the target CDB home, or to leave the source database unchanged.
- remove_underscore_parameters
  (Optional) Removes underscore (hidden) parameters from `PFILE` files during upgrade, and after upgrade, for all Oracle Databases in the configuration file.
- replay
  (Optional) Specifies whether to use Replay or to use a Classic upgrade to upgrade the database.
- restoration
  (Optional) Generates a Guaranteed Restore Point (GRP) for database restoration.
- revert_after_action
  (Optional) Specifies a custom action that you want to have run on the operating system after a system restoration is completed for the specific database job addressed by the prefix, and the database is up.
- revert_before_action
  (Optional) Specifies a custom action that you want to have run on the operating system before a system restoration is completed for the specific database job addressed by the prefix, and the database is up.
- run_dictionary_health
  (Optional) Specifies whether you run Oracle Dictionary Health Checks as part of preupgrade checks to identify database dictionary inconsistencies.
- run_utlrp
  (Optional) Enables or disables running a version of `utlrp.sql` as part of post upgrade, to recompile only invalid objects in Oracle-maintained schemas.
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
  (Optional) Specifies the `SID` of the target CDB into which a non-CDB Oracle Database is plugged in.
- target_pdb_copy_option=file_name_convert
  (Optional) Specifies the `file_name_convert` option used by the create pluggable database statement that AutoUpgrade runs when converting a non-CDB database to a PDB or an existing PDB from a different source CDB into a PDB in the specified target CDB.
- target_pdb_name
  (Optional) Specifies the name that you want to assign to a non-CDB source Oracle Database after it is plugged in to the target CDB.
- target_ldap_admin_dir
  (Optional) Specifies the path to the `LDAP_ADMIN` directory in the target database home.
- target_tns_admin_dir
  (Optional) Specifies the path to the `TNS_ADMIN` directory in the target database home.
- target_version
  (Optional) For AutoUpgrade patching, specifies the target release version on which you want AutoUpgrade to perform the patch maintenance operation.
- timezone_upg
  (Optional) Enables or disables running the time zone upgrade as part of the AutoUpgrade process.
- tune_setting
  (Optional) Enables special workflows that alter the behavior of AutoUpgrade during runtime, depending on the workflow option that you specify.
- upgrade_node
  (Optional) Specifies the node on which the current user configuration is valid. The default value is `localhost`.
- wincredential
  (Optional) Specifies the location of a Microsoft Windows credential object file that you have previously generated with the AutoUpgrade command-line parameter `load_win_credential`.

**Parent topic:** [AutoUpgrade Utility Configuration Files Parameters and Options](autoupgrade-utility-configuration-files.md)

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

- `-n` Number of processes to use for parallel operations. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) . For Classic upgrades, the default for `CDB$ROOT` and `NON-CDB` databases is 8.
- `-N` Number of processors to use when upgrading PDBs. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) For Classic upgrades, the default is 2
- `-T` Takes offline user schema-based table spaces.
- `-z` Turns on production debugging information for `catcon.pl`.

#### Examples

    sales4.catctl_options=-n 24 -N 4

**Related Topics**

- [Upgrade Script (catctl.pl) Parameters](upgrading-parallel-upgrade-utility-catctl-pl.md)

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### checklist

(Optional) Specifies the path to a checklist that you can use to override the default list of fixups that AutoUpgrade performs, such as fixups that you do not want implemented automatically, due to policy or security concerns.

#### Usage Notes

To use this parameter during other AutoUpgrade modes, you must run AutoUpgrade in `analyze` mode. After AutoUpgrade finishes the analysis, you can then find the checklist file identified by the database name under the precheck directory (`dbname``_checklist.cfg`). Update the file manually to exclude the fixups that you want AutoUpgrade to bypass, and save the file with a new name. When you run AutoUpgrade again, you can specify the parameter pointing to the checklist file that you created, and modify fixups that are performed for individual databases. If you do not specify a checklist file path, then the set of fixups that run during the upgrade is the latest version of the checklist file that is created during the deploy mode that you specified.

#### Examples

    sales.checklist=/u01/app/oracle/upgrade-jobs/salesdb_checklist.cfg

In the preceding example, `salesdb_checklist.cfg` is the checklist configuration file for the database `salesdb`.

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### close_source

(Optional) Closes the source non-CDB or source PDB just before AutoUpgrade starts a non-CDB to PDB conversion, starts an unplug-relocate upgrade, or uses a refreshable clone PDB.

#### Usage Notes

During the operations described above, if `close_source` is set to `yes` (the default), then AutoUpgrade closes source non-CDB or source PDB just before starting the upgrade. Additionally, if Oracle Real Application Clusters or Oracle Grid Infrastructure (CRS) services are configured for a non-CDB source, then they are disabled before starting the upgrade.

This parameter can only be used when the source and target databases are both on the same system. When they are on different systems, the source non-CDB or PDB cannot be closed, because AutoUpgrade has no access to it.

#### Options

    [yes | no]

The default value is `yes`.

#### Examples

    sales3.close_source=yes

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

### delete_wincredential_file

(Optional) Deletes the Microsoft Windows credential object file when the AutoUpgrade job is complete.

#### Usage Notes

When set to `NO`, AutoUpgrade does not delete the Microsoft Windows file credential after the AutoUpgrade job first using the credential is completed. The default value is `YES`.

The purpose of this parameter is to enable you to choose whether AutoUpgrade immediately deletes the Microsoft Windows object credentials loaded with the `wincredential` parameter after these credentials are first used, or if you want to be able to reuse the Windows object credential with other AutoUpgrade patching or upgrading operations.

**Note:**

If you set `delete_wincredential_file` to `NO`, then you must manually delete that credential after your AutoUpgrade jobs are complete. AutoUpgrade provides a notice in the postupgrade summary report to tell you that the Windows credential file was not removed, and that you should remove this credential file manually.

Use case:

You are performing multiple upgrades or patching operation with AutoUpgrade, and you want to specify credentials for the owner of database binaries on a Microsoft Windows server for more than one upgrade or patching operation so that they can all complete automatically. When you specify the `wincredential` parameter to load the credentials, and then also specify `delete_wincredential_file` to `NO`, AutoUpgrade can use that credential for multiple upgrades or patches of the same Oracle Database, or for different Oracle Databases. To use this feature, you must have already created the Windows PowerShell credential object, and then specify that credential object in the configuration file using `wincredential`.

#### Example

In the following example, the local configuration file setting `wincredential` provides the location where the Microsoft Windows credentials have been loaded, and `delete_wincredential_file=NO` specifies that AutoUpgrade does not automatically delete the Windows object credential file after the `db12201` database operation is complete.

    global.autoupg_log_dir=C:\Users\oracle\autoupg
    global.target.version=19.0.0
    global.target_home=C:\u01\app\oracle\product\19\dbhome_1

    upg1.sid=db12201
    upg1.source_home=C:\u01\app\oracle\product\12.2\dbhome_1
    upg1.log_dir=C:\Users\Oracle\autoupg
    upg1.upgrade_node=localhost
    upg1.target_base=C:\u01\app\oracle
    upg1.target_version=19.0.0.0
    upg1.wincredential=C:\Users\oracle\cred
    upg1.delete_wincredential_file=NO

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### download

(Optional for AutoUpgrade patching) Specifies whether to automatically download patches from My Oracle Support. .

#### Usage Notes

Specifies whether to automatically download patches from My Oracle Support. The default is YES.

When set to YES, you must either load My Oracle Support (MOS) credentials or an OAUTH token into AutoUpgrade Patching at the command line using the `-load_password` command-line option.

The patches that are downloaded are placed into the directory folder specified by the `folder` parameter.

If proxy information is required to connect to My Oracle Support, then set proxy values using the Linux operating system environment variables `https_proxy`, `http_proxy`, and `no_proxy`.

The supported format of the proxy definition is as follows, where `user_info` is a user account, `site` is a URL, and `port` is a designated port for the proxy listener:

    [https|http|socks5|socks]://(user_info@)site:port

Adding `user_info `to the proxy definition is optional, and has a format of username:password for the credentials of the proxy.

#### Options

    [yes | no]

The default value is `yes`.

#### Examples

Override the default (yes) so that you use patches that you have downloaded manually instead of having AutoUpgrade download the patches automatically:

    upg1.download=no

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### drop_grp_after_patching

For AutoUpgrade patching, deletes the Guaranteed Restore Point (GRP) after database patch maintenance.

#### Usage Notes

If you select this parameter option, then GRP is deleted after the AutoUpgrade patch maintenance completes successfully.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales4.drop_grp_after_patching=yes

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

### em_blackout_suffix

(Optional) Enables you to specify a suffix to add to the default autoupgrade blackout

#### Usage Notes

The Enterprise Manager command-line interface (EMCLI) enables AutoUpgrade to use scheduled blackouts to suspend any data collection activity on one or more monitored targets. Use this parameter to provide a specific suffix for AutoUpgrade blackouts. By default, when you enable the use of EMCLI to create blackouts, the default blackout name in the EMCLI log file is as follows, where sid is the system identifier of the database where the blackout is enabled:

`blackout_AutoUpgrade_``sid`

If you specify `em_blackout_suffix`, then in addition to the system identifier (`sid`), you can specify a suffix, so that you can track AutoUpgrade processes more precisely (`blackout-suffix`).

#### Syntax

    em_blackout_AutoUpgrade_sid_blackout-suffix

#### Example

Suppose you are updating a set of upgrades in your configuraiton file, and in the set of upgrades specified with the prefix `upg1`, you want to attach a suffix to the database with the system identifier `sales1`. The suffix you choose is `q3-updates`. To do this, you use em_blackout_autoupgrade as follows:

    upg1.em_blackout_autoupgrade_sid_q3-updates

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### em_target_name

(Optional) Enables you to specify that the database that you name is monitored by Enterprise Manager so the monitoring can be updated to the new Oracle home.

#### Usage Notes

AutoUpgade can use the Enterprise Manager command-line interface (EMCLI) to update Enterprise Manager monitoring to the new Oracle Database home. However, you must provide the name of the database so that AutoUpgade is configured to update the database to the new Oracle home.

#### Syntax

Enter the parameter in your configuration file, where `database-sid` is the database system identifier for the database where you need to update the monitored Oracle home:

    em_target_name=database-sid

#### Example

Update the Enterprise Manager monitored database `sales1` to point to the new Oracle Home

    upg1.em_target_name=sales1

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### emcli_path

(Optional) Enables you to specify the path to the Enterprise Manager Command Line Interface (EMCLI) command.

#### Usage Notes

AutoUpgade can use the Enterprise Manager command-line interface (EMCLI) to perform tasks during upgrade or patching. However, to access the command, you must provide AutoUpgrade the path to the EMCTL path for the database that EMCTL is monitoring to update the monitored database to the new Oracle home.

#### Syntax

    emctl_path=path-to-emctl-location

#### Example

Suppose you are updating a set of upgrades in your configuration file, and in the set of upgrades specified with the prefix `upg1`, you want to update Enterprise Manager monitored databases to their new Oracle home. The path to the Enterprise Manager command-line interface home is `var/opt/dbascripts/emcli/`. To do this, you use `emctl_path` as follows:

    upg1.emctl_path=var/opt/dbascripts/emcli/

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

### folder

(Required for AutoUpgrade patching) Specifies the directory that contains the patch zip files as well as the required Oracle Database base image.

#### Usage Notes

For AutoUpgrade to perform patching, you must identify the directory that contains the patch zip files. This directory must also contain the Oracle Database base image. There is no default value. You must provide the directory path. This parameter also is used in conjunction with the download parameter as follows:

When `download=YES`, the directory specified by the `folder` parameter is the directory to which the patches will be downloaded

When `download=NO`, the directory specified by the `folder` parameter is the directory that must contain the patches that have been manually downloaded.

The directory that you specify with the `folder` parameter must contain the base image of the source database's release (for example, Oracle Database Release 19.3).

#### Examples

    upg1.folder=/storage/patches

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### home_settings.option

(Optional) A set of parameters that enable you to specify information about the source and target Oracle homes.

This option enables you to use AutoUpgrade to enable or disable many database components at the binary level.

- home_settings.account_type
  (Optional) On Microsoft Windows, this option specifies the type of account to use when creating the target ORACLE_HOME.
- home_settings.binopt.asm
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle ASM (`asm`) turned ON or OFF.
- home_settings.binopt.dm
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Data Mining (`dm`) turned ON or OFF.
- home_settings.binopt.jox
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for the JavaVM JIT Compiler (jox) turned ON or OFF.
- home_settings.binopt.olap
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for the On Line Application Processing (OLAP) options (`olap`) turned ON or OFF.
- home_settings.binopt.part
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Partitioning (`part`) turned ON or OFF.
- home_settings.binopt.rac
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle RAC (`rac`) turned ON or OFF.
- home_settings.binopt.rat
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Real Application Testing (`rat`) turned ON or OFF.
- home_settings.binopt.sdo
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Spatial Data Option Messages (`sdo`) turned ON or OFF.
- home_settings.binopt.uniaud
  (Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle's unified auditing feature (`uniaud`) turned ON or OFF.
- home_settings.edition
  (Optional) Specifies the Oracle Database edition that you want to use for creating the target ORACLE_HOME.
- home_settings.home_name
  (Optional) Specifies the Oracle home name that will be used for the database in the `inventory.xml` file in the Oracle Inventory (oraInventory) directory when creating the target ORACLE_HOME.
- home_settings.ignore_opatch_conflict
  (Optional) Specifies the conflict resolution strategy for resolving conflicts between patches caused by one-off patches.
- home_settings.inventory_group
  (Optional) Specifies the group that is designated as the Oracle Inventory group (OINSTALL).
- home_settings.inventory_location
  (Optional) Specifies the directory that should be used for the Oracle Database inventory (`oraInventory`) directory.
- home_settings.oracle_base
  (Optional) Specifies the directory that should be used for the Oracle base directory.
- home_settings.osbackupdba_group
  (Optional) Specifies the group that is designated as the operating system OSBACKUPDBA backup and recovery system privileges group for an Oracle Database.
- home_settings.dba_group
  (Optional) Specifies the group that is designated as the operating system DBA system privileges group (OSDBA) management for the database.
- home_settings.osdgdba_group
  (Optional) Specifies the group that is designated as the operating system OSDGDBA system privileges to administer and monitor Oracle Data Guard.
- home_settings.oskmdba_group
  (Optional) Specifies the group that is designated as the operating system SYSKM system privileges for encryption key management for applications such as Oracle Wallet Manager.
- home_settings.oper_group
  (Optional) Specifies the group that is designated as the operating system operator (OSOPER) system privileges group.
- home_settings.osracdba_group
  (Optional) Specifies the group that is designated as the operating system SYSRAC privileges to perform day to day administration of Oracle Database on an Oracle RAC cluster.
- home_settings.read_only
  Specifies whether a Read-Only Oracle home should be enabled when creating the target ORACLE_HOME.
- home_settings.ru_apply
  (Optional) Specifies whether a release update (RU) is installed at the same time as the `ORACLE_HOME`, or installed as a separate step by OPatch.

**Related Topics**

- [How to Check and Enable/Disable Oracle Binary Options ? (Doc ID 948061.1)](https://support.oracle.com/rs?type=doc&id=948061.1)

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

#### home_settings.account_type

(Optional) On Microsoft Windows, this option specifies the type of account to use when creating the target ORACLE_HOME.

##### Usage Notes

On Microsoft Windows, the Oracle Home User can be either a **Windows Virtual Account** (`VIRTUAL`), a **Windows Built-in Account** (`BUILT_IN`), or a **standard Windows User Account** (not an Administrator account) (`USER`).

If a Windows Virtual Account is used, then it enables you to install an Oracle Database and create and manage Database services without passwords. If a Built-in Account is used, then no user name or password is required during installation and administration. If a Windows User Account is used as Oracle Home User, then you must provide the user name and password during installation and some of the administration tasks. A Virtual Account can be used as the Oracle Home User for Oracle Database Single Instance installations. Virtual accounts do not require a user name or password during installation and administration.

**Note:**

To use this option, the Windows user account (nonadministrative user) must exist before you run AutoUpgrade. AutoUpgrade cannot create these users.

##### Options

    [VIRTUAL|BUILT_IN|USER]

##### Examples

In this example, you specify the Oracle Home User account to be a Built-in account:

    upg1.home_settings.account_type=built_in

**Parent topic:** home_settings.option

#### home_settings.binopt.asm

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle ASM (`asm`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the Oracle Automatic Storage Management (`asm`) binary turned off. This parameter instructs AutoUpgrade to turn the `asm` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.asm=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.dm

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Data Mining (`dm`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration file `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the Oracle Data Mining (`dm`) binary turned off. This parameter instructs AutoUpgrade to turn the `dm` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.dm=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.jox

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for the JavaVM JIT Compiler (jox) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the JavaVM JIT Compiler (`jox`) binary turned off. This parameter instructs AutoUpgrade to turn the DM binary to ON in the target Oracle home.

    upg1.home_settings.binopt.jox=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.olap

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for the On Line Application Processing (OLAP) options (`olap`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the On Line Application Processing options (`olap`) binary turned off. This parameter instructs AutoUpgrade to turn the `olap` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.olap=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.part

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Partitioning (`part`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has Oracle Partitioning (`part`) binary turned off. This parameter instructs AutoUpgrade to turn the `part` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.part=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.rac

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle RAC (`rac`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the Oracle Real Application Clusters (Oracle RAC) binary (`rac`) turned off. This parameter instructs AutoUpgrade to turn the `rac` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.rac=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.rat

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Real Application Testing (`rat`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the Oracle Real Application Testing binary (`rat`) turned off. This parameter instructs AutoUpgrade to turn the `rat` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.rat=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.sdo

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle Spatial Data Option Messages (`sdo`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has the Oracle Spatial Data Option Messages (SDO) binary (`sdo`) turned off. This parameter instructs AutoUpgrade to turn the `sdo` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.sdo=yes

**Parent topic:** home_settings.option

#### home_settings.binopt.uniaud

(Optional) Specifies whether the target ORACLE_HOME being created by AutoUpgrade Patching has the binary option for Oracle's unified auditing feature (`uniaud`) turned ON or OFF.

##### Usage Notes

Oracle products and components are enabled or disabled at the binary level in the source Oracle home. When a source Oracle home is defined in the configuration file by using the local configuration parameter `source_home`, the value used for the target Oracle home matches the status of the binary option for the source Oracle home; the default is to leave the binary value unchanged. However you can choose to override the target Oracle home setting by choosing either `yes` or `no`.

##### Options

    [yes | no]

There is no default.

##### Examples

In this example, the source Oracle home has Oracle's unified auditing feature binary (`uniaud`) turned off. This parameter instructs AutoUpgrade to turn the `uniaud` binary to ON in the target Oracle home.

    upg1.home_settings.binopt.uniaud=yes

**Parent topic:** home_settings.option

#### home_settings.edition

(Optional) Specifies the Oracle Database edition that you want to use for creating the target ORACLE_HOME.

##### Usage Notes

When a source ORACLE_HOME is defined in the configuration file, the default value for edition matches the edition used for that ORACLE_HOME. Otherwise, there is no default value.

##### Options

Standard (SE2) or Enterprise Edition (EE):

    [se2|ee]

##### Examples

In this example, you specify the Oracle Database edition to be Oracle Database Standard Edition.

    upg1.home_settings.edition=se2

**Parent topic:** home_settings.option

#### home_settings.home_name

(Optional) Specifies the Oracle home name that will be used for the database in the `inventory.xml` file in the Oracle Inventory (oraInventory) directory when creating the target ORACLE_HOME.

##### Usage Notes

In a read/write ORACLE_HOME, the ORACLE_BASE_HOME path is the same as the ORACLE_HOME directory. However, in a read-only ORACLE_HOME, the ORACLE_BASE_HOME directory is not co-located with ORACLE_HOME, but instead is located at ORACLE_BASE/homes/HOME_NAME. The value for HOME_NAME is the internal name for the ORACLE_HOME. These home names are tracked in the `oraInventory` directory, which contains a file called `inventory.xml` that lists the names of all the Oracle homes installed on the system. Oracle software owners are members of this group. The default value is to use a generic name for the database homes, but you can specify a particular name by using this option.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the Oracle home name change the database home from a generic name, such as `dbhome_2`, to be `inv_west`:

    upg1.home_settings.home_name=inv_west

**Parent topic:** home_settings.option

#### home_settings.ignore_opatch_conflict

(Optional) Specifies the conflict resolution strategy for resolving conflicts between patches caused by one-off patches.

##### Usage Notes

This optional parameter enables you to configure a patching conflict policy that AutoUpgrade can apply when AutoUpgrade patching performs OPatch prerequisite checks. When you set a conflict policy using this parameter and AutoUpgrade detects conflicts among the patches specified by the `patch` parameter, AutoUpgrade applies the patch conflict policy to resolve the conflict.   If the conflict is only between the one-off patches specified by the `patch` parameter, then, based on the `home_settings.ignore_opatch_conflict` parameter value, AutoUpgrade patching can automatically resolve conflicts between those patches and proceed to complete the patching, without stopping with a patch conflict error.

**Note:**

If patch conflicts are between any other types of patches other than the one-off patches that you specify with the `patch` parameter, then AutoUpgrade will always stop and issue an error, regardless of the `ignore_patch_conflict` policy that you set.

##### Options

    [error|keep_first|skip_all]

The default is `error`. The values for `home_settings.ignore_opatch_conflict` are as follows:

- `error` (default) : When AutoUpgrade encounters patch conflicts, patching then stops. AutoUpgrade displays an error, indicating that there are conflicts among the specified patches.

- `keep_first`: When AutoUpgrade encounters patch conflicts, it prioritizes installing the one-off patches based on the order in which they are entered in the configuration file `prefix``.patch=RU,OPATCH,``patch-number1``,``patch-number2``,``patch-number3``...` parameter entry. When a conflict is found, the one-off patches that come first in the patch parameter value sequence continue to be installed, even if these patches conflict with patches that are specified later in the parameter patch priority list. At the end of the patching operation, AutoUpgrade reports the patches that could not be applied.

- `skip_all `: AutoUpgrade patching automatically skips installing all conflicted one-offs patches and proceeds to install patches that do not have conflicts.

##### Examples

##### ignore_opatch_conflict=error

In this example, the `ignore_opatch_conflict` option either is not specified (in which case the default is set to `ERROR`), or this option is set in the configuration file to `ERROR`. As a result, if AutoUpgrade encounters any conflicts between any of the one-off patches (101,102,103), then AutoUpgrade stops and displays an error.

    upg1.patch=RECOMMENDED,101,102,103 
    upg1.home_settings.ignore_opatch_conflict = ERROR  

##### ignore_opatch_conflict=keep_first

In this example, the `ignore_opatch_conflict` option is set in the configuration file to `KEEP_FIRST`.

    upg1.patch=RU,OPATCH,OJVM,101,102,103,104,105,106,107,108
    upg1.home_settings.ignore_opatch_conflict = KEEP_FIRST

Suppose conflict arise among the following one-off patches:

- 101,102
- 101,103
- 102,103
- 103,104
- 104,105
- 105,108

In this case, AutoUpgrade patching does not stop with an error message, but continues to install patches :(RU,OPATCH,OJVM,101,104,106,107,108), based on the order of their appearance in the patch parameter value sequence. AutoUpgrade automatically ignores installing patches 102,103, and 105. At the end of the patching operation, AutoUpgrade reports the patches that had conflicts (102,103,105), and were ignored, with the following message: "Conflicts are detected and ignored among the provided one-off patches for the following jobs."

##### ignore_opatch_conflict=skip_all

In this example, the `ignore_opatch_conflict` option is set in the configuration file to `SKIP_ALL`.

    upg1.patch=RU,OPATCH,OJVM,101,102,103,104,105
    upg1.home_settings.ignore_opatch_conflict = SKIP_ALL

Suppose that there are conflicts, but they only exist between patches 103 and 104. In that event, AutoUpgrade ignores patch numbers 103 and 104, and completes installing patches RU,OPATCH,OJVM, 101, 102, and 105, without stopping to display an error. At the end of the process, AutoUpgrade reports that patches 103 and 104 had conflicts that were detected, so these patches were ignored.

**Parent topic:** home_settings.option

#### home_settings.inventory_group

(Optional) Specifies the group that is designated as the Oracle Inventory group (OINSTALL).

##### Usage Notes

Members of the Oracle Inventory group group are granted OINSTALL privileges to read and write to the Oracle Inventory group directory (`oraInventory`). Oracle software owners are members of this group. When `oraInst.loc` already exists on the system, the default value matches the specified operating system group that is already defined on the system. Otherwise, the default value is `oinstall`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the OINSTALL group to be `oracle-owners`:

    upg1.home_settings.inventory_group=oracle-owners

**Parent topic:** home_settings.option

#### home_settings.inventory_location

(Optional) Specifies the directory that should be used for the Oracle Database inventory (`oraInventory`) directory.

##### Usage Notes

The Oracle Inventory directory (`oraInventory`) maintains an inventory of all installed Oracle software on the system. When `oraInst.loc` already exists on the system, the default value for `oraInventory` matches the specified `inventory_location` directory already defined. Otherwise, there is no default value.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the Oracle Inventory to be in the path location `/u02/app/oraInventory`:

    upg1.home_settings.inventory_location=/u02/app/oraInventory

**Parent topic:** home_settings.option

#### home_settings.oracle_base

(Optional) Specifies the directory that should be used for the Oracle base directory.

##### Usage Notes

For both a read-only ORACLE_HOME and a read/write ORACLE_HOME, the user-specific files, instance-specific files, and log files reside in a location known as the ORACLE_BASE_HOME. An Oracle base home directory by default has an Optimal Flexible Architecture (OFA) path, such as `/u01/app/oracle/`. If you prefer, you can change from the default Oracle base into some other path, such as an `/opt` path,

##### Examples

In this example, you specify the Oracle base home to be in the path location `/opt/oracle/databases/`:

    upg1.home_settings.inventory_location=/opt/oracle/databases/

**Parent topic:** home_settings.option

#### home_settings.osbackupdba_group

(Optional) Specifies the group that is designated as the operating system OSBACKUPDBA backup and recovery system privileges group for an Oracle Database.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the OSBACKUPDBA system privileges group. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the OSBACKUPDBA group used for that ORACLE_HOME. Otherwise, the default group uses the group that is specified for `home_settings.osdba_group`. You can override those defaults by specifying a named OSBACKUPDBA group.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the OSBACKUPDBA group to be `oracle_backup`:

    upg1.home_settings.osbackupdba_group=oracle_backup

**Parent topic:** home_settings.option

#### home_settings.dba_group

(Optional) Specifies the group that is designated as the operating system DBA system privileges group (OSDBA) management for the database.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the OSDBA system privileges group. Members of this group are granted the SYSDBA system privileges to administer the database. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the OSDBA system privileges group used for that ORACLE_HOME. If the `source_home` is not defined, then the default for this parameter then becomes `dba`.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the OSDBA group to be `inv_dba`:

    upg1.home_settings.osdba_group=inv_dba

**Parent topic:** home_settings.option

#### home_settings.osdgdba_group

(Optional) Specifies the group that is designated as the operating system OSDGDBA system privileges to administer and monitor Oracle Data Guard.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the OSDGDBA system privileges group. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the OSDGDBA system privileges group used for that ORACLE_HOME. Otherwise, the default group uses the group that is specified for `home_settings.osdba_group`. You can override those defaults by specifying a named OSDGDBA group.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the OSDGDBA group to be `oracle_dg`:

    upg1.home_settings.osdgdba_group=oracle_dg

**Parent topic:** home_settings.option

#### home_settings.oskmdba_group

(Optional) Specifies the group that is designated as the operating system SYSKM system privileges for encryption key management for applications such as Oracle Wallet Manager.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the SYSKM system privileges group. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the SYSKM system privileges used for that ORACLE_HOME. Otherwise, the default group uses the group that is specified for `home_settings.osdba_group`. You can override those defaults by specifying a named SYSKM group.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the SYSKM group to be `oracle_keystore`:

    upg1.home_settings.osdgdba_group=oracle_keystore

**Parent topic:** home_settings.option

#### home_settings.oper_group

(Optional) Specifies the group that is designated as the operating system operator (OSOPER) system privileges group.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the OSOPER system privileges group. Members of this group are granted the OPERATOR system privileges to start up and shut down the database. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the OSOPER system privileges group used for that ORACLE_HOME. Otherwise, the default group uses the group that is specified for `home_settings.osdba_group`. You can override those defaults by specifying a named OSOPER group.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the OSOPER group to be `inv_oper`:

    upg1.home_settings.osdba_group=inv_oper

**Parent topic:** home_settings.option

#### home_settings.osracdba_group

(Optional) Specifies the group that is designated as the operating system SYSRAC privileges to perform day to day administration of Oracle Database on an Oracle RAC cluster.

##### Usage Notes

This option is used with AutoUpgrade patching when installing the target ORACLE_HOME to specify the operating system RACDBA system privileges group. The user running AutoUpgrade Patching must be a member of the specified group. By default, when a source ORACLE_HOME is defined in the configuration file, the default value matches the RACDBA system privileges used for that ORACLE_HOME. Otherwise, the default group uses the group that is specified for `home_settings.osdba_group`. You can override those defaults by specifying a named RACDBA group.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Examples

In this example, you specify the RACDBAgroup to be `oracle_rac`:

    upg1.home_settings.osdgdba_group=oracle_rac

**Parent topic:** home_settings.option

#### home_settings.read_only

Specifies whether a Read-Only Oracle home should be enabled when creating the target ORACLE_HOME.

##### Usage Notes

A read-only Oracle home can simplify provisioning. In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home. See your platform installation guide for more information about read-only Oracle homes.

When a source ORACLE_HOME is defined in the configuration file, the default value matches the setting used for that ORACLE_HOME. Otherwise, the default for a read-only Oracle home is `no`. To provision a read-only Oracle home for the target Oracle home, you can use this option to select a read-only Oracle home by specifying this option with `yes`.

##### Options

    [yes|no]

The default is `no`.

##### Examples

In this example, you specify that the target Oracle home should be a read-only Oracle home:

    upg1.home_settings.read_only=yes

**Parent topic:** home_settings.option

#### home_settings.ru_apply

(Optional) Specifies whether a release update (RU) is installed at the same time as the `ORACLE_HOME`, or installed as a separate step by OPatch.

##### Usage Notes

When the parameter is specified to `YES` on a platform other than Microsoft Windows, the RU being installed during a deploy operation is installed when `runInstaller` is run using the `-applyRU` command line option. When the parameter is specified to `NO`, the RU is then installed separately by running OPatch after the ORACLE_HOME has already been installed.

**Note:**

This option is not available on Microsoft Windows platforms.

##### Options

    [yes|no}

The default value is `no`, unless the current operating system is Oracle Linux 9 or higher.

##### Examples

In this example, the parameter is specified to `no`, indicating that you plan to run OPatch after the Oracle home is installed.

    upg1.home_settings.ru_apply=no

**Parent topic:** home_settings.option

### ignore_errors

(Optional) Enables you to specify a comma-delimited list of specific Oracle errors that you want AutoUpgrade to ignore during the upgrade or patching process.

#### Usage Notes

If you add this parameter to your configuration file, then the error numbers that you specify are ignored during the upgrade for the upgrade prefix that you specify.

#### Examples

    sales3.ignore_errors=ORA-48181,ORA-00001

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### keep_pdb_save_state

(Optional) Specifies that if the PDB has a saved state in the source CDB, then you can either save or not save the PDB state on the target CDB.

#### Usage Notes

This parameter applies to the Unplug-Plug flow (including restorations). If the PDB state is saved in the source CDB, then by default that same saved state continues to be saved after the upgrade process (default is `yes`). When `keep_pdb_save_state` is set to `no`, the source PDB state is not saved after the upgrade. You can choose to set `keep_pdb_save_state` to `no` when you are advised to do so in AutoUpgrade preupgrade checks. For example, with Oracle Real Application Clusters (Oracle RAC) upgrades, Oracle recommends that you do not keep the source PDB saved state.

#### Options

    [yes | no]

The default value is `yes`.

#### Example

    sales1.keep_pdb_save_state.pdbA=no

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

**Note:**

On Microsoft Windows platforms, `global.autoupg_log` and `log_dir` should be configured on the same drive.

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

    manage_standbys_clause=STANDBYS=[NONE|ALL|ALL EXCEPT ('pdb-name', 'pdb-name', ...)|STANDBYS=('pdb-name', 'pdb-name', ...)]

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

### method

(Optional for AutoUpgrade patching) Specifies whether to create a new target Oracle home, and if so, how it will be created.

#### Usage Notes

The default value is `outofplace`. At the time of this release, outofplace is the only permitted value. When the AutoUpgrade command-line parameter `-patch` is used, AutoUpgrade creates a new target Oracle home using the base image contained in the directory specified by the `folder` parameter. Oracle recommends that all patching is performed as out-of-place patching, where a new Oracle home is created.

#### Examples

    upg1.method=outofplace

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### parallel_pdb_creation_clause

(Optional) Specifies the number of parallel execution servers to use when creating a pluggable database. This can be used for scenarios like PDB relocate, clone PDB, etc. It doesn't apply for cases when creating a PDB using an XML file.

#### Usage Notes

This parameter is optional. You can use this parameter to specify the number of parallel execution servers to copy the new PDB's data files to a new location when creating a PDB. This may result in faster creation of the PDB. Scenarios where you can take advantage of this option is when you want to upgrade and convert a non-CDB Oracle Database to a PDB, or you want to unplug a PDB from a source release CDB and relocate it in for an upgrade to a target release CDB.

The parameter is specific for every source database or pluggable database on the AutoUpgrade configuration file. The CDB can ignore this setting, depending on the current database load and the number of available parallel execution servers. Using this parameter enables you to provide better control of the load placed on the target database.

**Note:**

Note: This feature does not work during unplug/plug processes.

#### Options

Use an integer value to specify the number of servers to run in parallel, where `source-db-name-or-pdb` is the non-CDB database name or the PDB name, and `integer-value` is a numeric value specifying the number of servers to run in parallel::

    prefix.parallel_pdb_creation_clause.source-db-name-or-pdb='integer-value'

#### Example

In the following example, 16 servers are specified as the limit for the number of servers to run in parallel.

    upg1.parallel_pdb_creation_clause.pdb1=16

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### patch

(Required for AutoUpgrade patching) Specifies a comma-delimited list of the patches that you want to install.

#### Usage Notes

Required for AutoUpgrade patching.

#### Options

`[recommended|ru|ru:``x``.``y``|opatch|ojvm|ojvm:x.y|dpbp|``patch-number``]`

The default value is `RECOMMENDED`.

Options:

- `RECOMMENDED`: Alias for all of the following options: `RU`, `OPATCH`, `OJVM`, `DPBP`.

- `RU`: Latest release update

- `RU:x.y`: A release update (RU) of the specified release version, where `x` is the major release number, and `y` is the RU. For example: `RU:19.24`

- `OPATCH`: Use latest version of OPatch

- `OJVM`: Apply the Oracle Java VM patch that applies to the specified RU.

- `OJVM:x.y`: Apply the Oracle Java VM patch of the specified release version, where `x` is the major release number, and `y` is the RU. For example: `OJVM:19.24`

- `DPBP`: Apply the Oracle Data Pump patch for the specified RU

- `patch-number``[,``patch-number``,``patch-number``...]` specifies one or more specific one-off patches that you want AutoUpgrade to apply, in order of priority.

#### Examples

`patch-number`: Provide a specific one-off patch number.

    upg1.patch=ru:19.24,12345678,opatch

Apply recommended patches, which includes the set of recommended patch options: `RU` (the latest release update for the base image), as well as `OPATCH`, `OJVM`, and `DPBP`:

    upg1.patch=recommended

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### patch_in_upgrade_mode

(Optional) Specifies that the database that you want to patch is patched in upgrade mode, instead of normal mode.

#### Usage Notes

In AutoUpgrade 23.4 and earlier versions, the default for patching has been to perform patching in upgrade mode. Starting with AutoUpgrade 24.1, the default is to perform patching in normal mode. If you prefer to perform patching only in upgrade mode, then you can use this parameter to override that default behavior, and patch in upgrade mode.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales.patch_in_upgrade_mode=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### patch_node

(Optional) For AutoUpgrade patching, specifies the node on which the current user configuration is valid. The default value is `localhost`.

#### Usage Notes

The purpose of this parameter is to prevent AutoUpgrade patching from processing databases that are listed in the configuration file that you use with AutoUpgrade, where the value for the `patch_node` parameter does not correspond to the current host name. It does not enable running AutoUpgrade patching remotely. You can use the keyword `localhost` as a wild card to indicate that databases on the local host should be processed.

Use case:

The configuration file `config.cfg` contains 10 databases. Five of the databases have the value of `patch_node` set to `denver01`. The remaining five have the value of `patch_node` set to `denver02`. If AutoUpgrade is run on the server `denver01` using the configuration file `config.cfg`, then AutoUpgrade only processes the databases for patching where `patch_node` is set to `denver01`. It ignores the databases where `patch_node` is set to `denver02`. The utility `hostname` identifies the value used to resolve the upgrade node.

#### Example

    hostname
    denver02
    sales1.patch_node=denver01

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

### platform

(Optional) Specifies the platform used by AutoUpgrade Patching when downloading patches from My Oracle Support.

#### Usage Notes

The parameter `platform` specifies which platform patches AutoUpgrade uses for patching. AutoUpgrade Patching supports the following platforrms:

- `AIX.x64` IBM AIX on POWER Systems (64-Bit)
- `ARM.x64` LINUX ARM (`aarch64`)
- `LINUX.X64` Linux x86-64
- `SPARC.x64` Oracle Solaris on SPARC (64-Bit)
- `SOLARIS.x64` Oracle Solaris on x86-64 (64-Bit)
- `WINDOWS.X64` Microsoft Windows x64 (64-bit).

If the current operating system is one of the supported platforms, then the default value matches that platform. Otherwise, the default value is `LINUX.X64`

#### Options

`[AIX.x64|ARM.x64|LINUX.X64|SPARC.x64|SOLARIS.x64|WINDOWS.X64]`

The default value is `LINUX.X64`.

#### Example

    upg1.platform=LINUX.X64

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### raise_compatible

(Optional) Increases the Oracle Database `COMPATIBLE` initialization parameter to the default value of the target release after the upgrade is completed successfully.

#### Usage Notes

Options:

- `Y` : Increase the `COMPATIBLE` parameter setting to the target release
- `N` : Do not increase the `COMPATIBLE` parameter setting to the target release
- Increase the COMPATIBLE level to a specific release update (RU) level (for example, `23.0`, `23.4`, `23.7`)

The default is `N`.

**Caution:**

- After the `COMPATIBLE` parameter is increased, database downgrade is not possible.
- Oracle recommends that you only raise the `COMPATIBLE` parameter to the current release level after you have thoroughly tested the upgraded database.
- Regardless of what value you use for the `autoupgrade` command-line parameter `restore`, if you set the value of the configuration file parameter `raise_compatible` to `yes`, then before starting the upgrade, you must delete manually any guaranteed restore point you have created. After the upgrade is completed successfully, AutoUpgrade deletes the guaranteed restore point it creates before starting the upgrade. When AutoUpgrade starts the POSTUPGRADE stage, there is no way to restore the database.
- If you specify to raise `COMPATIBLE` to a target RU level, then the the RU level you specify cannot be greater than the target Oracle home release. For example, if the target Oracle home release is Oracle Database 23ai updated to RU 23.4, then 23.7 is not a valid value for `raise_compatible`.

#### Examples

Raise `COMPATIBLE` to the level of the target Oracle Database home:

    sales1.raise_compatible=yes

Raise `COMPATIBLE` to RU 23.4:

    sales1.raise_compatible=23.4

Raise `COMPATIBLE` to RU 23.7:

    sales1.raise_compatible=23.7

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

(Optional) Specifies whether to use Replay or to use a Classic upgrade to upgrade the database.

#### Usage Notes

By default, AutoUpgrade performs a Classic upgrade to upgrade the database.

#### Options

`[yes | no]`

The default value is `no`.

**Note:**

In addition to setting the `replay` parameter value to `yes`, both the PDBs that you want to upgrade with Replay Upgrade and `CDB$ROOT` must have `sys.database_properties.pdb_upgrade_sync` set to `1` (the default value).

If a container's `sys.database_properties.pdb_upgrade_sync` is not already set to the default value of 1, then log on to that container and run the following SQL command:

    ALTER PLUGGABLE DATABASE UPGRADE SYNC ON

#### Example

    upg1.replay=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### restoration

(Optional) Generates a Guaranteed Restore Point (GRP) for database restoration.

#### Usage Notes

If left at default value (`yes`), a fast recovery area configuration is required to create a GRP. If you set `restoration=no`, then both the database backup and restoration must be performed manually. Set to `no` for databases that operate in `NOARCHIVELOG` mode, and for Standard Edition and Standard Edition 2 databases, which do not support the Oracle Flashback technology feature Flashback Database. If you do not specify the parameter, then the default value (`yes`) is used, and a guaranteed restore point is created.

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

### run_dictionary_health

(Optional) Specifies whether you run Oracle Dictionary Health Checks as part of preupgrade checks to identify database dictionary inconsistencies.

#### Usage Notes

To help to identify database dictionary inconsistencies, you can specify that AutoUpgrade runs the `DBMS_DICTIONARY_CHECK` PL/SQL package on the source database as part of preupgrade checks. If set, the AutoUpgrade `run_dictionary_health` parameter enables you to specify for each upgrade source database that AutoUpgrade runs either the full array of Oracle Dictionary Health Checks on the database dictionary, or that it runs only the most critical set of checks. If the check detects potential or critical problems with the database dictionary, then it prevents the upgrade from starting.

Oracle Dictionary Health Check results are stored under the AutoUpgrade precheck directory in the format `dbname``_healthcheck_result.log`, where `dbname` is the name of the database on which the check was run. For more information about Oracle Dictionary Health Check, refer to the `DBMS_HCHECK` package documentation in Oracle Database PL/SQL Packages and Types Reference.

#### Options

`[full| critical]`

If the parameter is not set, then the default is to not run `DBMS_DICTIONARY_CHECK`.

#### Example

    sales1.run_dictionary_health=full
    sales2.run_dictionary_health=critical

**Related Topics**

- [DBMS_DICTIONARY_CHECK PL/SQL Package](../arpls/index.md)

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### run_utlrp

(Optional) Enables or disables running a version of `utlrp.sql` as part of post upgrade, to recompile only invalid objects in Oracle-maintained schemas.

#### Usage Notes

The `utlrp` utility recompiles all Data Dictionary objects that become invalid during a database upgrade. If you set `run_utlrp=no`, or if you want invalid user objects also to be recompiled, then Oracle recommends that you use this utility to recompile invalid objects after upgrading with AutoUpgrade.

**Note:**

Starting with AutoUpgrade 23.1, when you run the AutoUpgrade utility, AutoUpgrade runs the `utlprpom.sql` script, and does not run `utlrp.sql`. When AutoUpgrade is used for upgrades to Oracle Database 12c Release 2 (12.2.0.1) and later releases, AutoUpgrade only recompiles invalid objects owned by Oracle-maintained schemas. Because database upgrades do not need to touch user objects, AutoUpgrade maintains this policy when it recompiles invalid objects.

#### Options

`[yes | no]`

The default value is `yes`.

#### Example

    prefix.run_utlrp=yes

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File

### sid

(Required) Identifies the Oracle system identifier (SID) of the database that you want to upgrade.

#### Usage Notes

This parameter is case-sensitive.

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

(Optional) Specifies the `SID` of the target CDB into which a non-CDB Oracle Database is plugged in.

#### Usage Notes

This parameter is mandatory when you want to upgrade and convert a non-CDB Oracle Database. It is case-sensitive.

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

This parameter is optional. It is used when you want to upgrade and convert a non-CDB Oracle Database to a PDB, or you want to unplug a PDB from a source release CDB and plug it in for an upgrade to a target release CDB.

When you upgrade and convert an existing non-CDB database to a PDB on a target CDB, the `target_cdb` parameter is mandatory, because it specifies the target CDB. If you want to determine how the PDB is created on the target CDB, you can use the optional parameters `target_pdb_name` and `target_pdb_copy_option` to specify how the PDB is created on the target CDB. However, if neither optional parameters are used, then a full upgrade of the source CDB is performed.

The default name for the target PDB when you convert a non-CDB to a PDB is to use the database unique name of the non-CDB Oracle Database. To specify a name that is different from the existing name of the non-CDB when you plug it in to the CDB, set the new name by using `target_pdb_name`. In addition, if you are creating a refreshable clone database, then append a suffix to the parameter that specifies either the source database name or PDB name (`target_name``.``suffix`)

#### Examples

In the following example, the source non-CDB database is `emp19`. The target_pdb_name parameter is used to change the name to `emp23pdb` on the target CDB database.

    upg.target_pdb_name=emp23pdb

For a refreshable clone, add a prefix to indicate the source database for the clone. In this example, the source container database is `db122b` and we are cloning `pdb1` from `db122b` into the target container database `db19`. The suffix `pdb1` is used as the identifier for both `target_pdb_name` and `source_dblink`. The `pdb1` suffix identifier associates both the target PDB name and the dblink used to move the data from the source, `pdb1`, into the target PDB `PLUG122`.

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

### target_version

(Optional) For AutoUpgrade patching, specifies the target release version on which you want AutoUpgrade to perform the patch maintenance operation.

#### Usage Notes

The purpose of this parameter is to ensure that the proper set of patches are downloaded or installed into the target Oracle home that is being created. For AutoUpgrade patching, the local parameter `target_version` is only required if both of the following conditions are true:

1.  The `source_home` parameter is not specified in the configuration file
2.  The patch parameter does not use RU:x.y notation

If these conditions do not apply, then AutoUpgrade can derive the target release value. The allowed value is a single major release number. At the time of this release, the only valid value is for Oracle Database 19c (`19`).

Valid value:

    19

#### Example

    sales1.target_version=19

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

You can concatenate multiple parameters together in a single `tune_setting` entry

| Option                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `active_nodes_limit`    | Sets a new total of active cluster member nodes that you want to use during a distributed upgrade of Oracle Real Application Clusters databases. The default is 2. If the number you specify is equal to or greater than the maximum number of cluster member nodes, then all nodes are taken.<br>`sales3.tune_setting=active_nodes_limit=4`                                                                                                                                                                                                                                                                                                                                                                                             |
| `distributed_upgrade`   | Specifies that AutoUpgrade performs a **distributed upgrade**. A distributed upgrade leverages the resources of the Oracle Clusterware cluster member nodes to perform the upgrades of PDBs more rapidly on the cluster. Use this option when a CDB in an Oracle RAC cluster of at least two nodes is being upgraded. When you choose this option, the `proactive_fixups` option is also enabled by default. Example:<br>`sales3.tune_setting=proactive_fixups=true,distributed_upgrade=true`<br>Note: Distributed upgrades are not supported on Microsoft Windows.                                                                                                                                                                      |
| `make_pdbs_available`   | Opens the PDBs designated by the prefix in read/write and non-restricted mode after postfixups are complete when **proactive fixups** mode is used. This option enables PDBs designated by the prefix to become available for service immediately after the upgrade is completed, while other PDBs continue to be upgraded, which can be useful for large fleet upgrade deployments.<br>Precautions:<br>Choosing this option enables the PDBs you designate to accept service requests from users, while other PDBs are being upgraded. The response time of the PDBs for service requests, and the time required for ongoing PDB upgrades can each be affected.<br>Example:<br>`sales3.tune_setting=make_pdbs_available=true`           |
| `proactive_fixups`      | Enables proactive fixups mode, where the PDBs are upgraded as the last stage of the upgrade. When the number of PDBs is higher than the CPU count defined in the database, divided by 2, choosing this tuning option can result in a faster upgrade. Example:<br>`sales3.tune_setting=proactive_fixups=true`<br>Precautions:<br>If the number of CPUs is higher than the number of PDBs, then changing this setting may not improve performance.<br>Note:<br>Although the `proactive_fixups` configuration option by default is set to `TRUE`, proactive fixups is currently not supported on Windows.<br>Note: the `proactive_fixups` option is not currently supported for Application Containers or on Microsoft Windows systems      |
| `query_hint_parallel`   | Specifies a parallel thread specification to the code that gathers data from the tablespaces during the query of the PDBs specified by the prefix, so that you can allocate a greater number or lesser number of parallel threads to the PDBs specified by the prefix. Example:<br>`sales3.tune_setting=query_hint_parallel=8`<br>Choosing this option can cause AutoUpgrade to consume more system resources.<br>Option `NO_HINT` avoids the use of optimizer hints on the query that gathers information about database tablespaces. This option can be useful in environments where existing hints (materialize and parallel) affect the performance of the query. For example:<br>` sales3.tune_setting=query_hint_parallel=NO_HINT` |
| `utlrp_threads_per_pdb` | Overwrites default maximum number of threads generated by the recompilation of invalid objects in the CDB, and uses the number of threads that you specify. Example:<br>`sales3.tune_setting=utlrp_threads_per_pdb=8`<br>Precautions:<br>If the number of threads specified exceeds available threads on the system, then performance can be compromised.                                                                                                                                                                                                                                                                                                                                                                                |
| `utlrp_pdb_in_parallel` | Overwrites default maximum number of concurrent recompilation threads to the number that you specify. Use this option to overwrite the default maximum number of concurrent processes of recompilation of invalid objects. Example:<br>`sales3.tune_setting=utlrp_pdb_in_parallel=2`<br>Precautions:<br>Each PDB process requires from the system as many threads as specified by `utlrp_threads_per_pdb`.                                                                                                                                                                                                                                                                                                                               |

#### Examples

In the following example, the database upgrades specified with the prefix `sales3` are Oracle Real Application Clusters Oracle Database instances. The `tune_setting` parameter is used to set these database instances to use the setting `distributed_upgrade`, which distributes the upgrade load across multiple CDBs in the Oracle Grid Infrastructure cluster:

    sales3.tune_setting=distributed_upgrade=true

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

### wincredential

(Optional) Specifies the location of a Microsoft Windows credential object file that you have previously generated with the AutoUpgrade command-line parameter `load_win_credential`.

#### Usage Notes

The purpose of this parameter is to create a credentials file to store the user and password credentials for the owner of the Oracle database binaries, and to specify the location of the Administrator PowerShell credential object for those credentials, so that AutoUpgrade can be run using that that credential object during the Oracle Database upgrade. To use this feature, you must have already created the Windows PowerShell credential object, and then specify that credential object in the configuration file using `wincredential`.

Use case:

You want to specify credentials for the owner of database binaries on a Microsoft Windows server. To specify these credentials, after you enter the wincredential paramter in your configuration file, you run AutoUpgrade in Configuration mode using the `load_win_credentials` command-line paramter, and provide credentials as prompted. Microsoft Window Powershell then creates the credential object, and stores the generated credential object in the path location you specify with `wincredential`. For example, in the following file, the location of the credential file is specified with `upg1.wincredential=C:\Users\oracle\cred`

#### Example

    global.autoupg_log_dir=C:\Users\oracle\autoupg
    global.target.version=19.0.0
    global.target_home=C:\u01\app\oracle\product\19\dbhome_1

    upg1.sid=db12201
    upg1.source_home=C:\u01\app\oracle\product\12.2\dbhome_1
    upg1.log_dir=C:\Users\Oracle\autoupg
    upg1.upgrade_node=localhost
    upg1.target_base=C:\u01\app\oracle
    upg1.target_version=19.0.0.0
    upg1.wincredential=C:\Users\oracle\cred

**Parent topic:** Local Parameters for the AutoUpgrade Configuration File
