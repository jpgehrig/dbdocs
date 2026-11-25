Returns status data from GV\$PDBS for the specified database in the corresponding Container Database. This service requires db.cdb.adminUser credentials to be set in the pool configuration. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- pdb_name: string
  Name of the Pluggable Database.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of a specific Pluggable Database.

Body ()

Root Schema : DatabasePluggableDatabaseStatusItem

Type: `object`

This object describes the status of a Pluggable Database.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- inst_id(optional): integer
  Instance number from which the associated GV\$PDBS view information was obtained.
- links(optional): array links
- name(optional): string
  Name of the PDB.
- open_mode(optional): string
  Open mode information.
- restricted(optional): string
  Indicates whether only users possessing RESTRICTED SESSION privilege can connect to the PDB.

<!-- -->

    {
        "type":"object",
        "description":"This object describes the status of a Pluggable Database.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$PDBS view information was obtained."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "name":{
                "type":"string",
                "description":"Name of the PDB."
            },
            "open_mode":{
                "type":"string",
                "description":"Open mode information."
            },
            "restricted":{
                "type":"string",
                "description":"Indicates whether only users possessing RESTRICTED SESSION privilege can connect to the PDB."
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
