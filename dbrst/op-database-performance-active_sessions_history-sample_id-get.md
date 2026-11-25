Oracle Diagnostics Pack licence is required for this service. Returns specified records from GV\$ACTIVE_SESSION_HISTORY. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- sample_id: number
  ID of the sample.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Active session history record.

Body ()

Root Schema : PerformanceActionSessionHistoriesItem

Type: `object`

This object represents a sampled session activity in the database from GV\$ACTIVE_SESSION_HISTORY. It contains snapshots of active database sessions taken once a second. A database session is considered active if it was on the CPU or was waiting for an event that didn't belong to the Idle wait class. The list of attributes may vary depending on database version.

Show Source

- action(optional): string
  Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_ACTION procedure.
- blocking_hangchain_info(optional): string
  Indicates whether the information about BLOCKING_SESSION comes from the hang chain (Y) or not (N).
- blocking_inst_id(optional): integer
  Instance number of the blocker shown in BLOCKING_SESSION.
- blocking_session(optional): integer
  Session identifier of the blocking session. Populated only if the blocker is on the same instance and the session was waiting for enqueues or a 'buffer busy' wait.
- blocking_session_serial#(optional): integer
  Serial number of the blocking session.
- blocking_session_status(optional): string
  Status of the blocking session.
- capture_overhead(optional): string
  Indicates whether the session is executing capture code (Y) or not (N).
- client_id(optional): string
  Client identifier of the session.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- consumer_group_id(optional): integer
  Consumer group ID.
- current_block#(optional): integer
  ID of the block that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events.
- current_file#(optional): integer
  File number of the file containing the block that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events.
- current_obj#(optional): integer
  Object ID of the object that the session is referencing. This information is only available if the session was waiting for application, cluster, concurrency, and user I/O wait events.
- current_row#(optional): integer
  Row identifier that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events.
- dbop_exec_id(optional): integer
  Database operation execution identifier for the current execution. If the type is SQL, the DBOP_EXEC_ID will be NULL.
- dbop_name(optional): string
  Database operation name. If the type is SQL, the DBOP_NAME will be NULL.
- dbreplay_call_counter(optional): integer
  If the session is being captured or replayed, then DBREPLAY_CALL_COUNTER is the call counter of the user call that is being captured or replayed; otherwise it is NULL.
- dbreplay_file_id(optional): integer
  If the session is being captured or replayed, then DBREPLAY_FILE_ID is the file ID for the workload capture or workload replay; otherwise it is NULL.
- delta_interconnect_io_bytes(optional): integer
  Number of I/O bytes sent over the I/O interconnect over the last DELTA_TIME microseconds.
- delta_read_io_bytes(optional): integer
  Number of I/O bytes read by this session over the last DELTA_TIME microseconds.
- delta_read_io_requests(optional): integer
  Number of read I/O requests made by this session over the last DELTA_TIME microseconds.
- delta_read_mem_bytes(optional): integer
  Number of read bytes through the buffer cache.
- delta_time(optional): integer
  Time interval (in microseconds) since the last time this session was sampled or created, over which the next five statistics are accumulated.
- delta_write_io_bytes(optional): integer
  Number of I/O bytes written by this session over the last DELTA_TIME microseconds.
- delta_write_io_requests(optional): integer
  Number of write I/O requests made by this session over the last DELTA_TIME microseconds.
- ecid(optional): string
  Execution context identifier (sent by Application Server).
- event(optional): string
  If SESSION_STATE = WAITING, then the event for which the session was waiting for at the time of sampling. If SESSION_STATE = ON CPU, then this column is NULL.
- event#(optional): integer
  Number of the resource or event for which the session is waiting or for which the session last waited. Interpretation is similar to that of the EVENT column.
- event_id(optional): integer
  Identifier of the resource or event for which the session is waiting or for which the session last waited. Interpretation is similar to that of the EVENT column.
- force_matching_signature(optional): integer
  Signature used when the CURSOR_SHARING parameter is set to FORCE.
- in_bind(optional): string
  Indicates whether the session was doing bind operations at the time of sampling (Y) or not (N).
- in_connection_mgmt(optional): string
  Indicates whether the session was doing connection management at the time of sampling (Y) or not (N).
- in_cursor_close(optional): string
  Indicates whether the session was closing a cursor at the time of sampling (Y) or not (N).
- in_hard_parse(optional): string
  Indicates whether the session was hard parsing at the time of sampling (Y) or not (N).
- in_inmemory_populate(optional): string
  Indicates whether the session was populating the IM column store at the time of sampling (Y) or not (N).
- in_inmemory_prepopulate(optional): string
  Indicates whether the session was prepopulating the IM column store at the time of sampling (Y) or not (N).
- in_inmemory_query(optional): string
  Indicates whether the session was querying the In-Memory Column Store (IM column store) at the time of sampling (Y) or not (N).
- in_inmemory_repopulate(optional): string
  Indicates whether the session was repopulating the IM column store at the time of sampling (Y) or not (N).
- in_inmemory_trepopulate(optional): string
  Indicates whether the session was trickle repopulating the IM column store at the time of sampling (Y) or not (N).
- in_java_execution(optional): string
  Indicates whether the session was executing Java at the time of sampling (Y) or not (N).
- in_parse(optional): string
  Indicates whether the session was parsing at the time of sampling (Y) or not (N).
- in_plsql_compilation(optional): string
  Indicates whether the session was compiling PL/SQL at the time of sampling (Y) or not (N).
- in_plsql_execution(optional): string
  Indicates whether the session was executing PL/SQL at the time of sampling (Y) or not (N).
- in_plsql_rpc(optional): string
  Indicates whether the session was executing inbound PL/SQL RPC calls at the time of sampling (Y) or not (N).
- in_sequence_load(optional): string
  Indicates whether the session is loading in sequence (in sequence load code) (Y) or not (N).
- in_sql_execution(optional): string
  Indicates whether the session was executing SQL statements at the time of sampling (Y) or not (N).
- in_tablespace_encryption(optional): string
  Indicates whether encryption or decryption of a tablespace occurred at the time of sampling (Y) or not (N).
- inst_id(optional): integer
  Instance number from which the associated GV\$ACTIVE_SESSION_HISTORY view information was obtained.
- is_awr_sample(optional): string
  Indicates whether this sample has been flushed or will be flushed to the Automatic Workload Repository (DBA_HIST_ACTIVE_SESS_HISTORY) (Y) or not (N).
- is_captured(optional): string
  Indicates whether the session is being captured (Y) or not (N).
- is_replay_sync_token_holder(optional): string
  Indicates whether the session is holding a synchronization token (Y) or not (N) during workload replay.
- is_replayed(optional): string
  Indicates whether the session is being replayed (Y) or not (N).
- is_sqlid_current(optional): string
  Indicates whether the SQL identifier in the SQL_ID column is being executed (Y) or not (N).
- links(optional): array links
- machine(optional): string
  Client's operating system machine name.
- module(optional): string
  Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_MODULE procedure.
- p1(optional): integer
  First wait event parameter (in decimal).
- p1text(optional): string
  Description of the first wait event parameter.
- p2(optional): integer
  Second wait event parameter (in decimal).
- p2text(optional): string
  Description of the second wait event parameter.
- p3(optional): integer
  Third wait event parameter (in decimal).
- p3text(optional): string
  Description of the third wait event parameter.
- pga_allocated(optional): integer
  Amount of PGA memory (in bytes) consumed by this session at the time this sample was taken.
- plsql_entry_object_id(optional): integer
  Object ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack. Maps to DBA_OBJECTS.OBJECT_ID.
- plsql_entry_subprogram_id(optional): integer
  Subprogram ID of the top-most PL/SQL subprogram on the stack. Maps to DBA_OBJECTS.DATA_OBJECT_ID.
- plsql_object_id(optional): integer
  Object ID of the currently executing PL/SQL subprogram.
- plsql_subprogram_id(optional): integer
  Subprogram ID of the currently executing PL/SQL object.
- port(optional): integer
  Client port number.
- program(optional): string
  Name of the operating system program.
- qc_instance_id(optional): integer
  Query coordinator instance ID. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0.
- qc_session_id(optional): integer
  Query coordinator session ID. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0.
- qc_session_serial#(optional): integer
  Query coordinator session serial number. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0.
- remote_instance#(optional): integer
  Remote instance identifier that will serve the block that this session is waiting for. This information is only available if the session was waiting for cluster events.
- replay_overhead(optional): string
  Indicates whether the session is executing replay code (Y) or not (N).
- sample_id(optional): integer
  ID of the sample.
- sample_time(optional): string
  Time at which the sample was taken.
- seq#(optional): integer
  Sequence number that uniquely identifies the wait (incremented for each wait).
- service_hash(optional): integer
  Hash that identifies the Service.
- session_id(optional): integer
  Session identifier; maps to GV\$SESSION.SID.
- session_serial#(optional): integer
  Session serial number (used to uniquely identify a session's objects); maps to GV\$SESSION.SERIAL#.
- session_state(optional): string
  Session state.
- session_type(optional): string
  Session type.
- sql_adaptive_plan_resolved(optional): integer
  Indicates whether the SQL plan of the sampled database session is a resolved adaptive plan or not.
- sql_child_number(optional): integer
  Child number of the SQL statement that the session was executing at the time of sampling.
- sql_exec_id(optional): integer
  SQL execution identifier.
- sql_exec_start(optional): string
  Time when the execution of the SQL started.
- sql_full_plan_hash_value(optional): integer
  Numerical representation of the complete SQL plan for the cursor being executed by this session.
- sql_id(optional): string
  SQL identifier of the SQL statement that the session was executing at the time of sampling.
- sql_opcode(optional): integer
  Indicates what phase of operation the SQL statement was in.
- sql_opname(optional): string
  SQL command name.
- sql_plan_hash_value(optional): integer
  Numeric representation of the SQL plan for the cursor. This information might not be available for all session samples.
- sql_plan_line_id(optional): integer
  SQL plan line ID.
- sql_plan_operation(optional): string
  Plan operation name.
- sql_plan_options(optional): string
  Plan operation options.
- temp_space_allocated(optional): integer
  Amount of TEMP memory (in bytes) consumed by this session at the time this sample was taken.
- time_model(optional): integer
  Time model information.
- time_waited(optional): integer
  If SESSION_STATE = WAITING, then the time that the session actually spent waiting for that event (in microseconds). This column is set for waits that were in progress at the time the sample was taken. If a wait event lasted for more than a second and was caught waiting in more than one session sample row, then the actual time spent waiting for that wait event will be populated in the last of those session sample rows. At any given time, this information will not be available for the latest session sample.
- tm_delta_cpu_time(optional): integer
  Amount of time this session spent on CPU over the last TM_DELTA_TIME microseconds.
- tm_delta_db_time(optional): integer
  Amount of time spent by this session in database calls over the last TM_DELTA_TIME microseconds.
- tm_delta_time(optional): integer
  Time interval (in microseconds) over which TM_DELTA_CPU_TIME and TM_DELTA_DB_TIME are accumulated.
- top_level_call#(optional): integer
  Oracle top level call number.
- top_level_call_name(optional): string
  Oracle top level call name.
- top_level_sql_id(optional): string
  SQL identifier of the top level SQL statement.
- top_level_sql_opcode(optional): integer
  Indicates what phase of operation the top level SQL statement was in.
- user_id(optional): integer
  Oracle user identifier; maps to GV\$SESSION.USER#.
- wait_class(optional): string
  Wait class name of the event for which the session was waiting at the time of sampling.
- wait_class_id(optional): integer
  Wait class identifier of the event for which the session was waiting at the time of sampling.
- wait_time(optional): integer
  Total wait time for the event for which the session last waited if the session was on the CPU when sampled; 0 if the session was waiting at the time of sampling.
- xid(optional): string
  Transaction ID that the session was working on at the time of sampling.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a sampled session activity in the database from GV$ACTIVE_SESSION_HISTORY. It contains snapshots of active database sessions taken once a second. A database session is considered active if it was on the CPU or was waiting for an event that didn't belong to the Idle wait class. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$ACTIVE_SESSION_HISTORY view information was obtained."
            },
            "sample_id":{
                "type":"integer",
                "description":"ID of the sample."
            },
            "sample_time":{
                "type":"string",
                "description":"Time at which the sample was taken."
            },
            "is_awr_sample":{
                "type":"string",
                "description":"Indicates whether this sample has been flushed or will be flushed to the Automatic Workload Repository (DBA_HIST_ACTIVE_SESS_HISTORY) (Y) or not (N)."
            },
            "session_id":{
                "type":"integer",
                "description":"Session identifier; maps to GV$SESSION.SID."
            },
            "session_serial#":{
                "type":"integer",
                "description":"Session serial number (used to uniquely identify a session's objects); maps to GV$SESSION.SERIAL#."
            },
            "session_type":{
                "type":"string",
                "description":"Session type."
            },
            "user_id":{
                "type":"integer",
                "description":"Oracle user identifier; maps to GV$SESSION.USER#."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the SQL statement that the session was executing at the time of sampling."
            },
            "is_sqlid_current":{
                "type":"string",
                "description":"Indicates whether the SQL identifier in the SQL_ID column is being executed (Y) or not (N)."
            },
            "sql_child_number":{
                "type":"integer",
                "description":"Child number of the SQL statement that the session was executing at the time of sampling."
            },
            "sql_opcode":{
                "type":"integer",
                "description":"Indicates what phase of operation the SQL statement was in."
            },
            "force_matching_signature":{
                "type":"integer",
                "description":"Signature used when the CURSOR_SHARING parameter is set to FORCE."
            },
            "top_level_sql_id":{
                "type":"string",
                "description":"SQL identifier of the top level SQL statement."
            },
            "top_level_sql_opcode":{
                "type":"integer",
                "description":"Indicates what phase of operation the top level SQL statement was in."
            },
            "sql_opname":{
                "type":"string",
                "description":"SQL command name."
            },
            "sql_adaptive_plan_resolved":{
                "type":"integer",
                "description":"Indicates whether the SQL plan of the sampled database session is a resolved adaptive plan or not."
            },
            "sql_full_plan_hash_value":{
                "type":"integer",
                "description":"Numerical representation of the complete SQL plan for the cursor being executed by this session."
            },
            "sql_plan_hash_value":{
                "type":"integer",
                "description":"Numeric representation of the SQL plan for the cursor. This information might not be available for all session samples."
            },
            "sql_plan_line_id":{
                "type":"integer",
                "description":"SQL plan line ID."
            },
            "sql_plan_operation":{
                "type":"string",
                "description":"Plan operation name."
            },
            "sql_plan_options":{
                "type":"string",
                "description":"Plan operation options."
            },
            "sql_exec_id":{
                "type":"integer",
                "description":"SQL execution identifier."
            },
            "sql_exec_start":{
                "type":"string",
                "description":"Time when the execution of the SQL started."
            },
            "plsql_entry_object_id":{
                "type":"integer",
                "description":"Object ID of the top-most PL/SQL subprogram on the stack; NULL if there is no PL/SQL subprogram on the stack. Maps to DBA_OBJECTS.OBJECT_ID."
            },
            "plsql_entry_subprogram_id":{
                "type":"integer",
                "description":"Subprogram ID of the top-most PL/SQL subprogram on the stack. Maps to DBA_OBJECTS.DATA_OBJECT_ID."
            },
            "plsql_object_id":{
                "type":"integer",
                "description":"Object ID of the currently executing PL/SQL subprogram."
            },
            "plsql_subprogram_id":{
                "type":"integer",
                "description":"Subprogram ID of the currently executing PL/SQL object."
            },
            "qc_instance_id":{
                "type":"integer",
                "description":"Query coordinator instance ID. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0."
            },
            "qc_session_id":{
                "type":"integer",
                "description":"Query coordinator session ID. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0."
            },
            "qc_session_serial#":{
                "type":"integer",
                "description":"Query coordinator session serial number. This information is only available if the sampled session is a parallel query slave. For all other sessions, the value is 0."
            },
            "event":{
                "type":"string",
                "description":"If SESSION_STATE = WAITING, then the event for which the session was waiting for at the time of sampling. If SESSION_STATE = ON CPU, then this column is NULL."
            },
            "event_id":{
                "type":"integer",
                "description":"Identifier of the resource or event for which the session is waiting or for which the session last waited. Interpretation is similar to that of the EVENT column."
            },
            "event#":{
                "type":"integer",
                "description":"Number of the resource or event for which the session is waiting or for which the session last waited. Interpretation is similar to that of the EVENT column."
            },
            "seq#":{
                "type":"integer",
                "description":"Sequence number that uniquely identifies the wait (incremented for each wait)."
            },
            "p1text":{
                "type":"string",
                "description":"Description of the first wait event parameter."
            },
            "p1":{
                "type":"integer",
                "description":"First wait event parameter (in decimal)."
            },
            "p2text":{
                "type":"string",
                "description":"Description of the second wait event parameter."
            },
            "p2":{
                "type":"integer",
                "description":"Second wait event parameter (in decimal)."
            },
            "p3text":{
                "type":"string",
                "description":"Description of the third wait event parameter."
            },
            "p3":{
                "type":"integer",
                "description":"Third wait event parameter (in decimal)."
            },
            "wait_class":{
                "type":"string",
                "description":"Wait class name of the event for which the session was waiting at the time of sampling."
            },
            "wait_class_id":{
                "type":"integer",
                "description":"Wait class identifier of the event for which the session was waiting at the time of sampling."
            },
            "wait_time":{
                "type":"integer",
                "description":"Total wait time for the event for which the session last waited if the session was on the CPU when sampled; 0 if the session was waiting at the time of sampling."
            },
            "session_state":{
                "type":"string",
                "description":"Session state."
            },
            "time_waited":{
                "type":"integer",
                "description":"If SESSION_STATE = WAITING, then the time that the session actually spent waiting for that event (in microseconds). This column is set for waits that were in progress at the time the sample was taken. If a wait event lasted for more than a second and was caught waiting in more than one session sample row, then the actual time spent waiting for that wait event will be populated in the last of those session sample rows. At any given time, this information will not be available for the latest session sample."
            },
            "blocking_session_status":{
                "type":"string",
                "description":"Status of the blocking session."
            },
            "blocking_session":{
                "type":"integer",
                "description":"Session identifier of the blocking session. Populated only if the blocker is on the same instance and the session was waiting for enqueues or a 'buffer busy' wait."
            },
            "blocking_session_serial#":{
                "type":"integer",
                "description":"Serial number of the blocking session."
            },
            "blocking_inst_id":{
                "type":"integer",
                "description":"Instance number of the blocker shown in BLOCKING_SESSION."
            },
            "blocking_hangchain_info":{
                "type":"string",
                "description":"Indicates whether the information about BLOCKING_SESSION comes from the hang chain (Y) or not (N)."
            },
            "current_obj#":{
                "type":"integer",
                "description":"Object ID of the object that the session is referencing. This information is only available if the session was waiting for application, cluster, concurrency, and user I/O wait events."
            },
            "current_file#":{
                "type":"integer",
                "description":"File number of the file containing the block that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events."
            },
            "current_block#":{
                "type":"integer",
                "description":"ID of the block that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events."
            },
            "current_row#":{
                "type":"integer",
                "description":"Row identifier that the session is referencing. This information is only available if the session was waiting for cluster, concurrency, and user I/O wait events."
            },
            "top_level_call#":{
                "type":"integer",
                "description":"Oracle top level call number."
            },
            "top_level_call_name":{
                "type":"string",
                "description":"Oracle top level call name."
            },
            "consumer_group_id":{
                "type":"integer",
                "description":"Consumer group ID."
            },
            "xid":{
                "type":"string",
                "description":"Transaction ID that the session was working on at the time of sampling."
            },
            "remote_instance#":{
                "type":"integer",
                "description":"Remote instance identifier that will serve the block that this session is waiting for. This information is only available if the session was waiting for cluster events."
            },
            "time_model":{
                "type":"integer",
                "description":"Time model information."
            },
            "in_connection_mgmt":{
                "type":"string",
                "description":"Indicates whether the session was doing connection management at the time of sampling (Y) or not (N)."
            },
            "in_parse":{
                "type":"string",
                "description":"Indicates whether the session was parsing at the time of sampling (Y) or not (N)."
            },
            "in_hard_parse":{
                "type":"string",
                "description":"Indicates whether the session was hard parsing at the time of sampling (Y) or not (N)."
            },
            "in_sql_execution":{
                "type":"string",
                "description":"Indicates whether the session was executing SQL statements at the time of sampling (Y) or not (N)."
            },
            "in_plsql_execution":{
                "type":"string",
                "description":"Indicates whether the session was executing PL/SQL at the time of sampling (Y) or not (N)."
            },
            "in_plsql_rpc":{
                "type":"string",
                "description":"Indicates whether the session was executing inbound PL/SQL RPC calls at the time of sampling (Y) or not (N)."
            },
            "in_plsql_compilation":{
                "type":"string",
                "description":"Indicates whether the session was compiling PL/SQL at the time of sampling (Y) or not (N)."
            },
            "in_java_execution":{
                "type":"string",
                "description":"Indicates whether the session was executing Java at the time of sampling (Y) or not (N)."
            },
            "in_bind":{
                "type":"string",
                "description":"Indicates whether the session was doing bind operations at the time of sampling (Y) or not (N)."
            },
            "in_cursor_close":{
                "type":"string",
                "description":"Indicates whether the session was closing a cursor at the time of sampling (Y) or not (N)."
            },
            "in_sequence_load":{
                "type":"string",
                "description":"Indicates whether the session is loading in sequence (in sequence load code) (Y) or not (N)."
            },
            "in_inmemory_query":{
                "type":"string",
                "description":"Indicates whether the session was querying the In-Memory Column Store (IM column store) at the time of sampling (Y) or not (N)."
            },
            "in_inmemory_populate":{
                "type":"string",
                "description":"Indicates whether the session was populating the IM column store at the time of sampling (Y) or not (N)."
            },
            "in_inmemory_prepopulate":{
                "type":"string",
                "description":"Indicates whether the session was prepopulating the IM column store at the time of sampling (Y) or not (N)."
            },
            "in_inmemory_repopulate":{
                "type":"string",
                "description":"Indicates whether the session was repopulating the IM column store at the time of sampling (Y) or not (N)."
            },
            "in_inmemory_trepopulate":{
                "type":"string",
                "description":"Indicates whether the session was trickle repopulating the IM column store at the time of sampling (Y) or not (N)."
            },
            "in_tablespace_encryption":{
                "type":"string",
                "description":"Indicates whether encryption or decryption of a tablespace occurred at the time of sampling (Y) or not (N)."
            },
            "capture_overhead":{
                "type":"string",
                "description":"Indicates whether the session is executing capture code (Y) or not (N)."
            },
            "replay_overhead":{
                "type":"string",
                "description":"Indicates whether the session is executing replay code (Y) or not (N)."
            },
            "is_captured":{
                "type":"string",
                "description":"Indicates whether the session is being captured (Y) or not (N)."
            },
            "is_replayed":{
                "type":"string",
                "description":"Indicates whether the session is being replayed (Y) or not (N)."
            },
            "is_replay_sync_token_holder":{
                "type":"string",
                "description":"Indicates whether the session is holding a synchronization token (Y) or not (N) during workload replay."
            },
            "service_hash":{
                "type":"integer",
                "description":"Hash that identifies the Service."
            },
            "program":{
                "type":"string",
                "description":"Name of the operating system program."
            },
            "module":{
                "type":"string",
                "description":"Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_MODULE procedure."
            },
            "action":{
                "type":"string",
                "description":"Name of the executing module when sampled, as set by the DBMS_APPLICATION_INFO.SET_ACTION procedure."
            },
            "client_id":{
                "type":"string",
                "description":"Client identifier of the session."
            },
            "machine":{
                "type":"string",
                "description":"Client's operating system machine name."
            },
            "port":{
                "type":"integer",
                "description":"Client port number."
            },
            "ecid":{
                "type":"string",
                "description":"Execution context identifier (sent by Application Server)."
            },
            "dbreplay_file_id":{
                "type":"integer",
                "description":"If the session is being captured or replayed, then DBREPLAY_FILE_ID is the file ID for the workload capture or workload replay; otherwise it is NULL."
            },
            "dbreplay_call_counter":{
                "type":"integer",
                "description":"If the session is being captured or replayed, then DBREPLAY_CALL_COUNTER is the call counter of the user call that is being captured or replayed; otherwise it is NULL."
            },
            "tm_delta_time":{
                "type":"integer",
                "description":"Time interval (in microseconds) over which TM_DELTA_CPU_TIME and TM_DELTA_DB_TIME are accumulated."
            },
            "tm_delta_cpu_time":{
                "type":"integer",
                "description":"Amount of time this session spent on CPU over the last TM_DELTA_TIME microseconds."
            },
            "tm_delta_db_time":{
                "type":"integer",
                "description":"Amount of time spent by this session in database calls over the last TM_DELTA_TIME microseconds."
            },
            "delta_time":{
                "type":"integer",
                "description":"Time interval (in microseconds) since the last time this session was sampled or created, over which the next five statistics are accumulated."
            },
            "delta_read_io_requests":{
                "type":"integer",
                "description":"Number of read I/O requests made by this session over the last DELTA_TIME microseconds."
            },
            "delta_write_io_requests":{
                "type":"integer",
                "description":"Number of write I/O requests made by this session over the last DELTA_TIME microseconds."
            },
            "delta_read_io_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes read by this session over the last DELTA_TIME microseconds."
            },
            "delta_write_io_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes written by this session over the last DELTA_TIME microseconds."
            },
            "delta_interconnect_io_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes sent over the I/O interconnect over the last DELTA_TIME microseconds."
            },
            "delta_read_mem_bytes":{
                "type":"integer",
                "description":"Number of read bytes through the buffer cache."
            },
            "pga_allocated":{
                "type":"integer",
                "description":"Amount of PGA memory (in bytes) consumed by this session at the time this sample was taken."
            },
            "temp_space_allocated":{
                "type":"integer",
                "description":"Amount of TEMP memory (in bytes) consumed by this session at the time this sample was taken."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "dbop_name":{
                "type":"string",
                "description":"Database operation name. If the type is SQL, the DBOP_NAME will be NULL."
            },
            "dbop_exec_id":{
                "type":"integer",
                "description":"Database operation execution identifier for the current execution. If the type is SQL, the DBOP_EXEC_ID will be NULL."
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
