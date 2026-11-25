Returns the DBCA log file content from the DBCA job created through ORDS Database API in the specified Oracle Home. The Oracle Home is specified by \$ORACLE_HOME environment variable. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- jobId: string
  Identifier of the DBCA job.

Back to Top

### Response

Supported Media Types

- text/plain

#### 200 Response

Log file content from the DBCA jobs created in the default Oracle Home.

Body ()

Root Schema : schema

Type: `string`

Back to Top
