Returns GV\$DATAFILE and DBA_DATA_FILES records for a specific tablespace. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- tablespace_name: string
  Name of the tablespace.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Tablespace data file usage.

Body ()

Root Schema : DatabaseTablespaceDatafilesUsageItem

Type: `object`

Using GV\$DATAFILE and DBA_FREE_SPACE data this object represents the usage of a data file in the database.

Show Source

- items(optional): array items
- links(optional): array links

<!-- -->

    {
        "type":"object",
        "description":"Using GV$DATAFILE and DBA_FREE_SPACE data this object represents the usage of a data file in the database.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "type":"object",
                    "properties":{
                        "file_name":{
                            "type":"string",
                            "description":"Name of the database file."
                        },
                        "tablespace":{
                            "type":"string",
                            "description":"Name of the tablespace."
                        },
                        "status":{
                            "type":"string",
                            "description":"File status."
                        },
                        "total_space":{
                            "type":"integer",
                            "description":"Total size of the files (in bytes)."
                        },
                        "used_space":{
                            "type":"integer",
                            "description":"Total used space (in bytes)."
                        },
                        "used_space_pct":{
                            "type":"number",
                            "description":":Percentage of how much space is used."
                        },
                        "autoextend":{
                            "type":"string",
                            "description":"Indicates whether the file is autoextensible (YES) or not (NO)."
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
                "file_name":{
                    "type":"string",
                    "description":"Name of the database file."
                },
                "tablespace":{
                    "type":"string",
                    "description":"Name of the tablespace."
                },
                "status":{
                    "type":"string",
                    "description":"File status."
                },
                "total_space":{
                    "type":"integer",
                    "description":"Total size of the files (in bytes)."
                },
                "used_space":{
                    "type":"integer",
                    "description":"Total used space (in bytes)."
                },
                "used_space_pct":{
                    "type":"number",
                    "description":":Percentage of how much space is used."
                },
                "autoextend":{
                    "type":"string",
                    "description":"Indicates whether the file is autoextensible (YES) or not (NO)."
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

- autoextend(optional): string
  Indicates whether the file is autoextensible (YES) or not (NO).
- file_name(optional): string
  Name of the database file.
- status(optional): string
  File status.
- tablespace(optional): string
  Name of the tablespace.
- total_space(optional): integer
  Total size of the files (in bytes).
- used_space(optional): integer
  Total used space (in bytes).
- used_space_pct(optional): number
  :Percentage of how much space is used.

<!-- -->

    {
        "type":"object",
        "properties":{
            "file_name":{
                "type":"string",
                "description":"Name of the database file."
            },
            "tablespace":{
                "type":"string",
                "description":"Name of the tablespace."
            },
            "status":{
                "type":"string",
                "description":"File status."
            },
            "total_space":{
                "type":"integer",
                "description":"Total size of the files (in bytes)."
            },
            "used_space":{
                "type":"integer",
                "description":"Total used space (in bytes)."
            },
            "used_space_pct":{
                "type":"number",
                "description":":Percentage of how much space is used."
            },
            "autoextend":{
                "type":"string",
                "description":"Indicates whether the file is autoextensible (YES) or not (NO)."
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
