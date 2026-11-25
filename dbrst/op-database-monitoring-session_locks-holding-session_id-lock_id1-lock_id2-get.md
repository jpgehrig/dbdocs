Using DBA_LOCKS and DBA_BLOCKERS views, this service returns a specific DBA_LOCKS record where the session is not waiting for a locked object but is holding a lock on an object for which another session is waiting. In an Oracle RAC environment, this only applies if the blocker is on the same instance. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- lock_id1: string
  Type-specific lock identifier, part 1.
- lock_id2: string
  Type-specific lock identifier, part 2.
- session_id: number
  Session identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific session lock.

Body ()

Root Schema : MonitoringSessionLocksItem

Type: `object`

This object is represents a record on DBA_LOCK view. DBA_LOCK lists all locks or latches held in the database, and all outstanding requests for a lock or latch. The list of attributes may vary depending on database version.

Show Source

- blocking_others(optional): string
  Whether the lock is currently blocking others.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- last_convert(optional): integer
  The last convert.
- links(optional): array links
- lock_id1(optional): string
  Type-specific lock identifier, part 1.
- lock_id2(optional): string
  Type-specific lock identifier, part 2.
- lock_type(optional): string
  Lock type.
- mode_held(optional): string
  Lock mode.
- mode_requested(optional): string
  Lock mode requested.
- session_id(optional): integer
  Session holding or acquiring the lock.

<!-- -->

    {
        "type":"object",
        "description":"This object is represents a record on DBA_LOCK view. DBA_LOCK lists all locks or latches held in the database, and all outstanding requests for a lock or latch. The list of attributes may vary depending on database version.",
        "properties":{
            "session_id":{
                "type":"integer",
                "description":"Session holding or acquiring the lock."
            },
            "lock_type":{
                "type":"string",
                "description":"Lock type."
            },
            "mode_held":{
                "type":"string",
                "description":"Lock mode."
            },
            "mode_requested":{
                "type":"string",
                "description":"Lock mode requested."
            },
            "lock_id1":{
                "type":"string",
                "description":"Type-specific lock identifier, part 1."
            },
            "lock_id2":{
                "type":"string",
                "description":"Type-specific lock identifier, part 2."
            },
            "last_convert":{
                "type":"integer",
                "description":"The last convert."
            },
            "blocking_others":{
                "type":"string",
                "description":"Whether the lock is currently blocking others."
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
