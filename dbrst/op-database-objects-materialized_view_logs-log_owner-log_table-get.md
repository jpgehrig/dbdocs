Returns the corresponding record from DBA_MVIEW_LOGS or ALL_MVIEW_LOGS view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- log_owner: string
  Owner for the materialized view log.
- log_table: string
  Log table for the materialized view log.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific materialized view log.

Body ()

Root Schema : DatabaseObjectsMaterializedViewLogsItem

Type: `object`

This object describes a materialized view log in the database.

Show Source

- commit_scn_based(optional): string
  Indicates whether the materialized view log is commit SCN-based (YES) or not (NO).
- filter_columns(optional): string
  Indicates whether filter column information is recorded (YES) or not (NO).
- include_new_values(optional): string
  Indicates whether both old and new values are recorded (YES) or old values are recorded but new values are not recorded (NO).
- last_purge_date(optional): string
  Date of the last purge.
- last_purge_status(optional): integer
  Status of the last purge (error code or 0 for success).
- links(optional): array links
- log_owner(optional): string
  Owner of the materialized view log.
- log_table(optional): string
  Name of the table where the changes to the master table or master materialized view are logged.
- master(optional): string
  Name of the master table or master materialized view whose changes are logged.
- num_rows_purged(optional): integer
  Number of rows purged in the last purge.
- object_id(optional): string
  Indicates whether object identifier information in an object table is recorded (YES) or not (NO).
- primary_key(optional): string
  Indicates whether primary key information is recorded (YES) or not (NO).
- purge_asynchronous(optional): string
  Indicates whether the materialized view log is purged asynchronously (YES) or not (NO).
- purge_deferred(optional): string
  Indicates whether the materialized view log is purged in a deferred manner (YES) or not (NO).
- purge_interval(optional): string
  For deferred purge, the purge interval.
- purge_start(optional): string
  For deferred purge, the purge start date.
- rowids(optional): string
  Indicates whether rowid information is recorded (YES) or not (NO).
- sequence(optional): string
  Indicates whether the sequence value, which provides additional ordering information, is recorded (YES) or not (NO).
- staging_log(optional): string
  Indicates whether the materialized view log is a staging log for synchronous refresh (YES) or not (NO).

<!-- -->

    {
        "type":"object",
        "description":"This object describes a materialized view log in the database.",
        "properties":{
            "log_owner":{
                "type":"string",
                "description":"Owner of the materialized view log."
            },
            "master":{
                "type":"string",
                "description":"Name of the master table or master materialized view whose changes are logged."
            },
            "log_table":{
                "type":"string",
                "description":"Name of the table where the changes to the master table or master materialized view are logged."
            },
            "rowids":{
                "type":"string",
                "description":"Indicates whether rowid information is recorded (YES) or not (NO)."
            },
            "primary_key":{
                "type":"string",
                "description":"Indicates whether primary key information is recorded (YES) or not (NO)."
            },
            "object_id":{
                "type":"string",
                "description":"Indicates whether object identifier information in an object table is recorded (YES) or not (NO)."
            },
            "filter_columns":{
                "type":"string",
                "description":"Indicates whether filter column information is recorded (YES) or not (NO)."
            },
            "sequence":{
                "type":"string",
                "description":"Indicates whether the sequence value, which provides additional ordering information, is recorded (YES) or not (NO)."
            },
            "include_new_values":{
                "type":"string",
                "description":"Indicates whether both old and new values are recorded (YES) or old values are recorded but new values are not recorded (NO)."
            },
            "purge_asynchronous":{
                "type":"string",
                "description":"Indicates whether the materialized view log is purged asynchronously (YES) or not (NO)."
            },
            "purge_deferred":{
                "type":"string",
                "description":"Indicates whether the materialized view log is purged in a deferred manner (YES) or not (NO)."
            },
            "purge_start":{
                "type":"string",
                "description":"For deferred purge, the purge start date."
            },
            "purge_interval":{
                "type":"string",
                "description":"For deferred purge, the purge interval."
            },
            "last_purge_date":{
                "type":"string",
                "description":"Date of the last purge."
            },
            "last_purge_status":{
                "type":"integer",
                "description":"Status of the last purge (error code or 0 for success)."
            },
            "num_rows_purged":{
                "type":"integer",
                "description":"Number of rows purged in the last purge."
            },
            "commit_scn_based":{
                "type":"string",
                "description":"Indicates whether the materialized view log is commit SCN-based (YES) or not (NO)."
            },
            "staging_log":{
                "type":"string",
                "description":"Indicates whether the materialized view log is a staging log for synchronous refresh (YES) or not (NO)."
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
