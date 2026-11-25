## A Predefined Objects in Real Application Security

This appendix describes the following predefined objects in Real Application Security:

- Users

- Roles

- Namespaces

- Security Classes

- ACLs

### A.1 Users

`XSGUEST` - A system-defined Real Application Security user typically reserved for anonymous access.

### A.2 Roles

Real Application Security provides predefined application roles for regular application roles, dynamic application roles, and database roles.

This section includes the following topics:

- Regular Application Roles

- Dynamic Application Roles

- Database Roles

#### A.2.1 Regular Application Roles

Real Application Security provides the following predefined regular application roles:

- `XSPUBLIC` - This application role is similar to the `PUBLIC` role in the database. It is granted to all Real Application Security application users.

- `XSBYPASS` - A role used to bypass the restrictions imposed by a system constraining ACL.

- `XSPROVISIONER` - A role used to grant `PROVISION` and `CALLBACK` privileges.

- `XSSESSIONADMIN` - A role used for session administration.

- `XSNAMESPACEADMIN` - A role used for namespace attribute administration.

- `XSCACHEADMIN` - A role used for middle tier cache administration.

- `XSDISPATCHER` - A role used for session administration, namespace administration, and middle tier cache administration by a dispatcher.

- `XSCONNECT` — A role used to control whether a Real Application Security application user with a password can connect to the database or not.

#### A.2.2 Dynamic Application Roles

Real Application Security provides the following predefined dynamic application roles:

- `DBMS_AUTH`

  This application role depends on the authentication state of the application user. It is enabled whenever the application user is authenticated in the Real Application Security system as a direct-logon application user using any of the database authentication methods.

- `EXTERNAL_DBMS_AUTH`

  This application role depends on the authentication state of the external application user. It is enabled whenever the external application user is authenticated in the Real Application Security system as an external direct-logon application user using any of the database authentication methods.

- `DBMS_PASSWD`

  This application role depends on the authentication state of the application user. It is enabled whenever the application user is authenticated in the Real Application Security system as a direct-logon application user using a password authentication method.

- `MIDTIER_AUTH`

  This application role depends on the authentication state of the application user. It is enabled whenever the application user is authenticated in the Real Application Security system through the middle tier. The middle tier explicitly passes this application role to the database indicating that the application user has been authenticated by the middle tier.

- `XSAUTHENTICATED`

  This application role depends on the authentication state of the application user. It is enabled whenever the application user is authenticated in the Real Application Security system (either directly or through the middle tier).

- `XSSWITCH`

  This application role depends on the session state of the application user. It is enabled whenever the Real Application Security session for an application user is created as a result of a `switch_user` operation, that is, if the proxy user in the original Real Application Security session is switched to an application user.

#### A.2.3 Database Roles

Real Application Security provides the following database roles.

- `PROVISIONER` - A database role that has the `PROVISION` and `CALLBACK` privileges.

- `XS_SESSION_ADMIN` - A database role that has the `ADMINISTER_SESSION` privilege.

- `XS_NAMESPACE_ADMIN` - A database role that has the `ADMIN_ANY_NAMESPACE` privilege.

- `XS_CACHE_ADMIN` - A database role that can be used for middle tier cache administration.

### A.3 Namespaces

Real Application Security provides the following predefined namespaces:

- `XS$GLOBAL_VAR` - Contains the following NLS Attributes: `NLS_LANGUAGE`, `NLS_TERRITORY`, `NLS_SORT`, `NLS_DATE_LANGUAGE`, `NLS_DATE_FORMAT`, `NLS_CURRENCY`, `NLS_NUMERIC_CHARACTERS`, `NLS_ISO_CURRENCY`, `NLS_CALENDAR`, `NLS_TIME_FORMAT`, `NLS_TIMESTAMP_FORMAT`, `NLS_TIME_TZ_FORMAT`, `NLS_TIMESTAMP_TZ_FORMAT`, `NLS_DUAL_CURRENCY`, `NLS_COMP`, `NLS_LENGTH_SEMANTICS`, and `NLS_NCHAR_CONV_EXCP`.

  The `XS$GLOBAL_VAR` namespace can be loaded in to a Real Application Security session without requiring any privileges.

- `XS$SESSION` - Contains the following attributes: `CREATED_BY`, `CREATE_TIME`, `COOKIE`, `CURRENT_XS_USER`, `CURRENT_XS_USER_GUID`, `INACTIVITY_TIMEOUT`, `LAST_ACCESS_TIME`, `LAST_AUTHENTICATION_TIME`, `LAST_UPDATED_BY`, `PROXY_GUID`, `SESSION_ID`, `SESSION_SIZE`, `SESSION_XS_USER`, `SESSION_XS_USER_GUID`, `USERNAME`, and `USER_ID`.

### A.4 Security Classes

Real Application Security provides the following predefined security classes and application privileges:

- `DML` - DML Privileges security class. If an ACL does not specify its security class, `DML` is the default security class for the ACL. See "[DML Security Class](configuring-application-privileges-and-access-contol-lists.md)" for more information. Contains the following common application privileges for object manipulation.

  - `SELECT` - Privilege to read an object.

  - `INSERT` - Privilege to insert an object.

  - `UPDATE` - Privilege to update an object.

  - `DELETE` - Privilege to delete an object.

- `SYSTEM` - System security class. Contains the following application privileges:

  - `PROVISION` - Privilege for updating principal documents from FIDM. The `PROVISION` privilege is also extended for creating, deleting, and modifying Real Application Security principals (users or roles) beginning in Release 12.2. This Real Application Security system privilege is intended to replace the traditional use of database create user, alter user privileges, and so forth to create and alter Real Application Security application users and roles.

  - `CALLBACK` - Privilege to register and update global callbacks.

  - `ADMIN_ANY_SEC_POLICY` - Privilege for any administrative operation.

  - `ADMIN_SEC_POLICY` - Privilege for administering objects in its own schema.

  - `ADMIN_NAMESPACE` - Privilege for administering any namespace.

- `SESSION_SC` - Session security class. Contains the following application privileges:

  - `CREATE_SESSION` - Privilege to create a Real Application Security user session.

  - `TERMINATE_SESSION` - Privilege to terminate a Real Application Security user session.

  - `ATTACH_SESSION` - Privilege to attach to a Real Application Security user session.

  - `MODIFY_SESSION` - Privilege to modify contents of a Real Application Security user session.

  - `ASSIGN_USER` - Privilege to assign user to an anonymous Real Application Security user session.

  - `ADMINISTER_SESSION` - Privilege for Real Application Security user session administration, aggregate of `CREATE_SESSION`, `TERMINATE_SESSION`, `ATTACH_SESSION`, `MODIFY_SESSION`, and `SET_DYNAMIC_ROLES`.

  - `SET_DYNAMIC_ROLES` - Privilege to protect Real Application Security enablement and disablement of a dynamic role as part of the attach session and assign user operations.

- `NSTEMPLATE_SC` - Namespace template security class. Contains the following application privileges:

  - `MODIFY_NAMESPACE` - Privilege to modify session namespace.

  - `MODIFY_ATTRIBUTE` - Privilege to modify session namespace attribute.

  - `ADMIN_NAMESPACE` - Privilege for namespace administration, aggregate of `MODIFY_NAMESPACE` and `MODIFY_ATTRIBUTE`.

### A.5 ACLs

Real Application Security provides the following predefined ACLs:

- `SYSTEMACL` - ACL for granting `SYSTEM` security class privileges.

  Grants `PROVISION` and `CALLBACK` privileges to `PROVISIONER` database role and `XSPROVISIONER` Real Application Security role.

  Grants `ADMIN_ANY_SEC_POLICY` privilege to `DBA` database role.

  Grants `ADMIN_SEC_POLICY` privilege to `RESOURCE` and `XS_RESOURCE` database roles.

  Grants `ADMIN_ANY_NAMESPACE` privilege to `DBA` and `XS_NAMESPACE_ADMIN` database roles and `XSNAMESPACEADMIN` and `MIDTIER_AUTH` Real Application Security roles.

- `SESSIONACL` - ACL for granting `SESSION_SC` security class privileges.

  Grants `ADMINISTER_SESSION` privilege to `XS_SESSION_ADMIN` database role and `XSSESSIONADMIN` Real Application Security role.

- `NS_UNRESTRICTED_ACL` - ACL to grant `ADMIN_NAMESPACE` privilege to `PUBLIC` database role and `XSPUBLIC` Real Application Security role.
