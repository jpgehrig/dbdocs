Return data from GV\$SESSION_WAIT_HISTORY for the specified Session Identifier and Event Sequence Number. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- seq_number: number
  Sequence number of wait event; 1 is the most recent.
- sid: number
  Session Identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

The session wait history for a particular session and event.

Body ()

Root Schema : PerformanceActionSessionHistoryWaitsItem

Type: `object`

Describes a wait event for a session. Data corresponds to a record from GV\$SESSION_WAIT_HISTORY. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- event(optional): string
  Resource or event for which the session is waiting.
- event#(optional): integer
  Event number.
- inst_id(optional): integer
  Instance number from which the associated V\$ view information was obtained.
- links(optional): array links
- p1(optional): integer
  First wait event parameter (in decimal).
- p1text(optional): string
  Description of the first wait event parameter.
- p2(optional): integer
  Second wait event parameter (in decimal).
- p2text(optional): string
  Description of the second wait event parameter.
- p3(optional): integer
  Third wait event parameter (in decimal).
- p3text(optional): string
  Description of the third wait event parameter.
- seq#(optional): integer
  Sequence of wait events; 1 is the most recent.
- sid(optional): integer
  Session identifier.
- time_since_last_wait_micro(optional): integer
  Time elapsed (in microseconds) since the end of the previous wait in the wait history.
- username(optional): string
  Name of the user that is associated with the session.
- wait_time(optional): integer
  Amount of time waited (in hundredths of a second).
- wait_time_micro(optional): integer
  Amount of time waited (in microseconds).

<!-- -->

    {
        "type":"object",
        "description":"Describes a wait event for a session. Data corresponds to a record from GV$SESSION_WAIT_HISTORY. The list of attributes may vary depending on database version.",
        "properties":{
            "username":{
                "type":"string",
                "description":"Name of the user that is associated with the session."
            },
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated V$ view information was obtained."
            },
            "sid":{
                "type":"integer",
                "description":"Session identifier."
            },
            "seq#":{
                "type":"integer",
                "description":"Sequence of wait events; 1 is the most recent."
            },
            "event#":{
                "type":"integer",
                "description":"Event number."
            },
            "event":{
                "type":"string",
                "description":"Resource or event for which the session is waiting."
            },
            "p1text":{
                "type":"string",
                "description":"Description of the first wait event parameter."
            },
            "p1":{
                "type":"integer",
                "description":"First wait event parameter (in decimal)."
            },
            "p2text":{
                "type":"string",
                "description":"Description of the second wait event parameter."
            },
            "p2":{
                "type":"integer",
                "description":"Second wait event parameter (in decimal)."
            },
            "p3text":{
                "type":"string",
                "description":"Description of the third wait event parameter."
            },
            "p3":{
                "type":"integer",
                "description":"Third wait event parameter (in decimal)."
            },
            "wait_time":{
                "type":"integer",
                "description":"Amount of time waited (in hundredths of a second)."
            },
            "wait_time_micro":{
                "type":"integer",
                "description":"Amount of time waited (in microseconds)."
            },
            "time_since_last_wait_micro":{
                "type":"integer",
                "description":"Time elapsed (in microseconds) since the end of the previous wait in the wait history."
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
