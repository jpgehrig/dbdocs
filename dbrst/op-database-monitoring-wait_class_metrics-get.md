Returns all records from GV\$WAITCLASSMETRIC for all GV\$SYSTEM_WAIT_CLASS records except 'Idle' wait class. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Wait class metrics records.

Body ()

Root Schema : MonitoringWaitClassMetricsItem

Type: `object`

This object combines data from GV\$WAITCLASSMETRIC and GV\$SYSTEM_WAIT_CLASS views to represent metric values of wait classes for the most recent 60-second interval.

Show Source

- items(optional): array items
- links(optional): array links

<!-- -->

    {
        "type":"object",
        "description":"This object combines data from GV$WAITCLASSMETRIC and GV$SYSTEM_WAIT_CLASS views to represent metric values of wait classes for the most recent 60-second interval.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "begin_time":{
                            "type":"string",
                            "description":"Begin time of the interval."
                        },
                        "end_time":{
                            "type":"string",
                            "description":"End time of the interval."
                        },
                        "intsize_csec":{
                            "type":"integer",
                            "description":"Interval size (in hundredths of a second)."
                        },
                        "average_waiter_count":{
                            "type":"integer",
                            "description":"Average waiter count."
                        },
                        "dbtime_in_wait":{
                            "type":"integer",
                            "description":"Percent of database time spent in the wait."
                        },
                        "wait_count":{
                            "type":"integer",
                            "description":"Number of times waited."
                        },
                        "wait_count_fg":{
                            "type":"integer",
                            "description":"Number of times foreground processes waited."
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
                "begin_time":{
                    "type":"string",
                    "description":"Begin time of the interval."
                },
                "end_time":{
                    "type":"string",
                    "description":"End time of the interval."
                },
                "intsize_csec":{
                    "type":"integer",
                    "description":"Interval size (in hundredths of a second)."
                },
                "average_waiter_count":{
                    "type":"integer",
                    "description":"Average waiter count."
                },
                "dbtime_in_wait":{
                    "type":"integer",
                    "description":"Percent of database time spent in the wait."
                },
                "wait_count":{
                    "type":"integer",
                    "description":"Number of times waited."
                },
                "wait_count_fg":{
                    "type":"integer",
                    "description":"Number of times foreground processes waited."
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

- average_waiter_count(optional): integer
  Average waiter count.
- begin_time(optional): string
  Begin time of the interval.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- dbtime_in_wait(optional): integer
  Percent of database time spent in the wait.
- end_time(optional): string
  End time of the interval.
- intsize_csec(optional): integer
  Interval size (in hundredths of a second).
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
- wait_count(optional): integer
  Number of times waited.
- wait_count_fg(optional): integer
  Number of times foreground processes waited.

<!-- -->

    {
        "type":"object",
        "properties":{
            "begin_time":{
                "type":"string",
                "description":"Begin time of the interval."
            },
            "end_time":{
                "type":"string",
                "description":"End time of the interval."
            },
            "intsize_csec":{
                "type":"integer",
                "description":"Interval size (in hundredths of a second)."
            },
            "average_waiter_count":{
                "type":"integer",
                "description":"Average waiter count."
            },
            "dbtime_in_wait":{
                "type":"integer",
                "description":"Percent of database time spent in the wait."
            },
            "wait_count":{
                "type":"integer",
                "description":"Number of times waited."
            },
            "wait_count_fg":{
                "type":"integer",
                "description":"Number of times foreground processes waited."
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
