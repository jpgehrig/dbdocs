Returns records from GV\$INSTANCE and GV\$DATABASE. A client requires SQL Administrator role to invoke this service.

### Request

There are no request parameters for this operation.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Description of the database state.

Body ()

Root Schema : DatabaseStatusItem

Type: `object`

Relying on GV\$INSTANCE and GV\$DATABASE views this object provides information on the status of the database.

Show Source

- active_state(optional): string
  Quiesce state of the instance.
- archiver(optional): string
  Automatic archiving status.
- blocked(optional): string
  Indicates whether all services are blocked (YES) or not (NO).
- con_id(optional): integer
  The ID of the container to which the data pertains.
- database_status(optional): string
  Status of the database.
- database_type(optional): string
  Database type.
- db_unique_name(optional): string
  Unique database name.
- edition(optional): string
  The edition of the database.
- host_name(optional): string
  Name of the host machine.
- inst_id(optional): integer
  Instance number from which the associated GV\$INSTANCE view information was obtained.
- instance_mode(optional): string
  Shows the instance mode of the current instance.
- instance_name(optional): string
  Name of the instance.
- instance_number(optional): integer
  Instance number used for instance registration (corresponds to the INSTANCE_NUMBER initialization parameter).
- instance_role(optional): string
  Indicates whether the instance is an active instance (PRIMARY_INSTANCE) or an inactive secondary instance (SECONDARY_INSTANCE), or UNKNOWN if the instance has been started but not mounted.
- links(optional): array links
- log_switch_wait(optional): string
  Event that log switching is waiting for.
- logins(optional): string
  Indicates whether the instance is in unrestricted mode, allowing logins by all users (ALLOWED, or in restricted mode, allowing logins by database administrators only (RESTRICTED).
- name(optional): string
  Name of the database.
- open_mode(optional): string
  Open mode information.
- parallel(optional): string
  Indicates whether the instance is mounted in cluster database mode (YES) or not (NO).
- shutdown_pending(optional): string
  Indicates whether a shutdown is pending (YES) or not (NO).
- startup_time(optional): string
  Time when the instance was started.
- status(optional): string
  Status of the instance.
- thread#(optional): integer
  Redo thread opened by the instance.
- version(optional): string
  Database version.
- version_full(optional): string
  The version string with the new Oracle Database version scheme introduced in Oracle Database 18c.
- version_legacy(optional): string
  The legacy database version used before Oracle Database 18c. This column displays the same value as the VERSION column.

<!-- -->

    {
        "type":"object",
        "description":"Relying on GV$INSTANCE and GV$DATABASE views this object provides information on the status of the database.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$INSTANCE view information was obtained."
            },
            "instance_number":{
                "type":"integer",
                "description":"Instance number used for instance registration (corresponds to the INSTANCE_NUMBER initialization parameter)."
            },
            "instance_name":{
                "type":"string",
                "description":"Name of the instance."
            },
            "host_name":{
                "type":"string",
                "description":"Name of the host machine."
            },
            "version":{
                "type":"string",
                "description":"Database version."
            },
            "version_legacy":{
                "type":"string",
                "description":"The legacy database version used before Oracle Database 18c. This column displays the same value as the VERSION column."
            },
            "version_full":{
                "type":"string",
                "description":"The version string with the new Oracle Database version scheme introduced in Oracle Database 18c."
            },
            "startup_time":{
                "type":"string",
                "description":"Time when the instance was started."
            },
            "status":{
                "type":"string",
                "description":"Status of the instance."
            },
            "parallel":{
                "type":"string",
                "description":"Indicates whether the instance is mounted in cluster database mode (YES) or not (NO)."
            },
            "thread#":{
                "type":"integer",
                "description":"Redo thread opened by the instance."
            },
            "archiver":{
                "type":"string",
                "description":"Automatic archiving status."
            },
            "log_switch_wait":{
                "type":"string",
                "description":"Event that log switching is waiting for."
            },
            "logins":{
                "type":"string",
                "description":"Indicates whether the instance is in unrestricted mode, allowing logins by all users (ALLOWED, or in restricted mode, allowing logins by database administrators only (RESTRICTED)."
            },
            "shutdown_pending":{
                "type":"string",
                "description":"Indicates whether a shutdown is pending (YES) or not (NO)."
            },
            "database_status":{
                "type":"string",
                "description":"Status of the database."
            },
            "instance_role":{
                "type":"string",
                "description":"Indicates whether the instance is an active instance (PRIMARY_INSTANCE) or an inactive secondary instance (SECONDARY_INSTANCE), or UNKNOWN if the instance has been started but not mounted."
            },
            "active_state":{
                "type":"string",
                "description":"Quiesce state of the instance."
            },
            "blocked":{
                "type":"string",
                "description":"Indicates whether all services are blocked (YES) or not (NO)."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "instance_mode":{
                "type":"string",
                "description":"Shows the instance mode of the current instance."
            },
            "edition":{
                "type":"string",
                "description":"The edition of the database."
            },
            "database_type":{
                "type":"string",
                "description":"Database type."
            },
            "name":{
                "type":"string",
                "description":"Name of the database."
            },
            "db_unique_name":{
                "type":"string",
                "description":"Unique database name."
            },
            "open_mode":{
                "type":"string",
                "description":"Open mode information."
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
