Returns information about the components loaded into the database from DBA_REGISTRY view. A client requires SQL Administrator role to invoke this service.

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

All database components loaded into the database.

Body ()

Root Schema : DatabaseComponents

Type: `object`

DBA_REGISTRY displays information about all components in the database that are loaded into the component registry. The component registry tracks components that can be separately loaded into the Oracle Database. When a SQL script loads the PL/SQL packages and other database objects for a component into the database, the script records the component name, status, and version. If scripts are used to upgrade/downgrade the dictionary elements for the component, then those scripts also record status and version information.

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
        "description":"DBA_REGISTRY displays information about all components in the database that are loaded into the component registry. The component registry tracks components that can be separately loaded into the Oracle Database. When a SQL script loads the PL/SQL packages and other database objects for a component into the database, the script records the component name, status, and version. If scripts are used to upgrade/downgrade the dictionary elements for the component, then those scripts also record status and version information.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/DatabaseComponentsItem"
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

- Array of: object DatabaseComponentsItem
  A component registered in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseComponentsItem"
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

Nested Schema : DatabaseComponentsItem

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
