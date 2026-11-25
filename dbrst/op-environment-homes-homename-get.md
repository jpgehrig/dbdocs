Returns a description for a specific Oracle Home on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- homeName: string
  Name of the Oracle Home.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of the Oracle Home.

Body ()

Root Schema : EnvironmentHomesItem

Type: `object`

An Oracle home is a directory into which Oracle software is installed.

Show Source

- default(optional): boolean
  Indicates if the Oracle home is specified by the \$ORACLE_HOME environment variable.
- links(optional): array links
- name(optional): string
  The name of the Oracle home.
- read_only_home(optional): boolean
  Indicates if the Oracle home is configured in read only mode.
- version(optional): string
  The product version.

<!-- -->

    {
        "type":"object",
        "description":"An Oracle home is a directory into which Oracle software is installed.",
        "properties":{
            "name":{
                "type":"string",
                "description":"The name of the Oracle home."
            },
            "version":{
                "type":"string",
                "description":"The product version."
            },
            "default":{
                "type":"boolean",
                "description":"Indicates if the Oracle home is specified by the $ORACLE_HOME environment variable."
            },
            "read_only_home":{
                "type":"boolean",
                "description":"Indicates if the Oracle home is configured in read only mode."
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
