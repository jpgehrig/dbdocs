Returns all records from GV\$SESSION_LONGOPS for a specific session. A client requires SQL Administrator role to invoke this service.

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

Information on long running operations for the session.

Body ()

Root Schema : MonitoringSessionsLongRunningOperationItem

Type: `object`

This object represents operations for a specific session that run for longer than 6 seconds (in absolute time).

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- context(optional): integer
  Context.
- elapsed_seconds(optional): integer
  Number of elapsed seconds from the start of the operations.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- last_update_time(optional): string
  Time when statistics were last updated for the operation.
- links(optional): array links
- message(optional): string
  Statistics summary message.
- opname(optional): string
  Brief description of the operation.
- qcsid(optional): integer
  Session identifier of the parallel coordinator.
- serial#(optional): integer
  Serial number of the session processing the long-running operation. If multiple sessions are cooperating in the long-running operation, then SERIAL# corresponds to the main or master session. SERIAL# is used to uniquely identify a session's objects. Guarantees that session-level commands are applied to the correct session objects if the session ends and another session begins with the same session ID.
- sid(optional): integer
  Identifier of the session processing the long-running operation. If multiple sessions are cooperating in the long-running operation, then SID corresponds to the main or master session.
- sofar(optional): integer
  Units of work done so far for the operation specified in the OPNAME column.
- sql_address(optional): string
  Used with sql_hash_value to identify the SQL statement that is currently being executed.
- sql_exec_id(optional): integer
  SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started.
- sql_exec_start(optional): string
  Time when the execution of the SQL currently executed by this session started; NULL if SQL_ID is NULL.
- sql_hash_value(optional): integer
  Used with SQL_ADDRESS to identify the SQL statement that is currently being executed.
- sql_id(optional): string
  SQL identifier of the SQL statement that is currently being executed.
- sql_plan_hash_value(optional): integer
  Used with the value of the SQL_ADDRESS column to identify the SQL statement associated with the operation.
- sql_plan_line_id(optional): integer
  SQL plan line ID corresponding to the long operation; NULL if the long operation is not associated with a line of the execution plan.
- sql_plan_operation(optional): string
  Plan operation name; NULL if SQL_PLAN_LINE_ID is NULL.
- sql_plan_options(optional): string
  Plan operation options; NULL if SQL_PLAN_LINE_ID is NULL.
- start_time(optional): string
  Starting time of the operation.
- target(optional): string
  Object on which the operation is carried out.
- target_desc(optional): string
  Description of the target.
- time_remaining(optional): integer
  Estimate (in seconds) of time remaining for the operation to complete.
- timestamp(optional): string
  Timestamp specific to the operation.
- totalwork(optional): integer
  Total units of work for the operation specified in the OPNAME column.
- units(optional): string
  Units of measurement.
- username(optional): string
  User ID of the user performing the operation.

<!-- -->

    {
        "type":"object",
        "description":"This object represents operations for a specific session that run for longer than 6 seconds (in absolute time).",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "sid":{
                "type":"integer",
                "description":"Identifier of the session processing the long-running operation. If multiple sessions are cooperating in the long-running operation, then SID corresponds to the main or master session."
            },
            "serial#":{
                "type":"integer",
                "description":"Serial number of the session processing the long-running operation. If multiple sessions are cooperating in the long-running operation, then SERIAL# corresponds to the main or master session. SERIAL# is used to uniquely identify a session's objects. Guarantees that session-level commands are applied to the correct session objects if the session ends and another session begins with the same session ID."
            },
            "opname":{
                "type":"string",
                "description":"Brief description of the operation."
            },
            "target":{
                "type":"string",
                "description":"Object on which the operation is carried out."
            },
            "target_desc":{
                "type":"string",
                "description":"Description of the target."
            },
            "sofar":{
                "type":"integer",
                "description":"Units of work done so far for the operation specified in the OPNAME column."
            },
            "totalwork":{
                "type":"integer",
                "description":"Total units of work for the operation specified in the OPNAME column."
            },
            "units":{
                "type":"string",
                "description":"Units of measurement."
            },
            "start_time":{
                "type":"string",
                "description":"Starting time of the operation."
            },
            "last_update_time":{
                "type":"string",
                "description":"Time when statistics were last updated for the operation."
            },
            "timestamp":{
                "type":"string",
                "description":"Timestamp specific to the operation."
            },
            "time_remaining":{
                "type":"integer",
                "description":"Estimate (in seconds) of time remaining for the operation to complete."
            },
            "elapsed_seconds":{
                "type":"integer",
                "description":"Number of elapsed seconds from the start of the operations."
            },
            "context":{
                "type":"integer",
                "description":"Context."
            },
            "message":{
                "type":"string",
                "description":"Statistics summary message."
            },
            "username":{
                "type":"string",
                "description":"User ID of the user performing the operation."
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
            "sql_plan_hash_value":{
                "type":"integer",
                "description":"Used with the value of the SQL_ADDRESS column to identify the SQL statement associated with the operation."
            },
            "sql_exec_start":{
                "type":"string",
                "description":"Time when the execution of the SQL currently executed by this session started; NULL if SQL_ID is NULL."
            },
            "sql_exec_id":{
                "type":"integer",
                "description":"SQL execution identifier; NULL if SQL_ID is NULL or if the execution of that SQL has not yet started."
            },
            "sql_plan_line_id":{
                "type":"integer",
                "description":"SQL plan line ID corresponding to the long operation; NULL if the long operation is not associated with a line of the execution plan."
            },
            "sql_plan_operation":{
                "type":"string",
                "description":"Plan operation name; NULL if SQL_PLAN_LINE_ID is NULL."
            },
            "sql_plan_options":{
                "type":"string",
                "description":"Plan operation options; NULL if SQL_PLAN_LINE_ID is NULL."
            },
            "qcsid":{
                "type":"integer",
                "description":"Session identifier of the parallel coordinator."
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
