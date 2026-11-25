Returns a description of the database specified in the Oracle Home. The Oracle Home is on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- databaseName: string
  Name of the database.
- homeName: string
  Name of the Oracle Home.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of a database defined in the Oracle Home.

Body ()

Root Schema : EnvironmentDatabasesItem

Type: `object`

A database has a unique name within the context of the Oracle home it belongs to.

Show Source

- links(optional): array links
- name(optional): string
  The name of the database.
- type(optional): string
  The type of database. Either CDB or NON_CDB

<!-- -->

    {
        "type":"object",
        "description":"A database has a unique name within the context of the Oracle home it belongs to.",
        "properties":{
            "name":{
                "type":"string",
                "description":"The name of the database."
            },
            "type":{
                "type":"string",
                "description":"The type of database. Either CDB or NON_CDB"
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
