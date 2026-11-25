Oracle Diagnostics Pack licence is required for this service. Returns DBA_HIST_SQLSTAT and DBA_HIST_SNAPSHOT records for a specified SQL_ID. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- sql_id: string
  SQL identifier.

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

Historical statiscs for the specified SQL statement.

Body ()

Root Schema : PerformanceSQLStatementHistoryItem

Type: `object`

This object represents historical information about SQL statistics. The structure is based on DBA_HIST_SQLSTAT. The list of attributes may vary depending on database version.

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
        "description":"This object represents historical information about SQL statistics. The structure is based on DBA_HIST_SQLSTAT. The list of attributes may vary depending on database version.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "begin_interval_time_utc":{
                            "type":"string",
                            "description":"Time at the beginning of the snapshot interval in UTC timezone."
                        },
                        "startup_time":{
                            "type":"string",
                            "description":"Startup time of the instance."
                        },
                        "begin_interval_time":{
                            "type":"string",
                            "description":"Time at the beginning of the snapshot interval."
                        },
                        "end_interval_time":{
                            "type":"string",
                            "description":"Time at the end of the snapshot interval; the actual time the snapshot was taken."
                        },
                        "flush_elapsed":{
                            "type":"string",
                            "description":"Amount of time to perform the snapshot."
                        },
                        "error_count":{
                            "type":"integer",
                            "description":"Number of errors occurring in the tables for the particular snapshot."
                        },
                        "snap_flag":{
                            "type":"integer",
                            "description":"Condition under which the snapshot was inserted."
                        },
                        "snap_timezone":{
                            "type":"string",
                            "description":"Snapshot time zone expressed as offset from UTC (Coordinated Universal Time) time zone."
                        },
                        "sql_id":{
                            "type":"string",
                            "description":"SQL identifier of the parent cursor in the library cache."
                        },
                        "snap_id":{
                            "type":"integer",
                            "description":"Unique snapshot ID."
                        },
                        "dbid":{
                            "type":"integer",
                            "description":"Database ID for the snapshot."
                        },
                        "instance_number":{
                            "type":"integer",
                            "description":"Instance number for the snapshot."
                        },
                        "plan_hash_value":{
                            "type":"integer",
                            "description":"Numerical representation of the SQL plan for the cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line)."
                        },
                        "optimizer_cost":{
                            "type":"integer",
                            "description":"Cost of the query given by the optimizer."
                        },
                        "optimizer_mode":{
                            "type":"string",
                            "description":"Mode under which the SQL statement is executed."
                        },
                        "optimizer_env_hash_value":{
                            "type":"integer",
                            "description":"Hash Value for the optimizer environment."
                        },
                        "sharable_mem":{
                            "type":"integer",
                            "description":"Amount of shared memory used by the child cursor (in bytes)."
                        },
                        "loaded_versions":{
                            "type":"integer",
                            "description":"Indicates whether the context heap is loaded (1) or not (0)."
                        },
                        "version_count":{
                            "type":"integer",
                            "description":"Number of children associated with the cursor."
                        },
                        "module":{
                            "type":"string",
                            "description":"Contains the name of the module that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE."
                        },
                        "action":{
                            "type":"string",
                            "description":"Contains the name of the action that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION."
                        },
                        "sql_profile":{
                            "type":"string",
                            "description":"Name of the applied SQL Profile."
                        },
                        "force_matching_signature":{
                            "type":"integer",
                            "description":"The signature used when the CURSOR_SHARING parameter is set to FORCE."
                        },
                        "parsing_schema_id":{
                            "type":"integer",
                            "description":"Schema ID that was used to originally build the child cursor."
                        },
                        "parsing_schema_name":{
                            "type":"string",
                            "description":"Schema name that was used to originally build the child cursor."
                        },
                        "parsing_user_id":{
                            "type":"integer",
                            "description":"User ID that was used to originally build the child cursor."
                        },
                        "fetches_total":{
                            "type":"integer",
                            "description":"Cumulative number of fetches associated with the SQL statement."
                        },
                        "fetches_delta":{
                            "type":"integer",
                            "description":"Delta number of fetches associated with the SQL statement."
                        },
                        "end_of_fetch_count_total":{
                            "type":"integer",
                            "description":"Cumulative number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column."
                        },
                        "end_of_fetch_count_delta":{
                            "type":"integer",
                            "description":"Delta number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed."
                        },
                        "sorts_total":{
                            "type":"integer",
                            "description":"Cumulative number of sorts that were done for this child cursor."
                        },
                        "sorts_delta":{
                            "type":"integer",
                            "description":"Delta number of sorts that were done for this child cursor."
                        },
                        "executions_total":{
                            "type":"integer",
                            "description":"Cumulative number of executions that took place on this object since it was brought into the library cache."
                        },
                        "executions_delta":{
                            "type":"integer",
                            "description":"Delta number of executions that took place on this object since it was brought into the library cache."
                        },
                        "px_servers_execs_total":{
                            "type":"integer",
                            "description":"Cumulative number of PX server executions."
                        },
                        "px_servers_execs_delta":{
                            "type":"integer",
                            "description":"Delta number of PX server executions."
                        },
                        "loads_total":{
                            "type":"integer",
                            "description":"Cumulative number of times the object was either loaded or reloaded."
                        },
                        "loads_delta":{
                            "type":"integer",
                            "description":"Delta number of times the object was either loaded or reloaded."
                        },
                        "invalidations_total":{
                            "type":"integer",
                            "description":"Cumulative number of times this child cursor has been invalidated."
                        },
                        "invalidations_delta":{
                            "type":"integer",
                            "description":"Delta number of times this child cursor has been invalidated."
                        },
                        "parse_calls_total":{
                            "type":"integer",
                            "description":"Cumulative number of parse calls for this child cursor."
                        },
                        "parse_calls_delta":{
                            "type":"integer",
                            "description":"Delta number of parse calls for this child cursor."
                        },
                        "disk_reads_total":{
                            "type":"integer",
                            "description":"Cumulative number of disk reads for this child cursor."
                        },
                        "disk_reads_delta":{
                            "type":"integer",
                            "description":"Delta number of disk reads for this child cursor."
                        },
                        "buffer_gets_total":{
                            "type":"integer",
                            "description":"Cumulative number of buffer gets for this child cursor."
                        },
                        "buffer_gets_delta":{
                            "type":"integer",
                            "description":"Delta number of buffer gets for this child cursor."
                        },
                        "rows_processed_total":{
                            "type":"integer",
                            "description":"Cumulative number of rows the parsed SQL statement returns."
                        },
                        "rows_processed_delta":{
                            "type":"integer",
                            "description":"Delta number of rows the parsed SQL statement returns."
                        },
                        "cpu_time_total":{
                            "type":"integer",
                            "description":"Cumulative value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
                        },
                        "cpu_time_delta":{
                            "type":"integer",
                            "description":"Delta value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
                        },
                        "elapsed_time_total":{
                            "type":"integer",
                            "description":"Cumulative value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching. If the cursor uses parallel execution, then ELAPSED_TIME_TOTAL is the cumulative time for the query coordinator, plus all parallel query slave processes."
                        },
                        "elapsed_time_delta":{
                            "type":"integer",
                            "description":"Delta value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching."
                        },
                        "iowait_total":{
                            "type":"integer",
                            "description":"Cumulative value of user I/O wait time (in microseconds)."
                        },
                        "iowait_delta":{
                            "type":"integer",
                            "description":"Delta value of user I/O wait time (in microseconds)."
                        },
                        "clwait_total":{
                            "type":"integer",
                            "description":"Cumulative value of cluster wait time (in microseconds)."
                        },
                        "clwait_delta":{
                            "type":"integer",
                            "description":"Delta value of cluster wait time (in microseconds)."
                        },
                        "apwait_total":{
                            "type":"integer",
                            "description":"Cumulative value of application wait time (in microseconds)."
                        },
                        "apwait_delta":{
                            "type":"integer",
                            "description":"Delta value of application wait time (in microseconds)."
                        },
                        "ccwait_total":{
                            "type":"integer",
                            "description":"Cumulative value of concurrency wait time (in microseconds)."
                        },
                        "ccwait_delta":{
                            "type":"integer",
                            "description":"Delta value of concurrency wait time (in microseconds)."
                        },
                        "direct_writes_total":{
                            "type":"integer",
                            "description":"Cumulative value of direct writes."
                        },
                        "direct_writes_delta":{
                            "type":"integer",
                            "description":"Delta value of direct writes."
                        },
                        "plsexec_time_total":{
                            "type":"integer",
                            "description":"Cumulative value of PL/SQL Execution Time (in microseconds)."
                        },
                        "plsexec_time_delta":{
                            "type":"integer",
                            "description":"Delta value of PL/SQL Execution Time (in microseconds)."
                        },
                        "javexec_time_total":{
                            "type":"integer",
                            "description":"Cumulative value of Java Execution Time (in microseconds)."
                        },
                        "javexec_time_delta":{
                            "type":"integer",
                            "description":"Delta value of Java Execution Time (in microseconds)."
                        },
                        "io_offload_elig_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of I/O bytes which can be filtered by the Exadata storage system."
                        },
                        "io_offload_elig_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of I/O bytes which can be filtered by the Exadata storage system."
                        },
                        "io_interconnect_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of I/O bytes exchanged between Oracle Database and the storage system."
                        },
                        "io_interconnect_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of I/O bytes exchanged between Oracle Database and the storage system."
                        },
                        "physical_read_requests_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of physical read I/O requests issued by the monitored SQL."
                        },
                        "physical_read_requests_delta":{
                            "type":"integer",
                            "description":"Delta value of number of physical read I/O requests issued by the monitored SQL."
                        },
                        "physical_read_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of bytes read from disks by the monitored SQL."
                        },
                        "physical_read_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of bytes read from disks by the monitored SQL."
                        },
                        "physical_write_requests_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of physical write I/O requests issued by the monitored SQL."
                        },
                        "physical_write_requests_delta":{
                            "type":"integer",
                            "description":"Delta value of number of physical write I/O requests issued by the monitored SQL."
                        },
                        "physical_write_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of bytes written to disks by the monitored SQL."
                        },
                        "physical_write_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of bytes written to disks by the monitored SQL."
                        },
                        "optimized_physical_reads_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
                        },
                        "optimized_physical_reads_delta":{
                            "type":"integer",
                            "description":"Delta value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
                        },
                        "cell_uncompressed_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
                        },
                        "cell_uncompressed_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
                        },
                        "io_offload_return_bytes_total":{
                            "type":"integer",
                            "description":"Cumulative value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
                        },
                        "io_offload_return_bytes_delta":{
                            "type":"integer",
                            "description":"Delta value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
                        },
                        "bind_data":{
                            "type":"string",
                            "description":"Bind data."
                        },
                        "con_dbid":{
                            "type":"integer",
                            "description":"The database ID of the PDB for the sampled session."
                        },
                        "con_id":{
                            "type":"integer",
                            "description":"The ID of the container that CON_DBID identifies."
                        },
                        "elapsed_time_delta_s_per_exec":{
                            "type":"number",
                            "description":"Average elapsed time (in seconds) for parsing/executing/fetching across all recorded executions."
                        },
                        "sum_executions_delta":{
                            "type":"integer",
                            "description":"Total of all executions that took place on this object since it was brought into the library cache."
                        }
                    }
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

- Array of: object items

<!-- -->

    {
        "type":"array",
        "items":{
            "type":"object",
            "properties":{
                "begin_interval_time_utc":{
                    "type":"string",
                    "description":"Time at the beginning of the snapshot interval in UTC timezone."
                },
                "startup_time":{
                    "type":"string",
                    "description":"Startup time of the instance."
                },
                "begin_interval_time":{
                    "type":"string",
                    "description":"Time at the beginning of the snapshot interval."
                },
                "end_interval_time":{
                    "type":"string",
                    "description":"Time at the end of the snapshot interval; the actual time the snapshot was taken."
                },
                "flush_elapsed":{
                    "type":"string",
                    "description":"Amount of time to perform the snapshot."
                },
                "error_count":{
                    "type":"integer",
                    "description":"Number of errors occurring in the tables for the particular snapshot."
                },
                "snap_flag":{
                    "type":"integer",
                    "description":"Condition under which the snapshot was inserted."
                },
                "snap_timezone":{
                    "type":"string",
                    "description":"Snapshot time zone expressed as offset from UTC (Coordinated Universal Time) time zone."
                },
                "sql_id":{
                    "type":"string",
                    "description":"SQL identifier of the parent cursor in the library cache."
                },
                "snap_id":{
                    "type":"integer",
                    "description":"Unique snapshot ID."
                },
                "dbid":{
                    "type":"integer",
                    "description":"Database ID for the snapshot."
                },
                "instance_number":{
                    "type":"integer",
                    "description":"Instance number for the snapshot."
                },
                "plan_hash_value":{
                    "type":"integer",
                    "description":"Numerical representation of the SQL plan for the cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line)."
                },
                "optimizer_cost":{
                    "type":"integer",
                    "description":"Cost of the query given by the optimizer."
                },
                "optimizer_mode":{
                    "type":"string",
                    "description":"Mode under which the SQL statement is executed."
                },
                "optimizer_env_hash_value":{
                    "type":"integer",
                    "description":"Hash Value for the optimizer environment."
                },
                "sharable_mem":{
                    "type":"integer",
                    "description":"Amount of shared memory used by the child cursor (in bytes)."
                },
                "loaded_versions":{
                    "type":"integer",
                    "description":"Indicates whether the context heap is loaded (1) or not (0)."
                },
                "version_count":{
                    "type":"integer",
                    "description":"Number of children associated with the cursor."
                },
                "module":{
                    "type":"string",
                    "description":"Contains the name of the module that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE."
                },
                "action":{
                    "type":"string",
                    "description":"Contains the name of the action that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION."
                },
                "sql_profile":{
                    "type":"string",
                    "description":"Name of the applied SQL Profile."
                },
                "force_matching_signature":{
                    "type":"integer",
                    "description":"The signature used when the CURSOR_SHARING parameter is set to FORCE."
                },
                "parsing_schema_id":{
                    "type":"integer",
                    "description":"Schema ID that was used to originally build the child cursor."
                },
                "parsing_schema_name":{
                    "type":"string",
                    "description":"Schema name that was used to originally build the child cursor."
                },
                "parsing_user_id":{
                    "type":"integer",
                    "description":"User ID that was used to originally build the child cursor."
                },
                "fetches_total":{
                    "type":"integer",
                    "description":"Cumulative number of fetches associated with the SQL statement."
                },
                "fetches_delta":{
                    "type":"integer",
                    "description":"Delta number of fetches associated with the SQL statement."
                },
                "end_of_fetch_count_total":{
                    "type":"integer",
                    "description":"Cumulative number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column."
                },
                "end_of_fetch_count_delta":{
                    "type":"integer",
                    "description":"Delta number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed."
                },
                "sorts_total":{
                    "type":"integer",
                    "description":"Cumulative number of sorts that were done for this child cursor."
                },
                "sorts_delta":{
                    "type":"integer",
                    "description":"Delta number of sorts that were done for this child cursor."
                },
                "executions_total":{
                    "type":"integer",
                    "description":"Cumulative number of executions that took place on this object since it was brought into the library cache."
                },
                "executions_delta":{
                    "type":"integer",
                    "description":"Delta number of executions that took place on this object since it was brought into the library cache."
                },
                "px_servers_execs_total":{
                    "type":"integer",
                    "description":"Cumulative number of PX server executions."
                },
                "px_servers_execs_delta":{
                    "type":"integer",
                    "description":"Delta number of PX server executions."
                },
                "loads_total":{
                    "type":"integer",
                    "description":"Cumulative number of times the object was either loaded or reloaded."
                },
                "loads_delta":{
                    "type":"integer",
                    "description":"Delta number of times the object was either loaded or reloaded."
                },
                "invalidations_total":{
                    "type":"integer",
                    "description":"Cumulative number of times this child cursor has been invalidated."
                },
                "invalidations_delta":{
                    "type":"integer",
                    "description":"Delta number of times this child cursor has been invalidated."
                },
                "parse_calls_total":{
                    "type":"integer",
                    "description":"Cumulative number of parse calls for this child cursor."
                },
                "parse_calls_delta":{
                    "type":"integer",
                    "description":"Delta number of parse calls for this child cursor."
                },
                "disk_reads_total":{
                    "type":"integer",
                    "description":"Cumulative number of disk reads for this child cursor."
                },
                "disk_reads_delta":{
                    "type":"integer",
                    "description":"Delta number of disk reads for this child cursor."
                },
                "buffer_gets_total":{
                    "type":"integer",
                    "description":"Cumulative number of buffer gets for this child cursor."
                },
                "buffer_gets_delta":{
                    "type":"integer",
                    "description":"Delta number of buffer gets for this child cursor."
                },
                "rows_processed_total":{
                    "type":"integer",
                    "description":"Cumulative number of rows the parsed SQL statement returns."
                },
                "rows_processed_delta":{
                    "type":"integer",
                    "description":"Delta number of rows the parsed SQL statement returns."
                },
                "cpu_time_total":{
                    "type":"integer",
                    "description":"Cumulative value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
                },
                "cpu_time_delta":{
                    "type":"integer",
                    "description":"Delta value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
                },
                "elapsed_time_total":{
                    "type":"integer",
                    "description":"Cumulative value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching. If the cursor uses parallel execution, then ELAPSED_TIME_TOTAL is the cumulative time for the query coordinator, plus all parallel query slave processes."
                },
                "elapsed_time_delta":{
                    "type":"integer",
                    "description":"Delta value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching."
                },
                "iowait_total":{
                    "type":"integer",
                    "description":"Cumulative value of user I/O wait time (in microseconds)."
                },
                "iowait_delta":{
                    "type":"integer",
                    "description":"Delta value of user I/O wait time (in microseconds)."
                },
                "clwait_total":{
                    "type":"integer",
                    "description":"Cumulative value of cluster wait time (in microseconds)."
                },
                "clwait_delta":{
                    "type":"integer",
                    "description":"Delta value of cluster wait time (in microseconds)."
                },
                "apwait_total":{
                    "type":"integer",
                    "description":"Cumulative value of application wait time (in microseconds)."
                },
                "apwait_delta":{
                    "type":"integer",
                    "description":"Delta value of application wait time (in microseconds)."
                },
                "ccwait_total":{
                    "type":"integer",
                    "description":"Cumulative value of concurrency wait time (in microseconds)."
                },
                "ccwait_delta":{
                    "type":"integer",
                    "description":"Delta value of concurrency wait time (in microseconds)."
                },
                "direct_writes_total":{
                    "type":"integer",
                    "description":"Cumulative value of direct writes."
                },
                "direct_writes_delta":{
                    "type":"integer",
                    "description":"Delta value of direct writes."
                },
                "plsexec_time_total":{
                    "type":"integer",
                    "description":"Cumulative value of PL/SQL Execution Time (in microseconds)."
                },
                "plsexec_time_delta":{
                    "type":"integer",
                    "description":"Delta value of PL/SQL Execution Time (in microseconds)."
                },
                "javexec_time_total":{
                    "type":"integer",
                    "description":"Cumulative value of Java Execution Time (in microseconds)."
                },
                "javexec_time_delta":{
                    "type":"integer",
                    "description":"Delta value of Java Execution Time (in microseconds)."
                },
                "io_offload_elig_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of I/O bytes which can be filtered by the Exadata storage system."
                },
                "io_offload_elig_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of I/O bytes which can be filtered by the Exadata storage system."
                },
                "io_interconnect_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of I/O bytes exchanged between Oracle Database and the storage system."
                },
                "io_interconnect_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of I/O bytes exchanged between Oracle Database and the storage system."
                },
                "physical_read_requests_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of physical read I/O requests issued by the monitored SQL."
                },
                "physical_read_requests_delta":{
                    "type":"integer",
                    "description":"Delta value of number of physical read I/O requests issued by the monitored SQL."
                },
                "physical_read_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of bytes read from disks by the monitored SQL."
                },
                "physical_read_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of bytes read from disks by the monitored SQL."
                },
                "physical_write_requests_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of physical write I/O requests issued by the monitored SQL."
                },
                "physical_write_requests_delta":{
                    "type":"integer",
                    "description":"Delta value of number of physical write I/O requests issued by the monitored SQL."
                },
                "physical_write_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of bytes written to disks by the monitored SQL."
                },
                "physical_write_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of bytes written to disks by the monitored SQL."
                },
                "optimized_physical_reads_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
                },
                "optimized_physical_reads_delta":{
                    "type":"integer",
                    "description":"Delta value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
                },
                "cell_uncompressed_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
                },
                "cell_uncompressed_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
                },
                "io_offload_return_bytes_total":{
                    "type":"integer",
                    "description":"Cumulative value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
                },
                "io_offload_return_bytes_delta":{
                    "type":"integer",
                    "description":"Delta value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
                },
                "bind_data":{
                    "type":"string",
                    "description":"Bind data."
                },
                "con_dbid":{
                    "type":"integer",
                    "description":"The database ID of the PDB for the sampled session."
                },
                "con_id":{
                    "type":"integer",
                    "description":"The ID of the container that CON_DBID identifies."
                },
                "elapsed_time_delta_s_per_exec":{
                    "type":"number",
                    "description":"Average elapsed time (in seconds) for parsing/executing/fetching across all recorded executions."
                },
                "sum_executions_delta":{
                    "type":"integer",
                    "description":"Total of all executions that took place on this object since it was brought into the library cache."
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

Nested Schema : items

Type: `object`

Show Source

- action(optional): string
  Contains the name of the action that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION.
- apwait_delta(optional): integer
  Delta value of application wait time (in microseconds).
- apwait_total(optional): integer
  Cumulative value of application wait time (in microseconds).
- begin_interval_time(optional): string
  Time at the beginning of the snapshot interval.
- begin_interval_time_utc(optional): string
  Time at the beginning of the snapshot interval in UTC timezone.
- bind_data(optional): string
  Bind data.
- buffer_gets_delta(optional): integer
  Delta number of buffer gets for this child cursor.
- buffer_gets_total(optional): integer
  Cumulative number of buffer gets for this child cursor.
- ccwait_delta(optional): integer
  Delta value of concurrency wait time (in microseconds).
- ccwait_total(optional): integer
  Cumulative value of concurrency wait time (in microseconds).
- cell_uncompressed_bytes_delta(optional): integer
  Delta value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells.
- cell_uncompressed_bytes_total(optional): integer
  Cumulative value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells.
- clwait_delta(optional): integer
  Delta value of cluster wait time (in microseconds).
- clwait_total(optional): integer
  Cumulative value of cluster wait time (in microseconds).
- con_dbid(optional): integer
  The database ID of the PDB for the sampled session.
- con_id(optional): integer
  The ID of the container that CON_DBID identifies.
- cpu_time_delta(optional): integer
  Delta value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching.
- cpu_time_total(optional): integer
  Cumulative value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching.
- dbid(optional): integer
  Database ID for the snapshot.
- direct_writes_delta(optional): integer
  Delta value of direct writes.
- direct_writes_total(optional): integer
  Cumulative value of direct writes.
- disk_reads_delta(optional): integer
  Delta number of disk reads for this child cursor.
- disk_reads_total(optional): integer
  Cumulative number of disk reads for this child cursor.
- elapsed_time_delta(optional): integer
  Delta value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching.
- elapsed_time_delta_s_per_exec(optional): number
  Average elapsed time (in seconds) for parsing/executing/fetching across all recorded executions.
- elapsed_time_total(optional): integer
  Cumulative value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching. If the cursor uses parallel execution, then ELAPSED_TIME_TOTAL is the cumulative time for the query coordinator, plus all parallel query slave processes.
- end_interval_time(optional): string
  Time at the end of the snapshot interval; the actual time the snapshot was taken.
- end_of_fetch_count_delta(optional): integer
  Delta number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed.
- end_of_fetch_count_total(optional): integer
  Cumulative number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column.
- error_count(optional): integer
  Number of errors occurring in the tables for the particular snapshot.
- executions_delta(optional): integer
  Delta number of executions that took place on this object since it was brought into the library cache.
- executions_total(optional): integer
  Cumulative number of executions that took place on this object since it was brought into the library cache.
- fetches_delta(optional): integer
  Delta number of fetches associated with the SQL statement.
- fetches_total(optional): integer
  Cumulative number of fetches associated with the SQL statement.
- flush_elapsed(optional): string
  Amount of time to perform the snapshot.
- force_matching_signature(optional): integer
  The signature used when the CURSOR_SHARING parameter is set to FORCE.
- instance_number(optional): integer
  Instance number for the snapshot.
- invalidations_delta(optional): integer
  Delta number of times this child cursor has been invalidated.
- invalidations_total(optional): integer
  Cumulative number of times this child cursor has been invalidated.
- io_interconnect_bytes_delta(optional): integer
  Delta value of number of I/O bytes exchanged between Oracle Database and the storage system.
- io_interconnect_bytes_total(optional): integer
  Cumulative value of number of I/O bytes exchanged between Oracle Database and the storage system.
- io_offload_elig_bytes_delta(optional): integer
  Delta value of number of I/O bytes which can be filtered by the Exadata storage system.
- io_offload_elig_bytes_total(optional): integer
  Cumulative value of number of I/O bytes which can be filtered by the Exadata storage system.
- io_offload_return_bytes_delta(optional): integer
  Delta value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O).
- io_offload_return_bytes_total(optional): integer
  Cumulative value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O).
- iowait_delta(optional): integer
  Delta value of user I/O wait time (in microseconds).
- iowait_total(optional): integer
  Cumulative value of user I/O wait time (in microseconds).
- javexec_time_delta(optional): integer
  Delta value of Java Execution Time (in microseconds).
- javexec_time_total(optional): integer
  Cumulative value of Java Execution Time (in microseconds).
- loaded_versions(optional): integer
  Indicates whether the context heap is loaded (1) or not (0).
- loads_delta(optional): integer
  Delta number of times the object was either loaded or reloaded.
- loads_total(optional): integer
  Cumulative number of times the object was either loaded or reloaded.
- module(optional): string
  Contains the name of the module that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE.
- optimized_physical_reads_delta(optional): integer
  Delta value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL.
- optimized_physical_reads_total(optional): integer
  Cumulative value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL.
- optimizer_cost(optional): integer
  Cost of the query given by the optimizer.
- optimizer_env_hash_value(optional): integer
  Hash Value for the optimizer environment.
- optimizer_mode(optional): string
  Mode under which the SQL statement is executed.
- parse_calls_delta(optional): integer
  Delta number of parse calls for this child cursor.
- parse_calls_total(optional): integer
  Cumulative number of parse calls for this child cursor.
- parsing_schema_id(optional): integer
  Schema ID that was used to originally build the child cursor.
- parsing_schema_name(optional): string
  Schema name that was used to originally build the child cursor.
- parsing_user_id(optional): integer
  User ID that was used to originally build the child cursor.
- physical_read_bytes_delta(optional): integer
  Delta value of number of bytes read from disks by the monitored SQL.
- physical_read_bytes_total(optional): integer
  Cumulative value of number of bytes read from disks by the monitored SQL.
- physical_read_requests_delta(optional): integer
  Delta value of number of physical read I/O requests issued by the monitored SQL.
- physical_read_requests_total(optional): integer
  Cumulative value of number of physical read I/O requests issued by the monitored SQL.
- physical_write_bytes_delta(optional): integer
  Delta value of number of bytes written to disks by the monitored SQL.
- physical_write_bytes_total(optional): integer
  Cumulative value of number of bytes written to disks by the monitored SQL.
- physical_write_requests_delta(optional): integer
  Delta value of number of physical write I/O requests issued by the monitored SQL.
- physical_write_requests_total(optional): integer
  Cumulative value of number of physical write I/O requests issued by the monitored SQL.
- plan_hash_value(optional): integer
  Numerical representation of the SQL plan for the cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line).
- plsexec_time_delta(optional): integer
  Delta value of PL/SQL Execution Time (in microseconds).
- plsexec_time_total(optional): integer
  Cumulative value of PL/SQL Execution Time (in microseconds).
- px_servers_execs_delta(optional): integer
  Delta number of PX server executions.
- px_servers_execs_total(optional): integer
  Cumulative number of PX server executions.
- rows_processed_delta(optional): integer
  Delta number of rows the parsed SQL statement returns.
- rows_processed_total(optional): integer
  Cumulative number of rows the parsed SQL statement returns.
- sharable_mem(optional): integer
  Amount of shared memory used by the child cursor (in bytes).
- snap_flag(optional): integer
  Condition under which the snapshot was inserted.
- snap_id(optional): integer
  Unique snapshot ID.
- snap_timezone(optional): string
  Snapshot time zone expressed as offset from UTC (Coordinated Universal Time) time zone.
- sorts_delta(optional): integer
  Delta number of sorts that were done for this child cursor.
- sorts_total(optional): integer
  Cumulative number of sorts that were done for this child cursor.
- sql_id(optional): string
  SQL identifier of the parent cursor in the library cache.
- sql_profile(optional): string
  Name of the applied SQL Profile.
- startup_time(optional): string
  Startup time of the instance.
- sum_executions_delta(optional): integer
  Total of all executions that took place on this object since it was brought into the library cache.
- version_count(optional): integer
  Number of children associated with the cursor.

<!-- -->

    {
        "type":"object",
        "properties":{
            "begin_interval_time_utc":{
                "type":"string",
                "description":"Time at the beginning of the snapshot interval in UTC timezone."
            },
            "startup_time":{
                "type":"string",
                "description":"Startup time of the instance."
            },
            "begin_interval_time":{
                "type":"string",
                "description":"Time at the beginning of the snapshot interval."
            },
            "end_interval_time":{
                "type":"string",
                "description":"Time at the end of the snapshot interval; the actual time the snapshot was taken."
            },
            "flush_elapsed":{
                "type":"string",
                "description":"Amount of time to perform the snapshot."
            },
            "error_count":{
                "type":"integer",
                "description":"Number of errors occurring in the tables for the particular snapshot."
            },
            "snap_flag":{
                "type":"integer",
                "description":"Condition under which the snapshot was inserted."
            },
            "snap_timezone":{
                "type":"string",
                "description":"Snapshot time zone expressed as offset from UTC (Coordinated Universal Time) time zone."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the parent cursor in the library cache."
            },
            "snap_id":{
                "type":"integer",
                "description":"Unique snapshot ID."
            },
            "dbid":{
                "type":"integer",
                "description":"Database ID for the snapshot."
            },
            "instance_number":{
                "type":"integer",
                "description":"Instance number for the snapshot."
            },
            "plan_hash_value":{
                "type":"integer",
                "description":"Numerical representation of the SQL plan for the cursor. Comparing one PLAN_HASH_VALUE to another easily identifies whether or not two plans are the same (rather than comparing the two plans line by line)."
            },
            "optimizer_cost":{
                "type":"integer",
                "description":"Cost of the query given by the optimizer."
            },
            "optimizer_mode":{
                "type":"string",
                "description":"Mode under which the SQL statement is executed."
            },
            "optimizer_env_hash_value":{
                "type":"integer",
                "description":"Hash Value for the optimizer environment."
            },
            "sharable_mem":{
                "type":"integer",
                "description":"Amount of shared memory used by the child cursor (in bytes)."
            },
            "loaded_versions":{
                "type":"integer",
                "description":"Indicates whether the context heap is loaded (1) or not (0)."
            },
            "version_count":{
                "type":"integer",
                "description":"Number of children associated with the cursor."
            },
            "module":{
                "type":"string",
                "description":"Contains the name of the module that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_MODULE."
            },
            "action":{
                "type":"string",
                "description":"Contains the name of the action that was executing at the time that the SQL statement was first parsed, which is set by calling DBMS_APPLICATION_INFO.SET_ACTION."
            },
            "sql_profile":{
                "type":"string",
                "description":"Name of the applied SQL Profile."
            },
            "force_matching_signature":{
                "type":"integer",
                "description":"The signature used when the CURSOR_SHARING parameter is set to FORCE."
            },
            "parsing_schema_id":{
                "type":"integer",
                "description":"Schema ID that was used to originally build the child cursor."
            },
            "parsing_schema_name":{
                "type":"string",
                "description":"Schema name that was used to originally build the child cursor."
            },
            "parsing_user_id":{
                "type":"integer",
                "description":"User ID that was used to originally build the child cursor."
            },
            "fetches_total":{
                "type":"integer",
                "description":"Cumulative number of fetches associated with the SQL statement."
            },
            "fetches_delta":{
                "type":"integer",
                "description":"Delta number of fetches associated with the SQL statement."
            },
            "end_of_fetch_count_total":{
                "type":"integer",
                "description":"Cumulative number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed. By definition, the value of the END_OF_FETCH_COUNT column should be less or equal to the value of the EXECUTIONS column."
            },
            "end_of_fetch_count_delta":{
                "type":"integer",
                "description":"Delta number of times this cursor was fully executed since the cursor was brought into the library cache. The value of this statistic is not incremented when the cursor is partially executed, either because it failed during the execution or because only the first few rows produced by this cursor are fetched before the cursor is closed or re-executed."
            },
            "sorts_total":{
                "type":"integer",
                "description":"Cumulative number of sorts that were done for this child cursor."
            },
            "sorts_delta":{
                "type":"integer",
                "description":"Delta number of sorts that were done for this child cursor."
            },
            "executions_total":{
                "type":"integer",
                "description":"Cumulative number of executions that took place on this object since it was brought into the library cache."
            },
            "executions_delta":{
                "type":"integer",
                "description":"Delta number of executions that took place on this object since it was brought into the library cache."
            },
            "px_servers_execs_total":{
                "type":"integer",
                "description":"Cumulative number of PX server executions."
            },
            "px_servers_execs_delta":{
                "type":"integer",
                "description":"Delta number of PX server executions."
            },
            "loads_total":{
                "type":"integer",
                "description":"Cumulative number of times the object was either loaded or reloaded."
            },
            "loads_delta":{
                "type":"integer",
                "description":"Delta number of times the object was either loaded or reloaded."
            },
            "invalidations_total":{
                "type":"integer",
                "description":"Cumulative number of times this child cursor has been invalidated."
            },
            "invalidations_delta":{
                "type":"integer",
                "description":"Delta number of times this child cursor has been invalidated."
            },
            "parse_calls_total":{
                "type":"integer",
                "description":"Cumulative number of parse calls for this child cursor."
            },
            "parse_calls_delta":{
                "type":"integer",
                "description":"Delta number of parse calls for this child cursor."
            },
            "disk_reads_total":{
                "type":"integer",
                "description":"Cumulative number of disk reads for this child cursor."
            },
            "disk_reads_delta":{
                "type":"integer",
                "description":"Delta number of disk reads for this child cursor."
            },
            "buffer_gets_total":{
                "type":"integer",
                "description":"Cumulative number of buffer gets for this child cursor."
            },
            "buffer_gets_delta":{
                "type":"integer",
                "description":"Delta number of buffer gets for this child cursor."
            },
            "rows_processed_total":{
                "type":"integer",
                "description":"Cumulative number of rows the parsed SQL statement returns."
            },
            "rows_processed_delta":{
                "type":"integer",
                "description":"Delta number of rows the parsed SQL statement returns."
            },
            "cpu_time_total":{
                "type":"integer",
                "description":"Cumulative value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
            },
            "cpu_time_delta":{
                "type":"integer",
                "description":"Delta value of CPU time (in microseconds) used by this cursor for parsing/executing/fetching."
            },
            "elapsed_time_total":{
                "type":"integer",
                "description":"Cumulative value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching. If the cursor uses parallel execution, then ELAPSED_TIME_TOTAL is the cumulative time for the query coordinator, plus all parallel query slave processes."
            },
            "elapsed_time_delta":{
                "type":"integer",
                "description":"Delta value of elapsed time (in microseconds) used by this cursor for parsing/executing/fetching."
            },
            "iowait_total":{
                "type":"integer",
                "description":"Cumulative value of user I/O wait time (in microseconds)."
            },
            "iowait_delta":{
                "type":"integer",
                "description":"Delta value of user I/O wait time (in microseconds)."
            },
            "clwait_total":{
                "type":"integer",
                "description":"Cumulative value of cluster wait time (in microseconds)."
            },
            "clwait_delta":{
                "type":"integer",
                "description":"Delta value of cluster wait time (in microseconds)."
            },
            "apwait_total":{
                "type":"integer",
                "description":"Cumulative value of application wait time (in microseconds)."
            },
            "apwait_delta":{
                "type":"integer",
                "description":"Delta value of application wait time (in microseconds)."
            },
            "ccwait_total":{
                "type":"integer",
                "description":"Cumulative value of concurrency wait time (in microseconds)."
            },
            "ccwait_delta":{
                "type":"integer",
                "description":"Delta value of concurrency wait time (in microseconds)."
            },
            "direct_writes_total":{
                "type":"integer",
                "description":"Cumulative value of direct writes."
            },
            "direct_writes_delta":{
                "type":"integer",
                "description":"Delta value of direct writes."
            },
            "plsexec_time_total":{
                "type":"integer",
                "description":"Cumulative value of PL/SQL Execution Time (in microseconds)."
            },
            "plsexec_time_delta":{
                "type":"integer",
                "description":"Delta value of PL/SQL Execution Time (in microseconds)."
            },
            "javexec_time_total":{
                "type":"integer",
                "description":"Cumulative value of Java Execution Time (in microseconds)."
            },
            "javexec_time_delta":{
                "type":"integer",
                "description":"Delta value of Java Execution Time (in microseconds)."
            },
            "io_offload_elig_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of I/O bytes which can be filtered by the Exadata storage system."
            },
            "io_offload_elig_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of I/O bytes which can be filtered by the Exadata storage system."
            },
            "io_interconnect_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of I/O bytes exchanged between Oracle Database and the storage system."
            },
            "io_interconnect_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of I/O bytes exchanged between Oracle Database and the storage system."
            },
            "physical_read_requests_total":{
                "type":"integer",
                "description":"Cumulative value of number of physical read I/O requests issued by the monitored SQL."
            },
            "physical_read_requests_delta":{
                "type":"integer",
                "description":"Delta value of number of physical read I/O requests issued by the monitored SQL."
            },
            "physical_read_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of bytes read from disks by the monitored SQL."
            },
            "physical_read_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of bytes read from disks by the monitored SQL."
            },
            "physical_write_requests_total":{
                "type":"integer",
                "description":"Cumulative value of number of physical write I/O requests issued by the monitored SQL."
            },
            "physical_write_requests_delta":{
                "type":"integer",
                "description":"Delta value of number of physical write I/O requests issued by the monitored SQL."
            },
            "physical_write_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of bytes written to disks by the monitored SQL."
            },
            "physical_write_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of bytes written to disks by the monitored SQL."
            },
            "optimized_physical_reads_total":{
                "type":"integer",
                "description":"Cumulative value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
            },
            "optimized_physical_reads_delta":{
                "type":"integer",
                "description":"Delta value of number of physical reads from the Database Smart Flash Cache or the Exadata Smart Flash Cache by the monitored SQL."
            },
            "cell_uncompressed_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
            },
            "cell_uncompressed_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of uncompressed bytes (that is, size after decompression) that are offloaded to the Exadata cells."
            },
            "io_offload_return_bytes_total":{
                "type":"integer",
                "description":"Cumulative value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
            },
            "io_offload_return_bytes_delta":{
                "type":"integer",
                "description":"Delta value of number of bytes that are returned by the Exadata cell for smart scan only (that is, not including bytes for other database I/O)."
            },
            "bind_data":{
                "type":"string",
                "description":"Bind data."
            },
            "con_dbid":{
                "type":"integer",
                "description":"The database ID of the PDB for the sampled session."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container that CON_DBID identifies."
            },
            "elapsed_time_delta_s_per_exec":{
                "type":"number",
                "description":"Average elapsed time (in seconds) for parsing/executing/fetching across all recorded executions."
            },
            "sum_executions_delta":{
                "type":"integer",
                "description":"Total of all executions that took place on this object since it was brought into the library cache."
            }
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
