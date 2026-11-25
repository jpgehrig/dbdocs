Oracle Tuning Pack licence is required for this service. Returns data from GV\$SQL with GV\$SQL_MONITOR timing data. A client requires SQL Administrator role to invoke this service.

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

Description of all SQL statements in the database.

Body ()

Root Schema : PerformanceSQLStatements

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
                    "$ref":"#/definitions/PerformanceSQLStatementsItem"
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

- Array of: object PerformanceSQLStatementsItem
  This object describes an SQL statement. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/PerformanceSQLStatementsItem"
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

Nested Schema : PerformanceSQLStatementsItem

Type: `object`

This object describes an SQL statement. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- cpu_time(optional): number
  Sum of total CPU time; updated as the statement executes.
- duration(optional): integer
  Indicates the length of time the SQL statement has been running for. Calculated based on SQL_EXEC_START and LAST_REFRESH_TIME from GV\$SQL_MONITOR.
- elapsed_time(optional): integer
  Elapsed time (in microseconds); updated as the statement executes.
- end_time(optional): string
  When the status is 'DONE (ALL ROWS)' this is the LAST_REFRESH_TIME value from GV\$SQL_MONITOR.
- instance_dop(optional): string
  Distinct number of instances that the SQL statement executed compared with the logical parallel execution server process number executing (or having executed) the statement being monitored.
- io_time(optional): number
  Sum of total User I/O Wait Time; updated as the statement executes
- links(optional): array links
- session_id(optional): integer
  Session identifier executing (or having executed) the SQL statement being monitored.
- session_serial(optional): integer
  Session serial number executing the statement being monitored.
- sql_exec_id(optional): integer
  SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started.
- sql_exec_start(optional): string
  Time when the execution started. Part of the execution key for identifying a single record in GV\$SQL_MONITOR.
- sql_fulltext(optional): string
  All characters of the SQL text for the current cursor.
- sql_id(optional): string
  SQL identifier of the statement.
- start_time(optional): string
  Time when the execution started
- status(optional): string
  SQL execution status.

<!-- -->

    {
        "type":"object",
        "description":"This object describes an SQL statement. The list of attributes may vary depending on database version.",
        "properties":{
            "elapsed_time":{
                "type":"integer",
                "description":"Elapsed time (in microseconds); updated as the statement executes."
            },
            "sql_exec_id":{
                "type":"integer",
                "description":"SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started."
            },
            "status":{
                "type":"string",
                "description":"SQL execution status."
            },
            "duration":{
                "type":"integer",
                "description":"Indicates the length of time the SQL statement has been running for. Calculated based on SQL_EXEC_START and LAST_REFRESH_TIME from GV$SQL_MONITOR."
            },
            "sql_id":{
                "type":"string",
                "description":"SQL identifier of the statement."
            },
            "session_id":{
                "type":"integer",
                "description":"Session identifier executing (or having executed) the SQL statement being monitored."
            },
            "session_serial":{
                "type":"integer",
                "description":"Session serial number executing the statement being monitored."
            },
            "instance_dop":{
                "type":"string",
                "description":"Distinct number of instances that the SQL statement executed compared with the logical parallel execution server process number executing (or having executed) the statement being monitored."
            },
            "cpu_time":{
                "type":"number",
                "description":"Sum of total CPU time; updated as the statement executes."
            },
            "io_time":{
                "type":"number",
                "description":"Sum of total User I/O Wait Time; updated as the statement executes"
            },
            "start_time":{
                "type":"string",
                "description":"Time when the execution started"
            },
            "sql_exec_start":{
                "type":"string",
                "description":"Time when the execution started. Part of the execution key for identifying a single record in GV$SQL_MONITOR."
            },
            "end_time":{
                "type":"string",
                "description":"When the status is 'DONE (ALL ROWS)' this is the LAST_REFRESH_TIME value from GV$SQL_MONITOR."
            },
            "sql_fulltext":{
                "type":"string",
                "description":"All characters of the SQL text for the current cursor."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
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
