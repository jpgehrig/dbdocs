Returns records from GV\$SQL for specified SQL_ID. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- sql_id: string
  SQL identifier.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

The text of a specific SQL statement.

Body ()

Root Schema : PerformanceSQLStatementTextItem

Type: `object`

Describes the SQL Statement.

Show Source

- links(optional): array links
- sql_fulltext(optional): string
  Full text for the SQL statement.
- sql_text(optional): string
  First thousand characters of the SQL text for the current cursor.

<!-- -->

    {
        "type":"object",
        "description":"Describes the SQL Statement.",
        "properties":{
            "sql_text":{
                "type":"string",
                "description":"First thousand characters of the SQL text for the current cursor."
            },
            "sql_fulltext":{
                "type":"string",
                "description":"Full text for the SQL statement."
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
