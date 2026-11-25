Describes all object types in the database. Uses DBA_TYPES or ALL_TYPES view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

Description of all object types in the database.

Body ()

Root Schema : DatabaseObjectsTypes

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
                    "$ref":"#/definitions/DatabaseObjectsTypesItem"
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

- Array of: object DatabaseObjectsTypesItem
  This object describes an object type in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsTypesItem"
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

Nested Schema : DatabaseObjectsTypesItem

Type: `object`

This object describes an object type in the database.

Show Source

- attributes(optional): integer
  Number of attributes (if any) in the type.
- final(optional): string
  Indicates whether the type is a final type (YES) or not (NO).
- incomplete(optional): string
  Indicates whether the type is an incomplete type (YES) or not (NO).
- instantiable(optional): string
  Indicates whether the type is an instantiable type (YES) or not (NO).
- links(optional): array links
- local_attributes(optional): integer
  Number of local (not inherited) attributes (if any) in the subtype.
- local_methods(optional): integer
  Number of local (not inherited) methods (if any) in the subtype.
- methods(optional): integer
  Number of methods (if any) in the type.
- owner(optional): string
  Owner of the type.
- persistable(optional): string
  Indicates whether the type is a persistable type (YES) or not (NO).
- predefined(optional): string
  Indicates whether the type is a predefined type (YES) or not (NO).
- supertype_name(optional): string
  Name of the supertype (NULL if type is not a subtype).
- supertype_owner(optional): string
  Owner of the supertype (NULL if type is not a subtype).
- type_name(optional): string
  Name of the type.
- type_oid(optional): string
  Object identifier (OID) of the type.
- typecode(optional): string
  Typecode of the type.
- typeid(optional): string
  Type ID value of the type.

<!-- -->

    {
        "type":"object",
        "description":"This object describes an object type in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the type."
            },
            "type_name":{
                "type":"string",
                "description":"Name of the type."
            },
            "type_oid":{
                "type":"string",
                "description":"Object identifier (OID) of the type."
            },
            "typecode":{
                "type":"string",
                "description":"Typecode of the type."
            },
            "attributes":{
                "type":"integer",
                "description":"Number of attributes (if any) in the type."
            },
            "methods":{
                "type":"integer",
                "description":"Number of methods (if any) in the type."
            },
            "predefined":{
                "type":"string",
                "description":"Indicates whether the type is a predefined type (YES) or not (NO)."
            },
            "incomplete":{
                "type":"string",
                "description":"Indicates whether the type is an incomplete type (YES) or not (NO)."
            },
            "final":{
                "type":"string",
                "description":"Indicates whether the type is a final type (YES) or not (NO)."
            },
            "instantiable":{
                "type":"string",
                "description":"Indicates whether the type is an instantiable type (YES) or not (NO)."
            },
            "persistable":{
                "type":"string",
                "description":"Indicates whether the type is a persistable type (YES) or not (NO)."
            },
            "supertype_owner":{
                "type":"string",
                "description":"Owner of the supertype (NULL if type is not a subtype)."
            },
            "supertype_name":{
                "type":"string",
                "description":"Name of the supertype (NULL if type is not a subtype)."
            },
            "local_attributes":{
                "type":"integer",
                "description":"Number of local (not inherited) attributes (if any) in the subtype."
            },
            "local_methods":{
                "type":"integer",
                "description":"Number of local (not inherited) methods (if any) in the subtype."
            },
            "typeid":{
                "type":"string",
                "description":"Type ID value of the type."
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
