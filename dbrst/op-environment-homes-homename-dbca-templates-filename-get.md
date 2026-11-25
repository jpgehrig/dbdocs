Returns the database template file in the specified Oracle Home. The Oracle Home is on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- filename: string
  Name of the database template file.
- homeName: string
  Name of the Oracle Home.

Back to Top

### Response

Supported Media Types

- text/XML

#### 200 Response

The XML content of the database template file.

Body ()

Root Schema : schema

Type: `string`

Back to Top
