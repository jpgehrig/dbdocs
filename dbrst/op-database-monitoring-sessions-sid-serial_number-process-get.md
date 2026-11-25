Returns all records from GV\$PROCESS for a specific session. A client requires SQL Administrator role to invoke this service.

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

Description of actives processes for a session.

Body ()

Root Schema : MonitoringSessionsProcessItem

Type: `object`

This object represents information about the currently active processes for a specific session. Data is retrieved from GV\$PROCESS view.

Show Source

- addr(optional): string
  Address of the process state object.
- background(optional): string
  1 for a SYSTEM background process; NULL for foreground processes or non-SYSTEM background processes.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- cpu_used(optional): integer
  Tracks the CPU used by this process (in microseconds) from the time it was spawned.
- execution_type(optional): string
  Operating system execution type.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- latchspin(optional): string
  This column is obsolete.
- latchwait(optional): string
  Address of the latch the process is waiting for; NULL if none.
- links(optional): array links
- numa_curr(optional): integer
  The NUMA processor group of this process currently.
- numa_default(optional): integer
  The NUMA processor group of this process at initialization time.
- pga_alloc_mem(optional): integer
  PGA memory currently allocated by the process (including free PGA memory not yet released to the operating system by the server process), in bytes.
- pga_freeable_mem(optional): integer
  Allocated PGA memory which can be freed (in bytes).
- pga_max_mem(optional): integer
  Maximum PGA memory ever allocated by the process (in bytes).
- pga_used_mem(optional): integer
  PGA memory currently used by the process (in bytes).
- pid(optional): integer
  Oracle process identifier.
- pname(optional): string
  Name of this process.
- program(optional): string
  Program in progress.
- serial#(optional): integer
  Process serial number.
- sosid(optional): string
  Operating system (process, thread) identifier.
- spid(optional): string
  Operating system process identifier.
- stid(optional): string
  Operating system thread identifier.
- terminal(optional): string
  Operating system terminal identifier.
- tracefile(optional): string
  Trace file name of the process.
- traceid(optional): string
  Trace file identifier.
- username(optional): string
  Operating system process username.

<!-- -->

    {
        "type":"object",
        "description":"This object represents information about the currently active processes for a specific session. Data is retrieved from GV$PROCESS view.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "addr":{
                "type":"string",
                "description":"Address of the process state object."
            },
            "pid":{
                "type":"integer",
                "description":"Oracle process identifier."
            },
            "sosid":{
                "type":"string",
                "description":"Operating system (process, thread) identifier."
            },
            "spid":{
                "type":"string",
                "description":"Operating system process identifier."
            },
            "stid":{
                "type":"string",
                "description":"Operating system thread identifier."
            },
            "execution_type":{
                "type":"string",
                "description":"Operating system execution type."
            },
            "pname":{
                "type":"string",
                "description":"Name of this process."
            },
            "username":{
                "type":"string",
                "description":"Operating system process username."
            },
            "serial#":{
                "type":"integer",
                "description":"Process serial number."
            },
            "terminal":{
                "type":"string",
                "description":"Operating system terminal identifier."
            },
            "program":{
                "type":"string",
                "description":"Program in progress."
            },
            "traceid":{
                "type":"string",
                "description":"Trace file identifier."
            },
            "tracefile":{
                "type":"string",
                "description":"Trace file name of the process."
            },
            "background":{
                "type":"string",
                "description":"1 for a SYSTEM background process; NULL for foreground processes or non-SYSTEM background processes."
            },
            "latchwait":{
                "type":"string",
                "description":"Address of the latch the process is waiting for; NULL if none."
            },
            "latchspin":{
                "type":"string",
                "description":"This column is obsolete."
            },
            "pga_used_mem":{
                "type":"integer",
                "description":"PGA memory currently used by the process (in bytes)."
            },
            "pga_alloc_mem":{
                "type":"integer",
                "description":"PGA memory currently allocated by the process (including free PGA memory not yet released to the operating system by the server process), in bytes."
            },
            "pga_freeable_mem":{
                "type":"integer",
                "description":"Allocated PGA memory which can be freed (in bytes)."
            },
            "pga_max_mem":{
                "type":"integer",
                "description":"Maximum PGA memory ever allocated by the process (in bytes)."
            },
            "numa_default":{
                "type":"integer",
                "description":"The NUMA processor group of this process at initialization time."
            },
            "numa_curr":{
                "type":"integer",
                "description":"The NUMA processor group of this process currently."
            },
            "cpu_used":{
                "type":"integer",
                "description":"Tracks the CPU used by this process (in microseconds) from the time it was spawned."
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
