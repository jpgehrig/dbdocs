## AutoUpgrade Command-Line Parameters and Options

Review the AutoUpgrade parameters and select the parameters and options for your Oracle Database upgrade use case.

Use the parameters with the command `java -jar autoupgrade.jar`.

- AutoUpgrade Command-Line Syntax
  To see how to use AutoUpgrade to perform your upgrades, review the syntax and run time use cases.
- debug
  The AutoUpgrade parameter `debug` turns on the AutoUpgrade debug message feature, which assists you with correcting faulty AutoUpgrade job syntax.
- clear_recovery_data
  The AutoUpgrade parameter `clear_recovery_data` removes the recovery checkpoint, which causes AutoUpgrade to have a fresh start the next time the tool is launched on specified databases, or on all databases.
- config
  The AutoUpgrade parameter `config` identifies the configuration file that you use to provide information about databases that you want to upgrade.
- config_values
  The AutoUpgrade parameter `config_values` enables you to provide the same input values about systems as a text configuration file. You can use it conjunction with the `config` parameter.
- console
  The AutoUpgrade parameter `console` turns on the AutoUpgrade console, and provides a set of commands to monitor the progress of AutoUpgrade jobs.
- create_sample_file
  The AutoUpgrade parameter `create_sample_file` generates either a configuration file, or a settings file. You edit these files to create production configuration or settings files for AutoUpgrade.
- error_code
  The AutoUpgrade parameter `error_code` shows the error codes for AutoUpgrade errors.
- listchecks
  The AutoUpgrade parameter `listchecks` either provides a list of all upgrade checks for an upgrade, or if you specify a particular check, the details about the check you specify.
- load_password
  The AutoUpgrade parameter `load_password` enables you to enter passwords safely into AutoUpgrade's keystore.
- load_win_credential
  The AutoUpgrade parameter `load_win_credential` uses PowerShell to create a credential object so that AutoUpgrade can be run without interruption during the upgrade.
- mode
  The AutoUpgrade parameter `mode` value sets the mode from which AutoUpgrade runs.
- noconsole
  The AutoUpgrade parameter `noconsole` turns off the AutoUpgrade console, so that AutoUpgrade runs using only configuration file information.
- Patch
  The AutoUpgrade parameter `patch` is used to specify that AutoUpgrade is performing a patch operation, and not an upgrade operation.
- preupgrade
  The AutoUpgrade parameter `preupgrade` runs database checks and preupgrade fixups that fix most issues before you start an upgrade, and postupgrade fixups that fix most issues after an upgrade is completed.
- settings
  The AutoUpgrade parameter `settings` identifies the configuration file that you use to provide custom runtime configuration of the AutoUpgrade utility.
- version
  The AutoUpgrade parameter `version` prints to the terminal screen the current build of the `autoupgrade.jar` file.
- restore
  The AutoUpgrade parameter `restore` performs a system-level restoration of the AutoUpgrade jobs that you specify.
- restore_on_fail
  The AutoUpgrade parameter `restore_on_fail` automatically restores any job that failed during the deployment.
- zip
  The AutoUpgrade parameter `zip` creates a zip file of log files required for filing an AutoUpgrade service request.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### AutoUpgrade Command-Line Syntax

To see how to use AutoUpgrade to perform your upgrades, review the syntax and run time use cases.

#### Prerequisites

- AutoUpgrade is compatible with JDK 8 to JDK 11. You must have at least Java Development Kit (JDK) 8 or a later JDK release installed in your source environment.

  JDK 8 is installed with every release starting with Oracle Database 12c Release 2 (12.2). For any release earlier than 12.2, you must either run AutoUpgrade using the Java release in the target Oracle Database, or you must install JDK 8 on your source database server.

  Starting with Oracle Database 23ai, every Oracle home includes Java Runtime Environment (JRE) 11. AutoUpgrade is compiled with Java 11, and is compatible with JDK 8 to JDK 11.

- Oracle Database upgrades using the AutoUpgrade utility follow the same upgrade rules that apply to manual Oracle Database upgrades. Confirm that your source Oracle Database release is supported for upgrade.

With non-CDB to PDB conversion and upgrade, AutoUpgrade can automatically complete both upgrade and conversion when these conditions are met:

- The target release CDB must exist.

- In the AutoUpgrade configuration file, where the target CDB system identifier is `target_cdb`, you must set the local parameter `target_cdb` using the following syntax:

  `target_cdb=``target_cdb`. For example:

      target_cdb=cdb1

- The `target_cdb` value is the Oracle SID of the CDB into which you are plugging the non-CDB.

#### File Path

The AutoUpgrade utility is a Java JAR file that is located in the new release Oracle Database home.

`Oracle_home``/rdbms/admin/autoupgrade.jar`

Oracle strongly recommends that you obtain the latest AutoUpgrade JAR file from My Oracle Support. The JAR file and deployment instructions for the JAR file are available from My Oracle Support note 2485457.1

#### Syntax

AutoUpgrade command syntax is case-sensitive. Enter commands in lowercase.

    java -jar autoupgrade.jar [options]

Multiple options can be concatenated.

#### Run Type One (Basic) Parameters for AutoUpgrade

Run type one (Basic) parameters and options for AutoUpgrade provide a starting point for preparing for upgrades.

| Parameter                                                      | Description                                                                                                                            |
|:---------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `-version`                                                     | Displays the AutoUpgrade version.                                                                                                      |
| `-help`                                                        | Displays the help file for AutoUpgrade syntax.                                                                                         |
| `-create_sample_file [settings | config ``config-file-name``]` | Creates an example configuration file for AutoUpgrade. For a description of the options, see the `create_sample_file` parameter topic. |

#### Run Type Two (Core) Parameters for AutoUpgrade

Run type two (Core) parameters and options for AutoUpgrade provide essential upgrade functionality for most upgrade scenarios.

| Parameter                                                      | Description                                                                                                                                                                                                                                                                                     |
|:---------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-config [``config_path`` | -config_values ``config_values``]` | Identifies the configuration file that you use to provide information about databases that you want to upgrade. For a description of the options, see the `config` parameter topic.                                                                                                             |
| `-mode [analyze|fixups|deploy|upgrade|postfixups]`             | Sets the mode from which AutoUpgrade runs. For a description of the options, see the `mode` parameter topic.                                                                                                                                                                                    |
| `-restore -jobs ``job#`                                        | Performs a system-level restoration of the AutoUpgrade jobs that you specify                                                                                                                                                                                                                    |
| `-restore_on_fail`                                             | If set, then when a job fails, the database is restored automatically. Errors in PDBs are not considered irrecoverable, only errors in `CDB$ROOT` or Non-CDBs.                                                                                                                                  |
| `-console`                                                     | Starts AutoUpgrade with the console enabled.                                                                                                                                                                                                                                                    |
| `-noconsole`                                                   | Starts AutoUpgrade with the console disabled.                                                                                                                                                                                                                                                   |
| `-proceed`                                                     | Alters the predefined `start_time` on scheduled jobs, or jobs during the `REFRESHPDB` stage<br>For a full description of this parameter, see the `-proceed` parameter topic.                                                                                                                    |
| `-debug`                                                       | Enables debug messages.                                                                                                                                                                                                                                                                         |
| `-clear_recovery_data [-jobs ``job#,job#,...``]`               | Removes the recovery information, which causes AutoUpgrade to start from the beginning on all databases, or on databases in a comma-delimited list specified by `-jobs`. For a full description of the options, see the `clear_recovery_data` parameter topic.                                  |
| `-restore -jobs ``job#,job#,...`                               | Runs a system-level restoration of the specified jobs. The databases are flashed back to the Guaranteed Restore Point (GRP). Before you run this command, the GRP must already be created by AutoUpgrade. For a full description of the options, see the `clear_recovery_data` parameter topic. |
| `restore_on_fail`                                              | automatically restores any job that failed during the deployment.                                                                                                                                                                                                                               |
| `-zip [-sid ``sid``] [-d ``dir``]`                             | Zips up log files required for filing an AutoUpgrade service request. For a description of the options, see the `zip` parameter topic.                                                                                                                                                          |

#### Run Type Three (Additional) Parameters for AutoUpgrade

Run type three (Additional) parameters and options for AutoUpgrade are useful for particular upgrade scenarios, such as restarting from a failed point in an upgrade, or running particular fixups.

| Parameter                                  | Description                                                                                                                                                                                                                                     |
|:-------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-debug`                                   | Enables debug messages.                                                                                                                                                                                                                         |
| `-error_code`                              | Displays the AutoUpgrade error codes.                                                                                                                                                                                                           |
| `-help`                                    | Displays the help file for AutoUpgrade syntax.                                                                                                                                                                                                  |
| `-mode [analyze|fixups|postfixups]`        | Sets the mode from which AutoUpgrade runs. For a description of the options, see the `mode` parameter topic.                                                                                                                                    |
| `-listchecks`                              | Provides a list of all upgrade checks for an upgrade, or if you specify a particular check, the details about the check you specify.                                                                                                            |
| `-load_password`                           | Enables you to enter passwords AutoUpgrade requires safely into AutoUpgrade's keystore.                                                                                                                                                         |
| `-load_win_credential`                     | Uses PowerShell to create a credential object so that AutoUpgrade can be run without interruption during the upgrade.                                                                                                                           |
| `-patch`                                   | Specifies that AutoUpgrade is performing a patch operation, and not an upgrade operation.                                                                                                                                                       |
| `-preupgrade preupgrade_options ``options` | Runs database checks and preupgrade fixups that fix most issues before you start an upgrade, and postupgrade fixups that fix most issues after an upgrade is completed. For a description of the options, see the `preupgrade` parameter topic. |
| -settings                                  | Identifies the configuration file that you use to provide custom runtime configuration of the AutoUpgrade utility.                                                                                                                              |

**Related Topics**

- [My Oracle Support note 2485457.1](https://support.oracle.com/rs?type=doc&id=2485457.1)
- [Oracle Database Releases That Support Direct Upgrade](oracle-database-releases-that-support-direct-upgrade.md)

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### debug

The AutoUpgrade parameter `debug` turns on the AutoUpgrade debug message feature, which assists you with correcting faulty AutoUpgrade job syntax.

| Property       | Description                             |
|:---------------|:----------------------------------------|
| Parameter type | string                                  |
| Syntax         | `autoupgrade.jar -``parameter`` -debug` |

#### Description

The AutoUpgrade `debug` parameter turns on debugging messages, which can assist you with correcting AutoUpgrade command syntax.

#### Usage Notes

Use the `debug` parameter in concert with any other AutoUpgrade parameter.

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### clear_recovery_data

The AutoUpgrade parameter `clear_recovery_data` removes the recovery checkpoint, which causes AutoUpgrade to have a fresh start the next time the tool is launched on specified databases, or on all databases.

| Property       | Description                                                                                                                       |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                                                            |
| Syntax         | `clear_recovery_data [-jobs ``job_numbers``]`<br>where:<br>`job_numbers` is a comma-delimited list of jobs that you want to clear |

#### Description

The AutoUpgrade `clear_recovery_data` parameter removes the recovery information, which causes AutoUpgrade to start from the beginning on specified databases, or on all databases.

#### Usage Notes

Use after manually restoring a database and attempting a new upgrade. If no list of jobs is provided, then by default, all job metadata is removed. Removing the metadata does not remove log files, or reset the job identifier (`jobid`) counter. Only the AutoUpgrade files used to keep track of the progress of each job are removed.

#### Examples

The following example shows how to use the `clear_recovery_data` option after you encounter an issue, fix it, and then run AutoUpgrade again.

You start AutoUpgrade in deploy mode

    java -jar autoupgrade.jar -config config.cfg -mode deploy

However, you encounter an issue during the upgrade. You stop AutoUpgrade, restore the database, and make changes to the database to correct the issue. To start over the AutoUpgrade procedure and clear out the current job state information, specify the job number that is associated with the previously run job. If you specify the job number, then AutoUpgrade only removes the state information for that specific job. The rest of the jobs will remain untouched.

    java -jar autoupgrade.jar -config config.cfg -mode analyze -clear_recovery_data -jobs 100

**Note:**

The job ID number associates the job with the database. If you enter the wrong job id, then that causes AutoUpgrade to restart the wrong job from the beginning.

The analyze results are good, so you then run the deploy option again:

    java -jar autoupgrade.jar -config config.cfg -mode deploy

When you run `autoupgrade.jar -config` with the `-clear_recovery_data` parameter, AutoUpgrade only drops state files. It ignores any previously generated log files, so you can retain log files for further reference. Running AutoUpgrade with the `-clear_recovery_data` parameter also preserves the latest `jobid` information, so that the `jobid` AutoUpgrade creates for the next job is the next ID in sequence. By maintaining the `jobid` state, AutoUpgrade helps you to avoid mixing log output from earlier AutoUpgrade jobs in the same log file.

The following are additional examples of how you can run the `clear_recovery_data` parameter.

    java -jar autoupgrade.jar -config config.cfg -clear_recovery_data
    java -jar autoupgrade.jar -config config.cfg -clear_recovery_data -jobs 111,222

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### config

The AutoUpgrade parameter `config` identifies the configuration file that you use to provide information about databases that you want to upgrade.

| Property       | Description           |
|:---------------|:----------------------|
| Parameter type | string                |
| Syntax         | `-config [configfile` |
| Default value  | None                  |

#### Description

The `config` parameter specifies a configuration file name. It takes three arguments:

- The configuration file name

- (Optional) The path to the configuration file, as represented by `config-file`

  When used in conjunction with the parameter `-load_password`, AutoUpgrade also creates a keystore for Transparent Data Encryption (TDE) passwords in the location specified by the global configuration file parameter `global.keystore`, if that parameter is set in the configuration file for a database.

#### Examples

Running AutoUpgrade with a configuration file named `myconfig.cfg`, with the processing mode `deploy`:

    java -jar autoupgrade.jar -config myconfig.cfg -mode deploy

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### config_values

The AutoUpgrade parameter `config_values` enables you to provide the same input values about systems as a text configuration file. You can use it conjunction with the `config` parameter.

| Property       | Description                                                                        |
|:---------------|:-----------------------------------------------------------------------------------|
| Parameter type | String.                                                                            |
| Syntax         | `-config_values [config-parameter1=value*,config-parameter2=value,...]`<br>`     ` |
| Default value  | None.                                                                              |

#### Description

The `config_values` parameter enables you to provide values about database paths, instances, and target releases through the AutoUpgrade command line that otherwise require you to specify a configuration file. AutoUpgrade then creates a configuration file as the utility runs. Using `config_values` enables you to run AutoUpgrade without a configuration file.

The `config_values` options are a comma-delimited list that can support multiple database upgrades. Each database configuration is separated by asterisks (\*) to identify different databases. Global entries must include the global prefix in the name. For example:

    global.autoupg_log_dir=/u01/app/oracle/cfgtoollogs/upgradelogs/

Local entries only need to include the name:

    target_home=/u01/app/oracle/product/21.0.0.0/dbhome_1

Logging directories are resolved in the following manner.

- Case: Global `autoupg_log_dir` is not specified.

  If the `config_file` parameter is not passed to AutoUpgrade, then the local directory is used as the global log directory. If the `config_file` parameter is not passed to AutoUpgrade, then the global log directory defaults to the Java temporary directory:

  - Unix and Linux systems: `/tmp/autoupgrade`
  - Microsoft Windows: `C:\Users\name\AppData\Local\Temp\autoupgrade`
  - A configuration file is created with the name `autoupgradeYYYYMMMHHMMSS.cfg`, where `YYYY` is year, `MMM` is month, `HH` is hour, `MM` is minute, and `SS` is second.

- Case: `Global autoupg_log_dir` is specified.

  If the `config_file` parameter does not pass the directory to AutoUpgrade, then AutoUpgrade creates a configuration file in the AutoUpgrade log directory specified by the parameter. If the `config_file` parameter does not pass the directory to AutoUpgrade, then the configuration file is created under the global log directory. If you specify a configuration file name that already exists, then AutoUpgrade renames the existing configuration file using the suffix `YYYY``MMM``HH``MMMM``SS``.cfg`, where `YYYY` is year, `MMM` is month, `HH` is hour, `MM` is minute, and `SS` is second. For example: on April 29, 2020, at 08:30:04, if configuration file `\tmp\autoupgrade.cfg` already exists, and you pass the file name `-config_file \tmp\autoupgrade.cfg` to AutoUpgrade, then the existing file is renamed to `\tmp\autoupgrade.cfg20200429083004`. AutoUpgrade then creates the new configuration file `\tmp\autoupgrade.cfg`.

If you use the `-config_values` parameter, and the user account running the AutoUpgrade command has the following operating system environment variables set, then AutoUpgrade picks up the path defined for these variables:

- `ORACLE_HOME` - The Oracle home path for the source Oracle home

- `ORACLE_TARGET_HOME` - The target Oracle home path.
  - Linux and Unix: Equivalent to an `export ORACLE_TARGET_HOME` command. For example: `export ORACLE_TARGET_HOME=/u01/app/oracle/product/19.0.0/`
  - Microsoft Windows: Equivalent to a `SET ORACLE_TARGET_HOME` command. For example: `SET ORACLE_TARGET_HOME=C:\oracle\19`

- `ORACLE_SID` - The Oracle Database system identifier (SID).
  - Linux and Unix: Set with the operating system shell command `export ORACLE_SID`. For example: `export ORACLE_SID=sales`
  - Microsoft Windows: Set with the operating system shell command `SET ORACLE_SID` command. For example: `SET ORACLE_SID=sales`

- `ORACLE_TARGET_VERSION` - The target release of the new Oracle home. You must set this operating system environment variable either when the target Oracle home does not exist, or the target home is a release earlier than Oracle Database 18c.

  - Linux and Unix: Set with `export ORACLE_TARGET_VERSION`. For example, for Oracle Database 19c:

        export ORACLE_TARGET_VERSION=19.1

    For Oracle Database 21c:

        export ORACLE_TARGET_VERSION=21.1

  - Microsoft Windows: Set with `SET ORACLE_TARGET_VERSION`.

    For example, for Oracle Database 19c:

        SET ORACLE_TARGET_VERSION=19.1

    For example, for Oracle Database 21c:

        SET ORACLE_TARGET_VERSION=21.1

  If you use the `config_values` parameter in place of a configuration file, and you do not have these operating system environment variables set for the user account running AutoUpgrade, then you must provide at least these four values as arguments using `config_values`.

#### Example: Running AutoUpgrade With an Existing Configuration File

Scenario: Running AutoUpgrade with an existing configuration file, using `config_values`. The following command syntax creates the `global.autoupg_log_dir` from the local directory where the `myconfig.cfg` file is created. As a result of this command, the location for `global.autoupg_log_dir` is set to `/dir`:

    java –jar autoupgrade.jar –config /dir/myconfig.cfg –config_values
            “source_home=/srcdir, target_home=/trgdir, sid=sales” –mode
            deploy

The configuration file `myconfig` is created in the path `/dir`, with the following entries:

    global.autoupg_log_dir=/dir
    autoupgrade1.source_home=/srcdir
    autoupgrade1.target_home=/trgdir
    autoupgrade1.sid=sales

#### Example: Running AutoUpgrade Without Specifying a Value for `–config_values`

In analyze, fixup, upgrade, or deploy mode, if you have set user environment values that AutoUpgrade requires to run, and you do not pass these values as an argument for `–config_values`, then AutoUpgrade defaults to using the user environmental variables set on the server.

To understand how this works, suppose you run AutoUpgrade as the user `oracle`, for which the following environment variables are set, where the target version is Oracle Database 21c:

- `ORACLE_HOME` is set to `/u01/app/oracle/product/12.2.0.1/dbhome_1`
- `ORACLE_TARGET_HOME` is set to `/u01/app/oracle/product/19.0.0/dbhome_1`
- `ORACLE_SID` is set to `sales`
- `ORACLE_TARGET_VERSION` is set to `19.1`

Now suppose you run the following command at 11:45:15 AM on September 30, 2020:

    [Wed Sep 30 11:45:15] oracle@example:~$ java –jar autoupgrade.jar –config_values –mode analyze

Because the log directory was unspecified, AutoUpgrade defaults writing the configuration file for the run to the temporary directory. The configuration file AutoUpgrade creates resides in the path `/tmp/autoupgrade` as the file`/tmp/autoupgrade/autoupgrade20200501114515.cfg`, with the following entries:

    global.autoupg_log_dir=/tmp/autoupgrade
    # Value from environmental variable ORACLE_HOME
    autoupgrade1.source_home=/u02/app/oracle/122
    # Value from environmental variable ORACLE_TARGET_HOME
    autoupgrade1.target_home=/scratch/oracle/19
    # Value from environmental variable ORACLE_SID
    autoupgrade1.sid=sales
    # Value from environmental variable ORACLE_TARGET_VERSION
    autoupgrade1.target_version=19.3

This option enables you to use AutoUpgrade to handle a single database upgrade without requiring you to specify extensive details about the upgrade.

#### Example: Running AutoUpgrade with `–config_values` entries for multiple databases

In this scenario, you run AutoUpgrade with `–config_values` entries for multiple databases, using `*` to delimit values for each database, with a target release of Oracle Database 21c:

     java –jar autoupgrade.jar –config /tmp/auto.cfg –config_values "global.autoupg_log_dir=/scratch/upglogs,source_home=/scratch/122,target_home=/scratch/21,sid=sales,*,source_home=/scratch/18,target_home=/scratch/21,sid=employees"

The configuration file is created in the directory `/tmp` as `/tmp/auto.cfg`, with the following entries.

    global.autoupg_log_dir=/scratch/upglogs
    autoupgrade1.source_home=/scratch/19
    autoupgrade1.target_home=/scratch/21
    autoupgrade1.sid=sales
    autoupgrade2.source_home=/scratch/19
    autoupgrade2.target_home=/scratch/21
    autoupgrade2.sid=employees

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### console

The AutoUpgrade parameter `console` turns on the AutoUpgrade console, and provides a set of commands to monitor the progress of AutoUpgrade jobs.

| Property       | Description                                                  |
|:---------------|:-------------------------------------------------------------|
| Parameter type | string                                                       |
| Syntax         | `autoupgrade.jar -config ``your-file`` -mode ``your-mode`` ` |

#### Description

To monitor upgrades, use the AutoUpgrade parameter `console` to run the Console, which monitors the status of upgrade jobs.

The AutoUpgrade console starts by default with the AutoUpgrade command. You can enable or disable the AutoUpgrade console using the options `-console`\|`-noconsole`

When you use the `-noconsole` option, AutoUpgrade runs using only the settings in the configuration file, without requiring console input. Use the `noconsole` option when you want to create scripts for AutoUpgrade, such as in cases where you want to analyze multiple databases. After the AutoUpgrade jobs are finished, you can review the output of the Analyze mode logs to see what is required to upgrade each of the databases included with your configuration script.

You can use the proceed option to have AutoUpgrade start a job at a time that you specify. You have three options:

- Specify no start time (default: Delay start by one minute after the command is run)
- Specify a start time delay with an hour and minute value from the time the command is run
- Specify a start delay with a day, month, year, minute, and second delay value from the time the command is run

**Note:**

You can start as many instances of AutoUpgrade as you want, but each instance must use a unique global logging directory (`global.autoupg_log_dir`). If you only have one global logging directory, then you can only start one instance.

#### Usage Notes

When you start the console, you can use options within the console.

| Console Option                                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-exit`                                                                  | Closes and exits from the console. If there are jobs running, then they are stopped.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-help`                                                                  | Displays the console command help.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-lsj [(-r|-f|-p|-e)-a ``number``] -n ``number`                          | Lists jobs by status, up to the number of jobs you specify with the numeric value `number`. You can use the following flags:<br>`-f`: (Optional) Filter by finished jobs.<br>`-r`: (Optional) Filter by running jobs.<br>`-e`: (Optional) Filter by jobs with errors.<br>`-p`: (Optional) Filter by jobs in preparation.<br>`-a ``number`: (Optional) Repeats the command after the number of seconds specified by integer value (`number`).<br>`-n ``number``:` (Required) Number of jobs to display, specified by integer value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-lsr`                                                                   | Displays the restoration queue.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-lsa`                                                                   | Displays the queue of jobs to stop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-proceed -job ``job_number`` -newStartTime ``values`                    | Enables you to alter the predefined `start_time` on scheduled jobs or jobs during the `REFRESHPDB` stage. Use this feature with the AutoUpgrade hot cloning and relocate feature.<br>You must specify a job number by using the `-job_number` flag.<br>The `-proceed` parameter can only be used with the AutoUpgrade Console. You cannot use `-proceed` in `-noconsole` mode.<br>You can enter `-newStartTime` to specify a specific time. If no value for `-newStartTime` is specified, then by default the start time is delayed by one minute from the time the command is run for the job specified.<br>• `job_number` specifies the job number where you want to alter the start time.<br>• When specifying a different start time using the hour and minute, the following arguments apply:<br>• `#``h` specifies the numeric value of how many hours the job should be delayed. For example: 10h specifies a ten hour delay from the time the command is run.<br>• `#``m` is the numeric value of how many minutes past the hour you specify that the job should be delayed. For example, when the specification is `+10h17m`, the start time is specified as a ten hours and seventeen minutes delay from the time the command is run.<br>• When specifying a different date and time start, specify the delay using `dd``/``mm``/``yyyy`` ``hh``:``mm``:``ss` format, where the delay is by day, month, and year, and the time in 24-hour format by hour, minutes and seconds<br>`upg> proceed -job 100 -newStartTime +10h17m` |
| `-tasks`                                                                 | Displays the tasks that are running.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-clear`                                                                 | Clears the terminal display.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-resume -job ``number`` [-ignore_errors=ORA-``number``,ORA-``number``]` | Restarts from a previous job that was running, specified by a numeric value (`number`) for the job.<br>`ignore_errors` option: This flag is optional. If there are any resume errors during patching or upgrade stage processing, then that is reported as a stage failure. AutoUpgrade will not proceed to postupgrade operations. There are some cases where an error can be ignored, and postupgrade operations can continue. If you think that a specific error will not affect patching or upgrade, then you can use the `ignore_errors` option to specify the errors that you want to ignore, so that postupgrade operations can continue. The error numbers are specified by a comma-delimited list of errors. Example:<br>`-resume -job 444 -ignore_errors=ORA-48101,ORA-00001`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-status [-job ``number`` | -c ``dbname``| -config| -a ``number``]`      | Lists the status of a particular job with the response you specify with the flag.<br>Flags:<br>`-job ``number`: Shows information about a specific job, specified by a numeric value.<br>`-c ``dbname`: Displays information about the specific database name that you specify (`dbname`), with detailed information, if available.<br>`-config` number Displays configuration information for the job that you specify.<br>`-a ``number`: (Optional) Repeats the command after the number of seconds specified by integer value (`number`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-restore [-job (0-9)|-all_failed]`                                      | Restores the database in the AutoUpgrade job specified by the integer value `number` to its state before starting the upgrade.<br>When run with the `all_failed` option, restores all failed jobs to their previous state before the upgrade started.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-logs`                                                                  | Displays all log file locations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-abort -job ``number`                                                   | Stops the job specified by the numeric value that you provide (`number`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-h[ist][/``number``]`                                                   | Displays the console command-line history, and takes the option to run a command again, depending on the flat with which you run it:<br>Flags:<br>`/` Runs the last command again.<br>`/ ``number` Runs the command in the history log specified by the command line number that you specify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### create_sample_file

The AutoUpgrade parameter `create_sample_file` generates either a configuration file, or a settings file. You edit these files to create production configuration or settings files for AutoUpgrade.

| Property       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Syntax         | `-create_sample_file config [``filename``] [full|unplug|noncdbtopdb] | settings [``filename``]`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Default value  | For `create_sample_file config`, if you append a filename to the command, then an example configuration file is created with the name you provide. If you do not provide an output file name, then the example configuration file is created with the name `sample_config.cfg`.<br>You can add a clause to specify the type of AutoUpgrade configuration file, using one of the following options:<br>• `full` : A complete options AutoUpgrade configuration file<br>• `unplug` : An AutoUpgrade configuration file with options for unplug-plug upgrades of PDBs.<br>• `noncdbtopdb` : An AutoUpgrade configuration file with options for nonCDB to PDB upgrades.<br>When you add the `settings` clause, an internal settings configuration file is generated. You can accept the default file name, or specify a file name. |

#### Usage Notes

The `create_sample_file` parameter is optional. It cannot be used together with other parameters. When you specify this parameter, it requires either the `settings` or the `config` clause:

`settings`: Generates an AutoUpgrade **settings** file, either with the name `sample_autoupg.cfg`, or with a name that you specify.

`config`: Generates an AutoUpgrade **configuration** file, either with the name `sample_config.cfg`, or with a name that you specify.

After you generate one of these example files, you can modify the file to control how the AutoUpgrade utility performs upgrades.

- `config`: Generates a template upgrade configuration file of a configuration mode type. AutoUpgrade generates a file named `sample_config.cfg`, or with a name you provide, in the current folder

- `settings` AutoUpgrade generates a file named `sample_autoupg.cfg`, or with the name you provide, in the current folder.

For both the `config` and `settings` options, the default file name is generated with the extension `.cfg`. However, AutoUpgrade can read files without an extension, or with an extension that you provide, as long as the file is a valid (plain text) file. The default extension is for convenience in identifying these files as configuration files.

Generating an example configuration file is a standard part of preparing to use AutoUpgrade. After you customize the configuration file parameters in the example configuration file, you can use that file as the production settings and configuration file for your upgrade.

**Caution:**

The settings file is used to overwrite internal settings of the AutoUpgrade. Generating an example settings file is not required for most use cases. Use carefully.

#### Examples

Example of running the `create_sample_file` parameter with the `config` clause:

    [oracle@example ~]$ java -jar autoupgrade.jar -create_sample_file config
    Created sample configuration file /home/oracle/sample_config.cfg

Example of running the `create_sample_file` parameter with the `config`, clause specifying an output configuration file name:

    [oracle@example ~]$ java -jar autoupgrade.jar -create_sample_file config sales01
    Created sample configuration file /home/oracle/sales01.cfg

Example of running the `create_sample_file` parameter with the `settings` clause:

    oracle@example ~]$ java -jar autoupgrade.jar -create_sample_file settings
    Created sample settings file /home/oracle/sample_autoupg.cfg

Example of running the `create_sample_file` parameter with the `settings`, clause specifying an output configuration file name:

    oracle@example ~]$ java -jar autoupgrade.jar -create_sample_file settings testsetting.test
    Created sample settings file /home/oracle/testsetting.test

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### error_code

The AutoUpgrade parameter `error_code` shows the error codes for AutoUpgrade errors.

| Property       | Description                                                                                                                                                                                                |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                                                                                                                                     |
| Syntax         | `-error_code [``errorcode``] `                                                                                                                                                                             |
| Default value  | When no error code is specified, all AutoUpgrade error codes are displayed in the Console.<br>When an error code is specified, the information about the specified error code is displayed in the Console. |

#### Examples

When entered without a specification, Autoupgrade produces descriptions of all of the error codes:

    $ java -jar autoupgrade.jar  -error_code
    ERROR1000.ERROR  = UPG-1000
    ERROR1000.CAUSE  = It was not possible to create the data file where the jobsTable is being written or there was a problem during the writing, it might be thrown due to a permission error or a busy resource scenario

    ERROR1001.ERROR  = UPG-1001
    ERROR1001.CAUSE  = There was a problem reading the state file perhaps there was corruption writing the file and in the next write it might be fixed

    ERROR1002.ERROR  = UPG-1002
    ERROR1002.CAUSE  = Error deserializing the object for rerun, review log for any errors
    .
    .
    .

When entered with a specific error code, AutoUpgrade provides output for the error that you specify. For example:

    java -jar autoupgrade.jar -error_code UPG-3010

This command produces the following output:

    ERROR3010.ERROR  = UPG-3010
    ERROR3010.CAUSE  = Error running approot_to_pdb.sql script

Here is another example:

    $ java -jar autoupgrade.jar  -error_code UPG-1400

This command produces the following output:

    ERROR1400.ERROR  = UPG-1400
    ERROR1400.CAUSE  = Database upgrade failed with errors

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### listchecks

The AutoUpgrade parameter `listchecks` either provides a list of all upgrade checks for an upgrade, or if you specify a particular check, the details about the check you specify.

| Property       | Description                                                                                 |
|:---------------|:--------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                      |
| Syntax         | `-listchecks [checkname]`                                                                   |
| Default value  | None. If no specific check is specified, then a list of all AutoUpgrade checks is provided. |

#### Examples

When entered without a specification, the Autoupgrade `listchecks` parameter generates descriptions of all of the checks AutoUpgrade performs for the upgrade.

    $ java -jar autoupgrade.jar  -listchecks
    Check : AMD_EXISTS
            Description : Starting with Oracle Database 12c, the OLAP Catalog (OLAP AMD) is desupported and will be automatically marked as OPTION OFF during the database upgra
    de if present. Oracle recommends removing OLAP Catalog (OLAP AMD) before database upgrade.  This step can be manually performed before the upgrade to reduce downtime.
            Fixup Action : Remove OLAP Catalog by running the {1} SQL script $ORACLE_HOME/olap/admin/catnoamd.sql script.
            Severity : WARNING
            Fixup Stage : PRE
            Min Version(inclusive) Check applies : NONE
            Max Version(exclusive) Check applies : NONE
            Check Introduced Version : NONE
            Check Removed Version : NONE
            Manual Fixup or Automatic : AUTO
            AutoUpgrade Only : NO
            Run for Datapatch : NO

    Check : APEX_MANUAL_UPGRADE
            Description : Starting with Oracle Database Release 18, APEX is not upgraded automatically as part of the database upgrade. Refer to My Oracle Support Note 1088970.
    1 for information about APEX installation and upgrades. Refer to MOS Note 1344948.1 for the minimum APEX version supported for your target database release. Unsupported ver
    sions of APEX will be in an INVALID state when its database dependencies are not in sync with the upgraded database.
            Fixup Action : Upgrade Oracle Application Express (APEX) manually before or after the database upgrade.
            Severity : WARNING
            Fixup Stage : PRE
            Min Version(inclusive) Check applies : NONE
            Max Version(exclusive) Check applies : NONE
            Check Introduced Version : 18
            Check Removed Version : NONE
            Manual Fixup or Automatic : MANUAL
            AutoUpgrade Only : NO
            Run for Datapatch : NO

    Check : APEX_PATCH
            Description : The APEX patching process is not performed by the {1} Oracle database upgrade.  The APEX version upgrade only ensures that the APEX version is upgrade
    d to version {3} and does not guarantee the version is brought all the way to the patched level {2}.  If a PDB from this CDB is unplugged and plugged into another ROOT, the
    .
    .
    .

When entered with a specified check, `listchecks` provides details about the checks for the check you specify:

    $ java -jar autoupgrade.jar  -listchecks XDB_RESOURCE_TYPE
    Check : XDB_RESOURCE_TYPE
            Description : Direct access to either TYPE XDB.XDB$RESOURCE_T or TABLE XDB.XDB$RESOURCE is restricted to Oracle internal code only.
            Fixup Action : Please contact Oracle Support to resolve the problem.
            Severity : ERROR
            Fixup Stage : PRE
            Min Version(inclusive) Check applies : 11.1
            Max Version(exclusive) Check applies : NONE
            Check Introduced Version : NONE
            Check Removed Version : NONE
            Manual Fixup or Automatic : MANUAL
            AutoUpgrade Only : NO
            Run for Datapatch : NO

**Related Topics**

- [Databases are Fun: AutoUpgrade New Features: List All Checks](https://dohdatabase.com/2025/02/11/autoupgrade-new-features-list-all-checks/)

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### load_password

The AutoUpgrade parameter `load_password` enables you to enter passwords safely into AutoUpgrade's keystore. When you run AutoUpgrade in analyze mode, you are notified which passwords are needed, and can be loaded into the AutoUpgrade keystore.

| Property       | Description                                                                       |
|:---------------|:----------------------------------------------------------------------------------|
| Parameter type | string                                                                            |
| Syntax         | `-load_password`                                                                  |
| Default value  | None. AutoUpgrade prompts you for password input values in an interactive prompt. |

#### Description

To provide passwords required for upgrade, you can use the `load_password` parameter. This parameter must be used in conjunction with the `-config` parameter and the configuration file global parameter `keystore`, to designate the location of the dedicated software keystore where AutoUpgrade securely stores passwords. The `-load_password` parameter takes no arguments. Instead, it starts an interactive prompt with specific commands that enable you to provide information required for the keystore. This option can be used to add Transparent Data Encryption passwords (TDE), My Oracle Support credentials (MOS), Oracle Recovery Manager (RMAN) credentials, and database SYS passwords (PWD). The command options are slightly different for each of these use cases. Common options include the following:

- `group [tde|pwd|rman|mos]`

  Specifies the scope of the `load_password` option:

  - `mos`: Specifies that the `load_password` options in the group apply to the My Oracle Support user (MOS). This group option applies only when AutoUpgrade is used with the `-patch` command line option.
  - `pwd`: Specifies that the `load_password` options in the group apply to the specified database SYS password (PWD). This group option applies to both upgrades and patching.
  - `tde`: Specifies that the `load_password` options in the group apply to Transparent Data Encryption (TDE). This option applies for both upgrades and patching.
  - `rman`: Specifies that the `load_password` options in the group apply to the specified database RMAN password (RMAN). This group option applies only when AutoUpgrade is not used with the `-patch` command line option.

- `help`

  Lists all the available `load_password` commands.

- `exit`

  Exits the `load_password` interactive console. If the keystore has been modified and not yet saved, then you are prompted to determine if you want to save the keystore before exiting.

During the upgrade, AutoUpgrade places passwords in an encrypted password array in memory, so that AutoUpgrade can access source database keystores and resources. No passwords are written to SQL\*Plus scripts during the upgrade. After AutoUpgrade no longer requires the passwords, these passwords are purged from memory. No log records are kept of the passwords.

#### Transparent Data Encryption (TDE) Group Options

**Note:**

- If you configure an Keystore External Password Store in the database, then AutoUpgrade detects the presence of an Keystore External Password Store, and uses this external password store instead of requiring manual input of the TDE keystore passwords. However, if all databases are configured with Keystore External Password Store, then in some situations, you can still need to define global.keystore.
- In some situations, AutoUpgrade needs access to the AutoUpgrade keystore to write other sensitive information. For example, AutoUpgrade can write transport secrets (passphrases) that are used by `ADMINISTER KEY MANAGEMENT EXPORT KEYS` and `ADMINISTRATER KEY MANAGEMENT IMPORT KEYS` commands to AutoUpgrade.
- When you specify a keystore to load a Transparent Data Encryption passwords (TDE) group, the TDE keystore is for for the CDB root and any associated united mode PDBs. If the TDE keystore is not on the same local host CDB, then loading the TDE keystore fails for unplug-relocate operations.

For more information about Keystore External Password Stores, refer to Oracle Database Advanced Security Guide or Oracle Database Data Redaction Guide.

When you run AutoUpgrade using `-mode analyze`, AutoUpgrade detect which passwords are needed for the databases specified for upgrade in your configuration file, and lists them in the preupgrade summary report. Before the upgrade, you can then use `-load_password` to enter the passwords for the databases. These passwords are stored safely in AutoUpgrade's own keystore, in the location specified by `global.keystore`. The passwords are used only to access the source database TDE keystores, and to write the TDE passwords in the target keystores.

**Caution:**

Because the directory you specify AutoUpgrade to create with `global.keystore` contains a software keystore, it should be protected using the same security best practices as you use with TDE keystore files.

When you run AutoUpgrade with the `-load_parameter` option at the command line, AutoUpgrade starts an interactive console so that you can configure password options. The console indicates if you need

- `add ``ORACLE_SID`` [-pdb ``isolated-pdb``]`

  Adds a TDE password for the specified Oracle System identifier (`ORACLE_SID`).

  If you have an isolated PDB that requires a password, then use the optional `-pdb` parameter in the configuration file to specify an isolated PDB for which you want to provide a password. If the CDB root and all PDBs are configured in united mode, then the `-pdb` parameter is not required, as the keystore is shared between the CDB root and all PDBs that are configured in united mode.

- `delete ``ORACLE_SID`` [-pdb ``isolated-pdb``]`

  Deletes a loaded password for the specified Oracle System identifier (`ORACLE_SID`).

  If you loaded a password for an isolated PDB that you want to delete, then use the optional `-pdb pdbname` parameter in the configuration file to specify the name of the isolated PDB whose password you want to delete. If the CDB root and all PDBs are configured in united mode, then the `-pdb` parameter is not required.

- `list`

  Lists each Oracle Database by Oracle System Identifier (`ORACLE_SID`), provides details for each database, and indicates if further actions are necessary to perform an encrypted database upgrade. AutoUpgrade starts a deploy mode only when there are no pending actions for any of the databases listed in the configuration file. If an action is required before a database can be upgraded, then the AutoUpgrade check `tde_passwords_required` fails during the prechecks stage.

#### My Oracle Support (MOS) Credential Group Options

- `add -user ``email-address`

  The `add -user ``email-address` option stores My Oracle Support credentials in the AutoUpgrade Patching keystore, where `email-address` is the user email that you specify. When `download=YES`, the credentials are used to connect to My Oracle Support so that AutoUpgrade can download the required patches.

- `list` displays whether My Oracle Support credentials have been loaded into the keystore, and if so, whether the loaded credentials could be used successfully to connect to My Oracle Support. You can only load one set of credentials.

- `delete -user` deletes the My Oracle Support credentials.

#### Oracle Recovery Manager (RMAN) Credential Group Options

- `add ``ORACLE_SID`` -user ``username`

  Adds the username and password for the specified Oracle System identifier (`ORACLE_SID`).

- `delete ``ORACLE_SID`` -user ``username`

  Deletes username and password for the specified Oracle System identifier (`ORACLE_SID`).

- `list`

  Lists each Oracle Database by Oracle System Identifier (`ORACLE_SID`), provides details for each database, and indicates if further actions are necessary.

- `pwd`

  Specifies the RMAN password needed to connect to the specified database.

#### Database SYS Password (PWD) Credential Group Options

- `add ``ORACLE_SID`` -user ``username`

  Adds the username and password for the specified Oracle System identifier (`ORACLE_SID`).

- `delete ``ORACLE_SID`` -user ``username`

  deletes username and password for the specified Oracle System identifier (`ORACLE_SID`).

- `list`

  Lists each Oracle Database by Oracle System Identifier (`ORACLE_SID`), provides details for each database, and indicates if further actions are necessary to perform an encrypted database upgrade. AutoUpgrade starts a deploy mode only when there are no pending actions for any of the databases listed in the configuration file. If an action is required before a database can be upgraded, then the AutoUpgrade check `tde_passwords_required` fails during the prechecks stage.

- `pwd`

  Specifies the SYS password needed to connect to the specified database. Sampe options as RMAN

- `exit`

  Exits the `load_password` interactive console. If the keystore has been modified and not yet saved, then you are prompted to determine if you want to save the keystore before exiting.

#### Examples

#### TDE Keystore Passwords Added to AutoUpgrade Keystore

Run AutoUpgrade to add the TDE keystore passwords to AutoUpgrade's own keystore, using a configuration file named `myconfig.cfg`, where `-load_password` is used to prompt you for TDE passwords of any database where the TDE keystore password is needed:

    java -jar autoupgrade.jar -config myconfig.cfg -load_password

After the TDE passwords are loaded, you can then either run AutoUpgrade in `analyze` or config `mode`:

    java -jar autoupgrade.jar -config myfile.cfg -mode deploy

AutoUpgrade uses the TDE password files from its own keystore to access the source database TDE keystores, and to write the TDE passwords in the target database keystores.

#### Multiple Load Password Options Used with Multiple Source Database Upgrades

In the following example, all of the `load_password` command options are used to load TDE passwords from source databases `db12201`, `cdb122`, and `db19x` to the common target CDB `cdb19x`:

    $ java -jar autoupgrade.jar -config config.cfg -load_password
    Processing config file ...

    Starting AutoUpgrade Password Loader - Type help for available options
    Creating new keystore - Password required
    Enter password:
    Enter password again:
    Keystore was successfully created

    TDE> add cdb19x
    Enter your secret/Password:
    Re-enter your secret/Password:
    TDE> add cdb122
    Enter your secret/Password:
    Re-enter your secret/Password:
    TDE> add db12201
    Enter your secret/Password:
    Re-enter your secret/Password:
    TDE> add db19x
    Enter your secret/Password:
    Re-enter your secret/Password:
    TDE> delete cdb19x
    TDE> list
    +----------+----------------+------------------+-----------+------------------+
    |ORACLE_SID|Action Required | TDE Password     |SEPS Status|Active Wallet Type|
    +----------+----------------+------------------+-----------+------------------+
    |    cdb122|                |          Verified|   Inactive|               Any|
    |    cdb19x|Add TDE password|No password loaded|   Inactive|               Any|
    |   db12201|                |          Verified|   Inactive|        Auto-login|
    |     db19x|                |          Verified|   Inactive|               Any|
    +----------+----------------+------------------+-----------+------------------+
    TDE> help
    The following options are available
    -----------------------------------
    1 add
    2 delete
    3 list
    4 group
    5 save
    6 help
    7 exit

    TDE> save
    Convert the keystore to auto-login [YES|NO] ? YES
    TDE> exit

    AutoUpgrade Password Loader finished - Exiting AutoUpgrade

#### Adding an isolated PDB TDE Keystore Password Added to AutoUpgrade Keystore

In isolated mode, where a pluggable database (PDB) has its own keystore, PDBs are allowed to independently create and manage their own keystore. For isolated mode PDBs, start the AutoUpgrade Password Loader, and use the syntax `add ``Oracle_SID`` -pdb ``pdbname`, where `Oracle_SID` is the name of the CDB root, and `pdbname` is the name of the isolated PDB.

For example, where CDB root is `cdb19x` and the isolated PDB name is `iso`:

    TDE> add cdb19x -pdb iso
    Enter your secret/Password:
    Re-enter your secret/Password:

**Related Topics**

- [About Configuring United Mode](../asoag/managing-keystores-encryption-keys-in-united-mode.md)
- [About Configuring an External Keystore](../asoag/configuring-transparent-data-encryption.md)
- [Configuring Auto-Open Connections into External Key Managers](../asoag/managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### load_win_credential

The AutoUpgrade parameter `load_win_credential` uses PowerShell to create a credential object so that AutoUpgrade can be run without interruption during the upgrade.

#### Description

To provide passwords required for upgrade on Microsoft Windows platforms, you can use the `load_win_credential` parameter. This parameter must be used in conjunction with the `-config` parameter, and with a configuration file that specifies the local `wincredential` parameter. The parameter starts up a Microsoft Windows PowerShell credential request, where you can provide Administrator credentials to create a PowerShell credential object. By default, the Windows PowerShell Credential request is for the local machine. You provide the user name for the credential (the owner of the Oracle binaries) and that user password. Windows Powershell then generates a credential using the format database-name.xml, where database-name is the name of the database that you specified in your local configuration file SID entry. For example, `upg1.sid=sales1` in the configuration file with the `wincredential` entry `upg1.wincredential=C:\Users\oracle\cred` generates the powershell credential file `sales1.xml` in the path `sales1.wincredential=C:\Users\oracle\cred`

After AutoUpgrade no longer requires the passwords, these passwords are purged from memory. No log records are kept of the passwords.

**Note:**

If you do not provide a system identifier (SID) as an option to the `-load_win_credential` parameter, and if only one database is specified in the configuration file (config file), then AutoUpgrade uses the only SID in the configuration file. Specifying the SID is optional.

However, if two or more SIDs are specified in the config file, then you must specify the SID for each database, then AutoUpgrade is unable to identify for which SID it should use the credentials. The result is an error.

#### Usage Notes

When you run AutoUpgrade for the database upgrade, AutoUpgrade reads the credential from the path specified by the local `wincredential`, so that AutoUpgrade is able to create services automatically in the Target database without requiring an administrator to provide Administrator credentials manually during the upgrade.

Be aware that the account used in your connection can be restricted by a local security policy so that it either is not allowed to log on, or the login may be denied. If that is the case, then you see an error such as the following:.

    Start-Process : This command cannot be run due to the error:
    Logon failure: the user has not been granted the requested
    logon type at this computer.
    At line:1 char:1

To work around that error, work with your Microsoft Windows administrator to add the user account running AutoUpgrade to the local policy setting:

1.  Log on to the system (preferably as an administrator user).
2.  Go to Local Security Policy.
3.  Navigate to Security Settings, select Local Policies, and select User Rights Assignment.
4.  For the following policies, verify that either the group to which the user running AutoUpgrade belongs or the user account itself is added to the following lists:
    - Access this computer from Network
    - Allow log on locally
    - Allow log on through Remote Desktop Services

For details, see Microsoft Support: "Logon type has not been granted."

#### Example

In the following example, you complete these steps in order to automate calling the Administrator credentials during the upgrade:

1.  Create the configuration file, using the `wincredential` local parameter to specify the location for the Windows Powershell credential for the source database `db12201`:

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

2.  Run AutoUpgrade in Configuration mode, using the `load_win_credential` command-line parameter. If there s only one SID in your configuration file, then specifying the system identifier (`SID`) is optional, but not required. For example:

        C:\Users\oracle>java -jar autoupgrade.jar -config config.cfg -load_win_credential db12201
        AutoUpgrade 24.1.240306 launched with default internal options
        Processing config file ...

    **Note:**

    If the config file contains multiple SIDs, then you must specify the SID when you run AutoUpgrade. If you do not specify the SID when there are multiple SIDs in the configuration file, then the result is an error.

3.  A Microsoft Windows Powershell Credential prompt opens. Provide the credentials for the Oracle Database binary owner. PowerShell then generates the credential object (in this example, `db12201.xml`), and places it in the path that you specified with the `wincredential` parameter.

4.  During the upgrade, run AutoUpgrade using the configuration file that specifies the credential object path. For example:

        C:\Users\oracle>java -jar autoupgrade.jar -config config.cfg -mode deploy

    AutoUpgrade processes the upgrade without prompting you for credentials.

Suppose your configuration file contains two SIDs, `db12201` and `db19x`:

    upg1.sid=db12201
    upg1.source_home=C:\databases\ee\product\12.2\dbhome_1
    upg1.target_home=C:\databases\ee\product\18x\dbhome_1
    upg1.wincredential=C:\Users\oracle\cred

    upg2.sid=db19x
    upg2.source_home=C:\databases\ee\product\18x\dbhome_1
    upg2.target_home=C:\databases\ee\product\19x
    upg2.wincredential=C:\Users\oracle\anothercred

In this case, running `java -jar autoupgrade.jar -config config.cfg -load_win_credential` without specifying the SID results in an error. When you run AutoUpgrade in Configuration mode to load credentials, you must provide the SID so that AutoUpgrade can load the credentials for that SID. For example, to load the correct credentials for `db12201`:

    java -jar autoupgrade.jar -config config2.cfg -load_win_credential db12201

To load credentials for `db19x`, you conversely must specify the `db19x` SID:

    java -jar autoupgrade.jar -config config2.cfg -load_win_credential db19x

**Related Topics**

- [Microsoft Support: Logon type has not been granted](https://support.microsoft.com/en-gb/topic/logon-type-has-not-been-granted-b8df6776-d23a-47bf-a8c2-f3e27a71ae7a)

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### mode

The AutoUpgrade parameter `mode` value sets the mode from which AutoUpgrade runs.

| Property       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Syntax         | `-mode = [analyze|create_home|download|fixups|deploy|upgrade|postfixups]`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Default value  | None. Choose one of the following options:<br>• `analyze` : Runs upgrade readiness checks in the source Oracle home.<br>• `create_home` : Used with AutoUpgrade patching only. When set, a new target Oracle home is created as part of the patching operation without requiring either a source database or source ORACLE_HOME.<br>• `download` : Used with AutoUpgrade patching only. When set, AutoUpgrade downloads patches specified in the configuration file, and then exits.<br>• `fixups` : Runs the upgrade readiness checks and preupgrade fixups, but does not perform the upgrade.<br>• `deploy` : Performs the upgrade of the databases from start to finish.<br>• `upgrade` : Performs the database upgrade and postupgrade actions. Databases in the target Oracle homes must be up and running before you start this mode. Note: If autoupgrade.jar is run with the -patch parameter, then the command cannot include the `-mode upgrade` option.<br>• `postfixups` Runs postfixups of databases in the target Oracle home. |

#### Examples

    java -jar autoupgrade.jar -config config.cfg -mode analyze
    java -jar autoupgrade.jar -config config.cfg -mode deploy
    java -jar autoupgrade.jar -preupgrade "target_version=21" -mode fixups


**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### noconsole

The AutoUpgrade parameter `noconsole` turns off the AutoUpgrade console, so that AutoUpgrade runs using only configuration file information.

| Property       | Description  |
|:---------------|:-------------|
| Parameter type | string       |
| Syntax         | `-noconsole` |

#### Description

When you use the `noconsole` option, AutoUpgrade runs using only the settings in the configuration file, without requiring console input. Use the `noconsole` option when you want to run AutoUpgrade as part of a batch flow, or in scripts, such as in cases where you want to analyze multiple databases. After the AutoUpgrade jobs are finished, you can review the output of the Analyze mode logs to see what is required to upgrade each of the databases included with your configuration script.

**Note:**

You can run only one AutoUpgrade instance at a time that is associated with a given configuration file.

#### Usage Notes

In this example, AutoUpgrade is run in Analyze mode, using the configuration file in `noconsole` mode.

    java -jar autoupgrade.jar -config autoupgrade.cfg -mode analyze -noconsole

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### Patch

The AutoUpgrade parameter `patch` is used to specify that AutoUpgrade is performing a patch operation, and not an upgrade operation.

| Property       | Description    |
|:---------------|:---------------|
| Parameter type | String         |
| Syntax         | `-patch `      |
| Default value  | Not applicable |

#### Description

The `patch` command-line parameter specifies that the autoupgrade.jar command starts an AutoUpgrade patching operation.

#### Usage Notes

This parameter is used only with AutoUpgrade patching. It cannot be used with the `-preupgrade` command-line option. All other command-line options can be used with the patch option.

The `-mode` operations analyze, fixup, deploy, download, and create_home are supported with the patch command-line parameter. The modes `download` and `create_home` are specifically for use with the patch parameter:

- `-mode download`: Specifies to download specified patches and then exit.
- `-mode create_home` Specifies to create the new target Oracle home without requiring either a source database or source ORACLE_HOME.

#### Example

In this example, the patch parameter is used with `-mode download` to automatically download the patches specified in the configuration file:

    java -jar autoupgrade.jar -patch -mode download

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### preupgrade

The AutoUpgrade parameter `preupgrade` runs database checks and preupgrade fixups that fix most issues before you start an upgrade, and postupgrade fixups that fix most issues after an upgrade is completed.

| Property       | Description                                                                                              |
|:---------------|:---------------------------------------------------------------------------------------------------------|
| Parameter type | string                                                                                                   |
| Syntax         | `-preupgrade preupgrade_options -mode`<br>`      [analyze|fixups|postfixups]`<br>`                     ` |
| Default value  | `analyze`                                                                                                |

#### Description

The -preupgrade clause of AutoUpgrade replaces the functions previously preformed by the manual Pre-Upgrade Information Tool (preupgrade.jar) in previous releases. The `-mode` clause takes one of three values:

- `analyze`: Check your system for readiness to upgrade.
- `fixups`: Perform fixups as needed on your source Oracle Database release in preparation for upgrade
- `postfixups`: Perform fixups on your target Oracle Database release after upgrade is completed.

If no value for `-mode` is specified, then by default the `-preupgrade` parameter defaults to `analyze` mode.

#### Usage Notes

Use the `preupgrade` clause only if you want to obtain the same features previously made available with the Pre-Upgrade Information Tool (`preupgrade.jar`). For most upgrade scenarios, you do not need to use this parameter.

The `-preupgrade` parameter requires `preupgrade_options`, which specifies a list of comma-delimited option-value pairs in the following format: `option1``=``value1``,``option2``=``value2``,…`

#### Arguments

- `target_version=``release-number`: Specifies the target Oracle Database release version, which is the release to which you want to upgrade.

  The value for this argument is required by the `analyze` and `fixups` modes. However, the target release can be derived from `target_home`. Accordingly, for `analyze` and `fixups` modes, either `target_version` or `target_home` must be specified. The value for `target_version` must be `12.2`, or a later release value.

- `target_home=[``target-path|env-variable``]`: Specifies the Oracle Database home location of the target release to which you want to upgrade, which can either be the Oracle home path, or an operating system path variable.

  This argument is mandatory if you select the `postfixups` mode. If you select the `postfixups` mode, and you do not specify a target home path, then the default value is specified by the Oracle home environment variable for the Oracle home set for the user running AutoUpgrade (`$ORACLE_HOME` on Linux and Unix systems, or `%ORACLE_HOME%` on Microsoft Windows systems).

- `oh=[``source-path|env-variable``]`: Specifies the Oracle Database home location of the source release from which you want to upgrade, which can either be the Oracle home path, or an operating system path variable.

  This argument is mandatory if you select the `analyze` or `fixups` mode. If you select either `analyze` or `fixups` modes, and you do not specify a source home path, then the default value is specified by the Oracle home environment variable for the Oracle home set for the user running AutoUpgrade (`$ORACLE_HOME` on Linux and Unix systems, `%ORACLE_HOME%` on Microsoft Windows systems).

- `sid=``system-identifier`: Specifies an Oracle system identifier for the source database that you want to upgrade. This argument is mandatory for `analyze` or `fixups` modes. If you select either the `analyze` or the `fixups` mode, and you do not specify a system identifier, then the default value is specified by the Oracle home environment variable for the Oracle home set for the user running AutoUpgrade (`$ORACLE_SID` on Linux and Unix systems, `%ORACLE_SID%` on Microsoft Windows systems).

- `dir=``path`: Directs the output to a specific directory. If you do not specify an output directory with the `dir` argument, then the output is directed to a folder called `autoupgrade` that is placed in the temporary directory on your system. Typically, that directory is in one of the following locations:
  - Linux or Unix: `/tmp`, or `/var/tmp`.
  - Microsoft Windows: `C:\WINNT\TEMP`

- `inclusion_list=``list`: Specifies a list of pluggable databases (PDBs) inside a container database (CDBs) that you want to include for processing. Provide a space-delimited list of PDBs that you want processed, in one of the following two formats, where `pdb1`, `pdb2`, and `pdb3` are PDBs that you want processed:

  - `pdb1 pdb2 pdb3`
  - `(pdb1 pdb2 pdb3)`

  If you do not specify a list of PDBs, then all PDBs in a CDB are processed.

- `exclusion_list=``list`: Specifies a list of pluggable databases (PDBs) inside a container database (CDBs) that you want to exclude for processing. Provide a space-delimited list of PDBs that you want processed, in one of the following two formats, where `pdb1`, `pdb2`, and `pdb3` are PDBs that you want processed:

  - `pdb1 pdb2 pdb3`
  - `(pdb1 pdb2 pdb3)`

  If you do not specify a list of PDBs, then all PDBs in a CDB are processed.

- `user=``username`: Specifies the Oracle Database user name that the AutoUpgrade utility uses to connect to Oracle Database If the user is specified, then AutoUpgrade prompts for the user name password input on the command line. If no user name is specified, then AutoUpgrade uses operating system authentication for the Oracle Database connection.

#### Modes

- `analyze` (Default value): Runs Autoupgrade in Analyze mode, with all of the preupgrade checks that apply for the target release argument that you specify. If you do not specify a mode, then AutoUpgrade defaults to `analyze`.

- `fixups`: Runs preupgrade fixups (when available) for all issues reported by AutoUpgrade Analyze preupgrade checks on the source database that must be fixed before upgrade. All checks are run.

  Fixup results are reported in the file `upgrade.xml`. That file is placed in the path `log_dir``/``db_name``/``jobnumber``/prefixups/prefixups.xml`, where `log_dir` is the log directory that you specify using the `dir` argument, `db_name` is the name of the source database, and `jobnumber` is the AutoUpgrade job number.

- `postfixups`: Runs postupgrade fixups (when available) for all issues reported by AutoUpgrade Analyze preupgrade checks on the upgraded database that you must fix after the upgrade is completed.

  Postfixup results are reported in the file `postfixups.xml`. That file is placed in the path `log_dir``/``db_name``/``jobnumber``/postfixups`, where `log_dir` is the log directory that you specify using the `dir` argument, `db_name` is the name of the source database, and `jobnumber` is the AutoUpgrade job number.

#### Examples

Running AutoUpgrade with the preupgrade clause using `analyze` mode, and specifying that the target release is Oracle Database 19c.

    java -jar autoupgrade.jar -preupgrade "target_version=19" -mode analyze

Running AutoUpgrade with the preupgrade clause using `fixups` mode, and specifying that the target release is Oracle Database 19c.

    java -jar autoupgrade.jar -preupgrade "target_version=19" -mode fixups

Running AutoUpgrade with the preupgrade clause using `postfixups` mode, and specifying that the target Oracle home is in the path `C:\app\oracle\product\19.0.0\dbhome_1`.

    java -jar autoupgrade.jar -preupgrade "target_home=C:\app\oracle\product\19.0.0\dbhome_1" -mode postfixups

Running AutoUpgrade with the preupgrade clause without specifying the mode, and specifying that the target release is Oracle Database 19c. In this case, the mode used is the default mode, `analyze`.

    java -jar autoupgrade.jar -preupgrade "target_version=19"

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### settings

The AutoUpgrade parameter `settings` identifies the configuration file that you use to provide custom runtime configuration of the AutoUpgrade utility.

| Property       | Description                               |
|:---------------|:------------------------------------------|
| Parameter type | String                                    |
| Syntax         | `-settings ``my-custom-advanced-settings` |
| Default value  | Not applicable                            |

#### Description

The `settings` parameter has the required argument of the name and path to the settings configuration file, which you have modified with custom settings. The `settings` parameter cannot be used alone, but rather as a configuration input file that modifies the way that AutoUpgrade runs a processing mode.

#### Usage Notes

This parameter is an advanced parameter. For most upgrade scenarios, you should not need to modify any internal AutoUpgrade parameter settings.

#### Example

In this example, settings specifies a settings input file called my_custom_advanced_settings.cfg.

    java -jar autoupgrade.jar -settings my_custom_advanced_settings.cfg -config config.cfg -mode deploy

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### version

The AutoUpgrade parameter `version` prints to the terminal screen the current build of the `autoupgrade.jar` file.

| Property       | Description     |
|:---------------|:----------------|
| Parameter type | string          |
| Syntax         | -version        |
| Default value  | Not applicable. |

#### Description

Use this optional parameter to check which version of the autoupgrade.jar utility is on your server.

#### Usage Notes

Command Example:

    java -jar autoupgrade.jar -version

Output example:

    [oracle@example ~]$ java -jar autoupgrade.jar -version

    build.version 22.1.220304
    build.date 2022/03/04 13:29:34 -0500
    build.hash 29007da
    build.hash_date 2022/03/04 12:48:36 -0500
    build.supported_target_versions 12.2,18,19,21
    build.type production

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### restore

The AutoUpgrade parameter `restore` performs a system-level restoration of the AutoUpgrade jobs that you specify.

| Property       | Description                      |
|:---------------|:---------------------------------|
| Parameter type | string                           |
| Syntax         | `-restore -jobs ``job#``,``job#` |
| Default value  | Not applicable.                  |

#### Description

Use this optional parameter to specify a system-level restoration of the jobs you specify, using a comma-delimited list of job numbers. The databases in the upgrade jobs that you specify are flashed back to the Guarantee Restore Point (GRP). Before you run this command, the GRP must have been created by AutoUpgrade.

#### Examples

    java -jar autoupgrade.jar -config config.cfg -restore -jobs 111
    java -jar autoupgrade.jar -config config.cfg -restore -jobs 111,222 -console
    java -jar autoupgrade.jar -config config.cfg -restore -jobs 111,222 -noconsole

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### restore_on_fail

The AutoUpgrade parameter `restore_on_fail` automatically restores any job that failed during the deployment.

| Property       | Description        |
|:---------------|:-------------------|
| Parameter type | string             |
| Syntax         | `-restore_on_fail` |
| Default value  | Not applicable.    |

#### Description

Use this optional parameter to specify that AutoUpgrade restores any jobs that failed during the upgrade deployment.

#### Examples

    java -jar autoupgrade.jar -config config.cfg -mode deploy -restore_on_fail

**Parent topic:** AutoUpgrade Command-Line Parameters and Options

### zip

The AutoUpgrade parameter `zip` creates a zip file of log files required for filing an AutoUpgrade service request.

| Property       | Description                                                     |
|:---------------|:----------------------------------------------------------------|
| Parameter type | string                                                          |
| Syntax         | `-zip [-sid sid] [-d dir] [-zip_exclusion_list exclusion_list]` |
| Default value  | Not applicable.                                                 |

#### Description

Use this optional parameter to create a zip file that you can send to Oracle Support that contains the log files for jobs that are the object of your service request. Use the `-sid` clause to specify a comma-delimited list of system identifiers (SIDs) of databases whose log files you want to send. If no SID value is defined, then AutoUpgrade creates a zip file for all databases specified in the configuration file. Use the `-d `clause to specify a specific output directory. If no directory is specified, then the current directory from which the command is run is used for the zip file output. Use the `-zip_exclusion_list` clause to specify a double-comma-delimited regular string list that is used to exclude files that match any regular string from the zip file.

#### Usage Notes

**Note:**

When you use the `-zip` clause, you cannot use the `-mode` clause.

#### Examples

`java -jar autoupgrade.jar -config ``yourconfig``.cfg -zip `

`java -jar autoupgrade.jar -config ``yourconfig``.cfg -zip -sid sales1,sales2 -d /scratch/upgrd `

`java -jar autoupgrade.jar -config yourconfig.cfg -zip -zip_exclusion_list ".*/db11204/.*" `

`java -jar autoupgrade.jar -config yourconfig.cfg -zip -zip_exclusion_list "/home/oracle/autopatch/DB19X/100/goldimage/db_home_2023-09-21_09-18-13AM.zip,,/home/oracle/autopatch/DB19X/100/extract/35320081/.*" `

**Parent topic:** AutoUpgrade Command-Line Parameters and Options
