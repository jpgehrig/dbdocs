Returns a description of all DBCA jobs created through ORDS Database API in the specified Oracle Home. This Oracle Home is expected to be on the same host as the Oracle REST Data Services server instance. A client requires System Administrator role to invoke this service.

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

#### 200 Response

Description of all DBCA jobs created in the Oracle Home.

Body ()

Root Schema : EnvironmentDbcaJobs

Type: `object`

Show Source

- count(optional): integer
  Total number of records in the current response.
- hasMore(optional): boolean
  Indicates if there are more records to be retrieved.
- items(optional): array items
- limit(optional): integer
  The actual page size limit on number of records applied by the server.
- links(optional): array links
- offset(optional): integer
  The actual index from which the item resources are returned.

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/EnvironmentDbcaJobsItem"
                }
            },
            "hasMore":{
                "type":"boolean",
                "description":"Indicates if there are more records to be retrieved."
            },
            "limit":{
                "type":"integer",
                "description":"The actual page size limit on number of records applied by the server."
            },
            "offset":{
                "type":"integer",
                "description":"The actual index from which the item resources are returned."
            },
            "count":{
                "type":"integer",
                "description":"Total number of records in the current response."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object EnvironmentDbcaJobsItem
  Describes a Database Configuration Assistant job.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/EnvironmentDbcaJobsItem"
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

Nested Schema : EnvironmentDbcaJobsItem

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
