Oracle Tuning Pack licence is required for this service. Returns information on a monitored statement that is executed in parallel. Using GV\$SQL_MONITOR view, the information includes the Parallel Coordinator and the instance(s) where it was executed. A client requires SQL Administrator role to invoke this service.

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

Returns information on a monitored statement. The structure of the data may vary depending on the database used.

Body ()

Root Schema : PerformanceSQLStatementMonitorParallelism

Type: `object`

Describes the parallel execution of an SQL Statement. Using GV\$SQL_MONITOR view, the information includes the Parallel Coordinator and the instance(s) where it was executed.

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
        "description":"Describes the parallel execution of an SQL Statement. Using GV$SQL_MONITOR view, the information includes the Parallel Coordinator and the instance(s) where it was executed.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "node_id":{
                            "type":"integer",
                            "description":"Used as a distinguishing value in the Parallelism metadata. The value may be an Instance Number to represent the execution on an instance, 10000 when a Parallel Coordinator or some other value derived from the SERVER_GROUP data."
                        },
                        "parent_node_id":{
                            "type":"number",
                            "description":"The value may be an Instance Number to represent the execution of Parallel Coordinator or Server Group on an instance. May be NULL."
                        },
                        "name":{
                            "type":"string",
                            "description":"Name of either the Instance, Parallel Coordinator, Parellel Group, Parallel Set or Parallel Server that corresponds to the GV$SQL_MONITOR record."
                        },
                        "inst_id":{
                            "type":"number",
                            "description":"The Instance Number from the GV$SQL_MONITOR record."
                        },
                        "server_set":{
                            "type":"integer",
                            "description":"Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server."
                        },
                        "process_name":{
                            "type":"string",
                            "description":"Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001)."
                        },
                        "db_time":{
                            "type":"number",
                            "description":"The greater of either ELAPSED_TIME or a total of the following CPU_TIME + QUEUING_TIME + APPLICATION_WAIT_TIME + CONCURRENCY_WAIT_TIME + CLUSTER_WAIT_TIME + USER_IO_WAIT_TIME + PLSQL_EXEC_TIME + JAVA_EXEC_TIME."
                        },
                        "db_time_prop":{
                            "type":"number",
                            "description":"The proportional time spent for this GV$SQL_MONITOR record compared to other execution records for the same SQL Statement."
                        },
                        "db_time_max":{
                            "type":"number",
                            "description":"The maximum time spent for an execution of the SQL Statement."
                        },
                        "cpu_time":{
                            "type":"integer",
                            "description":"CPU time (in microseconds) used by this cursor for parsing, executing, and fetching."
                        },
                        "queuing_time":{
                            "type":"integer",
                            "description":"Duration of time (in microseconds) spent by SQL in the statement queue."
                        },
                        "application_wait_time":{
                            "type":"number",
                            "description":"Application wait time (in microseconds); updated as the statement executes."
                        },
                        "concurrency_wait_time":{
                            "type":"number",
                            "description":"Concurrency wait time (in microseconds); updated as the statement executes."
                        },
                        "cluster_wait_time":{
                            "type":"number",
                            "description":"Cluster wait time (in microseconds); updated as the statement executes."
                        },
                        "user_io_wait_time":{
                            "type":"number",
                            "description":"User I/O Wait Time (in microseconds); updated as the statement executes."
                        },
                        "plsql_exec_time":{
                            "type":"number",
                            "description":"PL/SQL execution time (in microseconds); updated as the statement executes."
                        },
                        "java_exec_time":{
                            "type":"number",
                            "description":"Java execution time (in microseconds); updated as the statement executes."
                        },
                        "other_wait_time":{
                            "type":"number",
                            "description":"The greater of either zero or a total of the following CPU_TIME - QUEUING_TIME - APPLICATION_WAIT_TIME - CONCURRENCY_WAIT_TIME - CLUSTER_WAIT_TIME - USER_IO_WAIT_TIME - PLSQL_EXEC_TIME - JAVA_EXEC_TIME."
                        },
                        "io_requests":{
                            "type":"number",
                            "description":"Total of number of physical read and write I/O requests issued by the monitored SQL."
                        },
                        "io_requests_prop":{
                            "type":"number",
                            "description":"The proportional number of physical read and write I/O requests issued by the monitored SQL compared to other execution records for the same SQL Statement."
                        },
                        "io_requests_max":{
                            "type":"number",
                            "description":"The maximum number of physical read and write I/O requests issued by a monitored SQL execution for the same SQL Statement."
                        },
                        "io_bytes":{
                            "type":"number",
                            "description":"Total of number of bytes read from disks and bytes written to disks by the monitored SQL."
                        },
                        "io_bytes_prop":{
                            "type":"number",
                            "description":"The proportional number of bytes read from disks and bytes written to disks by the monitored SQL compared to other execution records for the same SQL Statement."
                        },
                        "io_bytes_max":{
                            "type":"number",
                            "description":"The maximum number of bytes read from disks and bytes written to disks by a monitored SQL execution for the same SQL Statement."
                        },
                        "buffer_gets":{
                            "type":"number",
                            "description":"Number of buffer get operations; updated as the statement executes."
                        },
                        "buffer_gets_prop":{
                            "type":"number",
                            "description":"The proportional number of buffer get operations compared to other execution records for the same SQL Statement."
                        },
                        "buffer_gets_max":{
                            "type":"number",
                            "description":"The maximum number of buffer get operations by a monitored SQL execution for the same SQL Statement."
                        },
                        "dop_downgrade":{
                            "type":"string",
                            "description":"Percentage of actual number of parallel execution servers allocated to execute the query compared to the total number of parallel execution servers requested to execute the query."
                        },
                        "servers_requested":{
                            "type":"number",
                            "description":"Total number of parallel execution servers requested to execute the monitored SQL."
                        },
                        "servers_allocated":{
                            "type":"number",
                            "description":"Actual number of parallel execution servers allocated to execute the query."
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
                "node_id":{
                    "type":"integer",
                    "description":"Used as a distinguishing value in the Parallelism metadata. The value may be an Instance Number to represent the execution on an instance, 10000 when a Parallel Coordinator or some other value derived from the SERVER_GROUP data."
                },
                "parent_node_id":{
                    "type":"number",
                    "description":"The value may be an Instance Number to represent the execution of Parallel Coordinator or Server Group on an instance. May be NULL."
                },
                "name":{
                    "type":"string",
                    "description":"Name of either the Instance, Parallel Coordinator, Parellel Group, Parallel Set or Parallel Server that corresponds to the GV$SQL_MONITOR record."
                },
                "inst_id":{
                    "type":"number",
                    "description":"The Instance Number from the GV$SQL_MONITOR record."
                },
                "server_set":{
                    "type":"integer",
                    "description":"Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server."
                },
                "process_name":{
                    "type":"string",
                    "description":"Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001)."
                },
                "db_time":{
                    "type":"number",
                    "description":"The greater of either ELAPSED_TIME or a total of the following CPU_TIME + QUEUING_TIME + APPLICATION_WAIT_TIME + CONCURRENCY_WAIT_TIME + CLUSTER_WAIT_TIME + USER_IO_WAIT_TIME + PLSQL_EXEC_TIME + JAVA_EXEC_TIME."
                },
                "db_time_prop":{
                    "type":"number",
                    "description":"The proportional time spent for this GV$SQL_MONITOR record compared to other execution records for the same SQL Statement."
                },
                "db_time_max":{
                    "type":"number",
                    "description":"The maximum time spent for an execution of the SQL Statement."
                },
                "cpu_time":{
                    "type":"integer",
                    "description":"CPU time (in microseconds) used by this cursor for parsing, executing, and fetching."
                },
                "queuing_time":{
                    "type":"integer",
                    "description":"Duration of time (in microseconds) spent by SQL in the statement queue."
                },
                "application_wait_time":{
                    "type":"number",
                    "description":"Application wait time (in microseconds); updated as the statement executes."
                },
                "concurrency_wait_time":{
                    "type":"number",
                    "description":"Concurrency wait time (in microseconds); updated as the statement executes."
                },
                "cluster_wait_time":{
                    "type":"number",
                    "description":"Cluster wait time (in microseconds); updated as the statement executes."
                },
                "user_io_wait_time":{
                    "type":"number",
                    "description":"User I/O Wait Time (in microseconds); updated as the statement executes."
                },
                "plsql_exec_time":{
                    "type":"number",
                    "description":"PL/SQL execution time (in microseconds); updated as the statement executes."
                },
                "java_exec_time":{
                    "type":"number",
                    "description":"Java execution time (in microseconds); updated as the statement executes."
                },
                "other_wait_time":{
                    "type":"number",
                    "description":"The greater of either zero or a total of the following CPU_TIME - QUEUING_TIME - APPLICATION_WAIT_TIME - CONCURRENCY_WAIT_TIME - CLUSTER_WAIT_TIME - USER_IO_WAIT_TIME - PLSQL_EXEC_TIME - JAVA_EXEC_TIME."
                },
                "io_requests":{
                    "type":"number",
                    "description":"Total of number of physical read and write I/O requests issued by the monitored SQL."
                },
                "io_requests_prop":{
                    "type":"number",
                    "description":"The proportional number of physical read and write I/O requests issued by the monitored SQL compared to other execution records for the same SQL Statement."
                },
                "io_requests_max":{
                    "type":"number",
                    "description":"The maximum number of physical read and write I/O requests issued by a monitored SQL execution for the same SQL Statement."
                },
                "io_bytes":{
                    "type":"number",
                    "description":"Total of number of bytes read from disks and bytes written to disks by the monitored SQL."
                },
                "io_bytes_prop":{
                    "type":"number",
                    "description":"The proportional number of bytes read from disks and bytes written to disks by the monitored SQL compared to other execution records for the same SQL Statement."
                },
                "io_bytes_max":{
                    "type":"number",
                    "description":"The maximum number of bytes read from disks and bytes written to disks by a monitored SQL execution for the same SQL Statement."
                },
                "buffer_gets":{
                    "type":"number",
                    "description":"Number of buffer get operations; updated as the statement executes."
                },
                "buffer_gets_prop":{
                    "type":"number",
                    "description":"The proportional number of buffer get operations compared to other execution records for the same SQL Statement."
                },
                "buffer_gets_max":{
                    "type":"number",
                    "description":"The maximum number of buffer get operations by a monitored SQL execution for the same SQL Statement."
                },
                "dop_downgrade":{
                    "type":"string",
                    "description":"Percentage of actual number of parallel execution servers allocated to execute the query compared to the total number of parallel execution servers requested to execute the query."
                },
                "servers_requested":{
                    "type":"number",
                    "description":"Total number of parallel execution servers requested to execute the monitored SQL."
                },
                "servers_allocated":{
                    "type":"number",
                    "description":"Actual number of parallel execution servers allocated to execute the query."
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

- application_wait_time(optional): number
  Application wait time (in microseconds); updated as the statement executes.
- buffer_gets(optional): number
  Number of buffer get operations; updated as the statement executes.
- buffer_gets_max(optional): number
  The maximum number of buffer get operations by a monitored SQL execution for the same SQL Statement.
- buffer_gets_prop(optional): number
  The proportional number of buffer get operations compared to other execution records for the same SQL Statement.
- cluster_wait_time(optional): number
  Cluster wait time (in microseconds); updated as the statement executes.
- concurrency_wait_time(optional): number
  Concurrency wait time (in microseconds); updated as the statement executes.
- cpu_time(optional): integer
  CPU time (in microseconds) used by this cursor for parsing, executing, and fetching.
- db_time(optional): number
  The greater of either ELAPSED_TIME or a total of the following CPU_TIME + QUEUING_TIME + APPLICATION_WAIT_TIME + CONCURRENCY_WAIT_TIME + CLUSTER_WAIT_TIME + USER_IO_WAIT_TIME + PLSQL_EXEC_TIME + JAVA_EXEC_TIME.
- db_time_max(optional): number
  The maximum time spent for an execution of the SQL Statement.
- db_time_prop(optional): number
  The proportional time spent for this GV\$SQL_MONITOR record compared to other execution records for the same SQL Statement.
- dop_downgrade(optional): string
  Percentage of actual number of parallel execution servers allocated to execute the query compared to the total number of parallel execution servers requested to execute the query.
- inst_id(optional): number
  The Instance Number from the GV\$SQL_MONITOR record.
- io_bytes(optional): number
  Total of number of bytes read from disks and bytes written to disks by the monitored SQL.
- io_bytes_max(optional): number
  The maximum number of bytes read from disks and bytes written to disks by a monitored SQL execution for the same SQL Statement.
- io_bytes_prop(optional): number
  The proportional number of bytes read from disks and bytes written to disks by the monitored SQL compared to other execution records for the same SQL Statement.
- io_requests(optional): number
  Total of number of physical read and write I/O requests issued by the monitored SQL.
- io_requests_max(optional): number
  The maximum number of physical read and write I/O requests issued by a monitored SQL execution for the same SQL Statement.
- io_requests_prop(optional): number
  The proportional number of physical read and write I/O requests issued by the monitored SQL compared to other execution records for the same SQL Statement.
- java_exec_time(optional): number
  Java execution time (in microseconds); updated as the statement executes.
- name(optional): string
  Name of either the Instance, Parallel Coordinator, Parellel Group, Parallel Set or Parallel Server that corresponds to the GV\$SQL_MONITOR record.
- node_id(optional): integer
  Used as a distinguishing value in the Parallelism metadata. The value may be an Instance Number to represent the execution on an instance, 10000 when a Parallel Coordinator or some other value derived from the SERVER_GROUP data.
- other_wait_time(optional): number
  The greater of either zero or a total of the following CPU_TIME - QUEUING_TIME - APPLICATION_WAIT_TIME - CONCURRENCY_WAIT_TIME - CLUSTER_WAIT_TIME - USER_IO_WAIT_TIME - PLSQL_EXEC_TIME - JAVA_EXEC_TIME.
- parent_node_id(optional): number
  The value may be an Instance Number to represent the execution of Parallel Coordinator or Server Group on an instance. May be NULL.
- plsql_exec_time(optional): number
  PL/SQL execution time (in microseconds); updated as the statement executes.
- process_name(optional): string
  Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001).
- queuing_time(optional): integer
  Duration of time (in microseconds) spent by SQL in the statement queue.
- server_set(optional): integer
  Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V\$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server.
- servers_allocated(optional): number
  Actual number of parallel execution servers allocated to execute the query.
- servers_requested(optional): number
  Total number of parallel execution servers requested to execute the monitored SQL.
- user_io_wait_time(optional): number
  User I/O Wait Time (in microseconds); updated as the statement executes.

<!-- -->

    {
        "type":"object",
        "properties":{
            "node_id":{
                "type":"integer",
                "description":"Used as a distinguishing value in the Parallelism metadata. The value may be an Instance Number to represent the execution on an instance, 10000 when a Parallel Coordinator or some other value derived from the SERVER_GROUP data."
            },
            "parent_node_id":{
                "type":"number",
                "description":"The value may be an Instance Number to represent the execution of Parallel Coordinator or Server Group on an instance. May be NULL."
            },
            "name":{
                "type":"string",
                "description":"Name of either the Instance, Parallel Coordinator, Parellel Group, Parallel Set or Parallel Server that corresponds to the GV$SQL_MONITOR record."
            },
            "inst_id":{
                "type":"number",
                "description":"The Instance Number from the GV$SQL_MONITOR record."
            },
            "server_set":{
                "type":"integer",
                "description":"Number (1 or 2) of the logical set of parallel execution servers to which PX_SERVER# belongs (see SERVER_SET in V$PX_SESSION); NULL if this monitoring entry is not associated with a parallel execution server."
            },
            "process_name":{
                "type":"string",
                "description":"Process name identifier executing (or having executed)the statement; ora if the process is foreground, else the background process name (for example, p001 for PX server p001)."
            },
            "db_time":{
                "type":"number",
                "description":"The greater of either ELAPSED_TIME or a total of the following CPU_TIME + QUEUING_TIME + APPLICATION_WAIT_TIME + CONCURRENCY_WAIT_TIME + CLUSTER_WAIT_TIME + USER_IO_WAIT_TIME + PLSQL_EXEC_TIME + JAVA_EXEC_TIME."
            },
            "db_time_prop":{
                "type":"number",
                "description":"The proportional time spent for this GV$SQL_MONITOR record compared to other execution records for the same SQL Statement."
            },
            "db_time_max":{
                "type":"number",
                "description":"The maximum time spent for an execution of the SQL Statement."
            },
            "cpu_time":{
                "type":"integer",
                "description":"CPU time (in microseconds) used by this cursor for parsing, executing, and fetching."
            },
            "queuing_time":{
                "type":"integer",
                "description":"Duration of time (in microseconds) spent by SQL in the statement queue."
            },
            "application_wait_time":{
                "type":"number",
                "description":"Application wait time (in microseconds); updated as the statement executes."
            },
            "concurrency_wait_time":{
                "type":"number",
                "description":"Concurrency wait time (in microseconds); updated as the statement executes."
            },
            "cluster_wait_time":{
                "type":"number",
                "description":"Cluster wait time (in microseconds); updated as the statement executes."
            },
            "user_io_wait_time":{
                "type":"number",
                "description":"User I/O Wait Time (in microseconds); updated as the statement executes."
            },
            "plsql_exec_time":{
                "type":"number",
                "description":"PL/SQL execution time (in microseconds); updated as the statement executes."
            },
            "java_exec_time":{
                "type":"number",
                "description":"Java execution time (in microseconds); updated as the statement executes."
            },
            "other_wait_time":{
                "type":"number",
                "description":"The greater of either zero or a total of the following CPU_TIME - QUEUING_TIME - APPLICATION_WAIT_TIME - CONCURRENCY_WAIT_TIME - CLUSTER_WAIT_TIME - USER_IO_WAIT_TIME - PLSQL_EXEC_TIME - JAVA_EXEC_TIME."
            },
            "io_requests":{
                "type":"number",
                "description":"Total of number of physical read and write I/O requests issued by the monitored SQL."
            },
            "io_requests_prop":{
                "type":"number",
                "description":"The proportional number of physical read and write I/O requests issued by the monitored SQL compared to other execution records for the same SQL Statement."
            },
            "io_requests_max":{
                "type":"number",
                "description":"The maximum number of physical read and write I/O requests issued by a monitored SQL execution for the same SQL Statement."
            },
            "io_bytes":{
                "type":"number",
                "description":"Total of number of bytes read from disks and bytes written to disks by the monitored SQL."
            },
            "io_bytes_prop":{
                "type":"number",
                "description":"The proportional number of bytes read from disks and bytes written to disks by the monitored SQL compared to other execution records for the same SQL Statement."
            },
            "io_bytes_max":{
                "type":"number",
                "description":"The maximum number of bytes read from disks and bytes written to disks by a monitored SQL execution for the same SQL Statement."
            },
            "buffer_gets":{
                "type":"number",
                "description":"Number of buffer get operations; updated as the statement executes."
            },
            "buffer_gets_prop":{
                "type":"number",
                "description":"The proportional number of buffer get operations compared to other execution records for the same SQL Statement."
            },
            "buffer_gets_max":{
                "type":"number",
                "description":"The maximum number of buffer get operations by a monitored SQL execution for the same SQL Statement."
            },
            "dop_downgrade":{
                "type":"string",
                "description":"Percentage of actual number of parallel execution servers allocated to execute the query compared to the total number of parallel execution servers requested to execute the query."
            },
            "servers_requested":{
                "type":"number",
                "description":"Total number of parallel execution servers requested to execute the monitored SQL."
            },
            "servers_allocated":{
                "type":"number",
                "description":"Actual number of parallel execution servers allocated to execute the query."
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
