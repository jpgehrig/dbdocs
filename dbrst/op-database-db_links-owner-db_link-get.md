Describes a database link in the database. Uses DBA_DB_LINKS or ALL_DB_LINKS view depending on the role access at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- db_link: string
  Name of the database link.
- owner: string
  Owner for the database link.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on the specific database link.

Body ()

Root Schema : DatabaseLinksItem

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
