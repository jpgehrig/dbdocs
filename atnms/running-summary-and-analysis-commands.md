Use these commands to view the summary of deployment and status of Oracle Trace File Analyzer, and changes and events detected by Oracle Trace File Analyzer.

- tfactl analyze
  Use the `tfactl analyze` command to obtain analysis of your system by parsing the database, Oracle ASM, and Oracle Grid Infrastructure alert logs, system message logs, OSWatcher Top, and OSWatcher Slabinfo files.
- tfactl changes
  Use the `tfactl changes` command to view the changes detected by Oracle Trace File Analyzer.
- tfactl events
  Use the `tfactl events` command to view the events detected by Oracle Trace File Analyzer.
- tfactl isa
  Use the `tfactl isa`  command to view the Infrastructure Service Automation (ISA) score.
- tfactl run
  Use the `tfactl run`  command to run the requested action (can be inventory or scan or any support tool).
- tfactl search
  Use the `tfactl search` command to search all metadata stored in the Oracle Trace File Analyzer index.
- tfactl summary
  Use the `tfactl summary` command to view the summary of Oracle Trace File Analyzer deployment.
- tfactl toolstatus
  Use the `tfactl toolstatus`  command to view the status of Oracle Trace File Analyzer Support Tools across all nodes.

**Parent topic:** [Oracle Trace File Analyzer Installer, Command-Line and Shell Options](tfa-command-reference.md)

### E.3.1 tfactl analyze

Use the `tfactl analyze` command to obtain analysis of your system by parsing the database, Oracle ASM, and Oracle Grid Infrastructure alert logs, system message logs, OSWatcher Top, and OSWatcher Slabinfo files.

Filter the output of the command by component, error type, and time.

With the `tfactl analyze` command, you can choose from the following types of log file analysis:

- Show the most common messages within the logs: This analysis provides a quick indication of where larger issues are occurring. Oracle Trace File Analyzer takes important messages out of the alert logs and strips the extraneous information from the log messages, organizes the most commonly occurring messages, and displays them in the order from most common to least common. By default, Oracle Trace File Analyzer analyzes error messages, but you can specify a particular type of message for analysis.

- Search for text within log messages: This is similar to using the `grep` utility to search, only faster because Oracle Trace File Analyzer checks the time of each message and only shows those matching the last x number of minutes or any interval of time.

- Analyze the Oracle OSWatcher log statistics: Oracle Trace File Analyzer reads the various statistics available in the `OSWatcher` log files and provides detailed analysis showing first, highest, lowest, average, and the last three readings of each statistic. Choose any interval down to a specific minute or second. Oracle Trace File Analyzer optionally provides the original data from the `OSWatcher` logs for each value reported on (data point).

#### Syntax

    tfactl analyze [-search "pattern"]
    [-comp db|asm|crs|acfs|os|osw|oswslabinfo|oratop|all]
    [-type error|warning|generic]
    [-last n[h|d]]
    [-from "MMM/DD/YYYY HH24:MI:SS"]
    [-to "MMM/DD/YYYY HH24:MI:SS"]
    [-for "MMM/DD/YYYY HH24:MI:SS"]
    [-node all|local|n1,n2,...]
    [-verbose]
    [-o file]
    [-examples]

#### Parameters

Table E-12 tfactl analyze Command Parameters

| Parameter                                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:--------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-search "``pattern``"`                                 | Searches for a pattern enclosed in double quotation marks ("") in system and alert logs within a specified time range. This parameter supports both case-sensitive and case-insensitive search in alert and system message files across the cluster within the specified filters. Default is case insensitive.<br>If you do not specify the `-search` parameter, then Oracle Trace File Analyzer provides a summary of messages within specified filters from alert and system log messages across the cluster.<br>Oracle Trace File Analyzer displays message counts grouped by type (`error`, `warning`, and `generic`) and shows unique messages in a table organized by message type selected for analysis. The `generic` message type is assigned to all messages which are not either an `error` or `warning` message type. |
| `[-comp db|asm|crs|acfs|os|osw|oswslabinfo|oratop|all]` | Select which components you want Oracle Trace File Analyzer to analyze. Default is `all`.<br>• `db`: Database alert logs<br>• `asm`: Oracle ASM alert logs<br>• `crs`: Oracle Grid Infrastructure alert logs<br>• `acfs`: Oracle ACFS alert logs<br>• `os`: System message files<br>• `osw`: OSW Top output<br>• `oswlabinfo`: OSW Slabinfo output<br>When `OSWatcher` data is available, `OSW` and `OSWSLABINFO` components provide summary views of OSWatcher data.                                                                                                                                                                                                                                                                                                                                                             |
| `-type error | warning | generic`                       | Select what type of messages Oracle Trace File Analyzer analyzes. Default is `error`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `[-last ``n``[``h``|``d``]]`                            | Specify an amount of time, in hours or days, before current time that you want Oracle Trace File Analyzer to analyze.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-from | -to | -for "MMM/DD/YYYY HH24:MI:SS"`           | Specify a time interval, using the `-from` and `-to` parameters together, or a specific time using the `-for` parameter, that you want Oracle Trace File Analyzer to analyze.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `[-node all|local|``n1``, ``n2``,...]`                  | Specify a comma-separated list of host names. Use `-local` to analyze files on the local node. Default is all.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `–verbose`                                              | Displays verbose output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `–o ``file`                                             | Specify a file where Oracle Trace File Analyzer writes the output instead of displaying on the screen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `[-examples]`                                           | Specify this parameter to view `analyze` usage examples.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

#### -type Parameter Arguments

The `tfactl analyze` command classifies all the messages into different categories when you specify the `-type` parameter. The analysis component provides count of messages by the message type you configure and lists all unique messages grouped by count within specified filters. The message type patterns for each argument are listed in the following table.

Table E-13 tfactl analyze -type Parameter Arguments

| Argument  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `error`   | Error message patterns for database and Oracle ASM alert logs:<br>`.*ORA-00600:.*`<br>`.*ORA-07445:.*`<br>`.*IPC Send timeout detected. Sender: ospid.*`<br>`.*Direct NFS: channel id .* path .* to filer .* PING timeout.*`<br>`.*Direct NFS: channel id .* path .* to filer .* is DOWN.*`<br>`.*ospid: .* has not called a wait for .* secs.*`<br>`.*IPC Send timeout to .* inc .* for msg type .* from opid.*`<br>`.*IPC Send timeout: Terminating pid.*`<br>`.*Receiver: inst .* binc .* ospid.*`<br>`.* terminating instance due to error.*`<br>`.*: terminating the instance due to error.*`<br>`.*Global Enqueue Services Deadlock detected`<br>Error message patterns for Oracle Grid Infrastructure alert logs:<br>`.*CRS-8011:.*,.*CRS-8013:.*,.*CRS-1607:.*,.*CRS-1615:.*,`<br>`.*CRS-1714:.*,.*CRS-1656:.*,.*PRVF-5305:.*,.*CRS-1601:.*,`<br>`.*CRS-1610:.*,.*PANIC. CRSD exiting:.*,.*Fatal Error from AGFW Proxy:.*` |
| `warning` | Warning message patterns for database and Oracle ASM alert logs:<br>`NOTE: process .* initiating offline of disk .*`<br>`.*WARNING: cache read a corrupted block group.*`<br>`.*NOTE: a corrupted block from group FRA was dumped to`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `generic` | Any messages that do not match any of the preceding patterns.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### oratop options

The options available when using `-comp oratop`:

    -database dbname oratop options logon

Table E-14 tfactl analyze -comp oratop options

| Argument             | Description                                                                                                                                                                                    |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``dbname` | Specify the name of the Oracle Database to run `oratop`.                                                                                                                                       |
| `logon`              | Default is `/ as sysdba`.<br>Specify a different user using,<br>`{username[/password][@connect_identifier] | / } [AS {SYSDBA|SYSOPER}]`<br>Connect Identifier:<br>`host[:port]/[service_name]` |

Table E-15 oratop options

| Argument | Description                                                                  |
|:---------|:-----------------------------------------------------------------------------|
| `-d`     | Real-time (RT) wait events (section 3. Default is Cumulative..               |
| `-k`     | FILE#:BLOCK#, section 4 lt is (EVENT/LATCH).                                 |
| `-m`     | Specify `MODULE`/`ACTION` (section 4). Default is `USERNAME`/`PROGRAM`.      |
| `-s`     | Specify the SQL mode (section 4). Default is process mode.                   |
| `-c`     | Specify the Oracle Database service mode. Default is connect string.         |
| `-f`     | Specify the detailed format (132 columns). Default is standard (80 columns). |
| `-b`     | Specify the batch mode. Default is text-based user interface.                |
| `-n`     | Specify the maximum number of iterations.                                    |
| `-i`     | Specify the interval delay in seconds. Default is 5 seconds.                 |

#### Examples

The following command examples demonstrate how to use Oracle Trace File Analyzer to search collected data:

- `$ tfactl analyze -search "error" -last 2d`

  Oracle Trace File Analyzer searches alert and system log files from the past two days for messages that contain the case-insensitive string "error".

- `$ tfactl analyze -comp os -for "Jul/01/2016 11" -search "."`

  Oracle Trace File Analyzer displays all system log messages for July 1, 2016 at 11 am.

- `$ tfactl analyze -search "/ORA-/c" -comp db -last 2d`

  Oracle Trace File Analyzer searches database alert logs for the case-sensitive string "ORA-" from the past two days.

The following command examples demonstrate how to use Oracle Trace File Analyzer to analyze collected data:

- `$ tfactl analyze -last 5h`

  Oracle Trace File Analyzer displays a summary of events collected from all alert logs and system messages from the past five hours.

- `$ tfactl analyze -comp os -last 1d`

  Oracle Trace File Analyzer displays a summary of events from system messages from the past day.

- `$ tfactl analyze -last 1h -type generic`

  Oracle Trace File Analyzer analyzes all generic messages from the last hour.

The following command examples demonstrate how to use Oracle Trace File Analyzer to analyze `OSWatcher` Top and Slabinfo:

- `$ tfactl analyze -comp osw -last 6h`

  Oracle Trace File Analyzer displays `OSWatcher` Top summary for the past six hours.

- `$ tfactl analyze -comp oswslabinfo -from "2016-07-01" -to "2016-07-03"`

  Oracle Trace File Analyzer displays `OSWatcher` Slabinfo summary for specified time period.

**Parent topic:** Running Summary and Analysis Commands

### E.3.2 tfactl changes

Use the `tfactl changes` command to view the changes detected by Oracle Trace File Analyzer.

#### Syntax

    tfactl changes
    [-from time -to time | -for time | last time_length]

#### Parameters

| Option                     | Description                                                                                                                                                                                                                                                                         |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `from ``time`` -to ``time` | Specify the `-from` and `-to` parameters (you must use these two parameters together) to view changes that occurred during a specific time interval.<br>Supported time formats:<br>`"Mon/dd/yyyy hh:mm:ss"`<br>`"yyyy-mm-dd hh:mm:ss"`<br>`"yyyy-mm-ddThh:mm:ss"`<br>`"yyyy-mm-dd"` |
| `for ``time`               | Specify the `-for` parameter to view the changes that occurred at the time given.<br>Supported time formats:<br>`"Mon/dd/yyyy"`<br>`"yyyy-mm-dd"`                                                                                                                                   |
| `-last ``n``h``|``d`       | Specify the `-last` parameter to view changes for the past specific number of hours (h), or days (d).                                                                                                                                                                               |

#### Example

    $ tfactl changes

    Output from host : myserver69
    ------------------------------

    Output from host : myserver70
    ------------------------------
    Jul/26/2016 10:20:35 : Parameter 'sunrpc.transports' value changed : tcp 1048576 => udp 32768
    Jul/26/2016 10:20:35 : Parameter 'sunrpc.transports' value changed : tcp 1048576 => tcp-bc 1048576

    Output from host : myserver71
    ------------------------------
    Jul/26/2016 10:21:06 : Parameter 'sunrpc.transports' value changed : tcp 1048576 => udp 32768
    Jul/26/2016 10:21:06 : Parameter 'sunrpc.transports' value changed : tcp 1048576 => tcp-bc 1048576
    -bash-4.1# tfactl analyze
    INFO: analyzing all (Alert and Unix System Logs) logs for the last 60 minutes...  Please wait...
    INFO: analyzing host: myserver69

                           Report title: Analysis of Alert,System Logs
                      Report date range: last ~1 hour(s)
             Report (default) time zone: UTC - Coordinated Universal Time
                    Analysis started at: 26-Jul-2016 10:36:03 AM UTC
                  Elapsed analysis time: 1 second(s).
                     Configuration file: /scratch/app/11.2.0.4/grid/tfa/myserver69/tfa_home/ext/tnt/conf/tnt.prop
                    Configuration group: all
                    Total message count:         15,261, from 20-Nov-2015 02:06:21 AM UTC to 26-Jul-2016 10:10:58 AM UTC
      Messages matching last ~1 hour(s):              1, from 26-Jul-2016 10:10:58 AM UTC to 26-Jul-2016 10:10:58 AM UTC
            last ~1 hour(s) error count:              0
    last ~1 hour(s) ignored error count:              0
     last ~1 hour(s) unique error count:              0

    Message types for last ~1 hour(s)
       Occurrences percent  server name          type
       ----------- -------  -------------------- -----
                 1  100.0%  myserver69           generic
       ----------- -------
                 1  100.0%

    Unique error messages for last ~1 hour(s)
       Occurrences percent  server name          error
       ----------- -------  -------------------- -----
       ----------- -------
                 0  100.0%

**Parent topic:** Running Summary and Analysis Commands

### E.3.3 tfactl events

Use the `tfactl events` command to view the events detected by Oracle Trace File Analyzer.

#### Syntax

    tfactl events
    [-search keyword | -component ASM|CRS | -database db_name | -instance db_instance_name | -source filename | -from time -to time | -json | -fields all|fields_list]

#### Parameters

| Option                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `component [ASM|CRS]`                                                 | Searches all ASM or CRS events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `database ``db_name`                                                  | Specify the name of an Oracle Database to search all events from that Oracle Database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `instance ``db_instance_name`                                         | Specify the name of an Oracle Database instance to search all events from that Oracle Database instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `source ``filename`                                                   | Specify the source file name to search all events from that alert file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `json`                                                                | Displays event information in JSON format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-last ``n``h``|``d`` | -from ``time`` -to ``time`` | -for ``time``]` | • Specify the `-last` parameter to view events for the past specific number of hours (h) or days (d).<br>• Specify the `-from` and `-to` parameters (you must use these two parameters together) to view events that occurred during a specific time interval.<br>• Supported time formats:<br>• `"Mon/dd/yyyy hh:mm:ss"`<br>• `"yyyy-mm-dd hh:mm:ss"`<br>• `"yyyy-mm-ddThh:mm:ss"`<br>• `"yyyy-mm-dd"`<br>• Specify the `-for` parameter to view events for the time given.<br>• Supported time formats:<br>• `"Mon/dd/yyyy"`<br>• `"yyyy-mm-dd"`<br>**Note:**<br>If you specify both date and time, then you must enclose both the values in double quotation marks (""). If you specify only the date or the time, then you do not have to enclose the single value in quotation marks. |
| `fields all|``fields_list`                                            | When provided with the `-json` option, the command returns only the requested fields                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

#### Example

    $ tfactl events
    Output from host : myserver69
    ------------------------------
    Jul/25/2016 06:25:33 :
               [crs.myserver69] : [cssd(7513)]CRS-1603:CSSD on node myserver69 shutdown by user.
    Jul/25/2016 06:32:41 :
               [crs.myserver69] : [cssd(5794)]CRS-1601:CSSD Reconfiguration complete.
    Active nodes are myserver69 myserver70 myserver71 .
    Jul/25/2016 06:47:37 :
               [crs.myserver69] : [/scratch/app/11.2.0.4/grid/bin/scriptagent.bin(16233)]
    CRS-5818:Aborted command 'start' for resource 'ora.oc4j'. Details at (:CRSAGF00113:)
    {1:32892:193} in /scratch/app/11.2.0.4/grid/log/myserver69/agent/crsd/scriptagent_oragrid/scriptagent_oragrid.log.
    Jul/25/2016 06:24:43 :
               [db.apxcmupg.apxcmupg_1] : Instance terminated by USER, pid = 21581
    Jul/25/2016 06:24:43 :
               [db.rdb11204.rdb112041] : Instance terminated by USER, pid = 18683
    Jul/25/2016 06:24:44 :
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "FRA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "FRA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "FRA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "FRA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "FRA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "DATA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "DATA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "DATA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "DATA" does not exist or is not mounted
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15001: diskgroup "DATA" does not exist or is not mounted
    Jul/25/2016 06:24:53 :
               [db.+ASM1] : ORA-15032: not all alterations performed
               [db.+ASM1] : ORA-15027: active use of diskgroup "VDATA" precludes its dismount
    Jul/25/2016 06:25:22 :
               [db.+ASM1] : Shutting down instance (immediate)
               [db.+ASM1] : Shutting down instance: further logons disabled

    Summary :
    =========
    INFO   : 2
    ERROR   : 26
    WARNING   : 1

**Parent topic:** Running Summary and Analysis Commands

### E.3.4 tfactl isa

Use the `tfactl isa`  command to view the Infrastructure Service Automation (ISA) score.

#### Syntax

    tfactl isa
    [-availability]
    [-all]
    [-node all|local|n1,n2,...]

#### Parameters

Table E-16 tfactl run Command Parameters

| Parameter      | Description                                   |
|:---------------|:----------------------------------------------|
| `availability` | Includes the Availability Score.              |
| `all`          | Displays all the details.                     |
| `node`         | Specify a comma-separated list of host names. |

**Parent topic:** Running Summary and Analysis Commands

### E.3.5 tfactl run

Use the `tfactl run`  command to run the requested action (can be inventory or scan or any support tool).

#### Syntax

    tfactl run [inventory | scan | tool]

#### Parameters

Table E-17 tfactl run Command Parameters

| Parameter   | Description                              |
|:------------|:-----------------------------------------|
| `inventory` | Inventory of all trace file directories. |
| `scan`      | Runs a one off scan.                     |
| `tool`      | Runs the desired analysis tool.          |

#### Analysis Tools

Table E-18 tfactl run Analysis Tools Parameters

| Parameter      | Description                                                             |
|:---------------|:------------------------------------------------------------------------|
| `orachk`       | Runs `Oracle ORAchk`.                                                   |
| `oratop`       | Runs `oratop`.                                                          |
| `oswbb`        | Runs `OSWatcher Analyzer`.                                              |
| `prw`          | Runs `Procwatcher`.                                                     |
| `alertsummary` | Prints summary of important events in Oracle Database / ASM alert logs. |
| `calog`        | Prints Oracle Clusterware activity logs.                                |
| `dbglevel`     | Sets CRS log / trace levels using profiles.                             |
| `grep`         | `grep` for input string in logs.                                        |
| `history`      | Lists commands run in current Oracle Trace File Analyzer shell session. |
| `ls`           | Searches files in Oracle Trace File Analyzer.                           |
| `managelogs`   | Purge slogs.                                                            |
| `menu`         | Oracle Trace File Analyzer Collector menu system.                       |
| `param`        | Prints parameter value.                                                 |
| `ps`           | Finds a process.                                                        |
| `pstack`       | Runs `pstack`  on a process.                                            |
| `summary`      | Prints system summary.                                                  |
| `tail`         | Tails log files.                                                        |
| `triage`       | Summarize `OSWatcher` / `ExaWatcher` data.                              |
| `vi`           | Searches and opens files in the `vi`  editor.                           |

#### Profiling Tools

Table E-19 tfactl run Profiling Tools Parameters

| Parameter  | Description                                   |
|:-----------|:----------------------------------------------|
| `dbglevel` | Sets CRS log and trace levels using profiles. |

**Parent topic:** Running Summary and Analysis Commands

### E.3.6 tfactl search

Use the `tfactl search` command to search all metadata stored in the Oracle Trace File Analyzer index.

#### Syntax

    tfactl search
    [-json json_string | -fields all|fields_list | -showdatatypes | -showfields datatype]

#### Parameters

Table E-20 tfactl search Command Parameters

| Parameter       | Description                                             |
|:----------------|:--------------------------------------------------------|
| `json`          | JSON string containing the search criteria.             |
| `fields`        | Returns the JSON output with only the requested fields. |
| `showdatatypes` | Displays the list of all available datatypes.           |
| `showfields`    | Displays the list of fields available in a datatype.    |

**Parent topic:** Running Summary and Analysis Commands

### E.3.7 tfactl summary

Use the `tfactl summary` command to view the summary of Oracle Trace File Analyzer deployment.

#### Syntax

    tfactl [run] summary [OPTIONS]

#### Options

| Option            | Description                                                                                                             |
|:------------------|:------------------------------------------------------------------------------------------------------------------------|
| `[no_components]` | \[Default\] Complete summary collection                                                                                 |
| `-overview`       | \[Optional/Default\] Complete summary collection - Overview.                                                            |
| `-crs`            | \[Optional/Default\] CRS status summary.                                                                                |
| `-asm`            | \[Optional/Default\] Oracle ASM status summary.                                                                         |
| `-acfs`           | \[Optional/Default\] Oracle ACFS Status Summary.                                                                        |
| `-database`       | \[Optional/Default\] Oracle Database Status Summary.                                                                    |
| `-exadata`        | \[Optional/Default\] Oracle Exadata Status Summary.<br>Not enabled/ignored in Microsoft Windows and Non-Exadata machine |
| `-patch`          | \[Optional/Default\] Patch details.                                                                                     |
| `-listener`       | \[Optional/Default\] LISTENER status summary.                                                                           |
| `-network`        | \[Optional/Default\] NETWORK status summary.                                                                            |
| `-os`             | \[Optional/Default\] Operating system status summary.                                                                   |
| `-tfa`            | \[Optional/Default\] Oracle Trace File Analyzer status summary.                                                         |
| `-summary`        | \[Optional/Default\] Summary tool metadata.                                                                             |
| `-json`           | \[Optional\] - Prepare JSON report.                                                                                     |
| `-html`           | \[Optional\] - Prepare HTML report.                                                                                     |
| `-print`          | \[Optional\] - Display \[HTML or JSON\] report at console.                                                              |
| `-silent`         | \[Optional\] - Interactive console by default.                                                                          |
| `-history ``num`  | \[Optional\] - View Previous numberof summary collection history in interpreter.                                        |
| `-node`           | node(s) : \[Optional\] - local or comma-separated list of names of nodes.                                               |
| `-help`           | Usage/help                                                                                                              |

Example E-14 tfactl summary

    $ tfactl summary
    LOGFILE LOCATION : /opt/oracle.tfa/tfa/repository/suptools/myhost/summary/root/20180912055547/log/summary_command_20180912055547_myhost_5136.log

      Component Specific Summary collection :
        - Collecting CRS details ... Done.
        - Collecting ASM details ... Done.
        - Collecting ACFS details ... Done.
        - Collecting DATABASE details ... Done.
        - Collecting PATCH details ... Done.
        - Collecting LISTENER details ... Done.
        - Collecting NETWORK details ... Done.
        - Collecting OS details ... Done.
        - Collecting TFA details ... Done.
        - Collecting SUMMARY details ... Done.

      Prepare Clusterwide Summary Overview ... Done
          cluster_status_summary

      COMPONENT   STATUS    DETAILS
    +-----------+---------+--------------------------------------------------------------------------------------------------+
      CRS         OK        .-----------------------------------------------.
                            | CRS_SERVER_STATUS   : ONLINE                  |
                            | CRS_STATE           : ONLINE                  |
                            | CRS_INTEGRITY_CHECK : PASS                    |
                            | CRS_RESOURCE_STATUS : OFFLINE Resources Found |
                            '-----------------------------------------------'
      ASM         PROBLEM   .-------------------------------------------------------.
                            | ASM_DISK_SIZE_STATUS : WARNING - Available Size < 20% |
                            | ASM_BLOCK_STATUS     : PASS                           |
                            | ASM_CHAIN_STATUS     : PASS                           |
                            | ASM_INCIDENTS        : PASS                           |
                            | ASM_PROBLEMS         : FAIL                           |
                            '-------------------------------------------------------'
      ACFS        OFFLINE   .-----------------------.
                            | ACFS_STATUS : OFFLINE |
                            '-----------------------'
      DATABASE              .----------------------------------------------------------------------------------------------.
                            | ORACLE_HOME_DETAILS                                                       | ORACLE_HOME_NAME |
                            +---------------------------------------------------------------------------+------------------+
                            | .-----------------------------------------------------------------------. | OraDb11g_home1   |
                            | | PROBLEMS | INCIDENTS | DB_BLOCKS | DATABASE_NAME | STATUS | DB_CHAINS | |                  |
                            | +----------+-----------+-----------+---------------+--------+-----------+ |                  |
                            | | PASS     | PASS      | PASS      | apxcmupg      | OK     | PASS      | |                  |
                            | '----------+-----------+-----------+---------------+--------+-----------' |                  |
                            '---------------------------------------------------------------------------+------------------'
      PATCH       OK        .----------------------------------------------.
                            | CRS_PATCH_CONSISTENCY_ACROSS_NODES      : OK |
                            | DATABASE_PATCH_CONSISTENCY_ACROSS_NODES : OK |
                            '----------------------------------------------'
      LISTENER    OK        .-----------------------.
                            | LISTNER_STATUS   : OK |
                            '-----------------------'
      NETWORK     PROBLEM   .-------------------------------------.
                            | NODE_APPLICATION_CHECK : FAIL       |
                            | NODE_CONNECTIVITY : FAIL            |
                            | NTP_DAEMON_SLEW_OPTION_CHECK : FAIL |
                            '-------------------------------------'
      OS          OK        .-----------------------.
                            | MEM_USAGE_STATUS : OK |
                            '-----------------------'
      TFA         OK        .----------------------.
                            | TFA_STATUS : RUNNING |
                            '----------------------'
      SUMMARY     OK        .------------------------------------.
                            | SUMMARY_EXECUTION_TIME : 0H:1M:42S |
                            '------------------------------------'
    +-----------+---------+--------------------------------------------------------------------------------------------------+

            ### Entering in to SUMMARY Command-Line Interface ###

    tfactl_summary>list

      Components : Select Component - select [component_number|component_name]
            1 => overview
            2 => crs_overview
            3 => asm_overview
            4 => acfs_overview
            5 => database_overview
            6 => patch_overview
            7 => listener_overview
            8 => network_overview
            9 => os_overview
            10 => tfa_overview
            11 => summary_overview

    tfactl_summary>9

      IDLE_TIME   SWAP_USED   #CORES   HOSTNAME     MEM_USED   TASKS   LOAD   #PROCESSORS
    +-----------+-----------+--------+------------+----------+-------+------+-------------+
           78.7    8.11 %          1   myhost                    389   1.87             4
    +-----------+-----------+--------+------------+----------+-------+------+-------------+

    tfactl_summary_osoverview>list

      Status Type: Select Status Type - select [status_type_number|status_type_name]
            1 => os_clusterwide_status
            2 => os_myhost

    tfactl_summary_osoverview>1

      IDLE_TIME   SWAP_USED   #CORES   HOSTNAME     MEM_USED   TASKS   LOAD   #PROCESSORS
    +-----------+-----------+--------+------------+----------+-------+------+-------------+
           78.7    8.11 %          1   myhost                     389   1.87             4
    +-----------+-----------+--------+------------+----------+-------+------+-------------+

      Status Type: Select Status Type - select [status_type_number|status_type_name]
            1 => os_clusterwide_status
            2 => os_myhost

    tfactl_summary_osoverview>back

      Components : Select Component - select [component_number|component_name]
            1 => overview
            2 => crs_overview
            3 => asm_overview
            4 => acfs_overview
            5 => database_overview
            6 => patch_overview
            7 => listener_overview
            8 => network_overview
            9 => os_overview
            10 => tfa_overview
            11 => summary_overview

    tfactl_summary>help

      Following commands are supported in Summary Command-Line Interface
        l|list         => List Supported Components|Nodes|Databases|Tables
        number|select  => Select Component|Node|Database Listed in 'list'
        b|back         => UnSelect Component|Node|Database
        c|clear        => Clear Console
        q|quit         => Quit Summary Command-Line Interface
        ~              => Summary Command-Line Interface Home
        h|help         => Help

    tfactl_summary>q

            ### Exited From SUMMARY Command-Line Interface ###

    --------------------------------------------------------------------
    REPOSITORY  : /opt/oracle.tfa/tfa/repository/suptools/myhost/summary/root/20180912055547/myhost
    --------------------------------------------------------------------

**Parent topic:** Running Summary and Analysis Commands

### E.3.8 tfactl toolstatus

Use the `tfactl toolstatus`  command to view the status of Oracle Trace File Analyzer Support Tools across all nodes.

#### Syntax

    $ tfactl toolstatus

Example E-15 tfactl toolstatus

The `tfactl toolstatus`  command returns output similar to the following, showing which tool is deployed and where the tool is deployed.

    .------------------------------------------------------------------.
    |                 TOOLS STATUS - HOST : myhost                     |
    +----------------------+--------------+--------------+-------------+
    | Tool Type            | Tool         | Version      | Status      |
    +----------------------+--------------+--------------+-------------+
    | Development Tools    | orachk       |   12.2.0.1.3 | DEPLOYED    |
    |                      | oratop       |       14.1.2 | DEPLOYED    |
    +----------------------+--------------+--------------+-------------+
    | Support Tools Bundle | darda        | 2.10.0.R6036 | DEPLOYED    |
    |                      | oswbb        |        8.1.2 | RUNNING     |
    |                      | prw          | 12.1.13.11.4 | NOT RUNNING |
    +----------------------+--------------+--------------+-------------+
    | TFA Utilities        | alertsummary |   12.2.1.1.0 | DEPLOYED    |
    |                      | calog        |   12.2.0.1.0 | DEPLOYED    |
    |                      | dbcheck      |   18.3.0.0.0 | DEPLOYED    |
    |                      | dbglevel     |   12.2.1.1.0 | DEPLOYED    |
    |                      | grep         |   12.2.1.1.0 | DEPLOYED    |
    |                      | history      |   12.2.1.1.0 | DEPLOYED    |
    |                      | ls           |   12.2.1.1.0 | DEPLOYED    |
    |                      | managelogs   |   12.2.1.1.0 | DEPLOYED    |
    |                      | menu         |   12.2.1.1.0 | DEPLOYED    |
    |                      | param        |   12.2.1.1.0 | DEPLOYED    |
    |                      | ps           |   12.2.1.1.0 | DEPLOYED    |
    |                      | pstack       |   12.2.1.1.0 | DEPLOYED    |
    |                      | summary      |   12.2.1.1.0 | DEPLOYED    |
    |                      | tail         |   12.2.1.1.0 | DEPLOYED    |
    |                      | triage       |   12.2.1.1.0 | DEPLOYED    |
    |                      | vi           |   12.2.1.1.0 | DEPLOYED    |
    '----------------------+--------------+--------------+-------------'

    Note :-
      DEPLOYED    : Installed and Available - To be configured or run interactively.
      NOT RUNNING : Configured and Available - Currently turned off interactively.
      RUNNING     : Configured and Available.

**Parent topic:** Running Summary and Analysis Commands
