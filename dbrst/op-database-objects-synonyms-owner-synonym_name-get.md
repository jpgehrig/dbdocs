Returns a record from DBA_SYNONYMS or ALL_SYNONYMS view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- owner: string
  Owner of the synonym.
- synonym_name: string
  Name of the synonym.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific synonym.

Body ()

Root Schema : DatabaseObjectsSynonymsItem

Type: `object`

This object describes a synonym in the database. The list of attributes may vary depending on database version.

Show Source

- db_link(optional): string
  Name of the database link referenced, if any.
- links(optional): array links
- origin_con_id(optional): integer
  The ID of the container where the data originates.
- owner(optional): string
  Owner of the synonym.
- synonym_name(optional): string
  Name of the synonym.
- table_name(optional): string
  Name of the object referenced by the synonym. Although the column is called TABLE_NAME, the object does not necessarily have to be a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on.
- table_owner(optional): string
  Owner of the object referenced by the synonym, or creator of the referring synonym if the target is a public synonym (that is, the object referred to by TABLE_NAME). Although the column is called TABLE_OWNER, the object owned is not necessarily a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on.

<!-- -->

    {
        "type":"object",
        "description":"This object describes a synonym in the database. The list of attributes may vary depending on database version.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the synonym."
            },
            "synonym_name":{
                "type":"string",
                "description":"Name of the synonym."
            },
            "table_owner":{
                "type":"string",
                "description":"Owner of the object referenced by the synonym, or creator of the referring synonym if the target is a public synonym (that is, the object referred to by TABLE_NAME). Although the column is called TABLE_OWNER, the object owned is not necessarily a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on."
            },
            "table_name":{
                "type":"string",
                "description":"Name of the object referenced by the synonym. Although the column is called TABLE_NAME, the object does not necessarily have to be a table. It can be any general object such as a view, sequence, stored procedure, synonym, and so on."
            },
            "db_link":{
                "type":"string",
                "description":"Name of the database link referenced, if any."
            },
            "origin_con_id":{
                "type":"integer",
                "description":"The ID of the container where the data originates."
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
