Returns all database Oracle Homes that are on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of all database Oracle Homes available.

Body ()

Root Schema : EnvironmentHomes

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
                    "$ref":"#/definitions/EnvironmentHomesItem"
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

- Array of: object EnvironmentHomesItem
  An Oracle home is a directory into which Oracle software is installed.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/EnvironmentHomesItem"
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

Nested Schema : EnvironmentHomesItem

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
