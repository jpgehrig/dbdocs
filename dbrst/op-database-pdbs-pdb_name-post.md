Clone or Unplug a PDB. These operations have a significant impact on the specified pluggable databases. The unplug operation will delete the PDB. Note that when cloning a pluggable database, the state of the source database will temporarily be set to OPEN READ ONLY for the duration of the operation and reset to its original state. The use of of Oracle Transparent Data Encryption is only supported in topologies where the database and Oracle REST Data Services are on the same host. This service requires db.cdb.adminUser credentials to be set in the pool configuration. ORA- errors need to be reviewed by the user. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- pdb_name: string
  Name of the Pluggable Database to clone from or unplug.

Body ()

Root Schema : schema

Type: `object`

Show Source

- clonePDBName(optional): string
  The name of the new clone PDB. Required when method is specified as CLONE.
- fileNameConversions(optional): string
  Relevant for clone operations. As defined in the Oracle Multitenant Database documentation.
- getScript(optional): boolean
  If defined, the response will contain a JSON object with the information of the script that was generated for execution. No action is taken when this property is true and only the script text is returned.
- method: string
  Allowed Values: `[ "CLONE", "UNPLUG" ]`
  This property defines the type of operation. Note that CLONE may change the state of the source PDB and UNPLUG will result in the PDB being dropped.
- pdb_name(optional): string
  Source PDB in case of clone or the PDB to be unplugged in case of an unplug operation. This property is optional and the name defined in the URI takes priority.
- reuseTempFile(optional): boolean
  Relevant for clone operations. True for temporary file reusage.
- sparseClonePath(optional): string
  A Path specified for sparse clone snapshot copy. (Optional)
- tdeExport(optional): boolean
  TDE export for unplug operations.
- tdeKeystorePath(optional): string
  TDE keystore path is required if the tdeExport flag is set to true. Can be used in unplug operations only.
- tdePassword(optional): string
  TDE password for unplug operations only. This is required when the tdeExport flag is set to true.
- tdeSecret(optional): string
  TDE secret is required if the tdeExport flag is set to true. Can be used in unplug operations only.
- tempSize(optional): string
  Relevant for clone operations. Size of the temporary tablespace. See size_clause description in Database SQL Language Reference documentation.
- totalSize(optional): string
  Relevant for clone operations. Size of the tablespace. See size_clause description in Database SQL Language Reference documentation.
- unlimitedStorage(optional): boolean
  Relevant for clone operations. True for unlimited storage. Even when set to true, totalSize and tempSize MUST be specified in the request if method is CLONE.
- xmlFileName(optional): string
  Relevant for Unplug operations.

<!-- -->

    {
        "type":"object",
        "required":[
            "method"
        ],
        "properties":{
            "method":{
                "type":"string",
                "description":"This property defines the type of operation. Note that CLONE may change the state of the source PDB and UNPLUG will result in the PDB being dropped.",
                "enum":[
                    "CLONE",
                    "UNPLUG"
                ]
            },
            "pdb_name":{
                "type":"string",
                "description":"Source PDB in case of clone or the PDB to be unplugged in case of an unplug operation. This property is optional and the name defined in the URI takes priority."
            },
            "sparseClonePath":{
                "type":"string",
                "description":"A Path specified for sparse clone snapshot copy. (Optional)"
            },
            "clonePDBName":{
                "type":"string",
                "description":"The name of the new clone PDB. Required when method is specified as CLONE."
            },
            "fileNameConversions":{
                "type":"string",
                "description":"Relevant for clone operations. As defined in the Oracle Multitenant Database documentation."
            },
            "unlimitedStorage":{
                "type":"boolean",
                "description":"Relevant for clone operations. True for unlimited storage. Even when set to true, totalSize and tempSize MUST be specified in the request if method is CLONE."
            },
            "reuseTempFile":{
                "type":"boolean",
                "description":"Relevant for clone operations. True for temporary file reusage."
            },
            "totalSize":{
                "type":"string",
                "description":"Relevant for clone operations. Size of the tablespace. See size_clause description in Database SQL Language Reference documentation."
            },
            "tempSize":{
                "type":"string",
                "description":"Relevant for clone operations. Size of the temporary tablespace. See size_clause description in Database SQL Language Reference documentation."
            },
            "xmlFileName":{
                "type":"string",
                "description":"Relevant for Unplug operations."
            },
            "tdeExport":{
                "type":"boolean",
                "description":"TDE export for unplug operations."
            },
            "tdePassword":{
                "type":"string",
                "description":"TDE password for unplug operations only. This is required when the tdeExport flag is set to true."
            },
            "tdeKeystorePath":{
                "type":"string",
                "description":"TDE keystore path is required if the tdeExport flag is set to true. Can be used in unplug operations only."
            },
            "tdeSecret":{
                "type":"string",
                "description":"TDE secret is required if the tdeExport flag is set to true. Can be used in unplug operations only."
            },
            "getScript":{
                "type":"boolean",
                "description":"If defined, the response will contain a JSON object with the information of the script that was generated for execution. No action is taken when this property is true and only the script text is returned."
            }
        }
    }

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

The response will indicate the successful execution of a series of PL/SQL statements, or return a set of PL/SQL statements that could be executed to create a pluggable database.

Body ()

Root Schema : RESTSQLCollection

Type: `object`

Show Source

- env(optional): string
- items(optional): array items

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/SQLItem"
                }
            },
            "env":{
                "type":"string"
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object SQLItem

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/SQLItem"
        }
    }

Nested Schema : SQLItem

Type: `object`

Show Source

- response(optional): array response
- result(optional): integer
- statementId(optional): integer

<!-- -->

    {
        "type":"object",
        "properties":{
            "statementId":{
                "type":"integer"
            },
            "response":{
                "type":"array",
                "items":{
                    "type":"string"
                }
            },
            "result":{
                "type":"integer"
            }
        }
    }

Nested Schema : response

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

Back to Top

### Examples

The following example shows how to clone a pluggable database or unplug a pluggable database by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/database/pdbs/devpdb1/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, the path for this operation and the PDB identifier `devpdb1`. The pdb_name path parameter in this example is devpdb1. The PDB Lifecycle Management service requires the credentials of `db.cdb.adminUser` to be set in the pool configuration and in this example the default pool is configured for the container database.

The following is an example request body to create a new pluggable database by cloning the pluggable database specified by the `pdb_name` parameter in the URL. In this example, `fileNameConversions` parameter is also provided that results in a `FILE_NAME_CONVERT` clause included in the `CREATE PLUGGABLE DATABASE` statement executed in the container database.

    {
      "method": "CLONE",
      "clonePDBName": "pdb_new",
      "fileNameConversions": "('/disk1/oracle/dbs/devpdb1/','/disk1/oracle/dbs/pdb_new/')",
      "unlimitedStorage": true,
      "reuseTempFile": true,
      "totalSize": "UNLIMITED",
      "tempSize": "UNLIMITED"
    }

The following is an example request body to unplug the database specified by the `pdb_name` parameter in the URL. The pluggable database `devpdb1`, is disassociated from the container database and so will not be usable. An XML file, `sales_pdb.xml` in this example is generated with metadata about the pluggable database after it is unplugged. This metadata contains the required information to enable a `CREATE PLUGGABLE DATABASE` statement on a target container database to plug in the pluggable database.

    {
      "method": "UNPLUG",
      "xmlFileName": "/disk1/oracle/dbs/sales_pdb.xml"
    }

### Example of Response Header

The following example shows the response header:

    HTTP/1.1 200 OK
    Date: Thu, 05 Sep 2019 12:21:01 PDT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 200 returned in JSON format:

    {
      "env":{"defaultTimeZone":"PST8PDT"},
      "items":[
        {
          "statementId":1,
          "response":["\nPL\/SQL procedure successfully completed.\n\n"],
          "result":0
        }
      ]
    }

Back to Top
