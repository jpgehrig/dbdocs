Returns records from DBA_FEATURE_USAGE_STATISTICS for a specific feature. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- dbid: number
  Database identifier as found in GV\$DATABASE.
- name: string
  Name of the feature.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on the usage statistics for a specific feature.

Body ()

Root Schema : DatabaseFeatureUsageItem

Type: `object`

Statistics on the usage in the database for an Oracle Database feature.

Show Source

- aux_count(optional): integer
  This column stores feature-specific usage data in number format.
- currently_used(optional): string
  Indicates whether usage was detected the last time the system checked (TRUE) or not (FALSE).
- dbid(optional): integer
  Database identifier of the database being tracked.
- description(optional): string
  Description of the feature and usage detection logic.
- detected_usages(optional): integer
  Number of times the system has detected usage for the feature.
- feature_info(optional): string
  This column stores feature-specific usage data in character format.
- first_usage_date(optional): string
  First sample time the system detected usage of the feature.
- last_sample_date(optional): string
  The last time the system checked for usage.
- last_sample_period(optional): integer
  Amount of time (in seconds) between the last two usage sample times.
- last_usage_date(optional): string
  Last sample time the system detected usage of the feature.
- links(optional): array links
- name(optional): string
  Name of the feature.
- sample_interval(optional): integer
  Sample interval.
- total_samples(optional): integer
  Number of times the system has woken up and checked for feature usage.
- version(optional): string
  Database version in which the feature was tracked.

<!-- -->

    {
        "type":"object",
        "description":"Statistics on the usage in the database for an Oracle Database feature.",
        "properties":{
            "dbid":{
                "type":"integer",
                "description":"Database identifier of the database being tracked."
            },
            "name":{
                "type":"string",
                "description":"Name of the feature."
            },
            "version":{
                "type":"string",
                "description":"Database version in which the feature was tracked."
            },
            "detected_usages":{
                "type":"integer",
                "description":"Number of times the system has detected usage for the feature."
            },
            "total_samples":{
                "type":"integer",
                "description":"Number of times the system has woken up and checked for feature usage."
            },
            "currently_used":{
                "type":"string",
                "description":"Indicates whether usage was detected the last time the system checked (TRUE) or not (FALSE)."
            },
            "first_usage_date":{
                "type":"string",
                "description":"First sample time the system detected usage of the feature."
            },
            "last_usage_date":{
                "type":"string",
                "description":"Last sample time the system detected usage of the feature."
            },
            "aux_count":{
                "type":"integer",
                "description":"This column stores feature-specific usage data in number format."
            },
            "feature_info":{
                "type":"string",
                "description":"This column stores feature-specific usage data in character format."
            },
            "last_sample_date":{
                "type":"string",
                "description":"The last time the system checked for usage."
            },
            "last_sample_period":{
                "type":"integer",
                "description":"Amount of time (in seconds) between the last two usage sample times."
            },
            "sample_interval":{
                "type":"integer",
                "description":"Sample interval."
            },
            "description":{
                "type":"string",
                "description":"Description of the feature and usage detection logic."
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
