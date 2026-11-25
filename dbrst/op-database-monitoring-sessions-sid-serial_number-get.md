Returns the GV\$SESSION for the specified Session Identifier and Session Serial Number. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- serial_number: number
  Session serial number.
- sid: number
  Session identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on the specified session.

Body ()

Root Schema : MonitoringSessionsItem

Type: `object`

This object represents a record from GV\$SESSION view. GV\$SESSION displays session information for each current session. The list of attributes may vary depending on database version.

Show Source

- action(optional): string
  Name of the currently executing action as set by calling the DBMS_APPLICATION_INFO.SET_ACTION procedure.
- action_hash(optional): integer
  Hash value of the ACTION column.
- audsid(optional): integer
  Auditing session ID.
- blocking_instance(optional): integer
  Instance identifier of the blocking session. This column is valid only if BLOCKING_SESSION_STATUS has the value VALID.
- blocking_session(optional): integer
  Session identifier of the blocking session. This column is valid only if BLOCKING_SESSION_STATUS has the value VALID.
- blocking_session_status(optional): string
  This column provides details on whether there is a blocking session.
- client_identifier(optional): string
  Client identifier of the session.
- client_info(optional): string
  Information set by the DBMS_APPLICATION_INFO.SET_CLIENT_INFO procedure.
- command(optional): integer
  Command in progress (last statement parsed).
- con_id(optional): integer
  The ID of the container to which the data pertains.
- creator_addr(optional): string
  Address of the creating process or circuit.
- creator_serial#(optional): integer
  Serial number of the creating process or circuit.
- current_queue_duration(optional): integer
  If queued (1), the current amount of time the session has been queued. If not currently queued, the value is 0.
- ecid(optional): string
  Execution context identifier (sent by Application Server).
- event(optional): string
  If the session is currently waiting, then the resource or event for which the session is waiting. If the session is not in a wait, then the resource or event for which the session most recently waited.
- event#(optional): integer
  If the session is currently waiting, then the number of the resource or event for which the session is waiting. If the session is not in a wait, then the number of the resource or event for which the session most recently waited.
- external_name(optional): string
  External name of the database user. For enterprise users, returns the Oracle Internet Directory DN.
- failed_over(optional): string
  Indicates whether the session is running in failover mode and failover has occurred (YES) or not (NO).
- failover_method(optional): string
  Indicates the transparent application failover method for the session.
- failover_type(optional): string
  Indicates whether and to what extent transparent application failover (TAF) is enabled for the session.
- final_blocking_instance(optional): integer
  Instance identifier of the final blocking session. This column is valid only if FINAL_BLOCKING_SESSION_STATUS has the value VALID.
- final_blocking_session(optional): integer
  Session identifier of the blocking session. This column is valid only if FINAL_BLOCKING_SESSION_STATUS has the value VALID.
- final_blocking_session_status(optional): string
  The final blocking session is the final element in the wait chain constructed by following the sessions that are blocked by one another starting with this session. In the case of a cyclical wait chain, one of the sessions in the wait chain will be chosen as the final blocker.
- fixed_table_sequence(optional): integer
  This contains a number that increases every time the session completes a call to the database and there has been an intervening select from a dynamic performance table. This column can be used by performance monitors to monitor statistics in the database.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- last_call_et(optional): integer
  If the session STATUS is currently ACTIVE, then the value represents the elapsed time (in seconds) since the session has become active. If the session STATUS is currently INACTIVE, then the value represents the elapsed time (in seconds) since the session has become inactive.
- links(optional): array links
- lockwait(optional): string
  Address of the lock the session is waiting for; NULL if none.
- logon_time(optional): string
  Time of logon.
- machine(optional): string
  Operating system machine name.
- module(optional): string
  Name of the currently executing module as set by calling the DBMS_APPLICATION_INFO.SET_MODULE procedure.
- module_hash(optional): integer
  Hash value of the MODULE column.
- osuser(optional): string
  Operating system client user name.
- ownerid(optional): integer
  Identifier of the user who owns the migratable session.
- p1(optional): integer
  First wait event parameter (in decimal).
- p1raw(optional): string
  First wait event parameter (in hexadecimal).
- p1text(optional): string
  Description of the first wait event parameter.
- p2(optional): integer
  Second wait event parameter (in decimal).
- p2raw(optional): string
  Second wait event parameter (in hexadecimal).
- p2text(optional): string
  Description of the second wait event parameter.
- p3(optional): integer
  Third wait event parameter (in decimal).
- p3raw(optional): string
  Third wait event parameter (in hexadecimal).
- p3text(optional): string
  Description of the third wait event parameter.
- paddr(optional): string
  Address of the process that owns the session.
- pddl_status(optional): string
  If ENABLED, the session is in a PARALLEL DDL enabled mode. If DISABLED, PARALLEL DDL enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL DDL.
- pdml_enabled(optional): string
  This column has been replaced by the PDML_STATUS column.
- pdml_status(optional): string
  If ENABLED, the session is in a PARALLEL DML enabled mode. If DISABLED, PARALLEL DML enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL DML.
- pga_tunable_mem(optional): integer
  The amount of tunable PGA memory (in bytes).
- plsql_debugger_connected(optional): string
  Indicates whether the session is connected to a PL/SQL debugger.
- plsql_entry_object_id(optional): integer
  Object ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack.
- plsql_entry_subprogram_id(optional): integer
  Subprogram ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack.
- plsql_object_id(optional): integer
  Object ID of the currently executing PL/SQL subprogram; NULL if executing SQL.
- plsql_subprogram_id(optional): integer
  Subprogram ID of the currently executing PL/SQL object; NULL if executing SQL.
- port(optional): integer
  Client port number.
- pq_status(optional): string
  If ENABLED, the session is in a PARALLEL QUERY enabled mode. If DISABLED, PARALLEL QUERY enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL QUERY.
- prev_child_number(optional): integer
  Child number of the last SQL statement executed.
- prev_exec_id(optional): integer
  SQL execution identifier of the last executed SQL statement.
- prev_exec_start(optional): string
  SQL execution start of the last executed SQL statement.
- prev_hash_value(optional): integer
  Used with SQL_HASH_VALUE to identify the last SQL statement executed.
- prev_sql_addr(optional): string
  Used with PREV_HASH_VALUE to identify the last SQL statement executed.
- prev_sql_id(optional): string
  SQL identifier of the last SQL statement executed.
- process(optional): string
  Operating system client process ID.
- program(optional): string
  Operating system program name.
- resource_consumer_group(optional): string
  Name of the session's current resource consumer group.
- row_wait_block#(optional): integer
  Identifier for the block containing the row specified in row_wait_row#. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1.
- row_wait_file#(optional): integer
  Identifier for the data file containing the row specified in row_wait_row#. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1.
- row_wait_obj#(optional): integer
  Object ID for the table containing the row specified in row_wait_row#.
- row_wait_row#(optional): integer
  Current row being locked. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1.
- saddr(optional): string
  Session address.
- schema#(optional): integer
  Schema user identifier.
- schemaname(optional): string
  Schema user name.
- seconds_in_wait(optional): integer
  If the session is currently waiting, then the value is the amount of time waited for the current wait. If the session is not in a wait, then the value is the amount of time since the start of the last wait.
- seq#(optional): integer
  A number that uniquely identifies the current or last wait (incremented for each wait).
- serial#(optional): integer
  Session serial number. Used to uniquely identify a session's objects. Guarantees that session-level commands are applied to the correct session objects if the session ends and another session begins with the same session ID.
- server(optional): string
  Server type.
- service_name(optional): string
  Service name of the session.
- session_edition_id(optional): integer
  Shows the value that, in the session, would be reported by sys_context('USERENV', 'SESSION_EDITION_ID').
- shard_ddl_status(optional): string
  Indicates whether shard DDL is enabled in the current session (ENABLED) or not (DISABLED). This value is only relevant for the shard catalog database.
- sid(optional): integer
  Session identifier.
- sql_address(optional): string
  Used with sql_hash_value to identify the SQL statement that is currently being executed.
- sql_child_number(optional): integer
  Child number of the SQL statement that is currently being executed.
- sql_exec_id(optional): integer
  SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started.
- sql_exec_start(optional): string
  Time when the execution of the SQL currently executed by this session started; NULL if SQL_ID is NULL.
- sql_hash_value(optional): integer
  Used with SQL_ADDRESS to identify the SQL statement that is currently being executed.
- sql_id(optional): string
  SQL identifier of the SQL statement that is currently being executed.
- sql_trace(optional): string
  Indicates whether SQL tracing is enabled (ENABLED) or disabled (DISABLED).
- sql_trace_binds(optional): string
  Indicates whether bind tracing is enabled (TRUE) or not (FALSE).
- sql_trace_plan_stats(optional): string
  Frequency at which row source statistics are dumped in the trace files for each cursor.
- sql_trace_waits(optional): string
  Indicates whether wait tracing is enabled (TRUE) or not (FALSE).
- sql_translation_profile_id(optional): integer
  Object number of the SQL translation profile.
- state(optional): string
  Wait state.
- status(optional): string
  Status of the session.
- taddr(optional): string
  Address of the transaction state object.
- terminal(optional): string
  Operating system terminal name.
- time_remaining_micro(optional): integer
  Amount of time remaining remaining before a timeout. This field may indicate that a timeout has occurred, or that no timeout will occur.
- time_since_last_wait_micro(optional): integer
  Time elapsed since the end of the last wait (in microseconds). If the session is currently in a wait, then the value is 0.
- top_level_call#(optional): integer
  Oracle top level call number.
- type(optional): string
  Session type.
- user#(optional): integer
  Oracle user identifier.
- username(optional): string
  Oracle username.
- wait_class(optional): string
  Name of the class of the wait event.
- wait_class#(optional): integer
  Number of the class of the wait event.
- wait_class_id(optional): integer
  Identifier of the class of the wait event.
- wait_time(optional): integer
  If the session is currently waiting, then the value is 0. If the session is not in a wait, then the value indicates the duration of the last wait.
- wait_time_micro(optional): integer
  Amount of time waited (in microseconds). If the session is currently waiting, then the value is the time spent in the current wait. If the session is currently not in a wait, then the value is the amount of time waited in the last wait.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a record from GV$SESSION view. GV$SESSION displays session information for each current session. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "saddr":{
                "type":"string",
                "description":"Session address."
            },
            "sid":{
                "type":"integer",
                "description":"Session identifier."
            },
            "serial#":{
                "type":"integer",
                "description":"Session serial number. Used to uniquely identify a session's objects. Guarantees that session-level commands are applied to the correct session objects if the session ends and another session begins with the same session ID."
            },
            "audsid":{
                "type":"integer",
                "description":"Auditing session ID."
            },
            "paddr":{
                "type":"string",
                "description":"Address of the process that owns the session."
            },
            "user#":{
                "type":"integer",
                "description":"Oracle user identifier."
            },
            "username":{
                "type":"string",
                "description":"Oracle username."
            },
            "command":{
                "type":"integer",
                "description":"Command in progress (last statement parsed)."
            },
            "ownerid":{
                "type":"integer",
                "description":"Identifier of the user who owns the migratable session."
            },
            "taddr":{
                "type":"string",
                "description":"Address of the transaction state object."
            },
            "lockwait":{
                "type":"string",
                "description":"Address of the lock the session is waiting for; NULL if none."
            },
            "status":{
                "type":"string",
                "description":"Status of the session."
            },
            "server":{
                "type":"string",
                "description":"Server type."
            },
            "schema#":{
                "type":"integer",
                "description":"Schema user identifier."
            },
            "schemaname":{
                "type":"string",
                "description":"Schema user name."
            },
            "osuser":{
                "type":"string",
                "description":"Operating system client user name."
            },
            "process":{
                "type":"string",
                "description":"Operating system client process ID."
            },
            "machine":{
                "type":"string",
                "description":"Operating system machine name."
            },
            "port":{
                "type":"integer",
                "description":"Client port number."
            },
            "terminal":{
                "type":"string",
                "description":"Operating system terminal name."
            },
            "program":{
                "type":"string",
                "description":"Operating system program name."
            },
            "type":{
                "type":"string",
                "description":"Session type."
            },
            "sql_address":{
                "type":"string",
                "description":"Used with sql_hash_value to identify the SQL statement that is currently being executed."
            },
            "sql_hash_value":{
                "type":"integer",
                "description":"Used with SQL_ADDRESS to identify the SQL statement that is currently being executed."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the SQL statement that is currently being executed."
            },
            "sql_child_number":{
                "type":"integer",
                "description":"Child number of the SQL statement that is currently being executed."
            },
            "sql_exec_start":{
                "type":"string",
                "description":"Time when the execution of the SQL currently executed by this session started; NULL if SQL_ID is NULL."
            },
            "sql_exec_id":{
                "type":"integer",
                "description":"SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started."
            },
            "prev_sql_addr":{
                "type":"string",
                "description":"Used with PREV_HASH_VALUE to identify the last SQL statement executed."
            },
            "prev_hash_value":{
                "type":"integer",
                "description":"Used with SQL_HASH_VALUE to identify the last SQL statement executed."
            },
            "prev_sql_id":{
                "type":"string",
                "description":"SQL identifier of the last SQL statement executed."
            },
            "prev_child_number":{
                "type":"integer",
                "description":"Child number of the last SQL statement executed."
            },
            "prev_exec_start":{
                "type":"string",
                "description":"SQL execution start of the last executed SQL statement."
            },
            "prev_exec_id":{
                "type":"integer",
                "description":"SQL execution identifier of the last executed SQL statement."
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
            "module":{
                "type":"string",
                "description":"Name of the currently executing module as set by calling the DBMS_APPLICATION_INFO.SET_MODULE procedure."
            },
            "module_hash":{
                "type":"integer",
                "description":"Hash value of the MODULE column."
            },
            "action":{
                "type":"string",
                "description":"Name of the currently executing action as set by calling the DBMS_APPLICATION_INFO.SET_ACTION procedure."
            },
            "action_hash":{
                "type":"integer",
                "description":"Hash value of the ACTION column."
            },
            "client_info":{
                "type":"string",
                "description":"Information set by the DBMS_APPLICATION_INFO.SET_CLIENT_INFO procedure."
            },
            "fixed_table_sequence":{
                "type":"integer",
                "description":"This contains a number that increases every time the session completes a call to the database and there has been an intervening select from a dynamic performance table. This column can be used by performance monitors to monitor statistics in the database."
            },
            "row_wait_obj#":{
                "type":"integer",
                "description":"Object ID for the table containing the row specified in row_wait_row#."
            },
            "row_wait_file#":{
                "type":"integer",
                "description":"Identifier for the data file containing the row specified in row_wait_row#. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1."
            },
            "row_wait_block#":{
                "type":"integer",
                "description":"Identifier for the block containing the row specified in row_wait_row#. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1."
            },
            "row_wait_row#":{
                "type":"integer",
                "description":"Current row being locked. This property is valid only if the session is currently waiting for another transaction to commit and the value of row_wait_obj# is not -1."
            },
            "top_level_call#":{
                "type":"integer",
                "description":"Oracle top level call number."
            },
            "logon_time":{
                "type":"string",
                "description":"Time of logon."
            },
            "last_call_et":{
                "type":"integer",
                "description":"If the session STATUS is currently ACTIVE, then the value represents the elapsed time (in seconds) since the session has become active. If the session STATUS is currently INACTIVE, then the value represents the elapsed time (in seconds) since the session has become inactive."
            },
            "pdml_enabled":{
                "type":"string",
                "description":"This column has been replaced by the PDML_STATUS column."
            },
            "failover_type":{
                "type":"string",
                "description":"Indicates whether and to what extent transparent application failover (TAF) is enabled for the session."
            },
            "failover_method":{
                "type":"string",
                "description":"Indicates the transparent application failover method for the session."
            },
            "failed_over":{
                "type":"string",
                "description":"Indicates whether the session is running in failover mode and failover has occurred (YES) or not (NO)."
            },
            "resource_consumer_group":{
                "type":"string",
                "description":"Name of the session's current resource consumer group."
            },
            "pdml_status":{
                "type":"string",
                "description":"If ENABLED, the session is in a PARALLEL DML enabled mode. If DISABLED, PARALLEL DML enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL DML."
            },
            "pddl_status":{
                "type":"string",
                "description":"If ENABLED, the session is in a PARALLEL DDL enabled mode. If DISABLED, PARALLEL DDL enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL DDL."
            },
            "pq_status":{
                "type":"string",
                "description":"If ENABLED, the session is in a PARALLEL QUERY enabled mode. If DISABLED, PARALLEL QUERY enabled mode is not supported for the session. If FORCED, the session has been altered to force PARALLEL QUERY."
            },
            "current_queue_duration":{
                "type":"integer",
                "description":"If queued (1), the current amount of time the session has been queued. If not currently queued, the value is 0."
            },
            "client_identifier":{
                "type":"string",
                "description":"Client identifier of the session."
            },
            "blocking_session_status":{
                "type":"string",
                "description":"This column provides details on whether there is a blocking session."
            },
            "blocking_instance":{
                "type":"integer",
                "description":"Instance identifier of the blocking session. This column is valid only if BLOCKING_SESSION_STATUS has the value VALID."
            },
            "blocking_session":{
                "type":"integer",
                "description":"Session identifier of the blocking session. This column is valid only if BLOCKING_SESSION_STATUS has the value VALID."
            },
            "final_blocking_session_status":{
                "type":"string",
                "description":"The final blocking session is the final element in the wait chain constructed by following the sessions that are blocked by one another starting with this session. In the case of a cyclical wait chain, one of the sessions in the wait chain will be chosen as the final blocker."
            },
            "final_blocking_instance":{
                "type":"integer",
                "description":"Instance identifier of the final blocking session. This column is valid only if FINAL_BLOCKING_SESSION_STATUS has the value VALID."
            },
            "final_blocking_session":{
                "type":"integer",
                "description":"Session identifier of the blocking session. This column is valid only if FINAL_BLOCKING_SESSION_STATUS has the value VALID."
            },
            "seq#":{
                "type":"integer",
                "description":"A number that uniquely identifies the current or last wait (incremented for each wait)."
            },
            "event#":{
                "type":"integer",
                "description":"If the session is currently waiting, then the number of the resource or event for which the session is waiting. If the session is not in a wait, then the number of the resource or event for which the session most recently waited."
            },
            "event":{
                "type":"string",
                "description":"If the session is currently waiting, then the resource or event for which the session is waiting. If the session is not in a wait, then the resource or event for which the session most recently waited."
            },
            "p1text":{
                "type":"string",
                "description":"Description of the first wait event parameter."
            },
            "p1":{
                "type":"integer",
                "description":"First wait event parameter (in decimal)."
            },
            "p1raw":{
                "type":"string",
                "description":"First wait event parameter (in hexadecimal)."
            },
            "p2text":{
                "type":"string",
                "description":"Description of the second wait event parameter."
            },
            "p2":{
                "type":"integer",
                "description":"Second wait event parameter (in decimal)."
            },
            "p2raw":{
                "type":"string",
                "description":"Second wait event parameter (in hexadecimal)."
            },
            "p3text":{
                "type":"string",
                "description":"Description of the third wait event parameter."
            },
            "p3":{
                "type":"integer",
                "description":"Third wait event parameter (in decimal)."
            },
            "p3raw":{
                "type":"string",
                "description":"Third wait event parameter (in hexadecimal)."
            },
            "wait_class_id":{
                "type":"integer",
                "description":"Identifier of the class of the wait event."
            },
            "wait_class#":{
                "type":"integer",
                "description":"Number of the class of the wait event."
            },
            "wait_class":{
                "type":"string",
                "description":"Name of the class of the wait event."
            },
            "wait_time":{
                "type":"integer",
                "description":"If the session is currently waiting, then the value is 0. If the session is not in a wait, then the value indicates the duration of the last wait."
            },
            "seconds_in_wait":{
                "type":"integer",
                "description":"If the session is currently waiting, then the value is the amount of time waited for the current wait. If the session is not in a wait, then the value is the amount of time since the start of the last wait."
            },
            "state":{
                "type":"string",
                "description":"Wait state."
            },
            "wait_time_micro":{
                "type":"integer",
                "description":"Amount of time waited (in microseconds). If the session is currently waiting, then the value is the time spent in the current wait. If the session is currently not in a wait, then the value is the amount of time waited in the last wait."
            },
            "time_remaining_micro":{
                "type":"integer",
                "description":"Amount of time remaining remaining before a timeout. This field may indicate that a timeout has occurred, or that no timeout will occur."
            },
            "time_since_last_wait_micro":{
                "type":"integer",
                "description":"Time elapsed since the end of the last wait (in microseconds). If the session is currently in a wait, then the value is 0."
            },
            "service_name":{
                "type":"string",
                "description":"Service name of the session."
            },
            "sql_trace":{
                "type":"string",
                "description":"Indicates whether SQL tracing is enabled (ENABLED) or disabled (DISABLED)."
            },
            "sql_trace_waits":{
                "type":"string",
                "description":"Indicates whether wait tracing is enabled (TRUE) or not (FALSE)."
            },
            "sql_trace_binds":{
                "type":"string",
                "description":"Indicates whether bind tracing is enabled (TRUE) or not (FALSE)."
            },
            "sql_trace_plan_stats":{
                "type":"string",
                "description":"Frequency at which row source statistics are dumped in the trace files for each cursor."
            },
            "session_edition_id":{
                "type":"integer",
                "description":"Shows the value that, in the session, would be reported by sys_context('USERENV', 'SESSION_EDITION_ID')."
            },
            "creator_addr":{
                "type":"string",
                "description":"Address of the creating process or circuit."
            },
            "creator_serial#":{
                "type":"integer",
                "description":"Serial number of the creating process or circuit."
            },
            "ecid":{
                "type":"string",
                "description":"Execution context identifier (sent by Application Server)."
            },
            "sql_translation_profile_id":{
                "type":"integer",
                "description":"Object number of the SQL translation profile."
            },
            "pga_tunable_mem":{
                "type":"integer",
                "description":"The amount of tunable PGA memory (in bytes)."
            },
            "shard_ddl_status":{
                "type":"string",
                "description":"Indicates whether shard DDL is enabled in the current session (ENABLED) or not (DISABLED). This value is only relevant for the shard catalog database."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "external_name":{
                "type":"string",
                "description":"External name of the database user. For enterprise users, returns the Oracle Internet Directory DN."
            },
            "plsql_debugger_connected":{
                "type":"string",
                "description":"Indicates whether the session is connected to a PL/SQL debugger."
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
