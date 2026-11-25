## Changes in This Release for Oracle Database Real Application Security Administrator's and Developer's Guide

This preface contains:

- Changes in Oracle Database Release 19c Version 19.1

- Changes in Oracle Database Release 18c Version 18.1

- Changes in Oracle Database 12c Release 2 (12.2.0.1)

### Changes in Oracle Database Release 19c Version 19.1

The following are changes in Oracle Database Real Application Security Administrator's and Developer's Guide for Oracle Database release 19c, version 19.1:

- New Features

- Deprecated Features

#### New Features

There are no new features for this release.

#### Deprecated Features

There are no deprecated features for this release.

### Changes in Oracle Database Release 18c Version 18.1

The following are changes in Oracle Database Real Application Security Administrator's and Developer's Guide for Oracle Database release 18c, version 18.1:

- New Features

- Deprecated Features

#### New Features

There are no new features for this release.

#### Deprecated Features

There are no deprecated features for this release.

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database Real Application Security Administrator's and Developer's Guide for Oracle Database 12c Release 2 (12.2.0.1):

- New Features

- Deprecated Features

#### New Features

The following features are new in this release:

- Real Application Security includes support for privilege scoping

  Oracle Database 12c Release 2 (12.2) extends the Real Application Security model by allowing per principal session privilege grants, through an ACL set on the principal as a native Real Application Security application user, for granting session management privileges. In addition, Oracle Database 12c Release 2 (12.2) extends the Real Application Security model by allowing per principal session privilege grants, though an ACL set on the principal as a dynamic role, for granting only the `SET_DYNAMIC_ROLES` privilege. Principal-specific ACL grants take precedence over system-level session privilege grants. It allows for a negative grant to be set on the principal specific ACL. Use of an ACL allows a common set of grants to be enforced on a group of native application users and dynamic roles.

  This feature provides the following new API:
  - [SET_ACL Procedure](XS_PRINCIPAL-package.md)— Sets an ACL on the specified application user or dynamic role.

  This feature enhances the following APIs with the addition of the `acl` parameter:
  - [CREATE_USER Procedure](XS_PRINCIPAL-package.md)

  - [CREATE_DYNAMIC_ROLE Procedure](XS_PRINCIPAL-package.md)

  This feature enhances the following views by displaying the ACLs that are set on the user and or dynamic role or both:
  - [DBA_XS_USERS](real-application-security-data-dictionary-views.md)

  - [DBA_XS_DYNAMIC_ROLES](real-application-security-data-dictionary-views.md)

  This feature adds the `SET_DYNAMIC_ROLES` privilege, which is defined in the `SESSION_SC` security class to protect enablement and disablement of a dynamic role as part of the attach session and assign user operations.

  See [SET_ACL Procedure](XS_PRINCIPAL-package.md), [CREATE_USER Procedure](XS_PRINCIPAL-package.md), [CREATE_DYNAMIC_ROLE Procedure](XS_PRINCIPAL-package.md), [DBA_XS_USERS](real-application-security-data-dictionary-views.md), [DBA_XS_DYNAMIC_ROLES](real-application-security-data-dictionary-views.md), and the `SESSION_SC` security class in [Security Classes](predefined-objects-in-real-application-security.md) for more information.

  See [About Real Application Security Session Privilege Scoping Through ACL](configuring-application-sessions.md) for more information.

- Real Application Security supports column-level access control on DML statements. This allows users to insert, update, and delete specific column values based on their granted column-level privileges.

  Beginning with Oracle Database 12c Release 2 (12.2), users with required privileges can do DMLs with Data Security column security. This means:
  - To update a row value, an authorized user needs both the row-level `UPDATE` privilege as well as the column privilege on the protected columns to be updated.

  - To insert a row, an authorized user needs both the row-level `INSERT` privilege as well as the column privilege on each protected column. If the `INSERT` statement does not insert a value for a protected column, the column privilege is not required, and the default value (or `NULL` if there is no default value) is inserted.

  - To delete a row, an authorized user only needs the row-level `DELETE` privilege. The column privilege is not required.

  - No data is disclosed for DMLs with Data Security row-level and column-level security. DML statements with `RETURNING INTO` or with the parameter - `sql92_security` enabled require both the row-level `SELECT` privilege as well as the column privileges if the columns appear in the `RETURNING INTO` clause.

- Real Application Security includes support for schema-level security policy administration

  This feature enhances the following APIs:
  - [GRANT_SYSTEM_PRIVILEGE Procedure](XS_ADMIN_UTIL-package.md) by adding the `schema` parameter

  - [REVOKE_SYSTEM_PRIVILEGE Procedure](XS_ADMIN_UTIL-package.md) by adding the `schema` parameter

  This feature extends the `ADMIN_SEC_POLICY` privilege to schemas for policy management.

  See [XS_ACL Package](XS_ACL-package.md), [XS_DATA_SECURITY Package](XS_DATA_SECURITY-package.md), and [XS_SECURITY_CLASS Package](XS_SECURITY_CLASS-package.md) for more information.

  This feature adds the `APPLY_SEC_POLICY` privilege for policy enforcement within granted schemas to achieve policy enforcement within an application.

  The `APPLY_SEC_POLICY` privilege will be checked in the following APIs before enforcing policies: [APPLY_OBJECT_POLICY Procedure](XS_DATA_SECURITY-package.md), [REMOVE_OBJECT_POLICY Procedure](XS_DATA_SECURITY-package.md), [ENABLE_OBJECT_POLICY Procedure](XS_DATA_SECURITY-package.md), and [DISABLE_OBJECT_POLICY Procedure](XS_DATA_SECURITY-package.md).

  This feature adds two audit actions:
  - `AUDIT_GRANT_PRIVILEGE`

    — to audit the `GRANT_SYSTEM_PRIVILEGE` API

  - `AUDIT_REVOKE_PRIVILEGE`

    — to audit the `REVOKE_SYSTEM_PRIVILEGE` API

  This feature adds the following views: [ALL_XS_SECURITY_CLASSES](real-application-security-data-dictionary-views.md), [ALL_XS_SECURITY_CLASS_DEP](real-application-security-data-dictionary-views.md), [ALL_XS_PRIVILEGES](real-application-security-data-dictionary-views.md), [ALL_XS_IMPLIED_PRIVILEGES](real-application-security-data-dictionary-views.md), [ALL_XS_ACLS](real-application-security-data-dictionary-views.md), [ALL_XS_ACES](real-application-security-data-dictionary-views.md), [ALL_XS_POLICIES](real-application-security-data-dictionary-views.md), [ALL_XS_REALM_CONSTRAINTS](real-application-security-data-dictionary-views.md), [ALL_XS_INHERITED_REALMS](real-application-security-data-dictionary-views.md), [ALL_XS_ACL_PARAMETERS](real-application-security-data-dictionary-views.md), [ALL_XS_COLUMN_CONSTRAINTS](real-application-security-data-dictionary-views.md), [ALL_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md), and [DBA_XS_PRIVILEGE_GRANTS](real-application-security-data-dictionary-views.md).

  See [About Schema Level Real Application Security Policy Administration](configuring-data-security.md) for more information.

- Oracle Label Security support for the Oracle Database Real Application Security

  For the `user_name` parameter in the `SA_USER_ADMIN.SET_USER_LABELS` procedure and in the `SA_USER_ADMIN.SET_USER_PRIVS` procedure for Oracle Database, the user name can be an Oracle Database Real Application Security user name.

  See the `SA_USER_ADMIN.SET_USER_LABELS` procedure in [Oracle Label Security Administrator’s Guide](../olsag/oracle-label-security-pl-sql-packages.md) and the `SA_USER_ADMIN.SET_USER_PRIVS` procedure in [Oracle Label Security Administrator’s Guide](../olsag/oracle-label-security-pl-sql-packages.md) for more information.

  Labels or Oracle Label Security privileges assigned to the Real Application Security user are enforced in the Real Application Security user session. Oracle Label Security context is established upon the following Real Application Security session operations (`ATTACH_SESSION`, `SWITCH_USER`, `ASSIGN_USER`) and in Real Application Security direct logon sessions. Based on labels or privileges or both that the current Real Application Security session has, the Oracle Label Security policy is enforced.

  See [Attaching an Application Session to a Traditional Database Session](configuring-application-sessions.md), [Assigning an Application User to an Anonymous Application Session](configuring-application-sessions.md), [Switching a Current Application User to Another Application User in the Current Application Session](configuring-application-sessions.md), and [Oracle Label Security Context Is Established in Direct Logon Session](configuring-application-users-and-application-roles.md) for more information.

- Predefined application role `XSCONNECT`

  Allows the user granted this role to connect to the database. In other words, a user not granted this predefined role cannot connect to the database.

  See [Regular Application Roles](predefined-objects-in-real-application-security.md), [GRANT_ROLES Procedure](XS_PRINCIPAL-package.md), and [About Creating a Direct Login Application User Account](configuring-application-users-and-application-roles.md) for more information.

#### Deprecated Features

The following features are deprecated and will not be supported in future releases:

- For the `CREATE_USER` procedure

  The `PASSWORDEXPIRED` and `LOCKED` values for the parameter `STATUS` are deprecated.

  See "[CREATE_USER Procedure](XS_PRINCIPAL-package.md)" for more information.

- For the `SET_USER_STATUS` procedure

  The `PASSWORDEXPIRED` status value is deprecated.

  See "[SET_USER_STATUS Procedure](XS_PRINCIPAL-package.md)" for more information.

- For the `SET_PASSWORD` procedure

  The password types `XS_MD4` and `XS_O3LOGON` are deprecated.

  See "[SET_PASSWORD Procedure](XS_PRINCIPAL-package.md)" for more information.

- For the `SET_VERIFIER` procedure

  The verifier types `XS_SALTED_MD5`, `XS_SHA1`, `XS_SASL_MD5`, `XS_MD5`, `XS_MD4`, and `XS_O3LOGON` are deprecated.

  See "[SET_VERIFIER Procedure](XS_PRINCIPAL-package.md)" for more information.
