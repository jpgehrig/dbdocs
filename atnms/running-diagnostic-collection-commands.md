Run the diagnostic collection commands to collect diagnostic data.

- tfactl collection
  Use the `tfactl collection`  command to stop a running Oracle Trace File Analyzer collection.
- tfactl dbglevel
  Use the `tfactl dbglevel` command to set Oracle Grid Infrastructure trace levels.
- tfactl diagcollect
  Use the `tfactl diagcollect` command to perform on-demand diagnostic collection.
- tfactl diagcollect -srdc
  Use the `tfactl diagcollect -srdc` command to run a Service Request Data Collection (SRDC).
- tfactl directory
  Use the `tfactl directory` command to add a directory to, or remove a directory from the list of directories to analyze their trace or log files.
- tfactl ips
  Use the `tfactl ips`  command to collect Automatic Diagnostic Repository diagnostic data.
- tfactl managelogs
  Use the `tfactl managelogs`  command to manage Automatic Diagnostic Repository log and trace files.
- tfactl purge
  Use the `tfactl purge` command to delete diagnostic collections from the Oracle Trace File Analyzer repository that are older than a specific time.

**Parent topic:** [Oracle Trace File Analyzer Installer, Command-Line and Shell Options](tfa-command-reference.md)

### E.4.1 tfactl collection

Use the `tfactl collection`  command to stop a running Oracle Trace File Analyzer collection.

#### Syntax

    tfactl collection [stop collection_id]

You can only stop a collection using the `tfactl collection` command. You must provide a collection ID, which you can obtain by running the `tfactl print`  command.

**Parent topic:** Running Diagnostic Collection Commands

### E.4.2 tfactl dbglevel

Use the `tfactl dbglevel` command to set Oracle Grid Infrastructure trace levels.

#### Syntax

    tfactl [run] dbglevel
    [ {-set|-unset} profile_name
    -dependency [dep1,dep2,...|all]
    -dependency_type [type1,type2,type3,...|all]
    | {-view|-drop} profile_name
    | -lsprofiles
    | -lsmodules
    | -lscomponents [module_name]
    | -lsres
    | -create profile_name [ -desc description
    | [-includeunset] [-includetrace]
    | -debugstate | -timeout time ]
    | -modify profile_name [-includeunset] [-includetrace]
    | -getstate [ -module module_name ]
    | -active [profile_name]
    | -describe [profile_name] ] ]

#### Parameters

Table E-21 tfactl dbglevel Command Parameters

| Parameter         | Description                                                                   |
|:------------------|:------------------------------------------------------------------------------|
| `profile_name`    | Specify the name of the profile.                                              |
| `active`          | Displays the list of active profiles.                                         |
| `set`             | Sets the trace or log levels for the profile specified.                       |
| `unset`           | Unsets the trace or log levels for the profile specified.                     |
| `view`            | Displays the trace or log entries for the profile specified.                  |
| `create`          | Creates a profile.                                                            |
| `drop`            | Drops the profile specified.                                                  |
| `modify`          | Modifies the profile specified.                                               |
| `describe`        | Describes the profiles specified.                                             |
| `lsprofiles`      | Lists all the available profiles.                                             |
| `lsmodules`       | Lists all the discovered CRS modules.                                         |
| `lscomponents`    | Lists all the components associated with the CRS module.                      |
| `lsres`           | Lists all the discovered CRS resources.                                       |
| `getstate`        | Displays the current trace or log levels for the CRS components or resources. |
| `module`          | Specify the CRS module.                                                       |
| `dependency`      | Specify the dependencies to consider, start, or stop dependencies, or both.   |
| `dependency_type` | Specify the type of dependencies to be consider.                              |
| `debugstate`      | Generates a System State Dump for all the available levels.                   |
| `includeunset`    | Adds or modifies an unset value for the CRS components or resources.          |
| `includetrace`    | Adds or modifies a trace value for the CRS components.                        |

**WARNING:**

Set the profiles only at the direction of Oracle Support.

**Parent topic:** Running Diagnostic Collection Commands

### E.4.3 tfactl diagcollect

Use the `tfactl diagcollect` command to perform on-demand diagnostic collection.

Oracle Trace File Analyzer Collector can perform three types of on-demand collections:

- Default collections

- Event-driven Support Service Request Data Collection (SRDC) collections

- Custom collections

#### Prerequisites

Event-driven Support Service Request Data Collection (SRDC collections require components from the Oracle Trace File Analyzer Database Support Tools Bundle, which is available from My Oracle Support Note 1513912.2.

#### Syntax

    tfactl diagcollect [[component_name1] [component_name2] ... [component_nameN] | [-srdc srdc_profile] | [-defips]]
    [-sr SR#]
    [-node all|local|n1,n2,...]
    [-tag tagname]
    [-z filename]
    [-last nh|d | -from time -to time | -for time]
    [-nocopy]
    [-notrim]
    [-silent]
    [-nocores]
    [-collectalldirs]
    [-collectdir dir1,dir2...]
    [-examples]

    Components:-ips|-database|-asm|-crsclient|-dbclient|-dbwlm|-tns|-rhp|-procinfo|-afd|-crs|-cha|-wls|-emagent|-oms|-ocm|-emplugins|-em|-acfs
    |-install|-cfgtools|-os|-ashhtml|-ashtext|-awrhtml|-awrtext

#### Parameters

Prefix each option with a minus sign (-).

| Option                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `[[``component_name1``] [``component_name2``] ... [``component_nameN``] | [-srdc ``srdc_profile``] | [-defips]]] ` | Specify the list of components for which you want to obtain collections, or specify the SRDC name, or specify to include IPS Packages for ASM, CRS, and Oracle Databases in the default collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `[-sr ``SR#``]`                                                                                                    | Specify the Service Request number to which Oracle Trace File Analyzer automatically uploads all collections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-node all|local|``n1,n2,...`                                                                                      | Specify a comma-delimited list of nodes from which to collect diagnostic information. Default is all.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-tag ``description`                                                                                               | Use this parameter to create a subdirectory for the resulting collection in the Oracle Trace File Analyzer repository.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-z ``file_name`                                                                                                   | Use this parameter to specify an output file name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `[-last ``n``h``|``d`` | -from ``time`` -to ``time`` | -for ``time``]`                                             | • Specify the `-last` parameter to collect files that have relevant data for the past specific number of hours (h) or days (d). By default, using the command with this parameter also trims files that are large and shows files only from the specified interval.<br>• You can also use `-since`, which has the same functionality as `-last`. This option is included for backward compatibility.<br>• Specify the `-from` and `-to` parameters (you must use these two parameters together) to collect files that have relevant data during a specific time interval, and trim data before this time where files are large.<br>• Supported time formats:<br>• `"Mon/dd/yyyy hh:mm:ss"`<br>• `"yyyy-mm-dd hh:mm:ss"`<br>• `"yyyy-mm-ddThh:mm:ss"`<br>• `"yyyy-mm-dd"`<br>• Specify the `-for` parameter to collect files that have relevant data for the time given. The files TFACTL collects will have timestamps in between which the time you specify after `-for` is included. No data trimming is done for this option.<br>• Supported time formats:<br>• `"Mon/dd/yyyy"`<br>• `"yyyy-mm-dd"`<br>**Note:**<br>If you specify both date and time, then you must enclose both the values in double quotation marks (""). If you specify only the date or the time, then you do not have to enclose the single value in quotation marks. |
| `-nocopy`                                                                                                          | Specify this parameter to stop the resultant trace file collection from being copied back to the initiating node. The file remains in the Oracle Trace File Analyzer repository on the executing node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-notrim`                                                                                                          | Specify this parameter to stop trimming the files collected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-silent`                                                                                                          | Specify this parameter to run diagnostic collection as a background process                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-nocores`                                                                                                         | Specify this parameter to stop collecting core files when it would normally have been collected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-collectalldirs`                                                                                                  | Specify this parameter to collect all files from a directory that has `Collect All`  flag marked true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-collectdir ``dir1``,``dir2``,...``dirn`                                                                          | Specify a comma-delimited list of directories and collection includes all files from these directories irrespective of type and time constraints in addition to the components specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-examples`                                                                                                        | Specify this parameter to view `diagcollect` usage examples.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

Example E-16 tfactl diagcollect

    $ tfactl diagcollect

    By default TFA will collect diagnostics for the last 12 hours. This can result in large collections
    For more targeted collections enter the time of the incident, otherwise hit <RETURN> to collect for the last 12 hours
    [YYYY-MM-DD HH24:MI:SS,<RETURN>=Collect for last 12 hours] :

    Collecting data for the last 12 hours for all components...
    Collecting data for all nodes

    Collection Id : 20180912012618myhost

    Detailed Logging at : /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_26_18_PDT_2018_node_all/diagcollect_20180912012618_myhost.log
    2018/09/12 01:26:23 PDT : NOTE : Any file or directory name containing the string .com will be renamed to replace .com with dotcom
    2018/09/12 01:26:23 PDT : Collection Name : tfa_Wed_Sep_12_01_26_18_PDT_2018.zip
    2018/09/12 01:26:23 PDT : Collecting diagnostics from hosts : [myhost]
    2018/09/12 01:26:23 PDT : Scanning of files for Collection in progress...
    2018/09/12 01:26:23 PDT : Collecting additional diagnostic information...
    2018/09/12 01:27:18 PDT : Getting list of files satisfying time range [09/11/2018 13:26:23 PDT, 09/12/2018 01:27:18 PDT]
    2018/09/12 01:28:03 PDT : Collecting ADR incident files...
    2018/09/12 01:28:28 PDT : Completed collection of additional diagnostic information...
    2018/09/12 01:28:38 PDT : Completed Local Collection
    .--------------------------------------.
    |          Collection Summary          |
    +------------+-----------+------+------+
    | Host       | Status    | Size | Time |
    +------------+-----------+------+------+
    | myhost     | Completed | 71MB | 135s |
    '------------+-----------+------+------'

    Logs are being collected to: /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_26_18_PDT_2018_node_all
    /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_26_18_PDT_2018_node_all/myhost.tfa_Wed_Sep_12_01_26_18_PDT_2018.zip

    $ tfactl diagcollect -for "2018-09-11 21:00:00"
    Collecting data for all nodes
    Scanning files for sep/11/2018 21:00:00

    Collection Id : 20180912014217myhost

    Detailed Logging at : /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_42_17_PDT_2018_node_all/diagcollect_20180912014217_myhost.log
    2018/09/12 01:42:21 PDT : NOTE : Any file or directory name containing the string .com will be renamed to replace .com with dotcom
    2018/09/12 01:42:21 PDT : Collection Name : tfa_Wed_Sep_12_01_42_17_PDT_2018.zip
    2018/09/12 01:42:21 PDT : Collecting diagnostics from hosts : [myhost]
    2018/09/12 01:42:21 PDT : Scanning of files for Collection in progress...
    2018/09/12 01:42:21 PDT : Collecting additional diagnostic information...
    2018/09/12 01:42:36 PDT : Getting list of files satisfying time range [09/11/2018 09:00:00 PDT, 09/12/2018 01:42:21 PDT]
    2018/09/12 01:43:13 PDT : Collecting ADR incident files...
    2018/09/12 01:44:00 PDT : Completed collection of additional diagnostic information...
    2018/09/12 01:44:06 PDT : Completed Local Collection
    .--------------------------------------.
    |          Collection Summary          |
    +------------+-----------+------+------+
    | Host       | Status    | Size | Time |
    +------------+-----------+------+------+
    | myhost     | Completed | 73MB | 105s |
    '------------+-----------+------+------'

    Logs are being collected to: /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_42_17_PDT_2018_node_all
    /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_42_17_PDT_2018_node_all/myhost.tfa_Wed_Sep_12_01_42_17_PDT_2018.zip

The following command trims and zips all Oracle ASM logs from `myhost` updated between September 10, 2018 and September 11, 2018, and collects it on the initiating node:

    $ tfactl diagcollect -asm -node myhost -from "2018-09-10 21:00:00" -to "2018-09-11 21:00:00"
    Collecting data for myhost node(s)
    Scanning files from sep/10/2018 21:00:00 to sep/11/2018 21:00:00

    Collection Id : 20180912015138myhost

    Detailed Logging at : /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_51_38_PDT_2018_node_myhost/diagcollect_20180912015138_myhost.log
    2018/09/12 01:51:43 PDT : NOTE : Any file or directory name containing the string .com will be renamed to replace .com with dotcom
    2018/09/12 01:51:43 PDT : Collection Name : tfa_Wed_Sep_12_01_51_38_PDT_2018.zip
    2018/09/12 01:51:43 PDT : Collecting diagnostics from hosts : [myhost]
    2018/09/12 01:51:43 PDT : Getting list of files satisfying time range [09/10/2018 21:00:00 PDT, 09/11/2018 21:00:00 PDT]
    2018/09/12 01:51:43 PDT : Collecting additional diagnostic information...
    2018/09/12 01:51:45 PDT : Collecting ADR incident files...
    2018/09/12 01:52:16 PDT : Completed collection of additional diagnostic information...
    2018/09/12 01:52:20 PDT : Completed Local Collection
    .---------------------------------------.
    |           Collection Summary          |
    +------------+-----------+-------+------+
    | Host       | Status    | Size  | Time |
    +------------+-----------+-------+------+
    | myhost     | Completed | 818kB |  37s |
    '------------+-----------+-------+------'

    Logs are being collected to: /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_51_38_PDT_2018_node_myhost
    /opt/oracle.tfa/tfa/repository/collection_Wed_Sep_12_01_51_38_PDT_2018_node_myhost/myhost.tfa_Wed_Sep_12_01_51_38_PDT_2018.zip

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=1513912.2>

**Parent topic:** Running Diagnostic Collection Commands

### E.4.4 tfactl diagcollect -srdc

Use the `tfactl diagcollect -srdc` command to run a Service Request Data Collection (SRDC).

#### Syntax

    tfactl diagcollect -srdc srdc_profile
    [-tag tagname]
    [-z filename]
    [-last nh|d | -from time -to time | -for time]
    -database database

#### Parameters

Each option must be prefixed with a minus sign (-).

| Option                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `[-srdc ``srdc_profile``]`                                             | Specify the SRDC profile.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-tag ``description`                                                   | Use this parameter to create a subdirectory for the resulting collection in the Oracle Trace File Analyzer repository.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-z ``file_name`                                                       | Use this parameter to specify an output file name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `[-last ``n``h``|``d`` | -from ``time`` -to ``time`` | -for ``time``]` | • Specify the `-last` parameter to collect files that have relevant data for the past specific number of hours (h) or days (d). By default, using the command with this parameter also trims files that are large and shows files only from the specified interval.<br>• You can also use `-since`, which has the same functionality as `-last`. This option is included for backward compatibility.<br>• Specify the `-from` and `-to` parameters (you must use these two parameters together) to collect files that have relevant data during a specific time interval, and trim data before this time where files are large.<br>• Supported time formats:<br>• `"Mon/dd/yyyy hh:mm:ss"`<br>• `"yyyy-mm-dd hh:mm:ss"`<br>• `"yyyy-mm-ddThh:mm:ss"`<br>• `"yyyy-mm-dd"`<br>• Specify the `-for` parameter to collect files that have relevant data for the time given. The files TFACTL collects will have timestamps in between which the time you specify after `-for` is included. No data trimming is done for this option.<br>• Supported time formats:<br>• `"Mon/dd/yyyy"`<br>• `"yyyy-mm-dd"`<br>**Note:**<br>If you specify both date and time, then you must enclose both the values in double quotation marks (""). If you specify only the date or the time, then you do not have to enclose the single value in quotation marks. |
| `-database ``database`                                                 | Specify the name of the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### SRDC Profiles

| SRDC Profile             | Description                                                                                                                                      |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `listener_services`      | Collects data for listener services errors: `TNS-12514` / `TNS-12516` / `TNS-12518` / `TNS-12519` / `TNS-12520` / `TNS-12528`.                   |
| `naming_services`        | Collects data for naming services errors: `ORA-12514` / `ORA-12528`.                                                                             |
| `ORA-00020`              | Collects data regarding maximum number of processes exceeded.                                                                                    |
| `ORA-00060`, `ORA-00600` | Collects data for internal errors.                                                                                                               |
| `ORA-00700`              | Collects data for soft internal error.                                                                                                           |
| `ORA-01031`              | Collects standard information for `ORA-1031` / `ORA-1017` during SYSDBA connections                                                              |
| `ORA-01555`              | Collects data for Oracle Database `Snapshot too old` error.                                                                                      |
| `ORA-01578`              | Collects data for `NOLOGGING ORA-1578` / `ORA-26040 DBV-00201`.                                                                                  |
| `ORA-01628`              | Collects data for Oracle Database `Snapshot too old` error.                                                                                      |
| `ORA-04030`              | Collects data for `OS process private memory was exhausted` error.                                                                               |
| `ORA-04031`              | Collects data for `More shared memory is needed in the shared/streams pool.` error.                                                              |
| `ORA-07445`              | Collects data for `Exception encountered, core dump.` error.                                                                                     |
| `ORA-08102`              | Collects data for ORA error `ORA-08102`.                                                                                                         |
| `ORA-08103`              | Collects data for ORA error `ORA-08103`.                                                                                                         |
| `ORA-27300`              | Collects data for `OS system dependent operation: open failed with status: (status).` error.                                                     |
| `ORA-27301`              | Collects data for `OS failure message: (message).` error.                                                                                        |
| `ORA-27302`              | Collects data for `Failure occurred at: (module).` error.                                                                                        |
| `ORA-29548`              | Provides Supporting Information for Oracle JVM Issues (My Oracle Support note 2175568.1).                                                        |
| `ORA-30036`              | Collects data for Oracle Database `Unable to extend Undo Tablespace` error.                                                                      |
| `dbasm`                  | Collects data for Oracle Database storage problems.                                                                                              |
| `dbaudit`                | Collects standard information for Oracle Database auditing.                                                                                      |
| `dbawrspace`             | Collects data for Oracle Database Automatic Workload Repository (AWR) space problems.                                                            |
| `dbblockcorruption`      | Collects data for Alert Log Message `Corrupt block relative dba`.                                                                                |
| `dbdataguard`            | Collects data for Oracle Data Guard problems.                                                                                                    |
| `dbexp`                  | Collects information for troubleshooting original Export (exp) related problems.                                                                 |
| `dbexpdp`                | Collects data for Data Pump Export generic issues.                                                                                               |
| `dbexpdpapi`             | Collects data for Data Pump Export API Issues.                                                                                                   |
| `dbexpdpperf`            | Collects data for Data Pump Export performance issues.                                                                                           |
| `dbexpdptts`             | Collects data to supply for Transportable Tablespace Data Pump and original EXPORT, IMPORT.                                                      |
| `dbfs`                   | Collects data for `dbfs` issues.                                                                                                                 |
| `dbggclassicmode`        | Collects data for Oracle GoldenGate Classic Mode issues.                                                                                         |
| `dbggintegratedmode`     | Collects data for Oracle GoldenGate Extract / Replicat abends problems.                                                                          |
| `dbimp`                  | Collects data for troubleshooting original Import (imp) releated problems.                                                                       |
| `dbimpdp`                | Collects data for Data Pump Import generic issues.                                                                                               |
| `dbimpdpperf`            | Collects data for Data Pump Import performance issues.                                                                                           |
| `dbinstall`              | Collects data for Oracle Database install / upgrade problems.                                                                                    |
| `dbpartition`            | Collects data for `Create` / maintain partitioned / subpartitioned table / index problems.                                                       |
| `dbpartitionperf`        | Collects data for slow `Create` / `Alter` / `Drop` commands against partitioned table / index problems.                                          |
| `dbpatchconflict`        | Collects data for Oracle Database patch conflict problems.                                                                                       |
| `dbpatchinstall`         | Collects data for Oracle Database patch install problems.                                                                                        |
| `dbperf`                 | Collects data for Oracle Database performance problems.                                                                                          |
| `dbpreupgrade`           | Collects data for Oracle Database preupgrade problems.                                                                                           |
| `dbrman`                 | Collects data for RMAN related issues, such as backup, maintenance, restore and recover, `RMAN-08137`, or `RMAN-08120`.                          |
| `dbrman600`              | Collects data for `RMAN-00600` error (My Oracle Support note 2045195.1).                                                                         |
| `dbrmanperf`             | Collects data for RMAN Performance error (My Oracle Support note 1671509.1).                                                                     |
| `dbscn`                  | Collects data for Oracle Database SCN problems.                                                                                                  |
| `dbshutdown`             | Collects data for single instance Oracle Database shutdown problems.                                                                             |
| `dbsqlperf`              | Collects data for an SQL performance problem using Oracle Trace File Analyzer Collector.                                                         |
| `dbstartup`              | Collects data for single instance Oracle Database startup problems.                                                                              |
| `dbtde`                  | Collects data for Transparent Data Encryption (TDE) (My Oracle Support note 1905607.1)                                                           |
| `dbundocorruption`       | Collects data for UNDO corruption problems.                                                                                                      |
| `dbunixresources`        | Collects data for Oracle Database issues related to operating system resources.                                                                  |
| `dbupgrade`              | Collects data for Oracle Database upgrade problems.                                                                                              |
| `dbxdb`                  | Collects data Oracle Database XDB installation and invalid object problems.                                                                      |
| `dnfs`                   | Collects data for DNFS problems.                                                                                                                 |
| `emagentperf`            | Collects data for Enterprise Manager Agent performance issues.                                                                                   |
| `emcliadd`               | Collects data for Enterprise Manager errors while adding an Oracle Database, a listener, or an ASM target using Enterprise Manager command-line. |
| `emclusdisc`             | Collects data for cluster target, cluster (RAC) Oracle Database, or an ASM target is not discovered issue.                                       |
| `emdbsys`                | Collects data for Enterprise Manager Oracle Database system target is not discovered, detected, removed, or renamed correctly issue.             |
| `emdebugoff`             | Collects data for unsetting Enterprise Manager debug.                                                                                            |
| `emdebugon`              | Collects data for setting Enterprise Manager debug.                                                                                              |
| `emgendisc`              | Collects data for Enterprise Manager generic error while discovering, or removing an Oracle Database, a listener, or an ASM target.              |
| `emmetricalert`          | Collects data for Enterprise Manager metric events not raised and general metric alert related issues.                                           |
| `emomscrash`             | Collects for all Enterprise Manager OMS crash or restart performance issues.                                                                     |
| `emomsheap`              | Collects data for Enterprise Manager OMS heap usage alert performance issues.                                                                    |
| `emomshungcpu`           | Collects data for Enterprise Manager OMS hung or high CPU usage performance issues.                                                              |
| `emprocdisc`             | Collects data for Enterprise Manager Oracle Database, listener, or an ASM target is not discovered or detected by the discovery process issues.  |
| `emrestartoms`           | Collects data for Enterprise Manager restart OMS crash problems.                                                                                 |
| `emtbsmetric`            | Collects data for Enterprise Manager Tablespace space used metric issues.                                                                        |
| `esexalogic`             | Collects data for Oracle Exalogic Full Exalogs problems.                                                                                         |
| `ggintegratedmodenodb`   | Collects data for Oracle GoldenGate Extract/Replicat abends problems.                                                                            |
| `internalerror`          | Collects data for all other types of internal Oracle Database errors.                                                                            |

**Related Topics**

- [https://support.oracle.com/rs?type=doc&amp;id=2175568.1](https://support.oracle.com/rs?type=doc&amp;amp;id=2175568.1)
- [https://support.oracle.com/rs?type=doc&amp;id=2045195.1](https://support.oracle.com/rs?type=doc&amp;amp;id=2045195.1)
- [https://support.oracle.com/rs?type=doc&amp;id=1671509.1](https://support.oracle.com/rs?type=doc&amp;amp;id=1671509.1)
- [https://support.oracle.com/rs?type=doc&amp;id=1905607.1](https://support.oracle.com/rs?type=doc&amp;amp;id=1905607.1)

**Parent topic:** Running Diagnostic Collection Commands

### E.4.5 tfactl directory

Use the `tfactl directory` command to add a directory to, or remove a directory from the list of directories to analyze their trace or log files.

Also, use the `tfactl directory` command to change the directory permissions. When automatic discovery adds a directory, the directory is added as public. Any user who has sufficient permissions to run the `tfactl diagcollect` command collects any file in that directory. This is only important when non-root or `sudo` users run TFACTL commands.

If a directory is marked as private, then Oracle Trace File Analyzer, before allowing any files to be collected:

- Determines which user is running TFACTL commands

- Verifies if the user has permissions to see the files in the directory

**Note:**

A user can only add a directory to Oracle Trace File Analyzer to which they have read access. If you have automatic diagnostic collections configured, then Oracle Trace File Analyzer runs as `root`, and can collect all available files.

The `tfactl directory` command includes three verbs with which you can manage directories: `add`, `remove`, and `modify`.

#### Syntax

    tfactl directory add directory [-public] [-exclusions | -noexclusions | -collectall] [-node all | n1,n2...]

    tfactl directory remove directory [-node all | n1,n2...]

    tfactl directory modify directory [-private | -public] [-exclusions | -noexclusions | -collectall]

For each of the three syntax models, you must specify a directory path where Oracle Trace File Analyzer stores collections.

#### Parameters

Table E-22 tfactl directory Command Parameters

| Parameter                | Description                                                                                                                                                                                                                                                         |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-public`                | Use the `-public` parameter to make the files contained in the directory available for collection by any Oracle Trace File Analyzer user.                                                                                                                           |
| `-private`               | Use the `-private` parameter to prevent an Oracle Trace File Analyzer user who does not have permission to see the files in a directory (and any subdirectories) you are adding or modifying, from running a command to collect files from the specified directory. |
| `-exclusions`            | Use the `-exclusions` parameter to specify that files in this directory are eligible for collection if the files satisfy type, name, and time range restrictions.                                                                                                   |
| `-noexclusions`          | Use the `-noexclusions` parameter to specify that files in this directory are eligible for collection if the files satisfy time range restrictions.                                                                                                                 |
| `-collectall`            | Use the `-collectall` parameter to specify that files in this directory are eligible for collection irrespective of type and time range when the user specifies the `-collectalldirs` parameter with the `tfactl diagcollect` command.                              |
| `-node all | ``n1,n2...` | Add or remove directories from every node in the cluster or use a comma-delimited list to add or remove directories from specific nodes.                                                                                                                            |

#### Usage Notes

You must add all trace directory names to the Berkeley database so that Oracle Trace File Analyzer can collect file metadata in that directory. The discovery process finds most directories, but if new or undiscovered directories are required, then you can add these manually using the `tfactl directory` command.

When you add a directory using TFACTL, then Oracle Trace File Analyzer attempts to determine whether the directory is for

- Oracle Database

- Oracle Grid Infrastructure

- Operating system logs

- Some other component

- Which database or instance

If Oracle Trace File Analyzer cannot determine this information, then Oracle Trace File Analyzer returns an error and requests that you enter the information, similar to the following:

    # tfactl directory add /tmp

    Failed to add directory to TFA. Unable to determine parameters for directory: /tmp
    Please enter component for this Directory [RDBMS|CRS|ASM|INSTALL|OS|CFGTOOLS|TNS|DBWLM|ACFS|ALL] : RDBMS
    Please enter database name for this Directory :MYDB
    Please enter instance name for this Directory :MYDB1

**Note:**

For OS, CRS, CFGTOOLS, ACFS, ALL, or INSTALL files, only the component is requested and for Oracle ASM only the instance is created. No verification is done for these entries so use caution when entering this data.

Example E-17 tfactl directory

The following command adds a directory:

    # tfactl directory add /u01/app/grid/diag/asm/+ASM1/trace

The following command modifies a directory and makes the contents available for collection only to Oracle Trace File Analyzer users with sufficient permissions:

    # tfactl directory modify /u01/app/grid/diag/asm/+ASM1/trace -private

The following command removes a directory from all nodes in the cluster:

    # tfactl directory remove /u01/app/grid/diag/asm/+ASM1/trace -node all

**Parent topic:** Running Diagnostic Collection Commands

### E.4.6 tfactl ips

Use the `tfactl ips`  command to collect Automatic Diagnostic Repository diagnostic data.

#### Syntax

    tfactl ips
    [ADD]
    [ADD FILE]
    [ADD NEW INCIDENTS]
    [CHECK REMOTE KEYS]
    [COPY IN FILE]
    [COPY OUT FILE]
    [CREATE PACKAGE]
    [DELETE PACKAGE]
    [FINALIZE PACKAGE]
    [GENERATE PACKAGE]
    [GET MANIFEST]
    [GET METADATA]
    [GET REMOTE KEYS]
    [PACK]
    [REMOVE]
    [REMOVE FILE]
    [SET CONFIGURATION]
    [SHOW CONFIGURATION]
    [SHOW FILES]
    [SHOW INCIDENTS]
    [SHOW PROBLEMS]
    [SHOW PACKAGE]
    [UNPACK FILE]
    [UNPACK PACKAGE]
    [USE REMOTE KEYS]
    [options]

For detailed help on each topic use:

    help ips topic

#### Parameters

Table E-23 tfactl ips Command Parameters

| Parameter            | Description                                                                                                                  |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| `ADD`                | Adds incidents to an existing package.                                                                                       |
| `ADD FILE`           | Adds a file to an existing package.                                                                                          |
| `ADD NEW INCIDENTS`  | Finds new incidents for the problems and add the latest ones to the package.                                                 |
| `CHECK REMOTE KEYS`  | Creates a file with keys matching incidents in specified package.                                                            |
| `COPY IN FILE`       | Copies an external file into Automatic Diagnostic Repository, and associates it with a package and (optionally) an incident. |
| `COPY OUT FILE`      | Copies an Automatic Diagnostic Repository file to a location outside Automatic Diagnostic Repository.                        |
| `CREATE PACKAGE`     | Creates a package, and optionally select contents for the package.                                                           |
| `DELETE PACKAGE`     | Drops a package and its contents from Automatic Diagnostic Repository.                                                       |
| `FINALIZE PACKAGE`   | Gets a package ready for shipping by automatically including correlated contents.                                            |
| `GENERATE PACKAGE`   | Creates a physical package (`zip`  file) in target directory.                                                                |
| `GET MANIFEST`       | Extracts the manifest from a package file and displays it.                                                                   |
| `GET METADATA`       | Extracts the metadata XML document from a package file and displays it.                                                      |
| `GET REMOTE KEYS`    | Creates a file with keys matching incidents in specified package.                                                            |
| `PACK`               | Creates a package, and immediately generates the physical package.                                                           |
| `REMOVE`             | Removes incidents from an existing package.                                                                                  |
| `REMOVE FILE`        | Removes a file from an existing package.                                                                                     |
| `SET CONFIGURATION`  | Changes the value of an Incident Packaging Service configuration parameter.                                                  |
| `SHOW CONFIGURATION` | Shows the current Incident Packaging Service settings.                                                                       |
| `SHOW FILES`         | Shows the files included in the specified package.                                                                           |
| `SHOW INCIDENTS`     | Shows incidents included in the specified package.                                                                           |
| `SHOW PROBLEMS`      | Shows problems for the current Automatic Diagnostic Repository home.                                                         |
| `SHOW PACKAGE`       | Shows details for the specified package.                                                                                     |
| `UNPACK FILE`        | Unpackages a physical file into the specified path.                                                                          |
| `UNPACK PACKAGE`     | Unpackages physical files in the current directory into the specified path, if they match the package name.                  |
| `USE REMOTE KEYS`    | Adds incidents matching the keys in the specified file to the specified package.                                             |

- tfactl ips ADD
  Use the `tfactl ips ADD`  command to add incidents to an existing package.
- tfactl ips ADD FILE
  Use the `tfactl ADD FILE`  command to add a file to an existing package.
- tfactl ips ADD NEW INCIDENTS
  Use the `tfactl ips ADD NEW INCIDENTS`  command to find new incidents for the problems in a specific package, and add the latest ones to the package.
- tfactl ips CHECK REMOTE KEYS
  Use the `tfactl ips CHECK REMOTE KEYS`  command to create a file with keys matching incidents in a specified package.
- tfactl ips COPY IN FILE
  Use the `tfactl ips COPY IN FILE`  command to copy an external file into Automatic Diagnostic Repository, and associate the file with a package and (optionally) an incident.
- tfactl ips COPY OUT FILE
  Use the `tfactl ips COPY OUT FILE`  command to copy an Automatic Diagnostic Repository file to a location outside Automatic Diagnostic Repository.
- tfactl ips CREATE PACKAGE
  Use the `tfactl ips CREATE PACKAGE`  command to create a package, and optionally select the contents for the package.
- tfactl ips DELETE PACKAGE
  Use the `tfactl ips DELETE PACKAGE`  command to drop a package and its contents from the Automatic Diagnostic Repository.
- tfactl ips FINALIZE PACKAGE
  Use the `tfactl ips FINALIZE PACKAGE`  command to get a package ready for shipping by automatically including correlated contents.
- tfactl ips GENERATE PACKAGE
  Use the `tfactl ips GENERATE PACKAGE`  command to create a physical package (`zip` file) in the target directory.
- tfactl ips GET MANIFEST
  Use the `tfactl ips GET MANIFEST`  command to extract the manifest from a package file and view it.
- tfactl ips GET METADATA
  Use the `tfactl ips GET METADATA`  command to extract the metadata XML document from a package file and view it.
- tfactl ips GET REMOTE KEYS
  Use the `tfactl ips GET REMOTE KEYS`  command to create a file with keys matching incidents in a specific package.
- tfactl ips PACK
  Use the `tfactl ips PACK` command to create a package and immediately generate the physical package.
- tfactl ips REMOVE
  Use the `tfactl ips REMOVE`  command to remove incidents from an existing package.
- tfactl ips REMOVE FILE
  Use the `tfactl ips REMOVE FILE`  command to remove a file from an existing package.
- tfactl ips SET CONFIGURATION
  Use the `tfactl ips SET CONFIGURATION`  command to change the value of an Incident Packaging Service configuration parameter.
- tfactl ips SHOW CONFIGURATION
  Use the `tfactl ips SHOW CONFIGURATION`  command to view the current Incident Packaging Service settings.
- tfactl ips SHOW FILES
  Use the `tfactl ips SHOW FILES`  command to view the files included in a specific package.
- tfactl ips SHOW INCIDENTS
  Use the `tfactl ips SHOW INCIDENTS`  command to view the incidents included in a specific package.
- tfactl ips SHOW PROBLEMS
  Use the `tfactl ips SHOW PROBLEMS`  command to view the problems for the current Automatic Diagnostic Repository home.
- tfactl ips SHOW PACKAGE
  Use the `tfactl ips SHOW PACKAGE`  command to view the details of a specific package.
- tfactl ips UNPACK FILE
  Use the `tfactl ips UNPACK FILE`  command to unpack a physical file into a specific path.
- tfactl ips UNPACK PACKAGE
  Use the `tfactl ips UNPACK PACKAGE`  command to unpack physical files in the current directory into a specific path, if they match the package name.
- tfactl ips USE REMOTE KEYS
  Use the `tfactl ips USE REMOTE KEYS`  command to add incidents matching the keys in a specific file to a specific package.

**Parent topic:** Running Diagnostic Collection Commands

#### E.4.6.1 tfactl ips ADD

Use the `tfactl ips ADD`  command to add incidents to an existing package.

##### Syntax

    tfactl ips ADD [INCIDENT incid | PROBLEM prob_id | PROBLEMKEY prob_key | SECONDS seconds | TIME start_time TO end_time] PACKAGE package_id

##### Parameters

Table E-24 tfactl ips ADD Command Parameters

| Parameter    | Description                                                           |
|:-------------|:----------------------------------------------------------------------|
| `incid`      | Specify the ID of the incident to add to the package contents.        |
| `prob_id`    | Specify the ID of the problem to add to the package contents.         |
| `prob_key`   | Specify the problem key to add to the package contents.               |
| `seconds`    | Specify the number of seconds before now for adding package contents. |
| `start_time` | Specify the start of time range to look for incidents in.             |
| `end_time`   | Specify the end of time range to look for incidents in.               |

Example E-18 tfactl ips ADD

    $ tfactl ips add incident 22 package 12

**Parent topic:** tfactl ips

#### E.4.6.2 tfactl ips ADD FILE

Use the `tfactl ADD FILE`  command to add a file to an existing package.

##### Syntax

The file must be in the same `ADR_BASE`  as the package.

    tfactl ips ADD FILE file_spec PACKAGE pkgid

##### Parameters

Table E-25 tfactl ips ADD FILE Command Parameters

| Parameter    | Description                                             |
|:-------------|:--------------------------------------------------------|
| `file_spec`  | Specify the file with file and path (full or relative). |
| `package_id` | Specify the ID of the package to add the file to.       |

Example E-19 tfactl ips ADD FILE

    $ tfactl ips add file ADR_HOME/trace/mydb1_ora_13579.trc package 12

**Parent topic:** tfactl ips

#### E.4.6.3 tfactl ips ADD NEW INCIDENTS

Use the `tfactl ips ADD NEW INCIDENTS`  command to find new incidents for the problems in a specific package, and add the latest ones to the package.

##### Syntax

    tfactl ips ADD NEW INCIDENTS package_id

##### Parameters

Table E-26 tfactl ips ADD NEW INCIDENTS Command Parameters

| Parameter    | Description                                            |
|:-------------|:-------------------------------------------------------|
| `package_id` | Specify the ID of the package to add the incidents to. |

**Parent topic:** tfactl ips

#### E.4.6.4 tfactl ips CHECK REMOTE KEYS

Use the `tfactl ips CHECK REMOTE KEYS`  command to create a file with keys matching incidents in a specified package.

##### Syntax

    tfactl ips CHECK REMOTE KEYS file_spec PACKAGE package_id

##### Parameters

Table E-27 tfactl ips CHECK REMOTE KEYS Command Parameters

| Parameter    | Description                                        |
|:-------------|:---------------------------------------------------|
| `file_spec`  | Specify the file with file name and full path.     |
| `package_id` | Specify the ID of the package to get the keys for. |

**Parent topic:** tfactl ips

#### E.4.6.5 tfactl ips COPY IN FILE

Use the `tfactl ips COPY IN FILE`  command to copy an external file into Automatic Diagnostic Repository, and associate the file with a package and (optionally) an incident.

##### Syntax

    tfactl ips COPY IN FILE file [TO new_name] [OVERWRITE] PACKAGE pkgid [INCIDENT incid]

##### Parameters

Table E-28 tfactl ips COPY IN FILE Command Parameters

| Parameter  | Description                                                       |
|:-----------|:------------------------------------------------------------------|
| `file`     | Specify the file with file name and full path (full or relative). |
| `new_name` | Specify a name for the copy of the file.                          |
| `pkgid`    | Specify the ID of the package to associate the file with.         |
| `incid`    | Specify the ID of the incident to associate the file with.        |

##### Options

`OVERWRITE`: If the file exists, then use the `OVERWRITE` option to overwrite the file.

Example E-20 tfactl ips COPY IN FILE

    $ tfactl ips copy in file /tmp/key_file.txt to new_file.txt package 12 incident 62

**Parent topic:** tfactl ips

#### E.4.6.6 tfactl ips COPY OUT FILE

Use the `tfactl ips COPY OUT FILE`  command to copy an Automatic Diagnostic Repository file to a location outside Automatic Diagnostic Repository.

##### Syntax

    tfactl IPS COPY OUT FILE source TO target [OVERWRITE]

##### Parameters

Table E-29 tfactl ips COPY OUT FILE Command Parameters

| Parameter | Description                                                                                         |
|:----------|:----------------------------------------------------------------------------------------------------|
| `source`  | Specify the file with file name and full path (full or relative).<br>This file must be inside ADR.  |
| `target`  | Specify the file with file name and full path (full or relative).<br>This file must be outside ADR. |

##### Options

`OVERWRITE`: If the file exists, then use the `OVERWRITE` option to overwrite the file.

Example E-21 tfactl ips COPY OUT FILE

    $ tfactl ips copy out file ADR_HOME/trace/ora_26201 to /tmp/trace_26201.txt

**Parent topic:** tfactl ips

#### E.4.6.7 tfactl ips CREATE PACKAGE

Use the `tfactl ips CREATE PACKAGE`  command to create a package, and optionally select the contents for the package.

##### Syntax

    tfactl ips CREATE PACKAGE [INCIDENT inc_id | PROBLEM prob_id
    | PROBLEMKEY prob_key | SECONDS seconds | TIME start_time TO end_time] [CORRELATE BASIC | TYPICAL | ALL] [MANIFEST file_spec]
    [KEYFILE file_spec]

##### Parameters

Table E-30 tfactl ips CREATE PACKAGE Command Parameters

| Parameter    | Description                                                                  |
|:-------------|:-----------------------------------------------------------------------------|
| `incid`      | Specify the ID of the incident to use for selecting the package contents.    |
| `prob_id`    | Specify the ID of the problem to use for selecting the package contents.     |
| `prob_key`   | Specify the problem key to use for selecting the package contents.           |
| `seconds`    | Specify the number of seconds before now for selecting the package contents. |
| `start_time` | Specify the start of time range to look for the incidents in.                |
| `end_time`   | Specify the end of time range to look for the incidents in.                  |

##### Options

- `CORRELATE BASIC`: The package includes the incident dumps and the incident process trace files. If the incidents share relevant correlation keys, then more incidents are included automatically.

- `CORRELATE TYPICAL`: The package includes the incident dumps and all trace files that were modified in a time window around each incident. If the incidents share relevant correlation keys, or occurred in a time window around the main incidents, then more incidents are included automatically.

- `CORRELATE ALL`: The package includes the incident dumps and all trace files that were modified between the first selected incident and the last selected incident. If the incidents occurred in the same time range, then more incidents are included automatically.

- `MANIFEST file_spec`: Generates the XML format package manifest file.

- `KEYFILE file_spec`: Generates the remote key file.

**Note:**

- If you do not specify package contents, such as incident, problem, and so on, then Oracle Trace File Analyzer creates an empty package.

  You can add files and incidents later.

- If you do not specify the correlation level, then Oracle Trace File Analyzer uses the default level.

- The default is normally **TYPICAL**, but you can change using the `IPS SET CONFIGURATION`  command.

Example E-22 tfactl ips CREATE PACKAGE

    $ tfactl ips create package incident 861

    $ tfactl ips create package time '2006-12-31 23:59:59.00 -07:00' to '2007-01-01 01:01:01.00 -07:00'

**Parent topic:** tfactl ips

#### E.4.6.8 tfactl ips DELETE PACKAGE

Use the `tfactl ips DELETE PACKAGE`  command to drop a package and its contents from the Automatic Diagnostic Repository.

##### Syntax

    tfactl ips DELETE PACKAGE package_id

##### Parameters

Table E-31 tfactl ips DELETE PACKAGE Command Parameters

| Parameter    | Description                              |
|:-------------|:-----------------------------------------|
| `package_id` | Specify the ID of the package to delete. |

Example E-23 tfactl ips DELETE PACKAGE

    $ tfactl ips delete package 12

**Parent topic:** tfactl ips

#### E.4.6.9 tfactl ips FINALIZE PACKAGE

Use the `tfactl ips FINALIZE PACKAGE`  command to get a package ready for shipping by automatically including correlated contents.

##### Syntax

    tfactl ips FINALIZE PACKAGE package_id

Example E-24 tfactl ips FINALIZE PACKAGE

    $ tfactl ips finalize package 12

**Parent topic:** tfactl ips

#### E.4.6.10 tfactl ips GENERATE PACKAGE

Use the `tfactl ips GENERATE PACKAGE`  command to create a physical package (`zip` file) in the target directory.

##### Syntax

    tfactl ips GENERATE PACKAGE package_id [IN path][COMPLETE | INCREMENTAL]

##### Parameters

Table E-32 tfactl ips GENERATE PACKAGE Command Parameters

| Parameter    | Description                                                         |
|:-------------|:--------------------------------------------------------------------|
| `package_id` | Specify the ID of the package to create physical package file for.  |
| `path`       | Specify the path where the physical package file must be generated. |

##### Options

- `COMPLETE`: (Default) The package includes all package files even if a previous package sequence was generated.

- `INCREMENTAL`: The package includes only the files that have been added or changed since the last package was generated.

**Note:**

If no target path is specified, then Oracle Trace File Analyzer generates the physical package file in the current working directory.

Example E-25 tfactl ips GENERATE PACKAGE

    $ tfactl ips generate package 12 in /tmp

**Parent topic:** tfactl ips

#### E.4.6.11 tfactl ips GET MANIFEST

Use the `tfactl ips GET MANIFEST`  command to extract the manifest from a package file and view it.

##### Syntax

    tfactl ips GET MANIFEST FROM FILE file

##### Parameters

Table E-33 tfactl ips GET MANIFEST FROM FILE Command Parameters

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `file`    | Specify the external file with file name and full path. |

Example E-26 tfactl ips GET MANIFEST

    $ tfactl ips get manifest from file /tmp/IPSPKG_200704130121_COM_1.zip

**Parent topic:** tfactl ips

#### E.4.6.12 tfactl ips GET METADATA

Use the `tfactl ips GET METADATA`  command to extract the metadata XML document from a package file and view it.

##### Syntax

    tfactl ips GET METADATA [FROM FILE file | FROM ADR]

##### Parameters

Table E-34 tfactl ips GET METADATA Command Parameters

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `file`    | Specify the external file with file name and full path. |

Example E-27 tfactl ips GET METADATA

    $ tfactl ips get metadata from file /tmp/IPSPKG_200704130121_COM_1.zip

**Parent topic:** tfactl ips

#### E.4.6.13 tfactl ips GET REMOTE KEYS

Use the `tfactl ips GET REMOTE KEYS`  command to create a file with keys matching incidents in a specific package.

##### Syntax

    tfactl ips GET REMOTE KEYS FILE file_spec PACKAGE package_id

##### Parameters

Table E-35 tfactl ips GET REMOTE KEYS FILE Command Parameters

| Parameter    | Description                                                       |
|:-------------|:------------------------------------------------------------------|
| `file_spec`  | Specify the file with file name and full path (full or relative). |
| `package_id` | Specify the ID of the package to get keys for.                    |

Example E-28 tfactl ips GET REMOTE KEYS

    $ tfactl ips get remote keys file /tmp/key_file.txt package 12

**Parent topic:** tfactl ips

#### E.4.6.14 tfactl ips PACK

Use the `tfactl ips PACK` command to create a package and immediately generate the physical package.

##### Syntax

    tfactl ips PACK [INCIDENT incid | PROBLEM prob_id | PROBLEMKEY prob_key | SECONDS seconds | TIME start_time TO end_time]
    [CORRELATE BASIC | TYPICAL | ALL] [MANIFEST file_spec] [KEYFILE file_spec]

##### Parameters

Table E-36 tfactl ips PACK Command Parameters

| Parameter    | Description                                                                               |
|:-------------|:------------------------------------------------------------------------------------------|
| `incid`      | Specify the ID of the incident to use for selecting the package contents.                 |
| `prob_id`    | Specify the ID of the problem to use for selecting the package contents.                  |
| `prob_key`   | Specify the problem key to use for selecting the package contents.                        |
| `seconds`    | Specify the number of seconds before the current time for selecting the package contents. |
| `start_time` | Specify the start of time range to look for the incidents in.                             |
| `end_time`   | Specify the end of time range to look for the incidents in.                               |
| `path`       | Specify the path where the physical package file must be generated.                       |

##### Options

- `CORRELATE BASIC`: The package includes the incident dumps and the incident process trace files. If the incidents share relevant correlation keys, then more incidents are included automatically.

- `CORRELATE TYPICAL`: The package includes the incident dumps and all trace files that were modified in a time window around each incident. If the incidents share relevant correlation keys, or occurred in a time window around the main incidents, then more incidents are included automatically.

- `CORRELATE ALL`: The package includes the incident dumps and all trace files that were modified between the first selected incident and the last selected incident. If the incidents occurred in the same time range, then more incidents are included automatically.

- `MANIFEST file_spec`: Generate the XML format package manifest file.

- `KEYFILE file_spec`: Generate remote key file.

**Note:**

If you do not specify package contents, such as incident, problem, and so on, then Oracle Trace File Analyzer creates an empty package.

You can add files and incidents later.

If you do not specify the correlation level, then Oracle Trace File Analyzer uses the default level.

The default is normally **TYPICAL**, but you can change using the `IPS SET CONFIGURATION`  command.

Example E-29 tfactl ips PACK

    $ tfactl ips pack incident 861

    $ tfactl ips pack time '2006-12-31 23:59:59.00 -07:00' to '2007-01-01 01:01:01.00 -07:00'

**Parent topic:** tfactl ips

#### E.4.6.15 tfactl ips REMOVE

Use the `tfactl ips REMOVE`  command to remove incidents from an existing package.

##### Syntax

The incidents remain associated with the package, but not included in the physical package file.

    tfactl ips REMOVE [INCIDENT incid | PROBLEM prob_id | PROBLEMKEY prob_key] PACKAGE package_id

##### Parameters

Table E-37 tfactl ips REMOVE Command Parameters

| Parameter  | Description                                                    |
|:-----------|:---------------------------------------------------------------|
| `incid`    | Specify the ID of the incident to add to the package contents. |
| `prob_id`  | Specify the ID of the problem to add to the package contents.  |
| `prob_key` | Specify the problem key to add to the package contents.        |

Example E-30 tfactl ips REMOVE

    $ tfactl ips remove incident 22 package 12

**Parent topic:** tfactl ips

#### E.4.6.16 tfactl ips REMOVE FILE

Use the `tfactl ips REMOVE FILE`  command to remove a file from an existing package.

##### Syntax

The file must be in the same `ADR_BASE`  as the package. The file remains associated with the package, but not included in the physical package file.

    tfactl ips REMOVE FILE file_spec PACKAGE pkgid

##### Parameters

Table E-38 tfactl ips REMOVE FILE Command Parameters

| Parameter    | Description                                                       |
|:-------------|:------------------------------------------------------------------|
| `file_spec`  | Specify the file with file name and full path (full or relative). |
| `package_id` | Specify the ID of the package to remove the file from.            |

Example E-31 tfactl ips REMOVE FILE

    $ tfactl ips remove file ADR_HOME/trace/mydb1_ora_13579.trc package 12

**Parent topic:** tfactl ips

#### E.4.6.17 tfactl ips SET CONFIGURATION

Use the `tfactl ips SET CONFIGURATION`  command to change the value of an Incident Packaging Service configuration parameter.

##### Syntax

    tfactl ips SET CONFIGURATION parameter_id value

##### Parameters

Table E-39 tfactl ips SET CONFIGURATION Command Parameters

| Parameter      | Description                                |
|:---------------|:-------------------------------------------|
| `parameter_id` | Specify the ID of the parameter to change. |
| `value`        | Specify the new value for the parameter.   |

Example E-32 tfactl ips SET CONFIGURATION

    $ tfactl ips set configuration 6 2

**Parent topic:** tfactl ips

#### E.4.6.18 tfactl ips SHOW CONFIGURATION

Use the `tfactl ips SHOW CONFIGURATION`  command to view the current Incident Packaging Service settings.

##### Syntax

    tfactl ips SHOW CONFIGURATION parameter_id

Example E-33 tfactl ips SHOW CONFIGURATION

    $ tfactl ips show configuration

    Multiple ORACLE HOMES were found, please select one ...

    option[0] /scratch/app/oradb/product/11.2.0/dbhome_11204
    option[1] /scratch/app/11.2.0.4/grid

    Pls select an ORACLE_HOME to be used for the ADRCI binary [0] ?0
    /scratch/app/oradb/product/11.2.0/dbhome_11204 was selected

    Multiple ADR basepaths were found, please select one ...

    ( ) option[0] /scratch/app/oradb
    ( ) option[1] /scratch/app/oragrid

    Pls select an ADR basepath [0..1] ?0
    /scratch/app/oradb was selected

    Multiple ADR homepaths were found for /scratch/app/oradb, please select one ...

    ( ) option[0] diag/rdbms/racone/racone_2
    ( ) option[1] diag/rdbms/rdb11204/rdb112041
    ( ) option[2] diag/rdbms/ogg11204/ogg112041
    ( ) option[3] diag/rdbms/apxcmupg/apxcmupg_1
    ( ) option[4] diag/rdbms/apxcmupg/apxcmupg_2
        option[5] Done

    Pls select a homepath [5] ?0
    diag/rdbms/racone/racone_2 was selected

    PARAMETER INFORMATION:
       PARAMETER_ID           1
       NAME                   CUTOFF_TIME
       DESCRIPTION            Maximum age for an incident to be considered for inclusion
       UNIT                   Days
       VALUE                  90
       DEFAULT_VALUE          90
       MINIMUM                1
       MAXIMUM                4294967295
       FLAGS                  0

    PARAMETER INFORMATION:
       PARAMETER_ID           2
       NAME                   NUM_EARLY_INCIDENTS
       DESCRIPTION            How many incidents to get in the early part of the range
       UNIT                   Number
       VALUE                  3
       DEFAULT_VALUE          3
       MINIMUM                1
       MAXIMUM                4294967295
       FLAGS                  0

    PARAMETER INFORMATION:
       PARAMETER_ID           3
       NAME                   NUM_LATE_INCIDENTS
       DESCRIPTION            How many incidents to get in the late part of the range
       UNIT                   Number
       VALUE                  3
       DEFAULT_VALUE          3
       MINIMUM                1
       MAXIMUM                4294967295
       FLAGS                  0

    PARAMETER INFORMATION:
       PARAMETER_ID           4
       NAME                   INCIDENT_TIME_WINDOW
       DESCRIPTION            Incidents this close to each other are considered correlated
       UNIT                   Minutes
       VALUE                  5
       DEFAULT_VALUE          5
       MINIMUM                1
       MAXIMUM                4294967295
       FLAGS                  0

    PARAMETER INFORMATION:
       PARAMETER_ID           5
       NAME                   PACKAGE_TIME_WINDOW
       DESCRIPTION            Time window for content inclusion is from x hours before first included incident to x hours after last incident
       UNIT                   Hours
       VALUE                  24
       DEFAULT_VALUE          24
       MINIMUM                1
       MAXIMUM                4294967295
       FLAGS                  0

    PARAMETER INFORMATION:
       PARAMETER_ID           6
       NAME                   DEFAULT_CORRELATION_LEVEL
       DESCRIPTION            Default correlation level for packages
       UNIT                   Number
       VALUE                  2
       DEFAULT_VALUE          2
       MINIMUM                1
       MAXIMUM                4
       FLAGS                  0

**Parent topic:** tfactl ips

#### E.4.6.19 tfactl ips SHOW FILES

Use the `tfactl ips SHOW FILES`  command to view the files included in a specific package.

##### Syntax

    tfactl ips SHOW FILES PACKAGE package_id

Example E-34 tfactl ips SHOW FILES

    $ tfactl ips show files package 12

**Parent topic:** tfactl ips

#### E.4.6.20 tfactl ips SHOW INCIDENTS

Use the `tfactl ips SHOW INCIDENTS`  command to view the incidents included in a specific package.

##### Syntax

    tfactl ips SHOW INCIDENTS PACKAGE package_id

Example E-35 tfactl ips SHOW INCIDENTS

    $ tfactl ips show incidents package 12

**Parent topic:** tfactl ips

#### E.4.6.21 tfactl ips SHOW PROBLEMS

Use the `tfactl ips SHOW PROBLEMS`  command to view the problems for the current Automatic Diagnostic Repository home.

##### Syntax

    tfactl ips SHOW PROBLEMS

Example E-36 tfactl ips SHOW PROBLEMS

    tfactl ips show problems

    Multiple ADR basepaths were found, please select one ...

    ( ) option[0] /scratch/app/oradb
    ( ) option[1] /scratch/app/oragrid

    Pls select an ADR basepath [0..1] ?0
    /scratch/app/oradb was selected

    ADR Home = /scratch/app/oradb/diag/rdbms/racone/racone_2:
    *************************************************************************
    0 rows fetched

    ADR Home = /scratch/app/oradb/diag/rdbms/rdb11204/rdb112041:
    *************************************************************************
    PROBLEM_ID           PROBLEM_KEY                                                 LAST_INCIDENT        LASTINC_TIME
    -------------------- ----------------------------------------------------------- -------------------- ----------------------------------------
    2                    ORA 700 [kgerev1]                                           42605                2016-07-05 07:53:28.578000 -07:00
    1                    ORA 600                                                     42606                2016-07-05 07:53:30.427000 -07:00

    ADR Home = /scratch/app/oradb/diag/rdbms/ogg11204/ogg112041:
    *************************************************************************
    PROBLEM_ID           PROBLEM_KEY                                                 LAST_INCIDENT        LASTINC_TIME
    -------------------- ----------------------------------------------------------- -------------------- ----------------------------------------
    3                    ORA 4030                                                    51504                2017-09-26 10:03:03.922000 -07:00
    2                    ORA 700 [kgerev1]                                           54401                2017-09-26 10:03:10.371000 -07:00
    1                    ORA 600                                                     54402                2017-09-26 10:03:11.446000 -07:00
    6                    ORA 600 [gc_test_error]                                     54691                2017-10-23 03:03:40.599000 -07:00
    5                    ORA 4031                                                    64277                2017-12-13 04:48:16.035000 -08:00
    4                    ORA 7445                                                    96286                2018-05-29 08:26:11.326000 -07:00

    ADR Home = /scratch/app/oradb/diag/rdbms/apxcmupg/apxcmupg_1:
    *************************************************************************
    0 rows fetched

    ADR Home = /scratch/app/oradb/diag/rdbms/apxcmupg/apxcmupg_2:
    *************************************************************************
    0 rows fetched

**Parent topic:** tfactl ips

#### E.4.6.22 tfactl ips SHOW PACKAGE

Use the `tfactl ips SHOW PACKAGE`  command to view the details of a specific package.

##### Syntax

    tfactl ips SHOW PACKAGE package_id [BASIC | BRIEF | DETAIL]

**Note:**

It is possible to specify the level of detail to use with this command.

`BASIC` :  Shows a minimal amount of information. It is the default when no package ID is specified.

`BRIEF` :  Shows a more extensive amount of information. It is the default when a package ID is specified.

`DETAIL` :  Shows the same information as `BRIEF`, and also some package history and information on included incidents and files.

Example E-37 tfactl ips SHOW PACKAGE

    $ tfactl ips show package

    Multiple ADR basepaths were found, please select one ...

    ( ) option[0] /scratch/app/oradb
    ( ) option[1] /scratch/app/oragrid

    Pls select an ADR basepath [0..1] ?0
    /scratch/app/oradb was selected

    Multiple ADR homepaths were found for /scratch/app/oradb, please select one ...

    ( ) option[0] diag/rdbms/racone/racone_2
    ( ) option[1] diag/rdbms/rdb11204/rdb112041
    ( ) option[2] diag/rdbms/ogg11204/ogg112041
    ( ) option[3] diag/rdbms/apxcmupg/apxcmupg_1
    ( ) option[4] diag/rdbms/apxcmupg/apxcmupg_2
        option[5] Done

    Pls select a homepath [5] ?1
    diag/rdbms/rdb11204/rdb112041 was selected

       PACKAGE_ID             1
       PACKAGE_NAME           IPSPKG_20160731165615
       PACKAGE_DESCRIPTION
       DRIVING_PROBLEM        N/A
       DRIVING_PROBLEM_KEY    N/A
       DRIVING_INCIDENT       N/A
       DRIVING_INCIDENT_TIME  N/A
       STATUS                 Generated (4)
       CORRELATION_LEVEL      Typical (2)
       PROBLEMS               0 main problems, 0 correlated problems
       INCIDENTS              0 main incidents, 0 correlated incidents
       INCLUDED_FILES         27

       PACKAGE_ID             2
       PACKAGE_NAME           IPSPKG_20160731170111
       PACKAGE_DESCRIPTION
       DRIVING_PROBLEM        N/A
       DRIVING_PROBLEM_KEY    N/A
       DRIVING_INCIDENT       N/A
       DRIVING_INCIDENT_TIME  N/A
       STATUS                 Generated (4)
       CORRELATION_LEVEL      Typical (2)
       PROBLEMS               0 main problems, 0 correlated problems
       INCIDENTS              0 main incidents, 0 correlated incidents
       INCLUDED_FILES         27

       PACKAGE_ID             3
       PACKAGE_NAME           ORA700kge_20160731211334
       PACKAGE_DESCRIPTION
       DRIVING_PROBLEM        2
       DRIVING_PROBLEM_KEY    ORA 700 [kgerev1]
       DRIVING_INCIDENT       42605
       DRIVING_INCIDENT_TIME  N/A
       STATUS                 Generated (4)
       CORRELATION_LEVEL      Typical (2)
       PROBLEMS               2 main problems, 0 correlated problems
       INCIDENTS              2 main incidents, 0 correlated incidents
       INCLUDED_FILES         84

       PACKAGE_ID             4
       PACKAGE_NAME           IPSPKG_20160801203518
       PACKAGE_DESCRIPTION
       DRIVING_PROBLEM        N/A
       DRIVING_PROBLEM_KEY    N/A
       DRIVING_INCIDENT       N/A
       DRIVING_INCIDENT_TIME  N/A
       STATUS                 Generated (4)
       CORRELATION_LEVEL      Typical (2)
       PROBLEMS               0 main problems, 0 correlated problems
       INCIDENTS              0 main incidents, 0 correlated incidents
       INCLUDED_FILES         27

    $ tfactl ips show package 4 detail

    Multiple ADR basepaths were found, please select one ...

    ( ) option[0] /scratch/app/oradb
    ( ) option[1] /scratch/app/oragrid

    Pls select an ADR basepath [0..1] ?0
    /scratch/app/oradb was selected

    Multiple ADR homepaths were found for /scratch/app/oradb, please select one ...

    ( ) option[0] diag/rdbms/racone/racone_2
    ( ) option[1] diag/rdbms/rdb11204/rdb112041
    ( ) option[2] diag/rdbms/ogg11204/ogg112041
    ( ) option[3] diag/rdbms/apxcmupg/apxcmupg_1
    ( ) option[4] diag/rdbms/apxcmupg/apxcmupg_2
        option[5] Done

    Pls select a homepath [5] ?1
    diag/rdbms/rdb11204/rdb112041 was selected

    DETAILS FOR PACKAGE 4:
       PACKAGE_ID             4
       PACKAGE_NAME           IPSPKG_20160801203518
       PACKAGE_DESCRIPTION
       DRIVING_PROBLEM        N/A
       DRIVING_PROBLEM_KEY    N/A
       DRIVING_INCIDENT       N/A
       DRIVING_INCIDENT_TIME  N/A
       STATUS                 Generated (4)
       CORRELATION_LEVEL      Typical (2)
       PROBLEMS               0 main problems, 0 correlated problems
       INCIDENTS              0 main incidents, 0 correlated incidents
       INCLUDED_FILES         27
       SEQUENCES              Last 1, last full 1, last base 0
       UNPACKED               FALSE
       CREATE_TIME            2016-08-01 20:35:18.684231 -07:00
       UPDATE_TIME            N/A
       BEGIN_TIME             2016-08-01 13:59:04.000000 -07:00
       END_TIME               2016-08-01 20:34:50.000000 -07:00
       FLAGS                  0

    HISTORY FOR PACKAGE 4:
       SEQUENCE               1
       BASE_SEQUENCE          1
       MODE                   Complete (0)
       STATUS                 Generated (4)
       FILENAME               /scratch/app/oragrid/tfa/repository/suptools/srdc/user_oradb/IPSPKG_20160801203518_COM_1.zip
       ARCHIVE_TIME           2016-08-01 20:35:21.899095 -07:00
       UPLOAD_TIME            N/A
       UNPACK_TIME            N/A
       FORCE                  FALSE
       GENERATE_FLAGS         0
       UNPACK_FLAGS           0

    MAIN INCIDENTS FOR PACKAGE 4:
    CORRELATED INCIDENTS FOR PACKAGE 4:

    FILES FOR PACKAGE 4:
       FILE_ID                1
       FILE_LOCATION          <ADR_HOME>/trace
       FILE_NAME              alert_rdb112041.log
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2087
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_CONFIGURATION.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2088
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_PACKAGE.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2089
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_PACKAGE_INCIDENT.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2090
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_PACKAGE_FILE.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2091
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_PACKAGE_HISTORY.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2092
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_FILE_METADATA.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2093
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              IPS_FILE_COPY_LOG.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2094
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_ACTION_DEF.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2095
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_ACTION_PARAMETER_DEF.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2096
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_ACTION.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2097
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_ACTION_PARAMETER.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2098
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_INCIDENT_TYPE.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2099
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              DDE_USER_INCIDENT_ACTION_MAP.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2100
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              INCIDENT.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2101
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              INCCKEY.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2102
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              INCIDENT_FILE.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2103
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              PROBLEM.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2104
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              HM_RUN.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2105
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/export
       FILE_NAME              EM_USER_ACTIVITY.dmp
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2106
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1
       FILE_NAME              config.xml
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2107
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/opatch
       FILE_NAME              opatch.log
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2108
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1/opatch
       FILE_NAME              opatch.xml
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2109
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1
       FILE_NAME              metadata.xml
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2110
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1
       FILE_NAME              manifest_4_1.xml
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2111
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1
       FILE_NAME              manifest_4_1.html
       LAST_SEQUENCE          1
       EXCLUDE                Included

       FILE_ID                2112
       FILE_LOCATION          <ADR_HOME>/incpkg/pkg_4/seq_1
       FILE_NAME              manifest_4_1.txt
       LAST_SEQUENCE          1
       EXCLUDE                Included

**Parent topic:** tfactl ips

#### E.4.6.23 tfactl ips UNPACK FILE

Use the `tfactl ips UNPACK FILE`  command to unpack a physical file into a specific path.

##### Syntax

Running the following command automatically creates a valid `ADR_HOME`  structure. The path must exist and be writable.

    tfactl ips UNPACK FILE file_spec [INTO path]

##### Parameters

Table E-40 tfactl ips UNPACK FILE Command Parameters

| Parameter   | Description                                                          |
|:------------|:---------------------------------------------------------------------|
| `file_spec` | Specify the file with file name and full path.                       |
| `path`      | Specify the path where the physical package file should be unpacked. |

Example E-38 tfactl ips UNPACK FILE

    $ tfactl ips unpack file /tmp/IPSPKG_20061026010203_COM_1.zip into /tmp/newadr

**Parent topic:** tfactl ips

#### E.4.6.24 tfactl ips UNPACK PACKAGE

Use the `tfactl ips UNPACK PACKAGE`  command to unpack physical files in the current directory into a specific path, if they match the package name.

##### Syntax

Running the following command automatically creates a valid `ADR_HOME` structure. The path must exist and be writable.

    tfactl ips UNPACK PACKAGE pkg_name [INTO path]

##### Parameters

Table E-41 tfactl ips UNPACK PACKAGE Command Parameters

| Parameter  | Description                                                           |
|:-----------|:----------------------------------------------------------------------|
| `pkg_name` | Specify the name of the package.                                      |
| `path`     | Specify the path where the physical package files should be unpacked. |

Example E-39 tfactl ips UNPACK PACKAGE

    $ tfactl ips unpack package IPSPKG_20061026010203 into /tmp/newadr

**Parent topic:** tfactl ips

#### E.4.6.25 tfactl ips USE REMOTE KEYS

Use the `tfactl ips USE REMOTE KEYS`  command to add incidents matching the keys in a specific file to a specific package.

##### Syntax

    tfactl ips USE REMOTE KEYS FILE file_spec PACKAGE package_id

##### Parameters

Table E-42 tfactl ips USE REMOTE KEYS Command Parameters

| Parameter    | Description                                            |
|:-------------|:-------------------------------------------------------|
| `file_spec`  | Specify the file with file name and full path.         |
| `package_id` | Specify the ID of the package to add the incidents to. |

Example E-40 tfactl ips USE REMOTE KEYS

    $ tfactl ips use remote keys file /tmp/key_file.txt package 12

**Parent topic:** tfactl ips

### E.4.7 tfactl managelogs

Use the `tfactl managelogs`  command to manage Automatic Diagnostic Repository log and trace files.

#### Syntax

    tfactl managelogs
    [-purge [[-older nm|h|d] | [-gi] | [-database all|d1,d2,...]]]
    [-show [usage|variation] [[-older nd] | [-gi] | [-database all|d1,d2,...]]]

#### Parameters

Table E-43 tfactl managelogs Purge Options

| Purge Option | Description                                                                                                                       |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------|
| `-older`     | Time period for purging logs.                                                                                                     |
| `-gi`        | Purges Oracle Grid Infrastructure logs (all Automatic Diagnostic Repository homes under `GIBASE/diag`  and `crsdata (cvu dirs)`). |
| `-database`  | Purges Oracle database logs (Default is all, else provide a list).                                                                |
| `-dryrun`    | Estimates logs cleared by `purge`  command.                                                                                       |

Table E-44 tfactl managelogs Show Options

| Show Option | Description                                                                       |
|:------------|:----------------------------------------------------------------------------------|
| `-older`    | Time period for change in log volume.                                             |
| `-gi`       | Space utilization under `GIBASE`.                                                 |
| `-database` | Space utilization for Oracle database logs (Default is all, else provide a list). |

Example E-41 tfactl managelogs

    $ tfactl managelogs -show usage -gi

    Output from host : myhost
    ------------------------------

    .----------------------------------------------------------------------------.
    |                          Grid Infrastructure Usage                         |
    +----------------------------------------------------------------+-----------+
    | Location                                                       | Size      |
    +----------------------------------------------------------------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/alert                 | 2.51 MB   |
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/incident              | 4.00 KB   |
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/trace                 | 8.82 MB   |
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/cdump                 | 4.00 KB   |
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/hm                    | 4.00 KB   |
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/alert        | 83.32 MB  |
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/incident     | 4.00 KB   |
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/trace        | 516.38 MB |
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/cdump        | 4.00 KB   |
    +----------------------------------------------------------------+-----------+
    | Total                                                          | 611.05 MB |
    '----------------------------------------------------------------+-----------'

    $ tfactl managelogs -show variation  -older 2h -gi

    Output from host : myhost
    ------------------------------
    2018-09-12 21:16:40: INFO Checking space variation for 2 hours

    2018-09-12 21:16:40: INFO Space is calculated in bytes [without round off]

    2018-09-12 21:16:41: INFO Snapshot considered for size comparision was created at 12-Sep-2018 18:55:29 PDT [2 hours ago].

    .----------------------------------------------------------------------------------------.
    |                              Grid Infrastructure Variation                             |
    +----------------------------------------------------------------+-----------+-----------+
    | Directory                                                      | Old Size  | New Size  |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/trace        | 516.29 MB | 516.38 MB |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/incident     | 4.00 KB   | 4.00 KB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/cdump        | 4.00 KB   | 4.00 KB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/hm                    | 4.00 KB   | 4.00 KB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/trace                 | 8.82 MB   | 8.82 MB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/alert                 | 2.51 MB   | 2.51 MB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/incident              | 4.00 KB   | 4.00 KB   |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/tnslsnr/myhost/listener/alert        | 83.16 MB  | 83.33 MB  |
    +----------------------------------------------------------------+-----------+-----------+
    | /scratch/app/oragrid/diag/asm/+asm/+ASM1/cdump                 | 4.00 KB   | 4.00 KB   |
    '----------------------------------------------------------------+-----------+-----------'

**Parent topic:** Running Diagnostic Collection Commands

### E.4.8 tfactl purge

Use the `tfactl purge` command to delete diagnostic collections from the Oracle Trace File Analyzer repository that are older than a specific time.

#### Syntax

    tfactl purge -older n[h|d] [-force]

Example E-42 tfactl purge

To remove file(s) older than 30 days:

    $ tfactl purge -older 30d

To remove file(s) older than 10 hours:

    $ tfactl purge -older 10h

**Parent topic:** Running Diagnostic Collection Commands
