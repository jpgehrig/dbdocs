Oracle Tuning Pack licence is required for this service. Returns information on a monitored statement from GV\$SQL_MONITOR view. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- sql_exec_id: number
  Execution identifier.
- sql_exec_start: string(date-time)
  Time when the execution started.
- sql_id: string
  SQL identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Descrption of a monitored SQL statement.

Body ()

Root Schema : PerformanceSQLStatementMonitorsItem

Type: `object`

This object provides statistics for a single execution of an SQL statement. The list of attributes may vary depending on database version.

Show Source

- action(optional): string
  Name of the executing action when sampled, as set by the DBMS_APPLICATION_INFO.SET_ACTION procedure.
- application_wait_time(optional): integer
  Application wait time (in microseconds); updated as the statement executes.
- binds_xml(optional): string
  Information about bind variables used with the SQL, such as name, position, value, data type, and so on (stored in XML format).
- buffer_gets(optional): integer
  Number of buffer get operations; updated as the statement executes.
- client_identifier(optional): string
  Client identifier from the user session.
- client_info(optional): string
  Client information for the user session.
- cluster_wait_time(optional): integer
  Cluster wait time (in microseconds); updated as the statement executes.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- con_name(optional): string
  Container name of the object. The value of this column is NULL in non-CDBs.
- concurrency_wait_time(optional): integer
  Concurrency wait time (in microseconds); updated as the statement executes.
- cpu_time(optional): integer
  CPU time (in microseconds); updated as the statement executes.
- current_user(optional): integer
  Unique number identifying the current user.
- current_username(optional): integer
  Username for the current user.
- dbop_exec_id(optional): integer
  Database operation execution identifier for the current execution. If the type is SQL, the DBOP_EXEC_ID will be NULL.
- dbop_name(optional): string
  Database operation name. If the type is SQL, the DBOP_NAME will be NULL.
- direct_writes(optional): integer
  Number of direct writes; updated as the statement executes.
- disk_reads(optional): integer
  Number of disk reads; updated as the statement executes.
- ecid(optional): string
  Execution context identifier (sent by Application Server).
- elapsed_time(optional): integer
  Elapsed time (in microseconds); updated as the statement executes.
- error_facility(optional): string
  Error facility in case a SQL fails to execute successfully (for example, ORA in case of ORA-00932).
- error_message(optional): string
  Detailed error message displayed corresponding to the error number and error facility when a SQL fails to execute successfully.
- error_number(optional): string
  Error number encountered in case a SQL fails to execute successfully (for example, 932 in case of ORA-00932).
- exact_matching_signature(optional): integer
  Signature calculated on the normalized SQL text. The normalization includes the removal of white space and the uppercasing of all non-literal strings.
- fetches(optional): integer
  Number of fetches associated with the SQL statement; updated as the statement executes.
- first_refresh_time(optional): string
  Time when monitoring of the SQL statement started, generally a few seconds after execution start time.
- force_matching_signature(optional): integer
  Same as EXACT_MATCHING_SIGNATURE but literals in the SQL text are replaced by binds.
- in_dbop_exec_id(optional): integer
  If the SQL that is monitored was executed by a session that was also monitored by a database operation (DBOP), then this column specifies the execution ID of that DBO.
- in_dbop_name(optional): string
  If the SQL that is monitored was executed by a session that was also monitored by a database operation (DBOP), then this column specifies the name of that DBOP.
- inst_id(optional): integer
  Instance number from which the associated GV\$SQL_MONITOR view information was obtained.
- io_cell_offload_eligible_bytes(optional): integer
  Number of I/O bytes which can be filtered by the Exadata storage system.
- io_cell_offload_returned_bytes(optional): integer
  Number of filtered bytes returned by Exadata cells (that is, the number of bytes returned after processing has been offloaded on the Exadata cells).
- io_cell_uncompressed_bytes(optional): integer
  Number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells.
- io_interconnect_bytes(optional): integer
  Number of I/O bytes exchanged between Oracle Database and the storage system.
- is_adaptive_plan(optional): string
  Indicates whether the statistics are from an adaptive plan (Y) or not (N).
- is_final_plan(optional): string
  Indicates whether the statistics are from the final plan (Y) or not (N).
- is_full_sqltext(optional): string
  Indicates whether the SQL_TEXT column has the entire SQL text (Y) or not (N).
- java_exec_time(optional): integer
  Java execution time (in microseconds); updated as the statement executes.
- key(optional): integer
  Artificial join key to efficiently join GV\$SQL_MONITOR with its corresponding plan level monitoring statistics stored in GV\$SQL_PLAN_MONITOR.
- last_refresh_time(optional): string
  Time when statistics in V\$SQL_MONITOR were last updated for the SQL statement. Statistics are generally refreshed every second when the statement executes.
- links(optional): array links
- module(optional): string
  Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_MODULE procedure.
- other_xml(optional): string
  Additional information about SQL execution stored in XML format.
- physical_read_bytes(optional): integer
  Number of bytes read from disks by the monitored SQL.
- physical_read_requests(optional): integer
  Number of physical read I/O requests issued by the monitored SQL.
- physical_write_bytes(optional): integer
  Number of bytes written to disks by the monitored SQL.
- physical_write_requests(optional): integer
  Number of physical write I/O requests issued by the monitored SQL.
- plsql_entry_object_id(optional): integer
  Object ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack.
- plsql_entry_subprogram_id(optional): integer
  Subprogram ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack.
- plsql_exec_time(optional): integer
  PL/SQL execution time (in microseconds); updated as the statement executes.
- plsql_object_id(optional): integer
  Object ID of the currently executing PL/SQL subprogram; NULL if executing SQL.
- plsql_subprogram_id(optional): integer
  Subprogram ID of the currently executing PL/SQL object; NULL if executing SQL.
- process_name(optional): string
  Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001).
- program(optional): string
  Name of the operating system program that issued the monitored SQL.
- px_is_cross_instance(optional): string
  Indicates whether the SQL statement ran parallel across multiple instances (Y) or not (N).
- px_maxdop(optional): integer
  Maximum degree of parallelism for any plan operation executed on behalf of the monitored SQL.
- px_maxdop_instances(optional): integer
  Number of database instances touched at the maximum degree of parallelism.
- px_qcinst_id(optional): integer
  Instance identifier where the parallel execution coordinator runs; NULL if PX_SERVER# is NULL.
- px_qcsid(optional): integer
  Session identifier for the parallel execution coordinator; NULL if PX_SERVER# is NULL.
- px_server#(optional): integer
  Logical parallel execution server process number executing (or having executed) the statement being monitored; NULL if this monitoring entry is not associated with an execution server. This is a logical number within the parallel server set (see SERVER# in V\$PX_SESSION).
- px_server_group(optional): integer
  Logical parallel execution server group number to which PX_SERVER# belongs (see SERVER_GROUP in V\$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server. This value is generally 1 unless the SQL statement has one or more parallel sub-queries.
- px_server_set(optional): integer
  Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V\$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server.
- px_servers_allocated(optional): integer
  Actual number of parallel execution servers allocated to execute the query
- px_servers_requested(optional): integer
  Total number of parallel execution servers requested to execute the monitored SQL.
- queuing_time(optional): integer
  Duration of time (in microseconds) spent by SQL in the statement queue.
- refresh_count(optional): integer
  Number of times V\$SQL_MONITOR statistics have been refreshed (generally once every second when the SQL statement executes).
- report_id(optional): integer
  Unique ID of the XML report stored in Automatic Workload Repository (AWR) for this monitored entity.
- rm_consumer_group(optional): string
  The current consumer group for this SQL operation.
- rm_last_action(optional): string
  The most recent action that was taken on this SQL operation by Resource Manager.
- rm_last_action_reason(optional): string
  The reason for the most recent action that was taken on this SQL operation by Resource Manager.
- rm_last_action_time(optional): string
  The time of the most recent action that was taken on this SQL operation by Resource Manager.
- service_name(optional): string
  Service name of the user session.
- session_serial#(optional): integer
  Session serial number executing the statement being monitored.
- sid(optional): integer
  Session identifier executing (or having executed) the SQL statement being monitored.
- sql_child_address(optional): string
  Address of the child cursor (can be used with SQL_ID to join with GV\$SQL).
- sql_exec_id(optional): integer
  Execution identifier. Together, the three columns SQL_ID, SQL_EXEC_START, and SQL_EXEC_ID represent the execution key. The execution key is used to uniquely identify one execution of the SQL statement.
- sql_exec_start(optional): string
  Time when the execution started.
- sql_full_plan_hash_value(optional): integer
  Numeric representation of the complete SQL plan for this cursor. Comparing one SQL_FULL_PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line). Note that the SQL_FULL_PLAN_HASH_VALUE cannot be compared across databases releases. It is not backward compatible.
- sql_id(optional): string
  SQL identifier of the statement being monitored.
- sql_plan_hash_value(optional): integer
  SQL plan hash value.
- sql_text(optional): string
  Up to the first 2000 characters of the text of the SQL being monitored.
- status(optional): string
  SQL execution status.
- user#(optional): integer
  User ID of the database user who issued the SQL being monitored.
- user_io_wait_time(optional): integer
  User I/O Wait Time (in microseconds); updated as the statement executes.
- username(optional): string
  User name of the database user who issued the SQL being monitored.

<!-- -->

    {
        "type":"object",
        "description":"This object provides statistics for a single execution of an SQL statement. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$SQL_MONITOR view information was obtained."
            },
            "key":{
                "type":"integer",
                "description":"Artificial join key to efficiently join GV$SQL_MONITOR with its corresponding plan level monitoring statistics stored in GV$SQL_PLAN_MONITOR."
            },
            "report_id":{
                "type":"integer",
                "description":"Unique ID of the XML report stored in Automatic Workload Repository (AWR) for this monitored entity."
            },
            "status":{
                "type":"string",
                "description":"SQL execution status."
            },
            "user#":{
                "type":"integer",
                "description":"User ID of the database user who issued the SQL being monitored."
            },
            "username":{
                "type":"string",
                "description":"User name of the database user who issued the SQL being monitored."
            },
            "module":{
                "type":"string",
                "description":"Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_MODULE procedure."
            },
            "action":{
                "type":"string",
                "description":"Name of the executing action when sampled, as set by the DBMS_APPLICATION_INFO.SET_ACTION procedure."
            },
            "service_name":{
                "type":"string",
                "description":"Service name of the user session."
            },
            "client_identifier":{
                "type":"string",
                "description":"Client identifier from the user session."
            },
            "client_info":{
                "type":"string",
                "description":"Client information for the user session."
            },
            "program":{
                "type":"string",
                "description":"Name of the operating system program that issued the monitored SQL."
            },
            "plsql_entry_object_id":{
                "type":"integer",
                "description":"Object ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack."
            },
            "plsql_entry_subprogram_id":{
                "type":"integer",
                "description":"Subprogram ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack."
            },
            "plsql_object_id":{
                "type":"integer",
                "description":"Object ID of the currently executing PL/SQL subprogram; NULL if executing SQL."
            },
            "plsql_subprogram_id":{
                "type":"integer",
                "description":"Subprogram ID of the currently executing PL/SQL object; NULL if executing SQL."
            },
            "first_refresh_time":{
                "type":"string",
                "description":"Time when monitoring of the SQL statement started, generally a few seconds after execution start time."
            },
            "last_refresh_time":{
                "type":"string",
                "description":"Time when statistics in V$SQL_MONITOR were last updated for the SQL statement. Statistics are generally refreshed every second when the statement executes."
            },
            "refresh_count":{
                "type":"integer",
                "description":"Number of times V$SQL_MONITOR statistics have been refreshed (generally once every second when the SQL statement executes)."
            },
            "dbop_exec_id":{
                "type":"integer",
                "description":"Database operation execution identifier for the current execution. If the type is SQL, the DBOP_EXEC_ID will be NULL."
            },
            "dbop_name":{
                "type":"string",
                "description":"Database operation name. If the type is SQL, the DBOP_NAME will be NULL."
            },
            "sid":{
                "type":"integer",
                "description":"Session identifier executing (or having executed) the SQL statement being monitored."
            },
            "process_name":{
                "type":"string",
                "description":"Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001)."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the statement being monitored."
            },
            "sql_text":{
                "type":"string",
                "description":"Up to the first 2000 characters of the text of the SQL being monitored."
            },
            "is_full_sqltext":{
                "type":"string",
                "description":"Indicates whether the SQL_TEXT column has the entire SQL text (Y) or not (N)."
            },
            "sql_exec_start":{
                "type":"string",
                "description":"Time when the execution started."
            },
            "sql_exec_id":{
                "type":"integer",
                "description":"Execution identifier. Together, the three columns SQL_ID, SQL_EXEC_START, and SQL_EXEC_ID represent the execution key. The execution key is used to uniquely identify one execution of the SQL statement."
            },
            "sql_plan_hash_value":{
                "type":"integer",
                "description":"SQL plan hash value."
            },
            "sql_full_plan_hash_value":{
                "type":"integer",
                "description":"Numeric representation of the complete SQL plan for this cursor. Comparing one SQL_FULL_PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line). Note that the SQL_FULL_PLAN_HASH_VALUE cannot be compared across databases releases. It is not backward compatible."
            },
            "exact_matching_signature":{
                "type":"integer",
                "description":"Signature calculated on the normalized SQL text. The normalization includes the removal of white space and the uppercasing of all non-literal strings."
            },
            "force_matching_signature":{
                "type":"integer",
                "description":"Same as EXACT_MATCHING_SIGNATURE but literals in the SQL text are replaced by binds."
            },
            "sql_child_address":{
                "type":"string",
                "description":"Address of the child cursor (can be used with SQL_ID to join with GV$SQL)."
            },
            "session_serial#":{
                "type":"integer",
                "description":"Session serial number executing the statement being monitored."
            },
            "px_is_cross_instance":{
                "type":"string",
                "description":"Indicates whether the SQL statement ran parallel across multiple instances (Y) or not (N)."
            },
            "px_maxdop":{
                "type":"integer",
                "description":"Maximum degree of parallelism for any plan operation executed on behalf of the monitored SQL."
            },
            "px_maxdop_instances":{
                "type":"integer",
                "description":"Number of database instances touched at the maximum degree of parallelism."
            },
            "px_servers_requested":{
                "type":"integer",
                "description":"Total number of parallel execution servers requested to execute the monitored SQL."
            },
            "px_servers_allocated":{
                "type":"integer",
                "description":"Actual number of parallel execution servers allocated to execute the query"
            },
            "px_server#":{
                "type":"integer",
                "description":"Logical parallel execution server process number executing (or having executed) the statement being monitored; NULL if this monitoring entry is not associated with an execution server. This is a logical number within the parallel server set (see SERVER# in V$PX_SESSION)."
            },
            "px_server_group":{
                "type":"integer",
                "description":"Logical parallel execution server group number to which PX_SERVER# belongs (see SERVER_GROUP in V$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server. This value is generally 1 unless the SQL statement has one or more parallel sub-queries."
            },
            "px_server_set":{
                "type":"integer",
                "description":"Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server."
            },
            "px_qcinst_id":{
                "type":"integer",
                "description":"Instance identifier where the parallel execution coordinator runs; NULL if PX_SERVER# is NULL."
            },
            "px_qcsid":{
                "type":"integer",
                "description":"Session identifier for the parallel execution coordinator; NULL if PX_SERVER# is NULL."
            },
            "error_number":{
                "type":"string",
                "description":"Error number encountered in case a SQL fails to execute successfully (for example, 932 in case of ORA-00932)."
            },
            "error_facility":{
                "type":"string",
                "description":"Error facility in case a SQL fails to execute successfully (for example, ORA in case of ORA-00932)."
            },
            "error_message":{
                "type":"string",
                "description":"Detailed error message displayed corresponding to the error number and error facility when a SQL fails to execute successfully."
            },
            "binds_xml":{
                "type":"string",
                "description":"Information about bind variables used with the SQL, such as name, position, value, data type, and so on (stored in XML format)."
            },
            "other_xml":{
                "type":"string",
                "description":"Additional information about SQL execution stored in XML format."
            },
            "elapsed_time":{
                "type":"integer",
                "description":"Elapsed time (in microseconds); updated as the statement executes."
            },
            "queuing_time":{
                "type":"integer",
                "description":"Duration of time (in microseconds) spent by SQL in the statement queue."
            },
            "cpu_time":{
                "type":"integer",
                "description":"CPU time (in microseconds); updated as the statement executes."
            },
            "fetches":{
                "type":"integer",
                "description":"Number of fetches associated with the SQL statement; updated as the statement executes."
            },
            "buffer_gets":{
                "type":"integer",
                "description":"Number of buffer get operations; updated as the statement executes."
            },
            "disk_reads":{
                "type":"integer",
                "description":"Number of disk reads; updated as the statement executes."
            },
            "direct_writes":{
                "type":"integer",
                "description":"Number of direct writes; updated as the statement executes."
            },
            "io_interconnect_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes exchanged between Oracle Database and the storage system."
            },
            "physical_read_requests":{
                "type":"integer",
                "description":"Number of physical read I/O requests issued by the monitored SQL."
            },
            "physical_read_bytes":{
                "type":"integer",
                "description":"Number of bytes read from disks by the monitored SQL."
            },
            "physical_write_requests":{
                "type":"integer",
                "description":"Number of physical write I/O requests issued by the monitored SQL."
            },
            "physical_write_bytes":{
                "type":"integer",
                "description":"Number of bytes written to disks by the monitored SQL."
            },
            "application_wait_time":{
                "type":"integer",
                "description":"Application wait time (in microseconds); updated as the statement executes."
            },
            "concurrency_wait_time":{
                "type":"integer",
                "description":"Concurrency wait time (in microseconds); updated as the statement executes."
            },
            "cluster_wait_time":{
                "type":"integer",
                "description":"Cluster wait time (in microseconds); updated as the statement executes."
            },
            "user_io_wait_time":{
                "type":"integer",
                "description":"User I/O Wait Time (in microseconds); updated as the statement executes."
            },
            "plsql_exec_time":{
                "type":"integer",
                "description":"PL/SQL execution time (in microseconds); updated as the statement executes."
            },
            "java_exec_time":{
                "type":"integer",
                "description":"Java execution time (in microseconds); updated as the statement executes."
            },
            "rm_last_action":{
                "type":"string",
                "description":"The most recent action that was taken on this SQL operation by Resource Manager."
            },
            "rm_last_action_reason":{
                "type":"string",
                "description":"The reason for the most recent action that was taken on this SQL operation by Resource Manager."
            },
            "rm_last_action_time":{
                "type":"string",
                "description":"The time of the most recent action that was taken on this SQL operation by Resource Manager."
            },
            "rm_consumer_group":{
                "type":"string",
                "description":"The current consumer group for this SQL operation."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "con_name":{
                "type":"string",
                "description":"Container name of the object. The value of this column is NULL in non-CDBs."
            },
            "ecid":{
                "type":"string",
                "description":"Execution context identifier (sent by Application Server)."
            },
            "is_adaptive_plan":{
                "type":"string",
                "description":"Indicates whether the statistics are from an adaptive plan (Y) or not (N)."
            },
            "is_final_plan":{
                "type":"string",
                "description":"Indicates whether the statistics are from the final plan (Y) or not (N)."
            },
            "in_dbop_name":{
                "type":"string",
                "description":"If the SQL that is monitored was executed by a session that was also monitored by a database operation (DBOP), then this column specifies the name of that DBOP."
            },
            "in_dbop_exec_id":{
                "type":"integer",
                "description":"If the SQL that is monitored was executed by a session that was also monitored by a database operation (DBOP), then this column specifies the execution ID of that DBO."
            },
            "io_cell_uncompressed_bytes":{
                "type":"integer",
                "description":"Number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
            },
            "io_cell_offload_eligible_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes which can be filtered by the Exadata storage system."
            },
            "io_cell_offload_returned_bytes":{
                "type":"integer",
                "description":"Number of filtered bytes returned by Exadata cells (that is, the number of bytes returned after  processing has been offloaded on the Exadata cells)."
            },
            "current_user":{
                "type":"integer",
                "description":"Unique number identifying the current user."
            },
            "current_username":{
                "type":"integer",
                "description":"Username for the current user."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : LinkRelation

Type: `object`

Show Source

- href: string
- rel: string

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string"
            },
            "href":{
                "type":"string"
            }
        },
        "required":[
            "rel",
            "href"
        ]
    }

Back to Top
