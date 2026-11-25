Moves a database from the unamanged Oracle Database Software home to a patched working copy.

### Request

Supported Media Types

- application/json

Header Parameters

- Authorization: string
  Base64 encoding of the user name and password of the user making the request. For more information, see [Authentication for Fleet Patching and Provisioning](Authentication-RHP.md).

Body ()

Root Schema : MoveDatabaseBody

Type: `object`

Show Source

- abort(optional): boolean
  Default Value: `false`
  Abort the ongoing "move" operation.
- agpath(optional): string
  Read/write path for the persistent Oracle home path.
- aupath(optional): string
  Read-only gold image path for the persistent Oracle home path.
- auth(optional): string
  Use an authentication plugin to access the remote node.
- authArgs(optional): object authArgs
  Additional Properties Allowed: additionalProperties
  Additional properties for the selected authentication plugin.
- cc(optional): string
  List of users to whom email notifications will be sent, in addition to owner of working copy.
- client(optional): string
  Client cluster name
- continueRestart(optional): boolean
  Default Value: `false`
  Continue restarting databases on the next batch of nodes.
- dbname(optional): string
  Name of database (DB_UNIQUE_NAME) to be provisioned.
- disconnect(optional): boolean
  Default Value: `false`
  Disconnect all sessions before stopping or relocating services.
- drain_timeout(optional): integer(int32)
  Service drain timeout specified in seconds.
- eval(optional): boolean
  Default Value: `false`
  Evaluate without executing the command.
- ignorewcpatches(optional): boolean
  Default Value: `false`
  Ignores if the patched working copy is missing some patches which are present in the source path or working copy.
- keepplacement(optional): boolean
  Default Value: `false`
  Ensure that services of administrator-managed Oracle RAC or Oracle RAC One databases are running on the same instances before and after the move operation.
- noDataPatch(optional): boolean
  Default Value: `false`
  Indicates that "datapatch" should not be executed for databases being moved.
- noreplay(optional): boolean
  Default Value: `false`
  Disable session replay during disconnection.
- notify(optional): boolean
  Default Value: `false`
  Send email notification.
- oraclebase(optional): string
  ORACLE_BASE path for provisioning Oracle database home or Oracle Grid Infrastructure home.
- patchedwc(optional): string
  Name of the patchedwc to which the database needs to be moved
- path(optional): string
  Absolute path location of the software home (This will be the ORACLE_HOME).
- revert(optional): boolean
  Default Value: `false`
  Revert to source Oracle home or working copy in case of batch-move or smartmove.
- root(optional): boolean
  Default Value: `false`
  Use root credentials to access the remote node.
- saf(optional): string
  Service availability factor, the minimum percentage of instances on which a service must remain running during the move.
- schedule(optional): string
  Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05.
- separate(optional): boolean
  Default Value: `false`
  Process batches separately. Move operation pauses for user intervention before continuing with the next batch.
- skip(optional): boolean
  Default Value: `false`
  Skip current batch of nodes and restart databases on the next batch of nodes.
- sourceHome(optional): string
  Source Oracle home path
- stopoption(optional): string
  Allowed Values: `[ "ABORT", "IMMEDIATE", "NORMAL", "TRANSACTIONAL", "TRANSACTIONAL_LOCAL" ]`
  Stop option for database: ABORT, IMMEDIATE, NORMAL, TRANSACTIONAL, TRANSACTIONAL_LOCAL.
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
            "dbname":{
                "type":"string",
                "description":"Name of database (DB_UNIQUE_NAME) to be provisioned."
            },
            "agpath":{
                "type":"string",
                "description":"Read/write path for the persistent Oracle home path."
            },
            "aupath":{
                "type":"string",
                "description":"Read-only gold image path for the persistent Oracle home path."
            },
            "cc":{
                "type":"string",
                "description":"List of users to whom email notifications will be sent, in addition to owner of working copy."
            },
            "ignorewcpatches":{
                "type":"boolean",
                "default":false,
                "description":"Ignores if the patched working copy is missing some patches which are present in the source path or working copy."
            },
            "notify":{
                "type":"boolean",
                "default":false,
                "description":"Send email notification."
            },
            "noDataPatch":{
                "type":"boolean",
                "default":false,
                "description":"Indicates that \"datapatch\" should not be executed for databases being moved."
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
            "schedule":{
                "type":"string",
                "description":"Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05."
            },
            "abort":{
                "type":"boolean",
                "default":false,
                "description":"Abort the ongoing \"move\" operation."
            },
            "drain_timeout":{
                "type":"integer",
                "format":"int32",
                "description":"Service drain timeout specified in seconds."
            },
            "skip":{
                "type":"boolean",
                "default":false,
                "description":"Skip current batch of nodes and restart databases on the next batch of nodes."
            },
            "stopoption":{
                "type":"string",
                "description":"Stop option for database: ABORT, IMMEDIATE, NORMAL, TRANSACTIONAL, TRANSACTIONAL_LOCAL.",
                "enum":[
                    "ABORT",
                    "IMMEDIATE",
                    "NORMAL",
                    "TRANSACTIONAL",
                    "TRANSACTIONAL_LOCAL"
                ]
            },
            "continueRestart":{
                "type":"boolean",
                "default":false,
                "description":"Continue restarting databases on the next batch of nodes."
            },
            "disconnect":{
                "type":"boolean",
                "default":false,
                "description":"Disconnect all sessions before stopping or relocating services."
            },
            "keepplacement":{
                "type":"boolean",
                "default":false,
                "description":"Ensure that services of administrator-managed Oracle RAC or Oracle RAC One databases are running on the same instances before and after the move operation."
            },
            "revert":{
                "type":"boolean",
                "default":false,
                "description":"Revert to source Oracle home or working copy in case of batch-move or smartmove."
            },
            "noreplay":{
                "type":"boolean",
                "default":false,
                "description":"Disable session replay during disconnection."
            },
            "path":{
                "type":"string",
                "description":"Absolute path location of the software home (This will be the ORACLE_HOME)."
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed"
            },
            "separate":{
                "type":"boolean",
                "default":false,
                "description":"Process batches separately. Move operation pauses for user intervention before continuing with the next batch."
            },
            "saf":{
                "type":"string",
                "description":"Service availability factor, the minimum percentage of instances on which a service must remain running during the move."
            },
            "client":{
                "type":"string",
                "description":"Client cluster name"
            },
            "oraclebase":{
                "type":"string",
                "description":"ORACLE_BASE path for provisioning Oracle database home or Oracle Grid Infrastructure home."
            },
            "sourceHome":{
                "description":"Source Oracle home path",
                "type":"string"
            },
            "patchedwc":{
                "description":"Name of the patchedwc to which the database needs to be moved",
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

The following example shows how to patch an unmanaged Oracle database software home, where all the arguments are provided in the request body `body.json`, by submitting a PATCH request on the REST resource using cURL.

    curl -u restUser -X PATCH -H "Content-Type: application/json" -d "@body.json" "https://RHP_node_name:8894/rhp-restapi/rhp/databases"

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
        "dbname" : "dbwc1",
        "sourceHome" : "/oracle/home",
        "patchedwc" : "DB_Wcopy2"
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
