Gets the job output representing the job result and progress, which can be paginated using the limit and offset parameters.

### Request

Supported Media Types

- application/json

Path Parameters

- jobId: string
  Unique integer job ID value for the scheduled job.

Query Parameters

- limit(optional): integer
  The number of lines from the job result to be included in the job output resource.
  Default Value: `0`
- offset(optional): integer
  The identifier of the first line on the job result to be included in the job output resource.
  Default Value: `0`

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

OK. A JSON object containing a job output resource representation with multiple properties and the links array with at least the "self" link.

Body ()

Root Schema : jobOutputResource

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

The following example shows how to view the results and output of an existing job by submitting a GET request on the REST resource using cURL.

    curl -u restUser -X GET "https://RHP_node_name:8894/rhp-restapi/rhp/jobs/1/output"

### HTTP Status Code and Response Headers

The following shows an example of the response header.

    HTTP/1.1 200
    Access-Control-Allow-Origin: *
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: GET,PUT,POST,DELETE,PATCH,OPTIONS
    Access-Control-Allow-Headers: X-Requested-With, Content-Type, Content-Length, Authorization
    Connection: keep-alive
    Content-Type: application/json
    Content-Length: 556
    Date:  Tue, 19 Jun 2018 14:03:23 GMT

### Response Body

    {
           "output" : "nodeName.domain.com: Audit ID: 6\nnodeName.domain.com: Creating a new ACFS file system for image "DB_Image1" ...\nnodeName.domain.com: Copying files...\nnodeName.domain.com: Copying home contents...\nnodeName.domain.com: Changing the home ownership to user aime1...\nnodeName.domain.com: Changing the home ownership to user aime1...",
           "offset" : 0,
           "limit" : 6,
           "hasMore" : no,
           "links" : [{
                "uri" : "http://RHP_node_name:8894/rhp-restapi/rhp/jobs/1/output",
                "rel" : "self"
           }]
    }

Back to Top
