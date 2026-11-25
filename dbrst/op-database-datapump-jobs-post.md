Create a Data Pump job with the specified parameters and start it. Refer to Oracle Data Pump documentation for a more detailed explanation of parameters. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Body ()

Root Schema : schema

Type: `object`

Show Source

- datapump_dir(optional): string
  Default Value: `DATA_PUMP_DIR`
  Specify the database directory to use.
- file_name(optional): string
  The file name pattern to use for Data Pump import. Required when operation is IMPORT.
- filter(optional): string
  The filter to apply to identify database objects for export. This an export convenience for simple lists in metadata filter parameters, carried over from 19.1 implementation.
- job_mode(optional): string
  Default Value: `SCHEMA`
  Allowed Values: `[ "FULL", "SCHEMA", "TABLE", "TABLESPACE" ]`
  Specify the Data Pump job mode.
- name_expressions(optional): array name_expressions
  Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.
- operation: string
  Allowed Values: `[ "EXPORT", "IMPORT" ]`
  Specify the Data Pump job operation.
- remap_schemas(optional): array remap_schemas
  Used to define Remap Schema parameters for an import job. Only applicable for IMPORT.
- schema_expressions(optional): array schema_expressions
  Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.
- tablespace_expressions(optional): array tablespace_expressions
  Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.
- threads(optional): integer
  The maximum number of worker processes that can be used for the job. Set this parameter to adjust the amount of resources used for a job.

<!-- -->

    {
        "type":"object",
        "required":[
            "operation"
        ],
        "properties":{
            "operation":{
                "type":"string",
                "description":"Specify the Data Pump job operation.",
                "enum":[
                    "EXPORT",
                    "IMPORT"
                ]
            },
            "datapump_dir":{
                "type":"string",
                "description":"Specify the database directory to use.",
                "default":"DATA_PUMP_DIR"
            },
            "filter":{
                "type":"string",
                "description":"The filter to apply to identify database objects for export. This an export convenience for simple lists in metadata filter parameters, carried over from 19.1 implementation."
            },
            "job_mode":{
                "type":"string",
                "description":"Specify the Data Pump job mode.",
                "default":"SCHEMA",
                "enum":[
                    "FULL",
                    "SCHEMA",
                    "TABLE",
                    "TABLESPACE"
                ]
            },
            "file_name":{
                "type":"string",
                "description":"The file name pattern to use for Data Pump import. Required when operation is IMPORT."
            },
            "threads":{
                "type":"integer",
                "description":"The maximum number of worker processes that can be used for the job. Set this parameter to adjust the amount of resources used for a job."
            },
            "remap_schemas":{
                "type":"array",
                "description":"Used to define Remap Schema parameters for an import job. Only applicable for IMPORT.",
                "items":{
                    "type":"object",
                    "required":[
                        "source",
                        "target"
                    ],
                    "properties":{
                        "source":{
                            "type":"string",
                            "description":"Source schema to remap from."
                        },
                        "target":{
                            "type":"string",
                            "description":"Target schema to remap to."
                        }
                    }
                }
            },
            "name_expressions":{
                "type":"array",
                "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
                "items":{
                    "type":"object",
                    "required":[
                        "expression"
                    ],
                    "properties":{
                        "expression":{
                            "type":"string",
                            "description":"An SQL clause to be used as a Name Expression filter."
                        }
                    }
                }
            },
            "schema_expressions":{
                "type":"array",
                "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
                "items":{
                    "type":"object",
                    "required":[
                        "expression"
                    ],
                    "properties":{
                        "expression":{
                            "type":"string",
                            "description":"An SQL clause to be used as a Schema Expression filter."
                        }
                    }
                }
            },
            "tablespace_expressions":{
                "type":"array",
                "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
                "items":{
                    "type":"object",
                    "required":[
                        "expression"
                    ],
                    "properties":{
                        "expression":{
                            "type":"string",
                            "description":"An SQL clause to be used as a Tablespace Expression filter."
                        }
                    }
                }
            }
        }
    }

Nested Schema : name_expressions

Type: `array`

Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
        "items":{
            "type":"object",
            "required":[
                "expression"
            ],
            "properties":{
                "expression":{
                    "type":"string",
                    "description":"An SQL clause to be used as a Name Expression filter."
                }
            }
        }
    }

Nested Schema : remap_schemas

Type: `array`

Used to define Remap Schema parameters for an import job. Only applicable for IMPORT.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Remap Schema parameters for an import job. Only applicable for IMPORT.",
        "items":{
            "type":"object",
            "required":[
                "source",
                "target"
            ],
            "properties":{
                "source":{
                    "type":"string",
                    "description":"Source schema to remap from."
                },
                "target":{
                    "type":"string",
                    "description":"Target schema to remap to."
                }
            }
        }
    }

Nested Schema : schema_expressions

Type: `array`

Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
        "items":{
            "type":"object",
            "required":[
                "expression"
            ],
            "properties":{
                "expression":{
                    "type":"string",
                    "description":"An SQL clause to be used as a Schema Expression filter."
                }
            }
        }
    }

Nested Schema : tablespace_expressions

Type: `array`

Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job. Applicable for both EXPORT and IMPORT.",
        "items":{
            "type":"object",
            "required":[
                "expression"
            ],
            "properties":{
                "expression":{
                    "type":"string",
                    "description":"An SQL clause to be used as a Tablespace Expression filter."
                }
            }
        }
    }

Nested Schema : items

Type: `object`

Show Source

- expression: string
  An SQL clause to be used as a Name Expression filter.

<!-- -->

    {
        "type":"object",
        "required":[
            "expression"
        ],
        "properties":{
            "expression":{
                "type":"string",
                "description":"An SQL clause to be used as a Name Expression filter."
            }
        }
    }

Nested Schema : items

Type: `object`

Show Source

- source: string
  Source schema to remap from.
- target: string
  Target schema to remap to.

<!-- -->

    {
        "type":"object",
        "required":[
            "source",
            "target"
        ],
        "properties":{
            "source":{
                "type":"string",
                "description":"Source schema to remap from."
            },
            "target":{
                "type":"string",
                "description":"Target schema to remap to."
            }
        }
    }

Nested Schema : items

Type: `object`

Show Source

- expression: string
  An SQL clause to be used as a Schema Expression filter.

<!-- -->

    {
        "type":"object",
        "required":[
            "expression"
        ],
        "properties":{
            "expression":{
                "type":"string",
                "description":"An SQL clause to be used as a Schema Expression filter."
            }
        }
    }

Nested Schema : items

Type: `object`

Show Source

- expression: string
  An SQL clause to be used as a Tablespace Expression filter.

<!-- -->

    {
        "type":"object",
        "required":[
            "expression"
        ],
        "properties":{
            "expression":{
                "type":"string",
                "description":"An SQL clause to be used as a Tablespace Expression filter."
            }
        }
    }

Back to Top

### Response

Supported Media Types

- application/json

#### 201 Response

Details of the Data Pump job that has been successfully created.

Body ()

Root Schema : DataPumpJobsItem

Type: `object`

This object represents a specified Data Pump job in the database.

Show Source

- attached_sessions(optional): integer
  Number of sessions attached to the job.
- datapump_sessions(optional): integer
  Number of Data Pump sessions participating in the job.
- degree(optional): integer
  Number of worker processes performing the operation.
- job_mode(optional): string
  Mode of job.
- job_name(optional): string
  User-supplied name for the job (or the default name generated by the server).
- links(optional): array links
- operation(optional): string
  Type of job.
- owner_name(optional): string
  User that initiated the job.
- state(optional): string
  Current job state.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a specified Data Pump job in the database.",
        "properties":{
            "owner_name":{
                "type":"string",
                "description":"User that initiated the job."
            },
            "job_name":{
                "type":"string",
                "description":"User-supplied name for the job (or the default name generated by the server)."
            },
            "operation":{
                "type":"string",
                "description":"Type of job."
            },
            "job_mode":{
                "type":"string",
                "description":"Mode of job."
            },
            "state":{
                "type":"string",
                "description":"Current job state."
            },
            "degree":{
                "type":"integer",
                "description":"Number of worker processes performing the operation."
            },
            "attached_sessions":{
                "type":"integer",
                "description":"Number of sessions attached to the job."
            },
            "datapump_sessions":{
                "type":"integer",
                "description":"Number of Data Pump sessions participating in the job."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
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

The following example shows how to create a Data Pump job by submitting a POST request on the REST resource using cURL. Depending on the operation specified in the request body, the Data Pump job can be an import or an export job.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the database identifier, the schema identifier, the version of ORDS Database API to use, and the path for this operation.

The following is an example of a request body for submitting a Data Pump request to export the `HR` schema.

    {
      "operation": "EXPORT",
      "schema_expressions": [
        {
          "expression": "IN ( 'HR' )"
        }
      ]
    }

The following is an example of a request body for submitting a Data Pump request to import the `HR` schema and map it to the `BLAKE` schema.

    {
      "operation": "IMPORT",
      "job_mode": "FULL",
      "file_name": "EXPDAT%U2019-03-25-12_55_03.DMP",
      "remap_schemas": [
        {
          "source": "HR",
          "target": "BLAKE"
        }
      ]
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the status of the job.

    HTTP/1.1 201 Created
    Content-Type: application/json
    Content-Location: https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190906155736/
    ETag: "vdgVbEWipm96TpCidc5nFeC3BHMZd7adx8m4liaYSTEb7IwPVRykFAld4YP4Yh/PBuJ2Kv3fywyTvJykxERaEw=="
    Location: http://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190906155736/
    Transfer-Encoding: chunked

### Example of Response Body

The following example shows the response body with 201 returned in JSON format:

    {
        "job_name": "DATAPUMP_REST_EXPORT_20190906155736",
        "owner_name": "PDBADMIN",
        "operation": "EXPORT",
        "job_mode": "SCHEMA",
        "state": "EXECUTING",
        "degree": 1,
        "attached_sessions": 0,
        "datapump_sessions": 2,
        "job_state": "EXECUTING",
        "links": [
            {
                "rel": "collection",
                "href": "http://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/"
            },
            {
                "rel": "describedby",
                "href": "http://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/metadata-catalog/"
            },
            {
                "rel": "related",
                "href": "http://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190906155736/EXPDAT-2019-09-06-15_57_36.LOG"
            },
            {
                "rel": "self",
                "href": "http://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190906155736/"
            }
        ]
    }

Back to Top
