Returns LOCAL LISTENER and SERVICE NAME information from GV\$LISTENER_NETWORK for a specific host, port, and service combination. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- host_name: string
  Name of the host.
- port: number
  Port number being listened on.
- service_name: string
  Name of the service.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific listener and service.

Body ()

Root Schema : DatabaseConnectionsItem

Type: `object`

Information on the listeners configured for the database is retrieved from GV\$LISTENER_NETWORK. The list of attributes may vary depending on database version.

Show Source

- con_id(optional): integer
  The ID of the container to which the data pertains.
- host_name(optional): string
  Name of the host machine.
- inst_id(optional): integer
  Instance number from which the associated GV\$LISTENER_NETWORK view information was obtained.
- links(optional): array links
- port(optional): integer
  The TCP/IP port the listener is using.
- service_name(optional): string
  Name of the database service that is registered with the listener.

<!-- -->

    {
        "type":"object",
        "description":"Information on the listeners configured for the database is retrieved from GV$LISTENER_NETWORK. The list of attributes may vary depending on database version.",
        "properties":{
            "inst_id":{
                "type":"integer",
                "description":"Instance number from which the associated GV$LISTENER_NETWORK view information was obtained."
            },
            "host_name":{
                "type":"string",
                "description":"Name of the host machine."
            },
            "con_id":{
                "type":"integer",
                "description":"The ID of the container to which the data pertains."
            },
            "service_name":{
                "type":"string",
                "description":"Name of the database service that is registered with the listener."
            },
            "port":{
                "type":"integer",
                "description":"The TCP/IP port the listener is using."
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
