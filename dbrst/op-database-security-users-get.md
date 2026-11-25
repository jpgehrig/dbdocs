Returns records from DBA_USERS or ALL_USERS view depending on the role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

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

Description of all users in the database.

Body ()

Root Schema : DatabaseUsers

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
                    "$ref":"#/definitions/DatabaseUsersItem"
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

- Array of: object DatabaseUsersItem
  This object describes a database user. The list of attributes may vary depending on database version.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseUsersItem"
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

Nested Schema : DatabaseUsersItem

Type: `object`

This object describes a database user. The list of attributes may vary depending on database version.

Show Source

- account_status(optional): string
  Account status.
- all_shard(optional): string
  In a sharded database, the value in this column indicates whether the user was created with shard DDL enabled.
- authentication_type(optional): string
  Indicates the authentication mechanism for the user.
- common(optional): string
  Indicates whether a given user is common.
- created(optional): string
  User creation date.
- days_left(optional): integer
  Indicates the number of days left before the account expires. Can be a negative value if the account is expired.
- default_collation(optional): string
  Default collation for the user???s schema.
- default_tablespace(optional): string
  Default tablespace for data.
- editions_enabled(optional): string
  Indicates whether editions have been enabled for the corresponding user (Y) or not (N).
- expired_account(optional): integer
  When EXPIRY_DATE is in the past, 1, otherwise 0.
- expiry_date(optional): string
  Date of expiration of the account.
- external_name(optional): string
  User external name. For centrally managed users, if the database user mapping is an exclusive mapping, then this will be the directory service DN for the user. If this database user is a shared schema, it will be the DN of a group.
- implicit(optional): string
  Indicates whether this user is a common user created by an implicit application (YES) or not (NO).
- inherited(optional): string
  Indicates whether the user definition was inherited from another container (YES) or not (NO).
- initial_rsrc_consumer_group(optional): string
  Initial resource consumer group for the user.
- last_login(optional): string
  The time of the last user login.
- links(optional): array links
- local_temp_tablespace(optional): string
  Default local temporary tablespace for the user.
- lock_date(optional): string
  Date the account was locked if account status was LOCKED.
- locked_account(optional): integer
  When LOCK_DATE is set, 1, otherwise 0.
- open_account(optional): integer
  When ACCOUNT_STATUS = 'OPEN', 1, otherwise 0.
- oracle_maintained(optional): string
  Denotes whether the user was created, and is maintained, by Oracle-supplied scripts (such as catalog.sql or catproc.sql). A user for which this column has the value Y must not be changed in any way except by running an Oracle-supplied script.
- password_versions(optional): string
  Shows the list of versions of the password hashes (also known as 'verifiers') existing for the account.
- profile(optional): string
  User resource profile name.
- proxy_only_connect(optional): string
  Indicates whether a user can connect directly (N) or whether the account can only be proxied (Y) by users who have proxy privileges for this account (that is, by users who have been granted the 'connect through' privilege for this account).
- temporary_tablespace(optional): string
  Name of the default tablespace for temporary tables or the name of a tablespace group.
- user_id(optional): integer
  ID number of the user.
- username(optional): string
  Name of the user.

<!-- -->

    {
        "type":"object",
        "description":"This object describes a database user. The list of attributes may vary depending on database version.",
        "properties":{
            "username":{
                "type":"string",
                "description":"Name of the user."
            },
            "user_id":{
                "type":"integer",
                "description":"ID number of the user."
            },
            "account_status":{
                "type":"string",
                "description":"Account status."
            },
            "lock_date":{
                "type":"string",
                "description":"Date the account was locked if account status was LOCKED."
            },
            "expiry_date":{
                "type":"string",
                "description":"Date of expiration of the account."
            },
            "default_tablespace":{
                "type":"string",
                "description":"Default tablespace for data."
            },
            "temporary_tablespace":{
                "type":"string",
                "description":"Name of the default tablespace for temporary tables or the name of a tablespace group."
            },
            "local_temp_tablespace":{
                "type":"string",
                "description":"Default local temporary tablespace for the user."
            },
            "created":{
                "type":"string",
                "description":"User creation date."
            },
            "profile":{
                "type":"string",
                "description":"User resource profile name."
            },
            "initial_rsrc_consumer_group":{
                "type":"string",
                "description":"Initial resource consumer group for the user."
            },
            "external_name":{
                "type":"string",
                "description":"User external name. For centrally managed users, if the database user mapping is an exclusive mapping, then this will be the directory service DN for the user. If this database user is a shared schema, it will be the DN of a group."
            },
            "password_versions":{
                "type":"string",
                "description":"Shows the list of versions of the password hashes (also known as 'verifiers') existing for the account."
            },
            "editions_enabled":{
                "type":"string",
                "description":"Indicates whether editions have been enabled for the corresponding user (Y) or not (N)."
            },
            "authentication_type":{
                "type":"string",
                "description":"Indicates the authentication mechanism for the user."
            },
            "proxy_only_connect":{
                "type":"string",
                "description":"Indicates whether a user can connect directly (N) or whether the account can only be proxied (Y) by users who have proxy privileges for this account (that is, by users who have been granted the 'connect through' privilege for this account)."
            },
            "common":{
                "type":"string",
                "description":"Indicates whether a given user is common."
            },
            "last_login":{
                "type":"string",
                "description":"The time of the last user login."
            },
            "oracle_maintained":{
                "type":"string",
                "description":"Denotes whether the user was created, and is maintained, by Oracle-supplied scripts (such as catalog.sql or catproc.sql). A user for which this column has the value Y must not be changed in any way except by running an Oracle-supplied script."
            },
            "inherited":{
                "type":"string",
                "description":"Indicates whether the user definition was inherited from another container (YES) or not (NO)."
            },
            "default_collation":{
                "type":"string",
                "description":"Default collation for the user???s schema."
            },
            "implicit":{
                "type":"string",
                "description":"Indicates whether this user is a common user created by an implicit application (YES) or not (NO)."
            },
            "all_shard":{
                "type":"string",
                "description":"In a sharded database, the value in this column indicates whether the user was created with shard DDL enabled."
            },
            "locked_account":{
                "type":"integer",
                "description":"When LOCK_DATE is set, 1, otherwise 0."
            },
            "expired_account":{
                "type":"integer",
                "description":"When EXPIRY_DATE is in the past, 1, otherwise 0."
            },
            "open_account":{
                "type":"integer",
                "description":"When ACCOUNT_STATUS = 'OPEN', 1, otherwise 0."
            },
            "days_left":{
                "type":"integer",
                "description":"Indicates the number of days left before the account expires. Can be a negative value if the account is expired."
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
