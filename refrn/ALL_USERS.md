## 3.135 ALL_USERS

`ALL_USERS` lists all users of the database visible to the current user.

This view does not describe the users (see the related views).

### Related Views

- `DBA_USERS` describes all users of the database, and contains more columns than `ALL_USERS`.

- `USER_USERS` describes the current user, and contains more columns than `ALL_USERS`.

| Column              | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:--------------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`          | `VARCHAR2(128)` | `NOT NULL` | Name of the user                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `USER_ID`           | `NUMBER`        | `NOT NULL` | ID number of the user                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `CREATED`           | `DATE`          | `NOT NULL` | User creation date                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `COMMON`            | `VARCHAR2(3)`   |            | Indicates whether a given user is common. Possible values:<br>• `YES` if a user is common<br>• `NO` if a user is local (not common)                                                                                                                                                                                                                                                                                                                         |
| `ORACLE_MAINTAINED` | `VARCHAR2(1)`   |            | Denotes whether the user was created, and is maintained, by Oracle-supplied scripts (such as catalog.sql or catproc.sql). A user for which this column has the value `Y` must not be changed in any way except by running an Oracle-supplied script.                                                                                                                                                                                                        |
| `INHERITED`         | `VARCHAR2(3)`   |            | Indicates whether the user definition was inherited from another container (`YES`) or not (`NO`)                                                                                                                                                                                                                                                                                                                                                            |
| `DEFAULT_COLLATION` | `VARCHAR2(100)` |            | Default collation for the user’s schema                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `IMPLICIT`          | `VARCHAR2(3)`   |            | Indicates whether this user is a common user created by an implicit application (`YES`) or not (`NO`)                                                                                                                                                                                                                                                                                                                                                       |
| `ALL_SHARD`         | `VARCHAR2(3)`   |            | In a sharded database, the value in this column indicates whether the user was created with shard DDL enabled. The possible values are:<br>• `YES`: The user was created with shard DDL enabled. The user exists on all shards and the shard catalog.<br>• `NO`: The user was created without shard DDL enabled. The user exists only in the database in which the user was created.<br>In a non-sharded database, the value in this column is always `NO`. |

**See Also:**

- "[DBA_USERS](DBA_USERS.md)"

- "[USER_USERS](USER_USERS.md)"

- [Using Oracle Sharding](../shard/sharding-overview.md) for more information about sharded database management
