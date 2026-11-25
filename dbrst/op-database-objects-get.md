Returns all records from DBA_OBJECTS or ALL_OBJECTS depending on the role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

All database objects in the database. Returns records from DBA_OBJECTS or ALL_OBJECTS.

Body ()

Root Schema : DatabaseObjects

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
                    "$ref":"#/definitions/DatabaseObjectsItem"
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

- Array of: object DatabaseObjectsItem
  A description of an object in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsItem"
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

Nested Schema : DatabaseObjectsItem

Type: `object`

A description of an object in the database.

Show Source

- application(optional): string
  Indicates whether the object is an Application common object (Y) or not (N).
- created(optional): string
  Timestamp for the creation of the object.
- created_appid(optional): integer
  ID of the Application that created the object.
- created_vsnid(optional): integer
  ID of the Application Version that created the object.
- data_object_id(optional): integer
  Dictionary object number of the segment that contains the object.
- default_collation(optional): string
  Default collation for the object.
- duplicated(optional): string
  Indicates whether this object is duplicated on this shard (Y) or not (N).
- edition_name(optional): string
  Name of the edition in which the object is actual.
- editionable(optional): string
  Indicates if the object editionable in the database.
- generated(optional): string
  Indicates whether the name of this object was system-generated (Y) or not (N).
- last_ddl_time(optional): string
  Timestamp for the last modification of the object and dependent objects resulting from a DDL statement (including grants and revokes).
- links(optional): array links
- modified_appid(optional): integer
  ID of the Application that last modified the object.
- modified_vsnid(optional): integer
  ID of the Application Version that last modified the object.
- namespace(optional): integer
  Namespace for the object.
- object_id(optional): integer
  Dictionary object number of the object.
- object_name(optional): string
  Name of the object.
- object_type(optional): string
  Type of the object (such as TABLE, INDEX).
- oracle_maintained(optional): string
  Denotes whether the object was created, and is maintained, by Oracle-supplied scripts (such as catalog.sql or catproc.sql). An object for which this column has the value Y must not be changed in any way except by running an Oracle-supplied script.
- owner(optional): string
  Owner of the object.
- secondary(optional): string
  Indicates whether this is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N).
- sharded(optional): string
  Indicates whether this object is sharded (Y) or not (N).
- sharing(optional): string
  Indicates if the object is a metadata-linked, data-linked or not linked.
- status(optional): string
  Status of the object.
- subobject_name(optional): string
  Name of the subobject (for example, partition).
- temporary(optional): string
  Indicates whether the object is temporary (the current session can see only data that it placed in this object itself) (Y) or not (N).
- timestamp(optional): string
  Timestamp for the specification of the object (character data).

<!-- -->

    {
        "type":"object",
        "description":"A description of an object in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the object."
            },
            "object_name":{
                "type":"string",
                "description":"Name of the object."
            },
            "subobject_name":{
                "type":"string",
                "description":"Name of the subobject (for example, partition)."
            },
            "object_id":{
                "type":"integer",
                "description":"Dictionary object number of the object."
            },
            "data_object_id":{
                "type":"integer",
                "description":"Dictionary object number of the segment that contains the object."
            },
            "object_type":{
                "type":"string",
                "description":"Type of the object (such as TABLE, INDEX)."
            },
            "created":{
                "type":"string",
                "description":"Timestamp for the creation of the object."
            },
            "last_ddl_time":{
                "type":"string",
                "description":"Timestamp for the last modification of the object and dependent objects resulting from a DDL statement (including grants and revokes)."
            },
            "timestamp":{
                "type":"string",
                "description":"Timestamp for the specification of the object (character data)."
            },
            "status":{
                "type":"string",
                "description":"Status of the object."
            },
            "temporary":{
                "type":"string",
                "description":"Indicates whether the object is temporary (the current session can see only data that it placed in this object itself) (Y) or not (N)."
            },
            "generated":{
                "type":"string",
                "description":"Indicates whether the name of this object was system-generated (Y) or not (N)."
            },
            "secondary":{
                "type":"string",
                "description":"Indicates whether this is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N)."
            },
            "namespace":{
                "type":"integer",
                "description":"Namespace for the object."
            },
            "edition_name":{
                "type":"string",
                "description":"Name of the edition in which the object is actual."
            },
            "sharing":{
                "type":"string",
                "description":"Indicates if the object is a metadata-linked, data-linked or not linked."
            },
            "editionable":{
                "type":"string",
                "description":"Indicates if the object editionable in the database."
            },
            "oracle_maintained":{
                "type":"string",
                "description":"Denotes whether the object was created, and is maintained, by Oracle-supplied scripts (such as catalog.sql or catproc.sql). An object for which this column has the value Y must not be changed in any way except by running an Oracle-supplied script."
            },
            "application":{
                "type":"string",
                "description":"Indicates whether the object is an Application common object (Y) or not (N)."
            },
            "default_collation":{
                "type":"string",
                "description":"Default collation for the object."
            },
            "duplicated":{
                "type":"string",
                "description":"Indicates whether this object is duplicated on this shard (Y) or not (N)."
            },
            "sharded":{
                "type":"string",
                "description":"Indicates whether this object is sharded (Y) or not (N)."
            },
            "created_appid":{
                "type":"integer",
                "description":"ID of the Application that created the object."
            },
            "created_vsnid":{
                "type":"integer",
                "description":"ID of the Application Version that created the object."
            },
            "modified_appid":{
                "type":"integer",
                "description":"ID of the Application that last modified the object."
            },
            "modified_vsnid":{
                "type":"integer",
                "description":"ID of the Application Version that last modified the object."
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
