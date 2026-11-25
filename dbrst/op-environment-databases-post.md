Create a new database in the Oracle Home specified by \$ORACLE_HOME environment variable. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Body ()

A payload for creating a database.

Root Schema : schema

Type: `object`

Show Source

- container_configuration(optional): object container_configuration
  This object specifies that a Container Database is to be created with the PDB settings provided.
- global_database_name(optional): string
  Global Database Name.
- response_file(optional): string
  The name of the response file for DBCA to use.
- sys_user_password(optional): string
  The password for the sys user in the new database.
- system_user_password(optional): string
  The password for the system user in the new database.
- template_name(optional): string
  The name of the template file for DBCA to use.
- total_memory(optional): integer
  Total amount of physical memory, in megabytes, that can be used by the new database.

<!-- -->

    {
        "type":"object",
        "properties":{
            "global_database_name":{
                "type":"string",
                "description":"Global Database Name."
            },
            "template_name":{
                "type":"string",
                "description":"The name of the template file for DBCA to use."
            },
            "response_file":{
                "type":"string",
                "description":"The name of the response file for DBCA to use."
            },
            "system_user_password":{
                "type":"string",
                "description":"The password for the system user in the new database."
            },
            "sys_user_password":{
                "type":"string",
                "description":"The password for the sys user in the new database."
            },
            "container_configuration":{
                "type":"object",
                "description":"This object specifies that a Container Database is to be created with the PDB settings provided.",
                "items":{
                    "type":"object",
                    "required":[
                        "number_of_pdbs",
                        "pdb_administrator_password",
                        "pdb_name"
                    ],
                    "properties":{
                        "number_of_pdbs":{
                            "type":"integer",
                            "description":"The number of Pluggable Databases to create."
                        },
                        "pdb_administrator_password":{
                            "type":"string",
                            "description":"The password for the PDBADMIN user created in each Pluggable Database."
                        },
                        "pdb_name":{
                            "type":"string",
                            "description":"The name prefix to use for each Pluggable Database created."
                        }
                    }
                }
            },
            "total_memory":{
                "type":"integer",
                "description":"Total amount of physical memory, in megabytes, that can be used by the new database."
            }
        }
    }

Nested Schema : container_configuration

Type: `object`

This object specifies that a Container Database is to be created with the PDB settings provided.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"object",
        "description":"This object specifies that a Container Database is to be created with the PDB settings provided.",
        "items":{
            "type":"object",
            "required":[
                "number_of_pdbs",
                "pdb_administrator_password",
                "pdb_name"
            ],
            "properties":{
                "number_of_pdbs":{
                    "type":"integer",
                    "description":"The number of Pluggable Databases to create."
                },
                "pdb_administrator_password":{
                    "type":"string",
                    "description":"The password for the PDBADMIN user created in each Pluggable Database."
                },
                "pdb_name":{
                    "type":"string",
                    "description":"The name prefix to use for each Pluggable Database created."
                }
            }
        }
    }

Nested Schema : items

Type: `object`

Show Source

- number_of_pdbs: integer
  The number of Pluggable Databases to create.
- pdb_administrator_password: string
  The password for the PDBADMIN user created in each Pluggable Database.
- pdb_name: string
  The name prefix to use for each Pluggable Database created.

<!-- -->

    {
        "type":"object",
        "required":[
            "number_of_pdbs",
            "pdb_administrator_password",
            "pdb_name"
        ],
        "properties":{
            "number_of_pdbs":{
                "type":"integer",
                "description":"The number of Pluggable Databases to create."
            },
            "pdb_administrator_password":{
                "type":"string",
                "description":"The password for the PDBADMIN user created in each Pluggable Database."
            },
            "pdb_name":{
                "type":"string",
                "description":"The name prefix to use for each Pluggable Database created."
            }
        }
    }

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

The following example shows how to create a new database in the default Oracle Home by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/environment/databases/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, and the path for this operation.

The following is an example request body to create a container database with two pluggable databases in the default Oracle Home. The `General_Purpose.dbc` template file from the Oracle Home dbca templates directory is used. `container_configuration` property is provided in the request to indicate that a container database is to be created. The container database name `devcdb1` and the pluggable database names are pdbtest1 and pdbtest2 in this scenario. The response to this request will be the location of the DBCA job that has been created to process the request.

    {
      "global_database_name": "devcdb1",
      "template_name": "General_Purpose.dbc",
      "sys_user_password": "W3lc0m31",
      "system_user_password": "W3lc0m31",
      "container_configuration": {
        "number_of_pdbs": 2,
        "pdb_name": "pdbtest",
        "pdb_administrator_password": "W3lc0m31"
      }
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the DBCA job status:

    HTTP/1.1 202 Accepted
    Date: Fri, 06 Sep 2019 18:17:26 GMT
    X-Frame-Options: SAMEORIGIN
    Location: https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/Cuq5Mm190gZgvXlwJITEIw/
    Transfer-Encoding: chunked

### Example of Response Body

When a create database request is valid and accepted, the response body is empty. The response header contains the necessary information for the DBCA job.

Back to Top
