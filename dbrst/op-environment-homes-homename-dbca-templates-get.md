Returns a description of all database templates specified in the Oracle Home. The Oracle Home is on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

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

Description of all database templates defined in the Oracle Home.

Body ()

Root Schema : EnvironmentDbcaTemplates

Type: `object`

Represents a list of the DBCA Database Templates in the Oracle Home.

Show Source

- items(optional): array items
- links(optional): array links

<!-- -->

    {
        "type":"object",
        "description":"Represents a list of the DBCA Database Templates in the Oracle Home.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "filename":{
                            "type":"string",
                            "description":"Name of the template file."
                        },
                        "size":{
                            "type":"integer",
                            "description":"Size (in bytes) of the template file."
                        },
                        "updated":{
                            "type":"string",
                            "description":"The last update date of the template file."
                        },
                        "links":{
                            "type":"array",
                            "items":{
                                "$ref":"#/definitions/LinkRelation"
                            }
                        }
                    }
                }
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

- Array of: object items

<!-- -->

    {
        "type":"array",
        "items":{
            "type":"object",
            "properties":{
                "filename":{
                    "type":"string",
                    "description":"Name of the template file."
                },
                "size":{
                    "type":"integer",
                    "description":"Size (in bytes) of the template file."
                },
                "updated":{
                    "type":"string",
                    "description":"The last update date of the template file."
                },
                "links":{
                    "type":"array",
                    "items":{
                        "$ref":"#/definitions/LinkRelation"
                    }
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

Nested Schema : items

Type: `object`

Show Source

- filename(optional): string
  Name of the template file.
- links(optional): array links
- size(optional): integer
  Size (in bytes) of the template file.
- updated(optional): string
  The last update date of the template file.

<!-- -->

    {
        "type":"object",
        "properties":{
            "filename":{
                "type":"string",
                "description":"Name of the template file."
            },
            "size":{
                "type":"integer",
                "description":"Size (in bytes) of the template file."
            },
            "updated":{
                "type":"string",
                "description":"The last update date of the template file."
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
