Drop a pluggable database. This service requires db.cdb.adminUser credentials to be set in the pool configuration. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- pdb_name: string
  Name of the Pluggable Database.

Query Parameters

- action: string
  Specify if datafiles should be removed or not. The value can be INCLUDING or KEEP (default).
  Default Value: `KEEP`
  Allowed Values: `[ "KEEP", "INCLUDING" ]`
- getScript: boolean
  If defined, the response will contain a JSON object with the information of the script that was generated for execution. Script execution does not happen and the database is not dropped.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

The response will indicate the successful execution of a series of PL/SQL statements, or return a set of PL/SQL statements that could be executed to create a pluggable database.

Body ()

Root Schema : RESTSQLCollection

Type: `object`

Show Source

- env(optional): string
- items(optional): array items

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/SQLItem"
                }
            },
            "env":{
                "type":"string"
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object SQLItem

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/SQLItem"
        }
    }

Nested Schema : SQLItem

Type: `object`

Show Source

- response(optional): array response
- result(optional): integer
- statementId(optional): integer

<!-- -->

    {
        "type":"object",
        "properties":{
            "statementId":{
                "type":"integer"
            },
            "response":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "result":{
                "type":"integer"
            }
        }
    }

Nested Schema : response

Type: `array`

Show Source

- Array of: string

<!-- -->

    {
        "type":"array",
        "items":{
            "type":"string"
        }
    }

Back to Top
