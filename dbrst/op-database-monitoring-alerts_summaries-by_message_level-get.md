Group by message level on V\$DIAG_ALERT_EXT. In an Oracle RAC environment, data returned by this service may vary according to the instance to which a session is connected. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Summary of alerts, brokedown by message level.

Body ()

Root Schema : MonitoringAlertsSummaryMessageLevelItem

Type: `object`

This object represents a summary of V\$DIAG_ALERT_EXT records by message level. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- inst_id(optional): integer
  Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1.
- latest_messages(optional): string
  The text of the last 5 messages at this message level.
- links(optional): array links
- message_level(optional): integer
  Level the message belongs to. Lower level values imply higher severity for errors.
- message_level_name(optional): string
  A text description of the corresponding message level value.
- number_of_messages(optional): integer
  The count of records that have this message level.

<!-- -->

    {
        "type":"object",
        "description":"This object represents a summary of V$DIAG_ALERT_EXT records by message level. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Oracle Real Application Clusters instance number for which this data relates to. In a non-RAC database this number will be 1."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "message_level":{
                "type":"integer",
                "description":"Level the message belongs to. Lower level values imply higher severity for errors."
            },
            "message_level_name":{
                "type":"string",
                "description":"A text description of the corresponding message level value."
            },
            "number_of_messages":{
                "type":"integer",
                "description":"The count of records that have this message level."
            },
            "latest_messages":{
                "type":"string",
                "description":"The text of the last 5 messages at this message level."
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
