This appendix introduces monitoring the Oracle Clusterware environment and explains how you can enable dynamic debugging to troubleshoot Oracle Clusterware processing, and enable debugging and tracing for specific components and specific Oracle Clusterware resources to focus your troubleshooting efforts.

This appendix includes the following topics:

- Oracle Clusterware Diagnostic and Alert Log Data

- Diagnostics Collection Script

- Rolling Upgrade and Driver Installation Issues

- Testing Zone Delegation

- Oracle Clusterware Alerts

### Using the Cluster Resource Activity Log to Monitor Cluster Resource Failures

The cluster resource activity log provides precise and specific information about a resource failure, separate from diagnostic logs.

If an Oracle Clusterware-managed resource fails, then Oracle Clusterware logs messages about the failure in the **cluster resource activity log** located in the Grid Infrastructure Management Repository. Failures can occur as a result of a problem with a resource, a hosting node, or the network. The cluster resource activity log provides a unified view of the cause of resource failure.

Writes to the cluster resource activity log are tagged with an activity ID and any related data gets the same parent activity ID, and is nested under the parent data. For example, if Oracle Clusterware is running and you run the `crsctl stop clusterware -all` command, then all activities get activity IDs, and related activities are tagged with the same parent activity ID. On each node, the command creates sub-IDs under the parent IDs, and tags each of the respective activities with their corresponding activity ID. Further, each resource on the individual nodes creates sub-IDs based on the parent ID, creating a hierarchy of activity IDs. The hierarchy of activity IDs enables you to analyze the data to find specific activities.

For example, you may have many resources with complicated dependencies among each other, and with a database service. On Friday, you see that all of the resources are running on one node but when you return on Monday, every resource is on a different node, and you want to know why. Using the `crsctl query calog` command, you can query the cluster resource activity log for all activities involving those resources and the database service. The output provides a complete flow and you can query each sub-ID within the parent service failover ID, and see, specifically, what happened and why.

You can query any number of fields in the cluster resource activity log using filters. For example, you can query all the activities written by specific operating system users such as `root`. The output produced by the `crsctl query calog` command can be displayed in either a tabular format or in XML format.

The cluster resource activity log is an adjunct to current Oracle Clusterware logging and alert log messages.

**Note:**

Oracle Clusterware does not write messages that contain security-related information, such as log-in credentials, to the cluster activity log.

Use the following commands to manage and view the contents of the cluster resource activity log:

#### crsctl query calog

Query the cluster resource activity logs matching specific criteria.

##### Syntax

    crsctl query calog
    [-aftertime "timestamp"]
    [-beforetime "timestamp"]
    [-days "number_of_days"]
    [-duration "time_interval" | -follow]
    [-filter "filter_expression"]
    [-processname "writer_process"]
    [-processid "writer_process_id"]
    [-node "entity_hostname"]
    [-fullfmt | -xmlfmt]

##### Parameters

Table J-1 crsctl query calog Command Parameters

| Parameter                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-aftertime "``timestamp``"`              | Displays the activities logged after a specific time.<br>Specify the timestamp in the `YYYY-MM-DD HH24:MI:SS[.FF][TZH:TZM]` or `YYYY-MM-DD` or `YYYY-MM` or `YYYY` or `HH24:MI:SS[.FF][TZH:TZM]` format.<br>`TZH` and `TZM` stands for time zone hour and minute, and `FF` stands for microseconds.<br>If you specify `[TZH:TZM]`, then the `crsctl` command assumes UTC as time zone. If you do not specify `[TZH:TZM]`, then the `crsctl` command assumes the local time zone of the cluster node from where the `crsctl` command is run.<br>Use this parameter with `-beforetime` to query the activities logged at a specific time interval. |
| `-beforetime "``timestamp``"`             | Displays the activities logged before a specific time.<br>Specify the timestamp in the `YYYY-MM-DD HH24:MI:SS[.FF][TZH:TZM]` or `YYYY-MM-DD` or `YYYY-MM` or `YYYY` or `HH24:MI:SS[.FF][TZH:TZM]` format.<br>`TZH` and `TZM` stands for time zone hour and minute, and `FF` stands for microseconds.<br>If you specify `[TZH:TZM]`, then the `crsctl` command assumes UTC as time zone. If you do not specify `[TZH:TZM]`, then the `crsctl` command assumes the local time zone of the cluster node from where the `crsctl` command is run.<br>Use this parameter with `-aftertime` to query the activities logged at a specific time interval. |
| `-days "``number_of_days``"`              | Displays the activities logged in the last number of days specified. The number of days are specified as an integer value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-duration "``time_interval``" | -follow` | Use `-duration` to specify a time interval that you want to query when you use the `-aftertime` parameter.<br>Specify the timestamp in the `DD HH:MM:SS` format.<br>Use `-follow` to display a continuous stream of activities as they occur.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-filter "``filter_expression``"`         | Query any number of fields in the cluster resource activity log using the `-filter` parameter.<br>To specify multiple filters, use a comma-delimited list of filter expressions surrounded by double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-processname "``writer_process``"`       | Displays the activities logged by a specific process identified by name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-processid "``writer_process_id``"`      | Displays the activities logged by a specific process identified by ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-node "``entity_hostname``"`             | Displays the activities logged by a specific host.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-fullfmt | -xmlfmt`                      | To display cluster resource activity log data, choose full or XML format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

##### Cluster Resource Activity Log Fields

Query any number of fields in the cluster resource activity log using the `-filter` parameter.

Table J-2 Cluster Resource Activity Log Fields

| Field                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Use Case                                                                                                                                                             |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `timestamp`           | The time when the cluster resource activities were logged.                                                                                                                                                                                                                                                                                                                                                                                                                                 | Use this filter to query all the activities logged at a specific time.<br>This is an alternative to `-aftertime`, `-beforetime`, and `-duration` command parameters. |
| `writer_process_id`   | The ID of the process that is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                                                                                                | Query only the activities spawned by a specific process.                                                                                                             |
| `writer_process_name` | The name of the process that is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                                                                                              | When you query a specific process, CRSCTL returns all the activities for a specific process.                                                                         |
| `writer_user`         | The name of the user who is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                                                                                                  | Query all the activities written by a specific user.                                                                                                                 |
| `writer_group`        | The name of the group to which a user belongs who is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                                                                         | Query all the activities written by users belonging to a specific user group.                                                                                        |
| `writer_hostname`     | The name of the host on which the cluster resource activity log is written.                                                                                                                                                                                                                                                                                                                                                                                                                | Query all the activities written by a specific host.                                                                                                                 |
| `writer_clustername`  | The name of the cluster on which the cluster resource activity log is written.                                                                                                                                                                                                                                                                                                                                                                                                             | Query all the activities written by a specific cluster.                                                                                                              |
| `nls_product`         | The product of the NLS message, for example, `CRS`, `ORA`, or `srvm`.                                                                                                                                                                                                                                                                                                                                                                                                                      | Query all the activities that have a specific product name.                                                                                                          |
| `nls_facility`        | The facility of the NLS message, for example, `CRS` or `PROC`.                                                                                                                                                                                                                                                                                                                                                                                                                             | Query all the activities that have a specific facility name.                                                                                                         |
| `nls_id`              | The ID of the NLS message, for example 42008.                                                                                                                                                                                                                                                                                                                                                                                                                                              | Query all the activities that have a specific message ID.                                                                                                            |
| `nls_field_count`     | The number of fields in the NLS message.                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Query all the activities that correspond to NLS messages with more than, less than, or equal to `nls_field_count` command parameters.                                |
| `nls_field1`          | The first field of the NLS message.                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Query all the activities that match the first parameter of an NLS message.                                                                                           |
| `nls_field1_type`     | The type of the first field in the NLS message.                                                                                                                                                                                                                                                                                                                                                                                                                                            | Query all the activities that match a specific type of the first parameter of an NLS message.                                                                        |
| `nls_format`          | The format of the NLS message, for example, `Resource '%s' has been modified`.                                                                                                                                                                                                                                                                                                                                                                                                             | Query all the activities that match a specific format of an NLS message.                                                                                             |
| `nls_message`         | The entire NLS message that was written to the cluster resource activity log, for example, `Resource 'ora.cvu' has been modified`.                                                                                                                                                                                                                                                                                                                                                         | Query all the activities that match a specific NLS message.                                                                                                          |
| `actid`               | The unique activity ID of every cluster activity log.                                                                                                                                                                                                                                                                                                                                                                                                                                      | Query all the activities that match a specific ID.<br>Also, specify only partial `actid` and list all activities where the `actid` is a subset of the activity ID.   |
| `is_planned`          | Confirms if the activity is planned or not.<br>For example, if a user issues the command `crsctl stop crs` on a node, then the stack stops and resources bounce.<br>Running the `crsctl stop crs` command generates activities and logged in the `calog`. Since this is a planned action, the `is_planned` field is set to true (1).<br>Otherwise, the `is_planned` field is set to false (0).                                                                                             | Query all the planned or unplanned activities.                                                                                                                       |
| `onbehalfof_user`     | The name of the user on behalf of whom the cluster activity log is written.                                                                                                                                                                                                                                                                                                                                                                                                                | Query all the activities written on behalf of a specific user.                                                                                                       |
| `entity_isoraentity`  | Confirms if the entity for which the calog activities are being logged is an oracle entity or not.<br>If a resource, such as `ora.***`, is started or stopped, for example, then all those activities are logged in the cluster resource activity log.<br>Since `ora.***` is an Oracle entity, the `entity_isoraentity` field is set to true (1).<br>Otherwise the `entity_isoraentity` field is set to false (0).                                                                         | Query all the activities logged by Oracle or non-Oracle entities.                                                                                                    |
| `entity_type`         | The type of the entity, such as server, for which the cluster activity log is written.<br>Entity types that can be used to filter activities<br>• `resource`<br>• `resource_type`<br>• `resource_group`<br>• `server_category`<br>• `ohasd` - activities generated by `ohasd` and resources it manages<br>• `crsd` - activities generated by `crsd` and resources it manages<br>In addition, GI components can choose to use their own names for entities when they write to activity log. | Query all the activities that match a specific entity.                                                                                                               |
| `entity_name`         | The name of the entity, for example, foo for which the cluster activity log is written.                                                                                                                                                                                                                                                                                                                                                                                                    | Query all the cluster activities that match a specific entity name.                                                                                                  |
| `entity_hostname`     | The name of the host, for example, `node1`, associated with the entity for which the cluster activity log is written.                                                                                                                                                                                                                                                                                                                                                                      | Query all the cluster activities that match a specific host name.                                                                                                    |
| `entity_clustername`  | The name of the cluster, for example, cluster1 associated with the entity for which the cluster activity log is written.                                                                                                                                                                                                                                                                                                                                                                   | Query all the cluster activities that match a specific cluster name.<br>.                                                                                            |

##### Usage Notes

- Combine simple filters into expressions called expression filters using Boolean operators.

- Enclose timestamps and time intervals in double quotation marks ("").

- Enclose the filter expressions in double quotation marks ("").

- Enclose the values that contain parentheses or spaces in single quotation marks ('').

- If no matching records are found, then the Oracle Clusterware Control (CRSCTL) utility displays the following message:

      CRS-40002: No activities match the query.

##### Examples

Examples of filters include:

- `"writer_user==root"`: Limits the display to only root user.
- `"customer_data=='GEN_RESTART@SERVERNAME(rwsbi08)=StartCompleted~'"` : Limits the display to `customer_data` that has the specified value `GEN_RESTART@SERVERNAME(node1)=StartCompleted~`.

To query all the resource activities and display the output in full format:

    $ crsctl query calog -fullfmt

    ----ACTIVITY START----
    timestamp               : 2016-09-27 17:55:43.152000
    writer_process_id       : 6538
    writer_process_name     : crsd.bin
    writer_user             : root
    writer_group            : root
    writer_hostname         : node1
    writer_clustername      : cluster1-mb1
    customer_data           : CHECK_RESULTS=-408040060~
    nls_product             : CRS
    nls_facility            : CRS
    nls_id                  : 2938
    nls_field_count         : 1
    nls_field1              : ora.cvu
    nls_field1_type         : 25
    nls_field1_len          : 0
    nls_format              : Resource '%s' has been modified.
    nls_message             : Resource 'ora.cvu' has been modified.
    actid                   : 14732093665106538/1816699/1
    is_planned              : 1
    onbehalfof_user         : grid
    onbehalfof_hostname     : node1
    entity_isoraentity      : 1
    entity_type             : resource
    entity_name             : ora.cvu
    entity_hostname         : node1
    entity_clustername      : cluster1-mb1
    nls_severity            : INFO
    ----ACTIVITY END----

To query all the resource activities and display the output in XML format:

    $ crsctl query calog -xmlfmt

    <?xml version="1.0" encoding="UTF-8"?>
    <activities>
      <activity>
        <timestamp>2016-09-27 17:55:43.152000</timestamp>
        <writer_process_id>6538</writer_process_id>
        <writer_process_name>crsd.bin</writer_process_name>
        <writer_user>root</writer_user>
        <writer_group>root</writer_group>
        <writer_hostname>node1</writer_hostname>
        <writer_clustername>cluster1-mb1</writer_clustername>
        <customer_data>CHECK_RESULTS=-408040060~</customer_data>
        <nls_product>CRS</nls_product>
        <nls_facility>CRS</nls_facility>
        <nls_id>2938</nls_id>
        <nls_field_count>1</nls_field_count>
        <nls_field1>ora.cvu</nls_field1>
        <nls_field1_type>25</nls_field1_type>
        <nls_field1_len>0</nls_field1_len>
        <nls_format>Resource '%s' has been modified.</nls_format>
        <nls_message>Resource 'ora.cvu' has been modified.</nls_message>
        <actid>14732093665106538/1816699/1</actid>
        <is_planned>1</is_planned>
        <onbehalfof_user>grid</onbehalfof_user>
        <onbehalfof_hostname>node1</onbehalfof_hostname>
        <entity_isoraentity>1</entity_isoraentity>
        <entity_type>resource</entity_type>
        <entity_name>ora.cvu</entity_name>
        <entity_hostname>node1</entity_hostname>
        <entity_clustername>cluster1-mb1</entity_clustername>
        <nls_severity>INFO</nls_severity>
      </activity>
    </activities>

To query resource activities for a two-hour interval after a specific time and display the output in XML format:

    $ crsctl query calog -aftertime "2016-09-28 17:55:43" -duration "0 02:00:00" -xmlfmt
    <?xml version="1.0" encoding="UTF-8"?>
    <activities>
      <activity>
        <timestamp>2016-09-28 17:55:45.992000</timestamp>
        <writer_process_id>6538</writer_process_id>
        <writer_process_name>crsd.bin</writer_process_name>
        <writer_user>root</writer_user>
        <writer_group>root</writer_group>
        <writer_hostname>node1</writer_hostname>
        <writer_clustername>cluster1-mb1</writer_clustername>
        <customer_data>CHECK_RESULTS=1718139884~</customer_data>
        <nls_product>CRS</nls_product>
        <nls_facility>CRS</nls_facility>
        <nls_id>2938</nls_id>
        <nls_field_count>1</nls_field_count>
        <nls_field1>ora.cvu</nls_field1>
        <nls_field1_type>25</nls_field1_type>
        <nls_field1_len>0</nls_field1_len>
        <nls_format>Resource '%s' has been modified.</nls_format>
        <nls_message>Resource 'ora.cvu' has been modified.</nls_message>
        <actid>14732093665106538/1942009/1</actid>
        <is_planned>1</is_planned>
        <onbehalfof_user>grid</onbehalfof_user>
        <onbehalfof_hostname>node1</onbehalfof_hostname>
        <entity_isoraentity>1</entity_isoraentity>
        <entity_type>resource</entity_type>
        <entity_name>ora.cvu</entity_name>
        <entity_hostname>node1</entity_hostname>
        <entity_clustername>cluster1-mb1</entity_clustername>
        <nls_severity>INFO</nls_severity>
      </activity>
    </activities>

To query resource activities at a specific time:

    $ crsctl query calog -filter "timestamp=='2016-09-28 17:55:45.992000'"

    2016-09-28 17:55:45.992000 : node1 : INFO : Resource 'ora.cvu' has been modified. : 14732093665106538/1942009/1 :

To query resource activities using filters `writer_user` and `customer_data`:

    $ crsctl query calog -filter "writer_user==root AND customer_data=='GEN_RESTART@SERVERNAME(node1)=StartCompleted~'" -fullfmt

or

    $ crsctl query calog -filter "(writer_user==root) AND (customer_data=='GEN_RESTART@SERVERNAME(node1)=StartCompleted~')" -fullfmt

    ----ACTIVITY START----
    timestamp               : 2016-09-15 17:42:57.517000
    writer_process_id       : 6538
    writer_process_name     : crsd.bin
    writer_user             : root
    writer_group            : root
    writer_hostname         : node1
    writer_clustername      : cluster1-mb1
    customer_data           : GEN_RESTART@SERVERNAME(rwsbi08)=StartCompleted~
    nls_product             : CRS
    nls_facility            : CRS
    nls_id                  : 2938
    nls_field_count         : 1
    nls_field1              : ora.testdb.db
    nls_field1_type         : 25
    nls_field1_len          : 0
    nls_format              : Resource '%s' has been modified.
    nls_message             : Resource 'ora.devdb.db' has been modified.
    actid                   : 14732093665106538/659678/1
    is_planned              : 1
    onbehalfof_user         : oracle
    onbehalfof_hostname     : node1
    entity_isoraentity      : 1
    entity_type             : resource
    entity_name             : ora.testdb.db
    entity_hostname         : node1
    entity_clustername      : cluster1-mb1
    nls_severity            : INFO
    ----ACTIVITY END----

To query all the calogs that were generated after UTC+08:00 time "2016-11-15 22:53:08":

    $ crsctl query calog -aftertime "2016-11-15 22:53:08+08:00"

To query all the calogs that were generated after UTC-08:00 time "2016-11-15 22:53:08":

    $ crsctl query calog -aftertime "2016-11-15 22:53:08-08:00"

To query all the calogs by specifying the timestamp with microseconds:

    $ crsctl query calog -aftertime "2016-11-16 01:07:53.063000"
    2016-11-16 01:07:53.558000 : node1 : INFO : Resource 'ora.cvu' has been modified. : 14792791129816600/2580/7 :
    2016-11-16 01:07:53.562000 : node2 : INFO : Clean of 'ora.cvu' on 'node2' succeeded : 14792791129816600/2580/8 :

To query all the activities that were written by a specific process by name:

    $  crsctl query calog -processname crsd.bin

    2016-11-16 01:07:53.558000 : node1 : INFO : Resource 'ora.cvu' has been modified. : 14792791129816600/2580/7 :
    2016-11-16 01:07:53.562000 : node2 : INFO : Clean of 'ora.cvu' on 'node2' succeeded : 14792791129816600/2580/8 :

To query all the activities that were written by a specific process by ID:

    $ crsctl query calog -processid 6538

    2016-11-16 01:07:53.558000 : node1 : INFO : Resource 'ora.cvu' has been modified. : 14792791129816600/2580/7 :
    2016-11-16 01:07:53.562000 : node2 : INFO : Clean of 'ora.cvu' on 'node2' succeeded : 14792791129816600/2580/8 :

To query all the activities that were written by a specific node:

    $ crsctl query calog -node node2
    2016-11-16 01:07:53.562000 : node2 : INFO : Clean of 'ora.cvu' on 'node2' succeeded : 14792791129816600/2580/8 :

#### crsctl get calog maxsize

To store Oracle Clusterware-managed resource activity information, query the maximum space allotted to the cluster resource activity log.

##### Syntax

    crsctl get calog maxsize

##### Parameters

The `crsctl get calog maxsize` command has no parameters.

##### Example

The following example returns the maximum space allotted to the cluster resource activity log to store activities:

    $ crsctl get calog maxsize

    CRS-6760: The maximum size of the Oracle cluster activity log is 1024 MB.

#### crsctl get calog retentiontime

Query the retention time of the cluster resource activity log.

##### Syntax

    crsctl get calog retentiontime

##### Parameters

The `crsctl get calog retentiontime` command has no parameters.

##### Examples

The following example returns the retention time of the cluster activity log, in number of hours:

    $ crsctl get calog retentiontime

    CRS-6781: The retention time of the cluster activity log is 73 hours.

#### crsctl set calog maxsize

Configure the maximum amount of space allotted to store Oracle Clusterware-managed resource activity information.

##### Syntax

    crsctl set calog maxsize maximum_size

##### Usage Notes

Specify a value, in MB, for the maximum size of the storage space that you want to allot to the cluster resource activity log.

**Note:**

If you reduce the amount of storage space, then the contents of the storage are lost.

##### Example

The following example sets maximum amount of space, to store Oracle Clusterware-managed resource activity information, to 1024 MB:

    $ crsctl set calog maxsize 1024

#### crsctl set calog retentiontime

Configure the retention time of the cluster resource activity log.

##### Syntax

    crsctl set calog retentiontime hours

##### Parameters

The `crsctl set calog retentiontime` command takes a number of hours as a parameter.

##### Usage Notes

Specify a value, in hours, for the retention time of the cluster resource activity log.

##### Examples

The following example sets the retention time of the cluster resource activity log to 72 hours:

    $ crsctl set calog retentiontime 72

### Oracle Clusterware Diagnostic and Alert Log Data

Review this content to understand clusterware-specific aspects of how Oracle Clusterware uses ADR.

Oracle Clusterware uses Oracle Database fault diagnosability infrastructure to manage diagnostic data and its alert log. As a result, most diagnostic data resides in the Automatic Diagnostic Repository (ADR), a collection of directories and files located under a base directory that you specify during installation.

#### ADR Directory Structure

Oracle Clusterware ADR data is written under a root directory known as the ADR base. Because components other than ADR use this directory, it may also be referred to as the Oracle base. You specify the file system path to use as the base during Oracle Grid Infrastructure installation and can only be changed if you reinstall the Oracle Grid Infrastructure.

ADR files reside in an ADR home directory. The ADR home for Oracle Clusterware running on a given host always has this structure:

    ORACLE_BASE/diag/crs/host_name/crs

In the preceding example, `ORACLE_BASE` is the Oracle base path you specified when you installed the Oracle Grid Infrastructure and `host_name` is the name of the host. On a Windows platform, this path uses backslashes (`\`) to separate directory names.

Under the ADR home are various directories for specific types of ADR data. The directories of greatest interest are `incident`. The `trace` directory contains all normal (non-incident) trace files written by Oracle Clusterware daemons and command-line programs as well as the simple text version of the Oracle Clusterware alert log. This organization differs significantly from versions prior to Oracle Clusterware 12c release 1 (12.1.0.2), where diagnostic log files were written under distinct directories per daemon.

To change the log level, edit the `ORACLE_BASE``/crsdata/``host_name``/crsdiag/ocrcheck.ini` file.

#### Files in the Trace Directory

Starting with Oracle Clusterware 12c release 1 (12.1.0.2), diagnostic data files written by Oracle Clusterware programs are known as trace files and have a `.trc` file extension, and appear together in the `trace` subdirectory of the ADR home. The naming convention for these files generally uses the executable program name as the file name, possibly augmented with other data depending on the type of program.

Trace files written by Oracle Clusterware command-line programs incorporate the Operating System process ID (PID) in the trace file name to distinguish data from multiple invocations of the same command program. For example, trace data written by CRSCTL uses this name structure: `crsctl_``PID``.trc`. In this example, `PID` is the operating system process ID displayed as decimal digits.

Trace files written by Oracle Clusterware daemon programs do not include a PID in the file name, and they also are subject to a file rotation mechanism that affects naming. Rotation means that when the current daemon trace file reaches a certain size, the file is closed, renamed, and a new trace file is opened. This occurs a fixed number of times, and then the oldest trace file from the daemon is discarded, keeping the rotation set at a fixed size.

Most Oracle Clusterware daemons use a file size limit of 25 MB and a rotation set size of 10 files, thus maintaining a total of 250 MB of trace data. The current trace file for a given daemon uses the program name as the file name; older files in the rotation append a number to the file name. For example, the trace file currently being written by the Oracle High Availability Services daemon (OHASD) is named `ohasd.trc`; the most recently rotated-out trace file is named `ohasd_``n``.trc`, where `n` is an ever-increasing decimal integer. The file with the highest `n` is actually the most recently archived trace, and the file with the lowest `n` is the oldest.

Oracle Clusterware agents are daemon programs whose trace files are subject to special naming conventions that indicate the origin of the agent (whether it was spawned by the OHASD or the Cluster Ready Services daemon (CRSD)) and the Operating System user name with which the agent runs. Thus, the name structure for agents is:

    origin_executable_user_name

**Note:**

The first two underscores (\_) in the name structure are literal and are included in the trace file name. The underscore in `user_name` is not part of the file naming convention.

In the previous example, `origin` is either `ohasd` or `crsd`, `executable` is the executable program name, and `user_name` is the operating system user name. In addition, because they are daemons, agent trace files are subject to the rotation mechanism previously described, so files with an additional `_n` suffix are present after rotation occurs.

#### The Oracle Clusterware Alert Log

Besides trace files, the `trace` subdirectory in the Oracle Clusterware ADR home contains the simple text Oracle Clusterware alert log. It always has the name `alert.log`. The alert log is also written as an XML file in the `alert` subdirectory of the ADR home, but the text alert log is most easily read.

The alert log is the first place to look when a problem or issue arises with Oracle Clusterware. Unlike the Oracle Database instance alert log, messages in the Oracle Clusterware alert log are identified, documented, and localized (translated). Oracle Clusterware alert messages are written for most significant events or errors that occur.

**Note:**

Messages and data written to Oracle Clusterware trace files generally are not documented and translated and are used mainly by My Oracle Support for problem diagnosis.

#### Incident Trace Files

Certain errors occur in Oracle Clusterware programs that will raise an ADR incident. In most cases, these errors should be reported to My Oracle Support for diagnosis. The occurrence of an incident normally produces one or more descriptive messages in the Oracle Clusterware alert log.

In addition to alert messages, incidents also cause the affected program to produce a special, separate trace file containing diagnostic data related to the error. These incident-specific trace files are collected in the `incident` subdirectory of the ADR home rather than the `trace` subdirectory. Both the normal trace files and incident trace files are collected and submitted to Oracle when reporting the error.

**See Also:**

[Oracle Database Administrator's Guide](../admin/diagnosing-and-resolving-problems.md) for more information on incidents and data collection

#### Other Diagnostic Data

Besides ADR data, Oracle Clusterware collects or uses other data related to problem diagnosis. Starting with Oracle Clusterware 12c release 1 (12.1.0.2), this data resides under the same base path used by ADR, but in a separate directory structure with this form: `ORACLE_BASE``/crsdata/``host_name`. In this example, `ORACLE_BASE` is the Oracle base path you specified when you installed the Grid Infrastructure and `host_name` is the name of the host.

In this directory, on a given host, are several subdirectories. The two subdirectories of greatest interest if a problem occurs are named `core` and `output`. The `core` directory is where Oracle Clusterware daemon core files are written when the normal ADR location used for core files is not available (for example, before ADR services are initialized in a program). The `output` directory is where Oracle Clusterware daemons redirect their C standard output and standard error files. These files generally use a name structure consisting of the executable name with the characters OUT appended to a `.trc` file extension (like trace files). For example, the redirected standard output from the Cluster Time Synchronization Service daemon is named `octssdOUT.trc`. Typically, daemons write very little to these files, but in certain failure scenarios important data may be written there.

**Related Topics**

- [Oracle Database Administrator's Guide](../admin/diagnosing-and-resolving-problems.md)
- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md)

### Diagnostics Collection Script

When an Oracle Clusterware error occurs, run the `diagcollection.pl` diagnostics collection script to collect diagnostic information from Oracle Clusterware into trace files. The diagnostics provide additional information so My Oracle Support can resolve problems. Run this script as `root` from the `Grid_home``/bin` directory.

#### Syntax

Use the diagcollection.pl script with the following syntax:

    diagcollection.pl {--collect [--crs | --acfs | -all] [--chmos [--incidenttime time [--incidentduration time]]]
       [--adr location [--aftertime time [--beforetime time]]]
       [--crshome path | --clean | --coreanalyze}]

**Note:**

The `diagcollection.pl` script arguments are all preceded by two dashes (`--`).

#### Parameters

Table J-3 lists and describes the parameters used with the `diagcollection.pl` script.

Table J-3 diagcollection.pl Script Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--collect`     | Use this parameter with any of the following arguments:<br>• `--crs`: Use this argument to collect Oracle Clusterware diagnostic information<br>• `--acfs`: Use this argument to collect Oracle ACFS diagnostic information<br>• Note: You can only use this argument on UNIX systems.<br>• `--all`: Use this argument to collect all diagnostic information except CHM (OS) data<br>• Note: This is the default.<br>• `--chmos`: Use this argument to collect the following CHM diagnostic information<br>• `--incidenttime ``time`: Use this argument to collect CHM (OS) data from the specified time<br>• Note: The time format is MM/DD/YYYYHH24:MM:SS.<br>• `--incidentduration ``time`: Use this argument with `--incidenttime` to collect CHM (OS) data for the duration after the specified time<br>• Note: The time format is HH:MM. If you do not use `--incidentduration`, then all CHM (OS) data after the time you specify in `--incidenttime` is collected.<br>• `--adr ``location`: The Automatic Diagnostic Repository Command Interpreter (ADRCI) uses this argument to specify a location in which to collect diagnostic information for ADR<br>• See Also: [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md) for more information about ADRCI<br>• `--aftertime ``time`: Use this argument with the `--adr` argument to collect archives after the specified time<br>• Note: The time format is YYYYMMDDHHMISS24.<br>• `--beforetime ``time`: Use this argument with the `--adr` argument to collect archives before the specified time<br>• Note: The time format is YYYYMMDDHHMISS24.<br>• `--crshome ``path`: Use this argument to override the location of the Oracle Clusterware home<br>• Note: The `diagcollection.pl` script typically derives the location of the Oracle Clusterware home from the system configuration (either the `olr.loc` file or the Windows registry), so this argument is not required. |
| `--clean`       | Use this parameter to clean up the diagnostic information gathered by the `diagcollection.pl` script.<br>Note: You cannot use this parameter with `--collect`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--coreanalyze` | Use this parameter to extract information from core files and store it in a text file.<br>Note: You can only use this parameter on UNIX systems.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

### Storage Split in Oracle Extended Clusters

A storage split occurs when the private network between two or more disparate sites is available and online, but the storage network has failed.

When Oracle Automatic Storage Management (Oracle ASM) detects a storage split in a typical extended cluster configuration with three sites (two data sites and a quorum site), one of the data sites terminates and quarantines itself and the nodes it contains from the rest of the cluster. If Oracle ASM attempts to start on the quarantined site, then error CRS-2971 occurs.

Resolve the issue, as follows:

1.  Resolve the inter-site connectivity issue that resulted in the storage split.

2.  Ensure that all Oracle ASM disk groups are mounted on the site that is not quarantined, as follows:

        SELECT group_number, name, state FROM v$asm_diskgroup_stat;

3.  Obtain a list of online disks belonging to these disk groups by running the following command for each disk group:

        SELECT path FROM v$asm_disk_stat WHERE group_number=group_number AND state = 'NORMAL' AND mode_status = 'ONLINE';

4.  For each of the paths from you obtained in the previous step, ensure that the disk is accessible from the quarantined site, as follows:

        asmcmd lsdsk -I --member 'path'

5.  If the preceding verification succeeds, then rejuvenate the quarantined site, as follows:

        crsctl modify cluster site site_name -s rejuvenate

### Rolling Upgrade and Driver Installation Issues

During an upgrade, while running the Oracle Clusterware `root.sh` script, you may see the following messages:

- ACFS-9427 Failed to unload ADVM/ACFS drivers. A system restart is recommended.

- ACFS-9428 Failed to load ADVM/ACFS drivers. A system restart is recommended.

If you see these error messages during the upgrade of the initial (first) node, then do the following:

1.  Complete the upgrade of all other nodes in the cluster.

2.  Restart the initial node.

3.  Run the `root.sh` script on initial node again.

4.  Run the `Grid_home``/gridSetup -executeConfigTools -responseFile /u01/app/23.0.0/grid/install/response/gridinstall.rsp` command as the user who installed Oracle Grid Infrastructure to complete the upgrade.

For nodes other than the initial node (the node on which you started the installation):

1.  Restart the node where the error occurs.

2.  Run the `orainstRoot.sh` script as `root` on the node where the error occurs.

3.  Change directory to the Grid home, and run the `root.sh` script on the node where the error occurs.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/using-the-installation-response-file-for-postinstallation-configuration.md)

### Testing Zone Delegation

**See Also:**

[Oracle Clusterware Control (CRSCTL) Utility Reference](oracle-clusterware-control-crsctl-utility-reference.md) for information about using the CRSCTL commands referred to in this procedure

Use the following procedure to test zone delegation:

1.  Start the GNS VIP by running the following command as `root`:

        # crsctl start ip -A IP_name/netmask/interface_name

    The `interface_name` should be the public interface and netmask of the public network.

2.  Start the test DNS server on the GNS VIP by running the following command (you must run this command as `root` if the port number is less than 1024):

        # crsctl start testdns -address address [-port port]

    This command starts the test DNS server to listen for DNS forwarded packets at the specified IP and port.

3.  Ensure that the GNS VIP is reachable from other nodes by running the following command as `root`:

        crsctl status ip -A IP_name

4.  Query the DNS server directly by running the following command:

        crsctl query dns -name name -dnsserver DNS_server_address

    This command fails with the following error:

    CRS-10023: Domain name look up for name asdf.foo.com failed. Operating system error: Host name lookup failure

    Look at `Grid_home``/log/``host_name``/client/odnsd_*.log` to see if the query was received by the test DNS server. This validates that the DNS queries are not being blocked by a firewall.

5.  Query the DNS delegation of GNS domain queries by running the following command:

        crsctl query dns -name name

    **Note:**

    The only difference between this step and the previous step is that you are not giving the `-dnsserver` `DNS_server_address` option. This causes the command to query name servers configured in `/etc/resolv.conf`. As in the previous step, the command fails with same error. Again, look at `odnsd*.log` to ensure that `odnsd` received the queries. If step 5 succeeds but step 6 does not, then you must check the DNS configuration.

6.  Stop the test DNS server by running the following command:

        crsctl stop testdns -address address

7.  Stop the GNS VIP by running the following command as `root`:

        crsctl stop ip -A IP_name/netmask/interface_name

### Oracle Clusterware Alerts

Oracle Clusterware writes messages to the ADR alert log file (as previously described) for various important events. Alert log messages generally are localized (translated) and carry a message identifier that can be used to look up additional information about the message. The alert log is the first place to look if there appears to be problems with Oracle Clusterware.

The following is an example of alert log messages from two different CRS daemon processes:

    2014-07-16 00:27:22.074 [CTSSD(12817)]CRS-2403:The Cluster Time Synchronization Service on host stnsp014 is in observer mode.
    2014-07-16 00:27:22.146 [CTSSD(12817)]CRS-2407:The new Cluster Time Synchronization Service reference node is host stnsp013.
    2014-07-16 00:27:22.753 [CTSSD(12817)]CRS-2401:The Cluster Time Synchronization Service started on host stnsp014.
    2014-07-16 00:27:43.754 [CRSD(12975)]CRS-1012:The OCR service started on node stnsp014.
    2014-07-16 00:27:46.339 [CRSD(12975)]CRS-1201:CRSD started on node stnsp014.

The following example shows the start of the Oracle Cluster Time Synchronization Service (OCTSS) after a cluster reconfiguration:

    2014-07-15 23:51:17.532 [CTSSD(12813)]CRS-2403:The Cluster Time Synchronization Service on host stnsp014 is in observer mode.
    2014-07-15 23:51:18.292 [CTSSD(12813)]CRS-2407:The new Cluster Time Synchronization Service reference node is host stnsp013.
    2014-07-15 23:51:18.961 [CTSSD(12813)]CRS-2401:The Cluster Time Synchronization Service started on host stnsp014.

#### Alert Messages Using Diagnostic Record Unique IDs

Beginning with Oracle Database 11g release 2 (11.2), certain Oracle Clusterware messages contain a text identifier surrounded by "`(:`" and "`:)`". Usually, the identifier is part of the message text that begins with "`Details in...`" and includes an Oracle Clusterware diagnostic log file path and name similar to the following example. The identifier is called a DRUID, or diagnostic record unique ID:

    2014-07-16 00:18:44.472 [ORAROOTAGENT(13098)]CRS-5822:Agent
     '/scratch/12.1/grid/bin/orarootagent_root' disconnected from server. Details at
     (:CRSAGF00117:) in /scratch/12.1/grid/log/stnsp014/agent/crsd/orarootagent_
    root/orarootagent_root.log.

DRUIDs are used to relate external product messages to entries in a diagnostic log file and to internal Oracle Clusterware program code locations. They are not directly meaningful to customers and are used primarily by My Oracle Support when diagnosing problems.
