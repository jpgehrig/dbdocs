Create a pluggable database from PDB\$SEED or from an XML metadata file accessible to the database instance. The use of Oracle Transparent Data Encryption is only supported in topologies where the database and Oracle REST Data Services are on the same host. This service requires db.cdb.adminUser credentials to be set in the pool configuration. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Body ()

Root Schema : schema

Type: `object`

Show Source

- adminName(optional): string
  The administrator username for the new PDB. This property is required when the method property is CREATE.
- adminPwd(optional): string
  The administrator password for the new PDB. This property is required when the method property is CREATE.
- asClone(optional): boolean
  Indicate if 'AS CLONE' option should be used in the command to plug in a PDB. This property is applicable when the method property is PLUG but not required.
- copyAction(optional): string
  Allowed Values: `[ "COPY", "NOCOPY", "MOVE" ]`
  Indicate which copy option should be used in the command to plug in a PDB. This property is required when the method property is PLUG.
- fileNameConversions: string
  Relevant for create and plug operations. As defined in the Oracle Multitenant Database documentation. Values can be a filename convert pattern or NONE.
- getScript(optional): boolean
  If defined, the response will contain a JSON object with the information of the script that was generated for execution. A database is not created when this property is set to true.
- method: string
  Allowed Values: `[ "CREATE", "PLUG" ]`
  This property defines the type of operation. Depending on the method specified, other properties will be required in the payload.
- pdb_name: string
  The name of the new PDB. Relevant to both CREATE and PLUG method.
- reuseTempFile(optional): boolean
  Relevant for create and plug operations. True for temporary file reusage.
- sourceFileNameConversions(optional): string
  This property is required when the method property is PLUG. As defined in the Oracle Multitenant Database documentation. Values can be a source filename convert pattern or NONE.
- tdeImport(optional): boolean
  TDE import for plug operations.
- tdeKeystorePath(optional): string
  TDE keystore path is required if the tdeImport flag is set to true. Can be used in plug operations.
- tdePassword(optional): string
  TDE password when applicable (optional). Can be used in create and plug operations.
- tdeSecret(optional): string
  TDE secret is required if the tdeImport flag is set to true. Can be used in plug operations.
- tempSize(optional): string
  Relevant for create and clone operations. Total size for temporary tablespace as defined in the Oracle Multitenant Database documentation. See size_clause description in Database SQL Language Reference documentation.
- totalSize(optional): string
  Relevant for create and plug operations. Total size as defined in the Oracle Multitenant Database documentation. See size_clause description in Database SQL Language Reference documentation.
- unlimitedStorage(optional): boolean
  Relevant for create and plug operations. True for unlimited storage. Even when set to true, totalSize and tempSize MUST be specified in the request if method is CREATE.
- xmlFileName(optional): string
  The path of the XML metadata file to use when plugging-in a PDB.

<!-- -->

    {
        "type":"object",
        "required":[
            "method",
            "pdb_name",
            "fileNameConversions"
        ],
        "properties":{
            "method":{
                "type":"string",
                "description":"This property defines the type of operation. Depending on the method specified, other properties will be required in the payload.",
                "enum":[
                    "CREATE",
                    "PLUG"
                ]
            },
            "adminName":{
                "type":"string",
                "description":"The administrator username for the new PDB. This property is required when the method property is CREATE."
            },
            "adminPwd":{
                "type":"string",
                "description":"The administrator password for the new PDB. This property is required when the method property is CREATE."
            },
            "pdb_name":{
                "type":"string",
                "description":"The name of the new PDB. Relevant to both CREATE and PLUG method."
            },
            "asClone":{
                "type":"boolean",
                "description":"Indicate if 'AS CLONE' option should be used in the command to plug in a PDB. This property is applicable when the method property is PLUG but not required."
            },
            "xmlFileName":{
                "type":"string",
                "description":"The path of the XML metadata file to use when plugging-in a PDB."
            },
            "copyAction":{
                "type":"string",
                "description":"Indicate which copy option should be used in the command to plug in a PDB. This property is required when the method property is PLUG.",
                "enum":[
                    "COPY",
                    "NOCOPY",
                    "MOVE"
                ]
            },
            "sourceFileNameConversions":{
                "type":"string",
                "description":"This property is required when the method property is PLUG. As defined in the Oracle Multitenant Database documentation. Values can be a source filename convert pattern or NONE."
            },
            "fileNameConversions":{
                "type":"string",
                "description":"Relevant for create and plug operations. As defined in the  Oracle Multitenant Database documentation. Values can be a filename convert pattern or NONE."
            },
            "unlimitedStorage":{
                "type":"boolean",
                "description":"Relevant for create and plug operations. True for unlimited storage. Even when set to true, totalSize and tempSize MUST be specified in the request if method is CREATE."
            },
            "reuseTempFile":{
                "type":"boolean",
                "description":"Relevant for create and plug operations. True for temporary file reusage."
            },
            "totalSize":{
                "type":"string",
                "description":"Relevant for create and plug operations. Total size as defined in the Oracle Multitenant Database documentation. See size_clause description in Database SQL Language Reference documentation."
            },
            "tempSize":{
                "type":"string",
                "description":"Relevant for create and clone operations. Total size for temporary tablespace as defined in the Oracle Multitenant Database documentation. See size_clause description in Database SQL Language Reference documentation."
            },
            "tdePassword":{
                "type":"string",
                "description":"TDE password when applicable (optional). Can be used in create and plug operations."
            },
            "tdeImport":{
                "type":"boolean",
                "description":"TDE import for plug operations."
            },
            "tdeKeystorePath":{
                "type":"string",
                "description":"TDE keystore path is required if the tdeImport flag is set to true. Can be used in  plug operations."
            },
            "tdeSecret":{
                "type":"string",
                "description":"TDE secret is required if the tdeImport flag is set to true. Can be used in plug operations."
            },
            "getScript":{
                "type":"boolean",
                "description":"If defined, the response will contain a JSON object with the information of the script that was generated for execution. A database is not created when this property is set to true."
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

The following example shows how to create a new Pluggable Database by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/database/pdbs/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, and the path for this operation. The PDB Lifecycle Management service requires `db.cdb.adminUser` credentials to be set in the pool configuration and in this example, the default pool is configured for the container database.

The following is an example request body to create a pluggable database called `pdb_sample` in this example, from `PDB$SEED` with unlimited storage. In this example, `fileNameConversions` parameter is also provided that results in a `FILE_NAME_CONVERT` clause included in the` CREATE PLUGGABLE DATABASE` statement executed in the container database:

    {
      "method": "CREATE",
      "pdb_name": "pdb_sample",
      "adminName": "pdbadmin",
      "adminPwd": "W3lc0m31",
      "fileNameConversions": "('/disk1/oracle/dbs/pdbseed/','/disk1/oracle/dbs/pdb_sample/')",
      "unlimitedStorage": true,
      "reuseTempFile": true,
      "totalSize": "UNLIMITED",
      "tempSize": "UNLIMITED"
    }

The following is an example request body to get the generated script for creating a pluggable database from `PDB$SEED` with custom storage settings. Note that the script is not executed in the database. In this example, `fileNameConversions` parameter has a `NONE` value that results in a `FILE_NAME_CONVERT=NONE` clause included in the `CREATE PLUGGABLE DATABASE` statement generated.

    {
      "method": "CREATE",
      "pdb_name": "pdb_sample",
      "adminName": "pdbadmin",
      "adminPwd": "W3lc0m31",
      "fileNameConversions": "NONE",
      "reuseTempFile": true,
      "totalSize": "2G",
      "tempSize": "800M",
      "getScript": true
    }

The following is an example request body to plugin a pluggable database called `sales_pdb` into the container database. In this example request body the pluggable database definition is specified in the `sales_pdb.xml` file:

    {
      "method": "PLUG",
      "pdb_name": "sales_pdb",
      "xmlFileName": "/disk1/oracle/dbs/sales_pdb.xml",
      "sourceFileNameConversions": "NONE",
      "copyAction": "NOCOPY",
      "fileNameConversions": "NONE",
      "unlimitedStorage": true,
      "reuseTempFile": true,
      "totalSize": "UNLIMITED",
      "tempSize": "UNLIMITED"
    }

### Example of Response Header

The following example shows the response header:

    HTTP/1.1 200 OK
    Date: Fri, 06 Sep 2019 15:51:31 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 200 returned in JSON format:

    {
        "statementText": "BEGIN\n\tEXECUTE IMMEDIATE 'CREATE PLUGGABLE DATABASE \"pdb_sample\"\n\t\tUSING ''/disk1/oracle/dbs/sales_db.xml''\n\t\tSOURCE_FILE_NAME_CONVERT=NONE\n\t\tNOCOPY\n\t\tSTORAGE UNLIMITED\tTEMPFILE REUSE\n\t';\nEND;\n/\nALTER PLUGGABLE DATABASE \"pdb_sample\" OPEN READ WRITE INSTANCES=ALL\n/\n",
        "binds": []
    }

Back to Top
