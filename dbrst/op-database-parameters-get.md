Return records from GV\$SYSTEM_PARAMETER. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Query Parameters

- limit(optional): integer(int32)
  The maximum number of records to return.
- q(optional): string
  Filtering is the process of limiting a collection resource by using a per-request dynamic filter definition across multiple page resources, where each page contains a subset of items found in the complete collection. Filtering enables efficient traversal of large collections.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of all database parameters.

Body ()

Root Schema : DatabaseParameters

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
                    "$ref":"#/definitions/DatabaseParametersItem"
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

- Array of: object DatabaseParametersItem
  This documentation represents an initialization parameter that is currently in effect for the instance. A new session inherits parameter values from the instance-wide values. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseParametersItem"
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

Nested Schema : DatabaseParametersItem

Type: `object`

This documentation represents an initialization parameter that is currently in effect for the instance. A new session inherits parameter values from the instance-wide values. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- default_value(optional): string
  The default value for this parameter. This is the value of the parameter if a value is not explicitly specified for the parameter.
- description(optional): string
  Description of the parameter.
- display_value(optional): string
  Parameter value in a user-friendly format. For example, if the VALUE column shows the value 262144 for a big integer parameter, then the DISPLAY_VALUE column will show the value 256K.
- hash(optional): integer
  Hash value for the parameter name.
- inst_id(optional): integer
  Instance number from which the associated GV\$SYSTEM_PARAMETER view information was obtained.
- isadjusted(optional): string
  Indicates whether Oracle adjusted the input value to a more suitable value (for example, the parameter value should be prime, but the user input a non-prime number, so Oracle adjusted the value to the next prime number).
- isbasic(optional): string
  Indicates whether the parameter is a basic parameter (TRUE) or not (FALSE).
- isdefault(optional): string
  Indicates whether the parameter is set to the default value (TRUE) or the parameter value was specified in the parameter file (FALSE). The database sets the value of the ISDEFAULT column to TRUE for parameters that are not specified in the init.ora or server parameter file (SPFILE).
- isdeprecated(optional): string
  Indicates whether the parameter has been deprecated (TRUE) or not (FALSE).
- isinstance_modifiable(optional): string
  For parameters that can be changed with ALTER SYSTEM, indicates whether the value of the parameter can be different for every instance (TRUE) or whether the parameter must have the same value for all Real Application Clusters instances (FALSE). If the ISSYS_MODIFIABLE column is FALSE, then this column is always FALSE.
- ismodified(optional): string
  Indicates how the parameter was modified. If an ALTER SYSTEM was performed, the value will be MODIFIED.
- ispdb_modifiable(optional): string
  Indicates whether the parameter can be modified inside a PDB (TRUE) or not (FALSE). In a non-CDB, the value of this column is NULL.
- isses_modifiable(optional): string
  Indicates whether the parameter can be changed with ALTER SESSION (TRUE) or not (FALSE).
- issys_modifiable(optional): string
  Indicates whether the parameter can be changed with ALTER SYSTEM and when the change takes effect.
- links(optional): array links
- name(optional): string
  Name of the parameter.
- num(optional): integer
  Parameter number.
- type(optional): integer
  Parameter type.
- update_comment(optional): string
  Comments associated with the most recent update.
- value(optional): string
  Instance-wide parameter value.

<!-- -->

    {
        "type":"object",
        "description":"This documentation represents an initialization parameter that is currently in effect for the instance. A new session inherits parameter values from the instance-wide values. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$SYSTEM_PARAMETER view information was obtained."
            },
            "num":{
                "type":"integer",
                "description":"Parameter number."
            },
            "name":{
                "type":"string",
                "description":"Name of the parameter."
            },
            "type":{
                "type":"integer",
                "description":"Parameter type."
            },
            "value":{
                "type":"string",
                "description":"Instance-wide parameter value."
            },
            "display_value":{
                "type":"string",
                "description":"Parameter value in a user-friendly format. For example, if the VALUE column shows the value 262144 for a big integer parameter, then the DISPLAY_VALUE column will show the value 256K."
            },
            "default_value":{
                "type":"string",
                "description":"The default value for this parameter. This is the value of the parameter if a value is not explicitly specified for the parameter."
            },
            "isdefault":{
                "type":"string",
                "description":"Indicates whether the parameter is set to the default value (TRUE) or the parameter value was specified in the parameter file (FALSE). The database sets the value of the ISDEFAULT column to TRUE for parameters that are not specified in the init.ora or server parameter file (SPFILE)."
            },
            "isses_modifiable":{
                "type":"string",
                "description":"Indicates whether the parameter can be changed with ALTER SESSION (TRUE) or not (FALSE)."
            },
            "issys_modifiable":{
                "type":"string",
                "description":"Indicates whether the parameter can be changed with ALTER SYSTEM and when the change takes effect."
            },
            "ispdb_modifiable":{
                "type":"string",
                "description":"Indicates whether the parameter can be modified inside a PDB (TRUE) or not (FALSE). In a non-CDB, the value of this column is NULL."
            },
            "isinstance_modifiable":{
                "type":"string",
                "description":"For parameters that can be changed with ALTER SYSTEM, indicates whether the value of the parameter can be different for every instance (TRUE) or whether the parameter must have the same value for all Real Application Clusters instances (FALSE). If the ISSYS_MODIFIABLE column is FALSE, then this column is always FALSE."
            },
            "ismodified":{
                "type":"string",
                "description":"Indicates how the parameter was modified. If an ALTER SYSTEM was performed, the value will be MODIFIED."
            },
            "isadjusted":{
                "type":"string",
                "description":"Indicates whether Oracle adjusted the input value to a more suitable value (for example, the parameter value should be prime, but the user input a non-prime number, so Oracle adjusted the value to the next prime number)."
            },
            "isdeprecated":{
                "type":"string",
                "description":"Indicates whether the parameter has been deprecated (TRUE) or not (FALSE)."
            },
            "isbasic":{
                "type":"string",
                "description":"Indicates whether the parameter is a basic parameter (TRUE) or not (FALSE)."
            },
            "description":{
                "type":"string",
                "description":"Description of the parameter."
            },
            "update_comment":{
                "type":"string",
                "description":"Comments associated with the most recent update."
            },
            "hash":{
                "type":"integer",
                "description":"Hash value for the parameter name."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
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
