This section enables you to manage Oracle Database and Oracle Grid Infrastructure diagnostic data and disk usage snapshots.

- Managing Automatic Diagnostic Repository Log and Trace Files
  Use the `managelogs` command to manage Automatic Diagnostic Repository log and trace files.
- Managing Disk Usage Snapshots
  Use `tfactl` commands to manage Oracle Trace File Analyzer disk usage snapshots.
- Purging Oracle Database and Oracle Grid Infrastructure Logs
  Use these `tfactl` commands to manage log file purge policy for Oracle Database and Oracle Grid Infrastructure logs.

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)

### 20.1 Managing Automatic Diagnostic Repository Log and Trace Files

Use the `managelogs` command to manage Automatic Diagnostic Repository log and trace files.

The `-purge` command option removes files managed by Automatic Diagnostic Repository. This command clears files from “`ALERT`”, "`INCIDENT`", "`TRACE`", "`CDUMP`", "`HM`", "`UTSCDMP`", "`LOG`" under diagnostic destinations. The `-purge` command also provides details about the change in the file system space.

If the diagnostic destinations contain large numbers of files, then the command runs for a while. Check the removal of files in progress from the corresponding directories.

To remove files, you must have operating system privileges over the corresponding diagnostic destinations.

#### To manage Automatic Diagnostic Repository log and trace files:

1.  To limit purge, or show operations to only files older than a specific time:
        $ tfactl managelogs -older nm|h|d Files from past 'n' [d]ays or 'n' [h]ours or 'n' [m]inutes

    For example:
        $ tfactl managelogs -purge -older 30d -dryrun

        $ tfactl managelogs -purge -older 30d
2.  To get an estimate of how many files are removed and how much space is freed, use the `–dryrun` option:
    For example:
        $ tfactl managelogs -purge -older 30d -dryrun
3.  To remove files and clean disk space:
    For example:
        $ tfactl managelogs -purge -older 30d

        $ tfactl managelogs -purge -older 30d –gi

        $ tfactl managelogs -purge -older 30d -database
4.  To view the space usage of individual diagnostic destinations:
    For example:
        $ tfactl managelogs -show usage

        $ tfactl managelogs -show usage –gi

        $ tfactl managelogs -show usage -database

**Related Topics**

- [tfactl managelogs](running-diagnostic-collection-commands.md)

**Parent topic:** Managing Oracle Database and Oracle Grid Infrastructure Diagnostic Data

### 20.2 Managing Disk Usage Snapshots

Use `tfactl` commands to manage Oracle Trace File Analyzer disk usage snapshots.

Oracle Trace File Analyzer automatically monitors disk usage, records snapshots, and stores the snapshots under `tfa_install_dir``/tfa/repository/suptools/node/managelogs/usage_snapshot/`

By default, the time interval between snapshots is 60 minutes.

#### To manage disk usage snapshots:

1.  To change the default time interval for snapshots:
        $ tfactl set diskUsageMonInterval=minutes

    where `minutes` is the number of minutes between snapshots.
2.  To turn the disk usage monitor on or off:
        $ tfactl set diskUsageMon=ON|OFF

**Parent topic:** Managing Oracle Database and Oracle Grid Infrastructure Diagnostic Data

### 20.3 Purging Oracle Database and Oracle Grid Infrastructure Logs

Use these `tfactl` commands to manage log file purge policy for Oracle Database and Oracle Grid Infrastructure logs.

Automatic purging is enabled by default on a Domain Service Cluster (DSC), and disabled by default elsewhere. When automatic purging is enabled, every 60 minutes, Oracle Trace File Analyzer automatically purges logs that are older than 30 days.

#### To purge Oracle Trace File Analyzer logs automatically:

1.  To turn on or off automatic purging:
        $ tfactl set manageLogsAutoPurge=ON|OFF
2.  To adjust the age of logs to purge:
        $ tfactl set manageLogsAutoPurgePolicyAge=nd|h
3.  To adjust the frequency of purging:
        $ tfactl set manageLogsAutoPurgeInterval=minutes

**Parent topic:** Managing Oracle Database and Oracle Grid Infrastructure Diagnostic Data
