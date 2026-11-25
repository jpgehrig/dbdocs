Provision a new Oracle Database on a managed working copy.

### Request

Supported Media Types

- application/json

Path Parameters

- workingCopyId: string
  Name of the working copy.

Header Parameters

- Authorization: string
  Base64 encoding of the user name and password of the user making the request. For more information, see [Authentication for Fleet Patching and Provisioning](Authentication-RHP.md).

Body ()

Root Schema : AddDatabaseBody

Type: `object`

Show Source

- auth(optional): string
  Use an authentication plugin to access the remote node.
- authArgs(optional): object authArgs
  Additional Properties Allowed: additionalProperties
  Additional properties for the selected authentication plugin.
- cardinality(optional): string
  Cardinality for new server pool
- cdb(optional): boolean
  Default Value: `false`
  To create database as container database
- datafileDestination(optional): string
  Data file destination location or ASM disk group name
- dbname(optional): string
  Name of database (DB_UNIQUE_NAME) to be provisioned
- dbTemplate(optional): string
  Absolute file path for the template file or relative path to the image home directory on Rapid Home Provisioning Server
- dbType(optional): string
  Allowed Values: `[ "RAC", "RACONENODE", "SINGLE" ]`
  Type of database: Oracle RAC One Node or Oracle RAC or Single Instance
- eval(optional): boolean
  Default Value: `false`
  Evaluate without executing the command.
- newpool(optional): string
  Server pool name for pool to be created
- newpqpool(optional): string
  Server pool name for pool to be created
- nodes(optional): string
  Comma-separated list of nodes on which database will be created
- numberOfPDBs(optional): integer(int32)
  Number of PDBs to be created
- pDBName(optional): string
  The pdbName prefix if one or more PDBs need to be created
- pqcardinality(optional): string
  Cardinality for new PQ pool
- pqpool(optional): string
  Existing PQ pool name
- root(optional): boolean
  Default Value: `false`
  Use root credentials to access the remote node.
- schedule(optional): string
  Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05.
- serverpool(optional): string
  Comma-separated list of existing server pool names
- sudoPath(optional): string
  location of sudo binary.
- sudoUser(optional): string
  perform super user operations as sudo user name.
- superUserPasswd(optional): string
  The password for the super user account.
- targetNode(optional): string
  Node on which operation needs to be executed
- userActionData(optional): string
  Value to be passed to useractiondata parameter of useraction script

<!-- -->

    {
        "type":"object",
        "properties":{
            "pqpool":{
                "type":"string",
                "description":"Existing PQ pool name"
            },
            "newpqpool":{
                "type":"string",
                "description":"Server pool name for pool to be created"
            },
            "pqcardinality":{
                "type":"string",
                "description":"Cardinality for new PQ pool"
            },
            "cardinality":{
                "description":"Cardinality for new server pool",
                "type":"string"
            },
            "dbTemplate":{
                "type":"string",
                "description":"Absolute file path for the template file or relative path to the image home directory on Rapid Home Provisioning Server"
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed"
            },
            "datafileDestination":{
                "type":"string",
                "description":"Data file destination location or ASM disk group name"
            },
            "numberOfPDBs":{
                "type":"integer",
                "format":"int32",
                "description":"Number of PDBs to be created"
            },
            "pDBName":{
                "type":"string",
                "description":"The pdbName prefix if one or more PDBs need to be created"
            },
            "dbname":{
                "description":"Name of database (DB_UNIQUE_NAME) to be provisioned",
                "type":"string"
            },
            "cdb":{
                "type":"boolean",
                "default":false,
                "description":"To create database as container database"
            },
            "dbType":{
                "type":"string",
                "enum":[
                    "RAC",
                    "RACONENODE",
                    "SINGLE"
                ],
                "description":"Type of database: Oracle RAC One Node or Oracle RAC or Single Instance"
            },
            "userActionData":{
                "type":"string",
                "description":"Value to be passed to useractiondata parameter of useraction script"
            },
            "root":{
                "type":"boolean",
                "default":false,
                "description":"Use root credentials to access the remote node."
            },
            "sudoUser":{
                "type":"string",
                "description":"perform super user operations as sudo user name."
            },
            "sudoPath":{
                "type":"string",
                "description":"location of sudo binary."
            },
            "superUserPasswd":{
                "type":"string",
                "description":"The password for the super user account."
            },
            "authArgs":{
                "type":"object",
                "description":"Additional properties for the selected authentication plugin.",
                "additionalProperties":{
                    "type":"string"
                }
            },
            "auth":{
                "type":"string",
                "description":"Use an authentication plugin to access the remote node."
            },
            "eval":{
                "type":"boolean",
                "default":false,
                "description":"Evaluate without executing the command."
            },
            "newpool":{
                "description":"Server pool name for pool to be created",
                "type":"string"
            },
            "nodes":{
                "description":"Comma-separated list of nodes on which database will be created",
                "type":"string"
            },
            "serverpool":{
                "description":"Comma-separated list of existing server pool names",
                "type":"string"
            },
            "schedule":{
                "type":"string",
                "description":"Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05."
            }
        }
    }

Nested Schema : authArgs

Type: `object`

Additional Properties Allowed

Show Source

- string

<!-- -->

    {
        "type":"object",
        "description":"Additional properties for the selected authentication plugin.",
        "additionalProperties":{
            "type":"string"
        }
    }

Additional properties for the selected authentication plugin.

Security

- basicAuthentication: basic
  Type: `basic`

Back to Top

### Response

Supported Media Types

- application/json

#### 202 Response

Accepted. A JSON object containing job resource details of the accepted operation to obtain status and output of the progress.

Headers

- Location: string
  URL to the job that will execute the operation

Body ()

Root Schema : jobResource

Type: `object`

Show Source

- jobId(optional): string
- links(optional): array links
- operation(optional): string
- output(optional): object jobOutputResource
- status(optional): string

<!-- -->

    {
        "type":"object",
        "properties":{
            "jobId":{
                "type":"string"
            },
            "status":{
                "type":"string"
            },
            "operation":{
                "type":"string"
            },
            "output":{
                "$ref":"#/definitions/jobOutputResource"
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/singleResourceLinks"
                }
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object singleResourceLinks

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/singleResourceLinks"
        }
    }

Nested Schema : jobOutputResource

Type: `object`

Show Source

- hasMore(optional): boolean
  Default Value: `false`
- limit(optional): integer
- links(optional): array links
- offset(optional): integer
- output(optional): string

<!-- -->

    {
        "type":"object",
        "properties":{
            "output":{
                "type":"string"
            },
            "limit":{
                "type":"integer"
            },
            "offset":{
                "type":"integer"
            },
            "hasMore":{
                "type":"boolean",
                "default":false
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/collectionResourceLinks"
                }
            }
        }
    }

Nested Schema : singleResourceLinks

Type: `object`

Show Source

- href(optional): string
  The referenced hyperlink element provided in an absolute format.
- rel(optional): string
  Allowed Values: `[ "self", "collection", "up", "describedBy" ]`
  Specify the type of relationship the link has with the described resource.

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string",
                "description":"Specify the type of relationship the link has with the described resource.",
                "enum":[
                    "self",
                    "collection",
                    "up",
                    "describedBy"
                ]
            },
            "href":{
                "type":"string",
                "description":"The referenced hyperlink element provided in an absolute format."
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object collectionResourceLinks

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/collectionResourceLinks"
        }
    }

Nested Schema : collectionResourceLinks

Type: `object`

Show Source

- href(optional): string
  The referenced hyperlink element provided in an absolute format with the correct URL parameters.
- rel(optional): string
  Allowed Values: `[ "next", "prev", "first", "last" ]`
  Specify the type of relationship the link has with the described resource.

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string",
                "description":"Specify the type of relationship the link has with the described resource.",
                "enum":[
                    "next",
                    "prev",
                    "first",
                    "last"
                ]
            },
            "href":{
                "type":"string",
                "description":"The referenced hyperlink element provided in an absolute format with the correct URL parameters."
            }
        }
    }

#### 400 Response

Bad Request. A JSON object containing error details of the issue found while parsing a parameter value or name.

Body ()

Root Schema : errorResource

Type: `object`

Show Source

- errorCode(optional): string
  Application specific error code, related to the error message shown at title.
- errorDetails(optional): array errorDetails
  If multiple errors are reported they can be organized in a hierarchical structure in this array.
- errorPath(optional): string
  XPath or JSON path to indicate where the error occurs.
- instance(optional): string
  URI to the link that provides more detail about the error.
- status(optional): integer
  HTTP status code.
- title(optional): string
  Summary error message.
- type(optional): string
  Link to HTTP error code page.

<!-- -->

    {
        "type":"object",
        "properties":{
            "status":{
                "type":"integer",
                "description":"HTTP status code."
            },
            "type":{
                "type":"string",
                "description":"Link to HTTP error code page."
            },
            "title":{
                "type":"string",
                "description":"Summary error message."
            },
            "instance":{
                "type":"string",
                "description":"URI to the link that provides more detail about the error."
            },
            "errorDetails":{
                "type":"array",
                "description":"If multiple errors are reported they can be organized in a hierarchical structure in this array.",
                "items":{
                    "$ref":"#/definitions/errorResource"
                }
            },
            "errorPath":{
                "type":"string",
                "description":"XPath or JSON path to indicate where the error occurs."
            },
            "errorCode":{
                "type":"string",
                "description":"Application specific error code, related to the error message shown at title."
            }
        }
    }

Nested Schema : errorDetails

Type: `array`

If multiple errors are reported they can be organized in a hierarchical structure in this array.

Show Source

- Array of: object errorResource

<!-- -->

    {
        "type":"array",
        "description":"If multiple errors are reported they can be organized in a hierarchical structure in this array.",
        "items":{
            "$ref":"#/definitions/errorResource"
        }
    }

#### Default Response

Unexpected error. A JSON object containing error details of the issue while executing the operation.

Body ()

Root Schema : errorResource

Type: `object`

Show Source

- errorCode(optional): string
  Application specific error code, related to the error message shown at title.
- errorDetails(optional): array errorDetails
  If multiple errors are reported they can be organized in a hierarchical structure in this array.
- errorPath(optional): string
  XPath or JSON path to indicate where the error occurs.
- instance(optional): string
  URI to the link that provides more detail about the error.
- status(optional): integer
  HTTP status code.
- title(optional): string
  Summary error message.
- type(optional): string
  Link to HTTP error code page.

<!-- -->

    {
        "type":"object",
        "properties":{
            "status":{
                "type":"integer",
                "description":"HTTP status code."
            },
            "type":{
                "type":"string",
                "description":"Link to HTTP error code page."
            },
            "title":{
                "type":"string",
                "description":"Summary error message."
            },
            "instance":{
                "type":"string",
                "description":"URI to the link that provides more detail about the error."
            },
            "errorDetails":{
                "type":"array",
                "description":"If multiple errors are reported they can be organized in a hierarchical structure in this array.",
                "items":{
                    "$ref":"#/definitions/errorResource"
                }
            },
            "errorPath":{
                "type":"string",
                "description":"XPath or JSON path to indicate where the error occurs."
            },
            "errorCode":{
                "type":"string",
                "description":"Application specific error code, related to the error message shown at title."
            }
        }
    }

Nested Schema : errorDetails

Type: `array`

If multiple errors are reported they can be organized in a hierarchical structure in this array.

Show Source

- Array of: object errorResource

<!-- -->

    {
        "type":"array",
        "description":"If multiple errors are reported they can be organized in a hierarchical structure in this array.",
        "items":{
            "$ref":"#/definitions/errorResource"
        }
    }

Back to Top

### Examples

The following example shows how to provision a new Oracle database instance on a managed working copy, where all the arguments are provided in the request body `body.json`, by submitting a POST request on the REST resource using cURL.

    curl -u restUser -X POST -H "Content-Type: application/json" -d "@body.json" "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/DB_Wcopy181/databases"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 202
    Location: https://RHP_node_name:8894/rhp-restapi/rhp/jobs/1
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 159
    Date:  Tue, 19 Jun 2018 14:03:23 GMT

### Request Body (body.json)

    {
        "dbname" : "dbwc1"
    }

### Response Body

    {
         "links": [{
             "uri": "https://RHP_node_name:8894/rhp-restapi/rhp/jobs/1",
             "rel": "self"
          }],
         "jobId": "1",
         "output": {  }
    }

Back to Top
