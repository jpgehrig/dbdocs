Oracle Diagnostics Pack licence is required for this service. Group by sample_time and wait_class on GV\$ACTIVE_SESSION_HISTORY for records with sample_time within the last 7 days. Note that time waited is in microseconds. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Wait time summary from active session history records within the last 7 days.

Body ()

Root Schema : MonitoringWaitsRecentItem

Type: `object`

A summary of time waited for each wait class in GV\$ACTIVE_SESSION_HISTORY.

Show Source

- items(optional): array items
- links(optional): array links

<!-- -->

    {
        "type":"object",
        "description":"A summary of time waited for each wait class in GV$ACTIVE_SESSION_HISTORY.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "sample_time":{
                            "type":"string",
                            "description":"Time at which the sample was taken."
                        },
                        "wait_class":{
                            "type":"string",
                            "description":"Wait class name of the event for which the session was waiting at the time of sampling."
                        },
                        "time_waited":{
                            "type":"integer",
                            "description":"Amount of time (in microseconds) spent in waits from this wait class at the time of sampling."
                        }
                    }
                }
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
                "sample_time":{
                    "type":"string",
                    "description":"Time at which the sample was taken."
                },
                "wait_class":{
                    "type":"string",
                    "description":"Wait class name of the event for which the session was waiting at the time of sampling."
                },
                "time_waited":{
                    "type":"integer",
                    "description":"Amount of time (in microseconds) spent in waits from this wait class at the time of sampling."
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

- sample_time(optional): string
  Time at which the sample was taken.
- time_waited(optional): integer
  Amount of time (in microseconds) spent in waits from this wait class at the time of sampling.
- wait_class(optional): string
  Wait class name of the event for which the session was waiting at the time of sampling.

<!-- -->

    {
        "type":"object",
        "properties":{
            "sample_time":{
                "type":"string",
                "description":"Time at which the sample was taken."
            },
            "wait_class":{
                "type":"string",
                "description":"Wait class name of the event for which the session was waiting at the time of sampling."
            },
            "time_waited":{
                "type":"integer",
                "description":"Amount of time (in microseconds) spent in waits from this wait class at the time of sampling."
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
