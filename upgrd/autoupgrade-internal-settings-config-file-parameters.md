## AutoUpgrade Internal Settings Configuration File

Internal configuration settings control how AutoUpgrade runs.

### Usage Notes

These configuration settings are provided for reference only. Typically, you should not use these parameters.

Table 3-3 Internal Settings Configuration File Parameters for AutoUpgrade

| Parameter                       | Default                 | Description                                                                                                                                                            |
|:--------------------------------|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `heartbeatHeartbeatSleep`       | 1                       | Number of minutes to wait between each job heartbeat.                                                                                                                  |
| `heartbeatHeartbeatRetries`     | 10                      | Number of times to retry after a failed job heartbeat.                                                                                                                 |
| `lsjNoConsoleTimer`             | 30                      | Runtime interval in seconds of the `lsj` command for `noconsole`. The interval should be between 7 and 1200 seconds.                                                   |
| `shutdownJobWaitTime`           | 10                      | Number of minutes to wait before a running job is terminated in the job queue during a scheduled upgrade.                                                              |
| `systemChecksAbort_timer`       | 60                      | Number of minutes to wait before the system checks job is automatically terminated.                                                                                    |
| `systemChecksOracleHomeReqSpac` | 6g                      | Minimum adequate disk space (in GB) system check. (`g` is required.).                                                                                                  |
| `systemChecksMinCpuIdlePct`     | 10                      | Warning alert threshold percentage to indicate that the remaining available percentage of CPU resources on the system can be inadequate to complete the upgrade.       |
| `systemChecksMinFreeMemPct`     | 5                       | Warning alert threshold percentage to indicate that the remaining available percentage of system random access memory (RAM) can be inadequate to complete the upgrade. |
| `systemChecksMinFreeSwapPct`    | 5                       | Warning alert threshold percentage to indicate that the remaining available percentage of system swap space memory can be inadequate to complete the upgrade.          |
| `dbPreCheckAbortTimer`          | 60                      | Number of minutes to wait before the database preupgrade checks job is automatically terminated.                                                                       |
| `dbUpgradeDurationTimer`        | 180                     | Number of minutes to wait before the database upgrade job starts additional monitoring of the upgrade progress.                                                        |
| `dbUpgradeWakeupTimer`          | 3                       | Number of minutes to wait before the database upgrade job restarts monitoring the upgrade.                                                                             |
| `dbUpgradeAbortTimer`           | 1440                    | Number of minutes to wait before the database upgrade is automatically terminated.                                                                                     |
| `dbUpgradeFatalErrors`          | ORA-00600,<br>ORA-07445 | Identifies which upgrade internal errors automatically cause a post-upgrade restore of the database back to the guarantee restore point. Entries are comma-delimited.  |
| `dbPostUpgradeAbortTimer`       | 60                      | Number of minutes to wait before the postupgrade job is automatically terminated.                                                                                      |
| `dbGrpAbortTimer`               | 3                       | Number of minutes to wait before the guarantee restore point job is automatically terminated.                                                                          |

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
