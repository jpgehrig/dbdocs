Returns data from DBA_TABLESPACES along with data usage information from DBA_TABLESPACE_USAGE_METRICS for a specific tablespace. A client requires SQL Administrator role to invoke this service.

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

Tablespace information, including data usage, is returned. The response structure may vary depending on the database.

Body ()

Root Schema : DatabaseTablespacesItem

Type: `object`

Describes a tablespace in the database.

Show Source

- autoextensible(optional): string
  Indicates whether the file is autoextensible (YES) or not (NO).
- blocks(optional): integer
  Size of the file (in Oracle blocks).
- bytes(optional): integer
  Size of the file (in bytes).
- file_id(optional): integer
  File identifier number of the database file.
- file_name(optional): string
  Name of the database file.
- free_space(optional): integer
  Total free space (in bytes).
- increment_by(optional): integer
  Default increment for autoextension (in Oracle blocks).
- links(optional): array links
- maxblocks(optional): integer
  Maximum size of the file (in Oracle blocks).
- maxbytes(optional): integer
  Maximum size of the file (in bytes).
- online_status(optional): string
  Online status of the file.
- relative_fno(optional): integer
  Tablespace-relative file number.
- status(optional): string
  File status.
- tablespace_name(optional): string
  Name of the tablespace.
- total_space(optional): integer
  Total size of the files (in bytes).
- used_space(optional): integer
  Total used space (in bytes).
- user_blocks(optional): integer
  Size of the useful portion of the file (in Oracle blocks).
- user_bytes(optional): integer
  The size of the file available for user data. The actual size of the file minus the USER_BYTES value is used to store file related metadata.

<!-- -->

    {
        "type":"object",
        "description":"Describes a tablespace in the database.",
        "properties":{
            "tablespace_name":{
                "type":"string",
                "description":"Name of the tablespace."
            },
            "file_name":{
                "type":"string",
                "description":"Name of the database file."
            },
            "file_id":{
                "type":"integer",
                "description":"File identifier number of the database file."
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
            "online_status":{
                "type":"string",
                "description":"Online status of the file."
            },
            "total_space":{
                "type":"integer",
                "description":"Total size of the files (in bytes)."
            },
            "used_space":{
                "type":"integer",
                "description":"Total used space (in bytes)."
            },
            "free_space":{
                "type":"integer",
                "description":"Total free space (in bytes)."
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
