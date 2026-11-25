Submit a new DBCA job request to CREATE or DELETE a database in the Oracle Home specified. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

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

The following example shows how to submit a new DBCA job in the specified Oracle Home by submitting a POST request on the REST resource using cURL. The DBCA job can be a request to create or delete a database in the specified Oracle Home.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/dbca/jobs/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the version of ORDS Database API to use, the path for this operation. `OraDB18Home1` is given as the `homeName` parameter value in the path. All DBCA operations are performed in Oracle Home.

The following is an example request body to create a DBCA job for deleting a database. To perform the delete action, the credentials for a user in the database with SYSDBA role must be provided as these are required by the DBCA utility.

    {
      "operation": "DELETE",
      "global_database_name": "devdb1",
      "username": "sys",
      "password": "W3lc0m31"
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the DBCA job status.

    HTTP/1.1 201 Created
    Content-Type: application/json
    Content-Location: https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/dbca/jobs/RPKlPvbKPKqV7Ap6DN9iRg/
    X-Frame-Options: SAMEORIGIN
    Location: https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/dbca/jobs/RPKlPvbKPKqV7Ap6DN9iRg/
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 201 returned in a JSON format:

    {
      "job_id": "RPKlPvbKPKqV7Ap6DN9iRg",
      "description": "Running DBCA to Delete database",
      "status": "RUNNING",
      "submitted": "2019-09-06T19:30:06.981Z",
      "finished": null,
      "job_request": {
        "operation": "DELETE",
        "container_configuration": null,
        "database_system_identifier": null,
        "global_database_name": "devdb1",
        "response_file": null,
        "template_name": null,
        "total_memory": null,
        "username": "sys"
      },
      "dbca_log": [],
      "links": [
        {
          "rel": "self",
          "href": "https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/dbca/jobs/RPKlPvbKPKqV7Ap6DN9iRg/"
        },
        {
          "rel": "describedby",
          "href": "https://rest_server_url/ords/_/db-api/stable/metadata-catalog/"
        },
        {
          "rel": "collection",
          "href": "https://rest_server_url/ords/_/db-api/stable/environment/homes/OraDB18Home1/dbca/jobs/"
        }
      ]
    }

Back to Top
