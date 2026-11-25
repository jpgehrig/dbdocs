Returns information about the specified component loaded into the database from DBA_REGISTRY view. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- comp_id: string
  Identifier of the component.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information about the specified component.

Body ()

Root Schema : DatabaseComponentsItem

Type: `object`

A component registered in the database.

Show Source

- comp_id(optional): string
  Component identifier.
- comp_name(optional): string
  Component name.
- control(optional): string
  User that created the component entry.
- links(optional): array links
- modified(optional): string
  Time when the component was last modified.
- namespace(optional): string
  Component namespace.
- other_schemas(optional): string
  A list of ancillary schema names associated with the component.
- parent_id(optional): string
  Parent component identifier.
- procedure(optional): string
  Validation procedure.
- schema(optional): string
  User that contains the objects for the component.
- startup(optional): string
  Indicates whether the component requires a startup after the upgrade (REQUIRED) or not.
- status(optional): string
  Component status.
- version(optional): string
  Component version loaded.
- version_full(optional): string
  Component full version.

<!-- -->

    {
        "type":"object",
        "description":"A component registered in the database.",
        "properties":{
            "comp_id":{
                "type":"string",
                "description":"Component identifier."
            },
            "comp_name":{
                "type":"string",
                "description":"Component name."
            },
            "version":{
                "type":"string",
                "description":"Component version loaded."
            },
            "version_full":{
                "type":"string",
                "description":"Component full version."
            },
            "status":{
                "type":"string",
                "description":"Component status."
            },
            "modified":{
                "type":"string",
                "description":"Time when the component was last modified."
            },
            "namespace":{
                "type":"string",
                "description":"Component namespace."
            },
            "control":{
                "type":"string",
                "description":"User that created the component entry."
            },
            "schema":{
                "type":"string",
                "description":"User that contains the objects for the component."
            },
            "procedure":{
                "type":"string",
                "description":"Validation procedure."
            },
            "startup":{
                "type":"string",
                "description":"Indicates whether the component requires a startup after the upgrade (REQUIRED) or not."
            },
            "parent_id":{
                "type":"string",
                "description":"Parent component identifier."
            },
            "other_schemas":{
                "type":"string",
                "description":"A list of ancillary schema names associated with the component."
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
