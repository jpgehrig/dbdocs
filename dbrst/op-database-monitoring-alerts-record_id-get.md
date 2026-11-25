Returns specific alert record from V\$DIAG_ALERT_EXT. In an Oracle RAC environment, data returned by this service may vary according to the instance to which a session is connected. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- record_id: number
  Identifier for the alert record.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific alert.

Body ()

Root Schema : MonitoringAlertsItem

Type: `object`

This object represents an alert log record from V\$DIAG_ALERT_EXT. V\$DIAG_ALERT_EXT shows the contents of the XML-based alert log in the Automatic Diagnostic Repository (ADR). The list of attributes may vary depending on database version.

Show Source

- adr_home(optional): string
  Directory location of the Automatic Diagnostic Repository (ADR).
- client_id(optional): string
  ID of the client or security group that the message relates to.
- component_id(optional): string
  ID of the product or component that originated the message.
- con_id(optional): integer
  The ID of the container to which the data pertains.
- detailed_location(optional): string
  Absolute pathname of supplemental detail file on the originating host.
- downstream_comp_id(optional): string
  ID of a component that the originating component is working with on the downstream (server) side.
- error_instance_id(optional): integer
  ID of the instance where error occurred.
- error_instance_sequence(optional): integer
  Instance sequence where error occurred.
- execution_context_id(optional): string
  Identifies the thread of execution that the originating component participates in.
- execution_context_sequence(optional): integer
  Execution sequence of the thread that the originating component participates in.
- filename(optional): string
  Physical file on disk.
- host_address(optional): string
  IP of other network address of the originating host for the message.
- host_id(optional): string
  DNS hostname of originating host.
- links(optional): array links
- message_arguments(optional): string
  Arguments to be bound with the generic text of the message.
- message_group(optional): string
  Name of the group to which the message belongs.
- message_id(optional): string
  ID of the message.
- message_level(optional): integer
  Level the message belongs to. Lower level values imply higher severity for errors.
- message_level_name(optional): string
  A text description of the corresponding message level value.
- message_text(optional): string
  Fully formed and localized text of the message.
- message_type(optional): integer
  Type of the message, indicating that a different type of response is required.
- message_type_name(optional): string
  A text description of the corresponding message type value.
- module_id(optional): string
  ID of the module that originated the message. This value is unique within a component.
- normalized_timestamp(optional): string
  Date and time when the message originated, normalized for clock drift to the Oracle Enterprise Manager repository time.
- organization_id(optional): string
  ID of the organization that wrote the originating component, usually the domain of the organization.
- originating_timestamp(optional): string
  Date and time when the message was generated.
- partition(optional): integer
  Segment number of physical file.
- problem_key(optional): string
  Describes the key for the current problem that the message is associated with.
- process_id(optional): string
  ID of the process that originated the message.
- record_id(optional): integer
  Record number for the message (this value is same as the row number).
- supplemental_attributes(optional): string
  Supplemental attributes that are specific to a message. This field contains the impacts for an incident type error message.
- supplemental_details(optional): string
  Supplemental data that is specific to a particular program and error message required to complete the diagnosis.
- thread_id(optional): string
  ID of the thread of the process that originated the message.
- upstream_comp_id(optional): string
  ID of a component that the originating component is working with on the upstream (client) side.
- user_id(optional): string
  ID of the user that originated the message.
- version(optional): integer
  Oracle ARB logging standard version number for the message.

<!-- -->

    {
        "type":"object",
        "description":"This object represents an alert log record from V$DIAG_ALERT_EXT. V$DIAG_ALERT_EXT shows the contents of the XML-based alert log in the Automatic Diagnostic Repository (ADR). The list of attributes may vary depending on database version.",
        "properties":{
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "adr_home":{
                "type":"string",
                "description":"Directory location of the Automatic Diagnostic Repository (ADR)."
            },
            "originating_timestamp":{
                "type":"string",
                "description":"Date and time when the message was generated."
            },
            "normalized_timestamp":{
                "type":"string",
                "description":"Date and time when the message originated, normalized for clock drift to the Oracle Enterprise Manager repository time."
            },
            "organization_id":{
                "type":"string",
                "description":"ID of the organization that wrote the originating component, usually the domain of the organization."
            },
            "component_id":{
                "type":"string",
                "description":"ID of the product or component that originated the message."
            },
            "host_id":{
                "type":"string",
                "description":"DNS hostname of originating host."
            },
            "host_address":{
                "type":"string",
                "description":"IP of other network address of the originating host for the message."
            },
            "message_type":{
                "type":"integer",
                "description":"Type of the message, indicating that a different type of response is required."
            },
            "message_type_name":{
                "type":"string",
                "description":"A text description of the corresponding message type value."
            },
            "message_level":{
                "type":"integer",
                "description":"Level the message belongs to. Lower level values imply higher severity for errors."
            },
            "message_level_name":{
                "type":"string",
                "description":"A text description of the corresponding message level value."
            },
            "message_id":{
                "type":"string",
                "description":"ID of the message."
            },
            "message_group":{
                "type":"string",
                "description":"Name of the group to which the message belongs."
            },
            "client_id":{
                "type":"string",
                "description":"ID of the client or security group that the message relates to."
            },
            "module_id":{
                "type":"string",
                "description":"ID of the module that originated the message. This value is unique within a component."
            },
            "process_id":{
                "type":"string",
                "description":"ID of the process that originated the message."
            },
            "thread_id":{
                "type":"string",
                "description":"ID of the thread of the process that originated the message."
            },
            "user_id":{
                "type":"string",
                "description":"ID of the user that originated the message."
            },
            "detailed_location":{
                "type":"string",
                "description":"Absolute pathname of supplemental detail file on the originating host."
            },
            "upstream_comp_id":{
                "type":"string",
                "description":"ID of a component that the originating component is working with on the upstream (client) side."
            },
            "downstream_comp_id":{
                "type":"string",
                "description":"ID of a component that the originating component is working with on the downstream (server) side."
            },
            "execution_context_id":{
                "type":"string",
                "description":"Identifies the thread of execution that the originating component participates in."
            },
            "execution_context_sequence":{
                "type":"integer",
                "description":"Execution sequence of the thread that the originating component participates in."
            },
            "error_instance_id":{
                "type":"integer",
                "description":"ID of the instance where error occurred."
            },
            "error_instance_sequence":{
                "type":"integer",
                "description":"Instance sequence where error occurred."
            },
            "message_text":{
                "type":"string",
                "description":"Fully formed and localized text of the message."
            },
            "message_arguments":{
                "type":"string",
                "description":"Arguments to be bound with the generic text of the message."
            },
            "supplemental_attributes":{
                "type":"string",
                "description":"Supplemental attributes that are specific to a message. This field contains the impacts for an incident type error message."
            },
            "supplemental_details":{
                "type":"string",
                "description":"Supplemental data that is specific to a particular program and error message required to complete the diagnosis."
            },
            "partition":{
                "type":"integer",
                "description":"Segment number of physical file."
            },
            "record_id":{
                "type":"integer",
                "description":"Record number for the message (this value is same as the row number)."
            },
            "filename":{
                "type":"string",
                "description":"Physical file on disk."
            },
            "problem_key":{
                "type":"string",
                "description":"Describes the key for the current problem that the message is associated with."
            },
            "version":{
                "type":"integer",
                "description":" Oracle ARB logging standard version number for the message."
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
