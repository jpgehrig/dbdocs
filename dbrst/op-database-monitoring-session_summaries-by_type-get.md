Group by session type on GV\$SESSION. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Summary of different session types in the database.

Body ()

Root Schema : MonitoringSessionTypeSummariesItem

Type: `object`

Using data from GV\$SESSION this object represents a summary of the number of sessions in different states aggregated across different session types (BACKGROUND and USER).

Show Source

- items(optional): array items
- links(optional): array links

<!-- -->

    {
        "type":"object",
        "description":"Using data from GV$SESSION this object represents a summary of the number of sessions in different states aggregated across different session types (BACKGROUND and USER).",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "inst_id":{
                            "type":"integer",
                            "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
                        },
                        "type":{
                            "type":"string",
                            "description":"Session type."
                        },
                        "number_of_sessions":{
                            "type":"integer",
                            "description":"Total number of sessions of this type."
                        },
                        "number_of_active_sessions":{
                            "type":"integer",
                            "description":"Total number of active sessions of this type."
                        },
                        "number_of_inactive_sessions":{
                            "type":"integer",
                            "description":"Total number of inactive sessions of this type."
                        },
                        "number_of_active_blocking_sess":{
                            "type":"integer",
                            "description":"Total number of active blocking sessions of this type."
                        },
                        "number_of_act_non_blocking_ses":{
                            "type":"integer",
                            "description":"Total number of active non-blocking sessions of this type."
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
                "inst_id":{
                    "type":"integer",
                    "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
                },
                "type":{
                    "type":"string",
                    "description":"Session type."
                },
                "number_of_sessions":{
                    "type":"integer",
                    "description":"Total number of sessions of this type."
                },
                "number_of_active_sessions":{
                    "type":"integer",
                    "description":"Total number of active sessions of this type."
                },
                "number_of_inactive_sessions":{
                    "type":"integer",
                    "description":"Total number of inactive sessions of this type."
                },
                "number_of_active_blocking_sess":{
                    "type":"integer",
                    "description":"Total number of active blocking sessions of this type."
                },
                "number_of_act_non_blocking_ses":{
                    "type":"integer",
                    "description":"Total number of active non-blocking sessions of this type."
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

- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- number_of_act_non_blocking_ses(optional): integer
  Total number of active non-blocking sessions of this type.
- number_of_active_blocking_sess(optional): integer
  Total number of active blocking sessions of this type.
- number_of_active_sessions(optional): integer
  Total number of active sessions of this type.
- number_of_inactive_sessions(optional): integer
  Total number of inactive sessions of this type.
- number_of_sessions(optional): integer
  Total number of sessions of this type.
- type(optional): string
  Session type.

<!-- -->

    {
        "type":"object",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "type":{
                "type":"string",
                "description":"Session type."
            },
            "number_of_sessions":{
                "type":"integer",
                "description":"Total number of sessions of this type."
            },
            "number_of_active_sessions":{
                "type":"integer",
                "description":"Total number of active sessions of this type."
            },
            "number_of_inactive_sessions":{
                "type":"integer",
                "description":"Total number of inactive sessions of this type."
            },
            "number_of_active_blocking_sess":{
                "type":"integer",
                "description":"Total number of active blocking sessions of this type."
            },
            "number_of_act_non_blocking_ses":{
                "type":"integer",
                "description":"Total number of active non-blocking sessions of this type."
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
