Upgrade a database from a source working copy to a patched working copy.

### Request

Supported Media Types

- application/json

Path Parameters

- dbUniqueName: string
  Name of database (DB_UNIQUE_NAME) to be provisioned
- workingCopyId: string
  Name of the working copy.

Body ()

Root Schema : UpgradeDatabaseBody

Type: `object`

Show Source

- abort(optional): boolean
  Default Value: `false`
  Abort the ongoing operation.
- auth(optional): string
  Use an authentication plugin to access the remote node.
- authArgs(optional): object authArgs
  Additional Properties Allowed: additionalProperties
  Additional properties for the selected authentication plugin.
- client(optional): string
  Client cluster name
- destwc(optional): string
  Name of the destination working copy
- eval(optional): boolean
  Default Value: `false`
  Evaluate without executing the command.
- ignoreprereq(optional): boolean
  Default Value: `false`
  To ignore the CVU pre-requisite checks.
- imageName(optional): string
  Name of the image.
- path(optional): string
  Absolute path location of the software home to be imported (For database images, this will be the ORACLE_HOME).
- root(optional): boolean
  Default Value: `false`
  Use root credentials to access the remote node.
- schedule(optional): string
  Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05.
- sourcehome(optional): string
  Source Oracle home path.
- sourceHome(optional): string
  Source Oracle home path
- sourcewc(optional): string
  Name of the source working copy from which the Oracle Grid Infrastructure needs to be upgraded.
- sudoPath(optional): string
  location of sudo binary.
- sudoUser(optional): string
  perform super user operations as sudo user name.
- superUserPasswd(optional): string
  The password for the super user account.
- targetNode(optional): string
  Node on which operation needs to be executed

<!-- -->

    {
        "type":"object",
        "properties":{
            "sourcewc":{
                "type":"string",
                "description":"Name of the source working copy from which the Oracle Grid Infrastructure needs to be upgraded."
            },
            "imageName":{
                "type":"string",
                "description":"Name of the image."
            },
            "client":{
                "type":"string",
                "description":"Client cluster name"
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed"
            },
            "sourcehome":{
                "type":"string",
                "description":"Source Oracle home path."
            },
            "ignoreprereq":{
                "type":"boolean",
                "default":false,
                "description":"To ignore the CVU pre-requisite checks."
            },
            "path":{
                "type":"string",
                "description":"Absolute path location of the software home to be imported (For database images, this will be the ORACLE_HOME)."
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
                "description":"Abort the ongoing operation."
            },
            "sourceHome":{
                "description":"Source Oracle home path",
                "type":"string"
            },
            "destwc":{
                "type":"string",
                "description":"Name of the destination working copy"
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

The following example shows how to upgrade a database named `dbwc1` from a source working copy named `DB_WCopy122` to a destination working copy name `DB_WCopy181` specified in the request body `body.json`, by submitting a PUT request on the REST resource using cURL.

    curl -u restUser -X PUT -H "Content-Type: application/json" -d "@body.json" "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/DB_Wcopy122/databases/dbwc1"

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
        "destwc" : "DB_Wcopy181"
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
