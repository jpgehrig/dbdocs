Create a Data Pump export job with the specified parameters and start it. Refer to Oracle Data Pump documentation for a more detailed explanation of parameters. A client requires SQL Administrator role to invoke this service.

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
- filter(optional): string
  The filter to apply to identify database objects for export. Required when job_mode is not FULL.
- job_mode(optional): string
  Default Value: `SCHEMA`
  Allowed Values: `[ "FULL", "SCHEMA", "TABLE", "TABLESPACE" ]`
  Specify the Data Pump job mode.
- name_expressions(optional): array name_expressions
  Used to define Metadata Filter parameters for a Data Pump job.
- schema_expressions(optional): array schema_expressions
  Used to define Metadata Filter parameters for a Data Pump job.
- tablespace_expressions(optional): array tablespace_expressions
  Used to define Metadata Filter parameters for a Data Pump job.
- threads(optional): integer
  The maximum number of worker processes that can be used for the job. Set this parameter to adjust the amount of resources used for a job.

<!-- -->

    {
        "type":"object",
        "properties":{
            "datapump_dir":{
                "type":"string",
                "description":"Specify the database directory to use.",
                "default":"DATA_PUMP_DIR"
            },
            "filter":{
                "type":"string",
                "description":"The filter to apply to identify database objects for export. Required when job_mode is not FULL."
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
            "threads":{
                "type":"integer",
                "description":"The maximum number of worker processes that can be used for the job. Set this parameter to adjust the amount of resources used for a job."
            },
            "name_expressions":{
                "type":"array",
                "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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
                "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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
                "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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

Used to define Metadata Filter parameters for a Data Pump job.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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

Nested Schema : schema_expressions

Type: `array`

Used to define Metadata Filter parameters for a Data Pump job.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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

Used to define Metadata Filter parameters for a Data Pump job.

Show Source

- Array of: object items

<!-- -->

    {
        "type":"array",
        "description":"Used to define Metadata Filter parameters for a Data Pump job.",
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

Description of the Data Pump export job that has been created.

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

The following example shows how to create a Data Pump export job by submitting a POST request on the REST resource using cURL.

    curl -i -X POST -u username:password
    -d @request_body.json
    -H "Content-Type:application/json" https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/export

### Example of Request Body

**Note:**

The URL structure `https://rest_server_url/resource-path`, used in the preceding command has the following components:

- `rest_server_url` is the REST server where Oracle Rest Data Server is running
- The remainder of the URL includes the ORDS context root, the database identifier, the schema identifier, the version of ORDS Database API to use, and the path for this operation.

The following is an example of a request body for submitting a Data Pump request to export tables beginning with EMP, but not named EMP, from the SCOTT schema.

    {
      "job_mode": "TABLE",
      "name_expressions": [
        {"expression": "!='EMP'"},
        {"expression": "LIKE 'EMP%'"}
      ],
      "schema_expressions": [
        {"expression": "IN ('SCOTT')"}
      ]
    }

### Example of Response Header

The following example shows the response header. The `Location` header returns the URI that can be used to view the status of the job.

    HTTP/1.1 201 Created
    Content-Type:"application/json"
    Content-Location:"https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190706144505/"
    ETag:""nXEnxxIZe/tJIO5rgD+qkCggJtIVIMvKJG6T2dqhJ8Wy2Cr5u+anrmgez/2+3BWR3FKx0TlVjR2RRfITHZnFxQ==""
    Location:"https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190907144505/"
    Transfer-Encoding:"chunked"

### Example of Response Body

The following example shows the response body with 201 returned in JSON format:

    {
        "job_name": "DATAPUMP_REST_EXPORT_20190706144505",
        "owner_name": "PDBADMIN",
        "operation": "EXPORT",
        "job_mode": "TABLE",
        "state": "EXECUTING",
        "degree": 1,
        "attached_sessions": 0,
        "datapump_sessions": 2,
        "job_state": "EXECUTING",
        "links": [
            {
                "rel": "collection",
                "href": "https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/"
            },
            {
                "rel": "describedby",
                "href": "https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/metadata-catalog/"
            },
            {
                "rel": "related",
                "href": "https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190706144505/EXPDAT-2019-07-06-14_45_05.LOG"
            },
            {
                "rel": "self",
                "href": "https://rest_server_url/ords/orcl/pdbadmin/_/db-api/stable/database/datapump/jobs/PDBADMIN,DATAPUMP_REST_EXPORT_20190706144505/"
            }
        ]
    }

Back to Top
