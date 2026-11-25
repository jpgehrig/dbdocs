Creates a new working copy using an existing gold image

### Request

Supported Media Types

- application/json

Header Parameters

- Authorization: string
  Base64 encoding of the user name and password of the user making the request. For more information, see [Authentication for Fleet Patching and Provisioning](Authentication-RHP.md).

Body ()

Root Schema : AddWorkingCopyBody

Type: `object`

Show Source

- agpath(optional): string
  Read/write path for the persistent Oracle home path.
- asmClientData(optional): string
  File that contains the ASM client data.
- aupath(optional): string
  Read-only gold image path for the persistent Oracle home path.
- auth(optional): string
  Use an authentication plugin to access the remote node.
- authArgs(optional): object authArgs
  Additional Properties Allowed: additionalProperties
  Additional properties for the selected authentication plugin.
- cardinality(optional): string
  Cardinality for new server pool.
- cdb(optional): boolean
  Default Value: `false`
  To create database as container database.
- client(optional): string
  Client cluster name
- clusterManifest(optional): string
  Location of Cluster Manifest File.
- clusterNodes(optional): string
  Comma-separated list of node information on which Oracle Clusterware will be provisioned.
- datafileDestination(optional): string
  Data file destination location or ASM disk group name.
- dbname(optional): string
  Name of database (DB_UNIQUE_NAME) to be provisioned.
- dbTemplate(optional): string
  Absolute file path for the template file or relative path to the image home directory on Rapid Home Provisioning Server.
- dbType(optional): string
  Allowed Values: `[ "RAC", "RACONENODE", "SINGLE" ]`
  Type of database: Oracle RAC One Node or Oracle RAC or Single Instance.
- eval(optional): boolean
  Default Value: `false`
  Evaluate without executing the command.
- fixup(optional): boolean
  Default Value: `false`
  Execute fixup script. Valid only for Grid Infrastructure provisioning.
- gnsClientData(optional): string
  File that contains the GNS client data.
- groups(optional): string
  Comma-separated list of Oracle groups to be configured for the working copy. Specify a valid key such as OSDBA, OSOPER, OSASM, OSBACKUP, OSDG, OSKM, or OSRAC, equated to a valid group name as value.
- ignorePrereq(optional): boolean
  Default Value: `false`
  To ignore the CVU pre-requisite checks.
- imageName(optional): string
  Image name from the configured images
- inventory(optional): string
  Location of Oracle Inventory
- newpool(optional): string
  Server pool name for pool to be created.
- node(optional): string
  Comma-separated list of nodes on which database will be created
- numberOfPDBs(optional): integer(int32)
  Number of PDBs to be created.
- oracleBase(optional): string
  ORACLE_BASE path for provisioning Oracle database home or Oracle Grid Infrastructure home.
- path(optional): string
  Absolute path location of the software home to be imported (For database images, this will be the ORACLE_HOME).
- pDBName(optional): string
  The pDBName prefix if one or more PDBs need to be created.
- precheckonly(optional): boolean
  Perform only the patching precheck operations
- responsefile(optional): string
  response file to be used to perform Oracle Grid Infrastructure provisioning
- root(optional): boolean
  Default Value: `false`
  Use root credentials to access the remote node.
- schedule(optional): string
  Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05.
- serverpool(optional): string
  Comma-separated list of existing server pool names.
- setupSSH(optional): boolean
  Default Value: `false`
  sets up passwordless SSH user equivalence on the remote nodes for the provisioning user.
- softwareOnly(optional): string
  Default Value: `false`
  Perform Grid Infrastructure software-only provisioning.
- storagetype(optional): string
  Allowed Values: `[ "NFS", "LOCAL", "RHP_MANAGED" ]`
  Type of storage for the home.
- sudoPath(optional): string
  location of sudo binary.
- sudoUser(optional): string
  perform super user operations as sudo user name.
- superUserPasswd(optional): string
  The password for the super user account.
- targetNode(optional): string
  Node on which operation needs to be executed
- user(optional): string
  Name of the user for whom the software home is being provisioned.
- workingcopy(optional): string
  Name of the workingcopy

<!-- -->

    {
        "type":"object",
        "properties":{
            "client":{
                "type":"string",
                "description":"Client cluster name"
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed"
            },
            "setupSSH":{
                "type":"boolean",
                "default":false,
                "description":"sets up passwordless SSH user equivalence on the remote nodes for the provisioning user."
            },
            "node":{
                "type":"string",
                "description":"Comma-separated list of nodes on which database will be created"
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
            "schedule":{
                "type":"string",
                "description":"Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05."
            },
            "user":{
                "type":"string",
                "description":"Name of the user for whom the software home is being provisioned."
            },
            "clusterNodes":{
                "type":"string",
                "description":"Comma-separated list of node information on which Oracle Clusterware will be provisioned."
            },
            "fixup":{
                "type":"boolean",
                "default":false,
                "description":"Execute fixup script. Valid only for Grid Infrastructure provisioning."
            },
            "asmClientData":{
                "type":"string",
                "description":"File that contains the ASM client data."
            },
            "gnsClientData":{
                "type":"string",
                "description":"File that contains the GNS client data."
            },
            "clusterManifest":{
                "type":"string",
                "description":"Location of Cluster Manifest File."
            },
            "oracleBase":{
                "type":"string",
                "description":"ORACLE_BASE path for provisioning Oracle database home or Oracle Grid Infrastructure home."
            },
            "agpath":{
                "type":"string",
                "description":"Read/write path for the persistent Oracle home path."
            },
            "aupath":{
                "type":"string",
                "description":"Read-only gold image path for the persistent Oracle home path."
            },
            "ignorePrereq":{
                "type":"boolean",
                "default":false,
                "description":"To ignore the CVU pre-requisite checks."
            },
            "path":{
                "type":"string",
                "description":"Absolute path location of the software home to be imported (For database images, this will be the ORACLE_HOME)."
            },
            "dbTemplate":{
                "type":"string",
                "description":"Absolute file path for the template file or relative path to the image home directory on Rapid Home Provisioning Server."
            },
            "dbname":{
                "type":"string",
                "description":"Name of database (DB_UNIQUE_NAME) to be provisioned."
            },
            "cardinality":{
                "type":"string",
                "description":"Cardinality for new server pool."
            },
            "storagetype":{
                "type":"string",
                "description":"Type of storage for the home.",
                "enum":[
                    "NFS",
                    "LOCAL",
                    "RHP_MANAGED"
                ]
            },
            "datafileDestination":{
                "type":"string",
                "description":"Data file destination location or ASM disk group name."
            },
            "serverpool":{
                "type":"string",
                "description":"Comma-separated list of existing server pool names."
            },
            "numberOfPDBs":{
                "type":"integer",
                "format":"int32",
                "description":"Number of PDBs to be created."
            },
            "newpool":{
                "type":"string",
                "description":"Server pool name for pool to be created."
            },
            "pDBName":{
                "type":"string",
                "description":"The pDBName prefix if one or more PDBs need to be created."
            },
            "cdb":{
                "type":"boolean",
                "default":false,
                "description":"To create database as container database."
            },
            "softwareOnly":{
                "type":"string",
                "default":false,
                "description":"Perform Grid Infrastructure software-only provisioning."
            },
            "groups":{
                "type":"string",
                "description":"Comma-separated list of Oracle groups to be configured for the working copy. Specify a valid key such as OSDBA, OSOPER, OSASM, OSBACKUP, OSDG, OSKM, or OSRAC, equated to a valid group name as value."
            },
            "dbType":{
                "type":"string",
                "enum":[
                    "RAC",
                    "RACONENODE",
                    "SINGLE"
                ],
                "description":"Type of database: Oracle RAC One Node or Oracle RAC or Single Instance."
            },
            "imageName":{
                "description":"Image name from the configured images",
                "type":"string"
            },
            "inventory":{
                "description":"Location of Oracle Inventory",
                "type":"string"
            },
            "precheckonly":{
                "description":"Perform only the patching precheck operations",
                "type":"boolean"
            },
            "responsefile":{
                "description":"response file to be used to perform Oracle Grid Infrastructure provisioning",
                "type":"string"
            },
            "workingcopy":{
                "description":"Name of the workingcopy",
                "type":"string"
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

The following example shows how to create a working copy using an existing gold image specified on the request body `body.json`, by submitting a POST request on the REST resource using cURL.

    curl -u restUser -X POST -H "Content-Type: application/json" -d "@body.json" "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies"

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
        "path" : "/oracle/database/home",
        "oracleBase" : "/oracle/database/base",
        "storagetype" : "LOCAL",
        "imageName" : "DB_Image1",
        "workingcopy" : "DB_Wcopy1"
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
