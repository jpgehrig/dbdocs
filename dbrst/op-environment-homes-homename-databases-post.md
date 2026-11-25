Create a new database in the Oracle Home. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- homeName: string
  Name of the Oracle Home.

Back to Top

### Response

Supported Media Types

- application/json

#### 202 Response

Request to create a new databases has been accepted.

Headers

- Location: string
  Location header will provide URI of DBCA job so that processing of the request can be tracked.

Back to Top

### Examples

The following example shows how to create a new database in the specified Oracle Home by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/databases/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, and the path for this operation. `OraDB18Home1` is given as the `homeName` parameter value in the path. All DBCA operations are performed in Oracle Home.

The following is an example request body to create a non-container database. The non-container database is called `devdb1` based on the `General_Purpose.dbc` template, and a predefined response file used to set additional configuration properties. The response to this request will be the location of the DBCA job that has been created to process the request.

    {
      "global_database_name": "devdb1",
      "template_name": "General_Purpose.dbc",
      "sys_user_password": "W3lc0m31",
      "system_user_password": "W3lc0m31",
      "response_file": "/disk1/oracle/install_oracle_for_dev.rsp"
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the DBCA job status.

    HTTP/1.1 202 Accepted
    Date: Fri, 06 Sep 2019 18:17:26 GMT
    X-Frame-Options: SAMEORIGIN
    Location: https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/Buq5Mm395gZgvXlwPFRSJv/
    Transfer-Encoding: chunked

### Example of Response Body

When a create database request is valid and accepted, the response body is empty. The response header contains the necessary information for the DBCA job.

Back to Top
