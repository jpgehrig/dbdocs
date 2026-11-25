To specify a default behavior for a parameter for all Oracle Database upgrades addressed in the configuration file, you can use the optional AutoUpgrade global parameters.

### Usage Notes

All global parameters are optional, except for target_home when using upgrade or deploy mode. All global parameters take the prefix `global`.

The `add_after_upgrade_pfile` and `del_during_upgrade_pfile` global and local `PFILE` parameters operations are run in the following hierarchical order:

1.  Global Actions
    1.  Remove global
    2.  Add global
2.  Local Actions
    1.  Remove local
    2.  Add local

- add_after_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add after the `PFILE` is upgraded.
- add_during_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add during the `PFILE` is upgraded.
- after_action
  (Optional) Specifies a path and a file name for a custom user script that you want to have run after all the upgrade jobs finish successfully.
- autoupg_log_dir
  (Optional) Sets the location of the log files, and temporary files that belong to global modules, which AutoUpgrade uses.
- before_action
  (Optional) Specifies a custom user script that you want to have run for all upgrades before starting the upgrade jobs.
- catctl_options
  (Optional) Specifies one or more of a set of `catctl.pl` options that you can select for AutoUpgrade to submit for `catctl.pl` to override default behavior.
- del_after_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed after the `PFILE` upgrade.
- del_during_upgrade_pfile
  (Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed during the `PFILE` upgrade.
- drop_grp_after_upgrade
  (Optional) Deletes the Guaranteed Restore Point (GRP) after database upgrade.
- keystore
  (Optional) Specifies the location for a dedicated software keystore used exclusively by AutoUpgrade to store passwords, and other sensitive information.
- raise_compatible
  (Optional) Increases the compatible parameter to the default value of the target release after the upgrade is completed successfully.
- replay
  (Optional) Specifies whether to use replay to upgrade the database.
- target_base
  (Optional) Specifies the target `ORACLE_BASE` path for the target Oracle home.
- target_home
  (Optional for analyze and fixups modes. Required for upgrade and deploy modes.) Sets a global target home for all of the databases specified in the configuration file.
- target_version
  (Optional) Specifies the target release version on which you want AutoUpgrade to perform the upgrade.
- upgradexml
  (Optional) Generates the `upgrade.xml` file.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)

### add_after_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add after the `PFILE` is upgraded.

#### Usage Notes

This specification applies to all databases in the user configuration file.

#### Example

    global.add_after_upgrade_pfile=/path/to/my/add_after.ora

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### add_during_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to add during the `PFILE` is upgraded.

#### Usage Notes

This specification applies to all databases in the user configuration file.

#### Example

    global.add_during_upgrade_pfile=/path/to/my/add_during.ora

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### after_action

(Optional) Specifies a path and a file name for a custom user script that you want to have run after all the upgrade jobs finish successfully.

#### Usage Notes

The script that you use must be in the form of `name``.``ext` (for example, `myscript.sh`, so that AutoUpgrade can identify the type of script that you want to run. Permitted extension options:

- Unix shell (`.sh`)
- Microsoft Windows batch (`.bat`, `.cmd`)
- Microsoft Windows PowerShell (`.ps1`)

By default, if the script fails, then AutoUpgrade continues to run. Use the `Y` flag to specify that AutoUpgrade stops if the operating system detects that your script fails. If the script finishes with a status different than `0`, then it is considered a failed completion.

The output of the script is captured and stored in files. Both `stdout` and `stderr` are captured. The files are stored in the `postupgrade` subdirectory in the directory matching the specific database or job.

The following environment variables are set in the shell that runs the script:

- `ORACLE_SID`
- `ORACLE_UNQNAME`
- `ORACLE_BASE`
- `ORACLE_HOME`
- `TNS_ADMIN`

#### Examples

If the script fails, then stop AutoUpgrade:

    global.after_action=/path/to/my/script.sh Y

If the script fails, then continue AutoUpgrade:

    global.after_action=/path/to/my/script.sh

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### autoupg_log_dir

(Optional) Sets the location of the log files, and temporary files that belong to global modules, which AutoUpgrade uses.

#### Usage Notes

You can configure different log directory path in the `userconfig` file in the logs directory for a specific prefix

If you do not set this parameter to a path, then by default the log files are placed in the location indicated by the `orabase` utility for the databases that you include in your configuration file. In that case, the default logs directory is in the path `ORACLE_BASE``/cfgtoollogs/autoupgrade`.

If the `orabase` utility fails for all databases included in the configuration file, then the log file location is then based on the `temp` directory for the user running AutoUpgrade.

#### Examples

    global.autoupg_log_dir=/path/to/my/global/log/dir

Configure different log directory path in the `userconfig` file in the logs directory for a specific prefix

    global.autoupg_log_dir=/path/to/my/global/log/dir
    myprefix.log_dir=global.auto_log_dir:different/path

The result of using this syntax is that log files and temporary files are placed in the following path for databases identified by the prefix `myprefix`:

    /path/to/my/global/log/dir/different/path

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### before_action

(Optional) Specifies a custom user script that you want to have run for all upgrades before starting the upgrade jobs.

#### Usage Notes

The script that you use must be in the form of `name``.``ext` (for example,` myscript.sh`), so that AutoUpgrade can identify the type of script that you want to run. If you want to have a script run before a specific upgrade job, then specify that script by using the local parameter (`local.before_action`)

Permitted extension options:

- Unix shell (`.sh`)

- Microsoft Windows batch (`.bat`, `.cmd`)

- Microsoft Windows PowerShell (`.ps1`)

By default, if the script fails, then AutoUpgrade continues to run. Use the `Y` flag to specify that AutoUpgrade stops if the operating system detects that your script fails. If the script finishes with a status different than `0`, then it is considered a failed completion.

The output of the script is captured and stored in files. Both `stdout` and `stderr` are captured. The files are stored in the `preupgrade` subdirectory in the directory matching the specific database or job.

The following environment variables are set in the shell that runs the script:

- `ORACLE_SID`
- `ORACLE_UNQNAME`
- `ORACLE_BASE`
- `ORACLE_HOME`
- `TNS_ADMIN`

#### Examples

If the script fails, then stop AutoUpgrade:

    global.before_action=/path/to/my/script.sh Y

If the script fails, then continue AutoUpgrade:

    global.before_action=/path/to/my/script.sh

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### catctl_options

(Optional) Specifies one or more of a set of `catctl.pl` options that you can select for AutoUpgrade to submit for `catctl.pl` to override default behavior.

#### Options

Available `catctl.pl` options:

- `-n` Number of processes to use for parallel operations. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) . For Classic upgrades, the default for `CDB$ROOT` is 8.
- `-N` Number of processors to use when upgrading PDBs. For Replay upgrades, the number of parallel processes used for the upgrade defaults to the value of (`CPU_COUNT` divided by 4) For Classic upgrades, the default is 2
- `-T` Takes offline user schema-based table spaces.
- `-z` Turns on production debugging information for `catcon.pm`.

#### Examples

    global.catctl_options=-n 24 -N 4

**Related Topics**

- [Upgrade Script (catctl.pl) Parameters](../upgrd/upgrading-parallel-upgrade-utility-catctl-pl.md)

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### del_after_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed after the `PFILE` upgrade.

#### Usage Notes

This specification applies to all databases in the user configuration file.

#### Example

    global.del_after_upgrade_pfile=/path/to/my/del_after.ora

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### del_during_upgrade_pfile

(Optional) Specifies a path and file name of a `PFILE` whose parameters you want to have removed during the `PFILE` upgrade.

#### Usage Notes

This specification applies to all databases in the user configuration file.

#### Example

    global.del_during_upgrade_pfile=/path/to/my/del_during.ora

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### drop_grp_after_upgrade

(Optional) Deletes the Guaranteed Restore Point (GRP) after database upgrade.

#### Usage Notes

If you select this option, then GRP is deleted after upgrade completes successfully. If you set `raise_compatible` to `yes`, then you must also set the parameter `drop_grp_after_upgrade` to `yes`.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.drop_grp_after_upgrade=yes

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### keystore

(Optional) Specifies the location for a dedicated software keystore used exclusively by AutoUpgrade to store passwords, and other sensitive information.

#### Usage Notes

You can use the keystore parameter to specify where you want AutoUpgrade to create a dedicated software keystore that is used exclusively by AutoUpgrade.

The AutoUpgrade keystore contains the file `ewallet.p12` (similar to other kind of keystores used by the database). The file is created when you use the `save` command in the TDE prompt. If you choose to generate an auto-login keystore, then the file `cwallet.sso` is created as well. If you have an auto-login keystore, then AutoUpgrade does not prompt for a keystore password when AutoUpgrade starts.

The keystore generated by AutoUpgrade contains sensitive information, and is protected by a password that you choose when the keystore is used for the first time. Each time changes are made to the keystore, the password must be supplied. Unless you decide to create an auto-login keystore for AutoUpgrade, each time you start AutoUpgrade, and AutoUpgrade requires information from the keystore, you must provide the keystore password.

**Caution:**

Because the directory you specify with `global.keystore` contains a software keystore, it should be protected using the same security best practices as you use with all other highly secure keystore files.

#### Example

In the following example, replace `ORACLE_SID` with the system identifier of the database using the keystore.

    global.keystore=/etc/oracle/keystores/ORACLE_SID/autoupgrade

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

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

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### replay

(Optional) Specifies whether to use replay to upgrade the database.

#### Usage Notes

By default, AutoUpgrade performs a Classic upgrade to upgrade the database.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.replay=yes

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### target_base

(Optional) Specifies the target `ORACLE_BASE` path for the target Oracle home.

#### Usage Notes

Use of this parameter is only required in rare cases.

#### Example

    global.target_base=/u01/app/oracle
    sales4.target_base=/u04/app/oracle4

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### target_home

(Optional for analyze and fixups modes. Required for upgrade and deploy modes.) Sets a global target home for all of the databases specified in the configuration file.

#### Usage Notes

Use this option to avoid specifying the same `target_home` multiple times. This parameter can be overwritten locally.

#### Example

    global.target_home=/target/Oracle/home

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### target_version

(Optional) Specifies the target release version on which you want AutoUpgrade to perform the upgrade.

#### Usage Notes

AutoUpgrade uses the release version information that you provide in this parameter to ensure that the correct checks and fixups are used for the target Oracle Database release to which you are upgrading. The format for this parameter are period-delimited values of valid Oracle versions.

Valid values

- 12.2
- 18
- 19
- 21

This option is only required if the target home is not present on the system, or if the target home is a 12.2 release. Otherwise, AutoUpgrade can derive the target release value.

#### Example

    global.target_version=19
    employees.target_version=12.2

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File

### upgradexml

(Optional) Generates the `upgrade.xml` file.

#### Usage Notes

The `upgrade.xml` generated is equivalent to the file in earlier releases that the preupgrade package generated when you specified the XML parameter. This file is created during the analyze mode (`mode -analyze`). It is generated in the prechecks directory defined for the AutoUpgrade log files.

#### Options

`[yes | no]`

The default value is `no`.

#### Example

    global.upgradexml=yes

**Parent topic:** Global Parameters for the AutoUpgrade User Configuration File
