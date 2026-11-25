Returns maximum values for cpu time, elapsed time, disk reads, buffer gets and executions from GV\$SQL. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Maximum values for SQL statement performance statistics recorded in GV\$SQL.

Body ()

Root Schema : PerformanceTopSQLStatementsMaximumsItem

Type: `object`

Describes the maximum values on GV\$SQL view.

Show Source

- links(optional): array links
- max_buffer_gets(optional): integer
  Maximum number of buffer gets by an SQL Statement.
- max_cpu_time(optional): integer
  Maximum CPU time (in microseconds) used by an SQL Statement for parsing, executing, and fetching.
- max_disk_reads(optional): integer
  Maximum number of disk reads by an SQL Statement.
- max_elapsed_time(optional): integer
  Maximum elapsed time (in microseconds) used by an SQL Statement for parsing, executing, and fetching..
- max_executions(optional): integer
  Maximum number of executions that took place for an SQL Statement since it was brought into the library cache.

<!-- -->

    {
        "type":"object",
        "description":"Describes the maximum values on GV$SQL view.",
        "properties":{
            "max_cpu_time":{
                "type":"integer",
                "description":"Maximum CPU time (in microseconds) used by an SQL Statement for parsing, executing, and fetching."
            },
            "max_elapsed_time":{
                "type":"integer",
                "description":"Maximum elapsed time (in microseconds) used by an SQL Statement for parsing, executing, and fetching.."
            },
            "max_disk_reads":{
                "type":"integer",
                "description":"Maximum number of disk reads by an SQL Statement."
            },
            "max_buffer_gets":{
                "type":"integer",
                "description":"Maximum number of buffer gets by an SQL Statement."
            },
            "max_executions":{
                "type":"integer",
                "description":"Maximum number of executions that took place for an SQL Statement since it was brought into the library cache."
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
