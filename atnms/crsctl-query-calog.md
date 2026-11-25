Query the cluster resource activity logs matching specific criteria.

### Syntax

    crsctl query calog [-aftertime "timestamp"] [-beforetime "timestamp"]
      [-duration "time_interval" | -follow] [-filter "filter_expression"]
      [-fullfmt | -xmlfmt]

### Parameters

Table C-1 crsctl query calog Command Parameters

| Parameter                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-aftertime "``timestamp``"`              | Displays the activities logged after a specific time.<br>Specify the timestamp in the `YYYY-MM-DD HH24:MI:SS[.FF][TZH:TZM]` or `YYYY-MM-DD` or `HH24:MI:SS[.FF][TZH:TZM]` format.<br>`TZH` and `TZM` stands for time zone hour and minute, and `FF` stands for microseconds.<br>If you specify `[TZH:TZM]`, then the `crsctl` command assumes UTC as time zone. If you do not specify `[TZH:TZM]`, then the `crsctl` command assumes the local time zone of the cluster node from where the `crsctl` command is run.<br>Use this parameter with `-beforetime` to query the activities logged at a specific time interval. |
| `-beforetime "``timestamp``"`             | Displays the activities logged before a specific time.<br>Specify the timestamp in the `YYYY-MM-DD HH24:MI:SS[.FF][TZH:TZM]` or `YYYY-MM-DD` or `HH24:MI:SS[.FF][TZH:TZM]` format.<br>`TZH` and `TZM` stands for time zone hour and minute, and `FF` stands for microseconds.<br>If you specify `[TZH:TZM]`, then the `crsctl` command assumes UTC as time zone. If you do not specify `[TZH:TZM]`, then the `crsctl` command assumes the local time zone of the cluster node from where the `crsctl` command is run.<br>Use this parameter with `-aftertime` to query the activities logged at a specific time interval. |
| `-duration "``time_interval``" | -follow` | Use `-duration` to specify a time interval that you want to query when you use the `-aftertime` parameter.<br>Specify the timestamp in the `DD HH:MM:SS` format.<br>Use `-follow` to display a continuous stream of activities as they occur.                                                                                                                                                                                                                                                                                                                                                                             |
| `-filter "``filter_expression``"`         | Query any number of fields in the cluster resource activity log using the `-filter` parameter.<br>To specify multiple filters, use a comma-delimited list of filter expressions surrounded by double quotation marks (`""`).                                                                                                                                                                                                                                                                                                                                                                                              |
| `-fullfmt | -xmlfmt`                      | To display cluster resource activity log data, choose full or XML format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Cluster Resource Activity Log Fields

Query any number of fields in the cluster resource activity log using the `-filter` parameter.

Table C-2 Cluster Resource Activity Log Fields

| Field                 | Description                                                                                                                                                                                                                                                                                                                                                                                                        | Use Case                                                                                                                                                             |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `timestamp`           | The time when the cluster resource activities were logged.                                                                                                                                                                                                                                                                                                                                                         | Use this filter to query all the activities logged at a specific time.<br>This is an alternative to `-aftertime`, `-beforetime`, and `-duration` command parameters. |
| `writer_process_id`   | The ID of the process that is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                        | Query only the activities spawned by a specific process.                                                                                                             |
| `writer_process_name` | The name of the process that is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                      | When you query a specific process, CRSCTL returns all the activities for a specific process.                                                                         |
| `writer_user`         | The name of the user who is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                                          | Query all the activities written by a specific user.                                                                                                                 |
| `writer_group`        | The name of the group to which a user belongs who is writing to the cluster resource activity log.                                                                                                                                                                                                                                                                                                                 | Query all the activities written by users belonging to a specific user group.                                                                                        |
| `writer_hostname`     | The name of the host on which the cluster resource activity log is written.                                                                                                                                                                                                                                                                                                                                        | Query all the activities written by a specific host.                                                                                                                 |
| `writer_clustername`  | The name of the cluster on which the cluster resource activity log is written.                                                                                                                                                                                                                                                                                                                                     | Query all the activities written by a specific cluster.                                                                                                              |
| `nls_product`         | The product of the NLS message, for example, `CRS`, `ORA`, or `srvm`.                                                                                                                                                                                                                                                                                                                                              | Query all the activities that have a specific product name.                                                                                                          |
| `nls_facility`        | The facility of the NLS message, for example, `CRS` or `PROC`.                                                                                                                                                                                                                                                                                                                                                     | Query all the activities that have a specific facility name.                                                                                                         |
| `nls_id`              | The ID of the NLS message, for example 42008.                                                                                                                                                                                                                                                                                                                                                                      | Query all the activities that have a specific message ID.                                                                                                            |
| `nls_field_count`     | The number of fields in the NLS message.                                                                                                                                                                                                                                                                                                                                                                           | Query all the activities that correspond to NLS messages with more than, less than, or equal to `nls_field_count` command parameters.                                |
| `nls_field1`          | The first field of the NLS message.                                                                                                                                                                                                                                                                                                                                                                                | Query all the activities that match the first parameter of an NLS message.                                                                                           |
| `nls_field1_type`     | The type of the first field in the NLS message.                                                                                                                                                                                                                                                                                                                                                                    | Query all the activities that match a specific type of the first parameter of an NLS message.                                                                        |
| `nls_format`          | The format of the NLS message, for example, `Resource '%s' has been modified`.                                                                                                                                                                                                                                                                                                                                     | Query all the activities that match a specific format of an NLS message.                                                                                             |
| `nls_message`         | The entire NLS message that was written to the cluster resource activity log, for example, `Resource 'ora.cvu' has been modified`.                                                                                                                                                                                                                                                                                 | Query all the activities that match a specific NLS message.                                                                                                          |
| `actid`               | The unique activity ID of every cluster activity log.                                                                                                                                                                                                                                                                                                                                                              | Query all the activities that match a specific ID.<br>Also, specify only partial `actid` and list all activities where the `actid` is a subset of the activity ID.   |
| `is_planned`          | Confirms if the activity is planned or not.<br>For example, if a user issues the command `crsctl stop crs` on a node, then the stack stops and resources bounce.<br>Running the `crsctl stop crs` command generates activities and logged in the `calog`. Since this is a planned action, the `is_planned` field is set to true (1).<br>Otherwise, the `is_planned` field is set to false (0).                     | Query all the planned or unplanned activities.                                                                                                                       |
| `onbehalfof_user`     | The name of the user on behalf of whom the cluster activity log is written.                                                                                                                                                                                                                                                                                                                                        | Query all the activities written on behalf of a specific user.                                                                                                       |
| `entity_isoraentity`  | Confirms if the entity for which the calog activities are being logged is an oracle entity or not.<br>If a resource, such as `ora.***`, is started or stopped, for example, then all those activities are logged in the cluster resource activity log.<br>Since `ora.***` is an Oracle entity, the `entity_isoraentity` field is set to true (1).<br>Otherwise the `entity_isoraentity` field is set to false (0). | Query all the activities logged by Oracle or non-Oracle entities.                                                                                                    |
| `entity_type`         | The type of the entity, such as server, for which the cluster activity log is written.                                                                                                                                                                                                                                                                                                                             | Query all the activities that match a specific entity.                                                                                                               |
| `entity_name`         | The name of the entity, for example, foo for which the cluster activity log is written.                                                                                                                                                                                                                                                                                                                            | Query all the cluster activities that match a specific entity name.                                                                                                  |
| `entity_hostname`     | The name of the host, for example, `node1`, associated with the entity for which the cluster activity log is written.                                                                                                                                                                                                                                                                                              | Query all the cluster activities that match a specific host name.                                                                                                    |
| `entity_clustername`  | The name of the cluster, for example, cluster1 associated with the entity for which the cluster activity log is written.                                                                                                                                                                                                                                                                                           | Query all the cluster activities that match a specific cluster name.<br>.                                                                                            |

### Usage Notes

Combine simple filters into expressions called expression filters using Boolean operators.

Enclose timestamps and time intervals in double quotation marks ("").

Enclose the filter expressions in double quotation marks ("").

Enclose the values that contain parentheses or spaces in single quotation marks ('').

If no matching records are found, then the Oracle Clusterware Control (CRSCTL) utility displays the following message:

    CRS-40002: No activities match the query.

### Examples

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
      </activity>
    </activities>

To query resource activities at a specific time:

    $ crsctl query calog -filter "timestamp=='2016-09-28 17:55:45.992000'"

    2016-09-28 17:55:45.992000 : Resource 'ora.cvu' has been modified. : 14732093665106538/1942009/1 :

To query resource activities using filters `writer_user` and `customer_data`:

    $ crsctl query calog -filter "writer_user==root AND customer_data==
      'GEN_RESTART@SERVERNAME(node1)=StartCompleted~'" -fullfmt

or

    $ crsctl query calog -filter "(writer_user==root) AND (customer_data==
      'GEN_RESTART@SERVERNAME(node1)=StartCompleted~')" -fullfmt

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
    ----ACTIVITY END----

To query all the calogs that were generated after UTC+08:00 time "2016-11-15 22:53:08":

    $ crsctl query calog -aftertime "2016-11-15 22:53:08+08:00"

To query all the calogs that were generated after UTC-08:00 time "2016-11-15 22:53:08":

    $ crsctl query calog -aftertime "2016-11-15 22:53:08-08:00"

To query all the calogs by specifying the timestamp with microseconds:

    $ crsctl query calog -aftertime "2016-11-16 01:07:53.063000"

    2016-11-16 01:07:53.558000 : Resource 'ora.cvu' has been modified. : 14792791129816600/2580/7 :
    2016-11-16 01:07:53.562000 : Clean of 'ora.cvu' on 'rwsam02' succeeded : 14792791129816600/2580/8 :

**Parent topic:** [Managing the Cluster Resource Activity Log](cluster-resource-activity-log.md)
