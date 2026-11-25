Returns records from DBA_TEMP_FILES for a specific tablespace. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- tablespace_name: string
  Name of the tablespace.

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

Description of all temporary files used by the specified tablespace.

Body ()

Root Schema : DatabaseTablespaceTempfiles

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
                    "$ref":"#/definitions/DatabaseTablespaceTempfilesItem"
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

- Array of: object DatabaseTablespaceTempfilesItem
  Describes a temporary file in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseTablespaceTempfilesItem"
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

Nested Schema : DatabaseTablespaceTempfilesItem

Type: `object`

Describes a temporary file in the database.

Show Source

- autoextensible(optional): string
  Indicates whether the file is autoextensible (YES) or not (NO).
- blocks(optional): integer
  Size of the file (in Oracle blocks).
- bytes(optional): integer
  Size of the file (in bytes).
- file_id(optional): integer
  File identifier number of the database temp file.
- file_name(optional): string
  Name of the database file.
- increment_by(optional): integer
  Default increment for autoextension (in Oracle blocks).
- inst_id(optional): integer
  Instance ID of the instance to which the temp file belongs. This column has a NULL value for temp files that belong to shared tablespaces.
- links(optional): array links
- maxblocks(optional): integer
  Maximum size of the file (in Oracle blocks).
- maxbytes(optional): integer
  Maximum size of the file (in bytes).
- relative_fno(optional): integer
  Tablespace-relative file number.
- shared(optional): string
  Type of tablespace this file belongs to.
- status(optional): string
  File status.
- tablespace_name(optional): string
  Name of the tablespace.
- user_blocks(optional): integer
  Size of the useful portion of the file (in Oracle blocks).
- user_bytes(optional): integer
  The size of the file available for user data. The actual size of the file minus the USER_BYTES value is used to store file related metadata.

<!-- -->

    {
        "type":"object",
        "description":"Describes a temporary file in the database.",
        "properties":{
            "file_name":{
                "type":"string",
                "description":"Name of the database file."
            },
            "file_id":{
                "type":"integer",
                "description":"File identifier number of the database temp file."
            },
            "tablespace_name":{
                "type":"string",
                "description":"Name of the tablespace."
            },
            "bytes":{
                "type":"integer",
                "description":"Size of the file (in bytes)."
            },
            "blocks":{
                "type":"integer",
                "description":"Size of the file (in Oracle blocks)."
            },
            "status":{
                "type":"string",
                "description":"File status."
            },
            "relative_fno":{
                "type":"integer",
                "description":"Tablespace-relative file number."
            },
            "autoextensible":{
                "type":"string",
                "description":"Indicates whether the file is autoextensible (YES) or not (NO)."
            },
            "maxbytes":{
                "type":"integer",
                "description":"Maximum size of the file (in bytes)."
            },
            "maxblocks":{
                "type":"integer",
                "description":"Maximum size of the file (in Oracle blocks)."
            },
            "increment_by":{
                "type":"integer",
                "description":"Default increment for autoextension (in Oracle blocks)."
            },
            "user_bytes":{
                "type":"integer",
                "description":"The size of the file available for user data. The actual size of the file minus the USER_BYTES value is used to store file related metadata."
            },
            "user_blocks":{
                "type":"integer",
                "description":"Size of the useful portion of the file (in Oracle blocks)."
            },
            "shared":{
                "type":"string",
                "description":"Type of tablespace this file belongs to."
            },
            "inst_id":{
                "type":"integer",
                "description":"Instance ID of the instance to which the temp file belongs. This column has a NULL value for temp files that belong to shared tablespaces."
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
