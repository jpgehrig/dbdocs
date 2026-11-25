Returns all GV\$SQL_PLAN records for a specified SQL_ID. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- sql_id: string
  SQL identifier.

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

Execution plan for the specified SQL statement.

Body ()

Root Schema : PerformanceSQLStatementPlanItem

Type: `object`

Describes the explain plan for an SQL Statement.

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
        "description":"Describes the explain plan for an SQL Statement.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "id":{
                            "type":"integer",
                            "description":"A number assigned to each step in the execution plan."
                        },
                        "depth":{
                            "type":"integer",
                            "description":"Depth (or level) of the operation in the tree. The root operation (statement) is level 0."
                        },
                        "operation":{
                            "type":"string",
                            "description":"Name of the internal operation performed in this step (for example, TABLE ACCESS)."
                        },
                        "rows":{
                            "type":"string",
                            "description":"The number of rows the optimizer is expecting the operation to produce each time it is called. Also known as E-Rows."
                        },
                        "rowsourcetimes":{
                            "type":"integer",
                            "description":"The number of times the SQL Statement is referenced in GV$ACTIVE_SESSION_HISTORY."
                        }
                    }
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

- Array of: object items

<!-- -->

    {
        "type":"array",
        "items":{
            "type":"object",
            "properties":{
                "id":{
                    "type":"integer",
                    "description":"A number assigned to each step in the execution plan."
                },
                "depth":{
                    "type":"integer",
                    "description":"Depth (or level) of the operation in the tree. The root operation (statement) is level 0."
                },
                "operation":{
                    "type":"string",
                    "description":"Name of the internal operation performed in this step (for example, TABLE ACCESS)."
                },
                "rows":{
                    "type":"string",
                    "description":"The number of rows the optimizer is expecting the operation to produce each time it is called. Also known as E-Rows."
                },
                "rowsourcetimes":{
                    "type":"integer",
                    "description":"The number of times the SQL Statement is referenced in GV$ACTIVE_SESSION_HISTORY."
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

- depth(optional): integer
  Depth (or level) of the operation in the tree. The root operation (statement) is level 0.
- id(optional): integer
  A number assigned to each step in the execution plan.
- operation(optional): string
  Name of the internal operation performed in this step (for example, TABLE ACCESS).
- rows(optional): string
  The number of rows the optimizer is expecting the operation to produce each time it is called. Also known as E-Rows.
- rowsourcetimes(optional): integer
  The number of times the SQL Statement is referenced in GV\$ACTIVE_SESSION_HISTORY.

<!-- -->

    {
        "type":"object",
        "properties":{
            "id":{
                "type":"integer",
                "description":"A number assigned to each step in the execution plan."
            },
            "depth":{
                "type":"integer",
                "description":"Depth (or level) of the operation in the tree. The root operation (statement) is level 0."
            },
            "operation":{
                "type":"string",
                "description":"Name of the internal operation performed in this step (for example, TABLE ACCESS)."
            },
            "rows":{
                "type":"string",
                "description":"The number of rows the optimizer is expecting the operation to produce each time it is called. Also known as E-Rows."
            },
            "rowsourcetimes":{
                "type":"integer",
                "description":"The number of times the SQL Statement is referenced in GV$ACTIVE_SESSION_HISTORY."
            }
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
