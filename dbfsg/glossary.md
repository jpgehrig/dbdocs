## Glossary

### access control entry (ACE)

An entry in the access control list that grants or denies access to a given principal. One or more ACEs are listed within an access control list (ACL), in which the ordering of the ACEs is relevant.

### access control list (ACL)

A list of access control entries that determines which principals have access to a given resource or resources. In Oracle Database Real Application Security, you use ACLs to define user privileges.

### ACE

See access control entry (ACE).

### ACL

See access control list (ACL).

### aggregate privilege

A privilege that contains other privileges. When an aggregate privilege has been granted or denied, then all of its child privileges are granted or denied as well.

### application role

A role that can only be granted to a application user or to another application role.

### application session

A user session that contains information pertinent only to the application. Unlike traditional "heavyweight" database sessions, an application session does not hold its own database resources such as transactions and cursors.

### application user

A user account that does not own a schema and can create a application session through the middle tier to the database.

### column level security

The ability to apply specific privileges to a table column.

### custom privilege

A privilege not predefined by Oracle Database. See also system privilege.

### data realm

A set of rows within a database table whose access you control by associating it with an access control list (ACL). It is comprised of one or more object instances. See also dynamic data realm constraint and static data realm constraint.

### database role

A role that can only be granted to a database user. It is also called a heavyweight role. See also application role.

### database user

A user account that is created within the database and has a schema. It is also called a heavyweight user. See also application user.

### dynamic ACL

An access control list that has been associated with a dynamic data realm constraint.

### dynamic application role

A role that is enabled only under certain conditions, for example, when a user has logged on using SSL, or during a specified period.

### dynamic data realm constraint

An data realm whose `WHERE` predicate is rerun each time the user performs a query on the data realm constraint data. See also static data realm constraint.

### function security

The mechanism by which user access to an applications functionality is controlled. For example, for Oracle Database Real Application Security, use the `checkPrivilege()` method to check the privilege on the ACL for a row to determine if a specific privilege on one or more given ACLs is associated with that row. See [About the Check Privilege API](application-session-service-in-oracle-fusion-middleware.md) for more information.

### globally unique identifier (GUID)

The external ID that applications can use to manage the user's session information. This identifier is not guaranteed to be unique across all tiers, but the number of unique keys that comprises it is so large that the chances of it being duplicated are small. See also unique identifier (UID).

### GUID

See globally unique identifier (GUID).

### heavyweight role

A traditional database role.

### heavyweight user

A traditional database user account that owns a schema.

### namespace

A container consisting of attribute-value pairs that reflects the state of the application session.

### object instance

A single relational table row that is part of an data realm. It is identified by its primary key value.

### password verifier

A hashed version of a clear text password, which is then encoded as a BASE64 encoded string.

### principal

A user or collection of users alternately called a group or a role. See also application user and application role.

### privilege

A right or permission that can be granted or denied to a principal. See also aggregate privilege, custom privilege, and system privilege.

### security class

A named collection of privileges that can be associated with an ACL.

### static ACL

An access control list that has been associated with a static data realm constraint.

### static data realm constraint

An data realm whose `WHERE` predicate is stored in cache, so that it is not rerun each time the user performs a query on the data realm constraint data. See also dynamic data realm constraint.

### system privilege

Predefined privilege supplied by Oracle Database. See also custom privilege.

### unique identifier (UID)

A unique internal identifier that Oracle Database uses to track the user or role. It is used to manage the user's session information across the database enterprise. See also globally unique identifier (GUID).

### UID

See unique identifier (UID).

### user switch

The ability of an application user to proxy as another user. The application state (that is, namespaces and attributes) is maintained from the previous user, but the security context reflects that of the new user.
