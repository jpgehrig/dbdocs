Delete the image series from the server, but leave all the images intact.

### Request

Supported Media Types

- application/json

Path Parameters

- seriesId: string
  Name of the series.

Body ()

Root Schema : DeleteSeriesBody

Type: `object`

Show Source

- force(optional): boolean
  Default Value: `false`
  To remove forcibily.

<!-- -->

    {
        "type":"object",
        "properties":{
            "force":{
                "type":"boolean",
                "default":false,
                "description":"To remove forcibily."
            }
        }
    }

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

OK. A JSON object containing a series resource representation with multiple properties and the links array with at least the "self" link. Only if it was successfully deleted.

Body ()

Root Schema : seriesResource

Type: `object`

Show Source

- imageNames(optional): array imageNames
- links(optional): array links
- seriesId(optional): string
- subscribedUsers(optional): array subscribedUsers

<!-- -->

    {
        "type":"object",
        "properties":{
            "seriesId":{
                "type":"string"
            },
            "imageNames":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "subscribedUsers":{
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

Nested Schema : imageNames

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

Nested Schema : subscribedUsers

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

The following example shows how to delete an image series by submitting a DELETE request on the REST resource using cURL.

    curl -u restUser  -X DELETE "https://RHP_node_name:8894/rhp-restapi/rhp/series/CRM_DB_Serie1"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 200
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 259
    Date:  Tue, 19 Jun 2018 14:03:23 GMT

### Response Body

    {
         "seriesId": "CRM_DB_Serie1",
         "imageNames": ["DB_Image1","DB_Image2"],
         "subscribedUsers": ["grid","oracle"],
         "links": [{
             "uri": "https://RHP_node_name:8894/rhp-restapi/rhp/series/CRM_DB_Serie1",
             "rel": "self"
          }]
    }

Back to Top
