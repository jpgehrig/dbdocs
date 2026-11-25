## Locally Modifiable Global Parameters for AutoUpgrade Configuration File

Required configuration parameters for AutoUpgrade can be set either globally for all upgrades, or locally.

### Usage Notes

If you set required AutoUpgrade parameters globally, as a locally modifiable global parameter, then these parameters can be overridden by local parameters set for particular upgrades, so that you can better control AutoUpgrade job processing.

With locally modifiable global parameters, you can use the prefix `global` to set values for required parameters as global parameters for all jobs in your AutoUpgrade configuration file, but identify the same parameter with a local job prefix to reset the global value to a different value for a particular job in the same configuration file. You can also choose to set locally modifiable global parameters only as local parameters for each AutoUpgrade job.

**Note:**

These parameters are available in the latest version of AutoUpgrade that you can download from My Oracle Support.

When a locally modifiable global parameter is set both with a global prefix, and with a local job prefix, the locally modified parameter value overrides the global parameter values for the job identified by the prefix that you use with the parameter.

For example, with `global.target_home`, the syntax you use is in the form `global.target_home=``Global target Oracle home`, and `database``.target_home=``local target Oracle home``.`

### Example

In the AutoUpgrade configuration file, the required parameter `target_home` is set globally to one Oracle home path. But in the configuration file, the same parameter is set locally to a different Oracle home path. As AutoUpgrade processes the jobs in the configuration file, it uses the locally defined path for `target_home` for the job defined by the prefix `upgrade3`, overriding the global parameter setting:

    global.target_home=/u01/app/oracle/19.0.0/dbhome01
    upgrade3.target_home=/u03/app/oracle3/12.2.0.1/dbhome3

- defer_standby_log_shipping
  Defers shipping logs from the primary database to any standby database. All log archive destionations (`log_archive_dest_``n`) are set to deferred.
- dictionary_stats_after
  (Optional) Specifies that AutoUpgrade gathers data dictionary statistics on the target database after the upgrade is complete.
- dictionary_stats_before
  (Optional) Specifies that AutoUpgrade gathers data dictionary statistics on the source database before starting the upgrade.
- drop_grp_after_upgrade
  (Optional) Deletes the Guaranteed Restore Point (GRP) after database upgrade.
- enable_local_undo
  For a CDB upgrade, specifies whether or not `LOCAL` undo should be enabled before the upgrade of `CDB$ROOT`.
- export_rman_backup_for_noncdb_to_pdb
  (Optional) Specifies that AutoUpgrade transports metadata from the source non-CDB database to the target PDB database as part of the conversion process.
- fixed_stats_before
  (Optional) Specifies that AutoUpgrade gathers fixed object statistics on the source database before starting the upgrade.
- manage_network_files
  Specifies whether network files are processed during the upgrade.
- patch_in_upgrade_mode
  (Optional) Specifies that the database that you want to patch is patched in upgrade mode, instead of normal mode.
- raise_compatible
  (Optional) Increases the compatible parameter to the default value of the target release after the upgrade is completed successfully.
- replay
  (Optional) Specifies whether to use replay to upgrade the database.
- remove_underscore_parameters
  Removes underscore (hidden) parameters from `PFILE` files during upgrade, and after upgrade, for all Oracle Databases in the configuration file.
- restoration
  (Available with Enterprise Edition only) Generates a Guaranteed Restore Point (GRP) for database restoration.
- rman_catalog_connect_string
  (Optional) Specifies the RMAN connection string used to connect to an RMAN database.
- target_base
  Specifies the target `ORACLE_BASE` path for the target Oracle home.
- target_home
  (Required for upgrade and deploy modes, if the target home is not on the system. Optional for analyze and fixups mode.) Specifies the target Oracle home (`ORACLE_HOME`) path.
- target_version
  (Required if target Oracle home is not on the system, or is release 12.2) Specifies the target release version on which you want AutoUpgrade to perform the upgrade.

**Parent topic:** [AutoUpgrade Utility Configuration Files Parameters and Options](autoupgrade-utility-configuration-files.md)

### defer_standby_log_shipping

Defers shipping logs from the primary database to any standby database. All log archive destionations (`log_archive_dest_``n`) are set to deferred.

#### Usage Notes

By default, log shipping occurs as part of the upgrade. When Autoupgrade defers log shipping, you receive a notice that log shipping is deferred, and that after the upgrade completes successfully, you need to reenable shipping logs from the primary database to the secondary database.

**Note:**

This configuration file parameter affects not only standby databases, but all products or services that receive redo from the primary database, such as Oracle Zero Data Loss Recovery Appliance (ZDLRA) real-time log transport, and Oracle GoldenGate downstream capture.

#### Options

`[yes | no]`

The default value is `no`

The default is no (log-shipping is not deferred). If you change the default to `Yes`, then log shipping is deferred, and you must choose to re-enable it manually after upgrade.

#### Example

    defer_standby_log_shipping=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### dictionary_stats_after

(Optional) Specifies that AutoUpgrade gathers data dictionary statistics on the target database after the upgrade is complete.

#### Usage Notes

Oracle recommends that you gather dictionary statistics both before and after upgrading the database, because Data Dictionary tables are modified and created during the upgrade. When you specify yes, AutoUpgrade gathers dictionary statistics after the upgrade is completed.

#### Options

`[yes | no]`

The default value is `Yes`.

#### Example

    global.dictionary_stats_after=yes

    sales.dictionary_stats_after=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### dictionary_stats_before

(Optional) Specifies that AutoUpgrade gathers data dictionary statistics on the source database before starting the upgrade.

#### Usage Notes

Oracle recommends that you gather dictionary statistics both before and after upgrading the database, because Data Dictionary tables are modified and created during the upgrade. When you specify yes, AutoUpgrade gathers dictionary statistics before beginning the upgrade.

#### Options

`[yes | no]`

The default value is `Yes`.

#### Example

    global.dictionary_stats_before=yes

    sales.dictionary_stats_before=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### drop_grp_after_upgrade

(Optional) Deletes the Guaranteed Restore Point (GRP) after database upgrade.

#### Usage Notes

If you select this option, then GRP is deleted after upgrade completes successfully. If you set `raise_compatible` to `yes`, then you must also set the parameter `drop_grp_after_upgrade` to `yes`.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.drop_grp_after_upgrade=yes

    sales.drop_grp_after_upgrade=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### enable_local_undo

For a CDB upgrade, specifies whether or not `LOCAL` undo should be enabled before the upgrade of `CDB$ROOT`.

#### Usage Notes

If you select this option, then AutoUpgrade runs the following statement before upgrade: `ALTER DATABASE LOCAL UNDO ON;`.

When local undo is first enabled, the size of the undo tablespace in `PDB$SEED` is determined as a factor of the size of the undo tablespace in `CDB$ROOT`. The default is 30 percent of the undo tablespace size. Every other PDB in the CDB inherits this property from `PDB$SEED`. Ensure that there is enough space to allocate new `UNDO` tablespaces.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    enable_local_undo=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### export_rman_backup_for_noncdb_to_pdb

(Optional) Specifies that AutoUpgrade transports metadata from the source non-CDB database to the target PDB database as part of the conversion process.

#### Usage Notes

When converting a non-CDB to a PDB, you can extract the RMAN metadata from the source database, and put it into the target database, so that the metadata it will be available after the PDB conversion. Using this parameter enables the backups to be used as "pre-plugin" backups. If you want to restore the PDB right after plug-in, then the pre-plugin backups option can help to save time and effort.

This parameter applies to non-CDB to PDB conversions only (not with refreshable clone PDBs). In all other cases, the parameter should be ignored.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales.export_rman_backup_for_noncdb_to_pdb=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### fixed_stats_before

(Optional) Specifies that AutoUpgrade gathers fixed object statistics on the source database before starting the upgrade.

#### Usage Notes

Before an upgrade, Oracle recommends that you regather fixed object statistics.

Fixed objects are the `X$` tables and their indexes. `V$` performance views are defined through `X$` tables. Gathering fixed object statistics is valuable for database performance, because these statistics help the optimizer generate good execution plans, which can improve database performance. Failing to obtain representative statistics can lead to suboptimal execution plans, which can cause significant performance problems.

#### Options

`[yes | no]`

The default value is `Yes`.

#### Example

    global.fixed_stats_before=yes

    sales.fixed_stats_before=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### manage_network_files

Specifies whether network files are processed during the upgrade.

#### Usage Notes

If you select this option, then AutoUpgrade processes network files, depending on the option that you specify.

The following network files are processed: `oranfstab`, `ldap.ora`, `tnsnames.ora`, `sqlnet.ora`, and `listener.ora`

#### Options

\[`FULL|SKIP|IGNORE_READ_ONLY`\]

- `FULL`: (default) Raise all exceptions encountered during the copy and merge of network files into the target Oracle home.
- `SKIP`: Do not process network files during postupgrade.
- `IGNORE_READ_ONLY`: Attempt to copy and merge network files, but do not raise an exception during the upgrade if the target file is read only

#### Example

    manage_network_files=ignore_read_only

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### patch_in_upgrade_mode

(Optional) Specifies that the database that you want to patch is patched in upgrade mode, instead of normal mode.

#### Usage Notes

In AutoUpgrade 23.4 and earlier versions, the default for patching has been to perform patching in upgrade mode. Starting with AutoUpgrade 24.1, the default is to perform patching in normal mode. If you prefer to perform patching only in upgrade mode, then you can use this parameter to override that default behavior, and patch in upgrade mode.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    sales.patch_in_upgrade_mode=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### raise_compatible

(Optional) Increases the compatible parameter to the default value of the target release after the upgrade is completed successfully.

#### Usage Notes

If you select this option, then GRP is deleted after upgrade completes successfully. If you set `raise_compatible` to `yes`, then you must also set the parameter `drop_grp_after_upgrade` to `yes`.

**Caution:**

- After the `COMPATIBLE` parameter is increased, database downgrade is not possible.
- Oracle recommends that you only raise the `COMPATIBLE` parameter to the current release level after you have thoroughly tested the upgraded database.
- Regardless of what value you use for the `autoupgrade` command-line parameter `restore`, if you set the value of the configuration file parameter `raise_compatible` to `yes`, then before starting the upgrade, you must delete manually any guaranteed restore point you have created. After the upgrade is completed successfully, AutoUpgrade deletes the guaranteed restore point it creates before starting the upgrade. When AutoUpgrade starts the POSTUPGRADE stage, there is no way to restore the database.
- If you set `raise_compatible` to `yes`, then you must also set the parameter `drop_grp_after_upgrade` to `yes`.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.raise_compatible=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### replay

(Optional) Specifies whether to use replay to upgrade the database.

#### Usage Notes

By default, AutoUpgrade performs a Classic upgrade to upgrade the database.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.replay=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### remove_underscore_parameters

Removes underscore (hidden) parameters from `PFILE` files during upgrade, and after upgrade, for all Oracle Databases in the configuration file.

#### Usage Notes

Underscore parameters should only be used by advice of Oracle Support.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.remove_underscore_parameters=yes

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### restoration

(Available with Enterprise Edition only) Generates a Guaranteed Restore Point (GRP) for database restoration.

#### Usage Notes

This option determines whether database backup and database restoration must be performed manually by the DBA.

Standard Edition does not support Flashback Database, so this option is not available for Standard Edition. If your database is a Standard Edition Oracle Database, then you must ensure that you have a separate fallback mechanism is in place.

#### Options

`[yes | no]`

The default value is `yes`.

#### Example

    global.restoration=no

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### rman_catalog_connect_string

(Optional) Specifies the RMAN connection string used to connect to an RMAN database.

#### Usage Notes

To use this feature, you must save the RMAN username and password in the keystore using the AutoUpgrade command-line parameter `load_password`.

#### Example

    global.target_base=/u01/app/oracle
    sales4.rman_catalog_connect_string=string-alias

**Related Topics**

- [Daniel Overby Hansen Databases are Fun: AutoUpgrade New Features: Upgrade RMAN Catalog Schema](https://dohdatabase.com/2024/12/04/autoupgrade-new-features-upgrade-rman-catalog-schema/)

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### target_base

Specifies the target `ORACLE_BASE` path for the target Oracle home.

#### Example

    global.target_base=/u01/app/oracle
    sales4.target_base=/u04/app/oracle4

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### target_home

(Required for upgrade and deploy modes, if the target home is not on the system. Optional for analyze and fixups mode.) Specifies the target Oracle home (`ORACLE_HOME`) path.

#### Usage Notes

Use this option to specify the path to the target database home for the upgrade. This parameter can overwrite a global `target_home` setting.

    sales1.target_home=/target/Oracle/home

#### Options

Earlier releases of AutoUpgrade required you to set `target_home` and `target_version`. In later releases of AutoUpgrade, this restriction has been lifted for both `Analyze` and `Fixups` modes. However, if you don't set `target_home`, then you must specify `target_version`. Either one of them must be present.

#### Example

    sales3.target_home=/U01/app/oracle/product/19.0.0/dbhome_1
    sales1.target_home=/U01/app/oracle/product/23.0.0/dbhome_1

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File

### target_version

(Required if target Oracle home is not on the system, or is release 12.2) Specifies the target release version on which you want AutoUpgrade to perform the upgrade.

#### Usage Notes

AutoUpgrade uses the release version information that you provide in this parameter to ensure that the correct checks and fixups are used for the target Oracle Database release to which you are upgrading. The format for this parameter are period-delimited values of valid Oracle versions.

This option is only required if the target home is not present on the system, or if the target home is a 12.2 release. Otherwise, AutoUpgrade can derive the target release value.

#### Options

Valid values

- 12.2
- 18
- 19
- 21
- 23

#### Example

    global.target_version=23
    employees.target_version=19

**Parent topic:** Locally Modifiable Global Parameters for AutoUpgrade Configuration File
