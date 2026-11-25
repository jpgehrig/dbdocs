Get all resource limits for sessions using GV\$RESOURCE_LIMIT view. Since GV\$RESOURCE_LIMIT exposes global level information, it can only be queried from CDB\$ROOT or in a non-CDB database. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

All session limits in the database.

Body ()

Root Schema : MonitoringSessionLimitsItem

Type: `object`

This object is used to monitor the consumption of session resources in the database. Since GV\$RESOURCE_LIMIT exposes global/ CDB level information, it can only be queried from CDB\$ROOT or in a non-CDB database. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- current_utilization(optional): integer
  Number of (resources, locks, or processes) currently being used.
- initial_allocation(optional): string
  Initial allocation. This will be equal to the value specified for the resource in the initialization parameter file (UNLIMITED for infinite allocation).
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- limit_value(optional): string
  The maximum value of utilization that will be allowed.
- links(optional): array links
- max_utilization(optional): integer
  Maximum consumption of this resource since the last instance start-up.
- resource_name(optional): string
  Name of the resource. This will always be session in this case.

<!-- -->

    {
        "type":"object",
        "description":"This object is used to monitor the consumption of session resources in the database. Since GV$RESOURCE_LIMIT exposes global/ CDB level information, it can only be queried from CDB$ROOT or in a non-CDB database. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "resource_name":{
                "type":"string",
                "description":"Name of the resource. This will always be session in this case."
            },
            "current_utilization":{
                "type":"integer",
                "description":"Number of (resources, locks, or processes) currently being used."
            },
            "max_utilization":{
                "type":"integer",
                "description":"Maximum consumption of this resource since the last instance start-up."
            },
            "initial_allocation":{
                "type":"string",
                "description":"Initial allocation. This will be equal to the value specified for the resource in the initialization parameter file (UNLIMITED for infinite allocation)."
            },
            "limit_value":{
                "type":"string",
                "description":"The maximum value of utilization that will be allowed."
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
