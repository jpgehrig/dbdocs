Returns all records on DBA_SYNONYMS or ALL_SYNONYMS view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

Describes, using DBA_SYNONYMS or ALL_SYNONYMS view, all synonyms in the database.

Body ()

Root Schema : DatabaseObjectsSynonyms

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
                    "$ref":"#/definitions/DatabaseObjectsSynonymsItem"
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

- Array of: object DatabaseObjectsSynonymsItem
  This object describes a synonym in the database. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsSynonymsItem"
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

Nested Schema : DatabaseObjectsSynonymsItem

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
