Return records from GV\$SQLAREA for a given session with current waits on GV\$SESSION_WAIT_HISTORY. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- seq_number: number
  Sequence number of wait event; 1 is the most recent.
- sid: number
  Session Identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Stastics on the SQL statements currently executing for specific session.

Body ()

Root Schema : PerformanceActionSessionHistoryWaitsActiveSQLItem

Type: `object`

Describes statistics on an SQL statement that is in memory, parsed and ready for execution but waiting on an event. The list of attributes may vary depending on database version.

Show Source

- action(optional): string
  Contains the name of the action that was executing when the SQL statement was first parsed as set by calling DBMS_APPLICATION_INFO.SET_ACTION.
- action_hash(optional): integer
  Hash value of the action that is named in the ACTION column.
- address(optional): string
  Address of the handle to the parent for this cursor.
- application_wait_time(optional): integer
  Application wait time (in microseconds).
- bind_data(optional): string
  Bind data.
- buffer_gets(optional): integer
  Sum of buffer gets over all child cursors.
- child_latch(optional): integer
  Child latch number that is protecting the cursor. This column is obsolete and maintained for backward compatibility.
- cluster_wait_time(optional): integer
  Cluster wait time (in microseconds).
- command_type(optional): integer
  Oracle command type definition.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- concurrency_wait_time(optional): integer
  Concurrency wait time (in microseconds).
- cpu_time(optional): integer
  CPU time (in microseconds) used by this cursor for parsing, executing, and fetching.
- direct_reads(optional): integer
  Sum of the number of direct reads over all child cursors.
- direct_writes(optional): integer
  Sum of the number of direct writes over all child cursors.
- disk_reads(optional): integer
  Sum of the number of disk reads over all child cursors.
- elapsed_time(optional): integer
  Elapsed time (in microseconds) used by this cursor for parsing, executing, and fetching. If the cursor uses parallel execution, then ELAPSED_TIME is the cumulative time for the query coordinator, plus all parallel query slave processes.
- end_of_fetch_count(optional): integer
  Number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column.
- exact_matching_signature(optional): integer
  Signature used when the CURSOR_SHARING parameter is set to EXACT.
- executions(optional): integer
  Total number of executions, totalled over all the child cursors.
- fetches(optional): integer
  Number of fetches associated with the SQL statement.
- first_load_time(optional): string
  Timestamp of the parent creation time.
- force_matching_signature(optional): integer
  Signature used when the CURSOR_SHARING parameter is set to FORCE.
- full_plan_hash_value(optional): integer
  Numeric representation of the complete SQL plan for this cursor. Comparing one FULL_PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line). Note that the FULL_PLAN_HASH_VALUE cannot be compared across databases releases. It is not backward compatible.
- hash_value(optional): integer
  Hash value of the parent statement in the library cache.
- inst_id(optional): integer
  Instance number from which the associated V\$ view information was obtained.
- invalidations(optional): integer
  Total number of invalidations over all the child cursors.
- io_cell_offload_eligible_bytes(optional): integer
  Number of I/O bytes which can be filtered by the Exadata storage system.
- io_cell_offload_returned_bytes(optional): integer
  Number of bytes that are returned by Exadata cell through the regular I/O path.
- io_cell_uncompressed_bytes(optional): integer
  Number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells.
- io_interconnect_bytes(optional): integer
  Number of I/O bytes exchanged between Oracle Database and the storage system.
- is_bind_aware(optional): string
  Indicates whether the cursor is bind aware (Y) or not (N). A query is considered bind-aware if it has been marked to use extended cursor sharing. The query would already have been marked as bind-sensitive.
- is_bind_sensitive(optional): string
  Indicates whether the cursor is bind sensitive (Y) or not (N). A query is considered bind-sensitive if the optimizer peeked at one of its bind variable values when computing predicate selectivities and where a change in a bind variable value may cause the optimizer to generate a different plan.
- is_obsolete(optional): string
  Indicates whether the cursor has become obsolete (Y) or not (N). This can happen if the number of child cursors is too large.
- is_reoptimizable(optional): string
  This columns shows whether the next execution matching this child cursor will trigger a reoptimization.
- is_resolved_adaptive_plan(optional): string
  This column shows whether all of the adaptive parts of a plan have been resolved to the final plan.
- java_exec_time(optional): integer
  Java execution time (in microseconds).
- kept_versions(optional): integer
  Number of child cursors that have been marked to be kept using the DBMS_SHARED_POOL package.
- last_active_child_address(optional): string
  Address (identifier) of the child cursor that was the last to be active in the group (that is, the child cursor on behalf of which statistics in GV\$SQL were updated).
- last_active_time(optional): string
  Time at which the query plan was last active.
- last_load_time(optional): string
  Time at which the query plan was loaded into the library cache.
- links(optional): array links
- literal_hash_value(optional): integer
  Hash value of the literals which are replaced with system-generated bind variables and are to be matched, when CURSOR_SHARING is used. This is not the hash value for the SQL statement. If CURSOR_SHARING is not used, then the value is 0.
- loaded_versions(optional): integer
  Number of child cursors that are present in the cache and have their context heap loaded.
- loads(optional): integer
  Number of times the object was loaded or reloaded.
- locked_total(optional): integer
  Total number of times the child cursor has been locked.
- module(optional): string
  Contains the name of the module that was executing when the SQL statement was first parsed as set by calling DBMS_APPLICATION_INFO.SET_MODULE
- module_hash(optional): integer
  Hash value of the module that is named in the MODULE column.
- object_status(optional): string
  Status of the cursor.
- old_hash_value(optional): integer
  Old SQL hash value.
- open_versions(optional): integer
  Number of child cursors that are currently open under this current parent.
- optimized_phy_read_requests(optional): integer
  Number of physical read I/O requests from Database Smart Flash Cache issued by the monitored SQL.
- optimizer_cost(optional): integer
  Cost of this query given by the optimizer.
- optimizer_env(optional): string
  Optimizer environment.
- optimizer_env_hash_value(optional): integer
  Hash value for the optimizer environment.
- optimizer_mode(optional): string
  Mode under which the SQL statement was executed.
- outline_category(optional): string
  If an outline was applied during construction of the cursor, then this column displays the category of that outline. Otherwise the column is left blank..
- outline_sid(optional): string
  Outline session identifier.
- parse_calls(optional): integer
  Sum of all parse calls to all the child cursors under this parent.
- parsing_schema_id(optional): integer
  Schema ID that was used to parse this child cursor.
- parsing_schema_name(optional): string
  Schema name that was used to parse this child cursor.
- parsing_user_id(optional): integer
  User ID of the user that has parsed the very first cursor under this parent.
- persistent_mem(optional): integer
  Fixed amount of memory used for the lifetime of an open cursor. If multiple child cursors exist, then the fixed sum of memory used for the lifetime of all the child cursors.
- physical_read_bytes(optional): integer
  Number of bytes read from disks by the monitored SQL.
- physical_read_requests(optional): integer
  Number of physical read I/O requests issued by the monitored SQL.
- physical_write_bytes(optional): integer
  Number of bytes written to disks by the monitored SQL.
- physical_write_requests(optional): integer
  Number of physical write I/O requests issued by the monitored SQL.
- pinned_total(optional): integer
  Total number of times the child cursor has been pinned.
- plan_hash_value(optional): integer
  Numeric representation of the current SQL plan for this cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line).
- plsql_exec_time(optional): integer
  PL/SQL execution time (in microseconds).
- program_id(optional): integer
  Program identifier.
- program_line#(optional): integer
  Program line number.
- px_servers_executions(optional): integer
  Total number of executions performed by parallel execution servers (0 when the statement has never been executed in parallel).
- remote(optional): string
  Indicates whether the cursor is remote mapped (Y) or not (N).
- rows_processed(optional): integer
  Total number of rows processed on behalf of this SQL statement.
- runtime_mem(optional): integer
  Fixed amount of memory required during execution of a cursor. If multiple child cursors exist, then the fixed sum of all memory required during execution of all the child cursors.
- serializable_aborts(optional): integer
  Number of times the transaction failed to serialize, producing ORA-08177 errors, totalled over all the child cursors.
- sharable_mem(optional): integer
  Amount of shared memory used by a cursor. If multiple child cursors exist, then the sum of all shared memory used by all child cursors.
- sorts(optional): integer
  Sum of the number of sorts that were done for all the child cursors.
- sql_fulltext(optional): string
  All characters of the SQL text for the current cursor.
- sql_id(optional): string
  SQL identifier of the parent cursor in the library cache.
- sql_patch(optional): string
  SQL patch used for this statement, if any.
- sql_plan_baseline(optional): string
  SQL plan baseline used for this statement, if any.
- sql_profile(optional): string
  SQL profile used for this statement, if any.
- sql_text(optional): string
  First thousand characters of the SQL text for the current cursor.
- typecheck_mem(optional): integer
  Typecheck memory.
- user_io_wait_time(optional): integer
  User I/O Wait Time (in microseconds).
- username(optional): string
  Name of the user that is associated with the session that is waiting.
- users_executing(optional): integer
  Total number of users executing the statement over all child cursors.
- users_opening(optional): integer
  Number of users that have any of the child cursors open.
- version_count(optional): integer
  Number of child cursors that are present in the cache under this parent.

<!-- -->

    {
        "type":"object",
        "description":"Describes statistics on an SQL statement that is in memory, parsed and ready for execution but waiting on an event. The list of attributes may vary depending on database version.",
        "properties":{
            "username":{
                "type":"string",
                "description":"Name of the user that is associated with the session that is waiting."
            },
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated V$ view information was obtained."
            },
            "sql_text":{
                "type":"string",
                "description":"First thousand characters of the SQL text for the current cursor."
            },
            "sql_fulltext":{
                "type":"string",
                "description":"All characters of the SQL text for the current cursor."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the parent cursor in the library cache."
            },
            "sharable_mem":{
                "type":"integer",
                "description":"Amount of shared memory used by a cursor. If multiple child cursors exist, then the sum of all shared memory used by all child cursors."
            },
            "persistent_mem":{
                "type":"integer",
                "description":"Fixed amount of memory used for the lifetime of an open cursor. If multiple child cursors exist, then the fixed sum of memory used for the lifetime of all the child cursors."
            },
            "runtime_mem":{
                "type":"integer",
                "description":"Fixed amount of memory required during execution of a cursor. If multiple child cursors exist, then the fixed sum of all memory required during execution of all the child cursors."
            },
            "sorts":{
                "type":"integer",
                "description":"Sum of the number of sorts that were done for all the child cursors."
            },
            "version_count":{
                "type":"integer",
                "description":"Number of child cursors that are present in the cache under this parent."
            },
            "loaded_versions":{
                "type":"integer",
                "description":"Number of child cursors that are present in the cache and have their context heap loaded."
            },
            "open_versions":{
                "type":"integer",
                "description":"Number of child cursors that are currently open under this current parent."
            },
            "users_opening":{
                "type":"integer",
                "description":"Number of users that have any of the child cursors open."
            },
            "fetches":{
                "type":"integer",
                "description":"Number of fetches associated with the SQL statement."
            },
            "executions":{
                "type":"integer",
                "description":"Total number of executions, totalled over all the child cursors."
            },
            "px_servers_executions":{
                "type":"integer",
                "description":"Total number of executions performed by parallel execution servers (0 when the statement has never been executed in parallel)."
            },
            "end_of_fetch_count":{
                "type":"integer",
                "description":"Number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column."
            },
            "users_executing":{
                "type":"integer",
                "description":"Total number of users executing the statement over all child cursors."
            },
            "loads":{
                "type":"integer",
                "description":"Number of times the object was loaded or reloaded."
            },
            "first_load_time":{
                "type":"string",
                "description":"Timestamp of the parent creation time."
            },
            "invalidations":{
                "type":"integer",
                "description":"Total number of invalidations over all the child cursors."
            },
            "parse_calls":{
                "type":"integer",
                "description":"Sum of all parse calls to all the child cursors under this parent."
            },
            "disk_reads":{
                "type":"integer",
                "description":"Sum of the number of disk reads over all child cursors."
            },
            "direct_writes":{
                "type":"integer",
                "description":"Sum of the number of direct writes over all child cursors."
            },
            "direct_reads":{
                "type":"integer",
                "description":"Sum of the number of direct reads over all child cursors."
            },
            "buffer_gets":{
                "type":"integer",
                "description":"Sum of buffer gets over all child cursors."
            },
            "application_wait_time":{
                "type":"integer",
                "description":"Application wait time (in microseconds)."
            },
            "concurrency_wait_time":{
                "type":"integer",
                "description":"Concurrency wait time (in microseconds)."
            },
            "cluster_wait_time":{
                "type":"integer",
                "description":"Cluster wait time (in microseconds)."
            },
            "user_io_wait_time":{
                "type":"integer",
                "description":"User I/O Wait Time (in microseconds)."
            },
            "plsql_exec_time":{
                "type":"integer",
                "description":"PL/SQL execution time (in microseconds)."
            },
            "java_exec_time":{
                "type":"integer",
                "description":"Java execution time (in microseconds)."
            },
            "rows_processed":{
                "type":"integer",
                "description":"Total number of rows processed on behalf of this SQL statement."
            },
            "command_type":{
                "type":"integer",
                "description":"Oracle command type definition."
            },
            "optimizer_mode":{
                "type":"string",
                "description":"Mode under which the SQL statement was executed."
            },
            "optimizer_cost":{
                "type":"integer",
                "description":"Cost of this query given by the optimizer."
            },
            "optimizer_env":{
                "type":"string",
                "description":"Optimizer environment."
            },
            "optimizer_env_hash_value":{
                "type":"integer",
                "description":"Hash value for the optimizer environment."
            },
            "parsing_user_id":{
                "type":"integer",
                "description":"User ID of the user that has parsed the very first cursor under this parent."
            },
            "parsing_schema_id":{
                "type":"integer",
                "description":"Schema ID that was used to parse this child cursor."
            },
            "parsing_schema_name":{
                "type":"string",
                "description":"Schema name that was used to parse this child cursor."
            },
            "kept_versions":{
                "type":"integer",
                "description":"Number of child cursors that have been marked to be kept using the DBMS_SHARED_POOL package."
            },
            "address":{
                "type":"string",
                "description":"Address of the handle to the parent for this cursor."
            },
            "hash_value":{
                "type":"integer",
                "description":"Hash value of the parent statement in the library cache."
            },
            "old_hash_value":{
                "type":"integer",
                "description":"Old SQL hash value."
            },
            "plan_hash_value":{
                "type":"integer",
                "description":"Numeric representation of the current SQL plan for this cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line)."
            },
            "full_plan_hash_value":{
                "type":"integer",
                "description":"Numeric representation of the complete SQL plan for this cursor. Comparing one FULL_PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line). Note that the FULL_PLAN_HASH_VALUE cannot be compared across databases releases. It is not backward compatible."
            },
            "module":{
                "type":"string",
                "description":"Contains the name of the module that was executing when the SQL statement was first parsed as set by calling DBMS_APPLICATION_INFO.SET_MODULE"
            },
            "module_hash":{
                "type":"integer",
                "description":"Hash value of the module that is named in the MODULE column."
            },
            "action":{
                "type":"string",
                "description":"Contains the name of the action that was executing when the SQL statement was first parsed as set by calling DBMS_APPLICATION_INFO.SET_ACTION."
            },
            "action_hash":{
                "type":"integer",
                "description":"Hash value of the action that is named in the ACTION column."
            },
            "serializable_aborts":{
                "type":"integer",
                "description":"Number of times the transaction failed to serialize, producing ORA-08177 errors, totalled over all the child cursors."
            },
            "outline_category":{
                "type":"string",
                "description":"If an outline was applied during construction of the cursor, then this column displays the category of that outline. Otherwise the column is left blank.."
            },
            "cpu_time":{
                "type":"integer",
                "description":"CPU time (in microseconds) used by this cursor for parsing, executing, and fetching."
            },
            "elapsed_time":{
                "type":"integer",
                "description":"Elapsed time (in microseconds) used by this cursor for parsing, executing, and fetching. If the cursor uses parallel execution, then ELAPSED_TIME is the cumulative time for the query coordinator, plus all parallel query slave processes."
            },
            "outline_sid":{
                "type":"string",
                "description":"Outline session identifier."
            },
            "last_active_child_address":{
                "type":"string",
                "description":"Address (identifier) of the child cursor that was the last to be active in the group (that is, the child cursor on behalf of which statistics in GV$SQL were updated)."
            },
            "remote":{
                "type":"string",
                "description":"Indicates whether the cursor is remote mapped (Y) or not (N)."
            },
            "object_status":{
                "type":"string",
                "description":"Status of the cursor."
            },
            "literal_hash_value":{
                "type":"integer",
                "description":"Hash value of the literals which are replaced with system-generated bind variables and are to be matched, when CURSOR_SHARING is used. This is not the hash value for the SQL statement. If CURSOR_SHARING is not used, then the value is 0."
            },
            "last_load_time":{
                "type":"string",
                "description":"Time at which the query plan was loaded into the library cache."
            },
            "is_obsolete":{
                "type":"string",
                "description":"Indicates whether the cursor has become obsolete (Y) or not (N). This can happen if the number of child cursors is too large."
            },
            "is_bind_sensitive":{
                "type":"string",
                "description":"Indicates whether the cursor is bind sensitive (Y) or not (N). A query is considered bind-sensitive if the optimizer peeked at one of its bind variable values when computing predicate selectivities and where a change in a bind variable value may cause the optimizer to generate a different plan."
            },
            "is_bind_aware":{
                "type":"string",
                "description":"Indicates whether the cursor is bind aware (Y) or not (N). A query is considered bind-aware if it has been marked to use extended cursor sharing. The query would already have been marked as bind-sensitive."
            },
            "child_latch":{
                "type":"integer",
                "description":"Child latch number that is protecting the cursor. This column is obsolete and maintained for backward compatibility."
            },
            "sql_profile":{
                "type":"string",
                "description":"SQL profile used for this statement, if any."
            },
            "sql_patch":{
                "type":"string",
                "description":"SQL patch used for this statement, if any."
            },
            "sql_plan_baseline":{
                "type":"string",
                "description":"SQL plan baseline used for this statement, if any."
            },
            "program_id":{
                "type":"integer",
                "description":"Program identifier."
            },
            "program_line#":{
                "type":"integer",
                "description":"Program line number."
            },
            "exact_matching_signature":{
                "type":"integer",
                "description":"Signature used when the CURSOR_SHARING parameter is set to EXACT."
            },
            "force_matching_signature":{
                "type":"integer",
                "description":"Signature used when the CURSOR_SHARING parameter is set to FORCE."
            },
            "last_active_time":{
                "type":"string",
                "description":"Time at which the query plan was last active."
            },
            "bind_data":{
                "type":"string",
                "description":"Bind data."
            },
            "typecheck_mem":{
                "type":"integer",
                "description":"Typecheck memory."
            },
            "io_cell_offload_eligible_bytes":{
                "type":"integer",
                "description":"Number of I/O bytes which can be filtered by the Exadata storage system."
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
            "optimized_phy_read_requests":{
                "type":"integer",
                "description":"Number of physical read I/O requests from Database Smart Flash Cache issued by the monitored SQL."
            },
            "locked_total":{
                "type":"integer",
                "description":"Total number of times the child cursor has been locked."
            },
            "pinned_total":{
                "type":"integer",
                "description":"Total number of times the child cursor has been pinned."
            },
            "io_cell_uncompressed_bytes":{
                "type":"integer",
                "description":"Number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
            },
            "io_cell_offload_returned_bytes":{
                "type":"integer",
                "description":"Number of bytes that are returned by Exadata cell through the regular I/O path."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "is_reoptimizable":{
                "type":"string",
                "description":"This columns shows whether the next execution matching this child cursor will trigger a reoptimization."
            },
            "is_resolved_adaptive_plan":{
                "type":"string",
                "description":"This column shows whether all of the adaptive parts of a plan have been resolved to the final plan."
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
