Use the custom collection options to change the diagnostic collections from the default.

- Adjusting the Diagnostic Data Collection Period
  Oracle Trace File Analyzer trims and collects any important logs updated in the past 12 hours.
- Collecting from Specific Nodes
- Collecting from Specific Components
- Collecting from Specific Directories
- Changing the Collection Name
- Preventing Copying Zip Files and Trimming Files
- Performing Silent Collection
- Preventing Collecting Core Files
- Collecting Incident Packaging Service (IPS) Packages
  Incident Packaging Service packages details of problems stored by Oracle Database in ADR for later diagnosis.

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)

### 18.1 Adjusting the Diagnostic Data Collection Period

Oracle Trace File Analyzer trims and collects any important logs updated in the past 12 hours.

If you know that you only want logs for a smaller window, then you can cut this collection period. Cutting the collection period helps you make collections as small and quick as possible.

There are four different ways you can specify the period for collection:

Table 18-1 Ways to Specify the Collection Period

| Command                                                          | Description                                                                                                                                                                                  |
|:-----------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tfactl diagcollect -last ``n`` h|d`                             | Collects since the previous n hours or days.                                                                                                                                                 |
| `tfactl diagcollect -from “``yyyy-mm-dd``”`                      | Collects from the date and optionally time specified.<br>Valid date and time formats:<br>`"Mon/dd/yyyy hh:mm:ss"`<br>`"yyyy-mm-dd hh:mm:ss"`<br>`"yyyy-mm-ddThh:mm:ss"`<br>`"yyyy-mm-dd"`    |
| `tfactl diagcollect –from "``yyyy-mm-dd``" -to "``yyyy-mm-dd``"` | Collects between the date and optionally time specified.<br>Valid date and time formats:<br>`"Mon/dd/yyyy hh:mm:ss"`<br>`"yyyy-mm-dd hh:mm:ss"`<br>`"yyyy-mm-ddThh:mm:ss"`<br>`"yyyy-mm-dd"` |
| `tfactl diagcollect -for “``yyyy-mm-dd``”`                       | Collects for the specified date.<br>Valid date formats:<br>`"Mon/dd/yyyy"`<br>`"yyyy-mm-dd"`                                                                                                 |

**Parent topic:** Performing Custom Collections

### 18.2 Collecting from Specific Nodes

#### To collect from specific nodes:

1.  To collect from specific nodes:
        tfactl diagcollect –node list of nodes

    For example:
        $ tfactl diagcollect -last 1d -node myserver65

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.3 Collecting from Specific Components

#### To collect from specific components:

1.  To collect from specific components:
        tfactl diagcollect component

    For example:

    To trim and collect all files from the databases `hrdb` and `fdb` in the last 1 day:
        $ tfactl –diagcollect –database hrdb,fdb –last 1d

    To trim and collect all CRS files, operating system logs, and CHMOS/OSW data from `node1` and `node2` updated in the last 6 hours:
        $ tfactl diagcollect -crs -os -node node1,node2 -last 6h

    To trim and collect all Oracle ASM logs from `node1` updated between from and to time:
        $ tfactl diagcollect -asm -node node1 -from "2016-08-15" -to "2016-08-17"

    Following are the available component options.
    Table 18-2 Component Options

    | Component Option             | Description                                                                |
    |:-----------------------------|:---------------------------------------------------------------------------|
    | `-database ``database_names` | Collects database logs from databases specified in a comma-separated list. |
    | `-asm`                       | Collects Oracle ASM logs.                                                  |
    | `-crsclient`                 | Collects Client Logs that are under `GIBASE/diag/clients`.                 |
    | `-dbclient`                  | Collects Client Logs that are under `DB ORABASE/diag/clients`.             |
    | `-dbwlm`                     | Collects DBWLM logs.                                                       |
    | `-tns`                       | Collects TNS logs.                                                         |
    | `-rhp`                       | Collects RHP logs.                                                         |
    | `-procinfo`                  | Collects `Gathers stack` and `fd` from `/proc` for all processes.          |
    | `-afd`                       | Collects AFD logs.                                                         |
    | `-crs`                       | Collects CRS logs.                                                         |
    | `-wls`                       | Collects WLS logs.                                                         |
    | `-emagent`                   | Collects EMAGENT logs.                                                     |
    | `-oms`                       | Collects OMS logs.                                                         |
    | `-ocm`                       | Collects OCM logs.                                                         |
    | `-emplugins`                 | Collects EMPLUGINS logs.                                                   |
    | `-em`                        | Collects EM logs.                                                          |
    | `-acfs`                      | Collects ACFS logs and data.                                               |
    | `-install`                   | Collects Oracle Installation related files.                                |
    | `-cfgtools`                  | Collects CFGTOOLS logs.                                                    |
    | `-os`                        | Collects operating system files such as `/var/log/messages`.               |
    | `-ashhtml`                   | Collects Generate ASH HTML Report.                                         |
    | `-ashtext`                   | Collects Generate ASH TEXT Report.                                         |
    | `-awrhtml`                   | Collects AWRHTML logs.                                                     |

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.4 Collecting from Specific Directories

Oracle Trace File Analyzer discovers all Oracle diagnostics and collects relevant files based on the type and last time updated.

If you want to collect other files, then you can specify extra directories. Oracle Trace File Analyzer collects only the files updated in the relevant time range (12 hours by default).

You can configure collection of all files irrespective of the time last updated. Configure on a directory by directory basis using the `-collectall` option.

#### To collect from specific directories:

1.  To include all files updated in the last 12 hours:
        tfactl diagcollect –collectdir dir1,dir2,...dirn

    For example:

    To trim and collect all CRS files updated in the last 12 hours as well as all files from `/tmp_dir1` and `/tmp_dir2` at the initiating node:
        $ tfactl diagcollect –crs –collectdir /tmp_dir1,/tmpdir_2
2.  To configure Oracle Trace File Analyzer to collect all files from a directory, first configure it with the `-collectall` option:
        $ tfactl add dir -collectall

    or

        tfactl modify dir -collectall

    Start a diagnostic collection using the `-collectalldirs` option:
        $ tfactl diagcollect -collectalldirs

    **Note:**

    If the `-collectalldirs` option is not used normal, then the file type, name, and time range restrictions are applied.

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.5 Changing the Collection Name

Oracle Trace File Analyzer zips collections and puts the zip files in the repository directory, using the following naming format:

    repository/collection_date_time/node_all/node.tfa_date_time.zip

You must only change the name of the zipped files using the following options. Manually changing the file name prevents you from using collections with various Oracle Support self-service tools.

#### To change the collection name:

1.  To use your own naming to organize collections:
        –tag tagname

    The files are collected into `tagname` directory inside the repository.

    For example:
        $ tfactl diagcollect -last 1h -tag MyTagName
        Collecting data for all nodes
        ....
        ....

        Logs are being collected to: /scratch/app/crsusr/tfa/repository/MyTagName
        /scratch/app/crsusr/tfa/repository/MyTagName/host_name.tfa_Mon_Aug_22_05_26_17_PDT_2016.zip
        /scratch/app/crsusr/tfa/repository/MyTagName/host_name.tfa_Mon_Aug_22_05_26_17_PDT_2016.zip
2.  To rename the `zip` file:
        –z zip name

    For example:
        $ tfactl diagcollect -last 1h -z MyCollectionName.zip
        Collecting data for all nodes
        ....
        ....
        Logs are being collected to: /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_05_13_41_PDT_2016_node_all
        /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_05_13_41_PDT_2016_node_all/myserver65.tfa_MyCollectionName.zip
        /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_05_13_41_PDT_2016_node_all/myserver66.tfa_MyCollectionName.zip

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.6 Preventing Copying Zip Files and Trimming Files

By default, Oracle Trace File Analyzer Collector:

- Copies back all zip files from remote notes to the initiating node

- Trims files around the relevant time

#### To prevent copying zip files and trimming files:

1.  To prevent copying the zip file back to the initiating node:
        –nocopy

    For example:
        $ tfactl diagcollect -last 1d -nocopy
2.  To avoid trimming files:
        –notrim

    For example:
        $ tfactl diagcollect -last 1d -notrim

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.7 Performing Silent Collection

1.  To initiate a silent collection:
        –silent

    The `diagcollect` command is submitted as a background process.

    For example:
        $ tfactl diagcollect -last 1d -silent

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.8 Preventing Collecting Core Files

1.  To prevent core files being included:
        –nocores

    For example:
        $ tfactl diagcollect -last 1d -nocores

**Related Topics**

- [tfactl diagcollect](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections

### 18.9 Collecting Incident Packaging Service (IPS) Packages

Incident Packaging Service packages details of problems stored by Oracle Database in ADR for later diagnosis.

#### Syntax

Oracle Trace File Analyzer runs IPS to query and collect these packages.

    tfactl ips option

Table 18-3 tfactl ips Command Parameters

| Command                                                                     | Description                                                                                                                            |
|:----------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `tfactl ips`                                                                | Runs the IPS.                                                                                                                          |
| `tfactl ips show incidents`                                                 | Shows all IPS incidents.                                                                                                               |
| `tfactl ips show problems`                                                  | Shows all IPS problems.                                                                                                                |
| `tfactl ips show package`                                                   | Shows all IPS Packages.                                                                                                                |
| `tfactl diagcollect -ips -h`                                                | Shows all available `diagcollect` IPS options.                                                                                         |
| `tfactl diagcollect -ips`                                                   | Performs an IPS collection following prompts. You can use all the standard `diagcollect` options to limit the scope of IPS collection. |
| `tfactl diagcollect -ips -adrbasepath ``adr_base`` -adrhomepath ``adr_home` | Performs an IPS collection in silent mode.                                                                                             |
| `tfactl diagcollect -ips -incident ``incident_id`                           | Collects ADR details about a specific incident id.                                                                                     |
| `tfactl diagcollect -ips -problem ``problem_id`                             | Collect ADR details about a specific problem id.                                                                                       |

You can change the contents of the IPS package. Use the following options:

1.  Start the collection.

2.  Suspend the collection using the `-manageips` option.

    For example:

        $ tfactl diagcollect -ips -incident incident_id -manageips -node local

3.  Find the suspended collection using the `print suspendedips` option.

    For example:

        $ tfactl print suspendedips

4.  Manipulate the package.

5.  Resume the collection using the `-resumeips` option.

    For example:

        $ tfactl diagcollect -resumeips collection_id

Example 18-1 Show Incidents

    $ tfactl ips show incidents

    ADR Home = /scratch/app/crsusr/diag/clients/user_crsusr/host_622665046_106:

    *************************************************************************
    0 rows fetched

    ADR Home = /scratch/app/crsusr/diag/afdboot/user_root/host_622665046_106:

    *************************************************************************
    0 rows fetched

    ADR Home = /scratch/app/crsusr/diag/rdbms/_mgmtdb/-MGMTDB:

    *************************************************************************

    INCIDENT_ID PROBLEM_KEY CREATE_TIME

    -------------------- ----------------------------------------------------------- ----------------------------------------

    12913 ORA 700 [kskvmstatact: excessive swapping observed] 2016-06-30 14:05:48.491000 -07:00

    12914 ORA 700 [kskvmstatact: excessive swapping observed] 2016-06-30 15:06:16.545000 -07:00

    13161 ORA 445 2016-06-30 15:10:53.756000 -07:00

    ADR Home = /scratch/app/crsusr/diag/asm/+asm/+ASM1:

    *************************************************************************

    INCIDENT_ID PROBLEM_KEY CREATE_TIME

    -------------------- ----------------------------------------------------------- ----------------------------------------

    1177 ORA 445 2016-06-30 15:10:12.930000 -07:00

    ADR Home = /scratch/app/crsusr/diag/asm/user_root/host_622665046_106:

    *************************************************************************

Example 18-2 Show Problems

    $ tfactl ips show problems

    ADR Home = /scratch/app/crsusr/diag/afdboot/user_root/host_622665046_106:

    *************************************************************************

    0 rows fetched

    ADR Home = /scratch/app/crsusr/diag/rdbms/_mgmtdb/-MGMTDB:

    *************************************************************************

    PROBLEM_ID  PROBLEM_KEY LAST_INCIDENT LASTINC_TIME

    -------------------- ----------------------------------------------------------- --------------------

    1 ORA 700 [kskvmstatact: excessive swapping observed] 12914 2016-06-30 15:06:16.545000 -07:00

    2 ORA 445 13161  2016-06-30 15:10:53.756000 -07:00

    ADR Home = /scratch/app/crsusr/diag/asm/+asm/+ASM1:

    *************************************************************************

    PROBLEM_ID PROBLEM_KEY LAST_INCIDENT LASTINC_TIME

    -------------------- ----------------------------------------------------------- --------------------

    1 ORA 445 1177 2016-06-30 15:10:12.930000 -07:00

Example 18-3 Show Packages

    $ tfactl ips show package

                Multiple ADR homepaths were found for /scratch/app/crsusr, please select one ...

                ( ) option[0] diag/asmtool/user_root/host_622665046_106
                ( ) option[1] diag/asmtool/user_crsusr/host_622665046_106
                ( ) option[2] diag/clients/user_root/host_622665046_106
                ( ) option[3] diag/clients/user_crsusr/host_622665046_106
                ( ) option[4] diag/afdboot/user_root/host_622665046_106
                ( ) option[5] diag/rdbms/_mgmtdb/-MGMTDB
                    option[6] Done

                Pls select a homepath [6] ?5
                diag/rdbms/_mgmtdb/-MGMTDB was selected

                   PACKAGE_ID             1
                   PACKAGE_NAME           ORA700kge_20160731211334
                   PACKAGE_DESCRIPTION
                   DRIVING_PROBLEM        2
                   DRIVING_PROBLEM_KEY    ORA 700 [kgerev1]
                   DRIVING_INCIDENT       42605
                   DRIVING_INCIDENT_TIME  2016-07-05 07:53:28.578000 -07:00
                   STATUS                 Generated (4)
                   CORRELATION_LEVEL      Typical (2)
                   PROBLEMS               2 main problems, 0 correlated problems
                   INCIDENTS              2 main incidents, 0 correlated incidents
                   INCLUDED_FILES         84

                   PACKAGE_ID             2
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

Example 18-4 IPS Collect

    $ tfactl diagcollect -ips

    Collecting data for the last 12 hours for this component ...
    Collecting data for all nodes
    Creating ips package in master node ...

    Multiple ADR homepaths were found for /scratch/app/crsusr, please select one or more...

    ( ) option[0] diag/asmtool/user_root/host_622665046_106
    ( ) option[1] diag/asmtool/user_crsusr/host_622665046_106
    ( ) option[2] diag/clients/user_root/host_622665046_106
    ( ) option[3] diag/clients/user_crsusr/host_622665046_106
    ( ) option[4] diag/afdboot/user_root/host_622665046_106
    ( ) option[5] diag/rdbms/_mgmtdb/-MGMTDB
        option[6] Done

    Pls select a homepath [6] ?5
    diag/rdbms/_mgmtdb/-MGMTDB was selected

    Please select at least one ADR homepath.

    Multiple ADR homepaths were found for /scratch/app/crsusr, please select one or more...

    ( ) option[0] diag/asmtool/user_root/host_622665046_106
    ( ) option[1] diag/asmtool/user_crsusr/host_622665046_106
    ( ) option[2] diag/clients/user_root/host_622665046_106
    ( ) option[3] diag/clients/user_crsusr/host_622665046_106
    ( ) option[4] diag/afdboot/user_root/host_622665046_106
    (*) option[5] diag/rdbms/_mgmtdb/-MGMTDB
        option[6] Done

    Pls select a homepath [6] ?
    Trying ADR basepath /scratch/app/crsusr
    Trying to use ADR homepath diag/rdbms/_mgmtdb/-MGMTDB ...
    Submitting request to generate package for ADR homepath /scratch/app/crsusr/diag/rdbms/_mgmtdb/-MGMTDB
    Master package completed for ADR homepath /scratch/app/crsusr/diag/rdbms/_mgmtdb/-MGMTDB
    Created package 15 based on time range 2016-08-21 15:58:00.000000 -07:00 to 2016-08-22 03:58:00.000000 -07:00,
    correlation level basic
    Remote package completed for ADR homepath(s) /diag/rdbms/_mgmtdb/-MGMTDB

    Collection Id : 20160822035856myserver65

    Detailed Logging at : /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_03_58_56_PDT_2016_node_all/
    diagcollect_20160822035856_myserver65.log
    2016/08/22 03:59:40 PDT : Collection Name : tfa_Mon_Aug_22_03_58_56_PDT_2016.zip
    2016/08/22 03:59:40 PDT : Collecting diagnostics from hosts : [myserver65, myserver66]
    2016/08/22 03:59:40 PDT : Getting list of files satisfying time range [08/21/2016 15:59:40 PDT, 08/22/2016 03:59:40 PDT]
    2016/08/22 03:59:40 PDT : Collecting additional diagnostic information...
    2016/08/22 03:59:51 PDT : Completed collection of additional diagnostic information...
    2016/08/22 03:59:51 PDT : Completed Local Collection
    2016/08/22 03:59:51 PDT : Remote Collection in Progress...
    .---------------------------------------.
    |           Collection Summary          |
    +------------+-----------+-------+------+
    | Host       | Status    | Size  | Time |
    +------------+-----------+-------+------+
    | myserver66 | Completed | 254kB |  16s |
    | myserver65 | Completed | 492kB |  11s |
    '------------+-----------+-------+------'

    Logs are being collected to: /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_03_58_56_PDT_2016_node_all
    /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_03_58_56_PDT_2016_node_all/
    myserver66.tfa_Mon_Aug_22_03_58_56_PDT_2016.zip
    /scratch/app/crsusr/tfa/repository/collection_Mon_Aug_22_03_58_56_PDT_2016_node_all/
    myserver65.tfa_Mon_Aug_22_03_58_56_PDT_2016.zip

**Related Topics**

- [tfactl ips](running-diagnostic-collection-commands.md)

**Parent topic:** Performing Custom Collections
