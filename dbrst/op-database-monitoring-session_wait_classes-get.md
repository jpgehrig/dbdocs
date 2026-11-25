Returns all records from GV\$SESSION_WAIT_CLASS. A client requires SQL Administrator role to invoke this service.

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

Summary of session wait classes in the database.

Body ()

Root Schema : MonitoringSessionWaitClasses

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
                    "$ref":"#/definitions/MonitoringSessionWaitClassesItem"
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

- Array of: object MonitoringSessionWaitClassesItem
  This object represents a record from GV\$SESSION_WAIT_CLASS view. GV\$SESSION_WAIT_CLASS displays the time spent in various wait event operations on a per-session basis. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/MonitoringSessionWaitClassesItem"
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

Nested Schema : MonitoringSessionWaitClassesItem

Type: `object`

This object represents a record from GV\$SESSION_WAIT_CLASS view. GV\$SESSION_WAIT_CLASS displays the time spent in various wait event operations on a per-session basis. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- links(optional): array links
- serial#(optional): integer
  Serial number.
- sid(optional): integer
  Session identifier.
- time_waited(optional): integer
  Amount of time spent in the wait class by the session.
- total_waits(optional): integer
  Number of times waits of the class occurred for the session.
- wait_class(optional): string
  Name of the wait class.
- wait_class#(optional): integer
  Number of the wait class.
- wait_class_id(optional): integer
  Identifier of the wait class.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a record from GV$SESSION_WAIT_CLASS view. GV$SESSION_WAIT_CLASS displays the time spent in various wait event operations on a per-session basis. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "sid":{
                "type":"integer",
                "description":"Session identifier."
            },
            "serial#":{
                "type":"integer",
                "description":"Serial number."
            },
            "wait_class_id":{
                "type":"integer",
                "description":"Identifier of the wait class."
            },
            "wait_class#":{
                "type":"integer",
                "description":"Number of the wait class."
            },
            "wait_class":{
                "type":"string",
                "description":"Name of the wait class."
            },
            "total_waits":{
                "type":"integer",
                "description":"Number of times waits of the class occurred for the session."
            },
            "time_waited":{
                "type":"integer",
                "description":"Amount of time spent in the wait class by the session."
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
