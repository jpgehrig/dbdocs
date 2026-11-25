## AutoUpgrade Log File Structure

The AutoUpgrade utility produces a log file structure that includes job status and configuration files.

### AutoUpgrade Log File Base Path

The AutoUpgrade log file path is set using the global parameter `autoupg_log_dir`. By default, the global parameter has the following definition:

    global.autoupg_log_dir=/database/jobmgr

AutoUpgrade configuration and status file paths are relative to the directory path that you establish with `global.autoupg_log_dir`.

### /cfgtoollogs/upgrade/auto

The automatic configuration tools log directory (`/cfgtoollogs/upgrade/auto`) contains three trace log files that provide specific information about each job that the AutoUpgrade job manager processes:

- `autoupgrade.log`: Provides detailed logs of the job that identify any problems that occur during job runs.
- `autoupgrade_usr.log`: Job information, which is formatted to enhance readability.
- `autoupgrade_err.log`: A report of any unexpected exceptions that occur when the job runs.

If problems occur when jobs start or stop, then you can use information in these log files to determine the cause of problems.

### /config_files

The `config_files` directory contains AutoUpgrade internal runtime configurations and global temporary files.

### /status

The `/status` directory contains JSON job status files. It contains two directories:

- `status.json`: This directory contains the final job status of all jobs completed in the JSON file format.
- `progress.json`: This directory contains the progress of all jobs currently running in the JSON file format.

Each module in the directories contains a status file for the operation that it performed. The module takes the following format, where the prefix `dbname` is the database name, `operation` is the upgrade operation that was performed, and the suffix `status` is the completion status of that operation:

    dbname_operation-name.status

The success or the failure of that operation is indicated by the suffix, which is either `.success`, indicating the successful performance of that operation, or `.failure`, indicating the failure of that operation. For example, the following module name indicates a successful run of the prechecks operation on the database `sales`:

    sales_prechecks.success

The operation module name can be one of the following:

- `preupgrade`: The preupgrade stage, in which custom scripts can be run.
- `prechecks`: The upgrade checks completed before starting the upgrade.
- `grp`: Guaranteed restore point (using Oracle Flashback technology).
- `prefixups`: The preupgrade fixups run before starting the upgrade.
- `drain`: The stage where existing jobs are completed or migrated before starting the upgrade.
- `dbupgrade`: The stage in which the upgrade takes place.
- `postchecks`: The stage in which postupgrade checks are run after the upgrade is completed.
- `postfixups`: The stage in which postupgrade fixups are run.
- `postupgrade`: The stage in which custom postupgrade scripts can be run.

### Individual Job and Database Log File Directories

Each job started by the AutoUpgrade dispatcher is given a directory with that job identifier prefix. Inside that job directory, each database in the job is given a log directory in the path `/database/logs/``sid`, where `sid` is the system identifier for the database. For example, where the job identified in the configuration file is `sales1`, and the database system identifier is `sales`, the log file for the database sales is in the following path:

    sales.log_dir=/database/logs/sales1

The log directory contain all the relevant log files for all the tasks performed for that database. By default, a directory identified by SID is created under the `/database/logs` directory. Each database job can have a separate log directory, if you choose to set up your configuration file that way.

`/####` ( Job Number)

Individual job runs are placed in subdirectories identified by the run number, in the format `/``####`, where `####` represents the job run number. For example: `0004`. Job run number directories contain the following log files:

- `autoupgrade_err.log`: Reports any unexpected exceptions that occur while the job runs.
- `autoupgrade``YYYYMMDD``.log`: AutoUpgrade trace log file. Provides detailed logs of the job that identify any problems that occur during job runs. The variable `YYYYMMDD` represents year, month, and day of the job.
- `autoupgrade_``YYYYMMDD``_user.log`: AutoUpgrade job status file, which is formatted to enhance readability. The variable `YYYYYYMMDD` represents year, month, and day of the job.

`/preupgrade`

The preupgrade directory (`/preupgrade`) contains the following files and log files:

- `prechecks_``databasename``.log`: Trace log file. This file provides detailed logs that can assist with identifying problems that occur during the preupgrade job stage. The variable `databasename` is the name of the database checked.
- `databasename``_preupgrade.html`: HTML report on the database status. The variable `databasename` is the name of the database checked.
- `databasename``_preupgrade.log`: Text report on the database status. The variable `databasename` is the name of the database checked.

`/dbupgrade`

The database upgrade directory (`/dbupgrade`) contains all log files associated with the database upgrade:

- `autoupgrade``YYYYMMDDHHMISC``dbname``.log`: Log files for the source database, identified by the date on which the upgrade was run, and by the database name, indicating parallelism. Format:
  - `YYYY`: Year
  - `MM`: Month
  - `DD`: Day
  - `HH`: Hour
  - `MI`: Minute
  - `SC`: Second
  - `dbname`: Database name, where `dbname` is the database name.

- `catupgrade``YYYYMMDDHHMISC``dbnameN``.log`: log files for the source database, identified by the date on which the upgrade was run.

  Format:

  - `YYYY`: Year
  - `MM`: Month
  - `DD`: Day
  - `HH`: Hour
  - `MI`: Minute
  - `SC`: Second
  - `dbnameN`: Database name, where `dbname` is the database name, and `N` indicates the parallelism: 0...3 for CDB ROOT, and Non-CDB databases, and 0...1 for PDBs.

`/temp`

Temporary AutoUpgrade files (`/temp`). This directory can contain files such as the `PFILE` used during an upgrade.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
