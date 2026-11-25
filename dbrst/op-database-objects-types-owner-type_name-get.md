Describes a specific object type in the database. Uses DBA_TYPES or ALL_TYPES view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- owner: string
  Owner of the type.
- type_name: string
  Name of the type.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific object type.

Body ()

Root Schema : DatabaseObjectsTypesItem

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
