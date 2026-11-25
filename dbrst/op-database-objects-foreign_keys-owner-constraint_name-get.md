Returns the corresponding record from DBA_CONSTRAINTS and DBA_CONS_COLUMNS, or ALL_CONSTRAINTS and ALL_CONS_COLUMNS, views depending on role at runtime. Recorded included in the response are where the constraint type is 'R'. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- constraint_name: string
  Name of the constraint for the foreign key.
- owner: string
  Owner for the foreign key.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific foreign key.

Body ()

Root Schema : DatabaseObjectsForeignKeysItem

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
