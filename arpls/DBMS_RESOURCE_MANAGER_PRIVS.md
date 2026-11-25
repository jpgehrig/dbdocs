## 146  DBMS_RESOURCE_MANAGER_PRIVS

The `DBMS_RESOURCE_MANAGER_PRIVS` package maintains privileges associated with the Resource Manager.

This chapter contains the following topics:

- Summary of DBMS_RESOURCE_MANAGER_PRIVS Subprograms

**See Also:**

For more information on using the Database Resource Manager, see[Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

### 146.1 Summary of DBMS_RESOURCE_MANAGER_PRIVS Subprograms

This table lists the `DBMS_RESOURCE_MANAGER_PRIVS` subprograms and briefly describes them.

Table 146-1 DBMS_RESOURCE_MANAGER_PRIVS Package Subprograms

| Subprogram                             | Description                                                  |
|:---------------------------------------|:-------------------------------------------------------------|
| GRANT_SWITCH_CONSUMER_GROUP Procedure  | Grants the privilege to switch to resource consumer groups   |
| GRANT_SYSTEM_PRIVILEGE Procedure       | Performs a grant of a system privilege                       |
| REVOKE_SWITCH_CONSUMER_GROUP Procedure | Revokes the privilege to switch to resource consumer groups. |
| REVOKE_SYSTEM_PRIVILEGE Procedure      | Performs a revoke of a system privilege                      |

#### 146.1.1 GRANT_SWITCH_CONSUMER_GROUP Procedure

This procedure grants the privilege to switch to a resource consumer group.

##### Syntax

    DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SWITCH_CONSUMER_GROUP (
       grantee_name   IN VARCHAR2,
       consumer_group IN VARCHAR2,
       grant_option   IN BOOLEAN);

##### Parameters

Table 146-2 GRANT_SWITCH_CONSUMER_GROUP Procedure Parameters

| Parameter        | Description                                                             |
|:-----------------|:------------------------------------------------------------------------|
| `grantee_name`   | Name of the user or role to whom privilege is to be granted.            |
| `consumer_group` | Name of consumer group.                                                 |
| `grant_option`   | `TRUE` if grantee should be allowed to grant access, `FALSE` otherwise. |

##### Usage Notes

If you grant permission to switch to a particular consumer group to a user, then that user can immediately switch their current consumer group to the new consumer group.

If you grant permission to switch to a particular consumer group to a role, then any users who have been granted that role and have enabled that role can immediately switch their current consumer group to the new consumer group.

If you grant permission to switch to a particular consumer group to `PUBLIC`, then any user can switch to that consumer group.

If the `grant_option` parameter is `TRUE`, then users granted switch privilege for the consumer group may also grant switch privileges for that consumer group to others.

In order to set the initial consumer group of a user, you must grant the switch privilege for that group to the user.

**See Also:**

[DBMS_RESOURCE_MANAGER](DBMS_RESOURCE_MANAGER.md)

##### Examples

    BEGIN
    DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SWITCH_CONSUMER_GROUP (
     'scott', 'mail_maintenance_group', true);
    DBMS_RESOURCE_MANAGER.CREATE_PENDING_AREA();
    DBMS_RESOURCE_MANAGER.set_consumer_group_mapping(
      dbms_resource_manager.oracle_user, 'scott','mail_maintenance_group');
    DBMS_RESOURCE_MANAGER.SUBMIT_PENDING_AREA();
    END;
    /

#### 146.1.2 GRANT_SYSTEM_PRIVILEGE Procedure

This procedure performs a grant of a system privilege to a user or role.

##### Syntax

    DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SYSTEM_PRIVILEGE (
       grantee_name    IN VARCHAR2,
       privilege_name  IN VARCHAR2 DEFAULT 'ADMINISTER_RESOURCE_MANAGER',
       admin_option    IN BOOLEAN);

##### Parameters

Table 146-3 GRANT_SYSTEM_PRIVILEGE Procedure Parameters

| Parameter        | Description                                                    |
|:-----------------|:---------------------------------------------------------------|
| `grantee_name`   | Name of the user or role to whom privilege is to be granted.   |
| `privilege_name` | Name of the privilege to be granted.                           |
| `admin_option`   | `TRUE` if the grant is with `admin_option`, `FALSE` otherwise. |

##### Usage Notes

Currently, Oracle provides only one system privilege for the Resource Manager: `ADMINISTER_RESOURCE_MANAGER`. Database administrators have this system privilege with the `ADMIN` option. The grantee and the revokee can either be a user or a role. Users that have been granted the system privilege with the `ADMIN` option can also grant this privilege to others.

##### Examples

The following call grants this privilege to a user called `scott` without the `ADMIN` option:

    BEGIN
    DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SYSTEM_PRIVILEGE (
     grantee_name => 'scott',
     privilege_name => 'ADMINISTER_RESOURCE_MANAGER',
     admin_option => FALSE);
    END;
    /

#### 146.1.3 REVOKE_SWITCH_CONSUMER_GROUP Procedure

This procedure revokes the privilege to switch to a resource consumer group.

##### Syntax

    DBMS_RESOURCE_MANAGER_PRIVS.REVOKE_SWITCH_CONSUMER_GROUP (
       revokee_name   IN VARCHAR2,
       consumer_group IN VARCHAR2);

##### Parameters

Table 146-4 REVOKE_SWITCH_CONSUMER_GROUP Procedure Parameter

| Parameter        | Description                                    |
|:-----------------|:-----------------------------------------------|
| `revokee_name`   | Name of user/role from which to revoke access. |
| `consumer_group` | Name of consumer group.                        |

##### Usage Notes

If you revoke a user's switch privilege for a particular consumer group, then any subsequent attempts by that user to switch to that consumer group will fail.

If you revoke the initial consumer group from a user, then that user will automatically be part of the `DEFAULT_CONSUMER_GROUP` consumer group when logging in.

If you revoke the switch privilege for a consumer group from a role, then any users who only had switch privilege for the consumer group through that role will not be able to switch to that consumer group.

If you revoke the switch privilege for a consumer group from `PUBLIC`, then any users who could previously only use the consumer group through `PUBLIC` will not be able to switch to that consumer group.

##### Examples

The following example revokes the privileges to switch to `mail_maintenance_group` from Scott:

    BEGIN
    DBMS_RESOURCE_MANAGER_PRIVS.REVOKE_SWITCH_CONSUMER_GROUP (
     'scott', 'mail_maintenance_group');
    END;
    /

#### 146.1.4 REVOKE_SYSTEM_PRIVILEGE Procedure

This procedure performs a revoke of a system privilege from a user or role.

##### Syntax

    DBMS_RESOURCE_MANAGER_PRIVS.REVOKE_SYSTEM_PRIVILEGE (
       revokee_name   IN VARCHAR2,
       privilege_name IN VARCHAR2 DEFAULT 'ADMINISTER_RESOURCE_MANAGER');

##### Parameters

Table 146-5 REVOKE_SYSTEM_PRIVILEGE Procedure Parameters

| Parameter        | Description                                                    |
|:-----------------|:---------------------------------------------------------------|
| `revokee_name`   | Name of the user or role from whom privilege is to be revoked. |
| `privilege_name` | Name of the privilege to be revoked.                           |

##### Examples

The following call revokes the `ADMINISTER_RESOURCE_MANAGER` from user scott:

    BEGIN
    DBMS_RESOURCE_MANAGER_PRIVS.REVOKE_SYSTEM_PRIVILEGE ('scott');
    END;
    /
