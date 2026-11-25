Delete the DBCA job in the Oracle Home specified by \$ORACLE_HOME environment variable. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- homeName: string
  Name of the Oracle Home.
- jobId: string
  Identifier of the DBCA job.

Back to Top

### Response

Supported Media Types

- application/json

#### 204 Response

Confirmation that the DBCA job has been delete.

Back to Top
