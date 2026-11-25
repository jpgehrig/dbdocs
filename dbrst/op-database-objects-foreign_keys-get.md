Returns all records where the constraint type is 'R' from DBA_CONSTRAINTS and DBA_CONS_COLUMNS, or ALL_CONSTRAINTS and ALL_CONS_COLUMNS, views depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

Describes all constraint definitions, with constraint type 'R', on all tables in the database.

Body ()

Root Schema : DatabaseObjectsForeignKeys

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
                    "$ref":"#/definitions/DatabaseObjectsForeignKeysItem"
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

- Array of: object DatabaseObjectsForeignKeysItem
  Describes a foreign key constraint for referential integrity.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsForeignKeysItem"
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

Nested Schema : DatabaseObjectsForeignKeysItem

Type: `object`

Describes a foreign key constraint for referential integrity.

Show Source

- column_name(optional): string
  Name of the column or attribute of the object type column specified in the constraint definition.
- constraint_name(optional): string
  Owner of the constraint definition.
- links(optional): array links
- owner(optional): string
  Owner of the constraint definition.
- position(optional): integer
  The position of the column_name and referenced r_column_name.
- r_column_name(optional): string
  Name of the column referred to in a referential constraint.
- r_owner(optional): string
  Owner of the table referred to in a referential constraint.
- r_table_name(optional): string
  Name of the table referred to in a referential constraint.
- table_name(optional): string
  Name associated with the table (or view) with the constraint definition.

<!-- -->

    {
        "type":"object",
        "description":"Describes a foreign key constraint for referential integrity.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the constraint definition."
            },
            "constraint_name":{
                "type":"string",
                "description":"Owner of the constraint definition."
            },
            "table_name":{
                "type":"string",
                "description":"Name associated with the table (or view) with the constraint definition."
            },
            "column_name":{
                "type":"string",
                "description":"Name of the column or attribute of the object type column specified in the constraint definition."
            },
            "r_owner":{
                "type":"string",
                "description":"Owner of the table referred to in a referential constraint."
            },
            "r_table_name":{
                "type":"string",
                "description":"Name of the table referred to in a referential constraint."
            },
            "r_column_name":{
                "type":"string",
                "description":"Name of the column referred to in a referential constraint."
            },
            "position":{
                "type":"integer",
                "description":"The position of the column_name and referenced r_column_name."
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
