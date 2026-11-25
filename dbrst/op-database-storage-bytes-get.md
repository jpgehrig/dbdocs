Returns info on bytes allocated for storage and how much is used. Using DBA_DATA_FILES data to calculate the total bytes allocated for storage along with DBA_TABLESPACE_USAGE_METRICS and DBA_TABLESPACES data to calculate the used bytes. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Total bytes across all the data files and how much is used.

Body ()

Root Schema : DatabaseStorageBytesItem

Type: `object`

Total size of data files in the database and their total usage.

Show Source

- links(optional): array links
- total_bytes(optional): integer
  Total size (in bytes) of all the data files in the database.
- used_bytes(optional): integer
  Total number of bytes used by all the tablespaces in the database.

<!-- -->

    {
        "type":"object",
        "description":"Total size of data files in the database and their total usage.",
        "properties":{
            "total_bytes":{
                "type":"integer",
                "description":"Total size (in bytes) of all the data files in the database."
            },
            "used_bytes":{
                "type":"integer",
                "description":"Total number of bytes used by all the tablespaces in the database."
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
