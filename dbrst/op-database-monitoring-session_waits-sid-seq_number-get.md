Returns the corresponding record from GV\$SESSION_WAIT. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- seq_number: number
  Wait sequence number.
- sid: number
  Session identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on the specified session wait.

Body ()

Root Schema : MonitoringSessionWaitsItem

Type: `object`

This object represents a record from GV\$SESSION_WAIT view. GV\$SESSION_WAIT displays the current or last wait for each session. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- event(optional): string
  If the session is currently waiting, then the resource or event for which the session is waiting. If the session is not in a wait, then the resource or event for which the session most recently waited.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- links(optional): array links
- p1(optional): integer
  First wait event parameter (in decimal).
- p1raw(optional): string
  First wait event parameter (in hexadecimal).
- p1text(optional): string
  Description of the first wait event parameter.
- p2(optional): integer
  Second wait event parameter (in decimal).
- p2raw(optional): string
  Second wait event parameter (in hexadecimal).
- p2text(optional): string
  Description of the second wait event parameter.
- p3(optional): integer
  Third wait event parameter (in decimal).
- p3raw(optional): string
  Third wait event parameter (in hexadecimal).
- p3text(optional): string
  Description of the third wait event parameter.
- seconds_in_wait(optional): integer
  If the session is currently waiting, then the value is the amount of time waited for the current wait. If the session is not in a wait, then the value is the amount of time since the start of the last wait.
- seq#(optional): integer
  A number that uniquely identifies the current or last wait (incremented for each wait).
- sid(optional): integer
  Session identifier.
- state(optional): string
  Wait state.
- time_remaining_micro(optional): integer
  Amount of time remaining remaining before a timeout. This field may indicate that a timeout has occurred, or that no timeout will occur.
- time_since_last_wait_micro(optional): integer
  Time elapsed since the end of the last wait (in microseconds). If the session is currently in a wait, then the value is 0.
- wait_class(optional): string
  Name of the class of the wait event.
- wait_class#(optional): integer
  Number of the class of the wait event.
- wait_class_id(optional): integer
  Identifier of the class of the wait event.
- wait_time(optional): integer
  If the session is currently waiting, then the value is 0. If the session is not in a wait, then the value indicates the duration of the last wait.
- wait_time_micro(optional): integer
  Amount of time waited (in microseconds). If the session is currently waiting, then the value is the time spent in the current wait. If the session is currently not in a wait, then the value is the amount of time waited in the last wait.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a record from GV$SESSION_WAIT view. GV$SESSION_WAIT displays the current or last wait for each session. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "sid":{
                "type":"integer",
                "description":"Session identifier."
            },
            "seq#":{
                "type":"integer",
                "description":"A number that uniquely identifies the current or last wait (incremented for each wait)."
            },
            "event":{
                "type":"string",
                "description":"If the session is currently waiting, then the resource or event for which the session is waiting. If the session is not in a wait, then the resource or event for which the session most recently waited."
            },
            "p1text":{
                "type":"string",
                "description":"Description of the first wait event parameter."
            },
            "p1":{
                "type":"integer",
                "description":"First wait event parameter (in decimal)."
            },
            "p1raw":{
                "type":"string",
                "description":"First wait event parameter (in hexadecimal)."
            },
            "p2text":{
                "type":"string",
                "description":"Description of the second wait event parameter."
            },
            "p2":{
                "type":"integer",
                "description":"Second wait event parameter (in decimal)."
            },
            "p2raw":{
                "type":"string",
                "description":"Second wait event parameter (in hexadecimal)."
            },
            "p3text":{
                "type":"string",
                "description":"Description of the third wait event parameter."
            },
            "p3":{
                "type":"integer",
                "description":"Third wait event parameter (in decimal)."
            },
            "p3raw":{
                "type":"string",
                "description":"Third wait event parameter (in hexadecimal)."
            },
            "wait_class_id":{
                "type":"integer",
                "description":"Identifier of the class of the wait event."
            },
            "wait_class#":{
                "type":"integer",
                "description":"Number of the class of the wait event."
            },
            "wait_class":{
                "type":"string",
                "description":"Name of the class of the wait event."
            },
            "wait_time":{
                "type":"integer",
                "description":"If the session is currently waiting, then the value is 0. If the session is not in a wait, then the value indicates the duration of the last wait."
            },
            "seconds_in_wait":{
                "type":"integer",
                "description":"If the session is currently waiting, then the value is the amount of time waited for the current wait. If the session is not in a wait, then the value is the amount of time since the start of the last wait."
            },
            "state":{
                "type":"string",
                "description":"Wait state."
            },
            "wait_time_micro":{
                "type":"integer",
                "description":"Amount of time waited (in microseconds). If the session is currently waiting, then the value is the time spent in the current wait. If the session is currently not in a wait, then the value is the amount of time waited in the last wait."
            },
            "time_remaining_micro":{
                "type":"integer",
                "description":"Amount of time remaining remaining before a timeout. This field may indicate that a timeout has occurred, or that no timeout will occur."
            },
            "time_since_last_wait_micro":{
                "type":"integer",
                "description":"Time elapsed since the end of the last wait (in microseconds). If the session is currently in a wait, then the value is 0."
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
