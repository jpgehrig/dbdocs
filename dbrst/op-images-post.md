Create a gold image from the Software home specified in the body of this request, can be Oracle Database, Grid Infrastructure or any other Software home

### Request

Supported Media Types

- application/json

Header Parameters

- Authorization: string
  Base64 encoding of the user name and password of the user making the request. For more information, see [Authentication for Fleet Patching and Provisioning](Authentication-RHP.md).

Body ()

Root Schema : ImportImageBody

Type: `object`

Show Source

- auth(optional): string
  Use an authentication plugin to access the remote node.
- authArgs(optional): object authArgs
  Additional Properties Allowed: additionalProperties
  Additional properties for the selected authentication plugin.
- cc(optional): string
  List of users to whom email notifications will be sent, in addition to owner of working copy.
- client(optional): string
  Client cluster name.
- host(optional): string
  GIAAS host name.
- imageName(optional): string
  Name of the image.
- imageType(optional): string
  The software type. ("ORACLEDBSOFTWARE" (default) for Oracle database software, "ORACLEGISOFTWARE" for Oracle Grid Infrastructure software, ORACLEGGSOFTWARE for Oracle GoldenGate software, "LINUXOS" for linux Opearting System ISO, and "SOFTWARE" for all other software. For a custom image type, use the image type name.)
- notify(optional): boolean
  Default Value: `false`
  Send email notification.
- patches(optional): string
  Comma separated bug numbers or NFS downloaded zip location or combination of both.
- path(optional): string
  Absolute path location of the software home to be imported (For database images, this will be the ORACLE_HOME).
- pathOwner(optional): string
  User with read access to files under the specified path.
- port(optional): string
  Port number in the range of 1024-65536.
- psu(optional): string
  Bug number or downloaded zip location or released PSU/BP.
- root(optional): boolean
  Default Value: `false`
  Use root credentials to access the remote node.
- schedule(optional): string
  Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05.
- state(optional): string
  Allowed Values: `[ "TESTABLE", "RESTRICTED", "PUBLISHED" ]`
  State name.
- sudoPath(optional): string
  location of sudo binary.
- sudoUser(optional): string
  perform super user operations as sudo user name.
- superUserPasswd(optional): string
  The password for the super user account.
- targetNode(optional): string
  Node on which operation needs to be executed.
- userActionData(optional): string
  Value to be passed to useractiondata parameter of useraction script.
- version(optional): string
  Oracle database version for GIAAS, ODA patchbundle version for ODAPATCHSOFTWARE.
- zip(optional): string
  Absolute path of the compressed software home to be imported (a ZIP or TAR file).

<!-- -->

    {
        "type":"object",
        "properties":{
            "imageName":{
                "type":"string",
                "description":"Name of the image."
            },
            "client":{
                "type":"string",
                "description":"Client cluster name."
            },
            "imageType":{
                "type":"string",
                "description":"The software type. (\"ORACLEDBSOFTWARE\" (default) for Oracle database software, \"ORACLEGISOFTWARE\" for Oracle Grid Infrastructure software, ORACLEGGSOFTWARE for Oracle GoldenGate software, \"LINUXOS\" for linux Opearting System ISO, and \"SOFTWARE\" for all other software. For a custom image type, use the image type name.)"
            },
            "schedule":{
                "type":"string",
                "description":"Preferred time to execute the operation, in ISO-8601 format. For example: 2016-12-21T19:13:17+05."
            },
            "targetNode":{
                "type":"string",
                "description":"Node on which operation needs to be executed."
            },
            "userActionData":{
                "type":"string",
                "description":"Value to be passed to useractiondata parameter of useraction script."
            },
            "pathOwner":{
                "type":"string",
                "description":"User with read access to files under the specified path."
            },
            "zip":{
                "type":"string",
                "description":"Absolute path of the compressed software home to be imported (a ZIP or TAR file)."
            },
            "version":{
                "type":"string",
                "description":"Oracle database version for GIAAS, ODA patchbundle version for ODAPATCHSOFTWARE."
            },
            "state":{
                "type":"string",
                "description":"State name.",
                "enum":[
                    "TESTABLE",
                    "RESTRICTED",
                    "PUBLISHED"
                ]
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
            "host":{
                "type":"string",
                "description":"GIAAS host name."
            },
            "cc":{
                "type":"string",
                "description":"List of users to whom email notifications will be sent, in addition to owner of working copy."
            },
            "notify":{
                "type":"boolean",
                "default":false,
                "description":"Send email notification."
            },
            "psu":{
                "type":"string",
                "description":"Bug number or downloaded zip location or released PSU/BP."
            },
            "patches":{
                "type":"string",
                "description":"Comma separated bug numbers or NFS downloaded zip location or combination of both."
            },
            "port":{
                "type":"string",
                "description":"Port number in the range of 1024-65536."
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

The following example shows how to import a gold image from a software home in the specified `path` in the request body `body.json`, by submitting a POST request on the REST resource using cURL.

    curl -u restUser -X POST -H "Content-Type: application/json" -d "@body.json" "https://RHP_node_name:8894/rhp-restapi/rhp/images"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 202
    Location: https://rhpNodeName:8894/rhp-restapi/rhp/jobs/1
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 159
    Date:  Tue, 19 Jun 2018 14:03:23 GM

### Request Body (body.json)

    {
        "imageName": "DB_Image1",
        "path": "/oracle/dbwc1"
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
