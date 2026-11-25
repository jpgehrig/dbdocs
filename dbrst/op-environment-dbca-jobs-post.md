Submit a new Database Configuration Assistant (DBCA) job request to CREATE or DELETE a database in the Oracle Home specified by \$ORACLE_HOME environment variable. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Body ()

A payload for creating a DBCA job.

Root Schema : schema

Type: `object`

Show Source

- container_configuration(optional): object container_configuration
  This object specifies that a Container Database is to be created with the PDB settings provided.
- global_database_name: string
  Global Database Name to identify the database to create or delete
- operation: string
  Allowed Values: `[ "CREATE", "DELETE" ]`
  The DBCA operation to perform.
- password(optional): string
  Specifies the password for the account with SYSDBA role which DBCA will use to delete the database. Only required for DELETE operations.
- response_file(optional): string
  The name of the response file for DBCA to use when creating a database.
- sys_user_password(optional): string
  The password for the sys user in the new database.
- system_user_password(optional): string
  The password for the system user in the new database.
- template_name(optional): string
  The name of the template file for DBCA to use when creating a database.
- total_memory(optional): integer
  Total amount of physical memory, in megabytes, that can be used by the new database.
- username(optional): string
  Specifies the account with SYSDBA role which DBCA will use to delete the database. Only required for DELETE operations.

<!-- -->

    {
        "type":"object",
        "required":[
            "operation",
            "global_database_name"
        ],
        "properties":{
            "operation":{
                "type":"string",
                "description":"The DBCA operation to perform.",
                "enum":[
                    "CREATE",
                    "DELETE"
                ]
            },
            "global_database_name":{
                "type":"string",
                "description":"Global Database Name to identify the database to create or delete"
            },
            "template_name":{
                "type":"string",
                "description":"The name of the template file for DBCA to use when creating a database."
            },
            "response_file":{
                "type":"string",
                "description":"The name of the response file for DBCA to use when creating a database."
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
            },
            "username":{
                "type":"string",
                "description":"Specifies the account with SYSDBA role which DBCA will use to delete the database. Only required for DELETE operations."
            },
            "password":{
                "type":"string",
                "description":"Specifies the password for the account with SYSDBA role which DBCA will use to delete the database. Only required for DELETE operations."
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

#### 201 Response

Description of the new DBCA job.

Body ()

Root Schema : EnvironmentDbcaJobsItem

Type: `object`

Describes a Database Configuration Assistant job.

Show Source

- dbca_log(optional): array dbca_log
  The output from the DBCA process as it executes.
- description(optional): string
  DBCA job description.
- finished(optional): string
  Timestamp for when the DBCA job request finished.
- job_id(optional): string
  Unique identifier for the DBCA job in the Oracle Home.
- job_request(optional): object job_request
  Describes the DBCA job request.
- links(optional): array links
- status(optional): string
  DBCA job status.
- submitted(optional): string
  Timestamp for when the DBCA job request was submitted.

<!-- -->

    {
        "type":"object",
        "description":"Describes a Database Configuration Assistant job.",
        "properties":{
            "job_id":{
                "type":"string",
                "description":"Unique identifier for the DBCA job in the Oracle Home."
            },
            "description":{
                "type":"string",
                "description":"DBCA job description."
            },
            "status":{
                "type":"string",
                "description":"DBCA job status."
            },
            "submitted":{
                "type":"string",
                "description":"Timestamp for when the DBCA job request was submitted."
            },
            "finished":{
                "type":"string",
                "description":"Timestamp for when the DBCA job request finished."
            },
            "job_request":{
                "type":"object",
                "description":"Describes the DBCA job request.",
                "properties":{
                    "operation":{
                        "type":"string",
                        "description":"The DBCA operation to be performed: CREATE or DELETE."
                    },
                    "container_configuration":{
                        "type":"object",
                        "description":"This object represents container configuration details for a CDB.",
                        "properties":{
                            "number_of_pdbs":{
                                "type":"string",
                                "description":"Number of PDBs to create."
                            },
                            "pdb_name":{
                                "type":"string",
                                "description":"Base name of each PDB. A number is appended to each name if number_of_pdbs is greater than 1."
                            }
                        }
                    },
                    "database_system_identifier":{
                        "type":"string",
                        "description":"The database identifier."
                    },
                    "global_database_name":{
                        "type":"string",
                        "description":"Global database name."
                    },
                    "response_file":{
                        "type":"string",
                        "description":"Path for response file for DBCA to use when creating a database."
                    },
                    "template_name":{
                        "type":"string",
                        "description":"Path for the database template for DBCA to use when creating a database."
                    },
                    "total_memory":{
                        "type":"string",
                        "description":"Total memory parameter to provide to DBCA when creating a database."
                    },
                    "username":{
                        "type":"string",
                        "description":"The sysdba username for DBCA to use when deleting a database."
                    }
                }
            },
            "dbca_log":{
                "type":"array",
                "description":"The output from the DBCA process as it executes.",
                "items":{
                    "type":"string"
                }
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : dbca_log

Type: `array`

The output from the DBCA process as it executes.

Show Source

- Array of: string

<!-- -->

    {
        "type":"array",
        "description":"The output from the DBCA process as it executes.",
        "items":{
            "type":"string"
        }
    }

Nested Schema : job_request

Type: `object`

Describes the DBCA job request.

Show Source

- container_configuration(optional): object container_configuration
  This object represents container configuration details for a CDB.
- database_system_identifier(optional): string
  The database identifier.
- global_database_name(optional): string
  Global database name.
- operation(optional): string
  The DBCA operation to be performed: CREATE or DELETE.
- response_file(optional): string
  Path for response file for DBCA to use when creating a database.
- template_name(optional): string
  Path for the database template for DBCA to use when creating a database.
- total_memory(optional): string
  Total memory parameter to provide to DBCA when creating a database.
- username(optional): string
  The sysdba username for DBCA to use when deleting a database.

<!-- -->

    {
        "type":"object",
        "description":"Describes the DBCA job request.",
        "properties":{
            "operation":{
                "type":"string",
                "description":"The DBCA operation to be performed: CREATE or DELETE."
            },
            "container_configuration":{
                "type":"object",
                "description":"This object represents container configuration details for a CDB.",
                "properties":{
                    "number_of_pdbs":{
                        "type":"string",
                        "description":"Number of PDBs to create."
                    },
                    "pdb_name":{
                        "type":"string",
                        "description":"Base name of each PDB. A number is appended to each name if number_of_pdbs is greater than 1."
                    }
                }
            },
            "database_system_identifier":{
                "type":"string",
                "description":"The database identifier."
            },
            "global_database_name":{
                "type":"string",
                "description":"Global database name."
            },
            "response_file":{
                "type":"string",
                "description":"Path for response file for DBCA to use when creating a database."
            },
            "template_name":{
                "type":"string",
                "description":"Path for the database template for DBCA to use when creating a database."
            },
            "total_memory":{
                "type":"string",
                "description":"Total memory parameter to provide to DBCA when creating a database."
            },
            "username":{
                "type":"string",
                "description":"The sysdba username for DBCA to use when deleting a database."
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : container_configuration

Type: `object`

This object represents container configuration details for a CDB.

Show Source

- number_of_pdbs(optional): string
  Number of PDBs to create.
- pdb_name(optional): string
  Base name of each PDB. A number is appended to each name if number_of_pdbs is greater than 1.

<!-- -->

    {
        "type":"object",
        "description":"This object represents container configuration details for a CDB.",
        "properties":{
            "number_of_pdbs":{
                "type":"string",
                "description":"Number of PDBs to create."
            },
            "pdb_name":{
                "type":"string",
                "description":"Base name of each PDB. A number is appended to each name if number_of_pdbs is greater than 1."
            }
        }
    }

Nested Schema : LinkRelation

Type: `object`

Show Source

- href: string
- rel: string

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string"
            },
            "href":{
                "type":"string"
            }
        },
        "required":[
            "rel",
            "href"
        ]
    }

Back to Top

### Examples

The following example shows how to submit a new DBCA job in the default Oracle Home by submitting a POST request on the REST resource using cURL. The DBCA job can be a request to create or delete a database in the default Oracle Home.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, and the path for this operation.

The following is an example request body to create a DBCA job for creating a non-container database. The non-container database is called `devdb1` based on the `General_Purpose.dbc` template, and the total amount of physical memory used by the new databaase is 700mb.

    {
      "operation": "CREATE",
      "global_database_name": "devdb1",
      "template_name": "General_Purpose.dbc",
      "sys_user_password": "W3lc0m31",
      "system_user_password": "W3lc0m31",
      "total_memory": 700
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the DBCA job status.

    HTTP/1.1 201 Created
    Content-Type: application/json
    Content-Location: https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/OzQbsGnbUhVV7w7fiYPbJQ/
    X-Frame-Options: SAMEORIGIN
    Location: https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/OzQbsGnbUhVV7w7fiYPbJQ/
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 201 returned in JSON format:

    {
      "job_id": "OzQbsGnbUhVV7w7fiYPbJQ",
      "description": "Run DBCA to create database",
      "status": "RUNNING",
      "submitted": "2019-09-06T19:17:23.004Z",
      "finished": null,
      "job_request": {
        "operation": "CREATE",
        "container_configuration": null,
        "database_system_identifier": null,
        "global_database_name": "devdb1",
        "response_file": null,
        "template_name": "General_Purpose.dbc",
        "total_memory": 700,
        "username": null
      },
      "dbca_log": [],
      "links": [
        {
          "rel": "self",
          "href": "https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/OzQbsGnbUhVV7w7fiYPbJQ/"
        },
        {
          "rel": "describedby",
          "href": "https://rest_server_url/ords/_/db-api/stable/metadata-catalog/"
        },
        {
          "rel": "collection",
          "href": "https://rest_server_url/ords/_/db-api/stable/environment/dbca/jobs/"
        }
      ]
    }

Back to Top
