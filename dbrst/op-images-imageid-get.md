Display the details of the gold image associated to the given image name.

### Request

Supported Media Types

- application/json

Path Parameters

- imageId: string
  Name of the image.

Query Parameters

- dbtemplate(optional): boolean
  Displays template file names in the default template directory.
  Default Value: `false`
- drift(optional): string
  Lists the bug fixes not included in the golden image.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

OK. A JSON object containing an image resource representation with multiple properties and the links array with at least the "self" link.

Body ()

Root Schema : imageResource

Type: `object`

Show Source

- clientName(optional): string
- complete(optional): boolean
- containsNonRollingPatch(optional): boolean
- groupsConfigured(optional): string
- homePath(optional): string
- imageId(optional): string
- imageSize(optional): integer
- imageState(optional): string
- imageType(optional): string
- links(optional): array links
- owner(optional): string
- parentImage(optional): string
- patches(optional): array patches
- platform(optional): string
- roles(optional): array roles
- templateWithDataFiles(optional): array templateWithDataFiles
- templateWithoutDataFiles(optional): array templateWithoutDataFiles
- version(optional): string

<!-- -->

    {
        "type":"object",
        "properties":{
            "imageId":{
                "type":"string"
            },
            "clientName":{
                "type":"string"
            },
            "roles":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "patches":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "parentImage":{
                "type":"string"
            },
            "homePath":{
                "type":"string"
            },
            "imageState":{
                "type":"string"
            },
            "imageType":{
                "type":"string"
            },
            "imageSize":{
                "type":"integer"
            },
            "version":{
                "type":"string"
            },
            "owner":{
                "type":"string"
            },
            "complete":{
                "type":"boolean"
            },
            "platform":{
                "type":"string"
            },
            "containsNonRollingPatch":{
                "type":"boolean"
            },
            "groupsConfigured":{
                "type":"string"
            },
            "templateWithDataFiles":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "templateWithoutDataFiles":{
                "type":"array",
                "items":{
                    "type":"string"
                }
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

Nested Schema : patches

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

Nested Schema : roles

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

Nested Schema : templateWithDataFiles

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

Nested Schema : templateWithoutDataFiles

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

The following example shows how to view the configuration details of a gold image by submitting a GET request on the REST resource using cURL.

    curl -u restUser -X GET "https://RHP_node_name:8894/rhp-restapi/rhp/images/DB_Image1"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 200
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 855
    Date:  Tue, 19 Jun 2018 14:03:23 GM

### Response Body

    {
        "links": [{
            "uri": "https://RHP_node_name:8894/rhp-restapi/rhp/images/DB_Image1",
            "rel": "self"
        }],
        "homePath": "/rhp_storage/images/iDB_Image1345266/.ACFS/snaps/iDB_Image1/swhome",
        "version": "18.1.0.0.0:18.1.0.0.0",
        "imageState": "PUBLISHED",
        "imageSize": 7873,
        "patches": [""],
        "imageId": "DB_Image1",
        "roles": ["USER:gridUser1@clientClusterNodeName",
        "ROLE:OTHER",
        "ROLE:GH_IMG_PUBLISH",
        "ROLE:GH_IMG_ADMIN",
        "ROLE:GH_IMG_VISIBILITY"],
        "parentImage": "",
        "complete": true,
        "platform": "Linux_AMD64",
        "containsNonRollingPatch": false,
        "groupsConfigured": "OSDBA=svrtech,OSOPER=svrtech,OSBACKUP=svrtech,OSDG=svrtech,OSKM=svrtech,OSRAC=svrtech",
        "clientName": "aime1adc01gdf",
        "imageType": "ORACLEDBSOFTWARE",
        "owner": "gridUser1@clientClusterNodeName"
    }

Back to Top
