Return the list of names of the working copies based on a given golden image type.

### Request

Supported Media Types

- application/json

Path Parameters

- imageType: string
  The software type. ("ORACLEDBSOFTWARE" (default) for Oracle database software, "ORACLEGISOFTWARE" for Oracle Grid Infrastructure software, ORACLEGGSOFTWARE for Oracle GoldenGate software, "LINUXOS" for linux Opearting System ISO, and "SOFTWARE" for all other software. For a custom image type, use the image type name.)

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

OK. A JSON object containing an "items" property populated with 0 or more elements with at least an Id property and the links array with at least the "self" link.

Body ()

Root Schema : arrayOfItems

Type: `object`

Show Source

- items(optional): array items

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/singleResource"
                }
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object singleResource

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/singleResource"
        }
    }

Nested Schema : singleResource

Type: `object`

Show Source

- links(optional): array links
- resourceId(optional): string

<!-- -->

    {
        "type":"object",
        "properties":{
            "resourceId":{
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

The following example shows how to search working copies based on the ORACLEDBSOFTWARE image type, by submitting a GET request on the REST resource using cURL.

    curl -u restUser -X GET "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/imagetypes/ORACLEDBSOFTWARE"

### HTTP Status Code and Response Headers

    HTTP/1.1 200
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 239
    Date:  Tue, 19 Jun 2018 14:03:23 GMT

### Response Body

    {
      "items": [
        {
          "workingCopyId": "DB_WCopy1",
          "links": [{
                          "uri": "https://RHP_node_name:8894/rhp-restapi/rhp/workingcopies/DB_WCopy1",
                          "rel": "self"
              }
          ]
        }
      ]
    }

Back to Top
