Get all locks that are held in the database using DBA_LOCK view. A client requires SQL Administrator role to invoke this service.

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

All locks held in the database.

Body ()

Root Schema : MonitoringSessionLocks

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
                    "$ref":"#/definitions/MonitoringSessionLocksItem"
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

- Array of: object MonitoringSessionLocksItem
  This object is represents a record on DBA_LOCK view. DBA_LOCK lists all locks or latches held in the database, and all outstanding requests for a lock or latch. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/MonitoringSessionLocksItem"
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

Nested Schema : MonitoringSessionLocksItem

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
