Returns records where OBJECT_TYPE = 'FUNCTION' from DBA_PROCEDURES or ALL_PROCEDURES view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

Description of all functions in the database.

Body ()

Root Schema : DatabaseObjectsFunctions

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
                    "$ref":"#/definitions/DatabaseObjectsFunctionsItem"
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

- Array of: object DatabaseObjectsFunctionsItem
  Describes a function available in the database, along with associated properties. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsFunctionsItem"
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

Nested Schema : DatabaseObjectsFunctionsItem

Type: `object`

Describes a function available in the database, along with associated properties. The list of attributes may vary depending on database version.

Show Source

- aggregate(optional): string
  Indicates whether the procedure is an aggregate function (YES) or not (NO).
- authid(optional): string
  Indicates whether the procedure/function is declared to execute as DEFINER or CURRENT_USER (invoker).
- deterministic(optional): string
  YES, if the procedure/function is declared to be deterministic; otherwise NO.
- impltypename(optional): string
  Name of the implementation type, if any.
- impltypeowner(optional): string
  Owner of the implementation type, if any.
- interface(optional): string
  YES, if the procedure/function is a table function implemented using the ODCI interface; otherwise NO.
- links(optional): array links
- object_id(optional): integer
  Object number of the object.
- object_name(optional): string
  Name of the top-level function.
- object_type(optional): string
  The typename of the object.
- origin_con_id(optional): integer
  The ID of the container where the data originates.
- overload(optional): string
  Overload unique identifier.
- owner(optional): string
  Owner of the function.
- parallel(optional): string
  Indicates whether the procedure or function is parallel-enabled (YES) or not (NO).
- pipelined(optional): string
  Indicates whether the procedure is a pipelined table function (YES) or not (NO).
- polymorphic(optional): string
  The type of polymorphic table function.
- procedure_name(optional): string
  Name of the procedure.
- result_cache(optional): string
  Indicates whether the function is result???cached (YES) or not (NO).
- subprogram_id(optional): integer
  Unique subprogram identifier.

<!-- -->

    {
        "type":"object",
        "description":"Describes a function available in the database, along with associated properties. The list of attributes may vary depending on database version.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the function."
            },
            "object_name":{
                "type":"string",
                "description":"Name of the top-level function."
            },
            "procedure_name":{
                "type":"string",
                "description":"Name of the procedure."
            },
            "object_id":{
                "type":"integer",
                "description":"Object number of the object."
            },
            "subprogram_id":{
                "type":"integer",
                "description":"Unique subprogram identifier."
            },
            "overload":{
                "type":"string",
                "description":"Overload unique identifier."
            },
            "object_type":{
                "type":"string",
                "description":"The typename of the object."
            },
            "aggregate":{
                "type":"string",
                "description":"Indicates whether the procedure is an aggregate function (YES) or not (NO)."
            },
            "pipelined":{
                "type":"string",
                "description":"Indicates whether the procedure is a pipelined table function (YES) or not (NO)."
            },
            "impltypeowner":{
                "type":"string",
                "description":"Owner of the implementation type, if any."
            },
            "impltypename":{
                "type":"string",
                "description":"Name of the implementation type, if any."
            },
            "parallel":{
                "type":"string",
                "description":"Indicates whether the procedure or function is parallel-enabled (YES) or not (NO)."
            },
            "interface":{
                "type":"string",
                "description":"YES, if the procedure/function is a table function implemented using the ODCI interface; otherwise NO."
            },
            "deterministic":{
                "type":"string",
                "description":"YES, if the procedure/function is declared to be deterministic; otherwise NO."
            },
            "authid":{
                "type":"string",
                "description":"Indicates whether the procedure/function is declared to execute as DEFINER or CURRENT_USER (invoker)."
            },
            "result_cache":{
                "type":"string",
                "description":"Indicates whether the function is result???cached (YES) or not (NO)."
            },
            "origin_con_id":{
                "type":"integer",
                "description":"The ID of the container where the data originates."
            },
            "polymorphic":{
                "type":"string",
                "description":"The type of polymorphic table function."
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
