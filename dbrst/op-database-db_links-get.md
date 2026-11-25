Describes all database links in the database. Uses DBA_DB_LINKS or ALL_DB_LINKS view depending on the role access at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

All database links in the database.

Body ()

Root Schema : DatabaseLinks

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
                    "$ref":"#/definitions/DatabaseLinksItem"
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

- Array of: object DatabaseLinksItem
  A database link is a connection between two physical database servers that allows a client to access them as one logical database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseLinksItem"
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

Nested Schema : DatabaseLinksItem

Type: `object`

A database link is a connection between two physical database servers that allows a client to access them as one logical database.

Show Source

- created(optional): string
  Creation time of the database link.
- db_link(optional): string
  Name of the database link.
- host(optional): string
  Oracle Net connect string.
- links(optional): array links
- owner(optional): string
  Owner of the database link.
- shard_internal(optional): string
  Indicates whether the database link is used to support operations across sharded databases.
- username(optional): string
  Name of the user when logging in.
- valid(optional): string
  Indicates whether the database link is valid and usable.

<!-- -->

    {
        "type":"object",
        "description":"A database link is a connection between two physical database servers that allows a client to access them as one logical database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the database link."
            },
            "db_link":{
                "type":"string",
                "description":"Name of the database link."
            },
            "username":{
                "type":"string",
                "description":"Name of the user when logging in."
            },
            "host":{
                "type":"string",
                "description":"Oracle Net connect string."
            },
            "created":{
                "type":"string",
                "description":"Creation time of the database link."
            },
            "shard_internal":{
                "type":"string",
                "description":"Indicates whether the database link is used to support operations across sharded databases."
            },
            "valid":{
                "type":"string",
                "description":"Indicates whether the database link is valid and usable."
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
