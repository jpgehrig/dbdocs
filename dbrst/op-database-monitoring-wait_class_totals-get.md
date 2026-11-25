Returns all the records from GV\$SYSTEM_WAIT_CLASS, except 'Idle' wait class. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Summary information on the wait class time totals.

Body ()

Root Schema : MonitoringWaitClassTotalsItem

Type: `object`

Time totals for each registered wait class

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- links(optional): array links
- time_waited(optional): integer
  Amount of time (in hundredths of a second) spent in the wait by all sessions in the instance.
- time_waited_fg(optional): integer
  Amount of time (in hundredths of a second) spent in waits from this wait class in foreground sessions.
- total_waits(optional): integer
  Number of times waits of the class occurred.
- total_waits_fg(optional): integer
  Number of times waits from this wait class occurred in foreground sessions.
- wait_class(optional): string
  Name of the wait class.
- wait_class#(optional): integer
  Number of the wait class.
- wait_class_id(optional): integer
  Identifier of the wait class.

<!-- -->

    {
        "type":"object",
        "description":"Time totals for each registered wait class",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
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
                "description":"Number of times waits of the class occurred."
            },
            "time_waited":{
                "type":"integer",
                "description":"Amount of time (in hundredths of a second) spent in the wait by all sessions in the instance."
            },
            "total_waits_fg":{
                "type":"integer",
                "description":"Number of times waits from this wait class occurred in foreground sessions."
            },
            "time_waited_fg":{
                "type":"integer",
                "description":"Amount of time (in hundredths of a second) spent in waits from this wait class in foreground sessions."
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
