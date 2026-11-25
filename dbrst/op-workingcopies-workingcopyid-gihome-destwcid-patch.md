Moves the Oracle Grid Infrastructure from the source working copy to the destination working copy.

### Request

Supported Media Types

- application/json

Path Parameters

- destWcId: string
  Name of the destination working copy to which the Oracle Software needs to be moved
- workingCopyId: string
  Name of the working copy.

Body ()

Root Schema : MoveGihomeBody

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
- auto(optional): boolean
  Default Value: `false`
  Automatically patch databases along with patching Grid Infrastructure.
- batches(optional): string
  List of batches of nodes in the format: "(Ba),...,(Bz)".
- cleanpids(optional): boolean
  Default Value: `false`
  Cleans up processes during Oracle Grid Infrastructure move operation.
- continue(optional): boolean
  Default Value: `false`
  Continue restarting CRS stack on the next batch of nodes.
- dbhomes(optional): string
  Mapping of source and destination working copies in the format: "=,...,=".
- dblist(optional): string
  Patch only the specified databases.
- disconnect(optional): boolean
  Default Value: `false`
  Disconnect all sessions before stopping or relocating services.
- draintimeout(optional): integer(int32)
  Service drain timeout specified in seconds.
- eval(optional): boolean
  Default Value: `false`
  Evaluate without executing the command.
- excludedblist(optional): string
  Patch all databases except the specified databases.
- firstnode(optional): string
  Deprecated.
- ignoreDBStartError(optional): boolean
  Default Value: `false`
  Ignore any database startup errors during Oracle Grid Infrastructure patching.
- ignorewcpatches(optional): boolean
  Default Value: `false`
  Ignores if the patched working copy is missing some patches which are present in the source path or working copy.
- imageName(optional): string
  Name of the image.
- keepplacement(optional): boolean
  Default Value: `false`
  Ensure that services of administrator-managed Oracle RAC or Oracle RAC One databases are running on the same instances before and after the move operation.
- nodatapatch(optional): boolean
  Default Value: `false`
  Indicates that "datapatch" should not be executed for databases being moved.
- nonrolling(optional): boolean
  Default Value: `false`
  Move the Oracle home in non-rolling mode.
- path(optional): string
  The absolute path for the destination working copy.
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
- smartmove(optional): boolean
  Default Value: `false`
  Auto-generate the list of batches of nodes and move databases by restarting instances batch after batch.
- sourceHome(optional): string
  Source Oracle home path
- stopoption(optional): string
  Allowed Values: `[ "ABORT", "IMMEDIATE", "NORMAL", "TRANSACTIONAL", "TRANSACTIONAL_LOCAL" ]`
  Stop option for database: ABORT, IMMEDIATE, NORMAL, TRANSACTIONAL, TRANSACTIONAL_LOCAL.
- sudoPath(optional): string
  Location of sudo binary.
- sudoUser(optional): string
  Perform super user operations as sudo user name.
- superUserPasswd(optional): string
  The password for the super user account.
- targetNode(optional): string
  Node on which operation needs to be executed
- userActionData(optional): string
  Value to be passed to useractiondata parameter of useraction script.

<!-- -->

    {
        "type":"object",
        "properties":{
            "imageName":{
                "type":"string",
                "description":"Name of the image."
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed"
            },
            "agpath":{
                "type":"string",
                "description":"Read/write path for the persistent Oracle home path."
            },
            "aupath":{
                "type":"string",
                "description":"Read-only gold image path for the persistent Oracle home path."
            },
            "ignorewcpatches":{
                "type":"boolean",
                "default":false,
                "description":"Ignores if the patched working copy is missing some patches which are present in the source path or working copy."
            },
            "abort":{
                "type":"boolean",
                "default":false,
                "description":"Abort the ongoing \"move\" operation."
            },
            "saf":{
                "type":"string",
                "description":"Service availability factor, the minimum percentage of instances on which a service must remain running during the move."
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
            "batches":{
                "type":"string",
                "description":"List of batches of nodes in the format: \"(Ba),...,(Bz)\"."
            },
            "nonrolling":{
                "type":"boolean",
                "default":false,
                "description":"Move the Oracle home in non-rolling mode."
            },
            "smartmove":{
                "type":"boolean",
                "default":false,
                "description":"Auto-generate the list of batches of nodes and move databases by restarting instances batch after batch."
            },
            "firstnode":{
                "type":"string",
                "description":"Deprecated."
            },
            "excludedblist":{
                "type":"string",
                "description":"Patch all databases except the specified databases."
            },
            "cleanpids":{
                "type":"boolean",
                "default":false,
                "description":"Cleans up processes during Oracle Grid Infrastructure move operation."
            },
            "continue":{
                "type":"boolean",
                "default":false,
                "description":"Continue restarting CRS stack on the next batch of nodes."
            },
            "userActionData":{
                "type":"string",
                "description":"Value to be passed to useractiondata parameter of useraction script."
            },
            "draintimeout":{
                "type":"integer",
                "format":"int32",
                "description":"Service drain timeout specified in seconds."
            },
            "nodatapatch":{
                "type":"boolean",
                "default":false,
                "description":"Indicates that \"datapatch\" should not be executed for databases being moved."
            },
            "dbhomes":{
                "type":"string",
                "description":"Mapping of source and destination working copies in the format: \"<source_wc1>=<dest_wc1>,...,<source_oracle_home_path>=<dest_wcN>\"."
            },
            "auto":{
                "type":"boolean",
                "default":false,
                "description":"Automatically patch databases along with patching Grid Infrastructure."
            },
            "dblist":{
                "type":"string",
                "description":"Patch only the specified databases."
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
            "path":{
                "type":"string",
                "description":"The absolute path for the destination working copy."
            },
            "root":{
                "type":"boolean",
                "default":false,
                "description":"Use root credentials to access the remote node."
            },
            "sudoUser":{
                "type":"string",
                "description":"Perform super user operations as sudo user name."
            },
            "sudoPath":{
                "type":"string",
                "description":"Location of sudo binary."
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
            "ignoreDBStartError":{
                "type":"boolean",
                "default":false,
                "description":"Ignore any database startup errors during Oracle Grid Infrastructure patching."
            },
            "sourceHome":{
                "description":"Source Oracle home path",
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

The following example shows how to patch an Oracle Grid Infrastructure software home from a working copy named `GI_WCopy121` to the existing destination working copy named `GI_WCopy1212` by submitting a PATCH request on the REST resource using cURL.

    curl -u restUser -X PATCH -H "Content-Type: application/json" -d "@body.json "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/GI_WCopy121/gihome/GI_WCopy1212"

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
        "nonrolling" : true
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
