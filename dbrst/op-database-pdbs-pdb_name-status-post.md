Changes the state of a pluggable database. The executed ALTER PLUGGABLE DATABASE command in the database includes the INSTANCES=ALL clause so that in an Oracle Real Application Clusters environment the pluggable database state is changed in all instances. This service requires db.cdb.adminUser credentials to be set in the pool configuration. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- pdb_name: string
  Name of the Pluggable Database.

Body ()

Root Schema : schema

Type: `object`

Show Source

- getScript(optional): boolean
  If defined, the response will contain a JSON object with the information of the script that was generated for execution. The change of state does not happen.
- modifyOption: string
  Allowed Values: `[ "IMMEDIATE", "NORMAL", "READ ONLY", "READ WRITE", "RESTRICTED" ]`
  Extra options for opening and closing a PDB.
- state: string
  Allowed Values: `[ "OPEN", "CLOSE" ]`
  The target state of the PDB.

<!-- -->

    {
        "type":"object",
        "required":[
            "state",
            "modifyOption"
        ],
        "properties":{
            "state":{
                "type":"string",
                "description":"The target state of the PDB.",
                "enum":[
                    "OPEN",
                    "CLOSE"
                ]
            },
            "modifyOption":{
                "type":"string",
                "description":"Extra options for opening and closing a PDB.",
                "enum":[
                    "IMMEDIATE",
                    "NORMAL",
                    "READ ONLY",
                    "READ WRITE",
                    "RESTRICTED"
                ]
            },
            "getScript":{
                "type":"boolean",
                "description":"If defined, the response will contain a JSON object with the information of the script that was generated for execution. The change of state does not happen."
            }
        }
    }

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

### Examples

The following example shows how to open or close a pluggable database by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/database/pdbs/devpdb1/status

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, and the path for this operation, and the PDB identifier `devpdb1`. The `pdb_name` path parameter in this example is devpdb1. The PDB Lifecycle Management service requires the credentials of `db.cdb.adminUser` to be set in the pool configuration and in this example, the default pool is configured for the container database.

The following is an example request body to close the pluggable database specified by the `pdb_name` parameter in the URL.

    {
      "state": "CLOSE",
      "modifyOption": "IMMEDIATE"
    }

The following is an example request body to open the database specified by the `pdb_name` parameter in the URL. The `modifyOption` parameter is required in all cases and so the value is set to `NORMAL` to allow the default open mode to be applied.

    {
      "state": "OPEN",
      "modifyOption": "NORMAL"
    }

### Example of Response Header

The following example shows the response header:

    HTTP/1.1 200 OK
    Date: Thu, 05 Sep 2019 12:21:01 PDT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 200 returned in JSON format:

    {
      "env":{"defaultTimeZone":"PST8PDT"},
      "items":[
        {
          "statementId":1,
          "response":["\nPL\/SQL procedure successfully completed.\n\n"],
          "result":0
        }
      ]
    }

Back to Top
