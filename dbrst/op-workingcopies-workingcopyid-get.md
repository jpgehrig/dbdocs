Return the working copy configuration.

### Request

Supported Media Types

- application/json

Path Parameters

- workingCopyId: string
  Name of the working copy.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

OK. A JSON object containing a working copy resource representation with multiple properties and the links array with at least the "self" link.

Body ()

Root Schema : workingcopyResource

Type: `object`

Show Source

- accessControl(optional): array accessControl
- additionalBugFixesNotInImage(optional): string
- additionalPatchesComparedToImage(optional): string
- allPatchesAvailableInHome(optional): string
- clusterClass(optional): string
- clusterClient(optional): string
- clusterMode(optional): string
- clusterName(optional): string
- clusterNodes(optional): array clusterNodes
- clusterType(optional): string
- complete(optional): boolean
  Default Value: `false`
- configuredDatabases(optional): array configuredDatabases
- goldImagePath(optional): string
- groupsConfiguredInWorkingCopy(optional): array groupsConfiguredInWorkingCopy
- imageName(optional): string
- imageTypeName(optional): string
- links(optional): array links
- oracleBase(optional): string
- owner(optional): string
- softwareHomePath(optional): string
- softwareOnly(optional): boolean
  Default Value: `false`
- storageType(optional): string
- workingCopyId(optional): string
- workPath(optional): string

<!-- -->

    {
        "type":"object",
        "properties":{
            "accessControl":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "additionalBugFixesNotInImage":{
                "type":"string"
            },
            "additionalPatchesComparedToImage":{
                "type":"string"
            },
            "allPatchesAvailableInHome":{
                "type":"string"
            },
            "clusterClient":{
                "type":"string"
            },
            "clusterClass":{
                "type":"string"
            },
            "clusterName":{
                "type":"string"
            },
            "clusterNodes":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "clusterType":{
                "type":"string"
            },
            "complete":{
                "type":"boolean",
                "default":false
            },
            "configuredDatabases":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "goldImagePath":{
                "type":"string"
            },
            "groupsConfiguredInWorkingCopy":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "imageName":{
                "type":"string"
            },
            "imageTypeName":{
                "type":"string"
            },
            "oracleBase":{
                "type":"string"
            },
            "owner":{
                "type":"string"
            },
            "softwareHomePath":{
                "type":"string"
            },
            "storageType":{
                "type":"string"
            },
            "workingCopyId":{
                "type":"string"
            },
            "workPath":{
                "type":"string"
            },
            "softwareOnly":{
                "type":"boolean",
                "default":false
            },
            "clusterMode":{
                "type":"string"
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/singleResourceLinks"
                }
            }
        }
    }

Nested Schema : accessControl

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

Nested Schema : clusterNodes

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

Nested Schema : configuredDatabases

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

Nested Schema : groupsConfiguredInWorkingCopy

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

The following example shows how to view the configuration details of a working copy by submitting a GET request on the REST resource using cURL.

    curl -u restUser -X GET "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/DB_WCopy181"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 200
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 845
    Date:  Tue, 19 Jun 2018 14:03:23 GMT

### Response Body

    {
    "links": [{
       "uri": "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/DB_Wcopy181",
       "rel": "self"
      }
    ],
    "workPath": "",
    "imageName": "DB_Image1",
    "workingCopyId": "DB_Wcopy181",
    "complete": true,
    "clusterClient": "clusterClientNodeName01",
    "oracleBase": "/oracle/wcobase1",
    "accessControl": ["USER:gridUser1@clusterClientNodeName01","ROLE:GH_WC_ADMIN"],
    "additionalBugFixesNotInImage": "",
    "additionalPatchesComparedToImage": "",
    "allPatchesAvailableInHome": "",
    "configuredDatabases": ["dbwc1","dbwc2"],
    "goldImagePath": "",
    "groupsConfiguredInWorkingCopy": ["OSDBA=svrtech","OSOPER=svrtech","OSBACKUP=svrtech","OSDG=svrtech","OSKM=svrtech","OSRAC=svrtech"],
    "softwareHomePath": "/oracle/dbwc1",
    "storageType": "LOCAL",
    "imageTypeName": "ORACLEDBSOFTWARE",
    "owner": "gridUser1@clusterClientNodeName01"
    }

Back to Top
