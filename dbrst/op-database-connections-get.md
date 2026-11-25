Returns LOCAL LISTENER and SERVICE NAME records from GV\$LISTENER_NETWORK for this database. A client requires SQL Administrator role to invoke this service.

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

All the local listeners for this database.

Body ()

Root Schema : DatabaseConnections

Type: `object`

Information on the listeners configured for the database is retrieved from GV\$LISTENER_NETWORK.

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
        "description":"Information on the listeners configured for the database is retrieved from GV$LISTENER_NETWORK.",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/DatabaseConnectionsItem"
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

- Array of: object DatabaseConnectionsItem
  Information on the listeners configured for the database is retrieved from GV\$LISTENER_NETWORK. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseConnectionsItem"
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

Nested Schema : DatabaseConnectionsItem

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
