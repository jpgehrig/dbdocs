Use the `chactl query diagnosis` command to return problems and diagnosis, and suggested corrective actions associated with the problem for specific cluster nodes or Oracle Real Application Clusters (Oracle RAC) databases.

### Syntax

    chactl query diagnosis [-cluster|-db db_unique_name] [-start time -end time] [-htmlfile file_name][-help]

Specify date and time in the `YYYY-MM-DD HH24:MI:SS` format.

In the preceding syntax, you must consider the following points:

- If you do not provide any options, then the `chactl query diagnosis` command returns the current state of all monitored nodes and databases. The `chactl query diagnosis` command reports general state of the targets, for example, **ABNORMAL** by showing their diagnostic identifier, for example, `Storage Bandwidth Saturation`. This is a quick way to check for any **ABNORMAL** state in a database or cluster.

- If you provide a time option after the target name, then the `chactl query diagnosis` command returns the state of the specified target restricted to the conditions in the time interval specified. The compressed time series lists the identifiers of the causes for distinct incidents which occurred in the time interval, its start and end time.

- If an incident and cause recur in a specific time interval, then the problem is reported only once. The start time is the start time of the first occurrence of the incident and the end time is the end time of the last occurrence of the incident in the particular time interval.

- If you specify the `–db` option without a database name, then the `chactl query diagnosis` command displays diagnostic information for all databases. However, if a database name is specified, then the `chactl query diagnosis` command displays diagnostic information for all instances of the database that are being monitored.

- If you specify the `–cluster` option without a host name, then the `chactl query diagnosis` command displays diagnostic information for all hosts in that cluster.

- If you do not specify a time interval, then the `chactl query diagnosis` command displays only the current issues for all or the specified targets. The `chactl query diagnosis` command does not display the frequency statistics explicitly. However, you can count the number of normal and abnormal events that occurred in a target in the last 24 hours.

- If no incidents have occurred during the specified time interval, then the `chactl query diagnosis` command returns a text message, for example, `Database/host is operating NORMALLY`, or `no incidents were found`.

- If the state of a target is **NORMAL**, the command does not report it. The `chactl query diagnosis` command reports only the targets with **ABNORMAL** state for the specified time interval.

Output parameters:

- Incident start Time

- Incident end time (only for the default database and/or host, non-verbose output)

- Target (for example, database, host)

- Problem

  Description: Detailed description of the problem

  Cause: Root cause of the problem and contributing factors

- Action: an action that corrects the abnormal state covered in the diagnosis

Reporting Format: The diagnostic information is displayed in a time compressed or time series order, grouped by components.

### Examples

To display diagnostic information of a database for a specific time interval:

    $ chactl query diagnosis -db oltpacdb -start "2016-02-01 02:52:50.0" -end "2016-02-01 03:19:15.0"
    2016-02-01 01:47:10.0  Database oltpacdb  DB Control File IO Performance (oltpacdb_1) [detected]
    2016-02-01 01:47:10.0  Database oltpacdb  DB Control File IO Performance (oltpacdb_2) [detected]
    2016-02-01 02:52:15.0  Database oltpacdb  DB CPU Utilization (oltpacdb_2) [detected]
    2016-02-01 02:52:50.0  Database oltpacdb  DB CPU Utilization (oltpacdb_1) [detected]
    2016-02-01 02:59:35.0  Database oltpacdb  DB Log File Switch (oltpacdb_1) [detected]
    2016-02-01 02:59:45.0  Database oltpacdb  DB Log File Switch (oltpacdb_2) [detected]

    Problem: DB Control File IO Performance
    Description: CHA has detected that reads or writes to the control files are slower than expected.
    Cause: The Cluster Health Advisor (CHA) detected that reads or writes to the control files were slow
    because of an increase in disk IO.
    The slow control file reads and writes may have an impact on checkpoint and Log Writer (LGWR) performance.
    Action: Separate the control files from other database files and move them to faster disks or Solid State Devices.

    Problem: DB CPU Utilization
    Description: CHA detected larger than expected CPU utilization for this database.
    Cause: The Cluster Health Advisor (CHA) detected an increase in database CPU utilization
    because of an increase in the database workload.
    Action: Identify the CPU intensive queries by using the Automatic Diagnostic and Defect Manager (ADDM)
    and follow the recommendations given there. Limit the number of CPU intensive queries
    or relocate sessions to less busymachines. Add CPUs if the CPU capacity is insufficent to support the load
    without a performance degradation or effects on other databases.

    Problem: DB Log File Switch
    Description: CHA detected that database sessions are waiting longer than expected for log switch completions.
    Cause: The Cluster Health Advisor (CHA) detected high contention during log switches
    because the redo log files were small and the redo logs switched frequently.
    Action: Increase the size of the redo logs.

### Error Message

Message: `Target`` is operating normally`

Description: No incidents are found on the target.

Message: `No data was found for active ``Target`

Description: No data was found, but the target was operating or active at the time of the query.

Message: `Target is not active or was not being monitored.`

Description: No data was found because the target was not monitored at the time of the query.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
