Returns records from GV\$SQL ordered by CPU time descending, SQL Text ascending. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Query Parameters

- limit(optional): integer(int32)
  The maximum number of records to return.
- q(optional): string
  Filtering is the process of limiting a collection resource by using a per-request dynamic filter definition across multiple page resources, where each page contains a subset of items found in the complete collection. Filtering enables efficient traversal of large collections.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of the SQL statements in the database ordered to show the top SQL statements first.

Body ()

Root Schema : PerformanceTopSQLStatements

Type: `object`

Show Source

- count(optional): integer
  Total number of records in the current response.
- hasMore(optional): boolean
  Indicates if there are more records to be retrieved.
- items(optional): array items
- limit(optional): integer
  The actual page size limit on number of records applied by the server.
- links(optional): array links
- offset(optional): integer
  The actual index from which the item resources are returned.

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/SQLStatement"
                }
            },
            "hasMore":{
                "type":"boolean",
                "description":"Indicates if there are more records to be retrieved."
            },
            "limit":{
                "type":"integer",
                "description":"The actual page size limit on number of records applied by the server."
            },
            "offset":{
                "type":"integer",
                "description":"The actual index from which the item resources are returned."
            },
            "count":{
                "type":"integer",
                "description":"Total number of records in the current response."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object SQLStatement
  Corresponding to a record on GV\$SQL, this object describes an SQL Statement. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/SQLStatement"
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

Nested Schema : SQLStatement

Type: `object`

Corresponding to a record on GV\$SQL, this object describes an SQL Statement. The list of attributes may vary depending on database version.

Show Source

- action(optional): string
  Contains the name of the action that was executing when the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION.
- action_hash(optional): integer
  Hash value of the action listed in the ACTION column.
- address(optional): string
  Address of the handle to the parent for this cursor.
- application_wait_time(optional): integer
  Application wait time (in microseconds).
- bind_data(optional): string
  Bind data.
- buffer_gets(optional): integer
  Number of buffer gets for this child cursor.
- child_address(optional): string
  Address of the child cursor.
- child_latch(optional): integer
  Child latch number that is protecting the cursor. This column is obsolete and maintained for backward compatibility.
- child_number(optional): integer
  Number of this child cursor.
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
- ddl_no_invalidate(optional): string
  Indicates if a DDL statement updated a dependent object and did not invalidate this cursor.
- direct_reads(optional): integer
  Number of direct reads for this child cursor.
- direct_writes(optional): integer
  Number of direct writes for this child cursor.
- disk_reads(optional): integer
  Number of disk reads for this child cursor.
- elapsed_time(optional): integer
  Elapsed time (in microseconds) used by this cursor for parsing, executing, and fetching. If the cursor uses parallel execution, then ELAPSED_TIME is the cumulative time for the query coordinator, plus all parallel query slave processes.
- end_of_fetch_count(optional): integer
  Number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column.
- exact_matching_signature(optional): integer
  Signature calculated on the normalized SQL text. The normalization includes the removal of white space and the uppercasing of all non-literal strings.
- executions(optional): integer
  Number of executions that took place on this object since it was brought into the library cache.
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
- im_scan_bytes_inmemory(optional): integer
  In-memory size of data scanned from the IM column store.
- im_scan_bytes_uncompressed(optional): integer
  Uncompressed size of data scanned from the IM column store.
- im_scans(optional): integer
  Number of In-Memory Column Store (IM column store) segment scans.
- inst_id(optional): integer
  Instance number from which the associated GV\$SQL view information was obtained.
- invalidations(optional): integer
  Number of times this child cursor has been invalidated.
- io_cell_offload_eligible_bytes(optional): integer
  Number of I/O bytes which can be filtered by the Exadata storage system.
- io_cell_offload_returned_bytes(optional): integer
  Number of filtered bytes returned by Exadata cells (that is, the number of bytes returned after processing has been offloaded on the Exadata cells).
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
  This column shows whether all of the adaptive parts of a plan have been resolved to the final plan. Once the plan is resolved, the plan hash value and the plan displayed by DBMS_XPLAN will not change through the end of execution.
- is_rolling_invalid(optional): string
  Indicates if this cursor is rolling validated.
- is_rolling_refresh_invalid(optional): string
  Indicates if this cursor is rolling validated and requires execution time refresh.
- is_shareable(optional): string
  Indicates whether the cursor can be shared (Y) or not (N).
- java_exec_time(optional): integer
  Java execution time (in microseconds).
- kept_versions(optional): integer
  Indicates whether this child cursor has been marked to be kept pinned in the cache using the DBMS_SHARED_POOL package.
- last_active_time(optional): string
  TIme at which the query plan was last active.
- last_load_time(optional): string
  Time at which the query plan was loaded into the library cache.
- links(optional): array links
- literal_hash_value(optional): integer
  Hash value of the literals which are replaced with system-generated bind variables and are to be matched, when CURSOR_SHARING is used. This is not the hash value for the SQL statement. If CURSOR_SHARING is not used, then the value is 0.
- loaded_versions(optional): integer
  Indicates whether the context heap is loaded (1) or not (0).
- loads(optional): integer
  Number of times the object was either loaded or reloaded.
- locked_total(optional): integer
  Total number of times the child cursor has been locked.
- module(optional): string
  Contains the name of the module that was executing when the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE.
- module_hash(optional): integer
  Hash value of the module listed in the MODULE column.
- object_status(optional): string
  Status of the cursor.
- old_hash_value(optional): integer
  Old SQL hash value.
- open_versions(optional): integer
  Indicates whether the child cursor is locked (1) or not (0).
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
  If an outline was applied during construction of the cursor, then this column displays the category of that outline. Otherwise the column is left blank.
- outline_sid(optional): integer
  Outline session identifier.
- parse_calls(optional): integer
  Number of parse calls for this child cursor.
- parsing_schema_id(optional): integer
  Schema ID that was used to originally build this child cursor.
- parsing_schema_name(optional): string
  Schema name that was used to originally build this child cursor.
- parsing_user_id(optional): integer
  User ID of the user who originally built this child cursor.
- persistent_mem(optional): integer
  Fixed amount of memory used for the lifetime of the child cursor (in bytes).
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
- result_cache(optional): string
  Indicates whether the function is result???cached (YES) or not (NO).
- rows_processed(optional): integer
  Total number of rows the parsed SQL statement returns.
- runtime_mem(optional): integer
  Fixed amount of memory required during the execution of the child cursor.
- serializable_aborts(optional): integer
  Number of times the transaction failed to serialize, producing ORA-08177 errors, per cursor.
- service(optional): string
  Service name.
- service_hash(optional): integer
  Hash value for the name listed in the SERVICE column.
- sharable_mem(optional): integer
  Amount of shared memory used by the child cursor (in bytes).
- sorts(optional): integer
  Number of sorts that were done for the child cursor.
- sql_fulltext(optional): string
  Full text for the SQL statement exposed as a CLOB column. The full text of a SQL statement can be retrieved using this column instead of joining with the V\$SQLTEXT dynamic performance view.
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
- sqltype(optional): integer
  Denotes the version of the SQL language used for this statement.
- type_chk_heap(optional): string
  Descriptor of the type check heap for this child cursor.
- typecheck_mem(optional): integer
  Typecheck memory.
- user_io_wait_time(optional): integer
  User I/O Wait Time (in microseconds).
- users_executing(optional): integer
  Number of users executing the statement.
- users_opening(optional): integer
  Number of users that have any of the child cursors open.

<!-- -->

    {
        "type":"object",
        "description":"Corresponding to a record on GV$SQL, this object describes an SQL Statement. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$SQL view information was obtained."
            },
            "sql_text":{
                "type":"string",
                "description":"First thousand characters of the SQL text for the current cursor."
            },
            "sql_fulltext":{
                "type":"string",
                "description":"Full text for the SQL statement exposed as a CLOB column. The full text of a SQL statement can be retrieved using this column instead of joining with the V$SQLTEXT dynamic performance view."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the parent cursor in the library cache."
            },
            "sharable_mem":{
                "type":"integer",
                "description":"Amount of shared memory used by the child cursor (in bytes)."
            },
            "persistent_mem":{
                "type":"integer",
                "description":"Fixed amount of memory used for the lifetime of the child cursor (in bytes)."
            },
            "runtime_mem":{
                "type":"integer",
                "description":"Fixed amount of memory required during the execution of the child cursor."
            },
            "sorts":{
                "type":"integer",
                "description":"Number of sorts that were done for the child cursor."
            },
            "loaded_versions":{
                "type":"integer",
                "description":"Indicates whether the context heap is loaded (1) or not (0)."
            },
            "open_versions":{
                "type":"integer",
                "description":"Indicates whether the child cursor is locked (1) or not (0)."
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
                "description":"Number of executions that took place on this object since it was brought into the library cache."
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
                "description":"Number of users executing the statement."
            },
            "loads":{
                "type":"integer",
                "description":"Number of times the object was either loaded or reloaded."
            },
            "first_load_time":{
                "type":"string",
                "description":"Timestamp of the parent creation time."
            },
            "invalidations":{
                "type":"integer",
                "description":"Number of times this child cursor has been invalidated."
            },
            "parse_calls":{
                "type":"integer",
                "description":"Number of parse calls for this child cursor."
            },
            "disk_reads":{
                "type":"integer",
                "description":"Number of disk reads for this child cursor."
            },
            "direct_writes":{
                "type":"integer",
                "description":"Number of direct writes for this child cursor."
            },
            "direct_reads":{
                "type":"integer",
                "description":"Number of direct reads for this child cursor."
            },
            "buffer_gets":{
                "type":"integer",
                "description":"Number of buffer gets for this child cursor."
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
                "description":"Total number of rows the parsed SQL statement returns."
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
                "description":"User ID of the user who originally built this child cursor."
            },
            "parsing_schema_id":{
                "type":"integer",
                "description":"Schema ID that was used to originally build this child cursor."
            },
            "parsing_schema_name":{
                "type":"string",
                "description":"Schema name that was used to originally build this child cursor."
            },
            "kept_versions":{
                "type":"integer",
                "description":"Indicates whether this child cursor has been marked to be kept pinned in the cache using the DBMS_SHARED_POOL package."
            },
            "address":{
                "type":"string",
                "description":"Address of the handle to the parent for this cursor."
            },
            "type_chk_heap":{
                "type":"string",
                "description":"Descriptor of the type check heap for this child cursor."
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
            "child_number":{
                "type":"integer",
                "description":"Number of this child cursor."
            },
            "service":{
                "type":"string",
                "description":"Service name."
            },
            "service_hash":{
                "type":"integer",
                "description":"Hash value for the name listed in the SERVICE column."
            },
            "module":{
                "type":"string",
                "description":"Contains the name of the module that was executing when the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE."
            },
            "module_hash":{
                "type":"integer",
                "description":"Hash value of the module listed in the MODULE column."
            },
            "action":{
                "type":"string",
                "description":"Contains the name of the action that was executing when the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION."
            },
            "action_hash":{
                "type":"integer",
                "description":"Hash value of the action listed in the ACTION column."
            },
            "serializable_aborts":{
                "type":"integer",
                "description":"Number of times the transaction failed to serialize, producing ORA-08177 errors, per cursor."
            },
            "outline_category":{
                "type":"string",
                "description":"If an outline was applied during construction of the cursor, then this column displays the category of that outline. Otherwise the column is left blank."
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
                "type":"integer",
                "description":"Outline session identifier."
            },
            "child_address":{
                "type":"string",
                "description":"Address of the child cursor."
            },
            "sqltype":{
                "type":"integer",
                "description":"Denotes the version of the SQL language used for this statement."
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
            "is_shareable":{
                "type":"string",
                "description":"Indicates whether the cursor can be shared (Y) or not (N)."
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
                "description":"Signature calculated on the normalized SQL text. The normalization includes the removal of white space and the uppercasing of all non-literal strings."
            },
            "force_matching_signature":{
                "type":"integer",
                "description":"Signature used when the CURSOR_SHARING parameter is set to FORCE."
            },
            "last_active_time":{
                "type":"string",
                "description":"TIme at which the query plan was last active."
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
                "description":"Number of filtered bytes returned by Exadata cells (that is, the number of bytes returned after  processing has been offloaded on the Exadata cells)."
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
                "description":"This column shows whether all of the adaptive parts of a plan have been resolved to the final plan. Once the plan is resolved, the plan hash value and the plan displayed by DBMS_XPLAN will not change through the end of execution."
            },
            "im_scans":{
                "type":"integer",
                "description":"Number of In-Memory Column Store (IM column store) segment scans."
            },
            "im_scan_bytes_uncompressed":{
                "type":"integer",
                "description":"Uncompressed size of data scanned from the IM column store."
            },
            "im_scan_bytes_inmemory":{
                "type":"integer",
                "description":"In-memory size of data scanned from the IM column store."
            },
            "ddl_no_invalidate":{
                "type":"string",
                "description":"Indicates if a DDL statement updated a dependent object and did not invalidate this cursor."
            },
            "is_rolling_invalid":{
                "type":"string",
                "description":"Indicates if this cursor is rolling validated."
            },
            "is_rolling_refresh_invalid":{
                "type":"string",
                "description":"Indicates if this cursor is rolling validated and requires execution time refresh."
            },
            "result_cache":{
                "type":"string",
                "description":"Indicates whether the function is result???cached (YES) or not (NO)."
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
